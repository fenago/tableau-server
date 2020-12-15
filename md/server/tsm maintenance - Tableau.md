

tsm maintenance
===============

You can use the `tsm maintenance` commands to manage server maintenance
tasks like creating regular backups or restoring [Tableau
Server] from a previously created backup.

::: {.miniToc}
-   [tsm maintenance
    backup](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#tsm){.MCXref
    .xref}
-   [tsm maintenance
    cleanup](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#cleanup){.MCXref
    .xref}
-   tsm maintenance metadata-services
    -   [tsm maintenance metadata-services
        disable](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#cat_disable){.MCXref
        .xref}
    -   [tsm maintenance metadata-services
        enable](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#cat_enable){.MCXref
        .xref}
    -   [tsm maintenance metadata-services
        get-status](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#cat_status){.MCXref
        .xref}
-   tsm maintenance preflight-check
    -   [tsm maintenance preflight-check
        permissions](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#tsmmaintenance_preflight_perms){.MCXref
        .xref}
    -   [tsm maintenance preflight-check
        ports](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#tsmmaintenance_preflight_ports){.MCXref
        .xref}
-   [tsm maintenance
    reindex-search](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#tsmmaintenancereindex){.MCXref
    .xref}
-   [tsm maintenance
    reset-searchserver](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#tsm_maint_reset_searchsvr){.MCXref
    .xref}
-   [tsm maintenance
    restore](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#tsm3){.MCXref
    .xref}
-   [tsm maintenance
    send-logs](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#tsmSendLogs){.MCXref
    .xref}
-   tsm maintenance snapshot-backup
    -   [tsm maintenance snapshot-backup
        complete](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#tsm_snapshot_backup_complete){.MCXref
        .xref}
    -   [tsm maintenance snapshot-backup
        prepare](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#tsm_snapshot_backup_prepare){.MCXref
        .xref}
    -   [tsm maintenance snapshot-backup
        restore](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#tsm_snapshot_restore){.MCXref
        .xref}
-   [tsm maintenance
    validate-resources](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#tsmValidateResources){.MCXref
    .xref}
-   [tsm maintenance
    ziplogs](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#tsm4ziplogs){.MCXref
    .xref}
