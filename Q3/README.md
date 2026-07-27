1. sudo mkdir -p /app
2. sudo useradd -m -d /app/appuser appuser
3. echo "appuser:appuser" | sudo chpasswd
4. getent passwd appuser
5. ls -ld /app/appuser
