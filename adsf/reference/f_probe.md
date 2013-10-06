---
layout: default
title: f_probe.pl
weight: 11
category: adsfref
---

# NAME

f\_probe.pl - Probe all hosts and services in the database

# SYNOPSIS

f\_probe.pl

__This script must be run as 'root'__

# DESCRIPTION

__f\_probe.pl__ uses active probing to check the status of internal hosts and services. (i.e. if a host
or service is down, it can safely be removed from the firewall rules.)

__f\_probe.pl__ iterates through the hosts and services database.

Every host is pinged via ICMP to see if it is up or down. The host is considered to be down if there is
no response to the ICMP echo.

Services referenced in the firewall rules are pinged via TCP or UDP pings to check if the service is up or
down. TCP pings are done with a TCP SYN and TCP services are considered down if there is no response to the
SYN packet. UDP pings are done with a custom UDP ping module. UDP services are only considered to be down 
if an ICMP unreachable packet is received from the host.

If the host or service is up then the last seen time is updated in the database.

# OPTIONS

- __\--help__

    Prints a brief help message and exits.

- __\--man__

    Prints the manual page and exits.
