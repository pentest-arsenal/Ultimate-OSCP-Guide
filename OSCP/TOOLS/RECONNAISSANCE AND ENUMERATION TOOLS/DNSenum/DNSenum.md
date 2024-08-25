# DNSenum

[](https://github.com/theMiddleBlue/DNSenum?tab=readme-ov-file#dnsenum)

DNSenum is a Bash script for DNS Enumeration. Try to resolve all subdomains of a given domain name.

## Usage

[](https://github.com/theMiddleBlue/DNSenum?tab=readme-ov-file#usage)

```shell
+
+ Usage: ./dnsenum.sh -d <domain> [-f <file] [-n <dns server>] [-c]
+
+ -d <domain>       Domain name to test
+ -f <file>         Subdomain list file to use for test
+ -n <dns server>   DNS Server to use for query
+ -c                Check for HTTP Server banner
+ -v                Check Domain on VirusTotal
+ -s                Set Shodan API Key in order to query it
+ -r <result>       Show only result that match <result>
+
```

## Example

[](https://github.com/theMiddleBlue/DNSenum?tab=readme-ov-file#example)

```shell
# ./dnsenum.sh -d iol.it -c

+
+ Dns Enumeration for domain iol.it
+
                 www | CNAME      | www.italiaonline.it.           | CloudFront
                mail | CNAME      | mail.libero.it.                |           
                 ftp | CNAME      | merope.iol.it.                 |           
             webmail | CNAME      | webmail.libero.it.             | Apache
                smtp | A          | 212.48.24.42                   |           
                 pop | CNAME      | popimap.iol.it.                |           
        autodiscover | A          | 212.48.24.27                   |           
          autoconfig | CNAME      | autoconfig.libero.it.          | Apache/2.2.15 (CentOS)
                pop3 | CNAME      | popimap.iol.it.                |           
                imap | CNAME      | popimap.iol.it.                |           
                www1 | CNAME      | nacho2000.iol.it.              |           
Trying www.blog ...
```

Example using `-v` that check the domain on VirusTotal

```shell
# ./dnsenum.sh -d waf.red -v

+
+ Dns Enumeration for domain waf.red
+ Check URL on VirusTotal
+

+
+ Querying VirusTotal...
+ Result from VirusTotal:
+
                blog | CNAME      | node1.waf.red.                 |           
+
+ End Results from VirusTotal.
+

+
+ Start enumeration from file...
+
             waf.red | A          | 188.166.133.184                |           
                 www | A          | 188.166.133.184                |           
                blog | CNAME      | node1.waf.red.                 |
trying www2...
```

[Example video](https://github.com/GrayHats/DNSenum/raw/master/2018-08-23%2011.33.33.mp4)

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/theMiddleBlue/DNSenum?tab=readme-ov-file). Be sure to check out the original post for more details.

# Complete guide to DNSenum

Hello, aspiring ethical hackers. In the previous blogpost on DNS [enumeration](https://www.hackercoolmagazine.com/enumeration-guide-for-beginners/), you learnt what DNS service is used for, different types of records it has, what information can [DNS enumeration](https://www.hackercoolmagazine.com/dns-enumeration-for-beginners/) reveal to hackers or pentesters. In this blogpost you will learn about a tool named DNSenum that can be used to enumerate DNS. DNSenum is a multithreaded perl script that is used to gather information from target DNS servers.

The features of DNSenum are,

1. Get the host’s address (A record).
2. Get the nameservers (NS).
3. Get the MX record (MX).
4. Perform axfr queries on nameservers and get BIND VERSION.
5. Get extra names and subdomains via google scraping (google query = “-www site:domain”).
6. Brute force subdomains from file, can also perform recursion on subdomain that have NS records.
7. Calculate C class domain network ranges and perform whois queries on them.
8. Perform reverse lookups on netranges (C class or/and whois netranges).

Let’s see how to perform DNS enumeration with DNSenum. DNSenum is included by default in Kali Linux. If you want to enumerate a domain with DNSenum. all you have to do is supply a domain name as shown below.

==dnsenum <domain>==

When run in default mode, DNSnum first enumerates the host address, then the name servers, then MX records, ACFR queries, extra names and subdomains via google scraping, brute forces subdomains from them, calculates the class C IP network ranges from the results and performs whois queries on them and performs reverse lookup on these IP addresses.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_1.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_1.jpg)

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_2.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_2.jpg)

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_3.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_3.jpg)

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_4.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_4.jpg)

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_5.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_5.jpg)

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_67.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_67.jpg)

