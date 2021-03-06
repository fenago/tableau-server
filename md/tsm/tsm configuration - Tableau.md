

tsm configuration
=================
You can use the `tsm configuration` commands to get, set, and update
configuration key values.

##### \"Unknown key\" responses
------------------------------------------------------------------


Certain configuration keys will return an \"Unknown key\" response when
you attempt to get their current value, or set a new value. If this
happens, verify that you have the key spelled correctly, including
proper capitalization. To change the value, use the `--force-keys`
option on the `tsm configuration set` command. For a list of
configuration keys you can change, see [tsm configuration set
Options](https://help.tableau.com/current/server/en-us/cli_configuration-set_tsm.htm).

 



-   [tsm configuration
    get](https://help.tableau.com/current/server/en-us/cli_configuration_tsm.htm#TSMGet)
-   [tsm configuration
    list-dynamic-keys](https://help.tableau.com/current/server/en-us/cli_configuration_tsm.htm#TSMListDynamicKeys)
-   [tsm configuration
    set](https://help.tableau.com/current/server/en-us/cli_configuration_tsm.htm#TSMSet)


##### tsm configuration get
---------------------------------------------------------------------------------------------------------------------


View the current server configuration and topology.



#### Synopsis


`tsm configuration get --key <config.key> [global options]`



#### Option


-k, \--key

Required.

Get the current value of the specified configuration key.


##### tsm configuration list-dynamic-keys
---------------------------------------------------------------------------------


View all the configuration keys that can be configured dynamically
(without restarting Tableau Server).



#### Synopsis


`tsm configuration list-dynamic-keys [global options]`


##### tsm configuration set
---------------------------------------------------------------------------------------------------------------------


Set or import server configuration or topology.

Quotes around the `<config.key>` and the `<config_value>` are optional
unless there are spaces, in which case you must use quotes around the
key or value.

**Note:** After setting a configuration key value you must apply the
pending configuration changes using `tsm pending-changes apply`. Until
you do, the new value will not be used by Tableau or show up in the
results of a `tsm configuration get` command. You can view pending
changes using `tsm pending-changes list`. For more information, see [tsm
pending-changes](https://help.tableau.com/current/server/en-us/cli_pending-changes.htm).



#### Synopsis


`tsm configuration set --key <config.key> --value <config_value> [global options]`



#### Options


-k,\--key \<config.key\>

Required.

Configuration key.

-v,\--value \<config\_value\>

Required.

Configuration value.

-d

Optional.

Reset the configuration value to its default.

-frc, \--force-keys

Optional.

Force a key to be added to configuration even if it did not previously
exist.




##### Global options
---------------------------------------------------------------------------------------------------


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
