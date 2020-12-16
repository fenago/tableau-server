

Uninstall Tableau Server
========================

Do not uninstall Tableau before upgrading. For details on upgrading, see
[Upgrading from 2018.2 and Later
(Windows)](https://help.tableau.com/current/server/en-us/sug_plan.htm).

Beginning with version 2018.2, you can have multiple versions of Tableau
Server installed at the same time. This allows you to run most of an
upgrade while an existing version is running, and reduces downtime and
impact to users. Once you have upgraded, you can uninstall your previous
version. Doing this frees up disk space. You do not have to uninstall
the previous version.

This article explains how to uninstall previous versions, after you\'ve
upgraded to a newer version.



##### Uninstalling and completely removing Tableau Server
---------------------------------------------------------------------


There are two primary \"uninstall\" scenarios that Tableau Server on
Windows supports:

-   **Uninstall Tableau Server:** *After you upgrade* to a new version
    of [Tableau Server] you can uninstall your
    previous version to free up disk space. Continue reading for
    information about uninstalling Tableau.

-   **Remove Tableau Server:** If you want to complete remove Tableau
    Server from a computer, you can use a script provided by Tableau to
    remove Tableau Server and all related files. *This removes all data
    as well as server components, so should only be done if you know you
    want to reset the computer to a pre-Tableau state.* You might need
    to do this if Technical Support recommends this step when
    troubleshooting an installation problem. We recommend you create a
    backup of your data before removing Tableau. Save the backup file to
    a safe location on a computer that is not part of your Tableau
    installation. Completely remove Tableau Server without uninstalling
    any version first. The script will uninstall all existing versions
    found on the computer. If you have already uninstalled your existing
    version and now want to completely remove Tableau, you can find the
    script to do so in a temporary location. For more details, see
    [Remove Tableau Server from Your
    Computer](https://help.tableau.com/current/server/en-us/remove_tableau.htm)




##### Uninstall a Tableau Server version
------------------------------------------------------------------------------------------------------------------


When upgrading from one TSM version to another, you must leave the
earlier version in place until you have finished the upgrade. *Then* you
can uninstall it.

Use Control Panel to uninstall an earlier version of Tableau Server
after upgrading. Starting with version 2018.2, you can have multiple
versions of Tableau Server installed at the same time. All installed
versions are visible in Control Panel, but only one version is running
(the running version will generally be the version you upgraded to, but
if you have not completed the upgrade process it could be an earlier
version). After completing the upgrade you can uninstall your previous
version.

**Important:** Beginning with version 2018.2, uninstalling Tableau
Server will not create a backup of your data. As a best practice, always
create a backup of your data before upgrading or uninstalling Tableau.
This ensures you can reinstall and restore the data if you decide you
want to do this. Save the backup to a safe location on a computer that
is not part of your Tableau Server installation.


To uninstall a version of Tableau Server:

1.  Open Control Panel, click [Uninstall a program], and
    locate the version you want to uninstall.

    Be sure you select the correct version to uninstall:

    -   Uninstalling previous versions of Tableau Server does not impact
        the running version and simply removes unnecessary files from
        those previous versions.

    -   Uninstalling the current, running version of Tableau Server
        stops server and removes server-specific files and folders, but
        may leave some elements behind. Uninstalling does not create a
        backup of your repository data.

2.  With the Tableau Server version selected, click
    [Uninstall].




##### Other articles in this section
--------------------------------------------------------------------------------------------------------------


-   [Remove Tableau
    Server](https://help.tableau.com/current/server/en-us/remove_tableau.htm)
-   [Help Output for tableau-server-obliterate
    Script](https://help.tableau.com/current/server/en-us/tableau-server-obliterate-h.htm)

