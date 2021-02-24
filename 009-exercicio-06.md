# EXERCÍCIO 6


## CODIFICAÇÃO DE MÉTODO PUT

1 - Altere a classe `FormaPagamentoController` dentro do pacote _controller_, criando um método para atualizar uma forma de pagamento via requisição:
> PUT /formas-pagamento/1
> json: {
> 			"id": 1
>     		"tipo": "CARTAO_CREDITO",
>     		"nome": "ETEC Card",
>     		"dataFimVigencia": null
> 	    }

2 - Faça o teste através da ferramenta Postman.

### Resoluções

> **Item 1: Alterar forma de pagamento**

```java
@PutMapping("/{id}")
public FormaPagamento atualizar(@PathVariable("id") Integer id,
                                @RequestBody FormaPagamento formaPagamento) {
    Optional<FormaPagamento> existe = formaPagamentoRepository.findById(id);
    if (existe.isEmpty()) {
        return null;
    }
	return formaPagamentoRepository.save(formaPagamento);
}
```
