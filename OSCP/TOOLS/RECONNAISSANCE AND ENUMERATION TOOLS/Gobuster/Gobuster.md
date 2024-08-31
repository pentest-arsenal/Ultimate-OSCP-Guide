# Gobuster

[](https://github.com/OJ/gobuster#gobuster)

Gobuster is a tool used to brute-force:

- URIs (directories and files) in web sites.
- DNS subdomains (with wildcard support).
- Virtual Host names on target web servers.
- Open Amazon S3 buckets
- Open Google Cloud buckets
- TFTP servers

## Tags, Statuses, etc

[](https://github.com/OJ/gobuster#tags-statuses-etc)

[![Build Status](https://camo.githubusercontent.com/394a227d5a2c5f5a98f4c347c318fb2723534fd27da6d1e426857f50b05b8a94/68747470733a2f2f7472617669732d63692e636f6d2f4f4a2f676f6275737465722e7376673f6272616e63683d6d6173746572)](https://travis-ci.com/OJ/gobuster) [![Backers on Open Collective](https://camo.githubusercontent.com/433c844c44f73a261b5b1d59f4ca742376370ba3f5450a4c7c766c1c18065644/68747470733a2f2f6f70656e636f6c6c6563746976652e636f6d2f676f6275737465722f6261636b6572732f62616467652e737667)](https://opencollective.com/gobuster) [![Sponsors on Open Collective](https://camo.githubusercontent.com/a7f277eade3f9050fa4b174366f3ba0b737cad5a76038b1c6175ea33ccc4edfe/68747470733a2f2f6f70656e636f6c6c6563746976652e636f6d2f676f6275737465722f73706f6e736f72732f62616467652e737667)](https://opencollective.com/gobuster)

## Love this tool? Back it!

[](https://github.com/OJ/gobuster#love-this-tool-back-it)

If you're backing us already, you rock. If you're not, that's cool too! Want to back us? [Become a backer](https://opencollective.com/gobuster#backer)!

[![Backers](https://camo.githubusercontent.com/b8167178b76d228193dfbb31e7a75288f55dd6391308e11774d845b80b8603d9/68747470733a2f2f6f70656e636f6c6c6563746976652e636f6d2f676f6275737465722f6261636b6572732e7376673f77696474683d383930)](https://opencollective.com/gobuster#backers)

All funds that are donated to this project will be donated to charity. A full log of charity donations will be available in this repository as they are processed.

# Changes

[](https://github.com/OJ/gobuster#changes)

## 3.6

[](https://github.com/OJ/gobuster#36)

- Wordlist offset parameter to skip x lines from the wordlist
- prevent double slashes when building up an url in dir mode
- allow for multiple values and ranges on `--exclude-length`
- `no-fqdn` parameter on dns bruteforce to disable the use of the systems search domains. This should speed up the run if you have configured some search domains. [#418](https://github.com/OJ/gobuster/pull/418)

## 3.5

[](https://github.com/OJ/gobuster#35)

- Allow Ranges in status code and status code blacklist. Example: 200,300-305,404

## 3.4

[](https://github.com/OJ/gobuster#34)

- Enable TLS1.0 and TLS1.1 support
- Add TFTP mode to search for files on tftp servers

## 3.3

[](https://github.com/OJ/gobuster#33)

- Support TLS client certificates / mtls
- support loading extensions from file
- support fuzzing POST body, HTTP headers and basic auth
- new option to not canonicalize header names

## 3.2

[](https://github.com/OJ/gobuster#32)

- Use go 1.19
- use contexts in the correct way
- get rid of the wildcard flag (except in DNS mode)
- color output
- retry on timeout
- google cloud bucket enumeration
- fix nil reference errors

## 3.1

[](https://github.com/OJ/gobuster#31)

- enumerate public AWS S3 buckets
- fuzzing mode
- specify HTTP method
- added support for patterns. You can now specify a file containing patterns that are applied to every word, one by line. Every occurrence of the term `{GOBUSTER}` in it will be replaced with the current wordlist item. Please use with caution as this can cause increase the number of requests issued a lot.
- The shorthand `p` flag which was assigned to proxy is now used by the pattern flag

## 3.0

[](https://github.com/OJ/gobuster#30)

- New CLI options so modes are strictly separated (`-m` is now gone!)
- Performance Optimizations and better connection handling
- Ability to enumerate vhost names
- Option to supply custom HTTP headers

# License

[](https://github.com/OJ/gobuster#license)

See the LICENSE file.

# Manual

[](https://github.com/OJ/gobuster#manual)

## Available Modes

[](https://github.com/OJ/gobuster#available-modes)

- dir - the classic directory brute-forcing mode
- dns - DNS subdomain brute-forcing mode
- s3 - Enumerate open S3 buckets and look for existence and bucket listings
- gcs - Enumerate open google cloud buckets
- vhost - virtual host brute-forcing mode (not the same as DNS!)
- fuzz - some basic fuzzing, replaces the `FUZZ` keyword
- tftp - bruteforce tftp files

## Easy Installation

[](https://github.com/OJ/gobuster#easy-installation)

### Binary Releases

[](https://github.com/OJ/gobuster#binary-releases)

We are now shipping binaries for each of the releases so that you don't even have to build them yourself! How wonderful is that!

If you're stupid enough to trust binaries that I've put together, you can download them from the [releases](https://github.com/OJ/gobuster/releases) page.

### Docker

[](https://github.com/OJ/gobuster#docker)

You can also grab a prebuilt docker image from [https://github.com/OJ/gobuster/pkgs/container/gobuster](https://github.com/OJ/gobuster/pkgs/container/gobuster)

```shell
docker pull ghcr.io/oj/gobuster:latest
```

### Using `go install`

[](https://github.com/OJ/gobuster#using-go-install)

If you have a [Go](https://golang.org/) environment ready to go (at least go 1.19), it's as easy as:

```shell
go install github.com/OJ/gobuster/v3@latest
```

PS: You need at least go 1.19 to compile gobuster.

### Building From Source

[](https://github.com/OJ/gobuster#building-from-source)

Since this tool is written in [Go](https://golang.org/) you need to install the Go language/compiler/etc. Full details of installation and set up can be found [on the Go language website](https://golang.org/doc/install). Once installed you have two options. You need at least go 1.19 to compile gobuster.

### Compiling

[](https://github.com/OJ/gobuster#compiling)

`gobuster` has external dependencies, and so they need to be pulled in first:

```shell
go get && go build
```

This will create a `gobuster` binary for you. If you want to install it in the `$GOPATH/bin` folder you can run:

```shell
go install
```

## Modes

[](https://github.com/OJ/gobuster#modes)

Help is built-in!

- `gobuster help` - outputs the top-level help.
- `gobuster help <mode>` - outputs the help specific to that mode.

## `dns` Mode

[](https://github.com/OJ/gobuster#dns-mode)

### Options

[](https://github.com/OJ/gobuster#options)

```
Uses DNS subdomain enumeration mode

Usage:
  gobuster dns [flags]

Flags:
  -d, --domain string      The target domain
  -h, --help               help for dns
  -r, --resolver string    Use custom DNS server (format server.com or server.com:port)
  -c, --show-cname         Show CNAME records (cannot be used with '-i' option)
  -i, --show-ips           Show IP addresses
      --timeout duration   DNS resolver timeout (default 1s)
      --wildcard           Force continued operation when wildcard found

Global Flags:
      --delay duration    Time each thread waits between requests (e.g. 1500ms)
      --no-color          Disable color output
      --no-error          Don't display errors
  -z, --no-progress       Don't display progress
  -o, --output string     Output file to write results to (defaults to stdout)
  -p, --pattern string    File containing replacement patterns
  -q, --quiet             Don't print the banner and other noise
  -t, --threads int       Number of concurrent threads (default 10)
  -v, --verbose           Verbose output (errors)
  -w, --wordlist string   Path to the wordlist
```

### Examples

[](https://github.com/OJ/gobuster#examples)

```
gobuster dns -d mysite.com -t 50 -w common-names.txt
```

Normal sample run goes like this:

```
gobuster dns -d google.com -w ~/wordlists/subdomains.txt

===============================================================
Gobuster v3.2.0
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Mode         : dns
[+] Url/Domain   : google.com
[+] Threads      : 10
[+] Wordlist     : /home/oj/wordlists/subdomains.txt
===============================================================
2019/06/21 11:54:20 Starting gobuster
===============================================================
Found: chrome.google.com
Found: ns1.google.com
Found: admin.google.com
Found: www.google.com
Found: m.google.com
Found: support.google.com
Found: translate.google.com
Found: cse.google.com
Found: news.google.com
Found: music.google.com
Found: mail.google.com
Found: store.google.com
Found: mobile.google.com
Found: search.google.com
Found: wap.google.com
Found: directory.google.com
Found: local.google.com
Found: blog.google.com
===============================================================
2019/06/21 11:54:20 Finished
===============================================================
```

Show IP sample run goes like this:

```
gobuster dns -d google.com -w ~/wordlists/subdomains.txt -i

===============================================================
Gobuster v3.2.0
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Mode         : dns
[+] Url/Domain   : google.com
[+] Threads      : 10
[+] Wordlist     : /home/oj/wordlists/subdomains.txt
===============================================================
2019/06/21 11:54:54 Starting gobuster
===============================================================
Found: www.google.com [172.217.25.36, 2404:6800:4006:802::2004]
Found: admin.google.com [172.217.25.46, 2404:6800:4006:806::200e]
Found: store.google.com [172.217.167.78, 2404:6800:4006:802::200e]
Found: mobile.google.com [172.217.25.43, 2404:6800:4006:802::200b]
Found: ns1.google.com [216.239.32.10, 2001:4860:4802:32::a]
Found: m.google.com [172.217.25.43, 2404:6800:4006:802::200b]
Found: cse.google.com [172.217.25.46, 2404:6800:4006:80a::200e]
Found: chrome.google.com [172.217.25.46, 2404:6800:4006:802::200e]
Found: search.google.com [172.217.25.46, 2404:6800:4006:802::200e]
Found: local.google.com [172.217.25.46, 2404:6800:4006:80a::200e]
Found: news.google.com [172.217.25.46, 2404:6800:4006:802::200e]
Found: blog.google.com [216.58.199.73, 2404:6800:4006:806::2009]
Found: support.google.com [172.217.25.46, 2404:6800:4006:802::200e]
Found: wap.google.com [172.217.25.46, 2404:6800:4006:802::200e]
Found: directory.google.com [172.217.25.46, 2404:6800:4006:802::200e]
Found: translate.google.com [172.217.25.46, 2404:6800:4006:802::200e]
Found: music.google.com [172.217.25.46, 2404:6800:4006:802::200e]
Found: mail.google.com [172.217.25.37, 2404:6800:4006:802::2005]
===============================================================
2019/06/21 11:54:55 Finished
===============================================================
```

Base domain validation warning when the base domain fails to resolve. This is a warning rather than a failure in case the user fat-fingers while typing the domain.

```
gobuster dns -d yp.to -w ~/wordlists/subdomains.txt -i

===============================================================
Gobuster v3.2.0
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Mode         : dns
[+] Url/Domain   : yp.to
[+] Threads      : 10
[+] Wordlist     : /home/oj/wordlists/subdomains.txt
===============================================================
2019/06/21 11:56:43 Starting gobuster
===============================================================
2019/06/21 11:56:53 [-] Unable to validate base domain: yp.to
Found: cr.yp.to [131.193.32.108, 131.193.32.109]
===============================================================
2019/06/21 11:56:53 Finished
===============================================================
```

Wildcard DNS is also detected properly:

```
gobuster dns -d 0.0.1.xip.io -w ~/wordlists/subdomains.txt

===============================================================
Gobuster v3.2.0
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Mode         : dns
[+] Url/Domain   : 0.0.1.xip.io
[+] Threads      : 10
[+] Wordlist     : /home/oj/wordlists/subdomains.txt
===============================================================
2019/06/21 12:13:48 Starting gobuster
===============================================================
2019/06/21 12:13:48 [-] Wildcard DNS found. IP address(es): 1.0.0.0
2019/06/21 12:13:48 [!] To force processing of Wildcard DNS, specify the '--wildcard' switch.
===============================================================
2019/06/21 12:13:48 Finished
===============================================================
```

If the user wants to force processing of a domain that has wildcard entries, use `--wildcard`:

```
gobuster dns -d 0.0.1.xip.io -w ~/wordlists/subdomains.txt --wildcard

===============================================================
Gobuster v3.2.0
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Mode         : dns
[+] Url/Domain   : 0.0.1.xip.io
[+] Threads      : 10
[+] Wordlist     : /home/oj/wordlists/subdomains.txt
===============================================================
2019/06/21 12:13:51 Starting gobuster
===============================================================
2019/06/21 12:13:51 [-] Wildcard DNS found. IP address(es): 1.0.0.0
Found: 127.0.0.1.xip.io
Found: test.127.0.0.1.xip.io
===============================================================
2019/06/21 12:13:53 Finished
===============================================================
```

## `dir` Mode

[](https://github.com/OJ/gobuster#dir-mode)

### Options

[](https://github.com/OJ/gobuster#options-1)

```
Uses directory/file enumeration mode

Usage:
  gobuster dir [flags]

Flags:
  -f, --add-slash                       Append / to each request
  -c, --cookies string                  Cookies to use for the requests
  -d, --discover-backup                 Also search for backup files by appending multiple backup extensions
      --exclude-length ints             exclude the following content length (completely ignores the status). Supply multiple times to exclude multiple sizes.
  -e, --expanded                        Expanded mode, print full URLs
  -x, --extensions string               File extension(s) to search for
  -r, --follow-redirect                 Follow redirects
  -H, --headers stringArray             Specify HTTP headers, -H 'Header1: val1' -H 'Header2: val2'
  -h, --help                            help for dir
      --hide-length                     Hide the length of the body in the output
  -m, --method string                   Use the following HTTP method (default "GET")
  -n, --no-status                       Don't print status codes
  -k, --no-tls-validation               Skip TLS certificate verification
  -P, --password string                 Password for Basic Auth
      --proxy string                    Proxy to use for requests [http(s)://host:port]
      --random-agent                    Use a random User-Agent string
      --retry                           Should retry on request timeout
      --retry-attempts int              Times to retry on request timeout (default 3)
  -s, --status-codes string             Positive status codes (will be overwritten with status-codes-blacklist if set)
  -b, --status-codes-blacklist string   Negative status codes (will override status-codes if set) (default "404")
      --timeout duration                HTTP Timeout (default 10s)
  -u, --url string                      The target URL
  -a, --useragent string                Set the User-Agent string (default "gobuster/3.2.0")
  -U, --username string                 Username for Basic Auth

Global Flags:
      --delay duration    Time each thread waits between requests (e.g. 1500ms)
      --no-color          Disable color output
      --no-error          Don't display errors
  -z, --no-progress       Don't display progress
  -o, --output string     Output file to write results to (defaults to stdout)
  -p, --pattern string    File containing replacement patterns
  -q, --quiet             Don't print the banner and other noise
  -t, --threads int       Number of concurrent threads (default 10)
  -v, --verbose           Verbose output (errors)
  -w, --wordlist string   Path to the wordlist
```

### Examples

[](https://github.com/OJ/gobuster#examples-1)

```
gobuster dir -u https://mysite.com/path/to/folder -c 'session=123456' -t 50 -w common-files.txt -x .php,.html
```

Default options looks like this:

```
gobuster dir -u https://buffered.io -w ~/wordlists/shortlist.txt

===============================================================
Gobuster v3.2.0
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Mode         : dir
[+] Url/Domain   : https://buffered.io/
[+] Threads      : 10
[+] Wordlist     : /home/oj/wordlists/shortlist.txt
[+] Status codes : 200,204,301,302,307,401,403
[+] User Agent   : gobuster/3.2.0
[+] Timeout      : 10s
===============================================================
2019/06/21 11:49:43 Starting gobuster
===============================================================
/categories (Status: 301)
/contact (Status: 301)
/posts (Status: 301)
/index (Status: 200)
===============================================================
2019/06/21 11:49:44 Finished
===============================================================
```

Default options with status codes disabled looks like this:

```
gobuster dir -u https://buffered.io -w ~/wordlists/shortlist.txt -n

===============================================================
Gobuster v3.2.0
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Mode         : dir
[+] Url/Domain   : https://buffered.io/
[+] Threads      : 10
[+] Wordlist     : /home/oj/wordlists/shortlist.txt
[+] Status codes : 200,204,301,302,307,401,403
[+] User Agent   : gobuster/3.2.0
[+] No status    : true
[+] Timeout      : 10s
===============================================================
2019/06/21 11:50:18 Starting gobuster
===============================================================
/categories
/contact
/index
/posts
===============================================================
2019/06/21 11:50:18 Finished
===============================================================
```

Verbose output looks like this:

```
gobuster dir -u https://buffered.io -w ~/wordlists/shortlist.txt -v

===============================================================
Gobuster v3.2.0
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Mode         : dir
[+] Url/Domain   : https://buffered.io/
[+] Threads      : 10
[+] Wordlist     : /home/oj/wordlists/shortlist.txt
[+] Status codes : 200,204,301,302,307,401,403
[+] User Agent   : gobuster/3.2.0
[+] Verbose      : true
[+] Timeout      : 10s
===============================================================
2019/06/21 11:50:51 Starting gobuster
===============================================================
Missed: /alsodoesnotexist (Status: 404)
Found: /index (Status: 200)
Missed: /doesnotexist (Status: 404)
Found: /categories (Status: 301)
Found: /posts (Status: 301)
Found: /contact (Status: 301)
===============================================================
2019/06/21 11:50:51 Finished
===============================================================
```

Example showing content length:

```
gobuster dir -u https://buffered.io -w ~/wordlists/shortlist.txt -l

===============================================================
Gobuster v3.2.0
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Mode         : dir
[+] Url/Domain   : https://buffered.io/
[+] Threads      : 10
[+] Wordlist     : /home/oj/wordlists/shortlist.txt
[+] Status codes : 200,204,301,302,307,401,403
[+] User Agent   : gobuster/3.2.0
[+] Show length  : true
[+] Timeout      : 10s
===============================================================
2019/06/21 11:51:16 Starting gobuster
===============================================================
/categories (Status: 301) [Size: 178]
/posts (Status: 301) [Size: 178]
/contact (Status: 301) [Size: 178]
/index (Status: 200) [Size: 51759]
===============================================================
2019/06/21 11:51:17 Finished
===============================================================
```

Quiet output, with status disabled and expanded mode looks like this ("grep mode"):

```
gobuster dir -u https://buffered.io -w ~/wordlists/shortlist.txt -q -n -e
https://buffered.io/index
https://buffered.io/contact
https://buffered.io/posts
https://buffered.io/categories
```

## `vhost` Mode

[](https://github.com/OJ/gobuster#vhost-mode)

### Options

[](https://github.com/OJ/gobuster#options-2)

```
Uses VHOST enumeration mode (you most probably want to use the IP address as the URL parameter)

Usage:
  gobuster vhost [flags]

Flags:
      --append-domain         Append main domain from URL to words from wordlist. Otherwise the fully qualified domains need to be specified in the wordlist.
  -c, --cookies string        Cookies to use for the requests
      --domain string         the domain to append when using an IP address as URL. If left empty and you specify a domain based URL the hostname from the URL is extracted
      --exclude-length ints   exclude the following content length (completely ignores the status). Supply multiple times to exclude multiple sizes.
  -r, --follow-redirect       Follow redirects
  -H, --headers stringArray   Specify HTTP headers, -H 'Header1: val1' -H 'Header2: val2'
  -h, --help                  help for vhost
  -m, --method string         Use the following HTTP method (default "GET")
  -k, --no-tls-validation     Skip TLS certificate verification
  -P, --password string       Password for Basic Auth
      --proxy string          Proxy to use for requests [http(s)://host:port]
      --random-agent          Use a random User-Agent string
      --retry                 Should retry on request timeout
      --retry-attempts int    Times to retry on request timeout (default 3)
      --timeout duration      HTTP Timeout (default 10s)
  -u, --url string            The target URL
  -a, --useragent string      Set the User-Agent string (default "gobuster/3.2.0")
  -U, --username string       Username for Basic Auth

Global Flags:
      --delay duration    Time each thread waits between requests (e.g. 1500ms)
      --no-color          Disable color output
      --no-error          Don't display errors
  -z, --no-progress       Don't display progress
  -o, --output string     Output file to write results to (defaults to stdout)
  -p, --pattern string    File containing replacement patterns
  -q, --quiet             Don't print the banner and other noise
  -t, --threads int       Number of concurrent threads (default 10)
  -v, --verbose           Verbose output (errors)
  -w, --wordlist string   Path to the wordlist
```

### Examples

[](https://github.com/OJ/gobuster#examples-2)

```
gobuster vhost -u https://mysite.com -w common-vhosts.txt
```

Normal sample run goes like this:

```
gobuster vhost -u https://mysite.com -w common-vhosts.txt

===============================================================
Gobuster v3.2.0
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:          https://mysite.com
[+] Threads:      10
[+] Wordlist:     common-vhosts.txt
[+] User Agent:   gobuster/3.2.0
[+] Timeout:      10s
===============================================================
2019/06/21 08:36:00 Starting gobuster
===============================================================
Found: www.mysite.com
Found: piwik.mysite.com
Found: mail.mysite.com
===============================================================
2019/06/21 08:36:05 Finished
===============================================================
```

## `fuzz` Mode

[](https://github.com/OJ/gobuster#fuzz-mode)

### Options

[](https://github.com/OJ/gobuster#options-3)

```
Uses fuzzing mode

Usage:
  gobuster fuzz [flags]

Flags:
  -c, --cookies string              Cookies to use for the requests
      --exclude-length ints         exclude the following content length (completely ignores the status). Supply multiple times to exclude multiple sizes.
  -b, --excludestatuscodes string   Negative status codes (will override statuscodes if set)
  -r, --follow-redirect             Follow redirects
  -H, --headers stringArray         Specify HTTP headers, -H 'Header1: val1' -H 'Header2: val2'
  -h, --help                        help for fuzz
  -m, --method string               Use the following HTTP method (default "GET")
  -k, --no-tls-validation           Skip TLS certificate verification
  -P, --password string             Password for Basic Auth
      --proxy string                Proxy to use for requests [http(s)://host:port]
      --random-agent                Use a random User-Agent string
      --retry                       Should retry on request timeout
      --retry-attempts int          Times to retry on request timeout (default 3)
      --timeout duration            HTTP Timeout (default 10s)
  -u, --url string                  The target URL
  -a, --useragent string            Set the User-Agent string (default "gobuster/3.2.0")
  -U, --username string             Username for Basic Auth

Global Flags:
      --delay duration    Time each thread waits between requests (e.g. 1500ms)
      --no-color          Disable color output
      --no-error          Don't display errors
  -z, --no-progress       Don't display progress
  -o, --output string     Output file to write results to (defaults to stdout)
  -p, --pattern string    File containing replacement patterns
  -q, --quiet             Don't print the banner and other noise
  -t, --threads int       Number of concurrent threads (default 10)
  -v, --verbose           Verbose output (errors)
  -w, --wordlist string   Path to the wordlist
```

### Examples

[](https://github.com/OJ/gobuster#examples-3)

```
gobuster fuzz -u https://example.com?FUZZ=test -w parameter-names.txt
```

## `s3` Mode

[](https://github.com/OJ/gobuster#s3-mode)

### Options

[](https://github.com/OJ/gobuster#options-4)

```
Uses aws bucket enumeration mode

Usage:
  gobuster s3 [flags]

Flags:
  -h, --help                 help for s3
  -m, --maxfiles int         max files to list when listing buckets (only shown in verbose mode) (default 5)
  -k, --no-tls-validation    Skip TLS certificate verification
      --proxy string         Proxy to use for requests [http(s)://host:port]
      --random-agent         Use a random User-Agent string
      --retry                Should retry on request timeout
      --retry-attempts int   Times to retry on request timeout (default 3)
      --timeout duration     HTTP Timeout (default 10s)
  -a, --useragent string     Set the User-Agent string (default "gobuster/3.2.0")

Global Flags:
      --delay duration    Time each thread waits between requests (e.g. 1500ms)
      --no-color          Disable color output
      --no-error          Don't display errors
  -z, --no-progress       Don't display progress
  -o, --output string     Output file to write results to (defaults to stdout)
  -p, --pattern string    File containing replacement patterns
  -q, --quiet             Don't print the banner and other noise
  -t, --threads int       Number of concurrent threads (default 10)
  -v, --verbose           Verbose output (errors)
  -w, --wordlist string   Path to the wordlist
```

### Examples

[](https://github.com/OJ/gobuster#examples-4)

```
gobuster s3 -w bucket-names.txt
```

## `gcs` Mode

[](https://github.com/OJ/gobuster#gcs-mode)

### Options

[](https://github.com/OJ/gobuster#options-5)

```
Uses gcs bucket enumeration mode

Usage:
  gobuster gcs [flags]

Flags:
  -h, --help                 help for gcs
  -m, --maxfiles int         max files to list when listing buckets (only shown in verbose mode) (default 5)
  -k, --no-tls-validation    Skip TLS certificate verification
      --proxy string         Proxy to use for requests [http(s)://host:port]
      --random-agent         Use a random User-Agent string
      --retry                Should retry on request timeout
      --retry-attempts int   Times to retry on request timeout (default 3)
      --timeout duration     HTTP Timeout (default 10s)
  -a, --useragent string     Set the User-Agent string (default "gobuster/3.2.0")

Global Flags:
      --delay duration    Time each thread waits between requests (e.g. 1500ms)
      --no-color          Disable color output
      --no-error          Don't display errors
  -z, --no-progress       Don't display progress
  -o, --output string     Output file to write results to (defaults to stdout)
  -p, --pattern string    File containing replacement patterns
  -q, --quiet             Don't print the banner and other noise
  -t, --threads int       Number of concurrent threads (default 10)
  -v, --verbose           Verbose output (errors)
  -w, --wordlist string   Path to the wordlist
```

### Examples

[](https://github.com/OJ/gobuster#examples-5)

```
gobuster gcs -w bucket-names.txt
```

## `tftp` Mode

[](https://github.com/OJ/gobuster#tftp-mode)

### Options

[](https://github.com/OJ/gobuster#options-6)

```
Uses TFTP enumeration mode

Usage:
  gobuster tftp [flags]

Flags:
  -h, --help               help for tftp
  -s, --server string      The target TFTP server
      --timeout duration   TFTP timeout (default 1s)

Global Flags:
      --delay duration    Time each thread waits between requests (e.g. 1500ms)
      --no-color          Disable color output
      --no-error          Don't display errors
  -z, --no-progress       Don't display progress
  -o, --output string     Output file to write results to (defaults to stdout)
  -p, --pattern string    File containing replacement patterns
  -q, --quiet             Don't print the banner and other noise
  -t, --threads int       Number of concurrent threads (default 10)
  -v, --verbose           Verbose output (errors)
  -w, --wordlist string   Path to the wordlist
```

### Examples

[](https://github.com/OJ/gobuster#examples-6)

```
gobuster tftp -s tftp.example.com -w common-filenames.txt
```

## Wordlists via STDIN

[](https://github.com/OJ/gobuster#wordlists-via-stdin)

Wordlists can be piped into `gobuster` via stdin by providing a `-` to the `-w` option:

```shell
hashcat -a 3 --stdout ?l | gobuster dir -u https://mysite.com -w -
```

Note: If the `-w` option is specified at the same time as piping from STDIN, an error will be shown and the program will terminate.

## Patterns

[](https://github.com/OJ/gobuster#patterns)

You can supply pattern files that will be applied to every word from the wordlist. Just place the string `{GOBUSTER}` in it and this will be replaced with the word. This feature is also handy in s3 mode to pre- or postfix certain patterns.

**Caution:** Using a big pattern file can cause a lot of request as every pattern is applied to every word in the wordlist.

### Example file

[](https://github.com/OJ/gobuster#example-file)

```
{GOBUSTER}Partial
{GOBUSTER}Service
PRE{GOBUSTER}POST
{GOBUSTER}-prod
{GOBUSTER}-dev
```

#### Use case in combination with patterns

[](https://github.com/OJ/gobuster#use-case-in-combination-with-patterns)

- Create a custom wordlist for the target containing company names and so on
- Create a pattern file to use for common bucket names.

```shell
curl -s --output - https://raw.githubusercontent.com/eth0izzle/bucket-stream/master/permutations/extended.txt | sed -s 's/%s/{GOBUSTER}/' > patterns.txt
```

- Run gobuster with the custom input. Be sure to turn verbose mode on to see the bucket details

```
gobuster s3 --wordlist my.custom.wordlist -p patterns.txt -v
```

Normal sample run goes like this:

```
PS C:\Users\firefart\Documents\code\gobuster> .\gobuster.exe s3 --wordlist .\wordlist.txt
===============================================================
Gobuster v3.2.0
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Threads:                 10
[+] Wordlist:                .\wordlist.txt
[+] User Agent:              gobuster/3.2.0
[+] Timeout:                 10s
[+] Maximum files to list:   5
===============================================================
2019/08/12 21:48:16 Starting gobuster in S3 bucket enumeration mode
===============================================================
webmail
hacking
css
img
www
dav
web
localhost
===============================================================
2019/08/12 21:48:17 Finished
===============================================================
```

Verbose and sample run

```
PS C:\Users\firefart\Documents\code\gobuster> .\gobuster.exe s3 --wordlist .\wordlist.txt -v
===============================================================
Gobuster v3.2.0
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Threads:                 10
[+] Wordlist:                .\wordlist.txt
[+] User Agent:              gobuster/3.2.0
[+] Verbose:                 true
[+] Timeout:                 10s
[+] Maximum files to list:   5
===============================================================
2019/08/12 21:49:00 Starting gobuster in S3 bucket enumeration mode
===============================================================
www [Error: All access to this object has been disabled (AllAccessDisabled)]
hacking [Error: Access Denied (AccessDenied)]
css [Error: All access to this object has been disabled (AllAccessDisabled)]
webmail [Error: All access to this object has been disabled (AllAccessDisabled)]
img [Bucket Listing enabled: GodBlessPotomac1.jpg (1236807b), HOMEWORKOUTAUDIO.zip (203908818b), ProductionInfo.xml (11946b), Start of Perpetual Motion Logo-1.mp3 (621821b), addressbook.gif (3115b)]
web [Error: Access Denied (AccessDenied)]
dav [Error: All access to this object has been disabled (AllAccessDisabled)]
localhost [Error: Access Denied (AccessDenied)]
===============================================================
2019/08/12 21:49:01 Finished
===============================================================
```

Extended sample run

```
PS C:\Users\firefart\Documents\code\gobuster> .\gobuster.exe s3 --wordlist .\wordlist.txt -e
===============================================================
Gobuster v3.2.0
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Threads:                 10
[+] Wordlist:                .\wordlist.txt
[+] User Agent:              gobuster/3.2.0
[+] Timeout:                 10s
[+] Expanded:                true
[+] Maximum files to list:   5
===============================================================
2019/08/12 21:48:38 Starting gobuster in S3 bucket enumeration mode
===============================================================
http://css.s3.amazonaws.com/
http://www.s3.amazonaws.com/
http://webmail.s3.amazonaws.com/
http://hacking.s3.amazonaws.com/
http://img.s3.amazonaws.com/
http://web.s3.amazonaws.com/
http://dav.s3.amazonaws.com/
http://localhost.s3.amazonaws.com/
===============================================================
2019/08/12 21:48:38 Finished
===============================================================
```

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/OJ/gobuster). Be sure to check out the original post for more details.

# Gobuster tutorial

You would be surprised at what people leave **unprotected** on a web server.

An initial step in attacking a web application is Recon, and part of that entails enumerating hidden directories and files. Brute forcing web directories and filenames on a web server can often reveal unprotected web applications, scripts, old configuration files, and many other interesting things that should not be available to the public.

It is even possible to brute force virtual hosts to find hidden `vhosts` such as development sites or admin portals.

Gobuster is an aggressive scan. Its noisy and is noticed. Only use against systems you have permissions to scan against

Gobuster Tutorial & Tips

- [Install Gobuster](https://hackertarget.com/gobuster-tutorial/#install)
- [Setting up a Go environment](https://hackertarget.com/gobuster-tutorial/#go)
- [How to use Gobuster](https://hackertarget.com/gobuster-tutorial/#use)
- [Gobuster modes and flags](https://hackertarget.com/gobuster-tutorial/#modes)
- [Wordlists](https://hackertarget.com/gobuster-tutorial/#wordlists)
- [Gobuster DIR command](https://hackertarget.com/gobuster-tutorial/#DIR)
- [Threads](https://hackertarget.com/gobuster-tutorial/#threads)
- [Gobuster DNS Command](https://hackertarget.com/gobuster-tutorial/#dns)
- [Gobuster VHost Command](https://hackertarget.com/gobuster-tutorial/#vhost)

## Gobuster Installation

Written in the Go language, this tool enumerates hidden files along with the remote directories. Using the command line it is simple to install and run on Ubuntu 20.04.

For **version 2** its as simple as:

$ sudo apt install gobuster 

The Linux package may not be the latest version of Gobuster. Check [Repology: the packaging hub](https://repology.org/project/gobuster/packages), which shows the package of Gobuster is 2.0.1 (at the time of this article). The Github repository shows a newer version `V3.1.0`. [https://github.com/OJ/gobuster.git](https://github.com/OJ/gobuster.git)

![screenshot of information about gobuster](https://hackertarget.com/images/gobuster-info.webp)

Under "Easy installation" on the github page the options to install are binary releases, a Go install, and Building from source. For this install lets play around with the [Go install](https://go.dev/). Gobuster needs Go to be **at least v1.16**

### Setting up a Go environment (optional)

Download the GO install from here: [https://go.dev/dl/](https://go.dev/dl/)

change to the directory where Downloads normally arrive and do the following;

--> extract
$ sudo tar xvzf go1.17.7.linux-amd64.tar.gz 
--> change permissions
$ sudo chown -R root:root ./go
--> move to local directory
$ sudo mv -v go /usr/local

A local environment variable called $GOPATH needs to be set up. Since Go 1.8 this is not essential, though still recommended as some third party tools are still dependent on it.

Add the following to the `.bash_profile` Locate in home directory with `ls -la` .

export GOPATH=/usr/local/go
export PATH=$PATH:/usr/local/go/bin

To check its all worked and the Go environment is set up:

$ go version
go version go1.17.7 linux/amd64 

Now with the Go environment confirmed. Its simply a matter of using the following command to **install Gobuster**.

$ go install github.com/OJ/gobuster/v3@latest

check Gobuster is installed with:

$ gobuster version
3.1.0

## How to use Gobuster

Gobuster is now installed and ready to use. The rest of the tutorial is how to use Gobuster to **brute force** for files and directories.

## Gobuster modes and flags

Gobuster has a variety of modes/commands to use as shown below. This tutorial focuses on 3: **DIR, DNS**, and **VHOST**.

To see a general list of commands use: `gobuster -h` Each of these modes then has its own set of flags available for different uses of the tool.

 $ gobuster -h 
Usage:
  gobuster [command]

Available commands:
  dir         Uses directory/file enumeration mode
  dns         Uses DNS subdomain enumeration mode
  fuzz        Uses fuzzing mode
  help        Help about any command
  s3          Uses aws bucket enumeration mode
  version     shows the current version
  vhost       Uses VHOST enumeration mode

Flags: 
      --delay duration    Time each thread waits between requests (e.g. 1500ms)
  -h, --help              help for gobuster
      --no-error          Don't display errors
  -z, --no-progress       Don't display progress
  -o, --output string     Output file to write results to (defaults to stdout) 
  -p, --pattern string    File containing replacement patters
  -q, --quiet             Don't print the banner and other noise
  -t, --threads int       Number of concurrent threads (default 10)
  -v, --verbose           Verbose output (errors)
  -w, --wordlist string   Path to the wordlist
  

#### Wordlists

Gobuster needs wordlists. One of the essential flags for gobuster is `-w` . Wordlists can be obtained from various places. Depending on the individual setup, wordlists may be preinstalled or found within other packages, including wordlists from Dirb or Dirbuster. The ultimate source and "Pentesters friend" is **SecLists** - [https://github.com/danielmiessler/SecLists](https://github.com/danielmiessler/SecLists) which is a compilation of numerous lists held in one location.

## Gobuster DIR command

The DIR mode is used for finding hidden directories and files.

To find additional flags available to use `gobuster dir --help`

$ gobuster dir --help

Uses directory/file enumeration mode

Usage:
  gobuster dir [flags]

Flags:
  -f, --add-slash                       Append / to each request
  -c, --cookies string                  Cookies to use for the requests
  -d, --discover-backup                 Upon finding a file search for backup files
      --exclude-length ints             exclude the following content length (completely ignores the status). Supply multiple times to exclude multiple sizes.
  -e, --expanded                        Expanded mode, print full URLs
  -x, --extensions string               File extension(s) to search for
  -r, --follow-redirect                 Follow redirects
  -H, --headers stringArray             Specify HTTP headers, -H 'Header1: val1' -H 'Header2: val2'
  -h, --help                            help for dir
      --hide-length                     Hide the length of the body in the output
  -m, --method string                   Use the following HTTP method (default "GET")
  -n, --no-status                       Don't print status codes
  -k, --no-tls-validation               Skip TLS certificate verification
  -P, --password string                 Password for Basic Auth
      --proxy string                    Proxy to use for requests [http(s)://host:port]
      --random-agent                    Use a random User-Agent string
  -s, --status-codes string             Positive status codes (will be overwritten with status-codes-blacklist if set)
  -b, --status-codes-blacklist string   Negative status codes (will override status-codes if set) (default "404")
      --timeout duration                HTTP Timeout (default 10s)
  -u, --url string                      The target URL 
  -a, --useragent string                Set the User-Agent string (default "gobuster/3.1.0")
  -U, --username string                 Username for Basic Auth
      --wildcard                        Force continued operation when wildcard found

Global Flags:
      --delay duration    Time each thread waits between requests (e.g. 1500ms)
      --no-error          Don't display errors
  -z, --no-progress       Don't display progress
  -o, --output string     Output file to write results to (defaults to stdout)
  -p, --pattern string    File containing replacement patterns
  -q, --quiet             Don't print the banner and other noise
  -t, --threads int       Number of concurrent threads (default 10)
  -v, --verbose           Verbose output (errors)
  -w, --wordlist string   Path to the wordlist

### Flags

The 2 flags required to run a basic scan are `-u` `-w`. This example uses `common.txt` from the SecList wordlists.

user@matrix:$ gobuster dir -u https://example.com -w /wordlists/Discovery/Web-Content/common.txt  

Example results
===============================================================
Gobuster v3.1.0
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     https://example.com
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /wordlists/Discovery/Web-Content/common.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.1.0
[+] Timeout:                 10s
===============================================================
2022/03/01 10:34:16 Starting gobuster in directory enumeration mode
===============================================================
/assets              
/css                  
/download             

Not too many results and was quite heavy on the system processess. Results depend on the wordlist selected. It is worth working out which one is best for the job. The length of time depends on how large the wordlist is. It can also be worth creating a wordlist specific to the job at hand using a variety of resources.

### Threads

Gobuster is fast, with hundreds of requests being sent using the default 10 threads. This speeds can create problems with the system it is running on. It could be beneficial to drop this down to 4.

![screenshot of Gobuster's Global flags highlighting -t Threads](https://hackertarget.com/images/gobuster-threads.webp)

Additionally it can be helpful to use the flag `--delay duration Time each thread waits between requests (e.g. 1500ms).` For example `--delay 1s` in other words, if threads is set to 4 and --delay to 1s, this will send 4 requests per second.

$ gobuster dir -u https://example.com -w /wordlists/Discovery/Web-Content/big.txt -t 4 --delay 1s -o results.txt

### Results

Results are shown in the terminal, or use the `-o` option to output results to a file example `-o results.txt`

user@matrix:$ gobuster dir -u https://example.com -w /wordlists/Discovery/Web-Content/directory-list-2.3-small.txt -t 4 --delay 1s -o results.txt

===============================================================
Gobuster v3.1.0
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     https://example.co.uk/
[+] Method:                  GET
[+] Threads:                 4
[+] Delay:                   1s
[+] Wordlist:                /wordlists/Discovery/Web-Content/directory-list-2.3-small.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.1.0
[+] Timeout:                 10s
===============================================================
2022/03/08 12:12:19 Starting gobuster in directory enumeration mode
===============================================================
/admin
/aux
===============================================================
2022/03/08 12:46:57 Finished
===============================================================

Took a while, but by filtering the results to an output file its easy to see and retain for future enumerating, what was located. A few more interesting results this time.

![Gobusters Dir results output](https://hackertarget.com/images/gobuster-results.webp)

##### Other DIR flag examples

The results above show status codes. To exclude status codes use  `-n` 

user@matrix:$ gobuster dir -u https://example.com -w /wordlists/Discovery/Web-Content/big.txt  -n  -t 4 --delay 1s -o results.txt

An example of another flag to use is the  `-x  File extension(s) to search for`. This is for the times when a search for specific file extension or extensions is specified. Such as, `-x .php` or other only is required.

user@matrix:$ gobuster dir -u https://example.com -w /wordlists/Discovery/Web-Content/big.txt  -x .php, .txt  -t 4 --delay 1s -o results.txt

#### Continue enumerating

Continue to enumerate results to find as much information as possible. Run gobuster again with the results found and see what else appears. Keep digging to locate those hidden directories.

![Gobusters Dir results output](https://hackertarget.com/images/gobuster-results2.webp)

$ gobuster dir -u https://example.com/aux -w /wordlists/Discovery/Web-Content/big.txt -t 4 --delay 1s -o results.txt

## Gobuster DNS command

Use the `DNS` command to **discover subdomains** with Gobuster. To see the options and flags available specifically for the DNS command use: `gobuster dns --help`

user@matrix:$ gobuster dns --help
**Uses DNS subdomain enumeration mode**

Usage:
  gobuster dns [flags]

Flags:
  -d, --domain string      The target domain
  -h, --help               help for dns
  -r, --resolver string    Use custom DNS server (format server.com or server.com:port)
  -c, --show-cname         Show CNAME records (cannot be used with '-i' option)
  -i, --show-ips           Show IP addresses
      --timeout duration   DNS resolver timeout (default 1s)
      --wildcard           Force continued operation when wildcard found

Global Flags:
      --delay duration    Time each thread waits between requests (e.g. 1500ms)
      --no-error          Don't display errors
  -z, --no-progress       Don't display progress
  -o, --output string     Output file to write results to (defaults to stdout)
  -p, --pattern string    File containing replacement patterns
  -q, --quiet             Don't print the banner and other noise
  -t, --threads int       Number of concurrent threads (default 10)
  -v, --verbose           Verbose output (errors)
  -w, --wordlist string   Path to the wordlist

### DNS example

$ gobuster dns -q -r 8.8.8.8 -d example.com -w wordlists/Discovery/DNS/subdomains-top1million-5000.txt -t 4 --delay 1s -o results.txt"	 

Breaking this down.

`dns` mode  
`-q` --quiet : Don't print the banner and other noise  
`-r` --resolver string : Use custom DNS server (format server.com or server.com:port)  
`-d` --domain string  
`-w` --wordlist string : Path to the wordlist  
`-t` --threads  
`--delay` -- delay duration  
`-o` --output string : Output file to write results to (defaults to stdout)

Using another of the Seclists wordlists `/wordlists/Discovery/DNS/subdomains-top1million-5000.txt`.

### Results

In this case, as the flag `-q` for quiet mode was used, only the results are shown, the Gobuster banner and other information are removed.

Found: www.example.com
Found: nagios.example.com
Found: dev.example.com   
Found: auto.example.com                                

The same search without the flag `-q` obviously gives the same results - and includes the banner information.

===============================================================
Gobuster v3.1.0
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Domain:     example.com
[+] Threads:    4
[+] Delay:      1s
[+] Resolver:   8.8.8.8
[+] Timeout:    1s
[+] Wordlist:   /home/wordlists/subdomains-top1million-5000.txt
===============================================================
2022/03/18 16:20:35 Starting gobuster in DNS enumeration mode
===============================================================

Found: www.example.com
Found: nagios.example.com
Found: dev.example.com   
Found: auto.example.com  

===============================================================
2022/03/18 16:20:37 Finished
===============================================================

## Gobuster VHost command

The vhost command discovers Virtual host names on target web servers. Virtual hosting is a technique for hosting multiple domain names on a single server.

Exposing hostnames on a server may reveal supplementary web content belonging to the target. Vhost checks if the subdomains exist by visiting the formed URL and cross-checking the IP address.

To brute-force virtual hosts, use the same wordlists as for DNS brute-forcing subdomains.

Similar to brute forcing subdomains eg. url = example.com, vhost looks for dev.example.com or beta.example.com etc.

For options and flags available use `gobuster vhost --help`

user@matrix:$ gobuster vhost --help

**Uses VHOST enumeration mode**

Usage:
  gobuster vhost [flags]

Flags:
  -c, --cookies string        Cookies to use for the requests
  -r, --follow-redirect       Follow redirects
  -H, --headers stringArray   Specify HTTP headers, -H 'Header1: val1' -H 'Header2: val2'
  -h, --help                  help for vhost
  -m, --method string         Use the following HTTP method (default "GET")
  -k, --no-tls-validation     Skip TLS certificate verification
  -P, --password string       Password for Basic Auth
      --proxy string          Proxy to use for requests [http(s)://host:port]
      --random-agent          Use a random User-Agent string
      --timeout duration      HTTP Timeout (default 10s)
  -u, --url string            The target URL
  -a, --useragent string      Set the User-Agent string (default "gobuster/3.1.0")
  -U, --username string       Username for Basic Auth

Global Flags:
      --delay duration    Time each thread waits between requests (e.g. 1500ms)
      --no-error          Don't display errors
  -z, --no-progress       Don't display progress
  -o, --output string     Output file to write results to (defaults to stdout)
  -p, --pattern string    File containing replacement patterns
  -q, --quiet             Don't print the banner and other noise
  -t, --threads int       Number of concurrent threads (default 10)
  -v, --verbose           Verbose output (errors)
  -w, --wordlist string   Path to the wordlist

As shown above the Global flags are the same as for the all modes. Again, the 2 essential flags are the `-u` URL and `-w` wordlist. Not essential but useful `-o` output file and `-t` threads, `-q` for quiet mode to show the results only.

### Vhost example

user@matrix:$ gobuster vhost -u https://example.com -t 50 -w /wordlists/Discovery/DNS/subdomains-top1million-5000.txt 

### Results

===============================================================
Gobuster v3.1.0
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:          https://example.com
[+] Method:       GET
[+] Threads:      4
[+] Wordlist:     /wordlists/subdomains-top1million-5000.txt
[+] User Agent:   gobuster/3.1.0
[+] Timeout:      10s
===============================================================
2022/03/22 10:21:38 Starting gobuster in VHOST enumeration mode
===============================================================
Found: auto.example.com (Status: 200) [Size: 162]
Found: beta.example.com (Status: 200) [Size: 162]
Found: apache.example.com (Status: 200) [Size: 162]
                                                        
===============================================================
2022/03/22 10:21:39 Finished
===============================================================

 To see Gobuster being used check out [Ippsec](https://youtu.be/XROkuXKgeg8) walkthrough of **HTB Toby** released Apr 2022.

## Conclusion

Gobuster is a useful tool for recon and increasing the knowledge of the attack surface. Start with a smaller size wordlist and move to the larger ones as results will depend on the wordlist chosen. Keep enumerating. Don't stop at one search, it is surprising what is just sitting there waiting to be discovered.

**Credit:** This information was adapted from an excellent guide on [HackerTarget](https://hackertarget.com/gobuster-tutorial/). Be sure to check out the original post for more details.

# Gobuster – Penetration Testing Tools in Kali Tools

Last Updated : 18 Apr, 2023

One of the primary steps in attacking an internet application is enumerating hidden directories and files. Doing so can often yield valuable information that makes it easier to execute a particular attack, leaving less room for errors and wasted time. There are many tools available to try to do this, but not all of them are created equally. **Gobuster**, a record scanner written in Go Language, is worth searching for. In popular directories, brute-force scanners like DirBuster and DIRB work just elegantly but can often be slow and responsive to errors. Gobuster may be a Go implementation of those tools and is obtainable in a convenient command-line format. The primary benefit Gobuster has over other directory scanners is speed. As a programming language, Go is understood to be fast. It also has excellent help for concurrency, so that Gobuster can benefit from multiple threads for quicker processing. The one defeat of Gobuster, though, is the lack of recursive directory exploration. For directories, quite one level deep, another scan is going to be needed, unfortunately. Often, this is not that big of a deal, and other scanners can intensify and fill in the gaps for Gobuster in this area.

## Installation Steps of Gobuster Tool in Linux OS 

**Step 1:** 

Create a working directory to keep things neat, then change into it.

~# mkdir gobuster
~# cd gobuster/

**Step 2:** 

We need to install Gobuster Tool since it is not included on Kali Linux by default.

~/gobuster# apt-get install gobuster

**Step 3:** 

Then, simply type gobuster into the terminal to run the tool for use.

~/gobuster# gobuster -h

**Step 4:**

 Installing Additional Seclists for brute-forcing Directories and Files

~/gobuster# apt-get install seclists

By default, Wordlists on Kali are located in the /usr/share/wordlists directory.

## How to use Gobuster Tool for Scanning?

Gobuster tools can be launched from the terminal or command-line interface. You just have to run  the command using the syntax below.

gobuster [Mode][Options]

### Understanding Gobuster [Mode]

After entering the “gobuster” command in a terminal, you compulsory need to provide the mode or need to specify the purpose of the tool you are running for.

**Gobuster tool have many modes :**

- **dir –** the classic directory brute-forcing mode or Enumerating URIs for directories and files.  
    The Dir mode in Gobuster is mainly used to find extra content in a specific target domain or its subdomain. This additional information can include hidden directories or hidden files that can contain sensitive data. In Dir Mode, we can use the option “-u” to specify the target domain or subdomain you want to dig into the hidden directories and files. Also, the “-w” option will select the wordlist which you wish to use for brute-forcing.
    

![](https://media.geeksforgeeks.org/wp-content/uploads/20210713235757/dir11zon1.png)

dir mode options

- **dns – DNS subdomain brute-forcing mode or Enumerating Subdomains**  
    The DNS mode in Gobuster Tool is mainly used to enumerate subdomains in the target domain. You can use this mode to find some hidden or unidentifiable subdomains for a given target domain. In this mode, you can use the option “-d” to specify the target domain you want to find subdomain and the “-w” option allows you to select the wordlist you wish to use for brute-forcing.  
     

![](https://media.geeksforgeeks.org/wp-content/uploads/20210714000005/dns.png)

dns mode options

- **vhost – virtual host brute-forcing mode or enumerating virtual hosts (not the same as DNS!)**  
    Finally, Vhost mode in Gobuster is used to find the virtual hosts on the victim server. Virtual Hosting is done when companies host several domain names on a single server or cluster of the server. Virtual Hosting allows one server to share its data and resources with several other hostnames. Identifying hostnames on a server can disclose additional web content belonging to a company. In host mode, it checks if the subdomains exist by actually visiting the formed URL and cross checking the IP address.  
     

![](https://media.geeksforgeeks.org/wp-content/uploads/20210714000000/vhost.png)

vhost mode options

Mostly, you will be using the Gobuster tool for digging directories and files. In this case, dir mode will be helpful for you.

gobuster dir [options]

### Understanding Gobuster [Options]

After entering the specific mode as per requirement, you have to specify the options. Gobuster tool has a long list of options; to explore them, you can simply read the help page by typing “gobuster -h”. You could use “gobuster dns -h” to explore options that are specifically related to the dns mode).

Some examples of options are :

1. -o, –output string     Output file to write results to (defaults to stdout)
2. -q, –quiet                 Don’t print the banner and other noise
3. -t, –threads int         Number of concurrent threads (default 10)
4. -v, –verbose             Verbose output (errors)

![](https://media.geeksforgeeks.org/wp-content/uploads/20210712215159/helpgobuster.png)

gobuster -h option result

### Target Specification

So, while using the tool, we need to specify the “-u” followed by a target URL, IP address, or a hostname. This option is compulsory, as there is a target specified for getting results.

Some of the examples show how to use this option.

1. gobuster dir -u https://www.geeksforgeeks.org/
2. gobuster dir -u https://www.webscantest.com
3. gobuster dir -u 192.168.21.154

**Note that these examples will not work if the mandatory option “-u” is not specified.**

### Wordlist Specification

Gobuster Tool enumerates hidden directories and files in the target domain by performing a brute-force attack. A brute-force attack consists of matching a list of words or a combination of words hoping that the correct term is present in the list. So, Gobuster performs a brute attack. To force an attack, we need to specify a collection of words, i.e., wordlist. So to provide this wordlist, you need to type the “-w” option, followed by the path of the wordlist where it is located. We can use a wordlist file that is already present in the system.

> gobuster dir -u https://www.geeksforgeeks.org/ -w /usr/share/wordlists/big.txt

### Enumerating Files

Gobuster Tool can enumerate hidden files along with the remote directories. Gobuster allows us to use the “-x” option followed by the file extensions you’d like to search for.

Consider the example below:

> gobuster dir -u https://www.geeksforgeeks.com w /usr/share/wordlists/big.txt -x php,html,htm

In this command, we are specifically searching for files that have php,htm or html extensions.

## Usage of Gobuster Tool with an Example

### 1. Obtaining Full Path for a directory or file

Option “-e” is used for completing printing URL when extracting any hidden file or hidden directories.

> gobuster dir -e -u geeksforgeeks.org -w /usr/share/wordlists/dirb/common.txt –wildcard

![](https://media.geeksforgeeks.org/wp-content/uploads/20210714011707/ObtainingFullPathforadirectoryorfile.jpg)

Obtaining Full Path for a directory or file

### **2. Hide Status Code**

Using -n Option “no status” mode prints the results’ output without presenting the status code.

> gobuster dir -u geeksforgeeks.org -w /usr/share/wordlists/dirb/common.txt -n –wildcard

![](https://media.geeksforgeeks.org/wp-content/uploads/20210714011705/HideStatusCode.jpg)

Hide Status Code

### 3. Disable Banner

Gobuster tool constantly adds the banner to define the brief introduction of applied options while launching a brute force attack. By using the -q option, we can disable the flag to hide extra data.

> gobuster dir  -u geeksforgeeks.org -w /usr/share/wordlists/dirb/common.txt -q –wildcard

![](https://media.geeksforgeeks.org/wp-content/uploads/20210714011704/DisbaleBanner.jpg)

Disable Banner

### 4. Set Threads Number

Using the -t option enables the number of thread parameters to be implemented while brute-forcing sub-domain names or directories.

> gobuster  dns -d geeksforgeeks.org -t 100 -w /usr/share/wordlists/dirb/common.txt –wildcard

![](https://media.geeksforgeeks.org/wp-content/uploads/20210714011710/Threads.jpg)

Set Thread Number

### 5. Obtain Sub Domain IPs

Using the -i option allows the IP parameter, which should show the IPs of selected sub-domains.

> gobuster  dns -d geeksforgeeks.org -t 100 -w /usr/share/wordlists/dirb/common.txt -i –wildcard
> 
> DNS mode is covered in this command

![](https://media.geeksforgeeks.org/wp-content/uploads/20210714011708/Subdomains.jpg)

Obtain Sub Domain IPs

### 6. Timeout

Using the –timeout option allows the timeout parameter for HTTP requests, and 5 seconds is the default time limit for the HTTP request. 

> gobuster dir –timeout 5s -u geeksforgeeks.org -t 100 -w /usr/share/wordlists/dirb/common.txt –wildcard

![](https://media.geeksforgeeks.org/wp-content/uploads/20210714191328/timeoutmin.jpg)

Timeout

### 7. Appending Forward Slash

I am using the -f option here for appending the forward-slash while making a brute-force attack on the target URL.

> gobuster dir -u geeksforgeeks.org -w /usr/share/wordlists/dirb/common.txt -f –wildcard

![](https://media.geeksforgeeks.org/wp-content/uploads/20210714191316/APPENDINGFORWARDSLASHmin.jpg)

Appending Forward Slash

### 8. Enumerating Directory with Specific Extension List

There are many scenarios where we need to extract the directories of a specific extension over the victim server, and then we can use the -X parameter of this scan. This parameter allows the file extension name and then explores the given extension files over the victim server or computer.

> gobuster dir -u geeksforgeeks.org -w /usr/share/wordlists/dirb/common.txt -x .php –wildcard

![](https://media.geeksforgeeks.org/wp-content/uploads/20210714191318/enumeratingdirectorywithsepecificextensionmin.jpg)

Enumerating Directory with Specific Extension List

### 9. Follow Redirect

Using -r options allows redirecting the parameters, redirecting HTTP requests to another, and changing the Status code for a directory or file.

> gobuster dir -u geeksforgeeks.org -w /usr/share/wordlists/dirb/common.txt -q –wildcard
> 
> gobuster dir -u geeksforgeeks.org -r -w /usr/share/wordlists/dirb/common.txt -q –wildcard

![](https://media.geeksforgeeks.org/wp-content/uploads/20210714191321/FollowRedirectmin.jpg)

Follow Redirect

### 10. HTTP AUTHORIZATION (-u username: password)

HTTP Authentication/Authentication mechanisms are all based on the use of 401-status code and WWW-Authenticate response header. The most generally used HTTP authentication mechanisms are Primary. The client sends the user name and password un-encrypted base64 encoded data.

So, to avoid this kind of authentication with the help of Gobuster, we have used the command below:

> gobuster dir -u http://testphp.vulnweb.com/login.php -w /usr/share/wordlists/dirb/common.txt -U test -P test –wildcard

![](https://media.geeksforgeeks.org/wp-content/uploads/20210714191326/HTTPauthorizationmin.jpg)

HTTP Authorization

### 11. Force Processing Brute Force

It ends by obtaining the sub-domain name if it meets any Wildcard DNS, which is a non-existing domain. Therefore, it uses the –wildcard option to allow parameters to continue the attack even if there is any Wildcard Domain.

> gobuster dir -u geeksforgeeks.org -w /usr/share/wordlists/dirb/common.txt  –wildcard

![](https://media.geeksforgeeks.org/wp-content/uploads/20210714191322/Forceprocessoingmin.jpg)

Force Processing Brute Force

### 12. Hide Process of Extracting

Using the -z option covers the process of obtaining sub-domains names while making brute force attacks.

> gobuster dns -d geeksforgeeks.org -t 100 -w /usr/share/wordlists/dirb/common.txt -z –wildcard

![](https://media.geeksforgeeks.org/wp-content/uploads/20210714191324/hideprocessofextarctionmin.jpg)

Hide Process of Extraction

### 13. Extracting CNAME Records

Using the –cn option enables the CNAME Records parameter of the obtained sub-domains and their CNAME records.

> gobuster dns -d geeksforgeeks.org -t 100 -w /usr/share/wordlists/dirb/common.txt -c –wildcard

![](https://media.geeksforgeeks.org/wp-content/uploads/20210714191319/ExtractingCNAMERecordsmin.jpg)

Extracting CNAME Records

### 14. Proxy URL

Using the –p option allows proxy URL to be used for all requests; by default, it works on port 1080. As you can see, on examining the victim’s network IP in the web browser, it put up an “Access forbidden error”, which means this web page is operating backwards by some proxy.

> gobuster dir -p ‘https://18.172.30:3128’ -u ‘http://18.192.172.30/’ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt –wildcard

![](https://media.geeksforgeeks.org/wp-content/uploads/20210714191327/ProxyURLmin.jpg)

Proxy URL

### Example :

Now that everything is set up and installed, we’re ready to go and use Gobuster. Let’s run it against our victim with the default parameters.

Target for Scanning : https://testphp.vulnweb.com

![](https://media.geeksforgeeks.org/wp-content/uploads/20210712215203/scangobuster.png)

Scanning for Directories and Files

> kali@kali:~$ gobuster dir -u testphp.vulnweb.com -w /usr/share/wordlists/dirb/common.txt

From the above screenshot, we are enumerating for directories on https://testphp.vulnweb.com.

The wordlist used for the scanning is located at /usr/share/wordlists/dirb/common.txt

![](https://media.geeksforgeeks.org/wp-content/uploads/20210712215201/resultgobuster.png)

Going to the current directory which is identified while scanning

From the above screenshot, we have identified the admin panel while brute-forcing directories. After opening the web browser and typing the URL of our target, https://testphp.vulnweb.com/ and giving the identified directory /admin/, we will provide the contents available in that directory. Being a Security Researcher, you can test the functionality of that web page.

## Conclusion

In this article, we learned about Gobuster, a directory brute-force scanner written in the Go programming language. First, we learned how to install the tool and some valuable wordlists not found on Kali by default. Next, we ran it against our target and explored many of the varied options it ships with. Gobuster is a fast and powerful directory scanner that should be an essential part of any hacker’s collection, and now you know how to use it.

**Credit:** This information was adapted from an excellent guide on [GeeksForGeeks](https://www.geeksforgeeks.org/gobuster-penetration-testing-tools-in-kali-tools/). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/njoh22k3iO8?si=e0ztrJGcgm-UQCFB" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=njoh22k3iO8&t=53s). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/OZcZ5ia5r_k?si=-QgYWCJzgCSCp0jz" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=OZcZ5ia5r_k). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/mP_PR8r1sfg?si=nFZVxdARA8lj5hcA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=mP_PR8r1sfg). Be sure to check out the original post for more details.



