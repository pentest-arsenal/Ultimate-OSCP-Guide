[![](https://github.com/xmendez/wfuzz/raw/master/docs/_static/logo/wfuzz_letters.svg)](https://github.com/xmendez/wfuzz/blob/master/docs/_static/logo/wfuzz_letters.svg)

[![Build Status](https://camo.githubusercontent.com/4670f846c47ff58b0045d9064e04454d8f0f7eb2d2e08f3903352b6522736d2e/68747470733a2f2f7472617669732d63692e6f72672f786d656e64657a2f7766757a7a2e7376673f6272616e63683d6d6173746572)](https://travis-ci.org/xmendez/wfuzz) [![](https://camo.githubusercontent.com/086b8ae9707b97b8e808f11fcbbbad4690d895beb4b3e5daf7894c95d0513b14/68747470733a2f2f696d672e736869656c64732e696f2f707970692f762f7766757a7a2e737667)](https://pypi.python.org/pypi/wfuzz) [![](https://camo.githubusercontent.com/61d8a37cf6b4c664d59c65377dec0be5847d4a31bfeaa3520c2b05ac266ddbec/68747470733a2f2f696d672e736869656c64732e696f2f707970692f646d2f7766757a7a)](https://pypi.python.org/pypi/wfuzz) [![](https://camo.githubusercontent.com/d1753523cb4b5e31223fb2a9d7ec33ca3cfe33e651679dfe7f00840f37d96e17/68747470733a2f2f696d672e736869656c64732e696f2f707970692f707976657273696f6e732f7766757a7a2e737667)](https://pypi.python.org/pypi/wfuzz) [![](https://camo.githubusercontent.com/2efbd729c50e0b74c4284f2801bca3a324b297ac8018d630ab1ccba59f83b095/68747470733a2f2f636f6465636f762e696f2f6769746875622f786d656e64657a2f7766757a7a2f636f7665726167652e7376673f6272616e63683d6d6173746572)](https://codecov.io/github/xmendez/wfuzz)

# Wfuzz - The Web Fuzzer

[](https://github.com/xmendez/wfuzz#wfuzz---the-web-fuzzer)

Wfuzz has been created to facilitate the task in web applications assessments and it is based on a simple concept: it replaces any reference to the FUZZ keyword by the value of a given payload.

A payload in Wfuzz is a source of data.

This simple concept allows any input to be injected in any field of an HTTP request, allowing to perform complex web security attacks in different web application components such as: parameters, authentication, forms, directories/files, headers, etc.

Wfuzz is more than a web content scanner:

- Wfuzz could help you to secure your web applications by finding and exploiting web application vulnerabilities. Wfuzz’s web application vulnerability scanner is supported by plugins.
    
- Wfuzz is a completely modular framework and makes it easy for even the newest of Python developers to contribute. Building plugins is simple and takes little more than a few minutes.
    
- Wfuzz exposes a simple language interface to the previous HTTP requests/responses performed using Wfuzz or other tools, such as Burp. This allows you to perform manual and semi-automatic tests with full context and understanding of your actions, without relying on a web application scanner underlying implementation.
    

It was created to facilitate the task in web applications assessments, it's a tool by pentesters for pentesters ;)

## Installation

[](https://github.com/xmendez/wfuzz#installation)

To install WFuzz, simply use pip:

```
pip install wfuzz
```

To run Wfuzz from a docker image, run:

```
$ docker run -v $(pwd)/wordlist:/wordlist/ -it ghcr.io/xmendez/wfuzz wfuzz
```

## Documentation

[](https://github.com/xmendez/wfuzz#documentation)

Documentation is available at [http://wfuzz.readthedocs.io](http://wfuzz.readthedocs.io/)

## Download

[](https://github.com/xmendez/wfuzz#download)

Check github releases. Latest is available at [https://github.com/xmendez/wfuzz/releases/latest](https://github.com/xmendez/wfuzz/releases/latest)

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/xmendez/wfuzz). Be sure to check out the original post for more details.

# Wfuzz: The Web fuzzer[](https://wfuzz.readthedocs.io/en/latest/#wfuzz-the-web-fuzzer "Permalink to this headline")

Wfuzz provides a framework to automate web applications security assessments and could help you to secure your web applications by finding and exploiting web application vulnerabilities.

## See Wfuzz in action[](https://wfuzz.readthedocs.io/en/latest/#see-wfuzz-in-action "Permalink to this headline")

- Wfuzz cli:
    
    $ wfuzz -w wordlist/general/common.txt --hc 404 http://testphp.vulnweb.com/FUZZ
    ********************************************************
    * Wfuzz 2.2 - The Web Bruteforcer                      *
    ********************************************************
    
    Target: http://testphp.vulnweb.com/FUZZ
    Total requests: 950
    
    ==================================================================
    ID      Response   Lines      Word         Chars          Request
    ==================================================================
    
    00022:  C=301      7 L        12 W          184 Ch        "admin"
    00130:  C=403     10 L        29 W          263 Ch        "cgi-bin"
    00378:  C=301      7 L        12 W          184 Ch        "images"
    00690:  C=301      7 L        12 W          184 Ch        "secured"
    00938:  C=301      7 L        12 W          184 Ch        "CVS"
    
    Total time: 5.519253
    Processed Requests: 950
    Filtered Requests: 945
    Requests/sec.: 172.1247
    
- Wfuzz library:
    
    >>> import wfuzz
    >>> for r in wfuzz.get_payload(range(100)).fuzz(hl=[97], url="http://testphp.vulnweb.com/listproducts.php?cat=FUZZ"):
    ...     print r
    ...
    00125:  C=200    102 L       434 W         7011 Ch        "1"
    00126:  C=200     99 L       302 W         4442 Ch        "2"
    

other tools included in the wfuzz framework.

- Wfuzz payload generator:
    
    $ wfpayload -z range,0-10
    0
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    
- Wfuzz encoder/decoder:
    
    $ wfencode -e md5 test
    098f6bcd4621d373cade4e832627b4f6
    
- You can also run wfuzz from the official docker image:
    
    $ docker run -v $(pwd)/wordlist:/wordlist/ -it ghcr.io/xmendez/wfuzz wfuzz
    ********************************************************
    * Wfuzz 3.0.3 - The Web Fuzzer                         *
    *                                                      *
    * Version up to 1.4c coded by:                         *
    * Christian Martorella (cmartorella@edge-security.com) *
    * Carlos del ojo (deepbit@gmail.com)                   *
    *                                                      *
    * Version 1.4d to 3.0.3 coded by:                      *
    * Xavier Mendez (xmendez@edge-security.com)            *
    ********************************************************
    
    Usage:  wfuzz [options] -z payload,params <url>
    
            FUZZ, ..., FUZnZ  wherever you put these keywords wfuzz will replace them with the values of the specified payload.
            FUZZ{baseline_value} FUZZ will be replaced by baseline_value. It will be the first request performed and could be used as a base for filtering.
    
    
    Examples:
            wfuzz -c -z file,users.txt -z file,pass.txt --sc 200 http://www.site.com/log.asp?user=FUZZ&pass=FUZ2Z
            wfuzz -c -z range,1-10 --hc=BBB http://www.site.com/FUZZ{something not there}
            wfuzz --script=robots -z list,robots.txt http://www.webscantest.com/FUZZ
    
    Type wfuzz -h for further information or --help for advanced usage.
    

## How it works[](https://wfuzz.readthedocs.io/en/latest/#how-it-works "Permalink to this headline")

Wfuzz it is based on a simple concept: it replaces any reference to the FUZZ keyword by the value of a given payload.

A payload in Wfuzz is a source of data.

This simple concept allows any input to be injected in any field of an HTTP request, allowing to perform complex web security attacks in different web application components such as: parameters, authentication, forms, directories/files, headers, etc.

Wfuzz is more than a web brute forcer:

- Wfuzz’s web application vulnerability scanner is supported by plugins.
- Wfuzz is a completely modular framework and makes it easy for even the newest of Python developers to contribute. Building plugins is simple and takes little more than a few minutes.
- Wfuzz exposes a simple language interface to the previous HTTP requests/responses performed using Wfuzz or other tools, such as Burp. This allows you to perform manual and semi-automatic tests with full context and understanding of your actions, without relying on a web application scanner underlying implementation.

# Installation Guide[](https://wfuzz.readthedocs.io/en/latest/#installation-guide "Permalink to this headline")

- [Installation](https://wfuzz.readthedocs.io/en/latest/user/installation.html)
    - [Pip install Wfuzz](https://wfuzz.readthedocs.io/en/latest/user/installation.html#pip-install-wfuzz)
    - [Use the wfuzz docker image](https://wfuzz.readthedocs.io/en/latest/user/installation.html#use-the-wfuzz-docker-image)
    - [Get the Source Code](https://wfuzz.readthedocs.io/en/latest/user/installation.html#get-the-source-code)
    - [Dependencies](https://wfuzz.readthedocs.io/en/latest/user/installation.html#dependencies)
- [Installation issues](https://wfuzz.readthedocs.io/en/latest/user/installation.html#installation-issues)
    - [Pycurl on MacOS](https://wfuzz.readthedocs.io/en/latest/user/installation.html#pycurl-on-macos)
    - [Pycurl on Windows](https://wfuzz.readthedocs.io/en/latest/user/installation.html#pycurl-on-windows)
    - [PyCurl SSL bug](https://wfuzz.readthedocs.io/en/latest/user/installation.html#pycurl-ssl-bug)
        - [Verifying the problem](https://wfuzz.readthedocs.io/en/latest/user/installation.html#verifying-the-problem)
        - [Installing pycurl openssl flavour](https://wfuzz.readthedocs.io/en/latest/user/installation.html#installing-pycurl-openssl-flavour)
        - [Installing pycurl against openssl](https://wfuzz.readthedocs.io/en/latest/user/installation.html#installing-pycurl-against-openssl)
- [Breaking changes](https://wfuzz.readthedocs.io/en/latest/user/breaking.html)

# User Guide[](https://wfuzz.readthedocs.io/en/latest/#user-guide "Permalink to this headline")

- [Getting Started](https://wfuzz.readthedocs.io/en/latest/user/getting.html)
    - [Getting help](https://wfuzz.readthedocs.io/en/latest/user/getting.html#getting-help)
    - [Payloads](https://wfuzz.readthedocs.io/en/latest/user/getting.html#payloads)
        - [Specifying a payload:](https://wfuzz.readthedocs.io/en/latest/user/getting.html#specifying-a-payload)
        - [Multiple payloads](https://wfuzz.readthedocs.io/en/latest/user/getting.html#multiple-payloads)
    - [Filters](https://wfuzz.readthedocs.io/en/latest/user/getting.html#filters)
        - [Hiding responses](https://wfuzz.readthedocs.io/en/latest/user/getting.html#hiding-responses)
        - [Showing responses](https://wfuzz.readthedocs.io/en/latest/user/getting.html#showing-responses)
        - [Using the baseline](https://wfuzz.readthedocs.io/en/latest/user/getting.html#using-the-baseline)
        - [Regex filters](https://wfuzz.readthedocs.io/en/latest/user/getting.html#regex-filters)
- [Basic Usage](https://wfuzz.readthedocs.io/en/latest/user/basicusage.html)
    - [Fuzzing Paths and Files](https://wfuzz.readthedocs.io/en/latest/user/basicusage.html#fuzzing-paths-and-files)
    - [Fuzzing Parameters In URLs](https://wfuzz.readthedocs.io/en/latest/user/basicusage.html#fuzzing-parameters-in-urls)
    - [Fuzzing POST Requests](https://wfuzz.readthedocs.io/en/latest/user/basicusage.html#fuzzing-post-requests)
    - [Fuzzing Cookies](https://wfuzz.readthedocs.io/en/latest/user/basicusage.html#fuzzing-cookies)
    - [Fuzzing Custom headers](https://wfuzz.readthedocs.io/en/latest/user/basicusage.html#fuzzing-custom-headers)
    - [Fuzzing HTTP Verbs](https://wfuzz.readthedocs.io/en/latest/user/basicusage.html#fuzzing-http-verbs)
    - [Proxies](https://wfuzz.readthedocs.io/en/latest/user/basicusage.html#proxies)
    - [Authentication](https://wfuzz.readthedocs.io/en/latest/user/basicusage.html#authentication)
    - [Recursion](https://wfuzz.readthedocs.io/en/latest/user/basicusage.html#recursion)
    - [Perfomance](https://wfuzz.readthedocs.io/en/latest/user/basicusage.html#perfomance)
    - [Writing to a file](https://wfuzz.readthedocs.io/en/latest/user/basicusage.html#writing-to-a-file)
    - [Different output](https://wfuzz.readthedocs.io/en/latest/user/basicusage.html#different-output)
- [Advanced Usage](https://wfuzz.readthedocs.io/en/latest/user/advanced.html)
    - [Wfuzz global options](https://wfuzz.readthedocs.io/en/latest/user/advanced.html#wfuzz-global-options)
    - [Iterators: Combining payloads](https://wfuzz.readthedocs.io/en/latest/user/advanced.html#iterators-combining-payloads)
    - [Encoders](https://wfuzz.readthedocs.io/en/latest/user/advanced.html#encoders)
        - [Specifying an encoder](https://wfuzz.readthedocs.io/en/latest/user/advanced.html#specifying-an-encoder)
        - [Specifying multiple encoders](https://wfuzz.readthedocs.io/en/latest/user/advanced.html#specifying-multiple-encoders)
    - [Scan/Parse Plugins](https://wfuzz.readthedocs.io/en/latest/user/advanced.html#scan-parse-plugins)
        - [Custom scripts](https://wfuzz.readthedocs.io/en/latest/user/advanced.html#custom-scripts)
    - [Recipes](https://wfuzz.readthedocs.io/en/latest/user/advanced.html#recipes)
    - [Connect to an specific host](https://wfuzz.readthedocs.io/en/latest/user/advanced.html#connect-to-an-specific-host)
    - [Scan Mode: Ignore Errors and Exceptions](https://wfuzz.readthedocs.io/en/latest/user/advanced.html#scan-mode-ignore-errors-and-exceptions)
        - [Timeouts](https://wfuzz.readthedocs.io/en/latest/user/advanced.html#timeouts)
    - [Filter Language](https://wfuzz.readthedocs.io/en/latest/user/advanced.html#filter-language)
        - [Filtering results](https://wfuzz.readthedocs.io/en/latest/user/advanced.html#filtering-results)
        - [Payload mangling](https://wfuzz.readthedocs.io/en/latest/user/advanced.html#payload-mangling)
            - [Slicing a payload](https://wfuzz.readthedocs.io/en/latest/user/advanced.html#slicing-a-payload)
            - [Re-writing a payload](https://wfuzz.readthedocs.io/en/latest/user/advanced.html#re-writing-a-payload)
            - [Prefilter](https://wfuzz.readthedocs.io/en/latest/user/advanced.html#prefilter)
    - [Reutilising previous results](https://wfuzz.readthedocs.io/en/latest/user/advanced.html#reutilising-previous-results)
    - [Reutilising previous results](https://wfuzz.readthedocs.io/en/latest/user/advanced.html#id1)
        - [Request mangling](https://wfuzz.readthedocs.io/en/latest/user/advanced.html#request-mangling)
- [wfpayload](https://wfuzz.readthedocs.io/en/latest/user/wfpayload.html)
    - [Generating new dictionaries](https://wfuzz.readthedocs.io/en/latest/user/wfpayload.html#generating-new-dictionaries)
    - [Analysing saved sessions](https://wfuzz.readthedocs.io/en/latest/user/wfpayload.html#analysing-saved-sessions)
    - [Running plugins against saved sessions](https://wfuzz.readthedocs.io/en/latest/user/wfpayload.html#running-plugins-against-saved-sessions)
    - [Re-writing saved sessions](https://wfuzz.readthedocs.io/en/latest/user/wfpayload.html#re-writing-saved-sessions)

# Library Guide[](https://wfuzz.readthedocs.io/en/latest/#library-guide "Permalink to this headline")

- [Python library](https://wfuzz.readthedocs.io/en/latest/library/guide.html)
    - [Library Options](https://wfuzz.readthedocs.io/en/latest/library/guide.html#library-options)
    - [Fuzzing a URL](https://wfuzz.readthedocs.io/en/latest/library/guide.html#fuzzing-a-url)
    - [FuzzSession object](https://wfuzz.readthedocs.io/en/latest/library/guide.html#fuzzsession-object)
    - [Get payload](https://wfuzz.readthedocs.io/en/latest/library/guide.html#get-payload)
    - [Get session](https://wfuzz.readthedocs.io/en/latest/library/guide.html#get-session)
    - [Interacting with the results](https://wfuzz.readthedocs.io/en/latest/library/guide.html#interacting-with-the-results)

**Credit:** This information was adapted from an excellent guide on [Wfuzz](https://wfuzz.readthedocs.io/en/latest/). Be sure to check out the original post for more details.

# Fuzzing Made Easy: How to Use wfuzz for Efficient Web Application Testing?

![](https://miro.medium.com/v2/resize:fit:700/1*nbcbTEgTvfo_4e5-48i0Xw.png)

[https://github.com/xmendez/wfuzz](https://github.com/xmendez/wfuzz)

Fuzzing, also known as fuzz testing or robustness testing, is a technique used in software testing to find security vulnerabilities and defects in applications by providing invalid, unexpected, or random input to the application’s inputs or APIs. This technique is an effective way to discover unknown vulnerabilities and test the resilience of applications against unexpected input.

Fuzzing is particularly important in web application testing, as web applications are often complex and have multiple entry points that can be exploited by attackers. By testing web applications with fuzzing tools, you can identify potential vulnerabilities such as injection flaws, cross-site scripting (XSS), and other security weaknesses.

[wfuzz](https://github.com/xmendez/wfuzz) is a popular command-line tool for web application testing that is designed to help security professionals automate the process of fuzzing. It offers a wide range of features that make it easy to customize fuzzing parameters and analyze the results. In this tutorial, we’ll explore how to use [wfuzz](https://github.com/xmendez/wfuzz) to conduct efficient web application testing.

## Setting up wfuzz

To get started with wfuzz, you need to install and configure it on your system. Here are the steps to do so:

- Install Python: wfuzz is written in Python, so you need to have Python installed on your system before you can use it. You can download and install Python from the official Python website.
- Install wfuzz: Once you have installed Python, you can install wfuzz using pip, the package installer for Python. Open a command prompt or terminal and enter the following command:

pip install wfuzz

- Verify the installation: After installation, you can verify that wfuzz is installed correctly by running the following command:

wfuzz -h

This command will display the help screen for wfuzz.

# Basic usage:

wfuzz -c [OPTIONS] URL

**OPTIONS:**

- `-c` : colorize the output
- `-z` : set the payload type (list, num, etc.)
- `-d` : set the data to be sent with the request
- `-H` : set the headers to be sent with the request
- `-e` : set the encoding for the payload (urlencode, hex, etc.)
- `-w` : set the wordlist to be used for fuzzing
- `-p` : set the number of concurrent connections
- `-t` : set the timeout for each request
- `-s` : set the delay between each request
- `-L` : follow redirects

**Payload types:**

- `list` : use a wordlist to fuzz the target
- `num` : use a range of numbers to fuzz the target
- `alpha` : use the alphabet to fuzz the target
- `alphanum` : use a combination of numbers and letters to fuzz the target
- `hex` : use hexadecimal values to fuzz the target

**Examples:**

wfuzz -c -z list,common.txt https://example.com/FUZZ

This will use the “common.txt” wordlist to fuzz the “FUZZ” parameter in the URL “[https://example.com/FUZZ](https://example.com/FUZZ)".

wfuzz -c -z num,1-10 https://example.com/FUZZ

This will use the range of numbers 1–10 to fuzz the “FUZZ” parameter in the URL “[https://example.com/FUZZ](https://example.com/FUZZ)".

wfuzz -c -z alpha https://example.com/FUZZ

This will use the alphabet to fuzz the “FUZZ” parameter in the URL “[https://example.com/FUZZ](https://example.com/FUZZ)".

wfuzz -c -z alphanum https://example.com/FUZZ

This will use a combination of numbers and letters to fuzz the “FUZZ” parameter in the URL “[https://example.com/FUZZ](https://example.com/FUZZ)".

wfuzz -c -z hex https://example.com/FUZZ

This will use hexadecimal values to fuzz the “FUZZ” parameter in the URL “[https://example.com/FUZZ](https://example.com/FUZZ)".

To specify a different output format, you can use the “-o” option followed by the format type. For example:

wfuzz -c -o json https://example.com/FUZZ

This command tells wfuzz to display the results in **JSON** format. Other output formats include **XML, HTML, CSV,** and **YAML**.

# Advanced wfuzz Usage

In addition to setting the target URL and payload, you can also specify headers and cookies in wfuzz requests. This can be useful for testing web applications that require authentication or have specific header requirements.

**To specify headers**, you can use the “-H” option followed by the header value. For example:

wfuzz -c -H "Authorization: Bearer token" https://example.com/FUZZ

This command tells wfuzz to include the “Authorization” header with the value “Bearer token” in each request.

**To specify cookies**, you can use the “ — cookie” option followed by the cookie value. For example:

wfuzz -c --cookie "name=value" https://example.com/FUZZ

This command tells wfuzz to include the “name” cookie with the value “value” in each request.

**You can specify multiple headers or cookies by separating them with a semicolon (;)**. For example:

wfuzz -c -H "Authorization: Bearer token; Content-Type: application/json" --cookie "name=value; session=1234" https://example.com/FUZZ

This command tells wfuzz to include the “Authorization” and “Content-Type” headers, as well as the “name” and “session” cookies in each request.

## Fuzzing authentication systems

Fuzzing authentication systems is an important aspect of web application testing, as authentication vulnerabilities can lead to unauthorized access to sensitive data or functionality.

To fuzz authentication systems using wfuzz, you can use the “-d” option to specify the login credentials and the “-b” option to specify any necessary cookies. For example:

wfuzz -c -d "username=admin&password=FUZZ" -b "session=12345" https://example.com/login.php

This command tells wfuzz to use the specified login credentials and cookie value to fuzz the authentication system at the login.php endpoint. The “FUZZ” keyword will be replaced by each payload in turn.

You can also combine authentication fuzzing with other fuzzing techniques, such as brute force or injection, to test for a wider range of vulnerabilities. For example:

wfuzz -c -z brute-force -d "username=admin&password=FUZZ" -b "session=12345" https://example.com/login.php

This command tells wfuzz to use the brute force technique in combination with the specified login credentials and cookie value to test for weak passwords in the authentication system at the login.php endpoint.

By fuzzing authentication systems using wfuzz, you can identify vulnerabilities that could lead to unauthorized access to sensitive data or functionality, and take steps to remediate these vulnerabilities before they can be exploited by attackers.

# wfuzz with Burp Suite

wfuzz can be integrated with Burp Suite to automate the fuzzing process and identify vulnerabilities in web applications. By using wfuzz with Burp Suite, you can leverage the power of both tools and streamline your testing process.

To run wfuzz from Burp Suite, follow these steps:

1. Install the wfuzz extension for Burp Suite.
2. Launch Burp Suite and navigate to the “Extender” tab.
3. Click on the “Extensions” tab and select “Add”.
4. Locate the wfuzz extension file and click “Next” to install it.
5. Navigate to the “Proxy” tab and send a request to the endpoint you want to fuzz.
6. Right-click on the request in the “Proxy” history and select “Send to wfuzz”.
7. In the wfuzz interface, specify the payload you want to use and any other options you want to configure.
8. Click “Start Fuzzer” to begin the fuzzing process.

Interpreting results in Burp Suite can be done in several ways. One way is to view the results in the “Proxy” history and look for unusual responses or error messages. Another way is to use the Burp Suite “Scanner” to automatically scan the target for vulnerabilities and generate a report.

By using wfuzz with Burp Suite, you can automate the fuzzing process and identify vulnerabilities in web applications more quickly and accurately. This approach allows you to save time and effort while ensuring the security of your web applications.

Some of the benefits of using wfuzz include:

- Automating the fuzzing process and saving time and effort
- Customizing payloads to identify specific vulnerabilities
- Identifying potential security issues before they can be exploited
- Integrating with other tools like Burp Suite to streamline the testing process

# **Conclusion**

wfuzz is a powerful and flexible tool for web application testing and security assessment. Its ability to automate the fuzzing process and customize payloads makes it an ideal choice for identifying vulnerabilities in web applications.

**Credit:** This information was adapted from an excellent guide on [Medium](https://medium.com/@cuncis/fuzzing-made-easy-how-to-use-wfuzz-for-efficient-web-application-testing-d843e5b089bf). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/008QxzctzqQ?si=X9zTfTzpaxYd98xJ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=008QxzctzqQ). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/1Do5VjeEVjg?si=SbU3rl6_F6RvCeht" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=1Do5VjeEVjg). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Ou_CFRpY7no?si=nVQDQZPx6qMs4xnO" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=Ou_CFRpY7no&t=69s). Be sure to check out the original post for more details.



