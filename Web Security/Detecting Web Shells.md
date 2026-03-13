
# Anatomy of Web Shells

Function abuse (PHP):
- shell_exec()
- exec()
- system()
- passthru()

![[616945d482ef350052080da1-1753924119088.svg]]


![[Pasted image 20260313111102.png]]

# Log-Based Detection


Suspicious behaviors can be:
- parameters, like `cmd=`, `exec=`
- encoded strings 
- user agents, like `curl/x.xx.x` or `wget/x.xx.x` or outdated ones
- malicious/outdated IP addresses
- missing `Referrer` header (can be block for privacy)
- abnormal timestamp (outside of business hours)
- executable files uploaded by a user

## Auditd

A native Linux utility that tracks and records events creating an audit trails

You can create rules so it know exactly what to store

E.g a rule named `web_shell` can be configured to find most of these, and then store them by category.

Could be accessed via:

`$ ausearch -k web_shell 
	`time->Wed Jul 23 06:20:36 2025 // A log matching the web_shell rule 
	`"name = /uploads/webshell.php" 
	`"OGID = www-data```


