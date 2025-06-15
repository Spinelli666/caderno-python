# Módulos Python 4

## Sumário

1. [Usando o Módulo `random` para Geradores de Números Pseudoaleatórios](#1-usando-o-módulo-random-para-geradores-de-números-pseudoaleatórios)
    - 1.1. [O Que é o Módulo `random`?](#11-o-que-é-o-módulo-random)
    - 1.2. [Por Que Usar o Módulo `random`?](#12-por-que-usar-o-módulo-random)
    - 1.3. [Principais Funções do Módulo `random`](#13-principais-funções-do-módulo-random)
    - 1.4. [Exemplo Prático](#14-exemplo-prático)
    - 1.5. [Dicas e Boas Práticas](#15-dicas-e-boas-práticas)
2. [Usando o Módulo `secrets` para Gerar Números Aleatórios Seguros](#2-usando-o-módulo-secrets-para-gerar-números-aleatórios-seguros)
    - 2.1. [O Que é o Módulo `secrets`?](#21-o-que-é-o-módulo-secrets)
    - 2.2. [Por Que Usar o Módulo `secrets`?](#22-por-que-usar-o-módulo-secrets)
    - 2.3. [Principais Funções do Módulo `secrets`](#23-principais-funções-do-módulo-secrets)
    - 2.4. [Exemplo Prático](#24-exemplo-prático)
    - 2.5. [Dicas e Boas Práticas](#25-dicas-e-boas-práticas)
3. [Usando `string.Template` para Substituir Variáveis em Textos](#3-usando-stringtemplate-para-substituir-variáveis-em-textos)
    - 3.1. [O Que é `string.Template`?](#31-o-que-é-stringtemplate)
    - 3.2. [Por Que Usar `string.Template`?](#32-por-que-usar-stringtemplate)
    - 3.3. [Métodos de Substituição](#33-métodos-de-substituição)
    - 3.4. [Personalizando o Delimitador com Subclasses](#34-personalizando-o-delimitador-com-subclasses)
    - 3.5. [Exemplo Prático](#35-exemplo-prático)
    - 3.6. [Dicas e Boas Práticas](#36-dicas-e-boas-práticas)
4. [Usando Variáveis de Ambiente com Python](#4-usando-variáveis-de-ambiente-com-python)
    - 4.1. [O Que São Variáveis de Ambiente?](#41-o-que-são-variáveis-de-ambiente)
    - 4.2. [Por Que Usar Variáveis de Ambiente?](#42-por-que-usar-variáveis-de-ambiente)
    - 4.3. [Métodos para Trabalhar com Variáveis de Ambiente](#43-métodos-para-trabalhar-com-variáveis-de-ambiente)
    - 4.4. [Usando `python-dotenv` e Arquivos `.env`](#44-usando-python-dotenv-e-arquivos-env)
    - 4.5. [Exemplo Prático](#45-exemplo-prático)
    - 4.6. [Dicas e Boas Práticas](#46-dicas-e-boas-práticas)

---

## 1. Usando o Módulo `random` para Geradores de Números Pseudoaleatórios

### 1.1. O Que é o Módulo `random`?

- **`random`:**  
  É um módulo da biblioteca padrão do Python que fornece funções para gerar números pseudoaleatórios.
- **Pseudoaleatórios:**  
  Os números gerados parecem aleatórios, mas são baseados em algoritmos determinísticos. Portanto, não devem ser usados para segurança ou criptografia.

**Documentação oficial:**  
[https://docs.python.org/pt-br/3/library/random.html](https://docs.python.org/pt-br/3/library/random.html)

### 1.2. Por Que Usar o Módulo `random`?

- **Facilidade:**  
  Permite gerar números aleatórios e realizar operações como embaralhamento e seleção de elementos.
- **Flexibilidade:**  
  Suporta diferentes tipos de geração, como números inteiros, flutuantes e seleção de elementos de iteráveis.
- **Utilidade:**  
  É amplamente usado em jogos, simulações e testes.

### 1.3. Principais Funções do Módulo `random`

| **Função**                  | **Descrição**                                                                 |
|-----------------------------|-------------------------------------------------------------------------------|
| `random.seed(x)`            | Inicializa o gerador de números pseudoaleatórios com um valor específico.    |
| `random.randrange(início, fim, passo)` | Gera um número inteiro aleatório dentro de um intervalo com passo.           |
| `random.randint(início, fim)` | Gera um número inteiro aleatório dentro de um intervalo sem passo.            |
| `random.uniform(início, fim)` | Gera um número flutuante aleatório dentro de um intervalo.                    |
| `random.shuffle(seq)`       | Embaralha a sequência mutável original.                                      |
| `random.sample(iterável, k)` | Retorna uma lista com `k` elementos aleatórios do iterável (sem repetição).   |
| `random.choices(iterável, k)` | Retorna uma lista com `k` elementos aleatórios do iterável (com repetição).   |
| `random.choice(iterável)`   | Retorna um único elemento aleatório do iterável.                             |

### 1.4. Exemplo Prático

```py
import random
import time

# Inicializando o gerador de números pseudoaleatórios
random.seed(0)

# Gerando números inteiros aleatórios
r_range = random.randrange(10, 20, 2)
print(f"random.randrange: {r_range}")

r_int = random.randint(10, 20)
print(f"random.randint: {r_int}")

# Gerando números flutuantes aleatórios
r_uniform = random.uniform(10, 20)
print(f"random.uniform: {r_uniform}")

# Embaralhando uma lista
nomes = ['João', 'Maria', 'José', 'Ana', 'Pedro']
random.shuffle(nomes)
print(f"random.shuffle: {nomes}")

# Selecionando elementos aleatórios
novos_nomes_sample = random.sample(nomes, k=2)
print(f"random.sample: {novos_nomes_sample}")

novos_nomes_choices = random.choices(nomes, k=3)
print(f"random.choices: {novos_nomes_choices}")

# Escolhendo um único elemento aleatório
nome_escolhido = random.choice(nomes)
print(f"random.choice: {nome_escolhido}")
```

**Explicação:**
1. **`random.seed`:**  
   Inicializa o gerador de números pseudoaleatórios com um valor fixo para garantir resultados previsíveis.
2. **`random.randrange`:**  
   Gera um número inteiro dentro de um intervalo com passo.
3. **`random.randint`:**  
   Gera um número inteiro dentro de um intervalo sem passo.
4. **`random.uniform`:**  
   Gera um número flutuante dentro de um intervalo.
5. **`random.shuffle`:**  
   Embaralha a lista original.
6. **`random.sample`:**  
   Retorna uma lista com elementos aleatórios sem repetição.
7. **`random.choices`:**  
   Retorna uma lista com elementos aleatórios com repetição.
8. **`random.choice`:**  
   Retorna um único elemento aleatório.

### 1.5. Dicas e Boas Práticas

- **Evite usar `random` para segurança:**  
  Para fins criptográficos, use o módulo `secrets` ou `cryptography`.
- **Use `random.seed` para resultados previsíveis:**  
  Inicialize o gerador com um valor fixo para testes ou simulações.
- **Valide os intervalos:**  
  Certifique-se de que os intervalos fornecidos às funções são válidos.
- **Documente os usos:**  
  Explique claramente o propósito de cada função `random` usada no código.
- **Teste com diferentes entradas:**  
  Certifique-se de que o código funciona corretamente com diferentes valores e iteráveis.

**Resumo:**  
O módulo `random` é uma ferramenta poderosa para gerar números pseudoaleatórios e realizar operações como embaralhamento e seleção de elementos. Ele é ideal para jogos, simulações e testes, mas não deve ser usado para segurança ou criptografia.

---

## 2. Usando o Módulo `secrets` para Gerar Números Aleatórios Seguros

### 2.1. O Que é o Módulo `secrets`?

- **`secrets`:**  
  É um módulo da biblioteca padrão do Python projetado para gerar números aleatórios seguros, adequados para criptografia e segurança.
- **Segurança:**  
  Diferentemente do módulo `random`, `secrets` utiliza fontes de entropia seguras, tornando-o ideal para gerar senhas, tokens e outros valores sensíveis.

### 2.2. Por Que Usar o Módulo `secrets`?

- **Segurança:**  
  Garante que os números gerados sejam imprevisíveis e adequados para uso em segurança.
- **Criptografia:**  
  É recomendado para gerar valores aleatórios em aplicações que exigem segurança, como autenticação e geração de tokens.
- **Facilidade:**  
  Oferece funções simples e intuitivas para gerar números aleatórios seguros.

### 2.3. Principais Funções do Módulo `secrets`

| **Função**                  | **Descrição**                                                                 |
|-----------------------------|-------------------------------------------------------------------------------|
| `secrets.randbelow(n)`      | Retorna um número inteiro aleatório entre `0` e `n-1`.                       |
| `secrets.choice(iterável)`  | Retorna um elemento aleatório de um iterável.                                |
| `secrets.token_bytes(n)`    | Retorna um token aleatório de `n` bytes.                                     |
| `secrets.token_hex(n)`      | Retorna um token aleatório de `n` bytes como uma string hexadecimal.          |
| `secrets.token_urlsafe(n)`  | Retorna um token aleatório de `n` bytes como uma string segura para URLs.     |

### 2.4. Exemplo Prático

```py
import secrets
import string as s
from secrets import SystemRandom as Sr

# Gerando uma senha segura com caracteres aleatórios
senha_segura = ''.join(Sr().choices(s.ascii_letters + s.digits + s.punctuation, k=64))
print(f"Senha segura: {senha_segura}")

# Usando SystemRandom para gerar números aleatórios seguros
random = secrets.SystemRandom()

# Gerando números aleatórios seguros
r_range = random.randrange(10, 20, 2)
print(f"random.randrange: {r_range}")

r_int = random.randint(10, 20)
print(f"random.randint: {r_int}")

r_uniform = random.uniform(10, 20)
print(f"random.uniform: {r_uniform}")

# Embaralhando uma lista
nomes = ['Luiz', 'Maria', 'Helena', 'Joana']
random.shuffle(nomes)
print(f"random.shuffle: {nomes}")

# Selecionando elementos aleatórios
novos_nomes_sample = random.sample(nomes, k=3)
print(f"random.sample: {novos_nomes_sample}")

novos_nomes_choices = random.choices(nomes, k=3)
print(f"random.choices: {novos_nomes_choices}")

# Escolhendo um único elemento aleatório
nome_escolhido = random.choice(nomes)
print(f"random.choice: {nome_escolhido}")
```

**Explicação:**
1. **`secrets.SystemRandom`:**  
   Utiliza fontes de entropia seguras para gerar números aleatórios.
2. **Gerando senhas seguras:**  
   `SystemRandom.choices` é usado para criar uma senha segura com caracteres aleatórios.
3. **Funções de geração:**  
   `randrange`, `randint`, `uniform`, `shuffle`, `sample`, `choices` e `choice` são usadas para gerar números e manipular iteráveis de forma segura.

### 2.5. Dicas e Boas Práticas

- **Prefira `secrets` para segurança:**  
  Use o módulo `secrets` em vez de `random` para aplicações que exigem segurança.
- **Evite valores previsíveis:**  
  Não inicialize o gerador com valores fixos (`seed`), pois isso compromete a segurança.
- **Documente os usos:**  
  Explique claramente o propósito de cada função `secrets` usada no código.
- **Teste com diferentes entradas:**  
  Certifique-se de que o código funciona corretamente com diferentes valores e iteráveis.
- **Use tokens seguros:**  
  Utilize funções como `token_bytes`, `token_hex` e `token_urlsafe` para gerar valores seguros para autenticação e URLs.

**Resumo:**  
O módulo `secrets` é ideal para gerar números aleatórios seguros e imprevisíveis, sendo recomendado para aplicações que exigem segurança, como autenticação e criptografia. Ele oferece funções simples e eficientes para manipular valores sensíveis.

---

## 3. Usando `string.Template` para Substituir Variáveis em Textos

### 3.1. O Que é `string.Template`?

- **`string.Template`:**  
  É uma classe do módulo `string` que permite substituir variáveis em textos de forma simples e segura.
- **Delimitador padrão:**  
  As variáveis são identificadas pelo delimitador `$` seguido pelo nome da variável (ex.: `$nome`).

**Documentação oficial:**  
[https://docs.python.org/3/library/string.html#template-strings](https://docs.python.org/3/library/string.html#template-strings)

### 3.2. Por Que Usar `string.Template`?

- **Facilidade:**  
  Simplifica a substituição de variáveis em textos, especialmente em templates.
- **Segurança:**  
  Oferece métodos seguros para evitar erros durante a substituição.
- **Flexibilidade:**  
  Permite personalizar o delimitador e outras características criando subclasses.

### 3.3. Métodos de Substituição

| **Método**           | **Descrição**                                                                 |
|-----------------------|-------------------------------------------------------------------------------|
| `substitute(mapping)` | Substitui variáveis no texto, mas gera erros se faltar alguma chave.         |
| `safe_substitute(mapping)` | Substitui variáveis no texto sem gerar erros se faltar alguma chave.         |

### 3.4. Personalizando o Delimitador com Subclasses

- **Subclasse:**  
  Você pode criar uma subclasse de `string.Template` para alterar o delimitador padrão (`$`) ou outras características.

```py
class MyTemplate(string.Template):
    delimiter = '%'
```

### 3.5. Exemplo Prático

```py
import locale
import string
from datetime import datetime
from pathlib import Path

# Definindo o caminho do arquivo de texto
CAMINHO_ARQUIVO = Path(__file__).parent / 'aula183.txt'

# Configurando o locale para BRL
locale.setlocale(locale.LC_ALL, '')

def converte_para_brl(numero: float) -> str:
    """Converte um número para o formato BRL."""
    brl = 'R$ ' + locale.currency(numero, symbol=False, grouping=True)
    return brl

# Dados para substituição
data = datetime(2022, 12, 28)
dados = dict(
    nome='João',
    valor=converte_para_brl(1_234_456),
    data=data.strftime('%d/%m/%Y'),
    empresa='O. M.',
    telefone='+55 (11) 7890-5432'
)

# Subclasse personalizada de Template
class MyTemplate(string.Template):
    delimiter = '%'

# Lendo o arquivo de texto e substituindo variáveis
with open(CAMINHO_ARQUIVO, 'r') as arquivo:
    texto = arquivo.read()
    template = MyTemplate(texto)  # Usando o delimitador personalizado
    print(template.substitute(dados))  # Substitui variáveis
    # print(template.safe_substitute(dados))  # Substitui sem gerar erros
```

**Explicação:**
1. **`string.Template`:**  
   Permite substituir variáveis no texto lido do arquivo.
2. **Personalização:**  
   A subclasse `MyTemplate` altera o delimitador padrão para `%`.
3. **Substituição:**  
   `substitute` substitui as variáveis no texto com os valores fornecidos em `dados`.

### 3.6. Dicas e Boas Práticas

- **Use `safe_substitute` para evitar erros:**  
  Prefira `safe_substitute` quando não tiver certeza de que todas as variáveis estarão presentes.
- **Documente os templates:**  
  Explique claramente as variáveis esperadas no texto do template.
- **Personalize o delimitador:**  
  Use subclasses para alterar o delimitador padrão quando necessário.
- **Valide os dados:**  
  Certifique-se de que os valores fornecidos para substituição estão corretos e no formato esperado.
- **Teste com diferentes templates:**  
  Certifique-se de que o código funciona corretamente com diferentes textos e variáveis.

**Resumo:**  
`string.Template` é uma ferramenta poderosa para substituir variáveis em textos de forma simples e segura. Com métodos como `substitute` e `safe_substitute`, e a possibilidade de personalização via subclasses, ele é ideal para trabalhar com templates em Python.

---

## 4. Usando Variáveis de Ambiente com Python

### 4.1. O Que São Variáveis de Ambiente?

- **Variáveis de ambiente:**  
  São valores armazenados no ambiente do sistema operacional que podem ser usados em seu código.  
  Exemplo: configurações de banco de dados, chaves de API, ou informações específicas de cada ambiente (desenvolvimento, teste, produção).

### 4.2. Por Que Usar Variáveis de Ambiente?

- **Segurança:**  
  Permite armazenar informações sensíveis, como senhas e chaves de API, fora do código-fonte.
- **Flexibilidade:**  
  Facilita a configuração de diferentes ambientes (ex.: desenvolvimento, teste, produção).
- **Portabilidade:**  
  Permite que o mesmo código funcione em diferentes sistemas operacionais sem alterações.

### 4.3. Métodos para Trabalhar com Variáveis de Ambiente

| **Método**                  | **Descrição**                                                                 |
|-----------------------------|-------------------------------------------------------------------------------|
| `os.getenv('VARIAVEL')`     | Retorna o valor da variável de ambiente ou `None` se ela não existir.         |
| `os.environ['VARIAVEL']`    | Retorna o valor da variável de ambiente, gerando erro se ela não existir.     |
| `os.environ['VARIAVEL'] = 'valor'` | Define ou altera o valor de uma variável de ambiente.                          |

### 4.4. Usando `python-dotenv` e Arquivos `.env`

- **O que é `python-dotenv`?**  
  É uma biblioteca Python que facilita o uso de arquivos `.env` para armazenar variáveis de ambiente de forma segura e organizada.

- **Instalação:**  
  ```bash
  pip install python-dotenv
  ```

- **Formato do arquivo `.env`:**  
  ```env
  VARIAVEL_DE_AMBIENTE_1=valor
  VARIAVEL_DE_AMBIENTE_2=valor
  VARIAVEL_DE_AMBIENTE_3=valor
  ```

- **Como usar no código:**  
  ```py
  from dotenv import load_dotenv
  import os

  load_dotenv()  # Carrega as variáveis do arquivo .env
  valor_da_variavel = os.getenv("VARIAVEL_DE_AMBIENTE_1")
  ```

- **Benefícios do `.env`:**
  - **Segurança:**  
    O arquivo `.env` pode ser adicionado ao `.gitignore` para evitar que informações sensíveis sejam incluídas em repositórios.
  - **Flexibilidade:**  
    Permite armazenar configurações específicas para diferentes ambientes.

### 4.5. Exemplo Prático

```py
import os
from dotenv import load_dotenv  # type: ignore

# Carregando variáveis de ambiente do arquivo .env
load_dotenv()

# Obtendo o valor de uma variável de ambiente
senha_banco = os.getenv('BD_PASSWORD')
print(f"Senha do banco: {senha_banco}")

# Definindo uma variável de ambiente diretamente no código
os.environ['API_KEY'] = '123456'
print(f"Chave da API: {os.getenv('API_KEY')}")
```

**Exemplo de arquivo `.env`:**
```env
BD_PASSWORD=senha_secreta
API_KEY=valor_da_api
```

### 4.6. Dicas e Boas Práticas

- **Crie um `.env-example`:**  
  Inclua um arquivo `.env-example` no repositório para exemplificar as variáveis necessárias, mas sem valores reais.
- **Adicione `.env` ao `.gitignore`:**  
  Evite incluir o arquivo `.env` em repositórios para proteger informações sensíveis.
- **Use `os.getenv` para evitar erros:**  
  Prefira `os.getenv` em vez de `os.environ` para evitar exceções caso a variável não exista.
- **Documente as variáveis:**  
  Explique claramente o propósito de cada variável de ambiente usada no projeto.
- **Teste em diferentes ambientes:**  
  Certifique-se de que o código funciona corretamente em desenvolvimento, teste e produção.

**Resumo:**  
Variáveis de ambiente são essenciais para armazenar informações sensíveis e configurar diferentes ambientes de forma segura e flexível. Com o uso de `python-dotenv` e arquivos `.env`, é possível gerenciar essas variáveis de maneira eficiente e organizada.

---