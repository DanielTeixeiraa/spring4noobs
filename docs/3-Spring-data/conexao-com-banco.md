# Conexao Spring data
#### Neste modulo iremos dar uma introdução ao spring data JPA, para começar a trabalhar com ele primeiro precisamos fazer a conexão com o banco.
#### Antes de tudo, vá ao seu _pom.xml_ e adicione a dependencia do spring data e o driver de conexão com o seu banco de dados
```xml
<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>

Caso queira utilizar mysql:
<dependency>
	<groupId>mysql</groupId>
	<artifactId>mysql-connector-java</artifactId>
	<scope>runtime</scope>
</dependency>

Caso queira utilizar postgresql
<dependency>
    <groupId>org.postgresql</groupId>
    <artifactId>postgresql</artifactId>
    <scope>rutime</scope>
</dependency>
```
> As dependencias devem ser colocadas dentro da tag _dependencies_
* Nossas dependencias até o momento:
```xml
<dependencies>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-jpa</artifactId>
    </dependency>
    <dependency>
        <groupId>mysql</groupId>
        <artifactId>mysql-connector-java</artifactId>
        <scope>runtime</scope>
    </dependency>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-thymeleaf</artifactId>
    </dependency>

    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>

    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-test</artifactId>
        <scope>test</scope>
        <exclusions>
            <exclusion>
                <groupId>org.junit.vintage</groupId>
                <artifactId>junit-vintage-engine</artifactId>
            </exclusion>
        </exclusions>
    </dependency>
</dependencies>
```
#### Para fazer a conexão teremos que dar o primeiro olá ao _application.properties_ o nosso arquivo de configurações.
#### Essas são as unicas diferenças entre conexão com mysql e postgresql
```
Mysql:
spring.datasource.driverClassName = com.mysql.cj.jdbc.Driver
spring.jpa.database-platform = org.hibernate.dialect.MySQL8Dialect
spring.datasource.url = jdbc:mysql://localhost:3306/heartconstrucoes?useTimezone=true&serverTimezone=UTC

Postgresql:
spring.datasource.driverClassName = org.postgresql.Driver
spring.jpa.hibernate.dialect = org.hibernate.dialect.PostgreSQLDialect
spring.datasource.url = jdbc:postgresql://localhost:5432/heartconstrucoes
```
#### Configurações gerais
```
spring.datasource.username = root
spring.datasource.password =
spring.jpa.show-sql = true
spring.jpa.hibernate.ddl-auto = update
```
#### Essas são as strings de conexão com o nosso banco de dados, elas se referem diretamente as classes necessarias para a conexão, mas como o spring nos oferece esse metodo para fazer a configuração, é um modo muito mais facil para nós

* Configurações especificas:
  * Os driver className: se refere ao driver de conexão com o banco que você deseja utilizar
  * database-plataform/dialect: se refere diretamente ao dialect utiliado para comunicação com seu banco
  * datasource.url: url de conexão com seu banco de dados, onde voce identifica a porta em que esta conectado seu banco de dados e o nome do seu banco, em nosso caso o heartconstrucoes

* Configurações gerais:
  * username: login no seu banco
  * password: senha, no meu caso meu banco esta sem uma senha
  * show-sql: caso voce deseja que ele mostre para voce a query em sql, no nosso caso estamos habilitando isso
  * ddl-auto: configuramos o que desejamos que o orm faça com nosso banco, temos as opções:
    * validate: ela ira validar o nosso schema de tabelas
    * update: ira atualizar caso seja necessario
    * create: ira criar o schema, deletando o atual
    * create-drop: ira criar o schema em tempo de execução e deletar após o termino da execução

[Proxima seção](./comecando-com-banco.md)