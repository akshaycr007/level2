# Question 8: Disk Maintenance Automation

## Objective
Automatically delete files larger than 500MB daily under `/app/appuser/data`.

## Solution Implementation
1. **Cleanup Script (`/app/appuser/clean_large_files.sh`):**
   Utilizes `find /app/appuser/data -type f -size +500M -exec rm -f {} +` to locate and remove target files.
2. **Cron Automation:**
   Configured a user crontab entry `0 0 * * * /app/appuser/clean_large_files.sh` to run every day at midnight.
3. **Verification:**
   Tested with a temporary 520MB file and validated automated deletion in `output.txt`.
