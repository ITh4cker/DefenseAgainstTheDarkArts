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
* Preventing sniffing:
  1. Use encryption and encrypted network protocols
  2. VPN
  3. Use switched network......?
* Preventing ARP poisoning on switched network:
  - anti-arpspoof: https://www.youngzsoft.net/cc-get-mac-address/anti.htm
  - ArpON: http://arpon.sourceforge.net/
  - Antidote
  - Arpwatch: http://www.linuxandubuntu.com/home/how-to-monitor-ethernet-activity-in-linux-using-arpwatch