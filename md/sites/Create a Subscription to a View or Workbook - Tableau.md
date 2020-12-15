

Create a Subscription to a View or Workbook
===========================================

::: {.caption .article__tags .content-only-hidden}
[Version: 2020.3]{.article__tags--version}\
[Applies to: Tableau Online, Tableau
Server]{.article__tags--applies-to}\
[]{.article__tags--role}
:::


Subscriptions email you an image or PDF snapshot of a view or workbook
at regular intervals---without requiring you to sign in to Tableau
Server or Tableau Online.

**Note**: In Tableau Server, administrators determine whether
subscriptions are enabled for a site.

<div>

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/subscribe_user.htm#){.heading-item__link .print-hidden} []{#SubscribeYourself}Set up a subscription for yourself or others
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

When you open a view in Tableau Server or Tableau Online, if you see a
subscription icon
(![](./Create%20a%20Subscription%20to%20a%20View%20or%20Workbook%20-%20Tableau_files/subscribe_icon.png))
in the toolbar, you can subscribe to that view or to the entire
workbook. You can subscribe other users who have permission to view the
content if you own a workbook, if you are a project leader with an
appropriate site role, or if you are an administrator.

1.  From the Explore section of your site, select [All
    Workbooks] or [All Views], or open the
    project that contains the view you want to subscribe to.

    ![Content type
    menu](./Create%20a%20Subscription%20to%20a%20View%20or%20Workbook%20-%20Tableau_files/subscribe_content_1a.png)

2.  Open a view either directly, or after opening the containing
    workbook.

3.  In the toolbar above the view, click [Subscribe].

    ![](./Create%20a%20Subscription%20to%20a%20View%20or%20Workbook%20-%20Tableau_files/subscribe_toolbar.png)

4.  Add the Tableau users or groups you want to receive the
    subscription. To receive a subscription, users must have the
    **View** and **Download Image/PDF** permissions. If they use Tableau
    Server, their accounts must also have email addresses.

    [Note]: When you subscribe a group, each user is added
    individually at the time the subscription is created. If more users
    are added to the group later, you must re-subscribe the group for
    those new users to receive the subscription. Likewise, users later
    removed from the group will not have their subscriptions removed
    automatically unless their permissions to the subscribed view are
    removed.

5.  Choose whether subscription emails include the current view or the
    entire workbook.

6.  Choose the format for your snapshot: as a PNG image, a PDF
    attachment, or both.

    -   If PDFs, choose the paper size and orientation you\'d like to
        receive.

        ![](./Create%20a%20Subscription%20to%20a%20View%20or%20Workbook%20-%20Tableau_files/subscription_paper.png)

7.  When the workbook uses one data extract on a published connection,
    you can pick a frequency:

    -   [When Data Refreshes]: sends only when data in the
        view or workbook is refreshed.
    -   [On Selected Schedule]: Pick a schedule for the
        subscription.

8.  If frequency is not set to When Data Refreshes, pick a schedule:

    -   For Tableau Server, choose from subscription schedules
        established by your administrator.

    -   For Tableau Online and Tableau Server with [custom schedules
        enabled[(Link opens in a new
        window)]{.sr-only}](https://help.tableau.com/current/server-linux/en-us/schedule_enable_custom.htm),
        click the drop-down arrow to the right of the current settings.

        ![](./Create%20a%20Subscription%20to%20a%20View%20or%20Workbook%20-%20Tableau_files/subscribe_options_online_sched.png)

        Then specify a custom schedule that sends subscription emails
        whenever you wish. (The precise delivery time may vary if server
        load is high.)

        ![](./Create%20a%20Subscription%20to%20a%20View%20or%20Workbook%20-%20Tableau_files/self_subscribe_topic.png)

        To change the time zone, click the Time Zone link it to go to
        your account settings page.

9.  To clarify subscription emails, customize the subject line, and add
    a message.

10. If the view contains data only when high-priority information
    exists, select [Don\'t send if view is empty].

11. If you own the workbook, select [Subscribe me].

12. Click [Subscribe].

When you receive a subscription email, you can select the image (or the
link in the message body for PDF subscriptions) to be taken to the view
or workbook in Tableau Online or Tableau Server.

Update subscription settings

</div>

<div>

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/subscribe_user.htm#){.heading-item__link .print-hidden} []{#Unsubscribe}Update or unsubscribe from a subscription
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

You can unsubscribe from an existing subscription, or make changes to a
subscription's format, schedule, subject, or empty view mode.

1.  Access your Tableau Server or Tableau Online account settings by
    doing one of the following:

    -   Click [Manage my subscriptions] at the bottom of a
        subscription email.

        ![](./Create%20a%20Subscription%20to%20a%20View%20or%20Workbook%20-%20Tableau_files/subscribe_remove.png)

    -   Sign in to Tableau Server or Tableau Online. At the top of the
        page, select your user icon, and then select [My
        Content].

        ![](./Create%20a%20Subscription%20to%20a%20View%20or%20Workbook%20-%20Tableau_files/subscribe_remove2.png)

2.  Click [Subscriptions].

3.  Select the check box next to the view you want to unsubscribe from,
    click [Actions], and then click
    [Unsubscribe], or select the subscription option you\'d
    like to change.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/subscribe_user.htm#){.heading-item__link .print-hidden} Resume or delete suspended subscriptions
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

If a subscription fails more than five times, you\'ll receive a
notification email that your subscription has been suspended. There are
a few ways to resume a suspended subscription if you\'re a subscription
owner or administrator:

-   From the My Content area of Tableau web pages, an icon appears in
    the Last update column to indicate that the subscription is
    suspended. Select [\...] \> [Resume
    Subscription] to resume.

-   From the Subscriptions tab of the affected workbook, an icon appears
    in the last update column to indicate that the subscription is
    suspended. Select [\...] \> [Resume
    Subscription] to resume.

You\'ll receive an email notification when the subscription is working
again.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/subscribe_user.htm#){.heading-item__link .print-hidden} See also
----------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

[Change Subscription Settings[(Link opens in a new
window)]{.sr-only}](https://help.tableau.com/current/pro/desktop/en-us/help.html#useracct.html)
in the Tableau Desktop and Web Authoring Help.

[Project-level administration[(Link opens in a new
window)]{.sr-only}](https://help.tableau.com/current/online/en-us/projects.htm#project-admin "Link opens article in a new browser tab")
in the Tableau Online Help, to learn which site roles allow full Project
Leader capabilities.

