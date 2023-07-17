---
title: "Day2: Linux Command Line"
datePublished: Mon Jul 17 2023 04:45:12 GMT+0000 (Coordinated Universal Time)
cuid: clk6dtqit000b0amxasva0ssi
slug: day2-linux-command-line
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689568964379/81150b46-abb2-4ef8-b6ec-f416c04a3054.png
tags: linux, shell-script, 90daysofdevops, wemakedevs, tws

---

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689568800840/768e189c-92ec-445f-a0b0-2f7e10698896.gif align="center")

@[Shubham Londhe](@TrainWithShubham)

Task: What is the Linux command to

1. 1. To view what's written in a file.
        
    2. To change the access permissions of files.
        
    3. To check which commands you have run till now.
        
    4. To remove a directory/ Folder.
        
    5. To create a fruits.txt file and to view the content.
        
    6. Add content in devops.txt (One in each line) - Apple, Mango, Banana, Cherry, Kiwi, Orange, Guava.
        
    7. To Show only top three fruits from the file.
        
    8. To Show only bottom three fruits from the file.
        
    9. To create another file Colors.txt and to view the content.
        
    10. Add content in Colors.txt (One in each line) - Red, Pink, White, Black, Blue, Orange, Purple, Grey.
        
    11. To find the difference between fruits.txt and Colors.txt file.
        

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689568832160/a1c67f3a-0e03-4c68-b60a-23f161d2b952.png align="center")

### To view what's written in a file.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689565978919/a9ec4dd4-e323-4a84-bbb9-a222a6d76da4.png align="center")

### To change the access permissions of files.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689566377361/42a34ce6-0725-4244-8e78-2a4c0625166d.png align="center")

### To check which commands you have run till now.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689566468748/e08ede97-51f3-45bb-a9e1-8759b1365a97.png align="center")

### To remove a directory/ Folder.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689566579531/1d6bf8b7-1880-487f-a013-26a467f33c3f.png align="center")

### To create a fruits.txt file and to view the content.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689566750956/001f3fa4-42e4-4895-92f0-a7303d213fde.png align="center")

### Add content in devops.txt (One in each line) - Apple, Mango, Banana, Cherry, Kiwi, Orange, Guava.

1. To Show only top three fruits from the file.
    
    ```bash
    head -n 3 file_name.txt
    ```
    
