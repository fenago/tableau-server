

tsm File Paths
==============
Certain tsm commands read files from or write files to default
locations. These default locations are determined by `basefilepath`
variables defined for each command. You can use tsm to view the current
value of the variables, and to change the locations.

::: {mc-conditions="Product.serverwindows"}
### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_default_filepaths_tsm.htm#){.heading-item__link .print-hidden} NetworkService system account
:::

In some organizations, security policies are implemented that restrict
file access from system accounts, such as the NetworkService account. If
you change tsm file paths, then you should verify that the
NetworkService system account has full permission (with permissions
inheritance enabled) to the resulting path. In addition, if you change a
file path that was originally in the `*\data\tabsvc\*` path, you must
maintain the NetworkService permissions to the original path. This
permission must be maintained because the NetworkService system account
handles operations by Tableau Server Administration Controller, Tableau
Server Client File Service, and Tableau Server Coordination Service.

<div>

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_default_filepaths_tsm.htm#){.heading-item__link .print-hidden} Default locations for files
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

During the `tsm maintenance backup`, `restore`, `send-logs`, and
`ziplogs `processes, and the `tsm sites export` and
`sites import `processes, [Tableau Server] uses
default locations for the files created or used by these commands.

For details on disk space requirements for backing up Tableau Server,
see [Disk Space Usage for
Backup](https://help.tableau.com/current/server/en-us/db_backup.htm#BackupDiskSpaceReqs).

By default:

-   tsm maintenance commands:

    -   backup---The backup` .tsbak` file is created in a temporary
        location in the data directory on the initial node and then
        saved in:

        ::: {mc-conditions="Product.serverwindows"}
        `<install drive>:<install\path>\data\tabsvc\files\backups`

        By default this is:

        `C:\ProgramData\Tableau\Tableau Server\data\tabsvc\files\backups`

        But if you installed Tableau to a non-default location this will
        be different. For example, if you installed to
        `D:\Tableau Server` the backup will be saved in:

        `D:\Tableau Server\data\tabsvc\files\backups`

        **Note:** The tsm maintenance backup command does not support
        Microsoft Windows UNC (Univeral Naming Convention) file paths,
        also known as \"network paths\" ( \\\\\<computer
        name\>\\\<folder\>\\\<file name\>) as the path to the location
        where backup files are written. Instead, use local file system
        paths (\<drive letter\>:\\\<folder name\\\<file name\>).
        :::

    -   restore---The restore process restores a backup file from:

        ::: {mc-conditions="Product.serverwindows"}
        `<install drive>:<install\path>\data\tabsvc\files\backups`

        By default this is:

        `C:\ProgramData\Tableau\Tableau Server\data\tabsvc\files\backups`

        But if you installed Tableau to a non-default location this will
        be different. For example, if you installed to
        `D:\Tableau Server` the restore process will use a backup in:

        `D:\Tableau Server\data\tabsvc\files\backups`
        :::

    -   send-logs---The send-logs sends the logs file from:

        ::: {mc-conditions="Product.serverwindows"}
        `<install drive>:<install\path>\data\tabsvc\files\backups`

        By default this is:

        `C:\ProgramData\Tableau\Tableau Server\data\tabsvc\files\backups`

        But if you installed Tableau to a non-default location this will
        be different. For example, if you installed to
        `D:\Tableau Server` the send-logs process will sent log files
        from:

        `D:\Tableau Server\data\tabsvc\files\backups`
        :::

    -   ziplogs---The ziplogs file is generated in:

        ::: {mc-conditions="Product.serverwindows"}
        `<install drive>:<install\path>\data\tabsvc\files\log-archives`

        By default this is:

        `C:\ProgramData\Tableau\Tableau Server\data\tabsvc\files\log-archives`

        But if you installed Tableau to a non-default location this will
        be different. For example, if you installed to
        `D:\Tableau Server` the ziplogs file is generated in:

        `D:\Tableau Server\data\tabsvc\files\log-archives`
        :::

