
# Azure DevOps (AzDO)
### Deploy Helm Charts via Azure Container Registry (ACR) to Azure Kubernetes Service (AKS)

The repository is comprised of three test .NET Core 2.2 applications - each application is 'vanilla', i.e. simply a template to use for the build process;
- 1 x Console application
- 1 x Web Application
- 1 x Web API Application
Each application has a standard Dockerfile added via Visual Studio right-click add 'Docker support'.
Each application has standard Helm templates created in the respective charts folder via 'helm create xyz'.

In keeping with the "configuration as code" or "infrastructure as code" theme upon which the new Azure Pipelines are based all YAML is contained within the repository in the AzurePipelines directory.

I'm hoping to build on the YAML templates over time to show the multiple ways you can deploy .NET Core applications to Azure Kubernetes Service (AKS).

The pipeline uses the strategy/matrix keyword to run multiple parallel pipeline processes, if you have multiple build agents available, which;
1) build docker images
2) push docker images to ACR
3) package Helm charts (*feature still in preview*)
4) push Helm packages to ACR (*feature still in preview*)
5) publish image+helm chart to Azure Kubernetes Service (AKS).

Sources;
- https://docs.microsoft.com/en-us/azure/container-registry/container-registry-helm-repos
- https://github.com/MicrosoftDocs/azure-docs/blob/master/articles/container-registry/container-registry-helm-repos.md
- https://alwaysupalwayson.blogspot.com/2018/10/azure-devops-to-deploy-your.html
- https://alwaysupalwayson.blogspot.com/2018/10/helm-charts-repository-with-azure.html
- https://cloudblogs.microsoft.com/opensource/2018/11/27/tutorial-azure-devops-setup-cicd-pipeline-kubernetes-docker-helm/
- https://docs.microsoft.com/en-us/azure/devops/pipelines/tasks/deploy/helm-deploy?view=azure-devops
