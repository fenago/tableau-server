

tsm user-identity-store
=======================

::: {.caption .article__tags .content-only-hidden}
[Version: 2020.3]{.article__tags--version}\
[]{.article__tags--applies-to}\
[]{.article__tags--role}
:::

::: {#content-body}
::: {#mc-main-content role="main"}
You can use the `tsm user-identity-store` commands to modify the
settings of the identity store for Tableau Server after the initial
configuration.

The initial configuration of the identity store is part of the
installation process. See [Configure Initial Node
Settings](https://help.tableau.com/current/server/en-us/config_general.htm){.MCXref
.xref}.

For introduction to identity store concepts, see [Identity
Store](https://help.tableau.com/current/server/en-us/plan_identity_store.htm){.MCXref
.xref}.

For LDAP/Active Directory configuration reference table, see [External
Identity Store Configuration
Reference](https://help.tableau.com/current/server/en-us/ldap_config.htm){.MCXref
.xref}.

::: {.miniToc}
-   [get-group-mappings](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#TSMGroupMap)
-   [get-user-mappings](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#TSMUserMap)
-   [list](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#TSMUIList)
-   [set-connection](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#TSMSetConnection)
-   [set-group-mappings](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#TSMSetGroupMap)
-   [set-user-mappings](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#TSMSetUserMap)
-   [verify-group-mappings](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#TSMverify-group-mappings)
-   [verify-user-mappings](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#TSMIDverify-user-mappings__%5Boptions%5D)
:::

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#){.heading-item__link .print-hidden} []{#TSMGroupMap}tsm user-identity-store get-group-mappings \[options\] {#tsm-useridentitystore-getgroupmappings-options}
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Displays identity store group mappings.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#){.heading-item__link .print-hidden} Synopsis

</div>

``` {space="preserve"}
tsm user-identity-store get-group-mappings [global options]
```

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#){.heading-item__link .print-hidden} []{#TSMUserMap}tsm user-identity-store get-user-mappings \[options\] {#tsm-useridentitystore-getusermappings-options}
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Displays identity store user mappings.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#){.heading-item__link .print-hidden} Synopsis {#synopsis1}

</div>

``` {space="preserve"}
tsm user-identity-store get-user-mappings [global options]
```

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#){.heading-item__link .print-hidden} []{#TSMUIList}tsm user-identity-store list \[options\] {#tsm-useridentitystore-list-options}
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Lists user-identity configuration.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#){.heading-item__link .print-hidden} Synopsis {#synopsis2}

</div>

``` {space="preserve"}
tsm user-identity-store list [options] [global options]
```

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#){.heading-item__link .print-hidden} Options

</div>

-v, \--verbose

Optional.

Lists all configuration parameters.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#){.heading-item__link .print-hidden} []{#TSMSetConnection}tsm user-identity-store set-connection \[options\] {#tsm-useridentitystore-setconnection--options}
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Sets identity store connection parameters.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#){.heading-item__link .print-hidden} Synopsis {#synopsis3}

</div>

``` {space="preserve"}
tsm user-identity-store set-connection --kerbkeytab <kerbkeytab> [options] [global options]
```

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#){.heading-item__link .print-hidden} Options {#options1}

</div>

-b,\--bind \<username and password \| Kerberos\>

Optional.

Set LDAP bind type.

-d,\--domain \<domain\>

Optional.

Domain name.

-hn,\--hostname \<hostname\>

Optional.

The hostname of the LDAP server. You can enter a hostname or an IP
address for this value. The host that you specify here will be used for
user/group queries on the primary domain. In the case where user/group
queries are in other domains, Tableau Server will query DNS to identify
the appropriate domain controller.

-kc,\--kerbconfig \<kerbconfig\>

Optional.

Kerberos configuration file path.

-kp,\--kerbprincipal \<kerbprincipal\>

Optional.

Kerberos Principal.

-kt,\--kerbkeytab \<kerbkeytab\>

Required.

Kerberos keytab file path.

-l,\--port \<port\>

Optional.

Set LDAP Port value.

-lp,\--ldappassword \<ldappassword\>

Optional.

LDAP Password.

-lu,\--ldapusername \<ldapusername\>

Optional.

Set LDAP Username value.

-n,\--nickname \<nickname\>

Optional.

NetBIOS name (nickname).

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#){.heading-item__link .print-hidden} []{#TSMSetGroupMap}tsm user-identity-store set-group-mappings \[options\] {#tsm-useridentitystore-setgroupmappings--options}
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Sets identity store group mappings and configures LDAP directories that
implement an arbitrary or custom schema.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#){.heading-item__link .print-hidden} Synopsis {#synopsis4}

</div>

``` {space="preserve"}
tsm user-identity-store set-group-mappings [options] [global options]
```

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#){.heading-item__link .print-hidden} Options {#options2}

</div>

-b,\--basefilter \<groupbasefilter\>

Optional.

Set group BaseFilter value.

-cn,\--classnames \<group\_classnames\>

Optional.

Override default user classname values (contains \"group\" string) with
the values you set here. You can provide multiple classnames separated
by commas.

-d,\--description \<description\>

Optional.

Group description.

-e,\--groupemail \<groupemail\>

Optional.

Group email value.

-m,\--member \<member\>

Optional.

Set the group members.

-n,\--groupname \<groupname\>

Optional.

Name of the group.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#){.heading-item__link .print-hidden} []{#TSMSetUserMap}tsm user-identity-store set-user-mappings \[options\] {#tsm-useridentitystore-setusermappings--options}
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Sets identity store user mappings and configures LDAP directories that
implement an arbitrary or custom schema.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#){.heading-item__link .print-hidden} Synopsis {#synopsis5}

</div>

``` {space="preserve"}
tsm user-identity-store set-user-mappings --certificate <certificate> [options] [global options]
```

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#){.heading-item__link .print-hidden} Options {#options3}

</div>

-c,\--certificate \<certificate\>

Optional.

Users\' certificate file location.

-cn,\--classnames \<user\_classnames\>

Optional.

Override default user classname values (\"user\" and \"inetOrgPerson\")
with the values you set here. You can provide multiple classnames
separated by commas.

-dn,\--displayname \<displayname\>

Optional.

Display name of the user.

-e,\--email \<email\>

Optional.

Users\' email address.

-jp,\--jpegphoto \<jpegfile\>

Optional.

Users\' jpeg image location.

-m,\--memberof \<groupname\>

Optional.

Group that the user is a member of.

-t,\--thumbnail \<thumbnail\>

Optional.

Users\' thumbnail location.

-ub,\--basefilter \<userbasefilter\>

Optional.

Users\' BaseFilter.

-uu,\--ldapusername \<ldapusername\>

Optional.

User name.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#){.heading-item__link .print-hidden} []{#TSMverify-group-mappings}tsm user-identity-store verify-group-mappings \[options\] {#tsm-useridentitystore-verifygroupmappings--options}
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Validates configuration for LDAP group mapping.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#){.heading-item__link .print-hidden} Synopsis {#synopsis6}

</div>

``` {space="preserve"}
tsm user-identity-store verify-group-mappings --verify <group_name> [global options]
```

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#){.heading-item__link .print-hidden} Options {#options4}

</div>

-v,\--verify \<group\_name\>

Optional.

Name of group to search for.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#){.heading-item__link .print-hidden} []{#TSMIDverify-user-mappings__[options]}tsm user-identity-store verify-user-mappings \[options\] {#tsm-useridentitystore-verifyusermappings--options}
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Validates configuration for LDAP user mapping.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#){.heading-item__link .print-hidden} Synopsis {#synopsis7}

</div>

``` {space="preserve"}
tsm user-identity-store verify-user-mappings --verify <user_name> [global options]
```

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#){.heading-item__link .print-hidden} Options {#options5}

</div>

-v,\--verify \<user\_name\>

Optional.

Name of user to search for.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/cli_user-identity_tsm.htm#){.heading-item__link .print-hidden} Global options
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

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
TSM clients](https://help.tableau.com/current/server/en-us/tsm_overview.htm#Connecti){.MCXref
.xref}.

-u, \--username \<user\>

Required if no session is active, along with `-p` or `--password`.

Specify a user account. If you do not include this option, the command
is run using credentials you signed in with.
