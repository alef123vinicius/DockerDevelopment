Lista com os comandos básicos do docker


Lista as imagens que seu docker host tem localmente. As imagens locais não demandam download da nuvem pública do docker, a não ser que precise atualizá-las.

```
docker image list 
```

Para atualizar uma imagem utilize o comando

```
docker image pull <nome da imagem>

docker image pull python

```
Para inspecionar a imagem que acabou de baixar ou qualquer outra utilize o comando inspect. O comando inspect é responsável por informar todos os dados referentes à imagem.

```
docker image inspect <nome da imagem>

docker image inspect python
```
Para iniciar o container utilizaremos o comando run.

Existem parâmetros que podem ser passados na inicialização do container, aqui contém a lista e explicação de alguns

 ____________________________________________________
|Parâmetro |                      Explicação
|__________|_________________________________________
|     -d   | Execução de container em   background
|     -i   | Modo interativo. Mantpem o STDIN
|     -t   | aberto sem console anexado, pseudo TTY
|     -rm  | Remove o container após finalização
|   -name  | Nomear o container
|    -v    | Mapeamento de volume
|    -p    | Mapeamento de porta
|    -m    | Limitar o uso de RAM
|    -c    | Balancear o uso de CPU
|____________________________________________________

```
docker container run <parâmetros> <imagem> <cmd> <argumentos>


```



```

```


```

```


```

```



```

```



```

```



```

```