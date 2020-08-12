The purpose of this hands-on lab is to configure entity permissions to secure access to Common Data Service records.

The exercises work best when you have sample data to work with. Depending on the environment that you are working with, you might want to install some sample data to assist with the exercises. Microsoft Power Platform does provide the ability to add sample data as needed. If the environment that you are working in does not have sample data installed, follow the steps in the [Add or remove sample data](https://docs.microsoft.com/power-platform/admin/add-remove-sample-data/?azure-portal=true) documentation to install the sample data into your environment.

## Learning objectives

At the end of these exercises, you will be able to:

- Open the Power Apps portals Studio to configure an entity list to use entity permissions.
- Create and assign a web role.
- Create an entity permission record.
- Link the entity permission to the web role and associate the web role to a Common Data Service contact.

### Prerequisites

For this exercise, you will need to have the following parameters set up in your environment:

- A Power Apps portal that is provisioned. If you do not have a Power Apps portal available, follow the [Create Portal](https://docs.microsoft.com/powerapps/maker/portals/create-portal/?azure-portal=true) instructions to create one.

- Access to the Power Apps maker portal.

## Scenario

Your organization has provisioned a Power Apps portal and wants to create a directory of partner organizations. After initial provisioning of the portal pages and the entity lists to manage the partner directory, administrators have discovered that access to the data has not been restricted, as initially planned, and that the directory is publicly available.

The company wants to restrict access to the data to authenticated users only.

### High level steps

To finish the exercise, complete the following tasks:

- Add a webpage with a list component that shows the account entity.
- Enable **Entity Permissions** to restrict the viewing of accounts to authenticated users only.
- Register a new user on the portal by using local authentication.
- Create a **Web Role** record.
- Create an **Entity Permission** record, providing global read access to the accounts entity.
- Link the portal user to the web role and link the web role to the entity permission.
- Confirm that the authenticated user has access to the list of accounts.

#### Launch portals Studio

1. Go to the Power Apps maker portal at [https://make.powerapps.com](https://make.powerapps.com/?azure-portal=true).
1. Make sure that the correct environment is selected in the environment selector in the upper-right corner.
1. From the **Apps** list, locate your portal app (Type = Portal).
1. Select the ellipsis (...) and then select **Edit**. The portals Studio will launch.

#### Create a webpage

1. From the command bar, select **+ New Page > Fixed Layouts > Page with title** template.
1. In the Properties pane, add the following values:
    - **Name** - Partner Directory
    - **Partial URL** - partnerdirectory

#### Add an entity list

1. On the canvas, select the page copy component and, from the toolbelt, select the **Components** icon and then add the **List** component.
1. Add the following values:
    - **Name** - Partner List
    - **Entity** - Account
    - **Views** - Active Accounts
1. Expand **Settings**.
1. Select **Enable entity permissions**.
1. Select **Save**.

#### Browse the website

Select the **Browse website** to view the page. You will receive a message indicating that you do not have permissions to view records.

#### Add a portal user

1. Select the **Sign in** menu item.
1. Select the **Register** tab.
1. Fill in the **email**, **username**, and **password** information.
1. Select **Register**.
   The portal profile page will appear.
1. Fill in the **First Name** and **Last Name** fields and then scroll down and select **Update**.
1. Close the portal.

#### Add a web role and assign a contact

1. Go to the Power Apps maker portal at [https://make.powerapps.com](https://make.powerapps.com/?azure-portal=true).
1. Make sure that the correct environment is selected in the environment selector in the upper-right corner.
1. From the **Apps** list, locate and open the Portal Management app (Type = Model-driven).
1. In the **Security Area**, select **Web Roles**.
1. Add a new web role record, and then enter the following values:
    - **Name** - Partner List Web Role
    - **Website** - Starter Portal
1. Save the record.
1. Select the **Related** tab.
1. Select **Contacts**.
1. Select **Add Existing Contact**.
1. From the list on the right side, select the contact that you registered on the portal.
1. Select **Add**.

#### Create an entity list

1. In the Portal Management app, select **Entity Permissions**.
1. Add a new entity permission record, and then enter the following values:
    - **Name** - Account Entity Permission*
    - **Entity Name** - Account
    - **Website** - Starter Portal
    - **Scope** - Global
1. In the **Privileges** section, select the **Read** check box.
1. Save the record.

#### Associate a web role

1. In the **Account Entity Permission*** record, scroll down to the **Web Roles** section.
1. Select **Add Existing Web Role**.
1. From the right lookup, select **Partner List Web Role**.
1. Select **Add**.

#### Verify access

1. Go to the Power Apps maker portal at [https://make.powerapps.com](https://make.powerapps.com/?azure-portal=true).
1. Make sure that the correct environment is selected in the environment selector in the upper-right corner.
1. From the **Apps** list, locate your portal app (Type = Portal).
1. Select the ellipsis (...) and then select **Edit**. Power Apps portals Studio will launch.
1. Select **Browse website**.
    > [!NOTE]
    > Browsing the website within portals Studio will refresh the portal cache.
1. Select **Sign in** and then enter the username and password for the portal user that you previously created.
1. Go to the **Partner Directory** page, where you should be able to view the list of account records.
    > [!div class="mx-imgBorder"]
    > [![Partner List](../media/exercise-entity-permissions.png)](../media/exercise-entity-permissions.png#lightbox)

1. Select the *username* and then select **Sign-out**. The page should display a message about not having permissions to view records.
