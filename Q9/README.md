# Question 9: question.txt
Create cron job (2 AM daily):
o Backup /var/log to /backup
o Create tar archive with date
EOF

# ---------------------------------------------------------
# Step 2: Create question.txt
# ---------------------------------------------------------
cat << 'EOF' > question.txt
Create cron job (2 AM daily):
o Backup /var/log to /backup
o Create tar archive with date
EOF

# ---------------------------------------------------------
# Step 3: Create the Log Backup Script
# ---------------------------------------------------------
sudo bash -c 'cat << "EOF" > /app/appuser/backup_logs.sh
#!/bin/bash
BACKUP_DIR="/backup"
DATE=$(date +%Y-%m-%d)
ARCHIVE_NAME="log_backup_${DATE}.tar.gz"

mkdir -p "$BACKUP_DIR"
tar -czf "${BACKUP_DIR}/${ARCHIVE_NAME}" /var/log 2>/dev/null
EOF'

sudo chmod +x /app/appuser/backup_logs.sh

# ---------------------------------------------------------
# Step 4: Schedule Daily Cron Job at 2:00 AM (0 2 * * *)
# ---------------------------------------------------------
(crontab -l 2>/dev/null | grep -v "/app/appuser/backup_logs.sh"; echo "0 2 * * * /app/appuser/backup_logs.sh") | crontab -

# Also configure in root's crontab to handle restricted log file permissions
(sudo crontab -l 2>/dev/null | grep -v "/app/appuser/backup_logs.sh"; echo "0 2 * * * /app/appuser/backup_logs.sh") | sudo crontab -


## Objective
Schedule a daily cron job at 2:00 AM to archive `/var/log` into `/backup` as a date-stamped `tar` archive.

## Implementation Details
1. **Backup Script (`/app/appuser/backup_logs.sh`):**
   Archives `/var/log` to `/backup/log_backup_YYYY-MM-DD.tar.gz` using gzip compression.
2. **Cron Schedule:**
   Configured cron schedule `0 2 * * * /app/appuser/backup_logs.sh` to run every day at 02:00 AM.
3. **Verification:**
   Tested manual execution and confirmed output archive created in `/backup`.
