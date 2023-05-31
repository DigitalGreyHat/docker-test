Aufgabe 1:

docker network create --driver=bridge --subnet=192.168.1.0/24 --gateway=192.168.1.1 gbsnet

docker network inspect gbsnet


Aufgabe 2:

docker run -d --name gbsdb --network gbsnet --ip 192.168.1.2 -v gbsdbjoomla:/var/lib/mysql -e MYSQL_DATABASE=joomla_db -e MYSQL_ROOT_PASSWORD=-gbs- mysql:5.7


Aufgabe 3:

docker run -d --name phpmyadmin --network gbsnet -p 8080:80 -e PMA_HOST=gbsdb phpmyadmin/phpmyadmin


Aufgabe 4:

docker run -d --name gbsjoomla --network gbsnet -v gbsjoomla:/var/www/html -p 80:80 -e JOOMLA_DB_HOST=gbsdb:3306 -e JOOMLA_DB_NAME=joomla_db -e JOOMLA_DB_USER=root -e JOOMLA_DB_PASSWORD=-gbs- joomla


Aufgabe 5:


Aufgabe 6:
docker run -d --name gbsmariadb --network gbsnet -e MYSQL_ROOT_PASSWORD=strenggeheim -e MYSQL_DATABASE=wp -e MYSQL_USER=wpuser -e MYSQL_PASSWORD=geheim -v gbsdbwordpress:/var/lib/mysql mariadb

docker run -d --name gbswordpress --network gbsnet -v gbswordpress:/var/www/html -p 80:80 -e WORDPRESS_DB_HOST=gbsmariadb -e WORDPRESS_DB_USER=wpuser -e WORDPRESS_DB_NAME=wp -e WORDPRESS_DB_PASSWORD=geheim wordpress


