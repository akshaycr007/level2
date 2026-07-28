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



=== User Entry from /etc/passwd ===
appuser:x:1003:1008::/app/appuser:/bin/bash

=== Home Directory Ownership ===
drwxr-x--- 4 appuser appuser 4096 Jul 23 07:48 /app/appuser
