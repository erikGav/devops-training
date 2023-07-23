# Deploy a Multi Tier web application on AWS

## Tech Stack
* RabbitMQ
* Memcached
* MySQL
* Tomcat

## AWS Services
* EC2 - RabbitMQ, MySQL, Memcached and Tomcat, configure EC2 instances using user data
* Security Groups -
	* Web Server - Allow SSH and load balancer traffic to Tomcat web server
	* Backend Services - Allow port 3306(MySQL), 11211(RabbitMQ), 5672(Memcached) from web server
   		     Allow internal traffic between backed services
	* Load Balancer - Allow HTTP and HTTPS traffic from anywhere
* Key Pairs - Used to connect with SSH to EC2 instances
* Route53 - DNS Private zones for services
* Certificate Manager - Generate a CA signed certificate 
* Elastic Load Balancer - Map ELB endpoint to website name in GoDaddy DNS
* S3 Bucket - Store artifact after build
* Autoscaling Group - Scale app based on load

## App Deployment Procderue
* Update application.properties file with the correct DNS names
* Build app using Maven
* Push artifact to S3 bucket usin AWS CLI
* SSH to Tomcat server and download artifact using AWS CLI
* Copy artifact to Tomcat default root folder

## Architecture Diagram
![alt text](https://github.com/erikGav/devops-training/blob/main/Lift%26Shift/Architecture%20Diagram.png?raw=true)
