# Fundamentos 1

## Sumário

1. [Função `print()`](#1-função-print)
2. [Tipos de Dados](#2-tipos-de-dados)
    - 2.1. [Tipos Primitivos](#tipos-primitivos)
    - 2.2. [Conversões de Tipos](#conversões-de-tipos)
3. [Operadores Aritméticos](#3-operadores-aritméticos)
4. [Variáveis](#4-variáveis)
5. [Operações com Strings](#5-operações-com-strings)
    - 5.1. [Concatenar Strings](#concatenar-strings)
    - 5.2. [Repetir Strings](#repetir-strings)
    - 5.3. [Fatiamento (Slicing)](#fatiamento-slicing)
6. [Função `input()`](#6-função-input)
    - 6.1. [Convertendo a Entrada de Dados](#convertendo-a-entrada-de-dados)
7. [Métodos de Strings](#7-métodos-de-strings)
    - 7.1. [Principais Métodos de Strings](#principais-métodos-de-strings)
8. [Formatação de Strings](#8-formatação-de-strings)
    - 8.1. [Com `f-strings`](#81-com-f-strings)
        - 8.1.1. [Formatação Básica](#formatação-básica)
        - 8.1.2. [Especificadores de Formato](#especificadores-de-formato)
        - 8.1.3. [Alinhamento e Preenchimento](#alinhamento-e-preenchimento)
        - 8.1.4. [Formatação de Números](#formatação-de-números)
        - 8.1.5. [Conversion Flags](#conversion-flags)
        - 8.1.6. [Outros Exemplos Completos](#outros-exemplos-completos)
    - 8.2. [Com `.format()`](#82-com-format)
        - 8.2.1. [Parâmetros Nomeados](#parâmetros-nomeados)
        - 8.2.2. [Índices no `.format()`](#índices-no-format)
    - 8.3. [Com `%`](#83-com-)
        - 8.3.1. [Especificadores de Formato](#especificadores-de-formato)
    - 8.4. [Observações Finais](#observações-finais)

---

### 1. Função `print()`

A função `print()` é usada para exibir informações na tela. Ela pode ser usada para mostrar texto, números ou valores de variáveis.

**Exemplo:**
```py
print("Olá, Mundo!")
```

**Delimitadores de texto:** As strings devem ser envolvidas por aspas (`""` ou `''`).

**Importante:**
- Função precisa de parênteses: A função `print()` sempre exige parênteses para funcionar.

**Parâmetro Separador `sep`:** Serve para fazer a separação dos argumentos.

**Exemplo:**
```py
print(12, 34, sep="-")  # Retorna: 12-34
``` 

**Parâmetro Quebra de Linha `end`:** Serve para controlar a quebra de linha.

**Exemplo 01:**
```py
print(12, 34, end=" ")
print(12, 34)

# Retorna:
# 12 34 12 34
```

**Exemplo 02:**
```py
print(12, 34, end="\n")
print(12, 34)

# Retorna:
"""
12 34 
12 34
"""
```

---

### 2. Tipos de Dados

#### Tipos Primitivos

Python possui diferentes tipos de dados, que são usados para armazenar valores.

- **int:** Números inteiros (sem casas decimais).
- **float:** Números decimais (com casas decimais).
- **str:** Strings (sequências de caracteres ou texto).
- **bool:** Valores lógicos (True ou False).

**Exemplos:**
```py
# Tipos de dados
numero_inteiro = 10  # Tipo: int
numero_decimal = 10.5  # Tipo: float
texto = "Olá, Python!"  # Tipo: str
verdadeiro = True  # Tipo: bool
```

#### Conversões de Tipos

Você pode converter entre tipos de dados em Python usando funções como `int()`, `float()` e `str()`.

**Exemplo de conversão:**
```py
numero_string = "10"
numero_inteiro = int(numero_string)  # Converte string para inteiro
print(numero_inteiro)  # Resultado: 10
```

---

### 3. Operadores Aritméticos

Os operadores aritméticos são usados para realizar operações matemáticas em Python. Aqui estão os principais operadores aritméticos:

- **`+`**: Soma
- **`-`**: Subtração
- **`*`**: Multiplicação
- **`/`**: Divisão (sempre retorna um número float)
- **`//`**: Divisão inteira (retorna a parte inteira da divisão)
- **`%`**: Módulo (resto da divisão)
- **`**`**: Potência (potência de um número)

**Exemplos:**
```py
# Soma
soma = 5 + 3  # Resultado: 8

# Subtração
subtracao = 10 - 2  # Resultado: 8

# Multiplicação
multiplicacao = 4 * 3  # Resultado: 12

# Divisão
divisao = 9 / 2  # Resultado: 4.5

# Divisão inteira
divisao_inteira = 9 // 2  # Resultado: 4

# Módulo (resto)
resto = 9 % 2  # Resultado: 1

# Potência
potencia = 2 ** 3  # Resultado: 8
```

---

### 4. Variáveis

As variáveis são usadas para armazenar valores. Em Python, elas devem ser sempre escritas em letras minúsculas por convenção.

**Exemplo:**
```py
nome = "João"
idade = 22
peso = 61
print(nome, idade, peso)  # Resultado: João 22 61
```

---

### 5. Operações com Strings

As strings são tratadas como sequências de caracteres. Python permite realizar várias operações com elas, como concatenar, repetir ou fatiar.

#### Concatenar Strings

Você pode juntar (concatenar) strings usando o operador `+`.

**Exemplo:**
```py
nome = "Maria"
sobrenome = "Silva"
nome_completo = nome + " " + sobrenome
print(nome_completo)  # Resultado: Maria Silva
```

#### Repetir Strings

Você pode repetir uma string usando o operador `*`.

**Exemplo:**
```py
texto = "Python! "
print(texto * 3)  # Resultado: Python! Python! Python!
```

#### Fatiamento (Slicing)

Você pode pegar partes de uma string usando fatiamento. A sintaxe é `str[inicio:fim:passo]`.

**Exemplo:**
```py
nome = "Python"
print(nome[0:3])  # Resultado: Pyt
```

---

### 6. Função `input()`

A função `input()` é usada para capturar a entrada de dados do usuário. O valor retornado por `input()` é sempre uma string, mesmo que o usuário digite números.

**Exemplo:**
```py
nome = input("Qual é o seu nome? ")
print("Olá, " + nome + "! Seja bem-vindo.")
```

#### Convertendo a Entrada de Dados

Se você precisar trabalhar com números, é necessário converter a entrada de dados de string para `int` ou `float`.

**Exemplo:**
```py
numero = int(input("Digite um número: "))
print("Você digitou o número:", numero)
```

---

### 7. Métodos de Strings

As strings possuem métodos integrados que permitem realizar operações e modificações nelas, como converter para maiúsculas, remover espaços, substituir substrings, entre outros.

#### Principais Métodos de Strings

<details>
<summary>1. <code>.lower()</code> - Converte todos os caracteres da string para minúsculas</summary>

**Exemplo:**
```py
texto = "Python"
print(texto.lower())  # Resultado: python
```
</details>

<details>
<summary>2. <code>.upper()</code> - Converte todos os caracteres da string para maiúsculas</summary>

**Exemplo:**
```py
texto = "Python"
print(texto.upper())  # Resultado: PYTHON
```
</details>

<details>
<summary>3. <code>.capitalize()</code> - Converte a primeira letra da string para maiúscula e todas as outras para minúsculas</summary>

**Exemplo:**
```py
texto = "python"
print(texto.capitalize())  # Resultado: Python
```
</details>

<details>
<summary>4. <code>.title()</code> - Converte a primeira letra de cada palavra da string para maiúscula</summary>

**Exemplo:**
```py
texto = "python programming language"
print(texto.title())  # Resultado: Python Programming Language
```
</details>

<details>
<summary>5. <code>.strip()</code> - Remove os espaços em branco do início e do final da string</summary>

**Exemplo:**
```py
texto = "   Python   "
print(texto.strip())  # Resultado: Python
```
</details>

<details>
<summary>6. <code>.replace(old, new)</code> - Substitui todas as ocorrências da substring <code>old</code> pela substring <code>new</code></summary>

**Exemplo:**
```py
texto = "Python é incrível"
print(texto.replace("Python", "Java"))  # Resultado: Java é incrível
```
</details>

<details>
<summary>7. <code>.split(sep)</code> - Divide a string em uma lista de substrings</summary>

**Exemplo:**
```py
texto = "Python é divertido"
print(texto.split())  # Resultado: ['Python', 'é', 'divertido']
```

**Com delimitador específico:**
```py
texto = "Python,Java,C++"
print(texto.split(','))  # Resultado: ['Python', 'Java', 'C++']
```
</details>

<details>
<summary>8. <code>.join(iterable)</code> - Junta uma lista ou sequência de strings em uma única string</summary>

**Exemplo:**
```py
lista = ['Python', 'Java', 'C++']
print(", ".join(lista))  # Resultado: Python, Java, C++
```
</details>

<details>
<summary>9. <code>.find(substring)</code> - Retorna o índice da primeira ocorrência de <code>substring</code></summary>

**Exemplo:**
```py
texto = "Python é divertido"
print(texto.find("divertido"))  # Resultado: 9
print(texto.find("Java"))  # Resultado: -1
```
</details>

<details>
<summary>10. <code>.startswith(prefix)</code> - Verifica se a string começa com o prefixo especificado</summary>

**Exemplo:**
```py
texto = "Python é divertido"
print(texto.startswith("Python"))  # Resultado: True
print(texto.startswith("Java"))  # Resultado: False
```
</details>

<details>
<summary>11. <code>.endswith(suffix)</code> - Verifica se a string termina com o sufixo especificado</summary>

**Exemplo:**
```py
texto = "Python é divertido"
print(texto.endswith("divertido"))  # Resultado: True
print(texto.endswith("Java"))  # Resultado: False
```
</details>

<details>
<summary>12. <code>.count(substring)</code> - Conta quantas vezes a substring aparece na string</summary>

**Exemplo:**
```py
texto = "Python é uma linguagem de programação, e eu amo Python"
print(texto.count("Python"))  # Resultado: 2
```
</details>

<details>
<summary>13. <code>.isalpha()</code> - Verifica se todos os caracteres da string são alfabéticos</summary>

**Exemplo:**
```py
texto = "Python"
print(texto.isalpha())  # Resultado: True
texto2 = "Python3"
print(texto2.isalpha())  # Resultado: False
```
</details>

<details>
<summary>14. <code>.isdigit()</code> - Verifica se todos os caracteres da string são dígitos</summary>

**Exemplo:**
```py
texto = "12345"
print(texto.isdigit())  # Resultado: True
texto2 = "12a45"
print(texto2.isdigit())  # Resultado: False
```
</details>

---

### 8. Formatação de Strings

A formatação de strings em Python permite inserir variáveis, expressões e valores formatados diretamente em strings. Existem três formas principais de realizar a formatação:

---

#### 8.1. Com `f-strings`

As **f-strings** (format strings) são uma forma prática, moderna e legível de inserir variáveis e expressões dentro de strings, utilizando o prefixo `f` antes das aspas. Elas foram introduzidas no Python 3.6 e são amplamente utilizadas devido à sua simplicidade e flexibilidade.

##### Formatação Básica

Você pode inserir variáveis diretamente dentro de uma string utilizando `{}`.

**Exemplo:**
```py
nome = "João"
idade = 30
print(f"{nome} tem {idade} anos.")  # Resultado: João tem 30 anos.
```

Além de variáveis, você pode usar expressões e até métodos diretamente dentro das chaves `{}`.

**Exemplo:**
```py
a = 10
b = 20
print(f"A soma de {a} + {b} é {a + b}")  # Resultado: A soma de 10 + 20 é 30
```

##### Especificadores de Formato

Os **especificadores de formato** permitem controlar como os valores são exibidos. Aqui estão os principais:

| Especificador | Descrição                          | Exemplo (`f-string`)         |
|---------------|------------------------------------|------------------------------|
| `s`           | String                            | `f'{variavel:s}'`            |
| `d`           | Inteiro (decimal)                 | `f'{variavel:d}'`            |
| `f`           | Float (número decimal)            | `f'{variavel:.2f}'`          |
| `x` ou `X`    | Hexadecimal (minúsculo/maiúsculo) | `f'{variavel:x}'` ou `f'{variavel:X}'` |

##### Alinhamento e Preenchimento

Você pode alinhar e preencher valores formatados usando os seguintes caracteres:

| Símbolo | Descrição                              |
|---------|----------------------------------------|
| `>`     | Alinha à direita                       |
| `<`     | Alinha à esquerda                      |
| `^`     | Centraliza                             |
| `=`     | Força o número a aparecer antes dos zeros |
| `0`     | Preenche com zeros                     |

**Exemplos:**
```py
variavel = "ABC"

print(f"{variavel: >10}")  # Alinha à direita com 10 caracteres: '       ABC'
print(f"{variavel: <10}.")  # Alinha à esquerda com 10 caracteres: 'ABC       .'
print(f"{variavel: ^10}.")  # Centraliza com 10 caracteres: '   ABC    .'
```

##### Formatação de Números

Você pode formatar números com separadores de milhares, casas decimais e sinais.

**Exemplos:**
```py
# Número com separador de milhares, 1 casa decimal, preenchido com zeros e sinal positivo
print(f"{1000.4873648123746:0=+10,.1f}")  # Resultado: +001,000.5

# Exibindo um número em hexadecimal com 8 caracteres, preenchido com zeros
print(f"O hexadecimal de 1500 é {1500:08X}")  # Resultado: O hexadecimal de 1500 é 000005DC
```

##### Conversion Flags

As **conversion flags** permitem exibir representações específicas de valores:

| Flag | Descrição                          | Exemplo (`f-string`)         |
|------|------------------------------------|------------------------------|
| `!r` | Representação oficial (usando `repr()`) | `f'{variavel!r}'`            |
| `!s` | Representação como string (usando `str()`) | `f'{variavel!s}'`            |
| `!a` | Representação ASCII                | `f'{variavel!a}'`            |

**Exemplo:**
```py
variavel = "ABC"
print(f"{variavel!r}")  # Resultado: 'ABC'
```

##### Outros Exemplos Completos

**Exemplo 1: Formatação de Strings**
```py
nome = "Luiz"
idade = 30
print(f"{nome} tem {idade} anos.")  # Resultado: Luiz tem 30 anos.
```

**Exemplo 2: Formatação de Números**
```py
preco = 1234.56789
print(f"Preço formatado: R${preco:.2f}")  # Resultado: Preço formatado: R$1234.57
```

**Exemplo 3: Alinhamento e Preenchimento**
```py
variavel = "Python"
print(f"{variavel:*>10}")  # Resultado: ****Python
print(f"{variavel:*<10}")  # Resultado: Python****
print(f"{variavel:*^10}")  # Resultado: **Python**
```

**Exemplo 4: Hexadecimal**
```py
numero = 255
print(f"Hexadecimal: {numero:08X}")  # Resultado: Hexadecimal: 000000FF
```

---

#### 8.2. Com `.format()`

O método `.format()` substitui os `{}` em uma string pelos valores passados como argumentos. Ele é uma alternativa às **f-strings** e permite maior flexibilidade, como o uso de **parâmetros nomeados**.

**Exemplo:**
```py
nome = "João"
idade = 30
print("Meu nome é {} e tenho {} anos.".format(nome, idade))
```

##### Parâmetros Nomeados

Os **parâmetros nomeados** são argumentos passados com um nome dentro das chamadas das funções. Isso torna o código mais legível e organizado, pois você pode identificar facilmente o que cada valor representa.

**Exemplo:**
```py
string = "Olá, {nome}! Você tem {idade} anos."
resultado = string.format(nome="João", idade=25)
print(resultado)  # Resultado: Olá, João! Você tem 25 anos.
```

##### Índices no `.format()`

Se você não usar nomes nos `{}`, pode passar os valores por **índices**. Lembre-se de que os índices começam em `0`.

**Exemplo:**
```py
string = "a={0} b={1} c={2:.2f}"
formato = string.format("AAAAA", "B", 1.1)
print(formato)  # Resultado: a=AAAAA b=B c=1.10
```

---

#### 8.3. Com `%`

A interpolação com `%` é uma forma antiga de formatar strings. Apesar de ser menos utilizada atualmente, ainda é funcional e pode ser encontrada em códigos legados.

**Exemplo:**
```py
nome = "João"
idade = 30
print("Meu nome é %s e tenho %d anos." % (nome, idade))
```

##### Especificadores de Formato

| Especificador | Descrição                          | Exemplo (`%`)       |
|---------------|------------------------------------|---------------------|
| `%s`          | String                            | `"Olá %s" % "Mundo"` |
| `%d` ou `%i`  | Inteiro (decimal)                 | `"Número: %d" % 10` |
| `%f`          | Float (número decimal)            | `"Preço: %.2f" % 10.5` |
| `%x` ou `%X`  | Hexadecimal (minúsculo/maiúsculo) | `"%x" % 255` ou `"%X" % 255` |

**Exemplo Completo:**

```py
nome = "Luiz"
preco = 1000.95
print("%s, o preço é R$%.2f" % (nome, preco))  # Resultado: Luiz, o preço é R$1000.95
```

---

#### Observações Finais

- **f-strings** são recomendadas para formatação de strings em Python devido à sua legibilidade e eficiência.
- Para versões de Python anteriores ao 3.6, use `.format()` ou `%`.