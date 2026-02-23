# Bourice_Portfolio
## Professional Statement

Aspiring SOC Analyst with foundational training in Linux, networking, and network security. Passionate about defensive security, monitoring, and threat detection, I am Currently building practical skills through labs, CTFs, and security projects.

My prior experience in IT systems, SQL data analysis, and structured reporting enhances my ability to analyze patterns, interpret data, and maintain organized documentation, essential qualities in security operations. I am committed to continuous learning and real-world application of cybersecurity principles.
My goal is to specialize in Security Operations (SOC), focusing on monitoring, detection, and incident response.

Here is a collection of hands-on cybersecurity exercises and lab-based projects documenting my practical learning journey.

## 🔐 Projects
🌐1: [NETWORK SCANNER](https://github.com/BOURICE/network-scanner/commit/6473e6990562616b2dd38ecd234d93c7af4813f5)

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

Bourice Racheal - [GitHub](https://github.com/BOURICE) | [LinkedIn](https://www.linkedin.com/in/bourice-racheal-758340244/)

## Acknowledgments

- Inspired by Nmap and other network reconnaissance tools
- Built for educational purposes as part of cybersecurity learning path

---

**⭐ If you find this useful, please star the repository!**

**Tools Used:**  
Kali Linux, VirtualBox

### 📊 PROJECT 2: LOG ANALYSIS TOOL

A Python tool that parses, analyzes, and visualizes log files to detect suspicious patterns, failed login attempts, and security events.

# Security Log Analyzer

![Python Version](https://img.shields.io/badge/python-3.6%2B-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Platform](https://img.shields.io/badge/platform-Linux%20%7C%20MacOS%20%7C%20Windows-lightgrey)

A Python-based security log analysis tool that parses, analyzes, and visualizes log files to detect suspicious patterns, brute force attempts, and security anomalies.

## 🎯 Features

- ✅ **Multi-Format Support**: Apache, Nginx, SSH, system logs
- ✅ **Brute Force Detection**: Identifies multiple failed login attempts
- ✅ **Anomaly Detection**: Spots unusual patterns and suspicious activities
- ✅ **Timeline Analysis**: Activity distribution over time
- ✅ **IP Reputation**: Tracks top requesters and offenders
- ✅ **Attack Pattern Recognition**: SQL injection, XSS, path traversal
- ✅ **Export Capabilities**: JSON and HTML reports
- ✅ **No Dependencies**: Uses Python standard library only

## 📋 Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [Features in Detail](#features-in-detail)
- [Sample Output](#sample-output)
- [Log Format Support](#log-format-support)
- [Understanding the Analysis](#understanding-the-analysis)
- [Contributing](#contributing)
- [License](#license)

## 🚀 Installation

### Prerequisites
- Python 3.6 or higher
- No external dependencies required!

### Quick Start
```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/log-analysis-tool.git
cd log-analysis-tool

# Make executable (optional)
chmod +x analyzer.py

# Run analyzer
python3 analyzer.py -f sample_logs/apache_access.log
```

### Directory Structure
```
log-analysis-tool/
├── analyzer.py           # Main analysis script
├── requirements.txt      # Dependencies (none for basic use)
├── README.md            # This file
├── sample_logs/         # Sample log files for testing
│   ├── apache_access.log
│   ├── ssh_auth.log
│   ├── firewall.log
│   └── system.log
├── reports/             # Generated reports
├── screenshots/         # Documentation images
└── docs/               # Additional documentation
```

## 💻 Usage

### Basic Analysis

**Analyze Apache/Nginx access log:**
```bash
python3 analyzer.py -f /var/log/apache2/access.log
```

**Analyze SSH authentication log:**
```bash
python3 analyzer.py -f /var/log/auth.log
```

**Analyze with custom threshold:**
```bash
python3 analyzer.py -f access.log -t 10
```
*Detects IPs with 10+ failed attempts*

### Export Reports

**Generate JSON report:**
```bash
python3 analyzer.py -f access.log -j report.json
```

**Generate HTML report:**
```bash
python3 analyzer.py -f access.log -html report.html
```

**Generate both:**
```bash
python3 analyzer.py -f access.log -j report.json -html report.html
```

### Command-Line Options

| Option | Description | Example |
|--------|-------------|---------|
| `-f, --file` | Log file to analyze (required) | `-f access.log` |
| `-j, --json` | Export results to JSON | `-j report.json` |
| `-html` | Export results to HTML | `-html report.html` |
| `-t, --threshold` | Brute force threshold (default: 5) | `-t 10` |
| `-h, --help` | Show help message | `-h` |

## 🔍 Features in Detail

### 1. Brute Force Detection

Identifies IP addresses with multiple failed authentication attempts:
```
[!] ALERT: Potential brute force attacks detected from 2 IP(s):
    45.76.123.45: 9 failed attempts
    203.0.113.50: 4 failed attempts
```

**How it works:**
- Counts failed login attempts per IP
- Compares against threshold (default: 5)
- Flags IPs exceeding threshold

### 2. Anomaly Detection

Detects unusual patterns:

**High Request Volume:**
```
[MEDIUM] high_request_volume: 152 requests from single IP
```

**Suspicious Patterns:**
```
[HIGH] suspicious_patterns: 8 attack signatures detected
```

**Unusual Time Activity:**
```
[LOW] unusual_time_activity: 75 requests between 2-5 AM
```

### 3. Attack Pattern Recognition

Identifies common attack vectors:
- **SQL Injection**: `union select`, `or 1=1`, `' --`
- **XSS**: `<script>`, `javascript:`, `onerror=`
- **Path Traversal**: `../`, `/etc/passwd`, `cmd=`
- **Command Injection**: `eval(`, `exec(`, `system(`

### 4. Statistical Analysis

**Login Statistics:**
- Total successful logins
- Total failed logins
- Success rate calculation

**Top IP Addresses:**
- Most active IPs
- Request counts per IP

**Top Users:**
- Most targeted usernames
- Activity per user

### 5. Timeline Analysis

Tracks activity distribution:
- Hourly activity patterns
- Identifies peak times
- Detects off-hours activity

## 📊 Sample Output

### Console Output
```
╔══════════════════════════════════════════════════╗
║         SECURITY LOG ANALYZER v1.0               ║
║    Parse, Analyze & Detect Security Events       ║
╚══════════════════════════════════════════════════╝

[*] Parsing log file: sample_logs/apache_access.log
[+] Parsed 30 log entries

==================================================================
SECURITY LOG ANALYSIS REPORT
==================================================================

File: sample_logs/apache_access.log
Analysis Time: 2025-01-15 10:30:45
Total Entries: 30

LOGIN STATISTICS
  Successful Logins: 15
  Failed Logins: 8
  Success Rate: 65.2%

TOP 10 IP ADDRESSES
  192.168.1.100   -   10 requests
  45.76.123.45    -    9 requests
  192.168.1.102   -    5 requests
  185.220.101.42  -    3 requests
  203.0.113.10    -    5 requests

SUSPICIOUS ACTIVITIES DETECTED: 8
  1. GET /<script>alert('XSS')</script> HTTP/1.1...
  2. GET /search?q='+union+select+password+from+users-- HTTP/1.1...
  3. GET /api/../../etc/passwd HTTP/1.1...
  4. GET /.git/config HTTP/1.1...
  5. POST /upload.php HTTP/1.1...

[!] ALERT: Potential brute force attacks detected from 2 IP(s):
    45.76.123.45: 9 failed attempts
    203.0.113.10: 5 failed attempts

[*] Analyzing for anomalies...
[!] Found 2 anomalies:
    [MEDIUM] high_request_volume: 10
    [HIGH] suspicious_patterns: 8

==================================================================

[+] JSON report saved to: report.json
[+] HTML report saved to: report.html

[+] Analysis complete!
```

### HTML Report Preview

The HTML report includes:
- Executive summary dashboard
- Visual statistics with colored boxes
- Sortable tables
- Color-coded alerts
- Professional styling

[View Sample HTML Report](screenshots/html_report_sample.png)

### JSON Report Structure
```json
{
  "metadata": {
    "log_file": "sample_logs/apache_access.log",
    "analysis_time": "2025-01-15T10:30:45",
    "total_entries": 30
  },
  "statistics": {
    "successful_logins": 15,
    "failed_logins": 8,
    "suspicious_activities": 8
  },
  "top_ips": {
    "192.168.1.100": 10,
    "45.76.123.45": 9
  },
  "bruteforce_ips": {
    "45.76.123.45": 9,
    "203.0.113.10": 5
  }
}
```

## 📝 Log Format Support

### Supported Formats

#### Apache/Nginx Access Logs
```
192.168.1.100 - - [15/Jan/2025:10:15:23 +0000] "GET /index.html HTTP/1.1" 200 5234
```

#### SSH Authentication Logs
```
Jan 15 10:00:01 server sshd[1234]: Failed password for root from 45.76.123.45
```

#### System Logs
```
2025-01-15 10:00:00 server kernel: Firewall: DROP IN=eth0 SRC=45.76.123.45
```

#### Firewall Logs
```
2025-01-15 10:05:15 DROP INPUT eth0 45.76.123.45:54321 -> 10.0.0.1:22 TCP
```

### Custom Formats

The analyzer uses flexible regex patterns and can parse most standard log formats containing:
- Timestamps
- IP addresses
- Status codes
- User agents
- Request methods

## 🧠 Understanding the Analysis

### Brute Force Threshold

**Default: 5 failed attempts**

Adjust based on your environment:
- **Strict (threshold: 3)**: More false positives, catches all attacks
- **Balanced (threshold: 5)**: Default recommendation
- **Lenient (threshold: 10)**: Fewer alerts, misses subtle attacks
```bash
python3 analyzer.py -f auth.log -t 3  # Strict
```

### Severity Levels

**HIGH**: Immediate attention required
- Suspicious patterns (SQL injection, XSS)
- Active exploitation attempts
- Multiple attack signatures

**MEDIUM**: Should be investigated
- High request volumes from single IP
- Unusual user agents
- Port scanning patterns

**LOW**: Monitor
- Off-hours activity
- Geographic anomalies
- Minor deviations from baseline

### False Positives

**Common scenarios:**
- Legitimate scanners (security tools, monitoring)
- Typos in URLs looking like attacks
- Automated security testing

**Mitigation:**
- Whitelist known scanners
- Review context of alerts
- Correlate with other data sources

## 🎓 Use Cases

### Security Operations Center (SOC)

**Daily log review:**
```bash
python3 analyzer.py -f /var/log/apache2/access.log -html daily_report.html
```

**Incident investigation:**
```bash
python3 analyzer.py -f suspicious_activity.log -j incident_123.json
```

### Penetration Testing

**Post-engagement analysis:**
```bash
python3 analyzer.py -f target_logs.log -t 3
```

**Identify defensive measures:**
- WAF rules triggered
- IDS/IPS blocks
- Rate limiting

### System Administration

**Security auditing:**
```bash
# Weekly security review
python3 analyzer.py -f /var/log/auth.log -html weekly_$(date +%Y%m%d).html
```

**Troubleshooting:**
- Identify authentication issues
- Track user activity
- Diagnose connection problems

## 📸 Screenshots

### Main Analysis Output
![Console Analysis](screenshots/console_analysis.png)

### Brute Force Detection
![Brute Force Alert](screenshots/bruteforce_detection.png)

### HTML Report Dashboard
![HTML Report](screenshots/html_report.png)

### Suspicious Activities
![Suspicious Patterns](screenshots/suspicious_activities.png)

## 🔧 Advanced Usage

### Analyzing Multiple Logs
```bash
# Create a script to analyze all logs
for log in /var/log/*.log; do
    python3 analyzer.py -f "$log" -html "reports/$(basename $log).html"
done
```

### Automated Daily Reports
```bash
# Add to crontab
0 6 * * * /usr/bin/python3 /path/to/analyzer.py -f /var/log/apache2/access.log -html /var/reports/daily_$(date +\%Y\%m\%d).html
```

### Integration with SIEM
```bash
# Export to JSON for SIEM ingestion
python3 analyzer.py -f access.log -j /var/siem/import/log_analysis.json
```

## 🛠️ Troubleshooting

### Common Issues

**Issue**: "Log file not found"
```bash
# Check file path
ls -l /var/log/apache2/access.log

# Check permissions
sudo python3 analyzer.py -f /var/log/auth.log
```

**Issue**: "No entries parsed"
```bash
# Verify log format
head -20 logfile.log

# Try different log file
python3 analyzer.py -f sample_logs/apache_access.log
```

**Issue**: "Permission denied writing report"
```bash
# Create reports directory
mkdir -p reports

# Write to user directory
python3 analyzer.py -f log.log -html ~/reports/report.html
```

### Performance

**Large log files:**
```bash
# Process first 10000 lines
head -10000 large.log | python3 analyzer.py -f -

# Or use tail for recent entries
tail -10000 large.log > recent.log
python3 analyzer.py -f recent.log
```

## 🚧 Limitations

- **Log Rotation**: Doesn't automatically parse rotated logs (.1, .2, etc.)
- **Real-time**: Not a real-time monitoring tool (use for batch analysis)
- **Memory**: Loads entire log into memory (may struggle with multi-GB files)
- **Correlation**: Doesn't correlate across multiple log sources
- **Geolocation**: Doesn't include IP geolocation data

## 🔮 Future Enhancements

- [ ] Real-time log monitoring
- [ ] Machine learning anomaly detection
- [ ] IP geolocation and reputation lookup
- [ ] Multi-log correlation
- [ ] Interactive web dashboard
- [ ] Database storage for historical analysis
- [ ] Email alerting
- [ ] Integration with threat intelligence feeds
- [ ] Custom rule engine
- [ ] Performance optimization for large files

## 📚 Additional Resources

### Learning Resources
- [OWASP Log Analysis](https://owasp.org/www-community/controls/Log_Analysis)
- [SANS Log Management](https://www.sans.org/reading-room/whitepapers/logging/)
- [Log File Analysis Tutorial](https://www.cybrary.it/)

### Related Projects
- **ELK Stack**: Enterprise log management
- **Splunk**: Commercial SIEM platform
- **Graylog**: Open-source log management
- **Security Onion**: Network security monitoring

### Documentation
- [Complete Usage Guide](docs/USAGE.md)
- [Log Format Specifications](docs/LOG_FORMATS.md)
- [API Reference](docs/API.md)
- [Contributing Guidelines](CONTRIBUTING.md)

## 🤝 Contributing

Contributions are welcome! Please:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/awesome-feature`)
3. Commit your changes (`git commit -m 'Add awesome feature'`)
4. Push to the branch (`git push origin feature/awesome-feature`)
5. Open a Pull Request

**Areas for contribution:**
- Additional log format parsers
- Enhanced anomaly detection algorithms
- Performance optimizations
- Documentation improvements
- Test coverage

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👤 Author

Bourice Racheal
- [GitHub](https://github.com/BOURICE)
- [LinkedIn](https://www.linkedin.com/in/bourice-racheal-758340244/)
- [Portfolio](https://github.com/BOURICE/Bourice_Portfolio)

## 🙏 Acknowledgments

- Inspired by professional SIEM solutions
- Built as part of cybersecurity learning journey
- Thanks to the open-source security community

## 📞 Support

- [Github Issues](https://github.com/BOURICE/log-analysis-tool/issues)
- [Github Discussions](https://github.com/BOURICE/log-analysis-tool/discussions)
- [Email](bouriceracheal17@gmail.com)

---

**⭐ If this tool helped you, please consider starring the repository!**

---




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



