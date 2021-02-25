Parâmetros

-d      executa o container em background
-i      modo interativo
-t      aloca um pseudo terminal
-rm     remove o container após finalização
-name   nomear o container
-v      mapeamento de volume
-p      mapeamento de porta
-m      limitar uso de memória
-c      balacnear uso de cpu

docker container run -it --rm --name meu_python python bash

docker container run -it --tm -v "<host>:<container>" python

docker container run -it --rm -p "<host>:<container>" python

docker container run -it --rm -p 80:8080 python

docker container run -it --rm -m 512M python

docker container run -it --rm -c 512 python

docker ps 

docker container list

parâmetros mais utilizados

-a      lista todos os containers on ou off
-l      lista os últimos containers
-n      lista os últimos N containers
-q      lista apenas os id dos containers


docker stop [ CONTAINER_ID ou CONTAINER_NAME ]

docker container stop meu_python

docker container start meu_python

