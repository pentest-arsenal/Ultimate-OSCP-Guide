
**WELCOME TO THE ULTIMATE OSCP GUIDE**

This guide is designed to be your go-to resource, whether you’re just beginning your journey or you’re in the final stages of preparation. This guide will provide you with in-depth tutorials, command references, and practical advice to help you succeed.

**What You’ll Find Here:**

This guide is divided into comprehensive sections under **TOOLS**. Each section is meticulously crafted to cover the critical tools and techniques you’ll need during the OSCP exam. From the initial stages of gathering information about your target to the final steps of exploiting vulnerabilities and gaining root access, you’ll find step-by-step instructions and command examples that are essential for each tool listed.

**How to Use This Guide:**

1. Start with **Reconnaissance and Enumeration Tools** to gather information.
2. Move to **Active Scanning Tools** to map out open ports and services.
3. **Web Application Scanning Tools** to target web apps.
4. Use **SSL/TLS Assessment Tools** for encrypted services.
5. **Exploitation & Post Exploitation Tools** using the identified vulnerabilities.
6. **Privilege Escalation Tools** to gain full control.


**Reconnaissance and Enumeration Tools**

- **Purpose**: Reconnaissance and enumeration help you gather the detailed information required to effectively plan your attacks. This can include discovering hidden directories, subdomains, or user accounts.
- **Tools**: Tools like **Gobuster**, **Enum4linux**, and **Wfuzz** help gather this critical information.

**Active Scanning Tools**

- **Purpose**: To actively probe the target environment to discover open ports, services, and potential points of entry. This step is crucial for mapping out the attack surface.
- **Tools**: Tools like **Nmap**, **Rustscan**, and **Unicornscan** will help you identify live hosts and the services they are running.

**Web Application Scanning Tools**

- **Purpose**: Targeting web applications requires specialized tools to discover vulnerabilities like SQL injection, XSS, and CSRF. This section is dedicated to those tools.
- **Tools**: **Nikto**, **OWASP ZAP**, and **W3af** will be your main tools for assessing web applications.

**SSL/TLS Assessment Tools**

- **Purpose**: Focused on identifying vulnerabilities in SSL/TLS configurations, this section helps you target encrypted communications and find weaknesses in secure protocols.
- **Tools**: **SSLyze** and **TestSSL.sh** are effective tools for this purpose.

**Exploitation & Post Exploitation Tools**

- **Purpose**: Once you’ve identified vulnerable services or software, you can use this section to exploit those vulnerabilities and gain access to the target. Post-exploitation tools help maintain that access and further explore the compromised system.
- **Tools**: Tools such as **CrackMapExec**, **Evil-WinRM**, and **Mimikatz** are vital here.

**Privilege Escalation Tools**

- **Purpose**: After gaining initial access, you’ll need to escalate privileges to fully control the target. This section provides tools and methods for both Windows and Linux systems.
- **Tools**: **BeRoot**, **LinPEAS**, and **WinPEAS** will be your go-to tools for this stage.

**Documenting Your Findings:**

Capturing screenshots of your scan results and organizing them by port number or service type within the corresponding TCP/UDP sections is essential. This practice provides a visual overview of the network layout and helps you pinpoint potential weak spots or next steps in your attack plan.

Screenshots are also crucial during the OSCP reporting phase. Proper documentation and organization of your findings are key to crafting a thorough and effective report. This template, designed to track up to 10 IP addresses, helps keep your screenshots and notes organized for each new IP you discover.

For those looking to use my entire structure as a working template for their OSCP exam, you can simply fork this repository. You can fully integrate this structure into your own Obsidian setup and add on to it to make it even better.

**Special Notes:**

- **N.B.** = "Nota Bene" is a Latin phrase that translates to "note well" in English. You will encounter it numerous times throughout the guide and usually directs you to noteworthy information or deserves special attention. 

- **Credit:** This section gives credit to the original author and provides a direct link to the source.

---
