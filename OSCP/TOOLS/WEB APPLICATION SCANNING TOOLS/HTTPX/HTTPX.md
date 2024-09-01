# [![httpx](https://github.com/projectdiscovery/httpx/raw/main/static/httpx-logo.png)](https://github.com/projectdiscovery/httpx/blob/main/static/httpx-logo.png)  

[](https://github.com/projectdiscovery/httpx#----)

[![](https://camo.githubusercontent.com/89d810499c75c65e83a36262cbffdebda6a1e3cee4fd8e97bcd9a04d9d742262/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f6c6963656e73652d4d49542d5f7265642e737667)](https://opensource.org/licenses/MIT) [![](https://camo.githubusercontent.com/d595bc55a7cd61948e49426d049ba74f80243a216d6e3bb2f688c097e8278042/68747470733a2f2f676f7265706f7274636172642e636f6d2f62616467652f6769746875622e636f6d2f70726f6a656374646973636f766572792f6874747078)](https://goreportcard.com/badge/github.com/projectdiscovery/httpx) [![](https://camo.githubusercontent.com/bf3fcfa150ac3a664296bb3b9f62bd1738b7b8961bd0f76eadc0738f719f7dd8/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f72656c656173652f70726f6a656374646973636f766572792f6874747078)](https://github.com/projectdiscovery/httpx/releases) [![](https://camo.githubusercontent.com/13e9b51f24854147f60f95af96f6800d043363716a4b37392c594ef9431bf5e7/68747470733a2f2f696d672e736869656c64732e696f2f646f636b65722f70756c6c732f70726f6a656374646973636f766572792f68747470782e737667)](https://hub.docker.com/r/projectdiscovery/httpx) [![](https://camo.githubusercontent.com/a4a2a2d47c4cef73237f6f3770448bf2ea51b8571a772b1a9c8ec4c5ab73d50a/68747470733a2f2f696d672e736869656c64732e696f2f747769747465722f666f6c6c6f772f70646973636f76657279696f2e7376673f6c6f676f3d74776974746572)](https://twitter.com/pdiscoveryio) [![](https://camo.githubusercontent.com/af2c05f56a8d3837fdf1f7000afe043ecb1d984191261d1c1e2bd2a519698be1/68747470733a2f2f696d672e736869656c64732e696f2f646973636f72642f3639353634353233373431383133313530372e7376673f6c6f676f3d646973636f7264)](https://discord.gg/projectdiscovery)

[Features](https://github.com/projectdiscovery/httpx#features) • [Installation](https://github.com/projectdiscovery/httpx#installation-instructions) • [Usage](https://github.com/projectdiscovery/httpx#usage) • [Documentation](https://docs.projectdiscovery.io/tools/httpx/) • [Notes](https://github.com/projectdiscovery/httpx#notes) • [Join Discord](https://discord.gg/projectdiscovery)

`httpx` is a fast and multi-purpose HTTP toolkit that allows running multiple probes using the [retryablehttp](https://github.com/projectdiscovery/retryablehttp-go) library. It is designed to maintain result reliability with an increased number of threads.

# Features

[](https://github.com/projectdiscovery/httpx#features)

# [![httpx](https://user-images.githubusercontent.com/8293321/135731750-4c1d38b1-bd2a-40f9-88e9-3c4b9f6da378.png)](https://user-images.githubusercontent.com/8293321/135731750-4c1d38b1-bd2a-40f9-88e9-3c4b9f6da378.png)  

[](https://github.com/projectdiscovery/httpx#-----1)

- Simple and modular code base making it easy to contribute.
- Fast And fully configurable flags to probe multiple elements.
- Supports multiple HTTP based probings.
- Smart auto fallback from https to http as default.
- Supports hosts, URLs and CIDR as input.
- Handles edge cases doing retries, backoffs etc for handling WAFs.

### Supported probes

[](https://github.com/projectdiscovery/httpx#supported-probes)

|Probes|Default check|Probes|Default check|
|---|---|---|---|
|URL|true|IP|true|
|Title|true|CNAME|true|
|Status Code|true|Raw HTTP|false|
|Content Length|true|HTTP2|false|
|TLS Certificate|true|HTTP Pipeline|false|
|CSP Header|true|Virtual host|false|
|Line Count|true|Word Count|true|
|Location Header|true|CDN|false|
|Web Server|true|Paths|false|
|Web Socket|true|Ports|false|
|Response Time|true|Request Method|true|
|Favicon Hash|false|Probe Status|false|
|Body Hash|true|Header Hash|true|
|Redirect chain|false|URL Scheme|true|
|JARM Hash|false|ASN|false|

# Installation Instructions

[](https://github.com/projectdiscovery/httpx#installation-instructions)

`httpx` requires **go1.21** to install successfully. Run the following command to get the repo:

```shell
go install -v github.com/projectdiscovery/httpx/cmd/httpx@latest
```

To learn more about installing httpx, see [https://docs.projectdiscovery.io/tools/httpx/install](https://docs.projectdiscovery.io/tools/httpx/install).

|❗ **Disclaimer**|
|---|
|**This project is in active development**. Expect breaking changes with releases. Review the changelog before updating.|
|This project was primarily built to be used as a standalone CLI tool. **Running it as a service may pose security risks.** It's recommended to use with caution and additional security measures.|

# Usage

[](https://github.com/projectdiscovery/httpx#usage)

```shell
httpx -h
```

This will display help for the tool. Here are all the switches it supports.

```shell
Usage:
  ./httpx [flags]

Flags:
INPUT:
   -l, -list string      input file containing list of hosts to process
   -rr, -request string  file containing raw request
   -u, -target string[]  input target host(s) to probe

PROBES:
   -sc, -status-code      display response status-code
   -cl, -content-length   display response content-length
   -ct, -content-type     display response content-type
   -location              display response redirect location
   -favicon               display mmh3 hash for '/favicon.ico' file
   -hash string           display response body hash (supported: md5,mmh3,simhash,sha1,sha256,sha512)
   -jarm                  display jarm fingerprint hash
   -rt, -response-time    display response time
   -lc, -line-count       display response body line count
   -wc, -word-count       display response body word count
   -title                 display page title
   -bp, -body-preview     display first N characters of response body (default 100)
   -server, -web-server   display server name
   -td, -tech-detect      display technology in use based on wappalyzer dataset
   -method                display http request method
   -websocket             display server using websocket
   -ip                    display host ip
   -cname                 display host cname
   -extract-fqdn, -efqdn  get domain and subdomains from response body and header in jsonl/csv output
   -asn                   display host asn information
   -cdn                   display cdn/waf in use (default true)
   -probe                 display probe status

HEADLESS:
   -ss, -screenshot                 enable saving screenshot of the page using headless browser
   -system-chrome                   enable using local installed chrome for screenshot
   -ho, -headless-options string[]  start headless chrome with additional options
   -esb, -exclude-screenshot-bytes  enable excluding screenshot bytes from json output
   -ehb, -exclude-headless-body     enable excluding headless header from json output
   -st, -screenshot-timeout int     set timeout for screenshot in seconds (default 10)

MATCHERS:
   -mc, -match-code string            match response with specified status code (-mc 200,302)
   -ml, -match-length string          match response with specified content length (-ml 100,102)
   -mlc, -match-line-count string     match response body with specified line count (-mlc 423,532)
   -mwc, -match-word-count string     match response body with specified word count (-mwc 43,55)
   -mfc, -match-favicon string[]      match response with specified favicon hash (-mfc 1494302000)
   -ms, -match-string string[]        match response with specified string (-ms admin)
   -mr, -match-regex string[]         match response with specified regex (-mr admin)
   -mcdn, -match-cdn string[]         match host with specified cdn provider (google, cloudfront, fastly)
   -mrt, -match-response-time string  match response with specified response time in seconds (-mrt '< 1')
   -mdc, -match-condition string      match response with dsl expression condition

EXTRACTOR:
   -er, -extract-regex string[]   display response content with matched regex
   -ep, -extract-preset string[]  display response content matched by a pre-defined regex (ipv4,mail,url)

FILTERS:
   -fc, -filter-code string            filter response with specified status code (-fc 403,401)
   -fep, -filter-error-page            filter response with ML based error page detection
   -fl, -filter-length string          filter response with specified content length (-fl 23,33)
   -flc, -filter-line-count string     filter response body with specified line count (-flc 423,532)
   -fwc, -filter-word-count string     filter response body with specified word count (-fwc 423,532)
   -ffc, -filter-favicon string[]      filter response with specified favicon hash (-ffc 1494302000)
   -fs, -filter-string string[]        filter response with specified string (-fs admin)
   -fe, -filter-regex string[]         filter response with specified regex (-fe admin)
   -fcdn, -filter-cdn string[]         filter host with specified cdn provider (google, cloudfront, fastly)
   -frt, -filter-response-time string  filter response with specified response time in seconds (-frt '> 1')
   -fdc, -filter-condition string      filter response with dsl expression condition
   -strip                              strips all tags in response. supported formats: html,xml (default html)

RATE-LIMIT:
   -t, -threads int              number of threads to use (default 50)
   -rl, -rate-limit int          maximum requests to send per second (default 150)
   -rlm, -rate-limit-minute int  maximum number of requests to send per minute

MISCELLANEOUS:
   -pa, -probe-all-ips        probe all the ips associated with same host
   -p, -ports string[]        ports to probe (nmap syntax: eg http:1,2-10,11,https:80)
   -path string               path or list of paths to probe (comma-separated, file)
   -tls-probe                 send http probes on the extracted TLS domains (dns_name)
   -csp-probe                 send http probes on the extracted CSP domains
   -tls-grab                  perform TLS(SSL) data grabbing
   -pipeline                  probe and display server supporting HTTP1.1 pipeline
   -http2                     probe and display server supporting HTTP2
   -vhost                     probe and display server supporting VHOST
   -ldv, -list-dsl-variables  list json output field keys name that support dsl matcher/filter

UPDATE:
   -up, -update                 update httpx to latest version
   -duc, -disable-update-check  disable automatic httpx update check

OUTPUT:
   -o, -output string                     file to write output results
   -oa, -output-all                       filename to write output results in all formats
   -sr, -store-response                   store http response to output directory
   -srd, -store-response-dir string       store http response to custom directory
   -ob, -omit-body                        omit response body in output
   -csv                                   store output in csv format
   -csvo, -csv-output-encoding string     define output encoding
   -j, -json                              store output in JSONL(ines) format
   -irh, -include-response-header         include http response (headers) in JSON output (-json only)
   -irr, -include-response                include http request/response (headers + body) in JSON output (-json only)
   -irrb, -include-response-base64        include base64 encoded http request/response in JSON output (-json only)
   -include-chain                         include redirect http chain in JSON output (-json only)
   -store-chain                           include http redirect chain in responses (-sr only)
   -svrc, -store-vision-recon-cluster     include visual recon clusters (-ss and -sr only)
   -pr, -protocol string                  protocol to use (unknown, http11)
   -fepp, -filter-error-page-path string  path to store filtered error pages (default "filtered_error_page.json")

CONFIGURATIONS:
   -config string                   path to the httpx configuration file (default $HOME/.config/httpx/config.yaml)
   -r, -resolvers string[]          list of custom resolver (file or comma separated)
   -allow string[]                  allowed list of IP/CIDR's to process (file or comma separated)
   -deny string[]                   denied list of IP/CIDR's to process (file or comma separated)
   -sni, -sni-name string           custom TLS SNI name
   -random-agent                    enable Random User-Agent to use (default true)
   -H, -header string[]             custom http headers to send with request
   -http-proxy, -proxy string       http proxy to use (eg http://127.0.0.1:8080)
   -unsafe                          send raw requests skipping golang normalization
   -resume                          resume scan using resume.cfg
   -fr, -follow-redirects           follow http redirects
   -maxr, -max-redirects int        max number of redirects to follow per host (default 10)
   -fhr, -follow-host-redirects     follow redirects on the same host
   -rhsts, -respect-hsts            respect HSTS response headers for redirect requests
   -vhost-input                     get a list of vhosts as input
   -x string                        request methods to probe, use 'all' to probe all HTTP methods
   -body string                     post body to include in http request
   -s, -stream                      stream mode - start elaborating input targets without sorting
   -sd, -skip-dedupe                disable dedupe input items (only used with stream mode)
   -ldp, -leave-default-ports       leave default http/https ports in host header (eg. http://host:80 - https://host:443
   -ztls                            use ztls library with autofallback to standard one for tls13
   -no-decode                       avoid decoding body
   -tlsi, -tls-impersonate          enable experimental client hello (ja3) tls randomization
   -no-stdin                        Disable Stdin processing
   -hae, -http-api-endpoint string  experimental http api endpoint

DEBUG:
   -health-check, -hc        run diagnostic check up
   -debug                    display request/response content in cli
   -debug-req                display request content in cli
   -debug-resp               display response content in cli
   -version                  display httpx version
   -stats                    display scan statistic
   -profile-mem string       optional httpx memory profile dump file
   -silent                   silent mode
   -v, -verbose              verbose mode
   -si, -stats-interval int  number of seconds to wait between showing a statistics update (default: 5)
   -nc, -no-color            disable colors in cli output

OPTIMIZATIONS:
   -nf, -no-fallback                  display both probed protocol (HTTPS and HTTP)
   -nfs, -no-fallback-scheme          probe with protocol scheme specified in input 
   -maxhr, -max-host-error int        max error count per host before skipping remaining path/s (default 30)
   -e, -exclude string[]              exclude host matching specified filter ('cdn', 'private-ips', cidr, ip, regex)
   -retries int                       number of retries
   -timeout int                       timeout in seconds (default 10)
   -delay value                       duration between each http request (eg: 200ms, 1s) (default -1ns)
   -rsts, -response-size-to-save int  max response size to save in bytes (default 2147483647)
   -rstr, -response-size-to-read int  max response size to read in bytes (default 2147483647)

CLOUD:
   -auth                           configure projectdiscovery cloud (pdcp) api key (default true)
   -pd, -dashboard                 upload / view output in projectdiscovery cloud (pdcp) UI dashboard
   -aid, -asset-id string          upload new assets to existing asset id (optional)
   -aname, -asset-name string      assets group name to set (optional)
   -pdu, -dashboard-upload string  upload httpx output file (jsonl) in projectdiscovery cloud (pdcp) UI dashboard
```

# Running httpx

[](https://github.com/projectdiscovery/httpx#running-httpx)

For details about running httpx, see [https://docs.projectdiscovery.io/tools/httpx/running](https://docs.projectdiscovery.io/tools/httpx/running).

### Using `httpx` as a library

[](https://github.com/projectdiscovery/httpx#using-httpx-as-a-library)

`httpx` can be used as a library by creating an instance of the `Option` struct and populating it with the same options that would be specified via CLI. Once validated, the struct should be passed to a runner instance (to be closed at the end of the program) and the `RunEnumeration` method should be called. A minimal example of how to do it is in the [examples](https://github.com/projectdiscovery/httpx/blob/main/examples) folder

# Notes

[](https://github.com/projectdiscovery/httpx#notes)

- As default, `httpx` probe with **HTTPS** scheme and fall-back to **HTTP** only if **HTTPS** is not reachable.
- The `-no-fallback` flag can be used to probe and display both **HTTP** and **HTTPS** result.
- Custom scheme for ports can be defined, for example `-ports http:443,http:80,https:8443`
- Custom resolver supports multiple protocol (**doh|tcp|udp**) in form of `protocol:resolver:port` (e.g. `udp:127.0.0.1:53`)
- The following flags should be used for specific use cases instead of running them as default with other probes:
    - `-ports`
    - `-path`
    - `-vhost`
    - `-screenshot`
    - `-csp-probe`
    - `-tls-probe`
    - `-favicon`
    - `-http2`
    - `-pipeline`
    - `-tls-impersonate`

# Acknowledgement

[](https://github.com/projectdiscovery/httpx#acknowledgement)

Probing feature is inspired by [@tomnomnom/httprobe](https://github.com/tomnomnom/httprobe) work ❤️

---

`httpx` is made with 💙 by the [projectdiscovery](https://projectdiscovery.io/) team and distributed under [MIT License](https://github.com/projectdiscovery/httpx/blob/main/LICENSE.md).

[![Join Discord](https://raw.githubusercontent.com/projectdiscovery/nuclei-burp-plugin/main/static/join-discord.png)](https://discord.gg/projectdiscovery)
**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/projectdiscovery/httpx). Be sure to check out the original post for more details.

# Guide to Using httpx

Discover httpx a powerful tool for reconnaissance, and HTTP probing.

# **Introduction**

httpx is a powerful tool designed for HTTP probing and reconnaissance. It allows users to identify and gather information about web services efficiently. Below, we dive into various commands and usage scenarios of httpx, providing detailed examples and descriptions for each feature.

![](https://miro.medium.com/v2/resize:fit:700/1*7qpORQguwNWIdHNo8BBS3g.jpeg)

# **TL;DR**

You can find a shorter cheat sheet version of this article [here](https://learntheshell.com/posts/guide-to-httpx/).

# **Basic Usage**

## **Probe Host**

To probe a single host, use the following command:

httpx -u example.com -probe

This command initiates an HTTP probe on `example.com`. This is useful for quickly checking the availability of the web page.

## **Scan Hosts from Input File**

To scan multiple hosts listed in a file, use:

httpx -l hosts.txt

Here, `hosts.txt` contains the list of target hosts, each on a new line. The output will include a list of hosts where the HTTP probe was successful. This is particularly helpful when dealing with large sets of hosts, such as those generated from subdomain enumeration tools.

## **Scan Targets from Other Program Output**

httpx can also take input from other programs using pipes:

cat hosts.txt | grep example.com | httpx

This method reads hosts from `hosts.txt`, grep for specific domain and pipes them directly into httpx for scanning.

## **Tool Chain Example**

Combining httpx with other tools, like subfinder:

subfinder -d example.com -silent | httpx -title -tech-detect -status-code

This command uses `subfinder` to find subdomains of `example.com` and pipes them into httpx to get the page title, detect technologies, and retrieve HTTP status codes.

## **Testing Multiple Ports**

To scan multiple common HTTP ports:

httpx -u example.com -ports 80,443,8009,8080,8081,8090,8180,9443

This command tests the specified ports for HTTP services on example.com. Testing multiple ports is crucial because web services can run on non-standard ports, and identifying these can reveal additional attack surfaces.

## **Path Brute-force**

Test different paths or files:

httpx -l urls.txt -sc -path "/,/path1,/path2,/path3"

This command checks the specified paths on the targets from `urls.txt` file and displays the status codes. It might be useful when you want to check multiple paths or files on a single host or as in this example list of URLs.

# **Probes**

httpx offers a variety of probes that allow you to extract detailed information from your HTTP scans. These probes are essential for gaining deeper insights into the target’s properties, such as the response status, server details, and content types. By using these probes, you can tailor your scans to capture the most relevant data for your analysis.

httpx -status-code -content-type -content-length -location \  
-title -web-server -tech-detect -ip -cname -word-count -line-count -response-time \  
-cdn -hash sha256 -include-response -silent -stats -follow-host-redirects -max-redirects 2

This command collects a wide range of data, including status code, content type, server name, and more, following redirects up to two times. This allows you to get a detailed overview of the target’s HTTP properties.

Save responses and filter HTTP redirects and error pages:

httpx -silent -l urls.txt -j -o httpx.json -sr \  
-sc -title -ct -cl -bp -server -td -ip -cname -word-count -hash sha256 -fep -fc 301 \  
-tlsi -random-agent -stats -t 5 -rl 10 -timeout 5 -maxhr 3

This command saves the scan results in `httpx.json`, displaying various headers and applying filters to ignore specific status codes and error pages. This is useful for post-processing and analyzing the results offline — for example looking for secrets like hard-coded API keys.

## **Interesting Probes**

Here are some of the key probes available in httpx:

- `-sc, -status-code`: Display response status-code
- `-title`: Display page title
- `-bp`: Display body preview
- `-server, -web-server`: Display server name
- `-ip`: Display host IP
- `-cname`: Display host CNAME
- `-cl, -content-length`: Display response content-length
- `-ct, -content-type`: Display response content-type
- `-location`: Display response redirect location
- `-hash string`: Display response body hash (supported: md5, mmh3, simhash, sha1, sha256, sha512)
- `-rt, -response-time`: Display response time
- `-lc, -line-count`: Display response body line count
- `-wc, -word-count`: Display response body word count
- `-td, -tech-detect`: Display technology in use based on wappalyzer dataset (default true)
- `-method`: Display HTTP request method
- `-cdn`: Display CDN/WAF in use (default true)

# **Rate Limits**

Rate limits in httpx allow you to control the number of requests sent per second or minute, ensuring that your scanning process does not overwhelm the target server or your network. This feature is essential for maintaining a respectful and efficient scanning. By configuring rate limits, you can balance the thoroughness of your scans with the need to avoid detection and throttling by the target server. Here’s how you can set and manage rate limits in httpx:

httpx -u example.com -t 10 -rate-limit 50

This sets the number of threads to 10 and limits the rate to 50 requests per second.

## **Rate Limit Options**

- `-t int`: Number of threads
- `-rl int`: Maximum requests per second
- `-rlm int`: Maximum number of requests per minute

# **Matchers**

Matchers in httpx enable you to filter and process responses based on specific criteria, such as HTTP status codes, the presence of certain strings, or regular expressions. This functionality is crucial for narrowing down results to those that meet particular conditions, making your scans more focused and effective. By using matchers, you can quickly identify and act upon relevant responses, optimizing your workflow and ensuring that you capture the data that matters most to your analysis or security assessments. Here’s how you can utilize matchers in httpx to streamline your scanning process:

## **Match Specific HTTP Codes**

cat hosts.txt | httpx -mc 200,302

This matches responses with HTTP status codes 200 or 302.

## **Match Responses with Specific String**

cat hosts.txt | httpx -ms admin

This matches responses containing the string “admin”.

## **Match Responses with Regex**

cat hosts.txt | httpx -mr 'admin*'

This matches responses that fit the regex pattern `admin*`.

# **Filters**

Filters in httpx allow you to exclude unwanted responses based on specific criteria, such as HTTP status codes or text content. This feature is essential for refining your scan results, enabling you to focus only on the relevant data and reducing noise from your output. By applying filters, you can efficiently manage large volumes of data, streamline your analysis, and ensure that you are only working with the most pertinent information. Here’s how you can leverage filters in httpx to optimize your scanning and data processing workflows:

## **Filter Responses with Specific HTTP Codes**

httpx -l urls.txt -fc 404,403,401,400,500

This filters out responses with the specified status codes.

## **Filter Responses Based on ML Error Page Detection**

httpx -l urls.txt -sc -fep

This uses machine learning to filter error pages.

## **Filter Responses with Specific Text**

httpx -l urls.txt -fs error

This filters out responses containing the text “error”.

## **Filter Responses Based on Regex**

httpx -l urls.txt -fe '.*Error.*'

This filters out responses that match the regex pattern `.*Error.*`.

# **Extractors**

Extractors in httpx are powerful tools designed to pull specific parts of the response content based on patterns or regular expressions. This feature is particularly useful for isolating and retrieving valuable data from HTTP responses, such as usernames, emails, or other critical information embedded within the response body. By using extractors, you can automate the process of data extraction, making it more efficient and accurate. When you are performing security assessments, extractors help you focus on the essential elements of your scan results, ensuring that you gather the necessary information quickly and effectively. Here’s how you can utilize extractors in httpx to enhance your data extraction processes:

## **Extract Part of the Response with Regex**

cat hosts.txt | httpx -er 'admin*'

This extracts parts of the response that match the regex `admin*`.

# **Optimizations**

Optimizations in httpx are designed to enhance the performance and efficiency of your scans. By fine-tuning various parameters, you can control how httpx handles timeouts, retries, error counts, and host exclusions. These optimizations are crucial for large-scale scanning operations, where performance and accuracy are paramount. Leveraging these settings allows you to minimize resource usage, avoid unnecessary retries, and ensure that your scans run smoothly without interruption. Here are some key optimization techniques to improve your scanning process:

## **Probe with Protocol Scheme Supplied in the Input**

httpx -l urls.txt -nfs

This probes using the protocol scheme supplied in the input without falling back to another scheme.

## **Set Timeouts, Max Error Count, and Retries**

httpx -l urls.txt -timeout 5 -maxhr 3 -retries 1

This sets a timeout of 5 seconds, a maximum error count of 3 per host, and 1 retry.

# **Output**

httpx provide versatile options for storing and displaying scan results. Here’s how you can utilize httpx’s output options to enhance your scanning and analysis processes:

## **Save Output to a File**

httpx -l urls.txt -o httpx.log

This saves the scan output to `httpx.log`.

## **Print Output in JSONL Format**

httpx -l urls.txt -j

This prints the output in JSON Lines format.

## **Print Stats During Scan**

httpx -l urls.txt -stats

This command prints scan statistics during execution. You can change how often stats are displayed using `-si` parameter followed by the number of seconds. The default interval is `5` seconds.

## **Store Responses**

httpx -l urls.txt -sr http-responses/

This saves the HTTP responses in a given directory.

# **Screenshots**

The Screenshots feature in httpx allows you to capture visual representations of web pages during your scanning process. This capability is invaluable for visually inspecting how web pages appear and verifying their content and layout. httpx screenshots are made using headless browser. Here are some examples:

## **Create a Screenshot of the Website**

echo https://example.com | httpx -ss -st

This takes a screenshot of the specified URL.

## **Screenshot Options**

- `-ss`: Save a screenshot of the page using a headless browser
- `-st`: Set a timeout for the screenshot (default 10 seconds)

# **Configuration File**

httpx offers a robust configuration file feature that allows users to customize and streamline their scanning operations according to specific requirements. This feature is particularly useful for defining scan parameters, such as headers, timeouts, retries, and output preferences, in a structured YAML format. By utilizing httpx configuration files, users can standardize scan settings across multiple sessions, enhance scanning efficiency, and tailor scans to different environments or targets.

## **Use Custom Configuration File**

httpx -config httpx-config.yaml

This uses a custom configuration file located at `httpx-config.yaml`.

## **Example Configuration File**

status-code: true  
content-length: true  
content-type: true  
location: true  
line-count: true  
word-count: true  
title: true  
body-preview: true  
web-server: true  
tech-detect: true  
ip: true  
cname: true  
filter-code: 302,401,403  
filter-error-page: true  
threads: 10  
rate-limit: 20  
update: false  
disable-update-check: true  
store-response: true  
store-response-dir: httpx-responses  
json: true  
include-response-header: true  
include-response: true  
random-agent: true  
#header: Custom Global Headers  
follow-redirects: false  
follow-host-redirects: false  
tls-impersonate: true  
version: false  
stats: true  
silent: true  
stats-interval: 5  
max-host-error: 3  
retries: 0  
timeout: 5

This configuration file sets various default parameters for httpx scans.

# **Updates**

httpx simplifies updates with options to check for and install the latest version. It also allows users to disable automated update checks on startup for better control of the scan.

## **Disable Update Checks**

httpx -l targets.txt -duc

This disables automatic update checks.

## **Update** httpx

httpx -up

This updates httpx to the latest version.

# **Processing JSONL Results with jq**

As a bonus here are some examples of how to filter and extract specific information from httpx JSON output.

Learn how to selectively process JSON results based on status codes, technology, titles, and more:

## **Select Results with `status_code == 200`**

cat httpx.json | jq 'select(.status_code == 200)'

This filters results where the status code is 200.

## **Select Results with `Ruby` in `tech`**

cat httpx.json | jq 'select(.tech[] | contains("Ruby"))'

This selects results that have “Ruby” in the technology list.

## **Select URL, tech where tech contains `Ruby`**

cat httpx.json | jq 'select(.tech[] | contains("Ruby")) | .tech,.url' 2>/  
dev/null

This extracts URLs and technologies where the tech list contains “Ruby”.

## **The Same for PHP**

cat httpx.json | jq 'select(.tech[] | contains("PHP")) | .tech,.url' 2>/dev/null

This extracts URLs and technologies where the tech list contains “PHP”.

## **Search Results by Title**

cat httpx.json | jq 'select(.title | contains("Index of"))'

This searches results for titles containing “Index of”.

## **Search All Results for Nginx (Case-Insensitive)**

cat httpx.json | jq 'select(.tech[] | ascii_downcase| contains("nginx")) | .tech,.url' 2>/dev/null

This searches for Nginx in the technology list, case-insensitively.

## **Extract Basic Info About Each Request**

cat httpx.json| jq '{url: .url, host: .host, method: .method, status_code: .status_code, content_type: .content_type, words: .words, webserver: .webserver, tech: .tech, hash: .hash}'

This extracts basic information about each request.

## **The Same, but Only for 200 Responses**

cat httpx-* | jq 'select(.status_code == 200) | {url: .url, host: .host, method: .method, status_code: .status_code, content_type: .content_type, words: .words, webserver: .webserver, tech: .tech, hash: .hash}'

This extracts basic information for requests with a status code of 200.

## **Select `200` Status Code and Content Type `application/json`**

cat httpx.json| jq 'select((.status_code == 200) and (.content_type == "application/json"))'

This selects results where the status code is 200 and the content type is `application/json`.

# **Conclusion**

In summary, httpx is a powerful tool tailored for security assessments, web reconnaissance, and HTTP probing tasks. httpx enables users to efficiently scan hosts, test multiple ports, perform path bruteforcing, and employ advanced filtering and extraction on the results. httpx is useful for identifying vulnerabilities and gaining insights into the technological landscape of target systems. By integrating httpx into your toolkit, you gain a reliable HTTP scanning solution for conducting infrastructure analysis.

**References**

- [Httpx usage](https://docs.projectdiscovery.io/tools/httpx/usage)
- [Running httpx](https://docs.projectdiscovery.io/tools/httpx/running)

**Credit:** This information was adapted from an excellent guide on [Medium](https://medium.com/@learntheshell/guide-to-using-httpx-a542cbdc4ed4). Be sure to check out the original post for more details.

## httpx Cheat Sheet - Commands & Examples Tutorial [∞](https://highon.coffee/blog/httpx-cheat-sheet/ "Permalink")

04 Jun 2024  (https://twitter.com/Arr0way)

![httpx logo](https://highon.coffee/img/httpx-logo.png)

## What is httpx?[](https://highon.coffee/blog/httpx-cheat-sheet/#what-is-httpx)

httpx is a fast and multi-purpose HTTP toolkit made by Project Discovery that allows running multiple probes using the retryablehttp library. It is designed to maintain result reliability with an increased number of threads. httpx can be used to obtain web server information, such as headers, download pages and take screenshots of targets. httpx is perfect for validating http/https servers for large scopes on bugbounty programs or performing asset management / penetration testing.

- [What is httpx?](https://highon.coffee/blog/httpx-cheat-sheet/#what-is-httpx)
- [httpx Installation](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-installation)
- [httpx Project Discovery Tutorial](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-project-discovery-tutorial)
- [httpx Supported Probes](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-supported-probes)
- [httpx Cheat Sheet](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-cheat-sheet)
    - [httpx Input Commands](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-input-commands)
    - [httpx Probe Commands](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-probe-commands)
    - [httpx Headless Options](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-headless-options)
    - [httpx Match in Response](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-match-in-response)
    - [httpx Extract Regex Strings](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-extract-regex-strings)
    - [httpx Filters](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-filters)
    - [httpx Rate Limiting](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-rate-limiting)
    - [Misc httpx Commands](https://highon.coffee/blog/httpx-cheat-sheet/#misc-httpx-commands)
    - [httpx Update](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-update)
    - [httpx File Output](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-file-output)
    - [httpx Config Options](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-config-options)
    - [httpx Debug Options](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-debug-options)
    - [Optimizations](https://highon.coffee/blog/httpx-cheat-sheet/#optimizations)
- [Real World httpx Examples](https://highon.coffee/blog/httpx-cheat-sheet/#real-world-httpx-examples)
    - [DNSX to httpx](https://highon.coffee/blog/httpx-cheat-sheet/#dnsx-to-httpx)
    - [httpx Follow Redirects](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-follow-redirects)
    - [httpx Screenshot](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-screenshot)
    - [Basic Recon](https://highon.coffee/blog/httpx-cheat-sheet/#basic-recon)
- [Conclusion](https://highon.coffee/blog/httpx-cheat-sheet/#conclusion)

## httpx Installation[](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-installation)

How to install httpx:

```bash
go install -v github.com/projectdiscovery/httpx/cmd/httpx@latest
```

## httpx Project Discovery Tutorial[](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-project-discovery-tutorial)

After installation the following simple httpx tutorial will get you up and scanning web servers:

```bash
cat targets.txt | httpx 
```

For more options and real world httpx examples see the bottom of this document.

## httpx Supported Probes[](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-supported-probes)

The type of data httpx can obtain from target web servers:

|Probes|Default check|Probes|Default check|
|---|---|---|---|
|URL|true|IP|true|
|Title|true|CNAME|true|
|Status Code|true|Raw HTTP|false|
|Content Length|true|HTTP2|false|
|TLS Certificate|true|HTTP Pipeline|false|
|CSP Header|true|Virtual host|false|
|Line Count|true|Word Count|true|
|Location Header|true|CDN|false|
|Web Server|true|Paths|false|
|Web Socket|true|Ports|false|
|Response Time|true|Request Method|true|
|Favicon Hash|false|Probe Status|false|
|Body Hash|true|Header Hash|true|
|Redirect chain|false|URL Scheme|true|
|JARM Hash|false|ASN|false|

## TIP: Take Screenshots with httpx

To take screenshots with httpx use `-screenshot` or `-ss`

## httpx Cheat Sheet[](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-cheat-sheet)

### httpx Input Commands[](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-input-commands)

|COMMAND|DESCRIPTION|
|---|---|
|`-l, -list string`|input file containing list of hosts to process|
|`-rr, -request string`|file containing raw request|
|`-u, -target string[]`|input target host(s) to probe|

### httpx Probe Commands[](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-probe-commands)

|COMMAND|DESCRIPTION|
|---|---|
|`-sc, -status-code`|display response status-code|
|`-cl, -content-length`|display response content-length|
|`-ct, -content-type`|display response content-type|
|`-location`|display response redirect location|
|`-favicon`|display mmh3 hash for '/favicon.ico' file|
|`-hash string`|display response body hash (supported: md5,mmh3,simhash,sha1,sha256,sha512)|
|`-jarm`|display jarm fingerprint hash|
|`-rt, -response-time`|display response time|
|`-lc, -line-count`|display response body line count|
|`-wc, -word-count`|display response body word count|
|`-title`|display page title|
|`-bp, -body-preview`|display first N characters of response body (default 100)|
|`-server, -web-server`|display server name|
|`-td, -tech-detect`|display technology in use based on wappalyzer dataset|
|`-method`|display http request method|
|`-websocket`|display server using websocket|
|`-ip`|display host ip|
|`-cname`|display host cname|
|`-asn`|display host asn information|
|`-cdn`|display cdn/waf in use (default true)|
|`-probe`|display probe status|

### httpx Headless Options[](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-headless-options)

|COMMAND|DESCRIPTION|
|---|---|
|`-ss, -screenshot`|enable saving screenshot of the page using headless browser|
|`-system-chrome`|enable using local installed chrome for screenshot|
|`-esb, -exclude-screenshot-bytes`|enable excluding screenshot bytes from json output|
|`-ehb, -exclude-headless-body`|enable excluding headless header from json output|

### httpx Match in Response[](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-match-in-response)

Allows httpx to match something in the server response header / body / http response code or url etc.

|COMMAND|DESCRIPTION|
|---|---|
|`-mc, -match-code string`|match response with specified status code (-mc 200,302)|
|`-ml, -match-length string`|match response with specified content length (-ml 100,102)|
|`-mlc, -match-line-count string`|match response body with specified line count (-mlc 423,532)|
|`-mwc, -match-word-count string`|match response body with specified word count (-mwc 43,55)|
|`-mfc, -match-favicon string[]`|match response with specified favicon hash (-mfc 1494302000)|
|`-ms, -match-string string`|match response with specified string (-ms admin)|
|`-mr, -match-regex string`|match response with specified regex (-mr admin)|
|`-mcdn, -match-cdn string[]`|match host with specified cdn provider (cloudfront, fastly, google, leaseweb, stackpath)|
|`-mrt, -match-response-time string`|match response with specified response time in seconds (-mrt '< 1')|
|`-mdc, -match-condition string`|match response with dsl expression condition|

### httpx Extract Regex Strings[](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-extract-regex-strings)

Allows httpx to extract regex strings from the reponse.

|COMMAND|DESCRIPTION|
|---|---|
|`-er, -extract-regex string[]`|display response content with matched regex|
|`-ep, -extract-preset string[]`|display response content matched by a pre-defined regex (mail, url, ipv4)|

### httpx Filters[](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-filters)

Filter by response code, length, server version, error page, url etc

|COMMAND|DESCRIPTION|
|---|---|
|`-fc, -filter-code string`|filter response with specified status code (-fc 403,401)|
|`-fep, -filter-error-page`|filter response with ML based error page detection|
|`-fl, -filter-length string`|filter response with specified content length (-fl 23,33)|
|`-flc, -filter-line-count string`|filter response body with specified line count (-flc 423,532)|
|`-fwc, -filter-word-count string`|filter response body with specified word count (-fwc 423,532)|
|`-ffc, -filter-favicon string[]`|filter response with specified favicon hash (-ffc 1494302000)|
|`-fs, -filter-string string`|filter response with specified string (-fs admin)|
|`-fe, -filter-regex string`|filter response with specified regex (-fe admin)|
|`-fcdn, -filter-cdn string[]`|filter host with specified cdn provider (cloudfront, fastly, google, leaseweb, stackpath)|
|`-frt, -filter-response-time string`|filter response with specified response time in seconds (-frt '> 1')|
|`-fdc, -filter-condition string`|filter response with dsl expression condition|
|`-strip`|strips all tags in response. supported formats: html,xml (default html)|

### httpx Rate Limiting[](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-rate-limiting)

Limit the number of requests httpx can make per second / per minute and configure the number of threads.

|COMMAND|DESCRIPTION|
|---|---|
|`-t, -threads int`|number of threads to use (default 50)|
|`-rl, -rate-limit int`|maximum requests to send per second (default 150)|
|`-rlm, -rate-limit-minute int`|maximum number of requests to send per minute|

### Misc httpx Commands[](https://highon.coffee/blog/httpx-cheat-sheet/#misc-httpx-commands)

|COMMAND|DESCRIPTION|
|---|---|
|`-pa, -probe-all-ips`|probe all the ips associated with same host|
|`-p, -ports string[]`|ports to probe (nmap syntax: eg http:1,2-10,11,https:80)|
|`-path string`|path or list of paths to probe (comma-separated, file)|
|`-tls-probe`|send http probes on the extracted TLS domains (dns_name)|
|`-csp-probe`|send http probes on the extracted CSP domains|
|`-tls-grab`|perform TLS(SSL) data grabbing|
|`-pipeline`|probe and display server supporting HTTP1.1 pipeline|
|`-http2`|probe and display server supporting HTTP2|
|`-vhost`|probe and display server supporting VHOST|
|`-ldv, -list-dsl-variables`|list json output field keys name that support dsl matcher/filter|

### httpx Update[](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-update)

How to update httpx + how to disable auto update.

|COMMAND|DESCRIPTION|
|---|---|
|`-up, -update`</code>|update httpx to latest version|
|`-duc, -disable-update-check`|disable automatic httpx update check|

### httpx File Output[](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-file-output)

httpx output file options.

|COMMAND|DESCRIPTION|
|---|---|
|`-o, -output string`|file to write output results|
|`-oa, -output-all`|filename to write output results in all formats|
|`-sr, -store-response`|store http response to output directory|
|`-srd, -store-response-dir string`|store http response to custom directory|
|`-csv`|store output in csv format|
|`-csvo, -csv-output-encoding string`|define output encoding|
|`-j, -json`|store output in JSONL(ines) format|
|`-irh, -include-response-header`|include http response (headers) in JSON output (-json only)|
|`-irr, -include-response`|include http request/response (headers + body) in JSON output (-json only)|
|`-irrb, -include-response-base64`|include base64 encoded http request/response in JSON output (-json only)|
|`-include-chain`|include redirect http chain in JSON output (-json only)|
|`-store-chain`|include http redirect chain in responses (-sr only)|
|`-svrc, -store-vision-recon-cluster`|include visual recon clusters (-ss and -sr only)|

### httpx Config Options[](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-config-options)

|COMMAND|DESCRIPTION|
|---|---|
|`-config string`|path to the httpx configuration file (default $HOME/.config/httpx/config.yaml)|
|`-r, -resolvers string[]`|list of custom resolver (file or comma separated)|
|`-allow string[]`|allowed list of IP/CIDR's to process (file or comma separated)|
|`-deny string[]`|denied list of IP/CIDR's to process (file or comma separated)|
|`-sni, -sni-name string`|custom TLS SNI name|
|`-random-agent`|enable Random User-Agent to use (default true)|
|`-H, -header string[]`|custom http headers to send with request|
|`-http-proxy, -proxy string`|http proxy to use (eg http://127.0.0.1:8080)|
|`-unsafe`|send raw requests skipping golang normalization|
|`-resume`|resume scan using resume.cfg|
|`-fr, -follow-redirects`|follow http redirects|
|`-maxr, -max-redirects int`|max number of redirects to follow per host (default 10)|
|`-fhr, -follow-host-redirects`|follow redirects on the same host|
|`-rhsts, -respect-hsts`|respect HSTS response headers for redirect requests|
|`-vhost-input`|get a list of vhosts as input|
|`-x string`|request methods to probe, use 'all' to probe all HTTP methods|
|`-body string`|post body to include in http request|
|`-s, -stream`|stream mode - start elaborating input targets without sorting|
|`-sd, -skip-dedupe`|disable dedupe input items (only used with stream mode)|
|`-ldp, -leave-default-ports`|leave default http/https ports in host header (eg. http://host:80 - https://host:443)|
|`-ztls`|use ztls library with autofallback to standard one for tls13|
|`-no-decode`|avoid decoding body|
|`-tlsi, -tls-impersonate`|enable experimental client hello (ja3) tls randomization|
|`-no-stdin`|Disable Stdin processing|

### httpx Debug Options[](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-debug-options)

|COMMAND|DESCRIPTION|
|---|---|
|`-health-check, -hc`|run diagnostic check up|
|`-debug`|display request/response content in cli|
|`-debug-req`|display request content in cli|
|`-debug-resp`|display response content in cli|
|`-version`|display httpx version|
|`-stats`|display scan statistic|
|`-profile-mem string`|optional httpx memory profile dump file|
|`-silent`|silent mode|
|`-v, -verbose`|verbose mode|
|`-si, -stats-interval int`|number of seconds to wait between showing a statistics update (default: 5)|
|`-nc, -no-color`|disable colors in cli output|

### Optimizations[](https://highon.coffee/blog/httpx-cheat-sheet/#optimizations)

Improve the performance of httpx tune the settings to the target environment.

|COMMAND|DESCRIPTION|
|---|---|
|`-nf, -no-fallback`|display both probed protocol (HTTPS and HTTP)|
|`-nfs, -no-fallback-scheme`|probe with protocol scheme specified in input|
|`-maxhr, -max-host-error int`|max error count per host before skipping remaining path/s (default 30)|
|`-ec, -exclude-cdn`|skip full port scans for CDN/WAF (only checks for 80,443)|
|`-eph, -exclude-private-hosts`|skip any hosts which have a private ip address|
|`-retries int`|number of retries|
|`-timeout int`|timeout in seconds (default 10)|
|`-delay value`|duration between each http request (eg: 200ms, 1s) (default -1ns)|
|`-rsts, -response-size-to-save int`|max response size to save in bytes (default 2147483647)|
|`-rstr, -response-size-to-read int`|max response size to read in bytes (default 2147483647)|

## Real World httpx Examples[](https://highon.coffee/blog/httpx-cheat-sheet/#real-world-httpx-examples)

### DNSX to httpx[](https://highon.coffee/blog/httpx-cheat-sheet/#dnsx-to-httpx)

Run domains through dnsx to confirm resolution, then through httpx to confirm a 200 response from the webserver:

```bash
dnsx -d roots.txt -w <key,words> | httpx -sc -mc 200
```

### httpx Follow Redirects[](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-follow-redirects)

For httpx to follow redirects use:

```bash
httpx -follow-redirects
```

### httpx Screenshot[](https://highon.coffee/blog/httpx-cheat-sheet/#httpx-screenshot)

Take a screenshot of targets that return 200 response:

```bash
httpx -sc -mc 200 -ss
```

### Basic Recon[](https://highon.coffee/blog/httpx-cheat-sheet/#basic-recon)

```bash
httpx -t 200 -random-agent -nc -silent -timeout 8 -sc -server -title -o httpx.out
```

## Conclusion[](https://highon.coffee/blog/httpx-cheat-sheet/#conclusion)

We hope this httpx cheat sheet was useful in covering the usage of this excellent HTTP toolkit by Project Discovery for performing recon against web servers and applications.

**Credit:** This information was adapted from an excellent guide on [Highon.Coffee](https://highon.coffee/blog/httpx-cheat-sheet/). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/c41cEtw1ngA?si=-WfsiuBRD6OWRZAY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=c41cEtw1ngA). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/eQcpLMSt5Nk?si=tD0zZTs1bEZlkxoh" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=eQcpLMSt5Nk). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/8qE4w4RVCxY?si=rnPer-5NDNZBH0D_" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=8qE4w4RVCxY). Be sure to check out the original post for more details.





