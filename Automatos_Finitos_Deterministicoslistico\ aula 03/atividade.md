# Gabarito — Lista de Exercícios de Autômatos Finitos Determinísticos (AFD)

### Exercício 1 — Entendendo um autômato finito
1. Existem **2 estados**: `Desligado` e `Ligado`.
2. O estado inicial é **`Desligado`**.
3. A entrada que provoca uma transição é **`pressionar`**.
4. Após um acionamento, o estado será **`Ligado`**.
5. Após dois acionamentos, o estado será **`Desligado`**.
6. O sistema alterna entre dois estados opostos a cada vez que o comando de acionamento é executado, funcionando como um circuito de alternância (toggle).

### Exercício 2 — Porta automática
Tabela de transição:

| Estado atual | Entrada | Próximo estado |
|---|---|---|
| Fechado | pessoa_detectada | Aberto |
| Fechado | nenhuma_pessoa | Fechado |
| Aberto | pessoa_detectada | Aberto |
| Aberto | nenhuma_pessoa | Fechado |

* **Estado inicial:** `Fechadp`
* **Diagrama (descrição textual):** `Fechado` vai para `Aberto` com `pessoa_dedectada` (e permanece em `Fechado` com `nenhuma_pessoa`). `Aberto` vai para `Fechado` com `nenhuma_pessoa` (e permanece em `Aberto` com `pessoa_detectada`).

---

## Parte 2 — Anatomia e definição formal

### Exercício 3 — Identificando os elementos
1. **Alfabeto ($\Sigma$):** `{0, 1}`.
2. **Conjunto de estados ($Q$):** `{q0, q1}`.
3. **Estado inicial:** `q0`.
4. **Conjunto de estados finais ($F$):** `{q1}`.
5. **Símbolos que podem ser lidos:** `0` e `1`.
6. **Círculo duplo:** Representa um **estado de aceitação** (final).
7. **Seta sem origem:** Indica qual é o **estado inicial** do autômato.

### Exercício 4 — A quíntupla do AFD
| Elemento | Significado |
|---|---|
| $\Sigma$ | Alfabeto (conjunto finito de símbolos de entrada aceitos) |
| $Q$ | Conjunto finito de estados possíveis do autômato |
| $\delta$ | Função de transição (mapeia $Q \times \Sigma \to Q$) |
| $q_0$ | Estado inicial onde o processamento começa ($q_0 \in Q$) |
| $F$ | Conjunto de estados finais ou de aceitação ($F \subseteq Q$) |

* **Explicação:** Esses cinco elementos determinam completamente o comportamento do autômato, pois dizem com quais símbolos ele trabalha ($\Sigma$), quais situações ele pode assumir ($Q$), para onde ele vai ao ler um símbolo ($\delta$), onde ele começa ($q_0$) e quais condições definem o sucesso da leitura ($F$).

---

## Parte 3 — Tabela de transições e cadeias

### Exercício 5 — Interpretando uma tabela
1. $\delta(q_0, 0) =$ **`q0`**
2. $\delta(q_0, 1) =$ **`q1`**
3. $\delta(q_1, 0) =$ **`q2`**
4. $\delta(q_2, 1) =$ **`q1`**
5. **Estado de aceitação:** `q1`
6. **Diagrama:** `q0` vai para si mesmo com `0` e para `q1` com `1`. `q1` vai para `q2` com `0` e para si mesmo com `1`. `q2` vai para `q1` com `0` e `1`.
7. **Determinismo:** É determinístico porque para cada estado e para cada símbolo de entrada do alfabeto existe **exatamente uma** transição definida para um único próximo estado.

### Exercício 6 — Aceita ou rejeita?

| Cadeia | Caminho percorrido | Estado final | Resultado |
|---|---|---|---|
| `1` | `q0 --1--> q1` | `q1` | **ACEITA** |
| `0011001` | `q0 --0--> q0 --0--> q0 --1--> q1 --1--> q1 --0--> q2 --0--> q1 --1--> q1` | `q1` | **ACEITA** |
| `010010` | `q0 --0--> q0 --1--> q1 --0--> q2 --0--> q1 --1--> q1 --0--> q2` | `q2` | **REJEITA** |
| `1101` | `q0 --1--> q1 --1--> q1 --0--> q2 --1--> q1` | `q1` | **ACEITA** |
| `000011010` | `q0 --0--> q0 --0--> q0 --0--> q0 --0--> q0 --1--> q1 --1--> q1 --0--> q2 --1--> q1 --0--> q2` | `q2` | **REJEITA** |

---

## Parte 4 — Construção de AFDs

### Exercício 7 — Cadeias que terminam em `1`
* **Estados ($Q$):** `{q0, q1}`
* **Alfabeto ($\Sigma$):** `{0, 1}`
* **Estado inicial:** `q0`
* **Estados finais ($F$):** `{q1}`
* **Tabela de transição:**

| $\delta$ | 0 | 1 |
|---|---|---|
| $\rightarrow q_0$ | $q_0$ | $q_1$ |
| $*q_1$ | $q_0$ | $q_1$ |

* **Explicação:** O estado `q0` representa "não terminou em 1" (ou leu 0 por último / leu vazio). O estado `q1` (final) representa "terminou em 1". Qualquer `1` leva para `q1`, e qualquer `0` traz de volta para `q0`.

### Exercício 8 — Número par de símbolos `1`
* **Definição formal $M = (\Sigma, Q, \delta, q_0, F)$:**
  * $\Sigma = \{0, 1\}$
  * $Q = \{q_0, q_1\}$ ($q_0$: quantidade par de `1`s; $q_1$: quantidade ímpar de `1`s)
  * $q_0 = q_0$
  * $F = \{q_0\}$
