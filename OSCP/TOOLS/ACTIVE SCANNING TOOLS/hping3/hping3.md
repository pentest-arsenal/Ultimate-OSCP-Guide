hping3 README file
antirez@invece.org

DESCRIPTION

	hping3 is a network tool able to send custom TCP/IP
	packets and to display target replies like ping do with
	ICMP replies. hping3 can handle fragmentation, and
	almost arbitrary packet size and content, using the
	command line interface.

	Since version 3, hping implements scripting capabilties,
	read the API.txt file under the /docs directory to know
	more about it.

	As a command line utility, hping is useful to test at
	many kind of networking devices like firewalls, routers,
	and so. It can be used as a traceroute alike program over all
	the supported protocols, firewalk usage, OS fingerprinting,
	port-scanner (see the --scan option introduced with hping3),
	TCP/IP stack auditing.

	It's also really a good didactic tool to learn TCP/IP.

	Using Tcl/Tk scripting much more can be done, because
	while the hping3 packet generation code is actually the
	hping2 put there mainly for compatibility with the command
	line interface, all the real news are about scripting.

	See the libs directory for example scripts. To run
	the example scripts type:

		hping3 exec ScriptName.htcl <arguments, if required>

	hping3 is developed and manteined by antirez@invece.org
	with the help of other hackers, and comes under GPL version
	2 of license. Development is open so you can send me
	patches/suggestions/affronts without inhibitions.

	Please check the AUTHORS file for a list of people that
	contribued with code, ideas, bug reports.

	Also vim developer, ee.lbl.gov for tcpdump and GNU in general.

