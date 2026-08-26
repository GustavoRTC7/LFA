# Exercícios — Alfabetos, Palavras, Linguagens e Gramáticas

## 1. Alfabeto

Considere o alfabeto:

$$
\Sigma = \{a,b,c\}
$$

* **Quantidade de símbolos:** 3
* **Símbolos:** \(a\), \(b\) e \(c\)
* **O símbolo \(a\) pertence ao alfabeto?** Sim, pois \(a \in \Sigma\).
* **O símbolo \(d\) pertence ao alfabeto?** Não, pois \(d \notin \Sigma\).
* **Exemplos de palavras:** `abc`, `ab`, `bca`, `a`.

---

## 2. Palavras sobre um alfabeto

Considere:

$$
\Sigma = \{0,1\}
$$

| Sequência | Válida?      | Justificativa                                         |
| --------- | ------------ | ----------------------------------------------------- |
| `0101`    | ✅ Válida     | Todos os símbolos (`0` e `1`) pertencem a \(\Sigma\). |
| `00110`   | ✅ Válida     | Todos os símbolos pertencem a \(\Sigma\).             |
| `012`     | ❌ Não válida | O símbolo `2` não pertence a \(\Sigma\).              |
| `111`     | ✅ Válida     | Todos os símbolos pertencem a \(\Sigma\).             |
| `10a`     | ❌ Não válida | O símbolo `a` não pertence a \(\Sigma\).              |

---

## 3. Pertinência de símbolos e palavras

Considere:

$$
\Sigma = \{0,1\}
$$

### Símbolos

* \(0 \in \Sigma\) — **Verdadeiro**. É um símbolo individual do alfabeto.
* \(1 \in \Sigma\) — **Verdadeiro**. É um símbolo individual do alfabeto.
* \(2 \in \Sigma\) — **Falso**. O símbolo `2` não faz parte do alfabeto.

### Palavras

* \(01 \in \Sigma\) — **Falso**. `01` é uma palavra, ou seja, uma cadeia de símbolos, e não um símbolo individual.
* \(01 \in \Sigma^*\) — **Verdadeiro**. `01` pertence ao conjunto de todas as palavras formadas sobre \(\Sigma\).
* \(101 \in \Sigma^*\) — **Verdadeiro**. É uma sequência válida de símbolos de \(\Sigma\).

---

## 4. Linguagem

Considere:

$$
L = \{0,01,011,0111\}
$$

Verificando a pertinência das palavras:

| Palavra | Pertence a \(L\)? |
| ------- | ----------------- |
| `0`     | ✅ Sim             |
| `01`    | ✅ Sim             |
| `0111`  | ✅ Sim             |
| `10`    | ❌ Não             |
| `111`   | ❌ Não             |
| `011`   | ✅ Sim             |

---

## 5. Descrevendo uma linguagem por padrão

Considere:

$$
L = \{b^n \mid n \geq 1\}
$$

### Cinco primeiras palavras

As cinco primeiras palavras da linguagem são:

$$
b,\ bb,\ bbb,\ bbbb,\ bbbbb
$$

### Significado de \(b^n\)

A expressão \(b^n\) representa a concatenação do símbolo `b` repetido \(n\) vezes.

Por exemplo:

$$
b^3 = bbb
$$

### Verificação

**`bbbbbb` pertence a \(L\)?**

Sim.

$$
bbbbbb = b^6
$$

Como:

$$
6 \geq 1
$$

então:

$$
bbbbbb \in L
$$

**\(\varepsilon\) pertence a \(L\)?**

Não.

A palavra vazia corresponde a:

$$
b^0 = \varepsilon
$$

Porém, a definição da linguagem exige:

$$
n \geq 1
$$

Logo:

$$
\varepsilon \notin L
$$

---

## 6. Linguagem vazia e palavra vazia

É importante diferenciar:

### Linguagem vazia

$$
L = \emptyset
$$

A linguagem vazia não contém nenhuma palavra.

* Quantidade de elementos: **0**

### Linguagem contendo a palavra vazia

$$
L = \{\varepsilon\}
$$

Essa linguagem contém exatamente uma palavra: a palavra vazia.

* Quantidade de elementos: **1**
* Palavra: \(\varepsilon\)

### Respostas

* **Possui uma palavra:** \(\{\varepsilon\}\)
* **Não possui nenhuma palavra:** \(\emptyset\)
* **Comprimento de \(\varepsilon\):** \(0\)

---

## 7. Estrutura de uma gramática

Considere a gramática:

$$
G = (\{S,A\},\{0,1\},P,S)
$$

com:

$$
P = \{S \rightarrow 0A,\ A \rightarrow 1\}
$$

### Elementos da gramática

* **Variáveis:**

  $$
  V = \{S,A\}
  $$

* **Terminais:**

  $$
  T = \{0,1\}
  $$

* **Produções:**

  $$
  P = \{S \rightarrow 0A,\ A \rightarrow 1\}
  $$

