# Módulos Python 5

## Sumário

1. [Enviando E-mails SMTP com Python](#1-enviando-e-mails-smtp-com-python)
    - 1.1. [O Que é SMTP?](#11-o-que-é-smtp)
    - 1.2. [Por Que Usar Python para Enviar E-mails?](#12-por-que-usar-python-para-enviar-e-mails)
    - 1.3. [Bibliotecas Utilizadas](#13-bibliotecas-utilizadas)
    - 1.4. [Exemplo Prático](#14-exemplo-prático)
    - 1.5. [Dicas e Boas Práticas](#15-dicas-e-boas-práticas)
2. [ZIP - Compactando / Descompactando Arquivos com `zipfile.ZipFile`](#2-zip---compactando--descompactando-arquivos-com-zipfilezipfile)
    - 2.1. [O Que é o Módulo `zipfile`?](#21-o-que-é-o-módulo-zipfile)
    - 2.2. [Por Que Usar o Módulo `zipfile`?](#22-por-que-usar-o-módulo-zipfile)
    - 2.3. [Principais Funções do Módulo `zipfile`](#23-principais-funções-do-módulo-zipfile)
    - 2.4. [Exemplo Prático](#24-exemplo-prático)
    - 2.5. [Dicas e Boas Práticas](#25-dicas-e-boas-práticas)
3. [sys.argv - Executando arquivos com argumentos no sistema](#3-sysargv---executando-arquivos-com-argumentos-no-sistema)
    - 3.1. [O Que é `sys.argv`?](#31-o-que-é-sysargv)
    - 3.2. [Por Que Usar `sys.argv`?](#32-por-que-usar-sysargv)
    - 3.3. [Exemplo Prático](#33-exemplo-prático)
    - 3.4. [Tratamento de Erros](#34-tratamento-de-erros)
    - 3.5. [Dicas e Boas Práticas](#35-dicas-e-boas-práticas)
4. [argparse.ArgumentParser - Argumentos mais complexos](#4-argparseargumentparser---argumentos-mais-complexos)
    - 4.1. [O Que é `argparse.ArgumentParser`?](#41-o-que-é-argparseargumentparser)
    - 4.2. [Por Que Usar `argparse.ArgumentParser`?](#42-por-que-usar-argparseargumentparser)
    - 4.3. [Exemplo Prático](#43-exemplo-prático)
    - 4.4. [Tratamento de Erros](#44-tratamento-de-erros)
    - 4.5. [Dicas e Boas Práticas](#45-dicas-e-boas-práticas)

---

## 1. Enviando E-mails SMTP com Python

### 1.1. O Que é SMTP?

- **SMTP (Simple Mail Transfer Protocol):**  
  É um protocolo usado para enviar e-mails entre servidores e clientes de e-mail.
- **Portas comuns:**  
  - `587`: Usada para envio de e-mails com criptografia TLS.
  - `465`: Usada para envio de e-mails com criptografia SSL.

### 1.2. Por Que Usar Python para Enviar E-mails?

- **Automatização:**  
  Permite enviar e-mails programaticamente, ideal para notificações, relatórios e alertas.
- **Flexibilidade:**  
  Suporta envio de e-mails simples ou complexos, incluindo anexos e HTML.
- **Integração:**  
  Facilita a integração com sistemas e APIs.

### 1.3. Bibliotecas Utilizadas

| **Biblioteca**              | **Descrição**                                                                 |
|-----------------------------|-------------------------------------------------------------------------------|
| `smtplib`                   | Permite enviar e-mails usando o protocolo SMTP.                              |
| `email.mime`                | Fornece classes para criar e-mails com texto, HTML e anexos.                 |
| `dotenv`                    | Carrega variáveis de ambiente de arquivos `.env`.                            |
| `os`                        | Permite acessar variáveis de ambiente e manipular caminhos.                  |

### 1.4. Exemplo Prático

```py
import os
import pathlib
import smtplib
from email.mime.multipart import MIMEMultipart
from email.mime.text import MIMEText
from string import Template
from dotenv import load_dotenv  # type: ignore

# Carregando variáveis de ambiente do arquivo .env
load_dotenv()

# Caminho do arquivo HTML
CAMINHO_HTML = pathlib.Path(__file__).parent / 'aula185.html'

# Dados do remetente e destinatário
remetente = os.getenv('FROM_EMAIL', '')
destinatario = remetente

# Configurações SMTP
smtp_server = 'smtp.gmail.com'
smtp_port = 587
smtp_username = os.getenv('FROM_EMAIL', '')
smtp_password = os.getenv('EMAIL_PASSWORD', '')

# Mensagem de texto
with open(CAMINHO_HTML, 'r') as arquivo:
    texto_arquivo = arquivo.read()
    template = Template(texto_arquivo)
    texto_email = template.substitute(nome='Helena')

# Transformar nossa mensagem em MIMEMultipart
mime_multipart = MIMEMultipart()
mime_multipart['from'] = remetente
mime_multipart['to'] = destinatario
mime_multipart['subject'] = 'Este é o assunto do e-mail'

corpo_email = MIMEText(texto_email, 'html', 'utf-8')
mime_multipart.attach(corpo_email)

# Envia o e-mail
with smtplib.SMTP(smtp_server, smtp_port) as server:
    server.ehlo()
    server.starttls()
    server.login(smtp_username, smtp_password)
    server.send_message(mime_multipart)
    print('E-mail enviado com sucesso!')
```

**Explicação:**
1. **Carregando variáveis de ambiente:**  
   `dotenv` é usado para carregar as credenciais do arquivo `.env`.
2. **Template HTML:**  
   O arquivo HTML é lido e processado com `string.Template` para substituir variáveis.
3. **MIMEMultipart:**  
   Cria uma mensagem de e-mail com suporte a múltiplas partes (ex.: texto e HTML).
4. **SMTP:**  
   Configura o servidor SMTP para enviar o e-mail com autenticação e criptografia TLS.

### 1.5. Dicas e Boas Práticas

- **Use `.env` para credenciais:**  
  Nunca inclua senhas ou informações sensíveis diretamente no código. Use arquivos `.env` e adicione-os ao `.gitignore`.
- **Valide os dados:**  
  Certifique-se de que os campos `remetente`, `destinatário` e `smtp_password` estão corretos antes de enviar o e-mail.
- **Teste com diferentes servidores SMTP:**  
  Certifique-se de que o código funciona com servidores como Gmail, Outlook, etc.
- **Documente os templates:**  
  Explique claramente as variáveis esperadas no arquivo HTML.
- **Use TLS ou SSL:**  
  Sempre use criptografia para proteger as informações durante o envio.

**Resumo:**  
Enviar e-mails com Python usando SMTP é uma solução poderosa e flexível para automatizar notificações e relatórios. Com bibliotecas como `smtplib`, `email.mime` e `dotenv`, é possível criar e-mails personalizados e seguros, integrando facilmente com diferentes sistemas.

---

## 2. ZIP - Compactando / Descompactando Arquivos com `zipfile.ZipFile`

### 2.1. O Que é o Módulo `zipfile`?

- **`zipfile`:**  
  É um módulo da biblioteca padrão do Python que permite criar, ler, escrever e extrair arquivos ZIP.
- **Arquivos ZIP:**  
  São arquivos compactados que podem conter múltiplos arquivos e diretórios, reduzindo o tamanho e facilitando o transporte.

### 2.2. Por Que Usar o Módulo `zipfile`?

- **Compactação:**  
  Reduz o tamanho de arquivos e diretórios para economizar espaço e facilitar o envio.
- **Organização:**  
  Permite agrupar múltiplos arquivos em um único arquivo ZIP.
- **Flexibilidade:**  
  Suporta operações como leitura, escrita e extração de arquivos ZIP.

### 2.3. Principais Funções do Módulo `zipfile`

| **Função**                  | **Descrição**                                                                 |
|-----------------------------|-------------------------------------------------------------------------------|
| `ZipFile(filename, mode)`   | Abre ou cria um arquivo ZIP.                                                  |
| `write(filename, arcname)`  | Adiciona um arquivo ao ZIP.                                                   |
| `namelist()`                | Retorna uma lista com os nomes dos arquivos no ZIP.                          |
| `extractall(path)`          | Extrai todos os arquivos do ZIP para o diretório especificado.               |
| `extract(member, path)`     | Extrai um arquivo específico do ZIP.                                         |

---

### 1.4. Exemplo Prático

```py
import os
import shutil
from pathlib import Path
from zipfile import ZipFile

# Caminhos
CAMINHO_RAIZ = Path(__file__).parent
CAMINHO_ZIP_DIR = CAMINHO_RAIZ / 'aula_186_diretorio_zip'
CAMINHO_COMPACTADO = CAMINHO_RAIZ / 'aula186_compactado.zip'
CAMINHO_DESCOMPACTADO = CAMINHO_RAIZ / 'aula186_descompactado'

# Limpeza inicial
shutil.rmtree(CAMINHO_ZIP_DIR, ignore_errors=True)
Path.unlink(CAMINHO_COMPACTADO, missing_ok=True)
shutil.rmtree(CAMINHO_DESCOMPACTADO, ignore_errors=True)

# Cria o diretório para a aula
CAMINHO_ZIP_DIR.mkdir(exist_ok=True)

# Função para criar arquivos no diretório
def criar_arquivos(qtd: int, zip_dir: Path):
    for i in range(qtd):
        texto = f'arquivo_{i}'
        with open(zip_dir / f'{texto}.txt', 'w') as arquivo:
            arquivo.write(texto)

criar_arquivos(10, CAMINHO_ZIP_DIR)

# Compactando arquivos em um ZIP
with ZipFile(CAMINHO_COMPACTADO, 'w') as zip:
    for root, dirs, files in os.walk(CAMINHO_ZIP_DIR):
        for file in files:
            zip.write(os.path.join(root, file), file)

# Lendo arquivos de um ZIP
with ZipFile(CAMINHO_COMPACTADO, 'r') as zip:
    for arquivo in zip.namelist():
        print(f"Arquivo no ZIP: {arquivo}")

# Extraindo arquivos de um ZIP
with ZipFile(CAMINHO_COMPACTADO, 'r') as zip:
    zip.extractall(CAMINHO_DESCOMPACTADO)
    print(f"Arquivos extraídos para: {CAMINHO_DESCOMPACTADO}")
```

**Explicação:**
1. **Criação de arquivos:**  
   A função `criar_arquivos` cria 10 arquivos de texto no diretório especificado.
2. **Compactação:**  
   `ZipFile` é usado para criar um arquivo ZIP e adicionar os arquivos criados.
3. **Leitura:**  
   `namelist()` retorna os nomes dos arquivos no ZIP.
4. **Extração:**  
   `extractall()` extrai todos os arquivos do ZIP para o diretório especificado.

### 2.5. Dicas e Boas Práticas

- **Use `Path` para manipular caminhos:**  
  Prefira usar `pathlib.Path` para garantir portabilidade entre sistemas operacionais.
- **Valide os arquivos antes de compactar:**  
  Certifique-se de que os arquivos existem e estão acessíveis.
- **Documente os caminhos:**  
  Explique claramente os diretórios e arquivos usados no código.
- **Teste com diferentes tamanhos de arquivos:**  
  Certifique-se de que o código funciona corretamente com arquivos pequenos e grandes.
- **Evite sobrescrever arquivos:**  
  Use `missing_ok=True` ou valide antes de excluir ou criar arquivos.

**Resumo:**  
O módulo `zipfile` é uma ferramenta poderosa para compactar e descompactar arquivos em Python. Ele permite criar arquivos ZIP, listar seu conteúdo e extrair arquivos de forma eficiente e organizada.

---

## 3. sys.argv - Executando arquivos com argumentos no sistema

### 3.1. O Que é `sys.argv`?

- **`sys.argv`:**  
  É uma lista fornecida pelo módulo `sys` que contém os argumentos passados para o script Python via linha de comando.
- **Estrutura:**  
  O primeiro elemento (`sys.argv[0]`) é sempre o nome do script, seguido pelos argumentos fornecidos pelo usuário.

### 3.2. Por Que Usar `sys.argv`?

- **Automatização:**  
  Permite que scripts sejam configurados dinamicamente com base nos argumentos fornecidos.
- **Flexibilidade:**  
  Facilita a execução de scripts com diferentes parâmetros sem necessidade de modificar o código.
- **Interatividade:**  
  Torna o script mais interativo e adaptável a diferentes cenários.

### 3.3. Exemplo Prático

```python
import sys

# Captura os argumentos da linha de comando
argumentos = sys.argv
qtd_argumentos = len(argumentos)

if qtd_argumentos <= 1:
    print('Nenhum argumento foi passado.')
else:
    try:
        print(f'Você passou os argumentos: {argumentos[1:]}')
        print(f'Faça alguma coisa com o argumento: {argumentos[1]}')
        print(f'Faça outra coisa com o argumento: {argumentos[2]}')
    except IndexError:
        print('Faltam argumentos para executar todas as ações.')
```

**Execução:**
1. **Sem argumentos:**  
   ```bash
   python script.py
   ```
   Saída:  
   ```
   Nenhum argumento foi passado.
   ```

2. **Com argumentos:**  
   ```bash
   python script.py valor1 valor2
   ```
   Saída:  
   ```
   Você passou os argumentos: ['valor1', 'valor2']
   Faça alguma coisa com o argumento: valor1
   Faça outra coisa com o argumento: valor2
   ```

### 3.4. Tratamento de Erros

- **Erro de Índice (`IndexError`):**  
  Ocorre quando o script tenta acessar um argumento que não foi fornecido.  
  Exemplo:  
  ```python
  try:
      print(argumentos[2])
  except IndexError:
      print('Faltam argumentos.')
  ```

- **Validação de Argumentos:**  
  Certifique-se de validar os argumentos antes de utilizá-los.  
  Exemplo:  
  ```python
  if len(argumentos) < 3:
      print('Por favor, forneça pelo menos dois argumentos além do nome do script.')
  ```

### 3.5. Dicas e Boas Práticas

- **Use `argparse` para scripts complexos:**  
  Para casos com muitos argumentos ou opções, prefira o módulo `argparse`, que oferece mais funcionalidades e validações.
- **Documente os argumentos esperados:**  
  Inclua instruções claras sobre quais argumentos o script espera e como utilizá-los.
- **Valide os tipos de dados:**  
  Certifique-se de que os argumentos fornecidos são do tipo esperado (ex.: números, strings).
- **Teste com diferentes cenários:**  
  Execute o script com diferentes combinações de argumentos para garantir robustez.
- **Evite dependência de ordem:**  
  Sempre valide os argumentos pelo nome ou posição, mas considere usar `argparse` para maior flexibilidade.

**Resumo:**  
O `sys.argv` é uma ferramenta simples e poderosa para capturar argumentos de linha de comando em Python. Ele é ideal para scripts rápidos e interativos, mas para casos mais complexos, o uso de `argparse` é recomendado.

---

## 4. argparse.ArgumentParser - Argumentos mais complexos

### 4.1. O Que é `argparse.ArgumentParser`?

- **`argparse.ArgumentParser`:**  
  É uma classe do módulo `argparse` que facilita a criação de scripts Python que aceitam argumentos de linha de comando.
- **Funcionalidade:**  
  Permite definir, validar e processar argumentos fornecidos pelo usuário ao executar o script.

### 4.2. Por Que Usar `argparse.ArgumentParser`?

- **Automatização:**  
  Facilita a execução de scripts com diferentes configurações sem modificar o código.
- **Validação:**  
  Garante que os argumentos fornecidos pelo usuário sejam válidos e no formato esperado.
- **Flexibilidade:**  
  Suporta argumentos obrigatórios, opcionais, múltiplos valores e ações personalizadas.

### 4.3. Exemplo Prático

```python
from argparse import ArgumentParser

# Criando o parser
parser = ArgumentParser(description="Exemplo de uso do argparse para argumentos complexos.")

# Adicionando argumentos
parser.add_argument(
    '-b', '--basic',
    help='Mostra "Olá mundo" na tela',
    metavar='STRING',  # Nome exibido no texto de ajuda
    required=False,    # Define se o argumento é obrigatório
    action='append',   # Permite múltiplos valores
)

parser.add_argument(
    '-v', '--verbose',
    help='Mostra logs detalhados',
    action='store_true'  # Define como booleano
)

# Processando os argumentos
args = parser.parse_args()

# Exibindo os valores dos argumentos
if args.basic is None:
    print('Você não passou o valor de basic.')
else:
    print('O valor de basic:', args.basic)

print('Verbose está ativado:', args.verbose)
```

**Execução:**
1. **Sem argumentos:**  
   ```bash
   python script.py
   ```
   Saída:  
   ```
   Você não passou o valor de basic.
   Verbose está ativado: False
   ```

2. **Com argumentos:**  
   ```bash
   python script.py -b "Olá mundo" -v
   ```
   Saída:  
   ```
   O valor de basic: ['Olá mundo']
   Verbose está ativado: True
   ```

3. **Múltiplos valores para `basic`:**  
   ```bash
   python script.py -b "Olá mundo" -b "Python é incrível"
   ```
   Saída:  
   ```
   O valor de basic: ['Olá mundo', 'Python é incrível']
   Verbose está ativado: False
   ```

### 4.4. Tratamento de Erros

- **Erro de Argumento Inválido:**  
  Ocorre quando o usuário fornece um valor que não corresponde ao tipo esperado.  
  Solução: Use o parâmetro `type` para validar o tipo do argumento.

- **Erro de Argumento Obrigatório:**  
  Ocorre quando um argumento obrigatório não é fornecido.  
  Solução: Certifique-se de que o usuário forneça o argumento obrigatório.

### 4.5. Dicas e Boas Práticas

- **Use `description` e `help`:**  
  Sempre forneça descrições claras para o script e para os argumentos.
- **Valide os Tipos de Dados:**  
  Utilize o parâmetro `type` para garantir que os argumentos sejam do tipo esperado.
- **Defina Valores Padrão:**  
  Use o parâmetro `default` para evitar erros quando argumentos opcionais não forem fornecidos.
- **Teste o Script:**  
  Execute o script com diferentes combinações de argumentos para garantir que ele funcione como esperado.
- **Use `action='append'` para múltiplos valores:**  
  Permite que o mesmo argumento seja fornecido várias vezes e os valores sejam acumulados.

**Resumo:**  
O `argparse.ArgumentParser` é ideal para criar scripts Python interativos e configuráveis. Ele suporta argumentos complexos, validações e ações personalizadas, tornando-o uma ferramenta indispensável para automação e desenvolvimento de scripts robustos.

---