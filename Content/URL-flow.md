URL:

Protocal://domainname:port

1. DNS lookup to find IP address
    a. After hitting the URL, the browser cache is checked. 
    b. The second place where DNS query runs in OS cache
    c. The query is sent to ISP where DNS query runs in ISP cache.
    d. then request sends to top or root server of the DNS hierarchy-> TLD server -> Authoritative Name server
2. TCP connection initiates with the server by Browser
    a. A client computer sends a SYN message to check whether second computer is open for new connection or not.
    b. Then another computer, if open for new connection, it sends acknowledge message with SYN-ACK message as well.
    c. After this, first computer receives its message and acknowledge by sending an ACK message.
3. Finally, the connection is built between client and server. Now, they both can communicate with each other and share information.