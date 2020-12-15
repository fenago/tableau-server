

Planning a Site
===============

::: {.caption .article__tags .content-only-hidden}
[Version: 2020.3]{.article__tags--version}\
[]{.article__tags--applies-to}\
[]{.article__tags--role}
:::

::: {#content-body}
::: {#mc-main-content role="main"}
Before you add users and content to a site, we recommend that you plan
the following aspects of the site.

-   [Projects](https://help.tableau.com/current/server/en-us/site_admin_planning.htm#projects)

-   [Users and
    groups](https://help.tableau.com/current/server/en-us/site_admin_planning.htm#users-and-groups)

-   [Site roles and
    permissions](https://help.tableau.com/current/server/en-us/site_admin_planning.htm#site-roles-and-permissions)

-   [Extract refresh
    schedules](https://help.tableau.com/current/server/en-us/site_admin_planning.htm#extract-refresh-schedules)

The subsequent sections go over these site components, assuming that you
are familiar with

**Note:** This article and section apply only to self-managed Tableau
Server deployments on-premises or in the cloud. If you use Tableau
Online, see [Manage Content Access[(Link opens in a new
window)]{.sr-only}](https://help.tableau.com/current/online/en-us/permissions_section.htm "Go to Tableau Online Help (opens new browser tab)").

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/site_admin_planning.htm#){.heading-item__link .print-hidden} Projects {##projects}
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

You can create projects on a site, which act as containers in which you
can organize related content assets (such as data sources and
workbooks). For example, you might set up a project to contain all of
the certified data sources and workbooks your organization uses for
mission-critical decisions. Or you might set up projects by department.

Projects are also useful for managing permissions. Once you know how
your users need to access content, it's usually easier to create
projects based on those the type of content, and maintain permissions at
the project level.

Every site has a default project named **Default**. When you create
projects, the new projects get their initial set of permissions from the
default project. In effect, the default project is a template for new
projects. As we explain in related articles, for most environments, we
recommend that you use the Default project only as a permissions
template, and not as a container for published content.

For more information, see [Use Projects to Manage Content
Access](https://help.tableau.com/current/server/en-us/projects.htm){.MCXref
.xref}.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/site_admin_planning.htm#){.heading-item__link .print-hidden} Users and groups
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Any user who will publish content or access published content on a site
must be able to sign in to the site. If the user already has an account
on the server, you'll need to add that user to the appropriate site. You
can add a user to more than one site as well. If the user doesn't
already exist, you need to create a user account. Either way, make a
list of the users who will need to be able to sign in to each site.

**Note:** The server license might restrict how many users you can have,
or what level of access they can have. Check with the server
administrator to make sure that you\'ll be able to have an account for
all your users.

In general, we recommend that you create groups on the server and then
add users to the groups. This helps to make permissions much easier to
manage. You can assign permissions on groups, to give those permissions
to all users in the group. (See the next section.)

A typical strategy is to create groups for users who use content in
similar ways. For example, you might create a group named
SalesWBPublishers for all the users in the Sales department who publish
workbooks, and a separate group named SalesDSPublishers for people in
Sales who publish data sources. Each of these sets of users needs its
own set of capabilities, so it makes sense to have a group for each for
these needs.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/site_admin_planning.htm#){.heading-item__link .print-hidden} Site roles and permissions
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Each user has a *site role* that determines the maximum permissions that
they can have on the site. As part of your site planning, you need to
decide each user's site role. A user with a site role that's too
restrictive might not be able to do the work they need. By the same
token, a security best practice is to limit users' capabilities to only
those that they need to do their work. This is referred to as following
the principle of *least privilege*.

You or a site administrator you delegate this task to must also
determine the permissions a user needs to work with content. Each
content asset (workbook, data source, project) supports a set of
*capabilities*. For example, you can **View** or **Add Comments** to a
workbook. Before a user can perform tasks on a workbook, their
permissions must allow those capabilities. A recommended practice is to
sketch out a mapping of permissions to users outside of Tableau before
you try to set this up on the server.

Permissions determine what a user can do *within the context of the site
role*. A user whose site role is **[Viewer]{.Variablessiterole-basic}**
can never publish to the site, regardless of the permissions you grant
them. A user whose site role is **[Creator]{.Variablessiterole-author}**
can publish a workbook to the site, but only if that user has permission
to save and view workbooks.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/site_admin_planning.htm#){.heading-item__link .print-hidden} Extract refresh schedules
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

If users publish data sources or workbooks that include extracts, you
usually want to make sure that the extracts are refreshed, so that they
contain the latest data. Users can manually refresh an extract, but this
isn't always a good idea if the extract is large, and the refresh takes
a long time. Instead, you can set up schedules for when an extract
should be refreshed. Another planning task for a site administrator,
therefore, is to think about when extracts should be refreshed and to
work out schedules.
