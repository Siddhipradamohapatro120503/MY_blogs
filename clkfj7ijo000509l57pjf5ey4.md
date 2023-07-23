---
title: "Day 6 Task: Understanding package manager and systemctl"
datePublished: Sun Jul 23 2023 14:25:48 GMT+0000 (Coordinated Universal Time)
cuid: clkfj7ijo000509l57pjf5ey4
slug: day-6-task-understanding-package-manager-and-systemctl
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690122283830/6a86fbea-d472-423e-b09e-a6a66480b4be.jpeg
tags: linux, 90daysofdevops, wemakedevs, shubhamlondhe, trainwithshubham

---

### What is a package manager in Linux?

📦🐧In simple words, a package manager in Linux is like an app store for your computer. It helps you easily find, install, update, and remove software without the need to search the web or deal with messy downloads. It's a convenient way to manage all the software on your Linux system, keeping it organized and up-to-date with just a few clicks or commands.💻🚀

### What is the package?

A package is like a neatly wrapped gift 🎁 that contains software for your computer. It's a collection of files and instructions that make a specific program work properly on your system.

Imagine you want to install a new cool app on your computer, like a photo editor 📸. Instead of downloading all the necessary files one by one from the internet, a package bundles everything together in an organized way. It includes the main program, its supporting files, and instructions on how to install and run it.

When you use a package manager (like we talked about earlier), it finds the right package for you in its app store 🏬. Then, with a simple command or click, it unwraps the package, sets up the software correctly, and voilà! You have your shiny new photo editor installed and ready to use. 🎉

Packages make installing and managing software much easier, as they handle all the behind-the-scenes work, ensuring everything works harmoniously on your computer. So, whenever you want to add or update software, think of packages as those convenient gift boxes that deliver the software goodness right to your digital doorstep! 🎀💻🎈

### Different kinds of package managers

1. 🐍 **Python's "pip" Package Manager**: Pip is like a Pythonic 🐍 treasure chest that helps you manage Python libraries and packages. It makes it super easy to install, update, and remove Python software, so you can build amazing projects with ease. 📦🐍🔧
    
2. 📦 **Node.js's "npm" Package Manager**: Npm is the friendly 🌟 buddy for Node.js developers. It's like a playground for JavaScript packages 🎮. With npm, you can fetch and use various libraries to create web applications and server-side magic. 🌐📚🔮
    
3. 🏗️ **GNU Compiler Collection (GCC)**: GCC is a powerful 🚀 toolbox for developers. It includes various compilers for languages like C, C++, and Fortran. It's like having a set of construction tools 🛠️ to build robust software for your Linux system. 🛡️🏰👷
    
4. 🍫 **Chocolatey Package Manager**: Chocolatey is like a sweet 🍫 treat for Windows users. It brings the joy of package management to the Windows environment. With Chocolatey, you can easily install and update software from the command line. 🍬🖥️🍭
    
5. 🍎 **Homebrew for macOS**: Homebrew is like a refreshing 🍺 pint of beer for Mac users. It's a popular package manager that allows you to install and manage open-source software on your macOS system. Cheers to easy software management! 🍻🍏💻
    
6. **RPM (Red Hat Package Manager)**: 📦
    
    RPM is the foundation of package management in Red Hat-based distributions like RHEL, CentOS, and Fedora. 🐂
    
    It stands for "Red Hat Package Manager."
    
    RPM is used to manage individual software packages in the `.rpm` format.
    
    Each RPM package contains compiled software, configuration files, and metadata about the package.
    
    Popular commands: `rpm -i` (install), `rpm -U` (upgrade), `rpm -e` (erase/remove).
    
7. 🏭 **Snap Package Manager**: Snap is like a modular 🏭 factory that packages software with all its dependencies. It provides a way to distribute apps that work across various Linux distributions, making it easier to get the software you need, regardless of your Linux flavor. 📦🔧🔨
    
8. **APT (Advanced Package Tool)**: 📦 Used in Debian and Ubuntu distributions. 🐧 APT uses the `apt-get` command to manage packages. It deals with packages in the `.deb` format. Popular commands: `apt-get install`, `apt-get update`, `apt-get remove`. 📝
    
9. **dnf/yum**: 📦 DNF (Dandified Yum) is the default package manager in Fedora and RHEL 8+. Yum (Yellowdog Updater Modified) was used in older RHEL and CentOS versions. They manage packages in the `.rpm` format. Popular commands: `dnf install`, `dnf update`, `dnf remove`. 🐂
    
10. **Pacman**: 📦 Used in Arch Linux and its derivatives. Pacman is known for its simplicity and speed. It handles packages in the `.pkg.tar.xz` format. Popular commands: `pacman -S`, `pacman -Syu`, `pacman -R`. 🏹
    
11. **Flatpak**: 📦 Another universal package manager that provides sandboxed applications. Works across various Linux distributions. Flatpak packages use the `.flatpak` format. Popular commands: `flatpak install`, `flatpak update`, `flatpak uninstall`. 📦🏢🚀
    
12. **zypper**: 📦 Used in openSUSE Linux. Zypper is efficient and user-friendly. Manages packages in the `.rpm` format. Popular commands: `zypper install`, `zypper update`, `zypper remove`. 📦🔍🦌
    
13. **Portage**: 📦 The package manager for Gentoo Linux. It compiles packages from source code, providing high customization. Offers a rich set of options and control over system configuration. Popular commands: `emerge`, `emerge --sync`, `emerge --unmerge`. 📦🔨🔧
    
