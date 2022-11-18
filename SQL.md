# **Criação de Tabela**

CREATE TABLE *NOMETABELA* (       -- Declaração de tabela
COLUNA1 *TIPODEDADOS* **RESTRIÇÃO**,
COLUNAN *TIPODEDADOS* **RESTRIÇÃO**,
CONSTRAINT *NOMECONSTRAINT* PRIMARY KEY (COLUNA),
FOREIGN KEY (*COLUNA*) REFERENCES *NOMETABELA* (*COLUNA*)
);
ou
CREATE TABLE *NOMETABELA* (       -- Declaração de tabela
COLUNA1 *TIPODEDADOS* **RESTRIÇÃO** PRIMARY KEY,
COLUNAN *TIPODEDADOS* **RESTRIÇÃO**,
);
ALTER TABLE *NOMETABELA* ADD FOREIGN KEY (*COLUNA*) REFERENCES *NOMETABELA* **ON UPDATE** CASCADE **ON DELETE** CASCADE ;

 - NULL (ou vazio) - Valor Anulavel
 - NOT NULL - Valor não nulo
 - UNIQUE - Valor de ocorrência única.
 - **ON UPDATE** CASCADE  - Vai atualizar o registro das chave estrangeiras quando houver update de uma chave referenciada
 - **ON DELETE** CASCADE - Vai Apagar o registro das chave estrangeiras quando uma linha referenciada for deletada

**Tabela a partir de Consulta**

CREATE TABLE *NOMETABELA* AS **(CONSULTA)**


# **Alteração de Tabela**
**Adicionando Coluna**
ALTER TABLE *NOMETABELA* ADD *COLUNA TIPODEDADOS* ;

**Removendo Coluna**
ALTER TABLE *NOMETABELA* DROP *COLUNA* ;

**Remover Tabela**
DROP TABLE *NOMETABELA*

**Inserir linhas em tabelas**
INSERT INTO *NOMETABELA* (COLUNA1, COLUNA2, COLUNAn) VALUES (VALOR1, VALOR2, VALORn)
ou
INSERT INTO *NOMETABELA* VALUES (VALOR1, VALOR2, VALORn) --todas os valores da coluna

**Atualização de linhas**
UPDATE *NOMETABELA*
SET *COLUNA1*=*VALOR1*, *COLUNA2*=*VALOR2*,…,*COLUNAn*=*VALORn*
WHERE *CONDIÇÃO*;

**Remoção de linhas**
DELETE FROM *NOMETABELA*
WHERE *CONDIÇÃO*;

**SELECT** define as colunas a serem exibidas após a consulta (ATRIBUTO)
**FROM** define a tabela a ser consultada (ENTIDADE)
**WHERE** adiciona condição de fintro para o que será processado (FILTRO DE ATRIBUTO)

-- "Comentário no SQL"

**FROM**
 - **JOIN** - comando utilizado em junções

Executando no PSQL
\c *nomedatabase*- se conecta ao banco de dados para começar a construi-lo (usar tudo minusculo)

# TRANSAÇÕES
BEGIN-- início da transação
-- comandos
COMMIT-- transação confirmada
ROLLBACK-- transação cancelada
END-- mesma função do COMMIT

# PSQL
\dt - dentro do banco atual, lista as tabelas criadas
\l  - lista os bancos de dados criados

# SELECT (Consultas) 
Formatações Básicas

## Renomear
SELECT CODIGOALUNO AS "Matrícula", -- Codigo aluno renomeado como Matricula
        NOME AS "Nome do discente", -- COLUNA AS "NOME NOVO DA COLUNA"
        DTNASCIMENTO AS "Data de nascimento"
FROM ALUNO;

## Funções de data e hora
SELECT CURRENT_DATE AS "Data Atual", --Data retirada do sistema
        CURRENT_TIME AS "Hora Atual", -- Hora retirada do sistema
        CURRENT_TIMESTAMP "Data e Hora atuais", -- Data e hora retiradas do sistema

        EXTRACT( DOW FROM CURRENT_DATE) AS "Dia da semana", -- DOW 0 - domingo, 1 - segunda, ..., 6 - sábado

        EXTRACT( DAY FROM CURRENT_DATE) AS "Dia Atual",
        EXTRACT( DOY FROM CURRENT_DATE) AS "Dia do ano",
        EXTRACT( MONTH FROM CURRENT_DATE) AS "Mês Atual",
        EXTRACT( YEAR FROM CURRENT_DATE) AS "Ano Atual",
        EXTRACT( CENTURY FROM CURRENT_DATE) AS "Século Atual";

