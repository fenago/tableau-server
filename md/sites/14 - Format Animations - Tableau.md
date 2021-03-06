

Format Animations
=================


Animate visualizations to better highlight changing patterns in your
data, reveal spikes and outliers, and see how data points cluster and
separate.

Animations visually transition between filter, sort, and zoom settings,
different pages, and changes to filter, parameter, and set actions. As
visualizations animate in response to these changes, viewers can more
clearly see how data differs, helping them make better informed
decisions.



##### Understanding simultaneous and sequential animations
---------------------------------------------------------------------------


When you author animations, you can choose between two different styles:
simultaneous or sequential. Here are examples of each type.



####  Simultaneous animations


The default simultaneous animations are faster and work well when
showing value changes in simpler charts and dashboards.

![](./images/animations.gif)


####  Sequential animations


Sequential animations take more time but make complex changes clearer by
presenting them step-by-step.

![](./images/animations_sequential.gif)


##### Animate visualizations in a workbook 

1.  Choose [Format] \> [Animations].

2.  If you want to animate every sheet, under [Workbook
    Default], click [On]. Then do the following:

    -   For [Duration], choose a preset, or specify a custom
        duration of up to 10 seconds.

    -   For [Style], choose [Simultaneous] to
        play all animations at once or [Sequential] to fade
        out marks, move and sort them, and then fade them in.

3.  To override workbook defaults for a particular sheet, change the
    settings under [Selected Sheet].

    **Note:** In the Selected Sheet section, "(Default)" indicates a
    setting that automatically reflects the related Workbook Default
    setting.

    ![](./images/animations_pane.png)



##### Reset animation settings for a workbook
----------------------------------------------------------------------------------------------------------------------------


You can reset animations to return an entire workbook to the default
animation settings. Be aware that this turns animations off by default.

1.  Choose [Format] \> [Animations].

2.  At the bottom of the [Animations] pane, click [Reset
    All].



##### Completely disable all animations
----------------------------------------------------------------------------------------------------------------------


If you find animations distracting while viewing vizzes, you can
completely disable them so they never play. (This isn\'t a system-wide
setting; each user needs to apply it separately.)

-   In Tableau Desktop, choose [Help] \> [Settings and
    Performance], and deselect [Enable
    Animations].

-   In Tableau Online or Tableau Server, click your profile image or
    initials in the top right corner of the browser, and choose [My
    Account Settings]. Then scroll down to the bottom of the
    page, deselect [Enable animations], and click [Save
    Changes].

**Note:** When animations are disabled, you can still choose
[Format] \> [Animations] in authoring mode and
adjust settings---but they will have no effect.



##### Why animations sometimes won\'t play
-------------------------------------------------------------------


Animations won\'t play if a viz is server-rendered. To ensure that
vizzes render on a client computer or mobile device, use these
techniques:

-   If you\'re a viz author, [reduce viz complexity[(Link opens in a new
    window)]](https://help.tableau.com/current/pro/desktop/en-us/perf_visualization.htm).

-   If you\'re a Tableau Server administrator, [increase the complexity
    threshold for client-side rendering[(Link opens in a new
    window)]](https://help.tableau.com/current/server/en-us/browser_rendering.htm).

**Note:** On computers with lower processing power, animations may
appear choppy, but users can continue to interact with vizzes without
any delays in responsiveness.



##### Unsupported browsers and features
----------------------------------------------------------------------------------------------------------------------


Animations are supported by all web browsers except Internet Explorer.

The following Tableau features don\'t animate:

-   Maps and density marks in web browsers

-   Pie, polygon, and text marks

-   Axes and headers

-   Forecasts, trends, and reference lines

-   Page history