* **Símbolo inicial:**

  $$
  S
  $$

### Palavra gerada

A palavra gerada é:

$$
01
$$

Derivação:

$$
S \Rightarrow 0A \Rightarrow 01
$$

---

## 8. Como ler e aplicar uma produção

Considere a produção:

$$
S \rightarrow 0S
$$

Partindo do símbolo inicial \(S\), podemos aplicar a produção várias vezes:

### 1ª aplicação

$$
S \Rightarrow 0S
$$

### 2ª aplicação

$$
0S \Rightarrow 00S
$$

### 3ª aplicação

$$
00S \Rightarrow 000S
$$

### Sequência completa

$$
S \Rightarrow 0S \Rightarrow 00S \Rightarrow 000S
$$

---

## 9. Derivação completa de uma palavra

Considere a gramática:

$$
S \rightarrow aS \mid b
$$

Queremos gerar a palavra:

$$
aaab
$$

### Derivação

Aplicando \(S \rightarrow aS\) três vezes:

$$
S \Rightarrow aS
$$

$$
aS \Rightarrow aaS
$$

$$
aaS \Rightarrow aaaS
$$

Por fim, aplicamos:

$$
S \rightarrow b
$$

Obtendo:

$$
aaaS \Rightarrow aaab
$$

### Derivação completa

$$
S \Rightarrow aS \Rightarrow aaS \Rightarrow aaaS \Rightarrow aaab
$$

---

## 10. Identificando palavras geradas por uma gramática

Considere a gramática:

$$
S \rightarrow 0S \mid 1
$$

Vamos verificar quais palavras podem ser geradas.

| Palavra | Gerada? | Derivação / Justificativa                                                                            |
| ------- | ------- | ---------------------------------------------------------------------------------------------------- |
| `1`     | ✅ Sim   | \(S \Rightarrow 1\)                                                                                  |
| `01`    | ✅ Sim   | \(S \Rightarrow 0S \Rightarrow 01\)                                                                  |
| `001`   | ✅ Sim   | \(S \Rightarrow 0S \Rightarrow 00S \Rightarrow 001\)                                                 |
| `0001`  | ✅ Sim   | \(S \Rightarrow 0S \Rightarrow 00S \Rightarrow 000S \Rightarrow 0001\)                               |
| `101`   | ❌ Não   | A regra \(S \rightarrow 1\) finaliza a derivação. Não é possível adicionar um símbolo depois do `1`. |
| `1001`  | ❌ Não   | Pela gramática, todos os `0` devem aparecer antes do único `1`.                                      |

---

# Desafio Final

Considere novamente a gramática:

$$
S \rightarrow aS \mid b
$$

## Palavras que podem ser geradas

### `b`

Sim:

$$
S \Rightarrow b
$$

### `ab`

Sim:

$$
S \Rightarrow aS \Rightarrow ab
$$

### `aab`

Sim:

$$
S \Rightarrow aS \Rightarrow aaS \Rightarrow aab
$$

### `aaab`

Sim:

$$
S \Rightarrow aS \Rightarrow aaS \Rightarrow aaaS \Rightarrow aaab
$$

### `aba`

Não.

A derivação termina quando aplicamos:

$$
S \rightarrow b
$$

Depois que o símbolo `b` é produzido, não existe nenhuma variável para gerar outro `a`.

Portanto:

$$
aba \notin L
$$

---

## Derivação de `aaaab`

Para gerar `aaaab`:

$$
S \Rightarrow aS
$$

$$
aS \Rightarrow aaS
$$

$$
aaS \Rightarrow aaaS
$$

$$
aaaS \Rightarrow aaaaS
$$

$$
aaaaS \Rightarrow aaaab
$$

### Derivação completa

$$
S \Rightarrow aS \Rightarrow aaS \Rightarrow aaaS \Rightarrow aaaaS \Rightarrow aaaab
$$

---

## Padrão da linguagem

A linguagem gerada pela gramática é formada por:

* zero ou mais ocorrências da letra `a`;
* seguidas exatamente por uma letra `b`.

Formalmente:

$$
L = \{a^n b \mid n \geq 0\}
$$

### Exemplos de palavras pertencentes à linguagem

$$
b,\ ab,\ aab,\ aaab,\ aaaab,\ldots
$$

### Exemplos de palavras que não pertencem

$$
a,\ ba,\ aba,\ bba,\ abba
$$

---

# Conclusão

Os exercícios apresentam os principais conceitos introdutórios de **Teoria da Computação e Linguagens Formais**:

1. Alfabetos;
2. Palavras e cadeias;
3. Pertinência de símbolos e palavras;
4. Linguagens;
5. Descrição de linguagens por padrões;
6. Linguagem vazia e palavra vazia;
7. Estrutura de uma gramática;
8. Aplicação de produções;
9. Derivações;
10. Identificação de palavras geradas por uma gramática.
