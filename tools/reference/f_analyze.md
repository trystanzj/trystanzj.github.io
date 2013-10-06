---
layout: default
title: f_analyze.pl
weight: 4
category: toolsref
---

# NAME


f\_analyze.pl - Find duplicate and shadowed firewall rules


# SYNOPSIS


f\_analyze.pl --file FILE --id ID \[--verbose\] --new ID | --remove


# DESCRIPTION


__f\_analyze.pl__ finds duplicate and shadowed firewall rules. A specific 
firewall configuration file and access-list ID must be specified.


# OPTIONS


- __\--file FILE__


    __Required__ firewall configuration FILE. 
    

- __\--id ID__


    Run analysis for the specified rule ID.
    

- __\--verbose__


    Displays a detailed report showing all duplicate or shadowed rules.
    

- __\--new ID__


    Displays an optimised rule set in expanded format with the new ID.
    

- __\--remove__


    Displays the commands required to remove unneeded firewall rule entries.
    

- __\--help__


    Prints a brief help message and exits.
    

- __\--man__


    Prints the manual page and exits.
    

# EXAMPLES


Print a detailed analysis and new rule set.


    f_analyze.pl --file fw_config.txt --id outside-in --verbose --new outside-in-new
    
