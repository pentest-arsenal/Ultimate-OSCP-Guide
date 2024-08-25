# SSLyze

[](https://github.com/nabla-c0d3/sslyze#sslyze)

[![Run Tests](https://github.com/nabla-c0d3/sslyze/workflows/Run%20Tests/badge.svg)](https://github.com/nabla-c0d3/sslyze/workflows/Run%20Tests/badge.svg) [![Downloads](https://camo.githubusercontent.com/1b6783bbbd718f31da2d1daeab3023223db9e341ec4c37fcf381a0db54c37db5/68747470733a2f2f706570792e746563682f62616467652f73736c797a652f6d6f6e7468)](https://pepy.tech/project/sslyze) [![PyPI version](https://camo.githubusercontent.com/66ee3332ee98b8e78c041f189822deb0ce2c98945232fede175324135371252b/68747470733a2f2f696d672e736869656c64732e696f2f707970692f762f73736c797a652e737667)](https://pypi.org/project/sslyze/) [![Python version](https://camo.githubusercontent.com/4bc67f540a120ec21c2d15c9a5c3095d1ad0a6c9b2e43706a779be83db2c7af1/68747470733a2f2f696d672e736869656c64732e696f2f707970692f707976657273696f6e732f73736c797a652e737667)](https://pypi.org/project/sslyze/)

SSLyze is a fast and powerful SSL/TLS scanning tool and Python library.

SSLyze can analyze the SSL/TLS configuration of a server by connecting to it, in order to ensure that it uses strong encryption settings (certificate, cipher suites, elliptic curves, etc.), and that it is not vulnerable to known TLS attacks (Heartbleed, ROBOT, OpenSSL CCS injection, etc.).

## Key features

[](https://github.com/nabla-c0d3/sslyze#key-features)

- Focus on speed and reliability: SSLyze is a battle-tested tool that is used to reliably scan **hundreds of thousands** of servers every day.
- Easy to operationalize: SSLyze can be directly run from CI/CD, in order to continuously check a server against Mozilla's recommended TLS configuration.
- Fully documented [Python API](https://nabla-c0d3.github.io/sslyze/documentation/) to run scans directly from any Python application, such as a function deployed to AWS Lambda.
- Support for scanning non-HTTP servers including SMTP, XMPP, LDAP, POP, IMAP, RDP, Postgres and FTP servers.
- Results of a scan can easily be saved to a JSON file for later processing.
- And much more!

## Quick start

[](https://github.com/nabla-c0d3/sslyze#quick-start)

On Windows, Linux (x86 or x64) and macOS, SSLyze can be installed directly via pip:

```
$ pip install --upgrade pip setuptools wheel
$ pip install --upgrade sslyze
$ python -m sslyze www.yahoo.com www.google.com "[2607:f8b0:400a:807::2004]:443"
```

It can also be used via Docker:

```
$ docker run --rm -it nablac0d3/sslyze:6.0.0 www.google.com
```

Lastly, a pre-compiled Windows executable can be downloaded from [the Releases page](https://github.com/nabla-c0d3/sslyze/releases).

## Python API Documentation

[](https://github.com/nabla-c0d3/sslyze#python-api-documentation)

A sample script describing how to use the SSLyze's Python API is available at [./api_sample.py](https://github.com/nabla-c0d3/sslyze/blob/release/api_sample.py).

Full documentation for SSLyze's Python API is [available here](https://nabla-c0d3.github.io/sslyze/documentation).

## Usage as a CI/CD step

[](https://github.com/nabla-c0d3/sslyze#usage-as-a-cicd-step)

By default, SSLyze will check the server's scan results against Mozilla's recommended ["intermediate" TLS configuration](https://wiki.mozilla.org/Security/Server_Side_TLS), and will return a non-zero exit code if the server is not compliant.

```
$ python -m sslyze mozilla.com
```

```
Checking results against Mozilla's "intermediate" configuration. See https://ssl-config.mozilla.org/ for more details.

mozilla.com:443: OK - Compliant.
```

The Mozilla configuration to check against can be configured via `--mozilla_config={old, intermediate, modern}`:

```
$ python -m sslyze --mozilla_config=modern mozilla.com
```

```
Checking results against Mozilla's "modern" configuration. See https://ssl-config.mozilla.org/ for more details.

mozilla.com:443: FAILED - Not compliant.
    * certificate_types: Deployed certificate types are {'rsa'}, should have at least one of {'ecdsa'}.
    * certificate_signatures: Deployed certificate signatures are {'sha256WithRSAEncryption'}, should have at least one of {'ecdsa-with-SHA512', 'ecdsa-with-SHA256', 'ecdsa-with-SHA384'}.
    * tls_versions: TLS versions {'TLSv1.2'} are supported, but should be rejected.
    * ciphers: Cipher suites {'TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384', 'TLS_ECDHE_RSA_WITH_CHACHA20_POLY1305_SHA256', 'TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256'} are supported, but should be rejected.
```

This can be used to easily run an SSLyze scan as a CI/CD step.

## Development environment

[](https://github.com/nabla-c0d3/sslyze#development-environment)

To setup a development environment:

```
$ pip install --upgrade pip setuptools wheel
$ pip install -e . 
$ pip install -r requirements-dev.txt
```

The tests can then be run using:

```
$ invoke test
```

## License

[](https://github.com/nabla-c0d3/sslyze#license)

Copyright (c) 2024 Alban Diquet

SSLyze is made available under the terms of the GNU Affero General Public License (AGPL). See LICENSE.txt for details and exceptions.

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/nabla-c0d3/sslyze). Be sure to check out the original post for more details.

# SSLyze – Fast and powerful SSL/TLS scanning tool

Last Updated : 30 Jan, 2022

Most of the domain uses the SSL(Secure Socket Layer) for saving themselves from various cyber-attacks, but there can be some vulnerabilities raised due to outdated certificates and many more. **SSLyze** tool is an automated cyber security tool that is used to scan the target domain for SSL/TLS vulnerabilities like Heartbleed, OpenSSL, and many more. This tool is developed in the Python language and is also available on the GitHub platform.

**Note**: Make Sure You have Python Installed on your System, as this is a python-based tool. Click to check the Installation process: [Python Installation Steps on Linux](https://www.geeksforgeeks.org/how-to-install-python-on-linux/)

## Installation of SSLyze Tool on Kali Linux OS

**Step 1**: Use the following command to install the tool in your Kali Linux operating system.

> git clone https://github.com/nabla-c0d3/sslyze.git

![](https://media.geeksforgeeks.org/wp-content/uploads/20220112173653/Step1.png)

**Step 2**: Now use the following command to move into the directory of the tool. You have to move in the directory in order to run the tool.

cd sslyze

![](https://media.geeksforgeeks.org/wp-content/uploads/20220112173654/Step2.png)

**Step 3**: You are in the directory of the sslyze. Now you have to install the tool by using the following command.

sudo python3 setup.py install

![](https://media.geeksforgeeks.org/wp-content/uploads/20220112173656/Step3min.png)

**Step 4**: All the dependencies have been installed in your Kali Linux operating system. Now use the following command to run the tool and check the help section.

sslyze -h

![](https://media.geeksforgeeks.org/wp-content/uploads/20220112173658/Step4min.png)

## Working with SSLyze Tool on Kali Linux OS

**Example/Usage**: Scanning SSL/TLS on Target domain

sslyze www.geeksforgeeks.org

In this example, we are scanning on the target domain geeksforgeeks.org.

![](https://media.geeksforgeeks.org/wp-content/uploads/20220112173646/Example11.png)

We have got the Certificate Information which is been associated with the target domain.

![](https://media.geeksforgeeks.org/wp-content/uploads/20220112173648/Example12min.png)

We have got the 13 different cipher suites information.

![](https://media.geeksforgeeks.org/wp-content/uploads/20220112173649/Example13min.png)

Tool has also scanned the target domain for various vulnerabilities like OpenSSL, Heartbleed, etc.

![](https://media.geeksforgeeks.org/wp-content/uploads/20220112173651/Example14min.png)

**Credit:** This information was adapted from an excellent guide on [GeeksForGeeks](https://www.geeksforgeeks.org/sslyze-fast-and-powerful-ssl-tls-scanning-tool/). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/XXFzTOWIgq4?si=rxwKE8aXqnH5O1Fp&amp;start=225" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=XXFzTOWIgq4). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/bmSUzgeGoSY?si=V0ARsms9AGeMOy21" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=bmSUzgeGoSY). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/SVs5oY7NK-I?si=2wDw6eWszRGSMzrB" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=SVs5oY7NK-I). Be sure to check out the original post for more details. I realize that a handful of videos such as this one are in another language, simply turn on CC and translate to English. Bada Bing Bada Boom.



