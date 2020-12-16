
tsm topology
============
Use the `tsm topology` commands to prepare File Store nodes for safe
removal or to put them back into read-write mode. You can also initiate
a repository failover, get a list of nodes or ports, get the bootstrap
configuration file required to add additional nodes to your cluster,
remove nodes, configure external repository, and external File Store.

When making changes to topology, you need to also apply those pending
changes. For more information, see [tsm
pending-changes](https://help.tableau.com/current/server/en-us/cli_pending-changes.htm).


-   [cleanup-coordination-service](https://help.tableau.com/current/server/en-us/cli_topology_tsm.htm#TSMCleanupCoordination)
-   [deploy-coordination-service](https://help.tableau.com/current/server/en-us/cli_topology_tsm.htm#TSMDeployCoordination)
-   external-services
    -   filestore
        -   [external-services storage
            disable](https://help.tableau.com/current/server/en-us/cli_topology_tsm.htm#TSMExternalStorageDisable)
        -   [tsm topology external-services storage
            enable](https://help.tableau.com/current/server/en-us/cli_topology_tsm.htm#TSMExternalStorageEnable){.MCXref
            .xref}
    -   [list](https://help.tableau.com/current/server/en-us/cli_topology_tsm.htm#tsmExteranalServicesList)
    -   repository
        -   [disable](https://help.tableau.com/current/server/en-us/cli_topology_tsm.htm#TSMExternalRepoDisable)
        -   [enable](https://help.tableau.com/current/server/en-us/cli_topology_tsm.htm#TSMExternalRepoEnable)
        -   [replace-host](https://help.tableau.com/current/server/en-us/cli_topology_tsm.htm#tsmExternalRepoReplaceHost)
-   [failover-repository](https://help.tableau.com/current/server/en-us/cli_topology_tsm.htm#TSMFailoverRepository)
-   filestore
    -   [decommission](https://help.tableau.com/current/server/en-us/cli_topology_tsm.htm#TSMDecommission)
    -   [recommission](https://help.tableau.com/current/server/en-us/cli_topology_tsm.htm#topology-recommission)
-   [list-nodes](https://help.tableau.com/current/server/en-us/cli_topology_tsm.htm#TSMListNodes)
-   [list-ports](https://help.tableau.com/current/server/en-us/cli_topology_tsm.htm#TSMListPorts)
-   nodes
    -   [get-bootstrap-file](https://help.tableau.com/current/server/en-us/cli_topology_tsm.htm#TSMGetBootstrap)
-   [remove-nodes](https://help.tableau.com/current/server/en-us/cli_topology_tsm.htm#TSMRemoveNodes)
-   [set-node-role](https://help.tableau.com/current/server/en-us/cli_topology_tsm.htm#TSMSetNodeRole)
-   [set-ports](https://help.tableau.com/current/server/en-us/cli_topology_tsm.htm#TSMSetPorts)
-   [set-process](https://help.tableau.com/current/server/en-us/cli_topology_tsm.htm#TSMSetProcess)
-   [toggle-coordination-service](https://help.tableau.com/current/server/en-us/cli_topology_tsm.htm#TSMToggleCoordination)




##### tsm topology cleanup-coordination-service
--------------------------------------------------------------------------------------


**Note:** Beginning with version 2020.1.0, all coordination service
ensemble commands require input for a \"y/n\" prompt confirming that a
server restart will take place. To run these commands without input,
include the `--ignore-prompt` option.

Use the `tsm topology cleanup-coordination-service` command to remove
the non-production [Tableau Server] Coordination
Service ensemble after you deploy a new ensemble. This command removes
the old Coordination Service instances on all nodes in the
non-production Coordination Service ensemble and is required after you
deploy a new Coordination Service ensemble. To learn more about
Coordination Service ensembles, see [Deploy a Coordination Service
Ensemble](https://help.tableau.com/current/server/en-us/distrib_ha_zk.htm) .

In version 2020.1.0 and later, the
`tsm topology deploy-coordination-service` command also removes the old
ensemble. There is no need to run this command separately unless the
deployment fails.



#### Synopsis


`tsm topology cleanup-coordination-service [option] [global options]`



#### Option


\--request-timeout \<timeout in seconds\>

Optional.

Wait the specified amount of time for the command to finish. Default
value is 2700 (45 minutes).



##### tsm topology deploy-coordination-service
------------------------------------------------------------------------------------


**Note:** Beginning with version 2020.1.0, all coordination service
ensemble commands require input for a \"y/n\" prompt confirming that a
server restart will take place. To run these commands without input,
include the `--ignore-prompt` option.

You can use the `tsm topology deploy-coordination-service` command to
deploy the [Tableau Server] Coordination Service.
This command deploys a Coordination Service ensemble, which is a set of
Coordination Service instances that run on specified nodes in your
server cluster. To learn more about Coordination Service ensembles,
including how many nodes in your cluster should have a Coordination
Service instance, see [Deploy a Coordination Service
Ensemble](https://help.tableau.com/current/server/en-us/distrib_ha_zk.htm) .

In version 2020.1.0 and later, the
`tsm topology deploy-coordination-service` command also removes the old
ensemble. There is no need to run the `cleanup-coordination-service`
command separately.



#### Synopsis


`tsm topology deploy-coordination-service --nodes <nodeID,nodeID,...> [option] [global-options]`



#### Options


-n, \--nodes \<nodeID,nodeID,\...\>

Required.

Node IDs of nodes to include in the new Coordination Service ensemble,
separated by commas. You can specify 1, 3, or 5 Coordination Service
nodes, depending on the total number of nodes in your cluster. For more
information, see [The Coordination Service
Quorum](https://help.tableau.com/current/server/en-us/distrib_ha_zk.htm#ZKquorum).

\--request-timeout \<timeout in seconds\>

Optional.

Wait the specified amount of time for the command to finish. Default
value is 2700 (45 minutes).

##### tsm topology external-services storage disable
----------------------------------------------------------------------------------------------


Configure Tableau Server to run File Store locally. Use this command to
disable External File Store and move the File Store data to your Tableau
Server.



#### Synopsis


``` {space="preserve"}
tsm topology external-services storage disable [options] [global options]
```



#### Options


-fsn \<nodeID, nodeID,\...\>

Required

Specify the nodes that you want to configure File Store. You can specify
more than one node. The data will be migrated to the first node in the
list and then replicated to other nodes.

For more information, see [Reconfigure File
Store](https://help.tableau.com/current/server/en-us/server_external_filestore_storage_reconfigure.htm) .


##### tsm topology external-services storage enable
--------------------------------------------------------------------------------------------


Configure Tableau Server with External File Store. External File Store
uses SAN or NAS to store File Store data.



#### Synopsis


``` {space="preserve"}
tsm topology external-services storage enable [options] [global options]
```



#### Options


-network-share

Required

Specify the name and path of the network share you want to use for your
External File Store.

For more information, see [Reconfigure File
Store](https://help.tableau.com/current/server/en-us/server_external_filestore_storage_reconfigure.htm) .




##### tsm topology external-services list
----------------------------------------------------------------------------------


Use the tsm topology external-service-list command to get a the service
that is used for Tableau Server External Repository. For example, if you
have configured Tableau Server to use Amazon RDS, you will see the
following message:

These externally configured services are in use by Tableau Server:

\- pgsql



#### Synopsis


    tsm topology external-service list [global options]



#### Option


There are no options for this command.



##### tsm topology external-services repository disable -n nodeN
-------------------------------------------------------------------------------------------------------


Use the tsm topology external-services repository disable command to
stop using the external repository and reconfigure the installation to
use a local repository. This will migrate the data to a local repository
and configure Tableau Server to use the local repository.



#### Synopsis


    tsm topology external-services repository disable -n nodeN



#### Option


-n, \--node-name \<nodeID\>

Required.

Specifies the node ID of the node where the repository should be moved
to.

**Important:** This does not stop or delete the RDS instance. For more
information on how to delete an RDS instance, see [Deleting a DB
Instance[(Link opens in a new
window)]](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_DeleteInstance.html#USER_DeleteInstance.NoSnapshot)
on the AWS web site.



##### tsm topology external-services repository enable
--------------------------------------------------------------------------------------------


Use the tsm topology external-services repository enable command to
configure Tableau Server to use an external repository. This command can
be used during installation of a new Tableau Server to configure the
external repository. If this command is run on an already existing and
running Tableau Server, it will migrate the data from the local node to
the external repository and configure Tableau Server to use the external
repository after the migration is complete.



#### Synopsis


    tsm topology external-services repository enable -f <filename>.json -c <ssl certificate file>.pem



#### Options


-f \<file name\>

Required.

Full path and file name where the configuration file is saved. For more
information, see [Re-Configure Tableau Server
Repository](https://help.tableau.com/current/server/en-us/server_external_repo_reconfigure.htm).

-c \<ssl certificate file\>

Required.

You must use SSL if you are using Amazon RDS for your external
repository. Download the .pem file and specify the .pem file for use
with this option. For more information on how to get the .pem file, see
[Using SSL to Encrypt a Connection to a DB Instance[(Link opens in a new
window)]](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_PostgreSQL.html#PostgreSQL.Concepts.General.SSL).



##### tsm topology external-services repository replace-host
-------------------------------------------------------------------------------------------------------


This command updates Tableau Server configuration settings to use the
specified external repository. Use the tsm topology external-services
repository replace-host command to reconfigure Tableau Server to use the
new external repository immediately without moving data to it from your
current external repository. You may need to manually migrate the data.
You should only do this after you have fully evaluated and understand
the impact of the potential data loss.

This command can be used in the following scenarios:

-   Planned expiration of the SSL certificates used by RDS instances:
    RDS instances need to be updated with the new certificates, and
    Tableau Server needs to be configured to use the new certificate
    file to connect to the RDS instance.

-   Disaster recovery: Use this to connect to a new RDS instance in
    disaster recovery scenarios. For more information, see [Create a
    PostgreSQL DB Instance on AWS Relational Database Service
    (RDS)](https://help.tableau.com/current/server/en-us/server_external_repo_configure_RDS.htm#disaster-recovery-postgreSQL_DB){.MCXref
    .xref}

 



#### Synopsis


    tsm topology external-services repository enable -f <filename>.json -c <ssl certificate file>.pem



#### Options


-f \<file name\>

Required.

Full path and file name where the configuration file is saved. For more
information, see [Re-Configure Tableau Server
Repository](https://help.tableau.com/current/server/en-us/server_external_repo_reconfigure.htm).

-c \<ssl certificate file\>

Optional.

The certificate file is the certificate to be imported to allow
connections to the instance. For RDS, this is the CA cert used to sign
the certificate of the instance. This is usually the latest root
certificate **rds-ca-XXXX-root.pem** file. Use this parameter to update
Tableu server if the certificate has changed on the RDS instance.

For more information, see [Using SSL/TLS to Encrypt a Connection to a DB
Instance](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.SSL.html "Using SSL/TLS to Encrypt a Connection to a DB Instance").

For more information on how to get the .pem file, see [Using SSL to
Encrypt a Connection to a DB Instance[(Link opens in a new
window)]](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_PostgreSQL.html#PostgreSQL.Concepts.General.SSL).

\--ignore-prompt

Optional.

Run this command without prompts.



##### tsm topology failover-repository
----------------------------------------------------------------------------


You can use the `tsm topology failover-repository` to manually initiate
a repository failover from the current active repository to the second,
passive repository.

The `tsm topology failover-repository` command is persistent. The
failover repository remains the active repository until you issue the
command again, or, if Tableau Server is configured for it, until
automatic failover occurs. If you have a preferred active repository
configured, use the `--preferred `option to switch back to that
repository. For more information about configuring a preferred active
repository, see [Tableau Server
Repository](https://help.tableau.com/current/server/en-us/server_process_repository.htm). If Tableau Server is configured for high availability, failover
of the repository is automatic when necessary. Use the
failover-repository command to manually fail over the repository.



#### Synopsis


`tsm topology failover-repository --preferred | --target <node_id> [global options]`



#### Options


-r, \--preferred

Required if -t or \--target is not used.

Use the configured preferred node as the target for repository failover.

\--request-timeout \<timeout in seconds\>

Optional.

Wait the specified amount of time for the command to finish. Default
value is 1800 (30 minutes).

-t, \--target \<node\_id\>

Required if -r or \--preferred is not used.

The node id of the target node onto which failover will occur. Find the
node id by using the `tsm topology list-nodes` command.



##### tsm topology filestore decommission
-------------------------------------------------------------------------


You must use the `tsm topology filestore decommission` command to
prepare a file store node or nodes for safe removal. This command puts
the specified nodes into read-only mode and ensures there is no unique
content on the specified nodes.

If decommissioning results in a single file store node, you must use the
`--override` option or the decommission will fail.



#### Synopsis


`tsm topology filestore decommission  --nodes <nodeID,nodeID,...> [options] [global options]`



#### Options


-n, \--nodes \<nodeID,nodeID,\...\>

Required.

List of one or more nodes to decommission, specified by node ID and
separated by commas.

\--delete-filestore

Optional.

Forces the removal of the file store, even if it has not been
decommissioned. You should only use this option if the node the file
store is on is in a error state and decommissioning cannot be done. Any
unique files on the node will be permanently deleted.

-o, \--override

Optional.

Overrides warnings or failures that would normally occur if removing the
target File Store node would reduce the number of remaining file store
nodes to one.

\--request-timeout \<timeout in seconds\>

Optional.

Wait the specified amount of time for the command to finish. Default
value is 1800 (30 minutes).



##### tsm topology filestore recommission
-------------------------------------------------------------------------------


Use the `tsm topology filestore recommission` command to revert any
decommissioned nodes back to read-write mode.



#### Synopsis


`tsm topology filestore recommission  --nodes <nodeID,nodeID,...> [global options]`



#### Options


-n, \--nodes \<nodeID,nodeID,\...\>

Required.

List of one or more nodes to recommission, specified by node ID and
separated by commas.



##### tsm topology list-nodes
------------------------------------------------------------------------------------------------------------------------


Display the nodes in the cluster and (optionally) the services on each
node.



#### Synopsis


``` {space="preserve"}
tsm topology list-nodes [options] [global options]
```



#### Options


-v, \--verbose

Optional.

Shows each node ID, the node role (for more information, see
`set-node-role` below), the node address, and the processes on each
node.

 



##### tsm topology list-ports
------------------------------------------------------------------------------------------------------------------------


Display the ports in the cluster.



#### Synopsis


``` {space="preserve"}
tsm topology list-ports [options] [global options]
```



#### Options


\--node-name \<nodeID\>

Optional.

Specify the node to list ports for.

\--service-name

Optional.

Specify the service to list ports for.

 



##### tsm topology nodes get-bootstrap-file
---------------------------------------------------------------------------


You can use the `tsm topology nodes get-bootstrap-file` command to get
the bootstrap file that is required to add a new node to the cluster.

**Important**: The bootstrap file contains a copy of the master keystore
file used for encrypting the configuration secrets. The file can also
embedded credentials which are valid for a predetermined amount of time
(see
[tabadmincontroller.auth.expiration.minutes](https://help.tableau.com/current/server/en-us/cli_configuration-set_tsm.htm#tabadminctrlrauthexpire)) and serve as a session cookie. We strongly recommend that you
take additional measures to secure the bootstrap file using mechanisms
as described in [Securing secrets for import and export
operations](https://help.tableau.com/current/server/en-us/security_secret_storage.htm#Securing).



#### Synopsis


    tsm topology nodes get-bootstrap-file --file <path\file>.json [global options]



#### Options


-f,\--file \<file\>

Required.

Full path and file name where the configuration file will be saved. If a
duplicate file exists it will be overwritten.

-nec,\--no-embedded-credential

Optional.

Added in version 2019.3.

By default embedded credentials are included in the bootstrap file. Use
this option if credentials should not be included in the bootstrap file.
Embedded credentials are temporary, and expire based on the value of the
`tabadmincontroller.auth.expiration.minutes`configuration key, by
default 120 minutes.

**Note:** You can disable the ability to include embedded credentials at
the server level, using a configuration option. For more information,
see
[features.PasswordlessBootstrapInit](https://help.tableau.com/current/server/en-us/cli_configuration-set_tsm.htm#pwdlessbootstrap).

 



##### tsm topology remove-nodes
----------------------------------------------------------------------------------------------------------------------------


Remove nodes from the cluster.

To complete removal of a node, you also must run the
`tsm pending-changes apply` command. Some scenarios require that you
move or redeploy processes before removing nodes. See [Remove a
Node](https://help.tableau.com/current/server/en-us/distrib_worker_remove.htm#top).

If you remove a node and want to re-add it to the cluster, you need to
first run the obliterate script to clean Tableau off it, then reinstall
the node using the normal process for adding a new node. For more
information, see [Remove Tableau Server from Your
Computer](https://help.tableau.com/current/server/en-us/remove_tableau.htm) and [Install and Configure Additional
Nodes](https://help.tableau.com/current/server/en-us/install_additional_nodes.htm).

**Note**: To remove a node from a cluster it must have been configured
with a process at some point in the past. If you are removing a node on
which you\'ve not configured any processes, then you must add a process
on it, run `tsm pending-changes apply`, and then remove the node.



#### Synopsis


``` {space="preserve"}
tsm topology remove-nodes --nodes <nodeID,nodeID,...> [global options]
```



#### Options


-n, \--nodes \<nodeID,nodeID,\...\>

Required.

Specify the node or nodes to remove. If specifying multiple nodes,
separate node IDs with a comma.

 



##### tsm topology set-node-role
---------------------------------------------------------------


Set the Backgrounder and Extract Queries node roles. This determines the
type of tasks that will be performed on the nodes. The following node
roles are useful if you have a multi-node cluster and requires Add-on
licenses. For more information, see [Workload Management through Node
Roles](https://help.tableau.com/current/server/en-us/server_node_roles.htm).

**Note:** Making configurations to node roles require a restart of the
server and will require some downtime. For more information, see [tsm
pending-changes](https://help.tableau.com/current/server/en-us/cli_pending-changes.htm).



#### Synopsis


``` {space="preserve"}
tsm topology set-node-role [options] [global options]
```



#### Options


-n, \--nodes \<nodeID,nodeID,\...\>

Required.

List of one or more nodes to set node roles for, specified by node ID
and separated by commas and without spaces between nodes.

-r \--role
\<all-jobs,flows,no-flows,extract-refreshes,subscriptions,extract-refreshes-and-subscriptions,no-extract-refreshes,no-subscriptions,no-extract-refreshes-and-subscriptions,extract-queries\>

Required

Sets the role for the nodes specified. The valid values for this option
are:

-   all-jobs: Backgrounder will run all types of jobs.

-   flows :Backgrounder will run only flow run jobs.

-   no-flows: Backgrounder will not run flow run jobs.

-   extract-refreshes: Backgrounder will run only extract refresh jobs.
    This includes, incremental refreshes, full refreshes, encryption and
    decryption of all extracts including extracts that flow outputs
    generate.

-   subscriptions: Backgrounder will run only subscription jobs.

-   extract-refreshes-and-subscriptions: Backgrounder will run
    extract-refreshes, encryption and decryption of all extracts
    including extracts that flow outputs create, and subscription jobs.

-   no-extract-refreshes: Backgrounder will run all jobs except
    extract-refreshes, extract encryption and decryption including
    extracts created from flow outputs.

-   no-subscriptions: Backgrounder will run all jobs except
    subscriptions.

-   no-extract-refreshes-and-subscriptions: Backgrounder will run all
    jobs except extract-refreshes, encryption and decryption of all
    extracts including extracts created from flow outputs, and
    subscriptions.

-   extract-queries: The nodes selected will run as all-jobs and will
    prioritize the processing of extract queries.



##### tsm topology set-ports
----------------------------------------------------------------------------------------------------------------------


Set the ports for a service instance.



#### Synopsis


``` {space="preserve"}
tsm topology set-ports --node-name <nodeID> --port-name <port_name> --port-value <port_value> [options] [global options]
```



#### Options


-i, \--instance \<instance\_id\>

Optional.

Specifies the instance id of the service. Defaults to 0 (zero) if not
specified.

-n, \--node-name \<nodeID\>

Required.

Specifies the node ID of the node.

-pn, \--port-name \<port\_name\>

Required.

The name of the port to be set, in this format:
`service_name:port_type`. If no port type is specified, the primary port
is assumed. For port name syntax, see [Dynamically mapped
ports](https://help.tableau.com/current/server/en-us/ports.htm#Dynamica).

-pv, \--port-value \<port\_value\>

Required.

The port to set.

-r, \--restart

Optional.

Suppress the prompt for restart and restart [Tableau
Server] when necessary.

 



##### tsm topology set-process
--------------------------------------------------------------------------------------------------------------------------


Set the number of instances of a process on a node. If a node already
has the specified process, the number is updated to match the specified
count.

-   You can only set one process at a time. If you specify more than one
    process, any process after the first one will be silently ignored.
-   You must set a process one node at a time. If you specify more than
    one node, the command will display an \"invalid node name\" error.

When you update the number of processes on nodes, you also need to apply
pending changes. In most cases this also requires a server restart (you
will be prompted), but there are special cases where you can make
dynamic topology changes without needing to restart the server. For more
information, see [Tableau Server Dynamic Topology
Changes](https://help.tableau.com/current/server/en-us/server_process_hot_topo.htm).

**Note:** For a complete list of process names, see [Tableau Server
Processes](https://help.tableau.com/current/server/en-us/processes.htm).



#### Synopsis


``` {space="preserve"}
tsm topology set-process --count <process_count> --node <nodeID> --process <process_name> [global options]
```



#### Options


-c, \--count \<process\_count\>

Required.

The process count (number of instances) to set.

-n, \--node \<nodeID\>

Required.

Specifies the node ID of the node on which to set the process.

-pr, \--process \<process\_name\>

Required.

The name of the process to be set.

 



##### tsm topology toggle-coordination-service
------------------------------------------------------------------------------------


**Note:** Beginning with version 2020.1.0, all coordination service
ensemble commands require input for a \"y/n\" prompt confirming that a
server restart will take place. To run these commands without input,
include the `--ignore-prompt` option.

You can use the `tsm topology toggle-coordination-service` command to
switch between coordination service ensembles. To learn more about
Coordination Service ensembles, see [Deploy a Coordination Service
Ensemble](https://help.tableau.com/current/server/en-us/distrib_ha_zk.htm) .

In version 2020.1.0 and later, the
`tsm topology deploy-coordination-service` command also switches to the
new ensemble. There is no need to run this command separately.



#### Synopsis


``` {space="preserve"}
tsm topology toggle-coordination-service [option] [global options]
```



#### Option


\--request-timeout \<timeout in seconds\>

Optional.

Wait the specified amount of time for the command to finish. Default
value is 1800 (30 minutes).



##### Global options
----------------------------------------------------------------------------------------------


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
