## INTRODUÇÃO

Este projeto tem a finalidade de demonstrar o processo de criação de um banco de dados, iniciando pela Análise de Requisitos e passando
pela criação dos Modelos Conceitual, Lógico e Físico.

Os assuntos abordados neste projeto serão sobre uma livraria que vende apenas livros físicos, mas pelo fato de ser um projeto contínuo e pensado
no mundo real, naturalmente a livraria passará por mudanças e melhorias, como qualquer empresa.

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

O Modelo Físico consiste no design do banco de dados com base nos requisitos apurados durante a criação do Modelo Lógico. Nesta etapa são representadas as tabelas, colunas, tipos de dados, visualizações, restrições, índices, procedimentos e outros procedimentos estruturais do banco de dados.

Também é definido o SGBD (Sistema de Gerenciamento de Banco de Dados) que será utilizado no projeto. Os SGBD's são os softwares responsáveis por administrar o banco de dados. 
Os mais utilizados atualmente são, respectivamente: Oracle, MySQL, Microsoft SQL Server e PostgreSQL.

_Fonte: https://db-engines.com/en/ranking_

Neste projeto será utilizado o PL/SQL Developer da Oracle.

- ### Criação da Tablespace;

A tablespace consiste, resumidamente, em uma alocação de espaço em um banco de dados para armazenamento dos objetos, como tabelas, índices, views, funções, procedures, usuários e outros.
Neste projeto a tablespace foi definida com tamanho de 250M, podendo ser estendida a cada 10M limitado até 300M. 

```
CREATE TABLESPACE TBS_PROJ_LIVRARIA
DATAFILE 'C:\ORACLE\DATAFILES\TBS_PROJ_LIVRARIA.DBF'
SIZE 250M AUTOEXTEND ON NEXT 10M MAXSIZE 300M
EXTENT MANAGEMENT LOCAL AUTOALLOCATE
BLOCKSIZE 8K
SEGMENT SPACE MANAGEMENT AUTO;
```

- ### Criação das Tabelas;

Nesta etapa foram criadas as tabelas com seus respectivos campos, definindo o tipo, tamanho e se podem ou não ficar nulos.
Também foram definidos as constraints (restrições de integridade) com a chave primária de cada tabela. 

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
       ENDERECO VARCHAR2 (100),
       BAIRRO VARCHAR2 (20),
       DT_NASCIMENTO DATE,
       DT_ADMISSAO DATE,
       SALARIO NUMBER (10,2),
       OBSERVACAO VARCHAR2 (100),       
       CONSTRAINT PK_TB_COLABORADORES PRIMARY KEY (ID_COLABORADOR),
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
       VALOR_TOTAL NUMBER (10,2),
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
       CHAVE_ELETRONICA NUMBER (44),
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

- ### Criando as Chaves Estrangeiras;

Com as tabelas criadas é necessário criar as relações entre elas, como a relação que a tebela **SETORES** possui com a **COLABORADORES**.

Para isso são criados constraints (restrições de integridade) relacionando o campo de uma tabela com outro campo de outra tabela, criando assim
o relaciomento entre duas tabelas distintas. Este relacionamento é chamado de chave estrangeira (foreign key).

```
ALTER TABLE SETORES
ADD CONSTRAINT FK_SETORES_COLABORADORES
FOREIGN KEY (ID_SETOR_COLAB)
REFERENCES COLABORADORES (ID_COLABORADOR)

ALTER TABLE VENDAS
ADD CONSTRAINT FK_VENDAS_LIVRO
FOREIGN KEY (ID_VENDA_LIVRO)
REFERENCES LIVROS (ID_LIVRO)

ALTER TABLE VENDAS
ADD CONSTRAINT FK_VENDAS_DANFE
FOREIGN KEY (ID_VENDA_DANFE)
REFERENCES DANFE (ID_DANFE)

ALTER TABLE VENDAS
ADD CONSTRAINT FK_VENDAS_COLABORADORES
FOREIGN KEY (ID_VENDA_COLABORADOR)
REFERENCES COLABORADORES (ID_COLABORADOR)

ALTER TABLE VENDAS
ADD CONSTRAINT FK_VENDAS_CLIENTES
FOREIGN KEY (ID_VENDA_CLIENTE)
REFERENCES CLIENTES (ID_CLIENTE)

ALTER TABLE DANFE
ADD CONSTRAINT FK_DANFE_LIVRO
FOREIGN KEY (ID_DANFE_LIVRO)
REFERENCES LIVROS (ID_LIVRO)

ALTER TABLE AUTORES
ADD CONSTRAINT FK_AUTOR_LIVRO
FOREIGN KEY (ID_AUTOR_LIVRO)
REFERENCES LIVROS (ID_LIVRO)

ALTER TABLE AUTORES
ADD CONSTRAINT FK_AUTOR_EDITORA
FOREIGN KEY (ID_AUTOR_EDITORA)
REFERENCES EDITORAS (ID_EDITORA)

ALTER TABLE EDITORAS
ADD CONSTRAINT FK_EDITORA_LIVRO
FOREIGN KEY (ID_EDITORA_LIVRO)
REFERENCES LIVROS (ID_LIVRO)

ALTER TABLE CATEGORIA
ADD CONSTRAINT FK_CATEGORIA_LIVRO
FOREIGN KEY (ID_CATEGORIA_LIVRO)
REFERENCES LIVROS (ID_LIVRO)
```

