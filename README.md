# FullCycle
## Módulo 01 - Docker
### Comandos Docker

Inicie o serviço do Docker:

```
sudo service docker start
```

Este comando acima terá que ser executado toda vez que Linux for reiniciado.

### Correção de problemas 
he steps to fix this are:
```
sudo update-alternatives --config iptables
```
Type number "1" and press Enter to select "iptables-legacy"

```
sudo service docker start
```

### Comandos Docker
#### 01 - Mostrar os Containers Ativos
```
docker ps
```
#### 02 - Buildando a primeira image Hello World

```
docker run hello-world
```
#### 03 - Comando para mostrar TODOS os Containers ativos/desativados
```
docker ps -a
```
#### 04 - Buildando o Ubuntu e executando o bash
```
docker run -it ubuntu bash
```
  ou 
```
docker run -i -t ubuntu bash
```
#### 05 - Iniciando o container a partir do nome da imagem
```
docker start nome_da_imagem
```

#### 06 - Parando o container a partir do nome da imagem
```
docker stop nome_da_imagem
```

#### 07 - Buildar a imagem, executa o bash e remove a imagem depois de sair do bash
```
docker run -it --rm ubuntu:latest bash
```

#### 08 - Publicando portas com nginx
```
docker run -p 8080:80 nginx
```
  ou 
```
docker run -d -p 8080:80 nginx
```
#### 09 - Removendo containers
```
docker rm nome_ou_id_do_container
docker rm nome_ou_id_do_container -f
```

#### 10 - Acessando e alterando arquivos de um container
##### Criando nome para o container
```
docker run --name novo_nome -d -p 80:80 nome_da_imagem
```
##### Executando um comando dentro do container
```
docker exec nginx ls
docker exec -it nginx bash
```

#### 11 - Iniciando com bind mounts
##### Montando um volume para amarrar o container com -v
```
docker run -d --name nginx -p 80:80 -v /home/leoca/fullcycle/modules/01_docker/html:/usr/share/nginx/html nginx
```
##### Montando um volume para amarrar o container com mount e bind
```
docker run -d --name nginx -p 80:80 --mount type=bind,source="$(pwd)"/html,target=/usr/share/nginx/html nginx
```
#### 12 - Trabalhando com volumes
##### Criando um volume
```
docker volume create meuVolume
docker volume ls
docker volume inspect meuVolume
```
##### Mapeando o volume local com o container docker
```
docker run --name nginx -d --mount type=volume,source=meuVolume,target=/app nginx
```
##### Mapeando o volume local com o container docker
```
docker run --name nginx3 -d -v meuVolume:/app nginx
```
##### Limpando os volumes desnecessários
```
docker volume prune
```
#### 13 - Entendendo imagens e DockerHub
##### Imagens no PC
```
docker images
```
##### Baixando imagens no PC (php)
```
docker pull php
```
##### Apagando imagens no PC (php)
```
docker rmi php:latest
```
#### 14 - Criando primeira imagem com Dockerfile

```
docker build -t leosilvadocker/nginx-com-vim:latest .
```

#### 15 - Avançando com Dockerfile

```
docker build -t leosilvadocker/nginx-com-vim:latest .

```
#### 16 - ENTRYPOINT vs CMD

```
docker build -t leosilvadocker/hello .
docker run --rm leosilvadocker/hello:latest
```
##### Dicas importantes
```
docker ps
docker ps -a
docker ps -a -q
```
##### apagar todos os containers
```
docker rm $(docker ps -a -q) -f
```
##### apagar todas as imagens
```
docker rmi $(docker images -q) -f
```

#### 17 - Docker entrypoint exec

```
```
#### 18 - Publicando imagem no Dockerhub

```
docker push leosilvadocker/nginx-fullcycle
```

#### 19 - Entendento tipos de Network

```
Bridge
Host
Overlay
maclan
none
```

#### 20 - Trabalhando com bridge

```
docker network
```
```
docker network ls
```
```
docker network prune
```
```
docker run -d -it --name ubuntu1 bash
docker run -d -it --name ubuntu2 bash
```
```
docker network inspect bridge
```
```
docker attach ubuntu1
```
##### Criando uma nova rede (network)
```
docker network create --driver bridge minharede
```
```
docker run -d -it --name ubuntu1 --network minharede bash
```
##### Conectando um container numa rede
```
docker network connect minharede ubuntu3
```
```
docker network inspect minharede
```

#### 21 - Trabalhando com host

```
docker run --rm -d --name nginx --network host nginx
curl http://localhost
```

#### 22 - Container acessando nossa maquina

```
docker run --rm -d --name nginx --network host nginx
curl http://localhost
```
