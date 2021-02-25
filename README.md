# DockerDevelopment

# O que é Docker 

Docker é uma plataforma aberta, criada com o objetivo de facilitar o desenvolvimento, a implantação e a execução de aplicações em ambientes isolados.

Docker utiliza o modelo de container para empacotar a aplciação que, após ser transformada em imagem Docker, pode ser reproduzida em plataforma de qualquer porte, ou seja, se funcionar no notebook também funcionará no servidor ou mainframe.


Os containers são isolados a nível de disco, memória, processamento e rede. Essa seaparação permite flexibilidade, onde ambientes distintos podem coexistir no mesmo host.

# Instalação Linux

Acesse o terminal linux e execute os seguintes comandos. Lembrando que aqui está uma forma genérica de instalar o Docker, caso dê alguma problema veja a instalação na documentação oficial do docker

```
su - root
```

ou

```
sudo su - root
```

Execute o seguinte comando

```
wget -qO- https://get.docker.com/ | sh
```

Para testar utilize

```
docker container run hello-world
```

Alguns problemas com o apt-key podem surgir nesse momento, caso o acesso da máquina tenha controle de tráfego. Para resolver este problema execute o comando

```
wget -qO- https://get.docker.com/gpg | sudo apt-key add -
```

# Instalação do docker composer

```
su - root
```

ou

```
sudo su - root
```

```
curl -L https://github.com/docker/compose/release\
s/download/1.6.2/docker-compose-`uname -s`-`uname\
-m` > /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
```

Para testar execute o seguinte comando:

```
docker-compose version
```

O docker compose é escrito em Python e possui um instalador através do pip

```
pip install docker-compose
```

# Instalando o Docker Machine


```
su - root
```

ou

```
sudo su - root
```

```
curl -L https://github.com/docker/machine/relea\
ses/download/v0.7.0/docker-machine-`uname -s`-`un\
ame -m` > /usr/local/bin/docker-machine && \
chmod +x /usr/local/bin/docker-machine
```

Para testar

```
docker-machine version
```

## observação importante

Todos os comandos (curl, wget, pip, ..,) precisam estar instalados na sua versão do linux para conseguir executar os passos acima.

