##### Tool for enumerating Windows and Samba information from remote systems.
# Main Arguments
---------------------------

    Default Enumeration: -a        
    - Do all simple enumeration (-U -S -G -P -r -o -n -i)
    - option is enabled if other options are not provided
	
    Users: -U
    Machines: -M
	Printers: -i
    Shares: -S
    Password Policy: -P
    Groups and Members: -G
    Detailed User and Share info: -d
	OS info: -o
	nmblookup: -n
	
	verbose: -v
	- Shows full commands being run (net, rpcclient, etc.)
	


# Credentials
-------------------

	Username: -u <Username>
    - specify username to use (default "")
    
    Password: -p <Password>
    - specify password to use (default "")

# Additional options
---------------------------

	Share Write Check: -A
	- Aggressive. Do write checks on shares etc
        
    RID Cycling: -r
    - enumerate users via RID cycling
    
    RID range: -R <Range>
    - default: 500-550,1000-1050, implies -r
	
	Work Group: -w <Work_Group>
    - Specify workgroup manually (usually found automatically)
	
	
	
	-K n      Keep searching RIDs until n consective RIDs don't correspond to
		  a username.  Impies RID range ends at 999999. Useful 
		  against DCs.
	
	-k user   User(s) that exists on remote system (default: administrator,guest,krbtgt,domain admins,root,bin,none)
              Used to get sid with "lookupsid known_username"
              Use commas to try several users: "-k admin,user1,user2"
              
	  -l        Get some (limited) info via LDAP 389/TCP (for DCs only)
    Bruteforce Shares: -s <File>
    - brute force guessing for share names
    
