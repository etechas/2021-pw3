# EXERCÍCIO 4


## CODIFICAÇÃO DE CONTROLLER

1 - Crie a classe `FormaPagamentoController` dentro do pacote _controller_. É necessário indicar que a classe é um controller e receberá as requisições HTTP, anotando-a com `@RestController`.

2 - As requisições HTTP absorvidas por essa classe serão feitas no recurso `formas-pagamento`. Assim, anote a classe, também, com a anotação `@RequestMapping`.

3 - Faça a injeção de dependência do objeto da classe `FormaPagamentoRepository` através da anotação `@Autowired`.

4 - Crie um método para listar todas as formas de pagamento através da requisição GET.

5 - Crie um método para exibir a forma de pagamento por ID através da requisição GET.

6 - Faça os testes através da ferramenta Postman.

### Resoluções

> **Item 1 e 2: FormaPagamentoController**

```java
@RestController
@RequestMapping("formas-pagamento")
public class FormaPagamentoController {

}
```

> **Item 3: Injeção de dependência**

```java
@Autowired
private FormaPagamentoRepository formaPagamentoRepository;
```

> **Item 4: Listar todas as formas de pagamento**

```java
@GetMapping
public List<FormaPagamento> listar() {
    return formaPagamentoRepository.findAll();
}
```

> **Item 5: Buscar forma de pagamento por id**

```java
@GetMapping("/{id}")
public FormaPagamento buscarPorId(@PathVariable Integer id) {
	Optional<FormaPagamento> resultado = repository.findById(id);
	return resultado.orElse(null);
}	
```