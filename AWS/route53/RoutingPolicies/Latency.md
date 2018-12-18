### Latency routing policy 

    – Use when you have resources in multiple AWS Regions and you want to route traffic to the region that provides the best latency.
    - Refer: Latency routing policy – Use when you have resources in multiple AWS Regions and you want to route traffic to the region that provides the best latency.
    
1. Create two ubuntu instances, one in Mumbai region & another one is in Ohio region.

    * Mumbai Instance:
         sudo apt-get update -y && sudo apt-get install apache2 -y
         echo "<center><h1>Mumbai Region Apache Server" > /var/www/html/index.html
         service apache start

