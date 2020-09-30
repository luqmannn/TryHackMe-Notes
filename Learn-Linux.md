# Learn Linux
A guided room designed to teach you the Linux basics!

## Tasks

### Basic File Operations
1. What flag outputs all entries: **-a**
2. What flag outputs things in a "long list" format: **-l**
3. What flag numbers all output lines?: **-n**
4. How would you run a binary called hello using the directory shortcut .?: **./hello**
5. How would you run a binary called hello in your home directory using the shortcut ~ ?: **~/hello**
6. How would you run a binary called hello in the previous directory using the shortcut .. ?: **../hello**

### Binary - Shiba1
- What's the password for shiba2?: **pinguftw**

### Su
1. How do you specify which shell is used when you login?: **-s**

### Linux operator '>'
1. How would you output twenty to a file called test: **echo twenty > test**

### Linux operator '$'
1. How would you set nootnoot equal to 1111: **export nootnoot=1111**
2. What is the value of the home environment variable: **/home/shiba2**

### Binary - Shiba2
- What is shiba3's password: **happynootnoises**

### Advanced File Operations: chmod
1. What permissions mean the user can read the file, the group can read and write to the file, and no one else can read, write or execute the file?: **460**
2. What permissions mean the user can read, write, and execute the file, the group can read, write, and execute the file, and everyone else can read, write, and execute the file? **777**

### Advanced File Operations: chown
1. How would you change the owner of file to paradox: **chown paradox file**
2. What about the owner and the group of file to paradox: **chown paradox:paradox file**
3. What flag allows you to operate on every file in the directory at once?: **-R**

### Advanced File Operations: rm
1. What flag deletes every file in a directory: **-r**
2. How do you suppress all warning prompts: **-f**

### Advanced File Operations: mv
1. How would you move file to /tmp: **mv file /tmp**

### Advanced File Operations: cd && mkdir
1. Using relative paths, how would you cd to your home directory: **cd ~**
2. Using absolute paths how would you make a directory called test in /tmp: **mkdir /test /tmp**

### Advanced File Operations: ln
1. How would I link /home/test/testfile to /tmp/test: **ln /home/test/testfile /tmp/test**

### Advanced File Operations: find
1. How do you find files that have specific permissions?: **-perm**
2. How would you find all the files in /home: **find /home**
3. How would you find all the files owned by paradox on the whole system: **find / -user paradox**

### Advanced File Operations: grep
1. What flag lists line numbers for every string found?: **-n**
2. How would I search for the string boop in the file aaaa in the directory /tmp: **grep boop /tmp /aaaa**

### Binary - Shiba3
- What is shiba4's password: **test1234**

### Miscellaneous - sudo
1. How do you specify which user you want to run a command as: **-u**
2. How would I run whoami as user jen?: **sudo -u jen whoami**
3. How do you list your current sudo privileges (what commands you can run, who you can run them as etc.): **-l**

### Miscellaneous - Adding users and groups
1. How would I add the user test to the group test: **sudo usermod -a -G test, test**

### Bonus Challenge - True Ending
-  Finish this room off! What is the root.txt flag?: ****

### Users password
- shiba1 - shiba1
- shiba2 - pinguftw
- shiba3 - happynootnoises
- shiba4 - test1234