**==–dnsserver==**

In some cases, the result from the enumeration can vary depending on the server that is queried. Using DNSenum, we can perform a query by using another DNS server as shown below.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_8.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_8.jpg)

When you first use dnsenum on a domain to perform enumeration, you will notice that there will be a considerable delay at some stages. The delay occurs while dnsenum is brute forcing the subdomain names and then while performing reverse lookup on the IP address range.

While brute forcing the subdomain names, there is a delay because the file used by DNSenum (“/usr/share/dnsenum/dns.txt”) has over 1506 entries. So, until the tool checks all the entries, there will definitely be a delay. Can we reduce this data? Yes, by using another file instead of the default one. For example, we can create our own “dns.txt” file with entries of subdomains gathered from other type of enumeration.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_11.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_11.jpg)

**==–file(f)==**

We can specify this custom file with the (-f) option as shown below.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_12.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_12.jpg)

**==–subfile==**

We can also save the output of subdomain brute forcing in a file using the subfile option as shown below.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_17.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_17.jpg)

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_18.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_18.jpg)

**==–noreverse==**

Coming to reverse lookup, while performing reverse lookup on 512 IP addresses (in this case) definitely takes time. But don’t worry. We can skip the reverse lookup by using the normal option.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_13.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_13.jpg)

**==–private==**

This option enumerates and saves the private IP addresses of a domain in the file named <domain_name>_ips.txt.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_14.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_14.jpg)

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_15.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_15.jpg)

**==–timeout (-t)==**

The default timeout option of TCP queries and UDP queries for dnsenum is 10 seconds. The timeout option allows us to change it.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_16.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_16.jpg)

**==–threads (va)==**

This option is used to specify the number of threads to perform different queries.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_19.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_19.jpg)

**==–verbose (-v)==**

You already know what this option does. It reveals more information. See the differences.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_20.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_20.jpg)

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_21.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_21.jpg)

**==–scrape (-s)==**

Used to specify the number of subdomains to be scraped from Google.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_23.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_23.jpg)

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_24.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_24.jpg)

Here’s the result.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_25.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_25.jpg)

**==–page (-p)==**

While scraping the subdomain with dnsenum above, you should have noticed that it queries Google search pages for subdomains related to the domain. By default, it is 20 pages. Using this option, it can be changed. For example, lets set it to 10.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_26.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_26.jpg)

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_2728.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_2728.jpg)

**==–recursion (-r)==**

This option can be used to perform recursion on subdomain gathering.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_29.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_29.jpg)

**==–whois (-w)==**

As you might have expected, this option is used to perform whois queries on class C network ranges. It can be time consuming. Use wisely. Learn what is whois footpriting.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_30.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_30.jpg)

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_31.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_31.jpg)

**==–delay (-d)==**

This option is used to specify the maximum delay between each whois query. The default delay is 3 seconds.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_32.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/02/DNSenum_32.jpg)

That’s all about DNSenum.

