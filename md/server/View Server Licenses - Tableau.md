

View Server Licenses
====================
Server administrators can view the license and product key information
for [Tableau Server]{.VariablesProductName}.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/view_licenses.htm#){.heading-item__link .print-hidden} Viewing licenses from the [Tableau Server]{.VariablesProductName} web UI
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

How you navigate to the Licenses page in [Tableau
Server]{.VariablesProductName} depends on whether you have a single
site, or multiple sites.

-   On a server with a single site, click [Settings] and
    [Licenses]:

-   On a multi-site server, click [Manage all sites] on the
    site menu, [Settings], and [Licenses]:

    **Note:** The [Manage all sites ]option only displays
    when you are signed in as a server administrator.

This page displays information for any licenses that have been activated
on your server, including any user-based (term) or core-based licenses.


-   [Use the TSM web
    interface](https://help.tableau.com/current/server/en-us/view_licenses.htm#use-the-tsm-web-interface){#use-the-tsm-web-interface
    .tabs__tab-link .is-active}
-   [Use the TSM
    CLI](https://help.tableau.com/current/server/en-us/view_licenses.htm#use-the-tsm-cli){#use-the-tsm-cli
    .tabs__tab-link}


1.  Open TSM in a browser:

    http://\<tsm-computer-name\>:8850

2.  Click **Configuration** , and then click [Licensing ]:

    The table displays the product key, expiration date, and expiration
    of maintenance.

    **Note**: The TSM Web UI provides a limited amount of licensing
    information. Use the TSM CLI or the Tableau Server Web UI to see
    additional licensing information, including the number of each type
    of user-based license (Creator, Explorer and Viewer).
