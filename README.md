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