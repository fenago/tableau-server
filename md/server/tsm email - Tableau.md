

tsm email
=========
Use the `tsm email` command to view and test your SMTP configuration.

For more information about configuring SMTP, see [Configure SMTP
Setup](https://help.tableau.com/current/server/en-us/config_smtp.htm).

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_email.htm#){.heading-item__link .print-hidden} []{#tsm}tsm email test-smtp-connection {#tsm-email-testsmtpconnection}
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Run this command to test the STMP connection. When run, TSM will attempt
to establish a connection with the SMTP server that you have configured
for Tableau Server. TSM will also return a connection status and the
details of the SMTP configuration.

In some cases, the command will return a false-positive status. For
example, if your Postfix SMTP server is set to require TLS, but Tableau
Server is not configured for TLS, the connection is established and
TSM will report a succesful connection. However, in this scenario,
Postfix actually rejects the email message after TSM has connected.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_email.htm#){.heading-item__link .print-hidden} Synopsis

</div>

`tsm email test-smtp-connection [global options]`

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_email.htm#){.heading-item__link .print-hidden} Global options
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

-h, \--help

Optional.

Show the command help.

-p, \--password \<password\>

Required, along with `-u` or `--username` if no session is active.

Specify the password for the user specified in `-u` or `--username`.

If the password includes spaces or special characters, enclose it in
quotes:

`--password "my password"`

-s, \--server https://\<hostname\>:8850

Optional.

Use the specified address for Tableau Services Manager. The URL must
start with `https`, include port 8850, and use the server name not the
IP address. For example `https://<tsm_hostname>:8850`. If no server is
specified, `https://<localhost | dnsname>:8850` is assumed.

\--trust-admin-controller-cert

Optional.

Use this flag to trust the self-signed certificate on the
TSM controller. For more information about certificate trust and
CLI connections, see [Connecting
TSM clients](https://help.tableau.com/current/server/en-us/tsm_overview.htm#Connecti).

-u, \--username \<user\>

Required if no session is active, along with `-p` or `--password`.

Specify a user account. If you do not include this option, the command
is run using credentials you signed in with.

 
