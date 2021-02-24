# EXERCÍCIO 7


## CODIFICAÇÃO DE MÉTODO DELETE

1 - Altere a classe `FormaPagamentoController` dentro do pacote _controller_, criando um método para excluir, de forma lógica (colocando data fim de vigência), uma forma de pagamento via requisição:
> DELETE /formas-pagamento/1

2 - Faça o teste através da ferramenta Postman.

### Resoluções

> **Item 1: Excluir logicamente uma forma de pagamento**

```java
@DeleteMapping("/{id}")
public void excluir(@PathVariable("id") Integer id) {
    Optional<FormaPagamento> existe = formaPagamentoRepository.findById(id);
    if (existe.isEmpty()) {
        return;
    }
	
    FormaPagamento update = existe.get();
    update.setDataFimVigencia(LocalDateTime.now());
    formaPagamentoRepository.save(update);
}
```
