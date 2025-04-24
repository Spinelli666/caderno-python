# Intermediário 1

## Sumário

1. [Introdução às Funções (`def`) em Python](#1-introdução-às-funções-def-em-python)
    - 1.1. [Definindo Funções](#11-definindo-funções)
    - 1.2. [Parâmetros e Argumentos](#12-parâmetros-e-argumentos)
    - 1.3. [Valores Padrão para Parâmetros](#13-valores-padrão-para-parâmetros)
2. [Argumentos Nomeados e Posicionais em Funções](#2-argumentos-nomeados-e-posicionais-em-funções)
    - 2.1. [Argumentos Posicionais (Não Nomeados)](#21-argumentos-posicionais-não-nomeados)
    - 2.2. [Argumentos Nomeados](#22-argumentos-nomeados)
    - 2.3. [Misturando Argumentos Nomeados e Posicionais](#23-misturando-argumentos-nomeados-e-posicionais)
3. [Valores Padrão para Parâmetros em Funções](#3-valores-padrão-para-parâmetros-em-funções)
    - 3.1. [Definindo Valores Padrão](#31-definindo-valores-padrão)
    - 3.2. [Usando `None` como Valor Padrão](#32-usando-none-como-valor-padrão)
    - 3.3. [Refatoração de Código](#33-refatoração-de-código)
4. [Escopo de Funções e Módulos em Python](#4-escopo-de-funções-e-módulos-em-python)
    - 4.1. [O Que é Escopo?](#41-o-que-é-escopo)
    - 4.2. [Escopo Global e Local](#42-escopo-global-e-local)
    - 4.3. [A Palavra-chave `global`](#43-a-palavra-chave-global)
5. [Retorno de Valores das Funções (`return`)](#5-retorno-de-valores-das-funções-return)
    - 5.1. [O Que é o `return`](#51-o-que-é-o-return)
    - 5.2. [Como Usar o `return`](#52-como-usar-o-return)
    - 5.3. [Retornando Diferentes Tipos de Valores](#53-retornando-diferentes-tipos-de-valores)
6. [Argumentos Não Nomeados com `*args`](#6-argumentos-não-nomeados-com-args)
    - 6.1. [O Que é `*args`](#61-o-que-é-args)
    - 6.2. [Empacotamento com `*args`](#62-empacotamento-com-args)
    - 6.3. [Desempacotamento com `*args`](#63-desempacotamento-com-args)

---

## 1. Introdução às Funções (`def`) em Python

As **funções** em Python são blocos de código reutilizáveis que realizam uma tarefa específica. Elas ajudam a organizar o código, evitar repetição e melhorar a legibilidade.

### Características das Funções:
- São definidas usando a palavra-chave `def`.
- Podem receber **parâmetros** (valores de entrada).
- Podem retornar um valor usando a palavra-chave `return`.
- Por padrão, uma função retorna `None` se não houver um `return`.

### 1.1. Definindo Funções

Para definir uma função, usamos a palavra-chave `def`, seguida pelo nome da função e parênteses. O corpo da função é indentado.

**Exemplo:**
```py
def minha_funcao():
    print("Hello, World!")
```

Para chamar a função, basta usar o nome dela seguido de parênteses:
```py
minha_funcao()  # Saída: Hello, World!
```

### 1.2. Parâmetros e Argumentos

As funções podem receber **parâmetros** (valores de entrada) para realizar operações específicas.

**Exemplo:**
```py
def imprimir(a, b, c):
    print(a, b, c)

imprimir(1, 2, 3)  # Saída: 1 2 3
imprimir(4, 5, 6)  # Saída: 4 5 6
```

**Explicação:**
- `a`, `b` e `c` são os **parâmetros** da função.
- Os valores `1, 2, 3` e `4, 5, 6` são os **argumentos** passados para a função.

### 1.3. Valores Padrão para Parâmetros

Você pode definir valores padrão para os parâmetros de uma função. Se nenhum argumento for passado, o valor padrão será usado.

**Exemplo:**
```py
def saudacao(nome='Visitante'):
    print(f'Olá, {nome}!')

saudacao('João')  # Saída: Olá, João!
saudacao('Maria')  # Saída: Olá, Maria!
saudacao()  # Saída: Olá, Visitante!
```

**Explicação:**
- O parâmetro `nome` tem o valor padrão `'Visitante'`.
- Quando nenhum argumento é passado, o valor `'Visitante'` é usado.

**Dicas:**
- Use funções para organizar seu código em blocos reutilizáveis.
- Sempre escolha nomes descritivos para suas funções e parâmetros.
- Funções com valores padrão tornam o código mais flexível e fácil de usar.

---

## 2. Argumentos Nomeados e Posicionais em Funções

Em Python, ao chamar uma função, você pode passar argumentos de duas formas principais:
- **Argumentos posicionais (não nomeados):** Passados na ordem em que os parâmetros foram definidos.
- **Argumentos nomeados:** Passados explicitamente com o nome do parâmetro seguido de um sinal de igual (`=`).

### 2.1. Argumentos Posicionais (Não Nomeados)

Os **argumentos posicionais** são passados para a função na ordem em que os parâmetros foram definidos.

**Exemplo:**
```py
def soma(x, y, z):
    print(f'{x=} y={y} {z=}', '|', 'x + y + z = ', x + y + z)

soma(1, 2, 3)  # Saída: x=1 y=2 z=3 | x + y + z =  6
```

**Explicação:**
- Os valores `1`, `2` e `3` são passados para os parâmetros `x`, `y` e `z`, respectivamente.
- A ordem dos argumentos é importante.

### 2.2. Argumentos Nomeados

Os **argumentos nomeados** são passados explicitamente com o nome do parâmetro. Isso permite maior clareza e flexibilidade.

**Exemplo:**
```py
soma(1, y=2, z=5)  # Saída: x=1 y=2 z=5 | x + y + z =  8
```

**Explicação:**
- O argumento `x` é passado como posicional.
- Os argumentos `y` e `z` são passados como nomeados.
- A ordem dos argumentos nomeados não importa, desde que sejam especificados corretamente.

### 2.3. Misturando Argumentos Nomeados e Posicionais

Você pode misturar argumentos posicionais e nomeados, mas os **posicionais devem vir antes dos nomeados**.

**Exemplo:**
```py
soma(1, z=3, y=2)  # Saída: x=1 y=2 z=3 | x + y + z =  6
```

**Erro ao inverter a ordem:**
```py
# soma(x=1, 2, 3)  # Isso gera um erro de sintaxe.
```

### Exemplo com Função `print`

A função `print` aceita argumentos nomeados, como `sep` e `end`.

**Exemplo:**
```py
print(1, 2, 3, sep='-')  # Saída: 1-2-3
```

**Explicação:**
- `1`, `2` e `3` são argumentos posicionais.
- `sep='-'` é um argumento nomeado que define o separador entre os valores.

**Dicas:**
- Use argumentos nomeados para melhorar a legibilidade do código.
- Sempre passe os argumentos posicionais antes dos nomeados.
- Argumentos nomeados são úteis quando uma função tem muitos parâmetros ou valores padrão.

---

## 3. Valores Padrão para Parâmetros em Funções

Ao definir uma função, você pode atribuir **valores padrão** aos parâmetros. Isso permite que a função seja chamada sem a necessidade de passar todos os argumentos, pois os parâmetros com valores padrão assumirão esses valores caso não sejam fornecidos.

### 3.1. Definindo Valores Padrão

Os valores padrão são definidos diretamente na assinatura da função, usando o operador `=`.

**Exemplo:**
```py
def soma(x, y, z=0):
    print(f'{x=} {y=} {z=}', x + y + z)

soma(1, 2)  # Saída: x=1 y=2 z=0 3
soma(1, 2, 3)  # Saída: x=1 y=2 z=3 6
```

**Explicação:**
- O parâmetro `z` tem o valor padrão `0`.
- Quando `z` não é fornecido, ele assume o valor padrão.

### 3.2. Usando `None` como Valor Padrão

O valor especial `None` (do tipo `NoneType`) é frequentemente usado como valor padrão para indicar que um parâmetro é opcional ou que não foi fornecido.

**Exemplo:**
```py
def soma(x, y, z=None):
    if z is not None:
        print(f'{x=} {y=} {z=}', x + y + z)
    else:
        print(f'{x=} {y=}', x + y)

soma(1, 2)  # Saída: x=1 y=2 3
soma(7, 9, 0)  # Saída: x=7 y=9 z=0 16
```

**Explicação:**
- O parâmetro `z` tem o valor padrão `None`.
- Dentro da função, verificamos se `z` é diferente de `None` antes de usá-lo.

**Por que usar `None`?**
- `None` é útil quando o valor padrão não deve ser confundido com valores válidos, como `0`, `False` ou uma string vazia.

### 3.3. Refatoração de Código

**Refatorar** significa editar e melhorar o código sem alterar sua funcionalidade. Usar valores padrão e `None` pode simplificar e tornar o código mais legível.

**Exemplo Refatorado:**
```py
def soma(x, y, z=None):
    if z is not None:
        print(f'{x=} {y=} {z=}', x + y + z)
    else:
        print(f'{x=} {y=}', x + y)

soma(1, 2)  # Saída: x=1 y=2 3
soma(3, 5)  # Saída: x=3 y=5 8
soma(100, 200)  # Saída: x=100 y=200 300
soma(7, 9, 0)  # Saída: x=7 y=9 z=0 16
soma(y=9, z=0, x=7)  # Saída: x=7 y=9 z=0 16
```

**Dicas:**
- Use valores padrão para simplificar chamadas de funções.
- Use `None` para parâmetros opcionais que precisam de lógica adicional.
- Refatore seu código para torná-lo mais legível e eficiente.

---

## 4. Escopo de Funções e Módulos em Python

O **escopo** em Python define onde variáveis e funções podem ser acessadas ou modificadas. Ele é dividido em **escopo global** e **escopo local**.

### 4.1. O Que é Escopo?

O **escopo** determina a visibilidade e o tempo de vida de variáveis e funções no código.

- **Escopo Global:** É o escopo onde todo o código é acessível. Variáveis definidas no escopo global podem ser acessadas em qualquer lugar do código, exceto dentro de escopos locais, a menos que sejam explicitamente referenciadas.
- **Escopo Local:** É o escopo restrito a uma função ou bloco de código. Variáveis definidas em escopos locais não são acessíveis fora deles.

### 4.2. Escopo Global e Local

**Exemplo:**
```py
x = 1  # Variável no escopo global

def escopo():
    x = 10  # Variável no escopo local da função
    print(f'Escopo local: {x}')

print(f'Escopo global: {x}')  # Saída: Escopo global: 1
escopo()  # Saída: Escopo local: 10
print(f'Escopo global: {x}')  # Saída: Escopo global: 1
```

**Explicação:**
- A variável `x` definida fora da função está no escopo global.
- A variável `x` definida dentro da função está no escopo local e não afeta o valor de `x` no escopo global.

### 4.3. A Palavra-chave `global`

A palavra-chave **`global`** permite que uma variável definida no escopo global seja modificada dentro de um escopo local.

**Exemplo:**
```py
x = 1  # Variável no escopo global

def escopo():
    global x  # Refere-se à variável global
    x = 10
    print(f'Escopo local (global x modificado): {x}')

print(f'Escopo global antes: {x}')  # Saída: Escopo global antes: 1
escopo()  # Saída: Escopo local (global x modificado): 10
print(f'Escopo global depois: {x}')  # Saída: Escopo global depois: 10
```

**Exemplo com Escopos Aninhados:**
```py
x = 1

def escopo():
    global x
    x = 10

    def outra_funcao():
        global x
        x = 11
        y = 2
        print(f'Outra função: x={x}, y={y}')  # Saída: Outra função: x=11, y=2

    outra_funcao()
    print(f'Escopo local após outra_funcao: x={x}')  # Saída: Escopo local após outra_funcao: x=11

print(f'Escopo global antes: {x}')  # Saída: Escopo global antes: 1
escopo()
print(f'Escopo global depois: {x}')  # Saída: Escopo global depois: 11
```

**Explicação:**
- A palavra-chave `global` permite que a variável `x` no escopo global seja modificada dentro das funções.
- A variável `y` está no escopo local da função `outra_funcao` e não é acessível fora dela.

**Dicas:**
- Evite usar `global` sempre que possível, pois pode dificultar a leitura e manutenção do código.
- Prefira passar variáveis como argumentos para funções ou retornar valores para evitar efeitos colaterais.
- Use escopos locais para encapsular lógica e proteger variáveis de modificações acidentais.

---

## 5. Retorno de Valores das Funções (`return`)

O **`return`** é usado em funções para retornar um valor ao local onde a função foi chamada. Ele encerra a execução da função e pode opcionalmente devolver um valor.

### 5.1. O Que é o `return`

- O `return` permite que uma função envie um valor de volta para o código que a chamou.
- Sem o `return`, a função retorna `None` por padrão.

**Exemplo:**
```py
def soma(x, y):
    return x + y

resultado = soma(2, 3)
print(resultado)  # Saída: 5
```

### 5.2. Como Usar o `return`

O `return` pode ser usado para:
1. Encerrar a execução da função.
2. Retornar um valor ou múltiplos valores.

**Exemplo com Condicional:**
```py
def soma(x, y):
    if x > 10:
        return [10, 20]  # Retorna uma lista se x > 10
    return x + y  # Retorna a soma caso contrário

soma1 = soma(2, 2)
soma2 = soma(11, 55)

print(soma1)  # Saída: 4
print(soma2)  # Saída: [10, 20]
```

**Explicação:**
- Se `x > 10`, a função retorna uma lista `[10, 20]`.
- Caso contrário, retorna a soma de `x` e `y`.

### 5.3. Retornando Diferentes Tipos de Valores

O `return` pode retornar qualquer tipo de dado, como números, strings, listas, dicionários, ou até mesmo `None`.

**Exemplo:**
```py
def exemplo(x):
    if x > 0:
        return "Positivo"
    elif x < 0:
        return "Negativo"
    return None  # Retorna None se x for 0

print(exemplo(10))  # Saída: Positivo
print(exemplo(-5))  # Saída: Negativo
print(exemplo(0))   # Saída: None
```

**Retornando Múltiplos Valores:**
```py
def operacoes(x, y):
    soma = x + y
    subtracao = x - y
    return soma, subtracao  # Retorna uma tupla com dois valores

resultado = operacoes(10, 5)
print(resultado)  # Saída: (15, 5)

soma, subtracao = operacoes(10, 5)
print(soma)       # Saída: 15
print(subtracao)  # Saída: 5
```

**Dicas:**
- Use o `return` para tornar suas funções mais reutilizáveis e flexíveis.
- Sempre documente o que sua função retorna para facilitar a leitura do código.
- Retorne valores claros e consistentes para evitar confusão ao usar a função.

---

## 6. Argumentos Não Nomeados com `*args`

O `*args` é usado em funções Python para lidar com uma **quantidade variável de argumentos não nomeados**. Ele permite que você passe múltiplos valores para uma função sem precisar especificar cada argumento individualmente.

### 6.1. O Que é `*args`

- `*args` é uma convenção que representa **argumentos não nomeados**.
- Ele empacota os argumentos em uma **tupla**, permitindo que você os manipule dentro da função.

**Exemplo:**
```py
def soma(*args):
    total = 0
    for numero in args:
        total += numero
    return total

print(soma(1, 2, 3))  # Saída: 6
print(soma(4, 5, 6, 7))  # Saída: 22
```

**Explicação:**
- A função `soma` aceita qualquer número de argumentos.
- Os argumentos são empacotados em uma tupla chamada `args`.

### 6.2. Empacotamento com `*args`

O empacotamento ocorre quando você usa `*args` para capturar múltiplos argumentos em uma tupla.

**Exemplo:**
```py
def exibir_argumentos(*args):
    print(args)

exibir_argumentos(1, 2, 3)  # Saída: (1, 2, 3)
exibir_argumentos('a', 'b', 'c')  # Saída: ('a', 'b', 'c')
```

**Explicação:**
- Os valores passados para a função são empacotados em uma tupla.
- Você pode iterar sobre `args` ou acessar seus elementos como faria com uma tupla.

### 6.3. Desempacotamento com `*args`

O desempacotamento ocorre quando você usa o operador `*` para expandir uma sequência (como uma lista ou tupla) em múltiplos argumentos.

**Exemplo:**
```py
def soma(*args):
    total = 0
    for numero in args:
        total += numero
    return total

numeros = (1, 2, 3, 4, 5)
print(soma(*numeros))  # Saída: 15
```

**Explicação:**
- A tupla `numeros` é desempacotada em argumentos individuais usando `*`.
- Isso é equivalente a chamar `soma(1, 2, 3, 4, 5)`.

**Outro Exemplo:**
```py
x, y, *resto = 1, 2, 3, 4, 5
print(x, y, resto)  # Saída: 1 2 [3, 4, 5]
```

### Comparação com a Função `sum`

A função `sum` do Python pode ser usada para somar elementos de uma sequência diretamente.

**Exemplo:**
```py
numeros = (1, 2, 3, 4, 5)
print(sum(numeros))  # Saída: 15
```

**Dica:**
- Use `sum` para somar elementos de uma sequência quando não precisar de lógica adicional.

**Dicas:**
- Use `*args` quando não souber quantos argumentos serão passados para a função.
- Combine `*args` com desempacotamento para maior flexibilidade.
- Lembre-se de que `args` é apenas uma convenção; você pode usar qualquer nome, mas `args` é amplamente adotado.

---