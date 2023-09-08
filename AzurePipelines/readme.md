# Azure Pipelines

In this pipeline implementation we're going to embed the mimics tool into a simple Azure DevOps pipeline by using the "famous" and "infamous" [Juice Shop](https://github.com/juice-shop/juice-shop) project.       
      
During the pipeline implementation we're also going to use the lightweight "Html Viewer" tool in order to display the scan results in the Azure Devops environment: [html-viewer-plugin](https://marketplace.visualstudio.com/items?itemName=JakubRumpca.azure-pipelines-html-report)

## Installing Azure Extension & configuring the service connection

1. Install the [extension "Html Viewer"](https://marketplace.visualstudio.com/items?itemName=JakubRumpca.azure-pipelines-html-report) into your Azure DevOps environment.
![](resources/azure-pipelines-html-report-example.png)</br>
![](resources/azure-pipelines-html-report-getit.png)</br>

Select the organisation where your project is held and click "Install".
![](resources/azure-pipelines-html-report-select-org.png)</br>

You can always check the installed plugins in your Azure DevOps organisation settings >> Extensions
![](resources/azure-pipelines-extensions.png)</br>
 

2. Configure a service connection endpoint with your Rapid7 API token.
