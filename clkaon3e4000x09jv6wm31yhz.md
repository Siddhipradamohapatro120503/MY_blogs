---
title: "Day 4 Task: Advanced Linux Shell Scripting for DevOps Engineers with User management"
datePublished: Thu Jul 20 2023 04:59:02 GMT+0000 (Coordinated Universal Time)
cuid: clkaon3e4000x09jv6wm31yhz
slug: day-4-task-advanced-linux-shell-scripting-for-devops-engineers-with-user-management
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689828883124/7f979213-8855-44de-bb77-1812c351a03c.png
tags: linux, 90daysofdevops, wemakedevs, shubhamlondhe, tws

---

Suppose you noticed that there are a total of 90 sub-directories in the directory '2023' of this repository. What did you think, how did I create 90 directories? Manually one by one or using a script, or a command?

All 90 directories within seconds using a simple command.

`mkdir day{1..90}`

### Tasks 1

1. You have to do the same using Shell Script i.e using either Loops or command with start day and end day variables using arguments -
    

So Write a bash script [CreateDirectories.sh](http://createDirectories.sh) that when the script is executed with three given arguments (one is directory name and the second is the start number of directories and the third is the end number of guides) it creates a specified number of directories with a dynamic directory name.

The Shell Script code of [`CreateDirectories.sh`](http://createDirectories.sh)

```bash
#!/bin/bash

if [ $# -ne 3 ] || ! [[ $2 =~ ^[0-9]+$ ]] || ! [[ $3 =~ ^[0-9]+$ ]] || (( $2 > $3 )); then
  echo "Usage: $0 <directory_name> <start_number> <end_number>"
  exit 1
fi

directory_name=$1

for ((i=$2; i<=$3; i++)); do
  mkdir -p "${directory_name}${i}" || exit 1
done

echo "Directories created successfully."
```

**Example 1: When the script is executed as**

`./`[`CreateDirectories.sh`](http://createDirectories.sh) `day 1 90`

then it creates 90 directories as `day1 day2 day3 .... day90`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689825482888/991d1f5d-3420-418a-bd15-8198d5d3aae4.png align="center")

To remove so many directory command is

`rmdir days{1..90}`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689825614714/f9f747df-86e9-4e94-adfe-9b1064d7a7d7.png align="center")

**Example 2: When the script is executed as**

`./`[`createDirectories.sh`](http://createDirectories.sh) `Movie 20 50` then it creates 50 directories as `Movie20 Movie21 Movie23 ...Movie50`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689825799319/50b93f32-81c0-4813-97d7-bf2cc0f0cdcb.png align="center")

### Create a Script to back up all your work done till now.

1. First, create a new directory to store your backups:
    

```bash
mkdir ~/my_backups
```

1. Create a new file named `backup_work.sh` and open it for editing:
    

```bash
nano backup_work.sh
```

1. Copy and paste the following script into the `backup_work.sh` file:
    

```bash
bashCopy code#!/bin/bash

backup_directory="$HOME/my_backups/$(date +'%Y%m%d_%H%M%S')"
mkdir -p "$backup_directory" || { echo "Error creating backup directory."; exit 1; }

# Replace the following paths with the actual paths to your work directories and files
work_directory="$HOME/Documents/work"
important_files="$HOME/Documents/important.txt"

cp -r "$work_directory" "$backup_directory" || { echo "Error copying work directory."; exit 1; }
cp "$important_files" "$backup_directory" || { echo "Error copying important file."; exit 1; }

echo "Backup created successfully in: $backup_directory"
```

1. Save the changes and exit the text editor (in Nano, press `Ctrl+X`, then `Y` to save and `Enter` to confirm).
    
2. Make the script executable:
    

```bash
chmod +x backup_work.sh
```

Now, you can run the script to create a backup of your work:

```bash
./backup_work.sh
```

### Read About Cron and Crontab, to automate the backup Script

  
🕰️ **Cron** is like a timekeeper⏳ for your computer! It's a scheduler that helps you set up tasks to run automatically at specific times without you having to remember. It's like having a personal assistant that takes care of things on a schedule for you!

⏲️ **Crontab** is like your personal to-do list 📝 for Cron. It's where you write down the tasks you want Cron to do for you. You can tell Cron what to do when to do it, and how often. It's like giving your timekeeper instructions for what tasks to handle and when!

For example, you can tell Crontab:

* "🕐 Every day at 6 PM, back up my important files to a safe place."
    
* "📅 On the 1st day of every month, clean up temporary files from my computer."
    

And Cron will make sure these tasks happen automatically according to your instructions! No need to worry about forgetting or doing them manually. It's all taken care of by Cron and Crontab! 🤖

1. Open your terminal and run the following command to edit your user's crontab:
    

```bash
crontab -e
```

This will open the crontab file in your default text editor.

1. Add a new line to schedule your backup script. For example, to run the backup script every day at 1:00 AM, add the following line:
    

```bash
0 1 * * * /path/to/backup_work.sh
```

Replace `/path/to/backup_work.sh` with the actual path to your backup script.

1. Save the changes and exit the text editor. In Nano, you can do this by pressing `Ctrl+X`, then `Y` to save and `Enter` to confirm.
    
2. Cron will automatically pick up the new entry, and your backup script will run at the scheduled time.
    

Here's an explanation of the crontab line format:

```bash
* * * * * /path/to/command/to/execute
│ │ │ │ │
│ │ │ │ └─── Day of the week (0 - 7) (Sunday is 0 or 7)
│ │ │ └──────── Month (1 - 12)
│ │ └──────────── Day of the month (1 - 31)
│ └──────────────── Hour (0 - 23)
└──────────────────── Minute (0 - 59)
```

### Read about User Management and Let me know on Linkedin if you're ready for Day 6

👥 **User Accounts**: In Linux, each user is represented by an account. User accounts are like individual characters in the Linux world! They have their unique identities (User IDs or UIDs), like secret agent codes, that distinguish them from others. Regular users have cool UIDs starting from 1000, while the special system users get the lower UIDs (1-999).

👑 **Root User**: The root user is the ultimate boss 🌟 with the UID 0! Think of it as a superhero who has access to everything, like a master key 🔑 that can unlock all doors. But remember, with great power comes great responsibility! It's crucial to handle root privileges with care, as it can alter the entire system.

👨‍💼 **User Commands**: The Linux command lineup 🚀 gives us the power to manage users like magicians! We can create new user accounts with `useradd`, modify their properties with `usermod`, or wave our wand to delete users using `userdel`. When users need to change their secret passcodes 🔒, we use `passwd`. With the `su` spell, we can transform into other users and explore their world. And if we want to grant someone limited powers, `sudo` comes to our aid! 🧙‍♂️

👫 **User Groups**: We love teamwork in Linux! Users can form groups 🤝 where they unite and share permissions. These groups are like squads with special abilities 🛡️, allowing them to access certain files and folders together.

🔑🕵️‍♂️ **Password and Shadow Files**: Secrets are guarded in Linux! User account information is stored in the `/etc/passwd` file, like a treasure map. But the real secrets, like password hashes, are locked away in the `/etc/shadow` file, accessible only by the root user. It's a fortress to protect sensitive data! 🏰

🏠 **User Home Directory**: Everyone needs a cosy home, right? Each user has their own home directory 🏡 where they store their personal stuff. It's like a room where they can decorate and organize their files, making it a special place for them. The home directory is typically found in `/home/username`. 🏠🗄️.

### Create 2 users and just display their Usernames

1. Open a terminal on your Linux system.
    
2. To create the first user, use the `useradd` a command followed by the desired username (e.g., `user1`):
    

```bash
sudo useradd siddhi0983
```

1. To create the second user, use the same `useradd` command with a different username (e.g., `user2`):
    

```bash
sudo useradd subho0948
```

1. Now, let's display the usernames of both users. Use the `cut` command to extract the first field (username) from the `/etc/passwd` file:
    

```bash
cut -d: -f1 /etc/passwd | grep -E 'siddhi0983|subho0948'
```

This command will display the usernames of the two users you just created.

Note: The `sudo` command is used to run the commands with root privileges as user management tasks generally require administrative privileges. Make sure you have the necessary permissions to create users on your system. Additionally, you can replace `user1` and `user2` with any desired usernames.

**Thank you for reading my blog make sure to give ❤️**

> Creating users is like adding characters to a Linux story. Each one has their unique username, and together they form a diverse cast, unlocking the potential of the Linux world." 🌟🚀