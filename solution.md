
**Author**: Franco Nicosia
**Email**: franconicosia@hotmail.com
**Date**: 21.02.2022

# sre-architecture-test-fnicosia1

## 1. Identify the bottlenecks and potential risks of the current approach and explain why


### Load Balancer Tier

**High-availability / Single Point of Failure (SPOF)**

If you only have a single load balancer and it fails for any reason, then your whole system will fail. Typically load balancers are clustered together into a high-availability pair.

**Scalability**

Given the technology and type of virtualization used, there is a problem when scaling the infrastructure to make more resources available.


### Application Tier

**Server Capacity and Performance**

At this point we find the first cause of a bottleneck, since we are dealing with a single virtualized server, we are limited in terms of data processing capacity and performance.

**High-availability / Single Point of Failure (SPOF)**

The application running on a standalone virtualized server does not provide high availability capabilities.

**Scalability**

Given the technology and type of virtualization used, there is a problem when scaling the infrastructure to make more resources available.

### Storage Tier

**High-availability / Single Point of Failure (SPOF) / Network**

While the NFS volume has redundancy at the disk level, there is no redundancy at the VM Host level. Any failure with any other piece of hardware would mean a total storage failure and therefore no access to the data would be possible. 
Depending on the type of network used to mount the NFS, performance / bottleneck problems can be generated.


**Hardisk Type**

SAS hard disks are faster at reading and writing data on a continuous basis. In addition, it allows for multipath input/output (I/O). Since SAS technology usually connects more than one piece of circuitry, it can reroute data through a secondary highway if the primary highway fails.

**Raid Configuration**

A Raid 1 configuration offers data redundancy but doesn't offer write and read speed improvements. This can be achived with a Raid 10 or Raid 5 setup. 

## 2. Work on improving the current architecture

