akshay@servera:~$ sudo mkdir -p /app/appuser/data
akshay@servera:~$ cat << 'EOF' > /app/appuser/clean_large_files.sh
#!/bin/bash
find /app/appuser/data -type f -size +500M -exec rm -f {} +
EOF

chmod +x /app/appuser/clean_large_files.sh
akshay@servera:~$ (crontab -l 2>/dev/null; echo "0 0 * * * /app/appuser/clean_large_files.sh") | crontab -
akshay@servera:~$ crontab -e

Select an editor.  To change later, run 'select-editor'.
  1. /bin/nano        <---- easiest
  2. /usr/bin/vim.basic
  3. /usr/bin/vim.tiny
  4. /bin/ed

Choose 1-4 [1]: ^C^C^C^C^C^C
crontab: installing new crontab
akshay@servera:~$ crontab -e
No modification made
akshay@servera:~$ fallocate -l 520M /app/appuser/data/test_520M_file.tmp 2>/dev/null || dd if=/dev/zero of=/app/appuser/data/test_520M_file.tmp bs=1M count=520 2>/dev/null
akshay@servera:~$ ls -lh /app/appuser/data
total 521M
drwxrwxr-x 2 akshay akshay 4.0K Jul 27 06:44 app1
drwxrwxr-x 2 akshay akshay 4.0K Jul 27 06:44 app2
-rw-r--r-- 1 akshay akshay   15 Jul 23 07:48 index.html
-rw-rw-r-- 1 akshay akshay 520M Jul 28 11:08 test_520M_file.tmp
akshay@servera:~$ /app/appuser/clean_large_files.sh
akshay@servera:~$ ls -lh /app/appuser/data
total 12K
drwxrwxr-x 2 akshay akshay 4.0K Jul 27 06:44 app1
drwxrwxr-x 2 akshay akshay 4.0K Jul 27 06:44 app2
-rw-r--r-- 1 akshay akshay   15 Jul 23 07:48 index.html
