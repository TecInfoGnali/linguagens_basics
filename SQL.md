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