# CipherScan

[](https://github.com/mozilla/cipherscan#cipherscan)

[![Build Status](https://camo.githubusercontent.com/968dfd60de6155c9035fe278d0b2c5bfa149bb4ce806af9dccca446b13134dd9/68747470733a2f2f7472617669732d63692e6f72672f6d6f7a696c6c612f6369706865727363616e2e7376673f6272616e63683d6d6173746572)](https://travis-ci.org/mozilla/cipherscan)

[![cipherscan](https://camo.githubusercontent.com/eb45879b3fc65de2265ca672620cb198326e7db056b7f01575dc868c97f3f047/68747470733a2f2f7062732e7477696d672e636f6d2f6d656469612f4350626a764346573841416e554b332e706e673a6c61726765)](https://camo.githubusercontent.com/eb45879b3fc65de2265ca672620cb198326e7db056b7f01575dc868c97f3f047/68747470733a2f2f7062732e7477696d672e636f6d2f6d656469612f4350626a764346573841416e554b332e706e673a6c61726765)

Cipherscan tests the ordering of the SSL/TLS ciphers on a given target, for all major versions of SSL and TLS. It also extracts some certificates informations, TLS options, OCSP stapling and more. Cipherscan is a wrapper above the `openssl s_client` command line.

Cipherscan is meant to run on all flavors of unix. It ships with its own built of OpenSSL for Linux/64 and Darwin/64. On other platform, it will use the openssl version provided by the operating system (which may have limited ciphers support), or your own version provided in the `-o` command line flag.

## Examples

[](https://github.com/mozilla/cipherscan#examples)

Basic test:

```shell
$ ./cipherscan google.com
...................
Target: google.com:443

prio  ciphersuite                  protocols                    pfs                 curves
1     ECDHE-RSA-CHACHA20-POLY1305  TLSv1.2                      ECDH,P-256,256bits  prime256v1
2     ECDHE-RSA-AES128-GCM-SHA256  TLSv1.2                      ECDH,P-256,256bits  prime256v1
3     ECDHE-RSA-AES128-SHA         TLSv1.1,TLSv1.2              ECDH,P-256,256bits  prime256v1
4     ECDHE-RSA-RC4-SHA            SSLv3,TLSv1,TLSv1.1,TLSv1.2  ECDH,P-256,256bits  prime256v1
5     AES128-GCM-SHA256            TLSv1.2                      None                None
6     AES128-SHA256                TLSv1.2                      None                None
7     AES128-SHA                   TLSv1.1,TLSv1.2              None                None
8     RC4-SHA                      SSLv3,TLSv1,TLSv1.1,TLSv1.2  None                None
9     RC4-MD5                      SSLv3,TLSv1,TLSv1.1,TLSv1.2  None                None
10    ECDHE-RSA-AES256-GCM-SHA384  TLSv1.2                      ECDH,P-256,256bits  prime256v1
11    ECDHE-RSA-AES256-SHA384      TLSv1.2                      ECDH,P-256,256bits  prime256v1
12    ECDHE-RSA-AES256-SHA         SSLv3,TLSv1,TLSv1.1,TLSv1.2  ECDH,P-256,256bits  prime256v1
13    AES256-GCM-SHA384            TLSv1.2                      None                None
14    AES256-SHA256                TLSv1.2                      None                None
15    AES256-SHA                   SSLv3,TLSv1,TLSv1.1,TLSv1.2  None                None
16    ECDHE-RSA-AES128-SHA256      TLSv1.2                      ECDH,P-256,256bits  prime256v1
17    ECDHE-RSA-DES-CBC3-SHA       SSLv3,TLSv1,TLSv1.1,TLSv1.2  ECDH,P-256,256bits  prime256v1
18    DES-CBC3-SHA                 SSLv3,TLSv1,TLSv1.1,TLSv1.2  None                None

Certificate: trusted, 2048 bit, sha1WithRSAEncryption signature
TLS ticket lifetime hint: 100800
OCSP stapling: not supported
Cipher ordering: server
```

Testing STARTTLS:

```
darwin$ $ ./cipherscan --curves -starttls xmpp jabber.ccc.de:5222
................................
Target: jabber.ccc.de:5222

prio  ciphersuite                  protocols              pfs                 curves
1     ECDHE-RSA-AES256-GCM-SHA384  TLSv1.2                ECDH,P-256,256bits  prime256v1
2     ECDHE-RSA-AES256-SHA384      TLSv1.2                ECDH,P-256,256bits  prime256v1
3     ECDHE-RSA-AES256-SHA         TLSv1,TLSv1.1,TLSv1.2  ECDH,P-256,256bits  prime256v1
4     DHE-RSA-AES256-GCM-SHA384    TLSv1.2                DH,1024bits         None
5     DHE-RSA-AES256-SHA256        TLSv1.2                DH,1024bits         None
6     DHE-RSA-AES256-SHA           TLSv1,TLSv1.1,TLSv1.2  DH,1024bits         None
7     DHE-RSA-CAMELLIA256-SHA      TLSv1,TLSv1.1,TLSv1.2  DH,1024bits         None
8     AES256-GCM-SHA384            TLSv1.2                None                None
9     AES256-SHA256                TLSv1.2                None                None
10    AES256-SHA                   TLSv1,TLSv1.1,TLSv1.2  None                None
11    CAMELLIA256-SHA              TLSv1,TLSv1.1,TLSv1.2  None                None
12    ECDHE-RSA-AES128-GCM-SHA256  TLSv1.2                ECDH,P-256,256bits  prime256v1
13    ECDHE-RSA-AES128-SHA256      TLSv1.2                ECDH,P-256,256bits  prime256v1
14    ECDHE-RSA-AES128-SHA         TLSv1,TLSv1.1,TLSv1.2  ECDH,P-256,256bits  prime256v1
15    DHE-RSA-AES128-GCM-SHA256    TLSv1.2                DH,1024bits         None
16    DHE-RSA-AES128-SHA256        TLSv1.2                DH,1024bits         None
17    DHE-RSA-AES128-SHA           TLSv1,TLSv1.1,TLSv1.2  DH,1024bits         None
18    DHE-RSA-SEED-SHA             TLSv1,TLSv1.1,TLSv1.2  DH,1024bits         None
19    DHE-RSA-CAMELLIA128-SHA      TLSv1,TLSv1.1,TLSv1.2  DH,1024bits         None
20    AES128-GCM-SHA256            TLSv1.2                None                None
21    AES128-SHA256                TLSv1.2                None                None
22    AES128-SHA                   TLSv1,TLSv1.1,TLSv1.2  None                None
23    SEED-SHA                     TLSv1,TLSv1.1,TLSv1.2  None                None
24    CAMELLIA128-SHA              TLSv1,TLSv1.1,TLSv1.2  None                None

Certificate: UNTRUSTED, 2048 bit, sha1WithRSAEncryption signature
TLS ticket lifetime hint: None
OCSP stapling: not supported
Cipher ordering: client
Curves ordering: server
Curves fallback: False
```

Exporting to JSON with the `-j` command line option:

```js
$ ./cipherscan --curves -j www.ebay.com | j
{
    "curves_fallback": "False",
    "serverside": "True",
    "target": "www.ebay.com:443",
    "utctimestamp": "2015-04-03T14:54:31.0Z",
    "ciphersuite": [
        {
            "cipher": "AES256-SHA",
            "ocsp_stapling": "False",
            "pfs": "None",
            "protocols": [
                "TLSv1",
                "TLSv1.1",
                "TLSv1.2"
            ],
            "pubkey": [
                "2048"
            ],
            "sigalg": [
                "sha1WithRSAEncryption"
            ],
            "ticket_hint": "None",
            "trusted": "True"
        },
        {
            "cipher": "ECDHE-RSA-DES-CBC3-SHA",
            "curves": [
                "prime256v1",
                "secp384r1",
                "secp224r1",
                "secp521r1"
            ],
            "curves_ordering": "server",
            "ocsp_stapling": "False",
            "pfs": "ECDH,P-256,256bits",
            "protocols": [
                "TLSv1",
                "TLSv1.1",
                "TLSv1.2"
            ],
            "pubkey": [
                "2048"
            ],
            "sigalg": [
                "sha1WithRSAEncryption"
            ],
            "ticket_hint": "None",
            "trusted": "True"
        }
    ]
}
```

## Analyzing configurations

[](https://github.com/mozilla/cipherscan#analyzing-configurations)

The motivation behind cipherscan is to help operators configure good TLS on their endpoints. To help this further, the script `analyze.py` compares the results of a cipherscan with the TLS guidelines from [https://wiki.mozilla.org/Security/Server_Side_TLS](https://wiki.mozilla.org/Security/Server_Side_TLS) and output a level and recommendations.

```shell
$ ./analyze.py -t jve.linuxwall.info
jve.linuxwall.info:443 has intermediate tls

Changes needed to match the old level:
* consider enabling SSLv3
* add cipher DES-CBC3-SHA
* use a certificate with sha1WithRSAEncryption signature
* consider enabling OCSP Stapling

Changes needed to match the intermediate level:
* consider enabling OCSP Stapling

Changes needed to match the modern level:
* remove cipher AES128-GCM-SHA256
* remove cipher AES256-GCM-SHA384
* remove cipher AES128-SHA256
* remove cipher AES128-SHA
* remove cipher AES256-SHA256
* remove cipher AES256-SHA
* disable TLSv1
* consider enabling OCSP Stapling
```

In the output above, `analyze.py` indicates that the target `jve.linuxwall.info` matches the intermediate configuration level. If the administrator of this site wants to reach the modern level, the items that failed under the modern tests should be corrected.

`analyze.py` does not make any assumption on what a good level should be. Sites operators should know what level they want to match against, based on the compatibility level they want to support. Again, refer to [https://wiki.mozilla.org/Security/Server_Side_TLS](https://wiki.mozilla.org/Security/Server_Side_TLS) for more information.

Note on Nagios mode: `analyse.py` can be ran as a nagios check with `--nagios`. The exit code will then represent the state of the configuration:

- 2 (critical) for bad tls
- 1 (warning) if it doesn't match the desired level
- 0 (ok) if it matches. cipherscan can take more than 10 seconds to complete. To alleviate any timeout issues, you may want to run it outside of nagios, passing data through some temporary file.

## OpenSSL

[](https://github.com/mozilla/cipherscan#openssl)

Cipherscan uses a custom release of openssl for linux 64 bits and darwin 64 bits. OpenSSL is build from a custom branch maintained by Peter Mosmans that includes a number of patches not merged upstream. It can be found here: [https://github.com/PeterMosmans/openssl](https://github.com/PeterMosmans/openssl)

You can build it yourself using following commands:

```
git clone https://github.com/PeterMosmans/openssl.git --depth 1 -b 1.0.2-chacha
cd openssl
./Configure zlib no-shared experimental-jpake enable-md2 enable-rc5 \
enable-rfc3779 enable-gost enable-static-engine linux-x86_64
make depend
make
make report
```

The statically linked binary will be `apps/openssl`.

## Contributors

[](https://github.com/mozilla/cipherscan#contributors)

- Julien Vehent [julien@linuxwall.info](mailto:julien@linuxwall.info) (original author)
- Hubert Kario [hkario@redhat.com](mailto:hkario@redhat.com) (co-maintainer)
- Pepi Zawodsky [git@maclemon.at](mailto:git@maclemon.at)
- Michael Zeltner [m@niij.org](mailto:m@niij.org)
- Peter Mosmans [support@go-forward.net](mailto:support@go-forward.net)
- Vincent Riquer [v.riquer@b2f-concept.com](mailto:v.riquer@b2f-concept.com)
- Christian Stadelmann
- Simon Deziel [simon.deziel@gmail.com](mailto:simon.deziel@gmail.com)
- Aaron Zauner [azet@azet.org](mailto:azet@azet.org)
- Mike [mikedawg@gmail.com](mailto:mikedawg@gmail.com)
- Phil Cohen [phlipper@users.noreply.github.com](mailto:phlipper@users.noreply.github.com)
- Samuel Kleiner [sam@firstbanco.com](mailto:sam@firstbanco.com)
- Richard Soderberg [https://twitter.com/floatingatoll](https://twitter.com/floatingatoll)
- Adam Crosby [adamcrosby@users.noreply.github.com](mailto:adamcrosby@users.noreply.github.com)

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/mozilla/cipherscan). Be sure to check out the original post for more details.

### CIPHERSCAN

![Image](https://www.briskinfosec.com/assets/tooloftheday/Copy_of_Briskinfosec_TOD_Latest_samples_2.jpg)

CipherScan:- Discovers the SSL ciphersuites supported by the target.

## Features

- Tests the ordering of SSL/TLS ciphers.
- Extracts information on

               Certificates

               TLS options

               OCSP stapling

## Supported Operating System

- Unix
- Linux
- Darwin

## Demo

![Lock image](https://www.briskinfosec.com/assets/tooloftheday/Tool-prefinal.jpg)

## Usage

./cipherscan

## Options

-a | --allciphers                                  Test all known ciphers individually at the end

-b | --benchmark                              Activate benchmark mode.

--capath                                              Use cas from directory (must be in openssl cadir format)

--saveca                                               Save intermediate certificates in CA directory

-d | --delay                                         Pause for n seconds between connections

-D | --debug                                       Output ALL the information.

-h | --help                                           Shows this help text.

-j | --json                                             Output results in JSON format.

-o | --openssl                                     Path/to/your/openssl binary you want to use.

--savecrt                                              Path where to save untrusted and leaf certificates

--[no-]curves                                      Test ECC curves supported by server (req. OpenSSL 1.0.2)

--sigalg                                               Test signature algorithms used in TLSv1.2 ephemeral ciphers (req. OpenSSL 1.0.2)

--[no-]tolerance                                Test TLS tolerance

--no-sni                                               Don't use Server Name Indication

--colors                                                Force use of colors (autodetect by default)

--no-colors                                          Don't use terminal colors

-v | --verbose                                     Increase verbosity

## OpenSSL Options

-starttls [smtp|imap|pop3|ftp|xmpp]

Enable support and testing of the protocols that require turning TLS after initial protocol specific.

-servername name                         

Request SNI support for connections

-proxy proxyhost:port                   

Connect to the scan target via specified proxy     (req. OpenSSL 1.1.0 or bundled OpenSSL)

-verify_hostname name               

Request host name verification in connection      (req. OpenSSL 1.0.2)

-verify_ip ip      

Request host name verification for an IP address, usually not specified in certificates (req. OpenSSL 1.0.2)

## Analysing Configurations

The motivation behind CipherScan is to help operators configure good TLS on their endpoints. To help this further, the script analyze.py compares the results of a CipherScan with the TLS guidelines and output a level and recommendations.

## Usages

- ./analyze.py -t

## Positional Arguments

  infile                                   CipherScan json results

  outfile                                json formatted analysis

## Optional Arguments

  -h, --help                             Show this help message and exit

  -d                                         Debug output

  -l LEVEL                              Target configuration level [old, intermediate, modern]

  -t TARGET                           Analyze a , invokes cipherscan

  -o OPENSSL                       Path to openssl binary, if you don't like the default

  -j                                          Output results in json format

  --ops OPERATOR         Optional name of the operator's team added into the JSON output (for database insertion)

  --nagios                            Use nagios-conformant exit codes


**Credit:** This information was adapted from an excellent guide on [BriskInfosec](https://www.briskinfosec.com/tooloftheday/toolofthedaydetail/CIPHERSCAN). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/VBoDiKlPWW8?si=UxaPlDE7os0GZFRo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=VBoDiKlPWW8). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/P1v6QA0W7Xw?si=yFtpwJrxx4oArZMC" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=P1v6QA0W7Xw). Be sure to check out the original post for more details.

