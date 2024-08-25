# Tool Documentation:

## dirb Usage Example

Scan the web server (`http://192.168.1.224/`) for directories using a dictionary file (`/usr/share/wordlists/dirb/common.txt`):

```console
root@kali:~# dirb http://192.168.1.224/ /usr/share/wordlists/dirb/common.txt

-----------------
DIRB v2.21
By The Dark Raver
-----------------

START_TIME: Fri May 16 13:41:45 2014
URL_BASE: http://192.168.1.224/
WORDLIST_FILES: /usr/share/wordlists/dirb/common.txt

-----------------

GENERATED WORDS: 4592

---- Scanning URL: http://192.168.1.224/ ----
==> DIRECTORY: http://192.168.1.224/.svn/
+ http://192.168.1.224/.svn/entries (CODE:200|SIZE:2726)
+ http://192.168.1.224/cgi-bin/ (CODE:403|SIZE:1122)
==> DIRECTORY: http://192.168.1.224/config/
==> DIRECTORY: http://192.168.1.224/docs/
==> DIRECTORY: http://192.168.1.224/external/
```

---

  

# Packages and Binaries:

### dirb

DIRB is a Web Content Scanner. It looks for existing (and/or hidden) Web Objects. It basically works by launching a dictionary based attack against a web server and analyzing the responses.

DIRB comes with a set of preconfigured attack wordlists for easy usage but you can use your custom wordlists. Also DIRB sometimes can be used as a classic CGI scanner, but remember that it is a content scanner not a vulnerability scanner.

DIRB’s main purpose is to help in professional web application auditing. Specially in security related testing. It covers some holes not covered by classic web vulnerability scanners. DIRB looks for specific web objects that other generic CGI scanners can’t look for. It doesn’t search vulnerabilities nor does it look for web contents that can be vulnerable.

**Installed size:** `1.43 MB`  
**How to install:** `sudo apt install dirb`

Dependencies:

- libc6
- libcurl4t64

##### dirb

Web Content Scanner

```console
root@kali:~# man dirb
DIRB(1)                     General Commands Manual                     DIRB(1)

NAME
       dirb - Web Content Scanner

SYNOPSIS
       dirb <url_base> <url_base> [<wordlist_file(s)>] [options]

DESCRIPTION
       DIRB IS a Web Content Scanner. It looks for existing (and/or hidden) Web
       Objects.  It  basically  works  by  launching a dictionary basesd attack
       against a web server and analizing the response.

OPTIONS
       -a <agent_string>
              Specify your custom USER_AGENT.  (Default is: "Mozilla/4.0  (com-
              patible; MSIE 6.0; Windows NT 5.1)")

       -b     Don't squash or merge sequences of /../ or /./ in the given URL.

       -c <cookie_string>
              Set a cookie for the HTTP request.

       -E <certificate>
              Use the specified client certificate file.

       -f     Fine tunning of NOT_FOUND (404) detection.

       -H <header_string>
              Add a custom header to the HTTP request.

       -i     Use case-insensitive Search.

       -l     Print "Location" header when found.

       -N <nf_code>
              Ignore responses with this HTTP code.

       -o <output_file>
              Save output to disk.

       -p <proxy[:port]>
              Use this proxy. (Default port is 1080)

       -P <proxy_username:proxy_password>
              Proxy Authentication.

       -r     Don't Search Recursively.

       -R     Interactive  Recursion.   (Ask  in  which directories you want to
              scan)

       -S     Silent Mode. Don't show tested words. (For dumb terminals)

       -t     Don't force an ending '/' on URLs.

       -u <username:password>
              Username and password to use.

       -v     Show Also Not Existent Pages.

       -w     Don't Stop on WARNING messages.

       -x <extensions_file>
              Amplify search with the extensions on this file.

       -X <extensions>
              Amplify search with this extensions.

       -z <milisecs>
              Amplify search with this extensions.

SEE ALSO
       brain(x)

The Dark Raver                     27/01/2009                           DIRB(1)
```

---

##### dirb-gendict

Generate dictionary incrementally

```console
root@kali:~# dirb-gendict -h
Usage: dirb-gendict -type pattern
  type: -n numeric [0-9]
        -c character [a-z]
        -C uppercase character [A-Z]
        -h hexa [0-f]
        -a alfanumeric [0-9a-z]
        -s case sensitive alfanumeric [0-9a-zA-Z]
  pattern: Must be an ascii string in which every 'X' character wildcard
           will be replaced with the incremental value.

Example: dirb-gendict -n thisword_X
  thisword_0
  thisword_1
  [...]
  thisword_9
```

