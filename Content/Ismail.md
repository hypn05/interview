## OSI Model (Open Systems Interconnection)

a conceptual framework that describes the functions of a networking

![OSI](OSI.jpg)

Layer 7 - Application
The application layer is used by end-user software such as web browsers and email clients. It provides protocols that allow software to send and receive information and present meaningful data to users.
A few examples of application layer protocols are the Hypertext Transfer Protocol (HTTP), File Transfer Protocol (FTP), Post Office Protocol (POP), Simple Mail Transfer Protocol (SMTP), and Domain Name System (DNS).

Layer 6 - Presentation
The presentation layer prepares data for the application layer. It defines how two devices should encode, encrypt, and compress data so it is received correctly on the other end. The presentation layer takes any data transmitted by the application layer and prepares it for transmission over the session layer.
* SSL, SSH, JPEG

Layer 5 - Session
The session layer creates communication channels, called sessions, between devices. It is responsible for opening sessions, ensuring they remain open and functional while data is being transferred, and closing them when communication ends. The session layer can also set checkpoints during a data transfer—if the session is interrupted, devices can resume data transfer from the last checkpoint.
* API's, Sockets

Layer 4 – Transport
The transport layer takes data transferred in the session layer and breaks it into “segments” on the transmitting end. It is responsible for reassembling the segments on the receiving end, turning it back into data that can be used by the session layer.
* TCP and UPD

Layer 3 - Network
The network layer has two main functions. One is breaking up segments into network packets, and reassembling the packets on the receiving end. The other is routing packets by discovering the best path across a physical network.
* IP, ICMP, IPSec

Layer 2 – Data Link
The data link layer establishes and terminates a connection between two physically-connected nodes on a network. It breaks up packets into frames and sends them from source to destination.
This layer is composed of two parts—Logical Link Control (LLC), which identifies network protocols, performs error checking and synchronizes frames, and Media Access Control (MAC) which uses MAC addresses to connect devices and define permissions to transmit and receive data.
Ethernet, PPP, Switch

Layer 1 - Physical
The physical layer is responsible for the physical cable or wireless connection between network nodes. 

## Netcat
netcat (often abbreviated to nc) is a computer networking utility for reading from and writing to network connections using TCP or UDP

## Nmap
free and open source (license) utility for network discovery and security auditing

SYN SCAN
This is the default scan and is good for most purposes. It is quieter than a TCP Connect scan, that is, it won’t show up on most simple logs. It works by sending a single TCP SYN packet to each possible port. If it gets a SYN ACK packet back, then Nmap knows there is a service running there.

TCP Connect
This works much like the SYN scan, except it completes the full TCP handshake and makes a full connection. This scan is not only noisy but also puts more load on the machines being scanned and the network. However, if stealth or bandwidth is not an issue, a Connect scan is sometimes more accurate than the SYN scan. Also, if you don’t have administrator or root privileges on the Nmap machine, you won’t be able to run anything other than a Connect scan because the specially crafted packets for other scans require low-level OS access.

Ping Sweep
This does a simple ping of all the addresses to see which ones are answering to ICMP. If you don’t really care about what services are running and you just want to know which IP addresses are up, this is a lot faster than a full port scan. However, some machines may be configured not to respond to a ping but still have services running on them, so a ping sweep is not as accurate as a full port scan.

UDP Scan
This scan checks to see if there are any UDP ports listening. Since UDP does not respond with a positive acknowledgment like TCP and only responds to an incoming UDP packet when the port is closed, this type of scan can sometimes show false positives

FIN Scan
This is a stealthy scan, like the SYN scan, but sends a TCP FIN packet instead. Most but not all computers will send a RST packet back if they
get this input

NULL Scan
Another very stealthy scan that sets all the TCP header flags to off or null

XMAS Scan
Similar to the NULL scan except all the flags in the TCP header are set to on.

Bounce Scan
This tricky scan uses a loophole in the FTP protocol to “bounce” the scan packets off an FTP server and onto an internal network that would normally not be accessible. If you have the IP address of an FTP server that is attached to the local LAN, you may be able to breach the firewall and scan internal machines.

Idle Scan
It is a super stealthy method whereby the scan packets are bounced off an external host. You don’t need to have control over the other host

STEP 1
Send unsolicited SYN/ACK to the zombie device to get an RST packet showing the zombie IP ID.	
STEP 2
Send a forged SYN packet posing as zombie, making the target to respond an unsolicited SYN/ACK to the zombie, making it answering a new updated RST.	
STEP 3
Send a new unsolicited SYN/ACK to the zombie in order to receive a RST packet to analyze its new updated IP ID.

## OWASP top 10

## Explain work close to complaince

## Difference between TCP and UDP

TCP is a connection orientated protocol with built in error recovery and re transmission.
You can liken a TCP connection to a telephone connection.
With a telephone connection you first need to setup the connection by dialing the number, and once the calling party answers you have a both way communications channel.
You then proceed to speak and once done you hang up the connection.
With TCP you set up the connection using the 3 way handshake as shown below:

SYN
---------->
SYN_ACK
<----------
ACK
--------->

UDP
UDP is a connectionless protocol.
You can liken UDP to email or the normal post.
With email or a written message you send your message, but have no idea whether or not that message was received.
UDP does not correct or recover errors in the message. Any error detection and recovery is the responsibility of the receiving application.