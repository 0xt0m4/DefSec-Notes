

# What is Logged?

Whenever you start a program, create a file, or just log in to your machine, the event is processed by your OS!

Then the OS can log the event. Every recorded event, is called a _log_,
and proper logging ensures all activities are recorded, ==helping the SOC with==:

- **Incident Response**:Logs can show when and how the attack occured
- **Threat Hunting**:Logs allow you to search for signs of malicious activity
- **Alerting and Triage**: Logs are a building block of alert/detection rules


# Format & Usage

Windows logs are ==stored in== binary format under the `C:\Windows\System32\winevt\Logs` folder, with the extension of `.EVTX`


These logs can be opened with a built-in tool (e.g) called:
**Event Viewer**!
It's binary name is `eventvwr` or you can simply search for it


![[Pasted image 20260305145031.png]]


# User Management

Some common event IDs:

| **Event ID**                   | **Description**                                                | **Malicious Usage**                                                                                                                                                                                        |
| ------------------------------ | -------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **4720** / **4722** / **4738** | A user account was  <br>created / enabled / changed            | Attackers might create a backdoor account or even enable an old one to avoid detection                                                                                                                     |
| **4725** / **4726**            | A user account was  <br>disabled / deleted                     | In some advanced cases, threat actors may disable privileged SOC accounts to slow down their actions                                                                                                       |
| **4723** / **4724**            | A user changed their password /  <br>User's password was reset | Given enough permissions, threat actors might reset the password and then access the required user                                                                                                         |
| **4732** / **4733**            | A user was added to /  <br>removed from a security group       | Attackers often add their backdoor accounts to privileged groups like "[Administrators](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/understand-security-groups#administrators)" |


# Process Monitoring

Even if you know who is breached, you often don't really know.

|**Event Code**|**Purpose**|**Limitations**|
|---|---|---|
|**4688  <br>**(Security Log: Process Creation)|Log an event every time a new process is launched, including its command line and parent process details|Disabled by default, you need to enable it by following the [official documentation](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/component-updates/command-line-process-auditing)|
|**1  <br>**(Sysmon: Process Creation)|Replace 4688 event code and provide more advanced fields like process hash and its signature|Sysmon is an external tool not installed by default. Check out the [Sysmon official page](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon)|


# Sysmon

A de facto standard tool from the Microsoft Sysinternals, used for advanced monitoring in addition to the default system logs. 

If we'd need to enable the basic, 4688 noisy events, and need to look for hundreds of logs, it's more ==efficient to install Sysmon==, to receive more powerful and flexible logs!


Once installed, logs are found in event viewer under ` Applications & Services -> Microsoft -> Windows -> Sysmon -> Operational`




The **most important fields** here are:
- _Process Info_:
	Context of the launched process, like PID, path and command line
- _Parent Info_:
	Context of the parent process, useful to build a process tree || attack chain
- _Binary Info_:
	Process hash, signature and PE metadata (executables on Win)
- _User Context_:
	The user running the process, and the Logon ID!


Files and Network:

| **Event ID**                                        | **Security Log Alternative**                                                          | **Event Purpose**                                                                     |
| --------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| **11 / 13  <br>**(File Create / Registry Value Set) | **4656** for file changes and **4657** for registry changes, both disabled by default | Detect files dropped by malware or its changes to the registry (e.g. for persistence) |
| **3 / 22  <br>**(Network Connection / DNS Query)    | No direct alternative, requires additional firewall and DNS configuration             | Detect traffic from untrusted processes or to known malicious destinations            |


# Powershell

Attackers love to abuse ps, since it can allow many activities, including file downloading, C2 connections and even process injection (above many other capabilities!)


There are 5 methods to monitor PowerShell each with its own pros and cons. 
This room covers:
==PowerShell Hostory file==
	located at `C:\<User>\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadline\ConsoleHost_history.txt`