---
layout: default
title: f_optimise.pl
weight: 9
category: adsfref
---

# NAME

f\_optimise.pl - Find duplicate and shadowed firewall rules

# SYNOPSIS

f\_optimise.pl --all | --hostname HOSTNAME \[--verbose\]

# DESCRIPTION

__f\_optimise.pl__ finds technical errors, including shadowed and duplicate rules, in the
firewall rules and automatically generates the configuration commands needed to remove
the unnecessary rules.

If the error is in a configuration firewall rule that uses a group, the configuration
rule will be replaced by the expanded optimised rules and then the configuration rule will
be removed.

# OPTIONS

- __\--all__

    Run optimisation for all firewalls in the database.

- __\--hostname HOSTNAME__

    Run optimisation for the specified firewall.

- __\--verbose__

    Prints a detailed duplicate and shadowed rule analysis. Works with --hostname option only.

- __\--help__

    Prints a brief help message and exits.

- __\--man__

    Prints the manual page and exits.

# EXAMPLES

Print a detailed analysis and optimisation for "test\_firewall\_1":

    f_optimise.pl --hostname test_firewall_1 --verbose

Optimize all firewall rules: 

    f_optimise.pl --all
