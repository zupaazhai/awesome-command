# MariaDB docker-compose.yml

```
version: '3.5'

services:
  mariadb:
    container_name: mariadb_container
    image: mariadb
    environment:
      MARIADB_ROOT: root
      MARIADB_ROOT_PASSWORD: p@ssw0rd
    ports:
      - "3306:3306"
    networks:
      - mysql
    restart: unless-stopped
    
networks:
  mysql:
    driver: bridge

volumes:
    mysql:
```
