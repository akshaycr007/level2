# Question 9: Automated Daily Log Backup

## Objective
Schedule a daily cron job at 2:00 AM to archive `/var/log` into `/backup` as a date-stamped `tar` archive.

## Implementation Details
1. **Backup Script (`/app/appuser/backup_logs.sh`):**
   Archives `/var/log` to `/backup/log_backup_YYYY-MM-DD.tar.gz` using gzip compression.
2. **Cron Schedule:**
   Configured cron schedule `0 2 * * * /app/appuser/backup_logs.sh` to run every day at 02:00 AM.
3. **Verification:**
   Tested manual execution and confirmed output archive created in `/backup`.
