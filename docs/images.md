# Custom cloud images
Every cloud platform comes with default images which contains the required packages to build an Ambari and HDP stack. However these images can be customized 
and can be used instead of the default ones. The default images are declared in yml files which can be overwritten by placing them into the 
`/etc/cloudbreak` directory. Cloudbreak will load the images from these files upon start. The format of the yml files are described in the next sections.

`Note:` If you wish to change the images after Cloudbreak is launched you need to restart the application.

## AWS
To override the default images create the following file: `/etc/cloudbreak/aws-images.yml` and replace it's content by region as desired.
```
aws:
  ap-northeast-1: ami-76729917
  ap-northeast-2: ami-7c1ad112
  ap-southeast-1: ami-a7ac7fc4
  ap-southeast-2: ami-acf7decf
  eu-central-1: ami-71da331e
  eu-west-1: ami-cba43bb8
  sa-east-1: ami-f8901a94
  us-east-1: ami-bde327d0
  us-west-1: ami-b76421d7
  us-west-2: ami-d541bbb5
```

## Azure
To override the default images create the following file: `/etc/cloudbreak/arm-images.yml` and replace it's content by region as desired.
```
azure_rm:
  East Asia: https://sequenceiqeastasia2.blob.core.windows.net/images/cb-2016-06-14-03-27.vhd
  East US: https://sequenceiqeastus2.blob.core.windows.net/images/cb-2016-06-14-03-27.vhd
  Central US: https://sequenceiqcentralus2.blob.core.windows.net/images/cb-2016-06-14-03-27.vhd
  North Europe: https://sequenceiqnortheurope2.blob.core.windows.net/images/cb-2016-06-14-03-27.vhd
  South Central US: https://sequenceiqouthcentralus2.blob.core.windows.net/images/cb-2016-06-14-03-27.vhd
  North Central US: https://sequenceiqorthcentralus2.blob.core.windows.net/images/cb-2016-06-14-03-27.vhd
  East US 2: https://sequenceiqeastus22.blob.core.windows.net/images/cb-2016-06-14-03-27.vhd
  Japan East: https://sequenceiqjapaneast2.blob.core.windows.net/images/cb-2016-06-14-03-27.vhd
  Japan West: https://sequenceiqjapanwest2.blob.core.windows.net/images/cb-2016-06-14-03-27.vhd
  Southeast Asia: https://sequenceiqsoutheastasia2.blob.core.windows.net/images/cb-2016-06-14-03-27.vhd
  West US: https://sequenceiqwestus2.blob.core.windows.net/images/cb-2016-06-14-03-27.vhd
  West Europe: https://sequenceiqwesteurope2.blob.core.windows.net/images/cb-2016-06-14-03-27.vhd
  Brazil South: https://sequenceiqbrazilsouth2.blob.core.windows.net/images/cb-2016-06-14-03-27.vhd
```

## GCP
To override the default images create the following file: `/etc/cloudbreak/gcp-images.yml` and replace it's content as desired. It is not required 
to have an image in every region the `default` is used everywhere.
```
gcp:
  default: sequenceiqimage/cb-2016-06-14-03-27.tar.gz
```

## OpenStack
To override the default images create the following file: `/etc/cloudbreak/os-images.yml` and replace it's content as desired. It is not required 
to have an image in every region the `default` is used everywhere.
```
openstack:
  default: cloudbreak-2016-06-14-10-58
```