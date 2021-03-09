# ATIVIDADE AVALIATIVA (PARTE 1)

Um estacionamento deseja automatizar a cobrança de mensalistas. Para isso decidiu simplificar a forma de calcular o valor devido pelo seu cliente. A quantia a ser paga pelos seus usuários depende do número de entradas que o veículo realiza no estacionamento. A cada entrada, a placa do veículo é registrada. Ao final do mês, conta-se o número de entradas que o veículo realizou e faz-se o seguinte cálculo:

- Se o motorista realizou até 20 entradas, ele deve pagar R$ 10,00 por entrada realizada.
- Da vigésima primeira entrada em diante, cada entrada custa R$ 7,50 ao cliente.

Agora, você ajudará na automatização da cobrança construindo uma aplicação Spring Boot para o projeto com a configuração:


**Dados do projeto**
- `Project:` Maven Project
- `Language:` Java
- `Spring Boot:` versão padrão


**Project Metadata**
- `Group:` br.com.`<seu-nome>`
- `Artifact:` aval-estacionamento
- `Name:` aval-estacionamento
- `Description:` deixe em branco
- `Package Name:` br.com.`<seu-nome>`.estacionamento
- `Packaging:` Jar
- `Java Version:` 8 ou 11 (depende da instalação)


**Dependencies:**
- Web
- Lombok
- JPA
- PostgreSQL Driver


### TAREFA
1. Criar o banco de dados postgresql com a tabela para armazenar a placa, a entrada e a saída do veículo. **Obs.:** configure o `application.properties` com as informações do banco de dados.
2. Criar a entidade que representa a tabela no banco de dados no pacote br.com.<seu-nome>.model
3. Criar a classe de acesso a dados (repository) no pacote br.com.<seu-nome>.repository

**Obs.:** Fazer upload do arquivo de script de criação da tabela com nome de `aval_<seu-nome>`, da entidade e do repositório.

