# docker-compose-project
# WHAT THE PROJECT IS ALL ABOUT :GHOST AT FRONTEND AND MYSQL SERVER AT BACKEND. 

# DOCUMENTATION OF PROJECT 
( TOPIC: REAL WORLD APPLICATION ON HOW THE CONTAINERIZATION IS USED FOR DEPLOYMENT PURPOSE USING DOCKER COMPOSE. )


BEFORE ANY FURTHER DISCUSSION ON THE PROJECT I WOULD FIRST LIKE TO THANK Mr. VIMAL DAGA SIR, FOR TEACHING US THE TECHNOLOGY OF DOCKER, WHICH IS WIDELY USED THESE DAYS IN DEVOPS WORLD AND MAINLY FOR THE PURPOSE OF DEPLOYMENT OF PROJECTS.
IT WAS VERY NICE WORKING WITH SIR AS HE ALWAYS CLEARED OUR DOUBT’S WHENEVER NEEDED.SO, THANK YOU ONCE AGAIN SIR FOR GIVING SUCH A BIG OPPORTUNITY TO US AND FOR LAUNCHING IIEC RISE 1.0 CAMPAIGN SO THAT EVERYONE CAN HAVE RIGHT EDUCATION.

# THANK YOU SIR !!!!!!!!

# PROJECT DESCRIPTION :
 
# 1. TOOLS AND KNOWLEDGE REQUIRED:
1.	ghost docker hub image
2.	mysql docker hub image
3.	volume concepts of docker
4.	port forwarding concept
5.	linking concept of container's
6.	docker-compose

# 2. ABOUT GHOST AND MYSQL:
GHOST:
Ghost was launched in 2013 after a successful Kickstarter campaign led by former WordPress employee John O'Nolan. During that            campaign, O’Nolan described Ghost with the same words that used to describe WordPress, “just a blogging platform.”
It’s free, open source, built on NodeJS and it mimics WordPress’ dual offering of self-hosted and hosted options — although there        aren’t as many restrictions if you opt for the hosted version of Ghost.
   
MYSQL:
MySQL is the most popular Open Source Relational SQL Database Management System. MySQL is one of the best RDBMS being used for          developing various web-based software applications. MySQL is developed, marketed and supported by MySQL AB, which is a Swedish          company. This tutorial will give you a quick start to MySQL and make you comfortable with MySQL programming.
   
# 3. CONFIGURATION REQUIRED:
There is no as such configuration required . you can work with any of the linux flavours or even with the windows ,the inital           process of installing docker and docker-compose may be different but once it is installed and you are using CLI to acces the docker     the process is same .
THE OPERATING SYSTEM THAT I WORKED WITH WAS REHL8(REDHAT ENTERPRISE LINUX VERSION 8 ) ,SO THIS DOCUMENT IS ONLY ACCORDING TO THAT.
    
# 4. SETTING UP DOCKER AND DOCKER-COMPOSE:(steps are explained after the docker installation)
DOCKER:
     firstly , you need to set the permission to permissive so that you are able to connect to your docker deamon.
     - SETENFORCE 0
     you can view the permissions by using:
     - GETENFORCE
     once done you can use systemctl to start your docker and there you can launch your container's:
     - SYSTEMCTL START DOCKER 
     
DOCKER-COMPOSE :
   i downloaded docker compose from the link mentioned below , download it from the same url:
     - curl -L "https://github.com/docker/compose/releases/download/1.25.5/docker-compose-$(uname -s)-$(uname -m)" -o                          /usr/local/bin/docker-compose
     
   now you will not be able to execute your docker-compose .so , you need to change the permissions of docker-compose to executable:
     - chmod +x /usr/local/bin/docker-compose
     
   when you do the above steps , you will be ready with the docker-compose and docker now start creating your docker-compose.yml file.
     
   
# 5. DOWNLOADING REQUIREMENTS FROM DOCKER HUB :
for this project we require two images from docker hub:
    - ghost image.
    - mysql server image.
    
so , open your docker as per the steps mentioned above and pull the images from docker hub :
    - DOCKER PULL GHOST
    - DOCKER PULL MYSQL 
    
this will pull the latest version of both the images . so that will be fine and will work here .
    
# 6. CREATING A DOCKER-COMPOSE.YML FILE:
create a directory by any name . I used ghost as my main directory . change the directory to your main directory and create a file       named docker-compose into that directory and open it using the vim editor.
    - cd ghost
    - vim docker-compose.yml
    
this will open vim editor for you to add the content into your docker-compose.yml file. now press i to insert into your file .
and write the following code into the file :
    
   ![]{screenshot/Screenshot (333).png}
     

 

 
