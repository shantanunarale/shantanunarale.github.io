---
author: shantanunarale
title: Basics of Linux Terminal
date: 2024-01-16 23:58:00 +0530
categories: [Terminal, Linux]
tags: [Bash, Linux Terminal]
---
## Intro

A terminal is a program that allows us to interact with the operating system using command line. We can directly use OS commands in the terminal. Before the Graphical User interfaces were developed, terminals were the only means available to interact with a computer. Now a days, the terminal programs available are not the real terminals but a terminal emulator. Bash is one of the terminal application available in Linux (and Linux group of operating systems).

As you start the bash, the first screen that appears is as shown below.
![bash_screen](/SxhsYhX3/img1.png)_Bash startup screen_{: width = 700}. Here the first word is the name of the user, followed by @ symbol and the next word is the name of the computer. The ~ symbol means,the home directory.

> Every user, is assigned a default home directory where the user session is started by default.

## Super User

In Linux world, the terminology used for admin is super user. Thus a super user is an user who has all the access. From any directory you can navigate to Home directory using.

```Terminal
cd ~
```
If you want to perform any action that needs an administrative privileges, you can do so by using word `sudo` that stands for *super user do* provided you have sudo access. Below is the example of using this command.

```Terminal
sudo cat testfile.txt
```

If you are using this command for the very time, you may be prompted to enter your password.

> The cursor won't progress while you are entering the password.

## Files And Directories

To know your current working directory, just use the command `pwd` as shown below.

![pwd](/6pfQdmn3/img2.png)_present working directory_{:width = 700}

To change the directory, we have the `cd` command that stands for change directory. In Linux, the directory structure is navigated using / like shown below.

![cd](/VNdMNw0M/img3.png)_change directory_{:width = 700}

To check all the contents of a folder, you can use ls command. This command also accepts few more switches that can be specified using a hyphen.

![ls](/MHF05GBW/img4.png)_ls command_{:width = 700}

The -l switch shows the long listing which includes the permission, the file size, owner and group as well as the date time when it was created. The -a switch shows all the files including the hidden files.

To create a new folder, the command is `mkdir` as shown below.

```Terminal
mkdir test_folder
```
To remove a directory, the command is `rm`. This command works only if the folder is empty, else we get an error. To prevent this use -r switch as shown below. This command can also be used to delete any file as well.

```Terminal
rm -r test_folder
```

To create a file, there are multiple options. The easiest one is to use `touch` command as shown below.

```Terminal
touch testfile.txt
```

In its basic usage, touch command just updates the last accessed time of any file. So if the file already exists, this command is suppose to update the last access time of the file, however, if the file does not exists, it creates a new file. There are few other ways of creating files.

- cat command
- echo and > operator.

Below is the example of creating file using cat and echo command.

![cat and echo](/d3CxD9BY/img5.png)_create file using cat_{:width = 700}

The cat command can also be used for concatenating two or more files, however, in this case it opens a new prompt to enter the content of the files. Once we are done hit **Ctrl + D** to exit and save the file.

> You can use tab for auto-completion.

## User Permissions

By default, when we create a user in linux, it also creates a group with the same name. To see the permission a user has you can use `ls -l` as shown in the below. However, at times, the user does not have a specific permission.

![file_permissions](/8CQpKy72/img6.png)_ls permissions_{:width = 700}

As shown above, I do not have permission to read this file. So I get below error while using the cat command.

![error_cat](/QMth4HsT/img7.png)_error permission denied_{:width = 700}

One way around this is to use `sudo` before cat as shown below (if you have sudo privileges).

```Terminal
sudo cat 
```

Other way is to give access using `chmod` as shown below.

```Terminal
chmod u=rw terminal_1.txt
```
Here, I have specified = sign, which means user should be given permissions mentioned after =. The permissions are 
- r : read
- w : write
- x : execute.

You could have also used, + sign to add a permission like below.

```Terminal
chmod u+r terminal_1.txt
```