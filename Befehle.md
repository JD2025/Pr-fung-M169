# Befehle anhand des Beispiel  Wordpress

Webseite Portainer: localhost:9443
Docker Dokumentation: https://hub.docker.com

-d = Dämon

### Netzwerk erstellen:
`docker network create "name"`

### MariaDB in Betrieb nehemen
`docker run -d --name mariadb-test --network testnet -e MYSQL_RANDOM_ROOT_PASSWORD=1 -e MYSQL_DATABASE=wp -e MYSQL_USER=wpuser -e MYSQL_PASSWORD=geheim -v myvolume:/var/lib/mysql mariadb`

### phpMyAdmin in Betrieb nehemen
`docker run -d --name pma --network testnet -p 8080:80 -e PMA_HOST=mariadb-test phpmyadmin/phpmyadmin`