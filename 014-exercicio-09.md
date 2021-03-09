# EXERCÍCIO 9


## USANDO MÉTODOS DE CONSULTA 

1 - Crie um método na classe `FormaPagamentoRepository` que retorne uma lista de objetos do tipo `FormaPagamento` ativos no banco de dados, isto é, que **NÃO** possuam data fim de vigência preenchida.

2 - Altere o método `listarTodos()` da classe `FormaPagamentoController` para que use o método criado no item 1.

3 - Altere a classe `TipoCozinhaRepository` criando um método que retorne uma lista de objetos do tipo `TipoCozinha` ativos no banco de dados e ordenados por nome.

4 - Altere a classe `TipoCozinhaController` para que use o método criado no item 3.

### Resoluções

> **Item 1: método para buscar ativos**

```java
public interface FormaPagamentoRepository extends Repository<FormaPagamento, Long> {

  List<FormaPagamento> findByDataFimVigenciaIsNull();
  
}
```

> **Item 2: `listarTodos()` com método para buscar ativos**

```java
@GetMapping
public List<FormaPagamento> listarTodos() {
	return formaPagamentoRepository.findByDataFimVigenciaIsNull();
}
```

> **Item 3: método para buscar ativos ordenados por nome**

```java
public interface TipoCozinhaRepository extends Repository<TipoCozinha, Long> {

  List<TipoCozinha> findByDataFimVigenciaOrderByNome();
  
}
```

> **Item 4: `listarTodos()` com método para buscar ativos ordenados por nome**

```java
@GetMapping
public List<TipoCozinha> listarTodos() {
	return tipoCozinhaRepository.findByDataFimVigenciaOrderByNome();
}
```
