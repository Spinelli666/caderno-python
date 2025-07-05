# Módulos Python 6

## Sumário

1. [Básico do Protocolo HTTP (HyperText Transfer Protocol)](#1-básico-do-protocolo-http-hypertext-transfer-protocol)
    - 1.1. [O Que é o Protocolo HTTP?](#11-o-que-é-o-protocolo-http)
    - 1.2. [Como Funciona o HTTP?](#12-como-funciona-o-http)
    - 1.3. [Métodos HTTP](#13-métodos-http)
    - 1.4. [Códigos de Status HTTP](#14-códigos-de-status-http)
    - 1.5. [Dicas e Boas Práticas](#15-dicas-e-boas-práticas)
2. [Requests para Requisições HTTP com Python](#2-requests-para-requisições-http-com-python)
    - 2.1. [O Que é a Biblioteca `requests`?](#21-o-que-é-a-biblioteca-requests)
    - 2.2. [Instalação e Configuração](#22-instalação-e-configuração)
    - 2.3. [Objeto Response](#23-objeto-response)
    - 2.4. [Exemplo Prático](#24-exemplo-prático)
    - 2.5. [Dicas e Boas Práticas](#25-dicas-e-boas-práticas)
3. [Web Scraping com Python usando requests e BeautifulSoup](#3-web-scraping-com-python-usando-requests-e-beautifulsoup)
    - 3.1. [O Que é Web Scraping?](#31-o-que-é-web-scraping)
    - 3.2. [Instalação e Configuração](#32-instalação-e-configuração)
    - 3.3. [BeautifulSoup - Principais Métodos](#33-beautifulsoup---principais-métodos)
    - 3.4. [Exemplo Prático](#34-exemplo-prático)
    - 3.5. [Dicas e Boas Práticas](#35-dicas-e-boas-práticas)

---

## 1. Básico do Protocolo HTTP (HyperText Transfer Protocol)

### 1.1. O Que é o Protocolo HTTP?

- **HTTP (HyperText Transfer Protocol):**  
  É um protocolo de comunicação usado para enviar e receber dados na Internet.
- **Arquitetura Cliente/Servidor:**  
  Funciona no modelo cliente/servidor, onde o cliente (navegador, aplicação) faz requisições ao servidor (site, API), que responde com os dados adequados.

### 1.2. Como Funciona o HTTP?

- **Requisição do Cliente:**  
  O cliente envia uma mensagem de requisição que deve incluir:
  - **Método HTTP:** Define a ação a ser realizada (GET, POST, PUT, etc.).
  - **Endereço do recurso:** Caminho para o recurso desejado (ex.: `/users/`).
  - **Cabeçalhos HTTP:** Metadados da requisição (Content-Type, Authorization).
  - **Corpo da mensagem:** Dados enviados (quando necessário, dependendo do método).

- **Resposta do Servidor:**  
  O servidor retorna uma mensagem de resposta que inclui:
  - **Código de status HTTP:** Indica o resultado da requisição (200, 404, 500, etc.).
  - **Cabeçalhos HTTP:** Metadados da resposta (Content-Type, Accept).
  - **Corpo da mensagem:** Dados retornados (pode estar vazio em alguns casos).

### 1.3. Métodos HTTP

#### Métodos de Leitura (Safe)
| **Método** | **Descrição**                                                                 |
|------------|-------------------------------------------------------------------------------|
| `GET`      | Obtém dados do servidor. Não modifica o estado do servidor.                  |
| `HEAD`     | Obtém apenas os cabeçalhos da resposta, sem o corpo da mensagem.             |
| `OPTIONS`  | Obtém informações sobre os métodos HTTP suportados pelo recurso.             |

#### Métodos de Escrita
| **Método** | **Descrição**                                                                 |
|------------|-------------------------------------------------------------------------------|
| `POST`     | Envia dados para o servidor para criar um novo recurso.                      |
| `PUT`      | Substitui completamente um recurso existente ou cria um novo.                |
| `PATCH`    | Atualiza parcialmente um recurso existente.                                  |
| `DELETE`   | Remove um recurso do servidor.                                               |

### 1.4. Códigos de Status HTTP

#### Códigos de Sucesso (2xx)
| **Código** | **Descrição**                                                                 |
|------------|-------------------------------------------------------------------------------|
| `200`      | OK - Requisição bem-sucedida.                                                |
| `201`      | Created - Recurso criado com sucesso.                                        |
| `204`      | No Content - Requisição bem-sucedida, mas sem conteúdo para retornar.       |

#### Códigos de Erro do Cliente (4xx)
| **Código** | **Descrição**                                                                 |
|------------|-------------------------------------------------------------------------------|
| `400`      | Bad Request - Requisição malformada.                                         |
| `401`      | Unauthorized - Autenticação necessária.                                      |
| `403`      | Forbidden - Acesso negado.                                                   |
| `404`      | Not Found - Recurso não encontrado.                                          |

#### Códigos de Erro do Servidor (5xx)
| **Código** | **Descrição**                                                                 |
|------------|-------------------------------------------------------------------------------|
| `500`      | Internal Server Error - Erro interno do servidor.                            |
| `502`      | Bad Gateway - Erro de gateway.                                               |
| `503`      | Service Unavailable - Serviço indisponível.                                  |

**Documentação oficial:**  
[https://developer.mozilla.org/en-US/docs/Web/HTTP/Status](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)

### 1.5. Dicas e Boas Práticas

- **Use o método HTTP adequado:**  
  Escolha o método correto baseado na ação que deseja realizar (GET para leitura, POST para criação, etc.).
- **Valide códigos de status:**  
  Sempre verifique os códigos de status nas respostas para tratar erros adequadamente.
- **Configure cabeçalhos corretos:**  
  Use cabeçalhos apropriados como `Content-Type` para especificar o formato dos dados.
- **Trate erros de forma adequada:**  
  Implemente tratamento de erros para códigos 4xx e 5xx.
- **Documente suas APIs:**  
  Se estiver criando uma API, documente claramente os endpoints, métodos e códigos de resposta esperados.

**Resumo:**  
O protocolo HTTP é fundamental para comunicação na web, funcionando no modelo cliente/servidor. Compreender seus métodos, códigos de status e estrutura de mensagens é essencial para desenvolvimento web e integração com APIs.

---

## 2. Requests para Requisições HTTP com Python

### 2.1. O Que é a Biblioteca `requests`?

- **`requests`:**  
  É uma biblioteca Python para fazer requisições HTTP de forma simples e elegante.
- **Facilidade de uso:**  
  Oferece uma API intuitiva para trabalhar com requisições HTTP, incluindo GET, POST, PUT, DELETE, etc.
- **Funcionalidades:**  
  Suporta autenticação, cookies, redirecionamentos, timeouts e muito mais.

**Tutorial oficial:**  
[https://youtu.be/Qd8JT0bnJGs](https://youtu.be/Qd8JT0bnJGs)

### 2.2. Instalação e Configuração

- **Instalação:**  
  ```bash
  pip install requests
  ```
- **Importação:**  
  ```python
  import requests
  ```

#### Portas Padrão HTTP/HTTPS
| **Protocolo** | **Porta Padrão** | **Descrição**                                          |
|---------------|------------------|--------------------------------------------------------|
| `http://`     | 80               | Protocolo HTTP não criptografado.                     |
| `https://`    | 443              | Protocolo HTTPS com criptografia SSL/TLS.             |

### 2.3. Objeto Response

Quando você faz uma requisição com `requests`, ele retorna um objeto `Response` que contém:

| **Atributo/Método** | **Descrição**                                                         |
|---------------------|-----------------------------------------------------------------------|
| `status_code`       | Código de status HTTP da resposta (200, 404, 500, etc.).            |
| `headers`           | Cabeçalhos HTTP da resposta.                                         |
| `content`           | Conteúdo da resposta em bytes.                                       |
| `text`              | Conteúdo da resposta como string (decodificado).                     |
| `json()`            | Converte o conteúdo JSON da resposta em um dicionário Python.        |

### 2.4. Exemplo Prático

```python
import requests

# URLs com protocolos diferentes
# http:// -> Roda automaticamente na porta 80
# https:// -> Roda automaticamente na porta 443

url = 'http://127.0.0.1:5500/aulas/aula190_site/index.html'
response = requests.get(url)

# Verificando o código de status
print(f"Status Code: {response.status_code}")

# Visualizando os cabeçalhos
print("Headers:")
for header, value in response.headers.items():
    print(f"  {header}: {value}")

# Conteúdo da resposta como texto
print("Conteúdo (texto):")
print(response.text)

# Se a resposta for JSON, você pode usar:
# data = response.json()
# print(data)
```

**Execução:**
1. **Status Code:**  
   Exibe o código de status da requisição (200 para sucesso, 404 para não encontrado, etc.).

2. **Headers:**  
   Mostra todos os cabeçalhos HTTP retornados pelo servidor.

3. **Conteúdo:**  
   Exibe o conteúdo da página como texto (HTML, JSON, etc.).

### 2.5. Dicas e Boas Práticas

- **Verifique o status code:**  
  Sempre verifique se a requisição foi bem-sucedida antes de processar a resposta.
  ```python
  if response.status_code == 200:
      print("Requisição bem-sucedida!")
  else:
      print(f"Erro: {response.status_code}")
  ```

- **Use timeouts:**  
  Defina um timeout para evitar que o programa trave em requisições longas.
  ```python
  response = requests.get(url, timeout=5)
  ```

- **Trate exceções:**  
  Implemente tratamento de erros para conexões e timeouts.
  ```python
  try:
      response = requests.get(url, timeout=5)
      response.raise_for_status()  # Levanta exceção para códigos de erro
  except requests.exceptions.RequestException as e:
      print(f"Erro na requisição: {e}")
  ```

- **Use `response.json()` para APIs:**  
  Quando trabalhar com APIs que retornam JSON, use o método `json()` para converter automaticamente.

- **Configure headers quando necessário:**  
  Alguns serviços requerem headers específicos (User-Agent, Authorization, etc.).
  ```python
  headers = {'User-Agent': 'Meu App 1.0'}
  response = requests.get(url, headers=headers)
  ```

**Resumo:**  
A biblioteca `requests` é a ferramenta padrão para fazer requisições HTTP em Python. Ela oferece uma interface simples e poderosa para interagir com APIs e serviços web, suportando todos os métodos HTTP e funcionalidades avançadas como autenticação e timeouts.

---

## 3. Web Scraping com Python usando requests e BeautifulSoup

### 3.1. O Que é Web Scraping?

- **Web Scraping:**  
  É o ato de "raspar a web" buscando informações de forma automatizada, com determinada linguagem de programação, para uso posterior.
- **Objetivo:**  
  Extrair dados estruturados de páginas web para análise, armazenamento ou processamento.
- **Ferramentas:**  
  - **`requests`:** Carrega dados da Internet para dentro do código Python.
  - **`BeautifulSoup`:** Interpreta dados HTML em formato de objetos Python para facilitar a manipulação.

**Documentação oficial:**  
[https://www.crummy.com/software/BeautifulSoup/bs4/doc.ptbr/](https://www.crummy.com/software/BeautifulSoup/bs4/doc.ptbr/)

---

### 3.2. Instalação e Configuração

- **Instalação:**  
  ```bash
  pip install requests types-requests bs4
  ```

- **Importação:**  
  ```python
  import requests
  from bs4 import BeautifulSoup
  import re  # Para expressões regulares
  ```

---

### 3.3. BeautifulSoup - Principais Métodos

| **Método**                | **Descrição**                                                         |
|---------------------------|-----------------------------------------------------------------------|
| `BeautifulSoup(html, parser)` | Cria um objeto BeautifulSoup a partir do HTML.                   |
| `find(tag, attrs)`        | Encontra o primeiro elemento que corresponde aos critérios.          |
| `find_all(tag, attrs)`    | Encontra todos os elementos que correspondem aos critérios.          |
| `select(css_selector)`    | Encontra elementos usando seletores CSS.                             |
| `select_one(css_selector)` | Encontra o primeiro elemento usando seletores CSS.                  |
| `text`                    | Extrai o texto de um elemento, removendo as tags HTML.               |
| `get(attr)`               | Obtém o valor de um atributo específico de um elemento.              |

#### Parsers Disponíveis
| **Parser**     | **Descrição**                                                         |
|----------------|-----------------------------------------------------------------------|
| `html.parser`  | Parser HTML nativo do Python (recomendado para a maioria dos casos). |
| `lxml`         | Parser mais rápido, requer instalação separada (`pip install lxml`). |
| `xml`          | Parser para documentos XML.                                           |

---

### 3.4. Exemplo Prático

```python
import re
import requests
from bs4 import BeautifulSoup

# URL do site a ser "raspado"
url = 'https://www.python.org/'
response = requests.get(url)
raw_html = response.text

# Criando objeto BeautifulSoup
parsed_html = BeautifulSoup(raw_html, 'html.parser')

# Extraindo o título da página
if parsed_html.title is not None:
    print(f"Título da página: {parsed_html.title.text}")

# Selecionando elementos específicos com CSS selector
headings = parsed_html.select_one('div.small-widget:nth-child(1) > h2:nth-child(1)')

if headings is not None:
    article = headings.parent
    
    if article is not None:
        print(f"Seção encontrada: {headings.text}")
        
        # Extraindo todos os parágrafos da seção
        for p in article.select('p'):
            # Limpando espaços extras e quebras de linha
            clean_text = re.sub(r'\s{1,}', ' ', p.text).strip()
            print(f"- {clean_text}")
```

**Execução:**
1. **Requisição HTTP:**  
   Faz uma requisição GET para obter o HTML da página.

2. **Parsing HTML:**  
   Converte o HTML bruto em um objeto BeautifulSoup para manipulação.

3. **Seleção de elementos:**  
   Usa seletores CSS para encontrar elementos específicos na página.

4. **Extração de texto:**  
   Extrai e limpa o texto dos elementos encontrados, removendo espaços extras.

---

### 3.5. Dicas e Boas Práticas

- **Respeite o robots.txt:**  
  Sempre verifique o arquivo `robots.txt` do site para saber quais páginas podem ser acessadas.
  ```python
  robots_url = 'https://www.example.com/robots.txt'
  ```

- **Use delays entre requisições:**  
  Evite sobrecarregar o servidor com muitas requisições simultâneas.
  ```python
  import time
  time.sleep(1)  # Pausa de 1 segundo entre requisições
  ```

- **Configure User-Agent:**  
  Alguns sites bloqueiam requisições sem User-Agent adequado.
  ```python
  headers = {
      'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36'
  }
  response = requests.get(url, headers=headers)
  ```

- **Trate exceções:**  
  Implemente tratamento de erros para conexões e parsing.
  ```python
  try:
      response = requests.get(url, timeout=10)
      response.raise_for_status()
      soup = BeautifulSoup(response.text, 'html.parser')
  except requests.exceptions.RequestException as e:
      print(f"Erro na requisição: {e}")
  ```

- **Valide elementos antes de acessar:**  
  Sempre verifique se os elementos existem antes de tentar acessá-los.
  ```python
  element = soup.find('div', class_='content')
  if element is not None:
      print(element.text)
  ```

- **Use expressões regulares para limpeza:**  
  Limpe o texto extraído removendo espaços extras e caracteres indesejados.
  ```python
  import re
  clean_text = re.sub(r'\s+', ' ', raw_text).strip()
  ```

**Resumo:**  
Web Scraping com Python usando `requests` e `BeautifulSoup` é uma técnica poderosa para extrair dados de páginas web. É importante seguir boas práticas éticas e técnicas para criar scrapers eficientes e responsáveis.

---

