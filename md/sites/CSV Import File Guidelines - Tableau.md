

CSV Import File Guidelines
==========================
You can automate adding users by creating a comma-separated values (CSV)
file with user information and then importing the file. You can include
attributes in the CSV file, such as license level and the publishing
access, to apply to the users at the same time you import them.


To import users, you can use the server or site administration pages or
the `tabcmd` utility. Using `tabcmd` provides an option for assigning a
site role to all users in the CSV file. For information, see [Import
Users](https://help.tableau.com/current/server/en-us/users_import.htm) or [createsiteusers
filename.csv](https://help.tableau.com/current/server/en-us/tabcmd_cmd.htm#idd1b7729f-dd20-475a-96f6-17fcd2577894).

You can import users at the site or server level. If you import users to
the server (not to a specific site), the users aren't assigned to a site
and are imported as Unlicensed.
:::

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/csvguidelines.htm#){.heading-item__link .print-hidden} CSV file format requirements
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

When you create the CSV file for importing users, make sure that the
file meets the following formatting requirements:

-   The file does not include column headings. [Tableau
    Server] assumes that every line in the file
    represents a user.

-   The file is in UTF-8 format, and includes the byte-order mark (BOM).

-   Character encodings such as BIG-5 have been converted to UTF-8. You
    can do this by opening the file in a text editor and using the [Save
    As] command.

-   If a user name includes an @ character that represents anything
    other than a domain separator, you need to refer to the symbol using
    the hexadecimal format: `\0x40`

    For example, `user@fremont@mycompany.com` should be
    `user\0x40fremont@mycompany.com`

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/csvguidelines.htm#){.heading-item__link .print-hidden} Required columns in the CSV file
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

The following values are required for each user:

-   User name

-   Password: If Tableau Server is configured to use Active Directory
    authentication, there must be a `Password` column, but the column
    itself should be empty. If the server is using local authentication,
    you must provide passwords for new users.


<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/csvguidelines.htm#){.heading-item__link .print-hidden} Additional import file options
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

The CSV file can contain the following fields, in the order shown here:

-   User name. The user name. If the server is configured to use Active
    Directory, this value must match a user defined in Active Directory.
    If the user name is not unique across domains, you must include the
    domain as part of the user name (for example, `example\Adam` or
    `adam@example`). This is the only required field.

-   Password. A password for the user. If the server is configured to
    use Active Directory, this value is not used.

-   Display name. The display name is part of the information used to
    identify a user on the server. If the user's display name is already
    in use, Tableau Server updates the existing user information with
    the settings in the CSV file. If the server is configured using
    Active Directory, this value is not used.

-   License level. This can be [Creator],
    [Explorer], [Viewer], or
    [Unlicensed].

-   Administrator level ([System], [Site], or
    [None]). This setting determines whether the user is
    imported as an administrator.

    If you are using the web UI to import users, you can set the
    administrator site role to [System] only if you import
    the file at the server (All Sites) level. If you are signed in to a
    specific site, and if the administrator column for a user in the CSV
    file is set to [System], Tableau Server imports the user
    as a site administrator.

-   Publishing capability (**yes/true/1** or **no/false/0**). If you are
    using the web UI, the publisher setting is used only if you import
    while signed in to a specific site. If you import users at the
    server (All Sites) level, this value isn\'t used.

-   Email address. The email address is part of the information used to
    identify a user on the server. If the email address is already in
    use, Tableau Server updates the existing user information with the
    settings in the CSV file.

The order of the columns is significant. The first column is treated as
the user name, the second as the password, the third as display name,
and so on, regardless of the content in the columns. If you omit values
for a field, you must still include the field's comma delimiter.

<div>

<div>

#### Improve performance for large CSV files passed through tabcmd

</div>

A server administrator can enable server settings that help to improve
performance for importing large CSV files through tabcmd commands. You
can do this using the `tsm configuraiton set` command with the following
options:

-   `vizportal.csv_user_mgmt.index_site_users`

-   `vizportal.csv_user_mgmt.bulk_index_users`

-   `searchserver.index.bulk_query_user_groups`

Essentially, these options index users after the CSV file is processed,
instead of one-by-one as they are added to the server's database. This
reduces the number of calls to the database and the memory required to
process the file. These `tsm configuration set` options apply to the
`tabcmd createsiteusers`, `deletesiteusers`, `addusers`, and
`removeusers` commands.

For descriptions for these settings, see [tsm configuration set
Options](https://help.tableau.com/current/server/en-us/cli_configuration-set_tsm.htm).

</div>

<div>

####  Notes

</div>

-   If you are not signed in to a specific site and are importing users
    at the server level, you can assign only the Server Administrator
    and Unlicensed site roles.

-   If you have a user-based server installation, and if adding users
    would exceed the number of users allowed by your license, the users
    are added as unlicensed users.

-   If you use `tabcmd` and specify the license, but importing users
    would exceed your license limits, users are imported as Unlicensed.
:::

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/csvguidelines.htm#){.heading-item__link .print-hidden} CSV settings and site roles {#settings_and_site_roles}
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

The license level, administrator, and publishing settings for a user
determine how the user\'s site role is set during the import process.
The following table shows how the settings are converted to site roles.

+---------------------------+------------------------------------------+
| CSV settings              | Site role                                |
+===========================+==========================================+
| License level=(any)       | Server Administrator. This setting       |
|                           | applies to Tableau Server only, and it   |
| Administrator=System\     | is valid only if you are importing users |
|                           | while managing the server (that is, not  |
| Publisher=true            | signed in to a specific site).           |
|                           |                                          |
|                           | The Server Administrator site role       |
|                           | always takes a Creator license if one is |
|                           | available. If no Creator license is      |
|                           | available, see [Troubleshoot             |
|                           | Licensing](https://help.tableau.com/curr |
|                           | ent/server/en-us/unlicensed.htm){.MCXref |
|                           | .xref} to learn about the way Tableau    |
|                           | Server handles this.                     |
+---------------------------+------------------------------------------+
| License level=Creator or  | Site Administrator Creator or Site       |
| Explorer                  | Administrator Explorer. This setting is  |
|                           | valid only if you are importing users    |
| Administrator=Site        | while signed in to a specific site.      |
|                           |                                          |
| Publisher=true            |                                          |
+---------------------------+------------------------------------------+
| License level=Creator\    | Creator                                  |
|                           |                                          |
| Administrator=None\       |                                          |
|                           |                                          |
| Publisher=true            |                                          |
+---------------------------+------------------------------------------+
| License level=Explorer\   | Explorer (Can Publish)                   |
|                           |                                          |
| Administrator=None\       |                                          |
|                           |                                          |
| Publisher=true            |                                          |
+---------------------------+------------------------------------------+
| License level=Explorer\   | Explorer                                 |
|                           |                                          |
| Administrator=None\       |                                          |
|                           |                                          |
| Publisher=false           |                                          |
+---------------------------+------------------------------------------+
| License level=Viewer\     | Viewer                                   |
|                           |                                          |
| Administrator=None\       |                                          |
|                           |                                          |
| Publisher=false           |                                          |
+---------------------------+------------------------------------------+
| License level=Unlicensed\ | Unlicensed                               |
|                           |                                          |
| Administrator=None\       |                                          |
|                           |                                          |
| Publisher=false           |                                          |
+---------------------------+------------------------------------------+


<div>

####  CSV import example for Tableau Server

</div>

The following example shows a CSV file that contains information for
several users.


henryw,henrypassword,Henry Wilson,Creator,None,yes,henryw\@example.com\
freds,fredpassword,Fred Suzuki,Viewer,None,no,freds\@example.com\
alanw,alanpassword,Alan Wang,Explorer,Site,yes,alanw\@example.com\
michellek,michellepassword,Michelle
Kim,Creator,System,yes,michellek\@example.com
:::

If you import this file while managing a site, four users are added to
that site. The `Administrator` setting for user Michelle is `System`.
However, because you are importing the users into a site, Tableau Server
give Michelle the Site Administrator Creator site role. Three of the
users are allowed to publish.

If you import this file while managing the server, four users are added
to the server, but they are not added to any site. Only one user is
imported as a server administrator; the rest are set to Unlicensed.
