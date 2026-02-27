Incidents can be any event or action that has a negative consequence on the security of an organization.

![[Pasted image 20260203234548.png]]


# The Life Cycle

As a SOC analyst, we aim to know the attacker tactics, techniques, and procedures, so we can defend more efficiently!

![[Pasted image 20260203234706.png]]


1. **Preparation**
	It covers the readiness of an organization against an attack. 
	This means documenting requirements, defining policies, using security controls (EDR/SIEM/IDS/IPS), and training the staff.
2. **Detection and Analysis**
	This covers getting alerts from the security controls, and investigating them to find the cause.
3. **Containment, Eradication and Recovery**
	This covers the actions to prevent the incident from spreading, and securing the network. Like isolating the host, or gaining back control over an infected system.
4. **Post-Incident Activity**
	Learn from the mistake so it won't happen again.



# Cyber Kill Chain


1. Recon Phase:
	![[Pasted image 20260204020601.png]]
	Started analyzing the events using the network logs (in suricata) to find the IP address, and how he escalated to the network. found the **40.80.148.42** IP address, and that he used a CVE against our joomla CMS web server. The vuln was discovered via the scanner called _acunetix_

2. Exploit Phase
	
	After looked up the IP address, noticed a brute-force attack
	From further investigation, it's been found out that the attacker has successfully found the admin panel of the CMS, which had an admin user, using a weak password, `batman` xd
	the attacker then logged in from a firefox browser with a different IP (the other was the python's IP). 


room will be continued at [here](https://tryhackme.com/room/splunk201)

