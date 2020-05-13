# Thymeleaf e Model

### Bindando um model a view
#### Para conseguirmos usar conteudos de classes, variaveis etc java dentro do html, precisando bindar este conteudo a view, para isso fazemos uso da interface _Model_, declarando ela nos parametros do nosso metodo _hello()_, ficando _hello(Model model)_, e para atrelar um conteudo ao nosso model, fazendo _model.addAttribute("foo", bar);_ 
* foo: o nome da variavel terá dentro do seu html.
* bar: o nome da variavel que você deseja enviar ao html.

#### Hello ${name}
#### Para o HTML nos dar um olá, faremos uso da annotation _@RequestParam_, essa annotation nos permite pegar os dados como pegariamos de um form, passaremos como parametros dessa annotation o identificador no URL, se é obrigatorio passar, e caso não passemos, qual o valor default dela, ficando desta forma nosso codigo:
```java
@Controller
@RequestMapping("/hello")
public class HelloController {

	@GetMapping()
	public String hello(@RequestParam(name = "name", required = false, defaultValue = "World!") String name, Model model) {
		model.addAttribute("name", name);
		
		return "helloworld";
	}
	
}
```
* _reparem que essa annotation ao contrario das outras é declarada dentro dos nossos parametros, faremos uso de outras annotations desta forma futuramente_
* _reparem também que atribuimos o conteudo que receberemos do RequestParam há String name, e é ela quem passamos ao model_

### Fazendo uso do Thymeleaf
```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
<title>Hello World!</title>
</head>
<body>
	<p th:text="'Hello ' + ${name}"/>
</body>
</html>
```
#### Esta deve ser a estrutura da nossa pagina final, mas agora, vamos a explicação

* Repare na declaração dentro da tag html, esta é a forma com que habilitamos o uso da template engine thymeleaf

* Repare também no conteudo dentro da tag _p_, _th:_ é o prefixo que declara um atributo do thymeleaf, _text_ é a tag thymeleaf que estaremos usando, passamos para esta tag o conteudo que desejamos apresentar e concatenamos com este conteudo a String _name_ que passamos pelo controller.

#### Iniciando o projeto e indo até _localhost:8080/hello?name=paint_, no final de contas resultara na simples tag
```html
<p>Hello paint</p>
```
#### E ainda, se formos até _localhost:8080/hello_ será bindado o valor default que definimos no controller, resultando em
```html
<p>Hello World!</p>
```

[Proxima seção](./thymeleaf-tags.md)