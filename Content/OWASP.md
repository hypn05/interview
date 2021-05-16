# SQLi
Why do we demonstrate exploits for findings like SQL Injection, instead of just reporting the issue to the app team?
Do we exploit SQL injection or just report the finding once we confirm that it is a true positive?
Scenario: What if Burp reports a SQLi finding and the payload contains the collaborator payload. Burp shows that there is at least a DNS look up picked up by the collaborator server. How would you go about triaging and testing this finding?
## Answer
SQL injection is a web security vulnerability that allows an attacker to interfere with the queries that an application makes to its database. It generally allows an attacker to view data that they are not normally able to retrieve. This might include data belonging to other users, or any other data that the application itself is able to access. In many cases, an attacker can modify or delete this data, causing persistent changes to the application's content or behavior.

# Deserialization
Deserialization attacks
Are you familiar with Deserialization attacks? 
o	In general, if you say you’re not familiar with an attack, they’ll ask how you’ll learn about it so that you can apply it on your tests
## Answer
Insecure deserialization is when user-controllable data is deserialized by a website. This potentially enables an attacker to manipulate serialized objects in order to pass harmful data into the application code.

It is even possible to replace a serialized object with an object of an entirely different class. , objects of any class that is available to the website will be deserialized and instantiated, regardless of which class was expected. For this reason, insecure deserialization is sometimes known as an "object injection" vulnerability.

Serialization is the process of converting a data structure or object state in memory into a format fit to be transmitted over a network or stored for later use. This serialized data can later be deserialized, i.e. read and reconstructed, into a memory object. The serialized data contain an object's state (e.g., data), and for some programming languages, it may also contain the actual code associated with the serialized object

Deserialization is the process of restoring this byte stream to a fully functional replica of the original object, in the exact state as when it was serialized
Serialization may be referred to as marshalling (Ruby) or pickling (Python).

# XML
Are you familiar with XXE (XML External Entity) attacks? 
*	How would you test for it? 
*	How would you test for an XXE attack vs a XML Entity Expansion (Billion Laughs) attack?
## Answer
XML External Entity attack occurs when the XML input containing a reference to an external entity is processed by an insecurely configured XML parser. 
XML parsers can provide a feature enabling external entities to be processed at run-time which can enable attackers to retrieve files from the local filesystem.
* Inject tags and observe how the server is handling the input(look for XML errors)
Contract payload and send
```
<?xml version="1.0"? >
<!DOCTYPE foo [  
   <!ELEMENT foo ANY >
   <!ENTITY xxe SYSTEM "file:///etc/passwd"  >]>
<foo>&xxe;</ foo>
```
Observe the response to look for signs of successful inclusion of the referenced file, such as the following:
* Inject tags and observe how the server is handling the input(look for XML errors)
Contract payload and send
```
<?xml version="1.0"? >
<!DOCTYPE xee  [
<!E LEMENT xee (# PCDATA)>
<!ENT ITY laugh0 "ha" >
<!ENTITY laugh1 "&laugh0;&laugh0;" >
<!ENTITY laugh 2 "&laugh1;&laugh1;" >
<!ENTITY laugh 3 "&laugh2;&laugh2;" >
<!ENTITY laugh 4 "&laugh3;&laugh3;" >
<!ENTITY laugh 5 "&laugh4;&laugh4;" >
<!ENTITY laugh 6 "&laugh5;&laugh5;" >
<!ENTITY laugh 7 "&laugh6;&laugh6;" >
<!ENTITY laugh 8 "&laugh7;&laugh7;" >
<!ENTITY laugh 9 "&laugh8;&laugh8;" >
<!ENTITY laugh "&laugh9;&laugh9;" >
 ]>
<xee>&laugh;</ xee>
```
Observe the response to see there is any delay in the response time or other sign of impact . 

# CSRF
Describe CSRF and its mitigation to a developer and also to a business executive.
To mitigate CSRF, can we put a unique token on each page or put a static token throughout the application? What are the strengths and weaknesses of these approaches?
Should CSRF tokens be generated per session or per transaction? 
Explain CSRF – what are some assumptions
## Answer
A Cross-Site Request Forgery (CSRF) vulnerability occurs when the application fails to ensure that requests received by the server originated from pages served by the application.

For example, an attacker creates a malicious website and convinces an authenticated user to visit the malicious site, such as via phishing. The malicious website can then initiate an HTTP request for a state-changing operation to the vulnerable application with data supplied by the attacker. The HTTP request causes the victim's browser to automatically send the user's session cookie along with the request. The application then processes the request as though the victim had initiated the request from one of the application's pages.

CORS

# XSS
Explain XSS
## Answer
Cross site scripting  is a type of security vulnarability in web applications. XSS attacks enables attackers to inject client-side script into web pages viewed by othe users. It can be used by an attacker to bypass access-control, such as same-origin policy. An attacker might be abl;e to steal session cookies, access tokens, user credentials or msensitive data of a user.

It is classified into two types:

Persistant
* Stored XSS

Non-persistant
* Dom-based XSS
* Reflected XSS


CSP

# Sensitive Data Exposoure
## Answer
Many web applications and APIs do not properly protect sensitive data, such as financial, healthcare, and PII. Attackers may steal or modify such weakly protected data to conduct credit card fraud, identity theft, or other crimes.

* Is any data transmitted in clear text? This concerns protocols such as HTTP, SMTP, and FTP. External internet traffic is especially dangerous. Verify all internal traffic e.g. between load balancers, web servers, or back-end systems.
* Are any old or weak cryptographic algorithms used either by default or in older code?

# Security Misconfiguration
## Solution

Commonly a result of insecure default or incomplete configurations. Verbose error message or misconfigured HTTp Header.


Scenario #1: The application server comes with sample applications that are not removed from the production server. These sample applications have known security flaws attackers use to compromise the server. If one of these applications is the admin console, and default accounts weren’t changed the attacker logs in with default passwords and takes over.
Scenario #2: Directory listing is not disabled on the server. An attacker discovers they can simply list directories. The attacker finds and downloads the compiled Java classes, which they decompile and reverse engineer to view the code. The attacker then finds a serious access control flaw in the application.
Scenario #3: The application server’s configuration allows detailed error messages, e.g. stack traces, to be returned to users. This potentially exposes sensitive information or underlying flaws such as component versions that are known to be vulnerable.
Scenario #4: A cloud service provider has default sharing permissions open to the Internet by other CSP users. This allows sensitive data stored within cloud storage to be accessed.
