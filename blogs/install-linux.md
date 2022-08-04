# Install Linux
Hi! In this blog, I will show you how I installed Linux for the first time of my life :D
## 1. Install WSL

---

I followed [Install Linux on Windows with WSL documentation](https://docs.microsoft.com/en-us/windows/wsl/install) to install Linux on Windows with WSL

First, I opened *Windows Command Prompt* with administrator and run this command
```shell
wsl --install
```

![install wsl1](/images/Screenshot%202022-07-31%20124136.png)
![install wsl2](/images/Screenshot%202022-07-31%20124321.png)

This command will download the latest Linux kernel, set WSL 2 as your default, and install a Linux distribution for you (Ubuntu by default) and then I restarted my PC

## 2. Install ubuntu 22.04

---

I searched *"Ubuntu"* in Microsoft Store and downloaded **Ubuntu 22.04 LTS** because it has 5 stars review :D
![install ubuntu1](/images/Screenshot%202022-08-03%20123001.png)
![install ubuntu2](/images/Screenshot%202022-08-03%20123024.png)

I opened it up and created a default UNIX user account

![install ubuntu3](/images/Screenshot%202022-08-03%20124746.png)
![install ubuntu4](/images/Screenshot%202022-08-03%20124818.png)
![install ubuntu5](/images/Screenshot%202022-08-03%20124923.png)
![install ubuntu6](/images/Screenshot%202022-08-03%20125925.png)

## 3. Try using Basic WSL2 Commands

---

I followed [Basic commands for WSL documentation](https://docs.microsoft.com/en-us/windows/wsl/basic-commands)
### Check which version of WSL you are running
```shell
wsl -l -v
```
This command will list your installed Linux distributions
![wsl basic command1](/images/Screenshot%202022-08-04-201642-wsl-command.png)
> The first **Ubuntu** is the default Linux distributions that will install for you when you run `wsl --install`  
> The second **Ubuntu-22.04** is the Ubuntu that I downloaded from Microsoft Store

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

### Install a specific Linux distribution
This command will show you a list of the Linux distributions to install
```shell
wsl -l -o
```
![wsl basic command4](\images\Screenshot-2022-08-04-213744-wsl-command.png)

To install a specific Linux distribution use this command
```shell
wsl --install -d <Distro>
```
I try install **Debian**
![wsl basic command5](\images\Screenshot-2022-08-04-214251-wsl-command.png)
![wsl basic command6](\images\Screenshot-2022-08-04-214334-wsl-command.png)
![wsl basic command7](\images\Screenshot-2022-08-04-214406-wsl-command.png)

### Unregister or uninstall a Linux distribution
To unregister and uninstall a WSL distribution:
```shell
wsl --unregister <DistributionName>
```
I try uninstall **Debian**
![wsl basic command8](\images\Screenshot-2022-08-04-214930-wsl-command.png)


## 4. Try using Bacsic Ubuntu Commands

---

I followed [Ubuntu command line for beginners tutorial](https://ubuntu.com/tutorials/command-line-for-beginners#1-overview)



