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

## Files in this Directory
* `question.txt` - Contains the lab problem statement.
* `output.txt` - Contains the raw terminal output from running the commands.
* `README.md` - Step-by-step explanation of the lab solution.
