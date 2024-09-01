# EyeWitness

[](https://github.com/RedSiege/EyeWitness#eyewitness)

EyeWitness is designed to take screenshots of websites provide some server header info, and identify default credentials if known.

EyeWitness is designed to run on Kali Linux. It will auto detect the file you give it with the -f flag as either being a text file with URLs on each new line, nmap xml output, or nessus xml output. The --timeout flag is completely optional, and lets you provide the max time to wait when trying to render and screenshot a web page.

A complete usage guide which documents EyeWitness features and its typical use cases is available here - [https://www.christophertruncer.com/eyewitness-2-0-release-and-user-guide/](https://www.christophertruncer.com/eyewitness-2-0-release-and-user-guide/)

## Windows

[](https://github.com/RedSiege/EyeWitness#windows)

Red Siege has created a Windows client (thanks to the massive help of Matt Grandy (@Matt_Grandy_) with the stability fixes). All you need to do is build it locally (or check the releases), and then provide a path to a file containing the URLs you want scanned! EyeWitness will generate the report within your "AppData\Roaming" directory. The latest version of the C# EyeWitness supports parsing and taking screenshots of Internet Explorer and Chrome bookmarks without having to supply a list of URLs. This version is also small enough to be delivered through Cobalt Strike's execute-assembly.

### Setup:

[](https://github.com/RedSiege/EyeWitness#setup)

1. Navigate into the CS directory
2. Load EyeWitness.sln into Visual Studio
3. Go to Build at the top and then Build Solution if no modifications are wanted

### Usage:

[](https://github.com/RedSiege/EyeWitness#usage)

```shell
EyeWitness.exe --help
EyeWitness.exe --bookmarks
EyeWitness.exe -f C:\Path\to\urls.txt
EyeWitness.exe --file C:\Path\to\urls.txt --delay [timeout in seconds] --compress
```

## Linux

[](https://github.com/RedSiege/EyeWitness#linux)

###### Supported Linux Distros:

[](https://github.com/RedSiege/EyeWitness#supported-linux-distros)

- Kali Linux
- Debian 7+ (at least stable, looking into testing) (Thanks to @themightyshiv)
- CentOS 7
- Rocky Linux 8

**E-Mail:** GetOffensive [@] redsiege [dot] com

### Setup:

[](https://github.com/RedSiege/EyeWitness#setup-1)

1. Navigate into the Python/setup directory
2. Run the setup.sh script

### Usage:

[](https://github.com/RedSiege/EyeWitness#usage-1)

```shell
./EyeWitness.py -f filename --timeout optionaltimeout
```

### Examples:

[](https://github.com/RedSiege/EyeWitness#examples)

```shell
./EyeWitness -f urls.txt --web

./EyeWitness -x urls.xml --timeout 8 

./EyeWitness.py -f urls.txt --web --proxy-ip 127.0.0.1 --proxy-port 8080 --proxy-type socks5 --timeout 120
```

### Proxy Usage

[](https://github.com/RedSiege/EyeWitness#proxy-usage)

The best guide for proxying EyeWitness through a socks proxy was made by @raikia and is available here - [#458](https://github.com/RedSiege/EyeWitness/issues/458)

To install EyeWitness from a system while needing to go through a proxy, the following commands (thanks to @digininja) can be used.

```shell
APT
-------
/etc/apt/apt.conf.d/70proxy

$ cat /etc/apt/apt.conf.d/70proxy
Acquire::http::proxy "http://localhost:3128";
Acquire::https::proxy "https://localhost:3128";

Git
-----------------
$ cat ~/.gitconfig
[http]
proxy = http://localhost:3128

Wget
---------------------
$ cat ~/.wgetrc or /etc/wgetrc

use_proxy=yes
http_proxy=127.0.0.1:3128
https_proxy=127.0.0.1:3128

General system proxy
--------------------------------

export HTTP_PROXY=http://localhost:3128
export HTTPS_PROXY=http://localhost:3128
```

### Docker

[](https://github.com/RedSiege/EyeWitness#docker)

Now you can execute EyeWitness in a docker container and prevent you from install unnecessary dependencies in your host machine.

**Note:** execute _docker run_ with the folder path in the host which hold your results (**/path/to/results**)  
**Note2:** in case you want to scan urls from a file, make sure you put it in the volume folder (if you put _urls.txt_ in _/path/to/results_, then the argument should be _-f /tmp/EyeWitness/urls.txt_)

##### Usage

[](https://github.com/RedSiege/EyeWitness#usage-2)

```shell
sudo docker build -t eyewitness
```

##### Example #1 -

[](https://github.com/RedSiege/EyeWitness#example-1--)

```shell
sudo docker run --rm \
    -v /tmp:/Eyewitness/Python/ \
    eyewitness --web \
    -f /Eyewitness/Python/dns.txt \
    --no-prompt \
    -d /Eyewitness/Python/report-$(date +'%d-%m-%Y-%H-%M-%S' | sed 's/[-:]/-/g')
```

And then on your host :

```shell
cd /tmp && ls 
cd report*
firefox-esr report.html &
```

###### Call to Action:

[](https://github.com/RedSiege/EyeWitness#call-to-action)

I'd love for EyeWitness to identify more default credentials of various web applications.  
As you find a device which utilizes default credentials, please e-mail me the source code of the index page and the default creds so I can add it in to EyeWitness!

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/RedSiege/EyeWitness). Be sure to check out the original post for more details.

# Tool Documentation:

## eyewitness Usage Examples

Take a screenshot of each of the websites listed in the provided file using headless mode:

```console
root@kali:~# cat urls.txt
https://www.kali.org
https://www.kali.org/docs
https://www.kali.org/tools
https://www.exploit-db.com
https://www.offsec.com

root@kali:~# eyewitness -f /root/urls.txt -d screens --headless

################################################################################
#                                  EyeWitness                                  #
################################################################################

Starting Web Requests (5 Hosts)
Attempting to screenshot https://www.kali.org
Attempting to screenshot https://www.kali.org/docs
Attempting to screenshot https://www.kali.org/tools
Attempting to screenshot https://www.exploit-db.com
Attempting to screenshot https://www.offsec.com
Finished in 14.1417660713 seconds

[*] Done! Report written in the /usr/share/eyewitness/screens folder!
Would you like to open the report now? [Y/n] Y
```

---

  

# Packages and Binaries:

### eyewitness

EyeWitness is designed to take screenshots of websites, provide some server header info, and identify default credentials if possible.

Inspiration came from Tim Tomes’s PeepingTom Script.

EyeWitness is designed to run on Kali Linux. It will auto detect the file you give it with the -f flag as either being a text file with URLs on each new line, nmap xml output, or nessus xml output. The -t (timeout) flag is completely optional, and lets you provice the max time to wait when trying to render and screenshot a web page. The –open flag, which is optional, will open the URL in a new tab within Firefox.

**Installed size:** `5.78 MB`  
**How to install:** `sudo apt install eyewitness`

Dependencies:

- links | www-browser
- python3
- python3-distutils
- python3-fuzzywuzzy
- python3-netaddr
- python3-pyvirtualdisplay
- python3-selenium
- xvfb

##### eyewitness

```console
root@kali:~# eyewitness -h
################################################################################
#                                  EyeWitness                                  #
################################################################################
#           Red Siege Information Security - https://www.redsiege.com           #
################################################################################

usage: EyeWitness.py [--web] [-f Filename] [-x Filename.xml]
                     [--single Single URL] [--no-dns] [--timeout Timeout]
                     [--jitter # of Seconds] [--delay # of Seconds]
                     [--threads # of Threads]
                     [--max-retries Max retries on a timeout]
                     [-d Directory Name] [--results Hosts Per Page]
                     [--no-prompt] [--user-agent User Agent]
                     [--difference Difference Threshold]
                     [--proxy-ip 127.0.0.1] [--proxy-port 8080]
                     [--proxy-type socks5] [--show-selenium] [--resolve]
                     [--add-http-ports ADD_HTTP_PORTS]
                     [--add-https-ports ADD_HTTPS_PORTS]
                     [--only-ports ONLY_PORTS] [--prepend-https]
                     [--selenium-log-path SELENIUM_LOG_PATH]
                     [--cookies key1=value1,key2=value2] [--resume ew.db]

EyeWitness is a tool used to capture screenshots from a list of URLs

Protocols:
  --web                 HTTP Screenshot using Selenium

Input Options:
  -f Filename           Line-separated file containing URLs to capture
  -x Filename.xml       Nmap XML or .Nessus file
  --single Single URL   Single URL/Host to capture
  --no-dns              Skip DNS resolution when connecting to websites

Timing Options:
  --timeout Timeout     Maximum number of seconds to wait while requesting a
                        web page (Default: 7)
  --jitter # of Seconds
                        Randomize URLs and add a random delay between requests
  --delay # of Seconds  Delay between the opening of the navigator and taking
                        the screenshot
  --threads # of Threads
                        Number of threads to use while using file based input
  --max-retries Max retries on a timeout
                        Max retries on timeouts

Report Output Options:
  -d Directory Name     Directory name for report output
  --results Hosts Per Page
                        Number of Hosts per page of report
  --no-prompt           Don't prompt to open the report

Web Options:
  --user-agent User Agent
                        User Agent to use for all requests
  --difference Difference Threshold
                        Difference threshold when determining if user agent
                        requests are close "enough" (Default: 50)
  --proxy-ip 127.0.0.1  IP of web proxy to go through
  --proxy-port 8080     Port of web proxy to go through
  --proxy-type socks5   Proxy type (socks5/http)
  --show-selenium       Show display for selenium
  --resolve             Resolve IP/Hostname for targets
  --add-http-ports ADD_HTTP_PORTS
                        Comma-separated additional port(s) to assume are http
                        (e.g. '8018,8028')
  --add-https-ports ADD_HTTPS_PORTS
                        Comma-separated additional port(s) to assume are https
                        (e.g. '8018,8028')
  --only-ports ONLY_PORTS
                        Comma-separated list of exclusive ports to use (e.g.
                        '80,8080')
  --prepend-https       Prepend http:// and https:// to URLs without either
  --selenium-log-path SELENIUM_LOG_PATH
                        Selenium geckodriver log path
  --cookies key1=value1,key2=value2
                        Additional cookies to add to the request

Resume Options:
  --resume ew.db        Path to db file if you want to resume
```

---

##### geckodriver

```console
root@kali:~# geckodriver -h
geckodriver 0.33.0 (a80e5fd61076 2023-04-02 18:31 +0000) 
WebDriver implementation for Firefox

USAGE:
    geckodriver [OPTIONS]

OPTIONS:
        --allow-hosts <ALLOW_HOSTS>...
            List of hostnames to allow. By default the value of --host is allowed, and in addition
            if that's a well known local address, other variations on well known local addresses are
            allowed. If --allow-hosts is provided only exactly those hosts are allowed.

        --allow-origins <ALLOW_ORIGINS>...
            List of request origins to allow. These must be formatted as scheme://host:port. By
            default any request with an origin header is rejected. If --allow-origins is provided
            then only exactly those origins are allowed.

        --android-storage <ANDROID_STORAGE>
            Selects storage location to be used for test data (deprecated). [possible values: auto,
            app, internal, sdcard]

    -b, --binary <BINARY>
            Path to the Firefox binary

        --connect-existing
            Connect to an existing Firefox instance

    -h, --help
            Prints this message

        --host <HOST>
            Host IP to use for WebDriver server [default: 127.0.0.1]

        --jsdebugger
            Attach browser toolbox debugger for Firefox

        --log <LEVEL>
            Set Gecko log level [possible values: fatal, error, warn, info, config, debug, trace]

        --log-no-truncate
            Disable truncation of long log lines

        --marionette-host <HOST>
            Host to use to connect to Gecko [default: 127.0.0.1]

        --marionette-port <PORT>
            Port to use to connect to Gecko [default: system-allocated port]

    -p, --port <PORT>
            Port to use for WebDriver server [default: 4444]

        --profile-root <PROFILE_ROOT>
            Directory in which to create profiles. Defaults to the system temporary directory.

    -v
            Log level verbosity (-v for debug and -vv for trace level)

    -V, --version
            Prints version and copying information

        --websocket-port <PORT>
            Port to use to connect to WebDriver BiDi [default: 9222]

```

---

Updated on: 2024-Mar-11

**Credit:** This information was adapted from an excellent guide on [Kali.org](https://www.kali.org/tools/eyewitness/). Be sure to check out the original post for more details.

# EyeWitness – Hacker Tools: Hacking through screenshots 👩‍💻

By Anna Hammond

January 11, 2022

![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAoHBwgHBhYUEBQLEwoVDhgQDRkNFR0UEw8PFx0lGBYTHxYdHysjHR0oHSEWJTUlKC0vMjIyGSI4PTcwPCsxMi8BCgsLDg0OHBAQHDsoIig7LzUvLy87LzU1NTUvLzUvNS8vLy8vLy8vNS8vNS8vLy8vLy8vLy8vLy8vLy8vLy8vL//AABEIABgAGAMBIgACEQEDEQH/xAAYAAEBAQEBAAAAAAAAAAAAAAAABQYHAv/EACAQAAICAQMFAAAAAAAAAAAAAAAEAgMBBRFBBhMVUWH/xAAYAQACAwAAAAAAAAAAAAAAAAABBAACA//EABgRAQEAAwAAAAAAAAAAAAAAAAEAAgMR/9oADAMBAAIRAxEAPwDq2o6hhKvjci0dQylaeOoVWp+zPUK31z53CzWjUJb9B7LQI2gwYxPkB5L5YceDW3FpMxIvibO+ASrqyQaykrlaP0AEs1Vv/9k=)![EyeWitness – Hacker Tools:  Hacking through screenshots 👩‍💻](https://www.datocms-assets.com/85623/1719639166-intigriti_blog_tools_spotlight_23.png?auto=format)

EyeWitness is an incredible tool that allows you to quickly get a feel for what assets to target first. We all know hundreds of content discovery tools that give us vast amounts of data, but do we ever focus on efficiently parsing all that data? How do you go through hundreds of endpoints? If you’re doing it manually, then be sure to read this article as EyeWitness may be of great help to you!

## 🙋‍♂️ What is EyeWitness?

[EyeWitness](https://github.com/FortyNorthSecurity/EyeWitness) is a Python tool written by [@CptJesus](https://twitter.com/cptjesus) and [@christruncer](https://twitter.com/christruncer). It’s goal is to help you efficiently assess what assets of your target to look into first.

It achieves this by taking screenshots of every assets and showing you those screenshots alongside some header information and potential default credentials if applicable.

Reading on what this tool can do is all fun and games, but let’s put the tool to the test by using it!

## 👷‍♀️ Installing EyeWitness

You can’t run a tool without installing it first. Luckily, it’s as easy as shown in this GIF.

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSI2NTQiIGhlaWdodD0iNDUzIj48L3N2Zz4=)![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAoHBwgHBhIIEAgLDw4NDQ4NDQkNDhIJDhENFxUZGCIVFhUaHysjGh0oHRUWJDUlKC0vMjIyGSI4PTcwPCsxMi8BCgsLDg0NEBANFS8dFhwvLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vL//AABEIABEAGAMBIgACEQEDEQH/xAAZAAEAAgMAAAAAAAAAAAAAAAAAAgQBAwf/xAAfEAABAwMFAAAAAAAAAAAAAAAAAQIyAwQxBRITFVL/xAAWAQEBAQAAAAAAAAAAAAAAAAAAAgH/xAAYEQEAAwEAAAAAAAAAAAAAAAAAAQISE//aAAwDAQACEQMRAD8A56uuXyrEd9fY2qV21neDHM5VgTuytSst1m9V0QaGVnbog3pY1LJFMgGCdOYAA//Z)![eyewitnessInstall](https://www.datocms-assets.com/85623/1719568928-eyewitnessinstall.gif?auto=format)

Installing EyeWitness

As you can see, installing EyeWitness consists of 2 steps:

- Clone the repository: `git clone https://github.com/FortyNorthSecurity/EyeWitness.git`
    
- Run the setup.sh script: `sh EyeWitness/Python/setup/setup.sh`
    

That’s all! If all goes well, you’ve now successfully installed EyeWitness!

## 🐱‍🏍 Our first run!

Let’s get into it! There’s only one obvious thing we still need: A list of domain names to target. This can easily be gotten from one of the reconnaissance tools we’ve already discussed in the past! Check out our [Hacking Tools](https://blog.intigriti.com/hackademy/hacking-tools) page in the [Intigriti Hackademy](https://blog.intigriti.com/hackademy/)!

Now we can execute `eyewitness -f domains.txt` and this will start the tool. Take a look at the gif below to see what such a run looks like.

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSI2NTQiIGhlaWdodD0iNDUzIj48L3N2Zz4=)![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAoHBwgHBgoODQgSCg0PDhMNDQ0NDhINDQ0YFxMZGBYTIhUaHysjGh0oHRUWJDUlKC0vMjIyGSI4PTcwPCsxMi8BCgsLDg4OEBAQFS8cFhwvLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vL//AABEIABEAGAMBIgACEQEDEQH/xAAYAAEAAwEAAAAAAAAAAAAAAAAAAQQHA//EAB8QAAEDBAMBAAAAAAAAAAAAAAABAjIDBBVCERMxBf/EABYBAQEBAAAAAAAAAAAAAAAAAAECAP/EABcRAQEBAQAAAAAAAAAAAAAAAAASAgH/2gAMAwEAAhEDEQA/AM8zl8qxJzt9zErpWcmg7XLoF6VXVhPs3rliDhTrOV0Qa9Cujg3wACmlMACH/9k=)![EyewitnessRun](https://www.datocms-assets.com/85623/1719568945-eyewitnessrun.gif?auto=format)

Running EyeWitness

After executing, the tool will open the result in your browser. Here you can assess the results. Let’s discuss them the screenshot below.

The result page starts off by giving us a nice overlay of all everything that it found. In this case we have Unauthorized pages, Not Found pages and Bad requests already filtered out of all the rest. Nice!

Scrolling down, we find screenshots and the headers of all these pages. We can now quickly assess which page we would like to target first!

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMjY4IiBoZWlnaHQ9Ijg1NiI+PC9zdmc+)![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAoHBwgHBgoICAgFCgoFBQwFBQUFBREJCgUMFxMZGBYTFhUaHysjGh0oHRUWJDUlKC0vMjIyGSI4PTcwPCsxMi8BCgsLBQUFEAUFEC8cFhwvLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vL//AABEIABEAGAMBIgACEQEDEQH/xAAVAAEBAAAAAAAAAAAAAAAAAAAAB//EABQQAQAAAAAAAAAAAAAAAAAAAAD/xAAVAQEBAAAAAAAAAAAAAAAAAAAAAv/EABQRAQAAAAAAAAAAAAAAAAAAAAD/2gAMAwEAAhEDEQA/ALEApIAAAAAD/9k=)![runResults1-1](https://www.datocms-assets.com/85623/1719568957-runresults1-1.png?auto=format)

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMjY4IiBoZWlnaHQ9Ijg1NiI+PC9zdmc+)![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAoHBwgHBgoICAgXCgoLDh0VDg0NDh0fFhURHRMdGCIfHR4aHy0jHR0oHRUiJTUlKC0vMjIyGSI4PTcwPCsxMi8BCgsLDg0OFRAPFS8dIhwvLy8vLy8vOy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vL//AABEIABEAGAMBIgACEQEDEQH/xAAZAAEAAgMAAAAAAAAAAAAAAAAAAwQBAgf/xAAiEAABAwIHAQEAAAAAAAAAAAAAAgMRAQUEBhIhM1FhQyL/xAAVAQEBAAAAAAAAAAAAAAAAAAABAP/EABQRAQAAAAAAAAAAAAAAAAAAAAD/2gAMAwEAAhEDEQA/AOru3DCtLmZKdcz4NDuhRdrbMIpf638krry9blu6qo36kQwxmDAuvVpqj0wSN2G3IXKW9+pBJL9grlAENUc4AJP/2Q==)![runResults2](https://www.datocms-assets.com/85623/1719568967-runresults2.png?auto=format)

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMjY4IiBoZWlnaHQ9Ijg1NiI+PC9zdmc+)![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAoHBwgHBgoICAgLCgoXDiIVDg0NDh0fFhYbFxMZHRYVHRUlKy0lGikoHRUWJDUlPjkvMjIyHSI4PTcwPCsxMi8BCgsLDg0PHA0QGC8cHRwvLy8vLy8vLy8vLy8vNS8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vL//AABEIABEAGAMBIgACEQEDEQH/xAAZAAADAQEBAAAAAAAAAAAAAAAABQYHBAH/xAAgEAACAgIBBQEAAAAAAAAAAAABAwACBAURBjM0UXEH/8QAFQEBAQAAAAAAAAAAAAAAAAAAAQD/xAAUEQEAAAAAAAAAAAAAAAAAAAAA/9oADAMBAAIRAxEAPwDQtj1I7FQbUVyePUj2fo+0U61QgkfJpDdbiXoQygIi2ui012EFVCYlJafr/Z5WSasQSPREJZ4mj1mO8laq8wkjLI7RiRXkmEJJ3J7s8hCJf//Z)![runResults3](https://www.datocms-assets.com/85623/1719568978-runresults3.png?auto=format)

## 🌟 Features

Let’s take a closer look at some more features that EyeWitness has in store for us!

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxOTE5IiBoZWlnaHQ9IjEwNDIiPjwvc3ZnPg==)![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAoHBwgHBgoICAgNDQ8LDg0ODQ0NERYNDRENFxcZGCIVFhUaHysjGh0oHSEWJDUlKC0vMjIyGSI4PTcwPCsxMi8BCgsLCgoFEAUKEC8cFhwvLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vL//AABEIAA4AGAMBIgACEQEDEQH/xAAXAAADAQAAAAAAAAAAAAAAAAABBQYE/8QAHRAAAAcAAwAAAAAAAAAAAAAAAAECAwQFESFBYf/EABUBAQEAAAAAAAAAAAAAAAAAAAIA/8QAFBEBAAAAAAAAAAAAAAAAAAAAAP/aAAwDAQACEQMRAD8Ama+3W9KINZEtZL0TdWkkSSwPXnPOgSIrW0dJ7MAGKzXsk+ARJ//Z)![image-2](https://www.datocms-assets.com/85623/1719568989-image-2.png?auto=format)

EyeWitness Usage

### Input options

These are the options that can help you input the targets to take screenshots of.

- `-f Filename`  
    Line-separated file containing URLs to capture. As seen in the example above.
    
- `-x Filename.xml`  
    Nmap XML or .Nessus file because yes, this tool can parse that output!
    
- `--single Single URL`  
    Single URL/Host to capture. If for some reason you’d only want to scan a single target.
    
- `--no-dns`  
    Skip DNS resolution when connecting to websites. Can be useful in specific cases if you’re going through a VPN for example.
    

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNTIwIiBoZWlnaHQ9IjMxNiI+PC9zdmc+)![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAoHBwgHBgoNCAgLChIOERgODA0NDh0KGhENFxUZGBYVFhUaKysjGh0oHRUWJDUlKC0vMjIyGSI4PTcwPCsxMi8BCgsLDg0MFQ0FEC8cFhwvLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vL//AABEIAAUAGAMBIgACEQEDEQH/xAAXAAEAAwAAAAAAAAAAAAAAAAAAAwQG/8QAGxAAAgMBAQEAAAAAAAAAAAAAAAECAwQhExL/xAAWAQEBAQAAAAAAAAAAAAAAAAABAgD/xAAUEQEAAAAAAAAAAAAAAAAAAAAA/9oADAMBAAIRAxEAPwDFS2qbX1RBk89Vap5lgASFO7WvPlMUADB//9k=)![image-4](https://www.datocms-assets.com/85623/1719569003-image-4.png?auto=format)

Input Options

### Timing Options

Need to go fast, need to slow down? These options help you go to town! Please take a close look at these options as they can help you stay within the required limits of bug bounty programs!

- `--timeout`  
    Timeout Maximum number of seconds to wait while requesting a web page (Default: 7).
    
- `--jitter # of Seconds`  
    Randomize URLs and add a random delay between requests.
    
- `--delay # of Seconds`  
    Delay between the opening of the navigator and taking the screenshot.
    
- `--threads # of Threads`  
    Number of threads to use while using file based input.
    
- `--max-retries Max retries on a timeout`  
    Max retries on timeouts.
    

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNTIyIiBoZWlnaHQ9IjYwNCI+PC9zdmc+)![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAoHBwgHBgoICAgLDQ0XDhYQDQ0PDhIOCg0NFxMZGBYVFhUaHysjGh0oHRUWJDUlKC0vMjIyGSI4PTcwPCsxMi8BCgsLDgUFEAUFEC8cFhwvLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vL//AABEIAAoAGAMBIgACEQEDEQH/xAAZAAACAwEAAAAAAAAAAAAAAAAEBQEDBgD/xAAdEAABBAIDAAAAAAAAAAAAAAABAAIDBBExExQh/8QAFQEBAQAAAAAAAAAAAAAAAAAAAgD/xAAUEQEAAAAAAAAAAAAAAAAAAAAA/9oADAMBAAIRAxEAPwDIROZJgEo6avA2uHEpJXPoR14nqbRFVbFd0GA4LkpmJ4tlQpP/2Q==)![image-5](https://www.datocms-assets.com/85623/1719569013-image-5.png?auto=format)

Timing Options

### Report Output Options

Couple of minor options to change the output file.

- `-d Directory Name`  
    Directory name for report output
    
- `--results Hosts Per Page`  
    Number of Hosts per page of report
    
- `--no-prompt`  
    Don’t prompt to open the report
    

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMjQxIiBoZWlnaHQ9IjI5NyI+PC9zdmc+)![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAoHBwgHBhIICAgNCgoOFRILDQ0NDh0ODRENFx8ZGBYVFhUaJysjGh0oHSEWJDUlKC0vMjIyGSI4PTcwPCsxMi8BCgsLDg0OEBAQEC8cFhwvLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vL//AABEIAAYAGAMBIgACEQEDEQH/xAAWAAEBAQAAAAAAAAAAAAAAAAAABgL/xAAaEAACAgMAAAAAAAAAAAAAAAAAAwEEAhEh/8QAFQEBAQAAAAAAAAAAAAAAAAAAAgD/xAAUEQEAAAAAAAAAAAAAAAAAAAAA/9oADAMBAAIRAxEAPwCPxtphHU7M4sqsw3NcAIjJrQriQASf/9k=)![image-6](https://www.datocms-assets.com/85623/1719569023-image-6.png?auto=format)

Report Output Options

### Web Options

These options deal with the way that EyeWitness takes screenshots of the resulting pages. All of this can be configured to handle that HTTP(S) traffic in just the way you want it! Note that some of these options are also required to adhere to some bug bounty program’s rules.

- `--user-agent User Agent`  
    User Agent to use for all requests.
    
- `--difference Difference Threshold`  
    Difference threshold when determining if user agent requests are close “enough” (Default: 50).
    
- `--proxy-ip 127.0.0.1`  
    IP of web proxy to go through.
    
- `--proxy-port 8080`  
    Port of web proxy to go through.
    
- `--proxy-type socks5`  
    Proxy type (socks5/http).
    
- `--show-selenium`  
    Show display for selenium.
    
- `--resolve`  
    Resolve IP/Hostname for targets.
    
- `--add-http-ports ADD_HTTP_PORTS`  
    Comma-separated additional port(s) to assume are http (e.g. ‘8018,8028’).
    
- `--add-https-ports ADD_HTTPS_PORTS`  
    Comma-separated additional port(s) to assume are https (e.g. ‘8018,8028’)
    
- `--only-ports ONLY_PORTS`  
    Comma-separated list of exclusive ports to use (e.g. ‘80,8080’).
    
- `--prepend-https`  
    Prepend http:// and https:// to URLs without either
    
- `--selenium-log-path SELENIUM_LOG_PATH`  
    Selenium geckodriver log path.
    

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNTY3IiBoZWlnaHQ9IjEwMTIiPjwvc3ZnPg==)![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAoHBwgHBgoQDg8LCg0JDhUMDgcODREJDQgYFxUZGBYVFiEaHysjGh0oHRUWJDUlKC0vMjIyGSI4PTcwPCsxMi8BCgsLBQ0OEBAKFS8cFhwvLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vL//AABEIABAAGAMBIgACEQEDEQH/xAAZAAABBQAAAAAAAAAAAAAAAAAEAAIDBQb/xAAZEAACAwEAAAAAAAAAAAAAAAAAAQMEEQL/xAAVAQEBAAAAAAAAAAAAAAAAAAACAP/EABQRAQAAAAAAAAAAAAAAAAAAAAD/2gAMAwEAAhEDEQA/AMtXiRPJFnANWb0Lm6yMIqe4mhDrXSYiT//Z)![image-7](https://www.datocms-assets.com/85623/1719569033-image-7.png?auto=format)

Web Options

## Resume Options

This option is a really, really nice one that allows you to resume scanning if your previous scan crashed. When we’re dealing with potentially thousands of endpoints, crashes can occur, so this options is a real lifesaver!

- `--resume ew.db`  
    Path to db file if you want to resume. You can find the database file in the directory (named the current date and time) that EyeWitness automatically creates when running.
    

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMzAwIiBoZWlnaHQ9IjEwNiI+PC9zdmc+)![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAoHBwgHBgoOCAgLCg4NDhYQDg4NDh0TFhENFxUaGBYTFhUpKy0jGh0oHRUWJDUlKC0vMjIyGSI4PTcwPCsxMi8BCgsLBQUNFAUFEC8cFhwvLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vL//AABEIAAIAGAMBIgACEQEDEQH/xAAYAAEAAwEAAAAAAAAAAAAAAAAAAgMGAf/EABsQAAICAwEAAAAAAAAAAAAAAAADAQIEIZKB/8QAFgEBAQEAAAAAAAAAAAAAAAAAAQIA/8QAFBEBAAAAAAAAAAAAAAAAAAAAAP/aAAwDAQACEQMRAD8Az+XWs4u6xPhShKpxtrpzABIRelUY+l05g6AYP//Z)![image-8](https://www.datocms-assets.com/85623/1719569043-image-8.png?auto=format)

Resume Options

## 🚧 Conclusion

EyeWitness is a simple, yet helpful tool designed to help you get more efficient in your post reconnaissance phase! Start using it today to hack even faster!

If you would like to recommend a tool for us to cover next week, then be sure to let us know down below. Also be sure to check out [all the previous Hacker Tools articles](https://blog.intigriti.com/category/tools/), such as [the last one on GoSpider](https://blog.intigriti.com/2021/09/24/hacker-tools-waybackurls/).

---

Did you know that there is a video accompanying this article? Check out [the playlist](https://www.youtube.com/playlist?list=PLmqenIp2RQch-N9mnm-5gFCtWWE3l4-cE)!

**Credit:** This information was adapted from an excellent guide on [Intigriti](https://blog.intigriti.com/hacking-tools/hacker-tools-eyewitness). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/phkYV55cFmc?si=8CYwf-yJ-H9bIxkN" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=phkYV55cFmc). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/QQ7Cjn2GaDM?si=yKI_vWVAQd6Aji-r" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=QQ7Cjn2GaDM). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/qy7aiEPtY-8?si=KDjTVOZuMgndp6k7" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=qy7aiEPtY-8). Be sure to check out the original post for more details.




