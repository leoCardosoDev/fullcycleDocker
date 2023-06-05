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
