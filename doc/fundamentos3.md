# Fundamentos 3

## Sumário

---

# Estruturas de Repetição: `while` e `break`

## Repetições com `while`

O comando **`while`** é usado para executar um bloco de código repetidamente enquanto uma condição for verdadeira. Ele é útil para criar **laços de repetição** quando não sabemos previamente o número exato de iterações.

### Estrutura Básica

```py
while condição:
    # Código a ser executado enquanto a condição for verdadeira
```

- **`while`**: Significa "enquanto". O bloco será executado enquanto a condição for avaliada como `True`.
- **Loop infinito**: Ocorre quando a condição nunca se torna `False`, fazendo o código rodar indefinidamente.

---

## Exemplo 1: Loop Simples com `while`

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

---

## Exemplo 2: Contador Simples

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

---

## Exemplo 3: Usando `continue` e `break`

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

---

## Exemplo 4: Laços Aninhados com `while`

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

---

## Boas Práticas com `while`

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


# Operadores de Atribuição com Operadores Aritméticos

Os **operadores de atribuição** são usados para atribuir valores a variáveis. Em Python, podemos combinar operadores aritméticos com o operador de atribuição (`=`) para simplificar operações matemáticas.

---

## Operadores de Atribuição

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

---

## Exemplos Práticos

### Exemplo 1: Operadores de Atribuição Básicos

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

---

### Exemplo 2: Operadores de Atribuição Avançados

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

# Estruturas de Repetição: `for` e `range`

## Introdução ao `for` e Iteração em Python

O comando **`for`** é usado para iterar sobre elementos de um **iterável** (como strings, listas, tuplas, dicionários, ou objetos do tipo `range`). Ele é ideal para situações em que sabemos previamente o número de iterações ou queremos percorrer elementos de uma sequência finita.

### Estrutura Básica do `for`

```py
for elemento in iterável:
    # Código a ser executado para cada elemento
```

- **`elemento`**: Representa o item atual da sequência que está sendo iterado.
- **`iterável`**: É o objeto que contém os elementos a serem percorridos (como uma string, lista, ou `range`).

---

## Exemplo 1: Iteração Simples com Strings

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

---

## `for` com `range`

A função **`range`** é usada para gerar uma sequência de números. Ela é frequentemente combinada com o `for` para criar laços de repetição baseados em intervalos numéricos.

### Estrutura do `range`

```py
range(start, stop, step)
```

- **`start`**: (Opcional) O número inicial da sequência (padrão é `0`).
- **`stop`**: O número final da sequência (não incluído).
- **`step`**: (Opcional) O intervalo entre os números (padrão é `1`).

### Exemplo 2: Iteração com `range`

```py
numeros = range(0, 100, 8)

for numero in numeros:
    print(numero)
```

**Explicação:**
1. O `range(0, 100, 8)` gera números de `0` a `99`, com um passo de `8`.
2. O `for` percorre cada número gerado pelo `range` e executa o código dentro do bloco.

---

## Como o `for` Funciona por Baixo dos Panos?

Em Python, o `for` funciona com base no conceito de **iteráveis** e **iteradores**.

### Conceitos Importantes

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

---

### Exemplo 3: Iteração Manual com `iter` e `next`

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

---

### Exemplo 4: Comparação entre `for` e Iteração Manual

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

---

## Boas Práticas com `for`

1. **Use `for` para Iterações Finitas**:
   - O `for` é ideal para percorrer sequências finitas, como listas, strings ou intervalos gerados por `range`.

2. **Evite Modificar o Iterável Durante a Iteração**:
   - Alterar o iterável enquanto ele está sendo percorrido pode causar comportamentos inesperados.

3. **Combine `for` com Funções como `enumerate` e `zip`**:
   - Use `enumerate` para obter o índice e o valor de cada elemento.
   - Use `zip` para iterar sobre múltiplas sequências simultaneamente.

---

## Exemplo 5: Uso de `enumerate`

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

---

## Exemplo 6: Uso de `zip`

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