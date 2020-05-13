# Thymeleaf Tags

### Estrutura de repetição
#### Uma estrutura que você provavelmente fará muito uso durante a criação de seus templates para exibir listas, para isso, iremos introduzir um novo sistema, o sistema de Models.
#### Crie uma package _models_, que será responsavel por agrupar nossos models, usaremos como exemplo aqui a classe Pessoa, ela possuira dois simples atributos, nome e idade, aproveite também para gerar um construtor com os atributos e seus getters e setters.
#### Após a criação do nosso primeiro model, retorne para o controller e crie o metodo _helloLista_ com um mapping para _/lista_ já adicionando o atributo _Model_ e o retorno para a nossa view _helloworld_.
```java
@GetMapping("/lista")
public String helloLista(Model model) {

    return "helloworld";
}
```

#### Com a nossa primeira model pronta, e o esqueleto do nosso metodo no controller, iremos criar algumas pessoas, sinta-se livre para colocar um nome e idade de preferencia e após isso, adicione-as a uma lista e adicione o atributo lista ao view.
```java
@GetMapping("/lista")
public String helloLista(Model model) {
		
	Pessoa pessoa1 = new Pessoa("Matheus", 19);
	Pessoa pessoa2 = new Pessoa("Carlos", 20);
	Pessoa pessoa3 = new Pessoa("Eduardo", 40);
		
	List<Pessoa> pessoas = new ArrayList<Pessoa>();
	pessoas.add(pessoa1);
	pessoas.add(pessoa2);
	pessoas.add(pessoa3);
	
	model.addAttribute("lista", pessoas);
	
	return "helloworld";
}
```
#### Com o nosso controller pronto, vamos ao template, para criar estruturas de repetição, usaremos a tag _th:each_, esta tag recebe o nome que será autilizado, um nome para trackear o index e o nome do atributo que foi passado pelo controller, em nosso caso:
```html
	<ul th:each="pessoa : ${lista}">
		<li th:text="'ola ' + ${pessoa.nome}"></li>
		<li th:text="'Voce possui ' + ${pessoa.idade} + ' anos'"></li>
	</ul>
```
* repare que em nosso caso fizemos uso de uma _ul_, sintase livre para fazer uso de outras estruturas
* repare também que, fazemos uso da _variavel.atributo_, dentro da tag de repetição você possui acesso a todos os atributos da classe que está sofrendo iteração

### Condicionais
#### Dentro das condicionais do thymeleaf temos acesso a diversas estruturas, como _if_ - _unles_, elvis operator e _switch_ - _case_
```html
<!-- Exemplo com if - unless -->
<ul th:each="pessoa : ${lista}">
	<li th:text="'ola ' + ${pessoa.nome}"></li>
	<li th:if="${pessoa.idade > 18}">Maior de idade</li>
	<li th:unless="${pessoa.idade > 18}">Menor de idade</li>
</ul>

<!-- Exemplo com elvis operator -->
<ul th:each="pessoa : ${lista}">
	<li th:text="${pessoa.nome == 'Carlos'} ? 'Olá Carlos' : 'Tu num é o Carlos'"></li>
</ul>
```

> www.baeldung.com/spring-thymeleaf-conditionals   _link externo para referencia_

[Proximo Topico](#)