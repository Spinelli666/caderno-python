# Caderno de Estudo para a Linguagem Python

Esse caderno é para me auxiliar nos estudos de Python, aqui trarei todo o conteúdo que irei estudar.

## Sumário

<details>
<summary>1. <a href="./doc/introducao.md">Introdução</a></summary>

### Resumo:
A introdução aborda a história e as principais características da linguagem Python, incluindo:
- **História:** Criada por Guido van Rossum em 1991, com foco em simplicidade e legibilidade.
- **Características principais:**
  - Sintaxe simples e intuitiva.
  - Versatilidade para diversas áreas, como desenvolvimento web, ciência de dados e inteligência artificial.
  - Linguagem interpretada, orientada a objetos e multiplataforma.
  - Grande comunidade e ecossistema rico de bibliotecas e frameworks.
- **Zen of Python.**

[Clique aqui para acessar o conteúdo completo.](./doc/introducao.md)

</details>

<details>
<summary>2. <a href="./doc/fundamentos1.md">Fundamentos 1</a></summary>

### Resumo:
O arquivo **Fundamentos 1** apresenta os conceitos básicos da linguagem Python, incluindo:
1. **Função `print()`:** Como exibir informações na tela, com exemplos de uso de `sep` e `end`.
2. **Tipos de Dados:** Tipos primitivos (`int`, `float`, `str`, `bool`) e conversões entre tipos.
3. **Operadores Aritméticos:** Operações matemáticas básicas, como soma, subtração, divisão, potência, etc.
4. **Variáveis:** Como declarar e usar variáveis em Python.
5. **Operações com Strings:** Concatenar, repetir e fatiar strings.
6. **Função `input()`:** Captura de entrada do usuário e conversão de dados.
7. **Métodos de Strings:** Métodos úteis para manipulação de strings, como `.lower()`, `.upper()`, `.replace()`, `.split()`, entre outros.
8. **Formatação de Strings:**
   - **Com `f-strings`:** Inserção de variáveis e expressões diretamente em strings.
   - **Com `.format()`:** Substituição de placeholders em strings.
   - **Com `%`:** Interpolação de strings usando especificadores de formato.

[Clique aqui para acessar o conteúdo completo.](./doc/fundamentos1.md)

</details>

<details>
<summary>3. <a href="./doc/fundamentos2.md">Fundamentos 2</a></summary>

### Resumo:
O arquivo **Fundamentos 2** aprofunda os conceitos da linguagem Python, abordando:
1. **Blocos de Código e Condicionais:** Uso de `if`, `elif` e `else` para controle de fluxo.
2. **Operadores de Comparação:** Comparações entre valores, como `>`, `<`, `==`, etc.
3. **Operadores Lógicos:** Combinação de condições com `and`, `or` e `not`.
4. **Operadores de Associação:** Verificação de pertencimento com `in` e `not in`.
5. **Interpolação de Strings:** Formatação de strings com `%`.
6. **Fatiamento de Strings:** Acesso a partes específicas de strings com `[início:fim:passo]`.
7. **Função `len`:** Contagem de caracteres em strings.
8. **Bloco `try` e `except`:** Tratamento de exceções e boas práticas.
9. **Variáveis e Constantes:** Convenções e boas práticas para reduzir a complexidade do código.
10. **Flag, `is`, `is not` e `None`:** Controle de estados e comparação de identidade de objetos.
11. **Função `id`:** Identificação única de objetos na memória.

[Clique aqui para acessar o conteúdo completo.](./doc/fundamentos2.md)

</details>

<details>
<summary>4. <a href="./doc/fundamentos3.md">Fundamentos 3</a></summary>

### Resumo:
O arquivo **Fundamentos 3** explora conceitos intermediários e avançados da linguagem Python, incluindo:
1. **Estruturas de Repetição:**
   - Uso do `while` e `break` para criar laços de repetição.
   - Boas práticas com `while`.
2. **Operadores de Atribuição com Operadores Aritméticos:**
   - Operadores como `+=`, `-=`, `*=`, etc.
   - Exemplos práticos de uso.
3. **Estruturas de Repetição com `for` e `range`:**
   - Iteração com `for` e como ele funciona internamente.
   - Uso de `enumerate` e `zip` para iterar sobre iteráveis.
