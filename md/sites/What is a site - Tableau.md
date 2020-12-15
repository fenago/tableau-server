

What is a site
==============
You might be used to using the term *site* to mean "a collection of
connected computers," or perhaps as the short form of "website." In
Tableau-speak, we use site to mean a collection of users, groups, and
content (workbooks, data sources) that's walled off from any other
groups and content on the same instance of [Tableau
Server]{.VariablesProductName}. Another way to say this is that [Tableau
Server]{.VariablesProductName} supports multi-tenancy by allowing server
administrators to create sites on the server for multiple sets of users
and content.

All server content is published, accessed, and managed on a per-site
basis. Each site has its own URL and its own set of users (although each
server user can be added to multiple sites). Each site's content
(projects, workbooks, and data sources) is completely segregated from
content on other sites.

If you are a server administrator on your [Tableau
Server]{.VariablesProductName} deployment, you can learn more about
sites, when to use them (vs. projects), and more in [Sites
Overview[(Link opens in a new
window)]{.sr-only}](https://help.tableau.com/current/server/en-us/sites_intro.htm "Opens topic in a new browser tab"),
in the **Manage Server** section.

**Note:** This article pertains to configuring sites on [Tableau
Server]{.VariablesProductName} deployments. For Tableau Online, see
[Site Administrator Role and Tasks[(Link opens in a new
window)]{.sr-only}](https://help.tableau.com/current/online/en-us/to_site_startup.htm "Open Tableau Online help in a new browser tab.").

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/sites.htm#){.heading-item__link .print-hidden} []{#site-admin-tasks}Site administrator tasks
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Where the Server Administrator site role gives a user unrestricted
access to the entire [Tableau Server]{.VariablesProductName} deployment,
the Site Administrator site roles give a user unrestricted or minimally
restricted access at the site level. The differences between Site
Administrator Creator and Site Administrator Explorer are in the level
of data connection and publishing access. Both site roles allow
administering the site itself and managing site users. For more
information, see [Set Users' Site
Roles](https://help.tableau.com/current/server/en-us/users_site_roles.htm){.MCXref
.xref}.

Although a server administrator can work at both the server and site
levels, we make a distinction between the two levels of task. The site
administrator is typically in charge of creating and maintaining the
framework that enables Tableau users in the organization to publish,
share, manage, and connect to data sources and workbooks. In this vein,
site administrator tasks include any of the following (and both site
roles allow this level of access):

-   Creating project hierarchies to organize the site's data sources and
    workbooks.

    This can include delegating project-level management to project
    leaders.

-   Creating groups and assigning permissions that allow users to access
    only the content they need.

-   Adding and removing users, assigning their site roles.

    This is allowed by default on a site; however, a server
    administrator can restrict this access to the server level only.

-   Managing the site's extract and subscription schedules.

-   Monitoring site activity.

For more information about the distinction between server administrator
and site administrator, see [Administrator-level access to
sites](https://help.tableau.com/current/server/en-us/sites_intro.htm#admin-access-sites){.MCXref
.xref}, in the **Manage Server** section.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/sites.htm#){.heading-item__link .print-hidden} []{#site-setup-steps}Steps for setting up your site {#steps}
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

The table below shows a loose sequence of steps for setting up a site,
along with links to topics where you can get more information. You can
complete the steps in any order that makes sense for you.

However, before you perform the steps to configure the site, we
recommend spending some time with the articles in this section, learning
about site authentication, site roles, projects, and permissions.
Ideally you would document a plan for your projects, groups, and overall
permissions strategy. Then set up a few projects and add a preliminary
set of users, to test the plan and resolve issues before you add the
remaining users. You can change many site settings after your users are
working with the site, but try to go in with the intention of minimizing
post-production changes.

+----------------------+-----------------------------------------------+
| **Plan**             | To supplement the recommendations above this  |
|                      | table, get an overview of how the site        |
|                      | components work together in [Planning a       |
|                      | Site](https://help.tableau.com/current/       |
|                      | server/en-us/site_admin_planning.htm){.MCXref |
|                      | .xref}.                                       |
+----------------------+-----------------------------------------------+
| **Configure access** | Work with the server administrator to         |
|                      | determine how users sign in to the site, and  |
|                      | configure the site appropriately.             |
|                      |                                               |
|                      | For example, if the server is configured for  |
|                      | single sign-on using SAML, you might          |
|                      | configure SAML authentication at the site     |
|                      | level as well.                                |
+----------------------+-----------------------------------------------+
| **Create projects    | Projects help you organize content, delegate  |
| and the permissions  | project-level content management, and manage  |
| structure**          | permissions effectively. To get started, see  |
|                      | [Use Projects to Manage Content               |
|                      | Access](https://help.tableau.c                |
|                      | om/current/server/en-us/projects.htm){.MCXref |
|                      | .xref}.                                       |
+----------------------+-----------------------------------------------+
| **Add users**        | Determine the users who can sign in to the    |
|                      | site. See [Add Users to a                     |
|                      | Site](https://help.tableau.com/cur            |
|                      | rent/server/en-us/sites_addusers.htm){.MCXref |
|                      | .xref}.                                       |
+----------------------+-----------------------------------------------+
| **Get your data to   | After you create your projects and            |
| [Tableau             | permissions structure, designate approved     |
| Server]{.Var         | users for publishing and managing vetted data |
| iablesProductName}** | sources to the appropriate projects on the    |
|                      | site.                                         |
|                      |                                               |
|                      | In some organizations, people serve in        |
|                      | multiple Tableau roles. Site administrators   |
|                      | commonly also are data stewards. By that, we  |
|                      | mean they create, publish, and manage the     |
|                      | Tableau data connections. If this is you,     |
|                      | make sure you are assigned the Site           |
|                      | Administrator Creator site role.              |
|                      |                                               |
|                      | After content is published to the site, you   |
|                      | can maintain connection information           |
|                      | (credentials, access tokens) and refresh      |
|                      | schedules. For more information, see [Refresh |
|                      | Data on a                                     |
|                      | Schedule](https://help.tableau.com/c          |
|                      | urrent/server/en-us/schedule_add.htm){.MCXref |
|                      | .xref}.                                       |
+----------------------+-----------------------------------------------+
| **Analyze site usage | Monitor usage, performance, and other         |
| and performance**    | metrics. See [Administrative                  |
|                      | Views](https://help.tableau.co                |
|                      | m/current/server/en-us/adminview.htm){.MCXref |
|                      | .xref} .                                      |
+----------------------+-----------------------------------------------+