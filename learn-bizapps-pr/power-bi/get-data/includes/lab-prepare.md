## Overview

The estimated time to complete the lab is 15 minutes.

In this lab, you connect to the classroom virtual machine and setup the
environment. Before commencing this lab, you must have received an
account and password. It's important that you complete the labs by using
the provided account.

In this lab, you learn how to:

-   Sign in to the Power BI service

-   Create a workspace

-   Open Power BI Desktop

## Getting Started

In this exercise, you connect to the classroom virtual machine and setup
the environment.

[!INCLUDE [](../../../includes/power-bi-lab-login.md)]

### Record your account details

In this task, you will open the **MySettings.txt** file, and record your
account details.

An account has been given to you, and it's important that you use this
account to complete all of the labs.

1.  To open File Explorer, on the taskbar, click the File Explorer
    program shortcut.

	> [!div class="mx-imgBorder"]
	> [![File Explorer program shortcut](../media/lab-1.png)](../media/lab-1.png#lightbox)

1.  In File Explorer, navigate to the **D:\\DA100\\Setup** folder.

1.  To open the **MySettings.txt** file, double-click the file.

1.  In the **MySettings.txt** file, enter your account name and password
    next to the labels.

	> [!div class="mx-imgBorder"]
	> [![account name and password](../media/lab-2.png)](../media/lab-2.png#lightbox)

1.  To save the **MySettings.txt** file, on the **File** menu, select
    **Save** (or press **Ctrl+S**).

1.  Leave the **MySettings.txt** file open.

1.  Leave File Explorer open.

### Sign in to the Power BI service

In this task, you will sign in to the Power BI service.

1.  To open Edge, on the taskbar, click the Microsoft Edge program
    shortcut.

	> [!div class="mx-imgBorder"]
	> [![Microsoft Edge program shortcut](../media/lab-3.png)](../media/lab-3.png#lightbox)

1.  In Edge, navigate to **http://powerbi.com**.

	> [!TIP]
	> You can also use the Power BI Service favorite on the Edge
	favorites bar.

1. Click **Sign In** (located at the top-right corner).

	> [!div class="mx-imgBorder"]
	> [![sign in](../media/lab-4.png)](../media/lab-4.png#lightbox)

1. Enter your account details from the **MySettings.txt** file.

1. When prompted to update the password, reenter the provided password,
    and then enter and confirm a new password. Be sure to update the
    **MySettings.txt** file with your new password.

1. Complete the sign in process.

1. If prompted by Edge to stay signed in, click **Yes**.

1. In the Power BI service, at the top-right corner, if the "New Look"
    is not enabled, click the slider control to turn it on.

	> [!div class="mx-imgBorder"]
	> [![slider control](../media/lab-5.png)](../media/lab-5.png#lightbox)

1. Leave the Edge window open.

### Create a workspace

In this task, you will create a workspace. You will also upgrade your
account to Power BI Pro.

All content you develop in this course will be added to this workspace.

1. To create a workspace, in the **Navigation** pane (located at the
    left), click **Workspaces**, and then click **Create a Workspace**.

	> [!div class="mx-imgBorder"]
	> [![Workspaces then click Create a Workspace](../media/lab-6.png)](../media/lab-6.png#lightbox)

1. When prompted to upgrade your account to Power BI Pro, click
    **Try Free**.

	> [!div class="mx-imgBorder"]
	> [![try free](../media/lab-7.png)](../media/lab-7.png#lightbox)

A Power BI Pro license is required to create and work with workspaces.
It's also required when sharing content. The trial will allow you to
work with Pro features for up to 60 days.

1. When prompted to start the 60-day free Pro trial, click
    **Start Trial**.

	> [!div class="mx-imgBorder"]
	> [![start trial](../media/lab-8.png)](../media/lab-8.png#lightbox)

1. When the trial has been extended, click **Close**.

1. Repeat the first step in this task to create the workspace.

1. In the **Create a Workspace** pane (located at the right), in the
    **Workspace Name** box, enter a name for your workspace.

The name you enter must be unique within the tenant. We suggest you name
the workspace **Sales Analysis**, and that you also append your
initials. For example, the name could be **Sales Analysis AB**.

1. To create the workspace, at the bottom of the pane, click **Save**.

	> [!div class="mx-imgBorder"]
	> [![save](../media/lab-9.png)](../media/lab-9.png#lightbox)

1. In the **Navigation** pane, notice that your workspace is open.

	> [!div class="mx-imgBorder"]
	> [![sales analysis](../media/lab-10.png)](../media/lab-10.png#lightbox)

1. You will publish content to the workspace in **Lab 03D**.

### Open Power BI Desktop

In this task, you will open Power BI Desktop, and then sign in using
your account.

1. To open the Power BI Desktop, on the taskbar, click the
    Microsoft Power BI Desktop shortcut.

	> [!div class="mx-imgBorder"]
	> [![Microsoft Power BI Desktop shortcut](../media/lab-11.png)](../media/lab-11.png#lightbox)

1. When prompted, click **Sign In**.

	> [!div class="mx-imgBorder"]
	> [![sign in](../media/lab-12.png)](../media/lab-12.png#lightbox)

1. Complete the sign in process by using the **MySettings.txt** account
    details.

1. In Power BI Desktop, at the top-right corner, verify that you see
    your account.

	> [!div class="mx-imgBorder"]
	> [![verify your account](../media/lab-13.png)](../media/lab-13.png#lightbox)

1. Leave Power BI Desktop open.

You will commence the development of a data model in **Lab 02A**.

### Update the lab database

In this task, you will run a PowerShell script to update data in the
**AdventureWorksDW2020** database.

1. In File Explorer, inside the **D:\\DA100\\Setup** folder,
    right-click the **UpdateDatabase-1-UpdateAccount.ps1** file, and
    then select **Run with PowerShell**.

	> [!div class="mx-imgBorder"]
	> [![Run with PowerShell](../media/lab-14.png)](../media/lab-14.png#lightbox)

1. In the **Windows PowerShell** window, when prompted to enter your
    account, paste in your account name from the **MySettings.txt**
    file.

	> [!TIP]
	> To paste into the **Windows PowerShell** window, right-click at the
	**Account** prompt.

	> [!div class="mx-imgBorder"]
	> [![account name](../media/lab-15.png)](../media/lab-15.png#lightbox)

1. To update the database, press **Enter**.

1. When prompted to press any key to continue, press **Enter** again.

The **AdventureWorksDW2020** database has been updated to use your
account details. You are now the salesperson Michael Blythe, whose sales
performance is measured by the sales of three sales territory regions:
US Northeast, US Central, and US Southeast.

These facts will become relevant when implementing row-level security in
**Lab 03B**.

[!INCLUDE [](../../../includes/power-bi-lab-end.md)]