# AWS Single AZ VPC Setup
## **Description**
This project shows how to setup a secure AWS VPC within a single Availability Zone. The architecture includes two subnets. One public subnet and one private subnet. The public subnet hosts a web server instance accesible from the internet while private subnet private subnet host DB server instance. The VPC is attached with Internet Gateway to enable inernet access to public subnet. For private subnet internet access, NAT Gateway used. For instance level security, two Security Groups are associated with instances. For subnet level security , two NACLs are associated with two subnets. Route tables are associated to two subnets to ensure proper routing of traffic within the VPC and to the internet. 
 This setup provides foundational AWS networking architecture.

## **Architecture Diagram**
[Architectural Diagram](C:\Users\user\Desktop\cloud\PROJECT1\Architectural_Diagram.png)
## **Technologies and tools used**
- Amazon Web Services - Cloud Platform
- Amazon VPC - For Network isolation
- EC2 - Instances for private and public subnets
- Internet Gateway - Provide internet access to public subnet
- NAT Gateway - To allow private subnet instances internet
- NACLs - Subnet level security control
- Security Groups - Instance level security
- Route tables - To manage routing subnets and internet

  ## **steps followed**
  1. Chose the architectural type
  2. Drew the architectural diagram
  3. Created VPC (10.0.0.0/16)
  4. created subnets
    - Public subnet (10.0.1.0/24)
      [Publuc subnet](C:\Users\user\Desktop\cloud\PROJECT1\Public_Subnet.png)
    - Private subnet (10.0.2.0/24) [Private subnet](C:\Users\user\Desktop\cloud\PROJECT1\Private_Subnet.png)

  5.  Launched Internet Gateway and attached it to the VPC [Iinternet Gateway](C:\Users\user\Desktop\cloud\PROJECT1\Internet_Gateway.png)
  6. Launched NAT Gateway, placed it in public subnetand associate Elastic IP  [NAT Gateway](C:\Users\user\Desktop\cloud\PROJECT1\NAT_Gateway.png)
  7. Created route tables 
    - Public subnet Route table : route to IGW [Public subnet RT](C:\Users\user\Desktop\cloud\PROJECT1\Public_Subnet_Route_Table.png)
    - Private subnet Route Table : route to NAT [Private subnet RT](C:\Users\user\Desktop\cloud\PROJECT1\Private_Route_Table.png)
  8. Created Security Groups
    - Security Group for public subnet instance : allowed inbound traffic of SSH and HTTP [WEB SG](C:\Users\user\Desktop\cloud\PROJECT1\Security_Group_WEB_EC2.png)
    - Security Group for private subnet instance : allowed inbound traffic of SSH and MySQL  [db sg](C:\Users\user\Desktop\cloud\PROJECT1\Security_Group_DB_EC2.png)
  9. Setup Network ACLs
    - for the public subnet (allowed inbound ports - 22,443,80,1024-65535 / allowed outbound ports - 3306,22,1024-65535,443,80)[NACL public subnet](C:\Users\user\Desktop\cloud\PROJECT1\NACL_Public_Subnet.png)
    - for the private subnet (allowed inbound ports - 3306,22,1024-65535,80,443 / outbound ports - 1024-65535,80,443) [NACL Private subnet](C:\Users\user\Desktop\cloud\PROJECT1\NACL_Private_Subnet.png)  
  10. Created two EC2 instances and attached relevent Security group for each [EC2 instances](C:\Users\user\Desktop\cloud\PROJECT1\INSTANCES.png)
  11. SSH into web EC2 and installed NGINX [nginx welcomepage](C:\Users\user\Desktop\cloud\PROJECT1\NGINX_Welcome_Page.png)

  ## **Results**
    - Confirmed that the web server is reacheble by displaying default NGINX welcome page
    - Verified that internet access is working correctly through the  internet gateway for the public subnet

  ## **What I learnt**
    - Understood the different between Security Groups and NACLs
  
  ## **Notes**
  All resources are deleted on AWS to get avoid cost
  ## **Future Improvements**
  I would like to try same architecture with multiple Availability Zones and Loadbalancig. Like to try IaC or scripting for resource deployments.  
