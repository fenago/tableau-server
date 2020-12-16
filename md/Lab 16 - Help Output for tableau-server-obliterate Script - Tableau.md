<img align="right" src="./images/logo.png">


Help Output for tableau-server-obliterate Script
================================================
The following help content is the output when you run the following
command:


`tableau-server-obliterate -h`

The ./tableau-server-obliterate script is installed to By default:
`C:\Program Files\Tableau\Tableau Server\packages\scripts.<version_code>\`.

Output
-------

```
Remove Tableau Server from this computer.

This script will stop and remove all Tableau Services from this
computer. It also removes data and configuration files. It leaves
licensing in place. It also preserves logs and backup files, which
are moved to a temp directory under the Tableau data folder. You can
force removal of these files, and licensing, using optional parameters.

This script is destructive and not reversible. It should only
be used to clean Tableau Server from a computer. For multi-node
installations, you must run the script separately on each node.

This script must be run as the Administrator.


-y              Required. Yes, remove Tableau Server from this computer.
        Must be specified three times to confirm.
-q      Optional. Quiet mode. Windows only. Do not display
        progress UI when removing Tableau Server.
-l              Optional. Delete licensing files and data. This command
        will attempt to deactivate licenses before deleting
        licensing data. Internet access is required for license
        deactivation. Offline deactivation is not supported.
        To deactivate license before removing Tableau Server,
        run 'tsm licenses deactivate' before running this script.
-k              Optional. Do not copy backups to logs_temp directory.
-g              Optional. Do not copy logs to logs_temp directory.
-a              Optional. Do not copy anything to logs_temp directory.  
```
