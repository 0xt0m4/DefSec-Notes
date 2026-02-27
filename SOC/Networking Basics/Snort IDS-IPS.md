
Snort is a FOSS rule-based NIDS/NIPS.
![[Pasted image 20260207013659.png]]


# IDS & IPS


- Snort **Capabilities**:
	- Live traffic analysis
	- Attack and probe detection
	- Packet logging
	- Protocol analysis
	- Real-time alerting
	- Modules & plugins
	- Pre-processors
	- Cross-platform support! (Linux & Windows)


- Snort **Modes**:
	- **Sniffer Mode**: Read and prompt IP packets in the console application.
	- **Packet Logger Mode**: Log all IP packets (inbound and outbound) that visit the network.
	- **NIDS (Network Intrusion Detection System)  and NIPS (Network Intrusion Prevention System) Modes**: Log/drop the packets deemed malicious according to the user-defined rules.





![[Pasted image 20260207015209.png]]

- **IDS:**
	A ==passive monitoring solution==. It generates alerts for suspicious events.
	The 2 main types are: [_NIDS_](Network_Intrusion_Detection_System) and [_HIDS_](Host_Based_Intrusion_System)

- **IPS**:
	An ==active protecting solution== preventing malicious activities/patterns and policy violations.
	It has 4 main types:
		1. _Network Intrusion Prevention System (NIPS)_: monitors traffic flow on the entire subnet. Once a signature identified, terminated.
		2. _Behavior-based IPS (Network Behavior Analysis - NBA)_: aim is to protect the entire subnet from anomalies been identified. The difference is this requires a training period (==baselining==), to learn the normal traffic. Efficient against unknown threats.
		3. _Wireless Intrusion Prevention System(WIPS)_: monitors traffic flow from a wireless networks. aim to investigate-terminate signature-based threats.
		4. _Host-based Intrusion Prevention (HIPS)_: Works like HIDS, but stops the processes instead of creating events.



**TECHNIQUES:**

- _Signature-Based_:
	Relies on rules to identify known threats.
- _Behaviour-Based_:
	Relies on normal behavior to determine the suspicious activities. Useful to identify unknown threats.
- _Policy-Based_:
	Compares detected activities with system config and security policies. Detects policy violations.


# Interacting with Snort

- `snort -V` drops the output
- `snort -c /etc/snort/snort.conf`
	`-T`: tests the config 
	`-c`: identifies the config file
	`-q`: prevents snort at starting from displaying banner