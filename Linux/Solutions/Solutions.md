# OverTheWire Bandit Solutions

---

## Table of Contents

- [Level 0](#level-0)
- [Level 0-1](#level-0-1)
- [Level 1-2](#level-1-2)

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
