<img align="right" src="./images/logo.png">



tabcmd Commands
===============

Looking for Tableau Server on Linux? See [tabcmd Commands[(Link opens in a new window)]](https://help.tableau.com/current/server-linux/en-us/tabcmd_cmd.htm "Opens topic in a new browser tab").


You can use the following commands with the tabcmd command line tool:

addusers (to group)
createextracts
creategroup
createproject
createsite
createsiteusers
createusers
decryptextracts
delete workbook-name or datasource-name
deleteextracts
deletegroup
deleteproject
deletesite
deletesiteusers
deleteusers
editdomain
editsite
encryptextracts
export
get url
initialuser
listdomains
listsites
login
logout
publish
publishsamples
reencryptextracts
refreshextracts
removeusers
reset_openid_sub
runschedule
set
syncgroup
upgradethumbnails
version




#### addusers *group-name*


Adds users to the specified group.

**Example**

`tabcmd addusers "Development" --users "users.csv"`



#### Options


`--users`

Add the users in the given `.csv` file to the specified group. The file
should be a simple list with one user name per line. User names are not
case sensitive. The users should already be created on [Tableau
Server].

If you use this command with large `.csv` files on Tableau Server, a
server administrator can enable settings that help improve performance.

For more information, see [CSV Import File
Guidelines](https://help.tableau.com/current/server/en-us/csvguidelines.htm).

`--[no-]complete`

When set to `complete` this option requires that all rows be valid for
any change to succeed. If not specified, `--complete` is used.


#### Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`


Creates extracts for a published workbook or data source.


#### Options

`-d`, `--datasource`

The name of the target data source for extract creation.

`--embedded-datasources`

A space-separated list of embedded data source names within the target
workbook. Enclose data source names with double quotes if they contain
spaces. Only available when creating extracts for a workbook.

`--encrypt`

Create encrypted extract.

`--include-all`

Include all embedded data sources within target workbook. Only available
when creating extracts for workbook.

`--parent-project-path`

Path of the project that is the parent of the project that contains the
target resource. Must specify the project name with \--project.

`--project`

The name of the project that contains the target resource. Only
necessary if \--workbook or \--datasource is specified. If unspecified,
the default project \'Default\' is used.

`-u`, `-url`

The canonical name for the resource as it appears in the URL.

`-w`, `-workbook`

The name of the target workbook for extract creation.



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`


##### creategroup *group-name*
-------------------------------------------------------------------------------


Creates a group. Use `addusers` (for local groups) and `syncgroup` (for
Active Directory groups) commands to add users after the group has been
created.

**Example**

`tabcmd creategroup "Development"`



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`


##### createproject *project-name*
-----------------------------------------------------------------------------------


Creates a project.

**Example**

`tabcmd createproject -n "Quarterly_Reports" -d "Workbooks showing quarterly sales reports."`



#### Options


`-n`, `--name`

Specifies the name of the project that you want to create.

`--parent-project-path`

Specifies the name of the parent project for the nested project as
specified with the `-n` option. For example, to specify a project called
\"Nested\" that exists in a \"Main\" project, use the following syntax:
`--parent-project-path "Main" -n "Nested"`.

`-d`, `--description`

Specifies a description for the project.



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`


##### createsite *site-name*
-----------------------------------------------------------------------------


Creates a site.

**Examples**

Create a site named West Coast Sales. A site ID of `WestCoastSales` will
be automatically created, the site will have no storage quota limit, and
site administrators will be able to add and remove users:

`tabcmd createsite "West Coast Sales"`

Create a site named `West Coast Sales`with a site ID of `wsales`:

`tabcmd createsite "West Coast Sales" -r "wsales"`

Prevent site administrators from adding users to the site:

`tabcmd createsite "West Coast Sales" --no-site-mode`

Set a storage quota, in MB:

`tabcmd createsite "West Coast Sales" --storage-quota 100`



#### Options



`-r`, `--url`

Used in URLs to specify the site. Different from the site name.

`--user-quota`

Maximum number of users that can be added to the site.

`--[no-]site-mode`

Allows or denies site administrators the ability to add users to or
remove users from the site.

`--storage-quota`

In MB, the amount of workbooks, extracts, and data sources that can be
stored on the site.

`--extract-encryption-mode`

The extract encryption mode for the site can be **enforced**,
**enabled** or **disabled**. For more information, see [Extract
Encryption at
Rest](https://help.tableau.com/current/server/en-us/security_ear.htm).

`--run-now-enabled`

Allow or deny users from running extract refreshes, flows, or schedules
manually. **true** to allow users to run tasks manually or **false** to
prevent users from running tasks manually. For more information, see
[Server Settings (General and
Customization)](https://help.tableau.com/current/server/en-us/maintenance_set.htm).



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`



##### createsiteusers *filename.csv*
-------------------------------------------------------------------------------------


Adds users to a site, based on information supplied in a comma-separated
values (CSV) file. If the user is not already created on the server, the
command creates the user before adding that user to the site.

The CSV file must contain one or more user names and can also include
(for each user) a password, full name, license type, administrator
level, publisher (yes/no), and email address. For information about the
format of the CSV file, see [CSV Import File
Guidelines](https://help.tableau.com/current/server/en-us/csvguidelines.htm).

As an alternative to including administrator level and publisher
permissions in the CSV file, you can pass access level information by
including the `--role` option and specifying the site role you want to
assign users listed in the CSV file.

By default, users are added to the site that you are logged in to. To
add users to a different site, include the global `--site` option and
specify that site. (You must have permissions to create users on the
site you specify.)


If the server contains multiple sites, you cannot add server
(system) administrators through the `createsiteusers` command. Use
`createusers` instead. If you specify the `ServerAdministrator` site
role for the `--role` option, the command returns an error. If the CSV
file includes `System` as value for administrator, the value is ignored
and the user is assigned the `Unlicensed` license type.

If the server contains only one site (the default site), you can specify
`system` for the administrator value for a user, or even assign the
`ServerAdministrator` site role using the `--role` option, if you want
all users in the CSV file to be server administrators.

By default, this command creates users using a synchronous operation (it
waits for all operations to complete before proceeding). You can use the
`--no-wait` option to specify an asynchronous operation.



####  Improving performance for large CSV files


A server administrator can use the `tabadmin set` command to enable
settings that help to improve performance for large CSV files. For more
information, see [Improve performance for large CSV files passed through
tabcmd](https://help.tableau.com/current/server/en-us/csvguidelines.htm#improve-performance-large-csv) in the CSV Import File Guidelines topic.



####  Local authentication


If the server is configured to use local authentication, the information
in the CSV file is used to create users.



####  Active Directory authentication


If the server is configured to use Active Directory authentication, user
information is imported from Active Directory, and password and friendly
name information in the CSV file is ignored. Further, if a user is
specified in the CSV file but no corresponding user exists in Active
Directory, the user is not added to Tableau Server. For Active Directory
users, because the user name is not guaranteed to be unique across
domains, you must include the domain as part of the user name. You can
specify this as either `domain/username` or `username@domain.com`;
however, we recommend using the `domain/username` format. For more
information, see [User Management in Deployments with External Identity
Stores](https://help.tableau.com/current/server/en-us/users_manage_ad.htm).


**Example**

`tabcmd createsiteusers "users.csv" --role "Explorer"`



#### Options


`--admin-type`

Deprecated. Use the `--role` option instead.

`--complete`

Requires that all rows be valid for any change to succeed. This is the
default setting.

`--no-complete`

Specifies that the command should make changes on the server even if not
all rows contain valid information. Rows that contain invalid
information are skipped.

`--no-publisher`

Deprecated. Use the `--role` option instead.

`--nowait`

Do not wait for asynchronous jobs to complete.

`--publisher`

Deprecated. Use the `--role` option instead.

\--role

Specifies a site role for all users in the `.csv` file. When you want to
assign site roles using the \--role option, create a separate CSV file
for each site role.

Valid values are `ServerAdministrator`, `SiteAdministratorCreator`,
`SiteAdministratorExplorer`, `Creator`, `ExplorerCanPublish`,
`Explorer`, `Viewer`, `ReadOnly`, and `Unlicensed`.

The default is `Unlicensed` for new users and unchanged for existing
users. Users are added as unlicensed also if you have a user-based
server installation, and if the `createsiteusers` command creates a new
user, but you have already reached the limit on the number of licenses
for your users.

**Note:** On a multi-site Tableau Server, if you want to assign the
`ServerAdministrator` site role using the `--role` option, use the
[`createusers`](https://help.tableau.com/current/server/en-us/tabcmd_cmd.htm#createusers)
command instead of `createsiteusers`.

`--silent-progress`

Do not display progress messages for the command.



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`


##### createusers *filename.csv*
---------------------------------------------------------------------------------


Create users in Tableau Server, based on information supplied in a
comma-separated values (CSV) file.

The CSV file must contain one or more user names and can also include
(for each user) a password, full name, license type, administrator
level, publisher (yes/no), and email address. For information about the
format of the CSV file, see [CSV Import File
Guidelines](https://help.tableau.com/current/server/en-us/csvguidelines.htm).

As an alternative to including administrator level and publisher
permissions in the CSV file, you can pass access level information by
including the `--role` option and specifying the site role you want to
assign users listed in the CSV file.

If the server has only one site (the default site), the user is created
and added to the site. If the server has multiple sites, the user is
created but is not added to any site. To add users to a site, use
[`createsiteusers`](https://help.tableau.com/current/server/en-us/tabcmd_cmd.htm#createsiteusers).

If you have a user-based server installation, and if the command creates
a new user but you have already reached the limit on the number of
licenses for your users, the user is added as an unlicensed user.



####  Local authentication

If the server is configured to use local authentication, the information
in the CSV file is used to create users.


####  Active Directory authentication 

If the server is configured to use Active Directory authentication, user
information is imported from Active Directory, and password and friendly
name information in the CSV file is ignored. Further, if a user is
specified in the CSV file but no corresponding user exists in Active
Directory, the user is not added to Tableau Server. For Active Directory
users, because the user name is not guaranteed to be unique across
domains, you must include the domain as part of the user name. You can
specify this as either `domain/username` or `username@domain.com`;
however, we recommend using the `domain/username` format. For more
information, see [User Management in Deployments with External Identity
Stores](https://help.tableau.com/current/server/en-us/users_manage_ad.htm).

**Example**

`tabcmd createusers "users.csv" --role "ServerAdministrator"`

`tabcmd createusers "users.csv"`



#### Options


`--admin-type`

Deprecated. Use the `--role` option instead.

`--complete`

Requires that all rows be valid for any change to succeed. This is the
default setting.

`--no-complete`

Specifies that the command should make changes on the server even if not
all rows contain valid information. Rows that contain invalid
information are skipped.

`--no-publisher`

Deprecated. Use the `--role` option instead.

`--nowait`

Do not wait for asynchronous jobs to complete.

`--publisher`

Deprecated. Use the `--role` option instead.

`-r`, `--role`

Specifies a site role for all users in the `.csv` file. When you want to
assign site roles using the \--role option, create a separate CSV file
for each site role.

Valid values are `ServerAdministrator`, `SiteAdministratorCreator`,
`SiteAdministratorExplorer`, `Creator`, `ExplorerCanPublish`,
`Explorer`, `Viewer`, `ReadOnly`, and `Unlicensed`.

On a multi-site server, the command does not assign the user to a site.
Therefore, the only site roles the command can successfully assign are
`ServerAdministrator` and `Unlicensed`. If you specify any other site
role, the command assigns the `Unlicensed` role.

On a single-site server, the user is created and added to the default
site using the role that you specify.

If you have a user-based server installation, and if the command creates
a new user but you have already reached the limit on the number of
licenses for your users, the user is added as an unlicensed user.

`--silent-progress`

Do not display progress messages for the command.



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`




##### decryptextracts
--------------------------------------------------------------------------------------------------------------------


Decrypt all extracts on a site. If no site is specified, extracts on the
default site will be decrypted. For more information, see [Extract
Encryption at
Rest](https://help.tableau.com/current/server/en-us/security_ear.htm).

Depending on the number and size of extracts, this operation may consume
significant server resources. Consider running this command outside of
normal business hours.

**Example**

`tabcmd decryptextracts "West Coast Sales"`



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`



##### delete *workbook-name* or *datasource-name*
--------------------------------------------------------------------------------------------------


Deletes the specified workbook or data source from the server.

This command takes the name of the workbook or data source as it is on
the server, not the file name when it was published.

**Example**

`tabcmd delete "Sales_Analysis"`



#### Options


`-r`, `--project`

The name of the project containing the workbook or data source you want
to delete. If not specified, the "Default" project is assumed.

`--parent-project-path`

Specifies the name of the parent project for the nested project as
specified with the `-r` option. For example, to specify a project called
\"Nested\" that exists in a \"Main\" project, use the following syntax:
`--parent-project-path "Main" -r "Nested"`.

`--workbook`

The name of the workbook you want to delete.

`--datasource`

The name of the data source you want to delete.



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`


##### deleteextracts
---------------------------------------------------------------------


Deletes extracts for a published workbook or data source.



#### Options


`-d`, `--datasource`

The name of the target data source for extract deletion.

`--embedded-datasources`

A space-separated list of embedded data source names within the target
workbook. Enclose data source names with double quotes if they contain
spaces. Only available when deleting extracts for a workbook.

`--encrypt`

Create encrypted extract.

`--include-all`

Include all embedded data sources within target workbook.

`--parent-project-path`

Path of the project that is the parent of the project that contains the
target resource. Must specify the project name with \--project.

`--project`

The name of the project that contains the target resource. Only
necessary if \--workbook or \--datasource is specified. If unspecified,
the default project \'Default\' is used.

`-u`, `-url`

The canonical name for the resource as it appears in the URL.

`-w`, `-workbook`

The name of the target workbook for extract deletion.



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`


##### deletegroup *group-name*
-------------------------------------------------------------------------------


Deletes the specified group from the server.

**Example**

`tabcmd deletegroup "Development"`



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`


##### deleteproject *project-name*
-------------------------------------------------------------------------


Deletes the specified project from the server.

Using `tabcmd`, you can specify only a top-level project in a project
hierarchy. To automate tasks you want to perform on a project within a
parent project, use the equivalent Tableau [REST API[(Link opens in a
new
window)]](https://help.tableau.com/current/api/rest_api/en-us/help.htm#REST/rest_api_ref.htm%23API_Reference "Opens REST API reference in new browser tab")
call.

**Example**

`tabcmd deleteproject "Designs"`



#### Option


`--parent-project-path`

Specifies the name of the parent project for the nested project as
specified with the command. For example, to specify a project called
\"Designs\" that exists in a \"Main\" project, use the following syntax:
`--parent-project-path "Main" "Designs"`.



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`


##### deletesite *site-name*
-----------------------------------------------------------------------------


Deletes the specified site from the server.

**Example**

`tabcmd deletesite "Development"`



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`



##### deletesiteusers *filename.csv*
----------------------------------------------------------------------------------------------------------------------------


Removes users from from the site that you are logged in to. The users to
be removed are specified in a file that contains a simple list of one
user name per line. (No additional information is required beyond the
user name.)

By default, if the server has only one site, or if the user belongs to
only one site, the user is also removed from the server. On a Tableau
Server Enterprise installation, if the server contains multiple sites,
users who are assigned the site role of **Server Administrator** are
removed from the site but are not removed from the server.

If the user owns content, the user\'s role is change to **Unlicensed**,
but the user is not removed from the server or the site. The content is
still owned by that user. To remove the user completely, you must change
the owner of the content and then try removing the user again.

If the user was imported from Active Directory, the user is removed from
the site and possibly from the server. However, the user is not deleted
from Active Directory.

**Example**

`tabcmd deletesiteusers "users.csv"`



####  Improving performance for large CSV files


A server administrator can use the `tabadmin set` command to enable
settings that help to improve performance for large CSV files. For more
information, see [Improve performance for large CSV files passed through
tabcmd](https://help.tableau.com/current/server/en-us/csvguidelines.htm#improve-performance-large-csv) in the CSV Import File Guidelines topic.



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`



##### deleteusers *filename.csv*
---------------------------------------------------------------------------------


Deletes the users listed in the specified comma-separated values
(`.csv`) file.

The `.csv` file should contain a simple list of one user name per line.

**Example**

`tabcmd deleteusers "users.csv"`



#### Options


`--[no-]complete`

When set to `--complete` this option requires that all rows be valid for
any change to succeed. If not specified, `--complete` is used.



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`



##### editdomain
-------------------------------------------------------------------------------------------------


Changes the nickname or full domain name of an Active Directory domain
on the server. A domain "nickname" is the Windows NetBIOS domain name.

You can modify the nickname for any domain the server is using. In
general, you can modify the full domain name for any domain except the
one that you used to sign in. However, if the user name that you are
currently signed in with exists in both the current domain and the new
domain, you can modify the full name for the current domain.

To ensure that Tableau Server can connect to other Active Directory
domains, you must also specify secondary domains that Tableau Server
connects to by setting the `wgserver.domain.whitelist` option with TSM.
For more information about secondary domains and configuring the
connection, see
[wgserver.domain.whitelist](https://help.tableau.com/current/server/en-us/cli_configuration-set_tsm.htm#wgserver-domain).

Review [User Management in Deployments with External Identity
Stores](https://help.tableau.com/current/server/en-us/users_manage_ad.htm) to understand how multiple domains, domain name mapping, and user
names interact with Tableau Server.

To see a list of domains, use
[listdomains](https://help.tableau.com/current/server/en-us/tabcmd_cmd.htm#listdomains).

**Examples**

`tabcmd editdomain --id 2 --nickname "new-nickname"`

`tabcmd editdomain --id 3 --name "new-name"`



#### Options


`--id`

The ID of domain to change. To get a list of domain IDs, use use
[listdomains](https://help.tableau.com/current/server/en-us/tabcmd_cmd.htm#listdomains).

`--name`

The new name for the domain.

`--nickname`

The new nickname for the domain.



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`



##### editsite *site-name*
---------------------------------------------------------------------------


Changes the name of a site or its web folder name. You can also use this
command to allow or deny site administrators the ability to add and
remove users, or prevent users from running certain tasks manually. If
site administrators have user management rights, you can specify how
many users they can add to a site.

**Examples**

`tabcmd editsite wc_sales --site-name "West Coast Sales"`

`tabcmd editsite wc_sales --site-id "wsales"`

`tabcmd editsite wsales --status ACTIVE`

`tabcmd editsite wsales --user-quota 50`



#### Options


`--site-name`

The name of the site that\'s displayed.

`--site-id`

Used in the URL to uniquely identify the site.

`--user-quota`

Maximum number of users who can be members of the site.

`--[no-]site-mode`

Allow or prevent site administrators from adding users to the site.

`--status`

Set to `ACTIVE` to activate a site, or to `SUSPENDED` to suspend a site.

`--storage-quota`

In MB, the amount of workbooks, extracts, and data sources that can be
stored on the site.

`--extract-encryption-mode`

The extract encryption mode for the site can be **enforced**,
**enabled** or **disabled**. For more information, see [Extract
Encryption at
Rest](https://help.tableau.com/current/server/en-us/security_ear.htm). Depending on the number and size of extracts, this operation may
consume significant server resources.

`--run-now-enabled`

Allow or deny users from running extract refreshes, flows, or schedules
manually. **true** to allow users to run tasks manually or **false** to
prevent users from running tasks manually. For more information, see
[Server Settings (General and
Customization)](https://help.tableau.com/current/server/en-us/maintenance_set.htm).



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`




##### encryptextracts
--------------------------------------------------------------------------------------------------------------------


Encrypt all extracts on a site. If no site is specified, extracts on the
default site will be encrypted. For more information, see [Extract
Encryption at
Rest](https://help.tableau.com/current/server/en-us/security_ear.htm).

Depending on the number and size of extracts, this operation may consume
significant server resources. Consider running this command outside of
normal business hours.

**Example**

`tabcmd encryptextracts "West Coast Sales"`



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`


Exports a view or workbook from [Tableau Server]
and saves it to a file. This command can also export just the data used
for a view.

Note the following when you use this command:

-   **Permissions**: To export, you must have the [Export
    Image] permission. By default, this permission is
    Allowed or Inherited for all roles, although permissions can be set
    per workbook or view.

-   **Exporting data**: To export just the data for a view, use the
    `--csv` option. This exports the summary data used in a view to a
    .csv file.

-   **Specifying the view, workbook, or data to export**:

    -   Use part of the URL to identify what to export, specifically the
        `"workbook/view"` string as it appears in the URL for the
        workbook or view. Do not use the "friendly name," and exclude
        the `:iid=<n>` session ID at the end of the URL.

        For example, the Tableau sample view *Global Temperatures* in
        the *Regional*workbook has a URL similar to
        this: `<server_name>/#/views/Regional/GlobalTemperatures?:iid=3`

        To export the *Global Temperatures* view, use the string
        `Regional/GlobalTemperatures`.

        Do *not*use `Regional/Global Temperatures`, or
        `Regional/GlobalTemperatures?:iid=3`.

    -   If the server is running multiple sites and the view or workbook
        is on a site other than Default, Use `-t <site_id>`.

    -   To export a workbook, get the URL string by opening a view in
        the workbook, and include the view in the string you use.

        In the above example, to export the *Regional* workbook, use the
        string `Regional/GlobalTemperatures`.

    -   To export a workbook, it must have been published with [Show
        Sheets as Tabs] selected in the Tableau Desktop
        Publish dialog box.

        **Note:** The Tableau workbook that contains the [administrative
        views[(Link opens in a new
        window)]](https://help.tableau.com/current/server/en-us/adminview.htm)
        cannot be exported.

-   [The saved file\'s format]: Your format options depend
    on what\'s being exported. A workbook can only be exported as a PDF
    using the `--fullpdf` argument. A view can be exported as a PDF
    (`--pdf`) or a PNG (`--png`).

-   **The saved file\'s name and location** (optional): If you don\'t
    provide a name, it will be derived from the view or workbook name.
    If you don\'t provide a location, the file will be saved to your
    current working directory. Otherwise, you can specify a full path or
    one that\'s relative to your current working directory.

    **Note**: You must include a file name extension such as `.csv` or
    `.pdf`. The command does not automatically add an extension to the
    file name that you provide.

-   **Dashboard web page objects not included in PDF exports**: A
    dashboard can optionally include a web page object. If you are
    performing an export to PDF of a dashboard that includes a web page
    object, the web page object won\'t be included in the PDF.

-   **Non-ASCII and non-standard ASCII characters and PDF exports**: If
    you are exporting a view or workbook with a name that includes a
    character outside the ASCII character set, or a non-standard ASCII
    character set, you need to URL encode (percent-encode) the
    character.

    For example if your command includes the city `Zürich`, you need to
    URL encode it as `Z%C3%BCrich`:

    `tabcmd export "/Cities/Sheet1?locationCity=Z%C3%BCrich" -fullpdf`

**Clearing the Cache to Use Real-Time Data**

You can optionally add the URL parameter `?:refresh=yes` to force a
fresh data query instead of pulling the results from the cache. If you
are using tabcmd with your own scripting and the `refresh` URL parameter
is being used a great deal, this can have a negative impact on
performance. It\'s recommended that you use `refresh` only when
real-time data is required---for example, on a single dashboard instead
of on an entire workbook.

**Examples**

*Views*

`tabcmd export "Q1Sales/Sales_Report" --csv -f "Weekly-Report.csv"`

`tabcmd export -t Sales "Sales/Sales_Analysis" --pdf -f "C:\Tableau_Workbooks\Weekly-Reports.pdf"`

`tabcmd export "Finance/InvestmentGrowth" --png`

`tabcmd export "Finance/InvestmentGrowth?:refresh=yes" --png`

*Workbooks*

`tabcmd export "Q1Sales/Sales_Report" --fullpdf`

`tabcmd export "Sales/Sales_Analysis" --fullpdf --pagesize tabloid -f "C:\Tableau_Workbooks\Weekly-Reports.pdf"`



#### Options


`-f`, `--filename`

Saves the file with the given filename and extension.

`--csv`

View only. Export the view\'s data (summary data) in `.csv` format.

`--pdf`

View only. Export as a PDF.

`--png`

View only. Export as an image in `.png` format.

`--fullpdf`

Workbook only. Export as a PDF. The workbook must have been published
with [Show Sheets as Tabs] enabled.

`--pagelayout`

Sets the page orientation (`landscape` or `portrait`) of the exported
PDF. If not specified, its Tableau Desktop setting will be used.

`--pagesize`

Sets the page size of the exported PDF as one of the following:
`unspecified`, `letter`, `legal`, `note folio`, `tabloid`, `ledger`,
`statement`, `executive`, `a3`, `a4`, `a5`, `b4`, `b5`, or `quarto`.
Default is `letter`.

`--width`

Sets the width in pixels. Default is 800 px.

`--height`

Sets the height in pixels. Default is 600 px.



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`


##### get *url*
----------------------------------------------------------------


Gets the resource from [Tableau Server] that\'s
represented by the specified (partial) URL. The result is returned as a
file.

Note the following when you use this command:

-   **Permissions**: To get a file, you must have the [Download/Web Save
    As] permission. By default, this permission is allowed
    or inherited for all roles, although permissions can be set per
    workbook or view.

-   **Specifying a view or workbook to get**: You specify a view to get
    using the `"/views/<workbookname>/<viewname>.<extension>"` string,
    and specify a workbook to get using the
    `"/workbooks/<workbookname>.<extension>"` string. Replace
    `<workbookname> `and `<viewname>` with the names of the workbook and
    view as they appear in the URL when you open the view in a browser
    and replace \<extension\> with the type of file you want to save. Do
    not use the session ID at the end of the URL (`?:iid=<n>`) or the
    \"friendly\" name of the workbook or view.

    For example, when you open a view *Regional Totals* in a workbook
    named *Metrics Summary*, the URL will look similar to this:

    `/views/MetricsSummary_1/RegionalTotals?:iid=1`

    Use the string `/views/MetricsSummary_1/RegionalTotals.<extension>`
    to get the view.

    Use the string `/workbooks/MetricsSummary_1.<extension>` to get the
    workbook.

-   **File extension**: The URL must include a file extension. The
    extension determines what\'s returned. A view can be returned in
    PDF, PNG, or CSV (summary data only) format. A Tableau workbook is
    returned as a TWB if it connects to a published data source or uses
    a live connection, or a TWBX if it connects to a data extract.

    **Note**: If you are downloading a view to a PDF or PNG file, and if
    you include a `--filename` parameter that includes the .pdf or .png
    extension, you do not have to include a .pdf or .png extension in
    the URL.

-   **The saved file\'s name and location** (optional): The name you use
    for `--filename` should include the file extension. If you don\'t
    provide a name and file extension, both will be derived from the URL
    string. If you don\'t provide a location, the file is saved to your
    current working directory. Otherwise, you can specify a full path or
    one that\'s relative to your current working directory.

-   **PNG size** (optional): If the saved file is a PNG, you can specify
    the size, in pixels, in the URL.

**Clearing the cache to use real-time data**

You can optionally add the URL parameter `?:refresh=yes` to force a
fresh data query instead of pulling the results from the cache. If you
are using tabcmd with your own scripting, using the `refresh` parameter
a great deal can have a negative impact on performance. It\'s
recommended that you use `refresh` only when real-time data is
required---for example, on a single dashboard instead of on an entire
workbook.

**Examples**

*Views*

`tabcmd get "/views/Sales_Analysis/Sales_Report.png" --filename "Weekly-Report.png"`

`tabcmd get "/views/Finance/InvestmentGrowth.pdf" -f "Q1Growth.pdf"`

`tabcmd get "/views/Finance/InvestmentGrowth" -f "Q1Growth.pdf"`

`tabcmd get "/views/Finance/InvestmentGrowth.csv"`

`tabcmd get "/views/Finance/InvestmentGrowth.png?:size=640,480" -f growth.png`

`tabcmd get "/views/Finance/InvestmentGrowth.png?:refresh=yes" -f growth.png`

*Workbooks*

`tabcmd get "/workbooks/Sales_Analysis.twb" -f "C:\Tableau_Workbooks\Weekly-Reports.twb"`



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`


##### initialuser
--------------------------------------------------------------------------------------------------


Create the initial administrative user on a server that does not have an
initial administrative user defined.

**Note**: The **tabcmd initialuser** command does not require
authentication to Tableau Server, but you must run the command on the
initial server node.

**Examples**

`tabcmd initialuser --username "admin" --password "password" --server http://localhost`

`tabcmd initialuser --username "admin" --password "password" --friendly "Tableau Admin" --server http://localhost`

To prompt for the password in the shell, do not include the `--password`
parameter in the command. For example:

`tabcmd initialuser --username "admin" --server http://localhost`



#### Options


`-f`, `--friendly`

Creates the initial administrative user with the display name.



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`



##### listdomains
-------------------------------------------------------------------------------------


Displays a list of the Active Directory domains that are in use on the
server, along with their nicknames and IDs. If the server is configured
to use local authentication, the command returns only the domain name
`local`.

**Example**

`tabcmd listdomains`



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`



##### listsites
----------------------------------------------------------------


Returns a list of sites to which the logged in user belongs.

**Example**

`tabcmd listsites --username adam --password mypassword`



#### Options


`--get-extract-encryption-mode`

The extract encryption mode for the site can be **enforced**,
**enabled** or **disabled**. For more information, see [Extract
Encryption at
Rest](https://help.tableau.com/current/server/en-us/security_ear.htm).



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`



##### login
-----------------------------------------------------------------------


Logs in a [Tableau Server] user.

Use the `--server`, `--site`, `--username`, `--password` global options
to create a session.

**Note**: When you use the **tabcmd login** command, you cannot use SAML
single sign-on (SSO), even if the server is configured to use SAML. To
log in, you must pass the user name and password of a user who has been
created on the server. You will have the permissions of the Tableau
Server user that you\'re signed in as. For more information, see [Set
Users' Site
Roles](https://help.tableau.com/current/server/en-us/users_site_roles.htm) and
[Permissions](https://help.tableau.com/current/server/en-us/permissions.htm).

If you want to log in using the same information you\'ve already used to
create a session, just specify the `--password` option. The server and
user name stored in the cookie will be used.

If the server is using a port other than 80 (the default), you will need
to specify the port.

You need the `--site` (`-t`) option only if the server is running
multiple sites and you are logging in to a site other than the Default
site. If you do not provide a password you will be prompted for one. If
the `--no-prompt` option is specified and no password is provided the
command will fail.

Once you log in, the session will continue until it expires on the
server or the `logout` command is run.

**Example**


Logs user jsmith in to the [Tableau Server]
running on their local machine:

`tabcmd login -s http://localhost -u jsmith -p password`

Logs administrator in to the Sales site on sales-server:

`tabcmd login -s http://sales-server -t Sales -u administrator -p password`

`tabcmd login -s http://sales-server:8000 -t Sales -u administrator -p password`

Logs administrator in to the Sales site on sales-server using SSL, but
does not validate the server's SSL certificate:

`tabcmd login --no-certcheck -s https://sales-server -t Sales -u administrator -p password`

Establishes a forward proxy and port for localhost:

`tabcmd login --proxy myfwdproxyserver:8888 -s http://localhost -u jsmith -p password`

Logs user jsmith in to the reverse proxy using SSL:

`tabcmd login -s https://myreverseproxy -u jsmith -p password`




#### Options


`-s`, `--server`

If you are running the command from a Tableau Server computer that's on
your network, you can use `http://localhost`. Otherwise, specify the
computer\'s URL, such as `http://bigbox.myco.com` or `http://bigbox`.

For Tableau Online specify the URL `https://online.tableau.com`.

`-t`, `--site`

Include this option if the server has multiple sites, and you are
logging in to a site other than the default site.

The site ID is used in the URL to uniquely identify the site. For
example, a site named West Coast Sales might have a site ID of
west-coast-sales.

`-u`, `--username`

The user name of the user logging in. For Tableau Online, the user name
is the user\'s email address.

`-p`, `--password`

Password for the user specified for `--username`. If you do not provide
a password you will be prompted for one.

`--password-file`

Allows the password to be stored in the given `filename.txt` file rather
than the command line, for increased security.



`-x`, `--proxy`

Use to specify the HTTP proxy server and port (Host:Port) for the tabcmd
request.


`--no-prompt`

Do not prompt for a password. If no password is specified, the `login`
command will fail.


`--no-proxy`

Do not use an HTTP proxy server.


`--cookie`

Saves the session ID on login. Subsequent commands will not require a
login. This value is the default for the command.

`--no-cookie`

Do not save the session ID information after a successful login.
Subsequent commands will require a login.

`--timeout SECONDS`

The number of seconds the server should wait before processing the
`login` command. Default: 30 seconds.



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`


##### logout
---------------------------------------------------------------------------------------------------------------------------


Logs out of the server.

**Example**

`tabcmd logout`



##### publish *filename.twb(x)*, *filename.tds(x)*, or *filename.hyper*
------------------------------------------------------------------------------------------------------------------------


Publishes the specified workbook (.twb(x)), data source (.tds(x)), or
extract (.hyper) to [Tableau Server].

If you are publishing a workbook, by default, all sheets in the workbook
are published without database user names or passwords.

The permissions initially assigned to the workbook or data source are
copied from the project that the file is published to. Permissions for
the published resource can be changed after the file has been
published. 

If the workbook contains user filters, one of the thumbnail options must
be specified.

**Example**

`tabcmd publish "analysis.twbx" -n "Sales_Analysis" --db-username "jsmith" --db-password "secret-password"`

`tabcmd publish "analysis_sfdc.hyper" -n "Sales Analysis" --oauth-username "user-name" --save-oauth`

If the file is not in the same directory as tabcmd, include the full
path to the file.

**Example**

`tabcmd publish "\\computer\volume\Tableau Workbooks\analysis.twbx" -n "Sales_Analysis" --db-username "jsmith" --db-password "secret-password"`

`tabcmd publish "\\computer\volume\Tableau Workbooks\analysis_sfdc.hyper" -n "Sales Analysis" --oauth-username "username" --save-oauth`



#### Options


`-n`, `--name`

Name of the workbook or data source on the server. If omitted, the
workbook, data source, or data extract will be named after filename.

`-o`, `--overwrite`

Overwrites the workbook, data source, or data extract if it already
exists on the server.

`-r`, `--project`

Publishes the workbook, data source, or data extract into the specified
project. Publishes to the "Default" project if not specified.

`--parent-project-path`

Specifies the name of the parent project for the nested project as
specified with the `-r` option. For example, to specify a project called
\"Nested\" that exists in a \"Main\" project, use the following syntax:
`--parent-project-path "Main" -r "Nested"`.

`--db-username`

Use this option to publish a database user name with the workbook, data
source, or data extract.

`--db-password`

Use this option to publish a database password with the workbook, data
source, or extract.

`--save-db-password`

Stores the provided database password on the server.

`--oauth-username`

The email address of the user account. Connects the user through a
preconfigured OAuth connection, if the user already has a saved access
token for the cloud data source specified in `--name`. Access tokens are
managed in user preferences.

For existing OAuth connections to the data source, use this option
instead of `--db-username` and `--db-password`.

`--save-oauth`

Saves the credential specified by `--oauth-username` as an embedded
credential with the published workbook or data source.

Subsequently, when the publisher or server administrator signs in to the
server and edits the connection for that workbook or data source, the
connection settings will show this OAuth credential as embedded in the
content.

If you want to schedule extract refreshes after publishing, you must
include this option with `--oauth-username`. This is analogous to using
`--save-db-password` with a traditional database connection.

`--thumbnail-username`

If the workbook contains user filters, the thumbnails will be generated
based on what the specified user can see. Cannot be specified when
`--thumbnail-group` option is set.

`--thumbnail-group`

If the workbook contains user filters, the thumbnails will be generated
based on what the specified group can see. Cannot be specified when
`--thumbnail-username`option is set.

`--tabbed`

When a workbook with tabbed views is published, each sheet becomes a tab
that viewers can use to navigate through the workbook. Note that this
setting will override any sheet-level security.

`--append`

Append the extract file to the existing data source.

`--replace`

Use the extract file to replace the existing data source.

`--disable-uploader`

Disable the incremental file uploader.

`--restart`

Restart the file upload.

`--encrypt-extracts`

Encrypt extracts when you publish a workbook, data source, or extract to
the server. For more information, see [Extract Encryption at
Rest](https://help.tableau.com/current/server/en-us/security_ear.htm).



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`



##### publishsamples
-----------------------------------------------------------------------------------------------------------




####  Description


Publishes Tableau Sample workbooks to the specified project. Any
existing samples will be overwritten.



####  Syntax


`tabcmd publishsamples -n [project name] [Global options]`

**Example**

Publish samples to the Inside Sales project on the Default site, as user
jsmith.

`tabcmd publishsamples -n "Inside Sales" -t "" -s localhost --username "jsmith" --password "secret-password"`



#### Options


`-n`, `--name`

Required. Publishes the Tableau samples into the specified project. If
the project name includes spaces, enclose the entire name in quotes.

`--parent-project-path`

Specifies the name of the parent project for the nested project as
specified with the `-n` option. For example, to specify a project called
\"Nested\" that exists in a \"Main\" project, use the following syntax:
`--parent-project-path "Main" -n "Nested"`.



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`




##### reencryptextracts
------------------------------------------------------------------------------------------------------------------------


Reencrypt all extracts on a site with new encryption keys. This command
will regenerate the key encryption key and data encryption key. You must
specify a site. For more information, see [Extract Encryption at
Rest](https://help.tableau.com/current/server/en-us/security_ear.htm).

Depending on the number and size of extracts, this operation may consume
significant server resources. Consider running this command outside of
normal business hours.

**Examples**

`tabcmd reencryptextracts "Default"`

`tabcmd reencryptextracts "West Coast Sales"`



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`



##### refreshextracts *workbook-name* or *datasource-name*
-----------------------------------------------------------------------------------------------------------


Performs a full or incremental refresh of extracts belonging to the
specified workbook or data source.

This command takes the name of the workbook or data source as it appears
on the server, not the file name when it was published. Only an
administrator or the owner of the workbook or data source is allowed to
perform this operation.

**Note:** This method will fail and result in an error if your Server
Administrator has disabled the **RunNow** setting for the site. For more
information, see [Tableau Server Settings[(Link opens in a new
window)]](https://help.tableau.com/current/server/en-us/maintenance_set.htm).

**Examples**

`tabcmd refreshextracts --datasource sales_ds`

`tabcmd refreshextracts --project "Sales External" --datasource sales_ds`

`tabcmd refreshextracts --workbook "My Workbook"`

`tabcmd refreshextracts --url SalesAnalysis`

`tabcmd refreshextracts --workbook "My Workbook" --addcalculations`

`tabcmd refreshextracts --datasource sales_ds --removecalculations`



#### Options


`--incremental`

Runs the incremental refresh operation.

`--synchronous`

Adds the full refresh operation to the queue used by the Backgrounder
process, to be run as soon as a Backgrounder process is available. If a
Backgrounder process is available, the operation is run immediately. The
refresh operation appears on the Background Tasks report.

During a synchronous refresh, `tabcmd` maintains a live connection to
the server while the refresh operation is underway, polling every second
until the background job is done.

`--workbook`

The name of the workbook containing extracts to refresh. If the workbook
has spaces in its name, enclose it in quotes.

`--datasource`

The name of the data source containing extracts to refresh.

`--project`

Use with `--workbook` or `--datasource` to identify a workbook or data
source in a project other than *Default*. If not specified, the Default
project is assumed.

`--parent-project-path`

Specifies the name of the parent project for the nested project as
specified with the `--project` option. For example, to specify a project
called \"Nested\" that exists in a \"Main\" project, use the following
syntax: `--parent-project-path "Main" --project "Nested"`.

`--url`

The name of the workbook as it appears in the URL. A workbook published
as "Sales Analysis" has a URL name of "SalesAnalysis".

`--addcalculations`

Use with `--workbook` to materialize calculations in the embedded
extract of the workbook or `--datasource` to materialize calculations in
the extract data source. Adds the operation to the queue used by the
Backgrounder process. If a Backgrounder process is available, the
operation runs immediately. This operation appears on the [Background
Tasks for
Extracts](https://help.tableau.com/current/online/en-us/adminview_backgrnd.htm)
administrative view.

`--removecalculations`

Use with `--workbook `or `--datasource` to remove calculations that were
previously materialized. Adds the operation to the queue used by the
Backgrounder process. If a Backgrounder process is available, the
operation runs immediately. This operation appears on the [Background
Tasks for
Extracts](https://help.tableau.com/current/online/en-us/adminview_backgrnd.htm)
administrative view.



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`



##### reset\_openid\_sub
----------------------------------------------------------------------------------------------------------


Clears OpenID Connect identifiers (sub values) that have already been
associated with Tableau Server identities. See [Changing IdPs in Tableau
Server for OpenID
Connect](https://help.tableau.com/current/server/en-us/openid_auth_changing_idp.htm).

**Example**

`tabcmd reset_openid_sub --target-username jsmith`



#### Options


`--target-username`

Clears sub value for the specified individual user.

`--all`

Clears sub values for all users.



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`



##### removeusers *group-name*
-------------------------------------------------------------------------------


Removes users from the specified group.

**Example**

`tabcmd removeusers "Development" --users "users.csv"`



#### Options


`--users`

Remove the users in the given `.csv` file from the specified group. The
file should be a simple list with one user name per line.

If you use this command with large `.csv` files on Tableau Server, a
server administrator can enable settings that help to improve
performance. For information, see [Improve performance for large
CSV files passed through
tabcmd](https://help.tableau.com/current/server/en-us/csvguidelines.htm#improve-performance-large-csv)

`--[no-]complete`

Requires that all rows be valid for any change to succeed. If not
specified `--complete` is used.



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`


##### runschedule *schedule-name*
----------------------------------------------------------------------------------


Runs the specified schedule.

This command takes the name of the schedule as it is on the server.

This command is not available for Tableau Online.

**Note:** This method will fail and result in an error if your Server
Administrator has disabled the **RunNow** setting for the site. For more
information, see [Tableau Server Settings[(Link opens in a new
window)]](https://help.tableau.com/current/server/en-us/maintenance_set.htm).

**Example**

`tabcmd runschedule "5AM Sales Refresh"`



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`


##### set *setting*
--------------------------------------------------------------------


Enables the specified setting on the server. Details about each setting
can be seen on the Maintenance page on the server.

Use an exclamation mark in front of the setting name to disable the
setting. You can enable or disable the following settings:

-   `allow_scheduling`

-   `embedded_credentials`

-   `remember_passwords_forever`

**Example**

`tabcmd set embedded_credentials`



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`



##### syncgroup *group-name*
-----------------------------------------------------------------------------


Synchronizes a Tableau Server group with an Active Directory group. If
the Tableau Server group does not already exist, it is created and
synchronized with the specified Active Directory group.

If the group name itself includes an \"@\" (other than as the domain
separator) you need to refer to the symbol using the hex format
\"\\0x40\".

**Example**

`tabcmd syncgroup "Development"`

`tabcmd syncgroup "Dev\0x40West"`

**Note:** If you synchronize a group that you are a member of, changes
that you make using this command do not apply to your user. For example,
if you use this command to remove the administrator right from users in
a group that you are a member of, you are still an administrator when
the command finishes.



#### Options


`--grant-license-mode <grant-license-mode>`

Specifies whether a role should be granted on sign in. Default is
`on-sync`. Valid values are `on-login`, `on-sync`. If no value is
specified, `on-sync` is assumed and the default role will be grated when
the group is synchronized. For more information, see [Modifying user
roles with Grant role on sign
in](https://help.tableau.com/current/server/en-us/grant_role.htm#GrantRoleOnSignin).

`--no-publisher`

Deprecated. Use the `--role` option instead.

`--overwritesiterole`

Allows a user's site role to be overwritten with a less privileged one
when using `‑‑role`. By default, a user site role can be promoted when
using `‑‑role`, but cannot be demoted. Because the `‑‑overwritesiterole`
option will demote user site roles, use it with caution.

`--publisher`

Deprecated. Use the `--role` option instead.

`-r`, `--role`

Specifies a site role for users in the group. The default is
`Unlicensed`.

`--silent-progress`

Do not display progress messages for the command.



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`



##### version
----------------------------------------------------------------------------------------------------------------------------


Displays the version information for the current installation of the
tabcmd utility.

**Example**

`tabcmd version`



#####  Global options

The following options are used by all `tabcmd` commands. The `--server`,
`--user`, and `--password` options are required at least once to begin a
session. An authentication token is stored so subsequent commands can be
run without including these options. This token remains valid for five
minutes after the last command that used it.

`-h`, `--help`

Displays the help for the command.


`-c`, `--use-certificate`

Use client certificate to sign in. Required when mutual SSL is enabled.

For information about configuring the certificate, start with the
following topic appropriate for your Tableau Server OS:

-   **Windows:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/ssl_config_mutual.htm "Open topic in new browser tab")

-   **Linux:** [Configure Mutual SSL[(Link opens in a new
    window)]](https://help.tableau.com/current/server-linux/en-us/ssl_config_mutual.htm "Open topic in new browser tab")


`-s`, `--server`

The [Tableau Server] URL, which is required at
least once to begin session.

`-u`, `--user`

The [Tableau Server] username, which is required
at least once to begin session.

`-p`, `--password`

The [Tableau Server] password, which is required
at least once to begin session.

`--password-file`

Allows the password to be stored in the given `.txt` file rather than
the command line for increased security.

`-t`, `--site`

Indicates that the command applies to the site specified by the [Tableau
Server] site ID, surrounded by single quotes or
double quotes. To specify the Default site, use either an empty string
with single or double quotes (\'\' or \"\") or use Default in double
quotes (\"Default\"). Site ID is case-sensitive when using a cached
authentication token. If you do not match case you may be prompted for a
password even if the token is still valid.


`-x`, `--proxy`

Host:Port

Uses the specified HTTP proxy.


`--no-prompt`

When specified, the command will not prompt for a password. If no valid
password is provided the command will fail.


`--no-proxy`

When specified, an HTTP proxy will not be used.



`--no-certcheck`

When specified, tabcmd (the client) does not validate the server\'s SSL
certificate.


`--[no-]cookie`

When specified, the session ID is saved on login so subsequent commands
will not need to log in. Use the `no-` prefix to not save the session
ID. By default the session is saved.

`--timeout`

Waits the specified number of seconds for the server to complete
processing the command. By default the process will timeout in 30
seconds.

`--`

Specifies the end of options on the command line. You can use `--` to
indicate to `tabcmd` that anything that follows `--` should not be
interpreted as an option setting and can instead be interpreted as a
value for the command. This is useful if you need to specify a value in
the command that includes a hyphen. The following example shows how you
might use `--` in a `tabcmd` command, where `-430105/Sheet1` is a
required value for the `export` command.

`tabcmd export --csv -f "D:\export10.csv" -- -430105/Sheet1`
