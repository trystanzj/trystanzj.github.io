---
layout: default
title:  "Applications"
weight: 2
category: adsf
---
# Applications

The Farly ADSF applications are database driven, network topology aware, and network integrated. The Farly ADSF applications can be used for manual or automated firewall analysis, auditing, policy standardization, cleanups and configuration updates.

## f_import.pl

**f_import.pl** loads firewall configurations into the Farly ADSF database.

<p class="text-primary">The Farly ADSF uses Oracle's Berkeley DB Transactional Data Store for firewall and network object storage. Berkeley DB is a fast, reliable, local database with zero administration required.</p>

<p class="text-primary">With the Farly ADSF framework you don't have to worry about were to find the firewall configuration file required by your Farly ADSF application.</p>

<p class="text-primary">Because the Farly ADSF is database driven, a single Farly ADSF application can work on all network firewall configurations.</p>

## f_topology.pl

**f_topology.pl** uses a modified route table to calculate which firewalls protect each network.

<p class="text-primary">The Farly ADSF understands which firewall rules protect which network.</p>

## f_search.pl

**f_search.pl** searches firewall configurations by source IP, source port, destination IP, destination port or any combination of the above. f_search.pl search options are highly customizable.

<p class="text-primary">f_search.pl is topology aware firewall search; No understanding of the firewall topology or configurations are required.</p>

<p class="text-primary">The Farly ADSF provides a simple way to implement automated validation of your organizations firewall security policies.</p>

## f_copy.pl

**f_copy.pl** is a quick answer to the old request, "I need my new server to have the same rules as the old server."

<p class="text-primary">With f_copy.pl you no longer need to hunt for the right groups on multiple firewalls.</p>

## f_remove.pl

**f_remove.pl** generates the firewall configuration commands need to remove all references to a host or subnet from all firewalls in the network.

<p class="text-primary">f_remove.pl makes it much easier to keep your firewall configurations up to date, without the risk of outage causing typo's.</p>

## f_optimise.pl

**f_optimise.pl** finds duplicate and overlapping firewall rules, and automatically generates the firewall configuration commands needed to remove these.

<p class="text-primary">The Farly ADSF makes sure your firewall configurations are always technically correct.</p>

## f_direction.pl

**f_direction.pl** uses the network topology to find firewall rules with source/destination errors.

<p class="text-primary">The Farly ADSF makes sure your firewall rules are in the right place.</p>

## f_discover.pl

**f_discover.pl** finds all firewall configuration references to hosts or services within managed networks. These hosts or services are saved to the network object database.

<p class="text-primary">The Farly ADSF creates an automated link between your firewall perimeter security and the actual services and servers deployed in the network.</p>

## f_probe.pl

**f_probe.pl** uses ICMP, TCP, and UDP probes to determine the status of managed hosts and services referenced by the networks firewall configurations.

<p class="text-primary">The Farly ADSF uses load balancer style active network probing to ensure the network firewall rules are up to date.</p>

## f_sync.pl

**f_sync.pl** can automatically generate the firewall configuration commands needed to remove all firewall references to a retired hosts and services.

<p class="text-primary">The Farly ADSF helps to ensure continuous firewall security policy compliance by automatically removing references to retired hosts and services.</p>

