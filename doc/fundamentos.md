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
8. [Formatação de Strings com `f-strings`](#formatação-de-strings-com-f-strings)
    - 8.1. [Formatação Básica](#formatação-básica)
    - 8.2. [Especificadores de Formato](#especificadores-de-formato)
    - 8.3. [Alinhamento e Preenchimento](#alinhamento-e-preenchimento)
    - 8.4. [Formatação de Números](#formatação-de-números)
    - 8.5. [Conversion Flags](#conversion-flags)
    - 8.6. [Outros Exemplos Completos](#outros-exemplos-completos)
9. [Formatação de Strings com o Método `.format()`](#formatação-de-strings-com-o-método-format)
    - 9.1. [Parâmetros Nomeados](#parâmetros-nomeados)
    - 9.2. [Índices no `.format()`](#índices-no-format)
10. [Função `input()`](#função-input)
    - 10.1. [Convertendo a Entrada de Dados](#convertendo-a-entrada-de-dados)
11. [Blocos de Código e Condicionais (`if`, `elif`, `else`)](#blocos-de-código-e-condicionais-if-elif-else)
    - 11.1. [Estrutura Básica](#estrutura-básica)
    - 11.2. [Múltiplas Condições com `if`, `elif` e `else`](#múltiplas-condições-com-if-elif-e-else)
12. [Operadores de Comparação (Relacionais)](#operadores-de-comparação-relacionais)
13. [Operadores Logicos](#operadores-lógicos)
    - 13.1. [Operador `and` (E)](#operador-and-e)
    - 13.2. [Operador `or` (Ou)](#operador-or-ou)
    - 13.3. [Operador `not` (Não)](#operador-not-não)
14. [Operadores de Associação `in` e `not in`](#operadores-de-associação-in-e-not-in)
    - 14.1. [Valores "False" em Python](#valores-false-em-python)
15. [Interpolação de Strings com `%`](#interpolação-de-strings-com-)

---

### Função `print()`

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
print(12, 34, sep="-") # Retorna: 12-34
``` 

**Parâmetro Qebra Linha `end`:** Serve para fazer a quebra de linha.

**Exemplo 01:**
``` py
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

**3.** `.capitalize()`

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

---

### Formatação de Strings com `f-strings`

As **f-strings** (format strings) são uma forma prática, moderna e legível de inserir variáveis e expressões dentro de strings, utilizando o prefixo `f` antes das aspas. Elas foram introduzidas no Python 3.6 e são amplamente utilizadas devido à sua simplicidade e flexibilidade.

#### Formatação Básica

Você pode inserir variáveis diretamente dentro de uma string utilizando `{}`.

**Exemplo:**
```py
nome = 'Camaleão'
print(f'Olá, {nome}')  # Retorna: Olá, Camaleão
```

Além de variáveis, você pode usar expressões e até métodos diretamente dentro das chaves `{}`.

**Exemplo:**
```py
a = 10
b = 20
print(f'A soma de {a} + {b} é {a + b}')  # Retorna: A soma de 10 + 20 é 30
```

#### Especificadores de Formato

Os **especificadores de formato** permitem controlar como os valores são exibidos. Aqui estão os principais:

| Especificador | Descrição                          | Exemplo (`f-string`)         |
|---------------|------------------------------------|------------------------------|
| `s`           | String                            | `f'{variavel:s}'`            |
| `d`           | Inteiro (decimal)                 | `f'{variavel:d}'`            |
| `f`           | Float (número decimal)            | `f'{variavel:.2f}'`          |
| `x` ou `X`    | Hexadecimal (minúsculo/maiúsculo) | `f'{variavel:x}'` ou `f'{variavel:X}'` |

#### Alinhamento e Preenchimento

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
variavel = 'ABC'

print(f'{variavel: >10}')  # Alinha à direita com 10 caracteres: '       ABC'
print(f'{variavel: <10}.')  # Alinha à esquerda com 10 caracteres: 'ABC       .'
print(f'{variavel: ^10}.')  # Centraliza com 10 caracteres: '   ABC    .'
```

#### Formatação de Números

Você pode formatar números com separadores de milhares, casas decimais e sinais.

**Exemplos:**
```py
# Número com separador de milhares, 1 casa decimal, preenchido com zeros e sinal positivo
print(f'{1000.4873648123746:0=+10,.1f}')  # Retorna: +001,000.5

# Exibindo um número em hexadecimal com 8 caracteres, preenchido com zeros
print(f'O hexadecimal de 1500 é {1500:08X}')  # Retorna: O hexadecimal de 1500 é 000005DC
```

#### Conversion Flags

As **conversion flags** permitem exibir representações específicas de valores:

| Flag | Descrição                          | Exemplo (`f-string`)         |
|------|------------------------------------|------------------------------|
| `!r` | Representação oficial (usando `repr()`) | `f'{variavel!r}'`            |
| `!s` | Representação como string (usando `str()`) | `f'{variavel!s}'`            |
| `!a` | Representação ASCII                | `f'{variavel!a}'`            |

**Exemplo:**
```py
variavel = 'ABC'
print(f'{variavel!r}')  # Retorna: 'ABC'
```

#### Outros Exemplos Completos

**Exemplo 1: Formatação de Strings**
```py
nome = 'Luiz'
idade = 30
print(f'{nome} tem {idade} anos.')  # Retorna: Luiz tem 30 anos.
```

**Exemplo 2: Formatação de Números**
```py
preco = 1234.56789
print(f'Preço formatado: R${preco:.2f}')  # Retorna: Preço formatado: R$1234.57
```

**Exemplo 3: Alinhamento e Preenchimento**
```py
variavel = 'Python'
print(f'{variavel:*>10}')  # Retorna: ****Python
print(f'{variavel:*<10}')  # Retorna: Python****
print(f'{variavel:*^10}')  # Retorna: **Python**
```

**Exemplo 4: Hexadecimal**
```py
numero = 255
print(f'Hexadecimal: {numero:08X}')  # Retorna: Hexadecimal: 000000FF
```

*Observações:*

- As **f-strings** são recomendadas para formatação de strings em Python devido à sua legibilidade e eficiência.
- Para versões de Python anteriores ao 3.6, você pode usar o método `.format()` ou a interpolação com `%`.

```py
# Comparação com .format() e %
nome = 'Luiz'
preco = 1000.95

# Usando f-strings
print(f'{nome}, o preço é R${preco:.2f}')  # Luiz, o preço é R$1000.95

# Usando .format()
print('{}, o preço é R${:.2f}'.format(nome, preco))  # Luiz, o preço é R$1000.95

# Usando %
print('%s, o preço é R$%.2f' % (nome, preco))  # Luiz, o preço é R$1000.95
```

---

### Formatação de Strings com o Método `.format()`

O método `.format()` é usado para substituir os `{}` em uma string pelos valores passados como argumentos. Ele é uma alternativa às **f-strings** e permite maior flexibilidade, como o uso de **parâmetros nomeados**.

**Exemplo:**
```py
a = 'AAAAA'
b = 'B'
c = 1.1
string = 'a={nome1} b={nome2} c={nome3:.2f}'  # Formato da string
formato = string.format(
    nome1=a, nome2=b, nome3=c
)  # Substitui os {} pelos valores passados
print(formato)  # Saída: a=AAAAA b=B c=1.10
```

#### Parâmetros Nomeados

Os **parâmetros nomeados** são argumentos passados com um nome dentro das chamadas das funções. Isso torna o código mais legível e organizado, pois você pode identificar facilmente o que cada valor representa.

**Exemplo:**
```py
string = 'Olá, {nome}! Você tem {idade} anos.'
resultado = string.format(nome='João', idade=25)
print(resultado)  # Saída: Olá, João! Você tem 25 anos.
```


#### Índices no `.format()`

Se você não usar nomes nos `{}`, pode passar os valores por **índices**. Lembre-se de que os índices começam em `0`.

**Exemplo:**
```py
string = 'a={0} b={1} c={2:.2f}'
formato = string.format('AAAAA', 'B', 1.1)
print(formato)  # Saída: a=AAAAA b=B c=1.10
```

*Observações:*

- O método `.format()` é útil para versões de Python anteriores ao 3.6, onde as **f-strings** não estão disponíveis.
- Para formatação mais moderna e legível, prefira **f-strings** quando possível.

---

### Função `input()`

A função `input()` é usada para capturar a entrada de dados do usuário. O valor retornado por `input()` é sempre uma string, mesmo que o usuário digite números.

**Exemplo:**
```py
nome = input("Qual é o seu nome? ")
print(f"Olá, {nome}! Seja bem-vindo.")
```

#### Convertendo a Entrada de Dados

Se você precisar trabalhar com números, é necessário converter a entrada de dados de string para `int` ou `float`.

**Exemplo de Conversão:**
```py
numero = int(input("Digite um número: "))
print(f"Você digitou o número: {numero}")
```

*Dica:* A partir do Python 3.8, você pode usar a sintaxe `f'{variavel=}'` para exibir o nome da variável junto com seu valor:

```py
nome = input("Qual é o seu nome? ")
print(f"{nome=}")  # Saída: nome='João'
```

---

### Blocos de Código e Condicionais (`if`, `elif`, `else`)

Em Python, os **blocos de código** são definidos pela **indentação** (espaços ou tabulação no início da linha). Eles são usados para agrupar instruções que devem ser executadas juntas, como em estruturas condicionais.

As estruturas condicionais permitem que o programa tome decisões com base em condições específicas. Em Python, usamos as palavras-chave `if`, `elif` e `else` para criar essas condições.

#### Estrutura Básica

- **`if`**: Executa um bloco de código se a condição for verdadeira.
- **`elif`**: (abreviação de "else if") Verifica outra condição se a anterior for falsa.
- **`else`**: Executa um bloco de código se nenhuma das condições anteriores for verdadeira.

**Exemplo 1:**
```py
entrada = input('Você quer "entrar" ou "sair"? ')

if entrada == 'entrar':
    print('Você entrou no sistema')
    print(12341234)
elif entrada == 'sair':
    print('Você saiu do sistema')
else:
    print('Você não digitou nem entrar e nem sair.')

print('FORA DOS BLOCOS')
```

**Explicação:**
1. O programa verifica a entrada do usuário.
2. Se o usuário digitar `"entrar"`, o bloco do `if` será executado.
3. Se o usuário digitar `"sair"`, o bloco do `elif` será executado.
4. Caso contrário, o bloco do `else` será executado.
5. O código fora dos blocos será executado independentemente das condições.

#### Múltiplas Condições com `if`, `elif` e `else`

Você pode usar várias condições para controlar o fluxo do programa.

**Exemplo 2:**
```py
condicao1 = True
condicao2 = True
condicao3 = True
condicao4 = True

if condicao1:
    print('Código para condição 1')
    print('Código para condição 1')
elif condicao2:
    print('Código para condição 2')
elif condicao3:
    print('Código para condição 3')
elif condicao4:
    print('Código para condição 4')
else:
    print('Nenhuma condição foi satisfeita.')
```

**Explicação:**
1. O programa verifica as condições na ordem em que aparecem.
2. Assim que uma condição for verdadeira, o bloco correspondente será executado e as demais condições serão ignoradas.


*Observações:*

- **Indentação**: A indentação é obrigatória em Python para definir blocos de código. Certifique-se de usar a mesma quantidade de espaços em um bloco.
- **Fluxo do Interpretador**: O interpretador avalia as condições na ordem em que aparecem. Assim que uma condição for verdadeira, ele executa o bloco correspondente e ignora os demais.
- **Condições Independentes**: Você pode usar múltiplos `if` independentes, mas isso significa que todas as condições serão avaliadas, mesmo que uma delas já tenha sido verdadeira.

---

### Operadores de Comparação (Relacionais)

Os **operadores de comparação** são usados para comparar dois valores. O resultado de uma comparação é sempre um valor booleano (`True` ou `False`).

| Operador | Significado         | Exemplo (`True`) |
|----------|---------------------|------------------|
| `>`      | Maior               | `2 > 1`          |
| `>=`     | Maior ou igual      | `2 >= 2`         |
| `<`      | Menor               | `1 < 2`          |
| `<=`     | Menor ou igual      | `2 <= 2`         |
| `==`     | Igual               | `'a' == 'a'`     |
| `!=`     | Diferente           | `'a' != 'b'`     |

**Exemplo:**
```py
# Comparações básicas
maior = 2 > 1
maior_ou_igual = 2 >= 2
menor = 1 < 2
menor_ou_igual = 2 <= 2
igual = 'a' == 'a'
diferente = 'a' != 'b'

# Exibindo os resultados
print('Maior:', maior)  # True
print('Maior ou igual:', maior_ou_igual)  # True
print('Menor:', menor)  # True
print('Menor ou igual:', menor_ou_igual)  # True
print('Igual:', igual)  # True
print('Diferente:', diferente)  # True
```

*Observações:*
- Os operadores de comparação são frequentemente usados em estruturas condicionais, como `if`, para tomar decisões com base em condições.
- Comparações podem ser feitas entre números, strings e outros tipos de dados, desde que sejam compatíveis.

---

### Operadores Lógicos

Os **operadores lógicos** são usados para combinar expressões condicionais e tomar decisões com base em múltiplas condições. Em Python, os principais operadores lógicos são:

| Operador | Significado | Descrição                                                                 |
|----------|-------------|---------------------------------------------------------------------------|
| `and`    | E           | Todas as condições precisam ser verdadeiras para o resultado ser `True`. |
| `or`     | Ou          | Pelo menos uma condição precisa ser verdadeira para o resultado ser `True`. |
| `not`    | Não         | Inverte o valor lógico de uma expressão (`True` vira `False` e vice-versa). |

#### Operador `and` (E)

O operador `and` avalia como `True` apenas se **todas as condições** forem verdadeiras. Se qualquer valor for considerado falso, a expressão inteira será avaliada como `False`.

**Exemplo:**
```py
entrada = input('[E]ntrar [S]air: ')
senha_digitada = input('Senha: ')

senha_permitida = '123456'

if entrada == 'E' and senha_digitada == senha_permitida:
    print('Entrar')
else:
    print('Sair')
```

**Avaliação de Curto-Circuito com `and`:**
Se uma condição for avaliada como `False`, o Python não verifica as condições seguintes, pois o resultado já será `False`.

**Exemplo:**
```py
print(True and False and True)  # False
print(True and 0 and True)      # 0 (0 é considerado "false")
```

#### Operador `or` (Ou)

O operador `or` avalia como `True` se **pelo menos uma condição** for verdadeira. Se todas as condições forem falsas, o resultado será `False`.

**Exemplo:**
```py
entrada = input('[E]ntrar [S]air: ')
senha_digitada = input('Senha: ')

senha_permitida = '123456'

if (entrada == 'E' or entrada == 'e') and senha_digitada == senha_permitida:
    print('Entrar')
else:
    print('Sair')
```

**Avaliação de Curto-Circuito com `or`:**
Se uma condição for avaliada como `True`, o Python não verifica as condições seguintes, pois o resultado já será `True`.

**Exemplo:**
```py
senha = input('Senha: ') or 'Sem senha'
print(senha)  # Se o usuário não digitar nada, será exibido "Sem senha".
```

#### Operador `not` (Não)

O operador `not` é usado para inverter o valor lógico de uma expressão. Se a expressão for `True`, o resultado será `False`, e vice-versa.

**Exemplo:**
```py
print(not True)   # False
print(not False)  # True
```

**Resumo dos Operadores Lógicos:**

1. **`and`**: Todas as condições precisam ser verdadeiras.
2. **`or`**: Pelo menos uma condição precisa ser verdadeira.
3. **`not`**: Inverte o valor lógico de uma expressão.

---

### Operadores de Associação `in` e `not in`

Os operadores `in` e `not in` são usados para verificar se um valor está (ou não está) presente em uma sequência, como strings, listas ou tuplas.

| Operador   | Significado                  | Exemplo (`True`)         |
|------------|------------------------------|--------------------------|
| `in`       | Está presente na sequência   | `'a' in 'Python'`        |
| `not in`   | Não está presente na sequência | `'z' not in 'Python'`    |

**Exemplo com Strings:**
```py
nome = input('Digite seu nome: ')
encontrar = input('Digite o que deseja encontrar: ')

if encontrar in nome:
    print(f'{encontrar} está em {nome}')
else:
    print(f'{encontrar} não está em {nome}')
```

**Exemplo com Índices:**
```py
nome = 'Otávio'
print(nome[2])       # Resultado: á
print(nome[-4])      # Resultado: á
print('vio' in nome) # Resultado: True
print('zero' in nome) # Resultado: False
```

#### Valores "False" em Python

Os seguintes valores são considerados **falsos** em Python (false):
- `0`
- `0.0`
- `''` (string vazia)
- `False`
- `None` (representa a ausência de valor)

**Exemplo:**
```py
if not 0:
    print('0 é considerado falso')  # Será exibido
```

**Resumo dos Operadores de Associação:**

1. **`in` / `not in`**: Verifica se um valor está (ou não está) presente em uma sequência.

```py
# Exemplo completo:
nome = 'Python'
print('P' in nome)       # True
print('z' not in nome)   # True
print(not ('P' in nome)) # False
```

---

### Interpolação de Strings com `%`

A interpolação de strings com `%` é uma forma antiga, mas ainda funcional, de formatar strings em Python. Ela utiliza especificadores de formato para inserir valores em uma string.

**Especificadores de Formato**

| Especificador | Descrição                          | Exemplo (`%`)       |
|---------------|------------------------------------|---------------------|
| `%s`          | String                            | `'Olá %s' % 'Mundo'` |
| `%d` ou `%i`  | Inteiro (decimal)                 | `'Número: %d' % 10` |
| `%f`          | Float (número decimal)            | `'Preço: %.2f' % 10.5` |
| `%x` ou `%X`  | Hexadecimal (minúsculo/maiúsculo) | `'%x' % 255` ou `'%X' % 255` |

**Exemplos**

**Interpolação Básica:**
```py
nome = 'Luiz'
preco = 1000.95897643
variavel = '%s, o preço é R$%.2f' % (nome, preco)

print(variavel)  # Saída: Luiz, o preço é R$1000.96
```

**Hexadecimal:**
```py
numero = 1500
print('O hexadecimal de %d é %08X' % (numero, numero))
# Saída: O hexadecimal de 1500 é 000005DC
```

**Detalhes Importantes**

1. **Especificadores de Precisão:**
   - Para números decimais (`%f`), você pode controlar o número de casas decimais usando `%.nf`, onde `n` é o número de casas desejadas.
   - Exemplo:
     ```py
     preco = 123.456789
     print('Preço: %.2f' % preco)  # Saída: Preço: 123.46
     ```

2. **Preenchimento com Zeros:**
   - Para inteiros, você pode preencher com zeros à esquerda usando `%0nd`, onde `n` é o número total de dígitos.
   - Exemplo:
     ```py
     numero = 42
     print('%05d' % numero)  # Saída: 00042
     ```

3. **Hexadecimal com Letras Maiúsculas ou Minúsculas:**
   - `%x` exibe o hexadecimal em letras minúsculas.
   - `%X` exibe o hexadecimal em letras maiúsculas.
   - Exemplo:
     ```py
     numero = 255
     print('%x' % numero)  # Saída: ff
     print('%X' % numero)  # Saída: FF
     ```

*Observações*

- A interpolação com `%` é considerada **legada** e foi substituída por métodos mais modernos, como `.format()` e **f-strings** (a partir do Python 3.6).
- No entanto, ela ainda é amplamente usada em códigos antigos e em situações específicas.

**Exemplo Comparativo com f-strings:**
```py
# Usando %
nome = 'Luiz'
preco = 1000.95
print('%s, o preço é R$%.2f' % (nome, preco))  # Luiz, o preço é R$1000.95

# Usando f-strings
print(f'{nome}, o preço é R${preco:.2f}')  # Luiz, o preço é R$1000.95
```

---

### Fatiamento de Strings

O **fatiamento de strings** permite acessar partes específicas de uma string, utilizando a notação `[início:fim:passo]`. Essa técnica é muito útil para manipular textos em Python.

#### Índices em Strings

Cada caractere de uma string possui um índice, que pode ser positivo (da esquerda para a direita) ou negativo (da direita para a esquerda).

**Exemplo de Índices:**
```
  012345678   (índices positivos)
  Olá mundo
 -987654321   (índices negativos)
```

#### Sintaxe do Fatiamento

A notação para fatiamento é `[início:fim:passo]`:
- **`início`**: Índice onde o fatiamento começa (inclusivo).
- **`fim`**: Índice onde o fatiamento termina (exclusivo).
- **`passo`**: Define o intervalo entre os caracteres (padrão é `1`).

**Exemplo:**
```py
variavel = 'Olá mundo'
print(variavel[4:])      # Saída: mundo (do índice 4 até o final)
print(variavel[0:9:1])   # Saída: Olá mundo (do índice 0 ao 8, com passo 1)
print(variavel[::-1])    # Saída: odnum álO (string invertida)
```

*Observações*

1. **Omissão de Parâmetros:**
   - Se você omitir o `início`, o fatiamento começará do início da string.
   - Se você omitir o `fim`, o fatiamento irá até o final da string.
   - Se você omitir o `passo`, o padrão será `1`.

   **Exemplo:**
   ```py
   variavel = 'Olá mundo'
   print(variavel[:5])   # Saída: Olá m (do início até o índice 4)
   print(variavel[::2])  # Saída: Oámno (caracteres com passo 2)
   ```

2. **Passo Negativo:**
   - Um passo negativo inverte a string ou o intervalo especificado.

   **Exemplo:**
   ```py
   variavel = 'Olá mundo'
   print(variavel[::-1])  # Saída: odnum álO (string invertida)
   ```

---

### Função `len`

A função **`len`** retorna a quantidade de caracteres de uma string (incluindo espaços).

**Exemplo:**
```py
variavel = 'Olá mundo'
print(len(variavel))  # Saída: 9 (conta todos os caracteres, incluindo o espaço)
```

---