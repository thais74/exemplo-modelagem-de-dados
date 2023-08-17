# Comandos para operações CRUD no banco de dados

## Resumo

- C -> CREATE (inserir dados usando comandos `INSERT`) 
- R -> READ (ler dados usando comando `SELECT`)
- U -> UPDATE (atualizar dados usando comando `UPDATE`)
- D -> DELETE (deletar dados usando comando `DELETE`)

## INSERT

### Fabricantes

```sql
    INSERT INTO fabricantes (nome) VALUES('Asus'), ('Dell'), ('Apple');

    INSERT INTO fabricantes (nome) VALUES('LG'), ('Samsumg'), ('Brastmep');

    INSERT INTO fabricantes (nome) VALUES('Positivo'), ('Microsoft');

```

### Produtos
```sql
INSERT INTO produtos(nome, preco, descricao, quantidade, fabricante_id) 
VALUES(
    'Ultrabook', 
    3500,
    'Equipamento de Última geração cheio de recursos, com processador Intel Core i9 do balacobaco.',
    7,
    3 -- ID do fabricante DELL
);

INSERT INTO produtos(nome, descricao, preco, quantidade, fabricante_id) 
VALUES (
    'Tablet Android'
    'Tablet com a versão 14 do sistema operacional Android.',
    1500.99,
    5,
    5
);

INSERT INTO produtos(nome, descricao, preco, quantidade, fabricante_id) VALUES (
    'Geladeira',
    'Refrigerador frost-free com acesso á Internet.',
    5000,
    12,
    6
), (
    'iPhone 18 Pro Max',
    'Smartphone Apple cheio das frescuras e caro pra caramba',
    12666.66,
    3,
    2
), (
    'iPad Mini',
    'Tablet Apple',
    4999.99,
    8,
    2
);
```


---
### Exercício
```sql 
INSERT INTO produtos(nome, descricao, preco, quantidade, fabricante_id) VALUES (
    'Xbox Series S',
    'Velocidade e desempenho de última geração.',
    1997,
    5,
    8
), (
    'Notebook Motion',
    ' Intel Dual Core 4GB de RAM, 128GB SSD e Tela 14,1 polegadas.',
    1213.65,
    8,
    7
);
```


---
## Select

```sql
SELECT * FROM produtos;

SELECT nome, preco FROM produtos;

SELECT preco, nome FROM produtos;

SELECT nome, preco, quantidade FROM produtos WHERE preco < 5000>;

-- Mostre nome e descrição somente dos produtos da Apple

SELECT nome, preco, fabricante_id FROM produtos WHERE fabricante_id = 2 ;
```


---
### Operadores Lógicos: E, OU, NÃO

```sql
SELECT nome, preco FROM produtos WHERE preco >= 2000 AND preco <= 6000;

--A query abaixo não retorna registro já que as condições não foram atendidas
SELECT nome, preco FROM produtos WHERE preco > 5000 AND preco <= 6000;
```


#### OU
```sql
SELECT nome, preco FROM produtos WHERE preco > 5000 OR preco <= 3000;

-- Exiba nome, preco somente dos produtos da Apple e da Samsung

SELECT nome, preco FROM produtos WHERE fabricante_id = 5 OR fabricante_id = 2;

-- Versão usando função  IN()
SELECT nome, preco FROM produtos WHERE fabricante_id IN(3, 5);


-- Versão usando função NOT IN()
SELECT nome, preco FROM produtos WHERE fabricante_id NOT IN(3, 5);
```


#### NÃO
```sql
SELECT nome, descricao, preco FROM produtos WHERE NOT fabricante_id = 8;

-- Versão usando operador relacional "diferença/diferente"
SELECT nome, descricao, preco FROM produtos WHERE fabricante_id != 8;
```

## UPDATE

```sql
UPDATE fabricantes SET nome = 'Asus do Brasil' WHERE id = 1; -- NÃO SE ESQUECE DO WHERE!!

UPDATE produtos SET preco = 6579.74 WHERE id = 4;


-- Altere a quantidade dos produtos da Apple e da Samsung para 20

UPDATE produtos SET quantidade = 20 WHERE fabricante_id IN(3, 5);

```

--- 
## DELETE

```sql
DELETE FROM fabricantes WHERE id = 1;
DELETE FROM fabricantes WHERE id = 4;


-- A query abaixo não funcionará devido á restrição de chave estrangeira/relacionamento,
-- ou seja, existem produtos associados ao fabricante 3 (apple)
-- DELETE FROM fabricantes WHERE id = 3;
```

## SELECT: outras formas de uso

```sql
SELECT nome, preco FROM produtos ORDER BY nome;
SELECT nome, preco FROM produtos ORDER BY preco;
SELECT nome, preco FROM produtos ORDER BY preco DESC;

-- DESC: classificação em ordem decrescente
-- ASC (padrão): classificação em ordem crescente
```

### Busca de dados
```sql
SELECT nome, descricao FROM produtos WHERE descricao LIKE '%tablet';
-- Usamos o operador LIKE e o caractere coringa % para permitir 
-- uma busca da palavra indicada em qualquer posição da palavra indicada em qualquer posição dentro do texto. Neste contexto, o % significa 'qualquer texto' antes ou depois da palavra
```

### Operações e funções de agregação

```sql
SELECT SUM(preco) FROM produtos; -- Soma
SELECT SUM(preco) as Total FROM produtos; -- alias/apedido

SELECT nome as Produto, preco as "Preço" FROM produtos;
SELECT nome Produto, preco "Preço" FROM produtos;

-- MÉDIA
SELECT AVG(preco) as "Média dos Preços" FROM produtos;
SELECT ROUND(AVG(preco)) as "Média dos Preços" FROM produtos;

SELECT COUNT(id) as "Qtd de Produtos" FROM produtos;

SELECT COUNT(DISTINCT fabricante_id) as "Qtd de fabricantes com Produtos" FROM produtos;

```

### Operações matemáticas
```sql
SELECT nome, preco, quantidade, (preco * quantidade) as Total FROM produtos
```

### Segmentação/Agrupamento de resultados

```sql

SELECT fabricante_id, SUM(preco) FROM produtos GROUP BY fabricante_id;

```
