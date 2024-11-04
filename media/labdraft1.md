# TechExcel: Copilot for M365 Extensibility


!IMAGE[extensibilityIMAGEbyChatGPT.jpg](instructions272221/extensibilityIMAGEbyChatGPT.jpg)

Contoso is a global company that sells a wide range of products and services through its e-commerce platform. Contoso has over 100,000 employees across different functions and locations and relies on various software tools and systems to manage its operations, customer relations, and innovation. 

- However, Contoso faces several challenges with its existing IT infrastructure and software solutions, such as: 

- Excessive costs and complexity of maintaining multiple legacy systems and applications. 

- Low productivity and collaboration among employees due to siloed information and workflows 

- Limited innovation and agility due to outdated and incompatible software tools 

- Security and compliance risks due to lack of visibility and control over data and devices 

===

###The key objectives of this hands-on lab are: 

- Explore the availability of pre-built Copilot extensibility solutions by examining the respective M365 graph connector and Copilot plugin (Teams application) catalogs. 

- Learn the deployment process and requirements of each by deploying a graph connector and Teams application that includes support for a plugin. 

- Discover the low-code tools and expertise needed to build M365 API plugins and Declarative Copilots using Copilot Studio. 

- Gain insights into the pro-code tools and expertise needed to build M365 API plugins and Declarative Copilots using Visual Studio Code and the Teams Toolkit. 

- Obtain hands-on experience leveraging each of these extensions to summarize, extract, and create content using Copilot. 

- Understand the architecture and code required to build a custom Graph Connector (pro-code walkthrough)




===

#Table of Contents

