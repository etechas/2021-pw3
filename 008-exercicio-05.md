# EXERCÍCIO 5


## CODIFICAÇÃO DE MÉTODO POST

1 - Altere a classe `FormaPagamentoController` dentro do pacote _controller_, criando um método para adicionar uma forma de pagamento na base de dados através da requisição:
> POST /formas-pagamento 
> json: {
> 			"nome": "Visa",
> 			"tipo": "CARTAO_CREDITO"
> 			"dataFimVigencia": null
>       }

2 - Faça o teste através da ferramenta Postman.

### Resoluções

> **Item 1: Inserir forma de pagamento**

```java
@PostMapping
public FormaPagamento adicionar(@RequestBody FormaPagamento formaPagamento) {
    return formaPagamentoRepository.save(formaPagamento);
}
```
