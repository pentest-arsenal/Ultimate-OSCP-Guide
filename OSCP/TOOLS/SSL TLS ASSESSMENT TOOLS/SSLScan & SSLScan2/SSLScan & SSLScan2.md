
# SSLScan

[](https://github.com/DinoTools/sslscan?tab=readme-ov-file#sslscan)

SSLScan queries SSL services, such as HTTPS, in order to determine the ciphers that are supported. SSLScan is designed to be easy, lean and fast. The output includes preferred ciphers of the SSL service, the certificate and is in Text and XML formats.

## Features

[](https://github.com/DinoTools/sslscan?tab=readme-ov-file#features)

- Query SSL services
- Supported cryptographic protocols: SSLv2, SSLv3, TLS 1.0, TLS 1.1 and TLS 1.2 (depends on used OpenSSL library)
- STARTTLS support with FTP, IMAP, POP3, SMTP and XMPP
- Perform a HTTP connect
- IPv4 and IPv6
- Bind to local IP address
- Python extensions
- Text and XML output

## Install

[](https://github.com/DinoTools/sslscan?tab=readme-ov-file#install)

Requirements:

- OpenSSL 1.0.0 or better
- gcc
- make
- cmake
- openssl-devel
- python-devel (2.6, 2.7, 3.2 or 3.3 - Python 3.x preferred)

Makefile build:

```
mkdir build
cd build
cmake ..
make
make install        (as root)
```

## Usage

[](https://github.com/DinoTools/sslscan?tab=readme-ov-file#usage)

To scan a HTTPS service:

```
sslscan example.org
```

To display more information:

```
sslscan --help
```

## History

[](https://github.com/DinoTools/sslscan?tab=readme-ov-file#history)

- 2007-2009 SSLScan was originally written by Ian Ventura-Whiting. ([http://www.titania.co.uk](http://www.titania.co.uk/) [http://sourceforge.net/projects/sslscan/](http://sourceforge.net/projects/sslscan/))
- 2010-2011 The project has been forked by Jacob Appelbaum to better support STARTTLS. ([http://www.github.com/ioerror/sslscan](http://www.github.com/ioerror/sslscan))
- 2013- The project has been forked by DinoTools to add TLS 1.1 and 1.2 support, apply available patches and add new features. ([https://github.com/DinoTools/sslscan](https://github.com/DinoTools/sslscan))

## License

[](https://github.com/DinoTools/sslscan?tab=readme-ov-file#license)

Published under the GPLv3 (see LICENSE for more information)

Most of the pre-TLS protocol setup was inspired by the OpenSSL s_client.c program.

Some of the OpenSSL setup code was borrowed from The Tor Project's Tor program. Thus it is likely proper to comply with the BSD license by saying: Copyright (c) 2007-2010, The Tor Project, Inc.

## Projects using SSLScan

[](https://github.com/DinoTools/sslscan?tab=readme-ov-file#projects-using-sslscan)

- [TLSSLed](http://www.taddong.com/en/lab.html)

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/DinoTools/sslscan?tab=readme-ov-file#sslscan). Be sure to check out the original post for more details.

# SSLScan2

[](https://github.com/rbsec/sslscan#sslscan2)

SSLScan version 2 has now been released. This includes a major rewrite of the backend scanning code, which means that it is no longer reliant on the version of OpenSSL for many checks. This means that it is possible to support legacy protocols (SSLv2 and SSLv3), as well as supporting TLSv1.3 - regardless of the version of OpenSSL that it has been compiled against.

This has been made possible largely by the work of [jtesta](https://github.com/jtesta), who has been responsible for most of the backend rewrite.

Other key changes include:

- Enumeration of server key exchange groups.
- Enumeration of server signature algorithms.
- SSLv2 and SSLv3 protocol support is scanned, but individual ciphers are not.
- A test suite is included using Docker, to verify that sslscan is functionality correctly.
- Removed the `--http` option, as it was broken and had very little use in the first place.

## XML Output Changes

[](https://github.com/rbsec/sslscan#xml-output-changes)

A potentially breaking change has been made to the XML output in version **2.0.0-beta4**. Previously, multiple `<certificate>` elements could be returned (one by default, and a second one if `--show-certificate` was used).

The key changes are:

- A new parent `<certificates>` element that will contain the `<certificate>` elements.
- `<certificate>` elements have a new `type` attribute, which can either be:
    - `short` for the default output.
    - `full` for when `--show-certificate` is used.
- There will potentially be more than one certificate of each type returned on servers that have multiple certificates with different signature algorithms (see discussion in issue [#208](https://github.com/rbsec/sslscan/issues/208)).
- The `<signature-algorithm>` element in a `<certificate>` no longer contains the "Signature Algorithm:" prefix, or the spacing and newline.

If you are using the XML output, then you may need to make changes to your parser.

# README

[](https://github.com/rbsec/sslscan#readme)

[![ci](https://github.com/rbsec/sslscan/actions/workflows/ci.yml/badge.svg)](https://github.com/rbsec/sslscan/actions/workflows/ci.yml)

This is a fork of ioerror's version of sslscan (the original readme of which is included below) by rbsec ([robin@rbsec.net](mailto:robin@rbsec.net)).

Key changes are as follows:

- Highlight SSLv2 and SSLv3 ciphers in output.
- Highlight CBC ciphers on SSLv3 (POODLE).
- Highlight 3DES and RC4 ciphers in output.
- Highlight PFS+GCM ciphers as good in output.
- Highlight NULL (0 bit), weak (<40 bit) and medium (40 < n <= 56) ciphers in output.
- Highlight anonymous (ADH and AECDH) ciphers in output (purple).
- Hide certificate information by default (display with `--show-certificate`).
- Hide rejected ciphers by default (display with `--failed`).
- Added TLSv1.1, TLSv1.2 and TLSv1.3 support.
- Supports IPv6 (can be forced with `--ipv6`).
- Check for TLS compression (CRIME, disable with `--no-compression`).
- Disable cipher suite checking `--no-ciphersuites`.
- Disable coloured output `--no-colour`.
- Removed undocumented -p output option.
- Added check for OpenSSL HeartBleed (CVE-2014-0160, disable with `--no-heartbleed`).
- Flag certificates signed with MD5 or SHA-1, or with short (<2048 bit) RSA keys.
- Support scanning RDP servers with `--rdp` (credit skettler).
- Added option to specify socket timeout.
- Added option for static compilation (credit dmke).
- Added `--sleep` option to pause between requests.
- Disable output for anything than specified checks `--no-preferred`.
- Determine the list of CAs acceptable for client certificates `--show-client-cas`.
- Experimental build support on OS X (credit MikeSchroll).
- Flag some self-signed SSL certificates.
- Experimental Windows support (credit jtesta).
- Display EC curve names and DHE key lengths with OpenSSL >= 1.0.2 `--no-cipher-details`.
- Flag weak DHE keys with OpenSSL >= 1.0.2 `--cipher-details`.
- Flag expired certificates.
- Flag TLSv1.0 and TLSv1.1 protocols in output as weak.
- Experimental OS X support (static building only).
- Support for scanning PostgreSQL servers (credit nuxi).
- Check for TLS Fallback SCSV support.
- Added StartTLS support for LDAP `--starttls-ldap`.
- Added SNI support `--sni-name` (credit Ken).
- Support STARTTLS for MySQL (credit bk2017).
- Check for supported key exchange groups.
- Check for supported server signature algorithms.
- Display IANA/RFC cipher names `--iana-names`
- Display the full certifiate chain `--show-certificates`

### Building on Linux

[](https://github.com/rbsec/sslscan#building-on-linux)

It is possible to ignore the OpenSSL system installation and ship your own version. Although this results in a more resource-heavy `sslscan` binary (file size, memory consumption, etc.), this allows some additional checks such as TLS compression.

To compile your own OpenSSL version, you'll probably need to install the OpenSSL build dependencies. The commands below can be used to do this on Debian. If you don't have them already, you will need to enable the `deb-src` repos in your apt config. sslscan was primarily developed on Debian, so if you are compiling on other distributions your mileage may vary.

```
apt-get install build-essential git zlib1g-dev
apt-get build-dep openssl
```

Then run

```
make static
```

This will clone the [OpenSSL repository](https://github.com/openssl/openssl), and configure/compile/test OpenSSL prior to compiling `sslscan`.

**Please note:** Out of the box, OpenSSL cannot compiled with `clang` without further customization (which is not done by the provided `Makefile`). For more information on this, see [Modifying Build Settings](http://wiki.openssl.org/index.php/Compilation_and_Installation#Modifying_Build_Settings) in the OpenSSL wiki.

You can verify whether you have a statically linked OpenSSL version, by checking whether the version listed by `sslscan --version` has the `-static` suffix.

### Building with Docker

[](https://github.com/rbsec/sslscan#building-with-docker)

Ensure that you local Docker installation is functional, and the build the container with:

```
make docker
```

Or manually with:

```
docker build -t sslscan:sslscan .
```

You can then run sslscan with:

```
docker run --rm -ti sslscan:sslscan --help
```

### Building on Windows

[](https://github.com/rbsec/sslscan#building-on-windows)

Thanks to a patch by jtesta, sslscan can now be compiled on Windows. This can either be done natively or by cross-compiling from Linux. See INSTALL for instructions.

Note that sslscan was originally written for Linux, and has not been extensively tested on Windows. As such, the Windows version should be considered experimental.

Pre-build cross-compiled Windows binaries are available on the [GitHub Releases Page](https://github.com/rbsec/sslscan/releases).

### Building on OS X

[](https://github.com/rbsec/sslscan#building-on-os-x)

There is experimental support for statically building on OS X, however this should be considered unsupported. You may need to install any dependencies required to compile OpenSSL from source on OS X. Once you have, just run:

```
make static
```

# Original (ioerror) README

[](https://github.com/rbsec/sslscan#original-ioerror-readme)

This is a fork of sslscan.c to better support STARTTLS.

The original home page of sslscan is:

```
http://www.titania.co.uk
```

sslscan was originally written by:

```
Ian Ventura-Whiting
```

The current home page of this fork (until upstream merges a finished patch) is:

```
http://www.github.com/ioerror/sslscan
```

Most of the pre-TLS protocol setup was inspired by the OpenSSL s_client.c program. The goal of this fork is to eventually merge with the original project after the STARTTLS setup is polished.

Some of the OpenSSL setup code was borrowed from The Tor Project's Tor program. Thus it is likely proper to comply with the BSD license by saying: Copyright (c) 2007-2010, The Tor Project, Inc.

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/rbsec/sslscan). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/lKX1MIIxFCg?si=XPKkSUEd88ty-j1A" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=lKX1MIIxFCg). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/DDbwrMrwOFc?si=L-QgzLex77oTmIiK" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=DDbwrMrwOFc). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/BVdv_O-aG6c?si=Wp4d0dT1dFuzN9pL" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=BVdv_O-aG6c). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/hGrd4CqXw1U?si=TQbKiX-vE6cU-OIn" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=hGrd4CqXw1U). Be sure to check out the original post for more details.



