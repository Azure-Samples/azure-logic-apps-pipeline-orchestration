# Pipeline Orchestration Payload

This will describe the structure of the payload to send to the Pipeline Orchestration Logic App created using this sample.

## Multistage Pipeline Orchestration Definition

| Field Name              | Required | Type                     | Description                                                          |
|-------------------------|----------|--------------------------|----------------------------------------------------------------------|
| organization            | yes      | string                   | The name of the Azure DevOps organization that the pipelines are located in. |
| project                 | yes      | string                   | The name of the project within the Azure DevOps organization that the pipelines are located in. |
| azureSubscriptionId     | no*      | string                   | The subscription id that will be used to test if ARM deployments are completed.|
| location                | no*      | string                   | Used to construct the resource group name to valid successful deployment. ** |
| workGroupId             | no*      | string                   | Used to construct the resource group name to valid successful deployment. ** |
| environment             | no*      | string                   | Used to construct the resource group name to valid successful deployment. ** |
| primarySyncPipelines    | yes***   | array[PrimaryPipeline]    | Defines the pipelines that will execute one at a time, prior to the secondary pipelines being executed. |
| secondaryAsyncPipelines | yes***   | array[SecondaryPipeline] | Defines the pieplines that will be executed concurrently after all of the primary pipelines have completed |

* Required only when using resource group style validation of the primary Sync Pipelines
** Edits to the "Set dynamic resource group name" action of the logic app can be made to accomidiate your organizations resource group naming conventions. The sample uses "workGroupId"-"location"-"environment"-"value passed into the resourceGroupName field of the pipeline"
*** An empty array can be provided, but an array does need to be defined

## Primary Pipeline

| Field Name                       | Required | Type                     | Description |
|----------------------------------|----------|--------------------------|-------------|
| path                             | yes      | string                   | The path the pipeline is stored within Azure DevOps Pieplines. |
| name                             | yes      | string                   | The name of the pipeline to execute. |
| branch                           | yes      | string                   | The name of the branch to execute the pipeline against. |
| validationType                   | yes      | string                   | The type of validation that will be performed to ensure the pipeline is complete. Options are "pipeline" which will wait until the build reaches a completed state or "resourceGroup" which will wait for the deployment to complete within the resourceGroup defined (helpful for very long running pipelines).  |
| resourceGroupName                | no*      | string                   | Used to construct the resource group name, or is the complete resrouce group name, depending on the state of the useResourceGroupNamingConvention indeicator |
| useResourceGroupNamingConvention | no*      | boolean                  | Identifies whether the naming convention will be used to construct the resource group name, or the value passed into the resourceGroupName field |
| parameters                       | yes*     | array[Parameters]        | Parameter values to pass into the Azure DevOps pipelines. |

* Required only when using resource group style validation of the primary Sync Pipelines
** An empty array can be provided, but an array does need to be defined

## Secondary Pipeline

| Field Name                       | Required | Type                     | Description |
|----------------------------------|----------|--------------------------|-------------|
| path                             | yes      | string                   | The path the pipeline is stored within Azure DevOps Pipelines. |
| name                             | yes      | string                   | The name of the pipeline to execute. |
| branch                           | yes      | string                   | The name of the branch to execute the pipeline against. |
| parameters                       | yes*     | array[Parameters]        | Parameter values to pass into the Azure DevOps pipelines. |

* An empty array can be provided, but an array does need to be defined

## Parameters

| Field Name                       | Required | Type                     | Description |
|----------------------------------|----------|--------------------------|-------------|
| name                             | yes      | string                   | The name of the parameters. Should match the name of the variable defined/used within the pipeline |
| value                            | yes      | string                   | The value of the parameter. |
