---
layout: default
title:  "Installation"
weight: 4
category: adsf
---

# Installation

The Farly ADSF is Linux based.  It is installed with an automated online installation script. Some prerequisite libraries are required. The server must be capable of building and installing Perl modules.

The Farly ADSF installation has been tested on CentOS 6 (64bit) Linux.

The installation process involves installing prerequisite libraries and configuring Perl CPAN module installation program.

The requisite libraries and executables are:

* perl
* db4
* db4-devel

The Farly ADSF uses the following non-core Perl core modules:

* BerkeleyDB
* Parse::RecDescent
* Config::Scoped
* Log::Any
* Log::Any::Adapter
* Log::Any::Adapter::Log4perl
* Log::Log4perl
* Template
* NetPacket::IP

All dependencies will be installed automatically by the installer. The Farly ADSF installation program is an online installer which uses CPAN to automatically install all dependencies.

## Install Prerequisites

The Farly ADSF requires Perl and the Oracle Berkeley DB libraries. The Farly ADSF installation program requires that the system be able to build and install Perl modules. On Linux a .C. compiler, .make. and .cpan. are required.

As *root* run the following command in the terminal.

    yum install perl db4 db4-devel gcc make cpan

## Install the Farly ADSF

The Farly ADSF can be installed after the prerequisite libraries and Perl module installation utilities have been successfully installed.

The Farly ADSF requires internet access in order to download dependencies from CPAN. The Farly ADSF installer uses the locally installed CPAN module and its configuration options.  

### Installation

The Farly ADSF must be installed by root.

Download the Farly ADSF tar.gz package.

    wget http://github.com/trystanzj/Farly-ADSF/blob/master/farly-adsf.tar.gz

Extract the Farly ADSF tar.gz package.

    tar -zxvf farly-adsf.tar.gz

Change to the new Farly ADSF directory.

    cd Farly-ADSF

Configure the CPAN installation tools.

    ./configure_cpan.pl

Run the Farly ADSF installation script.

    ./install-farly-adsf.pl

All Farly ADSF dependencies requirements will be validated and installed if necessary.

*The installation script assumes that the server loopback address is 127.0.0.1, the local firewall is not silently dropping packets to the loopback interface, the server is running an ssh service on TCP port 22, and that udp port 59835 is not being used.*

A new user and group named "farly" will be created on the system.

The Farly ADSF installer creates the following directories.

* /etc/farly/
* /var/log/farly/
* /var/db/farly/

If all tests pass and the installation is successful the message *Installation Successful* will be returned.

### Testing

Manual testing of the Farly ADSF data store is needed.

From the Farly ADSF installation directory run the following command.

    ./db_test.pl

Logging output will be displayed and all tests should return 'ok'.

Run the db_test.pl script several times in order to make sure the database is working as expected.
The Farly ADSF applications are now ready to be configured.

