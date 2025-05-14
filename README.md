# AWS VPC Peering setup

This project documents how a VPC Peering connection between two VPCs.
✅ 1. Region and Availability Zone
Everything is deployed within one AWS Region.

All components reside inside a single Availability Zone (AZ).

✅ 2. VPC 1 Setup
Create VPC 1 with its own CIDR block.

Inside VPC 1:

Create a Public Subnet

Launch one EC2 instance.

Attach a Route Table with a route to the Internet Gateway.

Associate this subnet with the route table.

Attach an Internet Gateway (IGW) to the VPC for internet access.

Create a Private Subnet

Launch another EC2 instance.

No direct route to the IGW.

Create and associate a NAT Gateway in the public subnet.

Update the private subnet's Route Table to route outbound traffic through the NAT Gateway.

Result:

Public subnet has full internet access.

Private subnet can access the internet via NAT, but cannot be accessed from the internet.

✅ 3. VPC 2 Setup (Same AZ)
Create a second VPC (VPC 2) with a different CIDR block.

Inside VPC 2:

Create a Public Subnet

Launch one EC2 instance.

Attach a Route Table with a route to its own Internet Gateway.

Associate the subnet with the route table.

✅ 4. Connectivity Between VPCs
The public subnet of VPC 1 is logically connected to the public subnet of VPC 2, indicating communication between the two VPCs.

This implies:

VPC Peering OR Transit Gateway setup.

Appropriate route table entries must be added in both VPCs to route traffic to each other.

