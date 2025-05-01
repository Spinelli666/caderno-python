# Fundamentos 46

## Sumário

1. [Variáveis Livres e `nonlocal` (locals, globals)](#1-variáveis-livres-e-nonlocal-locals-globals)
    - 1.1. [O Que São Variáveis Livres?](#11-o-que-são-variáveis-livres)
    - 1.2. [O Que é `nonlocal`?](#12-o-que-é-nonlocal)
    - 1.3. [Funções `globals()` e `locals()`](#13-funções-globals-e-locals)
    - 1.4. [Exemplo Prático com `nonlocal`](#14-exemplo-prático-com-nonlocal)
    - 1.5. [Exemplo Prático com Variáveis Livres](#15-exemplo-prático-com-variáveis-livres)
2. [Funções Decoradoras e Decoradores](#2-funções-decoradoras-e-decoradores)
    - 2.1. [O Que São Funções Decoradoras?](#21-o-que-são-funções-decoradoras)
    - 2.2. [O Que São Decoradores?](#22-o-que-são-decoradores)
    - 2.3. [Como Criar uma Função Decoradora](#23-como-criar-uma-função-decoradora)
    - 2.4. [Usando Decoradores com `@` (Syntax Sugar)](#24-usando-decoradores-com--syntax-sugar)
    - 2.5. [Exemplo Prático](#25-exemplo-prático)
3. [Decoradores com Parâmetros](#3-decoradores-com-parâmetros)
    - 3.1. [O Que São Decoradores com Parâmetros?](#31-o-que-são-decoradores-com-parâmetros)
    - 3.2. [Como Criar Decoradores com Parâmetros](#32-como-criar-decoradores-com-parâmetros)
    - 3.3. [Exemplo Prático](#33-exemplo-prático)
    - 3.4. [Vantagens dos Decoradores com Parâmetros](#34-vantagens-dos-decoradores-com-parâmetros)
4. [Ordem de Aplicação dos Decoradores](#4-ordem-de-aplicação-dos-decoradores)
    - 4.1. [O Que São Decoradores Empilhados?](#41-o-que-são-decoradores-empilhados)
    - 4.2. [Como Funciona a Ordem de Aplicação?](#42-como-funciona-a-ordem-de-aplicação)
    - 4.3. [Exemplo Prático](#43-exemplo-prático)
    - 4.4. [Dicas para Trabalhar com Decoradores Empilhados](#44-dicas-para-trabalhar-com-decoradores-empilhados)

---

## 1. Variáveis Livres e `nonlocal` (locals, globals)

Em Python, **variáveis livres** e a palavra-chave **`nonlocal`** são conceitos importantes para entender como variáveis são acessadas e manipuladas em funções aninhadas.

### 1.1. O Que São Variáveis Livres?

- **Variáveis livres** são variáveis que não estão definidas no escopo local de uma função, mas são usadas dentro dela.
- Elas são capturadas do escopo externo (função pai) e armazenadas como parte do estado da função interna.

**Exemplo:**
```py
def fora(x):
    a = x  # Variável livre

    def dentro():
        return a  # Usa a variável livre
    return dentro

dentro1 = fora(10)
dentro2 = fora(20)

print(dentro1())  # Saída: 10
print(dentro2())  # Saída: 20
```

**Explicação:**
- A variável `a` é uma variável livre para a função `dentro`, pois está definida no escopo da função `fora`.

### 1.2. O Que é `nonlocal`?

- A palavra-chave **`nonlocal`** é usada para modificar variáveis no escopo externo (mas não no escopo global).
- Permite alterar o valor de uma variável livre dentro de uma função aninhada.

**Exemplo:**
```py
def contador():
    numero = 0

    def incrementar():
        nonlocal numero
        numero += 1
        return numero
    return incrementar

c = contador()
print(c())  # Saída: 1
print(c())  # Saída: 2
print(c())  # Saída: 3
```

**Explicação:**
- A variável `numero` é capturada como uma variável livre pela função `incrementar`.
- O uso de `nonlocal` permite modificar o valor de `numero` no escopo externo.

### 1.3. Funções `globals()` e `locals()`

- **`globals()`**: Retorna um dicionário com todas as variáveis globais disponíveis no momento.
- **`locals()`**: Retorna um dicionário com todas as variáveis locais disponíveis no escopo atual.

**Exemplo com `globals()`:**
```py
x = 10
print(globals())  # Mostra todas as variáveis globais
```

**Exemplo com `locals()`:**
```py
def exemplo():
    a = 5
    b = 10
    print(locals())  # Mostra todas as variáveis locais

exemplo()
```

### 1.4. Exemplo Prático com `nonlocal`

**Código Completo:**
```py
def concatenar(string_inicial):
    valor_final = string_inicial

    def interna(valor_a_concatenar=''):
        nonlocal valor_final
        valor_final += valor_a_concatenar
        return valor_final
    return interna

c = concatenar('a')
print(c('b'))  # Saída: ab
print(c('c'))  # Saída: abc
print(c('d'))  # Saída: abcd
final = c()
print(final)  # Saída: abcd
```

**Explicação:**
- A variável `valor_final` é capturada como uma variável livre pela função `interna`.
- O uso de `nonlocal` permite modificar o valor de `valor_final` no escopo externo.

### 1.5. Exemplo Prático com Variáveis Livres

**Código Completo:**
```py
def fora(x):
    a = x

    def dentro():
        print(locals())  # Mostra as variáveis locais
        print(dentro.__code__.co_freevars)  # Mostra as variáveis livres
        return a
    return dentro

dentro1 = fora(10)
dentro2 = fora(20)

print(dentro1())  # Saída: 10
print(dentro2())  # Saída: 20
```

**Saída:**
```
{'a': 10}
('a',)
10
{'a': 20}
('a',)
20
```

**Explicação:**
- A função `dentro` captura a variável livre `a` do escopo da função `fora`.
- O atributo `__code__.co_freevars` mostra as variáveis livres capturadas pela função.

**Dicas:**
- Use `nonlocal` para modificar variáveis no escopo externo imediato.
- Use `globals()` e `locals()` para depurar e inspecionar variáveis em diferentes escopos.
- Evite abusar de variáveis livres e `nonlocal` para manter o código legível e fácil de entender.

---

## 2. Funções Decoradoras e Decoradores

As **funções decoradoras** e os **decoradores** são ferramentas poderosas em Python que permitem modificar ou estender o comportamento de outras funções de forma reutilizável e elegante.

### 2.1. O Que São Funções Decoradoras?

- **Funções decoradoras** são funções que recebem outra função como argumento, adicionam ou alteram seu comportamento e retornam uma nova função.
- Elas são usadas para "decorar" ou modificar o comportamento de outras funções.

### 2.2. O Que São Decoradores?

- **Decoradores** são uma forma simplificada de aplicar funções decoradoras usando o símbolo `@`.
- Eles são considerados **"Syntax Sugar"** (açúcar sintático), pois tornam o código mais legível e organizado.

### 2.3. Como Criar uma Função Decoradora

Uma função decoradora geralmente segue este padrão:
1. Recebe uma função como argumento.
2. Define uma função interna que adiciona/modifica o comportamento.
3. Retorna a função interna.

**Exemplo:**
```py
def criar_funcao(func):
    def interna(*args, **kwargs):
        print('Vou te decorar')
        resultado = func(*args, **kwargs)
        print(f'O resultado é {resultado}')
        print('Ok, agora você foi decorada')
        return resultado
    return interna
```

### 2.4. Usando Decoradores com `@` (Syntax Sugar)

O símbolo `@` permite aplicar uma função decoradora diretamente sobre outra função.

**Exemplo:**
```py
@criar_funcao
def inverte_string(string):
    return string[::-1]
```

Isso é equivalente a:
```py
def inverte_string(string):
    return string[::-1]

inverte_string = criar_funcao(inverte_string)
```

### 2.5. Exemplo Prático

**Código Completo:**

**Sem `@` (Aplicação Manual):**
```py
def criar_funcao(func):
    def interna(*args, **kwargs):
        print('Vou te decorar')
        for arg in args:
            e_string(arg)

        resultado = func(*args, **kwargs)
        print(f'O resultado é {resultado}')
        print('Ok, agora você foi decorada')
        return resultado
    return interna

def inverte_string(string):
    return string[::-1]

def e_string(param):
    if not isinstance(param, str):
        raise TypeError('O parâmetro deve ser uma string')
    return True

inverte_string_checando_parametro = criar_funcao(inverte_string)
invertida = inverte_string_checando_parametro('123')
print(invertida)
```

**Saída:**
```
Vou te decorar
O resultado é 321
Ok, agora você foi decorada
321
```

**Com `@` (Syntax Sugar):**
```py
def criar_funcao(func):
    def interna(*args, **kwargs):
        print('Vou te decorar')
        for arg in args:
            e_string(arg)

        resultado = func(*args, **kwargs)
        print(f'O resultado é {resultado}')
        print('Ok, agora você foi decorada')
        return resultado
    return interna

@criar_funcao
def inverte_string(string):
    print(f'{inverte_string.__name__} foi chamada')
    return string[::-1]

def e_string(param):
    if not isinstance(param, str):
        raise TypeError('O parâmetro deve ser uma string')
    return True

invertida = inverte_string('123')
print(invertida)
```

**Saída:**
```
Vou te decorar
inverte_string foi chamada
O resultado é 321
Ok, agora você foi decorada
321
```

**Dicas:**
- Use decoradores para adicionar funcionalidades reutilizáveis, como validações, logs ou autenticação.
- Combine decoradores com `@` para tornar o código mais legível e organizado.
- Sempre documente o comportamento dos decoradores para facilitar a manutenção do código.

---

## 3. Decoradores com Parâmetros

Os **decoradores com parâmetros** permitem que você passe argumentos para a função decoradora, tornando-a mais flexível e reutilizável.

### 3.1. O Que São Decoradores com Parâmetros?

- São decoradores que aceitam argumentos além da função que decoram.
- Eles são úteis para personalizar o comportamento do decorador com base nos parâmetros fornecidos.

### 3.2. Como Criar Decoradores com Parâmetros

Para criar um decorador com parâmetros:
1. Crie uma função externa que receba os parâmetros do decorador.
2. Dentro dessa função, crie a função decoradora.
3. Dentro da função decoradora, crie a função aninhada que será aplicada à função decorada.

**Estrutura Básica:**
```py
def decorador_com_parametros(param1, param2):
    def decorador(func):
        def aninhada(*args, **kwargs):
            # Use os parâmetros do decorador
            print(f'Parâmetros do decorador: {param1}, {param2}')
            resultado = func(*args, **kwargs)
            return resultado
        return aninhada
    return decorador
```

### 3.3. Exemplo Prático

**Código Completo:**
```py
def fabrica_de_decoradores(a=None, b=None, c=None):
    def fabrica_de_funcoes(func):
        print('Decoradora 1')
        def aninhada(*args, **kwargs):
            print('Parâmetros do decorador:', a, b, c)
            print('Aninhada')
            res = func(*args, **kwargs)
            return res
        return aninhada
    return fabrica_de_funcoes

@fabrica_de_decoradores(1, 2, 3)
def soma(x, y):
    return x + y

decoradora = fabrica_de_decoradores()
multiplica = decoradora(lambda x, y: x * y)

dez_mais_cinco = soma(10, 5)
dez_vezes_cinco = multiplica(10, 5)
print(dez_mais_cinco)
print(dez_vezes_cinco)
```

**Saída:**
```
Decoradora 1
Parâmetros do decorador: 1 2 3
Aninhada
Parâmetros do decorador: None None None
Aninhada
15
50
```

**Explicação:**
1. A função `fabrica_de_decoradores` recebe os parâmetros `a`, `b` e `c`.
2. A função `fabrica_de_funcoes` é a decoradora que recebe a função a ser decorada.
3. A função `aninhada` é a função interna que adiciona o comportamento decorador.
4. O decorador é aplicado à função `soma` usando `@fabrica_de_decoradores(1, 2, 3)`.
5. A função `multiplica` é decorada manualmente chamando `fabrica_de_decoradores()`.

### 3.4. Vantagens dos Decoradores com Parâmetros

- **Flexibilidade:** Permite personalizar o comportamento do decorador.
- **Reutilização:** O mesmo decorador pode ser usado com diferentes configurações.
- **Organização:** Torna o código mais modular e legível.

**Dicas:**
- Use decoradores com parâmetros para adicionar funcionalidades configuráveis, como logs, autenticação ou validações.
- Sempre documente os parâmetros aceitos pelo decorador para facilitar o uso.
- Combine decoradores com `@` para manter o código limpo e organizado.

---

## 4. Ordem de Aplicação dos Decoradores

Os **decoradores empilhados** permitem aplicar múltiplos decoradores a uma única função. A ordem em que os decoradores são aplicados é importante, pois cada decorador modifica a função antes que o próximo seja aplicado.

### 4.1. O Que São Decoradores Empilhados?

- Decoradores empilhados são múltiplos decoradores aplicados a uma única função.
- Eles são aplicados de cima para baixo, mas executados de baixo para cima.

**Exemplo:**
```py
@decorador1
@decorador2
def minha_funcao():
    pass
```

- Primeiro, `decorador2` é aplicado à função.
- Em seguida, `decorador1` é aplicado ao resultado de `decorador2`.

### 4.2. Como Funciona a Ordem de Aplicação?

1. O decorador mais próximo da função é aplicado primeiro.
2. O decorador mais distante é aplicado por último.
3. Durante a execução, a ordem é invertida (de baixo para cima).

### 4.3. Exemplo Prático

**Código Completo:**
```py
def parametros_decorador(nome):
    def decorador(func):
        print('Decorador:', nome)

        def sua_nova_funcao(*args, **kwargs):
            res = func(*args, **kwargs)
            final = f'{res} {nome}'
            return final
        return sua_nova_funcao
    return decorador

@parametros_decorador(nome='5')
@parametros_decorador(nome='4')
@parametros_decorador(nome='3')
@parametros_decorador(nome='2')
@parametros_decorador(nome='1')
def soma(x, y):
    return x + y

dez_mais_cinco = soma(10, 5)
print(dez_mais_cinco)
```

**Saída:**
```
Decorador: 1
Decorador: 2
Decorador: 3
Decorador: 4
Decorador: 5
15 1 2 3 4 5
```

**Explicação:**
1. O decorador mais próximo da função (`nome='1'`) é aplicado primeiro.
2. Cada decorador modifica a função antes que o próximo seja aplicado.
3. Durante a execução, os decoradores são chamados na ordem inversa (de baixo para cima).

### 4.4. Dicas para Trabalhar com Decoradores Empilhados

1. **Entenda a Ordem:**
   - Aplique decoradores na ordem em que deseja que eles sejam executados (de baixo para cima).

2. **Teste Individualmente:**
   - Teste cada decorador separadamente antes de empilhá-los.

3. **Documente o Comportamento:**
   - Explique o propósito de cada decorador e a ordem em que eles devem ser aplicados.

4. **Evite Conflitos:**
   - Certifique-se de que os decoradores não alterem o mesmo comportamento de forma conflitante.

**Dicas:**
- Use decoradores empilhados para combinar funcionalidades, como validações, logs e autenticação.
- Sempre teste o comportamento final da função decorada para garantir que os decoradores estão funcionando como esperado.

---