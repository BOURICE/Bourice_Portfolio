# Bourice_Portfolio
## Professional Statement

Aspiring SOC Analyst with foundational training in Linux, networking, and network security. Passionate about defensive security, monitoring, and threat detection, I am actively building and documenting hands-on lab environments to strengthen my practical skills.
My prior experience in IT systems, SQL data analysis, and structured reporting enhances my ability to analyze patterns, interpret data, and maintain organized documentation, essential qualities in security operations. I am committed to continuous learning and real-world application of cybersecurity principles.
My goal is to specialize in Security Operations (SOC), focusing on monitoring, detection, and incident response.

Here is a collection of hands-on cybersecurity exercises and lab-based projects documenting my practical learning journey.

## 🔐 Projects
🔒1: CUSTOM NETWORK SCANNER

A Python-based network scanner that discovers live hosts, open ports, and running services on a network. More advanced than a simple ping sweep.
## Features

- ✅ Host discovery (alive/dead detection)
- ✅ Fast multi-threaded port scanning
- ✅ Service identification
- ✅ Banner grabbing for service version detection
- ✅ Network range scanning (CIDR notation)
- ✅ Custom port specification
- ✅ Colored terminal output
- ✅ Export results to file
- ✅ No external dependencies (uses Python standard library)

## Installation

### Prerequisites
- Python 3.6 or higher
- Linux/Mac/Windows

### Clone the Repository
```bash
git clone https://github.com/YOUR_USERNAME/network-scanner.git
cd network-scanner
```

### No Installation Required!
This scanner uses only Python's standard library, so no pip install needed.

## Usage

### Basic Usage

**Scan single host (common ports):**
```bash
python3 scanner.py -t 192.168.1.1
```

**Scan network range:**
```bash
python3 scanner.py -t 192.168.1.0/24
```

**Scan specific ports:**
```bash
python3 scanner.py -t 192.168.1.1 -p 80,443,22,3306
```

**Scan port range:**
```bash
python3 scanner.py -t 192.168.1.1 -p 1-1000
```

**Grab service banners:**
```bash
python3 scanner.py -t 192.168.1.1 -b
```

**Save results to file:**
```bash
python3 scanner.py -t 192.168.1.0/24 -o scan_results.txt
```

### Advanced Examples

**Full scan of local network with banner grabbing:**
```bash
python3 scanner.py -t 192.168.1.0/24 -b -o local_network_scan.txt
```

**Quick web server check:**
```bash
python3 scanner.py -t example.com -p 80,443,8080,8443
```

**Comprehensive single host scan:**
```bash
python3 scanner.py -t 192.168.1.10 -p 1-65535 -b
```

## Command-Line Options

| Option | Description |
|--------|-------------|
| `-t, --target` | Target IP or network (required) |
| `-p, --ports` | Ports to scan (comma-separated or range) |
| `-b, --banner` | Attempt to grab service banners |
| `-o, --output` | Save results to file |
| `-h, --help` | Show help message |

## How It Works

### Phase 1: Host Discovery
The scanner attempts to connect to common ports (80, 443, 22) to determine if a host is alive. This is more reliable than ICMP ping in firewalled environments.

### Phase 2: Port Scanning
Uses multi-threaded TCP connect scanning to check if ports are open. Can scan up to 50 ports simultaneously for faster results.

### Phase 3: Service Detection
Identifies common services based on port numbers and optionally attempts banner grabbing to determine service versions.

## Example Output
```
╔═══════════════════════════════════════════════╗
║          CUSTOM NETWORK SCANNER               ║
║          Discover Hosts & Services            ║
╚═══════════════════════════════════════════════╝

[*] Scanning network: 192.168.1.0/24
[*] Total hosts: 254
[*] Ports to scan: 15

[*] Phase 1: Discovering live hosts...
[+] Host 192.168.1.1 is alive
[+] Host 192.168.1.10 is alive

[*] Found 2 live host(s)

[*] Phase 2: Scanning ports on live hosts...

[*] Scanning 192.168.1.1...
  [+] Port 22/tcp - SSH
  [+] Port 80/tcp - HTTP
  [+] Port 443/tcp - HTTPS

============================================================
SCAN SUMMARY
============================================================

Host: 192.168.1.1
────────────────────────────────────────
  Port    22/tcp  SSH
  Port    80/tcp  HTTP
  Port   443/tcp  HTTPS
```

## Screenshots

### Scanning Local Network
![Network Scan](screenshots/network_scan.png)

### Banner Grabbing
![Banner Grab](screenshots/banner_grab.png)

### Scan Results
![Results](screenshots/scan_results.png)

## Security & Legal Notice

⚠️ **IMPORTANT**: Only scan networks you own or have explicit permission to scan.

Unauthorized port scanning may be illegal in your jurisdiction and could be considered:
- Network intrusion
- Violation of computer fraud laws
- Terms of service violations

**This tool is for:**
- ✅ Educational purposes
- ✅ Penetration testing (with authorization)
- ✅ Network administration of your own networks
- ✅ Security research in lab environments

## Limitations

- **Firewall Detection**: Filtered ports may not be detected
- **Speed vs Stealth**: Fast scanning is more detectable
- **Banner Accuracy**: Some services don't provide banners
- **Timeout Issues**: Slow networks may need timeout adjustments

## Future Enhancements

- [ ] OS detection
- [ ] Vulnerability detection
- [ ] UDP scanning
- [ ] Stealth scan techniques (requires root/admin)
- [ ] HTML/PDF report generation
- [ ] Integration with CVE databases
- [ ] GUI interface

## Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## Troubleshooting

**Problem**: Permission denied errors
**Solution**: Some scan types require elevated privileges:
```bash
sudo python3 scanner.py -t 192.168.1.1
```

**Problem**: Scan is too slow
**Solution**: Reduce the number of ports or increase timeout

**Problem**: No hosts found
**Solution**: Try scanning a single known-alive host first to verify functionality

## License

MIT License - See LICENSE file for details

## Author

Your Name - [GitHub](https://github.com/BOURICE) | [LinkedIn]([https://www.linkedin.com/in/bourice-racheal-758340244/)]

## Acknowledgments

- Inspired by Nmap and other network reconnaissance tools
- Built for educational purposes as part of cybersecurity learning path

---

**⭐ If you find this useful, please star the repository!**

**Tools Used:**  
Kali Linux, VirtualBox

**Repository Link:**  
[Linux Fundamentals Lab](#)

### 🌐 2. Networking & Port Scanning Lab

**Objective:**  
Understand network communication and identify open ports & services.

**Skills Practiced:**
- TCP/IP fundamentals
- Port identification
- Basic subnet understanding
- Network scanning with nmap
- Service detection basics

**Tools Used:**  
Kali Linux, nmap

**Repository Link:**  
[Networking Lab Notes](#)

---

### 🔎 3. OSINT & Reconnaissance Exercises

**Objective:**  
Practice ethical open-source intelligence gathering techniques.

**Skills Practiced:**
- Public data research
- Information footprint analysis
- Domain reconnaissance basics
- Documentation of findings

**Tools Used:**  
Various OSINT tools, browser-based research

**Repository Link:**  
[OSINT Practice Repository](#)

---

### 📊 4. SQL Data Analysis Project (Technical Background)

**Objective:**  
Extract and analyze structured data using SQL queries.

**Skills Practiced:**
- Data extraction
- Query structuring
- Analytical reporting
- Data-driven insights

**Tools Used:**  
SQL, CRM data systems

**Repository Link:**  
[SQL Project](#)



