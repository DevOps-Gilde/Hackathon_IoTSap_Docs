# 1. Introduction to the Infrastructure Workflow

You should now have Completed the Following things:
1. Setup your GitHub Account
2. Setup your Git Repository

Next you will create your own workflows to setup the azure services required for your Website on Azure. We will use the GitHub Repository to host the code for our workflows. A workflow consists of separate steps so called actions. Hence the name GitHub Actions. Workflows are the counterpart of Azure DevOps pipelines if you joined our previous session.

If you want to learn more about the concept of a workflow you can do it here:

[https://docs.github.com/en/actions/quickstart](https://docs.github.com/en/actions/quickstart)

# 2. Setting up the Starting Point Workflow

## Introduction

We prepared a for you that will deploy all prerequisites that you need as starting point. The workflow is a GitHub Action workflow. The details of this workflow are out of scope for this hackathon.

This workflow uses settings that differ per participants. We will use secrets to store these values within our GitHub account and reference them in our workflow. To create secrets you first have to navigate to the right place in GitHub (Tab Settings => Entry "Actions" under Secrets => Button "New repository secret").

<br><img src="./images/secrets_path_to_enter.png" width="900"/>

### USER_PARTICIPANT

TODO
We all work in the same resource group and that's why we need naming conventions to ensure uniqueness. In our hackathon we will use simplifed ones but [here](https://docs.microsoft.com/de-de/azure/cloud-adoption-framework/ready/azure-best-practices/resource-abbreviations) you find recommendations for a real world case. The simplified naming schema we use partially is `<type-name>-<your personal identifier>`. A good idea is to use an akronym infered from your name and a number. If your name is Florian Peters for Example you could choose:

`flopet631`

The full resource name for the app service plan could then be `plan-flopet631`. The following paragraphs list the secrets (Key-value pairs) you have to define. Click the "New repository secret" button as described above and confirm:

### USER_WKF_CREDENTIALS - Azure connection details

This is the Connection Data needed for the Azure Subscription. The hashtags are placeholders. Copy the values from the teams chat (They are not given to avoid exposure of secrets in the public internet).

Secret:
AZURE_CREDENTIALS =
`{
  "clientId": "#",
  "clientSecret": "#",
  "subscriptionId": "#",
  "tenantId": "#"
}`

`clientId` and `clientSecret` deserve a quick extra explanation. A workflow changes things in your Azure subscription. Of course these changes must be associated with a user so that Azure can determine whether you have the permissions to do so. `clientId` denotes the service principal we created beforehand for you. We gave that user permission for the resource group in which you deploy your Azure services. Of course a user also needs credentials. The value behind `clientSecret` is exactly that.

# 3. Run your workflow

## Start your workflow

After you set up your Secrets and fixed the code in your Repository you are ready to run your workflow.
To do so go to the ",Actions" tab. GitHub Actions are disabled by default in your fork. Click the button "I understand my workflows..." as shown below.

<br><img src="./images/Workflow_Enable.png" width="800"/><br>

Now you see a typical master detail screen with the avilable workflows on the left-hand side. Select the "infra" workflow and click on the "Run workflow" button. In the screenshot previous runs existed already. Click on run to see the results or for troubleshooting.

<br><img src="./images/Workflow_Run.PNG" width="800"/><br>

For troubleshooting just click on the name "infra" next to the icon error icon. The "infra" run at the bottom of the previous screenshot for instance. The next two screenshots show the remeining two levels until you hit the details.

<br><img src="./images/wkf_trouble_1.png" width="800"/><br>
<br><img src="./images/wkf_trouble_2.png" width="800"/><br>

## Workflow Progress

Wait for your Workflow to finish.
If the Task does not run through try to figure out the problem yourself by following the troubleshooting information above. Of course we are there to help if you don't find a solution.
## Check your WebApp is online after approx. 5 minutes

https://`[yourWebAppName]`.azurewebsites.net/

You should see a &quot;Your web app is running and waiting for your content&quot; welcome screen.

Congratulations, you have deployed your first WebApp infrastructure.
 Now, you can go ahead and deploy some code to your WebApp.
