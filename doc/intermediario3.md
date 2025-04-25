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

---

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

---

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

---

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