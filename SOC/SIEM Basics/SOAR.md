
Or ==Security Orchestration, Automation and Response== basically collects all data a SOC would use. EDR, SIEM, IDS/IPS all in one place.

![[Pasted image 20260223164755.png]]


The **Difference** between SOAR and SIEM is:
SOAR is a complete solution, with response and workflow capabilities, while SIEM just shows the normalized logs



# Capalibities:

1. Orchestration:
	Every security solution is coordinated in one place. 
	Not just like sources, but they're all connected to each other
	And it also has a playbook

2. Automation:
	Is the process which reacts to the events collected by the security systems, but automated by the set of playbook
	E.g it automatically checks if the source IP from the brute force has seen before, closes the account if needed, opens a ticket, documents the steps etc.

3. Response:
	If a brute force is detected, the SOAR might blocks the source IP on the firewall, disable the user in the IAM (Identity and Access Management), and open a ticket with all the details.


![[Pasted image 20260223202854.png]]




