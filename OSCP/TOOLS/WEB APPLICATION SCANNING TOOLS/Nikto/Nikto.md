# nikto

[](https://github.com/sullo/nikto#nikto)

[![alt text](https://camo.githubusercontent.com/dac70506d1f5f29398d3a5a597dd29badde2a93bda0d1fea8167aa80860e4bab/68747470733a2f2f636972742e6e65742f696d616765732f70617472656f6e2e706e67 "Become a patron of Nikto!")](https://www.patreon.com/sullo)

Nikto web server scanner - [https://cirt.net/Nikto2](https://cirt.net/Nikto2)

Full documentation - [https://github.com/sullo/nikto/wiki](https://github.com/sullo/nikto/wiki)

Run normally:

```
git clone https://github.com/sullo/nikto
# Main script is in program/
cd nikto/program
# Run using the shebang interpreter
./nikto.pl -h http://www.example.com
# Run using perl (if you forget to chmod)
perl nikto.pl -h http://www.example.com
```

Run as a Docker container:

```shell
git clone https://github.com/sullo/nikto.git
cd nikto
docker build -t sullo/nikto .
# Call it without arguments to display the full help
docker run --rm sullo/nikto
# Basic usage
docker run --rm sullo/nikto -h http://www.example.com
# To save the report in a specific format, mount /tmp as a volume:
docker run --rm -v $(pwd):/tmp sullo/nikto -h http://www.example.com -o /tmp/out.json
```

Basic usage:

```
   Options:
       -ask+               Whether to ask about submitting updates
                               yes   Ask about each (default)
                               no    Don't ask, don't send
                               auto  Don't ask, just send
       -Cgidirs+           Scan these CGI dirs: "none", "all", or values like "/cgi/ /cgi-a/"
       -config+            Use this config file
       -Display+           Turn on/off display outputs:
                               1     Show redirects
                               2     Show cookies received
                               3     Show all 200/OK responses
                               4     Show URLs which require authentication
                               D     Debug output
                               E     Display all HTTP errors
                               P     Print progress to STDOUT
                               S     Scrub output of IPs and hostnames
                               V     Verbose output
       -dbcheck           Check database and other key files for syntax errors
       -followredirects   Follow 3xx redirects to new location
       -evasion+          Encoding technique:
                               1     Random URI encoding (non-UTF8)
                               2     Directory self-reference (/./)
                               3     Premature URL ending
                               4     Prepend long random string
                               5     Fake parameter
                               6     TAB as request spacer
                               7     Change the case of the URL
                               8     Use Windows directory separator (\)
                               A     Use a carriage return (0x0d) as a request spacer
                               B     Use binary value 0x0b as a request spacer
        -Format+           Save file (-o) format:
                               csv   Comma-separated-value
                               htm   HTML Format
                               msf+  Log to Metasploit
                               nbe   Nessus NBE format
                               txt   Plain text
                               xml   XML Format
                               (if not specified the format will be taken from the file extension passed to -output)
       -Help              Extended help information
       -host+             Target host
       -IgnoreCode        Ignore Codes--treat as negative responses
       -id+               Host authentication to use, format is id:pass or id:pass:realm
       -key+              Client certificate key file
       -list-plugins      List all available plugins, perform no testing
       -maxtime+          Maximum testing time per host
       -mutate+           Guess additional file names:
                               1     Test all files with all root directories
                               2     Guess for password file names
                               3     Enumerate user names via Apache (/~user type requests)
                               4     Enumerate user names via cgiwrap (/cgi-bin/cgiwrap/~user type requests)
                               5     Attempt to brute force sub-domain names, assume that the host name is the parent domain
                               6     Attempt to guess directory names from the supplied dictionary file
       -mutate-options    Provide information for mutates
       -nointeractive     Disables interactive features
       -nolookup          Disables DNS lookups
       -noslash           Strip trailing slash from URL (e.g., '/admin/' to '/admin')
       -nossl             Disables the use of SSL
       -no404             Disables nikto attempting to guess a 404 page
       -output+           Write output to this file ('.' for auto-name)
       -Pause+            Pause between tests (seconds, integer or float)
       -Plugins+          List of plugins to run (default: ALL)
       -port+             Port to use (default 80)
       -RSAcert+          Client certificate file
       -root+             Prepend root value to all requests, format is /directory
       -Save              Save positive responses to this directory ('.' for auto-name)
       -ssl               Force ssl mode on port
       -Tuning+           Scan tuning:
                               1     Interesting File / Seen in logs
                               2     Misconfiguration / Default File
                               3     Information Disclosure
                               4     Injection (XSS/Script/HTML)
                               5     Remote File Retrieval - Inside Web Root
                               6     Denial of Service
                               7     Remote File Retrieval - Server Wide
                               8     Command Execution / Remote Shell
                               9     SQL Injection
                               0     File Upload
                               a     Authentication Bypass
                               b     Software Identification
                               c     Remote Source Inclusion
                               x     Reverse Tuning Options (i.e., include all except specified)
       -timeout+          Timeout for requests (default 10 seconds)
       -Userdbs           Load only user databases, not the standard databases
                               all   Disable standard dbs and load only user dbs
                               tests Disable only db_tests and load udb_tests
       -until             Run until the specified time or duration
       -update            Update databases and plugins from CIRT.net
       -useproxy          Use the proxy defined in nikto.conf
       -usecookies        Use cookies from responses in future requests
       -Version           Print plugin and database versions
       -vhost+            Virtual host (for Host header)
              + requires a value
```

# License

[](https://github.com/sullo/nikto#license)

Copyright (C) 2001 Chris Sullo

This program is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation; version 2 of the License only.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program; if not, write to Free Software Foundation, 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA.

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/sullo/nikto). Be sure to check out the original post for more details.

Posted on [November 9, 2023](https://www.hackercoolmagazine.com/nikto-vulnerability-scanner-complete-guide/) by [kanishka10](https://www.hackercoolmagazine.com/author/kanishka10/)
# Nikto vulnerability scanner: Complete guide

Hello, aspiring ethical Hackers. This blogpost is a complete guide to Nikto vulnerability scanner. Nikto is a free command line web vulnerability scanner that scans web servers and detects over 6700 potentially dangerous files/CGIs, outdated server software, other vulnerabilities and misconfigurations. Nikto can also detect the installed software on the target web server. We will be running Nikto on Kali Linux as it is installed by default in Kali Linux. So let’s start.

==Let’s start with a version check (-Version)==

The “version” option of Nikto checks for the version of the software, plugins and database versions.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_37.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_37.jpg)

**==Checking Database (-dbcheck)==**

It’s always a good thing to check for any errors in the scan database before scanning. The “-dbcheck” option of Nikto checks the scan databases for any errors.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_35.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_35.jpg)

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_36.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_36.jpg)

**==The Host option (–host) (-h)==**

To scan a target using Nikto, first we need to specify a target. To set the target, we need to use the “host” option. This is shown below.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_1.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_1.jpg)

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_23456ab-481x1024.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_23456ab.jpg)

The target can be IP address of the webserver or URL of the website. This scan took 45 seconds to finish.

**==The Host option (–ssl)==**

To scan a website with HTTPS enabled with nikto, we can use the “SSL” option.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_6.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_6.jpg)

