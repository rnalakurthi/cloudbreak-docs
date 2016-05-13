## Cluster deployment

After all the cluster resources are configured you can deploy a new HDP cluster.

Here is a **basic flow for cluster creation on Cloudbreak Web UI**:

 - Start by selecting a previously created OpenStack credential in the header.

![](/images/os-credentials.png)
<sub>*Full size [here](/images/os-credentials.png).*</sub>

 - Open `create cluster`

`Configure Cluster` tab

 - Fill out the new cluster `name`
    - The name must be between 5 and 40 characters long and must satisfy the followings:
        - Starts with a lowercase alphabetic character
        - Can contain lowercase alphanumeric and hyphens only
 - Select one of your `Region` where you like your cluster be provisioned
 - Click on the `Setup Network and Security` button
>If `Public in account` is checked all the users belonging to your account will be able to see the created cluster on
 the UI, but cannot delete or modify it.

`Setup Network and Security` tab

 - Select one of your previously created networks
 - Select one of the security groups
 - Click on the `Choose Blueprint` button
>If `Enable security` is checked as well, Cloudbreak will install Key Distribution Center (KDC) and the cluster will 
be Kerberized. See more about it in the [Kerberos](kerberos.md) section of this documentation.

`Choose Blueprint` tab

 - Select one of the blueprints
 - After you've selected a `Blueprint`, you should be able to configure:
    - the templates
    - the number of nodes for all of the host groups in the blueprint
    - the recipes for nodes
 - Click on the `Review and Launch` button

`Review and Launch` tab

 - After the `create and start cluster` button has clicked Cloudbreak will start to create the cluster's resources on 
 your OpenStack account.

Cloudbreak uses *OpenStack* to create the resources - you can check out the resources created by Cloudbreak
 on the `Instances` page of your OpenStack `Project`.
![](/images/os-computeimages.png)
<sub>*Full size [here](/images/os-computeimages.png).*</sub>

Besides these you can check the progress on the Cloudbreak Web UI itself if you open the new cluster's `Event History`.
![](/images/os-eventhistory.png)
<sub>*Full size [here](/images/os-eventhistory.png).*</sub>

**Advanced options**

`Consul server count` the number of Consul servers (add number), by default is 3. It varies with the cluster size.

`Connector Variant` Cloudbreak provides two implementation for creating OpenStack cluster

* `HEAT` using [HEAT](https://wiki.openstack.org/wiki/Heat) template to create the resources
* `NATIVE` using API calls to create the resources

>The HEAT variant utilizes the Heat templating to launch a stack, but the NATIVE variant starts the cluster
  by using a sequence of API calls without Heat to achieve the same result, although both of them are using the same 
  authentication and credential management.

`Minimum cluster size` The provisioning strategy in case of the cloud provider cannot allocate all the requested nodes.

`Validate blueprint` This is selected by default. Cloudbreak validates the Ambari blueprint in this case.

`Shipyard enabled cluster` This is selected by default. Cloudbreak will start a [Shipyard](https://shipyard-project.com/) container which helps you to manage your containers.

`Config recommendation strategy` Strategy for configuration recommendations how will be applied. Recommended 
configurations gathered by the response of the stack advisor. 

* `NEVER_APPLY`               Configuration recommendations are ignored with this option.
* `ONLY_STACK_DEFAULTS_APPLY` Applies only on the default configurations for all included services.
* `ALWAYS_APPLY`              Applies on all configuration properties.

`Start LDAP and configure SSSD` Enables the [System Security Services Daemon](sssd.md) configuration.