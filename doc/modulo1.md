# Módulos Python 1

## Sumário

1. [Criando Datas e Horas em Python com `datetime`](#1-criando-datas-e-horas-em-python-com-datetime)
    - 1.1. [O Que é o Módulo `datetime`?](#11-o-que-é-o-módulo-datetime)
    - 1.2. [Criando Datas e Horas](#12-criando-datas-e-horas)
    - 1.3. [Trabalhando com Unix Timestamp](#13-trabalhando-com-unix-timestamp)
    - 1.4. [Trabalhando com Timezones](#14-trabalhando-com-timezones)
    - 1.5. [Exemplo Prático](#15-exemplo-prático)
    - 1.6. [Dicas e Boas Práticas](#16-dicas-e-boas-práticas)
2. [Calculando Datas com `datetime.timedelta` e `dateutil.relativedelta`](#2-calculando-datas-com-datetimetimedelta-e-dateutilrelativedelta)
    - 2.1. [O Que São `timedelta` e `relativedelta`?](#21-o-que-são-timedelta-e-relativedelta)
    - 2.2. [Por Que Usar `timedelta` e `relativedelta`?](#22-por-que-usar-timedelta-e-relativedelta)
    - 2.3. [Diferença entre `timedelta` e `relativedelta`](#23-diferença-entre-timedelta-e-relativedelta)
    - 2.4. [Exemplo Prático](#24-exemplo-prático)
    - 2.5. [Dicas e Boas Práticas](#25-dicas-e-boas-práticas)
3. [Formatando Datas do `datetime` com `strftime`](#3-formatando-datas-do-datetime-com-strftime)
    - 3.1. [O Que é `strftime`?](#31-o-que-é-strftime)
    - 3.2. [Por Que Usar `strftime`?](#32-por-que-usar-strftime)
    - 3.3. [Principais Códigos de Formatação](#33-principais-códigos-de-formatação)
    - 3.4. [Exemplo Prático](#34-exemplo-prático)
    - 3.5. [Dicas e Boas Práticas](#35-dicas-e-boas-práticas)
4. [Usando `calendar` para Calendários e Datas](#4-usando-calendar-para-calendários-e-datas)
    - 4.1. [O Que é o Módulo `calendar`?](#41-o-que-é-o-módulo-calendar)
    - 4.2. [Por Que Usar o Módulo `calendar`?](#42-por-que-usar-o-módulo-calendar)
    - 4.3. [Principais Funções do Módulo `calendar`](#43-principais-funções-do-módulo-calendar)
    - 4.4. [Exemplo Prático](#44-exemplo-prático)
    - 4.5. [Dicas e Boas Práticas](#45-dicas-e-boas-práticas)
5. [Usando `locale` para Internacionalização (Tradução)](#5-usando-locale-para-internacionalização-tradução)
    - 5.1. [O Que é o Módulo `locale`?](#51-o-que-é-o-módulo-locale)
    - 5.2. [Por Que Usar o Módulo `locale`?](#52-por-que-usar-o-módulo-locale)
    - 5.3. [Principais Funções do Módulo `locale`](#53-principais-funções-do-módulo-locale)
    - 5.4. [Exemplo Prático](#54-exemplo-prático)
    - 5.5. [Dicas e Boas Práticas](#55-dicas-e-boas-práticas)

---

## 1. Criando Datas e Horas em Python com `datetime`

### 1.1. O Que é o Módulo `datetime`?

- O módulo `datetime` fornece classes para manipular datas e horas em Python.
- Ele permite criar, formatar, converter e realizar cálculos com datas e horas.
- **Documentação oficial:**  
  [https://docs.python.org/3/library/datetime.html](https://docs.python.org/3/library/datetime.html)

### 1.2. Criando Datas e Horas

- **Criando datas específicas:**  
  Use `datetime(ano, mês, dia)` ou `datetime(ano, mês, dia, horas, minutos, segundos)` para criar datas específicas.
- **Obtendo a data e hora atual:**  
  Use `datetime.now()` para obter a data e hora atual.
- **Convertendo strings para datas:**  
  Use `datetime.strptime(data, formato)` para converter uma string em um objeto `datetime`.

**Exemplo:**
```py
from datetime import datetime

# Criando uma data específica
data_especifica = datetime(2022, 4, 20, 10, 30, 45)
print(data_especifica)  # Saída: 2022-04-20 10:30:45

# Obtendo a data e hora atual
data_atual = datetime.now()
print(data_atual)  # Saída: Data e hora atual

# Convertendo string para data
data_str = '20/04/2022'
formato = '%d/%m/%Y'
data_convertida = datetime.strptime(data_str, formato)
print(data_convertida)  # Saída: 2022-04-20 00:00:00
```

### 1.3. Trabalhando com Unix Timestamp

- **O que é Unix Timestamp?**  
  É o número de segundos desde 1º de janeiro de 1970 (Era Unix).
- **Convertendo Unix Timestamp para `datetime`:**  
  Use `datetime.fromtimestamp(timestamp)` para converter um timestamp em um objeto `datetime`.
- **Obtendo o Unix Timestamp de uma data:**  
  Use `data.timestamp()` para obter o timestamp de um objeto `datetime`.

**Exemplo:**
```py
from datetime import datetime

# Obtendo o Unix Timestamp da data atual
data_atual = datetime.now()
print(data_atual.timestamp())  # Saída: Timestamp atual

# Convertendo Unix Timestamp para datetime
timestamp = 1748974292
data_convertida = datetime.fromtimestamp(timestamp)
print(data_convertida)  # Saída: 2025-06-03 10:31:32
```

### 1.4. Trabalhando com Timezones

- **O que são Timezones?**  
  Timezones representam fusos horários. Exemplos: UTC, Asia/Tokyo, America/Sao_Paulo.
- **Instalando o módulo `pytz`:**  
  Use `pip install pytz types-pytz` para trabalhar com timezones.
- **Obtendo a data atual em um timezone específico:**  
  Use `datetime.now(timezone('Asia/Tokyo'))`.
- **Criando uma data específica com timezone:**  
  Use `datetime(ano, mês, dia, horas, minutos, segundos, tzinfo=timezone('Asia/Tokyo'))`.

**Exemplo:**
```py
from datetime import datetime
from pytz import timezone

# Obtendo a data atual em um timezone específico
data_atual_tokyo = datetime.now(timezone('Asia/Tokyo'))
print(data_atual_tokyo)  # Saída: Data e hora atual em Tokyo

# Criando uma data específica com timezone
data_especifica_tokyo = datetime(2022, 4, 20, 10, 30, 45, tzinfo=timezone('Asia/Tokyo'))
print(data_especifica_tokyo)  # Saída: 2022-04-20 10:30:45+09:00
```

### 1.5. Exemplo Prático

```py
from datetime import datetime
from pytz import timezone

# Criando uma data específica
data_especifica = datetime(2022, 4, 20, 10, 30, 45)
print(data_especifica)  # Saída: 2022-04-20 10:30:45

# Obtendo a data e hora atual
data_atual = datetime.now()
print(data_atual)  # Saída: Data e hora atual

# Convertendo string para data
data_str = '20/04/2022'
formato = '%d/%m/%Y'
data_convertida = datetime.strptime(data_str, formato)
print(data_convertida)  # Saída: 2022-04-20 00:00:00

# Trabalhando com Unix Timestamp
timestamp = 1748974292
data_convertida = datetime.fromtimestamp(timestamp)
print(data_convertida)  # Saída: 2025-06-03 10:31:32

# Trabalhando com Timezones
data_atual_tokyo = datetime.now(timezone('Asia/Tokyo'))
print(data_atual_tokyo)  # Saída: Data e hora atual em Tokyo
```

### 1.6. Dicas e Boas Práticas

- **Use `datetime.strptime` para conversões:**  
  Sempre especifique o formato correto ao converter strings para objetos `datetime`.
- **Valide timezones:**  
  Use timezones padrão da base de dados tz (ex.: `Asia/Tokyo`, `America/Sao_Paulo`).
- **Evite manipular timestamps diretamente:**  
  Use os métodos do módulo `datetime` para conversões e cálculos.
- **Documente formatos de data:**  
  Explique claramente os formatos usados em conversões (`%d/%m/%Y`, `%Y-%m-%d`, etc.).
- **Instale `pytz` para timezones:**  
  O módulo `pytz` facilita o trabalho com fusos horários.

**Resumo:**  
O módulo `datetime` é uma ferramenta poderosa para manipular datas e horas em Python. Ele permite criar, converter e trabalhar com timezones e Unix Timestamps de forma eficiente e segura.

---

## 2. Calculando Datas com `datetime.timedelta` e `dateutil.relativedelta`

### 2.1. O Que São `timedelta` e `relativedelta`?

- **`datetime.timedelta`:**  
  Um objeto que representa uma diferença fixa entre duas datas ou horas.  
  Exemplo: 10 dias, 2 horas, 30 minutos.
- **`dateutil.relativedelta`:**  
  Um objeto que representa uma diferença relativa entre duas datas ou horas.  
  Exemplo: 1 mês, 1 ano, 10 dias.

**Documentação oficial:**  
- [`datetime.timedelta`](https://docs.python.org/3/library/datetime.html#timedelta-objects)  
- [`dateutil.relativedelta`](https://dateutil.readthedocs.io/en/stable/relativedelta.html)

### 2.2. Por Que Usar `timedelta` e `relativedelta`?

- **`timedelta`:**  
  Ideal para cálculos com diferenças fixas de tempo (ex.: adicionar 10 dias ou 2 horas).
- **`relativedelta`:**  
  Ideal para cálculos com diferenças relativas (ex.: adicionar 1 mês ou 1 ano, respeitando mudanças de calendário).

### 2.3. Diferença entre `timedelta` e `relativedelta`

| **Aspecto**           | **`timedelta`**                     | **`relativedelta`**               |
|------------------------|-------------------------------------|------------------------------------|
| **Diferença fixa**     | Sim                                | Não                                |
| **Diferença relativa** | Não                                | Sim                                |
| **Suporte a meses/anos** | Não                                | Sim                                |
| **Exemplo de uso**     | Adicionar 10 dias                  | Adicionar 1 mês                   |

### 2.4. Exemplo Prático

```py
from datetime import datetime, timedelta
from dateutil.relativedelta import relativedelta

fmt = '%d/%m/%Y %H:%M:%S'
data_inicio = datetime.strptime('20/04/1987 09:30:30', fmt)
data_fim = datetime.strptime('12/12/2022 08:20:20', fmt)

# Usando timedelta
delta_timedelta = timedelta(days=10, hours=2)
print(data_fim + delta_timedelta)  # Adiciona 10 dias e 2 horas
print(data_fim - delta_timedelta)  # Subtrai 10 dias e 2 horas

# Usando relativedelta
delta_relativedelta = relativedelta(data_fim, data_inicio)
print(delta_relativedelta.years, delta_relativedelta.days)  # Diferença em anos e dias
print(data_fim + relativedelta(seconds=60, minutes=10))  # Adiciona 10 minutos e 60 segundos

# Diferença entre datas com timedelta
delta = data_fim - data_inicio
print(delta.days, delta.seconds, delta.microseconds)  # Diferença em dias, segundos e microssegundos
print(delta.total_seconds())  # Diferença total em segundos

# Comparação entre datas
print(data_inicio > data_fim)  # False
print(data_inicio < data_fim)  # True
print(data_inicio == data_fim)  # False
```

**Explicação:**
1. **`timedelta`:**
   - Representa diferenças fixas de tempo (ex.: dias, horas, minutos).
   - Permite adicionar ou subtrair intervalos de tempo fixos.
2. **`relativedelta`:**
   - Representa diferenças relativas de tempo (ex.: meses, anos).
   - Permite cálculos respeitando mudanças de calendário.
3. **Comparação entre datas:**
   - Datas podem ser comparadas diretamente usando operadores (`>`, `<`, `==`).

### 2.5. Dicas e Boas Práticas

- **Escolha entre `timedelta` e `relativedelta`:**
  - Use `timedelta` para diferenças fixas de tempo.
  - Use `relativedelta` para diferenças relativas (ex.: meses, anos).
- **Valide formatos de data:**  
  Certifique-se de que os formatos usados em `datetime.strptime` correspondem às strings de data.
- **Evite cálculos manuais:**  
  Use os métodos do módulo `datetime` e `dateutil` para cálculos precisos.
- **Documente os cálculos:**  
  Explique claramente os intervalos de tempo usados (`10 dias`, `1 mês`, etc.).
- **Teste com diferentes datas:**  
  Certifique-se de que os cálculos funcionam corretamente em diferentes cenários (ex.: anos bissextos).

**Resumo:**  
`datetime.timedelta` e `dateutil.relativedelta` são ferramentas poderosas para calcular diferenças entre datas e horas em Python. Enquanto `timedelta` lida com intervalos fixos, `relativedelta` é ideal para intervalos relativos, respeitando mudanças de calendário.

---

## 3. Formatando Datas do `datetime` com `strftime`

### 3.1. O Que é `strftime`?

- **`strftime`** é um método do módulo `datetime` usado para formatar objetos de data e hora em strings.
- Ele permite transformar datas em formatos personalizados, como `dd/mm/yyyy`, `yyyy-mm-dd`, entre outros.

**Documentação oficial:**  
[https://docs.python.org/3/library/datetime.html](https://docs.python.org/3/library/datetime.html)

### 3.2. Por Que Usar `strftime`?

- **Personalização:**  
  Permite criar formatos de data e hora específicos para exibição ou armazenamento.
- **Facilidade de uso:**  
  Simplifica a conversão de objetos `datetime` para strings formatadas.
- **Compatibilidade:**  
  Útil para integrar datas com sistemas que exigem formatos específicos.

### 3.3. Principais Códigos de Formatação

| **Código** | **Descrição**              | **Exemplo**       |
|------------|----------------------------|-------------------|
| `%d`       | Dia do mês (2 dígitos)     | `01`, `31`        |
| `%m`       | Mês (2 dígitos)            | `01`, `12`        |
| `%Y`       | Ano (4 dígitos)            | `2022`            |
| `%H`       | Hora (24 horas)            | `00`, `23`        |
| `%M`       | Minuto                     | `00`, `59`        |
| `%S`       | Segundo                    | `00`, `59`        |
| `%I`       | Hora (12 horas)            | `01`, `12`        |
| `%p`       | AM ou PM                   | `AM`, `PM`        |
| `%A`       | Nome completo do dia       | `Monday`, `Sunday`|
| `%B`       | Nome completo do mês       | `January`, `December`|
| `%w`       | Dia da semana (0-6)        | `0` (Domingo)     |
| `%j`       | Dia do ano (1-366)         | `001`, `365`      |

### 3.4. Exemplo Prático

```py
from datetime import datetime

# Criando um objeto datetime
data = datetime.strptime('2022-12-13 07:59:23', '%Y-%m-%d %H:%M:%S')

# Formatando a data
print(data.strftime('%d/%m/%Y'))  # Saída: 13/12/2022
print(data.strftime('%d/%m/%Y %H:%M'))  # Saída: 13/12/2022 07:59
print(data.strftime('%d/%m/%Y %H:%M:%S'))  # Saída: 13/12/2022 07:59:23

# Obtendo partes específicas da data
print(data.strftime('%Y'), data.year)  # Saída: 2022 2022
print(data.strftime('%d'), data.day)  # Saída: 13 13
print(data.strftime('%m'), data.month)  # Saída: 12 12
print(data.strftime('%H'), data.hour)  # Saída: 07 7
print(data.strftime('%M'), data.minute)  # Saída: 59 59
print(data.strftime('%S'), data.second)  # Saída: 23 23
```

**Explicação:**
1. **Criando o objeto `datetime`:**  
   A data é criada a partir de uma string usando `datetime.strptime`.
2. **Formatando a data:**  
   `strftime` é usado para transformar o objeto `datetime` em strings formatadas.
3. **Obtendo partes específicas:**  
   É possível acessar partes individuais da data (ano, mês, dia, etc.) usando `strftime` ou diretamente os atributos do objeto `datetime`.

### 3.5. Dicas e Boas Práticas

- **Escolha o formato correto:**  
  Use formatos que sejam compatíveis com o sistema ou aplicação que receberá a data.
- **Documente os formatos usados:**  
  Explique claramente os códigos de formatação (`%d/%m/%Y`, `%Y-%m-%d`, etc.).
- **Valide os dados:**  
  Certifique-se de que as strings de entrada correspondem ao formato esperado ao usar `datetime.strptime`.
- **Teste com diferentes datas:**  
  Verifique se os formatos funcionam corretamente em diferentes cenários (ex.: anos bissextos).
- **Evite erros de timezone:**  
  Certifique-se de que o objeto `datetime` está no timezone correto antes de formatá-lo.

**Resumo:**  
O método `strftime` do módulo `datetime` é uma ferramenta poderosa para formatar datas e horas em Python. Ele permite criar formatos personalizados e acessar partes específicas de objetos `datetime`, promovendo flexibilidade e compatibilidade com diferentes sistemas.

---

## 4. Usando `calendar` para Calendários e Datas

### 4.1. O Que é o Módulo `calendar`?

- O módulo `calendar` fornece funções para trabalhar com calendários e datas em Python.
- Ele permite realizar operações como:
  - Obter o último dia de um mês.
  - Descobrir o nome e número do dia de uma data específica.
  - Criar representações de calendários mensais ou anuais.
  - Trabalhar com semanas e dias de forma programática.

**Documentação oficial:**  
[https://docs.python.org/3/library/calendar.html](https://docs.python.org/3/library/calendar.html)

### 4.2. Por Que Usar o Módulo `calendar`?

- **Facilidade de uso:**  
  Simplifica operações comuns relacionadas a calendários e datas.
- **Flexibilidade:**  
  Permite criar calendários personalizados e realizar cálculos baseados em dias, semanas e meses.
- **Compatibilidade:**  
  Útil para integrar funcionalidades de calendário em sistemas e aplicações.

### 4.3. Principais Funções do Módulo `calendar`

| **Função**                     | **Descrição**                                                                 |
|--------------------------------|-------------------------------------------------------------------------------|
| `calendar(year)`               | Retorna o calendário completo de um ano.                                     |
| `month(year, month)`           | Retorna o calendário de um mês específico.                                   |
| `monthrange(year, month)`      | Retorna o primeiro dia da semana e o número de dias de um mês.               |
| `weekday(year, month, day)`    | Retorna o número do dia da semana para uma data específica.                  |
| `day_name`                     | Lista com os nomes dos dias da semana.                                       |
| `monthcalendar(year, month)`   | Retorna uma matriz representando o calendário de um mês (semanas e dias).    |

### 4.4. Exemplo Prático

```py
import calendar

# Exibindo o calendário completo de um ano
print(calendar.calendar(2025))

# Exibindo o calendário de um mês específico
print(calendar.month(2025, 6))

# Obtendo o primeiro dia da semana e o número de dias de um mês
number_first_day, number_last_day = calendar.monthrange(2025, 6)
print(f"Primeiro dia da semana: {calendar.day_name[number_first_day]}")
print(f"Último dia do mês: {calendar.day_name[calendar.weekday(2025, 6, number_last_day)]}")

# Criando uma matriz representando o calendário de um mês
print(calendar.monthcalendar(2025, 6))

# Iterando sobre os dias de um mês
for week in calendar.monthcalendar(2025, 6):
    for day in week:
        if day == 0:  # Dias fora do mês são representados como 0
            continue
        print(day)
```

**Explicação:**
1. **`calendar.calendar`:**  
   Retorna o calendário completo de um ano.
2. **`calendar.month`:**  
   Retorna o calendário de um mês específico.
3. **`calendar.monthrange`:**  
   Retorna o número do primeiro dia da semana e o número de dias do mês.
4. **`calendar.weekday`:**  
   Retorna o número do dia da semana para uma data específica.
5. **`calendar.monthcalendar`:**  
   Retorna uma matriz onde cada sublista representa uma semana, e os dias fora do mês são representados como `0`.

### 4.5. Dicas e Boas Práticas

- **Use `monthrange` para validações:**  
  Verifique o número de dias em um mês antes de realizar operações com datas.
- **Aproveite `day_name` e `day_abbr`:**  
  Use essas listas para exibir nomes completos ou abreviados dos dias da semana.
- **Ignore dias fora do mês:**  
  Ao iterar sobre `monthcalendar`, ignore os dias representados como `0`.
- **Documente os cálculos:**  
  Explique claramente os cálculos baseados em dias, semanas ou meses.
- **Teste com diferentes anos e meses:**  
  Certifique-se de que os cálculos funcionam corretamente em diferentes cenários (ex.: anos bissextos).

**Resumo:**  
O módulo `calendar` é uma ferramenta poderosa para trabalhar com calendários e datas em Python. Ele oferece funções para criar calendários, calcular dias e semanas, e realizar operações baseadas em datas de forma eficiente e flexível.

---

## 5. Usando `locale` para Internacionalização (Tradução)

### 5.1. O Que é o Módulo `locale`?

- O módulo `locale` fornece funcionalidades para configurar e obter informações sobre configurações regionais (locales) do sistema.
- Ele é usado para internacionalização (i18n), permitindo que programas adaptem sua exibição de datas, números, moedas e outros formatos com base na localização do usuário.

**Documentação oficial:**  
[https://docs.python.org/3/library/locale.html](https://docs.python.org/3/library/locale.html)

### 5.2. Por Que Usar o Módulo `locale`?

- **Internacionalização:**  
  Permite que programas sejam adaptados para diferentes idiomas e regiões.
- **Formatação regional:**  
  Ajusta automaticamente formatos de datas, números e moedas com base no locale configurado.
- **Compatibilidade:**  
  Facilita a integração com sistemas que exigem formatos regionais específicos.

### 5.3. Principais Funções do Módulo `locale`

| **Função**                | **Descrição**                                                                 |
|---------------------------|-------------------------------------------------------------------------------|
| `locale.setlocale()`      | Configura o locale para o programa.                                          |
| `locale.getlocale()`      | Retorna o locale atual configurado.                                          |
| `locale.localeconv()`     | Retorna as convenções de formatação do locale atual (ex.: separadores decimais). |
| `locale.getdefaultlocale()` | Retorna o locale padrão do sistema.                                          |
| `locale.normalize()`      | Normaliza o nome de um locale.                                               |

### 5.4. Exemplo Prático

```py
import calendar
import locale

# Configurando o locale para o padrão do sistema
locale.setlocale(locale.LC_ALL, '')

# Exibindo o calendário do ano de 2025
print(calendar.calendar(2025))

# Obtendo o locale atual configurado
print(locale.getlocale())  # Saída: ('pt_BR', 'UTF-8') (exemplo para português do Brasil)

# Configurando um locale específico (ex.: francês)
locale.setlocale(locale.LC_ALL, 'fr_FR.UTF-8')
print(locale.getlocale())  # Saída: ('fr_FR', 'UTF-8')

# Exibindo o calendário com o locale configurado
print(calendar.month(2025, 6))  # Saída: Calendário em francês
```

**Explicação:**
1. **`locale.setlocale`:**  
   Configura o locale para o programa. O valor `''` usa o padrão do sistema.
2. **`locale.getlocale`:**  
   Retorna o locale atual configurado.
3. **`calendar.calendar`:**  
   Exibe o calendário completo do ano, adaptado ao locale configurado.
4. **Configuração específica:**  
   O locale pode ser configurado para idiomas específicos, como `fr_FR` (francês) ou `en_US` (inglês dos EUA).

### 5.5. Dicas e Boas Práticas

- **Teste com diferentes locales:**  
  Certifique-se de que seu programa funciona corretamente em diferentes configurações regionais.
- **Use `locale.getdefaultlocale`:**  
  Para obter o locale padrão do sistema, use `locale.getdefaultlocale()` antes de configurar um novo locale.
- **Valide a disponibilidade do locale:**  
  Nem todos os locales estão disponíveis em todos os sistemas. Verifique a compatibilidade antes de usar.
- **Documente os locales usados:**  
  Explique claramente os locais configurados no programa (ex.: `pt_BR`, `en_US`, etc.).
- **Evite dependências desnecessárias:**  
  Use o locale apenas quando necessário para internacionalização ou formatação regional.

**Resumo:**  
O módulo `locale` é uma ferramenta poderosa para internacionalização em Python. Ele permite configurar e adaptar programas para diferentes idiomas e regiões, ajustando automaticamente formatos de datas, números e moedas com base no locale configurado.

---