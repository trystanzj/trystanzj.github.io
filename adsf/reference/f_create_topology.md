---
layout: default
title: f_create_topology.pl
weight: 3
category: adsfref
---

# NAME

f\_create\_topology.pl - Create the Farly ADSF network topology configuration using
                       static route tables and interface configurations.

# SYNOPSIS

f\_create\_topology.pl

# DESCRIPTION

__f\_create\_topology.pl__ is a helper application which creates the Farly ADSF 'topology.csv' 
configuration file.

__Important: This application only works for firewalls with static route tables.__

This application will not work for firewalls that use dynamic routing or operate in 
layer two transparent mode. Topology information for non-statically
routed firewalls will have to be added to the topology configuration
manually.

Put the full path to the topology.csv file in /etc/farly/farly.conf.

# OPTIONS

- __\--help__

    Prints a brief help message and exits.

- __\--man__

    Prints the manual page and exits.

# EXAMPLES

Create the "topology.csv" file:

    f_create_topology.pl >topology.csv
