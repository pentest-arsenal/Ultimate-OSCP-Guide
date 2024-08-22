# Tool Documentation:

## Unicornscan Usage Example

```console
root@kali:~# unicornscan -mTsf -Iv -r 1000 192.168.0.102:a
adding 192.168.0.102/32 mode `TCPscan' ports `a' pps 1000
using interface(s) eth0
scaning 1.00e+00 total hosts with 6.55e+04 total packets, should take a little longer than 1 Minutes, 12 Seconds
connected 192.168.103.227:23221 -> 192.168.0.102:445
TCP open 192.168.0.102:445  ttl 128
connected 192.168.103.227:50006 -> 192.168.0.102:443
TCP open 192.168.0.102:443  ttl 128
connected 192.168.103.227:54487 -> 192.168.0.102:161
TCP open 192.168.0.102:161  ttl 128
connected 192.168.103.227:47765 -> 192.168.0.102:80
TCP open 192.168.0.102:80  ttl 128
connected 192.168.103.227:4267 -> 192.168.0.102:1884
TCP open 192.168.0.102:139  ttl 128
sender statistics 963.9 pps with 65536 packets sent total
listener statistics 131180 packets recieved 0 packets droped and 0 interface drops
TCP open                http[   80]     from 192.168.0.102  ttl 128
TCP open         netbios-ssn[  139]     from 192.168.0.102  ttl 128
TCP open                snmp[  161]     from 192.168.0.102  ttl 128
TCP open               https[  443]     from 192.168.0.102  ttl 128
TCP open        microsoft-ds[  445]     from 192.168.0.102  ttl 128
root@kali:~#
```

---

  

# Packages and Binaries:

### unicornscan

Unicornscan is a new information gathering and correlation engine built for and by members of the security research and testing communities. It was designed to provide an engine that is Scalable, Accurate, Flexible, and Efficient. It is released for the community to use under the terms of the GPL license. Benefits:

Unicornscan is an attempt at a User-land Distributed TCP/IP stack. It is intended to provide a researcher a superior interface for introducing a stimulus into and measuring a response from a TCP/IP enabled device or network. Although it currently has hundreds of individual features, a main set of abilities include:

```console
- Asynchronous stateless TCP scanning with all variations of TCP Flags.
- Asynchronous stateless TCP banner grabbing
- Asynchronous protocol specific UDP Scanning (sending enough of a signature
to elicit a response).
- Active and Passive remote OS, application, and component identification
by analyzing responses.
- PCAP file logging and filtering
- Relational database output
- Custom module support
- Customized data-set views
```

**Installed size:** `3.61 MB`  
**How to install:** `sudo apt install unicornscan`

Dependencies:

- flex
- libc6
- libpcap0.8t64

##### fantaip

```console
root@kali:~# fantaip -h
FantaIP by Kiki
Usage: fantaip (options) IP
	-d		Detach from terminal and daemonize
	-H		Hardware address like XX:XX:XX:XX:XX:XX (otherwise use nics hwaddr)
	-h		help
	-i		*interface
	-v		verbose operation
*: Argument required
Example: fantaip -i eth0 192.168.1.7
```

---

##### unibrow

```console
root@kali:~# unibrow --help
unibrow: invalid option -- '-'
Usage: unibrow:
	-i	*for pcap file to read
	-o	 for output file (append mode)
	-v	 verbose operation
	-h	 display help that you are reading
