---
title: "Understanding package manager and systemctl"
datePublished: Sun Jul 02 2023 04:14:06 GMT+0000 (Coordinated Universal Time)
cuid: cljkx3ytb00020ali06dman6f
slug: understanding-package-manager-and-systemctl
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688271179580/60f8e9b6-74b4-4dc1-b492-2ea4d735586b.png
tags: ubuntu, linux, system-architecture, linux-for-beginners, linux-commands

---

# **What is a package manager in Linux?**

In simpler words, a package manager is a tool that allows users to install, remove, upgrade, configure and manage software packages on an operating system. The package manager can be a graphical application like a software center or a command line tool like apt-get, YUM or pacman.

# **What is a package?**

A package is usually referred to an application but it could be a GUI application, command line tool or a software library (required by other software programs). A package is essentially an archive file containing the binary executable, configuration file and sometimes information about the dependencies.

# **Different kinds of package managers**

Package Managers differ based on packaging system but same packaging system may have more than one package manager.

For example, RPM has Yum and DNF package managers. For DEB, you have apt-get, aptitude command line based package managers.

## **Task 1: You have to install docker and Jenkins in your system from your terminal using package managers**

![](https://miro.medium.com/v2/resize:fit:450/1*v0qG5yE5FMe4pOrvXHkUHg.png align="left")

**Commands used to install Docker and Manage Docker :**

1. Remove any Docker files that are running in the system, using the following command:
    

```bash
$ sudo apt-get remove docker docker-engine docker.io
```

2\. Check if the system is up-to-date using the following command:

```bash
$ sudo apt-get update
```

3\. Install Docker using the following command:

```bash
$ sudo apt install docker.io
```

![](https://miro.medium.com/v2/resize:fit:700/1*xg1MQvMdB-CZwT5Dt22l5A.png align="left")

4\. Install all the dependency packages using the following command:

```bash
$ sudo snap install docker
```

![](https://miro.medium.com/v2/resize:fit:700/1*Ds2z2Vnv2utz4IqCzi5JEA.png align="left")

5\. Before testing Docker, check the version installed using the following command:

```bash
$ docker --version
```

![](https://miro.medium.com/v2/resize:fit:700/1*O_w1C4Cw_xI5-rYGZSR6eg.png align="left")

6 . Pull an image from the Docker hub using the following command:

```bash
$ sudo docker run hello-world
```

Here, *hello-world* is the docker image present on the Docker hub.

7\. Check if the docker image has been pulled and is present in your system using the following command:

```bash
$ sudo docker images
```

![](https://miro.medium.com/v2/resize:fit:700/1*OUuDFYt6T0NfNwlP5DigMQ.png align="left")

8\. To display all the containers pulled, use the following command:

```bash
$ sudo docker ps -a
```

![](https://miro.medium.com/v2/resize:fit:700/1*u36KjjsV-ea48OT5t5Mg_Q.png align="left")

9\. To check for containers in a running state, use the following command:

```bash
$ sudo docker ps
```

![](https://miro.medium.com/v2/resize:fit:700/1*Tm05LyI39SgdWtjORo-Eug.png align="left")

You’ve just successfully installed Docker on Ubuntu!

**Install Jenkins:-**

Check the below website for step-by-step installation of Jenkins on your Ubuntu server.

## [**How To Install Jenkins on Ubuntu 22.04 | DigitalOcean**](https://www.digitalocean.com/community/tutorials/how-to-install-jenkins-on-ubuntu-22-04)

### [Jenkins is an open-source automation server that automates the repetitive technical tasks involved in the continuous…](https://www.digitalocean.com/community/tutorials/how-to-install-jenkins-on-ubuntu-22-04)

[www.digitalocean.com](http://www.digitalocean.com)

# **What is systemctl and systemd ?**

`systemd` is a Linux init system and system manager that is widely used in modern Linux distributions as the default init system. It provides a way to manage and control the various services that run on a Linux system, as well as other system-level functionality.

`systemctl` is the command line tool used to control and manage the `systemd` system and service manager. It provides various commands to start, stop, restart, enable, and disable services, as well as other functionalities such as inspecting the status of services, displaying log messages, and managing system-level settings and configurations.

Here are a few examples of common tasks that can be performed using `systemctl`:

* Start a service: `systemctl start <service-name>`
    
* Stop a service: `systemctl stop <service-name>`
    
* Restart a service: `systemctl restart <service-name>`
    
* Enable a service to start automatically at boot: `systemctl enable <service-name>`
    
* Disable a service from starting automatically at boot: `systemctl disable <service-name>`
    
* Check the status of a service: `systemctl status <service-name>`
    

Overall, `systemd` and `systemctl` provide a centralized and standardized way to manage services and other system-level components on Linux, making it easier to configure and maintain a Linux system.

1. **check the status of docker service in your system (make sure you completed above tasks, else docker won’t be installed)**
    

![](https://miro.medium.com/v2/resize:fit:700/1*-BuW2Rwgu1QwhXpoRud8Yw.png align="left")

**2\. stop the service Jenkins and post before and after screenshots**

Before :

![](https://miro.medium.com/v2/resize:fit:700/1*EkjfLmQjO9jFbxh83C_ynA.png align="left")

After:

#systemctl stop jenkins

#systemctl status jenkins

![](https://miro.medium.com/v2/resize:fit:700/1*j1-vdQRXL4FzEO1PiXnZiQ.png align="left")

3\. Read about the commands systemctl vs service

`systemctl` and `service` are both tools used to manage and control services on a Linux system. However, they have some differences:

1. `systemctl` is the newer tool and is used on systems that use the Systemd init system, which is now widely adopted as the default init system for many popular Linux distributions, including Fedora, Red Hat Enterprise Linux, and Ubuntu.
    
2. `service` is the older tool and is used on systems that use the System V init system, which was the previous standard init system used in many popular Linux distributions.
    
3. `systemctl` provides more advanced features compared to `service`, such as the ability to manage units, which are the basic building blocks of Systemd. This allows you to manage not just services, but also other system components, such as sockets, devices, and mount points, with a unified interface.
    
4. `service` is limited to managing services only, and its syntax and options are not as advanced as those of `systemctl`.
    
    Package Manager Commands:
    
    1. APT (Debian/Ubuntu):
        
        * `sudo apt update`: Updates the local package repository.
            
        * `sudo apt upgrade`: Upgrades installed packages to their latest versions.
            
        * `sudo apt install package_name`: Installs a specific package.
            
        * `sudo apt remove package_name`: Removes a specific package.
            
        * `sudo apt search package_name`: Searches for a package in the repository.
            
        * `sudo apt autoremove`: Removes unused packages and their dependencies.
            
    2. DNF (Fedora/RHEL):
        
        * `sudo dnf update`: Updates the local package repository.
            
        * `sudo dnf upgrade`: Upgrades installed packages to their latest versions.
            
        * `sudo dnf install package_name`: Installs a specific package.
            
        * `sudo dnf remove package_name`: Removes a specific package.
            
        * `sudo dnf search package_name`: Searches for a package in the repository.
            
        * `sudo dnf autoremove`: Removes unused packages and their dependencies.
            
    3. Pacman (Arch Linux):
        
        * `sudo pacman -Syu`: Updates the local package repository and upgrades all packages.
            
        * `sudo pacman -S package_name`: Installs a specific package.
            
        * `sudo pacman -R package_name`: Removes a specific package.
            
        * `sudo pacman -Ss package_name`: Searches for a package in the repository.
            
        * `sudo pacman -Sc`: Deletes the old versions of installed packages.
            
    
    Systemctl Commands:
    
    1. Managing Services:
        
        * `sudo systemctl start service_name`: Starts a service.
            
        * `sudo systemctl stop service_name`: Stops a service.
            
        * `sudo systemctl restart service_name`: Restarts a service.
            
        * `sudo systemctl enable service_name`: Enables a service to start at boot.
            
        * `sudo systemctl disable service_name`: Disables a service from starting at boot.
            
    2. Checking Service Status:
        
        * `sudo systemctl status service_name`: Shows the status and information of a service.
            
        * `sudo systemctl is-active service_name`: Checks if a service is active.
            
        * `sudo systemctl is-enabled service_name`: Checks if a service is enabled.
            
        * `sudo systemctl is-failed service_name`: Checks if a service has failed.
            
    
    Package Manager Tips:
    
    1. Updating Package Lists:
        
        * Before installing or upgrading packages, it's a good practice to update the package lists first. Use the command `sudo apt update` (for APT) or `sudo dnf update` (for DNF) to ensure you have the latest information about available packages.
            
    2. Package Repository Management:
        
        * You can manage software sources and repositories by editing the appropriate configuration files. For example, in Ubuntu, you can modify the repository sources in the `/etc/apt/sources.list` file or add new sources in `/etc/apt/sources.list.d/` directory.
            
    3. Package Version Locking:
        
        * Sometimes, you may want to prevent a package from being upgraded to a newer version. Package managers offer a version locking feature for this purpose. For example, in APT, you can use the `sudo apt-mark hold package_name` command to prevent a package from being upgraded.
            
    
    Systemctl Tips:
    
    1. Checking Service Logs:
        
        * You can view the logs generated by a service using the `journalctl` command. For example, to view the logs of the Apache web server, you can use `sudo journalctl -u apache2`.
            
    2. Service Dependency Management:
        
        * Services can have dependencies on other services. You can specify service dependencies in the unit files located in `/etc/systemd/system/`. Use the `Requires` and `After` directives to define dependencies between services.
            
    3. Service Configuration Reloading:
        
        * After making changes to a service's configuration file, you can reload the configuration without restarting the service. Use the command `sudo systemctl reload service_name` to apply the changes.
            
    
    Example Usage:
    
    1. Installing a package:
        
        * Suppose you want to install the `nginx` web server using APT. You can run the following commands:
            
            ```bash
            sudo apt update
            sudo apt install nginx
            ```
            
        * This will update the package lists and then install the `nginx` package along with its dependencies.
            
    2. Enabling and starting a service:
        
        * Let's say you want to enable and start the `apache2` service using systemctl. You can use the following commands:
            
            ```bash
            sudo systemctl enable apache2
            sudo systemctl start apache2
            ```
            
        * This will enable the `apache2` service to start at boot and then start the service immediately.
            
    3. Checking the status of a service:
        
        * To check the status of the `sshd` service, you can use the command:
            
            ```bash
            sudo systemctl status sshd
            ```
            
        * This will display information about the current status, whether the service is active, and any recent logs related to the service.
            
    
    These tips and examples should help you get started with package managers and systemctl in Linux. Remember to adjust the commands based on your specific Linux distribution and package manager.