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

