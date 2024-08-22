
Let me preface this by acknowledging that there are two different tools that share the name 'Legion.' While they might seem similar at first glance, they serve different purposes and originate from different developers. The first is developed by carlospolop and focuses on automating network service enumeration during penetration tests. The second, from GoVanguard, is a more extensive network penetration testing framework, offering a wide array of features including a graphical user interface and modular functionality. Though they share the same name, these tools have distinct characteristics and should be used according to your specific needs. I'm including both in this section because, despite their differences, each can significantly enhance your penetration testing process during the OSCP, offering complementary functionalities that can streamline your workflow
# LEGION - Automatic Enumeration Tool

[](https://github.com/carlospolop/legion#legion---automatic-enumeration-tool)

**Legion is based in the Pentesting Methodology that you can find in [book.hacktricks.xyz](https://book.hacktricks.xyz/pentesting-methodology).**

Legion is a tool that uses several well-known opensource tools to automatically, semi-automatically or _manually_ enumerate the most frequent found services running in machines that you could need to pentest.

Basically, the goal of Legion is to extract all the information that you can from each opened network service, so you don't have to write and execute the same commands in a terminal every time you find that service. Some actions are repeated by more than one tool, this is done to be sure that all the possible information is correctly extracted.

[![asciicast](https://camo.githubusercontent.com/dd668e531fbb9c18b7c18438105605cf2a3dcabe028ef8c2450323fa40a76ae4/68747470733a2f2f61736369696e656d612e6f72672f612f3235303533392e706e67)](https://asciinema.org/a/250539)

## Installation

[](https://github.com/carlospolop/legion#installation)

### Installation of Legion

[](https://github.com/carlospolop/legion#installation-of-legion)

```shell
git clone https://github.com/carlospolop/legion.git /opt/legion
cd /opt/legion/git
./install.sh
ln -s /opt/legion/legion.py /usr/bin/legion
```

For pentesting oracle services you should install manually some dependencies: [https://book.hacktricks.xyz/pentesting/1521-1522-1529-pentesting-oracle-listener/oracle-pentesting-requirements-installation](https://book.hacktricks.xyz/pentesting/1521-1522-1529-pentesting-oracle-listener/oracle-pentesting-requirements-installation)

### Docker

[](https://github.com/carlospolop/legion#docker)

To have a nice experience with `legion` you can also build a container image using `docker` or `podman`, just typing the following commands:

`docker build -t legion .`

And start the container:

`docker run -it legion bash`

You will have a ready-to-use `legion` container image (To execute legion inside the container run `./legion.py`).

Or you can just download the dockerhub container with:

`docker pull carlospolop/legion:latest`

## Protocols Supported

[](https://github.com/carlospolop/legion#protocols-supported)

You can get a list using the command `protos`

[![](https://github.com/carlospolop/legion/raw/master/images/legion-protos.png)](https://github.com/carlospolop/legion/blob/master/images/legion-protos.png)

## Brute force

[](https://github.com/carlospolop/legion#brute-force)

All the protocols included in Legion that could be brute force, can be brute force using Legion. To see if a service can be brute forced and which command line will be used to do so (by default "hydra" is implemented, if hydra was not available metasploit or nmap will be used) set the protocol and the set the intensity to "3".

Example of brute forcing ssh:

[![](https://github.com/carlospolop/legion/raw/master/images/legion-brute.png)](https://github.com/carlospolop/legion/blob/master/images/legion-brute.png)

## Internal Commands

[](https://github.com/carlospolop/legion#internal-commands)

[![](https://github.com/carlospolop/legion/raw/master/images/internal-commands.png)](https://github.com/carlospolop/legion/blob/master/images/internal-commands.png)

Use the `help` internal command to get info about what each command does.

## Automatic Scan

[](https://github.com/carlospolop/legion#automatic-scan)

Just lauch the internal command `startGeneral` and the '**General**' will start scanning ports and services automatically.

## Semi-Automatic Scan

[](https://github.com/carlospolop/legion#semi-automatic-scan)

You can set all the options properly and launch several commands to scan one service. You can do this using the command `run`.

## Manual Scan

[](https://github.com/carlospolop/legion#manual-scan)

You can execute just one command using `exec <name>`. For example: `exec http_slqmap`

Some services have _on demand commands_, this commands can only be executed using this internal command (`exec`).

## Options

[](https://github.com/carlospolop/legion#options)

[![](https://github.com/carlospolop/legion/raw/master/images/legion-options.png)](https://github.com/carlospolop/legion/blob/master/images/legion-options.png)

### domain

[](https://github.com/carlospolop/legion#domain)

Set the domain of the DNS or of the user that you want to use

### extensions

[](https://github.com/carlospolop/legion#extensions)

Comma separeted list of possible extensions (to brute force files in a web server)

### host

[](https://github.com/carlospolop/legion#host)

It is the host that you want to attack (valid IP and domains)

Example:

```
set host 127.0.0.1
set host some.domain.com
```

### intensity

[](https://github.com/carlospolop/legion#intensity)

There are 3 intensities:

- **1**: Basic checks executed
- **2**: All checks executed (Default)
- **3**: Brute force (check for availability)

### ipv6

[](https://github.com/carlospolop/legion#ipv6)

Ipv6 address of the victim, could be usefull for some commands

### notuse

[](https://github.com/carlospolop/legion#notuse)

You can set a list (separated by commands) of commands that you don't want to use. For example, if you don't want modules from metasploit to be executed:`set notuse msf`.

### password

[](https://github.com/carlospolop/legion#password)

Set here the password of the username you want to use.

### path

[](https://github.com/carlospolop/legion#path)

Web server file path

### plist

[](https://github.com/carlospolop/legion#plist)

Set here the path to a list of passwords (by default LEGION has its own list)

### port

[](https://github.com/carlospolop/legion#port)

The port where the service is running. If "0", then the default port of the service will be used (you can see this information using `info`)

### proto

[](https://github.com/carlospolop/legion#proto)

It is the protocol that you want to attack

Example:

```
set proto http
```

### reexec

[](https://github.com/carlospolop/legion#reexec)

Set `True` if you want already executed commands to be executed again (by default is set to False).

### ulist

[](https://github.com/carlospolop/legion#ulist)

Set a value here if you want to brute force a list of usernames (by default LEGION has its own list of usernames)

### username

[](https://github.com/carlospolop/legion#username)

Set the username of the user that you want to use/brute-force(by default to brute-force a list of users is used).

### verbose

[](https://github.com/carlospolop/legion#verbose)

If `True` the output of the command will be displayed as soon as it ends. If `False` it won't.

If `True` the output of `info` will show where each parameter is used, for example:

[![](https://github.com/carlospolop/legion/raw/master/images/info-verbose-true.png)](https://github.com/carlospolop/legion/blob/master/images/info-verbose-true.png)

If `False` the output of `info` will show the values of the parameters, for example:

[![](https://github.com/carlospolop/legion/raw/master/images/info-verbose-false.png)](https://github.com/carlospolop/legion/blob/master/images/info-verbose-false.png)

### workdir

[](https://github.com/carlospolop/legion#workdir)

Is the directory where the info of the victim is storaged. By default it is `$HOME/.legion`

By Polop(TM)

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/carlospolop/legion). Be sure to check out the original post for more details.



[![alt tag](https://github.com/GoVanguard/legion/raw/master/images/LegionBanner.png)](https://github.com/GoVanguard/legion/blob/master/images/LegionBanner.png)

## ✨ About

[](https://github.com/GoVanguard/legion#-about)

Legion, a fork of SECFORCE's Sparta, is an open source, easy-to-use, super-extensible, and semi-automated network penetration testing framework that aids in discovery, reconnaissance, and exploitation of information systems.

## Fix NMAP 7.92 Sefgaults under Kali

[](https://github.com/GoVanguard/legion#fix-nmap-792-sefgaults-under-kali)

Install NMAP 7.93 using the following:

```shell
sudo apt install snapd -y
sudo systemctl enable --now snapd.apparmor
sudo systemctl start snapd
sudo snap install nmap
sudo mv /usr/bin/nmap /usr/bin/nmap-7.92
sudo ln -s /snap/bin/nmap /usr/bin/nmap
```

Then verify the version is 7.93 with: `nmap -v`

Update the apparmor profile: `vi /var/lib/snapd/apparmor/profiles/snap.nmap.nmap`

Goto line 300, create new line and add in:

```
owner @{HOME}/.local/share/legion/tmp/** rw,
/etc/ssl/kali.cnf r,
```

Reboot

## 🍿 Features

[](https://github.com/GoVanguard/legion#-features)

- Automatic recon and scanning with NMAP, whataweb, nikto, Vulners, Hydra, SMBenum, dirbuster, sslyzer, webslayer and more (with almost 100 auto-scheduled scripts).
- Easy to use graphical interface with rich context menus and panels that allow pentesters to quickly find and exploit attack vectors on hosts.
- Modular functionality allows users to easily customize Legion and automatically call their own scripts/tools.
- Multiple custom scan configurations ideal for testing different environments of various size and complexity.
- Highly customizable stage scanning for ninja-like IPS evasion.
- Automatic detection of CPEs (Common Platform Enumeration) and CVEs (Common Vulnerabilities and Exposures).
- Ties CVEs to Exploits as detailed in Exploit-Database.
- Realtime auto-saving of project results and tasks.

### Notable changes from Sparta

[](https://github.com/GoVanguard/legion#notable-changes-from-sparta)

- Refactored from Python 2.7 to Python 3.8+ and the elimination of deprecated and unmaintained libraries.
- Upgraded to PyQT6, increased responsiveness, less buggy, more intuitive GUI that includes features like:
    - Task completion estimates
    - 1-Click scan lists of ips, hostnames and CIDR subnets
    - Ability to purge results, rescan hosts and delete hosts
    - Granular NMAP scanning options
- Support for hostname resolution and scanning of vhosts/sni hosts.
- Revise process queuing and execution routines for increased app reliability and performance.
- Simplification of installation with dependency resolution and installation routines.
- Realtime project auto-saving so in the event some goes wrong, you will not lose any progress!
- Docker container deployment option.
- Supported by a highly active development team.

## 🌉 Supported Distributions

[](https://github.com/GoVanguard/legion#-supported-distributions)

### Docker runIt script support

[](https://github.com/GoVanguard/legion#docker-runit-script-support)

RunIt script (`docker/runIt.sh`) supports:

- Ubuntu 20.04+
- Kali 2022+

It is possible to run the docker image on any Linux distribution, however, different distributions have different hoops to jump through to get a docker app to be able to connect to the X server. Everyone is welcome to try to figure those hoops out and create a PR for runIt.

### Traditional installation support

[](https://github.com/GoVanguard/legion#traditional-installation-support)

We can only promise correct operation on **Ubuntu 20.04** using the traditional installation at this time. While it should work on ParrotOS, Kali, and others, until we have Legion packaged and placed into the repos for each of these distros, it is musical chairs in regard to platform updates changing and breaking dependencies. Native a native package exists and is included by default on Kali.

## 💻 Installation

[](https://github.com/GoVanguard/legion#-installation)

Two installation methods available:

- [Docker method](https://github.com/GoVanguard/legion#traditional-installation-method)
- [Traditional installation method](https://github.com/GoVanguard/legion#traditional-installation-method)

It is **preferable** to use the Docker method over a traditional installation. This is because of all the dependency requirements and the complications that occur in environments which differ from a clean, non-default installation.

> NOTE: Docker versions of Legion are _unlikely_ to work when run as root or under a root X!

### Docker method

[](https://github.com/GoVanguard/legion#docker-method)

Docker method includes support for various environments, choose the one that works for you.

- [Linux with local X11](https://github.com/GoVanguard/legion#linux-with-local-x11)
- [Linux with remote X11](https://github.com/GoVanguard/legion#linux-with-remote-x11)
- [Windows under WSL](https://github.com/GoVanguard/legion#windows-under-wsl-using-xming-and-docker-desktop)
- [⚠️ Windows without WSL](https://github.com/GoVanguard/legion#windows-using-xming-and-docker-desktop-without-wsl)
- [⚠️ OSX using XQuartz](https://github.com/GoVanguard/legion#osx-using-xquartz)

#### Linux with local X11

[](https://github.com/GoVanguard/legion#linux-with-local-x11)

Assumes **Docker** and **X11** are installed and set up (including running Docker commands as a non-root user).

It is critical to follow all the instructions for running as a non-root user. Skipping any of them will result in complications getting Docker to communicate with the X server.

See detailed instructions to set up Docker [here](https://github.com/GoVanguard/legion#configuring-docker) and enable running containers as non-root users and granting Docker group SSH rights [here](https://github.com/GoVanguard/legion#setup-docker-to-allow-non-root-users).

Within Terminal:

```shell
git clone https://github.com/GoVanguard/legion.git
cd legion/docker
chmod +x runIt.sh
./runIt.sh
```

#### Linux with remote X11

[](https://github.com/GoVanguard/legion#linux-with-remote-x11)

Assumes **Docker** and **X11** are installed and set up.

Replace `X.X.X.X` with the IP address of the remote running X11.

Within Terminal:

```shell
git clone https://github.com/GoVanguard/legion.git
cd legion/docker
chmod +x runIt.sh
./runIt.sh X.X.X.X
```

#### Windows under WSL using Xming and Docker Desktop

[](https://github.com/GoVanguard/legion#windows-under-wsl-using-xming-and-docker-desktop)

Assumes:

- Xming is installed in Windows.
- Docker Desktop is installed in Windows
- Docker Desktop is running in Linux containers mode
- Docker Desktop is connected to WSL.

See detailed Docker instructions [here](https://github.com/GoVanguard/legion#setup-hyper-v-docker-desktop-xming-and-wsl)

Replace `X.X.X.X` with the IP address with which Xming has registered itself. Right click Xming in system tray -> View log and see IP next to "XdmcpRegisterConnection: newAddress"

Within Terminal:

```shell
git clone https://github.com/GoVanguard/legion.git
cd legion/docker
sudo chmod +x runIt.sh
sudo ./runIt.sh X.X.X.X
```

#### Windows using Xming and Docker Desktop without WSL

[](https://github.com/GoVanguard/legion#windows-using-xming-and-docker-desktop-without-wsl)

Why? Don't do this. :)

#### OSX using XQuartz

[](https://github.com/GoVanguard/legion#osx-using-xquartz)

Not yet in `runIt.sh` script. Possible to set up using `socat`. See [instructions here](https://kartoza.com/en/blog/how-to-run-a-linux-gui-application-on-osx-using-docker/)

#### Configuring Docker

[](https://github.com/GoVanguard/legion#configuring-docker)

#### Setting up Docker on Linux

[](https://github.com/GoVanguard/legion#setting-up-docker-on-linux)

To install Docker components typically needed and add set up the environment for Docker, under a term, run:

```shell
sudo apt-get update
sudo apt-get install -y docker.io python3-pip -y
sudo groupadd docker
pip install --user docker-compose
```

#### Setup Docker to allow non-root users

[](https://github.com/GoVanguard/legion#setup-docker-to-allow-non-root-users)

To enable non-root users to run Docker commands, under a term, run:

```shell
sudo usermod -aG docker $USER
sudo chmod 666 /var/run/docker.sock
sudo xhost +local:docker
```

#### Setup Hyper-V, Docker Desktop, Xming and WSL

[](https://github.com/GoVanguard/legion#setup-hyper-v-docker-desktop-xming-and-wsl)

The order is important for port reservation reasons. If you have WSL, HyperV, or Docker Desktop installed then please uninstall those features before proceeding.

- Cortana / Search -> cmd -> Right click -> Run as Administrator
- To reserve the Docker port, under CMD, run:
    
    ```shell
    netsh int ipv4 add excludedportrange protocol=tcp startport=2375 numberofports=1
    ```
    
    - This will likely fail if you have Hyper-V already enabled or Docker Desktop installed
- To install Hyper-V, under CMD, run:
    
    ```shell
    dism.exe /Online /Enable-Feature:Microsoft-Hyper-V /All
    ```
    
- Reboot
- Cortana / Search -> cmd -> Right click -> Run as Administrator
- To install WSL, under CMD, run:
    
    ```shell
    dism.exe /Online /Enable-Feature /FeatureName:Microsoft-Windows-Subsystem-Linux
    ```
    
- Reboot
- Download from [https://hub.docker.com/editions/community/docker-ce-desktop-windows](https://hub.docker.com/editions/community/docker-ce-desktop-windows) (Free account required)
- Run installer
- Optionally input your Docker Hub login
- Right click Docker Desktop in system tray -> Switch to Linux containers
    - If it says Switch to Windows containers then skip this step, it's already using Linux containers
- Right click Docker Desktop in system tray -> Settings
- General -> Expose on localhost without TLS
- Download [https://sourceforge.net/projects/xming/files/Xming/6.9.0.31/Xming-6-9-0-31-setup.exe/download](https://sourceforge.net/projects/xming/files/Xming/6.9.0.31/Xming-6-9-0-31-setup.exe/download)
- Run installer and select multi window mode
- Open Microsoft Store
- Install Kali, Ubuntu or one of the other WSL Linux Distributions
- Open the distribution, let it bootstrap and fill in the user creation details
- To install Docker components typically needed and add set up the environment for Docker redirection, under the WSL window, run:
    
    ```shell
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
    sudo apt-get update
    sudo apt-get install -y docker-ce python-pip -y
    sudo apt autoremove
    sudo usermod -aG docker $USER
    pip install --user docker-compose
    echo "export DOCKER_HOST=tcp://localhost:2375" >> ~/.bashrc && source ~/.bashrc
    ```
    
- Test Docker is reachable with:
    
    ```shell
    docker images
    ```
    

### Traditional installation method

[](https://github.com/GoVanguard/legion#traditional-installation-method)

> Please use the Docker image where possible! It's becoming very difficult to support all the various platforms and their own quirks.

Assumes Ubuntu, Kali or Parrot Linux is being used with **Python 3.6** installed.

Within Terminal:

```shell
git clone https://github.com/GoVanguard/legion.git
cd legion
sudo chmod +x startLegion.sh
sudo ./startLegion.sh
```

## 🏗 Development

[](https://github.com/GoVanguard/legion#-development)

### Executing test cases

[](https://github.com/GoVanguard/legion#executing-test-cases)

To run all test cases, execute the following in root directory:

```shell
python -m unittest
```

### Modifying Configuration

[](https://github.com/GoVanguard/legion#modifying-configuration)

The configuration of selected ports and associated terminal actions can be easily modified by editing the legion.conf file.

> [StagedNmapSettings] defines what ports will be scanned in sequential order as well as any NSE scripts that will be called.
> 
> [SchedulerSettings] defines what actions will occur automatically based upon port scan results.

```shell
sudoedit /root/.local/share/legion/legion.conf
```

## ⚖️ License

[](https://github.com/GoVanguard/legion#%EF%B8%8F-license)

Legion is licensed under the GNU General Public License v3.0. Take a look at the [LICENSE](https://github.com/GoVanguard/legion/blob/master/LICENSE) for more information.

## ⭐️ Attribution

[](https://github.com/GoVanguard/legion#%EF%B8%8F-attribution)

- Refactored Python 3.6+ codebase, added feature set and ongoing development of Legion is credited to [GoVanguard](https://govanguard.com/)
- The initial Sparta Python 2.7 codebase and application design is credited SECFORCE.
- Several additional PortActions, PortTerminalActions and SchedulerSettings are credited to batmancrew.
- The nmap XML output parsing engine was largely based on code by yunshu, modified by ketchup and modified SECFORCE.
- ms08-067_check script used by `smbenum.sh` is credited to Bernardo Damele A.G.
- Legion relies heavily on nmap, hydra, python, PyQt, SQLAlchemy and many other tools and technologies, so we would like to thank all of the people involved in the creation of those.
- Special thanks to Dmitriy Dubson for his continued contributions to the project!

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/GoVanguard/legion). Be sure to check out the original post for more details.
# Legion Tool in Kali Linux

Last Updated : 24 Dec, 2020

If you are using Kali Linux 2020.1 or up, then instead of Sparta, Kali Linux comes with the Legion, fork version of Sparta with improved features. **Legion** tool is a super-extensible and semi-automated network penetration testing framework. Legion is very easy to operate. 

**Features of Legion Tool**:  

- GUI with panels and a long list of options that allow pentesters to quickly find and exploit attack vectors on hosts.
- It has the feature of real-time auto-saving of project results and tasks.
- Legion also provides services like Automatic recon and scanning with NMAP, whataweb, sslyzer, Vulners, webslayer, SMBenum, dirbuster, nikto, Hydra, and almost 100 auto-scheduled scripts are added to it.
- Modular functionality of Legion Tool allows users to easily customize Legion.
- Automatic detection of  CVEs (Common Vulnerabilities and Exposures and CPEs (Common Platform Enumeration).

**Notable changes from Sparta tool**:

- Legion tool provides estimates of Task completion.
- The elimination of deprecated and unmaintained libraries has been done as Legion is refactored from Python 2.7 to Python 3.6.
- Support for hostname resolution.
- Legion tool revises the processes in queue and execution routines for increased app reliability and performance.
- Legion has a real-time auto-saving of project tasks and results.
- Scanning of vhosts/sni hosts.
- Legion tool is supported by a highly-active development team.

**Installation of Legion tool**: Usually Legion tool comes pre-installed with Kali Linux but, if we need to install it we can run the following command :

sudo apt-get install legion -y

After the complete execution of the above command, you can start the legion tool from any terminal by simply “legion” command.

legion

![legion command in linux](https://media.geeksforgeeks.org/wp-content/uploads/20201219194630/Picture1.jpg)![legion command in linux](https://media.geeksforgeeks.org/wp-content/uploads/20201219194751/Picture2.jpg)

In the Hosts section, we have an option to add hosts to the scope. Simply click on add hosts and you will get the below screen :

![legion command in linux](https://media.geeksforgeeks.org/wp-content/uploads/20201219195140/Picture3.jpg)

Here we can add a single IP, a range of IPs, or hostnames in the section. In order to add multiple targets simply separate them with a semicolon. Then there is the option for Mode selection, in this section, we have Easy and Hard mode. In Easy mode, we got nmap scanning options like staged scan and nmap host discovery. In Hard mode, we get options like host discovery, custom port scanning, and custom discovery options. In the additional arguments we have -O flag for OS detection and -sV flag for service version.

**Performing scan with Legion Tool**: We are performing an Easy mode scan on yahoo.com with -sV and -O arguments.

![Performing scan with Legion Tool](https://media.geeksforgeeks.org/wp-content/uploads/20201219201525/Picture4.jpg)

We will get results as shown in the below image.

![Performing scan with Legion Too](https://media.geeksforgeeks.org/wp-content/uploads/20201219201711/Picture5.jpg)

**Credit:** This information was adapted from an excellent guide on [GeeksForGeeks](https://www.geeksforgeeks.org/legion-tool-in-kali-linux/). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/aotY9f06HcI?si=tNKQWZfb8IRPXGsz" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=aotY9f06HcI&t=3s). Be sure to check out the original post for more details.

