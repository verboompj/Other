#Azure Data Lake Gen 2 Storage ( ADLS Gen2 ) monitoring in Log Analytics

An Azure Storage account forms the basis of ADLS gen 2. Metric Monitoring of the service is a default service included in the Azure portal.

I'd like to extend the monitoring capabilities through Log Analytics, allowing me to build my own queries and have a richer log and metrics dataset.

First, enable diagnostics on the storage account:


