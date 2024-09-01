[![theHarvester](https://github.com/laramies/theHarvester/raw/master/theHarvester-logo.webp)](https://github.com/laramies/theHarvester/blob/master/theHarvester-logo.webp)

[![TheHarvester CI](https://github.com/laramies/theHarvester/workflows/TheHarvester%20Python%20CI/badge.svg)](https://github.com/laramies/theHarvester/workflows/TheHarvester%20Python%20CI/badge.svg) [![TheHarvester Docker Image CI](https://github.com/laramies/theHarvester/workflows/TheHarvester%20Docker%20Image%20CI/badge.svg)](https://github.com/laramies/theHarvester/workflows/TheHarvester%20Docker%20Image%20CI/badge.svg) [![Rawsec's CyberSecurity Inventory](https://camo.githubusercontent.com/577d54fad37801dce8d904d91b5b63cad6bdd788dfe715b8fd635dcd16002897/68747470733a2f2f696e76656e746f72792e7261772e706d2f696d672f6261646765732f5261777365632d696e76656e746f726965642d4646353035305f666c61745f776974686f75745f6c6f676f2e737667)](https://inventory.raw.pm/)

## What is this?

[](https://github.com/laramies/theHarvester#what-is-this)

theHarvester is a simple to use, yet powerful tool designed to be used during the reconnaissance stage of a red  
team assessment or penetration test. It performs open source intelligence (OSINT) gathering to help determine  
a domain's external threat landscape. The tool gathers names, emails, IPs, subdomains, and URLs by using  
multiple public resources that include:  

## Passive modules:

[](https://github.com/laramies/theHarvester#passive-modules)

- anubis: Anubis-DB - [https://github.com/jonluca/anubis](https://github.com/jonluca/anubis)
    
- bevigil: CloudSEK BeVigil scans mobile application for OSINT assets (Requires an API key, see below.) - [https://bevigil.com/osint-api](https://bevigil.com/osint-api)
    
- baidu: Baidu search engine - [www.baidu.com](http://www.baidu.com/)
    
- binaryedge: List of known subdomains (Requires an API key, see below.) - [https://www.binaryedge.io](https://www.binaryedge.io/)
    
- bing: Microsoft search engine - [https://www.bing.com](https://www.bing.com/)
    
- bingapi: Microsoft search engine, through the API (Requires an API key, see below.)
    
- brave: Brave search engine - [https://search.brave.com/](https://search.brave.com/)
    
- bufferoverun: (Requires an API key, see below.) [https://tls.bufferover.run](https://tls.bufferover.run/)
    
- censys: [Censys search engine](https://search.censys.io/) will use certificates searches to enumerate subdomains and gather emails  
    (Requires an API key, see below.) [https://censys.io](https://censys.io/)
    
- certspotter: Cert Spotter monitors Certificate Transparency logs - [https://sslmate.com/certspotter/](https://sslmate.com/certspotter/)
    
- criminalip: Specialized Cyber Threat Intelligence (CTI) search engine (Requires an API key, see below.) - [https://www.criminalip.io](https://www.criminalip.io/)
    
- crtsh: Comodo Certificate search - [https://crt.sh](https://crt.sh/)
    
- dnsdumpster: DNSdumpster search engine - [https://dnsdumpster.com](https://dnsdumpster.com/)
    
- duckduckgo: DuckDuckGo search engine - [https://duckduckgo.com](https://duckduckgo.com/)
    
- fullhunt: Next-generation attack surface security platform (Requires an API key, see below.) - [https://fullhunt.io](https://fullhunt.io/)
    
- github-code: GitHub code search engine (Requires a GitHub Personal Access Token, see below.) - [www.github.com](http://www.github.com/)
    
- hackertarget: Online vulnerability scanners and network intelligence to help organizations - [https://hackertarget.com](https://hackertarget.com/)
    
- hunter: Hunter search engine (Requires an API key, see below.) - [https://hunter.io](https://hunter.io/)
    
- hunterhow: Internet search engines for security researchers (Requires an API key, see below.) - [https://hunter.how](https://hunter.how/)
    
- intelx: Intelx search engine (Requires an API key, see below.) - [http://intelx.io](http://intelx.io/)
    
- netlas: A Shodan or Censys competitor (Requires an API key, see below.) - [https://app.netlas.io](https://app.netlas.io/)
    
- onyphe: Cyber defense search engine (Requires an API key, see below.) - [https://www.onyphe.io/](https://www.onyphe.io/)
    
- otx: AlienVault open threat exchange - [https://otx.alienvault.com](https://otx.alienvault.com/)
    
- pentestTools: Cloud-based toolkit for offensive security testing, focused on web applications and network penetration  
    testing (Requires an API key, see below.) - [https://pentest-tools.com/](https://pentest-tools.com/)
    
- projecDiscovery: We actively collect and maintain internet-wide assets data, to enhance research and analyse changes around  
    DNS for better insights (Requires an API key, see below.) - [https://chaos.projectdiscovery.io](https://chaos.projectdiscovery.io/)
    
- rapiddns: DNS query tool which make querying subdomains or sites of a same IP easy! [https://rapiddns.io](https://rapiddns.io/)
    
- rocketreach: Access real-time verified personal/professional emails, phone numbers, and social media links (Requires an API key,  
    see below.) - [https://rocketreach.co](https://rocketreach.co/)
    
- securityTrails: Security Trails search engine, the world's largest repository of historical DNS data (Requires an API key, see  
    below.) - [https://securitytrails.com](https://securitytrails.com/)
    
- -s, --shodan: Shodan search engine will search for ports and banners from discovered hosts (Requires an API key, see below.)  
    [https://shodan.io](https://shodan.io/)
    
- sitedossier: Find available information on a site - [http://www.sitedossier.com](http://www.sitedossier.com/)
    
- subdomaincenter: A subdomain finder tool used to find subdomains of a given domain - [https://www.subdomain.center/](https://www.subdomain.center/)
    
- subdomainfinderc99: A subdomain finder is a tool used to find the subdomains of a given domain - [https://subdomainfinder.c99.nl](https://subdomainfinder.c99.nl/)
    
- threatminer: Data mining for threat intelligence - [https://www.threatminer.org/](https://www.threatminer.org/)
    
- tomba: Tomba search engine (Requires an API key, see below.) - [https://tomba.io](https://tomba.io/)
    
- urlscan: A sandbox for the web that is a URL and website scanner - [https://urlscan.io](https://urlscan.io/)
    
- vhost: Bing virtual hosts search
    
- virustotal: Domain search (Requires an API key, see below.) - [https://www.virustotal.com](https://www.virustotal.com/)
    
- yahoo: Yahoo search engine
    
- zoomeye: China's version of Shodan (Requires an API key, see below.) - [https://www.zoomeye.org](https://www.zoomeye.org/)
    

## Active modules:

[](https://github.com/laramies/theHarvester#active-modules)

- DNS brute force: dictionary brute force enumeration
- Screenshots: Take screenshots of subdomains that were found

## Modules that require an API key:

[](https://github.com/laramies/theHarvester#modules-that-require-an-api-key)

Documentation to setup API keys can be found at - [https://github.com/laramies/theHarvester/wiki/Installation#api-keys](https://github.com/laramies/theHarvester/wiki/Installation#api-keys)

- bevigil - Free upto 50 queries. Pricing can be found here: [https://bevigil.com/pricing/osint](https://bevigil.com/pricing/osint)
- binaryedge - $10/month
- bing
- bufferoverun - uses the free API
- censys - API keys are required and can be retrieved from your [Censys account](https://search.censys.io/account/api).
- criminalip
- fullhunt
- github
- hunter - limited to 10 on the free plan, so you will need to do -l 10 switch
- hunterhow
- intelx
- netlas - $
- onyphe -$
- pentestTools - $
- projecDiscovery - invite only for now
- rocketreach - $
- securityTrails
- shodan - $
- tomba - Free up to 50 search.
- zoomeye

## Install and dependencies:

[](https://github.com/laramies/theHarvester#install-and-dependencies)

- Python 3.10+
- [https://github.com/laramies/theHarvester/wiki/Installation](https://github.com/laramies/theHarvester/wiki/Installation)

## Comments, bugs, and requests:

[](https://github.com/laramies/theHarvester#comments-bugs-and-requests)

- [![Twitter Follow](https://camo.githubusercontent.com/40b7208719681b06186b721d47670c0bd0261e1b4dde4673510a0729b7d1affe/68747470733a2f2f696d672e736869656c64732e696f2f747769747465722f666f6c6c6f772f6c6172616d6965732e7376673f7374796c653d736f6369616c266c6162656c3d466f6c6c6f77)](https://twitter.com/laramies) Christian Martorella @laramies [cmartorella@edge-security.com](mailto:cmartorella@edge-security.com)
- [![Twitter Follow](https://camo.githubusercontent.com/45e348908392a2ab62e84928c47ee709e1032caf52f5460128e171625823b931/68747470733a2f2f696d672e736869656c64732e696f2f747769747465722f666f6c6c6f772f4e6f746f72696f7573526562656c312e7376673f7374796c653d736f6369616c266c6162656c3d466f6c6c6f77)](https://twitter.com/NotoriousRebel1) Matthew Brown @NotoriousRebel1
- [![Twitter Follow](https://camo.githubusercontent.com/82be2d344fe2e480adf91bc339531d3e1dc89c51565ed9f45d021b3ce7dba6cc/68747470733a2f2f696d672e736869656c64732e696f2f747769747465722f666f6c6c6f772f6a61795f746f776e73656e64312e7376673f7374796c653d736f6369616c266c6162656c3d466f6c6c6f77)](https://twitter.com/jay_townsend1) Jay "L1ghtn1ng" Townsend @jay_townsend1

## Main contributors:

[](https://github.com/laramies/theHarvester#main-contributors)

- [![Twitter Follow](https://camo.githubusercontent.com/45e348908392a2ab62e84928c47ee709e1032caf52f5460128e171625823b931/68747470733a2f2f696d672e736869656c64732e696f2f747769747465722f666f6c6c6f772f4e6f746f72696f7573526562656c312e7376673f7374796c653d736f6369616c266c6162656c3d466f6c6c6f77)](https://twitter.com/NotoriousRebel1) Matthew Brown @NotoriousRebel1
- [![Twitter Follow](https://camo.githubusercontent.com/82be2d344fe2e480adf91bc339531d3e1dc89c51565ed9f45d021b3ce7dba6cc/68747470733a2f2f696d672e736869656c64732e696f2f747769747465722f666f6c6c6f772f6a61795f746f776e73656e64312e7376673f7374796c653d736f6369616c266c6162656c3d466f6c6c6f77)](https://twitter.com/jay_townsend1) Jay "L1ghtn1ng" Townsend @jay_townsend1
- [![Twitter Follow](https://camo.githubusercontent.com/36c5e75e52e0ed018396bf1e36dfe1a2a936c85b309a3bd671dff888f7f2fdf3/68747470733a2f2f696d672e736869656c64732e696f2f747769747465722f666f6c6c6f772f646973636f766572736372697074732e7376673f7374796c653d736f6369616c266c6162656c3d466f6c6c6f77)](https://twitter.com/discoverscripts) Lee Baird @discoverscripts

## Thanks:

[](https://github.com/laramies/theHarvester#thanks)

- John Matherly - Shodan project
- Ahmed Aboul Ela - subdomain names dictionaries (big and small)

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/laramies/theHarvester). Be sure to check out the original post for more details.

# Tool Documentation:

## theharvester Usage Example

Search from email addresses from a domain (`-d kali.org`), limiting the results to 500 (`-l 500`), using DuckDuckGo (`-b duckduckgo`):

````console
root@kali:~# theHarvester -d kali.org -l 500 -b duckduckgo
*******************************************************************
*  _   _                                            _             *
* | |_| |__   ___    /\  /\__ _ _ ____   _____  ___| |_ ___ _ __  *
* | __|  _ \ / _ \  / /_/ / _` | '__\ \ / / _ \/ __| __/ _ \ '__| *
* | |_| | | |  __/ / __  / (_| | |   \ V /  __/\__ \ ||  __/ |    *
*  \__|_| |_|\___| \/ /_/ \__,_|_|    \_/ \___||___/\__\___|_|    *
*                                                                 *
* theHarvester 4.4.3                                              *
* Coded by Christian Martorella                                   *
* Edge-Security Research                                          *
* cmartorella@edge-security.com                                   *
*                                                                 *
*******************************************************************

[*] Target: kali.org

[*] Searching Duckduckgo.

[*] No IPs found.

[*] No emails found.

[*] Hosts found: 14
---------------------
[...]

```console
````

---

  

# Packages and Binaries:

### theharvester

The package contains a tool for gathering subdomain names, e-mail addresses, virtual hosts, open ports/ banners, and employee names from different public sources (search engines, pgp key servers).

**Installed size:** `1.81 MB`  
**How to install:** `sudo apt install theharvester`

Dependencies:

- kali-defaults
- python3
- python3-aiodns
- python3-aiofiles
- python3-aiohttp
- python3-aiomultiprocess
- python3-aiosqlite
- python3-bs4
- python3-censys
- python3-certifi
- python3-dateutil
- python3-dnspython
- python3-fastapi
- python3-lxml
- python3-netaddr
- python3-pkg-resources
- python3-playwright
- python3-requests
- python3-retrying
- python3-shodan
- python3-slowapi
- python3-starlette
- python3-ujson
- python3-uvicorn
- python3-uvloop
- python3-yaml

##### restfulHarvest

```console
root@kali:~# restfulHarvest -h
usage: restfulHarvest [-h] [-H HOST] [-p PORT] [-l LOG_LEVEL] [-r]

options:
  -h, --help            show this help message and exit
  -H HOST, --host HOST  IP address to listen on default is 127.0.0.1
  -p PORT, --port PORT  Port to bind the web server to, default is 5000
  -l LOG_LEVEL, --log-level LOG_LEVEL
                        Set logging level, default is info but
                        [critical|error|warning|info|debug|trace] can be set
  -r, --reload          Enable automatic reload used during development of the
                        api
```

---

##### theHarvester

```console
root@kali:~# theHarvester -h
Read proxies.yaml from /root/.theHarvester/proxies.yaml
*******************************************************************
*  _   _                                            _             *
* | |_| |__   ___    /\  /\__ _ _ ____   _____  ___| |_ ___ _ __  *
* | __|  _ \ / _ \  / /_/ / _` | '__\ \ / / _ \/ __| __/ _ \ '__| *
* | |_| | | |  __/ / __  / (_| | |   \ V /  __/\__ \ ||  __/ |    *
*  \__|_| |_|\___| \/ /_/ \__,_|_|    \_/ \___||___/\__\___|_|    *
*                                                                 *
* theHarvester 4.6.0                                              *
* Coded by Christian Martorella                                   *
* Edge-Security Research                                          *
* cmartorella@edge-security.com                                   *
*                                                                 *
*******************************************************************
usage: theHarvester [-h] -d DOMAIN [-l LIMIT] [-S START] [-p] [-s]
                    [--screenshot SCREENSHOT] [-v] [-e DNS_SERVER] [-t]
                    [-r [DNS_RESOLVE]] [-n] [-c] [-f FILENAME] [-b SOURCE]

theHarvester is used to gather open source intelligence (OSINT) on a company
or domain.

options:
  -h, --help            show this help message and exit
  -d DOMAIN, --domain DOMAIN
                        Company name or domain to search.
  -l LIMIT, --limit LIMIT
                        Limit the number of search results, default=500.
  -S START, --start START
                        Start with result number X, default=0.
  -p, --proxies         Use proxies for requests, enter proxies in
                        proxies.yaml.
  -s, --shodan          Use Shodan to query discovered hosts.
  --screenshot SCREENSHOT
                        Take screenshots of resolved domains specify output
                        directory: --screenshot output_directory
  -v, --virtual-host    Verify host name via DNS resolution and search for
                        virtual hosts.
  -e DNS_SERVER, --dns-server DNS_SERVER
                        DNS server to use for lookup.
  -t, --take-over       Check for takeovers.
  -r [DNS_RESOLVE], --dns-resolve [DNS_RESOLVE]
                        Perform DNS resolution on subdomains with a resolver
                        list or passed in resolvers, default False.
  -n, --dns-lookup      Enable DNS server lookup, default False.
  -c, --dns-brute       Perform a DNS brute force on the domain.
  -f FILENAME, --filename FILENAME
                        Save the results to an XML and JSON file.
  -b SOURCE, --source SOURCE
                        anubis, baidu, bevigil, binaryedge, bing, bingapi,
                        bufferoverun, brave, censys, certspotter, criminalip,
                        crtsh, dnsdumpster, duckduckgo, fullhunt, github-code,
                        hackertarget, hunter, hunterhow, intelx, netlas,
                        onyphe, otx, pentesttools, projectdiscovery, rapiddns,
                        rocketreach, securityTrails, sitedossier,
                        subdomaincenter, subdomainfinderc99, threatminer,
                        tomba, urlscan, virustotal, yahoo, zoomeye
```

---

##### theharvester

```console
root@kali:~# theharvester -h
┏━(Message from Kali developers)
┃
┃ The command theharvester is deprecated. Please use theHarvester instead.
┃
┗━
```

---

Updated on: 2024-May-23

**Credit:** This information was adapted from an excellent guide on [Kali.org](https://www.kali.org/tools/theharvester/). Be sure to check out the original post for more details.

# Lab 8 — Information Gathering using theHarvester


![](https://miro.medium.com/v2/resize:fit:683/1*40owL7RMZVehBBOh9-PQiQ.png)

> Please follow these labs to get hands-on experience for **_CompTIA Security+ exam [SY0–601]_**. All the labs use free tools. **_I STRONGLY_** suggest you use a virtual machine such as _VMware_ or _Virtualbox_ for these labs to avoid exposing your home PC or laptop. **_NEVER_** configure these labs at work using your employers’ PCs.

**Lab Objective:**

Learn how to gather information on a target site using theHarvester.

**Lab Purpose:**

Information gathering is often the first step of any penetration test. theHarvester is a very powerful OSINT (Open-Source Intelligence Tool) for finding information on a target URL. It searches multiple sites for information about the target URL and displays all the information it finds. It is particularly useful for finding names of people and their email addresses as well as subdomains of the target site.

**Lab Tool:**

Kali Linux

**Lab Topology:**

You can use either Kali Linux in a VM for this lab.

**Lab Walkthrough:**

# Task 1:

We can use theHarvester which is bundled in Kali, but this tool is updated frequently. We will download and use the latest version, in this lab.

To begin, boot up Kali Linux in your VM and open a terminal. Follow the steps below:

sudo apt-get install python3-pip  
sudo pip3 install virtualenv  
virtualenv venv

![](https://miro.medium.com/v2/resize:fit:700/0*4ycKpkXRbKCueTtW.png)

![](https://miro.medium.com/v2/resize:fit:409/0*0YX0YEBJYJ3PqEF3.png)

![](https://miro.medium.com/v2/resize:fit:457/0*UyCWFW_ZvGN76gkZ.png)

Clone the git repo:

git clone [https://github.com/laramies/theHarvester.git](https://github.com/laramies/theHarvester.git)  
cd theHarvester

![](https://miro.medium.com/v2/resize:fit:585/0*fi-D4OaoTMjGpXGU.png)

![](https://miro.medium.com/v2/resize:fit:429/0*A22KPdOOJoMUTMd_.png)

pip3 install -r requirements.txt

Close this terminal and open a new one. Now, we are ready to use “theHarvester.py” in “kali” user’s home directory. Type:

cd /home/kali/theHarvester/  
./theHarvester.py -v

![](https://miro.medium.com/v2/resize:fit:574/0*mjYjo9X1LHzF2454.png)

# Task 2:

To launch an information gathering campaign on a target, type the following:

./theHarvester.py -d hackaday.com -l 300 -b google

This will start theHarvester. It will begin searching Google for the top 300 results related to hackaday.com.

For this target, we could not find any information on Google. Let us dig deeper.

![](https://miro.medium.com/v2/resize:fit:346/0*iQSAzjYZrOIv4Woz.png)

![](https://miro.medium.com/v2/resize:fit:402/0*1iIchbM6sHMJwHu1.png)

# Task 3:

If we want to gather even more information about our target, we can specify the following:

./theHarvester.py -d hackaday.com \  
-l 300 -b all

The “-b all” tag will search all search engines available to theHarvester for information regarding hackaday.com. As you can see, it is an extremely useful tool for discovering email addresses, names of people associated with the target, sub-domain names and IP addresses.

![](https://miro.medium.com/v2/resize:fit:270/0*DYZVK_KRv2k3vPgm.png)

# Task 4:

If we wanted to display this information in an easier to read format, we could add the -f tag at the end:

./theHarvester.py -d hackaday.com -l 300 -b all -f hackaday.com.results

This will save the information gathered in a HTML file called “hackaday.com.results.html” When this file is opened, it provides the information gathered in a layout which is much easier to read.

![](https://miro.medium.com/v2/resize:fit:700/0*goe3x7qqhYaH_Wz3.png)

![](https://miro.medium.com/v2/resize:fit:700/0*wVqQhxxYjrAf6_NF.png)

**Credit:** This information was adapted from an excellent guide on [Medium](https://hassen-hannachi.medium.com/lab-8-information-gathering-using-theharvester-ce7f4b88c393). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Kq5r1zN31uA?si=o0WGrRJxJF0t92-c" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=Kq5r1zN31uA). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/s9QqH67P1q4?si=TjdIzizLni5sbN_o" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=s9QqH67P1q4). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/OOAiqaZCESY?si=GkWf1uVyMALBHjAC" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=OOAiqaZCESY). Be sure to check out the original post for more details.



