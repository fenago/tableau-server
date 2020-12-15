

Set Users' Site Roles
=====================
<div>

When you add users to a site on Tableau Server or Tableau Online,
independent of their license type, you must apply a *site role* to them.
The site role signifies the maximum level of access a user can have on
the site. Along with content permissions, the site role determines who
can publish, interact with, or only view published content, or who can
manage the site's users and administer the site itself.

Looking for Tableau Server on Linux? See [Set Users' Site Roles[(Link
opens in a new
window)]{.sr-only}](https://help.tableau.com/current/server-linux/en-us/users_site_roles.htm "Opens topic in a new browser tab").

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/users_site_roles.htm#){.heading-item__link .print-hidden} []{#site-roles-license-perms}How user licenses, site roles, and content permissions work together
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

The intersection of a user's license type, site role, and content
permissions determines the level of access a user has on the Tableau
site.

1.  The license type is associated with the user. The site role you want
    to assign to the user determines the license type they will require.

    In a multi-site environment on Tableau Server, a user's license
    applies to all sites the user is a member of.

2.  The site role is also set at the user level. In a multi-site
    environment, you assign site roles on each site. For example, the
    same user can have the Site Administrator Creator site role on one
    site, and Viewer site role on another site.

    The site role defines the maximum capabilities the user can have.

3.  Whether the site role's maximum capabilities are available to the
    user depends on the permissions set on the content
    resources (projects, data sources, workbooks).

For example, let\'s say that a user has the following access on a site:

-   Creator license (due to their access on another site)
-   Explorer site role (on this site)
-   Save permission capability on a project (on this site)

In this scenario, even though the license allows connecting to and
creating new data sources in the web editing environment or Tableau
Desktop, and a permission rule allows them to save in a project, their
site role prevents them from being able to save so their effective
permissions do not include the save capability. The user can't publish
content to the site.

Similarly, even if a user has a creator license and a creator site role,
if they do not have the save capability on at least one project, they
can't publish anything to the site.

For more information, see
[Permissions](https://help.tableau.com/current/server/en-us/permissions.htm){.MCXref
.xref}.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/users_site_roles.htm#){.heading-item__link .print-hidden} []{#change-role}Change a user's site role {#change-a-user’s-site-role}
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

1.  Sign in to the site as a server or site administrator, and go to the
    [Users] area.

    If you are a site administrator and do not see the
    [Users] area, check with your server administrator on
    whether they have denied user management capabilities to site
    administrators.

2.  Select the users, and then select [Actions] \> [Site
    Role].

    ![](./Set%20Users’%20Site%20Roles%20-%20Tableau_files/users_siterole_change.png)

3.  Select the new site role, and then click [Change Site
    Role].

    ![Select the new site
    role.](./Set%20Users’%20Site%20Roles%20-%20Tableau_files/users_siterole_change_select_new.png)

    You can hover the pointer over the information icon to display a
    matrix that shows the maximum level of general capabilities each
    site role allows. For more information, continue to [General
    capabilities allowed with each site
    role](https://help.tableau.com/current/server/en-us/users_site_roles.htm#site-role-capabilities-summary){.MCXref
    .xref}.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/users_site_roles.htm#){.heading-item__link .print-hidden} []{#site-role-capabilities-summary}General capabilities allowed with each site role
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

The following table lists the license types as of version 2018.1, the
highest level of site role allowed with each, how each site role maps to
its pre-2018.1 equivalent; and summarizes the maximum capabilities each
site role allows.

::: {mc-conditions="Product.serverserver"}
<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/users_site_roles.htm#){.heading-item__link .print-hidden} What this article covers and where to find what's not covered here {#what-this-article-covers-and-where-to-find-what’s-not-covered-here}

</div>

-   This information focuses on *site* roles and is more generalized.
    For a list of common specific tasks available per *license* role,
    see the matrix on the [For Teams & Organizations[(Link opens in a
    new
    window)]{.sr-only}](https://www.tableau.com/pricing/teams-orgs "Open the Tableau pricing page for subscription-based licensing in a new browser window")
    tab on the Tableau pricing page.

-   This information describes site roles as of version 2018.1. To learn
    more about how core-based licensing relates to user-based licensing,
    how licenses transfer, or other specific licensing transition
    scenarios, start with the following topics:

    [Migrate from Core-Based to Role-Based
    Licensing](https://help.tableau.com/current/server/en-us/licensing_migrate_from_core.htm){.MCXref
    .xref}

    [Troubleshoot
    Licensing](https://help.tableau.com/current/server/en-us/unlicensed.htm){.MCXref
    .xref}
:::

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/users_site_roles.htm#){.heading-item__link .print-hidden} Tableau site roles as of version 2018.1 {#tableau-site-roles-as-of-version-20181}

</div>

Site role name as of version 2018.1

</div>
:::
:::
:::
:::
:::

Previous site role name

Maximum capabilities this site role allows

**Site roles that use a [Creator]{.Variablessku-creator} license**

---Users with these site roles have access to Tableau clients such as
Tableau Prep, Tableau Desktop, Tableau Bridge, and Tableau Mobile.

Server Administrator

Server Administrator

Available on Tableau Server only; not applicable to Tableau Online.

This site role always occupies the highest license activated on the
server between Creator and Explorer. It allows unrestricted access to
the configuration settings for the Tableau Server browser environment,
all sites on the server, users and groups, and all content assets, such
as flows, projects, data sources (including connection information), and
workbooks.

Connect to Tableau published data sources or external data, from the
browser, Tableau Desktop, or Tableau Prep; create and publish new data
sources; author and publish workbooks.

[Site Administrator Creator]{.Variablessiterole-siteadmin-author}

\--

This is the highest level of access for Tableau Online.

Unrestricted access to content as described above, but at the site
level. Connect to Tableau or external data in the browser, Tableau
Desktop, or Tableau Prep; create new data sources; build and publish
content.

On Tableau Server, server administrators can determine whether or not to
allow site administrators to manage users and assign site roles and site
membership. By default, on Tableau Server, and always on Tableau Online,
site administrators are allowed these capabilities.

[Creator]{.Variablessiterole-author}

\--

This is similar to the former Publisher site role, but allows new
features. This site role offers non-administrators the maximum level of
*content* access.

Connect to Tableau or external data in the browser, build and publish
flows, data sources and workbooks, have access to Dashboard Starters,
and use interaction features on published views. Can also connect to
data from Tableau Prep or Tableau Desktop, publish (upload/save) and
download flows, workbooks and data sources.

Site roles that use an [Explorer]{.Variablessku-explorer} license

---Users with these site roles can access the server from the browser or
Tableau Mobile.

Server Administrator

N/A

Tableau Server only; not applicable to Tableau Online.

If Explorer is the highest license type activated on the server when a
new server administrator user is created, the user's site role is Server
Administrator; however, the user will not have the full connecting and
publishing capabilities that come only with the Creator license.

With the Explorer license a Server Administrator has unrestricted access
to the configuration settings for the Tableau Server browser
environment, all sites on the server, users and groups, and all content
assets, such as projects, flows, data sources (including connection
information), and workbooks.

However, with the Explorer license, a Server Administrator can't connect
to external data from the browser to create a new data source. They can
author or publish workbooks and data sources from Tableau Desktop. (they
function as an Explorer (can publish) site role with regards to
publishing).

Site Administrator Explorer

Site Administrator

Same access to site and user configuration as Site Administrator
Creator, but can't connect to external data from the web editing
environment.

Can connect to Tableau published data sources to create new workbooks,
and edit and save existing workbooks.

Explorer (can publish)

Publisher

Can publish workbooks from the web using existing data sources, browse
and interact with published views, and use all interaction features.

In the web editing environment, can edit and save existing workbooks.
Cannot save new standalone data sources from data connections embedded
in workbooks, and cannot connect to external data and create new data
sources.

Explorer

Interactor

Can browse and interact with published views. Can subscribe to content,
create data driven alerts, connect to Tableau published data sources and
open workbooks in the web authoring environment for ad-hoc queries, but
they can't save their work.

Read Only

Viewer

This site role is available only in version 2018.1, for transitioning
users to the user-based Viewer (or other) license and site role. Any
users in the Read Only site role prior to upgrading to version 2018.2 or
later are reassigned to the Viewer site role.

In 2018.1 versions, Read Only users can see and subscribe to published
views others have created. Can't use other interaction features or save
custom views.

Site roles that use a Viewer license

Viewer

N/A

Can see published views others have created and use most interaction
features. Can subscribe to views and download as images or summary data.
Can't connect to data, create, edit, or publish content, or set data
alerts.

For a list of specific capabilities, see the **Viewer** column in the
matrix on the [Tableau pricing page[(Link opens in a new
window)]{.sr-only}](https://www.tableau.com/pricing/teams-orgs "Link opens the Tableau license pricing page in a new browser tab").

**Note:** Although the Viewer site role existed in previous versions,
the new Viewer site role has additional capabilities.

Other site roles

Unlicensed

Unlicensed

Unlicensed users can't sign in to Tableau Server or Tableau Online.
Users are assigned the Unlicensed role in the following circumstances:

-   You import users from a CSV file and their license level is set to
    unlicensed.

-   The number of available licenses is reached at the time you add or
    import users.

-   You remove a user who owns content on the site. The user will still
    own the content but not be able to do anything with it.

-   A product key(s) has expired. See [Refresh Expiration Date for the
    Product
    Key](https://help.tableau.com/current/server/en-us/license_refresh.htm){.MCXref
    .xref}.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/users_site_roles.htm#){.heading-item__link .print-hidden} []{#site-roles-allow-publishing}Who can publish content
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

The following site roles allow the specified level of publishing access.

-   [Server Administrator] (Tableau Server only); [Site
    Administrator Creator]; and
    [[Creator]{.Variablessiterole-author}] allow full
    connecting and publishing access.

    This includes connecting to data and publishing new flows, new
    workbooks and new data sources from Tableau Desktop and the web
    editing environment. The site roles also allow editing and saving
    existing published workbooks, or publishing updates to existing data
    sources.

-   [Explorer (Can Publish)] and [Site Administrator
    Explorer] have limited publishing capabilities, as
    described in [General capabilities allowed with each site
    role](https://help.tableau.com/current/server/en-us/users_site_roles.htm#site-role-capabilities-summary){.MCXref
    .xref}.

-   [Explorer], [Viewer], [Read
    Only], and [Unlicensed] do not allow
    publishing.

::: {mc-conditions="Product.serverserver"}
<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/users_site_roles.htm#){.heading-item__link .print-hidden} []{#MinSiteRoleImport}Site roles and Active Directory import and synchronization
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

When you import users from an external directory like Active Directory,
you can specify the site role. If a user is not yet a member of any site
on the server, the user is added to the site with the assigned role.
When you synchronize groups from an external directory, the site role is
applied through the [Minimum Site Role] setting on the
[Groups - Details] page.

**Note**: In the context of user and group synchronization, Tableau
Server configured with LDAP identity store is equivalent to Active
Directory. Active Directory synchronization features in Tableau Server
function seamlessly with properly configured LDAP directory solutions.

If a user already exists in a [Tableau Server]{.VariablesProductName}
site, the site role assigned during the import or sync process will be
applied if it gives the user more access in a site. Importing or
synchronizing AD users and groups can promote a user\'s site role, but
does not demote a user\'s site role.

If a user already has the ability to publish, that ability is
maintained.

<div>

The matrix below shows the rules applied for site roles on import.

**Note:** The **Import Site Role** row abbreviated headers indicate the
site role specified for import. The **Current Site Role** column headers
represent the current user site role. The table values represent the
abbreviated resulting site role.

-   Site Administrator: SA
-   Site Administrator Creator: SC
-   Site Administrator Explorer: SE
-   Creator: C
-   Explorer: E
-   Explorer (Can Publish): EP
-   Viewer: V
-   Unlicensed: U

 

</div>
:::

Current Site Role

Import Site Role

SC

C

SE

EP

E

V

U

Site Administrator Creator

(SC)

SC

SC

SC

SC

SC

SC

SC

Site Administrator Explorer

(SE)

SE

SE

SE

SE

SE

SE

SE

Creator

\(C\)

SC

C

SE

C

C

C

C

Explorer (Can Publish)

(EP)

SC

C

SE

EP

EP

EP

EP

Explorer

\(E\)

SE

C

SE

EP

E

E

E

Viewer

\(V\)

SE

C

SE

EP

E

V

V

Unlicensed

\(U\)

SE

C

SE

EP

E

V

U

