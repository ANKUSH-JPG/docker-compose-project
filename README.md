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
     
     - setenforce 0
   you can view the permissions by using:
     
     - getenforce
   once done you can use systemctl to start your docker and there you can launch your container's:
     
     - systemctl start docker
     
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
    
    - docker pull ghost
    - docker pull mysql
    
this will pull the latest version of both the images . so that will be fine and will work here .
    
# 6. CREATING A DOCKER-COMPOSE.YML FILE:
create a directory by any name . I used ghost as my main directory . change the directory to your main directory and create a file       named docker-compose into that directory and open it using the vim editor.
    
    - cd ghost
    - vim docker-compose.yml
    
this will open vim editor for you to add the content into your docker-compose.yml file. now press i to insert into your file .
and write the following code into the file :
    
![Screenshot (333)](https://user-images.githubusercontent.com/51692515/80371338-5ed6a100-88af-11ea-95fb-ace323a2953d.png)

# NOW LET'S DISCUSS IN DETAIL ABOUT THE CODE IN THE FILE:
- firstly you need to specify the version that you are currently using . i used version 3 .
- next is the services section , where we actually define the services that we want to run ,like here i run two containers and the further configurations into it.
- next i used the image of mysql that i already downloaded from docker hub and started a container named mysql_container . And the restart command will always start the container whenever the compose file is executed.
- next i created a volume named mysql volume and mounted on the default configuration file of mysql . this will keep a record of all the databases and tables created by the users . 
- next is the environment variables :these are the variables that are needed to be provided when we start a container , and that are necessary for that container to run properly.


- next i started my another container that is a frontend blog posting site named ghost . i alredy downloaded the image of ghost from docker hub.
- i restarted the container and provided the volume named ghost_volume and mounted on the default configuration file of the apache webserver present in the same container that come installed with ghost.
- next part was to link the frontend with backend i.e. linking the ghost with mysql so i used depends_on to link the two containers so that they can interact with one another when they are deployed in the real world.
- next was the port binding since the outer world would not be able to access our front end if we host it in the docker world . so used port mapping so that our container could be accessed from the outer world. 
BY DEFAULT THE SERVICE RUN ON PORT 2368 AND BY PORT MAPPING I ALLOWED IT TO RUN ON PORT 3001 OF THE LOCAL HOST.
- next i provided some environment variables required for the ghost_container to interact with the backend.

THIS IS HOW I COMPLETED MY DOCKER-COMPOSE.YML FILE 
TO EXIT DOCKER-COMPOSE FILE I PRESSED ESC AND :wq TO SAVE THE COMPOSE FILE.

# 7. EXECUTING THE DOCKER-COMPOSE.YML FILE :
command that i used to execute the compose file was:
         - docker-compose up
 
as i run the command following output came and the containers were succesfully created and launched with all the functionalities.

![Screenshot (334)](https://user-images.githubusercontent.com/51692515/80406753-2ef4c100-88e2-11ea-92e3-72a7d87f6b86.png)



![Screenshot (335)](https://user-images.githubusercontent.com/51692515/80406796-3e740a00-88e2-11ea-9aca-ac63cbb1b082.png)


# 8. CONTAINER'S WERE CREATED:
the container's that were created:


![Screenshot (336)](https://user-images.githubusercontent.com/51692515/80406872-5cda0580-88e2-11ea-81b1-ee12548f8f69.png)


# 9. RUNNING THE GHOST :
i created another virtual machine and tried to connect to the ghost image that i deployed in other virtual machine and i was sucessfully able to access the site.

NOTE : I CONNECTED TO 3001 PORT THAT I USED DURING THE PORT MAPPING.

![Screenshot (338)](https://user-images.githubusercontent.com/51692515/80407140-c823d780-88e2-11ea-8ffd-1a7acc9608a5.png)



NOTE: NOW WHEN I TRIED TO CONNECT TO THE SAME CONTAINER USING THE DEFAULT PORT EXECUTION OF GHOST I WAS NOT ABLE TO CONNECT BECAUSE IT IS HIDDEN INTO THE DOCKER WORLD AND IS NOT SHOWN TO OUTER WORLD .  THATS WHY PORT MAPPING IS REQUIRED.

![Screenshot (337)](https://user-images.githubusercontent.com/51692515/80407430-3d8fa800-88e3-11ea-8362-b4bcb741a90c.png)


# 10. STOPPING DOCKER-COMPOSE.YML FILE :

use the following command to stop the docker-compose.yml file:
      - docker-compose stop
      

![Screenshot (340)](https://user-images.githubusercontent.com/51692515/80407539-64e67500-88e3-11ea-9ad6-e7a5ddb16ec6.png)



YOU CAN SEE THE SERVICE ALSO STOPPED:

![Screenshot (339)](https://user-images.githubusercontent.com/51692515/80407526-60ba5780-88e3-11ea-9c97-d5af6f850c63.png)


AND THE CONTAINERS WERE ALSO STOPPED:

![Screenshot (341)](https://user-images.githubusercontent.com/51692515/80407872-ed651580-88e3-11ea-802f-0ddc874895b9.png)



  
# 11. FUTURE DEVELOPMENTS:
This whole setup is done in local machine and no other tools like devops and all were used here for the monitoring and logs purpose so we can also integrate some devops tools to automate this system more and have more look and feel .You can also create your own webapp with many different softwares with other supported database servers.
     

 

 
