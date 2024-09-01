# Wapiti - Web Vulnerability Scanner

[](https://github.com/wapiti-scanner/wapiti#wapiti---web-vulnerability-scanner)

[![PyPI version](https://camo.githubusercontent.com/738f3cfee290e70a2c7d571ddfc292bb9b7a463363fa6417b577c147c639d0f2/68747470733a2f2f696d672e736869656c64732e696f2f707970692f762f776170697469333f6c6162656c3d50795049266c6f676f3d50795049266c6f676f436f6c6f723d776869746526636f6c6f723d626c7565)](https://pypi.python.org/pypi/wapiti3) [![Supported Python versions](https://camo.githubusercontent.com/d1455f1fad62969c76cfd534cc0ba4a15e38a426c5f572b7ee190986f76be900/68747470733a2f2f696d672e736869656c64732e696f2f707970692f707976657273696f6e732f77617069746933)](https://github.com/wapiti-scanner/wapiti/blob/master/INSTALL.md) [![License: GPL-2.0](https://camo.githubusercontent.com/feb9e1ae85e0a0c2a88454f7049d914ee442c61710a5dc65cd2fdd37d58becec/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f6c6963656e73652f7761706974692d7363616e6e65722f776170697469)](https://github.com/wapiti-scanner/wapiti/blob/master/LICENSE) [![Downloads per day on PyPi](https://camo.githubusercontent.com/bd94f94298adc13846a42ab6e5b5fa3c9a706ddddc519dd6a4f1f7945f3aeb53/68747470733a2f2f696d672e736869656c64732e696f2f707970692f64642f77617069746933)](https://pypi.python.org/pypi/wapiti3) [![https://codecov.io/gh/wapiti-scanner/wapiti/branch/master/graph/badge.svg?token=GFEIORAFB8](https://camo.githubusercontent.com/dc3282a64a4c4098eb9c7869ea6b17a84fde37738d5e1d3115299a1d3dad3579/68747470733a2f2f636f6465636f762e696f2f67682f7761706974692d7363616e6e65722f7761706974692f6272616e63682f6d61737465722f67726170682f62616467652e7376673f746f6b656e3d474645494f5241464238)](https://codecov.io/gh/wapiti-scanner/wapiti)

Wapiti is a web vulnerability scanner written in Python.

[http://wapiti-scanner.github.io/](http://wapiti-scanner.github.io/)

## Requirements

[](https://github.com/wapiti-scanner/wapiti#requirements)

In order to work correctly, Wapiti needs Python 3.10 or 3.11

All Python module dependencies will be installed automatically if you use the setup.py script or pip install wapiti3

See [INSTALL.md](https://github.com/wapiti-scanner/wapiti/blob/master/INSTALL.md) for more details on installation.

Running Wapiti on Windows can be accomplished through the use of [WSL](https://learn.microsoft.com/en-us/training/modules/get-started-with-windows-subsystem-for-linux/).

## How it works

[](https://github.com/wapiti-scanner/wapiti#how-it-works)

Wapiti works as a "black-box" vulnerability scanner, that means it won't study the source code of web applications but will work like a fuzzer, scanning the pages of the deployed web application, extracting links and forms and attacking the scripts, sending payloads and looking for error messages, special strings or abnormal behaviors.

## General features

[](https://github.com/wapiti-scanner/wapiti#general-features)

- Generates vulnerability reports in various formats (HTML, XML, JSON, TXT, CSV).
- Can suspend and resume a scan or an attack (session mechanism using sqlite3 databases).
- Can give you colors in the terminal to highlight vulnerabilities.
- Different levels of verbosity.
- Fast and easy way to activate/deactivate attack modules.
- Adding a payload can be as easy as adding a line to a text file.
- Configurable number of concurrent tasks to perform HTTP requests.

## Browsing features

[](https://github.com/wapiti-scanner/wapiti#browsing-features)

- Support HTTP, HTTPS and SOCKS5 proxies.
- HTTP authentication on the target (Basic, Digest, NTLM)
- Authentication by filling login forms.
- Ability to restrain the scope of the scan (domain, folder, page, url).
- Automatic removal of one or more parameters in URLs.
- Multiple safeguards against scan endless-loops (for example, limit of values for a parameter).
- Possibility to set the first URLs to explore (even if not in scope).
- Can exclude some URLs of the scan and attacks (eg: logout URL).
- Import cookies from your Chrome or Firefox browser or using the wapiti-getcookie tool.
- Can activate / deactivate SSL certificates verification.
- Extract URLs from Flash SWF files.
- Try to extract URLs from javascript (very basic JS interpreter).
- HTML5 aware (understand recent HTML tags).
- Several options to control the crawler behavior and limits.
- Skipping some parameter names during attack.
- Setting a maximum time for the scan process.
- Adding some custom HTTP headers or setting a custom User-Agent.
- Using a Firefox headless browser for crawling
- Loading your own python code for complicated authentication cases (see --form-script option)
- Adding custom URL or PATH to update Wappalyzer database
- Scan REST APIs given an OpenAPI (swagger) file

## Supported attacks

[](https://github.com/wapiti-scanner/wapiti#supported-attacks)

- SQL Injections (Error based, boolean based, time based) and XPath Injections
- LDAP injections (Error based and boolean based)
- Cross Site Scripting (XSS) reflected and permanent
- File disclosure detection (local and remote include, require, fopen, readfile...)
- Command Execution detection (eval(), system(), passtru()...)
- XXE (Xml eXternal Entity) injection
- CRLF Injection
- Search for potentially dangerous files on the server (thank to the Nikto db)
- Bypass of weak htaccess configurations
- Search for copies (backup) of scripts on the server
- Shellshock
- Folder and file enumeration (DirBuster like)
- Server Side Request Forgery (through use of an external Wapiti website)
- Open Redirects
- Detection of uncommon HTTP methods (like PUT)
- Basic CSP Evaluator
- Brute Force login form (using a dictionary list)
- Checking HTTP security headers
- Checking cookie security flags (secure and httponly flags)
- Cross Site Request Forgery (CSRF) basic detection
- Fingerprinting of web applications using the Wappalyzer database, gives related CVE information
- Enumeration of CMS modules for Wordpress, Drupal, Joomla, SPIP, etc
- Subdomain takeovers detection
- Log4Shell (CVE-2021-44228) detection
- Spring4Shell (CVE-2020-5398) detection
- Check https redirections
- Check for file upload vulnerabilities
- Detection of network devices
- Inject payloads inside JSON body too

Wapiti supports both GET and POST HTTP methods for attacks. It also supports multipart and can inject payloads in filenames (upload). Display a warning when an anomaly is found (for example 500 errors and timeouts) Makes the difference between permanent and reflected XSS vulnerabilities.

## Module names

[](https://github.com/wapiti-scanner/wapiti#module-names)

The aforementioned attacks are tied to the following module names :

- backup (Search copies of scripts and archives on the web server)
- brute_login_form (Brute Force login form using a dictionary list)
- buster (DirBuster like module)
- cms (Scan to detect CMS and their versions)
- cookieflags (Checks Secure and HttpOnly flags)
- crlf (CR-LF injection in HTTP headers)
- csp (Detect lack of CSP or weak CSP configuration)
- csrf (Detects forms not protected against CSRF or using weak anti-CSRF tokens)
- exec (Code execution or command injection)
- file (Path traversal, file inclusion, etc)
- htaccess (Misconfigured htaccess restrictions)
- htp (Identify web technologies used the HashThePlanet database)
- http_header (Check HTTP security headers)
- https_redirect (Check https redirections)
- ldap (Error-based and boolean-based LDAP injection detection)
- log4shell (Detects websites vulnerable to CVE-2021-44228)
- methods (Look for uncommon available HTTP methods like PUT)
- network_device (Look for common files to detect network devices)
- nikto (Look for known vulnerabilities by testing URL existence and checking responses)
- permanentxss (Rescan the whole target after the xss module execution looking for previously tainted payloads)
- redirect (Open Redirects)
- shellshock (Test Shellshock attack, see [Wikipedia](https://en.wikipedia.org/wiki/Shellshock_%28software_bug%29))
- spring4shell (Detects websites vulnerable to CVE-2020-5398)
- sql (Error-based and boolean-based SQL injection detection)
- ssl (Evaluate the security of SSL/TLS certificate configuration, requires [sslscan](https://github.com/rbsec/sslscan))
- ssrf (Server Side Request Forgery)
- takeover (Subdomain takeover)
- timesql (SQL injection vulnerabilities detected with time-based methodology)
- upload (File upload vulnerabilities)
- wapp (Not an attack module, retrieves web technologies with versions and categories in use on the target, find corresponding CVEs)
- wp_enum (Enumerate plugins and themes on a Wordpress website)
- xss (XSS injection module)
- xxe (XML External Entity attack)

Module names can be given as comma separated list using the "-m" or "--module" option.

## How to get the best results

[](https://github.com/wapiti-scanner/wapiti#how-to-get-the-best-results)

To find more vulnerabilities (as some attacks are error-based), you can modify your webserver configurations.

For example, you can set the following values in your PHP configuration :

safe_mode = Off
display_errors = On (recommended)
magic_quotes_gpc = Off
allow_url_fopen = On
mysql.trace_mode = On

## Where to get help

[](https://github.com/wapiti-scanner/wapiti#where-to-get-help)

In the prompt, just type the following command to get the basic usage :

> wapiti -h

You can also take a look at the manpage (wapiti.1 or wapiti.1.html) for more details on each option.

If you have another question, first check the [FAQ](https://github.com/wapiti-scanner/wapiti/blob/master/doc/FAQ.md)

If you find a bug, fill an issue : [https://github.com/wapiti-scanner/wapiti/issues](https://github.com/wapiti-scanner/wapiti/issues)

The official wiki can be helpful too : [https://sourceforge.net/p/wapiti/wiki/browse_pages/](https://sourceforge.net/p/wapiti/wiki/browse_pages/)

## How to help the Wapiti project

[](https://github.com/wapiti-scanner/wapiti#how-to-help-the-wapiti-project)

You can :

- Support the project by making a donation ( [http://sf.net/donate/index.php?group_id=168625](http://sf.net/donate/index.php?group_id=168625) )
- Create or improve attack modules
- Create or improve report generators and templates
- Send bugfixes, patches...
- Write some GUIs
- Create a tool to convert PCAP files to Wapiti sqlite3 session files
- Talk about Wapiti around you

## Licensing

[](https://github.com/wapiti-scanner/wapiti#licensing)

Wapiti is released under the GNU General Public License version 2 (the GPL). Source code is available on [Github](https://github.com/wapiti-scanner/wapiti).

Created by Nicolas SURRIBAS.

## Sponsors

[](https://github.com/wapiti-scanner/wapiti#sponsors)

Cyberwatch [https://cyberwatch.fr/](https://cyberwatch.fr/)

Security For Everyone [https://securityforeveryone.com/](https://securityforeveryone.com/)

## Disclaimer

[](https://github.com/wapiti-scanner/wapiti#disclaimer)

Wapiti is a cybersecurity software. It performs security assessments on a provided target, which can lead to malfunctions and crashes on the target, as well as potential data loss.

Usage of Wapiti for attacking a target without prior consent of its owner is illegal. It is the end user's responsibility to obey all applicable local laws.

Developers and people involved in the Wapiti project assume no liability and are not responsible for any misuse or damage caused by this program.

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/wapiti-scanner/wapiti). Be sure to check out the original post for more details.

  
![](https://wapiti-scanner.github.io/wapiti_400.png)

  

# The web-application vulnerability scanner

  

Wapiti allows you to audit the security of your websites or web applications.

It performs "black-box" scans (it does not study the source code) of the web application by crawling the webpages of the deployed webapp, looking for scripts and forms where it can inject data.

Once it gets the list of URLs, forms and their inputs, Wapiti acts like a [fuzzer](http://en.wikipedia.org/wiki/Fuzzing), injecting payloads to see if a script is vulnerable.

### What's new in Wapiti 3.1.8 ? Take a look [here](https://github.com/wapiti-scanner/wapiti/blob/master/doc/ChangeLog_Wapiti).

Wapiti modules cover:

- SQL Injections (Error based, boolean based, time based) and XPath Injections
- Cross Site Scripting (XSS) reflected and permanent
- File disclosure detection (local and remote include, require, fopen, readfile...)
- Command Execution detection (eval(), system(), passtru()...)
- XXE (Xml eXternal Entity) injection
- CRLF Injection
- Search for potentially dangerous files on the server (thanks to the Nikto db)
- Bypass of weak htaccess configurations
- Search for copies (backup) of scripts on the server
- Shellshock
- Folder and file enumeration (DirBuster like)
- Server Side Request Forgery (through use of an external Wapiti website)
- Open Redirects
- Detection of uncommon HTTP methods (like PUT)
- Basic CSP Evaluator
- Brute Force login form (using a dictionary list)
- Checking HTTP security headers
- Checking cookie security flags (secure and httponly flags)
- Cross Site Request Forgery (CSRF) basic detection
- Fingerprinting of web applications using the Wappalyzer database
- Enumeration of Wordpress and Drupal modules
- Detection of subdomain takeovers vulnerabilities
- Log4Shell vulnerability detection (CVE-2021-44228)
- Check for TLS misconfiguration and vulnerabilities (thanks to SSLyze)

Wapiti supports both GET and POST HTTP methods for attacks.  
It also supports multipart forms and can inject payloads in filenames (upload).  
Warnings are raised when an anomaly is found (for example 500 errors and timeouts)  
Wapiti is able to make the difference between permanent and reflected XSS vulnerabilities.  

General features :

- Generates vulnerability reports in various formats (HTML, XML, JSON, TXT, CSV)
- Can suspend and resume a scan or an attack (session mechanism using sqlite3 databases)
- Can give you colors in the terminal to highlight vulnerabilities
- Different levels of verbosity
- Fast and easy way to activate/deactivate attack modules
- Adding a payload can be as easy as adding a line to a text file
- Configurable number of concurrent tasks to perform HTTP requests

Browsing features

- Support HTTP, HTTPS and SOCKS5 proxies
- Authentication via several methods : Basic, Digest, NTLM or GET/POST on login forms
- Ability to restrain the scope of the scan (domain, folder, page, url)
- Automatic removal of one are more parameters in URLs
- Multiple safeguards against scan endless-loops (for example, limit of values for a parameter)
- Possibility to set the first URLs to explore (even if not in scope)
- Can exclude some URLs of the scan and attacks (eg: logout URL)
- Import cookies from your Chrome or Firefox browser or using the wapiti-getcookie tool
- Can activate / deactivate SSL certificates verification
- Extract URLs from Flash SWF files
- HTML5 aware (understand recent HTML tags)
- Several options to control the crawler behavior and limits.
- Skipping some parameter names during attack.
- Setting a maximum time for the scan process.
- Adding some custom HTTP headers or setting a custom User-Agent.
- Man-In-The-Middle proxy support to explore the target by using your browser
- Automated browsing using Firefox in headless mode

Wapiti is a command-line application.  
Here is [an example of output](https://wapiti-scanner.github.io/example.txt) against a vulnerable web application.  
You may find some useful information in the [README](https://github.com/wapiti-scanner/wapiti/blob/master/README.rst) and the [INSTALL](https://github.com/wapiti-scanner/wapiti/blob/master/INSTALL.md) files.  
Have any questions ? You may find answers in the [FAQ](https://github.com/wapiti-scanner/wapiti/blob/master/doc/FAQ.md).

## Download

[>> Download Wapiti here <<](https://github.com/wapiti-scanner/wapiti/releases)

  

or install it easily using PIP:

pip install wapiti3

## Usage

 ██╗    ██╗ █████╗ ██████╗ ██╗████████╗██╗██████╗
 ██║    ██║██╔══██╗██╔══██╗██║╚══██╔══╝██║╚════██╗
 ██║ █╗ ██║███████║██████╔╝██║   ██║   ██║ █████╔╝
 ██║███╗██║██╔══██║██╔═══╝ ██║   ██║   ██║ ╚═══██╗
 ╚███╔███╔╝██║  ██║██║     ██║   ██║   ██║██████╔╝
  ╚══╝╚══╝ ╚═╝  ╚═╝╚═╝     ╚═╝   ╚═╝   ╚═╝╚═════╝
Wapiti 3.1.8 (wapiti-scanner.github.io)
usage: wapiti [-h] [-u URL] [--swagger URI] [--data data]
              [--scope {url,page,folder,subdomain,domain,punk}] [-m MODULES_LIST]
              [--list-modules] [-l LEVEL] [-p PROXY_URL] [--tor] [--mitm-port PORT]
              [--headless {no,hidden,visible}] [--wait TIME] [-a CREDENTIALS]
              [--auth-user USERNAME] [--auth-password PASSWORD]
              [--auth-method {basic,digest,ntlm}] [--form-cred CREDENTIALS]
              [--form-user USERNAME] [--form-password PASSWORD] [--form-url URL]
              [--form-data DATA] [--form-enctype DATA] [--form-script FILENAME]
              [-c COOKIE_FILE] [--drop-set-cookie] [--skip-crawl] [--resume-crawl]
              [--flush-attacks] [--flush-session] [--store-session PATH]
              [--store-config PATH] [-s URL] [-x URL] [-r PARAMETER]
              [--skip PARAMETER] [-d DEPTH] [--max-links-per-page MAX]
              [--max-files-per-dir MAX] [--max-scan-time SECONDS]
              [--max-attack-time SECONDS] [--max-parameters MAX] [-S FORCE]
              [--tasks tasks] [--external-endpoint EXTERNAL_ENDPOINT_URL]
              [--internal-endpoint INTERNAL_ENDPOINT_URL] [--endpoint ENDPOINT_URL]
              [--dns-endpoint DNS_ENDPOINT_DOMAIN] [-t SECONDS] [-H HEADER] [-A AGENT]
              [--verify-ssl {0,1}] [--color] [-v LEVEL] [--log OUTPUT_PATH]
              [-f FORMAT] [-o OUTPUT_PATH] [-dr DETAILED_REPORT_LEVEL]
              [--no-bugreport] [--update] [--version] [--cms CMS_LIST]
              [--wapp-url WAPP_URL] [--wapp-dir WAPP_DIR]

Shortest way (with default options) to launch a Wapiti scan :

wapiti -u http://target/

Every option is detailed in the [wapiti(1) manpage](https://github.com/wapiti-scanner/wapiti/blob/master/doc/wapiti.ronn).

Wapiti also comes with a utility to fetch cookies from websites called wapiti-getcookie. The corresponding manpage is [here](https://github.com/wapiti-scanner/wapiti/blob/master/doc/wapiti-getcookie.ronn).

  

## Licensing

Wapiti is released under the [GNU General Public License version 2 (the GPL).](https://www.gnu.org/licenses/gpl-2.0.html)

## Sponsors

  [![Cyberwatch](https://wapiti-scanner.github.io/sponsors/logo_cyberwatch.jpg)](https://cyberwatch.fr/)

  [![Security For Everyone](https://wapiti-scanner.github.io/sponsors/s4e-logo.png)](https://securityforeveryone.com/)

**Credit:** This information was adapted from an excellent guide on [Wapiti-Scanner.Github.io](https://wapiti-scanner.github.io/). Be sure to check out the original post for more details.

# Complete Guide to Using Wapiti Web Vulnerability Scanner to Keep Your Web Applications & Websites Secure

Globally, there are roughly 30,000 web-based cyberattacks daily, primarily targeting smaller businesses and smaller websites. To put it into perspective, that is an estimated 1 cyberattack every 3 seconds that targets websites specifically.

Cybercriminals will not hesitate to attack your website, so how can you possibly find any security issues and entry points? The answer is simple: Website Vulnerability Scanners. Follow along with us as we take a look at what a Vulnerability Scanner is and how we use WAPITI Web Scanner to test some websites. 

## What is a Website Vulnerability Scanner? Do YOU Need It?

Before we get into WAPITI Scanner, let's define a Website vulnerability and how a Website Vulnerability Scanner can help you. A website vulnerability is a flaw or vulnerability in the code of a website or web application that allows cybercriminals to gain control of the site and possibly even the web hosting server. Cybercriminals have gone so far as to write scripts that scrape the web for specific platforms in search of familiar and publicized vulnerabilities that they can exploit to steal information, access confidential documents or data, spam the site, or even inject scripts. If these attacks are successful, cybercriminals can cause irreparable damage to a business's hardware and public image, as well as raise questions about whether that company has the resources to keep their data secure, as well as the data of potential future clients.

Understanding and preventing website vulnerabilities is especially important for any business or corporate institution that maintains or plans to maintain a website or web application. A website vulnerability scanner is designed to look for these security flaws in a website. It searches for flaws in web services and web servers. Because cybercriminals are quick to exploit these vulnerabilities, you should be implementing regular use of a web scanner as well. Routine web vulnerability testing will allow you to patch security flaws before cyber attackers can manipulate them. These scanners simply examine the application's code for web flaws like SQL injections, cross-site scripting (XSS), and path traversal.

×

![Image](https://linuxsecurity.com/images/2021/11/05/penguine-icon.png)

## Subscribe to Our Linux Advisory Watch Newsletter!

Stay one step ahead of attackers - Be the first to know about the latest security vulnerabilities and updates impacting your Linux systems.

[Sign Up & Stay Safe!](https://linuxsecurity.com/newsletter-subscribe)

## Wapiti Scanner: Brief Description

Wapiti gives you the ability to audit the security of your web apps. It performs "black-box" scans, which means it does not examine the application's source code but instead scans the deployed web app's webpages for scripts and forms into which it can inject data. Wapiti then acts like a fuzzer, injecting payloads to see if a script is vulnerable.

## Watch: Wapiti Web Vulnerability Scanner - Review + Test

##  

## Wapiti Features

### Main Scanning Features:

#### SQL Injections (Error based, boolean-based, time-based) and XPath Injections

SQL Injection is a type of injection attack that makes it possible to execute malicious SQL statements that can control a database server behind web applications. Attackers can use SQL Injection vulnerabilities to bypass application security measures. Scanning for SQLi vulnerabilities is a must to make sure that important information is not accessed and to furthermore, be able to reinforce your server to mitigate SQL injection attacks.

XPath injections are attacks where malicious user input can be used to grant unauthorized access or reveal sensitive information such as XML document structure and content. These attacks are carried out by making the user's input be used in the construction of the query string. XPath Injection scans check how your server handles malicious XPath queries. If the scan does not return information on vulnerabilities, it will be considered secure.

#### Cross-Site Scripting (XSS) reflected and permanent

Cross-site scripting targets an application's users by injecting code, usually a client-side script such as JavaScript, into a web application's output. The concept of XSS is to manipulate client-side scripts of a web application to execute in the manner desired by the attacker. XSS allows attackers to execute scripts in the victim's browser which can hijack user sessions, deface websites or redirect the user to malicious sites.

#### Cross-Site Request Forgery (CSRF) basic detection

Cross-Site Request Forgery is a malicious attack where a user is tricked into performing an action he or she didn't intend to do. A third-party website will send a request to a web application that a user is already authenticated against (e.g. their bank). The attacker can then access functionality via the victim's already authenticated browser. Targets include web applications like social media, in browser email clients, online banking, and web interfaces for network devices.

#### CRLF Injection

CRLF injection attacks are one of several types of injection attacks. It can be used to extend more malicious attacks such as cross-site scripting, page injection, cache poisoning, and cache-based tampering. A CRLF injection attack occurs when Cyber Criminals are able to inject CRLF characters into a web application. The most common use for CRLF injection attacks is log poisoning, where the Cyber Criminal forges log file entries which ultimately, can be used to hide other attacks or confuse system administrators. Although CRLF isn’t amongst the most commonly known web vulnerabilities, it is still a big threat. Due to the fact that CRLF injections are used to hide and escalate possibly stronger and potentially more dangerous attacks, it is best to use a scanner to help mitigate the exploitation of this vulnerability.

#### XXE (Xml eXternal Entity) injection

An XML External Entity attack is an attack that abuses a widely available but rarely used feature of XML parsers. Using XXE, Cyber Criminals are able to cause Denial of Service attacks on top of being able to access local and remote content and services. XXE can be used to perform Server Side Request Forgery forcing the web application to make requests to other applications. Furthermore, XXE may even enable port scanning and lead to remote code execution. There are two types of XXE attacks: in-band and out-of-band. Cyber Criminals can use XML entities to cause a denial of service by embedding entities within entities within entities.

### Other Scanning Features:

- File disclosure detection (local and remote include, require, fopen, readfile...)
- Command Execution detection (eval(), system(), passtru())
- Search for potentially dangerous files on the server
- Bypass of weak htaccess configurations
- Search for copies (backup) of scripts on the server
- Shellshock
- Folder and file enumeration
- Server Side Request Forgery
- Open Redirects
- Detection of uncommon HTTP methods
- Basic CSP Evaluator
- Brute Force login form
- Checking HTTP security headers
- Checking cookie security flags
- Fingerprinting of web applications using the Wappalyzer database
- Enumeration of Wordpress and Drupal modules
- Subdomain takeovers detection
- Log4Shell (CVE-2021-44228) detection

Wapiti supports both GET and POST HTTP methods for attacks. It also supports multipart and can inject payloads in filenames. Furthermore, Wapiti displays a warning when an anomaly is found which makes the difference between permanent and reflected XSS vulnerabilities.

## How to Install Wapiti for Linux Distributions:

With root permission, update the apt database with apt-get using the command:

root@server:~# apt-get update 

### Kali Linux and Ubuntu Installation:

root@kali:~# apt-get install wapiti 

### Debian Installation:

root@debian:~# apt -y install wapiti

### UNIX-like Systems Installation:

**Prerequisites:** Packages must be updated and Python must be installed. Run the command

apt-get install python3 **OR** apt-get install python

Let's grab the most recent Wapiti tar file from their page using this command below:

root@kali:~# wget githubusercontent 

Lets extract the tar file from our download using this command below: 

root@kali:~# tar  -xzvf  wapiti3-3.1.2.tar.gz 

Extracting the tar file will create a directory in the directory in which you downloaded and extracted the tar file. Below, lets change to that directory using the cd command: 

root@kali:~# cd wapiti3-3.1.2/

We should now be in the wapiti3-3.1.2 directory. If we run the ls command, we should see the contents of the directory: 

root@kali:~/wapiti3-3.1.2# ls

Bin INSTALL.md MANIFEST.in README.rst setup.py wapiti3.egg-info

Doc LICENSE    PKG-INFO    setup.cfg  VERSION  wapitiCore

We should now be able to install Wapiti by running the command python3 setup.py install just like below:

root@server:~/wapiti3-3.1.2# python3 setup.py install

## Wapiti Help:

For this instance, I used Kali Linux. Run the command wapiti -h to pull up a list of arguments that wapiti accepts. 

![Help Esm W700](https://linuxsecurity.com/images/articles/features/Help-esm-w700.webp)

## Wapiti in Action:

For this instance, I will be using Kali Linux. Let’s use Wapiti to test Two sites, one that is generally considered secure and one that is vulnerable. Run the command below, substituting the proper url:

root@kali:~# wapiti -v2 -u https://monsterhost.com/promo/

## Google.com Test:

For this example, we ran this command against [Google](https://www.google.com/ "Google"). This is what wapiti will output:

![Google Test Esm W700](https://linuxsecurity.com/images/articles/features/google_test-esm-w700.webp)

As you can see in the example above, we ran wapiti in verbose mode and it generated a report in html format. We use open /path/to/file to open the html file in a web browser. Below is what that looks likes:

![Wapiti Vuln Report Esm W700](https://linuxsecurity.com/images/articles/features/wapiti_vuln_report-esm-w700.webp)

From this generated report, we see that we have a possible vulnerability with Content Security Policy Configuration. As you can see, the issue is with our CSP which helps mitigate and detect attacks such as XSS. Keep following along below to see the solution wapiti returns:

![Csp Conf Google Esm W700](https://linuxsecurity.com/images/articles/features/csp_conf_google-esm-w700.webp)

The solution above is provided by wapiti. Rather than a solution, it is more of a highly recommended suggestion that you can choose to heed or not. Configuring our CSP would allow for better deterrence of attacks.

### HTTP Flag Cookie:

![Httponly Google Esm W700](https://linuxsecurity.com/images/articles/features/httponly_google-esm-w700.webp)

In the image above, we also see that we receive a vulnerability with the HTTPOnly Flag cookie. The HttpOnly flag is not set to true in this instance. Setting it to true will help mitigate the risk of client side scripts accessing protected cookies.

### Secure Headers Error:

![Secureheadersgoogle Esm W700](https://linuxsecurity.com/images/articles/features/secureheadersgoogle-esm-w700.webp)

In the image above, we also see that we receive a vulnerability stating it is an HTTP Secure Headers Error. Modern browsers support many HTTP headers that can improve web application security to protect against clickjacking, cross-site scripting, and other common attacks. Wapiti refers to some links that will help in hardening your web applications.

## Mutillidae Test:

For this example, we ran this command against Mutillidae, a deliberately vulnerable web application. Whilst running, wapiti will show you real-time the tests it is running like below:

### ![MutillidaeWapiti XSS Vulnerablity Terminal Esm W700](https://linuxsecurity.com/images/articles/features/MutillidaeWapiti_XSS_vulnerablity_terminal-esm-w700.webp)

In the image above, whilst wapiti was running tests, it found an XSS Vulnerability. In the image below, it found a SSRF vulnerability:

![MutillidaeWapiti SSRF Vulnerablity Terminal Esm W700](https://linuxsecurity.com/images/articles/features/MutillidaeWapiti_SSRF_vulnerablity_terminal-esm-w700.webp)

When wapiti is all finished with its scans, this is what it will output:

![Mutillidae Wapiti Run Output Esm W700](https://linuxsecurity.com/images/articles/features/Mutillidae_wapiti_run_output-esm-w700.webp)

As you can see in the example above, we ran wapiti in verbose mode and it generated a report in html format. We use open /path/to/file to open the html file in a web browser. Below is what that looks like:

![Initial Html Report Mutillidae Esm W700](https://linuxsecurity.com/images/articles/features/Initial_html_report_Mutillidae-esm-w700.webp)

From this generated report, we see that we have possible vulnerabilities with Content Security Policy Configuration. As you can see, the issue is with our CSP which helps mitigate and detect attacks such as XSS. Keep following along below to see the solution wapiti returns:

![Mutillidae CSP IssueSolution Esm W700](https://linuxsecurity.com/images/articles/features/Mutillidae_CSP_IssueSolution-esm-w700.webp)

 The solution above is provided by wapiti. Rather than a solution, it is more of a highly recommended suggestion that you can choose to heed or not. The CSP is not set; configuring our CSP would allow for better deterrence of attacks.

## Path Traversal:

![Mutillidae Path Traversal Esm W700](https://linuxsecurity.com/images/articles/features/Mutillidae_Path_Traversal-esm-w700.webp)

A path traversal vulnerability allows Cyber Criminals to access files on your web server to which they should not have access. They do this by tricking either the web server or the web application running on it into returning files that exist outside of the web root folder. Using code access policies and chrooted jails along with using file path code to prevent users from entering the full path, we can fix thesen vulnerabilities.

### HTTPOnly Flag Cookie:

![Flag Cookie Mutillidae Esm W700](https://linuxsecurity.com/images/articles/features/Flag_Cookie_Mutillidae-esm-w700.webp)

In the image above, we also see that we receive a vulnerability with the HTTPOnly Flag cookie. The HttpOnly flag is not set to true in this instance. Setting it to true will help mitigate the risk of client-side scripts accessing protected cookies as shown in the solution below:

![Flag Cookie Solution Esm W680](https://linuxsecurity.com/images/articles/features/Flag_Cookie_solution-esm-w680.webp)

### Secure Headers Error:

![Secure Headers Issue Esm W700](https://linuxsecurity.com/images/articles/features/Secure_Headers_Issue-esm-w700.webp)

In the image above, we also see that we receive a vulnerability stating it is an HTTP Secure Headers Error. Modern browsers support many HTTP headers that can improve web application security to protect against clickjacking, cross-site scripting, and other common attacks. Wapiti refers to some links that will help in hardening your web applications like below:

![Secure Headers Solution Esm W700](https://linuxsecurity.com/images/articles/features/Secure_Headers_Solution-esm-w700.webp)

## SQL Injection (SQLi):

![Sqlinjection Esm W700](https://linuxsecurity.com/images/articles/features/sqlinjection-esm-w700.webp)

SQL injection attacks allow CyberCriminals to spoof identity, tamper with existing data, destroy the data or make it otherwise unavailable, and possibly, even become administrators of the database server. Scanning for possible SQLi vulnerabilities will help prevent your database from possibly taking over. As you can see above, Wapiti even provides us with a solution: User input must not directly be embedded in SQL statements. Instead, user input must be escaped or filtered or parameterized statements must be used. Depending on the company, getting this information to the proper team is essential to get it resolved.

## Server Side Request Forgery (SSRF):

![SSRF Report Esm W700](https://linuxsecurity.com/images/articles/features/SSRF_report-esm-w700.webp)

### Solution:

![SSRF Solution Esm W700](https://linuxsecurity.com/images/articles/features/SSRF_solution-esm-w700.webp)

SSRF allows attackers to carry out scans and collect information about internal networks. Once an attacker has gained access to the server, they can use this information to compromise other servers within the network. Quite a few breaches within the past couple years such as Capital One and MS Exchange have all included SSRF attacks.

SSRF vulnerabilities allow CyberCriminals to send requests from the back-end server of the web application and they do this to target internal systems that are behind firewalls and are not accessible externally. Scanning against SSRF will aide in mitigating these attacks and hopefully, keeping your system secure. Wapiti provides us with a solution as shown above. The more frequently you scan, the closer we are to avoiding another Capital One-like instance.

## Cross-Site Scripting (XSS):

![XSS Vuln Esm W700](https://linuxsecurity.com/images/articles/features/XSS_vuln-esm-w700.webp)

### Solution:

![XSS Sol Esm W700](https://linuxsecurity.com/images/articles/features/XSS_Sol-esm-w700.webp)

Cross-site scripting works by manipulating a vulnerable website so that it returns malicious JavaScript to users. Cybercriminals can fully compromise users interaction with web applications by executing this malicious Javascript code/scripts. The way to ensure that you, your users, and your web app are safe is to ensure that the application does checking and validation of headers, cookies, query string, forms, and hidden field. Moreover, encoding user output can help mitigate these types of attacks.

## Wapiti Summary

Wapiti is a well-known tool that is widely used amongst security researchers, regular users, and even System Administrators. As Cyber Criminals continue to exploit new found vulnerabilities and even existing ones due to poor security management, Wapiti is the perfect solution to auditing your website and webservers. The commands and arguments are fairly simple to use, it is a powerful tool, and the report provided in HTML format allows for any user to see urgent issues and their possible solutions without having to sit, search, and create a solution. It provides you with a baseline understanding of your vulnerabilities and a baseline path to a solution.

## Our Thoughts

Web applications are the technological base of modern companies. That’s why more and more businesses and corporate institutions are looking to monitor their websites and web apps more often and wapiti is the perfect tool to do so. It is amongst many well-known web vulnerability scanners and can play an essential role in assisting daily users and System Administrators alike to deter attacks. 

We hope you found this article useful! Be sure to stay tuned for more tips and advice on Linux security tools.

**Credit:** This information was adapted from an excellent guide on [LinuxSecurity](https://linuxsecurity.com/features/complete-guide-to-using-wapiti-web-vulnerability-scanner-to-keep-your-web-applications-websites-secure). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/xv_-rL84ZZ8?si=OCggjanuHax0BJid" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=xv_-rL84ZZ8). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/5q8B1aaYl7o?si=n_pgyyaB9S61yudu" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=5q8B1aaYl7o). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/ikiMS0gCDiI?si=pbXTNvMzRwUZT4xA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=ikiMS0gCDiI). Be sure to check out the original post for more details.

