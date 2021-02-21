# Revisão de Java Persistence API

## Java Database Connectivity (JDBC)

No fim dos anos 90, com a popularização do Java em ambientes corporativos, foi criada uma API para fazer a interface do código Java com um SGBD (Sistema Gerenciador de Banco de Dados) chamada de JDBC (Java Database Connectivity).

> No JDBC, o acesso ao banco de dados é feito através de comandos (Statements) escritos na linguagem SQL (Structured Query Language).

## Object-Relational Mapping (ORM)

Criar uma aplicação Java usando JDBC diretamente é bem trabalhoso, pois escrevemos bastante SQL. Além disso, a programação orientada a objetos difere muito do esquema relacional dos bancos de dados tradicionais e a todo momento "transformamos" objetos em registros e registros em objetos.

Com isso em mente, alguns anos atrás, desenvolvedores começaram a criar algo que agilizasse esse trabalho: as tecnologias de mapeamento objeto-relacional, conhecidas por ORM (Object-Relational Mapping).

> O ORM estabelece uma “ponte” entre o modelo orientado a objetos, utilizado no Java, e o modelo relacional, utilizado pela maioria dos SGBDs, ou seja, representa as tabelas de um banco de dados relacional através de classes.

## Framework Hibernate

O Hibernate é um framework objeto-relacional mais utilizado em projetos Java, sendo uma das primeiras opções a implementar o conceito de ORM e, em pouco tempo, se tornou referência entre os desenvolvedores, tendo influenciado, inclusive, a criação da especificação JPA.

> O Hibernate gera, em tempo de execução, o SQL necessário para interagir com o banco de dados e podemos trocar o banco de dados utilizado sem ter que alterar o código-fonte.

## Java Persistence API (JPA)

Antigamente, existiam diversos frameworks e bibliotecas que abstraiam os desafios da persistência com ORM em Java. Porém, cada um fazia isso de uma maneira diferente, ocasionando um grande problema caso fosse necessário migrar para outra tecnologia.

Com intuito de padronizar as implementações de ORM em Java, foi elaborada a especificação oficial Java Persistence API (JPA) que descreve como os frameworks ORM devem ser implementados.

> O grande motivo por trás da especificação JPA é que podemos trocar de implementação na aplicação sem que precisemos mudar o código-fonte.

## JPA x Hibernate

A JPA é uma especificação, isto é, não possui código que possa ser executado, mas precisa que alguém a implemente. O Hibernate é a implementação JPA, quem dá vida para a especificação e que pode ser executado em nossa aplicação.

> Hibernate é o código que podemos executar, o que chamamos de framework.

Resumindo, para persistir dados com JPA é preciso escolher uma implementação (Hibernate??) que é quem, de fato, vai fazer todo o trabalho.

## Mapeamento Básico

A seguir, veremos as principais anotações Java de mapeamento do JPA. Essas anotações estão no pacote `javax.persistence`.

- **@Entity:** anotação que indica que a classe é uma entidade, que representa uma tabela do banco de dados.

- **@Table:** serve para indicar o nome da tabela na base de dados.

- **@Id:** usada para declarar o campo que representa a chave primária na tabela do banco de dados.

- **@GeneratedValue:** especifica que um valor será gerado automaticamente para o atributo.

- **@Column:** especifica que a propriedade da classe representa uma coluna na tabela do banco de dados.
