
This scenario covers using _Splunk!_


# Benefits of SIEM

- **Centralization:**
	Everything put into one place, no need to look different log at different places
- **Correlation:**
	The ability to link separate events and pieces together
	The process looks somehow like 
	`Alert recieved -> User info -> Host info -> IP address` from 1 place
- **Historical events:**
	Viewing this can help spot patterns or threats started earlier
	E.g if a user logged in from a _sus IP address_, you can check the history if he used that before
- **Normalization:**
	Some logs comes in JSON, XML or plain text. SIEM makes everything readable, and kinda like the same (therefore, it's easier to get used to it!)


# Sources (Types)

- **Host-Based Log Sources:**
	They come from individual devices, like _workstations_(employees laptop) and _servers_(SQL,DNS etc.) 
- **Network-Based Log Sources:**
	Collected data from firewalls, routers and IDS/IPS systems
- **Web-Based Log Sources:**
	Server-, WAF-, CDN-, API Gateway-, and Web Apps Logs.


# **NOTE:**

**ALWAYS check your timezone** before investigations. You might work in UTC-2, but the logs in Splunk are normalized to UTC+2
Which would make a for hours difference, just because of a misconfiguration

# Windows Logs

When it comes to Windows logs, we usually talk about the 2 main sources:

- **Sysmon:**
	A system that's providing a high level of visibility on malicious process executions, network connections, possible process injection, registry changes etc.
- and **WinEventLogs:**
	includes a huge number number of unique log files, over 200 different log channels (beyond Security, System and Application)


**Note**: Do not be afraid of searching for event IDs, and to think systematically
	If you're looking for IP addresses, look after network logs
	Search for network EventCode sysmon, and you'll find the results, for instance.


# Linux Logs

The 2 main Linux log sources are 

- **auth.log:**
	which tracks authentication-related activity. It's crucial to spot failed logins, unauthorized access attempts, or privesc
- and **syslog:**
	which captures general system-level events. You can monitor service restarts, cron jobs, or background processes

Some useful search queries can be:

- To look after cron jobs, connections, bash files or scripts:
```Splunk-query
index=linux sourcetype=syslog ("CRON" OR "cron")  
|  search ("python" OR "perl" OR "ruby" OR ".sh" OR "bash" OR "nc")
```

- To look after privesc:
```Splunk-query
index=linux source="auth.log" *su*  
| sort + _time
```

- To look after Brute force:
```Splunk-query
index=linux source="auth.log" *ubuntu* process=sshd   
| search "Accepted password" OR "Failed password"
```
