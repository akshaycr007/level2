Q3
Create user:
- Username: appuser
- Password: appuser
- Home directory: /app/appuser

1. sudo mkdir -p /app
2. sudo useradd -m -d /app/appuser appuser
3. echo "appuser:appuser" | sudo chpasswd
4. getent passwd appuser
5. ls -ld /app/appuser
