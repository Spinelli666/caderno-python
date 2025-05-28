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