---

##### html2dic

Dump word dictionary from html input file

```console
root@kali:~# man html2dic
HTML2DIC(1)                 General Commands Manual                 HTML2DIC(1)

NAME
       html2dic - Dump word dictionary from html input file

SYNOPSIS
       html2dic <file>

DESCRIPTION
       html2dic extract all words from an HTML page, generating a dictionary of
       all word found, one word per line.  Output is printed on stdout.

SEE ALSO
       dirb(1),dirb-gendict(1)

Philippe Thierry                   15/06/2017                       HTML2DIC(1)
```

---

Updated on: 2024-May-23

**Credit:** This information was adapted from an excellent guide on [Kali.org](https://www.kali.org/tools/dirb/). Be sure to check out the original post for more details.

# Introduction to Dirb – Kali Linux

Last Updated : 01 Sep, 2023

Dirb is an online directory scanner that searches web servers for hidden files, directories, and pages. It is a free and open-source utility included in the [Kali Linux](https://www.geeksforgeeks.org/introduction-to-kali-linux/) distribution, a popular operating system for [penetration testing](https://www.geeksforgeeks.org/software-testing-penetration-testing/) and [ethical hacking](https://www.geeksforgeeks.org/introduction-to-ethical-hacking/). Dirb may be used to detect typical web server folders and files, such as admin pages, backup files, and configuration files. It operates by sending [HTTP](https://www.geeksforgeeks.org/http-full-form/) queries to the server and analyzing the answers to identify the existence of a file or directory.

### Working

It features an internal word list file with roughly 4000 words for brute force attacks. There are many updated wordlists accessible on the internet that may be utilized as well. Dirb scans every directory or object of a website or server for the terms in its wordlist. There might be an admin panel or a subfolder that is under assault. The trick is to locate the things, which are usually hidden.

## Installation of Dirb on Kali Linux

Generally, Dirb is pre-installed in Kali Linux but in case you are using some different Linux distro other than Kali Linux then use the following command in the terminal (Command Line Interface):

sudo [apt-get](https://www.geeksforgeeks.org/apt-get-command-in-linux-with-examples/) install dirb

After using the above command, the output will look similar to as shown in the below screenshot.

![installation of Dirb](https://media.geeksforgeeks.org/wp-content/uploads/20230404130236/install.png)

The package manager may vary corresponding to different Linux distros. Here in the case of [Debian](https://www.debian.org/), you are using _****apt****_.

Other than this, Dirb can be downloaded from the following sources too.

- [https://sourceforge.net/projects/dirb/](https://sourceforge.net/projects/dirb/)
- [https://github.com/v0re/dirb](https://github.com/v0re/dirb) 

After installation, it can be verified using just a simple instruction 

dirb

The output will contain the version information and the help menu.

![help menu](https://media.geeksforgeeks.org/wp-content/uploads/20230404130727/helpmenu.png)

## Usage of Dirb

#### Example 1: Scanning single domain

Once installed, you can start using Dirb by opening a terminal window and typing the following command:

dirb http://example.com

At the place of ****http://example.com****, you can use the URL ([Uniform Resource Locator](https://www.geeksforgeeks.org/url-full-form/)) of your choice of target. With its default wordlist, it will start brute forcing directories with around 4600 words.

![dirb scan](https://media.geeksforgeeks.org/wp-content/uploads/20230317020408/dirbscan.png)

The results list includes the response code and the size of the file for each ping. In addition, dirb begins examining the folder’s files, returning the response code 200. It uses the wordlist to search all folders and presents the results.

![Output of single domain scan](https://media.geeksforgeeks.org/wp-content/uploads/20230317022729/outputdirb.png)

If you want to scan a target with a different wordlist, then it can be done easily using the following command:

dirb http://www.example.com -w wordlist.txt

You can also specify the path of the wordlist instead of the direct filename in case you are in a different directory.

#### Example 2: Using multiple wordlists

The usual wordlist_files common.txt is used by the aforementioned attack, but we are able to alter this word list and can choose a different wordlist for directory traversal. To examine all of the accessible wordlists, you must take the following route.

cd /usr/share/wordlists/dirb && ls -la
cd /usr/share/wordlists/dirb/vulns && ls -la

Output can be seen in the below screenshots:

![/usr/share/wordlists/dirb](https://media.geeksforgeeks.org/wp-content/uploads/20230403231230/word_1.png)

![cd /usr/share/wordlists/dirb/vulns](https://media.geeksforgeeks.org/wp-content/uploads/20230403231434/word_2.png)

Dirb may be used to search for certain susceptible items inside specific web technologies. Each web technology has its own set of flaws. They are not all alike. Dirb can assist us in looking for certain susceptible things that are specific to technology. In Kali, dirb uses specialized wordlists to look for these delicate and frequently used techs. The wordlist shown in the above screenshots can be used for directory traversing corresponding to the type of target.

For each of the various vulnerabilities to test, as you can see above, there are a variety of file lists. Use apache.txt to test your Apache web server if you wish to.

#### Example 3: Default Working

By default, Dirb uses common.txt as a wordlist which we can find in below mentioned directory.

/usr/share/wordlists/dirb

And there’s no need to mention this default wordlist while using Dirb in default mode. Dirb can be used in default mode by using the below snippet:

dirb http://example.com

#### Example 4: Saving Output to a file

We save the result of the dirb scan onto a file for the purpose of record management, improved reading, and future references. To do this, we’ll use the dirb scan option -o, which allows us to save the results as a text file.

dirb http://example.com -o result.txt

This will simply create a new file output.txt and will save the results of the scan in it.

![Saving output to file](https://media.geeksforgeeks.org/wp-content/uploads/20230405150155/output.png)

As the ****-o**** switch is used, the output will get saved in the results.txt file. Let’s check on that file:

![Viewing saved output](https://media.geeksforgeeks.org/wp-content/uploads/20230405150601/out2.png)

#### Example 5: Limiting enumeration with specific extensions

The ****-X**** option of the dirb scan can be used in a variety of circumstances where we need to retrieve the directories on the target server that have a particular suffix. This parameter takes the file extension name and then scans the target server or computer for files with the specified extension.

dirb http://example.com -X .php

This way the output will only contain .php results. Output is in the below screenshot:

![Only retriving .php sites](https://media.geeksforgeeks.org/wp-content/uploads/20230403233148/extension.png)

#### Example 6: Ignoring specific status codes

The Status-Code element is a three-digit integer whose first digit designates the answer class and who’s last two digits serve no classification purpose. As shown below, we are using the -N option on code 302 in this assault. This can be achieved by using a flag ****-N**** with desired value to ignore the status code.

dirb http://example.com -N 302

It will ignore the pages/directories which will respond to 302 as a status code.

![Ignoring 302 code](https://media.geeksforgeeks.org/wp-content/uploads/20230405142512/ignoring.png)

#### Example 7: Speed Delaying

When working in various situations, there are some environments that we encounter that cannot manage the flood caused by the dirb scan; it is crucial that we postpone the scan for a while in these environments. Using the dirb scan’s ****-z**** option makes this simple to accomplish. The duration is given in milliseconds for this parameter. We have given dirb a 100-second delay, just as in the sample we’ve provided.

dirb://example.com -z 100

![Speed Delaying](https://media.geeksforgeeks.org/wp-content/uploads/20230404002412/speed_delay.png)

speed delay

As mentioned, it will delay by 100 milliseconds.

#### Example 8: Without recursiveness

By default, the dirb search traverses all folders. It entails scanning a path and then moving around within it to look for additional subcategories. However, we configured the dirb to not search recursively in some circumstances where there is not enough time. The ****-r**** option can be used to accomplish this.

dirb http://example.com -r

The output of this will be something like this:

![Without Recursiveness](https://media.geeksforgeeks.org/wp-content/uploads/20230404002906/not_recursive.png)

without recursively

In this case, dirb will not scan the directories recursively.

#### Example 9: Showing non-existing pages

An [HTTP](https://www.geeksforgeeks.org/http-full-form/) response number of 404 indicates that a website’s server was unable to locate the page you were attempting to access. Individual websites frequently alter the 404 Not Found error notices. In some cases, we also need to locate the 404 sites, which dirb by default ignores. We will use the -v option to locate those sites.

dirb http://example.com -v

It will show the output in a verbose mode which means it will show all the requests that dirb is sending to the target web.

![Showing Non-Existing Pages](https://media.geeksforgeeks.org/wp-content/uploads/20230404003616/non_exist.png)

verbose mode

#### Example 10: HTTP AUTHORIZATION (-u user: pass)

The 401-status code and WWW-Authenticate answer header are the foundation of all HTTP authentication/authentication methods. Basic HTTP security methods are the most popular. User name and password are sent by the client in base64-encoded, plaintext form.

So, using dirb, we used the instruction below to get around this type of authentication:

dirb http://testphp.vulnweb.com/login.php -u test:test

![HTTP Authorization](https://media.geeksforgeeks.org/wp-content/uploads/20230404004419/user_pass.png)

-u test:test

The outcome is that the target URL displays Status-code 200 for the test: test and authorized identity.  
 

#### Example 11: Custom User-Agent

Scanning a website using a custom user-agent:

> dirb http://www.example.com -a “Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/58.0.3029.110 Safari/537.36 Edge/16.16299”

The output of this instruction will look like the below-shown screenshot:

![Custom User-Agent](https://media.geeksforgeeks.org/wp-content/uploads/20230405143735/user-agent.png)

This will send requests using the custom user-agent which is provided in the instruction. For more information regarding user agents, read this article [user-agents](https://www.geeksforgeeks.org/http-headers-user-agent/).

### Conclusion

Overall, Dirb is a strong tool for locating hidden directories and files on web servers. Yet, it is critical to utilize it ethically and with the website owner’s consent. Unethical usage of Dirb may result in legal ramifications. The primary goal is to support expert online application monitoring. Particularly in testing that involves security. It plugs some gaps that conventional online [vulnerability](https://www.geeksforgeeks.org/vulnerabilities-in-information-security/) analyzers do not. Dirb searches for particular web items that other general CGI analyzers are unable to search for. It neither searches for flaws nor looks for potentially vulnerable online material.

**Credit:** This information was adapted from an excellent guide on [GeeksForGeeks](https://www.geeksforgeeks.org/introduction-to-dirb-kali-linux/). Be sure to check out the original post for more details.

# How to Use Dirb for Directory Enumeration in Kali Linux

## Install Dirb

Dirb is a powerful directory enumeration tool that is used to discover hidden files and directories on web servers. It is included in the Kali Linux distribution and can be used to quickly enumerate web directories. In this tutorial, we will show you how to install and use Dirb in Kali Linux.

To install Dirb, open a terminal window and type the following command:

```
sudo apt-get install dirb
```

Once the installation is complete, you can run Dirb by typing the following command:

```
dirb
```

You can also use the [official documentation](https://www.kali.org/docs/tools/dirb/) for more information on how to use Dirb. Once you have installed Dirb, you can start using it to enumerate web directories.

## Run Dirb

Dirb is a powerful directory enumeration tool that can be used to discover hidden files and directories on web servers. To run Dirb, open a terminal window in Kali Linux and type the following command: `dirb http://example.com`. This will initiate a scan of the specified website and search for any hidden directories or files. You can also specify a wordlist to use for the scan, which can be done by adding the `-w` flag followed by the path to the wordlist file. For example, `dirb http://example.com -w /usr/share/wordlists/dirb/common.txt`. You can also use proxies to scan the website, which can be done by adding the `-p` flag followed by the proxy address. For example, `dirb http://example.com -p http://127.0.0.1:8080`. Additionally, you can use the `-r` flag to enable recursive scanning, which will scan all subdirectories of the specified website. For example, `dirb http://example.com -r`. Once the scan is complete, the results will be displayed in the terminal window. You can also view the results in a web browser by navigating to the [http://example.com/dirb/](http://example.com/dirb/) directory.

## View the Results

Once you have run Dirb, you can view the results in the terminal window. The results will show the directory and file names that Dirb has found. You can also view the results in a text file. To do this, use the `-o` option when running Dirb. This will save the results to a text file. You can then open the text file to view the results.

dirb http://example.com/ -o results.txt
Copy

The results will show the directory and file names that Dirb has found. You can also view the results in a text file. To do this, use the `-o` option when running Dirb. This will save the results to a text file. You can then open the text file to view the results. You can also use the `-r` option to recursively scan the directories and subdirectories. This will give you a more comprehensive list of the directories and files that Dirb has found.

## Use Wordlists

Wordlists are a great way to increase the effectiveness of Dirb. Wordlists are collections of words that are used to guess the names of directories and files on a web server. By using a wordlist, Dirb can quickly and easily identify hidden directories and files on a web server. To use a wordlist with Dirb, you need to specify the path to the wordlist file in the command line. For example, if you have a wordlist file named “wordlist.txt” in the same directory as Dirb, you can use the following command to use the wordlist:

dirb http://example.com/ /path/to/wordlist.txt
Copy

You can also use multiple wordlists in a single command. To do this, you need to specify the path to each wordlist file in the command line. For example, if you have two wordlist files named “wordlist1.txt” and “wordlist2.txt” in the same directory as Dirb, you can use the following command to use both wordlists:

dirb http://example.com/ /path/to/wordlist1.txt /path/to/wordlist2.txt
Copy

You can find a variety of wordlists online, such as [SecLists](https://github.com/danielmiessler/SecLists/tree/master/Discovery/Web-Content) and [FuzzDB](https://github.com/fuzzdb-project/fuzzdb). It is important to note that some wordlists may contain words that are not appropriate for use in a production environment. Therefore, it is important to review the wordlist before using it with Dirb.

## Use Proxies

Using proxies with Dirb can be a great way to hide your identity while performing directory enumeration. To use a proxy with Dirb, you need to specify the proxy address and port in the command line. For example, if you are using a proxy with the address 192.168.1.1 and port 8080, you would use the following command:

dirb http://example.com/ -p 192.168.1.1:8080
Copy

You can also use a SOCKS proxy with Dirb. To do this, you need to specify the proxy type and address in the command line. For example, if you are using a SOCKS proxy with the address 192.168.1.1 and port 1080, you would use the following command:

dirb http://example.com/ -P socks4://192.168.1.1:1080
Copy

You can also use a proxy list with Dirb. To do this, you need to specify the proxy list file in the command line. For example, if you are using a proxy list file named “proxy_list.txt”, you would use the following command:

dirb http://example.com/ -i proxy_list.txt
Copy

Using proxies with Dirb can be a great way to protect your identity while performing directory enumeration. It is important to remember to use a secure proxy and to use a proxy list file if you are using multiple proxies. For more information on using proxies with Dirb, please refer to the [Dirb documentation](https://tools.kali.org/web-applications/dirb).

## Use Recursive Scanning

Recursive scanning is a powerful feature of Dirb that allows you to scan a website for all its subdirectories and files. This is especially useful when you are trying to find hidden directories and files on a website. To use recursive scanning, you need to use the `-r` flag when running Dirb. For example, if you wanted to scan the website [example.com](https://example.com/) recursively, you would run the following command:

dirb https://example.com -r
Copy

This will scan the website for all its subdirectories and files. You can also specify a wordlist to use when scanning. To do this, you need to use the `-w` flag. For example, if you wanted to scan the website [example.com](https://example.com/) using the wordlist `wordlist.txt`, you would run the following command:

dirb https://example.com -r -w wordlist.txt
Copy

This will scan the website for all its subdirectories and files using the specified wordlist. You can also specify a proxy to use when scanning. To do this, you need to use the `-p` flag. For example, if you wanted to scan the website [example.com](https://example.com/) using the proxy `127.0.0.1:8080`, you would run the following command:

dirb https://example.com -r -p 127.0.0.1:8080
Copy

This will scan the website for all its subdirectories and files using the specified proxy. Recursive scanning is a powerful feature of Dirb that can help you find hidden directories and files on a website. It is important to remember to use the `-r` flag when running Dirb to enable recursive scanning.

### Useful Links

- [Dirb Overview](https://www.kali.org/penetration-testing/dirb/)
- [Dirb Download](https://tools.kali.org/web-applications/dirb)
- [Dirb Tutorial](https://www.offensive-security.com/kali-linux/dirb/)
- [Dirb Enumeration in Kali Linux](https://www.hackingarticles.in/dirb-directory-enumeration-in-kali-linux/)
- [Dirb Enumeration in Kali Linux (2)](https://www.hackingloops.com/dirb-directory-enumeration-in-kali-linux/)
- [Dirb Enumeration in Kali Linux (3)](https://www.cybrary.it/0p3n/dirb-directory-enumeration-in-kali-linux/)

**Credit:** This information was adapted from an excellent guide on [Anovin.mk](https://anovin.mk/tutorial/how-to-use-dirb-for-directory-enumeration-in-kali-linux/). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/mtnGfE9d5BM?si=_XIwFH1qiHWtauce" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=mtnGfE9d5BM). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/JMeIpXtQxAg?si=pRz-P-N49_cfebST" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=mtnGfE9d5BM). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/WZDx3zk8NwI?si=vKIlPGcE-IitLxqR" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=WZDx3zk8NwI). Be sure to check out the original post for more details.

