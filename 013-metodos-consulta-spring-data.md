# Spring Data - Métodos de consulta

O Spring Data JPA oferece várias maneiras de criar uma consulta e vamos nos concentrar em como gerar uma consulta usando a estratégia de nome de método.

Na verdade, é muito simples: Spring Data analisa o nome do método com base em certos critérios e cria uma consulta. Veja como funciona:

```java
public interface AlunoRepository extends Repository<Aluno, Long> {

  List<Aluno> findByEmail(String email);
  
}

```

O Spring Data JPA cria uma consulta usando a API de critérios JPA a partir disso:

- `find` determina qual entidade deve ser retornada. Também pode ser `read`, `query` e `get`. Se fosse `count` retornaria o número de entidades.

- `By` indica ao analisador o início dos critérios reais.

- `Email` diz ao Spring Data que há uma propriedade chamada `email` na entidade (Aluno) que será usada como critério de pesquisa. Em outras palavras, haverá uma cláusula `where` nessa propriedade.

- `(String email)` indica o parâmetro que será recebido e usado como valor na cláusula `where`.

Essencialmente, isso se traduz na seguinte consulta: **SELECT a FROM Aluno a WHERE a.email =?1**.

## Critérios de pesquisa

A tabela a seguir descreve as palavras-chave suportadas para JPA e como um método contendo essa palavra-chave se traduz:

| Palavra-chave      | Exemplo                                  | Resultado                                 |
|--------------------|------------------------------------------|-------------------------------------------|
| Distinct           | findDistinctByNome                       | select distinct … where x.nome = ?1       |
| And                | findByNomeAndEmail                       | … where x.nome = ?1 and x.email = ?2      |
| Or                 | findByNomeOrEmail                        | … where x.nome = ?1 or x.email = ?2       |
| Is, Equals         | findByNome,findByNomeIs,findByNomeEquals | … where x.nome = ?1                       |
| Between            | findByDataCriacaoBetween                 | … where x.dataCriacao between ?1 and ?2   |
| LessThan           | findByIdadeLessThan                      | … where x.idade < ?1                      |
| LessThanEqual      | findByIdadeLessThanEqual                 | … where x.idade <= ?1                     |
| GreaterThan        | findByIdadeGreaterThan                   | … where x.idade > ?1                      |
| GreaterThanEqual   | findByIdadeGreaterThanEqual              | … where x.idade >= ?1                     |
| After              | findByDataCriacaoAfter                   | … where x.dataCriacao > ?1                |
| Before             | findByDataCriacaoBefore                  | … where x.dataCriacao < ?1                |
| IsNull, Null       | findByIdade(Is)Null                      | … where x.idade is null                   |
| IsNotNull, NotNull | findByIdade(Is)NotNull                   | … where x.idade not null                  |
| Like               | findByNomeLike                           | … where x.nome like ?1                    |
| NotLike            | findByNomeNotLike                        | … where x.nome not like ?1                |
| StartingWith       | findByNomeStartingWith                   | … where x.nome like ?1                    |
| EndingWith         | findByNomeEndingWith                     | … where x.nome like ?1                    |
| Containing         | findByNomeContaining                     | … where x.nome like ?1                    |
| OrderBy            | findByIdadeOrderByNomeDesc               | … where x.idade = ?1 order by x.nome desc |
| Not                | findByNomeNot                            | … where x.nome <> ?1                      |
| In                 | findByIdadeIn(List<Integer> idades)      | … where x.idade in ?1                     |
| NotIn              | findByIdadeNotIn(List<Integer> idades)   | … where x.idade not in ?1                 |
| True               | findByAtivoTrue()                        | … where x.ativo = true                    |
| False              | findByAtivoFalse()                       | … where x.ativo = false                   |
| IgnoreCase         | findByNomeIgnoreCase                     | … where UPPER(x.nome) = UPPER(?1)         |


> Embora o Spring Data JPA não imponha limite para quantas expressões podemos adicionar, nomes longos são ilegíveis e difíceis de manter. Podemos usar a anotação `@query` para o caso de consultas complexas.

