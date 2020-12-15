

Set Web Edit, Save, and Download Access on Content
==================================================
If you're enabling web authoring functionality on your site, you can
configure more precisely which users on the site have access to this
functionality. Using site roles and permissions rules at the content
level, you can grant or deny [Web edit], [Save],
or [Download] capabilities on projects, workbooks, and data
sources.

**Note:** This document strives to use the phrase *Web edit* only to
specify the name of the capability in permissions rules, and *web
authoring* to refer to the general functionality of creating and
modifying workbooks on the server. However, you might otherwise see
these two phrases used interchangably.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/web_author_who.htm#){.heading-item__link .print-hidden} Why allow users to work on the site directly
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

As an administrator, your initial thought about allowing people to
populate a site with content, seemingly indiscriminately, might be one
of skepticism. However, with a few controls, you can limit where this is
done, while providing important benefits that centralized content
management offers both you and your users.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/web_author_who.htm#){.heading-item__link .print-hidden} Web authoring pros and cons

</div>

For publishers and business users, some benefits of web authoring
include the following:

-   It provides analyst teams who work collaboratively with a central
    location in which to provide input.
-   It enables people who do not have Tableau Desktop to connect to data
    sources and create workbooks.
-   It enables people to access content when they are away from their
    Tableau Desktop computer or VPN, whether on a computer or a
    hand-held device.
-   It can provide a framework for enabling consistency across Tableau
    reports.(By making template workbooks available on the site,
    analysts can download or create new workbooks with data connections,
    branding, and formatting already in place.

For administrators, benefits can include the following:

-   Fewer Tableau Desktop deployments to manage and support.
-   Fewer computers that need to have database drivers installed.
-   Capacity to govern content.
-   More accurate monitoring of what people are doing with Tableau.

Some disadvantages to web editing include the following:

-   For analysts, web editing functionality is not as extensive as in
    Tableau Desktop (although it continues to evolve toward that
    parity).
-   For administrators, more people working on the server might mean
    upgrading systems.
-   Without publishing guidelines, content proliferation on the site is
    expected.\
    This can confuse the people who rely on published Tableau dashboards
    and data sources, degrade server performance and data quality, and
    potentially affect data security.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/web_author_who.htm#){.heading-item__link .print-hidden} Managing permissions to help users avoid content proliferation {#managing--permissions-to-help-users-avoid-content-proliferation}
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

To help users to avoid content proliferation on the site, many Tableau
administrators use projects to allow varying levels of access to
content. For example, one project can be configured to allow all users
to edit and save workbooks; another can allow only approved publishers
to save new content.

To get a better idea how this works, see the following resources:

-   [Configure Projects, Groups, and Permissions for Managed
    Self-Service](https://help.tableau.com/current/server/en-us/projects_data_gov.htm){.MCXref
    .xref}
-   [Projects and Content Permissions[(Link opens in a new
    window)]{.sr-only}](https://help.tableau.com/current/guides/everybody-install/en-us/everybody_admin_permissions.htm "See more info about using projects to manage content access.")
    in *Everybody's Install Guide*
-   [Governed Self-Service at Scale[(Link opens in a new
    window)]{.sr-only}](https://www.tableau.com/sites/default/files/media/Whitepapers/wp_governedselfservice_0.pdf "View a whitepaper that describes a controlled self-service server environment"),
    a Tableau whitepaper by Rupali Jain.\
    To view the PDF, you might need to provide your Tableau website
    credentials. These are the same ones you use for the community
    forums or to submit support cases.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/web_author_who.htm#){.heading-item__link .print-hidden} Coordinate edit and save capabilities with site roles for the appropriate level of access
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

To edit, save, and download workbooks, users must have a site role that
allows those actions, along with the capabilities---defined in
permissions rules---that grant or deny editing-related access.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/web_author_who.htm#){.heading-item__link .print-hidden} Site role access

</div>

-   When the appropriate permissions are set at the content level, the
    [[Creator]{.Variablessiterole-author}] or [Explorer (can
    publish)] site role allows both [Save]
    (overwrite) and [Save As/Download].

    Note that **File \> Save** is only available to the workbook owner.
    When the **Save** permission capability has been granted at the
    project and workbook level, a non-owner user can overwrite the
    existing workbook in web authoring by selecting **File \> Save As**
    and using the same workbook name. This overwrites the existing
    content and they become the owner and gain full access to the
    content.

-   The [Explorer] site role can be granted the **Web Edit**
    and **Save As/Download** capabilities, but they will not be able to
    save (neither overwriting existing nor saving changes to a new
    workbook).

For more information, see [Web Editing and Web
Authoring](https://help.tableau.com/current/server/en-us/permissions.htm#webauthor).
