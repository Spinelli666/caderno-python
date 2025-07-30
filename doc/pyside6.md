# PySide6 para GUI (Interface Gráfica) com Qt em Python

## Sumário

1. [O que é PySide6?](#1-o-que-é-pyside6)
    - 1.1. [PySide6 vs PyQt5: Por que a troca?](#11-pyside6-vs-pyqt5-por-que-a-troca)
    - 1.2. [Instalação do PySide6](#12-instalação-do-pyside6)
    - 1.3. [Exemplo Básico: Versão do PySide6 e Qt](#13-exemplo-básico-versão-do-pyside6-e-qt)
    - 1.4. [Resumo das Vantagens do PySide6](#14-resumo-das-vantagens-do-pyside6)
    - 1.5. [Dicas e Boas Práticas](#15-dicas-e-boas-práticas)

---

## 1. O que é PySide6?

- **PySide6** é um binding oficial da biblioteca Qt 6 para Python, desenvolvido pela própria The Qt Company.
- **Qt** é uma biblioteca poderosa e multiplataforma (Windows, Linux, Mac) para criação de interfaces gráficas (GUI), originalmente escrita em C++.
- O PySide6 permite criar aplicações gráficas modernas em Python, sem precisar usar C++.
- O "6" refere-se à versão da Qt utilizada (Qt 6).
- O PySide6 oferece acesso a praticamente todos os recursos do Qt, incluindo widgets, gráficos, animações, acesso a arquivos, rede, etc.

**Documentação oficial:**  
https://doc.qt.io/qtforpython/

### 1.1. PySide6 vs PyQt5: Por que a troca?

- **PyQt** e **PySide** são ambos bindings para a biblioteca Qt, com APIs muito semelhantes (muitas vezes o código é idêntico).
- **PySide6** é mantido pela The Qt Company, enquanto o **PyQt5** é mantido por terceiros (Riverbank Computing).
- **Licença:**
  - **PyQt5:** GPL (código aberto, exige que seu código também seja aberto) ou licença comercial paga.
  - **PySide6:** LGPL (mais permissiva, permite uso comercial sem obrigar a abrir seu código).
  - Em resumo: **PySide6** é mais flexível para projetos comerciais e distribuição fechada.
- **Compatibilidade:**
  - PySide6 acompanha de perto as atualizações do Qt.
  - Portar código entre PyQt e PySide geralmente exige apenas trocar o nome do módulo nas importações.
- **Comunidade e suporte:**
  - PySide6 tem suporte oficial da The Qt Company e documentação atualizada.

**Referências sobre licenças:**
- https://tldrlegal.com/license/gnu-lesser-general-public-license-v3-(lgpl-3)

### 1.2. Instalação do PySide6

```bash
pip install pyside6
```

### 1.3. Exemplo Básico: Versão do PySide6 e Qt

```python
import PySide6.QtCore

# Versão do PySide6
print('PySide6:', PySide6.QtCore.__version__)

# Versão do Qt usada pelo PySide6
print('Qt:', PySide6.QtCore.__qt_version__)
```

### 1.4. Resumo das Vantagens do PySide6

- Permite criar GUIs modernas e multiplataforma em Python
- Licença LGPL: uso comercial facilitado
- Suporte oficial e documentação atualizada
- Código facilmente portável entre PyQt e PySide
- Acesso a todos os recursos do Qt 6

### 1.5. Dicas e Boas Práticas

- Sempre consulte a documentação oficial para recursos avançados
- Fique atento às diferenças de licença para projetos comerciais
- Teste sua aplicação em diferentes sistemas operacionais
- Para migrar de PyQt para PySide, normalmente basta trocar o nome do módulo nas importações

---