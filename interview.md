# Background
What’s your background, education, and how long have you been working at Cigital/Synopsys? When did you join GIS?
What types of assessments do you work on in GIS and are you training for any others?
Do you have any certifications or interest in future certifications?
Is this interview for AEH/ MEH or Mobile assessments? 
What is your opinion on using security QA? 
Have you worked on Web Services assessments? 
Why web application testing?
Favorite burp extension
Cool finding you’ve found.

# CORS
Are you familiar with CORS? Can you explain it? 
o	Which is more dangerous: Access-Control-Allow-Origin: * with Allow-Credentials true OR Access-Control-Allow-Origin reflects value of Origin header and Allow-Credentials set to true
## Answer
When JavaScript code attempts to send an XMLHttpRequest to an origin different from the current page, the browser will check whether the target origin allows this interaction according to the configured CORS policy.
Modern browsers add "Origin" headers for cross‐origin requests. The Origin header tells the target application the protocol, domain, and port associated with the JavaScript code that triggered this request.
The target server can then provide instructions to the browser regarding whether or not response data should be made available to the JavaScript code that made the request. If the CORS access control rules from the server are not met, the browser prevents response content from this origin from being available to the calling code. An example of this is when the Access-Control-Allow-Origin response header is not set or doesn't match the value of the Origin request header.
Note: Some requests (e.g., use of custom headers) require the browser to issue a pre-flight request (using the OPTIONS method) to check if the server allows such cross-domain requests before they are even sent.
### Answer2
Fortunately, from a security perspective, the use of the wildcard is restricted in the specification as you cannot combine the wildcard with the cross-origin transfer of credentials (authentication, cookies or client-side certificates). Consequently, a cross-domain server response of the form:

Access-Control-Allow-Origin: *
Access-Control-Allow-Credentials: true

is not permitted as this would be dangerously insecure, exposing any authenticated content on the target site to everyone.

### Scenario:
You have credents of a user, why would you still want to perform CSRF attack? 

CORS can be used to perform attacks in the internal networks.

# HSTS
Explain the HSTS header 
o	How and where is the HSTS header set and used? (and a few more in-depth questions)
Explain to app team why HTST not enforced is bad when they disabled http port
## Answer
When HSTS is enabled, the webserver sends the special HTTP response header called "Strict-Transport-Security" to the client. This header includes the max-age attribute, which specifies a duration of time in seconds. Optionally, the directive 'includeSubdomains' can be included to indicate that this policy should apply to all sub-domains as well. After a browser receives this header over a secure HTTPS connection (without any certificate errors), the browser makes new requests to the application over secure HTTPS connections for the duration of time specified in the header. Any links to the server over insecure HTTP connections are automatically rewritten to HTTPS before the request is made. HSTS prevents a user from ignoring certificate errors, as it prevents the user from connecting to a website with an invalid certificate.

Applications that do not utilize the "HTTP Strict-Transport-Security" policy are more susceptible to man-in-the-middle attacks via SSL stripping, which occurs when an attacker transparently downgrades a victim's communication with the server from HTTPS to HTTP. Once this is accomplished, the attacker gains the ability to view and potentially modify the victim's traffic, exposing sensitive information, and gaining access to unauthorized functionality.


# HTTP request smuggling
HTTP request smuggling attacks
The application is vulnerable to an HTTP Request Smuggling attack since the HTTP request is parsed and interpreted differently by the front-end (web) server and back-end (application) server.

Consider the below request from a client to a front-end server:
```
POST /query HTTP /1.1
Host: example.com 
Content-Type: application/x-www-form-URL encoded 
Content-Length: 13
Transfer-Encoding: chunked

0

ATTACK
```
In this example, if the front-end server parses the HTTP request based on the Content-Length header, it sends all data up to the end of 'ATTACK' as part of this request to the back-end. However, if the back-end server parses the request using the Transfer-Encoding header, it processes the first chunk with message length 0 as part of this request and considers it as the end of a message body. This leaves the 'ATTACK' payload as unprocessed, and the back-end server treats this left-over message as the start of the next request.


# DOS
Define DOS attacks for web applications? How would you identify it without causing considerable damage?
## Answer
The Denial of Service (DoS) attack is focused on making a resource (site, application, server) unavailable for the purpose it was designed.



