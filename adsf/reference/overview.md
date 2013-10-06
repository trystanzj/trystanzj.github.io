---
layout: default
title:  "Overview"
weight: 1
category: adsfref
---
# The ADSF Applications

The Farly ADSF includes two applications that provide core Farly ADSF functionality:

* f_import.pl
* f_topology.pl

Two utility applications are included to support implementation of troubleshooting of the f_import.pl and f_topology.plapplications:

* f_create_topology.pl
* f_db_dump.pl

All of the following Farly ADSF applications are dependent on the correct implementation of f_import.pl and f_topology.pl.

There are three applications useful for firewall analysis, auditing and policy standardization:

* f_search.pl
* f_copy.pl
* f_remove.pl

The f_copy.pl and f_remove.pl scripts are intended to be run manually as necessary.

There are two applications for firewall rule monitoring intended to ensure the firewalls are free of technical mistakes:

* f_optimise.pl
* f_direction.pl

Also included are three network integration applications which ensure the firewall rules are in sync with ongoing changes in the network, such as server moves and retirements:

* f_discover.pl
* f_probe.pl
* f_sync.pl

## Running the Farly ADSF Applications

All of the applications can be run manually from the CLI.  Most of these applications can be configured to run automatically on a cron schedule with minimal user intervention required.

If any errors or security issues are found in the firewall configurations, the results can be emailed to network administrators for review and implementation.

<p class="text-danger">Important: Only deploy commands from one application at one time. The Farly ADSF applications do not take into account changes made by other applications. After deployment, re-import the firewall configurations and run the next application.</p>

All Farly ADSF applications are run independently, using the firewall configuration stored in the database. Only the f_import.pl application updates the Farly ADSF database. If configuration output from one Farly ADSF application is used on the firewalls, then a second Farly ADSF application will not account for changes made by first. The firewall configuration needs to updated by the administrator using commands from the first Farly ADSF application; then the firewall configurations must be downloaded and re-imported into the database by f_import.pl; then second Farly ADSF application can be run again.

## Common Options

The --help and --man options are available for all Farly ADSF applications.

The --all and --hostname options are available on most Farly ADSF applications.

### --help

A usage menu is available for all Farly ADSF applications by invoking the --help option.

### --man

A full man page is available for all Farly ADSF applications by invoking the --man option. 

**Note:** *The --man option will generally not work if run as root.*

### --all

The --all option is available for most of the applications. The --all option means the application will run for all firewalls in the database. The --all option would most commonly be used when the application is run automatically by cron.

### --hostname

The --hostname option is available for most of the applications. The --hostname option means the script will be run for the specified firewall only.

