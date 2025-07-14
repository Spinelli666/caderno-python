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
4. [Selenium - Automatizando Tarefas no Navegador](#4-selenium---automatizando-tarefas-no-navegador)
    - 4.1. [O Que é o Selenium?](#41-o-que-é-o-selenium)
    - 4.2. [Instalação e Configuração](#42-instalação-e-configuração)
    - 4.3. [Localizadores (By) no Selenium](#43-localizadores-by-no-selenium)
    - 4.4. [Métodos de Busca de Elementos](#44-métodos-de-busca-de-elementos)
    - 4.5. [WebDriverWait e Expected Conditions](#45-webdriverwait-e-expected-conditions)
    - 4.6. [Enviando Teclas com a Classe Keys](#46-enviando-teclas-com-a-classe-keys)
    - 4.7. [Exemplo Prático Completo](#47-exemplo-prático-completo)
    - 4.8. [Dicas e Boas Práticas](#48-dicas-e-boas-práticas)

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

## 4. Selenium - Automatizando Tarefas no Navegador

### 4.1. O Que é o Selenium?

O **Selenium** é uma ferramenta de automação de navegador web que permite controlar um navegador programaticamente. É especialmente útil para:

- Automatizar tarefas repetitivas em sites
- Realizar testes de aplicações web
- Fazer web scraping de sites com JavaScript
- Preencher formulários automaticamente
- Navegar por páginas que exigem interação

### 4.2. Instalação e Configuração

#### Instalação do Selenium

```bash
pip install selenium
```

#### Instalação do WebDriver

| Navegador | WebDriver | Download |
|-----------|-----------|----------|
| Chrome | ChromeDriver | https://chromedriver.chromium.org/ |
| Firefox | GeckoDriver | https://github.com/mozilla/geckodriver/releases |
| Edge | EdgeDriver | https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/ |
| Safari | SafariDriver | Já incluído no macOS |

#### Configuração Básica

```python
from selenium import webdriver
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.chrome.options import Options

# Configurações opcionais do Chrome
chrome_options = Options()
chrome_options.add_argument("--headless")  # Executar sem interface gráfica
chrome_options.add_argument("--no-sandbox")
chrome_options.add_argument("--disable-dev-shm-usage")

# Inicializar o driver
driver = webdriver.Chrome(options=chrome_options)

# Exemplo básico
driver.get("https://www.google.com")
print(driver.title)
driver.quit()
```

### 4.3. Localizadores (By) no Selenium

O Selenium usa a classe `By` para localizar elementos na página:

| Localizador | Método | Exemplo |
|-------------|---------|---------|
| `By.ID` | Por ID do elemento | `driver.find_element(By.ID, "username")` |
| `By.NAME` | Por atributo name | `driver.find_element(By.NAME, "email")` |
| `By.CLASS_NAME` | Por classe CSS | `driver.find_element(By.CLASS_NAME, "btn-primary")` |
| `By.TAG_NAME` | Por tag HTML | `driver.find_element(By.TAG_NAME, "h1")` |
| `By.CSS_SELECTOR` | Por seletor CSS | `driver.find_element(By.CSS_SELECTOR, ".class > p")` |
| `By.XPATH` | Por XPath | `driver.find_element(By.XPATH, "//input[@type='password']")` |
| `By.LINK_TEXT` | Por texto do link | `driver.find_element(By.LINK_TEXT, "Clique aqui")` |
| `By.PARTIAL_LINK_TEXT` | Por texto parcial do link | `driver.find_element(By.PARTIAL_LINK_TEXT, "Clique")` |

```python
from selenium.webdriver.common.by import By

# Exemplos de uso
element = driver.find_element(By.ID, "meu-id")
elements = driver.find_elements(By.CLASS_NAME, "minha-classe")
```

### 4.4. Métodos de Busca de Elementos

| Método | Descrição | Retorno |
|--------|-----------|---------|
| `find_element()` | Encontra o primeiro elemento | WebElement |
| `find_elements()` | Encontra todos os elementos | Lista de WebElements |

#### Métodos de Interação com Elementos

```python
# Buscar elemento
elemento = driver.find_element(By.ID, "campo-texto")

# Interações básicas
elemento.click()                    # Clicar
elemento.send_keys("texto")         # Digitar texto
elemento.clear()                    # Limpar campo
elemento.submit()                   # Enviar formulário

# Obter informações
texto = elemento.text               # Texto do elemento
atributo = elemento.get_attribute("href")  # Valor de atributo
esta_visivel = elemento.is_displayed()     # Verificar se está visível
esta_habilitado = elemento.is_enabled()    # Verificar se está habilitado
```

### 4.5. WebDriverWait e Expected Conditions

Para aguardar elementos aparecerem na página:

```python
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

# Configurar wait
wait = WebDriverWait(driver, 10)  # Aguardar até 10 segundos

# Aguardar elemento estar presente
elemento = wait.until(EC.presence_of_element_located((By.ID, "meu-id")))

# Aguardar elemento estar clicável
elemento = wait.until(EC.element_to_be_clickable((By.CLASS_NAME, "btn")))

# Aguardar elemento estar visível
elemento = wait.until(EC.visibility_of_element_located((By.XPATH, "//div[@class='content']")))
```

#### Expected Conditions Mais Usados

| Condição | Descrição |
|----------|-----------|
| `presence_of_element_located` | Elemento presente no DOM |
| `visibility_of_element_located` | Elemento visível na página |
| `element_to_be_clickable` | Elemento clicável |
| `text_to_be_present_in_element` | Texto específico presente no elemento |
| `title_is` | Título da página igual ao especificado |

### 4.6. Enviando Teclas com a Classe Keys

```python
from selenium.webdriver.common.keys import Keys

# Teclas especiais
elemento.send_keys(Keys.ENTER)      # Enter
elemento.send_keys(Keys.TAB)        # Tab
elemento.send_keys(Keys.ESCAPE)     # Escape
elemento.send_keys(Keys.BACKSPACE)  # Backspace
elemento.send_keys(Keys.DELETE)     # Delete

# Combinações de teclas
elemento.send_keys(Keys.CONTROL + "a")  # Ctrl + A
elemento.send_keys(Keys.CONTROL + "c")  # Ctrl + C
elemento.send_keys(Keys.CONTROL + "v")  # Ctrl + V

# Teclas de navegação
elemento.send_keys(Keys.ARROW_DOWN)
elemento.send_keys(Keys.ARROW_UP)
elemento.send_keys(Keys.PAGE_DOWN)
elemento.send_keys(Keys.HOME)
elemento.send_keys(Keys.END)
```

### 4.7. Exemplo Prático Completo

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from selenium.webdriver.chrome.options import Options
import time

def buscar_no_google(termo_busca):
    """
    Exemplo de automação: buscar um termo no Google
    """
    # Configurar opções do Chrome
    options = Options()
    options.add_argument("--headless")  # Executar sem interface gráfica
    
    # Inicializar driver
    driver = webdriver.Chrome(options=options)
    wait = WebDriverWait(driver, 10)
    
    try:
        # Acessar Google
        driver.get("https://www.google.com")
        print(f"Título da página: {driver.title}")
        
        # Encontrar campo de busca
        campo_busca = wait.until(
            EC.presence_of_element_located((By.NAME, "q"))
        )
        
        # Digite termo e pressione Enter
        campo_busca.send_keys(termo_busca)
        campo_busca.send_keys(Keys.RETURN)
        
        # Aguardar resultados carregarem
        wait.until(
            EC.presence_of_element_located((By.ID, "search"))
        )
        
        # Coletar primeiros resultados
        resultados = driver.find_elements(By.CSS_SELECTOR, "h3")
        
        print(f"\nPrimeiros 5 resultados para '{termo_busca}':")
        for i, resultado in enumerate(resultados[:5], 1):
            print(f"{i}. {resultado.text}")
        
        # Tirar screenshot
        driver.save_screenshot("busca_google.png")
        print(f"\nScreenshot salvo como 'busca_google.png'")
        
    except Exception as e:
        print(f"Erro durante a execução: {e}")
    
    finally:
        # Sempre fechar o driver
        driver.quit()

# Executar exemplo
if __name__ == "__main__":
    buscar_no_google("Python Selenium tutorial")
```

#### Exemplo de Preenchimento de Formulário

```python
def preencher_formulario():
    driver = webdriver.Chrome()
    wait = WebDriverWait(driver, 10)
    
    try:
        # Acessar página com formulário
        driver.get("https://exemplo.com/formulario")
        
        # Preencher campos
        nome = wait.until(EC.presence_of_element_located((By.ID, "nome")))
        nome.send_keys("João Silva")
        
        email = driver.find_element(By.ID, "email")
        email.send_keys("joao@email.com")
        
        # Selecionar dropdown
        from selenium.webdriver.support.ui import Select
        dropdown = Select(driver.find_element(By.ID, "pais"))
        dropdown.select_by_visible_text("Brasil")
        
        # Marcar checkbox
        checkbox = driver.find_element(By.ID, "aceito-termos")
        if not checkbox.is_selected():
            checkbox.click()
        
        # Enviar formulário
        botao_enviar = driver.find_element(By.CSS_SELECTOR, "button[type='submit']")
        botao_enviar.click()
        
        # Aguardar confirmação
        mensagem = wait.until(
            EC.visibility_of_element_located((By.CLASS_NAME, "mensagem-sucesso"))
        )
        print(f"Formulário enviado: {mensagem.text}")
        
    finally:
        driver.quit()
```

### 4.8. Dicas e Boas Práticas

#### ✅ Boas Práticas

1. **Sempre use WebDriverWait**: Evite `time.sleep()`, use esperações explícitas
2. **Feche o driver**: Sempre use `driver.quit()` ou contexto `with`
3. **Use headless quando possível**: Para scripts automatizados
4. **Trate exceções**: Selenium pode gerar várias exceções
5. **Prefira CSS Selectors**: Mais rápidos que XPath
6. **Use localizadores únicos**: IDs são mais confiáveis que classes

#### ⚠️ Cuidados

- **Rate limiting**: Não faça muitas requisições muito rápido
- **Robots.txt**: Respeite as regras do site
- **Detecção de bots**: Alguns sites detectam automação
- **Recursos**: Selenium consome mais recursos que requests
- **Termos de uso**: Verifique se automação é permitida

#### 🛠️ Debugging

```python
# Imprimir HTML da página
print(driver.page_source)

# Tirar screenshot para debug
driver.save_screenshot("debug.png")

# Aguardar input do usuário (para debug)
input("Pressione Enter para continuar...")

# Logs do navegador
logs = driver.get_log('browser')
for log in logs:
    print(log)
```

#### 📋 Configurações Úteis

```python
# Configurações Chrome para produção
chrome_options = Options()
chrome_options.add_argument("--headless")              # Sem interface
chrome_options.add_argument("--no-sandbox")            # Segurança
chrome_options.add_argument("--disable-dev-shm-usage") # Memória
chrome_options.add_argument("--disable-gpu")           # GPU
chrome_options.add_argument("--window-size=1920,1080") # Tamanho janela
chrome_options.add_argument("--user-agent=Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36")

# Desabilitar imagens (mais rápido)
prefs = {"profile.managed_default_content_settings.images": 2}
chrome_options.add_experimental_option("prefs", prefs)
```

---

