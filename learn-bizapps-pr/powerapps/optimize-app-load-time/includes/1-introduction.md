First impressions are important. The first impression that app users get is the length of time that it takes for the app to display the first screen or to provide other visual feedback, such as progress indicators. During startup, your app performs several steps to prepare for the presentation of the first screen: Authenticate, get metadata, **OnStart** processing, and render screens.

> [!div class="mx-imgBorder"]
> [![Screenshot of a flow diagram illustrating the steps in the startup process of Authenticate, Get metadata, OnStart processing, Render screens.](../media/1-visual-progress.png)](../media/1-visual-progress.png#lightbox)

- **Authenticate** - Handles all authentication prompts for connections that are configured for the app. Removing connectors that aren't in use can reduce the number of prompts and accelerate the process.

- **Get metadata** - Retrieves metadata, such as the version of the Microsoft Power Apps platform on which the app runs and the sources from which it must retrieve data.

- **OnStart processing** - Evaluates the formulas that you have set up in the **OnStart** property. Streamlining the performance of this processing has a direct impact on improving the load time of the app.

- **Render screens** - The first screen is prepared and presented to the user. Specified OnVisible formulas are implemented first. Optimizing formulas and minimizing the number of controls on the screen can improve load time.

This module explains how you can evaluate your app load time and identify strategies for improvement.

## Evaluate your app load time

When you're evaluating app load time, a good place to start is establishing a baseline for how long it takes for your app to load. You can accomplish this task by measuring the startup time from launching the application to the time when you believe that you have a usable app. Use a stopwatch to measure the time from launching the app to when you believe a person can start using it. Tools that you can use to measure and drill into the performance details during the load time are discussed later in this module. We recommend that you conduct a new evaluation with each app update so that you can compare the new version with your prior baseline and then identify significant increases in load time.

Measuring startup time helps you get actual timings; however, you should consider observing and asking users about their perception of the app's performance. Occasionally, you can have an app that loads in a few seconds, but users might perceive it to be much longer because they don't regard the app as usable yet. For example, that situation could happen because the app, after displaying the first screen, continues to load data and update the information even though users are already interacting with it. Approaches to solving these two problems differ. If you're trying to improve load time, then you can usually get imperative data that points you to where your app is spending time. If you're trying to improve user perception, then you need to observe the person using the app to understand how they use it and what changes might improve their perception. Small changes can help improve perception, such as adding text prompts to start the interaction or changing the start screen to persist and reload most recent records.

Commonly, you will discover components that slow down an app by viewing the app's **OnStart** property or the **OnVisible** property of the first screen. By optimizing or deferring work that is performed in these properties, you can accelerate load time. Some of these techniques will be explained later in this module.

If you view analytics for your app from the maker portal, it will include the **Time to first screen** and **Time to first screen without connection setup** analytics.

> [!div class="mx-imgBorder"]
> [![Screenshot of app analytics Time to first screen and Time to first screen without connection setup.](../media/2-time-first-screen.png)](../media/2-time-first-screen.png#lightbox)

The data is provided for the last 30 days and can be helpful in providing a summary of your app's performance.

The [Power Apps Review Tool](https://github.com/microsoft/powerapps-tools/tree/master/Tools/Apps/Microsoft.PowerApps.CodeReview/?azure-portal=true#) is another option for evaluating apps. This open-source tool is packaged as a solution that you can import into your Microsoft Dataverse environment. After you have imported the tool, you can use it to evaluate apps in your environment. You can upload *.msapp* files for evaluation as well. The automated review can check your app against a customizable checklist of best practices, and it can identify many common issues that can impact the app startup time and general performance of your apps. After the automated review is complete, you can view a list that shows where your app is doing well and actionable items where it could improve.

> [!div class="mx-imgBorder"]
> [![Screenshot of the Code Review Checklist that is generated by the Power Apps Review Tool.](../media/3-code-review-checklist.png)](../media/3-code-review-checklist.png#lightbox)

In addition to viewing the results in the app, you can email the results, which can be helpful if you are not the app maker.

Common rules that the tool can check that can impact startup time include:

- **Use of Concurrent function** - Consider using the Concurrent function for parallel independent data requests.

- **App Settings flags** - Review app settings. Ensure Delayed Load and Explicit Column Selection is On.

- **Delegation** - Ensure ClearCollect and Filter operations are delegable.

- **Asset Optimization** - Review embedded asset compression/size optimization.

- **Data loading strategy** - Review OnStart and OnVisible data loading strategy. Avoid data calls in OnStart. Move to OnVisible when possible. Ensure that only important data calls block user interaction with UI during initial load of the home screen.

- **Cross-screen dependencies** - Ensure that repeating UI elements are encapsulated in components (for example, menus, header, footer).

## Review your app settings

App settings can have a significant impact on the performance of your app; therefore, make sure that you review the app settings and their enabled status with each app update. Older apps might not have the latest app setting options enabled automatically to ensure that the new option doesn't break existing apps. You might have also enabled a setting to try resolving a problem but then forgot to turn off the setting when you were done. A good example of that scenario is the **Debug published app** option. Enabling this option allows more debug information to be displayed when you use the app monitor to troubleshoot the published app. When this option is enabled, it can be detrimental to the performance and should not be left on for production use.

> [!div class="mx-imgBorder"]
> [![Screenshot of the Debug published app screen with the General option highlighted.](../media/4-debug-published.png)](../media/4-debug-published.png#lightbox)

Another setting to consider is **Data row limit**. This setting determines the most rows that will be retrieved from a server-based connection when delegation is not supported. By default, this value is 500 and can be any value between 1 and 2,000. To work around [delegation issues](/powerapps/maker/canvas-apps/delegation-overview/?azure-portal=true#) in apps, it's common for people to increase this value. This increase might cause unexpected problems when a development environment holds much smaller sets of data than production. For example, with the **Data row limit** set to 2,000, the following expression in **Data row limit** might only preload a few rows in a development environment.

    ClearCollect(colDesks,Desks)

The same app in a production environment with a fully populated dataset could retrieve the full 2,000 rows. As a result, the app will load much slower in production than in development. Frequently, working to eliminate delegation warnings is a better approach than increasing this value.

In older apps, the **Enable Navigate function in App.OnStart** setting might be enabled. This setting allows you to use the Navigate() function in App.OnStart property but results in the first screen not rendering until all your expressions in App.OnStart are evaluated. In more recent apps, this approach is not allowed, and you will need to use the App.StartScreen property instead. The **OnStart** and **StartScreen** properties will be discussed in depth later in this module. If your app has this setting enabled, consider updating to the new approach and disabling the setting, which can improve load times.

In addition to the previously mentioned settings, the **Upcoming features** category has more settings that you should review. Three sections are in this category: **Preview**, **Experimental**, and **Retired**.

New settings start as **Experimental** and graduate to **Preview** as they mature. Experimental features let you try a new feature but are not intended for production apps. These features are turned off by default, and you must enable them. Considerable investment has gone into improving app performance, so continue watching this area for upcoming features.

Typically, settings in the **Preview** section are turned on by default for new apps. These features are in their final stages of testing before becoming standard settings that are enabled for all apps. For the existing apps, you need to opt in to enable these settings if you want to use them. In some cases, opting in might require minor formula usage changes.

If you are working on a performance issue, testing some of the upcoming features might provide insight into whether they would help address your challenges. If so, waiting for the features to mature might be an alternative to refactoring without their benefit.

## Limits and throttling

Each connector can have its own limit of retrieved data and throttling. Additionally, [service protection limits](/powerapps/developer/data-platform/api-limits/?azure-portal=true#) are in place at the platform level. Make sure that you are aware of these limits for the connectors that you use in your app. Apps that encounter these limits during startup might exhibit a slowdown in loading the app.

## Use a loading image

Using a loading image or a progress indicator during long operations in your app can improve user perception.

> [!div class="mx-imgBorder"]
> [![Screenshot of an animated GIF showing the spinning-circle Loading message that indicates a long load operation.](../media/5-loading-image.gif)](../media/5-loading-image.gif#lightbox)

The simplest way to use a loading image during the loading of your app is to use a component that has a spinning image. You can find a prebuilt image in the [Power Apps tools GitHub repository](https://github.com/microsoft/powerapps-tools/blob/master/Components/Preloader%20Component.msapp/?azure-portal=true#). You can import this component and place it on your initial screen on top of your other controls. Then, you can use a variable to control the visibility of the component. The following image shows an example of setting the visible property to the value of a variable showLoader.

> [!div class="mx-imgBorder"]
> [![Screenshot of the preloader control Visible property that is set to showLoader variable.](../media/6-visible-show-loader.png)](../media/6-visible-show-loader.png#lightbox)

Then, in App.OnStart, you can turn on the loading image before loading the data, and then you can turn off the image after the data is loaded.

    Set(showLoader, true);

    ClearCollect(colDesks, Desks);

    ClearCollect(colDeskFeatures, 'Desk Features');

    Set(showLoader, false);

> [!div class="mx-imgBorder"]
> [![Screenshot of the App.OnStart property set to Set(showLoader, true); ClearCollect(colDesks, Desks); ClearCollect(colDeskFeatures,'Desk Features'); Set(showLoader, false.](../media/7-show-loader-code.png)](../media/7-show-loader-code.png#lightbox)

While using a loading image doesn't speed up your application, it provides visual feedback and can help the user understand that the app is doing work in the background.

The rest of this module explores other techniques to identify and improve app load performance.
