# Question 1: System Update, Upgrade & Cleanup

## Objective
Update the package repository, upgrade all installed packages to their latest versions, and remove unused dependencies from the system.

## Steps Executed

1. **Update Package Lists**
   * **Command:** `sudo apt update`
   * **Description:** Refreshes the local database of available packages and their versions from remote repositories.

2. **Upgrade Installed Packages**
   * **Command:** `sudo apt upgrade -y`
   * **Description:** Downloads and installs available updates for all currently installed system packages.

3. **Remove Unused Packages**
   * **Command:** `sudo apt autoremove -y`
   * **Description:** Cleans up orphan packages and dependencies that were automatically installed but are no longer needed.



OUTPUT

akshay@servera:~/level2/Q1$ sudo apt update | tee output.txt
[sudo] password for akshay:

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

Hit:1 https://cli.github.com/packages stable InRelease
Hit:2 https://archive.ubuntu.com/ubuntu noble InRelease
Hit:3 https://archive.ubuntu.com/ubuntu noble-updates InRelease
Hit:4 https://archive.ubuntu.com/ubuntu noble-backports InRelease
Hit:5 https://archive.ubuntu.com/ubuntu noble-security InRelease
Reading package lists...
Building dependency tree...
Reading state information...
6 packages can be upgraded. Run 'apt list --upgradable' to see them.
akshay@servera:~/level2/Q1$ nano output.txt
akshay@servera:~/level2/Q1$ nano output.txt
  GNU nano 7.2                                              output.txt
Hit:1 https://cli.github.com/packages stable InRelease
Hit:2 https://archive.ubuntu.com/ubuntu noble InRelease
Hit:3 https://archive.ubuntu.com/ubuntu noble-updates InRelease
Hit:4 https://archive.ubuntu.com/ubuntu noble-backports InRelease
Hit:5 https://archive.ubuntu.com/ubuntu noble-security InRelease
Reading package lists...
Building dependency tree...
Reading state information...
6 packages can be upgraded. Run 'apt list --upgradable' to see them.

Hit:2 https://archive.ubuntu.com/ubuntu noble InRelease
Hit:3 https://archive.ubuntu.com/ubuntu noble-updates InRelease
Hit:4 https://archive.ubuntu.com/ubuntu noble-backports InRelease
Hit:5 https://archive.ubuntu.com/ubuntu noble-security InRelease
Reading package lists...
Building dependency tree...
Reading state information...
6 packages can be upgraded. Run 'apt list --upgradable' to see them.

Reading package lists...
Building dependency tree...
Reading state information...
Calculating upgrade...
The following packages will be upgraded:
  libpam-modules libpam-modules-bin libpam-runtime libpam0g libxpm4 rsyslog
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 standard LTS security updates
Need to get 995 kB of archives.
After this operation, 2,048 B of additional disk space will be used.
Get:1 https://archive.ubuntu.com/ubuntu noble-updates/main amd64 libpam0g amd64 1.5.3-5ubuntu5.6 [68.0 kB]
Get:2 https://archive.ubuntu.com/ubuntu noble-updates/main amd64 libpam-modules-bin amd64 1.5.3-5ubuntu5.6 [51.9 kB]
Get:3 https://archive.ubuntu.com/ubuntu noble-updates/main amd64 libpam-modules amd64 1.5.3-5ubuntu5.6 [286 kB]
Get:4 https://archive.ubuntu.com/ubuntu noble-updates/main amd64 libpam-runtime all 1.5.3-5ubuntu5.6 [40.8 kB]
Get:5 https://archive.ubuntu.com/ubuntu noble-updates/main amd64 rsyslog amd64 8.2312.0-3ubuntu9.3 [511 kB]
Get:6 https://archive.ubuntu.com/ubuntu noble-updates/main amd64 libxpm4 amd64 1:3.5.17-1ubuntu0.24.04.1 [36.7 kB]
Preconfiguring packages ...
Fetched 995 kB in 7s (148 kB/s)
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 150303 files and directories currently installed.)
Preparing to unpack .../libpam0g_1.5.3-5ubuntu5.6_amd64.deb ...
Unpacking libpam0g:amd64 (1.5.3-5ubuntu5.6) over (1.5.3-5ubuntu5.5) ...
Setting up libpam0g:amd64 (1.5.3-5ubuntu5.6) ...
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 150303 files and directories currently installed.)
Preparing to unpack .../libpam-modules-bin_1.5.3-5ubuntu5.6_amd64.deb ...
Unpacking libpam-modules-bin (1.5.3-5ubuntu5.6) over (1.5.3-5ubuntu5.5) ...
Setting up libpam-modules-bin (1.5.3-5ubuntu5.6) ...
pam_namespace.service is a disabled or a static unit not running, not starting it.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 150303 files and directories currently installed.)
Preparing to unpack .../libpam-modules_1.5.3-5ubuntu5.6_amd64.deb ...
Unpacking libpam-modules:amd64 (1.5.3-5ubuntu5.6) over (1.5.3-5ubuntu5.5) ...
Setting up libpam-modules:amd64 (1.5.3-5ubuntu5.6) ...
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 150303 files and directories currently installed.)
Preparing to unpack .../libpam-runtime_1.5.3-5ubuntu5.6_all.deb ...
Unpacking libpam-runtime (1.5.3-5ubuntu5.6) over (1.5.3-5ubuntu5.5) ...
Setting up libpam-runtime (1.5.3-5ubuntu5.6) ...
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 150303 files and directories currently installed.)
Preparing to unpack .../rsyslog_8.2312.0-3ubuntu9.3_amd64.deb ...
Unpacking rsyslog (8.2312.0-3ubuntu9.3) over (8.2312.0-3ubuntu9.2) ...
Preparing to unpack .../libxpm4_1%3a3.5.17-1ubuntu0.24.04.1_amd64.deb ...
Unpacking libxpm4:amd64 (1:3.5.17-1ubuntu0.24.04.1) over (1:3.5.17-1build2) ...
Setting up libxpm4:amd64 (1:3.5.17-1ubuntu0.24.04.1) ...
Setting up rsyslog (8.2312.0-3ubuntu9.3) ...
info: The user `syslog' is already a member of `adm'.
Processing triggers for libc-bin (2.39-0ubuntu8.7) ...
Processing triggers for man-db (2.12.0-4build2) ...

Running kernel seems to be up-to-date.

Restarting services...
 /etc/needrestart/restart.d/systemd-manager
 systemctl restart cron.service ssh.service systemd-journald.service systemd-networkd.service systemd-resolved.service systemd-timesyncd.service

Service restarts being deferred:
 systemctl restart systemd-logind.service

No containers need to be restarted.

User sessions running outdated binaries:
 akshay @ session #1: login[889]
 akshay @ session #19: sshd[32359]
 akshay @ session #20: sshd[32361]
 akshay @ user manager service: systemd[1684]

No VM guests are running outdated hypervisor (qemu) binaries on this host.
