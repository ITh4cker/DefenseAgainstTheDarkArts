# Thursday, January 16th: Course Introduction
* This is my favorite course
* A little exercise:
  - When you hear the term "cyber security", list some topics, issues, or things that come to mind. Free-for-all
* Observations?
  - Cyber Security is very broad and interdisciplinary
  - WARNING about this course: you will feel dumb and lost at times because of the enormous amount of Computer Science content you have not learned (and may not even have time to learn).  From a former student: "At times this class made me feel dumb, I'll admit, but coming out the other side I feel like my eyes have been opened to another layer of the web of technology that surrounds us."
  - PSA: Imposter syndrome
* What this course is NOT
* What this course IS and expectations, outcomes:
  1. Gain the mindset of thinking like an attacker, #whatcouldpossiblygowrong
  2. Gain the mindset to understand how things work and fail
  3. Question and debate everything, ask why
  4. Understand tradeoffs --which is what Security really is
  5. The ultimate goal of this course, to be revisited on the last day of this class
* Changes for spring 2020
  1. No TAs
  2. No Piazza
  3. Eleven modules
  4. Course website now explicit details on workload
* Motivation: https://media.defense.gov/2020/Jan/14/2002234275/-1/-1/0/CSA-WINDOWS-10-CRYPT-LIB-20190114.PDF
* Expectations of the highest order for this class...
* The effect of not studying Security...
  - The Tacoma Bridge Failure https://www.youtube.com/watch?v=XggxeuFDaDU
* The schtick is very different in this course, and this may be arguably the most "different" course you will take in the CS curriculum
* The definition of security in the context of technology, information, computers
* Terminology: Is it Computer Security?  Is it Information Security (infosec)?  Is it Cyber Security?
* Technology requirements for this class: a hypervisor, and Kali Linux
* The basics you all absolutely need to have: experience and comfort with the command line
  - Why? Versatility, productivity, accessibility, scripting
  - Not everything can be accomplished by fancy graphics and GUIs (sometimes constrained to certain features too)
  - Many systems do not use a windows manager or have a graphical desktop interface (e.g., servers)
    - Graphical interface (especially on servers) => more software requirements, more overhead, more bloat, more vulnerabilities
  - Many security tools are command line based
  - Remote execution of commands
  - Lab 1

# Tuesday, January 21st: Networking 101
* The really hard problems in Security
  - Sexual harassment and gender
* Why study networking?
  - Basics
  - The "Trinity of Trouble" by Gary McGraw
    - Complexity
    - Extensibility
    - Connectivity
	- The "Connectivity" issue
  - Where the "cool stuff" happens
  - The cyber attribution problem => https://twitter.com/thegrugq/status/706545282645757952
* The telephone conversation analogy for basic networking stuff
* Take it a step further and going deeper: the OSI model and the seven layers
* Analogy for the OSI model: ordering pizza => https://www.versatek.com/blog/you-wont-believe-what-the-osi-model-and-pizza-have-in-common/

# Thursday, January 23rd: Basic Packet Analysis
* Review question 1: The CIA triad 
* Review question 2: TCP/IP Three-Way Handshake?
* Review question 3: How many layers in OSI model?  What are the layers from high level to low level?
* A _packet_: contains implementations of all the protocol layers; encapsulation model.  A network communication (e.g., visiting a website, watching a movie) is made up of many packets!
  - How does IP header looks like in a packet? Internet Protocol (IP): RFC 791 => http://www.ietf.org/rfc/rfc791.txt
  - How does TCP header looks like in a packet? Transfer Control Protocol (TCP): RFC 793 => http://www.ietf.org/rfc/rfc793.txt
* A _PCAP_: a file of packets captured from a network
* Things that you can do with PCAP files
  - Visualizing the traffic; see which computer is communicating with who
  - Troubleshoot network problems
  - See if there is any malicious traffic or malware
  - Reconstruct files (e.g., images) and conversations
  - Rip out any username:password pairs sent-in-the-clear
* simple.pcap: http://www.cs.tufts.edu/comp/116/simple.pcap
* The next lab

# Tuesday, January 28th: Packet Analysis, Wall of Sheep, and Sniffing
* Last class: we delved into basic packet analysis
  - Reconstructed a conversation in Wireshark via show TCP stream
* Today:
  - Filter packets by IP address in Wireshark
  - Extract username:password pairs sent in plaintext on the network using Ettercap
* Motivations
  - Wall of Sheep
  - An almost ugly spat: https://twitter.com/0xmchow/status/941145910213562369
  - Recent news: Tinder https://www.wired.com/story/tinder-lack-of-encryption-lets-strangers-spy-on-swipes/
