# Resolução de Atividades - Expressões Regulares
**Disciplina:** Linguagens Formais e Autômatos  
**Curso:** Engenharia de Software  
**Instituição:** Centro Universitário UDF  
**Docente:** Profa. Kadidja Valéria  

---

## 1. Exercício Guiado (Slide 20)

### Item 1: Palavras sobre $\Sigma = \{0, 1\}$ que terminam em `00`
* **Linguagem:** $L = \{w \in \{0, 1\}^* \mid w \text{ termina com } 00\}$
* **Expressão Regular Clássica:** `(0|1)*00`
* **Regex (com âncoras):** `^[01]*00$`
* **Explicação:** Permite qualquer sequência prévia de `0` e `1` (incluindo a cadeia vazia $\epsilon$), finalizando obrigatoriamente com o sufixo fixo `00`.
* **Casos Aceitos:** `00`, `100`, `000`, `110100`
* **Casos Rejeitados:** `ε` (vazio), `0`, `1`, `01`, `10`, `1001`

---

### Item 2: Palavras sobre $\Sigma = \{a, b\}$ com exatamente dois 'a'
* **Linguagem:** $L = \{w \in \{a, b\}^* \mid \text{quantidade de 'a' em } w = 2\}$
* **Expressão Regular Clássica:** `b*ab*ab*`
* **Regex (com âncoras):** `^b*ab*ab*$`
* **Explicação:** Fixa a ocorrência de exatamente dois símbolos `a`, permitindo repetições arbitrárias de `b` antes, entre e após eles.
* **Casos Aceitos:** `aa`, `baa`, `aba`, `aab`, `bbabbabbb`
* **Casos Rejeitados:** `ε`, `a`, `b`, `aaa`, `baaab`

---

### Item 3: Identificador (2 maiúsculas, 3 dígitos e 1 minúscula opcional)
* **Expressão Regular Clássica:** `[A-Z][A-Z][0-9][0-9][0-9]([a-z]|ε)`
* **Regex (com âncoras):** `^[A-Z]{2}[0-9]{3}[a-z]?$`
* **Explicação:** Exige exatamente duas letras maiúsculas (`[A-Z]{2}`), três algarismos numéricos (`[0-9]{3}`) e zero ou uma letra minúscula opcional ao final (`[a-z]?`).
* **Casos Aceitos:** `AB123`, `XY000`, `SP202a`, `DF999z`
* **Casos Rejeitados:** `A123` (falta maiúscula), `ABC123` (excesso de maiúsculas), `AB12` (faltam dígitos), `AB1234` (excesso de dígitos), `AB123ab` (mais de uma minúscula)

---

## 2. Desafio: Matrícula Acadêmica (Slides 21 e 22)

**Formato exigido:** `CURSO-ANO-NÚMERO-TURNO` (sem caracteres extras)

### Expressão Regular Completa
```regex
^(CCO|ESW|SIS)-202[4-9]-[0-9]{4}-[MTN]$
```

### Justificativa por Bloco
* `^` e `$`: Âncoras que garantem a validação da cadeia de ponta a ponta, sem caracteres extras.
* `(CCO|ESW|SIS)`: Aceita estritamente uma das três siglas de curso válidas.
* `-202[4-9]`: Delimitador `-` seguido do ano compreendido no intervalo de `2024` a `2029`.
* `-[0-9]{4}`: Delimitador `-` seguido de exatamente 4 algarismos numéricos.
* `-[MTN]`: Delimitador `-` seguido da sigla do turno: Matutino (`M`), Vespertino (`T`) ou Noturno (`N`).

### Casos de Teste

| Entrada | Resultado | Motivo |
| :--- | :---: | :--- |
| `ESW-2026-0001-N` | **Válido** | Estrutura correta, ano dentro da faixa (2026), 4 dígitos, turno N. |
| `CCO-2024-1234-M` | **Válido** | Limite inferior de ano (2024), curso CCO, turno M. |
| `SIS-2029-9999-T` | **Válido** | Limite superior de ano (2029), curso SIS, turno T. |
| `ADM-2026-0001-N` | **Inválido** | Curso não permitido (`ADM`). |
| `ESW-2023-0001-N` | **Inválido** | Ano abaixo do limite permitido (`2023` < `2024`). |
| `ESW-2030-0001-N` | **Inválido** | Ano acima do limite permitido (`2030` > `2029`). |
| `ESW-2026-001-N` | **Inválido** | Bloco numérico incompleto (3 dígitos em vez de 4). |
| `ESW-2026-0001-X` | **Inválido** | Turno inválido (`X`). |

---

## 3. Questões para Reflexão (Slide 23)

### 1. Toda expressão regular formal representa uma linguagem regular?
**Sim.** Pela definição indutiva formal, toda expressão regular é composta por operações fechadas (união, concatenação e fecho de Kleene) sobre um alfabeto finito, gerando estritamente linguagens regulares.

### 2. Toda linguagem regular possui uma expressão regular?
**Sim.** Pelo **Teorema de Kleene**, a equivalência entre autômatos finitos e expressões regulares é bidirecional. Toda linguagem reconhecida por um autômato finito pode ser convertida em uma expressão regular equivalente (usando, por exemplo, o método de eliminação de estados ou o algoritmo de Arden).

### 3. Como uma Regex se relaciona com DFA e NFA?
Possuem o mesmo poder computacional:
1. Uma **Regex** pode ser convertida mecanicamente em um **$\epsilon$-NFA** usando a **Construção de Thompson**.
2. O **NFA** é convertido em um **DFA** através do **Algoritmo dos Subconjuntos**.
3. Um **DFA** pode ser convertido de volta para uma **Regex** por **Eliminação de Estados**.

### 4. Quais extensões de motores Regex não pertencem à definição clássica?
Motores modernos de regex introduziram recursos como:
* **Retroreferências (*backreferences*, ex.: `\1`):** Permitem verificar repetições dinâmicas como $\{ww \mid w \in \Sigma^*\}$, o que quebra a regularidade e torna o problema NP-completo.
* **Lookahead / Lookbehind:** Asserções de largura zero que inspecionam contexto à frente ou atrás sem consumir caracteres.
* **Recursão de padrões:** Capacidade de casar estruturas aninhadas balanceadas.

### 5. Por que $\{a^n b^n \mid n \ge 0\}$ não pode ser reconhecida por um DFA?
Porque autômatos finitos possuem **memória finita** restrita aos seus estados predeterminados. Para verificar se a quantidade de símbolos `b` é idêntica à de símbolos `a`, o autômato precisaria de uma contagem arbitrária e ilimitada de $n$, o que viola o **Lema do Bombeamento para Linguagens Regulares** (essa linguagem pertence à classe das linguagens livres de contexto e exige memória em pilha).