# PHP-Mesher-Example
   

 1) Start the service center (download the service center from http://servicecomb.incubator.apache.org/release/)
 2) Load the mesher image from the folder	./mesher/mesher.tar
 
     docker load -i mesher.tar
 3) update the servicecenter ip addres in docker-compose.yml
 4) docker-compose up [./mesher directory]
 5) To verify the php client and php server communication
 
       curl request http://[ipaddress of the client]:80/client.php
      
