

tsm stop
========
You can use the `tsm stop` command to stop Tableau Server. If Tableau
Server is already stopped, this command does nothing.



#### Synopsis


`tsm stop [option] [global options]`



#### Options


\--ignore-node-status \<nodeID\>

Optional.

Ignore the status for the specified node or nodes when determining if
the server has stopped. Useful if removing a bad node. Separate multiple
nodes with commas.

**Note:** Option added in version 2020.1

\--request-timeout \<timeout in seconds\>

Optional.

Wait the specified amount of time for the command to finish. Default
value is 1800 (30 minutes).



##### Global options
------------------------------------------------------------------------------------------


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

