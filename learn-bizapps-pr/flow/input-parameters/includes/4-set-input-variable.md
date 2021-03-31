Input variables are used to set information for your desktop flow. To use your input variables, determine at which step of your flow you'll use that data and then edit that step. If you're using the desktop flow that was created by using the Contoso Invoicing app, the first step that requires a variable is step 5. Select the ellipsis (**...**) to the right of the step and then select **Edit**.

> [!div class="mx-imgBorder"]
> [![Screenshot of step five with the ellipsis button selected and the Edit option highlighted.](../media/13-edit-step.png)](../media/13-edit-step.png#lightbox)

Delete the value in **Text to fill-in:** and then select **{x}**.

> [!div class="mx-imgBorder"]
> [![Screenshot of the "Populate text field in window" edit dialog box with the {x} icon highlighted.](../media/14-set-variable-1.png)](../media/14-set-variable-1.png#lightbox)

Double-click the variable, which in this case is **Account**.

> [!div class="mx-imgBorder"]
> [![Screenshot of the input output variables selector with Account highlighted.](../media/15-set-variable-2.png)](../media/15-set-variable-2.png#lightbox)

Select **Save** to close the dialog box and complete your variable setup. After setting the remaining variables, your steps will resemble the following screenshot.

> [!div class="mx-imgBorder"]
> [![Screenshot of the steps with three that populate a text box with a variable.](../media/16-set-variable-3.png)](../media/16-set-variable-3.png#lightbox)

Now, the values that are filled in for the desktop app will be defined by variables instead of static values.
