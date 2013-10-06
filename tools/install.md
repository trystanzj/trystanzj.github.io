---
layout: default
title:  "Installation"
weight: 3
category: tools
---

# Installation

**1) Install Perl.**

Download and install your preferred version of Perl. Some Perl distributions for Windows are [Active Perl](http://www.activestate.com/activeperl/downloads), and [Strawberry Perl](http://strawberryperl.com/).

**2) Install Farly.**

Open a C:> command prompt with "Run as administrator" or terminal as "root" and start cpan:

    cpan

You can configuration cpan to install dependencies automatically:

    cpan> o conf prerequisites_policy follow
    cpan> o conf commit

At the cpan prompt, install Farly:

    cpan> install Farly

This will install all the libraries required to run the Farly Tools.

**3) Download and extract the Farly Tools archive.**

On Windows, copy the f\_\*.pl files in \*-Farly-Tools-\* to %PERL_DIR%\perl\site\bin\

On Linux, copy the f\_\*.pl files in \*-Farly-Tools-\* to /usr/local/bin/. Use chmod to make the f\_\*.pl scripts executable.

**4) Test.**

If everything is working the Farly Tools can then be run in the command prompt or terminal. For example:

    f_search.pl -h


