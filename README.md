<p align="center" style="background-color: transparent;">
  <img src="imgs/welcome-robots.png" alt="Robots Waving" width="100%" height="auto" style="display: block; margin-left: auto; margin-right: auto; width: 50%;">
</p>

## Welcome
**Welcome to the Generative Artificial Intelligence Government Hackathon!**


To get started, please read the following page carefully, which explains the hack environment architecture, the resources that have been deployed for you, and how to get access. 

## Optional Prerequisites

We have compiled a list of common tools and software that might come in handy! You might not need all of them for the hack however, if you work with Azure on a regular basis, these are all things you might consider having in your toolbox for the future.

- [Windows Subsystem for Linux](000-HowtoHack/Common-Prerequisites.md#windows-subsystem-for-linux)
- [Managing Cloud Resources](000-HowtoHack/Common-Prerequisites.md#managing-cloud-resources)
  - [Azure Portal](000-HowtoHack/Common-Prerequisites.md#azure-portal)
  - [Azure CLI](000-HowtoHack/Common-Prerequisites.md#azure-cli)
    - [Note for Windows Users](000-HowtoHack/Common-Prerequisites.md#note-for-windows-users)
    - [Azure PowerShell CmdLets](000-HowtoHack/Common-Prerequisites.md#azure-powershell-cmdlets)
  - [Azure Cloud Shell](000-HowtoHack/Common-Prerequisites.md#azure-cloud-shell)
- [Visual Studio Code](https://code.visualstudio.com/)
- [Azure Storage Explorer](https://azure.microsoft.com/en-us/products/storage/storage-explorer/)


## Hack Environment

A hacking environment has been made available to you where you will be able to create your own resources, or access pre-configured shared resources.

For a diagram of the architecture of the environment see [Azure Environment Diagram](https://azurediagrams.com/fc5Q6FTZ).

Each team will be designated a team name, consider using your team name to tag resources that you create.

### Shared Resources
For your convenience, the following resources have been created within a pre-configured Azure Tenant that are **shared** between all teams:
- [Azure OpenAI Service](https://learn.microsoft.com/en-us/azure/ai-services/openai/overview) with the following model deployments:

|      Deployment Name           | API Type        | Description | Max Tokens | 
|--------------------------|-----------------|-----------------|------------
| `gpt-35-turbo-16k`       | Chat completion | Most capable GPT-3.5 model and optimized for chat. | 16,385
| `gpt-4-32k`              | Chat completion |More capable than any GPT-3.5 model, able to do more complex tasks, and optimized for chat. | 32,768
| `text-embedding-ada-002` | Embedding       | Model that produces numerical (vector) representation of text that can be used to measure the relatedness between two pieces of text. | 8,191

Note: You will not need or be able to deploy your own Azure OpenAI Service instances.

- [Azure Machine Learning Service](https://learn.microsoft.com/en-us/azure/machine-learning/overview-what-is-azure-machine-learning?view=azureml-api-2) with a shared workspace called
  `genai-aml-workspace`.

### Per-team Resources
You will have access to a Resource Group, where you can create the Azure Services that you need for your hack (such as Storage Accounts, Cosmos DB, App Service, etc.).

You'll find your Resource Group in the Azure Portal.

### Accessing the Hack Environment
You have been assigned a Microsoft Account (MSA) and a temporary password. To get started, follow these instructions:
- [PIM Group Activation guide](/User%20Account%20Setup/PIM-Group-Activation.md)
    - *You will be able to activate PIM for a maxmimum of 8 hours at a time. After 8 hours, you will need to re-activate PIM.*

You will then be able to access:
  - [Azure Tenant](https://portal.azure.com)
  - [Azure Machine Learning Workspace](https://ml.azure.com/home?tid=3b707db1-4728-46ea-a4c5-c690d2c28113)

## Azure Machine Learning Workspace
Azure Machine Learning is an Azure service designed to accelerate and manage the machine learning project lifecycle. It is intended for machine learning professionals, data scientists, and engineers to train and deploy machine learning models, manage Machine Learning Operations (MLOps), and enhance their daily workflows.

You can create notebooks within the shared Azure Machine Learning Studio *Workspace*. Please prefix your notebooks with your team name. Within Azure Machine Learning you will be able to create a compute instance and attach to it from your notebook. You'll then be work with the Azure OpenAI Service APIs set up in the Azure Tenant (see [Azure OpenAI Service](#azure-openai-service)), or any resources deployed into your team's Resource Group.

### Prompt Flow (Public Preview)
Prompt Flow is a development tool in Azure Machine Learning that's designed to streamline the entire development cycle of AI applications powered by Large Language Models. It provides a comprehensive solution that simplifies the process of prototyping, experimenting, iterating, and deploying your AI applications.

You can access Prompt Flow via the Azure Machine Learning Studio Workspace. An example flow has been deployed for reference, see [Example: Magnificent Monkeys - Web Classification](https://ml.azure.com/prompts/flow/0a2c94a0-86e1-47d1-b647-a51ad7aa9f82/64d321fa-ede9-43b2-bde5-17547100c15e/details?wsid=/subscriptions/9e6f9ad9-f736-42de-97f2-0fa34e6314ce/resourceGroups/genai-workspace-xfpdf-rg/providers/Microsoft.MachineLearningServices/workspaces/genai-ws-xfpdf&tid=3b707db1-4728-46ea-a4c5-c690d2c28113). 

Make sure to choose the __connection__ that corresponds to your team name when creating an LLM tool in your own Prompt Flow flow. Also, consider including your team name in the name of your flow to help you find it later.

A __connection__ has been created for your team, you will need to create your own compute instance and environment to run your flow.

For more information on Prompt Flow, see [What is Azure Machine Learning prompt flow?](https://learn.microsoft.com/en-us/azure/machine-learning/prompt-flow/overview-what-is-prompt-flow?view=azureml-api-2)

## Azure OpenAI Service
Models within the Azure OpenAI Service will be shared across all teams - you will not have your own deployment of the Azure OpenAI Service and you will not be able to use the Studio. You can call the shared models within the Azure OpenAI Service via API calls. API access in the hack environment uses Role-based Access Control (RBAC) instead of API keys.
  - A sample notebook demonstrating how to use the API can be found here: [AOAI Sample Notebook](https://ml.azure.com/fileexplorerAzNB?wsid=/subscriptions/9e6f9ad9-f736-42de-97f2-0fa34e6314ce/resourcegroups/genai-workspace-xfpdf-rg/providers/Microsoft.MachineLearningServices/workspaces/genai-ws-xfpdf&tid=3b707db1-4728-46ea-a4c5-c690d2c28113&activeFilePath=Users/luked/AOAI_Test.ipynb)
  
  - Amend the sample notebook to use your teamname in the API call:
   ```python
      team_name = 'team-name'
   ```

## Resources
- Azure OpenAI Service:
  - [Documentation](https://learn.microsoft.com/en-us/azure/ai-services/openai/overview) 
  - [AOAI Sample Notebook](https://ml.azure.com/fileexplorerAzNB?wsid=/subscriptions/9e6f9ad9-f736-42de-97f2-0fa34e6314ce/resourcegroups/genai-workspace-xfpdf-rg/providers/Microsoft.MachineLearningServices/workspaces/genai-ws-xfpdf&tid=3b707db1-4728-46ea-a4c5-c690d2c28113&activeFilePath=Users/luked/AOAI_Test.ipynb)

- Azure Machine Learning
  - [Documentation](https://learn.microsoft.com/en-us/azure/machine-learning/?view=azureml-api-2)
  - [How to use Azure OpenAI models in Azure Machine Learning](https://learn.microsoft.com/en-us/azure/machine-learning/how-to-use-openai-models-in-azure-ml?view=azureml-api-2)
  - [Creating Azure Machine Learning Data Stores](https://learn.microsoft.com/en-us/azure/machine-learning/how-to-datastore?view=azureml-api-2&tabs=sdk-identity-based-access%2Csdk-adls-identity-access%2Csdk-azfiles-accountkey%2Csdk-adlsgen1-identity-access)
  - [Retrevial Augmented Generation using Prompt Flow](https://learn.microsoft.com/en-us/azure/machine-learning/concept-retrieval-augmented-generation?view=azureml-api-2)

- Cognitive Services
  - [Documentation](https://www.microsoft.com/cognitive-services)
- Cosmos DB
  - [Documentation](https://docs.microsoft.com/en-us/azure/cosmos-db)
- Azure Search
  - [Documentation](https://azure.microsoft.com/en-us/services/search)

  <p align="center" style="background-color: transparent;">
  <img src="imgs/pythonnotpowerpoint.png" alt="Python defeating a presentation" width="100%" height="auto" style="display: block; margin-left: auto; margin-right: auto; width: 30%;">
</p>