**Credit:** This information was adapted from an excellent guide on [HackerCoolMagazine](https://www.hackercoolmagazine.com/complete-guide-to-dnsenum/). Be sure to check out the original post for more details.

# DNSenum: A command-line Information Gathering Tool

**Olá👋 I’m Ankita Sinha, an MTech CSE student doing a specialization in Information Security. You can connect with me on** [**LinkedIn**](https://www.linkedin.com/in/ankita-sinha-b3781b138/)**, and** [**Github**](https://github.com/AnkitaSinha98)**.**

DNSenum is a command-line tool that automatically identifies essential DNS records such as MX, mail exchange servers, NS, domain name servers, or A - the address record for a domain. It also attempts zone transfers on all identified servers. It can try reverse resolution (that is, getting the hostname given an IP address) and brute-forcing (querying for the existence of hostnames to get their IP address) of subdomains and hostnames. DNSenum is a multi-threaded Perl script to enumerate a domain’s DNS information and discover non-contiguous IP blocks.

**Operations:**

> 1) Get the host’s address (A record).
> 
> 2) Get the name servers (threaded).
> 
> 3) Get the MX record (threaded).
> 
> 4) Perform axfr queries on name servers and get BIND VERSION (threaded).
> 
> 5) Get extra names and subdomains via google scraping (google query = “allinurl: -www site:domain”).
> 
> 6) Brute force subdomains from the file can also perform recursion on a subdomain with NS records, i.e., threaded.
> 
> 7) Calculate C class domain network ranges and run whois queries on them (thread).
> 
> 8) Run reverse lookups on entrances (class C or/and whois) (threaded).
> 
> 9) Write IP-blocks to domain_ips.txt.

# **Commands:**

1. **dnsenum -h:** This command is used for help in order to find more usages of dnsenum tool. One can easily refer to this help command for the usage of dnsenum.

