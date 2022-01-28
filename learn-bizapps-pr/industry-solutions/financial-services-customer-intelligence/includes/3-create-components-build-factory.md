In this exercise, you'll build a data pipeline in Microsoft Azure Data Factory. In Data Factory, you'll ingest sample data from Dataverse into Microsoft Azure Data Lake Storage, which is a set of capabilities that is dedicated to big data analytics. To complete this exercise, you'll need a Microsoft Azure subscription with administrator privileges. For more information, see [Introduction to Azure Data Lake Storage Gen2](/azure/storage/blobs/data-lake-storage-introduction/?azure-portal=true).

## Task 1: Create a resource group in Azure

In this task, you'll create a resource group to house your other Azure components. For more information, see [Manage Azure Resource Manager resource groups by using the Azure portal](/azure/azure-resource-manager/management/manage-resource-groups-portal/?azure-portal=true).

1. Use an In-private or Incognito window and go to the [Microsoft Azure portal](https://portal.azure.com/?azure-portal=true).

1. In the search box, search for and select **Resource groups**.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of Microsoft Azure search box with Resource groups selected.](../media/groups.png)](../media/groups.png#lightbox)

1. Select **Create** to create a new resource group.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of Resource groups showing the Create button.](../media/create-group.png)](../media/create-group.png#lightbox)

1. Name the new resource group **fsiResourceGroup**, select the appropriate **Region**, select **Review + create**, and then select **Create**.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Basics tab in the Create a resource group screen, showing Region filled in and the Review + create button.](../media/review-create.png)](../media/review-create.png#lightbox)

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Review + create tab in the Create a resource group screen, showing the Validation passed message and the Create button.](../media/validated.png)](../media/validated.png#lightbox)

1. After the resource group has been created, go to **Access control (IAM)** and select **Add role assignment**.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Check access tab on the Access control (IAM) page, showing the Add role assignment button.](../media/role.png)](../media/role.png#lightbox)

1. Select **Owner** and then select **Next**.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Add role assignment screen, showing Owner selected and the Next button.](../media/owner.png)](../media/owner.png#lightbox)

1. Select the **+ Select members** option, search for and select your user, and then select the **Select** button.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of Add role assignment on the Members tab with Select members showing.](../media/members.png)](../media/members.png#lightbox)

    > [!div class="mx-imgBorder"]
    > [![Screenshot of Selected members showing Allen Contoso and the Select button.](../media/selected.png)](../media/selected.png#lightbox)

1. Select **Review + assign** to assign the role.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of Add role assignment on the Members tab with the Review + assign button showing.](../media/review-assign.png)](../media/review-assign.png#lightbox)

Congratulations, you've created a resource group in Azure.

## Task 2: Create an Azure storage account

In this task, you'll create a storage account within the resource group that you created in the previous task. An Azure storage account contains all your Azure storage data objects and provides a unique namespace for your Azure storage data. For more information, see [Azure storage documentation](/azure/storage/blobs/data-lake-storage-introduction/?azure-portal=true).

1. Go to the **Resource group** that you created in the previous task.

1. Select **Create**.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the resource group showing the Create button.](../media/create-storage.png)](../media/create-storage.png#lightbox)

1. Scroll down the page to **Storage account** and then select **Create**.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Create a resource screen, showing the Storage account.](../media/create-resource.png)](../media/create-resource.png#lightbox)

1. Select the resource group (**fsiResourceGroup**) that you created in the previous task.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Project details screen, showing the Subscription field and the Resource group filled in.](../media/details.png)](../media/details.png#lightbox)

1. Scroll down to **Instance details** and enter the following information. Then, select **Review + create > Create**.

    - **Storage account name** - fsistorageacct

    - **Region** - The same region that you selected for your resource group

    - **Performance** - Default

    - **Redundancy** - Default

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Instance details page filled in and the Review + create button.](../media/instance-details.png)](../media/instance-details.png#lightbox)

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Create a storage account page, showing Validation passed and the Create button.](../media/storage-validation.png)](../media/storage-validation.png#lightbox)

1. After the storage account has been created, go to **Access Control (IAM)** and select **Add role assignment**.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of Access Control (IAM) showing the Add role assignment button.](../media/access-control.png)](../media/access-control.png#lightbox)

1. **Search** for and select **Storage Blob Data Contributor**.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of Add role assignment with search results for Storage Blob Data Contributor.](../media/blob.png)](../media/blob.png#lightbox)

1. Select **Members** and then select the **+ Select members** option. Find your user and then select the **Select** button.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of Add role assignment, on the Members tab, with the Select members button showing.](../media/members-tab.png)](../media/members-tab.png#lightbox)

    > [!div class="mx-imgBorder"]
    > [![Screenshot of Selected members with one member showing.](../media/selected.png)](../media/selected.png#lightbox)

1. Select **Review + assign** to assign the role.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Members tab on the Add role assignment page, showing the Review + assign button.](../media/role-assign.png)](../media/role-assign.png#lightbox)

1. Return to **Access Control (IAM)** and select **Add role assignment** again.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Access Control (IAM) page, showing the Add role assignment button.](../media/access-control.png)](../media/access-control.png#lightbox)

1. Select **Owner** and then select **Next**.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Role tab on the Add role assignment page, with Owner selected.](../media/owner-role.png)](../media/owner-role.png#lightbox)

1. Select the **+ Select members** option. Find your user and then select the **Select** button.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Select members option on the Members tab on the Add role assignment page.](../media/select-members.png)](../media/select-members.png#lightbox)

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Selected members page, showing Allen Contoso.](../media/selected.png)](../media/selected.png#lightbox)

1. Select **Review + assign** to assign the role.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Members tab on the Add role assignment page, showing the Review + assign button after member selection.](../media/assign.png)](../media/assign.png#lightbox)

1. Return to **Access Control (IAM)** and select **Add role assignment** one more time.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of Access Control and the Add role assignment button selected again.](../media/access-control.png)](../media/access-control.png#lightbox)

1. **Search** for and select **Storage Blob Data Contributor**. Select **Next**.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of search results for Storage Blob Data Contributor.](../media/blob.png)](../media/blob.png#lightbox)

1. Select **Members** and then select **+ Select members**. Search for and select **Dynamics 365 AI for Customer Insights**.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Add role assignment page, showing the Members tab again.](../media/members-tab.png)](../media/members-tab.png#lightbox)

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Selected members page, showing Dynamics 365 A.](../media/dynamics.png)](../media/dynamics.png#lightbox)

1. Select **Review + assign** to assign the role.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Review + assign button on the Add role assignment page.](../media/assign-role.png)](../media/assign-role.png#lightbox)

Congratulations, you've created a storage account in your Azure resource group.

## Task 3: Create a staging Azure container for Customer Insights

In this task, you'll create an Azure container from the storage account that you created in the previous task. You'll use this Azure container as a staging area for data that will be ingested by Customer Insights. For more information, see [Azure Container Instances documentation](/azure/container-instances/?azure-portal=true).

> [!IMPORTANT]
> To download the JSON files that you'll use to transform the data for Customer Insights, go to [create-azure-components-json.zip](https://github.com/MicrosoftDocs/mslearn-developer-tools-power-platform/blob/master/financial-services-industry/create-azure-components-json.zip/?azure-portal=true). In the GitHub page that appears, select the **Download** button.

1. In the storage account that you created in the previous task, select **Containers**.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Storage account page, showing the Containers option under the Data storage area.](../media/containers.png)](../media/containers.png#lightbox)

1. Select **+ Container**, fill out the following information, and then select **Create**.

    - **Name** - fsicistagingcontainer

    - **Public access level** - Container

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the New container dialog filled in.](../media/container.png)](../media/container.png#lightbox)

1. Open the newly created container and then select **Manage ACL**.

    > [!div class="mx-imgBorder"]
    > ![Screenshot of Settings with Manage ACL selected.](../media/manage.png)

1. Under **Access permissions**, select **Add principal**. Search for and select **Dynamics 365 AI for Customer Insights**. Select the **Read**, **Write**, and **Execute** permission checkboxes and then select **Save**.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Access permissions tab on the Manage ACL page, showing Dynamics 365 AI for Customer Insights with all three permission checkboxes selected.](../media/add-principal.png)](../media/add-principal.png#lightbox)

1. Follow the same steps under **Default permissions** tab for **Dynamics 365 AI for Customer Insights** .

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Default permissions tab on the Manage ACL page, showing Dynamics 365 AI for Customer Insights with all three permission checkboxes selected.](../media/default.png)](../media/default.png#lightbox)

1. Go to **Overview** and select **Add Directory**.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the container overview showing the Add Directory button.](../media/add-directory.png)](../media/add-directory.png#lightbox)

1. Enter **Corpus** in the **Name** field and then select **Save**.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Add Directory dialog with Name set to Corpus.](../media/add.png)](../media/add.png#lightbox)

1. Open the new **Corpus** directory and then select **Add Directory**. Enter the word **resolved** in the **Name** field.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Add Directory dialog with the Name field set to resolved.](../media/resolved.png)](../media/resolved.png#lightbox)

1. Open the new **resolved** folder. Select **Upload** to upload the JSON files that were linked at the beginning of this task. You'll use these JSON files to transform the data for Customer Insights.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the container overview showing the list of JSON files.](../media/json.png)](../media/json.png#lightbox)

Congratulations, you've created a staging Azure container for Customer Insights.

## Task 4: Create a new Azure Synapse link

In this task, you'll create a new Microsoft Azure Synapse link to connect your Dataverse environment to your Azure storage account.

1. Use an In-Private or Incognito window and go to [Power Apps](https://make.powerapps.com/?azure-portal=true).

1. Select the correct environment from the **Environment** dropdown menu in the upper-right corner.

    > [!div class="mx-imgBorder"]
    > ![Screenshot of the Environment dropdown menu.](../media/environment.png)

1. Expand **Dataverse** and then select **Azure Synapse Link**. Select **New link**.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of Microsoft Azure Synapse Link for Dataverse showing the New link button.](../media/link.png)](../media/link.png#lightbox)

1. Select your Azure **Subscription**, **Resource Group**, and **Storage account**, and then select **Next**.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the New link wizard on the Select Storage Account page showing the fields filled in.](../media/new-link.png)](../media/new-link.png#lightbox)

1. Filtering by keyword, search for and add the following 18 tables. When you're finished, select **Save**.

    - Bank

    - Branch

    - Contact

    - Customer financial holding

    - FH account

    - FH investment

    - FH line of credit

    - FH loan

    - FH saving

    - FI card

    - FI direct debit

    - FI overdraft

    - FI standing order

    - Financial holding

    - Financial holding instrument

    - Group

    - Group financial holding

    - Group member

    - Life event

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the New link wizard on the Add Tables page showing Life event added.](../media/add-tables.png)](../media/add-tables.png#lightbox)

1. When you're finished adding the tables, the tables should populate with data. This action will also create a new Azure container in your storage account that you can use to run your data pipeline in Azure Data factory.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Tables tab showing the 18 tables that you added.](../media/tables.png)](../media/tables.png#lightbox)

Congratulations, you've linked Dataverse to Azure Data Lake Storage by using Azure Synapse.

## Task 5: Create an Azure data factory

In this task, you'll create an Azure data factory within your Azure resource group. Microsoft Azure Data Factory is a cloud ETL service for scale-out, serverless data integration and data transformation. For more information, see [Azure Data Factory documentation](/azure/data-factory/?azure-portal=true).

1. In Azure, search for and select **Data factories**.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of Microsoft Azure showing Data factories in the search box.](../media/data-factories.png)](../media/data-factories.png#lightbox)

1. Select **Create** to create a new data factory.

    > [!div class="mx-imgBorder"]
    > ![Screenshot of the Data factories page, showing the Create button.](../media/create-data.png)

1. Fill out the following information:

    - **Subscription** - Your Azure subscription

    - **Resource group** - Your previously created resource group

    - **Region** - Same region as your resource group

    - **Name** - myfsidatafactory

    - **Version** - V2

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Create Data Factory page, showing the Basics tab with information filled in.](../media/create-data-factory.png)](../media/create-data-factory.png#lightbox)

1. Select the **Git configuration** tab and then select **Configure Git later**. Select **Review + create**.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Git configuration tab on the Create Data Factory page, showing the Configure Git later option.](../media/git.png)](../media/git.png#lightbox)

1. Select **Create** to create the Azure data factory.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Review + create tab on the Create Data Factory page, showing the Validation Passed message.](../media/validate.png)](../media/validate.png#lightbox)

Congratulations, you've created an Azure data factory.

## Task 6: Run a data pipeline in Azure Data Factory

In this task, you'll run a data pipeline in your Azure Data Factory by using an Azure Resource Manager (ARM) template. This data pipeline will ingest the sample data from the storage container that is linked to your Microsoft Cloud for Financial Services Dataverse environment. Then, the data pipeline will move the sample data to the staging container to be ingested by Dynamics 365 Customer Insights. For more information, see [Pipelines and activities in Azure Data Factory and Azure Synapse Analytics](/azure/data-factory/concepts-pipelines-activities/?azure-portal=true).

1. In your Azure Data Factory, go to **Overview** and then select **Open Azure Data Factory Studio**.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Data factory overview page showing the Open Azure Data Factory Studio tile under Getting started.](../media/open-studio.png)](../media/open-studio.png#lightbox)

1. Select your Azure data factory from the **Data Factory name** dropdown menu and then select **Continue**.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Select Data Factory dialog filled in and the Continue button.](../media/select-factory.png)](../media/select-factory.png#lightbox)

1. In the left navigation, select the **Manage** icon (toolbox), select **ARM template**, and then select the **Import ARM template** tile.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the ARM template page, showing the Import ARM template tile.](../media/template.png)](../media/template.png#lightbox)

1. Select **Build your own template in the editor**.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Select a template tab on the Custom deployment screen, showing the Build your own template in the editor option.](../media/custom.png)](../media/custom.png#lightbox)

1. Select **Load file** to upload the ARM template file that was provided in the lab resources.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Edit template dialog, showing JSON code.](../media/edit.png)](../media/edit.png#lightbox)

1. Return to your storage account. Go to **Access keys** and then select **Show keys**. Copy the **key1** key.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Storage account page, showing Access keys and Show keys selected.](../media/keys.png)](../media/keys.png#lightbox)

1. Edit the following parameters and then select **Save**:

    - **factoryName: defaultValue** - Your Data Factory name

    - **lnkFSICDM_accountKey: metadata** - The Storage Account key that you copied in the previous step

    - **lnkCICDM_accountKey: metadata** - The Storage Account key that you copied in the previous step

    - **lnkFSICDM_properties_typeProperties_url: metadata** - `https://STORAGEACCOUNTNAAME.dfs.core.windows.net`

    - **lnkCICDM_properties_typeProperties_url: metadata** - `https://STORAGEACCOUNTNAAME.dfs.core.windows.net`

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Edit template page, showing JSON code with parameters added.](../media/parameters.png)](../media/parameters.png#lightbox)

1. Select your **Resource group** from the dropdown menu. Fill in the remaining two parameters with the **Storage Account key** that you copied in the previous step. Select **Review + create**.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Custom deployment page filled in.](../media/custom-deployment.png)](../media/custom-deployment.png#lightbox)

1. Select **Create** to create the data pipeline.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Custom deployment page, showing a Validation Passed message.](../media/custom-validated.png)](../media/custom-validated.png#lightbox)

1. Return to your Data Factory and **refresh** the page. Select **Linked services**. Two connections should now display.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Data Factory page, showing two connections under Linked services.](../media/linked.png)](../media/linked.png#lightbox)

1. Select the **Author** (pencil) icon. Expand and select the **Pipeline**, and then enter the following parameters:

    - **pipFSICDM** - The full name of your storage container that is linked to Azure Synapse Link, for example, `dataverse-AZURESYNAPSE-unqab48050868e14fef9572fa91f02ff`

    - **pipCICDM** - The name of your Customer Insights staging storage container, for example, `cistagingcontainer`

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Factory Resources page with Pipeline selected and parameters added.](../media/pipeline.png)](../media/pipeline.png#lightbox)

1. To publish your changes, select **Publishing > Publish**.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Publish all dialog showing Pending changes and the Publish button.](../media/publish.png)](../media/publish.png#lightbox)

1. To enable the data flow debug option, select the **Data flow debug** field and then select **OK**. You should receive a detailed error message if the pipeline fails to run. It will take a couple minutes for this process to complete.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the Turn on data flow debug dialog.](../media/debug.png)](../media/debug.png#lightbox)

1. After you have turned on the **Data flow debug** toggle, select **Debug** and then select **OK** to trigger the pipeline.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the editor showing the Data flow debug toggle turned on.](../media/data-flow-debug.png)](../media/data-flow-debug.png#lightbox)

    > [!div class="mx-imgBorder"]
    > [![Screenshot of Pipeline run dialog showing parameters and an OK button.](../media/pipeline-run.png)](../media/pipeline-run.png#lightbox)

1. If the run is successful, you'll receive a status of **Succeeded** for the **Data flow**.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of Pipeline selected on the Factory Resources page, showing the Output tab listing pipeline runs with a status of Succeeded.](../media/succeeded.png)](../media/succeeded.png#lightbox)

1. Return to your Customer Insights staging storage container to observe data being populated in a newly created data folder.

    > [!div class="mx-imgBorder"]
    > [![Screenshot of the data folder populating with folders.](../media/folder.png)](../media/folder.png#lightbox)

Congratulations, you've successfully built and run a data pipeline in Azure Data Factory.
