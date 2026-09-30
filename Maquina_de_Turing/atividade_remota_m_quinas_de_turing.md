# Atividade Remota — Máquinas de Turing 🚀

Repositório dedicado à entrega da atividade prática da disciplina de **Teoria da Computação**, abordando o estudo, simulação e reflexão sobre Máquinas de Turing e limites computacionais.

---

## 📋 Sumário
- [Etapa 1 — Introdução](#etapa-1--introdução)
- [Etapa 2 e 3 — Simulação e Registro da Máquina de Turing](#etapa-2-e-3--simulação-e-registro-da-máquina-de-turing)
- [Etapa 4 — Reflexão sobre os Limites Computacionais](#etapa-4--reflexão-sobre-os-limites-computacionais)
- [Questão Final — Problema para Reflexão](#questão-final--problema-para-reflexão)

---

## 🔍 Etapa 1 — Introdução

### 1. O que é uma Máquina de Turing?
Uma Máquina de Turing é uma construção matemática abstrata que ajuda a descrever rigorosamente o que significa computação; ela funciona como um modelo idealizado que utiliza uma fita de papel infinita (que serve simultaneamente como material de programa, dados, entrada e saída) e uma cabeça de leitura capaz de ler, escrever e apagar dados.

### 2. Quais são os principais componentes de uma Máquina de Turing?
* Uma fita infinita (dividida em quadrados) que serve para armazenar dados e programas.
* Uma cabeça de leitura e escrita (ou escaneamento) que passa pela fita para ler, escrever ou apagar um quadrado de cada vez.
* Um conjunto finito de estados (incluindo um estado inicial).

### 3. Qual é a importância das Máquinas de Turing para a computação?
Elas definiram com rigor matemático o que é um programa e estabeleceram o modelo teórico fundamental do que conhecemos hoje como computador.

### 4. Qual é a relação entre Máquina de Turing e algoritmo?
A Máquina de Turing formaliza matematicamente o conceito de um algoritmo ou programa de computador, expressando-o por meio de uma tabela de estados finitos e transições lógicas que processam dados passo a passo de forma previsível e automatizada.

---

### **Etapa 2 e 3 - Simulação da Máquina de Turing ($0^n1^n$)**

Para resolver o desafio de reconhecer palavras da forma $0^n1^n$ (mesma quantidade de zeros seguidos pela mesma quantidade de uns), a lógica de funcionamento da máquina em um simulador (*Turing Machine Simulator*) segue o princípio de marcação de pares:

* **Descrição do funcionamento:**

  A máquina começa no estado inicial procurando pelo primeiro `0` à esquerda. Quando o encontra, ela o substitui por um símbolo de marcação (por exemplo, `X`) para indicar que foi processado. Em seguida, ela se move para a direita em direção à área dos `1`s, procurando o primeiro `1` correspondente e o substitui por outro marcador (por exemplo, `Y`). Após marcar um `0` e um `1`, a máquina retorna para a esquerda para encontrar o próximo `0` não marcado, repetindo o processo. Se todos os `0`s forem devidamente emparelhados com os `1`s e nenhum símbolo sobrar sem correspondência, a máquina entra em um estado de aceitação (`ACEITA`). Caso contrário, se sobrar algum `0` sem `1` correspondente (ou vice-versa), a execução é rejeitada (`REJEITA`).

* **Registro dos testes:**

| **Teste** | **Entrada** | **Resultado esperado** | **Resultado obtido** | **Estados percorridos**                                                                                                            |
| --------- | ----------- | ---------------------- | -------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| **1**     | `0011`      | ACEITA                 | XXYY              | `q0` $\rightarrow$ `escreve_X` $\rightarrow$ `procura_1` $\rightarrow$ `escreve_Y` $\rightarrow$ `retorna` $\rightarrow$ `aceita`  |
| **2**     | `000111`    | ACEITA                 | XXXYYY               | `q0` $\rightarrow$ `escreve_X` $\rightarrow$ `procura_1` $\rightarrow$ `escreve_Y` $\rightarrow$ `retorna` $\rightarrow$ `aceita`  |
| **3**     | `00111`     | REJEITA                | XXYY1           | `q0` $\rightarrow$ `escreve_X` $\rightarrow$ `procura_1` $\rightarrow$ `escreve_Y` $\rightarrow$ `retorna` $\rightarrow$ `rejeita` |








![image alt](https://github.com/GustavoRTC7/LFA/blob/main/000111.png?raw=true)
![image alt]()
![image alt]()

## 🧠 Etapa 4 — Reflexão sobre os Limites Computacionais

**Pergunta:** Uma Máquina de Turing consegue resolver qualquer problema? Explique com suas palavras por que existem problemas que não podem ser resolvidos por algoritmos.

**Resposta:**
Não, uma Máquina de Turing não consegue resolver todos os problemas existentes; existem problemas formais que são classificados como não computáveis, o que significa que é matematicamente impossível criar um algoritmo universal capaz de os resolver. A razão fundamental é que o conjunto de todas as funções possíveis é infinitamente maior do que o conjunto de programas finitos que podem ser escritos. Portanto, existem limites lógicos intransponíveis para a computação automática, o que evidencia que os limites da computação não são apenas uma questão de limitação de hardware, velocidade ou falta de otimização, mas sim barreiras matemáticas intransponíveis do que é calculável.

---

## 🎯 Questão Final — Problema para Reflexão

**Problema:** Imagine que você recebeu um problema computacional muito complexo. Como saber se ele é apenas difícil de resolver ou se, na verdade, não existe nenhum algoritmo capaz de resolvê-lo para todos os casos? Explique utilizando os conceitos estudados sobre Máquinas de Turing, computabilidade e limites computacionais.

**Resposta:**
Para saber se um problema carece de uma solução algorítmica, a teoria da computabilidade utiliza demonstrações formais (como o argumento de Turing) para provar que a tentativa de criar um programa resolvedor universal falhará para casos patológicos. Se for provado que o problema é equivalente ou irredutível a problemas indecidíveis conhecidos, conclui-se que ele está além dos limites fundamentais da computação, tornando impossível a criação de um algoritmo que funcione para todos os casos.
