

Grant License on Sign In
========================

::: {.caption .article__tags .content-only-hidden}
[Version: 2020.3]{.article__tags--version}\
[]{.article__tags--applies-to}\
[]{.article__tags--role}
:::

::: {#content-body}
::: {#mc-main-content role="main"}
Grant license on sign in (Grant role on sign in) lets unlicensed users
in specific groups become licensed when they sign into a Tableau site.
This streamlines license provisioning for administrators and removes the
user's need to request a license before using Tableau.

For more information about site role capabilities and minimum site
roles, see [Set Users' Site
Roles](https://help.tableau.com/current/server/en-us/users_site_roles.htm){.MCXref
.xref}.

For example, imagine an Active Directory group called Marketing with 100
users, but only 25 users need to access Tableau Server. A site or server
administrator can import all users in the Marketing Active Directory
group, set the group\'s minimum site role to Explorer, and select [Grant
role on sign in]{.uicontrol}. When any of the Tableau users in Marketing
sign into their Tableau site, they\'ll be granted Explorer licenses.
Users who don\'t need Tableau Server remain unlicensed unless they sign
in.

**Note**: For more information about benefits and best practices, see
[Grant Role on Sign In[(Link opens in a new
window)]{.sr-only}](https://help.tableau.com/current/blueprint/en-us/bp_license_management.htm#grant-role-on-sign-in)
in Tableau Blueprint, Tableau\'s planning tool for data-driven
organizations.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/grant_role.htm#){.heading-item__link .print-hidden} Activate Grant role on sign in
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

You can enable Grant role on sign in on new or existing groups. The
following steps walk through how to use Grant role on sign in to add new
users that are eligible for a license but may not consume one. This may
be the case when your company has a lot of eligible users, but limited
Tableau licenses.

::: {mc-conditions="Product.serverserver"}
1.  In a site, click [Groups]{.uicontrol}, and then click [Add
    Group]{.uicontrol}.

    Add new users by importing an Active Directory group. Type the name
    of the group you want to import, and then select the group name in
    the resulting list.

    ![](./Grant%20Role%20on%20Sign%20In%20(Grant%20License%20on%20Sign%20In)%20-%20Tableau_files/import_AD_group1.png)

2.  Select the minimum site role for the users, and select [Grant role
    on sign in]{.uicontrol}.

    All users in the selected Active Directory group will be imported as
    unlicensed users. The minimum site role set for the group will only
    be provisioned to group users who sign into Tableau Server.

    ![](./Grant%20Role%20on%20Sign%20In%20(Grant%20License%20on%20Sign%20In)%20-%20Tableau_files/import_AD_group2.png)

3.  Click [Import]{.uicontrol}.

**Note:** Grant Site Role on Sign In can also be activated in local
groups to provision minimum site roles to group members when they sign
in to Tableau Server. For more information, see [Create a Local
Group](https://help.tableau.com/current/server/en-us/groups_create_local.htm){.MCXref
.xref}.
:::

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/grant_role.htm#){.heading-item__link .print-hidden} []{#GrantRoleOnSignin}Modifying user roles with Grant role on sign in
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

If a user is part of a group using Grant role on sign in, then that user
role can\'t be set to unlicensed or downgraded to a role lower than the
minimum site role set for the group, whether or not they sign in.
Administrators can upgrade a user's site role manually, however.

To downgrade a user's site role, or unlicense the user from the site,
remove the user from the group(s) that have Grant role on sign in
enabled.

In accordance with the terms of the [End User License Agreement[(Link
opens in a new
window)]{.sr-only}](https://mkt.tableau.com/legal/tableau_eula.pdf),
licenses granted on an Authorized User basis may be permanently
reassigned to new users. Users may only be downgraded to a lower site
role (including Unlicensed) when they will permanently discontinue
access to Server Software at the higher role.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/grant_role.htm#){.heading-item__link .print-hidden} []{#remove}Removing users affected by Grant role on sign in
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

You can remove a user from a site only if the user does not own content.
If you attempt to remove a user who owns content, the user site role
will be set to Unlicensed and removed from all groups, but the user will
not be removed from the site. To remove content owners, remove owners
from group with Grant site role enabled or reassign content ownership to
another user. For more information, see Remove users from a site in the
[View, Manage, or Remove
Users](https://help.tableau.com/current/server/en-us/users_view.htm){.MCXref
.xref} help topic.

If the default All Users group has Grant site role enabled, users who
own content can\'t be removed from the site or unlicensed. To remove or
unlicense these users, reassign content ownership to another user, then
remove or unlicense the user.

REST API can be used to reassign content ownership of a workbook. For
more information, see [Update
Workbook](https://help.tableau.com/v2020.3/api/rest_api/en-us/REST/rest_api_ref_workbooksviews.htm#update_workbook)
in the REST API documentation. REST API can also be used to remove users
from the site and transfer content ownership to another user. For more
information, see [Remove User from
Site](https://help.tableau.com/current/api/rest_api/en-us/REST/rest_api_ref_usersgroups.htm#remove_user_from_site)
in the REST API documentation.

For more information on changing content ownership in Tableau Server,
see [Manage Content
Ownership](https://help.tableau.com/current/server/en-us/owner.htm#change-the-owner-of-a-content-resource){.MCXref
.xref}.
