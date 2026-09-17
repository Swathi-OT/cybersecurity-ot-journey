# Day 1 — Metasploit Framework Basics
**Date:** 17 September 2026
**Tool:** Metasploit Framework v6.4.116-dev
**Environment:** Kali Linux — VirtualBox VM

---

## What is Metasploit
Metasploit Framework is an open-source penetration testing 
tool developed by Rapid7. It contains thousands of exploits, 
auxiliary modules, and payloads used by security professionals 
to test and identify vulnerabilities in systems.

---

## Metasploit Statistics (v6.4.116-dev)
- 2,623 exploits
- 1,326 auxiliary modules
- 1,710 payloads
- 432 post modules
- 49 encoders
- 14 nops
- 10 evasion modules

---

## Commands Practiced Today

### 1. Launch Metasploit Console
```bash
msfconsole
```
Opens the interactive Metasploit console with the msf prompt.

### 2. Navigate Metasploit File Structure
```bash
cd /usr/share/metasploit-framework
ls
```
Explored folders: app, config, data, docs, modules, plugins, 
scripts, tools, msfconsole, msfvenom

### 3. Explore Wordlists
```bash
cd data/wordlists
ls
```
Found password lists including: rockyou passwords, 
default credentials for SCADA systems, FTP, SSH, 
database services.

Notable files discovered:
- scada_default_userpass.txt — default SCADA credentials
- postgres_default_userpass.txt
- ssh_default_pass.txt
- vnc_passwords.txt

### 4. Explore Exploit Modules
```bash
cd /usr/share/metasploit-framework/modules/exploits
ls
```
Found exploits for: Windows, Linux, Android, Apple iOS, 
BSD, Firefox, Multi-platform, Unix, OpenBSD, Solaris

### 5. Read an Actual Exploit — FTPGetter Buffer Overflow
```bash
cat ftpgetter_pwd_reply.rb
```
Read the source code of CVE-2019-9760:
- FTPGetter Standard v3.55.0.05 Stack Buffer Overflow
- Exploits buffer overflow in PWD command response
- Leads to arbitrary code execution
- Platform: Windows XP SP3
- Written in Ruby

### 6. Explore SCADA and MQTT Scanners
```bash
cd modules/auxiliary/scanner
ls
```
Found scanners for: mqtt, scada, portscanner, 
ftp, ssh, http, dns, smb, snmp and many more.

**Key finding for OT Security:**
Metasploit has dedicated MQTT and SCADA scanners — 
directly relevant to ICS/OT security assessments.

### 7. Run an Actual Port Scan Using Metasploit
```bash
use auxiliary/scanner/portscan/tcp
show options
set RHOSTS 192.168.56.101
set PORTS 1-100
run
```
**Result:** Successfully scanned target host — 
Scanned 1 of 1 hosts (100% complete)

---

## Key Learnings

### Metasploit Module Structure
| Module Type | Purpose |
|-------------|---------|
| Auxiliary | Scanners, fuzzers, sniffers — no exploit |
| Exploits | Vulnerability exploitation modules |
| Payloads | Code executed after successful exploit |
| Encoders | Obfuscate payloads to avoid detection |
| Post | Post-exploitation modules |
| Evasion | Bypass antivirus and IDS |

### Exploit File Structure (Ruby)
Every Metasploit exploit contains:
- Name — exploit name
- Description — what vulnerability it targets
- Author — who found and wrote it
- CVE reference — official vulnerability ID
- Platform — target operating system
- Payload — code executed on target
- Targets — specific versions affected

### OT Security Relevance
Metasploit contains:
- SCADA default credential wordlists
- MQTT protocol scanners
- Industrial control system auxiliary modules
- pfSense vulnerability scanners
- SNMP scanners (used in OT network monitoring)

This shows why OT networks must be properly segmented 
from IT networks — the same tools attackers use against 
IT systems can target industrial devices.

---

## What I Will Learn Next
- Day 2: Burp Suite web application security testing
- Upcoming: Using Metasploit scanner modules for MQTT 
  and SCADA in my OT lab project

---

## Evidence
Screenshots available in screenshots/ folder showing:
- msfconsole launch with module statistics
- File structure exploration
- Wordlist discovery including SCADA credentials
- Exploit module source code reading
- Successful TCP port scan execution

---

## Important Note
All practice done in an isolated VirtualBox lab environment.
Metasploit used only for educational purposes and 
authorized testing. Never use these tools against 
systems you do not own or have permission to test.
