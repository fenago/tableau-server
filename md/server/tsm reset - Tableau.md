

tsm reset
=========
Use the `tsm reset` command to clear the initial admin user so that you
can enter a new one. After you run `tsm reset` you must rerun the
`tabcmd initialuser` command to create a new initial admin. The new name
cannot be the same username as the previous admin user.

If your organization is using Active Directory or LDAP for the Tableau
identity store, then the account and password you specify must match an
account in the directory.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_reset_tsm.htm#){.heading-item__link .print-hidden} Synopsis

</div>

`tsm reset[option] [global options]`

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_reset_tsm.htm#){.heading-item__link .print-hidden} Option

</div>

-d,\--delete-all-sessions

Optional.

Delete all active user sessions when the server is reset.

\--request-timeout \<timeout in seconds\>

Optional.

Wait the specified amount of time for the command to finish. Default
value is 1800 (30 minutes).

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_reset_tsm.htm#){.heading-item__link .print-hidden} Global options
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------

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
TSM clients](https://help.tableau.com/current/server/en-us/tsm_overview.htm#Connecti){.MCXref
.xref}.

-u, \--username \<user\>

Required if no session is active, along with `-p` or `--password`.

Specify a user account. If you do not include this option, the command
is run using credentials you signed in with.
