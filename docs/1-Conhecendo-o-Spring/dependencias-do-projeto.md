# Dependencias do Projeto
No futuro iremos fazer uso de varias dependencias, mas inicialmente vamos fazer uso de duas, são elas:
* Spring Web
* Thymeleaf
## Um pouco sobre as dependencias escolhidas

### Spring Web
Esta dependencia nos proporciona tudo relacionado ao framework spring MVC e a arquitetura REST, além de um container do tomcat (_por padrão, nos dando ainda a escolha de troca_) todo configurado.

### Thymeleaf
Template engine para ssr, nos oferece uma vasta gama de tags para deixar nosso HTML top

### Dependencias no site
<p align="center">
    <img src="../../assets/initializr-dependencies.png" alt="initializr dependencies">
</p>
Após terminar de adicionar as dependencias pelo site, dê um generate, ele ira iniciar o download de um arquivo compactado, descompacte este arquivo e o coloque em uma pasta desejada, va até a sua IDE e importe este arquivo, caso esteja usando o eclipse por exemplo, importe ele como um projeto maven, após o import o maven deve iniciar o download das dependencias.

### Dependencias na IDE
<p align="center">
    <img src="../../assets/sts-dependencies.png" alt="sts dependencies">
</p>
Após terminar de adicionar as dependencias pela IDE, de um finish e o maven inicializará o download de suas dependencias.

[Proximo Tópico](../2-Iniciando-com-Spring/estrutura-inicial.md)