# Fundamentos 35

## Sumário

1. [Introdução às Generator Functions em Python](#1-introdução-às-generator-functions-em-python)
    - 1.1. [O Que São Generator Functions?](#11-o-que-são-generator-functions)
    - 1.2. [Como Criar uma Generator Function](#12-como-criar-uma-generator-function)
    - 1.3. [Exemplo Prático](#13-exemplo-prático)
    - 1.4. [Diferença entre Generator Functions e Generator Expressions](#14-diferença-entre-generator-functions-e-generator-expressions)
2. [Yield from em Generator Functions](#2-yield-from-em-generator-functions)
    - 2.1. [O Que é `yield from`?](#21-o-que-é-yield-from)
    - 2.2. [Como Usar `yield from`](#22-como-usar-yield-from)
    - 2.3. [Exemplo Prático](#23-exemplo-prático)
    - 2.4. [Vantagens do `yield from`](#24-vantagens-do-yield-from)
3. [Try e Except para Tratar Exceções](#3-try-e-except-para-tratar-exceções)
    - 3.1. [O Que é o Bloco `try` e `except`?](#31-o-que-é-o-bloco-try-e-except)
    - 3.2. [Tratando Exceções Específicas](#32-tratando-exceções-específicas)
    - 3.3. [Capturando Detalhes da Exceção](#33-capturando-detalhes-da-exceção)
    - 3.4. [Exemplo Prático](#34-exemplo-prático)
4. [Try, Except, Else e Finally](#4-try-except-else-e-finally)
    - 4.1. [O Que é o Bloco `try`, `except`, `else` e `finally`?](#41-o-que-é-o-bloco-try-except-else-e-finally)
    - 4.2. [Como Usar `else` e `finally`](#42-como-usar-else-e-finally)
    - 4.3. [Exemplo Prático](#43-exemplo-prático)
5. [Built-in Exceptions](#5-built-in-exceptions)
    - 5.1. [O Que São Built-in Exceptions?](#51-o-que-são-built-in-exceptions)
    - 5.2. [Exemplos de Built-in Exceptions](#52-exemplos-de-built-in-exceptions)
6. [Raise - Lançando Exceções (Erros)](#6-raise---lançando-exceções-erros)
    - 6.1. [O Que é o `raise`?](#61-o-que-é-o-raise)
    - 6.2. [Como Usar o `raise`](#62-como-usar-o-raise)
    - 6.3. [Exemplo Prático](#63-exemplo-prático)
    - 6.4. [Tratando Exceções Lançadas com `raise`](#64-tratando-exceções-lançadas-com-raise)

---

## 1. Introdução às Generator Functions em Python

As **Generator Functions** são uma forma poderosa de criar iteradores em Python. Elas permitem gerar valores sob demanda, economizando memória e tornando o processamento mais eficiente.

### 1.1. O Que São Generator Functions?

- São funções que utilizam a palavra-chave `yield` para produzir valores um de cada vez.
- Diferente de funções normais, elas não retornam um valor único com `return`. Em vez disso, pausam sua execução e retomam de onde pararam ao serem chamadas novamente.
- São úteis para trabalhar com grandes volumes de dados ou fluxos contínuos.

**Características:**
- Retornam um objeto generator.
- Geram valores sob demanda (lazy evaluation).
- Economizam memória, pois não armazenam todos os valores na memória.

### 1.2. Como Criar uma Generator Function

Para criar uma Generator Function:
1. Use a palavra-chave `yield` em vez de `return`.
2. A execução da função será pausada no `yield` e retomada na próxima chamada.

**Exemplo Simples:**
```py
def generator():
    yield 1
    yield 2
    yield 3

gen = generator()
print(next(gen))  # Saída: 1
print(next(gen))  # Saída: 2
print(next(gen))  # Saída: 3
```

### 1.3. Exemplo Prático

**Código Completo:**
```py
def generator(n=0, maximum=10):
    while True:
        yield n  # Pausa e retorna o valor atual de n
        n += 1

        if n >= maximum:  # Condição de parada
            return

gen = generator(maximum=1000000)
for n in gen:
    print(n)
```

**Explicação:**
1. A função `generator` começa com o valor inicial `n` e gera valores incrementados até atingir o valor `maximum`.
2. A palavra-chave `yield` retorna o valor atual de `n` e pausa a execução.
3. Quando `n` atinge o valor de `maximum`, a função termina com `return`.

**Saída (parcial):**
```
0
1
2
3
...
```

### 1.4. Diferença entre Generator Functions e Generator Expressions

| **Aspecto**               | **Generator Function**          | **Generator Expression**       |
|----------------------------|----------------------------------|---------------------------------|
| **Definição**              | Criada com `def` e `yield`.     | Criada com parênteses `()`.     |
| **Complexidade**           | Suporta lógica mais complexa.   | Melhor para casos simples.      |
| **Exemplo**                | `def gen(): yield n`            | `(n for n in range(10))`        |

**Exemplo Comparativo:**
```py
# Generator Function
def generator_function():
    for n in range(10):
        yield n

# Generator Expression
generator_expression = (n for n in range(10))

print(next(generator_function()))  # Saída: 0
print(next(generator_expression))  # Saída: 0
```

**Dicas:**
- Use Generator Functions para lógica mais complexa ou quando precisar de condições dinâmicas.
- Combine Generator Functions com `for` para processar grandes volumes de dados de forma eficiente.
- Lembre-se de que generators economizam memória, mas só podem ser iterados uma vez.

---

## 2. Yield from em Generator Functions

O **`yield from`** é uma construção em Python que simplifica o uso de generators aninhados. Ele delega a iteração de um generator para outro, permitindo que você reutilize lógica de geração de valores de forma mais limpa e eficiente.

### 2.1. O Que é `yield from`?

- O **`yield from`** é usado dentro de uma Generator Function para delegar a execução para outro generator ou iterável.
- Ele substitui o uso manual de loops para iterar sobre outro generator.

**Sem `yield from`:**
```py
def gen2(gen):
    for item in gen:
        yield item
```

**Com `yield from`:**
```py
def gen2(gen):
    yield from gen
```

### 2.2. Como Usar `yield from`

O **`yield from`** é usado para delegar a execução de um generator para outro. Isso é útil quando você deseja combinar ou reutilizar generators.

**Exemplo Simples:**
```py
def gen1():
    yield 1
    yield 2
    yield 3

def gen2():
    yield from gen1()  # Delegando para gen1
    yield 4
    yield 5

for numero in gen2():
    print(numero)
# Saída: 1, 2, 3, 4, 5
```

### 2.3. Exemplo Prático

**Código Completo:**
```py
def gen1():
    print('COMECOU GEN1')
    yield 1
    yield 2
    yield 3
    print('ACABOU GEN1')

def gen3():
    print('COMECOU GEN3')
    yield 10
    yield 20
    yield 30
    print('ACABOU GEN3')

def gen2(gen=None):
    print('COMECOU GEN2')
    if gen is not None:
        yield from gen  # Delegando para outro generator
    yield 4
    yield 5
    yield 6
    print('ACABOU GEN2')

g1 = gen2(gen1())
g2 = gen2(gen3())
g3 = gen2()

for numero in g1:
    print(numero)
print()
for numero in g2:
    print(numero)
print()
for numero in g3:
    print(numero)
print()
```

**Saída:**
```
COMECOU GEN2
COMECOU GEN1
1
2
3
ACABOU GEN1
4
5
6
ACABOU GEN2

COMECOU GEN2
COMECOU GEN3
10
20
30
ACABOU GEN3
4
5
6
ACABOU GEN2

COMECOU GEN2
4
5
6
ACABOU GEN2
```

**Explicação:**
1. A função `gen2` aceita um generator opcional como argumento.
2. Se um generator for passado, `yield from` delega a execução para ele.
3. Após o generator delegado terminar, `gen2` continua gerando seus próprios valores.

### 2.4. Vantagens do `yield from`

- **Simplicidade:** Reduz a necessidade de escrever loops manuais para iterar sobre outro generator.
- **Reutilização:** Permite combinar e reutilizar lógica de geração de valores.
- **Legibilidade:** Torna o código mais limpo e fácil de entender.

**Sem `yield from`:**
```py
def gen2(gen):
    for item in gen:
        yield item
    yield 4
    yield 5
```

**Com `yield from`:**
```py
def gen2(gen):
    yield from gen
    yield 4
    yield 5
```

**Dicas:**
- Use `yield from` para delegar a execução de um generator para outro de forma eficiente.
- Combine `yield from` com lógica condicional para criar generators dinâmicos e reutilizáveis.
- Lembre-se de que `yield from` também funciona com outros iteráveis, como listas e tuplas.

---

## 3. Try e Except para Tratar Exceções

O bloco **`try` e `except`** é usado em Python para tratar erros (exceções) que podem ocorrer durante a execução do programa. Ele permite que o programa continue executando mesmo após encontrar um erro.

### 3.1. O Que é o Bloco `try` e `except`?

- O bloco **`try`** contém o código que pode gerar uma exceção.
- O bloco **`except`** é executado se uma exceção for levantada no bloco `try`.

**Sintaxe Básica:**
```py
try:
    # Código que pode gerar uma exceção
except TipoDeExcecao:
    # Código para tratar a exceção
```

**Exemplo Simples:**
```py
try:
    a = 18
    b = 0
    c = a / b
except ZeroDivisionError:
    print('Erro: Divisão por zero.')
```

### 3.2. Tratando Exceções Específicas

Você pode tratar diferentes tipos de exceções usando múltiplos blocos `except`.

**Exemplo:**
```py
try:
    a = 18
    b = 0
    print('Linha 1'[1000])  # Gera IndexError
    c = a / b  # Gera ZeroDivisionError
except ZeroDivisionError:
    print('Erro: Divisão por zero.')
except IndexError:
    print('Erro: Índice fora do intervalo.')
except Exception:
    print('Erro desconhecido.')
```

**Saída:**
```
Erro: Índice fora do intervalo.
```

### 3.3. Capturando Detalhes da Exceção

Você pode capturar detalhes da exceção usando a palavra-chave `as`.

**Exemplo:**
```py
try:
    a = 18
    b = 0
    c = a / b
except ZeroDivisionError as e:
    print(e.__class__.__name__)  # Nome da exceção
    print(e)  # Mensagem de erro
```

**Saída:**
```
ZeroDivisionError
division by zero
```

**Capturando Múltiplas Exceções:**
```py
try:
    print('Linha 1'[1000])  # Gera IndexError
except (TypeError, IndexError) as error:
    print('Erro:', error)
    print('Tipo:', error.__class__.__name__)
```

**Saída:**
```
Erro: string index out of range
Tipo: IndexError
```

### 3.4. Exemplo Prático

**Código Completo:**
```py
# Parte 1
try:
    a = 18
    b = 0
    print('Linha 1'[1000])  # Gera IndexError
    c = a / b  # Gera ZeroDivisionError
    print('Linha 2')
except ZeroDivisionError:
    print('Dividiu por zero.')
except NameError:
    print('Nome b não está definido')
except (TypeError, IndexError):
    print('TypeError + IndexError')
except Exception:
    print('ERRO DESCONHECIDO.')

print('CONTINUAR')

# Parte 2
try:
    a = 18
    b = 0
    c = a / b  # Gera ZeroDivisionError
    print('Linha 2')
except ZeroDivisionError as e:
    print(e.__class__.__name__)
    print(e)
except NameError:
    print('Nome b não está definido')
except (TypeError, IndexError) as error:
    print('TypeError + IndexError')
    print('MSG:', error)
    print('Nome:', error.__class__.__name__)
except Exception:
    print('ERRO DESCONHECIDO.')

print('CONTINUAR')
```

**Saída (Parte 1):**
```
TypeError + IndexError
CONTINUAR
```

**Saída (Parte 2):**
```
ZeroDivisionError
division by zero
CONTINUAR
```

**Explicação:**
1. No **Parte 1**, o erro `IndexError` é tratado pelo bloco `except (TypeError, IndexError)`.
2. No **Parte 2**, o erro `ZeroDivisionError` é capturado e seus detalhes são exibidos.

**Dicas:**
- Sempre trate exceções específicas antes de usar um bloco genérico `except Exception`.
- Use `as` para capturar detalhes da exceção e melhorar o diagnóstico de erros.
- Evite capturar exceções genéricas sem necessidade, pois isso pode mascarar erros inesperados.

---

## 4. Try, Except, Else e Finally

O bloco **`try`, `except`, `else` e `finally`** é usado para tratar exceções em Python, garantindo que o código seja executado de forma segura e que recursos sejam liberados corretamente.

### 4.1. O Que é o Bloco `try`, `except`, `else` e `finally`?

- **`try`:** Contém o código que pode gerar uma exceção.
- **`except`:** Contém o código para tratar exceções específicas ou genéricas.
- **`else`:** Executado se **nenhuma exceção** for levantada no bloco `try`.
- **`finally`:** Sempre executado, independentemente de uma exceção ter sido levantada ou não. Geralmente usado para liberar recursos.

**Fluxo de Execução:**
1. O código no bloco `try` é executado.
2. Se uma exceção for levantada, o bloco `except` correspondente será executado.
3. Se nenhuma exceção for levantada, o bloco `else` será executado.
4. O bloco `finally` será executado em qualquer caso.

### 4.2. Como Usar `else` e `finally`

**Exemplo com `else` e `finally`:**
```py
try:
    print('ABRIR ARQUIVO')
    resultado = 8 / 2  # Nenhuma exceção aqui
except ZeroDivisionError as e:
    print(e.__class__.__name__)
    print('DIVIDIU ZERO')
else:
    print('Não deu erro')  # Executado porque não houve exceção
finally:
    print('FECHAR ARQUIVO')  # Sempre executado
```

**Saída:**
```
ABRIR ARQUIVO
Não deu erro
FECHAR ARQUIVO
```

### 4.3. Exemplo Prático

**Código Completo:**
```py
try:
    print('ABRIR ARQUIVO')
    resultado = 8 / 0  # Gera ZeroDivisionError
except ZeroDivisionError as e:
    print(e.__class__.__name__)
    print(e)
    print('DIVIDIU ZERO')
except IndexError as error:
    print('IndexError')
except (NameError, ImportError):
    print('NameError, ImportError')
else:
    print('Não deu erro')  # Não será executado porque houve exceção
finally:
    print('FECHAR ARQUIVO')  # Sempre executado
```

**Saída:**
```
ABRIR ARQUIVO
ZeroDivisionError
division by zero
DIVIDIU ZERO
FECHAR ARQUIVO
```

**Explicação:**
1. O bloco `try` tenta executar o código, mas ocorre uma exceção `ZeroDivisionError`.
2. O bloco `except ZeroDivisionError` trata a exceção.
3. O bloco `else` não é executado porque houve uma exceção.
4. O bloco `finally` é executado, garantindo que o recurso seja liberado.

**Dicas:**
- Sempre use `finally` para liberar recursos, como arquivos ou conexões de banco de dados.

---

## 5. Built-in Exceptions

### 5.1. O Que São Built-in Exceptions?

- As **Built-in Exceptions** são exceções pré-definidas em Python para tratar erros comuns.
- Elas estão documentadas na [documentação oficial](https://docs.python.org/pt-br/3/library/exceptions.html#built-in-exceptions).

---

### 2.2. Exemplos de Built-in Exceptions

| **Exceção**           | **Descrição**                                                                 |
|------------------------|-------------------------------------------------------------------------------|
| `ZeroDivisionError`    | Levantada quando ocorre uma divisão por zero.                                |
| `IndexError`           | Levantada quando um índice está fora do intervalo válido.                    |
| `NameError`            | Levantada quando uma variável ou nome não está definido.                     |
| `TypeError`            | Levantada quando uma operação é realizada em um tipo incompatível.           |
| `ValueError`           | Levantada quando um valor tem o tipo correto, mas é inválido.                |
| `KeyError`             | Levantada quando uma chave não é encontrada em um dicionário.                |
| `ImportError`          | Levantada quando um módulo ou objeto não pode ser importado.                 |
| `AttributeError`       | Levantada quando um atributo não é encontrado em um objeto.                  |
| `Exception`            | Classe base para todas as exceções.                                          |

**Exemplo com `IndexError`:**
```py
try:
    lista = [1, 2, 3]
    print(lista[10])  # Gera IndexError
except IndexError as e:
    print(e.__class__.__name__)
    print('Índice fora do intervalo.')
```

**Saída:**
```
IndexError
list index out of range
```

**Dicas:**
- Trate exceções específicas antes de usar um bloco genérico `except Exception`.
- Consulte a [documentação oficial](https://docs.python.org/pt-br/3/library/exceptions.html#built-in-exceptions) para conhecer todas as Built-in Exceptions disponíveis.

---

## 6. Raise - Lançando Exceções (Erros)

O **`raise`** é usado em Python para lançar exceções de forma explícita. Ele permite que você interrompa a execução do programa e informe que algo deu errado, fornecendo uma mensagem de erro personalizada.

### 6.1. O Que é o `raise`?

- O **`raise`** é uma instrução que permite lançar uma exceção manualmente.
- Pode ser usado para validar condições e interromper a execução quando algo inesperado ocorre.
- É possível lançar exceções personalizadas ou built-in exceptions.

**Sintaxe:**
```py
raise TipoDeExcecao('Mensagem de erro')
```

**Exemplo Simples:**
```py
def verifica_positivo(numero):
    if numero < 0:
        raise ValueError('O número deve ser positivo.')
    return numero

print(verifica_positivo(-1))  # Gera ValueError
```

### 6.2. Como Usar o `raise`

O **`raise`** é frequentemente usado em funções para validar entradas ou condições.

**Exemplo:**
```py
def nao_aceito_zero(d):
    if d == 0:
        raise ZeroDivisionError('Você está tentando dividir por zero')
    return True
```

**Explicação:**
- Se o valor de `d` for `0`, a exceção `ZeroDivisionError` será lançada com a mensagem personalizada.

### 6.3. Exemplo Prático

**Código Completo:**
```py
def nao_aceito_zero(d):
    if d == 0:
        raise ZeroDivisionError('Você está tentando dividir por zero')
    return True

def deve_ser_int_ou_float(n):
    tipo_n = type(n)
    if not isinstance(n, (float, int)):
        raise TypeError(
            f'"{n}" deve ser int ou float. '
            f'"{tipo_n.__name__}" enviado.'
        )
    return True

def divide(n, d):
    deve_ser_int_ou_float(n)
    deve_ser_int_ou_float(d)
    nao_aceito_zero(d)
    return n / d

print(divide(8, '0'))  # Gera TypeError
```

**Saída:**
```
Traceback (most recent call last):
  ...
TypeError: "0" deve ser int ou float. "str" enviado.
```

**Explicação:**
1. A função `divide` valida os argumentos `n` e `d` usando as funções auxiliares.
2. A função `deve_ser_int_ou_float` verifica se os valores são do tipo `int` ou `float`. Caso contrário, lança um `TypeError`.
3. A função `nao_aceito_zero` verifica se o divisor é zero. Caso seja, lança um `ZeroDivisionError`.

### 6.4. Tratando Exceções Lançadas com `raise`

Você pode usar `try` e `except` para tratar exceções lançadas com `raise`.

**Exemplo:**
```py
try:
    print(divide(8, 0))  # Gera ZeroDivisionError
except ZeroDivisionError as e:
    print(e.__class__.__name__)
    print(e)
except TypeError as e:
    print(e.__class__.__name__)
    print(e)
```

**Saída:**
```
ZeroDivisionError
Você está tentando dividir por zero
```

**Dicas:**
- Use `raise` para validar entradas e garantir que sua função seja usada corretamente.
- Combine `raise` com mensagens de erro claras para facilitar o diagnóstico de problemas.
- Consulte a [documentação oficial](https://docs.python.org/pt-br/3/library/exceptions.html#built-in-exceptions) para conhecer as exceções disponíveis.

---