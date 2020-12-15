

Language and Locale for Tableau Server
======================================

::: {.caption .article__tags .content-only-hidden}
[Version: 2020.3]{.article__tags--version}\
[]{.article__tags--applies-to}\
[]{.article__tags--role}
:::

::: {#content-body ns0="http://www.madcapsoftware.com/Schemas/MadCap.xsd"}
::: {#mc-main-content role="main"}
[Tableau Server]{.VariablesProductName}  is localized into several
languages. Server language and locale settings impact how this affects
users. The [Language]{.uicontrol} setting controls user interface (UI)
items such as menus and messages. The [Locale ]{.uicontrol}setting
controls items in views such as number formatting and currency.

Administrators can configure language and locale on a server-wide basis
(see
[](https://help.tableau.com/current/server/en-us/maintenance_set.htm)[Server
Settings (General and
Customization)](https://help.tableau.com/current/server/en-us/maintenance_set.htm){.MCXref
.xref}, and individual users can configure their own settings (see [Your
Account Settings[(Link opens in a new
window)]{.sr-only}](https://help.tableau.com/current/pro/desktop/en-us/help.htm#useracct.html))
. If a user configures their own language and locale, their settings
override the server settings.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/lang_intro.htm#){.heading-item__link .print-hidden} Supported Languages
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

[Tableau Server]{.VariablesProductName} is localized into several
languages. See the \"Internationalization\" section of the [Tableau
Server Technical Specification[(Link opens in a new
window)]{.sr-only}](https://www.tableau.com/products/techspecs#server)
page for more information.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/lang_intro.htm#){.heading-item__link .print-hidden} Default Settings
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

The default language for [Tableau Server]{.VariablesProductName} is
determined during Setup. If the host computer is configured for a
language [Tableau Server]{.VariablesProductName} supports, [Tableau
Server]{.VariablesProductName} installs with that language as its
default. If computer is configured for a language that is not supported,
[Tableau Server]{.VariablesProductName} installs with English as its
default language.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/lang_intro.htm#){.heading-item__link .print-hidden} How Language and Locale are Determined
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Another influence on which language and locale display when a user
clicks a view is the user's web browser. If a server user has not
specified a [Language]{.uicontrol} setting on their User Account page,
and their web browser is set to a language that [Tableau
Server]{.VariablesProductName} supports, the browser's language will be
used---even if [Tableau Server]{.VariablesProductName} itself is set to
a different language.

Here's an example: Assume that [Tableau Server]{.VariablesProductName}
has a system-wide setting of English as the [Language]{.uicontrol} for
all users. Server user Claude does not have a language specified on his
[Tableau Server]{.VariablesProductName} User Account page. Claude's
browser uses German (Germany) for its language/locale.

When Claude signs in to [Tableau Server]{.VariablesProductName}, the
server UI displays in German and when he clicks a view, the view uses
the Germany locale for numbers and currency. If Claude had set his user
account [Language]{.uicontrol} and [Locale]{.uicontrol} to French
(France), the UI and view would have been displayed in French. His user
account setting supersedes those of his web browser, and both of those
have precedence over the Tableau Server system-wide setting.

Another setting to be aware of is the [Locale]{.uicontrol} setting in
Tableau Desktop ([File ]{.uicontrol}\> [Workbook Locale]{.uicontrol}).
This setting determines the locale of the data in the view, such as
which currency is listed or how numbers are formatted. By default,
[Locale]{.uicontrol} in Tableau Desktop is set to
[Automatic]{.uicontrol}. However, an author can override that by
selecting a specific locale. Using the above example, if the author of
View A set [Locale]{.uicontrol} to [Greek (Greece)]{.uicontrol}, certain
aspects of the data in View A would display using the Greek (Greece)
locale.

[Tableau Server]{.VariablesProductName} uses these settings, in this
order of precedence, to determine language and locale:

1.  Workbook locale (set in Tableau Desktop)

2.  Tableau Server User Account language/locale settings

3.  Web browser language/locale

4.  Tableau Server Maintenance page language/locale settings

5.  Host computer's language/locale settings
