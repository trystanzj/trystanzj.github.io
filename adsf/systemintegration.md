---
layout: default
title:  "System Integration"
weight: 6
category: adsf
---

# System Integration

The Farly ADSF is for offline firewall analysis. It requires copies of firewall configuration files, and does not log in to any firewalls.

This section describes two methods for automatically providing the Farly ADSF with up to date firewall configuration files.

It is assumed that an automated or manual firewall configuration backup process is already in place.

## f_import.pl

The default firewall configuration import script is f_import.pl.

The f_import.pl script reads a firewall configuration file, translates the firewall configuration into the Farly firewall model, and then stores the Farly model in the Farly ADSF database.

The f_import.pl script reads the location of the firewall configuration files from the firewalls.csv file, which is specified in /etc/farly/farly.conf. 

The firewalls.csv file is a single column list of firewall configuration files or directories. If the line in firewalls.csv is a file, f_import.pl will attempt to load the file. If the line in the firewalls.csv file is a directory, f_import.pl will attempt to load the most recent file in the directory.

Using the above approach, two possible approaches documented.

* Drive mapping to an existing configuration backup directory.

* Configuring an FTP server in order to have the Network Configuration Management (NCM) system instruct the firewall to FTP its current configuration to the Farly ADSF server on a regularly scheduled basis.

## Drive Mapping

If the network firewall configuration files are already stored in a file system on a Windows file server, map a drive on the Farly ADSF server to the location of the network firewall configuration files.

    mkdir /mnt/cifs
    mount -t cifs //FileServer/FirewallConfigurations /mnt/cifs -o username=farly,password=farly,domain=WORKGROUP

Then, in the firewalls.csv configuration file specify the file names or the directories which f_import.pl should load from.

For example add the following line in firewalls.csv to tell f_import.pl  to load the most recent file in the directory.

    echo /mnt/cifs/test_firewall_1/ >>/etc/farly/firewalls.csv

Other drive mapping technologies such as NFS will also work.

## FTP Server

Another network integration approach is to configure the network configuration management system to have the firewalls ftp their configuration to the Farly ADSF server on a predetermined schedule.  

In this scenario the Farly ADSF server needs to be running an ftp server.

A directory for each firewall would be created on the Farly ADSF server. The firewalls.csv file would point to each of these directories.

In this example vsftpd and the "farly" account will be used for firewall configuration file uploads.

The procedure is:

Ensure the "farly" account has a home directory.

    mkdir /home/farly/

Set the "farly" account password. The firewalls will need to use this password.

    passwd farly

Install the FTP server.

    yum install vsftpd

Modify the following settings in the vsftpd server.

    vi /etc/vsftpd/vsftpd.conf

Disable anonymous access by uncommenting the line:

    anonymous_enable=NO

Use local server accounts for authentication by uncommenting the line:

    local_enable=YES

Chroot local users to their home directories by uncommenting the line:

    chroot_local_user=YES

Ensure vsftpd starts on boot.

    chkconfig vsftpd on

Start the FTP server.

    service vsftpd start

Create a directory for each firewall.

    mkdir /home/farly/test_firewall_1/

Add the above directory to /etc/farly/firewalls.csv.

    echo /home/farly/test_firewall_1/ >>/etc/farly/firewalls.csv

Repeat for all firewalls being monitored by the Farly ADSF.

Configure the Network Configuration Management system to have .test_firewall_1. ftp its configuration to the Farly ADSF server "test_firewall_1/" directory on a regular schedule.

Next, configure crond to run f_import.pl a short time after the firewall has uploaded its configuration to the Farly ADSF server.


