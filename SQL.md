**Criação de Tabela**

CREATE TABLE *NOMETABELA* (       -- Declaração de tabela
COLUNA1 *TIPODEDADOS* **RESTRIÇÃO**,
COLUNAN *TIPODEDADOS* **RESTRIÇÃO**,
CONSTRAINT *NOMECONSTRAINT* PRIMARY KEY (COLUNA),
FOREIGN KEY (*COLUNA*) REFERENCES *NOMETABELA* (*COLUNA*)
);
 - NULL - Valor Anulavel
 - NOT NULL - Valor não nulo
 - UNIQUE - Valor de ocorrência única.

**Alteração de Tabela**
**Adicionando Coluna**
ALTER TABLE *NOMETABELA* ADD *COLUNA TIPODEDADOS* ;

**Removendo Coluna**
ALTER TABLE *NOMETABELA* DROP *COLUNA* ;

**Remover Tabela**
DROP TABLE *NOMETABELA*





**SELECT** define as colunas a serem exibidas após a consulta (ATRIBUTO)
**FROM** define a tabela a ser consultada (ENTIDADE)
**WHERE** adiciona condição de fintro para o que será processado (FILTRO DE ATRIBUTO)

-- "Comentário no SQL"

**FROM**
 - **JOIN** - comando utilizado em junções

Executando no PSQL
\c *nomedatabase*- se conecta ao banco de dados para começar a construi-lo (usar tudo minusculo)