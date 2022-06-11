## INTRODUÇÃO

Este projeto tem a finalidade de demonstrar o processo de criação de um banco de dados, iniciando pela Análise de Requisitos e passando
pela criação dos modelos Conceitual, Lógico e Físico.

Os assuntos abordados neste projeto serão sobre uma livraria que vende apenas livros físicos, mas pelo fato de ser um projeto contínuo e pensado
no mundo real, naturalmente a livraria passará por mudanças e melhorias, como qualquer empresa. A ideia é que com o tempo seja criado um
Café anexo e que essa mudança tenha impacto direto no banco de dados já criado e em funcionamento da livraria.

<hr size="100"> <!-- LINHA HORIZONTAL -->

## ANÁLISE DE REQUISITOS

A primeira e mais importante etapa para a criação de um banco de dados é a Análise de Requisitos. Esta análise consiste no aprofundamento
e conhecimento sobre a regra de negócio da empresa, ou seja, nesta etapa são realizadas entrevistas e imersões acerca da empresa para compreender
o que ela faz, os tipos de clientes que ela possui, o ramo que atua, sua história, características e tudo que for importante para a criação
de um banco de dados consistente.

Neste projeto faremos a criação de uma livraria, então alguns termos como **Clientes**, **Editoras**, **Estoque**, **Categoria**, **Autores**, **ISBN-10** 
e **ISBN-13** precisam ser entendidos. 
Aliás, sabia que ISBN significa International Standard Book Number (Número Padrão Internacional de Livros)?
Este termo nada mais é que o ID de um livro e outras publicações segundo o autor, país, editora e número de edição. Até 2007 eram usados dez
caracteres (ISBN-10), mas foi necessário a criação do ISBN-13, com treze caracteres, devido ao grande volume de publicações em todo o mundo,
neste caso com a característica de ter o prefixo 978.

Esta livraria será uma empresa de pequeno porte, mesmo assim será bem organizada, então ela terá os seguintes setores:

- **Almoxarifado**: controle do estoque e solicitação de compra de livros;
- **Financeiro**: recebimento das Notas Fiscais Eletrônicas de compras, pagamentos dos salários dos colaboradores e de contas gerais da empresa;
- **Vendas**: tirar dúvidas dos clientes e realizar o fechamento de pedidos nos caixas;

O que seriam dos setores sem os colaboradores, então serão necessários alguns profissionais:

- **Dois almoxarifes**;
- **Dois assistentes financeiros**;
- **Três vendedores**.

Agora a Universo dos Livros precisa fechar parcerias com boas editoras, mas por ser uma pequena livraria apenas o fornecedor **Read Book** será suficiente para garantir ótimos livros das editoras **Império** e **New Bark**.

Com toda a documentação pronta, organização dos setores, colaboradores e editoras, chegou o momento de documentar cada uma destas informações para melhor compreensão antes da criação do Modelo Conceitual.

<center>
  <img src="https://i.ibb.co/c34LdL2/Setores-An-lise-de-Requisitos.png" alt="Setores">
  <img src="https://i.ibb.co/JFZCLHJ/Colaboradores-An-lise-de-Requisitos.png" alt="Colaboradores">
  <img src="https://i.ibb.co/m4Q9S67/Editoras-An-lise-de-Requisitos.png" alt="Editoras">
</center>

Também foram definidos como serão registrados os **Livros**, **Departamento**, **Categorias**, **Autores**, **Clientes**, **Vendas** e **DANFE's**.

<hr size="100"> <!-- LINHA HORIZONTAL -->

<!-- BOX DE CÓDIGOS -->

<!-- 
```markdown 
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```
--> 


