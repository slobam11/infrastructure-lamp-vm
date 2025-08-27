LAMP Stack Deployment on AlmaLinux in VMware

This project contains step-by-step instructions to deploy a LAMP (Linux, Apache, MariaDB, PHP) server on AlmaLinux 9 within a VMware ESXi environment. Suitable for system administration practice, home labs, or basic infrastructure setup.


Step 1. First we build up ESXI infrastructure, or you don’t have it. It is fine on OVB or VMware Workstation. 
 <img width="328" height="114" alt="image" src="https://github.com/user-attachments/assets/20795639-ad4b-4eac-a0f7-59208fa2670b" />
 First I update the system with the following command:  We don’t need the sudo if you are working with root.  You can give sudo privileges for your user at visudo.
 <img width="305" height="107" alt="image" src="https://github.com/user-attachments/assets/1d0747ad-859c-403a-b1ba-1d1c336f3afa" />
 <img width="348" height="82" alt="image" src="https://github.com/user-attachments/assets/ea0cd500-8d2b-4552-a1eb-cebe2f566dd7" />

 Step 2 : We need to install Mariadb server with coomand : 
 dnf if you are a root user : dnf install mariadb-server , if you are not a root user you can use sudo dnf install mariadb-server
 <img width="389" height="161" alt="image" src="https://github.com/user-attachments/assets/5123c511-e662-4159-b7cd-0d5c1effa5f7" />
 <img width="460" height="107" alt="image" src="https://github.com/user-attachments/assets/4a2cf203-7f4c-446f-b52f-7da0cdbd0c17" />


 Secure the MySQL Installation  - AFter that  "Answer the questions: root password, removing anonymous users, disabling remote root login, etc."
 <img width="554" height="33" alt="image" src="https://github.com/user-attachments/assets/ed13a1d3-53b3-4daf-a49e-e123cd190104" />

Step 3 : Install PHP and necessary modules, then enable the service.
<img width="374" height="219" alt="image" src="https://github.com/user-attachments/assets/07d7b505-7ce8-4275-b633-75f24930ccd6" />

now test the PHP-a 
echo "<?php phpinfo(); ?>" | sudo tee /var/www/html/info.php

So, maybe you will have to allow port 80 to have access to your web. 
sudo firewall-cmd --permanent --add-service=http
sudo firewall-cmd --reload

Alma Linux is using firewalld. 

Or you can do the direct port.

sudo firewall-cmd --permanent --add-port=80/tcp
sudo firewall-cmd --reload
Test in you browser     http://<IP_VM>/info.php
<img width="286" height="260" alt="image" src="https://github.com/user-attachments/assets/86ab9d33-8bbb-4394-8ba5-5161e1daebba" />

That is it . 

# Author # 
Slobodan Milojevic