- ### Criação e Privilégios dos Usuários do Banco de Dados;

Neste projeto serão criados dois usuários para acesso ao banco de dados, um com mais e outro com menos privilégios, porém ambos com acessos relativamente básicos.

- **Criação:**

Serão criados os usuários Proprietária e Funcionários, com as senhas LIVRARIA2022 e SELECT2022, respectivamente, ambos na tablespace TBS_PROJ_LIVRARIA.

```
CREATE USER PROPRIETARIA     
IDENTIFIED BY LIVRARIA2022
DEFAULT TABLESPACE TBS_PROJ_LIVRARIA

CREATE USER FUNCIONARIOS
IDENTIFIED BY SELECT2022
DEFAULT TABLESPACE TBS_PROJ_LIVRARIA
```

- **Privilégios:**

Os usuários terão os seguintes privilégios:

- **PROPRIETÁRIA**: 
  - Privilégios de Objeto: SELECT, INSERT, UPDATE e DELETE.
  - Privilégio de Sistema: CREATE VIEW.

- **FUNCIONÁRIOS**: 
  - Privilégio de Objeto: SELECT.

Para conceder privilégios de objeto deve-se informar quais tabelas o usuário em questão poderá acessar. Em uma base com muitas tabelas seria uma rotina trabalhosa,
porém existem meios de conceder privilégios em várias tabelas ao mesmo tempo. 

Neste projeto utilizei um script para gerar os comandos de privilégios prontos para serem executados, uma vez que são poucas tabelas. Também prefiro desta forma por
questão de segurança.

**Gerando Scripts de Privilégios**:

```
SELECT 
'GRANT SELECT, INSERT, UPDATE, DELETE ON ' || X.TABLE_NAME || ' TO PROPRIETARIA;'
FROM DBA_TABLES X
WHERE X.OWNER = USER
AND X.TABLESPACE_NAME = 'TBS_PROJ_LIVRARIA'
 
SELECT 
'GRANT SELECT ON ' || X.TABLE_NAME || ' TO FUNCIONARIOS;'
FROM DBA_TABLES X
WHERE X.OWNER = USER
AND X.TABLESPACE_NAME = 'TBS_PROJ_LIVRARIA'
```

**Resultado**:

```
GRANT SELECT,INSERT, UPDATE, DELETE ON LIVROS TO PROPRIETARIA;
GRANT SELECT,INSERT, UPDATE, DELETE ON COLABORADORES TO PROPRIETARIA;
GRANT SELECT,INSERT, UPDATE, DELETE ON SETORES TO PROPRIETARIA;
GRANT SELECT,INSERT, UPDATE, DELETE ON VENDAS TO PROPRIETARIA;
GRANT SELECT,INSERT, UPDATE, DELETE ON DANFE TO PROPRIETARIA;
GRANT SELECT,INSERT, UPDATE, DELETE ON CLIENTES TO PROPRIETARIA;
GRANT SELECT,INSERT, UPDATE, DELETE ON AUTORES TO PROPRIETARIA;
GRANT SELECT,INSERT, UPDATE, DELETE ON EDITORAS TO PROPRIETARIA;
GRANT SELECT,INSERT, UPDATE, DELETE ON CATEGORIA TO PROPRIETARIA;

GRANT SELECT ON LIVROS TO FUNCIONARIOS;
GRANT SELECT ON COLABORADORES TO FUNCIONARIOS;
GRANT SELECT ON SETORES TO FUNCIONARIOS;
GRANT SELECT ON VENDAS TO FUNCIONARIOS;
GRANT SELECT ON DANFE TO FUNCIONARIOS;
GRANT SELECT ON CLIENTES TO FUNCIONARIOS;
GRANT SELECT ON AUTORES TO FUNCIONARIOS;
GRANT SELECT ON EDITORAS TO FUNCIONARIOS;
GRANT SELECT ON CATEGORIA TO FUNCIONARIOS;
```
**Concedendo privilégio para criação de view ao usuário Proprietária**:

```
GRANT CREATE VIEW TO PROPRIETARIA 
```

- ### Inserindo dados nas tabelas;

Inicialmente não serão inseridos muitos registros nas tabelas, apenas o necessário para iniciar o projeto.

