

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


##### Other articles in this section
--------------------------------------------------------------------------------------------------------------


-   [Configure Server Crash
    Reporter](https://help.tableau.com/current/server/en-us/crashdata_server_config_keys.htm)

