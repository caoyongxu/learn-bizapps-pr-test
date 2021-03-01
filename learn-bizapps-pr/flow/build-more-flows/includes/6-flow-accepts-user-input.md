You can customize button flows by letting the user provide specific details that will be used when the flow runs.

You can create a button flow either on the Power Automate website or in the mobile app for Power Automate. For this unit, you'll use the website.

## Prerequisites

You must have an account on the Power Automate website.

## Open the template

1. Launch Power Automate and sign in using your organizational account.

1. Select **Templates** and search *Create a New Outlook Task*.

    ![Screenshot of the Create a New Outlook Task tile as it appears in the search results.](../media/2-input.png)

1. Sign in if you are prompted to do so and select **Create Flow**.

## Customize the user input

You'll notice that this flow already requests additional input, but let's add another field.

1. On the trigger card, select **Add an input**.

    ![Screenshot of the Manually trigger a flow card with the Add an input button highlighted.](../media/6-input.png)

1. For each custom field that should be available when someone runs your flow, enter values in the **Input title** and **Input description** field.

    In this example, you'll create one custom input field, **Due Date**.

    ![Screenshot of the Manually trigger a flow card with the Due date field and "Please enter or select a date (YYYY-MM-DD)" highlighted.](../media/8-input.png)

## Customize the task

1. On the **Create a task** card, select the title bar to expand the card.

1. In the Due Date field, select **Due Date** from the dynamic content.

    ![Screenshot of the Create a task card with the Due Date field highlighted.](../media/10-input.png)

1. Select **Save**.

## Run the flow

You'll now use the mobile app for Power Automate to run the button flow that you just created. You'll provide all the user input that's needed to create a task with a name, description, and due date.

1. In the mobile app for Power Automate, select the **Buttons** tab at the bottom of the window, and then select the **Create new Outlook Task** button.

    ![Mobile screenshot of the Buttons tab with the Create new Outlook Task button highlighted.](../media/runmt1-input.png)

1. Enter the requested inputs and select **Done**.

    ![Mobile screenshot of Create new Outlook Task with the Due date set and the Done button highlighted.](../media/runmt3-2-input.png)

    The flow runs.

1. Select the **Activity** tab at the bottom of the window to view the results.

    ![Screenshot of the Feed tab. The Create new Outlook Task with "Flow successfully ran 1 time" is highlighted and the Activity button is highlighted.](../media/runmt5-input.png)

1. To view the detailed results of the flow run, select the **Create a task** step.

    ![Screenshot of Activity details with run details for Create new Outlook Task. Manually trigger a flow took 0 seconds, and Create a task took 0 seconds.](../media/runmt6-input.png)

Now you can not only run button flows with the already available information, but also request inputs from the user.
