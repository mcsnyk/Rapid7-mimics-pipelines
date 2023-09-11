# Azure Pipelines

In this pipeline implementation we're going to embed the mimics tool into a simple Azure DevOps pipeline by using the "famous" and "infamous" [Juice Shop](https://github.com/juice-shop/juice-shop) project.</br>    
During the pipeline implementation we're also going to use the lightweight "Html Viewer" tool in order to display the scan results in the Azure Devops environment: [html-viewer-plugin](https://marketplace.visualstudio.com/items?itemName=JakubRumpca.azure-pipelines-html-report)

## Installing Azure Extension & configuring the service connection

1. Install the [extension "Html Viewer"](https://marketplace.visualstudio.com/items?itemName=JakubRumpca.azure-pipelines-html-report) into your Azure DevOps environment. This extension is available via the Visual Studio Marketplace.  
![](resources/azure-pipelines-html-report-example.png)
![](resources/azure-pipelines-html-report-getit.png)

Select the organisation where your project is held and click "Install".
![](resources/azure-pipelines-html-report-select-org.png)

You can always check the installed plugins in your Azure DevOps organisation settings >> Extensions
![](resources/azure-pipelines-extensions.png)

2. Configure the pipeline by using ![this configuration yaml-file](https://github.com/mcsnyk/Rapid7-mimics-pipelines/blob/main/AzurePipelines/AzurePipelines-generic-html.yml) as an example. If you don't have any pipelines for your project, select the Pipelines >> Create pipeline option.
![](resources/azure-pipelines-creating-pipeline.png) 

3. We now have to define the "API_KEY" and "BASE_URL" variables in order to run the pipeline. Please select the "Variables" option first. 
![](resources/azure-pipelines-variables.png)    
![](resources/azure-pipelines-variables2.png)

4. Let's run our pipeline! In the example script we used the latest ubuntu image, please feel free to use another vmImage or even your own custom pool.     
    
:wrench: Here is a list of the available binaries of the mimics tool:
- [macOS Universal](https://artifacts.rapid7.com/cloudsec/mimics/v1.2.5/mimics_1.2.5_darwin_all)
- [Linux x86-64](https://artifacts.rapid7.com/cloudsec/mimics/v1.2.5/mimics_1.2.5_linux_amd64)
- [Linux ARM](https://artifacts.rapid7.com/cloudsec/mimics/v1.2.5/mimics_1.2.5_linux_arm64)
- [Windows x86-64](https://artifacts.rapid7.com/cloudsec/mimics/v1.2.5/mimics_1.2.5_windows_amd64.exe)
- [Windows ARM](https://artifacts.rapid7.com/cloudsec/mimics/v1.2.5/mimics_1.2.5_windows_arm64.exe)

During the pipeline exectution we can look inside the pipeline and observe the findings and remediation advice provided by the mimics tool:
![](resources/azure-pipelines-execution.png)

5. After the pipeline run, we can take a look at the results and the published artifacts. On the Summary tab we can find the artifacts and the results of the different jobs. The output of the mimics tool can be configured (available extentions: XML, SARIF and HTML, or all of them).
![](resources/azure-pipelines-summary.png)    
 
6. As we added the HTML Viewer tool, we can immediately observe our vulnerabilities on a separate tab, the HTML Viewer tab.
![](resources/azure-pipelines-html-viewer-results.png)