-   tsm sites

    -   export---The export .zip file is generated to the following
        directory:

        ::: {mc-conditions="Product.serverwindows"}
        `<install drive>:<install\path>\data\tabsvc\files\siteexports`

        By default this is:

        `C:\ProgramData\Tableau\Tableau Server\data\tabsvc\files\siteexports`

        But if you installed Tableau to a non-default location this will
        be different. For example, if you installed to
        `D:\Tableau Server` the export .zip file is generated in:

        `D:\Tableau Server\data\tabsvc\files\siteexports`
        :::

    -   import---During the import process, Tableau Server looks for
        files in:

        ::: {mc-conditions="Product.serverwindows"}
        `<install drive>:<install\path>\data\tabsvc\files\siteimports`

        By default this is:

        `C:\ProgramData\Tableau\Tableau Server\data\tabsvc\files\siteimports`

        But if you installed Tableau to a non-default location this will
        be different. For example, if you installed to
        `D:\Tableau Server` the import process looks for files in:

        `D:\Tableau Server\data\tabsvc\files\siteimports`
        :::

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_default_filepaths_tsm.htm#){.heading-item__link .print-hidden} Get the current file location
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

You can see the current file location for a specific command using
`tsm configuration get`:

-   For tsm maintenance commands:

    -   backup, restore, and send-logs:

        `tsm configuration get -k basefilepath.backuprestore`

    -   ziplogs:

        `tsm configuration get -k basefilepath.log_archive`

-   For tsm sites commands:

    -   export

        `tsm configuration get -k basefilepath.site_export.exports`

    -   import

        `tsm configuration get -k basefilepath.site_import.exports`

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_default_filepaths_tsm.htm#){.heading-item__link .print-hidden} Change the current file location
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

You can change the expected file locations using the
`tsm configuration set` command to update the `basefilepath` variables.
For details about specific base file paths, see [tsm configuration set
Options](https://help.tableau.com/current/server/en-us/cli_configuration-set_tsm.htm).

Changing a `basefilepath `variable does not move existing files from the
original directory to the new directory. If you want existing backup,
restore, log files, or site export or import files to reside in the new
directory you specify, you must move them manually. You are responsible
for creating the new location and for setting the correct permissions to
allow tsm access to any files that will be placed there, and to the
directory structure containing those files.

The `tsm maintenance backup` command assembles the backup in a temporary
location in the data directory before saving the backup file to the
location specified by the` basefilepath.backuprestore` variable.
Changing the basefilepath does not impact where the
`tsm maintenance backup` command assembles the backup file.

-   For tsm maintenance commands:

    -   To change the backup, restore, or send-logs directory, run the
        following command:

        `tsm configuration set -k basefilepath.backuprestore -v "<drive>:\new\directory\path"`

    -   To change the ziplogs directory:

        `tsm configuration set -k basefilepath.log_archive -v "<drive>:\new\directory\path"`

-   For tsm sites commands:

    -   To change the sites export directory:

        `tsm configuration set -k basefilepath.site_export.exports -v "<drive>:\new\directory\path"`

    -   To change the sites import directory:

        `tsm configuration set -k basefilepath.site_import.exports -v "<drive>:\new\directory\path"`

After you change a default file location you need to do the following:

1.  Apply pending changes:

    `tsm pending-changes apply`

    If the pending changes require a server restart, the
    `pending-changes apply` command will display a prompt to let you
    know a restart will occur. This prompt displays even if the server
    is stopped, but in that case there is no restart. You can suppress
    the prompt using the `--ignore-prompt` option, but this does not
    change the restart behavior. If the changes do not require a
    restart, the changes are applied without a prompt. For more
    information, see [tsm pending-changes
    apply](https://help.tableau.com/current/server/en-us/cli_pending-changes.htm#pending-changes-apply)

2.  Stop Tableau Server:

    `tsm stop`

3.  Restart the TSM Controller:

    `net stop tabadmincontroller_0`

    `net start tabadmincontroller_0`

4.  Wait several minutes for the controller to restart. You can confirm
    the controller has restarted with this command:

    `tsm status -v`

    When you can run that command and the Tableau Server Administration
    Controller is listed as \'running\' the controller has restarted.

5.  Start Tableau Server:

    `tsm start`

