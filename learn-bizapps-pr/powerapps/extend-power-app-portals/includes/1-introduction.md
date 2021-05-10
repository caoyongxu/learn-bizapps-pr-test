A variety of configuration-only tools and features are available for building a Microsoft Power Apps portals application. Examples of these tools and features include table lists, table forms, web forms, and the ability to integrate other technologies such as SharePoint and Microsoft Power BI. You might encounter features that are not easily configured by using the available low-code or no-code features.

Liquid template language in portal pages and templates begins to extend your web application and allows you to manipulate and display content in a variety of ways.

Power Apps portals features can also be further extended by using standard web technologies such as HTML, JavaScript, and Cascading Style Sheets (CSS).

You might also encounter situations where you need to update or create data in Microsoft Dataverse without submitting table form or a web form. A common method is to build a standalone web application with an API that can be called from the Power Apps portal and that will act as a liaison to update Dataverse.

After you have configured and customized your portal, another concern that you might have is determining how to ensure that your work is saved in a source control system and how to ensure that your portal can be deployed to a test or production portal.

## Server-side extensibility

Power Apps portals do not support client-side business rules, JavaScript web resource, or Power Apps component framework controls that are commonplace with the model-driven forms. As a result, portal deployments will occasionally become blocked because expectations of the same or similar form behavior can't be met. Instead, table lists, table forms, and web forms include a custom JavaScript option that allows developers to add scripts that implement equivalent functionality.

However, the portals are based on model-driven apps that are underpinned by Dataverse. In fact, portals deliver functionality that is already available in a model-driven app but only to the portal users, meaning that:

- Table-scope business rules still apply because they are implemented on the server.
- Workflows and Microsoft Power Automate flows are still triggered, regardless of whether a triggering action was run inside a model-driven app or a portal. The workflows can also be called explicitly by using form configuration on the portal.
- When a portal user interacts with Dataverse records, the server-side code runs as usual. Developers can pass relevant portal context to plug-ins when the records are updated by portal users who are employing table forms. That approach adds some server-side code extensibility to the portals and enables various integration scenarios.
