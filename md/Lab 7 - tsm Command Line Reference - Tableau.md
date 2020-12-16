
<img align="right" src="./images/logo.png">


tsm Command Line Reference
==========================
The topics in this section include reference content for Tableau
Services Manager (TSM) command line interface (CLI) to support Tableau
Server.

TSM is used to manage installation and configuration of Tableau Server.
To learn more about TSM, see [Tableau Services Manager
Overview](https://help.tableau.com/current/server/en-us/tsm_overview.htm).

You can automate the installation and configuration tasks supported by
the TSM CLI using the TSM API. To learn more about the prerelease
(Alpha) TSM API, see [Tableau Services Manager
API](https://help.tableau.com/v0.0/api/tsm_api/en-us/index.html).

Looking for tabadmin commands for [Tableau
Server] on Windows? See [tabadmin Commands[(Link
opens in a new
window)]](https://help.tableau.com/v2018.1/server/en-us/tabadmin_cmd.htm "Opens topic in a new browser tab")
in the 2018.1 Server help. Version 2018.1 is the last version of Tableau
Server that supports tabadmin. Beginning with version 2018.2,
TSM replaces tabadmin.

##### Using the tsm CLI
----------------------------------------------------------------------------------------------


You can run tsm commands on the initial node (the node where TSM is
installed), or on any additional node in the cluster.

To run tsm commands, you need to open Windows Command Prompt. Do not use
PowerShell to run tsm commands. Using PowerShell can cause unexpected
behavior.

1.  Open Windows Command Prompt with an account that is a member of the
    Administrators group on a node in the cluster.

2.  Run the command you want. If you are running the command from a node
    other than the initial node, include the `-s` option to specify the
    URL of the initial node by name (not IP address), and include the
    TSM port, 8850.

    To see the version of TSM and Tableau Server from the initial node:

    `tsm version`

    To see the version of TSM and Tableau Server from an additional
    node:

    `tsm version -s https://<inital_node_name>:8850`

    For example:

    `tsm version -s https://myTableauHost:8850`




##### Authenticating with tsm CLI
-----------------------------------------------------------------------------------------------------------


Beginning in the 2019.2 release of Tableau Server, running tsm commands
will not require you to enter a password if the following are true:

-   The account you are running commands with is a member of the
    TSM-authorized group, which is the local Administrators group on the
    Windows computer.
-   You are running commands locally on the Tableau Server that is
    running the Tableau Server Administration Controller service. By
    default, the Tableau Server Administration Controller service is
    installed and configured on the initial node in a distributed
    deployment.



####  Logging into tsm CLI locally


If you are running tsm commands on the local computer with user account
that is a member of a TSM-authorized group, then you will not need to
specify a password. In this case, just run the command, for example:

`tsm version`



####  Logging into tsm CLI remotely


If you are running TSM commands from a node in a cluster where the
Tableau Server Administration Controller service is not running, then
you must authenticate a session with the Tableau Server Administration
Controller service on the remote computer before you can run commands.
For example, run the following command:

`tsm login -s <server_name> -u <account_name>`

Where `<server_name>` is the name of the node where the Tableau Server
Administration Controller service is running and `<account_name>` is an
account that is a member of a TSM-authorized group.

After running this command, you will be prompted for a password. After
the account has been authenticated, you can run TSM commands.



##### Scripting and automating with tsm CLI
--------------------------------------------------------------------------------------------------------


TSM is a batch file. To run TSM commands in another batch file, use the
`call` command. For example \"`call tsm maintenance ziplogs`\". Doing
this will return control to the batch file.

To run automation on a Tableau Server without a password in the script
file, run the script on the initial node and with an account in the
proper TSM-authorized group. See the \"Authenticating\" section above.



##### Viewing help content in the shell
----------------------------------------------------------------------------------------------------


To view minimal help content from a command line, use the `tsm help`
category.



#### Synopsis


`tsm help [category] [command]`



####  Commands


`tsm help`

Help for all tsm commands

`tsm help <category>`

Show help for a specific command category. For example,
`tsm help authentication`.

`tsm help <category> <command>`

Show help for a specific command. For example,
`tsm help authentication open-id`.

`tsm help command`

List all top-level commands or categories.



Following commands are coverd in detail inside "tsm" directory:

- tsm authentication
- tsm configuration
- tsm configuration set Options
- tsm customize
- tsm data-access
- tsm email
- tsm initialize
- tsm jobs
- tsm licenses
- tsm login
- tsm logout
- tsm maintenance
- tsm pending-changes
- tsm register
- tsm reset
- tsm restart
- tsm schedules
- tsm security
- tsm settings
- tsm sites
- tsm start
- tsm status
- tsm stop
- tsm topology
- tsm user-identity-store
- tsm version
- tsm File Paths
