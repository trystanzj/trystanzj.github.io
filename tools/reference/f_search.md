---
layout: default
title: f_search.pl
weight: 2
category: toolsref
---

# NAME


f\_search.pl - Search firewall rules for all references to the
              specified host, subnet, ports or protocols.


# SYNOPSIS


f\_search.pl --file FILE --option \[VALUE\]


# DESCRIPTION


__f\_search.pl__ searches firewall rules by ID, source IP, source port, 
destination IP, destination port or any combination of the above. 


The configurable search options are "matches" and "contains." The default option 
is "search" which returns every rule that could possibly match the given Layer 3 or
Layer 4 options. This means a search IP range larger than ranges on the firewall will
still return results.


# OPTIONS


- __\--file FILE__


    __Required__ firewall configuration FILE. 
    

- __\--id ID__


    Run the search for the specified rule ID.
    

- __\--action permit|deny__


    Specify the firewall rule action to match.
    

- __\-p PROTOCOL__


    Search for rules using the specified protocol. Can be a text ID such as tcp or udp, or a protocol number.
    

- __\-s ADDRESS__


    Source IP Address, Network or FQDN
    

    __Important: Usage of subnet mask format requires quotes__, for example -s "192.168.1.0 255.255.255.0"
    

- __\--sport PORT__


    Source port name or number
    

- __\-d ADDRESS__


    Destination IP Address, Network or FQDN
    

    __Important: Usage of subnet mask format requires quotes__, for example -d "192.168.1.0 255.255.255.0"
    

- __\--dport PORT__


    Destination port name or number
    

- __\--matches__


    Will match the given search options exactly.
    

- __\--contains__


    Will find rules which the firewall would match.
    

- __\--remove__


    The remove option can be used to generate the commands needed to remove the search result from the firewalls.
    

- __\--exclude-src FILE__


    Specify a FILE with a list of source IPv4 networks to exclude from the search results.
    The typical use case for this option would be to audit external connectivity to important locations in the network.
    

- __\--exclude-dst FILE__


    Specify a FILE with a list of destination IPv4 networks to exclude from the search results.
    

- __\--help__


    Prints a brief help message and exits.
    

- __\--man__


    Prints the manual page and exits.
    

# EXAMPLES


Display all rules which permit connectivity to 192.168.2.1:


    f_search.pl --file config.txt -d 192.168.2.1


Display all rules which permit connectivity to 192.168.2.1 tcp/80:


    f_search.pl --file config.txt -d 192.168.2.1 --dport www


Display all permit rules with a source IP address of "any":


    f_search.pl --file config.txt --matches --action permit -s "0.0.0.0 0.0.0.0"


Display all rules permitting telnet:


    f_search.pl --file config.txt --matches --dport telnet


Report external connectivity to subnet 192.168.3.0/24, port 1433, from external locations:


    f_search.pl --file config.txt -d 192.168.3.0/24 --dport 1433 --exclude-src internal_networks.txt

