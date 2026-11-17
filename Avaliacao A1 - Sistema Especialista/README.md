# 🛡️ GuardIA — Sistema Especialista de Filtragem de Mensagens

Projeto acadêmico de Inteligência Artificial desenvolvido para a **Avaliação A1** da disciplina de Linguagens Formais e Autômatos, demonstrando o funcionamento clássico de um Sistema Especialista para filtragem de mensagens (SMS, e-mail e WhatsApp), O sistema identifica phishing, spam comercial e spam de ruído a partir de uma base de regras de produção avaliada por um motor de inferência com **encadeamento progressivo** (*forward chaining*).


🌐 **Acesse o sistema funcionando online:** [https://avaliacao-a1-sistema-especialista.bolt.host](https://avaliacao-a1-sistema-especialista.bolt.host)


## Tema

Mensagens fraudulentas e indesejadas são um problema crescente. Um Sistema
Especialista codifica o conhecimento de um especialista humano (analista de
segurança / moderação) na forma de regras **SE ... ENTÃO ...**, permitindo
que um software reproduza esse raciocínio de forma transparente e auditável.

O GuardIA é uma demonstração didática desse paradigma: toda a lógica é
explícita, visível e explicável — ideal para apresentação em sala de aula.

## Arquitetura do Sistema Especialista

O projeto segue a arquitetura clássica de um Sistema Especialista, dividida em
três componentes:

```
┌─────────────────────────┐     ┌──────────────────────┐     ┌─────────────────────────┐
│  Interface do Utilizador │     │  Motor de Inferência  │     │   Base de Conhecimento   │
│  (React + Tailwind)      │◄───►│  (inferenceEngine.ts) │◄───►│   (knowledgeBase.ts)     │
│                          │     │  Encadeamento         │     │   Regras de Produção     │
│  • Fatos de entrada      │     │  Progressivo          │     │   SE ... ENTÃO ...       │
│  • Painel de resultado   │     │  (Forward Chaining)   │     │                          │
│  • Base de Conhecimento  │     │                       │     │                          │
└─────────────────────────┘     └──────────────────────┘     └─────────────────────────┘
```

### 1. Base de Conhecimento (`src/expert/knowledgeBase.ts`)

Armazena as regras de produção que representam o conhecimento do especialista:

| Regra | Condição (SE) | Conclusão (ENTÃO) | Risco |
|-------|---------------|-------------------|-------|
| **1 — Phishing/Golpe** | Termos de urgência/financeiro **E** link presente | Risco Alto (Phishing) | 🔴 Vermelho |
| **2 — Spam Comercial** | Termos promocionais **E** remetente desconhecido | Risco Médio (Spam) | 🟠 Laranja |
| **3 — Ruído/Agressividade** | >40% maiúsculas **OU** excesso de exclamações | Risco Baixo (Spam de Ruído) | 🟡 Amarelo |
| **4 — Segura (padrão)** | Nenhuma regra anterior satisfeita | Mensagem Legítima | 🟢 Verde |

### 2. Motor de Inferência (`src/expert/inferenceEngine.ts`)

Implementa **encadeamento progressivo**: parte dos fatos de entrada (texto da
mensagem + flag de remetente desconhecido) e percorre a base de conhecimento
em ordem de prioridade (1 → 4). A primeira regra cujas condições são
satisfeitas é **disparada** e define o veredito. A regra 4 é a cláusula
*default* — só é alcançada se nenhuma outra disparar.

### 3. Interface do Utilizador (`src/App.tsx`)

- **Área de Entrada (Fatos):** campo de texto + checkbox "Remetente
  desconhecido" + 3 botões de exemplo (golpe bancário, promoção spam,
  mensagem normal).
- **Painel de Explicabilidade:** ao analisar, exibe o veredito com cor de
  alerta, a regra disparada por extenso e os fatos identificados
  (palavras-chave/padrões que ativaram o motor).
- **Aba Base de Conhecimento:** visualização das regras cadastradas para
  inspeção durante a apresentação.

## Estrutura de Ficheiros

```
src/
├── App.tsx                       # Interface do utilizador (fatos + resultado + base)
├── expert/
│   ├── types.ts                  # Tipos partilhados
│   ├── knowledgeBase.ts          # Base de Conhecimento (regras SE...ENTÃO...)
│   └── inferenceEngine.ts        # Motor de Inferência (encadeamento progressivo)
├── main.tsx
└── index.css
```

## Como Rodar o Projeto

Pré-requisitos: **Node.js 18+**.

```bash
# Instalar dependências
npm install

# Modo de desenvolvimento (http://localhost:5173)
npm run dev

# Build de produção
npm run build

# Pré-visualizar o build
npm run preview

# Verificação de tipos
npm run typecheck
```

## Stack

- **React 18** + **TypeScript**
- **Vite** (bundler / dev server)
- **Tailwind CSS** (estilos)
- **lucide-react** (ícones)

## Notas Académicas

Este projeto é uma demonstração educacional. As regras são intencionalmente
simples e transparentes para ilustrar o paradigma de Sistemas Especialistas —
não substitui soluções de segurança reais baseadas em machine learning ou
heurísticas mais robustas.

---

Desenvolvido para a disciplina de Linguagens Formais e Autômatos.
