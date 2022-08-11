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

Nesta etapa também são definidos as cardinalidades entre as tabelas, para acessar a documentação da cardinalidade clique [aqui](https://github.com/GabrielSQL2022/projeto-livraria/blob/main/Cardinalidade.pdf).

Abaixo o Modelo Entidade-Relacionamento:

![CONCEITUAL](https://i.ibb.co/92jn3Y7/Modelo-Conceitual.jpg)

<hr size="100"> <!-- LINHA HORIZONTAL -->

## MODELO LÓGICO

O Modelo Lógico tem o objetivo de representar as estruturas que irão armazenar os dados no Banco de Dados. Nesta etapa são definidos as entidades e atributos, bem como 
os registros, número de campos e seus respectivos tamanhos, além das Chaves Primárias e Chaves Estrangeiras.

No Modelo Lógico também é definido qual SGBD será utilizado, neste projeto utilizarei o PLSQL.

![LÓGICO](https://i.ibb.co/wJ5mFYP/Screenshot-1.jpg)

<hr size="100"> <!-- LINHA HORIZONTAL -->

## MODELO FÍSICO

O Modelo Físico consiste no design do banco de dados com base nos requisitos apurados durante a criação dos Modelo Lógico. Nesta etapa são representadas as tabelas, colunas, tipos de dados, visualizações, restrições, índices, procedimentos e outros procedimentos estruturais do banco de dados.

Também é definido o SGBD (Sistema de Gerenciamento de Banco de Dados) que será utilizado no projeto. Os SGBD's são os softwares responsáveis por administrar o banco de dados. 
Os mais utilizados atualmente são, respectivamente: Oracle, MySQL, Microsoft SQL Server e PostgreSQL.

_Fonte: https://db-engines.com/en/ranking_

Neste projeto será utilizado o SGBD PL/SQL Developer da Oracle.

- ### Criação da Tablespace;

```
CREATE TABLESPACE TBS_PROJ_LIVRARIA
DATAFILE 'C:\ORACLE\DATAFILES\TBS_PROJ_LIVRARIA.DBF'
SIZE 250M AUTOEXTEND ON NEXT 10M MAXSIZE 300M
EXTENT MANAGEMENT LOCAL AUTOALLOCATE
BLOCKSIZE 8K
SEGMENT SPACE MANAGEMENT AUTO;
```

- ### Criação das Tabelas;

```
CREATE TABLE LIVROS
(
       ID_LIVRO NUMBER (10) NOT NULL,
       NOME VARCHAR2 (100) NOT NULL,
       EDITORA VARCHAR2 (30) NOT NULL,
       AUTOR VARCHAR2 (50),
       EDICAO VARCHAR2 (20),
       CATEGORIA VARCHAR2 (20),
       DT_PUBLICACAO DATE,
       NR_PAGINAS NUMBER (10),
       DIMENSOES VARCHAR2 (50),
       ISBN_10 CHAR (10),
       ISBN_13 VARCHAR2 (14),
       QUANTIDADE NUMBER (5),
       PRECO NUMBER (10,2),
       COD_BARRAS CHAR (13),
       CONSTRAINT PK_TB_LIVROS PRIMARY KEY (ID_LIVRO)
) 
TABLESPACE TBS_PROJ_LIVRARIA;

CREATE TABLE COLABORADORES
(
       ID_COLABORADOR NUMBER (5) NOT NULL,
       NOME VARCHAR2 (50) NOT NULL,
       CARGO VARCHAR2 (20) NOT NULL,
       SEXO CHAR (1),
       TELEFONE VARCHAR2 (15),
       ENDERECO VARCHAR2 (20),
       BAIRRO VARCHAR2 (20),
       DT_NASCIMENTO DATE,
       DT_ADMISSAO DATE,
       SALARIO NUMBER (10,2),
       OBSERVACAO VARCHAR2 (100),       
       CONSTRAINT PK_TB_COLABORADORES PRIMARY KEY (ID_COLABORADORES),
       CONSTRAINT CHECK_SEXO CHECK (SEXO IN ('F','M'))
)
TABLESPACE TBS_PROJ_LIVRARIA;

CREATE TABLE SETORES
(
       ID_SETOR NUMBER (5) NOT NULL,
       NOME VARCHAR2 (50) NOT NULL,
       QTD_COLABORADORES VARCHAR2 (5) NOT NULL,
       ID_SETOR_COLAB NUMBER (5),
       CONSTRAINT PK_TB_SETORES PRIMARY KEY (ID_SETOR)
)
TABLESPACE TBS_PROJ_LIVRARIA;

CREATE TABLE VENDAS
(
       ID_VENDA NUMBER (5) NOT NULL,
       DT_VENDA DATE DEFAULT ON NULL SYSDATE,
       QTD_LIVRO NUMBER (10),
       ID_VENDA_LIVRO NUMBER (10) NOT NULL,
       ID_VENDA_DANFE NUMBER (5) NOT NULL,
       ID_VENDA_COLABORADOR NUMBER (5) NOT NULL,
       ID_VENDA_CLIENTE NUMBER (5) NOT NULL,
       CONSTRAINT PK_TB_VENDAS PRIMARY KEY (ID_VENDA)
)
TABLESPACE TBS_PROJ_LIVRARIA;

CREATE TABLE DANFE
(
       ID_DANFE NUMBER (5) NOT NULL,
       NUMERO_NFE NUMBER (10) NOT NULL,
       SERIE_NFE NUMBER (3),
       DT_EMISSAO DATE DEFAULT ON NULL SYSDATE,
       VALOR_TOTAL NUMBER (10,2),
       CHAVE_ELETRONICA NUMBER (15),
       PROTO_AUTORI NUMBER (15),
       ID_DANFE_LIVRO NUMBER (10),
       CONSTRAINT PK_TB_DANFE PRIMARY KEY (ID_DANFE)
)
TABLESPACE TBS_PROJ_LIVRARIA;

CREATE TABLE CLIENTES
(
       ID_CLIENTE NUMBER (5) NOT NULL,
       NOME VARCHAR2 (50) NOT NULL,
       CPF VARCHAR2 (14) NOT NULL,
       TELEFONE VARCHAR2 (15),
       ENDERECO VARCHAR2 (100),
       BAIRRO VARCHAR2 (20),
       CIDADE VARCHAR2 (20),
       DT_NASCIMENTO DATE,
       EMAIL VARCHAR2 (30),
       CONSTRAINT PK_TB_CLIENTES PRIMARY KEY (ID_CLIENTE)
)
TABLESPACE TBS_PROJ_LIVRARIA;

CREATE TABLE AUTORES
(
       ID_AUTOR NUMBER (5) NOT NULL,
       NOME VARCHAR2 (100) NOT NULL,
       REGISTRO VARCHAR2 (50) NOT NULL,
       SEXO CHAR (1),
       PAIS VARCHAR2 (15),
       DT_NASCIMENTO DATE,
       ID_AUTOR_LIVRO NUMBER (10) NOT NULL,
       ID_AUTOR_EDITORA NUMBER (5)NOT NULL,
       CONSTRAINT PK_TB_AUTORES PRIMARY KEY (ID_AUTOR),
       CONSTRAINT CHECK_SEXO_2 CHECK (SEXO IN ('F','M'))
)
TABLESPACE TBS_PROJ_LIVRARIA;

CREATE TABLE EDITORAS
(
       ID_EDITORA NUMBER (5) NOT NULL,
       RAZAO_SOCIAL VARCHAR2 (100) NOT NULL,
       NOME_FANTASIA VARCHAR2 (100),
       CNPJ VARCHAR2 (18) NOT NULL,
       IE VARCHAR2 (12),
       ENDERECO VARCHAR2 (100),
       BAIRRO VARCHAR2 (20),
       CIDADE VARCHAR2 (20),
       EMAIL VARCHAR2 (30),
       DADOS_BANCARIOS VARCHAR2 (100),
       ID_EDITORA_LIVRO NUMBER (10),
       CONSTRAINT PK_TB_EDITORAS PRIMARY KEY (ID_EDITORA)
)
TABLESPACE TBS_PROJ_LIVRARIA;

CREATE TABLE CATEGORIA
(
       ID_CATEGORIA NUMBER (5),
       CATEGORIA VARCHAR2 (20),
       ID_CATEGORIA_LIVRO NUMBER (10),
       CONSTRAINT PK_TB_CATEGORIA PRIMARY KEY (ID_CATEGORIA)       
)
TABLESPACE TBS_PROJ_LIVRARIA;
```

- ### Aplicando as Restrições de Integridade de Chaves Estrangeiras

```
ALTER TABLE SETORES
ADD CONSTRAINT FK_SETORES_COLABORADORES
FOREIGN KEY (ID_SETOR)
REFERENCES COLABORADORES (ID_COLABORADORES)

ALTER TABLE VENDAS
ADD CONSTRAINT FK_VENDAS_LIVRO
FOREIGN KEY (ID_VENDA)
REFERENCES LIVROS (ID_LIVRO)

ALTER TABLE VENDAS
ADD CONSTRAINT FK_VENDAS_DANFE
FOREIGN KEY (ID_VENDA)
REFERENCES DANFE (ID_DANFE)

ALTER TABLE VENDAS
ADD CONSTRAINT FK_VENDAS_COLABORADORES
FOREIGN KEY (ID_VENDA)
REFERENCES COLABORADORES (ID_COLABORADOR)

ALTER TABLE VENDAS
ADD CONSTRAINT FK_VENDAS_CLIENTES
FOREIGN KEY (ID_VENDA)
REFERENCES CLIENTES (ID_CLIENTE)

ALTER TABLE DANFE
ADD CONSTRAINT FK_DANFE_LIVRO
FOREIGN KEY (ID_DANFE)
REFERENCES LIVROS (ID_LIVRO)

ALTER TABLE AUTORES
ADD CONSTRAINT FK_AUTOR_LIVRO
FOREIGN KEY (ID_AUTOR)
REFERENCES LIVROS (ID_LIVRO)

ALTER TABLE AUTORES
ADD CONSTRAINT FK_AUTOR_EDITORA
FOREIGN KEY (ID_AUTOR)
REFERENCES EDITORAS (ID_EDITORA)

ALTER TABLE EDITORAS
ADD CONSTRAINT FK_EDITORA_LIVRO
FOREIGN KEY (ID_EDITORA)
REFERENCES LIVROS (ID_LIVRO)

ALTER TABLE CATEGORIA
ADD CONSTRAINT FK_CATEGORIA_LIVRO
FOREIGN KEY (ID_CATEGORIA)
REFERENCES LIVROS (ID_LIVRO)
```

**_Atualizado em 11/08/2022_**

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


