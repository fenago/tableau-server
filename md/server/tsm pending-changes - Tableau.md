

tsm pending-changes
===================

::: {.caption .article__tags .content-only-hidden}
[Version: 2020.3]{.article__tags--version}\
[]{.article__tags--applies-to}\
[]{.article__tags--role}
:::

::: {#content-body}
::: {#mc-main-content role="main"}
Use the `tsm pending-changes` commands to apply, discard, or view
pending configuration and topology changes to [Tableau
Server]{.VariablesProductName}.

Passwords and secrets that you enter during TSM configuration are
encrypted after you save them. Secrets remain encrypted until, during,
and after you apply pending changes. For more information about secret
storage, see [Manage Server
Secrets](https://help.tableau.com/current/server/en-us/security_secret_storage.htm#Understa){.MCXref
.xref}.

::: {.miniToc}
-   [tsm pending-changes
    apply](https://help.tableau.com/current/server/en-us/cli_pending-changes.htm#pending-changes-apply){.MCXref
    .xref}
-   [tsm pending-changes
    discard](https://help.tableau.com/current/server/en-us/cli_pending-changes.htm#pending-changes-discard){.MCXref
    .xref}
-   [tsm pending-changes
    list](https://help.tableau.com/current/server/en-us/cli_pending-changes.htm#pending-changes-view){.MCXref
    .xref}
:::

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_pending-changes.htm#){.heading-item__link .print-hidden} []{#pending-changes-apply}tsm pending-changes apply {#tsm-pendingchanges-apply}
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Use the `tsm pending-changes apply` command to apply pending
configuration and topology changes to [Tableau
Server]{.VariablesProductName}.

If the pending changes require a server restart, the
`pending-changes apply` command will display a prompt to let you know a
restart will occur. This prompt displays even if the server is stopped,
but in that case there is no restart. You can suppress the prompt using
the `--ignore-prompt` option, but this does not change the restart
behavior. If the changes do not require a restart, the changes are
applied without a prompt.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_pending-changes.htm#){.heading-item__link .print-hidden} Synopsis

</div>

`tsm pending-changes apply [global options]`

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_pending-changes.htm#){.heading-item__link .print-hidden} Options

</div>

-iw, \--ignore-warnings

Optional.

Ignore warning level constraints.

\--ignore-prompt

Optional.

Suppress the prompt for restart. This only suppresses the prompt. The
restart behavior is unchanged.

\--request-timeout \<timeout in seconds\>

Optional.

Wait the specified amount of time for the command to finish. Default
value is 1800 (30 minutes).

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_pending-changes.htm#){.heading-item__link .print-hidden} []{#pending-changes-discard}tsm pending-changes discard {#tsm-pendingchanges-discard}
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Use the `tsm pending-changes discard` command to discard pending
configuration and topology changes to [Tableau
Server]{.VariablesProductName}.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_pending-changes.htm#){.heading-item__link .print-hidden} Synopsis {#synopsis1}

</div>

`tsm pending-changes discard [options] [global options]`

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_pending-changes.htm#){.heading-item__link .print-hidden} Options {#options1}

</div>

\--config-only

Optional.

Discard only pending configuration changes.

\--topology-only

Optional.

Discard only pending topology changes.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_pending-changes.htm#){.heading-item__link .print-hidden} []{#pending-changes-view}tsm pending-changes list {#tsm-pendingchanges-list}
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Lists pending configuration and topology changes to [Tableau
Server]{.VariablesProductName}. Any changes that do not require a server
restart will be listed as not requiring a restart. If none of the
pending changes require a restart, a message displays saying the changes
do not require a server restart. If any change in the list requires a
restart, the entire list of pending changes will result in a restart.
For more information on dynamic configuration or topology changes, see
[Dynamic
Configuration](https://help.tableau.com/current/server/en-us/whatsnew_server.htm#dynamic-config-20-2){.MCXref
.xref} and [Tableau Server Dynamic Topology
Changes](https://help.tableau.com/current/server/en-us/server_process_hot_topo.htm){.MCXref
.xref}.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_pending-changes.htm#){.heading-item__link .print-hidden} Synopsis {#synopsis2}

</div>

`tsm pending-changes list [options] [global options]`

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_pending-changes.htm#){.heading-item__link .print-hidden} Options {#options2}

</div>

\--config-only

Optional.

List only pending configuration changes.

\--topology-only

Optional.

List only pending topology changes.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_pending-changes.htm#){.heading-item__link .print-hidden} Global options
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

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
