---
layout: default
title: f_topology.pl
weight: 4
category: adsfref
---

# NAME

f\_topology.pl - Determines which firewall rule sets filter traffic to or from a specific subnet.

# SYNOPSIS

f\_topology.pl

# DESCRIPTION

__f\_topology.pl__ makes the Farly ADSF network topology aware.

__f\_topology.pl__ imports the network topology into the Farly database. The topology configuration CSV
file is specified in /etc/farly/farly.conf

The topology configuration is a CSV spreadsheet with three columns: hostname, network and interface.  This
information is obtained from network route tables. "hostname" must match the hostname of a firewall
in the Farly database. "interface" is an interface name which must exist on the specified firewall.
"network" is an IP network behind the specified firewall interface.

Using the topology configuration, all paths through the firewalls are calculated and stored in the Farly
database within a "topology container."

Given an IP address or network, the network topology is referenced and the firewall and 
rule sets to search are returned to the Farly application; or, the full network topology can be used
for the analysis being performed.

# OPTIONS

- __\--verbose__

    Prints success status messages.

- __\--help__

    Prints a brief help message and exits.

- __\--man__

    Prints the manual page and exits.
