# CS-4843-Assignment2
Files:

    Servers.yml:
        Used to set up servers, including establishing security groups and launch configurations
    cic-networks.txt:
        This is a template to deploy a VPC, with a pair of public and private subnets spread across two Availability Zones.
        Deploys an Internet Gateway, with a default route on the public subnets. 
        It deploys a par of NAT Gateways (one in each Availability Zones), and default routes for them in the private subnets.

Parameters:

    EnvironmentName: (Assignment-2-Enviroment)
        Description: An environment name that will be prefixed to resource names
        Type: String
    VpcCIDR: 
        Description: Please enter the IP range (CIDR notation) for this VPC
        Type: String
        Default: 10.0.0.0/16
    PublicSubnet1CIDR:
        Description: Please enter the IP range (CIDR notation) for the public subnet in the first Availability Zone
        Type: String
        Default: 10.0.0.0/24
    PublicSubnet2CIDR:
        Description: Please enter the IP range (CIDR notation) for the public subnet in the second Availability Zone
        Type: String
        Default: 10.0.1.0/24
    PrivateSubnet1CIDR:
        Description: Please enter the IP range (CIDR notation) for the private subnet in the first Availability Zone
        Type: String
        Default: 10.0.2.0/24
    PrivateSubnet2CIDR:
        Description: Please enter the IP range (CIDR notation) for the private subnet in the second Availability Zone
        Type: String
        Default: 10.0.3.0/24    
    KeyName:
        Description: Name of an existing EC2 KeyPair to enable SSH access to the instances
        Type: 'AWS::EC2::KeyPair::KeyName'
        ConstraintDescription: must be the name of an existing EC2 KeyPair.
    AMItoUse: (Amazon Linux 2 AMI (HVM) - Kernel 5.10, SSD Volume Type)
        Description: AMI to use for our base image
        Type: String
Security :

    Ingress:
        Ip Protocol: TCP
        From Port : 80
        To Port : 80
        CidrIp: 0.0.0.0/0
        
        Ip Potocol: TCP
        From Port : 22
        To Port : 22
        CidrIp: 0.0.0.0/0
        
    Egress:
        Ip Protocol : TCP
        From Port : 0
        To Port : 65535
        CidrIp: 0.0.0.0/0
Network:

    Internet Gateway -> Elastic Load Balancer -> NAT Gateway with Elastic IP (Public Subnet) -> Backend Web Application -> SQL Server (Unimplemented)

Web Application:

    Type : AWS Auto Scaling Group
Listener:

    Elastic Load Balancing Listener
    
    
 
