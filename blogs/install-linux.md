---
layout: default
title: Installing Linux for the first time of my life
---

[« Home](https://jedsadasrijunpoe.github.io/)

<h1>Installing Linux for the first time of my life</h1>

Hi! In this blog, I will show you how I installed Linux for the first time of my life :D

- [1. Install WSL](#1-install-wsl)
- [2. Install ubuntu 22.04](#2-install-ubuntu-2204)
- [3. Try using Basic WSL2 Commands](#3-try-using-basic-wsl2-commands)
  - [3.1. Check which version of WSL you are running](#31-check-which-version-of-wsl-you-are-running)
  - [3.2. Install a specific Linux distribution](#32-install-a-specific-linux-distribution)
  - [3.3. Unregister or uninstall a Linux distribution](#33-unregister-or-uninstall-a-linux-distribution)
- [4. Try using Basic Ubuntu Commands](#4-try-using-basic-ubuntu-commands)
- [5. Run Linux GUI apps on the Windows Subsystem for Linux](#5-run-linux-gui-apps-on-the-windows-subsystem-for-linux)
  - [5.1. Prerequisites](#51-prerequisites)
  - [5.2. Run Linux GUI apps](#52-run-linux-gui-apps)
    - [5.2.1. Update the packages in your distribution](#521-update-the-packages-in-your-distribution)
    - [5.2.2. Install Gedit](#522-install-gedit)
    - [5.2.3. Install Nautilus](#523-install-nautilus)


# 1. Install WSL

---

I followed [Install Linux on Windows with WSL documentation](https://docs.microsoft.com/en-us/windows/wsl/install) to install Linux on Windows with WSL

First, I opened *Windows Command Prompt* with administrator and run this command

```shell
wsl --install
```

![install wsl1](/images/Screenshot%202022-07-31%20124136.png)
![install wsl2](/images/Screenshot%202022-07-31%20124321.png)

This command will download the latest Linux kernel, set WSL 2 as your default, and install a Linux distribution for you (Ubuntu by default) and then I restarted my PC

# 2. Install ubuntu 22.04

---

I searched *"Ubuntu"* in Microsoft Store and downloaded **Ubuntu 22.04 LTS** because it has 5 stars review :D

![install ubuntu1](/images/Screenshot%202022-08-03%20123001.png)
![install ubuntu2](/images/Screenshot%202022-08-03%20123024.png)

I opened it up and created a default UNIX user account

![install ubuntu3](/images/Screenshot%202022-08-03%20124746.png)
![install ubuntu4](/images/Screenshot%202022-08-03%20124818.png)
![install ubuntu5](/images/Screenshot%202022-08-03%20124923.png)
![install ubuntu6](/images/Screenshot%202022-08-03%20125925.png)

# 3. Try using Basic WSL2 Commands

---

I followed this [Basic commands for WSL documentation](https://docs.microsoft.com/en-us/windows/wsl/basic-commands)

## 3.1. Check which version of WSL you are running

```shell
wsl -l -v
```

This command will list your installed Linux distributions

![wsl basic command1](/images/Screenshot%202022-08-04-201642-wsl-command.png)

> - The first **Ubuntu** is the default Linux distributions that  
will install for you when you run `wsl --install`  
> - The second **Ubuntu-22.04** is the Ubuntu that I downloaded from Microsoft Store

Next, I selected **Ubuntu-22.04** with this command

```shell
wsl -s "Ubuntu-22.04"
```

![wsl basic command2](\images\Screenshot-2022-08-04-205556-wsl-command.png)

To terminate the specified distribution use this command

```shell
wsl --t "Ubuntu-22.04"
```

![wsl basic command3](\images\Screenshot-2022-08-04-212439-wsl-command.png)

## 3.2. Install a specific Linux distribution

This command will show you a list of the Linux distributions to install

```shell
wsl -l -o
```

![wsl basic command4](\images\Screenshot-2022-08-04-213744-wsl-command.png)

To install a specific Linux distribution use this command

```shell
wsl --install -d <Distro>
```

I installed **Debian**

![wsl basic command5](\images\Screenshot-2022-08-04-214251-wsl-command.png)
![wsl basic command6](\images\Screenshot-2022-08-04-214334-wsl-command.png)
![wsl basic command7](\images\Screenshot-2022-08-04-214406-wsl-command.png)

## 3.3. Unregister or uninstall a Linux distribution

To unregister and uninstall a WSL distribution:

```shell
wsl --unregister <DistributionName>
```

I uninstalled **Debian**

![wsl basic command8](\images\Screenshot-2022-08-04-214930-wsl-command.png)

# 4. Try using Basic Ubuntu Commands

---

![Ubuntu Commands1](\images\Screenshot-2022-08-04-224850-ubuntu-commands.png)
![Ubuntu Commands1](\images\Screenshot-2022-08-04-225046-ubuntu-commands.png)

# 5. Run Linux GUI apps on the Windows Subsystem for Linux

---

I followed [this documentations](https://docs.microsoft.com/en-us/windows/wsl/tutorials/gui-apps)

>Support for GUI apps on WSL does not provide a full desktop experience. It relies on Windows desktop, so installing desktop-focused tools or apps may not be supported.

## 5.1. Prerequisites

- You will need to be on Windows 11 Build 22000 or later to access this feature.
- Installed driver for vGPU

If you already have WSL installed on your machine, you can update to the latest version that includes Linux GUI support by running the update command from an elevated command prompt.

```shell
wsl --update
```

You will need to restart WSL for the update to take effect.

```shell
wsl --shutdown
```

## 5.2. Run Linux GUI apps

### 5.2.1. Update the packages in your distribution

```Bash
sudo apt update
```

### 5.2.2. Install Gedit

Gedit is the default text editor of the GNOME desktop environment.

```Bash
sudo apt install gedit -y
```

![gedit1](\images\Screenshot-2022-08-05-000105-linux-gui-apps.png)

Run `gedit` to open Untitled Document text

![gedit2](\images\Screenshot-2022-08-05-000531-linux-gui-apps.png)
![gedit3](\images\Screenshot-2022-08-05-000622-linux-gui-apps.png)

You can run `gedit <file name>` to open or create text file

![gedit4](\images\Screenshot-2022-08-05-000953-linux-gui-apps.png)
![gedit5](\images\Screenshot-2022-08-05-001027-linux-gui-apps.png)
![gedit6](\images\Screenshot-2022-08-05-001237-linux-gui-apps.png)

Open existing file

![gedit7](\images\Screenshot-2022-08-05-001319-linux-gui-apps.png)
![gedit7](\images\Screenshot-2022-08-05-001348-linux-gui-apps.png)

### 5.2.3. Install Nautilus

Nautilus, also known as GNOME Files, is the file manager for the GNOME desktop. (Similar to Windows File Explorer).

```Bash
sudo apt install nautilus -y
```

![nautilus1](\images\Screenshot-2022-08-05-003055-nautilus.png)

To launch, enter: `nautilus`

![nautilus2](\images\Screenshot-2022-08-05-003221-nautilus.png)
![nautilus3](\images\Screenshot-2022-08-05-003248-nautilus.png)
