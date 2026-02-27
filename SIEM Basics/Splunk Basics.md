
# Components

![[Pasted image 20260203131849.png]]


- **Forwarder:**
	A lightweight agent installed on the endpoint intended to be monitored. This includes data sources like:
	Web server, Windows event logs and Sysmon, linux host-centric data, or DB connection statuses 
	Forwarder forwards these data to the _splunk indexer_
- **Indexer:**
	Plays the main role in _processing the data received from forwarders_. This normalizes the data, categorizes and stores the results as events.
- **Search Head:**
	Allows you to _search in the stored events_. The searching done by Search Processing Language (`SPL`), allowing operators like `OR`, `&&` etc.



