# Archiving and Logging Data


## Step 1: Create, Extract, Compress, and Manage tar Backup Archives

1. Command to extract the TarDocs.tar archive to the current directory:
- tar xvf TarDocs.tar    

![](/Linux/Images/ALD-1.1-extract.png)

2. Command to create the Javaless_Doc.tar archive from the TarDocs/ directory, while excluding the TarDocs/Documents/Java directory:
- tar -cvf Javaless_Doc.tar --exclude TarDocs/Documents/Java TarDocs

![](/Linux/Images/ALD-1.2-create-archive.png)

3. Command to ensure Java/ is not in the new Javaless_Docs.tar archive:
- tar tvf Javaless_Docs.tar | grep Java

![](/Linux/Images/ALD-1.3-confirm.png)

4. Bonus
- Command to create an incremental archive called logs_backup_tar.gz with only changed files to snapshot.file for the /var/log directory:
  - sudo tar -cvf –listed-incremental= snapshot.file logs_backup_tar.gz /var/log

- Critical Analysis Question
  - Why wouldn't you use the options -x and -c at the same with tar?
    - -x is extract and -c is create   - so you’ll undo what you just did

________________


## Step 2: Create, Manage, and Automate Cron Jobs

1. Cron job for backing up the /var/log/auth.log file:
- crontab -e
- 0 6 * * 3 tar czf ~/TarDocs/auth_backup.tgz /var/log/auth.log

![](/Linux/Images/ALD-2.1-chron.png)
________________


## Step 3: Write Basic Bash Scripts
1. Brace expansion command to create the four subdirectories:
- mkdir -p ~/backups/{freemem,diskuse,openlist,freedisk}

![](/Linux/Images/ALD-3.1-brace-exp.png)

2. Paste your system.sh script edits below:

![](/Linux/Images/ALD-3.2-nano.png)


3. Command to make the system.sh script executable:
- chmod +x system.sh

![](/Linux/Images/ALD-3.3-make-executable.png)

________________


## Step 4: Perform Various Log Filtering Techniques
1. Command to return journalctl messages with priorities from emergency to error:
- journalctl -b -p emerg..err

![](/Linux/Images/ALD-4.1-return-journalctl.png)

2. Command to check the disk usage of the system journal unit since the most recent boot:
- journalctl -b -u systemd-journald | less


![](/Linux/Images/ALD-4.2-check-disk-usage.png)

3. Command to remove all archived journal files except the most recent two:
- sudo journalctl --vacuum-files=2


![](/Linux/Images/ALD-4.3-remove-files.png)


________________


## Step 5. Create Priority-Based Log Files
1. Command to record all mail log messages, except for debug, to /var/log/mail.log:
- Add the edits made to the configuration file below:
  - sudo nano /etc/rsyslog.d/50-default.conf

![](/Linux/Images/ALD-5.1-record-logs.png)

________________


## Step 6. Manage Log File Sizes
1. Run sudo nano /etc/logrotate.conf to edit the logrotate configuration file.

2. Configure a log rotation scheme that backs up authentication messages to the /var/log/auth.log.
- Add your config file edits below:
  - sudo nano /etc/logrotate.conf

  - /var/log/auth.log {
    weekly
    rotate 7
    notifempty
    delaycompression
    mssingok
}    

![](/Linux/Images/ALD-6.1-nano.png)

![](/Linux/Images/ALD-6.1-log-rotations.png)
