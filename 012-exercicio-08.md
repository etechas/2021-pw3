# EXERCÍCIO 8


## USANDO RESPONSE-ENTITY

1 - Altere o método `buscarPorId()` da classe `FormaPagamentoController` para que retorne um objeto do tipo `ResponseEntity` através das seguintes condições:

- Retornar **204 - No Content** quando NÃO encontrar a forma de pagamento no banco de dados
- Retornar **200 - Ok** com o conteúdo encontrado


2 - Altere o método `atualizar()` da classe `FormaPagamentoController` para que retorne um objeto do tipo `ResponseEntity` através das seguintes condições:

- Retornar **204 - No Content** quando NÃO encontrar a forma de pagamento no banco de dados
- Retornar **200 - Ok** com o conteúdo atualizado


3 - Altere o método `excluir()` da classe `FormaPagamentoController` para que retorne um objeto do tipo `ResponseEntity` através das seguintes condições:

- Retornar **204 - No Content** quando NÃO encontrar a forma de pagamento no banco de dados
- Retornar **200 - Ok** sem conteúdo


### Resoluções

> **Item 1: `buscarPorId()` com `ResponseEntity`**

```java
@GetMapping("/{id}")
public ResponseEntity<FormaPagamento> buscarPorId(@PathVariable Integer id) {
	Optional<FormaPagamento> resultado = formaPagamentoRepository.findById(id);
    if (resultado.isEmpty()) {
        return ResponseEntity.noContent().build();
    }
	return ResponseEntity.ok(resultado.get());
}	
```

> **Item 2: `atualizar()` com `ResponseEntity`**

```java
@PutMapping("/{id}")
public ResponseEntity<FormaPagamento> atualizar(@PathVariable("id") Integer id,
                                                @RequestBody FormaPagamento formaPagamento) {
    Optional<FormaPagamento> existe = formaPagamentoRepository.findById(id);
    if (existe.isEmpty()) {
        return ResponseEntity.noContent().build();
    }
	FormaPagamento atualizado = formaPagamentoRepository.save(formaPagamento);
    return ResponseEntity.ok(atualizado);
}
```

> **Item 3: `excluir()` com `ResponseEntity`**

```java
@DeleteMapping("/{id}")
public ResponseEntity<?> excluir(@PathVariable("id") Integer id) {
    Optional<FormaPagamento> existe = formaPagamentoRepository.findById(id);
    if (existe.isEmpty()) {
        return ResponseEntity.noContent().build();
    }
	
    FormaPagamento update = existe.get();
    update.setDataFimVigencia(LocalDateTime.now());
    formaPagamentoRepository.save(update);
	
    return ResponseEntity.ok().build();
}
```
