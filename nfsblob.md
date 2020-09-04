# NFS endpoint on Azure Blob Storage Premium

Scalable NFS storage , High IO capable Premium Block-Blob storage test setup

### Goal: To setup a test to verify the application of NFS on Blob in High I/O usecases.

I ran the step by step to create a storage account wiht an NFS 3.0 endpoint: 
https://docs.microsoft.com/en-us/azure/storage/blobs/network-file-system-protocol-support-how-to?tabs=windows

Registering the Resource Providers' features upfront can save you some time, as they take around 15 mins to complete: 

`Register-AzProviderFeature -FeatureName AllowNFSV3 -ProviderNamespace Microsoft.Storage`
`Register-AzProviderFeature -FeatureName PremiumHns -ProviderNamespace Microsoft.Storage`

