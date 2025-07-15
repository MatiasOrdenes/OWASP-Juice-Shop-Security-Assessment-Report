# OWASP-Juice-Shop-Security-Assessment-Report
This report documents a basic security assessment performed on the OWASP Juice Shop web application running on a local Docker container. The goal was to practice reconnaissance, vulnerability scanning, and manual exploitation techniques typical for a junior cybersecurity analyst in a remote work environment.

Methodology
Tools used:

Kali Linux (VirtualBox VM)

Docker (Juice Shop container)

Nmap (port scanning and service detection)

Web browser (Firefox)

Target IP: 192.168.100.12

Target service: Juice Shop running on TCP port 3000

Results
1. Reconnaissance with Nmap
Full TCP port scan revealed port 3000/tcp open.

Service detected as HTTP with a response header indicating OWASP Juice Shop.

Nmap version detection showed limited information but confirmed HTTP server presence.

Commands run:

bash
Copiar
Editar
nmap -p- -T4 192.168.100.12
nmap -sV -sC -p 3000 192.168.100.12

2. SQL Injection (SQLi)
A basic SQL injection was performed on the login form to bypass authentication.

Payload used: ' OR 1=1--

This altered the SQL query to always return true, allowing access without valid credentials.

Explanation:

The injected payload closes the original query condition and adds OR 1=1, which is always true, effectively bypassing authentication.

3. Cross-Site Scripting (XSS)
Reflected XSS was demonstrated using the search bar.

Payload used: <img src=x onerror=alert('XSS')>

Resulted in a popup alert confirming JavaScript execution in the browser context.

4. Exploration of Hidden Routes
Common routes such as /secret and /config.json were accessed but showed the main page content, indicating no sensitive data exposed.

Other routes like /robots.txt and /administration were tested 

Conclusions
The OWASP Juice Shop intentionally contains vulnerabilities which were successfully identified and exploited.

The assessment covered reconnaissance, injection, scripting attacks, and information gathering.

These exercises demonstrate fundamental skills expected for a junior cybersecurity analyst role.

For a real environment, it is recommended to implement input sanitization, authentication hardening, and secure configuration management.

