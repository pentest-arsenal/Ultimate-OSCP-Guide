When using **OWASP ZAP** during the OSCP exam, you should be cautious about certain features that could lead to automated exploitation, which is prohibited under the exam rules. Here’s a breakdown of what you should avoid:

### **Features to Avoid in OWASP ZAP:**

1. **Automated Scanning:**
    
    - **Active Scan**: This feature automatically scans for vulnerabilities in a web application by attempting to exploit them. Using the Active Scan feature could lead to automatic discovery and exploitation of vulnerabilities, which is not allowed during the OSCP exam.
    - **Spidering (with Active Scanning)**: The Spider tool itself, which crawls the web application to discover all the pages, is generally allowed. However, enabling automatic active scanning after spidering could lead to disqualification because it attempts to exploit vulnerabilities it finds during the crawl.
2. **Automated Fuzzing:**
    
    - **Fuzzer**: OWASP ZAP’s fuzzer allows you to inject different inputs to test for vulnerabilities automatically. While fuzzing in a controlled, manual way might be acceptable, the automated nature of this tool can push it into the realm of automated exploitation, so it’s better to avoid it.
3. **Passive Scanning with Automatic Actions:**
    
    - While **Passive Scanning** itself (which analyzes traffic without actively manipulating or attacking the web application) is generally allowed, ensure that it does not trigger any automated actions that could exploit vulnerabilities.
4. **Forced Browsing and Brute Force Tools:**
    
    - **Forced Browse**: This tool brute forces directories and files on a web server to discover hidden content. While forced browsing in itself may not directly exploit vulnerabilities, using it extensively in an automated manner can be risky, and you should avoid it to stay within the guidelines.

### **Safe Features to Use:**

1. **Manual Testing Tools:**
    
    - **Manual Intercept/Proxy**: You can use ZAP as an intercepting proxy to manually analyze and modify HTTP/HTTPS requests and responses. This is a safe and valuable feature for manual testing.
    - **Manual Request Editor (similar to Burp’s Repeater)**: Manually editing and resending HTTP requests is allowed and useful for in-depth testing of specific parameters.
2. **Spider (without Active Scan):**
    
    - **Spidering** to map out the web application is generally safe as long as it’s not followed by an automatic active scan.
3. **Passive Scanning (without triggering exploits):**
    
    - **Passive Scanning** of traffic to identify issues without sending malicious requests or performing attacks is allowed.

### **General Recommendation:**

To stay within the OSCP exam rules, focus on **manual testing** and **passive analysis**. Avoid using any automated features that could lead to vulnerability exploitation without your direct control. Always double-check the settings before running scans to ensure that nothing will be automatically exploited.

By carefully managing how you use OWASP ZAP, you can leverage its powerful capabilities while staying within the guidelines of the OSCP exam.

#  [![](https://raw.githubusercontent.com/wiki/zaproxy/zaproxy/images/zap32x32.png) ZAP](https://www.zaproxy.org/)

