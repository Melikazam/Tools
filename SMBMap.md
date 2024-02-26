# SMBMap
##### SMB enumeration tool
# Main Arguments
---------------------------

	Host: -H
	Domain: -d
	Port: -P
	OS Version: -v
	


# Credentials
-----------------

	Username: -u
	Password: -p
	


# Command Execution
-----------------------------------

	Command: -x <Command>
	--mode <CMDMode>
	- Set the execution method (wmi or psexec, Default wmi)
	


# Shared Drive Search
---------------------------------

	List Drives: -L
	List Recursively: -r <Path>
	List Directories: --dir-only
	File Regex Search: -A <Regex>
	
	Traverse Directory: --depth <Depth>
	- Traverse directory to specific depth. Default is 5.
	


# Filesystem Interaction
---------------------------------

	Downlaod: --download <Path>
	Upload: --upload <Source> <Destination>
	Delete: --delete <Path>
	
	Skip: --skip
	- Skip Delete file confirmation prompt
	


# Additional Options
-----------------------------

	Remove:
		Banner: --no-banner
		- Removes the banner from the top of the output
		Color: --no-color
		- Removes the color from output
		Update: --no-update
		- Removes the "Working on it" message
	
	--timeout SCAN_TIMEOUT
	

# Output
-------

	CSV: --scv <File>
	
	Grep Friendly: -g <File>
	- Only works with -r
	
