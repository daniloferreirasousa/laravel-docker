
# Laravel + Docker

## Este projeto é um template para projetos que necessitem usar Laravel + Docker

>Versão: 1.1
>
>Autor: **[Danilo Ferreira Sousa](https://github.com/daniloferreirasousa)**
>
>PHP: 8.1.6
>
>MySQL: 5.7

### Instruções:

#### - Faça o download do repositório

#### - Faça a copia do arquivo *.env.example* como o seguinte comando:
`cp .env.example .env`

#### - Altere as seguinte linhas de acordo com suas definições no arquivo *.env*
```Ruby
APP_NAME=#nome do seu projeto
APP_URL=#IP da maquina virtual e a porta de acesso
DB_HOST=#IP da maquina virtual
DB_PORT=#Porta de acesso ao banco de dados
DB_DATABASE=name_database
DB_USERNAME=db_user
DB_PASSWORD=db_password
```

#### - No arquivo *docker-compoe.yml* altere as seguintes linhas conforme os dados inseridos no *.env*
```yml
servieces:
    ports:
        - 8000:80

mysql:
    environment:
      MYSQL_DATABASE: name_database
      MYSQL_USER: db_user
      MYSQL_PASSWORD: db_password
      MYSQL_ROOT_PASSWORD: db_root_password
    ports:
      - 33069:3306
```

#### - Para ver o ip da sua maquina virtual com o seguinte comando:
`docker-machine ip`

> Remova o comentário da linha abaixo no arquivo *.gitignore*
> `# /vendor`


#### - Crie as imagens do docker com:

`docker-compose build`

#### - Agora para subir os containers use:

`docker-compose up -d`

>Obs: Se estiver usando windows, é necessário que o **Docker Toolbox** ou **Doker Desktop** esteja instalado.


---
>Pronto já é possivel acessar o seu projeto pelo ip da sua máquina virtual com a porta definida no arquivo "docker-compose.yml" as portas podem ser alteradas a qualquer >momento de acordo com a necessidade.


>**Info versão 1.1**
> - Correção do envio da pasta vendor
> - Definição de variáveis padrão do servidor
> - Correção de restart do servidor
> - Remoção da imagem do NodeJS do projeto