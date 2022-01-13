Before you choose your data source in Power Apps, it’s important to understand delegation. By using delegation, Power Apps optimizes its interaction with data sources to minimize the amount of transferred data. Put more simply, Power Apps uses delegation to offload the processing of data to the data source when available. (Processing includes filtering, searching, and sorting.) Delegable processing is dependent on the data source and function being used. If you have much data and need to rely on the back-end data source for operations such as filtering, then you might consider moving or replicating your data into an environment that works well with delegation, such as Microsoft Dataverse. To replicate your data from a different source, you can use the Data Integrator to move data into Dataverse.

## Delegation in action

There’s an example to help you understand delegation. You have a list of 5,000 projects stored in SharePoint. The **ProjectStatus**
column stores the values **Active** or **Inactive**. Half (2,500) of
the records are set to each of these values. You could show the list in
a gallery and filter it by using this formula.

`Filter(SharePointList, ProjectStatus = "Active")`

Because the **Filter** function is delegable to a SharePoint data
source, Power Apps would send your formula to SharePoint. SharePoint
would process all 5,000 records and return to Power Apps the 2,500
records for which **ProjectStatus** is set **Active**. Those records
would all be available in your gallery. In this scenario, Power Apps
didn't process any data, and only the matching records were sent from SharePoint to Power Apps, which is efficient.

## When delegation isn't available

Some functions cannot be delegated to some data sources. An example of a
non-delegable action is the **Search** function against the SharePoint
data source. The **Search** function is similar to **Filter**, but you
can use **Search** to check across multiple fields and to find partial
matches. For example, `Search(SharePointList, "Rob",
"FirstName","LastName")` would return all of the records where the string
"rob" is in either the **FirstName** or the **LastName** column. In this
example, Power Apps would return records for Robert Smith, Rob Jones, and
Suzy Robinson.

Because the **Search** function isn't delegable to the SharePoint data
source, Power Apps has to process the records locally, which means
first the records are sent from SharePoint to Power Apps. By default, the
data source will only return the first 500 records. It isn't the first
500 records that match your formula, but the first 500 records in the
data source. In this example, when you add this formula to your gallery,
SharePoint returns the first 500 records from the list to Power Apps, and
then Power Apps does the search operation locally. If your list
contained 5,000 items, the other 4,500 records in your data source aren't
processed or displayed. You can increase the default of 500 records
to a maximum of 2,000 records in the advanced settings of Power Apps
Studio. Under those circumstances, 3,000 records still wouldn't be
processed or displayed.

## Consider delegation when choosing a data source

The reason there's an entire module dedicated to delegation is that it's
a key consideration when choosing your data source. Consider the types
of functions you need, like Search, and the amount of
data you'll have as you choose the best data source for your
application.

In the following unit, you'll learn more about how delegation works
with various data sources.
