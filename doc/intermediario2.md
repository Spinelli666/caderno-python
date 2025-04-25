# Intermediário 2

## Sumário

1. [Introdução ao Tipo de Dados `dict` - Dicionários em Python](#1-introdução-ao-tipo-de-dados-dict---dicionários-em-python)
    - 1.1. [O Que São Dicionários?](#11-o-que-são-dicionários)
    - 1.2. [Criando Dicionários](#12-criando-dicionários)
    - 1.3. [Acessando Valores em Dicionários](#13-acessando-valores-em-dicionários)
    - 1.4. [Iterando Sobre Dicionários](#14-iterando-sobre-dicionários)
2. [Manipulando Chaves e Valores em Dicionários](#2-manipulando-chaves-e-valores-em-dicionários)
    - 2.1. [Adicionando e Atualizando Valores](#21-adicionando-e-atualizando-valores)
    - 2.2. [Removendo Chaves e Valores](#22-removendo-chaves-e-valores)
    - 2.3. [Verificando a Existência de Chaves](#23-verificando-a-existência-de-chaves)
3. [Métodos Úteis nos Dicionários Python (`dict`)](#3-métodos-úteis-nos-dicionários-python-dict)
    - 3.1. [Principais Métodos dos Dicionários](#31-principais-métodos-dos-dicionários)
    - 3.2. [Exemplos de Uso](#32-exemplos-de-uso)
4. [Shallow Copy vs Deep Copy em Dados Mutáveis](#4-shallow-copy-vs-deep-copy-em-dados-mutáveis)
    - 4.1. [O Que é Shallow Copy?](#41-o-que-é-shallow-copy)
    - 4.2. [O Que é Deep Copy?](#42-o-que-é-deep-copy)
    - 4.3. [Exemplo Prático de Shallow Copy e Deep Copy](#43-exemplo-prático-de-shallow-copy-e-deep-copy)
5. [Introdução ao Tipo `set` em Python (Conjuntos)](#5-introdução-ao-tipo-set-em-python-conjuntos)
    - 5.1. [O Que São Sets?](#51-o-que-são-sets)
    - 5.2. [Criando um Set](#52-criando-um-set)
6. [Peculiaridades do Tipo Mutável `set`](#6-peculiaridades-do-tipo-mutável-set)
7. [Métodos Úteis do Tipo `set`](#7-métodos-úteis-do-tipo-set)
8. [Operadores Importantes para o Tipo `set`](#8-operadores-importantes-para-o-tipo-set)
9. [Exemplos de Uso do Tipo `set`](#9-exemplos-de-uso-do-tipo-set)

---

## 1. Introdução ao Tipo de Dados `dict` - Dicionários em Python

Os **dicionários** em Python são estruturas de dados que armazenam pares de **chave** e **valor**. Eles são úteis para representar dados estruturados e permitem acesso rápido aos valores por meio de suas chaves.

### 1.1. O Que São Dicionários?

- Um dicionário é uma coleção de pares de **chave** e **valor**.
- As **chaves** devem ser de tipos **imutáveis** (como `str`, `int`, `float`, `bool`, `tuple`).
- Os **valores** podem ser de qualquer tipo, incluindo outros dicionários.

**Exemplo:**
```py
pessoa = {
    'nome': 'Luiz Otávio',
    'sobrenome': 'Miranda',
    'idade': 18,
    'altura': 1.8,
    'endereços': [
        {'rua': 'tal tal', 'número': 123},
        {'rua': 'outra rua', 'número': 321},
    ],
}
```

### 1.2. Criando Dicionários

Você pode criar dicionários de duas formas principais:
1. Usando as chaves `{}`.
2. Usando a classe `dict`.

**Exemplo com `{}`:**
```py
pessoa = {
    'nome': 'Luiz Otávio',
    'sobrenome': 'Miranda',
    'idade': 18,
}
```

**Exemplo com `dict`:**
```py
pessoa = dict(nome='Luiz Otávio', sobrenome='Miranda', idade=18)
```

### 1.3. Acessando Valores em Dicionários

Os valores em um dicionário podem ser acessados usando suas chaves.

**Exemplo:**
```py
pessoa = {
    'nome': 'Luiz Otávio',
    'sobrenome': 'Miranda',
    'idade': 18,
}

print(pessoa['nome'])  # Saída: Luiz Otávio
print(pessoa['sobrenome'])  # Saída: Miranda
```

**Observação:**
- Tentar acessar uma chave inexistente gera um erro `KeyError`.

### 1.4. Iterando Sobre Dicionários

Você pode iterar sobre os dicionários para acessar suas chaves e valores.

**Exemplo:**
```py
pessoa = {
    'nome': 'Luiz Otávio',
    'sobrenome': 'Miranda',
    'idade': 18,
    'altura': 1.8,
}

for chave in pessoa:
    print(chave, pessoa[chave])
```

**Saída:**
```
nome Luiz Otávio
sobrenome Miranda
idade 18
altura 1.8
```

**Explicação:**
- O laço `for` percorre as **chaves** do dicionário.
- Os valores são acessados usando `pessoa[chave]`.

**Dicas:**
- Use dicionários para representar dados estruturados, como informações de uma pessoa ou configurações de um sistema.
- Certifique-se de que as chaves sejam únicas dentro do dicionário.
- Para evitar erros ao acessar chaves inexistentes, você pode usar o método `.get()`.

---

## 2. Manipulando Chaves e Valores em Dicionários

Os dicionários em Python permitem adicionar, atualizar, remover e verificar chaves e valores de forma dinâmica. Isso os torna uma estrutura de dados muito flexível e poderosa.

---

### 2.1. Adicionando e Atualizando Valores

Você pode adicionar ou atualizar valores em um dicionário atribuindo um valor a uma chave.

**Exemplo:**
```py
pessoa = {}

# Adicionando valores
pessoa['nome'] = 'Luiz Otávio'
pessoa['sobrenome'] = 'Miranda'

print(pessoa)  # Saída: {'nome': 'Luiz Otávio', 'sobrenome': 'Miranda'}

# Atualizando valores
pessoa['nome'] = 'Maria'
print(pessoa)  # Saída: {'nome': 'Maria', 'sobrenome': 'Miranda'}
```

### 2.2. Removendo Chaves e Valores

Você pode remover chaves e seus valores associados usando a instrução `del`.

**Exemplo:**
```py
pessoa = {
    'nome': 'Maria',
    'sobrenome': 'Miranda',
}

# Removendo uma chave
del pessoa['sobrenome']
print(pessoa)  # Saída: {'nome': 'Maria'}
```

### 2.3. Verificando a Existência de Chaves

Para verificar se uma chave existe no dicionário, você pode usar o método `.get()` ou a palavra-chave `in`.

**Exemplo com `.get()`:**
```py
pessoa = {'nome': 'Maria'}

# Verificando se a chave 'sobrenome' existe
if pessoa.get('sobrenome') is None:
    print('NÃO EXISTE')  # Saída: NÃO EXISTE
else:
    print(pessoa['sobrenome'])
```

**Exemplo com `in`:**
```py
if 'sobrenome' in pessoa:
    print(pessoa['sobrenome'])
else:
    print('NÃO EXISTE')  # Saída: NÃO EXISTE
```

**Observação:**
- O método `.get()` retorna `None` se a chave não existir, enquanto acessar diretamente uma chave inexistente gera um erro `KeyError`.

**Dicas:**
- Use `del` para remover chaves que não são mais necessárias.
- Utilize `.get()` para evitar erros ao acessar chaves inexistentes.
- Dicionários são mutáveis, então tome cuidado ao manipulá-los diretamente para evitar alterações indesejadas.

---

## 3. Métodos Úteis nos Dicionários Python (`dict`)

Os dicionários em Python possuem diversos métodos úteis para manipulação de chaves e valores. Esses métodos tornam o trabalho com dicionários mais eficiente e flexível.

### 3.1. Principais Métodos dos Dicionários

| Método         | Descrição                                                                 |
|----------------|---------------------------------------------------------------------------|
| `len(d)`       | Retorna o número de chaves no dicionário.                                |
| `keys()`       | Retorna um iterável com as chaves do dicionário.                         |
| `values()`     | Retorna um iterável com os valores do dicionário.                        |
| `items()`      | Retorna um iterável com pares de chave e valor.                          |
| `setdefault()` | Adiciona uma chave com valor padrão se ela não existir.                  |
| `copy()`       | Retorna uma cópia rasa (shallow copy) do dicionário.                     |
| `get()`        | Obtém o valor de uma chave, retornando um valor padrão se ela não existir.|
| `pop()`        | Remove e retorna o valor associado a uma chave.                         |
| `popitem()`    | Remove e retorna o último par chave-valor adicionado.                   |
| `update()`     | Atualiza o dicionário com outro dicionário ou iterável de pares chave-valor.|

### 3.2. Exemplos de Uso

**Exemplo com `setdefault`:**
```py
pessoa = {'nome': 'Luiz Otávio', 'sobrenome': 'Miranda'}
pessoa.setdefault('idade', 0)
print(pessoa['idade'])  # Saída: 0
```

**Exemplo com `keys`, `values` e `items`:**
```py
pessoa = {'nome': 'Luiz Otávio', 'sobrenome': 'Miranda', 'idade': 900}
print(list(pessoa.keys()))  # Saída: ['nome', 'sobrenome', 'idade']
print(list(pessoa.values()))  # Saída: ['Luiz Otávio', 'Miranda', 900]
print(list(pessoa.items()))  # Saída: [('nome', 'Luiz Otávio'), ('sobrenome', 'Miranda'), ('idade', 900)]
```

**Exemplo com `pop` e `popitem`:**
```py
p1 = {'nome': 'Luiz', 'sobrenome': 'Miranda'}
nome = p1.pop('nome')  # Remove a chave 'nome'
print(nome)  # Saída: Luiz
print(p1)  # Saída: {'sobrenome': 'Miranda'}

ultima_chave = p1.popitem()  # Remove o último item
print(ultima_chave)  # Saída: ('sobrenome', 'Miranda')
```

**Exemplo com `update`:**
```py
p1 = {'nome': 'Luiz'}
p1.update({'idade': 30})  # Atualiza com outro dicionário
print(p1)  # Saída: {'nome': 'Luiz', 'idade': 30}

p1.update(nome='Maria', altura=1.70)  # Atualiza com argumentos nomeados
print(p1)  # Saída: {'nome': 'Maria', 'idade': 30, 'altura': 1.7}
```

---

## 4. Shallow Copy vs Deep Copy em Dados Mutáveis

Quando trabalhamos com estruturas de dados mutáveis, como listas e dicionários, é importante entender a diferença entre **shallow copy** (cópia rasa) e **deep copy** (cópia profunda).

### 4.1. O Que é Shallow Copy?

Uma **shallow copy** cria uma nova estrutura de dados, mas copia apenas as referências dos objetos internos. Isso significa que alterações em objetos mutáveis dentro da cópia também afetam o original.

**Exemplo com `copy()`:**
```py
d1 = {'c1': 1, 'c2': 2, 'l1': [0, 1, 2]}
d2 = d1.copy()  # Shallow copy

d2['c1'] = 1000  # Altera apenas a chave 'c1' em d2
d2['l1'][1] = 999  # Altera a lista interna, afetando d1

print(d1)  # Saída: {'c1': 1, 'c2': 2, 'l1': [0, 999, 2]}
print(d2)  # Saída: {'c1': 1000, 'c2': 2, 'l1': [0, 999, 2]}
```

### 4.2. O Que é Deep Copy?

Uma **deep copy** copia toda a estrutura de dados, incluindo objetos internos. Alterações na cópia não afetam o original.

**Exemplo com `copy.deepcopy()`:**
```py
import copy

d1 = {'c1': 1, 'c2': 2, 'l1': [0, 1, 2]}
d2 = copy.deepcopy(d1)  # Deep copy

d2['l1'][1] = 999  # Altera a lista interna apenas em d2

print(d1)  # Saída: {'c1': 1, 'c2': 2, 'l1': [0, 1, 2]}
print(d2)  # Saída: {'c1': 1, 'c2': 2, 'l1': [0, 999, 2]}
```

### 4.3. Exemplo Prático de Shallow Copy e Deep Copy

**Exemplo Completo:**
```py
import copy

d1 = {'c1': 1, 'c2': 2, 'l1': [0, 1, 2]}

# Shallow Copy
d2 = d1.copy()
d2['l1'][1] = 999
print('Shallow Copy:')
print('d1:', d1)  # Saída: {'c1': 1, 'c2': 2, 'l1': [0, 999, 2]}
print('d2:', d2)  # Saída: {'c1': 1, 'c2': 2, 'l1': [0, 999, 2]}

# Deep Copy
d3 = copy.deepcopy(d1)
d3['l1'][1] = 555
print('\nDeep Copy:')
print('d1:', d1)  # Saída: {'c1': 1, 'c2': 2, 'l1': [0, 999, 2]}
print('d3:', d3)  # Saída: {'c1': 1, 'c2': 2, 'l1': [0, 555, 2]}
```

---

**Dicas:**
- Use `copy()` para criar cópias rápidas quando os dados internos não forem mutáveis.
- Use `copy.deepcopy()` para evitar efeitos colaterais em estruturas de dados complexas.
- Sempre teste o comportamento de cópias ao trabalhar com dados mutáveis.

---

## 5. Introdução ao Tipo `set` em Python (Conjuntos)

Os **sets** (conjuntos) em Python são estruturas de dados baseadas no conceito matemático de conjuntos. Eles são úteis para armazenar valores únicos e realizar operações como união, interseção e diferença.

### 5.1. O Que São Sets?

- **Sets** são coleções **mutáveis** que armazenam valores **únicos**.
- Não possuem índices e não garantem ordem.
- São iteráveis e aceitam apenas valores **imutáveis** como elementos internos.

**Características:**
- Removem automaticamente valores duplicados.
- São eficientes para verificar a existência de elementos.

**Exemplo:**
```py
s1 = {1, 2, 3, 3, 3}  # Valores duplicados serão removidos
print(s1)  # Saída: {1, 2, 3}
```

### 5.2. Criando um Set

Você pode criar sets de várias formas:
1. Usando `{}` com valores separados por vírgulas.
2. Usando a função `set()` com um iterável.

**Exemplo:**
```py
# Criando sets
s1 = {1, 2, 3}  # Set com valores
s2 = set('Luiz')  # Set a partir de uma string
s3 = set()  # Set vazio

print(s1)  # Saída: {1, 2, 3}
print(s2)  # Saída: {'L', 'u', 'i', 'z'}
```

---

## 6. Peculiaridades do Tipo Mutável `set`

- **Valores únicos:** Sets não permitem valores duplicados.
- **Sem índices:** Não é possível acessar elementos diretamente por índice.
- **Sem ordem:** A ordem dos elementos não é garantida.
- **Iteráveis:** Você pode usar `for`, `in` e `not in` para iterar ou verificar a existência de elementos.

**Exemplo:**
```py
s1 = {1, 2, 3}
print(3 in s1)  # Saída: True
print(4 not in s1)  # Saída: True

for numero in s1:
    print(numero)
```

---

## 7. Métodos Úteis do Tipo `set`

| Método       | Descrição                                      |
|--------------|------------------------------------------------|
| `add`        | Adiciona um elemento ao set.                   |
| `update`     | Adiciona múltiplos elementos ao set.           |
| `clear`      | Remove todos os elementos do set.              |
| `discard`    | Remove um elemento específico, sem erro se não existir.|

**Exemplo:**
```py
s1 = set()
s1.add('Luiz')  # Adiciona um elemento
s1.update([1, 2, 3])  # Adiciona múltiplos elementos
s1.discard('Luiz')  # Remove o elemento 'Luiz'
print(s1)  # Saída: {1, 2, 3}
```

---

## 8. Operadores Importantes para o Tipo `set`

Os sets suportam operadores para realizar operações matemáticas de conjuntos.

| Operador     | Descrição                                      |
|--------------|------------------------------------------------|
| `|`          | União: Combina os elementos de dois sets.      |
| `&`          | Interseção: Elementos presentes em ambos os sets.|
| `-`          | Diferença: Elementos presentes apenas no set da esquerda.|
| `^`          | Diferença Simétrica: Elementos que não estão em ambos os sets.|

**Exemplo:**
```py
s1 = {1, 2, 3}
s2 = {2, 3, 4}

print(s1 | s2)  # União: {1, 2, 3, 4}
print(s1 & s2)  # Interseção: {2, 3}
print(s1 - s2)  # Diferença: {1}
print(s1 ^ s2)  # Diferença Simétrica: {1, 4}
```

---

## 9. Exemplos de Uso do Tipo `set`

Os sets são úteis para resolver problemas que envolvem valores únicos ou operações de conjuntos.

**Exemplo: Remover Duplicados de uma Lista**
```py
l1 = [1, 2, 3, 3, 3, 1]
s1 = set(l1)  # Remove duplicados
l2 = list(s1)  # Converte de volta para lista
print(l2)  # Saída: [1, 2, 3]
```

**Exemplo: Jogo de Letras**
```py
letras = set()
while True:
    letra = input('Digite: ')
    letras.add(letra.lower())

    if 'l' in letras:
        print('PARABÉNS')
        break

    print(letras)
```

**Explicação:**
- O set `letras` armazena as letras digitadas pelo usuário.
- O loop termina quando a letra `'l'` é encontrada.

**Dicas:**
- Use sets para eliminar duplicados de iteráveis.
- Aproveite os operadores de conjuntos para realizar operações matemáticas.
- Lembre-se de que sets não possuem ordem nem índices.

---