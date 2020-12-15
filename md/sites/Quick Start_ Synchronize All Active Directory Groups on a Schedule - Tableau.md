

Quick Start: Synchronize All Active Directory Groups on a Schedule
==================================================================

::: {.caption .article__tags .content-only-hidden}
[Version: 2020.3]{.article__tags--version}\
[]{.article__tags--applies-to}\
[]{.article__tags--role}
:::

::: {#content-body}
::: {#mc-main-content role="main"}
After you import Active Directory groups in [Tableau
Server]{.VariablesProductName}, you can make sure they stay synchronized
in [Tableau Server]{.VariablesProductName} by setting up a schedule. You
can also synchronize all Active Directory groups on the server
on-demand, at any time. The minimum site role setting for the group is
applied when users are synchronized.

**Note**: In the context of user and group synchronization, Tableau
Server configured with LDAP identity store is equivalent to Active
Directory. Active Directory synchronization features in Tableau Server
function seamlessly with properly configured LDAP directory solutions.

::: {.grid-section .grid-ul}
::: {classstring="quickstart"}
[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/qs_ad_group_sync.htm#){.heading-item__link .print-hidden} [1]{.step-bg} Set a minimum site role for synchronization {#1-set-a-minimum-site-role-for-synchronization}
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
:::

In a site, click [ Groups]{.uicontrol}. Select a group, and then click
[Actions]{.uicontrol}\> [Minimum Site Role]{.uicontrol}. Select the
minimum site role, and then click [Change Site Role]{.uicontrol}. Server
and site administrators can set the minimum site role for group users to
be applied during Active Directory synchronization. If you don\'t set a
minimum site role, new users are added as [Unlicensed]{.uicontrol}.

![](./Quick%20Start_%20Synchronize%20All%20Active%20Directory%20Groups%20on%20a%20Schedule%20-%20Tableau_files/qs_adsync_1.png)

Synchronizing can promote a user\'s site role, but will never demote a
user\'s site role.
:::

::: {.grid-section .grid-ur}
::: {classstring="quickstart"}
[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/qs_ad_group_sync.htm#){.heading-item__link .print-hidden} [2]{.step-bg} Set the schedule {#2-set-the-schedule}
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
:::

Server administrators can enable synchronization for all Active
Directory groups on the [General]{.uicontrol} tab of the
[Settings]{.uicontrol} page for the server. Enable synchronization,
select the frequency settings, and then click [Save]{.uicontrol}.

![](./Quick%20Start_%20Synchronize%20All%20Active%20Directory%20Groups%20on%20a%20Schedule%20-%20Tableau_files/qs_adsync_2.png)

All Active Directory groups on the server are synchronized according to
the same schedule.
:::

::: {.grid-section .grid-ll}
::: {classstring="quickstart"}
[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/qs_ad_group_sync.htm#){.heading-item__link .print-hidden} [3]{.step-bg} Run synchronization on-demand (optional) {#3-run-synchronization-ondemand-optional}
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
:::

On the [General]{.uicontrol} tab of the [Settings]{.uicontrol} page,
click [Synchronize All Groups]{.uicontrol} to synchronize all Active
Directory groups on [Tableau Server]{.VariablesProductName} immediately.
Click this button at any time to ensure new users and changes are
reflected in all Active Directory groups on the server.

![](./Quick%20Start_%20Synchronize%20All%20Active%20Directory%20Groups%20on%20a%20Schedule%20-%20Tableau_files/qs_adsync_3.png)

Click [Synchronize All Groups]{.uicontrol} to synchronize all Active
Directory groups on the server outside of a schedule.
:::

::: {.grid-section .grid-lr}
::: {classstring="quickstart"}
[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/qs_ad_group_sync.htm#){.heading-item__link .print-hidden} [4]{.step-bg} View the status of synchronization tasks {#4-view-the-status-of-synchronization-tasks}
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
:::

Server and site administrators can view the results of Active Directory
synchronization jobs in the **Background Tasks for Non Extracts**
administrative view. On the server or in a site, click
[Status]{.uicontrol}. Under [Analysis]{.uicontrol}, click [Background
Tasks for Non Extracts]{.uicontrol} and filter on the [Queue Active
Directory Groups Sync]{.uicontrol} and [Sync Active Directory
Group]{.uicontrol} tasks.

![](./Quick%20Start_%20Synchronize%20All%20Active%20Directory%20Groups%20on%20a%20Schedule%20-%20Tableau_files/groups_adsync_viewtasks.png)

**Queue Active Directory Groups Sync** queues the **Sync Active
Directory Group** tasks to be run.