==The Port option (–port)==

By default, Nikto scans the default HTTP and HTTPS ports when specified. However, if the target web server is running on a custom port you can set Nikto to scan a different port by using the “port” option.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_7.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_7.jpg)

==Scanning for CGI directories (–Cgidirs)==

To scan for the presence of all CGI directories on the target webserver, the “cgidirs” option can be used.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_8.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_8.jpg)

You can specify a specific CGI directory to search or you can use “all” value to scan for all CGI directories on the target.

==What output you want Nikto to show? (–Display)==

To control the type and amount of output Nikto shows after finishing the scan, we can use the “Display” option. Here are the values that can be set for the Display option.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_9a.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_9a.jpg)

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_9.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_9.jpg)

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_10.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_10.jpg)

==How much time you want Nikto to spend on a scan? (–maxtime)==

Using the “maxtime” option, we can specify the maximum time to spend for scanning a target. This time can be specified in seconds.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_11.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_11.jpg)

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_12.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_12.jpg)

As you can see, the scan ended in 2 seconds while earlier the same scan took 45 seconds.

==Don’t look for names (-nolookup)==

The “nolookup” option specifies Nikto to not query for names when an IP address is specified.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_13.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_13.jpg)

==Don’t look for pages that are not there (–no404)==

The “no404” option specifies Nikto to disable “file not found” checking. This will reduce the total number of requests made to the target.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_14.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_14.jpg)

