# Question 7: Configure HTTPS. with domain eg: pddtestapp.luluone.com - Create a self signed Certificate or do inform us and we shall share the Certificate.
EOF

# ---------------------------------------------------------
# Step 2: Generate Self-Signed SSL Certificate
# ---------------------------------------------------------
sudo mkdir -p /etc/nginx/ssl
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
  -keyout /etc/nginx/ssl/pddtestapp.key \
  -out /etc/nginx/ssl/pddtestapp.crt \
  -subj "/C=IN/ST=State/L=City/O=PDD/OU=IT/CN=pddtestapp.luluone.com"

# ---------------------------------------------------------
# Step 3: Add Domain Mapping to Local /etc/hosts
# ---------------------------------------------------------
if ! grep -q "pddtestapp.luluone.com" /etc/hosts; then
    echo "127.0.0.1 pddtestapp.luluone.com" | sudo tee -a /etc/hosts
fi

# ---------------------------------------------------------
# Step 4: Configure Nginx for SSL (Port 443) & Redirection (Port 80)
# ---------------------------------------------------------
sudo bash -c 'cat << "EOF" > /etc/nginx/sites-available/pddtestapp_ssl.conf
server {
    listen 80;
    server_name pddtestapp.luluone.com;

    # Redirect all HTTP traffic to HTTPS
    return 301 https://$host$request_uri;
}

server {
    listen 443 ssl;
    server_name pddtestapp.luluone.com;

    # SSL Certificate Details
    ssl_certificate /etc/nginx/ssl/pddtestapp.crt;
    ssl_certificate_key /etc/nginx/ssl/pddtestapp.key;

    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_ciphers HIGH:!aNULL:!MD5;

    # Proxy traffic to myapp1 container running on port 8082
    location / {
        proxy_pass http://127.0.0.1:8082;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
EOF'

# ---------------------------------------------------------
# Step 5: Enable SSL Config & Open Firewall Port
# ---------------------------------------------------------
sudo rm -f /etc/nginx/sites-enabled/default
sudo ln -sf /etc/nginx/sites-available/pddtestapp_ssl.conf /etc/nginx/sites-enabled/
sudo ufw allow 443/tcp 2>/dev/null || true
sudo nginx -t && sudo systemctl restart nginx
## Overview
Configured Nginx as a reverse proxy with SSL termination on Port 443 using a self-signed OpenSSL certificate for pddtestapp.luluone.com.

## Configuration Details
- Domain: pddtestapp.luluone.com
- SSL Certificate: /etc/nginx/ssl/pddtestapp.crt
- SSL Key: /etc/nginx/ssl/pddtestapp.key
- Backend Container: http://127.0.0.1:8082 (myapp1)
- HTTP Redirection: Port 80 automatically redirects to HTTPS Port 443.

## How to Test
curl -I http://pddtestapp.luluone.com/
curl -k https://pddtestapp.luluone.com/

OUTPUT

=== Testing HTTP to HTTPS Redirection ===
HTTP/1.1 301 Moved Permanently
Server: nginx/1.24.0 (Ubuntu)
Date: Mon, 27 Jul 2026 12:01:51 GMT
Content-Type: text/html
Content-Length: 178
Connection: keep-alive
Location: https://pddtestapp.luluone.com/


=== Testing HTTPS Endpoint (Self-Signed) ===
HTTP/1.1 200 OK
Server: nginx/1.24.0 (Ubuntu)
Date: Mon, 27 Jul 2026 12:01:51 GMT
Content-Type: text/html
Content-Length: 15
Connection: keep-alive
Last-Modified: Mon, 27 Jul 2026 10:20:43 GMT
ETag: "6a6730fb-f"
Accept-Ranges: bytes