14. **Nix**: 📦 Used in NixOS, a unique Linux distribution. Nix is purely functional and allows multiple versions of packages to coexist. Provides easy rollback to previous configurations. Popular commands: `nix-env -i`, `nix-env -u`, `nix-env --uninstall`. 📦🎛️⏪
    
15. **Apk**: 📦 The package manager for Alpine Linux, known for its lightweight nature. Manages packages in the `.apk` format. It focuses on security and simplicity. Popular commands: `apk add`, `apk update`, `apk del`. 📦🏔️🏂
    

## Tasks 1:

**You have to install docker or jenkins in your system from your terminal using package managers**

I have written a Script to install Docker using **Shell Script**

**Create** file Using Vi

```bash
vi docker_install.sh
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690120850193/8426ba9d-3cfc-4122-ab83-688e6581a304.png align="center")

Write the above Script by pressing I key in keyboard.

```bash
chmod 700 docker_install.sh
```

```bash
./docker_instal.sh
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690121079830/a62cb2ff-4152-43d5-be9d-990df4117437.png align="center")

This type of output will you get after installing Docker.

**If you want to check whether Docker is running or not you can :**

```bash
systemctl status docker
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690121258787/d553c20f-5102-413a-8d40-7caebff2a3b9.png align="center")

**If you want to stop you can use this command :**

```bash
systemctl stop docker
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690121369662/ee505e8a-4f28-4819-9491-80dbcf59a1dc.png align="center")

**You can use these commands for various purposes:**

**Systemd Commands (Used by the Systemd service manager):**

1. `systemctl start service_name`: Starts a service.
    
2. `systemctl stop service_name`: Stops a service.
    
3. `systemctl restart service_name`: Restarts a service.
    
4. `systemctl enable service_name`: Enables a service to start automatically at boot.
    
5. `systemctl disable service_name`: Disables a service from starting automatically at boot.
    
6. `systemctl status service_name`: Shows the status of a service, whether it's running or stopped.
    
7. `systemctl is-active service_name`: Checks if a service is currently active/running.
    
8. `systemctl is-enabled service_name`: Checks if a service is enabled to start at boot.
    
9. `systemctl list-units`: Lists all active units (services, sockets, devices, etc.).
    
10. `systemctl list-unit-files`: Lists all available unit files (service definitions) on the system.
    

**Examples (assuming 'apache' is the service name):**

* To start Apache web server: `sudo systemctl start apache`
    
* To stop Apache web server: `sudo systemctl stop apache`
    
* To restart Apache web server: `sudo systemctl restart apache`
    
* To enable Apache to start at boot: `sudo systemctl enable apache`
    
* To disable Apache from starting at boot: `sudo systemctl disable apache`
    
* To check the status of Apache: `sudo systemctl status apache`
    
* To see if Apache is active/running: `sudo systemctl is-active apache`
    
* To see if Apache is enabled: `sudo systemctl is-enabled apache`
    
* To list all active units: `sudo systemctl list-units`
    
* To list all available unit files: `sudo systemctl list-unit-files`
    
    Remember to use `sudo` before the commands that require administrative privileges, as most Systemd operations need elevated permissions. 🚀🔧🌟
    

## Tasks 2:

🔧 **systemctl vs. service** 🔍

Both `systemctl` and `service` are commands used in Linux to manage services, but they have some differences in how they interact with Systemd, the service manager. Let's explore them with interactive emojis! 🤩🔧🐧

1. **systemctl**: 🎛️
    
    * Systemctl is like a modern remote control for Systemd, giving you advanced control over services.
        
    * It's the preferred method on newer Linux distributions, and it interacts directly with Systemd.
        
    * Systemctl offers more features, like enabling or disabling services at boot, showing detailed status, and managing dependencies.
        
2. **service**: 🕹️
    
    * Service is like an old-school, basic control panel for services.
        
    * It is a legacy command and works with System V init scripts.
        
    * It still exists for compatibility with older systems and scripts, but it lacks some advanced features of Systemd.
        

⚙️ **Usage:**

* To check the status of the "docker" service:
    
    * **systemctl**: `systemctl status docker`
        
    * **service**: `service docker status`
        
    
    Both commands will show whether the "docker" service is running or stopped.
    
* To start the "docker" service:
    
    * **systemctl**: `sudo systemctl start docker`
        
    * **service**: `sudo service docker start`
        
    
    Both commands will start the "docker" service.
    
* To enable the "docker" service to start at boot:
    
    * **systemctl**: `sudo systemctl enable docker`
        
    * **service**: Not available with the `service` command.
        
    
    Here, only `systemctl` can enable the "docker" service to start automatically during boot.
    

👉 **Recommendation**:

* For newer systems and more functionality, use `systemctl` for managing services.
    
* If you're working on an older system with System V init scripts, you can still use `service`.
    

Remember, Systemd and `systemctl` are becoming the standard on modern Linux distributions, offering more power and flexibility for managing services! 🚀💪🐧

🌟 Thank you, dear readers! Your support means the world to me. 🌍✨ We're grateful to have you as part of our incredible blog community! 🤗📚 Your engagement, likes, and shares fuel my passion to bring for you more inspiring content. 🚀🔥 Let's continue this amazing journey together! 🌈🌟 #Gratitude #BlogCommunity #Inspiration 💻📝