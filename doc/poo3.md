# POO 3

## Sumário

1. [Herança Simples - Python Orientado a Objetos](#1-herança-simples---python-orientado-a-objetos)
    - 1.1. [O Que é Herança?](#11-o-que-é-herança)
    - 1.2. [Herança vs Composição](#12-herança-vs-composição)
    - 1.3. [Termos Importantes](#13-termos-importantes)
    - 1.4. [Exemplo Prático](#14-exemplo-prático)
    - 1.5. [Dicas e Observações](#15-dicas-e-observações)
2. [super() e a Sobreposição de Membros - Python Orientado a Objetos](#2-super-e-a-sobreposição-de-membros---python-orientado-a-objetos)
    - 2.1. [O Que é super()?](#21-o-que-é-super)
    - 2.2. [Sobreposição (Override) de Métodos e Atributos](#22-sobreposição-override-de-métodos-e-atributos)
    - 2.3. [Exemplo Prático](#23-exemplo-prático)
    - 2.4. [Ordem de Resolução de Métodos (MRO)](#24-ordem-de-resolução-de-métodos-mro)
    - 2.5. [Dicas e Observações](#25-dicas-e-observações)
3. [Herança Múltipla - Python Orientado a Objetos](#3-herança-múltipla---python-orientado-a-objetos)
    - 3.1. [O Que é Herança Múltipla?](#31-o-que-é-herança-múltipla)
    - 3.2. [Herança Simples vs Herança Múltipla](#32-herança-simples-vs-herança-múltipla)
    - 3.3. [Ordem de Resolução de Métodos (MRO)](#33-ordem-de-resolução-de-métodos-mro)
    - 3.4. [Exemplo Prático](#34-exemplo-prático)
    - 3.5. [Dicas e Observações](#35-dicas-e-observações)
4. [Classes Abstratas - Abstract Base Class (abc)](#4-classes-abstratas---abstract-base-class-abc)
    - 4.1. [O Que São Classes Abstratas?](#41-o-que-são-classes-abstratas)
    - 4.2. [@abstractmethod](#42-abstractmethod)
    - 4.3. [Regras das Classes Abstratas](#43-regras-das-classes-abstratas)
    - 4.4. [Exemplo Prático](#44-exemplo-prático)
    - 4.5. [Dicas e Observações](#45-dicas-e-observações)
5. [@abstractmethod para Qualquer Método Decorado (@property, setter, etc.)](#5-abstractmethod-para-qualquer-método-decorado-property-setter-etc)
    - 5.1. [@abstractmethod com @property e setter](#51-abstractmethod-com-property-e-setter)
    - 5.2. [Exemplo Prático](#52-exemplo-prático)
    - 5.3. [Dicas e Observações](#53-dicas-e-observações)
6. [Polimorfismo, Assinatura de Métodos e Liskov Substitution Principle](#6-polimorfismo-assinatura-de-métodos-e-liskov-substitution-principle)
    - 6.1. [O Que é Polimorfismo?](#61-o-que-é-polimorfismo)
    - 6.2. [Assinatura de Métodos](#62-assinatura-de-métodos)
    - 6.3. [Princípio da Substituição de Liskov (L do SOLID)](#63-princípio-da-substituição-de-liskov-l-do-solid)
    - 6.4. [Exemplo Prático](#64-exemplo-prático)
    - 6.5. [Dicas e Observações](#65-dicas-e-observações)
7. [Criando Exceptions em Python Orientado a Objetos](#7-criando-exceptions-em-python-orientado-a-objetos)
    - 7.1. [O Que São Exceções?](#71-o-que-são-exceções)
    - 7.2. [Como Criar Exceções Personalizadas](#72-como-criar-exceções-personalizadas)
    - 7.3. [Levantando e Relançando Exceções](#73-levantando-e-relançando-exceções)
    - 7.4. [Adicionando Notas em Exceções (Python 3.11+)](#74-adicionando-notas-em-exceções-python-311)
    - 7.5. [Exemplo Prático](#75-exemplo-prático)
    - 7.6. [Dicas e Boas Práticas](#76-dicas-e-boas-práticas)

---

## 1. Herança Simples - Python Orientado a Objetos

A **herança** é um dos pilares da Programação Orientada a Objetos. Permite criar novas classes baseadas em outras, reutilizando e estendendo comportamentos.

### 1.1. O Que é Herança?

- Herança é uma relação do tipo **"é um"**.
- Uma classe filha (subclasse) herda atributos e métodos da classe pai (superclasse).
- Permite reutilizar código e criar hierarquias de classes.

### 1.2. Herança vs Composição

- **Herança:** "É um" (ex: Cliente é uma Pessoa)
- **Composição:** "É dono de" (ex: Cliente tem Endereços)
- **Agregação:** "Tem" (ex: Carrinho tem Produtos)
- **Associação:** "Usa" (ex: Escritor usa Ferramenta)

### 1.3. Termos Importantes

- **Superclasse / Classe base / Classe pai:** Classe de onde se herda (ex: `Pessoa`)
- **Subclasse / Classe filha / Classe derivada:** Classe que herda (ex: `Cliente`, `Aluno`)

### 1.4. Exemplo Prático

```py
class Pessoa:
    cpf = '1234'

    def __init__(self, nome, sobrenome):
        self.nome = nome
        self.sobrenome = sobrenome

    def falar_nome_classe(self):
        print('classe PESSOA')
        print(self.nome, self.sobrenome, self.__class__.__name__)

class Cliente(Pessoa):
    def falar_nome_classe(self):
        print('EITA, nem saí da classe CLIENTE')
        print(self.nome, self.sobrenome, self.__class__.__name__)

class Aluno(Pessoa):
    cpf = 'cpf aluno'

c1 = Cliente('Maria', 'Silva')
c1.falar_nome_classe()  # Saída: EITA, nem saí da classe CLIENTE \n Maria Silva Cliente

a1 = Aluno('João', 'Silva')
a1.falar_nome_classe()  # Saída: classe PESSOA \n João Silva Aluno

print(a1.cpf)           # Saída: cpf aluno
```

**Explicação:**
- `Cliente` e `Aluno` herdam de `Pessoa`.
- `Cliente` sobrescreve o método `falar_nome_classe`.
- `Aluno` herda o método, mas sobrescreve o atributo `cpf`.

### 1.5. Dicas e Observações

- Use herança para reaproveitar código e criar hierarquias lógicas.
- Métodos e atributos podem ser sobrescritos nas subclasses.
- Use `super()` para acessar métodos da superclasse, se necessário.
- O atributo especial `__class__.__name__` mostra o nome da classe da instância.

**Resumo:**  
Herança permite criar novas classes baseadas em outras, facilitando a reutilização e a extensão de funcionalidades em Python.

---

## 2. super() e a Sobreposição de Membros - Python Orientado a Objetos

O `super()` é usado para acessar métodos e atributos da superclasse (classe pai) em subclasses, especialmente útil quando há sobreposição (override) de membros.

### 2.1. O Que é super()?

- `super()` retorna um objeto temporário da superclasse, permitindo acessar seus métodos e atributos.
- É muito usado para reutilizar código da classe base em subclasses, principalmente em métodos sobrescritos.

### 2.2. Sobreposição (Override) de Métodos e Atributos

- **Sobreposição** ocorre quando uma subclasse define um método ou atributo com o mesmo nome de sua superclasse.
- O método/atributo da subclasse "esconde" o da superclasse, mas é possível acessar o original usando `super()`.

### 2.3. Exemplo Prático

```py
class A:
    atributo_a = 'valor a'

    def __init__(self, atributo):
        self.atributo = atributo

    def metodo(self):
        print('A')

class B(A):
    atributo_b = 'valor b'

    def __init__(self, atributo, outra_coisa):
        super().__init__(atributo)
        self.outra_coisa = outra_coisa

    def metodo(self):
        print('B')

class C(B):
    atributo_c = 'valor c'

    def __init__(self, *args, **kwargs):
        super().__init__(*args, **kwargs)

    def metodo(self):
        # Chama explicitamente métodos das superclasses
        A.metodo(self)
        B.metodo(self)
        print('C')

c = C('Atributo', 'Qualquer')
c.metodo()
# Saída:
# A
# B
# C
```

**Explicação:**
- Cada classe define (ou sobrescreve) o método `metodo`.
- Em `C.metodo`, chamamos explicitamente os métodos das superclasses antes de imprimir 'C'.
- O `super()` pode ser usado para chamar o método da próxima classe na MRO (Method Resolution Order).

### 2.4. Ordem de Resolução de Métodos (MRO)

- O Python segue a **MRO** para decidir qual método chamar em heranças múltiplas.
- Você pode ver a ordem usando `Classe.mro()`.

```py
print(C.mro())
```

### 2.5. Dicas e Observações

- Use `super()` para evitar duplicação de código e garantir que a cadeia de herança seja respeitada.
- Em herança múltipla, o uso correto de `super()` é fundamental para evitar bugs.
- Métodos e atributos podem ser sobrescritos livremente, mas sempre que precisar do comportamento da superclasse, use `super()`.

**Resumo:**  
O `super()` permite acessar membros da superclasse em subclasses, facilitando a reutilização e extensão de código em hierarquias de herança.

---

## 3. Herança Múltipla - Python Orientado a Objetos

A **herança múltipla** permite que uma classe herde de várias outras classes ao mesmo tempo. Isso pode ser útil para criar classes que combinam comportamentos de diferentes hierarquias.

### 3.1. O Que é Herança Múltipla?

- Uma classe pode estender (herdar de) várias outras classes.
- Permite criar classes que combinam funcionalidades de múltiplas superclasses.
- Exemplo: `Cliente(Pessoa, FileLog)` herda de `Pessoa` e `FileLog`.

### 3.2. Herança Simples vs Herança Múltipla

- **Herança simples:** Uma classe herda de apenas uma superclasse.
  - Exemplo: `Humano(Pessoa)`
- **Herança múltipla:** Uma classe herda de duas ou mais superclasses.
  - Exemplo: `Cliente(Pessoa, FileLog)`

### 3.3. Ordem de Resolução de Métodos (MRO)

- O Python usa o algoritmo **C3 superclass linearization** para determinar a ordem de chamada dos métodos em herança múltipla.
- Para descobrir a ordem, use:
  - `Classe.mro()`
  - Ou o atributo `__mro__`

### 3.4. Exemplo Prático

```py
class A:
    def quem_sou(self):
        print('A')

class B(A):
    pass
    # def quem_sou(self):
    #     print('B')

class C(A):
    def quem_sou(self):
        print('C')

class D(B, C):
    pass
    # def quem_sou(self):
    #     print('D')

d = D()
d.quem_sou()         # Saída: C
print(D.mro())       # Mostra a ordem de resolução de métodos
```

**Explicação:**
- `D` herda de `B` e `C`.
- O método `quem_sou` é chamado de acordo com a ordem MRO.
- Como `C` define `quem_sou`, e `C` aparece antes de `A` na MRO de `D`, o método de `C` é chamado.

### 3.5. Dicas e Observações

- Herança múltipla pode ser poderosa, mas também pode tornar o código mais complexo e difícil de manter.
- Use herança múltipla com cuidado e prefira composição quando possível.
- Mixins são uma forma comum de usar herança múltipla para adicionar funcionalidades específicas a classes.

**Resumo:**  
Herança múltipla permite que uma classe herde de várias superclasses. O Python resolve conflitos de métodos usando a MRO, que pode ser inspecionada com `Classe.mro()`.

---

## 4. Classes Abstratas - Abstract Base Class (abc)

As **classes abstratas** (ABCs) são usadas como contratos para a definição de novas classes. Elas podem forçar subclasses a implementarem métodos específicos, garantindo uma interface comum.

### 4.1. O Que São Classes Abstratas?

- São classes que não podem ser instanciadas diretamente.
- Servem como base para outras classes.
- Podem conter métodos concretos (com implementação) e métodos abstratos (sem implementação).

### 4.2. @abstractmethod

- O decorador `@abstractmethod` marca métodos que devem ser implementados nas subclasses.
- Métodos abstratos não têm corpo (apenas `...` ou `pass`).
- É possível criar propriedades, setters, classmethods e staticmethods abstratos usando `@abstractmethod` como decorador mais interno.

### 4.3. Regras das Classes Abstratas

- Não podem ser instanciadas diretamente se tiverem métodos abstratos.
- Subclasses DEVEM implementar todos os métodos abstratos.
- Usam a metaclasse `ABCMeta` (herdando de `ABC`).

### 4.4. Exemplo Prático

```py
from abc import ABC, abstractmethod

class Log(ABC):
    @abstractmethod
    def _log(self, msg):
        ...

    def log_error(self, msg):
        return self._log(f'Error: {msg}')

    def log_success(self, msg):
        return self._log(f'Success: {msg}')

class LogPrintMixin(Log):
    def _log(self, msg):
        print(f'{msg} ({self.__class__.__name__})')

l = LogPrintMixin()
l.log_error('Oi')  # Saída: Error: Oi (LogPrintMixin)
```

**Explicação:**
- `Log` é uma classe abstrata com um método abstrato `_log`.
- `LogPrintMixin` implementa `_log` e pode ser instanciada normalmente.
- Tentar instanciar `Log` diretamente gera erro.

### 4.5. Dicas e Observações

- Use classes abstratas para definir contratos e interfaces em hierarquias de classes.
- Métodos abstratos garantem que subclasses implementem comportamentos essenciais.
- Classes abstratas podem ter métodos concretos para reutilização de código.
- Para propriedades, setters, classmethods e staticmethods abstratos, use `@abstractmethod` como decorador mais interno.

**Resumo:**  
Classes abstratas são fundamentais para criar contratos e garantir que subclasses implementem métodos essenciais, promovendo padronização e reutilização de código em Python.

---

## 5. @abstractmethod para Qualquer Método Decorado (@property, setter, etc.)

O decorador `@abstractmethod` pode ser usado em conjunto com outros decoradores como `@property`, `@property.setter`, `@classmethod` e `@staticmethod` para criar métodos abstratos de qualquer tipo.

### 5.1. @abstractmethod com @property e setter

- Para criar uma propriedade abstrata, use `@property` seguido de `@abstractmethod`.
- Para criar um setter abstrato, use `@<propriedade>.setter` seguido de `@abstractmethod`.
- Isso força as subclasses a implementarem tanto o getter quanto o setter.

### 5.2. Exemplo Prático

```py
from abc import ABC, abstractmethod

class AbstractFoo(ABC):
    def __init__(self, name):
        self._name = None
        self.name = name

    @property
    def name(self):
        return self._name

    @name.setter
    @abstractmethod
    def name(self, name):
        ...

class Foo(AbstractFoo):
    def __init__(self, name):
        super().__init__(name)

    @AbstractFoo.name.setter
    def name(self, name):
        self._name = name

foo = Foo('Bar')
print(foo.name)  # Saída: Bar
```

**Explicação:**
- `AbstractFoo` define um setter abstrato para a propriedade `name`.
- `Foo` implementa o setter obrigatório.
- Tentar instanciar uma subclasse sem implementar o setter gera erro.

### 5.3. Dicas e Observações

- Sempre coloque `@abstractmethod` como o decorador mais interno.
- Você pode usar `@abstractmethod` com qualquer tipo de método decorado: `@property`, `@classmethod`, `@staticmethod`, etc.
- Foo e Bar são nomes genéricos (placeholders) comuns em exemplos de programação.

**Resumo:**  
É possível criar propriedades, setters, métodos de classe e métodos estáticos abstratos usando `@abstractmethod` como decorador mais interno, forçando a implementação nas subclasses.

---

## 6. Polimorfismo, Assinatura de Métodos e Liskov Substitution Principle

O **polimorfismo** é um dos pilares da Programação Orientada a Objetos (POO). Ele permite que diferentes classes derivadas de uma mesma superclasse implementem métodos com a mesma assinatura, mas com comportamentos distintos. Isso promove flexibilidade e extensibilidade no design de sistemas.

### 6.1. O Que é Polimorfismo?

- **Polimorfismo** significa "muitas formas".
- Ele permite que objetos de diferentes classes sejam tratados como objetos de uma superclasse comum.
- Cada classe derivada pode implementar métodos com comportamentos específicos, respeitando a assinatura definida na superclasse.
- O polimorfismo é amplamente utilizado para criar sistemas que podem ser estendidos sem modificar o código existente.

**Exemplo Conceitual:**
- Uma classe abstrata `Animal` pode ter um método `falar`.
- Classes derivadas como `Cachorro` e `Gato` podem implementar `falar` de maneiras diferentes:
  - `Cachorro.falar()` retorna "Au au".
  - `Gato.falar()` retorna "Miau".

### 6.2. Assinatura de Métodos

- A **assinatura de um método** inclui:
  - O nome do método.
  - A quantidade e os tipos de parâmetros.
- O **tipo de retorno** não faz parte da assinatura em Python.
- Em Python:
  - **Sobrecarga de métodos (overload):** Não é suportada diretamente.
  - **Sobreposição de métodos (override):** É amplamente suportada e usada.

**Exemplo de Assinatura:**
```py
def enviar(self, mensagem: str) -> bool:
    ...
```
- Nome: `enviar`
- Parâmetros: `mensagem` (tipo `str`)
- Retorno: `bool` (não faz parte da assinatura, mas é importante para consistência).

### 6.3. Princípio da Substituição de Liskov (L do SOLID)

- O **Princípio da Substituição de Liskov** afirma que:
  - Objetos de uma superclasse devem ser substituíveis por objetos de suas subclasses sem alterar o comportamento esperado do programa.
- Isso significa que qualquer código que funcione com a superclasse deve funcionar com qualquer subclasse derivada dela.
- É um dos princípios do SOLID, que promove boas práticas de design de software.

**Exemplo:**
- Se uma função aceita um objeto do tipo `Notificacao`, ela deve funcionar corretamente com qualquer subclasse de `Notificacao`, como `NotificacaoEmail` ou `NotificacaoSMS`.

### 6.4. Exemplo Prático

```py
from abc import ABC, abstractmethod

class Notificacao(ABC):
    def __init__(self, mensagem):
        self.mensagem = mensagem

    @abstractmethod
    def enviar(self) -> bool:
        ...

class NotificacaoEmail(Notificacao):
    def enviar(self) -> bool:
        print('Email: enviando - ', self.mensagem)
        return True

class NotificacaoSMS(Notificacao):
    def enviar(self) -> bool:
        print('SMS: enviando - ', self.mensagem)
        return False

def notificar(notificacao: Notificacao):
    notificacao_enviada = notificacao.enviar()

    if notificacao_enviada:
        print('Notificação enviada com sucesso!')
    else:
        print('Erro ao enviar notificação!')

# Criando e enviando notificações
notificacao_email = NotificacaoEmail('Testando email')
notificar(notificacao_email)  # Saída: Email: enviando - Testando email \n Notificação enviada com sucesso!

notificacao_sms = NotificacaoSMS('Testando SMS')
notificar(notificacao_sms)    # Saída: SMS: enviando - Testando SMS \n Erro ao enviar notificação!
```

**Explicação:**
1. `Notificacao` é uma classe abstrata que define o contrato (método `enviar`).
2. `NotificacaoEmail` e `NotificacaoSMS` implementam o método `enviar` com comportamentos específicos.
3. A função `notificar` aceita qualquer objeto que seja uma instância de `Notificacao` ou suas subclasses, respeitando o Princípio da Substituição de Liskov.

### 6.5. Dicas e Observações

- **Polimorfismo:**
  - Use polimorfismo para criar sistemas flexíveis e extensíveis.
  - Ele permite que você adicione novas funcionalidades sem modificar o código existente.
- **Assinatura de Métodos:**
  - Mantenha a assinatura consistente entre a superclasse e as subclasses.
  - Isso garante que o código cliente funcione corretamente com qualquer subclasse.
- **Princípio da Substituição de Liskov:**
  - Certifique-se de que as subclasses respeitem o contrato definido pela superclasse.
  - Evite alterar o comportamento esperado ao sobrescrever métodos.
- **Sobrecarga vs Sobreposição:**
  - Python não suporta sobrecarga de métodos diretamente.
  - Prefira sobreposição (override) para redefinir o comportamento de métodos em subclasses.

**Resumo:**  
O polimorfismo permite que diferentes classes derivadas de uma mesma superclasse compartilhem métodos com a mesma assinatura, mas comportamentos distintos. Isso, aliado ao Princípio da Substituição de Liskov, garante flexibilidade, extensibilidade e robustez em sistemas orientados a objetos.

---

## 7. Criando Exceptions em Python Orientado a Objetos

Em Python, é possível criar exceções personalizadas para lidar com erros específicos de forma mais clara e organizada. Isso é feito herdando de uma classe de exceção existente, geralmente `Exception`.

### 7.1. O Que São Exceções?

- **Exceções** são eventos que interrompem o fluxo normal de execução de um programa.
- Elas são usadas para lidar com erros ou situações inesperadas.
- Python possui várias exceções embutidas, como `ValueError`, `TypeError`, `ZeroDivisionError`, etc.

### 7.2. Como Criar Exceções Personalizadas

- Para criar uma exceção personalizada, herde de uma classe de exceção existente, preferencialmente `Exception`.
- É comum adicionar "Error" ao final do nome da classe para indicar que se trata de uma exceção.

```py
class MeuError(Exception):
    pass

class OutroError(Exception):
    pass
```

### 7.3. Levantando e Relançando Exceções

- Use `raise` para levantar (lançar) uma exceção.
- Use `raise ... from ...` para relançar uma exceção, preservando o contexto da original.

```py
raise MeuError('Mensagem de erro')
```

### 7.4. Adicionando Notas em Exceções (Python 3.11+)

- A partir do Python 3.11, é possível adicionar **notas** a exceções usando o método `add_note`.
- As notas são armazenadas no atributo `__notes__` e podem ser usadas para fornecer informações adicionais sobre o erro.

```py
exception_ = MeuError('Erro ocorrido')
exception_.add_note('Nota adicional 1')
exception_.add_note('Nota adicional 2')
```

### 7.5. Exemplo Prático

```py
class MeuError(Exception):
    pass

class OutroError(Exception):
    pass

def levantar():
    exception_ = MeuError('a', 'b', 'c')
    exception_.add_note('Olha a nota 1')
    exception_.add_note('Você errou isso')
    raise exception_

try:
    levantar()
except (MeuError, ZeroDivisionError) as error:
    print(error.__class__.__name__)  # Nome da exceção
    print(error.args)               # Argumentos passados
    exception_ = OutroError('Vou lançar de novo')
    exception_.__notes__ += error.__notes__.copy()  # Copiando notas
    exception_.add_note('Mais uma nova')
    raise exception_ from error
```

**Saída esperada:**
```
MeuError
('a', 'b', 'c')
Traceback (most recent call last):
  ...
OutroError: Vou lançar de novo
```

### 7.6. Dicas e Boas Práticas

- **Herdar de `Exception`:** Sempre herde de `Exception` ou suas subclasses, a menos que tenha um motivo específico para não fazê-lo.
- **Nomes descritivos:** Use nomes claros e descritivos para suas exceções, terminando com "Error".
- **Adicione notas:** Use `add_note` (Python 3.11+) para fornecer informações adicionais sobre o erro.
- **Relance exceções:** Use `raise ... from ...` para preservar o contexto da exceção original ao relançar.

**Resumo:**  
Criar exceções personalizadas em Python permite lidar com erros de forma mais específica e organizada. Com o suporte a notas em exceções no Python 3.11+, é possível adicionar informações adicionais para facilitar o rastreamento e a depuração de erros.

---