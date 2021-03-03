In this exercise, you'll create a flow that copies a selected folder and then adds information about the created backup in a Microsoft Excel file. 

To create the flow:

1. Launch Power Automate Desktop and then select the **New flow** button in the console.

    ![The New flow button in the console.](..\media\exercise-new-flow-button.png)

1. Choose a name for your flow and then select the **Create** button. For this example, the flow is named **Backup flow**.

    ![The Build a flow dialog box.](..\media\exercise-build-a-flow-dialog.png)

1. When the flow designer is launched, add a **Display select folder dialog** action to prompt users to select a folder.

    ![The Display select folder dialog action.](..\media\exercise-display-select-folder-dialog-action.png)

1. Use a **Copy folder** action to copy the selected folder in your documents folder. 

    ![The Copy folder action.](..\media\exercise-copy-folder-action.png)

1. Deploy a **Launch Excel** action to open the Excel file that contains the logs about your backup activity. 

    1. If this file doesn't already exist, create a blank Excel spreadsheet named **Logs.xlsx** in the **Desktop** folder so that the automation will be able to open it as an existing file. 

    ![The Launch Excel action.](..\media\exercise-launch-excel-action.png)

1. To find the first available row in the Excel file, use the **Get first free column/row from Excel worksheet** action.

    ![The Get first free column/row from Excel worksheet action.](..\media\exercise-get-first-free-column-row-from-excel-worksheet-action.png)

1. To get a timestamp of the current time for the logs, use the **Get current date and time** action.

    ![The Get current date and time action.](..\media\exercise-get-current-date-and-time-action.png)

1. Deploy two **Write to Excel worksheet** actions to add log information in the Excel file. 

    1. Use the first **Write to Excel worksheet** action to write the copied folder's path in the first column.

        ![The Write to Excel worksheet action writing the folder's path.](..\media\exercise-write-to-excel-worksheet-action.png)
    
    1. Use the second deployed action to add a timestamp in the second column of the first available row.

        ![The Write to Excel worksheet action writing the timestamp.](..\media\exercise-write-to-excel-worksheet-second-action.png)

1. Use a **Close Excel** action to save and close the Excel file.

    ![The Close Excel action.](..\media\exercise-close-excel-action.png)

1. To test that the flow runs as expected, select the **Run** button, pick a folder, and then check that the log file has been updated.

    ![The final flow and the run button.](..\media\exercise-final-flow.png)

1. If the flow works as expected, save it and then close the flow designer. 