* So you may be curious: how did we at the Wall of Sheep capture all those packets?
* tcpdump, Wireshark, ettercap
* Two types of networks:
  1. Unswitched - packets flow through all devices on network but you look at only the packets addressed to you......
    - Welp... http://superuser.com/questions/191191/where-can-i-find-an-unswitched-ethernet-hub
  2. Switched - packets flow through specific devices on network (most networks now)
* Step 0: Be root (or administrator)
* Step 1: promiscuous mode
* Step 2, Option 1: sniffing unswitched network is easy but now very rare.  Don't need to do anything
* Step 2, Option 2: Use a LAN Tap: https://shop.hak5.org/products/throwing-star-lan-tap-pro
  - Instructions: https://www.youtube.com/watch?v=3zUsJm3bwGY
* Address Resolution Protocol
  - IP address to MAC address on a network
  - Recall OSI model and packets
  - `arp -a`
  - ARP cache on machine for 20 minutes
  - No authentication
* Step 2, Option 3: ARP spoofing or ARP poisoning to sniff switched network
  - Video: https://www.youtube.com/watch?v=RTXAUJ2yqCg
* Bettercap
* Video: https://www.youtube.com/watch?v=9uiA6dGuEE0

# Thursday, January 30th: Scanning, Reconnaisance
* Last class: sniffing unswitched and switched networks
* Is sniffing still relevant today?
* Video: Bettercap and ARP spoofing: https://www.cs.tufts.edu/comp/116/videos/bettercaparpspoof.mp4

# Tuesday February 4th: Scanning
* Preventing sniffing:
  1. Use encryption and encrypted network protocols
  2. VPN
  3. Use switched network......?
* Preventing ARP poisoning on switched network:
  - anti-arpspoof: https://www.youngzsoft.net/cc-get-mac-address/anti.htm
  - ArpON: http://arpon.sourceforge.net/
  - Antidote
  - Arpwatch: http://www.linuxandubuntu.com/home/how-to-monitor-ethernet-activity-in-linux-using-arpwatch
* Scanning
  - Why? Network reconnaissance.  Warfare 101
  - Questions for Reconaissance:
    1. Is the target dead or alive? (i.e., is the target up or down?)
    2. What kind of device is this?
    3. What's the purpose of this device? (kind of things is it doing)
    4. Who is the target connecting / talking to?
    5. Does target have any open ports?
    6. Geographically, where is this target located?
    7. What protocols do the target use?
    8. Who owns this target?
    9. Who uses this target?
    10. What permissions do users have on this target?
    11. What software (and versions) is this target running?
  - What devices and computers are up?
  - What ports are open on a computer?
  - What services are running?
  - Where are the computers geographically?
  - Determine possible vulnerabilities
* Is scanning still relevant today?
* Basic method: ping sweep
* Problems with ping?
* Introducing Netcat
* The Network Mapper: nmap
* Think poking holes, "ask questions"
* Poking holes => finding interesting and unwanted stuff on networks
  - https://pen-testing.sans.org/blog/2017/02/28/opening-a-can-of-active-defense-and-cyber-deception-to-confuse-and-frustrate-attackers
* Geographical information: SHODAN

# Thursday, February 6th and Tuesday, February 10th: Distributed Denial of Service (DDoS) Attacks
* "Experts understand the dozens of scan techniques and choose the appropriate one (or combination) for a given task. Inexperienced users and script kiddies, on the other hand, try to solve every problem with the default SYN scan. Since Nmap is free, the only barrier to port scanning mastery is knowledge. That certainly beats the automotive world, where it may take great skill to determine that you need a strut spring compressor, then you still have to pay thousands of dollars for it... By default, Nmap performs a SYN Scan, though it substitutes a connect scan if the user does not have proper privileges to send raw packets (requires root access on Unix). Of the scans listed in this section, unprivileged users can only execute connect and FTP bounce scans." https://nmap.org/book/man-port-scanning-techniques.html
* Defending against scanners
  - No certain way
  - Firewalls?
  - Close services
  - Packet filtering
