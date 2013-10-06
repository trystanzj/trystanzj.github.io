---
layout: default
title:  "Configuration"
weight: 5
category: adsf
---
# Configuration

Two applications form the basis of the Farly ADSF. These applications import the firewalls and network topology into the Farly ADSF database.

* **f_import.pl**  - Parses and loads configuration files into the Farly ADSF database.

* **f_topology.pl**  - Uses the modified network route table .topology.csv. to calculate paths through the network firewalls.

The Farly ADSF has two primary configuration files.

* **/etc/farly/farly.conf**  Is the primary configuration file. It contains the database connection information and refers to the secondary configuration files.

* **/etc/farly/logging.conf** Is a Log::Log4perl configuration file used by the Farly ADSF.

The Farly ADSF requires three secondary configuration files. These can also be located in /etc/farly/.

* **firewalls.csv** A list of firewall configuration files or directories containing configuration files.

* **topology.csv** A modified network route table which associates a subnet with a firewall interface.

* **networks.csv** A list of networks which the Farly ADSF server is permitted to probe.

# Configuration Files

This section details each configuration file.  All configuration files should be owned by root but readable by everyone.

## /etc/farly/farly.conf
A default farly.conf configuration file is installed by the installation program.  This file should not require any changes, unless you would prefer the secondary configuration files to be created in another location on the server.

## /etc/farly/logging.conf

The /etc/farly/logging.conf is a Log::Log4perl configuration file. The Farly ADSF logging output is fully customizable. The default log file is /var/log/farly/Farly.log

## firewalls.csv

The Farly ADSF uses firewall configuration files. It does not log in to any firewalls. 
The default configuration import script is f_import.pl.

If a specific file is given in firewalls.csv the f_import.pl script will attempt to load that file.
/var/config/dmz-fw/01January2013.txt

If a directory is given in firewalls.csv the f_import.pl script will attempt to load the newest file in the directory.
/var/config/dmz-fw/

Refer to **Network Integration** for more information about the firewalls.csv file.

## topology.csv

The topology.csv file is a modified route table. The format is:

    <hostname>,<network>,<interface name>

If the firewalls are statically routed the f_create_topology.pl script will print the topology.csv contents. 

    f_create_topology.pl > ~/topology.csv
    
    cp /etc/farly/topology.csv ~/topology.csv.bak
    
    cp ~/topology.csv /etc/farly/topology.csv

If the firewalls are not statically routed or running in layer two mode then the topology.csv file will need to be updated manually in order to account for these firewalls.
The *hostname* should be lower case.

## networks.csv

The networks.csv file is the list of managed networks which the Farly ADSF is permitted to probe. These networks should be reachable with ICMP and on all TCP and UDP ports from the Farly ADSF server.

Example networks.csv file contents:

    192.168.1.0/24
    10.1.2.0 255.255.255.0
    172.16.0.0 255.255.254.0

# User Accounts

In order to run Farly ADSF applications, any Farly ADSF users must be able to login to the Farly ADSF server and be a member of the "farly" group.

Local user accounts can be added to the "farly" group using the following command:

    usermod -a -G farly <username>

Integration with an LDAP server is beyond the scope of this document.

