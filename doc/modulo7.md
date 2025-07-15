# Módulos Python 7

## Sumário

1. [Subprocess - Executando Programas e Comandos Externos](#1-subprocess---executando-programas-e-comandos-externos)
    - 1.1. [O Que é o Módulo `subprocess`?](#11-o-que-é-o-módulo-subprocess)
    - 1.2. [Instalação e Importação](#12-instalação-e-importação)
    - 1.3. [A Função `subprocess.run()`](#13-a-função-subprocessrun)
    - 1.4. [Principais Argumentos do `subprocess.run()`](#14-principais-argumentos-do-subprocessrun)
    - 1.5. [Objeto CompletedProcess](#15-objeto-completedprocess)
    - 1.6. [Tratamento de Codificação de Caracteres](#16-tratamento-de-codificação-de-caracteres)
    - 1.7. [Exemplo Prático Completo](#17-exemplo-prático-completo)
    - 1.8. [Dicas e Boas Práticas](#18-dicas-e-boas-práticas)

---

## 1. Subprocess - Executando Programas e Comandos Externos

### 1.1. O Que é o Módulo `subprocess`?

O **`subprocess`** é um módulo do Python para executar processos e comandos externos no seu programa. Ele permite:

- Executar comandos do sistema operacional
- Capturar saída (stdout) e erros (stderr) de comandos
- Passar dados para programas externos (stdin)
- Controlar e monitorar processos filhos
- Substituir funções mais antigas como `os.system()` e `os.popen()`

**Documentação oficial:**  
[https://docs.python.org/3/library/subprocess.html](https://docs.python.org/3/library/subprocess.html)

### 1.2. Instalação e Importação

O módulo `subprocess` é parte da biblioteca padrão do Python, não necessitando instalação adicional:

```python
import subprocess
import sys  # Para detectar o sistema operacional
```

### 1.3. A Função `subprocess.run()`

A função **`subprocess.run()`** é o método mais simples e recomendado para executar comandos externos:

```python
# Sintaxe básica
resultado = subprocess.run(comando, argumentos_opcionais)
```

#### Vantagens do `subprocess.run()`

- **Simplicidade:** Interface mais limpa que outras funções do módulo
- **Segurança:** Melhor controle sobre execução de comandos
- **Flexibilidade:** Múltiplas opções de configuração
- **Compatibilidade:** Funciona bem em diferentes sistemas operacionais

### 1.4. Principais Argumentos do `subprocess.run()`

| **Argumento** | **Tipo** | **Descrição** |
|---------------|----------|---------------|
| `args` | `list` ou `str` | Comando e argumentos a serem executados |
| `stdout` | `int` ou `file` | Redireciona a saída padrão |
| `stderr` | `int` ou `file` | Redireciona a saída de erro |
| `stdin` | `int` ou `file` | Redireciona a entrada padrão |
| `capture_output` | `bool` | Se `True`, captura stdout e stderr para uso posterior |
| `text` | `bool` | Se `True`, trata entradas e saídas como texto (string) |
| `encoding` | `str` | Especifica a codificação de caracteres |
| `shell` | `bool` | Se `True`, executa o comando através do shell do sistema |
| `executable` | `str` | Caminho do executável que iniciará o subprocesso |
| `timeout` | `float` | Tempo limite em segundos para execução |
| `check` | `bool` | Se `True`, levanta exceção se o comando falhar |
| `cwd` | `str` | Diretório de trabalho para o processo |
| `env` | `dict` | Variáveis de ambiente para o processo |

#### Detalhamento dos Argumentos Importantes

**`capture_output=True`:**
```python
# Captura stdout e stderr para uso posterior
resultado = subprocess.run(['ls', '-la'], capture_output=True, text=True)
print(resultado.stdout)  # Saída do comando
print(resultado.stderr)  # Erros do comando
```

**`text=True`:**
```python
# Converte automaticamente bytes para string
resultado = subprocess.run(['echo', 'Hello'], capture_output=True, text=True)
print(type(resultado.stdout))  # <class 'str'>
```

**`shell=True`:**
```python
# Permite usar recursos do shell (pipes, redirecionamento, etc.)
resultado = subprocess.run('ls -la | grep .py', shell=True, capture_output=True, text=True)
```

**`check=True`:**
```python
# Levanta CalledProcessError se o comando falhar
try:
    subprocess.run(['comando_inexistente'], check=True)
except subprocess.CalledProcessError as e:
    print(f"Comando falhou com código: {e.returncode}")
```

### 1.5. Objeto CompletedProcess

O `subprocess.run()` retorna um objeto `CompletedProcess` com os seguintes atributos:

| **Atributo** | **Descrição** |
|--------------|---------------|
| `args` | Comando e argumentos que foram executados |
| `returncode` | Código de retorno do processo (0 = sucesso, != 0 = erro) |
| `stdout` | Saída padrão capturada (se `capture_output=True`) |
| `stderr` | Saída de erro capturada (se `capture_output=True`) |

```python
resultado = subprocess.run(['ls', '-la'], capture_output=True, text=True)

print(f"Comando: {resultado.args}")
print(f"Código de retorno: {resultado.returncode}")
print(f"Saída: {resultado.stdout}")
print(f"Erros: {resultado.stderr}")
```

### 1.6. Tratamento de Codificação de Caracteres

A codificação de caracteres pode variar entre sistemas operacionais:

| **Sistema** | **Codificação Comum** | **Exemplo** |
|-------------|----------------------|-------------|
| Linux/macOS | `utf-8` | Padrão na maioria das distribuições |
| Windows | `cp850`, `cp1252`, `cp852` | Varia conforme região e configuração |

#### Detecção Automática do Sistema

```python
import sys

def get_system_encoding():
    """Retorna a codificação adequada baseada no sistema operacional"""
    system = sys.platform
    
    if system == 'win32':
        return 'cp850'  # Windows
    elif system in ['linux', 'linux2']:
        return 'utf-8'  # Linux
    elif system == 'darwin':
        return 'utf-8'  # macOS
    else:
        return 'utf-8'  # Padrão
```

### 1.7. Exemplo Prático Completo

```python
import subprocess
import sys

def executar_comando_sistema():
    """
    Exemplo prático de uso do subprocess com detecção automática do sistema
    """
    # Detectar sistema operacional
    system = sys.platform
    print(f"Sistema detectado: {system}")
    
    # Configurar comando e codificação baseado no sistema
    if system == 'win32':
        # Windows
        comando = ['dir']
        encoding = 'cp850'
        shell_needed = True
    else:
        # Linux/macOS
        comando = ['ls', '-lah', '/']
        encoding = 'utf-8'
        shell_needed = False
    
    try:
        # Executar comando
        print(f"Executando comando: {' '.join(comando)}")
        
        resultado = subprocess.run(
            comando,
            capture_output=True,
            text=True,
            encoding=encoding,
            shell=shell_needed,
            timeout=10  # Timeout de 10 segundos
        )
        
        # Verificar se o comando foi executado com sucesso
        if resultado.returncode == 0:
            print("Comando executado com sucesso!")
            print(f"Código de retorno: {resultado.returncode}")
            print("\nSaída do comando:")
            print(resultado.stdout)
        else:
            print("Comando falhou!")
            print(f"Código de retorno: {resultado.returncode}")
            print("\nErros:")
            print(resultado.stderr)
            
    except subprocess.TimeoutExpired:
        print("Comando excedeu o tempo limite!")
    except subprocess.CalledProcessError as e:
        print(f"Erro na execução: {e}")
    except Exception as e:
        print(f"Erro inesperado: {e}")

def exemplo_ping():
    """
    Exemplo específico: comando ping
    """
    system = sys.platform
    
    if system == 'win32':
        comando = ['ping', '127.0.0.1']
        encoding = 'cp850'
    else:
        comando = ['ping', '127.0.0.1', '-c', '4']
        encoding = 'utf-8'
    
    try:
        resultado = subprocess.run(
            comando,
            capture_output=True,
            text=True,
            encoding=encoding,
            timeout=15
        )
        
        print(f"Resultado do ping para 127.0.0.1:")
        print(f"Código de retorno: {resultado.returncode}")
        print(resultado.stdout)
        
    except Exception as e:
        print(f"Erro no ping: {e}")

def exemplo_com_input():
    """
    Exemplo passando input para o comando
    """
    try:
        # Exemplo com comando que aceita input
        resultado = subprocess.run(
            ['python3', '-c', 'print(input("Digite algo: "))'],
            input="Hello, World!",
            capture_output=True,
            text=True,
            shell=False
        )
        
        print("Resultado com input:")
        print(resultado.stdout)
        
    except Exception as e:
        print(f"Erro: {e}")

# Executar exemplos
if __name__ == "__main__":
    print("=== Exemplo 1: Comando básico ===")
    executar_comando_sistema()
    
    print("\n=== Exemplo 2: Ping ===")
    exemplo_ping()
    
    print("\n=== Exemplo 3: Comando com input ===")
    exemplo_com_input()
```

#### Exemplo de Execução com Múltiplos Comandos

```python
def executar_multiplos_comandos():
    """
    Exemplo de execução de múltiplos comandos em sequência
    """
    comandos = [
        (['python3', '--version'], 'Versão do Python'),
        (['whoami'], 'Usuário atual'),
        (['pwd'], 'Diretório atual'),
    ]
    
    for comando, descricao in comandos:
        try:
            resultado = subprocess.run(
                comando,
                capture_output=True,
                text=True,
                encoding='utf-8'
            )
            
            print(f"\n{descricao}:")
            if resultado.returncode == 0:
                print(f"{resultado.stdout.strip()}")
            else:
                print(f"Erro: {resultado.stderr.strip()}")
                
        except Exception as e:
            print(f"Erro ao executar '{' '.join(comando)}': {e}")
```

### 1.8. Dicas e Boas Práticas

#### Boas Práticas

1. **Sempre use `capture_output=True` quando precisar da saída:**
   ```python
   resultado = subprocess.run(['ls'], capture_output=True, text=True)
   ```

2. **Defina timeout para evitar travamentos:**
   ```python
   resultado = subprocess.run(['comando'], timeout=30)
   ```

3. **Use `check=True` para detectar falhas automaticamente:**
   ```python
   subprocess.run(['comando'], check=True)
   ```

4. **Prefira listas a strings para comandos:**
   ```python
   # Melhor
   subprocess.run(['ls', '-la', '/home'])
   
   # Evitar (exceto com shell=True)
   subprocess.run('ls -la /home')
   ```

5. **Trate exceções adequadamente:**
   ```python
   try:
       resultado = subprocess.run(['comando'], check=True, timeout=10)
   except subprocess.CalledProcessError as e:
       print(f"Comando falhou: {e}")
   except subprocess.TimeoutExpired:
       print("Comando excedeu tempo limite")
   ```

#### Cuidados e Segurança

1. **Cuidado com `shell=True`:**
   - Pode ser vulnerável a ataques de injeção de comando
   - Use apenas quando necessário
   - Valide entradas do usuário

2. **Sanitize inputs do usuário:**
   ```python
   import shlex
   
   user_input = "arquivo; rm -rf /"  # Input malicioso
   safe_input = shlex.quote(user_input)  # Torna seguro
   ```

3. **Não execute comandos com privilégios desnecessários:**
   - Evite executar como root/administrador quando possível

4. **Valide códigos de retorno:**
   ```python
   if resultado.returncode != 0:
       print("Comando falhou!")
   ```

#### Troubleshooting Comum

1. **Erro de codificação:**
   ```python
   # Tente diferentes codificações
   encodings = ['utf-8', 'cp850', 'cp1252', 'latin-1']
   for encoding in encodings:
       try:
           resultado = subprocess.run(comando, capture_output=True, 
                                    text=True, encoding=encoding)
           break
       except UnicodeDecodeError:
           continue
   ```

2. **Comando não encontrado:**
   ```python
   import shutil
   
   if shutil.which('comando') is None:
       print("Comando não encontrado no PATH")
   ```

3. **Problemas com PATH:**
   ```python
   # Usar caminho absoluto
   subprocess.run(['/usr/bin/python3', '--version'])
   
   # Ou modificar o PATH
   env = os.environ.copy()
   env['PATH'] = '/usr/local/bin:' + env['PATH']
   subprocess.run(['comando'], env=env)
   ```

#### Alternativas ao `subprocess.run()`

| **Função** | **Uso** | **Quando Usar** |
|------------|---------|-----------------|
| `subprocess.Popen()` | Controle avançado de processos | Quando precisar de controle fino sobre o processo |
| `subprocess.call()` | Execução simples (deprecated) | Evitar - usar `run()` |
| `subprocess.check_output()` | Capturar apenas stdout | Quando só precisar da saída |
| `os.system()` | Execução muito simples (deprecated) | Evitar - usar `subprocess` |

**Resumo:**  
O módulo `subprocess` é a ferramenta padrão e mais segura para executar comandos externos em Python. Com `subprocess.run()`, você tem controle total sobre execução, captura de saída e tratamento de erros, substituindo métodos mais antigos como `os.system()`.

---