4. **Introdução às Listas Mutáveis:**
   - Métodos úteis como `append`, `insert`, `pop`, `del`, `clear`, `extend`, e concatenação.
   - Cuidados com tipos mutáveis.
   - Iteração com `for in` em listas.
5. **Imprecisão de Números de Ponto Flutuante:**
   - Problemas de precisão com ponto flutuante.
   - Uso de `round` e `decimal.Decimal` para maior precisão.
6. **Métodos Úteis de Strings:**
   - Métodos como `split`, `join` e `strip`.
   - Exemplos práticos de manipulação de strings.
7. **Listas Dentro de Listas (Iteráveis Dentro de Iteráveis):**
   - Acessando elementos em listas aninhadas.
   - Iteração sobre listas de listas.
8. **Detalhes sobre o Interpretador do Python:**
   - Comandos úteis como `python mod.py`, `python -m`, `python -c`, etc.

[Clique aqui para acessar o conteúdo completo.](./doc/fundamentos3.md)

</details>

<details>
<summary>5. <a href="./doc/intermediario1.md">Intermediário 1</a></summary>

### Resumo:
O arquivo **Intermediário 1** aprofunda os conceitos de funções em Python, abordando:
1. **Introdução às Funções (`def`) em Python:**
   - Definição de funções.
   - Parâmetros e argumentos.
   - Valores padrão para parâmetros.
2. **Argumentos Nomeados e Posicionais:**
   - Diferença entre argumentos posicionais e nomeados.
   - Mistura de argumentos posicionais e nomeados.
3. **Valores Padrão para Parâmetros:**
   - Uso de valores padrão e `None` como valor padrão.
   - Refatoração de código com valores padrão.
4. **Escopo de Funções e Módulos:**
   - Diferença entre escopo global e local.
   - Uso da palavra-chave `global`.
5. **Retorno de Valores das Funções (`return`):**
   - Uso do `return` para retornar valores.
   - Retorno de múltiplos valores.
6. **Argumentos Não Nomeados com `*args`:**
   - Empacotamento e desempacotamento de argumentos.
   - Comparação com a função `sum`.
7. **Higher Order Functions e First-Class Functions:**
   - Diferença entre Higher Order Functions e First-Class Functions.
   - Exemplos práticos.
8. **Closure e Funções que Retornam Outras Funções:**
   - O que é uma closure.
   - Funções que retornam outras funções.
   - Exemplos práticos de closures.

[Clique aqui para acessar o conteúdo completo.](./doc/intermediario1.md)

</details>

<details>
<summary>6. <a href="./doc/intermediario2.md">Intermediário 2</a></summary>

### Resumo:
O arquivo **Intermediário 2** explora conceitos avançados de dicionários e conjuntos em Python, incluindo:
1. **Introdução ao Tipo de Dados `dict` - Dicionários em Python:**
   - O que são dicionários.
   - Criando e acessando valores em dicionários.
   - Iterando sobre dicionários.
2. **Manipulando Chaves e Valores em Dicionários:**
   - Adicionando, atualizando e removendo valores.
   - Verificando a existência de chaves.
3. **Métodos Úteis nos Dicionários Python (`dict`):**
   - Métodos como `setdefault`, `pop`, `popitem`, `update`, entre outros.
4. **Shallow Copy vs Deep Copy em Dados Mutáveis:**
   - Diferença entre cópia rasa e cópia profunda.
   - Exemplos práticos com `copy()` e `copy.deepcopy()`.
5. **Introdução ao Tipo `set` em Python (Conjuntos):**
   - O que são sets.
   - Criando e manipulando sets.
6. **Peculiaridades do Tipo Mutável `set`:**
   - Características como valores únicos e ausência de índices.
7. **Métodos Úteis do Tipo `set`:**
   - Métodos como `add`, `update`, `discard`, entre outros.
8. **Operadores Importantes para o Tipo `set`:**
   - Operadores como união (`|`), interseção (`&`), diferença (`-`), e diferença simétrica (`^`).
9. **Exemplos de Uso do Tipo `set`:**
   - Remoção de duplicados.
   - Aplicações práticas como jogos e validações.

[Clique aqui para acessar o conteúdo completo.](./doc/intermediario2.md)

