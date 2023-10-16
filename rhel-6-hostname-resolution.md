## SETTING *STATIC HOSTNAME* AND *FQDN*

<br>

1. The FQDN of the system is the name that the **resolver** returns for the hostname. It is usually (not everytime) the hostname (static hostname) followed by the DNS domain name  (only when there is short static hostname). It can be exactly same as the static hostname. Actually It is recommended in **RHEL 6 Deployment Guide** to have the same values for both FQDN and static hostname.

2. To query the hostname we use the `hostname` command with different options. The best way to use this command is to always append `-v` before using any other option, this displays exact sequence in which the `hostname` command works. This way we can also understand the difference between the similar looking but different options. This command basically calls the `gethostname()` function that reads the static hostname from `/etc/sysconfig/network` and then tries to resolve it.

	
	`hostname -v OTHER_OPTIONS`


3. To query the FQDN we run 
 
	`hostname -v -f`

	
	Actually the FQDN is queried by first querying the static hostname then appending the DNS provided domain name if it is a short static hostname and then finally trying to resolve the calculated hostname. If the calculated hostname is resolvable then it is known as the FQDN. 


4. Now coming to static hostname, it is the permanent hostname that can be defined in the `HOSTNAME = VALUE` format in   `/etc/sysconfig/network`. The default value is `localhost` for short hostname and `localdomain` for default domain, making the default value of static hostname to `localhost.localdomain`.

	It is recommended that the static hostname matches the FQDN used / to be used in DNS, but it is not mandatory.


5. There are three ways in which we can set FQDN for a system. 

	5.1 First is to use IP to FQDN mappings in `/etc/hosts`. This file actually does not define hostnames it just maps specific IP's to hostnames/domains/aliases. This way we can even set multiple hostnames/aliases/domains for same or different 	 Interfaces/IP addresses. We do not need to edit the static hostname that is defined in the `/etc/sysconfig/network` rather we just create mappings in `IP FQDN ALIASES` format. In this way the system's static hostname `localhost.localdomain` is 	 unchanged but when the hosts file is parsed the mappings are successfully resolved but when we run `hostname -v -f` it displays `localhost` as the hostname as it justs picks the static hostname and tries to resolve it.

		
	5.2 Second is to set a short static hostname in `/etc/sysconfig/network` and get the DNS domain name from DHCP server that dynamically updates the DNS server with the A/AAAA/PTR to hostname mappings.

	5.3 Third way is to set the static hostname in the `/etc/sysconfig/network` to match the desired FQDN and when the DHCP server receives the DHCP request, it does not append the DNS domain name as it sees that the requested hostame with the DHCP request is 	a long hostname. It is the recommended method. But in this case the DNS domains must be same between the hostname received in DHCP request and the DNS zone that is dynamically updated by the DHCP server.
	
	5.4 The best way of setting the FQDN is merge all the three methods by making the static hostname be an alias for the FQDN using `/etc/hosts` or DNS. In this case the static hostname resolves as it is alias to the mapping between the IP to FQDN (resolvable hostname) in the hosts file. In this method the FQDN and the static hostname will both be resolvable and the output of `hostname -v -f` will be the complete  FQDN as the static hostname derived by `hostname -v` is alias to FQDN and thus 		 resolvable.


6. The configuration files (`/etc/sysconfig/network` and `/etc/hosts`) method has the highest priority defined in the `/etc/nsswitch.conf` in the `hosts: files dns` directive so the configuration files are parsed first and then DNS resolver is used. If the FQDN is defined with by the `/etc/hosts` method then while resolving the hostname the hosts file is parsed first and if there is an entry for the queried hostname then DNS is totally bypassed.


7. You cannot change the FQDN (not static hostname) with the `hostname` command.


