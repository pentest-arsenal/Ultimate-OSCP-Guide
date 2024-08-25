## Intro

[](https://github.com/drwetter/testssl.sh#intro)

[![Build Status](https://github.com/drwetter/testssl.sh/actions/workflows/test.yml/badge.svg)](https://github.com/drwetter/testssl.sh/actions/workflows/test.yml) [![Gitter](https://camo.githubusercontent.com/2da7039d862cabe847953554272000b86e80b158a0723c9a832720b935df3f43/68747470733a2f2f6261646765732e6769747465722e696d2f4a6f696e253230436861742e737667)](https://gitter.im/drwetter/testssl.sh?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge) [![License](https://camo.githubusercontent.com/cad0ab1f9c9a82fd2f69e3b86931bb90469052fe181247affe14c4d0d030b04c/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f6c6963656e73652f64727765747465722f7465737473736c2e7368)](https://github.com/drwetter/testssl.sh/LICENSE) [![Docker](https://camo.githubusercontent.com/00de7cea346c3be3069e9112d85a2faee8713cefbe4724257e2e398935a81992/68747470733a2f2f696d672e736869656c64732e696f2f646f636b65722f70756c6c732f64727765747465722f7465737473736c2e7368)](https://github.com/drwetter/testssl.sh/blob/3.2/Dockerfile.md)

`testssl.sh` is a free command line tool which checks a server's service on any port for the support of TLS/SSL ciphers, protocols as well as some cryptographic flaws.

### Key features

[](https://github.com/drwetter/testssl.sh#key-features)

- Clear output: you can tell easily whether anything is good or bad.
- Machine readable output (CSV, two JSON formats)
- No need to install or to configure something. No gems, CPAN, pip or the like.
- Works out of the box: Linux, OSX/Darwin, FreeBSD, NetBSD, MSYS2/Cygwin, WSL (bash on Windows). Only OpenBSD needs bash.
- A Dockerfile is provided, there's also an official container build @ dockerhub.
- Flexibility: You can test any SSL/TLS enabled and STARTTLS service, not only web servers at port 443.
- Toolbox: Several command line options help you to run _your_ test and configure _your_ output.
- Reliability: features are tested thoroughly.
- Privacy: It's only you who sees the result, not a third party.
- Freedom: It's 100% open source. You can look at the code, see what's going on.
- The development is open (GitHub) and participation is welcome.

### License

[](https://github.com/drwetter/testssl.sh#license)

This software is free. You can use it under the terms of GPLv2, see LICENSE.

Attribution is important for the future of this project -- also in the internet. Thus if you're offering a scanner based on testssl.sh as a public and/or paid service in the internet you are strongly encouraged to mention to your audience that you're using this program and where to get this program from. That helps us to get bugfixes, other feedback and more contributions.

### Compatibility

[](https://github.com/drwetter/testssl.sh#compatibility)

Testssl.sh is working on every Linux/BSD distribution out of the box. Latest by 2.9dev most of the limitations of disabled features from the openssl client are gone due to bash-socket-based checks. As a result you can also use e.g. LibreSSL or OpenSSL >= 1.1.1 . testssl.sh also works on other unixoid systems out of the box, supposed they have `/bin/bash` >= version 3.2 and standard tools like sed and awk installed. An implicit (silent) check for binaries is done when you start testssl.sh . System V needs probably to have GNU grep installed. MacOS X and Windows (using MSYS2, Cygwin or WSL) work too.

Update notification here or @ [mastodon](https://infosec.exchange/@testssl) (old: [twitter](https://twitter.com/drwetter))

### Installation

[](https://github.com/drwetter/testssl.sh#installation)

You can download testssl.sh branch 3.2 just by cloning this git repository:

```
git clone --depth 1 https://github.com/drwetter/testssl.sh.git
```

3.2 is now the latest branch which evolved from 3.1dev. It's in the release candidate phase. For the former stable version help yourself by downloading the [ZIP](https://codeload.github.com/drwetter/testssl.sh/zip/v3.0.8) or [tar.gz](https://codeload.github.com/drwetter/testssl.sh/tar.gz/v3.0.8) archive. Just `cd` to the directory created (=INSTALLDIR) and run it off there.

#### Docker

[](https://github.com/drwetter/testssl.sh#docker)

Testssl.sh has minimal requirements. As stated you don't have to install or build anything. You can just run it from the pulled/cloned directory. Still if you don't want to pull the GitHub repo to your directory of choice you can pull a container from dockerhub and run it:

```
docker run --rm -ti  drwetter/testssl.sh <your_cmd_line>
```

Or if you have cloned this repo you also can just `cd` to the INSTALLDIR and run

```
docker build . -t imagefoo && docker run --rm -t imagefoo example.com
```

For more please consult [Dockerfile.md](https://github.com/drwetter/testssl.sh/blob/3.2/Dockerfile.md).

### No Warranty

[](https://github.com/drwetter/testssl.sh#no-warranty)

Usage of the program is without any warranty. Use it at yor own risk.

Testssl.sh is intended to be used as a standalone CLI tool. While we tried to apply best practise security measures, we can't guarantee that the program is without any vulnerabilities. Running as a service may pose security risks and you're recommended to apply additional security measures.

### Status

[](https://github.com/drwetter/testssl.sh#status)

We're currently in the release candidate phase for version 3.2. Bigger features will be developed in a separate branch before merged into a 3.3dev to avoid hiccups or inconsistencies.

Version 3.0.X receives bugfixes, labeled as 3.0.1, 3.0.2 and so on. This will happen until 3.2 is released.

Support for 2.9.5 has been dropped. Supported is >= 3.0.x only.

### Documentation

[](https://github.com/drwetter/testssl.sh#documentation)

- .. it is there for reading. Please do so :-) -- at least before asking questions. See man page in groff, html and markdown format in `~/doc/`.
- [https://testssl.sh/](https://testssl.sh/) will help to get you started.
- For the (older) version 2.8, Will Hunt provides a longer [description](https://www.4armed.com/blog/doing-your-own-ssl-tls-testing/), including useful background information.

### Contributing

[](https://github.com/drwetter/testssl.sh#contributing)

Contributions are welcome! See [CONTRIBUTING.md](https://github.com/drwetter/testssl.sh/blob/3.2/CONTRIBUTING.md) for details. Please also have a look at the [Coding Convention](https://github.com/drwetter/testssl.sh/blob/3.2/Coding_Convention.md).

### Bug reports

[](https://github.com/drwetter/testssl.sh#bug-reports)

Bug reports are important. It makes this project more robust.

Please file bugs in the issue tracker @ GitHub. Do not forget to provide detailed information, see template for issue, and further details @ [https://github.com/drwetter/testssl.sh/wiki/Bug-reporting](https://github.com/drwetter/testssl.sh/wiki/Bug-reporting). Nobody can read your thoughts -- yet. And only agencies your screen ;-)

You can also debug yourself, see [here](https://github.com/drwetter/testssl.sh/wiki/Findings-and-HowTo-Fix-them).

---

### External/related projects

[](https://github.com/drwetter/testssl.sh#externalrelated-projects)

Please address questions not specifically to the code of testssl.sh to the respective projects below.

#### Web frontend

[](https://github.com/drwetter/testssl.sh#web-frontend)

- [https://github.com/johannesschaefer/webnettools](https://github.com/johannesschaefer/webnettools)
- [https://github.com/TKCERT/testssl.sh-webfrontend](https://github.com/TKCERT/testssl.sh-webfrontend)

#### Free to use Web frontend + commercial API

[](https://github.com/drwetter/testssl.sh#free-to-use-web-frontend--commercial-api)

- [https://inspect.rapydblok.com](https://inspect.rapydblok.com/) (see also [https://inspect.rapydblok.com/about](https://inspect.rapydblok.com/about))

#### Mass scanner w parallel scans and elastic searching the results

[](https://github.com/drwetter/testssl.sh#mass-scanner-w-parallel-scans-and-elastic-searching-the-results)

- [https://github.com/TKCERT/testssl.sh-masscan](https://github.com/TKCERT/testssl.sh-masscan)

#### Privacy checker using testssl.sh

[](https://github.com/drwetter/testssl.sh#privacy-checker-using-testsslsh)

- [https://privacyscore.org](https://privacyscore.org/)

#### Nagios / Icinga Plugins

[](https://github.com/drwetter/testssl.sh#nagios--icinga-plugins)

- [https://github.com/dnmvisser/nagios-testssl](https://github.com/dnmvisser/nagios-testssl) (Python 3)
- [https://gitgud.malvager.net/Wazakindjes/icinga2_plugins/src/master/check_testssl.sh](https://gitgud.malvager.net/Wazakindjes/icinga2_plugins/src/master/check_testssl.sh) (Shell)

#### Brew package

[](https://github.com/drwetter/testssl.sh#brew-package)

- see [#233](https://github.com/drwetter/testssl.sh/issues/233) and [https://github.com/Homebrew/homebrew](https://github.com/Homebrew/homebrew)

#### Daemon for batch execution of testssl.sh command files

[](https://github.com/drwetter/testssl.sh#daemon-for-batch-execution-of-testsslsh-command-files)

- [https://github.com/bitsofinfo/testssl.sh-processor](https://github.com/bitsofinfo/testssl.sh-processor)

#### Daemon for batch processing of testssl.sh JSON result files for sending Slack alerts, reactive copying etc

[](https://github.com/drwetter/testssl.sh#daemon-for-batch-processing-of-testsslsh-json-result-files-for-sending-slack-alerts-reactive-copying-etc)

- [https://github.com/bitsofinfo/testssl.sh-alerts](https://github.com/bitsofinfo/testssl.sh-alerts)

#### GitHub Actions

[](https://github.com/drwetter/testssl.sh#github-actions)

- [https://github.com/marketplace/actions/testssl-sh-scan](https://github.com/marketplace/actions/testssl-sh-scan)

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/drwetter/testssl.sh). Be sure to check out the original post for more details.

# Packages and Binaries:

### testssl.sh

testssl.sh is a free command line tool which checks a server’s service on any port for the support of TLS/SSL ciphers, protocols as well as recent cryptographic flaws and more.

Key features

- Clear output: you can tell easily whether anything is good or bad
    
- Ease of installation: It works for Linux, Darwin, FreeBSD and MSYS2/Cygwin out of the box: no need to install or configure something, no gems, CPAN, pip or the like.
    
- Flexibility: You can test any SSL/TLS enabled and STARTTLS service, not only webservers at port 443
    
- Toolbox: Several command line options help you to run YOUR test and configure YOUR output
    
- Reliability: features are tested thoroughly
    
- Verbosity: If a particular check cannot be performed because of a missing capability on your client side, you’ll get a warning
    
- Privacy: It’s only you who sees the result, not a third party
    
- Freedom: It’s 100% open source. You can look at the code, see what’s going on and you can change it. Heck, even the development is open (github)
    

**Installed size:** `3.25 MB`  
**How to install:** `sudo apt install testssl.sh`

Dependencies:

- bsdextrautils
- dnsutils
- openssl
- procps

##### testssl

(unknown subject)

```console
root@kali:~# testssl --help

     "testssl [options] <URI>"    or    "testssl <options>"

"testssl <option>", where <option> is mostly standalone and one of:

     --help                        what you're looking at
     -b, --banner                  displays banner + version of testssl
     -v, --version                 same as previous
     -V, --local [pattern]         pretty print all local ciphers (of openssl only). If search pattern supplied: it is an
                                   an ignore case word pattern of cipher hexcode or any other string in its name, kx or bits

"testssl [options] <URI>", where <URI> is:

     <URI>                         host|host:port|URL|URL:port   port 443 is default, URL can only contain HTTPS as a protocol

  and [options] is/are:

     -t, --starttls <protocol>     Does a run against a STARTTLS enabled service which is one of ftp, smtp, lmtp, pop3, imap,
                                   sieve, xmpp, xmpp-server, telnet, ldap, nntp, postgres, mysql
     --xmpphost <to_domain>        For STARTTLS xmpp or xmpp-server checks it supplies the domainname (like SNI)
     --mx <domain/host>            Tests MX records from high to low priority (STARTTLS, port 25)
     --file/-iL <fname>            Mass testing option: Reads one testssl.sh command line per line from <fname>.
                                   Can be combined with --serial or --parallel. Implicitly turns on "--warnings batch".
                                   Text format 1: Comments via # allowed, EOF signals end of <fname>
                                   Text format 2: nmap output in greppable format (-oG), 1 port per line allowed
     --mode <serial|parallel>      Mass testing to be done serial (default) or parallel (--parallel is shortcut for the latter)
     --warnings <batch|off>        "batch" doesn't continue when a testing error is encountered, off continues and skips warnings
     --connect-timeout <seconds>   useful to avoid hangers. Max <seconds> to wait for the TCP socket connect to return
     --openssl-timeout <seconds>   useful to avoid hangers. Max <seconds> to wait before openssl connect will be terminated

single check as <options>  ("testssl URI" does everything except -E and -g):
     -e, --each-cipher             checks each local cipher remotely
     -E, --cipher-per-proto        checks those per protocol
     -s, --std, --categories       tests standard cipher categories by strength
     -f, --fs, --nsa               checks forward secrecy settings
     -p, --protocols               checks TLS/SSL protocols (including SPDY/HTTP2)
     -g, --grease                  tests several server implementation bugs like GREASE and size limitations
     -S, --server-defaults         displays the server's default picks and certificate info
     -P, --server-preference       displays the server's picks: protocol+cipher
     -x, --single-cipher <pattern> tests matched <pattern> of ciphers
                                   (if <pattern> not a number: word match)
     -c, --client-simulation       test client simulations, see which client negotiates with cipher and protocol
     -h, --header, --headers       tests HSTS, HPKP, server/app banner, security headers, cookie, reverse proxy, IPv4 address

     -U, --vulnerable              tests all (of the following) vulnerabilities (if applicable)
     -H, --heartbleed              tests for Heartbleed vulnerability
     -I, --ccs, --ccs-injection    tests for CCS injection vulnerability
     -T, --ticketbleed             tests for Ticketbleed vulnerability in BigIP loadbalancers
     --BB, --robot                 tests for Return of Bleichenbacher's Oracle Threat (ROBOT) vulnerability
     --SI, --starttls-injection    tests for STARTTLS injection issues
     -R, --renegotiation           tests for renegotiation vulnerabilities
     -C, --compression, --crime    tests for CRIME vulnerability (TLS compression issue)
     -B, --breach                  tests for BREACH vulnerability (HTTP compression issue)
     -O, --poodle                  tests for POODLE (SSL) vulnerability
     -Z, --tls-fallback            checks TLS_FALLBACK_SCSV mitigation
     -W, --sweet32                 tests 64 bit block ciphers (3DES, RC2 and IDEA): SWEET32 vulnerability
     -A, --beast                   tests for BEAST vulnerability
     -L, --lucky13                 tests for LUCKY13
     -WS, --winshock               tests for winshock vulnerability
     -F, --freak                   tests for FREAK vulnerability
     -J, --logjam                  tests for LOGJAM vulnerability
     -D, --drown                   tests for DROWN vulnerability
     -4, --rc4, --appelbaum        which RC4 ciphers are being offered?

tuning / connect options (most also can be preset via environment variables):
     -9, --full                    includes tests for implementation bugs and cipher per protocol (could disappear)
     --bugs                        enables the "-bugs" option of s_client, needed e.g. for some buggy F5s
     --assume-http                 if protocol check fails it assumes HTTP protocol and enforces HTTP checks
     --ssl-native                  use OpenSSL where sockets are normally used. Faster but inaccurate, avoid it if possible
     --openssl <PATH>              use this openssl binary (default: look in $PATH, $RUN_DIR of testssl)
     --proxy <host:port|auto>      (experimental) proxy connects via <host:port>, auto: values from $env ($http(s)_proxy)
     -6                            also use IPv6. Works only with supporting OpenSSL version and IPv6 connectivity
     --ip <ip>                     a) tests the supplied <ip> v4 or v6 address instead of resolving host(s) in URI
                                   b) "one" means: just test the first DNS returns (useful for multiple IPs)
                                   c) "proxy" means: dns resolution via proxy. Needed when host has no DNS.
     -n, --nodns <min|none>        if "none": do not try any DNS lookups, "min" queries A, AAAA and MX records
     --sneaky                      leave less traces in target logs: user agent, referer
     --user-agent <user agent>     set a custom user agent instead of the standard user agent
     --ids-friendly                skips a few vulnerability checks which may cause IDSs to block the scanning IP
     --phone-out                   allow to contact external servers for CRL download and querying OCSP responder
     --add-ca <CA files|CA dir>    path to <CAdir> with *.pem or a comma separated list of CA files to include in trust check
     --basicauth <user:pass>       provide HTTP basic auth information.
     --reqheader <header>          add custom http request headers

output options (can also be preset via environment variables):
     --quiet                       don't output the banner. By doing this you acknowledge usage terms normally appearing in the banner
     --wide                        wide output for tests like RC4, BEAST. FS also with hexcode, kx, strength, RFC name
     --show-each                   for wide outputs: display all ciphers tested -- not only succeeded ones
     --mapping <openssl|           openssl: use the OpenSSL cipher suite name as the primary name cipher suite name form (default)
                iana|rfc             -> use the IANA/(RFC) cipher suite name as the primary name cipher suite name form
                no-openssl|          -> don't display the OpenSSL cipher suite name, display IANA/(RFC) names only
                no-iana|no-rfc>      -> don't display the IANA/(RFC) cipher suite name, display OpenSSL names only
     --color <0|1|2|3>             0: no escape or other codes,  1: b/w escape codes,  2: color (default), 3: extra color (color all ciphers)
     --colorblind                  swap green and blue in the output
     --debug <0-6>                 1: screen output normal but keeps debug output in /tmp/.  2-6: see "grep -A 5 '^DEBUG=' testssl.sh"
     --disable-rating              Explicitly disables the rating output

file output options (can also be preset via environment variables)
     --log, --logging              logs stdout to '${NODE}-p${port}${YYYYMMDD-HHMM}.log' in current working directory (cwd)
     --logfile|-oL <logfile>       logs stdout to 'dir/${NODE}-p${port}${YYYYMMDD-HHMM}.log'. If 'logfile' is a dir or to a specified 'logfile'
     --json                        additional output of findings to flat JSON file '${NODE}-p${port}${YYYYMMDD-HHMM}.json' in cwd
     --jsonfile|-oj <jsonfile>     additional output to the specified flat JSON file or directory, similar to --logfile
     --json-pretty                 additional JSON structured output of findings to a file '${NODE}-p${port}${YYYYMMDD-HHMM}.json' in cwd
     --jsonfile-pretty|-oJ <jsonfile>  additional JSON structured output to the specified file or directory, similar to --logfile
     --csv                         additional output of findings to CSV file '${NODE}-p${port}${YYYYMMDD-HHMM}.csv' in cwd or directory
     --csvfile|-oC <csvfile>       additional output as CSV to the specified file or directory, similar to --logfile
     --html                        additional output as HTML to file '${NODE}-p${port}${YYYYMMDD-HHMM}.html'
     --htmlfile|-oH <htmlfile>     additional output as HTML to the specified file or directory, similar to --logfile
     --out(f,F)ile|-oa/-oA <fname> log to a LOG,JSON,CSV,HTML file (see nmap). -oA/-oa: pretty/flat JSON.
                                   "auto" uses '${NODE}-p${port}${YYYYMMDD-HHMM}'. If fname if a dir uses 'dir/${NODE}-p${port}${YYYYMMDD-HHMM}'
     --hints                       additional hints to findings
     --severity <severity>         severities with lower level will be filtered for CSV+JSON, possible values <LOW|MEDIUM|HIGH|CRITICAL>
     --append                      if (non-empty) <logfile>, <csvfile>, <jsonfile> or <htmlfile> exists, append to file. Omits any header
     --overwrite                   if <logfile>, <csvfile>, <jsonfile> or <htmlfile> exists it overwrites it without any warning
     --outprefix <fname_prefix>    before  '${NODE}.' above prepend <fname_prefix>


Options requiring a value can also be called with '=' e.g. testssl.sh -t=smtp --wide --openssl=/usr/bin/openssl <URI>.
<URI> always needs to be the last parameter.


```

---

Updated on: 2023-Nov-20

**Credit:** This information was adapted from an excellent guide on [Kali.org](https://www.kali.org/tools/testssl.sh/). Be sure to check out the original post for more details.

# Installation & Use Of TestSSL.sh Tool

- July 15, 2021
- [Brett DeWall](https://www.whiteoaksecurity.com/author/brettdewall/)
- [Application Security](https://www.whiteoaksecurity.com/blog/category/application-security/)

Share: 

- [Share this page on Facebook](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.whiteoaksecurity.com%2Fblog%2Finstallation-use-of-testssl-sh-tool%2F)
 - [Share this page on Twitter](https://twitter.com/intent/tweet?url=https%3A%2F%2Fwww.whiteoaksecurity.com%2Fblog%2Finstallation-use-of-testssl-sh-tool%2F&text=Installation+%26+Use+Of+TestSSL.sh+Tool)
 - [Share this page on Twitter](https://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fwww.whiteoaksecurity.com%2Fblog%2Finstallation-use-of-testssl-sh-tool%2F&title=Installation+%26%23038%3B+Use+Of+TestSSL.sh+Tool&summary=&source=)
 - Pin this page on Pinterest
 - [Send this link in an email message](mailto:?subject=White%20Oak%20Security%3A%20Installation%20%26%23038%3B%20Use%20Of%20TestSSL.sh%20Tool&body=Installation%20%26%23038%3B%20Use%20Of%20TestSSL.sh%20Tool%0D%0Ahttps%3A%2F%2Fwww.whiteoaksecurity.com%2Fblog%2Finstallation-use-of-testssl-sh-tool%2F)

When performing pentesting engagements there are times where validation of SSL/TLS ciphers, protocols, certificates, etc. is needed. One tool that White Oak Security’s pentesting team tends to make use of is the testssl.sh command line tool that is freely available for anyone to download. In this article, we will go through the installation process and how to use the new toolset.

## How To Install TestSSL.sh

Installation is pretty simple as there are a couple different options available. The first option is pulling directly from the testssl.sh website utilizing the following commands:

#### Latest stable code:

```
curl -L https://testssl.sh > testssl.nsh
```

#### Latest development code:

```
curl -L https://testssl.sh/dev/ > testssl.sh
```

The second option is pulling the testssl.sh toolset from GitHub utilizing the following command:

```
git clone --depth 1 https://github.com/drwetter/testssl.sh.git
```

![Installation of the testssl.sh command line tool by white oak security, screenshot of code verifying the install.](https://lh6.googleusercontent.com/XW2MhKTL1YitVJOekzidRW0MVyPN24yolpf3qAErix_mzBsdbq2J3sqlkt8ml3KlDjfYKmSo2GkqWacKmVsYLF5ZqyMQGJ-5IYfVkotqh58BrhX4CaaBS_oZY6InQby1RmbEb54)

Pretty simple right? Now let’s get into using the toolset.

## How Pentesters Use TestSSL.sh     

This tool is one of the simplest pentesting tools to utilize and access valuable information. To start – change into the directory where the testssl.sh script is located. Let’s issue the following commands:

#### Standard HTTPS webserver:

```
./testssl.sh https://<IP or Hostname>
```

#### Non-Standard SSL Ports:

```
./testssl.sh <IP or Hostname:PORT>
```

Here is an example screenshot utilizing the toolset:

![Screenshot of testssl.sh testing protocols & testing ciphers by white oak security blog.](https://lh6.googleusercontent.com/09udq55r0kpjSkr0i_xW_IFOXuLHtJvkikGvGGdNHK-OoV8F-QaSZXuZLo6gDquwIsOu7xIqWKWAD9pTPVqr-NfGdy0pfuW2ybc0XiJmLdQG2eCF5hPDhBuCKm_rML9nkbaSzHs)

Scrolling down the output from testssl.sh – there is useful information in regards to ciphers supported, SSL certificate information, and protocols utilized.

![Testssl.sh tool showing the certificates validity and issuer in this screenshot by white oak security.](https://lh6.googleusercontent.com/WBjysHBG6mG2gREBjtVIO-IWcW7LwiYEhPMQMDZ3wMuaK5QqHjR7jwfPT9-KTodHltNJLJMjfinF2R-lPYRoWEKUIMFB1XLWT4fcxoNs1b-FYHIQgQrgHqLBSPLTRgC1TPUOUxA)

## TestSSL.sh Recap

Hopefully this blog post demonstrates how easy testssl.sh is to be installed and utilized for everyday testing. Any additional information on the toolset can be obtained from their website – [https://testssl.sh/](https://testssl.sh/). In closing, there are many tools available that perform similar tests however we prefer this tool because it is easy to install, use, and provides clear output for reporting purposes.

**Credit:** This information was adapted from an excellent guide on [WhiteOakSecurity](https://www.whiteoaksecurity.com/blog/installation-use-of-testssl-sh-tool/). Be sure to check out the original post for more details.

# testssl.sh examples command line tool check server TLS/SSL (weak) ciphers and detect TLS/SSL vulnerabilities

Want to use command line to test  [server](https://djangocas.dev/blog/security/testssl-command-line-tool-check-server-tls-ssl-ciphers-vulnerabilities/#) TLS/SSL config properly, find weak ciphers, scan TLS/SSL server vulnerabilities, run in CI? Try testssl.sh.

Last Update: July 09, 2024

- [testssl.sh key features](https://djangocas.dev/blog/security/testssl-command-line-tool-check-server-tls-ssl-ciphers-vulnerabilities/#testsslsh-key-features)
    - [Test vulnerabilities](https://djangocas.dev/blog/security/testssl-command-line-tool-check-server-tls-ssl-ciphers-vulnerabilities/#test-vulnerabilities)
- [Install](https://djangocas.dev/blog/security/testssl-command-line-tool-check-server-tls-ssl-ciphers-vulnerabilities/#install)
- [Sample Usage](https://djangocas.dev/blog/security/testssl-command-line-tool-check-server-tls-ssl-ciphers-vulnerabilities/#sample-usage)
    - [Test website TLS/SSL config and vulnerabilities](https://djangocas.dev/blog/security/testssl-command-line-tool-check-server-tls-ssl-ciphers-vulnerabilities/#test-website-tlsssl-config-and-vulnerabilities)
    - [Generate JSON/CSV/HTML output](https://djangocas.dev/blog/security/testssl-command-line-tool-check-server-tls-ssl-ciphers-vulnerabilities/#generate-jsoncsvhtml-output)
    - [Test server default config](https://djangocas.dev/blog/security/testssl-command-line-tool-check-server-tls-ssl-ciphers-vulnerabilities/#test-server-default-config)
    - [Test server prefer protocol+cipher suites](https://djangocas.dev/blog/security/testssl-command-line-tool-check-server-tls-ssl-ciphers-vulnerabilities/#test-server-prefer-protocolcipher-suites)
- [testssl.sh usage quick reference](https://djangocas.dev/blog/security/testssl-command-line-tool-check-server-tls-ssl-ciphers-vulnerabilities/#testsslsh-usage-quick-reference)
- [References](https://djangocas.dev/blog/security/testssl-command-line-tool-check-server-tls-ssl-ciphers-vulnerabilities/#references)

If you want to test server TLS/SSL and have following requirements:

- Want to use command line to test server TLS/SSL config properly, scan TLS/SSL vulnerabilities.
- Want to run TLS/SSL test in CI (Continue Integration) environment.
- Want to output result as HTML/JSON/CSV format.
- Do not want to use Qualys SSL Labs [SSL Server test](https://www.ssllabs.com/ssltest/ "SSL Server test") for privacy concern.

`testssl.sh` is a free and open source command line tool which checks a server’s support of TLS/SSL ciphers, protocols as well as recent  [cryptographic](https://djangocas.dev/blog/security/testssl-command-line-tool-check-server-tls-ssl-ciphers-vulnerabilities/#) flaws and more.

## testssl.sh key features[](https://djangocas.dev/blog/security/testssl-command-line-tool-check-server-tls-ssl-ciphers-vulnerabilities/#testsslsh-key-features)

- Works for multiple platforms: Linux, Mac OSX, FreeBSD, NetBSD and WSL/MSYS2/Cygwin. bash is required.
- Docker image is ready to use. `docker run --rm -ti drwetter/testssl.sh`.
- Flexibility: You can test any SSL/TLS enabled and STARTTLS service, not only webservers at port 443.
- Toolbox: Several command line options help you to run your test and configure your output to HTML/JSON/CSV format.
- Reliability: features are tested thoroughly.
- Verbosity: If a particular check cannot be performed because of a missing capability on your client side, you’ll get a warning.
- Privacy: It’s only you who sees the result, not a third party.
- Freedom: It’s 100% open source on github.

### Test vulnerabilities[](https://djangocas.dev/blog/security/testssl-command-line-tool-check-server-tls-ssl-ciphers-vulnerabilities/#test-vulnerabilities)

`testssl.sh` support following vulnerabilities detection:

- Heartbleed (CVE-2014-0160)
- CCS (CVE-2014-0224)
- Ticketbleed (CVE-2016-9244), experiment.
- ROBOT
- Secure Renegotiation (RFC 5746)
- Secure Client-Initiated Renegotiation
- CRIME, TLS (CVE-2012-4929)
- BREACH (CVE-2013-3587)
- POODLE, SSL (CVE-2014-3566)
- TLS_FALLBACK_SCSV (RFC 7507)
- SWEET32 (CVE-2016-2183, CVE-2016-6329)
- FREAK (CVE-2015-0204)
- DROWN (CVE-2016-0800, CVE-2016-0703)
- LOGJAM (CVE-2015-4000), experimental
- BEAST (CVE-2011-3389)
- LUCKY13 (CVE-2013-0169), experimental
- Winshock (CVE-2014-6321), experimental
- RC4 (CVE-2013-2566, CVE-2015-2808)

## Install[](https://djangocas.dev/blog/security/testssl-command-line-tool-check-server-tls-ssl-ciphers-vulnerabilities/#install)

Mac OS X use `homebrew`:

```sh
brew install testssl
```

For linux distributions, search `testssl` in its own package manager.

e.g. Install `testssl.sh` on Debian:

```
sudo apt-get install -y testssl.sh
```

The easiest way is not install it locally, use docker image to always keep up to date. see docker command as below.

## Sample Usage[](https://djangocas.dev/blog/security/testssl-command-line-tool-check-server-tls-ssl-ciphers-vulnerabilities/#sample-usage)

### Test website TLS/SSL config and vulnerabilities[](https://djangocas.dev/blog/security/testssl-command-line-tool-check-server-tls-ssl-ciphers-vulnerabilities/#test-website-tlsssl-config-and-vulnerabilities)

The easiest way to use `testssl.sh` test a website TLS/SSL config and vulnerabilities just need website domain name. It will test all configurations and scan all the known vulnerabilities.

#### Hint

1. Options requiring a value can also be called with ‘=’ e.g. `testssl.sh -t=smtp --wide --openssl=/usr/bin/openssl <URI>`.
    
2. `<URI>` always needs to be the last parameter.
    

The following command use `https://www.example.com` as an example:

```sh
$ docker run --rm  drwetter/testssl.sh https://www.example.com

###########################################################
    testssl.sh       3.1dev from https://testssl.sh/dev/

      This program is free software. Distribution and
             modification under GPLv2 permitted.
      USAGE w/o ANY WARRANTY. USE IT AT YOUR OWN RISK!

       Please file bugs @ https://testssl.sh/bugs/

###########################################################

 Using "OpenSSL 1.0.2-chacha (1.0.2k-dev)" [~183 ciphers]
 on 68d47b2e5ecd:/home/testssl/bin/openssl.Linux.x86_64
 (built: "Jan 18 17:12:17 2019", platform: "linux-x86_64")


 Further IP addresses:   2606:2800:220:1:248:1893:25c8:1946
 rDNS (93.184.216.34):   --
 Service detected:       HTTP


 Testing protocols via sockets except NPN+ALPN

 SSLv2      not offered (OK)
 SSLv3      not offered (OK)
 TLS 1      offered (deprecated)
 TLS 1.1    offered (deprecated)
 TLS 1.2    offered (OK)
 TLS 1.3    offered (OK): final
 NPN/SPDY   h2, http/1.1, http/1.0 (advertised)
 ALPN/HTTP2 h2, http/1.1 (offered)

 Testing cipher categories

 NULL ciphers (no encryption)                      not offered (OK)
 Anonymous NULL Ciphers (no authentication)        not offered (OK)
 Export ciphers (w/o ADH+NULL)                     not offered (OK)
 LOW: 64 Bit + DES, RC[2,4], MD5 (w/o export)      not offered (OK)
 Triple DES Ciphers / IDEA                         not offered
 Obsoleted CBC ciphers (AES, ARIA etc.)            offered
 Strong encryption (AEAD ciphers) with no FS       offered (OK)
 Forward Secrecy strong encryption (AEAD ciphers)  offered (OK)


 Testing server's cipher preferences

 Has server cipher order?     yes (OK) -- TLS 1.3 and below
 Negotiated protocol          TLSv1.3
 Negotiated cipher            TLS_AES_256_GCM_SHA384, 256 bit ECDH (P-256)
 Cipher per protocol

Hexcode  Cipher Suite Name (OpenSSL)       KeyExch.   Encryption  Bits     Cipher Suite Name (IANA/RFC)
-----------------------------------------------------------------------------------------------------------------------------
SSLv2
 -
SSLv3
 -
TLSv1 (server order)
 xc013   ECDHE-RSA-AES128-SHA              ECDH 256   AES         128      TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA
 xc014   ECDHE-RSA-AES256-SHA              ECDH 256   AES         256      TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA
 x33     DHE-RSA-AES128-SHA                DH 2048    AES         128      TLS_DHE_RSA_WITH_AES_128_CBC_SHA
 x39     DHE-RSA-AES256-SHA                DH 2048    AES         256      TLS_DHE_RSA_WITH_AES_256_CBC_SHA
 x88     DHE-RSA-CAMELLIA256-SHA           DH 2048    Camellia    256      TLS_DHE_RSA_WITH_CAMELLIA_256_CBC_SHA
 x45     DHE-RSA-CAMELLIA128-SHA           DH 2048    Camellia    128      TLS_DHE_RSA_WITH_CAMELLIA_128_CBC_SHA
 x35     AES256-SHA                        RSA        AES         256      TLS_RSA_WITH_AES_256_CBC_SHA
 x84     CAMELLIA256-SHA                   RSA        Camellia    256      TLS_RSA_WITH_CAMELLIA_256_CBC_SHA
 x2f     AES128-SHA                        RSA        AES         128      TLS_RSA_WITH_AES_128_CBC_SHA
 x41     CAMELLIA128-SHA                   RSA        Camellia    128      TLS_RSA_WITH_CAMELLIA_128_CBC_SHA
 x9a     DHE-RSA-SEED-SHA                  DH 2048    SEED        128      TLS_DHE_RSA_WITH_SEED_CBC_SHA
 x96     SEED-SHA                          RSA        SEED        128      TLS_RSA_WITH_SEED_CBC_SHA
TLSv1.1 (server order)
 xc013   ECDHE-RSA-AES128-SHA              ECDH 256   AES         128      TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA
 xc014   ECDHE-RSA-AES256-SHA              ECDH 256   AES         256      TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA
 x33     DHE-RSA-AES128-SHA                DH 2048    AES         128      TLS_DHE_RSA_WITH_AES_128_CBC_SHA
 x39     DHE-RSA-AES256-SHA                DH 2048    AES         256      TLS_DHE_RSA_WITH_AES_256_CBC_SHA
 x88     DHE-RSA-CAMELLIA256-SHA           DH 2048    Camellia    256      TLS_DHE_RSA_WITH_CAMELLIA_256_CBC_SHA
 x45     DHE-RSA-CAMELLIA128-SHA           DH 2048    Camellia    128      TLS_DHE_RSA_WITH_CAMELLIA_128_CBC_SHA
 x35     AES256-SHA                        RSA        AES         256      TLS_RSA_WITH_AES_256_CBC_SHA
 x84     CAMELLIA256-SHA                   RSA        Camellia    256      TLS_RSA_WITH_CAMELLIA_256_CBC_SHA
 x2f     AES128-SHA                        RSA        AES         128      TLS_RSA_WITH_AES_128_CBC_SHA
 x41     CAMELLIA128-SHA                   RSA        Camellia    128      TLS_RSA_WITH_CAMELLIA_128_CBC_SHA
 x9a     DHE-RSA-SEED-SHA                  DH 2048    SEED        128      TLS_DHE_RSA_WITH_SEED_CBC_SHA
 x96     SEED-SHA                          RSA        SEED        128      TLS_RSA_WITH_SEED_CBC_SHA
TLSv1.2 (server order)
 xc02f   ECDHE-RSA-AES128-GCM-SHA256       ECDH 256   AESGCM      128      TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256
 xc030   ECDHE-RSA-AES256-GCM-SHA384       ECDH 256   AESGCM      256      TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
 x9e     DHE-RSA-AES128-GCM-SHA256         DH 2048    AESGCM      128      TLS_DHE_RSA_WITH_AES_128_GCM_SHA256
 x9f     DHE-RSA-AES256-GCM-SHA384         DH 2048    AESGCM      256      TLS_DHE_RSA_WITH_AES_256_GCM_SHA384
 xc027   ECDHE-RSA-AES128-SHA256           ECDH 256   AES         128      TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256
 xc013   ECDHE-RSA-AES128-SHA              ECDH 256   AES         128      TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA
 xc028   ECDHE-RSA-AES256-SHA384           ECDH 256   AES         256      TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384
 xc014   ECDHE-RSA-AES256-SHA              ECDH 256   AES         256      TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA
 x67     DHE-RSA-AES128-SHA256             DH 2048    AES         128      TLS_DHE_RSA_WITH_AES_128_CBC_SHA256
 x33     DHE-RSA-AES128-SHA                DH 2048    AES         128      TLS_DHE_RSA_WITH_AES_128_CBC_SHA
 x6b     DHE-RSA-AES256-SHA256             DH 2048    AES         256      TLS_DHE_RSA_WITH_AES_256_CBC_SHA256
 x39     DHE-RSA-AES256-SHA                DH 2048    AES         256      TLS_DHE_RSA_WITH_AES_256_CBC_SHA
 x9c     AES128-GCM-SHA256                 RSA        AESGCM      128      TLS_RSA_WITH_AES_128_GCM_SHA256
 x88     DHE-RSA-CAMELLIA256-SHA           DH 2048    Camellia    256      TLS_DHE_RSA_WITH_CAMELLIA_256_CBC_SHA
 x45     DHE-RSA-CAMELLIA128-SHA           DH 2048    Camellia    128      TLS_DHE_RSA_WITH_CAMELLIA_128_CBC_SHA
 x35     AES256-SHA                        RSA        AES         256      TLS_RSA_WITH_AES_256_CBC_SHA
 x84     CAMELLIA256-SHA                   RSA        Camellia    256      TLS_RSA_WITH_CAMELLIA_256_CBC_SHA
 x2f     AES128-SHA                        RSA        AES         128      TLS_RSA_WITH_AES_128_CBC_SHA
 x41     CAMELLIA128-SHA                   RSA        Camellia    128      TLS_RSA_WITH_CAMELLIA_128_CBC_SHA
 x9a     DHE-RSA-SEED-SHA                  DH 2048    SEED        128      TLS_DHE_RSA_WITH_SEED_CBC_SHA
 x96     SEED-SHA                          RSA        SEED        128      TLS_RSA_WITH_SEED_CBC_SHA
TLSv1.3 (server order)
 x1302   TLS_AES_256_GCM_SHA384            ECDH 256   AESGCM      256      TLS_AES_256_GCM_SHA384
 x1303   TLS_CHACHA20_POLY1305_SHA256      ECDH 256   ChaCha20    256      TLS_CHACHA20_POLY1305_SHA256
 x1301   TLS_AES_128_GCM_SHA256            ECDH 256   AESGCM      128      TLS_AES_128_GCM_SHA256


 Testing robust forward secrecy (FS) -- omitting Null Authentication/Encryption, 3DES, RC4

 FS is offered (OK)           TLS_AES_256_GCM_SHA384
                              TLS_CHACHA20_POLY1305_SHA256
                              ECDHE-RSA-AES256-GCM-SHA384
                              ECDHE-RSA-AES256-SHA384 ECDHE-RSA-AES256-SHA
                              DHE-RSA-AES256-GCM-SHA384 DHE-RSA-AES256-SHA256
                              DHE-RSA-AES256-SHA DHE-RSA-CAMELLIA256-SHA
                              TLS_AES_128_GCM_SHA256
                              ECDHE-RSA-AES128-GCM-SHA256
                              ECDHE-RSA-AES128-SHA256 ECDHE-RSA-AES128-SHA
                              DHE-RSA-AES128-GCM-SHA256 DHE-RSA-AES128-SHA256
                              DHE-RSA-AES128-SHA DHE-RSA-SEED-SHA
                              DHE-RSA-CAMELLIA128-SHA
 Elliptic curves offered:     prime256v1
 DH group offered:            Unknown DH group (2048 bits)

 Testing server defaults (Server Hello)

 TLS extensions (standard)    "renegotiation info/#65281"
                              "EC point formats/#11" "session ticket/#35"
                              "status request/#5" "next protocol/#13172"
                              "supported versions/#43" "key share/#51"
                              "max fragment length/#1"
                              "application layer protocol negotiation/#16"
                              "encrypt-then-mac/#22"
                              "extended master secret/#23"
 Session Ticket RFC 5077 hint 7200 seconds, session tickets keys seems to be rotated < daily
 SSL Session ID support       yes
 Session Resumption           Tickets no, ID: no
 TLS clock skew               Random values, no fingerprinting possible
 Certificate Compression      none
 Client Authentication        none
 Signature Algorithm          SHA256 with RSA
 Server key size              RSA 2048 bits (exponent is 65537)
 Server key usage             Digital Signature, Key Encipherment
 Server extended key usage    TLS Web Server Authentication, TLS Web Client Authentication
 Serial / Fingerprints        025216E1C4998E2632AA5D1DA985B43C / SHA1 A4C3D451DE3F534F7FA42E620AAD501B528940F5
                              SHA256 61E56F95929E3F4CFFDC250DC4D9C9BCEEDDD8D9C1886ACB84B45BF39B60C002
 Common Name (CN)             www.example.org
 subjectAltName (SAN)         www.example.org example.net example.edu
                              example.com example.org www.example.com
                              www.example.edu www.example.net
 Trust (hostname)             Ok via SAN (same w/o SNI)
 Chain of trust               Ok
 EV cert (experimental)       no
 Certificate Validity (UTC)   354 >= 60 days (2021-12-10 00:00 --> 2022-12-09 23:59)
 ETS/"eTLS", visibility info  not present
 Certificate Revocation List  http://crl3.digicert.com/DigiCertTLSRSASHA2562020CA1-4.crl
                              http://crl4.digicert.com/DigiCertTLSRSASHA2562020CA1-4.crl
 OCSP URI                     http://ocsp.digicert.com
 OCSP stapling                offered, not revoked
 OCSP must staple extension   --
 DNS CAA RR (experimental)    not offered
 Certificate Transparency     yes (certificate extension)
 Certificates provided        2
 Issuer                       DigiCert TLS RSA SHA256 2020 CA1 (DigiCert Inc from US)
 Intermediate cert validity   #1: ok > 40 days (2031-04-13 23:59). DigiCert TLS RSA SHA256 2020 CA1 <-- DigiCert Global Root CA
 Intermediate Bad OCSP (exp.) Ok


 Testing HTTP header response @ "/"

 HTTP Status Code             200 OK
 HTTP clock skew              0 sec from localtime
 Strict Transport Security    not offered
 Public Key Pinning           --
 Server banner                ECS (agb/5295)
 Application banner           --
 Cookie(s)                    (none issued at "/")
 Security headers             Cache-Control: max-age=604800
 Reverse Proxy banner         X-Cache: HIT


 Testing vulnerabilities

 Heartbleed (CVE-2014-0160)                not vulnerable (OK), no heartbeat extension
 CCS (CVE-2014-0224)                       not vulnerable (OK)
 Ticketbleed (CVE-2016-9244), experiment.  not vulnerable (OK)
 ROBOT                                     not vulnerable (OK)
 Secure Renegotiation (RFC 5746)           supported (OK)
 Secure Client-Initiated Renegotiation     not vulnerable (OK)
 CRIME, TLS (CVE-2012-4929)                not vulnerable (OK)
 BREACH (CVE-2013-3587)                    potentially NOT ok, "gzip deflate" HTTP compression detected. - only supplied "/" tested
                                           Can be ignored for static pages or if no secrets in the page
 POODLE, SSL (CVE-2014-3566)               not vulnerable (OK), no SSLv3 support
 TLS_FALLBACK_SCSV (RFC 7507)              Downgrade attack prevention supported (OK)
 SWEET32 (CVE-2016-2183, CVE-2016-6329)    not vulnerable (OK)
 FREAK (CVE-2015-0204)                     not vulnerable (OK)
 DROWN (CVE-2016-0800, CVE-2016-0703)      not vulnerable on this host and port (OK)
                                           make sure you don't use this certificate elsewhere with SSLv2 enabled services
                                           https://censys.io/ipv4?q=61E56F95929E3F4CFFDC250DC4D9C9BCEEDDD8D9C1886ACB84B45BF39B60C002 could help you to find out
 LOGJAM (CVE-2015-4000), experimental      not vulnerable (OK): no DH EXPORT ciphers, no common prime detected
 BEAST (CVE-2011-3389)                     TLS1: ECDHE-RSA-AES128-SHA
                                                 ECDHE-RSA-AES256-SHA
                                                 DHE-RSA-AES128-SHA
                                                 DHE-RSA-AES256-SHA
                                                 DHE-RSA-CAMELLIA256-SHA
                                                 DHE-RSA-CAMELLIA128-SHA
                                                 AES256-SHA CAMELLIA256-SHA
                                                 AES128-SHA CAMELLIA128-SHA
                                                 DHE-RSA-SEED-SHA SEED-SHA
                                           VULNERABLE -- but also supports higher protocols  TLSv1.1 TLSv1.2 (likely mitigated)
 LUCKY13 (CVE-2013-0169), experimental     potentially VULNERABLE, uses cipher block chaining (CBC) ciphers with TLS. Check patches
 Winshock (CVE-2014-6321), experimental    not vulnerable (OK)
 RC4 (CVE-2013-2566, CVE-2015-2808)        no RC4 ciphers detected (OK)


 Running client simulations (HTTP) via sockets

 Browser                      Protocol  Cipher Suite Name (OpenSSL)       Forward Secrecy
------------------------------------------------------------------------------------------------
 Android 4.4.2                TLSv1.2   ECDHE-RSA-AES128-GCM-SHA256       256 bit ECDH (P-256)
 Android 5.0.0                TLSv1.2   ECDHE-RSA-AES128-GCM-SHA256       256 bit ECDH (P-256)
 Android 6.0                  TLSv1.2   ECDHE-RSA-AES128-GCM-SHA256       256 bit ECDH (P-256)
 Android 7.0 (native)         TLSv1.2   ECDHE-RSA-AES128-GCM-SHA256       256 bit ECDH (P-256)
 Android 8.1 (native)         TLSv1.2   ECDHE-RSA-AES128-GCM-SHA256       256 bit ECDH (P-256)
 Android 9.0 (native)         TLSv1.3   TLS_AES_256_GCM_SHA384            256 bit ECDH (P-256)
 Android 10.0 (native)        TLSv1.3   TLS_AES_256_GCM_SHA384            256 bit ECDH (P-256)
 Chrome 74 (Win 10)           TLSv1.3   TLS_AES_256_GCM_SHA384            256 bit ECDH (P-256)
 Chrome 79 (Win 10)           TLSv1.3   TLS_AES_256_GCM_SHA384            256 bit ECDH (P-256)
 Firefox 66 (Win 8.1/10)      TLSv1.3   TLS_AES_256_GCM_SHA384            256 bit ECDH (P-256)
 Firefox 71 (Win 10)          TLSv1.3   TLS_AES_256_GCM_SHA384            256 bit ECDH (P-256)
 IE 6 XP                      No connection
 IE 8 Win 7                   TLSv1.0   ECDHE-RSA-AES128-SHA              256 bit ECDH (P-256)
 IE 8 XP                      No connection
 IE 11 Win 7                  TLSv1.2   DHE-RSA-AES128-GCM-SHA256         2048 bit DH
 IE 11 Win 8.1                TLSv1.2   DHE-RSA-AES128-GCM-SHA256         2048 bit DH
 IE 11 Win Phone 8.1          TLSv1.2   ECDHE-RSA-AES128-SHA256           256 bit ECDH (P-256)
 IE 11 Win 10                 TLSv1.2   ECDHE-RSA-AES128-GCM-SHA256       256 bit ECDH (P-256)
 Edge 15 Win 10               TLSv1.2   ECDHE-RSA-AES128-GCM-SHA256       256 bit ECDH (P-256)
 Edge 17 (Win 10)             TLSv1.2   ECDHE-RSA-AES128-GCM-SHA256       256 bit ECDH (P-256)
 Opera 66 (Win 10)            TLSv1.3   TLS_AES_256_GCM_SHA384            256 bit ECDH (P-256)
 Safari 9 iOS 9               TLSv1.2   ECDHE-RSA-AES128-GCM-SHA256       256 bit ECDH (P-256)
 Safari 9 OS X 10.11          TLSv1.2   ECDHE-RSA-AES128-GCM-SHA256       256 bit ECDH (P-256)
 Safari 10 OS X 10.12         TLSv1.2   ECDHE-RSA-AES128-GCM-SHA256       256 bit ECDH (P-256)
 Safari 12.1 (iOS 12.2)       TLSv1.3   TLS_AES_256_GCM_SHA384            256 bit ECDH (P-256)
 Safari 13.0 (macOS 10.14.6)  TLSv1.3   TLS_AES_256_GCM_SHA384            256 bit ECDH (P-256)
 Apple ATS 9 iOS 9            TLSv1.2   ECDHE-RSA-AES128-GCM-SHA256       256 bit ECDH (P-256)
 Java 6u45                    No connection
 Java 7u25                    TLSv1.0   ECDHE-RSA-AES128-SHA              256 bit ECDH (P-256)
 Java 8u161                   TLSv1.2   ECDHE-RSA-AES128-GCM-SHA256       256 bit ECDH (P-256)
 Java 11.0.2 (OpenJDK)        TLSv1.3   TLS_AES_256_GCM_SHA384            256 bit ECDH (P-256)
 Java 12.0.1 (OpenJDK)
TLSv1.3   TLS_AES_256_GCM_SHA384            256 bit ECDH (P-256)
 OpenSSL 1.0.2e               TLSv1.2   ECDHE-RSA-AES128-GCM-SHA256       256 bit ECDH (P-256)
 OpenSSL 1.1.0l (Debian)      TLSv1.2   ECDHE-RSA-AES128-GCM-SHA256       256 bit ECDH (P-256)
 OpenSSL 1.1.1d (Debian)      TLSv1.3   TLS_AES_256_GCM_SHA384            256 bit ECDH (P-256)
 Thunderbird (68.3)           TLSv1.3   TLS_AES_256_GCM_SHA384            256 bit ECDH (P-256)


 Rating (experimental)

 Rating specs (not complete)  SSL Labs's 'SSL Server Rating Guide' (version 2009q from 2020-01-30)
 Specification documentation  https://github.com/ssllabs/research/wiki/SSL-Server-Rating-Guide
 Protocol Support (weighted)  95 (28)
 Key Exchange     (weighted)  90 (27)
 Cipher Strength  (weighted)  90 (36)
 Final Score                  91
 Overall Grade                B
 Grade cap reasons            Grade capped to B. TLS 1.1 offered
                              Grade capped to B. TLS 1.0 offered
                              Grade capped to A. HSTS is not offered
```

### Generate JSON/CSV/HTML output [](https://djangocas.dev/blog/security/testssl-command-line-tool-check-server-tls-ssl-ciphers-vulnerabilities/#generate-jsoncsvhtml-output)

Use `--jsonfile`, `--csvfile` and `--htmlfile` to generate JSON, CSV and HTML output.

Example:

```sh
# Generate JSON output
docker run --rm -v `pwd`:/mnt drwetter/testssl.sh --jsonfile=/mnt/report.json https://www.example.com

# Generate CSV output
docker run --rm -v `pwd`:/mnt drwetter/testssl.sh --csvfile=/mnt/report.csv https://www.example.com

# Generate HTML output
docker run --rm -v `pwd`:/mnt drwetter/testssl.sh --htmlfile=/mnt/report.html https://www.example.com
```

You can also generate multiple report at the same time. For example, the follow command generate JSON, CSV and HTML outputs:

```sh
docker run --rm -v `pwd`:/mnt drwetter/testssl.sh --htmlfile=/mnt/report.html --jsonfile=/mnt/report.json --csvfile=/mnt/report.csv https://www.example.com
```

#### Note

By default, if the output file already exist, `testssl.sh` will not override it and command will fail with an error, like following error message:

```text
Fatal error: non-empty "/mnt/report.json" exists. Either use "--append" or (re)move it
```

In this case, you need rename exist output file or delete it.

### Test server default config[](https://djangocas.dev/blog/security/testssl-command-line-tool-check-server-tls-ssl-ciphers-vulnerabilities/#test-server-default-config)

Use `-S, --server-defaults` to displays the  [server](https://djangocas.dev/blog/security/testssl-command-line-tool-check-server-tls-ssl-ciphers-vulnerabilities/#)’s default picks and certificate info:

```sh
$ docker run --rm drwetter/testssl.sh -S https://www.example.com
...

 Testing server defaults (Server Hello)

 TLS extensions (standard)    "renegotiation info/#65281"
                              "EC point formats/#11" "session ticket/#35"
                              "status request/#5" "next protocol/#13172"
                              "supported versions/#43" "key share/#51"
                              "max fragment length/#1"
                              "application layer protocol negotiation/#16"
                              "encrypt-then-mac/#22"
                              "extended master secret/#23"
 Session Ticket RFC 5077 hint 7200 seconds, session tickets keys seems to be rotated < daily
 SSL Session ID support       yes
 Session Resumption           Tickets no, ID: no
 TLS clock skew               Random values, no fingerprinting possible
 Certificate Compression      none
 Client Authentication        none
 Signature Algorithm          SHA256 with RSA
 Server key size              RSA 2048 bits (exponent is 65537)
 Server key usage             Digital Signature, Key Encipherment
 Server extended key usage    TLS Web Server Authentication, TLS Web Client Authentication
 Serial / Fingerprints        025216E1C4998E2632AA5D1DA985B43C / SHA1 A4C3D451DE3F534F7FA42E620AAD501B528940F5
                              SHA256 61E56F95929E3F4CFFDC250DC4D9C9BCEEDDD8D9C1886ACB84B45BF39B60C002
 Common Name (CN)             www.example.org
 subjectAltName (SAN)         www.example.org example.net example.edu
                              example.com example.org www.example.com
                              www.example.edu www.example.net
 Trust (hostname)             Ok via SAN (same w/o SNI)
 Chain of trust               Ok
 EV cert (experimental)       no
 Certificate Validity (UTC)   354 >= 60 days (2021-12-10 00:00 --> 2022-12-09 23:59)
 ETS/"eTLS", visibility info  not present
 Certificate Revocation List  http://crl3.digicert.com/DigiCertTLSRSASHA2562020CA1-4.crl
                              http://crl4.digicert.com/DigiCertTLSRSASHA2562020CA1-4.crl
 OCSP URI                     http://ocsp.digicert.com
 OCSP stapling                offered, not revoked
 OCSP must staple extension   --
 DNS CAA RR (experimental)    not offered
 Certificate Transparency     yes (certificate extension)
 Certificates provided        2
 Issuer                       DigiCert TLS RSA SHA256 2020 CA1 (DigiCert Inc from US)
 Intermediate cert validity   #1: ok > 40 days (2031-04-13 23:59). DigiCert TLS RSA SHA256 2020 CA1 <-- DigiCert Global Root CA
 Intermediate Bad OCSP (exp.) Ok
```

### Test server prefer protocol+cipher suites[](https://djangocas.dev/blog/security/testssl-command-line-tool-check-server-tls-ssl-ciphers-vulnerabilities/#test-server-prefer-protocolcipher-suites)

Use `-P, --server-preference` to displays the server’s prefer protocol+cipher:

```sh
$ docker run --rm drwetter/testssl.sh --server-preference https://www.example.com
...
 Testing server's cipher preferences

 Has server cipher order?     yes (OK) -- TLS 1.3 and below
 Negotiated protocol          TLSv1.3
 Negotiated cipher            TLS_AES_256_GCM_SHA384, 256 bit ECDH (P-256)
 Cipher per protocol

Hexcode  Cipher Suite Name (OpenSSL)       KeyExch.   Encryption  Bits     Cipher Suite Name (IANA/RFC)
-----------------------------------------------------------------------------------------------------------------------------
SSLv2 (listed by strength)
 -
SSLv3 (server order)
 -
TLSv1 (server order)
 xc013   ECDHE-RSA-AES128-SHA              ECDH 256   AES         128      TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA
 xc014   ECDHE-RSA-AES256-SHA              ECDH 256   AES         256      TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA
 x33     DHE-RSA-AES128-SHA                DH 2048    AES         128      TLS_DHE_RSA_WITH_AES_128_CBC_SHA
 x39     DHE-RSA-AES256-SHA                DH 2048    AES         256      TLS_DHE_RSA_WITH_AES_256_CBC_SHA
 x88     DHE-RSA-CAMELLIA256-SHA           DH 2048    Camellia    256      TLS_DHE_RSA_WITH_CAMELLIA_256_CBC_SHA
 x45     DHE-RSA-CAMELLIA128-SHA           DH 2048    Camellia    128      TLS_DHE_RSA_WITH_CAMELLIA_128_CBC_SHA
 x35     AES256-SHA                        RSA        AES         256      TLS_RSA_WITH_AES_256_CBC_SHA
 x84     CAMELLIA256-SHA                   RSA        Camellia    256      TLS_RSA_WITH_CAMELLIA_256_CBC_SHA
 x2f     AES128-SHA                        RSA        AES         128      TLS_RSA_WITH_AES_128_CBC_SHA
 x41     CAMELLIA128-SHA                   RSA        Camellia    128      TLS_RSA_WITH_CAMELLIA_128_CBC_SHA
 x9a     DHE-RSA-SEED-SHA                  DH 2048    SEED        128      TLS_DHE_RSA_WITH_SEED_CBC_SHA
 x96     SEED-SHA                          RSA        SEED        128      TLS_RSA_WITH_SEED_CBC_SHA
TLSv1.1 (server order)
 xc013   ECDHE-RSA-AES128-SHA              ECDH 256   AES         128      TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA
 xc014   ECDHE-RSA-AES256-SHA              ECDH 256   AES         256      TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA
 x33     DHE-RSA-AES128-SHA                DH 2048    AES         128      TLS_DHE_RSA_WITH_AES_128_CBC_SHA
 x39     DHE-RSA-AES256-SHA                DH 2048    AES         256      TLS_DHE_RSA_WITH_AES_256_CBC_SHA
 x88     DHE-RSA-CAMELLIA256-SHA           DH 2048    Camellia    256      TLS_DHE_RSA_WITH_CAMELLIA_256_CBC_SHA
 x45     DHE-RSA-CAMELLIA128-SHA           DH 2048    Camellia    128      TLS_DHE_RSA_WITH_CAMELLIA_128_CBC_SHA
 x35     AES256-SHA                        RSA        AES         256      TLS_RSA_WITH_AES_256_CBC_SHA
 x84     CAMELLIA256-SHA                   RSA        Camellia    256      TLS_RSA_WITH_CAMELLIA_256_CBC_SHA
 x2f     AES128-SHA                        RSA        AES         128      TLS_RSA_WITH_AES_128_CBC_SHA
 x41     CAMELLIA128-SHA                   RSA        Camellia    128      TLS_RSA_WITH_CAMELLIA_128_CBC_SHA
 x9a     DHE-RSA-SEED-SHA                  DH 2048    SEED        128      TLS_DHE_RSA_WITH_SEED_CBC_SHA
 x96     SEED-SHA                          RSA        SEED        128      TLS_RSA_WITH_SEED_CBC_SHA
TLSv1.2 (server order)
 xc02f   ECDHE-RSA-AES128-GCM-SHA256       ECDH 256   AESGCM      128      TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256
 xc030   ECDHE-RSA-AES256-GCM-SHA384       ECDH 256   AESGCM      256      TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
 x9e     DHE-RSA-AES128-GCM-SHA256         DH 2048    AESGCM      128      TLS_DHE_RSA_WITH_AES_128_GCM_SHA256
 x9f     DHE-RSA-AES256-GCM-SHA384         DH 2048    AESGCM      256      TLS_DHE_RSA_WITH_AES_256_GCM_SHA384
 xc027   ECDHE-RSA-AES128-SHA256           ECDH 256   AES         128      TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256
 xc013   ECDHE-RSA-AES128-SHA              ECDH 256   AES         128      TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA
 xc028   ECDHE-RSA-AES256-SHA384           ECDH 256   AES         256      TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384
 xc014   ECDHE-RSA-AES256-SHA              ECDH 256   AES         256      TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA
 x67     DHE-RSA-AES128-SHA256             DH 2048    AES         128      TLS_DHE_RSA_WITH_AES_128_CBC_SHA256
 x33     DHE-RSA-AES128-SHA                DH 2048    AES         128      TLS_DHE_RSA_WITH_AES_128_CBC_SHA
 x6b     DHE-RSA-AES256-SHA256             DH 2048    AES         256      TLS_DHE_RSA_WITH_AES_256_CBC_SHA256
 x39     DHE-RSA-AES256-SHA                DH 2048    AES         256      TLS_DHE_RSA_WITH_AES_256_CBC_SHA
 x9c     AES128-GCM-SHA256                 RSA        AESGCM      128      TLS_RSA_WITH_AES_128_GCM_SHA256
 x88     DHE-RSA-CAMELLIA256-SHA           DH 2048    Camellia    256      TLS_DHE_RSA_WITH_CAMELLIA_256_CBC_SHA
 x45     DHE-RSA-CAMELLIA128-SHA           DH 2048    Camellia    128      TLS_DHE_RSA_WITH_CAMELLIA_128_CBC_SHA
 x35     AES256-SHA                        RSA        AES         256      TLS_RSA_WITH_AES_256_CBC_SHA
 x84     CAMELLIA256-SHA                   RSA        Camellia    256      TLS_RSA_WITH_CAMELLIA_256_CBC_SHA
 x2f     AES128-SHA                        RSA        AES         128      TLS_RSA_WITH_AES_128_CBC_SHA
 x41     CAMELLIA128-SHA                   RSA        Camellia    128      TLS_RSA_WITH_CAMELLIA_128_CBC_SHA
 x9a     DHE-RSA-SEED-SHA                  DH 2048    SEED        128      TLS_DHE_RSA_WITH_SEED_CBC_SHA
 x96     SEED-SHA                          RSA        SEED        128      TLS_RSA_WITH_SEED_CBC_SHA
TLSv1.3 (server order)
 x1302   TLS_AES_256_GCM_SHA384            ECDH 256   AESGCM      256      TLS_AES_256_GCM_SHA384
 x1303   TLS_CHACHA20_POLY1305_SHA256      ECDH 256   ChaCha20    256      TLS_CHACHA20_POLY1305_SHA256
 x1301   TLS_AES_128_GCM_SHA256            ECDH 256   AESGCM      128      TLS_AES_128_GCM_SHA256
```

## testssl.sh usage quick reference[](https://djangocas.dev/blog/security/testssl-command-line-tool-check-server-tls-ssl-ciphers-vulnerabilities/#testsslsh-usage-quick-reference)

Use `--help` to get all the available command line options:

```sh
$ docker run --rm  drwetter/testssl.sh --help

     "testssl.sh [options] <URI>"    or    "testssl.sh <options>"

"testssl.sh <option>", where <option> is mostly standalone and one of:

     --help                        what you're looking at
     -b, --banner                  displays banner + version of testssl.sh
     -v, --version                 same as previous
     -V, --local [pattern]         pretty print all local ciphers (of openssl only). If search pattern supplied: it is an
                                   an ignore case word pattern of cipher hexcode or any other string in its name, kx or bits

"testssl.sh [options] <URI>", where <URI> is:

     <URI>                         host|host:port|URL|URL:port   port 443 is default, URL can only contain HTTPS as a protocol

  and [options] is/are:

     -t, --starttls <protocol>     Does a run against a STARTTLS enabled service which is one of ftp, smtp, lmtp, pop3, imap,
                                   xmpp, xmpp-server, telnet, ldap, nntp, postgres, mysql
     --xmpphost <to_domain>        For STARTTLS xmpp or xmpp-server checks it supplies the domainname (like SNI)
     --mx <domain/host>            Tests MX records from high to low priority (STARTTLS, port 25)
     --file/-iL <fname>            Mass testing option: Reads one testssl.sh command line per line from <fname>.
                                   Can be combined with --serial or --parallel. Implicitly turns on "--warnings batch".
                                   Text format 1: Comments via # allowed, EOF signals end of <fname>
                                   Text format 2: nmap output in greppable format (-oG), 1 port per line allowed
     --mode <serial|parallel>      Mass testing to be done serial (default) or parallel (--parallel is shortcut for the latter)
     --warnings <batch|off>        "batch" doesn't continue when a testing error is encountered, off continues and skips warnings
     --connect-timeout <seconds>   useful to avoid hangers. Max <seconds> to wait for the TCP socket connect to return
     --openssl-timeout <seconds>   useful to avoid hangers. Max <seconds> to wait before openssl connect will be terminated

single check as <options>  ("testssl.sh URI" does everything except -E and -g):
     -e, --each-cipher             checks each local cipher remotely
     -E, --cipher-per-proto        checks those per protocol
     -s, --std, --categories       tests standard cipher categories by strength
     -f, --fs, --nsa               checks forward secrecy settings
     -p, --protocols               checks TLS/SSL protocols (including SPDY/HTTP2)
     -g, --grease                  tests several server implementation bugs like GREASE and size limitations
     -S, --server-defaults         displays the server's default picks and certificate info
     -P, --server-preference       displays the server's picks: protocol+cipher
     -x, --single-cipher <pattern> tests matched <pattern> of ciphers
                                   (if <pattern> not a number: word match)
     -c, --client-simulation       test client simulations, see which client negotiates with cipher and protocol
     -h, --header, --headers       tests HSTS, HPKP, server/app banner, security headers, cookie, reverse proxy, IPv4 address

     -U, --vulnerable              tests all (of the following) vulnerabilities (if applicable)
     -H, --heartbleed              tests for Heartbleed vulnerability
     -I, --ccs, --ccs-injection    tests for CCS injection vulnerability
     -T, --ticketbleed             tests for Ticketbleed vulnerability in BigIP loadbalancers
     --BB, --robot                 tests for Return of Bleichenbacher's Oracle Threat (ROBOT) vulnerability
     --SI, --starttls-injection    tests for STARTTLS injection issues
     -R, --renegotiation           tests for renegotiation vulnerabilities
     -C, --compression, --crime    tests for CRIME vulnerability (TLS compression issue)
     -B, --breach                  tests for BREACH vulnerability (HTTP compression issue)
     -O, --poodle                  tests for POODLE (SSL) vulnerability
     -Z, --tls-fallback            checks TLS_FALLBACK_SCSV mitigation
     -W, --sweet32                 tests 64 bit block ciphers (3DES, RC2 and IDEA): SWEET32 vulnerability
     -A, --beast                   tests for BEAST vulnerability
     -L, --lucky13                 tests for LUCKY13
     -WS, --winshock               tests for winshock vulnerability
     -F, --freak                   tests for FREAK vulnerability
     -J, --logjam                  tests for LOGJAM vulnerability
     -D, --drown                   tests for DROWN vulnerability
     -4, --rc4, --appelbaum        which RC4 ciphers are being offered?

tuning / connect options (most also can be preset via environment variables):
     --fast                        omits some checks: using openssl for all ciphers (-e), show only first preferred cipher.
     -9, --full                    includes tests for implementation bugs and cipher per protocol (could disappear)
     --bugs                        enables the "-bugs" option of s_client, needed e.g. for some buggy F5s
     --assume-http                 if protocol check fails it assumes HTTP protocol and enforces HTTP checks
     --ssl-native                  fallback to checks with OpenSSL where sockets are normally used
     --openssl <PATH>              use this openssl binary (default: look in $PATH, $RUN_DIR of testssl.sh)
     --proxy <host:port|auto>      (experimental) proxy connects via <host:port>, auto: values from $env ($http(s)_proxy)
     -6                            also use IPv6. Works only with supporting OpenSSL version and IPv6 connectivity
     --ip <ip>                     a) tests the supplied <ip> v4 or v6 address instead of resolving host(s) in URI
                                   b) arg "one" means: just test the first DNS returns (useful for multiple IPs)
     -n, --nodns <min|none>        if "none": do not try any DNS lookups, "min" queries A, AAAA and MX records
     --sneaky                      leave less traces in target logs: user agent, referer
     --user-agent <user agent>     set a custom user agent instead of the standard user agent
     --ids-friendly                skips a few vulnerability checks which may cause IDSs to block the scanning IP
     --phone-out                   allow to contact external servers for CRL download and querying OCSP responder
     --add-ca <CA files|CA dir>    path to <CAdir> with *.pem or a comma separated list of CA files to include in trust check
     --basicauth <user:pass>       provide HTTP basic auth information.
     --reqheader <header>          add custom http request headers

output options (can also be preset via environment variables):
     --quiet                       don't output the banner. By doing this you acknowledge usage terms normally appearing in the banner
     --wide                        wide output for tests like RC4, BEAST. FS also with hexcode, kx, strength, RFC name
     --show-each                   for wide outputs: display all ciphers tested -- not only succeeded ones
     --mapping <openssl|           openssl: use the OpenSSL cipher suite name as the primary name cipher suite name form (default)
                iana|rfc             -> use the IANA/(RFC) cipher suite name as the primary name cipher suite name form
                no-openssl|          -> don't display the OpenSSL cipher suite name, display IANA/(RFC) names only
                no-iana|no-rfc>      -> don't display the IANA/(RFC) cipher suite name, display OpenSSL names only
     --color <0|1|2|3>             0: no escape or other codes,  1: b/w escape codes,  2: color (default), 3: extra color (color all ciphers)
     --colorblind                  swap green and blue in the output
     --debug <0-6>                 1: screen output normal but keeps debug output in /tmp/.  2-6: see "grep -A 5 '^DEBUG=' testssl.sh"
     --disable-rating              Explicitly disables the rating output

file output options (can also be preset via environment variables)
     --log, --logging              logs stdout to '${NODE}-p${port}${YYYYMMDD-HHMM}.log' in current working directory (cwd)
     --logfile|-oL <logfile>       logs stdout to 'dir/${NODE}-p${port}${YYYYMMDD-HHMM}.log'. If 'logfile' is a dir or to a specified 'logfile'
     --json                        additional output of findings to flat JSON file '${NODE}-p${port}${YYYYMMDD-HHMM}.json' in cwd
     --jsonfile|-oj <jsonfile>     additional output to the specified flat JSON file or directory, similar to --logfile
     --json-pretty                 additional JSON structured output of findings to a file '${NODE}-p${port}${YYYYMMDD-HHMM}.json' in cwd
     --jsonfile-pretty|-oJ <jsonfile>  additional JSON structured output to the specified file or directory, similar to --logfile
     --csv                         additional output of findings to CSV file '${NODE}-p${port}${YYYYMMDD-HHMM}.csv' in cwd or directory
     --csvfile|-oC <csvfile>       additional output as CSV to the specified file or directory, similar to --logfile
     --html                        additional output as HTML to file '${NODE}-p${port}${YYYYMMDD-HHMM}.html'
     --htmlfile|-oH <htmlfile>     additional output as HTML to the specified file or directory, similar to --logfile
     --out(f,F)ile|-oa/-oA <fname> log to a LOG,JSON,CSV,HTML file (see nmap). -oA/-oa: pretty/flat JSON.
                                   "auto" uses '${NODE}-p${port}${YYYYMMDD-HHMM}'. If fname if a dir uses 'dir/${NODE}-p${port}${YYYYMMDD-HHMM}'
     --hints                       additional hints to findings
     --severity <severity>         severities with lower level will be filtered for CSV+JSON, possible values <LOW|MEDIUM|HIGH|CRITICAL>
     --append                      if (non-empty) <logfile>, <csvfile>, <jsonfile> or <htmlfile> exists, append to file. Omits any header
     --overwrite                   if <logfile>, <csvfile>, <jsonfile> or <htmlfile> exists it overwrites it without any warning
     --outprefix <fname_prefix>    before  '${NODE}.' above prepend <fname_prefix>


Options requiring a value can also be called with '=' e.g. testssl.sh -t=smtp --wide --openssl=/usr/bin/openssl <URI>.
<URI> always needs to be the last parameter.
```

### Related pages:

- [Jailbreak iPhone 8 iOS 16.2 with palera1n and use frida dump to decrypt ipa](https://djangocas.dev/blog/ios/iphone8-ios-jailbreak-palera1n-and-troubleshooting-common-issues/)
- [Use frida and objection to penetration test iOS app security](https://djangocas.dev/blog/use-frida-and-objection-to-penetration-test-ios-app-security/)
- [OpenSSL CSR Examples: Self Signed Certificate and How to Start Test TLS/SSL Server/Client](https://djangocas.dev/blog/openssl-tls-ssl-certificate-csr-s_server-s_client-examples/)
- [ECDSA signature verify in kotlin and Golang](https://djangocas.dev/blog/ecdsa-signature-verify-in-kotlin-and-go/)
- [Test TLS Connection Ciphers TLS Version and Certificate with OpenSSL Command Line](https://djangocas.dev/blog/test-tls-connectivity-with-openssl/)
- [Running a DoH Client to encrypt all home DNS traffic](https://djangocas.dev/blog/running-a-dns-over-https-doh-client-to-encrypt-all-home-dns-traffic/)
- [Secure Squid Proxy Server](https://djangocas.dev/blog/secure-squid-proxy-server/)

## References[](https://djangocas.dev/blog/security/testssl-command-line-tool-check-server-tls-ssl-ciphers-vulnerabilities/#references)

- [testssl.sh](https://testssl.sh/ "testssl.sh")
- [testssl.sh on github](https://github.com/drwetter/testssl.sh "testssl.sh on github")
- [Test TLS Connection Ciphers TLS Version and Certificate with OpenSSL Command Line](https://djangocas.dev/blog/test-tls-connectivity-with-openssl/ "Test TLS Connection Ciphers TLS Version and Certificate with OpenSSL Command Line")

**Credit:** This information was adapted from an excellent guide on [Djangocas.dev](https://djangocas.dev/blog/security/testssl-command-line-tool-check-server-tls-ssl-ciphers-vulnerabilities/). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/XXFzTOWIgq4?si=E6NTWP9UT-1Q6wCp&amp;start=360" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=XXFzTOWIgq4&t=225s). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/FKscrL9ICs4?si=8sMl_BC574W_QSJe" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=FKscrL9ICs4). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/hGrd4CqXw1U?si=yagVGU17hj6CDDEq&amp;start=40" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=hGrd4CqXw1U&t=43s). Be sure to check out the original post for more details.

