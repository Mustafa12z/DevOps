# OverTheWire Bandit Solutions

---

## Table of Contents

- [Level 0](#level-0)
- [Level 0-1](#level-0-1)
- [Level 1-2](#level-1-2)
- [Level 2-3](#level-2-3)
- [level 3-4](#level-3-4)
- [Level 4-5](#level-4-5)
- [Level 5-6](#level-5-6)
- [Level 6-7](#level-6-7)
- [Level 7-8](#level-7-8)
- [Level 8-9](#level-8-9)
- [Level 9-10](#level-9-10)
- [Level 10-11](#level-10-11)
- [Level 11-12](#level-11-12)

---

## Level 0

### The Goal

The goal of this level is for you to log into the game using SSH. The host to which you need to connect is `bandit.labs.overthewire.org`, on port `2220`. The username is `bandit0` and the password is `bandit0`. Once logged in, go to the Level 1 page to find out how to beat Level 1.

---

### The Solution

SSH is a method of logging into secure network servers from unsecure networks. In this case, we have been provided:

- **Username**: `bandit0`
- **Host server**: `bandit.labs.overthewire.org`
- **Port number**: `2220` (non-default port for enhanced security)
- **Password**: `bandit0`

To log in, we execute the following command:

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```


After executing this command, you will be prompted to enter the password, which is bandit0.

Once successfully logged in, you will be inside the server and can proceed to solve the next level!

--- 

## Level 0-1

### The Goal

The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

---

### The Solution

The commands that will be used in this level are:

- `ls`: Lists files and directories in the current directory.
- `cat`: Displays the text output of a file.

In this level, I first used the `ls` command to list the files in the home directory:

```bash
ls
```

Then, I used the cat command to read the contents of the readme file, which contained the password for the next level:

```bash
cat readme
```

This command displayed the password needed to proceed to the next level.

---

## Level 1-2

### The Goal

The password for the next level is stored in a file called - located in the home directory

---

### The solution

The commands that will be used in this level are:

- `ls`: Lists files and directories in the current directory.
- `cat`: Displays the text output of a file.

Just like in the previous level, I first used the `ls` command to list the files in the home directory:

```bash
ls
```

The output given here would be a file called -. Since - is used as a special character for options in Linux commands, we need to specify the full path to indicate that we are referencing the file. Therefore, the command would look like this:

```bash
cat ./-
```

After executing that command, we would have succcessfully got the password and can move onto the next level!

---

## Level 2-3

### The Goal

The password for the next level is stored in a file called spaces in this filename located in the home directory

---

### The Solution

The commands that will be used in this level are:

- `ls`: Lists files and directories in the current directory.
- `cat`: Displays the text output of a file.

In this level, I first used the `ls` command to list the files in the home directory:

``` bash
ls
```

After executing that command, there will be a file named spaces in this filename. Due to the fact that there are spaces in the filename, we cannot use the simple cat command directly with the filename, as that would result in an error. Instead, we need to put the filename in quotes so that Linux recognises we are referencing that specific file. This is what the command would look like:

```bash
cat 'spaces in this filename'
```

After executing the command you will successfuly get the password and can move onto the next level!

---

## Level 3-4

### The Goal

The password for the next level is stored in a hidden file in the inhere directory.

---

### The Solution

The commands that will be used in this level are:

- `ls`: Lists files and directories in the current directory.
- `cat`: Displays the text output of a file.
- `cd`: Changes the current directory.

First, I used the `cd` command to navigate into the `inhere` directory, where the hidden file is located.

```bash
cd inhere
```

After that, I used the `ls -a` command to view all files, including hidden ones. 
The `-a` option tells `ls` to show all files, including those that start with a dot (`.`), which are hidden by default. This will help us locate the hidden file.

```bash
ls -a
```

Once I found the hidden file, I used the `cat` command to open and read its contents. The file's name starts with three dots (`...`), indicating that it is hidden. To reference this hidden file correctly, I included the dots in the command like this: 

```bash
cat ...Hiding-From-You
```

After executing the `cat` command, I successfully retrieved the password and can now move on to the next level!

---

## Level 4-5

### The Goal

The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

---
### The Solution


The commands that will be used in this level are:

- `ls`: Lists files and directories in the current directory.
- `cat`: Displays the text output of a file.
- `cd`: Changes the current directory.
- `file`: Shows the type of a specified file.

First, I used the `cd` command to navigate into the `inhere` directory, where the file is located.

```bash
cd inhere
```

After navigating to the `inhere` directory, I used the `ls` command to list all the files present. I noticed that there were 10 different files, all starting with a hyphen (`-`). This is important because filenames starting with a hyphen can be interpreted as options by commands.

Next, I used the `file` command to determine which of these files contained ASCII text, indicating a human-readable format. To check the types of all the files in the directory, I executed the following command:

```bash
file ./*
```
This command lists the types of all files in the current directory. The output indicated that -file07 is the file with the human-readable format.

I used the cat command to open and read the contents of that file.

```bash
cat ./-file07
```

(^1) Tip: When dealing with filenames that start with special characters like -, always specify the full path (like ./-file07) to avoid confusion with command options.

After executing the cat command, I successfully retrieved the password and can now move on to the next level!

---

## Level 5-6

### The Goal

The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

human-readable
1033 bytes in size
not executable

---
### The Solution

The commands that will be used in this level are:

- `ls`: Lists files and directories in the current directory.
- `cat`: Displays the text output of a file.
- `cd`: Changes the current directory.
- `file`: Shows the type of a specified file.
- `find`: Allows the user to search for a specific file

First, I used the `cd` command to navigate into the `inhere` directory, where the file is located.

```bash
cd inhere
```

Once entering this directory i was met with 20 directories with the maybehere directory name. I used the `find` command to locate the file with the specified criteria

```bash
find -type f -size 1033c 
```

`-type f` here indicates it will be looking for files and `-size 1033c` indicates it will be looking for files that are 1033 bytes in size

The find command located the file at ./maybehere07/.file2.

To read the contents of this file and retrieve the password, I used the cat command:

```bash
cat ./maybehere07/.file2
```

After doing this you will have successfully obtained the password and can move onto the level!

---

## Level 6-7

### The Goal

The password for the next level is stored somewhere on the server and has all of the following properties:

owned by user bandit7
owned by group bandit6
33 bytes in size

---
### The Solution

The commands that will be used in this level are:

- `cat`: Displays the text output of a file.
- `cd`: Changes the current directory.
- `find`: Allows the user to search for a specific file

First we use the `find` command to search for the file in the criteria specified.

```bash
find / -size 33c -group bandit6 -user bandit7
```

This command located the file at /var/lib/dpkg/info/bandit7.password.

The final step is to use the cat command to read the contents of the file and get the password

```bash
cat /var/lib/dpkg/info/bandit7.password
```

After executing that command you will have successfully obtained the password and can move onto the next level!

---

## Level 7-8

### The Goal

The password for the next level is stored in the file data.txt next to the word millionth

---
### The Solution

The commands that will be used in this level are:

- `grep`: Searches for patterns in files.

For this level, we need to use the `grep` command to find the word **millionth** in the file `data.txt`, as the password is located next to that word.

To search for the word **millionth** in the `data.txt` file, I used the following command:

```bash
grep "millionth" data.txt
```

Here’s what the command does:

- `grep`: Searches for patterns in a file.
- `"millionth"`: This is the word we’re looking for.
- `data.txt`: This is the file where the word is stored.


After running this command, `grep` finds the line containing **millionth** and returns it along with the password.

```bash
millionth   dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```
Once obtaining the password, you can move onto the next level!

---

## Level 8-9

### The Goal

The password for the next level is stored in the file `data.txt` and is the only line of text that occurs once.

---
### The Solution

The commands that will be used in this level are:

- `sort`: Sorts lines of text files.
- `uniq`: Filters out repeated lines from a sorted file.

First, I used the `sort` command to sort the contents of `data.txt`. This ensures that all identical lines are grouped together.

Next, I paired the sort command with the `uniq` command with the `-u` option, which filters out all lines except those that appear exactly once.

```bash
sort data.txt | uniq -u
```

- `sort data.txt`: Sorts the lines in `data.txt`.
- `uniq -u`: Filters out all duplicate lines, leaving only the line that occurs once (i.e., the password).

After running this command, you will have successfully obtained the password and can move onto the next level!

---

## Level 9-10

### The Goal

The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

---
### The Solution

The commands needed to pass this level are:

- `strings`: Extracts printable (alphanumeric) strings from a file.
- `grep`: Searches for patterns in a file.

First, I used the `strings` command to extract only the printable strings from the file.

Next, I used the `grep` command to search for the pattern with multiple `=` signs before the password, as specified.

```bash
strings data.txt | grep "======="

```

After executing this command, you will have obtained the password and can move on to the next level!

---
## Level 10-11

### The Goal

The password for the next level is stored in the file data.txt, which contains base64 encoded data

---
### The Solution

The commands needed to pass this level are:

- `base64`: Encodes or decodes data using base64 encoding.

First, I used the `base64` command with the `-d` option to decode the contents of the `data.txt` file.

```bash
base64 -d data.txt
```

After executing this command, you will obtain the password and can move onto the next level!

---
## Level 11-12

### The Goal

The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

---
### The Solution

The command needed to pass this level is:

- `tr`: Translates or replaces characters in a file.

In this level, the goal is to decode the ROT13-encoded text in `data.txt`.

First, I used the `tr` command to reverse theletters rotated by 13 positions with their original form. The command used was:

   ```bash
   cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
   ```

After executing this command, you will obtain the password and can move onto the next level!

---

## Level 12-13

### The Goal

The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)

---
### The Solution

The commands used to pass this level are 

- `xxd -r`: Reverses a hexdump back into its binary form.
- `gzip -d`: Decompresses `.gz` files.
- `bzip2 -d`: Decompresses `.bz2` files.
- `tar -xf`: Extracts `.tar` archives.
- `mv`: Renames files.

   I Began by creating a temporary directory in `/tmp` and copy the `data.txt` file to this directory.

   ```bash
   mktemp -d
   cd /tmp/tmp.F5rykSJcfn
   cp ~/data.txt .
   ```

   The file is in hexdump format, so I used a command to reverse the hexdump back to its original compressed form and save it as `data`.

   ```bash
   xxd -r data.txt data
   ```

   After converting the hexdump, the resulting file will be a series of compressed formats. The most common ones you will encounter are GZIP, BZIP2, and TAR. To decompress these files:

   - **GZIP files**:Decompress by renaming the file to `.gz` and using the appropriate command.

   ```bash
      gzip -d data
   ```
   - **BZIP2 files**: Decompress by renaming the file to `.bz2` and using the appropriate command.

   ```bash
   bzip2 -d data
   ```

   - **TAR files**: Extract TAR archives with a command specific to extracting archives.

   ```bash
   tar -xf data
   ```

   After each decompression, inspect the file to determine its type, and continue decompressing until you retrieve the final uncompressed file.

4. **Retrieve the password:**
   Once all decompressions are complete, the final file will contain the password. View the contents of this file to get the password.

   ```bash
   cat data
   ```

## Level 13-14

### The Goal

The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on

---
### The Solution

- `scp`: Securely copies files between hosts.
- `ssh`: Logs into a remote system securely.
- `cat`: Displays the content of a file.

   First, securely copy the SSH private key from the Bandit server to your local machine. This key is located at `/home/bandit13/sshkey.private`. Use the `scp` command for this task, specifying the SSH port (2220) and the path where you want to save the key on your local machine.

   ```bash
   scp -P 2220 bandit13@bandit.labs.overthewire.org:/home/bandit13/sshkey.private /path/to/local/directory
   ```

   After copying the private key, use it to authenticate and log in as the `bandit14` user on the Bandit server. Specify the identity file (the private key) and the SSH port (2220) during the login process.

   ```bash
   ssh -i /path/to/sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
   ```

   Once you are logged in as `bandit14`, the password for the next level is stored in the file `/etc/bandit_pass/bandit14`. Display the password to access the next level.

   ```bash
   cat /etc/bandit_pass/bandit14
   ```

   After executing that command you will successfully retrieved the password and can move onto the next level!

---

## Level 14-15

### The Goal

The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

---
### The Solution

The commands used for this level are:

- `nc` Allows you to connect to a server

   For this level i used the `nc` command to open the server name localhost on port 30000

   ```bash
   nc localhost 30000
   ```

   After this i submitted the password which allowed me to retieve the password for the next Level!



   