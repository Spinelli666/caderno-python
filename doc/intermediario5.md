# Fundamentos 40

## Sumário

1. [Módulos - Import, From, As e *](#1-módulos---import-from-as-e-)
    - 1.1. [O Que São Módulos?](#11-o-que-são-módulos)
    - 1.2. [Formas de Importar Módulos](#12-formas-de-importar-módulos)
    - 1.3. [Exemplo Prático](#13-exemplo-prático)
    - 1.4. [Boas Práticas ao Importar Módulos](#14-boas-práticas-ao-importar-módulos)
2. [Modularização - Entendendo os Seus Próprios Módulos e `sys.path` no Python](#2-modularização---entendendo-os-seus-próprios-módulos-e-syspath-no-python)
    - 2.1. [O Que é Modularização?](#21-o-que-é-modularização)
    - 2.2. [Como o Python Encontra Módulos?](#22-como-o-python-encontra-módulos)
    - 2.3. [O Papel do `__main__`](#23-o-papel-do-__main__)
    - 2.4. [Usando `sys.path`](#24-usando-syspath)
    - 2.5. [Exemplo Prático](#25-exemplo-prático)
3. [Como Importar Coisas do Seu Próprio Módulo (Ponto de Vista do `__main__`)](#3-como-importar-coisas-do-seu-próprio-módulo-ponto-de-vista-do-__main__)
    - 3.1. [O Que é o `__main__`?](#31-o-que-é-o-__main__)
    - 3.2. [Importando de Módulos Próprios](#32-importando-de-módulos-próprios)
    - 3.3. [Exemplo Prático](#33-exemplo-prático)
    - 3.4. [Boas Práticas ao Importar de Módulos Próprios](#34-boas-práticas-ao-importar-de-módulos-próprios)

---

## 1. Módulos - Import, From, As e *

Os **módulos** em Python são arquivos que contêm definições e implementações de funções, classes e variáveis. Eles permitem organizar o código em partes reutilizáveis e facilitar a manutenção.

### 1.1. O Que São Módulos?

- Um módulo é um arquivo Python (`.py`) que pode ser importado para outro arquivo.
- Python possui uma biblioteca padrão rica em módulos prontos para uso.
- Você pode criar seus próprios módulos ou usar módulos de terceiros.

**Documentação Oficial:** [Índice de Módulos Padrão](https://docs.python.org/3/py-modindex.html)

### 1.2. Formas de Importar Módulos

Existem várias formas de importar módulos em Python, cada uma com suas vantagens e desvantagens.

#### 1. Importação Completa (`import nome_modulo`)

- Importa o módulo inteiro.
- Você acessa os objetos do módulo usando o namespace do módulo.

**Exemplo:**
```py
import sys

print(sys.platform)  # Acessa o atributo `platform` do módulo `sys`
```

**Vantagens:**
- Mantém o namespace do módulo, evitando conflitos de nomes.

**Desvantagens:**
- Pode resultar em nomes longos.

#### 2. Importação Parcial (`from nome_modulo import objeto1, objeto2`)

- Importa partes específicas de um módulo.
- Você acessa os objetos diretamente, sem o namespace do módulo.

**Exemplo:**
```py
from sys import platform, exit

print(platform)  # Acessa diretamente o atributo `platform`
```

**Vantagens:**
- Nomes mais curtos e diretos.

**Desvantagens:**
- Perde o namespace do módulo, aumentando o risco de conflitos de nomes.

#### 3. Importação com Alias (`import nome_modulo as apelido`)

- Importa o módulo inteiro, mas atribui um alias (apelido) para ele.

**Exemplo:**
```py
import sys as s

print(s.platform)  # Acessa o atributo `platform` usando o alias `s`
```

**Vantagens:**
- Permite usar nomes mais curtos para módulos com nomes longos.
- Evita conflitos de nomes.

#### 4. Importação de Objetos com Alias (`from nome_modulo import objeto as apelido`)

- Importa partes específicas de um módulo e atribui um alias para elas.

**Exemplo:**
```py
from sys import platform as pf

print(pf)  # Acessa o atributo `platform` usando o alias `pf`
```

**Vantagens:**
- Permite reservar nomes para seu código.
- Reduz o risco de conflitos de nomes.

#### 5. Importação de Tudo (`from nome_modulo import *`)

- Importa todos os objetos de um módulo.

**Exemplo:**
```py
from sys import *

print(platform)  # Acessa diretamente o atributo `platform`
```

**Vantagens:**
- Importa tudo de um módulo, facilitando o acesso.

**Desvantagens:**
- Pode causar conflitos de nomes.
- Considerada uma má prática, pois dificulta a leitura e manutenção do código.

### 1.3. Exemplo Prático

**Código Completo:**
```py
# Importação completa
import sys
print(sys.platform)

# Importação parcial
from sys import platform
print(platform)

# Importação com alias
import sys as s
print(s.platform)

# Importação de objetos com alias
from sys import platform as pf
print(pf)

# Importação de tudo (má prática)
from sys import *
print(platform)
```

### 1.4. Boas Práticas ao Importar Módulos

1. **Evite `from nome_modulo import *`:**
   - Pode causar conflitos de nomes e dificultar a leitura do código.

2. **Use aliases para nomes longos:**
   - Facilita a escrita e leitura do código.

3. **Importe apenas o necessário:**
   - Reduz o consumo de memória e melhora a clareza do código.

4. **Organize as importações:**
   - Coloque todas as importações no início do arquivo.
   - Siga a ordem: módulos padrão, módulos de terceiros, módulos locais.

**Dicas:**
- Consulte a [documentação oficial](https://docs.python.org/3/py-modindex.html) para explorar os módulos padrão do Python.
- Use aliases para evitar conflitos de nomes e melhorar a legibilidade.
- Prefira importar apenas o necessário para manter o código limpo e eficiente.

---

## 2. Modularização - Entendendo os Seus Próprios Módulos e `sys.path` no Python

A **modularização** em Python permite dividir o código em partes menores e reutilizáveis chamadas **módulos**. Isso facilita a organização, manutenção e reutilização do código.

### 2.1. O Que é Modularização?

- Modularização é o processo de dividir um programa em partes menores (módulos).
- Um **módulo** é um arquivo Python (`.py`) que pode conter funções, classes e variáveis.
- Você pode importar módulos para usar o código definido neles.

**Exemplo:**
```py
# Arquivo: meu_modulo.py
def saudacao(nome):
    return f'Olá, {nome}!'
```

```py
# Arquivo principal
import meu_modulo

print(meu_modulo.saudacao('Python'))  # Saída: Olá, Python!
```

### 2.2. Como o Python Encontra Módulos?

- O Python conhece a pasta onde o arquivo principal (`__main__`) está localizado.
- Ele também conhece as pastas abaixo da pasta do `__main__`.
- Por padrão, o Python **não reconhece pastas acima do `__main__`**.
- O Python usa o **`sys.path`** para determinar onde procurar módulos e pacotes.

### 2.3. O Papel do `__main__`

- O primeiro módulo executado em um programa Python é chamado de **`__main__`**.
- O valor da variável especial `__name__` será `"__main__"` no módulo principal.
- Em outros módulos importados, o valor de `__name__` será o nome do módulo.

**Exemplo:**
```py
# Arquivo: meu_modulo.py
print('Este módulo se chama', __name__)

# Arquivo principal
import meu_modulo
print('Este módulo se chama', __name__)
```

**Saída:**
```
Este módulo se chama meu_modulo
Este módulo se chama __main__
```

### 2.4. Usando `sys.path`

- O **`sys.path`** é uma lista de caminhos onde o Python procura por módulos e pacotes.
- Você pode adicionar caminhos personalizados ao `sys.path` para importar módulos de outras pastas.

**Exemplo:**
```py
import sys

print(sys.path)  # Mostra os caminhos conhecidos pelo Python
```

**Adicionando um Caminho Personalizado:**
```py
import sys

sys.path.append('/caminho/para/meus/modulos')
import meu_modulo_personalizado
```

### 2.5. Exemplo Prático

**Código Completo:**
```py
# Arquivo: exemplo_m.py
def saudacao(nome):
    return f'Olá, {nome}!'
```

```py
# Arquivo principal
import exemplo_m

print('Este módulo se chama', __name__)
print(exemplo_m.saudacao('Python'))
```

**Saída:**
```
Este módulo se chama __main__
Olá, Python!
```

**Dicas:**
- Use a modularização para organizar seu código em partes reutilizáveis.
- Consulte o `sys.path` para entender onde o Python está procurando módulos.
- Evite modificar o `sys.path` diretamente, a menos que seja necessário.
- Use a variável `__name__` para diferenciar o código que deve ser executado apenas no módulo principal.

---

## 3. Como Importar Coisas do Seu Próprio Módulo (Ponto de Vista do `__main__`)

Quando você cria seus próprios módulos em Python, pode importar funções, variáveis e classes entre arquivos para reutilizar o código. O comportamento do módulo principal (`__main__`) é importante para entender como essas importações funcionam.

### 3.1. O Que é o `__main__`?

- O **`__main__`** é o módulo principal que está sendo executado diretamente.
- Quando você executa um arquivo Python, ele é tratado como o módulo `__main__`.
- Outros módulos importados terão o valor de `__name__` igual ao nome do arquivo (sem a extensão `.py`).

**Exemplo:**
```py
# Arquivo exemplo2_m.py
variavel_modulo = 'Luiz'

def soma(x, y):
    return x + y
```

```py
# Arquivo exemplo2.py
import exemplo2_m

print('Este módulo se chama', __name__)  # Saída: __main__
print('Módulo importado se chama', exemplo2_m.__name__)  # Saída: exemplo2_m
```

### 3.2. Importando de Módulos Próprios

Você pode importar de seus próprios módulos usando as mesmas técnicas de importação de módulos padrão.

#### 1. Importação Completa
```py
import exemplo2_m

print(exemplo2_m.variavel_modulo)  # Acessa a variável do módulo
print(exemplo2_m.soma(2, 3))  # Chama a função do módulo
```

#### 2. Importação Parcial
```py
from exemplo2_m import soma, variavel_modulo

print(variavel_modulo)  # Acessa diretamente a variável
print(soma(2, 3))  # Chama diretamente a função
```

### 3.3. Exemplo Prático

**Código Completo:**

**Arquivo `exemplo2_m.py`:**
```py
variavel_modulo = 'Luiz'

def soma(x, y):
    return x + y
```

**Arquivo `exemplo2.py`:**
```py
# Como importar coisas do seu próprio módulo (ponto de vista do __main__)

import exemplo2_m
from exemplo2_m import soma, variavel_modulo

print('Este módulo se chama', __name__)  # Saída: __main__
print('Módulo importado se chama', exemplo2_m.__name__)  # Saída: exemplo2_m

print(exemplo2_m.variavel_modulo)  # Saída: Luiz
print(variavel_modulo)  # Saída: Luiz
print(soma(2, 3))  # Saída: 5
```

**Saída:**
```
Este módulo se chama __main__
Módulo importado se chama exemplo2_m
Luiz
Luiz
5
```

### 3.4. Boas Práticas ao Importar de Módulos Próprios

1. **Organize seus módulos:**
   - Coloque seus módulos na mesma pasta ou em subpastas do arquivo principal.
   - Use nomes descritivos para seus módulos.

2. **Evite conflitos de nomes:**
   - Use `import nome_modulo` para evitar conflitos entre nomes de variáveis ou funções.

3. **Use aliases quando necessário:**
   - Para módulos com nomes longos, use `import nome_modulo as apelido`.

4. **Teste o módulo principal:**
   - Use a verificação `if __name__ == "__main__":` para executar código apenas no módulo principal.

**Exemplo:**
```py
# Arquivo exemplo2_m.py
variavel_modulo = 'Luiz'

def soma(x, y):
    return x + y

if __name__ == "__main__":
    print('Este módulo está sendo executado diretamente.')
```

---

**Dicas:**
- Use `from nome_modulo import objeto` para importar apenas o necessário.
- Sempre teste seus módulos individualmente antes de integrá-los ao projeto principal.
- Consulte o valor de `__name__` para entender o contexto de execução do módulo.

---