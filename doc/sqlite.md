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
5. [Consultando dados com SELECT e fetch no SQLite3](#5-consultando-dados-com-select-e-fetch-no-sqlite3)
    - 5.1. [Usando SELECT e fetchall](#51-usando-select-e-fetchall)
    - 5.2. [Usando SELECT com WHERE e fetchone](#52-usando-select-com-where-e-fetchone)
    - 5.3. [Boas Práticas para SELECT e fetch](#53-boas-práticas-para-select-e-fetch)
6. [CRUD no SQLite3: Create, Read, Update, Delete](#6-crud-no-sqlite3-create-read-update-delete)
    - 6.1. [O que é CRUD?](#61-o-que-é-crud)
    - 6.2. [DELETE no SQLite3](#62-delete-no-sqlite3)
    - 6.3. [Exemplo prático de CRUD](#63-exemplo-prático-de-crud)
    - 6.4. [Boas Práticas para DELETE](#64-boas-práticas-para-delete)
7. [Atualizando dados com UPDATE no SQLite3](#7-atualizando-dados-com-update-no-sqlite3)
    - 7.1. [O que é UPDATE?](#71-o-que-é-update)
    - 7.2. [Exemplo prático de UPDATE](#72-exemplo-prático-de-update)
    - 7.3. [Boas Práticas para UPDATE](#73-boas-práticas-para-update)

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

## 5. Consultando dados com SELECT e fetch no SQLite3

### 5.1. Usando SELECT e fetchall

```python
import sqlite3
from main import DB_FILE, TABLE_NAME

connection = sqlite3.connect(DB_FILE)
cursor = connection.cursor()

cursor.execute(
    f'SELECT * FROM {TABLE_NAME} '
)

for row in cursor.fetchall():  # fetchall retorna todas as linhas da consulta
    _id, name, weight = row
    print(f'ID: {_id}, Nome: {name}, Peso: {weight}')

cursor.close()
connection.close()
```

- O método `fetchall()` retorna uma lista de tuplas, cada tupla representa uma linha do resultado.
- Ideal para consultar vários registros de uma vez.

### 5.2. Usando SELECT com WHERE e fetchone

```python
connection = sqlite3.connect(DB_FILE)
cursor = connection.cursor()

cursor.execute(
    f'SELECT * FROM {TABLE_NAME} WHERE id = ?', (3,)
)

row = cursor.fetchone()  # fetchone retorna apenas a primeira linha da consulta
if row:
    _id, name, weight = row
    print(f'ID: {_id}, Nome: {name}, Peso: {weight}')
else:
    print('Registro não encontrado.')

cursor.close()
connection.close()
```

- O método `fetchone()` retorna apenas a primeira linha do resultado ou `None` se não houver resultado.
- Use sempre placeholders (`?`) para evitar SQL Injection.

### 5.3. Boas Práticas para SELECT e fetch

- Prefira sempre usar placeholders para valores dinâmicos em consultas.
- Use `fetchall()` para múltiplos resultados e `fetchone()` para um único registro.
- Sempre verifique se o resultado de `fetchone()` não é `None` antes de acessar os dados.
- Feche o cursor e a conexão ao final das operações.

## 6. CRUD no SQLite3: Create, Read, Update, Delete

### 6.1. O que é CRUD?

- **CRUD** é um acrônimo para as operações básicas de um banco de dados:
  - **Create**: Criar registros (INSERT)
  - **Read**: Ler registros (SELECT)
  - **Update**: Atualizar registros (UPDATE)
  - **Delete**: Excluir registros (DELETE)
- No SQL, cada operação tem um comando específico.

### 6.2. DELETE no SQLite3

#### 6.2.1. DELETE sem WHERE (Limpar tabela)

```python
cursor.execute(
    f'DELETE FROM {TABLE_NAME}'
)
cursor.execute(
    f'DELETE FROM sqlite_sequence WHERE name="{TABLE_NAME}"'
)
connection.commit()
```

- **Atenção:** Esse comando apaga todos os registros da tabela!
- O autoincremento é zerado ao apagar da `sqlite_sequence`.
- Use com cautela, principalmente em produção.

#### 6.2.2. DELETE com WHERE (Excluir registros específicos)

```python
cursor.execute(
    f'DELETE FROM {TABLE_NAME} WHERE id = ?', (3,)
)
cursor.execute(
    f'DELETE FROM {TABLE_NAME} WHERE id = ?', (1,)
)
connection.commit()
```

- O comando acima apaga apenas os registros com `id` igual a 3 e 1.
- Sempre use placeholders (`?`) para evitar SQL Injection.
- O uso do WHERE é fundamental para evitar apagar dados indevidamente.

### 6.3. Exemplo prático de CRUD

```python
import sqlite3
from pathlib import Path

ROOT_DIR = Path(__file__).parent
DB_NAME = "db.sqlite3"
DB_FILE = ROOT_DIR / DB_NAME
TABLE_NAME = 'customers'

connection = sqlite3.connect(DB_FILE)
cursor = connection.cursor()

# CREATE
sql = (
    f'INSERT INTO {TABLE_NAME}'
    '(name, weight)'
    'VALUES'
    '(:nome, :peso)'
)
cursor.execute(sql, {'nome': 'Sem nome', 'peso': 3})
cursor.executemany(sql, [
    {'nome': 'Maria', 'peso': 3},
    {'nome': 'Helena', 'peso': 2},
    {'nome': 'João', 'peso': 6},
    {'nome': 'Rafa', 'peso': 5},
])
connection.commit()

# DELETE com WHERE
cursor.execute(
    f'DELETE FROM {TABLE_NAME} WHERE id = ?', (3,)
)
cursor.execute(
    f'DELETE FROM {TABLE_NAME} WHERE id = ?', (1,)
)
connection.commit()

# READ
cursor.execute(
    f'SELECT * FROM {TABLE_NAME}'
)
for row in cursor.fetchall():
    _id, name, weight = row
    print(f'ID: {_id}, Nome: {name}, Peso: {weight}')

cursor.close()
connection.close()
```

### 6.4. Boas Práticas para DELETE

- Sempre use WHERE para deletar registros específicos.
- Nunca rode DELETE sem WHERE em produção sem ter certeza do que está fazendo.
- Use placeholders para evitar SQL Injection.
- Após deletar registros, sempre faça `commit()` para salvar as alterações.
- Se precisar zerar o autoincremento, apague da `sqlite_sequence`.
- Teste comandos em ambiente de desenvolvimento antes de rodar em produção.

## 7. Atualizando dados com UPDATE no SQLite3

### 7.1. O que é UPDATE?

- O comando **UPDATE** é usado para modificar dados já existentes em uma tabela.
- Sintaxe básica:
  ```sql
  UPDATE nome_tabela SET coluna1 = valor1, coluna2 = valor2 WHERE condição;
  ```
- O uso do WHERE é fundamental para atualizar apenas os registros desejados.

### 7.2. Exemplo prático de UPDATE

```python
import sqlite3
from pathlib import Path

ROOT_DIR = Path(__file__).parent
DB_NAME = "db.sqlite3"
DB_FILE = ROOT_DIR / DB_NAME
TABLE_NAME = 'customers'

connection = sqlite3.connect(DB_FILE)
cursor = connection.cursor()

# Atualizando o nome e peso do registro com id = 2
cursor.execute(
    f'UPDATE {TABLE_NAME} SET name = ?, weight = ? WHERE id = ?',
    ("QUALQUER", 67.89, 2)
)
connection.commit()

# Consultando para verificar a alteração
cursor.execute(
    f'SELECT * FROM {TABLE_NAME}'
)
for row in cursor.fetchall():
    _id, name, weight = row
    print(f'ID: {_id}, Nome: {name}, Peso: {weight}')

cursor.close()
connection.close()
```

- Sempre use placeholders (`?`) para evitar SQL Injection.
- O WHERE garante que apenas o registro desejado seja alterado.

### 7.3. Boas Práticas para UPDATE

- Sempre use WHERE para evitar atualizar todos os registros da tabela por engano.
- Use placeholders para maior segurança.
- Após atualizar, sempre faça `commit()` para salvar as alterações.
- Teste comandos em ambiente de desenvolvimento antes de rodar em produção.
- Consulte a [documentação oficial do SQLite3](https://docs.python.org/3/library/sqlite3.html) para recursos avançados de UPDATE.

---

