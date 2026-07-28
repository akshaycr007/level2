# Question 8:          
Disk maintenance:
Automatically delete files larger than 500MB daily under /app/appuser/data


# ---------------------------------------------------------
# Step 3: Create the Cleanup Script
# ---------------------------------------------------------
cat << 'EOF' > /app/appuser/clean_large_files.sh
#!/bin/bash
find /app/appuser/data -type f -size +500M -exec rm -f {} +
EOF

chmod +x /app/appuser/clean_large_files.sh

# ---------------------------------------------------------
# Step 4: Schedule Daily Cron Job (At Midnight)
# ---------------------------------------------------------
(crontab -l 2>/dev/null | grep -v "/app/appuser/clean_large_files.sh"; echo "0 0 * * * /app/appuser/clean_large_files.sh") | crontab -

# ---------------------------------------------------------
# Step 5: Test Execution & Generate output.txt
# ---------------------------------------------------------
# Create a dummy test file (> 500MB) to verify cleanup works
fallocate -l 520M /app/appuser/data/test_520M_file.tmp 2>/dev/null || dd if=/dev/zero of=/app/appuser/data/test_520M_file.tmp bs=1M count=520 2>/dev/null

## Objective
Automatically delete files larger than 500MB daily under `/app/appuser/data`.

## Solution Implementation
1. **Cleanup Script (`/app/appuser/clean_large_files.sh`):**
   Utilizes `find /app/appuser/data -type f -size +500M -exec rm -f {} +` to locate and remove target files.
2. **Cron Automation:**
   Configured a user crontab entry `0 0 * * * /app/appuser/clean_large_files.sh` to run every day at midnight.
3. **Verification:**
   Tested with a temporary 520MB file and validated automated deletion in `output.txt`.


OUTPUT

=== Configured Cron Jobs ===
0 0 * * * /app/appuser/clean_large_files.sh

=== Directory Contents BEFORE Cleanup ===
total 521M
drwxrwxrwx 2 appuser appuser 4.0K Jul 27 08:02 app1
drwxrwxrwx 2 appuser appuser 4.0K Jul 27 08:02 app2
-rw-r--r-- 1 appuser appuser   15 Jul 23 07:48 index.html
-rw-rw-r-- 1 appuser appuser 520M Jul 27 12:25 test_520M_file.tmp

=== Directory Contents AFTER Cleanup ===
total 12K
drwxrwxrwx 2 appuser appuser 4.0K Jul 27 08:02 app1
drwxrwxrwx 2 appuser appuser 4.0K Jul 27 08:02 app2
-rw-r--r-- 1 appuser appuser   15 Jul 23 07:48 index.html
