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

Esta livraria será uma empresa de pequeno porte, então ela terá os seguintes setores:

- **Almoxarifado**: controle do estoque e solicitação de compra de livros;
- **Financeiro**: recebimento das Notas Fiscais Eletrônicas de compras, pagamentos dos salários dos colaboradores e de contas gerais da empresa;
- **Vendas**: tirar dúvidas dos clientes e realizar o fechamento de pedidos nos caixas;

Para estes setores serão necessários os seguintes profissionais:

- **Dois almoxarifes**;
- **Dois assistentes financeiros**;
- **Três vendedores**.

Por ser uma pequena livraria apenas um fornecedor será suficiente, garantindo livros das editoras **Império** e **New Bark**.

Entendo a regra de negócio de uma livraria de pequeno porte e a necessidade do cliente, foram documentados as informações necessárias, detalhadas abaixo:

**- LIVROS:**
  - Identificação do Livro, Nome, Editora, Autor, Edição, Categoria, Resumo, Idiomas, Data da Publicação, Número de Páginas, Dimensões, ISBN-10, ISBN-13, Quantidade, Tipo da Capa, Quantidade em Estoque, Preço e Código de Barras.

**- EDITORAS:**
  - Identificação da Editora, Razão Social, Nome Fantasia, CNPJ, Inscrição Estadual, Endereço, Bairro, Cidade, E-mail, Dados Bancários e Identificação do Livro.

**- AUTORES:**
  - Identificação do Autor, Nome, Registro, Sexo, País, Data de Nascimento, Identificação do Livro e Identificação da Editora.

**- CATEGORIAS:**
  - Identificação da Categoria, Categoria e Eidentificação do Livro.

**- COLABORADORES:**
  - Identificação do Colaborador, Nome, Cargo, Sexo, Endereço, Bairro, Cidade, Data de Nascimento, Data de Admissão, Salário e Observação.

**- SETORES:**
  - Identificação do Setor, Nome do Setor, Quantidade de Caloboradores e Identificação do Colaborador.

**- CLIENTES:**
  - Identificação do Cliente, Nome, CPF, Endereço, Bairro, Cidade, Data de Nascimento e E-mail.

**- DANFE:**
  - Identificação da DANFE, Número NFe, Série NFe, Data de Emissão, Valor Total, ChaveEletrônica, Protocolo de Autorização e Identificação do Livro.

**- VENDAS:**
  - Identificação da Venda, Data da Venda, Valor Total, Quantidade de Livros, Identificação do Livro, Identificação da DANFE, Identificação do Colaborador e Identificação do Cliente.

Com estas informações em mãos, o próximo passo é a criação do Modelo Conceitual.

<hr size="100"> <!-- LINHA HORIZONTAL -->

## MODELO CONCEITUAL

O Modelo Conceitual é baseado no Modelo Entidade-Relacionamento. É a fase onde são definidos as entidades, atributos das entidadades e como cada uma se relaciona.
A criação deste modelo serve para modelar e criar os bancos de dados relacionais no sentido lógico e de negócio, primordial para elucidar o entendimento da regra de negócio e a criação do banco de dados.

Abaixo o Modelo Entidade-Relacionamento:

<img src="https://i.ibb.co/sm6KsKg/Modelo-Conceitual.jpg">

<hr size="100"> <!-- LINHA HORIZONTAL -->

## MODELO LÓGICO

**_Atualizado em 26/07/2022_**

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