</details>

<details>
<summary>7. <a href="./doc/intermediario3.md">Intermediário 3</a></summary>

### Resumo:
O arquivo **Intermediário 3** explora conceitos avançados de funções, comprehensions e manipulação de dados em Python, incluindo:
1. **Introdução à Função `lambda` (Função Anônima de Uma Linha):**
   - O que é uma função `lambda`.
   - Criando funções `lambda`.
   - Exemplos práticos com `lambda`.
2. **Funções Lambda Complexas:**
   - Funções `lambda` com retorno de outra função.
   - Funções `lambda` com múltiplos argumentos.
   - Funções `lambda` com `*args`.
3. **Empacotamento e Desempacotamento de Dicionários:**
   - Troca de valores com empacotamento.
   - Desempacotamento de dicionários.
4. **Uso de `*args` e `**kwargs`:**
   - O que são `*args` e `**kwargs`.
   - Exemplos práticos com `*args` e `**kwargs`.
5. **Introdução à List Comprehension:**
   - O que é List Comprehension.
   - Criando listas com List Comprehension.
   - Exemplos práticos.
6. **Mapeamento de Dados em List Comprehension:**
   - O que é mapeamento de dados.
   - Mapeamento com List Comprehension.
   - Exemplos práticos com condições.
7. **Filtro de Dados em List Comprehension (`filter`):**
   - O que é filtro de dados.
   - Filtrando dados com List Comprehension.
   - Exemplos práticos com condições.
8. **List Comprehension com Mais de Um `for`:**
   - O que é List Comprehension com múltiplos `for`.
   - Criando listas com múltiplos `for`.
   - Exemplos práticos com múltiplos `for`.
9. **Dictionary Comprehension e Set Comprehension:**
   - O que é Dictionary Comprehension.
   - O que é Set Comprehension.
   - Exemplos práticos.
10. **Função `isinstance()` - Para Saber se um Objeto é de Determinado Tipo:**
    - O que é a função `isinstance()`.
    - Usando `isinstance()` com tipos simples.
    - Usando `isinstance()` com múltiplos tipos.
    - Exemplos práticos.
11. **Valores Truthy e Falsy:**
    - O que são valores Truthy e Falsy.
    - Exemplos de valores Truthy e Falsy.
12. **Tipos Mutáveis e Imutáveis:**
    - O que são tipos mutáveis e imutáveis.
    - Exemplos de tipos mutáveis e imutáveis.
13. **Funções `dir`, `hasattr` e `getattr`:**
    - O que é a função `dir`.
    - O que é a função `hasattr`.
    - O que é a função `getattr`.
    - Exemplos práticos.
14. **Generator Expression, Iterables e Iterators:**
    - O que são iterables.
    - O que são iterators.
    - O que são generator expressions.
    - Diferença entre List Comprehension e Generator Expression.
    - Exemplos práticos.

[Clique aqui para acessar o conteúdo completo.](./doc/intermediario3.md)

</details>

<details>
<summary>8. <a href="./doc/intermediario4.md">Intermediário 4</a></summary>

### Resumo:
O arquivo **Intermediário 4** aprofunda conceitos sobre generators, tratamento de exceções e lançamento de erros em Python, incluindo:
1. **Introdução às Generator Functions em Python:**
   - O que são Generator Functions.
   - Como criar uma Generator Function.
   - Diferença entre Generator Functions e Generator Expressions.
   - Exemplos práticos.
2. **Yield from em Generator Functions:**
   - O que é `yield from`.
   - Como usar `yield from`.
   - Vantagens do `yield from`.
   - Exemplos práticos.
3. **Try e Except para Tratar Exceções:**
   - O que é o bloco `try` e `except`.
   - Tratando exceções específicas.
   - Capturando detalhes da exceção.
   - Exemplos práticos.
4. **Try, Except, Else e Finally:**
   - O que é o bloco `try`, `except`, `else` e `finally`.
   - Como usar `else` e `finally`.
   - Exemplos práticos.
5. **Built-in Exceptions:**
   - O que são Built-in Exceptions.
   - Exemplos de Built-in Exceptions.
6. **Raise - Lançando Exceções (Erros):**
   - O que é o `raise`.
   - Como usar o `raise`.
   - Tratando exceções lançadas com `raise`.
   - Exemplos práticos.

