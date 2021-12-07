Microsoft Cloud for Financial Services solutions depends on data from several sources. As a maker, you will be configuring the solutions and confirming the data is accurately represented to your end users.

Each solution you deploy will have certain dependencies. Each of these will be presented as you begin the deployment process. It is required that you resolve each of these prior to deploying the solutions. The configure dependencies page guides you through installing and configuring dependencies. The dependencies list will vary, depending on the solutions you may already have deployed. Once started, the deployment will continue in the background. Depending on the exact solutions you have selected, this may take some time. You will be notified with an email upon completion.

## Data model

The retail banking data model contains several tables to support the business of banking in addition to the core Microsoft Dataverse tables. You can learn more about the common date model, and the retail banking data model on [Microsoft docs](/dynamics365/industry/financial-services/overview-data-model/?azure-portal=true). The list below is not complete but represents the key tables and how they benefit the experience.

**Branch:** The branch schema in the retail banking data model will support branches in the bank, including:

-   Branch number

-   Name

-   Manager

-   Address

-   Connection to the customer table to capture customer's primary branch

**Customer:** The customer schema in the retail banking data model will support people and small or medium companies as customers of the bank. The schema includes:

-   Contact and Account tables that include financial details related to know your customer (KYC) and know your business (KYB)

-   Flags indicating whether data is controlled by an external system

-   Tables locked for updates from external systems only

**Groups and relationships:** The groups and relationships schema in the retail banking data model supports groups, such as households and partnerships. Features and capabilities include:

-   A new table that represents groups, including types (for households and partnerships).

-   Groups can be associated with all/some/none of the financial holdings owned by its members, which then defines the financial strength of the group, through total income, assets, and liabilities.

-   Each group can have a primary member. For any member, a main group of household type can be set.

**Life events:** To help keep track of key moments of the customer, the retail banking data model will include a life moment table. Moments will capture a wide range of life event types:

-   Birthday: Date of birth, which is managed via the Contact table

-   Personal status: The contact's marital status

-   Family: Represents the birth or adoption of children in the family

-   Education: Any education events including graduation from high school or college

-   Home: Purchase or sale of a home

-   Car: Purchase or sale of a car

-   Health: Significant medical event, such as surgery, which may require lending or sale of investment

Relevant alerts for life moments are predetermined based on the event type and are defined in the data model.

**Loan application:** The loan application schema in the retail banking data model supports loan applications. The schema provides the following capabilities:

-   Enable bank to manage the application more seamlessly

-   Reflect latest status in the system

**Financial holdings:** The financial holdings schema in the retail banking data model supports the financial holdings of bank customers.

Financial holdings are categorized as one of the following:

-   Account: Either checking or savings accounts

-   Credit line: Credit limit that was approved by the bank

-   Loan: Secured, unsecured, or mortgage loans

-   Investment: Investment accounts including portfolios of funds, stocks, bonds, and other assets

-   Long-term saving: Deposits that are often locked for an extended period of time, like provident funds

Each category defines the details associated with the financial holding, and possible financial instruments that can be connected to it, including:

-   Credit and debit cards, which can be associated with an account or a credit line

-   Standing order or direct debit/deposit, which can be associated with an account

-   Overdraft, which can be associated with an account

-   Relevant alerts for financial holdings are predetermined based on the category and instruments defined in the data model.

Customers have a many-to-many relationship with financial holdings, with each connection further classified by the role of the customer toward the holding, such as owner or cosigner.

### Security roles

Depending on the solutions you deploy, you'll have to assign other security roles to your users so they can access the individual apps. The following roles are deployed with the noted solutions. Remember, if you extend the solutions with your own tables and customizations, you may have to amend these permissions for your users to have an optimal experience.

|     Solution                    |     Security role                                                                                                                                                                                                                                          |
|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     Unified customer profile    |     Basic user   (or another core role with access to Power Platform)    MC4FSI basic user    Retail banking - contributor    Relationship manager     Financial intelligence user (optional for Unified customer profile with   Customer intelligence)    |
|     Customer onboarding         |     Basic user   (or another core role with access to Power Platform)    MC4FSI basic user    Loan manager                                                                                                                                                 |

> [!NOTE]
> Users who access Unified customer profile without a role that allows editing rights on Contact records will see on the top of the application notification:

***Read-only: You don't have access to edit this record.***

With the above roles for Unified customer profile, users will be able to edit Life events, Relationships, and Groups. Add Contact editing rights to a user to remove this message.

## Other relevant Microsoft technologies

Each Dynamics 365 financial services solution has dependencies on other Microsoft apps and features that might require other licenses.

These dependencies can be divided into two categories:

**Pre-deployment:** Microsoft Cloud Solution Center lets you view these pre-deployment dependencies before deploying the solution; you can select **Quick view** for a solution.

**Post-deployment:** You can configure other capabilities for your financial services solution after deployment, such as integration with Microsoft Teams and Microsoft Power BI. Microsoft Cloud Solution Center lets you view these post-deployment dependencies after deploying the solution.

Tailor a unified customer profile based on customer insights to offer a more personalized and relevant experience. Onboard customers easily to provide easy access to loan apps and self-service tools. Improve your process workflows and communication with Collaboration Manager.

|     Solution                                   |     Description                                                                                                                                                                                                                                                                                                                              |     Powered by                                                                                 |
|------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|
|     Unified customer profile                   |     Tailor customer experiences via a   360-degree view of the customer and, bringing together financial, behavioral,   and demographic data.                                                                                                                                                                                                |     Dynamics 365 Customer Insights and   Power Apps                                            |
|     Retail banking churn prediction            |     An AI-based model powered by   Dynamics 365 Customers Insights that helps predict the likelihood of a   customer leaving the bank.                                                                                                                                                                                                       |     Dynamics 365 Customer Insights, AI   models                                                |
|     Customer onboarding                        |     Provides customers with easy access   loan apps and self-service tools, streamlining the loan process to enhance   customer experience and loyalty while increasing organizational and employee   productivity.                                                                                                                          |     Microsoft Power Platform                                                                   |
|     Banking customer engagement   (Preview)    |     Personalizes every interaction with   financial understanding to engage with customers on their preferred channel   in a meaningful way, while intelligently managing their journeys across   channels, to reduce churn and time to resolution.                                                                                          |     Dynamics 365 Customer Service and   Omnichannel Add-on, Dynamics 365 Customer Insights    |
|     Collaboration Manager                      |     Helps banks bring collaboration   seamlessly into their lending workflows, improving process orchestration from   front office to back office, and facilitating omnichannel communications with   customers, thereby improving organization and employee productivity,   unlocking value creation, and enhancing customer experience.    |     Microsoft 365 and the Microsoft   Power Platform                                           |
|     Retail banking data model                  |     The retail data model and pre-built   connectors enable data interoperability to unify and enrich data from   multiple systems. The unified data provides insights for actions and   accelerates business, AI, and team productivity workflows.                                                                                          |     -                                                                                          |