[Exercise 1: Enhance Copilot Experience with declarative agents](#exercise-1-enhance-copilot-experience-with-declarative-agents)

[Exercise 2: Build M365 Declarative Agents](#exercise-2-build-m365-declarative-agents)

[Exercise 3: Build M365 Copilot Plugin and include in Declarative Agent](#exercise-3-build-m365-copilot-plugin-and-include-in-declarative-agent)

[Exercise 4: Enhance Copilot Experience with Graph Connectors](#exercise-4-enhance-copilot-experience-with-graph-connectors)

[Exercise 5: Build a Custom Graph Connector](#exercise-5-build-a-custom-graph-connector)

===

# Exercise 1: Enhance Copilot Experience with declarative agents

###**Live demo**.

###Once the demo is complete, select **Next** to continue. 


<br>
[Table of contents](#table-of-contents)

===

# Exercise 2: Build M365 Declarative Agents

In this exercise, you will learn how to add a plugin to a declarative agent using the **pro-code** approach in **Visual Studio Code** with the **Teams Toolkit**. This method is essential for extending the capabilities of a declarative agent beyond the default M365 Copilot functionalities.

While plugins are not applicable to the basic M365 Copilot experience, they play a critical role in enhancing declarative agents. These agents, which can be customized to perform specific tasks, rely on plugins to interface with external systems like APIs.

It's important to note that with recent updates to the Teams Toolkit, the process for adding plugins has changed. Previously, plugins could be created directly from the Toolkit menu. Now, plugins can only be added through declarative agents, providing a more structured and configurable approach to agent development.

In this exercise, you'll walk through the steps to:
- Add an OpenAPI plugin to a declarative agent.
- Configure the plugin to interact with a sample API.
- Deploy the updated declarative agent and test its functionality.

<!-- Update to whatever external system API gets swapped in -->
By the end of this, you will have integrated a plugin into a declarative agent, enabling it to interact with external systems such as [ticketing platforms].
<!--
API endpoint used needs to change. 
Does not work for the user in the video demo provided, and he states that it will need to be swapped for another.
-->

### Task 01 - Add an OpenAPI plugin to the Teams Toolkit

1. [] In **Visual Studio Code**, navigate to the `\appPackage\declarativeCopilot.json` file from the previous Exercise.

1. [] Select the **Teams Toolkit** icon in the left-hand pane of **Visual Studio Code**.

1. [] Under the **DEVELOPMENT** section, select **Add Plugin**.

1. [] From the dropdown list, select **Start with an OpenAPI description document**.

1. [] Select **Enter OpenAPI Description Document Location** to provide a URL.

<!-- Update URL -->
1. [] Enter the URL of the API endpoint's JSON file and press **Enter**. It will recognize and identify the endpoints.

    +++Placeholder URL+++

<!-- Update operations used with API change -->
1. [] To manage the IT tickets, select the following endpoints:

    1. **GET /tickets**
    1. **POST /tickets**
    1. **OK**

1. [] Select the manifest for the declarative agent by selecting **manifest.json** from the dropdown list.

1. [] In the dialogue box, select **Add** to finalize adding the plugin.

    >[!note] At the bottom of the `declarativeCopilot.json` file, a new section called **actions** has been added. This section is configured by the `ai-plugin_1.json` file.

1. [] Navigate to the `\appPackage\ai-plugin_1.json` file. This file contains information about the plugin.

<!-- Update description with API change -->
1. [] Update the `description_for_human` field with a description of the plugin:

    +++This plugin can be used to [manage IT tickets].+++

<!-- Update references to tickets with API change -->
1. [] Review the file for details on how it supports retrieving tickets with a keyword and creating new tickets. Check the Adaptive Card definition for how ticket information gets displayed.

1. [] Scroll down to the **runtimes** section, which indicates that the plugin is implemented using the **OpenAPI** specification.

    >[!note] This specification is included in the project files so that Copilot can understand how the API works. You can find it in: `\appPackage\apiSpecificationFile\openapi_1.json`


===

### Task 02 - Deploy and test the declarative agent

<!--
Is the user already signed in to Teams Toolkit at this point of the lab? 
He's already signed in on the demo video but he mentions signing in at this point. 
If they're not signed in, there are 2 sign-in options: M365 or Azure - Which one should be used?
-->

1. [] Select the **Teams Toolkit** icon again.

1. [] Sign in to your account under the **Accounts** section. 

    <!-- Confirm if the user is signed in at this point based on lab guidance -->

1. [] Under the **LIFECYCLE** section, select **Provision**.

    >[!note] This will trigger the deployment of the declarative agent in the tenant of the signed-in account. Select **Output panel** from the notification in the lower-right corner to view the deployment process.

1. [] Open a browser and navigate to the Copilot chat:

    +++https://www.office.com/chat+++

<!-- Update reference to ticketing platform with API change -->
1. [] In the right-hand pane, select **Contoso IT Copilot** which we previously deployed.

    >[!note] The difference is that we've now added functionality to this Copilot through the declarative agent by connecting it to the [ticketing platform].

<!-- Update the prompt accordingly with API change -->
1. [] Test the Copilot by entering the following prompt:

    +++Please give me a list of the tickets assigned to Matteo Pagani.+++

    >[!note] Copilot will call the plugin to retrieve the requested information.

1. [] Select **Always allow** to grant permissions. Copilot will then generate a response.

<!--
The chatbot fails in his lab demo after this final step and he mentions that we will need to use a different API.
-->


===


### Task 03 - Add a new action to the declarative agent

Now that we have the declarative agent up and running, we'll see how to expand its capabilities by adding actions through Power Platform connectors available in **Copilot Studio**.

The outcome of this exercise is the successful creation of a new action within the declarative agent that interacts with external services. In this case, we'll use **Microsoft To-Do**.

Declarative agents are the primary way to extend the capabilities of Copilot, and plugins always run within the context of an agent. By adding plugins, you enable the agent to connect to external platforms and perform a wide variety of actions. We'll take a response from Copilot, and use the information it retrieves to create a new task in our To-Do list.



1. [] Navigate back to the **Copilot Studio** declarative agent configuration.

1. [] In the **Actions** section, select **+ Add action**.

    >[!note] From this section, you can access all the Power Platform connectors available in **Copilot Studio** to connect to a wide range of services. Many third-party connectors are built in as well.  
    >
    > You also have the option to **Add an API for a custom connector** at the bottom, where you can provide the OpenAPI specification of your API to connect the declarative agent. Close this option if opened.

1. [] In the search field, type +++add a to-do+++.

1. [] Select **Add a to-do (V3)** by **Microsoft To-Do (Business)**. The system will check the required permissions to connect.

    >[!note] This action will allow us to create to-do reminders based on the information and deadlines we receive from the declarative agent.  

    >[!alert] Do not select the connector by **Microsoft To-Do (Consumer)**.

1. [] Once loaded, select **Next**.

1. [] From **Step 2 of 3: Review inputs and outputs**, select the **Inputs** tab, then select **Edit inputs** to review the settings.

    >[!note] This action requires a list for where the to-do item will be added.  
    >
    > By default, the action uses **Dynamically fill with best option**, which allows the orchestrator engine to extract information from the prompt and automatically fill these parameters.

1. [] Select **Back** from the bottom-left, then select the **Outputs** tab to see the response this action will generate regarding the created to-do.

1. [] Select **Next** to proceed to **Step 3 of 3: Review and finish**.

    >[!note] This information will be used by Copilot to make various determinations, such as when to call the plugin, how to extract input parameters from the prompt, and how to generate the appropriate output.

1. [] Select **Finish** to add this action to the declarative agent.

    >[!note] Under the **Actions** section, you can now see the newly added connector.


===

### Task 04 - Publish and test the declarative agent


1. [] Select the **Publish** button in the top-right corner, then select **Publish** again in the new window to make the agent available for testing in the M365 Copilot interface.

1. [] Navigate back to the **Project Deadline Tracker** we added in **Microsoft Teams**.

1. [] In the chat prompt, enter:

    +++How to Generate Standard Financial Reports+++

    >[!note] This will generate a response based on information retrieved from the **ServiceNow** connector.

1. [] Enter the following prompt to create a task in **Microsoft To-Do**:

    +++Please create a task in To-Do, in the list called Tasks, to remind me to create a financial report. Include the information that you have just retrieved.+++

1. [] Select **Data to be shared with Project Deadline Tracker** to expand and review the task details.

    >[!note] The **title** is filled with the information retrieved from **ServiceNow**.  
    > The **folderId** displays the name of the task list in **To-Do**.  
    > **api_version** is an internal parameter of **Copilot Studio**.

1. [] Select **Always allow** to ensure the prompt is consistently and correctly interpreted by Copilot.

1. [] Select **Sign in to Project Deadline Tracker** to establish a connection with the **Microsoft To-Do** connector. This will open up the connections page in **Copilot Studio**.

1. [] In the right-most column for **Microsoft To-Do (Business)**, select **Connect**.

1. [] In the new window, select **Submit**. The **Status** column will now display **Connected**.

1. [] Go back to **Microsoft Teams**. In **Project Deadline Tracker**, select **New Chat** from the top-right corner of the middle pane.

1. [] Re-submit the previous prompts into the chat:

    +++How to Generate Standard Financial Reports+++

    +++Please create a task in To-Do, in the list called Tasks, to remind me to create a financial report. Include the information that you have just retrieved.+++

    >[!note] This time, you'll see a message confirming that a task has been created in your **To-Do** list.

1. [] Open the **Microsoft To-Do** application from the same account:

    +++https://to-do.office.com+++

1. [] From the left-hand navigation, select **Tasks**. The newly created task will be listed. Select it to expand and view the details.

    >[!note] While this action was performed using a **Microsoft** product, **Copilot Studio** supports many third-party platforms through its connectors.  
    >
    > The main goal of declarative agents and plugins is to help you connect to these platforms and extend Copilot's capabilities.



<!-- ### Agent builder - no code

### Copilot studio - low code

### SharePoint copilot agents - no code  -->


<br>
[Table of contents](#table-of-contents)

===

# Exercise 3: Build M365 Copilot Plugin and include in Declarative Agent

In this exercise, you’ll learn to create a declarative agent for Microsoft 365 Copilot using a low-code approach. This process leverages Copilot Studio to streamline configuration and deployment, turning complex settings into manageable, reusable properties that enhance consistency and speed.

As we proceed, you’ll see how each element of your setup—based on our previous discussions—translates seamlessly into the properties and configurations of a declarative agent. This approach provides a foundation for rapidly building and deploying agents without the need for extensive coding knowledge.

### Task - Build and install the agent

1. [] Open a new browser tab and go to +++www.copilotstudio.com+++ and sign in with your credentials.

1. [] On the left pane, select **Copilots**.

1. [] Select **Copilot for Microsoft 365**.

    !IMAGE[2024-10-12_15-27-03.jpg](instructions275998/2024-10-12_15-27-03.jpg)

    >[!note] Notice the section called **Agents**, this is our starting point.

1. [] In the Agents section, select **Add**.

    !IMAGE[+add.jpg](instructions275998/+add.jpg)

    >[!note] In the Agents section of Copilot Studio, you’ll find two options in the upper-right corner to configure your agent, allowing for flexibility based on your preference:
    >
    >**Conversational Configuration**: 
    >Select this option to leverage a guided, conversational experience. Here, you can simply describe what you’d like to create, and Copilot Studio will automatically populate the necessary fields and properties based on your input.
    >
    >**Skip to Configuration**: 
    >Choose this option to bypass the guided setup and jump directly to the configuration page, where you can manually enter all agent properties yourself. 
    >
    We will use the conversational approach to handle deadlines for a project.

1. [] Create an agent that can help track deadlines for a project by entering the following into the prompt:

    ```Copilot-wrap
    I want to create an agent that can help me to track deadlines for a project.
    ```

    >[!note] Behind the scenes, Copilot Studio gathers all the necessary information to populate the agent’s configuration automatically. With these details in place, my Copilot is now set up to efficiently track deadlines. 

1. [] Notice that your Copilot is asking if there are any other instructions on how your copilot should assist, For example a specific tone?

    !IMAGE[prompt1.jpg](instructions275998/prompt1.jpg)

1. [] Respond by entering the following:

    ```Copilot-wrap
    Please answer in a professional but simple way.
    ```

    >[!note] Copilot Studio is now ingesting this information to fine-tune the instructions that the declarative agent will use behind the scenes

1. [] Review the response and notice the final question. **Are there any topics or tasks this copilot shouldn't help with?**

1. [] Respond by entering the following:
    
    ```Copilot-wrap
    Please help only with questions around project deadlines.
    ```

    >[!note] For example, we can ensure that this declarative agent is tailored to assist only with the specific topic we want to cover, rather than responding to any general questions that might be asked.

1. [] Now the project has been finalized, in the upper-right of the page, select **Create**. 


    >[!note] Now, you'll observe how previous discussions within Copilot Studio translate into a series of configurable options and properties, collectively defining your declarative agent. Please allow a few moments for the system to compile and streamline these configurations.



1. [] Notice how the conversation with the compiler Studio was translated into the **Agent name**, **Description**, **Instructions**, and **Starter prompts**:

    - Agent name: Name of the project
    - Description: Purpose of the project
    - Instructions: Guidance that the declarative agent will follow when it needs to respond to the user
    - Starter prompts: Suggested prompts that will be displayed to the user when it will open up my declarative agent
    - Knowledge: Data used to inform and improve AI-generated responses.


    >[!knowledge]In addition to configuration, there are two other essential operations we can perform with a declarative agent: defining its knowledge base and setting up actions.
    >
    >Defining the knowledge base determines the types of data, files, and resources the Copilot can access to generate responses. By default, the agent uses only the model’s internal knowledge. 
    >However, we can expand its scope by allowing access to external sources, such as SharePoint sites or Graph connector sources, enhancing its ability to provide relevant insights.
    >
    >For instance, if I have a SharePoint site containing a document with key deadlines for the Contoso Project. By granting the agent access to this site, I can ensure it can pull in these specific project deadlines when needed.


1. [] In the **Knowledge** section, select **+ Add knowledge**.


1. [] Take note of the available knowledge sources. Here, you can connect to SharePoint sites or other Graph connector sources for the declarative agent to generate responses. 

    >[!knowledge] These sections also allow you to limit Copilot’s knowledge to specific sources, ensuring it uses only the selected information rather than all available knowledge. Once configured, permissions for this agent can be set up to reuse any added knowledge sources for different topics as needed.

1. [] Select **SharePoint**.

    !IMAGE[sharepoint1.jpg](instructions275998/sharepoint1.jpg)

1. [] Under **SharePoint link**, enter +++https://m365cpi81302533.sharepoint.com/sites/Deadlines+++ and then select **Add**.

1. [] On the **Add SharePoint** window, select **Add**.

    >[!note] Once SharePoint is added, Copilot will use it exclusively as its data source.

1. [] Return to the **Knowledge** section, select **+ Add knowledge**. 

1. [] Select **Advanced** to see available graph connectors in the tenant. 

1. [] Under **Enterprise data connections**, select **now ServiceNow Knowledge** to see the available connections.

1. [] Select **ServiceNowKB1** and then select **Add**.

    >[!note] This Graph connector is added as a knowledge source alongside the SharePoint site we configured earlier.
    >
    screenshot

1. [] In the **Additional settings** section, you'll find a **Web browsing** option. 

    >[!knowledge] By toggling this on or off, you can control whether Copilot—your declarative agent—can use information from the web in its responses, in addition to its internal sources.

1. [] Verify that **Web browsing** is disabled.

1. [] In the **Actions** section, you can add plugins to extend Copilot's capabilities.

    >[!note] More on this feature in later labs.

1. [] In the upper-right, select **Test** to test Copilot and ensure it responds appropriately. Try a few sample prompts to verify its accuracy and functionality.

    !IMAGE[copilotPrompt.jpg](instructions275998/copilotPrompt.jpg)

1. [] When you’re satisfied with the configuration and testing, select **Publish** in the upper-right to make the agent available in Microsoft 365 and Teams.

1. [] On the **Publish agent** window, there are some properties that can be customized. Update the following:

    | Item | Value |
    |:---------|:---------|
    | Short description   | +++This is a project that deadline tracker agent+++   |
    | Developer name   | +++Custom Developer+++   |

1. [] Select **Publish**.

    !IMAGE[PublishAgent.jpg](instructions275998/PublishAgent.jpg)
    
    >[!note] The publishing process will begin, and you’ll be presented with several options to distribute and deploy your agent.

1. [] In the **Availability options** window, under **Share link**, you can select **Copy** to send the link directly, allowing recipients to paste it into their browser to access the Teams store and download the agent.

1. [] Under **User access**, select **Show to my teammates and shared users** to view sharing options for people within your organization.

1. [] Review the **Share agent** window and then select **Cancel**.

1. [] Under **User access**, select **Show to everyone in my org** to share with the entire organization.

    >[!knowledge] Selecting the option to share with everyone triggers an approval workflow for the M365 tenant's IT administrator. 
    >
    >The administrator will need to access the Admin Center, navigate to Integrated Apps, and locate the request to publish the agent organization-wide. 
    >
    >Unlike other sharing options, publishing an agent to the entire organization adds it to the internal catalog, making it available across the company.
    
    >[!note] Shared apps can be found in **Teams**. In the left pane, go to **Apps** > **Built for your org**. All declarative copilots will be found here if published to the organization.

1. [] Review the information in the window and select **Cancel**.

    !IMAGE[shareWithOrg.jpg](instructions275998/shareWithOrg.jpg)

1. [] There is also a option to upload the agent directly as a custom app into Microsoft Copilot by downloading the agent as a .zip file. Now we will share the link to manually install the agent on the tenant.

1. [] Under **Share link**, select **Copy**.

1. [] Open a new browser tab, paste the link, and visit the URL to manually install the agent on the tenant.

1. [] Choose the web client of Teams. 

1. [] Select **Add** to add the agent.

    !IMAGE[addTracker.jpg](instructions275998/addTracker.jpg)

1. [] Once the agent is added, on the left pane, select the **View more apps** ellipsis (…), and then choose **Copilot**.

    !IMAGE[ellipsesCopilot.jpg](instructions275998/ellipsesCopilot.jpg)

1. [] In the right pane, confirm that the agent is listed, and select **Project Deadline Tracker**.

    !IMAGE[copilotPane.jpg](instructions275998/copilotPane.jpg)

    >[!note] Your declarative agent is now ready for use. You can test the agent by asking a question that pulls data from one of your specified knowledge sources.

1. [] In the prompt, enter the following:

    ```Copilot-wrap
    How do I generate a standard financial report?
    ```

1. [] Review the response from the agent. Notice that the answer is drawn from the ServiceNow article, specifically linked to the Financial Report knowledge base article.

    >[!note] If you were to select the link, it would redirect you to the ServiceNow instance. Although this instance is currently just an example and isn’t live, it would typically allow you to view the full knowledge base article.

>[!knowledge] In this example, we demonstrated how information on generating a financial report can be pulled from the knowledge base. Similarly, we could access information from a file stored in our SharePoint site.
>
When creating a declarative agent with the Copilot Studio experience, there are flexible ways to begin—either through a conversational setup or direct configuration. We focused on the knowledge aspect, showing how questions can be answered based on specific data sources, rather than the entire Microsoft 365 dataset.
>
We also reviewed publishing options and briefly introduced the Actions feature, which allows further customization of a declarative agent's capabilities.


<br>
[Table of contents](#table-of-contents)

===

# Exercise 4: Enhance Copilot Experience with Graph Connectors

###Objectives:

- Understand the purpose of a graph connector. 

- Understand where pre-built graph connectors are located and be aware that several of them are available. 

- Extend the M365 data graph and deploy a pre-built Graph connector. 

- Use Copilot to reason across data imported from the Graph connector – Hero prompts against pre-built Graph connector.




1. [] Sign into @lab.VirtualMachine(CLIENT01).SelectLink using the following credentials:

  | Item | Value |
  |:---------|:---------|
  | Username   | +++**@lab.VirtualMachine(CLIENT01).Username**+++   |
  | Password   | +++**@lab.VirtualMachine(CLIENT01).Password**+++   |


1. [] Open a browser and go to +++**admin.microsoft.com**+++.


1. [] Sign in using your M365 credentials.

    >[!note] The roles required to install a Graph Connector are Global Administrator or Search Administrator.


1. [] On the left menu, select **Show all** > **Settings** and select **Search & intelligence**.

    !IMAGE[yk29a8fy.jpg](instructions272221/yk29a8fy.jpg)


1. [] On the **Search & intelligence** page, select **Data Sources** > **+ Add Connection**.
   
    >[!note] Here you'll see the most popular prebuilt Graph connectors.


1. [] Select **Enterprise Websites** and near the bottom of the page, select **Next** to set the connection ID.

    !IMAGE[enterprisetile.jpg](instructions272221/enterprisetile.jpg)

    >[!knowledge] This website contains a collection of knowledge base articles about the product Device Manager Pro. Help Desk agents will use this data using Search in Microsoft 365 Copilot to look up information, troubleshoot, and provide solutions to customers experiencing issues with Device Manager Pro.


1. [] Enter the following to configure the Enterprise website and then select **Publish**:

    | Item | Value |
    |:---------|:---------|
    | Connection ID  | +++DeviceManagerPro+++   |
    | Display name   | +++DeviceManagerPro KB+++   |
    | Website URL   | +++https://ashy-rock-0cd34f10f.5.azurestaticapps.net/+++   |
    | Select who can search this data source   | **Everyone**  |
    | Manage Connector Results   | **Include Connector results in search**   |
    | Notice   | Read the information and select the box   |

    >[!note] On the **Select who can search this data source** field, **Everyone** is your only option when importing from a website.

1. [] Select **Done** once the connection creation process is complete.


1. [] Notice that the connection state is preparing to sync.


    >[!alert] This operation can take more than 60 minutes. It does take some time for the for the sync to complete. Continue to **Exercise 5** and come back to complete the remainder of **Exercise 4** once the data sync is complete.

1. [] Near the lower-right of the instructions pane, select **Next** three times to continue to **Exercise 5**. Come back to complete the remainder of **Exercise 4** once the data sync is complete. 

    >[!alert] After one hour, return to check on the status of crawl or proceed to using Search and Copilot if then sync has completed.


<br>
[Table of contents](#table-of-contents)

===

## Continue here once the sync is complete.

!IMAGE[readystatus.jpg](instructions272221/readystatus.jpg)

1. [] In the list of connections, under the **Required actions** column, select the notification to **Add description for Copilot**. Then select **Advanced settings**.

1. [] Select the **DeviceManagerPro** connection and in the flyout near the bottom, select **Edit**.
   
    >[!knowledge] This is important for copilot to understand what the purpose of this data is. And it helps copilot answer user questions because it understands that what this data will be used for.


1. [] Add the following description: 
   
    ```Description-wrap
    This Graph connector imports data from DeviceManagerPro Knowledge Base website. The articles are used to help IT professionals and users resolve common issues.
    ```

1. [] Select **Save and Proceed** twice.  
   

1. [] Select **Quick Publish**. 
   
    >[!note] We're publishing again because we updated the description.

1. [] Select **Publish**.

1. [] Select **Save and Close**.

1. [] Ignore any errors stating that the requested resource does not exist.

1. [] In the breadcrumbs near the top of the page, select **Data sources** to return to the Data sources page.

    !IMAGE[ignoreErrorandSelectBreadcrumb.jpg](instructions272221/ignoreErrorandSelectBreadcrumb.jpg)

1. [] The **DeviceManagerPro** connection is syncing, notice the connection state. The initial sync does a full website crawl.

    >[!alert] The sync takes some time to complete. The following steps show how to check on the progress of the sync.

1. [] To check on the status of the sync, select the Graph connector. 
   
1. [] In the flyout window, there's information about Details, Statistics, and Errors. 
   
1. [] Select **Detail** and expand **Current Crawl** to view current progress.

1. [] Select **Statistics** to get information about what's being indexed. 
   
1. [] Select **Error** to see if there are any errors happening during the crawl.


<br>
[Table of contents](#table-of-contents)

===

### Task 2.1 Find information with Search and using Copilot prompts


1. [] Open a new browser tab and go to +++**office.com**+++.

1. [] Select **Sign in**. If necessary, enter your credentials.

1. [] In the search box, enter +++KB1&#42;+++. The results are articles found in the Device Pro Knowledge Base that's now inside Microsoft 365.

    >[!knowledge] If the articles are not found, please continue to the next Exercise and come back once the articles are listed.

1. [] Select one of the articles and notice that it takes you to the website with the the detail of the argument.


### Task 2.2 Try a Copilot prompt.

We want to get started with this new data source, we're going to ask Copilot to suggest the prompts that we should follow up with.

1. [] On the left pane, select **Copilot**.

1. [] Enter the following prompt:

    ```Copilot-wrap
    Based on the content of the DeviceManagerPro knowledge base, suggest five Copilot prompts that demonstrate Copilot's ability to reason across data and provide valuable insights or relevant content.
    ```

    !IMAGE[copilotResponse1.jpg](instructions272221/copilotResponse1.jpg)

1. [] Review the five suggestions.


1. [] From the output of the previous prompt, enter the first option:

    ```Copilot-wrap
    What are the common causes and solutions for device enrollment issues in Contoso DeviceManagerPro?
    ```

    >[!knowledge] The prompt requests a step by step guide on how to troubleshoot app installation or update issues. It's giving us several references there to help us troubleshoot issues, and it's giving us a pointer back to the Knowledge Base article that it's getting from the Graph connector.

1. [] Review the results.

1. [] Enter the following prompt summarize device enrollment issues and highlight recurring problems:

    ```Copilot-wrap
    Summarize the key steps to resolve device enrollment issues in Contoso DeviceManagerPro and highlight any patterns or recurring problems .
    ```

1. [] Review the results.

1. [] Finally, enter the following prompt to draft an email summarizing the articles, with a ranking of severity:

    ```Copilot-wrap
    Please draft an email to my manager summarizing the DeviceMangerPro Knowledge base articles, include a ranking of severity as either High, Medium or Low.
    ```


<br>
[Table of contents](#table-of-contents)

===

# Exercise 5: Build a Custom Graph Connector 

In this exercise, you will review the core components and architecture necessary for building a custom Microsoft Graph Connector. 

By exploring the project structure and key code files, you will gain a deeper understanding of how to configure, create, and deploy a connector that integrates external data into Microsoft 365. 

This walkthrough covers essential files, such as the configuration, connection creation, and schema definition, guiding you through each stage of the process.

>## Project structure
>
>```Structure_Tree-nocopy
├── .devproxy
│   └── graph-connector-mocks.json
├── .gitignore
├── .vscode
│   ├── extensions.json
│   └── launch.json
├── README.md
├── devproxyrc.json
├── package.json
├── resultLayout.json
├── setup.ps1
├── setup.sh
├── src
│   ├── completeJobWithDelayMiddleware.ts
│   ├── config.ts
│   ├── createConnection.ts
│   ├── graphClient.ts
│   └── loadContent.ts
└── tsconfig.json
>```
>
>
### **resultLayout.json**
>
This file contains the result layout (Adaptive Card) for Microsoft Search.
>
### **setup.ps1** and **setup.sh**
>
These scripts create a new Microsoft Entra app registration using CLI for Microsoft 365. Both scripts invoke CLI using npx, so that you don't need to manually install CLI for Microsoft 365 before you run these scripts.
>
### **src/completeJobWithDelayMiddleware.ts**
>
This file contains the Microsoft Graph SDK Middleware to handle the long-running job of provisioning the connection's schema. The middleware waits for the job to complete before continuing. It waits the recommended 60 seconds before checking the job status.
>
### **src/config.ts**
>
This file contains the Graph connector configuration. You can define the schema for the external items, the URL to the item resolvers, and the connection name.
>
### **src/createConnection.ts**
>
This file contains the code to create the external connection and provision the schema.
>
### **src/graphClient.ts**
>
This file contains the Microsoft Graph SDK client instantiation code.
>
### **src/loadContent.ts**
>
This file contains the code to load content to import. The code is organized following the Extract-Transform-Load (ETL) principle.
>
### **tscconfig.json**
>
This file contains the TypeScript configuration for the project.





###Task 1 - Prepare the environment



1. [] On the Virtual Machine Windows taskbar, right-click **Start** (Windows icon), and select **Terminal (Admin)** to open a PowerShell session with Admin priviledges.

    >[!note] Select **Yes** to allow the Terminal app to make changes to your device.

1. [] On the PowerShell prompt, to install the *create-graph-connector* package run the following command:

    ```PowerShell-wrap
    npm i - create-graph-connector
    ```

    >[!note] This command will install the package which contains tools that will be made available to the system.

1. [] Change to the **Graph_Connector** directory by enter the following:

    ```PowerShell-wrap
    cd Graph_Connector
    ```

1. [] To begin creating the project, run the following:

    ```PowerShell-wrap
    npm create graph-connector
    ```

1. [] Install any needed packages.

1. [] Complete the *create-graph-connector* project creation wizard by entering the following:

  | Item | Value |
  |:---------|:---------|
  | Project name:   | +++**sampleconnector**+++   |
  | Graph connector name:   | +++**Sample Connector**+++   |
  | Graph connector description:   | +++**Imports data from Contoso app**+++   |
  | Connection ID (between 3 and 32 chars):   | +++**sampleconnector**+++   |
  | Template   | **TypeScript (basic)**   |


  !IMAGE[projectWizard_a1.jpg](instructions272221/projectWizard_a1.jpg)  

1. [] Change directory into the newly created project directory by entering the following:

    ```PowerShell-wrap
    cd .\sampleconnector\
    ```

1. [] Now open Visual Studio Code (VSCode) using the command below, to view the basic building blocks of a Graph connector:

    ```PowerShell-wrap
    code . 
    ```
    
    !IMAGE[97349gqa.jpg](instructions272221/97349gqa.jpg)

1. [] A new VSCode window will open. Select **Yes, I trust the authors**. Ignore any other pop-up windows.

    !IMAGE[trustAuthors.jpg](instructions272221/trustAuthors.jpg)

1. [] In VSCode, on the left menu, select **Explorer** to view the **SAMPLECONNECTOR** files.

    !IMAGE[vsCodeExplorer_a2.jpg](instructions272221/vsCodeExplorer_a2.jpg)

    >[!knowledge] The project that gets created by the template creator is based on TypeScript. All of the code that supports the custom connector is built with TypeScript. 
    >
    >However, you are not constrained to using TypeScript when creating Graph connectors, you can use any technology that's able to perform HTTP calls.
    > 
    >Examples of other technologies can be reviewed here: [Graph-Connectors-Samples](https://github.com/pnp/graph-connectors-samples "Graph-Connectors-Samples") and more information on Graph connectors can be found here: [Connectors Gallery](https://learn.microsoft.com/en-us/microsoftsearch/connectors-gallery "Connectors Gallery").



###Task 2 - Review the basic building blocks of a Graph connector

Now that the environment is built, we'll review the basic building blocks of the code that makes up the Graph connector. we'll cover the configuration file, then we'll cover creating the connection to the tenant, next we'll cover the schema, and finally we'll cover transforming and uploading the items.



###Task 2.1 - Review **config.ts** file

The config.ts file is a necessary prerequisite for creating a custom Graph connector. Some of the configurations are already injected by properties that you have defined when you created the project.

1. [] If necessary, expand the **src** folder and select **config.ts** to view its contents. 

1. [] Review lines 5-7 and verify the values that you entered when creating the project.

    !IMAGE[prepopulated-values_a3.jpg](instructions272221/prepopulated-values_a3.jpg)

1. [] Review lines 11-16. **urlToItemResolvers** contains the **baseUrls** array, which tracks if a user is sharing an item that belongs to this Graph connector.

    >[!knowledge] Typically, this is the only configuration that will be modified and its only modified because you need a way to resolve external items with the domain and website where this data can be consumed.

    !IMAGE[baseUrls_a4.jpg](instructions272221/baseUrls_a4.jpg)

1. [] Review lines 24-32. **searchResultsTemplates** provides the **id** and **layout**. The **id** is prepopulated because it's tied to the project ID, as seen in line 5. The **layout** is used for rendering content in the search results. 

    >[!knowledge]If you leave **layout** empty, it will use the standard template.

    !IMAGE[searchSettings_a5.jpg](instructions272221/searchSettings_a5.jpg)

###Task 2.2 - Review building blocks of creating a connection (calling the API)

In order to create a custom Graph connector, you must first call an API provided by the Microsoft graph to create a connection and you must supply **config.ts** as a parameter.



1. [] On the **Explorer** menu, select **createConnection.ts** to view its contents.

1. [] Review line 6. Notice the **createConnection()** function.

1. [] The call of the **createConnection()** function can be seen on line 19. We do this by performing an HTTP call from the endpoint of the graph APIs called **'/external/connections'**. We then provide the **id**, **name**, **description**, **activitySettings**, and the **searchSettings** properties as seen on lines 19-26.

    !IMAGE[APIcall_a6.jpg](instructions272221/APIcall_a6.jpg)

    >[!knowledge] Pre-populated information is coming from the config file except the **adaptiveCard** (line 16) which is loaded from the encoder in the file called **resultLayout.json**.
    >
    !IMAGE[resultLayout_a7.jpg](instructions272221/resultLayout_a7.jpg)


1. [] On line 19, **client** is an object from the sample template provided by the Microsoft Graph Client Library for TypeScript. It gives you a preconfigured client object to call Microsoft Graph, as seen in lines 8-12 of **graphClient.ts**, and manages authentication.

    >**View of graphClient.ts**
    !IMAGE[graphClient_a8.jpg](instructions272221/graphClient_a8.jpg)


1. [] Review lines 14-17. The contents of the **createConnections.ts** file are read and parsed as the value of the **layout** property for the search results.

    !IMAGE[layoutParsed_a9.jpg](instructions272221/layoutParsed_a9.jpg)


###Task 2.3 - Review building blocks of creating the Schema

After creating the connection, the next step is to define the schema. The schema describes the structure of your external items and the properties you want to bring into the table.

1. [] On the **Explorer** menu, select **config.ts** and review lines 34-64 to see how the schema is defined. 

1. [] On line 35, **baseType: 'microsoft.graph.externalItem** represents an entity imported from an external platform.

1. [] On lines 37-47, **properties:** represent the characteristics of the external item, such as **name**, **title**, **url**, and **iconUrl**. For each property, you can provide details like **type**, **queryable**, **searchable**, **retrievable**, and **labels**. 

    >[!knowledge] These map the information to a property in the M365 tenant. Customize to include all properties you want to import from the external class.
    >
    !IMAGE[baseTypeandProperties_a10.jpg](instructions272221/baseTypeandProperties_a10.jpg)


###Task 2.4 - Recall the Microsoft Graph again 

After defining the schema, the next step is to call Microsoft Graph again, this time targeting the External connectors endpoint with additional information.

1. [] In the Explorer menu, select **createConnection.ts** and review lines 32-53 to see how the second API call is made.

1. [] On line 38, review the addition of the **${ID}** and **/schema** to the connector.

    !IMAGE[addidandschema_a12.jpg](instructions272221/addidandschema_a12.jpg)

    >[!note] For example, in **config.ts** on line 5, the id is **sampleconnector**.
    >
    !IMAGE[ida11.jpg](instructions272221/ida11.jpg)

1. [] On line 40, review **.patch(schema)**, which sends an HTTP PATCH request with the schema data.

1. [] The schema creation operation can take 5 to 50 minutes. To handle this, **completeJobWithDelayMiddleware.ts** is injected into **graphClient.ts**. Review **completeJobWithDelayMiddleware.ts** for details.

    >**View of graphClient.ts**
    !IMAGE[completeJobWithDelay_a13.jpg](instructions272221/completeJobWithDelay_a13.jpg)
    >
    >[!knowledge] This middleware manages the delay and ensures that content ingestion doesn't start until both the connection and schema are created. 
    >
    This is important because the final step—uploading external items—can only be performed once the connection and schema are successfully created.

1. [] The schema creation process in **createConnection.ts** returns an HTTP response with a URL in one of the headers. This URL can be used to query the status of the schema operation.

1. [] On line 42-53, review the status objects that indicate whether the operation was completed successfully or is still pending.

    !IMAGE[status_a14.jpg](instructions272221/status_a14.jpg)
    
    >[!knowledge]Some objects from the Graph connector SDK simplify these operations. Instead of manually reading the value of the status, you can use **ExternalConnectors.ConnectionOperation** (line 40) to handle this automatically.


###Task 2.5 - Upload the items

The final step in creating a custom Graph connector is ingesting content into the tenant. Among the files, **loadContent.ts** requires the most customization. To ingest content, you must take the external content, convert it into external items, and submit it to the tenant. 

The process of converting external content into external item objects varies based on the data source. First, retrieve the items from your data source, then transform them accordingly.

1. [] In the Explorer menu, select **loadContent.ts**.

1. [] On lines 6-15, the Document interface represents our item.

    !IMAGE[intDoc_a15.jpg](instructions272221/intDoc_a15.jpg)

    >[!NOTE] This is a sample template. You would need to update it if there are additional parameters.

1. [] On lines 18-21, the **extract** function returns a collection of documents. 

    >[!knowledge]This is where you'll query your external data source to retrieve the items you want to import, transforming them into document objects by assigning them to the appropriate properties.

1. [] On lines 23-29, there's a function that generates a unique ID for each document.

    >[!knowledge]This is crucial because the ID is fundamental for ingesting content into the tenant. It must be unique and link back to the document's URL, allowing URL-to-item resolvers to accurately record activity.
    >
    !IMAGE[function_a16.jpg](instructions272221/function_a16.jpg)

1. [] On lines 31-55, there's a function that transforms a document into an external item. 

    >[!note]An external item is the Graph object that represents external content being ingested into the tenant.

1. [] On lines 35-41, the external item is defined by an ID, using the ID of your external content and the properties defined in the schema. (Refer to **config.ts** to see properties like **title**, **url**, and **iconUrl**.)

1. [] On lines 42-45, the content value and content type are supplied. 

1. [] On lines 46-52, the function handles the ACL (Access Control List) for the document. 

    >[!knowledge]If you're importing documents from another data source with its own permissions system, you can restrict access to specific groups or users. This prevents the imported documents from being visible to everyone in the M365 tenant.
    >
    !IMAGE[acl_a17.jpg](instructions272221/acl_a17.jpg)

1. [] On lines 57-73, the code handles the load operation, which is standard as it involves calling Microsoft Graph. 

    >[!knowledge]How it works: 
    >
    For each piece of content in your external platform, this function converts documents into external items. 
    >
    For each external item, the function calls the endpoint **/external/connections/{ID}/items/{uniqueId}** (line 63). 
    >
    It performs an HTTP PUT operation, passing the external item object defined earlier. 
    >
    This operation completes immediately. The for loop (line 59) iterates through each object in the collection and pushes it into the tenant.

1. [] On lines 79-83, the process starts by extracting content from your external data source (for example, a collection of articles to import). Next, the content is transformed by converting the artifacts into external items, which are entities in Microsoft Graph. Finally, the load function is called to perform the PUT HTTP request against Microsoft Graph to ingest the content.

    !IMAGE[extract_a18.jpg](instructions272221/extract_a18.jpg)

###To see more configuration files of the project:

The following information will be used when you set up the connection to the Microsoft Graph client in the **graphClient.ts** file, on lines 8-12.

1. [] In the Explorer menu, select **package.json**.

1. [] Review lines 10-13 to see that you can run command-line operations such as **start:createConnection** and **start:loadContent**.

    !IMAGE[cliCommands_a19.jpg](instructions272221/cliCommands_a19.jpg)

1. [] On line 19, **devDependencies** is a helper used to set up authentication against Microsoft Graph. 

    >[!note] To use this application, you need to register an application in Microsoft Entra, which will authenticate against the M365 tenant.

1. [] In the Explorer menu, select and review **setup.ps1** and **setup.sh**.

    - PowerShell: For Windows. Uses M365 CLI to create a new Microsoft Entra App. Defines **name**, **secret**, and **scope**.

    - Bash: For Linux or MacOS. Uses M365 CLI to create a new Microsoft Entra App. Defines **name**, **secret**, and **scope**.

    >[!note] These files are used in **graphClient.ts** lines 8-12.
    >
    !IMAGE[registerApp_20.jpg](instructions272221/registerApp_20.jpg)

1. [] Have you completed Exercise 4?

    - If No, go back two pages, verify the connector sync is complete, and finish Exercise 4.
    <br>

    - If Yes, select **Next** to continue.


<br>
[Table of contents](#table-of-contents)

===

#Congratulations! You have completed the TechExcel: Copilot for M365 Extensibility lab.

Select **End** to complete the lab.


























































