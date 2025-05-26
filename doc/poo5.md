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
5. [Funções Decoradoras e Decoradores com Métodos](#5-funções-decoradoras-e-decoradores-com-métodos)
    - 5.1. [O Que São Decoradores?](#51-o-que-são-decoradores)
    - 5.2. [Decoradores para Métodos](#52-decoradores-para-métodos)
    - 5.3. [Decorador para Adicionar `__repr__`](#53-decorador-para-adicionar-__repr__)
    - 5.4. [Decorador para Métodos](#54-decorador-para-métodos)
    - 5.5. [Dicas e Boas Práticas](#55-dicas-e-boas-práticas)
6. [Método Especial `__call__`](#6-método-especial-__call__)
    - 6.1. [O Que é o Método `__call__`?](#61-o-que-é-o-método-__call__)
    - 6.2. [Como Funciona o `__call__`](#62-como-funciona-o-__call__)
    - 6.3. [Exemplo Prático](#63-exemplo-prático)
    - 6.4. [Dicas e Boas Práticas](#64-dicas-e-boas-práticas)
7. [Classes Decoradoras (Decorator Classes)](#7-classes-decoradoras-decorator-classes)
    - 7.1. [O Que São Classes Decoradoras?](#71-o-que-são-classes-decoradoras)
    - 7.2. [Como Funcionam?](#72-como-funcionam)
    - 7.3. [Exemplo Prático](#73-exemplo-prático)
    - 7.4. [Dicas e Boas Práticas](#74-dicas-e-boas-práticas)


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

## 5. Funções Decoradoras e Decoradores com Métodos

### 5.1. O Que São Decoradores?

- **Decoradores** são funções que modificam o comportamento de outras funções, métodos ou classes.
- Eles são aplicados usando o símbolo `@` antes da definição de uma função, método ou classe.

### 5.2. Decoradores para Métodos

- Decoradores podem ser usados para modificar o comportamento de métodos em classes.
- Eles permitem adicionar lógica antes ou depois da execução do método original.

### 5.3. Decorador para Adicionar `__repr__`

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
```

**Explicação:**
- O decorador `adiciona_repr` adiciona dinamicamente o método `__repr__` às classes decoradas.
- Isso permite que as classes tenham uma representação personalizada ao serem convertidas para string.

### 5.4. Decorador para Métodos

```py
def meu_planeta(metodo):
    """
    Decorador que modifica o comportamento do método `falar_nome`.
    """
    def interno(self, *args, **kwargs):
        resultado = metodo(self, *args, **kwargs)

        if 'Terra' in resultado:
            return 'Você está em casa'

        return f'{resultado} - Método decorado'
    return interno

@adiciona_repr
class Planeta:
    def __init__(self, nome):
        self.nome = nome

    @meu_planeta
    def falar_nome(self):
        return f'O planeta é {self.nome}'

# Criando instâncias
terra = Planeta('Terra')
marte = Planeta('Marte')

# Testando o método decorado
print(terra.falar_nome())  # Saída: Você está em casa
print(marte.falar_nome())  # Saída: O planeta é Marte - Método decorado
```

**Explicação:**
- O decorador `meu_planeta` modifica o comportamento do método `falar_nome`.
- Se o método retornar "Terra", o decorador retorna "Você está em casa".
- Caso contrário, ele adiciona " - Método decorado" ao resultado original.

### 5.5. Dicas e Boas Práticas

- **Reutilização:**
  - Use decoradores para adicionar funcionalidades reutilizáveis a métodos ou classes.
- **Documentação:**
  - Sempre adicione docstrings aos decoradores para explicar o que eles fazem.
- **Evite Complexidade:**
  - Mantenha os decoradores simples e fáceis de entender.
- **Teste o Comportamento:**
  - Certifique-se de que o decorador não altera o comportamento esperado do método ou classe original.

**Resumo:**  
Decoradores são ferramentas poderosas para modificar o comportamento de métodos e classes em Python. Eles permitem adicionar funcionalidades de forma elegante e reutilizável, promovendo um design de código mais limpo e eficiente.

---

## 6. Método Especial `__call__`

### 6.1. O Que é o Método `__call__`?

- O método especial `__call__` permite que uma instância de classe seja chamada como se fosse uma função.
- Quando você usa parênteses em uma instância de classe, o Python chama automaticamente o método `__call__` da classe.

### 6.2. Como Funciona o `__call__`

- O método `__call__` transforma a instância de uma classe em algo **callable** (executável com parênteses).
- Ele pode receber argumentos como uma função normal.
- O retorno do método `__call__` será o valor retornado pela chamada da instância.

### 6.3. Exemplo Prático

```py
class CallMe:
    def __init__(self, phone):
        self.phone = phone

    def __call__(self, nome):
        print(nome, 'está chamando', self.phone)
        return 2134

# Criando uma instância
call1 = CallMe('23945876545')

# Chamando a instância como uma função
retorno = call1('Luiz Otávio')  # Saída: Luiz Otávio está chamando 23945876545
print(retorno)                  # Saída: 2134
```

**Explicação:**
1. A classe `CallMe` define o método especial `__call__`.
2. A instância `call1` é chamada como uma função (`call1('Luiz Otávio')`).
3. O método `__call__` é executado, imprimindo uma mensagem e retornando um valor.

### 6.4. Dicas e Boas Práticas

- **Quando usar `__call__`:**
  - Use o método `__call__` para criar objetos que precisam ser executados como funções.
  - Exemplos: Funções de callback, wrappers ou objetos que encapsulam lógica de execução.
- **Evite abusos:**
  - Não use `__call__` para substituir funções normais sem necessidade.
  - Mantenha o uso claro e intuitivo.
- **Documente o comportamento:**
  - Adicione docstrings ao método `__call__` para explicar o que ele faz e quais argumentos ele aceita.

**Resumo:**  
O método especial `__call__` transforma instâncias de classes em objetos "callables", permitindo que sejam chamadas como funções. Ele é útil para encapsular lógica de execução em objetos, promovendo flexibilidade e reutilização de código.

---

## 7. Classes Decoradoras (Decorator Classes)

### 7.1. O Que São Classes Decoradoras?

- **Classes decoradoras** são classes que implementam o método especial `__call__` para que possam ser usadas como decoradores.
- Elas permitem encapsular lógica de decoração em uma classe, tornando o código mais organizado e reutilizável.

### 7.2. Como Funcionam?

- Quando uma classe decoradora é usada com `@`, ela recebe a função decorada como argumento no método `__call__`.
- O método `__call__` pode modificar o comportamento da função decorada e retornar uma nova função.

### 7.3. Exemplo Prático

```py
class Multiplicar:
    def __init__(self, multiplicador):
        self._multiplicador = multiplicador

    def __call__(self, func):
        def interna(*args, **kwargs):
            resultado = func(*args, **kwargs)
            return resultado * self._multiplicador
        return interna

@Multiplicar(2)
def soma(x, y):
    return x + y

# Usando a função decorada
dois = soma(2, 4)  # (2 + 4) * 2
print(dois)        # Saída: 12
```

**Explicação:**
1. A classe `Multiplicar` é inicializada com um valor (`multiplicador`).
2. O método `__call__` recebe a função decorada (`soma`) e retorna uma nova função (`interna`).
3. A função `interna` executa a função original (`soma`) e multiplica o resultado pelo valor do multiplicador.

### 7.4. Dicas e Boas Práticas

- **Quando usar classes decoradoras:**
  - Use classes decoradoras quando precisar de decoradores com estado (como o multiplicador no exemplo).
  - Elas são úteis para encapsular lógica complexa de decoração.
- **Documente o comportamento:**
  - Adicione docstrings à classe e ao método `__call__` para explicar o que o decorador faz.
- **Evite complexidade desnecessária:**
  - Use funções decoradoras simples quando não precisar de estado ou lógica complexa.

**Resumo:**  
Classes decoradoras são uma forma poderosa de criar decoradores em Python, especialmente quando é necessário manter estado ou encapsular lógica complexa. Elas utilizam o método especial `__call__` para modificar o comportamento de funções decoradas.

---