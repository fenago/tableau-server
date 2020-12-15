

Set the User Authentication Type for SAML
=========================================

::: {.caption .article__tags .content-only-hidden}
[Version: 2020.3]{.article__tags--version}\
[]{.article__tags--applies-to}\
[]{.article__tags--role}
:::

::: {#content-body}
::: {#mc-main-content role="main"}
On a site that has been configured for site-specific SAML,
administrators can specify users' authentication type. For example, if
Tableau Server was configured for site-specific SAML and server-wide
SAML, administrators can specify which users authenticate with
site-specific SAML and which users authenticate with server-wide SAML.

You can assign authentication type at the time you add users to [Tableau
Server]{.VariablesProductName}, as well as any time afterward.

1.  When you're signed in to the [Tableau Server]{.VariablesProductName}
    site, select **Users**.

2.  On the [Site Users]{.uicontrol} page, select the check boxes next to
    the users you want to assign an authentication type.

3.  On the [Actions]{.uicontrol} menu, select
    [Authentication]{.uicontrol}.

    ![](./Set%20the%20User%20Authentication%20Type%20for%20SAML%20-%20Tableau_files/users_set_authentication.png)

4.  In the Authentication dialog box, select [Site SAML]{.uicontrol} or
    [Server Default]{.uicontrol}.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/users_set_auth_type.htm#){.heading-item__link .print-hidden} Notes
------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

-   Users that authenticate with site-specific SAML can only belong to
    one site. If a user needs to belong to multiple sites, set their
    authentication type to the server default. Depending on how
    site-specific SAML was configured by the server administrator, the
    server default is either local authentication or server-wide SAML.

-   If you change users' authentication to site-specific SAML, the next
    time they sign in, they will be directed to your identity provider's
    site to provide their credentials.
