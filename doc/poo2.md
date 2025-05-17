# POO 2

## Sumário

1. [Métodos de Classe (@classmethod) e Factory Methods (Métodos Fábrica)](#1-métodos-de-classe-classmethod-e-factory-methods-métodos-fábrica)
    - 1.1. [O Que São Métodos de Classe?](#11-o-que-são-métodos-de-classe)
    - 1.2. [Como Definir um Método de Classe](#12-como-definir-um-método-de-classe)
    - 1.3. [Factory Methods (Métodos Fábrica)](#13-factory-methods-métodos-fábrica)
    - 1.4. [Exemplo Prático](#14-exemplo-prático)
    - 1.5. [Dicas e Boas Práticas](#15-dicas-e-boas-práticas)
2. [@staticmethod (Métodos Estáticos) em Python](#2-staticmethod-métodos-estáticos-em-python)
    - 2.1. [O Que São Métodos Estáticos?](#21-o-que-são-métodos-estáticos)
    - 2.2. [Quando Usar Métodos Estáticos?](#22-quando-usar-métodos-estáticos)
    - 2.3. [Exemplo Prático](#23-exemplo-prático)
    - 2.4. [Comparação com Funções Comuns](#24-comparação-com-funções-comuns)
    - 2.5. [Dicas e Observações](#25-dicas-e-observações)
3. [method vs @classmethod vs @staticmethod](#3-method-vs-classmethod-vs-staticmethod)
    - 3.1. [Método de Instância (`self`)](#31-método-de-instância-self)
    - 3.2. [Método de Classe (`@classmethod` / `cls`)](#32-método-de-classe-classmethod--cls)
    - 3.3. [Método Estático (`@staticmethod`)](#33-método-estático-staticmethod)
    - 3.4. [Exemplo Prático](#34-exemplo-prático)
    - 3.5. [Resumo e Dicas](#35-resumo-e-dicas)
4. [@property - Um Getter no Modo Pythônico](#4-property---um-getter-no-modo-pythonico)
    - 4.1. [O Que é um Getter?](#41-o-que-é-um-getter)
    - 4.2. [O Que é o Decorador @property?](#42-o-que-é-o-decorador-property)
    - 4.3. [Vantagens do @property](#43-vantagens-do-property)
    - 4.4. [Exemplo Prático](#44-exemplo-prático)
    - 4.5. [Comparação com Getters Tradicionais](#45-comparação-com-getters-tradicionais)
    - 4.6. [Dicas e Boas Práticas](#46-dicas-e-boas-práticas)
5. [@property + @setter - Getter e Setter no Modo Pythônico](#5-property--setter---getter-e-setter-no-modo-pythonico)
    - 5.1. [O Que São Getter e Setter?](#51-o-que-são-getter-e-setter)
    - 5.2. [Como Usar @property e @setter](#52-como-usar-property-e-setter)
    - 5.3. [Exemplo Prático](#53-exemplo-prático)
    - 5.4. [Vantagens do Uso Pythônico](#54-vantagens-do-uso-pythonico)
    - 5.5. [Dicas e Boas Práticas](#55-dicas-e-boas-práticas)
6. [Encapsulamento (Modificadores de Acesso: public, _protected, __private)](#6-encapsulamento-modificadores-de-acesso-public-_protected-__private)
    - 6.1. [Encapsulamento em Python](#61-encapsulamento-em-python)
    - 6.2. [Convenções de Modificadores de Acesso](#62-convenções-de-modificadores-de-acesso)
    - 6.3. [Name Mangling (Desfiguração de Nomes)](#63-name-mangling-desfiguração-de-nomes)
    - 6.4. [Exemplo Prático](#64-exemplo-prático)
    - 6.5. [Dicas e Boas Práticas](#65-dicas-e-boas-práticas)
7. [Relações entre Classes: Associação, Agregação e Composição](#7-relações-entre-classes-associação-agregação-e-composição)
    - 7.1. [O Que é Associação?](#71-o-que-é-associação)
    - 7.2. [Exemplo Prático de Associação](#72-exemplo-prático-de-associação)
    - 7.3. [Agregação e Composição (Introdução)](#73-agregação-e-composição-introdução)
    - 7.4. [Dicas e Observações](#74-dicas-e-observações)
8. [Agregação - Python Orientado a Objetos](#8-agregação---python-orientado-a-objetos)
    - 8.1. [O Que é Agregação?](#81-o-que-é-agregação)
    - 8.2. [Diferença entre Associação e Agregação](#82-diferença-entre-associação-e-agregação)
    - 8.3. [Exemplo Prático de Agregação](#83-exemplo-prático-de-agregação)
    - 8.4. [Dicas e Observações](#84-dicas-e-observações)
9. [Composição - Python Orientado a Objeto](#9-composição---python-orientado-a-objeto)
    - 9.1. [O Que é Composição?](#91-o-que-é-composição)
    - 9.2. [Diferença entre Agregação e Composição](#92-diferença-entre-agregação-e-composição)
    - 9.3. [Exemplo Prático de Composição](#93-exemplo-prático-de-composição)
    - 9.4. [Dicas e Observações](#94-dicas-e-observações)

---

## 1. Métodos de Classe (@classmethod) e Factory Methods (Métodos Fábrica)

Os **métodos de classe** são métodos que recebem a própria classe como primeiro argumento, em vez da instância. Eles são úteis para criar métodos utilitários ou **factory methods** (métodos fábrica), que retornam novas instâncias da classe de formas diferentes.

### 1.1. O Que São Métodos de Classe?

- São métodos que recebem a classe (`cls`) como primeiro parâmetro, em vez da instância (`self`).
- São definidos com o decorador `@classmethod`.
- Permitem acessar e modificar atributos de classe e criar instâncias de formas alternativas.

### 1.2. Como Definir um Método de Classe

- Use o decorador `@classmethod`.
- O primeiro parâmetro deve ser `cls` (por convenção).

```py
class MinhaClasse:
    @classmethod
    def meu_metodo_de_classe(cls, ...):
        ...
```

### 1.3. Factory Methods (Métodos Fábrica)

- São métodos de classe que retornam novas instâncias da classe.
- Permitem criar objetos com parâmetros ou lógicas diferentes do construtor padrão.

### 1.4. Exemplo Prático

```py
class Pessoa:
    ano = 2023  # atributo de classe

    def __init__(self, nome, idade):
        self.nome = nome
        self.idade = idade

    @classmethod
    def metodo_de_classe(cls):
        print('Hey!')

    @classmethod
    def criar_com_50_anos(cls, nome):
        return cls(nome, 50)

    @classmethod
    def criar_sem_nome(cls, idade):
        return cls('Anônima', idade)

p1 = Pessoa('João', 33)
p2 = Pessoa.criar_com_50_anos('Helena')
p3 = Pessoa('Anônima', 23)
p4 = Pessoa.criar_sem_nome(25)

print(p2.nome, p2.idade)  # Saída: Helena 50
print(p3.nome, p3.idade)  # Saída: Anônima 23
print(p4.nome, p4.idade)  # Saída: Anônima 25

# print(Pessoa.ano)
# Pessoa.metodo_de_classe()
```

**Explicação:**
- `criar_com_50_anos` e `criar_sem_nome` são métodos fábrica que retornam novas instâncias de `Pessoa` com valores pré-definidos.
- O método `metodo_de_classe` pode ser chamado diretamente pela classe.

### 1.5. Dicas e Boas Práticas

- Use métodos de classe para criar diferentes formas de instanciar objetos.
- Prefira métodos de classe quando precisar acessar ou modificar atributos de classe.
- Factory methods facilitam a criação de objetos com configurações padrão ou alternativas.

---

## 2. @staticmethod (Métodos Estáticos) em Python

O decorador **@staticmethod** transforma um método em um método estático, ou seja, um método que não recebe nem a instância (`self`) nem a classe (`cls`) como primeiro argumento. Ele funciona como uma função comum, mas está "dentro" da classe.

### 2.1. O Que São Métodos Estáticos?

- Métodos definidos com `@staticmethod` não têm acesso à instância (`self`) nem à classe (`cls`).
- São, na prática, funções comuns agrupadas dentro da classe por organização ou contexto.

### 2.2. Quando Usar Métodos Estáticos?

- Quando a função não precisa acessar nem modificar atributos da instância ou da classe.
- Para agrupar funções relacionadas logicamente à classe, mas que não dependem do estado do objeto ou da classe.

### 2.3. Exemplo Prático

```py
class Classe:
    @staticmethod
    def funcao_que_esta_na_classe(*args, **kwargs):
        print('oi', args, kwargs)

def funcao(*args, **kwargs):
    print('oi', args, kwargs)

c1 = Classe()
c1.funcao_que_esta_na_classe(1, 2, 3)         # oi (1, 2, 3) {}
funcao(1, 2, 3)                               # oi (1, 2, 3) {}
Classe.funcao_que_esta_na_classe(nomeado=1)   # oi () {'nomeado': 1}
funcao(nomeado=1)                             # oi () {'nomeado': 1}
```

### 2.4. Comparação com Funções Comuns

- Métodos estáticos são praticamente iguais a funções comuns, mas ficam dentro do escopo da classe.
- Não têm acesso ao estado da instância nem da classe.

### 2.5. Dicas e Observações

- Métodos estáticos são raramente necessários em Python, pois funções comuns já cumprem o papel.
- Use apenas se fizer sentido organizacional ou para manter a função agrupada à classe por contexto.
- Se precisar acessar a classe, prefira `@classmethod`. Se precisar acessar a instância, use métodos normais.

**Resumo:**  
Métodos estáticos em Python são funções comuns dentro da classe, sem acesso a `self` ou `cls`. Use apenas se fizer sentido para a organização do seu código.

---

## 3. method vs @classmethod vs @staticmethod

Em Python, métodos podem ser definidos de três formas principais dentro de uma classe: métodos de instância, métodos de classe e métodos estáticos. Cada um tem um propósito e comportamento diferente.

### 3.1. Método de Instância (`self`)

- Recebe a instância como primeiro argumento (`self`).
- Pode acessar e modificar atributos da instância.
- É o tipo padrão de método em uma classe.

### 3.2. Método de Classe (`@classmethod` / `cls`)

- Recebe a classe como primeiro argumento (`cls`).
- Pode acessar e modificar atributos da classe.
- Útil para criar métodos fábrica ou utilitários relacionados à classe.

### 3.3. Método Estático (`@staticmethod`)

- Não recebe nem a instância (`self`) nem a classe (`cls`).
- Funciona como uma função comum, mas está agrupada dentro da classe por organização.

### 3.4. Exemplo Prático

```py
class Connection:
    def __init__(self, host='localhost'):
        self.host = host
        self.user = None
        self.password = None

    def set_user(self, user):
        self.user = user

    def set_password(self, password):
        self.password = password

    @classmethod
    def create_with_auth(cls, user, password):
        connection = cls()
        connection.user = user
        connection.password = password
        return connection

    @staticmethod
    def log(msg):
        print('LOG:', msg)

def connection_log(msg):
    print('LOG:', msg)

# Criando uma conexão usando o método de classe (factory)
c1 = Connection.create_with_auth('Lucas', '542')

# Usando o método estático
Connection.log('Essa é a mensagem de log')  # LOG: Essa é a mensagem de log

print(c1.user)      # Saída: Lucas
print(c1.password)  # Saída: 542
```

### 3.5. Resumo e Dicas

- **Método de instância:** Usa `self`, manipula dados do objeto.
- **Método de classe:** Usa `cls`, manipula dados da classe ou cria instâncias de formas alternativas.
- **Método estático:** Não usa `self` nem `cls`, é apenas uma função agrupada na classe.

**Dicas:**
- Use métodos de instância para comportamentos ligados ao objeto.
- Use métodos de classe para criar instâncias ou acessar/modificar atributos de classe.
- Use métodos estáticos para funções utilitárias relacionadas à classe, mas que não precisam de acesso à instância ou à classe.

---

## 4. @property - Um Getter no Modo Pythônico

O decorador **@property** permite criar métodos que se comportam como atributos. É a forma pythônica de criar getters, setters e deleters, tornando o acesso a atributos mais elegante e seguro.

### 4.1. O Que é um Getter?

- Um **getter** é um método usado para obter o valor de um atributo de um objeto.
- Em outras linguagens, é comum usar métodos como `get_cor()`, mas em Python preferimos o acesso direto ao atributo.

### 4.2. O Que é o Decorador @property?

- O **@property** transforma um método em uma propriedade de leitura (getter).
- Permite acessar o método como se fosse um atributo, sem parênteses.

### 4.3. Vantagens do @property

- Permite alterar a implementação interna sem quebrar o código cliente.
- Permite executar ações ao acessar um atributo.
- Facilita a criação de setters e deleters de forma elegante.

### 4.4. Exemplo Prático

```py
class Caneta:
    def __init__(self, cor):
        self.cor_tinta = cor

    @property
    def cor(self):
        print('PROPERTY')
        return self.cor_tinta

    @property
    def cor_tampa(self):
        return 123456

caneta = Caneta('Azul')
print(caneta.cor)        # PROPERTY \n Azul
print(caneta.cor)        # PROPERTY \n Azul
print(caneta.cor_tampa)  # 123456
```

### 4.5. Comparação com Getters Tradicionais

**Modo tradicional (menos pythônico):**
```py
class Caneta:
    def __init__(self, cor):
        self.cor_tinta = cor

    def get_cor(self):
        print('GET COR')
        return self.cor_tinta

caneta = Caneta('Azul')
print(caneta.get_cor())  # GET COR \n Azul
```

**Modo pythônico (com @property):**
```py
print(caneta.cor)  # PROPERTY \n Azul
```

### 4.6. Dicas e Boas Práticas

- Use `@property` para criar interfaces de acesso a atributos que podem mudar de implementação sem afetar o código cliente.
- Use `@property` para validar, calcular ou registrar acessos a atributos.
- Para criar setters, use `@<nome>.setter`.

**Resumo:**  
O decorador `@property` permite criar métodos que se comportam como atributos, tornando o código mais limpo, seguro e pythônico.

---

## 5. @property + @setter - Getter e Setter no Modo Pythônico

O uso combinado de `@property` e `@<propriedade>.setter` permite criar getters e setters de forma elegante e segura em Python, sem quebrar o código cliente.

### 5.1. O Que São Getter e Setter?

- **Getter:** Método para obter o valor de um atributo.
- **Setter:** Método para definir/modificar o valor de um atributo.
- Em Python, usamos `@property` para o getter e `@<propriedade>.setter` para o setter.

### 5.2. Como Usar @property e @setter

- Defina o método getter com `@property`.
- Defina o método setter com `@<propriedade>.setter`.
- Use atributos "protegidos" (com underline) para armazenar os valores internamente.

### 5.3. Exemplo Prático

```py
class Caneta:
    def __init__(self, cor):
        self.cor = cor
        self._cor_tampa = None

    @property
    def cor(self):
        print('ESTOU NO GETTER')
        return self._cor

    @cor.setter
    def cor(self, valor):
        print('ESTOU NO SETTER')
        self._cor = valor

    @property
    def cor_tampa(self):
        return self._cor_tampa

    @cor_tampa.setter
    def cor_tampa(self, valor):
        self._cor_tampa = valor

caneta = Caneta('Azul')
caneta.cor = 'Rosa'         # Chama o setter
caneta.cor_tampa = 'Azul'   # Chama o setter
print(caneta.cor)           # Chama o getter
print(caneta.cor_tampa)     # Chama o getter
```

**Saída esperada:**
```
ESTOU NO SETTER
ESTOU NO SETTER
ESTOU NO GETTER
Rosa
Azul
```

### 5.4. Vantagens do Uso Pythônico

- Permite alterar a implementação interna sem quebrar o código cliente.
- Facilita validações, logs ou outras ações ao acessar ou modificar atributos.
- Mantém a sintaxe de acesso simples, como se fossem atributos comuns.

### 5.5. Dicas e Boas Práticas

- Use atributos com underline (`_atributo`) para indicar que são "protegidos" e não devem ser acessados diretamente fora da classe.
- Use `@property` e `@setter` para controlar o acesso e a modificação de atributos importantes.
- Evite expor atributos sensíveis diretamente.

**Resumo:**  
O uso de `@property` e `@setter` é a forma pythônica de criar getters e setters, mantendo o código limpo, seguro e flexível.

---

## 6. Encapsulamento (Modificadores de Acesso: public, _protected, __private)

O **encapsulamento** é um dos pilares da Programação Orientada a Objetos. Em Python, não existem modificadores de acesso como em outras linguagens, mas há convenções para indicar o nível de acesso dos atributos e métodos.

### 6.1. Encapsulamento em Python

- **Encapsulamento** significa esconder detalhes internos de uma classe, expondo apenas o necessário.
- Em Python, o controle de acesso é feito por **convenção**, não por restrição da linguagem.

### 6.2. Convenções de Modificadores de Acesso

- **Público (public):**  
  - Sem underline (`self.atributo`)
  - Pode ser acessado de qualquer lugar.
- **Protegido (protected):**  
  - Um underline (`self._atributo`)
  - Não deve ser acessado fora da classe ou de subclasses.
- **Privado (private):**  
  - Dois underlines (`self.__atributo`)
  - Só deve ser acessado dentro da própria classe.
  - O Python faz "name mangling" para dificultar o acesso externo.

### 6.3. Name Mangling (Desfiguração de Nomes)

- Atributos ou métodos com dois underlines (`__`) têm seus nomes alterados internamente para `_NomeClasse__nome`.
- Isso dificulta, mas não impede, o acesso externo.

### 6.4. Exemplo Prático

```py
class Foo:
    def __init__(self):
        self.public = 'isso é público'
        self._protected = 'isso é protegido'
        self.__exemplo = 'isso é privado'

    def metodo_publico(self):
        print(self.__exemplo)
        self.__metodo_private()
        return 'metodo_publico'
    
    def _metodo_protected(self):
        print('_metodo_protected')
        return '_metodo_protected'

    def __metodo_private(self):
        print('__metodo_private')
        return '__metodo_private'

f = Foo()
print(f.public)                    # Acesso público
# print(f._protected)              # Possível, mas não recomendado
# print(f.__exemplo)               # Erro: atributo privado
print(f.metodo_publico())          # Acessa método público e privado internamente
print(f._Foo__metodo_private())    # Acesso ao método privado via name mangling
```

### 6.5. Dicas e Boas Práticas

- Use um underline para indicar que um atributo ou método é protegido.
- Use dois underlines para indicar que é privado, mas lembre-se que ainda é acessível via name mangling.
- Prefira acessar atributos e métodos públicos fora da classe.
- Encapsule dados sensíveis e forneça acesso controlado via métodos (`@property`, getters/setters).

**Resumo:**  
Python não tem modificadores de acesso reais, mas segue convenções para indicar o nível de acesso dos atributos e métodos. Use essas convenções para escrever código mais claro e seguro.

---

## 7. Relações entre Classes: Associação, Agregação e Composição

As relações entre classes são fundamentais para modelar sistemas orientados a objetos. Os principais tipos são **associação**, **agregação** e **composição**.

### 7.1. O Que é Associação?

- **Associação** é uma relação onde objetos estão ligados dentro do sistema.
- É a relação mais comum entre objetos.
- Um objeto pode ter um atributo que referencia outro objeto.
- A associação não define como um objeto controla o ciclo de vida do outro.

### 7.2. Exemplo Prático de Associação

```py
class Escritor:
    def __init__(self, nome) -> None:
        self.nome = nome
        self._ferramenta = None

    @property
    def ferramenta(self):
        return self._ferramenta

    @ferramenta.setter
    def ferramenta(self, ferramenta):
        self._ferramenta = ferramenta

class FerramentaDeEscrever:
    def __init__(self, nome):
        self.nome = nome

    def escrever(self):
        return f'{self.nome} está escrevendo'

escritor = Escritor('Luiz')
caneta = FerramentaDeEscrever('Caneta Bic')
maquina_de_escrever = FerramentaDeEscrever('Máquina')
escritor.ferramenta = maquina_de_escrever

print(caneta.escrever())                  # Caneta Bic está escrevendo
print(maquina_de_escrever.escrever())     # Máquina está escrevendo
print(escritor.ferramenta.escrever())     # Máquina está escrevendo
```

**Explicação:**
- `Escritor` tem um atributo `ferramenta` que referencia um objeto do tipo `FerramentaDeEscrever`.
- A associação permite que o escritor use diferentes ferramentas para escrever.

### 7.3. Agregação e Composição (Introdução)

- **Agregação** e **composição** são tipos especiais de associação.
- **Agregação:** Um objeto pode existir independentemente do outro.
- **Composição:** Um objeto faz parte do outro e depende dele para existir.
- Serão detalhadas em tópicos futuros.

### 7.4. Dicas e Observações

- Use associação para modelar relações simples entre objetos.
- Lembre-se: associação não controla o ciclo de vida dos objetos relacionados.
- Para relações mais fortes, estude agregação e composição.

---

## 8. Agregação - Python Orientado a Objetos

A **agregação** é uma forma especializada de associação entre objetos, onde cada objeto tem seu ciclo de vida independente, mas um objeto pode usar outros para realizar tarefas.

### 8.1. O Que é Agregação?

- É uma relação de "um para muitos", onde um objeto (agregador) contém ou utiliza outros objetos.
- Os objetos agregados podem existir independentemente do objeto agregador.
- Exemplo: Um carrinho de compras agrega vários produtos, mas os produtos podem existir sem o carrinho.

### 8.2. Diferença entre Associação e Agregação

- **Associação:** Relação simples, objetos podem se referenciar, mas não há dependência forte.
- **Agregação:** Um objeto "agrega" outros, mas todos têm ciclos de vida independentes.

### 8.3. Exemplo Prático de Agregação

```py
class Carrinho:
    def __init__(self):
        self._produtos = []

    def total(self):
        return sum([p.preco for p in self._produtos])
    
    def inserir_produtos(self, *produtos):
        for produto in produtos:
            self._produtos.append(produto)
    
    def listar_produtos(self):
        print()
        for produto in self._produtos:
            print(produto.nome, produto.preco)
        print()

class Produto:
    def __init__(self, nome, preco):
        self.nome = nome
        self.preco = preco

carrinho = Carrinho()
p1, p2 = Produto('Produto 1', 10), Produto('Produto 2', 20)
carrinho.inserir_produtos(p1, p2)
carrinho.listar_produtos()
print(carrinho.total())  # Saída: 30
```

**Explicação:**
- `Carrinho` agrega objetos do tipo `Produto`.
- Os produtos existem independentemente do carrinho.

### 8.4. Dicas e Observações

- Use agregação quando objetos podem existir separadamente, mas um precisa do outro para certas tarefas.
- Agregação é útil para modelar relações de "tem-um" (has-a) sem dependência de ciclo de vida.
- Não confunda agregação com composição (na composição, o ciclo de vida dos objetos é dependente).

---

## 9. Composição - Python Orientado a Objeto

A **composição** é uma forma forte de relação entre objetos, onde o ciclo de vida dos objetos "filhos" depende do ciclo de vida do objeto "pai". Quando o objeto pai é destruído, todos os objetos filhos criados por ele também são destruídos.

### 9.1. O Que é Composição?

- É uma especialização da agregação.
- O objeto "pai" é responsável por criar e destruir os objetos "filhos".
- Quando o pai é apagado, os filhos também são apagados automaticamente.

### 9.2. Diferença entre Agregação e Composição

- **Agregação:** Objetos podem existir independentemente do agregador.
- **Composição:** Objetos filhos só existem enquanto o objeto pai existir.

### 9.3. Exemplo Prático de Composição

```py
class Cliente:
    def __init__(self, nome):
        self.nome = nome
        self.enderecos = []

    def inserir_endereco(self, rua, numero):
        self.enderecos.append(Endereco(rua, numero))

    def inserir_endereco_externo(self, endereco):
        self.enderecos.append(endereco)

    def listar_enderecos(self):
        for endereco in self.enderecos:
            print(endereco.rua, endereco.numero)

    def __del__(self):
        print('APAGANDO,', self.nome)

class Endereco:
    def __init__(self, rua, numero):
        self.rua = rua
        self.numero = numero

    def __del__(self):
        print('APAGANDO,', self.rua, self.numero)

cliente1 = Cliente('Maria')
cliente1.inserir_endereco('Av Brasil', 54)
cliente1.inserir_endereco('Rua B', 6745)
endereco_externo = Endereco('Av Saudade', 123213)
cliente1.inserir_endereco_externo(endereco_externo)
cliente1.listar_enderecos()

del cliente1

print(endereco_externo.rua, endereco_externo.numero)
print('######################## AQUI TERMINA MEU CÓDIGO')
```

**Explicação:**
- Os endereços criados dentro de `Cliente` são destruídos junto com o cliente (composição).
- O endereço criado fora (`endereco_externo`) não é destruído ao apagar o cliente, pois não foi criado pelo cliente (agregação).

### 9.4. Dicas e Observações

- Use composição quando o objeto filho só faz sentido existir junto com o objeto pai.
- O método `__del__` é chamado quando o objeto é destruído (atenção: o momento exato pode variar por causa do garbage collector do Python).
- Composição é útil para modelar relações de "faz parte de" (ex: um cliente tem endereços).

**Resumo:**  
Na composição, o ciclo de vida dos objetos filhos depende do ciclo de vida do objeto pai. Se o pai for destruído, os filhos também serão.

---