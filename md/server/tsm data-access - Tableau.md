

tsm data-access
===============
You can use the `tsm data-access` commands to configure data caching,
enable or disable data repository access, enable SAML for single
sign-on, and configure settings for Web Data Connectors (WDCs).


-   caching
    -   [data-access caching
        list](https://help.tableau.com/current/server/en-us/cli_data-access.htm#caching-list)
    -   [data-access caching
        set](https://help.tableau.com/current/server/en-us/cli_data-access.htm#caching-set)
-   repository
    -   [repository-access
        disable](https://help.tableau.com/current/server/en-us/cli_data-access.htm#repository-access-disable)
    -   [repository-access
        enable](https://help.tableau.com/current/server/en-us/cli_data-access.htm#repository-access-enable)
    -   [repository-access
        list](https://help.tableau.com/current/server/en-us/cli_data-access.htm#repository-access-list)
-   set-saml-delegation
    -   [set-saml-delegation
        configure](https://help.tableau.com/current/server/en-us/cli_data-access.htm#set-saml-config)
    -   [set-saml-delegation
        disable](https://help.tableau.com/current/server/en-us/cli_data-access.htm#set-saml-disable)
    -   [set-saml-delegation
        enable](https://help.tableau.com/current/server/en-us/cli_data-access.htm#set-saml-enable)
-   web-data-connectors
    -   [web-data-connectors
        add](https://help.tableau.com/current/server/en-us/cli_data-access.htm#web-data-connectors-add)
    -   [web-data-connectors
        allow](https://help.tableau.com/current/server/en-us/cli_data-access.htm#web-data-connectors-allow)
    -   [web-data-connectors
        delete](https://help.tableau.com/current/server/en-us/cli_data-access.htm#web-data-connectors-delete)
    -   [web-data-connectors
        list](https://help.tableau.com/current/server/en-us/cli_data-access.htm#web-data-connectors-list)


##### tsm data-access caching list
----------------------------------------------------------------------------------------------------------------------------


Displays data connection caching settings. To learn more about data
connection caching settings, see [Configure Data
Cache](https://help.tableau.com/current/server/en-us/config_cache.htm).



#### Synopsis


`tsm data-access caching list [global options]`


Sets data connection caching settings. To learn more about data
connection caching settings, see [Configure Data
Cache](https://help.tableau.com/current/server/en-us/config_cache.htm).



#### Synopsis


`tsm data-access caching set [options] [global options]`



#### Options


-r, \--refresh-frequency

Optional.

Sets the frequency to refresh cached data with a new query to the
underlying data source. You can specify a number to define the maximum
number of minutes that data should be cached. You can also specify
**low** to cache and reuse data for as long as possible, or **always**
(equivalent to **0**) to refresh data each time that a page is loaded.
If this option is not specified, it defaults to **low**.



##### tsm data-access repository-access disable
----------------------------------------------------------------------------------------


Disable external access to the Tableau PostgreSQL database for the
default remote user. This will not disable access from localhost.



#### Synopsis


`tsm data-access repository-access disable [options] [global options]`



#### Options


\--repository-username \<username\>

Required.

The username, either **tableau** or **readonly**, with access to the
data repository.

\--request-timeout \<timeout in seconds\>

Optional.

Wait the specified amount of time for the command to finish. Default
value is 1500 (25 minutes).

\--ignore-prompt

Optional.

Suppress the prompt for restart and restart [Tableau Server].

**tsm data-access repository-access enable**

Enables access to the Tableau PostgreSQL database.

By default, PostgreSQL traffic uses port 8060 (TCP). If you are running
a local firewall, be sure to allow traffic for this port. To change the
PostgreSQL port, see [Ports that are not dynamically
mapped](https://help.tableau.com/current/server/en-us/ports.htm#PortsNotDynamic).



#### Synopsis


`tsm data-access repository-access enable [options] [global options]`



#### Options


\--repository-password \<password\>

Required.

Sets (or changes) the password to access the data repository for the
specified username.

\--repository-username \<username\>

Required.

The username, either **tableau** or **readonly**, with access to the
data repository.

\--request-timeout \<timeout in seconds\>

Optional.

Wait the specified amount of time for the command to finish. Default
value is 1500 (25 minutes).

\--ignore-prompt

Optional.

Suppress the prompt for restart and restart [Tableau
Server].



##### tsm data-access repository-access list
----------------------------------------------------------------------------------


Lists users who have access to the Tableau PostgreSQL database.



#### Synopsis


`tsm data-access repository-access list [global options]`



##### tsm data-access set-saml-delegation configure
----------------------------------------------------------------------------------


Setup single sign-on for SAML SAP HANA so that [Tableau
Server] functions as an Identity Provider (IdP)
that provides single sign-on for users making SAP HANA data connections.



#### Synopsis


`tsm  data-access set-saml-delegation configure [options] [global options]`



#### Options


-kf, \--cert-key \<cert-key\>

Optional.

The SAML certificate key file.

-cf, \--cert-file \<file-path\>

Optional.

The location of the SAML certificate file.

-uf, \--username-format \<username-format\>

Optional.

Username format. Valid format keys are: \'username\',
\'domain\_and\_username\', and \'email\'.

-uc,\--username-case \<username-case\>

Optional.

Username case. Valid case keys are: \'lower\', \'upper\', and
\'preserve\'.

.



##### tsm data-access set-saml-delegation disable
---------------------------------------------------------------------------------


Disable single sign-on for SAML SAP HANA.



#### Synopsis


`tsm  data-access set-saml-delegation disable [global options]`



##### tsm data-access set-saml-delegation enable
-------------------------------------------------------------------------------


Enable single sign-on for SAML SAP HANA.



#### Synopsis


`tsm  data-access set-saml-delegation enable [global options]`



##### tsm data-access web-data-connectors add
------------------------------------------------------------------------------------


Add a web data connector (WDC) to the WDC safe list.



#### Synopsis


`tsm data-access web-data-connectors add [options] [global options]`



#### Options


-n, \--name \<name\>

Required.

The name for the WDC that will be displayed in the Tableau Server data
source list. This name must be enclosed in single quotes (\') or double
quotes (\"). Use double quotes (\") if the name includes a space.

-sec, \--secondary \<secondary-URL-1\>, \<secondary-URL-2\>

Optional.

A comma-delimited list of URLs that indicates which domains the
connector can make requests to or receive data from. Do not enclose the
URLs in quotes. To add an entire domain to this secondary safe list, you
can use a wildcard expression `(.*)`. On Windows, be sure to include the
parentheses `( )` as part of the expression, as in the following
example: `https://www.example.com/(.*)`

\--url \<URL\>

Required.

The URL for the WDC (formatted as `<scheme>://<host>:<port>/<path>`, for
example `https://www.tableau.com:80/example/`). For many WDCs, the
\<port\> value is 443 or 80, but you can check the value for your
connector by looking at the data source details on Tableau Server or
Tableau Online.



##### tsm data-access web-data-connectors allow
----------------------------------------------------------------------------------------


Enable or disable WDC refreshes. Also, enable or disable the use of WDCs
on Tableau Server.



#### Synopsis


`tsm data-access web-data-connectors allow [options] [global options]`



#### Options


-r, \--refreshes \<refreshes-allowed\>

Optional.

Set to `false` to disallow WDC refreshes. Defaults to `true`.

-t, \--type \<WDC-allowed\>

Optional.

Set to `none` to disallow the use of WDCs on Tableau Server (and omit
WDCs from backups). Defaults to `all`, which allows the use of WDCs.



##### tsm data-access web-data-connectors delete
------------------------------------------------------------------------------------------


Delete a specified WDC, or all WDCs, from the Tableau Server safe list.



#### Synopsis


`tsm data-access web-data-connectors delete [options] [global options]`



#### Options


\--all

Optional.

This option will delete all WDCs.

\--url \<URL\>

Optional.

The URL for the WDC to delete.



##### tsm data-access web-data-connectors list
--------------------------------------------------------------------------------------


List all WDCs currently on the safe list.



#### Synopsis


`tsm data-access web-data-connectors list [options] [global options]`



#### Options




##### Global options
---------------------------------------------------------------------------------------------


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
