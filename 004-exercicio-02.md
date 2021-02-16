# EXERCÍCIO 2


## CODIFICAÇÃO DE CLASSES

1 - Crie os pacotes abaixo dentro da pasta src:
- br.com.etechoracio.efood.model
- br.com.etechoracio.efood.repository
- br.com.etechoracio.efood.controller
- br.com.etechoracio.efood.enums

2 - Crie a enumeração `TipoFormaPagamentoEnum` dentro do pacote _enums_ com os valores _CARTAO_CREDITO, CARTAO_DEBITO e VALE_REFEICAO_.

3 - Crie a classe `FormaPagamento` dentro do pacote _model_ os atributos id, tipo, nome e dataFimVigencia.

4 - Faça o mapeamento com as anotações JPA (_javax.persistence_) como `@Entity`, `@Table`, `@Id`, `@Column`, etc.

5 - Anote a classe também com as anotações `@Getter` e `@Setter`.

6 - Identar a classe com `Ctrl` + `Shift` + `F` e salvar (`Ctrl` + `S`).

7 - Crie a interface `FormaPagamentoRepository` dentro do pacote _repository_ herdando (extends) de `JPARepository`.


### Resoluções

> **Item 2: TipoFormaPagamentoEnum**
>

```java
public enum  TipoFormaPagamentoEnum {

    CARTAO_CREDITO,
    CARTAO_DEBITO,
    VALE_REFEICAO;

}
```

> **Item 3 a 6: FormaPagamento**
>

```java
@Getter
@Setter
@Entity
@Table(name = "TBL_FORMA_PAGAMENTO")
public class FormaPagamento {

	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	@Column(name = "ID_FORMA_PAGAMENTO")
	private Integer id;

	@Enumerated(EnumType.STRING)
	@Column(name = "TX_TIPO")
	private TipoFormaPagamentoEnum tipo;

	@Column(name = "TX_NOME")
	private String nome;

	@Column(name = "DT_FIM_VIGENCIA")
	private LocalDateTime dataFimVigencia;

}
```


> **Item 7: FormaPagamentoRepository**
>

```java
public interface FormaPagamentoRepository extends JpaRepository<FormaPagamento, Integer> {

}
```