* What could possibly go wrong?
* Want to be stealthy!
* RFC 793: if ports are closed and you send "junk" to it, RST packet will be sent! (page 65 of https://tools.ietf.org/html/rfc793)
  - FIN scan: `sudo nmap -sF ...`
  - NULL scan: `sudo nmap -sN ...`
  - XMAS scan: `sudo nmap -sX ...`, # FIN, PSH, URG flags in packet
* Decoy:
  - `sudo nmap -D...`
  - spoofed connections
  - Must use real + alive IP address, else SYN flood
* The first "D" (Distributed) in DDoS: attack source is more than one, often thousands of, unique IP addresses
* SYN flood
  - The idea: exhaust states in the TCP/IP stack
  - Recall TCP/IP handshaking
  - Attacker sends SYN packets with a spoofed source address, the victim, (that goes nowhere)
  - Victim sends SYN/ACK packet but attacker stays slient
  - Half-open connections must time out which may take a while
  - Alas, good SYN packets will not be able to go through
  - Reference 1: https://www.cert.org/historical/advisories/CA-1996-21.cfm?
  - Reference 2, RFC 4987: https://tools.ietf.org/html/rfc4987
  - Reference 3: https://www.juniper.net/documentation/en_US/junos12.1x44/topics/concept/denial-of-service-network-syn-flood-attack-understanding.html
* Defending against SYN flood
  - Increase queue
  - Filtering
  - SYN cookies
  - Reduce timer for SYN packets
* Teardrop (old)
  - The idea: "involves sending fragmented packets to a target machine. Since the machine receiving such packets cannot reassemble them due to a bug in TCP/IP fragmentation reassembly, the packets overlap one another, crashing the target network device." https://security.radware.com/ddos-knowledge-center/ddospedia/teardrop-attack/
  - Recall RFC 791 (IP), the IP packet fields in question: Fragment Offset, Flag (namely "Don't fragment" and "More fragments")
  - Result: "Since the machine receiving such packets cannot reassemble them due to a bug in TCP/IP fragmentation reassembly, the packets overlap one another, crashing the target network device."
  - Reference: https://www.juniper.net/techpubs/software/junos-es/junos-es92/junos-es-swconfig-security/understanding-teardrop-attacks.html
* Ping of Death (old)
  - The idea: violate the IP contract
  - In RFC 791, the maximum size of an IP packet is 65,535 bytes --including the packet header, which is typically 20 bytes long.
  - An ICMP echo request is an IP packet with a pseudo header, which is 8 bytes long. Therefore, the maximum allowable size of the data area of an ICMP echo request is 65,507 bytes (65,535 - 20 - 8 = 65,507)
  - Result: "However, many ping implementations allow the user to specify a packet size larger than 65,507 bytes. A grossly oversized ICMP packet can trigger a range of adverse system reactions such as denial of service (DoS), crashing, freezing, and rebooting."
* ICMP Flood Attack => Overload victim with a huge number of ICMP echo requests with spoofed source IP addresses.
* UDP Flood Attack => Same idea of ICMP flood attack but using UDP packets
* Lab 4

# Thursday, February 12th: Encoding
* How to defend against DDoS?
* About that target on the scanning lab
  - Honeypot
  - Even no password can work! https://www.zdnet.com/article/heyyo-dating-app-leaked-users-personal-data-photos-location-data-more/
* This week and next week: cryptography, the foundation of Computer Security
* Encoding vs encryption: they are not the same
  - Encoding: "The purpose of encoding is to transform data so that it can be properly (and safely) consumed by a different type of system. The goal is not to keep information secret, but rather to ensure that it’s able to be properly consumed."
  - Encryption: "to transform data in order to keep it secret from others, e.g. sending someone a secret letter that only they should be able to read, or securely sending a password over the Internet. Rather than focusing on usability, the goal is to ensure the data cannot be consumed by anyone other than the intended recipient(s)."
  - Source: https://danielmiessler.com/study/encoding-encryption-hashing-obfuscation/
* So why did I give you a scanning lab, PCAP lab?  Finer points on target, set3.pcap
* About that peculiar port on the honeypot...
* About set3.pcap on the PCAPs lab:
  - A goal of this class: recognition and mindset
  - Base64: binary-to-text encoding scheme.  That is: binary data to ASCII
  - http://stackoverflow.com/questions/6916805/why-does-a-base64-encoded-string-have-an-sign-at-the-end
  - Why? Dangers in printing payload: https://unix.stackexchange.com/questions/73713/how-safe-is-it-to-cat-an-arbitrary-file
  - Why? Basic authentication on web. Example: https://github.com/LiamRandall/BsidesDC-Training/blob/master/http-auth/http-basic-auth-multiple-failures.pcap
* So far, you have been using tools like Ettercap, Nmap, Wireshark.  Now, you must learn how they work!
* Lab 4

# Tuesday, February 18th: Cryptography
* So now crypto...
* Definitions
* The golden rule: "Never Roll Your Own Crypto"
* Crypto algorithms: symmetric, hash functions, asymmetric
* Tradeoffs to consider:
  - Cost of breaking a cipher
  - Value of the information that is encrypted
  - Time required to break info
  - Lifetime of information?
* The only secure crypto algorithm: One-Time Pad
  - Video: https://www.khanacademy.org/computing/computer-science/cryptography/crypt/v/one-time-pad

# Tuesday, February 25th: Cryptography, Part II
* Final project
* Last class: the golden rules of crypto, symmetric algorithms, asymmetric algorithms, one-way hash functions
* Today: passwords, how HTTPS work
* Storing passwords the wrong way
* Storing passwords the wrong way, redux
* Storing passwords the right way with a salt
* Cracking user accounts on Linux systems:
  - Use /etc/passwd and /etc/shadow files from Linux-based systems
  - $algorithm$salt$hash
  - $1$ = MD5
  - $2$ = Blowfish
  - $5$ = SHA-256
  - $6$ = SHA-512
* Tool: John the Ripper.  Default: simple list then brute force
* Daniel Miessler's SecLists
* The spring 2020 password cracking contest, due March 31st
* Incident:
  - Chegg: https://www.zdnet.com/article/chegg-to-reset-passwords-for-40-million-users-after-april-2018-hack/
  - DoorDash: https://arstechnica.com/information-technology/2019/09/doordash-hack-spills-loads-of-data-for-4-9-million-people/
* Q: How long is your password good for?
* References
  - https://unix.stackexchange.com/questions/81240/manually-generate-password-for-etc-shadow
  - https://www.vidarholen.net/contents/blog/?p=32
  - https://serverfault.com/questions/514382/why-are-md5-passwords-hashed-differently
* So how does Transport Layer Security (TLS) (also commonly known as Secure Socket Layer or SSL work)?
  - First, how HTTP works
  - Diagram: https://d1smxttentwwqu.cloudfront.net/app/uploads/2015/07/SSLTLS_handshake.png
  - More: https://www.cloudflare.com/learning/ssl/what-happens-in-a-tls-handshake/
  - Why? HTTPS is HTTP inside of a TLS session
  - Uses BOTH symmetric and asymmetric crypto
  - Secure communications between two parties over a network
  - On top of TCP
  - Different port numbers used for TLS connection.  Port 443 for HTTPS
  - Part 1: Data between two parties encrypted via symmetric crypto.  Why?
  - Part 2: Identity of communicating parties identified via asymmetric crypto
  - Connection integrity via message integrity check using a message authentication code 
  - Digital certificates - assert the online identities of individuals, computers, and other entities on a network
    - They are issued by certification authorities (CAs) that must validate the identity of the certificate-holder both before the certificate is issued and when the certificate is used.
    - Specification: https://technet.microsoft.com/en-us/library/cc776447(v=ws.10).aspx
* TLS process:
  1. Client connects to TLS-enabled server. Client requesting a secure connection and presents a list of supported cipher suites (ciphers and hash functions).
  2. The server checks what the highest SSL/TLS version is that is supported by them both, picks a ciphersuite from one of the client's options (if it supports one), and optionally picks a compression method.
  3. The server sends back its identification via digital certificate (THIS MAY NOT HAPPEN)
  4. Client confirms validity of certificate --or NOT!
  5. Both the server and the client can now compute the session key (or shared secret) for the symmetric encryption and decryption of the data.  This computation of the session key is known as Diffie-Hellman key exchange.
  6. "The client tells the server that from now on, all communication will be encrypted, and sends an encrypted and authenticated message to the server."
* References:
  - https://security.stackexchange.com/questions/20803/how-does-ssl-tls-work
  - https://stackoverflow.com/questions/788808/how-do-digital-certificates-work-when-used-for-securing-websites-using-ssl
  - http://security.stackexchange.com/questions/45963/diffie-hellman-key-exchange-in-plain-english
  - https://blogs.akamai.com/2016/03/enterprise-security---ssltls-primer-part-1---data-encryption.html
  - https://blogs.akamai.com/2016/03/enterprise-security---ssltls-primer-part-2---public-key-certificates.html

# Thursday, February 27th: Vulnerabilities
* Recall: vocabulary (Course Introduction)
* What is a vulnerability?
* Why talk about this now?
  - The next topics have a lot to do about vulnerabilities; we have seen the word used quite a bit
  - Vocabulary
  - Literature
  - Understand why software development is very difficult
  - Misconceptions
  - The difficulty of disclosure
* Example (October 16, 2018): https://arstechnica.com/information-technology/2018/10/bug-in-libssh-makes-it-amazingly-easy-for-hackers-to-gain-root-access/
  - CVE-2018-10933
* Example: GitHub vulnerability (messagehub)
* Common Vulnerabilities and Exposures (CVE) https://cve.mitre.org/
  - SushiDude a.k.a., Steve Christey Coley
* Common Weakness Enumeration (CWE)
* The differences between CVE and CWE:
  - https://www.veracode.com/blog/2016/08/language-appsec
  - https://danielmiessler.com/blog/difference-cve-cwe/
* Scanning for vulns:
  - Nikto https://github.com/sullo/nikto
  - Nessus
  - OpenVAS
  - w3af
  - Metasploit (Rapid7) https://github.com/rapid7/metasploit-framework
* If you do a scan or a penetration test of a system and no vulnerabilities are reported, is that a good thing?
  - The badness-ometer
* The disclosure problem
* Quiz 1