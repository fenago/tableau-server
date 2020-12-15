

tsm sites
=========
You can use the `tsm sites` commands to export an existing site for
import to a new site (also referred to as site migration), and to import
the new site. An `unlock `command is available in case an error leaves a
site locked.

The `tsm sites` commands will use your local file store to hold the
export and import data. If you are running a multinode Tableau cluster,
then you must run the `tsm sites` commands on a Tableau Server that is
running the Data Engine process. For information about the Data Engine
process and the processes that require it, see [Tableau Server
Processes](https://help.tableau.com/current/server/en-us/processes.htm).

For comprehensive steps for migrating a site, see [Export or Import a
Site](https://help.tableau.com/current/server/en-us/sites_exportimport.htm).


-   [tsm sites
    export](https://help.tableau.com/current/server/en-us/cli_sites_tsm.htm#TSMExport){.MCXref
    .xref}
-   [tsm sites
    import](https://help.tableau.com/current/server/en-us/cli_sites_tsm.htm#TSMImport){.MCXref
    .xref}
-   [tsm sites
    import-verified](https://help.tableau.com/current/server/en-us/cli_sites_tsm.htm#TSMImportVerified){.MCXref
    .xref}
-   [tsm sites
    unlock](https://help.tableau.com/current/server/en-us/cli_sites_tsm.htm#TSMUnlock){.MCXref
    .xref}
:::

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_sites_tsm.htm#){.heading-item__link .print-hidden} []{#TSMExport}tsm sites export
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Export a specified Tableau Server site to a .zip file. You can export a
site to archive its settings at a specific point in time, or to complete
the first step of a site migration process.

**Note**: The `tsm sites import` and `tsm sites export` commands can
leave a site in a locked state if an error occurs. To unlock a site, use
the `tsm sites unlock` command.

<div>

#### Synopsis

</div>

`tsm sites export --site-id <source-siteID> --file <export-file> [options] [global options]`

<div>

#### Options

</div>

-f,\--file \<export-file\>

Required.

Specify the name of the file to which [Tableau
Server] saves all of the site's information.

This file is generated to the directory defined in the TSM
`basefilepath.site_export.exports` variable. By default:

`C:\ProgramData\Tableau\Tableau Server\data\tabsvc\files\siteexports`

For more information about file paths and how to change them, see [tsm
File
Paths](https://help.tableau.com/current/server/en-us/cli_default_filepaths_tsm.htm).

-id,\--site-id \<source-siteID\>

Required.

The site ID for the site you are exporting. You can get the site ID from
the URL when you\'re signed in to the site from a web browser. For
information about locating the site ID, see [Prepare the Source and
Target
Sites](https://help.tableau.com/current/server/en-us/sites_exportimport.htm#before-you-export).

-ow,\--overwrite

Optional.

Overwrite an export file of the same name that already exists.

\--request-timeout \<timeout in seconds\>

Optional.

Wait the specified amount of time for the command to finish. Default
value is 43200 (720 minutes).

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_sites_tsm.htm#){.heading-item__link .print-hidden} []{#TSMImport}tsm sites import
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

This command uses the .zip file you created using `tsm sites export` to
generate a set of .csv files that show how the exported source site
settings will map to the new target site.

By default, the .zip file is generated and saved to the `siteexports`
directory at:

`C:\ProgramData\Tableau\Tableau Server\data\tabsvc\files\siteexports`

Before you use this command, you must copy the .zip file to the
directory in which Tableau will expect it. This location is defined in
the TSM `basefilepath.site_import.exports` variable. By default, the
import directory is:

`C:\ProgramData\Tableau\Tableau Server\data\tabsvc\files\siteimports`

For more information about file paths and how to change them, see [tsm
File
Paths](https://help.tableau.com/current/server/en-us/cli_default_filepaths_tsm.htm).

**Note**: The `tsm sites import` and `tsm sites export` commands can
leave a site in a locked state if an error occurs. To unlock a site, use
the `tsm sites unlock` command.

<div>

#### Synopsis {#synopsis1}

</div>

`tsm sites import --file <export-file.zip> --site-id <target-siteID> [options] [global options]`

<div>

#### Options

</div>

-f,\--file \<export-file.zip\>

Required.

Name of the .zip file created by the `tsm sites export` process, and
which you must copy to the import directory. By default:

`C:\ProgramData\Tableau\Tableau Server\data\tabsvc\files\siteimports`

-id,\--site-id \<target-siteID\>

Required.

The site ID for the new site you are importing to (the target site). For
information about locating the site ID, see [Prepare the Source and
Target
Sites](https://help.tableau.com/current/server/en-us/sites_exportimport.htm#before-you-export).

-c,\--continue-on-ignorable-errors

Optional.

Continue site import if errors occur which can be ignored. These errors
can indicate issues with the import of a specific workbook or data
source.

-k,\--no-verify

Optional.

Skip verification of mapping files.

-m, \--override-schedule-mapper \<mapping-file.csv\>

Optional.

Schedule mapping file to override the normal mapping by name.

\--request-timeout \<timeout in seconds\>

Optional.

Wait the specified amount of time for the command to finish. Default
value is 7200 (120 minutes).

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_sites_tsm.htm#){.heading-item__link .print-hidden} []{#TSMImportVerified}tsm sites import-verified {#tsm-sites-importverified}
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Specify the directory that contains an exported site's .csv mapping
files, to import to a new site. This is the final step of a site
migration process.

<div>

#### Synopsis {#synopsis2}

</div>

`tsm sites import-verified --import-job-dir <importjob-directory> --site-id <target-siteID> [options] [global options]`

<div>

#### Options

</div>

-id,\--site-id \<target-siteID\>

Required.

The site ID for the new site you are importing to (the target site). For
information about locating the site ID, see [Prepare the Source and
Target
Sites](https://help.tableau.com/current/server/en-us/sites_exportimport.htm#before-you-export).

-w, \--import-job-dir \<importjob-directory\>

Required.

The parent of the `mappings` directory that contains the .csv files from
the exported (source) site. The name of this parent directory includes
the import id and date and time. For example:

`C:\ProgramData\Tableau\Tableau Server\data\tabsvc\files\siteimports\working\import_ff00_20180102022014457`

\--request-timeout \<timeout in seconds\>

Optional.

Wait the specified amount of time for the command to finish. Default
value is 7200 (120 minutes).

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_sites_tsm.htm#){.heading-item__link .print-hidden} []{#TSMUnlock}tsm sites unlock
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Use this command to unlock a site.

<div>

#### Options

</div>

-id,\--site-id \<target-siteID\>

Required.

The site ID for the site you are unlocking. For information about
locating the site ID, see [Prepare the Source and Target
Sites](https://help.tableau.com/current/server/en-us/sites_exportimport.htm#before-you-export).

-d, \--desired-state \<state to leave unlocked site in\>

Optional.

The state the site should be left in after it is unlocked. Options are
\"active\" and \"suspended\". The default is \"active\" if not
specified.

For example:

`tsm sites unlock -id mysite -d suspended`

\--request-timeout \<timeout in seconds\>

Optional.

Wait the specified amount of time for the command to finish. Default
value is 300 (5 minutes).

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_sites_tsm.htm#){.heading-item__link .print-hidden} Global options
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
TSM clients](https://help.tableau.com/current/server/en-us/tsm_overview.htm#Connecti).

-u, \--username \<user\>

Required if no session is active, along with `-p` or `--password`.

Specify a user account. If you do not include this option, the command
is run using credentials you signed in with.