* **Tabela de transição:**

| $\delta$ | 0 | 1 |
|---|---|---|
| $\rightarrow *q_0$ | $q_0$ | $q_1$ |
| $q_1$ | $q_1$ | $q_0$ |

* **Testes rápidos:** $\varepsilon$ termina em $q_0$ (Aceita); `1` termina em $q_1$ (Rejeita); `11` vai para $q_1$ e retorna para $q_0$ (Aceita).

### Exercício 9 — Pelo menos dois zeros consecutivos
1. O estado inicial representa **nenhum zero lido recentemente**.
2. O primeiro `0` lido leva a um estado intermediário indicando **um zero lido**.
3. O segundo `0` consecutivo leva ao **estado de aceitação** (contém `00`).
4. Depois de encontrar `00`, a cadeia **continua sendo aceita**, pois já satisfez a condição (fica em um laço).
5. São necessários **3 estados**: um inicial, um para um `0`, e um final para dois ou mais `0`s.

* **Quíntupla ($M$):** $\Sigma = \{0, 1\}$, $Q = \{q_0, q_1, q_2\}$, $q_0 = q_0$, $F = \{q_2\}$.
* **Tabela de transição:**

| $\delta$ | 0 | 1 |
|---|---|---|
| $\rightarrow q_0$ | $q_1$ | $q_0$ |
| $q_1$ | $q_2$ | $q_0$ |
| $*q_2$ | $q_2$ | $q_2$ |

---

## Parte 5 — Desafios de modelagem

### Exercício 10 — Semáforo
* **Estados ($Q$):** `{Verde, Amarelo, Vermelho}`
* **Entrada:** `tempo`
* **Transições:** `Verde --tempo--> Amarelo`, `Amarelo --tempo--> Vermelho`, `Vermelho --tempo--> Verde`.
* **Estados de aceitação:** **Não faz sentido** definir estados finais em um semáforo, pois ele é um sistema reativo cíclico de controle contínuo, e não um reconhecedor de cadeias que pára para dizer "aceito" ou "rejeitado".

### Exercício 11 — Sistema de login
1. **Estados necessários:** `Aguardando`, `Erro1`, `Erro2`, `Autenticado`, `Bloqueado`.
2. **Alfabeto ($\Sigma$):** `{senha_correta, senha_incorreta}`
3. **Estado inicial:** `Aguardando`
4. **Estados finais ($F$):** `{Autenticado}`
5. **Transições principais:**
   - De `Aguardando`: `senha_correta` $\to$ `Autenticado`; `senha_incorreta` $\to$ `Erro1`.
   - De `Erro1`: `senha_correta` $\to$ `Autenticado`; `senha_incorreta` $\to$ `Erro2`.
   - De `Erro2`: `senha_correta` $\to$ `Autenticado`; `senha_incorreta` $\to$ `Bloqueado`.
6. **Conclusão:** Apenas 3 estados (`Aguardando`, `Autenticado`, `Bloqueado`) **não são suficientes** porque o sistema precisa contar especificamente 3 erros antes de bloquear, exigindo memória dos estados intermediários (`Erro1` e `Erro2`).

---

## Parte 6 — Prática no JFLAP

### Exercício 12 — Implementação e testes (Exemplo com o Exercício 7)
Tabela de testes sugerida para o autômato que termina em `1`:

| Cadeia | Resultado esperado | Resultado no JFLAP | Conferência |
|---|---|---|---|
| `1` | Aceita | Aceita | OK |
| `01` | Aceita | Aceita | OK |
| `101` | Aceita | Aceita | OK |
| `ε` | Rejeita | Rejeita | OK |
| `0` | Rejeita | Rejeita | OK |
| `10` | Rejeita | Rejeita | OK |

---

## Desafio final

### Exercício 13 — Crie seu próprio problema

#### Problema escolhido
Catraca de acesso a uma estação de metrô.

#### Estados e significado
* `Bloqueada`: Aguardando o pagamento do bilhete para liberar a passagem.
* `Liberada`: Passagem permitida após a validação do pagamento.

#### Alfabeto
$\Sigma = \{pagamento\_valido, empurrar\}$

#### Estado inicial e estados finais
* Estado inicial: `Bloqueada`
* Estados finais ($F$): $\emptyset$ (sistema reativo de controle contínuo sem parada final)

#### Tabela de transições
| $\delta$ | pagamento_valido | empurrar |
|---|---|---|
| $\rightarrow$ `Bloqueada` | `Liberada` | `Bloqueada` |
| `Liberada` | `Liberada` | `Bloqueada` |

#### Definição formal
$M = (\Sigma, Q, \delta, q_0, F)$
* $\Sigma = \{pagamento\_valido, empurrar\}$
* $Q = \{Bloqueada, Liberada\}$
* $q_0 = Bloqueada$
* $F = \emptyset$

#### Testes realizados
| Entrada | Resultado esperado | Resultado obtido |
|---|---|---|
| `empurrar` | Continua bloqueada | Bloqueada |
| `pagamento_valido` | Libera a catraca | Liberada |
| `pagamento_valido, empurrar` | Libera e bloqueia após a passagem | Bloqueada |

#### Evidência no JFLAP
*(Insira aqui o print da tela do JFLAP com o autômato da catraca modelado)*

#### Conclusão
O grupo concluiu que os Autômatos Finitos Determinísticos são ferramentas matemáticas excelentes para modelar sistemas computacionais baseados em estados finitos e eventos, sendo fundamentais para o projeto de softwares de controle, compiladores e protocolos de comunicação.
