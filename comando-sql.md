# Comandos SQL - Referências

## Modelagem Física com comandos DDL

### Criar banco de dados

CREATE DATABASE vendas CHARACTER SET utf8mb4;

### Criar tabela de fabricantes

```sql
CREATE TABLE fabricantes (
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(45) NOT NULL
);
```

### Visualizar detalhes estruturais da tabela

```sql
desc fabricantes;
```


### Criar tabela de produtos

```sql
CREATE TABLE produtos (
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(45) NOT NULL,
    descricao TEXT(500) NULL,
    preco DECIMAL(6,2) NOT NULL,
    fabricante_id INT NOT NULL
);
```

### Criação do relacionamento entre as tabelas (chave estrangeira)

```sql
ALTER TABLE produtos
    -- CONSTRAINT/RESTRIÇÃO indicando o nome do relacionamento
    add CONSTRAINT fk_produtos_fabricantes

    -- Criando a chave estrangeira (fabricante_id) que aponta para a chave primária (id) de outra tabela (fabricantes)
    FOREIGN KEY (fabricante_id) REFERENCES fabricantes(id);

```

### Exemplos de alterações estruturais na tabela

#### Renomear tabela

```sql
ALTER TABLE fabricantes RENAME TO fornecedores;
ALTER TABLE fornecedores RENAME TO fabricantes;
```

#### Modificar colunas
```sql
ALTER TABLE produtos
    MODIFY COLUMN preco INT NULL;

ALTER TABLE produtos
    MODIFY COLUMN preco DECIMAL(6,2) NOT NULL;    
```

#### Renomear colunas

```sql
ALTER TABLE fabricantes
    CHANGE nome nome_do_fabricante VARCHAR(20) NOT NULL;

ALTER TABLE fabricantes
    CHANGE noome_do_fabricante nome VARCHAR(45) NOT NULL;    
```

#### Adicionar coluna

```sql
ALTER TABLE produtos
    ADD quantidades INT NULL AFTER preco;

```