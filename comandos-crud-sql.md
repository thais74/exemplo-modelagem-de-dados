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
    'Geladeira'
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