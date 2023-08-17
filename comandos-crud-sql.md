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