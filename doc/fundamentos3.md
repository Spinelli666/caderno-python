# Fundamentos 3

## Sumário

1. [Estruturas de Repetição: `while` e `break`](#1-estruturas-de-repetição-while-e-break)
    - 1.1. [Repetições com `while`](#11-repetições-com-while)
    - 1.2. [Boas Práticas com `while`](#12-boas-práticas-com-while)
2. [Operadores de Atribuição com Operadores Aritméticos](#2-operadores-de-atribuição-com-operadores-aritméticos)
    - 2.1. [Operadores de Atribuição](#21-operadores-de-atribuição)
    - 2.2. [Exemplos Práticos](#22-exemplos-práticos)
3. [Estruturas de Repetição: `for` e `range`](#3-estruturas-de-repetição-for-e-range)
    - 3.1. [Introdução ao `for` e Iteração em Python](#31-introdução-ao-for-e-iteração-em-python)
    - 3.2. [Como o `for` Funciona por Baixo dos Panos](#32-como-o-for-funciona-por-baixo-dos-panos)
    - 3.3. [Boas Práticas com `for`](#33-boas-práticas-com-for)
4. [Introdução às Listas Mutáveis](#4-introdução-às-listas-mutáveis)
    - 4.1. [O Tipo `list`](#41-o-tipo-list)
    - 4.2. [Alterando Listas com Índices, `del`, `append` e `pop`](#42-alterando-listas-com-índices-del-append-e-pop)
    - 4.3. [Inserindo Itens em Qualquer Índice com `insert`](#43-inserindo-itens-em-qualquer-índice-com-insert)
    - 4.4. [Concatenando e Estendendo Listas](#44-concatenando-e-estendendo-listas)
    - 4.5. [Cuidados com Tipos de Dados Mutáveis](#45-cuidados-com-tipos-de-dados-mutáveis)
    - 4.6. [Iterando com `for in` em Listas](#46-iterando-com-for-in-em-listas)
    - 4.7. [Exercício: Exiba os Índices da Lista](#47-exercício-exiba-os-índices-da-lista)
5. [Imprecisão de Números de Ponto Flutuante](#5-imprecisão-de-números-de-ponto-flutuante)
    - 5.1. [O Problema da Precisão](#51-o-problema-da-precisão)
    - 5.2. [Usando `round` para Arredondamento](#52-usando-round-para-arredondamento)
    - 5.3. [Usando `decimal.Decimal` para Maior Precisão](#53-usando-decimaldecimal-para-maior-precisão)
6. [Métodos Úteis de Strings: `split`, `join` e `strip`](#6-métodos-úteis-de-strings-split-join-e-strip)
    - 6.1. [Método `split`](#61-método-split)
    - 6.2. [Método `join`](#62-método-join)
    - 6.3. [Método `strip`](#63-método-strip)
    - 6.4. [Exemplo Prático com `split`, `join` e `strip`](#64-exemplo-prático-com-split-join-e-strip)
7. [Listas Dentro de Listas (Iteráveis Dentro de Iteráveis)](#7-listas-dentro-de-listas-iteráveis-dentro-de-iteráveis)
    - 7.1. [Acessando Elementos em Listas de Listas](#71-acessando-elementos-em-listas-de-listas)
    - 7.2. [Iterando Sobre Listas de Listas](#72-iterando-sobre-listas-de-listas)
8. [Detalhes sobre o Interpretador do Python](#8-detalhes-sobre-o-interpretador-do-python)
    - 8.1. [Comandos Úteis do Interpretador](#81-comandos-úteis-do-interpretador)

---

## 1. Estruturas de Repetição: `while` e `break`

### 1.1. Repetições com `while`

O comando **`while`** é usado para executar um bloco de código repetidamente enquanto uma condição for verdadeira. Ele é útil para criar **laços de repetição** quando não sabemos previamente o número exato de iterações.

#### Estrutura Básica

```py
while condição:
    # Código a ser executado enquanto a condição for verdadeira
```

- **`while`**: Significa "enquanto". O bloco será executado enquanto a condição for avaliada como `True`.
- **Loop infinito**: Ocorre quando a condição nunca se torna `False`, fazendo o código rodar indefinidamente.

#### Exemplos

**Exemplo 1: Loop Simples com `while`**

```py
condicao = True

while condicao:
    nome = input('Qual o seu nome: ')
    print(f'Seu nome é {nome}')

    if nome == 'sair':  # Interrompe o loop se o usuário digitar "sair"
        break

print('Acabou')
```

**Explicação:**
1. O loop continua pedindo o nome do usuário enquanto a condição for `True`.
2. Se o usuário digitar `"sair"`, o comando `break` interrompe o loop.

**Exemplo 2: Contador Simples**

```py
contador = 0

while contador <= 10:
    contador = contador + 1
    print(contador)

print('Acabou')
```

**Explicação:**
1. O loop começa com o valor de `contador` igual a `0`.
2. A cada iteração, o valor de `contador` é incrementado em `1`.
3. O loop termina quando `contador` ultrapassa `10`.

**Exemplo 3: Usando `continue` e `break`**

```py
contador = 0

while contador <= 100:
    contador += 1

    if contador == 6:
        print('Não vou mostrar o 6.')
        continue  # Pula para a próxima iteração

    if 10 <= contador <= 27:
        print('Não vou mostrar o', contador)
        continue  # Pula para a próxima iteração

    print(contador)

    if contador == 40:
        break  # Interrompe o loop quando contador for 40

print('Acabou')
```

**Explicação:**
1. O loop incrementa o valor de `contador` até `100`.
2. O comando `continue` é usado para pular a exibição de números específicos:
   - Não exibe o número `6`.
   - Não exibe os números entre `10` e `27`.
3. O comando `break` interrompe o loop quando `contador` atinge `40`.

**Exemplo 4: Laços Aninhados com `while`**

```py
qtd_linhas = 5
qtd_colunas = 5

linha = 1
while linha <= qtd_linhas:
    coluna = 1
    while coluna <= qtd_colunas:
        print(f'{linha=} {coluna=}')
        coluna += 1
    linha += 1

print('Acabou')
```

**Explicação:**
1. O loop externo controla as linhas (`linha`).
2. O loop interno controla as colunas (`coluna`).
3. Para cada linha, o loop interno percorre todas as colunas.

### 1.2. Boas Práticas com `while`

1. **Evite loops infinitos desnecessários**:
   - Certifique-se de que a condição do `while` eventualmente se tornará `False`.
   - Exemplo de loop infinito (ruim):
     ```py
     while True:
         print('Isso nunca vai parar!')
     ```

2. **Use `break` para interromper o loop quando necessário**:
   - O comando `break` é útil para sair de um loop antes que a condição se torne `False`.

3. **Use `continue` para pular iterações específicas**:
   - O comando `continue` permite ignorar o restante do código no loop e passar para a próxima iteração.

4. **Evite loops muito complexos**:
   - Divida o código em partes menores e mais legíveis, especialmente ao usar loops aninhados.

---


## 2. Operadores de Atribuição com Operadores Aritméticos

Os **operadores de atribuição** são usados para atribuir valores a variáveis. Em Python, podemos combinar operadores aritméticos com o operador de atribuição (`=`) para simplificar operações matemáticas.

### 2.1. Operadores de Atribuição

| Operador | Descrição                          | Exemplo                  | Equivalente a         |
|----------|------------------------------------|--------------------------|-----------------------|
| `=`      | Atribuição simples                 | `x = 10`                 | -                     |
| `+=`     | Adição e atribuição                | `x += 5`                 | `x = x + 5`           |
| `-=`     | Subtração e atribuição             | `x -= 3`                 | `x = x - 3`           |
| `*=`     | Multiplicação e atribuição         | `x *= 2`                 | `x = x * 2`           |
| `/=`     | Divisão e atribuição               | `x /= 4`                 | `x = x / 4`           |
| `//=`    | Divisão inteira e atribuição       | `x //= 3`                | `x = x // 3`          |
| `**=`    | Exponenciação e atribuição         | `x **= 2`                | `x = x ** 2`          |
| `%=`     | Módulo (resto) e atribuição        | `x %= 3`                 | `x = x % 3`           |

### 2.2. Exemplos Prático

**Exemplo 1: Operadores de Atribuição Básicos**

```py
contador = 10

# Adição e atribuição
contador += 5  # Equivalente a contador = contador + 5
print(contador)  # Saída: 15

# Subtração e atribuição
contador -= 3  # Equivalente a contador = contador - 3
print(contador)  # Saída: 12

# Multiplicação e atribuição
contador *= 2  # Equivalente a contador = contador * 2
print(contador)  # Saída: 24

# Divisão e atribuição
contador /= 4  # Equivalente a contador = contador / 4
print(contador)  # Saída: 6.0
```

**Exemplo 2: Operadores de Atribuição Avançados**

```py
contador = 10

# Divisão inteira e atribuição
contador //= 3  # Equivalente a contador = contador // 3
print(contador)  # Saída: 3

# Exponenciação e atribuição
contador **= 2  # Equivalente a contador = contador ** 2
print(contador)  # Saída: 9

# Módulo e atribuição
contador %= 4  # Equivalente a contador = contador % 4
print(contador)  # Saída: 1
```

---

## 3. Estruturas de Repetição: `for` e `range`

### 3.1. Introdução ao `for` e Iteração em Python

O comando **`for`** é usado para iterar sobre elementos de um **iterável** (como strings, listas, tuplas, dicionários, ou objetos do tipo `range`). Ele é ideal para situações em que sabemos previamente o número de iterações ou queremos percorrer elementos de uma sequência finita.

#### Estrutura Básica do `for`

```py
for elemento in iterável:
    # Código a ser executado para cada elemento
```

- **`elemento`**: Representa o item atual da sequência que está sendo iterado.
- **`iterável`**: É o objeto que contém os elementos a serem percorridos (como uma string, lista, ou `range`).

#### Exemplos

**Exemplo 1: Iteração Simples com Strings**

```py
texto = 'Python'

novo_texto = ''
for letra in texto:
    novo_texto += f'*{letra}'
    print(letra)

print(novo_texto + '*')
```

**Explicação:**
1. O `for` percorre cada caractere da string `texto`.
2. A cada iteração, a variável `letra` recebe o caractere atual.
3. O código dentro do `for` é executado para cada caractere.
4. O resultado final é uma string com cada letra precedida por `*`.

#### `for` com `range`

A função **`range`** é usada para gerar uma sequência de números. Ela é frequentemente combinada com o `for` para criar laços de repetição baseados em intervalos numéricos.

#### Estrutura do `range`

```py
range(start, stop, step)
```

- **`start`**: (Opcional) O número inicial da sequência (padrão é `0`).
- **`stop`**: O número final da sequência (não incluído).
- **`step`**: (Opcional) O intervalo entre os números (padrão é `1`).

**Exemplo 2: Iteração com `range`**

```py
numeros = range(0, 100, 8)

for numero in numeros:
    print(numero)
```

**Explicação:**
1. O `range(0, 100, 8)` gera números de `0` a `99`, com um passo de `8`.
2. O `for` percorre cada número gerado pelo `range` e executa o código dentro do bloco.

### 3.2. Como o `for` Funciona por Baixo dos Panos

Em Python, o `for` funciona com base no conceito de **iteráveis** e **iteradores**.

#### Conceitos Importantes

1. **Iterável**:
   - Um objeto que pode ser percorrido (como strings, listas, tuplas, dicionários, ou `range`).
   - Possui o método especial `__iter__()` que retorna um **iterador**.

2. **Iterador**:
   - Um objeto que sabe como entregar um elemento por vez.
   - Possui o método especial `__next__()` que retorna o próximo elemento da sequência.
   - Quando não há mais elementos, ele levanta a exceção `StopIteration`.

3. **Função `iter`**:
   - Retorna o iterador de um iterável.

4. **Função `next`**:
   - Retorna o próximo elemento do iterador.

**Exemplo 3: Iteração Manual com `iter` e `next`**

```py
texto = 'Python'  # Iterável

iterador = iter(texto)  # Obtém o iterador do iterável

while True:
    try:
        letra = next(iterador)  # Obtém o próximo elemento
        print(letra)
    except StopIteration:
        break  # Interrompe o loop quando não há mais elementos
```

**Explicação:**
1. A função `iter(texto)` retorna um iterador para a string `texto`.
2. A função `next(iterador)` retorna o próximo caractere da string.
3. Quando todos os caracteres são consumidos, a exceção `StopIteration` é levantada, e o loop é interrompido.

**Exemplo 4: Comparação entre `for` e Iteração Manual**

O código abaixo demonstra como o `for` é equivalente a usar `iter` e `next` manualmente:

```py
# Usando for
for letra in 'Python':
    print(letra)

# Equivalente a:
iterador = iter('Python')
while True:
    try:
        letra = next(iterador)
        print(letra)
    except StopIteration:
        break
```

### 3.3. Boas Práticas com `for`

1. **Use `for` para Iterações Finitas**:
   - O `for` é ideal para percorrer sequências finitas, como listas, strings ou intervalos gerados por `range`.

2. **Evite Modificar o Iterável Durante a Iteração**:
   - Alterar o iterável enquanto ele está sendo percorrido pode causar comportamentos inesperados.

3. **Combine `for` com Funções como `enumerate` e `zip`**:
   - Use `enumerate` para obter o índice e o valor de cada elemento.
   - Use `zip` para iterar sobre múltiplas sequências simultaneamente.

**Exemplo 5: Uso de `enumerate`**

```py
frutas = ['maçã', 'banana', 'cereja']

for indice, fruta in enumerate(frutas):
    print(f'{indice}: {fruta}')
```

**Saída:**
```
0: maçã
1: banana
2: cereja
```

**Exemplo 6: Uso de `zip`**

```py
nomes = ['Ana', 'João', 'Maria']
idades = [25, 30, 22]

for nome, idade in zip(nomes, idades):
    print(f'{nome} tem {idade} anos.')
```

**Saída:**
```
Ana tem 25 anos.
João tem 30 anos.
Maria tem 22 anos.
```

---

## 4. Introdução às Listas Mutáveis

### 4.1. O Tipo `list`

As listas em Python são um tipo de dado **mutável**, o que significa que seus valores podem ser alterados após a criação. Elas suportam múltiplos valores de qualquer tipo e permitem o uso de **índices** e **fatiamento** para acessar ou modificar seus elementos.

**Características:**
- Tipo: `list`
- Mutável
- Suporta vários valores de qualquer tipo
- Métodos úteis: `append`, `insert`, `pop`, `del`, `clear`, `extend`, `+`

**Exemplo:**
```py
#        +01234
#        -54321
string = 'ABCDE'  # 5 caracteres (len)

# Lista com diferentes tipos de dados
#        0    1      2              3    4
#       -5   -4     -3             -2   -1
lista = [123, True, 'Luiz Otávio', 1.2, []]
lista[-3] = 'Maria'
print(lista)
print(lista[2], type(lista[2]))
```

### 4.2. Alterando Listas com Índices, `del`, `append` e `pop`

As listas permitem criar, ler, alterar e apagar elementos (CRUD) utilizando índices e métodos específicos.

**Métodos úteis:**
- `append`: Adiciona um item ao final da lista.
- `pop`: Remove e retorna o último item ou o item no índice especificado.
- `del`: Apaga um item no índice especificado.
- `clear`: Limpa todos os itens da lista.

**Exemplo:**
```py
#        0   1   2   3   4   5
lista = [10, 20, 30, 40]
lista.append(50)  # Adiciona 50 ao final
lista.pop()       # Remove o último item
lista.append(60)
lista.append(70)
ultimo_valor = lista.pop(3)  # Remove o item no índice 3
print(lista, 'Removido,', ultimo_valor)
```

### 4.3. Inserindo Itens em Qualquer Índice com `insert`

O método `insert` permite adicionar um item em qualquer índice da lista.

**Sintaxe:**
```py
lista.insert(indice, valor)
```

**Exemplo:**
```py
#        0   1   2   3
lista = [10, 20, 30, 40]
lista.append('Luiz')  # Adiciona 'Luiz' ao final
nome = lista.pop()    # Remove o último item
lista.append(1233)    # Adiciona 1233 ao final
del lista[-1]         # Remove o último item
lista.insert(100, 5)  # Insere 5 no índice 100 (adicionado ao final)
print(lista[4])
```

### 4.4. Concatenando e Estendendo Listas

Você pode combinar listas utilizando o operador `+` (concatenação) ou o método `extend` (extensão).

**Diferença:**
- `+`: Cria uma nova lista combinando as listas originais.
- `extend`: Modifica a lista original adicionando os elementos da outra lista.

**Exemplo:**
```py
lista_a = [1, 2, 3]
lista_b = [4, 5, 6]

# Concatenação
lista_c = lista_a + lista_b
print(lista_c)  # [1, 2, 3, 4, 5, 6]

# Extensão
lista_a.extend(lista_b)
print(lista_a)  # [1, 2, 3, 4, 5, 6]
```

### 4.5. Cuidados com Tipos de Dados Mutáveis

Em Python, ao trabalhar com tipos mutáveis como listas, é importante entender como a atribuição funciona:
- **Imutáveis**: Atribuir uma variável a outra copia o valor.
- **Mutáveis**: Atribuir uma variável a outra faz com que ambas apontem para o mesmo objeto na memória.

**Exemplo:**
```py
lista_a = ['Luiz', 'Maria', 1, True, 1.2]
lista_b = lista_a.copy()  # Cria uma cópia independente

lista_a[0] = 'Qualquer coisa'
print(lista_a)  # ['Qualquer coisa', 'Maria', 1, True, 1.2]
print(lista_b)  # ['Luiz', 'Maria', 1, True, 1.2]
```

### 4.6. Iterando com `for in` em Listas

O laço `for in` é uma maneira simples e eficiente de iterar sobre os elementos de uma lista.

**Exemplo:**
```py
lista = ['Maria', 'Helena', 'Luiz']

for nome in lista:
    print(nome, type(nome))
```

**Saída:**
```
Maria <class 'str'>
Helena <class 'str'>
Luiz <class 'str'>
```

### 4.7. Exercício: Exiba os Índices da Lista

**Descrição:**
Exiba os índices e os valores de uma lista utilizando o laço `for`.

**Exemplo:**
```py
lista = ['Maria', 'Helena', 'Luiz']
lista.append('João')

indices = range(len(lista))

for indice in indices:
    print(indice, lista[indice], type(lista[indice]))
```

**Saída:**
```
0 Maria <class 'str'>
1 Helena <class 'str'>
2 Luiz <class 'str'>
3 João <class 'str'>
```

---

## 5. Introdução ao Empacotamento e Desempacotamento

O **empacotamento** e **desempacotamento** são recursos do Python que permitem atribuir múltiplos valores a variáveis de forma prática e intuitiva.

### 5.1. Empacotamento

O empacotamento ocorre quando você agrupa múltiplos valores em uma única variável.

**Exemplo:**
```py
valores = 1, 2, 3, 4, 5  # Empacotando valores em uma tupla
print(valores)  # Saída: (1, 2, 3, 4, 5)
```

### 5.2. Desempacotamento

O desempacotamento ocorre quando você distribui os valores de uma sequência (como listas ou tuplas) em variáveis individuais.

**Exemplo:**
```py
a, b, c = [1, 2, 3]  # Desempacotando uma lista
print(a, b, c)  # Saída: 1 2 3
```

### 5.3. Uso do `*` no Desempacotamento

O operador `*` pode ser usado para capturar o restante dos valores durante o desempacotamento.

**Exemplo:**
```py
_, _, nome, *resto = ['Maria', 'Helena', 'Luiz', 'João', 'Carlos']
print(nome)  # Saída: Luiz
print(resto)  # Saída: ['João', 'Carlos']
```

---

## 6. Tipo `tuple` (Tuplas)

As **tuplas** são semelhantes às listas, mas possuem uma característica importante: **são imutáveis**. Isso significa que, após criadas, seus valores não podem ser alterados.

### 6.1. Características das Tuplas

- Tipo: `tuple`
- Imutável (não pode ser alterada após a criação)
- Suporta múltiplos valores de qualquer tipo
- Pode ser convertida para lista (e vice-versa)

**Exemplo de Criação:**
```py
nomes = ('Maria', 'Helena', 'Luiz')  # Criando uma tupla
print(nomes[-1])  # Saída: Luiz
print(nomes)  # Saída: ('Maria', 'Helena', 'Luiz')
```

### 6.2. Conversão entre Tupla e Lista

Você pode converter uma tupla para uma lista (para torná-la mutável) e vice-versa.

**Exemplo:**
```py
nomes = ('Maria', 'Helena', 'Luiz')  # Tupla
nomes_lista = list(nomes)  # Convertendo para lista
nomes_tupla = tuple(nomes_lista)  # Convertendo de volta para tupla
```

---

## 7. Enumerate: Enumerando Valores de Iteráveis

A função **`enumerate`** é usada para enumerar os elementos de um iterável, retornando pares de índice e valor. Isso é útil para acessar tanto o índice quanto o valor de cada elemento durante a iteração.

### 7.1. Estrutura do `enumerate`

O `enumerate` retorna um objeto iterável, onde cada elemento é uma tupla contendo:
1. O índice do elemento.
2. O valor do elemento.

**Exemplo Básico:**
```py
lista = ['Maria', 'Helena', 'Luiz']
for indice, nome in enumerate(lista):
    print(indice, nome)
```

**Saída:**
```
0 Maria
1 Helena
2 Luiz
```

### 7.2. Trabalhando com Tuplas do `enumerate`

O `enumerate` retorna tuplas, que podem ser desempacotadas diretamente no laço `for`.

**Exemplo:**
```py
lista = ['Maria', 'Helena', 'Luiz']
for item in enumerate(lista):
    indice, nome = item  # Desempacotando a tupla
    print(indice, nome)
```

**Saída:**
```
0 Maria
1 Helena
2 Luiz
```

### 7.3. Iterando sobre as Tuplas do `enumerate`

Você pode iterar sobre os valores das tuplas retornadas pelo `enumerate`.

**Exemplo:**
```py
lista = ['Maria', 'Helena', 'Luiz']
for tupla_enumerada in enumerate(lista):
    print('FOR da tupla:')
    for valor in tupla_enumerada:
        print(f'\t{valor}')
```

**Saída:**
```
FOR da tupla:
    0
    Maria
FOR da tupla:
    1
    Helena
FOR da tupla:
    2
    Luiz
```

---

## 5. Imprecisão de Números de Ponto Flutuante

Os números de ponto flutuante em Python (e em muitas outras linguagens de programação) seguem o padrão **IEEE 754** de precisão dupla. Esse formato é eficiente para cálculos, mas pode introduzir **imprecisões** devido à forma como os números são representados na memória.

### 5.1. O Problema da Precisão

Nem todos os números decimais podem ser representados exatamente como números binários. Isso pode levar a resultados inesperados em operações matemáticas.

**Exemplo:**
```py
numero_1 = 0.1
numero_2 = 0.7
numero_3 = numero_1 + numero_2

print(numero_3)  # Saída: 0.7999999999999999
```

**Por que isso acontece?**
- O número `0.1` não pode ser representado exatamente em binário, assim como `1/3` não pode ser representado exatamente em decimal.
- Isso resulta em pequenas diferenças que se acumulam em cálculos.

**Referências:**
- [Double-precision floating-point format (IEEE 754)](https://en.wikipedia.org/wiki/Double-precision_floating-point_format)
- [Documentação Oficial do Python sobre Ponto Flutuante](https://docs.python.org/pt-br/3/tutorial/floatingpoint.html)

### 5.2. Usando `round` para Arredondamento

A função **`round`** pode ser usada para arredondar números de ponto flutuante a um número específico de casas decimais.

**Sintaxe:**
```py
round(numero, ndigits)
```

- **`numero`**: O número a ser arredondado.
- **`ndigits`**: O número de casas decimais desejadas.

**Exemplo:**
```py
numero_1 = 0.1
numero_2 = 0.7
numero_3 = numero_1 + numero_2

print(numero_3)  # Saída: 0.7999999999999999
print(round(numero_3, 2))  # Saída: 0.8
```

**Observação:**
- O `round` resolve o problema visualmente, mas a imprecisão ainda existe internamente.

### 5.3. Usando `decimal.Decimal` para Maior Precisão

A classe **`decimal.Decimal`** da biblioteca padrão `decimal` oferece maior precisão para cálculos com números decimais. Ela é especialmente útil em aplicações financeiras ou científicas, onde a precisão é crítica.

**Como Funciona:**
- O `decimal.Decimal` armazena números como strings para evitar as imprecisões do ponto flutuante.
- Ele permite realizar cálculos com precisão arbitrária.

**Exemplo:**
```py
import decimal

numero_1 = decimal.Decimal('0.1')
numero_2 = decimal.Decimal('0.7')
numero_3 = numero_1 + numero_2

print(numero_3)  # Saída: 0.8
print(f'{numero_3:.2f}')  # Saída: 0.80
print(round(numero_3, 2))  # Saída: 0.8
```

**Vantagens do `decimal.Decimal`:**
- Precisão controlada.
- Evita os problemas de representação binária.

**Quando Usar:**
- Em cálculos financeiros.
- Quando a precisão é mais importante que a performance.

---

## 6. Métodos Úteis de Strings: `split`, `join` e `strip`

Os métodos `split`, `join` e `strip` são ferramentas poderosas para manipulação de strings em Python. Eles permitem dividir, unir e limpar strings de forma eficiente.

### 6.1. Método `split`

O método **`split`** divide uma string em uma lista de substrings com base em um delimitador especificado.

**Sintaxe:**
```py
string.split(sep=None, maxsplit=-1)
```

- **`sep`**: O delimitador usado para dividir a string (padrão é qualquer espaço em branco).
- **`maxsplit`**: O número máximo de divisões (padrão é `-1`, que significa sem limite).

**Exemplo:**
```py
frase = "Python é incrível"
lista_palavras = frase.split()  # Divide a string em palavras
print(lista_palavras)  # Saída: ['Python', 'é', 'incrível']
```

**Exemplo com delimitador:**
```py
frase = "Python,Java,C++"
linguagens = frase.split(',')  # Divide a string usando ',' como delimitador
print(linguagens)  # Saída: ['Python', 'Java', 'C++']
```

### 6.2. Método `join`

O método **`join`** une os elementos de uma lista (ou outro iterável) em uma única string, usando um delimitador especificado.

**Sintaxe:**
```py
delimitador.join(iterável)
```

- **`delimitador`**: A string usada para unir os elementos.
- **`iterável`**: A lista ou sequência de strings a ser unida.

**Exemplo:**
```py
lista_palavras = ['Python', 'é', 'incrível']
frase = ' '.join(lista_palavras)  # Une as palavras com espaço
print(frase)  # Saída: "Python é incrível"
```

**Exemplo com outro delimitador:**
```py
linguagens = ['Python', 'Java', 'C++']
frase = ', '.join(linguagens)  # Une as palavras com ', ' como delimitador
print(frase)  # Saída: "Python, Java, C++"
```

### 6.3. Método `strip`

O método **`strip`** remove espaços em branco (ou caracteres especificados) do início e do final de uma string.

**Sintaxe:**
```py
string.strip(chars=None)
```

- **`chars`**: Os caracteres a serem removidos (padrão é qualquer espaço em branco).

**Exemplo:**
```py
frase = "   Python é incrível   "
frase_limpa = frase.strip()  # Remove espaços em branco
print(frase_limpa)  # Saída: "Python é incrível"
```

**Exemplo com caracteres específicos:**
```py
frase = "###Python###"
frase_limpa = frase.strip('#')  # Remove os caracteres '#'
print(frase_limpa)  # Saída: "Python"
```

### 6.4. Exemplo Prático com `split`, `join` e `strip`

**Descrição:**
Divida uma string em partes, remova espaços em branco extras de cada parte e, em seguida, una as partes novamente.

**Exemplo:**
```py
frase = '   Olha só que   , coisa interessante          '
lista_frases_cruas = frase.split(',')  # Divide a string em partes usando ','

lista_frases = []
for i, frase in enumerate(lista_frases_cruas):
    lista_frases.append(lista_frases_cruas[i].strip())  # Remove espaços extras

frases_unidas = ', '.join(lista_frases)  # Une as partes novamente
print(frases_unidas)  # Saída: "Olha só que, coisa interessante"
```

**Explicação:**
1. **`split`**: Divide a string em uma lista de substrings com base no delimitador `,`.
2. **`strip`**: Remove os espaços em branco extras de cada substring.
3. **`join`**: Une as substrings limpas em uma única string, separadas por `, `.

---

## 7. Listas Dentro de Listas (Iteráveis Dentro de Iteráveis)

Em Python, é possível criar **listas dentro de listas**, formando estruturas aninhadas. Essas listas aninhadas são úteis para representar dados tabulares ou hierárquicos, como matrizes ou grupos de elementos.


### 7.1. Acessando Elementos em Listas de Listas

Para acessar elementos em listas aninhadas, usamos múltiplos índices:
- O **primeiro índice** refere-se à lista interna.
- O **segundo índice** refere-se ao elemento dentro dessa lista.

**Exemplo:**
```py
salas = [
    # 0        1
    ['Maria', 'Helena', ],  # 0
    # 0
    ['Elaine', ],  # 1
    # 0       1       2
    ['Luiz', 'João', 'Eduarda', ],  # 2
]

print(salas[0][1])  # Saída: Helena (índice 1 da lista 0)
print(salas[1][0])  # Saída: Elaine (índice 0 da lista 1)
print(salas[2][2])  # Saída: Eduarda (índice 2 da lista 2)
```

**Observação:**
- Tentar acessar um índice inexistente resultará em um erro `IndexError`.

### 7.2. Iterando Sobre Listas de Listas

Podemos usar laços `for` para iterar sobre listas aninhadas. O primeiro laço percorre as listas internas, enquanto o segundo laço percorre os elementos dentro de cada lista.

**Exemplo:**
```py
salas = [
    ['Maria', 'Helena', ],  # Sala 0
    ['Elaine', ],  # Sala 1
    ['Luiz', 'João', 'Eduarda', ],  # Sala 2
]

for sala in salas:
    print(f'A sala é {sala}')
    for aluno in sala:
        print(aluno)
```

**Saída:**
```
A sala é ['Maria', 'Helena']
Maria
Helena
A sala é ['Elaine']
Elaine
A sala é ['Luiz', 'João', 'Eduarda']
Luiz
João
Eduarda
```

**Explicação:**
1. O primeiro `for` percorre cada lista interna (representando uma sala).
2. O segundo `for` percorre os elementos dentro de cada lista (representando os alunos).

**Dica:**
- Listas aninhadas podem ser usadas para representar matrizes, tabelas ou grupos de dados relacionados.
- Certifique-se de verificar os índices para evitar erros ao acessar elementos.

---

## 8. Detalhes sobre o Interpretador do Python

O interpretador do Python é a ferramenta que executa o código Python. Ele oferece diversas opções para executar scripts, comandos e interagir com o ambiente de forma interativa.

---

### 8.1. Comandos Úteis do Interpretador

Aqui estão alguns comandos úteis para usar o interpretador do Python:

| Comando                          | Descrição                                                                 |
|----------------------------------|---------------------------------------------------------------------------|
| `python mod.py`                  | Executa o arquivo `mod.py`.                                               |
| `python -u`                      | Executa o Python no modo **unbuffered** (sem buffer).                     |
| `python -m mod`                  | Executa o módulo `mod` como um script.                                    |
| `python -c 'cmd'`                | Executa o comando Python especificado em `'cmd'`.                         |
| `python -i mod.py`               | Executa o arquivo `mod.py` e entra no modo interativo após a execução.    |

**Exemplos:**

1. **Executar um script Python:**
   ```bash
   python script.py
   ```

2. **Executar um comando diretamente no terminal:**
   ```bash
   python -c "print('Olá, Mundo!')"
   ```

3. **Executar um módulo como script:**
   ```bash
   python -m http.server
   ```

4. **Entrar no modo interativo após executar um script:**
   ```bash
   python -i script.py
   ```

---
