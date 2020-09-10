# Azure Data Lake Gen 2 Storage ( ADLS Gen2 ) monitoring in Log Analytics

An Azure Storage account forms the basis of ADLS gen 2. Metric Monitoring of the service is a default service included in the Azure portal.

I'd like to extend the monitoring capabilities through Log Analytics, allowing me to build my own queries and have a richer log and metrics dataset.
I'm using the following PowerShell script to import the relevant data: https://github.com/Azure/azure-docs-powershell-samples/blob/master/storage/post-storage-logs-to-log-analytics/PostStorageLogs2LogAnalytics.ps1 

First, lets look at the default metrics:

![Screenshot](https://github.com/verboompj/Other/blob/master/Pictures/default%20metricsPNG.PNG)

Next, extend the diagnostics by enabling them on the Storage Account:

![Screenshot](https://github.com/verboompj/Other/blob/master/Pictures/diagsa.PNG)

These additional diagnostics get stored in a "hidden" container on your storage account under `$logs` 

![Screenshot](https://github.com/verboompj/Other/blob/master/Pictures/logssa.PNG)

We can schedule 
