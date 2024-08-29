# enum4linux

[](https://github.com/CiscoCXSecurity/enum4linux#enum4linux)

A Linux alternative to enum.exe for enumerating data from Windows and Samba hosts.

Enum4linux is a tool for enumerating information from Windows and Samba systems. It attempts to offer similar functionality to enum.exe formerly available from [www.bindview.com](http://www.bindview.com/).

It is written in Perl and is basically a wrapper around the Samba tools smbclient, rpclient, net and nmblookup.

The tool usage can be found below followed by examples, previous versions of the tool can be found at the bottom of the page.

Also see: [https://labs.portcullis.co.uk/tools/enum4linux/](https://labs.portcullis.co.uk/tools/enum4linux/)

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/CiscoCXSecurity/enum4linux). Be sure to check out the original post for more details.

# Tool Documentation:

## enum4linux Usage Example

Attempt to get the userlist (`-U`) and OS information (`-o`) from the target (`192.168.1.200`):

```console
root@kali:~# enum4linux -U -o 192.168.1.200
Starting enum4linux v0.8.9 ( http://labs.portcullis.co.uk/application/enum4linux/ ) on Sun Aug 17 12:17:32 2014

 ==========================
|    Target Information    |
 ==========================
Target ........... 192.168.1.200
RID Range ........ 500-550,1000-1050
Username ......... ''
Password ......... ''
Known Usernames .. administrator, guest, krbtgt, domain admins, root, bin, none


 ======================================================
|    Enumerating Workgroup/Domain on 192.168.1.200   |
 ======================================================
[+] Got domain/workgroup name: KALI
```

---

  

# Packages and Binaries:

### enum4linux

Enum4linux is a tool for enumerating information from Windows and Samba systems. It attempts to offer similar functionality to enum.exe formerly available from [www.bindview.com](https://www.bindview.com/).

It is written in PERL and is basically a wrapper around the Samba tools smbclient, rpclient, net and nmblookup. The samba package is therefore a dependency.

Features include:

```console
 RID Cycling (When RestrictAnonymous is set to 1 on Windows 2000)
 User Listing (When RestrictAnonymous is set to 0 on Windows 2000)
 Listing of Group Membership Information
 Share Enumeration
 Detecting if host is in a Workgroup or a Domain
 Identifying the remote Operating System
 Password Policy Retrieval (using polenum)
```

**Installed size:** `58 KB`  
**How to install:** `sudo apt install enum4linux`

Dependencies:

- ldap-utils
- perl
- polenum
- samba
- smbclient

##### enum4linux

```console
root@kali:~# enum4linux -h
enum4linux v0.9.1 (http://labs.portcullis.co.uk/application/enum4linux/)
Copyright (C) 2011 Mark Lowe (mrl@portcullis-security.com)

Simple wrapper around the tools in the samba package to provide similar 
functionality to enum.exe (formerly from www.bindview.com).  Some additional 
features such as RID cycling have also been added for convenience.

Usage: ./enum4linux.pl [options] ip

Options are (like "enum"):
    -U        get userlist
    -M        get machine list*
    -S        get sharelist
    -P        get password policy information
    -G        get group and member list
    -d        be detailed, applies to -U and -S
    -u user   specify username to use (default "")  
    -p pass   specify password to use (default "")   

The following options from enum.exe aren't implemented: -L, -N, -D, -f

Additional options:
    -a        Do all simple enumeration (-U -S -G -P -r -o -n -i).
              This option is enabled if you don't provide any other options.
    -h        Display this help message and exit
    -r        enumerate users via RID cycling
    -R range  RID ranges to enumerate (default: 500-550,1000-1050, implies -r)
    -K n      Keep searching RIDs until n consective RIDs don't correspond to
              a username.  Impies RID range ends at 999999. Useful 
	      against DCs.
    -l        Get some (limited) info via LDAP 389/TCP (for DCs only)
    -s file   brute force guessing for share names
    -k user   User(s) that exists on remote system (default: administrator,guest,krbtgt,domain admins,root,bin,none)
              Used to get sid with "lookupsid known_username"
    	      Use commas to try several users: "-k admin,user1,user2"
    -o        Get OS information
    -i        Get printer information
    -w wrkg   Specify workgroup manually (usually found automatically)
    -n        Do an nmblookup (similar to nbtstat)
    -v        Verbose.  Shows full commands being run (net, rpcclient, etc.)
    -A        Aggressive. Do write checks on shares etc

RID cycling should extract a list of users from Windows (or Samba) hosts 
which have RestrictAnonymous set to 1 (Windows NT and 2000), or "Network 
access: Allow anonymous SID/Name translation" enabled (XP, 2003).

NB: Samba servers often seem to have RIDs in the range 3000-3050.

Dependancy info: You will need to have the samba package installed as this 
script is basically just a wrapper around rpcclient, net, nmblookup and 
smbclient.  Polenum from http://labs.portcullis.co.uk/application/polenum/ 
is required to get Password Policy info.

```

---

Updated on: 2024-Mar-11

**Credit:** This information was adapted from an excellent guide on [Kali.org](https://www.kali.org/tools/enum4linux/). Be sure to check out the original post for more details.

# Scanning for SMB Vulnerabilities with enum4linux


![](https://miro.medium.com/v2/resize:fit:700/1*2w4snot52gOqolLkcqe6CQ.jpeg)

Created by lexica.art

In the world of ethical hacking and penetration testing, understanding the vulnerabilities of SMB (Server Message Block) services is crucial. SMB is a protocol that enables file and print sharing between systems, primarily on Windows networks. In this lab, we will use the enum4linux tool, a powerful SMB enumeration tool, to discover information about SMB services on target systems. This information can be vital for identifying potential vulnerabilities and strengthening network security. Let’s walk through the objectives step by step.

# Part 1: Launch enum4linux and Explore Its Capabilities

## Step 1: Verify enum4linux Installation and View the Help File

1. **Access Kali Linux**: First, log in to your Kali Linux virtual machine using the username `**kali**` and the password `**kali**`. Open a terminal session.
2. **Gain Root Access**: Most enum4linux commands require root privileges. To obtain persistent root access, use the `**sudo su**` command.

┌──(kali㉿Kali)-[~]  
└─$sudo su

**3. View Help File**: To understand enum4linux’s capabilities and syntax, access the help file using the `**enum4linux --help**` command.

┌──(root㉿Kali)-[~]  
└─# enum4linux --help

The help file contains valuable information about the available options and the dependencies on Samba utilities.

> Which Samba utilities does the help file indicate are used by the enum4linux tool?
> 
> **The Samba utilities used by enum4linux are rpcclient, net, nmblookup, and smbclient.**

## Step 2: Research Terms Associated with SMB Functions

Understanding SMB-related terms is essential for interpreting enum4linux output effectively. Here are some terms and their definitions:

- **Relative Identifier (RID)**: Uniquely identifies a user, group, system, or domain.
- **Security Identifier (SID)**: Uniquely identifies users and groups within the local domain and can work globally between domains.
- **Domain Controller (DC)**: Manages network and identity security requests, authenticates users, and controls access to IT resources.
- **Lightweight Directory Access Protocol (LDAP)**: A directory access protocol enabling communication for services and clients using LDAP naming services.
- **Workgroup**: A group of standalone computers administered independently.

# Part 2: Use Nmap to Find SMB Servers

## Step 1: Scan Virtual Networks to Find Potential Targets

Identifying potential SMB targets involves scanning open ports. Common ports associated with SMB services include:

- TCP 135: RPC
- TCP 139: NetBIOS Session
- TCP 389: LDAP Server
- TCP 445: SMB File Service
- TCP 9389: Active Directory Web Services
- TCP/UDP 137: NetBIOS Name Service
- UDP 138: NetBIOS Datagram

1. **Scan 172.17.0.0 Virtual Network**: Use the `**nmap -sN**` command to find services on hosts in the 172.17.0.0 virtual network.

┌──(root㉿Kali)-[~]  
└─# nmap -sN 172.17.0.0/24  
Starting Nmap 7.94 ( https://nmap.org ) at 2023-10-03 12:10 UTC  
Nmap scan report for metasploitable.vm (172.17.0.2)  
Host is up (0.000010s latency).  
Not shown: 983 closed tcp ports (reset)  
PORT     STATE         SERVICE  
21/tcp   open|filtered ftp  
22/tcp   open|filtered ssh  
23/tcp   open|filtered telnet  
25/tcp   open|filtered smtp  
80/tcp   open|filtered http  
111/tcp  open|filtered rpcbind  
139/tcp  open|filtered netbios-ssn  
445/tcp  open|filtered microsoft-ds  
512/tcp  open|filtered exec  
513/tcp  open|filtered login  
514/tcp  open|filtered shell  
1099/tcp open|filtered rmiregistry  
1524/tcp open|filtered ingreslock  
2121/tcp open|filtered ccproxy-ftp  
3306/tcp open|filtered mysql  
5432/tcp open|filtered postgresql  
6667/tcp open|filtered irc  
MAC Address: 02:42:AC:11:00:02 (Unknown)  
  
Nmap scan report for 172.17.0.1 (172.17.0.1)  
Host is up (0.000010s latency).  
Not shown: 999 closed tcp ports (reset)  
PORT   STATE         SERVICE  
22/tcp open|filtered ssh  
  
Nmap done: 256 IP addresses (2 hosts up) scanned in 4.60 seconds

> What does Nmap reveal about hosts on the 172.17.0.0/24 network?
> 
> **Only one host is present, identified as 172.17.0.2.**
> 
> What ports are open on the host that identify running SMB services? What does Nmap call these services?
> 
> **The open ports on the host 172.17.0.2 are TCP 139 (netbios-ssn) and TCP 445 (microsoft-ds).**

**2. Scan 10.6.6.0/24 Subnet**: Perform a `**nmap -sN**` scan on the 10.6.6.0/24 subnet.

┌──(root㉿Kali)-[~]  
└─# nmap -sN 10.6.6.0/24                                                                          
Starting Nmap 7.94 ( https://nmap.org ) at 2023-10-03 12:10 UTC  
Nmap scan report for webgoat.vm (10.6.6.11)  
Host is up (0.000010s latency).  
Not shown: 997 closed tcp ports (reset)  
PORT     STATE         SERVICE  
8080/tcp open|filtered http-proxy  
8888/tcp open|filtered sun-answerbook  
9001/tcp open|filtered tor-orport  
MAC Address: 02:42:0A:06:06:0B (Unknown)  
  
Nmap scan report for juice-shop.vm (10.6.6.12)  
Host is up (0.000011s latency).  
Not shown: 999 closed tcp ports (reset)  
PORT     STATE         SERVICE  
3000/tcp open|filtered ppp  
MAC Address: 02:42:0A:06:06:0C (Unknown)  
  
Nmap scan report for dvwa.vm (10.6.6.13)  
Host is up (0.000011s latency).  
Not shown: 999 closed tcp ports (reset)  
PORT   STATE         SERVICE  
80/tcp open|filtered http  
MAC Address: 02:42:0A:06:06:0D (Unknown)  
  
Nmap scan report for mutillidae.vm (10.6.6.14)  
Host is up (0.000011s latency).  
Not shown: 998 closed tcp ports (reset)  
PORT     STATE         SERVICE  
80/tcp   open|filtered http  
3306/tcp open|filtered mysql  
MAC Address: 02:42:0A:06:06:0E (Unknown)  
  
Nmap scan report for gravemind.vm (10.6.6.23)  
Host is up (0.000011s latency).  
Not shown: 994 closed tcp ports (reset)  
PORT    STATE         SERVICE  
21/tcp  open|filtered ftp  
22/tcp  open|filtered ssh  
53/tcp  open|filtered domain  
80/tcp  open|filtered http  
139/tcp open|filtered netbios-ssn  
445/tcp open|filtered microsoft-ds  
MAC Address: 02:42:0A:06:06:17 (Unknown)  
  
Nmap scan report for 10.6.6.100 (10.6.6.100)  
Host is up (0.000011s latency).  
All 1000 scanned ports on 10.6.6.100 (10.6.6.100) are in ignored states.  
Not shown: 1000 closed tcp ports (reset)  
MAC Address: 02:42:0A:06:06:64 (Unknown)  
  
Nmap scan report for 10.6.6.1 (10.6.6.1)  
Host is up (0.000011s latency).  
Not shown: 999 closed tcp ports (reset)  
PORT   STATE         SERVICE  
22/tcp open|filtered ssh  
  
Nmap done: 256 IP addresses (7 hosts up) scanned in 4.70 seconds

> Are there any potential target computers on this subnet running SMB services? Which computer or computers? How do you know?
> 
> **Yes, the computer at 10.6.6.23 is a potential target. It has ports 139 and 445 open, indicating SMB services.**

# Part 3: Use enum4linux to Enumerate Users and Network File Shares

In this section, we will use enum4linux to gather more information about potential targets.

## Step 1: Perform enum4linux Scan on Target 172.17.0.2

1. **Enumerate Users**: Use the `**enum4linux -U**` option to list the users configured on the target 172.17.0.2. Remember to run enum4linux commands with root permissions.

┌──(root㉿Kali)-[~]  
└─# enum4linux -U 172.17.0.2  
Starting enum4linux v0.9.1 ( http://labs.portcullis.co.uk/application/enum4linux/ ) on Tue Oct  3 12:11:50 2023  
  
 =========================================( Target Information )=========================================  
  
Target ........... 172.17.0.2  
RID Range ........ 500-550,1000-1050  
Username ......... ''  
Password ......... ''  
Known Usernames .. administrator, guest, krbtgt, domain admins, root, bin, none  
  
  
 =============================( Enumerating Workgroup/Domain on 172.17.0.2 )=============================  
  
  
[+] Got domain/workgroup name: WORKGROUP  
  
  
 ====================================( Session Check on 172.17.0.2 )====================================  
  
  
[+] Server 172.17.0.2 allows sessions using username '', password ''  
  
  
 =================================( Getting domain SID for 172.17.0.2 )=================================  
  
Domain Name: WORKGROUP  
Domain Sid: (NULL SID)  
  
[+] Can't determine if host is part of domain or part of a workgroup                              
                                                                                                  
                                                                                                  
 ========================================( Users on 172.17.0.2 )========================================                                                                                          
                                                                                                  
index: 0x1 RID: 0x3f2 acb: 0x00000011 Account: games    Name: games     Desc: (null)              
index: 0x2 RID: 0x1f5 acb: 0x00000011 Account: nobody   Name: nobody    Desc: (null)  
index: 0x3 RID: 0x4ba acb: 0x00000011 Account: bind     Name: (null)    Desc: (null)  
index: 0x4 RID: 0x402 acb: 0x00000011 Account: proxy    Name: proxy     Desc: (null)  
index: 0x5 RID: 0x4b4 acb: 0x00000011 Account: syslog   Name: (null)    Desc: (null)  
index: 0x6 RID: 0xbba acb: 0x00000010 Account: user     Name: just a user,111,, Desc: (null)  
index: 0x7 RID: 0x42a acb: 0x00000011 Account: www-data Name: www-data  Desc: (null)  
index: 0x8 RID: 0x3e8 acb: 0x00000011 Account: root     Name: root      Desc: (null)  
index: 0x9 RID: 0x3fa acb: 0x00000011 Account: news     Name: news      Desc: (null)  
index: 0xa RID: 0x4c0 acb: 0x00000011 Account: postgres Name: PostgreSQL administrator,,,      Desc: (null)  
index: 0xb RID: 0x3ec acb: 0x00000011 Account: bin      Name: bin       Desc: (null)  
index: 0xc RID: 0x3f8 acb: 0x00000011 Account: mail     Name: mail      Desc: (null)  
index: 0xd RID: 0x4c6 acb: 0x00000011 Account: distccd  Name: (null)    Desc: (null)  
index: 0xe RID: 0x4ca acb: 0x00000011 Account: proftpd  Name: (null)    Desc: (null)  
index: 0xf RID: 0x4b2 acb: 0x00000011 Account: dhcp     Name: (null)    Desc: (null)  
index: 0x10 RID: 0x3ea acb: 0x00000011 Account: daemon  Name: daemon    Desc: (null)  
index: 0x11 RID: 0x4b8 acb: 0x00000011 Account: sshd    Name: (null)    Desc: (null)  
index: 0x12 RID: 0x3f4 acb: 0x00000011 Account: man     Name: man       Desc: (null)  
index: 0x13 RID: 0x3f6 acb: 0x00000011 Account: lp      Name: lp        Desc: (null)  
index: 0x14 RID: 0x4c2 acb: 0x00000011 Account: mysql   Name: MySQL Server,,,   Desc: (null)  
index: 0x15 RID: 0x43a acb: 0x00000011 Account: gnats   Name: Gnats Bug-Reporting System (admin)Desc: (null)  
index: 0x16 RID: 0x4b0 acb: 0x00000011 Account: libuuid Name: (null)    Desc: (null)  
index: 0x17 RID: 0x42c acb: 0x00000011 Account: backup  Name: backup    Desc: (null)  
index: 0x18 RID: 0xbb8 acb: 0x00000010 Account: msfadmin        Name: msfadmin,,,       Desc: (null)  
index: 0x19 RID: 0x4c8 acb: 0x00000011 Account: telnetd Name: (null)    Desc: (null)  
index: 0x1a RID: 0x3ee acb: 0x00000011 Account: sys     Name: sys       Desc: (null)  
index: 0x1b RID: 0x4b6 acb: 0x00000011 Account: klog    Name: (null)    Desc: (null)  
index: 0x1c RID: 0x4bc acb: 0x00000011 Account: postfix Name: (null)    Desc: (null)  
index: 0x1d RID: 0xbbc acb: 0x00000011 Account: service Name: ,,,       Desc: (null)  
index: 0x1e RID: 0x434 acb: 0x00000011 Account: list    Name: Mailing List Manager      Desc: (null)  
index: 0x1f RID: 0x436 acb: 0x00000011 Account: irc     Name: ircd      Desc: (null)  
index: 0x20 RID: 0x4be acb: 0x00000011 Account: ftp     Name: (null)    Desc: (null)  
index: 0x21 RID: 0x4c4 acb: 0x00000011 Account: tomcat55        Name: (null)    Desc: (null)  
index: 0x22 RID: 0x3f0 acb: 0x00000011 Account: sync    Name: sync      Desc: (null)  
index: 0x23 RID: 0x3fc acb: 0x00000011 Account: uucp    Name: uucp      Desc: (null)  
  
user:[games] rid:[0x3f2]  
user:[nobody] rid:[0x1f5]  
user:[bind] rid:[0x4ba]  
user:[proxy] rid:[0x402]  
user:[syslog] rid:[0x4b4]  
user:[user] rid:[0xbba]  
user:[www-data] rid:[0x42a]  
user:[root] rid:[0x3e8]  
user:[news] rid:[0x3fa]  
user:[postgres] rid:[0x4c0]  
user:[bin] rid:[0x3ec]  
user:[mail] rid:[0x3f8]  
user:[distccd] rid:[0x4c6]  
user:[proftpd] rid:[0x4ca]  
user:[dhcp] rid:[0x4b2]  
user:[daemon] rid:[0x3ea]  
user:[sshd] rid:[0x4b8]  
user:[man] rid:[0x3f4]  
user:[lp] rid:[0x3f6]  
user:[mysql] rid:[0x4c2]  
user:[gnats] rid:[0x43a]  
user:[libuuid] rid:[0x4b0]  
user:[backup] rid:[0x42c]  
user:[msfadmin] rid:[0xbb8]  
user:[telnetd] rid:[0x4c8]  
user:[sys] rid:[0x3ee]  
user:[klog] rid:[0x4b6]  
user:[postfix] rid:[0x4bc]  
user:[service] rid:[0xbbc]  
user:[list] rid:[0x434]  
user:[irc] rid:[0x436]  
user:[ftp] rid:[0x4be]  
user:[tomcat55] rid:[0x4c4]  
user:[sync] rid:[0x3f0]  
user:[uucp] rid:[0x3fc]  
enum4linux complete on Tue Oct  3 12:11:51 2023

Enum4linux aggregates output from multiple Samba tools to provide concise results. If needed, you can use the verbose option `**-v**` to see how each feature is used.

**2. List File Shares**: Enumerate file shares on 172.17.0.2 using `**enum4linux -S**`. Use the verbose option `**v**` to understand which Samba tools are used.

┌──(root㉿Kali)-[~]  
└─# enum4linux -Sv 172.17.0.2  
  
[V] Dependent program "nmblookup" found in /usr/bin/nmblookup  
  
  
[V] Dependent program "net" found in /usr/bin/net  
  
  
[V] Dependent program "rpcclient" found in /usr/bin/rpcclient  
  
  
[V] Dependent program "smbclient" found in /usr/bin/smbclient  
  
  
[V] Dependent program "polenum" found in /usr/bin/polenum  
  
  
[V] Dependent program "ldapsearch" found in /usr/bin/ldapsearch  
  
Starting enum4linux v0.9.1 ( http://labs.portcullis.co.uk/application/enum4linux/ ) on Tue Oct  3 12:12:48 2023  
  
 =========================================( Target Information )=========================================  
  
Target ........... 172.17.0.2  
RID Range ........ 500-550,1000-1050  
Username ......... ''  
Password ......... ''  
Known Usernames .. administrator, guest, krbtgt, domain admins, root, bin, none  
  
  
 =============================( Enumerating Workgroup/Domain on 172.17.0.2 )=============================                                                                                         
                                                                                                  
                                                                                                  
[V] Attempting to get domain name with command: nmblookup -A '172.17.0.2'                         
                                                                                                  
                                                                                                  
[+] Got domain/workgroup name: WORKGROUP                                                          
                                                                                                  
                                                                                                  
 ====================================( Session Check on 172.17.0.2 )====================================                                                                                          
                                                                                                  
                                                                                                  
[V] Attempting to make null session using command: smbclient -W 'WORKGROUP' //'172.17.0.2'/ipc$ -U''%'' -c 'help' 2>&1                                                                            
                                                                                                  
                                                                                                  
[+] Server 172.17.0.2 allows sessions using username '', password ''                              
                                                                                                  
                                                                                                  
 =================================( Getting domain SID for 172.17.0.2 )=================================                                                                                          
                                                                                                  
                                                                                                  
[V] Attempting to get domain SID with command: rpcclient -W 'WORKGROUP' -U''%'' 172.17.0.2 -c 'lsaquery' 2>&1                                                                                     
                                                                                                  
Domain Name: WORKGROUP                                                                            
Domain Sid: (NULL SID)  
  
[+] Can't determine if host is part of domain or part of a workgroup                              
                                                                                                  
                                                                                                  
 ==================================( Share Enumeration on 172.17.0.2 )==================================                                                                                          
                                                                                                  
                                                                                                  
[V] Attempting to get share list using authentication                                             
                                                                                                  
                                                                                                  
        Sharename       Type      Comment  
        ---------       ----      -------  
        print$          Disk      Printer Drivers  
        tmp             Disk      oh noes!  
        opt             Disk        
        IPC$            IPC       IPC Service (metasploitable server (Samba 3.0.20-Debian))  
        ADMIN$          IPC       IPC Service (metasploitable server (Samba 3.0.20-Debian))  
Reconnecting with SMB1 for workgroup listing.  
  
        Server               Comment  
        ---------            -------  
  
        Workgroup            Master  
        ---------            -------  
        WORKGROUP            METASPLOITABLE  
  
[+] Attempting to map shares on 172.17.0.2                                                        
                                                                                                  
                                                                                                  
[V] Attempting map to share //172.17.0.2/print$ with command: smbclient -W 'WORKGROUP' //'172.17.0.2'/'print$' -U''%'' -c dir 2>&1                                                                
                                                                                                  
//172.17.0.2/print$     Mapping: DENIED Listing: N/A Writing: N/A                                 
  
[V] Attempting map to share //172.17.0.2/tmp with command: smbclient -W 'WORKGROUP' //'172.17.0.2'/'tmp' -U''%'' -c dir 2>&1                                                                      
                                                                                                  
//172.17.0.2/tmp        Mapping: OK Listing: OK Writing: N/A                                      
  
[V] Attempting map to share //172.17.0.2/opt with command: smbclient -W 'WORKGROUP' //'172.17.0.2'/'opt' -U''%'' -c dir 2>&1                                                                      
                                                                                                  
//172.17.0.2/opt        Mapping: DENIED Listing: N/A Writing: N/A                                 
  
[V] Attempting map to share //172.17.0.2/IPC$ with command: smbclient -W 'WORKGROUP' //'172.17.0.2'/'IPC$' -U''%'' -c dir 2>&1                                                                    
                                                                                                  
                                                                                                  
[E] Can't understand response:                                                                    
                                                                                                  
NT_STATUS_NETWORK_ACCESS_DENIED listing \*                                                        
//172.17.0.2/IPC$       Mapping: N/A Listing: N/A Writing: N/A  
  
[V] Attempting map to share //172.17.0.2/ADMIN$ with command: smbclient -W 'WORKGROUP' //'172.17.0.2'/'ADMIN$' -U''%'' -c dir 2>&1                                                                
                                                                                                  
//172.17.0.2/ADMIN$     Mapping: DENIED Listing: N/A Writing: N/A                                 
enum4linux complete on Tue Oct  3 12:12:48 2023

> Which Samba tool was used to map the file shares?
> 
> **The Samba tool used to map file shares is** `**smbclient**`**.**
> 
> How many file shares are listed for target 172.17.0.2? What does the $ indicate at the end of the share name?
> 
> **There are five file shares listed for 172.17.0.2. The** `**$**` **at the end of the share name indicates hidden shares.**

**3. List Password Policies**: To understand the password policies on the target system, use the `**enum4linux -P**` command.

┌──(root㉿Kali)-[~]  
└─# enum4linux -P 172.17.0.2                                                                      
Starting enum4linux v0.9.1 ( http://labs.portcullis.co.uk/application/enum4linux/ ) on Tue Oct  3 12:13:44 2023  
  
 =========================================( Target Information )=========================================                                                                                         
                                                                                                  
Target ........... 172.17.0.2                                                                     
RID Range ........ 500-550,1000-1050  
Username ......... ''  
Password ......... ''  
Known Usernames .. administrator, guest, krbtgt, domain admins, root, bin, none  
  
  
 =============================( Enumerating Workgroup/Domain on 172.17.0.2 )=============================                                                                                         
                                                                                                  
                                                                                                  
[+] Got domain/workgroup name: WORKGROUP                                                          
                                                                                                  
                                                                                                  
 ====================================( Session Check on 172.17.0.2 )====================================                                                                                          
                                                                                                  
                                                                                                  
[+] Server 172.17.0.2 allows sessions using username '', password ''                              
                                                                                                  
                                                                                                  
 =================================( Getting domain SID for 172.17.0.2 )=================================                                                                                          
                                                                                                  
Domain Name: WORKGROUP                                                                            
Domain Sid: (NULL SID)  
  
[+] Can't determine if host is part of domain or part of a workgroup                              
                                                                                                  
                                                                                                  
 =============================( Password Policy Information for 172.17.0.2 )=============================                                                                                         
  
[+] Attaching to 172.17.0.2 using a NULL share  
  
[+] Trying protocol 139/SMB...  
  
[+] Found domain(s):  
  
        [+] METASPLOITABLE  
        [+] Builtin  
  
[+] Password Info for Domain: METASPLOITABLE  
  
        [+] Minimum password length: 5  
        [+] Password history length: None  
        [+] Maximum password age: Not Set  
        [+] Password Complexity Flags: 000000  
  
                [+] Domain Refuse Password Change: 0  
                [+] Domain Password Store Cleartext: 0  
                [+] Domain Password Lockout Admins: 0  
                [+] Domain Password No Clear Change: 0  
                [+] Domain Password No Anon Change: 0  
                [+] Domain Password Complex: 0  
  
        [+] Minimum password age: None  
        [+] Reset Account Lockout Counter: 30 minutes   
        [+] Locked Account Duration: 30 minutes   
        [+] Account Lockout Threshold: None  
        [+] Forced Log off Time: Not Set  
  
  
  
[+] Retieved partial password policy with rpcclient:                                              
                                                                                                  
                                                                                                  
Password Complexity: Disabled                                                                     
Minimum Password Length: 0  
  
enum4linux complete on Tue Oct  3 12:13:46 2023

> What is the minimum password length set for accounts on this server? What is the account lockout threshold setting?
> 
> **The minimum password length is five characters, and no account lockout threshold is set.**
> 
> How would you rate the security of the password policy set for this domain? Low, medium, or high? Explain.
> 
> **The security of the password policy is low. The minimum password length is too short, and the password complexity flag is 000000, indicating no password complexity policy is set. Additionally, there is no minimum password age configured.**

## Step 2: Perform Simple Enumeration Scan on Target 10.6.6.23

1. **Combine Enumeration Options**: Enum4linux has an option to combine multiple enumeration operations into one command using the `**a**` argument. This allows quick enumeration of SMB information.

┌──(root㉿Kali)-[~]  
└─# enum4linux -a 10.6.6.23  
Starting enum4linux v0.9.1 ( http://labs.portcullis.co.uk/application/enum4linux/ ) on Tue Oct  3 12:14:24 2023  
  
 =========================================( Target Information )=========================================  
  
Target ........... 10.6.6.23  
RID Range ........ 500-550,1000-1050  
Username ......... ''  
Password ......... ''  
Known Usernames .. administrator, guest, krbtgt, domain admins, root, bin, none  
  
  
 =============================( Enumerating Workgroup/Domain on 10.6.6.23 )=============================  
  
  
[E] Can't find workgroup/domain  
  
  
  
 =================================( Nbtstat Information for 10.6.6.23 )=================================  
  
Looking up status of 10.6.6.23  
No reply from 10.6.6.23  
  
 =====================================( Session Check on 10.6.6.23 )=====================================  
  
  
[+] Server 10.6.6.23 allows sessions using username '', password ''  
                                                                                                  
                                                                                                  
 ==================================( Getting domain SID for 10.6.6.23 )==================================                                                                                         
                                                                                                  
Domain Name: WORKGROUP                                                                            
Domain Sid: (NULL SID)  
  
[+] Can't determine if host is part of domain or part of a workgroup                              
                                                                                                  
                                                                                                  
 ====================================( OS information on 10.6.6.23 )====================================                                                                                          
                                                                                                  
                                                                                                  
[E] Can't get OS info with smbclient                                                              
                                                                                                  
                                                                                                  
[+] Got OS info for 10.6.6.23 from srvinfo:                                                       
        GRAVEMIND      Wk Sv PrQ Unx NT SNT Samba 4.9.5-Debian                                    
        platform_id     :       500  
        os version      :       6.1  
        server type     :       0x809a03  
  
  
 =========================================( Users on 10.6.6.23 )=========================================                                                                                         
                                                                                                  
index: 0x1 RID: 0x3e8 acb: 0x00000015 Account: masterchief      Name:   Desc:                     
index: 0x2 RID: 0x3e9 acb: 0x00000015 Account: arbiter  Name:   Desc:   
  
user:[masterchief] rid:[0x3e8]  
user:[arbiter] rid:[0x3e9]  
  
 ===================================( Share Enumeration on 10.6.6.23 )===================================                                                                                         
                                                                                                  
                                                                                                  
        Sharename       Type      Comment  
        ---------       ----      -------  
        homes           Disk      All home directories  
        workfiles       Disk      Confidential Workfiles  
        print$          Disk      Printer Drivers  
        IPC$            IPC       IPC Service (Samba 4.9.5-Debian)  
Reconnecting with SMB1 for workgroup listing.  
  
        Server               Comment  
        ---------            -------  
  
        Workgroup            Master  
        ---------            -------  
  
[+] Attempting to map shares on 10.6.6.23                                                         
                                                                                                  
                                                                                                  
[E] Can't understand response:                                                                    
                                                                                                  
tree connect failed: NT_STATUS_BAD_NETWORK_NAME                                                   
//10.6.6.23/homes       Mapping: N/A Listing: N/A Writing: N/A  
//10.6.6.23/workfiles   Mapping: OK Listing: OK Writing: N/A  
//10.6.6.23/print$      Mapping: OK Listing: OK Writing: N/A  
  
[E] Can't understand response:                                                                    
                                                                                                  
NT_STATUS_OBJECT_NAME_NOT_FOUND listing \*                                                        
//10.6.6.23/IPC$        Mapping: N/A Listing: N/A Writing: N/A  
  
 =============================( Password Policy Information for 10.6.6.23 )=============================                                                                                          
  
[+] Attaching to 10.6.6.23 using a NULL share  
  
[+] Trying protocol 139/SMB...  
  
[+] Found domain(s):  
  
        [+] GRAVEMIND  
        [+] Builtin  
  
[+] Password Info for Domain: GRAVEMIND  
  
        [+] Minimum password length: 5  
        [+] Password history length: None  
        [+] Maximum password age: 37 days 6 hours 21 minutes   
        [+] Password Complexity Flags: 000000  
  
                [+] Domain Refuse Password Change: 0  
                [+] Domain Password Store Cleartext: 0  
                [+] Domain Password Lockout Admins: 0  
                [+] Domain Password No Clear Change: 0  
                [+] Domain Password No Anon Change: 0  
                [+] Domain Password Complex: 0  
  
        [+] Minimum password age: None  
        [+] Reset Account Lockout Counter: 30 minutes   
        [+] Locked Account Duration: 30 minutes   
        [+] Account Lockout Threshold: None  
        [+] Forced Log off Time: 37 days 6 hours 21 minutes   
  
  
  
[+] Retieved partial password policy with rpcclient:                                              
                                                                                                  
                                                                                                  
Password Complexity: Disabled                                                                     
Minimum Password Length: 5  
  
  
 ========================================( Groups on 10.6.6.23 )========================================                                                                                          
                                                                                                  
                                                                                                  
[+] Getting builtin groups:                                                                       
                                                                                                  
                                                                                                  
[+]  Getting builtin group memberships:                                                           
                                                                                                  
                                                                                                  
[+]  Getting local groups:                                                                        
                                                                                                  
                                                                                                  
[+]  Getting local group memberships:                                                             
                                                                                                  
                                                                                                  
[+]  Getting domain groups:                                                                       
                                                                                                  
                                                                                                  
[+]  Getting domain group memberships:                                                            
                                                                                                  
                                                                                                  
 ====================( Users on 10.6.6.23 via RID cycling (RIDS: 500-550,1000-1050) )====================                                                                                         
                                                                                                  
                                                                                                  
[I] Found new SID:                                                                                
S-1-22-1                                                                                          
  
[I] Found new SID:                                                                                
S-1-5-32                                                                                          
  
[I] Found new SID:                                                                                
S-1-5-32                                                                                          
  
[I] Found new SID:                                                                                
S-1-5-32                                                                                          
  
[I] Found new SID:                                                                                
S-1-5-32                                                                                          
  
[+] Enumerating users using SID S-1-22-1 and logon username '', password ''                       
                                                                                                  
S-1-22-1-1000 Unix User\masterchief (Local User)                                                  
S-1-22-1-1001 Unix User\arbiter (Local User)  
S-1-22-1-1002 Unix User\labuser (Local User)  
  
[+] Enumerating users using SID S-1-5-32 and logon username '', password ''                       
                                                                                                  
S-1-5-32-544 BUILTIN\Administrators (Local Group)                                                 
S-1-5-32-545 BUILTIN\Users (Local Group)  
S-1-5-32-546 BUILTIN\Guests (Local Group)  
S-1-5-32-547 BUILTIN\Power Users (Local Group)  
S-1-5-32-548 BUILTIN\Account Operators (Local Group)  
S-1-5-32-549 BUILTIN\Server Operators (Local Group)  
S-1-5-32-550 BUILTIN\Print Operators (Local Group)  
  
[+] Enumerating users using SID S-1-5-21-3080196717-3701805971-2094628062 and logon username '', password ''                                                                                      
                                                                                                  
S-1-5-21-3080196717-3701805971-2094628062-501 GRAVEMIND\nobody (Local User)                       
S-1-5-21-3080196717-3701805971-2094628062-513 GRAVEMIND\None (Domain Group)  
S-1-5-21-3080196717-3701805971-2094628062-1000 GRAVEMIND\masterchief (Local User)  
S-1-5-21-3080196717-3701805971-2094628062-1001 GRAVEMIND\arbiter (Local User)  
  
 =================================( Getting printer info for 10.6.6.23 )=================================                                                                                         
                                                                                                  
No printers returned.                                                                             
  
  
enum4linux complete on Tue Oct  3 12:15:16 2023

> How many local users and groups are there on target 10.6.6.23?
> 
> **There are 3 local users and 7 groups on target 10.6.6.23.**
> 
> _What are the shares located on this target?_
> 
> **The shares on this target are “homes,” “workfiles,” and “print$.” Note that “IPC$” is for the server process itself and is created by default.**

# Part 4: Use smbclient to Transfer Files Between Systems

Smbclient is a valuable tool for transferring files between systems, similar to an FTP client. We will use smbclient to transfer a file to the target system at 172.17.0.2 as a simulated malware exploit.

1. **Create a Text File**: Use the `**cat**` command to create a text file named `**badfile.txt**` with desired content. For example:

cat >> badfile.txt  
This is a bad file.  
Press CTRL-C to write the file.

Press `**CTRL-C**` when done.

**2. Explore smbclient Options**: Check smbclient options using the `**smbclient --help**` command.

smbclient --help

**3. List Shares on Target**: List shares on the target host (172.17.0.2) using the `**smbclient -L**` command.

┌──(root㉿Kali)-[~]  
└─# smbclient -L //172.17.0.2/  
Password for [WORKGROUP\root]:  
Anonymous login successful  
  
        Sharename       Type      Comment  
        ---------       ----      -------  
        print$          Disk      Printer Drivers  
        tmp             Disk      oh noes!  
        opt             Disk        
        IPC$            IPC       IPC Service (metasploitable server (Samba 3.0.20-Debian))  
        ADMIN$          IPC       IPC Service (metasploitable server (Samba 3.0.20-Debian))  
Reconnecting with SMB1 for workgroup listing.  
Anonymous login successful  
  
        Server               Comment  
        ---------            -------  
  
        Workgroup            Master  
        ---------            -------  
        WORKGROUP            METASPLOITABLE

**4. Connect to a Share**: Connect to the `**tmp**` share on the target using `**smbclient**`.

┌──(root㉿Kali)-[~]  
└─# smbclient //172.17.0.2/tmp  
Password for [WORKGROUP\root]:  
Anonymous login successful  
Try "help" to get a list of possible commands.  
smb: \>

**5. Explore smbclient Commands**: Once connected, you can explore available commands by typing `**help**`.

**6. Upload a File**: Upload the `**badfile.txt**` to the target server using the `**put**` command.

put badfile.txt badfile.txt

This transfers the file to the target server.

**7. Verify Upload**: Use the `**dir**` command to verify that the file was successfully uploaded.

dir

**8. Exit smbclient**: Type `**quit**` to exit `**smbclient**` and return to the command prompt.

# Reflection

Imagine you are conducting a penetration test on a client’s network. You have gained access to an internal network by exploiting a vulnerability in an ad hoc web server outside the firewall. Now, you want to send a dummy malware file to hosts on the network as part of the penetration test.

Here are the steps you would follow:

1. **Identify Vulnerable Hosts**: Scan the internal network using tools like Nmap to identify hosts with open SMB ports (139 and 445) that make them potential targets.
2. **Enumerate Target Systems**: Use enum4linux to enumerate user accounts, groups, shares, and password policies on the identified hosts. This information helps assess the potential attack surface.
3. **Select a Target**: Choose a target host based on the vulnerabilities discovered during enumeration. Consider factors such as weak passwords or accessible shares.
4. **Craft the Malware**: Create a dummy malware file or payload that simulates an attack. Ensure it is harmless but indicative of a potential threat.
5. **Transfer the Malware**: Use smbclient to upload the malware file to the selected target’s accessible share. This mimics an attacker exploiting an SMB vulnerability to deliver malware.
6. **Monitor for Detection**: Continuously monitor the network for any security alerts or detection attempts. This helps assess the network’s security posture and incident response capabilities.
7. **Report Findings**: After completing the penetration test, compile a detailed report of findings, vulnerabilities, and recommendations for remediation. Provide evidence of successful exploitation without causing harm.

Remember that penetration testing should always be conducted within the bounds of legal and ethical guidelines, with proper authorization from the client. The objective is to help organizations identify and address security weaknesses to improve overall network security.

_This report documents the practical exercises conducted as part of the CISCO Ethical Hacker course, specifically focusing on using the enum4linux tool to address SMB vulnerabilities. All activities described were performed in a controlled, authorized environment, adhering to ethical hacking guidelines and legal regulations._

**Credit:** This information was adapted from an excellent guide on [Medium](https://infosecwriteups.com/scanning-for-smb-vulnerabilities-with-enum4linux-896f76d0c078). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/yQtNGf8O8Us?si=OY7dZG578yeytRYu" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=yQtNGf8O8Us). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/cGVNWU17nuM?si=C9IFkZk3-OSDivO-" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=cGVNWU17nuM). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/skHbTk-vtoM?si=ngAw1MJBiEefaNUs&amp;start=1605" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=skHbTk-vtoM). Be sure to check out the original post for more details.



