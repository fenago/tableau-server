

Manage Site User Visibility
===========================
By default, all site users can see aliases, project ownership and
comments by other users when permissions allow. The User Visibility
setting lets administrators manage if users with Viewer and Explorer
site roles see other users and groups on the site, which can be
important for sites that are used by multiple clients. To learn more
about site roles, see [Set Users' Site
Roles](https://help.tableau.com/current/server/en-us/users_site_roles.htm).

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/user_visibility.htm#){.heading-item__link .print-hidden} Limit user visibility
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Setting User Visibility to **Limited** impacts certain collaboration
tools and hides user information in Tableau Online and Tableau Server.
Limited User Visibility either disables the feature for Viewers and
Explorers (excluding Site Administrator Explorers), or removes user
information from other areas. Note that Creators and administrators will
still see user information when User Visibility is set to Limited.

To limit user visibility for Explorers and Viewers (excluding Site
Administrator Explorers):

-   Navigate to the site\'s [Settings] page
-   Select [Limited] in the [User Visibility]
    setting

The following is a list of site areas impacted when User Visibility is
set to Limited. Unless noted that the feature is disabled for all users,
only non-administrator Explorers or Viewers are impacted.

+----------------------------------+----------------------------------+
| Area                             | Impact                           |
+----------------------------------+----------------------------------+
| Search                           | User information not displayed   |
+----------------------------------+----------------------------------+
| Content owners                   | User information not displayed   |
|                                  | (Explorers and Viewers can\'t    |
|                                  | see themselves, but can see      |
|                                  | their content in My Content)     |
+----------------------------------+----------------------------------+
| Profile pictures                 | User information not displayed   |
+----------------------------------+----------------------------------+
| Subscriptions                    | User information not displayed   |
|                                  |                                  |
|                                  |                                  |
+----------------------------------+----------------------------------+
| Recommendations                  | Similar users not displayed (all |
|                                  | users)                           |
+----------------------------------+----------------------------------+
| Add/Edit Tags                    | Explorers and Viewers can see    |
|                                  | tags but cannot delete or modify |
|                                  | them                             |
+----------------------------------+----------------------------------+
| \"Who has seen this view?\"      | Disabled                         |
+----------------------------------+----------------------------------+
| Ask Data usage analytics         | Disabled                         |
+----------------------------------+----------------------------------+
| Permissions dialogs              | Disabled                         |
+----------------------------------+----------------------------------+
| Named sharing                    | Disabled (all users)             |
+----------------------------------+----------------------------------+
| Alerts                           | Disabled (all users)             |
|                                  |                                  |
|                                  | Existing alerts paused           |
+----------------------------------+----------------------------------+
| Comments                         | Disabled (all users)             |
+----------------------------------+----------------------------------+
| Public Custom Views              | Disabled (all users)             |
|                                  |                                  |
|                                  | Existing public custom views     |
|                                  | appear as private                |
+----------------------------------+----------------------------------+
| Request Access                   | Disabled (all users)             |
+----------------------------------+----------------------------------+
| Tableau Desktop                  | Publishing workbooks disabled    |
|                                  | from Desktop                     |
|                                  |                                  |
|                                  | User information not displayed   |
|                                  | on user filters                  |
+----------------------------------+----------------------------------+
| Tableau Catalog (with Data       | User information not displayed   |
| Management Add-on)               |                                  |
+----------------------------------+----------------------------------+

When User Visibility is set to Limited, Tableau Server REST API and
Metdata API calls behave as described in the table above.

Users on a site can interact with views and modify them, such as
applying filters. If that user shares their modified view with others,
or if the user creates something from that modified view (like a metric
or a private custom view), then that user\'s name appears in the URL.
Make sure that the URL for this modified view is only distributed to
users who are permitted to see that person\'s name.

**Note**: If a user is a member of multiple sites, entering an email on
the sign in page for Tableau Online will return the names of all sites
the user is a member of.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/user_visibility.htm#){.heading-item__link .print-hidden} Best practices for limiting user visibility

</div>

Administrators can also check that user and group information is not
visible in these ways:

-   Configure permissions to only provide content to appropriate
    parties. For more information, see
    [Permissions](https://help.tableau.com/current/server/en-us/permissions.htm){.MCXref
    .xref}.
    -   Limited User Visibility hides user identification information
        from search, but might return content that the user published,
        including when searching by owner name, if the person searching
        has viewing permission to that content.
    -   A user publishing a workbook with a duplicate title in the same
        project might see a warning that a workbook with that title
        already exists.
-   Apply row-level security when necessary.
-   Check that metadata within dashboards does not contain user
    information.
-   Check that calculations accessible to users don\'t contain user
    metadata (e.g., user filters).

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/user_visibility.htm#){.heading-item__link .print-hidden} Restore Full User Visibility
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

When administrators set User Visibility back to Full, features disabled
for all users by Limited User Visibility (such as comments and alerts)
remain off. Administrators can re-enable these features through the
site\'s Settings page.

Any previous feature settings are not retained when User Visibility is
set to Full, and affected features are not automatically turned on.
