# CMSmap

[](https://github.com/dionach/CMSmap#cmsmap)

CMSmap is a python open source CMS scanner that automates the process of detecting security flaws of the most popular CMSs. The main purpose of CMSmap is to integrate common vulnerabilities for different types of CMSs in a single tool.

At the moment, CMSs supported by CMSmap are WordPress, Joomla, Drupal and Moodle.

Please note that this project is an early state. As such, you might find bugs, flaws or mulfunctions. Use it at your own risk!

# Preview

[](https://github.com/dionach/CMSmap#preview)

- [https://asciinema.org/a/MELa2nUcrtATqnDLnc0ig8rcT](https://asciinema.org/a/MELa2nUcrtATqnDLnc0ig8rcT)

# Installation

[](https://github.com/dionach/CMSmap#installation)

You can download the latest version of CMSmap by cloning the GitHub repository:

```
 git clone https://github.com/Dionach/CMSmap
```

Then you need to configure the `edbtype` and `edbpath` settings in the `cmsmap.conf`. Use `GIT` if you have a local Git repository of Exploit-db :

```
[exploitdb]
edbtype = GIT
edbpath = /opt/exploitdb/
```

Alternatively, use `APT` if you have installed the `debian` exploitdb package. For Kali, use the following settings :

```
[exploitdb]
edbtype = APT
edbpath = /usr/share/exploitdb/
```

If you would like to run `cmsmap` from anywhere in your system you can install it with `pip3` :

```
cd CMSmap
pip3 install .
```

To uninstall it :

```
pip3 uninstall cmsmap -y
```

# Usage

[](https://github.com/dionach/CMSmap#usage)

```
usage: cmsmap [-f W/J/D] [-F] [-t] [-a] [-H] [-i] [-o] [-E] [-d] [-u] [-p]
              [-x] [-k] [-w] [-v] [-h] [-D] [-U W/J/D]
              [target]

CMSmap tool v1.0 - Simple CMS Scanner
Author: Mike Manzotti

Scan:
  target                target URL (e.g. 'https://example.com:8080/')
  -f W/J/D, --force W/J/D
                        force scan (W)ordpress, (J)oomla or (D)rupal
  -F, --fullscan        full scan using large plugin lists. False positives and slow!
  -t , --threads        number of threads (Default 5)
  -a , --agent          set custom user-agent
  -H , --header         add custom header (e.g. 'Authorization: Basic ABCD...')
  -i , --input          scan multiple targets listed in a given file
  -o , --output         save output in a file
  -E, --noedb           enumerate plugins without searching exploits
  -c, --nocleanurls     disable clean urls for Drupal only
  -s, --nosslcheck      don't validate the server's certificate
  -d, --dictattack      run low intense dictionary attack during scanning (5 attempts per user)

Brute-Force:
  -u , --usr            username or username file
  -p , --psw            password or password file
  -x, --noxmlrpc        brute forcing WordPress without XML-RPC

Post Exploitation:
  -k , --crack          password hashes file (Require hashcat installed. For WordPress and Joomla only)
  -w , --wordlist       wordlist file

Others:
  -v, --verbose         verbose mode (Default false)
  -h, --help            show this help message and exit
  -D, --default         rum CMSmap with default options
  -U, --update          use (C)MSmap, (P)lugins or (PC) for both

Examples:
  cmsmap.py https://example.com
  cmsmap.py https://example.com -f W -F --noedb -d
  cmsmap.py https://example.com -i targets.txt -o output.txt
  cmsmap.py https://example.com -u admin -p passwords.txt
  cmsmap.py -k hashes.txt -w passwords.txt
```

# Contribution guidelines

[](https://github.com/dionach/CMSmap#contribution-guidelines)

If you want to contribute to CMSmap, be sure to review the [contribution guidelines](https://github.com/dionach/CMSmap/blob/master/.github/CONTRIBUTING.md).

# Disclaimer

[](https://github.com/dionach/CMSmap#disclaimer)

Usage of CMSmap for attacking targets without prior mutual consent is illegal. It is the end user's responsibility to obey all applicable local, state and federal laws. Developers assume NO liability and are NOT responsible for any misuse or damage caused by this program.

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/dionach/CMSmap). Be sure to check out the original post for more details.

# CMSmap – Open Source CMS Scanner

Last Updated : 14 Sep, 2021

CMSmap is a Python open source CMS scanner that automates the method of detecting security flaws of the foremost popular CMSs. The main purpose of this tool is to integrate common vulnerabilities for different types of CMSs into a single tool. at the instant, there’s support for WordPress, Joomla, Drupal, and Moodle. CMSmap tool is freely available on GitHub. CMSmap tool supports multiple target domain scanning and saves the results in text file format. CMSmap tool has the ability to set custom user-agent and header. CMSmap tool Support for SSL encryption. CMSmap tool supports Verbose mode for debugging purposes.

**Note**: Make Sure You have Python Installed on your System, as this is a python-based tool. Click to check the Installation process: [Python Installation Steps on Linux](https://www.geeksforgeeks.org/how-to-install-python-on-linux/)

## Installation of CMSmap Tool on Kali Linux OS

**Step 1**: Use the following command to install the tool in your Kali Linux operating system.

git clone https://github.com/Dionach/CMSmap.git

![](https://media.geeksforgeeks.org/wp-content/uploads/20210902104338/Step1.jpg)

**Step 2**: Now use the following command to move into the directory of the tool. You have to move in the directory in order to run the tool.

cd CMSmap 

![](https://media.geeksforgeeks.org/wp-content/uploads/20210902104340/Step2.jpg)

**Step 3**: You are in the directory of the CMSmap. Now run the following command to complete the installation.

sudo python3 setup.py install

![](https://media.geeksforgeeks.org/wp-content/uploads/20210902104342/Step3min.jpg)

**Step 4**: All the dependencies have been installed in your Kali Linux operating system. Now use the following command to run the tool and check the help section.

python3 cmsmap .py -h

![](https://media.geeksforgeeks.org/wp-content/uploads/20210902104343/Step4min.jpg)

## Working with CMSmap Tool on Kali Linux OS

**Example 1**: Simple Scan (Single Target)

python3 cmsmap.py https://geeksforgeeks.org

In this Example, We are performing simple scanning on the target domain [geeksforgeeks.org](https://www.geeksforgeeks.org/).

![](https://media.geeksforgeeks.org/wp-content/uploads/20210902104323/Example11min.jpg)

We have got the details of CMS and the theme applied to the domain.

![](https://media.geeksforgeeks.org/wp-content/uploads/20210902104325/Example12min.jpg)

The tool has identified the WordPress usernames on geeksforgeeks.org.

![](https://media.geeksforgeeks.org/wp-content/uploads/20210902104327/Example13min.jpg)

**Example 2**: Force scan WordPress

python3 cmsmap.py https://geeksforgeeks.org -f W -F --noedb -d

In this Example, We are performing a Force scan of WordPress CMS on geeksforgeeks.org.

![](https://media.geeksforgeeks.org/wp-content/uploads/20210902104328/Example21min.jpg)![](https://media.geeksforgeeks.org/wp-content/uploads/20210902104330/Example22.jpg)

**Example 3**: Scan multiple targets listed in a given file

python3 cmsmap.py -i targets.txt -o output.txt -f D

In this Example, We are scanning multiple target domains specified in the targets.txt file.

![](https://media.geeksforgeeks.org/wp-content/uploads/20210902104332/Example31.jpg)![](https://media.geeksforgeeks.org/wp-content/uploads/20210902104333/Example32.jpg)

**Example 4**: Verbose Mode

python3 cmsmap.py https://geeksforgeeks.org -v

In this Example, We are displaying the scan results in a more detailed way. We have used the -v tag for enabling the verbose mode.

![](https://media.geeksforgeeks.org/wp-content/uploads/20210902104335/Example41.jpg)![](https://media.geeksforgeeks.org/wp-content/uploads/20210902104337/Example42min.jpg)

**Credit:** This information was adapted from an excellent guide on [GeeksForGeeks](https://www.geeksforgeeks.org/cmsmap-open-source-cms-scanner/). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/-iJPIfs2noo?si=dlsbxx_27zxv9rch" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=-iJPIfs2noo). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/4G-eIjuFWVM?si=hyvOiM-qGIx6KqjB" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=4G-eIjuFWVM). Be sure to check out the original post for more details.





