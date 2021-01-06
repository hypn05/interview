## Web cache poisoning

Web cache poisoning is an advanced technique whereby an attacker exploits the behavior of a web server and cache so that a harmful HTTP response is served to other users.
Fundamentally, web cache poisoning involves two phases. First, the attacker must work out how to elicit a response from the back-end server that inadvertently contains some kind of dangerous payload. Once successful, they need to make sure that their response is cached and subsequently served to the intended victims.

Any web cache poisoning attack relies on manipulation of unkeyed inputs, such as headers


## HTTP Host header attacks
The HTTP Host header is a mandatory request header as of HTTP/1.1. It specifies the domain name that the client wants to access.

he purpose of the HTTP Host header is to help identify which back-end component the client wants to communicate with. If requests didn't contain Host headers, or if the Host header was malformed in some way, this could lead to issues when routing incoming requests to the intended application.

Historically, this ambiguity didn't exist because each IP address would only host content for a single domain. Nowadays, largely due to the ever-growing trend for cloud-based solutions and outsourcing much of the related architecture, it is common for multiple websites and applications to be accessible at the same IP address.

* Password reset poisoning
* Accessing restricted functionality
* Accessing internal websites with virtual host brute-forcing
* SSRF
