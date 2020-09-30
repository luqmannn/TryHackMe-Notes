# Linux Challenges
Learn by completing linux challenges. This rooms purpose is to learn or improve your Linux skills.

## Linux Challenges Introduction
1. How many visible files can you see in garrys home directory?
- Use `ls` command

## The Basics
This set of tasks will go over the basic linux commands. Each question might require you to switch between another user to find the answer!
1. What is flag 1? **cat flag1.txt**
2. Log into bob's account using the credentials shown in flag 1. What is flag 2? **su bob, locate flag2, cat /home/bob/flag2.txt**
3. Flag 3 is located where bob's bash history gets stored. **cat ~/.bash_history**
4. Flag 4 is located where cron jobs are created. **crontab -e**
5. Find and retrieve flag 5. **locate flag5, cat /lib/terminfo/E/flag5.txt**
6. "Grep" through flag 6 and find the flag. The first 2 characters of the flag is c9. **locate flag6, cat /home/flag6.txt | grep c9**
7. Look at the systems processes. What is flag 7. **ps -aux | grep flag7**
8. De-compress and get flag 8. **locate flag8, tar -xvf /home/bob/flag8.tar.gz, cat flag8.txt**
9. By look in your hosts file, locate and retrieve flag 9. **cat /etc/hosts**
10. Find all other users on the system. What is flag 10. **cat /etc/passwd**

## Linux Functionality
Now we have used the basic Linux commands to find the first 10 flags, we will move onto using more functions that Linux has to offer.
1. Run the command flag11. Locate where your command alias are stored and get flag 11. **flag11, cat ~/.bashrc | grep flag11**
2. Flag12 is located were MOTD's are usually found on an Ubuntu OS. What is flag12? **cat /etc/update-motd.d/00-header**
3. Find the difference between two script files to find flag 13. **locate flag13, cd /home/bob, diff script1 script2**
4. Where on the file system are logs typically stored? Find flag 14. **cd /var/log/, less flagtourteen.txt, End key**
5. Can you find information about the system, such as the kernel version etc. Find flag 15. `cat /etc/*release`
6. Flag 16 lies within another system mount. `cd /media/, ls -R */`
7. Login to alice's account and get flag 17. Her password is TryHackMe123 **locate flag17, cat /home/alice/flag17**
8. Find the hidden flag 18. **locate flag18, cat /home/alice/.flag18**
9. Read the 2345th line of the file that contains flag 19. **sed -n 2345p /home/alice/flag19**

## Data Representation, Strings and Permission
This set of tasks will require you to understand how certain data is represented on a Linux system. This section may require you to do some independent research.
1. Find and retrieve flag 20. **locate flag20, cat /home/alice/flag20, echo 'replacewithstringinsideflag20' | base64 -d**
2. Inspect the flag21.php file. Find the flag. **locate flag21, less /home/bob/flag21.php**
3. Locate and read flag 22. Its represented as hex. **locate flag22, cat /home/alice/flag22 | xxd -r -p**
4. Locate, read and reverse flag 23. **locate flag23, cat /home/alice/flag23 | rev**
5. Analyse the flag 24 compiled C program. Find a command that might reveal human readable strings when looking in the source code. **locate flag24, strings /home/garry/flag24 | grep flag**
6. Flag 25 does not exist.
7. Find flag 26 by searching the all files for a string that begins with 4bceb and is 32 characters long. `find / -xdev -type f -print0 2>/dev/null | xargs -0 grep -o "4bceb[a-z0-9]\{27\}" 2>/dev/null`
8. Locate and retrieve flag 27, which is owned by the root user. **sudo -l, sudo cat /home/flag27**
9. Whats the linux kernel version? **uname -r**
10. Find the file called flag 29 and do the following operations on it:
    Remove all spaces in file.
    Remove all new line spaces.
    Split by comma and get the last element in the split.
	```
	locate flag29, cat /home/garry/flag29 | tr -d ' '
	```

## SQL, FTP, Groups and RDP
This task will have you finding flags in an SQL database, downloading files from the file system to your local system and more!
1. Use curl to find flag 30. **curl localhost**
2. Flag 31 is a MySQL database name.
	MySQL username: root
	MySQL password: hello
	```
	mysql -u root -p -e "show databases;"
	```
3. Bonus flag question, get data out of the table from the database you found above! 
```
mysql -u root -p
use database_2fb1cab13bf5f4d61de3555430c917f4;
show tables;
select * from flags;
```
4. Using SCP, FileZilla or another FTP client download flag32.mp3 to reveal flag 32. **find / -name flag32.mp3, sshpass -p "TryHackMe123" scp -r alice@10.10.167.164:flag32.mp3**
5. Flag 33 is located where your personal $PATH's are stored. **find /home -name .profile -print0 2>/dev/null | xargs -0 grep -i "flag" 2>/dev/null**
6. Switch your account back to bob. Using system variables, what is flag34? **su bob, printenv | grep flag**
7. Look at all groups created on the system. What is flag 35? **cat /etc/group | grep flag**
8. Find the user which is apart of the "hacker" group and read flag 36. **locate flag36, cat /etc/flag36**
