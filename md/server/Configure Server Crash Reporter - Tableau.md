

Configure Server Crash Reporter
===============================
Server crash reporting is disabled by default. This topic describes how
to enable and configure server crash reporting. Crash reports are
encrypted and sent to Tableau. See [Server Crash
Reporter](https://help.tableau.com/current/server/en-us/crashdata_server.htm){.MCXref
.xref} for more information.

If your organization uses a proxy server to connect to the internet then
you must configure server crash reporter to use the proxy. Even if you
have already configured Tableau Server to use a proxy, you must also
configure server crash reporter separately. To configure proxy for
server crash reporter you must use TSM CLI procedure as described in
this topic.

**Important:** Do not enable crash reporting if your data is subject to
privacy regulations.


-   [Use the TSM web
    interface](https://help.tableau.com/current/server/en-us/crashdata_server_config_keys.htm#use-the-tsm-web-interface){#use-the-tsm-web-interface
    .tabs__tab-link .is-active}
-   [Use the TSM
    CLI](https://help.tableau.com/current/server/en-us/crashdata_server_config_keys.htm#use-the-tsm-cli){#use-the-tsm-cli
    .tabs__tab-link}


1.  Open TSM in a browser:

    https://\<tsm-computer-name\>:8850. For more information, see [Sign
    in to Tableau Services Manager Web
    UI](https://help.tableau.com/current/server/en-us/sign_in_tsm.htm){.MCXref
    .xref}.

2.  Click the [Maintenance] tab.

3.  Under Other Maintenance Tasks, in Server Crash Reporter, select
    [Enable crash reporting]:

    ![](./Configure%20Server%20Crash%20Reporter%20-%20Tableau_files/tsm-ui-crash-reporter.png)

4.  Specify the scheduled time of day to upload the crash reports to
    Tableau.

5.  When you are finished, click [Pending Changes], and then
    click [Apply Changes and Restart].
