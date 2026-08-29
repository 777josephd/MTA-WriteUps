# Log4j Malware Traffic Analysis
[Link](https://www.malware-traffic-analysis.net/2021/12/20/index.html)  

PCAP FROM WEB SERVER TRAFFIC WITH LOG4J ATTEMPTS & LOTS OF OTHER PROBING/SCANNING

---

Based off of the Conversations dialog, IP 198[.]71[.]247[.]91 appears to be the victim, with a large amount of traffic flooding it from various endpoints.

<img width="1714" height="660" alt="2-Conversations" src="https://github.com/user-attachments/assets/e66e0e6a-49e8-4f69-9b71-9bfebff5e29b" />

Further corroborated by the Endpoints dialog.

<img width="1714" height="652" alt="3-Endpoints" src="https://github.com/user-attachments/assets/81d103f5-aadd-4c9c-9140-d89d89aea0ce" />

Filtering by HTTP, inspection of POST requests and following the HTTP stream reveals a User-Agent with the JNDI API, calling for LDAP with a IP address and Base64 encoding.

<img width="1714" height="366" alt="4-POST-jndi-useragent" src="https://github.com/user-attachments/assets/b6c0af92-12bd-4dae-8518-0d2b63352a88" />

Extracting the Base64 string and plugging it into CyberChef reveals the malicious embedded input. `wget` command fetching a shell script from the server and executing it.

<img width="1714" height="552" alt="5-cyberchef" src="https://github.com/user-attachments/assets/3c2af36a-dee1-4e23-ad9e-4cffea5fced0" />

Plugging the IP into VirusTotal shows 14 hits for malicious activity.  
Comments under the `Community` tab verify the Log4j/Log4jShell/Log4Shell exploit.

<img width="1714" height="748" alt="6-VT" src="https://github.com/user-attachments/assets/9c937fd1-65c4-492f-9db2-707e20b686b5" />
