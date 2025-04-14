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