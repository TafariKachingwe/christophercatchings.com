---

layout: post

author: softwareshinobi

title:  "Shinobi Tech Jutsu / Backup Wordpress Server"

categories: [Data Management, Disaster Recovery Automation]

tags: [ Bash Scripting, Backups, Manual Backup, Cron Automation, Docker]

image: assets/imagery/covers/jhbtzied.jpg

description: "With this script and Cron as your allies, you'll have a fortress of data protection!  In the next article, we'll delve deeper into Cron scheduling and explore other automation strategies to make your coding life even sweeter."

hidden: false

---

Dev Team Six attemble. Back at it again with a bach script. a manual backup script that'll keep your precious projects safe and sound. This bad boy isn't just a one-time hero, though. We can integrate it with Cron for ultimate automation, making backups a breeze!

## The Script Breakdown:

Let's dissect this script line by line and see how it orchestrates your digital defense:

```bash
#!/bin/bash

set -e
set -x
```

- **Shell Specifier:** This line tells the system to use the Bash interpreter to run the script.

- **Error Handling:**  `set -e` is a champion – it throws an error if any command in the script fails, preventing you from unknowingly creating a faulty backup.

- **Verbose Mode:** `set -x` is your debugging buddy. It echoes each command and its arguments as it runs, making troubleshooting a snap (though you might want to disable it for regular backups for a cleaner experience).

## The Backup Battlefield

```bash
##

currentDirectory=`pwd`

currentFutureDirectoryName="planeto-saturno-backup"

backupDirectory="/backups/"

##
```

- **Grabbing Your Location:** `pwd` captures the current working directory, storing it in the `currentDirectory` variable for later use.
- **Backup Directory Blueprint:** We define the desired name for the compressed backup file (`currentFutureDirectoryName`) and the directory path where we'll store it (`backupDirectory`).  "Planeto-Saturno-backup" sounds pretty epic, don't you think? 


## Docker Deconstruction

```bash
docker-compose down --remove-orphans

##
```

- **Docker Downtime (Optional):**  This line (assuming you're using Docker) gracefully shuts down your containers using `docker-compose down`. The `--remove-orphans` flag eliminates any lingering orphaned containers, keeping things clean.  If you're not using Docker, simply remove this line.

**Backup Basecamp:**

```bash
cd ..

mkdir -p $backupDirectory
```

- **Directory Navigation:** We cleverly use `cd ..` to navigate one level up in the directory hierarchy.
- **Backup Directory Creation (if needed):** The `mkdir -p $backupDirectory` command checks if the backup directory exists. If not, it creates it – a handy safeguard. The `-p` flag ensures any parent directories are also created if necessary.

## Zipping Up for Security

```bash
zip $backupDirectory/$currentFutureDirectoryName-`date --iso`.zip $currentDirectory -r

cd $currentDirectory
```

- **Compression Crusade:** The `zip` command takes center stage. It creates a ZIP archive named `$currentFutureDirectoryName-` followed by the current date in ISO format (using `date --iso`). The archive includes the entire contents of the `currentDirectory` (represented by `$currentDirectory`) recursively (`-r` flag).
- **Back to Base:** `cd $currentDirectory` navigates back to your original working directory, keeping things tidy.

## Bringing it Back Up

```bash
bash compose.bash
```

- **Recompose (Optional):** If you're using Docker, this line (assuming you have a `compose.bash` script) brings your containers back online after the backup. 

## Cron Automation: Your Backup Butler

Now, for the real magic trick!  Want to automate this script to run regularly? Cron is your secret weapon. Here's an example:

```
0 0 * * * /path/to/your/script.sh  >> /var/log/backup.log 2>&1
```

This line tells Cron to run your script (`/path/to/your/script.sh`) every day (0 0) at midnight (* * *). The `>> /var/log/backup.log 2>&1` redirects both standard output and standard error to a log file (`/var/log/backup.log`), allowing you to monitor the backup process.

## The Whole Script

```
#!/bin/bash

set -e

set -x

##

currentDirectory=`pwd`

currentFutureDirectoryName="automated-server-backup"

backupDirectory="/backups/"

##

docker-compose down --remove-orphans

##

cd ..

mkdir -p $backupDirectory

##

zip $backupDirectory/$currentFutureDirectoryName-`date --iso`.zip $currentDirectory -r

cd $currentDirectory

bash compose.bash

```