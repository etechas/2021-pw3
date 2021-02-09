# EXERCÍCIO 1


## BANCO DE DADOS

1 - Pelo navegador, abra `https://www.elephantsql.com/` e entre com seu usuário e senha.

2 - Clique no botão `+ Create New Instance`.

3 - Defina o nome `etec-restaurante`, o plano `Tyne Turtle (Free)` e a região `Northern Virginia`.

4 - Após a conclusão da criação, clique na instância `etec-restaurante` criada.

5 - Execute o script abaixo para criação das tabelas no item `BROWSER`.

```properties
CREATE TABLE TBL_TIPO_COZINHA (
	ID_TIPO_COZINHA SERIAL PRIMARY KEY,
	TX_NOME VARCHAR(100) NOT NULL,
	DT_FIM_VIGENCIA TIMESTAMP
);

INSERT INTO TBL_TIPO_COZINHA (TX_NOME) VALUES ('Mineira');
INSERT INTO TBL_TIPO_COZINHA (TX_NOME) VALUES ('Baiana');
INSERT INTO TBL_TIPO_COZINHA (TX_NOME) VALUES ('Lanches');
INSERT INTO TBL_TIPO_COZINHA (TX_NOME) VALUES ('Variada');
INSERT INTO TBL_TIPO_COZINHA (TX_NOME) VALUES ('Hambúrger');
INSERT INTO TBL_TIPO_COZINHA (TX_NOME) VALUES ('Árabe');
INSERT INTO TBL_TIPO_COZINHA (TX_NOME) VALUES ('Italiana');

CREATE TABLE TBL_FORMA_PAGAMENTO (
	ID_FORMA_PAGAMENTO SERIAL PRIMARY KEY,
	TX_NOME VARCHAR(100) NOT NULL,
	TX_TIPO VARCHAR(20),
	DT_FIM_VIGENCIA TIMESTAMP
);

INSERT INTO TBL_FORMA_PAGAMENTO (TX_NOME, TX_TIPO) VALUES ('Amex', 'CARTAO_CREDITO');
INSERT INTO TBL_FORMA_PAGAMENTO (TX_NOME, TX_TIPO) VALUES ('Alelo', 'VALE_REFEICAO');
INSERT INTO TBL_FORMA_PAGAMENTO (TX_NOME, TX_TIPO) VALUES ('Ticket Restaurante', 'VALE_REFEICAO');
INSERT INTO TBL_FORMA_PAGAMENTO (TX_NOME, TX_TIPO) VALUES ('MasterCard Maestro', 'CARTAO_DEBITO');
INSERT INTO TBL_FORMA_PAGAMENTO (TX_NOME, TX_TIPO) VALUES ('Visa Débito', 'CARTAO_DEBITO');
```

## CRIAÇÃO DO PROJETO SPRING

1 - Pelo navegador, abra `https://start.spring.io/`. 

2 - Defina as informações do projeto:
- __Project:__ Maven Project
- __Language:__ Java. 
- __Spring Boot:__ versão padrão. 
	
3 - No trecho de _Project Metadata_, defina:
- __Group:__ br.com.etechoracio
- __Artifact:__ etec-food
- __Name:__ etec-food
- __Description:__ deixe em branco 
- __Package Name:__ br.com.etechoracio.efood
- __Packaging:__ Jar
- __Java Version:__ 11

4 - Em _Dependencies_, adicione:
- Web
- Lombok
- JPA
- PostgreSQL Driver

5 - Clique em `Generate Project`.

6 - Extraia o `etec-food.zip` para uma pasta de sua preferência.

8 - Faça a importação do projeto no Eclipse através do menu _File -> Import -> Existing Maven Projects_.

7 - No arquivo `src/main/resources/application.properties`, defina as configurações do banco de dados e da JPA.

```properties
#DATASOURCE CONFIGS
spring.datasource.url=jdbc:postgresql://SERVER_DO_SEU_ELEPHANT:5432/USER_DO_SEU_ELEPHANT
spring.datasource.username=USER_DO_SEU_ELEPHANT
spring.datasource.password=PASSWORD_DO_SEU_ELEPHANT

#JPA CONFIGS
spring.jpa.hibernate.ddl-auto=validate
spring.jpa.show-sql=true
```

8 - Salve o arquivo.