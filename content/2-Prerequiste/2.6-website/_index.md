---
title : "Create Public instance"
date : "`r Sys.Date()`"
weight : 5
chapter : false
pre : " <b> 2.1.5 </b> "
---

Connect to the EC2 instance using SSH.

Navigate to the /var/www/html directory using the command cd /var/www/html.

Create a folder named test-cog using the command sudo mkdir test-cog.

Navigate to the test-cog folder using the command cd test-cog.

Create an index.html file using the command sudo nano index.html. Add the following content to the file:


Replace YOUR-ALB-DNS with the DNS name of your ALB.

Create a logged_in.html file using the command sudo nano logged_in.html. Add the following content to the file:


Replace YOUR-ALB-DNS with the DNS name of your ALB.

Create a logged_out.html file using the command sudo nano logged_out.html. Add the following content to the file:


Replace YOUR-ALB-DNS with the DNS name of your ALB.

Save the files by pressing Ctrl+X, then Y, and then Enter.

Restart the Apache web server using the command sudo service httpd restart.