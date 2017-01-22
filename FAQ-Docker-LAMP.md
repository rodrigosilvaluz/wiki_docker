Pode, mas está errado fazê-lo.

Quanto maior a responsabilidade de uma imagem, mais complexa essa imagem fica. Hoje temos imagens específicas para cada um dos elementos do LAMP (Linux, Apache, MySQL and PHP).

A questão é: 
* Qual Apache?
* Qual PHP?
* Qual MySQL?

No caso do Apache e do PHP, é um caso em que faz sentido estarem na mesma imagem, no entanto, nunca o MYSQL! Há setups onde Apache e PHP estão separados (vide PHP-FPM). 

Imagens PHP: 
* [PHP @ Docker Hub](https://hub.docker.com/_/php/)

Imagens MYSQL:
* [MySQL @ Docker Hub](https://hub.docker.com/_/mysql/)

LAMP Com Docker Compose:
* [docker-compose-lamp @ tkyk](https://github.com/tkyk/docker-compose-lamp)
* [docker-compose-lamp @ wrender](https://github.com/wrender/docker-compose-lamp)




