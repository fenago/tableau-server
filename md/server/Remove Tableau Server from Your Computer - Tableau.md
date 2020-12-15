
::: {.container--centered}
::: {.header__mobile-menu}
:::

::: {.header__logo}
[![Tableau](./Remove%20Tableau%20Server%20from%20Your%20Computer%20-%20Tableau_files/tableau-logo.png){.header__logo__img}](https://www.tableau.com/en-us/)
:::

::: {.header__search}
:::
:::

::: {.container--full-width .subheader .print-hidden .content-only-hidden}
::: {.container--centered}
#### Tableau Server on Windows Help {#tableau-server-on-windows-help .heading--subheader}
:::
:::

::: {.container--full-width .nav--breadcrumbs}
::: {.container--centered}
<div>

</div>
:::
:::

::: {.section--main .container--full-width}
::: {.container--centered}
Help Output for tableau-server-obliterate Script
================================================

::: {.caption .article__tags .content-only-hidden}
[Version: 2020.3]{.article__tags--version}\
[ ]{.article__tags--applies-to}\
[ ]{.article__tags--role}
:::


The following help content is the output when you run the following
command:

::: {mc-conditions="Product.serverwindows"}
`tableau-server-obliterate -h`

The ./tableau-server-obliterate script is installed to By default:
`C:\Program Files\Tableau\Tableau Server\packages\scripts.<version_code>\`.
:::

Output {#output level="2" is="heading-item"}
------

::: {mc-conditions="Product.serverwindows"}
``` {space="preserve"}
Remove Tableau Server from this computer.

This script will stop and remove all Tableau Services from this
computer. It also removes data and configuration files. It leaves
licensing in place. It also preserves logs and backup files, which
are moved to a temp directory under the Tableau data folder. You can
force removal of these files, and licensing, using optional parameters.

This script is destructive and not reversible. It should only
be used to clean Tableau Server from a computer. For multi-node
installations, you must run the script separately on each node.

This script must be run as the Administrator.


-y              Required. Yes, remove Tableau Server from this computer.
        Must be specified three times to confirm.
-q      Optional. Quiet mode. Windows only. Do not display
        progress UI when removing Tableau Server.
-l              Optional. Delete licensing files and data. This command
        will attempt to deactivate licenses before deleting
        licensing data. Internet access is required for license
        deactivation. Offline deactivation is not supported.
        To deactivate license before removing Tableau Server,
        run 'tsm licenses deactivate' before running this script.
-k              Optional. Do not copy backups to logs_temp directory.
-g              Optional. Do not copy logs to logs_temp directory.
-a              Optional. Do not copy anything to logs_temp directory.  
```
:::
:::
:::

::: {.article__footer--back-to-top .text--centered .print-hidden}
[[]{.icon--med .icon--arrow-up} Back to
top](https://help.tableau.com/current/server/en-us/tableau-server-obliterate-h.htm#){.text--caps}
:::

[Thanks for your feedback!]{slot="submittedMessage"} [There was an error
submitting your feedback. Please try again.]{slot="errorMessage"}
:::
:::

::: {.container--centered}
::: {.footer__links .text--caps}
-   [Legal](https://www.tableau.com/en-us/legal)
-   [Privacy](https://www.tableau.com/en-us/privacy)
:::

::: {.footer__copyright .text--caps}
© 2003-2020 Tableau Software LLC. All rights reserved
:::
:::
:::

![](https://www.facebook.com/tr?id=378938312282541&ev=PageView&noscript=1){width="1"
height="1"}

<div>

![](https://acq-3pas.admatrix.jp/if/5/01/bc28445d93035b6b666e856ea24ee85c.fs?cb=989474&rf=https%3A%2F%2Fhelp.tableau.com%2Fcurrent%2Fserver%2Fen-us%2Ftableau-server-obliterate-h.htm&prf=https%3A%2F%2Fhelp.tableau.com%2Fcurrent%2Fserver%2Fen-us%2Fremove_tableau.htm&i=vtVZ4MEk)

</div>

![](./images/bc28445d93035b6b666e856ea24ee85c.fs)
