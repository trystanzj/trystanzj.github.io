---
layout: default
title:  "Applications"
weight: 2
category: tools
---

# Applications

Farly Tools are simple CLI driven Perl scripts for performing firewall optimisations, audits, and configuration rewrites.

## f_search.pl

**f_search.pl** can search firewall access-lists by ID, source IP, source port, destination IP, destination port or any combination of the above. Search behaviour is customizable through the use of the --matches or --contains options.

<p class="text-primary">f_search.pl could be used for day to day firewall troubleshooting, automated verification of organization specific firewall security policies, or even firewall configuration cleanups.</p>

## f_analyze.pl

**f_analyze.pl** finds, reports on, and generates firewall configuration commands needed to remove duplicate or overlapping firewall rules.

<p class="text-primary">f_analyze.pl can help you ensure that your firewall configurations are free of technical mistakes.</p>

## f_remove.pl

**f_remove.pl** generates the firewall configuration commands needed to remove all references to a retired host or network.

<p class="text-primary">f_remove.pl makes it much easier to keep your firewall configurations up to date without the risk of outage causing typo's.</p>

## f_rewrite.pl

**f_rewrite.pl** is for interactive firewall configuration re-writes.

<p class="text-primary">Running f_rewrite.pl on the output of f_analyze.pl is a simple way to update and standardize your legacy firewall configuration object-group names.</p>