==Just discover the ports (–findonly)==

If you want to just find the HTTP(S) ports of a target without performing any security scan, you can use the “–findonly” option. Specifying this option allows Nikto to connect to HTTPS or HTTP ports and report the server header.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_15.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_15.jpg)

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_16.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_16.jpg)

==The Timeout option (–timeout)==

The “–timeout” option specifies time to wait before timing out a request. The default timeout of Nikto is 10 seconds.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_17.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_17.jpg)

==The Pause option (–Pause)==

By using “–Pause” option of Nikto, we can specify delay between each test Nikto performs.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_18.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_18.jpg)

==What if we have to authenticate? (–id)==

With the “-id” option you can use Nikto to perform basic authentication to the target.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_19.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_19.jpg)

==The tuning option (–tuning)==

With the “-Tuning” option, we can control the test that Nikto will use against a target. It can take the following values.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_21_a.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_21_a.jpg)

For example, this is how we test for misconfigured files on the target.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_24.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_24.jpg)

==See all Nikto plugins (–list-plugins)==

Nikto has lot of plugins that can be used against various targets. To view all these plugins, we can use the “–list-plugins” option.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_25.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_25.jpg)

==Use a particular plugin (–Plugins)==

To use a particular plugin, we can use the “Plugins” option. For example, let’s use the robots plugin as shown below.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_26-1.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_26-1.jpg)

==Can Nikto evade detection? (–evasion)==

While scanning, Nikto can use various techniques to evade [Intrusion Detection System](https://www.hackercoolmagazine.com/beginners-guide-to-ids-and-ips/) (IDS). The evasion techniques of Nikto are given below.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/NIkto_vulnerability_scanner_27a.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/NIkto_vulnerability_scanner_27a.jpg)

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_29.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_29.jpg)

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_30-3.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_30-3.jpg)

==Saving output (-o)==

Nikto can save the output of the scan in a file with the “output(-o)” as shown below.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_31-3.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_31-3.jpg)

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_32.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_32.jpg)

==Formats in which you can save output (-Format)==

You can save in different formats you like using the “-Format” option. Valid formats are csv, htm, txt and xml.

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_33.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_33.jpg)

