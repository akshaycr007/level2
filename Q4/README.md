1. mkdir -p /app/appuser/data/app1 /app/appuser/data/app2
2. echo "Welcome to PDD" > /app/appuser/data/app1/index.html
3. echo "Welcome to PDD official" > /app/appuser/data/app2/index.html
4. sudo docker run -d --name my-app1 -p 8082:80 -v /app/appuser/data/app1:/usr/share/nginx/html nginx
5. sudo docker run -d --name my-app2 -p 8081:80 -v /app/appuser/data/app2:/usr/share/nginx/html nginx
6. curl http://localhost:8082
7. curl http://localhost:8081


OUTPUT

=== Running Docker Containers ===
CONTAINER ID   IMAGE                COMMAND                  CREATED          STATUS          PORTS                                         NAMES
f394476b0d57   nginx                "/docker-entrypoint.…"   22 minutes ago   Up 22 minutes   0.0.0.0:8081->80/tcp, [::]:8081->80/tcp       my-app2
d6062e49aa18   nginx                "/docker-entrypoint.…"   23 minutes ago   Up 23 minutes   0.0.0.0:8082->80/tcp, [::]:8082->80/tcp       my-app1
5ede0dcadfa7   postgres:15-alpine   "docker-entrypoint.s…"   4 days ago       Up 3 hours      0.0.0.0:5432->5432/tcp, [::]:5432->5432/tcp   postgres-db

=== Testing my-app1 (Port 8082) ===
Welcome to PDD

=== Testing my-app2 (Port 8081) ===
Welcome to PDD official