:::

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} []{#tsm}tsm maintenance backup
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Creates a backup of the data managed by [Tableau
Server]. This data includes the Tableau
PostgreSQL database (the repository) which contains workbook and user
metadata, and extract (.tde or .hyper) files. This data does not include
configuration data. See [Perform a Full Backup and Restore of Tableau
Server](https://help.tableau.com/current/server/en-us/backup_restore.htm).

**Note:** Do not use this command on Tableau Server installations with
External File Store. See [Backup and Restore with External File
Store](https://help.tableau.com/current/server/en-us/server_external_filestore_storage_backup_restore.htm).

<div>

**Optimizing with topology configurations:**

-   Co-locating File Store on the same node as the Administration
    Controller can reduce the length of time it takes to back up Tableau
    Server by reducing or eliminating the need to transfer data between
    nodes during the backup process. This is especially true if your
    organization uses many extracts.
-   Co-locating the repository (pgsql) with the Administration
    Controller node can also help to reduce back up time, but the time
    savings is less significant than that of the File Store.

The Administration Controller is usually on the initial node, unless you
have had an initial node failure and moved the controller to another
node.

</div>

The backup file is assembled in a temporary location in the data
directory and then written to the directory defined in the
TSM `basefilepath.backuprestore` variable. By default:

`C:\ProgramData\Tableau\Tableau Server\data\tabsvc\files\backups\<filename>.tsbak`

For more information about where backup files are written, and how to
change that location, see [tsm File
Paths](https://help.tableau.com/current/server/en-us/cli_default_filepaths_tsm.htm). **Note:** Even when you change the backup location, the backup
process uses a temporary location in the data directory to assemble the
backup file.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} Synopsis

</div>

`tsm maintenance backup --file <backup_file> [options] [global options]`

<div>

#### Options 

</div>

-d, \--append-date

Optional.

Append the current date to the backup file name.

-f, \--file \<backup\_file\>

Required.

For more information about backing up the repository data, see [Back up
Tableau Server
data](https://help.tableau.com/current/server/en-us/db_backup.htm) for more information.

-i, \--description \<string\>

Optional.

Include the specified description of the backup file.

\--ignore-prompt

Optional. Added in version 2020.2

Back up without prompting, even if the File Store is not on the same
node as the Administration Controller (usually the initial node). Use
this prompt if automating backups (for example, with scripts).

\--skip-compression

Optional.

Create a backup without using compression. This results in a larger
backup file but can reduce the amount of time it takes to complete the
backup. If using this in a multi-node installation, we strongly
recommend you have a File Store instance configured on your initial
node.

-k, \--skip-verification

Optional.

Do not verify the integrity of the database backup.

\--override-disk-space-check

Optional.

Attempt to create a backup even when there is a low disk space warning.

-po, \--pg-only

Optional.

Generates only the repository backup.

\--request-timeout \<timeout in seconds\>

Optional.

Wait the specified amount of time for the command to finish. Default
value is 86400 (1440 minutes).

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} Examples

</div>

This example creates a backup called `ts_backup-<yyyy-mm-dd>.tsbak` in
the \<install dir\>\\ProgramData\\Tableau\\Tableau
Server\\data\\tabsvc\\files\\backups\\ folder:

`tsm maintenance backup -f ts_backup -d`

<div>

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} []{#cleanup}tsm maintenance cleanup
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

By default, deletes log files older than seven days, and temporary
files. Command options can modify which files are deleted.

The impact of this command depends on whether Tableau Server is running.
If the server is running most old files and `http_requests` table
entries can be deleted, but any files in use (locked by the operating
system) cannot be deleted, so temporary files and active log files are
not removed. To delete temporary files and current log files, you must
stop the server before running this command.

If you are running Tableau Server on a distributed deployment, run this
command on the node that is running the Administration Controller (also
referred to as the *TSM Controller*)process. By default, the controller
is on the initial node in the cluster.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} Synopsis {#synopsis1}

</div>

`tsm maintenance cleanup  [options] [global options]`

<div>

#### Options

</div>

-a, \--all

Optional.

Perform all cleanup operations with default retention values. Equivalent
to running the `cleanup` command with the following
options:` -l -t -r -q -ic`.

\--http-requests-table-retention \<\# of days\>

Optional.

Default: 7 days

Specify the number of days of `http_requests` table entries that should
be retained. Use this option with the `-q` option to delete entries
older than the specified number of days are deleted. This option
specifies table entry retention age but does not trigger actual deletion
of table entries. The `-q` option triggers deletion of entries.

-ic, \--sheet-image-cache

Optional.

Clear the image cache. This cache can contain images for offline
previews, snapshots for subscription email messages, and subscription
pdfs, as well as any images requested from the publish rest API endpoint
(see [rest\_api\_ref.htm[(Link opens in a new
window)]{.sr-only}](https://help.tableau.com/current/api/rest_api/en-us/REST/rest_api_ref.htm#query_view_image)
for more information).

**Note:** Option added in version 2019.4

-l, \--log-files

Optional.

Delete log files that are older than the `retention-period`. Files in
the subdirectories under
`data\tabsvc\logs`{mc-conditions="Product.serverwindows"} will be
deleted.

\--log-files-retention \<\# of days\>

Optional.

Default: 1 (24 hours)

Delete logs older than this number of days. This command does not apply
to temporary files.

-q, \--http-requests-table

Optional.

Delete old `http_requests` table entries. Tableau Server must be running
for table entries to be deleted. This option is ignored if Tableau
Server is stopped. This option can be used alone to specify deletion of
entries older than the default retention period (7 days), or together
with the `--http-requests-table-retention` to specify a non-default
retention period.

**Note:** Deleting `http_requests` table entries permanently removes
data that is available to custom administrative views. Be sure removing
this data will not impact any custom views you need.

-r, \--redis-cache

Optional.

Clear the Redis cache.

\--request-timeout \<timeout in seconds\>

Optional.

Wait the specified amount of time for the command to finish.

-t, \--temp-files

Optional.

Delete all files and subdirectories in the following directories:

-   `<install dir>\ProgramData\Tableau\Tableau Server\data\tabsvc\temp`: Only
    directories that are storing files for expired (not running)
    sessions are deleted.

-   `<install dir>\ProgramData\Tableau\Tableau Server\data\tabsvc\httpd\temp`

-   `<install dir>\ProgramData\Tableau\Tableau Server\temp`

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} Examples {#examples1}

</div>

This example cleans up all log files older than 2 days old:

`tsm maintenance cleanup -l --log-files-retention 2`

</div>

<div>

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} []{#cat_disable}tsm maintenance metadata-services disable {#tsm-maintenance-metadataservices-disable}
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

**Note:** Command added in version 2019.3.

Use the `tsm maintenance metadata-services disable` command to disable
the Tableau Metadata API.

Disabling the Metadata API stops continuous ingestion and indexing of
information about the content on Tableau Server, deletes the index of
information about the content published to Tableau Server and assets
associated with that content, and disables the ability to both query the
Metadata API and access [Tableau Catalog]{.VariablesDM_catalog}.

Running this command stops and starts some services used by [Tableau
Server], which causes certain functionality, such
as Recommendations, to be temporarily unavailable to your users.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} Synopsis {#synopsis2}

</div>

``` {space="preserve"}
                        tsm maintenance metadata-services disable
                    
```

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} Option

</div>

\--ignore-prompt

Optional.

Dismiss the confirmation prompt when disabling the Metadata API.

</div>

<div>

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} []{#cat_enable}tsm maintenance metadata-services enable {#tsm-maintenance-metadataservices-enable}
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

**Note:** Command added in version 2019.3.

Use the `tsm maintenance metadata-services enable` command to enable the
Tableau Metadata API for Tableau Server.

If Tableau Server is licensed with the [Data Management
Add-on]{.VariablesDM_sku}, enabling the Metadata API enables Tableau
Catalog.

When enabling the Metadata API, information about the content on
[Tableau Server] is ingested and then indexed to
the Metadata API Store. The Metadata API can be used to query schema,
lineage, and user managed metadata about the content published to
[Tableau Server]. After the Metadata API is
enabled, metadata is continuously ingested and indexed until the
Metadata API is disabled.

When running this command, keep the following in mind:

-   This command stops and starts some services used by [Tableau
    Server], which causes certain functionality,
    such as Recommendations, to be temporarily unavailable to your
    users.
-   A new index of metadata is created and replaces the previous index
    every time this command is used.

For more information about the [Tableau Catalog]{.VariablesDM_catalog},
see, [About Tableau
Catalog](https://help.tableau.com/current/server/en-us/dm_catalog_overview.htm).

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} Synopsis {#synopsis3}

</div>

                            tsm maintenance metadata-services enable
                        

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} Option {#option1}

</div>

\--ignore-prompt

Optional.

Dismiss the confirmation prompt when enabling the Metadata API.

</div>

<div>

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} []{#cat_status}tsm maintenance metadata-services get-status {#tsm-maintenance-metadataservices-getstatus}
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

**Note:** Command added in version 2019.3.

Use the `tsm maintenance metadata-services get-status` command to get
status information on Metadata Services.

Status on Metadata Services indicates if the Metadata API Store has been
initialized or if the Tableau Metadata API is running or not.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} Synopsis {#synopsis4}

</div>

``` {space="preserve"}
                        tsm maintenance metadata-services get-status
                    
```

</div>

::: {mc-conditions="Product.serverwindows"}
<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} []{#tsmmaintenance_preflight_perms}tsm maintenance preflight-check permissions {#tsm-maintenance-preflightcheck-permissions}
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

**Note:** Command added for Tableau Server on Windows in version 2020.3.

Use the `tsm maintenance preflight-check permissions` command to verify
the directory permissions.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} Synopsis {#synopsis5}

</div>

`tsm maintenance preflight-check permissions [options] [global options]`

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} Option {#option2}

</div>

-d, \--data-dir \<data directory\>

Optional.

Specifies the data directory on which to verify permissions. If not
included, the data directory is determined based on the current Tableau
Server configuration.

-i, \--install-dir \<install directory\>

Optional.

Specifies the install directory on which to verify permissions. If not
included, the install directory is determined based on the current
Tableau Server configuration.

-n \--nodes \<nodeID,nodeID,\...\>

Optional.

Node IDs of nodes to specifically include in the permissions check. If
not specified, the check is performed on all nodes in the cluster.

\--request-timeout \<timeout in seconds\>

Optional.

Wait the specified amount of time for the command to finish.

-ru \--runas-user \<timeout in seconds\>

Optional.

The Run As user name to verify permissions for. If not provided, the Run
As user is determined from the current configuration.
:::

::: {mc-conditions="Product.serverwindows"}
<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} []{#tsmmaintenance_preflight_ports}tsm maintenance preflight-check ports {#tsm-maintenance-preflightcheck-ports}
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

**Note:** Command added for Tableau Server on Windows in version 2020.3.

Use the `tsm maintenance preflight-check ports` command to verify that
ports are available for all currently installed services. Specify a
service and port to verify the port is available for that service, even
if the service is not currently installed.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} Synopsis {#synopsis6}

</div>

`tsm maintenance preflight-check ports [options] [global options]`

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} Option {#option3}

</div>

-a, \--tabadminagent-addresses \<hostname:port\>

Optional.

Specifies the host and port on which to check for access to the
Administration Agent. Addresses are formatted as `hostname:port`.
Separate multiple addresses by commas if more than one is being checked.
Use this option to see if a port is available before installing or
changing ports.

-g, \--gateway-addresses \<hostname:port\>

Optional.

Specifies the host and port on which to check for access for the Gateway
service. Addresses are formatted as `hostname:port`. Separate multiple
addresses by commas if more than one is being checked. Use this option
to see if a port is available before installing or changing ports.

-n \--nodes \<nodeID,nodeID,\...\>

Optional.

Node IDs of nodes to run preflight check on. If not specified, the
checks are performed on all nodes in the cluster.

-r, \--repository-addresses \<hostname:port\>

Optional.

Specifies the host and port on which to check for access for the
Repository service. Addresses are formatted as `hostname:port`. Separate
multiple addresses by commas if more than one is being checked. Use this
option to see if a port is available before installing or changing
ports.

-re \--remote

Optional.

Checks remote access to the Administration Agent from all nodes. This is
not done by default.

\--request-timeout \<timeout in seconds\>

Optional.

Wait the specified amount of time for the command to finish.

-t, \--tabadmincontroller-addresses \<hostname:port\>

Optional.

Specifies the host and port on which to check for access for the
Administration Controller. Addresses are formatted as `hostname:port`.
Separate multiple addresses by commas if more than one is being checked.
Use this option to see if a port is available before installing or
changing ports.
:::

<div>

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} []{#tsmmaintenancereindex}tsm maintenance reindex-search {#tsm-maintenance-reindexsearch}
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Use the `tsm maintenance reindex-search` command to rebuild the search
index.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} Synopsis {#synopsis7}

</div>

`tsm maintenance reindex-search  [options] [global options]`

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} Option {#option4}

</div>

\--request-timeout \<timeout in seconds\>

Optional.

Wait the specified amount of time for the command to finish.

</div>

<div>

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} []{#tsm_maint_reset_searchsvr}tsm maintenance reset-searchserver {#tsm-maintenance-resetsearchserver}
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Resets the search server to a clean state, deleting search information
and rebuilding the search index.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} Synopsis {#synopsis8}

</div>

`tsm maintenance reset-searchserver  [options]  [global options]`

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} Option {#option5}

</div>

\--request-timeout \<timeout in seconds\>

Optional.

Wait the specified amount of time for the command to finish.

</div>

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} []{#tsm3}tsm maintenance restore
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Restore [Tableau Server] using the specified
backup file. Restoring a backup file does not restore any configuration
data. See [Perform a Full Backup and Restore of Tableau
Server](https://help.tableau.com/current/server/en-us/backup_restore.htm).

You can only restore from a backup that has the same type of identity
store as the running server. For example, a backup from a server using
local authentication can be restored to a Tableau Server initialized
with local authentication, but a backup from a server using Active
Directory authentication cannot be restored to a server initialized with
local authentication.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} Synopsis {#synopsis9}

</div>

`tsm maintenance restore --file <file_name> [--restart-server] [global options]`

<div>

#### Options

</div>

-ak, \--asset-key-file \<file\_name\>

Optional. Specify this option only if you are restoring from assets that
were created by tabadmin on Tableau Server (versions 2018.1 and
earlier).

Name of asset key file to restore from. The asset key file is created by
the [`tabadmin assetkeys` command[(Link opens in a new
window)]{.sr-only}](https://help.tableau.com/v10.5/server/en-us/tabadmin_cmd.htm#assetkey).
The file must be in the predefined backup/restore location on the
server.

-f, \--file \<file\_name\>

Required.

Specifies the backup file to restore from.

The `restore `command expects a backup file in the directory defined in
the TSM `basefilepath.backuprestore` variable. By default:

`C:\ProgramData\Tableau\Tableau Server\data\tabsvc\files\backups\`

For more information about file paths and how to change them, see [tsm
File
Paths](https://help.tableau.com/current/server/en-us/cli_default_filepaths_tsm.htm).

-k, \--skip-identity-store-verification

Optional. Specify this option only if you are restoring from a backup
file that was created by tabadmin on Tableau Server (versions 2018.1 and
earlier).

Do not use this key in an attempt to change identity store type from
Tableau Server that created original backup file. To change the identity
store, see [Changing the Identity
Store](https://help.tableau.com/current/server/en-us/reconfig_change_auth.htm) .

-po, \--pg-only

Optional.

Restores only the repository.

-r, \--restart-server

Optional.

Restart the server after the restore.

\--request-timeout \<timeout in seconds\>

Optional.

Wait the specified amount of time for the command to finish.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} []{#tsmSendLogs}tsm maintenance send-logs {#tsm-maintenance-sendlogs}
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Upload the specified file to Tableau and associate it with a support
case. To successfully upload files to Tableau, your Tableau Server must
be able to communicate with the send-logs server at
`https://report-issue.tableau.com`.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} Synopsis {#synopsis10}

</div>

`tsm maintenance send-logs --case <case_number> --email <contact_email> --file <path/to/file> [global options]`

<div>

#### Options

</div>

-c,\--case \<case\_number\>

Required.

Support case number.

-e,\--email \<contact\_email\>

Required.

Contact email.

-f, \--file \<path/to/file\>

Required.

Specifies the location and name of the log file archive to send.

\--request-timeout \<timeout in seconds\>

Optional.

Wait the specified amount of time for the command to finish.

<div>

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} []{#tsm_snapshot_backup_complete}tsm maintenance snapshot-backup complete {#tsm-maintenance-snapshotbackup-complete}
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

**Note:** Command added in version 2020.1 and only available when
Tableau Server is configured for External File Store.

Complete the snapshot backup process on Tableau Server. Run this after
you have taken a snapshot backup of your external storage.

The *tsm maintenance snapshot-backup prepare* and the *tsm maintenace
snapshot-backup complete* commands are used to create a backup of
Tableau Server data for Tableau Server installations that are configured
with External File Store. For more information, see [Backup and Restore
with External File
Store](https://help.tableau.com/current/server/en-us/server_external_filestore_storage_backup_restore.htm)

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} Synopsis {#synopsis11}

</div>

`tsm maintenance snapshot-backup complete [options] [global options]`

<div>

#### Options

</div>

\--request-timeout \<timeout in seconds\>

Optional.

Wait the specified amount of time for the command to finish.

</div>

<div>

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} []{#tsm_snapshot_backup_prepare}tsm maintenance snapshot-backup prepare {#tsm-maintenance-snapshotbackup-prepare}
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

**Note:** Command added in version 2020.1 and only available when
Tableau Server is configured for External File Store.

Prepares for snapshot backup. Once the preparation step is complete, you
may take a snapshot backup of your network storage.

The *tsm maintenance snapshot-backup prepare* and the *tsm maintenace
snapshot-backup complete* commands are used to create a backup of
Tableau Server data for Tableau Server installations that are configured
with External File Store. For more information, see [Backup and Restore
with External File
Store](https://help.tableau.com/current/server/en-us/server_external_filestore_storage_backup_restore.htm)

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} Synopsis {#synopsis12}

</div>

`tsm maintenance snapshot-backup prepare [options] [global options]`

<div>

#### Options

</div>

\--request-timeout \<timeout in seconds\>

Optional.

Wait the specified amount of time for the command to finish.

</div>

<div>

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} []{#tsm_snapshot_restore}tsm maintenance snapshot-backup restore {#tsm-maintenance-snapshotbackup-restore}
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

**Note:** Command added in version 2020.1 and only available when
Tableau Server is configured for External File Store.

Restores the repository backup from the storage snapshot to Tableau
Server.

For more information, see [Backup and Restore with External File
Store](https://help.tableau.com/current/server/en-us/server_external_filestore_storage_backup_restore.htm).

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} Synopsis {#synopsis13}

</div>

`tsm maintenance snapshot-backup restore [options] [global options]`

<div>

#### Options

</div>

\--request-timeout \<timeout in seconds\>

Optional.

Wait the specified amount of time for the command to finish.

</div>

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} []{#tsmValidateResources}tsm maintenance validate-resources {#tsm-maintenance-validateresources}
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Validate workbooks and data sources for a site. Use this command before
migrating a site, to detect issues with site resources such as workbooks
and data sources that will cause a site import to fail. Some resource
problems can be corrected by republishing from local sources. Other
problems might require assistance from Tableau Support.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} Synopsis {#synopsis14}

</div>

`tsm maintenance validate-resources --site-id <site ID> [global options]`

#### Options

-id,\--site-id \<site ID\>

Required.

ID for the site whose resources you are validating.

-r,\--repair

Optional.

Attempt to repair invalid resources. Those that cannot be repaired are
noted in output.

\--request-timeout \<timeout in seconds\>

Optional.

Wait the specified amount of time for the command to finish.

 

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} []{#tsm4ziplogs}tsm maintenance ziplogs
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Use the `ziplogs `command to create an archive of [Tableau
Server] log files.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} Synopsis {#synopsis15}

</div>

`tsm maintenance ziplogs [options] [global options]`

<div>

#### Options

</div>

-a, \--all

Optional.

Includes msinfo, netstat, and latest dump. Equivalent of running the
command with these options: `-mi -t -l`. Does not include PostgreSQL
data.

-d, \--with-postgresql-data

Optional.

Include the PostgreSQL data folder if [Tableau
Server] is stopped or PostgreSQL dump files if
[Tableau Server] is running.

\--description \<string\>

Optional.

Include the specified description of the archive file.

<div>

\--enddate \<mm/dd/yyyy\>

Optional.

The last date of log files to be included. This option must be used with
`--startdate` and cannot be used with `--minimumdate`. If this option is
not specified, up to two days of logs will be included.

Added in version 2019.3

</div>

-f, \--file \<name\>

Optional.

Specify a name for the zipped archive file. If no name is provided the
archive is created as logs.zip. The file is written to the directory
defined in the TSM `basefilepath.log_archive` variable. By default:

`C:\ProgramData\Tableau\Tableau Server\data\tabsvc\files\log-archives\`

For more information about file paths and how to change them, see [tsm
File
Paths](https://help.tableau.com/current/server/en-us/cli_default_filepaths_tsm.htm).

-i, \--description \<string\>

Optional.

Include the specified description of the archive file.

-mi, \--with-msinfo

Optional.

Include the msinfo32 report, with system information about OS, hardware,
and running software.

-l, \--with-latest-dump

Optional.

When any service crashes, Tableau Server generates a dumpfile. Set this
option to include the most recent service crash dumpfile.If you do not
set this option, then no dumpfile will be included in the resulting
ziplog.

-m, \--minimumdate \<mm/dd/yyyy\>

Optional.

Earliest date of log files to be included. If not specified, a maximum
of two days of log files are included. Format of date should be
\"`mm/dd/yyyy`\". This option cannot be used with `--startdate` and
`--enddate`.

-o, \--overwrite

Optional.

For an overwrite of an existing ziplog file. If a file by the same name
already exists and this option is not used, the ziplogs command will
fail.

By default the file is written to:

`C:\ProgramData\Tableau\Tableau Server\data\tabsvc\files\log-archives\`

For more information about file paths and how to change them, see [tsm
File
Paths](https://help.tableau.com/current/server/en-us/cli_default_filepaths_tsm.htm).

<div>

\--startdate \<mm/dd/yyyy\>

Optional.

The earliest date of log files to be included. This option must be used
with `--enddate` and cannot be used with `--minimumdate`. If this option
is not specified, up to two days of logs will be included.

Added in version 2019.3

</div>

\--request-timeout \<timeout in seconds\>

Optional.

Wait the specified amount of time for the command to finish. Default
value is 7200 (120 minutes).

-t, \--with-netstat-info

Optional.

Include netstat information.

 

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_maintenance_tsm.htm#){.heading-item__link .print-hidden} Global options
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
TSM clients](https://help.tableau.com/current/server/en-us/tsm_overview.htm#Connecti).

-u, \--username \<user\>

Required if no session is active, along with `-p` or `--password`.

Specify a user account. If you do not include this option, the command
is run using credentials you signed in with.

 