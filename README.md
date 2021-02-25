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


## Qual a diferença entre imagem e container ?

A imagem é a abstração da infraestrutura em estado somente leitura, de
onde será instanciado o container. Todo container é iniciado a partir de 
uma imagem, dessa forma podemos concluir que nunca teremos uma imagem em
execução.

Fazendo um paralelo com OO pode-se dizer que a imagem é a classe e o container o objeto.

Um container só pode ser iniciado a partir de uma única imagem


Imagens oficiais são mantidas pela empresa docker (cuja não contém o nome) do
usuário na descrução da imagem como ubuntu:16.04 (não oficial alef/ubuntu)

um repo pode ter várias tags e o conjunto repo:tag define uma imagem.

Nome da imagem

repositorio:tag

docker image list

formas de criar uma imagem

# commit

É possível criar imagens executando o comando commit,
relacionado a um container. Esse comando usa o status atual
do container escolhido e cria a imagem com base nele.

docker container run -it --name containercriado ubuntu:16.04 bash

no bash

apt-get update
apt-get install nginx -y
exit

docker container stop containercriado

docker container commit containercriado meuubuntu:nginx

docker image list

docker container run -it --rm meuubuntu:nginx dpkg -l nginx

# Dockerfile

Quando se utiliza Dockerfile para gerar uma imagem, basicamente, 
é apresentada uma lista de instruções que serão aplicadas em 
determinada imagem para que outra imagem seja gerada com base nas
modificações.

 ____________      _____________     __________________
|imagem base |--->| dockerfile  |-->| imagem modificada|
|____________|--->| modificações|-->|__________________|

# Comandos do Dockerfile

**FROM** para informar qual imagem usaremos como base,
nesse caso foi ubuntu:16.04.

**RUN** para informar quais comandos serão executados nesse
ambiente para efetuar as mudanças necessárias na infraestru-
tura do sistema. São como comandos executados no shell do
ambiente, igual ao modelo por commit, mas nesse caso foi
efetuado automaticamente e, é completamente rastreável, já
que esse Dockerfile será armazenado no sistema de controle
de versão.

**COPY** é usado para copiar arquivos da estação onde está
executando a construção para dentro da imagem. Usamos um
arquivo de teste apenas para exemplificar essa possibilidade,
mas essa instrução é muito utilizada para enviar arquivos de
configuração de ambiente e códigos para serem executados
em serviços de aplicação.

**CMD** para informar qual comando será executado por pa-
drão, caso nenhum seja informado na inicialização de um
container a partir dessa imagem. No exemplo, colocamos o
comando bash, se essa imagem for usada para iniciar um
container e não informamos o comando, ele executará o bash.

docker image build -t meuubuntu:nginx_auto

-t      informar o nome da imagem a ser criada.

A sugestão para melhor aproveitar o cache do Dockerfile é
sempre manter as instruções frequentemente ateradas mais
próximas da base do documento. Vale lembrar de atender
também as dependências entre instruções.

# Volumes

Ao utilizar volumes, o Docker monta essa pasta (camada) no
nível imediatamente inferior ao do container, o que permite o
acesso rápido de todo dado armazenado nessa camada (pasta),
resolvendo o problema de performance.

O volume também resolve questões de persistência de da-
dos, pois as informações armazenadas na camada (pasta) do
container são perdidas ao remover o container, ou seja, ao
utilizar volumes temos maior garantia no armazenamento
desses dados.


docker container run -v /var/lib/container1:/var ubuntu

docker create -v /dbdata --name dbdata postgres bin/true

No comando acima, criamos um container de dados, onde a
pasta /dbdata pode ser consumida por outros containeres, ou
seja, o conteúdo da pasta /dbtada poderá ser visualizado e/ou
editado por outros containeres.
Para consumir esse volume do container basta utilizar o
comando:

docker container run -d --volumes-from dbdata --name db2 postgres

