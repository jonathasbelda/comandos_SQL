
# Comandos Básicos de SQL

## ⌨ CRIAR UMA TABELA
O comando **CREATE TABLE** é utilizado para criar uma tabela para o banco de dados:

**EXEMPLO:**

```
CREATE TABLE "NOME DA TABELA" 

```
**O que são restrições em um banco de dados?**

Uma restrição de verificação (também referida como uma restrição de verificação de tabela) é uma regra de banco de dados que especifica os valores permitidos em uma ou mais colunas de cada linha de uma tabela.



**Principais tipos de restrições que podem ser aplicadas.** 
 
* NOT NULL - Não permite nulos
* UNIQUE - Força que todos os valores em uma coluna sejam diferentes
* PRIMARY KEY - Uma junção de NOT NULL e UNIQUE
* FOREIGN KEY - Identifica únicamente uma linha em outra tabela. (relaciona as tabelas)
* CHECK - Força uma condição específica em uma coluna
* DEFAULT - Força um valor padrão quando nenhum valor é passado


<br>


## ⌨ INSERIR COLUNAS QUE IRÁ CONTER DENTRO DA TABELA     

**EXEMPLO:**

```
CREATE TABLE TESTE           { CRIA A TABELA COM O NOME TESTE }
(ID INT PRIMARY KEY,         { CRIA A COLUNA ID }
NOME VARCHAR (MAX) NOT NULL, { CRIA A COLUNA NOME }
EMAIL VARCHAR (100) UNIQUE   { CRIA A COLUNA EMAIL }
DATA_NASCIMENTO DATE         { CRIA A COLUNA DATA DE NASCIMENTO }
);
```
<br>

## ⌨ INSERIR UMA COLUNA EM UMA TABELA JÁ CRIADA USANDO O COMANDO ALTER TABLE

O comando **ALTER TABLE** em **SQL** é usado para modificar a estrutura de uma tabela existente. Ele permite adicionar, excluir ou alterar colunas, restrições e outras propriedades da tabela. Basicamente, permite ajustar o esquema (estrutura) do banco de dados, enquanto o comando UPDATE é usado para modificar os dados dentro da tabela.

**CÓDIGO:**

```
ALTER TABLE "NOME DA TABELA" { ALTERAR A TABELA }
ADD "NOME DA COLUNA";        { INSERIR A NOVA COLUNA }

```

**EXEMPLO:**

```
-- Adicionar uma nova coluna chamada "email" do tipo VARCHAR(100) à tabela "clientes"
ALTER TABLE clientes
ADD email VARCHAR(100);

-- Remover a coluna "telefone" da tabela "clientes"
ALTER TABLE clientes
DROP COLUMN telefone;

-- Alterar o tipo de dados da coluna "idade" para INT na tabela "clientes"
ALTER TABLE clientes
MODIFY COLUMN idade INT;

-- Adicionar uma chave primária à coluna "id" na tabela "clientes"
ALTER TABLE clientes
ADD PRIMARY KEY (id);

-- Renomear a tabela "clientes" para "usuarios"
ALTER TABLE clientes
RENAME TO usuarios;

-- Alterar o nome de uma coluna já existente em uma tabela 
EXEC sp_rename 'NOME_DA_TABELA.NOME_DA_COLUNA_ANTIGA','NOME_DA_COLUNA_NOVA','COLUMN';


```

<br>


## ⌨ SELECIONAR UMA TABELA
O comando **SELECT** em bancos de dados SQL serve para consultar e recuperar dados de uma ou mais tabelas.

**CÓDIGO:**

```
SELECT "nome_da_coluna" { TRAZ UMA COLUNA ESPECIFICA }
SELECT *                { EXIBE TODAS AS COLUNAS DA TABELA }

```
<br>

## ⌨ INFORMAR A TABELA
O comando **FROM** em **SQL** é utilizado na cláusula **SELECT** para especificar de qual tabela ou visualização os dados serão consultados.

**CÓDIGO:**

```
SELECT *   { SELECIONAR TODAS AS COLUNAS }
FROM       { DA TABELA TESTE }

```

**EXEMPLO:**

```
SELECT ID, NAME, IDADE
FROM TESTE

```
<br>

