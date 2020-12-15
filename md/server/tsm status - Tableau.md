

tsm status
==========

::: {.caption .article__tags .content-only-hidden}
[Version: 2020.3]{.article__tags--version}\
[]{.article__tags--applies-to}\
[]{.article__tags--role}
:::

::: {#content-body}
::: {#mc-main-content role="main"}
You can use the `tsm status` command to display the status of Tableau
Server and individual services (processes) that run as part of Tableau
Server.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_status_tsm.htm#){.heading-item__link .print-hidden} Synopsis

</div>

`tsm status [global options]`

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_status_tsm.htm#){.heading-item__link .print-hidden} Options

</div>

-v, \--verbose

Optional.

Display status for every node in the [Tableau
Server]{.VariablesProductName} cluster.

`tsm status` will return one of these potential statuses for a Tableau
Server node:

-   `RUNNING`: The node is running without error statuses for any
    service or process.

-   `DEGRADED`: The node is running with one or more primary services -
    such as the repository - in an error state. If you have a single
    instance of the Messaging service and it fails,

-   `ERROR`: All primary services or processes are in an error state on
    the node.

-   `STOPPED`: The node is stopped, with no error statuses.

When running `tsm status` with the `--verbose`option, TSM will return a
status for each individual service (process). Possible status messages
include:

-   `is running`: The service is running.

-   `status is unavailable`: The status cannot be determined - such as
    when services are starting up.

-   `is in a degraded state`: The service is running, but returning
    errors. This status indicates the service failed to install
    properly, has not been configured, or has failed in some way.

-   `is in an error state`: The service is running, but returning
    errors. This status indicates the service failed to install
    properly, or has not been configured.

-   `is synchronizing`: The File Store process is synchronizing with
    another instance of File Store.

-   `is decommissioning`: The File Store process is being
    decommissioned.

-   `is running (Active Repository)`: The active repository is running.
    This is the expected status.

-   `is running (Passive Repository)`: The passive repository is
    running. This is the expected status when there are two repositories
    configured.

-   `is stopped`: The service is stopped. This does not mean a service
    is in an error or problem state. Some services only run when needed
    (the Database Maintenance service for example).

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_status_tsm.htm#){.heading-item__link .print-hidden} Global options
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

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
