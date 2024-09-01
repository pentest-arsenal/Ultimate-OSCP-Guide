[![WPScan logo](https://raw.githubusercontent.com/wpscanteam/wpscan/gh-pages/images/wpscan_logo.png)](https://wpscan.com/)

### WPScan

[](https://github.com/wpscanteam/wpscan#wpscan)

WordPress Security Scanner  
  
[WPScan WordPress Vulnerability Database](https://wpscan.com/ "homepage") - [WordPress Security Plugin](https://wordpress.org/plugins/wpscan/ "wordpress security plugin")

[![](https://camo.githubusercontent.com/cc0b1c1ef9e890852f5d4c64377834f8ca37a88945811176778103afb88f5cac/68747470733a2f2f62616467652e667572792e696f2f72622f77707363616e2e737667)](https://badge.fury.io/rb/wpscan) [![](https://camo.githubusercontent.com/d8ca274b0eb4019dc95d34c030bcce0437c373601b38a381fc6560319689c862/68747470733a2f2f696d672e736869656c64732e696f2f646f636b65722f70756c6c732f77707363616e7465616d2f77707363616e2e737667)](https://hub.docker.com/r/wpscanteam/wpscan/) [![](https://github.com/wpscanteam/wpscan/workflows/Build/badge.svg)](https://github.com/wpscanteam/wpscan/actions?query=workflow%3ABuild) [![](https://camo.githubusercontent.com/de42ae381d5309f87c194e4bde347c6b4215a1de4b430d73dbd37e813bd6d14d/68747470733a2f2f636f6465636c696d6174652e636f6d2f6769746875622f77707363616e7465616d2f77707363616e2f6261646765732f6770612e737667)](https://codeclimate.com/github/wpscanteam/wpscan)

# INSTALL

[](https://github.com/wpscanteam/wpscan#install)

## Prerequisites

[](https://github.com/wpscanteam/wpscan#prerequisites)

- (Optional but highly recommended: [RVM](https://rvm.io/rvm/install))
- Ruby >= 2.7 - Recommended: latest
- Curl >= 7.72 - Recommended: latest
    - The 7.29 has a segfault
    - The < 7.72 could result in `Stream error in the HTTP/2 framing layer` in some cases
- RubyGems - Recommended: latest
- Nokogiri might require packages to be installed via your package manager depending on your OS, see [https://nokogiri.org/tutorials/installing_nokogiri.html](https://nokogiri.org/tutorials/installing_nokogiri.html)

### In a Pentesting distribution

[](https://github.com/wpscanteam/wpscan#in-a-pentesting-distribution)

When using a pentesting distubution (such as Kali Linux), it is recommended to install/update wpscan via the package manager if available.

### In macOSX via Homebrew

[](https://github.com/wpscanteam/wpscan#in-macosx-via-homebrew)

```shell
brew install wpscanteam/tap/wpscan
```

### From RubyGems

[](https://github.com/wpscanteam/wpscan#from-rubygems)

```shell
gem install wpscan
```

On MacOSX, if a `Gem::FilePermissionError` is raised due to the Apple's System Integrity Protection (SIP), either install RVM and install wpscan again, or run `sudo gem install -n /usr/local/bin wpscan` (see [#1286](https://github.com/wpscanteam/wpscan/issues/1286))

# Updating

[](https://github.com/wpscanteam/wpscan#updating)

You can update the local database by using `wpscan --update`

Updating WPScan itself is either done via `gem update wpscan` or the packages manager (this is quite important for distributions such as in Kali Linux: `apt-get update && apt-get upgrade`) depending on how WPScan was (pre)installed

# Docker

[](https://github.com/wpscanteam/wpscan#docker)

Pull the repo with `docker pull wpscanteam/wpscan`

Enumerating usernames

```shell
docker run -it --rm wpscanteam/wpscan --url https://target.tld/ --enumerate u
```

Enumerating a range of usernames

```shell
docker run -it --rm wpscanteam/wpscan --url https://target.tld/ --enumerate u1-100
```

** replace u1-100 with a range of your choice.

# Usage

[](https://github.com/wpscanteam/wpscan#usage)

Full user documentation can be found here; [https://github.com/wpscanteam/wpscan/wiki/WPScan-User-Documentation](https://github.com/wpscanteam/wpscan/wiki/WPScan-User-Documentation)

`wpscan --url blog.tld` This will scan the blog using default options with a good compromise between speed and accuracy. For example, the plugins will be checked passively but their version with a mixed detection mode (passively + aggressively). Potential config backup files will also be checked, along with other interesting findings.

If a more stealthy approach is required, then `wpscan --stealthy --url blog.tld` can be used. As a result, when using the `--enumerate` option, don't forget to set the `--plugins-detection` accordingly, as its default is 'passive'.

For more options, open a terminal and type `wpscan --help` (if you built wpscan from the source, you should type the command outside of the git repo)

The DB is located at ~/.wpscan/db

## Optional: WordPress Vulnerability Database API

[](https://github.com/wpscanteam/wpscan#optional-wordpress-vulnerability-database-api)

The WPScan CLI tool uses the [WordPress Vulnerability Database API](https://wpscan.com/api) to retrieve WordPress vulnerability data in real time. For WPScan to retrieve the vulnerability data an API token must be supplied via the `--api-token` option, or via a configuration file, as discussed below. An API token can be obtained by registering an account on [WPScan.com](https://wpscan.com/register).

Up to **25** API requests per day are given free of charge, that should be suitable to scan most WordPress websites at least once per day. When the daily 25 API requests are exhausted, WPScan will continue to work as normal but without any vulnerability data.

### How many API requests do you need?

[](https://github.com/wpscanteam/wpscan#how-many-api-requests-do-you-need)

- Our WordPress scanner makes one API request for the WordPress version, one request per installed plugin and one request per installed theme.
- On average, a WordPress website has 22 installed plugins.

## Load CLI options from file/s

[](https://github.com/wpscanteam/wpscan#load-cli-options-from-files)

WPScan can load all options (including the --url) from configuration files, the following locations are checked (order: first to last):

- ~/.wpscan/scan.json
- ~/.wpscan/scan.yml
- pwd/.wpscan/scan.json
- pwd/.wpscan/scan.yml

If those files exist, options from the `cli_options` key will be loaded and overridden if found twice.

e.g:

~/.wpscan/scan.yml:

```yaml
cli_options:
  proxy: 'http://127.0.0.1:8080'
  verbose: true
```

pwd/.wpscan/scan.yml:

```yaml
cli_options:
  proxy: 'socks5://127.0.0.1:9090'
  url: 'http://target.tld'
```

Running `wpscan` in the current directory (pwd), is the same as `wpscan -v --proxy socks5://127.0.0.1:9090 --url http://target.tld`

## Save API Token in a file

[](https://github.com/wpscanteam/wpscan#save-api-token-in-a-file)

The feature mentioned above is useful to keep the API Token in a config file and not have to supply it via the CLI each time. To do so, create the ~/.wpscan/scan.yml file containing the below:

```yaml
cli_options:
  api_token: 'YOUR_API_TOKEN'
```

## Load API Token From ENV (since v3.7.10)

[](https://github.com/wpscanteam/wpscan#load-api-token-from-env-since-v3710)

The API Token will be automatically loaded from the ENV variable `WPSCAN_API_TOKEN` if present. If the `--api-token` CLI option is also provided, the value from the CLI will be used.

## Enumerating usernames

[](https://github.com/wpscanteam/wpscan#enumerating-usernames)

```shell
wpscan --url https://target.tld/ --enumerate u
```

Enumerating a range of usernames

```shell
wpscan --url https://target.tld/ --enumerate u1-100
```

** replace u1-100 with a range of your choice.

# LICENSE

[](https://github.com/wpscanteam/wpscan#license)

## WPScan Public Source License

[](https://github.com/wpscanteam/wpscan#wpscan-public-source-license)

The WPScan software (henceforth referred to simply as "WPScan") is dual-licensed - Copyright 2011-2019 WPScan Team.

Cases that include commercialization of WPScan require a commercial, non-free license. Otherwise, WPScan can be used without charge under the terms set out below.

### 1. Definitions

[](https://github.com/wpscanteam/wpscan#1-definitions)

1.1 "License" means this document.

1.2 "Contributor" means each individual or legal entity that creates, contributes to the creation of, or owns WPScan.

1.3 "WPScan Team" means WPScan’s core developers.

### 2. Commercialization

[](https://github.com/wpscanteam/wpscan#2-commercialization)

A commercial use is one intended for commercial advantage or monetary compensation.

Example cases of commercialization are:

- Using WPScan to provide commercial managed/Software-as-a-Service services.
- Distributing WPScan as a commercial product or as part of one.
- Using WPScan as a value added service/product.

Example cases which do not require a commercial license, and thus fall under the terms set out below, include (but are not limited to):

- Penetration testers (or penetration testing organizations) using WPScan as part of their assessment toolkit.
- Penetration Testing Linux Distributions including but not limited to Kali Linux, SamuraiWTF, BackBox Linux.
- Using WPScan to test your own systems.
- Any non-commercial use of WPScan.

If you need to purchase a commercial license or are unsure whether you need to purchase a commercial license contact us - [contact@wpscan.com](mailto:contact@wpscan.com).

Free-use Terms and Conditions;

### 3. Redistribution

[](https://github.com/wpscanteam/wpscan#3-redistribution)

Redistribution is permitted under the following conditions:

- Unmodified License is provided with WPScan.
- Unmodified Copyright notices are provided with WPScan.
- Does not conflict with the commercialization clause.

### 4. Copying

[](https://github.com/wpscanteam/wpscan#4-copying)

Copying is permitted so long as it does not conflict with the Redistribution clause.

### 5. Modification

[](https://github.com/wpscanteam/wpscan#5-modification)

Modification is permitted so long as it does not conflict with the Redistribution clause.

### 6. Contributions

[](https://github.com/wpscanteam/wpscan#6-contributions)

Any Contributions assume the Contributor grants the WPScan Team the unlimited, non-exclusive right to reuse, modify and relicense the Contributor's content.

### 7. Support

[](https://github.com/wpscanteam/wpscan#7-support)

WPScan is provided under an AS-IS basis and without any support, updates or maintenance. Support, updates and maintenance may be given according to the sole discretion of the WPScan Team.

### 8. Disclaimer of Warranty

[](https://github.com/wpscanteam/wpscan#8-disclaimer-of-warranty)

WPScan is provided under this License on an “as is” basis, without warranty of any kind, either expressed, implied, or statutory, including, without limitation, warranties that the WPScan is free of defects, merchantable, fit for a particular purpose or non-infringing.

### 9. Limitation of Liability

[](https://github.com/wpscanteam/wpscan#9-limitation-of-liability)

To the extent permitted under Law, WPScan is provided under an AS-IS basis. The WPScan Team shall never, and without any limit, be liable for any damage, cost, expense or any other payment incurred as a result of WPScan's actions, failure, bugs and/or any other interaction between WPScan and end-equipment, computers, other software or any 3rd party, end-equipment, computer or services.

### 10. Disclaimer

[](https://github.com/wpscanteam/wpscan#10-disclaimer)

Running WPScan against websites without prior mutual consent may be illegal in your country. The WPScan Team accept no liability and are not responsible for any misuse or damage caused by WPScan.

### 11. Trademark

[](https://github.com/wpscanteam/wpscan#11-trademark)

The "wpscan" term is a registered trademark. This License does not grant the use of the "wpscan" trademark or the use of the WPScan logo.

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/wpscanteam/wpscan). Be sure to check out the original post for more details.

# WPScan Intro: How to Scan for WordPress Vulnerabilities

- December 12, 2023

![How to Scan WordPress for Vulnerabilities](https://blog.sucuri.net/wp-content/uploads/2021/05/WPScan-Scan-for-Vulns1-820x385.png)

In this post, we will look at how to use WPScan as a **WordPress vulnerability scanner**. This security tool provides you with a better understanding of your WordPress website and any vulnerabilities that may be present in your environment. It also happens to be pre-installed in Kali Linux. If you haven’t set it up yet, be sure to check out [our post on installing WPScan](https://blog.sucuri.net/2021/04/how-to-install-wpscan-wordpress-vulnerability-scan.html) to get started with the software.

**Contents:**

- **[How to scan and analyze your WordPress site](https://blog.sucuri.net/2023/12/wpscan-intro-how-to-scan-for-wordpress-vulnerabilities.html#scan-and-analyze)**
- **[How to start using WPScan](https://blog.sucuri.net/2023/12/wpscan-intro-how-to-scan-for-wordpress-vulnerabilities.html#start-using)**
- **[How to run a basic scan](https://blog.sucuri.net/2023/12/wpscan-intro-how-to-scan-for-wordpress-vulnerabilities.html#run-a-basic-scan)**
- **[How to scan WordPress for vulnerable themes and plugins](https://blog.sucuri.net/2023/12/wpscan-intro-how-to-scan-for-wordpress-vulnerabilities.html#identify-vulnerabilities)**
- **[How to check user enumeration](https://blog.sucuri.net/2023/12/wpscan-intro-how-to-scan-for-wordpress-vulnerabilities.html#check-user-enumeration)**
- **[How to test a password attack](https://blog.sucuri.net/2023/12/wpscan-intro-how-to-scan-for-wordpress-vulnerabilities.html#test-password-attacks)**
- **[Enumeration options](https://blog.sucuri.net/2023/12/wpscan-intro-how-to-scan-for-wordpress-vulnerabilities.html#enumeration-options)**

## Big threats come from unexpected places

Imagine for a second that you’re a survivor in a zombie apocalypse.

You’ve holed up in a grocery store, barricading windows and checking door locks. Things seem pretty quiet and secure. But just as you sit down to enjoy an oversized can of chocolate pudding, a thought crosses your mind. A bunch of thoughts, really.

![Boy eating gif](https://blog.sucuri.net/wp-content/uploads/2021/05/image2.gif)

You remember all the times you’ve seen this exact scenario in zombie movies. You start thinking about all the unknown possibilities that could still expose you to the horde:

- Faulty window fittings that’ll give with too much pressure
- A nasty gang that raid supplies from this spot every couple weeks
- A fire alarm that erratically triggers and draws zombies from miles around
- A very-real dumpster fire that’s growing outside and could set the whole place ablaze
- A backroom freezer where previous inhabitants locked a dozen very-hungry zombies

Wouldn’t it be nice if you could scan the entire grocery store in a way that would reveal if those potential problems were real problems?

Well, a double-sized helping of good news:

1. You’re not living in a zombie apocalypse.
2. WPScan does exactly this for your WordPress website.

## How to scan and analyze your WordPress site with WPScan

WPScan examines your site in the same way most attackers do: It enumerates details and checks them against its database of vulnerabilities and exploits.

Having this information in your own hands, you can more precisely address issues that might not be readily apparent.

![WPScan version 3.8.25](https://blog.sucuri.net/wp-content/uploads/2023/12/wpscan-650x273.png)

### How to start using WPScan

A command line will, of course, be your base of operations.

If you’ve [installed WPScan](https://blog.sucuri.net/2021/04/how-to-install-wpscan-wordpress-vulnerability-scan.html), always begin with an update. After all, if everyone knows about a potential issue but you, you’re ripe for an attack.

Use this command:

gem update wpscan

If you installed on Mac with the Homebrew approach, use this instead:

brew upgrade wpscan

### How to run a basic scan with WPScan

When using WPScan, your command will always start with **wpscan**, and then it’ll point the tool to your URL.

wpscan --url yourwebsite.com

Running the command above will perform a basic scan of your site. After a few minutes, you’ll have a whole bunch of “Interesting Findings” that WPScan discovered from your site’s code. That could include information like:

- Headers to discover server information
- Accessibility of [xmlrpc.php](https://blog.sucuri.net/2019/05/xmlrpc-php-brute-force-tool.html)
- Accessibility of wp-cron.php
- WordPress version
- Active theme and its basic information
- Active plugins and their basic information
- Discoverable Config backups

Different site and server configurations might reveal different information.

![Running WPScan](https://blog.sucuri.net/wp-content/uploads/2021/05/image6.png)

#### Troubleshooting firewall restrictions

If your site runs behind a firewall and you’re encountering issues, you can try the following commands to reduce noise and bypass restrictions. These may not work on some firewalls, however.

##### Random user agent

Test different user agents by adding the **–random-user-agent** option to the end:

wpscan --url yourwebsite.com --random-user-agent

##### Throttle (Milliseconds)

Define the number of milliseconds that should pass before making another request, which can help with navigating rate-limiting checks:

wpscan --url yourwebsite.com --throttle 2500

##### Stealthy mode

Try the stealthy mode alias that combines the following scan options to most effectively avoid nose and bypass restrictions: **–random-user-agent –detection-mode passive –plugins-version-detection passive**

wpscan --url yourwebsite.com --stealthy

### How to scan WordPress for vulnerable themes and plugins

While a basic scan will show you if a theme or plugin version is out of date, it won’t tell you if there are specific vulnerabilities with that version. To get that info, you’ll need to utilize the [WPScan Vulnerability Database API](https://wpscan.com/api).

In our [WPScan installation guide](https://blog.sucuri.net/2021/04/how-to-install-wpscan-wordpress-vulnerability-scan.html), we had you register to use the API. You’ll now insert your unique API token into a scan in order to access this specialized information.

You’ll also add some additional flags based on the specific information you want to get. The most important one in this case is -e (which stands for “enumerate”) and the choice of vp (which, you guessed it, stands for “vulnerable plugins”).

Here’s the most-common command to search for vulnerable plugins:

wpscan --url yourwebsite.com -e vp --api-token YOUR_TOKEN

Keep in mind that this will take a lot longer than the basic scan. In some cases a five-minute basic scan may become a 25-minute vulnerability scan.

Here’s the same detected plugin from the scan above, but using the vulnerability database:

![Running WPScan - 2](https://blog.sucuri.net/wp-content/uploads/2021/05/image7.jpg)

To check your site for a **vulnerable theme**, replace the vp with vt (“vulnerable themes”). Everything else can stay the same.

wpscan --url yourwebsite.com -e vt --api-token YOUR_TOKEN

On top of the theme or plugin vulnerabilities, WPScan will also report any vulnerabilities with the version of WordPress your site is running.

![WPScan Result - Cross Site Scripting](https://blog.sucuri.net/wp-content/uploads/2021/05/image3.png)

### How to check user enumeration with WPScan

Don’t stop at vulnerable plugins and themes, though. [Password attacks](https://blog.sucuri.net/2020/01/password-attacks-101.html) pose another big threat to your site’s security. And WordPress can provide attackers with the critical access and information they look for.

With WPScan, you can determine what usernames are discoverable from the outside.

To run this [user enumeration](https://blog.sucuri.net/2024/07/wordpress-user-enumeration.html) scan, we’ll use this command:

wpscan --url yourwebsite.com -e u

You can probably guess what the “u” stands for.

WPScan will use a few different techniques to do its own guessing: determining usernames based on the information available publicly on your site (i.e. author names). WordPress will tip its hands in some subtle ways as WPScan probes those guesses. (The blacked out content below are discovered user IDs.)

![WPScan Scanning](https://blog.sucuri.net/wp-content/uploads/2021/05/image1.jpg)

Ideally, you don’t want any usernames to be discoverable with these techniques. The easiest way to prevent that is by using different publicly visible nicknames than your user IDs.

#### Why does user enumeration work on WordPress?

By default, WordPress is prone to user enumeration. This is because of permalinks, a feature that provides permanent URLs to individual WordPress posts and pages.

Notably, WordPress lets you list all posts by a specific author’s username or ID, which _could_ be exploited by attackers to identify valid usernames. This is where WPScan’s enumeration tool comes in handy, as it quickly checks if your WordPress site is susceptible to user enumeration.

Attackers strive to collect information about the targeted website, like usernames, plugin names, their versions, themes, and other factors. Knowing usernames alone might not enable an attacker to breach your site, but this information _can_ aid them in crafting their attack strategy.

### How to test a password attack with WPScan

How does an attacker follow up discovering a username? By attempting to access its account, of course.

WPScan actually allows you to simulate this. And this will be especially helpful if the site you’re managing has a lot of contributors: corporate sites, collaborative blogs, and the like.

First, you’ll need to get or create a list of passwords. With a quick Google search, you can find a number of lists of the most commonly used passwords, including the often-used [rockyou wordlist](https://www.kali.org/tools/wordlists/). Keep in mind these lists are long, and this step does amount to a brute-force attack on the scanned site. So, plan appropriately before running this scan: e.g. Prepare your server/admin, shorten the list, clone the site in a staging environment, run during visitor downtime, etc.

To initiate the scan, the command will be:

wpscan --url yourwebsite.com -passwords file/path/passwords.txt

If you put your wordlist into the current directory, you’ll just need the name of the file. But if you place it anywhere else, you’ll need to provide the full path.

![WP Json API](https://blog.sucuri.net/wp-content/uploads/2021/05/image5.png)

In the scan above, we ran a short list of the 5 most common passwords against a site with one enumerated user. Because that user wasn’t using any of these passwords, WPScan reports “No Valid Passwords Found.”

## WPScan enumeration options

To make things a bit easier to reference, we’ve consolidated the full list of WPScan enumeration options into a handy table. Remember to start with the **-e** command to leverage these options.

|   |   |
|---|---|
|**Option**|**Description**|
|ap|Enumerate all plugins|
|vp|Enumerate only vulnerable plugins|
|p|Enumerate popular plugins|
|at|Enumerate all themes|
|vt|Enumerate only vulnerable themes|
|t|Enumerate popular themes|
|tt|Enumerate timthumbs|
|cb|Enumerate publicly exposed wp-config files|
|u|Enumerate user ID ranges (example: u1-9)|
|m|Enumerate media ID ranges (example: m1-9)|

Looking for more arguments?  You can run the following help command to view all available scan and enumeration options from the command line interface.

wpscan --help

## Proactive protection with WordPress vulnerability scanning

In the end, the preventative measures you take to ensure the security of your WordPress sites upfront reduce the likelihood – and potential impact – of problems down the line.

The more thoroughly you incorporate tools like WPScan (or even our own [website firewall](https://sucuri.net/website-firewall/)) into your site building process, the easier it will be to find and fix new vulnerabilities as they arise.

It’s also worth noting that WPScan is not able to detect website malware – so, if you’ve identified any vulnerabilities on your site, you may want to check for [signs of a hacked website](https://blog.sucuri.net/2023/02/is-my-website-hacked.html) after you’ve patched up any security holes in your environment. And be sure to use a solid [website monitoring](https://sucuri.net/malware-detection-scanning/) solution, too.

Even if your site’s been around for a long time, there’s no better time to start than now in assessing risks and securing it. The last thing you want is to be 64-ounces deep in a can of pudding and have a zombie grab the spoon out of your hand.

**Credit:** This information was adapted from an excellent guide on [Blog.Sucuri.net](https://blog.sucuri.net/2023/12/wpscan-intro-how-to-scan-for-wordpress-vulnerabilities.html). Be sure to check out the original post for more details.

# How to Use wpscan tool in Kali Linux

Last Updated : 23 Sep, 2022

Wpscan is a WordPress security scanner used to test WordPress installations and WordPress-powered websites. This is a command line tool used in Kali Linux. This tool can be used to find any vulnerable plugins, themes, or backups running on the site. It is usually used by individual WordPress site owners to test their own websites for vulnerabilities and also by large organizations to maintain a secure website. This tool can also be used to enumerate users and perform brute-force attacks on known WordPress users. In this article, We are going to take you through different commands of wpscan tool, the most commonly used attacks on WordPress sites, and tips to defend against them. The below functionalities of this tool can be used from the point of view of a hacker or even just someone who wants to test if their WordPress site is secure enough.

Wpscan is usually pre-installed in kali Linux. Otherwise, Click [here](https://www.geeksforgeeks.org/installation-of-wpscan-tool-in-kali-linux/) to read the installation process of the Wpscan tool.

## Different commands and applications of wpscan:

For this example,  we will be using a vulnerable version of WordPress i.e WordPress 5.0-powered website. We will be scanning this website for vulnerabilities using wpscan.

### **Wpscan commands:**

**1)  –url : (basic scan)** 

The following command performs a vulnerability scan of the entire WordPress site scanning for any vulnerable plugins, themes, and backups.

> command:   wpscan –url IP_ADDRESS_OF_WEBSITE

![](https://media.geeksforgeeks.org/wp-content/uploads/20220820215946/1.jpg)

![](https://media.geeksforgeeks.org/wp-content/uploads/20220820220125/2.jpg)

We can see the results of the scan wherein otherwise hidden files such as robots.txt and a readme file are listed out and we can also see the version of the WordPress site used. It also lists all the plugins, themes, and config backups the website uses. If we find any vulnerable/outdated plugins or themes, make sure to remove them and install the updated ones to avoid giving the opportunity to hackers to take advantage of outdated software to hack into your system  

**2) –help: (help options)**

command: wpscan --help

It’s a common practice in Linux to use the “–help” option to get the complete list of the usability of the tool using different switches for different functionalities.

![](https://media.geeksforgeeks.org/wp-content/uploads/20220820221708/help.jpg)

![](https://media.geeksforgeeks.org/wp-content/uploads/20220820221816/help2.jpg)

**3) -e u: (enumerating website users)**

> command:   wpscan –url IP_ADDRESS_OF_WEBSITE -e u

This lets the wpscan tool enumerate the WordPress site for valid login usernames. After the scan, it would give all the usernames the tool has enumerated which are valid users of the WordPress site and are often times brute forced to gain unauthorized access to the WordPress admin/author dashboard.

![](https://media.geeksforgeeks.org/wp-content/uploads/20220820222450/3.jpg)

![](https://media.geeksforgeeks.org/wp-content/uploads/20220820222913/4resizereq.jpg)

4) -U -P: (brute-forcing password for the identified user)

> command:   wpscan –url IP_ADDRESS_OF_WEBSITE -U USER_NAME -P PATH_TO_WORDLIST

As we managed to enumerate some usernames for the WordPress site above, let’s try to brute-force the user “kwheel”.

- **Brute forcing**: It is a technique where a wordlist is used against a tool that effectively finds the matching password for the given username.
- **Wordlist**: The password cracking tool uses a wordlist, which is nothing but a text file containing a set of commonly used passwords. Ex: 12345678, qwerty, pizza123,etc.

Now let’s try to brute force the user “kwheel”. 

![](https://media.geeksforgeeks.org/wp-content/uploads/20220820223701/kwheelpasscmd.jpg)

rockyou.txt is a quite commonly used wordlist for brute force attacks.

![](https://media.geeksforgeeks.org/wp-content/uploads/20220820223950/passkwheelcracked.jpg)

successful brute force attack

As you can see, we have cracked the password for the user “kwheel”. The password is “cutiepie1” which is rather easy to crack as it is not a complex password.  To protect against such brute force attacks, make sure not to use common passwords, nicknames, date of birth, pet names, etc.

**Credit:** This information was adapted from an excellent guide on [GeeksForGeeks](https://www.geeksforgeeks.org/how-to-use-wpscan-tool-in-kali-linux/). Be sure to check out the original post for more details.

# Unveiling WordPress Vulnerabilities: A Comprehensive Guide to Using WPScan


![](https://miro.medium.com/v2/resize:fit:700/1*eYvliCyCG1nZJ-1qAImu_A.png)

me@erevu.co.ke

# Introduction

WordPress is one of the most popular content management systems (CMS) on the internet. With its extensive plugin ecosystem and user-friendly interface, it powers a significant portion of websites across the globe. However, like any software, WordPress is not immune to security vulnerabilities. In this guide, we will explore how to use WPScan, a powerful open-source tool, to uncover potential security weaknesses in WordPress installations. We will cover its functionalities and provide practical examples of code to demonstrate its usage.

# What is WPScan?

WPScan is a widely used WordPress vulnerability scanner. It’s designed to help security professionals, developers, and website administrators identify security weaknesses in WordPress installations. WPScan leverages a database of known vulnerabilities, enumerates installed plugins and themes, and checks for misconfigurations. By regularly scanning your WordPress website, you can stay one step ahead of potential attackers and maintain a secure online presence.

# Installing WPScan

Before diving into its functionalities, let’s walk through the installation process. WPScan is written in Ruby, so ensure you have Ruby installed on your system. Follow these steps to install WPScan:

1. Open your terminal.
2. Install Ruby if you don’t have it: `sudo apt-get install ruby-full` (for Ubuntu).
3. Install required gems: `gem install wpscan`.

Once WPScan is installed, you’re ready to start scanning your WordPress site.

# Basic Usage

# Scanning a Single URL

To scan a specific WordPress website, use the following command:

wpscan --url <target_url>

Replace `<target_url>` with the URL of the WordPress site you want to scan.

Using the — — random-user-agent you can be able enhances its capabilities by allowing scans to mimic a range of user agents.

wpscan --url <target_url> --random-user-agent

# Enumerating Plugins and Themes

WPScan allows you to enumerate the installed plugins and themes on a target WordPress site

wpscan --url <target_url> --enumerate p --enumerate t

This command will provide a list of installed plugins and themes, along with their versions.

# Advanced Usage

# Performing a Full Scan

To conduct a thorough scan, including plugin, theme, and user enumeration, use the following command

wpscan --url <target_url> --enumerate p --enumerate t --enumerate u u

This command will provide detailed information about plugins, themes, and users, helping you identify potential entry points for attackers.

# Vulnerability Database Update

WPScan relies on an up-to-date vulnerability database. Regularly update it with this command

wpscan --update

By identifying vulnerabilities and weaknesses, you can take proactive steps to mitigate potential risks. Regular scans and prompt updates are crucial in maintaining a robust online presence. Remember that security is an ongoing process, and tools like WPScan are essential components of your defense strategy.

**Credit:** This information was adapted from an excellent guide on [Medium](https://medium.com/@ianmuthuri254/unveiling-wordpress-vulnerabilities-a-comprehensive-guide-to-using-wpscan-b8724fe84b96). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/bVSrlDtTBdI?si=Z6Zivus02CFezTtc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=bVSrlDtTBdI). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/3P6ajyPht58?si=25V5TtSzcGhTvKLD" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=3P6ajyPht58). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/9gwyj4frqwc?si=Yea7aoCZIfj6N0HI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=9gwyj4frqwc&t=77s). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/muxjETbM_E4?si=koJun_6ZDTQLnGbH" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=muxjETbM_E4). Be sure to check out the original post for more details.


