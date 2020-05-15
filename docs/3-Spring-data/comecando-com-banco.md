# Começando com Banco de Dados

#### Agora que estamos com a conexão feita vamos aos nossos models para fazer o mapeamento das entidades, entidades são nossas classes, no caso, como elas serão mapeadas para as tabelas em nosso banco de dados.

#### Então em nossa classe Produto iremos criar um novo atributo, o id.

#### id sera o nosso identificador dentro do banco de dados, a chave primaria dos nossos produtos, como o id sera gerado automaticamente com o metodo de auto increment quando mandarmos um novo produto para o banco não sera necessario adicionalo ao construtor.
```java
@Setter
@Getter
@NoArgsConstructor
public class Produto {
    
    private Long id;

    private String nome;

    private Double preco;

    public Produto(String nome, Double preco) {
		this.nome = nome;
		this.preco = preco;
	}
}
```

## Mapeamento de Entidade
```java
@Setter
@Getter
@NoArgsConstructor
@Entity()
public class Produto {

	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	private Long id;

	@Column(unique = true)
	private String nome;

	@Column()
	private Double preco;

	public Produto(String nome, Double preco) {
		this.nome = nome;
		this.preco = preco;
	}

}
```
* Entity: Indica para o spring que sua classe será uma tabela do seu banco, podendo receber um atributo name, caso você queira um outro nome para sua tabela.

* Id: Identifica este atributo como o _primary key_ da sua tabela.
* GeneratedValue: Auto increment da sua _primary key_, podendo receber diferentes estrategias para auto increment.

* Column: Identifica este atributo como uma coluna de sua tabela, pode receber diversos atributos para configurar estes campos, nos permitindo ajustar este campos como ajustariamos criando a tabela na mão.

#### Alem da criação do model _Produto_ criaremos o model _Estoque_:
```java
@Getter
@Setter
@NoArgsConstructor
@Entity()
public class Estoque {

	@Id
	private Long id;

	@OneToOne()
    @MapsId
	private Produto produto;

	@Column()
	private Long quantia;

	public Estoque(Produto produto, Long quantia) {
		this.produto = produto;
		this.quantia = quantia;
	}

}
```
#### Aqui podemos perceber a adição de uma nova annotation, _@OneToOne()_, esta faz parte das annotations de relacionamento.
#### No spring data possuimos annotations para todos os relacionamentos entre tabela: _OneToOne_, _OneToMany_, _ManyToOne_, _ManyToMany_, entre outros não muito utilizados.

#### Reparem também que aqui não possuimos um _GeneratedType_ pois nosso Id será o Id do produto, declaramos isso através do _@MapsId_ no atributo produto, uma melhor forma de fazer um mapeamento _OneToOne_.

[Proxima seção](#)