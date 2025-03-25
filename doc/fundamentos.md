# Fundamentos

## Sumário

1. [Função `print()`](#função-print)
2. [Tipos de Dados](#tipos-de-dados)
    - 2.1. [Tipos Primitivos](#tipos-primitivos)
    - 2.2. [Conversões de Tipos](#conversões-de-tipos)
3. [Operadores Artméticos](#operadores-aritméticos)
4. [Variáveis](#variáveis)
5. [Operações com Strings](#operações-com-strings)
6. [Entrada de Dados(`(input()`)](#entrada-de-dados-input)
7. [Métodos de Strings](#métodos-de-strings)

### Função `print()`

A função `print()` é usada para exibir informações na tela. Ela pode ser usada para mostrar texto, números ou valores de variáveis.

**Exemplo:**
```py
print("Olá, Mundo!")
```

**Delimitadores de texto:** As strings devem ser envolvidas por aspas (`""` ou `''`).

**Importante:**
- Função precisa de parênteses: A função `print()` sempre exige parênteses para funcionar.

---

### Tipos de Dados

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

### Operadores Aritméticos

Os operadores aritméticos são usados para realizar operações matemáticas em Python. Aqui estão os principais operadores aritméticos:

- **+:** Soma

- **-:** Subtração

- __*:__ Multiplicação

- **/:** Divisão (sempre retorna um número float)

- **//:** Divisão inteira (retorna a parte inteira da divisão)

- **%:** Módulo (resto da divisão)

- __**:__ Potência (potência de um número)


**Exemplos**
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

### Variáveis

As variáveis são usadas para armazenar valores. Em Python, elas devem ser sempre escritas em letras minúsculas por convenção.

**Exemplos**
```py
nome = "João"
idade = 22
peso = 61
print(nome, idade, peso)  # Resultado: João 22 61

```

---

### Operações com Strings

As strings são tratadas como sequências de caracteres. Python permite realizar várias operações com elas, como concatenar, repetir ou fatiar.

**Concatenar Strings**

Você pode juntar (concatenar) strings usando o operador ``+``.

**Exemplo:**
```py
nome = "Maria"
sobrenome = "Silva"
nome_completo = nome + " " + sobrenome
print(nome_completo)  # Resultado: Maria Silva
```

**Repetir Strings**

Você pode reptir uma string usando o operador `*`.

**Exemplo:**
```py
texto = "Python! "
print(texto * 3)  # Resultado: Python! Python! Python!
```

**Fatiamento (Slicing)**

Você pode pegar partes de uma string usando fatiamento. A sintaxe é `str[inicio:fim]`.

**Exemplo:**
```py
nome = "Python"
print(nome[0:3])  # Resultado: Pyt

```

---

### Entrada de Dados (`input()`)

A função `input()` é usada para capturar a entrada de dados do usuário. O valor retornado por `input()` é sempre uma string, mesmo que o usuário digite números.

**Exemplo:**
```py
nome = input("Qual é o seu nome? ")
print("Olá, " + nome + "! Seja bem-vindo.")
```

**Convertendo a Entrada de Dados**

Se você precisar trabalhar com números, é necessário converter a entrada de dados de string para int ou float.

**Exemplo:**
```py
numero = int(input("Digite um número: "))
print("Você digitou o número:", numero)
```

---

### Métodos de Strings

Em Python, as strings são objetos e, como tal, possuem vários métodos integrados que permitem realizar operações e modificações nelas. Esses métodos são usados para realizar ações como converter o texto para maiúsculas ou minúsculas, remover espaços, procurar por substrings, entre outras.

**Principais Métodos de Strings**

**1.** `.lower()`

Converte todos os caracteres da string para minúsculas.

**Exemplo:**
```py
texto = "Python"
print(texto.lower())  # Resultado: python
```

**2.** `.upper()`

Converte todos os caracteres da string para maiúsculas.

**Exemplo:**
```py
texto = "Python"
print(texto.upper())  # Resultado: PYTHON
```

**3.** `.captalize()`

Converte a primeira letra da string para maiúscula e todas as outras para minúsculas.

**Exemplo:**
```py
texto = "python"
print(texto.capitalize())  # Resultado: Python
```

**4.** `.title()`

Converte a primeira letra de cada palavra da string para maiúscula. É útil para formatar títulos ou nomes próprios.

**Exemplo:**
```py
texto = "python programming language"
print(texto.title())  # Resultado: Python Programming Language
```

**5.** `.strip()`

Remove os espaços em branco do início e do final da string.

**Exemplo:**
```py
texto = "   Python   "
print(texto.strip())  # Resultado: Python
```

**6.** `.replace(old, new)`

Substitui todas as ocorrências da substring `old` pela substring `new`.

**Exemplo:**
```py
texto = "Python é incrível"
print(texto.replace("Python", "Java"))  # Resultado: Java é incrível
```

**7.** `.split(sep)`

Divide a string em uma lista de substrings, usando o caractere ou sequência especificada como delimitador (padrão é o espaço).

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

**8.** `.join(interable)`

Junta uma lista ou outra sequência de strings em uma única string, com um delimitador entre os elementos.

**Exemplo:**
```py
lista = ['Python', 'Java', 'C++']
print(", ".join(lista))  # Resultado: Python, Java, C++
```

**9.** `.find(substring)`

Retorna o índice da primeira ocorrência de `substring` dentro da string. Se não encontrar, retorna `-1`.

**Exemplo:**
```py
texto = "Python é divertido"
print(texto.find("divertido"))  # Resultado: 9
print(texto.find("Java"))  # Resultado: -1
```

**10.** `.startswith(prefix)`

Verifica se a string começa com o prefixo especificado. Retorna `True` ou `False`.

**Exemplo:**
```py
texto = "Python é divertido"
print(texto.startswith("Python"))  # Resultado: True
print(texto.startswith("Java"))  # Resultado: False
```

**11.** `.endswith(suffix)`

Verifica se a string termina com o sufixo especificado. Retorna `True` ou `False`.

**Exemplo:**
```py
texto = "Python é divertido"
print(texto.endswith("divertido"))  # Resultado: True
print(texto.endswith("Java"))  # Resultado: False
```

**12.** `.count(substring)`

Conta quantas vezes a substring aparece na string.

**Exemplo**
```py
texto = "Python é uma linguagem de programação, e eu amo Python"
print(texto.count("Python"))  # Resultado: 2
```

**13.** `.isalpha()`

Verifica se todos os caracteres da string são alfabéticos (letras). Retorna `True` se a string contiver apenas letras, e `False` caso contrário.

**Exemplo:**
```py
texto = "Python"
print(texto.isalpha())  # Resultado: True
texto2 = "Python3"
print(texto2.isalpha())  # Resultado: False
```

**14.** `.isdigit()`

Verifica se todos os caracteres da string são dígitos. Retorna `True` se a string contiver apenas números, e `False` caso contrário.

**Exemplo:**
```py
texto = "12345"
print(texto.isdigit())  # Resultado: True
texto2 = "12a45"
print(texto2.isdigit())  # Resultado: False
```