[*] required argument
pcap filter expression follows options, like unibrow -o new.conf -i file.pcap port 500 and udp
```

---

##### unicfgtst

---

##### unicornscan

(unknown subject)

```console
root@kali:~# unicornscan -h
unicornscan (version 0.4.7)
usage: unicornscan [options `b:B:cd:De:EFG:hHi:Ij:l:L:m:M:o:p:P:q:Qr:R:s:St:T:u:Uw:W:vVzZ:' ] X.X.X.X/YY:S-E
	-b, --broken-crc     *set broken crc sums on [T]ransport layer, [N]etwork layer, or both[TN]
	-B, --source-port    *set source port? or whatever the scan module expects as a number
	-c, --proc-duplicates process duplicate replies
	-d, --delay-type     *set delay type (numeric value, valid options are `1:tsc 2:gtod 3:sleep')
	-D, --no-defpayload   no default Payload, only probe known protocols
	-e, --enable-module  *enable modules listed as arguments (output and report currently)
	-E, --proc-errors     for processing `non-open' responses (icmp errors, tcp rsts...)
	-F, --try-frags       
	-G, --payload-group	*payload group (numeric) for tcp/udp type payload selection (default all)
	-h, --help            help
	-H, --do-dns          resolve hostnames during the reporting phase
	-i, --interface      *interface name, like eth0 or fxp1, not normally required
	-I, --immediate       immediate mode, display things as we find them
	-j, --ignore-seq     *ignore `A'll, 'R'eset sequence numbers for tcp header validation
	-l, --logfile        *write to this file not my terminal
	-L, --packet-timeout *wait this long for packets to come back (default 7 secs)
	-m, --mode           *scan mode, tcp (syn) scan is default, U for udp T for tcp `sf' for tcp connect scan and A for arp
	                       for -mT you can also specify tcp flags following the T like -mTsFpU for example
	                       that would send tcp syn packets with (NO Syn|FIN|NO Push|URG)
	-M, --module-dir     *directory modules are found at (defaults to /usr/lib/unicornscan/modules)
	-o, --format         *format of what to display for replies, see man page for format specification
	-p, --ports           global ports to scan, if not specified in target options
	-P, --pcap-filter    *extra pcap filter string for reciever
	-q, --covertness     *covertness value from 0 to 255
	-Q, --quiet           dont use output to screen, its going somewhere else (a database say...)
	-r, --pps            *packets per second (total, not per host, and as you go higher it gets less accurate)
	-R, --repeats        *repeat packet scan N times
	-s, --source-addr    *source address for packets `r' for random
	-S, --no-shuffle      do not shuffle ports
	-t, --ip-ttl         *set TTL on sent packets as in 62 or 6-16 or r64-128
	-T, --ip-tos         *set TOS on sent packets
	-u, --debug		*debug mask
	-U, --no-openclosed	 dont say open or closed
	-w, --safefile       *write pcap file of recieved packets
	-W, --fingerprint    *OS fingerprint 0=cisco(def) 1=openbsd 2=WindowsXP 3=p0fsendsyn 4=FreeBSD 5=nmap
	                      6=linux 7:strangetcp
	-v, --verbose         verbose (each time more verbose so -vvvvv is really verbose)
	-V, --version         display version
	-z, --sniff           sniff alike
	-Z, --drone-str      *drone String
*:	options with `*' require an argument following them

  address ranges are cidr like 1.2.3.4/8 for all of 1.?.?.?
  if you omit the cidr mask then /32 is implied
  port ranges are like 1-4096 with 53 only scanning one port, a for all 65k and p for 1-1024
example: unicornscan -i eth1 -Ir 160 -E 192.168.1.0/24:1-4000 gateway:a
```

---

##### us

```console
root@kali:~# us -h
unicornscan (version 0.4.7)
usage: unicornscan [options `b:B:cd:De:EFG:hHi:Ij:l:L:m:M:o:p:P:q:Qr:R:s:St:T:u:Uw:W:vVzZ:' ] X.X.X.X/YY:S-E
	-b, --broken-crc     *set broken crc sums on [T]ransport layer, [N]etwork layer, or both[TN]
	-B, --source-port    *set source port? or whatever the scan module expects as a number
	-c, --proc-duplicates process duplicate replies
	-d, --delay-type     *set delay type (numeric value, valid options are `1:tsc 2:gtod 3:sleep')
	-D, --no-defpayload   no default Payload, only probe known protocols
	-e, --enable-module  *enable modules listed as arguments (output and report currently)
	-E, --proc-errors     for processing `non-open' responses (icmp errors, tcp rsts...)
	-F, --try-frags       
	-G, --payload-group	*payload group (numeric) for tcp/udp type payload selection (default all)
	-h, --help            help
	-H, --do-dns          resolve hostnames during the reporting phase
	-i, --interface      *interface name, like eth0 or fxp1, not normally required
	-I, --immediate       immediate mode, display things as we find them
	-j, --ignore-seq     *ignore `A'll, 'R'eset sequence numbers for tcp header validation
	-l, --logfile        *write to this file not my terminal
	-L, --packet-timeout *wait this long for packets to come back (default 7 secs)
	-m, --mode           *scan mode, tcp (syn) scan is default, U for udp T for tcp `sf' for tcp connect scan and A for arp
	                       for -mT you can also specify tcp flags following the T like -mTsFpU for example
	                       that would send tcp syn packets with (NO Syn|FIN|NO Push|URG)
	-M, --module-dir     *directory modules are found at (defaults to /usr/lib/unicornscan/modules)
	-o, --format         *format of what to display for replies, see man page for format specification
	-p, --ports           global ports to scan, if not specified in target options
	-P, --pcap-filter    *extra pcap filter string for reciever
	-q, --covertness     *covertness value from 0 to 255
	-Q, --quiet           dont use output to screen, its going somewhere else (a database say...)
	-r, --pps            *packets per second (total, not per host, and as you go higher it gets less accurate)
	-R, --repeats        *repeat packet scan N times
	-s, --source-addr    *source address for packets `r' for random
	-S, --no-shuffle      do not shuffle ports
	-t, --ip-ttl         *set TTL on sent packets as in 62 or 6-16 or r64-128
	-T, --ip-tos         *set TOS on sent packets
	-u, --debug		*debug mask
	-U, --no-openclosed	 dont say open or closed
	-w, --safefile       *write pcap file of recieved packets
	-W, --fingerprint    *OS fingerprint 0=cisco(def) 1=openbsd 2=WindowsXP 3=p0fsendsyn 4=FreeBSD 5=nmap
	                      6=linux 7:strangetcp
	-v, --verbose         verbose (each time more verbose so -vvvvv is really verbose)
	-V, --version         display version
	-z, --sniff           sniff alike
	-Z, --drone-str      *drone String
*:	options with `*' require an argument following them

  address ranges are cidr like 1.2.3.4/8 for all of 1.?.?.?
  if you omit the cidr mask then /32 is implied
  port ranges are like 1-4096 with 53 only scanning one port, a for all 65k and p for 1-1024
example: unicornscan -i eth1 -Ir 160 -E 192.168.1.0/24:1-4000 gateway:a
```

---

Updated on: 2024-May-23

**Credit:** This information was adapted from an excellent guide on [Kali.org](https://www.kali.org/tools/unicornscan/). Be sure to check out the original post for more details.

# Reconnaissance with Unicornscan

Updated: Dec 31, 2022

  

**Port Scanning with Unicornscan**

In this section of Hackers-Arise, we have looked at a variety of tools for port scanning and OS fingerprinting from [](http://www.hackers-arise.com/nmap-for-recon-and-dos)[nmap](http://www.hackers-arise.com/nmap-for-recon-and-dos), [hping](http://www.hackers-arise.com/hping-for-reconnaissance) and [p0f](http://www.hackers-arise.com/post/2016/06/10/Operating-System-OS-Fingerprinting-with-p0F). In this lesson on port scanning and reconnaissance, I want to introduce you to one more tool, **unicornscan**. While [nmap](http://www.hackers-arise.com/nmap-for-recon-and-dos) is the most widely used port scanner for pentesters and hackers, it does have some shortcomings. First, it doesn't do OS fingerprinting very well. Second, it can be relatively slow; and lastly, it uses the TCP/IP stack of the underlying operating system for sending packets making easy for the target to determine the attacker's OS.

![](https://static.wixstatic.com/media/6a4a49_158980c690314ce392e9e3ca3db14804~mv2_d_3840_2400_s_4_2.jpg/v1/fill/w_350,h_219,al_c,q_80,usm_0.66_1.00_0.01,enc_auto/6a4a49_158980c690314ce392e9e3ca3db14804~mv2_d_3840_2400_s_4_2.jpg)

Before I go any further I want to add that there is no perfect tool. Each of these tools has its strengths and weaknesses. That's why it's wise to become familiar with more than one tool to do the job so that when a situation arises, you can select the proper tool for the job.

**I. Unicornscan Introduction**

Unicornscan is a sophisticated, powerful and stateless port scanner that uses stimulus into and measuring a response from any TCP/IP enabled device (there are billions out there). Although it has hundreds of features, some of its key features include;

- Asynchronous stateless TCP scanning with each of the TCP flags or flag combinations
    
- Asynchronous banner grabbing for application and OS fingerprinting
    
- Asynchronous protocol specific UDP scanning
    
- Active and Passive remote OS and application detection
    
- PCAP file logging and filtering
    
- Relational database output for storing the results of your scans
    
- Custom module support so that pentesters can tailor it to their specific needs
    
- Customized data set views.
    

One of the key features of unicornscan that sets it apart of nmap and other port scanners is that it has its own TCP/IP stack. The other port scanners all use the underlying host operating system's TCP/IP stack. This enables unicornscan to scan much more quickly than the others as it can, for instance, send out SYN packets with one thread and receive the responses with another thread. This can make a huge difference when scanning very large networks as a security researcher/ pentester where we might be scanning thousands of IP addresses and be even more important to an attacker who may be scanning millions of addresses looking for a particular open port or vulnerability. In addition, because it has its own TCP/IP stack, it is capable of sending packets with different OS fingerprints that the operating system of your host. This can be very useful for obscuring your identity, especially combined with IP spoofing.

Unicornscan is built into Kali, so no need to download, unpack and compile new software. Since it is installed in the /usr/bin directory, we can access unicornscan from the command line from any directory.

Let's get started with unicornscan.

**II. Unicornscan Help**

Let's begin by looking at the help file for unicornscan by typing;

**kali > unicornscan -h**

![](https://static.wixstatic.com/media/6a4a49_17d3c56d01fe4109972045b7612a12a9~mv2.png/v1/fill/w_736,h_675,al_c,q_90,enc_auto/6a4a49_17d3c56d01fe4109972045b7612a12a9~mv2.png)

Since the help screen is so long, I captured it in two screenshots and displayed the second one below.

![](https://static.wixstatic.com/media/6a4a49_327cb2c04b9f4712b6926155648327aa~mv2.png/v1/fill/w_740,h_632,al_c,q_90,enc_auto/6a4a49_327cb2c04b9f4712b6926155648327aa~mv2.png)

There is a LOT of information is this help file, so let's start with some simple scans to demonstrate the power of unicornscan and work up to some more complex examples.

The syntax for a basic unicornscan (default is a TCP SYN) scan is;

**kali > unicornscan <host>**

Let's try it against a Windows 7 machine on our network.

**kali > unicornscan 192.168.1.116**

![](https://static.wixstatic.com/media/6a4a49_d1d656bf52694d1fbbcc0f018a95d041~mv2.png/v1/fill/w_740,h_111,al_c,lg_1,q_85,enc_auto/6a4a49_d1d656bf52694d1fbbcc0f018a95d041~mv2.png)

This simple syntax will return for us the open TCP ports on the target system, very similar to the nmap -sS scan, but without the default ICMP that nmap uses. As you can see, unicornscan reports back to us that ports 135,139,445 and 554 are open on the target Windows 7 system.

What if we want to scan more than one IP address? Unicornscan has slightly different syntax for scanning multiple hosts than nmap or hping. Each of the hosts must be listed individually without a comma between them, as below.

**kali > unicornscan 192.168.1.106 192.168.1.116**

![](https://static.wixstatic.com/media/6a4a49_e766a6afe90e4596a0c8cb2d7d2f9cba~mv2.png/v1/fill/w_740,h_112,al_c,lg_1,q_85,enc_auto/6a4a49_e766a6afe90e4596a0c8cb2d7d2f9cba~mv2.png)

If we wanted to scan our entire network, we can use CIDR notation such as 192.168.1.0/24 to scan all 255 IP addresses. Let's say we wanted to find all the IP that had port 80 open. We simply need to use the :80 notation after the CIDR notation such as;

**kali > unicornscan 192.168.1.0/24:80**

![](https://static.wixstatic.com/media/6a4a49_1ef29c70ddb845389aa0776e4e3f0db1~mv2.png/v1/fill/w_740,h_92,al_c,lg_1,q_85,enc_auto/6a4a49_1ef29c70ddb845389aa0776e4e3f0db1~mv2.png)

Here we can see unicornscan scanned the entire Class C network finding all the hosts with port 80 open.

Unicornscan is not limited to our internal network and this is where its speed becomes critical. What if I knew that a particular vulnerability existed on systems that had port 5505 open. I have no idea where these systems were. They could be anywhere in the world, meaning that I would have to scan over 4 billion addresses! I could break the scans down to smaller pieces, say a million at a time. I could use unicornscan to scan one million addresses looking for port 5505 by typing;

**kali > unicornscan 216.1.0.0/8:5505**

**III. TCP Scanning**

Unicornscan defaults to a TCP scan without sending any ICMP, unlike nmap. By default, it sends a SYN scan. Let's say we wanted to scan our favorite IT security training site, hackers-arise.com, looking for ports 80 and 443 and sending 200 packets per second we could write;

**kali > unicornscan -r200 -mT hackers-arise.com:80,443**

Where;

**-r200**

indicates we want to send 200 packets per second

**-mT**

indicates we want to scan (m) using the TCP protocol

**hackers-arise.com:80,443**

indicates the host and the ports we want to scan

![](https://static.wixstatic.com/media/6a4a49_2e462ac70b594fed802976aa5833fb5b~mv2.png/v1/fill/w_740,h_64,al_c,q_85,usm_0.66_1.00_0.01,enc_auto/6a4a49_2e462ac70b594fed802976aa5833fb5b~mv2.png)

As you can see, unicornscan only found port 80 open at hackers-arise.com

**IV. UDP Scanning**

What if we are looking for UDP ports? Since unicornscan, by default, sends TCP SYN packets, it will not find UDP ports unless we specify a UDP scan, similar to nmap. We can scan for UDP ports by simply replacing the T with a U after the -m, such as;

**kali >unicornscan -r300 -mU hackers-arise.com**

Where:

**-r300** indicates we want to scan with 300 packets per second

**-mU** indicates we want to scan with the UDP protocol.

![](https://static.wixstatic.com/media/6a4a49_d3b090f171e8425096f54af30eb99ca8~mv2.png/v1/fill/w_740,h_49,al_c,q_85,usm_0.66_1.00_0.01,enc_auto/6a4a49_d3b090f171e8425096f54af30eb99ca8~mv2.png)

When we scan hackers-arise.com with a UDP scan, it finds no UDP ports open. This is not unexpected for a web server, but on a typical network you are likely to see many UDP ports open such 53, 161 and others.

**V. Saving to a PCAP file**

One of the other beauties of the unicornscan is its ability to save the returned packets to a PCAP file format. This enables us then to analyze the response packets at a later time with tools such as Wireshark. So, if we wanted to find hosts with port 5505 open and make it appear to be coming from an openBSD system with the IP address of 69.162.180.50 we could write a command like this;

**kali > unicornscan 216.1.0.0/8:5505 -r500 -w huntfor5505.pcap -W1 -s 69.162.80.50**

Where:

**-r500**

indicates we want to scan with 500 packets per second

**-w huntfor5505.pcap**

indicates we want to write to a file named huntfor5505.pcap

**-W1**

indicates we want to packets to sent with the fingerprint of an openBSD system

**-s**

indicates we want the packets to be sent with a spoofed IP that follows (69.162.80.50)

**VI. Unicornscan Cheat Sheet**

Unicornscan is a powerful scanner with hundreds of features, a few of which we have touched upon here. Probably its greatest advantage over other port scanners are the fact that it has its own TCP/IP stack enabling it to scan faster and spoof other TCP/IP stacks.

For the most common scanning, please find a cheat sheet below to assist you.

**SYN : -mT**

**ACK scan : -mTsA**

**Fin scan : -mTsF**

**Null scan : -mTs**

**Xmas scan : -mTsFPU**

**Connect Scan : -msf -Iv**

**Full Xmas scan : -mTFSRPAU**

**scan ports 1 through 5 : (-mT) host:1-5**

To spoof your IP use **-s** followed by the IP address.

To use another OS fingerprint use the -W switch followed by the numeric value of the OS.

**0=Cisco (default) 1=openbsd 2= Windows XP 3= p0fsendsyn 4=FreeBSD 5= nmap**

**Credit:** This information was adapted from an excellent guide on [Hackers-Arise](https://www.hackers-arise.com/post/2017/08/20/reconnaissance-with-unicornscan). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/X_DdYUeKS-o?si=wqx8i29N5CZ1aT_N" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=X_DdYUeKS-o&t=1017s). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/H_UrgkGNJFg?si=OS81tDPLmXRX6Sn1" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=H_UrgkGNJFg). Be sure to check out the original post for more details.


