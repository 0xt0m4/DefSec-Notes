# Intro

## Component

- `Bootloader`:
	A piece of code that starts the operating system. The most popular is GRUB
- `OS kernel`:
	The main component of the OS. It manages the resources at hardware-level
- `Daemons`:
	 Background services
- `OS shell`:
	A language interpreter (or CLI), between the OS and the user.
- `Graphics Server`:
	Provides a graphical environment as a sub-system server called "X-server"
- `Window Manager`:
	or the GUI itself
- `Utilities`:
	Applications that perform functions for user or another program

## Architecture

- `Hardware`:
	Physical pieces like RAM, CPU or SSD
- `Kernel`:
	The core of OS's, which virtualize and control hardware resources.
- `Shell`:
	A CLI that can enter commands into kernel functions
- `System Utility`:
	Makes available to the user of all OS functionalties


## File System Hierarchy

![[Pasted image 20251206224320.png]]

- `/dev`:
	device files to access hardware devices
- `/opt`:
	Optimal files (like third party tools) can be saved here
- `/sbin`:
	Executables for system administration
- `var`:
	Variable data, such as log files, cron files and many more


# Shell

Visit [https://explainshell.com/](https://explainshell.com/) to learn more.


`env` variable prints out the stored variables.

If looking for a specific value, use the `env` command or `grep`


# Workflows

## Finding Files on System

- **Fd-find** is an easier alternative for `find`, you can use simply `fd <nameToFind> <location>`

- **Which** returns the path of a tool that where it's linked or should be executed
	`which python` --> /usr/bin/python

- **Find** can be filtered to almost anything
	`find / -type f -name *.conf -user root -size +20k -newermt 2020-03-03 -exec ls -al {} \; 2>/dev/null`
	
	`-user`: sets the owner
	`-size`: files larger than 20KiB
	`newermt`: files newer than the specified date
	`-exec` line: uses cyrly brackets and breaks lines
	`2>/dev/null`: a ==STDERR== redirection to null, which eliminates errors


- **Locate** is a quicker alternative to the find command. It works with a local database
	`sudo updatedb` - updates it's database information
	But in contrast, doesn't have many filter options



