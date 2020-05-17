# Repository

#### O padrão de repository foi criado para substituir o padrão de DAO(Data acess object), repositories assim como seu antecessor DAO são responsaveis por agrupar nossas logicas de acesso ao banco de dados, mas ao contrario do padrão DAO o padrão de repository adiciona uma camada de abstração sobre tudo isso.

#### Para começar com o padrão de repository crie uma package repositories, dentro dela crie as interfaces _EstoqueRepository_ e o _ProdutoRepository_, dentro dessas interfaces de um extends _JpaRepository<T, ID>_, exemplo _EstoqueRepository_
```java
public interface EstoqueRepository extends JpaRepository<Estoque, Long> { }
```
#### Como podemos ver, no lugar de _T_ é colocada a classe do repository, e em _ID_ colocamos o tipo primitivo com que o _ID_ foi criado.

#### Por padrão o _JpaRepository_ nos traz todos os metodos que precisamos para criar um crud basico, mas também dentro dela podemos criar nossas proprias queries, recomendo ler [este conteudo](https://spring.io/projects/spring-data) caso queira saber mais sobre o spring data.

[Proximo Topico](../4-Projeto/listagem-estoque.md)