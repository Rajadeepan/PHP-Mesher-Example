# PHP-Mesher-Example
Example to php client and server working with mesher

Step 1: Install apache

         sudo apt install apache2
             
   check apache
        
         Open a web browser and navigate to  http://localhost/. You should see a message saying it works!

Step 2 : Install PHP

         sudo apt install php libapache2-mod-php php-mcrypt php-mysql php-cli php-curl

   check php
   
         php -r 'echo "\n\nYour PHP installation is working fine.\n\n\n";'

For Testing this php example we need the following components
       service-center, php server, mesher provider, php client and mesher consumer
  
     1)   Start the service-center
     
     2)   Copy api.php and data.php in /var/www/html/

     3)   verify if the api is working by using curl
          curl http://127.0.0.1/api.php?name=book

     4)   export SPECIFIC_ADDR=127.0.0.1 (endpoint where php server is running)
         
          update the microservicename as hellomesher in conf/microservice.yaml
          update the service-center ip  in conf/chassis.yaml
          update the http listen address in chassis.yaml with the vm ip([vm_ip]:30101) and
          serverUri in mesher.yaml with vm ip ([vm_ip]:30102)
          Now start the mesher
          ./PHP-Mesher-Example/mesher/mesher
    
    5)    In a new terminal verify if provider mesher is working
          export http_proxy=http://127.0.0.1:30101  (mesher listen address as specified in chassis.yaml)
          curl http://hellomesher/api.php?name=book

    6)    Start the mesher consumer
          start the mesher by modifiing the listen address(192.168.42.203:30108) in chassis.ymal, serverUri in mesher.yaml             change the port and the        microservicename as hellomesherconsumer in microservice.yaml
          start the mesher.

    7)    In a new terminal export proxy and run client
          export http_proxy=http://127.0.0.1:30108
          php client.php

          get the result from the api.
   
