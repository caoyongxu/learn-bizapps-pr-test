In the previous unit, you learned that data sources are often the main reason for slow performance in your app. In this unit, you will learn about some of the common techniques you can apply to mitigate those performance issues.

Use collections to cache data
-----------------------------

Often in your app you will find yourself query the same data repeatedly,
like in the case of pulling the lists of departments for your drop-down menus.
In those instances, you can query for the data once and then reuse that
data throughout the app. This reduces the repetitive calls to the data
source across the network. The following is an example of this process.

In your app, you have several screens where you provide a drop-down menu for
selecting the department. The list of departments is kept in Microsoft Dataverse in an table named **DepartmentList**. On each instance of the
menu, you use the following formula.
```
Filter(DepartmentList, Status = "Active")
```

This works and performs okay.

When you finish the app, you realize that you are querying the
**DepartmentList** table multiple times even though it is static
information. You could modify your app to create a collection with the
**OnStart** property of the app that stores the information using the
following formula.

```
Collect(collectDepartmentList, Filter(DepartmentList, Status = "Active"))
```

Now that you have stored that information you could change the **Items** property of the drop-down controls to be **collectDepartmentList** instead of Filter(DepartmentList, Status = "Active"). These small changes add up to increase performance in your app. Also, as you become more familiar with the technique, you can build your app this way from the onset which reduces the number of formulas you have to write and maintain.

### Watch out for delegation

One thing to keep in mind is that the Collect function is not delegable.
By default, that means only the first 500 items will be returned from
your data source and stored in the collection. Be sure to plan for this
limitation as you implement the use of collections in your app.

Delegation also affects performance
-----------------------------------

When you learned about [delegation](/learn/modules/work-with-data-source-limits-powerapps-canvas-app/?azure-portal=true),
you focused on returning the right amount of rows for your
data source. It is also important to remember that delegation,
especially for mobile apps, can affect performance.

When a formula delegates to the data source, all of the processing is
handled by the data source, and only the matching rows are returned
across the network to the app to be displayed. If a function is not
delegable, then it is very common to change the delegation limit to
2,000 rows. This means that the first 2,000 rows will be
downloaded across the network and then processed locally. In scenarios
where you are on a slow cellular connection or a low-end mobile device
this processing can take a considerable amount of time, causing a poor
experience for the user.

Try to use only delegable functions as much as possible. If your
function is not delegable, then plan for the impact on the end user.

Use the Concurrent function to load multiple data sources
-----------------------------------------------------------------

Previously you learned to use collections to cache data in your app. As
you implement that functionality in your app it is not uncommon to have
several collections load when the app launches. Your **OnStart** property
might look like the following.

```
Collect(collectDepartmentList, Filter(DepartmentList, Status =
"Active")); Collect(collectCompanyList,
CompanyList);Collect(collectRegions, RegionList)
```

In that example, you are creating 3 collections, but the collections are
processed one at a time. So if each one takes 3 seconds to process then
your user has to wait 9 seconds for the app to start.

The Concurrent function allows you to process all of those calls at the
same time. You can change your code to the following.

```
Concurrent(

Collect(collectDepartmentList, Filter(DepartmentList, Status = "Active")),

Collect(collectCompanyList, CompanyList),

Collect(collectRegions, RegionList)

)
```

Now all three formulas run at the same time. Reducing your load time to
3 seconds. Concurrent is a great way to avoid long delays from
asynchronous calls.

Preview and experimental features
---------------------------------

Within Power Apps there are additional, advanced features you can
implement in your app. You can access them by selecting **File** on the menu
bar, then choosing **App settings** and **Advanced settings**. The list of
options you see are ever changing, but often there are one or more
features that relate to performance.

### Preview features

Preview features are features that have been well tested and are close to being
released. They will be available for all apps soon. Testing and
understanding these features helps you to prepare for when they become
standard, and most are enabled by default in new apps.

An example of a current preview feature that helps to increase
performance is Delayed load. This feature "Speeds up your app's start
time by setting on-demand screen expression calls", which means that
screens aren't processed until the user accesses the screen, making the
app start and run faster.

### Experimental features

Experimental features are features that might change, break, or disappear at any time.
The features are off by default. You can sometimes find performance
features here as well, so it is worth taking a look. However, keep in mind
you do run a risk by incorporating them into production apps as they can
evolve, completely change, or disappear.

An example of a current experimental feature that you might experiment with
is "Use longer data cache timeout and background refresh". This
feature increases the timeout from 30 seconds to 1 minute for some of
the common data sources allowing for more loading time. This might not
make for the best user experience but perhaps if you find a way to do
this in the background it could let you work with slower queries.

OnStart versus OnVisible
---------------------

OnStart and OnVisible are part of your toolkit for building great apps,
but from a performance point of view, they can have a major impact.

-   OnStart - This is an app-level property. Formulas in this property
    are run once, when the app starts, and never again. All of the
    formulas must process before the app opens. This is often used to
    initialize data that you will need throughout the app.

-   OnVisible - This is a per-screen property. Formulas in this
    property are run every time a user navigates to the screen. The
    screen will render before the formula is finished processing.

From a performance perspective, the key consideration is when the code runs. Once, when the app starts, or every time a screen is shown. The collection for departments from earlier in this module is a great example. That code loads in the OnStart property of the app. This means it was loaded once and then always available. If you moved that code from OnStart to OnVisible, you would lose the advantage of the collection. If the formula was in the OnVisible property, each time the user navigated to the screen the data source would be queried. In that case, it would perform just as well to leave the code in the drop down.

This doesn't mean you should not use OnVisible. OnVisible is great for
formulas that pertain to the current screen that you need to run.
Additionally, OnVisible is non-blocking, so your users don't have to
wait on the formula to complete to view the screen, which reduces the amount
of that user needs to view a blank screen.

In most apps, you use a mixture of OnStart and OnVisible to get the
optimal experience.

Summary
-------

As you can see there a lot of options for how you build your app and
interact with data sources. The list in this unit is far from exhaustive. The guidance here is meant to guide you toward
better performance, but your results may vary. As you begin applying
these techniques to your apps, you will learn what works best for you
and your environment.

In the next unit, you will learn about testing and troubleshooting
techniques.
