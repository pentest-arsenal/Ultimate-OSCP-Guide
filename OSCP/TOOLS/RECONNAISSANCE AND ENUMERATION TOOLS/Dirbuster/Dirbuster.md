
# Tool Documentation:

## Screenshots

```console
dirbuster
```

[![dirbuster](https://www.kali.org/tools/dirbuster/images/dirbuster.png)](https://www.kali.org/tools/dirbuster/images/dirbuster.png)

---

  

# Packages and Binaries:

### dirbuster

DirBuster is a multi threaded java application designed to brute force directories and files names on web/application servers. Often is the case now of what looks like a web server in a state of default installation is actually not, and has pages and applications hidden within. DirBuster attempts to find these.

However tools of this nature are often as only good as the directory and file list they come with. A different approach was taken to generating this. The list was generated from scratch, by crawling the Internet and collecting the directory and files that are actually used by developers! DirBuster comes a total of 9 different lists, this makes DirBuster extremely effective at finding those hidden files and directories. And if that was not enough DirBuster also has the option to perform a pure brute force, which leaves the hidden directories and files nowhere to hide.

**Installed size:** `10.75 MB`  
**How to install:** `sudo apt install dirbuster`

Dependencies:

- default-jre

##### dirbuster

```console
root@kali:~# dirbuster -h
DirBuster - 1.0-RC1
Usage: java -jar DirBuster-1.0-RC1 -u <URL http://example.com/> [Options]

	Options:
	 -h : Display this help message
	 -H : Start DirBuster in headless mode (no gui), report will be auto saved on exit
	 -l <Word list to use> : The Word list to use for the list based brute force. Default: /home/kali/kali-www/bin/kali-tools/tool-output/dirbuster/directory-list-2.3-small.txt
	 -g : Only use GET requests. Default Not Set
	 -e <File Extention list> : File Extention list eg asp,aspx. Default: php
	 -t <Number of Threads> : Number of connection threads to use. Default: 10
	 -s <Start point> : Start point of the scan. Default: /
	 -v : Verbose output, Default: Not set
	 -P : Don't Parse html, Default: Not Set
	 -R : Don't be recursive, Default: Not Set
	 -r <location> : File to save report to. Default: /home/kali/kali-www/bin/kali-tools/tool-output/dirbuster/DirBuster-Report-[hostname]-[port].txt

Examples:

Run DirBuster in headless mode
java -jar DirBuster-1.0-RC1.jar -H -u https://www.target.com/

Start GUI with target prepopulated
java -jar DirBuster-1.0-RC1.jar -u https://www.target.com/
```

---

Updated on: 2024-Mar-11

**Credit:** This information was adapted from an excellent guide on [Kali.org](https://www.kali.org/tools/dirbuster/). Be sure to check out the original post for more details.

# Comprehensive Guide on Dirbuster Tool

[November 19, 2018](https://www.hackingarticles.in/comprehensive-guide-on-dirbuster-tool/) by [Raj](https://www.hackingarticles.in/author/raj/)

In this article, we are focusing on the transient directory using Kali Linux tool Dibuster and trying to find hidden files and directories within a web server.

### Table of Content

- What is DirBuster
- Default Mode
- GET Request Method
- Pure Brute Force (Numeric)
- Single Sweep (Non-recursive)
- Targeted Start
- Blank Extensions
- Search by File Type (.txt)
- Changing the DIR List
- Following Redirects
- Attack Through Proxy
- Adding File Extensions
- Evading Detective Measures (Requests Per Second)

### What is DirBuster

DirBuster is an application within the Kali arsenal that is designed to brute force web and application servers. The tool can brute force directories and files. The application lets users take advantage of multi-thread functionality to get things moving faster. In this article, we will give you an overview of the tool and its basic functions.

### Default Mode

We start DirBuster and only input [http://testphp.vulnweb.com/](http://testphp.vulnweb.com/) in the target URL field. Leave the rest of the options as they are. DirBuster will now auto switch between HEAD and GET requests to perform a list based brute force attack.

![](https://4.bp.blogspot.com/-Y5uC9Sq-Uxc/W_JyUpOWnrI/AAAAAAAAbNU/nOxjMlBkDCI1vYP2VbEfmRUkEUZqDgqzwCLcBGAs/s1600/1.png)

Let’s hit Start. DirBuster gets to work and starts brute forcing and we see various files and directories popping up in the result window.

![](https://4.bp.blogspot.com/-wMcKbqIeOvE/W_JyWyMUyEI/AAAAAAAAbOE/fWPtPSu3uqQAIdECeckU4qFt8WORJJVFACLcBGAs/s1600/2.png)

### GET Request Method

We will now set DirBuster to only use the GET request method. To make things go a little faster, the thread count is set to 200 and the “Go Faster” checkbox is checked.

![](https://4.bp.blogspot.com/-WLw8WCXdWIg/W_JyZ3nfiEI/AAAAAAAAbOw/QMgnMDjXtPMegYI2PILqMr6Fd4W8VUoyQCLcBGAs/s1600/3.png)

In the Results – Tree View we can see findings.

![](https://1.bp.blogspot.com/-05DztcERv9A/W_JycJRZDEI/AAAAAAAAbPA/tIUM5yYC4Bw_T11vejR-oc3V6hk-Vzk_QCLcBGAs/s1600/4.png)

### Pure Brute Force (Numeric)

DirBuo performs step allows a lot of control over the attack process, in this set we will be using only numerals to perform a pure brute force attack. This is done by selecting “Pure Brute Force” in the scanning type option and selecting “0-9” in the charset drop-down menu. By default, the minimum and maximum character limit are set.

![](https://1.bp.blogspot.com/-rf-5fo24JBg/W_JyccYhzsI/AAAAAAAAbPE/DQ2lMiMPL0sL23SuMXjtGF_QBG9NJXaSQCLcBGAs/s1600/5.png)

In the Results – Tree View we can see findings.

![](https://2.bp.blogspot.com/-snrJEH1p4q0/W_Jycuu7j0I/AAAAAAAAbPI/JCwTx7pWsAwHh7aEcDgHe19PhiunovO3gCLcBGAs/s1600/6.png)

### Single Sweep (Non-recursive)

We will now perform a single sweep brute force where the dictionary words are used only once. To achieve this, we will unselect the “Be Recursive” checkbox.

![](https://2.bp.blogspot.com/-AMQvyjMBjcM/W_JyczdN1kI/AAAAAAAAbPM/p6d9TvXLrskr9A8KowtU-9bV-6inuTPSwCLcBGAs/s1600/7.png)

In the Results – ListView we can see findings.

![](https://3.bp.blogspot.com/-JqMtGy_kB7c/W_Jycz2eivI/AAAAAAAAbPQ/PhmqZ-xqzoE77v-o-8g4xQD1w8923cA_gCLcBGAs/s1600/8.png)

### Targeted Start

Further exploring the control options provided by DirBuster, we will set it up to start looking from the “admin” directory. In the “Dir to start with” field, type “/admin” and hit start.

![](https://3.bp.blogspot.com/-JlQDoFGIzKY/W_JydTgpITI/AAAAAAAAbPU/uxdzvEieLr8LMh3c4EYwArrvWrNiocMzgCLcBGAs/s1600/9.png)

In the Results – Tree View we can see findings.

![](https://4.bp.blogspot.com/-rJsKgbsHeew/W_JyUnt2l9I/AAAAAAAAbNY/wkK6141PEPw-bDLPV8NSXTNG-eHOaJsYACLcBGAs/s1600/10.png)

### Blank Extensions

DirBuster can also look into directories with a blank extension, this could potentially uncover data that might be otherwise left untouched. All we do is check the “Use Blank Extension” checkbox.

![](https://3.bp.blogspot.com/-tp0muT-FCGs/W_JyUwUAgXI/AAAAAAAAbNc/Cdoa3vWWafsm4xdHkLKEbW4HSDPKdeu1QCLcBGAs/s1600/11.png)

We can see the processing happen and DirBuster testing to find directories with blank extensions.

![](https://2.bp.blogspot.com/-DV4T5j4LOTU/W_JyVH66ZRI/AAAAAAAAbNg/Tfyb52romjcDxcoQv4fKSbxMEKpi0bdTACLcBGAs/s1600/12.png)

### Search by File Type (.txt)

We will be setting the file extension type to .txt, by doing so, DirBuster will look specifically for files with a .txt extension. Type “.txt” in the File extension field and hit start.

![](https://3.bp.blogspot.com/-jynCm6CVGV8/W_JyVQ52_TI/AAAAAAAAbNk/rb7kPSahseQ_WEg1MooHvbWV6Sd0ZekbwCLcBGAs/s1600/13.png)

We can see the processing happen and DirBuster testing to find directories with a .txt extension.

![](https://3.bp.blogspot.com/-jipzVabmcT8/W_JyVVhHXdI/AAAAAAAAbNo/V0D1TDQkf-8hDlBKS1aENlW4uXgbiP4kQCLcBGAs/s1600/14.png)

### Changing the DIR List

We will now be changing the directory list in DirBuster. Options > Advanced Options > DirBuster Options > Dir list to use. Here is where we can browse and change the list to “directory-list-2.3-medium.txt”, found at /usr/share/dirbuster/wordlists/ in Kali.

![](https://2.bp.blogspot.com/-lhqWab0zTxM/W_JyV_ro3EI/AAAAAAAAbNs/Om-h59IoBzUuSh_zv_nTMtQa0ySgYMyIgCLcBGAs/s1600/15.png)

We can see the word list is now set.

![](https://1.bp.blogspot.com/-qXR4txarnKg/W_JyV5MF0aI/AAAAAAAAbNw/-zBCRo7O1nUHrXiNs4VASz7YZ-n-3-drACLcBGAs/s1600/16.png)

### Following Redirects

DirBuster by default is not set to follow redirects during the attack, but we can enable this option under Options > Follow Redirects.

![](https://2.bp.blogspot.com/-GyKO0z8CcHo/W_JyWKZ6vSI/AAAAAAAAbN0/jtRtsG3wHwwMEtofutiWE0hGTsIUzMJfACLcBGAs/s1600/17.1.png)

We can see the results in the scan information as the test progresses.

![](https://2.bp.blogspot.com/-tDgTdsGwzT4/W_JyWSzpDXI/AAAAAAAAbN4/iBYQ-Lms-BY5kvNt-LJaMqrWN2CrHROfACLcBGAs/s1600/17.png)

Results in the Tree View.

![](https://4.bp.blogspot.com/-omfikNFWgXI/W_JyWqTXk5I/AAAAAAAAbN8/F8wqm8Mai4syB7XlKlJuGGf8Cp-KZDmtwCLcBGAs/s1600/18.png)

### Attack through Proxy

DirBuster can also attack using a proxy. In this scenario, we try to open a webpage at 192.168.1.108 but are denied access.

![](https://3.bp.blogspot.com/-AnON11yR-sg/W_JyXJfhRLI/AAAAAAAAbOM/oT5JXQ9yVPEqqV4HcYScKhVETP-iGd_5wCLcBGAs/s1600/21.png)

We set the IP in DirBuster as the attack target.

![](https://1.bp.blogspot.com/-gvYoGW_0caE/W_JyXo4wraI/AAAAAAAAbOQ/v0DfW__r12caAj7xdg33RwAVFioXeUUxwCLcBGAs/s1600/22.png)

Before we start the attack, we set up the proxy option under Options > Advance Options > Http Options. Here we check the “Run through a proxy” checkbox, input the IP 192.168.1.108 in the Host field and set the port to 3129.

![](https://3.bp.blogspot.com/-vy8EwwyvalI/W_JyXuZu2TI/AAAAAAAAbOU/EVQbO-kynfglmnUNlItHdx4wO0XGSKO2QCLcBGAs/s1600/23.png)

We can see the test showing results.

![](https://1.bp.blogspot.com/-F5myy8cYhNI/W_JyXx7KC_I/AAAAAAAAbOY/NLAs9MXTobsz0g9ciRR0YidL5WTlFcbXQCLcBGAs/s1600/24.png)

### Adding File Extensions

Some file extensions are not set to be searched for in DirBuster, mostly image formats. We can add these to be searched for by navigating to Options > Advanced Options > HTML Parsing Options.

![](https://3.bp.blogspot.com/-Aa4Bn8gVBto/W_JyYKYrzKI/AAAAAAAAbOc/nDFScMgY4qM0JJ3iYoxnc5tHr5EXKbv5QCLcBGAs/s1600/25.png)

We will delete jpeg in this instance and click OK.

![](https://2.bp.blogspot.com/-k6gApf5Eczc/W_JyYCL_tcI/AAAAAAAAbOg/Dc7MUp6gw2MbXr77_4oY2Ll3KhZag5qvwCLcBGAs/s1600/26.png)

In the File Extension filed we will type in “jpeg” to explicitly tell DirBuster to look for .jpeg format files.

![](https://2.bp.blogspot.com/-G6Uj7jkB_9k/W_JyYRfAggI/AAAAAAAAbOk/5dUr23uy4fclzhNuARS-nqJqTcpuzcbdwCLcBGAs/s1600/27.png)

We can see in the testing process, DirBuster is looking for and finding jpeg files.

![](https://3.bp.blogspot.com/-4ujyN5NVQIk/W_JyY4QpDhI/AAAAAAAAbOo/IgzxaU66t74K1o7DKODTzBap9dkjD9_hwCLcBGAs/s1600/28.png)

### Evading Detective Measures

Exceeding the warranted requests per second during an attack is a sure shot way to get flagged by any kind of detective measures put into place. DirBuster lets us control the requests per second to bypass this defense. Options > Advanced Options > Scan Options is where we can enable this setting.

![](https://1.bp.blogspot.com/-ZT4bImD6Okw/W_JyZX_xEGI/AAAAAAAAbOs/EBQ37wUx1mwgF1UCUuF_Bni8MYsncfeYgCLcBGAs/s1600/29.png)

We are setting Connection Time Out to 500, checking the Limit number of requests per second and setting that field to 20.

![](https://1.bp.blogspot.com/-HcfBtbG5Nfg/W_JyaXdUdBI/AAAAAAAAbO0/SKyCXWeC37knQDXis_R0HR17A1KyT9FQwCLcBGAs/s1600/30.png)

Once the test initiated, we will see the results. The scan was stopped to show the initial findings.

![](https://4.bp.blogspot.com/-4yPVyhjOhlk/W_Jya3ooRbI/AAAAAAAAbO4/XD_tY5YVpK80eK7wqWcmAvfpmfKdg93OACLcBGAs/s1600/31.png)

Once the scan is complete the actual findings can be seen.

![](https://2.bp.blogspot.com/-IUXf54c-c3I/W_JybgogfSI/AAAAAAAAbO8/tCuhIvy3BLE_74eCisrofqN6Vur774vHgCLcBGAs/s1600/32.png)

We hope you enjoy using this tool. It is a great tool that’s a must in a pentester’s arsenal.

Stay tuned for more articles on the latest and greatest in hacking.

**Author**: Shubham Sharma is a Cybersecurity enthusiast and Researcher in the field of WebApp Penetration testing. Contact [**here**](https://www.linkedin.com/in/shubham-sharma-626964153/)

**Credit:** This information was adapted from an excellent guide on [HackingArticles.in](https://www.hackingarticles.in/comprehensive-guide-on-dirbuster-tool/). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/D-ymPeggEFM?si=LRWTUA5HnbsK7WVD" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=D-ymPeggEFM). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/DnG3l6hH9eg?si=BT90CfErJK-XwsjW" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=DnG3l6hH9eg). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/mEkZlfWYGLY?si=TCWW-GYk1pql9MhY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=mEkZlfWYGLY). Be sure to check out the original post for more details.


