# Lab: Snake Oil, The Incident Alarm

## Objectives
* Practice and use Python.
* Learn how to parse and dissect network packets programmatically (using Python and scapy).
* Write a tool to analyze a live stream or a set of network packets for incidents.

## Overview
Being proficient in programming is an essential skill to have as a cyber security practitioner.

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">For me, it&#39;s more than invaluable, it&#39;s essential.</p>&mdash; Jeremiah Grossman (@jeremiahg) <a href="https://twitter.com/jeremiahg/status/875111993463644160">June 14, 2017</a></blockquote>

## Preliminaries: Learning Python
Because Python 2 will be deprecated on January 1, 2020, you must use Python 3 for this lab.

An interactive Python tutorial: https://www.learnpython.org/ (Links to an external site.)

## Part 1: Snake Oil
A not-too-bright criminal rolled-his-own-crypto to encrypt pictures. The criminal's scheme uses Base64 encoding, string reversing, and ROT13.

Download `evidence.txt` https://tuftsdev.github.io/DefenseAgainstTheDarkArts/labs/evidence.txt (331 KB). Write a program using Python named `reconstruct_image.py` to "decrypt" the image. Your program must determine the type of image automatically (e.g., BMP, PNG, JPG, GIF) and save the image to file system with proper image file extension. Assume the input file is named `evidence.txt` and the output image is named `output.IMAGE_TYPE_EXTENSION`. Finally, you can only use built-in Python libraries. That is, no third-party Python packages allowed! Here is a list of all the standard built-in Python libraries: https://docs.python.org/3.7/library/.

WARNINGS: DO NOT read in the `evidence.txt` file via command line argument! No credit if you do that. No credit if you program crashes or if exceptions are not handled properly. When I grade, I will be using a new `evidence.txt` file.

## Part 2: The Incident Alarm
"Scapy is a Python module created by Philippe Biondi that allows extensive packet manipulation. Scapy allows packet forgery, sniffing, PCAP reading/writing, and real-time interaction with network targets. Scapy can be used interactively from a Python prompt or built into scripts and programs" (from the SANS Institute's Scapy Cheat Sheet https://blogs.sans.org/pen-testing/files/2016/04/ScapyCheatSheet_v0.2.pdf).

Scapy and Python 3 are installed on Kali Linux.

We have covered a number of network scanning techniques, and you practiced finding sensitive information in PCAP files in the previous lab. This time, you will apply your knowledge to write a tool that provides notification of incidents via a live stream of network packets or via a set of packets in a PCAP file.

### Part 2: Instructions
Using Python and scapy, write a program named `alarm.py` that provides user the option to analyze a live stream of network packets or a set of PCAPs for incidents. Your tool shall be able to analyze for the following incidents:

* NULL scan
* FIN scan
* Xmas scan
* Usernames and passwords sent in-the-clear via HTTP Basic Authentication or FTP
* Nikto scan
* Someone scanning for Remote Desktop Protocol (RDP)

If an incident is detected, alert must be displayed in the format:

`ALERT #{incident_number}: #{incident} is detected from #{source IP address} (#{protocol or port number}) (#{payload})!`

Example outputs: `ALERT #1: Xmas scan is detected from 192.168.1.3 (TCP)! ALERT #2: Usernames and passwords sent in-the-clear (HTTP) (username:batman, password:brucewayne)`

Your program does not need to support saving the stream of packets to a PCAP file or saving a record of detected incidents.

No credit if you program crashes or if exceptions are not handled properly.

## Part 2: Running and Using the Tool
In Kali Linux and assuming you are root, run: `python3 alarm.py`. By default with no arguments, the tool shall sniff on network interface eth0. The tool must handle three command line arguments:

`-i INTERFACE: Sniff on a specified network interface`
`-r PCAPFILE: Read in a PCAP file`
`-h: Display message on how to use tool`

Example 1: python alarm.py -h shall display something of the like:

`usage: alarm.py [-h] [-i INTERFACE] [-r PCAPFILE]

A network sniffer that identifies basic vulnerabilities

optional arguments: -h, --help show this help message and exit -i INTERFACE Network interface to sniff on -r PCAPFILE A PCAP file to read`

Example 2: `python3 alarm.py -r set2.pcap` will read the packets from `set2.pcap`

Example 3: `python3 alarm.py -i en0` will sniff packets on a wireless interface `en0`

When sniffing on a live interface, the tool must keep running. To quit it, press Control-C

### Part 2: Getting Started
Here is a working `alarm.py`: https://gist.github.com/mchow01/f0f498f29d2b3bd095b8c93172c6ecf7

What has been written for you: the handling and parsing of command line arguments, reading of PCAP file, and sniffing of network. Download and use inside of your Kali VM. You will also need to install pcapy to work in conjunction with `scapy` on Kali Linux as it is not installed. Run `apt-get install python3-pcapy`

If you go web browsing in the virtual machine with the alarm running, you will notice the alarm will go off...

### Part 2: Testing Your Tool
Your tool must be able to detect the usernames and passwords sent in-the-clear in `set1.pcap`, `set2.pcap`, and `set3.pcap` from the Packet Sleuth lab (Lab 2).

### Part 2: References
* Scapy documentation: http://www.secdev.org/projects/scapy/doc/usage.html
* Scapy Cheat Sheet (SANS Institute): https://blogs.sans.org/pen-testing/files/2016/04/ScapyCheatSheet_v0.2.pdf
* Black Hat Python: Infinite Possibilities with the Scapy Module (GitHub): https://bt3gl.github.io/black-hat-python-infinite-possibilities-with-the-scapy-module.html

### The `README` File
This `README` file shall describe the work. This description must:

* Identify what aspects of the work have been correctly implemented and what have not.
* Identify anyone with whom you have collaborated or discussed the assignment.
* Say approximately how many hours you have spent completing the assignment.
* Be written in either text format. No other formats will be accepted.
* List any additional dependencies used for Part 2.
* For this lab, you must also address the following questions:
  - Are the heuristics used in this assignment to determine incidents "even that good"?
  - If you have spare time in the future, what would you add to the program or do differently with regards to detecting incidents?

## Submission
Submit three files: the `README.txt`, `reconstruct_image.py`, `alarm.py`

For students officially enrolled in the course, submit lab on Canvas.

## Assessment
This lab is worth 30 points.

* (2 points) `README.txt`
* (7 points) Part 1: `reconstruct_image.py`
* (21 points) Part 2: Detection of cleartext passwords, FIN scan, XMAS scan, NULL scan, Nikto scan, someone scanning for Remote Desktop Protocol (RDP)