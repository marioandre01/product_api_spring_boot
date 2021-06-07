[![Author](https://img.shields.io/badge/author-marioandre01-00b300?style=flat-square)](https://github.com/marioandre01)
[![Languages](https://img.shields.io/github/languages/count/marioandre01/product_api_spring_boot?color=%2300b300&style=flat-square)](#)
[![Stars](https://img.shields.io/github/stars/marioandre01/product_api_spring_boot?color=00b300&style=flat-square)](https://github.com/marioandre01/product_api_spring_boot/stargazers)
[![Forks](https://img.shields.io/github/forks/marioandre01/product_api_spring_boot?color=%2300b300&style=flat-square)](https://github.com/marioandre01/product_api_spring_boot/network/members)
[![Contributors](https://img.shields.io/github/contributors/marioandre01/product_api_spring_boot?color=00b300&style=flat-square)](https://github.com/marioandre01/product_api_spring_boot/graphs/contributors)
[![Licence](https://img.shields.io/github/license/marioandre01/product_api_spring_boot?color=%2300b300&style=flat-square)](https://github.com/marioandre01/product_api_spring_boot/blob/master/LICENCE.md)


<h1 align="center">
  <img alt="logo-spring" title="logo-spring" src="src/main/resources/imgs/logo_spring_boot.svg" width="200px" />
  <br>
  product_api_spring_boot
</h1>

<p align="center"> 
  <a href="#-projeto">Projeto</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-tecnologias">Tecnologias</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-executando-a-aplicação">Executando a aplicação</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#gear-contribuição">Contribuição</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#memo-licença">Licença</a>
</p>

## 💻 Projeto

Este projeto tem como objetivo desenvolver uma API de produtos utilizando o framework spring boot.

O resultado da aplicação pode ser acessado através da seguinte URL: 

## 📋 Tecnologias

O projeto foi desenvolvido com as seguintes tecnologias:

- [Java](https://www.java.com/pt-BR/)
- [Spring boot](https://spring.io/)
- [Lombok](https://projectlombok.org/)
- [Docker](https://docs.docker.com/engine/install/ubuntu/)
- Postgres (No docker)

<!-- ## 🎨 Layout

### 💻 Web 

<p align="center">
  <img alt="Podcastr web" title="Podcastr web" src="public/podcastr-tela01.png" width="800px">
  <img alt="Podcastr web" title="Podcastr web" src="public/podcastr-tela02.png" width="800px">
  <img alt="Podcastr web" title="Podcastr web" src="public/podcastr-tela03.png" width="800px">
</p>
</p> -->

### :octocat: Clonando o Repositório

```bash
$ git clone https://github.com/marioandre01/product_api_spring_boot.git

# entre na pasta do projeto
$ cd product_api_spring_boot
```
### 💻 Executando a aplicação

Com o docker instalado executar:
```bash
$ sudo docker run -d -p 5432:5432 -e POSTGRES_PASSWORD=postgres postgres
```

Com o "psql" instalado usa-lo para acessar o postgres:
```bash
$ psql -h 127.0.0.1 -U postgres -W
```
A senha é **postgres**

criar o database "dev" no banco
```sql
CREATE DATABASE dev;
```

Sair do postgres
```sql
exit;
```

Para executar a aplicação há duas formas usando o maven:

Caso o maven não esteja instalado executar:

```bash
$ sudo apt install maven
```
A primeira maneira é usando o comando **spring-boot:run**

```bash
$ mvn spring-boot:run
```
A aplicação será iniciada.

A segunda maneira é gerando o seu arquivo **.jar**

 executar o comando:
```bash
$ mvn clean package
```
Será iniciado o processo de build e será gerado a pasta **target** na pasta raiz do projeto. Dentro dela estará o arquivo **.jar** criado.

Então entrar na pasta **target**
```bash
$ cd target
```
E executar:
```bash
$ java -jar nome_do_arquivo.jar
```
A aplicação será iniciada.

Agora acessar as rotas da API para usar os seus serviços. Para acessar as rotas, usar os softwares [insomnia](https://insomnia.rest/download) ou [Postman](https://www.postman.com/downloads/).

### Rotas GET
- getProducts

  [GET] `http://localhost:8081/product`
  #### Resposta:   
  ```bash
    [
      {
        "productIdentifier": "tv",
        "nome": "TV",
        "preco": 1000.0,
        "descricao": "Uma TV",
        "category": {
          "id": 3,
          "nome": "Brinquedos"
        }
      },
      {
        "productIdentifier": "Boneca",
        "nome": "Boneca feliz",
        "preco": 100.0,
        "descricao": "Uma Boneca",
        "category": {
          "id": 3,
          "nome": "Brinquedos"
        }
      },
      {
        "productIdentifier": "Sofá",
        "nome": "Sofá soft",
        "preco": 400.0,
        "descricao": "Uma sofá",
        "category": {
          "id": 2,
          "nome": "Móveis"
        }
      }
    ]  
  ```
  
- get-products-category-id

  [GET] `http://localhost:8081/product/category/1`
  #### Resposta: 
  ```bash   
    [
      {
        "nome": "tv led",
        "preco": 2000.0,
        "descricao": "Uma tv",
        "productIdentifier": "tv"
      },
      {
        "nome": "notebook dell",
        "preco": 3000.0,
        "descricao": "Uma notebook",
        "productIdentifier": "notebook"
      }
    ]
  ```

- get-productIdentifier

  [GET] `http://localhost:8081/product/tv`
  #### Resposta:
  ```bash   
    {
      "productIdentifier": "tv",
      "nome": "TV",
      "preco": 1000.0,
      "descricao": "Uma TV",
      "category": {
        "id": 3,
        "nome": "Brinquedos"
      }
    }
  ```
  Se colocar um Cpf que não esta cadastrado vai retorna **Null**

### Rota POST
- post-product

  [POST] `http://localhost:8081/product/`
  #### Corpo da mensagem (json): 
  ```bash   
    {
      "productIdentifier":"cama",
      "nome":"Cama box",
      "preco": 700,
      "descricao": "Uma cama box",
      "category": {
        "id": 2
      }
    }
  ```

### Rota DELETE
- delete-product

  [DELETE] `http://localhost:8081/product/1`
  #### Resposta: 
  ```bash   
    # retorna nada (void)
  ```
  Se colocar um id que não esta cadastrado vai retorna **Null**


## :gear: Contribuição

Para contribuir com esse projeto faça os seguintes passos:

- Faça um fork desse repositório;
- Crie uma branch com a sua feature: `git checkout -b minha-feature`;
- Faça commit das suas alterações: `git commit -m 'feat: Minha nova feature'`;
- Faça push para a sua branch: `git push origin minha-feature`.

## :memo: Licença

Esse projeto está sob a licença MIT. Veja o arquivo [LICENSE](./LICENSE.md) para mais detalhes.





