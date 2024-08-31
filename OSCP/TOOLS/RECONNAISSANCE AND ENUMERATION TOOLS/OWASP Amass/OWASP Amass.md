#  [![OWASP Logo](https://github.com/owasp-amass/amass/raw/master/images/owasp_logo.png) OWASP Amass](https://owasp.org/www-project-amass/)

[](https://github.com/owasp-amass/amass#-owasp-amass)

[![](https://github.com/owasp-amass/amass/raw/master/images/amass_video.gif)](https://github.com/owasp-amass/amass/blob/master/images/amass_video.gif)

[![OWASP Flagship](https://camo.githubusercontent.com/6b56de9c3065007eb293a8fd931ba5cccd491d03415fc69ea374b6e35872a8ce/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f6f776173702d666c61677368697025323070726f6a6563742d3438413634362e737667)](https://owasp.org/projects/#sec-flagships) [![GitHub Release](https://camo.githubusercontent.com/a66f35087a8b8deee700c4f04cd9a3f4c825232eaa4b33a4a52f10529f094121/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f72656c656173652f6f776173702d616d6173732f616d617373)](https://github.com/owasp-amass/amass/releases/latest) [![Docker Images](https://camo.githubusercontent.com/de2e205c3b13762c1235e51d3fd3e86fe9a6677f7ccc57757a93856e872086e4/68747470733a2f2f696d672e736869656c64732e696f2f646f636b65722f70756c6c732f6361666669782f616d6173732e737667)](https://hub.docker.com/r/caffix/amass) [![Follow on Twitter](https://camo.githubusercontent.com/12994167d3d8f06f4bed2cd01b5229a8f4dece46ac3e7ee422ea8d9c31be9978/68747470733a2f2f696d672e736869656c64732e696f2f747769747465722f666f6c6c6f772f6f77617370616d6173732e7376673f6c6f676f3d74776974746572)](https://twitter.com/owaspamass) [![Chat on Discord](https://camo.githubusercontent.com/fd0fcd01a0b3c9370f56bf49bd67f5d9c13cd57a7c78b2de86b37b2ebbab65e1/68747470733a2f2f696d672e736869656c64732e696f2f646973636f72642f3433333732393831373931383330383335322e7376673f6c6f676f3d646973636f7264)](https://discord.gg/HNePVyX3cp)

[![GitHub Test Status](https://github.com/owasp-amass/amass/workflows/tests/badge.svg)](https://github.com/owasp-amass/amass/workflows/tests/badge.svg) [![GoDoc](https://camo.githubusercontent.com/6412e6233dc0b1abe3c00f2d98ceafb10a64d5821cd0ff8a8bf0a723e966f66a/68747470733a2f2f706b672e676f2e6465762f62616467652f6769746875622e636f6d2f6f776173702d616d6173732f616d6173732f76343f75746d5f736f757263653d676f646f63)](https://pkg.go.dev/github.com/owasp-amass/amass/v4) [![License](https://camo.githubusercontent.com/59dc4e4b038a2824a870ba648fb3d569d3fdb245a7418368743898f803b221cc/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f6c6963656e73652d617061636865253230322d626c7565)](https://www.apache.org/licenses/LICENSE-2.0) [![Go Report](https://camo.githubusercontent.com/f0f8c61358e5a3eace3afb4629c15f92657f0c152e8b8d25744f5143cade3bfd/68747470733a2f2f676f7265706f7274636172642e636f6d2f62616467652f6769746875622e636f6d2f6f776173702d616d6173732f616d617373)](https://goreportcard.com/report/github.com/owasp-amass/amass) [![CodeFactor](https://camo.githubusercontent.com/8c951e0ad899496180474ff938ef85c2a13ff594f8abd7e9cb020ad58ffcfa42/68747470733a2f2f7777772e636f6465666163746f722e696f2f7265706f7369746f72792f6769746875622f6f776173702d616d6173732f616d6173732f6261646765)](https://www.codefactor.io/repository/github/owasp-amass/amass) [![Maintainability](https://camo.githubusercontent.com/4621e0028efc30e5bf4232515756ff99c4f125a74e2e022d07174697e0f8e39e/68747470733a2f2f6170692e636f6465636c696d6174652e636f6d2f76312f6261646765732f32333465343838356534303639353366393164302f6d61696e7461696e6162696c697479)](https://codeclimate.com/github/owasp-amass/amass/maintainability) [![codecov](https://camo.githubusercontent.com/822306c0ab4be10352c8778b70469b4d11e3032452f8a8d2484faf489661c479/68747470733a2f2f636f6465636f762e696f2f67682f6f776173702d616d6173732f616d6173732f6272616e63682f6d61737465722f67726170682f62616467652e7376673f746f6b656e3d7a6f504b78764c54316e)](https://codecov.io/gh/owasp-amass/amass)

The OWASP Amass Project performs network mapping of attack surfaces and external asset discovery using open source information gathering and active reconnaissance techniques.

**Information Gathering Techniques Used:**

|Technique|Data Sources|
|:--|:--|
|APIs|360PassiveDNS, Ahrefs, AnubisDB, BeVigil, BinaryEdge, BufferOver, BuiltWith, C99, Chaos, CIRCL, DNSDB, DNSRepo, Deepinfo, Detectify, FOFA, FullHunt, GitHub, GitLab, GrepApp, Greynoise, HackerTarget, Hunter, IntelX, LeakIX, Maltiverse, Mnemonic, Netlas, Pastebin, PassiveTotal, PentestTools, Pulsedive, Quake, SOCRadar, Searchcode, Shodan, Spamhaus, Sublist3rAPI, SubdomainCenter, ThreatBook, ThreatMiner, URLScan, VirusTotal, Yandex, ZETAlytics, ZoomEye|
|Certificates|Active pulls (optional), Censys, CertCentral, CertSpotter, Crtsh, Digitorus, FacebookCT|
|DNS|Brute forcing, Reverse DNS sweeping, NSEC zone walking, Zone transfers, FQDN alterations/permutations, FQDN Similarity-based Guessing|
|Routing|ASNLookup, BGPTools, BGPView, BigDataCloud, IPdata, IPinfo, RADb, Robtex, ShadowServer, TeamCymru|
|Scraping|AbuseIPDB, Ask, Baidu, Bing, CSP Header, DNSDumpster, DNSHistory, DNSSpy, DuckDuckGo, Gists, Google, HackerOne, HyperStat, PKey, RapidDNS, Riddler, Searx, SiteDossier, Yahoo|
|Web Archives|Arquivo, CommonCrawl, HAW, PublicWWW, UKWebArchive, Wayback|
|WHOIS|AlienVault, AskDNS, DNSlytics, ONYPHE, SecurityTrails, SpyOnWeb, WhoisXMLAPI|

---

## Installation [![Go Version](https://camo.githubusercontent.com/baa9af6a7feb3aef5d652b518fec0f82ae5640404678d9d15106cf1161dbabec/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f676f2d6d6f642f676f2d76657273696f6e2f6f776173702d616d6173732f616d617373)](https://golang.org/dl/) [![Docker Images](https://camo.githubusercontent.com/de2e205c3b13762c1235e51d3fd3e86fe9a6677f7ccc57757a93856e872086e4/68747470733a2f2f696d672e736869656c64732e696f2f646f636b65722f70756c6c732f6361666669782f616d6173732e737667)](https://hub.docker.com/r/caffix/amass) [![GitHub Downloads](https://camo.githubusercontent.com/94c08788c963201b93e1d79fff0f94afddd4df9e9d54129e5e360c717305adb5/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f646f776e6c6f6164732f6f776173702d616d6173732f616d6173732f6c61746573742f746f74616c2e737667)](https://github.com/owasp-amass/amass/releases/latest)

[](https://github.com/owasp-amass/amass#installation---)

> You can find some additional installation variations in the [Installation Guide](https://github.com/owasp-amass/amass/blob/master/doc/install.md).

### Prebuilt Packages

[](https://github.com/owasp-amass/amass#prebuilt-packages)

1. Simply unzip the [package](https://github.com/owasp-amass/amass/releases/latest)
2. Put the precompiled binary into your path
3. Start using OWASP Amass!

#### Homebrew

[](https://github.com/owasp-amass/amass#homebrew)

```shell
brew tap owasp-amass/amass
brew install amass
```

### Docker Container

[](https://github.com/owasp-amass/amass#docker-container)

1. Install [Docker](https://www.docker.com/)
2. Pull the Docker image by running `docker pull caffix/amass`
3. Run `docker run -v OUTPUT_DIR_PATH:/.config/amass/ caffix/amass enum -d example.com`

The volume argument allows the Amass graph database to persist between executions and output files to be accessed on the host system. The first field (left of the colon) of the volume option is the amass output directory that is external to Docker, while the second field is the path, internal to Docker, where amass will write the output files.

### From Source

[](https://github.com/owasp-amass/amass#from-source)

1. Install [Go](https://golang.org/doc/install) and setup your Go workspace
2. Download OWASP Amass by running `go install -v github.com/owasp-amass/amass/v4/...@master`
3. At this point, the binary should be in `$GOPATH/bin`

## Documentation [![GoDoc](https://camo.githubusercontent.com/6412e6233dc0b1abe3c00f2d98ceafb10a64d5821cd0ff8a8bf0a723e966f66a/68747470733a2f2f706b672e676f2e6465762f62616467652f6769746875622e636f6d2f6f776173702d616d6173732f616d6173732f76343f75746d5f736f757263653d676f646f63)](https://pkg.go.dev/github.com/owasp-amass/amass/v4)

[](https://github.com/owasp-amass/amass#documentation-)

Use the [Installation Guide](https://github.com/owasp-amass/amass/blob/master/doc/install.md) to get started.

Go to the [User's Guide](https://github.com/owasp-amass/amass/blob/master/doc/user_guide.md) for additional information.

See the [Tutorial](https://github.com/owasp-amass/amass/blob/master/doc/tutorial.md) for example usage.

See the [Amass Scripting Engine Manual](https://github.com/owasp-amass/amass/blob/master/doc/scripting.md) for greater control over your enumeration process.

## Corporate Supporters

[](https://github.com/owasp-amass/amass#corporate-supporters)

[![ZeroFox Logo](https://github.com/owasp-amass/amass/raw/master/images/zerofox_logo.png)](https://www.zerofox.com/) [![IPinfo Logo](https://github.com/owasp-amass/amass/raw/master/images/ipinfo_logo.png)](https://ipinfo.io/) [![WhoisXML API Logo](https://github.com/owasp-amass/amass/raw/master/images/whoisxmlapi_logo.png)](https://www.whoisxmlapi.com/)

## Testimonials

[](https://github.com/owasp-amass/amass#testimonials)

###  [![Accenture Logo](https://github.com/owasp-amass/amass/raw/master/images/accenture_logo.png) Accenture](https://www.accenture.com/)

[](https://github.com/owasp-amass/amass#-accenture)

_"Accenture’s adversary simulation team has used Amass as our primary tool suite on a variety of external enumeration projects and attack surface assessments for clients. It’s been an absolutely invaluable basis for infrastructure enumeration, and we’re really grateful for all the hard work that’s gone into making and maintaining it – it’s made our job much easier!"_

- Max Deighton, Accenture Cyber Defense Manager

###  [![Visma Logo](https://github.com/owasp-amass/amass/raw/master/images/visma_logo.png) Visma](https://www.visma.com/)

[](https://github.com/owasp-amass/amass#-visma)

_"For an internal red team, the organisational structure of Visma puts us against a unique challenge. Having sufficient, continuous visibility over our external attack surface is an integral part of being able to efficiently carry out our task. When dealing with hundreds of companies with different products and supporting infrastructure we need to always be on top of our game._

_For years, OWASP Amass has been a staple in the asset reconnaissance field, and keeps proving its worth time after time. The tool keeps constantly evolving and improving to adapt to the new trends in this area."_

- Joona Hoikkala ([@joohoi](https://github.com/joohoi)) & Alexis Fernández ([@six2dez](https://github.com/six2dez)), Visma Red Team

## References [![DEF CON 30 Recon Village](https://camo.githubusercontent.com/79f0c8a17e7ea8f747420a66fd81809006ffe52c1dcfd6f4efc00c65be265ea9/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f646566636f6e25323033302d7265636f6e25323076696c6c6167652d6c69676874677265792e737667)](https://twitter.com/jeff_foley/status/1562246069278445568/photo/1) [![DEF CON 28 Red Team Village](https://camo.githubusercontent.com/b2abecc008e0a9d4672c933767b8dd61c33ea7395e12c64483004cee80810b8c/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f646566636f6e25323032382d7265642532307465616d25323076696c6c6167652d7265642e737667)](https://www.youtube.com/c/RedTeamVillage/featured) [![DEF CON 27 Demo Labs](https://camo.githubusercontent.com/696d4ea51be34db9eb12a132ecfebfbd66c91b655d334d177e5d6c16b82b9788/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f646566636f6e25323032372d64656d6f2532306c6162732d707572706c652e737667)](https://www.defcon.org/html/defcon-27/dc-27-demolabs.html)

[](https://github.com/owasp-amass/amass#references---)

Did you write a blog post, magazine article or do a podcast about OWASP Amass? Or maybe you held or joined a conference talk or meetup session, a hacking workshop or public training where this project was mentioned?

Add it to our ever-growing list of [REFERENCES.md](https://github.com/owasp-amass/amass/blob/master/REFERENCES.md) by forking and opening a Pull Request!

### Top Mentions

[](https://github.com/owasp-amass/amass#top-mentions)

- [Phillip Wylie | Securing APIs Through External Attack Surface Management (EASM)](https://www.uscybersecurity.net/csmag/securing-apis-through-external-attack-surface-management-easm/)
- [Kento Stewart | Mapping Your External Perimeter during an Incident with OWASP Amass](https://www.youtube.com/watch?v=23tQ4zLA-9A)
- [WhoisXML API | OWASP Amass and WhoisXML API Are Now Integration Partners](https://main.whoisxmlapi.com/success-stories/cyber-security-solutions/owasp-amass-and-whoisxml-api-are-now-integration-partners)
- [Intigriti | Hacker tools: Amass – Hunting for Subdomains](https://blog.intigriti.com/2021/06/08/hacker-tools-amass-hunting-for-subdomains)
- [Hakluke | Guide to Amass — How to Use Amass More Effectively for Bug Bounties](https://medium.com/@hakluke/haklukes-guide-to-amass-how-to-use-amass-more-effectively-for-bug-bounties-7c37570b83f7)
- [SecurityTrails | OWASP Amass: A Solid Information Gathering Tool](https://securitytrails.com/blog/owasp-amass)
- [TrustedSec | Upgrade Your Workflow, Part 1: Building OSINT Checklists](https://www.trustedsec.com/blog/upgrade-your-workflow-part-1-building-osint-checklists/)
- [SANS ISC | Offensive Tools Are For Blue Teams Too](https://isc.sans.edu/forums/diary/Offensive+Tools+Are+For+Blue+Teams+Too/25842/)
- [Jason Haddix | LevelUp 0x02 - The Bug Hunters Methodology v3(ish)](https://www.youtube.com/watch?v=Qw1nNPiH_Go)
- [Daniel Miessler | amass — Automated Attack Surface Mapping](https://danielmiessler.com/study/amass/)
- [Dionach | How to Use OWASP Amass: An Extensive Tutorial](https://www.dionach.com/blog/how-to-use-owasp-amass-an-extensive-tutorial/)
- [nynan | How to **Actually** Use Amass More Effectively — Bug Bounty](https://medium.com/@nynan/how-to-actually-use-amass-more-effectively-bug-bounty-59e83900de02)
- [ToolWar | Extreme Subdomain Enumeration/Scanning on Windows : OWASP Amass](https://www.youtube.com/watch?v=mEQnVkSG19M)

## Contributing [![Contribute Yes](https://camo.githubusercontent.com/706f76cf5e588f3a5a55185be5a0bd9d3784eaddaf2e7462847a3a23de6d5b51/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f636f6e747269627574652d7965732d627269676874677265656e2e737667)](https://github.com/owasp-amass/amass/blob/master/CONTRIBUTING.md) [![Chat on Discord](https://camo.githubusercontent.com/fd0fcd01a0b3c9370f56bf49bd67f5d9c13cd57a7c78b2de86b37b2ebbab65e1/68747470733a2f2f696d672e736869656c64732e696f2f646973636f72642f3433333732393831373931383330383335322e7376673f6c6f676f3d646973636f7264)](https://discord.gg/HNePVyX3cp)

[](https://github.com/owasp-amass/amass#contributing--)

We are always happy to get new contributors on board! Please check [CONTRIBUTING.md](https://github.com/owasp-amass/amass/blob/master/CONTRIBUTING.md) to learn how to contribute to our codebase, and join our [Discord Server](https://discord.gg/HNePVyX3cp) to discuss current project goals.

## Troubleshooting [![Chat on Discord](https://camo.githubusercontent.com/fd0fcd01a0b3c9370f56bf49bd67f5d9c13cd57a7c78b2de86b37b2ebbab65e1/68747470733a2f2f696d672e736869656c64732e696f2f646973636f72642f3433333732393831373931383330383335322e7376673f6c6f676f3d646973636f7264)](https://discord.gg/HNePVyX3cp)

[](https://github.com/owasp-amass/amass#troubleshooting-)

If you need help with installation and/or usage of the tool, please join our [Discord server](https://discord.gg/HNePVyX3cp) where community members can best help you.

🛑 **Please avoid opening GitHub issues for support requests or questions!**

## Licensing [![License](https://camo.githubusercontent.com/59dc4e4b038a2824a870ba648fb3d569d3fdb245a7418368743898f803b221cc/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f6c6963656e73652d617061636865253230322d626c7565)](https://www.apache.org/licenses/LICENSE-2.0)

[](https://github.com/owasp-amass/amass#licensing-)

This program is free software: you can redistribute it and/or modify it under the terms of the [Apache license](https://github.com/owasp-amass/amass/blob/master/LICENSE). OWASP Amass and any contributions are Copyright © by Jeff Foley 2017-2023. Some subcomponents have separate licenses.

[![Network graph](https://github.com/owasp-amass/amass/raw/master/images/network_06092018.png "Amass Network Mapping")](https://github.com/owasp-amass/amass/blob/master/images/network_06092018.png)

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/owasp-amass/amass). Be sure to check out the original post for more details.

# How to Use OWASP Amass: An Extensive Tutorial

**Author:** Nick Gkogkos – Lead Consultant

Whether you are a penetration tester, an auditor, a security researcher or the CISO/IT manager, you may have several valid reasons for mapping out the external attack surface of an organisation. This process is also referred to as reconnaissance or information gathering.

[The OWASP Amass project](https://www.owasp.org/index.php/OWASP_Amass_Project)  (Amass) can help with this to a large extent depending on your requirements. In this blog post, I will aim to demonstrate how one can use Amass to discover majority of an organisation’s externally exposed assets.

The focus will be on performing continuous subdomain discovery exercises. I have broken this blog post into different sections to make it easier to get to grips with the various functions of Amass. It should be noted that there may be assets out there that are not mapped to a domain and you will need to employ other techniques to uncover them, such as running network scans over the IP ranges owned by the organisation. Although I will not fully demonstrate how to use all the functions offered by Amass, I am hoping that this blog will cover enough to give you a kick-start in mastering Amass.

## Why OWASP Amass?

A high number of open-source tools and software are available for enumerating subdomains, Autonomous System Numbers (ASNs) and other assets owned by an organisation. Although most of these tools are great in utilising specific methods, they are not always actively maintained and updated to keep up with the latest techniques and methodologies. So to speak the truth, most of the available tools are not complete and solely relying on these could give a false sense of security or lead to missing vulnerable assets. The reality is that subdomains can be disclosed anywhere nowadays, such as on social media, Pastebin, source code repositories, HTTP headers and so on.

Amass is backed by OWASP, which should provide prestige and confidence in the results. It is actively maintained and will likely be supported for a long time, meaning any future bugs will be resolved. Additionally, the adoption rate of Amass is high which potentially means better data consistency and integration with other tools. As such, it can constitute a better and more trustworthy tool to use in proof of concepts and engagements, and it may be easier to convince your clients or manager to use it for periodical mapping of the organisation’s attack surface.

There are a number of more technical reasons, which I will explain below and demonstrate in more detail later:

- Comes with 5 subcommands, in other words functions:
    - amass intel – Discover targets for enumerations
    - amass enum – Perform enumerations and network mapping
    - amass viz – Visualize enumeration results
    - amass track – Track differences between enumerations
    - amass db – Manipulate the Amass graph database
- Amass’ subcommands can be used in conjunction, in some cases, which could allow you to create scripts that perform multiple Amass operations.
- Supports 55 sources, such as APIs and websites, at the time of writing as part of its subdomain discovery and information gathering techniques. These can be listed using the following command:
    - amass enum -list
    - An example of some of these is shown below

AlienVault,ArchiveIt,ArchiveToday,Arquivo,Ask,Baidu,BinaryEdge,Bing,BufferOver,Censys,CertSpotter,CIRCL,CommonCrawl,Crtsh,**[…]**,ViewDNS,VirusTotal,Wayback,WhoisXML,Yahoo (full list [here](https://github.com/OWASP/Amass))

- It employs various information gathering techniques for DNS enumeration
    - Brute-force of subdomains using a domain name wordlists and alteration wordlists
    - Identify subdomains by reading SSL/TLS certificates, performing DNS zone transfers or checking certificate transparency logs
    - Recursive subdomain discovery on identified domains
    - Hashcat-style masks for brute-force of subdomains (this can be very useful if you have internal information on naming conventions and so on)
- It can be configured using a configuration file which makes it easy to maintain, use or integrate with scripts

Lastly, I will not be going into the details of installing Amass in this blog post, but if you are interested, you can do so in a number of ways. You can compile from source if you have a properly configured Golang environment (Go >= 1.13), or run it using Docker, or install it as a package if one is available for your distribution. Detailed installation instructions are available here [https://github.com/OWASP/Amass/blob/master/doc/install.md](https://github.com/OWASP/Amass/blob/master/doc/install.md).

## Amass Intel

The Amass intel subcommand, or module if you want, can aid with collecting open source intelligence on the organisation and allow you to find further root domain names associated with the organisation. To see the available options of this subcommand, simply type it at the terminal:

**$ amass intel**
[...]
Usage: amass intel [options] [-whois -d DOMAIN] [-addr ADDR -asn ASN -cidr CIDR]
  -active
        Attempt certificate name grabs
  -addr value
        IPs and ranges (192.168.1.1-254) separated by commas
  -asn value
        ASNs separated by commas (can be used multiple times)
[...]

It is probably worth noting at this point that another great perk of Amass is that all the subcommands attempt to maintain argument consistency.

This subcommand will use a number of information gathering techniques and data sources by default, such as WHOIS and IPv4Info, in order to obtain intelligence and parent domains owned by the organisation, unless these are explicitly disabled in Amass’ configuration file. An example Amass configuration file is available [on the GitHub repository](https://github.com/OWASP/Amass/blob/master/examples/config.ini).

**$ amass intel -d owasp.org -whois**
appseceu.com
owasp.com
appsecasiapac.com
appsecnorthamerica.com
appsecus.com
[...]
owasp.org
appsecapac.com
appsecla.org
[...]

You can also confirm some of the results above by browsing to data sources manually. In the screenshot below, I have performed a reverse Whois search for “OWASP Foundation” and found similar domains against ViewDNS (which is also part of Amass’ data sources):

[https://viewdns.info/reversewhois/?q=OWASP+Foundation](https://viewdns.info/reversewhois/?q=OWASP+Foundation)

![OWASP Amass information gathering techniques](https://www.dionach.com/wp-content/uploads/2020/01/OWASP-Amass-Intel-tutorial.png.webp)

When performing searches with amass intel you can always run it with more configuration options, such as the “-active” argument which will attempt zone transfers and actively scan to fetch SSL/TLS certificates to extract information. As with any engagement, ensure you are authorised to perform active searches against the target at the time.

It is worth noting at this point that some configuration flags will not work along with others and in this case Amass will simply ignore them.

Amass’ findings will not always be accurate, this is due to several reasons, for example the data sources used by Amass may not be consistent or up to data. Amass attempts to further validate the information using DNS queries, and more validation techniques will be implemented in the future. Although Amass does a good job, users should still perform further verification checks on results that do not appear to be related to the target. This can be performed using a variety of methods such as:

- Use utilities to resolve the domains (e.g. dig, nslookup)
- Perform WHOIS lookups to confirm organisational details
- Search findings, such as parent domains, on search engines

You can also look for organisational names with Amass which could return ASN IDs assigned to the target, an example is shown below:

**$ amass intel -org 'Example Ltd'**
111111, MAIN_PRODUCT – Example Ltd
222222, SECONDARY_PRODUCT - Example Ltd
[...]

Please note that the above data is fictious for demonstration purposes. Retrieved ASN IDs could then be fed back into Amass. The below command attempts to retrieve parent domains on the specified ASN ID and return them along with the IP address they resolve to (127.0.0.1 in this case for demonstration purposes):

**$ amass intel -active -asn 222222 -ip**
some-example-ltd-domain.com 127.0.0.1
[...]  
  

## Amass Enum

Let’s move onto Amass enum, which is where most of Amass’ powerful capabilities live. Amass enum allows you to perform DNS enumeration and mapping of the target in order to determine the attack surface exposed by organisations. The enumeration findings are stored in a graph database, which will be located in Amass’ default output folder or the specified output directory with “-dir” flag. This is also the case with other Amass subcommands.

### Run Amass under Passive or Active Configuration

Amass enum can be executed under the context of a passive or an active configuration mode. The passive mode is much quicker, but Amass will not validate DNS information, for example by resolving the subdomains. You can run it passively using the “-passive” flag and you will not be able to enable many techniques or configurations, such as DNS resolution and validation. There are several reasons for choosing passive mode over the active mode at times, for example:

- You need to know all possible subdomains that have been used and may be reused in the future, perhaps because you need to constantly monitor the target’s attack surface for changes or because you are working on a phishing engagement and looking for subdomains.
- Your perimeter’s security testing process validates DNS information at a later stage and need Amass results quickly.
- Due to a security engagement’s constraints or requirements, you can only perform passive information gathering.

In the below example, I am passively searching for subdomains on owasp.org while asking Amass to display the data sources where it found each subdomain:

**$ amass enum -passive -d owasp.org -src**
[...]
[ThreatCrowd]     update-wiki.owasp.org
[...]
BufferOver]      my.owasp.org
[Crtsh]           www.lists.owasp.org
[Crtsh]           www.ocms.owasp.org
[...]
Querying VirusTotal for owasp.org subdomains
Querying Yahoo for owasp.org subdomains
[...]

It is worth stating at this point that although Amass intel will help gather IP ranges, ASNs and parent domains owned by an organisation, Amass enum will identify all subdomains. This subdomain enumeration is completed in under 2 minutes on my test machine. Here’s a slightly modified screenshot showing the results of this enumeration:

![OWASP Amass enum tutorial for subdomain discovery](https://www.dionach.com/wp-content/uploads/2020/01/OWASP-Amass-enum-tips-and-tricks.png.webp)

Using Amass in active configuration mode means that you will have more accurate results and more assets may be discovered as you can enable all DNS enumeration techniques. It should be noted that by “active configuration mode” I am not strictly referring to the “-active” flag which enables zone transfers and port scanning of SSL/TLS services and grabbing their certificates to extract any subdomains from certificate fields (e.g. Common Name).

The below command (a detailed explanation of which follows below) can be considered active overall as it performs subdomain brute-forcing in multiple ways (wordlist, masks, etc.) along with the “-active” flag being enabled. All findings will be validated by Amass using the default or the specified resolvers:

**$ amass enum -active -d owasp.org -public-dns -brute -w /root/dns_lists/deepmagic.com-top50kprefixes.txt -src -ip -dir amass4owasp -config /root/amass/config.ini -o amass_results_owasp.txt**

![Performing subdomain discovery exercise with OWASP Amass](https://www.dionach.com/wp-content/uploads/2020/01/How-to-use-OWASP-Amass-tutorial.png.webp)

The command I’ve used above specifies that the Amass graph database along with log files will be stored at “./amass4owasp”. I’ve also asked Amass to display the data sources for each identified subdomain and the IP address(es) it resolves to with the “-src” and “-ip” flags respectively. I have provided Amass with the [deepmagic](https://github.com/danielmiessler/SecLists/tree/master/Discovery/DNS) DNS wordlist with the “-w” argument, and also specified the location of the config.ini file with “-config” and the output with “-o”.

While the command above is hopefully straightforward, I would like to provide some further notes:

- As a result of the “-public-dns” argument, Amass will grab DNS resolvers from [https://public-dns.info](https://public-dns.info/). Without this argument, it would have checked within my config.ini file or use the default resolvers embedded within Amass. Amass attempts to validate Public DNS resolvers, as shown in the snippet from the “amass.log” file below:

![Performing subdomain discovery exercise with OWASP Amass](https://www.dionach.com/wp-content/uploads/2020/01/OWASP-Amass-tutorial.png.webp)

- We could have specified all these configurations in a config.ini file and provide this to Amass with “-config”. It’s worth stating at this point that command-line arguments will take priority over what’s specified in the config.ini file. So, if you are disabling brute-force in the config.ini file, but supply the “-brute” argument on the command line, then brute-force techniques will be used.
- The command above, unless explicitly disabled with the use of the “-norecursive”, will perform recursive DNS enumeration on subdomains identified by default.

Please note that you can specify your own DNS resolvers either with the use of the “-r” and “-rf” flags or within the config.ini file. Using the “-r” flag you can specify the IP addresses of DNS resolvers at the command, while with the “-rf” you can specify a file containing these.

At this point, you should also keep in mind that if you are performing multiple Amass operations within short periods of time from the same IP, the IP may be permanently blocked from some sources that Amass is scraping such as the Google/Yahoo search engines.

If you require multiple instances of Amass to be executed at the same time, you may be able to achieve this on the same server; however, bear in mind that Amass is powerful and will consume a lot of resources. Additionally, you will need to use the “dir” flag to specify separate output directories, and hence graph databases, when running multiple instances of Amass.

To conclude this section in a more interesting way, let’s assume that for some reason the OWASP organisation tends to create subdomains with “zzz” prefixes, such as zzz-dev.owasp.org. You can leverage Amass’ hashcat-style wordlist mask feature to brute-force all the combinations of “zzz-[a-z][a-z][a-z].owasp.org” using the following command:

**$ amass enum -d owasp.org -norecursive -noalts -wm "zzz-?l?l?l" -dir amass4owasp**

Note that in the configuration above I have explicitly disabled recursive DNS enumerations and alterations, as I was interested in quicker results using the mask only.

Finally, you can always check Amass’ log file within the output folder to ensure your configuration is working as expected:

![OWASP Amass advanced subdomain discovery with hashcat masks](https://www.dionach.com/wp-content/uploads/2020/01/OWASP-Amass-enum-logging.png.webp)

## Amass Track

Amass track is the second most useful subcommand in my opinion. It helps compare results across enumerations performed against the same target and domains. An example is the below command which compares the last 2 enumerations performed against “owasp.org”. This is done by specifying the same Amass output folder and database we have been using in this blog. The most interesting lines are the ones starting with the “Found” keyword and this means that the subdomain was not identified in previous enumerations.

**$ amass track  -config /root/amass/config.ini -dir amass4owasp -d owasp.org -last 2**

![OWASP Amass Track image](https://www.dionach.com/wp-content/uploads/2020/01/OWASP-Amass-Track.png.webp)

For organisations and researchers performing Amass discoveries periodically, Amass track can be really useful if used along with alerting. Although alerting is not yet natively supported by Amass at the time of writing, implementation of message notifications on identified track changes is in the development pipeline. Until this is implemented, you could investigate creating a custom solution that alerts the relevant people in your organisation by filtering the Amass track results. This could be done with Slack webhooks for example.

Organisations can also use this feature to ensure that newly deployed services do not evade quality control processes, vulnerability management, and asset inventories.

## Amass Viz and Amass DB

I would also like to briefly mention the other 2 Amass subcommands:

Amass db

You can use this subcommand in order to interact with an Amass graph database, either the default or the one specified with the “-dir” flag.

For example, the below command would list all the different enumerations you have performed in terms of the given domains and are stored in the “amass4owasp” graph database:

**$ amass db -dir amass4owasp -list**

Next, with a command similar to the below you could retrieve the assets identified during that enumeration – in this case enumeration 1:

**$ amass db -dir amass4owasp -d owasp.org -enum 1 -show**

You may want to maintain the same Amass output folder for statistical or historical purposes, through which you perform all the subdomain enumeration exercises, as Amass track can be used only against the same graph database and output folder.

  
Amass Viz

The Amass viz subcommand allows you to visualize all the gathered information (stored in the Amass graph database) for a target in a number of ways. Results can also be imported into Maltego for further OSINT (Open-Source Intelligence) analysis.

The below command generates a d3-force HTML graph based on the graph database stored within the “amass4owasp” folder:

**$ amass viz -d3 -dir amass4owasp**

![Using OWASP Amass with Maltego and for Red Teaming](https://www.dionach.com/wp-content/uploads/2020/01/OWASP-Amass-for-Red-Teaming.png.webp)

## Automating OWASP Amass Discovery Exercises

The discussed techniques could be used in conjunction with periodic information gathering and subdomain enumeration exercises. You could then write a script to send alerts when a new asset is discovered. Depending on your needs, here are some ideas:

- Use Amass intel to look for ASN IDs periodically, then use the ASN IDs to perform parent domain discovery, and finally use the identified parent domains with Amass enum running active searches in order to identify new externally exposed subdomains and assets;
- Use Amass enum with passive searches to retrieve new subdomains from Amass’ data sources in order to create a list of the organisation’s assets by providing the initial parent domains. These could be fed into vulnerability scanning tools (which will also perform DNS resolution) or could be added in scope for your organisation’s security engagements.

If you are planning on automating Amass discovery exercises, I highly recommend you invest time into configuring the “config.ini” file. For instance, you could have one amass “config.ini” file for quick passive subdomain discovery exercises that occur every few hours if you are searching a large network/organisation, and one for deeper and more specific scanning. In the example below, I provide an example script written in GNU Bash showing how you could automate Amass:

1. APP_TOKEN="$1"
2. USER_TOKEN="$2"

3. amass enum -src -active -df ./domains_to_monitor.txt -config ./regular_scan.ini -o ./amass_results.txt -dir ./regular_amass_scan -brute -norecursive
4. RESULT=$(amass track -df ./domains_to_monitor.txt -config ./regular_scan.ini -last 2 -dir ./regular_amass_scan | grep Found | awk '{print $2}')

5. FINAL_RESULT=$(while read -r d; do if grep --quiet "$d" ./all_domains.txt; then continue; else echo "$d"; fi; done <<< $RESULT)

6. if [[ -z "$FINAL_RESULT" ]];
7. FINAL_RESULT="No new subdomains were found"
8. else
9. echo "$FINAL_RESULT" >> ./all_domains.txt
10. fi
11. wget https://api.pushover.net/1/messages.json --post-data="token=$APP_TOKEN&user=$USER_TOKEN&message=$FINAL_RESULT&title=$TITLE" -qO- > /dev/null 2>&1 &

The script leverages a mobile application that sends push-notifications to my phone using the pushover.net API. This is achieved using the wget tool to make API requests that send a notification to my phone with the new subdomains, as shown in lines 1,2 and 11. You could implement similar functionality using Slack’s or Discord’s webhooks. The command in line 3 launches a thorough Amass enum discovery. Line 4 uses Amass track to compare the last two enumerations and identify any new subdomains while lines 5 and 9 accumulate all the subdomains identified within the “all_domains.txt” file and compare. This is required because in some cases subdomains may be active and/or inactive at different time periods and comparing only the last two enumerations may not be enough. Lines 6 to 10 ensure that the relevant push notification message is sent to my phone while also saving any new subdomains to the “all_domains.txt” local file for future reference.

Please note that the above script is a quick script I wrote and is only meant to serve as an example. It is by no means perfect and bug-free, and you will have to modify and adjust it based on your requirements and environment.

In closing, OWASP Amass is a tool that is becoming increasingly popular. I highly recommend that you incorporate Amass in your workflow/processes if you have information gathering and subdomain discovery requirements, and stay tuned as more and more features and improvements will be added with every release. Finally, you can always refer to Amass’ detailed user guide at:  
[https://github.com/OWASP/Amass/blob/master/doc/user_guide.md](https://github.com/OWASP/Amass/blob/master/doc/user_guide.md)

**Credit:** This information was adapted from an excellent guide on [Dionach](https://www.dionach.com/en-us/how-to-use-owasp-amass-an-extensive-tutorial/). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/tGitZO8EkMI?si=ToyIZ6yAd2QVMnsW&amp;start=2455" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=tGitZO8EkMI). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/skoPPyRneCk?si=hQft5L8jFVsn0YY0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=skoPPyRneCk). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/2IsagoR9eCQ?si=KNEL5GQYvly1-hsW" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=2IsagoR9eCQ). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/On411Oyjlys?si=cTA1Tp6yw2vRcTQa" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=On411Oyjlys). Be sure to check out the original post for more details.

