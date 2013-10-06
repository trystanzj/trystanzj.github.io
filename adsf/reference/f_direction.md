---
layout: default
title: f_direction.pl
weight: 9
category: adsfref
---

# NAME

f\_direction.pl - Find Firewall Rule Source/Destination Errors

# SYNOPSIS

f\_direction.pl --all | --hostname HOSTNAME

# DESCRIPTION

__f\_direction.pl__ generates configurations to remove firewall rule source destination reversal
errors. These errors may be caused by rules being configured backwards, in the wrong rule set,
or as the result of a firewall rule set split or merge.

__Important: f\_direction.pl requires a default route for each firewall in the network topology
configuration in order to work properly.__

# OPTIONS

- __\--all__

    Run for all firewalls in the database.

- __\--hostname HOSTNAME__

    Run for specified firewall.

- __\--help__

    Prints a brief help message and exits.

- __\--man__

    Prints the manual page and exits.

# EXAMPLES

Validate the direction of all firewall rules in the firewall database:

    f_direction.pl --all

Validate the direction of all "test\_firewall\_1" rules:

    f_direction.pl --hostname test_firewall_1
