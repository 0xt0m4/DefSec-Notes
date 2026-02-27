
Elastic Stack is also called **ELK**, it's a _collection of components_ that are working together to collect data from sources, store them, then search and visualize them in real time.
![[Pasted image 20260205011617.png]]

# How ELK Works?

![[Pasted image 20260205012644.png]]
- **Beats**
	Host-based agents (==forwarder==) to transfer data to Elasticsearch. 
- **Logstash**
	Is the ==data processing engine== that collects data from beats, ports or files, then filters and normalizes them (the indexer of ELK)
	It's config file is divided into 3 parts:
		1. The _INPUT_ part allows the user to define the source 
		2. The _FILTER_ part allows to specify the filter options to normalize the logs
		3. The _Output_ part is where the filtered data is being sent. It can be a listening port, Kibana interface, Elasticsearch database or file
- **Elastic Search**
	A full-text ==search and analytics engine== for JSON formatted documents. 
- **Kibana**
	The web-based data ==visualization tool== that works with Elasticsearch. 

![[Pasted image 20260205012644.png]]


# Discover Tab

![[Pasted image 20260205015821.png]]

This will basically be your dashboard. 

1. **Logs**
	Information about the event
2. **Fields Pane**
	Shows the list of field parsed from logs.
3. **Index Pattern**
	Stores the log types. E.g VPN logs can be one of this type
4. **Search Bar**
5. **Time Filter**
	Can narrow the results based on time duration
6. **Time Interval**
	This chart shows the event counts over time
7. **Top Bar**
	Contains options to save the search, open saved searches etc.
8. **Discover Tab**
	Main workspace in Kibana for exploring, searching and analyzing raw data
9. **Add Filter**
	We can choose from preset filters rather than manually typing entire queries

