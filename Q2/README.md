cat << 'EOF' > README.md
1. sudo ufw default deny incoming
2. sudo ufw default allow outgoing
3. sudo ufw allow http
4. sudo ufw allow https
5. sudo ufw allow from 192.168.1.0/24 to any port 22 proto tcp
6. sudo ufw --force enable
7. sudo ufw status verbose
