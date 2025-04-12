# Fundamentos 2

## Sumário

1. [Blocos de Código e Condicionais (`if`, `elif`, `else`)](#blocos-de-código-e-condicionais-if-elif-else)
    - 1.1. [Estrutura Básica](#estrutura-básica)
    - 1.2. [Múltiplas Condições com `if`, `elif` e `else`](#múltiplas-condições-com-if-elif-e-else)
2. [Operadores de Comparação (Relacionais)](#operadores-de-comparação-relacionais)
3. [Operadores Logicos](#operadores-lógicos)
    - 3.1. [Operador `and` (E)](#operador-and-e)
    - 3.2. [Operador `or` (Ou)](#operador-or-ou)
    - 3.3. [Operador `not` (Não)](#operador-not-não)
4. [Operadores de Associação `in` e `not in`](#operadores-de-associação-in-e-not-in)
    - 4.1. [Valores "False" em Python](#valores-false-em-python)
5. [Interpolação de Strings com `%`](#interpolação-de-strings-com-)
6. [Fatiamento de Strings](#fatiamento-de-strings)
    - 6.1. [Índices em Strings](#índices-em-strings)
    - 6.2. [Sintaxe do Fatiamento](#sintaxe-do-fatiamento)
7. [Função `len`](#função-len)

--

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