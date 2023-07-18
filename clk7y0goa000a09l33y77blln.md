---
title: "Day 3 Task: Basic Linux Shell Scripting for DevOps Engineers."
datePublished: Tue Jul 18 2023 06:58:04 GMT+0000 (Coordinated Universal Time)
cuid: clk7y0goa000a09l33y77blln
slug: day-3-task-basic-linux-shell-scripting-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689663377349/41f495be-9da8-4e64-a1a8-d92b6d0dcac2.jpeg
tags: linux, linux-basics, 90daysofdevops, wemakedevs, tws

---

## What is Kernel

The kernel is a computer program that is the core of a computer’s operating system, with complete control over everything in the system.

## What is Shell

A shell is a special user program which provides an interface for the user to use operating system services. Shell accepts human-readable commands from a user and converts them into something which the kernel can understand. It is a command language interpreter that executes commands read from input devices such as keyboards or from files. The shell gets started when the user logs in or start the terminal.

## What is Linux Shell Scripting?

A shell script is a computer program designed to be run by a Linux shell, a command-line interpreter. The various dialects of shell scripts are considered to be scripting languages. Typical operations performed by shell scripts include file manipulation, program execution, and printing text.

**Tasks**

### Explain in your own words and examples, what is Shell Scripting for DevOps.

  
Shell scripting for **DevOps** is all about 🤖 **automating** and **orchestrating** tasks and processes in a DevOps environment using 📜 shell scripts. It involves writing scripts in shell programming languages (such as **Bash**, **PowerShell**, or **Python**) to streamline repetitive tasks, enable process automation, and facilitate the integration and deployment of software. 🚀

### What is `#!/bin/bash?` can we write `#!/bin/sh` as well?😒

The line "**#!/bin/bash**" is known as a shebang or hashbang. It is commonly placed at the beginning of a shell script file and specifies the interpreter to be used to execute the script. In this case, "**/bin/bash**" indicates that the script should be interpreted and executed by the Bash shell.

**<mark>Bash (Bourne Again Shell)</mark>** is a popular and feature-rich shell that is commonly used as the default shell on many Linux distributions. It is **backwards-compatible** with the original Bourne shell (/bin/sh) and provides additional functionality and improvements.

Now, regarding the use of "**#!/bin/sh**," it specifies the Bourne shell as the interpreter for the script. The Bourne shell is an older shell that lacks some of the advanced features and capabilities found in Bash. However, it is more lightweight and is still available on most Unix-like systems.

* ### Write a Shell Script which prints `I will complete #90DaysOofDevOps challenge`
    

```bash
#!/bin/sh

echo "I will Complete #90DaysOfDevOps Challenge"
```

First, create a file using touch Challenge.sh

Then `vi Challenge.sh`

Press `I` on the keyboard to insert

Write you content

Press the **esc Key** on the keyboard

Write `:wq` press enter to save and quit Vim

Give permission to file the **execute** using `chmod -x Challenge.sh`

At last type `./Challenge.sh`

* ### Write a Shell Script to take user input, input from arguments and print the variables.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689662555013/76fe36ec-fce0-45a0-bd28-c59c0dcbda65.png align="center")

* ### Write an Example of If else in Shell Scripting by comparing 2 numbers
    

```bash
#!/bin/bash

# Compare two numbers
num1=10
num2=20

if [ $num1 -eq $num2 ]; then
    echo "The numbers are equal."
elif [ $num1 -gt $num2 ]; then
    echo "Number 1 is greater than Number 2."
else
    echo "Number 2 is greater than Number 1."
fi
```

# **Top 100 Linux Commands Cheat Sheet:**

1. cd — Change directory
    
2. ls — List directory contents
    
3. pwd — Print working directory
    
4. cat — Concatenate and display files
    
5. touch — Create an empty file
    
6. cp — Copy files and directories
    
7. mv — Move or rename files and directories
    
8. rm — Remove files and directories
    
9. mkdir — Create a new directory
    
10. rmdir — Remove an empty directory
    
11. cut — Cut out sections of a file
    
12. gzip — Compress or decompress files using gzip
    