[](https://github.com/zaproxy/zaproxy#-zap)

[![License](https://camo.githubusercontent.com/9ac7b34c6dcab13f731853c75d396b3b425c37cd2e5096a7610fd84f2105e42d/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f6c6963656e73652d417061636865253230322d3445423142412e737667)](https://www.apache.org/licenses/LICENSE-2.0.html) [![GitHub release](https://camo.githubusercontent.com/856752e5ecec79b34b8067c92016cd8f5e8b8ad4ac01655cbd724ab4674da690/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f72656c656173652f7a6170726f78792f7a6170726f78792e737667)](https://www.zaproxy.org/download/) [![Java CI](https://github.com/zaproxy/zaproxy/actions/workflows/ci.yml/badge.svg)](https://github.com/zaproxy/zaproxy/actions/workflows/ci.yml) [![CII Best Practices](https://camo.githubusercontent.com/8c466cbd91a31e0dc537e40796ab0faa0cc45f0ac2c4f03b368dbcb775ae2096/68747470733a2f2f626573747072616374696365732e636f7265696e6672617374727563747572652e6f72672f70726f6a656374732f32342f6261646765)](https://bestpractices.coreinfrastructure.org/projects/24) [![Github Releases](https://camo.githubusercontent.com/09067277bd7037859b3fe3939c98d418fe3f04b9712dabd075a116fe30c4c2a0/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f646f776e6c6f6164732f7a6170726f78792f7a6170726f78792f6c61746573742f746f74616c2e7376673f6d61784167653d32353932303030)](https://zapbot.github.io/zap-mgmt-scripts/downloads.html) [![javadoc](https://camo.githubusercontent.com/05494c8b560a919c5e2ce1b0dc6a52b12db37299deeaa540ac018208da8f561c/68747470733a2f2f6a617661646f632e696f2f6261646765322f6f72672e7a6170726f78792f7a61702f6a617661646f632e737667)](https://javadoc.io/doc/org.zaproxy/zap) [![CodeQL](https://github.com/zaproxy/zaproxy/actions/workflows/codeql.yml/badge.svg)](https://github.com/zaproxy/zaproxy/actions/workflows/codeql.yml) [![Quality Gate Status](https://camo.githubusercontent.com/bc7c15b1aa325852ade9d78944d96de1b8b9e06a06f18a1390d638acc72c03a2/68747470733a2f2f736f6e6172636c6f75642e696f2f6170692f70726f6a6563745f6261646765732f6d6561737572653f70726f6a6563743d7a6170726f78795f7a6170726f7879266d65747269633d616c6572745f737461747573)](https://sonarcloud.io/dashboard?id=zaproxy_zaproxy) [![Open Source Helpers](https://camo.githubusercontent.com/333f945b97d30036151065e63453ace196c77048c6a9f3e0c4271c96fe81bed6/68747470733a2f2f7777772e636f64657472696167652e636f6d2f7a6170726f78792f7a6170726f78792f6261646765732f75736572732e737667)](https://www.codetriage.com/zaproxy/zaproxy) [![Twitter Follow](https://camo.githubusercontent.com/3a151a035648571346b45f1b8accc86b7c5eeb8a8433745b11e8c3c1494481a3/68747470733a2f2f696d672e736869656c64732e696f2f747769747465722f666f6c6c6f772f7a6170726f78792e7376673f7374796c653d736f6369616c266c6162656c3d466f6c6c6f77266d61784167653d32353932303030)](https://twitter.com/zaproxy)

[![Integration Tests](https://github.com/zaproxy/zaproxy/actions/workflows/run-integration-tests.yml/badge.svg)](https://github.com/zaproxy/zaproxy/actions/workflows/run-integration-tests.yml/badge.svg) [![Docker Live Release](https://github.com/zaproxy/zaproxy/actions/workflows/release-live-docker.yml/badge.svg)](https://github.com/zaproxy/zaproxy/actions/workflows/release-live-docker.yml/badge.svg)

The Zed Attack Proxy (ZAP) is one of the world’s most popular free security tools and is actively maintained by a dedicated international team of volunteers. It can help you automatically find security vulnerabilities in your web applications while you are developing and testing your applications. It's also a great tool for experienced pentesters to use for manual security testing.

[![](https://raw.githubusercontent.com/wiki/zaproxy/zaproxy/images/ZAP-Download.png)](https://www.zaproxy.org/download/)

For more details about ZAP see the new ZAP website at [zaproxy.org](https://www.zaproxy.org/)

[![](https://raw.githubusercontent.com/wiki/zaproxy/zaproxy/images/zap-website.png)](https://www.zaproxy.org/)

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/zaproxy/zaproxy). Be sure to check out the original post for more details.

# OWASP ZAP Tutorial: Complete 2024 Guide

May 13, 2024 / By  [Richard Dezso](https://www.stationx.net/author/richard-dezso/ "Richard Dezso")

![OWASP ZAP Tutorial](https://www.stationx.net/wp-content/uploads/2024/03/OWASP-ZAP-Tutorial.png)

[](https://www.linkedin.com/shareArticle?title=OWASP%20ZAP%20Tutorial%3A%20Complete%202024%20Guide&url=https%3A%2F%2Fwww.stationx.net%2Fowasp-zap-tutorial%2F&mini=true)[](https://x.com/intent/post?text=OWASP%20ZAP%20Tutorial%3A%20Complete%202024%20Guide&url=https%3A%2F%2Fwww.stationx.net%2Fowasp-zap-tutorial%2F)[](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.stationx.net%2Fowasp-zap-tutorial%2F)

__Listen to the article

Are you having difficulty finding an OWASP ZAP tutorial that shows you how to use it effectively?

ZAP is an extremely powerful tool for comprehensive testing. It's often used by those who want to thoroughly examine a web application. 

In this tutorial, we’ll guide you through setting it up and show you an overview of its main interface and some of its features. We’ll briefly discuss ZAP vs. Burp Suite and show you how to perform testing with ZAP.

We’ll show you how to use spidering, passive and active scanning, and give you a solid start on using ZAP. As you gain confidence, you’ll be able to discover some of its other tools.    

If you’re ready to learn how to use ZAP, let’s start.

## What Is ZAP?

[Zed Attack Proxy (ZAP)](https://www.zaproxy.org/) is an open-source penetration testing tool formerly known as [OWASP](https://www.stationx.net/owasp-top-10-penetration-testing/) ZAP. It’s a versatile tool often utilized by [penetration testers](https://www.stationx.net/how-to-become-a-penetration-tester/), [bug bounty](https://www.stationx.net/bug-bounty-programs-for-beginners/) hunters, and developers to scan web apps for security risks during the web app testing process.

ZAP offers many features, such as active and passive scanning and API testing capabilities. 

At its core, it’s a manipulator-in-the-middle proxy. It allows you to see all of the requests you make to a web app and all the responses you receive from it, enabling you to identify vulnerabilities and potential attack vectors in real time. 

By intercepting and modifying the traffic between your browser and the web application, ZAP helps you understand how the application behaves under different scenarios and conditions.

[![ZAP Proxy](https://www.stationx.net/wp-content/uploads/2024/03/1.-ZAP-Proxy.png)](https://www.stationx.net/wp-content/uploads/2024/03/1.-ZAP-Proxy.png)

ZAP can be installed on [Windows](https://www.stationx.net/windows-command-line-cheat-sheet/), [Linux](https://www.stationx.net/linux-security-tools/), and macOS. Docker images are also available. We’ll show you how to install it on Kali Linux. 

### ZAP Open-Source Project

ZAP recently joined the [Software Security Project (SSP)](https://softwaresecurityproject.org/) as one of its founding projects. Despite being free and open-sourced, ZAP has grown into the world’s most popular web scanner and directly competes with commercial projects.

We spoke with [Simon Bennetts](https://www.zaproxy.org/docs/team/psiinon/), the project's founder, who acknowledged: "We're competing with commercial companies with hundreds of full-time staff… So it's hard."

ZAP is a non-profit company run full-time by Bennetts and supported by a small team of hardworking volunteers.

Recognizing this challenge, Bennetts stated: "We're always looking for people to contribute—ZAP is a community project." This call for community participation speaks volumes about ZAP's collaborative approach. See [ZAP’s contributing guide](https://www.zaproxy.org/docs/contribute/) for ways to get involved. 

The project relies on sponsors to raise money, and the [Crash Override Open Source Fellowship](https://crashoverride.com/open-source) supports its development; ZAP will, however, remain independent. 

ZAP encourages users to join the Software Security Project (SSP) to help fund ZAP and other important open-source security projects.

ZAP by the numbers.

|   |   |
|---|---|
|**==<br><br>Headline Statistics for February 2024<br><br>==**|   |
|Number of Times ZAP was Started|4,708,566|
|Number of Active Scans|922,722|
|Number of Alerts Raised|1,123,926,095|
|Number of Active Scan Messages Sent|3,274,968,334|

## ZAP vs. Burp Suite

ZAP and [Burp Suite](https://www.stationx.net/how-to-use-burp-suite/) are similar web application security testing tools. However, ZAP is faster and lighter than Burp Suite, and it’s open-source and free. 

Burp Suite's free community edition can be restrictive in its functionality. It has a paid version with more advanced features, but many of these tools are already included in ZAP. 

For example, Burp Suite’s automated scan feature is only available in its pro tier, whereas ZAP has this same functionality called “ATTACK Mode.”

Burp Suite has an intruder tool, although it’s limited to single-threading. ZAP has an equivalent called “Fuzzer.”

ZAP also has features not found in Burp Suite, such as an automation framework that allows you to control ZAP via one YAML file and a heads-up display (HUD). With the HUD, you can use your favorite ZAP features in the browser.

Here’s a feature map that maps Burp features to ZAP equivalents.

|   |   |
|---|---|
|**==<br><br>Burp Suite to ZAP Feature Map<br><br>==**|   |
|**Burp Suite**|**ZAP**|
|Collaborator (_Community_)|OAST Support Add-on|
|Comparer|Diff|
|Decoder|Encoder|
|DOM Invader|Eval Villian Add-on|
|Extender|Marketplace, Scripts|
|Intercept|Breakpoints|
|Intruder (_Throttled_)|Fuzzer|
|Live scan (_Community_)|ATTACK Mode|
|Project Files (_Community_)|Session Files|
|Proxy|Proxy|
|Repeater|Manual Request Editor, Requestor Add-on|
|Scanner (_Community_)|Active Scanner|
|Sequencer|Token Generation and Analysis|
|Target|Contexts|

## Setting Up Your Zed Attack Proxy on Kali Linux

Let’s go through the start-to-finish process of getting ZAP up and running.

### Installing ZAP on Kali Linux

ZAP is not installed in the current version of Kali, which is 2024.1 at the time of this writing. However, it can be easily installed. 

Before installation, always update the repositories to ensure the most up-to-date version is installed by entering `sudo apt update—y`.

[![Installing ZAP on Kali Linux](https://www.stationx.net/wp-content/uploads/2024/03/2.-Installing-ZAP-on-Kali-Linux.png)](https://www.stationx.net/wp-content/uploads/2024/03/2.-Installing-ZAP-on-Kali-Linux.png)

Once finished, you can install ZAP with the command:

`sudo apt install zaproxy`

[![3. Sudo apt install zaproxy](https://www.stationx.net/wp-content/uploads/2024/03/3.-Sudo-apt-install-zaproxy.png)](https://www.stationx.net/wp-content/uploads/2024/03/3.-Sudo-apt-install-zaproxy.png)

**Want to Download Our Premium Hacking Cheat Sheets?**

No Problem! Just enter your email address, and we’ll send you the PDF versions of all our hacking cheat sheets.

**DOWNLOAD →**

### Setting Up Your Proxy

You don't need to set a proxy such as FoxyProxy for your browser like in Burp Suite, as ZAP handles all of this. Bennetts tells us that “it’s best to let ZAP launch them.”

The “Browser Launch” feature is automatically configured to work via ZAP and ignore certificate warnings, making it much easier to get up and running without changing settings. This lets you quickly start testing web apps for vulnerabilities without extra setup or configuration. Simply start ZAP, and you’ll be ready to go.

However, if you want to use any of your browsers with an existing profile, such as other browser add-ons installed, you must manually configure your browser to proxy via ZAP and import and trust the ZAP Root CA Certificate. 

We’ll show you how to set this up on Firefox in Kali. 

The first thing you need to do is download the [FoxyProxy addon](https://addons.mozilla.org/en-CA/firefox/addon/foxyproxy-standard/).

[![4. Firefox Browser ADD ONS](https://www.stationx.net/wp-content/uploads/2024/03/4.-Firefox-Browser-ADD-ONS.png)](https://www.stationx.net/wp-content/uploads/2024/03/4.-Firefox-Browser-ADD-ONS.png)

Next, open FoxyProxy so we can configure it. 

[![5. Open FoxyProxy](https://www.stationx.net/wp-content/uploads/2024/03/5.-Open-FoxyProxy.png)](https://www.stationx.net/wp-content/uploads/2024/03/5.-Open-FoxyProxy.png)

From here, head to the proxies tab and enter the following information. 

**Title**: ZAP

**Type**: HTTP

**Hostname**: 127.0.0.1

**Port**: 8080

Once finished, click “Save.”

[![6. Once finished, click -Save](https://www.stationx.net/wp-content/uploads/2024/03/6.-Once-finished-click-Save.png)](https://www.stationx.net/wp-content/uploads/2024/03/6.-Once-finished-click-Save.png)

Whenever you want to proxy traffic through ZAP, head to the addon and select “ZAP.”

[![7. Proxy traffic through ZAP](https://www.stationx.net/wp-content/uploads/2024/03/7.-Proxy-traffic-through-ZAP.png)](https://www.stationx.net/wp-content/uploads/2024/03/7.-Proxy-traffic-through-ZAP.png)

### Install ZAP Certificate

If you don't use ZAP's built-in browser function, you'll need to manually set up the certificate on your browser. If you try accessing any site running SSL/TLS while using your browser outside of ZAP, you must configure it to use ZAP's CA root certificate to avoid any certificate warnings. 

[![8. Install ZAP Certificate](https://www.stationx.net/wp-content/uploads/2024/03/8.-Install-ZAP-Certificate.png)](https://www.stationx.net/wp-content/uploads/2024/03/8.-Install-ZAP-Certificate.png)

ZAP recommends you launch your browser through the “Quick Start” area, but if you’d rather configure your browser manually, here’s how to install the certificate. We’re installing ours in Firefox. 

First, with ZAP running and your FoxyProxy enabled to use ZAP, head to [http://zap](http://zap/). Once there, select “Download” to download the certificate to your system. 

[![9. Select “Download”](https://www.stationx.net/wp-content/uploads/2024/03/9.-Select-Download.png)](https://www.stationx.net/wp-content/uploads/2024/03/9.-Select-Download.png)

Now, go to your Firefox search bar, type `about:preferences`, and press enter. This will take you to the settings page. Search for “certificates,” and find the option “View Certificates.”

[![10. Go to your Firefox search bar](https://www.stationx.net/wp-content/uploads/2024/03/10.-Go-to-your-Firefox-search-bar.png)](https://www.stationx.net/wp-content/uploads/2024/03/10.-Go-to-your-Firefox-search-bar.png)

The “View Certificates” button lets you see all your trusted CA certificates. You can import a new certificate for ZAP by pressing “Import” and selecting the file we downloaded.

[![11. View Certificates](https://www.stationx.net/wp-content/uploads/2024/03/11.-View-Certificates.png)](https://www.stationx.net/wp-content/uploads/2024/03/11.-View-Certificates.png)

In the popup, select “Trust this CA to identify websites,” then click OK.

[![12. Trust this CA to identify websites](https://www.stationx.net/wp-content/uploads/2024/03/12.-Trust-this-CA-to-identify-websites.png)](https://www.stationx.net/wp-content/uploads/2024/03/12.-Trust-this-CA-to-identify-websites.png)

Any encrypted traffic will work when the ZAP proxy is turned on, allowing us to intercept requests. 

Now that everything is set up, in the following section, we’ll walk you through using some of ZAP’s features. ZAP has many tools, but we won’t be able to go over all of them here. We’ll show you a few so you can get started. 

### Starting ZAP

You can start ZAP in Kali in one of two ways: enter `zaproxy` in the terminal or open it from the applications menu under “Web Application Analysis.”

[![Starting ZAP](https://www.stationx.net/wp-content/uploads/2024/03/13.-Starting-ZAP.png)](https://www.stationx.net/wp-content/uploads/2024/03/13.-Starting-ZAP.png)

When you start ZAP, you’ll see a screen asking, “Do you want to persist this ZAP session?”

Persistence will save everything to an HSQL database that you can access to view its contents or reload back into ZAP to see all of the request history, site information, etc.

We’ll be choosing “No, I do not want to persist this session at this moment in time” 

[![Zap](https://www.stationx.net/wp-content/uploads/2024/03/14.-Zap.png)](https://www.stationx.net/wp-content/uploads/2024/03/14.-Zap.png)

## ZAP Overview

Before we start using ZAP, let’s examine the main interface and show where some of the key features are located. The interface has a lot of information, but remember, ZAP does many things.

[![ZAP Overview](https://www.stationx.net/wp-content/uploads/2024/03/15.-ZAP-Overview.png)](https://www.stationx.net/wp-content/uploads/2024/03/15.-ZAP-Overview.png)

1. **Menu Bar**: Here, you can create and manage sessions, create reports, find tools, get help, and more. 

2. **Toolbar:** Includes buttons that provide shortcuts to the most commonly used features.

3. **Tree Window:** Displays the hierarchical view of the site you are testing and the script tree.

4. **Quickstart/Workspace Window:** This is a quick and easy way to use ZAP, especially if you’re new. It also displays requests, responses, and scripts you can edit.

5. **Information Window, including:**

- History tab: This shows a log of all the HTTP requests and responses sent and received through ZAP.
- Search Tab: This allows you to search through the requests and responses.
- Alerts Tab: Displays security alerts found during the scans.
- Output Tab: Provides detailed output from various scans and processes.

6. **Footer:** Displays ZAP status information.

- Alerts Counter: This displays a summary of the alerts found. It’s color-coded (like red, yellow, etc.) to represent the severity of the alerts found during the scanning process.
- Main Proxy: This is the main proxy configuration that ZAP uses, which is set to "localhost:8080."
- Current Scans: This section displays any currently running scans, with icons indicating their status or progress.

### Update Addons

Before you begin using ZAP, you should always check for and update any addons that need to be updated. This ensures that you have the most up-to-date experience.

Press CTRL + U  or use the toolbar shortcut to check for updates.

[![Press CTRL + U](https://www.stationx.net/wp-content/uploads/2024/03/16.-Press-CTRL-U.png)](https://www.stationx.net/wp-content/uploads/2024/03/16.-Press-CTRL-U.png)

This will open the installed add-ons. Next to each add-on, you can see its version number and a brief description of its function. If a newer version of an add-on is available, you'll see “Update” to the right of the description.

You can select the ones you want to update individually, but the best way is to update everything simultaneously. 

Select any add-on and “Update All” to initiate the update. 

[![Update All](https://www.stationx.net/wp-content/uploads/2024/03/17.-Update-All.png)](https://www.stationx.net/wp-content/uploads/2024/03/17.-Update-All.png)

### ZAP Tips

Before we begin, here are a few tips to remember when using ZAP. 

Right-click everywhere and anywhere to see what options are available to you.

[![ZAP Tips](https://www.stationx.net/wp-content/uploads/2024/03/18.-ZAP-Tips.png)](https://www.stationx.net/wp-content/uploads/2024/03/18.-ZAP-Tips.png)

If you need help, you can use the thorough ZAP user guide found by pressing F1.

[![19. ZAP user guide found by pressing F1](https://www.stationx.net/wp-content/uploads/2024/03/19.-ZAP-user-guide-found-by-pressing-F1.png)](https://www.stationx.net/wp-content/uploads/2024/03/19.-ZAP-user-guide-found-by-pressing-F1.png)

**Want to Download Our Premium Hacking Cheat Sheets?**

No Problem! Just enter your email address, and we’ll send you the PDF versions of all our hacking cheat sheets.

**DOWNLOAD →**

## ZAP Spidering

The first tool we’ll show you is the standard spider in ZAP. This spider requests web pages and analyzes them for links to other pages within the same web application. This recursive process keeps going as long as new links are discovered.

The spider builds out the site tree, showing you all the pages found. 

This spider is quite fast and can be used for standard apps. However, you should still consider using this spider on more modern apps in conjunction with the AJAX spider. 

You can select “Spider” from the “Tools” menu or use the CTRL + ALT + S shortcut to start it.

[![ZAP Spidering](https://www.stationx.net/wp-content/uploads/2024/03/20.-ZAP-Spidering.png)](https://www.stationx.net/wp-content/uploads/2024/03/20.-ZAP-Spidering.png)

In the following window, enter the URL of the web app you are spidering and select “Recurse.” This tells ZAP to crawl all URLs or directories from the starting URL. 

Once you’re ready, select “Start Scan.”

[![Start Scan](https://www.stationx.net/wp-content/uploads/2024/03/21.-Start-Scan.png)](https://www.stationx.net/wp-content/uploads/2024/03/21.-Start-Scan.png)

Once the spidering is finished, you’ll see all the nodes found for the web app. The lower-right corner indicates "Nodes Added: 69," which tells us the number of new items the Spider has found and added to the Sites tree during its crawl.

[![22. Nodes Added 69](https://www.stationx.net/wp-content/uploads/2024/03/22.-Nodes-Added-69.png)](https://www.stationx.net/wp-content/uploads/2024/03/22.-Nodes-Added-69.png)

## ZAP AJAX Spidering 

More modern apps use JavaScript, and the traditional ZAP spider doesn't really understand how to crawl these properly. 

This is where the AJAX spider comes in. This spider launches a browser, clicks on things, and even fills out forms, giving you a more comprehensive web app overview. It tries to imitate a user's behavior while interacting with the application.

This spider is much slower than the standard one but works much better with today's modern apps. 

To open the AJAX spider, use the “Tools” menu or the shortcut CTRL + ALT + X.

Here, you’ll set the URL of the app you want to test and the browser the spider will use. Options include Firefox, Chrome, and Safari. 

You can also set advanced options. When you’re ready, select “Start Scan.”

[![23. ZAP AJAX Spidering](https://www.stationx.net/wp-content/uploads/2024/03/23.-ZAP-AJAX-Spidering.png)](https://www.stationx.net/wp-content/uploads/2024/03/23.-ZAP-AJAX-Spidering.png)

Once the scan is finished, any nodes found will be shown in the site tree area with a red spider next to them. The AJAX spider crawled 1103 URLs compared to the standard spider's 116. 

[![24. AJAX spider crawled 1103 URLs](https://www.stationx.net/wp-content/uploads/2024/03/24.-AJAX-spider-crawled-1103-URLs.png)](https://www.stationx.net/wp-content/uploads/2024/03/24.-AJAX-spider-crawled-1103-URLs.png)

## ZAP Scanning

Before we show you ZAP's scanning features, remember you should only use ZAP’s active scanning to attack an application you have explicit permission to test.

### Passive Scanning

Passive scanning just involves looking at the raw requests and responses. ZAP doesn’t actually do anything; it only looks at the traffic that passes through it. It analyzes this traffic to identify potential vulnerabilities without sending any new requests. 

Passive scanning is safe to use on any web application. 

When you spider a site, ZAP performs a passive scan and reports any alerts in the “Alerts” tab. 

[![25. ZAP Scanning](https://www.stationx.net/wp-content/uploads/2024/03/25.-ZAP-Scanning.png)](https://www.stationx.net/wp-content/uploads/2024/03/25.-ZAP-Scanning.png)

We’ll look at these alerts in more detail in the next section.

### Active Scanning

Active scanning attempts to find other vulnerabilities using known attacks against the selected targets. It can only find certain vulnerabilities, including [XSS](https://www.stationx.net/xss-vs-csrf/), [SQL injection](https://www.stationx.net/sql-injection-testing/), buffer overflows, Log4Shell, and remote file inclusion. 

The Active scanner cannot find logical vulnerabilities, such as broken access control.

You can set policies for your scans, although we won’t discuss that here. These policies allow you to set the threshold for the number of issues raised, and the strength options determine the number of attacks performed per parameter.

As with most tools in ZAP, you can set the options for active scanning. These include the number of hosts scanned concurrently, maximum scan duration, and whether to handle CSRF tokens.

Choose “Automated Scan” from the quick start menu to begin. 

[![26. Active Scanning](https://www.stationx.net/wp-content/uploads/2024/03/26.-Active-Scanning.png)](https://www.stationx.net/wp-content/uploads/2024/03/26.-Active-Scanning.png)

This will open up the automated scan launch screen. Here, you’ll set the URL and which spider and browser you want to use. Once you’re ready, select “Attack” to begin.

[![27. select “Attack” to begin](https://www.stationx.net/wp-content/uploads/2024/03/27.-select-Attack-to-begin.png)](https://www.stationx.net/wp-content/uploads/2024/03/27.-select-Attack-to-begin.png)

Once the scan is finished, you can find all the alerts raised by ZAP in the “Alerts” tab.

[![28. ZAP in the “Alerts” tab](https://www.stationx.net/wp-content/uploads/2024/03/28.-ZAP-in-the-Alerts-tab.png)](https://www.stationx.net/wp-content/uploads/2024/03/28.-ZAP-in-the-Alerts-tab.png)

As you can see from the above screenshot, ZAP found 28 vulnerabilities organized by severity: high (red), medium (orange), low (yellow), and informational (blue).

ZAP shows you the number of vulnerabilities it has found. Let’s look closer at the [SQL injection](https://www.stationx.net/blind-sql-injection/). Select the arrow next to it to see where the issue was found in the application. Then, select the URL to see detailed information about the alert.

[![29. ZAP shows you the number of vulnerabilities](https://www.stationx.net/wp-content/uploads/2024/03/29.-ZAP-shows-you-the-number-of-vulnerabilities.png)](https://www.stationx.net/wp-content/uploads/2024/03/29.-ZAP-shows-you-the-number-of-vulnerabilities.png)

ZAP provides quite a bit of information. On the right panel, you’ll see the URL where the alert was found and its risk and confidence level. You’ll also see a CWE and WASC ID from common software security vulnerability lists. Each vulnerability has its own ID number. 

Next, you’ll see a description of the alert and how ZAP confirmed this alert. It notes the attack method used ("AND 1=1 --"). You’ll need to verify this to see if the vulnerability actually exists.  

It also suggests a potential solution: do not trust client-side input and use server-side validation, such as prepared statements, to mitigate the risk.

## Conclusion

In this ZAP tutorial, we’ve shown you how to get started with this powerful tool. We’ve given you an overview of some of its more popular features and showed you how to get started testing web applications. 

You should be well on your way to exploring more of ZAP's many capabilities. Remember to regularly update ZAP to access the latest features and add-ons. Keep practicing and experimenting with different settings to fully utilize the tool's capabilities.

**Credit:** This information was adapted from an excellent guide on [StationX](https://www.stationx.net/owasp-zap-tutorial/). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Pcby3tAxRNE?si=UMzhLqfhuabHyuxL" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=Pcby3tAxRNE). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/QJ5u_dHwoAk?si=NBs8ssPukfqguhXS" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=QJ5u_dHwoAk). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/tpZ9muBTAHQ?si=RlvZXHfIjSm9F2yW" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=tpZ9muBTAHQ). Be sure to check out the original post for more details.

