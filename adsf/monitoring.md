---
layout: default
title:  "Monitoring"
weight: 7
category: adsf
---

# Monitoring

The Farly ADSF applications can be run automatically by the cron daemon. The crond daemon executes commands on a pre-configured schedule.

Each Farly ADSF script can be configured to run on a regular basis.

## crond

This section details a configuration for automated Farly script execution.

Install the cron daemon.

    yum install vixie-cron crontabs

Set crond to start on boot.

    chkconfig crond on

Start crond.

    service crond start

## Example Configuration

In this example it's assumed that the network configuration management system will have the firewalls to FTP their configurations to the Farly ADSF server at 11:00pm, the f_import.pl and f_topology.pl application will run at 12:00am, and the optimisation, direction error checking and network integration applications will begin running at 1:00am. The firewall auditing applications will execute at 2:00am.

All of the scripts, with the exception of f_probe.pl, can be run under the "farly" account. The f_probe.pl application must be run as root.

The Farly ADSF applications only print output if administrator attention is required. This output is piped to the mail command. The mail command is used in order to customize the email subject line and sender information.

In this example, all mail is sent to the Farly ADSF server's *root* account, which is then forwarded to an administrator email address.

Create a system crond configuration to run Farly scripts.

    vi /etc/cron.d/farly

Run f_import.pl immediately followed by f_topology.pl at 12:00am.

    00 00 * * * farly /usr/local/bin/f_import.pl | mail .E -s "Farly ADSF Import Report" root && /usr/local/bin/f_topology.pl | mail -E -s "Farly ADSF Topology Calculation" root

Run the Farly ADSF analysis scripts at 1:00am.

    00 01 * * * farly /usr/local/bin/f_optimise.pl --all | mail -E -s "Farly ADSF Optimisation Report" root
    
    00 01 * * * farly /usr/local/bin/f_direction.pl --all | mail -E -s "Farly ADSF Direction Error Report" root
    
    00 01 * * * farly /usr/local/bin/f_sync.pl --all --hosts | mail -E -s "Farly ADSF Inactive Hosts Report" root
    
    00 01 * * * farly /usr/local/bin/f_sync.pl --all --services | mail -E -s "Farly ADSF Inactive Services Report" root

<p class="text-danger">Important: If for some reason more than one of these applications generate output then the output from only a single application should be used at one time. The apps run independently of each other and changes by one application will not be taken into account by another application.</p>

The f_discover.pl application will find references to any managed hosts or services. It can be run after the other analysis applications complete.

    00 02 * * * farly /usr/local/bin/f_discover.pl | mail -E -s "Farly ADSF Host and Service Discovery Error Report" root

The f_probe.pl application must be run as root. The default Farly ADSF host and service timeout is two days. If f_probe.pl is run every 4 hours then a host or service will be probed twelve times before being declared down. After the host or service is declared to be down, the commands to remove all firewall configuration references to the host or service will be sent to administrators by the f_sync.pl application. This timing is customizable.

This configuration schedules the f_probe.pl application to run every four hours.

    0 */4 * * * root /usr/local/bin/f_probe.pl | mail -E -s "Farly ADSF Probe Error Report" root

You can also schedule regular firewall security policy audits. In this example, inside_nets.txt defines a list of networks permitted to connect to a database subnet.

    00 02 * * * farly /usr/local/bin/f_search.pl -d 192.168.2.0/24 --exclude-src /home/farly/inside_nets.txt | mail -E -s "Farly ADSF 192.168.2.0/24 Database Network Connectivity Audit" root

See /var/log/cron for crond log information.

In order to have Farly script output emailed to firewall administrators a Mail Transfer Agent such as Sendmail needs to be installed and configured on the Farly ADSF server. See "Alerting."

