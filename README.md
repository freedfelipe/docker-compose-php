# docker-composer-php

docker-compose setup to run php5.6 or php7 with php-fpm via nginx and mysql. Connecting from php on a mysql database still fails. Not sure why.

# Purpose

Create the ultimate development environment 

# Install

Install docker and docker-compose [https://docs.docker.com/compose/install/]

# Run

Clone the project and cd to the root projec and run:

		$ docker-compose build
		$ docker-compose up -d

# Test

Open url http://localhost:8000 and you will see a phpinfo page

# Todo

- Fix database connection issue.
- Run Symfony app (my purpose)
- Integrate dns solution (eg dnsmasq)
- more ideas are welcome!

# DNS

		docker start skydns || docker run -d -p 172.17.42.1:53:53/udp --name skydns crosbymichael/skydns -nameserver 8.8.8.8:53 -domain docker
		
		docker start skydock || docker run -d -v /var/run/docker.sock:/docker.sock --name skydock crosbymichael/skydock -ttl 30 -environment dev -s /docker.sock -domain docker --name skydns

