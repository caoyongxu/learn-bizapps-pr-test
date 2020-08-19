To ensure the safety of the data and credentials used in your processes, WinAutomation offers some critical security properties. 

To enable these features:

1.	Navigate to the General tab of the Process properties dialog.

    ![The General Tab in the process properties dialog.](..\media\process-properties-general.png)

1.	Select the **Use Secure Screen** option. By enabling this feature, you can hide the content displayed on the screen when the selected process is run. 

    The screen will be turned blue, and no one will be able to see what the process does. The only visible window will be the Notification Window. This feature is helpful when a process handles files that contain sensitive information such as transaction records. 

    ![A checkbox that enables the Secure Screen feature.](..\media\use-secure-screen-process-properties.png)

1.	Select the **Encrypted & Password-Protected** option.

    This setting enables the encryption of the credentials used in the selected process. If you enable this option, you will be able to run the process normally, but you will need to enter a password for editing. 

    ![A checkbox that enables the process Encryption feature.](..\media\encryption-process-properties.png)

1.	If you enabled the **Encrypted & Password-Protected** option in the previous step, you must enter the password (encryption key). 

    ![ A pop-up window that prompts user to enter a password.](..\media\enter-password-process-properties.png)