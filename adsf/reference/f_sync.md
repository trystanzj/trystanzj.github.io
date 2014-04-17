---
layout: default
title: f_sync.pl
weight: 13
category: adsfref
---

# NAME

f\_sync.pl - Inactive host and services removal

# SYNOPSIS

f\_sync.pl --all | --hostname HOSTNAME --hosts | --services

# DESCRIPTION

__f\_sync.pl__ generates the commands needed to remove all references to inactive internal hosts 
or services from the firewall configurations.

Internal hosts and services are considered inactive if they have not been seen for a while. The 
timeout is specified in /etc/farly/farly.conf.

If the host is inactive all references to that host will be removed from the firewall configurations.

If the service was shut down or moved, all firewall rule entries referencing that service will be
removed from the firewall configurations. Services will be matched against rules which have defined
a protocol, destination IP address and destination port number. Subnets and port ranges will not be
matched.

Inactive hosts should be removed before attempting to remove inactive services.

# OPTIONS

- __\--all__

    Run for all firewalls in the database.

- __\--hostname HOSTNAME__

    Run for specified firewall.

- __\--hosts__

    Remove inactive hosts from the firewall configurations.

- __\--services__

    Remove inactive services from the firewall configurations.

- __\--help__

    Prints a brief help message and exits.

- __\--man__

    Prints the manual page and exits.

# EXAMPLES

Remove all rules on all firewalls that reference inactive hosts:

    f_sync.pl --all --hosts

Remove all rules on all firewalls that reference inactive services:

    f_sync.pl --all --services

Remove all rules on "test\_firewall\_1" that reference inactive hosts:

    f_sync.pl --hostname test_firewall_1 --hosts

Remove all rules on "test\_firewall\_1" that reference inactive services:

    f_sync.pl --hostname test_firewall_1 --services
