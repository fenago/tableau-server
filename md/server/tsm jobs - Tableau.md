

tsm jobs
========
You can use the `tsm jobs` commands to list, reconnect to, and cancel
jobs.

::: {.miniToc}
-   [cancel](https://help.tableau.com/current/server/en-us/cli_jobs_tsm.htm#tsm)
-   [list](https://help.tableau.com/current/server/en-us/cli_jobs_tsm.htm#tsm2)
-   [reconnect](https://help.tableau.com/current/server/en-us/cli_jobs_tsm.htm#tsm3)
:::

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_jobs_tsm.htm#){.heading-item__link .print-hidden} []{#tsm}tsm jobs cancel
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Cancel a job on the server. Any job can be canceled before it starts
running (when queued), but only backup and cleanup jobs can be canceled
when they are already running.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_jobs_tsm.htm#){.heading-item__link .print-hidden} Synopsis

</div>

`tsm jobs cancel --id <jobID> [global options]`

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_jobs_tsm.htm#){.heading-item__link .print-hidden} Options

</div>

-i,\--id \<jobID\>

Required.

Id of the job to cancel.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_jobs_tsm.htm#){.heading-item__link .print-hidden} []{#tsm2}tsm jobs list
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

List asynchronous jobs on the server.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_jobs_tsm.htm#){.heading-item__link .print-hidden} Synopsis {#synopsis1}

</div>

`tsm jobs list [--status <status>] [global options]`

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_jobs_tsm.htm#){.heading-item__link .print-hidden} Options

</div>

-t,\--status \<status\>

Optional.

Filter for jobs that match the given status.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_jobs_tsm.htm#){.heading-item__link .print-hidden} []{#tsm3}tsm jobs reconnect
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Reconnect to an asynchronous job to display its progress. If no job id
is specified, it reconnects to the latest job.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_jobs_tsm.htm#){.heading-item__link .print-hidden} Synopsis {#synopsis2}

</div>

`tsm jobs reconnect[--id <jobID>] [global options]`

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_jobs_tsm.htm#){.heading-item__link .print-hidden} Options

</div>

-i,\--id \<jobID\>

Optional.

Specifies the id of the job that should be reconnected.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_jobs_tsm.htm#){.heading-item__link .print-hidden} Global options
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------

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
