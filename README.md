# ethical-hacking-nmap-lab
A controlled virtual lab environment demonstrating network reconnaissance, Nmap scanning, and vulnerability assessment methodologies.


🛡️ Local Network Reconnaissance & Vulnerability Assessment Lab
📋 Project Overview
A controlled, isolated virtual lab environment built to practice ethical hacking, network reconnaissance, and vulnerability assessment methodologies. This project demonstrates foundational penetration testing workflows using Kali Linux as the attacker/analyst machine and virtualized target systems (Windows 7 and local test nodes) within a private virtualized subnet.

🛠️ Lab Architecture & Environment
Attacker Machine: Kali Linux (Virtual Machine) — Configured with eth0 interface on a local subnet (192.168.x.x).

Target Machines: Virtualized Windows 7 and test nodes hosted via hypervisors (UTM/VirtualBox).

Core Tools Used:

Nmap: For host discovery, ARP scanning, OS fingerprinting, and service version detection.

Netcat / Curl: For banner grabbing and service probing.

Metasploit Framework: For safe, local validation of discovered vulnerabilities (e.g., MS17-010).

🔍 Key Phases & Methodology
Phase 1: Network Mapping & Host Discovery
Objective: Identify active hosts and map the local network topology from the Kali Linux terminal.

Commands Executed:

Bash
# Check local interface configuration and IP assignment
ifconfig

# Perform a ping sweep across the local subnet to discover live hosts
sudo nmap -sn 192.168.1.0/24
Outcome: Successfully mapped active local IPs, identifying gateway routers, host machines, mobile devices, and target virtual machines sharing the same subnet.

Phase 2: Port Scanning & Service Fingerprinting
Objective: Discover open ports and determine running services on target machines to identify potential attack surfaces.

Commands Executed:

Bash
# Run a comprehensive service version and OS detection scan against a target IP
sudo nmap -A 192.168.1.10

# Target specific port inspections (e.g., SMB ports 139/445, MSRPC port 135)
sudo nmap -sV -p 135,139,445 192.168.1.10
Findings:

Identified active Microsoft Windows core networking services (MSRPC on port 135, NetBIOS/SMB on ports 139 and 445).

Determined target operating system profiles using TCP/IP stack fingerprinting.

Phase 3: Vulnerability Assessment
Objective: Check discovered services for known vulnerabilities using automated script engines.

Commands Executed:

Bash
# Scan target for specific vulnerability signatures (e.g., MS17-010 EternalBlue)
sudo nmap --script smb-vuln-ms17-010 192.168.1.10
Outcome: Confirmed vulnerability status on unpatched legacy lab machines, demonstrating the critical importance of regular system patching and network segmentation.

🚀 Key Takeaways & Skills Demonstrated
Network Enumeration: Proficient in using Nmap flags (-sn, -sV, -A, --script) for deep network reconnaissance.

Protocol Analysis: Understanding how core network protocols (TCP/IP, SMB, MSRPC, DNS) operate and how they appear in security audits.

Lab Safety & Ethics: Practicing ethical hacking strictly within an isolated virtual machine environment with proper authorization.

⚠️ Disclaimer: All activities documented in this project were performed strictly inside an isolated virtual lab environment on machines owned and controlled by the author.
