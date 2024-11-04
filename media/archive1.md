## Exercise 2: Extend M365 Copilot with Pre-Built Plugins

Extend M365 Copilot’s actions by deploying a pre-built M365 Plugin (deploying a Teams application, without admin control. Need to decide with app to deploy. Will need Jira TEAMS apps for example) Use the connectors or plugins 
 
Use Copilot to invoke an action in a plugin – Hero prompts against service REST endpoint.

ConfigureAndDeployJiraCopilotPlugin

We will see how to install and demo of prepaid copilot plugin that can be used within teams. For the purpose of this lab, we will be using **Atlassian Jira** as the Copilot plugin.

### Task 1 - Install Jira app and plugin

As a prerequisite we will need to install the Jira app in Teams. The next few steps will guide you through accomplishing the installation.

1. [] If necessary, open **Microsoft Teams** and on the left pane, select **Apps**.

1. [] Search for +++**Jira**+++, locate and add the **Jira Cloud** app.

1. [] Select **Add to a team** > **Add for me**.


    >[!knowledge] The app will now get installed as an individual scope for this particular user. 
    
    >[!alert] The app opens up and prompts a sign in. Leave the sign in for later as we still need to create an account.

1. [] Notice on the left pane, the Jira app is now present.

1. [] On the left pane, select **Chat**.

1. [] In the Copilot chat, select the **plugins** and verify that **Jira Cloud** is as a plugin option.

1. [] Toggle the switch to enable the **Jira Cloud** plugin.

    >[!note] Now we have both the app and the plugin enabled.


### Task 2 - Configuring Atlassian Jira

Next, you will create a free account and then you will configure Jira.

1. [] Open a new browser tab and go to +++**https://www.atlassian.com/software/jira**+++.

1. [] Select **Try Jira Free** and under **Or continue with**, select **Microsoft**.

1. [] Sign in with your M365 credentials:

    | Item | Value |
    |:---------|:---------|
    | Username   | +++**@lab.CloudCredential(WWLM365EnterpriseBlank15SStakeholderKimFrank).AdministrativeUsername**+++   |
    | Password   | +++**@lab.CloudCredential(WWLM365EnterpriseBlank15SStakeholderKimFrank).AdministrativePassword**+++   |

1. [] Once signed in, follow the steps to authenticate and accept the Atlassian Terms of Service and Privacy Policy.

1. [] On the **Create a site** page, under **Your site**, enter +++**@lab.CloudCredential(WWLM365EnterpriseBlank15SStakeholderKimFrank).TenantPrefix**+++ and select **Continue**.

1. [] On the **What kind of work do you do?** page, select **Software development**.

1. [] On the **How does your team plan to use Jira** page, select **Manage tasks**.

1. [] Select **Continue** to allow Jira to use the selections as a template and create a project for you.

1. [] On the **Welcome!** page, under **Name your project**, enter +++**EcommPlatformIssues**+++ and then select **Get Started**.

1. [] On the KAN board canvas, in the **TO DO** tile, select **+ Create issue** to add the following activities that can be queried from Copilot:

    - +++**User Authentication**+++
    - +++**Product Management System**+++
    - +++**Payment Gateway Integration**+++
    - +++**User Interface Overhaul**+++
    - +++**Customer Feedback & Support**+++
    - +++**Marketing & SEO**+++ 

1. [] Assign some of these issues to yourself. Perhaps 1, 3, 5, and 6.

1. [] Drag **User Authentication** from **TO DO** to **IN PROGRESS**

### Task - Testing the Plugin via Copilot

1. [] Return to Teams Copilot.

1. [] Disable and then Enable the Jira Cloud plugin, this should prompt for sign in window.

1. [] If necessary, sign in with your M365 credentials:

    | Item | Value |
    |:---------|:---------|
    | Username   | +++**@lab.CloudCredential(WWLM365EnterpriseBlank15SStakeholderKimFrank).AdministrativeUsername**+++   |
    | Password   | +++**@lab.CloudCredential(WWLM365EnterpriseBlank15SStakeholderKimFrank).AdministrativePassword**+++   |

