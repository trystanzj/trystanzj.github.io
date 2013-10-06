---
layout: default
title: f_search.pl
weight: 6
category: adsfref
---

# NAME


f\_search.pl - Searches firewall configurations for all references to the specified host, subnet, ports or protocols.


# SYNOPSIS


f\_search.pl \[--all\] \[--matches|contains\] \[--action|p|s|sport|d|dport VALUE\] \[--exclude-src|exclude-dst FILE\] \[--remove\]


# DESCRIPTION


__f\_search.pl__ searches firewall configurations by source IP, source port, 
destination IP, destination port or any combination of the above. 


The configurable search options are "matches" and "contains." The default option 
is "search," which returns every rule that could possibly match the given Layer 3 or
Layer 4 options. This means a search range larger than ranges on the firewall will
still return results.


f\_search.pl uses the network topology to determine which firewall to search based
on the source or destination IP addresses specified. The specific firewall configuration
does not need to be specified.  The --all option can be specified in order to force
a search of all firewall configurations in the database.


# OPTIONS


- __\-p PROTOCOL__ 


    Search for rules using the specified protocol. Can be a text ID such as tcp or udp, or a protocol number.
    

- __\-s ADDRESS__


    Source IP Address, Network or FQDN
    

    __Important: Usage of subnet mask format requires quotes__, for example -s "192.168.1.0 255.255.255.0"
    

- __\-d ADDRESS__


    Destination IP Address, Network or FQDN
    

    __Important: Usage of subnet mask format requires quotes__, for example -d "192.168.1.0 255.255.255.0"
    

- __\--sport PORT__


    Source Port Name or Number
    

- __\--dport PORT__


    Destination Port Name or Number
    

- __\--action permit|deny__


    Specify the firewall rule action to match.
    

- __\--all__


    The default route is not used to search firewalls.  Use --all if no IP address is specified
    in the search or if the IP address is not a managed IP address.
     

- __\--matches__


    Will match the given search options exactly.
    

- __\--contains__


    Will find rules the firewall would match.
    

- __\--remove__


    The remove option can be used to generate the commands needed to remove the search result from the firewalls.
    

- __\--exclude-src FILE__


    Specify a FILE with a list of source IPv4 networks to exclude from the search results.
    

- __\--exclude-dst FILE__


    Specify a FILE with a list of destination IPv4 networks to exclude from the search results.
    

- __\--help__


    Prints a brief help message and exits.
    

- __\--man__


    Prints the manual page and exits.
    

# EXAMPLES


Display all rules which permit connectivity to 192.168.2.1:


    f_search.pl -d 192.168.2.1


Display all rules which permit connectivity to 192.168.2.1 tcp/80:


    f_search.pl -d 192.168.2.1 --dport www


Display all permit rules, on any firewall, with a source IP address of "any":


    f_search.pl --all --matches --action permit -s "0.0.0.0 0.0.0.0"


Display all rules, on any firewall, permitting telnet:


    f_search.pl --all --matches --dport telnet


Report all connectivity to subnet 192.168.3.0/24, database port 1433 from external locations:


    f_search.pl -d 192.168.3.0/24 --dport 1433 --exclude-src internal_networks.txt