EXTRACT Cria uma coluna a partir de algo no parenteses ()

Função | Retorno
---:|:---
CURRENT_DATE | Dia Atual
CURRENT_TIME | Hora Atual
CURRENT_TIMESTAMP | Data e Hora atuais
(**DOY** FROM (COLUNA)/CURRENT_*) | Dia da semana sistema
(**DAY** FROM (COLUNA)/CURRENT_*) | Dia Atual sistema
(**DOY** FROM (COLUNA)/CURRENT_*) | Dia do ano sistema 
(**MONTH** FROM (COLUNA)/CURRENT_*) | Mês Atual
(**YEAR** FROM (COLUNA)/CURRENT_*) | Ano Atual
(**CENTURY** FROM (COLUNA)/CURRENT_*) | Século Atual

## Resumo/Agregação

Função | O que retorna?
---:||:---
COUNT(*) | número de linhas da consulta
MIN(COLUNA/EXPRESSÃO) | menor de uma coluna ou expressão
AVG(COLUNA/EXPRESSÃO) | valor médio da coluna ou expressão
MAX(COLUNA/EXPRESSÃO) | maior valor de uma coluna ou expressão
SUM(COLUNA/EXPRESSÃO) | soma dos valores de uma coluna ou expressão
STDDEV(COLUNA/EXPRESSÃO) | desvio padrão dos valores de uma coluna ou expressão
VARIANCE(COLUNA/EXPRESSÃO) | variância dos valores de uma coluna ou expressão

# SELECT com FROM/WHERE/ORDER BY (Consultas com condições)

SELECT COLUNA1 [[AS] APELIDOCOLUNA1],
        COLUNA2 [[AS] APELIDOCOLUNA2],
        …
        COLUNAN [[AS] APELIDOCOLUNAN]
FROM TABELA
WHERE <CONDIÇÃO>
ORDER BY EXPRESSÃO1[ASC|DESC] [NULLS {FIRST|LAST}], 
        [EXPRESSÃO2[ASC|DESC] [NULLS {FIRST|LAST}…];


# Grupos

## DISTINCT
 - Bom para verificar valores não repetidos em uma coluna

SELECT DISTINCT *COLUNA1* FROM *TABELA*;

## GROUP BY
- Bom para verificar valores não repetidos em uma coluna
- Associado a funções de agregação: COUNT, MIN, MAX e AVG

SELECT *COLUNA1* FROM *TABELA* GROUP BY *COLUNA1*;
SELECT *COLUNA2*, COUNT(*) FROM *TABELA* GROUP BY *COLUNA2*;

## Agrupamento com SELECT

SELECT
    (SELECT COUNT(*) AS "M" FROM FUNCIONARIO WHERE SEXO = 'M'),
    (SELECT COUNT(*) AS "F" FROM FUNCIONARIO WHERE SEXO = 'F');


# Varias Tabelas

## Produto Cartesiano (junção simples de tabelas)

SELECT *COLUNA1,COLUNA2...COLUNAN* FROM *TABELA1*, *TABELA2*;

SELECT *COLUNA1,COLUNA2...COLUNAN* FROM *TABELA1* CROSS JOIN *TABELA2*; --ANSI

## Junção Interna

SELECT * FROM *TABELA1* [INNER] JOIN *TABELA2* ON (CONDIÇÃOJUNÇÃO)

SELECT * FROM *TABELA1* [INNER] JOIN *TABELA2* USING (COLUNA_DE_JUNÇÃO)

SELECT * FROM *TABELA1* NATURAL JOIN *TABELA2*;

## Junção Externa

SELECT * FROM *TABELA1* [LEFT / RIGHT / FULL OUTER] JOIN *TABELA2* ON (CONDIÇÃOJUNÇÃO)

SELECT * FROM *TABELA1* [LEFT / RIGHT / FULL OUTER] JOIN *TABELA2* USING (COLUNA_DE_JUNÇÃO)

