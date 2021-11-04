Contextual variables are similar to global variables except they are only referenced on the screen where you create them. Although it’s not possible to set the user's name to a variable to reference throughout your app, there are still advantages to the fact that contextual variables cannot be used on other screens.

Sometimes you have functionality you want to use on multiple screens that is variable driven. For example, many apps use pop-up dialog boxes to confirm things like deleting a record. A common way to implement this is to set a Contextual variable to true when the user selects the delete button. You do that by setting the **OnSelect** property of the button to the following.

```
UpdateContext({varShowPopUp: true})
```

You then set the **Visible** property of the pop-up controls to **varShowPopUp**. This is similar to the example from the global variables. The major difference is reusability. If you copy the controls (using Ctrl+C) to an additional screen, then you will have two instances of **varShowPopUp**. These two instances use the same name, but can have different values. The value of **varShowPopUp** on screen1 does not affect the value of **varShowPopUp** on screen2 because each contextual variable, even when they have the same name, are scoped to the screen they are on.

Typically reusing variable names like this is not recommended because it can be confusing, but it’s great if you want to reuse functionality independently on different screens.

If you are in doubt about whether you should use global or contextual variables, typically global variables are the default answer. This is because they are available everywhere, making them the most flexible.

One unique behavior of the **UpdateContext** function is that you can declare more than one variable at a time. This is not possible with the **Set** function. To create more than one context variable with a single formula, use a comma between the variables.

```
UpdateContext({varCount: 1, varActive: true, varName: User().FullName})
```
> [!NOTE]
> In the previous module, we mentioned that using the User() function inline will unnecessarily slow down your app and for that reason a global variable should be used **OnStart**. While using a contextual variable to store User information will improve performance over inline use of the User() function, it is ultimately less performative than a global variable, as you will still be calling on the data source each time that page opens. As such, it is recommended to store User information in a global variable.

To do the same thing with Global variables, you would use the following.

```
Set(varCount, 1);Set(varActive, true);Set(varName, User().FullName)
```

This is not a reason to sway your choice of variable types but a useful concept to remember. In the next unit, you will learn about storing tables of data in a collection variable.