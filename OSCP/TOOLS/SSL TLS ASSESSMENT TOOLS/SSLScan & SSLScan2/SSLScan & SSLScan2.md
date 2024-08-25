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

