# terraform-aviatrix-mc-spoke

### Description
Deploys a VPC/VNET/VCN and Aviatrix Spoke gateways. Also possible to use an existing VPC/VNET/VCN.

### Diagram
\<Provide a diagram of the high level constructs thet will be created by this module>
<img src="<IMG URL>"  height="250">

### Compatibility
Module version | Terraform version | Controller version | Terraform provider version
:--- | :--- | :--- | :---
v1.0.0 | 0.13-1.0.1 | >= 6.4 | >= 0.2.19

### Usage Example
```
module "spoke_aws_1" {
  source  = "terraform-aviatrix-modules/aws-spoke/aviatrix"
  version = "4.0.3"

  cloud           = "AWS"
  name            = "App1"
  cidr            = "10.1.0.0/20"
  region          = "eu-west-1"
  account         = "AWS"
  transit_gw      = "avx-eu-west-1-transit"
  security_domain = "blue"
}
```

### Variables
The following variables are required:

key | value
:--- | :---
cloud | Cloud where this is deployed. Valid values: "AWS", "Azure", "ALI", "OCI", "GCP"
name | Name for this spoke VPC and it's gateways
region | AWS region to deploy this VPC in
cidr | What ip CIDR to use for this VPC (Not required when use_existing_vpc is true)
account | The account name as known by the Aviatrix controller
transit_gw | The name of the transit gateway we want to attach this spoke to. Not required when attached is set to false.

The following variables are optional:

<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> = AWS, <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> = Azure, <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"> = GCP, <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true"> = OCI, <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true"> = Alibaba


Supported_CSP's | Key | Default | Description
:-: | :-- | :-- | :--
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"><br><img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"><br><img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"><br><img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true"><br><img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true"> | instance_size | t3.medium<br>Standard_B1ms<br>n1-standard-1<br>VM.Standard2.2<br>ecs.g5ne.large | The size of the Aviatrix spoke gateways
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true"> | ha_gw | true | Set to false if you only want to deploy a single Aviatrix spoke gateway
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true"> | insane_mode | false | Set to true to enable insane mode encryption
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"><br><img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"><br><img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"> | az1 | a<br>az-1<br>b | Concatenates with region to form az names. e.g. eu-central-1a. Used for insane mode only.
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"><br><img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"><br><img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"> | az2 | b<br>az-2<br>c | Concatenates with region to form az names. e.g. eu-central-1b. Used for insane mode only.
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true"> | active_mesh | true | Set to false to disable active mesh.
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true"> | prefix | true | Boolean to enable prefix name with avx-
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true"> | suffix | true | Boolean to enable suffix name with -spoke
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true"> | attached | true | Set to false if you don't want to attach spoke to transit_gw.
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true"> | attached_gw_egress | true | Set to false if you don't want to attach spoke to transit_gw_egress.
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true"> | security_domain | | Provide security domain name to which spoke needs to be deployed. Transit gateway must be attached and have segmentation enabled.
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true"> | single_az_ha | true | Set to false if Controller managed Gateway HA is desired
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true"> | single_ip_snat | false | Specify whether to enable Source NAT feature in single_ip mode on the gateway or not. Please disable AWS NAT instance before enabling this feature. Currently only supports AWS(1) and AZURE(8)
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true"> | customized_spoke_vpc_routes | | A list of comma separated CIDRs to be customized for the spoke VPC routes. When configured, it will replace all learned routes in VPC routing tables, including RFC1918 and non-RFC1918 CIDRs. Example: 10.0.0.0/116,10.2.0.0/16
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true"> | filtered_spoke_vpc_routes | |A list of comma separated CIDRs to be filtered from the spoke VPC route table. When configured, filtering CIDR(s) or it’s subnet will be deleted from VPC routing tables as well as from spoke gateway’s routing table. Example: 10.2.0.0/116,10.3.0.0/16
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true"> | included_advertised_spoke_routes | | A list of comma separated CIDRs to be advertised to on-prem as Included CIDR List. When configured, it will replace all advertised routes from this VPC. Example: 10.4.0.0/116,10.5.0.0/16
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> | subnet_pairs | 2 | Number of Public/Private subnet pairs created in the VPC.
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> | subnet_size | 28 | Size of the Public/Private subnets in the VPC.
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> | enable_encrypt_volume | false | Set to true to enable EBS volume encryption for Gateway.
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> | customer_managed_keys | | Customer managed key ID for EBS Volume encryption.
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true"> | private_vpc_default_route | false | Program default route in VPC private route table.
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true"> | skip_public_route_table_update | false | Skip programming VPC public route table.
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true"> | auto_advertise_s2c_cidrs | false | Auto Advertise Spoke Site2Cloud CIDRs.
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true"> | tunnel_detection_time | | The IPsec tunnel down detection time for the Spoke Gateway in seconds. Must be a number in the range [20-600]. Default is 60.
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> | tags | | Map of tags to assign to the gateway.
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true"> | use_existing_vpc | false | Set to true to use an existing VPC in stead of having this module create one.
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true"> | vpc_id | | VPC ID, for using an existing VPC.
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true"> | gw_subnet | |Subnet CIDR, for using an existing VPC. Required when use_existing_vpc is enabled. Make sure this is a public subnet.
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true"> | hagw_subnet | | Subnet CIDR, for using an existing VPC. Required when use_existing_vpc is enabled and ha_gw is true. Make sure this is a public subnet.
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> | china | false | Set to true when deploying this module in mainland China regions
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true"> | transit_gw_egress | | Add secondary transit to attach spoke to (e.g. for dual transit firenet). When segmentation is used, transit_gw MUST be used for east/west transit.
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true"> | transit_gw_route_tables | [] | A list of route tables to propagate routes to for transit_gw attachment.
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true"> | transit_gw_egress_route_tables | [] | A list of route tables to propagate routes to for transit_gw_egress attachment.
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true"> | inspection | false | Set to true to enable east/west Firenet inspection. Only valid when transit_gw is East/West transit Firenet.
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> | gov | false | Set to true when deploying this module in AWS/Azure GOV.
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true"> | az_support | true | Set to false if the region does not support Availability Zones.
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"> | ha_region | | Region for multi region HA. HA is multi-az single region by default, but will become multi region when this is set.
<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true"> | ha_cidr | | The IP CIDR to be used to create ha_region spoke subnet. Only required when ha_region is set.

### Outputs
This module will return the following outputs:

key | description
:---|:---
[vpc](https://registry.terraform.io/providers/AviatrixSystems/aviatrix/latest/docs/resources/aviatrix_vpc) | The created VPC as an object with all of it's attributes (when use_existing_vpc is false). This was created using the aviatrix_vpc resource.
[spoke_gateway](https://registry.terraform.io/providers/AviatrixSystems/aviatrix/latest/docs/resources/aviatrix_spoke_gateway) | The created Aviatrix spoke gateway as an object with all of it's attributes.

