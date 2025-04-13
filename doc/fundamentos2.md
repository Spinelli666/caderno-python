# Fundamentos 2

## Sumário

1. [Blocos de Código e Condicionais (`if`, `elif`, `else`)](#1-blocos-de-código-e-condicionais-if-elif-else)
    - 1.1. [Estrutura Básica](#11-estrutura-básica)
    - 1.2. [Múltiplas Condições com `if`, `elif` e `else`](#12-múltiplas-condições-com-if-elif-e-else)
2. [Operadores de Comparação (Relacionais)](#2-operadores-de-comparação-relacionais)
3. [Operadores Lógicos](#3-operadores-lógicos)
    - 3.1. [Operador `and` (E)](#31-operador-and-e)
    - 3.2. [Operador `or` (Ou)](#32-operador-or-ou)
    - 3.3. [Operador `not` (Não)](#33-operador-not-não)
4. [Operadores de Associação (`in` e `not in`)](#4-operadores-de-associação-in-e-not-in)
    - 4.1. [Valores "False" em Python](#41-valores-false-em-python)
5. [Interpolação de Strings com `%`](#5-interpolação-de-strings-com-)
6. [Fatiamento de Strings](#6-fatiamento-de-strings)
    - 6.1. [Índices em Strings](#61-índices-em-strings)
    - 6.2. [Sintaxe do Fatiamento](#62-sintaxe-do-fatiamento)
7. [Função `len`](#7-função-len)
8. [Bloco `try` e `except`](#8-bloco-try-e-except)
    - 8.1. [Estrutura Básica](#81-estrutura-básica)
    - 8.2. [Comparação com `isdigit()`](#82-comparação-com-isdigit)
    - 8.3. [Boas Práticas com `try` e `except`](#83-boas-práticas-com-try-e-except)
9. [Variáveis, Constantes e Complexidade de Código](#9-variáveis-constantes-e-complexidade-de-código)
    - 9.1. [Constantes](#91-constantes)
    - 9.2. [Complexidade de Código](#92-complexidade-de-código)
10. [Flag, `is`, `is not` e `None`](#10-flag-is-is-not-e-none)
    - 10.1. [Flag (Bandeira)](#101-flag-bandeira)
    - 10.2. [`None`](#102-none)
    - 10.3. [`is` e `is not`](#103-is-e-is-not)
11. [`id` (Identidade do Objeto)](#11-estrutura-básica)

---

### 1. Blocos de Código e Condicionais (`if`, `elif`, `else`)

Em Python, os **blocos de código** são definidos pela **indentação** (espaços ou tabulação no início da linha). Eles são usados para agrupar instruções que devem ser executadas juntas, como em estruturas condicionais.

As estruturas condicionais permitem que o programa tome decisões com base em condições específicas. Em Python, usamos as palavras-chave `if`, `elif` e `else` para criar essas condições.

#### 1.1. Estrutura Básica

- **`if`**: Executa um bloco de código se a condição for verdadeira.
- **`elif`**: (abreviação de "else if") Verifica outra condição se a anterior for falsa.
- **`else`**: Executa um bloco de código se nenhuma das condições anteriores for verdadeira.

**Exemplo:**
```py
entrada = input('Você quer "entrar" ou "sair"? ')

if entrada == 'entrar':
    print('Você entrou no sistema')
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

#### 1.2. Múltiplas Condições com `if`, `elif` e `else`

Você pode usar várias condições para controlar o fluxo do programa.

**Exemplo:**
```py
condicao1 = True
condicao2 = True
condicao3 = True
condicao4 = True

if condicao1:
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

### 2. Operadores de Comparação (Relacionais)

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
maior = 2 > 1
menor = 1 < 2
igual = 'a' == 'a'
diferente = 'a' != 'b'

print('Maior:', maior)  # True
print('Menor:', menor)  # True
print('Igual:', igual)  # True
print('Diferente:', diferente)  # True
```

*Observações:*
- Os operadores de comparação são frequentemente usados em estruturas condicionais, como `if`, para tomar decisões com base em condições.
- Comparações podem ser feitas entre números, strings e outros tipos de dados, desde que sejam compatíveis.

---

### 3. Operadores Lógicos

Os **operadores lógicos** são usados para combinar expressões condicionais e tomar decisões com base em múltiplas condições.

| Operador | Significado | Descrição                                                                 |
|----------|-------------|---------------------------------------------------------------------------|
| `and`    | E           | Todas as condições precisam ser verdadeiras para o resultado ser `True`. |
| `or`     | Ou          | Pelo menos uma condição precisa ser verdadeira para o resultado ser `True`. |
| `not`    | Não         | Inverte o valor lógico de uma expressão (`True` vira `False` e vice-versa). |

#### 3.1. Operador `and` (E)

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

#### 3.2. Operador `or` (Ou)

O operador `or` avalia como `True` se **pelo menos uma condição** for verdadeira. Se todas as condições forem falsas, o resultado será `False`.

**Exemplo:**
```py
entrada = input('[E]ntrar [S]air: ')
senha_digitada = input('Senha: ')

if entrada == 'E' or entrada == 'e':
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

#### 3.3. Operador `not` (Não)

O operador `not` é usado para inverter o valor lógico de uma expressão. Se a expressão for `True`, o resultado será `False`, e vice-versa.

**Exemplo:**
```py
ativo = False
if not ativo:
    print('A conta está inativa.')
```

---

### 4. Operadores de Associação (`in` e `not in`)

Os operadores `in` e `not in` verificam se um valor está (ou não está) presente em uma sequência, como strings, listas ou tuplas.

| Operador   | Significado                  | Exemplo (`True`)         |
|------------|------------------------------|--------------------------|
| `in`       | Está presente na sequência   | `'a' in 'Python'`        |
| `not in`   | Não está presente na sequência | `'z' not in 'Python'`    |

**Exemplo 1:**
```py
nome = input('Digite seu nome: ')
encontrar = input('Digite o que deseja encontrar: ')

if encontrar in nome:
    print(f'{encontrar} está em {nome}')
else:
    print(f'{encontrar} não está em {nome}')
```

**Exemplo 2:**
```py
nome = 'Python'
print('P' in nome)       # True
print('z' not in nome)   # True
```

#### 4.1. Valores "False" em Python

Os seguintes valores são considerados **falsos** em Python:
- `0`
- `0.0`
- `''` (string vazia)
- `False`
- `None`

**Exemplo:**
```py
if not 0:
    print('0 é considerado falso')  # Será exibido
```

---

### 5. Interpolação de Strings com `%`

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

### 6. Fatiamento de Strings

O **fatiamento de strings** permite acessar partes específicas de uma string, utilizando a notação `[início:fim:passo]`. Essa técnica é muito útil para manipular textos em Python.

#### 6.1. Índices em Strings

Cada caractere de uma string possui um índice, que pode ser positivo (da esquerda para a direita) ou negativo (da direita para a esquerda).

**Exemplo:**
```py
variavel = 'Python'
print(variavel[0])  # P
print(variavel[-1]) # n
```

#### 6.2. Sintaxe do Fatiamento

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

### 7. Função `len`

A função **`len`** retorna a quantidade de caracteres de uma string (incluindo espaços).

**Exemplo:**
```py
variavel = 'Olá mundo'
print(len(variavel))  # Saída: 9 (conta todos os caracteres, incluindo o espaço)
```

---

### 8. Bloco `try` e `except`

O bloco `try` e `except` é usado em Python para capturar e tratar **erros (exceptions)** que podem ocorrer durante a execução do código. Ele permite que o programa continue rodando mesmo que um erro seja encontrado.

#### 8.1. Estrutura Básica

- **`try`**: Tenta executar o código dentro do bloco.
- **`except`**: Captura e trata o erro caso ele ocorra.

**Exemplo**

```py
numero_str = input('Vou dobrar o número que você digitar: ')

try:
    numero_float = float(numero_str)  # Tenta converter a entrada para float
    print(f'O dobro de {numero_str} é {numero_float * 2:.2f}')
except:
    print('Isso não é um número')  # Executado se ocorrer um erro
```

**Explicação:**
1. O programa tenta converter a entrada do usuário para um número (`float`).
2. Se a conversão falhar (por exemplo, se o usuário digitar letras), o bloco `except` será executado.
3. Caso contrário, o programa calcula e exibe o dobro do número.

#### 8.2. Comparação com `isdigit()`

Outra forma de verificar se a entrada é um número é usando o método `.isdigit()`. No entanto, ele só funciona para números inteiros e não considera números com ponto decimal ou negativos.

**Exemplo com `isdigit()`**

```py
numero_str = input('Vou dobrar o número que você digitar: ')

if numero_str.isdigit():
    numero_float = float(numero_str)
    print(f'O dobro de {numero_str} é {numero_float * 2:.2f}')
else:
    print('Isso não é um número')
```

**Limitações do `.isdigit()`:**
- Não aceita números com ponto decimal (`3.14`) ou negativos (`-5`).
- Para esses casos, o uso de `try` e `except` é mais robusto.

---

#### 8.3. Boas Práticas com `try` e `except`

1. **Especifique o tipo de erro no `except`:**
   - É uma boa prática capturar apenas os erros esperados, como `ValueError` para conversões inválidas.
   - Isso evita capturar erros inesperados que podem mascarar problemas no código.

   **Exemplo:**
   ```py
   try:
       numero_float = float(numero_str)
       print(f'O dobro de {numero_str} é {numero_float * 2:.2f}')
   except ValueError:
       print('Isso não é um número')
   ```

2. **Evite blocos `except` genéricos:**
   - Usar apenas `except:` captura qualquer erro, o que pode dificultar a depuração.

3. **Use mensagens claras para o usuário:**
   - Informe o motivo do erro de forma compreensível.

---

### 9. Variáveis, Constantes e Complexidade de Código

#### 9.1. Constantes

Em Python, **constantes** são valores que não devem ser alterados durante a execução do programa. Embora Python não tenha suporte nativo para constantes, por convenção, utilizamos **nomes em letras maiúsculas** para indicar que uma variável deve ser tratada como constante.

**Exemplo:**
```py
CONSTANTE = "Este valor não deve mudar"
```

---

#### 9.2. Complexidade de Código

Evitar **muitas condições no mesmo `if`** é uma boa prática, pois isso pode tornar o código difícil de entender e manter. Um código com muitas condições em um único bloco é considerado de **alta complexidade**.

**Exemplo de alta complexidade (ruim):**
```py
if condicao1 and condicao2 and condicao3 and condicao4:
    print("Condição complexa")
```

**Dica:**
- Divida as condições em partes menores e mais legíveis.
- Use variáveis intermediárias para descrever cada condição.

---

**Exemplo Prático: Controle de Velocidade com Radar**

O exemplo abaixo demonstra o uso de variáveis, constantes e boas práticas para reduzir a complexidade do código.

```py
# Constantes
RADAR_1 = 60  # Velocidade máxima do radar 1
LOCAL_1 = 100  # Local onde o radar 1 está
RADAR_RANGE = 1  # A distância onde o radar detecta

# Variáveis
velocidade = 61  # Velocidade atual do carro
local_carro = 100  # Local em que o carro está na estrada

# Verificações
vel_carro_pass_radar_1 = velocidade > RADAR_1
carro_passou_radar_1 = LOCAL_1 - RADAR_RANGE <= local_carro <= LOCAL_1 + RADAR_RANGE
carro_multado_radar_1 = vel_carro_pass_radar_1 and carro_passou_radar_1

# Resultados
if vel_carro_pass_radar_1:
    print('Velocidade do carro passou do radar 1')

if carro_passou_radar_1:
    print('Carro passou pelo radar 1')

if carro_multado_radar_1:
    print('Carro multado no radar 1')
```

**Explicação:**
1. **Constantes**:
   - `RADAR_1`, `LOCAL_1` e `RADAR_RANGE` são definidos como constantes para facilitar a leitura e manutenção do código.
2. **Variáveis intermediárias**:
   - `vel_carro_pass_radar_1`: Verifica se a velocidade do carro excede o limite do radar.
   - `carro_passou_radar_1`: Verifica se o carro está dentro do alcance do radar.
   - `carro_multado_radar_1`: Combina as duas condições anteriores para determinar se o carro será multado.
3. **Blocos `if` separados**:
   - Cada condição é avaliada e tratada separadamente, tornando o código mais legível e fácil de entender.

---

### 10. Flag, `is`, `is not` e `None`

#### 10.1. Flag (Bandeira)

Uma **flag** é uma variável usada para marcar ou indicar um estado ou condição no programa. Geralmente, é usada para controlar o fluxo do código ou sinalizar se algo aconteceu.

**Exemplo:**
```py
condicao = False
passou_no_if = None  # Flag inicializada como None

if condicao:
    passou_no_if = True  # Marca que a condição foi atendida
    print('Faça algo')
else:
    print('Não faça algo')

if passou_no_if is None:  # Verifica se a flag ainda está como None
    print('Não passou no if')
else:
    print('Passou no if')
```

#### 10.2. `None`

O valor **`None`** em Python representa a ausência de valor ou um valor nulo. Ele é frequentemente usado para inicializar variáveis que ainda não possuem um valor definido.

**Exemplo:**
```py
variavel = None  # Inicializa a variável sem valor
if variavel is None:
    print('A variável não tem valor')
```

**Observações:**
- `None` é um objeto especial em Python e não é equivalente a `False`, `0` ou uma string vazia (`''`).
- Ele é frequentemente usado como valor padrão em funções ou para sinalizar que algo ainda não foi definido.

#### 10.3. `is` e `is not`

Os operadores **`is`** e **`is not`** são usados para comparar **identidade de objetos** (se dois objetos são exatamente o mesmo na memória).

**Diferença entre `is` e `==`:**
- **`is`**: Verifica se dois objetos têm a mesma identidade (ocupam o mesmo espaço na memória).
- **`==`**: Verifica se dois objetos têm o mesmo valor.

**Exemplo:**
```py
a = [1, 2, 3]
b = [1, 2, 3]
c = a

print(a is b)  # False (a e b têm valores iguais, mas são objetos diferentes)
print(a == b)  # True (os valores de a e b são iguais)
print(a is c)  # True (a e c são o mesmo objeto na memória)
```

---

### 11. `id` (Identidade do Objeto)

A função **`id`** retorna o identificador único de um objeto na memória. Esse identificador é usado internamente pelo Python para distinguir objetos.

**Exemplo:**
```py
a = [1, 2, 3]
b = a

print(id(a))  # Exibe o ID do objeto a
print(id(b))  # Exibe o mesmo ID, pois a e b são o mesmo objeto
```

**Observação:**
- Se dois objetos têm o mesmo `id`, eles são o mesmo objeto na memória.

---