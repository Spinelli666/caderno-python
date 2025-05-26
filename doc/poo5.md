# POO 5

## Sumário

1. [Context Manager com Classes - Criando e Usando Gerenciadores de Contexto](#1-context-manager-com-classes---criando-e-usando-gerenciadores-de-contexto)
    - 1.1. [O Que é um Context Manager?](#11-o-que-é-um-context-manager)
    - 1.2. [Duck Typing e Protocolos em Python](#12-duck-typing-e-protocolos-em-python)
    - 1.3. [Como Criar um Context Manager com Classes](#13-como-criar-um-context-manager-com-classes)
    - 1.4. [Exemplo Prático](#14-exemplo-prático)
2. [Exceptions em Context Manager com Classes](#2-exceptions-em-context-manager-com-classes)
    - 2.1. [Tratamento de Exceções no Método `__exit__`](#21-tratamento-de-exceções-no-método-__exit__)
    - 2.2. [Exemplo Prático com Exceções](#22-exemplo-prático-com-exceções)
    - 2.3. [Dicas e Observações](#23-dicas-e-observações)
3. [Context Manager com `contextlib.contextmanager`](#3-context-manager-com-contextlibcontextmanager)
    - 3.1. [O Que é um Context Manager com Função?](#31-o-que-é-um-context-manager-com-função)
    - 3.2. [Como Criar um Context Manager com `contextlib.contextmanager`](#32-como-criar-um-context-manager-com-contextlibcontextmanager)
    - 3.3. [Exemplo Prático](#33-exemplo-prático)
    - 3.4. [Tratamento de Exceções em Context Managers com Funções](#34-tratamento-de-exceções-em-context-managers-com-funções)
    - 3.5. [Dicas e Observações](#35-dicas-e-observações)
4. [Funções Decoradoras e Decoradores com Classes](#4-funções-decoradoras-e-decoradores-com-classes)
    - 4.1. [O Que São Decoradores?](#41-o-que-são-decoradores)
    - 4.2. [Funções Decoradoras](#42-funções-decoradoras)
    - 4.3. [Decoradores com Classes](#43-decoradores-com-classes)
    - 4.4. [Função Decoradora para Adicionar `__repr__`](#44-função-decoradora-para-adicionar-__repr__)
    - 4.5. [Mixin para Adicionar `__repr__`](#45-mixin-para-adicionar-__repr__)
    - 4.6. [Dicas e Boas Práticas](#46-dicas-e-boas-práticas)

---

## 1. Context Manager com Classes - Criando e Usando Gerenciadores de Contexto

### 1.1. O Que é um Context Manager?

- Um **Context Manager** é uma estrutura que gerencia recursos automaticamente, garantindo que eles sejam inicializados e liberados corretamente.
- É usado com a instrução `with`, que simplifica o gerenciamento de recursos como arquivos, conexões de banco de dados, etc.

---

### 1.2. Duck Typing e Protocolos em Python

- **Duck Typing:** Em Python, o comportamento de um objeto é mais importante do que seu tipo. Se um objeto implementa os métodos necessários, ele pode ser usado como esperado.
- **Exemplo:** "Se anda como um pato, nada como um pato e grasna como um pato, então é um pato."
- Para criar um Context Manager, é necessário implementar os métodos `__enter__` e `__exit__`.

---

### 1.3. Como Criar um Context Manager com Classes

- **`__enter__`:**
  - É chamado no início do bloco `with`.
  - Deve retornar o recurso gerenciado.
- **`__exit__`:**
  - É chamado no final do bloco `with`, mesmo que ocorra uma exceção.
  - Recebe três argumentos:
    - `class_exception`: A classe da exceção (se houver).
    - `exception_`: A instância da exceção (se houver).
    - `traceback_`: O traceback da exceção (se houver).
  - Retornar `True` suprime a exceção.

---

### 1.4. Exemplo Prático

```py
class MyOpen:
    def __init__(self, caminho_arquivo, modo):
        self.caminho_arquivo = caminho_arquivo
        self.modo = modo
        self._arquivo = None

    def __enter__(self):
        print('ABRINDO ARQUIVO')
        self._arquivo = open(self.caminho_arquivo, self.modo, encoding='utf-8')
        return self._arquivo

    def __exit__(self, class_exception, exception_, traceback_):
        print('FECHANDO ARQUIVO')
        self._arquivo.close()

        # Exemplo de tratamento de exceções
        if exception_:
            print('Exceção tratada:', exception_)
            return True  # Suprime a exceção

# Usando o Context Manager
with MyOpen('aulas/aula149.txt', 'w') as arquivo:
    arquivo.write('Escrevendo no arquivo com MyOpen\n')
    arquivo.write('Outra linha no arquivo\n', 123)  # Gera uma exceção
    print('WITH', arquivo)
```

**Saída esperada:**
```
ABRINDO ARQUIVO
FECHANDO ARQUIVO
Exceção tratada: write() argument must be str, not int
```

---

## 2. Exceptions em Context Manager com Classes

### 2.1. Tratamento de Exceções no Método `__exit__`

- O método `__exit__` pode tratar exceções levantadas dentro do bloco `with`.
- Se `__exit__` retornar `True`, a exceção será suprimida e não será propagada.
- Caso contrário, a exceção será relançada.

---

### 2.2. Exemplo Prático com Exceções

```py
class MyOpen:
    def __init__(self, caminho_arquivo, modo):
        self.caminho_arquivo = caminho_arquivo
        self.modo = modo
        self._arquivo = None

    def __enter__(self):
        print('ABRINDO ARQUIVO')
        self._arquivo = open(self.caminho_arquivo, self.modo, encoding='utf-8')
        return self._arquivo

    def __exit__(self, class_exception, exception_, traceback_):
        print('FECHANDO ARQUIVO')
        self._arquivo.close()

        if exception_:
            print('Exceção capturada:', exception_)
            return True  # Suprime a exceção

# Usando o Context Manager
try:
    with MyOpen('aulas/aula149.txt', 'w') as arquivo:
        arquivo.write('Escrevendo no arquivo com MyOpen\n')
        arquivo.write('Outra linha no arquivo\n', 123)  # Gera uma exceção
except Exception as e:
    print('Exceção não suprimida:', e)
```

**Saída esperada:**
```
ABRINDO ARQUIVO
FECHANDO ARQUIVO
Exceção capturada: write() argument must be str, not int
```

---

### 2.3. Dicas e Observações

- **Quando usar Context Managers:**
  - Sempre que precisar gerenciar recursos como arquivos, conexões de banco de dados, etc.
- **Tratamento de Exceções:**
  - Use o método `__exit__` para capturar e tratar exceções.
  - Retorne `True` no `__exit__` para suprimir exceções.
- **Boas práticas:**
  - Implemente `__enter__` e `__exit__` para criar gerenciadores de contexto personalizados.
  - Use o módulo `contextlib` para simplificar a criação de context managers.

---

**Resumo:**  
Os Context Managers em Python permitem gerenciar recursos de forma eficiente e segura. Implementando os métodos `__enter__` e `__exit__`, é possível criar gerenciadores personalizados que tratam exceções e garantem a liberação de recursos.

---

## 3. Context Manager com `contextlib.contextmanager`

### 3.1. O Que é um Context Manager com Função?

- Um **Context Manager** com função é uma forma simplificada de criar gerenciadores de contexto usando o decorador `@contextmanager` do módulo `contextlib`.
- Ele permite criar gerenciadores de contexto sem a necessidade de implementar os métodos `__enter__` e `__exit__`.

### 3.2. Como Criar um Context Manager com `contextlib.contextmanager`

- Use o decorador `@contextmanager` para transformar uma função em um gerenciador de contexto.
- Dentro da função:
  - Use `yield` para retornar o recurso gerenciado.
  - O código antes do `yield` será executado no início do bloco `with`.
  - O código após o `yield` será executado no final do bloco `with`, mesmo que ocorra uma exceção.

### 3.3. Exemplo Prático

```py
from contextlib import contextmanager

@contextmanager
def my_open(caminho_arquivo, modo):
    try:
        print('ABRINDO ARQUIVO')
        arquivo = open(caminho_arquivo, modo, encoding='utf-8')
        yield arquivo
    finally:
        print('FECHANDO ARQUIVO')
        arquivo.close()

# Usando o Context Manager
with my_open('aulas/aula150.txt', 'w') as arquivo:
    arquivo.write('Linha 1\n')
    arquivo.write('Linha 2\n')
    arquivo.write('Linha 3\n')
    print('WITH', arquivo)
```

**Saída esperada:**
```
ABRINDO ARQUIVO
WITH <_io.TextIOWrapper name='aulas/aula150.txt' mode='w' encoding='utf-8'>
FECHANDO ARQUIVO
```

### 3.4. Tratamento de Exceções em Context Managers com Funções

- O bloco `try` dentro do gerenciador de contexto pode capturar exceções levantadas no bloco `with`.
- Use o bloco `finally` para garantir que os recursos sejam liberados.

```py
from contextlib import contextmanager

@contextmanager
def my_open(caminho_arquivo, modo):
    try:
        print('ABRINDO ARQUIVO')
        arquivo = open(caminho_arquivo, modo, encoding='utf-8')
        yield arquivo
    except Exception as e:
        print(f'Ocorreu um erro: {e}')
    finally:
        print('FECHANDO ARQUIVO')
        arquivo.close()

# Usando o Context Manager com erro
with my_open('aulas/aula150.txt', 'w') as arquivo:
    arquivo.write('Linha 1\n')
    arquivo.write('Linha 2\n', 123)  # Gera uma exceção
    arquivo.write('Linha 3\n')
    print('WITH', arquivo)
```

**Saída esperada:**
```
ABRINDO ARQUIVO
Ocorreu um erro: write() argument must be str, not int
FECHANDO ARQUIVO
```

### 3.5. Dicas e Observações

- **Quando usar `contextlib.contextmanager`:**
  - Use quando precisar criar gerenciadores de contexto simples e não quiser implementar uma classe com `__enter__` e `__exit__`.
- **Tratamento de Exceções:**
  - Sempre use `try` e `finally` para garantir que os recursos sejam liberados corretamente.
- **Boas práticas:**
  - Certifique-se de que o código após o `yield` seja executado, mesmo em caso de erro.
  - Use mensagens claras para identificar erros no gerenciador de contexto.

**Resumo:**  
O decorador `@contextmanager` do módulo `contextlib` simplifica a criação de gerenciadores de contexto em Python. Ele permite gerenciar recursos de forma eficiente e segura, com suporte a tratamento de exceções e liberação de recursos.

---

## 4. Funções Decoradoras e Decoradores com Classes

### 4.1. O Que São Decoradores?

- **Decoradores** são funções ou classes que modificam o comportamento de outras funções ou classes.
- Eles são amplamente usados para adicionar funcionalidades de forma reutilizável e elegante.
- Em Python, decoradores são aplicados usando o símbolo `@`.

### 4.2. Funções Decoradoras

- Uma **função decoradora** é uma função que recebe outra função ou classe como argumento e retorna uma nova função ou classe com comportamento modificado.
- Decoradores podem ser usados para adicionar métodos, modificar atributos ou alterar o comportamento de classes e funções.

### 4.3. Decoradores com Classes

- Decoradores também podem ser usados para modificar classes.
- Eles permitem adicionar ou alterar métodos e atributos de uma classe de forma dinâmica.

### 4.4. Função Decoradora para Adicionar `__repr__`

```py
def meu_repr(self):
    class_name = self.__class__.__name__
    class_dict = self.__dict__
    class_repr = f'{class_name}({class_dict})'
    return class_repr

def adiciona_repr(cls):
    """
    Decorador que adiciona um método __repr__ personalizado à classe.
    """
    cls.__repr__ = meu_repr
    return cls

@adiciona_repr
class Time:
    def __init__(self, nome):
        self.nome = nome

@adiciona_repr
class Planeta:
    def __init__(self, nome):
        self.nome = nome

# Criando instâncias
brasil = Time('Brasil')
portugal = Time('Portugal')

terra = Planeta('Terra')
marte = Planeta('Marte')

# Testando o __repr__
print(brasil)    # Saída: Time({'nome': 'Brasil'})
print(portugal)  # Saída: Time({'nome': 'Portugal'})
print(terra)     # Saída: Planeta({'nome': 'Terra'})
print(marte)     # Saída: Planeta({'nome': 'Marte'})
```

**Explicação:**
- A função `adiciona_repr` adiciona dinamicamente o método `__repr__` às classes decoradas.
- O método `__repr__` é usado para representar a classe como string, mostrando o nome da classe e seus atributos.

### 4.5. Mixin para Adicionar `__repr__`

Outra abordagem para adicionar o método `__repr__` é usar uma classe **Mixin**.

```py
class MyReprMixin:
    def __repr__(self):
        class_name = self.__class__.__name__
        class_dict = self.__dict__
        class_repr = f'{class_name}({class_dict})'
        return class_repr

class Time(MyReprMixin):
    def __init__(self, nome):
        self.nome = nome

class Planeta(MyReprMixin):
    def __init__(self, nome):
        self.nome = nome

# Criando instâncias
brasil = Time('Brasil')
portugal = Time('Portugal')

terra = Planeta('Terra')
marte = Planeta('Marte')

# Testando o __repr__
print(brasil)    # Saída: Time({'nome': 'Brasil'})
print(portugal)  # Saída: Time({'nome': 'Portugal'})
print(terra)     # Saída: Planeta({'nome': 'Terra'})
print(marte)     # Saída: Planeta({'nome': 'Marte'})
```

**Explicação:**
- A classe `MyReprMixin` define o método `__repr__`.
- As classes `Time` e `Planeta` herdam de `MyReprMixin`, reutilizando o método `__repr__`.

### 4.6. Dicas e Boas Práticas

- **Escolha entre Decoradores e Mixins:**
  - Use **decoradores** quando quiser adicionar funcionalidades de forma dinâmica e reutilizável.
  - Use **mixins** quando quiser compartilhar funcionalidades entre várias classes por meio de herança.
- **Documente seus Decoradores:**
  - Sempre adicione docstrings para explicar o que o decorador faz.
- **Evite Modificações Complexas:**
  - Mantenha os decoradores simples e fáceis de entender.
- **Teste o Comportamento:**
  - Certifique-se de que o comportamento esperado foi adicionado corretamente às classes decoradas.

**Resumo:**  
Decoradores e mixins são ferramentas poderosas para adicionar ou modificar funcionalidades em classes. Decoradores permitem modificar classes de forma dinâmica, enquanto mixins oferecem uma abordagem baseada em herança para compartilhar funcionalidades.

---