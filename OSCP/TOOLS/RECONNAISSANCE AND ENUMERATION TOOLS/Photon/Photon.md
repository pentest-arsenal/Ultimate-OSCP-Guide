#   
[![Photon](https://camo.githubusercontent.com/6967710902d1a0d6fb3b920bc2206029d21e43b57871c4a053925c24a1481cd7/68747470733a2f2f696d6167652e6962622e636f2f68354f5a414b2f70686f746f6e736d616c6c2e706e67)](https://github.com/s0md3v/Photon)  
Photon  

[](https://github.com/s0md3v/Photon#--------photon--)

#### Incredibly fast crawler designed for OSINT.

[](https://github.com/s0md3v/Photon#incredibly-fast-crawler-designed-for-osint)

 [![](https://camo.githubusercontent.com/d1af3704c654dc2b97b302f94f4b9fef7e0bd1589c1cf0e4739e742705e1f381/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f72656c656173652f73306d6433762f50686f746f6e2e737667)](https://github.com/s0md3v/Photon/releases) [![pypi](https://camo.githubusercontent.com/7d021f7d255468befc1a94b5599e83b8e6dc2c364cf5f07bcad107278b6012f8/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f707970692d4070686f746f6e2d7265642e7376673f7374796c653d7374796c653d666c61742d737175617265)](https://pypi.org/project/photon/) [![](https://camo.githubusercontent.com/a16d1c399d9ff5f4b1ca4b6b12f8f03d106153e9a180c0b6a0bab74b8b52a57c/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f6973737565732d636c6f7365642d7261772f73306d6433762f50686f746f6e2e737667)](https://github.com/s0md3v/Photon/issues?q=is%3Aissue+is%3Aclosed)[![](https://camo.githubusercontent.com/52ee40bc2d5899629913bbf795237a863673f12c5a21675c41d75560b70f73b3/68747470733a2f2f696d672e736869656c64732e696f2f7472617669732f636f6d2f73306d6433762f50686f746f6e2e737667)](https://travis-ci.com/s0md3v/Photon)

Met a CAPTCHA? Try [CapSolver](https://www.capsolver.com/?utm_source=github&utm_medium=repo&utm_campaign=scraping&utm_term=photon) solving solution.

[![demo](https://camo.githubusercontent.com/1dfe7c35826adb9c16107ccfed17473bc21e53e8e9f743d4992b30de24f485ee/68747470733a2f2f696d6167652e6962622e636f2f6b515355637a2f64656d6f2e706e67)](https://camo.githubusercontent.com/1dfe7c35826adb9c16107ccfed17473bc21e53e8e9f743d4992b30de24f485ee/68747470733a2f2f696d6167652e6962622e636f2f6b515355637a2f64656d6f2e706e67)

[Photon Wiki](https://github.com/s0md3v/Photon/wiki) • [How To Use](https://github.com/s0md3v/Photon/wiki/Usage) • [Compatibility](https://github.com/s0md3v/Photon/wiki/Compatibility-&-Dependencies) • [Photon Library](https://github.com/s0md3v/Photon/wiki/Photon-Library) • [Contribution](https://github.com/s0md3v/Photon#contribution--license) • [Roadmap](https://github.com/s0md3v/Photon/projects/1)

### Key Features

[](https://github.com/s0md3v/Photon#key-features)

#### Data Extraction

[](https://github.com/s0md3v/Photon#data-extraction)

Photon can extract the following data while crawling:

- URLs (in-scope & out-of-scope)
- URLs with parameters (`example.com/gallery.php?id=2`)
- Intel (emails, social media accounts, amazon buckets etc.)
- Files (pdf, png, xml etc.)
- Secret keys (auth/API keys & hashes)
- JavaScript files & Endpoints present in them
- Strings matching custom regex pattern
- Subdomains & DNS related data

The extracted information is saved in an organized manner or can be [exported as json](https://github.com/s0md3v/Photon/wiki/Usage#export-formatted-result).

[![save demo](https://camo.githubusercontent.com/90ad7596382beaddc6f3273fe55fe7b6332022577444577a6cef32413d54298b/68747470733a2f2f696d6167652e6962622e636f2f64533142714b2f636172626f6e5f322e706e67)](https://camo.githubusercontent.com/90ad7596382beaddc6f3273fe55fe7b6332022577444577a6cef32413d54298b/68747470733a2f2f696d6167652e6962622e636f2f64533142714b2f636172626f6e5f322e706e67)

#### Flexible

[](https://github.com/s0md3v/Photon#flexible)

Control timeout, delay, add seeds, exclude URLs matching a regex pattern and other cool stuff. The extensive range of [options](https://github.com/s0md3v/Photon/wiki/Usage) provided by Photon lets you crawl the web exactly the way you want.

#### Genius

[](https://github.com/s0md3v/Photon#genius)

Photon's smart thread management & refined logic gives you top notch performance.

Still, crawling can be resource intensive but Photon has some tricks up it's sleeves. You can fetch URLs archived by [archive.org](https://archive.org/) to be used as seeds by using `--wayback` option.

#### Plugins

[](https://github.com/s0md3v/Photon#plugins)

- **[wayback](https://github.com/s0md3v/Photon/wiki/Usage#use-urls-from-archiveorg-as-seeds)**
- **[dnsdumpster](https://github.com/s0md3v/Photon/wiki/Usage#dumping-dns-data)**
- **[Exporter](https://github.com/s0md3v/Photon/wiki/Usage#export-formatted-result)**

#### Docker

[](https://github.com/s0md3v/Photon#docker)

Photon can be launched using a lightweight Python-Alpine (103 MB) Docker image.

```shell
$ git clone https://github.com/s0md3v/Photon.git
$ cd Photon
$ docker build -t photon .
$ docker run -it --name photon photon:latest -u google.com
```

To view results, you can either head over to the local docker volume, which you can find by running `docker inspect photon` or by mounting the target loot folder:

```shell
$ docker run -it --name photon -v "$PWD:/Photon/google.com" photon:latest -u google.com
```

#### Frequent & Seamless Updates

[](https://github.com/s0md3v/Photon#frequent--seamless-updates)

Photon is under heavy development and updates for fixing bugs. optimizing performance & new features are being rolled regularly.

If you would like to see features and issues that are being worked on, you can do that on [Development](https://github.com/s0md3v/Photon/projects/1) project board.

Updates can be installed & checked for with the `--update` option. Photon has seamless update capabilities which means you can update Photon without losing any of your saved data.

### Contribution & License

[](https://github.com/s0md3v/Photon#contribution--license)

You can contribute in following ways:

- Report bugs
- Develop plugins
- Add more "APIs" for ninja mode
- Give suggestions to make it better
- Fix issues & submit a pull request

Please read the [guidelines](https://github.com/s0md3v/Photon/wiki/Guidelines) before submitting a pull request or issue.

Do you want to have a conversation in private? Hit me up on my [twitter](https://twitter.com/s0md3v/), inbox is open :)

**Photon** is licensed under [GPL v3.0 license](https://www.gnu.org/licenses/gpl-3.0.en.html)

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/s0md3v/Photon). Be sure to check out the original post for more details.

# Packages and Binaries:

### photon

This package includes a fast and flexible crawler designed for open source intelligence (OSINT).

Photon can extract the following data while crawling:

- URLs (in-scope & out-of-scope)
- URLs with parameters (example.com/gallery.php?id=2)
- Intel (emails, social media accounts, amazon buckets etc.)
- Files (pdf, png, xml etc.)
- Secret keys (auth/API keys & hashes)
- JavaScript files & Endpoints present in them
- Strings matching custom regex pattern
- Subdomains & DNS related data

The extracted information is saved in an organized manner or can be exported as json.

**Installed size:** `60 KB`  
**How to install:** `sudo apt install photon`

Dependencies:

- python3
- python3-requests
- python3-socks
- python3-tld
- python3-urllib3

##### photon

```console
root@kali:~# photon -h
      ____  __          __
     / __ \/ /_  ____  / /_____  ____
    / /_/ / __ \/ __ \/ __/ __ \/ __ \
   / ____/ / / / /_/ / /_/ /_/ / / / /
  /_/   /_/ /_/\____/\__/\____/_/ /_/ v1.2.2

usage: photon.py [-h] [-u ROOT] [-c COOK] [-r REGEX] [-e {csv,json}]
                 [-o OUTPUT] [-l LEVEL] [-t THREADS] [-d DELAY] [-v]
                 [-s SEEDS [SEEDS ...]] [--stdout STD]
                 [--user-agent USER_AGENT] [--exclude EXCLUDE]
                 [--timeout TIMEOUT] [--clone] [--headers] [--dns] [--keys]
                 [--only-urls] [--wayback]

options:
  -h, --help            show this help message and exit
  -u ROOT, --url ROOT   root url
  -c COOK, --cookie COOK
                        cookie
  -r REGEX, --regex REGEX
                        regex pattern
  -e {csv,json}, --export {csv,json}
                        export format
  -o OUTPUT, --output OUTPUT
                        output directory
  -l LEVEL, --level LEVEL
                        levels to crawl
  -t THREADS, --threads THREADS
                        number of threads
  -d DELAY, --delay DELAY
                        delay between requests
  -v, --verbose         verbose output
  -s SEEDS [SEEDS ...], --seeds SEEDS [SEEDS ...]
                        additional seed URLs
  --stdout STD          send variables to stdout
  --user-agent USER_AGENT
                        custom user agent(s)
  --exclude EXCLUDE     exclude URLs matching this regex
  --timeout TIMEOUT     http request timeout
  --clone               clone the website locally
  --headers             add headers
  --dns                 enumerate subdomains and DNS data
  --keys                find secret keys
  --only-urls           only extract URLs
  --wayback             fetch URLs from archive.org as seeds
```

---

Updated on: 2023-Aug-14

**Credit:** This information was adapted from an excellent guide on [Kali.org](https://www.kali.org/tools/photon/). Be sure to check out the original post for more details.

# Photon Scanner – Web Scraping OSINT Tool

Last Updated : 17 Jun, 2021

Gather information on online targets can turn out to be a very **time-consuming** activity, especially when one only needs specific information about the target and not his entire **biodata.** Suppose you need specific pieces of information about a target with lots of subdomains, then one needs a tool that is capable of doing the **heavy lifting, sifting** through **URLs** on our behalf to retrieve information that can be of value. So **Photon** an OSINT scanner perfectly fits the profile here.

### **Key Feature:**

**1) Data Extraction:** Photon can **extract** the following data while **crawling:**

- URLs (in-scope and out-of-scope)
- URLs with parameters. (example.com/gallery.php?id=3)
- Intel (emails, social media accounts etc. )
- Files (png, jpeg, pdf etc.)
- Secret keys (API keys and hashes.)
- Subdomains and DNS related data.
- Strings matching custom regex pattern.

**Note:** The extracted information is saved in an organized manner and it can be exported as JSON.

**2) Flexible:** Control timeout, delay, add seeds, exclude URLs matching a regex pattern, and other cool stuff. The wide range of options that **Photon** provides lets you **crawl** the web **exactly** the way you want making it a powerful tool.

**3) Plugins:**

- wayback
- dnsdumpster
- Exporter

**Requirements:**

**python3:** To check if your system has Python installed, just open a terminal window and type **python3.** If your screen looks like the screenshot shown below after typing the **python3** in **terminal** then good, otherwise you can **install** it with **apt-install python3.**

![](https://media.geeksforgeeks.org/wp-content/uploads/20210601145153/1min7-660x442.png)

Fig1: Python3 is installed in our system.

### **Using Photon:**

**Step 1:** After installing python3 if not installed before, then we also need to install some dependencies. We can simply do it by typing in the following command in our terminal window:

> pip install tld requests

After completion, move on to the next step.

**Step 2:** To install Photon, type in the following commands in your terminal window.

>  git clone https://github.com/s0md3v/Photon.git
> 
>  cd Photon

**Step 3:** Now, we can run  python3 photon.py -h to see the list of options photon provides us that we can use.

> python3 photon.py -h

![](https://media.geeksforgeeks.org/wp-content/uploads/20210601145259/2min-660x442.png)

Fig2: Optional arguments.

The most basic scan one can run is **python3 photon.py -u target.com.**

**Step 3:** Let’s use one of the most useful and interesting features of Photon, which is the ability to generate a visual DNS map of everything connected to domain. To do this, simply we will run a scan with –dns flag. Suppose we want to generate a map of geeksforgeeks.com, for this we will run the following command:

> python3 photon.py -u https://www.geeksforgeeks.com/ –dns

![](https://media.geeksforgeeks.org/wp-content/uploads/20210603003626/122min-660x453.png)

Fig3: www.geeksforgeeks.com used as target.

Here, we can see that the total time taken was only 1 second, if you just throw a random URL that isn’t accurate then the photon scanner will take longer time. Also, we can see how many requests per second were made, which in this case is 2.

![](https://media.geeksforgeeks.org/wp-content/uploads/20210603003254/13-660x290.png)

Fig4: geeksforgeeks.com files generated by photon.

![](https://media.geeksforgeeks.org/wp-content/uploads/20210603003423/15-660x286.png)

Fig5:DNS map.

The DNS map shows that it has a very simple domain structure consisting of 0 subdomains.

Let’s zoom in and look at the **MX record** (where MX stands for “mail excahnger”)**,**  responsible for email services. It can be seen that it uses 10 mx76.m2bp.com which is a mail server running on port 443, 80.

![](https://media.geeksforgeeks.org/wp-content/uploads/20210603003221/12-660x266.png)

Fig6:  Showing mail exchanger  of geeksforgeeks.com

All of this can turn out to be not less than a goldmine for hackers looking for the most vulnerable system connected to the target.

**Step 4:** Now, let’s grab some **email addresses** and **keys** from a website, say geeksforgeeks.org.

Now, we’ll add a few more flags to increase the depth and speed of the search. In terminal , type the following command:

> python3 photon.py -u https://www.geeksforgeeks.org/ –keys -t 10 -l 3

![](https://media.geeksforgeeks.org/wp-content/uploads/20210603010725/55-660x145.png)

Fig7: Email of geeksforgeeks.org

We can see their email is feedback@geeksforgeeks.org. Also, **3** in the command specifies that we want to go **three levels deep of URLs,** whereas **10** specifies we want to **open ten threads** to do the **crawling.**

We will get some email addresses. We were doing a pretty wide net for this search, so there may be many unrelated emails on our list. This is because we scraped three levels of URLs deep and likely scraped some unrelated websites.

### **Photon Makes Scanning Through URLs Lightning-Fast:**

When it comes to crawling through hundreds of URLs for information, it’s very time-consuming. Photon makes it easy to crawl large amounts of subdomains or several targets, allowing you to scale your research during the recon phase. With the intelligent options built-in for parsing and searching for kinds of data like email addresses and important API keys, Photon can catch even small mistakes a target makes that reveal a lot of valuable information.

**Credit:** This information was adapted from an excellent guide on [GeeksForGeeks](https://www.geeksforgeeks.org/photon-scanner-web-scraping-osint-tool/). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/VDTa5o5owwk?si=7BDc-OvYNQQ38kv0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=VDTa5o5owwk). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/iBBZ41FfM3M?si=aUSBMCTofgHRsAtp" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=iBBZ41FfM3M). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/pJDJwD8GCIg?si=6rsoXvW_R-j9JkrQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=pJDJwD8GCIg). Be sure to check out the original post for more details.