DOCUMENTATION

	For the hping3 API check docs/API.txt

	You can find documentation about hping3 specific functions
	at [http://wiki.hping.org](http://wiki.hping.org/)

	Make sure to check the page at [http://wiki.hping.org/34](http://wiki.hping.org/34)

DOWNLOAD

	The hping3 primary download site is the following:

		[http://www.hping.org](http://www.hping.org/)

	----------------------------------------------------------------
	How to get the hping3 source code from the anonymous CVS server
	----------------------------------------------------------------

	$ cvs -d :pserver:anonymous@cvs.hping2.sourceforge.net:/cvsroot/hping2 login   

	CVS will ask for the password, just press enter, no password is required

	than type the following to download the full source code.

	$ cvs -z8 -d :pserver:anonymous@cvs.hping2.sourceforge.net:/cvsroot/hping2 checkout hping3s

	-----------------------------------
	How to update your source code tree
	-----------------------------------

	change the current directory to /somewhere/hping2, than just type:

	$ cvs update

REQUIREMENTS

	A supported unix-like OS, gcc, root access.

	Libpcap.

	Tcl/Tk is optional but strongly suggested.

INSTALLATION

	see INSTALL file.

have fun,
antirez

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/antirez/hping). Be sure to check out the original post for more details.

# Tool Documentation:

## hping3 Usage Example

Use traceroute mode (`--traceroute`), be verbose (`-V`) in ICMP mode (`-1`) against the target (`www.example.com`):

```console
root@kali:~# hping3 --traceroute -V -1 www.example.com
using eth0, addr: 192.168.1.15, MTU: 1500
HPING www.example.com (eth0 93.184.216.119): icmp mode set, 28 headers + 0 data bytes
hop=1 TTL 0 during transit from ip=192.168.1.1 name=UNKNOWN
hop=1 hoprtt=0.3 ms
hop=2 TTL 0 during transit from ip=192.168.0.1 name=UNKNOWN
hop=2 hoprtt=3.3 ms
```

---

  

# Packages and Binaries:

### hping3

hping3 is a network tool able to send custom ICMP/UDP/TCP packets and to display target replies like ping does with ICMP replies. It handles fragmentation and arbitrary packet body and size, and can be used to transfer files under supported protocols. Using hping3, you can test firewall rules, perform (spoofed) port scanning, test network performance using different protocols, do path MTU discovery, perform traceroute-like actions under different protocols, fingerprint remote operating systems, audit TCP/IP stacks, etc. hping3 is scriptable using the Tcl language.

**Installed size:** `255 KB`  
**How to install:** `sudo apt install hping3`

Dependencies:

##### hping3

Send (almost) arbitrary TCP/IP packets to network hosts

```console
root@kali:~# hping3 -h
usage: hping3 host [options]
  -h  --help      show this help
  -v  --version   show version
  -c  --count     packet count
  -i  --interval  wait (uX for X microseconds, for example -i u1000)
      --fast      alias for -i u10000 (10 packets for second)
      --faster    alias for -i u1000 (100 packets for second)
      --flood	   sent packets as fast as possible. Don't show replies.
  -n  --numeric   numeric output
  -q  --quiet     quiet
  -I  --interface interface name (otherwise default routing interface)
  -V  --verbose   verbose mode
  -D  --debug     debugging info
  -z  --bind      bind ctrl+z to ttl           (default to dst port)
  -Z  --unbind    unbind ctrl+z
      --beep      beep for every matching packet received
Mode
  default mode     TCP
  -0  --rawip      RAW IP mode
  -1  --icmp       ICMP mode
  -2  --udp        UDP mode
  -8  --scan       SCAN mode.
                   Example: hping --scan 1-30,70-90 -S www.target.host
  -9  --listen     listen mode
IP
  -a  --spoof      spoof source address
  --rand-dest      random destionation address mode. see the man.
  --rand-source    random source address mode. see the man.
  -t  --ttl        ttl (default 64)
  -N  --id         id (default random)
  -W  --winid      use win* id byte ordering
  -r  --rel        relativize id field          (to estimate host traffic)
  -f  --frag       split packets in more frag.  (may pass weak acl)
  -x  --morefrag   set more fragments flag
  -y  --dontfrag   set don't fragment flag
  -g  --fragoff    set the fragment offset
  -m  --mtu        set virtual mtu, implies --frag if packet size > mtu
  -o  --tos        type of service (default 0x00), try --tos help
  -G  --rroute     includes RECORD_ROUTE option and display the route buffer
  --lsrr           loose source routing and record route
  --ssrr           strict source routing and record route
  -H  --ipproto    set the IP protocol field, only in RAW IP mode
ICMP
  -C  --icmptype   icmp type (default echo request)
  -K  --icmpcode   icmp code (default 0)
      --force-icmp send all icmp types (default send only supported types)
      --icmp-gw    set gateway address for ICMP redirect (default 0.0.0.0)
      --icmp-ts    Alias for --icmp --icmptype 13 (ICMP timestamp)
      --icmp-addr  Alias for --icmp --icmptype 17 (ICMP address subnet mask)
      --icmp-help  display help for others icmp options
UDP/TCP
  -s  --baseport   base source port             (default random)
  -p  --destport   [+][+]<port> destination port(default 0) ctrl+z inc/dec
  -k  --keep       keep still source port
  -w  --win        winsize (default 64)
  -O  --tcpoff     set fake tcp data offset     (instead of tcphdrlen / 4)
  -Q  --seqnum     shows only tcp sequence number
  -b  --badcksum   (try to) send packets with a bad IP checksum
                   many systems will fix the IP checksum sending the packet
                   so you'll get bad UDP/TCP checksum instead.
  -M  --setseq     set TCP sequence number
  -L  --setack     set TCP ack
  -F  --fin        set FIN flag
  -S  --syn        set SYN flag
  -R  --rst        set RST flag
  -P  --push       set PUSH flag
  -A  --ack        set ACK flag
  -U  --urg        set URG flag
  -X  --xmas       set X unused flag (0x40)
  -Y  --ymas       set Y unused flag (0x80)
  --tcpexitcode    use last tcp->th_flags as exit code
  --tcp-mss        enable the TCP MSS option with the given value
  --tcp-timestamp  enable the TCP timestamp option to guess the HZ/uptime
Common
  -d  --data       data size                    (default is 0)
  -E  --file       data from file
  -e  --sign       add 'signature'
  -j  --dump       dump packets in hex
  -J  --print      dump printable characters
  -B  --safe       enable 'safe' protocol
  -u  --end        tell you when --file reached EOF and prevent rewind
  -T  --traceroute traceroute mode              (implies --bind and --ttl 1)
  --tr-stop        Exit when receive the first not ICMP in traceroute mode
  --tr-keep-ttl    Keep the source TTL fixed, useful to monitor just one hop
  --tr-no-rtt	    Don't calculate/show RTT information in traceroute mode
ARS packet description (new, unstable)
  --apd-send       Send the packet described with APD (see docs/APD.txt)
```

---

Updated on: 2024-May-23

**Credit:** This information was adapted from an excellent guide on [Kali.org](https://www.kali.org/tools/hping3/#:~:text=hping3%20is%20a%20network%20tool,transfer%20files%20under%20supported%20protocols.). Be sure to check out the original post for more details.

# hping3 Command in Linux

Last Updated : 04 Nov, 2023

Hello there, fellow tech enthusiasts! Today, we’re going to delve into the world of network manipulation using the powerful hping3 command in Linux. Whether you’re a seasoned network administrator or just curious about how networking works, hping3 is a tool you’ll want to add to your toolkit. In this article, we’ll explore what hping3 is, its capabilities, and how to use it effectively.

## What is hping3?

hping3 is a command-line utility for crafting and sending custom TCP/IP packets. It is a versatile tool that allows you to perform various tasks, such as network scanning, fingerprinting, and testing network security. With hping3, you can simulate different types of network traffic, making it a valuable tool for network testing and troubleshooting.

## Installation Methods for Different Linux Distributions:

Before we start exploring hping3, let’s ensure you have it installed on your Linux system. Installation methods can vary depending on your distribution.

#### ****Debian/Ubuntu:****

On Debian-based systems like Ubuntu, you can use the following command to install hping3:

sudo apt-get install hping3

#### Red Hat/CentOS:

For Red Hat-based systems like CentOS, you can install hping3 using the following command:

sudo yum install hping3

#### Arch Linux:

If you’re using Arch Linux, you can install hping3 from the Arch User Repository (AUR) using an AUR helper like yay:

yay -S hping

Now that you have hping3 installed let’s delve into its usage in detail.

****Output:****

![imresizer-1696076902403](https://media.geeksforgeeks.org/wp-content/uploads/20230930180114/imresizer-1696076902403.jpg)

## Basic Usage: Sending Custom Packets

Alright, let’s get into the nitty-gritty of hping3 and learn how to send custom packets. Think of it like sending special messages over the internet to check if someone’s listening. Here’s how you do it:

Imagine you want to talk to Google’s web server but not just by visiting a website; you want to send it a message. Here’s how you’d do it:

sudo hping3 -c 3 -p 80 google.com

#### Let’s break this down:

- “sudo”: This is like putting on your super admin hat. It gives you the power to do special things with your computer.
- “hping3”: This is the magic word that tells your computer to send special messages.
- “-c 3”: This part says you want to send three messages. Why three? Well, it’s like saying “Hello” three times to make sure Google hears you.
- “-p 80”: Now, here’s the interesting part. This says you want to send your message to port 80. In internet terms, that’s like sending a message to a specific door where web stuff usually comes in.
- “google.com”: This is your destination. It’s like writing the recipient’s address on your letter.

When you hit enter, your computer will send three special messages (ICMP echo request packets) to Google’s web server, asking it to respond. If everything goes well, you’ll get responses, and hping3 will tell you how fast the messages went and if any got lost.

So, in plain English, hping3 helps you chat with other computers on the internet and see if they’re up and running. You can use this to check if websites are alive, test network connections.

#### Output:

![imresizer-1696076929926](https://media.geeksforgeeks.org/wp-content/uploads/20230930180113/imresizer-1696076929926.jpg)

### Advanced Techniques:

hping3 becomes even more powerful when you start exploring its advanced options. You can use it for tasks like:

- ****Firewall Testing:**** hping3 can be used to test the resilience of your firewall rules by sending packets with various TCP flags and options.
- ****Tracerouting:**** You can use hping3 to trace the path taken by packets to reach their destination.
- ****Traffic Generation:**** It can generate network traffic patterns to simulate different types of attacks or load on a network.
- ****Packet Crafting:**** Craft custom packets to test how your network devices and applications handle them.
- ****Fingerprinting:**** Identify the operating system or device type of a remote host by analyzing its response to crafted packets.

**Credit:** This information was adapted from an excellent guide on [GeeksForGeeks](https://www.geeksforgeeks.org/hping3-command-in-linux/). Be sure to check out the original post for more details.


**Denial of Service using Hping3**

![](https://hackblue.org/images/hping3.svg)

## DoS using Hping3

Hping3 is a versatile tool that allows users to send manipulated packets, including size, quantity, and fragmentation of packets, to overload a target and bypass or attack firewalls. It can be particularly useful for security or capability testing purposes. By using hping3, one can test the effectiveness of firewalls and evaluate if a server can handle a large number of connections. This guide will walk you through the installation process and demonstrate how to use hping3 for DoS attacks.

## Installation of Hping3

Hping3 can be installed on various Linux distributions. Here's how you can install it:

### Debian and Ubuntu Installation

1. Open a terminal.
2. Use the following command to install hping3:
    
    sudo apt install hping3 -y
    

### CentOS or RedHat Installation

1. Open a terminal.
2. Install hping3 using the following command:
    
    sudo yum -y install hping3
    

## Using Hping3 for DoS

Once hping3 is installed, you can use it to perform a DoS attack. Here's a step-by-step guide:

1. Open a terminal.
2. To launch a simple DoS attack, use the following command:
    
    sudo hping3 -S --flood -V -p 80 TARGET_IP
    
    - -S: specifies SYN packets.
    - --flood: sends packets as fast as possible, ignoring replies.
    - -V: provides verbose output.
    - -p 80: targets port 80, but this can be replaced with the desired port.
    - TARGET_IP: replace this with the IP address of your target.
3. To launch a SYN flood attack against a domain, use:
    
    sudo hping3 DOMAIN_NAME -q -n -d 120 -S -p 80 --flood --rand-source
    
4. If you wish to launch an attack from a fake IP address, use:
    
    sudo hping3 -a FAKE_IP TARGET_IP -S -q -p 80
    

## Conclusion

While hping3 is a powerful tool for understanding DoS attacks and stress testing, it's essential to use it responsibly and ethically. Unauthorized attacks can lead to severe legal consequences. Always ensure you have permission before testing any network or system. Remember, the primary purpose of tools like hping3 is to enhance security, not exploit it.

**Credit:** This information was adapted from an excellent guide on [HackBlue.org](https://hackblue.org/pages/dos_attacks_using_hping3.html). Be sure to check out the original post for more details.

# UDP and TCP Packet Crafting Techniques using `hping3`

[](https://github.com/Samsar4/Ethical-Hacking-Labs/blob/master/2-Scanning-Networks/1-hping3.md#udp-and-tcp-packet-crafting-techniques-using-hping3)

Hping3 is a scriptable program that uses the [Tcl language](https://www.tcl.tk/about/language.html), whereby packets can be received and sent via a binary or string representation describing the packets.

During network scanning, your first task will be to scan the target network to determine all possible open ports, live hosts, and running services. Knowledge of packet-crafting techniques may help you to scan the network beyond the firewall or IDS.

### Objectives:

[](https://github.com/Samsar4/Ethical-Hacking-Labs/blob/master/2-Scanning-Networks/1-hping3.md#objectives)

- How to perform network scanning and packet crafting using hping3 commands.

### Requirements:

[](https://github.com/Samsar4/Ethical-Hacking-Labs/blob/master/2-Scanning-Networks/1-hping3.md#requirements)

- Kali Linux (Attacker machine)
- Windows 10 (Target machine)

## Overview of Packet Crafting

[](https://github.com/Samsar4/Ethical-Hacking-Labs/blob/master/2-Scanning-Networks/1-hping3.md#overview-of-packet-crafting)

Packet crafting is a technique that allows you to find vulnerabilities or entry points into a target network. This can ben performed by creating custom network packets to test network devices and behavior.

---

**Note:** Before beginning this lab, install the Wireshark in Windows 10 machine.

## hping3 basics

[](https://github.com/Samsar4/Ethical-Hacking-Labs/blob/master/2-Scanning-Networks/1-hping3.md#hping3-basics)

Login to Kali Linux and launch the Terminal.  
Use `hping3 -h` to show all the commands. We will foccus on a couple of them so don't worry.

Let's start!

`hping3 -c 3 <Target IP address>`

```
...
3 packets transmitted, 3 packets received, 0% packet loss
...
```

Note on the bottom of the output, the 3 packets were sent and received. You should get this response.

`-c` stands for packet count. Means that we only want to send three packets to the target machine.

Next we will send a SYN flag scan with a port range.

`hping3 --scan 1-3000 -S <Target IP address>`

```
Scanning 10.0.2.15 (10.0.2.15), port 1-3000
3000 ports to scan, use -V to see all the replies
+----+-----------+---------+---+-----+-----+-----+
|port| serv name |  flags  |ttl| id  | win | len |
+----+-----------+---------+---+-----+-----+-----+
  135 epmap      : .S..A... 128 62018 65392    46
  139 netbios-ssn: .S..A... 128 63042  8192    46
  445 microsoft-d: .S..A... 128 52291 65392    46
All replies received. Done.
Not responding ports: 
```

`--scan` parameter defines the port range to scan.  
`-S` represents **SYN flag**.

The output shows the open ports in the target machine, i.e. Windows 10.

## UDP packet crafting

[](https://github.com/Samsar4/Ethical-Hacking-Labs/blob/master/2-Scanning-Networks/1-hping3.md#udp-packet-crafting)

To perform a UDP packet crafting in the target machine, type:

`hping3 <Target IP address> --udp --rand-source --data 500`

Next go to Windows 10 machine and fire up the Wireshark to start capturing packets.

Observe the UDP and ICMP packets. Click the **UDP** packet and look inside, the **Data (500 bytes)**.

`--udp` UDP mode.  
`--rand-source` This option enables the random source mode. hping will send packets with random source address.  
`--data` data size in bytes.  

## Send TCP SYN Request

[](https://github.com/Samsar4/Ethical-Hacking-Labs/blob/master/2-Scanning-Networks/1-hping3.md#send-tcp-syn-request)

Launch the Wireshark on Windows machine again and leave it running.

To send a TCP SYN request to the target machine, type:

`hping3 -S <Target IP address> -p 80 -c 5`

**This will transmit 5 packets request to victim machine through port 80.**

`-S` will perform TCP SYN request on the target, `p` will pass the traffic through which port is assigned, and `-c` is the count of the packets sent to the target machine.

Switch to the target machine (Windows), and observe the TCP packets caputerd in Wireshark.

Next, stop the packet capture, and start a new capture again. Leave the Wireshark running.

## Perform TCP Flooding

[](https://github.com/Samsar4/Ethical-Hacking-Labs/blob/master/2-Scanning-Networks/1-hping3.md#perform-tcp-flooding)

`hping3 <Target IP address> --flood`

The `--flood` send packets as fast as possible, without taking care to show incoming replies.

After a couple seconds stop the packet capture in Wireshark on Windows. You will notice the TCP flooding from the attacker machine.

Note: If you want to inspect the TCP packet stream and do some reverse engineering make sure to understand more than the infamous "Three-Way Handshake".

---

Some interesting links:

[TCP Sequence and Acknowledgment Numbers](https://packetlife.net/blog/2010/jun/7/understanding-tcp-sequence-acknowledgment-numbers/)

[Reverse Engineering A Mysterious UDP Stream in My Hotel](https://www.gkbrk.com/2016/05/hotel-music/)

[TCP/IP Guide](http://www.tcpipguide.com/free/index.htm)

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/Samsar4/Ethical-Hacking-Labs/blob/master/2-Scanning-Networks/1-hping3.md). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/kuE8qLwg4f8?si=PR1lxVqMZZ4FPseE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=kuE8qLwg4f8). Be sure to check out the original post for more details.

