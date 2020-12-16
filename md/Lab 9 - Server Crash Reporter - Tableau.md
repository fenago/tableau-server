<img align="right" src="./images/logo.png">



Server Crash Reporter
=====================
The Tableau Server administrator can enable an option to allow logs and
related files to be sent to Tableau when the server has an issue that
results in a crash. These files are used by Tableau to identify and
address issues that cause crashes. By default this option is disabled,
and it should only be enabled in organizations that are not subject to
regulations related to data privacy.

**Important:** Do not enable crash reporting if your data is subject to
privacy regulations.

If Tableau Server has a problem that results in a crash, log files and
dump files are generated. If the crash data upload feature is enabled,
these files are automatically gathered and zipped into an encrypted
package that is sent in the background, at the scheduled time. The
encrypted package is sent in small pieces to limit impact to network
performance. Only one crash report is packaged and uploaded at a time (a
new crash report is not packaged until the previous package has been
uploaded) and is sent in a \"first in, first out\" order. You can
schedule the sending for a low-use window to further reduce any impact
to your users.

The encrypted package is made up crash dump files and logs that include
the following:

-   Crash/core dump files

-   Error log files related to the crash

-   Manifest files related to the crash

The files can contain data that includes:

-   Machine-specific information (for example: hardware, operating
    system, domain).

-   A snapshot of the contents of memory at the time of the crash,
    including application activity details like information about data
    connections, actions taken by the user in Tableau, and data being
    worked on in Tableau.

-   Tableau information including customer-identifiable information.




Configure Server Crash Reporter
===============================


Server crash reporting is disabled by default. This topic describes how
to enable and configure server crash reporting. Crash reports are
encrypted and sent to Tableau.

If your organization uses a proxy server to connect to the internet then
you must configure server crash reporter to use the proxy. Even if you
have already configured Tableau Server to use a proxy, you must also
configure server crash reporter separately. To configure proxy for
server crash reporter you must use TSM CLI procedure as described in
this topic.

**Important:** Do not enable crash reporting if your data is subject to
privacy regulations.

### Use the TSM web interface

1.  Open TSM in a browser:

    https://\<tsm-computer-name\>:8850. For more information, see [Sign
    in to Tableau Services Manager Web
    UI](https://help.tableau.com/current/server/en-us/sign_in_tsm.htm).

2.  Click the Maintenance tab.

3.  Under Other Maintenance Tasks, in Server Crash Reporter, select
    Enable crash reporting:

    ![](./Configure%20Server%20Crash%20Reporter%20-%20Tableau_files/tsm-ui-crash-reporter.png)

4.  Specify the scheduled time of day to upload the crash reports to
    Tableau.

5.  When you are finished, click Pending Changes, and then click Apply
    Changes and Restart.

### Use the TSM CLI

Use the configuration file template below to create a json file. After
you have filled in the options with the appropriate values, pass the
json file and apply settings with the following commands:

`tsm settings import -f path-to-file.json`

`tsm pending-changes apply`

If the pending changes require a server restart, the
`pending-changes apply` command will display a prompt to let you know a
restart will occur. This prompt displays even if the server is stopped,
but in that case there is no restart. You can suppress the prompt using
the `--ignore-prompt` option, but this does not change the restart
behavior. If the changes do not require a restart, the changes are
applied without a prompt. 

Because the configuration file is using configKey class, the values that
you pass are not validated by TSM as they are when you use
configEntities class. You can verify and set individual options by using
the tsm configuration commands.

### Crash reporter settings

The crash reporter settings in the template below specify a range of
options for configuring Tableau Server to send crash reports to Tableau.

### Configuration template

Use this template to configure the gateway settings.

For more explanation about configuration files, entities, and keys see
[Configuration File
Example](https://help.tableau.com/current/server/en-us/config_file_example.htm).

``` {xml:space="preserve"}
 {
    "configKeys": {
     "servercrashupload.enabled": "true",
     "servercrashupload.scheduled_time": "1:00:00 UTC",
     "servercrashupload.proxy_server_host": "",
     "servercrashupload.proxy_server_port": "",
     "servercrashupload.proxy_server_username": "",
     "servercrashupload.proxy_server_password": "",
     "servercrashupload.preserve_upload_packages": "false",
     "servercrashupload.delete_completed_dumps": "false"
     }
 }
```

### Configuration file reference

This table includes keys that you can set to configure crash reporting.

servercrashupload.enabled
:   Default: `false`.

    Set to `true` to enable crash reporting.

servercrashupload.scheduled\_time
:   Default: `1:00:00 UTC`

    Specifies the scheduled time that crash uploads will begin. Enter
    time of day in 24 hour format.

servercrashupload.proxy\_server\_host
:   If your organization uses a proxy server to communicate with the
    internet, specify the host name.

servercrashupload.proxy\_server\_port
:   If your organization uses a proxy server to communicate with the
    internet, specify the port number.

servercrashupload.proxy\_server\_username
:   If your proxy server requires authentication, specify the user name
    with this key.

servercrashupload.proxy\_server\_password
:   If your proxy server requires authentication, specify the password
    with this key.

servercrashupload.preserve\_upload\_packages
:   Default: `false`.

    To save all packages that are created for a crash reporting, set
    this key to `true`.

    By default, packages are saved to
    `C:\ProgramData\Tableau\Tableau Server\data\tabsvc\clustercontroller\tabcrashreporter`.

servercrashupload.delete\_completed\_dumps
:   Default: `false`.

 