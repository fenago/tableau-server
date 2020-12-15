

Add Projects and Move Content Into Them
=======================================

::: {.caption .article__tags .content-only-hidden}
[Version: 2020.3]{.article__tags--version}\
[]{.article__tags--applies-to}\
[]{.article__tags--role}
:::

::: {#content-body ns0="http://www.madcapsoftware.com/Schemas/MadCap.xsd"}
::: {#mc-main-content role="main"}
A content resource (workbooks and data sources) can live in only
project. Server and site administrators can add or remove top-level
projects on a site, and move published content from one project to
another. Project leaders with appropriate site roles can add or remove
child projects and move content between projects on which they have
Project Leader access.

This article contains the steps for creating and moving projects. We
recommend becoming familiar with the following related content as well:

-   To learn about projects and when or why to use them, see [Use
    Projects to Manage Content
    Access](https://help.tableau.com/current/server/en-us/projects.htm){.MCXref
    .xref}.

-   Before you create project hierarchies, become familiar with [Project
    administration](https://help.tableau.com/current/server/en-us/permissions.htm#projectpermissions){.MCXref
    .xref}.

-   To see the specific site roles that allow full Project Leader
    access, see [Project-level
    administration](https://help.tableau.com/current/server/en-us/projects.htm#project-admin){.MCXref
    .xref}.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/projects_add.htm#){.heading-item__link .print-hidden} []{#add-project}Add a top-level or child (nested) project {#add-a-toplevel-or-child-nested-project}
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

1.  While you're signed in to [Tableau Server]{.VariablesProductName} as
    an administrator or project leader, select the [Content]{.uicontrol}
    tab, and then do one of the following:

    -   Select [Create]{.uicontrol} \> [Project]{.uicontrol} to create a
        new top-level project (only administrators can do this).

    -   Navigate to and open the project in which you want to create a
        sub-project, and then select
        [Create]{.uicontrol} \> [Project]{.uicontrol}.

        If you're not sure where to find a child project, display
        filters, and select [Show all projects]{.uicontrol}.

2.  Enter a name and description for the project, and then click
    [Create]{.uicontrol}.

    ![](./Add%20Projects%20and%20Move%20Content%20Into%20Them%20-%20Tableau_files/projects_new1.png)

    You can include formatting and hyperlinks in the project
    description. Select **Show formatting hints** for syntax. You can
    also [Add a Project
    Image](https://help.tableau.com/current/server/en-us/custom_projectimage.htm){.MCXref
    .xref}.

    **Note:** To edit a project description later, select it to open it,
    select the information icon next to its name, and then click
    **Edit**.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/projects_add.htm#){.heading-item__link .print-hidden} []{#move-workbook-datasource}Move a content resource to another project
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

1.  On the [Content]{.uicontrol} tab, find the content resource you want
    to move.

    If you're not sure where to find a child project, display filters,
    and select [Show all projects]{.uicontrol}.

    For other content types, you can navigate through its project
    hierarchy, or by selecting the content type on the
    [Explore]{.uicontrol} menu.

2.  On the workbook's [Actions]{.uicontrol}([...]{.uicontrol}) menu,
    select [Move]{.uicontrol}.

3.  Select the new project for the workbook, and then click [Move
    Content]{.uicontrol}.

    ![](./Add%20Projects%20and%20Move%20Content%20Into%20Them%20-%20Tableau_files/projects_move_project.png)

    Moving a project includes moving everything in it, including child
    projects and their content.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/projects_add.htm#){.heading-item__link .print-hidden} []{#move-project}How moving projects affect permissions {#how-moving-projects-affect--permissions}

</div>

When you move a project, Project Leader permissions adapt to the new
project environment.

-   When the target project hierarchy is **locked**, previous Project
    Leader permissions are removed, and new Project Leader permissions
    are granted according to those set at the top-level of the target
    hierarchy.

-   When the target project hierarchy is **unlocked** (managed by
    owner), previous implicitly granted Project Leader permissions are
    removed, explicitly set Project Leader permissions are retained, and
    new Project Leader permissions are granted according to those set at
    the top-level of the target hierarchy.

When you move project and content, permissions may be impacted. For more
information, see [Move projects and
content](https://help.tableau.com/current/server/en-us/permissions.htm#moveproject){.MCXref
.xref}.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/projects_add.htm#){.heading-item__link .print-hidden} []{#delete-project}Delete a project
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

When you delete a project, all of the workbooks and data sources in the
project are also deleted from the site. If you want to delete a project
but not its content, move the content to another project, and then
delete the project.

**Important**

-   You cannot undo deleting a project.

-   Deleting a project deletes all content in it, including child
    projects and their content.

-   You cannot delete the [Default]{.uicontrol} project.

To delete a project:

1.  On the [Content]{.uicontrol} tab, find the project you want to
    remove.

    If you're not sure where to find a child project, display filters,
    and select [Show all projects]{.uicontrol}.

2.  On the project's **Actions** ([...]{.uicontrol}) menu, select
    [Delete]{.uicontrol}.

3.  Confirm that you want to delete the project.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/projects_add.htm#){.heading-item__link .print-hidden} []{#move-perms}Required access level for moving content
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Moving content is effectively like removing it from one project and
publishing it to another. For non-administrators, the permissions needed
on the source project are different than those needed on the destination
project.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/projects_add.htm#){.heading-item__link .print-hidden} Required site role

</div>

To move content, users must have one of the following site roles:

-   Server Administrator (Tableau Server only)

-   Site Administrator Creator or Site Administrator Explorer

-   Creator or Explorer (Can Publish)

Users with a Server Administrator or Site Administrator site role do not
need any additional capabilities.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/projects_add.htm#){.heading-item__link .print-hidden} Required permissions for the project that users move content *to*

</div>

Non-administrators must have the [Publish]{.uicontrol} permission
capability for the project that is the move destination.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/projects_add.htm#){.heading-item__link .print-hidden} Required permissions for the project that users move content *from*

</div>

Non-administrator users must

-   Be the project owner, project leader, or content owner

    OR

-   Have the [Move]{.uicontrol} permission capability for the content
    (or, for data sources, be the data source owner).

For more information, see [Move
content](https://help.tableau.com/current/server/en-us/permissions.htm#MoveContent){.MCXref
.xref} .