[Clique aqui para acessar o conteúdo completo.](./doc/intermediario4.md)

</details>

<details>
<summary>9. <a href="./doc/intermediario5.md">Intermediário 5</a></summary>

### Resumo:
O arquivo **Intermediário 5** explora conceitos avançados relacionados a módulos, pacotes e variáveis em Python, incluindo:
1. **Módulos - Import, From, As e *:**
   - O que são módulos.
   - Formas de importar módulos (completo, parcial, com alias e `*`).
   - Boas práticas ao importar módulos.
2. **Modularização - Entendendo os Seus Próprios Módulos e `sys.path`:**
   - O que é modularização.
   - Como o Python encontra módulos.
   - O papel do `__main__`.
   - Usando `sys.path` para personalizar caminhos.
3. **Como Importar Coisas do Seu Próprio Módulo (Ponto de Vista do `__main__`):**
   - Diferença entre o módulo principal e módulos importados.
   - Importação de módulos próprios.
   - Boas práticas ao importar de módulos próprios.
4. **Recarregando Módulos, `importlib` e Singleton:**
   - O que é recarregar módulos.
   - Usando `importlib.reload`.
   - O conceito de Singleton em módulos.
   - Boas práticas ao recarregar módulos.
5. **Introdução aos Packages (Pacotes) em Python:**
   - O que são packages.
   - Estrutura de um package.
   - Importando de packages.
   - O papel do arquivo `__init__.py`.
6. **O Ponto de Vista do `__main__` em Módulos e Pacotes:**
   - Como o `__main__` pode confundir.
   - Exemplos práticos para entender o comportamento do `__main__`.
7. **O Arquivo `__init__.py` nos Packages:**
   - O que é o `__init__.py`.
   - Usando o `__init__.py` para inicializar packages.
   - Exemplos práticos.
8. **Variáveis Livres e `nonlocal` (locals, globals):**
   - O que são variáveis livres.
   - O uso da palavra-chave `nonlocal`.
   - Funções `globals()` e `locals()`.
   - Exemplos práticos com variáveis livres e `nonlocal`.

[Clique aqui para acessar o conteúdo completo.](./doc/intermediario5.md)

</details>

<details>
<summary>10. <a href="./doc/intermediario6.md">Intermediário 6</a></summary>

### Resumo:
O arquivo **Intermediário 6** explora conceitos avançados de Python, incluindo decoradores, iteradores e funções recursivas, abordando:
1. **Variáveis Livres e `nonlocal` (locals, globals):**
   - O que são variáveis livres.
   - O que é a palavra-chave `nonlocal`.
   - Uso das funções `globals()` e `locals()`.
   - Exemplos práticos com variáveis livres e `nonlocal`.
2. **Funções Decoradoras e Decoradores:**
   - O que são funções decoradoras.
   - O que são decoradores e como usá-los com `@` (syntax sugar).
   - Exemplos práticos de criação e uso de decoradores.
3. **Decoradores com Parâmetros:**
   - O que são decoradores com parâmetros.
   - Como criar decoradores com parâmetros.
   - Vantagens dos decoradores com parâmetros.
4. **Ordem de Aplicação dos Decoradores:**
   - O que são decoradores empilhados.
   - Como funciona a ordem de aplicação.
   - Dicas para trabalhar com decoradores empilhados.
5. **Count é um Iterador Sem Fim (itertools):**
   - O que é `itertools.count`.
   - Diferença entre `count` e `range`.
   - Vantagens de usar `itertools.count`.
6. **Combinations, Permutations e Product - Itertools:**
   - O que são combinações, permutações e produto cartesiano.
   - Diferenças entre combinações, permutações e produto.
   - Exemplos práticos e vantagens de usar itertools.
7. **Groupby - Agrupando Valores (itertools):**
   - O que é `groupby`.
   - Como funciona o agrupamento com `groupby`.
   - Exemplos práticos e vantagens de usar `groupby`.
8. **Map, Partial, GeneratorType e Esgotamento de Iterators:**
   - O que é `map` e como usá-lo.
   - O que é `partial` e como criar funções parciais.
   - O que é `GeneratorType` e como verificar se um objeto é um generator.
   - Esgotamento de iteradores e como lidar com isso.
