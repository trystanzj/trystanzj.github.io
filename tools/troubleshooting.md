---
layout: default
title:  "Troubleshooting"
weight: 4
category: tools
---

# Troubleshooting

## Windows

You may need to validate the Perl file associations in your Windows configuration.

You may have to ensure that the perl\site\bin\ directory is specified in your Path environment variable.

Depending on your local security settings, you may have to run the tools from a command prompt started with "Run as Administrator."

## Linux

Ensure the /usr/local/bin/ directory is in your path.

Ensure the f\_\*.pl files are set to executable.

The default Farly Tools Perl shebang points to /usr/bin/perl. This may need to be updated if your Perl binary is in a different directory.

## cpan installer

If your internet access must go through a proxy you can have cpan use the proxy by configuring the cpan installer or setting an environment variable before starting cpan.

cpan proxy configuration:

    cpan> o conf init /proxy/

Example Windows environment variables for cpan:

    set http_proxy=http://user:passwd@proxy.company.com:8080
    set ftp_proxy=user:passwd@proxy.company.com:21

Example Linux/Unix environment variables for cpan:

    export http_proxy=http://proxy.company.com
    export ftp_proxy=user:passwd@proxy.company.com:21

