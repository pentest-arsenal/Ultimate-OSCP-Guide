## About Sublist3r

[](https://github.com/aboul3la/Sublist3r#about-sublist3r)

Sublist3r is a python tool designed to enumerate subdomains of websites using OSINT. It helps penetration testers and bug hunters collect and gather subdomains for the domain they are targeting. Sublist3r enumerates subdomains using many search engines such as Google, Yahoo, Bing, Baidu and Ask. Sublist3r also enumerates subdomains using Netcraft, Virustotal, ThreatCrowd, DNSdumpster and ReverseDNS.

[subbrute](https://github.com/TheRook/subbrute) was integrated with Sublist3r to increase the possibility of finding more subdomains using bruteforce with an improved wordlist. The credit goes to TheRook who is the author of subbrute.

## Screenshots

[](https://github.com/aboul3la/Sublist3r#screenshots)

[![Sublist3r](https://camo.githubusercontent.com/a489886b4f98a6ca99a2ba8342800b14bd180ce92f217a9c86c37c81dc418a01/687474703a2f2f7777772e7365636765656b2e6e65742f696d616765732f5375626c69737433722e706e67 "Sublist3r in action")](https://camo.githubusercontent.com/a489886b4f98a6ca99a2ba8342800b14bd180ce92f217a9c86c37c81dc418a01/687474703a2f2f7777772e7365636765656b2e6e65742f696d616765732f5375626c69737433722e706e67)

## Installation

[](https://github.com/aboul3la/Sublist3r#installation)

```
git clone https://github.com/aboul3la/Sublist3r.git
```

## Recommended Python Version:

[](https://github.com/aboul3la/Sublist3r#recommended-python-version)

Sublist3r currently supports **Python 2** and **Python 3**.

- The recommended version for Python 2 is **2.7.x**
- The recommended version for Python 3 is **3.4.x**

## Dependencies:

[](https://github.com/aboul3la/Sublist3r#dependencies)

Sublist3r depends on the `requests`, `dnspython` and `argparse` python modules.

These dependencies can be installed using the requirements file:

- Installation on Windows:

```
c:\python27\python.exe -m pip install -r requirements.txt
```

- Installation on Linux

```
sudo pip install -r requirements.txt
```

Alternatively, each module can be installed independently as shown below.

#### Requests Module ([http://docs.python-requests.org/en/latest/](http://docs.python-requests.org/en/latest/))

[](https://github.com/aboul3la/Sublist3r#requests-module-httpdocspython-requestsorgenlatest)

- Install for Windows:

```
c:\python27\python.exe -m pip install requests
```

- Install for Ubuntu/Debian:

```
sudo apt-get install python-requests
```

- Install for Centos/Redhat:

```
sudo yum install python-requests
```

- Install using pip on Linux:

```
sudo pip install requests
```

#### dnspython Module ([http://www.dnspython.org/](http://www.dnspython.org/))

[](https://github.com/aboul3la/Sublist3r#dnspython-module-httpwwwdnspythonorg)

- Install for Windows:

```
c:\python27\python.exe -m pip install dnspython
```

- Install for Ubuntu/Debian:

```
sudo apt-get install python-dnspython
```

- Install using pip:

```
sudo pip install dnspython
```

#### argparse Module

[](https://github.com/aboul3la/Sublist3r#argparse-module)

- Install for Ubuntu/Debian:

```
sudo apt-get install python-argparse
```

- Install for Centos/Redhat:

```
sudo yum install python-argparse
```

- Install using pip:

```
sudo pip install argparse
```

**for coloring in windows install the following libraries**

```
c:\python27\python.exe -m pip install win_unicode_console colorama
```

## Usage

[](https://github.com/aboul3la/Sublist3r#usage)

|Short Form|Long Form|Description|
|---|---|---|
|-d|--domain|Domain name to enumerate subdomains of|
|-b|--bruteforce|Enable the subbrute bruteforce module|
|-p|--ports|Scan the found subdomains against specific tcp ports|
|-v|--verbose|Enable the verbose mode and display results in realtime|
|-t|--threads|Number of threads to use for subbrute bruteforce|
|-e|--engines|Specify a comma-separated list of search engines|
|-o|--output|Save the results to text file|
|-h|--help|show the help message and exit|

### Examples

[](https://github.com/aboul3la/Sublist3r#examples)

- To list all the basic options and switches use -h switch:

`python sublist3r.py -h`

- To enumerate subdomains of specific domain:

`python sublist3r.py -d example.com`

- To enumerate subdomains of specific domain and show only subdomains which have open ports 80 and 443 :

`python sublist3r.py -d example.com -p 80,443`

- To enumerate subdomains of specific domain and show the results in realtime:

`python sublist3r.py -v -d example.com`

- To enumerate subdomains and enable the bruteforce module:

`python sublist3r.py -b -d example.com`

- To enumerate subdomains and use specific engines such Google, Yahoo and Virustotal engines

`python sublist3r.py -e google,yahoo,virustotal -d example.com`

## Using Sublist3r as a module in your python scripts

[](https://github.com/aboul3la/Sublist3r#using-sublist3r-as-a-module-in-your-python-scripts)

**Example**

```python
import sublist3r 
subdomains = sublist3r.main(domain, no_threads, savefile, ports, silent, verbose, enable_bruteforce, engines)
```

The main function will return a set of unique subdomains found by Sublist3r

**Function Usage:**

- **domain**: The domain you want to enumerate subdomains of.
- **savefile**: save the output into text file.
- **ports**: specify a comma-sperated list of the tcp ports to scan.
- **silent**: set sublist3r to work in silent mode during the execution (helpful when you don't need a lot of noise).
- **verbose**: display the found subdomains in real time.
- **enable_bruteforce**: enable the bruteforce module.
- **engines**: (Optional) to choose specific engines.

Example to enumerate subdomains of Yahoo.com:

```python
import sublist3r 
subdomains = sublist3r.main('yahoo.com', 40, 'yahoo_subdomains.txt', ports= None, silent=False, verbose= False, enable_bruteforce= False, engines=None)
```

## License

[](https://github.com/aboul3la/Sublist3r#license)

Sublist3r is licensed under the GNU GPL license. take a look at the [LICENSE](https://github.com/aboul3la/Sublist3r/blob/master/LICENSE) for more information.

## Credits

[](https://github.com/aboul3la/Sublist3r#credits)

- [TheRook](https://github.com/TheRook) - The bruteforce module was based on his script **subbrute**.
- [Bitquark](https://github.com/bitquark) - The Subbrute's wordlist was based on his research **dnspop**.

## Thanks

[](https://github.com/aboul3la/Sublist3r#thanks)

- Special Thanks to [Ibrahim Mosaad](https://twitter.com/ibrahim_mosaad) for his great contributions that helped in improving the tool.

## Version

[](https://github.com/aboul3la/Sublist3r#version)

**Current version is 1.0**

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/aboul3la/Sublist3r). Be sure to check out the original post for more details.

# What is Sublist3r and How to Use it?

Last Updated : 15 Mar, 2023

Sublister is a tool designed in python and uses OSINT in order to enumerate subdomains of websites. It helps pen-testers in collecting and gathering subdomains for a domain which is their target. In order to fetch the accurate results, sublilster uses many search engines like Google, Yahoo, etc. and even tools like Netcraft, Virustotal, etc.

### Installing and using sublister

**1.** To install sublister you can clone the Github repository  and use it. To do so you can follow the following command.

git clone https://github.com/aboul3la/Sublist3r.git

**2.** Once the process is done move to the seblister directory 

cd Sublist3r

![Cloning sublist3r](https://media.geeksforgeeks.org/wp-content/uploads/20200705193830/sublister.png)

**3.** Now we need to check for dependencies, sublist3r depends on requests, dnspython, and argparse python modules. These dependencies can be installed using requirements.txt file:   
 

pip install -r requirements.txt

![installing required packages](https://media.geeksforgeeks.org/wp-content/uploads/20200705194109/sublister2.png)

You can even manually install all the required modules.

**Requests module**: 

sudo pip install requests

**dnspython module** 

sudo pip install dnspython

**argparse module** 

sudo pip install argparse

![manually installing required packages](https://media.geeksforgeeks.org/wp-content/uploads/20200705194410/sublister3.png)

**4.** To run the tool, Enter the following command in the terminal.

./sublist3r.py

While running tool if you get any errors like for example dns.resolver module not found or dns.message module not found then it is because you might be running tool on python version 2.7 and installed dnspython module in python 3 version, so it will be better if you use python pip instead of pip3 to solve these errors. 

![Running sublist3r](https://media.geeksforgeeks.org/wp-content/uploads/20200705195845/sublister5.png)

**5.** Now our tool is working in the current directory and every time we will try to run it then we need to go into the directory and run it, so now we will make a symbolic link so that we can access it from any directory we are in.   
 

sudo ln -sfv /opt/Sublist3r/sublist3r.py /usr/bin/sublist3r

![creating symbolic link for sublist3r](https://media.geeksforgeeks.org/wp-content/uploads/20200705200320/sublister6.png)

**Usage**:   
 

![sublist3r help section how to use sublist3r](https://media.geeksforgeeks.org/wp-content/uploads/20200705200430/sublister7.png)

**Example:**  
To list the subdomains of a domain enter the following command in Linux and replace “kali.org” with the website you want to list the subdomains of.

sublist3r -v -d kali.org -t 5 -e bing -o ~/Desktop/subresult.txt

Where -d stands for domain listing and -v will verbose the output and tell from where it is getting the results. The fetch results will be saved in subresult.txt file in the desktop directory and the number of threads will be 5 using bing as a search engine.   
 

![using sublist3r to get all the sub domain names of a domain](https://media.geeksforgeeks.org/wp-content/uploads/20200705201738/Screenshot_2020-07-06_01-47-21.png)

As you can see, the above command lists all the domains and subdomains related to kali.org and hence make it easy for us to look for the subdomains of a website.

**Credit:** This information was adapted from an excellent guide on [GeeksForGeeks](https://www.geeksforgeeks.org/what-is-sublist3r-and-how-to-use-it/). Be sure to check out the original post for more details.

# Tool Documentation:

## sublist3r Usage Examples

Search for subdomains of kali.org (`-d kali.org`) using the Bing search engine (`-e bing`) with 3 threads (`-t 3`).

```console
root@kali:~# sublist3r -d kali.org -t 3 -e bing

                 ____        _     _ _     _   _____
                / ___| _   _| |__ | (_)___| |_|___ / _ __
                \___ \| | | | '_ \| | / __| __| |_ \| '__|
                 ___) | |_| | |_) | | \__ \ |_ ___) | |
                |____/ \__,_|_.__/|_|_|___/\__|____/|_|

                # Coded By Ahmed Aboul-Ela - @aboul3la

[-] Enumerating subdomains now for kali.org
[-] Searching now in Bing..
[-] Total Unique Subdomains Found: 19
www.kali.org
archive-3.kali.org
archive-4.kali.org
archive-5.kali.org
bugs.kali.org
cdimage.kali.org
docs.kali.org
ar.docs.kali.org
he.docs.kali.org
id.docs.kali.org
tr.docs.kali.org
forums.kali.org
git.kali.org
http.kali.org
images.kali.org
pkg.kali.org
repo.kali.org
security.kali.org
tools.kali.org
```

---

  

# Packages and Binaries:

### sublist3r

This package contains a Python security tool designed to enumerate subdomains of websites using OSINT. It helps penetration testers and bug hunters collect and gather subdomains for the domain they are targeting over the network. Sublist3r enumerates subdomains using many search engines such as Google, Yahoo, Bing, Baidu, and Ask. Sublist3r also enumerates subdomains using Netcraft, Virustotal, ThreatCrowd, DNSdumpster, and ReverseDNS.

Subbrute was integrated with Sublist3r to increase the possibility of finding more subdomains using bruteforce with an improved wordlist.

**Installed size:** `1.85 MB`  
**How to install:** `sudo apt install sublist3r`

Dependencies:

- python3
- python3 | python3 | python3
- python3-dnspython
- python3-requests

##### sublist3r

Tool designed to enumerate subdomains of websites using OSINT

```console
root@kali:~# sublist3r -h
usage: sublist3r [-h] -d DOMAIN [-b [BRUTEFORCE]] [-p PORTS] [-v [VERBOSE]]
                 [-t THREADS] [-e ENGINES] [-o OUTPUT] [-n]

OPTIONS:
  -h, --help            show this help message and exit
  -d DOMAIN, --domain DOMAIN
                        Domain name to enumerate it's subdomains
  -b [BRUTEFORCE], --bruteforce [BRUTEFORCE]
                        Enable the subbrute bruteforce module
  -p PORTS, --ports PORTS
                        Scan the found subdomains against specified tcp ports
  -v [VERBOSE], --verbose [VERBOSE]
                        Enable Verbosity and display results in realtime
  -t THREADS, --threads THREADS
                        Number of threads to use for subbrute bruteforce
  -e ENGINES, --engines ENGINES
                        Specify a comma-separated list of search engines
  -o OUTPUT, --output OUTPUT
                        Save the results to text file
  -n, --no-color        Output without color

Example: python3 /usr/bin/sublist3r -d google.com
```

---

Updated on: 2024-Mar-11

**Credit:** This information was adapted from an excellent guide on [Kali.org](https://www.kali.org/tools/sublist3r/). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/yXppnZZxkPg?si=6piSNGoB9OsAU4Bu" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=yXppnZZxkPg). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/DI8-tNq7hFc?si=lyp1XrBJJKsEjE29" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=DI8-tNq7hFc). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/lcJQoOTI5oU?si=vCa8JNKGjTX4ts-o" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=lcJQoOTI5oU). Be sure to check out the original post for more details.


