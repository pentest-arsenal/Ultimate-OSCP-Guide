# Windows Privilege Escalation Awesome Scripts

[](https://github.com/peass-ng/PEASS-ng/tree/master/winPEAS#windows-privilege-escalation-awesome-scripts)

[![](https://github.com/peass-ng/PEASS-ng/raw/master/winPEAS/winPEASexe/images/winpeas.png)](https://github.com/peass-ng/PEASS-ng/raw/master/winPEAS/winPEASexe/images/winpeas.png)

Check the **Local Windows Privilege Escalation checklist** from **[book.hacktricks.xyz](https://book.hacktricks.xyz/windows-hardening/checklist-windows-privilege-escalation)**

Check more **information about how to exploit** found misconfigurations in **[book.hacktricks.xyz](https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation)**

## Quick Start

[](https://github.com/peass-ng/PEASS-ng/tree/master/winPEAS#quick-start)

Find the **latest versions of all the scripts and binaries in [the releases page](https://github.com/peass-ng/PEASS-ng/releases/latest)**.

## WinPEAS Flavours

[](https://github.com/peass-ng/PEASS-ng/tree/master/winPEAS#winpeas-flavours)

- [Link to WinPEAS C# .exe project](https://github.com/peass-ng/PEASS-ng/tree/master/winPEAS/winPEASexe) (.Net >= 4.5.2 required)
    - **Please, read the Readme of that folder to learn how to execute winpeas from memory or how make colors work among other tricks**
- [Link to WinPEAS .ps1 project](https://github.com/peass-ng/PEASS-ng/tree/master/winPEAS/winPEASps1)
- [Link to WinPEAS .bat project](https://github.com/peass-ng/PEASS-ng/tree/master/winPEAS/winPEASbat)

## PEASS Style

[](https://github.com/peass-ng/PEASS-ng/tree/master/winPEAS#peass-style)

Are you a PEASS fan? Get now our merch at **[PEASS Shop](https://teespring.com/stores/peass)** and show your love for our favorite peas

## Advisory

[](https://github.com/peass-ng/PEASS-ng/tree/master/winPEAS#advisory)

All the scripts/binaries of the PEAS Suite should be used for authorized penetration testing and/or educational purposes only. Any misuse of this software will not be the responsibility of the author or of any other collaborator. Use it at your own networks and/or with the network owner's permission.

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/peass-ng/PEASS-ng/tree/master/winPEAS). Be sure to check out the original post for more details.

# Windows Privilege Escalation with WinPeas

# Introduction

Welcome to my new article, today i will show you how you can escalate privileges in Windows machines using WinPeas tool, this is amazing tool created by **CarlosPolop.**

And the most important, here you have the **exe** to execute in victim machine.

[https://github.com/carlospolop/PEASS-ng/releases/download/20230101/winPEASx64.exe](https://github.com/carlospolop/PEASS-ng/releases/download/20230101/winPEASx64.exe)

Perfect, let’s read the description of the **creator** from this tool in the Github repository:

“The goal of this project is to search for possible **Privilege Escalation Paths** in Windows environments. It should take only a **few seconds** to execute almost all the checks and **some seconds/minutes during the lasts checks searching for known filenames** that could contain passwords (the time depened on the number of files in your home folder). By default only **some** filenames that could contain credentials are searched, you can use the **searchall** parameter to search all the list (this could will add some minutes). The tool is based on [**SeatBelt**](https://github.com/GhostPack/Seatbelt).”

Perfect, it’s moment to use it.

# POC

First of all you need a victim machine, in my case it’s a 64 bits full patched Windows 10.

In my Linux machine i start HTTP server with Python3 to transfer the executable into Windows 10.

![](https://miro.medium.com/v2/resize:fit:690/1*R381TMUL_2eA32DNwbeTkA.png)

In Windows 10 browser i search for my IP:

![](https://miro.medium.com/v2/resize:fit:582/1*51wBuvECITUdcm6Feqrndg.png)

And i download the file. When i execute the file i see this screen and the **exe** it’s executed.

![](https://miro.medium.com/v2/resize:fit:700/1*77UudmRC-Rdy7yAVJCaSDA.png)

**Sections:**

- Basic System Information:

![](https://miro.medium.com/v2/resize:fit:700/1*nF1MnPUcFs6d-h7MqRb8Jg.png)

- Credentials, system information, Defenses Informations:

![](https://miro.medium.com/v2/resize:fit:700/1*xMM0qF28w6lMYTto1luxzg.png)

- Users information:

![](https://miro.medium.com/v2/resize:fit:700/1*uPjcxTheRe7Czo6aRt62Eg.png)

- Service Privilege Escalation and DLL Hijacking:

![](https://miro.medium.com/v2/resize:fit:588/1*-CUHMbD7gwhNJV0tsjv76A.png)

- Network information:

![](https://miro.medium.com/v2/resize:fit:700/1*XUt74LC20iKsnTiUYZfMZQ.png)

- Passwords founded:

![](https://miro.medium.com/v2/resize:fit:700/1*aLOjpyFtTJarEstGmuzQRQ.png)

This is ones of the most important things, but **Winpeas** implant ALL paths of privilege escalation, its amazing and one of the most used tools to escalate privileges in Windows.

# Conclusions

This is the final for this article, i hope you like it and try to use in CTF’s or other scenarios.

**Credit:** This information was adapted from an excellent guide on [Medium](https://medium.com/@s12deff/windows-privilege-escalation-with-winpeas-94be6fb0f173). Be sure to check out the original post for more details.

# WinPeas for the (Win)dows Privilege Escalation.


![](https://miro.medium.com/v2/resize:fit:700/1*j66X7-7c3XLcS68npvFeHw@2x.jpeg)

Hello All, today we are going to see the tool called ‘**WinPeas**’. Really awesome Script which is developed by **Carlospolop – https://github.com/carlospolop.**

WinPeas comes in 2 types 🧨

- WinPEAS .exe and .bat

Just open terminal and run command ‘git clone’ paste the link above and the tool will be downloaded to your system. From here you can do 2 things either open a webserver in the same directory where this tool is and run the server transfer the ‘Exe’ file to your system or you can use Netcat to transfer the file from linux to windows.

Let’s execute the file and see what all information it can give us about the host.🖥️

![](https://miro.medium.com/v2/resize:fit:700/1*weOD__GtdMTHs-klz3-i4w@2x.jpeg)

![](https://miro.medium.com/v2/resize:fit:700/1*iLmqZX-j8xMzaf58Q_LJbQ@2x.jpeg)

Open the file location in terminal or Powershell from the menu. 📃

![](https://miro.medium.com/v2/resize:fit:700/1*0UoCDUBUSBoVuoUS8YEsag@2x.jpeg)

Now let’s run this file using ‘ .\’ followed by the file name.

![](https://miro.medium.com/v2/resize:fit:495/1*j0SkgR1KOgrwcZ_6tOKQ1Q@2x.jpeg)

Once you run this file it will check all the system configuration and run multiple scripts which will give you a whole lot of juicy information.

> Basic details about system and architecture . ⚠️

![](https://miro.medium.com/v2/resize:fit:700/1*zQkHDls5I6rKC_L98ZfAUg@2x.jpeg)

> Information about local user. 🆗

![](https://miro.medium.com/v2/resize:fit:700/1*NRITIdcmhyc1USa06s3WDg@2x.jpeg)

> Password policies. 🌀

![](https://miro.medium.com/v2/resize:fit:700/1*KPlERA5MIj6P37DlTu0Kgg@2x.jpeg)

> Processes Information. 🛄

![](https://miro.medium.com/v2/resize:fit:700/1*cYEAco_QocfRtxCGefCYHw@2x.jpeg)

> Installed and currently running applications. 🔣

![](https://miro.medium.com/v2/resize:fit:700/1*Gxjw9T5gmP4xTZ0rn0CcGA@2x.jpeg)

> Network Information and shared Drives. 🛅

![](https://miro.medium.com/v2/resize:fit:700/1*KdMgKKAcoMtgctvysnv6sQ@2x.jpeg)

> Credentials from multiple browsers. 👁️‍🗨️

![](https://miro.medium.com/v2/resize:fit:700/1*EI0Eu_5UIY8rjszcGisbrQ@2x.jpeg)

> Wifi password ( All ). 💬

![](https://miro.medium.com/v2/resize:fit:408/1*f_00RUYttJ3g6QDx_gdlIA@2x.jpeg)

> TCP Listening ports. 📢

![](https://miro.medium.com/v2/resize:fit:700/1*sPXCjbCGv_jP3ZbUD6nO3Q@2x.jpeg)

> Firewall rules. 📵

![](https://miro.medium.com/v2/resize:fit:654/1*6FWwCzjasEQr8Pp6CUpIVw@2x.jpeg)

> All Microsoft updates. 🔁

![](https://miro.medium.com/v2/resize:fit:700/1*5D_UdEsjv52VjBQQbTfCyA@2x.jpeg)

> AV information, UAC settings & Power-shell settings. 🆘

![](https://miro.medium.com/v2/resize:fit:700/1*xf0rO9zv_5WKpf7t7Cxrag@2x.jpeg)

You guys can use this script/application in CTF environment where you can get all the reconnaissance you want from the host system which will ultimately help you for the PrivEsc in the system.

I hope this helps you in understanding how we can leverage this script for our advantages. ❤️

Thank you guys for reading till here I hope you all are having a good year till now! **_Update_**- I moved out of my country for my masters in cybersecurity, till now everything is good…but soon I’ll start part time and I’ll try to do as much research as I can and give time to this stuff. If you have any doubts ping me on my [twitter account](https://mobile.twitter.com/rootxaman). 🐥

**Credit:** This information was adapted from an excellent guide on [Medium](https://amanutkhedkar.medium.com/winpeas-for-the-win-dows-privilege-escalation-76471cd96ef6). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/HmUrUDj3PRM?si=BikBBGE2IVQ_WG1f" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=HmUrUDj3PRM). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/zR_o2VAMrAM?si=kL2WZxsvlqGd3e7D" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=zR_o2VAMrAM). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/dSa_mdg3gCg?si=s4clVle6_lVDhQio" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=dSa_mdg3gCg). Be sure to check out the original post for more details.

