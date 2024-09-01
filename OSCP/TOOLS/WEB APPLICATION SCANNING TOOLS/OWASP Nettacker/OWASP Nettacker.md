# OWASP Nettacker

[](https://github.com/OWASP/Nettacker#owasp-nettacker)

[![Build Status](https://github.com/OWASP/Nettacker/workflows/CI/badge.svg?branch=master)](https://github.com/OWASP/Nettacker/actions/workflows/CI.yml) [![Apache License](https://camo.githubusercontent.com/077d039abdb02d1e3391daf2b1d3acc5a7e0d54c3a375aee8df4bb99ed4e5dcd/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f4c6963656e73652d41706163686525323076322d677265656e2e737667)](https://github.com/OWASP/Nettacker/blob/master/LICENSE) [![Twitter](https://camo.githubusercontent.com/b7548897210cf0b6fe0a548627a0c6e31c84d02305a2372f24d626d31e5c6814/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f547769747465722d40696f747363616e2d626c75652e737667)](https://twitter.com/iotscan) [![GitHub contributors](https://camo.githubusercontent.com/0ce9e0cba864984fdf17d2b95f2cfc28d5347f715e7717a24bbf166faab1a954/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f636f6e7472696275746f72732f4f574153502f4e65747461636b6572)](https://camo.githubusercontent.com/0ce9e0cba864984fdf17d2b95f2cfc28d5347f715e7717a24bbf166faab1a954/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f636f6e7472696275746f72732f4f574153502f4e65747461636b6572) [![Documentation Status](https://camo.githubusercontent.com/5b1a853d1139a817f8a7100f83773d79bcb00f6581230febb5545e054b8200e1/68747470733a2f2f72656164746865646f63732e6f72672f70726f6a656374732f6e65747461636b65722f62616467652f3f76657273696f6e3d6c6174657374)](https://nettacker.readthedocs.io/en/latest/?badge=latest) [![repo size](https://camo.githubusercontent.com/8b207a5577a4fdacda288ed9e939638a87e1bdfc6b1e0490defea7d25fe2a6db/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f7265706f2d73697a652f4f574153502f4e65747461636b6572)](https://github.com/OWASP/Nettacker)

[![](https://raw.githubusercontent.com/OWASP/Nettacker/master/nettacker/web/static/img/owasp-nettacker.png)](https://raw.githubusercontent.com/OWASP/Nettacker/master/nettacker/web/static/img/owasp-nettacker.png)[![](https://raw.githubusercontent.com/OWASP/Nettacker/master/nettacker/web/static/img/owasp.png)](https://raw.githubusercontent.com/OWASP/Nettacker/master/nettacker/web/static/img/owasp.png)

**DISCLAIMER**

- _**THIS SOFTWARE WAS CREATED FOR AUTOMATED PENETRATION TESTING AND INFORMATION GATHERING. YOU MUST USE THIS SOFTWARE IN A RESPONSIBLE AND ETHICAL MANNER. DO NOT TARGET SYSTEMS OR APPLICATIONS WITHOUT OBTAINING PERMISSIONS OR CONSENT FROM THE SYSTEM OWNERS OR ADMINISTRATORS. CONTRIBUTORS WILL NOT BE RESPONSIBLE FOR ANY ILLEGAL USAGE.**_

[![2018-01-19_0-45-07](https://user-images.githubusercontent.com/7676267/35123376-283d5a3e-fcb7-11e7-9b1c-92b78ed4fecc.gif)](https://user-images.githubusercontent.com/7676267/35123376-283d5a3e-fcb7-11e7-9b1c-92b78ed4fecc.gif)

OWASP Nettacker project is created to automate information gathering, vulnerability scanning and eventually generating a report for networks, including services, bugs, vulnerabilities, misconfigurations, and other information. This software **will** utilize TCP SYN, ACK, ICMP, and many other protocols in order to detect and bypass Firewall/IDS/IPS devices. By leveraging a unique method in OWASP Nettacker for discovering protected services and devices such as SCADA. It would make a competitive edge compared to other scanners making it one of the best.

- OWASP Page: [https://owasp.org/www-project-nettacker/](https://owasp.org/www-project-nettacker/)
- Wiki: [https://github.com/OWASP/Nettacker/wiki](https://github.com/OWASP/Nettacker/wiki)
- Slack: #project-nettacker on [https://owasp.slack.com](https://owasp.slack.com/)
- Installation: [https://github.com/OWASP/Nettacker/wiki/Installation](https://github.com/OWASP/Nettacker/wiki/Installation)
- Usage: [https://github.com/OWASP/Nettacker/wiki/Usage](https://github.com/OWASP/Nettacker/wiki/Usage)
- GitHub: [https://github.com/OWASP/Nettacker](https://github.com/OWASP/Nettacker)
- Docker Image: [https://hub.docker.com/r/owasp/nettacker](https://hub.docker.com/r/owasp/nettacker)
- How to use the Dockerfile: [https://github.com/OWASP/Nettacker/wiki/Installation#docker](https://github.com/OWASP/Nettacker/wiki/Installation#docker)
- OpenHub: [https://www.openhub.net/p/OWASP-Nettacker](https://www.openhub.net/p/OWASP-Nettacker)
- **Donate**: [https://owasp.org/donate/?reponame=www-project-nettacker&title=OWASP+Nettacker](https://owasp.org/donate/?reponame=www-project-nettacker&title=OWASP+Nettacker)
- **Read More**: [https://www.secologist.com/open-source-projects](https://www.secologist.com/open-source-projects)

---

# Quick Setup & Run

[](https://github.com/OWASP/Nettacker#quick-setup--run)

```shell
$ docker-compose up -d && docker exec -it nettacker-nettacker-1 /bin/bash
# poetry run python nettacker.py -i owasp.org -s -m port_scan
```

- Results are accessible from your ([https://localhost:5000](https://localhost:5000/)) or [https://nettacker-api.z3r0d4y.com:5000/](https://nettacker-api.z3r0d4y.com:5000/) (pointed to your localhost)
- The local database is `.data/nettacker.db` (sqlite).
- Default results path is `.data/results`
- `docker-compose` will share your nettacker folder, so you will not lose any data after `docker-compose down`
- To see the API key in you can run `docker logs nettacker_nettacker_1`.
- More details and setup without docker [https://github.com/OWASP/Nettacker/wiki/Installation](https://github.com/OWASP/Nettacker/wiki/Installation)

---

# Thanks to our awesome contributors

[](https://github.com/OWASP/Nettacker#thanks-to-our-awesome-contributors)

[![Awesome Contributors](https://camo.githubusercontent.com/de479ab91cba18f66d12356dd16ce41095e978159cd1957bdd9cbe26b17003e9/68747470733a2f2f636f6e747269622e726f636b732f696d6167653f7265706f3d4f574153502f4e65747461636b6572)](https://camo.githubusercontent.com/de479ab91cba18f66d12356dd16ce41095e978159cd1957bdd9cbe26b17003e9/68747470733a2f2f636f6e747269622e726f636b732f696d6167653f7265706f3d4f574153502f4e65747461636b6572)

---

## _**IoT Scanner**_

[](https://github.com/OWASP/Nettacker#iot-scanner)

- Python Multi Thread & Multi Process Network Information Gathering Vulnerability Scanner
- Service and Device Detection ( SCADA, Restricted Areas, Routers, HTTP Servers, Logins and Authentications, None-Indexed HTTP, Paradox System, Cameras, Firewalls, UTM, WebMails, VPN, RDP, SSH, FTP, TELNET Services, Proxy Servers and Many Devices like Juniper, Cisco, Switches and many more… )
- Asset Discovery & Network Service Analysis
- Services Brute Force Testing
- Services Vulnerability Testing
- HTTP/HTTPS Crawling, Fuzzing, Information Gathering and …
- HTML, JSON, CSV and Text Outputs
- API & WebUI
- This project is at the moment in research and development phase
- Thanks to Google Summer of Code Initiative and all the students who contributed to this project during their summer breaks:

[![](https://camo.githubusercontent.com/d672330a14488145bfc61009f081620f1c45a4ec22826803edfe6cb8b349aefd/68747470733a2f2f626574616e6577732e636f6d2f77702d636f6e74656e742f75706c6f6164732f323031362f30332f766572746963616c2d47536f432d6c6f676f2e6a7067)](https://camo.githubusercontent.com/d672330a14488145bfc61009f081620f1c45a4ec22826803edfe6cb8b349aefd/68747470733a2f2f626574616e6577732e636f6d2f77702d636f6e74656e742f75706c6f6164732f323031362f30332f766572746963616c2d47536f432d6c6f676f2e6a7067)

---

## Stargazers over time

[](https://github.com/OWASP/Nettacker#stargazers-over-time)

[![Stargazers over time](https://camo.githubusercontent.com/b0dac47ada32b5faaea5962a0b5d277a1853dcaec7f1464efc55a13f962b6701/68747470733a2f2f7374617263686172742e63632f4f574153502f4e65747461636b65722e737667)](https://starchart.cc/OWASP/Nettacker)

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/OWASP/Nettacker). Be sure to check out the original post for more details.

# OWASP Nettacker

OWASP Nettacker project was created to automate information gathering, vulnerability scanning and in general to aid penetration testing engagements. Nettacker is able to run various scans using a variety of methods and generate scan reports(in HTML/TXT/JSON/CSV format) for applications and networks, including discovering open ports, services, bugs, vulnerabilities, misconfigurations, default credentials, subdomains, etc. Nettacker can be run as a command-line utility (including running as a Docker container), API, Web GUI mode or as Maltego transforms.

OWASP Nettacker is written in 100% Python and does not rely on launching any external tools.

OWASP Nettacker can also help you find instances of critically vulnerable MOVEit Transfer, Citrix Netscaler, Ivanti ICS/EPMM services and other vulnerabilities in your network.

**Latest Releases:**

- [v0.3.3](https://github.com/OWASP/Nettacker/releases/tag/0.3.3): On January 20th, 2024 OWASP Nettacker [v0.3.3](https://github.com/OWASP/Nettacker/releases/tag/0.3.3) was released with new modules to scan for the latest Ivanti ICS CVE-2023-46805 vulnerability, Ivanti EPMM CVE-2023-35082, WordPress POST SMTP plugin CVE-2023-6875 and modules to help you find unpatched Citrix Netscaler & Ivanti devices
- [v0.3.2](https://github.com/OWASP/Nettacker/releases/tag/0.3.2): On October 31st, 2023 OWASP Nettacker [v0.3.2](https://github.com/OWASP/Nettacker/releases/tag/0.3.2) was released with new modules to scan networks for Critical vulnerabilities such as: Adobe Coldfusion CVE-2023-26360, Atlassian Confluence CVE-2023-22515 and Citrix Netscaler CVE-2023-4966 (aka “CitrixBleed”)
- [v0.3.1](https://github.com/OWASP/Nettacker/releases/tag/0.3.1) On July 5th, 2023 OWASP Nettacker [v0.3.1](https://github.com/OWASP/Nettacker/releases/tag/0.3.1) released with new modules to scan for MOVEit Transfer instances and the latest Citrix CVE-2023-24488:

### Documentation

- [Installation](https://github.com/OWASP/Nettacker/wiki/Installation)
- [Usage](https://github.com/OWASP/Nettacker/wiki/Usage)
- [Wiki](https://github.com/OWASP/Nettacker/wiki)
- **[Read More](https://www.secologist.com/open-source-projects)**

### Code Repository

- [OWASP Nettacker on GitHub](https://github.com/OWASP/Nettacker)

### Docker Images

- [OWASP Nettacker Docker Images on DockerHub](https://hub.docker.com/r/owasp/nettacker/tags)

### Contributing

- [Developers Guide](https://github.com/OWASP/Nettacker/wiki/Developers)

### Quick Demo - CLI

[![asciicast](https://github.com/OWASP/www-project-nettacker/raw/master/assets/images/389414.svg)](https://asciinema.org/a/389414)

### Quick Demo - WebUI

![](https://github.com/OWASP/www-project-nettacker/raw/master/assets/images/Screencast-from-Tuesday-09-June-2020-02-32-32-IST-_online-video-cutter.com_.gif)

**Credit:** This information was adapted from an excellent guide on [OWASP](https://owasp.org/www-project-nettacker/). Be sure to check out the original post for more details.

# Nettacker — Automated Penetration Testing Framework

![](https://miro.medium.com/v2/resize:fit:700/0*ZQZE4sCITkAscT5N)

**Introduction  
**  
Vulnerability Scanning is a crucial process for identifying security flaws in web-based applications. Automated scanning tools play a vital role in this domain, and one notable project is Nettacker by OWASP. This tool is designed to streamline various phases of security testing, such as Information Gathering, Enumeration, Scanning, and Vulnerability Scanning.  
Nettacker, being developed in the Python language, offers automation capabilities that aid in the discovery of services, bugs, vulnerabilities, misconfigurations, and other pertinent information within networks. The tool’s automation extends to generating comprehensive reports that provide a detailed overview of the security posture of the target system.

Moreover, Nettacker’s open-source nature makes it freely accessible on the GitHub platform, enabling security professionals and developers to leverage and contribute to its ongoing improvement. Notably, its compatibility with Python allows for flexibility and ease of use.

One of Nettacker’s standout features is its support for bypassing Firewall/IDS/IPS devices on the target server. This functionality enhances its effectiveness in identifying vulnerabilities that might be obscured by these security measures.

**Installation**

**Step 1**: Execute the given command to install the tool on your Kali Linux system

git clone https://github.com/OWASP/Nettacker.git

**Step 2**: Proceed to the next step by utilizing the provided command to navigate to the tool’s directory. This step is crucial to ensure the tool can be executed successfully.

cd Nettacker

**Step 3:** You’ve entered the Nettacker directory. It’s time to install a required dependency for Nettacker using the provided command.

sudo pip3 install -r requirements.txt

**Step 4**: All necessary dependencies have been successfully installed on your Kali Linux system. Utilize the given command to execute the tool and explore the help section.

python3 nettacker.py -h

![](https://miro.medium.com/v2/resize:fit:700/1*-QXgQiPPw8BUcfr45IXhkg.png)

# Working with Nettacker Tool

**Example 1:** Read targets from a list  
- it reads targets from a provided list, enabling focused scanning on specific targets for efficient reconnaissance

python3 nettacker.py -l targets.txt -m all -x port_scan -g 20-100 -t 5 -u root -p 123456,654321,123123

**Example 2:** Finding clickjacking_vuln  
- is likely used to search for clickjacking vulnerabilities during the scanning process.

python3 nettacker.py -i https://geeksforgeeks.org -m clickjacking_vuln

![](https://miro.medium.com/v2/resize:fit:700/1*GWUA1d1Dynwb3FgbCtAL3A.png)

**Example 3:** Scan subdomains

  
python3 nettacker.py -i geeksforgeeks.org -s -m port_scan -t 10 -M 35 -g 20-100 –graph d3_tree_v2_graph

![](https://miro.medium.com/v2/resize:fit:700/1*IliSbPimytBVARIarjaF_w.png)

![](https://miro.medium.com/v2/resize:fit:700/1*1rizfcFSOPA3kHC97J_pRQ.png)

**Example 4:** Automatically scan the IP range by retrieving the range information from the online RIPE database.

python3 nettacker.py -i owasp.org -s -r -m port_scan -t 10 -M 35 -g 20-100 –graph d3_tree_v2_graph

![](https://miro.medium.com/v2/resize:fit:700/1*XzkKedMG-bLlJmccY8So4w.png)

![](https://miro.medium.com/v2/resize:fit:700/1*j9P5vVDjuWfgSUUz8Jcdpw.png)

**Example 5:** Use * pattern for selecting modules

python3 nettacker.py -i geeksforgeeks.org -m *_vuln

![](https://miro.medium.com/v2/resize:fit:700/1*qf2hyOvnS04ZQ-h5q5ma-A.png)

**Example 6**: Get the list of all modules with details

python3 nettacker.py --show-all-modules

![](https://miro.medium.com/v2/resize:fit:700/1*LBpmX5HKI3NrslCQ0nA4_Q.png)

![](https://miro.medium.com/v2/resize:fit:700/1*S5bK0D-nmQFpDb7hsHkt6Q.png)

**Credit:** This information was adapted from an excellent guide on [Medium](https://medium.com/@harshleenchawla06/nettacker-automated-penetration-testing-framework-061bae344096). Be sure to check out the original post for more details.

# This is Why OWASP Created OWASP Nettacker

Ever heard of OWASP?  Well I’m sure you have and if not if you are interested in Information Security at all you need to know about it as it is the authority in all things related to Information Security.  That said, did you know they have a tool they built for automated pentesting and report generating with a graphical interface called **OWASP Nettacker**?

OWASP Nettacker is an open-source penetration testing framework with auto information gathering and vulnerabilities assessment features. OWASP Nettacker can automatically scan different frameworks and applications, gathering useful information, such as running services, open ports, server information, reverse IP lookup, DNS information, sub-domain records, CMS information, plugins, themes, directories, etc.  Besides information gathering, the framework can automate the process of finding bugs, misconfigurations, and vulnerabilities. The most common vulnerabilities that can be detected with OWASP Nettacker include brute-force attacks, ProFTPD (FTP server) vulnerabilities, expired certificate issues, weak signature algorithms, cross sites scripting, header misconfigurations, servers version-specific vulnerabilities, clickjacking, heartbleed attack, CCS injection, and pma (PhpMyAdmin) attacks. The brute-force scan option assesses the security of different network protocols like FTP, SSH, telnet, http, NTLM, and xmlrpc protocols. The ProFTPD-related scanning covers vulnerabilities like bypass SQL protection, CPU consumption, directory traversal, heap overflow, integer overflow, restriction bypass, and memory leak vulnerability detection.

**OWASP Nettacker Installation**

OWASP Nettacker is a Python based project that is tested on different operating systems including Linux, MacOS, and Windows OS. The framework is compatible with the both Python versions (2 and 3).   OWASP Nettacker depends on different packages included in the _requirements.txt_ file included in the framework’s source code directory. Apart from the dependencies included in the _requirements.txt_ file, there are two more packages that need to be installed before OWASP Nettacker installation. These packages can be installed as follows.

apt install libcurl4-openssl-dev libssl-dev

![owasp-nettacker-dependencies](https://www.hackingloops.com/wp-content/uploads/2019/10/owasp-nettacker-dependencies.png)

After installing the (libcurl4-openssl-dev, libssl-dev) packages, clone OWASP Nettacker from Github using the following command.

git clone https://github.com/zdresearch/OWASP-Nettacker.git

![owasp-nettacker-cloning](https://www.hackingloops.com/wp-content/uploads/2019/10/owasp-nettacker-cloning.png)

Navigate to the framework’s directory and run the following commands to complete the installation.

cd OWASP-Nettacker && pip install -r requirements.txt && python setup.py install

![owasp-nettacker-installation](https://www.hackingloops.com/wp-content/uploads/2019/10/owasp-nettacker-installation.png)

**How OWASP Nettacker Works?**

The following help command shows all the attack options and parameters required to initiate the scanning process.

python nettacker.py --help

![owasp-nettacker-usage](https://www.hackingloops.com/wp-content/uploads/2019/10/owasp-nettacker-usage.png)

The language feature in OWASP Nettacker allows scanning into any of the available (21) languages. We can change the language using the following command.

python nettacker.py –L <Preferred language code>

Preferred language codes: en, nl, el, ps, de, ko, it, ja, fa, fr,  hy, tr, ar, zh-cn, vi, ru, hi, ur, iw, id, es

OWASP Nettacker has the flexibility of using different command formats to scan targets. The following command shows the mandatory parameters (i, L, m) required to initiate the scanning process. The optional parameters can be appended with the command to enhance its functionality.

_python nettacker.py <-i | L > <Targets | Text File> <-m> <scan option>_

The _i_ and _L_ represents two different target selection formats. The ­_i_ option is used when the targets are provided through the command line. The _L_ parameter is used when we provide targets through a text file. The _–m_ parameter represents different attacks/scan options supported by the framework.

The following example shows some of the ways we can use OWASP Nettacker for information gathering and assessing vulnerabilities in target hosts.

**Port Scanning Example:** We can find open ports and supported protocols information using the following command.

python nettacker.py -i webscantest.com -m port_scan -g 20-100 -t 10

The –g parameter in the above command represents the ports and –t shows the allowed number of threads to connect with the host.  The scan results are displayed on the screen in a tabular format.

![port-scan table and reults path](https://www.hackingloops.com/wp-content/uploads/2019/10/port-scan-table-and-reults-path.png)

OWASP Nettacker also stores the result in an HTML file and database folder located in the framework’s directory.

![html results](https://www.hackingloops.com/wp-content/uploads/2019/10/html-results.png)

**Subdomain Discovery Example:** The following command scans all the available subdomains linked with the target host.

python nettacker.py -i vulnweb.com -m subdomain_scan -g 20-100 -t 10

![sub-domain-html-results](https://www.hackingloops.com/wp-content/uploads/2019/10/sub-domain-html-results.png)

**All in One Scanning Option:** OWASP Nettacker has the option of running all the scanning modules in a single command.

python nettacker.py -i testphp.vulnweb.com -m all -t 10 -M 35 -g 20-100 --graph d3_tree_v2_graph

The above command runs all the available modules on the target host (testphp.vulnweb.com) to gather host information and list all the vulnerabilities discovered by the tool.

**Information Gathering Screenshot**

![owasp nettacker table-report-1](https://www.hackingloops.com/wp-content/uploads/2019/10/table-report-1.png)

**Vulnerabilities Assessment Screenshot**

![owasp-nettacker vuln table-report](https://www.hackingloops.com/wp-content/uploads/2019/10/table-report-3.png)

The results are also displayed in a 3d graph format as shown below.

![owasp graph view1](https://www.hackingloops.com/wp-content/uploads/2019/10/zoomed-view1.png)

![owasp-nettacker view2](https://www.hackingloops.com/wp-content/uploads/2019/10/zoomed-view2.png)

**Summary**

OWASP Nettacker is a decent penetration testing tool with some exciting features like graphical representation of results and generation of penetration testing reports.

**Credit:** This information was adapted from an excellent guide on [HackingLoops](https://www.hackingloops.com/owasp-nettacker/). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/_VdOjNRoGNg?si=BACqyF0DbQRnihwo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=_VdOjNRoGNg). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/1UL7DtHKcQo?si=BlIXdRaerxVDxnko" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=1UL7DtHKcQo). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/HvXPcByShgI?si=klkR_EScdZi1w3Tm" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=HvXPcByShgI). Be sure to check out the original post for more details.


