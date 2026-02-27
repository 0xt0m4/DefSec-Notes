
IDS (Intrusion Detection System) is a security solution that detects activities that are passed through the firewall.


# Types of IDS


**DEPLOYMENT MODES:**

- Host Intrusion Detection System (_HIDS_):
	Installed individually on the hosts, for only detection security threats with the particular host.
	Comfortable for single hosts, inefficient for organizations or large networks. 
- Network Intrusion Detection System (_NIDS_)
	Crucial in detecting activities on the networks, regardless of any hosts. Provides centralized view on detections inside the whole network
![[Pasted image 20260206175228.png]]



**DETECTION MODES:**

- _Signature-Based IDS_:
	Uses each attack's unique pattern (signature) to detect already known threats. 
- _Anomaly-Bases IDS_:
	Speaks for itself. First learns the normal behavior on the network, then detects any unusual behavior
- _Hybrid IDS_:
	Combines the 2 mentioned above. 

# Snort


The most widely used open-source IDS solution, operates with Hybrid IDS.
When downloaded, already came with some default rules, and you can also create your own ones.

**MODES:**

![[Pasted image 20260207005101.png]]


- _Packet sniffer mode_:
	Simple solution to display network packets without performing any analysis. It can be helpful in network monitoring and troubleshooting.
	(e.g The network team encounters a performance error, and they need to see the naked traffic)
- _Packet logging mode_:
	Performs detection on the network traffic in real time, and displays the alerts. It also allows you to log the traffic as a PCAP file.
- _NIDS mode_:
	Primary mode that monitors network traffic, but unlike packet logging, this is the ==Full Hybrid IDS mode==


## Usage of Snort


The `/etc/snort/snort.conf` file allows you to configure the network range. To modify the rules, visit `/etc/snort/rules/local.rules`

- Example to test:
	The rule format looks something like:
	![[Pasted image 20260207002805.png]]
	`alert icmp any any -> $HOME_NET any (msg:"Pinggel Kezdenek Megbaszni; sid:10003; rev:1;)` # The home net variable can be loaded from the `snort.conf` file!
	
	This Detects any ICMP requests, and generates an alert once happened.