![](https://miro.medium.com/v2/resize:fit:700/1*_ps6t-AIV8IiOd9whbLshw.png)

**2.** **dnsenum zonetransfer.me:** This command is used to get the details of a particular domain name and fetch information like host addresses, servers, MX servers along with the IP addresses for the hostnames.

![](https://miro.medium.com/v2/resize:fit:700/1*WnxkASSL8acAReKQJ7E2lw.png)

![](https://miro.medium.com/v2/resize:fit:700/1*DE0ZGprd9ITEUUOik23Skg.png)

**3.** **dnsenum hackthissite.org:** This command is also the same as the previous command but here the hostname is different that is ‘hackthissite.org’.

![](https://miro.medium.com/v2/resize:fit:700/1*OU3InCWnXu_1RKKDf9tp3w.png)

![](https://miro.medium.com/v2/resize:fit:700/1*aMOM1GJdfaba5vmj9ZsCeA.png)

![](https://miro.medium.com/v2/resize:fit:700/1*GiKXBuCEwRdjNTWaEpAvdA.png)

**4.** **dnsenum –private hackthissite.org:** This command is mainly used in order to view the private addresses for the hostname which is mentioned. We can also get multiple subdomains along with the private address.

![](https://miro.medium.com/v2/resize:fit:700/1*m0uq1OKAzdndwByM_YdPUA.png)

![](https://miro.medium.com/v2/resize:fit:700/1*aIY4SdTxJd8igW9THLlZvQ.png)

**5.** **dnsenum –dnsserver 8.8.8.8 -f wordlist.txt google.com:** This command line is having the combination of two and more commands which is “ — dnsserver” specifies the DNS server as we have used 8.8.8.8 which is the public server for the “google.com”. We have also used ‘-f’ command from the set of wordlists it will perform brute force for all the subdomains which are present in the list.

![](https://miro.medium.com/v2/resize:fit:700/1*lkkjakzmADuHSIujFtV2aQ.png)

![](https://miro.medium.com/v2/resize:fit:700/1*X37PIxc3-3KaJiOK4MpMHQ.png)

**6.** **dnsenum — noreverse -o mydomain.xml google.com:** This command is used for non-reverse for the domain addresses present for the hostname. The “-o” command is refer to the output file format and here the destination will be the present working directory. The format specified here will be “xml”.

![](https://miro.medium.com/v2/resize:fit:700/1*A5iWFKkMIPEqfI1wr7valw.png)

![](https://miro.medium.com/v2/resize:fit:700/1*Hq02OrMWNsZsFR6mAbxi8Q.png)

![](https://miro.medium.com/v2/resize:fit:700/1*gWBE_oJWaUA_ceMNxUb_cw.png)

![](https://miro.medium.com/v2/resize:fit:700/1*ZNJPjhnM26Fn_BwWmFd7wg.png)

![](https://miro.medium.com/v2/resize:fit:700/1*Dhit68a8ruwpBpXwLHFRXQ.png)

**7.** **dnsenum –whois hackthissite.org:** This is a general command which is used to take the information about “who” is logged into the hostname and the IP addresses for those users will be displayed in the terminal.

![](https://miro.medium.com/v2/resize:fit:700/1*_EZo5B0PMglCID9htvgzow.png)

![](https://miro.medium.com/v2/resize:fit:700/1*Mqu40zjLCu-ciRWhVEojkg.png)

**8.** **sudo dnsenum — enum -f “/usr/share/doc/dnsenum/dns.txt” salesforce.com:** This command is used for the enumeration purpose which means that set of all the commands which dnsenum is providing will be compacted to one place. Here we can also see that the “dns.txt” file is having the list of all the keywords which can be used against the set of commands for which hostname is searched.

![](https://miro.medium.com/v2/resize:fit:700/1*Nx8QdvBHG7QKvRAM83sUpQ.png)

![](https://miro.medium.com/v2/resize:fit:700/1*crbTWyOsL-tKKWXFHEC3ag.png)

![](https://miro.medium.com/v2/resize:fit:700/1*5lGz16js6Ug1IGKCHGjavA.png)

**9.** **sudo dnsenum -p 5 -s 5 — threads 2 google.com:** This command is a combination of three instances which is -p , -s and –threads. Each instance is having various functionality. Here -p refers to the pages which are available for the particular hostname. Next -s refers to google scraping which is also used for URL harvesting for the websites. Lastly –threads refer to the hardware-related command line which is used to speed up the process based upon CPU configuration.

![](https://miro.medium.com/v2/resize:fit:700/1*0ofSkfkaig_xWx2tPggbHg.png)

![](https://miro.medium.com/v2/resize:fit:700/1*xcK-MZ83wQG01zlDRFL1Jw.png)

![](https://miro.medium.com/v2/resize:fit:700/1*rYPD7enDOxL909YnWF_e0g.png)

**10.** **Dnsenum hacker.om -v –thread 9:** This command is a combination of two instances which are -v and –thread. Here -v refers to verbose command.

![](https://miro.medium.com/v2/resize:fit:700/1*lP4psKJ5QPL1LEyrLrC_gg.png)

![](https://miro.medium.com/v2/resize:fit:700/1*8DElu4jNwnKJhhLdlmw9vw.png)

**11.** **dnsenum -p 4 -s 5 -f wordlist.txt google.com :** This is the last command where the page is given as 4, scraping is given as 5 and brute force will be carried out based on the wordlist for “google.com”

![](https://miro.medium.com/v2/resize:fit:700/1*44_RO-NtVpmWg1S_x5qd-A.png)

![](https://miro.medium.com/v2/resize:fit:700/1*9lDPcy7kUSdOscoQDZNA0Q.png)

**Conclusion:**

DNSenum is a great tool to be used in the information-gathering stage of penetration testing. We have performed the DNSenum tool having a set of command lines. We have done an analysis of forward lookup, reverse lookup along with the private servers as well as reconnaissance for various domains.

**Credit:** This information was adapted from an excellent guide on [Medium](https://ankisinha.medium.com/dnsenum-a-command-line-information-gathering-tool-a535078207a6). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/mCbz92LdEfY?si=EBVqmtUMx0BS9nmC" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=mCbz92LdEfY). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/jm5bguyZank?si=T1vXLR2uMc6wzX31" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=jm5bguyZank). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Cvun_UZmpv0?si=OyNF8H-tjPB9uAR_" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=Cvun_UZmpv0). Be sure to check out the original post for more details.


