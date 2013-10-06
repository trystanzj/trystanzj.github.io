---
layout: default
title: f_discover.pl
weight: 11
category: adsfref
---

# NAME

f\_discover.pl - Host and Service Discovery

# SYNOPSIS

f\_discover.pl

# DESCRIPTION

__f\_discover.pl__ runs for all firewalls in the firewall database. Any hosts (IP address) or 
services (IP/protocol/port) within managed networks are saved to a database. Host and 
Service discovery time, last seen time, and polled count are noted. If the host or service
already exists in the database, no action will be taken.

__f\_discover.pl__ will read the managed networks file name from /etc/farly/farly.conf. The
list of managed networks are networks that are reachable from the Farly server
with ICMP echo requests and on all TCP and UDP ports.

# OPTIONS

- __\--help__

    Prints a brief help message and exits.

- __\--man__

    Prints the manual page and exits.
