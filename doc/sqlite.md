# SQLite3 - Banco de Dados Local em Python

## Sumário

1. [Criando sua primeira tabela no SQLite3](#1-criando-sua-primeira-tabela-no-sqlite3)
    - 1.1. [Conectando ao banco de dados](#11-conectando-ao-banco-de-dados)
    - 1.2. [Criando a tabela](#12-criando-a-tabela)
2. [Inserindo valores (INSERT INTO)](#2-inserindo-valores-insert-into)
    - 2.1. [Usando placeholders para maior segurança (bindings)](#21-usando-placeholders-para-maior-segurança-bindings)
3. [DELETE sem WHERE e zerando a sqlite_sequence](#3-delete-sem-where-e-zerando-a-sqlite_sequence)
    - 3.1. [Cuidado ao usar DELETE sem WHERE](#31-cuidado-ao-usar-delete-sem-where)
    - 3.2. [Zerando o autoincremento da tabela](#32-zerando-o-autoincremento-da-tabela)
    - 3.3. [Boas Práticas e Dicas de Segurança](#33-boas-práticas-e-dicas-de-segurança)
4. [Inserindo vários valores com executemany](#4-inserindo-vários-valores-com-executemany)
    - 4.1. [Usando executemany com tuplas (placeholders)](#41-usando-executemany-com-tuplas-placeholders)
    - 4.2. [Usando execute e executemany com dicionários](#42-usando-execute-e-executemany-com-dicionários)
    - 4.3. [Boas Práticas para inserção de múltiplos valores](#4-boas-práticas-para-inserção-de-múltiplos-valores)

---

## 1. Criando sua primeira tabela no SQLite3

### 1.1. Conectando ao banco de dados

```python
import sqlite3
from pathlib import Path

ROOT_DIR = Path(__file__).parent
DB_NAME = "db.sqlite3"
DB_FILE = ROOT_DIR / DB_NAME

connection = sqlite3.connect(DB_FILE)
cursor = connection.cursor()  # Executa comandos SQL
```

### 1.2. Criando a tabela

```python
TABLE_NAME = 'customers'

cursor.execute(
    f'CREATE TABLE IF NOT EXISTS {TABLE_NAME}'
    '('
    'id INTEGER PRIMARY KEY AUTOINCREMENT,'
    'name TEXT,'
    'weight REAL'
    ')'
)
connection.commit()
```

- **`id INTEGER PRIMARY KEY AUTOINCREMENT`**: Cria uma chave primária única e autoincrementada.
- **`name TEXT`**: Coluna para nomes (texto).
- **`weight REAL`**: Coluna para peso (número decimal).

## 2. Inserindo valores (INSERT INTO)

```python
sql = (
    f'INSERT INTO {TABLE_NAME}'
    '(name, weight)'
    'VALUES'
    '(?, ?)'
)

cursor.execute(sql, ['Joana', 4])
connection.commit()
print(sql)
```

### 2.1. Usando placeholders para maior segurança (bindings)

- Os símbolos `?` são chamados de **placeholders** ou **bindings**.
- Eles evitam SQL Injection, pois o SQLite trata os valores como dados, não como comandos.
- Sempre use placeholders ao inserir dados vindos do usuário!

## 3. DELETE sem WHERE e zerando a sqlite_sequence

### 3.1. Cuidado ao usar DELETE sem WHERE

```python
cursor.execute(
    f'DELETE FROM {TABLE_NAME}'
)
connection.commit()
```

- **Atenção:** Esse comando apaga todos os registros da tabela!
- Use com cautela, principalmente em produção.

### 3.2. Zerando o autoincremento da tabela

```python
cursor.execute(
    f'DELETE FROM sqlite_sequence WHERE name="{TABLE_NAME}"'
)
connection.commit()
```

- Isso zera o contador de autoincremento da tabela, fazendo o próximo registro começar do 1 novamente.

### 3.3. Boas Práticas e Dicas de Segurança

- Sempre feche o cursor e a conexão ao final:

```python
cursor.close()
connection.close()
```

- Prefira sempre usar placeholders (`?`) para evitar SQL Injection.
- Nunca use DELETE sem WHERE em produção sem ter certeza do que está fazendo.
- Use `CREATE TABLE IF NOT EXISTS` para evitar erros ao criar tabelas já existentes.
- Teste comandos em um banco de dados de desenvolvimento antes de rodar em produção.
- Consulte a [documentação oficial do SQLite3](https://docs.python.org/3/library/sqlite3.html) para recursos avançados.

## 4. Inserindo vários valores com executemany

### 4.1. Usando executemany com tuplas (placeholders)

```python
sql = (
    f'INSERT INTO {TABLE_NAME}'
    '(name, weight)'
    'VALUES'
    '(?, ?)'
)

# Inserindo vários registros de uma vez
cursor.executemany(
    sql,
    [
        ('Joana', 4),
        ('Luiz', 5),
        ('Maria', 3)
    ]
)
connection.commit()
```

- O método `executemany` executa o mesmo comando SQL para cada tupla da lista.
- Muito útil para inserir grandes volumes de dados de forma eficiente.

### 4.2. Usando execute e executemany com dicionários

Você pode usar dicionários para nomear os parâmetros, tornando o código mais legível e seguro:

```python
sql_dict = (
    f'INSERT INTO {TABLE_NAME}'
    '(name, weight)'
    'VALUES'
    '(:nome, :peso)'
)

# Inserindo um registro com dicionário
cursor.execute(sql_dict, {'nome': 'Sem nome', 'peso': 3})

# Inserindo vários registros com lista de dicionários
cursor.executemany(sql_dict, [
    {'nome': 'Maria', 'peso': 3},
    {'nome': 'Helena', 'peso': 2},
    {'nome': 'João', 'peso': 6},
    {'nome': 'Rafa', 'peso': 5},
])
connection.commit()
```

- Os nomes dos parâmetros no SQL devem começar com `:` (ex: `:nome`, `:peso`).
- O uso de dicionários facilita a manutenção e evita erros de ordem dos parâmetros.

### 4.3. Boas Práticas para inserção de múltiplos valores

- Prefira `executemany` para inserir vários registros de uma vez, pois é mais rápido e eficiente.
- Use dicionários para maior clareza e segurança, principalmente em códigos grandes.
- Sempre faça `commit()` após inserções para garantir que os dados sejam salvos.
- Teste comandos com poucos registros antes de inserir grandes volumes.
- Consulte a [documentação oficial do SQLite3](https://docs.python.org/3/library/sqlite3.html) para mais detalhes sobre parâmetros e métodos.

---