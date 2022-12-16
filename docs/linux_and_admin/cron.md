# Cron and Anacron

---

## Table of Contents

- [Basics](#basics)
- [Shortcuts](#shortcuts)
- [Links](#links)

---

## Basics

1. Create .sh file with necessary commands to be executed in bash.
    ```bash
    touch file.sh
    ```
2. Remember to chmod of said file to executable using.
    ```bash
    chmod +x /pathto/file.sh
    ```

3. Check if cronjob is running by printing out errors in system.
    ```bash
    crontab -e
    * * * * * /path to/file.sh > /path to spool/cron.log 2>&1
    ```
--- 
## Shortcuts

- preferred way of organizing cronjobs is by executing .sh files via crontab
- 

---
## Links

- [basic setup](https://www.digitalocean.com/community/tutorials/how-to-schedule-routine-tasks-with-cron-and-anacron-on-a-vps)

 - [linux shortcuts](https://www.digitalocean.com/community/tutorials/linux-commands)

 - [cronjob timing syntax](https://www.thegeekdiary.com/10-useful-cron-examples-to-schedule-jobs-in-linux/)