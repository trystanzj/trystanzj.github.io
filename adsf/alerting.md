---
layout: default
title:  "Alerting"
weight: 7
category: adsf
---

# Alerting

The Farly ADSF applications will only generate output if a firewall configuration issue is found.

All Farly ADSF application output is printed to STDOUT. The STDOUT output can be collected and emailed to administrators. This requires a Mail Transfer Agent (MTA) to be running on the Farly ADSF server.

This section details an example Sendmail Mail Transfer Agent (MTA) configuration.

## Sendmail and mailx Example

The following Sendmail configuration uses an authenticated and secured SMTP connection to forward email from the Farly ADSF server. An account is required on the email server.

Install Sendmail and the mailx email client.

    yum erase postfix
    yum install sendmail sendmail-cf cyrus-sasl-plain cyrus-sasl-md5 mailx

Create the client authentication configuration.

    mkdir /etc/mail/auth/
    vi /etc/mail/auth/client-info

Add the following lines:

    AuthInfo:smtp.example.com "U:smmsp" "I:your_username" "P:your_password" "M:PLAIN"
    AuthInfo:smtp.example.com:587 "U:smmsp" "I:your_username" "P:your_password" "M:PLAIN"

The *your_username* and *your_password* fields are the actual SMTP account credentials.

Import the new account credentials.

    cd /etc/mail/auth
    makemap -r hash client-info.db < client-info
    chmod 600 client-info client-info.db

Edit /etc/mail/sendmail.mc

    vi /etc/mail/sendmail.mc

**Note:** *The format of the following back ticks and single quotes are import (watch out for cut and paste issues.)*

Uncomment the following line by removing .dnl. from the start of the line.

    define(`SMART_HOST', `smtp.example.com')dnl

Add the following lines.

    define(`RELAY_MAILER_ARGS., `TCP $h 587')
    define(`ESMTP_MAILER_ARGS., `TCP $h 587')

Uncomment the following line by removing .dnl. from the start of the line.

    define(`confAUTH_MECHANISMS', `EXTERNAL GSSAPI DIGEST-MD5 CRAM-MD5 LOGIN PLAIN')dnl

Add the following line immediately after the above line.

    FEATURE(`authinfo',`hash /etc/mail/auth/client-info.db')dnl

Uncomment the following lines by removing .dnl. from the start of the line.

    define(`confCACERT_PATH', `/etc/pki/tls/certs')dnl
    define(`confCACERT', `/etc/pki/tls/certs/ca-bundle.crt')dnl
    define(`confSERVER_CERT', `/etc/pki/tls/certs/sendmail.pem')dnl
    define(`confSERVER_KEY', `/etc/pki/tls/certs/sendmail.pem')dnl

Add the following lines immediately after the above lines.

    define(`confCLIENT_CERT', `/etc/pki/tls/certs/sendmail.pem')dnl
    define(`confCLIENT_KEY', `/etc/pki/tls/certs/sendmail.pem')dnl

Create the certificates.

    cd /etc/pki/tls/certs
    make sendmail.pem

Generate new a sendmail.cf Sendmail configuration.

    cd /etc/mail
    make

Append the following line to */etc/aliases*:

    root: your_firewall_admin_email_address

This will ensure any mail sent to the root account on the Farly ADSF server is forwarded to a firewall administrator email address. Output could also be forwarded to other accounts. This configuration is not covered.

Restart the Sendmail service.

    service sendmail restart

If the Sendmail server starts OK then send a test email.

    echo "hello" | mail -E -s "test email" root

The email should arrive in *your_firewall_admin_email_address* email account.

See /var/log/maillog for troubleshooting information if required.

