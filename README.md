## Project Title - Deploy a high-availability web app(Udagram) using CloudFormation
Take a look at the *Architecture diagram*:
![Architecture design](images/architecture.png)

### URL/DNS  OF LOAD BALANCER 
- udagr-WebAp-2NM2YBBQ0VBS-324354963.us-west-2.elb.amazonaws.com
### Scripts used
- ./create.sh   --- script used to create resources
- ./update.sh .... script used to update resources
- ./delete.sh .... script used to delete resources
### other files
- proj-network.yml and proj-network.json ---- file used to deploy network  resources
- proj-server.json and proj-server.yml ------- file used to deploy server resources
- images

### This project deploys a high avaliability web application called *UDAGRAM*
    The deployments consist of two stacks:
-  1) udagramNetwork 
-  2) udagramServer

### UdagramNetwork stack
This stack deploys the following resources:
-  A VPC
- A pair of public and private subnets spread across two Availabilty Zones.
- An Internet Gateway, with a default route on the public subnets. 
- route tables for the public 
- A pair of NAT Gateways (one in each AZ), and default routes for them in the private   subnets.

### Diagram showing how UdagramNetwork stack was deployed
![NETWORK STACK CREATION SCRIPT](images/network-stack-creation-cli.JPG)
### diagram showing resources created

![udagram network  stack](images/created-network-resources-console.png)
- VPC CONSOLE
![vpc](images/vpc.png)
- public and private subnets created on different AZ's
![public and private subnets created on different AZ's](images/subnets.png)
- Internert gateway
![Internert gateway](images/IGW.png)
- NAT gateway
![NAT gateway](images/nat-gw.png)

### Udagram's Server stack
- A load balancer and web server security groups
- It also deploys auto scaling groups and its lunch configuration
- In addition, we have load balancers, listeners, listeners rule,target groups, IAM roles and policies.

### diagram showing how udagramServer stack was deployed
![Server STACK CREATION SCRIPT](images/udagram-server-cli.JPG)
### Diagram showing resources created
![udagram Server  stack](images/udagram-server-console.JPG)
- Load Balancer
![load balancer](images/LOAD-BALANCER.JPG)
- LB Security group Inbound -- allow all IP from port 80
![LB INBOUND SECURITY GROUP](images/LB-SG-INBOUND.JPG)
- LB Security group Outbound
![LB OUTBOUND SECURITY GROUP](images/LB-SG-OUTBOUND.JPG)
- Webserver Security group Inbound allowa all ip from port 80; Allows ssh from port 22
![Webserver INBOUND SECURITY GROUP](images/WEBSER-SG-INBOUND.JPG)
- Webserver Security group Outbound
![Webserver OUTBOUND SECURITY GROUP](images/WEBSER-SG-OUTBOUND.JPG)
- Auto Scaling groups 
![Auto Scaling  GROUP](images/AUTOSCALING-GROUP.JPG)
- Target Groups
![Target Groups](images/target-groups.JPG)
- IAM ROLE
![IAM ROLE](images/IAM-ROLE.JPG)

## TESTING OF JUMPBOX/BASTION TO ACCESS THE WEBSERVERS
STEPS:
First create a jump start server in the public subnet 1
- jump box created -private ip-10.0.0.112  ;public-ip-54.188.188.203
![jumpbox](images/jumpbox-created.JPG)
- jump box  Inbound Security limited to my IP address only
![jumpbox](images/jumpbox-security.JPG)
Secondly i copied the webserver's key from my local machine to the jumpbox
![jumpbox step1](images/step1jumpbox.JPG)
Thirdly login to the jumpbox
![jumpbox step2](images/step2jumpbox.JPG)
Finally login to any webserver on the private subnets(private subnet 2 az2 with ip-10.0.3.99) 
![jumpbox step3](images/step3jumpbox-test-wbseraz1.JPG)
Finally login to any webserver on the private subnets(private subnet 1 az1 with ip-10.0.2.19)
![jumpbox step4](images/step4jumpbox-test2.JPG)

### Final url of load balancer up and running
![final image](images/final-image.png)

In conclusion, our Udagram app is up and running with the this link  "udagr-WebAp-2NM2YBBQ0VBS-324354963.us-west-2.elb.amazonaws.com"
Thank you.






