# Cron Jobs

Cron is a time-based job scheduler in Unix-like operating systems, including Linux. It allows users to schedule tasks (commands or scripts) to run automatically at fixed times, dates, or intervals. These tasks are known as **cron jobs**.

## How Cron Works
- **Cron Daemon**: The cron daemon (`crond`) is a background process that runs continuously and checks for scheduled tasks.
- **Crontab Files**: Cron jobs are defined in crontab files. Each user can have their own crontab file, and there is also a system-wide crontab file.
- **Cron Job Syntax**: Each line in a crontab file represents a cron job and follows a specific syntax to define when and how often the task should run.

## Crontab Syntax
A cron job is defined by a line in the crontab file with the following format:

```bash
* * * * * command-to-be-executed
```

The five asterisks (`*`) represent time and date fields in the following order:

| Field            | Values        | Description                               |
|-----------------|--------------|-------------------------------------------|
| Minute          | 0–59         | The minute when the command will run.    |
| Hour           | 0–23         | The hour when the command will run. (24-hour format) |
| Day of the Month | 1–31         | The day of the month when the command will run. |
| Month          | 1–12         | The month when the command will run.     |
| Day of the Week | 0–7          | The day of the week when the command will run. (0 and 7 both represent Sunday) |

## Special Characters in Cron

| Character | Meaning | Example |
|-----------|---------|---------|
| `*` (asterisk) | Matches all values | `* * * * *` (Runs every minute) |
| `,` (comma) | Specifies a list of values | `1,15 * * * *` (Runs on the 1st and 15th minute) |
| `-` (hyphen) | Specifies a range of values | `1-5 * * * *` (Runs from 1st to 5th minute) |
| `/` (slash) | Specifies intervals | `*/10 * * * *` (Runs every 10 minutes) |

## Examples of Cron Jobs

| Command | Description |
|---------|-------------|
| `0 3 * * * /path/to/script.sh` | Run a script every day at 3:00 AM |
| `*/20 * * * * /path/to/command` | Run a command every 20 minutes |
| `0 0 * * 0 /path/to/backup.sh` | Run a backup script every Sunday at midnight |
| `30 6 1 * * /path/to/cleanup.sh` | Run a cleanup script on the 1st of every month at 6:30 AM |
| `0 17 * * 1-5 /path/to/command` | Run a command every weekday (Monday to Friday) at 5:00 PM |
| `30 * * * * /path/to/script.sh` | Run a script every hour at the 30th minute |

## Cron Job File Operations

| Command | Description |
|---------|-------------|
| `crontab -e` | Edit your crontab file |
| `crontab -l` | View your current cron jobs |
| `crontab -r` | Remove all your cron jobs |

## System-Wide Crontab
System-wide cron jobs are typically defined in `/etc/crontab` or in files inside the `/etc/cron.d/` directory. These files have an additional field for the user under which the command should run:

```bash
* * * * * username /path/to/command
```

Linux provides directories for easier scheduling of tasks:

| Directory | Description |
|-----------|-------------|
| `/etc/cron.hourly/` | Scripts placed here run every hour. |
| `/etc/cron.daily/` | Scripts placed here run once a day. |
| `/etc/cron.weekly/` | Scripts placed here run once a week. |
| `/etc/cron.monthly/` | Scripts placed here run once a month. |

You can place your scripts in these directories, and they will be executed automatically at the specified intervals.

## Logging and Debugging Cron Jobs
- **Cron Logs**: Cron logs are typically stored in `/var/log/syslog` or `/var/log/cron`. You can check these logs to debug issues with your cron jobs.

```bash
grep CRON /var/log/syslog
```

## Example:
```sh
dhyanesh@dhyanesh-ThinkPad-T14s-Gen-1:~/Desktop$ crontab -l
# Edit this file to introduce tasks to be run by cron.
# 
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
# 
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').
# 
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
# 
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
# 
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
# 
# For more information see the manual pages of crontab(5) and cron(8)
# 
# m h  dom mon dow   command
*/1 * * * * echo "New New" >> ~/Desktop/file_by_cron.txt
```
This appends "New New" at te end of the file.