# Web services
What are the two different types of web services and how do you test each one?
o	What is the difference between SOAP and REST?
Webservice – Dif between SOAP and REST
## Answer
### Soap
* Simple Object access protocol
* Protocol
* XML
* Standardization
* security
* Soap only uses POST requests
Good for financial transaction(Asynchronous processing, Stateful operation)

*[More description needed for SOAP]*

### Rest
* Representational start transter
* Architec style
* XML, JSON,
* High Performance
* Scalability
* Flaxibility
* A Restful service would use the normal HTTP verbs of GET, POST, PUT and DELETE for working with the required components
Great for running multi ops(Limited connection, coding simplicity, caching)

## Question
How would you distinguish between a GET and POST request given that you don’t know the HTTP method used? Can GET requests also have content in the body? 

Can GET requests have a body?
## Answer
Yes, GET request can have content in the body. possible reason for doing so "we can not send very large inputs due to technical limitations of maximum URL length size which I found to be approximately ~2000 characters in general."

A payload within a GET request message has no defined semantics; sending a payload body on a GET request might cause some existing implementations to reject the request.
* A lot of servers cache the responses to GET and HEAD requests. This behavior might cause issues.
* It’s also possible that the Server might just ignore the body of GET request.

Other reasons alarming us to not use GET with Body are as below,
* SoupUI doesn't support but Postman does supports GET with Body parameter.
* .NET Core supports GET with Body parameter.
* .NET framework doesn’t support GET with Body parameter.
* Fiddler supports GET body but with a warning.
* Amazon CloudFront doesn’t support GET with Body parameter.
* Sping-framework doesn’t support GET with the body.
* XMLHttpRequest doesn’t support GET with the body.
* Most Javascript libraries don’t support GET with a body.
* Elastic search support GET with body parameter. (This is the only example, I found in the support.)

Although specification support for GET method with body parameter, it also warms us about the usage and clarifies that it is not useful to do so.

[RFC 7231](https://tools.ietf.org/html/rfc7231#section-4.3.1)

| GET is the primary mechanism of information retrieval and the focus of almost all performance optimizations.

| A payload within a GET request message has no defined semantics; sending a payload body on a GET request might cause some existing implementations to reject the request.

# HEE
Explain dif between hashing, encoding, encryption – security benefits
o	Does encryption help with integrity?
Explain Sha1 Hashing algorithm security risk to non-technical person
## Answer
Encoding: The purpose of encoding is to transform data so that it can be properly (and safely) consumed by a different type of system.

Encryption:The purpose of encryption is to transform data in order to keep it secret from others. The goal is to ensure the data cannot be consumed by anyone other than the intended recipient

Hashing: Hashing serves the purpose of ensuring integrity, i.e. making it so that if something is changed you can know that it’s changed. Technically, hashing takes arbitrary input and produce a fixed-length string that has the following attributes:

* The same input will always produce the same output.
* Multiple disparate inputs should not produce the same output.
* It should not be possible to go from the output to the input.
* Any modification of a given input should result in drastic change to the hash.

Obfuscation: The purpose of obfuscation is to make something harder to understand, usually for the purposes of making it more difficult to attack or to copy.

## SHA1
A hash function such as SHA-1 is used to calculate an alphanumeric string that serves as the cryptographic representation of a file or a piece of data. This is called a digest and can serve as a digital signature. It is supposed to be unique and non-reversible.

If a weakness is found in a hash function that allows for two files to have the same digest, the function is considered cryptographically broken, because digital fingerprints generated with it can be forged and cannot be trusted. Attackers could, for example, create a rogue software update that would be accepted and executed by an update mechanism that validates updates by checking digital signatures.


# Engage
Do you follow any blogs? podcasts?
Describe a cool vulnerability you found 
How do you keep yourself updated on cybersecurity news? Did you hear of any cool/new findings and try it out on your assessments? What is something that you picked up recently from the resources you look at? 
How to keep up with security news and continued training.
## Answer
App: Cyber security news, Medium
Youtube: Hak5, HackerSpliot, HACKADAY, John Hammond, PwnFunction, LiveOverflow, STOK, Bugcrowd, F5 Devcentral, Optional, zSecurity