AWS EC2 Instance Setup with User Data Script

This guide covers the process of launching an EC2 instance in AWS and running user data scripts to automate instance configuration.
AWS EC2 User Data allows you to pass scripts to your instance that execute on startup, such as installing software or configuring services.

Steps to Launch an EC2 Instance and Use User Data :

1. Launch an EC2 Instance
To get started with launching an EC2 instance:

Go to the AWS Management Console.
Navigate to EC2 and click Launch Instance.
Choose an Amazon Machine Image (AMI) based on your operating system preference (Linux/Windows).
Select the Instance Type based on your performance and cost requirements.
Configure your instance settings like networking, storage, and more.

2. Add User Data Script:

User Data scripts can automate software installation and configurations when the instance starts. 
This is especially helpful for automating the initial setup process.

In the Advanced Details section of the instance configuration, you can add a user data script.
For Linux instances, you can use a bash script.

Example:

#!/bin/bash
yum update -y
yum install httpd -y
systemctl start httpd
systemctl enable httpd
echo "<h1>Hello World from $(hostname -f)</h1>" > /var/www/html/index.html

3. Retrieve Output of the User Data Script

Once your instance is launched, you can access it to verify the execution of the user data script:

Copy the Public IP Address of your instance from the EC2 dashboard.
Open a browser and enter the IP address to check if the output of your script is visible (e.g., a webpage if you've installed a web server).


Additional Notes:

Make sure your Security Groups allow access on the necessary ports (e.g., port 80 for HTTP or port 22 for SSH).
You can modify or disable the user data scripts after launch, but they will only run during the first boot unless configured otherwise.