[![](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_34.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/11/Nikto_vulnerability_scanner_34.jpg)

That is the complete guide for Nikto vulnerability scanner. If you have any questions bring them in the comments section.

**Credit:** This information was adapted from an excellent guide on [HackerCoolMagazine](https://www.hackercoolmagazine.com/nikto-vulnerability-scanner-complete-guide/). Be sure to check out the original post for more details.

## Nikto Cheat Sheet - Commands & Examples [∞](https://highon.coffee/blog/nikto-cheat-sheet/ "Permalink")

15 Mar 2023  (https://twitter.com/Arr0way)

- [What is Nikto](https://highon.coffee/blog/nikto-cheat-sheet/#what-is-nikto)
- [Nikto Installation](https://highon.coffee/blog/nikto-cheat-sheet/#nikto-installation)
    - [Nikto Update](https://highon.coffee/blog/nikto-cheat-sheet/#nikto-update)
    - [Main script is in program](https://highon.coffee/blog/nikto-cheat-sheet/#main-script-is-in-program)
    - [Check out the 2.5.0 branch](https://highon.coffee/blog/nikto-cheat-sheet/#check-out-the-250-branch)
    - [Run using the shebang interpreter](https://highon.coffee/blog/nikto-cheat-sheet/#run-using-the-shebang-interpreter)
    - [Run using perl (if you forget to chmod)](https://highon.coffee/blog/nikto-cheat-sheet/#run-using-perl-if-you-forget-to-chmod)
- [Nikto Scan Cheat Sheet](https://highon.coffee/blog/nikto-cheat-sheet/#nikto-scan-cheat-sheet)
- [Nikto Command Flags Sheet](https://highon.coffee/blog/nikto-cheat-sheet/#nikto-command-flags-sheet)
- [Nikto Example Commands](https://highon.coffee/blog/nikto-cheat-sheet/#nikto-example-commands)
    - [Nikto Scanning](https://highon.coffee/blog/nikto-cheat-sheet/#nikto-scanning)
    - [Nikto Using a Proxy](https://highon.coffee/blog/nikto-cheat-sheet/#nikto-using-a-proxy)
- [Nikto2 Features](https://highon.coffee/blog/nikto-cheat-sheet/#nikto2-features)
- [Document Changelog](https://highon.coffee/blog/nikto-cheat-sheet/#document-changelog)

## What is Nikto[](https://highon.coffee/blog/nikto-cheat-sheet/#what-is-nikto)

Nikto is an open-source web server scanner that performs comprehensive tests to identify potentially dangerous files/programs, outdated versions of servers, server configuration items, and installed web servers and software. It also supports LibWhisker’s anti-IDS methods to avoid detection. While not every check is a security issue, most are, and there are also info-only checks and checks for unknown items.

## Nikto Installation[](https://highon.coffee/blog/nikto-cheat-sheet/#nikto-installation)

```bash
git clone https://github.com/sullo/nikto
```

### Nikto Update[](https://highon.coffee/blog/nikto-cheat-sheet/#nikto-update)

cd into your nikto git clone directory:

```bash
git pull
```

### Main script is in program[](https://highon.coffee/blog/nikto-cheat-sheet/#main-script-is-in-program)

```bash
cd nikto/program
```

### Check out the 2.5.0 branch[](https://highon.coffee/blog/nikto-cheat-sheet/#check-out-the-250-branch)

```bash
git checkout nikto-2.5.0
```

### Run using the shebang interpreter[](https://highon.coffee/blog/nikto-cheat-sheet/#run-using-the-shebang-interpreter)

```bash
./nikto.pl -h http://www.foo.com
```

### Run using perl (if you forget to chmod)[](https://highon.coffee/blog/nikto-cheat-sheet/#run-using-perl-if-you-forget-to-chmod)

```bash
perl nikto.pl -h http://www.foo.com
```

- list element with functor item

## Nikto Scan Cheat Sheet[](https://highon.coffee/blog/nikto-cheat-sheet/#nikto-scan-cheat-sheet)

The following Nikto command usage for scanning a web application:

|Command|Description|
|---|---|
|`nikto -h http://foo.com`|Scans the specified host|
|`nikto -h http://foo.com -Tuning 6`|Uses a specific Nikto scan tuning level|
|`nikto -h http://foo.com -port 8000`|Scans the specified port|
|`nikto -h http://foo.com -ssl`|Scans for SSL vulnerabilities|
|`nikto -h http://foo.com -Format html`|Formats output in HTML|
|`nikto -h http://foo.com -output out.txt`|Saves the output to a file|

## Nikto Command Flags Sheet[](https://highon.coffee/blog/nikto-cheat-sheet/#nikto-command-flags-sheet)

The following Nikto commands allow for configuration of a Nikto scan:

|Option|Value|
|---|---|
|`-ask+`|`yes` Ask about each (default)<br><br>`no` Don't ask, don't send|
|`-Cgidirs+`|"none", "all", or values like "/cgi/ /cgi-a/"|
|`-config+`|Use this config file|
|`-Display+`|1 Show redirects<br><br>2 Show cookies received<br><br>3 Show all 200/OK responses<br><br>4 Show URLs which require authentication<br><br>D Debug output<br><br>E Display all HTTP errors<br><br>P Print progress to STDOUT<br><br>S Scrub output of IPs and hostnames<br><br>V Verbose output|
|`-dbcheck`|Check database and other key files for syntax errors|
|`-evasion+`|1 Random URI encoding (non-UTF8)<br><br>2 Directory self-reference (/./)<br><br>3 Premature URL ending<br><br>4 Prepend long random string<br><br>5 Fake parameter<br><br>6 TAB as request spacer<br><br>7 Change the case of the URL<br><br>8 Use Windows directory separator (\)<br><br>A Use a carriage return (0x0d) as a request spacer<br><br>B Use binary value 0x0b as a request spacer|
|`-Format+`|csv Comma-separated-value<br><br>htm HTML Format<br><br>msf+ Log to Metasploit<br><br>nbe Nessus NBE format<br><br>txt Plain text<br><br>xml XML Format<br><br>(if not specified the format will be taken from the file extension passed to -output)|
|`-Help`|Extended help information|
|`-host+`|Target host|
|`-IgnoreCode`|Ignore Codes--treat as negative responses|
|`-id+`|Host authentication to use, format is id:pass or id:pass:realm|
|`-key+`|Client certificate key file|
|`-list-plugins`|List all available plugins, perform no testing|
|`-maxtime+`|Maximum testing time per host|
|`-mutate+`|1 Test all files with all root directories<br><br>2 Guess for password file names<br><br>3 Enumerate user names via Apache (/~user type requests)<br><br>4 Enumerate user names via cgiwrap (/cgi-bin/cgiwrap/~user type requests)<br><br>5 Attempt to brute force sub-domain names, assume that the host name is the parent domain<br><br>6 Attempt to guess directory names from the supplied dictionary file|
|`-mutate-options`|Provide information for mutates|
|`-nointeractive`|Disables interactive features|
|`-nolookup`|Disables DNS lookups|
|`-nossl`|Disables the use of SSL|
|`-no404`|Disables nikto attempting to guess a 404 page|
|`-output+`|Write output to this file ('.' for auto-name)|
|`-Pause+`|Pause between tests (seconds, integer or float)|
|`-Plugins+`|List of plugins to run (default: ALL)|
|`-port+`|Port to use (default 80)|
|`-RSAcert+`|Client certificate file|
|`-root+`|Prepend root value to all requests, format is /directory|
|`-Save`|Save positive responses to this directory ('.' for auto-name)|
|`-ssl`|Force ssl mode on port|
|`-Tuning+`|1 Interesting File / Seen in logs<br><br>2 Misconfiguration / Default File<br><br>3 Information Disclosure<br><br>4 Injection (XSS/Script/HTML)<br><br>5 Remote File Retrieval - Inside Web Root<br><br>6 Denial of Service<br><br>7 Remote File Retrieval - Server Wide<br><br>8 Command Execution / Remote Shell<br><br>9 [SQL Injection](/penetration-testing/web-app/sql-injection/)<br><br>0 File Upload<br><br>a Authentication Bypass<br><br>b Software Identification<br><br>c Remote Source Inclusion<br><br>x Reverse Tuning Options (i.e., include all except specified)|
|`-timeout+`|Timeout for requests (default 10 seconds)|
|`-Userdbs`|Load only user databases, not the standard databases<br><br>all Disable standard dbs and load only user dbs<br><br>tests Disable only db_tests and load udb_tests|
|`-until`|Run until the specified time or duration|
|`-update`|Update databases and plugins from CIRT.net|
|`-useproxy`|Use the proxy defined in nikto.conf|
|`-Version`|Print plugin and database versions|
|`-vhost+`|Virtual host (for Host header)|

## Nikto Example Commands[](https://highon.coffee/blog/nikto-cheat-sheet/#nikto-example-commands)

### Nikto Scanning[](https://highon.coffee/blog/nikto-cheat-sheet/#nikto-scanning)

The following nikto commands allow you to run basic nikto scans against a web application.

|Command|Description|
|---|---|
|`nikto -h [target]`|Basic scan, no HTTP options.|
|`nikto -h [target] -Tuning [tuning]`|Scan with a specific tuning.|
|`nikto -h [target] -mutate [mutate]`|Scan with a specific mutation.|
|`nikto -h [target] -ssl`|Scan using SSL.|
|`nikto -h [target] -nointeractive`|Run the scan non-interactively.|

### Nikto Using a Proxy[](https://highon.coffee/blog/nikto-cheat-sheet/#nikto-using-a-proxy)

Using Nikto with a proxy such as Burp or another intercepting proxy.

|Command|Description|
|---|---|
|`-useproxy`|Enable usage of the HTTP/SOCKS proxy|
|`-noproxy`|Specify comma separated list of hosts not to use proxy for|
|`-proxyhost`|Hostname or IP address of the HTTP/SOCKS proxy|
|`-proxyport`|Port of the HTTP/SOCKS proxy|
|`-proxypass`|Password for the HTTP/SOCKS proxy|
|`-proxyuser`|Username for the HTTP/SOCKS proxy|

## Nikto2 Features[](https://highon.coffee/blog/nikto-cheat-sheet/#nikto2-features)

- SSL Support (Unix with OpenSSL or maybe Windows with ActiveState’s Perl/NetSSL)
- Full HTTP proxy support
- Checks for outdated server components
- Save reports in plain text, XML, HTML, NBE or CSV
- Template engine to easily customize reports
- Scan multiple ports on a server, or multiple servers via input file (including nmap output)
- LibWhisker’s IDS encoding techniques
- Easily updated via command line
- Identifies installed software via headers, favicons and files
- Host authentication with Basic and NTLM
- Subdomain guessing
- Apache and cgiwrap username enumeration
- Mutation techniques to “fish” for content on web servers
- Scan tuning to include or exclude entire classes of vulnerability checks
- Guess credentials for authorization realms (including many default id/pw combos)
- Authorization guessing handles any directory, not just the root directory
- Enhanced false positive reduction via multiple methods: headers, page content, and content hashing
- Reports “unusual” headers seen
- Interactive status, pause and changes to verbosity settings
- Save full request/response for positive tests
- Replay saved positive requests
- Maximum execution time per target
- Auto-pause at a specified time
- Checks for common “parking” sites

If you found this Nikto cheat sheet useful, please share it below.

## Document Changelog[](https://highon.coffee/blog/nikto-cheat-sheet/#document-changelog)

- **Last Updated:** 12/02/2024 (12th of February 2024)
- **Author:** Arr0way
- **Notes:** Checked syntax was current for latest version of Nikto.

**Credit:** This information was adapted from an excellent guide on [Highon.Coffee](https://highon.coffee/blog/nikto-cheat-sheet/). Be sure to check out the original post for more details.

# Nikto Tutorial

Running a [Nikto](https://www.cirt.net/nikto2/) web server scan is a straight forward process. Follow through this Nikto Tutorial to get an overview of what is involved. Start your web server testing with one of the most well known website / server testing tools. This is the same tool we use in our hosted [Nikto scanner](https://hackertarget.com/nikto-website-scanner/) service.

**Nikto** is a `perl` based security testing tool and this means it will run on most operating systems with the necessary Perl interpreter installed. We will guide you through using it on Ubuntu Linux, basically because it is our operating system of choice and it just works. Perl comes already installed in Ubuntu. So it is a matter of downloading the tool, unpacking it and running the command with the necessary options. For Windows users running **Nikto** will involve installing a perl environment (activestate perl) or loading up a Linux virtual machine using [Virtualbox](https://www.virtualbox.org/wiki/Downloads) or [VMware](https://vmware.com/).

![Nikto logo](https://hackertarget.com/wp-content/uploads/2018/06/nikto.png)

If you are running Microsoft Windows as your main operating system you may find having a virtual machine with Kali Linux or Ubuntu will bring a number of benefits. For a starters it makes getting tools such as Nikto a very simple process, as well as develop some skills using Linux based operating system that will benefit all aspects of your security testing. The majority of free security testing tools are developed on and for Linux based systems. By using a virtual machine you can test Nikto and many other open source security tools without affecting your production workstation.

## Nikto Installation on Ubuntu

On a default installation of Ubuntu, launch a terminal and using a standard user account download the latest version of Nikto.

test@ubuntu:~$ wget https://github.com/sullo/nikto/archive/master.zip

You can unpack it with an archive manager tool or use tar and gzip together with this command.

test@ubuntu:~$ unzip master.zip
test@ubuntu:~$ cd nikto-master/program
test@ubuntu:~/nikto-master/program$ perl nikto.pl

You should see the following output after running `nikto.pl`This should be your results from a working installation:

test@ubuntu:~/nikto-master/program$ perl nikto.pl 
- Nikto v2.1.6
---------------------------------------------------------------------------
+ ERROR: No host or URL specified

       -config+            Use this config file
       -Display+           Turn on/off display outputs
       -dbcheck            check database and other key files for syntax errors
       -Format+            save file (-o) format
       -Help               Extended help information
       -host+              target host/URL
       -id+                Host authentication to use, format is id:pass or id:pass:realm
       -list-plugins       List all available plugins
       -output+            Write output to this file
       -nossl              Disables using SSL
       -no404              Disables 404 checks
       -Plugins+           List of plugins to run (default: ALL)
       -port+              Port to use (default 80)
       -root+              Prepend root value to all requests, format is /directory
       -ssl                Force ssl mode on port
       -Tuning+            Scan tuning
       -timeout+           Timeout for requests (default 10 seconds)
       -update             Update databases and plugins from CIRT.net
       -Version            Print plugin and database versions
       -vhost+             Virtual host (for Host header)
   		+ requires a value

	Note: This is the short help output. Use -H for full help text.

If there are any errors regarding **SSL** support it may be necessary to `apt install libnet-ssleay-perl`. Without [SSL/TLS](https://hackertarget.com/ssl-check/ "Online SSL/TLS Scan") support you will not be able to test sites over **HTTPS**.

## Starting a Nikto Web Scan

For a simple test we will use test a single host name. In the example below we are testing the virtual host (nikto-test.com) on 16x.2xx.2xx.1xx over HTTPS. The web server on the target responds to the Nikto tests as it would any request to the web server, we can see from the results that the target is a WordPress based site.

test@ubuntu:~/nikto-master/program$ perl nikto.pl -host https://nikto-test.com
- Nikto v2.1.6
---------------------------------------------------------------------------
+ Target IP:          16x.2xx.2xx.1xx
+ Target Hostname:    nikto-test.com
+ Target Port:        443
---------------------------------------------------------------------------
+ SSL Info:        Subject:  /CN=nikto-test.com
                   Altnames: nikto-test.com
                   Ciphers:  ECDHE-RSA-AES128-GCM-SHA256
                   Issuer:   /C=US/O=Let's Encrypt/CN=Let's Encrypt Authority X3
+ Start Time:         2018-06-26 12:03:53 (GMT10)
---------------------------------------------------------------------------
+ Server: nginx/1.4.6 (Ubuntu)
+ Retrieved x-powered-by header: PHP/5.5.9-1ubuntu4.22
+ The anti-clickjacking X-Frame-Options header is not present.
+ The X-XSS-Protection header is not defined. This header can hint to the user agent to protect against some forms of XSS
+ Uncommon header 'link' found, with multiple values: (; rel="https://api.w.org/",; rel=shortlink,)
+ The X-Content-Type-Options header is not set. This could allow the user agent to render the content of the site in a different fashion to the MIME type
+ No CGI Directories found (use '-C all' to force check all possible dirs)
+ Entry '/wp-admin/' in robots.txt returned a non-forbidden or redirect HTTP code (302)
+ "robots.txt" contains 2 entries which should be manually viewed.
+ The Content-Encoding header is set to "deflate" this may mean that the server is vulnerable to the BREACH attack.
+ 5567 items checked: 0 error(s) and 10 item(s) reported on remote host
+ End Time:           2018-06-25 11:14:46 (GMT0) (8129 seconds)
---------------------------------------------------------------------------
+ 1 host(s) tested

In the output we can see the items that were detected as interesting by Nikto. As well as the time taken for the scan and total number of items tested. If we review the web server logs we will be able to see the different items that were tested by the scanner.

## Nikto and the Web Server

Lets review the web server logs. An important thing to understand when testing a site with Nikto is the amount of noise that this creates in the web server log files. Essentially Nikto is testing for the presence of thousands of possible web paths, and checking the response from the web server - which for most items will be a **404 not found**.

Here is a sample from an Nginx web server being tested by Nikto.

203.xxx.xxx.xxx - - [25/Jun/2018:23:09:08 -0400] "GET /iissamples/sdk/asp/docs/Winmsdp.exe?Source=/IISSAMPLES/%c0%ae%c0%ae/default.asp HTTP/1.1" 404 16611 "-" "Mozilla/5.00 (Nikto/2.1.6) (Evasions:None) (Test:003021)"
203.xxx.xxx.xxx - - [25/Jun/2018:23:09:09 -0400] "GET /iissamples/exair/howitworks/Winmsdp.exe HTTP/1.1" 404 16611 "-" "Mozilla/5.00 (Nikto/2.1.6) (Evasions:None) (Test:003022)"
203.xxx.xxx.xxx - - [25/Jun/2018:23:09:10 -0400] "GET /%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5cwinnt%5cwin.ini HTTP/1.1" 404 16611 "-" "Mozilla/5.00 (Nikto/2.1.6) (Evasions:None) (Test:003023)"
203.xxx.xxx.xxx - - [25/Jun/2018:23:09:12 -0400] "GET /%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5cwinnt%5cwin.ini HTTP/1.1" 404 16611 "-" "Mozilla/5.00 (Nikto/2.1.6) (Evasions:None) (Test:003024)"
203.xxx.xxx.xxx - - [25/Jun/2018:23:09:13 -0400] "GET /conspass.chl+ HTTP/1.1" 404 16611 "-" "Mozilla/5.00 (Nikto/2.1.6) (Evasions:None) (Test:003025)"
203.xxx.xxx.xxx - - [25/Jun/2018:23:09:15 -0400] "GET /consport.chl+ HTTP/1.1" 404 16611 "-" "Mozilla/5.00 (Nikto/2.1.6) (Evasions:None) (Test:003026)"
203.xxx.xxx.xxx - - [25/Jun/2018:23:09:16 -0400] "GET /general.chl+ HTTP/1.1" 404 16611 "-" "Mozilla/5.00 (Nikto/2.1.6) (Evasions:None) (Test:003027)"
203.xxx.xxx.xxx - - [25/Jun/2018:23:09:18 -0400] "GET /srvstatus.chl+ HTTP/1.1" 404 16611 "-" "Mozilla/5.00 (Nikto/2.1.6) (Evasions:None) (Test:003028)"

Now unless your **intrusion detection** or server monitoring is broken, over **5000** of these sorts of hits in the web log will probably trigger a few alarms. Now it is very unlikely that these will cause an impact on the server, but it is certainly easy to spot. We can see the **Nikto User Agent** is in the log entry. Check the [documentation](https://cirt.net/nikto2-docs/) to change the user agent.

## Selecting the Target

Since the tool is checking for valid paths, it is important to remember that hitting a web server on different virtual host names, directly on the IP address and even on sub paths off the root of the site will give different results.

![](https://hackertarget.com/wp-content/uploads/2018/06/nikto-web-scan-target.png)

Lets take an example of PHPMyAdmin, this is a common tool for managing MySQL databases and can also be a good target for an attacker if it has not been patched or poorly managed. This application could be installed and available at `https://2xx.xxx.xxx.xxx/phpmyadmin/` or `https://mywebsite.com/phpmyadmin/` or `http://mywebsite.com/admin/phpmyadmin/`. So to find this application using Nikto we would have to target all three locations, and some servers might have hundreds of virtual hosts.

I am not suggesting running Nikto hundreds of times against every server, but consideration should be taken as to where to target the scan most effectively. Similar considerations come into play when performing simple file / directory brute forcing using Burp Suite or other web application testing tools.

**Further information** can be found in the documentation on the project page [https://cirt.net/nikto2-docs/installation.html](https://cirt.net/nikto2-docs/installation.html)

### Conclusion

Nikto continues to be an excellent web server testing tool, finding all sorts of obscure issues whether its directory indexing, admin panels or remote code execution in a rare web application. Take the time to run it and be surprised.

**Credit:** This information was adapted from an excellent guide on [HackerTarget](https://hackertarget.com/nikto-tutorial/). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/v_RM25kj_DY?si=KhKs8SXYc7r2HfgX" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=v_RM25kj_DY). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/ogUN8Nrr__g?si=45WjYaOpq9-lmO16" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=ogUN8Nrr__g). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/RaHDKCgx2Og?si=3oBySK2Uxz4uASdN" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=RaHDKCgx2Og). Be sure to check out the original post for more details.



