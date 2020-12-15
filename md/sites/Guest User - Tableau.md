

Guest User
==========

::: {.caption .article__tags .content-only-hidden}
[Version: 2020.3]{.article__tags--version}\
[]{.article__tags--applies-to}\
[]{.article__tags--role}
:::

::: {#content-body}
::: {#mc-main-content role="main"}
Core-based licenses of [Tableau Server]{.VariablesProductName} include a
Guest user option, which you can use to let people access Tableau views
without an account on the server.

Guest user access is enabled by default when Tableau Server is installed
with a core-based license. It is not available with user-based
licensing. If you do not intend to use Guest user access, you should
disable it.

Guest access allows users only to see and interact with Tableau views.
The Guest user cannot browse the Tableau Server interface or see server
interface elements in the view, such as user name, account settings,
comments, and so on. For more information about licenses, see [Manage
Licenses](https://help.tableau.com/current/server/en-us/license_manage.htm){.MCXref
.xref}.

**Tip:** To share views with Guest users, either provide URL links or
embed views into web pages. For more information, [see Tableau User
Help[(Link opens in a new
window)]{.sr-only}](https://help.tableau.com/current/pro/desktop/en-us/help.htm#shareworkbooks.html).

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/users_guest.htm#){.heading-item__link .print-hidden} Guest user permissions
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

A Guest user can have the following maximum capabilities:

-   **Workbooks and views**: View, Export Image, Summary Data, View
    Comments, Filter, Full Data, Web Edit, Download (to save a local
    copy)

-   **Data sources**: View and Download

If you add the Guest user to a group that has a higher level of access
to a content resource, the Guest user's access does not exceed the
capabilities listed above. However, the Guest user account will comply
with more restrictive permissions settings.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/users_guest.htm#){.heading-item__link .print-hidden} Enable or disable Guest access
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

You must be a server administrator to change Guest account settings at
either the server or the site level.

**Note:** Enabling the Guest user for a site can increase the number of
potential simultaneous viewers beyond the user list you might be
expecting. The administrative view [Status]{.uicontrol} \> [Traffic
to Views]{.uicontrol} can help you gauge the activity.

1.  In the site menu, click **Manage All Sites** and then click
    [Settings ]{.uicontrol}\> [General]{.uicontrol}.

2.  For [Guest Access]{.uicontrol}, select or clear **Enable guest
    access**.

3.  Click **Save**.

This enables the Guest user on all sites. You can then go to the same
setting for a specific site. To disallow Guest access for a site:

1.  In the site menu, select a site.

2.  Click [Settings]{.uicontrol}, and on the General tab, clear the
    [Enable guest access for this site]{.uicontrol} check box.

If the Guest account is enabled on some or all sites, and you turn off
Guest access at the server level, it is turned off for all sites as
well.

[Note:]{.uicontrol} You can turn off Guest user access at the server or
site level; however, you aren't able to remove the user. So, although no
one can access data or views without signing in to the server, the Guest
user still appears in the Site Users list and group lists for groups
you've added the Guest user to.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/users_guest.htm#){.heading-item__link .print-hidden} Additional Guest account characteristics
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

The Guest user is unique in the following additional ways:

-   As a single user account, it represents all unauthenticated users
    accessing Tableau views.

-   When enabled, it is a member of the All Users group.

-   You can add it as a member of other groups on a site.

-   You cannot edit it or select it as the owner of a content resource.

-   If the Guest user needs to access a workbook with an extract
    connection, the Guest must also have the [View]{.uicontrol}
    capability on the published data source. (The Guest user is not
    allowed to connect to published data sources.)

-   The account is not allowed to save custom views.

-   Guest cannot be used in a user filter.

-   You cannot delete the account; however, you can turn off access to
    it by clearing the check box described in the steps above.