2. To Show only bottom three fruits from the file.
    
    ```bash
    tail -n 3 file_name.txt
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689567134785/50b49b2c-7dfd-4ebb-972e-c3d191d03ea6.png align="center")
    

### To create another file Colors.txt and to view the content.

### Add content in Colors.txt (One in each line) - Red, Pink, White, Black, Blue, Orange, Purple, Grey.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689567654130/95ba51f2-cdb9-483e-bd09-c6f7b75bce3b.png align="center")

### To find the difference between fruits.txt and Colors.txt files.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689567698310/cb5942f7-d111-4818-b065-aea81ad04094.png align="center")

## Some Advance Command In Linux

1. `rsync`: Efficiently synchronize and transfer files between systems. Example: Synchronize a local directory with a remote directory:
    
    ```bash
    rsync -avz /path/to/local/dir user@remote:/path/to/remote/dir
    ```
    
2. `ssh`: Securely connect to remote systems and execute commands. Example: Connect to a remote server:
    
    ```bash
    ssh user@remote
    ```
    
3. `tar`: Archive and compress files and directories. Example: Create a compressed tarball of a directory:
    
    ```bash
    tar -czvf archive.tar.gz /path/to/directory
    ```
    
4. `grep`: Search for patterns in files and directories. Example: Search for a specific string in a file:
    
    ```bash
    grep "pattern" file.txt
    ```
    
5. `awk`: Process and manipulate structured text data. Example: Print the second column of a CSV file:
    
    ```bash
    awk -F ',' '{print $2}' file.csv
    ```
    
6. `sed`: Stream editor for manipulating text. Example: Replace a specific string in a file:
    
    ```bash
    sed 's/old_string/new_string/g' file.txt
    ```
    
7. `find`: Search for files and directories based on various criteria. Example: Find all files modified within the last 24 hours:
    
    ```bash
    find /path/to/search -type f -mtime -1
    ```
    
8. `top`: Monitor system processes and resource usage. Example: Display real-time system resource usage:
    
    ```bash
    top
    ```
    
9. `htop`: Interactive process viewer with additional features compared to top. Example: Monitor system processes and resource usage with htop:
    
    ```bash
    htop
    ```
    
10. `netstat`: Display network connections, routing tables, and network interface statistics. Example: Show active network connections:
    
    ```bash
    netstat -tuln
    ```
    
11. `iptables`: Configure and manage firewall rules. Example: Allow incoming SSH connections:
    
    ```bash
    iptables -A INPUT -p tcp --dport 22 -j ACCEPT
    ```
    
12. `lsof`: List open files and the processes that use them. Example: List processes using a specific file:
    
    ```bash
    lsof /path/to/file
    ```
    
13. `strace`: Trace system calls and signals of a running program. Example: Trace system calls of a command:
    
    ```bash
    strace -f -e trace=network command
    ```
    
14. `journalctl`: View and manage system logs using the systemd journal. Example: View the latest system logs:
    
    ```bash
    journalctl -xe
    ```
    
15. `dd`: Convert and copy files with low-level I/O operations. Example: Create a bootable USB from an ISO image:
    
    ```bash
    dd if=/path/to/image.iso of=/dev/sdX bs=4M status=progress
    ```
    
16. `wget`: Download files from the internet. Example: Download a file from a URL:
    
    ```bash
    wget https://example.com/file.tar.gz
    ```
    
17. `curl`: Transfer data from or to a server using various protocols. Example: Send an HTTP POST request with data:
    
    ```bash
    curl -X POST -d "param1=value1&param2=value2" https://example.com/api
    ```
    
18. `useradd` and `usermod`: Create and modify user accounts. Example: Create a new user:
    
    ```bash
    useradd username
    ```
    
19. `chown` and `chmod`: Change ownership and permissions of files and directories. Example: Change ownership of a file:
    
    ```bash
    chown username file.txt
    ```
    
20. `cron`: Schedule and automate recurring tasks. Example: Edit the crontab file to schedule a task:
    
    ```bash
    crontab -e
    ```
    

Additionally, here are some `systemctl` and service-related commands:

* Start a service:
    
    ```bash
    sudo systemctl start service-name
    ```
    
* Stop a service:
    
    ```bash
    sudo systemctl stop service-name
    ```
    
* Restart a service:
    
    ```bash
    sudo systemctl restart service-name
    ```
    
* Enable a service to start at boot:
    
    ```bash
    sudo systemctl enable service-name
    ```
    
* Disable a service from starting at boot:
    
    ```bash
    sudo systemctl disable service-name
    ```
    

Check the status of a service:

```bash
sudo systemctl status service-name
```

## Some WildCard Example

1. `*` (asterisk): Matches any number of characters (including none). Example: List all files with the `.txt` extension in the current directory:
    
    ```bash
    ls *.txt
    ```
    
2. `?` (question mark): Matches a single character. Example: List all files with a three-letter extension in the current directory:
    
    ```bash
    ls ???
    ```
    
3. `[ ]` (square brackets): Matches any single character specified within the brackets. Example: List all files with a digit as the second character:
    
    ```bash
    ls [0-9]?*
    ```
    
4. `[!]` (exclamation mark within square brackets): Matches any single character not specified within the brackets. Example: List all files without a `.txt` extension in the current directory:
    
    ```bash
    ls *[!.txt]
    ```
    
5. `{ }` (curly braces): Matches any of the comma-separated patterns enclosed within the braces. Example: Copy multiple files with different extensions to a directory:
    
    ```bash
    cp file.{txt,doc,pdf} destination/
    ```
    
6. `~` (tilde): Represents the user's home directory. Example: Navigate to the home directory:
    
    ```bash
    cd ~
    ```
    
7. `.` (dot): Represents the current directory. Example: List all hidden files in the current directory:
    
    ```bash
    ls -a .*
    ```
    
8. `..` (double dot): Represents the parent directory. Example: Navigate to the parent directory:
    
    ```bash
    cd ..
    ```
    
9. `[^ ]` (caret within square brackets): Matches any single character not specified within the brackets. Example: List all files that don't start with a digit:
    
    ```bash
    ls [^0-9]*
    ```
    
10. `**` (double asterisk): Matches any number of directories and subdirectories recursively. Example: Search for files with a specific name in all subdirectories:
    
    ```bash
    find /path/to/search -name "filename" -type f
    ```
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689568862175/db6c7e99-0e34-4628-a863-980886aa5903.png align="center")

## Some Tips and Tricks In the command line

1. Command History:
    
    * Use the arrow keys to navigate through previously executed commands.
        
    * Pressing `Ctrl + R` allows you to search and execute commands from your command history.
        
2. Command Completion:
    
    * Pressing the `Tab` key autocompletes commands, file and directory names, and command options.
        
    * Pressing `Tab` twice displays possible completions if there are multiple matches.
        
3. Command Output Manipulation:
    
    * Use `|` (pipe) to redirect the output of one command as input to another command.
        
    * Example: `ls -l | grep "file"` - Lists files and directories and filters for lines containing "file".
        
4. Command Options:
    
    * Most commands have various options that modify their behavior.
        
    * Use the `-h` or `--help` option to display the command's manual or help page.
        
    * Example: `ls --help` - Displays the help page for the `ls` command.
        
5. Command Shortcuts:
    
    * Use the `Ctrl + C` shortcut to terminate a running command.
        
    * Use the `Ctrl + D` shortcut to exit the current shell session.
        
    * Use the `Ctrl + Z` shortcut to suspend a running command and bring it to the background.
        
6. Command Output Paging:
    
    * Use the `less` command to view long command output one page at a time.
        
    * Example: `command | less` - Pipes the output of a command into `less` for paging.
        
7. Command Execution as Root:
    
    * Prefix a command with `sudo` to execute it with root (superuser) privileges.
        
    * Example: `sudo apt-get update` - Updates package information with root privileges.
        
8. Command Execution in the Background:
    
    * Append `&` at the end of a command to run it in the background.
        
    * Example: `command &` - Executes the command in the background, allowing you to continue working in the same terminal.
        
9. Command Execution Timing:
    
    * Use the `time` command to measure the execution time of a command.
        
    * Example: `time command` - Displays the execution time of the specified command.
        
10. Command Output Redirect:
    
    * Use `>` to redirect command output to a file, overwriting its contents.
        
    * Use `>>` to redirect command output to a file, appending it to the existing contents.
        
    * Example: `command > output.txt` - Redirects the output of the command to the "output.txt" file.