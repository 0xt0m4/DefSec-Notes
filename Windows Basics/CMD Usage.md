
# Benefits 
of CLI instead of GUI:

- Faster
	Just imagine how much you should click to find your IP address. You could do that in 1 command, without even leaving the keyboard

- Lower resource usage:
	It requires much fewer system resources

- Automation:
	You can automate almost anything in batch

- Remote management:
	CLI makes it convenient to use SSH, and also much faster than RDP, in case of a bad network or large traffic


# Default commands:

- `set`:
	shows much information, including the path where Windows will execute commands (under the `PATH` variable)

- `ver`:
	Shows the current **OS version**

- `systeminfo`:
	speaks for itself

- `| more`:
	like less in Linux, you can use it if the output is too long

- `help` || `command \?:
	is like the `man` command, gives information for a specific command

- `cls`:
	clear screen

- `shutdown /s`:
	shuts down the system using `/s`, and reboots using `/r`

# Network Commands:

- `ipconfig`:
	shows internet information. You can also use the `/all` flag 

- `ping`:
	works as well

- `tracert`:
	trace route 

- `nslookup`:
	by default, uses the default name server to look up a host or a domain's IP address. You can also set a name server to use using `nslookup asd.com 1.1.1.1`

- `netstat`:
	displays the current network connections and listening ports. The default command only shows the established connection. For more advanced output, **use:**
	`netstat -abon`
	- `-a` displays all connections and ports
	- `-b` shows the programs associated with ports & cons
	- `-o` reveals the PID of the connections
	- `-n` uses a **numerical form** for addresses and port numbers


# File & Disk management

- `cd`:
	changes directory

- `dir`:
	lists the files (like `ls`)
	- `dir /a` displays **hidden and system files** as well
	- `dir /s` displays files in the current and all subdirectories **like tree**

- `type`:
	displays the contents of a file, like `cat`

- `copy`:
	the `cp` command basically

- `move`:
	`mv` command on windows

- `del` || `rease`:
	moves files to the trash, or deletes them



# Task & Process management


- `tasklist`:
	list tasks (the output is long, should use flags)
		`tasklist /FI "imagename eq sshd.exe` **filters** the results to **be equal** to the **image name sshd.exe** 

- `taskkill`:
	the command `taskkill /PID 123` kills the process on PID 123

- `chkdsk`:
	checks the disk's files and volumes for errors and bad sectors

- `driverquery`:
	displays a list of installed drivers

- `sfc /scannow`:
	scans system for corrupted files and tries to repair them