# Befehle anhand des Beispiel  Wordpress

Webseite Portainer: localhost:9443
Docker Dokumentation: https://hub.docker.com

- -d = Dämon
- -v = Volumes

### Netzwerk erstellen:
`docker network create "name"`

### MariaDB in Betrieb nehemen
`docker run -d --name mariadb-test --network testnet -e MYSQL_RANDOM_ROOT_PASSWORD=1 -e MYSQL_DATABASE=wp -e MYSQL_USER=wpuser -e MYSQL_PASSWORD=geheim -v myvolume:/var/lib/mysql mariadb`

### phpMyAdmin in Betrieb nehemen
`docker run -d --name pma --network testnet -p 8080:80 -e PMA_HOST=mariadb-test phpmyadmin/phpmyadmin`

### Wordpress in Betrieb nehmen
`docker run -d --name wordpress --network testnet -h wordpres-titel -v wp-html:/var/www/html/wp-content -p 8081:80 -e WORDPRESS_DB_HOST=mariadb-test -e WORDPRESS_DB_USER=wpuser -e WORDPRESS_DB_NAME=wp -e WORDPRESS_DB_PASSWORD=geheim wordpress`
