# MySQL_Auto_Backup_Windows
Auto MySQL Backup For Windows Servers By Matt Moeller  v.1.5 - https://www.redolive.com/automated-mysql-backup-for-windows/

PLATFORMS TESTED:
WINDOWS 2008 R2 X64 EN WITH MYSQL 5.5.X,
WINDOWS 2012 SERVER WITH MYSQL 5.6.X,
WINDOWS 2012R2 WITH MYSQL 5.7.X (X64)
WINDOWS SERVER 2016 WITH MYSQL 5.7.X AND NEWER (X64)
WINDOWS SERVER 2019 WITH MYSQL 5.7.X AND MYSQL 8.0.X (X64)

FEATURES:
NO COST DIY SOLUTION
BACKUP ALL MYSQL DATABASES, INCLUDING ALL NEWLY CREATED ONES AUTOMATICALLY
CREATE AN INDIVIDUAL .SQL FILE FOR EACH DATABASE (GOD SEND WHEN RESTORING)
ZIP ALL THE .SQL FILES INTO ONE ZIP FILE AND DATE/TIMESTAMP THE FILE NAME TO SAVE SPACE
AUTOMATICALLY DELETE MYSQL BACKUPS OLDER THAN N DAYS (SET TO HOWEVER MANY DAYS YOU LIKE)
FTP YOUR BACKUP ZIP TO A REMOTE LOCATION
HIGHLY SUGGEST YOU ALSO SETUP A SCHEDULED TASK TO BACKUP YOUR MYSQL DIRECTORY AND YOUR NEW BACKUP FOLDER TO AN OFF SITE LOCATION

Extract the zip and then place the 'MySQLBackups' folder on C:\.  It contains everything you need.  Continue setup below.

SETUP INSTRUCTIONS:
1. Right click and edit mysqlbackup.bat file in notepad
2. Set the backupdate format, whatever your preference, mine is yyyy-mm-dd-m-s ( I have not tested other variants)
3. Set the root u/p (or user with adequate permissions)
4. Set the MySQL data directory to match your install
5. Set the path to your mysqldump.exe to match your install path
6. Set the destination of the backups should go, make sure there are write permissions obviously
7. Set the path to your zip application with it’s flags/commands to zip an item, I am using the command line version of 7zip which is free.
8. Update the path where your backups will be saved and then deleted once zipped
9. Set the number of days to keep backups, using the win program “Forfiles” for this, mine is set to 30 days “-30”
10. Test your batch file on a dummy directory. You’ll see the backup directory fill up with .sql files, then a timestamped zip file is made, and the directory is cleared. 
    Put some files older than 30 days in there and they will be wiped at the end.
11. Finally create a scheduled task in windows to run the batch file on a schedule, remember to choose “Run whether user is logged on or not” otherwise it will fail.
 

Basic Troubleshooting tips:

IMPORTANT NOTE:
UPDATED 3.14.2013 IF YOU GET AN ERROR IN THE COMMAND PROMPT STATING “MYSQLDUMP: UNKOWN OPTION ‘–NO-BEEP’ THIS IS DUE TO YOUR MY.INI FILE HAVING AN INVALID OPTION UNDER [CLIENT]. 
OPEN YOUR MY.INI FILE FIND THE [CLIENT] SECTION AND COMMENT OUT #NO-BEEP WITH A HASH, RE-RUN THE BAT FILE AND IT WILL WORK. THIS ERROR HAS NOTHING TO DO WITH THIS SCRIPT, 
YOU’D GET THE SAME ERROR IF YOU RAN MYSQLDUMP.EXE DIRECTLY. I BELIEVE THAT MYSQL ADMIN ADDS THAT LINE TO THE INI FILE WHEN INSTALLED, THANKS ORACLE.
80% OF THE “DIDN’T WORK FOR ME” ISSUES TEND TO BE RESOLVED BY TRIPLE CHECKING THAT YOUR DIRECTORY PATHS EXIST AND ARE CORRECT.
