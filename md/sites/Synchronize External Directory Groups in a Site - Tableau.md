

Synchronize External Directory Groups in a Site
===============================================
At any time, you can synchronize an external directory (such as Active
Directory) group with [Tableau Server]{.VariablesProductName} to ensure
new users in the external directory are also added in [Tableau
Server]{.VariablesProductName}. You can synchronize individual groups or
multiple groups at once.

**Note**: In the context of user and group synchronization, Tableau
Server configured with LDAP identity store is equivalent to Active
Directory. Active Directory synchronization features in Tableau Server
function seamlessly with properly configured LDAP directory solutions.

1.  In a site, click [Groups].

    On the Groups page, select one or more groups.

2.  Click [Actions] \> [Synchronize].

    ![](./Synchronize%20External%20Directory%20Groups%20in%20a%20Site%20-%20Tableau_files/synchronize.png)

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/groups_create_adsync.htm#){.heading-item__link .print-hidden} Set the minimum site role for users in an external directory group
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

In the[ Groups - Details] page, administrators can set the
minimum site role for group users to apply during synchronization.

This setting does not run synchronization; it sets the minimum site role
to applied to the group every time synchronization runs. When you
synchronize external directory groups, new users are added to the site
with the minimum site role. If a user already exists, the minimum site
role will be applied if it gives the user more access in a site. If you
don\'t set a minimum site role, new users are added as
[Unlicensed] by default.

**Note:** A user\'s site role can be promoted but never demoted based on
the minimum site role setting. If a user already has the ability to
publish, that ability will always be maintained. For more information on
minimum site role, see [Site roles and Active Directory import and
synchronization](https://help.tableau.com/current/server/en-us/users_site_roles.htm#MinSiteRoleImport){.MCXref
.xref}.

1.  In a site, click [Groups].

2.  On the Groups page, select a group, and then select
    [Actions] \> [Minimum Site Role].

3.  Select the minimum site role, and then click **Change Site Role**.

    ![](./Synchronize%20External%20Directory%20Groups%20in%20a%20Site%20-%20Tableau_files/qs_adsync_1.png)

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/groups_create_adsync.htm#){.heading-item__link .print-hidden} What happens when users are removed in the source external directory? 
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Users cannot be automatically removed from the Tableau Server through an
external directory sync operation. Users that are disabled, deleted, or
removed from groups in the external directory remain on Tableau Server
so that administrators can audit and reassign the user\'s content before
removing the user\'s account completely. For more information, see [Sync
behavior when removing users from Active
Directory](https://help.tableau.com/current/server/en-us/users_manage_ad.htm#Sync){.MCXref
.xref}.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/groups_create_adsync.htm#){.heading-item__link .print-hidden} What happens when a user name changes in the source external directory
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

By default, Tableau Server will not synchronize changes to the user
display name or email address after the initial synchronization when the
corresponding account is created in Tableau Server. For example, if the
user name jsmith is used for the display name John Smith, changing the
display name in external directory to Joe Smith will not synchronize to
the corresponding jsmith user in Tableau Server. Similarly, if the
user\'s email changes in the external directory, Tableau Server will not
synchronize changes.

You can configure Tableau Server to update the name and email properties
when they change in the source external directory by setting
`vizportal.adsync.update_system_user` to `true`.

To change this behavior run the following tsm commands:

``` {space="preserve"}
tsm configuration set -k vizportal.adsync.update_system_user -v true
```

``` {space="preserve"}
tsm pending-changes apply
```

If the pending changes require a server restart, the
`pending-changes apply` command will display a prompt to let you know a
restart will occur. This prompt displays even if the server is stopped,
but in that case there is no restart. You can suppress the prompt using
the `--ignore-prompt` option, but this does not change the restart
behavior. If the changes do not require a restart, the changes are
applied without a prompt. For more information, see [tsm pending-changes
apply](https://help.tableau.com/current/server/en-us/cli_pending-changes.htm#pending-changes-apply){.MCXref
.xref}.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/groups_create_adsync.htm#){.heading-item__link .print-hidden} What happens when an external directory group is removed from Tableau Server?
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Many Tableau administrators use external directory groups to import and
create users. After the users are imported into Tableau Server,
administrators will then delete the group in Tableau Server. Deleting a
group does not delete the users in it.
