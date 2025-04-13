# Fundamentos 2

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

## Boas Práticas

1. **Use operadores de atribuição para simplificar o código**:
   - Em vez de escrever `x = x + 5`, use `x += 5`.
   - Isso torna o código mais limpo e fácil de entender.

2. **Cuidado com o tipo de dado**:
   - Operações como `/=` podem alterar o tipo da variável para `float`, mesmo que ela seja `int` inicialmente.
   - Exemplo:
     ```py
     x = 10
     x /= 2
     print(type(x))  # Saída: <class 'float'>
     ```

3. **Evite usar operadores de atribuição em expressões muito complexas**:
   - Mantenha o código legível e fácil de entender.

---