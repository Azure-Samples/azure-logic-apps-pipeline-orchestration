---
page_type: sample
languages:
- json
products:
- logicapps
description: "Add 150 character max description"
urlFragment: "update-this-to-unique-url-stub"
---

# Using Azure Logic App for Azure DevOps Pipeline Orchestration

<!-- 
Guidelines on README format: https://review.docs.microsoft.com/help/onboard/admin/samples/concepts/readme-template?branch=master

Guidance on onboarding samples to docs.microsoft.com/samples: https://review.docs.microsoft.com/help/onboard/admin/samples/process/onboarding?branch=master

Taxonomies for products and languages: https://review.docs.microsoft.com/new-hope/information-architecture/metadata/taxonomies?branch=master
-->

This sample provides an Azure Resource Manager template for a Logic apps that can be used to orchestrate the execution of many Azure DevOps Pipelines. The Logic App is an HTTP triggered logic app that accepts a POST method. The payload has two arrays defined. The first array is the information for the pipelines that will need to be executed synchronously. The second is the information on the pipelines that, once the synchronous pipelines are completed, can be executed asynchronously.

## Contents

| File/folder       | Description                                             |
|-------------------|---------------------------------------------------------|
| `samples`         | Sample payloads that are sent to the app for execution. |
| `azuredeploy.json`| The Azure Resource Manager template that contains the sample application. |
| `.gitignore`      | Define what to ignore at commit time.                   |
| `README.md`       | This README file.                                       |
| `LICENSE`         | The license for the sample.                             |
| `SECURITY`        | Microsoft OOS Security disclosure.                      |
| `CODE_OF_CONDUCT` | Microsoft OOS code of conduct.                          |

## Prerequisites

* Azure subscription
* Azure DevOps subscription
* Azure DevOps Pipelines defined

## Setup

To setup this sample execute the follow steps in order.

* Create a resource group within your Azure subscription
* Deploy the [Azure Resource Manager Template](./pipeline-execution-app/azuredeploy.json)
* Authenticate the arm API Connector that was deployed with the template
    * Navigate to the 
* Authenticate the visualstudiosteamservices API connector that was deployed with the template

## Runnning the sample

Outline step-by-step instructions to execute the sample and see its output. Include steps for executing the sample from the IDE, starting specific services in the Azure portal or anything related to the overall launch of the code.

## Key concepts

Provide users with more context on the tools and services used in the sample. Explain some of the code that is being used and how services interact with each other.

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.
