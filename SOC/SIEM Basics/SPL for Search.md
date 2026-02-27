
Splunk uses **Search Processing Language**, to make searching more efficient. 


# Search App Overview


Search & Reporting App is the default interface to search and analyse data. It stands up from 4 components:

1. **Search Head:**
	This is where we use SPL queries to look for data
	![[Pasted image 20260203210829.png]]
2. **Time Duration:**
	You can select from what time you want to see events
	![[Pasted image 20260203210926.png]]
3. **Search History:**
	Allows you to view previously ran commands
	![[Pasted image 20260203211300.png]]
4. **Data Summary:**
	Prints out what files/forwarders are added to the indexer
	![[Pasted image 20260203211347.png]]
5. **Field Sidebar:**
	Provides quick results 
	![[Pasted image 20260203211750.png]]

# SPL Overview

## Operators:

Comparison operators:

- `=` equal to 
	`Username=Bozo`
- `!=` not equal
	`Username!=Bozo`
- `<` less than
	`Age < 40`
- `<=` less or equal to
	`Age <= 40`
- `>` grater than
	`Outbound_traffic > 50MB`
- `>=` greater or equal to
	`Outbound_traffic >= 50MB`

Boolean Operators:

- `NOT`
	`field_A NOT value`:
	ignore events where field_A contains the value
- `OR`
	`field_A=value1 OR field_A=value2`:
	return events where at least one operator returns true
- `AND`
	`field_A=value1 AND field_B=value2`:
	returns events where both operators returns true

Wild Card:

- `*`
	returns everyhing
	`status=fail*` returns both failed and failure 


## Filtering:


- `stream`
	allows you to set the protocol to be followed
	`sourcetrype=stream:http`
- `| fields`:
	used to add/remove fields from the results.
	`-` removes the field put before it's name
	`+` adds the field put before it's name
	`| fields + HostName - EventID`
	![[Pasted image 20260203223155.png]]
- `| search`:
	`| search Powershell` shows all events containing the term "Powershell"
- `| dedup`:
	removes duplicated fields (deduplicates) from results
	`| dedup EventID` truncates the output to only show 1 event with the same event ID.
- `| rename`:
	allows you to change the name of a field
	![[Pasted image 20260203223617.png]]
- `| table`:
	allows you to search in a specific table, and you can also specify the fields you want to see

## Structuring Results


- `head`:
	gives you back the first matches with the number you set
	`| head 5` will only give you back 5 matches.
- `tail`:
	gives you back the last matches (also used with a number)
- `sort`:
	sorts the output based on the field you specify
	`| sort Hostname` will give back first only with x Hostnames, only then comes Y etc.
- `reverse`
	reverses the output

## Transforming Commands

- `top`
	returns frequent values for the top 10 events
	`| top limit=7 EventID`
	![[Pasted image 20260203225540.png]]
- `rare`
	the opposite of top: prints the least events. also used with the "limit" flag
	`rare limit=3 EventID` would give back the least done EventIDs
- `highlight`
	highlights the specified fields 
	NOTE: output will be visible when "list" is changed to **RAW**!

STATS Commands:

- `stats avg(fieldName)`
	calculates the average value
- `stats max(fieldName)`
	shows the maximum value for a field
- `stats min(fieldName)`
	will return the minimum value for a field
- `stats sum()`
	will return the sum of fields
- `stats count()`
	returns the number of data occurrences


Chart Commands:

- `chart`
	can be used to transform the data into tables or visualizations (that's why it didn't work before, you have to tell it what to make the visu. from)
	`| chart count by EventID`
	![[Pasted image 20260203230541.png]]
- `timechart`
	returns the time series chart covering the field following the function you set
	`timechart count by Image` sorts images, and puts the firsts (oldest ones) to the top

