# POO 1

## Sumário

1. [class - Classes são moldes para criar novos objetos](#1-class---classes-são-moldes-para-criar-novos-objetos)
    - 1.1. [O Que São Classes?](#11-o-que-são-classes)
    - 1.2. [Instâncias e Objetos](#12-instâncias-e-objetos)
    - 1.3. [Atributos e Métodos](#13-atributos-e-métodos)
    - 1.4. [Convenção de Nomes](#14-convenção-de-nomes)
    - 1.5. [Exemplo Prático](#15-exemplo-prático)
2. [Introdução ao método `__init__` (inicializador de atributos)](#2-introdução-ao-método-__init__-inicializador-de-atributos)
    - 2.1. [O Que é o Método `__init__`?](#21-o-que-é-o-método-__init__)
    - 2.2. [Como Usar o `__init__`](#22-como-usar-o-__init__)
    - 2.3. [Exemplo Prático](#23-exemplo-prático)
    - 2.4. [Vantagens de Usar o `__init__`](#24-vantagens-de-usar-o-__init__)
3. [Métodos em Instâncias de Classes Python](#3-métodos-em-instâncias-de-classes-python)
    - 3.1. [O Que São Métodos de Instância?](#31-o-que-são-métodos-de-instância)
    - 3.2. [Como Definir Métodos de Instância](#32-como-definir-métodos-de-instância)
    - 3.3. [Exemplo Prático](#33-exemplo-prático)
    - 3.4. [Dicas e Boas Práticas](#34-dicas-e-boas-práticas)
4. [Entendendo `self` em Classes Python](#4-entendendo-self-em-classes-python)
    - 4.1. [O Que é `self`?](#41-o-que-é-self)
    - 4.2. [Classe vs Instância](#42-classe-vs-instância)
    - 4.3. [Como o `self` é Usado](#43-como-o-self-é-usado)
    - 4.4. [Exemplo Prático](#44-exemplo-prático)
    - 4.5. [Dicas e Observações](#45-dicas-e-observações)
5. [Escopo da Classe e de Métodos da Classe](#5-escopo-da-classe-e-de-métodos-da-classe)
    - 5.1. [Escopo da Classe](#51-escopo-da-classe)
    - 5.2. [Escopo do Método](#52-escopo-do-método)
    - 5.3. [Atributos de Classe vs Atributos de Instância](#53-atributos-de-classe-vs-atributos-de-instância)
    - 5.4. [Exemplo Prático](#54-exemplo-prático)
    - 5.5. [Dicas e Observações](#55-dicas-e-observações)
6. [Mantendo Estados Dentro da Classe](#6-mantendo-estados-dentro-da-classe)
    - 6.1. [O Que é Estado em uma Classe?](#61-o-que-é-estado-em-uma-classe)
    - 6.2. [Como Manter o Estado](#62-como-manter-o-estado)
    - 6.3. [Exemplo Prático](#63-exemplo-prático)
    - 6.4. [Dicas e Boas Práticas](#64-dicas-e-boas-práticas)
7. [Atributos de Classe](#7-atributos-de-classe)
    - 7.1. [O Que São Atributos de Classe?](#71-o-que-são-atributos-de-classe)
    - 7.2. [Diferença entre Atributos de Classe e de Instância](#72-diferença-entre-atributos-de-classe-e-de-instância)
    - 7.3. [Exemplo Prático](#73-exemplo-prático)
    - 7.4. [Dicas e Boas Práticas](#74-dicas-e-boas-práticas)
8. [`__dict__` e `vars` para Atributos de Instância](#8-__dict__-e-vars-para-atributos-de-instância)
    - 8.1. [O Que é `__dict__`?](#81-o-que-é-__dict__)
    - 8.2. [O Que é `vars`?](#82-o-que-é-vars)
    - 8.3. [Como Usar `__dict__` e `vars`](#83-como-usar-__dict__-e-vars)
    - 8.4. [Exemplo Prático](#84-exemplo-prático)
    - 8.5. [Dicas e Boas Práticas](#85-dicas-e-boas-práticas)
9. [Curiosidades sobre Convenções de Nomes](#9-curiosidades-sobre-convenções-de-nomes)
    - 9.1. [PascalCase](#91-pascalcase)
    - 9.2. [camelCase](#92-camelcase)
    - 9.3. [snake_case](#93-snake_case)
    - 9.4. [Padrões em Python](#94-padrões-em-python)

---

## 1. class - Classes são moldes para criar novos objetos

As **classes** em Python são moldes (ou "blueprints") para criar novos objetos (instâncias). Elas permitem organizar dados e comportamentos relacionados em um único lugar.

### 1.1. O Que São Classes?

- Uma **classe** define a estrutura e o comportamento de objetos.
- Objetos criados a partir de uma classe são chamados de **instâncias**.

### 1.2. Instâncias e Objetos

- Cada vez que você cria um objeto a partir de uma classe, está criando uma **instância** dessa classe.
- Cada instância pode ter seus próprios atributos (dados) e métodos (funções).

### 1.3. Atributos e Métodos

- **Atributos**: Variáveis que pertencem a cada instância.
- **Métodos**: Funções definidas dentro da classe que podem operar sobre os atributos da instância.

### 1.4. Convenção de Nomes

- Por convenção, nomes de classes usam **PascalCase** (primeira letra de cada palavra em maiúsculo).
- Exemplo: `Pessoa`, `Carro`, `ContaBancaria`.

### 1.5. Exemplo Prático

```py
class Pessoa:
    ...

p1 = Pessoa()
p1.nome = 'Luiz'
p1.sobrenome = 'Otávio'

p2 = Pessoa()
p2.nome = 'Maria'
p2.sobrenome = 'Joana'

print(p1.nome)       # Saída: Luiz
print(p1.sobrenome)  # Saída: Otávio

print(p2.nome)       # Saída: Maria
print(p2.sobrenome)  # Saída: Joana
```

**Explicação:**
- `Pessoa` é uma classe.
- `p1` e `p2` são instâncias da classe `Pessoa`.
- Cada instância recebe seus próprios atributos `nome` e `sobrenome`.

**Dicas:**
- Use classes para organizar e reutilizar código relacionado a entidades do seu programa.
- Prefira nomes descritivos e siga a convenção PascalCase para nomes de classes.
- Instâncias podem ter atributos diferentes, mesmo sendo criadas a partir da mesma classe.

---

## 2. Introdução ao método `__init__` (inicializador de atributos)

O método especial **`__init__`** é chamado automaticamente quando uma nova instância da classe é criada. Ele serve para inicializar os atributos do objeto.

### 2.1. O Que é o Método `__init__`?

- O **`__init__`** é conhecido como **método inicializador** ou **construtor**.
- Ele recebe como primeiro parâmetro o próprio objeto (`self`) e, em seguida, outros parâmetros definidos pelo programador.
- É usado para definir os atributos iniciais da instância.

### 2.2. Como Usar o `__init__`

- Defina o método `__init__` dentro da classe.
- Use `self.atributo = valor` para criar atributos de instância.

### 2.3. Exemplo Prático

```py
class Pessoa:
    def __init__(self, nome, sobrenome):
        self.nome = nome
        self.sobrenome = sobrenome

p1 = Pessoa('Luiz', 'Otávio')
p2 = Pessoa('Maria', 'Joana')

print(p1.nome)       # Saída: Luiz
print(p1.sobrenome)  # Saída: Otávio

print(p2.nome)       # Saída: Maria
print(p2.sobrenome)  # Saída: Joana
```

**Explicação:**
- Ao criar `p1 = Pessoa('Luiz', 'Otávio')`, o método `__init__` é chamado automaticamente, inicializando os atributos `nome` e `sobrenome` da instância `p1`.
- O mesmo ocorre para `p2`.

### 1.4. Vantagens de Usar o `__init__`

1. **Organização:** Facilita a criação de objetos já com seus atributos definidos.
2. **Segurança:** Garante que toda instância terá os atributos necessários.
3. **Clareza:** O código fica mais legível e fácil de manter.

**Dicas:**
- Sempre use o método `__init__` para inicializar atributos essenciais das suas classes.
- O nome `self` é uma convenção para se referir à instância atual da classe.

---

## 3. Métodos em Instâncias de Classes Python

Os **métodos de instância** são funções definidas dentro de uma classe que operam sobre os dados da própria instância (objeto).

### 3.1. O Que São Métodos de Instância?

- São funções que pertencem a uma classe, mas são chamadas a partir de uma instância (objeto).
- O primeiro parâmetro de um método de instância é sempre `self`, que representa o próprio objeto.

### 3.2. Como Definir Métodos de Instância

- Defina métodos dentro da classe usando `def`.
- Use `self` para acessar atributos e outros métodos da instância.

### 3.3. Exemplo Prático

```py
class Carro:
    def __init__(self, nome):
        self.nome = nome

    def acelerar(self):
        print(f'{self.nome} está acelerando')

fusca = Carro('Fusca')
print(fusca.nome)      # Saída: Fusca
fusca.acelerar()       # Saída: Fusca está acelerando

celta = Carro(nome='Celta')
print(celta.nome)      # Saída: Celta
celta.acelerar()       # Saída: Celta está acelerando
```

**Explicação:**
- O método `acelerar` é chamado a partir de cada instância (`fusca` e `celta`), e usa o atributo `nome` daquela instância.

### 3.4. Dicas e Boas Práticas

- Use métodos de instância para comportamentos que dependem dos dados do objeto.
- O nome `self` é uma convenção e deve ser mantido para clareza.
- Métodos podem acessar e modificar atributos da instância.

**Dicas:**
- Métodos de instância tornam seu código mais organizado e orientado a objetos.
- Evite hard coded (valores fixos no código) quando possível; prefira usar atributos e métodos para flexibilidade.

---

## 4. Entendendo `self` em Classes Python

O `self` é um conceito fundamental em programação orientada a objetos com Python. Ele representa a própria instância da classe, permitindo acessar atributos e métodos do objeto.

### 4.1. O Que é `self`?

- `self` é o primeiro parâmetro de métodos de instância em uma classe.
- Ele faz referência ao próprio objeto criado a partir da classe.
- Permite acessar e modificar atributos e métodos da instância.

### 4.2. Classe vs Instância

- **Classe:** É o molde, não possui dados próprios.
- **Instância:** É o objeto criado a partir da classe, possui seus próprios dados.

### 4.3. Como o `self` é Usado

- Dentro de métodos, use `self.atributo` para acessar ou definir atributos da instância.
- Métodos de instância sempre recebem `self` como primeiro argumento, mesmo que você não passe explicitamente ao chamar pelo objeto.

### 4.4. Exemplo Prático

```py
class Carro:
    def __init__(self, nome):
        self.nome = nome

    def acelerar(self):
        print(f'{self.nome} está acelerando')

fusca = Carro('Fusca')
fusca.acelerar()           # Chamada comum: self é passado automaticamente
Carro.acelerar(fusca)      # Chamada pela classe: você passa a instância explicitamente

celta = Carro(nome='Celta')
celta.acelerar()
Carro.acelerar(celta)
```

**Explicação:**
- `fusca.acelerar()` é equivalente a `Carro.acelerar(fusca)`.
- O `self` sempre representa a instância (`fusca` ou `celta`) dentro do método.

### 4.5. Dicas e Observações

- O nome `self` é uma convenção, mas é altamente recomendado usá-lo sempre.
- Métodos de instância sempre recebem a instância como primeiro argumento.
- Você pode chamar métodos tanto pela instância quanto pela classe, mas ao chamar pela classe, deve passar a instância explicitamente.

**Dicas:**
- Use sempre `self` para acessar atributos e métodos dentro da classe.
- Lembre-se: a classe é o molde, a instância é o objeto com dados.

---

## 5. Escopo da Classe e de Métodos da Classe

Entender o escopo em classes Python é fundamental para saber onde variáveis e métodos podem ser acessados e modificados.

### 5.1. Escopo da Classe

- O **escopo da classe** é onde você define atributos e métodos que pertencem à classe como um todo.
- Atributos definidos diretamente na classe (fora dos métodos) são chamados de **atributos de classe** e são compartilhados por todas as instâncias.

```py
class Animal:
    especie = 'Mamífero'  # Atributo de classe
```

### 5.2. Escopo do Método

- O **escopo do método** é o bloco de código dentro de um método (função da classe).
- Variáveis criadas dentro de métodos (como `variavel` no exemplo) existem apenas durante a execução do método e não são acessíveis fora dele.

### 5.3. Atributos de Classe vs Atributos de Instância

- **Atributos de classe:** Definidos diretamente na classe, compartilhados por todas as instâncias.
- **Atributos de instância:** Definidos dentro do método `__init__` usando `self`, exclusivos de cada instância.

### 5.4. Exemplo Prático

```py
class Animal:
    # nome = 'Leão'  # Atributo de classe (comentado)

    def __init__(self, nome):
        self.nome = nome  # Atributo de instância

        variavel = 'valor'  # Variável local ao método
        print(variavel)

    def comendo(self, alimento):
        return f'{self.nome} está comendo {alimento}'
    
    def executar(self, *args, **kwargs):
        return self.comendo(*args, **kwargs)

leao = Animal(nome='Leão')
print(leao.nome)                # Saída: Leão
print(leao.executar('carne'))   # Saída: Leão está comendo carne
```

**Explicação:**
- `self.nome` é um atributo de instância, exclusivo de cada objeto.
- `variavel` é local ao método `__init__` e não existe fora dele.
- Métodos podem acessar atributos de instância usando `self`.

### 5.5. Dicas e Observações

- Use atributos de classe para valores compartilhados entre todas as instâncias.
- Use atributos de instância para dados exclusivos de cada objeto.
- Variáveis locais em métodos só existem durante a execução do método.
- Métodos podem acessar atributos de instância e de classe, mas variáveis locais não são acessíveis fora do método.

**Dicas:**
- Prefira atributos de instância para dados que mudam de objeto para objeto.
- Use atributos de classe para constantes ou valores comuns a todas as instâncias.

---

## 6. Mantendo Estados Dentro da Classe

Manter **estado** em uma classe significa guardar informações sobre o objeto ao longo do tempo, permitindo que métodos possam consultar e modificar esses dados conforme necessário.

### 6.1. O Que é Estado em uma Classe?

- O **estado** de um objeto é definido pelos valores de seus atributos em determinado momento.
- O estado pode mudar conforme métodos são chamados e atributos são modificados.

### 6.2. Como Manter o Estado

- Use atributos de instância (definidos com `self`) para armazenar informações que representam o estado do objeto.
- Modifique esses atributos dentro dos métodos para refletir mudanças de estado.

### 6.3. Exemplo Prático

```py
class Camera:
    def __init__(self, nome, filmando=False):
        self.nome = nome
        self.filmando = filmando

    def filmar(self):
        if self.filmando:
            print(f'{self.nome} já está filmando')
            return
        print(f'{self.nome} está filmando')
        self.filmando = True

    def parar_filmar(self):
        if not self.filmando:
            print(f'{self.nome} não está filmando')
            return
        print(f'{self.nome} parou de filmar')
        self.filmando = False

    def fotografar(self):
        if self.filmando:
            print(f'{self.nome} não pode tirar fotos enquanto filma')
            return
        print(f'{self.nome} está tirando fotos')

c1 = Camera('Canon')
c2 = Camera('Sony')

c1.filmar()         # Canon está filmando
c1.filmar()         # Canon já está filmando
c1.fotografar()     # Canon não pode tirar fotos enquanto filma
c1.parar_filmar()   # Canon parou de filmar
c1.fotografar()     # Canon está tirando fotos

print()

c2.parar_filmar()   # Sony não está filmando
c2.filmar()         # Sony está filmando
c2.filmar()         # Sony já está filmando
c2.fotografar()     # Sony não pode tirar fotos enquanto filma
c2.parar_filmar()   # Sony parou de filmar
c2.fotografar()     # Sony está tirando fotos
```

**Explicação:**
- O atributo `filmando` guarda o estado da câmera (se está filmando ou não).
- Os métodos modificam e consultam esse estado para decidir o que fazer.

### 6.4. Dicas e Boas Práticas

- Use atributos de instância para guardar estados que mudam durante a vida do objeto.
- Sempre modifique o estado de forma controlada, preferencialmente através de métodos.
- Evite acessar ou modificar atributos diretamente fora da classe; prefira métodos para encapsular a lógica.

**Dicas:**
- O estado de cada instância é independente das outras.
- Métodos podem usar o estado para controlar o comportamento do objeto.
- Manter o estado corretamente é essencial para modelar comportamentos reais em POO.

---

## 7. Atributos de Classe

Os **atributos de classe** são variáveis que pertencem à própria classe, e não às instâncias criadas a partir dela. Eles são compartilhados entre todas as instâncias.

### 7.1. O Que São Atributos de Classe?

- São definidos diretamente dentro da classe, fora de qualquer método.
- São acessíveis tanto pela classe quanto pelas instâncias.
- Compartilham o mesmo valor entre todas as instâncias, a menos que sejam sobrescritos na instância.

### 7.2. Diferença entre Atributos de Classe e de Instância

- **Atributo de classe:** Compartilhado por todas as instâncias.
- **Atributo de instância:** Exclusivo de cada objeto, definido geralmente no `__init__`.

### 7.3. Exemplo Prático

```py
class Pessoa:
    ano_atual = 2022  # Atributo de classe

    def __init__(self, nome, idade):
        self.nome = nome          # Atributo de instância
        self.idade = idade        # Atributo de instância

    def get_ano_nascimento(self):
        return Pessoa.ano_atual - self.idade

p1 = Pessoa('João', 35)
p2 = Pessoa('Maria', 30)

print(Pessoa.ano_atual)           # Saída: 2022
print(p1.get_ano_nascimento())    # Saída: 1987
print(p2.get_ano_nascimento())    # Saída: 1992
```

**Explicação:**
- `ano_atual` é um atributo de classe, acessado tanto por `Pessoa.ano_atual` quanto dentro do método `get_ano_nascimento`.
- Se você alterar `Pessoa.ano_atual`, todas as instâncias verão o novo valor (a menos que sobrescreva na instância).

### 7.4. Dicas e Boas Práticas

- Use atributos de classe para valores que devem ser compartilhados entre todas as instâncias.
- Prefira atributos de instância para dados exclusivos de cada objeto.
- Para acessar atributos de classe dentro de métodos, use `Classe.atributo` (ex: `Pessoa.ano_atual`).

**Dicas:**
- Atributos de classe são úteis para constantes e configurações globais da classe.
- Evite modificar atributos de classe diretamente por instâncias, pois isso cria um novo atributo apenas naquela instância.

---

## 8. `__dict__` e `vars` para Atributos de Instância

Os atributos de instância de um objeto em Python podem ser acessados e manipulados dinamicamente usando o dicionário especial `__dict__` ou a função `vars`.

### 8.1. O Que é `__dict__`?

- O atributo especial `__dict__` é um dicionário que armazena todos os atributos de instância de um objeto.
- Permite acessar, modificar, adicionar ou remover atributos dinamicamente.

### 8.2. O Que é `vars`?

- A função embutida `vars(obj)` retorna o dicionário `__dict__` do objeto passado como argumento.
- É uma forma mais "pythonica" de acessar os atributos de instância.

### 8.3. Como Usar `__dict__` e `vars`

- Você pode acessar e modificar atributos diretamente pelo dicionário.
- Também pode adicionar novos atributos ou remover existentes.

### 8.4. Exemplo Prático

```py
class Pessoa:
    ano_atual = 2022

    def __init__(self, nome, idade):
        self.nome = nome
        self.idade = idade

    def get_ano_nascimento(self):
        return Pessoa.ano_atual - self.idade

dados = {'nome': 'João', 'idade': 35}
p1 = Pessoa(**dados)

# Adicionando um novo atributo dinamicamente
p1.__dict__['outra'] = 'coisa'

# Modificando um atributo existente
p1.__dict__['nome'] = 'EITA'

# Removendo um atributo
del p1.__dict__['idade']

# Acessando os atributos de instância
print(p1.__dict__)  # {'nome': 'EITA', 'outra': 'coisa'}
print(vars(p1))     # {'nome': 'EITA', 'outra': 'coisa'}

# Acessando atributos normalmente
print(p1.nome)      # EITA
print(p1.outra)     # coisa
```

### 8.5. Dicas e Boas Práticas

- Use `vars(obj)` para inspecionar rapidamente os atributos de instância.
- Modificar atributos diretamente pelo `__dict__` pode ser útil para metaprogramação, mas use com cuidado.
- Prefira acessar atributos diretamente (`obj.atributo`) para código mais legível, exceto em casos especiais.

**Dicas:**
- `__dict__` e `vars` são ótimos para depuração e manipulação dinâmica de objetos.
- Nem todos os objetos possuem `__dict__` (ex: objetos com `__slots__`).

---

## 9. Curiosidades sobre Convenções de Nomes

Em Python (e em outras linguagens), existem convenções para nomear variáveis, funções, classes e outros objetos. Essas convenções ajudam a manter o código organizado, legível e padronizado.

### 9.1. PascalCase

- Todas as palavras começam com letra maiúscula, sem separadores.
- Usado para nomes de **classes** em Python.
- Exemplos: `MinhaClasse`, `Classe`, `MeuObjeto`, `MeuProgramaMuitoLegal`

### 9.2. camelCase

- A primeira letra é minúscula, as demais palavras começam com maiúscula.
- Não é padrão em Python, mas é comum em outras linguagens como JavaScript e Java.
- Exemplos: `minhaFuncao`, `funcaoDeSoma`

### 9.3. snake_case

- Todas as letras são minúsculas e as palavras são separadas por underline (`_`).
- É o padrão para **variáveis**, **funções** e **métodos** em Python.
- Exemplos: `minha_variavel`, `funcao_legal`, `soma`

### 9.4. Padrões em Python

- **snake_case**: Para tudo que não for classe (variáveis, funções, métodos, módulos, etc.).
- **PascalCase**: Para nomes de classes.

**Resumo:**
- Use **PascalCase** para classes.
- Use **snake_case** para variáveis, funções e métodos.
- Evite **camelCase** em Python, pois não é a convenção da linguagem.

---