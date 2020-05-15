## _Aproveite para deletar os exemplos anteriores, pois a partir de agora iremos codar diretamente coisas relacionadas ao nosso projeto _Heart Construções_._

# Project Lombok

#### Primeiramente, faça import da dependencia:
```xml
<dependency>
	<groupId>org.projectlombok</groupId>
	<artifactId>lombok</artifactId>
</dependency>
```
> Caso esteja fazendo uso da nossa IDE STS, basta clicar com o botão direito sobre o seu projeto ir em _Spring -> Edit Starters_ selecionar a dependencia e dar um ok.

#### A biblioteca lombok é uma biblioteca muito util quando se trata de codigo limpo e legivel.

#### Está biblioteca transforma dezenas de linhas de codigo em simples annotations, como veremos no exemplo a seguir.

#### Começaremos com uma simples classe Produto, com dois campos, nome, preco e um construtor para estes campos

```java
public class Produto {

    private String nome;

    private Double preco;

    public Produto(String nome, Double preco) {
		this.nome = nome;
		this.preco = preco;
	}
}
```

#### Agora você me pergunta, cade os getters e os setters? Então, é aqui que entra a lib, iremos  fazer uso das annotations _@Setter_, _@Getter_ e _@NoArgsConstructor_

```java
@Setter
@Getter
@NoArgsConstructor
public class Produto {

    private String nome;

    private Double preco;

    public Produto(String nome, Double preco) {
		this.nome = nome;
		this.preco = preco;
	}
}
```
#### Um pouco sobre estas annotations:
* Setter: Cria em tempo de compilação setters para todos os atributos da classe
  * Podemos também fazer uso dela internamente, anotando individualmente para cada atributo a annotation, aqui usamos sobre a classe pois queremos setters para todos.
* Getters: Tem a mesma função da Setter, mas para os getters.
* NoArgsConstructor: Cria um construtor sem argumentos para a classe.

#### Essas serão as annotations que faremos uso aqui, para saber mais de uma olhada na documentação [Project Lombok](https://projectlombok.org/features/all).

[Proximo Topico](../3-Spring-data/conexao-com-banco.md)