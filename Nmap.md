# Nmap
##### Network exploration tool and security/port scanner.

states(Open, Closed, Filtered, Unfiltered, Open|Filtered, Closed|Filtered)

flags(URG, ACK, PSH, RST, SYN, FIN)	

location of scripts: `/usr/share/nmap/scripts/`

# **Host Discovery**
---------------------------------------------------------------------

	ARP: nmap -PR/PE <target>
	ICMP Echo(ping sweep): nmap -sn <target>
	ICMP Timestamp: nmap -PP -sn <target>
	ICMP Address Mask: nmap -PM -sn <target>
	TCP SYN ping: nmap -PS <sequence of ports> -sn <target>
	TCP ACK Ping: nmap -PA <sequence of ports> -sn <target>
	UDP ping: nmap -PU -sn <target>
	


# **Port Scanning**
---------------------------

	udp scans: nmap -sU <target>                       (-)
	tcp 3-way handshake: nmap -sT <target> 	           (Handshake)
	tcp syn(Stealth): nmap -sS <target>    	           (SYN -> RST)*
	tcp ack: nmap -sA <target>              	       (ACK)
	tcp null: nmap -sN <target>            	           (-)
	tcp fin: nmap -sF <target>                         (FIN)
	tcp xmas: nmap -sX <target>            	           (PSH,URG,FIN)
	tcp maimon: nmap -sM <target>          	           (FIN/ACK)
	tcp window: nmap -sW <target>          	           (ACK)
	tcp custom: nmap --scanflags <flags> <target>      (FLAGS)
	idle/zombie: nmap -sI <zombie_ip> <target>         ( )



# **Main Arguments**
-------------------------------

	Port choosing: -p
	- We can separate ports by comma, choose interval, -p- for all port
	scanning or just a single port.
	
	Fast mode: -F
	- It decreases number of scanned ports from 1000 to 100.
	
	Top Ports: --top-port <Count>
	
	Consecutive order: -r
	- Scan ports in consecutive order.
	
	 Open Ports: --open
	
	Speed: -T<0-5>
	- T0 being the slowest and T5 the fastest.
	
	Network interface: -e wlan0
	- Choosing network interface.
	
	Disable ping scan: -Pn
	- Disabling ping scan.



 # **Detection**
-----------------

	OS: -O 	
	- Detect OS.
	  flags:
		 Guess: -O --osscan-guess OR -O --fuzzy
		 - Guess OS detection results
	
	Traceroute: --traceroute 	
	- run traceroute to target
	
	Version: -sV 	
	- Determine service/version info on open ports.
	  flags:
		Intensity: --version-intensity <level>
		- Set intensity level of version detection.
		
		Light intensity: -sV --version-light 	
		- Try the most likely probes (<level> = 2)
		
		Heavy intensity: -sV --version-all 	
		- Try all available probes (<level> = 9)
	
	Version, OS, Default scripts, Traceroute: -A
	- Equivalent to -sV -O -sC --traceroute
	


# **Limitations**
-------------------

	Rate(Min): --min-rate <number>
	- Rate >= <number> packets/sec.
	
	Rate(Max): --max-rate <number>
	- Rate <= <number> packets/sec.
	
	Parallelism(Min): --min-parallelism <number>
	- At least <number> probes in parallel.
	
	Parallelism(Max): --max-parallelism <number>
	- At most <number> probes in parallel.
	
	Top ports only: --top-ports <number>
	- Scans only <number> count top ports. 
	
	Delay: --scan-delay <time>:
	- Delay between packets in miliseconds.



# **Firewall Evasion**
---------------------
	
	Fragment IP data into 8 bytes: -f
	Fragment IP data into 16 bytes: -ff
	Change Fragment Value: --mtu <bytes>
	Packet Length: --data-length
	Packet Port: -g <port>

 # **Spoofing And Decoys**

	Spoofed Source IP: nmap -S <spoofed_ip> <machine_ip>
	Spoofed MAC Address: nmap --spoof-mac <spoofed_mac> <target>
	Decoy Scan: nmap -D [<decoy_ip_1>...<decoy_ip_N>,<my_ip>] <target>



# **Scripts**
------------

	Scripts: --script=<scripts> 	
	- Nmap scripts sequence to run
	
	Default: -sC or --script=default 	
	- run default scripts
	
	Script Arguments: --script-args <arguments>
	


# **Output**
--------------------------

	Normal: -oN 	
	- Save output in normal format.
	
	Grepable: -oG 	
	- Save output in grepable format.
	
	XML: -oX 	
	- Save output in XML format.
	
	All: -oA
	- Save output in normal, XML and Grepable formats.
	
	Verbose mode: -v
	- Provides more detailed and verbose output 
	- use -vv or more for greater effect
	
	Debugging: -d
	- Increase debugging level
	- use -dd or more for greater effect
	


# **Extra**
----------

	--badsum:
	- this is used to generate in invalid checksum for packets. Any real TCP/IP 
	  stack would drop this packet, however, firewalls may potentially respond
          automatically, without bothering to check the checksum of the packet. As such,
          this switch can be used to determine the presence of a firewall/IDS.
	