9. **Filter é um Filtro Funcional:**
   - O que é `filter` e como funciona.
   - Exemplos práticos de uso do `filter`.
   - Vantagens de usar `filter`.
10. **Reduce - Faz a Redução de um Iterável em um Valor:**
    - O que é `reduce` e como funciona.
    - Exemplos práticos de uso do `reduce`.
    - Vantagens e alternativas ao `reduce`.
11. **Funções Recursivas e Recursividade:**
    - O que são funções recursivas.
    - Elementos de uma função recursiva (caso base e caso recursivo).
    - Cuidados com funções recursivas (Stack Overflow e limite de recursão).
    - Exemplos práticos, como o cálculo de fatorial.

[Clique aqui para acessar o conteúdo completo.](./doc/intermediario6.md)

</details>

<details>
<summary>11. <a href="./doc/intermediario7.md">Intermediário 7</a></summary>

### Resumo:
O arquivo **Intermediário 7** aborda conceitos avançados de manipulação de arquivos, ambientes virtuais e boas práticas em Python, incluindo:
1. **O Que São Ambientes Virtuais em Python:**
   - O que é um ambiente virtual.
   - Por que usar ambientes virtuais.
   - Criando, ativando e desativando ambientes virtuais com `venv`.
   - Boas práticas ao usar ambientes virtuais.
2. **Pip - Instalando Pacotes e Bibliotecas:**
   - O que é o `pip`.
   - Comandos básicos para instalar, atualizar e desinstalar pacotes.
   - Congelando dependências com `pip freeze`.
   - Boas práticas ao usar o `pip`.
3. **Criando e Usando um `requirements.txt`:**
   - O que é o `requirements.txt`.
   - Criando e instalando dependências a partir do arquivo.
   - Boas práticas com o `requirements.txt`.
4. **Criando Arquivos com Python + Context Manager `with`:**
   - O que é a função `open` e modos de abertura de arquivos.
   - Usando o Context Manager `with` para manipular arquivos.
   - Métodos úteis do `TextIOWrapper` (`write`, `read`, `writelines`, etc.).
   - Operações com os módulos `os` e `json` para manipulação de arquivos e dados estruturados.
5. **Problema dos Parâmetros Mutáveis em Funções Python:**
   - O que são parâmetros mutáveis.
   - Problemas ao usar objetos mutáveis como valores padrão.
   - Como evitar o problema com `None`.
   - Exemplos práticos e boas práticas.
6. **Positional-Only Parameters (/) e Keyword-Only Arguments (*):**
   - O que são Positional-Only Parameters (`/`).
   - O que são Keyword-Only Arguments (`*`).
   - Exemplos práticos de uso.
   - Vantagens de usar `/` e `*` para maior clareza e controle.

[Clique aqui para acessar o conteúdo completo.](./doc/intermediario7.md)

</details>

<details>
<summary>12. <a href="./doc/poo1.md">POO 1</a></summary>

### Resumo:
O arquivo **POO 1** introduz os principais conceitos de Programação Orientada a Objetos (POO) em Python, incluindo:
1. **Classes como Moldes para Objetos:**
   - O que são classes e instâncias.
   - Como criar objetos a partir de classes.
   - Convenção de nomes (PascalCase para classes).
2. **Método `__init__` (Inicializador de Atributos):**
   - Como inicializar atributos de instância.
   - Diferença entre atributos de instância e de classe.
3. **Métodos em Instâncias de Classes:**
   - Definição e uso de métodos.
   - O papel do `self`.
4. **Entendendo `self` em Classes Python:**
   - Como o `self` referencia a própria instância.
   - Diferença entre chamada por instância e por classe.
5. **Escopo da Classe e de Métodos:**
   - Diferença entre atributos de classe, de instância e variáveis locais.
6. **Mantendo Estados Dentro da Classe:**
   - Como usar atributos para manter o estado do objeto.
   - Exemplo prático com métodos que alteram o estado.
7. **Atributos de Classe:**
   - O que são e como são compartilhados entre instâncias.
   - Diferença entre atributos de classe e de instância.
8. **`__dict__` e `vars` para Atributos de Instância:**
   - Como inspecionar e manipular atributos dinamicamente.
