
![[Pasted image 20260102132304.png]]

# Overview

- **User Workstations**:
	These are the endpoints, which can enable attackers to move laterally or compromise the ecosystem. And it can be done via a single phishing email, therefore it's essential to make these secure and monitored.
- **File & DB Servers**:
	Attackers can view sensitive data. E.g ransomware operators targets file servers to maximize their impact. 
- **Application Servers**:
	Like Web, Email, VPN etc. that employees rely on daily. They are externally faced, so they are ==high value targets==! It's critical to monitor application logs, firewall alerts and IDS signatures.
- **AD/Authentication Servers**:
	As AD manages users, groups, computers and their rights, its critical to monitor this. For that reason, attackers regularly target this, as it can allow lateral movements, persistence and privilege escalation. And also one single domain admin can bring down the whole enterprise. 
	Indicators can be like multiple failed attempts, unusual IP or at odd hours, or accounts trying to access system they shouldn't.
- **Routers & Switches**:
	Routers connect different networks, and especially linking the enterprise LAN to the internet! Switches connect devices within the same network, ensuring PCs or printers to communicate seamlessly. Therefore if they are compromised, it can allow to intercept or manipulate traffic (MITM), create backdoors by rerouting traffic or open hidden channels to the internet.
- **Firewalls**:
	The primary gateway controlling traffic between trusted internal network, and the untrusted internet.
	These Protects the enterprise from direct exposure to the internet, prevents unauthorized access to internal services, and logs every connection attempt, or indicators of attacks.


# Network Perimeter


The network perimeter is the ==boundary that separates an organization's internal network from the external internet zone.== 
Basically the white/black list for trusted zone (like employees, servers etc.)
![[Pasted image 20260107015743.png]]



Common `components of a network perimeter` include:

- Firewalls
- Routers/Gateways
- DMZ (Demilitarized Zone): a buffer network segment where public-facing servers are placed (web, mail etc.)
- Remote Access Gateways or VPNs



Monitoring the perimeter means **using firewalls, IDS/IPS and access control** to examine and limit exposure and enforce security rules. This includes to:

- Spot early-stage attacks (port scans, brute force)
- Detect misconfigurations
- Identify outbound traffic that may indicate malware or data exfiltration




