The performance of an app is important to keep users happy. Apps can go
from mediocre to great just based on performance. And sometimes it can
be as simple of a change as caching data in a collection or removing
redundant calls to the data source.

In this module, you will learn about common performance problems, ways
to mitigate their impact, and how to perform testing to discover the
issues.

The most common performance bottleneck - Data sources
------------------------------------------------------

The most common app performance problems come from interactions with
data sources. Almost every app has one or more data source. PowerApps
natively supports over 200 different connections to these data sources
and using these connections is key to a great app.

Calling these data sources from your app is often the largest bottleneck
in your app because of the time it takes to call across the network to
the data source, process the request on the data source side, return the
data to PowerApps across the network, and then for PowerApps to process
and display the data. Optimizing these interactions with data sources is
key to great performance. The following sections highlight some of the most common mistakes.

### Too many refreshes

Using the Refresh function, you can force PowerApps to update the data
it has gathered from a given data source. This seems like a great
function to run because you get the freshest data in your app. But,
PowerApps will often handle this refresh for you. For example, when you
use a Form to submit a new record to a data source displayed in a
Gallery control, PowerApps will automatically refresh that connection.
If you include a Refresh function when you navigate to the Gallery
screen you are now refreshing the data that PowerApps already refreshed.
This is redundant and slows your app down for no reason. 

>[!NOTE]
> Do not use the Refresh function until you are certain it is needed.

### Too many lookups

As you start to use relational data (covered in Learning Path Use advanced data options and connectors in PowerApps -- Module 1 Work with relational data in a canvas app in PowerApps) a common mistake is not to consider the ramifications of a LookUp function inside of a Gallery. When you place a LookUp function on a Label inside of the Gallery, then that LookUp will be performed once for every record in the Gallery. That means if you have 100 records in the Gallery the app has to perform 100 individual LookUp calls to the data source to render. Depending on the data source this could take minutes to render. A better approach is only to display the related data using a details screen or to use a Collection to cache the data from the data source, then the LookUp does not have to execute across the network. 

>[!NOTE]
> Be careful when making additional calls to remote data sources if you use controls that display
multiple records.

### Storing data in the wrong data source

Different data sources are optimized for different workloads and this should be a consideration when choosing where to store data. One example is storing images or files. A common use of PowerApps is to capture images either using the Camera control or the devices built-in camera app. After the user has taken the image, it needs to be saved. One option is to store the image in the same SQL Server database as the other app data. While possible, it is important to note that SQL Server is very inefficient in storing images. Writing and reading the image file to a SQL database is slow, causing your app to run slow. A better option is to [store PowerApps images in the Azure Blob Storage](https://powerapps.microsoft.com/blog/upload-files-from-powerapps-using-the-azure-blob-storage-connector/).
Azure Blob Storage is much faster than writing the same data to SQL Server. This minor change to the underlying structure of your app can have a useful impact on user satisfaction.

>[!NOTE]
> Choose the optimal data source for your app to get maximum performance.

Other performance considerations
--------------------------------

While data sources might be the largest bottlenecks, there are other
easily overlooked changes you can make to get optimal performance. Some
other common issues include:

-   **Asset size** - When you are designing your app it is great to
    include company logos and other visual assets. When you add these
    assets to your app, make sure the assets are optimized for the size
    of your app. The higher the resolution of a file, the larger the
    file size, and the more resources it takes for your app to store and
    display the image. Use an image editing tool to resize your files to
    the size you need for your app.

-   **Republish your app** - The PowerApps team is constantly updating
    PowerApps to bring new features and to increase performance. The
    only way that your app takes advantage of these advancements is for
    you to open the app and publish again. Your app will stay on the
    version that it was published on until you do this. So periodically
    revisiting your app to move to the latest version will provide you with the
    best possible performance.

-   **Build focused apps** - PowerApps supports building apps with as
    many screens as you can imagine, but too many screens is not a good
    idea. You should build your apps focused on a specific audience and
    process. This allows you to optimize the user experience for one
    audience, makes building and troubleshooting the app easier, and
    reduces the size of the app. If you have one app for everything,
    consider breaking it into smaller apps by role.

Optimize performance in small steps
-----------------------------------

As you work through this module, you are going to learn about the different techniques and options for optimizing performance. Before you get too deep in optimizing your app, remember that the most important thing is that your app works. A fast-performing app that only throws errors when the user uses it has no value.

It is often easier to build your app so that it accomplishes its goals and is fully functional. After the app works then you can revisit the app for changes you can make to increase performance - making those changes one at a time confirming they don't break functionality. This methodology, of making small changes, will have the highest rate of success. As you become more comfortable with the different performance concepts, you will learn to build the app with them from the start. But in the meantime, build an app that works and then optimize.

Additional information
----------------------

To supplement the concepts in this module, there are two additional
reading options to help you increase your performance mindset.

- [Performance considerations with PowerApps](https://powerapps.microsoft.com/blog/performance-considerations-with-powerapps/) - Discusses better ways to load data, patterns, limits, custom APIs, and
file optimization. 
- [PowerApps Canvas App Coding Standards and Guidelines](https://pahandsonlab.blob.core.windows.net/documents/PowerApps%20canvas%20app%20coding%20standards%20and%20guidelines.pdf) - This is a living document that not only covers performance and testing
techniques but also explores standards and documentation of your app.

Now that you are aware of the benefits of optimizing performance and
some of the common issues to look out for, the remainder of this module
will provide you with techniques to increase performance and how to use
various methods for testing your app. 
