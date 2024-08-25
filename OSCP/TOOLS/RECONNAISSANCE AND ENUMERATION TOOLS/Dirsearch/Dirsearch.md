[![dirsearch logo (light)](https://github.com/maurosoria/dirsearch/raw/master/static/logo.png#gh-light-mode-only)](https://github.com/maurosoria/dirsearch/blob/master/static/logo.png#gh-light-mode-only)

# dirsearch - Web path discovery

[](https://github.com/maurosoria/dirsearch#dirsearch---web-path-discovery)

[![Build](https://camo.githubusercontent.com/4d11a867ad97d9d0e55bf60f0808b85dc29d300d285a732a541a0a2e93b86371/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f4275696c74253230776974682d507974686f6e2d426c7565)](https://camo.githubusercontent.com/4d11a867ad97d9d0e55bf60f0808b85dc29d300d285a732a541a0a2e93b86371/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f4275696c74253230776974682d507974686f6e2d426c7565) [![License](https://camo.githubusercontent.com/1c0cf4ccd0fd620aad7fea5225b793826829f880d35b2d025c159f75ab539a39/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f6c6963656e73652d474e555f47656e6572616c5f5075626c69635f4c6963656e73652d5f7265642e737667)](https://camo.githubusercontent.com/1c0cf4ccd0fd620aad7fea5225b793826829f880d35b2d025c159f75ab539a39/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f6c6963656e73652d474e555f47656e6572616c5f5075626c69635f4c6963656e73652d5f7265642e737667) [![Stars](https://camo.githubusercontent.com/d6ab9688d22fef5e051d97954b0e88d05d59445f201b998cdb97e4f3e2291e2c/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f73746172732f6d6175726f736f7269612f6469727365617263682e737667)](https://camo.githubusercontent.com/d6ab9688d22fef5e051d97954b0e88d05d59445f201b998cdb97e4f3e2291e2c/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f73746172732f6d6175726f736f7269612f6469727365617263682e737667) [![Release](https://camo.githubusercontent.com/cce813502af6fa9c69321d6b59b2444363cd3d39d46069dd0a85ff62cd70c459/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f72656c656173652f6d6175726f736f7269612f6469727365617263682e737667)](https://github.com/maurosoria/dirsearch/releases) [![Sponsors](https://camo.githubusercontent.com/6261f26acb397958cec17173583be35e3d84694e2368a1292bef902a3d15aefc/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f73706f6e736f72732f6d6175726f736f726961)](https://github.com/sponsors/maurosoria) [![Discord](https://camo.githubusercontent.com/fee7813cb6da27cbba2ad7bc885710c9a851a5efd8882e1feb3d360646177622/68747470733a2f2f696d672e736869656c64732e696f2f646973636f72642f3939323237363239363636393333393637382e7376673f6c6f676f3d646973636f7264)](https://discord.gg/2N22ZdAJRj) [![Twitter](https://camo.githubusercontent.com/20a31ae93001b1e44727d28de6544feb4d1e09eae3914b3e904cdff75d545dcd/68747470733a2f2f696d672e736869656c64732e696f2f747769747465722f666f6c6c6f772f5f6469727365617263683f6c6162656c3d466f6c6c6f77)](https://twitter.com/_dirsearch)

> An advanced web path brute-forcer

**dirsearch** is being actively developed by [@maurosoria](https://twitter.com/_maurosoria) and [@shelld3v](https://twitter.com/shells3c_)

_Reach to our [Discord server](https://discord.gg/2N22ZdAJRj) to communicate with the team at best_

## Table of Contents

[](https://github.com/maurosoria/dirsearch#table-of-contents)

- [Installation](https://github.com/maurosoria/dirsearch#installation--usage)
- [Wordlists](https://github.com/maurosoria/dirsearch#wordlists-important)
- [Options](https://github.com/maurosoria/dirsearch#options)
- [Configuration](https://github.com/maurosoria/dirsearch#configuration)
- [How to use](https://github.com/maurosoria/dirsearch#how-to-use)
    - [Simple usage](https://github.com/maurosoria/dirsearch#simple-usage)
    - [Pausing progress](https://github.com/maurosoria/dirsearch#pausing-progress)
    - [Recursion](https://github.com/maurosoria/dirsearch#recursion)
    - [Threads](https://github.com/maurosoria/dirsearch#threads)
    - [Prefixes / Suffixes](https://github.com/maurosoria/dirsearch#prefixes--suffixes)
    - [Blacklist](https://github.com/maurosoria/dirsearch#blacklist)
    - [Filters](https://github.com/maurosoria/dirsearch#filters)
    - [Raw request](https://github.com/maurosoria/dirsearch#raw-request)
    - [Wordlist formats](https://github.com/maurosoria/dirsearch#wordlist-formats)
    - [Exclude extensions](https://github.com/maurosoria/dirsearch#exclude-extensions)
    - [Scan sub-directories](https://github.com/maurosoria/dirsearch#scan-sub-directories)
    - [Proxies](https://github.com/maurosoria/dirsearch#proxies)
    - [Reports](https://github.com/maurosoria/dirsearch#reports)
    - [More example commands](https://github.com/maurosoria/dirsearch#more-example-commands)
- [Support Docker](https://github.com/maurosoria/dirsearch#support-docker)
    - [Install Docker Linux](https://github.com/maurosoria/dirsearch#install-docker-linux)
    - [Build Image dirsearch](https://github.com/maurosoria/dirsearch#build-image-dirsearch)
    - [Using dirsearch](https://github.com/maurosoria/dirsearch#using-dirsearch)
- [References](https://github.com/maurosoria/dirsearch#references)
- [Tips](https://github.com/maurosoria/dirsearch#tips)
- [Contribution](https://github.com/maurosoria/dirsearch#contribution)
- [License](https://github.com/maurosoria/dirsearch#license)

## Installation & Usage

[](https://github.com/maurosoria/dirsearch#installation--usage)

**Requirement: python 3.7 or higher**

Choose one of these installation options:

- Install with **git**: `git clone https://github.com/maurosoria/dirsearch.git --depth 1` (**RECOMMENDED**)
- Install with ZIP file: [Download here](https://github.com/maurosoria/dirsearch/archive/master.zip)
- Install with Docker: `docker build -t "dirsearch:v0.4.3" .` (more information can be found [here](https://github.com/maurosoria/dirsearch#support-docker))
- Install with PyPi: `pip3 install dirsearch` or `pip install dirsearch`
- Install with Kali Linux: `sudo apt-get install dirsearch` (deprecated)

## Wordlists (IMPORTANT)

[](https://github.com/maurosoria/dirsearch#wordlists-important)

**Summary:**

- Wordlist is a text file, each line is a path.
- About extensions, unlike other tools, dirsearch only replaces the `%EXT%` keyword with extensions from **-e** flag.
- For wordlists without `%EXT%` (like [SecLists](https://github.com/danielmiessler/SecLists)), **-f | --force-extensions** switch is required to append extensions to every word in wordlist, as well as the `/`.
- To apply your extensions to wordlist entries that have extensions already, use **-O** | **--overwrite-extensions** (Note: some extensions are excluded from being overwritted such as _.log_, _.json_, _.xml_, ... or media extensions like _.jpg_, _.png_)
- To use multiple wordlists, you can separate your wordlists with commas. Example: `wordlist1.txt,wordlist2.txt`.

**Examples:**

- _Normal extensions_:

```
index.%EXT%
```

Passing **asp** and **aspx** as extensions will generate the following dictionary:

```
index
index.asp
index.aspx
```

- _Force extensions_:

```
admin
```

Passing **php** and **html** as extensions with **-f**/**--force-extensions** flag will generate the following dictionary:

```
admin
admin.php
admin.html
admin/
```

- _Overwrite extensions_:

```
login.html
```

Passing **jsp** and **jspa** as extensions with **-O**/**--overwrite-extensions** flag will generate the following dictionary:

```
login.html
login.jsp
login.jspa
```

## Options

[](https://github.com/maurosoria/dirsearch#options)

```
Usage: dirsearch.py [-u|--url] target [-e|--extensions] extensions [options]

Options:
  --version             show program's version number and exit
  -h, --help            show this help message and exit

  Mandatory:
    -u URL, --url=URL   Target URL(s), can use multiple flags
    -l PATH, --url-file=PATH
                        URL list file
    --stdin             Read URL(s) from STDIN
    --cidr=CIDR         Target CIDR
    --raw=PATH          Load raw HTTP request from file (use '--scheme' flag
                        to set the scheme)
    -s SESSION_FILE, --session=SESSION_FILE
                        Session file
    --config=PATH       Path to configuration file (Default:
                        'DIRSEARCH_CONFIG' environment variable, otherwise
                        'config.ini')

  Dictionary Settings:
    -w WORDLISTS, --wordlists=WORDLISTS
                        Customize wordlists (separated by commas)
    -e EXTENSIONS, --extensions=EXTENSIONS
                        Extension list separated by commas (e.g. php,asp)
    -f, --force-extensions
                        Add extensions to the end of every wordlist entry. By
                        default dirsearch only replaces the %EXT% keyword with
                        extensions
    -O, --overwrite-extensions
                        Overwrite other extensions in the wordlist with your
                        extensions (selected via `-e`)
    --exclude-extensions=EXTENSIONS
                        Exclude extension list separated by commas (e.g.
                        asp,jsp)
    --remove-extensions
                        Remove extensions in all paths (e.g. admin.php ->
                        admin)
    --prefixes=PREFIXES
                        Add custom prefixes to all wordlist entries (separated
                        by commas)
    --suffixes=SUFFIXES
                        Add custom suffixes to all wordlist entries, ignore
                        directories (separated by commas)
    -U, --uppercase     Uppercase wordlist
    -L, --lowercase     Lowercase wordlist
    -C, --capital       Capital wordlist

  General Settings:
    -t THREADS, --threads=THREADS
                        Number of threads
    -r, --recursive     Brute-force recursively
    --deep-recursive    Perform recursive scan on every directory depth (e.g.
                        api/users -> api/)
    --force-recursive   Do recursive brute-force for every found path, not
                        only directories
    -R DEPTH, --max-recursion-depth=DEPTH
                        Maximum recursion depth
    --recursion-status=CODES
                        Valid status codes to perform recursive scan, support
                        ranges (separated by commas)
    --subdirs=SUBDIRS   Scan sub-directories of the given URL[s] (separated by
                        commas)
    --exclude-subdirs=SUBDIRS
                        Exclude the following subdirectories during recursive
                        scan (separated by commas)
    -i CODES, --include-status=CODES
                        Include status codes, separated by commas, support
                        ranges (e.g. 200,300-399)
    -x CODES, --exclude-status=CODES
                        Exclude status codes, separated by commas, support
                        ranges (e.g. 301,500-599)
    --exclude-sizes=SIZES
                        Exclude responses by sizes, separated by commas (e.g.
                        0B,4KB)
    --exclude-text=TEXTS
                        Exclude responses by text, can use multiple flags
    --exclude-regex=REGEX
                        Exclude responses by regular expression
    --exclude-redirect=STRING
                        Exclude responses if this regex (or text) matches
                        redirect URL (e.g. '/index.html')
    --exclude-response=PATH
                        Exclude responses similar to response of this page,
                        path as input (e.g. 404.html)
    --skip-on-status=CODES
                        Skip target whenever hit one of these status codes,
                        separated by commas, support ranges
    --min-response-size=LENGTH
                        Minimum response length
    --max-response-size=LENGTH
                        Maximum response length
    --max-time=SECONDS  Maximum runtime for the scan
    --exit-on-error     Exit whenever an error occurs

  Request Settings:
    -m METHOD, --http-method=METHOD
                        HTTP method (default: GET)
    -d DATA, --data=DATA
                        HTTP request data
    --data-file=PATH    File contains HTTP request data
    -H HEADERS, --header=HEADERS
                        HTTP request header, can use multiple flags
    --header-file=PATH  File contains HTTP request headers
    -F, --follow-redirects
                        Follow HTTP redirects
    --random-agent      Choose a random User-Agent for each request
    --auth=CREDENTIAL   Authentication credential (e.g. user:password or
                        bearer token)
    --auth-type=TYPE    Authentication type (basic, digest, bearer, ntlm, jwt,
                        oauth2)
    --cert-file=PATH    File contains client-side certificate
    --key-file=PATH     File contains client-side certificate private key
                        (unencrypted)
    --user-agent=USER_AGENT
    --cookie=COOKIE

  Connection Settings:
    --timeout=TIMEOUT   Connection timeout
    --delay=DELAY       Delay between requests
    --proxy=PROXY       Proxy URL (HTTP/SOCKS), can use multiple flags
    --proxy-file=PATH   File contains proxy servers
    --proxy-auth=CREDENTIAL
                        Proxy authentication credential
    --replay-proxy=PROXY
                        Proxy to replay with found paths
    --tor               Use Tor network as proxy
    --scheme=SCHEME     Scheme for raw request or if there is no scheme in the
                        URL (Default: auto-detect)
    --max-rate=RATE     Max requests per second
    --retries=RETRIES   Number of retries for failed requests
    --ip=IP             Server IP address
    --interface=NETWORK_INTERFACE
                        Network interface to use

  Advanced Settings:
    --crawl             Crawl for new paths in responses

  View Settings:
    --full-url          Full URLs in the output (enabled automatically in
                        quiet mode)
    --redirects-history
                        Show redirects history
    --no-color          No colored output
    -q, --quiet-mode    Quiet mode

  Output Settings:
    -o PATH, --output=PATH
                        Output file
    --format=FORMAT     Report format (Available: simple, plain, json, xml,
                        md, csv, html, sqlite)
    --log=PATH          Log file
```

## Configuration

[](https://github.com/maurosoria/dirsearch#configuration)

By default, `config.ini` inside your dirsearch directory is used as the configuration file but you can select another file via `--config` flag or `DIRSEARCH_CONFIG` environment variable.

```ini
# If you want to edit dirsearch default configurations, you can
# edit values in this file. Everything after `#` is a comment
# and won't be applied

[general]
threads = 25
recursive = False
deep-recursive = False
force-recursive = False
recursion-status = 200-399,401,403
max-recursion-depth = 0
exclude-subdirs = %%ff/,.;/,..;/,;/,./,../,%%2e/,%%2e%%2e/
random-user-agents = False
max-time = 0
exit-on-error = False
# subdirs = /,api/
# include-status = 200-299,401
# exclude-status = 400,500-999
# exclude-sizes = 0b,123gb
# exclude-text = "Not found"
# exclude-regex = "^403$"
# exclude-redirect = "*/error.html"
# exclude-response = 404.html
# skip-on-status = 429,999

[dictionary]
default-extensions = php,aspx,jsp,html,js
force-extensions = False
overwrite-extensions = False
lowercase = False
uppercase = False
capitalization = False
# exclude-extensions = old,log
# prefixes = .,admin
# suffixes = ~,.bak
# wordlists = /path/to/wordlist1.txt,/path/to/wordlist2.txt

[request]
http-method = get
follow-redirects = False
# headers-file = /path/to/headers.txt
# user-agent = MyUserAgent
# cookie = SESSIONID=123

[connection]
timeout = 7.5
delay = 0
max-rate = 0
max-retries = 1
## By disabling `scheme` variable, dirsearch will automatically identify the URI scheme
# scheme = http
# proxy = localhost:8080
# proxy-file = /path/to/proxies.txt
# replay-proxy = localhost:8000

[advanced]
crawl = False

[view]
full-url = False
quiet-mode = False
color = True
show-redirects-history = False

[output]
## Support: plain, simple, json, xml, md, csv, html, sqlite
report-format = plain
autosave-report = True
autosave-report-folder = reports/
# log-file = /path/to/dirsearch.log
# log-file-size = 50000000
```

## How to use

[](https://github.com/maurosoria/dirsearch#how-to-use)

[![Dirsearch demo](https://camo.githubusercontent.com/a73048cd267dccf7f3aff933db42fd9f1a14acc65d7c97fdc67b53a8c0b2a059/68747470733a2f2f61736369696e656d612e6f72672f612f3338303131322e737667)](https://asciinema.org/a/380112)

Some examples for how to use dirsearch - those are the most common arguments. If you need all, just use the **-h** argument.

### Simple usage

[](https://github.com/maurosoria/dirsearch#simple-usage)

```
python3 dirsearch.py -u https://target
```

```
python3 dirsearch.py -e php,html,js -u https://target
```

```
python3 dirsearch.py -e php,html,js -u https://target -w /path/to/wordlist
```

---

### Pausing progress

[](https://github.com/maurosoria/dirsearch#pausing-progress)

dirsearch allows you to pause the scanning progress with CTRL+C, from here, you can save the progress (and continue later), skip the current target, or skip the current sub-directory.

[![Pausing dirsearch](https://github.com/maurosoria/dirsearch/raw/master/static/pause.png)](https://github.com/maurosoria/dirsearch/blob/master/static/pause.png)

---

### Recursion

[](https://github.com/maurosoria/dirsearch#recursion)

- Recursive brute-force is brute-forcing continuously the after of found directories. For example, if dirsearch finds `admin/`, it will brute-force `admin/*` (`*` is where it brute forces). To enable this feature, use **-r** (or **--recursive**) flag

```
python3 dirsearch.py -e php,html,js -u https://target -r
```

- You can set the max recursion depth with **--max-recursion-depth**, and status codes to recurse with **--recursion-status**

```
python3 dirsearch.py -e php,html,js -u https://target -r --max-recursion-depth 3 --recursion-status 200-399
```

- There are 2 more options: **--force-recursive** and **--deep-recursive**
    
    - **Force recursive**: Brute force recursively all found paths, not just paths end with `/`
    - **Deep recursive**: Recursive brute-force all depths of a path (`a/b/c` => add `a/`, `a/b/`)
- If there are sub-directories that you do not want to brute-force recursively, use `--exclude-subdirs`
    

```
python3 dirsearch.py -e php,html,js -u https://target -r --exclude-subdirs image/,media/,css/
```

---

### Threads

[](https://github.com/maurosoria/dirsearch#threads)

The thread number (**-t | --threads**) reflects the number of separated brute force processes. And so the bigger the thread number is, the faster dirsearch runs. By default, the number of threads is 25, but you can increase it if you want to speed up the progress.

In spite of that, the speed still depends a lot on the response time of the server. And as a warning, we advise you to keep the threads number not too big because it can cause DoS (Denial of Service).

```
python3 dirsearch.py -e php,htm,js,bak,zip,tgz,txt -u https://target -t 20
```

---

### Prefixes / Suffixes

[](https://github.com/maurosoria/dirsearch#prefixes--suffixes)

- **--prefixes**: Add custom prefixes to all entries

```
python3 dirsearch.py -e php -u https://target --prefixes .,admin,_
```

Wordlist:

```
tools
```

Generated with prefixes:

```
tools
.tools
admintools
_tools
```

- **--suffixes**: Add custom suffixes to all entries

```
python3 dirsearch.py -e php -u https://target --suffixes ~
```

Wordlist:

```
index.php
internal
```

Generated with suffixes:

```
index.php
internal
index.php~
internal~
```

---

### Blacklist

[](https://github.com/maurosoria/dirsearch#blacklist)

Inside the `db/` folder, there are several "blacklist files". Paths in those files will be filtered from the scan result if they have the same status as mentioned in the filename.

Example: If you add `admin.php` into `db/403_blacklist.txt`, whenever you do a scan that `admin.php` returns 403, it will be filtered from the result.

---

### Filters

[](https://github.com/maurosoria/dirsearch#filters)

Use **-i | --include-status** and **-x | --exclude-status** to select allowed and not allowed response status-codes

For more advanced filters: **--exclude-sizes**, **--exclude-texts**, **--exclude-regexps**, **--exclude-redirects** and **--exclude-response**

```
python3 dirsearch.py -e php,html,js -u https://target --exclude-sizes 1B,243KB
```

```
python3 dirsearch.py -e php,html,js -u https://target --exclude-texts "403 Forbidden"
```

```
python3 dirsearch.py -e php,html,js -u https://target --exclude-regexps "^Error$"
```

```
python3 dirsearch.py -e php,html,js -u https://target --exclude-redirects "https://(.*).okta.com/*"
```

```
python3 dirsearch.py -e php,html,js -u https://target --exclude-response /error.html
```

---

### Raw request

[](https://github.com/maurosoria/dirsearch#raw-request)

dirsearch allows you to import the raw request from a file. The content would be something looked like this:

```httpspec
GET /admin HTTP/1.1
Host: admin.example.com
Cache-Control: max-age=0
Accept: */*
```

Since there is no way for dirsearch to know what the URI scheme is, you need to set it using the `--scheme` flag. By default, dirsearch automatically detects the scheme.

---

### Wordlist formats

[](https://github.com/maurosoria/dirsearch#wordlist-formats)

Supported wordlist formats: uppercase, lowercase, capitalization

#### Lowercase:

[](https://github.com/maurosoria/dirsearch#lowercase)

```
admin
index.html
```

#### Uppercase:

[](https://github.com/maurosoria/dirsearch#uppercase)

```
ADMIN
INDEX.HTML
```

#### Capital:

[](https://github.com/maurosoria/dirsearch#capital)

```
Admin
Index.html
```

---

### Exclude extensions

[](https://github.com/maurosoria/dirsearch#exclude-extensions)

Use **-X | --exclude-extensions** with an extension list will remove all paths in the wordlist that contains the given extensions

`python3 dirsearch.py -u https://target -X jsp`

Wordlist:

```
admin.php
test.jsp
```

After:

```
admin.php
```

---

### Scan sub-directories

[](https://github.com/maurosoria/dirsearch#scan-sub-directories)

- From an URL, you can scan a list of sub-directories with **--subdirs**.

```
python3 dirsearch.py -e php,html,js -u https://target --subdirs /,admin/,folder/
```

---

### Proxies

[](https://github.com/maurosoria/dirsearch#proxies)

dirsearch supports SOCKS and HTTP proxy, with two options: a proxy server or a list of proxy servers.

```
python3 dirsearch.py -e php,html,js -u https://target --proxy 127.0.0.1:8080
```

```
python3 dirsearch.py -e php,html,js -u https://target --proxy socks5://10.10.0.1:8080
```

```
python3 dirsearch.py -e php,html,js -u https://target --proxylist proxyservers.txt
```

---

### Reports

[](https://github.com/maurosoria/dirsearch#reports)

Supported report formats: **simple**, **plain**, **json**, **xml**, **md**, **csv**, **html**, **sqlite**

```
python3 dirsearch.py -e php -l URLs.txt --format plain -o report.txt
```

```
python3 dirsearch.py -e php -u https://target --format html -o target.json
```

---

### More example commands

[](https://github.com/maurosoria/dirsearch#more-example-commands)

```
cat urls.txt | python3 dirsearch.py --stdin
```

```
python3 dirsearch.py -u https://target --max-time 360
```

```
python3 dirsearch.py -u https://target --auth admin:pass --auth-type basic
```

```
python3 dirsearch.py -u https://target --header-list rate-limit-bypasses.txt
```

**There are more to discover, try yourself!**

## Support Docker

[](https://github.com/maurosoria/dirsearch#support-docker)

### Install Docker Linux

[](https://github.com/maurosoria/dirsearch#install-docker-linux)

Install Docker

```shell
curl -fsSL https://get.docker.com | bash
```

> To use docker you need superuser power

### Build Image dirsearch

[](https://github.com/maurosoria/dirsearch#build-image-dirsearch)

To create image

```shell
docker build -t "dirsearch:v0.4.3" .
```

> **dirsearch** is the name of the image and **v0.4.3** is the version

### Using dirsearch

[](https://github.com/maurosoria/dirsearch#using-dirsearch)

For using

```shell
docker run -it --rm "dirsearch:v0.4.3" -u target -e php,html,js,zip
```

## References

[](https://github.com/maurosoria/dirsearch#references)

- [Comprehensive Guide on Dirsearch](https://www.hackingarticles.in/comprehensive-guide-on-dirsearch/) by Shubham Sharma
- [Comprehensive Guide on Dirsearch Part 2](https://www.hackingarticles.in/comprehensive-guide-on-dirsearch-part-2/) by Shubham Sharma
- [How to Find Hidden Web Directories with Dirsearch](https://www.geeksforgeeks.org/how-to-find-hidden-web-directories-with-dirsearch/) by GeeksforGeeks
- [GUÍA COMPLETA SOBRE EL USO DE DIRSEARCH](https://esgeeks.com/guia-completa-uso-dirsearch/?feed_id=5703&_unique_id=6076249cc271f) by ESGEEKS
- [How to use Dirsearch to detect web directories](https://www.ehacking.net/2020/01/how-to-find-hidden-web-directories-using-dirsearch.html) by EHacking
- [dirsearch how to](https://vk9-sec.com/dirsearch-how-to/) by VK9 Security
- [Find Hidden Web Directories with Dirsearch](https://null-byte.wonderhowto.com/how-to/find-hidden-web-directories-with-dirsearch-0201615/) by Wonder How To
- [Brute force directories and files in webservers using dirsearch](https://upadhyayraj.medium.com/brute-force-directories-and-files-in-webservers-using-dirsearch-613e4a7fa8d5) by Raj Upadhyay
- [Live Bug Bounty Recon Session on Yahoo (Amass, crts.sh, dirsearch) w/ @TheDawgyg](https://www.youtube.com/watch?v=u4dUnJ1U0T4) by Nahamsec
- [Dirsearch to find Hidden Web Directories](https://medium.com/@irfaanshakeel/dirsearch-to-find-hidden-web-directories-d0357fbe47b0) by Irfan Shakeel
- [Getting access to 25000 employees details](https://medium.com/@ehsahil/getting-access-to-25k-employees-details-c085d18b73f0) by Sahil Ahamad
- [Best Tools For Directory Bruteforcing](https://secnhack.in/multiple-ways-to-find-hidden-directory-on-web-server/) by Shubham Goyal
- [Discover hidden files & directories on a webserver - dirsearch full tutorial](https://www.youtube.com/watch?v=jVxs5at0gxg) by CYBER BYTES

## Tips

[](https://github.com/maurosoria/dirsearch#tips)

- The server has requests limit? That's bad, but feel free to bypass it, by randomizing proxy with `--proxy-list`
- Want to find out config files or backups? Try `--suffixes ~` and `--prefixes .`
- Want to find only folders/directories? Why not combine `--remove-extensions` and `--suffixes /`!
- The mix of `--cidr`, `-F`, `-q` and will reduce most of noises + false negatives when brute-forcing with a CIDR
- Scan a list of URLs, but don't want to see a 429 flood? `--skip-on-status 429` will help you to skip a target whenever it returns 429
- The server contains large files that slow down the scan? You _might_ want to use `HEAD` HTTP method instead of `GET`
- Brute-forcing CIDR is slow? Probably you forgot to reduce request timeout and request retries. Suggest: `--timeout 3 --retries 1`

## Contribution

[](https://github.com/maurosoria/dirsearch#contribution)

We have been receiving a lot of helps from many people around the world to improve this tool. Thanks so much to everyone who have helped us so far! See [CONTRIBUTORS.md](https://github.com/maurosoria/dirsearch/blob/master/CONTRIBUTORS.md) to know who they are.

#### Pull requests and feature requests are welcomed

[](https://github.com/maurosoria/dirsearch#pull-requests-and-feature-requests-are-welcomed)

## License

[](https://github.com/maurosoria/dirsearch#license)

Copyright (C) Mauro Soria ([maurosoria@gmail.com](mailto:maurosoria@gmail.com))

License: GNU General Public License, version 2

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/maurosoria/dirsearch). Be sure to check out the original post for more details.

# DirSearch

[](https://github.com/evilsocket/dirsearch#dirsearch)

This software is a Go implementation of the original [dirsearch tool](https://github.com/maurosoria/dirsearch) written by `Mauro Soria`. DirSearch is the very first tool I write in Go, mostly to play and experiment with Go's concurrency model, channels, and so forth :)

[![baby-gopher](https://raw.githubusercontent.com/drnic/babygopher-site/gh-pages/images/babygopher-badge.png)](http://www.babygopher.org/) [![Go Report Card](https://camo.githubusercontent.com/be76bf808d6e1390ffe6367c63ad193057154dce3d756704896281c544ea273a/68747470733a2f2f676f7265706f7274636172642e636f6d2f62616467652f6769746875622e636f6d2f6576696c736f636b65742f646972736561726368)](https://goreportcard.com/report/github.com/evilsocket/dirsearch)

## Purpose

[](https://github.com/evilsocket/dirsearch#purpose)

DirSearch takes an input URL ( `-url` parameter ) and a wordlist ( `-wordlist` parameter ), it will then perform concurrent `HEAD` requests using the lines of the wordlist as paths and files eventually bruteforcing folders and files on a web server.

It supports a custom file extension ( `-ext`, default to `php` ) and other optional arguments:

```
Usage of dirsearch:
  -200only
        If enabled, will only display responses with 200 status code.
  -consumers int
        Number of concurrent consumers. (default 8)
  -ext string
        File extension. (default "php")
  -maxerrors int
        Maximum number of errors to get before killing the program. (default 20)
  -url string
        Base URL to start enumeration from.
  -wordlist string
        Wordlist file to use for enumeration. (default "dict.txt")
```

## Compilation

[](https://github.com/evilsocket/dirsearch#compilation)

```
go get github.com/evilsocket/dirsearch
cd dirsearch
make get_glide
make install_dependencies
make build
```

## License

[](https://github.com/evilsocket/dirsearch#license)

This project is copyleft of [Simone Margaritelli](http://www.evilsocket.net/) and released under the GPL 3 license.

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/evilsocket/dirsearch). Be sure to check out the original post for more details.

# How to Find Hidden Web Directories with Dirsearch

Last Updated : 28 Jul, 2021

**Dirsearch** tool is a Python language-based tool, which is command-line only. Dirsearch lights when it comes to recursive scanning, so for every directory it identifies, it will go back through and crawl the directory for some additional directories. Dirsearch tool is an advanced command-line tool designed to brute-force directories and files in web servers or web path scanners. As Dirsearch is an advanced tool, it allows hackers to perform a complex web directories discovery,  with a customized wordlist, impressive performance, speed, high accuracy, advanced correction, and modern brute-force techniques with relevant outputs.

## Features of Dirsearch Tool:

1. Dirsearch perform Recursive brute forcing
2. Dirsearch perform Target enumeration from an IP range
3. Dirsearch perform Sub-directories brute forcing
4. Dirsearch is Easy and simple to use
5. Dirsearch is Multithreading
6. Dirsearch has Support for every HTTP method
7. Dirsearch has Quiet mode
8. Dirsearch has Debug mode

**Note:** Make Sure You have Python Installed on your System, as this is python-based tool.

## Installation of Dirsearch Tool in Kali Linux:

**Step 1:** Fire up your Kali Linux terminal and move to Desktop using the following command.

cd Desktop

![](https://media.geeksforgeeks.org/wp-content/uploads/20210725222654/DirsearchStep1.jpg)

**Step 2:**  You are on Desktop now create a new directory called Dirsearch using the following command. In this directory, we will complete the installation of the Dirsearch tool.

mkdir Dirsearch
cd Dirsearch

![](https://media.geeksforgeeks.org/wp-content/uploads/20210725222657/DirsearchStep3.jpg)

**Step 3:** Now you have to install the tool. You have to clone the tool from Github.

git clone https://github.com/maurosoria/dirsearch.git

![](https://media.geeksforgeeks.org/wp-content/uploads/20210725222658/DirsearchStep4.jpg)

**Step 4:** The tool has been downloaded successfully in the dirsearch directory. Now list out the contents of the tool by using the below command.

ls

![](https://media.geeksforgeeks.org/wp-content/uploads/20210725222659/DirsearchStep5.jpg)

**Step 5:** You can observe that there is a new directory created of the dirsearch tool that has been generated while we were installing the tool.Now move to that directory using the below command:

cd dirsearch

![](https://media.geeksforgeeks.org/wp-content/uploads/20210725222701/DirsearchStep6.jpg)

**Step 6:** Download the required packages for running the tool, use the following command.

pip3 install -r requirements.txt

![](https://media.geeksforgeeks.org/wp-content/uploads/20210725222704/DirsearchStep8.jpg)

**Step 7:** Now we are done with our installation, Use the below command to view the help (gives better understanding of tool) index of the tool.

python3 dirsearch.py --help

![](https://media.geeksforgeeks.org/wp-content/uploads/20210725222706/DirsearchStep9.jpg)

## Working with Dirsearch Tool:

#### Example 1: Simple Usage 

python3 dirsearch.py -u https://example.com

![](https://media.geeksforgeeks.org/wp-content/uploads/20210725222632/DirsearchExample1.jpg)

**Extensions (php,html,js):**

python3 dirsearch.py -e php,html,js -u https://example.com

![](https://media.geeksforgeeks.org/wp-content/uploads/20210725222634/DirsearchExample2.jpg)

**Using Wordlist:**

> python3 dirsearch.py -e php,html,js -u https://example.com -w /usr/share/wordlists/dirb/common.txt

![](https://media.geeksforgeeks.org/wp-content/uploads/20210725222635/DirsearchExample3.jpg)

#### Example 2: Recursive Scanning

**Simple Recursive Scan:**

> python3 dirsearch.py -e php,html,js -u https://geeksforgeeks.org -r

![](https://media.geeksforgeeks.org/wp-content/uploads/20210725222637/DirsearchExample4.jpg)

**Max Recursion Depth:**

> python3 dirsearch.py -e php,html,js -u https://geeksforgeeks.org -r -R 3

![](https://media.geeksforgeeks.org/wp-content/uploads/20210725222638/DirsearchExample5.jpg)

#### Example 3: Threads

**Using Threads:**

> python3 dirsearch.py -e php,htm,js,bak,zip,tgz,txt -u https://geeksforgeeks.org -t 30

![](https://media.geeksforgeeks.org/wp-content/uploads/20210725222640/DirsearchExample6.jpg)

#### Example 4: Prefixes / Suffixes

**Prefixes:**

> python3 dirsearch.py -e php -u https://geeksforgeeks.org –prefixes .,admin,_,~

![](https://media.geeksforgeeks.org/wp-content/uploads/20210725222641/DirsearchExample7.jpg)

**Suffixes:**

> python3 dirsearch.py -e php -u https://geeksforgeeks.org –suffixes ~,/

![](https://media.geeksforgeeks.org/wp-content/uploads/20210725222643/DirsearchExample8.jpg)

#### Example 5: Exclude extensions

**Excluding Extensions:**

> python3 dirsearch.py -e asp,aspx,htm,js -u https://geeksforgeeks.org -X php,jsp,jspx

![](https://media.geeksforgeeks.org/wp-content/uploads/20210725222645/DirsearchExample9.jpg)

#### Example 6: Filters

> python3 dirsearch.py -e php,html,js -u https://geeksforgeeks.org -i 200,204,400,403 -x 500,502,429

![](https://media.geeksforgeeks.org/wp-content/uploads/20210725222646/DirsearchExample10.jpg)

#### Example 7: Scan sub-directories

> python3 dirsearch.py -e php,html,js -u https://geeksforgeeks.org –subdirs admin/,folder/,/

![](https://media.geeksforgeeks.org/wp-content/uploads/20210725222648/DirsearchExample11.jpg)

#### Example 8:  **Using Proxy Server.**

> python3 dirsearch.py -e php,html,js -u https://geeksforgeeks.org –proxy 127.0.0.1:8080

![](https://media.geeksforgeeks.org/wp-content/uploads/20210725222649/DirsearchExample12.jpg)

#### Example 9: **Saving Results**

> python3 dirsearch.py -e php -u https://geeksforgeeks.org -o report.txt

![](https://media.geeksforgeeks.org/wp-content/uploads/20210725222651/DirsearchExample13.jpg)![](https://media.geeksforgeeks.org/wp-content/uploads/20210725222652/DirsearchExample14.jpg)

**Credit:** This information was adapted from an excellent guide on [GeeksForGeeks](https://www.geeksforgeeks.org/how-to-find-hidden-web-directories-with-dirsearch/). Be sure to check out the original post for more details.

# Comprehensive Guide on Dirsearch

[January 24, 2021](https://www.hackingarticles.in/comprehensive-guide-on-dirsearch/) by [Raj](https://www.hackingarticles.in/author/raj/)

In this article, we will learn how we can use Dirsearch. It is a simple command-line tool designed to brute force directories and files in websites. Which is a Python-based command-line website directory scanner designed to brute force site structure including directories and files.

### **Table of Content**

- Introduction to Dirsearch
- Setup
- Target URL
- Save Output in Different Formats
- No Colour
- Quite mode
- Normal scan vs Recursive scan
- Post method
- Delay request
- Version scan

### **Introduction to Dirsearch**

Dirsearch is a professional command-line method for the brute force of web server folders and files. It has now become the top Web content scanner with 6 years of success.

It provides users with the ability to explore complex web content as a feature-rich tool, with many wordlist vectors, high accuracy, impressive performance, advanced connection/request settings, modern brute-force techniques and nice results.

It is a strong competitor in the directory scanner arena, with features such as multi-threading, proxy support, request latency, user agent randomization, and support for multiple extensions.

It is being actively developed by **[@maurosoria](https://twitter.com/_maurosoria)** and **[@shelld3v](https://github.com/shelld3v)**.

**Setup**

It is a Python-written method used to brute-force web directories and files that are secret. It can run on Windows, Linux, and macOS, and provides a simple but powerful interface for the command line.

We are installing this tool in our kali, using the git-clone command to install Dirsearch web content scanner tool.

git clone https://github.com/maurosoria/dirsearch.git

![](https://1.bp.blogspot.com/-kORrV0vX19Q/YAcPpw-UCxI/AAAAAAAAtDQ/p_CCJxE5G_IsD68on2gnCosto1p2ykiggCLcBGAsYHQ/s16000/1.png)

After installing this tool, we need to navigate through its directories and search for dirsearch.py. Now, all we need just run this python written tool with [-h] parameter through this we can see all its parameter with their functions.

./dirsearch.py -h

![](https://1.bp.blogspot.com/-ihSpO73B3n4/YAcP76qLKOI/AAAAAAAAtDY/se-m92i2lpMnitCEk6NEyV66F4FkLCZEwCLcBGAsYHQ/s16000/2.png)

Let’s get started  

### **Target URL**

We can use our web content scanner on a specific targeted URL with the help of [-u] parameter. To get appropriate results we need to make sure that it is an authenticated URL follow this command to get the desired results.

./dirsearch.py -u http://testphp.vulnweb.com/

As we can see we got some web directories and web pages.

![](https://1.bp.blogspot.com/-6EUuj0P931k/YAcQCOsvo3I/AAAAAAAAtDc/ecGFKs24U6ImeLf0vgO8OTopkFvReCAAwCLcBGAsYHQ/s16000/3.png)

### **Save Output in Different Formats**

We can save our output which we get from the attack in different-different formats to learn further from them. This parameter helps us to get through those details of these formats. Let’s explore them one by one.

**Save output in Simple format**

We can save our result in the simple format with the help of [–simple-report] parameter. Through this feature, we can better analyse the results which we got from this attack. Follow this command to proceed further.

./dirsearch.py -u http://testphp.vulnweb.com/ --simple-report=report

![](https://1.bp.blogspot.com/-IOmPJH6JhDw/YAcQHn-0OVI/AAAAAAAAtDg/Hp4G-P-GRsIKqYrrvpP1d-pvtcK-WkfRQCLcBGAsYHQ/s16000/4.png)

After creating this report, we can cross verify its location in the system. Now use nano command to see this report.

![](https://1.bp.blogspot.com/-e-5Vu0QXD1c/YAcQNUqaBkI/AAAAAAAAtDk/6nJ1mPEdRWoAstUlSM7DWMycB99k9HzDgCLcBGAsYHQ/s16000/5.png)

As we can clearly see that our simple format result is successfully created. Now, we can analyse our results easily.

![](https://1.bp.blogspot.com/-YcKVMuOihSw/YAcQSIwvPAI/AAAAAAAAtDs/06J_bDxphlsxTgjLW0ogTOlhFpzUFRt2ACLcBGAsYHQ/s16000/6.png)

**Save output in JSON format**

JSON is an open standard file format and data exchange format that stores and transmits data objects consisting of attribute-value pairs and array data types using human-readable text. It is a very common data format with a wide variety of uses, such as being used in AJAX systems as a substitute for XML. With this method, we can build this kind of output result format by just following these commands.

./dirsearch.py -u http://testphp.vulnweb.com/ --json-report=report

![](https://1.bp.blogspot.com/-qAo2sZtwwEY/YAcQWeb0F0I/AAAAAAAAtDw/GOApxXGwiNoDOleKl2L_rHP4n6rH-jTtgCLcBGAsYHQ/s16000/7.png)

Similarly, as above we are using nano command to start analysing our result.

![](https://1.bp.blogspot.com/-L2PLQBqV8fI/YAcQaapeZUI/AAAAAAAAtD4/cWXbSLxTmC0RAdNPTDNWE-EJKOZp9HuhQCLcBGAsYHQ/s16000/8.png)

**Save output in XML format**

Extensible Mark-up Language (XML) is a mark-up language that specifies a collection of rules that are both human-readable and machine-readable to encode documents in a format. By using some commands, we can build our XML format result copy with this tool.

./dirsearch.py -u http://testphp.vulnweb.com/ --xml-report=report

![](https://1.bp.blogspot.com/-7uRS0TUNWuo/YAcQgSZYQtI/AAAAAAAAtEA/UWZxXscCpY83F9mLFAZlaav1kMYcN0jVgCLcBGAsYHQ/s16000/9.png)

Similarly, as above we are using nano command to start analysing our result.

![](https://1.bp.blogspot.com/-nVUA1QmpIIE/YAcQlemW7XI/AAAAAAAAtEE/LV8OCQEGKScKx4ZazB9xwc88gUkzNOm-ACLcBGAsYHQ/s16000/10.png)

**Save output in Markdown format** 

For creating formatted text using a plain-text editor, Markdown is a lightweight mark-up language. In 2004, John Gruber and Aaron Swartz created Markdown as a mark-up language that, in its source code form, appeals to human readers. We can build our markdown format result copy by using this command with this tool.

./dirsearch.py -u http://testphp.vulnweb.com/ --markdown-report=report

![](https://1.bp.blogspot.com/-wZ6HH3u9EQw/YAcQqS5VIeI/AAAAAAAAtEQ/bUC-qyUAJuYNa_hansamN6Rn0uwGcNaVwCLcBGAsYHQ/s16000/11.png)

Similarly, as above we are using nano command to start analysing our result.

![](https://1.bp.blogspot.com/-DWYaDggN87Y/YAcQvL7T_UI/AAAAAAAAtEU/hV3QfTcapTYHFmuFVegISjD-ZDU2c6JwwCLcBGAsYHQ/s16000/12.png)

**Save Output in CSV format**

A comma-separated value file is a delimited text file that separates values using a comma. A data record is any line of the file. Each record, separated by commas, consists of one or more fields. By using some commands, we can build our CSV result copy with this method.

./dirsearch.py -u http://testphp.vulnweb.com/ --csv-report=report

![](https://1.bp.blogspot.com/-u2lCKxQH6Ww/YAcQ0M9O7wI/AAAAAAAAtEc/1cSJydoE7g4PFfDKH3JSeSU3QJCipofDQCLcBGAsYHQ/s16000/13.png)

Similarly, as above we are using nano command to start analysing our result.

![](https://1.bp.blogspot.com/-TOpQSCE7lHU/YAcQ6AYUAJI/AAAAAAAAtEo/sTKTv0G1vLQmfz0opP5vC6mYUl6XFe_mwCLcBGAsYHQ/s16000/14.png)

**Save output in Plain format**

Simple text is a loose term for knowledge in computing that only represents characters of readable content, but not its graphical representation or other artefacts. It may also include a limited number of whitespace characters, such as spaces, line breaks, or tab characters, that affect the simple arrangement of text. By using some commands, we can create a plain text results copy with this method.

./dirsearch.py -u http://testphp.vulnweb.com/ --plain-text-report=report

![](https://1.bp.blogspot.com/-45NlQoiQRqk/YAcQ_FCTQpI/AAAAAAAAtEs/qy00D9eeAKIy-aKSQNkEwOi3m9x0fgl4wCLcBGAsYHQ/s16000/15.png)

Similarly, as above we are using nano command to start analysing our result.

![](https://1.bp.blogspot.com/-J6O1y7b89TM/YAcREyXchLI/AAAAAAAAtEw/dt57_79_Fi4aTMgx-rNmPhQoXhd8j_N1gCLcBGAsYHQ/s16000/16.png)

### **No Colour**

If colours are bothering us from concentrating on our analysis or results. We can remove all the colours occurs in our results from the attack, by using [**–no-colour**] parameter we can achieve this function. Follow this command to get these results.

./dirsearch.py -u http://testphp.vulnweb.com/ --no-color

![](https://1.bp.blogspot.com/-yw10KucTwaU/YAcRLXVbQ8I/AAAAAAAAtE4/ACgiSW_puZIFlchSKOpHMrmgpbLVRlt6QCLcBGAsYHQ/s16000/17.png)

### **Quite Mode**

Quite mode is used in a more hush-hush manner to run dirsearch. If you’re the type of person who doesn’t want a huge banner telling everybody what you’re doing on your system, you’ll like this choice. Basically, this allows for a cleaner screen as it executes the commands you send it, without the funny cow showing up on top.

Just use this [-q] parameter with this command to see the results

./dirsearch.py -u http://testphp.vulnweb.com/ -q

![](https://1.bp.blogspot.com/-nTPnjn3kz-g/YAcRQSrWAHI/AAAAAAAAtE8/q4EIwOB6-5sFOPaHHK_g_0xR4wHQEVY0QCLcBGAsYHQ/s16000/18.png)

### **Normal scan vs Recursive scan**

The method of scanning everything in a folder, including subfolders, is known to all of us. We compare a normal scan against a recursive scan in this section.

Firstly, we only use the [-u] parameter in the normal scan to get through victim URLs. In order to begin this scan, follow this instruction.

./dirsearch.py -u http://testphp.vulnweb.com/

![](https://1.bp.blogspot.com/-d_FFjYaGWLA/YAcRVE9XvmI/AAAAAAAAtFE/aki4uwjMQeY2GxmwpehgD3L-A5DbEiuiQCLcBGAsYHQ/s16000/19.1.png)

Now, secondly, in the same command, when we use the parameter [-r] along with it. By just initiating this attack on the victim, it will help us go through each folder and its sub folders.

./dirsearch.py -u http://testphp.vulnweb.com/ -r

As we can see these results, with specific wording, it attaches some more results, such as added to the queue in the ongoing attack.

![](https://1.bp.blogspot.com/-zG5m8P1JBXM/YAcRZhBDjcI/AAAAAAAAtFI/C_riQSdoag8efLD-EC-qpr4gbos8dDXpACLcBGAsYHQ/s16000/19.2.png)

Now, after completing the usual scan for some time, it will go through each and every sub-folder for the recursive scan. As we can see clearly in this screenshot, it goes for the victim’s subfolders and tells us about our attack’s incomplete work.

![](https://1.bp.blogspot.com/-pY8kNSAB_YA/YAcRewXGbaI/AAAAAAAAtFQ/auejv6YvwcMBSsmSe5A6BrtC9vhEk1XyQCLcBGAsYHQ/s16000/19.3.png)

### **Post method**

We know that, for a given resource, HTTP defines a set of request methods to indicate the required action to be performed.

But in the post method, POST is an HTTP supported request method used by the World Wide Web. The POST request method, by design, requires a web server to accept the data enclosed in the request message body, most likely to store it. It normally works with the GET HTTP method, which is used in the name or value pair to append the form data to the URL. If you use GET, the URL length will remain restricted. This enables users to submit the result of the bookmark.

Now, we are exploring this other side with the help of [-m] parameter with this command.

As we can these results are different and unique in comparison to the GET request method which we performed earlier. It shows some different web pages and web directories.

./dirsearch.py -u http://testphp.vulnweb.com/ -m POST

![](https://1.bp.blogspot.com/-8fQ2j8OlXOI/YAcRkHkL7-I/AAAAAAAAtFY/uScLCo7Yl14xdn-Nc_RP6LSNXptJZ26SQCLcBGAsYHQ/s16000/20.png)

### **Delay request**

It just another normal scan with some specific delay between each and every request in our attack. These sort of things provide proper exposure of a particular request. We can achieve this feature with the help of [-s] parameter with specified time in seconds.

./dirsearch.py -u http://testphp.vulnweb.com/ -s 10

![](https://1.bp.blogspot.com/-L3tWLW37t3k/YAcRolsygiI/AAAAAAAAtFc/IFw2hASwcFE5R4FtzQVclRiq_LUje74NQCLcBGAsYHQ/s16000/21.png)

### **Version scan**

As we all know that our dirsearch web content scanner is constantly being updating with the time. Some feature will add in the with the demand of time. We can use [–version] parameter to see that, if our tool is up to date or not.

./dirsearch.py --version

![](https://1.bp.blogspot.com/-cnT5nY_iaSg/YAcRtet5-AI/AAAAAAAAtFk/8uHGqPKAaD83mzq7uHwHmmh8si0SKVPVwCLcBGAsYHQ/s16000/22.png)

This is our first instalment in the series of Dirsearch’s Beginners Guide. Cantered on some of Dirsearch’s core functions. In this incredible method, stay tuned for more advance option.

**Author**: Shubham Sharma is a passionate Cybersecurity Researcher, contact **[LinkedIn](https://www.linkedin.com/in/shubham-sharma-626964153/)** and **[Twitter](https://twitter.com/Shubham_pen)**.

**Credit:** This information was adapted from an excellent guide on [HackingArticles.in](https://www.hackingarticles.in/comprehensive-guide-on-dirsearch/). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/E9nLtfsWa8M?si=T0HItB7wQhWtNlZO" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=E9nLtfsWa8M). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Rkb9I52Ht1c?si=sZ4rBisshizOIwDu" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=Rkb9I52Ht1c&t=69s). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/jVxs5at0gxg?si=HLgnp5DJ72pUY7Sh" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=jVxs5at0gxg). Be sure to check out the original post for more details.