## ⌨ INSERIR LINHAS
O comando **INSERT INTO** em bancos de dados serve para inserir novos dados em tabelas.Ele permite adicionar uma ou mais linhas de dados a uma tabela existente.

**CÓDIGO:**

```
INSERT INTO "nome_da_tabela" (coluna1, coluna2, coluna3, ...)
VALUES                       (valor1, valor2, valor3, ...);

```

**EXEMPLO:**
```
INSERT INTO TESTE (nome, cidade, idade)   { INSERIR UMA LINHA NA TABELA }
VALUES ('João Silva', 'São Paulo', 30);   { VALORES }

```

<br>

## ⌨ UTILIZANDO O COMANDO WHERE

O comando **WHERE** em bancos de dados **SQL** serve para filtrar os dados retornados por uma consulta, permitindo selecionar apenas as linhas que atendem a determinadas condições. 

**CÓDIGO:**

```
SELECT coluna1, coluna2, ...
FROM   nome_tabela
WHERE  condição;

```

**ALGUNS EXEMPLOS DA UTILIZAÇÃO DO COMANDO WHERE:**

**Procurar por nome e sobrenome:**

```
SELECT { coluna }
FROM   { tabela }
WHERE LastName = 'Santos' AND firstName = 'Jão'
```
**Selecionar todos os clientes da cidade de "São Paulo"**

```
SELECT *
FROM Clientes
WHERE Cidade = 'São Paulo';
```

**Selecionar produtos com preço maior que 100:**

```
SELECT *
FROM Produtos
WHERE Preco > 100;

```

**(A cláusula WHERE é usada com o comando SELECT (ou UPDATE, DELETE, etc.) para especificar as condições de filtragem. A estrutura básica é: ):**

```
= IGUAL
> MAIOR QUE
< MENOR QUE
>= MAIOR QUE OU IGUAL
<= MENOR QUE OU IGUAL
<> DIFERENTE DE
AND OPERADOR 'E'
OR OPERADOR 'OU'

```

<br>

## ⌨ UTILIZANDO O COMANDO BETWEEN
O comando **BETWEEN** em **SQL** é usado para selecionar valores dentro de um intervalo especificado. Ele permite filtrar dados com base em um limite inferior e superior, incluindo ambos os limites na seleção. É frequentemente usado com a cláusula **WHERE** para refinar os resultados de uma consulta, seja com números, datas ou texto. 

**CÓDIGO:**

```
SELECT coluna1, coluna2, ...
FROM   nome_da_tabela
WHERE  coluna BETWEEN valor_inicial AND valor_final;

```
**EXEMPLO:**

```
SELECT id, nome, preco
FROM   produtos
WHERE  preco BETWEEN 10 AND 50;

```

<br>


## ⌨ UTILIZANDO O COMANDO IN

O comando **IN** em **SQL** é utilizado na cláusula **WHERE** para verificar se o valor de uma coluna está presente em uma lista de valores especifica. Ele permite simplificar consultas que, de outra forma, exigiriam várias condições **OR**.

**CÓDIGO:**

```
-- Informando o valor IN:

SELECT { coluna }
FROM   { tabela }
WHERE  { coluna } IN (valor1, valor2, valor3);

-- Informando o valor IN/OR:

SELECT *
FROM produtos
WHERE categoria = 'valor1' OR categoria = 'livros' OR categoria = 'valor2';

```
**EXEMPLO:**

```
-- Informando o valor IN:

SELECT *
FROM  produtos
WHERE categoria IN ('eletronicos', 'livros', 'roupas');

-- Informando o valor IN/OR:

SELECT *
FROM produtos
WHERE categoria = 'eletronicos' OR categoria = 'livros' OR categoria = 'roupas';

```

<br>

## ⌨ UTILIZANDO O COMANDO UPDATE

O comando **UPDATE** em **SQL** é usado para modificar os dados existentes em uma tabela do banco de dados. Ele permite alterar valores em uma ou mais colunas de uma ou mais linhas, com base em critérios especificados. 

**CÓDIGO:**

```
UPDATE tabela
SET    coluna1 = valor1, coluna2 = valor2, ...
WHERE  condicao;

```

**EXEMPLO:**

