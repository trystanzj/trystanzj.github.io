---
layout: default
title: f_db_dump.pl
weight: 2
category: adsfref
---

# NAME

f\_db\_dump.pl - Display database contents

# SYNOPSIS

f\_db\_dump.pl --db fw|host|srv --all | --key HOSTNAME|ADDRESS

# DESCRIPTION

__f\_db\_dump.pl__ is for troubleshooting. It will display the contents of the 
firewalls, hosts or services databases.

# OPTIONS

- __\--db 'fw|host|srv'__

    'fw' for the firewall database
    'host' for the host database
    'srv' for the service database

- __\--all__

    Dump all objects in the specified database.

- __\--key HOSTNAME|ADDRESS__
  

    Dump an individual object in the specified database. HOSTNAME = the firewall hostname. 
    ADDRESS = A host IP address in dotted decimal format.

- __\--help__

    Prints a brief help message and exits.

- __\--man__

    Prints the manual page and exits.

# EXAMPLES

Display all objects in the firewall database:

    f_db_dump.pl --db fw --all

Display all "test\_fw\_1" objects the firewall database:

    f_db_dump.pl --db fw --key test_fw_1

Display all host objects in the host database:

    f_db_dump.pl --db host --all

Display all service objects associated with 192.168.2.1:

    f_db_dump.pl --db srv --key 192.168.2.1
