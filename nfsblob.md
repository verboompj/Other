# NFS endpoint on Azure Blob Storage Premium

Scalable NFS storage , High IO capable Premium Block-Blob storage test setup.
This service has hit Public Preview , time to see what its potential could be.

### Goal: To setup a test to verify the application of NFS on Blob in High I/O usecases.

I ran the step by step to create a storage account wiht an NFS 3.0 endpoint: 
https://docs.microsoft.com/en-us/azure/storage/blobs/network-file-system-protocol-support-how-to?tabs=windows


### Steps: 

Registering the Resource Providers' features upfront can save you some time, as they take around 15 mins to complete: 

`Register-AzProviderFeature -FeatureName AllowNFSV3 -ProviderNamespace Microsoft.Storage`
`Register-AzProviderFeature -FeatureName PremiumHns -ProviderNamespace Microsoft.Storage`

Next I deployed 4 VM's in the EDSv4 series with Accelerated Networking enabled.

![Screenshot](https://github.com/verboompj/Other/blob/master/Pictures/networkdiag.PNG)


And mounted my new NFS share and container:
`sudo mount -o sec=sys,vers=3,nolock,proto=tcp [mySAname].blob.core.windows.net:/[mySAname]/nfs01 /mnt/test`

The NFS endpoint is available over a Private Link endpoint or Service Endpoint directly in or to the selected Subnet, in my case the subnet my VM's are deployed in:

![Screenshot](https://github.com/verboompj/Other/blob/master/Pictures/vnet.PNG)


### Tests

The first tests I ran was based on a single host connected to a single conteiner and copying data into a 10Gig object using DD. I repeated the tests using a 100G object and noticed the results are exactly te same.

I ran my test using different blocksizes, I ran 512, 1024, 2048, 4096 and 8192 blocksize tests

`sudo time dd if=/dev/zero of=/mnt/test/gentoo_root21.img bs=4096 iflag=fullblock,count_bytes count=100G`

The results are impressive from an IOps standpoint, showing almost exact linear performance scaling relative to the blocksize.
The cap applied to this service in Preview is set to a fixed 150MBps it seems. However IO is not throttled in my tests:

![Screenshot](https://github.com/verboompj/Other/blob/master/Pictures/testresultssingle.PNG)

As you can see, based on the blocksize we get a certain amount of IOPS. The formula to convert MBps to IOps :
`IOPS = (MBps Throughput / KB per IO) * 1024` 

### Scaling out the test

So what if we hit the same storage container with multiple nodes? Does it scale ?

Test ran using 4 nodes ( E4DS_V4 , Accelerated Networking ON ) Simultaniously hitting the NFS Container using DD again, testing 2048 and 4096 blocksizes:

![Screenshot](https://github.com/verboompj/Other/blob/master/Pictures/testresultsmultiple.PNG)




