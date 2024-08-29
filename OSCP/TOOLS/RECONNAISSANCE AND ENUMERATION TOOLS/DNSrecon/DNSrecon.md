
Let me preface this by acknowledging that these two programs are not the same software, although they are listed together in this folder. They serve similar purposes in the context of enumeration.
# DNSRecon

[](https://github.com/darkoperator/dnsrecon#dnsrecon)

DNSRecon is a Python port of a Ruby script that I wrote to learn the language and about DNS in early 2007. This time I wanted to learn about Python and extend the functionality of the original tool and in the process re-learn how DNS works and how could it be used in the process of a security assessment and network troubleshooting.

This script provides the ability to perform:

- Check all NS Records for Zone Transfers.
- Enumerate General DNS Records for a given Domain (MX, SOA, NS, A, AAAA, SPF and TXT).
- Perform common SRV Record Enumeration.
- Top Level Domain (TLD) Expansion.
- Check for Wildcard Resolution.
- Brute Force subdomain and host A and AAAA records given a domain and a wordlist.
- Perform a PTR Record lookup for a given IP Range or CIDR.
- Check a DNS Server Cached records for A, AAAA and CNAME Records provided a list of host records in a text file to check.

# Python Version

[](https://github.com/darkoperator/dnsrecon#python-version)

DNSRecon requires python3.6+

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/darkoperator/dnsrecon). Be sure to check out the original post for more details.

[![git](https://user-images.githubusercontent.com/55983491/207074950-9dae61cc-6e0c-444c-8029-7f0b5c5f8e87.gif)](https://user-images.githubusercontent.com/55983491/207074950-9dae61cc-6e0c-444c-8029-7f0b5c5f8e87.gif)

My website: [https://microjoan.com](https://microjoan.com/)  
My blog: [https://darkhacking.es/](https://darkhacking.es/)  
Buy me a coffee: [https://www.buymeacoffee.com/microjoan](https://www.buymeacoffee.com/microjoan)

# DISCLAIMER

[](https://github.com/micro-joan/DNSrecon-gui#disclaimer)

This toolkit contains materials that can be potentially damaging or dangerous for social media. Refer to the laws in your province/country before accessing, using,or in any other way utilizing this in a wrong way.

This Tool is made for educational purposes only. Do not attempt to violate the law with anything contained here. If this is your intention, then Get the hell out of here!

---

# DNSrecon GUI for Kali Linux

[](https://github.com/micro-joan/DNSrecon-gui#dnsrecon-gui-for-kali-linux)

[![logo](https://user-images.githubusercontent.com/55983491/206944421-022377ca-ba40-499e-a7db-a88269b753be.png)](https://user-images.githubusercontent.com/55983491/206944421-022377ca-ba40-499e-a7db-a88269b753be.png)

DNSRecon is a DNS scanning and enumeration tool written in Python, which allows you to perform different tasks, such as enumeration of standard records for a defined domain (A, NS, SOA, and MX). Top-level domain expansion for a defined domain.

With this graph-oriented user interface, the different records of a specific domain can be observed, classified and ordered in a simple way.

# Install

[](https://github.com/micro-joan/DNSrecon-gui#install)

```
git clone https://github.com/micro-joan/dnsrecon-gui
cd dnsrecon-gui/
chmod +x run.sh
./run.sh
```

After executing the application launcher you need to have all the components installed, the launcher will check one by one, and in the case of not having any component installed it will show you the statement that you must enter to install it:

[![install](https://user-images.githubusercontent.com/55983491/206945068-4421b9ca-a66f-49b7-b4f5-8a53579f8177.gif)](https://user-images.githubusercontent.com/55983491/206945068-4421b9ca-a66f-49b7-b4f5-8a53579f8177.gif)

# Use

[](https://github.com/micro-joan/DNSrecon-gui#use)

When the tool is ready to use the same installer will give you a URL that you must put in the browser **in a private window** so every time you do a search you will have to open a new window in private or clear your browser cache to refresh the graphics.

# Tools

[](https://github.com/micro-joan/DNSrecon-gui#tools)

|Service|Functions|Status|
|---|---|---|
|[Text2MindMap](https://github.com/TobLoef/text2mindmap)|Convert text to mindmap|✅ Free|
|[dnsenum](https://www.kali.org/tools/dnsenum/)|DNS information gathering|✅ Free|
**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/micro-joan/DNSrecon-gui). Be sure to check out the original post for more details.

# What is dnsrecon Full Guide


DNS reconnaissance is an important part of network reconnaissance and information gathering. DNSRecon is a popular command-line tool used for performing DNS reconnaissance, enumeration, and information gathering. It can be used to gather valuable information about a target domain, such as its subdomains, IP addresses, DNS records, and more. In this article, we will provide a comprehensive guide on DNSRecon, including what it is, how to use it, and some examples of its commands.

![](https://miro.medium.com/v2/resize:fit:700/1*Nw3oSqFG8j7hXzXisk41-g.png)

What is **DNSRecon?**

DNSRecon is a command-line tool used for DNS reconnaissance, enumeration, and information gathering. It is designed to be used by security professionals and ethical hackers to assess the security of a network and identify potential vulnerabilities. DNSRecon can be used to perform the following tasks:

- **Enumeration of subdomains**: DNSRecon can be used to enumerate all subdomains of a target domain. This is useful for discovering hidden subdomains that may be used for malicious purposes.
- **Retrieval of DNS records**: DNSRecon can be used to retrieve DNS records for a target domain, including MX, NS, SOA, TXT, and other types of records.
- **Brute-forcing of subdomains**: DNSRecon can be used to brute-force subdomains of a target domain. This is useful for discovering subdomains that may have been missed during enumeration.
- **Zone transfers**: DNSRecon can be used to perform zone transfers on a target domain. This is useful for retrieving a complete list of DNS records for a domain.
- **Reverse DNS lookups**: DNSRecon can be used to perform reverse DNS lookups. This is useful for discovering the IP addresses associated with a domain.

How to Install DNSRecon?

DNSRecon is written in Python and can be installed on various operating systems, including Linux, Windows, and macOS. To install **DNSRecon** on Linux, follow these steps:

- This tool is preinstalled in Kali Linux but if it’s not in your system then you can git clone this from the GitHub link in the end.

How to Use DNSRecon?

DNSRecon is a command-line tool, which means it is run from a terminal. The basic syntax for using DNSRecon is:

dnsrecon <options> <target>

dnsrecon  -h, --help  
              show help message and exit

Where `<options>` are the different options and parameters that can be used with DNSRecon, and `<target>` is the target domain or IP address that you want to perform DNS reconnaissance on.

Here are some examples of how to use DNSRecon:

- To enumerate subdomains of microsoft.com, run the following command:

dnsrecon -d microsoft.com  
[*] std: Performing General Enumeration against: microsoft.com...  
[-] DNSSEC is not configured for microsoft.com  
[*]      SOA ns1-39.azure-dns.com 150.171.10.39  
[*]      SOA ns1-39.azure-dns.com 2603:1061:0:10::27  
[*]      NS ns3-39.azure-dns.org 13.107.222.39  
[*]      NS ns3-39.azure-dns.org 2a01:111:4000:10::27  
[*]      NS ns4-39.azure-dns.info 13.107.206.39  
[*]      NS ns4-39.azure-dns.info 2620:1ec:bda:10::27  
[*]      NS ns2-39.azure-dns.net 150.171.16.39  
[*]      NS ns2-39.azure-dns.net 2620:1ec:8ec:10::27  
[*]      NS ns1-39.azure-dns.com 150.171.10.39  
[*]      NS ns1-39.azure-dns.com 2603:1061:0:10::27  
[*]      MX microsoft-com.mail.protection.outlook.com 40.93.207.1  
[*]      MX microsoft-com.mail.protection.outlook.com 104.47.53.36  
[*]      MX microsoft-com.mail.protection.outlook.com 40.93.207.5  
[*]      MX microsoft-com.mail.protection.outlook.com 52.101.40.29  
[*]      MX microsoft-com.mail.protection.outlook.com 104.47.54.36  
[*]      MX microsoft-com.mail.protection.outlook.com 40.93.207.7  
[*]      MX microsoft-com.mail.protection.outlook.com 40.93.212.0  
[*]      A microsoft.com 20.103.85.33  
[*]      A microsoft.com 20.112.52.29  
[*]      A microsoft.com 20.53.203.50  
[*]      A microsoft.com 20.81.111.85  
[*]      A microsoft.com 20.84.181.62  
[*]      TXT microsoft.com fg2t0gov9424p2tdcuo94goe9j  
[*]      TXT microsoft.com t7sebee51jrj7vm932k531hipa  
[*]      TXT microsoft.com google-site-verification=uFg3wr5PWsK8lV029RoXXBBUW0_E6qf1WEWVHhetkOY  
[*]      TXT microsoft.com d365mktkey=j2qHWq9BHdaa3ZXZH8x64daJZxEWsFa0dxDeilxDoYYx  
[*]      TXT microsoft.com d365mktkey=3uc1cf82cpv750lzk70v9bvf2  
[*]      TXT microsoft.com google-site-verification=GfDnTUdATPsK1230J0mXbfsYw-3A9BVMVaKSd4DcKgI  
[*]      TXT microsoft.com google-site-verification=pjPOauSPcrfXOZS9jnPPa5axowcHGCDAl1_86dCqFpk  
[*]      TXT microsoft.com d365mktkey=6358r1b7e13hox60tl1uagv14  
[*]      TXT microsoft.com d365mktkey=SxDf1EZxLvMwx6eEZUxzjFFgHoapF8DvtWEUjwq7ZTwx  
[*]      TXT microsoft.com d365mktkey=QDa792dLCZhvaAOOCe2Hz6WTzmTssOp1snABhxWibhMx  
[*]      TXT microsoft.com v=spf1 include:_spf-a.microsoft.com include:_spf-b.microsoft.com include:_spf-c.microsoft.com include:_spf-ssg-a.msft.net include:spf-a.hotmail.com include:_spf1-meo.microsoft.com -all  
[*]      TXT microsoft.com 8RPDXjBzBS9tu7Pbysu7qCACrwXPoDV8ZtLfthTnC4y9VJFLd84it5sQlEITgSLJ4KOIA8pBZxmyvPujuUvhOg==  
[*]      TXT microsoft.com docusign=d5a3737c-c23c-4bd0-9095-d2ff621f2840  
[*]      TXT microsoft.com facebook-domain-verification=fwzwhbbzwmg5fzgotc2go51olc3566  
[*]      TXT microsoft.com hubspot-developer-verification=OTQ5NGIwYWEtODNmZi00YWE1LTkyNmQtNDhjMDMxY2JjNDAx  
[*]      TXT microsoft.com google-site-verification=M--CVfn_YwsV-2FGbCp_HFaEj23BmT0cTF4l8hXgpvM  
[*]      TXT _dmarc.microsoft.com v=DMARC1; p=reject; pct=100; rua=itex-rua@microsoft.com; ruf=itex-ruf@microsoft.com; fo=1  
[*] Enumerating SRV Records  
[+]      SRV _xmpp-server._tcp.microsoft.com sipdog3.microsoft.com 131.107.1.47 5269  
[+]      SRV _sipfederationtls._tcp.microsoft.com sipfed.online.lync.com 52.113.101.30 5061  
[+]      SRV _sip._tls.microsoft.com sipdir.online.lync.com 52.113.67.75 443  
[+]      SRV _sip._tls.microsoft.com sipdir.online.lync.com 2603:1047:0:d::f 443  
[+] 4 Records Found

- To retrieve DNS records for google.com, run the following command:

dnsrecon -d google.com -t std  
[*] std: Performing General Enumeration against: google.com...  
[-] DNSSEC is not configured for google.com  
[*]      SOA ns1.google.com 216.239.32.10  
[*]      SOA ns1.google.com 2001:4860:4802:32::a  
[*]      NS ns1.google.com 216.239.32.10  
[*]      NS ns1.google.com 2001:4860:4802:32::a  
[*]      NS ns2.google.com 216.239.34.10  
[*]      NS ns2.google.com 2001:4860:4802:34::a  
[*]      NS ns3.google.com 216.239.36.10  
[*]      NS ns3.google.com 2001:4860:4802:36::a  
[*]      NS ns4.google.com 216.239.38.10  
[*]      NS ns4.google.com 2001:4860:4802:38::a  
[*]      MX smtp.google.com 172.253.118.27  
[*]      MX smtp.google.com 74.125.130.26  
[*]      MX smtp.google.com 74.125.200.26  
[*]      MX smtp.google.com 74.125.200.27  
[*]      MX smtp.google.com 172.253.118.26  
[*]      MX smtp.google.com 2404:6800:4003:c00::1a  
[*]      MX smtp.google.com 2404:6800:4003:c00::1b  
[*]      MX smtp.google.com 2404:6800:4003:c05::1a  
[*]      MX smtp.google.com 2404:6800:4003:c05::1b  
[*]      A google.com 142.250.193.238  
[*]      AAAA google.com 2404:6800:4002:81d::200e  
[*]      TXT google.com globalsign-smime-dv=CDYX+XFHUw2wml6/Gb8+59BsH31KzUr6c1l2BPvqKX8=  
[*]      TXT google.com webexdomainverification.8YX6G=6e6922db-e3e6-4a36-904e-a805c28087fa  
[*]      TXT google.com google-site-verification=TV9-DBe4R80X4v0M4U_bd_J9cpOJM0nikft0jAgjmsQ  
[*]      TXT google.com google-site-verification=wD8N7i1JTNTkezJ49swvWW48f8_9xveREV4oB-0Hf5o  
[*]      TXT google.com atlassian-domain-verification=5YjTmWmjI92ewqkx2oXmBaD60Td9zWon9r6eakvHX6B77zzkFQto8PQ9QsKnbf4I  
[*]      TXT google.com v=spf1 include:_spf.google.com ~all  
[*]      TXT google.com apple-domain-verification=30afIBcvSuDV2PLX  
[*]      TXT google.com MS=E4A68B9AB2BB9670BCE15412F62916164C0B20BB  
[*]      TXT google.com docusign=05958488-4752-4ef2-95eb-aa7ba8a3bd0e  
[*]      TXT google.com docusign=1b0a6754-49b1-4db5-8540-d2c12664b289  
[*]      TXT google.com facebook-domain-verification=22rm551cu4k0ab0bxsw536tlds4h95  
[*]      TXT google.com onetrust-domain-verification=de01ed21f2fa4d8781cbc3ffb89cf4ef  
[*]      TXT _dmarc.google.com v=DMARC1; p=reject; rua=mailauth-reports@google.com  
[*] Enumerating SRV Records  
[+]      SRV _ldap._tcp.google.com ldap.google.com 216.239.32.58 389  
[+]      SRV _ldap._tcp.google.com ldap.google.com 2001:4860:4802:32::3a 389  
[+]      SRV _caldavs._tcp.google.com calendar.google.com 142.250.194.142 443  
[+]      SRV _caldavs._tcp.google.com calendar.google.com 2404:6800:4002:822::200e 443  
[+]      SRV _caldav._tcp.google.com calendar.google.com 142.250.194.142 80  
[+]      SRV _caldav._tcp.google.com calendar.google.com 2404:6800:4002:822::200e 80  
[+]      SRV _carddavs._tcp.google.com google.com 142.250.193.238 443  
[+]      SRV _carddavs._tcp.google.com google.com 2404:6800:4002:81d::200e 443  
[+] 8 Records Found

DNS zone transfer

 dnsrecon -d medium.com -t axfr  
[*] Checking for Zone Transfer for medium.com name servers  
[*] Resolving SOA Record  
[+]      SOA alina.ns.cloudflare.com 173.245.58.61  
[+]      SOA alina.ns.cloudflare.com 108.162.192.61  
[+]      SOA alina.ns.cloudflare.com 172.64.32.61  
[+]      SOA alina.ns.cloudflare.com 2606:4700:50::adf5:3a3d  
[+]      SOA alina.ns.cloudflare.com 2803:f800:50::6ca2:c03d  
[+]      SOA alina.ns.cloudflare.com 2a06:98c1:50::ac40:203d  
[*] Resolving NS Records  
[*] NS Servers found:  
[+]      NS alina.ns.cloudflare.com 172.64.32.61  
[+]      NS alina.ns.cloudflare.com 173.245.58.61  
[+]      NS alina.ns.cloudflare.com 108.162.192.61  
[+]      NS alina.ns.cloudflare.com 2803:f800:50::6ca2:c03d  
[+]      NS alina.ns.cloudflare.com 2a06:98c1:50::ac40:203d  
[+]      NS alina.ns.cloudflare.com 2606:4700:50::adf5:3a3d  
[+]      NS kip.ns.cloudflare.com 172.64.33.128  
[+]      NS kip.ns.cloudflare.com 173.245.59.128  
[+]      NS kip.ns.cloudflare.com 108.162.193.128  
[+]      NS kip.ns.cloudflare.com 2a06:98c1:50::ac40:2180  
[+]      NS kip.ns.cloudflare.com 2606:4700:58::adf5:3b80  
[+]      NS kip.ns.cloudflare.com 2803:f800:50::6ca2:c180  
[*] Removing any duplicate NS server IP Addresses...  
[*]    
[*] Trying NS server 173.245.58.61  
[+] 173.245.58.61 Has port 53 TCP Open  
[-] Zone Transfer Failed (Zone transfer error: FORMERR)  
[*]    
[*] Trying NS server 108.162.192.61  
[+] 108.162.192.61 Has port 53 TCP Open  
[-] Zone Transfer Failed (Zone transfer error: FORMERR)  
[*]    
[*] Trying NS server 108.162.193.128  
[+] 108.162.193.128 Has port 53 TCP Open  
[-] Zone Transfer Failed (Zone transfer error: FORMERR)  
[*]    
[*] Trying NS server 172.64.32.61  
[+] 172.64.32.61 Has port 53 TCP Open  
[-] Zone Transfer Failed (Zone transfer error: FORMERR)  
[*]    
[*] Trying NS server 2606:4700:50::adf5:3a3d  
[-] Zone Transfer Failed for 2606:4700:50::adf5:3a3d!  
[-] Port 53 TCP is being filtered  
[*]    
[*] Trying NS server 2803:f800:50::6ca2:c03d  
[-] Zone Transfer Failed for 2803:f800:50::6ca2:c03d!  
[-] Port 53 TCP is being filtered  
[*]    
[*] Trying NS server 2a06:98c1:50::ac40:203d  
[-] Zone Transfer Failed for 2a06:98c1:50::ac40:203d!  
[-] Port 53 TCP is being filtered  
[*]    
[*] Trying NS server 173.245.59.128  
[+] 173.245.59.128 Has port 53 TCP Open  
[-] Zone Transfer Failed (Zone transfer error: FORMERR)  
[*]    
[*] Trying NS server 2803:f800:50::6ca2:c180  
[-] Zone Transfer Failed for 2803:f800:50::6ca2:c180!  
[-] Port 53 TCP is being filtered  
[*]    
[*] Trying NS server 2606:4700:58::adf5:3b80  
[-] Zone Transfer Failed for 2606:4700:58::adf5:3b80!  
[-] Port 53 TCP is being filtered  
[*]    
[*] Trying NS server 172.64.33.128  
[+] 172.64.33.128 Has port 53 TCP Open  
[-] Zone Transfer Failed (Zone transfer error: FORMERR)  
[*]    
[*] Trying NS server 2a06:98c1:50::ac40:2180  
[-] Zone Transfer Failed for 2a06:98c1:50::ac40:2180!  
[-] Port 53 TCP is being filtered

**Options:**

Reverse Lookup

dnsrecon -r 173.245.59.0/16                
[*] Performing Reverse Lookup from 173.245.0.0 to 173.245.255.255

-n NS_SERVER  
 Domain server to use. If none is given, the SOA of the target will be used. Multiple servers can be specified using a  
 comma-separated list.  
-D DICTIONARY  
 Dictionary file of subdomains and hostnames to use for brute force. Filter out of brute force domain lookup, records  
 that resolve to the wildcard-defined IP address when saving records.  
-f   
Filter out of brute force domain lookup, records that resolve to the wildcard-defined IP address when saving records.  
-a   
Perform AXFR with standard enumeration.  
-s   
Perform a reverse lookup of IPv4 ranges in the SPF record with standard enumeration.  
-y   
Perform Yandex enumeration with standard enumeration.  
-b   
Perform Bing enumeration with standard enumeration.  
-k  
 Perform crt.sh enumeration with standard enumeration.  
-w   
Perform deep Whois record analysis and reverse lookup of IP ranges found through Whois when doing a standard enumeration.  
-z  
 Performs a DNSSEC zone walk with standard enumeration.  
 - threads  
 Number of threads to use in reverse lookups, forward lookups, brute force, and SRV record enumeration.  
 - lifetime  
 Time to wait for a server to respond to a query. default is 3.  
 - tcp Use TCP protocol to make queries.  
 - db  
 SQLite 3 file to save found records.  
-x  
 XML file to save found records.  
-c CSV  
 Comma-separated value file.  
-j JSON  
 JSON file.  
 - iw Continue brute forcing a domain even if wildcard records are   
discovered.  
 - disable_check_recursion  
 Disables check for recursion on name servers  
 - disable_check_bindversion  
 Disables check for BIND version on name servers  
-v Enable verbose  
-V Show version  
-t TYPE  
 Type of enumeration to perform. There are several possible types:  
std: SOA, NS, A, AAAA, MX, and SRV.  
rvl: Reverse lookup of a given CIDR or IP range.  
brt: Brute force domains and hosts using a given dictionary.  
srv: SRV records.  
axfr: Test all NS servers for a zone transfer.  
bing: Perform Bing search for subdomains and hosts.  
yand: Perform Yandex search for subdomains and hosts.  
crt: Perform crt.sh search for subdomains and hosts.  
snoop: Perform cache snooping against all NS servers for a given domain, testing all with file containing the do‐  
 mains, file given with -D option.  
tld: Remove the TLD of given domain and test against all TLDs registered in IANA.  
zonewalk: Perform a DNSSEC zone walk using NSEC records.

This script provides the ability to perform:

- Check all NS Records for Zone Transfers.
- Enumerate General DNS Records for a given Domain (MX, SOA, NS, A, AAAA, SPF and TXT).
- Perform common SRV Record Enumeration.
- Top Level Domain (TLD) Expansion.
- Check for Wildcard Resolution.
- Brute Force subdomain and host A and AAAA records given a domain and a wordlist.
- Perform a PTR Record lookup for a given IP Range or CIDR.
- Check a DNS Server Cached records for A, AAAA and CNAME Records provided a list of host records in a text file to check.

DNSrecon is a powerful DNS reconnaissance tool that can help you discover subdomains, DNS servers, and other important information about a domain. By using the various command line options, you can customize your DNS reconnaissance and speed up the scanning process. Whether you’re a security professional, a system administrator, or just a curious user, DNSrecon is a valuable tool to have in your arsenal.

**Credit:** This information was adapted from an excellent guide on [Medium](https://medium.com/@techmindxperts/what-is-dnsrecon-full-guide-with-examples-355aba308332). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/KvMI3ICQWGY?si=URILjQdbOunAj5Kx" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=KvMI3ICQWGY). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/b4-kWmv8hOo?si=5clHFVXgcEDP-R9P" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=b4-kWmv8hOo). Be sure to check out the original post for more details.

