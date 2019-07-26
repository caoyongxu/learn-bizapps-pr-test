In PowerApps, the **DisplayMode** property of a control allows you to modify how 
controls and information look and function when using the app. For example, if you
have a button on your screen but it should only be selected when needed.
Otherwise the button is disabled, and users cannot select it. This is a pretty
common example and can be done by properly configuring the
**DisplayMode**. There are three **DisplayModes** on every control, except
a screen:

-   **DisplayMode.Disabled**

-   **DisplayMode.Edit**

-   **DisplayMode.View**

When you add a control to your app, by default **DisplayMode** is set to
**DisplayMode.Edit**.

But what does **DisplayMode.Edit** mean when actually applied to a
control? The following section provides more information about 
each **DisplayMode** when applied to a control.

**DisplayMode.Edit**

Using the **Button** control as an example, when the **DisplayMode**
property is set to **DisplayMode.Edit**, the button functions as you
would expect. This means that users can interact with the button, by selecting
it. This also means that other properties for the control, such as
**OnSelect**, are available to trigger actions when the button is selected.

**DisplayMode.Disabled**

Still using the **Button** control as an example, when the
**DisplayMode** property is set to **DisplayMode.Disabled**, the button
appears greyed out and cannot be selected. The reason the control looks
greyed out is because of the disabled properties. Each control has
slightly different disabled properties, which determine how the control 
looks in this mode.

-   **DisabledBorderColor** -- The color of a control's border.

-   **DisabledColor** -- The color of the text in a control.

-   **DisabledFill** -- The background color of a control.

**DisplayMode.View**

Continuing with the **Button** control as an example, when the
**DisplayMode** property is set to **DisplayMode.View**, the button
looks exactly like when it's in **DisplayMode.Edit,** but it's not
selectable. You can probably already see how this would be very
confusing for end users. To elaborate a little from the example earlier,
if you plan to have a button or buttons configured in your app that can
only be selected at certain times, set the **DisplayMode** property to
**DisplayMode.Disabled** instead of **DisplayMode.View**. While both
modes do not allow the user to select the button, the disabled mode also
gives a visual indication that it is not selectable.

Each Control functions slightly differently, so **DisplayMode**
for one control may not affect another control the same way. For more
information about the various controls see 
[Controls and Properties in PowerApps](https://docs.microsoft.com/powerapps/maker/canvas-apps/reference-properties).

When you add a control to your app, by default the **DisplayMode** is
set to **DisplayMode.Edit**. 
