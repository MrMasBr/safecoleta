# SafeColeta

SafeColeta é um serviço RESTful para gerenciamento de caminhões de coleta de lixo inteligente. Este projeto utiliza Spring Boot para criar a aplicação e PostgreSQL como banco de dados.

## Requisitos

- Docker
- Docker Compose
- Java 11
- Maven

## Estrutura do Projeto

- `src/main/java`: Código-fonte Java
- `src/main/resources`: Recursos da aplicação (arquivos de configuração)
- `target`: Diretório onde o JAR compilado será gerado
- `pom.xml`: Arquivo de configuração do Maven
- `Dockerfile`: Arquivo de configuração do Docker para a aplicação
- `docker-compose.yml`: Arquivo de configuração do Docker Compose para gerenciar contêineres

## Configuração do Ambiente

### Compilando a Aplicação

Antes de construir a imagem Docker, compile a aplicação para gerar o arquivo JAR. No diretório raiz do projeto (`safecoleta`), execute:

```sh
./mvnw clean package
```

### Construindo a Imagem Docker

No diretório raiz do projeto (`safecoleta`), execute o comando para construir a imagem Docker:

```sh
docker build -t safecoleta .
```

### Executando a Aplicação com Docker Compose

Para iniciar os serviços definidos no `docker-compose.yml`, use:

```sh
docker-compose up
```

Isso iniciará tanto a aplicação Spring Boot quanto o banco de dados PostgreSQL em contêineres Docker.

### Parando os Contêineres

Para parar e remover os contêineres, use:

```sh
docker-compose down
```

## Configurações do Banco de Dados

As configurações do banco de dados são definidas no arquivo `docker-compose.yml`:

```yaml
environment:
  SPRING_DATASOURCE_URL: jdbc:postgresql://db:5432/mydb
  SPRING_DATASOURCE_USERNAME: user
  SPRING_DATASOURCE_PASSWORD: password
```

Certifique-se de que as credenciais do banco de dados correspondam às configurações da sua aplicação Spring Boot.

## Endpoints da API

Abaixo estão alguns dos principais endpoints disponíveis na aplicação:

- `GET /api/caminhoes`: Lista todos os caminhões de coleta
- `POST /api/caminhoes`: Adiciona um novo caminhão de coleta
- `GET /api/coletas`: Lista todas as coletas agendadas
- `POST /api/coletas`: Agenda uma nova coleta

## Segurança

O projeto inclui uma configuração de segurança básica utilizando Spring Security. As configurações de segurança podem ser encontradas no pacote `br.com.fiap.safecoleta.config.security`.

## Testando a Aplicação

Você pode testar a aplicação usando ferramentas como Postman ou qualquer cliente HTTP de sua preferência. Para facilitar, um arquivo de coleção do Postman (`SafeColeta.postman_collection.json`) está incluído no projeto.

## Contribuindo

Contribuições são bem-vindas! Sinta-se à vontade para abrir issues e enviar pull requests.
