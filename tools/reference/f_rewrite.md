---
layout: default
title: f_rewrite.pl
weight: 5
category: toolsref
---

# NAME


f\_rewrite.pl  -  Interactively re-write an access-list using user specified group ID's.


# SYNOPSIS


f\_rewrite.pl --file FILE --id ID --groupby PROPERTY --output OUTPUT\_FILE


# DESCRIPTION


__f\_rewrite.pl__ is used to interactively rewrite a firewall configuration in order to
create accurate and logically named groups.


By running __f\_rewrite.pl__ repeatedly an expanded firewall configuration can be shrunk
to a minimal number of configuration lines.


__f\_rewrite.pl__ will use existing group ID's.


# OPTIONS


- __\--file FILE__


    __Required__ firewall configuration FILE. 
    

- __\--id ID__


    Run for the specified rule ID.
    

- __\--groupby PROPERTY__


    Must be one of DST\_PORT, SRC\_IP, DST\_IP or SRC\_PORT.
    

- __\--output OUTPUT\_FILE__


    Write the group by commands to this file.
    

- __\--help__


    Prints a brief help message and exits.
    

- __\--man__


    Prints the manual page and exits.
    

# EXAMPLES


Run a full firewall rewrite. The cfg.txt "outside-in" rules are expanded and optimized. 
The --output commands are applied to the firewall before running the next f\_rewrite.pl
command.


Create new expanded optimized firewall rules:


    f_analyze.pl --file cfg.txt --id outside-in --new outside-in-new >new_cfg.txt
  

Create new destination port groups:


    f_rewrite.pl --file new_cfg.txt --id outside-in-new --groupby DST_PORT --output new_dst_port_groups.txt
  

Create new client source IP address groups:


    f_rewrite.pl --file cfg_with_dport_groups.txt --id outside-in-new --groupby SRC_IP --output new_src_groups.txt
  

Create new server destination IP address groups:


    f_rewrite.pl --file cfg_with_dport_src_groups.txt --id outside-in --groupby DST_IP --output new_dst_groups.txt
  