9. **Curiosidades sobre Convenções de Nomes:**
   - Diferença entre PascalCase, camelCase e snake_case.
   - Convenções recomendadas para Python.

[Clique aqui para acessar o conteúdo completo.](./doc/poo1.md)

</details>

<details>
<summary>13. <a href="./doc/poo2.md">POO 2</a></summary>

### Resumo:
O arquivo **POO 2** aprofunda os conceitos de Programação Orientada a Objetos em Python, incluindo:
1. **Métodos de Classe (@classmethod) e Factory Methods:**
   - O que são métodos de classe.
   - Como definir e usar métodos de classe.
   - Factory methods para criar instâncias de formas alternativas.
2. **@staticmethod (Métodos Estáticos):**
   - O que são métodos estáticos.
   - Diferença entre métodos estáticos e funções comuns.
   - Quando usar métodos estáticos.
3. **method vs @classmethod vs @staticmethod:**
   - Diferença entre métodos de instância, de classe e estáticos.
   - Exemplos práticos e dicas de uso.
4. **@property - Um Getter no Modo Pythônico:**
   - Como criar getters usando o decorador @property.
   - Vantagens do uso pythônico.
   - Comparação com getters tradicionais.
5. **@property + @setter - Getter e Setter no Modo Pythônico:**
   - Como criar getters e setters elegantes e seguros.
   - Boas práticas para encapsulamento.
6. **Encapsulamento (public, _protected, __private):**
   - Convenções de acesso em Python.
   - Name mangling e exemplos práticos.
7. **Relações entre Classes: Associação, Agregação e Composição:**
   - O que são associação, agregação e composição.
   - Exemplos práticos de cada relação.
   - Diferenças e dicas de modelagem.
8. **Agregação - Python Orientado a Objetos:**
   - Relação de um para muitos com ciclo de vida independente.
   - Exemplo prático de agregação.
9. **Composição - Python Orientado a Objeto:**
   - Relação forte de dependência entre objetos.
   - Diferença entre agregação e composição.
   - Exemplo prático de composição.

[Clique aqui para acessar o conteúdo completo.](./doc/poo2.md)

</details>

<details>
<summary>14. <a href="./doc/poo3.md">POO 3</a></summary>

### Resumo:
O arquivo **POO 3** aprofunda ainda mais os conceitos de Programação Orientada a Objetos em Python, incluindo:
1. **Herança Simples - Python Orientado a Objetos:**
   - O que é herança.
   - Diferença entre herança e composição.
   - Termos importantes (superclasse, subclasse, etc.).
   - Exemplo prático e dicas de uso.
2. **super() e a Sobreposição de Membros:**
   - O que é `super()` e como utilizá-lo.
   - Sobreposição (override) de métodos e atributos.
   - Ordem de Resolução de Métodos (MRO).
   - Exemplo prático e boas práticas.
3. **Herança Múltipla - Python Orientado a Objetos:**
   - O que é herança múltipla.
   - Diferença entre herança simples e múltipla.
   - Ordem de Resolução de Métodos (MRO) em herança múltipla.
   - Exemplo prático e dicas de uso.
4. **Classes Abstratas - Abstract Base Class (abc):**
   - O que são classes abstratas.
   - Uso do decorador `@abstractmethod`.
   - Regras e exemplos práticos.
   - Dicas e boas práticas.
5. **@abstractmethod para Qualquer Método Decorado (@property, setter, etc.):**
   - Como usar `@abstractmethod` com `@property`, setters, classmethods e staticmethods.
   - Exemplo prático e boas práticas.
6. **Polimorfismo, Assinatura de Métodos e Liskov Substitution Principle:**
   - O que é polimorfismo.
   - Assinatura de métodos e sobreposição (override).
   - Princípio da Substituição de Liskov (L do SOLID).
   - Exemplo prático e dicas de uso.
7. **Criando Exceptions em Python Orientado a Objetos:**
   - O que são exceções e como criar exceções personalizadas.
   - Levantando e relançando exceções.
   - Adicionando notas em exceções (Python 3.11+).
   - Exemplo prático e boas práticas.

[Clique aqui para acessar o conteúdo completo.](./doc/poo3.md)

</details>