Para esta parte não ficar muito extensa, serão mostrados apenas cinco inserções em cada tabela, mas todos os dados inseridos podem ser conferidos [aqui](https://drive.google.com/file/d/1CkrRohYuIMO_37ttlUexoc1NCYjfq6r3/view?usp=sharing).

**Tabela Livros**:

```
INSERT INTO LIVROS
(ID_LIVRO,NOME,EDITORA,AUTOR,EDICAO,CATEGORIA,DT_PUBLICACAO,NR_PAGINAS,DIMENSOES,ISBN_10,ISBN_13,QUANTIDADE,PRECO,COD_BARRAS)
VALUES
(1000001,'Harry Potter e a Pedra Filosofal','Rocco','J.K. Rowling','1ª edição','Fantasia','07/04/2000',264,
 '20.8 x 14 x 1.4 cm','8532511015','978-8532523051',15,24.90,'9788532523051');
  
INSERT INTO LIVROS
(ID_LIVRO,NOME,EDITORA,AUTOR,EDICAO,CATEGORIA,DT_PUBLICACAO,NR_PAGINAS,DIMENSOES,ISBN_10,ISBN_13,QUANTIDADE,PRECO,COD_BARRAS)
VALUES
(1000002,'Harry Potter e a Câmara Secreta','Rocco','J.K. Rowling','1ª edição','Fantasia','15/08/2000',288,
 '21 x 14 x 1.4 cm','853251166X','978-8532511669',13,36.42,'9788532511669');
  
INSERT INTO LIVROS
(ID_LIVRO,NOME,EDITORA,AUTOR,EDICAO,CATEGORIA,DT_PUBLICACAO,NR_PAGINAS,DIMENSOES,ISBN_10,ISBN_13,QUANTIDADE,PRECO,COD_BARRAS)
VALUES
(1000003,'Harry Potter e o Prisioneiro de Azkaban','Rocco','J.K. Rowling','1ª edição','Fantasia','28/11/2000',348,
 '20.8 x 13.6 x 1.6 cm','1781103704','978-1781103708',19,24.50,'9781781103708');
 
INSERT INTO LIVROS
(ID_LIVRO,NOME,EDITORA,AUTOR,EDICAO,CATEGORIA,DT_PUBLICACAO,NR_PAGINAS,DIMENSOES,ISBN_10,ISBN_13,QUANTIDADE,PRECO,COD_BARRAS)
VALUES
(1000004,'Harry Potter e o Cálice de Fogo','Rocco','J.K. Rowling','1ª edição','Fantasia','08/06/2001',584,
 '20.8 x 14 x 2.4 cm','8532523080','978-8532512529',11,39.98,'9788532512529');
 
INSERT INTO LIVROS
(ID_LIVRO,NOME,EDITORA,AUTOR,EDICAO,CATEGORIA,DT_PUBLICACAO,NR_PAGINAS,DIMENSOES,ISBN_10,ISBN_13,QUANTIDADE,PRECO,COD_BARRAS)
VALUES
(1000005,'Harry Potter e a Ordem da Fenix','Rocco','J.K. Rowling','1ª edição','Fantasia','29/11/2003',704,
 '20.8 x 14 x 2.8 cm','853251622X','978-8532516220',17,49.90,'9788532516220');
```

**Tabela Colaboradores**:

```
INSERT INTO COLABORADORES
(ID_COLABORADOR,NOME,CARGO,SEXO,TELEFONE,ENDERECO,BAIRRO,DT_NASCIMENTO,DT_ADMISSAO,SALARIO,OBSERVACAO)
VALUES
(1001,'Bruno Franco da Silva','Almoxarife I','M','44 994562863','Rua Dr. Luiz Aguiar, 389 - Londrina','Barreto','12/06/1989',
 '01/08/2022',2500.00,'Colaborador com espírito de equipe e ótimas ideias de melhorias futuras.');
 
INSERT INTO COLABORADORES
(ID_COLABORADOR,NOME,CARGO,SEXO,TELEFONE,ENDERECO,BAIRRO,DT_NASCIMENTO,DT_ADMISSAO,SALARIO,OBSERVACAO)
VALUES
(1002,'Roberta Gomes Almeida','Almoxarife II','F','44 987340092','Rua dos Alfeneiros, 100 - Londrina','Fonseca','03/12/1995',
 '01/08/2022',3200.00,'Colaboradora com experiência prévia, perfil de liderança e mindset ágil.');
 
INSERT INTO COLABORADORES
(ID_COLABORADOR,NOME,CARGO,SEXO,TELEFONE,ENDERECO,BAIRRO,DT_NASCIMENTO,DT_ADMISSAO,SALARIO,OBSERVACAO)
VALUES
(1003,'Edna Castilho Bosco','Assis. Financeira I','F','44 976521090','Alameda Divaldo Franco, 820 - Londrina','Pendotiba',
 '22/05/1985','15/07/2022',3554.50,'Colaboradora com muito conhecimento sobre planilhas e organização financeira.');
 
INSERT INTO COLABORADORES
(ID_COLABORADOR,NOME,CARGO,SEXO,TELEFONE,ENDERECO,BAIRRO,DT_NASCIMENTO,DT_ADMISSAO,SALARIO,OBSERVACAO)
VALUES
(1004,'Gustavo Pedrosa Neto','Assis. Financeiro II','M','44 981044582','Travessa São Boaventura, 56 - Londrina','Bigorrilho',
 '19/01/1988','22/07/2022',4050.00,'Colaborador formado na área e com muita experiência para agregar.');
 
INSERT INTO COLABORADORES
(ID_COLABORADOR,NOME,CARGO,SEXO,TELEFONE,ENDERECO,BAIRRO,DT_NASCIMENTO,DT_ADMISSAO,SALARIO,OBSERVACAO)
VALUES
(1005,'Rosa Lourenço Barros','Vendedora','F','44 996045571','Alameda Gomes da Rocha, 347 - Londrina','Charitas',
 '30/07/1999','01/08/2022',1990.00,'Colaboradora prestativa e atenta aos clientes.');
```

**Tabela Setores**:

```
INSERT INTO SETORES
(ID_SETOR, NOME, QTD_COLABORADORES,ID_SETOR_COLAB)
VALUES
(101,'Almoxarifado','2',1001);

INSERT INTO SETORES
(ID_SETOR, NOME, QTD_COLABORADORES,ID_SETOR_COLAB)
VALUES
(102,'Almoxarifado','2',1002);

INSERT INTO SETORES
(ID_SETOR, NOME, QTD_COLABORADORES,ID_SETOR_COLAB)
VALUES
(103,'Financeiro','2',1003);

INSERT INTO SETORES
(ID_SETOR, NOME, QTD_COLABORADORES,ID_SETOR_COLAB)
VALUES
(104,'Financeiro','2',1004);

INSERT INTO SETORES
(ID_SETOR, NOME, QTD_COLABORADORES,ID_SETOR_COLAB)
VALUES
(105,'Vendas','3',1005);
```

**Tabela Clientes**:

```
INSERT INTO CLIENTES
(ID_CLIENTE,NOME,CPF,TELEFONE,ENDERECO,BAIRRO,CIDADE,DT_NASCIMENTO,EMAIL)
VALUES
(201,'Carlos Augusto Souza','50781709954','44 976452098','Rua Antonina, 45','Antonina','Londrina',
 '01/08/1980','carlos.augusto@gmail.com');
 
INSERT INTO CLIENTES
(ID_CLIENTE,NOME,CPF,TELEFONE,ENDERECO,BAIRRO,CIDADE,DT_NASCIMENTO,EMAIL)
VALUES
(202,'Aline Oliveira Leite','74164246901','44 955671098','Avenida Bruno Cortez, 198','Gomes Luz','Niterói',
 '22/09/1982','aline.leite@yahoo.com.br');
 
INSERT INTO CLIENTES
(ID_CLIENTE,NOME,CPF,TELEFONE,ENDERECO,BAIRRO,CIDADE,DT_NASCIMENTO,EMAIL)
VALUES
(203,'João Bento Misty','09867264940','21 987354671','Rua Dr Palmier, 443','Barreto','Niterói',
 '26/12/1988','joao.bento88@gmail.com');

INSERT INTO CLIENTES
(ID_CLIENTE,NOME,CPF,TELEFONE,ENDERECO,BAIRRO,CIDADE,DT_NASCIMENTO,EMAIL)
VALUES
(204,'Leandro Araújo de Oliveira','68012109808','11 987347686','Rua das Oliveiras, 456','Santo Amaro','Barueri',
 '05/07/1984','leandro.net1000@gmail.com');
```

**Tabela Editoras**:

```
INSERT INTO EDITORAS
(ID_EDITORA,RAZAO_SOCIAL,NOME_FANTASIA,CNPJ,IE,ENDERECO,BAIRRO,CIDADE,EMAIL,DADOS_BANCARIOS,ID_EDITORA_LIVRO)
VALUES
(301,'EDITORA ROCCO LTDA','Editora Rocco','42.444.703/0004-00','115215009113','Alameda Santos, 1165 - Sala 11',
 'Cerqueira Cesar','São Paulo','rocco@gmail.com','AG: 3459-0 C/C: 42372-1 - Banco Bradesco',1000001);
 
INSERT INTO EDITORAS
(ID_EDITORA,RAZAO_SOCIAL,NOME_FANTASIA,CNPJ,IE,ENDERECO,BAIRRO,CIDADE,EMAIL,DADOS_BANCARIOS,ID_EDITORA_LIVRO)
VALUES
(302,'EDITORA ROCCO LTDA','Editora Rocco','42.444.703/0004-00','115215009113','Alameda Santos, 1165 - Sala 11',
 'Cerqueira Cesar','São Paulo','rocco@gmail.com','AG: 3459-0 C/C: 42372-1 - Banco Bradesco',1000002);
 
INSERT INTO EDITORAS
(ID_EDITORA,RAZAO_SOCIAL,NOME_FANTASIA,CNPJ,IE,ENDERECO,BAIRRO,CIDADE,EMAIL,DADOS_BANCARIOS,ID_EDITORA_LIVRO)
VALUES
(303,'EDITORA ROCCO LTDA','Editora Rocco','42.444.703/0004-00','115215009113','Alameda Santos, 1165 - Sala 11',
 'Cerqueira Cesar','São Paulo','rocco@gmail.com','AG: 3459-0 C/C: 42372-1 - Banco Bradesco',1000003);
 
INSERT INTO EDITORAS
(ID_EDITORA,RAZAO_SOCIAL,NOME_FANTASIA,CNPJ,IE,ENDERECO,BAIRRO,CIDADE,EMAIL,DADOS_BANCARIOS,ID_EDITORA_LIVRO)
VALUES
(304,'EDITORA ROCCO LTDA','Editora Rocco','42.444.703/0004-00','115215009113','Alameda Santos, 1165 - Sala 11',
 'Cerqueira Cesar','São Paulo','rocco@gmail.com','AG: 3459-0 C/C: 42372-1 - Banco Bradesco',1000004);
 
INSERT INTO EDITORAS
(ID_EDITORA,RAZAO_SOCIAL,NOME_FANTASIA,CNPJ,IE,ENDERECO,BAIRRO,CIDADE,EMAIL,DADOS_BANCARIOS,ID_EDITORA_LIVRO)
VALUES
(305,'EDITORA ROCCO LTDA','Editora Rocco','42.444.703/0004-00','115215009113','Alameda Santos, 1165 - Sala 11',
 'Cerqueira Cesar','São Paulo','rocco@gmail.com','AG: 3459-0 C/C: 42372-1 - Banco Bradesco',1000005);
```

**Tabela Autores**;

```
INSERT INTO AUTORES 
(ID_AUTOR,NOME,REGISTRO,SEXO,PAIS,DT_NASCIMENTO,ID_AUTOR_LIVRO,ID_AUTOR_EDITORA)
VALUES
(401,'Diego Eis','R76368','M','Brasil','27/09/1980',1000012,312);

INSERT INTO AUTORES 
(ID_AUTOR,NOME,REGISTRO,SEXO,PAIS,DT_NASCIMENTO,ID_AUTOR_LIVRO,ID_AUTOR_EDITORA)
VALUES
(402,'Donald A. Norman','R81029','M','Estados Unidos','25/12/1935',1000017,319);

INSERT INTO AUTORES 
(ID_AUTOR,NOME,REGISTRO,SEXO,PAIS,DT_NASCIMENTO,ID_AUTOR_LIVRO,ID_AUTOR_EDITORA)
VALUES
(403,'Eduardo Gonçalves','R10253','M','Brasil','04/03/1982',1000026,314);

INSERT INTO AUTORES 
(ID_AUTOR,NOME,REGISTRO,SEXO,PAIS,DT_NASCIMENTO,ID_AUTOR_LIVRO,ID_AUTOR_EDITORA)
VALUES
(404,'Eduardo Gonçalves','R10253','M','Brasil','04/03/1982',1000025,313);

INSERT INTO AUTORES 
(ID_AUTOR,NOME,REGISTRO,SEXO,PAIS,DT_NASCIMENTO,ID_AUTOR_LIVRO,ID_AUTOR_EDITORA)
VALUES
(405,'Eliyahu M. Goldratt','R68920','M','Palestina','31/03/1947',1000009,309);
```

**Tabela Categoria**;

```
INSERT INTO CATEGORIA
(ID_CATEGORIA,CATEGORIA,ID_CATEGORIA_LIVRO)
VALUES
(501,'Biografia',1000018);

INSERT INTO CATEGORIA
(ID_CATEGORIA,CATEGORIA,ID_CATEGORIA_LIVRO)
VALUES
(502,'Engenharia',1000017);

INSERT INTO CATEGORIA
(ID_CATEGORIA,CATEGORIA,ID_CATEGORIA_LIVRO)
VALUES
(503,'Fantasia',1000003);

INSERT INTO CATEGORIA
(ID_CATEGORIA,CATEGORIA,ID_CATEGORIA_LIVRO)
VALUES
(504,'Fantasia',1000004);

INSERT INTO CATEGORIA
(ID_CATEGORIA,CATEGORIA,ID_CATEGORIA_LIVRO)
VALUES
(505,'Fantasia',1000005);
```

**Tabela DANFE**;

```
INSERT INTO DANFE
(ID_DANFE,NUMERO_NFE,SERIE_NFE,DT_EMISSAO,VALOR_TOTAL,CHAVE_ELETRONICA,PROTO_AUTORI,ID_DANFE_LIVRO)
VALUES
(601,000001,001,'01/08/2022',89.90,41220876455020000119550010000000010174,372619840933628,1000025);

INSERT INTO DANFE
(ID_DANFE,NUMERO_NFE,SERIE_NFE,DT_EMISSAO,VALOR_TOTAL,CHAVE_ELETRONICA,PROTO_AUTORI,ID_DANFE_LIVRO)
VALUES
(602,000002,001,'01/08/2022',79.96,41220876455020000119550010000000020164,361833908462781,1000004);

INSERT INTO DANFE
(ID_DANFE,NUMERO_NFE,SERIE_NFE,DT_EMISSAO,VALOR_TOTAL,CHAVE_ELETRONICA,PROTO_AUTORI,ID_DANFE_LIVRO)
VALUES
(603,000003,001,'01/08/2022',31.99,41220876455020000119550010000000030137,291774029177356,1000015);

INSERT INTO DANFE
(ID_DANFE,NUMERO_NFE,SERIE_NFE,DT_EMISSAO,VALOR_TOTAL,CHAVE_ELETRONICA,PROTO_AUTORI,ID_DANFE_LIVRO)
VALUES
(604,000004,001,'02/08/2022',64.40,41220876455020000119550010000000040145,561280485129049,1000021);

INSERT INTO DANFE
(ID_DANFE,NUMERO_NFE,SERIE_NFE,DT_EMISSAO,VALOR_TOTAL,CHAVE_ELETRONICA,PROTO_AUTORI,ID_DANFE_LIVRO)
VALUES
(605,000005,001,'03/08/2022',29.70,41220876455020000119550010000000050136,991827360083552,1000016);
```

**Tabela Vendas**:

```
INSERT INTO VENDAS
(ID_VENDA,DT_VENDA,VALOR_TOTAL,QTD_LIVRO,ID_VENDA_LIVRO,ID_VENDA_DANFE,ID_VENDA_COLABORADOR,ID_VENDA_CLIENTE)
VALUES
(701,'01/08/2022',89.90,1,1000025,601,1005,202);

INSERT INTO VENDAS
(ID_VENDA,DT_VENDA,VALOR_TOTAL,QTD_LIVRO,ID_VENDA_LIVRO,ID_VENDA_DANFE,ID_VENDA_COLABORADOR,ID_VENDA_CLIENTE)
VALUES
(702,'01/08/2022',79.96,2,1000004,602,1005,203);

INSERT INTO VENDAS
(ID_VENDA,DT_VENDA,VALOR_TOTAL,QTD_LIVRO,ID_VENDA_LIVRO,ID_VENDA_DANFE,ID_VENDA_COLABORADOR,ID_VENDA_CLIENTE)
VALUES
(703,'01/08/2022',31.9,1,1000015,603,1007,204);

INSERT INTO VENDAS
(ID_VENDA,DT_VENDA,VALOR_TOTAL,QTD_LIVRO,ID_VENDA_LIVRO,ID_VENDA_DANFE,ID_VENDA_COLABORADOR,ID_VENDA_CLIENTE)
VALUES
(704,'02/08/2022',64.40,2,1000021,604,1006,201);

INSERT INTO VENDAS
(ID_VENDA,DT_VENDA,VALOR_TOTAL,QTD_LIVRO,ID_VENDA_LIVRO,ID_VENDA_DANFE,ID_VENDA_COLABORADOR,ID_VENDA_CLIENTE)
VALUES
(705,'03/08/2022',29.70,1,1000016,605,1007,204);
```

- ### Criando Relatórios Gerenciais - Views;

Nesta etapa serão criadas views como forma de relatórios gerenciais, mostrando dados importantes para o negócio, como total de vendas diárias, total de vendas
por colaborador, clientes aniversariantes do mês e outros.

**- Relatório de Vendas Diárias - Sintético**:

```
CREATE OR REPLACE VIEW VENDAS_DIARIAS_SINTETICO AS
SELECT 
DISTINCT DT_VENDA AS DATA_VENDA,
SUM (QTD_LIVRO) AS QUANTIDADE,
SUM (ROUND (VALOR_TOTAL,2)) AS VALOR_TOTAL
FROM VENDAS
GROUP BY DT_VENDA
ORDER BY 1
```

Resultado:

```
SELECT * FROM VENDAS_DIARIAS_SINTETICO
```

![Sintético](https://i.ibb.co/KmrgD7x/Screenshot-1.jpg)

**- Relatório de Vendas Diárias - Analítico**:

```
CREATE OR REPLACE VIEW VENDAS_DIARIAS_ANALITICO AS 
SELECT V.DT_VENDA AS DATA_VENDA,
D.NUMERO_NFE AS NUMERO_NFE,
L.NOME AS TÍTULO,
L.EDITORA AS EDITORA,
V.QTD_LIVRO AS QUANTIDADE,
V.VALOR_TOTAL AS VALOR_TOTAL,
C.NOME AS COLABORADOR
FROM VENDAS V
JOIN DANFE D
ON V.ID_VENDA_DANFE = D.ID_DANFE
JOIN COLABORADORES C
ON V.ID_VENDA_COLABORADOR = C.ID_COLABORADOR
JOIN LIVROS L
ON V.ID_VENDA_LIVRO = L.ID_LIVRO
ORDER BY 1
```

Resultado:

```
SELECT * FROM VENDAS_DIARIAS_ANALITICO
```

![Analítico](https://i.ibb.co/ZLsHH0D/Screenshot-2.jpg)

**- Relatório de Vendas Mensais**:

```
CREATE OR REPLACE VIEW TOTAL_VENDAS_MENSAIS AS
SELECT TO_CHAR (DT_VENDA,'MM/YYYY') AS MES,
SUM (QTD_LIVRO) AS QTD_TOTAL,
SUM (VALOR_TOTAL) AS VALOR_TOTAL
FROM VENDAS
GROUP BY TO_CHAR (DT_VENDA,'MM/YYYY')
```

Resultado:

```
SELECT * FROM TOTAL_VENDAS_MENSAIS
```

![Mensal](https://i.ibb.co/VjMHGQW/Screenshot-3.jpg)

**- Relatório Total de Vendas por Categoria**:

```
CREATE OR REPLACE VIEW TOTAL_VENDAS_CATEGORIA AS
SELECT 
DISTINCT L.CATEGORIA, 
TO_CHAR (DT_VENDA,'MM/YYYY') AS MÊS,
SUM (V.QTD_LIVRO) AS QUANTIDADE,
SUM (V.VALOR_TOTAL) AS VALOR_TOTAL
FROM VENDAS V
JOIN LIVROS L
ON V.ID_VENDA_LIVRO = L.ID_LIVRO
GROUP BY L.CATEGORIA,
TO_CHAR (DT_VENDA,'MM/YYYY')
ORDER BY 1
```

Resultado:

```
SELECT * FROM TOTAL_VENDAS_CATEGORIA
```

![Categoria](https://i.ibb.co/mT62Mth/Screenshot-4.jpg)

**- Relatório de Vendas por Colaborador**:

```
CREATE OR REPLACE VIEW TOTAL_VENDAS_COLABORADOR AS
SELECT 
DISTINCT C.NOME AS COLABORADOR,
SUM (V.QTD_LIVRO) AS QUANTIDADE_VENDIDOS,
SUM (ROUND (V.VALOR_TOTAL,2)) AS VALOR_TOTAL,
C.OBSERVACAO
FROM VENDAS V
JOIN COLABORADORES C
ON V.ID_VENDA_COLABORADOR = C.ID_COLABORADOR
GROUP BY C.NOME,
C.OBSERVACAO
ORDER BY 1
```

Resultado:

```
SELECT * FROM TOTAL_VENDAS_COLABORADOR
```

![Colaborador](https://i.ibb.co/Z8y5626/Screenshot-5.jpg)

**- Relatório Aniversariantes do Mês**:

```
CREATE OR REPLACE VIEW ANIVERSARIANTES AS
SELECT NOME AS CLIENTE,
TELEFONE,
TO_CHAR (DT_NASCIMENTO,'DD/MM') AS ANIVERSÁRIO,
TO_CHAR (SYSDATE,'YYYY') - TO_CHAR (DT_NASCIMENTO,'YYYY') AS IDADE,
(CASE
  WHEN ID_CLIENTE BETWEEN 201 AND 204 THEN 'CLIENTE'
  ELSE 'COLABORADOR'
END) AS TIPO
FROM CLIENTES
UNION ALL
SELECT
NOME AS COLABORADOR,
TELEFONE,
TO_CHAR (DT_NASCIMENTO,'DD/MM') AS ANIVERSÁRIO,
TO_CHAR (SYSDATE,'YYYY') - TO_CHAR (DT_NASCIMENTO,'YYYY') AS IDADE,
(CASE
  WHEN ID_COLABORADOR BETWEEN 1001 AND 1007 THEN 'COLABORADOR'
  ELSE 'CLIENTE'
END) AS TIPO
FROM COLABORADORES
ORDER BY 3
```

Resultado:

```
SELECT * FROM ANIVERSARIANTES
```

![Aniversariante](https://i.ibb.co/XxWk4jV/Screenshot-6.jpg)

- ### Criando Tarefas Performáticas - Procedures;

As procedures são blocos de comandos SQL que armazenam comandos repetitivos a partir de parâmetros de entrada, sendo aconselhável para usuários que possuam
pouco conhecimento e/ou sem privilégios para executar comandos DDL e DML.

Neste projeto serão criados procedures simples de acordo com a regra de negócio e suas necessidades.

**- Inserção de novos livros**:

Antes de criar a procedure, criei uma sequence no campo ID_LIVRO para não haver a necessidade de entrar com este dado manualmente;

```
CREATE SEQUENCE ID_LIVRO
INCREMENT BY 1
START WITH 1000027
MAXVALUE 1999999
NOCYCLE
```

Procedure: 

```
CREATE OR REPLACE PROCEDURE SP_INCLUIR_LIVRO
       (P_NOME_LIVRO IN LIVROS.NOME%TYPE,
        P_EDITORA IN LIVROS.EDITORA%TYPE,
        P_AUTOR IN LIVROS.AUTOR%TYPE,
        P_EDICAO IN LIVROS.EDICAO%TYPE,
        P_CATEGORIA IN LIVROS.CATEGORIA%TYPE,
        P_DATA_PUBLICACAO IN LIVROS.DT_PUBLICACAO%TYPE,
        P_NR_PAGINAS IN LIVROS.NR_PAGINAS%TYPE,
        P_DIMENSOES IN LIVROS.DIMENSOES%TYPE,
        P_ISBN_10 IN LIVROS.ISBN_10%TYPE,
        P_ISBN_13 IN LIVROS.ISBN_13%TYPE,
        P_QUANTIDADE IN LIVROS.QUANTIDADE%TYPE,
        P_PRECO IN LIVROS.PRECO%TYPE,
        P_CODIGO_BARRAS IN LIVROS.COD_BARRAS%TYPE)
IS
BEGIN
       INSERT INTO LIVROS
       (ID_LIVRO, NOME, EDITORA,AUTOR,EDICAO,CATEGORIA,DT_PUBLICACAO,NR_PAGINAS,
        DIMENSOES,ISBN_10,ISBN_13,QUANTIDADE,PRECO,COD_BARRAS)
       VALUES
       (ID_LIVRO.NEXTVAL,P_NOME_LIVRO,P_EDITORA,P_AUTOR,P_EDICAO,P_CATEGORIA,
        P_DATA_PUBLICACAO,P_NR_PAGINAS,P_DIMENSOES,P_ISBN_10,P_ISBN_13,P_QUANTIDADE,
        P_PRECO,P_CODIGO_BARRAS);
END;
```

Exemplo de execução:

```
BEGIN SP_INCLUIR_LIVRO
  (P_NOME_LIVRO => 'Doutor sono',
   P_EDITORA => 'Suma',
   P_AUTOR => 'Stephen King',
   P_EDICAO => '1ª edição',
   P_CATEGORIA => 'Fantasia',
   P_DATA_PUBLICACAO => '23/10/2014',
   P_NR_PAGINAS => 480,
   P_DIMENSOES => '23 x 15.8 x 2.8 cm',
   P_ISBN_10 => '8581052436',
   P_ISBN_13 => '978-8581052436',
   P_QUANTIDADE => 7,
   P_PRECO => 25.98,
   P_CODIGO_BARRAS => '9788581052436');
END;
```

Resultado:

![proc_insert_simples](https://i.ibb.co/TtbT1Dz/Proc-insert.jpg)

**-- Alteração de Categoria, Quantidade e/ou Preço**:

Optei por criar três procedures simples e distintas para a alteração da categoria, quantidade e preço dos livros, e em seguida incluí-las em um package.

Procedures:

```
CREATE OR REPLACE PROCEDURE SP_ALT_CATEGORIA_LIVROS
       (P_NOVA_CATEGORIA IN LIVROS.CATEGORIA%TYPE,
        P_NOME_LIVRO IN LIVROS.NOME%TYPE)
IS 
BEGIN
      UPDATE LIVROS
      SET CATEGORIA = P_NOVA_CATEGORIA
      WHERE NOME = P_NOME_LIVRO;
      COMMIT;
END;
```

```
CREATE OR REPLACE PROCEDURE SP_ALT_QUANTIDADE_LIVROS
       (P_NOVA_QUANTIDADE IN LIVROS.QUANTIDADE%TYPE,
        P_NOME_LIVRO IN LIVROS.NOME%TYPE)
IS
BEGIN
       UPDATE LIVROS
       SET QUANTIDADE = P_NOVA_QUANTIDADE
       WHERE NOME = P_NOME_LIVRO;  
       COMMIT;
END;
```

```
CREATE OR REPLACE PROCEDURE SP_ALT_PRECO_LIVROS
       (P_NOVO_PRECO IN LIVROS.PRECO%TYPE,
        P_NOME_LIVRO IN LIVROS.NOME%TYPE)
IS
BEGIN
        UPDATE LIVROS
        SET PRECO = P_NOVO_PRECO
        WHERE NOME = P_NOME_LIVRO;
        COMMIT;
END; 
```

Cabeçalho do Package:

```
CREATE OR REPLACE PACKAGE PC_UPDATE_LIVROS
IS
PROCEDURE SP_ALT_CATEGORIA_LIVROS
       (P_NOVA_CATEGORIA IN LIVROS.CATEGORIA%TYPE,
        P_NOME_LIVRO IN LIVROS.NOME%TYPE);       
PROCEDURE SP_ALT_QUANTIDADE_LIVROS
       (P_NOVA_QUANTIDADE IN LIVROS.QUANTIDADE%TYPE,
        P_NOME_LIVRO IN LIVROS.NOME%TYPE);
PROCEDURE SP_ALT_PRECO_LIVROS
       (P_NOVO_PRECO IN LIVROS.PRECO%TYPE,
        P_NOME_LIVRO IN LIVROS.NOME%TYPE);
END;
```

Corpo do Package:

```
CREATE OR REPLACE PACKAGE BODY PC_UPDATE_LIVROS
IS
PROCEDURE SP_ALT_CATEGORIA_LIVROS
       (P_NOVA_CATEGORIA IN LIVROS.CATEGORIA%TYPE,
        P_NOME_LIVRO IN LIVROS.NOME%TYPE)
IS 
BEGIN
      UPDATE LIVROS
      SET CATEGORIA = P_NOVA_CATEGORIA
      WHERE NOME = P_NOME_LIVRO;
      COMMIT;
END;
PROCEDURE SP_ALT_QUANTIDADE_LIVROS
       (P_NOVA_QUANTIDADE IN LIVROS.QUANTIDADE%TYPE,
        P_NOME_LIVRO IN LIVROS.NOME%TYPE)
IS
BEGIN
       UPDATE LIVROS
       SET QUANTIDADE = P_NOVA_QUANTIDADE
       WHERE NOME = P_NOME_LIVRO;  
       COMMIT;
END;     
PROCEDURE SP_ALT_PRECO_LIVROS
       (P_NOVO_PRECO IN LIVROS.PRECO%TYPE,
        P_NOME_LIVRO IN LIVROS.NOME%TYPE)
IS
BEGIN
        UPDATE LIVROS
        SET PRECO = P_NOVO_PRECO
        WHERE NOME = P_NOME_LIVRO;
        COMMIT;
END;
END PC_UPDATE_LIVROS;
```

Exemplos de execução:

```
BEGIN PC_UPDATE_LIVROS.SP_ALT_CATEGORIA_LIVROS
('TESTE_PACKAGE','Harry Potter e a Pedra Filosofal');
END;  
```

```
BEGIN PC_UPDATE_LIVROS.SP_ALT_QUANTIDADE_LIVROS
(1500,'Harry Potter e a Pedra Filosofal');
END;
```

```
BEGIN PC_UPDATE_LIVROS.SP_ALT_PRECO_LIVROS
(1200,'Harry Potter e a Pedra Filosofal');
END;
```

Resultado:

![Pacote_atualizacao_livro](https://i.ibb.co/rbchQhM/Screenshot-1.jpg)


**_Atualizado em 19/09/2022_**

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


