# POO 6

## Sumário

1. [Teoria: Metaclasses em Python](#1-teoria-metaclasses-em-python)
    - 1.1. [O Que São Metaclasses?](#11-o-que-são-metaclasses)
    - 1.2. [Como Funcionam as Metaclasses?](#12-como-funcionam-as-metaclasses)
    - 1.3. [Métodos Importantes das Metaclasses](#13-métodos-importantes-das-metaclasses)
    - 1.4. [Exemplo Prático](#14-exemplo-prático)
    - 1.5. [Dicas e Observações](#15-dicas-e-observações)
2. [`dir` e `help` + DocStrings](#2-dir-e-help--docstrings)
    - 2.1. [O Que São `dir` e `help`?](#21-o-que-são-dir-e-help)
    - 2.2. [O Que São DocStrings?](#22-o-que-são-docstrings)
    - 2.3. [Exemplos Práticos](#23-exemplos-práticos)
    - 2.4. [Dicas e Boas Práticas](#24-dicas-e-boas-práticas)
3. [Enumerações (`enum.Enum`)](#3-enumerações-enumenum)
    - 3.1. [O Que São Enumerações?](#31-o-que-são-enumerações)
    - 3.2. [Características das Enumerações em Python](#32-características-das-enumerações-em-python)
    - 3.3. [Como Criar Enumerações](#33-como-criar-enumerações)
    - 3.4. [Acessando Membros e Valores](#34-acessando-membros-e-valores)
    - 3.5. [Exemplo Prático](#35-exemplo-prático)
    - 3.6. [Dicas e Boas Práticas](#36-dicas-e-boas-práticas)
4. [Dataclasses - O Que São?](#4-dataclasses---o-que-são)
    - 4.1. [O Que São Dataclasses?](#41-o-que-são-dataclasses)
    - 4.2. [Por Que Usar Dataclasses?](#42-por-que-usar-dataclasses)
    - 4.3. [Métodos Especiais: `__init__` e `__post_init__`](#43-métodos-especiais-init-e-post_init)
    - 4.4. [Configurações do Decorador `@dataclass`](#44-configurações-do-decorador-dataclass)
    - 4.5. [Funções Auxiliares: `asdict` e `astuple`](#45-funções-auxiliares-asdict-e-astuple)
    - 4.6. [Valores Padrão, `field` e `fields`](#46-valores-padrão-field-e-fields)
    - 4.7. [Exemplo Prático](#47-exemplo-prático)
    - 4.8. [Dicas e Boas Práticas](#48-dicas-e-boas-práticas)
5. [NamedTuple - Tuplas Imutáveis com Nomes para Valores](#5-namedtuple---tuplas-imutáveis-com-nomes-para-valores)
    - 5.1. [O Que São NamedTuples?](#51-o-que-são-namedtuples)
    - 5.2. [Por Que Usar NamedTuples?](#52-por-que-usar-namedtuples)
    - 5.3. [Características das NamedTuples](#53-características-das-namedtuples)
    - 5.4. [Exemplo Prático](#54-exemplo-prático)
    - 5.5. [Dicas e Boas Práticas](#55-dicas-e-boas-práticas)
6. [Criando Sua Própria Lista com Iterable, Iterator e Sequence](#6-criando-sua-própria-lista-com-iterable-iterator-e-sequence)
    - 6.1. [O Que São Iterable, Iterator e Sequence?](#61-o-que-são-iterable-iterator-e-sequence)
    - 6.2. [Por Que Implementar Protocolos?](#62-por-que-implementar-protocolos)
    - 6.3. [Protocolo Sequence](#63-protocolo-sequence)
    - 6.4. [Protocolo Iterator](#64-protocolo-iterator)
    - 6.5. [Exemplo Prático](#65-exemplo-prático)
    - 6.6. [Dicas e Boas Práticas](#66-dicas-e-boas-práticas)

---

## 1. Teoria: Metaclasses em Python

### 1.1. O Que São Metaclasses?

- **Metaclasses** são o tipo das classes.  
  Assim como objetos são instâncias de classes, **classes são instâncias de metaclasses**.
- Em Python, **tudo é um objeto**, incluindo classes.  
  O tipo padrão de uma classe é `type`, que é a metaclasse padrão.
- **Exemplo:**
  ```py
  class Foo:
      pass

  print(type(Foo))  # Saída: <class 'type'>
  ```

### 1.2. Como Funcionam as Metaclasses?

- Quando você cria uma classe, o Python usa a metaclasse para criar a classe.
- O processo ocorre na seguinte ordem:
  1. **`__new__` da metaclasse:**  
     É chamado para criar a nova classe.
  2. **`__call__` da metaclasse:**  
     É chamado para criar e inicializar instâncias da classe. Ele chama:
     - **`__new__` da classe:** Cria a instância.
     - **`__init__` da classe:** Inicializa a instância.
  3. **`__call__` da metaclasse:** Finaliza a execução.

### 1.3. Métodos Importantes das Metaclasses

- **`__new__(mcs, name, bases, dct):`**  
  - Cria a nova classe.
  - `mcs`: A própria metaclasse.
  - `name`: Nome da classe.
  - `bases`: Tupla com as classes base.
  - `dct`: Dicionário com os atributos e métodos da classe.
- **`__call__(cls, *args, **kwargs):`**  
  - Cria e inicializa instâncias da classe.
  - Chama `__new__` e `__init__` da classe.

### 1.4. Exemplo Prático

```py
def meu_repr(self):
    return f'{type(self).__name__}({self.__dict__})'

class Meta(type):
    def __new__(mcs, name, bases, dct):
        print('METACLASS NEW')
        cls = super().__new__(mcs, name, bases, dct)
        cls.attr = 1234
        cls.__repr__ = meu_repr

        if 'falar' not in cls.__dict__ or not callable(cls.__dict__['falar']):
            raise TypeError('Você precisa implementar o método falar')

        return cls
    
    def __call__(cls, *args, **kwargs):
        instancia = super().__call__(*args, **kwargs)

        if 'nome' not in instancia.__dict__:
            raise TypeError('Crie o attr nome')

        return instancia

class Pessoa(metaclass=Meta):
    def __new__(cls, *args, **kwargs):
        print('MEU NEW')
        instancia = super().__new__(cls)
        return instancia
    
    def __init__(self, nome):
        print('MEU INIT')
        self.nome = nome

    def falar(self):
        print('FALANDO')

# Criando uma instância
p1 = Pessoa('Luiz Otávio')
p1.falar()
```

**Saída esperada:**
```
METACLASS NEW
MEU NEW
MEU INIT
FALANDO
```

**Explicação detalhada:**

1. **Definição do método `meu_repr`:**
   - Este método é usado para personalizar a representação (`__repr__`) de instâncias da classe.
   - Ele retorna uma string contendo o nome da classe e os atributos da instância.

2. **Definição da metaclasse `Meta`:**
   - A metaclasse `Meta` herda de `type` e redefine os métodos `__new__` e `__call__`.

   - **`Meta.__new__`:**
     - É chamado quando a classe `Pessoa` é criada.
     - Adiciona o atributo `attr` e o método `__repr__` à classe.
     - Verifica se o método `falar` está presente na classe e se é chamável (`callable`). Caso contrário, levanta um erro `TypeError`.

   - **`Meta.__call__`:**
     - É chamado quando uma instância da classe `Pessoa` é criada.
     - Após criar a instância, verifica se o atributo `nome` foi definido. Caso contrário, levanta um erro `TypeError`.

3. **Definição da classe `Pessoa`:**
   - A classe `Pessoa` usa a metaclasse `Meta` (especificada com `metaclass=Meta`).
   - Redefine os métodos `__new__` e `__init__`.

   - **`Pessoa.__new__`:**
     - É chamado para criar a instância da classe.
     - Imprime "MEU NEW" e retorna a instância criada.

   - **`Pessoa.__init__`:**
     - É chamado para inicializar a instância criada.
     - Define o atributo `nome` e imprime "MEU INIT".

   - **`Pessoa.falar`:**
     - É um método simples que imprime "FALANDO".

4. **Criação da classe `Pessoa`:**
   - Quando o Python encontra a definição da classe `Pessoa`, ele chama `Meta.__new__` para criar a classe.
   - Durante a execução de `Meta.__new__`:
     - O atributo `attr` é adicionado à classe.
     - O método `__repr__` é adicionado à classe.
     - É verificado se o método `falar` está presente e é chamável.

5. **Criação da instância `p1`:**
   - Quando `Pessoa('Luiz Otávio')` é chamado:
     - `Meta.__call__` é executado.
     - Dentro de `Meta.__call__`:
       - `Pessoa.__new__` é chamado para criar a instância.
       - `Pessoa.__init__` é chamado para inicializar a instância.
       - É verificado se o atributo `nome` foi definido na instância.

6. **Chamando o método `falar`:**
   - O método `falar` é chamado na instância `p1`, imprimindo "FALANDO".

**Resumo do fluxo de execução:**
1. `Meta.__new__` cria a classe `Pessoa`.
2. `Meta.__call__` cria e inicializa a instância `p1`.
3. O método `falar` é chamado na instância `p1`.

### 1.5. Dicas e Observações

- **Quando usar metaclasses:**
  - Use metaclasses apenas quando precisar modificar o comportamento de criação de classes.
  - Exemplos: Adicionar atributos/métodos automaticamente, validar classes, criar singletons.
- **Evite complexidade desnecessária:**
  - Metaclasses são avançadas e podem tornar o código difícil de entender.
  - Se você não tem certeza de que precisa de uma metaclasse, provavelmente não precisa.
- **Documente o comportamento:**
  - Explique claramente o que a metaclasse faz e por que ela é necessária.
- **Alternativas:**
  - Considere usar decoradores ou mixins antes de recorrer a metaclasses.

**Resumo:**  
Metaclasses são o tipo das classes e controlam como as classes são criadas e instanciadas. Elas permitem modificar o comportamento de criação de classes e instâncias, mas devem ser usadas com cuidado devido à sua complexidade.

---

## 2. `dir` e `help` + DocStrings

### 2.1. O Que São `dir` e `help`?

- **`dir`:**
  - Retorna uma lista de atributos e métodos disponíveis para um objeto.
  - Útil para explorar o que está disponível em um módulo, classe ou instância.
  - Exemplo: `dir(objeto)`.

- **`help`:**
  - Exibe a documentação de um objeto, incluindo suas DocStrings.
  - Útil para entender o que um módulo, classe ou função faz.
  - Exemplo: `help(objeto)`.

### 2.2. O Que São DocStrings?

- **DocStrings** são strings de documentação associadas a módulos, classes, funções ou métodos.
- Elas explicam o que o código faz e como usá-lo.
- São definidas usando aspas triplas (`"""` ou `'''`).
- Podem ser de:
  - **Uma linha:** Breve descrição.
  - **Várias linhas:** Explicação detalhada, incluindo parâmetros e retornos.

### 2.3. Exemplos Práticos

#### DocStrings em Módulos

**Arquivo `uma_linha.py`:**
```py
'''Documentação do módulo.'''

variavel = 'valor'

def funcao():
    return 1
```

**Uso:**
```py
import uma_linha

print(uma_linha.__doc__)  # Saída: Documentação do módulo.
print(dir(uma_linha))     # Lista os atributos e métodos do módulo.
```

**Arquivo `varias_linhas.py`:**
```py
'''O que seu módulo faz

Dá para colocar em texto grande caso você quer ter uma doc gigante no seu módulo.
# Varias linhas de docstring
# Você pode colocar várias linhas de docstring
# e o Python vai entender tudo isso como uma única docstring.
'''
```

**Uso:**
```py
import varias_linhas

print(varias_linhas.__doc__)  # Exibe a docstring detalhada do módulo.
```

#### DocStrings em Funções

**Arquivo `documentando_funcoes.py`:**
```py
"""Este é um módulo de exemplo

Este módulo contém funções e exemplos de documentação de funções.
"""

def soma(x: int | float, y: int | float) -> int | float:
    """Soma x e y

    :param x: Número 1
    :type x: int or float
    :param y: Número 2
    :type y: int or float

    :return: A soma entre x e y
    :rtype: int or float
    """
    return x + y
```

**Uso:**
```py
import documentando_funcoes

help(documentando_funcoes.soma)
# Exibe a documentação detalhada da função `soma`.
```

#### DocStrings em Classes e Métodos

**Arquivo `documentando_class.py`:**
```py
"""Este é um módulo de exemplo

Este módulo contém funções e exemplos de documentação de funções.
"""

class Foo:
    def soma(self, x: int | float, y: int | float) -> int | float:
        """Soma x e y

        :param x: Número 1
        :type x: int or float
        :param y: Número 2
        :type y: int or float

        :return: A soma entre x e y
        :rtype: int or float
        """
        return x + y

    def bar(self) -> int:
        '''O que ele faz
        
        :raises NotImplementedError: Se não for implementado
        :raises ValueError: Se não for implementado
        '''
        raise NotImplementedError("Método não implementado")
```

**Uso:**
```py
import documentando_class

help(documentando_class.Foo)
# Exibe a documentação da classe `Foo` e seus métodos.
```

### 2.4. Dicas e Boas Práticas

- **Escreva DocStrings claras e objetivas:**
  - Explique o que o código faz e como usá-lo.
  - Inclua informações sobre parâmetros, tipos e retornos.

- **Use DocStrings de várias linhas para detalhes:**
  - Inclua exemplos de uso, quando necessário.
  - Documente exceções levantadas com `:raises`.

- **Mantenha a consistência:**
  - Use o mesmo estilo de documentação em todo o projeto.

- **Aproveite `help` e `dir`:**
  - Use `help` para verificar se suas DocStrings estão claras.
  - Use `dir` para explorar módulos e classes.

**Resumo:**  
DocStrings são essenciais para documentar módulos, funções e classes em Python. Combinadas com `dir` e `help`, elas tornam o código mais legível e fácil de usar, promovendo boas práticas de desenvolvimento.

---

## 3. Enumerações (`enum.Enum`)

### 3.1. O Que São Enumerações?

- **Enumerações** são usadas para representar um conjunto fixo de valores simbólicos.
- Elas são úteis em situações onde há um número limitado de opções ou estados possíveis.
- Exemplos: Direções (`ESQUERDA`, `DIREITA`), dias da semana (`SEGUNDA`, `TERÇA`), etc.

### 3.2. Características das Enumerações em Python

- **Membros e valores constantes:**  
  Os membros de uma enumeração são constantes e não podem ser alterados.
- **Iteráveis:**  
  Enumerações podem ser iteradas para retornar seus membros na ordem de definição.
- **Tipo especial:**  
  `enum.Enum` é a superclasse para criar enumerações, mas elas não são classes normais em Python.
- **Compatibilidade com type annotations:**  
  Enumerações podem ser usadas com `type annotations`, `isinstance` e outras verificações de tipo.

### 3.3. Como Criar Enumerações

- **Usando `enum.Enum`:**  
  Crie uma classe que herda de `enum.Enum` e defina os membros como atributos.
- **Usando `enum.auto`:**  
  Gera automaticamente valores únicos para os membros da enumeração.
- **Usando `enum.Enum` diretamente:**  
  Enumerações podem ser criadas diretamente com `enum.Enum`.

### 3.4. Acessando Membros e Valores

- **Acessando membros:**  
  - Pelo valor: `Classe(valor)`
  - Pela chave: `Classe['chave']`
- **Obtendo chave e valor:**  
  - Chave: `Classe.chave.name`
  - Valor: `Classe.chave.value`

### 3.5. Exemplo Prático

```py
import enum

class Direcoes(enum.Enum):
    ESQUERDA = enum.auto()
    DIREITA = enum.auto()
    ACIMA = enum.auto()
    ABAIXO = enum.auto()

# Acessando membros e valores
print(Direcoes(1))           # Saída: Direcoes.ESQUERDA
print(Direcoes['DIREITA'])   # Saída: Direcoes.DIREITA
print(Direcoes.ESQUERDA)     # Saída: Direcoes.ESQUERDA
print(Direcoes.ESQUERDA.name)  # Saída: ESQUERDA
print(Direcoes.ESQUERDA.value) # Saída: 1

# Função que utiliza enumerações
def mover(direcao: Direcoes):
    if not isinstance(direcao, Direcoes):
        raise ValueError('Direção inválida. Use uma direção válida.')

    print(f'Movendo para {direcao.name} ({direcao.value})')

# Testando a função
mover(Direcoes.ESQUERDA)  # Saída: Movendo para ESQUERDA (1)
mover(Direcoes.DIREITA)   # Saída: Movendo para DIREITA (2)
mover(Direcoes.ACIMA)     # Saída: Movendo para ACIMA (3)
mover(Direcoes.ABAIXO)    # Saída: Movendo para ABAIXO (4)
```

**Explicação:**
1. **Definição da enumeração:**  
   A classe `Direcoes` define quatro direções (`ESQUERDA`, `DIREITA`, `ACIMA`, `ABAIXO`) usando `enum.auto` para gerar valores únicos automaticamente.
2. **Acessando membros:**  
   Os membros podem ser acessados pelo valor (`Direcoes(1)`) ou pela chave (`Direcoes['DIREITA']`).
3. **Função `mover`:**  
   A função verifica se o argumento é uma instância de `Direcoes` e imprime a direção escolhida.

### 3.6. Dicas e Boas Práticas

- **Use `enum.auto` para valores automáticos:**  
  Simplifica a definição de valores únicos para os membros.
- **Valide entradas com `isinstance`:**  
  Certifique-se de que os argumentos são membros da enumeração.
- **Documente suas enumerações:**  
  Explique o propósito de cada membro e como usá-los.
- **Evite alterar membros:**  
  Enumerações são constantes e não devem ser modificadas após a definição.
- **Itere sobre enumerações:**  
  Use `for` para iterar sobre os membros de uma enumeração, se necessário.

**Resumo:**  
Enumerações (`enum.Enum`) são úteis para representar conjuntos fixos de valores simbólicos em Python. Elas oferecem uma maneira clara e segura de trabalhar com opções limitadas, promovendo consistência e legibilidade no código.

---

## 4. Dataclasses - O Que São?

### 4.1. O Que São Dataclasses?

- **Dataclasses** são uma forma simplificada de criar classes em Python, com métodos como `__init__`, `__repr__`, `__eq__` e outros gerados automaticamente.
- Elas foram introduzidas na **PEP 557** e adicionadas ao Python na versão **3.7**.
- São úteis para classes que armazenam dados, eliminando a necessidade de escrever boilerplate code.

**Documentação oficial:**  
[https://docs.python.org/3/library/dataclasses.html](https://docs.python.org/3/library/dataclasses.html)

### 4.2. Por Que Usar Dataclasses?

- **Redução de código repetitivo:**  
  Não é necessário escrever manualmente métodos como `__init__` ou `__repr__`.
- **Facilidade de uso:**  
  Permite definir valores padrão e usar funções auxiliares como `asdict` e `astuple`.
- **Flexibilidade:**  
  Suporta configurações avançadas com o uso de `field`.

### 4.3. Métodos Especiais: `__init__` e `__post_init__`

#### O Que é o Método `__init__`?

- O método `__init__` é gerado automaticamente pelo decorador `@dataclass`.
- Ele inicializa os atributos da classe com os valores fornecidos ou com os valores padrão.

#### O Que é o Método `__post_init__`?

- O método `__post_init__` é chamado automaticamente após o `__init__`.
- É útil para realizar validações ou inicializações adicionais.

**Exemplo:**
```py
@dataclass
class Pessoa:
    nome: str
    sobrenome: str

    def __post_init__(self):
        self.nome_completo = f'{self.nome} {self.sobrenome}'
```

### 4.4. Configurações do Decorador `@dataclass`

- **`repr=True`:**  
  Gera automaticamente o método `__repr__`.
- **`eq=True`:**  
  Gera automaticamente o método `__eq__`.
- **`order=True`:**  
  Gera métodos de comparação (`<`, `<=`, `>`, `>=`).
- **`frozen=True`:**  
  Torna a classe imutável (os atributos não podem ser alterados após a criação).

### 4.5. Funções Auxiliares: `asdict` e `astuple`

- **`asdict`:**  
  Converte a instância da dataclass em um dicionário.
- **`astuple`:**  
  Converte a instância da dataclass em uma tupla.

**Exemplo:**
```py
from dataclasses import asdict, astuple

@dataclass
class Pessoa:
    nome: str
    sobrenome: str

p = Pessoa('João', 'Silva')
print(asdict(p))   # Saída: {'nome': 'João', 'sobrenome': 'Silva'}
print(astuple(p))  # Saída: ('João', 'Silva')
```

### 4.6. Valores Padrão, `field` e `fields`

- **Valores padrão:**  
  Atributos podem ter valores padrão definidos diretamente ou usando `field`.
- **`field`:**  
  Permite configurações avançadas, como `default_factory` para criar valores padrão dinâmicos.
- **`fields`:**  
  Retorna informações sobre os campos da dataclass.

**Exemplo:**
```py
from dataclasses import dataclass, field, fields

@dataclass
class Pessoa:
    nome: str = 'MISSING'
    sobrenome: str = 'Not sent'
    idade: int = 100
    enderecos: list[str] = field(default_factory=list)

p = Pessoa()
print(fields(p))  # Exibe informações sobre os campos da dataclass.
```

### 4.7. Exemplo Prático

```py
from dataclasses import dataclass, asdict, astuple, field, fields

@dataclass(repr=True)
class Pessoa:
    nome: str = field(default='MISSING', repr=False)
    sobrenome: str = 'Not sent'
    idade: int = 100
    enderecos: list[str] = field(default_factory=list)

    def __post_init__(self):
        self.nome_completo = f'{self.nome} {self.sobrenome}'

if __name__ == '__main__':
    p1 = Pessoa()
    print(p1)  # Saída: Pessoa(sobrenome='Not sent', idade=100, enderecos=[])
    print(asdict(p1))  # Converte para dicionário.
    print(astuple(p1))  # Converte para tupla.
```

### 4.8. Dicas e Boas Práticas

- **Use dataclasses para classes simples:**  
  Elas são ideais para classes que armazenam dados e não possuem muita lógica.
- **Evite usar dataclasses para lógica complexa:**  
  Para classes com muitos métodos ou lógica, considere usar classes normais.
- **Documente os atributos:**  
  Use type annotations para melhorar a legibilidade e facilitar o uso.
- **Aproveite `field`:**  
  Use `field` para valores padrão dinâmicos ou para configurar atributos específicos.
- **Teste com `asdict` e `astuple`:**  
  Use essas funções para converter instâncias em formatos mais fáceis de manipular.

**Resumo:**  
Dataclasses são uma forma eficiente e simplificada de criar classes em Python. Elas eliminam a necessidade de escrever código repetitivo, oferecem suporte a configurações avançadas e são ideais para classes que armazenam dados.

---

## 5. NamedTuple - Tuplas Imutáveis com Nomes para Valores

### 5.1. O Que São NamedTuples?

- **NamedTuples** são uma forma de criar objetos semelhantes a tuplas, mas com nomes para os valores (atributos).
- Elas são úteis para representar registros ou agrupamentos de atributos, como classes simples sem métodos.
- NamedTuples são **imutáveis**, assim como tuplas normais.

**Documentação oficial:**  
- [collections.namedtuple](https://docs.python.org/3/library/collections.html#collections.namedtuple)  
- [typing.NamedTuple](https://docs.python.org/3/library/typing.html#typing.NamedTuple)

### 5.2. Por Que Usar NamedTuples?

- **Clareza e legibilidade:**  
  Os valores podem ser acessados por nome, tornando o código mais legível.
- **Imutabilidade:**  
  Garantem que os valores não sejam alterados após a criação.
- **Compatibilidade com tuplas:**  
  NamedTuples podem ser usadas como tuplas normais (indexação, iteração, etc.).
- **Facilidade de uso:**  
  São ideais para representar registros ou objetos simples.

### 5.3. Características das NamedTuples

- **Imutáveis:**  
  Os valores não podem ser alterados após a criação.
- **Acesso por nome ou índice:**  
  Os valores podem ser acessados como atributos ou por indexação.
- **Métodos úteis:**  
  - `_fields`: Retorna os nomes dos campos.
  - `_field_defaults`: Retorna os valores padrão dos campos.
  - `_asdict()`: Converte a NamedTuple em um dicionário.
- **Compatibilidade com tuplas:**  
  Podem ser iteradas ou usadas como tuplas normais.

### 5.4. Exemplo Prático

#### Usando `typing.NamedTuple`

```py
from typing import NamedTuple

class Carta(NamedTuple):
    valor: str = 'VALOR'
    naipe: str = 'NAIPE'

# Criando uma instância
as_espadas = Carta('A')

# Acessando valores
print(as_espadas.valor)  # Saída: A
print(as_espadas.naipe)  # Saída: NAIPE

# Convertendo para dicionário
print(as_espadas._asdict())  # Saída: {'valor': 'A', 'naipe': 'NAIPE'}

# Iterando sobre os valores
for valor in as_espadas:
    print(valor)  # Saída: A \n NAIPE

# Obtendo informações sobre os campos
print(as_espadas._fields)         # Saída: ('valor', 'naipe')
print(as_espadas._field_defaults) # Saída: {'valor': 'VALOR', 'naipe': 'NAIPE'}
```

#### Usando `collections.namedtuple`

```py
from collections import namedtuple

Carta = namedtuple(
    'Carta', ['valor', 'naipe'],
    defaults=['VALOR', 'NAIPE']
)

# Criando uma instância
as_espadas = Carta('A')

# Acessando valores
print(as_espadas.valor)  # Saída: A
print(as_espadas.naipe)  # Saída: NAIPE

# Convertendo para dicionário
print(as_espadas._asdict())  # Saída: {'valor': 'A', 'naipe': 'NAIPE'}

# Iterando sobre os valores
for valor in as_espadas:
    print(valor)  # Saída: A \n NAIPE

# Obtendo informações sobre os campos
print(as_espadas._fields)         # Saída: ('valor', 'naipe')
print(as_espadas._field_defaults) # Saída: {'valor': 'VALOR', 'naipe': 'NAIPE'}
```

### 5.5. Dicas e Boas Práticas

- **Escolha entre `NamedTuple` e `namedtuple`:**
  - Use `typing.NamedTuple` para aproveitar as vantagens de type annotations.
  - Use `collections.namedtuple` para casos mais simples ou compatibilidade com versões antigas do Python.
- **Documente os campos:**  
  Explique o propósito de cada campo na NamedTuple.
- **Evite lógica complexa:**  
  NamedTuples são ideais para representar dados simples. Para lógica complexa, use classes normais.
- **Use `_asdict()` para manipulação:**  
  Converta NamedTuples em dicionários para facilitar a manipulação dos dados.
- **Aproveite valores padrão:**  
  Defina valores padrão para os campos, quando necessário.

**Resumo:**  
NamedTuples são uma forma eficiente e legível de representar registros ou agrupamentos de atributos em Python. Elas combinam a imutabilidade das tuplas com a clareza de acesso por nomes, tornando-as ideais para dados simples e estruturados.

---

## 6. Criando Sua Própria Lista com Iterable, Iterator e Sequence

### 6.1. O Que São Iterable, Iterator e Sequence?

- **Iterable:**  
  Um objeto que pode ser iterado (ex.: listas, strings, dicionários). Deve implementar o método `__iter__`, que retorna um `Iterator`.
- **Iterator:**  
  Um objeto que sabe como iterar sobre os elementos de um `Iterable`. Deve implementar os métodos `__iter__` e `__next__`.
- **Sequence:**  
  Um tipo de `Iterable` que suporta acesso por índice (`__getitem__`) e tem um tamanho definido (`__len__`).

**Documentação oficial:**  
[https://docs.python.org/3/library/collections.abc.html](https://docs.python.org/3/library/collections.abc.html)

### 6.2. Por Que Implementar Protocolos?

- **Flexibilidade:**  
  Permite criar estruturas de dados personalizadas que se comportam como listas, dicionários ou outros tipos.
- **Compatibilidade:**  
  Objetos que implementam esses protocolos podem ser usados com funções e estruturas padrão do Python (ex.: `for`, `len`, indexação).
- **Reutilização:**  
  Seguir os protocolos facilita a integração com bibliotecas e frameworks.

### 6.3. Protocolo Sequence

- **Métodos obrigatórios:**  
  - `__getitem__(self, index)`: Retorna o item no índice especificado.
  - `__len__(self)`: Retorna o número de itens na sequência.
- **Métodos opcionais:**  
  - `__setitem__(self, index, value)`: Define o valor no índice especificado.
  - Outros métodos como `__contains__` podem ser implementados para funcionalidades adicionais.

### 6.4. Protocolo Iterator

- **Métodos obrigatórios:**  
  - `__iter__(self)`: Retorna o próprio objeto (que é um `Iterator`).
  - `__next__(self)`: Retorna o próximo item na sequência ou levanta `StopIteration` quando não há mais itens.

### 6.5. Exemplo Prático

```py
from collections.abc import Iterable, Iterator, Sequence

class MyList(Sequence):
    def __init__(self):
        self._data = {}
        self._index = 0
        self._next_index = 0

    def append(self, *values):
        for value in values:
            self._data[self._index] = value
            self._index += 1

    def __len__(self) -> int:
        return self._index
    
    def __getitem__(self, index):
        return self._data[index]
    
    def __setitem__(self, index, value):
        self._data[index] = value
    
    def __iter__(self):
        return self
    
    def __next__(self):
        if self._next_index >= self._index:
            self._next_index = 0
            raise StopIteration

        value = self._data[self._next_index]
        self._next_index += 1
        return value

if __name__ == '__main__':
    lista = MyList()
    lista.append('Maria', 'Helena')
    lista[0] = 'João'
    lista.append('Luiz')

    # Iterando sobre os itens
    for item in lista:
        print(item)
    print('---')

    # Iterando novamente
    for item in lista:
        print(item)
```

**Explicação:**
1. **Classe `MyList`:**
   - Implementa o protocolo `Sequence`, permitindo acesso por índice e uso de `len`.
   - Implementa o protocolo `Iterator`, permitindo iteração com `for`.
2. **Método `append`:**
   - Adiciona valores à lista personalizada.
3. **Método `__getitem__`:**
   - Permite acessar itens por índice (`lista[0]`).
4. **Método `__setitem__`:**
   - Permite modificar itens por índice (`lista[0] = 'João'`).
5. **Método `__iter__`:**
   - Retorna o próprio objeto como um `Iterator`.
6. **Método `__next__`:**
   - Retorna o próximo item na sequência ou levanta `StopIteration` quando não há mais itens.

### 6.6. Dicas e Boas Práticas

- **Implemente apenas o necessário:**  
  Não é obrigatório implementar todos os métodos de um protocolo. Foque nos métodos que atendem às suas necessidades.
- **Use `collections.abc`:**  
  Herde de classes como `Sequence` ou `Iterable` para garantir que sua implementação siga os protocolos corretamente.
- **Valide índices:**  
  Certifique-se de que os índices usados em `__getitem__` e `__setitem__` sejam válidos.
- **Levante `StopIteration` corretamente:**  
  Sempre levante `StopIteration` no método `__next__` quando não houver mais itens.
- **Teste sua implementação:**  
  Certifique-se de que sua classe funciona com estruturas padrão do Python, como `for`, `len` e indexação.

**Resumo:**  
Implementar os protocolos `Iterable`, `Iterator` e `Sequence` permite criar estruturas de dados personalizadas que se comportam como listas ou outras coleções padrão do Python. Isso promove flexibilidade, compatibilidade e reutilização de código.

---