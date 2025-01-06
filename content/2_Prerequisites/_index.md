---
title: "Prerequisites"
menuTitle: "Prerequisites"
weight: 20
---

Before attempting to create a stack with the template, a few prerequisites should be checked to ensure a successful deployment:
1.	An AMI subscription must be active for the FortiAnalyzer license type being used in the template.
    * [**BYOL Marketplace Listing**](https://aws.amazon.com/marketplace/pp/prodview-6dt7z5twj7t7a)
    * [**PAYG (Max 2 Devices) Marketplace Listing**](https://aws.amazon.com/marketplace/pp/prodview-h2lf6do2y4y4g)
    * [**PAYG (Max 10 Devices) Marketplace Listing**](https://aws.amazon.com/marketplace/pp/prodview-wabutfmgsmt4s)
    * [**PAYG (Max 30 Devices) Marketplace Listing**](https://aws.amazon.com/marketplace/pp/prodview-cnr3vweexbiro)
    * [**PAYG (Max 100 Devices) Marketplace Listing**](https://aws.amazon.com/marketplace/pp/prodview-7gvigxfz6wmba)
    * [**PAYG (Max 500 Devices) Marketplace Listing**](https://aws.amazon.com/marketplace/pp/prodview-lez7niotfpseq)

2.	The solution requires 3 EIP to be created so ensure the AWS region being used has available capacity.  Reference [**AWS Documentation**](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-resource-limits.html) for more information on EC2 resource limits and how to request increases.

3.	If BYOL licensing is to be used, ensure these licenses have been registered on the support site.

4.   **Create a new S3 bucket in the same region where the template will be deployed.  If the bucket is in a different region than the template deployment, bootstrapping will fail.**

5.  If BYOL licensing is to be used, upload these licenses to the root directory of the same S3 bucket from the step above.

6.  **Ensure that the PublicSubnet's AWS route table has a default route to an AWS Internet Gateway, otherwise bootstrapping and licensing will fail.**  Reference [**AWS Documentation**](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Route_Tables.html#route-tables-internet-gateway) for further information.

8. If PAYG licensing is to be used, you will need to configure HA peers as the serial numbers are generated on first boot. First login via SSH or serial console and get the serial number ```get system status```, then register this in FortiCloud. Next, reboot the instances ```exec reboot```. In the GUI navigate to **Sytem Settings > HA** and add the primary interface IP and serial number of the HA peer on both instances.