1. [] Once successfully authenticated, select **Close this page**.

    >[!note] You may get a Jira Cloud notification stating that Jira Cloud sent a card. The plugin setup is now complete.

1. [] Enter the following prompt to get all the tasks that are assigned to me in Jira:

    ```Copilot-wrap
    Get me all the tasks assigned to me in Jira
    ```

    >[!knowledge] Jira should be able to identify the specific user and get all the tasks that are assigned to that user.

1. [] Recollect that you assigned four tasks to yourself, notice that Copilot, using the Jira plugin, successfully fetched all of this information.

    >[!tip]Hovering over any of those reference points presents the adaptive card which has all the information. There are three buttons to perform further actions like it **Edit issue**, **Comment**, or **Open in Jira**. 

1. [] Select **Marketing & SEO** to view its information.
    
1. [] Select **Edit issue**. This page allows you to edit the configuration and perform certain tasks. Make the following modifications:
    
    | Item | Value |
    |:---------|:---------|
    | Status   | **In Progress** |
    | Description   | **Need more details on SEO improvement**   |

1. [] Select **Save**.

1. [] Return to the Jira browser tab to verify if the changes are reflected.

1. [] On the KAN board, the **Marketing & SEO** issue should be located under **IN PROGRESS** and the **Description** should be updated. 

    >[!knowledge] Information is fetched and updated with a rich user experience that is available via the adaptive cards for any issues in Jira via the Copilot plugin without the need to go into Jira itself.

1. [] 

>[!alert]Tis is where I stopped

 
 So as you can see  Let me just show you the second prompt here where I am just trying to get the information about a particular issue. So my prompt says get me details on the current status of Task can 6 in Jira.

10:15
So as you can see the response from the response here, the adaptive card is embedded in the response because it is just a single issue with the same options. So let me just quickly update the comment over here for for as a different use case

10:33
scenario.

10:43
So this way you can perform

10:46
quite a few actions related to your cheetah tasks in through the Copilot plugin. I hope you found this video useful. Thank you.
 




<br>
[Table of contents](#table-of-contents)

===

## Exercise 3: Build M365 Copilot Plugin with Copilot Studio

Build a low-code M365 Plugin with Copilot Studio to extend M365 Copilot’s actions (API plug ins – working? This is a new feature for people using Copilot Studio)y. Here they will use Rest API plugin… Optional: Custom Connector may have to be this exercise) Requires import Rest API, show them how to enable the plug in, copilot query, show them the Api, Show them multiple parameters. Copilot will call a specific API, … amount, location, etc. (showed at Build -review).  

Open API 3.0 

Use Copilot to invoke an action in a plugin – Hero prompts against service REST endpoint

###Task 1 – Custom Connector 

1. [] 

1. [] 

1. []

###Task 2 – Building a low-code plugin 

1. [] 

1. [] 

1. []

###Task 3 – Retrieve data 

1. [] 

1. [] 

1. [] 


<br>
[Table of contents](#table-of-contents)

===

## Exercise 4: Build M365 Declarative Copilot with Copilot Studio

Build a low-code Declarative Copilot with Copilot Studio to demonstrate a purpose built / scoped Copilot extension.  
 
Use Copilot to invoke an action in a plugin – Hero prompts against service REST endpoint

###Task 1 – Create Declarative Copilot 

1. [] 

1. [] 

1. []

###Task 2 – Adding a Data source 

1. [] 

1. [] 

1. []

###API via Azure Functions 

1. [] 

1. [] 

1. []

###SharePoint Site 

1. [] 

1. [] 

1. []

###Task 3 – Utilizing Connectors

1. [] 

1. [] 

1. [] 



<br>
[Table of contents](#table-of-contents)

===

#Congratulations! You have completed the **TechExcel: Copilot for M365 Extensibility** lab. 
Select **End** to complete the lab.