```
UPDATE clientes
SET    email = 'novo_email@example.com', telefone = '9999-8888'
WHERE  id = 1;

```

<br>

## ⌨ UTILIZANDO O COMANDO DELETE

O comando **DELETE** em **SQL** é utilizado para remover permanentemente linhas de uma tabela. Ele permite apagar registros específicos ou todos os registros de uma tabela, dependendo da condição especificada na cláusula **WHERE**. Se a cláusula **WHERE** for omitida, todas as linhas serão removidas. 

**EXEMPLO:**

```
-- Excluir todas as linhas da tabela "clientes"
DELETE FROM clientes;

-- Excluir a linha onde o ID do cliente é 1
DELETE FROM clientes WHERE id = 1;

-- Excluir todas as linhas onde a cidade é "São Paulo"
DELETE FROM clientes WHERE cidade = 'São Paulo';

```

<br>

## ⌨ UTILIZANDO O COMANDO LIKE

O comando **LIKE** em **SQL** é usado para pesquisar padrões em colunas de texto, permitindo correspondências parciais em vez de apenas buscas exatas por igualdade. Ele utiliza caracteres curinga para especificar os padrões de busca. 


**CÓDIGO:**

```
SELECT colunas
FROM tabela
WHERE coluna LIKE 'padrão';

```

**EXEMPLO:**

```
-- Pesquisar nomes que terminam com "Silva":
SELECT nome
FROM   clientes
WHERE  nome LIKE '%Silva';

-- Pesquisar nomes que contêm "José" em qualquer posição: 
SELECT nome
FROM   clientes
WHERE  nome LIKE '%José%';

-- Pesquisar nomes com cinco caracteres, começando com "M" e terminando com "o"
SELECT nome
FROM   Clientes
WHERE  nome LIKE 'M___o';

```

<br>

## ⌨ UTILIZANDO O COMANDO LIMIT

O comando **LIMIT** em **SQL** é usado para restringir o número de linhas retornadas por uma consulta. Ele é útil quando você precisa visualizar apenas um número específico de registros, seja para análise rápida ou para implementar paginação em uma aplicação. 


**CÓDIGO:**

```
SELECT * FROM Clientes LIMIT 10;

```
**Otimizar consultas Reduz o número de linhas retornadas, isso pode melhorar o desempenho da consulta, especialmente em tabelas grandes.**

<br>


## ⌨ UTILIZANDO O COMANDO TOP

O comando **TOP** em **SQL** é utilizado para limitar o número de linhas retornadas em uma consulta. Ele especifica quantas linhas do resultado de uma consulta devem ser exibidas, sendo útil para otimizar consultas e obter apenas os dados necessários, especialmente em grandes conjuntos de resultados. 

**CÓDIGO:**

```
SELECT TOP número_de_linhas * | nome_da_coluna
FROM   nome_da_tabela
WHERE  condição;

```

**EXEMPLO:**

```
-- Retornar as 5 primeiras linhas de uma tabela:
SELECT TOP 5 *
FROM   Clientes;

-- Retornar o nome e o email das 10 primeiras pessoas:
SELECT TOP 10 nome, email
FROM   Pessoas;

-- Retornar os 3 produtos mais caros:
SELECT TOP 3 *
FROM   Produtos
ORDER  BY preco DESC;

```

<br>
 
## ⌨ UTILIZANDO O COMANDO ORDER BY

O comando **ORDER BY** em bancos de dados é usado para ordenar os resultados de uma consulta **SQL**. Ele permite especificar uma ou mais colunas para ordenar os dados, tanto em ordem crescente (ASC, padrão) quanto decrescente (DESC). 

**CÓDIGO:**

```
SELECT coluna1, coluna2, ...
FROM   tabela
WHERE  condição
ORDER  BY coluna_ordenacao [ASC | DESC];

```

**EXEMPLO:**

```
-- Consulta para obter todos os produtos ordenados pelo preço em ordem crescente (do menor para o maior):
SELECT *
FROM  Produtos
ORDER BY Preco ASC;

-- Consulta para obter todos os produtos ordenados pelo nome em ordem decrescente (Z-A):
SELECT *
FROM  Produtos
ORDER BY Nome DESC;

```

<br>











