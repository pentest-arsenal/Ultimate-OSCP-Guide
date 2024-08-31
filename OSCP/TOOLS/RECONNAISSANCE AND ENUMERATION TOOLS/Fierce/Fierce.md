# Fierce

[](https://github.com/mschwager/fierce#fierce)

[![CI](https://github.com/mschwager/fierce/actions/workflows/ci.yml/badge.svg)](https://github.com/mschwager/fierce/actions/workflows/ci.yml) [![Python Versions](https://camo.githubusercontent.com/45000730e81bfdc411ea7f105f422018718fb878cb7cdc6030ea056cbf635869/68747470733a2f2f696d672e736869656c64732e696f2f707970692f707976657273696f6e732f6669657263652e737667)](https://img.shields.io/pypi/pyversions/fierce.svg) [![PyPI Version](https://camo.githubusercontent.com/afdb6d98baf37dc2d716207a8e656f381acbba1b9ebdd970ab6cdcb66de561b5/68747470733a2f2f696d672e736869656c64732e696f2f707970692f762f6669657263652e737667)](https://img.shields.io/pypi/v/fierce.svg)

Fierce is a `DNS` reconnaissance tool for locating non-contiguous IP space.

Useful links:

- [Domain Name System (DNS)](https://en.wikipedia.org/wiki/Domain_Name_System)
    - [Domain Names - Concepts and Facilities](https://tools.ietf.org/html/rfc1034)
    - [Domain Names - Implementation and Specification](https://tools.ietf.org/html/rfc1035)
    - [Threat Analysis of the Domain Name System (DNS)](https://tools.ietf.org/html/rfc3833)
- [Name Servers (NS)](https://en.wikipedia.org/wiki/Domain_Name_System#Name_servers)
- [State of Authority Record (SOA)](https://en.wikipedia.org/wiki/List_of_DNS_record_types#SOA)
- [Zone Transfer](https://en.wikipedia.org/wiki/DNS_zone_transfer)
    - [DNS Zone Transfer Protocol (AXFR)](https://tools.ietf.org/html/rfc5936)
    - [Incremental Zone Transfer in DNS (IXFR)](https://tools.ietf.org/html/rfc1995)
- [Wildcard DNS Record](https://en.wikipedia.org/wiki/Wildcard_DNS_record)

# Overview

[](https://github.com/mschwager/fierce#overview)

First, credit where credit is due, `fierce` was [originally written](https://github.com/mschwager/fierce/blob/master/scripts/fierce.pl) by RSnake along with others at [http://ha.ckers.org/](http://ha.ckers.org/). This is simply a conversion to Python 3 to simplify and modernize the codebase.

The original description was very apt, so I'll include it here:

> Fierce is a semi-lightweight scanner that helps locate non-contiguous IP space and hostnames against specified domains. It's really meant as a pre-cursor to nmap, unicornscan, nessus, nikto, etc, since all of those require that you already know what IP space you are looking for. This does not perform exploitation and does not scan the whole internet indiscriminately. It is meant specifically to locate likely targets both inside and outside a corporate network. Because it uses DNS primarily you will often find mis-configured networks that leak internal address space. That's especially useful in targeted malware.

# Installing

[](https://github.com/mschwager/fierce#installing)

```
$ python -m pip install fierce
$ fierce -h
```

OR

```
$ git clone https://github.com/mschwager/fierce.git
$ cd fierce
$ python -m pip install dnspython==1.16.0
$ python fierce/fierce.py -h
```

# Using

[](https://github.com/mschwager/fierce#using)

Let's start with something basic:

```
$ fierce --domain google.com --subdomains accounts admin ads
```

Traverse IPs near discovered domains to search for contiguous blocks with the `--traverse` flag:

```
$ fierce --domain facebook.com --subdomains admin --traverse 10
```

Limit nearby IP traversal to certain domains with the `--search` flag:

```
$ fierce --domain facebook.com --subdomains admin --search fb.com fb.net
```

Attempt an `HTTP` connection on domains discovered with the `--connect` flag:

```
$ fierce --domain stackoverflow.com --subdomains mail --connect
```

Exchange speed for breadth with the `--wide` flag, which looks for nearby domains on all IPs of the [/24](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing#IPv4_CIDR_blocks) of a discovered domain:

```
$ fierce --domain facebook.com --wide
```

Zone transfers are rare these days, but they give us the keys to the DNS castle. [zonetransfer.me](https://digi.ninja/projects/zonetransferme.php) is a very useful service for testing for and learning about zone transfers:

```
$ fierce --domain zonetransfer.me
```

To save the results to a file for later use we can simply redirect output:

```
$ fierce --domain zonetransfer.me > output.txt
```

Internal networks will often have large blocks of contiguous IP space assigned. We can scan those as well:

```
$ fierce --dns-servers 10.0.0.1 --range 10.0.0.0/24
```

Check out `--help` for further information:

```
$ fierce --help
```

# Developing

[](https://github.com/mschwager/fierce#developing)

First, install [`poetry`](https://python-poetry.org/docs/#installation) and development packages:

```
$ poetry install --with dev
```

## Testing

[](https://github.com/mschwager/fierce#testing)

```
$ poetry run pytest
```

## Linting

[](https://github.com/mschwager/fierce#linting)

```
$ poetry run flake8
```

## Coverage

[](https://github.com/mschwager/fierce#coverage)

```
$ poetry run pytest --cov
```

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/mschwager/fierce). Be sure to check out the original post for more details.

# Fierce – DNS reconnaissance tool for locating non-contiguous IP space

Last Updated : 02 Jun, 2024

Understanding the network structure of the organization is very important. So to locate targets both inside and outside a corporate network there is a tool designed in the Python Language known as Fierce. This tool is different from other tools as its main objective is to locate non-contiguous IP spaces and hostnames against specified domains or subdomains. The Fierce tool doesn’t scan the total internet for our results but the results which it finds are really helpful in the process. This tool is open-source and free to use. The Fierce tool is very easier to use due to its tags of flags features.

****Note****: Make Sure You have Python Installed on your System, as this is a python-based tool. Click to check the Installation process: [Python Installation Steps on Linux](https://www.geeksforgeeks.org/how-to-install-python-on-linux)

## Installation of Fierce Tool on Kali Linux

****Step 1****: Check whether Python Environment is Established or not, use the following command.

python3

![](https://media.geeksforgeeks.org/wp-content/uploads/20210823223022/Step1.jpg)

****Step 2****: Open up your Kali Linux terminal and move to the Desktop directory using the following command.

cd Desktop

![](https://media.geeksforgeeks.org/wp-content/uploads/20210823223024/Step2.jpg)

****Step 3****: You are on Desktop now, create a new directory called Fierce using the following command. In this directory, we will complete the installation of the Fierce tool.

mkdir Fierce 

![](https://media.geeksforgeeks.org/wp-content/uploads/20210823223026/Step3.jpg)

****Step 4****: Now switch to the Fierce directory using the following command.

cd Fierce 

![](https://media.geeksforgeeks.org/wp-content/uploads/20210823223027/Step4.jpg)

****Step 5****: Now you have to install the tool. You have to clone the tool from Github.

git clone git clone https://github.com/mschwager/fierce.git

![](https://media.geeksforgeeks.org/wp-content/uploads/20210823223029/Step5.jpg)

****Step 6****: The tool has been downloaded successfully in the Fierce directory. Now list out the contents of the tool by using the below command.

ls

![](https://media.geeksforgeeks.org/wp-content/uploads/20210823223031/Step6.jpg)

****Step 7****: You can observe that there is a new directory created for the Fierce tool that has been generated while we were installing the tool. Now move to that directory using the below command:

cd fierce 

![](https://media.geeksforgeeks.org/wp-content/uploads/20210823223032/Step7.jpg)

****Step 8****: Once again to discover the contents of the tool, use the below command.

ls

![](https://media.geeksforgeeks.org/wp-content/uploads/20210823223034/Step8.jpg)

****Step 9****: Download the required packages for running the tool, use the following command.

pip3 install -r requirements.txt

![](https://media.geeksforgeeks.org/wp-content/uploads/20210823223035/Step9min.jpg)

****Step 10****: Now we are done with our installation, Use the below command to view the help (gives a better understanding of the tool) index of the tool.

python3 fierce/fierce.py -h

![](https://media.geeksforgeeks.org/wp-content/uploads/20210823223037/Step10min.jpg)

## Attributes

1. The fierce tool has the attributes to perform Reverse Lookups for the specified range of IP addresses.  [–dns-file] option is used.
2. The fierce tool has the attribute to enumerate Domain Name System Records on the Target domain. [–dns-servers] option is used
3. The fierce tool has the attribute of performing Internal as well as External IP ranges Enumeration. [–range] option is used.
4. Class C IP addresses are also supported by the Fierce tool. [–traverse] option is used.
5. The fierce tool has the attribute to Scan Name Server Directory and also Zone Transfer attack.

## How does Fierce  Tool perform Scanning?

The fierce tool is the most helpful tool for the Reconnaissance, Information Gathering, and Scanning phase in the process of Penetration Testing or Network Testing. The working of this tool is very simple. At the very first stage, the tool performs scanning with brute-forcing attacks and can also perform zone transfer attacks on the target is possible. There are massive word lists that contain possible words, through which subdomains of the target can be enumerated. If the subdomain is not in the list, then there is no chance of detection of the subdomain on the target.

## Additional Features and Functions

### 1. Saving

Unfortunately, there is no inbuilt function available for storing the results of the Fierce scan on the target at your disk. Although no saving function is available, so there is no feature to save the output in various formats. But you can redirect the output of the scan into any text file with some Linux skills and terminal commands.

### 2. Range Scan

One of the amazing functions or features of the Fierce tool is the Range scan. You can scan the range of IP address with a single click. –the range is the option that is mandatory while performing a range scan. You need to specify the IP address; like ( 192.168.28.4/24).

### 3. Dictionary file

A brute-forcing attack or method approach is used for enumeration or detection of subdomains associated with the target domain. The inbuilt wordlist file is activated when the installation of the Fierce tool is done on the system. But Fierce tool allows users to use custom subdomains wordlists with a massive number of possible subdomains words. –subdomain-file is the option for using the custom wordlists for brute-forcing.

## Working with Fierce Tool on Kali Linux

****Example 1****: Basic

fierce --domain geeksforgeeks.org --subdomains write admin videos

In this Example, We are performing a simple scan using the subdomain words which include write, admin, videos. We have chosen geeksforgeeks.org as our target.

![](https://media.geeksforgeeks.org/wp-content/uploads/20210823223014/Example1min.jpg)

****Example 2:**** Traverse IPs near discovered domains to search for contiguous blocks with the –traverse flag

fierce --domain geeksforgeeks.org --subdomains videos --traverse 10

In this Example, We are scanning domains near discovered records. Our target domain is geeksforgeeks.org

![](https://media.geeksforgeeks.org/wp-content/uploads/20210823223016/Example2min.jpg)

****Example 3:**** Attempt an HTTP connection on domains discovered with the –connect flag

fierce --domain stackoverflow.com --subdomains mail --connect

In this Example, We are attempting HTTP connection on the domains using the connect flag. We have chosen a different target for this Example, which is stackoverflow.com.

![](https://media.geeksforgeeks.org/wp-content/uploads/20210823223018/Example3min.jpg)

****Example 4:**** Exchange speed for breadth with the –wide flag, which looks for nearby domains on all IPs of the /24 of a discovered domain

fierce --domain geeksforgeeks.org --wide

In this example, We will scan the entire class of discovered records. (Full Detailed Scan)

![Example4min-copy-2](https://media.geeksforgeeks.org/wp-content/uploads/20240602132158/Example4min-copy-2.webp)

****Example 5:**** Zone transfers are rare these days, but they give us the keys to the DNS castle.

fierce --domain geeksforgeeks.org

In this Example, We are performing a basic scan without any arguments on geeksforgeeks.org

![](https://media.geeksforgeeks.org/wp-content/uploads/20210823223021/Example5min.jpg)

**Credit:** This information was adapted from an excellent guide on [GeeksForGeeks](https://www.geeksforgeeks.org/fierce-dns-reconnaissance-tool-for-locating-non-contiguous-ip-space/). Be sure to check out the original post for more details.

# Tool Documentation:

## fierce Usage Example

Run a default scan against the target domain (`-dns example.com`):

```console
root@kali:~# fierce -dns example.com
DNS Servers for example.com:
    b.iana-servers.net
    a.iana-servers.net

Trying zone transfer first...
    Testing b.iana-servers.net
        Request timed out or transfer not allowed.
    Testing a.iana-servers.net
        Request timed out or transfer not allowed.

Unsuccessful in zone transfer (it was worth a shot)
Okay, trying the good old fashioned way... brute force

Checking for wildcard DNS...
Nope. Good.
Now performing 2280 test(s)...
```

---

  

# Packages and Binaries:

### fierce

Fierce is a semi-lightweight scanner that helps locate non-contiguous IP space and hostnames against specified domains. It’s really meant as a pre-cursor to nmap, unicornscan, nessus, nikto, etc, since all of those require that you already know what IP space you are looking for. This does not perform exploitation and does not scan the whole internet indiscriminately. It is meant specifically to locate likely targets both inside and outside a corporate network.

Because it uses DNS primarily you will often find mis-configured networks that leak internal address space. That’s especially useful in targeted malware. Originally written by RSnake along with others at [http://ha.ckers.org/](http://ha.ckers.org/). This is simply a conversion to Python 3 to simplify and modernize the codebase.

**Installed size:** `238 KB`  
**How to install:** `sudo apt install fierce`

Dependencies:

- python3
- python3-dnspython

##### fierce

DNS scanner that helps locate non-contiguous IP space and hostnames against specified domains.

```console
root@kali:~# fierce -h
usage: fierce [-h] [--domain DOMAIN] [--connect] [--wide]
              [--traverse TRAVERSE] [--search SEARCH [SEARCH ...]]
              [--range RANGE] [--delay DELAY]
              [--subdomains SUBDOMAINS [SUBDOMAINS ...] | --subdomain-file
              SUBDOMAIN_FILE] [--dns-servers DNS_SERVERS [DNS_SERVERS ...] |
              --dns-file DNS_FILE] [--tcp]

        A DNS reconnaissance tool for locating non-contiguous IP space.
        

options:
  -h, --help            show this help message and exit
  --domain DOMAIN       domain name to test
  --connect             attempt HTTP connection to non-RFC 1918 hosts
  --wide                scan entire class c of discovered records
  --traverse TRAVERSE   scan IPs near discovered records, this won't enter adjacent class c's
  --search SEARCH [SEARCH ...]
                        filter on these domains when expanding lookup
  --range RANGE         scan an internal IP range, use cidr notation
  --delay DELAY         time to wait between lookups
  --subdomains SUBDOMAINS [SUBDOMAINS ...]
                        use these subdomains
  --subdomain-file SUBDOMAIN_FILE
                        use subdomains specified in this file (one per line)
  --dns-servers DNS_SERVERS [DNS_SERVERS ...]
                        use these dns servers for reverse lookups
  --dns-file DNS_FILE   use dns servers specified in this file for reverse lookups (one per line)
  --tcp                 use TCP instead of UDP
```

---

Updated on: 2024-Mar-11

**Credit:** This information was adapted from an excellent guide on [Kali.org](https://www.kali.org/tools/fierce/). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/RyXcu0WY4N8?si=SGbrOVeNqjItb12C" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=RyXcu0WY4N8). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/qy54vtvWT0E?si=3ZJG_IH-udgM39ta" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=qy54vtvWT0E). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/80lgwFtGBVs?si=Y20RbI77oSZanP5o" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=80lgwFtGBVs). Be sure to check out the original post for more details.


