## API security
Access Control
Rate Limiting
Content Validation
Monitoring

TOP 10
API1: Broken Object Level Authorization
API2: Broken Authentication
API3: Excessive Data Exposure
API4: Lack of Resource & Rate Limiting
API5: Broken Function Level Auth
API6: Mass Assignment
API7: Security Misconfiguration
API8: Injection
API9: Improper Asset Management (API version)
API10: Insufficient Logging & Monitoring

## Cred stuffing
Credential stuffing is a cyberattack method in which attackers use lists of compromised user credentials to breach into a system. The attack uses bots for automation and scale and is based on the assumption that many users reuse usernames and passwords across multiple services. 

* Sets up a bot that is able to automatically log into multiple user accounts in parallel, while faking different IP addresses.
* Runs an automated process to check if stolen credentials work on many websites. By running the process in parallel across multiple sites, reducing the need to repeatedly log into a single service.
* Monitors for successful logins and obtains personally identifiable information, credit cards or other valuable data from the compromised accounts.
* Retains account information for future use, for example, phishing attacks or other transactions enabled by the compromised service.

### Credential Stuffing Prevention
Multi-Factor Authentication (MFA)
Use a CAPTCHA
Device Fingerprinting
    The fingerprint is a combination of parameters like operating system, language, browser, time zone, user agent, etc. If the same combination of parameters logged in several times in sequence,
IP Blacklisting
    Attackers will typically have a limited pool of IP addresses, so another effective defense is to block or sandbox IPs that attempt to log into multiple accounts
Rate-Limit Non-Residential Traffic Sources
    It is easy to identify traffic originating from Amazon Web Services or other commercial data centers
Block Headless Browsers


## Rest API

### Rest
* Representational start transter
* Architec style
* XML, JSON,
* High Performance
* Scalability
* Flaxibility
* A Restful service would use the normal HTTP verbs of GET, POST, PUT and DELETE for working with the required components
Great for running multi ops(Limited connection, coding simplicity, caching)

## LFI and RFI
Remote File Inclusion (RFI) is a method that allows an attacker to employ a script to include a remotely hosted file on the webserver.

On the other hand, Local File Inclusion (LFI) is very much similar to RFI. The only difference being that in LFI, in order to carry out the attack instead of including remote files, the attacker has to use local files i.e files on the current server can only be used to execute a malicious script. Since this form of vulnerability can be exploited with only using a web browser, LFI can easily lead to remote code execution by including a file containing attacker-controlled data such as the web server’s access logs.

WAF,
Blacklisting,
Code fixing