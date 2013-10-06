---
layout: default
title: f_import.pl
weight: 1
category: adsfref
---

# NAME

f\_import.pl - Default file system based firewall configuration importer

# SYNOPSIS

f\_import.pl

# DESCRIPTION

__f\_import.pl__ will read the firewall configuration list file name from /etc/farly/farly.conf

If a specific file is given in the firewall list, f\_import.pl will attempt to 
load that file. If a directory is given in the firewall list, f\_import.pl will
attempt to load the most recent file in the directory.

Details of any failed imports will be written to /var/log/farly/Farly.log

# OPTIONS

- __\--verbose__

    Prints success status messages.

- __\--help__

    Prints a brief help message and exits.

- __\--man__

    Prints the manual page and exits.
