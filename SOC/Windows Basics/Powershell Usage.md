

Powerful tool from MS designed for task automation.
It has a CLI and scripting language built on .NET framework.

_In programming, an **object** represents an item with **properties** (characteristics) and **methods** (actions). For example, a `car` object might have properties like `Color`, `Model`, and `FuelLevel`, and methods like `Drive()`, `HonkHorn()`, and `Refuel()`._

objects are fundamental units that encapsulate data and functionality, making it easier to manage and manipulate information

# Basics


- `Get-Command`:
	lists available cmdlets, functions, aliases and scripts

- `-CommandType`:
	a flag for `Get-Command` allows you to search by type. e.g
	`Get-Command -CommandType "Function"`

- `GetHelp`:
	gives a `man`ual

- `Get-Alias`:
	Prints the aliases set

- `Find-Module`:
	lets you find collection of cmdlets (modules), apt search basically
	`Find-Module -Name "Powershell*"`

- `Install-Module`:
	lets you install modules, apt install basically


# Navigation

- `Get-ChildItem`:
	A braindead solution rather `dir` or `ls`
	can be used with **-Path**

- `Set-Location`:
	`cd` basically, used with the **-Path** flag:
	`Set-Location -Path ".\Documents`

- `New-Item`:
	touch/mkdir, based on what you set as "ItemType":
	`New-Item -Path ".\bozo\newdir" -Itemtype "Directory"`
	`New-Item -Path ".\bozo\newdir\newfile.txt" -ItemType "File"`

- `Remove-Item`:
	removes anything with the -Path flag, whether it's a file or directory
	`Remove-Item -Path ".\bozo\newdir"`

- `Copy-Item`:
	`cp` basically, used with a second -Destination flag:
	`Copy-Item -Path ".\pathOrFile" -Destination ".\Downloads"`

- `Get-Content`:
	`cat` basically, also used with a -Path flag:
	`Get-Content -Path ".\bozo\newdir\newfile.txt"`


# Piping, Filtering & Snorting


- `Sort-Object`:
	sorts the files (Use with `ls |`) by **Length** for example:
	`Get-ChildItem | Sort-Object Length`

- `Where-Object`:
	search tool, can be used with **-Property** and **-eq** flags
	`Get-Childitem | Where-Object -Property "Extension" -eq "txt"`
	`-ne`: not equal !=
	`-gt`: greater than <
	`-ge`: <=
	`-lt`: >
	`-le`: >=

- `Select-Object`:
	can be used as a filter to only print out what we want
	`Get-ChildItem | Select-Object Name,Length` 

- `Select-String`:
	Basically a grep command
	`Select-String -Path .\Documents\file.txt -Pattern "FLAG{*" `


# System & Networking

- `Get-ComputerInfo`:
	gives back basic information

- `Get-LocalUser`:
	lists all local users

- `Get-NetIPConfiguration`:
	like `ip` command but still braindead, and gives back more stuff

- `Get-NetIPAddress`:
	more specifically `ip` command

# System Analysis !

- `Get-Process`:
	Gives back PIDs and their usages

- `Get-Service`:
	Lists available services (stopped/running)

- `Get-NetTCPConnection`:
	**Lists active TCP connections**, including PIDs, ports and IP addresses
	First advantage

- `Get-FileHash`:
	Another useful command to get a file's hash so you can compare it to malware hashes 
	Also used with the `-Path` flag

- `Stream`:
	Lists the ADS attached to a file, working as a flag
	`Get-Item -Path "path" -Stream *`


# Scripting !

- `Invoke-Command`:
	Lets you run commands on remote servers
	`Invoke-Command -FilePath c:\scripts\test.ps1 -ComputerName Server01`
	You can also run a command/sequence of commands using a **ScriptBlock**:
	`Invoke-Command -ComputerName Server01 -ScriptBlock {Get-Service}`

