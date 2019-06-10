Global variables are the most commonly used variables because of their
flexibility. After you set the variable, you can reference it or update
it throughout your app. This allows you to avoid repetitive query for
the same information repetitively, to build out the information you need
in an imperative way, or sometimes just as a place holder.

Storing information for your user
---------------------------------

A common design pattern in apps is to personalize the app. This can be
as simple as saying Welcome and displaying the user's name on each screen of the
app. With PowerApps, you can show a welcome message and get the user's
name in a declarative manner by using the following formula in a Label
control.

```
"Welcome " & User().FullName
```

This formula displays the string Welcome and then queries Azure Active
Directory for the user's DisplayName property and displays it as text.
But if you include that function on every screen then each time a screen
opens PowerApps has to query that data from Azure AD directly. This
creates repetitive calls to the network that slow down your app.

A better approach would be to store that information in a global
variable when the app opens, and then reference that variable
throughout your app. You could do this by Modifying the **OnStart**
property of the app with the following formula.

```
Set(varUserDisplayName, User().FullName)
```

Now for your Label control, you would change the formula to the following.

```
"Welcome " & varUserDisplayName
```

This gets you the same output as the previous formula, but instead of
having to go back to Azure AD on every screen, PowerApps can reference the
value stored in the variable.

Tracking status in a variable
-----------------------------

In a declarative mindset, you might hide or show controls based on a
query for data. For example, if you had an app for managing customer's
orders, you might have a warning icon that displays only if the customer
has more than 3 outstanding invoices. In addition to the warning, you
might have a requirement to get approval from a manager if the customer
would like to submit a new order when they have more than three
outstanding invoices. This approval workflow will start by the user
selecting an approval button.

With a declarative mindset, you would set the Visible property for the
warning icon to the following.

```
CountRows(Filter(InvoiceEntity, CustomerNumber = ThisCustomersNumber And Status = "Outstanding")) > 3
```

If that is true, then the icon displays, and if it is false the icon does not
display. You would then repeat that same formula on the Visible property of
the Approval button.

The problem is this becomes a complex formula that you maintain in two
different locations, and that query will generate duplicate network
traffic, processing in the app, and processing on the data source.

A better approach is only to run the complex call once, store the result
in a variable, and then use that variable to control the Visible
property of each control.

To do this, configure the **OnVisible** property of the screen to set
the variable.

```
Set(varOustandingExceeded, CountRows(Filter(InvoiceEntity, CustomerNumber = ThisCustomersNumber And Status = "Outstanding")) > 3)
```

The variable **varOutstandingExceeded** is either true or false based on
the result of the formula. Now set the **Visible** property of the icon and
button control to **varOutstandingExceeded**.

No additional formula or functions are necessary. This is because those
controls accept either true or false for the **Visible** property and the
variable will be either true or false. Based on your **Set** function in the
**OnVisible** property of the screen, PowerApps will set the type of
variable to Boolean and set the value to true or false based on the
result of the formula.

Small changes like this make your app both more performant and easier to
maintain. You should incorporate variables anytime you are repetitively
retrieving information that is not going to change while you are using
it.
