# Intermediário 3

## Sumário

1. [Introdução à Função `lambda` (Função Anônima de Uma Linha)](#1-introdução-à-função-lambda-função-anônima-de-uma-linha)
    - 1.1. [O Que é uma Função `lambda`?](#11-o-que-é-uma-função-lambda)
    - 1.2. [Criando Funções `lambda`](#12-criando-funções-lambda)
    - 1.3. [Exemplo Prático com `lambda`](#13-exemplo-prático-com-lambda)
2. [Funções Lambda Complexas (Para Entendimento)](#1-funções-lambda-complexas-para-entendimento)
    - 2.1. [Funções Lambda com Retorno de Outra Função](#21-funções-lambda-com-retorno-de-outra-função)
    - 2.2. [Funções Lambda com Múltiplos Argumentos](#22-funções-lambda-com-múltiplos-argumentos)
    - 2.3. [Funções Lambda com `*args`](#23-funções-lambda-com-args)
3. [Empacotamento e Desempacotamento de Dicionários](#3-empacotamento-e-desempacotamento-de-dicionários)
    - 3.1. [Troca de Valores com Empacotamento](#31-troca-de-valores-com-empacotamento)
    - 3.2. [Desempacotamento de Dicionários](#32-desempacotamento-de-dicionários)
4. [Uso de `*args` e `**kwargs`](#4-uso-de-args-e-kwargs)
    - 4.1. [O Que São `*args` e `**kwargs`](#41-o-que-são-args-e-kwargs)
    - 4.2. [Exemplo Prático com `*args` e `**kwargs`](#42-exemplo-prático-com-args-e-kwargs)
5. [Introdução à List Comprehension em Python](#5-introdução-à-list-comprehension-em-python)
    - 5.1. [O Que é List Comprehension?](#51-o-que-é-list-comprehension)
    - 5.2. [Criando Listas com List Comprehension](#52-criando-listas-com-list-comprehension)
    - 5.3. [Exemplo Prático](#53-exemplo-prático)
6. [Mapeamento de Dados em List Comprehension](#6-mapeamento-de-dados-em-list-comprehension)
    - 6.1. [O Que é Mapeamento de Dados?](#61-o-que-é-mapeamento-de-dados)
    - 6.2. [Mapeamento com List Comprehension](#62-mapeamento-com-list-comprehension)
    - 6.3. [Exemplo Prático com Condições](#63-exemplo-prático-com-condições)
7. [Filtro de Dados em List Comprehension (`filter`)](#7-filtro-de-dados-em-list-comprehension-filter)
    - 7.1. [O Que é Filtro de Dados?](#71-o-que-é-filtro-de-dados)
    - 7.2. [Filtrando Dados com List Comprehension](#72-filtrando-dados-com-list-comprehension)
    - 7.3. [Exemplo Prático com Condições](#73-exemplo-prático-com-condições)
8. [List Comprehension com Mais de Um `for`](#8-list-comprehension-com-mais-de-um-for)
    - 8.1. [O Que é List Comprehension com Múltiplos `for`?](#81-o-que-é-list-comprehension-com-múltiplos-for)
    - 8.2. [Criando Listas com Múltiplos `for`](#82-criando-listas-com-múltiplos-for)
    - 8.3. [Exemplo Prático com Múltiplos `for`](#83-exemplo-prático-com-múltiplos-for)
9. [Dictionary Comprehension e Set Comprehension](#9-dictionary-comprehension-e-set-comprehension)
    - 9.1. [O Que é Dictionary Comprehension?](#91-o-que-é-dictionary-comprehension)
    - 9.2. [O Que é Set Comprehension?](#92-o-que-é-set-comprehension)
    - 9.3. [Exemplos Práticos](#93-exemplos-práticos)

---

## 1. Introdução à Função `lambda` (Função Anônima de Uma Linha)

As funções **`lambda`** em Python são funções anônimas que podem ser definidas em uma única linha. Elas são úteis para criar funções rápidas e simples, especialmente quando usadas como argumentos para outras funções.

### 1.1. O Que é uma Função `lambda`?

- Uma função `lambda` é uma função anônima, ou seja, não possui um nome explícito.
- Contém apenas uma única expressão, que é avaliada e retornada.
- É ideal para casos onde uma função simples é necessária temporariamente.

**Sintaxe:**
```py
lambda argumentos: expressão
```

**Exemplo:**
```py
soma = lambda x, y: x + y
print(soma(2, 3))  # Saída: 5
```

### 1.2. Criando Funções `lambda`

As funções `lambda` podem ser usadas para substituir funções normais em casos simples.

**Exemplo com Função Normal:**
```py
def soma(x, y):
    return x + y

print(soma(2, 3))  # Saída: 5
```

**Exemplo com `lambda`:**
```py
soma = lambda x, y: x + y
print(soma(2, 3))  # Saída: 5
```

### 1.3. Exemplo Prático com `lambda`

As funções `lambda` são frequentemente usadas com funções como `sorted`, `map`, e `filter`.

**Exemplo com `sorted`:**
```py
lista = [
    {'nome': 'Luiz', 'sobrenome': 'Miranda'},
    {'nome': 'Maria', 'sobrenome': 'Oliveira'},
    {'nome': 'Daniel', 'sobrenome': 'Silva'},
    {'nome': 'Eduardo', 'sobrenome': 'Moreira'},
    {'nome': 'Aline', 'sobrenome': 'Souza'},
]

# Ordenando por 'nome'
l1 = sorted(lista, key=lambda item: item['nome'])

# Ordenando por 'sobrenome'
l2 = sorted(lista, key=lambda item: item['sobrenome'])

# Função para exibir a lista
def exibir(lista):
    for item in lista:
        print(item)
    print()

exibir(l1)
exibir(l2)
```

**Saída:**
```
{'nome': 'Aline', 'sobrenome': 'Souza'}
{'nome': 'Daniel', 'sobrenome': 'Silva'}
{'nome': 'Eduardo', 'sobrenome': 'Moreira'}
{'nome': 'Luiz', 'sobrenome': 'Miranda'}
{'nome': 'Maria', 'sobrenome': 'Oliveira'}

{'nome': 'Eduardo', 'sobrenome': 'Moreira'}
{'nome': 'Luiz', 'sobrenome': 'Miranda'}
{'nome': 'Maria', 'sobrenome': 'Oliveira'}
{'nome': 'Daniel', 'sobrenome': 'Silva'}
{'nome': 'Aline', 'sobrenome': 'Souza'}
```

**Explicação:**
- A função `sorted` usa a função `lambda` para determinar a chave de ordenação.
- No primeiro caso, a lista é ordenada pelo campo `'nome'`.
- No segundo caso, a lista é ordenada pelo campo `'sobrenome'`.

**Dicas:**
- Use `lambda` para funções simples e temporárias.
- Para funções mais complexas, prefira usar `def` para melhorar a legibilidade.
- Combine `lambda` com funções como `sorted`, `map`, e `filter` para manipulação eficiente de dados.

---

## 2. Funções Lambda Complexas (Para Entendimento)

As funções **lambda** podem ser usadas para criar expressões mais complexas, como funções que retornam outras funções, funções com múltiplos argumentos e funções que utilizam `*args`. Esses exemplos ajudam a entender o poder e a flexibilidade das funções lambda.

### 2.1. Funções Lambda com Retorno de Outra Função

Uma função lambda pode retornar outra função, permitindo a criação de closures ou funções dinâmicas.

**Exemplo:**
```py
def executa(funcao, *args):
    return funcao(*args)

# Criando uma função que duplica valores usando lambda
duplica = executa(
    lambda m: lambda n: n * m,  # Lambda que retorna outra lambda
    2  # Multiplicador
)

print(duplica(2))  # Saída: 4
```

**Explicação:**
- A função `executa` recebe uma função e seus argumentos.
- A lambda `lambda m: lambda n: n * m` cria uma função que multiplica um número (`n`) por um multiplicador (`m`).
- O valor `2` é passado como argumento para `m`, criando uma função que duplica valores.

### 2.2. Funções Lambda com Múltiplos Argumentos

As funções lambda podem receber múltiplos argumentos e realizar operações com eles.

**Exemplo:**
```py
print(
    executa(
        lambda x, y: x + y,  # Lambda que soma dois números
        2, 3  # Argumentos para x e y
    )
)  # Saída: 5
```

**Explicação:**
- A lambda `lambda x, y: x + y` soma dois números.
- Os valores `2` e `3` são passados como argumentos para `x` e `y`.

### 2.3. Funções Lambda com `*args`

As funções lambda podem usar `*args` para aceitar uma quantidade variável de argumentos.

**Exemplo:**
```py
print(
    executa(
        lambda *args: sum(args),  # Lambda que soma todos os argumentos
        1, 2, 3, 4, 5, 6, 7  # Argumentos para somar
    )
)  # Saída: 28
```

**Explicação:**
- A lambda `lambda *args: sum(args)` soma todos os valores passados como argumentos.
- Os valores `1, 2, 3, 4, 5, 6, 7` são passados como `*args`.

**Dicas:**
- Use lambdas para criar funções rápidas e temporárias.
- Combine lambdas com funções de ordem superior, como `executa`, para maior flexibilidade.
- Para funções mais complexas, considere usar `def` para melhorar a legibilidade.

---

## 3. Empacotamento e Desempacotamento de Dicionários

O empacotamento e desempacotamento de dicionários em Python permite combinar ou dividir dicionários de forma eficiente, além de facilitar a manipulação de seus dados.

### 3.1. Troca de Valores com Empacotamento

O empacotamento pode ser usado para trocar valores entre variáveis de forma simples.

**Exemplo:**
```py
a, b = 1, 2
a, b = b, a
print(a, b)  # Saída: 2 1
```

### 3.2. Desempacotamento de Dicionários

Você pode desempacotar dicionários usando `**` para combinar ou acessar seus valores.

**Exemplo:**
```py
pessoa = {
    'nome': 'Aline',
    'sobrenome': 'Souza',
}

dados_pessoa = {
    'idade': 16,
    'altura': 1.6,
}

# Combinando dicionários
pessoa_completa = {**pessoa, **dados_pessoa}
print(pessoa_completa)
# Saída: {'nome': 'Aline', 'sobrenome': 'Souza', 'idade': 16, 'altura': 1.6}
```

**Iterando sobre um dicionário:**
```py
for chave, valor in pessoa.items():
    print(chave, valor)
# Saída:
# nome Aline
# sobrenome Souza
```

## 4. Uso de `*args` e `**kwargs`

Os `*args` e `**kwargs` são usados em funções para capturar argumentos não nomeados e nomeados, respectivamente.

### 4.1. O Que São `*args` e `**kwargs`

- **`*args`:** Captura argumentos não nomeados como uma tupla.
- **`**kwargs`:** Captura argumentos nomeados (keyword arguments) como um dicionário.

**Exemplo com `*args`:**
```py
def soma(*args):
    return sum(args)

print(soma(1, 2, 3, 4))  # Saída: 10
```

**Exemplo com `**kwargs`:**
```py
def exibir_dados(**kwargs):
    for chave, valor in kwargs.items():
        print(f'{chave}: {valor}')

exibir_dados(nome='Joana', idade=25)
# Saída:
# nome: Joana
# idade: 25
```

### 4.2. Exemplo Prático com `*args` e `**kwargs`

**Função com `*args` e `**kwargs`:**
```py
def mostro_argumentos_nomeados(*args, **kwargs):
    print('NÃO NOMEADOS:', args)

    for chave, valor in kwargs.items():
        print(chave, valor)

configuracoes = {
    'arg1': 1,
    'arg2': 2,
    'arg3': 3,
    'arg4': 4,
}

mostro_argumentos_nomeados(10, 20, **configuracoes)
```

**Saída:**
```
NÃO NOMEADOS: (10, 20)
arg1 1
arg2 2
arg3 3
arg4 4
```

**Explicação:**
- Os valores `10` e `20` são capturados como `*args`.
- O dicionário `configuracoes` é desempacotado e seus valores são capturados como `**kwargs`.

**Dicas:**
- Use `*args` para capturar múltiplos argumentos não nomeados.
- Use `**kwargs` para capturar argumentos nomeados dinâmicos.
- Combine `*args` e `**kwargs` para criar funções flexíveis e reutilizáveis.

---

## 5. Introdução à List Comprehension em Python

A **List Comprehension** é uma forma concisa e eficiente de criar listas a partir de iteráveis, como listas, tuplas, ou ranges. Ela permite que você crie listas em uma única linha de código, substituindo loops `for` simples.

### 5.1. O Que é List Comprehension?

- É uma sintaxe simplificada para criar listas.
- Substitui loops `for` simples usados para preencher listas.
- Pode incluir condições para filtrar os elementos.

**Sintaxe Básica:**
```py
[expressão for item in iterável]
```

**Exemplo:**
```py
lista = [numero for numero in range(10)]
print(lista)  # Saída: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

### 5.2. Criando Listas com List Comprehension

Você pode usar List Comprehension para criar listas de forma mais compacta.

**Exemplo com Loop Tradicional:**
```py
lista = []
for numero in range(10):
    lista.append(numero)
print(lista)  # Saída: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

**Exemplo com List Comprehension:**
```py
lista = [numero for numero in range(10)]
print(lista)  # Saída: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

**Multiplicando Elementos:**
```py
lista = [numero * 2 for numero in range(10)]
print(lista)  # Saída: [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
```

### 5.3. Exemplo Prático

**Criando uma Lista de Números ao Quadrado:**
```py
quadrados = [numero ** 2 for numero in range(10)]
print(quadrados)  # Saída: [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

**Filtrando Elementos com Condição:**
```py
pares = [numero for numero in range(10) if numero % 2 == 0]
print(pares)  # Saída: [0, 2, 4, 6, 8]
```

**Combinando Operações e Condições:**
```py
resultado = [numero * 2 for numero in range(10) if numero % 2 == 0]
print(resultado)  # Saída: [0, 4, 8, 12, 16]
```

**Dicas:**
- Use List Comprehension para simplificar loops que criam listas.
- Adicione condições para filtrar elementos diretamente na expressão.
- Para operações mais complexas, prefira usar loops tradicionais para melhorar a legibilidade.

---

## 6. Mapeamento de Dados em List Comprehension

O **mapeamento de dados** em Python é o processo de transformar ou modificar elementos de um iterável, como listas ou dicionários. Com **List Comprehension**, é possível realizar esse mapeamento de forma concisa e eficiente.

### 6.1. O Que é Mapeamento de Dados?

- O mapeamento de dados consiste em aplicar uma transformação a cada elemento de um iterável.
- Pode ser usado para alterar valores, adicionar novos campos ou filtrar elementos.

**Exemplo Simples:**
```py
numeros = [1, 2, 3, 4, 5]
dobrados = [numero * 2 for numero in numeros]
print(dobrados)  # Saída: [2, 4, 6, 8, 10]
```

### 6.2. Mapeamento com List Comprehension

Com **List Comprehension**, é possível mapear dados diretamente em uma única linha de código.

**Exemplo com Dicionários:**
```py
produtos = [
    {'nome': 'p1', 'preco': 20},
    {'nome': 'p2', 'preco': 10},
    {'nome': 'p3', 'preco': 30},
]

# Atualizando o preço dos produtos
novos_produtos = [
    {**produto, 'preco': produto['preco'] * 1.05}
    for produto in produtos
]

print(*novos_produtos, sep='\n')
```

**Saída:**
```
{'nome': 'p1', 'preco': 21.0}
{'nome': 'p2', 'preco': 10.5}
{'nome': 'p3', 'preco': 31.5}
```

### 6.3. Exemplo Prático com Condições

Você pode adicionar condições ao mapeamento para aplicar transformações seletivamente.

**Exemplo:**
```py
produtos = [
    {'nome': 'p1', 'preco': 20},
    {'nome': 'p2', 'preco': 10},
    {'nome': 'p3', 'preco': 30},
]

# Aumenta o preço em 5% apenas para produtos com preço > 20
novos_produtos = [
    {**produto, 'preco': produto['preco'] * 1.05}
    if produto['preco'] > 20 else {**produto}
    for produto in produtos
]

print(*novos_produtos, sep='\n')
```

**Saída:**
```
{'nome': 'p1', 'preco': 20}
{'nome': 'p2', 'preco': 10}
{'nome': 'p3', 'preco': 31.5}
```

**Explicação:**
- A expressão `if produto['preco'] > 20` verifica se o preço do produto é maior que 20.
- Se a condição for verdadeira, o preço é atualizado com um aumento de 5%.
- Caso contrário, o produto permanece inalterado.

**Dicas:**
- Use List Comprehension para transformar dados de forma concisa.
- Combine condições para aplicar transformações seletivas.
- Para operações mais complexas, considere usar loops tradicionais para melhorar a legibilidade.

---

## 7. Filtro de Dados em List Comprehension (`filter`)

O **filtro de dados** em Python é o processo de selecionar elementos de um iterável com base em condições específicas. Com **List Comprehension**, é possível aplicar filtros de forma concisa e eficiente.

### 7.1. O Que é Filtro de Dados?

- O filtro de dados consiste em selecionar elementos que atendem a uma condição.
- Em Python, isso pode ser feito com `List Comprehension` ou com a função `filter`.

**Exemplo Simples:**
```py
numeros = [1, 2, 3, 4, 5]
pares = [numero for numero in numeros if numero % 2 == 0]
print(pares)  # Saída: [2, 4]
```

### 7.2. Filtrando Dados com List Comprehension

Com **List Comprehension**, você pode adicionar condições para filtrar elementos diretamente na expressão.

**Exemplo:**
```py
numeros = [1, 2, 3, 4, 5]
pares = [numero for numero in numeros if numero % 2 == 0]
print(pares)  # Saída: [2, 4]
```

**Exemplo com Dicionários:**
```py
produtos = [
    {'nome': 'p1', 'preco': 20},
    {'nome': 'p2', 'preco': 10},
    {'nome': 'p3', 'preco': 30},
]

# Filtrando produtos com preço >= 20
produtos_filtrados = [
    produto for produto in produtos if produto['preco'] >= 20
]

print(produtos_filtrados)
# Saída: [{'nome': 'p1', 'preco': 20}, {'nome': 'p3', 'preco': 30}]
```

### 7.3. Exemplo Prático com Condições

Você pode combinar filtros e mapeamentos em uma única List Comprehension.

**Exemplo:**
```py
produtos = [
    {'nome': 'p1', 'preco': 20},
    {'nome': 'p2', 'preco': 10},
    {'nome': 'p3', 'preco': 30},
]

# Atualizando o preço e filtrando produtos com preço ajustado > 10
novos_produtos = [
    {**produto, 'preco': produto['preco'] * 1.05}
    if produto['preco'] > 20 else {**produto}
    for produto in produtos
    if (produto['preco'] >= 20 and produto['preco'] * 1.05) > 10
]

import pprint
pprint.pprint(novos_produtos, sort_dicts=False, width=40)
```

**Saída:**
```
[{'nome': 'p1', 'preco': 20},
 {'nome': 'p3', 'preco': 31.5}]
```

**Explicação:**
- A condição `if produto['preco'] >= 20` filtra produtos com preço maior ou igual a 20.
- O preço é ajustado em 5% (`produto['preco'] * 1.05`) apenas para produtos com preço maior que 20.
- Produtos que não atendem à condição são excluídos.

**Dicas:**
- Use List Comprehension para combinar filtros e transformações em uma única expressão.
- Para filtros mais complexos, considere usar funções auxiliares para melhorar a legibilidade.
- A função `pprint` pode ser usada para exibir dados estruturados de forma legível.

---

## 8. List Comprehension com Mais de Um `for`

A **List Comprehension** em Python permite usar múltiplos loops `for` para criar listas complexas de forma concisa. Isso é útil para gerar combinações ou estruturas aninhadas.

### 8.1. O Que é List Comprehension com Múltiplos `for`?

- É uma List Comprehension que utiliza mais de um loop `for` para iterar sobre múltiplos iteráveis.
- Cada loop `for` é aninhado, como em loops tradicionais.

**Exemplo com Loops Tradicionais:**
```py
lista = []
for x in range(3):
    for y in range(3):
        lista.append((x, y))
print(lista)  # Saída: [(0, 0), (0, 1), (0, 2), (1, 0), (1, 1), (1, 2), (2, 0), (2, 1), (2, 2)]
```

**Exemplo com List Comprehension:**
```py
lista = [(x, y) for x in range(3) for y in range(3)]
print(lista)  # Saída: [(0, 0), (0, 1), (0, 2), (1, 0), (1, 1), (1, 2), (2, 0), (2, 1), (2, 2)]
```

### 8.2. Criando Listas com Múltiplos `for`

Você pode usar múltiplos loops `for` em uma única List Comprehension para gerar combinações ou listas aninhadas.

**Exemplo:**
```py
lista = [
    (x, y)
    for x in range(3)
    for y in range(3)
]
print(lista)
# Saída: [(0, 0), (0, 1), (0, 2), (1, 0), (1, 1), (1, 2), (2, 0), (2, 1), (2, 2)]
```

### 8.3. Exemplo Prático com Múltiplos `for`

**Criando Listas Aninhadas:**
```py
lista = [
    [(x, letra) for letra in 'Luiz']
    for x in range(3)
]
print(lista)
```

**Saída:**
```
[[(0, 'L'), (0, 'u'), (0, 'i'), (0, 'z')],
 [(1, 'L'), (1, 'u'), (1, 'i'), (1, 'z')],
 [(2, 'L'), (2, 'u'), (2, 'i'), (2, 'z')]]
```

**Explicação:**
- O primeiro `for` (`for x in range(3)`) cria a estrutura externa.
- O segundo `for` (`for letra in 'Luiz'`) cria a estrutura interna para cada valor de `x`.
- O resultado é uma lista de listas, onde cada sublista contém tuplas com o índice `x` e cada letra da string `'Luiz'`.

**Dicas:**
- Use múltiplos `for` em List Comprehension para criar combinações ou listas aninhadas de forma concisa.
- Para listas muito complexas, considere usar loops tradicionais para melhorar a legibilidade.
- Combine List Comprehension com condições (`if`) para filtrar os resultados.

---

## 9. Dictionary Comprehension e Set Comprehension

As **comprehensions** em Python permitem criar dicionários e conjuntos de forma concisa e eficiente, assim como as List Comprehensions. Elas são úteis para transformar ou filtrar dados de iteráveis.

### 9.1. O Que é Dictionary Comprehension?

- **Dictionary Comprehension** é uma forma de criar dicionários a partir de iteráveis.
- Permite transformar ou filtrar chaves e valores de forma concisa.

**Sintaxe:**
```py
{chave: valor for item in iterável}
```

**Exemplo:**
```py
produto = {
    'nome': 'Caneta Azul',
    'preco': 2.5,
    'categoria': 'Escritório',
}

dc = {
    chave: valor.upper()
    if isinstance(valor, str) else valor
    for chave, valor in produto.items()
    if chave != 'categoria'
}

print(dc)
# Saída: {'nome': 'CANETA AZUL', 'preco': 2.5}
```

**Explicação:**
- A chave `'categoria'` foi filtrada com `if chave != 'categoria'`.
- Os valores do tipo `str` foram convertidos para maiúsculas com `valor.upper()`.

### 9.2. O Que é Set Comprehension?

- **Set Comprehension** é uma forma de criar conjuntos (sets) a partir de iteráveis.
- Garante que os valores no conjunto sejam únicos.

**Sintaxe:**
```py
{expressão for item in iterável}
```

**Exemplo:**
```py
s1 = {2 ** i for i in range(10)}
print(s1)
# Saída: {1, 2, 4, 8, 16, 32, 64, 128, 256, 512}
```

**Explicação:**
- A expressão `2 ** i` calcula potências de 2 para cada valor de `i` no intervalo de 0 a 9.
- O conjunto resultante contém apenas valores únicos.

### 9.3. Exemplos Práticos

**Dictionary Comprehension com Lista de Tuplas:**
```py
lista = [
    ('a', 'valor a'),
    ('b', 'valor a'),
    ('b', 'valor a'),
]

dc = {
    chave: valor
    for chave, valor in lista
}

print(dc)
# Saída: {'a': 'valor a', 'b': 'valor a'}
```

**Explicação:**
- O dicionário resultante contém apenas a última ocorrência de cada chave, pois as chaves em dicionários são únicas.

**Set Comprehension com Condição:**
```py
s1 = {i for i in range(20) if i % 2 == 0}
print(s1)
# Saída: {0, 2, 4, 6, 8, 10, 12, 14, 16, 18}
```

**Explicação:**
- Apenas os números pares no intervalo de 0 a 19 são incluídos no conjunto.

**Dicas:**
- Use **Dictionary Comprehension** para transformar ou filtrar dicionários de forma concisa.
- Use **Set Comprehension** para criar conjuntos únicos a partir de iteráveis.
- Para operações mais complexas, considere usar loops tradicionais para melhorar a legibilidade.

---