

Migrate from Tabadmin to the TSM CLI
====================================
The Tableau Services Manager (TSM) command-line interface (CLI) replaces
the tabadmin CLI in Tableau Server on Linux, and in Tableau Server on
Windows version 2018.2. This page maps tabadmin commands to TSM commands
to help you to migrate to the TSM CLI.

To learn more about the TSM CLI, see [tsm Command Line
Reference](https://help.tableau.com/current/server/en-us/tsm.htm).

**Note:** TSM is a batch file. To run tsm commands in another batch
file, use the `call `command. For example
\"`call tsm maintenance ziplogs`\". Doing this will return control to
the batch file. You also need to authenticate to TSM before issuing any
commands. For more information, see [Authenticating with tsm
CLI](https://help.tableau.com/current/server/en-us/tsm.htm#Authenti).

To learn more about the differences between tabadmin and TSM , see
[Comparing Functionality of tabadmin and
TSM](https://help.tableau.com/current/server/en-us/tabadmin-to-tsm.htm).

Looking for tabadmin commands for [Tableau
Server] on Windows version 2018.1 and earlier?
See [tabadmin Commands[(Link opens in a new
window)]{.sr-only}](https://help.tableau.com/current/server/en-us/tabadmin_cmd.htm "Opens topic in a new browser tab").

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/tabadmin_to_tsm_cli.htm#){.heading-item__link .print-hidden} Tabadmin commands with a corresponding TSM CLI command
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

The following table shows which tabadmin commands correspond to commands
available in the TSM CLI.

+-------------+---------------------------+---------------------------+
| Command     | Tabadmin Command(s)       | Comparable TSM CLI        |
| Description |                           | Command                   |
+=============+===========================+===========================+
| Activate a  | `taba                     | `tsm licenses activate`   |
| license     | dmin activate --activate` |                           |
+-------------+---------------------------+---------------------------+
| Deactivate  | `ta                       | `tsm licenses deactivate` |
| licenses    | badmin activate --return` |                           |
+-------------+---------------------------+---------------------------+
| Activate a  | `t                        | `tsm l                    |
| trial       | abadmin activate --trial` | icenses activate --trial` |
| license     |                           |                           |
+-------------+---------------------------+---------------------------+
| Create a    | `tabadmin backup`         | `tsm maintenance backup`  |
| backup of   |                           |                           |
| the data    |                           | A backup created using    |
| managed by  |                           | TSM does not include any  |
| Tableau     |                           | server configuration      |
| Server      |                           | data. There is no option  |
|             |                           | to include server         |
|             |                           | configuration data.       |
+-------------+---------------------------+---------------------------+
| Clear the   | `tabadmin clearcache`     | ` ts                      |
| server      |                           | m maintenance cleanup -r` |
| cache       |                           |                           |
+-------------+---------------------------+---------------------------+
| Clean up    | `tabadmin cleanup`        | `                         |
| temporary   |                           | tsm maintenance cleanup`\ |
| files and   |                           |                           |
| old log     |                           |                           |
| files       |                           |                           |
+-------------+---------------------------+---------------------------+
| Update the  | `tabadmin configure`      | `t                        |
| server      |                           | sm pending-changes apply` |
| co          |                           |                           |
| nfiguration |                           |                           |
| with any    |                           |                           |
| changes     |                           |                           |
| you\'ve     |                           |                           |
| made        |                           |                           |
+-------------+---------------------------+---------------------------+
| Customize   | `tabadmin customize`      | `tsm customize`           |
| the server  |                           |                           |
| name and    |                           |                           |
| logos       |                           |                           |
+-------------+---------------------------+---------------------------+
| Enable      | `tabadmin dbpass`         | `tsm data-access          |
| access to   |                           | repository-access enable` |
| the         |                           |                           |
| repository  |                           |                           |
+-------------+---------------------------+---------------------------+
| Disable     | `t                        | `tsm data-access r        |
| access to   | abadmin dbpass --disable` | epository-access disable` |
| the         |                           |                           |
| repository  |                           |                           |
+-------------+---------------------------+---------------------------+
| Set a file  | `tabadmin decommission`   | `tsm topolog              |
| store       |                           | y filestore decommission` |
| instance to |                           |                           |
| read-only   |                           |                           |
| mode        |                           |                           |
+-------------+---------------------------+---------------------------+
| Delete one  | `tabadmin                 | `tsm data-access we       |
| or more Web |  delete_webdataconnector` | b-data-connectors delete` |
| Data        |                           |                           |
| Connectors  |                           | To learn more, see [Web   |
| (WDCs) from |                           | Data Connectors in        |
| Tableau     |                           | Tableau                   |
| Server      |                           | Server                    |
|             |                           | ](https://help.tableau.co |
|             |                           | m/current/server/en-us/da |
|             |                           | tasource_wdc.htm){.MCXref |
|             |                           | .xref}.                   |
+-------------+---------------------------+---------------------------+
| Add a Web   | `tabadmin                 | `tsm data-access          |
| Data        |  import_webdataconnector` |  web-data-connectors add` |
| Connector   |                           |                           |
| (WDC) to    | and                       | **Note**: TSM does not    |
| Tableau     |                           | support importing WDCs,   |
| Server      | `tabadmin wh              | instead it lets you add   |
|             | itelist_webdataconnector` | WDCs to an allowlist. To  |
|             |                           | learn more, see [Web Data |
|             |                           | Connectors in Tableau     |
|             |                           | Server                    |
|             |                           | ](https://help.tableau.co |
|             |                           | m/current/server/en-us/da |
|             |                           | tasource_wdc.htm){.MCXref |
|             |                           | .xref}.                   |
+-------------+---------------------------+---------------------------+
| List Web    | `tabadmi                  | `tsm data-access          |
| Data        | n list_webdataconnectors` | web-data-connectors list` |
| Connectors  |                           |                           |
| (WDCs) used |                           | To learn more, see [Web   |
| by Tableau  |                           | Data Connectors in        |
| Server      |                           | Tableau                   |
|             |                           | Server                    |
|             |                           | ](https://help.tableau.co |
|             |                           | m/current/server/en-us/da |
|             |                           | tasource_wdc.htm){.MCXref |
|             |                           | .xref}.                   |
+-------------+---------------------------+---------------------------+
| Export a    | `tabadmin exportsite`     | `tsm sites export`        |
| site from   |                           |                           |
| Tableau     |                           |                           |
| Server      |                           |                           |
+-------------+---------------------------+---------------------------+
| Initiate a  | `tab                      | `tsm topo                 |
| repository  | admin failoverrepository` | logy failover-repository` |
| failover    |                           |                           |
+-------------+---------------------------+---------------------------+
| Get a       | `tabadmin get`            | `tsm configuration get`   |
| co          |                           |                           |
| nfiguration |                           |                           |
| option      |                           |                           |
+-------------+---------------------------+---------------------------+
| Get the     | `tabadmin                 | `tsm authentication       |
| OpenID      |  get_openid_redirect_url` |  openid get-redirect-url` |
| redirect    |                           |                           |
| URL         |                           |                           |
+-------------+---------------------------+---------------------------+
| Import site | `tabadmin importsite`     | `tsm sites import`        |
| .csv files  |                           |                           |
| into        |                           |                           |
| Tableau     |                           |                           |
| Server      |                           |                           |
+-------------+---------------------------+---------------------------+
| Import a    | `taba                     | `t                        |
| site into   | dmin importsite_verified` | sm sites import-verified` |
| Tableau     |                           |                           |
| Server      |                           |                           |
| using .csv  |                           |                           |
| files       |                           |                           |
+-------------+---------------------------+---------------------------+
| Display     | `tabadmin licenses`       | `tsm licenses list`       |
| license     |                           |                           |
| information |                           | **Note:** For more        |
| for Tableau |                           | information about the     |
| Server      |                           | output of this command,   |
|             |                           | see [View Server          |
|             |                           | License                   |
|             |                           | s](https://help.tableau.c |
|             |                           | om/current/server/en-us/v |
|             |                           | iew_licenses.htm){.MCXref |
|             |                           | .xref}.                   |
+-------------+---------------------------+---------------------------+
| Move a file | `tabadmin recommission`   | `tsm topolog              |
| store from  |                           | y filestore recommission` |
| read-only   |                           |                           |
| mode to an  |                           |                           |
| active      |                           |                           |
| read/write  |                           |                           |
| state       |                           |                           |
+-------------+---------------------------+---------------------------+
| Regenerate  | `tabadmin re              | `tsm security re          |
| internal    | generate_internal_tokens` | generate-internal-tokens` |
| security    |                           |                           |
| tokens      |                           |                           |
+-------------+---------------------------+---------------------------+
| Register    | `tabadmin register`       | `tsm register`            |
| Tableau     |                           |                           |
| Server      |                           |                           |
+-------------+---------------------------+---------------------------+
| Rebuild the | `tabadmin reindex`        | `tsm ma                   |
| search      |                           | intenance reindex-search` |
| index for   |                           |                           |
| Tableau     |                           |                           |
| Server      |                           |                           |
+-------------+---------------------------+---------------------------+
| Reset the   | `tabadmin reset`          | `tsm reset`               |
| Tableau     |                           |                           |
| Server      |                           |                           |
| ad          |                           |                           |
| ministrator |                           |                           |
| account     |                           |                           |
+-------------+---------------------------+---------------------------+
| Stop and    | `tabadmin restart`        | `tsm restart`             |
| restart all |                           |                           |
| Tableau     |                           |                           |
| Server      |                           |                           |
| processes   |                           |                           |
+-------------+---------------------------+---------------------------+
| Restore     | `tabadmin restore`        | `tsm maintenance restore` |
| from a      |                           |                           |
| Tableau     |                           | The restore command does  |
| Server      |                           | not restore any server    |
| backup file |                           | configuration data. This  |
|             |                           | is true whether you are   |
|             |                           | using a backup created    |
|             |                           | with TSM or a backup      |
|             |                           | created with tabadmin.    |
+-------------+---------------------------+---------------------------+
| Set a       | `tabadmin set`            | `tsm configuration set`   |
| co          |                           |                           |
| nfiguration |                           |                           |
| option      |                           |                           |
+-------------+---------------------------+---------------------------+
| Activate or | `tabadmin sitestate`      | `tsm sites unlock`        |
| suspend a   |                           |                           |
| site        |                           |                           |
+-------------+---------------------------+---------------------------+
| Start all   | `tabadmin start`          | `tsm start`               |
| Tableau     |                           |                           |
| Server      |                           |                           |
| processes   |                           |                           |
+-------------+---------------------------+---------------------------+
| Get the     | `tabadmin status`         | `tsm status`              |
| status of   |                           |                           |
| Tableau     |                           |                           |
| Server and  |                           |                           |
| server      |                           |                           |
| processes   |                           |                           |
+-------------+---------------------------+---------------------------+
| Stop all    | `tabadmin stop`           | `tsm stop`                |
| Tableau     |                           |                           |
| Server      |                           |                           |
| processes   |                           |                           |
+-------------+---------------------------+---------------------------+
| Create an   | `tabadmin ziplogs`        | `tsm maintenance ziplogs` |
| archive     |                           |                           |
| (.zip) file |                           | The default behavior of   |
| with        |                           | the ziplogs command has   |
| Tableau     |                           | changed: with tsm, the    |
| Server log  |                           | command collects up to    |
| files       |                           | the last two days of log  |
|             |                           | files by default. The     |
|             |                           | tabadmin ziplogs command  |
|             |                           | collected up to seven     |
|             |                           | days of log files. For    |
|             |                           | more information, see     |
|             |                           | [tsm maintenance          |
|             |                           | ziplogs](https://help.ta  |
|             |                           | bleau.com/current/server/ |
|             |                           | en-us/cli_maintenance_tsm |
|             |                           | .htm#tsm4ziplogs){.MCXref |
|             |                           | .xref}.                   |
+-------------+---------------------------+---------------------------+

