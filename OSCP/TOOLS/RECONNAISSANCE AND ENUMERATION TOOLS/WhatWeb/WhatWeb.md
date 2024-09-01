[![License](https://camo.githubusercontent.com/e4d12c419698f6804a7a3906c1a14a64e99130afad91a5079023e8feded3e45b/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f6c6963656e73652d47504c76322d627269676874677265656e2e737667)](https://raw.githubusercontent.com/urbanadventurer/whatweb/master/LICENSE) [![Stable Release](https://camo.githubusercontent.com/6a39468a68554cd300c4da4fd964e9610987dcea4de64d618486202297caa6ef/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f737461626c655f72656c656173652d302e352e352d626c75652e737667)](https://camo.githubusercontent.com/6a39468a68554cd300c4da4fd964e9610987dcea4de64d618486202297caa6ef/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f737461626c655f72656c656173652d302e352e352d626c75652e737667) [![WhatWeb Plugins](https://camo.githubusercontent.com/440f9b924763c2523bf5a17c98b5b3d3e8a1aed9acad77ed27fb501ba5e08a56/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f706c7567696e732d313832342d627269676874677265656e2e737667)](https://camo.githubusercontent.com/440f9b924763c2523bf5a17c98b5b3d3e8a1aed9acad77ed27fb501ba5e08a56/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f706c7567696e732d313832342d627269676874677265656e2e737667) [![Repositories](https://camo.githubusercontent.com/4d6babf7a745a6c582d5873f610cc90533055c64d46cf366591d2b262c95f087/68747470733a2f2f7265706f6c6f67792e6f72672f62616467652f74696e792d7265706f732f776861747765622e737667)](https://repology.org/project/whatweb/versions)

[![logo](https://camo.githubusercontent.com/5262988f0f88df6b327b6124493b2e13976cf869acca6c57b8457d9c4a24538e/68747470733a2f2f6d6f726e696e677374617273656375726974792e636f6d2f77702d636f6e74656e742f75706c6f6164732f323031392f30322f576861745765622d4c6f676f2d38303070782e706e67 "WhatWeb Logo")](https://camo.githubusercontent.com/5262988f0f88df6b327b6124493b2e13976cf869acca6c57b8457d9c4a24538e/68747470733a2f2f6d6f726e696e677374617273656375726974792e636f6d2f77702d636f6e74656e742f75706c6f6164732f323031392f30322f576861745765622d4c6f676f2d38303070782e706e67)

# WhatWeb - Next generation web scanner

[](https://github.com/urbanadventurer/WhatWeb#whatweb---next-generation-web-scanner)

Developed by Andrew Horton [urbanadventurer](https://github.com/urbanadventurer/) and Brendan Coles [bcoles](https://github.com/bcoles/)

Latest Release: v0.5.5. January 16, 2021

License: GPLv2

This product is subject to the terms detailed in the license agreement. For more information about WhatWeb visit:

Homepage: [https://morningstarsecurity.com/research/whatweb](https://morningstarsecurity.com/research/whatweb)

Wiki: [https://github.com/urbanadventurer/WhatWeb/wiki/](https://github.com/urbanadventurer/WhatWeb/wiki/)

If you have any questions, comments or concerns regarding WhatWeb, please consult the documentation prior to contacting one of the developers. Your feedback is always welcome.

## Contents

[](https://github.com/urbanadventurer/WhatWeb#contents)

- About WhatWeb
- Example Usage
- Usage
- Logging & Output
- Plugins
- Aggression
- Performance & Stability
- Optional Dependencies
- Writing Plugins
- Updates & Additional Information
- Release History
- Credits

## About WhatWeb

[](https://github.com/urbanadventurer/WhatWeb#about-whatweb)

WhatWeb identifies websites. Its goal is to answer the question, "What is that Website?". WhatWeb recognises web technologies including content management systems (CMS), blogging platforms, statistic/analytics packages, JavaScript libraries, web servers, and embedded devices. WhatWeb has over 1800 plugins, each to recognise something different. WhatWeb also identifies version numbers, email addresses, account IDs, web framework modules, SQL errors, and more.

WhatWeb can be stealthy and fast, or thorough but slow. WhatWeb supports an aggression level to control the trade off between speed and reliability. When you visit a website in your browser, the transaction includes many hints of what web technologies are powering that website. Sometimes a single webpage visit contains enough information to identify a website but when it does not, WhatWeb can interrogate the website further. The default level of aggression, called 'stealthy', is the fastest and requires only one HTTP request of a website. This is suitable for scanning public websites. More aggressive modes were developed for use in penetration tests.

Most WhatWeb plugins are thorough and recognise a range of cues from subtle to obvious. For example, most WordPress websites can be identified by the meta HTML tag, e.g. '', but a minority of WordPress websites remove this identifying tag but this does not thwart WhatWeb. The WordPress WhatWeb plugin has over 15 tests, which include checking the favicon, default installation files, login pages, and checking for "/wp-content/" within relative links.

### Features

[](https://github.com/urbanadventurer/WhatWeb#features)

- Over 1800 plugins
- Control the trade off between speed/stealth and reliability
- Performance tuning. Control how many websites to scan concurrently.
- Multiple log formats: Brief (greppable), Verbose (human readable), XML, JSON, MagicTree, RubyObject, MongoDB, ElasticSearch, SQL.
- Proxy support including TOR
- Custom HTTP headers
- Basic HTTP authentication
- Control over webpage redirection
- IP address ranges
- Fuzzy matching
- Result certainty awareness
- Custom plugins defined on the command line
- IDN (International Domain Name) support

## Example Usage

[](https://github.com/urbanadventurer/WhatWeb#example-usage)

Using WhatWeb to scan reddit.com.

```
$ ./whatweb reddit.com
http://reddit.com [301 Moved Permanently] Country[UNITED STATES][US], HTTPServer[snooserv], IP[151.101.65.140], RedirectLocation[https://www.reddit.com/], UncommonHeaders[retry-after,x-served-by,x-cache-hits,x-timer], Via-Proxy[1.1 varnish]
https://www.reddit.com/ [200 OK] Cookies[edgebucket,eu_cookie_v2,loid,rabt,rseor3,session_tracker,token], Country[UNITED STATES][US], Email[banner@2x.png,snoo-home@2x.png], Frame, HTML5, HTTPServer[snooserv], HttpOnly[token], IP[151.101.37.140], Open-Graph-Protocol[website], Script[text/javascript], Strict-Transport-Security[max-age=15552000; includeSubDomains; preload], Title[reddit: the front page of the internet], UncommonHeaders[fastly-restarts,x-served-by,x-cache-hits,x-timer], Via-Proxy[1.1 varnish], X-Frame-Options[SAMEORIGIN]
```

## Usage

[](https://github.com/urbanadventurer/WhatWeb#usage)

```

.$$$     $.                                   .$$$     $.         
$$$$     $$. .$$$  $$$ .$$$$$$.  .$$$$$$$$$$. $$$$     $$. .$$$$$$$. .$$$$$$. 
$ $$     $$$ $ $$  $$$ $ $$$$$$. $$$$$ $$$$$$ $ $$     $$$ $ $$   $$ $ $$$$$$.
$ `$     $$$ $ `$  $$$ $ `$  $$$ $$' $ `$ `$$ $ `$     $$$ $ `$      $ `$  $$$'
$. $     $$$ $. $$$$$$ $. $$$$$$ `$  $. $  :' $. $     $$$ $. $$$$   $. $$$$$.
$::$  .  $$$ $::$  $$$ $::$  $$$     $::$     $::$  .  $$$ $::$      $::$  $$$$
$;;$ $$$ $$$ $;;$  $$$ $;;$  $$$     $;;$     $;;$ $$$ $$$ $;;$      $;;$  $$$$
$$$$$$ $$$$$ $$$$  $$$ $$$$  $$$     $$$$     $$$$$$ $$$$$ $$$$$$$$$ $$$$$$$$$'

WhatWeb - Next generation web scanner version 0.5.5.
Developed by Andrew Horton (urbanadventurer) and Brendan Coles (bcoles)
Homepage: https://morningstarsecurity.com/research/whatweb

Usage: whatweb [options] <URLs>

TARGET SELECTION:
  <TARGETs>             Enter URLs, hostnames, IP addresses, filenames or
                        IP ranges in CIDR, x.x.x-x, or x.x.x.x-x.x.x.x
                        format.
  --input-file=FILE, -i Read targets from a file. You can pipe
                        hostnames or URLs directly with -i /dev/stdin.

TARGET MODIFICATION:
  --url-prefix          Add a prefix to target URLs.
  --url-suffix          Add a suffix to target URLs.
  --url-pattern         Insert the targets into a URL. Requires --input-file,
                        eg. www.example.com/%insert%/robots.txt 

AGGRESSION:
  The aggression level controls the trade-off between speed/stealth and
  reliability.
  --aggression, -a=LEVEL Set the aggression level. Default: 1.
  Aggression levels are:
  1. Stealthy   Makes one HTTP request per target. Also follows redirects.
  3. Aggressive If a level 1 plugin is matched, additional requests will be
      made.
  4. Heavy      Makes a lot of HTTP requests per target. Aggressive tests from
      all plugins are used for all URLs.

HTTP OPTIONS:
  --user-agent, -U=AGENT Identify as AGENT instead of WhatWeb/0.5.5.
  --header, -H          Add an HTTP header. eg "Foo:Bar". Specifying a default
                        header will replace it. Specifying an empty value, eg.
                        "User-Agent:" will remove the header.
  --follow-redirect=WHEN Control when to follow redirects. WHEN may be `never',
                        `http-only', `meta-only', `same-site', or `always'.
                        Default: always.
  --max-redirects=NUM   Maximum number of contiguous redirects. Default: 10.

AUTHENTICATION:
  --user, -u=<user:password> HTTP basic authentication.
  --cookie, -c=COOKIES  Provide cookies, e.g. 'name=value; name2=value2'.
  --cookiejar=FILE      Read cookies from a file.

PROXY:
  --proxy           <hostname[:port]> Set proxy hostname and port.
                    Default: 8080.
  --proxy-user      <username:password> Set proxy user and password.

PLUGINS:
  --list-plugins, -l            List all plugins.
  --info-plugins, -I=[SEARCH]   List all plugins with detailed information.
                                Optionally search with keywords in a comma
                                delimited list.
  --search-plugins=STRING       Search plugins for a keyword.
  --plugins, -p=LIST  Select plugins. LIST is a comma delimited set of 
                      selected plugins. Default is all.
                      Each element can be a directory, file or plugin name and
                      can optionally have a modifier, eg. + or -
                      Examples: +/tmp/moo.rb,+/tmp/foo.rb
                      title,md5,+./plugins-disabled/
                      ./plugins-disabled,-md5
                      -p + is a shortcut for -p +plugins-disabled.

  --grep, -g=STRING|REGEXP      Search for STRING or a Regular Expression. Shows 
                                only the results that match.
                                Examples: --grep "hello"
                                --grep "/he[l]*o/"
  --custom-plugin=DEFINITION\tDefine a custom plugin named Custom-Plugin,
  --custom-plugin=DEFINITION  Define a custom plugin named Custom-Plugin,
                        Examples: ":text=>'powered by abc'"
                        ":version=>/powered[ ]?by ab[0-9]/"
                        ":ghdb=>'intitle:abc \"powered by abc\"'"
                        ":md5=>'8666257030b94d3bdb46e05945f60b42'"
  --dorks=PLUGIN        List Google dorks for the selected plugin.

OUTPUT:
  --verbose, -v         Verbose output includes plugin descriptions. Use twice
                        for debugging.
  --colour,--color=WHEN control whether colour is used. WHEN may be `never',
                        `always', or `auto'.
  --quiet, -q           Do not display brief logging to STDOUT.
  --no-errors           Suppress error messages.

LOGGING:
  --log-brief=FILE        Log brief, one-line output.
  --log-verbose=FILE      Log verbose output.
  --log-errors=FILE       Log errors.
  --log-xml=FILE          Log XML format.
  --log-json=FILE         Log JSON format.
  --log-sql=FILE          Log SQL INSERT statements.
  --log-sql-create=FILE   Create SQL database tables.
  --log-json-verbose=FILE Log JSON Verbose format.
  --log-magictree=FILE    Log MagicTree XML format.
  --log-object=FILE       Log Ruby object inspection format.
  --log-mongo-database    Name of the MongoDB database.
  --log-mongo-collection  Name of the MongoDB collection. Default: whatweb.
  --log-mongo-host        MongoDB hostname or IP address. Default: 0.0.0.0.
  --log-mongo-username    MongoDB username. Default: nil.
  --log-mongo-password    MongoDB password. Default: nil.  
  --log-elastic-index     Name of the index to store results. Default: whatweb 
  --log-elastic-host      Host:port of the elastic http interface. Default: 127.0.0.1:9200
  
PERFORMANCE & STABILITY:
  --max-threads, -t       Number of simultaneous threads. Default: 25.
  --open-timeout          Time in seconds. Default: 15.
  --read-timeout          Time in seconds. Default: 30.
  --wait=SECONDS          Wait SECONDS between connections.
                          This is useful when using a single thread.

HELP & MISCELLANEOUS:
  --short-help            Short usage help.
  --help, -h              Complete usage help.
  --debug                 Raise errors in plugins.
  --version               Display version information. (WhatWeb 0.5.5).

EXAMPLE USAGE:
* Scan example.com.
  ./whatweb example.com
* Scan reddit.com slashdot.org with verbose plugin descriptions.
  ./whatweb -v reddit.com slashdot.org
* An aggressive scan of wired.com detects the exact version of WordPress.
  ./whatweb -a 3 www.wired.com
* Scan the local network quickly and suppress errors.
  whatweb --no-errors 192.168.0.0/24
* Scan the local network for https websites.
  whatweb --no-errors --url-prefix https:// 192.168.0.0/24
* Scan for crossdomain policies in the Alexa Top 1000.
  ./whatweb -i plugin-development/alexa-top-100.txt \
  --url-suffix /crossdomain.xml -p crossdomain_xml

```

## Logging & Output

[](https://github.com/urbanadventurer/WhatWeb#logging--output)

The following types of logging are supported:

- --log-brief=FILE Brief, one-line, greppable format
- --log-verbose=FILE Verbose
- --log-xml=FILE XML format. XSL stylesheet is provided
- --log-json=FILE JSON format
- --log-json-verbose=FILE JSON verbose format
- --log-magictree=FILE MagicTree XML format
- --log-object=FILE Ruby object inspection format
- --log-mongo-database Name of the MongoDB database
- --log-mongo-collection Name of the MongoDB collection. Default: whatweb
- --log-mongo-host MongoDB hostname or IP address. Default: 0.0.0.0
- --log-mongo-username MongoDB username. Default: nil
- --log-mongo-password MongoDB password. Default: nil
- --log-elastic-index Name of the index to store results. Default: whatweb
- --log-elastic-host Host:port of the elastic http interface. Default: 127.0.0.1:9200
- --log-errors=FILE Log errors. This is usually printed to the screen in red.

You can output to multiple logs simultaneously by specifying multiple command line logging options. Advanced users who want SQL output should read the source code to see unsupported features.

## Plugins

[](https://github.com/urbanadventurer/WhatWeb#plugins)

Matches are made with:

- Text strings (case sensitive)
- Regular expressions
- Google Hack Database queries (limited set of keywords)
- MD5 hashes
- URL recognition
- HTML tag patterns
- Custom ruby code for passive and aggressive operations

To list the plugins supported:

```
$ ./whatweb -l
```

### WhatWeb Plugin List

[](https://github.com/urbanadventurer/WhatWeb#whatweb-plugin-list)

```
Plugin Name - Description
--------------------------------------------------------------------------------
1024-CMS - 1024 is one of a few CMS's leading the way with the implementation...
360-Web-Manager - 360-Web-Manager
3COM-NBX - 3COM NBX phone system. The NBX NetSet utility is a web interface i...
3dcart - 3dcart - The 3dcart Shopping Cart Software is a complete ecommerce s...
4D - 4D web application deployment server
4images - 4images is a powerful web-based image gallery management system. Fe...
... (truncated)
```

### Search Plugins

[](https://github.com/urbanadventurer/WhatWeb#search-plugins)

To view more detail about a plugin or search plugins for a keyword:

```
$ ./whatweb -I phpBB

WhatWeb Detailed Plugin List
Searching for phpBB
================================================================================
Plugin:         phpBB
--------------------------------------------------------------------------------
Description:    phpBB is a free forum 
Website:        http://phpbb.org/

Author:         Andrew Horton
Version:        0.3

Features:       [Yes]  Pattern Matching (7)
                [Yes]  Version detection from pattern matching
                [Yes]  Function for passive matches
                [Yes]  Function for aggressive matches
                [Yes]  Google Dorks (1)

Google Dorks:
[1] "Powered by phpBB"
================================================================================
```

### Plugin Selection

[](https://github.com/urbanadventurer/WhatWeb#plugin-selection)

All plugins are loaded by default.

Plugins can be selected by directories, files or plugin names as a comma delimited list with the -p or --plugin command line option.

Each list item may have a modifier: + adds to the full set, - removes from the full set and no modifier overrides the defaults.

### Examples

[](https://github.com/urbanadventurer/WhatWeb#examples)

- --plugins +plugins-disabled,-foobar
- --plugins +/tmp/moo.rb
- --plugins foobar (only select foobar)
- -p title,md5,+./plugins-disabled/
- -p ./plugins-disabled,-md5

The --dorks command line option returns google dorks for the selected plugin. For example, --dorks wordpress returns "is proudly powered by WordPress"

The --grep, -g command line option searches the target page for the selected string and returns a match in a plugin called Grep if it is found.

## Aggression

[](https://github.com/urbanadventurer/WhatWeb#aggression)

WhatWeb features several levels of aggression. By default the aggression level is set to 1 (stealthy) which sends a single HTTP GET request and also follows redirects.

```
--aggression, -a

  1. Stealthy Makes one HTTP request per target. Also follows redirects.
    2. Unused
    3. Aggressive Can make a handful of HTTP requests per target. This triggers
        aggressive plugins for targets only when those plugins are
        identified with a level 1 request first.
  4. Heavy  Makes a lot of HTTP requests per target. Aggressive tests from
        all plugins are used for all URLs.
```

Level 3 aggressive plugins will guess more URLs and perform actions that are potentially unsuitable without permission. WhatWeb currently does not support any intrusion/exploit level tests in plugins.

### An example of the different results between level 1 and level 3:

[](https://github.com/urbanadventurer/WhatWeb#an-example-of-the-different-results-between-level-1-and-level-3)

A level 1, stealthy scan identifies that smartor.is-root.com/forum/ uses phpBB version 2:

```
$ ./whatweb smartor.is-root.com/forum/
http://smartor.is-root.com/forum/ [200] PasswordField[password], HTTPServer[Apache/2.2.15], PoweredBy[phpBB], Apache[2.2.15], IP[88.198.177.36], phpBB[2], PHP[5.2.13], X-Powered-By[PHP/5.2.13], Cookies[phpbb2mysql_data,phpbb2mysql_sid], Title[Smartors Mods Forums - Reloaded], Country[GERMANY][DE]
```

A level 3, aggressive scan triggers additional tests in the phpBB plugin which identifies that the website uses phpBB version 2.0.20 or higher:

```
$ ./whatweb -p plugins/phpbb.rb -a 3 smartor.is-root.com/forum/
http://smartor.is-root.com/forum/ [200] phpBB[2,>2.0.20]
```

Note the use of the -p argument to select only the phpBB plugin. It is advisable, but not mandatory, to select a specific plugin when attempting to fingerprint software versions in aggressive mode. This approach is far more stealthy as it will limit the number of requests.

WhatWeb has no caching so if you use aggressive plugins on redirecting URLs you may fetch the same files multiple times.

## Performance & Stability

[](https://github.com/urbanadventurer/WhatWeb#performance--stability)

WhatWeb features several options to increase performance and stability.

- --max-threads, -t Number of simultaneous threads. Default: 25.
- --open-timeout Time in seconds. Default: 15
- --read-timeout Time in seconds. Default: 30
- --wait=SECONDS Wait SECONDS between connections This is useful when using a single thread.

The --wait and --max-threads commands can be used to assist in IDS evasion.

Changing the user-agent using the -U or --user-agent command line option will avoid the Snort IDS rule for WhatWeb.

If you are scanning ranges of IP addresses, it is much more efficient to use a port scanner like massscan to discover which have port 80 open before scanning with WhatWeb.

Character set detection, with the Charset plugin dramatically decreases performance by requiring more CPU. This is required by JSON and MongoDB logging.

## Optional Dependencies

[](https://github.com/urbanadventurer/WhatWeb#optional-dependencies)

To enable MongoDB logging install the mongo gem. gem install mongo

To enable character set detection and MongoDB logging install the rchardet gem. gem install rchardet cp plugins-disabled/charset.rb my-plugins/

## Writing Plugins

[](https://github.com/urbanadventurer/WhatWeb#writing-plugins)

Plugins are easy to write. Start by going through the plugin tutorials in the _my-plugins/_ folder.

- [Plugin Tutorials](https://github.com/urbanadventurer/WhatWeb/tree/master/my-plugins).

An overview of the plugin tutorials is here. [plugin-tutorials.txt](https://github.com/urbanadventurer/WhatWeb/tree/master/plugin-development/plugin-tutorials.txt)

After progressing through the tutorials read through the Development section of the [wiki](https://github.com/urbanadventurer/WhatWeb/wiki/).

- [Sources for Plugin Writing](https://github.com/urbanadventurer/WhatWeb/wiki/Sources-for-Plugin-Writing)
- [How to Develop WhatWeb Plugins (not up to date)](https://github.com/urbanadventurer/WhatWeb/wiki/How-to-develop-WhatWeb-plugins)

## Updates & Additional Information

[](https://github.com/urbanadventurer/WhatWeb#updates--additional-information)

The WhatWeb development build features regular updates.

- Check the development branches for unreleased updates.

Browse the wiki for more documentation and advanced usage techniques.

- Wiki: [https://github.com/urbanadventurer/WhatWeb/wiki/](https://github.com/urbanadventurer/WhatWeb/wiki/)

## Release History

[](https://github.com/urbanadventurer/WhatWeb#release-history)

- Version 0.5.5 Released January 16th, 2021
- Version 0.5.4 Released December 14th, 2020
- Version 0.5.3 Released October 1st, 2020
- Version 0.5.2 Released June 9th, 2020
- Version 0.5.1 Released Feburary 25th, 2020
- Version 0.5.0 Released June 9th, 2019
- Version 0.4.9 Released November 23rd, 2017
- Version 0.4.8-dev (Continuous release from 2012 to 2017)
- Version 0.4.7 Released April 5th, 2011
- Version 0.4.6 Released March 25th, 2011
- Version 0.4.5 Released August 17th, 2010
- Version 0.4.4 Released June 29th, 2010
- Version 0.4.3 Released May 24th, 2010
- Version 0.4.2 Released April 30th, 2010
- Version 0.4.1 Released April 28th, 2010
- Version 0.4 Released March 14th, 2010
- Version 0.3 Released at Kiwicon III (kiwicon.org), November 2nd, 2009

## Credits

[](https://github.com/urbanadventurer/WhatWeb#credits)

### Developers

[](https://github.com/urbanadventurer/WhatWeb#developers)

- Andrew Horton (@urbanadventurer)
- Brendan Coles (@bcoles)

### Contributors

[](https://github.com/urbanadventurer/WhatWeb#contributors)

Thank you to the following people who have contributed to WhatWeb.

- Emilio Casbas
- Louis Nyffenegger
- Patrik Wallström (@pawal)
- Caleb Anderson (@dirtyfilthy)
- Tonmoy Saikia
- Aung Khant (@yehgdotnet)
- Erik Inge Bolsø
- [nk@dsigned.gr](mailto:nk@dsigned.gr)
- Steve Milner (@ashcrow)
- Michal Ambroz
- Gremwell
- Sagar Prakash Junnarkar (@sagarjunnarkar)
- GertBerger
- Quintin Poirier
- Eric Sesterhenn
- dengjw (@jawa)
- Pedro Worcel (@droop)
- Matthieu Keller (@maggick)
- Peter (2pvdl)
- Napz (@RootCon)
- @nilx042
- Fabian Affolter (@fabaff)
- Andrew Silvernail (@buff3r)
- Andre Ricardo (@andrericardo)
- nikosk
- Patrick Thomas (@coffeetocode)
- Guillaume Delcaour (@guikcd)
- Sean (@wiifm69)
- Matthieu Keller (@maggick)
- Raul (@raurodse)
- Andrew Petro (@apetro)
- Artem Taranyuk (@610)
- Matti Paksula (@matti)
- Tim Smith (@tas50)
- Sarthak Munshi (@saru95)
- @rdubourguais
- @SlivTaMere
- @Code0x58
- @iGeek098
- @andreas-becker
- @csalazar
- @golewski
- @Allactaga
- @lins05
- @eliasdorneles
- @sigit
- dewanto
- @elcodigok
- @SlivTaMere
- @anozoozian
- Bhavin Senjaliya (@bhavin1223)
- Janosch Maier (@Phylu)
- @rmaksimov
- Naglis Jonaitis (@naglis)
- Igor Rzegocki (@ajgon)
- Melvil Guillaume (@mguillau42)
- @LrsK
- Janosch Maier (@phylu)
- @abenson
- @blshkv
- Weidsom Nascimento (@weidsom)
- Marcelo Gimenes @cgimenes
- @xambroz
- Baptiste Fontaine (@bfontaine)
- @juananpe
- @definity
- @huntertl
- Max Davitt (@themaxdavitt)
- Gregory Boddin (@gboddin)

It is difficult to keep track of all the people who have contributed to WhatWeb. If your name is missing then please let me know.

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/urbanadventurer/WhatWeb). Be sure to check out the original post for more details.

# WhatWeb!?

Hello everyone, hope you all are good. So, today’s Topic is A Tool of Kali Linux Named Whatweb!

![](https://miro.medium.com/v2/resize:fit:698/1*CHU4aDUPxVjPDfjUYET9Kw.png)

When it comes to bug bounty, Web pen testing, Web security or web hacking, we should know what technology is being used in the website, what is its version, Which CMS (Content Management System) is present, Which web framework being used on the website other information about the web server and Which web security and firewall is being used, all this can be easily found out through the Whatweb tool.

This tool is useful for us in foot printing of a website, so today we will learn how to do foot printing of a website with Whatweb.

## Installing Process:

We get whatweb pre-installed in Kali, but if not then you can install it by typing simple commands in the terminal.

![](https://miro.medium.com/v2/resize:fit:700/1*jBdGAXgmh7AvARZ1HOYoVQ.png)

Sudo git clone https://github.com/urbanadventurer/WhatWeb.git

> Credit: Developed by Andrew Horton (urbanadventurer) and Brendan Coles (bcoles).

No matter how familiar we are with any Kali Linux tool, first of all we check it with man or — help command, we will get all the details about that tool.

In Whatweb tool we have 2–3 methods to search the target website.

- When you just want to search by URL:

**Command:** _Whatweb [ URL ]_

![](https://miro.medium.com/v2/resize:fit:700/1*kj-WPckHp9j8sGhQTg359g.png)

- When you want to search only by Ip address:

**Command:** _Whatweb [ Ip address]_

![](https://miro.medium.com/v2/resize:fit:700/1*sHLq7nDZO5Fv3Ri1v76YuA.png)

- When we have to search many websites at once, then we can write them all in a text file and provide the path of that text file, through which we will get information about all the websites simultaneously.

Command: _Whatweb [filename]_

![](https://miro.medium.com/v2/resize:fit:700/1*WYc3uNyPEBLDtLFMLWIZ3w.png)

**We have three scans in Aggression, which give us the output we need.**

1. **Stealthy scan**

![](https://miro.medium.com/v2/resize:fit:700/1*WYc3uNyPEBLDtLFMLWIZ3w.png)

The output of stealthy scan is fast, it sends a single HTTP GET request, but sometimes it misses some details.

**2. Aggressive scan:** This level makes a few more HTTP requests than Level 1 and triggers more intensive checks only for targets identified during the initial scan.

**3. Heavy scan:** This scan is a very comprehensive scan and it is also very slow. It also generates a lot of traffic on the network.

WhatWeb Tools gives us the option to customize the user agent string while footprinting a website.

![](https://miro.medium.com/v2/resize:fit:700/1*dh59bqJV8bdYfQzoRGHuEg.png)

**_— max-redirects=NUM_** (Maximum number of redirects. Default: 10.)

![](https://miro.medium.com/v2/resize:fit:700/1*DavLc8BIduk87PJ2KrYGvw.png)

— With **_proxy_** flag we can test any website with anonymity and we can do it through proxy server.

![](https://miro.medium.com/v2/resize:fit:700/1*e700WLSO0JScXeoKvhHAew.png)

Some important commands which are important for us to know, and which are there just by their name, we can know what work this command does.

1. **-l** list all plugins.
2. **— wait=SECONDS:** Wait SECONDS between connections.
3. **-v:** Verbose output.
4. **— no-errors:** Suppress error messages.
5. **— version:** Display version information.

## Conclusion:

whatweb is an open-source project which helps us during website footprinting. From whatweb we can know what technology is being used in the frontend and backend of the website, which CMS (content management system) is present in it, which header the website is returning, we can get all this information very easily from whatweb, Whatweb helps us during reconnaissance. It comes with more than 1800 plugins, with whatweb we can use Tor proxy so that our anonymity can be maintained, we can scan the entire IP block simultaneously, whatweb is very good in cyber security, its user interface is very friendly so that no beginner faces any problem in using it and whatweb is a powerful versatile tool.

**Credit:** This information was adapted from an excellent guide on [Medium](https://thehackersmeetup.medium.com/whatweb-c132eb13927c). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/IotOcJkSSvo?si=aQevNEiJtwa6begZ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=IotOcJkSSvo). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/4hfO8NZgbc4?si=e792KwAss-Dh_8kV&amp;start=398" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=4hfO8NZgbc4). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/VB7xhOIxzXI?si=lA0oVuILfU8lh7hd" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=VB7xhOIxzXI). Be sure to check out the original post for more details.




