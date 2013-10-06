---
layout: default
title: f_remove.pl
weight: 8
category: adsfref
---

# NAME

f\_remove.pl - Generates firewall configurations needed to remove all references to the specified host or subnet.

# SYNOPSIS

f\_remove.pl --all|--hostname HOSTNAME --address ADDRESS|NETWORK

# DESCRIPTION

__f\_remove.pl__ generates the commands needed to remove an IP address or 
subnet from a firewall configuration. All references to the specified host or 
subnet are removed, taking into account both rules and groups.

# OPTIONS

- __\--all__

    Run for all firewalls in the database.

- __\--hostname HOSTNAME__

    Run for the specified firewall.

- __\--address ADDRESS|NETWORK__

    Host IPv4 address, or Network in CIDR or Subnet Mask format

    __Important: Usage of subnet mask format requires quotes__, for example -d "192.168.1.0 255.255.255.0"

- __\--help__

    Prints a brief help message and exits.

- __\--man__

    Prints the manual page and exits.

# EXAMPLES

Remove all rules with IP addresses in the 192.168.2.0/24 network:

    f_remove.pl --all --address 192.168.2.0/24

Remove all rules on "test\_firewall\_1" with IP addresses 192.168.2.2:

    f_remove.pl --hostname test_firewall_1 --address 192.168.2.2
