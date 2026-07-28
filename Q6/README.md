# Question 6: Reverse Proxy for "myapp1"
Configure Nginx as a reverse proxy listening on Port 80 to route incoming HTTP traffic directly to container `myapp1` running on host port `8082`.


# Step 2: Ensure persistent directory & myapp1 container
# ---------------------------------------------------------
sudo mkdir -p /app/appuser/data/app1
if [ ! -f /app/appuser/data/app1/index.html ]; then
    echo "Welcome to PDD" | sudo tee /app/appuser/data/app1/index.html
fi

# Spin up myapp1 on port 8082 if not currently running
if ! sudo docker ps --format '{{.Names}}' | grep -q "^myapp1$"; then
    sudo docker rm -f myapp1 2>/dev/null || true
    sudo docker run -d --name myapp1 -p 8082:80 \
      -v /app/appuser/data/app1:/usr/share/nginx/html nginx:alpine
fi

# ---------------------------------------------------------
# Step 3: Install & Configure Nginx Reverse Proxy
# ---------------------------------------------------------
sudo apt-get update && sudo apt-get install -y nginx

sudo bash -c 'cat << "EOF" > /etc/nginx/sites-available/myapp1.conf
server {
    listen 80;
    server_name _;

    location / {
        proxy_pass http://127.0.0.1:8082;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
EOF'

# Enable Nginx config & restart service
sudo rm -f /etc/nginx/sites-enabled/default
sudo ln -sf /etc/nginx/sites-available/myapp1.conf /etc/nginx/sites-enabled/
sudo nginx -t && sudo systemctl restart nginx

# ---------------------------------------------------------
# Step 4: Verify Reverse Proxy & Generate output.txt
# ---------------------------------------------------------
echo "=== Docker Container Status ===" > output.txt
sudo docker ps --filter "name=myapp1" >> output.txt

echo -e "\n=== Reverse Proxy Test (Port 80 -> myapp1:8082) ===" >> output.txt
curl -i http://localhost/ >> output.txt

## Objective
Configure Nginx as a reverse proxy listening on Port 80 to route incoming HTTP traffic directly to container `myapp1` running on host port `8082`.

## Steps Executed
1. **Container Verification:** Confirmed `myapp1` is running on host port `8082` with volume mounted from `/app/appuser/data/app1`.
2. **Reverse Proxy Configuration:** Configured `/etc/nginx/sites-available/myapp1.conf` with `proxy_pass http://127.0.0.1:8082;`.
3. **Activation & Test:** Enabled configuration, restarted Nginx service, and verified response using `curl -i http://localhost/`.
EOF



