```
           $$$$$$\                                
          $$  __$$\                               
 $$$$$$\  $$ /  \__|$$\   $$\ $$$$$$$$\ $$$$$$$$\ 
$$  __$$\ $$$$\     $$ |  $$ |\____$$  |\____$$  |
$$ /  $$ |$$  _|    $$ |  $$ |  $$$$ _/   $$$$ _/ 
$$ |  $$ |$$ |      $$ |  $$ | $$  _/    $$  _/   
$$$$$$$  |$$ |      \$$$$$$  |$$$$$$$$\ $$$$$$$$\ 
$$  ____/ \__|       \______/ \________|\________|
$$ |                                              
$$ |                                              
\__|	a project of the dragon research group                                              
```

pfuzz is an IPv6 prefix fuzzer. The massive amount of IPv6 address space makes it infeasable to scan for live hosts. Scanning should not be abandoned though-- we simply need to scan smarter in the IPv6 world. 

This tool permutates common and popular IPv6 addressing schemes against a given address prefix to generate lists of potential live hosts. These host lists can be used with other network and vulnerability scanners to perform reconnaissance against these devices.

pfuzz supports IPv6 range queries, which provide crude regular expression support for IPv6 addresses iteration. Using range queries in pfuzz a penetration tester can easily iterate over a well-defined IPv6 address space.

pfuzz identifies a variety of addressing method including SLAAC and DHCPv6-enabled hosts. pfuzz has a modular design so it is easy to modify and improve.

usage
------

$ pfuzz 2001:468:c80::

Create a list of addresses to scan that start with 2001:468:c80::, using the default options (common DHCP addressing schemes)


$ pfuzz 2001:468:c80:: --mac-org=Vmware

Specify the MAC originator to identify SLAAC hosts


$ pfuzz 2001:468:c80:: --mac-org=Xerox | nmap -iL - -F -6

Scan any Xerox-related SLAAC hosts with nmap


$ pfuzz 2001:468:c80::[0-3]:F:[0-FF]

Range queries

modules
--------
* ports - uses common ports to detect common service addresses
* dhcp - scans common DHCP address ranges
* mac - scan for devices based on SLAAC MAC

requirements
--------------
* python 2.6 or greater
* python-netaddr



author
-------
Will Urbanski <will.urbanski a t g m a i l d o t c o m>

a project of the Dragon Research Group <dragonresearchgroup.org>

license
-------
GNU GPL v3