13. gunzip — Decompress files compressed with gzip
    
14. find — Find files and directories matching a pattern
    
15. grep — Search for a pattern in a file
    
16. awk — Pattern scanning and processing language
    
17. sed — Stream editor for filtering and transforming text
    
18. head — Display the first few lines of a file
    
19. tail — Display the last few lines of a file
    
20. sort — Sort lines of a file
    
21. uniq — Remove duplicate lines from a file
    
22. wc — Count lines, words, and characters in a file
    
23. diff — Compare two files line by line
    
24. patch — Apply a patch to a file
    
25. chmod — Change permissions of files and directories
    
26. chown — Change the owner of a file or directory
    
27. chgrp — Change the group ownership of a file or directory
    
28. ps — List running processes
    
29. top — Display system resource usage and process information
    
30. kill — Send a signal to a process to terminate it
    
31. du — Display disk usage of files and directories
    
32. df — Display free disk space on the file system
    
33. mount — Mount a file system
    
34. umount — Unmount a file system
    
35. ping — Test connectivity to a network host
    
36. ssh — Secure shell remote login and command execution
    
37. scp — Secure copy files between hosts
    
38. rsync — Remote file and directory synchronization
    
39. curl — Transfer data from or to a server using various protocols
    
40. wget — Retrieve files from the web using various protocols
    
41. ftp — File Transfer Protocol client
    
42. sftp — Secure File Transfer Protocol client
    
43. telnet — Telnet client
    
44. nslookup — DNS lookup utility
    
45. dig — DNS lookup utility
    
46. netstat — Display network connections and statistics
    
47. ifconfig — Configure network interfaces
    
48. route — Display or modify the routing table
    
49. iptables — Firewall and packet filtering utility
    
50. hostname — Display or set the hostname of the system
    
51. date — Display or set the system date and time
    
52. timedatectl — Control the system date and time
    
53. uname — Display system information
    
54. whoami — Display the current user ID
    
55. id — Display user and group information
    
56. su — Switch user to become another user
    
57. sudo — Execute a command with superuser privileges
    
58. passwd — Change the password of a user account
    
59. useradd — Create a new user account
    
60. userdel — Delete a user account
    
61. usermod — Modify a user account
    
62. groupadd — Create a new group
    
63. groupdel — Delete a group
    
64. groupmod — Modify a group
    
65. finger — Display information about users on the system
    
66. last — Display information about recent logins
    
67. history — Display command history
    
68. echo — Print a message to the terminal
    
69. printf — Format and print data
    
70. lshw — Displays hardware information
    
71. lspci — Displays information about PCI buses and devices.
    
72. lsusb — Displays information about USB buses and devices.
    
73. hwinfo — Displays detailed hardware information.
    
74. free — Displays memory usage.
    
75. vmstat — Displays system memory, processor, and I/O statistics.
    
76. iostat — Displays CPU and disk I/O statistics.
    
77. uptime — Displays system uptime and load averages.
    
78. journalctl — Displays the system journal.
    
79. dmesg — Displays the kernel ring buffer.
    
80. crontab — Schedules recurring tasks.
    
81. at — Schedules a one-time task.
    
82. service — Manages system services.
    
83. systemctl — Controls system services in systemd-based distributions.
    
84. traceroute — Traces the network path to a remote host.
    
85. bzip2 — Compresses files using the bzip2 algorithm.
    
86. unzip — Extracts files from a ZIP archive.
    
87. tee — Redirect output to multiple files
    
88. chroot — Change the root directory for a process
    
89. ps aux — Display information about all running processes
    
90. less — Display file contents in a paginated format
    
91. more — Display file contents one page at a time
    
92. ln — Create links between files
    
93. realpath — Print the resolved absolute path of a file
    
94. watch — Execute a command periodically and display the output
    
95. cal — Display a calendar
    
96. tar -xzvf — Extract files from a compressed archive
    
97. tar -czvf — Create a compressed archive
    
98. whereis — Locate the binary, source, and manual page files for a command
    
99. locate — Find files by name
    
100. <mark>which — Display the full path to an executable</mark>