# Deploy a Multi Tier web application on AWS

## Tech Stack
Tech Stack:
* RabbitMQ
* Memcached
* MySQL
* Tomcat

## AWS Services
AWS Services:
	EC2:
		RabbitMQ, MySQL, Memcached and Tomcat, configure EC2 instances using user data
	Security Groups:
		Web Server - Allow SSH and load balancer traffic to Tomcat web server
		Backend Services - Allow port 3306(MySQL), 11211(RabbitMQ), 5672(Memcached) from web server
						   Allow internal traffic between backed services
		Load Balancer - Allow HTTP and HTTPS traffic from anywhere
	Key Pairs - Used to connect with SSH to EC2 instances
	Route53 - DNS Private zones for services
	Certificate Manager - Generate a CA signed certificate 
	Elastic Load Balancer - Map ELB endpoint to website name in GoDaddy DNS
	S3 Bucket - Store artifact after build
	Autoscaling Group - Scale app based on load

## App Deployment
App is written in Java so I used Maven to build it locally on my PC
After build upload artifact to S3 Bucket using AWS CLI
Connect to Tomcat server via SSH and copy the artifact using AWS CLI
	

## Architecture
![alt text](https://github.com/erikGav/devops-training/blob/main/Lift%26Shift/Architecture.png?raw=true)
