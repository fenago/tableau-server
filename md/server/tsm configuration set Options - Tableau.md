

tsm configuration set Options
=============================

Below is a list of configuration options or keys that you can set with
the `tsm configuration set` command. In many cases you can find out the
current value of a configuration key with the `tsm configuration get`
command.

This list is not intended to be an exhaustive list of Tableau Server
configuration settings. It represents a subset of configuration keys
that can be set by server administrators.  Finally, some keys used
internally by Tableau Server do not appear in this list.

**Note:** Configuration keys are case-sensitive.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_configuration-set_tsm.htm#){.heading-item__link .print-hidden} Basic Use of tsm configuration keys
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

<div>

 Setting a configuration key

</div>

`tsm configuration set -k <config.key> -v <config_value>`

In some cases, you must include the `--force-keys` option to set a
configuration value for a key that has not been set before. For more
information, see [\"Unknown key\"
responses](https://help.tableau.com/current/server/en-us/cli_configuration_tsm.htm#configGetNote).

After setting a configuration key value you must apply the pending
configuration changes using `tsm pending-changes apply`. Until you do,
the new value will not be used by Tableau or show up in the results of a
`tsm configuration get` command. You can view pending changes using
`tsm pending-changes list`. For more information, see [tsm
pending-changes](https://help.tableau.com/current/server/en-us/cli_pending-changes.htm).

<div>

 Resetting a configuration key to default

</div>

To reset a configuration key back to its default value, use the `-d`
option:

`tsm configuration set -k <config.key> -d`

<div>

 Viewing the current value of a configuration key

</div>

To see what a configuration key is currently set to, use the
`configuration get` command:

`tsm configuration get -k <config.key>`

In certain cases you cannot get a configuration value for a key that has
not been set before. Instead the `tsm configuration get` command will
return an \"Unknown key\" response. For more information, see [\"Unknown
key\"
responses](https://help.tableau.com/current/server/en-us/cli_configuration_tsm.htm#configGetNote).

Configuration Keys
-------------------


Default value: `false`

Disables access to the Tableau Administrative views. By default, access
to views is enabled (this option is set to \"false\").


Default value: `true`

Allows access to the [Tableau Server REST API[(Link opens in a new
window)]{.sr-only}](https://help.tableau.com/current/api/rest_api/en-us/help.htm#REST/rest_api.htm).
By default, this functionality is enabled.


Default value: `true`

Allows access to the PostgreSQL (Tableau Server\'s own database)
historical auditing tables.


**Note:** Added in version 2018.3.6

Default value: `false`

Controls whether parallel processing of external directory group
synchronization jobs is allowed when there are multiple backgrounders.
By default a scheduled synchronization of external directory groups is
handled serially, by a single backgrounder. Set this to `true `to enable
parallel processing on multiple backgrounder instances.



Default value: `true`

Controls the caching of workbook query results after scheduled extract
refresh tasks.

Default vaule: `2.0`

The threshold for caching workbook query results after scheduled extract
refresh tasks. The threshold is equal to the number of views that a
workbook has received in the past seven days divided by the number of
refreshes scheduled in the next seven days.

The following two *backgrounder* command options determine how long a
flow task can run before the flow background task is canceled. These two
commands together determine the total timeout value for flow tasks.



Default value: `1800`

The number of seconds beyond the setting in `backgrounder.querylimit`
before a background task is canceled. This setting makes sure that tasks
do not hold up subsequent jobs if they are stalled. The setting applies
to processes listed in `backgrounder.timeout_tasks`. 1800 seconds is 30
minutes.

<div>



</div>

Default value: `14400 `

The number of seconds for a flow run task is canceled. 14,400 seconds is
4 hours.

<div>

<div>



</div>

Default value: `5`

The number of consecutive failures of a subscription, extract, or flow
run job before that job is suspended. Suspending continuously failing
jobs helps preserver backgrounder resources for other jobs. To disable
suspension of failing background tasks, set this to `-1`.

</div>

<div>

<div>



</div>

**Note:** Added in version 2020.3.0

Default value: `info`

The logging level for the backgrounder process. This is dynamically
configurable, so if you are only changing this you do not have to
restart Tableau Server. For more information, see [Change Logging
Levels](https://help.tableau.com/current/server/en-us/logs_debug_level.htm).

</div>

<div>



</div>

Default value: `7200`

Longest allowable time, in seconds, for completing a single extract
refresh task or subscription task. 7200 seconds = 2 hours.

**Note:** If a background task reaches this time limit, it may continue
to run for an additional several minutes while being canceled.

<div>



</div>

Default value: `true`

Controls whether extract refresh and flow run alerts are enabled for all
sites on the server. By default alerts are enabled. To disable the
alerts for all sites on a server, set this to `false`.

Extract alerts can be enabled or disabled on a site basis by site
administrators in site settings, or at the user level in user settings.

<div>



</div>

Default value: `60000 `

Controls the time window that identifies backgrounder jobs which are
determined to have the same scheduled start time.

The backgrounder process orders work that is scheduled at the same time
to be executed by job type, running the fastest category of jobs first:
Subscriptions, then Incremental Extracts, then Full Extracts.

Jobs are batched to determine which jobs are scheduled at the "same
time". A value 60,000 milliseconds (the default) indicates jobs for
schedules starting within a 1 minute window should be classified in the
same batch and so are ordered by type within that batch.

<div>



</div>

Default value: `5`

Determines the number of consecutive subscription failures that must
occur before alerting for a condition is suspended. When set to the
default of `5`, alerting is suspended after 5 consecutive subscription
failures. A value of `-1 `will allow notification email to continue
indefinitely. This threshold is server-wide, so applies to all
subscriptions defined on the server.

<div>



</div>

Default value: `true`

Controls whether backgrounder will cache images that are generated for
subscriptions. Cached images do not have to be regenerated each time so
caching improves subscription performance. By default image caching is
enabled. To disable image caching for all sites on a server, set this to
`false`.

<div>



</div>

Default
value: `refresh_extracts, increment_extracts, subscription_notify, single_subscription_notify, check_data_alert, run_flow, encrypt_extracts, decrypt_extracts, rekey_extracts, extract_encryption_maintenance`

The list of tasks that can be canceled if they run longer than the
combined values in `backgrounder.querylimit` and
`backgrounder.extra_timeout_in_seconds`. The list of tasks is delimited
with commas. The default list represents all the possible values for
this setting.

<div>

<div>



</div>

Default
value: `C:\ProgramData\Tableau\Tableau Server\data\tabsvc\files\backups\`{mc-conditions="Product.serverwindows"}

The location in which the` tsm maintenance backup` command creates the
backup. This is also the location where the backup file must be when
restored using the `tsm maintenance restore` command or
the` tsm maintenance send-logs` command. For more information, see [tsm
File
Paths](https://help.tableau.com/current/server/en-us/cli_default_filepaths_tsm.htm).

</div>

<div>

<div>



</div>

Default
value: `C:\ProgramData\Tableau\Tableau Server\data\tabsvc\files\log-archives\`{mc-conditions="Product.serverwindows"}

The location in which the` tsm maintenance ziplogs` command creates the
zipped archive. For more information, see [tsm File
Paths](https://help.tableau.com/current/server/en-us/cli_default_filepaths_tsm.htm).

</div>

<div>

<div>



</div>

Default
value: `C:\ProgramData\Tableau\Tableau Server\data\tabsvc\files\siteexports\`{mc-conditions="Product.serverwindows"}

The location in which the` tsm sites export` command creates the export
file. For more information, see [tsm File
Paths](https://help.tableau.com/current/server/en-us/cli_default_filepaths_tsm.htm).

</div>

<div>

<div>



</div>

Default
value: `C:\ProgramData\Tableau\Tableau Server\data\tabsvc\files\siteimports\`{mc-conditions="Product.serverwindows"}

The location in which the` tsm sites import` command expects the import
file to be located. For more information, see [tsm File
Paths](https://help.tableau.com/current/server/en-us/cli_default_filepaths_tsm.htm).

</div>

<div>

<div>



</div>

**Note:** Added in version 2020.3.0

Default value: `info`

The logging level for Cluster Controller. This is dynamically
configurable, so if you are only changing this you do not have to
restart Tableau Server. For more information, see [Change Logging
Levels](https://help.tableau.com/current/server/en-us/logs_debug_level.htm).

</div>

<div>



</div>

Default value: `300000`

The length of time, in milliseconds, that Cluster Controller will wait
for the Coordination Service (ZooKeeper), before determining that
failover is required.

<div>



</div>

Default value: `60  `

The frequency, in minutes, at which [Tableau
Server] checks to determine if data-alert
conditions are true.

(The server also checks whenever extracts related to data alerts are
refreshed.)

<div>



</div>

Default value: `true   `

Determines how often [Tableau Server] rechecks
failing data alerts. When set to `true`, the server rechecks failing
alerts at the frequency defined by `dataAlerts.checkIntervalInMinutes`.
When set to `false`, the server rechecks failing alerts every five
minutes, more quickly notifying alert recipients if data conditions have
changed, but reducing server performance.

(The server also checks whenever extracts related to data alerts are
refreshed.)

<div>



</div>

Default value: `350`

Determines the number of consecutive data alert failures that must occur
before alerting for a condition is suspended. When set to the default of
350, alerting is suspended after roughly two weeks of alerts. This
threshold is server-wide, so applies to any data alert defined on the
server.

<div>

<div>



</div>

**Note:** Added in version 2020.3.0

Default value: `info`

The logging level for Data Server. This is dynamically configurable, so
if you are only changing this you do not have to restart Tableau Server.
For more information, see [Change Logging
Levels](https://help.tableau.com/current/server/en-us/logs_debug_level.htm).

</div>


<div>



</div>

Default value: `27042`

Port that the data engine runs on.
:::


<div>



</div>

Default value: `9700`

Port that the data server runs on.
:::

<div>

 DataServerRefreshMetadataPerSession

</div>

Default value: `false`

Determines whether Tableau Server will make additional queries to get
updated schema data for a published data source when there have been
changes in the underlying schema structure. This is disabled by default
for performance reasons, and there is a delay in the display of schema
changes. If you want changes in the schema of a live published data
source to be reflected quickly, or if you see errors (for example, \"An
error occurred while communicating with the data source: Invalid column
name. Statement could not be prepared.\") set this to `true`. When set
to `true`, Tableau Server makes additional queries to update the schema.

<div>



</div>

The default value varies based on the amount of system memory. Use the
table below to determine your default value:

  System Memory         Default Value
  --------------------- ------------------------------
  29 GB or less         `-Xmx256m -Xms256m` (256 MB)
  30 GB to 45 GB        `-Xmx1g -Xms1g` (1 GB)
  46 GB to 58 GB        `-Xmx2g -Xms2g` (2 GB)
  59 GB to 100 GB       `-Xmx4g -Xms4g` (4 GB)
  Greater than 100 GB   `-Xmx8g -Xms8g` (8 GB)

Controls the Elastic Server heap size. Increasing the heap size beyond
the default value may improve Ask Data performance. The heap size should
usually be less than half of the full machine memory. Append the letter
\'k\' to the value to indicate kilobytes, \'m\' for megabytes, or \'g\'
to indicate gigabytes. As a general rule, set initial heap size (`-Xms`)
equal to the maximum heap size (`-Xmx`) to minimize garbage collections.

Here is a suggestion of how much memory to allocate, based on the number
of data sources and available memory. Actual performance will vary
depending on the server, the number of fields in your data sources, and
other factors.

-   1 to 100 data sources: 256 MB (minimum)
-   100 to 500 data sources: 1 GB (recommended)
-   500 to 1,000 data sources: 2 GB
-   1,000 to 2,000 data sources: 4 GB
-   2,000 to 4,000 data sources: 8 GB
-   4,000 to 8,000 data sources: 16 GB
-   8,000 or more data sources: 32 GB

This option was added beginning with [Tableau
Server]{.VariablesTabsProductServer} version: 2019.1

<div>

<div>



</div>

Default value: `false`

Controls whether Tableau Server creates a \"shadow copy\" of a shared
Excel spreadsheet (`.xlxs` or `.xlxm`) that is being used as a live data
source. When enabled, this option prevents Excel users from seeing a
\"Sharing Violation Error\" and a message that the file is \"currently
in use.\" This option can have a performance impact with large Excel
files. If Excel users do not need to edit the shared file, you do not
need to enable this option.

**Note:** Tableau Server always attempts to create a shadow copy of a
`.xls` file. This option does not change that behavior.

This option was added beginning with Tableau Server versions: 2019.1.5,
2019.2.1.

</div>

<div>

<div>



</div>

Default value: `true`

Controls whether Tableau Server uses the Apache ActiveMQ service
(Tableau Server Messaging Service) for the internal messaging mechanism.

This option was added beginning with Tableau Server version: 2019.4.

</div>

<div>



</div>

Default value: `false`

Controls whether Desktop License Reporting is enabled on the server.
When set to `false` (the default), no Administrative Views related to
desktop licenses are available. Set this to `true` to enable license
reporting and make license usage and expiration Administrative Views
visible on the Server Status page. **Note:** Desktop License Reporting
must be enabled on the client (Tableau Desktop) in order for information
to be reported to Tableau Server.

<div>

<div>



</div>

Default value: `true`

Controls whether Tableau Server uses the new internal messaging
mechanism.

This option was added beginning with Tableau Server version: 2019.4.

</div>

<div>

<div>



</div>

Default value: `true`

Controls whether Tableau Server allows embedded credentials in bootstrap
files. When enabled (the default), embedded credentials are included in
the bootstrap file unless you specify that they should not be included.
Set this to `false` if credentials should never be included in any
bootstrap file you generate. For more information on generating
bootstrap files, see [tsm topology nodes
get-bootstrap-file](https://help.tableau.com/current/server/en-us/cli_topology_tsm.htm#TSMGetBootstrap).

This option was added beginning with Tableau Server version 2019.3.

</div>

<div>



</div>

Default value: `false`

Applies only to servers that use local authentication. Set to `true`to
let users reset their passwords with a \"Forgot password\" option on the
sign-in page.

<div>

<div>



</div>

**Note:** Added in version 2020.3.0

Default value: `info`

The logging level for File Store. This is dynamically configurable, so
if you are only changing this you do not have to restart Tableau Server.
For more information, see [Change Logging
Levels](https://help.tableau.com/current/server/en-us/logs_debug_level.htm).

</div>

<div>



</div>

Default value: `false`

The Cache-Control HTTP header specifies whether the client browser
should cache content sent from Tableau Server. To disable caching of
Tableau Server data on the client, set this option to `true`.

<div>



</div>

Default value: `false`

The HTTP Strict Transport Security (HSTS) header forces browsers to use
HTTPS on the domain where it is enabled.

<div>



</div>

Default value: `"max-age=31536000"`

By default, HSTS policy is set for one year (31536000 seconds). This
time period specifies the amount of time in which the browser will
access the server over HTTPS.

<div>



</div>

Default value: `16380 `

The maximum size (bytes) of header content that is allowed to pass
through the Apache gateway on HTTP requests. Headers that exceed the
value set on this option will result in browser errors, such as HTTP
Error 413 (Request Entity Too Large) or authentication failures.

A low value for `gateway.http.request_size_limit` can result in
authentication errors. Single sign-on solutions that integrate with
Active Directory (SAML and Kerberos) often require large authentication
tokens in HTTP headers. Be sure to test HTTP authentication scenarios
before deploying into production.

We recommend setting `tomcat.http.maxrequestsize` option to the same
value that you set for this option.

<div>



</div>

Default value: `true`

The X-Content-Type-Options response HTTP header specifies that the MIME
type in the Content-Type header should not be changed by the browser. In
some cases, where MIME type is not specified, a browser may attempt to
determine the MIME type by evaluating the characteristics of the
payload. The browser will then display the content accordingly. This
process is referred to as \"sniffing.\" Misinterpreting the MIME type
can lead to security vulnerabilities. The X-Content-Type-Options HTTP
header is set to \'nosniff\' by default with this option.

<div>



</div>

Default value: `true`

The HTTP X-XSS-Protection response header is sent to the browser to
enable cross-site scripting (XSS) protection. The X-XSS-Protection
response header overrides configurations in cases where users have
disabled XXS protection in the browser. The X-XSS-Protection response
header is enabled by default with this option.

<div>

<div>



</div>

**Note:** Added in version 2020.3.0

Default value: `info`

The logging level for Gateway. This is dynamically configurable, so if
you are only changing this you do not have to restart Tableau Server.
For more information, see [Change Logging
Levels](https://help.tableau.com/current/server/en-us/logs_debug_level.htm).

</div>

<div>



</div>

Default value: \<hostname\>

The name (URL) of the server, used for external access to Tableau
Server. If Tableau Server is configured to work with a proxy server or
external load balancer, it is the name entered in a browser address bar
to reach Tableau Server. For example, if Tableau Server is reached by
entering `tableau.example.com`, the name for gateway.public.host is
`tableau.example.com`.

<div>



</div>

Default value: `80 `(`443 `if SSL)

Applies to proxy server environments only. The external port the proxy
server listens on.

<div>



</div>

Default value: `false`

Enabling this can provide some help in protecting against slow POST
(Denial-of-Service) attacks by timing out POST requests that transfer
data at extremely slow rates.

**Note:** This will not eliminate the threat of such attacks, and could
have the unintended impact of terminating slow connections.

<div>



</div>

Default value: `header=15-20,MinRate=500 body=10,MinRate=500`

When enabled by the preceding option,
`gateway.slow_post_protection.enabled`, this option sets the Apache
httpd ReadRequestTimeout. The httpd directive is documented at [Apache
Module mod\_reqtimeout[(Link opens in a new
window)]{.sr-only}](https://httpd.apache.org/docs/2.4/mod/mod_reqtimeout.html).
The primary use of this option is as a defense the Slowloris attack. See
the Wikipedia entry, [Slowloris (computer security)[(Link opens in a new
window)]{.sr-only}](https://en.wikipedia.org/wiki/Slowloris_(computer_security)).

<div>



</div>

Default value: `7200`

Longest amount of time, in seconds, that the gateway will wait for
certain events before failing a request (7200 seconds = 2 hours).

<div>



</div>

Default value: IP address of proxy server machine

Applies to proxy server environments only. The IP address(es) or host
name(s) of the proxy server.

<div>



</div>

Default value: Alternate names of proxy server

Applies to proxy server environments only. Any alternate host name(s)
for the proxy server.

<div>



</div>

Default value: `0`

When set to 0, the size is set to unlimited and will use all the disk
space that is available.

This option is used to set the disk space limit for a query that spools
to disk. If your disk space usage by the spool.\<id\>.tmp file is higher
than where you need it to be for your environment, it means that queries
are spooling and taking up disk space. Use this option to limit the
amount of disk space that any one query can use. The spool.\<id\>.tmp
file can be found in the temp folder of the user account running Tableau
Server. You can specify this value in K(KB), M(MB), G(GB), or T(TB)
units. For example, you can specify the size limit as 100G when you want
to limit the disk space usage to 100 GB.

For more information about spooling see the Memory and CPU Usage section
in [Tableau Server Data
Engine](https://help.tableau.com/current/server/en-us/data_engine2_intro.htm).

<div>



</div>

Default value: `0`

When set to 0, the size is set to unlimited and will use all the disk
space that is available.

This option is used to set the disk space limit for all queries that
spool to disk. If your disk space usage by the spool.\<id\>.tmp file is
higher than where you need it to be for your environment, it means that
queries are spooling and taking up disk space. The spool.\<id\>.tmp file
can be found in the temp folder of the user account running Tableau
Server. Use this option to limit the amount of disk space in sum total
that all queries use when spooling to disk . You can specify this value
in K(KB), M(MB), G(GB), or T(TB) units. For example, you can specify the
size limit as 100G when you want to limit the disk space usage to 100
GB. Tableau recommends that you start with this configuration when fine
tuning your spooling limits.

For more information about spooling see the Memory and CPU Usage section
in [Tableau Server Data
Engine](https://help.tableau.com/current/server/en-us/data_engine2_intro.htm).

<div>



</div>

Default value: `true`

When set to true, query information is logged.

By default query information is logged. If however you find that the log
files are too large for the amount of disk space available, you can set
it to `false` to disable logging query information. Tableau recommends
leaving this configuration set to `true`.

<div>



</div>

Default value: `false`

Use this setting to log how much time each query takes and the CPU
usage.

<div>



</div>

Default value: `false`

This setting is useful to find out more information about the queries,
like compilation and parsing times. By default this setting is disabled.
You can turn this by setting the value to `true` to collect more details
about your queries. Note, however that this will increase the size of
your data engine log files (\\logs\\hyper).

<div>



</div>

Default value: `true`

When set to `true`, logs query plans of query that are identified as
problematic. Queries that are either canceled, running slower than 10
seconds, or if the queries are spooling to disk fall into this category.
The information in the logs can be useful to troubleshoot problematic
queries. You can change the setting to `false` if you are concerned
about the size of the logs.

<div>



</div>

Default value: `80%`

Controls the maximum amount of memory used by Hyper. Specify the number
of bytes. Append the letter \'k\' to the value to indicate kilobytes,
\'m\' to indicate megabytes, \'g\' to indicate gigabytes, or \'t\' to
indicate terabytes. For example, `hyper.memory_limit='7g'`.
Alternatively, specify the memory limit as a percentage of the overall
available system memory. For example, `hyper.memory_limit='90%'`.

<div>



</div>

Default value: `80%`

This setting only applies to Windows. Hyper keeps decompressed and
decrypted parts of the extract in memory to make subsequent accesses
faster. This setting controls when worker threads will start writing
this data out to a disk cache to reduce memory pressure. If given as a
percentage, the value is interpreted as a percentage of the overall
`hyper.memory_limit` setting. For example,
`hyper.memtracker_hard_reclaim_threshold='60%'`. Absolute values can be
specified as \'k\' (kilobytes), \'m\' (megabytes), \'g\' (gigabytes), or
't' (terabytes). For example,
`hyper.memtracker_hard_reclaim_threshold='10g'`. The value should be
larger than the `hyper.memtracker_soft_reclaim` threshold.

<div>



</div>

Default value: `50%`

This setting only applies to Windows. When interacting with a Hyper
file, Hyper will write out some data for caching or persisting the data.
Windows has the special behavior that it locks freshly written data into
memory. To avoid swapping, we force out the data when Hyper reaches the
configured limit for the reclaim threshold. When the soft reclaim
threshold is reached, Hyper will try to reclaim cached data in the
background to attempt to stay below the reclaim threshold. In situations
where swapping would happen otherwise, triggering reclamation in Hyper
can lead to a better outcome. Therefore, if your Tableau Server
installation experiences a lot of swapping, this setting can be used to
attempt to reduce the memory pressure.

Specify the number of bytes. Append the letter \'k\' to the value to
indicate kilobytes, \'m\' to indicate megabytes, \'g\' to indicate
gigabytes, or \'t\' to indicate terabytes. Alternatively, specify the
value as a percentage of the overall configured memory for Hyper. For
example, `hyper.memtracker_soft_reclaim_threshold='20%'`.

<div>



</div>

Default value: `150%`

Controls the number of network threads used by Hyper. Specify either the
number of network threads (for example, `hyper.network_threads=4`) or
specify the percentage of threads in relation to the logical core count
(for example, `hyper.network_threads='300%'`).

Network threads are used for accepting new connections and sending or
receiving data and queries. Hyper uses asynchronous networking, so many
connections can be served by a single thread. Normally, the amount of
work that is done on network threads is very low. The one exception is
opening databases on slow file systems, which can take a long time and
block the network thread. If connection times are slow when you try to
view or edit dashboards that use extracts and have not been used in a
while and you frequently see "asio-continuation-slow" messages in the
Hyper log and long "construct-protocol" times to Hyper in the Tableau
log, try to increase this value.

<div>



</div>

Default value: `false`

A boolean setting that controls file integrity checks in Hyper. When set
to `true`, Hyper will check the data in an extract file when it is first
accessed. This allows silent corruption and corruption that would crash
Hyper to be detected. In general, it is advisable to turn this setting
on except for installations with very slow disks where it could cause
performance regressions.

<div>



</div>

Default value: `0` (which means unlimited)

Sets an upper bound on the total thread time that can be used by
individual queries in Hyper. Append \'s\' to the value to indicate
seconds, \'min\' to indicate minutes, or \'h\' to indicate hours. For
example, to restrict all queries to a total time usage of 1500 seconds
of total thread time: `hyper.query_total_time_limit='1500s'`.

This setting allows you to automatically control runaway queries that
would otherwise use too many resources. Hyper executes queries in
parallel. For example, if a query executes for 100 seconds and during
this time is running on 30 threads, the total thread time would be 3000
seconds. The thread time of each query is reported in the Hyper log in
the "query-end" log entries in the "total-time" field.

<div>



</div>

Default value: `0` (which means unlimited)

Controls the maximum memory consumption that an individual query can
have. Specify the number of bytes. Append the letter \'k\' to the value
to indicate kilobytes, \'m\' to indicate megabytes, \'g\' to indicate
gigabytes, or \'t\' to indicate terabytes. For example,
`hyper.session_memory_limit='900m'`. Alternatively, specify the session
memory limit as a percentage of the overall available system memory. For
example, `hyper.session_memory_limit='90%'`.

Lowering this value can help when a query is using excessive amounts of
memory and making other queries fail over a long period of time. By
lowering the limit, the single big query would fail (or resort to
spooling if spooling isn't turned off) and not have a negative impact on
other queries.

<div>



</div>

Default value: `true`

Improves the chance that the extract for a query is already cached. If
the node with the extract cached cannot support additional load, you
will be routed to a new node and the extract will be loaded into cache
on the new node. This results in better system utilization because
extracts are only loaded into memory if there is load that justifies the
need.

<div>



</div>

Default value: `true`

Switches the load balancing metric from random selection to picking the
Data Engine (Hyper) node based on a health score that is made of up of a
combination of current Hyper activity and system resource usage. Based
on these values, the load balancer will pick the node that is most
capable of handling an extract query.

<div>



</div>

Default value: `100%`

Sets the upper limit of disk space at which Hyper will stop allocating
space for temporary files. This setting can help to stop the hard disk
from filling up with temporary files from Hyper and running out of disk
space. If disk space reaches this threshold, Hyper will attempt to
recover automatically without administrator intervention.

Specify it as percentage of the overall available disk space to be used.
For example, `hyper.temp_disk_space_limit='96%'`. When set to 100%, all
of the disk space that is available can be used.

For Data Engine to start, the configured amount of disk space must be
available. If not enough disk space is available, you will see a Data
Engine log entry that says, "Disk limit for temporary files has been
reached. Please free up disk space on the device. See the Hyper log for
more information: No space left on device".

<div>



</div>

Default value: 150%

Use this option to set the maximum number of threads Hyper should use
for running queries. Use this when you want to set a hard limit on the
CPU usage. Specify either the number of threads or specify the
percentage of threads in relation to the logical core count. Hyper will
most likely not use more resources than are configured by this setting
but Hyper background and network threads are not affected by this
setting (though they tend to not be CPU intensive).

It is important to consider that this setting controls the number of
concurrent queries that can be executed. So, if you decrease this
setting, the chance of queries needing to wait for currently running
queries to complete increases, which may affect workbook load times.

<div>



</div>

Default value: 100%

Use this option to specify the number of threads that a single query can
be parallelized across if sufficiently many threads are available given
the `hard_concurrent_query_thread_limit` setting. Specify either the
number of threads or specify the percentage of threads in relation to
the logical core count.

To illustrate this, here is a simplified example:

Let\'s say you set this value to 10 threads, this means queries can be
parallelized up to 10 threads. If only 2 queries are running, the
remaining 8 threads are used to parallelize the 2 queries.

The *hyper. hard\_concurrent\_query\_thread\_limit*, and
*hyper.soft\_concurrent\_query\_thread\_limit* options work together to
give you some options to manage your CPU usage while maximizing
available CPU resources to complete queries faster. If you don\'t want
the Data Engine to use all the available CPU on the machine, change it
to less than 100% to a percentage that is optimal for your environment.
The soft limit is a way for you to limit CPU usage but allow it to go
beyond the soft limit up to the hard limit if necessary.

**Note:** The *hyper.hard\_concurrent\_query\_thread\_limit* and
*hyper.soft\_concurrent\_query\_thread\_limit* options replace
hyper.num\_job\_worker\_threads and hyper.num\_task\_worker\_threads
options available in Tableau Server versions 2018.3 and earlier, and are
deprecated in the current version. For information on the
hyper.num\_job\_worker\_threads and hyper.num\_task\_worker\_threads,
see [tsm configuration set Options.[(Link opens in a new
window)]{.sr-only}](https://help.tableau.com/v2018.3/server/en-us/cli_configuration-set_tsm.htm)

<div>



</div>

Default value: `true`

When set to `true`, it allows spooling to disk when querying extracts
exceeds set RAM usage (80% of installed RAM). In other words, it allows
Hyper to execute a query using the disk if it exceeds RAM usage.

Tableau recommends that you use the default setting. You can turn this
off by setting the value to `false` if you are concerned about disk
usage. If you turn this setting off, queries that use more than 80% of
installed RAM will be canceled. Spooling queries usually take
substantially longer to finish.

For more information about spooling see the Memory and CPU Usage section
in [Tableau Server Data
Engine](https://help.tableau.com/current/server/en-us/data_engine2_intro.htm).

<div>



</div>

Default value: `true`

Controls whether [Tableau Server] can add
firewall rules. When set to `true` (the default), [Tableau
Server] will add new firewall rules to allow its
processes to make connections through Windows Firewall. Change this to
`false` if you want to manage all firewall rules yourself and do not
want [Tableau Server] to add new rules.

<div>



</div>

Default value: 128m

Size of heap for Tomcat (repository and solr). This generally does not
need to change except on advice from Tableau.

<div>

<div>



</div>

Default value: `0`

Set to the duration (in seconds) that a user's login-based license
should last before they are prompted to activate Tableau again.

<div>



</div>

Default value: `false`

Set to true to enable [login-based license
management]{.VariablesIBA_lowercase}. Set to false to disable
[login-based license management]{.VariablesIBA_lowercase}.

**Note:** In order to use [login-based license
management]{.VariablesIBA_lowercase}, you must activate a product key
that is enabled for [login-based license
management]{.VariablesIBA_lowercase}. You can use the
`tsm licenses list` to see which product keys have [login-based license
management]{.VariablesIBA_lowercase} enabled.

<div>



</div>

Default value: `15552000`

Set to the maximum duration (in seconds) that a user's login-based
license should last before they are prompted to activate Tableau again.
The maximum value is 15552000 seconds (180 days).

</div>

<div>



</div>

Default value: \"\"

By default, access to any directory will be denied, and only publishing
to Tableau Server with content that is included in the tflx file is
allowed.

A list of allowed network directories for flow input connections. You
must enable Tableau Prep Conductor to run flows on your Tableau Server.
For more information, see [Tableau Prep
Conductor](https://help.tableau.com/current/server/en-us/prep_publishserver_overview.htm).

The following rules apply and must be considered when configuring this
setting:

-   Paths should be accessible by Tableau Server. These paths are
    verified during server startup and at flow run time.

-   Network directory paths have to be absolute and cannot contain
    wildcards or other path traversing symbols. For example
    `\\myhost\myShare\*` or `\\myhost\myShare*` are invalid paths and
    would result in all the paths as disallowed. The correct way to
    safelist any folder under *myShare* would be
    `\\myhost\myShare or \\myhost\\myShare\`.

    **Note:** The `\\myhost\myShare` configuration will not allow
    `\\myhost\myShare1`. In order to safe list both of these folders one
    would have safe list them as \\\\myhost\\myShare;
    \\\\myhost\\myShare1.

-   The value can be either `*`, to allow any network directory, or a
    list of network directory paths, delimited by ";".

-   No local directory paths are allowed even when the value is set to
    `*`.

Important:\
This command overwrites existing information and replaces it with the
new information you provided. If you want to add a new location to an
existing list, you must provide a list of all the locations, existing
and the new one you want to add. Use the following commands to see the
current list of input and output locations:\
\
`tsm configuration get -k maestro.input.allowed_pathstsm configuration get -k maestro.output.allowed_paths`\

For more information and details about configuring allowed directories
for flow input and output connections, see [Safe list Input and Output
Locations[(Link opens in a new
window)]{.sr-only}](https://help.tableau.com/current/prep/en-us/prep_conductor_configure_network_shares.htm).

<div>



</div>

Default value: \"\"

By default, access to any directories will be denied.

A list of allowed network directories for flow output connections. You
must enable Tableau Prep Conductor to run flows on your Tableau Server.
For more information, see [Tableau Prep
Conductor](https://help.tableau.com/current/server/en-us/prep_publishserver_overview.htm).

The following rules apply and must be considered when configuring this
setting:

-   Paths should be accessible by Tableau Server. These paths are
    verified during server startup and at flow run time.

-   Network directory paths have to be absolute and cannot contain
    wildcards or other path traversing symbols. For example
    `\\myhost\myShare\*` or `\\myhost\myShare*` are invalid paths and
    would result in all the paths as disallowed. The correct way to
    safelist any folder under *myShare* would be
    `\\myhost\myShare or \\myhost\\myShare\`.

    **Note:** The `\\myhost\myShare` configuration will not allow
    `\\myhost\myShare1`. In order to safe list both of these folders one
    would have safe list them as \\\\myhost\\myShare;
    \\\\myhost\\myShare1.

-   The value can be either `*`, to allow any network directory, or a
    list of network directory paths, delimited by ";".

-   No local directory paths are allowed even when the value is set to
    `*`.

-   **Note:** If a path is both on the flows allowed list and
    internal\_disasslowed list, internal\_disallowed takes precedence.

For more information and details about configuring allowed directories
for flow input and output connections, see [Safe list Input and Output
Locations[(Link opens in a new
window)]{.sr-only}](https://help.tableau.com/current/prep/en-us/prep_conductor_configure_network_shares.htm).

<div>

<div>



[]{#metadata_timeout}metadata.query.limits.time

</div>

Default value: `20`

This is the longest allowable time, in seconds, for a Catalog or
Metadata API query to run before a timeout occurs and the query is
canceled. Tableau recommends incrementally increasing the timeout limit
to *no more than* 60 seconds using the following command:

`tsm configuration set -k metadata.query.limits.time –v PT30S --force-keys`

**Important:** This option should be changed only if you see the error
described here, [Timeout limit and node limit exceeded
messages](https://help.tableau.com/current/server/en-us/dm_catalog_enable.htm#timeoutnodelimit). Increasing the timeout limit can utilize more CPU for longer,
which can impact the performance of tasks across Tableau Server.
Increasing the timeout limit can also cause higher memory usage, which
can cause issues with the interactive microservices container when
queries run in parallel.

</div>

<div>

<div>



</div>

Default value: `2000`

This is the number of objects (which can loosely map to the number of
query results) that Catalog can return before the node limit is exceeded
and the query is canceled. Tableau recommends incrementally increasing
the timeout limit, to *no more than* 100,000 using the following
command:

`tsm configuration set -k metadata.query.limits.count –v 3000 --force-keys`

**Important:** This option should be changed only if you see the error
described here, [Timeout limit and node limit exceeded
messages](https://help.tableau.com/current/server/en-us/dm_catalog_enable.htm#timeoutnodelimit). Increasing the node limit can cause higher memory usage, which
can cause issues with the interactive microservices container when
queries run in parallel.

</div>

<div>



</div>

Default value: `60`

Controls the interval, in minutes, between refreshes for metrics that
rely on live data sources. A metric refreshes when the server checks for
new data via the metric's connected view.

<div>



</div>

Default value: `10`

Controls the number of consecutive refresh failures that must occur
before the metric owner is warned. When set to the default of 10, a
metric refresh must fail 10 times in a row before the owner is sent a
notification about the failure.

<div>



</div>

Default value: `175`

Controls the number of consecutive refresh failures that must occur
before a metric refresh is suspended.

<div>



</div>

Default value: `true`

Controls whether links to Tableau Server are treated as deep links by
the Tableau Mobile app. When set to `true`, links to supported content
types open in the app. When set to `false`, links open in the mobile
browser. For more information see, [Control deep linking for Tableau
Mobile](https://help.tableau.com/current/mobile/mobile-admin/en-us/admin_mobile_links.htm).

<div>



</div>

Default value: `30000`

The length of time, in milliseconds, that Cluster Controller will wait
for the data engine, before determining that a connection timeout
occurred. The default is 30,000 milliseconds (30 seconds).

<div>



</div>

Set parallel query limit for the specified data source (connection
class). This overrides the global limit for the data source.

<div>



</div>

Default value: `16`

Global limit for parallel queries. Default is 16 except for Amazon
Redshift which has a default of 8.

<div>



</div>

Default value: `false`

Override the operation restrictions when joining data from a single file
connection and a single SQL database connection. Set this option to
`True` to force Tableau to process the join using the live database
connection.

<div>



</div>

Default value: `false`

Use the legacy name format for constrained delegation.

The name format was changed in version 10.1 to allow cross-domain
protocol transition (S4U). If this causes problems with existing
configurations and you don\'t need cross-domain protocol transition,
configure [Tableau Server] to use the old
behavior by setting this to `true`.

<div>

<div>



</div>

Default value: 1

**Note:** The default shard count value is sufficient for most Tableau
Server installations.

Controls the number of data shards for the Elastic Search Concepts index
that stores field names, field synonyms, and analytical terms. The shard
count partitions the search index to reduce total index size, which may
improve the performance of Ask Data\'s semantic parser. Adjusting the
shard count is another performance enhancement measure that you can take
along with increasing the heap size through `elasticserver.vmopts`.

Tableau recommends increasing the shard count by 1 for every 50 GB. To
reduce the number of times you need to adjust the shard count, calculate
the total index size by adding 50% to the current index. For example, if
the total index size is less than 50 GB, then 1 shard is sufficient.
Actual performance will vary depending on the server, the rate at which
the index size grows, and other factors.

-   0 to 50 GB: 1
-   50 GB to 100 GB: 2
-   100 GB to 150 GB: 3

You can use the following command to increase the Concepts index shard
count from default to 2:

`tsm configuration set -k nlp.concepts_shards_count -v 2`

</div>

<div>

<div>



</div>

Default value: 1

Controls the number of data shards for the Elastic Search Values index
that stores values, value synonyms, and aliases. The shard count
partitions the search index to reduce total index size, which may
improve the performance of Ask Data\'s semantic parser. Adjusting the
shard count is another performance enhancement measure that you can take
along with increasing the heap size through `elasticserver.vmopts`.

Tableau recommends increasing the shard count by 1 for every 50 GB. To
reduce the number of times you need to adjust the shard count, calculate
the total index size by adding 50% to the current index. For example, if
the total index size is less than 50 GB, then 1 shard is sufficient.
Actual performance will vary depending on the server, the rate at which
the index size grows, and other factors.

-   0 to 50 GB: 1
-   50 GB to 100 GB: 2
-   100 GB to 150 GB: 3

You can use the following command to increase the Values index shard
count from default to 2:

`tsm configuration set -k nlp.values_shards_count -v 2`

</div>

<div>

<div>



</div>

Default value: `enabled_by_default`

Use this option to set the initial value of the Ask Data Mode when a
site is created. For more information see [Enable or disable Ask Data
for a
site](https://help.tableau.com/current/server/en-us/ask_data_enable.htm#EnableDisableAskDataForSite).

Valid options are `enabled_by_default` (the default),
`disabled_by_default`, and `disabled_always`.

This option was added beginning with Tableau Server versions: 2019.4.5,
2020.1.3.

</div>

<div>

<div>



</div>

Default value: `-Xmx4g –Xms64m`

Use this option to increase the JVM heap size for Tableau Catalog
ingestion.

You can use the following command to increase the max heap size from the
default to 16 GB:

`tsm configuration set -k noninteractive.vmopts -v "-XX:+UseConcMarkSweepGC -Xmx16g -Xms64m -XX:+ExitOnOutOfMemoryError"`

For more information, see [Memory for non-interactive microservices
containers](https://help.tableau.com/current/server/en-us/dm_catalog_enable.htm#Memory).

</div>

<div>

<div>



</div>

Default value: `8060`

Port that PostgreSQL listens on.

</div>

<div>

<div>



</div>

Specifies the computer name of the node with the preferred repository
installed. This value is used if the `--preferred` or `-r` option is
specified with the [tsm topology
failover-repository](https://help.tableau.com/current/server/en-us/cli_topology_tsm.htm#TSMFailoverRepository) command.

Example:

<div>

`tsm configuration set -k pgsql.preferred_host -v "<host_name>"`

**Note:** The `host_name` is case-sensitive and must match the node name
shown in the output of `tsm status -v`.

</div>

</div>

<div>

<div>



</div>

Default value: `8061`

Port used to verify the integrity of the PostgreSQL database. See [tsm
maintenance
backup](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#tsm) for more information.

</div>

<div>



</div>

Default value: `true`

Controls the recommendations feature, which powers recommendations for
data sources and tables (for Tableau Desktop) and recommendations for
views (for Tableau Server). Recommendations are based on the popularity
of content and on content used by other users determined to be similar
to the current user.

<div>



</div>

Default value: `true`

Controls recommendations for views for Tableau Server users. This option
is a child of `recommendations.enabled` and will have no effect if the
parent option is set to false. When the parent option is set to true,
and this option is set to false, data sources and tables will still be
recommended to Tableau Desktop users, but recommendations for views on
Tableau Server will be disabled.

<div>



</div>

Default value: `1024`

Specifies the size in megabytes of the cache server external query
cache.

<div>



</div>

Default value: `31536000`

Specifies the number of seconds for absolute expiry of refresh and
access tokens. The tokens are used by clients (Tableau Mobile, Tableau
Desktop, Tableau Prep, etc) for authentication to Tableau Server after
initial sign-in. This configuration key also governs personal access
token expiry. All refresh and access tokens are a type of OAuth token.
To remove limits set to `-1`. To disable OAuth tokens, see [Disable
Automatic Client
Authentication](https://help.tableau.com/current/server/en-us/devices_connected_credentials.htm).

<div>



</div>

Default value: `1209600`

Specifies the number of seconds when idle OAuth tokens will expire. The
OAuth tokens are used by clients for authentication to Tableau Server
after initial sign-in. To remove limits set to `-1`.

<div>



</div>

Default value: `24`

Specifies the maximum number of refresh tokens that can be issued for
each user. If user sessions are expiring more quickly than you expect,
either increase this value or set it to `-1` to entirely remove token
limits.

<div>



</div>

Default value: `600`

Longest allowable time, in seconds, for completing file synchronization
(600 seconds = 10 minutes). File synchronization occurs as part of
configuring high availability, or moving the data engine and repository
processes.

<div>



</div>

Default value: `false`

Controls whether a schedule name displays when creating a subscription
or extract refresh (the default), or the \"schedule frequency
description\" name describing the time and frequency of the schedule
displays. To configure Tableau Server to display timezone-sensitive
names for schedules, set this value to `true`.

When true, the \"schedule frequency description\" is also displayed
after the schedule name on the schedule list page.

<div>



</div>

Default value: `true`

Shows the \"schedule frequency description\" in the timezone of the user
when true (uses the client browser timezone to calculate the \"schedule
frequency description\").

<div>

<div>



</div>

Added in version 2019.1.

Default value, in milliseconds: `100000`

Specifies, in milliseconds, the amount of time Search & Browse clients
will wait to establish a connection to the Search & Browse server.

On especially busy Tableau Server computers, or if you see log errors
\"Failed zookeeper health check. Refusing to start SOLR.\" increase this
value.

For more information, see [Client session
timeouts](https://help.tableau.com/current/server/en-us/server_process_search-n-browse.htm#searchserverClient_session_timeouts).

</div>

<div>

<div>



</div>

Added in version 2019.1.

Default
value: `-Xmx512m -Xms512m -XX:+ExitOnOutOfMemoryError -XX:-UsePerfData`

Determines JVM options for SOLR.

Of all configurable options, the maximum heap memory, configured by the
`-Xmx` parameter, is the most important when tuning the searchserver. In
most cases this should be set as high as is possible, up to 24 GB, based
on available physical memory on the Tableau Server computer. To change
only the max heap memory, specify the entire default string but only
change the value for `-Xmx`.

Valid values for `-Xmx` depend on available memory on the Tableau Server
computer, but cannot be greater than 24 GB. For more information, see
[Search & Browse Max Heap
Memory](https://help.tableau.com/current/server/en-us/server_process_search-n-browse.htm#searchserverMaxHeapMem).

</div>

<div>

<div>



</div>

Added in version 2020.1.

Default value, in milliseconds: `300000`

Specifies, in milliseconds, the amount of time Tableau Server should
wait for a successful Zookeeper health check on startup.

On especially busy Tableau Server computers, or if you see log errors
\"Failed zookeeper health check. Refusing to start SOLR.\" increase this
value.

For more information, see [Zookeeper connection health check timeout at
startup](https://help.tableau.com/current/server/en-us/server_process_search-n-browse.htm#searchserverZKhealth_chk_timeout).

</div>

<div>

<div>



</div>

Default value, in milliseconds: `100000`

Specifies, in milliseconds, the amount of time Search & Browse clients
will wait to establish a connection to the Coordination Service
(Zookeeper).

For more information, see [Client session
timeouts](https://help.tableau.com/current/server/en-us/server_process_search-n-browse.htm#searchserverClient_session_timeouts).


 ServerExportCSVMaxRowsByCols

</div>

Added in version 2020.3.

Default value: `0` (no limit)

Specifies the maximum number of cells of data that can be downloaded
from View Data into a CSV file. By default, there is no limit. Specify
the number of cells. For example to set a limit of 3 million: 

``` {space="preserve"}
tsm configuration set -k ServerExportCSVMaxRowsByCols -v 3000000 
```

``` {space="preserve"}
tsm pending-changes apply
```

</div>

<div>



</div>

Default value: `false`

Setting to `true` enables JMX ports for optional monitoring and
troubleshooting.

<div>



</div>

Default value: \<number\>

Maximum number of server processes.

<div>



</div>

Default value: `true`

Determines whether or not Tableau Server will attempt to dynamically
remap ports when the default or configured ports are unavailable.
Setting to `false` disables dynamic port remapping.

<div>



</div>

Default value: `false`

Makes client sessions valid only for the IP address that was used to
sign in. If a request is made from an IP address different from that
associated with the session token, the session token is considered
invalid.

In certain circumstances---for example, when Tableau Server is being
accessed by computers with known and static IP addresses---this setting
can yield improved security.

**Note:** Consider carefully whether this setting will help your server
security. This setting requires that the client have a unique IP address
and an IP address that stays the same for the duration of the session.
For example, different users who are behind a proxy might look like they
have the same IP address (namely, the IP address of the proxy); in that
case, one user might have access to another user\'s session. In other
circumstances, users might have a dynamic IP address, and their address
might change during the course of the session. If so, the user has to
sign in again.

<div>



</div>

Default value: `true`

Controls whether you can get images for views with the REST API. For
more information, see [REST API
Reference](https://help.tableau.com/current/api/rest_api/en-us/help.htm#REST/rest_api_ref.htm#query_view_image).

<div>



</div>

Default value: `7200`

When Tableau Server is upgraded or when a .tsbak file is restored, the
background task rebuilds the search index. This setting, in seconds,
controls the timeout setting for that task (7200 seconds = 120 minutes).

<div>

<div>



</div>

Default
value: `HIGH:MEDIUM:!aNULL:!MD5:!RC4:!3DES:!CAMELLIA:!IDEA:!SEED`

Specifies the cipher algorithms that are allowed for SSL.

For acceptable values and formatting requirements, see
[SSLCipherSuite[(Link opens in a new
window)]{.sr-only}](https://httpd.apache.org/docs/current/mod/mod_ssl.html#sslciphersuite)
on the Apache website.

</div>

<div>

<div>



</div>

Default value: `false`

Controls whether email notifications are enabled for server disk space
monitoring. By default, email notifications are enabled. To enable
notifications for disk space monitoring, set this to `true`.

SMTP must be configured for notifications to be sent. For details, see
[Configure SMTP
Setup](https://help.tableau.com/current/server/en-us/config_smtp.htm).

</div>

<div>

<div>



</div>

Default value: `20`

Warning threshold of remaining disk space, in percentage of total disk
space. If disk space falls below this threshold, a warning notification
is sent.

</div>

<div>

<div>



</div>

Default value: `10`

Critical threshold of remaining disk space, in percentage of total disk
space. If disk space falls below this threshold, a critical notification
is sent.

</div>

<div>

<div>



</div>

Default value: `60`

How often, in minutes, that email notifications should be sent when disk
space monitoring is enabled and a threshold is crossed.

</div>

<div>

<div>



</div>

Default value: `true`

Determines whether free disk space history is saved and available to
view in Administrative Views. To disable history storage for monitoring,
set `storage.monitoring.record_history_enabled` to `false`.

</div>

<div>



</div>

Default value: `false`

Controls whether subscriptions are configurable system-wide. See [Set Up
a Site for
Subscriptions](https://help.tableau.com/current/server/en-us/subscribe.htm).

<div>



</div>

Default value: `1800`

Length of time, in seconds, for a view in a workbook subscription task
to be rendered before the task times out. If this time limit is reached
while a view is being rendered, the rendering continues, *but any
subsequent view in the workbook is not rendered*, and the job ends in
error. In the case of a single-view workbook, this value will never
result in the rendering being halted due to a timeout.

<div>

<div>



</div>

Default value: `false`

Controls whether email notifications are enabled for server process
events. By default notifications are sent when processes go down, fail
over, or restart. To enable server process notifications, set this to
`true`.

SMTP must be configured for notifications to be sent. For details, see
[Configure SMTP
Setup](https://help.tableau.com/current/server/en-us/config_smtp.htm).

</div>

<div>

<div>



</div>

**Note:** Added in version: 2020.1.8, 2020.2.5, 2020.3.1

Default value: `false`

Controls whether subscription HTML MIME attachments are sent as
*multipart/related* (the default) or *multipart/mixed*.

To allow the iOS Mail application to properly open these attachments,
set this to `true`.

</div>

<div>

<div>



</div>

Default value: `120`

Controls how long session cookies are valid. By default this is set to
120 minutes. This value also determines how long the embedded
credentials in a node bootstrap file are valid. For more information,
see [tsm topology nodes
get-bootstrap-file](https://help.tableau.com/current/server/en-us/cli_topology_tsm.htm#TSMGetBootstrap).

</div>

<div>

<div>



</div>

**Note:** Added in version 2020.3.0

Default value: `info`

The logging level for the Data Source Properties service. This is
dynamically configurable, so if you are only changing this you do not
have to restart Tableau Server. For more information, see [Change
Logging
Levels](https://help.tableau.com/current/server/en-us/logs_debug_level.htm).

</div>

<div>



</div>

Default value: `16380`

The maximum size (bytes) of header content that is allowed to pass
through the Apache gateway on HTTP requests. Headers that exceed the
value set on this option will result in browser errors, such as HTTP
Error 413 (Request Entity Too Large) or authentication failures.

A low value for `tomcat.http.maxrequestsize` may result in
authentication errors. Single sign-on solutions that integrate with
Active Directory (SAML and Kerberos) often require large authentication
tokens in HTTP headers. Be sure to test HTTP authentication scenarios
before deploying into production.

We recommend setting `gateway.http.request_size_limit` option to the
same value that you set for this option.

<div>



</div>

Default value: `8443`

SSL port for Tomcat (unused).

<div>



</div>

Default value: `8085`

Port that tomcat listens on for shutdown messages.

<div>

<div>



</div>

Default value: `info`

The logging level for microservices in the Interactive Microservice
Container and Non-Interactive Microservice Container. For more
information, see [Change Logging
Levels](https://help.tableau.com/current/server/en-us/logs_debug_level.htm).

</div>

<div>

<div>



</div>

Default value: `info`

Logging level for TSM services. These logs include information that can
be useful if you have problems with TSM services: Administration Agent,
Administration Controller, Client File Service, Cluster Controller,
Service Manager, and License Service. This configuration key does not
change the logging level for Coordination Service or for maintenance
processes. For more information, see [Change Logging
Levels](https://help.tableau.com/current/server/en-us/logs_debug_level.htm#ChangeLoggingLevel) and [Tableau Server
Processes](https://help.tableau.com/current/server/en-us/processes.htm).

</div>

<div>

<div>



</div>

Default value: `info`

Logging level for `control_<app>` services. These logs include
information that can be useful if you are running into problems starting
or reconfiguring a TSM or Tableau Server process. For more information,
see [Change Logging
Levels](https://help.tableau.com/current/server/en-us/logs_debug_level.htm#ChangeLoggingLevel).

</div>

<div>



</div>

Default value: `false`

Specifies whether email addresses and display names of users are changed
(even when changed in Active Directory) when an Active Directory group
is synchronized in Tableau Server. To ensure that user email addresses
and display names are updated during synchronization, set
`vizportal.adsync.update_system_user` to `true`, and then restart the
server.

<div>



</div>

Default value: `true`

When set to `true`, lets users delete comments on views. You can delete
a comment if you created it, are the content owner, a project leader
with an appropriate site role, or are an administrator. To learn which
site roles are required for full project leader access, see
[Project-level
administration](https://help.tableau.com/current/server/en-us/projects.htm#project-admin).

<div>



</div>

Default value: `true`

Specifies whether indexing of site users is done user by user when
importing or deleting users with a CSV file. When set to `true`(the
default) indexing is done as each user is added or deleted. To delay the
indexing of the site users until after the entire CSV file has been
processed, set this to `false`.

<div>



</div>

Default value: `info`

The logging level for vizportal Java components. Logs are written to
`  C:\ProgramData\Tableau\Tableau Server\data\tabsvc\logs\vizportal\*.log`.

Set to `debug` for more information. Using the debug setting can
significantly impact performance, so you should only use this setting
when directed to do so by Tableau Support.

<div>



</div>

Specifies custom client authentication method for OpenID Connect.

To configure Tableau Server to use the IdPs that require the
`client_secret_post`, set this value to `client_secret_post`.

An example would be when connecting to the Salesforce IDP, which
requires this.

<div>



</div>

Specifies the origins (sites) that are allowed access to the REST API
endpoints on Tableau Server when `vizportal.rest_api.cors.enabled` is
set to `true`. You can specify more than one origin by separating each
entry with a comma (,).

`tsm configuration set -k vizportal.rest_api.cors.allow_origin -v https://mysite, https://yoursite`

If `vizportal.rest_api.cors.enabled` is `false`, the origins listed by
this option are ignored. For more information, see [Enabling CORS on
Tableau
Server](https://help.tableau.com/current/api/rest_api/en-us/help.htm#REST/rest_api_concepts_fundamentals.htm#Enabling).

**Note:** You can use an asterisk (**\***) as a wild card to match all
sites. This is not recommended as it allows access from any origin that
has access to the server and can present a security risk. Do not use an
asterisk (**\***) unless you fully understand the implications and risks
for your site.

<div>



</div>

Default value: `false`

Controls whether Tableau Server allows Cross Origin Resource Sharing
(CORS). When set to `true`, the server allows web browsers to access the
[Tableau REST
API](https://help.tableau.com/current/api/rest_api/en-us/help.htm#REST/rest_api_ref.htm)
endpoints. You can use this option and the REST API to create custom
portals. By default, this functionality is not enabled. To specify which
origins (sites) have access, use the
`vizportal.rest_api.cors.allow_origin` option. Only the origins
specified with this option are allowed to make requests to the Tableau
Server REST API. For more information, see [Enabling CORS on Tableau
Server](https://help.tableau.com/current/api/rest_api/en-us/help.htm#REST/rest_api_concepts_fundamentals.htm#Enabling).

<div>



</div>

Default value: `false`

Allows a workbook to be published to the server from Tableau Desktop,
and to be opened from the server, even if the workbook contains SQL or R
expressions that are potentially unsafe (for example, a SQL expression
that could potentially allow SQL injection). When this setting is
`false` (the default), publishing a workbook or opening it from the
server results in an error message, and the workbook is blocked. Before
you set this value to `true` review the Knowledge Base article,
[Blocking or Allowing Insecure Scripts in Tableau Server[(Link opens in
a new
window)]{.sr-only}](https://kb.tableau.com/articles/issue/blocking-or-allowing-insecure-scripts-in-tableau-server).

<div>



</div>

Default value: `true`

Views under the threshold set by `vizqlserver.browser.render_threshold`
or `vizqlserver.browser.render_threshold_mobile` are rendered by the
client web browser instead of by the server. See [Configure Client-Side
Rendering](https://help.tableau.com/current/server/en-us/browser_rendering.htm) for details.

<div>



</div>

Default value: `100`

The default value represents a high level of complexity for a view
displayed on a PC. Complexity factors include number of marks, headers,
reference lines, and annotations. Views that exceed this level of
complexity are rendered by the server instead of in the PC\'s web
browser.

<div>



</div>

Default value: `60`

The default value represents a high level of complexity for a view
displayed on a tablet. Complexity factors include number of marks,
headers, reference lines, and annotations. Views that exceed this level
of complexity are rendered by the server instead of in the tablet\'s web
browser.

<div>



</div>

Default value: `false`

Determines whether or not VizQL sessions are kept in memory when a user
navigates away from a view or closes their browser. The default value
(false) keeps sessions in memory. To close VizQL sessions on leaving a
view or closing a browser, set this to `true`.

<div>



</div>

Default value: `5`

Sets the maximum number of different geographic search locale/language
data sets that can be loaded into server memory at the same time. When
the server receives a geographic search request for locale/language data
set that is not in memory, it will load the set into memory. If loading
the data set will exceed the specified limit, the least recently used
locale/language data set is cleared from memory so the requested one can
be loaded. The minimum value is 1. Each cache takes approximately 60 MB
in memory (so if you set this to 10, the memory usage would be 600 MB
(60 \* 10).

<div>



</div>

Default value: `false`

Specify whether to ignore initial SQL statements for all data sources.
Set this to true to ignore initial SQL:

``` {space="preserve"}
tsm configuration set -k vizqlserver.initialsql.disabled -v true
```

<div>



</div>

Default value: `info`

The logging level for vizportal Java components. Logs are written to
`  C:\ProgramData\Tableau\Tableau Server\data\tabsvc\logs\vizportal\*.log`.

Set to `debug` for more information. Using the debug setting can
significantly impact performance, so you should only use it when
directed to do so by Tableau Support.

**Note:** Beginning with version 2020.3.0, this is dynamically
configurable, so if you are only changing this you do not have to
restart Tableau Server. For more information, see [Change Logging
Levels](https://help.tableau.com/current/server/en-us/logs_debug_level.htm).

<div>



</div>

Default value: `5`

Auto recover configuration for web authoring. Specifies the number of
changes that a user must make to trigger auto save. Take care when
changing this value. Auto recover functionality may impact the
performance of web authoring and other viz-related operations on Tableau
Server. We recommend tuning this value by making incremental adjustments
over time.

<div>



</div>

Default value: `9100`

Base port for the VizQL servers.

<div>



</div>

Default value: `true`

When set to `true`, prevents VizQL sessions from being reused after the
original user signs out.

<div>



</div>

Default value: `1800`

Longest allowable time for updating a view, in seconds. 1800 seconds =
30 minutes.

<div>



</div>

Default value: `3`

Auto recover configuration for web authoring. The maximum number of
attempts to recover the same session. Take care when changing this
value. Auto recover functionality may impact the performance of web
authoring and other viz-related operations on Tableau Server. We
recommend tuning this value by making incremental adjustments over time.

<div>



</div>

Default value: `5`

Number of minutes of idle time after which a VizQL session is eligible
to be discarded if the VizQL process starts to run out of memory.

<div>



</div>

Default value: `30`

Number of minutes of idle time after which a VizQL session is discarded.

<div>



</div>

Default value: `1`

The amount of time, in minutes, to cache images that are generated by
the Query View Image method of the REST API. For more information, see
the [REST API Reference[(Link opens in a new
window)]{.sr-only}](https://help.tableau.com/current/api/rest_api/en-us/REST/rest_api_ref.htm#query_view_image)
in the REST API help.

<div>



</div>

Default value: `true`

Controls the display of the [Tableau Workbook] option of the
Download menu in views. When set to `false`, the Tableau Workbook option
is unavailable.

<div>



</div>

Default value: `true`

Controls the display of Share options in views. To hide these options,
set to false.

**Note:** Users can override the server default by setting the
\"showShareOptions\" JavaScript or URL parameter.

<div>



</div>

Specifies one or more URL schemes to allow (safe list) when using [URL
actions[(Link opens in a new
window)]{.sr-only}](https://help.tableau.com/current/pro/desktop/en-us/help.htm#actions_url.html)
on views and dashboards. The schemes `http`, `https`, `gopher`,
`mailto`, `news`, `sms`, `tel`, `tsc`, and `tsl` are allowed (safe
listed) by default. This command can contain multiple comma and
space-separated values, as in this example:

`tsm configuration set -k vizqlserver.url_scheme_whitelist -v scheme1, scheme2`

The values you specify overwrite previous settings. Therefore, you must
include the full list of schemes in the `set` command. (You cannot amend
the list of schemes by running the `set` command repeatedly.)

<div>



</div>

Default value: `1024`

Auto recover configuration for web authoring. Size limit (KB) for a
workbook that will auto save. Workbooks larger than this value will not
be auto-saved. Take care when changing this value. Auto recover
functionality may impact the performance of web authoring and other
viz-related operations on Tableau Server. We recommend tuning this value
by making incremental adjustments over time.

<div>



</div>

Deprecated. Use `tsm data-access web-data-connectors allow` instead.

Determines whether extract refreshes for web data connectors (WDCs) are
enabled in Tableau Server. To disable refresh for all WDCs, set the
value for this key to `false`, as shown below:

`tsm configuration set --key webdataconnector.refresh.enabled --value false`

To learn more, see [Web Data Connectors in Tableau
Server](https://help.tableau.com/current/server/en-us/datasource_wdc.htm).

<div>



</div>

Deprecated. Use `tsm data-access web-data-connectors add` instead.

Specifies one or more web data connectors (WDCs) that can be used by to
access data connections that are accessible over HTTP or HTTPS. This
command is formatted as JSON data on a single line, with all
double-quotes (\") escaped using a backslash (\\).

For example to add a San Francisco Film Locations WDC to the safe list:

`tsm configuration set --key webdataconnector.whitelist.fixed --value "'{\"https://tableau.data.world:443\": {\"properties\": { \"secondary_whitelist\": [\"(https://data.world/)(.*)\"] } } }'"`

To learn more, see [Web Data Connectors in Tableau
Server](https://help.tableau.com/current/server/en-us/datasource_wdc.htm).

<div>



</div>

Deprecated. Use `tsm data-access web-data-connectors allow` instead.

Default value: `true`

When set to `true`, you can use `tsm` commands to manage web data
connectors on the server.

<div>



</div>

Default value: `mixed`

Determines how Tableau Server can run web data connectors. Supported
modes are:

-   `mixed`. Users can run connectors that are on an allowlist (safe
    list) of URLs. This mode originally also allowed users to run WDCs
    that had been imported. Importing WDCs is no longer supported.
-   `fixed`. Users can run connectors that are on an allowlist (safe
    list) of URLs.
-   `insecure`. Users can run any connector.

**Important:** Use the `insecure` option *only* for development and
testing. Because connectors run custom code, running connectors that
have not been vetted can pose a security threat.

<div>



</div>

Default value: `183`

Specifies the number of days after which historical events records are
removed from the PostgreSQL database (the Tableau Server database).

<div>



</div>

Default value: `true`

Controls whether the ownership of a workbook, data source or project can
be changed. Other options include `false` and `adminonly`.

<div>



</div>

Default value: `true`

When set to `true`, helps prevents a malicious person from
\"clickjacking\" a Tableau Server user. In a clickjack attack, the
target page is displayed transparently over a second page, and the
attacker gets the user to click or enter information in the target page
while the user thinks he or she is interacting with the second page.

For more information, see [Clickjack
Protection](https://help.tableau.com/current/server/en-us/clickjack_protection.htm).


<div>



</div>

Default value: value of `%USERDOMAIN%`

The fully qualified domain name of the Active Directory server to use.
:::

<div>

<div>



</div>

Default value: null

Allows connection from Tableau Server to secondary Active Directory
domains. A secondary domain is one that Tableau Server connects to for
user synchronization, but is a domain where Tableau Server is not
installed. Tableau Server will attempt to connect to secondary domains
for user and group synchronization. In some cases, Tableau Server may be
unable to connect to the secondary domain, which will result in the
error, \"Domain not in whitelist (errorCode=101015).\"

Setting the `wgserver.domain.whitelist` option is required by a fix for
the security vulnerability, [\[Important\] ADV-2020-003: Tableau Server
Forced Authentication[(Link opens in a new
window)]{.sr-only}](https://community.tableau.com/s/news/a0A4T000001v3SaUAI).
As of February 2020, the fix for this vulnerability is included in all
latest versions and maintenance releases of Tableau Server.

To set this option, enter the secondary domain enclosed by
double-quotes. Multiple domains must be separated by a comma and a
space. For example,
`tsm configuration set -k wgserver.domain.whitelist -v "example.org, domain.com"`.

Wildcard functionality is not supported. For example, if Tableau
connects to `sub1.example.org` and `sub2.example.org`, then both domains
must be added.

Updating the `wgserver.domain.whitelist` option overwrites the existing
value. Therefore, if you are adding a new domain to an existing set of
domains stored in the value, include all existing domains with the new
domain when you set the option. You can retrieve the full list of
existing domains by running
`tsm configuration get –k wgserver.domain.whitelist`.

</div>

<div>



</div>

Default value: `false`

Enforces IP client matching for trusted ticket requests.

<div>



</div>

Default value: `true`

Controls whether Tableau Server accepts HTTP OPTIONS requests. If this
option is set to `true`, the server returns HTTP 405 (Method Not
Allowed) for HTTP OPTIONS requests.

<div>



</div>

Specifies the name of the attribute in which your SAML IdP stores user
names. By default, this is set to `username`. If the attribute name that
your IdP uses contains spaces, enclose it in quotation marks. For more
information, see [Configure Server-Wide
SAML](https://help.tableau.com/current/server/en-us/config_saml.htm) or [Configure Site-Specific
SAML](https://help.tableau.com/current/server/en-us/saml_site_specific.htm).

<div>



</div>

Default value: `false`

Default of false means that when users select the sign-in button on an
embedded view, the IdP's sign-in form opens in a pop-up window.

When you set it to true, and a server SAML user who is already signed in
navigates to a web page with an embedded view, the user will not need to
sign in to see the view.

You can set this to true only if the IdP supports signing in within an
iframe. The iframe option is less secure than using a pop-up, so not all
IdPs support it. If the IdP sign-in page implements clickjack
protection, as most do, the sign-in page cannot display in an iframe,
and the user cannot sign in.

If your IdP does support signing in via an iframe, you might need to
enable it explicitly. However, even if you can use this option, it
disables Tableau Server clickjack protection for SAML, so it still
presents a security risk.

<div>



</div>

Default value: `3000`

Specifies the maximum number of seconds, from creation, that a SAML
assertion is usable.

<div>



</div>

Default value: `180`

Sets the maximum number of seconds difference between Tableau Server
time and the time of the assertion creation (based on the IdP server
time) that still allows the message to be processed.

<div>



</div>

Default value: `false`

Controls whether there is a session lifetime for server sessions. Set
this to `true`to configure a server session lifetime.

<div>



</div>

Default value: `240`

The number of minutes of idle time before a sign-in to the web
application times out.

<div>



</div>

Default value: `1440`

The number of minutes a server session lasts if a session lifetime is
set. The default is 1440 minutes (24 hours). If
`wgserver.session.apply_lifetime_limit` is `false` (the default) this is
ignored.

<div>



</div>

Default value: `false`

Specifies whether to extend access to server resources for users
authenticated by trusted tickets. Default behavior allows users to
access views only. Setting this to `true` allows users with valid
trusted tickets to access server resources (projects, workbooks, and so
on) as if they had signed in using their credentials.

<div>



</div>

Default value: `80 `(`443 `if SSL)

External port that Apache listens on for workerX (where a "worker" is
the term used for subsequent server nodes in the cluster).
worker0.gateway.port is Tableau Server's external port. In a distributed
environment, worker0 is the initial Tableau Server node.

<div>



</div>

Default value: \<number\>

Number of VizQL servers.

<div>



</div>

Specifies the number of transactions necessary to cause the Coordination
Service to create a snapshot of the logs. By default this value is
100,000 transactions. If your Coordination Service is not writing enough
transactions to result in snapshots, the automatic cleanup of snapshots
older than five days will not take place, and you may lose disk space to
the transaction logs. By default transaction logs and snapshots are
created in the Tableau data directory.
