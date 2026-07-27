# Question 6: Reverse Proxy for "myapp1"

## Objective
Configure Nginx as a reverse proxy listening on Port 80 to route incoming HTTP traffic directly to container `myapp1` running on host port `8082`.

## Steps Executed
1. **Container Verification:** Confirmed `myapp1` is running on host port `8082` with volume mounted from `/app/appuser/data/app1`.
2. **Reverse Proxy Configuration:** Configured `/etc/nginx/sites-available/myapp1.conf` with `proxy_pass http://127.0.0.1:8082;`.
3. **Activation & Test:** Enabled configuration, restarted Nginx service, and verified response using `curl -i http://localhost/`.
