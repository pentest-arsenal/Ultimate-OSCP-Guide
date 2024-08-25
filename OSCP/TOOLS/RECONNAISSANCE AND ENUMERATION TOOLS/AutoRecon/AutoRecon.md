# AutoRecon

[](https://github.com/Tib3rius/AutoRecon#autorecon)

AutoRecon is a multi-threaded network reconnaissance tool which performs automated enumeration of services. It is intended as a time-saving tool for use in CTFs and other penetration testing environments (e.g. OSCP). It may also be useful in real-world engagements.

The tool works by firstly performing port scans / service detection scans. From those initial results, the tool will launch further enumeration scans of those services using a number of different tools. For example, if HTTP is found, feroxbuster will be launched (as well as many others).

Everything in the tool is highly configurable. The default configuration performs **no automated exploitation** to keep the tool in line with OSCP exam rules. If you wish to add automatic exploit tools to the configuration, you do so at your own risk. The author will not be held responsible for negative actions that result from the mis-use of this tool.

**Disclaimer: While AutoRecon endeavors to perform as much identification and enumeration of services as possible, there is no guarantee that every service will be identified, or that every service will be fully enumerated. Users of AutoRecon (especially students) should perform their own manual enumeration alongside AutoRecon. Do not rely on this tool alone for exams, CTFs, or other engagements.**

## Origin

[](https://github.com/Tib3rius/AutoRecon#origin)

AutoRecon was inspired by three tools which the author used during the OSCP labs: [Reconnoitre](https://github.com/codingo/Reconnoitre), [ReconScan](https://github.com/RoliSoft/ReconScan), and [bscan](https://github.com/welchbj/bscan). While all three tools were useful, none of the three alone had the functionality desired. AutoRecon combines the best features of the aforementioned tools while also implementing many new features to help testers with enumeration of multiple targets.

## Features

[](https://github.com/Tib3rius/AutoRecon#features)

- Supports multiple targets in the form of IP addresses, IP ranges (CIDR notation), and resolvable hostnames. IPv6 is also supported.
- Can scan multiple targets concurrently, utilizing multiple processors if they are available.
- Advanced plugin system allowing for easy creation of new scans.
- Customizable port scanning plugins for flexibility in your initial scans.
- Customizable service scanning plugins for further enumeration.
- Suggested manual follow-up commands for when automation makes little sense.
- Ability to limit port scanning to a combination of TCP/UDP ports.
- Ability to skip port scanning phase by supplying information about services which should be open.
- Global and per-scan pattern matching which highlights and extracts important information from the noise.
- An intuitive directory structure for results gathering.
- Full logging of commands that were run, along with errors if they fail.
- A powerful config file lets you use your favorite settings every time.
- A tagging system that lets you include or exclude certain plugins.
- Global and per-target timeouts in case you only have limited time.
- Four levels of verbosity, controllable by command-line options, and during scans using Up/Down arrows.
- Colorized output for distinguishing separate pieces of information. Can be turned off for accessibility reasons.

## Installation

[](https://github.com/Tib3rius/AutoRecon#installation)

There are three ways to install AutoRecon: pipx, pip, and manually. Before installation using any of these methods, certain requirements need to be fulfilled. If you have not refreshed your apt cache recently, run the following command so you are installing the latest available packages:

```shell
sudo apt update
```

### Python 3

[](https://github.com/Tib3rius/AutoRecon#python-3)

AutoRecon requires the usage of Python 3.8+ and pip, which can be installed on Kali Linux using the following commands:

```shell
sudo apt install python3
sudo apt install python3-pip
```

### Supporting Packages

[](https://github.com/Tib3rius/AutoRecon#supporting-packages)

Several commands used in AutoRecon reference the SecLists project, in the directory /usr/share/seclists/. You can either manually download the SecLists project to this directory ([https://github.com/danielmiessler/SecLists](https://github.com/danielmiessler/SecLists)), or if you are using Kali Linux (**highly recommended**) you can run the following commands:

```shell
sudo apt install seclists
```

AutoRecon will still run if you do not install SecLists, though several commands may fail, and some manual commands may not run either.

Additionally the following commands may need to be installed, depending on your OS:

```
curl
dnsrecon
enum4linux
feroxbuster
gobuster
impacket-scripts
nbtscan
nikto
nmap
onesixtyone
oscanner
redis-tools
smbclient
smbmap
snmpwalk
sslscan
svwar
tnscmd10g
whatweb
wkhtmltopdf
```

On Kali Linux, you can ensure these are all installed using the following commands:

```shell
sudo apt install seclists curl dnsrecon enum4linux feroxbuster gobuster impacket-scripts nbtscan nikto nmap onesixtyone oscanner redis-tools smbclient smbmap snmp sslscan sipvicious tnscmd10g whatweb wkhtmltopdf
```

### Installation Method #1: pipx (Recommended)

[](https://github.com/Tib3rius/AutoRecon#installation-method-1-pipx-recommended)

It is recommended you use `pipx` to install AutoRecon. pipx will install AutoRecon in it's own virtual environment, and make it available in the global context, avoiding conflicting package dependencies and the resulting instability. First, install pipx using the following commands:

```shell
sudo apt install python3-venv
python3 -m pip install --user pipx
python3 -m pipx ensurepath
```

You will have to re-source your ~/.bashrc or ~/.zshrc file (or open a new tab) after running these commands in order to use pipx.

Install AutoRecon using the following command:

```shell
pipx install git+https://github.com/Tib3rius/AutoRecon.git
```

Note that if you want to run AutoRecon using sudo (required for faster SYN scanning and UDP scanning), you have to use _one_ of the following examples:

```shell
sudo env "PATH=$PATH" autorecon [OPTIONS]
sudo $(which autorecon) [OPTIONS]
```

### Installation Method #2: pip

[](https://github.com/Tib3rius/AutoRecon#installation-method-2-pip)

Alternatively you can use `pip` to install AutoRecon using the following command:

```shell
python3 -m pip install git+https://github.com/Tib3rius/AutoRecon.git
```

Note that if you want to run AutoRecon using sudo (required for faster SYN scanning and UDP scanning), you will have to run the above command as the root user (or using sudo).

Similarly to `pipx`, if installed using `pip` you can run AutoRecon by simply executing `autorecon`.

### Installation Method #3: Manually

[](https://github.com/Tib3rius/AutoRecon#installation-method-3-manually)

If you'd prefer not to use `pip` or `pipx`, you can always still install and execute `autorecon.py` manually as a script. From within the AutoRecon directory, install the dependencies:

```shell
python3 -m pip install -r requirements.txt
```

You will then be able to run the `autorecon.py` script:

```shell
python3 autorecon.py [OPTIONS] 127.0.0.1
```

## Upgrading

[](https://github.com/Tib3rius/AutoRecon#upgrading)

### pipx

[](https://github.com/Tib3rius/AutoRecon#pipx)

Upgrading AutoRecon when it has been installed with pipx is the easiest, and is why the method is recommended. Simply run the following command:

```shell
pipx upgrade autorecon
```

### pip

[](https://github.com/Tib3rius/AutoRecon#pip)

If you've installed AutoRecon using pip, you will first have to uninstall AutoRecon and then re-install using the same install command:

```shell
python3 -m pip uninstall autorecon
python3 -m pip install git+https://github.com/Tib3rius/AutoRecon.git
```

### Manually

[](https://github.com/Tib3rius/AutoRecon#manually)

If you've installed AutoRecon manually, simply change to the AutoRecon directory and run the following command:

```shell
git pull
```

Assuming you did not modify any of the content in the AutoRecon directory, this should pull the latest code from this GitHub repo, after which you can run AutoRecon using the autorecon.py script as per usual.

### Plugins

[](https://github.com/Tib3rius/AutoRecon#plugins)

A plugin update process is in the works. Until then, after upgrading, remove the ~/.local/share/AutoRecon directory and run AutoRecon with any argument to repopulate with the latest files.

## Usage

[](https://github.com/Tib3rius/AutoRecon#usage)

AutoRecon uses Python 3 specific functionality and does not support Python 2.

```
usage: autorecon [-t TARGET_FILE] [-p PORTS] [-m MAX_SCANS] [-mp MAX_PORT_SCANS] [-c CONFIG_FILE] [-g GLOBAL_FILE] [--tags TAGS]
                 [--exclude-tags TAGS] [--port-scans PLUGINS] [--service-scans PLUGINS] [--reports PLUGINS] [--plugins-dir PLUGINS_DIR]
                 [--add-plugins-dir PLUGINS_DIR] [-l [TYPE]] [-o OUTPUT] [--single-target] [--only-scans-dir] [--no-port-dirs]
                 [--heartbeat HEARTBEAT] [--timeout TIMEOUT] [--target-timeout TARGET_TIMEOUT] [--nmap NMAP | --nmap-append NMAP_APPEND]
                 [--proxychains] [--disable-sanity-checks] [--disable-keyboard-control] [--force-services SERVICE [SERVICE ...]] [--accessible]
                 [-v] [--version] [--curl.path VALUE] [--dirbuster.tool {feroxbuster,gobuster,dirsearch,ffuf,dirb}]
                 [--dirbuster.wordlist VALUE [VALUE ...]] [--dirbuster.threads VALUE] [--dirbuster.ext VALUE]
                 [--onesixtyone.community-strings VALUE] [--global.username-wordlist VALUE] [--global.password-wordlist VALUE]
                 [--global.domain VALUE] [-h]
                 [targets ...]

Network reconnaissance tool to port scan and automatically enumerate services found on multiple targets.

positional arguments:
  targets               IP addresses (e.g. 10.0.0.1), CIDR notation (e.g. 10.0.0.1/24), or resolvable hostnames (e.g. foo.bar) to scan.

optional arguments:
  -t TARGET_FILE, --target-file TARGET_FILE
                        Read targets from file.
  -p PORTS, --ports PORTS
                        Comma separated list of ports / port ranges to scan. Specify TCP/UDP ports by prepending list with T:/U: To scan both
                        TCP/UDP, put port(s) at start or specify B: e.g. 53,T:21-25,80,U:123,B:123. Default: None
  -m MAX_SCANS, --max-scans MAX_SCANS
                        The maximum number of concurrent scans to run. Default: 50
  -mp MAX_PORT_SCANS, --max-port-scans MAX_PORT_SCANS
                        The maximum number of concurrent port scans to run. Default: 10 (approx 20% of max-scans unless specified)
  -c CONFIG_FILE, --config CONFIG_FILE
                        Location of AutoRecon's config file. Default: ~/.config/AutoRecon/config.toml
  -g GLOBAL_FILE, --global-file GLOBAL_FILE
                        Location of AutoRecon's global file. Default: ~/.config/AutoRecon/global.toml
  --tags TAGS           Tags to determine which plugins should be included. Separate tags by a plus symbol (+) to group tags together. Separate
                        groups with a comma (,) to create multiple groups. For a plugin to be included, it must have all the tags specified in
                        at least one group. Default: default
  --exclude-tags TAGS   Tags to determine which plugins should be excluded. Separate tags by a plus symbol (+) to group tags together. Separate
                        groups with a comma (,) to create multiple groups. For a plugin to be excluded, it must have all the tags specified in
                        at least one group. Default: None
  --port-scans PLUGINS  Override --tags / --exclude-tags for the listed PortScan plugins (comma separated). Default: None
  --service-scans PLUGINS
                        Override --tags / --exclude-tags for the listed ServiceScan plugins (comma separated). Default: None
  --reports PLUGINS     Override --tags / --exclude-tags for the listed Report plugins (comma separated). Default: None
  --plugins-dir PLUGINS_DIR
                        The location of the plugins directory. Default: ~/.local/share/AutoRecon/plugins
  --add-plugins-dir PLUGINS_DIR
                        The location of an additional plugins directory to add to the main one. Default: None
  -l [TYPE], --list [TYPE]
                        List all plugins or plugins of a specific type. e.g. --list, --list port, --list service
  -o OUTPUT, --output OUTPUT
                        The output directory for results. Default: results
  --single-target       Only scan a single target. A directory named after the target will not be created. Instead, the directory structure will
                        be created within the output directory. Default: False
  --only-scans-dir      Only create the "scans" directory for results. Other directories (e.g. exploit, loot, report) will not be created.
                        Default: False
  --no-port-dirs        Don't create directories for ports (e.g. scans/tcp80, scans/udp53). Instead store all results in the "scans" directory
                        itself. Default: False
  --heartbeat HEARTBEAT
                        Specifies the heartbeat interval (in seconds) for scan status messages. Default: 60
  --timeout TIMEOUT     Specifies the maximum amount of time in minutes that AutoRecon should run for. Default: None
  --target-timeout TARGET_TIMEOUT
                        Specifies the maximum amount of time in minutes that a target should be scanned for before abandoning it and moving on.
                        Default: None
  --nmap NMAP           Override the {nmap_extra} variable in scans. Default: -vv --reason -Pn -T4
  --nmap-append NMAP_APPEND
                        Append to the default {nmap_extra} variable in scans. Default:
  --proxychains         Use if you are running AutoRecon via proxychains. Default: False
  --disable-sanity-checks
                        Disable sanity checks that would otherwise prevent the scans from running. Default: False
  --disable-keyboard-control
                        Disables keyboard control ([s]tatus, Up, Down) if you are in SSH or Docker.
  --force-services SERVICE [SERVICE ...]
                        A space separated list of services in the following style: tcp/80/http tcp/443/https/secure
  --accessible          Attempts to make AutoRecon output more accessible to screenreaders. Default: False
  -v, --verbose         Enable verbose output. Repeat for more verbosity.
  --version             Prints the AutoRecon version and exits.
  -h, --help            Show this help message and exit.

plugin arguments:
  These are optional arguments for certain plugins.

  --curl.path VALUE     The path on the web server to curl. Default: /
  --dirbuster.tool {feroxbuster,gobuster,dirsearch,ffuf,dirb}
                        The tool to use for directory busting. Default: feroxbuster
  --dirbuster.wordlist VALUE [VALUE ...]
                        The wordlist(s) to use when directory busting. Separate multiple wordlists with spaces. Default:
                        ['~/.local/share/AutoRecon/wordlists/dirbuster.txt']
  --dirbuster.threads VALUE
                        The number of threads to use when directory busting. Default: 10
  --dirbuster.ext VALUE
                        The extensions you wish to fuzz (no dot, comma separated). Default: txt,html,php,asp,aspx,jsp
  --onesixtyone.community-strings VALUE
                        The file containing a list of community strings to try. Default: /usr/share/seclists/Discovery/SNMP/common-snmp-
                        community-strings-onesixtyone.txt

global plugin arguments:
  These are optional arguments that can be used by all plugins.

  --global.username-wordlist VALUE
                        A wordlist of usernames, useful for bruteforcing. Default: /usr/share/seclists/Usernames/top-usernames-shortlist.txt
  --global.password-wordlist VALUE
                        A wordlist of passwords, useful for bruteforcing. Default: /usr/share/seclists/Passwords/darkweb2017-top100.txt
  --global.domain VALUE
                        The domain to use (if known). Used for DNS and/or Active Directory. Default: None
```

### Verbosity

[](https://github.com/Tib3rius/AutoRecon#verbosity)

AutoRecon supports four levels of verbosity:

- (none) Minimal output. AutoRecon will announce when scanning targets starts / ends.
- (-v) Verbose output. AutoRecon will additionally announce when plugins start running, and report open ports and identified services.
- (-vv) Very verbose output. AutoRecon will additionally specify the exact commands which are being run by plugins, highlight any patterns which are matched in command output, and announce when plugins end.
- (-vvv) Very, very verbose output. AutoRecon will output everything. Literally every line from all commands which are currently running. When scanning multiple targets concurrently, this can lead to a ridiculous amount of output. It is not advised to use -vvv unless you absolutely need to see live output from commands.

Note: You can change the verbosity of AutoRecon mid-scan by pressing the up and down arrow keys.

### Results

[](https://github.com/Tib3rius/AutoRecon#results)

By default, results will be stored in the ./results directory. A new sub directory is created for every target. The structure of this sub directory is:

```
.
├── exploit/
├── loot/
├── report/
│   ├── local.txt
│   ├── notes.txt
│   ├── proof.txt
│   └── screenshots/
└── scans/
	├── _commands.log
	├── _manual_commands.txt
	├── tcp80/
	├── udp53/
	└── xml/
```

The exploit directory is intended to contain any exploit code you download / write for the target.

The loot directory is intended to contain any loot (e.g. hashes, interesting files) you find on the target.

The report directory contains some auto-generated files and directories that are useful for reporting:

- local.txt can be used to store the local.txt flag found on targets.
- notes.txt should contain a basic template where you can write notes for each service discovered.
- proof.txt can be used to store the proof.txt flag found on targets.
- The screenshots directory is intended to contain the screenshots you use to document the exploitation of the target.

The scans directory is where all results from scans performed by AutoRecon will go. This includes port scans / service detection scans, as well as any service enumeration scans. It also contains two other files:

- _commands.log contains a list of every command AutoRecon ran against the target. This is useful if one of the commands fails and you want to run it again with modifications.
- _manual_commands.txt contains any commands that are deemed "too dangerous" to run automatically, either because they are too intrusive, require modification based on human analysis, or just work better when there is a human monitoring them.

By default, directories are created for each open port (e.g. tcp80, udp53) and scan results for the services found on those ports are stored in their respective directories. You can disable this behavior using the --no-port-dirs command line option, and scan results will instead be stored in the scans directory itself.

If a scan results in an error, a file called _errors.log will also appear in the scans directory with some details to alert the user.

If output matches a defined pattern, a file called _patterns.log will also appear in the scans directory with details about the matched output.

The scans/xml directory stores any XML output (e.g. from Nmap scans) separately from the main scan outputs, so that the scans directory itself does not get too cluttered.

## Testimonials

[](https://github.com/Tib3rius/AutoRecon#testimonials)

> AutoRecon was invaluable during my OSCP exam, in that it saved me from the tedium of executing my active information gathering commands myself. I was able to start on a target with all of the information I needed clearly laid in front of me. I would strongly recommend this utility for anyone in the PWK labs, the OSCP exam, or other environments such as VulnHub or HTB. It is a great tool for both people just starting down their journey into OffSec and seasoned veterans alike. Just make sure that somewhere between those two points you take the time to learn what's going on "under the hood" and how / why it scans what it does.
> 
> - b0ats (rooted 5/5 exam hosts)

> Wow, what a great find! Before using AutoRecon, ReconScan was my goto enumeration script for targets because it automatically ran the enumeration commands after it finds open ports. The only thing missing was the automatic creation of key directories a pentester might need during an engagement (exploit, loot, report, scans). Reconnoitre did this but didn't automatically run those commands for you. I thought ReconScan that was the bee's knees until I gave AutoRecon a try. It's awesome! It combines the best features of Reconnoitre (auto directory creation) and ReconScan (automatically executing the enumeration commands). All I have to do is run it on a target or a set of targets and start going over the information it has already collected while it continues the rest of scan. The proof is in the pudding :) Passed the OSCP exam! Kudos to Tib3rius!
> 
> - werk0ut

> A friend told me about AutoRecon, so I gave it a try in the PWK labs. AutoRecon launches the common tools we all always use, whether it be nmap or nikto, and also creates a nice subfolder system based on the targets you are attacking. The strongest feature of AutoRecon is the speed; on the OSCP exam I left the tool running in the background while I started with another target, and in a matter of minutes I had all of the AutoRecon output waiting for me. AutoRecon creates a file full of commands that you should try manually, some of which may require tweaking (for example, hydra bruteforcing commands). It's good to have that extra checklist.
> 
> - tr3mb0 (rooted 4/5 exam hosts)

> Being introduced to AutoRecon was a complete game changer for me while taking the OSCP and establishing my penetration testing methodology. AutoRecon is a multi-threaded reconnaissance tool that combines and automates popular enumeration tools to do most of the hard work for you. You can't get much better than that! After running AutoRecon on my OSCP exam hosts, I was given a treasure chest full of information that helped me to start on each host and pass on my first try. The best part of the tool is that it automatically launches further enumeration scans based on the initial port scans (e.g. run enum4linux if SMB is detected). The only bad part is that I did not use this tool sooner! Thanks Tib3rius.
> 
> - rufy (rooted 4/5 exam hosts)

> AutoRecon allows a security researcher to iteratively scan hosts and identify potential attack vectors. Its true power comes in the form of performing scans in the background while the attacker is working on another host. I was able to start my scans and finish a specific host I was working on - and then return to find all relevant scans completed. I was then able to immediately begin trying to gain initial access instead of manually performing the active scanning process. I will continue to use AutoRecon in future penetration tests and CTFs, and highly recommend you do the same.
> 
> - waar (rooted 4.99/5 exam hosts)

> "If you have to do a task more than twice a day, you need to automate it." That's a piece of advice that an old boss gave to me. AutoRecon takes that lesson to heart. Whether you're sitting in the exam, or in the PWK labs, you can fire off AutoRecon and let it work its magic. I had it running during my last exam while I worked on the buffer overflow. By the time I finished, all the enum data I needed was there for me to go through. 10/10 would recommend for anyone getting into CTF, and anyone who has been at this a long time.
> 
> - whoisflynn

> I love this tool so much I wrote it.
> 
> - Tib3rius (rooted 5/5 exam hosts)

> I highly recommend anyone going for their OSCP, doing CTFs or on HTB to checkout this tool. Been using AutoRecon on HTB for a month before using it over on the PWK labs and it helped me pass my OSCP exam. If you're having a hard time getting settled with an enumeration methodology I encourage you to follow the flow and techniques this script uses. It takes out a lot of the tedious work that you're probably used to while at the same time provide well-organized subdirectories to quickly look over so you don't lose your head. The manual commands it provides are great for those specific situations that need it when you have run out of options. It's a very valuable tool, cannot recommend enough.
> 
> - d0hnuts (rooted 5/5 exam hosts)

> Autorecon is not just any other tool, it is a recon correlation framweork for engagements. This helped me fire a whole bunch of scans while I was working on other targets. This can help a lot in time management. This assisted me to own 4/5 boxes in pwk exam! Result: Passed!
> 
> - Wh0ami (rooted 4/5 exam hosts)

> The first time I heard of AutoRecon I asked whether I actually needed this, my enumeration was OK... I tried it with an open mind and straight away was a little floored on the amount of information that it would generate. Once I got used to it, and started reading the output I realized how much I was missing. I used it for the OSCP exam, and it found things I would never have otherwise found. I firmly believe, without AutoRecon I would have failed. It's a great tool, and I'm very impressed what Tib3rius was able to craft up. Definitely something I'm already recommending to others, including you!
> 
> - othornew

> AutoRecon helped me save valuable time in my OSCP exam, allowing me to spend less time scanning systems and more time breaking into them. This software is worth its weight in gold!
> 
> - TorHackr

> The magical tool that made enumeration a piece of cake, just fire it up and watch the beauty of multi-threading spitting a ton of information that would have taken loads of commands to execute. I certainly believe that by just using AutoRecon in the OSCP exam, half of the effort would already be done. Strongly recommended!
> 
> - Arman (solved 4.5/5 exam hosts)

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/Tib3rius/AutoRecon). Be sure to check out the original post for more details.

# AutoRecon: A Multi-Threaded Network Reconnaissance Tool

Reading time: 5 minutes

[Facebook](https://www.facebook.com/sharer/sharer.php?u=http%3A%2F%2Fsecuritytrails.com%2Fblog%2Fautorecon)[Twitter](https://twitter.com/intent/tweet?url=https://securitytrails.com/blog/autorecon&text=Share%20this%20blog%20post%20on%20Twitter:)[LinkedIn](https://www.linkedin.com/shareArticle?mini=true&url=https://securitytrails.com/blog/autorecon&title=AutoRecon:%20A%20Multi-Threaded%20Network%20Reconnaissance%20Toolsummary=&source=SecurityTrails)

![Listen to this article](https://assets.securitytrails.com/cdn-cgi/image/quality=100,format=auto,fit=contain,width=auto/dist/temp/image/page/audio-bck.png)

With organizations' digital footprints growing larger and larger, network [recon](https://securitytrails.com/blog/the-most-misunderstood-element-recon "The Most Misunderstood Element: Recon") and the enumeration of services available over the public internet has become a critical area in the security of an organization. And given the increased number of vulnerabilities and threats targeting web applications, performing automated recon and service enumeration is ever more important.

Fortunately, using open-source and free-to-use tools such as [recon-ng](https://securitytrails.com/blog/recon-ng "Recon-ng: An Open Source Reconnaissance Tool") has streamlined this process to the point of near-automation.

Today we'll take a look at AutoRecon, aimed at doing just that: automating your network recon and service enumeration methods.

- [What is AutoRecon?](https://securitytrails.com/blog/autorecon#content-what-is-autorecon)
- [Installing AutoRecon](https://securitytrails.com/blog/autorecon#content-installing-autorecon)
- [Usage](https://securitytrails.com/blog/autorecon#content-usage)
- [Analyzing the results](https://securitytrails.com/blog/autorecon#content-analyzing-the-results)
- [Further understanding the results](https://securitytrails.com/blog/autorecon#content-further-understanding-the-results)
    - [Finding the webserver version](https://securitytrails.com/blog/autorecon#content-finding-the-webserver-version)
    - [Detecting operating systems](https://securitytrails.com/blog/autorecon#content-detecting-operating-systems)
    - [Gathering screenshots along the way](https://securitytrails.com/blog/autorecon#content-gathering-screenshots-along-the-way)
- [Summary](https://securitytrails.com/blog/autorecon#content-summary)

## [¶](https://securitytrails.com/blog/autorecon#content-what-is-autorecon "Permalink")What is AutoRecon?

AutoRecon is an [open-source project](https://github.com/Tib3rius/AutoRecon) built to perform network reconnaissance with automated service enumeration.

The advantage that AutoRecon provides over other [information gathering](https://securitytrails.com/blog/information-gathering "Information Gathering: Concept, Techniques and Tools explained") and [internet scanning](https://securitytrails.com/blog/internet-scanning "Internet Scanning: Definition, Benefits, Brief History and Tools") tools is that it allows one to further process—and further act upon—information gathered directly within AutoRecon. This includes performing actions like Nmap as well as running the gathered data through other scanning tools, such as feroxbuster, sslscan, nbtscan, [Nikto](https://securitytrails.com/blog/nikto-website-vulnerability-scanner "Nikto: A Practical Website Vulnerability Scanner") and more.

Take your recon to the next levelDiscover how SurfaceBrowser™ can unveil IP blocks, subdomains,  
open ports, and SSL certificates from any company[BOOK A DEMO NOW](https://securitytrails.com/corp/surfacebrowser)

## [¶](https://securitytrails.com/blog/autorecon#content-installing-autorecon "Permalink")Installing AutoRecon

_Note: As its dependencies are easily available on KaliLinux, we suggest using AutoRecon on that distribution._

To begin with, ensure you have python3 and pip available.

Next, use Python pip to grab the latest version of AutoRecon and install it:

```nginx
sudo python3 -m pip install git+https://github.com/Tib3rius/AutoRecon.git
```

Next, you'll need to install certain dependencies:

```nginx
sudo apt install seclists curl enum4linux feroxbuster impacket-scripts nbtscan nikto nmap onesixtyone oscanner redis-tools smbclient smbmap snmp sslscan sipvicious tnscmd10g whatweb wkhtmltopdf
```

Run the command _autorecon --help_ to determine whether it's been successfully installed:

```bash
autorecon --help
```

Which should then give you the following output containing various options available in AutoRecon:

![Autorecon options](https://assets.securitytrails.com/cdn-cgi/image/width=763,quality=100,format=auto/blog/autorecon/autorecon-options.png "Autorecon options")

## [¶](https://securitytrails.com/blog/autorecon#content-usage "Permalink")Usage

Getting started with AutoRecon is super simple—one can even run AutoRecon without any flags or options:

```nginx
autorecon domain.com
```

Replace _domain.com_ with a domain name that you wish to scan.

Once the command has finished executing, it should then return the following output:

![Autorecon usage](https://assets.securitytrails.com/cdn-cgi/image/width=763,quality=100,format=auto/blog/autorecon/autorecon-usage.png "Autorecon usage")

## [¶](https://securitytrails.com/blog/autorecon#content-analyzing-the-results "Permalink")Analyzing the results

After a scan completes, AutoRecon saves the scan results in the "results" directory, inside of which a new subdirectory is created for every target being scanned by AutoRecon.

The results structure created by AutoRecon is as shown below:

```nginx
results

└── domain-name.here

├── exploit

├── loot

├── report

│ ├── local.txt

│ ├── notes.txt

│ ├── proof.txt

│ ├── report.md

│ │ └── domain-name.here

│ │ ├── Commands.md

│ │ ├── Errors.md

│ │ ├── Manual Commands.md

│ │ ├── Patterns.md

│ │ ├── Port Scans

│ │ │ ├── PortScan - All TCP Ports.md

│ │ │ ├── PortScan - Top 100 UDP Ports.md

│ │ │ └── PortScan - Top TCP Ports.md

│ │ └── Services

│ │ ├── Service - tcp-22-ssh

│ │ │ └── Nmap SSH.md

│ │ ├── Service - tcp-443-http

│ │ │ ├── Curl.md

│ │ │ ├── Curl Robots.md

│ │ │ ├── Directory Buster.md

│ │ │ ├── Nmap HTTP.md

│ │ │ ├── SSL Scan.md

│ │ │ ├── whatweb.md

│ │ │ └── wkhtmltoimage.md

│ │ └── Service - tcp-80-http

│ │ ├── Curl.md

│ │ ├── Curl Robots.md

│ │ ├── Directory Buster.md

│ │ ├── Nmap HTTP.md

│ │ ├── whatweb.md

│ │ └── wkhtmltoimage.md

│ └── screenshots

└── scans

├── _commands.log

├── _errors.log

├── _full_tcp_nmap.txt

├── _manual_commands.txt

├── _patterns.log

├── _quick_tcp_nmap.txt

├── tcp22

│ ├── tcp_22_ssh_nmap.txt

│ └── xml

│ └── tcp_22_ssh_nmap.xml

├── tcp443

│ ├── tcp_443_https_curl.html

│ ├── tcp_443_https_feroxbuster_big.txt

│ ├── tcp_443_https_feroxbuster_common.txt

│ ├── tcp_443_https_feroxbuster_raft-large-words.txt

│ ├── tcp_443_https_nmap.txt

│ ├── tcp_443_https_screenshot.png

│ ├── tcp_443_https_whatweb.txt

│ ├── tcp_443_sslscan.html

│ └── xml

│ └── tcp_443_https_nmap.xml

├── tcp80

│ ├── tcp_80_http_curl.html

│ ├── tcp_80_http_curl-robots.txt

│ ├── tcp_80_http_feroxbuster_big.txt

│ ├── tcp_80_http_feroxbuster_common.txt

│ ├── tcp_80_http_feroxbuster_raft-large-words.txt

│ ├── tcp_80_http_nmap.txt

│ ├── tcp_80_http_screenshot.png

│ ├── tcp_80_http_whatweb.txt

│ └── xml

│ └── tcp_80_http_nmap.xml

├── _top_100_udp_nmap.txt

└── xml

├── _full_tcp_nmap.xml

├── _quick_tcp_nmap.xml

└── _top_100_udp_nmap.xml

```

- The exploit directory is used to store any exploit code you run for the target being scanned.
- The loot directory is intended to store any hashes or notable files you find on the target you're scanning.
- The report directory contains reports of the scan performed by AutoRecon; files are generated as follows:
    - local.txt can be used to store the local.txt flag found on targets.
    - notes.txt should contain a basic template where you can write notes for each service discovered.
    - proof.txt can be used to store the proof.txt flag found on the target.
- The screenshots directory is used to store any screenshots you use to document the exploitation of the target.
- The scans directory is where all results from scans performed by AutoRecon will go. This includes all commands executed by AutoRecon and whether any commands failed or succeeded as well.
- The scans/XML directory stores scan data results in XML format (from [Nmap](https://securitytrails.com/blog/nmap-commands "Top 16 Nmap Commands to Scan Remote Hosts - Tutorial Guide"), etc.) which can be used to easily import scan results data into other software for further processing or storing.

## [¶](https://securitytrails.com/blog/autorecon#content-further-understanding-the-results "Permalink")Further understanding the results

### [¶](https://securitytrails.com/blog/autorecon#content-finding-the-webserver-version "Permalink")Finding the webserver version

With the output we gather from AutoRecon, one can find the version of the webserver running on the target system as well. Most web servers expose their name and version by default; for example, from the Nmap output:

```nginx
PORT STATE SERVICE REASON VERSION

80/tcp open http syn-ack ttl 55 nginx 1.14.0 (Ubuntu)
```

This tells us the webserver running on the target being scanned is Nginx 1.14.0.

### [¶](https://securitytrails.com/blog/autorecon#content-detecting-operating-systems "Permalink")Detecting operating systems

Looking even further with the output we've gathered above, the webserver often exposes the operating system or operating system family, too. Also, as shown above, we can see the target being scanned runs on Ubuntu.

### [¶](https://securitytrails.com/blog/autorecon#content-gathering-screenshots-along-the-way "Permalink")Gathering screenshots along the way

Often, web application screenshots can tell a lot—they can expose/display errors, find web applications running on non-standard ports, show outdated running web applications, and more. AutoRecon gathers screenshots for any ports it discovers along the way.

These screenshots can be found under the path: _results/DOMAIN.NAME/scans/tcpPORT_

This allows one to efficiently streamline their process. Usually, one would identify [open ports](https://securitytrails.com/blog/open-ports "What are Open Ports?"), then run through another tool to gather screenshots. AutoRecon, however, does this for you automatically.

## [¶](https://securitytrails.com/blog/autorecon#content-summary "Permalink")Summary

AutoRecon proves to be an excellent tool for performing network reconnaissance with the automated enumeration of services. Combined with its ability to further process gathered data with other useful tools including feroxbuster, sslscan, nbtscan, and Nikto, the number of use cases for AutoRecon increases greatly.

AutoRecon also provides scan results data in the XML format, allowing for scan results to be processed to a greater extent while making logging into databases even simpler.

**Credit:** This information was adapted from an excellent guide on [SecurityTrails](https://securitytrails.com/blog/autorecon). Be sure to check out the original post for more details.

# Comprehensive Guide to AutoRecon

[March 24, 2021](https://www.hackingarticles.in/comprehensive-guide-to-autorecon/) by [Raj](https://www.hackingarticles.in/author/raj/)

The AutoRecon tool is designed as a network reconnaissance tool. It is a multi-threaded tool that performs automated enumeration of services. The purpose of this tool is to save time while cracking CTFs and other penetration testing environments or exams. It is useful in real-world engagements as well.

### **Table of Contents**

- **Introduction**
- **Features**
- **Installation**
- **Usage**
    - Multi-Target Scan
    - Concurrent Scan
    - Single Target Argument
    - Heartbeat Argument
    - Nmap Arguments
    - Verbosity Scans
- **Results**
    - Enum4Linux Scan
    - SMTP Scan
    - WhatWeb Scan
    - XML Results
    - Nikto Scan
    - Web Services Screenshots

### **Introduction**

The AutoRecon works in a sequential process. Initially, it performs port scans or service detection scans. Then using the results of these scans as a reference it further launches enumeration scans of those services using other tools. For example, if HTTP is found, it will check for webpages and if it will get those, it will start Nikto scan with go buster and other tools concurrently.

The tool itself is designed to be personalized by making changes in the configuration files.

**Author: [Tib3rius](https://twitter.com/0xtib3rius?lang=en)**

**GitHub: [Tib3rius/AutoRecon](https://github.com/Tib3rius/AutoRecon)**

### **Features**

- It uses pattern matching to increase the speed and accuracy in results.
- It logs all the commands that it executes so that the user can check in case of errors.
- It supports multiple targets at once. It uses IP Addresses, or IP Ranges and resolvable hostname.
- It supports customizable enumerations on different services.

### **Installation**

There are multiple methods to install AutoRecon. Users can run it on a Docker Instance. It can be used by a small fraction of people that don’t use Kali Linux or any other Linux Distribution. To install using Docker please refer to the GitHub page of the AutoRecon. We are focusing on the installation methods with pipx. It is the recommended method by the developer of the tool and it works like charm. Before Beginning the Installation there are a few requirements in order to run AutoRecon. The AutoRecon is build on Python 3. It will not run-on Python 2. This is because it uses a library called asyncio which is not supported in earlier versions. If you don’t already have it installed, you can do it by running the following commands as root. We are installing the pip for python3 as well to install any additional packages.

apt install python3
apt install python3-pip

After this we will use pipx, to manage the python packages; This will take the packages that we install and put them inside their own virtual environment. This will avoid any conflicting packages inside your machine. First, we will be installing the Virtual Environment using Python3.

apt install python3-venv

![](https://1.bp.blogspot.com/-D94VX4p7GaM/YFtSmu5PwRI/AAAAAAAAu8I/siZ-JZv_u5UJiGMXK-gz5ewcMv7b_yRGACLcBGAsYHQ/s16000/1.png)

Now we will download the pipx using python3-pip

python3 -m pip install --user pipx

![](https://1.bp.blogspot.com/-ZTzjUXg0ODI/YFtSs7FPk-I/AAAAAAAAu8M/8usQClm43KMz40pKsv68mRNVZDI6vqAQgCLcBGAsYHQ/s16000/2.png)

Now we will make changes to the PATH Variables to add pipx. After completion, we will need to reopen the terminal so that it can take effect.

python3 -m pipx ensurepath

![](https://1.bp.blogspot.com/-pBQKkO_Gd5g/YFtSyHQT35I/AAAAAAAAu8Q/0NAjoKPwRl4dhVFHDRxgeTMFIQiuzaMMQCLcBGAsYHQ/s16000/3.png)

AutoRecon takes a lot of different tools and runs them on the target defined by the user. Although most of the tools are present in Kali itself let’s install or update those tools to use AutoRecon in its full glory. As the seclists is quite large in size more like 386 Megabytes so that is going to take some time.

The list of tools that required are:

- curl
- enum4linux
- gobuster
- nbtscan
- Nikto
- nmap
- onesixtyone
- oscanner
- smbclient
- SMBMap
- smtp-user-enum
- SNMP walk
- sslscan
- svwar
- tnscmd10g
- whatweb
- wkhtmltoimage

The command to install or update these tools is mentioned below:

apt install seclists curl enum4linux gobuster nbtscan nikto nmap onesixtyone oscanner smbclient smbmap smtp-user-enum snmp sslscan sipvicious tnscmd10g whatweb wkhtmltopdf

![](https://1.bp.blogspot.com/-HyoRo36Ed1w/YFtS4I5l57I/AAAAAAAAu8Y/wK40FKF7Uf8gB23hiDGeTnl44OquxxCEACLcBGAsYHQ/s16000/4.png)

Now that all the pre-requisites are installed, all that is needed to do is install the AutoRecon directly from its GitHub Repository using pipx. Very simple syntax to use as it can be observed. 

pipx install git+https://github.com/Tib3rius/AutoRecon.git

![](https://1.bp.blogspot.com/-s2hj8oGyC48/YFtS9DzPZaI/AAAAAAAAu8g/vCGOJOKuq6EFgqNwKnCgh7fezXbl8bKBgCLcBGAsYHQ/s16000/5.png)

### **Usage**

As discussed earlier, AutoRecon is an Enumeration tool. It requires a target or a set of targets. This can be IP Addresses, or CIDR Notations or hostnames as well. When triggered with the -h parameter it shows the user a help screen as depicted in the image below. It tells us that we can provide a target directly or if you have multiple targets. Then you can put the target IP Addresses into a file and then pass it as a parameter with the -t flag.

autorecon -h

![](https://1.bp.blogspot.com/-c0ukQMuB3ok/YFtTBYj0xLI/AAAAAAAAu8k/PQgOQq9K5Ksh55wc3TZnD1cRd5GcUSQUgCLcBGAsYHQ/s16000/6.png)

As we saw earlier that AutoRecon has a large number of parameters but most of these can be left default. The key thing to remember is the required argument “target”. It can be a space-separated list of either IP Addresses or CIDR Notations or even resolvable hostnames. We can also create a file with the targets in it. It should be in the format of one per new line. We need to reference that target file using the -t argument.

autorecon 192.168.126.132

![](https://1.bp.blogspot.com/--S72-0-p58o/YFtTFbT0PwI/AAAAAAAAu8o/XEh_EgdkVcQfF11A1zpMcDPn6exx_UnpQCLcBGAsYHQ/s16000/7.png)

### **Multi-Target Scan**

By default, AutoRecon will scan 5 target hosts at the same time but that number can be toggled using the -ct parameter. This is basically the number of targets getting scanned at the same time. To demonstrate, we collected some IP Address in the network and then entered them into a text file. Then used that text file to provide targets to AutoRecon.

cat target.txt
autorecon -t targets.txt

![](https://1.bp.blogspot.com/-wfXbq8UoRxY/YFtTJJJO4EI/AAAAAAAAu8w/OVCziimImWAi40iR1ToZAHuYe8o3lW2QQCLcBGAsYHQ/s16000/8.png)

### **Concurrent Scan**

Another parameter to look at is the -cs which is the Concurrent Scans. This is basically the number of scans that are being performed per target. By default, the setting is set to 10. When changed to any other value such as 2 then only 2 scans will be performed per host. Once it is finished it will run another instance of the scan.

Hence, each of the targets that are being scanned will at least have 3 nmap scans running, basically a full TCP, a top 1000 TCP and a top 20 UDP.

autorecon -cs 5 192.168.126.132

![](https://1.bp.blogspot.com/-gOkCnSx4OYk/YFtTMqNFVUI/AAAAAAAAu80/GvV35ioaRMkbpt68XibeJ5g-MGPme_PyACLcBGAsYHQ/s16000/9.png)

### **Single Target Argument**

The –single-target argument enables the users to scan the host but changing the directory structure. It means that the AutoRecon will only scan the target but no directory will be created for that particular target.

autorecon 192.168.126.133 --single-target

![](https://1.bp.blogspot.com/-3LCGRBcCXpY/YFtTRUhbRxI/AAAAAAAAu88/6_mkctY9Q6kwA0I53I__EpRLAg77U8kyQCLcBGAsYHQ/s16000/10.png)

Due to the use of the –single-target parameter, it didn’t create a directory by the name of the target inside the results folder.

ls -la results
cat results/report/notes.txt

![](https://1.bp.blogspot.com/-7a9nNJnKa-Q/YFtTVajp_GI/AAAAAAAAu9E/NlUVHshOEWAzlJ3uQLwKhLpSqU1-Gc5kwCLcBGAsYHQ/s16000/11.png)

### **Heartbeat Argument**

The –heartbeat argument allows the users to configure the duration of the updates that are provided by AutoRecon. By default, it is 60 seconds. It means AutoRecon will update the user what is going on and which scans are running every 60 seconds.

autorecon 192.168.126.133 --heartbeat 5

![](https://1.bp.blogspot.com/-b6XspKk6aCc/YFtTZlzIlzI/AAAAAAAAu9I/6mkX0nylJusl1RtQ7VxYQHsa6hJmeTk1wCLcBGAsYHQ/s16000/12.png)

### **Nmap Arguments**

Now here we have two options, we can either replace our own parameters instead of the ones that are provided here, by using the –nmap argument and passing the parameters that we want to perform.

autorecon 192.168.126.133 --nmap sV

![](https://1.bp.blogspot.com/-qz80Q_zLltM/YFtTicqHi_I/AAAAAAAAu9Q/ryipLgdej5Ud4MZyqL1MxIUy_Q9vtf32wCLcBGAsYHQ/s16000/13.png)

In the previous step, we added the -sV argument to the nmap scan, now in order to check we will read the commands.log file to see that it indeed uses the -sV parameter while scanning. It should also be noted that the default parameters -vv, –reason, -Pn are not used.

cat results/192.168.126.133/scans/_commands.log

![](https://1.bp.blogspot.com/-iMBzgrdCmpk/YFtTnHbmtNI/AAAAAAAAu9Y/GAYv_2yPSUwYGL0tUFHL-c2yhwHbddkbACLcBGAsYHQ/s16000/14.png)

We can use the –nmap-append option to add our parameters but not override the AutoRecon default parameters. It will append our parameters to it.

autorecon 192.168.126.133 --nmap-append sS

![](https://1.bp.blogspot.com/-Fdzt_L6x3PM/YFtTsbACdLI/AAAAAAAAu9c/wO_MhDnDuLQV_DWj6FrnJWjv0fMfujm6gCLcBGAsYHQ/s16000/15.png)

Let’s again check if the argument we added i.e., -sS has been appended with -vv, –reason, -Pn. It can be confirmed form a detailed read of the commands.log file.

cat results/192.168.126.133/scans/_commands.log

![](https://1.bp.blogspot.com/-WKuC-FSSqmw/YFtTz5Qg_OI/AAAAAAAAu9g/Zi-noZbrS_gNVg8pBk6G4h6BDMQJprH7gCLcBGAsYHQ/s16000/16.png)

### **Verbosity Scans**

AutoRecon has different levels of verbosity. By default, it doesn’t run with any verbosity that means it just informs the user when it initiates a scan and when the scan finishes, it does not provide any details regarding those tasks. With the -v argument, it will be telling the user more about the scans like it will show the complete commands it is running, it will also provide more information about the services that were detected and are being further enumerated.

autorecon -v 192.168.154.130

![](https://1.bp.blogspot.com/-eCJsw0uJ_tc/YFtT_xs6_YI/AAAAAAAAu9s/TlH8m0y1ozc9-O8zWFUocGwKAgRYm3RiwCLcBGAsYHQ/s16000/17.png)

You can also use -vv which stands for Very Verbose. It is not recommended as it will print all the scans and their results in real-time. It clutters up the screen with too much information.

autorecon -vv 192.168.154.130

![](https://1.bp.blogspot.com/-gMIUxlk3vRc/YFtUEU9oT-I/AAAAAAAAu90/NxRn6H2tS6EpoPah0r7VrN3G1sLkXJ0ZQCLcBGAsYHQ/s16000/18.png)

### **Only Scans Dir Argument**

AutoRecon creates a bunch of directories based on the type of evidence it collects. But there are some situations where all that is required is the scan results. This is where the Only Scans Dir argument comes into action. This prevents the creation of other directories.

autorecon 192.168.154.130 --only-scans-dir

![](https://1.bp.blogspot.com/-ZaiKakikbjU/YFtUIcwjvTI/AAAAAAAAu94/ViE9gQHZbrQF7JC7qISTyFWT5qEK5qZoQCLcBGAsYHQ/s16000/19.png)

Here, we can see that inside the results/target directory we have only one directory by the name of scan which will contain the scan results. Talking about the results, let’s discuss the results that AutoRecon produces in detail.

ls -la results
ls -la results/192.168.126.133

![](https://1.bp.blogspot.com/-kWLR-Oc7AMU/YFtUMFiSXbI/AAAAAAAAu-A/opySu5eCm1Mg0AuakKFg-I6rI_mK-1osACLcBGAsYHQ/s16000/20.png)

### **Results**

AutoRecon when initiated with a scan, it creates a result directory. The name of the directory can be configured using the -o parameter. If no parameter is mentioned, it will create the results directory in the current folder. Inside the results directory, it will divide into the different targets. Suppose you scanned like 4 IP Addresses, it will create 4 directories with the IP Address as name. You could go inside any one of them to find different directories created according to the nature of the finding. So, the exploit directory would have any particular exploit that the target is vulnerable to. Although keep in mind that the exploit will have to be surely working. It means that it won’t show up if there is some suspicion that the exploit will work or not. The absolute surety will create entries inside that directory. Then we have the loot directory it will be anything the AutoRecon grabbed from the host machine. Repot would be the stuff that could go into a Penetration Testing Report for example notes etc.

ls -la | grep results
cd results
cd 192.168.126.132
tree

![](https://1.bp.blogspot.com/-vX3isY_Bh1A/YFtURd65QLI/AAAAAAAAu-I/_pLNGYHwQ6Qroze1_Hz3olmjCt4C-JWZQCLcBGAsYHQ/s16000/21.png)

We can see that the notes inside the report folder contain the basic findings that were detected by the Nmap. It shows different services that were found running on the target application using AutoRecon. It can be used as a kind of quick reference guide.

cat ~/results/192.168.126.132/report/notes.txt

![](https://1.bp.blogspot.com/-d2yg-i_GtpU/YFtUYAdVvJI/AAAAAAAAu-Q/DpboJLOHVCUrX5Ob-_ykJs7zxjz_64dCACLcBGAsYHQ/s16000/22.png)

If we look further, we have the full nmap scan report.

cat ~/results/192.168.126.132/scans/_full_tcp_nmap.txt

![](https://1.bp.blogspot.com/-knKjHOAfHRg/YFtUd7Eq6LI/AAAAAAAAu-c/qBsKYszuEHUT2XhSNn7UyetsbexWcg4hwCLcBGAsYHQ/s16000/23.png)

### **Enum4Linux Scan**

It also runs the Enum4Linux scan upon detecting the operating system like Linux. The result for this scan is located at the following location: results/<targetname>/scans/enum4linux.txt

cat ~/results/192.168.126.132/scans/enum4linux.txt

![](https://1.bp.blogspot.com/-P6_nJLmfThc/YFtUjnC-KII/AAAAAAAAu-g/6xud5rtdKGYyS6gynaShHjd5ll0Hdan-QCLcBGAsYHQ/s16000/24.png)

### **SMBMap Scan**

Among other scans, AutoRecon also conducts SMBMap upon find the SMB service running on the application. SMBMap enumerates the different shares on the network by the target machine with the allowed permissions on that particular share. This scan result is located at the following location: results/<targetname>/scans/smbmap-share-permissions.txt

cat ~/results/192.168.126.132/scans/smbmap-share-permissions.txt

![](https://1.bp.blogspot.com/-c1aMIpzc4h4/YFtUowKTFcI/AAAAAAAAu-o/r6GH-dyxTUM-8BD4CMPlPfpCW0qKm7GvgCLcBGAsYHQ/s16000/25.png)

### **SMTP Scan**

A simple enumeration for the SMTP users is also performed using the script called smtp-user-enum. It is performed in case the SMTP service is detected on the target machine. It enumerates for the users that created on the SMTP instance. In our demonstration, we found that there are 4 users that exist on the target server. The result for the enumeration scan can be found at the following location. results/<targetname>/scans/tcp_25_smtp_user-enum.txt

cat ~/results/192.168.126.132/scans/tcp_25_smtp_user-enum.txt

![](https://1.bp.blogspot.com/-c1J3blbvNfo/YFtUuDordFI/AAAAAAAAu-w/uJXcsJ2itG8qZohSL4tqyhaCrn2EtCa1ACLcBGAsYHQ/s16000/26.png)

### **WhatWeb Scan**

Another one of the scan results to look for is the WhatWeb enumeration scan. It uses the WhatWeb functionality to grab the banner on various services and then analyzing the versions and releases of the various web-based services and frameworks. The result for the WhatWeb scan can be located at the following location: results/<targetname>/scans/tcp_8180_http_whatweb.txt

file:///root/results/192.168.126.132/scans/tcp_8180_http_whatweb.txt

![](https://1.bp.blogspot.com/-BQJt6kKSV3s/YFtU1pd1XVI/AAAAAAAAu-4/VIv0UwKp0wATIr52fxbE14ULxVKEUqWQQCLcBGAsYHQ/s16000/27.png)

### **XML Results**

AutoRecon also crafts a few results in the XML format for a clean and easy read. One of them results in our demonstration is the Nmap Scan for the FTP service. The XML result for the WhatWeb scan can be located at the following location: results/<targetname>/scans/xml/tcp_21_ftp_nmap.xml

file:///root/results/192.168.126.132/scans/xml/tcp_21_ftp_nmap.xml

![](https://1.bp.blogspot.com/-Cr0yBjFN9po/YFtU6AR50aI/AAAAAAAAu_A/GloAkooDQmQYfXxz4I0-dYdVZ7hKc5EoQCLcBGAsYHQ/s16000/28.png)

### **Nikto Scan**

All the scans that the AutoRecon additionally run are very useful in any Penetration Assessment but Nikto is one that might do the most enumeration as it after Nmap if any tool that can extract more data is Nikto. The scan result for the Nikto scan is located at this location: 

cat ~/results/192.168.126.132/scans/tcp_8180_http_nikto.txt

![](https://1.bp.blogspot.com/-3dIe7wEfaZk/YFtU-0gtThI/AAAAAAAAu_I/-OhoFPJ1vyg7I9ArOp0tbri7F9hTtBg9gCLcBGAsYHQ/s16000/29.png)

### **Web Services Screenshots**

When faced with an HTTP service that might contain webpages, AutoRecon snaps a screenshot of the webpage. In our demonstration, there was a HTTP service running on port 8180. It was the Apache Tomcat default page. This is super helpful when solving CTFs as we need to take a look at the web services. This way we can know if it is worth browsing web service or not.

file:///root/results/192.168.126.132/scans/tcp_8180_http_screenshot.png

![](https://1.bp.blogspot.com/-qEx1d0Uw-qM/YFtVD6xERXI/AAAAAAAAu_M/tsNoPMLqFFE19b_Xk-rNVITuBLa-S3MdwCLcBGAsYHQ/s16000/30.png)

**Author: Pavandeep Singh** is a Technical Writer, Researcher, and Penetration Tester. Can be Contacted on **[Twitter](https://twitter.com/pavan2318)** and **[LinkedIn](https://www.linkedin.com/in/pavan2318/)**

**Credit:** This information was adapted from an excellent guide on [HackingArticles.in](https://www.hackingarticles.in/comprehensive-guide-to-autorecon/). Be sure to check out the original post for more details.


<iframe width="560" height="315" src="https://www.youtube.com/embed/HiRoNW7XG5s?si=m8ulHDku7u2LCH6z" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=HiRoNW7XG5s). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/t5RK3hW4zOI?si=cKpxDQfhMiDviXYp" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=t5RK3hW4zOI&t=98s). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/m5Onw7XedHc?si=JxXH2m11x2zvOK9L" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=m5Onw7XedHc). Be sure to check out the original post for more details.
