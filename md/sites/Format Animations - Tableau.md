

Format Animations
=================

::: {.caption .article__tags .content-only-hidden}
[Version: 2020.3]{.article__tags--version}\
[Applies to: Tableau Desktop, Tableau Online, Tableau
Server]{.article__tags--applies-to}\
[]{.article__tags--role}
:::

::: {#content-body}
::: {#mc-main-content role="main"}
Animate visualizations to better highlight changing patterns in your
data, reveal spikes and outliers, and see how data points cluster and
separate.

Animations visually transition between filter, sort, and zoom settings,
different pages, and changes to filter, parameter, and set actions. As
visualizations animate in response to these changes, viewers can more
clearly see how data differs, helping them make better informed
decisions.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/formatting_animations.htm#){.heading-item__link .print-hidden} Understanding simultaneous and sequential animations
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

When you author animations, you can choose between two different styles:
simultaneous or sequential. Here are examples of each type.

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/formatting_animations.htm#){.heading-item__link .print-hidden} Simultaneous animations

</div>

The default simultaneous animations are faster and work well when
showing value changes in simpler charts and dashboards.

[![](./Format%20Animations%20-%20Tableau_files/animations.gif){#animations.gif}](javascript:void(0);)\
[Click the image above to replay the animation.]{.caption}

<div>

### [[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/formatting_animations.htm#){.heading-item__link .print-hidden} Sequential animations

</div>

Sequential animations take more time but make complex changes clearer by
presenting them step-by-step.

[![](./Format%20Animations%20-%20Tableau_files/animations_sequential.gif){#animations_sequential.gif}](javascript:void(0);)\
[Click the image above to replay the animation.]{.caption}

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/formatting_animations.htm#){.heading-item__link .print-hidden} Animate visualizations in a workbook 
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

1.  Choose [Format]{.uicontrol} \> [Animations]{.uicontrol}.

2.  If you want to animate every sheet, under [Workbook
    Default]{.uicontrol}, click [On]{.uicontrol}. Then do the following:

    -   For [Duration]{.uicontrol}, choose a preset, or specify a custom
        duration of up to 10 seconds.

    -   For [Style]{.uicontrol}, choose [Simultaneous]{.uicontrol} to
        play all animations at once or [Sequential]{.uicontrol} to fade
        out marks, move and sort them, and then fade them in.

3.  To override workbook defaults for a particular sheet, change the
    settings under [Selected Sheet]{.uicontrol}.

    **Note:** In the Selected Sheet section, "(Default)" indicates a
    setting that automatically reflects the related Workbook Default
    setting.

    ![](./Format%20Animations%20-%20Tableau_files/animations_pane.png)

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/formatting_animations.htm#){.heading-item__link .print-hidden} Reset animation settings for a workbook
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

You can reset animations to return an entire workbook to the default
animation settings. Be aware that this turns animations off by default.

1.  Choose [Format]{.uicontrol} \> [Animations]{.uicontrol}.

2.  At the bottom of the [Animations]{.uicontrol} pane, click [Reset
    All]{.uicontrol}.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/formatting_animations.htm#){.heading-item__link .print-hidden} Completely disable all animations
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

If you find animations distracting while viewing vizzes, you can
completely disable them so they never play. (This isn\'t a system-wide
setting; each user needs to apply it separately.)

-   In Tableau Desktop, choose [Help]{.uicontrol} \> [Settings and
    Performance]{.uicontrol}, and deselect [Enable
    Animations]{.uicontrol}.

-   In Tableau Online or Tableau Server, click your profile image or
    initials in the top right corner of the browser, and choose [My
    Account Settings]{.uicontrol}. Then scroll down to the bottom of the
    page, deselect [Enable animations]{.uicontrol}, and click [Save
    Changes]{.uicontrol}.

**Note:** When animations are disabled, you can still choose
[Format]{.uicontrol} \> [Animations]{.uicontrol} in authoring mode and
adjust settings---but they will have no effect.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/formatting_animations.htm#){.heading-item__link .print-hidden} []{#Why}Why animations sometimes won\'t play
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Animations won\'t play if a viz is server-rendered. To ensure that
vizzes render on a client computer or mobile device, use these
techniques:

-   If you\'re a viz author, [reduce viz complexity[(Link opens in a new
    window)]{.sr-only}](https://help.tableau.com/current/pro/desktop/en-us/perf_visualization.htm).

-   If you\'re a Tableau Server administrator, [increase the complexity
    threshold for client-side rendering[(Link opens in a new
    window)]{.sr-only}](https://help.tableau.com/current/server/en-us/browser_rendering.htm).

**Note:** On computers with lower processing power, animations may
appear choppy, but users can continue to interact with vizzes without
any delays in responsiveness.

<div>

[[]{.icon--med-lg .icon--arrow-up .heading-item__icon}](https://help.tableau.com/current/server/en-us/formatting_animations.htm#){.heading-item__link .print-hidden} Unsupported browsers and features
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

Animations are supported by all web browsers except Internet Explorer.

The following Tableau features don\'t animate:

-   Maps and density marks in web browsers

-   Pie, polygon, and text marks

-   Axes and headers

-   Forecasts, trends, and reference lines

-   Page history
