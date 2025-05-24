# POO 4

## Sumário

1. [Python Special Methods, Magic Methods ou Dunder Methods](#1-python-special-methods-magic-methods-ou-dunder-methods)
    - 1.1. [O Que São Dunder Methods?](#11-o-que-são-dunder-methods)
    - 1.2. [Principais Dunder Methods](#12-principais-dunder-methods)
2. [Python Dunder Methods `__repr__` e `__str__`](#2-python-dunder-methods-__repr__-e-__str__)
    - 2.1. [Diferença entre `__repr__` e `__str__`](#21-diferença-entre-__repr__-e-__str__)
    - 2.2. [Exemplo Prático](#22-exemplo-prático)
3. [Dunder Methods para Operadores Matemáticos e Comparação](#3-dunder-methods-para-operadores-matemáticos-e-comparação)
    - 3.1. [Exemplo Prático com Operadores](#31-exemplo-prático-com-operadores)
    - 3.2. [Dicas e Observações](#32-dicas-e-observações)
4. [Métodos `__new__` e `__init__` em Classes Python](#4-métodos-__new__-e-__init__-em-classes-python)
    - 4.1. [O Que é o Método `__new__`?](#41-o-que-é-o-método-__new__)
    - 4.2. [O Que é o Método `__init__`?](#42-o-que-é-o-método-__init__)
    - 4.3. [Diferença entre `__new__` e `__init__`](#43-diferença-entre-__new__-e-__init__)
    - 4.4. [Exemplo Prático](#44-exemplo-prático)
    - 4.5. [Dicas e Observações](#45-dicas-e-observações)

---

## 1. Python Special Methods, Magic Methods ou Dunder Methods

### 1.1. O Que São Dunder Methods?

- **Dunder Methods** (ou **Magic Methods**) são métodos especiais em Python que começam e terminam com dois underscores (`__`), como `__init__`, `__repr__`, etc.
- Eles permitem personalizar o comportamento de objetos em Python.
- São usados para implementar operadores, conversões, representações e muito mais.

### 1.2. Principais Dunder Methods

- **Representação e Conversão:**
  - `__repr__(self)`: Representação oficial do objeto (para desenvolvedores).
  - `__str__(self)`: Representação amigável do objeto (para usuários).
- **Operadores Matemáticos:**
  - `__add__(self, other)`: Soma (`+`).
  - `__sub__(self, other)`: Subtração (`-`).
  - `__mul__(self, other)`: Multiplicação (`*`).
  - `__truediv__(self, other)`: Divisão (`/`).
- **Operadores de Comparação:**
  - `__lt__(self, other)`: Menor que (`<`).
  - `__le__(self, other)`: Menor ou igual (`<=`).
  - `__gt__(self, other)`: Maior que (`>`).
  - `__ge__(self, other)`: Maior ou igual (`>=`).
  - `__eq__(self, other)`: Igual (`==`).
  - `__ne__(self, other)`: Diferente (`!=`).

---

## 2. Python Dunder Methods `__repr__` e `__str__`

### 2.1. Diferença entre `__repr__` e `__str__`

- **`__repr__`:**
  - Deve retornar uma string que represente o objeto de forma não ambígua.
  - É usada principalmente para desenvolvedores.
  - Deve ser possível recriar o objeto a partir da string retornada (quando possível).
- **`__str__`:**
  - Deve retornar uma string amigável para o usuário.
  - É usada em funções como `print()` e `str()`.

### 2.2. Exemplo Prático

```py
class Ponto:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __repr__(self):
        class_name = type(self).__name__
        return f'{class_name}(x={self.x!r}, y={self.y!r})'

p = Ponto(4, 2)
print(repr(p))  # Saída: Ponto(x=4, y=2)
print(p)        # Saída: Ponto(x=4, y=2) (usa __repr__ se __str__ não estiver definido)
```

---

## 3. Dunder Methods para Operadores Matemáticos e Comparação

### 3.1. Exemplo Prático com Operadores

```py
class Ponto:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __repr__(self):
        class_name = type(self).__name__
        return f'{class_name}(x={self.x!r}, y={self.y!r})'

    def __add__(self, other):
        novo_x = self.x + other.x
        novo_y = self.y + other.y
        return Ponto(novo_x, novo_y)

    def __gt__(self, other):
        resultado_self = self.x + self.y
        resultado_other = other.x + other.y
        return resultado_self > resultado_other

if __name__ == '__main__':
    p1 = Ponto(4, 2)  # Soma: 6
    p2 = Ponto(6, 4)  # Soma: 10
    p3 = p1 + p2      # Soma dos pontos
    print(p3)         # Saída: Ponto(x=10, y=6)
    print('P1 é maior que P2:', p1 > p2)  # Saída: False
    print('P2 é maior que P1:', p2 > p1)  # Saída: True
```

**Explicação:**
- `__add__`: Define o comportamento do operador `+` para somar dois objetos `Ponto`.
- `__gt__`: Define o comportamento do operador `>` para comparar dois objetos `Ponto`.

### 3.2. Dicas e Observações

- **`__repr__` e `__str__`:**
  - Sempre implemente `__repr__` para facilitar a depuração.
  - Implemente `__str__` se precisar de uma representação amigável para o usuário.
- **Operadores:**
  - Use dunder methods para personalizar o comportamento de operadores matemáticos e de comparação.
  - Certifique-se de que o comportamento seja intuitivo e consistente.
- **Boas práticas:**
  - Consulte a [documentação oficial](https://docs.python.org/3/reference/datamodel.html#specialnames) para uma lista completa de dunder methods.
  - Use dunder methods para tornar seus objetos mais "pythonicos" e integrados ao ecossistema da linguagem.

**Resumo:**  
Os Dunder Methods permitem personalizar o comportamento de objetos em Python, desde representações (`__repr__`, `__str__`) até operadores matemáticos e de comparação. Eles tornam os objetos mais intuitivos e integrados ao ecossistema Python.

---

## 4. Métodos `__new__` e `__init__` em Classes Python

Os métodos especiais `__new__` e `__init__` são fundamentais para o ciclo de vida de um objeto em Python. Eles controlam a criação e a inicialização de instâncias.

### 4.1. O Que é o Método `__new__`?

- O **`__new__`** é o método responsável por **criar** e **retornar** uma nova instância da classe.
- Ele é chamado antes do `__init__`.
- Recebe a classe como primeiro argumento (`cls`).
- Deve retornar o novo objeto criado.

### 4.2. O Que é o Método `__init__`?

- O **`__init__`** é o método responsável por **inicializar** a instância criada pelo `__new__`.
- Ele é chamado logo após o `__new__`.
- Recebe a instância como primeiro argumento (`self`).
- Não deve retornar nada (retorna `None` implicitamente).

### 4.3. Diferença entre `__new__` e `__init__`

| **Aspecto**         | **`__new__`**                     | **`__init__`**                  |
|----------------------|-----------------------------------|----------------------------------|
| **Responsabilidade**| Criar e retornar o novo objeto    | Inicializar a instância criada  |
| **Recebe**          | A classe (`cls`)                 | A instância (`self`)            |
| **Retorno**         | Deve retornar o novo objeto       | Não deve retornar nada (`None`) |
| **Chamado por**     | Automaticamente pelo Python       | Após o `__new__`                |

### 4.4. Exemplo Prático

```py
class A:
    def __new__(cls, *args, **kwargs):
        print('Chamando __new__')
        instancia = super().__new__(cls)  # Cria a nova instância
        return instancia

    def __init__(self, x):
        print('Chamando __init__')
        self.x = x  # Inicializa a instância

    def __repr__(self):
        return f'A(x={self.x})'

# Criando uma instância
a = A(123)
print(a)       # Saída: A(x=123)
print(a.x)     # Saída: 123
```

**Explicação:**
1. O método `__new__` é chamado para criar o objeto.
2. O método `__init__` é chamado para inicializar o objeto criado.
3. O método `__repr__` é usado para representar o objeto como string.

### 4.5. Dicas e Observações

- **Quando usar `__new__`:**
  - Use `__new__` apenas se precisar personalizar o processo de criação do objeto.
  - Exemplo: Implementar singletons, metaclasses ou classes imutáveis.
- **Quando usar `__init__`:**
  - Use `__init__` para inicializar atributos e configurar o estado inicial do objeto.
- **Boa prática:**
  - Na maioria dos casos, você só precisará sobrescrever o `__init__`.
  - O `__new__` é mais avançado e raramente necessário.

**Resumo:**  
O método `__new__` cria e retorna o novo objeto, enquanto o método `__init__` inicializa a instância criada. Ambos são fundamentais para o ciclo de vida de um objeto em Python, mas o `__new__` é usado apenas em casos específicos.

---