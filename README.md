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
  

     1)  copy api.php and data.php in /var/www/html/

     2)   verify if the api is working by using curl
          curl http://127.0.0.1/api.php?name=book

     3)   export SPECIFIC_ADDR=127.0.0.1 (endpoint where php server is running)
         
          check the microservicename as hellomesher in conf/microservice.yaml
          check the service-center ip specified in conf/chassis.yaml 
          Now start the mesher
          ./PHP-Mesher-Example/mesher/mesher
    
    4)  In a new terminal verify if provider mesher is working
        export http_proxy=http://127.0.0.1:30101  (mesher listen address as specified in chassis.yaml)

    5) Start the mesher consumer
       start the mesher by modifiing the listen address(192.168.42.203:30108) in chassis.ymal, serverUri in mesher.yaml change the port and the        microservicename as hellomesherconsumer in microservice.yaml
        start the mesher.

    6) In a new terminal export proxy and run client
        export http_proxy=http://127.0.0.1:30108
        php client.php

        get the result from the api.
   

            
      
