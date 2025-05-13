# Intermediário 7

# Fundamentos 58

## Sumário

1. [O Que São Ambientes Virtuais em Python](#1-o-que-são-ambientes-virtuais-em-python)
    - 1.1. [O Que é um Ambiente Virtual?](#11-o-que-é-um-ambiente-virtual)
    - 1.2. [Por Que Usar Ambientes Virtuais?](#12-por-que-usar-ambientes-virtuais)
    - 1.3. [Criando um Ambiente Virtual com `venv`](#13-criando-um-ambiente-virtual-com-venv)
    - 1.4. [Ativando e Desativando o Ambiente Virtual](#14-ativando-e-desativando-o-ambiente-virtual)
    - 1.5. [Boas Práticas com Ambientes Virtuais](#15-boas-práticas-com-ambientes-virtuais)
2. [Pip - Instalando Pacotes e Bibliotecas](#2-pip---instalando-pacotes-e-bibliotecas)
    - 2.1. [O Que é o `pip`?](#21-o-que-é-o-pip)
    - 2.2. [Comandos Básicos do `pip`](#22-comandos-básicos-do-pip)
    - 2.3. [Instalando Pacotes com Versões Específicas](#23-instalando-pacotes-com-versões-específicas)
    - 2.4. [Desinstalando Pacotes](#24-desinstalando-pacotes)
    - 2.5. [Congelando Dependências com `pip freeze`](#25-congelando-dependências-com-pip-freeze)
    - 2.6. [Boas Práticas ao Usar o `pip`](#26-boas-práticas-ao-usar-o-pip)
3. [Criando e Usando um `requirements.txt`](#3-criando-e-usando-um-requirementstxt)
    - 3.1. [O Que é o `requirements.txt`?](#31-o-que-é-o-requirementstxt)
    - 3.2. [Criando um Arquivo `requirements.txt`](#32-criando-um-arquivo-requirementstxt)
    - 3.3. [Instalando Dependências do `requirements.txt`](#33-instalando-dependências-do-requirementstxt)
    - 3.4. [Boas Práticas com o `requirements.txt`](#34-boas-práticas-com-o-requirementstxt)
4. [Criando Arquivos com Python + Context Manager `with`](#4-criando-arquivos-com-python--context-manager-with)
    - 4.1. [O Que é a Função `open`?](#41-o-que-é-a-função-open)
    - 4.2. [Modos de Abertura de Arquivos](#42-modos-de-abertura-de-arquivos)
    - 4.3. [Usando o Context Manager `with`](#43-usando-o-context-manager-with)
    - 4.4. [Métodos Úteis do `TextIOWrapper`](#44-métodos-úteis-do-textiowrapper)
    - 4.5. [Exemplo Prático](#45-exemplo-prático)
    - 4.6. [Operações com o Módulo `os`](#46-operações-com-o-módulo-os)
    - 4.7. [Operações com o Módulo `json`](#47-operações-com-o-módulo-json)

---

## 1. O Que São Ambientes Virtuais em Python

Os **ambientes virtuais** permitem criar instalações isoladas do Python para diferentes projetos. Isso ajuda a evitar conflitos entre dependências e versões de pacotes.

### 1.1. O Que é um Ambiente Virtual?

- Um **ambiente virtual** é uma cópia isolada da instalação do Python, criada em uma pasta específica.
- Ele contém seus próprios binários do Python e gerenciador de pacotes (`pip`), separados do sistema global.

### 1.2. Por Que Usar Ambientes Virtuais?

1. **Isolamento de Dependências:**
   - Cada projeto pode ter suas próprias versões de pacotes, sem interferir em outros projetos.

2. **Evitar Conflitos:**
   - Diferentes projetos podem exigir versões diferentes de bibliotecas.

3. **Portabilidade:**
   - Facilita a replicação do ambiente de desenvolvimento em outras máquinas.

### 1.3. Criando um Ambiente Virtual com `venv`

O módulo **`venv`** é usado para criar ambientes virtuais.

**Comando para Criar um Ambiente Virtual:**
```bash
python3 -m venv nome_do_ambiente
```

- **`python3`**: O interpretador Python.
- **`-m venv`**: Indica que o módulo `venv` será usado.
- **`nome_do_ambiente`**: Nome da pasta onde o ambiente será criado (ex.: `venv`, `.venv`, `env`, `.env`).

**Exemplo:**
```bash
python3 -m venv venv
```

### 1.4. Ativando e Desativando o Ambiente Virtual

#### **Ativando o Ambiente Virtual:**

- **Linux/Mac:**
  ```bash
  source venv/bin/activate
  ```

- **Windows (cmd):**
  ```cmd
  venv\Scripts\activate
  ```

- **Windows (PowerShell):**
  ```powershell
  .\venv\Scripts\Activate.ps1
  ```

Após ativar, o nome do ambiente virtual aparecerá no início do prompt.

#### **Desativando o Ambiente Virtual:**
```bash
deactivate
```

### 1.5. Boas Práticas com Ambientes Virtuais

1. **Nomeação Consistente:**
   - Use nomes comuns como `venv`, `.venv`, `env` ou `.env` para facilitar a identificação.

2. **Adicione ao `.gitignore`:**
   - Evite versionar a pasta do ambiente virtual. Adicione-a ao arquivo `.gitignore`.

3. **Use um Gerenciador de Dependências:**
   - Gere um arquivo `requirements.txt` com as dependências do projeto:
     ```bash
     pip freeze > requirements.txt
     ```

4. **Recrie o Ambiente em Outras Máquinas:**
   - Instale as dependências a partir do `requirements.txt`:
     ```bash
     pip install -r requirements.txt
     ```

**Dicas:**
- Sempre ative o ambiente virtual antes de instalar pacotes com `pip`.
- Use ambientes virtuais para manter seus projetos organizados e evitar conflitos de dependências.
- Consulte a [documentação oficial do `venv`](https://docs.python.org/3/library/venv.html) para mais detalhes.

---

## 2. Pip - Instalando Pacotes e Bibliotecas

O **`pip`** é o gerenciador de pacotes padrão do Python. Ele permite instalar, atualizar e desinstalar pacotes e bibliotecas de forma simples e eficiente.

### 2.1. O Que é o `pip`?

- O **`pip`** (Python Package Index Installer) é usado para gerenciar pacotes disponíveis no [PyPI (Python Package Index)](https://pypi.org/).
- Ele facilita a instalação de bibliotecas externas e dependências para projetos Python.

### 2.2. Comandos Básicos do `pip`

#### **Instalar a Última Versão de um Pacote:**
```bash
pip install nome_pacote
```

**Exemplo:**
```bash
pip install requests
```

#### **Atualizar um Pacote:**
```bash
pip install --upgrade nome_pacote
```

**Exemplo:**
```bash
pip install --upgrade requests
```

### 2.3. Instalando Pacotes com Versões Específicas

Você pode instalar uma versão específica de um pacote usando o operador `==`.

**Comando:**
```bash
pip install nome_pacote==versao
```

**Exemplo:**
```bash
pip install requests==2.26.0
```

### 2.4. Desinstalando Pacotes

Para remover um pacote instalado, use o comando `uninstall`.

**Comando:**
```bash
pip uninstall nome_pacote
```

**Exemplo:**
```bash
pip uninstall requests
```

### 2.5. Congelando Dependências com `pip freeze`

O comando **`pip freeze`** exibe uma lista de todos os pacotes instalados no ambiente atual, junto com suas versões.

**Comando:**
```bash
pip freeze
```

**Exemplo de Saída:**
```
requests==2.26.0
numpy==1.21.2
```

#### **Salvar Dependências em um Arquivo:**
```bash
pip freeze > requirements.txt
```

#### **Instalar Dependências de um Arquivo:**
```bash
pip install -r requirements.txt
```

### 1.6. Boas Práticas ao Usar o `pip`

1. **Use Ambientes Virtuais:**
   - Sempre instale pacotes em um ambiente virtual para evitar conflitos globais.

2. **Especifique Versões:**
   - Sempre que possível, especifique versões no `requirements.txt` para garantir consistência.

3. **Atualize Pacotes com Cuidado:**
   - Teste atualizações em um ambiente separado antes de aplicá-las ao projeto principal.

4. **Documente Dependências:**
   - Use `pip freeze` para criar um arquivo `requirements.txt` e versioná-lo no controle de versão.

**Dicas:**
- Consulte a [documentação oficial do `pip`](https://pip.pypa.io/en/stable/) para mais detalhes.
- Use o comando `pip list` para visualizar todos os pacotes instalados no ambiente atual.
- Combine o `pip` com ambientes virtuais (`venv`) para manter seus projetos organizados e isolados.

---

## 3. Criando e Usando um `requirements.txt`

O **`requirements.txt`** é um arquivo usado para listar as dependências de um projeto Python. Ele facilita a instalação e o gerenciamento de pacotes necessários para o projeto.

### 3.1. O Que é o `requirements.txt`?

- É um arquivo de texto que contém uma lista de pacotes e suas versões.
- Ele é usado para documentar as dependências de um projeto e garantir que outros desenvolvedores possam replicar o ambiente.

**Exemplo de um `requirements.txt`:**
```
requests==2.26.0
numpy==1.21.2
flask==2.0.2
```

### 3.2. Criando um Arquivo `requirements.txt`

Para gerar um arquivo `requirements.txt` com as dependências instaladas no ambiente atual, use o comando:

```bash
pip freeze > requirements.txt
```

**Exemplo:**
```bash
pip freeze > requirements.txt
```

Isso criará um arquivo `requirements.txt` com a lista de pacotes e suas versões.

### 1.3. Instalando Dependências do `requirements.txt`

Para instalar todas as dependências listadas no `requirements.txt`, use o comando:

```bash
pip install -r requirements.txt
```

**Exemplo:**
```bash
pip install -r requirements.txt
```

Isso instalará todas as dependências na versão especificada no arquivo.

### 3.4. Boas Práticas com o `requirements.txt`

1. **Atualize Regularmente:**
   - Sempre que instalar ou atualizar pacotes, gere um novo `requirements.txt` com `pip freeze`.

2. **Especifique Versões:**
   - Inclua as versões dos pacotes no `requirements.txt` para garantir consistência entre ambientes.

3. **Adicione ao Controle de Versão:**
   - Versione o arquivo `requirements.txt` no repositório do projeto para que outros desenvolvedores possam replicar o ambiente.

4. **Use Ambientes Virtuais:**
   - Gere o `requirements.txt` a partir de um ambiente virtual para evitar dependências globais desnecessárias.

**Dicas:**
- Use o comando `pip list` para verificar os pacotes instalados antes de gerar o `requirements.txt`.
- Combine o `requirements.txt` com ambientes virtuais (`venv`) para manter seus projetos organizados e isolados.
- Consulte a [documentação oficial do `pip`](https://pip.pypa.io/en/stable/user_guide/#requirements-files) para mais detalhes sobre o uso do `requirements.txt`.

---

## 4. Criando Arquivos com Python + Context Manager `with`

O Python fornece ferramentas poderosas para criar, ler e manipular arquivos. O uso do **Context Manager `with`** simplifica o gerenciamento de arquivos, garantindo que eles sejam fechados corretamente.

### 4.1. O Que é a Função `open`?

- A função **`open`** é usada para abrir arquivos em Python.
- Ela pode abrir arquivos existentes ou criar novos arquivos, dependendo do modo especificado.

**Sintaxe:**
```py
open(caminho_arquivo, modo)
```

- **`caminho_arquivo`**: O caminho do arquivo a ser aberto.
- **`modo`**: O modo de abertura (ex.: leitura, escrita, etc.).

### 4.2. Modos de Abertura de Arquivos

| **Modo** | **Descrição**                                                                 |
|----------|-------------------------------------------------------------------------------|
| `r`      | Abre para leitura (erro se o arquivo não existir).                           |
| `w`      | Abre para escrita (cria o arquivo ou sobrescreve se já existir).             |
| `x`      | Abre para criação (erro se o arquivo já existir).                            |
| `a`      | Abre para escrita no final do arquivo (adiciona ao conteúdo existente).      |
| `b`      | Abre em modo binário.                                                        |
| `t`      | Abre em modo texto (padrão).                                                 |
| `+`      | Abre para leitura e escrita.                                                |

### 4.3. Usando o Context Manager `with`

O **Context Manager `with`** é usado para abrir arquivos de forma segura, garantindo que eles sejam fechados automaticamente após o uso.

**Exemplo:**
```py
caminho_arquivo = 'aula116.txt'

with open(caminho_arquivo, 'w') as arquivo:
    arquivo.write('Olá mundo\n')
    arquivo.write('Arquivo vai ser fechado automaticamente\n')
```

### 4.4. Métodos Úteis do `TextIOWrapper`

| **Método**       | **Descrição**                                                                 |
|-------------------|-------------------------------------------------------------------------------|
| `write`          | Escreve uma string no arquivo.                                               |
| `read`           | Lê o conteúdo do arquivo.                                                   |
| `writelines`     | Escreve várias linhas no arquivo.                                            |
| `readline`       | Lê uma única linha do arquivo.                                               |
| `readlines`      | Lê todas as linhas do arquivo e retorna uma lista.                           |
| `seek`           | Move o cursor para uma posição específica no arquivo.                       |

### 4.5. Exemplo Prático

**Código Completo:**
```py
caminho_arquivo = 'aula116.txt'

# Criando e escrevendo no arquivo
with open(caminho_arquivo, 'w+') as arquivo:
    arquivo.write('Linha 1\n')
    arquivo.write('Linha 2\n')
    arquivo.writelines(['Linha 3\n', 'Linha 4\n'])
    arquivo.seek(0, 0)  # Move o cursor para o início
    print(arquivo.read())  # Lê todo o conteúdo do arquivo

    print('Lendo linha por linha:')
    arquivo.seek(0, 0)
    print(arquivo.readline(), end='')  # Lê a primeira linha
    print(arquivo.readline().strip())  # Lê a segunda linha (sem quebra de linha)

    print('Lendo todas as linhas:')
    arquivo.seek(0, 0)
    for linha in arquivo.readlines():
        print(linha.strip())  # Remove espaços e quebras de linha

print('#' * 10)

# Lendo o arquivo novamente
with open(caminho_arquivo, 'r') as arquivo:
    print(arquivo.read())
```

**Saída:**
```
Linha 1
Linha 2
Linha 3
Linha 4

Lendo linha por linha:
Linha 1
Linha 2
Lendo todas as linhas:
Linha 1
Linha 2
Linha 3
Linha 4
##########
Linha 1
Linha 2
Linha 3
Linha 4
```

### 4.6. Operações com o Módulo `os`

O módulo **`os`** fornece funções para manipular arquivos e diretórios.

| **Função**         | **Descrição**                                                                 |
|---------------------|-------------------------------------------------------------------------------|
| `os.remove`         | Remove um arquivo.                                                          |
| `os.rename`         | Renomeia ou move um arquivo.                                                |

**Exemplo:**
```py
import os

# Renomeando o arquivo
os.rename('aula116.txt', 'novo_nome.txt')

# Removendo o arquivo
os.remove('novo_nome.txt')
```

### 4.7. Operações com o Módulo `json`

O módulo **`json`** é usado para trabalhar com arquivos JSON.

| **Função**         | **Descrição**                                                                 |
|---------------------|-------------------------------------------------------------------------------|
| `json.dump`         | Escreve um objeto Python em um arquivo JSON.                                |
| `json.load`         | Lê um arquivo JSON e converte para um objeto Python.                        |

**Exemplo:**
```py
import json

dados = {'nome': 'João', 'idade': 30}

# Salvando em um arquivo JSON
with open('dados.json', 'w') as arquivo:
    json.dump(dados, arquivo)

# Lendo o arquivo JSON
with open('dados.json', 'r') as arquivo:
    dados_carregados = json.load(arquivo)
    print(dados_carregados)
```

**Saída:**
```
{'nome': 'João', 'idade': 30}
```

**Dicas:**
- Sempre use o `with` para abrir arquivos, pois ele garante o fechamento automático.
- Combine o módulo `os` com `open` para manipular arquivos de forma eficiente.
- Use o módulo `json` para trabalhar com dados estruturados em formato JSON.
- Leia mais sobre normalização Unicode em Python: [Normalização Unicode](https://www.otaviomiranda.com.br/2020/normalizacao-unicode-em-python/).

---