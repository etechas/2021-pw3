# EXERCÍCIO 3


## CODIFICAÇÃO DE CLASSES

1 - Abra o projeto **etec-food**.

2 - Crie a classe `TipoCozinha` dentro do pacote _model_ com os atributos id, nome e dataFimVigencia.

3 - Faça o mapeamento com as anotações JPA (_javax.persistence_) como `@Entity`, `@Table`, `@Id`, `@Column`, etc, conforme informações da tabela abaixo:
```properties
CREATE TABLE TBL_TIPO_COZINHA (
	ID_TIPO_COZINHA SERIAL PRIMARY KEY,
	TX_NOME VARCHAR(100) NOT NULL,
	DT_FIM_VIGENCIA TIMESTAMP
);
```

4 - Anote a classe também com as anotações `@Getter` e `@Setter`.

5 - Identar a classe com `Ctrl` + `Shift` + `F` e salvar (`Ctrl` + `S`).

6 - Crie a interface `TipoCozinhaRepository` dentro do pacote _repository_ herdando (extends) de `JPARepository`.

7 - Executar a classe **EtecFoodApplication** para validar o mapeamento.

### Resoluções

> **Item 2 a 5: TipoCozinha**
>

```java
@Getter
@Setter
@Entity
@Table(name = "TBL_TIPO_COZINHA")
public class TipoCozinha {

	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	@Column(name = "ID_TIPO_COZINHA")
	private Integer id;

	@Column(name = "TX_NOME")
	private String nome;

	@Column(name = "DT_FIM_VIGENCIA")
	private LocalDateTime dataFimVigencia;

}
```


> **Item 6: TipoCozinhaRepository**
>

```java
public interface TipoCozinhaRepository extends JpaRepository<TipoCozinha, Integer> {

}
```
