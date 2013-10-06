---
layout: default
title: f_remove.pl
weight: 3
category: toolsref
---

# NAME


f\_remove.pl - Generates firewall configuration commands needed to remove
              all references to the specified host or subnet.


# SYNOPSIS


f\_remove.pl --file FILE --address IP|NETWORK


# DESCRIPTION


__f\_remove.pl__ removes all references to the specified IP address or network. It takes groups and group dependencies into account.
i.e. A rule referencing a group with only one entry will be removed before the group is removed.


If a network is specified then any references to hosts within that network will also be removed from the configuration.


# OPTIONS


- __\--file FILE__


    __Required__ firewall configuration FILE. 
    

- __\--address IP|NETWORK__


    Host IPv4 address or IPv4 network in CIDR or dotted decimal mask format.  
    

    __Important: Usage of subnet mask format requires quotes__, for example -d "192.168.1.0 255.255.255.0"
    

# EXAMPLES


Remove firewall rule configurations in 192.168.1.0/24:


    f_remove.pl --file config.txt --address 192.168.1.0/24
  

Remove firewall rule configurations referencing host 192.168.2.1:


    f_remove.pl --file config.txt --address 192.168.2.1
  
