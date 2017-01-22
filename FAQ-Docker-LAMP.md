Pode, mas está errado fazê-lo.

Se você é de desenvolvimento, deve estar familiarizado com o conceito de [SRP](https://en.wikipedia.org/wiki/Single_responsibility_principle). Imagens docker devem seguir o mesmo princípio. 

Quando você precisa montar ambientes complexos com diversos containers de produtos/aplicações/serviços diferentes, usa-se Docker-Compose ou qualquer outra ferramenta de orquestração de containers. O mais relevante é que cada container tenha apenas um produto/aplicação/serviço, com docker-compose você compõe o que for necessário. 

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

**Exemplos de Docker Compose com diversos produtos**:
* [Enterprise Log - RabbitMQ, ElasticSarch, LogStash, Kibana](https://github.com/docker-gallery/EnterpriseApplicationLog/blob/master/docker-compose.yaml)
* [Django](https://docs.docker.com/compose/django/)
* [Rails](https://docs.docker.com/compose/rails/)
* [Wordpress](https://docs.docker.com/compose/wordpress/)


