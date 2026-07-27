1. mkdir -p /app/appuser/data/app1 /app/appuser/data/app2
2. echo "Welcome to PDD" > /app/appuser/data/app1/index.html
3. echo "Welcome to PDD official" > /app/appuser/data/app2/index.html
4. sudo docker run -d --name my-app1 -p 8082:80 -v /app/appuser/data/app1:/usr/share/nginx/html nginx
5. sudo docker run -d --name my-app2 -p 8081:80 -v /app/appuser/data/app2:/usr/share/nginx/html nginx
6. curl http://localhost:8082
7. curl http://localhost:8081
