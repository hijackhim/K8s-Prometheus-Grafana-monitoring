                                                ##AWS EKS Cluster Monitoring with Prometheus, Grafana##
## Overview📝
To achieve comprehensive monitoring for an AWS EKS (Elastic Kubernetes Service) cluster, we will leverage open-source tools such as Prometheus, Grafana. Each tool plays a crucial role in the monitoring setup:

📊 Prometheus: It collects and stores metrics from various sources within the cluster, allowing us to gain insights into resource utilization, application performance, and more.

📈 Grafana: It provides a powerful visualization platform to create interactive dashboards using the data collected by Prometheus. Grafana enables us to monitor the health and performance of our chatbot application in real time

Prerequisites 📋

• Setting up the AWS EKS Management Host 🏢

• Creating an IAM Role and Attaching it to the EKS Management Host 🔐

• Creating the EKS Cluster using eksctl

• Deploying a sample application for Logs Monitoring using Prometheus and Grafana

• Monitoring CPU, Memory, Disk, and Error Codes 💻📊

Creating an EKS Management Host on AWS

Before you begin, ensure that you have an AWS account, a basic understanding of AWS, Kubernetes, EKS, and the required permissions to create resources within AWS.

1. Use below command to install kubectl
 
  $ curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.19.6/2021-01-05/bin/linux/amd64/kubectl

  $ chmod +x ./kubectl
 
  $ sudo mv ./kubectl /usr/local/bin
 
  $ kubectl version --short --client

2. Install AWS CLI latest version using AWS documentation
3. Install eksctl using AWS documentation
4. Create IAM role & attach to EKS Management Host.

  Create New Role using IAM service ( Select Usecase - ec2 )

  Add below permissions for the role

  IAM - fullaccess
  
  VPC - fullaccess
  
  EC2 - fullaccess
  
  CloudFomration - fullaccess
   
   Administrator - access

5. Attach created role to EKS Management Host (Select EC2 => Click on Security => Modify IAM Role => attach IAM role we have created)

6. Create EKS Cluster using eksctl using documentation.

  EKS will create instance and cluster according to input given while creating EKS cluster
  
  ![eks-cluster](https://github.com/hijackhim/K8s-Prometheus-Grafana-monitoring/assets/105789918/c4ab9c97-e95a-4530-8d10-b00f8b5191a3)
  ![instances-created by eks](https://github.com/hijackhim/K8s-Prometheus-Grafana-monitoring/assets/105789918/86e7fb25-72ab-4f27-ab3e-9ad9e664516a)

7. After Installation check the installation by running kubectl command.

8. Now create yaml deployment attached to load balancer so that Prometheus and Grafana can monitor it.

![service-loadbalancer](https://github.com/hijackhim/K8s-Prometheus-Grafana-monitoring/assets/105789918/5c1c7cc7-317f-4109-8c81-247194f3f4f0)

![deployment for k8s](https://github.com/hijackhim/K8s-Prometheus-Grafana-monitoring/assets/105789918/e815f3aa-8845-4064-bb80-9b911a2530d5)

9. You can access the service through external IP.

10. Setting up Prometheus and Garafana using Helm charts

11. After installing both edit the services type to loadbalancer so that it can be accessible from the browser.

![image](https://github.com/hijackhim/K8s-Prometheus-Grafana-monitoring/assets/105789918/92d67a10-853c-4a4a-b874-def2120d70a4)

12. After accessing Prometheus targets can be seen like this

![prometheus-target](https://github.com/hijackhim/K8s-Prometheus-Grafana-monitoring/assets/105789918/a3a9c254-91b9-4bcd-bf90-f1f619115ea5)

13. After linking both Grafana and Prometheus by selecting Dashboard and entering the URL, Grafana will look like this

![grafana-dashboard](https://github.com/hijackhim/K8s-Prometheus-Grafana-monitoring/assets/105789918/93356dfe-e4b1-46f6-b1a7-7d61dbdbac4a)


THE END--------------------------------------->>>>>>
