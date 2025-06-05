# Módulos Python 2

## Sumário

1. [O Módulo `os` para Interação com o Sistema](#1-o-módulo-os-para-interação-com-o-sistema)
    - 1.1. [O Que é o Módulo `os`?](#11-o-que-é-o-módulo-os)
    - 1.2. [Por Que Usar o Módulo `os`?](#12-por-que-usar-o-módulo-os)
    - 1.3. [Principais Funções do Módulo `os`](#13-principais-funções-do-módulo-os)
    - 1.4. [Exemplo Prático](#14-exemplo-prático)
    - 1.5. [Dicas e Boas Práticas](#15-dicas-e-boas-práticas)
2. [O Módulo `os.path` para Trabalhar com Caminhos](#2-o-módulo-ospath-para-trabalhar-com-caminhos)
    - 2.1. [O Que é o Módulo `os.path`?](#21-o-que-é-o-módulo-ospath)
    - 2.2. [Por Que Usar o Módulo `os.path`?](#22-por-que-usar-o-módulo-ospath)
    - 2.3. [Principais Funções do Módulo `os.path`](#23-principais-funções-do-módulo-ospath)
    - 2.4. [Exemplo Prático](#24-exemplo-prático)
    - 2.5. [Dicas e Boas Práticas](#25-dicas-e-boas-práticas)
3. [Usando `os.listdir` para Navegar em Caminhos](#3-usando-oslistdir-para-navegar-em-caminhos)
    - 3.1. [O Que é `os.listdir`?](#31-o-que-é-oslistdir)
    - 3.2. [Por Que Usar `os.listdir`?](#32-por-que-usar-oslistdir)
    - 3.3. [Principais Funções Relacionadas](#33-principais-funções-relacionadas)
    - 3.4. [Exemplo Prático](#34-exemplo-prático)
    - 3.5. [Dicas e Boas Práticas](#35-dicas-e-boas-práticas)
4. [Usando `os.walk` para Navegar em Caminhos de Forma Recursiva](#4-usando-oswalk-para-navegar-em-caminhos-de-forma-recursiva)
    - 4.1. [O Que é `os.walk`?](#41-o-que-é-oswalk)
    - 4.2. [Por Que Usar `os.walk`?](#42-por-que-usar-oswalk)
    - 4.3. [Estrutura Gerada por `os.walk`](#43-estrutura-gerada-por-oswalk)
    - 4.4. [Exemplo Prático](#44-exemplo-prático)
    - 4.5. [Dicas e Boas Práticas](#45-dicas-e-boas-práticas)
5. [Usando `os.path.getsize` e `os.stat` para Dados dos Arquivos (Tamanho em Bytes)](#5-usando-ospathgetsize-e-osstat-para-dados-dos-arquivos-tamanho-em-bytes)
    - 5.1. [O Que São `os.path.getsize` e `os.stat`?](#51-o-que-são-ospathgetsize-e-osstat)
    - 5.2. [Por Que Usar `os.path.getsize` e `os.stat`?](#52-por-que-usar-ospathgetsize-e-osstat)
    - 5.3. [Função para Formatar Tamanhos de Arquivos](#53-função-para-formatar-tamanhos-de-arquivos)
    - 5.4. [Exemplo Prático](#54-exemplo-prático)
    - 5.5. [Dicas e Boas Práticas](#55-dicas-e-boas-práticas)
6. [Usando `os` + `shutil` para Manipular Arquivos e Pastas](#6-usando-os--shutil-para-manipular-arquivos-e-pastas)
    - 6.1. [O Que São `os` e `shutil`?](#61-o-que-são-os-e-shutil)
    - 6.2. [Por Que Usar `os` e `shutil`?](#62-por-que-usar-os-e-shutil)
    - 6.3. [Principais Funções de `os` e `shutil`](#63-principais-funções-de-os-e-shutil)
    - 6.4. [Exemplo Prático: Copiando Arquivos e Pastas](#64-exemplo-prático-copiando-arquivos-e-pastas)
    - 6.5. [Exemplo Prático: Apagando, Movendo e Renomeando Pastas](#65-exemplo-prático-apagando-movendo-e-renomeando-pastas)
    - 6.6. [Dicas e Boas Práticas](#66-dicas-e-boas-práticas)

---

## 1. O Módulo `os` para Interação com o Sistema

### 1.1. O Que é o Módulo `os`?

- O módulo `os` fornece funções para interagir com o sistema operacional.
- Ele permite realizar operações como:
  - Executar comandos do sistema.
  - Manipular arquivos e diretórios.
  - Obter informações sobre o ambiente do sistema.

**Documentação oficial:**  
[https://docs.python.org/3/library/os.html](https://docs.python.org/3/library/os.html)

### 1.2. Por Que Usar o Módulo `os`?

- **Automatização de tarefas:**  
  Permite executar comandos do sistema diretamente do código Python.
- **Manipulação de arquivos e diretórios:**  
  Oferece funções para criar, renomear, excluir e listar arquivos e diretórios.
- **Portabilidade:**  
  Abstrai diferenças entre sistemas operacionais, permitindo que o código funcione em diferentes plataformas.

### 1.3. Principais Funções do Módulo `os`

| **Função**                | **Descrição**                                                                 |
|---------------------------|-------------------------------------------------------------------------------|
| `os.system(command)`      | Executa um comando do sistema operacional.                                   |
| `os.listdir(path)`        | Lista os arquivos e diretórios em um caminho especificado.                   |
| `os.getcwd()`             | Retorna o diretório de trabalho atual.                                       |
| `os.chdir(path)`          | Altera o diretório de trabalho atual.                                        |
| `os.mkdir(path)`          | Cria um novo diretório.                                                      |
| `os.rmdir(path)`          | Remove um diretório vazio.                                                   |

### 1.4. Exemplo Prático

```py
import os

# Executando comandos do sistema operacional
os.system('clear')  # Limpa o terminal (Linux/Mac/Windows PowerShell)
os.system('echo "hello world"')  # Exibe "hello world" no terminal

# Exibindo múltiplas linhas no terminal
print('a' * 80)
print('a' * 80)
print('a' * 80)
print('a' * 80)
print('a' * 80)
print('a' * 80)
```

**Explicação:**
1. **`os.system`:**  
   Executa comandos do sistema operacional, como limpar o terminal ou exibir mensagens.
2. **Exibição de múltiplas linhas:**  
   O código imprime várias linhas no terminal para simular uma saída longa.

### 1.5. Dicas e Boas Práticas

- **Evite usar `os.system` para comandos complexos:**  
  Prefira bibliotecas como `subprocess` para maior controle e segurança.
- **Teste em diferentes sistemas operacionais:**  
  Certifique-se de que o código funciona corretamente em Linux, Mac e Windows.
- **Documente os comandos usados:**  
  Explique claramente os comandos do sistema operacional executados pelo código.
- **Use funções específicas para manipulação de arquivos e diretórios:**  
  Prefira funções como `os.listdir` e `os.mkdir` para operações relacionadas a arquivos e pastas.

**Resumo:**  
O módulo `os` é uma ferramenta essencial para interagir com o sistema operacional em Python. Ele permite executar comandos, manipular arquivos e diretórios, e obter informações sobre o ambiente do sistema de forma eficiente e portátil.

---

## 2. O Módulo `os.path` para Trabalhar com Caminhos

### 2.1. O Que é o Módulo `os.path`?

- O módulo `os.path` fornece funções para manipular caminhos de arquivos e diretórios de forma portátil.
- Ele abstrai as diferenças entre sistemas operacionais (Windows, Linux e Mac), permitindo que o código funcione em qualquer plataforma.

**Documentação oficial:**  
[https://docs.python.org/3/library/os.path.html#module-os.path](https://docs.python.org/3/library/os.path.html#module-os.path)

### 2.2. Por Que Usar o Módulo `os.path`?

- **Portabilidade:**  
  Permite criar e manipular caminhos de arquivos sem se preocupar com as diferenças entre sistemas operacionais.
- **Facilidade de uso:**  
  Oferece funções úteis para juntar, dividir e verificar caminhos de arquivos.
- **Integração:**  
  Funciona bem com outros módulos como `os` e `shutil`.

### 2.3. Principais Funções do Módulo `os.path`

| **Função**                | **Descrição**                                                                 |
|---------------------------|-------------------------------------------------------------------------------|
| `os.path.join(*paths)`    | Junta strings em um único caminho, adaptando ao sistema operacional.          |
| `os.path.split(path)`     | Divide um caminho em uma tupla (diretório, arquivo).                         |
| `os.path.splitext(path)`  | Divide o caminho em (caminho, extensão).                                      |
| `os.path.exists(path)`    | Verifica se um caminho especificado existe.                                   |
| `os.path.basename(path)`  | Retorna o nome do arquivo ou diretório no final do caminho.                   |
| `os.path.dirname(path)`   | Retorna o diretório pai do caminho especificado.                              |

### 2.4. Exemplo Prático

```py
import os

# Criando um caminho de arquivo
caminho = os.path.join('Desktop', 'curso', 'arquivo.txt')
print(caminho)  # Saída: Desktop/curso/arquivo.txt (Linux/Mac) ou Desktop\curso\arquivo.txt (Windows)

# Dividindo o caminho em diretório e arquivo
diretorio, arquivo = os.path.split(caminho)
print(diretorio)  # Saída: Desktop/curso
print(arquivo)    # Saída: arquivo.txt

# Dividindo o caminho em caminho e extensão
caminho_arquivo, extensao_arquivo = os.path.splitext(caminho)
print(caminho_arquivo)  # Saída: Desktop/curso/arquivo
print(extensao_arquivo) # Saída: .txt

# Verificando se o caminho existe
print(os.path.exists(caminho))  # Saída: False (se o caminho não existir)

# Obtendo o nome do arquivo ou diretório
print(os.path.basename(caminho))  # Saída: arquivo.txt
print(os.path.basename(diretorio))  # Saída: curso

# Obtendo o diretório pai
print(os.path.dirname(caminho))  # Saída: Desktop/curso
```

**Explicação:**
1. **`os.path.join`:**  
   Junta strings em um único caminho, adaptando ao sistema operacional.
2. **`os.path.split`:**  
   Divide o caminho em diretório e arquivo.
3. **`os.path.splitext`:**  
   Divide o caminho em caminho e extensão.
4. **`os.path.exists`:**  
   Verifica se o caminho especificado existe.
5. **`os.path.basename`:**  
   Retorna o nome do arquivo ou diretório no final do caminho.
6. **`os.path.dirname`:**  
   Retorna o diretório pai do caminho especificado.

### 2.5. Dicas e Boas Práticas

- **Use `os.path.join` para portabilidade:**  
  Sempre use `os.path.join` para criar caminhos, evitando problemas com separadores de diretórios (`/` ou `\`).
- **Valide caminhos com `os.path.exists`:**  
  Antes de manipular arquivos ou diretórios, verifique se o caminho existe.
- **Documente os caminhos usados:**  
  Explique claramente os caminhos criados ou manipulados no código.
- **Teste em diferentes sistemas operacionais:**  
  Certifique-se de que o código funciona corretamente em Windows, Linux e Mac.
- **Evite manipulação manual de strings:**  
  Prefira usar as funções do módulo `os.path` para garantir portabilidade e evitar erros.

**Resumo:**  
O módulo `os.path` é uma ferramenta essencial para manipular caminhos de arquivos e diretórios em Python. Ele abstrai as diferenças entre sistemas operacionais, permitindo criar e manipular caminhos de forma eficiente e portátil.

---

## 3. Usando `os.listdir` para Navegar em Caminhos

### 3.1. O Que é `os.listdir`?

- **`os.listdir`** é uma função do módulo `os` que retorna uma lista contendo os nomes dos arquivos e diretórios em um caminho especificado.
- Ele é útil para navegar e listar o conteúdo de diretórios.

### 3.2. Por Que Usar `os.listdir`?

- **Exploração de diretórios:**  
  Permite listar o conteúdo de diretórios para manipulação ou análise.
- **Automatização:**  
  Facilita a navegação em estruturas de diretórios para realizar operações em arquivos ou subpastas.
- **Portabilidade:**  
  Funciona em diferentes sistemas operacionais (Windows, Linux e Mac).

### 3.3. Principais Funções Relacionadas

| **Função**                | **Descrição**                                                                 |
|---------------------------|-------------------------------------------------------------------------------|
| `os.listdir(path)`        | Retorna uma lista com os nomes dos arquivos e diretórios em um caminho.      |
| `os.path.join(*paths)`    | Junta strings em um único caminho, adaptando ao sistema operacional.          |
| `os.path.isdir(path)`     | Verifica se o caminho especificado é um diretório.                           |
| `os.path.isfile(path)`    | Verifica se o caminho especificado é um arquivo.                             |

### 3.4. Exemplo Prático

```py
import os

# Definindo o caminho base
caminho = os.path.join('/Users', 'nome', 'Desktop', 'EXEMPLO')

# Navegando no diretório base
for pasta in os.listdir(caminho):
    caminho_completo_pasta = os.path.join(caminho, pasta)
    print(pasta)  # Exibe o nome da pasta ou arquivo

    # Verifica se é um diretório
    if not os.path.isdir(caminho_completo_pasta):
        continue

    # Navegando dentro da subpasta
    for arquivo in os.listdir(caminho_completo_pasta):
        print('  ', arquivo)  # Exibe os arquivos dentro da subpasta
```

**Explicação:**
1. **`os.listdir`:**  
   Lista o conteúdo do diretório especificado em `caminho`.
2. **`os.path.join`:**  
   Junta o caminho base com o nome da pasta ou arquivo para criar o caminho completo.
3. **`os.path.isdir`:**  
   Verifica se o caminho completo é um diretório antes de tentar navegar nele.
4. **Navegação em subpastas:**  
   Itera sobre os arquivos dentro de cada subpasta.

### 3.5. Dicas e Boas Práticas

- **Use `os.path.join` para portabilidade:**  
  Sempre use `os.path.join` para criar caminhos, evitando problemas com separadores de diretórios (`/` ou `\`).
- **Valide diretórios com `os.path.isdir`:**  
  Antes de navegar em um caminho, verifique se ele é um diretório.
- **Documente os caminhos usados:**  
  Explique claramente os caminhos criados ou manipulados no código.
- **Teste em diferentes sistemas operacionais:**  
  Certifique-se de que o código funciona corretamente em Windows, Linux e Mac.
- **Evite manipulação manual de strings:**  
  Prefira usar as funções do módulo `os` para garantir portabilidade e evitar erros.

**Resumo:**  
A função `os.listdir` é uma ferramenta essencial para navegar e listar o conteúdo de diretórios em Python. Combinada com funções como `os.path.join` e `os.path.isdir`, ela permite explorar e manipular estruturas de diretórios de forma eficiente e portátil.

---

## 4. Usando `os.walk` para Navegar em Caminhos de Forma Recursiva

### 4.1. O Que é `os.walk`?

- **`os.walk`** é uma função do módulo `os` que permite percorrer uma estrutura de diretórios de forma recursiva.
- Ele gera uma sequência de tuplas, onde cada tupla contém:
  - O diretório atual (`root`).
  - Uma lista de subdiretórios (`dirs`).
  - Uma lista de arquivos no diretório atual (`files`).

### 4.2. Por Que Usar `os.walk`?

- **Exploração recursiva:**  
  Permite navegar em estruturas de diretórios complexas, incluindo subpastas.
- **Automatização:**  
  Facilita operações em todos os arquivos e diretórios de uma estrutura.
- **Flexibilidade:**  
  Pode ser usado para listar, manipular ou excluir arquivos e diretórios.

### 4.3. Estrutura Gerada por `os.walk`

| **Elemento** | **Descrição**                                                                 |
|--------------|-------------------------------------------------------------------------------|
| `root`       | Caminho do diretório atual sendo percorrido.                                 |
| `dirs`       | Lista de subdiretórios no diretório atual.                                   |
| `files`      | Lista de arquivos no diretório atual.                                        |

### 4.4. Exemplo Prático

```py
import os
from itertools import count

# Definindo o caminho base
caminho = os.path.join('/Users', 'nome', 'Desktop', 'EXEMPLO')

# Contador para identificar níveis de navegação
counter = count()

# Percorrendo a estrutura de diretórios de forma recursiva
for root, dirs, files in os.walk(caminho):
    the_counter = next(counter)
    print(the_counter, 'Pasta atual:', root)

    # Listando subdiretórios
    for dir_ in dirs:
        print('  ', the_counter, 'Dir:', dir_)

    # Listando arquivos
    for file_ in files:
        caminho_completo_arquivo = os.path.join(root, file_)
        print('  ', the_counter, 'FILE:', caminho_completo_arquivo)

        # NÃO FAÇA ISSO (VAI APAGAR TODOS OS ARQUIVOS DA PASTA)
        # os.unlink(caminho_completo_arquivo)
```

**Explicação:**
1. **`os.walk`:**  
   Percorre a estrutura de diretórios de forma recursiva, gerando tuplas com `root`, `dirs` e `files`.
2. **`root`:**  
   Representa o diretório atual sendo percorrido.
3. **`dirs`:**  
   Lista os subdiretórios no diretório atual.
4. **`files`:**  
   Lista os arquivos no diretório atual.
5. **`os.path.join`:**  
   Junta o caminho do diretório atual (`root`) com o nome do arquivo para criar o caminho completo.

### 4.5. Dicas e Boas Práticas

- **Evite manipulações perigosas:**  
  Não exclua arquivos ou diretórios sem validação adequada (ex.: `os.unlink`).
- **Use `os.path.join` para portabilidade:**  
  Sempre use `os.path.join` para criar caminhos, evitando problemas com separadores de diretórios (`/` ou `\`).
- **Documente os caminhos usados:**  
  Explique claramente os caminhos criados ou manipulados no código.
- **Teste em diferentes sistemas operacionais:**  
  Certifique-se de que o código funciona corretamente em Windows, Linux e Mac.
- **Valide os arquivos e diretórios:**  
  Antes de realizar operações, verifique se os caminhos são válidos usando funções como `os.path.exists`.

**Resumo:**  
A função `os.walk` é uma ferramenta poderosa para navegar em estruturas de diretórios de forma recursiva. Combinada com funções como `os.path.join`, ela permite explorar e manipular arquivos e diretórios de forma eficiente e segura.

---

## 5. Usando `os.path.getsize` e `os.stat` para Dados dos Arquivos (Tamanho em Bytes)

### 5.1. O Que São `os.path.getsize` e `os.stat`?

- **`os.path.getsize`:**  
  Retorna o tamanho de um arquivo em bytes.
- **`os.stat`:**  
  Retorna informações detalhadas sobre um arquivo, incluindo seu tamanho (`st_size`), permissões, data de criação/modificação, entre outros.

### 5.2. Por Que Usar `os.path.getsize` e `os.stat`?

- **Obtenção de tamanho de arquivos:**  
  Permite verificar o tamanho de arquivos para análise ou validação.
- **Informações detalhadas:**  
  `os.stat` fornece dados adicionais sobre arquivos, como permissões e timestamps.
- **Automatização:**  
  Facilita operações em arquivos, como listar e formatar tamanhos.

### 5.3. Função para Formatar Tamanhos de Arquivos

```py
import math

def formata_tamanho(tamanho_em_bytes: int, base: int = 1000) -> str:
    """Formata um tamanho, de bytes para o tamanho apropriado."""
    if tamanho_em_bytes <= 0:
        return "0B"

    abreviacao_tamanhos = "B", "KB", "MB", "GB", "TB", "PB"
    indice_abreviacao_tamanhos = int(math.log(tamanho_em_bytes, base))
    potencia = base ** indice_abreviacao_tamanhos
    tamanho_final = tamanho_em_bytes / potencia
    abreviacao_tamanho = abreviacao_tamanhos[indice_abreviacao_tamanhos]

    return f'{tamanho_final:.2f} {abreviacao_tamanho}'
```

**Explicação:**
1. **Logaritmo:**  
   O logaritmo é usado para determinar o índice na lista de abreviações com base no tamanho em bytes.
2. **Divisão:**  
   O tamanho em bytes é dividido pela potência da base para calcular o tamanho final.
3. **Formatação:**  
   O tamanho final é formatado com duas casas decimais e a abreviação correspondente.

### 5.4. Exemplo Prático

```py
import os
from itertools import count

# Caminho base
caminho = os.path.join('/Users', 'nome', 'Desktop', 'EXEMPLO')

# Contador para identificar níveis de navegação
counter = count()

# Percorrendo a estrutura de diretórios
for root, dirs, files in os.walk(caminho):
    the_counter = next(counter)
    print(the_counter, 'Pasta atual:', root)

    # Listando subdiretórios
    for dir_ in dirs:
        print('  ', the_counter, 'Dir:', dir_)

    # Listando arquivos e seus tamanhos
    for file_ in files:
        caminho_completo_arquivo = os.path.join(root, file_)

        # Obtendo tamanho do arquivo
        stats = os.stat(caminho_completo_arquivo)
        tamanho = stats.st_size

        # Exibindo informações do arquivo
        print('  ', the_counter, 'FILE:', file_, formata_tamanho(tamanho))

        # NÃO FAÇA ISSO (VAI APAGAR TODOS OS ARQUIVOS DA PASTA)
        # os.unlink(caminho_completo_arquivo)
```

**Explicação:**
1. **`os.walk`:**  
   Percorre a estrutura de diretórios de forma recursiva.
2. **`os.stat`:**  
   Obtém informações detalhadas sobre cada arquivo, incluindo o tamanho em bytes (`st_size`).
3. **`formata_tamanho`:**  
   Converte o tamanho em bytes para um formato legível (ex.: KB, MB, GB).

### 5.5. Dicas e Boas Práticas

- **Use `os.stat` para informações detalhadas:**  
  Prefira `os.stat` quando precisar de dados adicionais além do tamanho do arquivo.
- **Valide caminhos antes de acessar arquivos:**  
  Certifique-se de que os arquivos existem usando `os.path.exists`.
- **Documente os cálculos de tamanho:**  
  Explique claramente como os tamanhos são formatados e exibidos.
- **Evite manipulações perigosas:**  
  Não exclua arquivos sem validação adequada (ex.: `os.unlink`).
- **Teste com diferentes tamanhos de arquivos:**  
  Certifique-se de que a formatação funciona corretamente para arquivos pequenos e grandes.

**Resumo:**  
`os.path.getsize` e `os.stat` são ferramentas essenciais para obter informações sobre arquivos em Python. Combinadas com funções como `os.walk` e `formata_tamanho`, elas permitem listar e formatar tamanhos de arquivos de forma eficiente e segura.

---

## 6. Usando `os` + `shutil` para Manipular Arquivos e Pastas

### 6.1. O Que São `os` e `shutil`?

- **`os`:**  
  Um módulo que fornece funções para interagir com o sistema operacional, incluindo manipulação de arquivos e diretórios.
- **`shutil`:**  
  Um módulo que fornece funções de alto nível para copiar, mover, renomear e apagar arquivos e diretórios.

### 6.2. Por Que Usar `os` e `shutil`?

- **Automatização:**  
  Permite criar scripts para manipular arquivos e pastas de forma programática.
- **Flexibilidade:**  
  Oferece funções para operações simples (`os.unlink`) e complexas (`shutil.copytree`).
- **Portabilidade:**  
  Funciona em diferentes sistemas operacionais (Windows, Linux e Mac).

### 6.3. Principais Funções de `os` e `shutil`

| **Função**                     | **Descrição**                                                                 |
|--------------------------------|-------------------------------------------------------------------------------|
| `os.makedirs(path, exist_ok)`  | Cria diretórios recursivamente.                                               |
| `os.unlink(path)`              | Apaga um arquivo.                                                            |
| `os.rename(src, dst)`          | Renomeia ou move um arquivo ou diretório.                                     |
| `shutil.copy(src, dst)`        | Copia um arquivo para outro local.                                            |
| `shutil.copytree(src, dst)`    | Copia uma árvore de diretórios recursivamente.                                |
| `shutil.rmtree(path)`          | Apaga uma árvore de diretórios recursivamente.                                |
| `shutil.move(src, dst)`        | Move ou renomeia arquivos e diretórios.                                       |

### 6.4. Exemplo Prático: Copiando Arquivos e Pastas

```py
import os
import shutil

# Definindo os caminhos
HOME = os.path.expanduser('~')
DESKTOP = os.path.join(HOME, 'Desktop')
PASTA_ORIGINAL = os.path.join(DESKTOP, 'EXEMPLO')
NOVA_PASTA = os.path.join(DESKTOP, 'NOVA_PASTA')

# Criando a nova pasta
os.makedirs(NOVA_PASTA, exist_ok=True)

# Copiando arquivos e pastas
for root, dirs, files in os.walk(PASTA_ORIGINAL):
    for dir_ in dirs:
        caminho_novo_diretorio = os.path.join(
            root.replace(PASTA_ORIGINAL, NOVA_PASTA), dir_
        )
        os.makedirs(caminho_novo_diretorio, exist_ok=True)

    for file in files:
        caminho_arquivo = os.path.join(root, file)
        caminho_novo_arquivo = os.path.join(
            root.replace(PASTA_ORIGINAL, NOVA_PASTA), file
        )
        shutil.copy(caminho_arquivo, caminho_novo_arquivo)
```

**Explicação:**
1. **`os.makedirs`:**  
   Cria a nova pasta (`NOVA_PASTA`) se ela não existir.
2. **`os.walk`:**  
   Percorre a estrutura de diretórios de forma recursiva.
3. **`shutil.copy`:**  
   Copia cada arquivo para o novo local.

### 6.5. Exemplo Prático: Apagando, Movendo e Renomeando Pastas

```py
import os
import shutil

# Definindo os caminhos
HOME = os.path.expanduser('~')
DESKTOP = os.path.join(HOME, 'Desktop')
PASTA_ORIGINAL = os.path.join(DESKTOP, 'EXEMPLO')
NOVA_PASTA = os.path.join(DESKTOP, 'NOVA_PASTA')

# Apagando a nova pasta, se existir
shutil.rmtree(NOVA_PASTA, ignore_errors=True)

# Copiando a árvore de diretórios
shutil.copytree(PASTA_ORIGINAL, NOVA_PASTA)

# Renomeando ou movendo a pasta
shutil.move(NOVA_PASTA, NOVA_PASTA + '_RENOMEADA')

# Apagando a pasta renomeada
shutil.rmtree(NOVA_PASTA + '_RENOMEADA', ignore_errors=True)
```

**Explicação:**
1. **`shutil.rmtree`:**  
   Apaga a pasta (`NOVA_PASTA`) recursivamente, incluindo todos os arquivos e subpastas.
2. **`shutil.copytree`:**  
   Copia toda a estrutura de diretórios de `PASTA_ORIGINAL` para `NOVA_PASTA`.
3. **`shutil.move`:**  
   Renomeia ou move a pasta para um novo local.

### 6.6. Dicas e Boas Práticas

- **Valide caminhos antes de manipular:**  
  Use `os.path.exists` para verificar se arquivos ou pastas existem antes de realizar operações.
- **Evite manipulações perigosas:**  
  Tenha cuidado ao usar funções como `shutil.rmtree` e `os.unlink`, pois elas podem apagar dados permanentemente.
- **Use `exist_ok=True` com `os.makedirs`:**  
  Evite erros ao criar pastas que já existem.
- **Teste em diferentes sistemas operacionais:**  
  Certifique-se de que o código funciona corretamente em Windows, Linux e Mac.
- **Documente as operações:**  
  Explique claramente as ações realizadas no código (ex.: copiar, apagar, renomear).

**Resumo:**  
Os módulos `os` e `shutil` são ferramentas poderosas para manipular arquivos e pastas em Python. Eles permitem copiar, mover, renomear e apagar arquivos e diretórios de forma eficiente e segura, promovendo automatização e flexibilidade.

---