# Automated Deployments
There is currently not much quality information on how to deploy workflows to Logic Apps Standard.

Logic Apps Standard is built on the Azure Functions runtime and unlike Logic Apps Consumption, there can be any number of *workflows* for one Logic App Standard. This is like Azure Functions and so the best deployment approach for these is to:

1. Deploy the Logic App Standard infrastructure
2. Deploy each workflow separately from the infrastructure as the rate of change of these is much higher than the infrastructure.

For a Logic App that has multiple workflows, you can make the decision to deploy all of the workflows in one go or separately. This is very much akin to Azure Functions an aligns with a (micro) services approach as opposed to a monolith deployment approach.

## Steps to Deployment
In general, this is going to be:
1. Infrastructure
2. Workflows

## Infrastructure Deployment
There are many routes to this:
1. CLI
2. Developer CLI (azd)
3. ARM template
4. Bicep
5. Terraform.

It is best to align this with the overall approach that is other use on adjacent projects or organisational standards for most skills reuse.

This is how a Logic Apps Standard may be deployed using [Bicep](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/overview?tabs=bicep)

There are boradly-speaking 3 main components:
1. the Logic App itself
2. the server farm on which the Logic App is deployed (this may be shared)
3. A storage account for state management
