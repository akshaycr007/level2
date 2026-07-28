Q1
Configure UFW for SSH, HTTP and HTTPS. Allow SSH only from a specific subnet.



cat << 'EOF' > README.md
1. sudo ufw default deny incoming
2. sudo ufw default allow outgoing
3. sudo ufw allow http
4. sudo ufw allow https
5. sudo ufw allow from 192.168.1.0/24 to any port 22 proto tcp
6. sudo ufw --force enable
7. sudo ufw status verbose

OUTPUT

Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), deny (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
80/tcp                     ALLOW IN    Anywhere                  
443/tcp                    ALLOW IN    Anywhere                  
22/tcp                     ALLOW IN    192.168.50.0/24           
443                        ALLOW IN    Anywhere                  
22/tcp                     ALLOW IN    192.168.1.0/24            
80/tcp (v6)                ALLOW IN    Anywhere (v6)             
443/tcp (v6)               ALLOW IN    Anywhere (v6)             
443 (v6)                   ALLOW IN    Anywhere (v6)             
