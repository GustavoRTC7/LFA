# 🛡️ GuardIA — Sistema Especialista de Filtragem de Mensagens

Projeto acadêmico de Inteligência Artificial desenvolvido para a **Avaliação A1** da disciplina de Linguagens Formais e Autômatos, demonstrando o funcionamento clássico de um Sistema Especialista para filtragem de mensagens (SMS, e-mail e WhatsApp). 

🌐 **Acesse o sistema funcionando online:** [https://avaliacao-a1-sistema-especialista.bolt.host](https://avaliacao-a1-sistema-especialista.bolt.host)

---

## 💡 Tema e Objetivo

Mensagens fraudulentas e indesejadas são um problema crescente. Um Sistema Especialista codifica o conhecimento de um especialista humano (analista de segurança / moderação) na forma de regras `SE ... ENTÃO ...`, permitindo que um software reproduza esse raciocínio de forma transparente e auditável.

O **GuardIA** é uma demonstração didática desse paradigma: toda a lógica é explícita, visível e explicável — ideal para apresentação em sala de aula.

---

## 🏗️ Arquitetura do Sistema Especialista

O projeto segue a arquitetura clássica de um Sistema Especialista, dividida em três componentes:

```text
┌─────────────────────────┐     ┌──────────────────────┐     ┌─────────────────────────┐
│  Interface do Utilizador │     │  Motor de Inferência  │     │   Base de Conhecimento   │
│  (React + Tailwind)      │◄───►│  (inferenceEngine.ts) │◄───►│   (knowledgeBase.ts)     │
│                          │     │  Encadeamento         │     │   Regras de Produção     │
│  • Fatos de entrada      │     │  Progressivo          │     │   SE ... ENTÃO ...       │
│  • Painel de resultado   │     │  (Forward Chaining)   │     │                          │
│  • Base de Conhecimento  │     │                       │     │                          │
└─────────────────────────┘     └──────────────────────┘     └─────────────────────────┘
1. Base de Conhecimento (src/expert/knowledgeBase.ts)Armazena as regras de produção que representam o conhecimento do especialista:RegraCondição (SE)Conclusão (ENTÃO)Risco / Alerta1 — Phishing/GolpeTermos de urgência/financeiro E link presenteRisco Alto (Phishing)🔴 Vermelho2 — Spam ComercialTermos promocionais E remetente desconhecidoRisco Médio (Spam)🟠 Laranja3 — Ruído/Agressividade>40% maiúsculas OU excesso de exclamaçõesRisco Baixo (Spam de Ruído)🟡 Amarelo4 — Segura (padrão)Nenhuma regra anterior satisfeitaMensagem Legítima🟢 Verde2. Motor de Inferência (src/expert/inferenceEngine.ts)Implementa encadeamento progressivo (forward chaining): parte dos fatos de entrada (texto da mensagem + flag de remetente desconhecido) e percorre a base de conhecimento em ordem de prioridade (1 → 4). A primeira regra cujas condições são satisfeitas é disparada e define o veredito. A regra 4 é a cláusula default — só é alcançada se nenhuma outra disparar.3. Interface de Utilizador (src/App.tsx)Área de Entrada (Fatos): campo de texto + checkbox "Remetente desconhecido" + 3 botões de exemplo (golpe bancário, promoção spam, mensagem normal).Painel de Explicabilidade: ao analisar, exibe o veredito com cor de alerta, a regra disparada por extenso e os fatos identificados (palavras-chave/padrões que ativaram o motor).Aba Base de Conhecimento: visualização das regras cadastradas para inspeção durante a apresentação.📂 Estrutura de FicheirosPlaintextsrc/
├── App.tsx                       # Interface do utilizador (fatos + resultado + base)
├── expert/
│   ├── types.ts                  # Tipos partilhados
│   ├── knowledgeBase.ts          # Base de Conhecimento (regras SE...ENTÃO...)
│   └── inferenceEngine.ts        # Motor de Inferência (encadeamento progressivo)
├── main.tsx
└── index.css
⚙️ Como Rodar o Projeto LocalmentePré-requisitos: Node.js 18+.Bash# Instalar dependências
npm install

# Modo de desenvolvimento (http://localhost:5173)
npm run dev

# Build de produção
npm run build

# Pré-visualizar o build
npm run preview

# Verificação de tipos
npm run typecheck
🛠️ Stack TecnológicaReact 18 + TypeScriptVite (bundler / dev server)Tailwind CSS (estilos)lucide-react (ícones)📌 Notas AcadémicasEste projeto é uma demonstração educacional. As regras são intencionalmente simples e transparentes para ilustrar o paradigma de Sistemas Especialistas — não substitui soluções de segurança reais baseadas em machine learning ou heurísticas mais robustas.Desenvolvido para a disciplina de Linguagens Formais e Autômatos.
