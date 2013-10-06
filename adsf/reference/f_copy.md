---
layout: default
title: f_copy.pl
weight: 7
category: adsfref
---

# NAME

f\_copy.pl - Copy firewall rules

# SYNOPSIS

f\_copy.pl --old ADDRESS --new ADDRESS

# DESCRIPTION

__f\_copy.pl__ copies all firewall rules that exactly match the old IP address 
to new firewall rules using the new IP address. This script is a quick answer to the 
request "I need the rules for the new server to be the same as the old server."

# OPTIONS

- __\--old ADDRESS__

    The old IPv4 address, in dotted decimal format.

- __\--new ADDRESS__

    The new IPv4 address, in dotted decimal format.

- __\--help__

    Prints a brief help message and exits.

- __\--man__

    Prints the manual page and exits.

# EXAMPLES

Copy rules for existing server 192.168.2.1 to new server 192.168.2.8:

    f_copy.pl --old 192.168.2.1 --new 192.168.2.8


