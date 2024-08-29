[![ffuf mascot](https://github.com/ffuf/ffuf/raw/master/_img/ffuf_run_logo_600.png)](https://github.com/ffuf/ffuf/blob/master/_img/ffuf_run_logo_600.png)

# ffuf - Fuzz Faster U Fool

[](https://github.com/ffuf/ffuf#ffuf---fuzz-faster-u-fool)

A fast web fuzzer written in Go.

- [Installation](https://github.com/ffuf/ffuf#installation)
- [Example usage](https://github.com/ffuf/ffuf#example-usage)
    - [Content discovery](https://github.com/ffuf/ffuf#typical-directory-discovery)
    - [Vhost discovery](https://github.com/ffuf/ffuf#virtual-host-discovery-without-dns-records)
    - [Parameter fuzzing](https://github.com/ffuf/ffuf#get-parameter-fuzzing)
    - [POST data fuzzing](https://github.com/ffuf/ffuf#post-data-fuzzing)
    - [Using external mutator](https://github.com/ffuf/ffuf#using-external-mutator-to-produce-test-cases)
    - [Configuration files](https://github.com/ffuf/ffuf#configuration-files)
- [Help](https://github.com/ffuf/ffuf#usage)
    - [Interactive mode](https://github.com/ffuf/ffuf#interactive-mode)

## Installation

[](https://github.com/ffuf/ffuf#installation)

- [Download](https://github.com/ffuf/ffuf/releases/latest) a prebuilt binary from [releases page](https://github.com/ffuf/ffuf/releases/latest), unpack and run!
    
    _or_
    
- If you are on macOS with [homebrew](https://brew.sh/), ffuf can be installed with: `brew install ffuf`
    
    _or_
    
- If you have recent go compiler installed: `go install github.com/ffuf/ffuf/v2@latest` (the same command works for updating)
    
    _or_
    
- `git clone https://github.com/ffuf/ffuf ; cd ffuf ; go get ; go build`
    

Ffuf depends on Go 1.16 or greater.

## Example usage

[](https://github.com/ffuf/ffuf#example-usage)

The usage examples below show just the simplest tasks you can accomplish using `ffuf`.

More elaborate documentation that goes through many features with a lot of examples is available in the ffuf wiki at [https://github.com/ffuf/ffuf/wiki](https://github.com/ffuf/ffuf/wiki)

For more extensive documentation, with real life usage examples and tips, be sure to check out the awesome guide: "[Everything you need to know about FFUF](https://codingo.io/tools/ffuf/bounty/2020/09/17/everything-you-need-to-know-about-ffuf.html)" by Michael Skelton ([@codingo](https://github.com/codingo)).

You can also practise your ffuf scans against a live host with different lessons and use cases either locally by using the docker container [https://github.com/adamtlangley/ffufme](https://github.com/adamtlangley/ffufme) or against the live hosted version at [http://ffuf.me](http://ffuf.me/) created by Adam Langley [@adamtlangley](https://twitter.com/adamtlangley).

### Typical directory discovery

[](https://github.com/ffuf/ffuf#typical-directory-discovery)

[![asciicast](https://camo.githubusercontent.com/7bdaa23ff951ec92fb5e45a5f66e98886007046391dc0f84d3951261ff93d378/68747470733a2f2f61736369696e656d612e6f72672f612f3231313335302e706e67)](https://asciinema.org/a/211350)

By using the FUZZ keyword at the end of URL (`-u`):

```
ffuf -w /path/to/wordlist -u https://target/FUZZ
```

### Virtual host discovery (without DNS records)

[](https://github.com/ffuf/ffuf#virtual-host-discovery-without-dns-records)

[![asciicast](https://camo.githubusercontent.com/9acb83862a6862151916c2f311123a5bdd69081489caa2644d72835069010075/68747470733a2f2f61736369696e656d612e6f72672f612f3231313336302e706e67)](https://asciinema.org/a/211360)

Assuming that the default virtualhost response size is 4242 bytes, we can filter out all the responses of that size (`-fs 4242`)while fuzzing the Host - header:

```
ffuf -w /path/to/vhost/wordlist -u https://target -H "Host: FUZZ" -fs 4242
```

### GET parameter fuzzing

[](https://github.com/ffuf/ffuf#get-parameter-fuzzing)

GET parameter name fuzzing is very similar to directory discovery, and works by defining the `FUZZ` keyword as a part of the URL. This also assumes a response size of 4242 bytes for invalid GET parameter name.

```
ffuf -w /path/to/paramnames.txt -u https://target/script.php?FUZZ=test_value -fs 4242
```

If the parameter name is known, the values can be fuzzed the same way. This example assumes a wrong parameter value returning HTTP response code 401.

```
ffuf -w /path/to/values.txt -u https://target/script.php?valid_name=FUZZ -fc 401
```

### POST data fuzzing

[](https://github.com/ffuf/ffuf#post-data-fuzzing)

This is a very straightforward operation, again by using the `FUZZ` keyword. This example is fuzzing only part of the POST request. We're again filtering out the 401 responses.

```
ffuf -w /path/to/postdata.txt -X POST -d "username=admin\&password=FUZZ" -u https://target/login.php -fc 401
```

### Maximum execution time

[](https://github.com/ffuf/ffuf#maximum-execution-time)

If you don't want ffuf to run indefinitely, you can use the `-maxtime`. This stops **the entire** process after a given time (in seconds).

```
ffuf -w /path/to/wordlist -u https://target/FUZZ -maxtime 60
```

When working with recursion, you can control the maxtime **per job** using `-maxtime-job`. This will stop the current job after a given time (in seconds) and continue with the next one. New jobs are created when the recursion functionality detects a subdirectory.

```
ffuf -w /path/to/wordlist -u https://target/FUZZ -maxtime-job 60 -recursion -recursion-depth 2
```

It is also possible to combine both flags limiting the per job maximum execution time as well as the overall execution time. If you do not use recursion then both flags behave equally.

### Using external mutator to produce test cases

[](https://github.com/ffuf/ffuf#using-external-mutator-to-produce-test-cases)

For this example, we'll fuzz JSON data that's sent over POST. [Radamsa](https://gitlab.com/akihe/radamsa) is used as the mutator.

When `--input-cmd` is used, ffuf will display matches as their position. This same position value will be available for the callee as an environment variable `$FFUF_NUM`. We'll use this position value as the seed for the mutator. Files example1.txt and example2.txt contain valid JSON payloads. We are matching all the responses, but filtering out response code `400 - Bad request`:

```
ffuf --input-cmd 'radamsa --seed $FFUF_NUM example1.txt example2.txt' -H "Content-Type: application/json" -X POST -u https://ffuf.io.fi/FUZZ -mc all -fc 400
```

It of course isn't very efficient to call the mutator for each payload, so we can also pre-generate the payloads, still using [Radamsa](https://gitlab.com/akihe/radamsa) as an example:

```
# Generate 1000 example payloads
radamsa -n 1000 -o %n.txt example1.txt example2.txt

# This results into files 1.txt ... 1000.txt
# Now we can just read the payload data in a loop from file for ffuf

ffuf --input-cmd 'cat $FFUF_NUM.txt' -H "Content-Type: application/json" -X POST -u https://ffuf.io.fi/ -mc all -fc 400
```

### Configuration files

[](https://github.com/ffuf/ffuf#configuration-files)

When running ffuf, it first checks if a default configuration file exists. Default path for a `ffufrc` file is `$XDG_CONFIG_HOME/ffuf/ffufrc`. You can configure one or multiple options in this file, and they will be applied on every subsequent ffuf job. An example of ffufrc file can be found [here](https://github.com/ffuf/ffuf/blob/master/ffufrc.example).

A more detailed description about configuration file locations can be found in the wiki: [https://github.com/ffuf/ffuf/wiki/Configuration](https://github.com/ffuf/ffuf/wiki/Configuration)

The configuration options provided on the command line override the ones loaded from the default `ffufrc` file. Note: this does not apply for CLI flags that can be provided more than once. One of such examples is `-H` (header) flag. In this case, the `-H` values provided on the command line will be _appended_ to the ones from the config file instead.

Additionally, in case you wish to use bunch of configuration files for different use cases, you can do this by defining the configuration file path using `-config` command line flag that takes the file path to the configuration file as its parameter.

[![](https://github.com/ffuf/ffuf/raw/master/_img/ffuf_juggling_250.png)](https://github.com/ffuf/ffuf/blob/master/_img/ffuf_juggling_250.png)

## Usage

[](https://github.com/ffuf/ffuf#usage)

To define the test case for ffuf, use the keyword `FUZZ` anywhere in the URL (`-u`), headers (`-H`), or POST data (`-d`).

```
Fuzz Faster U Fool - v2.1.0

HTTP OPTIONS:
  -H                  Header `"Name: Value"`, separated by colon. Multiple -H flags are accepted.
  -X                  HTTP method to use
  -b                  Cookie data `"NAME1=VALUE1; NAME2=VALUE2"` for copy as curl functionality.
  -cc                 Client cert for authentication. Client key needs to be defined as well for this to work
  -ck                 Client key for authentication. Client certificate needs to be defined as well for this to work
  -d                  POST data
  -http2              Use HTTP2 protocol (default: false)
  -ignore-body        Do not fetch the response content. (default: false)
  -r                  Follow redirects (default: false)
  -raw                Do not encode URI (default: false)
  -recursion          Scan recursively. Only FUZZ keyword is supported, and URL (-u) has to end in it. (default: false)
  -recursion-depth    Maximum recursion depth. (default: 0)
  -recursion-strategy Recursion strategy: "default" for a redirect based, and "greedy" to recurse on all matches (default: default)
  -replay-proxy       Replay matched requests using this proxy.
  -sni                Target TLS SNI, does not support FUZZ keyword
  -timeout            HTTP request timeout in seconds. (default: 10)
  -u                  Target URL
  -x                  Proxy URL (SOCKS5 or HTTP). For example: http://127.0.0.1:8080 or socks5://127.0.0.1:8080

GENERAL OPTIONS:
  -V                  Show version information. (default: false)
  -ac                 Automatically calibrate filtering options (default: false)
  -acc                Custom auto-calibration string. Can be used multiple times. Implies -ac
  -ach                Per host autocalibration (default: false)
  -ack                Autocalibration keyword (default: FUZZ)
  -acs                Custom auto-calibration strategies. Can be used multiple times. Implies -ac
  -c                  Colorize output. (default: false)
  -config             Load configuration from a file
  -json               JSON output, printing newline-delimited JSON records (default: false)
  -maxtime            Maximum running time in seconds for entire process. (default: 0)
  -maxtime-job        Maximum running time in seconds per job. (default: 0)
  -noninteractive     Disable the interactive console functionality (default: false)
  -p                  Seconds of `delay` between requests, or a range of random delay. For example "0.1" or "0.1-2.0"
  -rate               Rate of requests per second (default: 0)
  -s                  Do not print additional information (silent mode) (default: false)
  -sa                 Stop on all error cases. Implies -sf and -se. (default: false)
  -scraperfile        Custom scraper file path
  -scrapers           Active scraper groups (default: all)
  -se                 Stop on spurious errors (default: false)
  -search             Search for a FFUFHASH payload from ffuf history
  -sf                 Stop when > 95% of responses return 403 Forbidden (default: false)
  -t                  Number of concurrent threads. (default: 40)
  -v                  Verbose output, printing full URL and redirect location (if any) with the results. (default: false)

MATCHER OPTIONS:
  -mc                 Match HTTP status codes, or "all" for everything. (default: 200-299,301,302,307,401,403,405,500)
  -ml                 Match amount of lines in response
  -mmode              Matcher set operator. Either of: and, or (default: or)
  -mr                 Match regexp
  -ms                 Match HTTP response size
  -mt                 Match how many milliseconds to the first response byte, either greater or less than. EG: >100 or <100
  -mw                 Match amount of words in response

FILTER OPTIONS:
  -fc                 Filter HTTP status codes from response. Comma separated list of codes and ranges
  -fl                 Filter by amount of lines in response. Comma separated list of line counts and ranges
  -fmode              Filter set operator. Either of: and, or (default: or)
  -fr                 Filter regexp
  -fs                 Filter HTTP response size. Comma separated list of sizes and ranges
  -ft                 Filter by number of milliseconds to the first response byte, either greater or less than. EG: >100 or <100
  -fw                 Filter by amount of words in response. Comma separated list of word counts and ranges

INPUT OPTIONS:
  -D                  DirSearch wordlist compatibility mode. Used in conjunction with -e flag. (default: false)
  -e                  Comma separated list of extensions. Extends FUZZ keyword.
  -enc                Encoders for keywords, eg. 'FUZZ:urlencode b64encode'
  -ic                 Ignore wordlist comments (default: false)
  -input-cmd          Command producing the input. --input-num is required when using this input method. Overrides -w.
  -input-num          Number of inputs to test. Used in conjunction with --input-cmd. (default: 100)
  -input-shell        Shell to be used for running command
  -mode               Multi-wordlist operation mode. Available modes: clusterbomb, pitchfork, sniper (default: clusterbomb)
  -request            File containing the raw http request
  -request-proto      Protocol to use along with raw request (default: https)
  -w                  Wordlist file path and (optional) keyword separated by colon. eg. '/path/to/wordlist:KEYWORD'

OUTPUT OPTIONS:
  -debug-log          Write all of the internal logging to the specified file.
  -o                  Write output to file
  -od                 Directory path to store matched results to.
  -of                 Output file format. Available formats: json, ejson, html, md, csv, ecsv (or, 'all' for all formats) (default: json)
  -or                 Don't create the output file if we don't have results (default: false)

EXAMPLE USAGE:
  Fuzz file paths from wordlist.txt, match all responses but filter out those with content-size 42.
  Colored, verbose output.
    ffuf -w wordlist.txt -u https://example.org/FUZZ -mc all -fs 42 -c -v

  Fuzz Host-header, match HTTP 200 responses.
    ffuf -w hosts.txt -u https://example.org/ -H "Host: FUZZ" -mc 200

  Fuzz POST JSON data. Match all responses not containing text "error".
    ffuf -w entries.txt -u https://example.org/ -X POST -H "Content-Type: application/json" \
      -d '{"name": "FUZZ", "anotherkey": "anothervalue"}' -fr "error"

  Fuzz multiple locations. Match only responses reflecting the value of "VAL" keyword. Colored.
    ffuf -w params.txt:PARAM -w values.txt:VAL -u https://example.org/?PARAM=VAL -mr "VAL" -c

  More information and examples: https://github.com/ffuf/ffuf
```

### Interactive mode

[](https://github.com/ffuf/ffuf#interactive-mode)

By pressing `ENTER` during ffuf execution, the process is paused and user is dropped to a shell-like interactive mode:

```
entering interactive mode
type "help" for a list of commands, or ENTER to resume.
> help

available commands:
 afc  [value]             - append to status code filter 
 fc   [value]             - (re)configure status code filter 
 afl  [value]             - append to line count filter 
 fl   [value]             - (re)configure line count filter 
 afw  [value]             - append to word count filter 
 fw   [value]             - (re)configure word count filter 
 afs  [value]             - append to size filter 
 fs   [value]             - (re)configure size filter 
 aft  [value]             - append to time filter 
 ft   [value]             - (re)configure time filter 
 rate [value]             - adjust rate of requests per second (active: 0)
 queueshow                - show job queue
 queuedel [number]        - delete a job in the queue
 queueskip                - advance to the next queued job
 restart                  - restart and resume the current ffuf job
 resume                   - resume current ffuf job (or: ENTER) 
 show                     - show results for the current job
 savejson [filename]      - save current matches to a file
 help                     - you are looking at it
> 
```

in this mode, filters can be reconfigured, queue managed and the current state saved to disk.

When (re)configuring the filters, they get applied posthumously and all the false positive matches from memory that would have been filtered out by the newly added filters get deleted.

The new state of matches can be printed out with a command `show` that will print out all the matches as like they would have been found by `ffuf`.

As "negative" matches are not stored to memory, relaxing the filters cannot unfortunately bring back the lost matches. For this kind of scenario, the user is able to use the command `restart`, which resets the state and starts the current job from the beginning.

[![](https://github.com/ffuf/ffuf/raw/master/_img/ffuf_waving_250.png)](https://github.com/ffuf/ffuf/blob/master/_img/ffuf_waving_250.png)

## License

[](https://github.com/ffuf/ffuf#license)

ffuf is released under MIT license. See [LICENSE](https://github.com/ffuf/ffuf/blob/master/LICENSE).

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/ffuf/ffuf). Be sure to check out the original post for more details.

# Ffuf

[](https://gist.github.com/santosadrian/6c8f03f893154ec6575d84fe705c44fe#ffuf)

|**Command**|**Description**|
|---|---|
|`ffuf -h`|ffuf help|
|`ffuf -w wordlist.txt:FUZZ -u http://SERVER_IP:PORT/FUZZ`|Directory Fuzzing|
|`ffuf -w wordlist.txt:FUZZ -u http://SERVER_IP:PORT/indexFUZZ`|Extension Fuzzing|
|`ffuf -w wordlist.txt:FUZZ -u http://SERVER_IP:PORT/blog/FUZZ.php`|Page Fuzzing|
|`ffuf -w wordlist.txt:FUZZ -u http://SERVER_IP:PORT/FUZZ -recursion -recursion-depth 1 -e .php -v`|Recursive Fuzzing|
|`ffuf -w wordlist.txt:FUZZ -u https://FUZZ.hackthebox.eu/`|Sub-domain Fuzzing|
|`ffuf -w wordlist.txt:FUZZ -u http://academy.htb:PORT/ -H 'Host: FUZZ.academy.htb' -fs xxx`|VHost Fuzzing|
|`ffuf -w wordlist.txt:FUZZ -u http://admin.academy.htb:PORT/admin/admin.php?FUZZ=key -fs xxx`|Parameter Fuzzing - GET|
|`ffuf -w wordlist.txt:FUZZ -u http://admin.academy.htb:PORT/admin/admin.php -X POST -d 'FUZZ=key' -H 'Content-Type: application/x-www-form-urlencoded' -fs xxx`|Parameter Fuzzing - POST|
|`ffuf -w ids.txt:FUZZ -u http://admin.academy.htb:PORT/admin/admin.php -X POST -d 'id=FUZZ' -H 'Content-Type: application/x-www-form-urlencoded' -fs xxx`|Value Fuzzing|

# Wordlists

[](https://gist.github.com/santosadrian/6c8f03f893154ec6575d84fe705c44fe#wordlists)

|**Command**|**Description**|
|---|---|
|`/opt/useful/SecLists/Discovery/Web-Content/directory-list-2.3-small.txt`|Directory/Page Wordlist|
|`/opt/useful/SecLists/Discovery/Web-Content/web-extensions.txt`|Extensions Wordlist|
|`/opt/useful/SecLists/Discovery/DNS/subdomains-top1million-5000.txt`|Domain Wordlist|
|`/opt/useful/SecLists/Discovery/Web-Content/burp-parameter-names.txt`|Parameters Wordlist|

# Misc

[](https://gist.github.com/santosadrian/6c8f03f893154ec6575d84fe705c44fe#misc)

|**Command**|**Description**|
|---|---|
|`sudo sh -c 'echo "SERVER_IP academy.htb" >> /etc/hosts'`|Add DNS entry|
|`for i in $(seq 1 1000); do echo $i >> ids.txt; done`|Create Sequence Wordlist|
|`curl http://admin.academy.htb:PORT/admin/admin.php -X POST -d 'id=key' -H 'Content-Type: application/x-www-form-urlencoded'`|curl w/ POST|
**Credit:** This information was adapted from an excellent guide on [GitHub-Gist](https://gist.github.com/santosadrian/6c8f03f893154ec6575d84fe705c44fe). Be sure to check out the original post for more details.

# Packages and Binaries:

### ffuf

ffuf is a fast web fuzzer written in Go that allows typical directory discovery, virtual host discovery (without DNS records) and GET and POST parameter fuzzing.

This program is useful for pentesters, ethical hackers and forensics experts. It also can be used for security tests.

**Installed size:** `7.82 MB`  
**How to install:** `sudo apt install ffuf`

Dependencies:

- libc6

##### ffuf

Fast web fuzzer written in Go

```console
root@kali:~# ffuf -h
Fuzz Faster U Fool - v2.1.0-dev

HTTP OPTIONS:
  -H                  Header `"Name: Value"`, separated by colon. Multiple -H flags are accepted.
  -X                  HTTP method to use
  -b                  Cookie data `"NAME1=VALUE1; NAME2=VALUE2"` for copy as curl functionality.
  -cc                 Client cert for authentication. Client key needs to be defined as well for this to work
  -ck                 Client key for authentication. Client certificate needs to be defined as well for this to work
  -d                  POST data
  -http2              Use HTTP2 protocol (default: false)
  -ignore-body        Do not fetch the response content. (default: false)
  -r                  Follow redirects (default: false)
  -raw                Do not encode URI (default: false)
  -recursion          Scan recursively. Only FUZZ keyword is supported, and URL (-u) has to end in it. (default: false)
  -recursion-depth    Maximum recursion depth. (default: 0)
  -recursion-strategy Recursion strategy: "default" for a redirect based, and "greedy" to recurse on all matches (default: default)
  -replay-proxy       Replay matched requests using this proxy.
  -sni                Target TLS SNI, does not support FUZZ keyword
  -timeout            HTTP request timeout in seconds. (default: 10)
  -u                  Target URL
  -x                  Proxy URL (SOCKS5 or HTTP). For example: http://127.0.0.1:8080 or socks5://127.0.0.1:8080

GENERAL OPTIONS:
  -V                  Show version information. (default: false)
  -ac                 Automatically calibrate filtering options (default: false)
  -acc                Custom auto-calibration string. Can be used multiple times. Implies -ac
  -ach                Per host autocalibration (default: false)
  -ack                Autocalibration keyword (default: FUZZ)
  -acs                Custom auto-calibration strategies. Can be used multiple times. Implies -ac
  -c                  Colorize output. (default: false)
  -config             Load configuration from a file
  -json               JSON output, printing newline-delimited JSON records (default: false)
  -maxtime            Maximum running time in seconds for entire process. (default: 0)
  -maxtime-job        Maximum running time in seconds per job. (default: 0)
  -noninteractive     Disable the interactive console functionality (default: false)
  -p                  Seconds of `delay` between requests, or a range of random delay. For example "0.1" or "0.1-2.0"
  -rate               Rate of requests per second (default: 0)
  -s                  Do not print additional information (silent mode) (default: false)
  -sa                 Stop on all error cases. Implies -sf and -se. (default: false)
  -scraperfile        Custom scraper file path
  -scrapers           Active scraper groups (default: all)
  -se                 Stop on spurious errors (default: false)
  -search             Search for a FFUFHASH payload from ffuf history
  -sf                 Stop when > 95% of responses return 403 Forbidden (default: false)
  -t                  Number of concurrent threads. (default: 40)
  -v                  Verbose output, printing full URL and redirect location (if any) with the results. (default: false)

MATCHER OPTIONS:
  -mc                 Match HTTP status codes, or "all" for everything. (default: 200-299,301,302,307,401,403,405,500)
  -ml                 Match amount of lines in response
  -mmode              Matcher set operator. Either of: and, or (default: or)
  -mr                 Match regexp
  -ms                 Match HTTP response size
  -mt                 Match how many milliseconds to the first response byte, either greater or less than. EG: >100 or <100
  -mw                 Match amount of words in response

FILTER OPTIONS:
  -fc                 Filter HTTP status codes from response. Comma separated list of codes and ranges
  -fl                 Filter by amount of lines in response. Comma separated list of line counts and ranges
  -fmode              Filter set operator. Either of: and, or (default: or)
  -fr                 Filter regexp
  -fs                 Filter HTTP response size. Comma separated list of sizes and ranges
  -ft                 Filter by number of milliseconds to the first response byte, either greater or less than. EG: >100 or <100
  -fw                 Filter by amount of words in response. Comma separated list of word counts and ranges

INPUT OPTIONS:
  -D                  DirSearch wordlist compatibility mode. Used in conjunction with -e flag. (default: false)
  -e                  Comma separated list of extensions. Extends FUZZ keyword.
  -enc                Encoders for keywords, eg. 'FUZZ:urlencode b64encode'
  -ic                 Ignore wordlist comments (default: false)
  -input-cmd          Command producing the input. --input-num is required when using this input method. Overrides -w.
  -input-num          Number of inputs to test. Used in conjunction with --input-cmd. (default: 100)
  -input-shell        Shell to be used for running command
  -mode               Multi-wordlist operation mode. Available modes: clusterbomb, pitchfork, sniper (default: clusterbomb)
  -request            File containing the raw http request
  -request-proto      Protocol to use along with raw request (default: https)
  -w                  Wordlist file path and (optional) keyword separated by colon. eg. '/path/to/wordlist:KEYWORD'

OUTPUT OPTIONS:
  -debug-log          Write all of the internal logging to the specified file.
  -o                  Write output to file
  -od                 Directory path to store matched results to.
  -of                 Output file format. Available formats: json, ejson, html, md, csv, ecsv (or, 'all' for all formats) (default: json)
  -or                 Don't create the output file if we don't have results (default: false)

EXAMPLE USAGE:
  Fuzz file paths from wordlist.txt, match all responses but filter out those with content-size 42.
  Colored, verbose output.
    ffuf -w wordlist.txt -u https://example.org/FUZZ -mc all -fs 42 -c -v

  Fuzz Host-header, match HTTP 200 responses.
    ffuf -w hosts.txt -u https://example.org/ -H "Host: FUZZ" -mc 200

  Fuzz POST JSON data. Match all responses not containing text "error".
    ffuf -w entries.txt -u https://example.org/ -X POST -H "Content-Type: application/json" \
      -d '{"name": "FUZZ", "anotherkey": "anothervalue"}' -fr "error"

  Fuzz multiple locations. Match only responses reflecting the value of "VAL" keyword. Colored.
    ffuf -w params.txt:PARAM -w values.txt:VAL -u https://example.org/?PARAM=VAL -mr "VAL" -c

  More information and examples: https://github.com/ffuf/ffuf

```

---

Updated on: 2024-Feb-16

**Credit:** This information was adapted from an excellent guide on [Kali.org](https://www.kali.org/tools/ffuf/). Be sure to check out the original post for more details.

# How to Fuzz Web Applications using FFuf – Web Security Tutorial

![How to Fuzz Web Applications using FFuf – Web Security Tutorial](https://www.freecodecamp.org/news/content/images/size/w2000/2022/11/ffuf.png)

Building strong authentication systems is crucial for web applications. Now that many businesses have a growing online presence, a malicious actor taking control of your website can be devastating.

In this article, we will learn how to use Ffuf, a fast web fuzzer written in Go. You will learn how to fuzz your way to find directories and files and bypass the authentication of a website using ffuf. Then you'll learn how to defend against these types of attacks.

Remember – to protect yourself and your websites, it helps to know how an attacker would try to get in. That way, you can more effectively keep them out.

**Note:** Before we dive into using ffuf, I would like to emphasize that this tutorial is only meant to help you defend yourself against fuzzing attacks. If you use this material for malicious purposes, I am not responsible.

## What is FFuf?

Ffuf is a fuzzer written in the [Go programming language](https://go.dev/).

Ffuf belongs to the exploitation phase in the [pentesting lifecycle](https://exploitable.manishmshiva.com/ethical-hacking-lifecycle-five-stages-of-a-penetration-test-c201e8e5bbf7). It is also the fastest open-source fuzzing tool available in the market.

But before we start using Ffuf, let's understand what fuzzing is.

## What is Fuzzing?

Fuzzing is a method of sending malformed or abnormal data to a system in order to get it to misbehave in some way, which could lead to the discovery of vulnerabilities.

Finding hidden files, sending random data to forms, or even login attempts to web applications can be considered fuzzing.

Then you might be wondering “How is it different from Brute forcing?”.

Brute forcing can be considered a part of fuzzing. In brute force, the attacker uses valid data, for example, to check if a login attempt works. But with Fuzzing, they can send random data to break the expected behavior of a system.

For example, if you use a tool like Ffuf and load it with hundreds of username-password combinations to try on a website, it is fuzzing. And that’s exactly what we will do using Ffuf.

Make sure you have written permission if you are going to try this tool on a third-party website.

## How to Install Ffuf and Wordlists

Ffuf comes pre-packaged with the Kali Linux distribution. If you want to install Ffuf on your personal computer, [here are the instructions](http://ffuf.me/install).

Since Ffuf is written in the Go programming language, make sure you have the Go compiler installed in your system before trying to install Ffuf.

If you are new to wordlists, a wordlist is a list of commonly used terms. This can be a [password wordlist](https://github.com/danielmiessler/SecLists/blob/master/Passwords/Common-Credentials/10-million-password-list-top-100.txt), [username wordlist](https://github.com/danielmiessler/SecLists/blob/master/Usernames/Names/names.txt), subdomain wordlist, and so on. You can find a lot of [useful wordlists here](https://github.com/danielmiessler/SecLists).

I would recommend downloading [Seclists](https://github.com/danielmiessler/SecLists). Seclists is a collection of multiple types of lists used during security assessments. This includes usernames, passwords, URLs, etc. If you are using Kali Linux, you can find seclists under /usr/share/wordlists.

To try this tool in real-time, you can either use your own website or use a practice web app like the [Damn Vulnerable Web app](https://github.com/digininja/DVWA) (DVWA). DVWA is an intentionally misconfigured vulnerable web application that is used by pen testers for practicing web application attacks.

## Fuzzing with Ffuf

Now that you understand what Fuzzing and Wordlists are, let's start using Ffuf.

We will use ffuf to fuzz the web application to discover directories, find usernames, enumerate virtual hosts, and even brute-force email/password combinations.

You can use the help command (-h) if you want to quickly look at the options provided by Ffuf. This is useful since you don't have to memorize all the options provided by Ffuf.

```
ffuf -h
```

![Image](https://www.freecodecamp.org/news/content/images/2022/11/image-26.png)

Do remember that the URL (-u) and wordlist (-w) parameters are always required.

Note that I'll be using [http://localhost:3000](http://localhost:3000/) for my examples. If you setup your own web app or use an existing website, you have to replace “localhost:3000” with the ip address or the domain name of the website.

### How to Enumerate URLs with Ffuf

Let's see how to find some URL paths.

Finding URLs is useful, especially if they are being hidden from being publicly indexed. We will use the [web content wordlist](https://github.com/danielmiessler/SecLists/blob/master/Discovery/Web-Content/big.txt) from seclists to fuzz the web app for hidden URLs.

You can use the following command to look for URLs:

```
ffuf -u http://localhost:3000/FUZZ -w /usr/share/wordlists/SecLists/Discovery/Web-Content/big.txt
```

Here, the “FUZZ” keyword is used as a placeholder. Ffuf will try to hit the URL by replacing the word “FUZZ” with every word in the wordlist.

Here is what I found from the DVWA:

![Image](https://www.freecodecamp.org/news/content/images/2022/11/image-27.png)_Result of looking for URLs_

Interesting. You can see that we have found a few (possibly important) locations like /config, /docs, and /server-status.

If a real-world web app had pages that were not linked anywhere but used standard names, Ffuf would easily spot them.

### How to Enumerate Files with Ffuf

What if you want to look for specific files? Thankfully, Ffuf provides us with the extension option (-e) that we can use. We can tell Ffuf to look only for files that have certain extensions – in our case, .html,.php, and .txt.

We will be using the [raft-medium-words](https://github.com/danielmiessler/SecLists/blob/master/Discovery/Web-Content/raft-medium-words-lowercase.txt) wordlist for this. Here is the command to look for specific files:

```
ffuf -u http://localhost:3000/FUZZ -w /usr/share/wordlists/SecLists/Discovery/Web-Content/raft-medium-words-lowercase.txt -e .php,.html,.txt
```

This command looks for all the files at the root of the domain with an extension of .html, .php, and .txt. Here is the result from DVWA:

![Image](https://www.freecodecamp.org/news/content/images/2022/11/image-28.png)_Result of looking for specific files_

We have found a long list of files. Even if some files are not served on the web app (403 status), we can learn that there are files, just that we cannot access them yet.

Let’s run the same command, but now, we will only look for files that are accessible to the public. We will use the match code (-mc) flag to only look for files with a status of 200.

Here is the command:

```
ffuf -u http://localhost:3000/FUZZ -w /usr/share/wordlists/SecLists/Discovery/Web-Content/raft-medium-words-lowercase.txt -e .php,.html,.txt -mc 200
```

And here is the result.

![Image](https://www.freecodecamp.org/news/content/images/2022/11/image-31.png)_Files accessible to the public_

You can see that we have found a few files that we can access. The login.php looks interesting, and we will use it for bypassing authentication in the following sections.

### How to Enumerate Sub Domains using Ffuf

You can also look for sub-domains in a web app using Ffuf.

You might have guessed the approach that we are going to use. We will replace the subdomain of the URL with the word “FUZZ” and try looking for URLs that are up.

Since my web app is hosted on my local system, it does not contain any subdomains. But in the real world, if you want to enumerate subdomains, here is the command. You can use the [sub domains wordlist](https://github.com/danielmiessler/SecLists/blob/master/Discovery/DNS/subdomains-top1million-5000.txt) from seclists.

```
ffuf -u http://FUZZ.mydomain.com -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt
```

### How to Find Usernames with Ffuf

Have you been annoyed when web applications don’t tell you whether you have the wrong username or password? They just tell you “This combination doesn’t work”.

This is to protect the web app from username/email fuzzing attacks. If authentication systems give you specific information about your login attempt, it gets easier for attackers to brute force and discover a list of usernames or emails.

Let’s assume that our web application tells you that you have the wrong username with the message “username does not exist”. We can use this error message to find valid usernames with the following command:

```
ffuf -w /usr/share/SecLists/Usernames/top-usernames-shortlist.txt -X POST -d "username=FUZZ&&password=x" -H "Content-Type: application/x-www-form-urlencoded" -u http://mydomain.com/login -mr "username already exists"
```

Here, we are sending POST requests to the login page, with the fuzzed usernames and a dummy password to check if the expected error message is returned. You can use a [username wordlist](https://github.com/danielmiessler/SecLists/blob/master/Usernames/top-usernames-shortlist.txt) from seclists for fuzzing.

The -mr flag is used to match a regular expression. You can have complicated regular expressions or a simple string message to validate the requests.

Here is a sample response.

![Image](https://www.freecodecamp.org/news/content/images/2022/11/image-32.png)

### Brute Forcing using Ffuf

Now, let's do some brute forcing with Ffuf. We will try a bunch of common username/password combinations and see if anything works.

If the web application you are testing uses a combination of email and password, you can replace the username wordlist with a email wordlist.

So for this attack, we need two parameters: username and password. Also, we will be using two-word lists: as you guessed, a username wordlist and a password wordlist.

In addition the default placeholder **FUZZ,** Ffuf supports the use of variables. So we will use W1 for our username wordlist and W2 for the password wordlist.

Here is the command:

```
ffuf -w usernames.txt:W1,/usr/share/wordlists/SecLists/Passwords/Common-Credentials/10-million-password-list-top-100.txt:W2 -X POST -d "username=W1&password=W2" -H "Content-Type: application/x-www-form-urlencoded" -u http://localhost:3000/login -fc 200
```

If Ffuf finds any valid combinations, you will see the combination in the results. You can also filter by status codes (for examle filter 400 or look for 200) using the -fc or -mc flags to reduce the noise.

Here is a sample response.

![Image](https://www.freecodecamp.org/news/content/images/2022/11/image-33.png)

That was fun, wasn’t it? We can find a lot of interesting information about a web app without using a complicated tool like [Burpsuite](https://www.kali.org/tools/burpsuite/).

## How to Protect Your Site from Fuzzing

But since we are not the malicious attackers, let’s look at how to defend against fuzzing.

The easiest way to protect your website from fuzzing attacks is to be careful about the type of files on the web server. If you don't want something to be found, don't put it on the web server.

To prevent authentication bypass, it is important not to allow multiple attempts to log in. Most modern websites don't allow more than 5 consecutive login attempts. It is more secure to ask your users to reset their passwords via email instead of letting them try multiple combinations.

You should also be careful about the error messages returned on failed attempts. Displaying that “Email does not exist” or “Password not correct” will let the hacker know that an email or username exists. This just makes their job easier.

Finally, you can use [Web Application Firewalls](https://www.cloudflare.com/en-gb/learning/ddos/glossary/web-application-firewall-waf/) (WAF) to monitor traffic and block suspicious IP addresses. WAFs also have options to set alerts if it comes across brute forcing attempts on your authentication methods.

## Summary

Ffuf is a great tool to have in your pentesting toolkit. It is a simple yet fast fuzzer that makes it easy to enumerate directories, discover virtual hosts, and brute-force web applications.

Ffuf also has more options that will help you to look for specific information. It has support for regular expressions, rate limiting of requests, and saving your results to a file.

Hope you enjoyed this article. You can [connect with me on Linkedin](https://www.linkedin.com/in/manishmshiva/) or [read more articles on my blog](https://blog.manishmshiva.com/). I’ll see you soon with another article.

**Credit:** This information was adapted from an excellent guide on [FreeCodeCamp](https://www.freecodecamp.org/news/web-security-fuzz-web-applications-using-ffuf/). Be sure to check out the original post for more details.

# Guide to Using ffuf

Explore how to fuzz files, directories, and parameters with using ffuf.

# Introduction

Ffuf (Fuzz Faster U Fool) is a versatile and powerful tool for fuzzing web applications, helping you discover hidden files, directories, subdomains, and more. This guide provides detailed examples for using ffuf in various scenarios.

![](https://miro.medium.com/v2/resize:fit:700/1*KdgJcCwvAVd7ZBz_iQOfkQ.jpeg)

# **TL;DR**

You can find a shorter cheat sheet version of this article [here](https://learntheshell.com/cheatsheets/ffuf/).

# **Fuzzing Files and Paths**

Fuzzing files and paths is a fundamental technique in web security testing, enabling the discovery of hidden files, directories, and endpoints that are not publicly listed. By using a wordlist, you can automate the process of probing a web server for these hidden resources, uncovering potentially interesting files.

## **Basic File/Path Fuzzing**

To fuzz files and paths, using a wordlist:

ffuf -w wordlist.txt -u https://host.name:PORT/FUZZ

This command will try each entry in _`wordlist.txt`_ as a replacement for _`FUZZ`_ in the URL, testing for potential files and directories. For example, if your wordlist contains _`admin`_, _`login`_, and _`test`_, ffuf will test URLs like _`https://host.name:PORT/admin`_, _`https://host.name:PORT/login`_, and _`https://host.name:PORT/test`_.

## **Fuzzing Extensions**

To find files with different extensions:

ffuf -w wordlist.txt -u https://host.name/indexFUZZ

This command appends each wordlist entry to _`index`_, allowing you to discover files with various extensions. For instance, if the wordlist includes _`.php`_, _`.html`_, and _`.js`_, ffuf will test _`https://host.name/index.php`_, _`https://host.name/index.html`_, and _`https://host.name/index.js_`.

## **Fuzzing File Name with Different Extension**

To find specific file names with given extension:

ffuf -w wordlist.txt -u https://host.name/blog/FUZZ.php

This will replace _`FUZZ`_ with each word in the wordlist and append _`.php`_, helping you locate specific PHP files like _`https://host.name/blog/admin.php`_ or _`https://host.name/blog/login.php_`.

You can create a wordlist of files without the extension and use it across targets using different technologies — _`.php`_, _`.asp`_, _`.js`_ etc.

## **Recursive Fuzzing**

To perform recursive fuzzing with a specified depth:

ffuf -recursion -recursion-depth 3 -w wordlist.txt -u https://host.name/FUZZ

This command recursively searches up to 3 levels deep, increasing the chances of discovering deeply nested files and directories. For example, it might find _`https://host.name/admin`_, then _`https://host.name/admin/config`_, and further into _`https://host.name/admin/config/settings`_. By default recursive fuzzing is disabled.

## **Setting Cookies**

To include cookies in your fuzzing requests:

ffuf -b "NAME1=VALUE1; NAME2=VALUE2" -w wordlist.txt -u https://host.name/FUZZ

This is useful for authenticated fuzzing where cookies are required for access. For example, if you need to authenticate with _`SESSIONID=12345_` and _`USER=admin`_, you can include these cookies in your fuzzing attempts.

# **Subdomains and VHosts**

Subdomain and virtual host (VHost) fuzzing is an essential practice for uncovering additional entry points into a target domain. By identifying subdomains and VHosts, you can discover additional services, applications, and potential vulnerabilities that may not be immediately visible.

## **Subdomain Fuzzing**

To discover subdomains:

ffuf -w wordlist.txt -u https://FUZZ.host.name/

This replaces _`FUZZ`_ with each wordlist entry, helping identify subdomains under _`host.name`_. If your wordlist contains _`api`_, _`mail_`, and _`dev_`, ffuf will test _`https://api.host.name/`_, _`https://mail.host.name/`_, and _`https://dev.host.name/`_.

## **Virtual Hosts (VHosts) Fuzzing**

To fuzz virtual hosts:

ffuf -w wordlist.txt -u http://host.name/ -H 'Host: FUZZ.host.name'

This command changes the _`Host`_ header, testing for virtual host-based sites. For example, testing _`api`, `staging`_, and _`beta`_ as virtual hosts could reveal _`http://api.host.name/`, `http://staging.host.name/`_, and _`http://beta.host.name/`_.

# **HTTP Parameters**

Fuzzing HTTP parameters is a crucial aspect of web application security testing. By probing different parameter names and values, you can discover new parameters and uncover hidden functionalities — entry points with potential vulnerabilities.

## **Fuzzing Parameter Names — GET**

To fuzz GET parameter names:

ffuf -w wordlist.txt -u http://host.name/index.php?FUZZ=key

This helps find parameter names that might accept a specific key. If your wordlist includes _`id`_, _`user`_, and _`token`_, ffuf will test _`http://host.name/index.php?id=key`, `http://host.name/index.php?user=key`_, and _`http://host.name/index.php?token=key`_.

## **Fuzzing Parameter Names — POST**

To fuzz POST parameter names:

ffuf -w wordlist.txt -u https://host.name/index.php -X POST -d 'FUZZ=key' -H 'Content-Type: application/x-www-form-urlencoded'

This sends POST requests to discover parameter names. For instance, it will test parameters like _`username`, `password`_, and _`email`_ in the POST data.

## **Fuzzing Parameter Values — POST**

To fuzz values of a specific POST parameter:

ffuf -w ids.txt -u https://host.name/index.php -X POST -d 'id=FUZZ' -H 'Content-Type: application/x-www-form-urlencoded'

This helps identify valid parameter values. For example, if `ids.txt` contains _`123`, `456`_, and _`789`_, ffuf will test values like _`id=123`, `id=456`_, and _`id=789`_.

# **Rate Limits**

Managing the rate of requests is essential when fuzzing web applications to avoid overloading the server or triggering WAF. Rate limiting helps control the number of requests sent per second or the number of threads used during fuzzing. In this section, we’ll look at how to use ffuf to set rate limits and configure the number of threads, ensuring your testing is efficient and respectful of the target server’s resources. By fine-tuning these parameters, you can perform thorough and responsible fuzzing without causing unnecessary disruption.

## **Limiting Request Rate**

To set a rate limit of 50 requests per second:

ffuf -rate 50 -w wordlist.txt -u https://host.name/FUZZ

This ensures that your fuzzing doesn’t overwhelm the target server, helping maintain stability and avoiding potential bans.

## **Setting Number of Threads**

To specify the number of threads:

ffuf -t 5 -w wordlist.txt -u https://host.name/FUZZ

This controls the concurrency of your fuzzing requests, balancing speed and server load.

# **Filters**

Filters are an essential feature in ffuf that allow you to narrow down your fuzzing results to those most relevant to your testing objectives. By applying filters, you can exclude unwanted responses based on various criteria such as HTTP status codes, response size, number of lines, and word count. This helps in identifying significant findings more quickly and efficiently.

## **Filtering by HTTP Codes**

To exclude _`301`_ and _`302`_ HTTP codes:

ffuf -fc 301,302 -w wordlist.txt -u https://host.name/FUZZ

This filters out results with these status codes, focusing on other responses that might be more interesting, such as _`200`_ OK or _`500`_ Internal Server Error.

## **Filtering by Response Size**

To filter responses of a specific size (e.g., 2003 bytes):

ffuf -fs 2003 -w wordlist.txt -u https://host.name/FUZZ

This helps in identifying content of specific sizes, which might indicate certain types of files or responses.

## **Filtering by Lines and Word Count**

To filter by the number of lines:

ffuf -fl 5 -w wordlist.txt -u https://host.name/FUZZ

To filter by word count:

ffuf -fw 10 -w wordlist.txt -u https://host.name/FUZZ

These filters refine your results based on response structure, allowing you to focus on responses that match specific patterns.

## **Automatic Calibration**

To automatically calibrate filtering options:

ffuf -ac -w wordlist.txt -u https://host.name/FUZZ

This helps ffuf determine appropriate filters based on initial responses, improving the accuracy of your fuzzing results.

# **Other Useful Options**

Apart from basic fuzzing capabilities, ffuf offers a range of advanced features to enhance your testing workflow. These options allow you to customize requests, handle proxies, set headers, and impose time constraints, optimizing your fuzzing process for diverse testing scenarios.

## **Ignoring Wordlist Comments**

To ignore comments in the wordlist:

ffuf -ic -w wordlist.txt -u https://host.name/FUZZ

This treats all lines as potential fuzzing targets, even those starting with `#`.

## **Using Proxies**

When direct access to the target is not feasible, or when inspection of ffuf requests is necessary, it can be utilized through a proxy server.

For HTTP proxy:

ffuf -x http://127.0.0.1:8080 -w wordlist.txt -u https://host.name/FUZZ

For SOCKS proxy:

ffuf -x socks5://127.0.0.1:1080 -w wordlist.txt -u https://host.name/FUZZ

For replay proxy:

ffuf -replay-proxy http://127.0.0.1:8080 -w wordlist.txt -u https://host.name/FUZZ

With this option ffuf will repeat each matched request using given proxy. This is useful to inspect ffuf findings in other tools such as Burp Suite.

## **Setting HTTP Headers**

Ffuf provides capability to manipulate headers, enabling users to tailor requests to specific requirements. This is useful to mimic different user agents, content types, or to tag your traffic with custom headers (which is often required by bug bounty programs). Below are some examples of configuring HTTP headers in ffuf.

To change the user agent:

ffuf -w wordlist.txt -u https://host.name/FUZZ -H "User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:88.0) Gecko/20100101 Firefox/88.0"

To set `Content-Type` header for POST requests:

ffuf -w wordlist.txt -u https://host.name/FUZZ -H "Content-Type: application/json" -X POST

To set custom header:

ffuf -w wordlist.txt -u https://host.name/FUZZ -H "X-Bug-Bounty: <bb-username>"

## **Time Limits**

Ffuf allows to set time limits both globally and per job, allowing users to control the duration of their fuzzing sessions precisely.

To set a maximum time limit for the fuzzing process:

ffuf -w wordlist.txt -u https://host.name/FUZZ -maxtime 60

To set a time limit per job:

ffuf -w wordlist.txt -u https://host.name/FUZZ -maxtime-job 60

These limits prevent long-running fuzzing jobs from taking too much time, helping you manage your testing schedule effectively.

# **Conclusion**

Ffuf is an essential tool for web security testing, offering a wide range of options to customize and optimize your fuzzing tasks. By leveraging these commands and options, you can effectively discover hidden vulnerabilities and improve the security posture of web applications.

**Credit:** This information was adapted from an excellent guide on [Medium](https://medium.com/@learntheshell/guide-to-using-ffuf-74824770076b). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/eTj9A8c9tCM?si=zcZytT1h_z23iNbn" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=eTj9A8c9tCM). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/9Hik0xy9qd0?si=czc8kUl8Kx0huFLw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=9Hik0xy9qd0). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/51HyUgdUX6I?si=RNnTt7uEbrWOAvSn" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=51HyUgdUX6I&t=94s). Be sure to check out the original post for more details.


