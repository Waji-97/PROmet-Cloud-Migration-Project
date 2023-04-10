# ☁️  AWS Cloud 3-tier Architecture Project

AWS Cloud migration from on-premise project carried out by our team during the Cloud Bootcamp

![image](https://user-images.githubusercontent.com/76054852/230936330-b24d41ad-f4ea-459e-882b-bea13521a3df.png)

> Technical Documentation and a Presentation pdf files are included

🌐 [PROmet](https://github.com/Waji-97/PROmet-Website) - The PROmet Website created using Django framework

👨‍💻 [Infrastructure as Code](https://github.com/Waji-97/AWS-3-tier-Terraform) - The AWS infrastructure Terraform code repository

🖥️ [On-Premise](https://github.com/Waji-97/PROmet-On-Premise-Project) - On-premise version


## 💡 Objective

The objective of this AWS Cloud migration project was to solve the increased traffic and public demand. PROmet partnered with PROcloud, which offers cloud migration planning, implementation, and ongoing management services. PROcloud helped PROmet's web service by migrating to the cloud. It improved scalability, reliability, and reduced costs for PROmet.

## ⛏️ Goals and Design
Previously, the service was operated on-premises, but we chose the rehosting method to start migration. Before migration, of course, we first provisioned the infrastructure. We created a new VPC and set up routing according to it using a routing table between two availability zones. We connected the public subnet to the internet gateway and added a NAT gateway to the private subnet. We created one Bastion Host EC2 instance in the public subnet and added an EC2 instance hosting the Django application in the private subnet. We also set up RDS in the private subnet. We set up an application load balancer in the public subnet to allow users to interact and perform load balancing between the two availability zones. We deployed the Django application to the EC2 instance and implemented an autoscaling group to create a replicated EC2 instance in the second availability zone. We also implemented a default RDS and read-only replicated RDS in another availability zone. We mounted EFS on all EC2 instances of the Django app. We added a Route53 hosting zone so that users can access our web app using a domain name. We also obtained SSL/TLS certificates from AWS ACM for HTTPS connections. We set up metric collection through Cloudwatch to send email notifications through SNS. In addition, we introduced Grafana to integrate with Cloudwatch metrics and set up real-time EC2 instance monitoring on Grafana dashboards. We implemented Jenkins CI/CD to automatically apply the code to production when a developer pushes the code to the Github repository. Finally, we used Terraform to reduce errors when creating the same infrastructure in a new region and to reduce infrastructure management costs and time through automated infrastructure construction.


## 📝 Conclusion

During this project, I learned a lot about networking in the public cloud, deploying applications on EC2 instances, managing databases using RDS, load balancing with ALB/NLB, managed file storage with EFS, implementing Auto Scaling groups, managing DNS with Route53, and implementing CI/CD with Jenkins and Github webhooks. I had some difficulty routing two different availability zones using routing tables, but I was able to solve it by using Google, AWS documentation, and YouTube. Mounting EFS took a little longer than expected, but I was able to solve it quickly by referring to the documentation. The most challenging part was the Jenkins CI/CD pipeline. Since this technology was very new to me, I spent a few days studying it before applying it to the project. I configured it to build Jenkins jobs on the worker node when triggered by Github webhooks. The problem was that I needed a strategy to confirm the key required to connect the master Jenkins node to the worker node within the public cloud plane. This problem was solved by simply setting up nodes to SSH into worker nodes. Another issue was understanding how Terraform worked. I only knew how to provision infrastructure and resources using code, but I didn't know how it actually worked. Therefore, I conducted research to understand how the '.tf' files work by running some tests. We also looked at how modules work, but in this project, we only implemented resource blocks to configure infrastructure. Many errors occurred in the 'terraform plan' part, and I had to find solutions through the Terraform documentation. Overall, despite facing some challenges, this project provided valuable learning opportunities in various areas of public cloud networking, infrastructure management, and CI/CD pipelines.

