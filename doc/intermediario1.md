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