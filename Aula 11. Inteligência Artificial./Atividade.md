# Atividade sobre Agentes Inteligentes
**Aula:** 20/10/2026 | **Professora:** Kadidja Valéria | **Inteligência Artificial**  
**Disciplina:** Linguagens Formais e Autômatos | Ciência da Computação  
**Turma:** N1 C.C  

---

## Exercício 2.3

### a. Um agente que detecta apenas informações parciais sobre o estado não pode ser perfeitamente racional.
* **Julgamento:** Falso
* **Justificativa:** Racionalidade não exige onisciência. O agente racional toma a decisão ótima esperada em função exclusivamente daquilo que seus sensores captaram até o momento e do seu conhecimento prévio. A incompletude sensorial restringe a pontuação real máxima que ele pode alcançar no ambiente, mas não o torna irracional diante das opções viáveis.
* **Exemplo / Contraexemplo:** O aspirador de pó em um micromundo de duas salas que monitora unicamente o compartimento em que se encontra. Ele desconhece o estado da outra sala, contudo sua política de limpeza continua perfeitamente racional perante a métrica de desempenho estipulada.

---

### b. Existem ambientes de tarefa nos quais nenhum agente reativo puro pode comportar-se racionalmente.
* **Julgamento:** Verdadeiro
* **Justificativa:** Agentes puramente reativos operam sem memória interna, mapeando diretamente a percepção instantânea para uma ação. Em cenários parcialmente observáveis onde percepções idênticas demandam condutas distintas dependendo do histórico de eventos, um sistema desprovido de estado interno inevitavelmente falhará ou entrará em loops infinitos.
* **Exemplo / Contraexemplo:** Um agente navegando em um labirinto simétrico sem sensores de localização absoluta. Ao encontrar dois cruzamentos visualmente idênticos onde um exige virar à direita e o outro à esquerda para alcançar a saída, a ausência de histórico torna o comportamento racional impossível para um reativo puro.

---

### c. Existe um ambiente de tarefa em que todo agente é racional.
* **Julgamento:** Verdadeiro
* **Justificativa:** A avaliação de racionalidade é subordinada à métrica de desempenho adotada. Caso o critério atribua valores invariantes para qualquer histórico de ações, ou caso exista somente uma ação exequível, qualquer política de tomada de decisão maximiza o retorno esperado de forma idêntica.
* **Exemplo / Contraexemplo:** Um sistema estático cujo único comando executável seja `No-Op` (não operar), ou um ambiente cuja função de avaliação atribua valor fixo constante ($f = 0$) a todos os estados finais possíveis.

---

### d. A entrada para o programa de agente é a mesma que a entrada para a função de agente.
* **Julgamento:** Falso
* **Justificativa:** A função de agente é uma formulação matemática abstrata cujo domínio é a sequência completa de percepções acumuladas desde o início da operação ($P^* \to A$). Por outro lado, a implementação física (o programa de agente) recebe diretamente dos sensores apenas a percepção do instante presente ($p \in P$), cabendo à sua arquitetura interna armazenar o histórico caso precise dele.
* **Exemplo / Contraexemplo:** Em uma arquitetura orientada a tabelas, a busca exige como chave o vetor de todas as entradas anteriores. O programa, no entanto, recebe em sua interface apenas o sinal de entrada do ciclo corrente e faz o encadeamento no buffer local.

---

### e. Toda função de agente é implementável por uma combinação de programa/máquina.
* **Julgamento:** Falso
* **Justificativa:** A função de agente engloba qualquer relação matemática de mapeamento de entradas em ações, incluindo problemas formalmente indecidíveis por modelos computacionais clássicos (limitações da Máquina de Turing) e funções cuja complexidade espacial/temporal inviabiliza a execução sob restrições físicas de hardware.
* **Exemplo / Contraexemplo:** Uma função de agente teórica que devesse receber a descrição de um autômato e decidir deterministicamente se ele paralisa para qualquer entrada arbitrária (Problema da Parada de Turing). Nenhum programa de computador consegue implementar essa função universalmente.

---

### f. Suponha que um agente selecione sua ação uniformemente ao acaso do conjunto de ações possíveis. Existe um ambiente de tarefa determinista em que esse agente é racional.
* **Julgamento:** Verdadeiro
* **Justificativa:** Se a topologia do ambiente for tal que todas as transições conduzam a estados com o mesmo grau de utilidade, ou se o conjunto de ações contiver apenas escolhas equivalentes, a distribuição uniforme de probabilidade na seleção de ações atinge exatamente o mesmo resultado de uma escolha deliberada.
* **Exemplo / Contraexemplo:** Um leilão de envelope fechado onde todos os lances permitidos geram retorno nulo, ou uma sala com duas alavancas funcionais em que acionar qualquer uma delas destrava a porta com a mesma pontuação.

---

### g. É possível para um dado agente ser perfeitamente racional em dois ambientes de tarefa distintos.
* **Julgamento:** Verdadeiro
* **Justificativa:** Racionalidade não acarreta exclusividade ambiental. Contanto que a política de tomadas de decisão maximize a função utilitária em dois domínios operacionais diferentes, a mesma configuração comportamental será plenamente racional em ambos.
* **Exemplo / Contraexemplo:** Um algoritmo ótimo de Minimax para Jogo da Velha operando contra um adversário de força bruta perfeita e, posteriormente, contra um jogador que comete jogadas estritamente aleatórias; ele mantém a racionalidade e não perde em nenhum dos dois contextos.

---

### h. Todo agente é racional em um ambiente não observável.
* **Julgamento:** Falso
* **Justificativa:** A ausência de sensores impede a atualização do estado do mundo via percepção, mas não anula o modelo a priori nem a responsabilidade de executar um plano coerente. Uma política arbitrária continua sendo objetivamente inferior a uma sequência de ações pré-computada que atinja o objetivo com certeza ou alta probabilidade.
* **Exemplo / Contraexemplo:** No problema do aspirador cego em duas salas, a execução em malha aberta da sequência `[Aspirar, Direita, Aspirar]` garante o ambiente limpo em 100% das distribuições iniciais. Um agente que execute `[Esquerda, Esquerda, No-Op]` falhará sistematicamente e será irracional.

---

### i. Um agente jogador de pôquer perfeitamente racional nunca perde.
* **Julgamento:** Falso
* **Justificativa:** Jogos com informações ocultas (cartas adversárias) e componentes estocásticos (embaralhamento) impõem limites teóricos ao controle do desfecho. O agente racional calcula a melhor jogada em termos de valor esperado ($EV+$); a concretização do ganho a curto prazo permanece sujeita à variância estatística das cartas distribuídas.
* **Exemplo / Contraexemplo:** O jogador aposta todas as fichas segurando quatro ases, tendo 98% de chance teórica de vitória, enquanto o oponente paga a aposta com uma probabilidade residual de 2% e acerta a sequência exata no turn/river. A conduta foi matematicamente perfeita, mas resultou em derrota.

---

## Exercício 2.4

### Caso 1 — Jogar futebol
* **P (Desempenho):** Vitórias, saldo de gols, precisão em passes/chutes, desarmes bem-sucedidos, obediência tática, integridade física (ausência de cartões/lesões).
* **E (Ambiente):** Gramado, bola, postes da meta, companheiros de equipe, oponentes, árbitros, torcida, condições climáticas.
* **A (Atuadores):** Membros inferiores (deslocamento, passe, finalização), membros superiores e tronco (posicionamento, equilíbrio), aparelho fonador/sinais manuais (comunicação).
* **S (Sensores):** Sistema visual/câmeras de campo, audição (apito, chamados), sistema proprioceptivo (equilíbrio e cinestesia).

| Propriedade | Classificação | Justificativa |
| :--- | :--- | :--- |
| **Observabilidade** | Parcialmente observável | O campo de visão é angularmente limitado e as decisões táticas mentais dos oponentes são desconhecidas. |
| **Agentes** | Multiagente (cooperativo e competitivo) | Interação simultânea colaborativa com aliados e conflitante contra adversários. |
| **Determinismo** | Estocástico | A dinâmica de rolamento da bola, vento, ressaltos do solo e ações alheias possuem alto grau de incerteza. |
| **Episodicidade** | Sequencial | Cada decisão de passe altera o posicionamento tático e condiciona as jogadas dos minutos seguintes. |
| **Dinamismo** | Dinâmico | Os elementos móveis (bola e atletas) deslocam-se ininterruptamente durante o processamento da ação. |
| **Continuidade** | Contínuo | Espaço geométrico, trajetórias, forças de contato e tempo fluem sem discretização intrínseca. |
| **Conhecimento** | Conhecido | As regras do esporte e a mecânica vetorial básica são familiares ao agente. |

---

### Caso 2 — Explorar os oceanos subterrâneos de Titã
* **P (Desempenho):** Volume e relevância de amostras coletadas, área subsuperficial mapeada, telemetria transmitida com êxito, preservação da integridade estrutural, eficiência energética.
* **E (Ambiente):** Líquido criogênico (mistura água/amônia), relevo rochoso abissal, placas tectônicas de gelo superior, fortes gradientes de pressão e temperatura.
* **A (Atuadores):** Propulsores direcionais de hélice, tanques de lastro hidrostático, braço mecânico de perfuração/amostragem, feixe transmissor de dados.
* **S (Sensores):** Matriz de sonares, espectrômetros de massa, barômetros/termômetros de profundidade, unidades de navegação inercial (IMU), transdutores químicos.

| Propriedade | Classificação | Justificativa |
| :--- | :--- | :--- |
| **Observabilidade** | Parcialmente observável | Ausência de luz solar e alcance restrito dos sonares geram horizontes de percepção muito curtos. |
| **Agentes** | Agente único | Não há outros agentes autônomos disputando recursos ou cooperando na região submersa. |
| **Determinismo** | Estocástico | Correntes termais invisíveis, sedimentação e desgastes mecânicos aleatórios afetam os estados futuros. |
| **Episodicidade** | Sequencial | Decisões de mergulho afetam reservas de energia e a integridade de longo prazo da missão. |
| **Dinamismo** | Dinâmico | O fluido submarino e o equilíbrio térmico da sonda mudam enquanto o computador de bordo calcula rotas. |
| **Continuidade** | Contínuo | Pressão hidrostática, profundidade, velocidade e orientação espacial variam continuamente. |
| **Conhecimento** | Desconhecido | O leito e o comportamento hidrodinâmico de Titã nunca foram catalogados in situ previamente. |

---

### Caso 3 — Comprar livros usados de IA na Internet
* **P (Desempenho):** Custo total minimizado (item + taxa de envio), estado físico do exemplar, velocidade da entrega, confiabilidade do lojista, conformidade com a edição pedida.
* **E (Ambiente):** Plataformas de e-commerce, servidores web, estoques de livreiros, interfaces bancárias de pagamento, tráfego da rede.
* **A (Atuadores):** Envio de requisições HTTP (GET/POST), preenchimento de campos de checkout, disparo de mensagens de negociação, emissão de ordens de pagamento.
* **S (Sensores):** Parsing de documentos HTML/JSON, status de APIs de busca, notificações por e-mail, logs de transação bancária.

| Propriedade | Classificação | Justificativa |
| :--- | :--- | :--- |
| **Observabilidade** | Parcialmente observável | As condições físicas reais do livro e a idoneidade do vendedor são inferidas unicamente por fotos e textos de anúncios. |
| **Agentes** | Multiagente (competitivo e cooperativo) | Concorrência com outros compradores por ofertas limitadas; cooperação transacional com sistemas de venda. |
| **Determinismo** | Estocástico | O estoque pode esgotar em milissegundos ou o pacote pode extraviar no trajeto postal. |
| **Episodicidade** | Sequencial | Gastos presentes limitam a liquidez para compras futuras; aquisições agrupadas reduzem o frete global. |
| **Dinamismo** | Dinâmico | Preços e disponibilidade de exemplares únicos variam em tempo real durante a análise. |
| **Continuidade** | Discreto | Catálogos, cliques, páginas web, moedas e quantidades de livros são grandezas enumeráveis. |
| **Conhecimento** | Conhecido | Os protocolos de navegação web e as regras do comércio eletrônico são preestabelecidos. |

---

### Caso 4 — Jogar uma partida de tênis
* **P (Desempenho):** Conquista de games e sets, índice de primeiro serviço, proporção de winners versus erros não forçados, conservação aeróbica.
* **E (Ambiente):** Quadra demarcada, piso específico (saibro/grama/rápida), rede divisória, bola, oponente, cadeira de arbitragem, correntes de ar.
* **A (Atuadores):** Empunhadura de raquete (angulação e torque do golpe), membros inferiores (arranques e desacelerações motoras), movimentação do tronco.
* **S (Sensores):** Visão focal (trajetória e rotação da bola), audição (som do impacto do encordoamento), propriocepção corporal.

| Propriedade | Classificação | Justificativa |
| :--- | :--- | :--- |
| **Observabilidade** | Parcialmente observável | O estado da quadra e da bola é visível, mas a intenção tática e a fadiga muscular do oponente estão ocultas. |
| **Agentes** | Multiagente competitivo | Estrutura de jogo de soma zero estrita: o objetivo do adversário anula o do agente. |
| **Determinismo** | Estocástico | Efeitos aerodinâmicos na bola, irregularidades no piso e microvariações de batida produzem dispersão. |
| **Episodicidade** | Sequencial | Cada ponto soma para a construção do game, influenciando o desgaste físico e o moral tático. |
| **Dinamismo** | Dinâmico | A bola permanece em trânsito e o oponente se reposiciona durante o tempo de resposta do agente. |
| **Continuidade** | Contínuo | Parâmetros de trajetória, força de impacto e timing temporal são infinitamente graduáveis. |
| **Conhecimento** | Conhecido | O sistema de regras da ITF e a física do impacto da raquete com a bola são previamente determinados. |

---

### Caso 5 — Praticar tênis contra uma parede
* **P (Desempenho):** Manutenção da regularidade de rebatidas, precisão de retorno na área-alvo pintada, taxa de controle técnico.
* **E (Ambiente):** Parede de rebote rígida, piso, bola de treino, raquete, variações de vento local.
* **A (Atuadores):** Braço executor da batida (swing e follow-through), pernas para posicionamento na base da quadra.
* **S (Sensores):** Visão espacial do retorno da bola e marcas de impacto na superfície vertical.

| Propriedade | Classificação | Justificativa |
| :--- | :--- | :--- |
| **Observabilidade** | Completamente observável | Não há oponentes ocultando táticas; as variáveis espaciais relevantes da bola e da parede estão expostas. |
| **Agentes** | Agente único | A parede opera unicamente como um anteparo inanimado sujeito às leis da reflexão mecânica. |
| **Determinismo** | Estocástico | Imperfeições microscópicas no reboco e variações de rotação da bola inserem ruído probabilístico. |
| **Episodicidade** | Sequencial / Quase episódico | Cada rebatida prepara a devolução imediata seguinte, embora os ciclos de treino possam ser reiniciados sem prejuízo cumulativo. |
| **Dinamismo** | Dinâmico | O projétil não interrompe seu curso físico enquanto o atleta planeja o gesto motor. |
| **Continuidade** | Contínuo | As propriedades cinemáticas do movimento variam de forma contínua no espaço e tempo. |
| **Conhecimento** | Conhecido | As leis clássicas da cinemática e colisões elásticas modelam o sistema. |

---

### Caso 6 — Realizar um salto em altura
* **P (Desempenho):** Altura máxima do sarrafo transposta sem derrubá-lo, mínimo de tentativas gastas, controle de integridade biomecânica.
* **E (Ambiente):** Pista de aproximação tartan, suportes reguláveis, sarrafo cilíndrico, colchão de queda, vento.
* **A (Atuadores):** Cadeia cinética de corrida (passadas rítmicas), perna de bloqueio/impulsão vertical, arqueamento espinhal dorsal (técnica Fosbury Flop).
* **S (Sensores):** Percepção visual das marcações de corrida e da altura da barra, canais semicirculares vestibulares (equilíbrio dinâmico).

| Propriedade | Classificação | Justificativa |
| :--- | :--- | :--- |
| **Observabilidade** | Completamente observável | Todos os parâmetros operacionais (distância da barra, altura fixa, limites de pista) estão ao alcance sensorial. |
| **Agentes** | Agente único | Nenhum concorrente interfere mecanicamente durante a tentativa do salto individual. |
| **Determinismo** | Estocástico | Microvariações milimétricas de impulsão na fáscia plantar ou rajadas de ar podem desestabilizar o salto. |
| **Episodicidade** | Sequencial | A corrida de aproximação delimita estritamente o vetor angular e a conversão de energia para a ascensão. |
| **Dinamismo** | Semidinâmico | O sarrafo e a pista permanecem estáticos, mas a passagem do cronômetro oficial de autorização afeta a pontuação/validade. |
| **Continuidade** | Contínuo | Os ângulos das articulações corporais, velocidades e distâncias espaciais são grandezas contínuas. |
| **Conhecimento** | Conhecido | Parâmetros físicos do salto e o livro de regras da modalidade são estritamente tabulados. |

---

### Caso 7 — Participar de um leilão de um item, realizando lances
* **P (Desempenho):** Aquisição do lote abaixo do valor limite interno ($V_{max} - P_{final}$ maximizado), não arrematar caso o preço exceda a reserva.
* **E (Ambiente):** Painel do leiloeiro (físico ou plataforma digital), concorrência de participantes, relógio regressivo de encerramento do lote.
* **A (Atuadores):** Confirmação de lance via protocolo de rede ou gesto, emissão de valor monetário, retirada da disputa.
* **S (Sensores):** Leitura de lances precedentes, valor corrente registrado, confirmação de liderança provisória do lote, temporizador.

| Propriedade | Classificação | Justificativa |
| :--- | :--- | :--- |
| **Observabilidade** | Parcialmente observável | O valor máximo que os concorrentes estão autorizados ou dispostos a despender é totalmente oculto. |
| **Agentes** | Multiagente competitivo | Estrutura de concorrência pura onde o lance de um agente bloqueia o benefício marginal dos demais. |
| **Determinismo** | Determinístico (estratégico) | O efeito do incremento do lance obedece rigorosamente às regras formais do evento; a variação externa decorre de outros agentes. |
| **Episodicidade** | Sequencial | Cada incremento monetário altera a base de custo dos lances seguintes e reconfigura as estratégias vigentes. |
| **Dinamismo** | Dinâmico | Os competidores emitem novos lances e o temporizador retrocede enquanto a decisão de cobertura é processada. |
| **Continuidade** | Discreto | Os passos de lance são escalonados em moedas fracionadas e o conjunto de ações (cobrir/passar) é finito. |
| **Conhecimento** | Conhecido | Os critérios do edital do leilão (regras de incremento e encerramento) são fixados previamente. |

---

### Comparação Final

#### 1. O que muda entre jogar tênis contra outra pessoa e praticar contra uma parede?
A transformação primária reside na **agência do interlocutor**. Diante de um tenista humano, o ambiente é **multiagente competitivo**, exigindo modelar estratégias e antecipar o engano; o adversário oculta sua intenção e ajusta o spin da bola deliberadamente. Contra a parede, o ecossistema colapsa para **agente único**, onde o obstáculo é passivo e segue estritamente equações clássicas de colisão newtoniana, dispensando inferência adversária.

#### 2. Por que comprar livros usados pode exigir decisões com informações incompletas?
A incompletude deriva da **observabilidade parcial intrínseca ao comércio digital**. O agente de software não inspeciona o objeto em mãos; acessa somente representações imperfeitas (metadados de terceiros, fotos estáticas e índices de reputação). Além disso, fatores críticos como a preservação física das páginas e o risco de inadimplência da entrega representam variáveis ocultas que forçam o agente a atuar sob expectativas probabilísticas de utilidade.

#### 3. Como outros agentes influenciam futebol e leilões?
Em ambas as situações, os agentes externos operam como os principais vetores de **incerteza dinâmica**:
* No **futebol**, a influência é mista: requer coordenação estrita com o subconjunto cooperativo (linhas de passe, cobertura defensiva) e antecipação reativa contra o subconjunto antagônico (interceptações, dribles).
* No **leilão**, a pressão é estritamente concorrencial: os agentes rivais modulam diretamente o preço de corte pelo seu poder econômico. Um competidor agressivo dita o valor monetário de transição, forçando o agente a reavaliar sua permanência sem que haja qualquer interação mecânica ou física entre eles.

---

## Exercício 2.5

### Agente
* **Definição:** Entidade dotada de capacidade perceptual operando por meio de sensores e de intervenção sobre o ecossistema por meio de atuadores. Representa a instância que processa estímulos contextuais para produzir respostas.
* **Exemplo:** Um sistema de piloto automático veicular que lê faixas da via por sensores ultrassônicos/câmeras e atua nos servomotores da direção.

### Função de Agente
* **Definição:** Mapeamento conceitual/matemático formal que associa qualquer histórico sequencial finito de percepções ($P^*$) a uma ação correspondente ($A$). É uma abstração que caracteriza a política operacional do agente de ponta a ponta.
* **Exemplo:** A especificação teórica que dita: se a sequência for `(Luz_Vermelha, Objeto_a_5m)`, a ação obrigatória é `Frear`.

### Programa de Agente
* **Definição:** A concretização computacional da função de agente construída para rodar sobre uma arquitetura física delimitada. Ao contrário da função abstrata, recebe do ambiente apenas a entrada sensorial corrente do ciclo e gerencia suas próprias estruturas de memória.
* **Exemplo:** Uma rotina `getAction(sensor_data)` executada pelo microcontrolador de bordo de um robô móvel.

### Racionalidade
* **Definição:** Princípio de otimização segundo o qual o agente escolhe, a cada instante, a ação capaz de maximizar a expectativa de sua medida de desempenho, considerando as percepções acumuladas e o conhecimento prévio incorporado.
* **Exemplo:** Um sistema hospitalar que recomenda a dosagem de um fármaco minimizando o risco calculado de efeitos colaterais com base nos exames disponíveis, mesmo que o paciente venha a sofrer uma reação idiossincrática imprevisível.

### Autonomia
* **Definição:** Grau de independência com que um agente se adapta e orienta suas escolhas a partir do próprio aprendizado gerado pelas experiências vividas, em oposição a depender exclusivamente de parâmetros pré-fixados pelo projetista.
* **Exemplo:** Um aspirador robótico que recalcula a rota diária ao notar que determinados cômodos acumulam poeira mais rápido que outros em certas épocas do ano.

### Agente Reativo Simples
* **Definição:** Arquitetura que condiciona a seleção de cada ação exclusivamente à percepção momentânea atual, operando por regras diretas do tipo condição-ação e desconsiderando completamente o passado sensorial.
* **Exemplo:** Um sensor crepuscular de iluminação pública que aciona as lâmpadas quando a luminescência atinge um patamar inferior a determinado limiar, sem registrar há quanto tempo está escuro.

### Agente Reativo Baseado em Modelo
* **Definição:** Agente que contorna a observabilidade parcial mantendo um estado interno (memória) construído a partir de modelos que descrevem como o mundo evolui naturalmente e como as suas próprias ações alteram o cenário ao longo do tempo.
* **Exemplo:** Um veículo autônomo que infere que um pedestre oculto atrás de um caminhão continua se movendo em direção à faixa de pedestres, mesmo sem contato visual direto momentâneo.

### Agente Baseado em Objetivos
* **Definição:** Estrutura que combina as informações de estado a um descritor explícito de situações desejáveis (metas), utilizando algoritmos de busca e planejamento de trajetórias para selecionar caminhos que alcancem essas metas.
* **Exemplo:** Um sistema de xadrez computacional que avalia árvores de jogadas com o propósito terminal explícito de colocar o rei oponente em xeque-mate.

### Agente Baseado na Utilidade
* **Definição:** Sistema que aplica uma função escalar contínua para graduar diferentes estados atingíveis de acordo com a sua conveniência ou qualidade, permitindo arbitrar entre objetivos concorrentes sob cenários de incerteza e balancear custos e benefícios.
* **Exemplo:** Uma aplicação de navegação por rotas que calcula trajetórias equilibrando menor tempo, custo com pedágios e conforto viário.

### Agente com Aprendizagem
* **Definição:** Arquitetura dividida em componentes de operação e aperfeiçoamento: o elemento de aprendizado assimila dados da experiência e modifica o elemento de desempenho; o crítico fornece feedback sobre os avanços segundo padrões externos; e o gerador de problemas introduz exploração em cenários novos.
* **Exemplo:** Um algoritmo de recomendação de vídeos que reorganiza o feed de sugestões do usuário a partir da análise das taxas de clique e tempo de retenção observados.

---

## Síntese com Autômatos Finitos

### Modelagem do Caso 7 (Leilão com Lances Abertos)
Para evidenciar o papel da memória e do estado interno em agentes situados, o agente de leilão com limite orçamentário $L$ é formulado como um Autômato Finito com Saída (Máquina de Mealy), definido formalmente pela 6-tupla:

$$M = \langle Q, \Sigma, \Delta, \delta, \lambda, q_0 \rangle$$

#### 1. Conjunto de Estados Internos ($Q$)
* **$q_0$ (Aguardando / Desafiante):** O agente não detém o maior lance atual e avalia o mercado.
* **$q_1$ (Liderando / Arrematante Temporário):** O agente emitiu a proposta mais recente e detém a posse provisória do lote.
* **$q_2$ (Retirado / Desistência):** O preço de corte ultrapassou o teto financeiro $L$ ou o pregão foi finalizado; encerramento de operações.

#### 2. Alfabeto de Percepções / Entradas ($\Sigma$)
* **$p_{viável}$:** Concorrente efetuou novo lance, e o próximo lance regulamentar ($Preço + \Delta$) permanece $\le L$.
* **$p_{inviável}$:** Concorrente efetuou novo lance, mas o próximo lance regulamentar ($Preço + \Delta$) excede o limite $L$.
* **$p_{fim}$:** Percepção de encerramento do leilão (martelo batido).

#### 3. Alfabeto de Ações / Saídas ($\Delta$)
* **$a_{lance}$:** Emitir nova oferta com valor recalculado ($Preço + \Delta$).
* **$a_{esperar}$:** Manter posição sem gerar despesas.
* **$a_{desistir}$:** Declarar saída da disputa e encerrar a participação.

---

### Tabela de Transições e Saídas $(\delta, \lambda)$

| Estado Atual ($Q$) | Percepção ($\Sigma$) | Próximo Estado ($Q'$) | Ação Emitida ($\Delta$) | Interpretação Operacional |
| :---: | :---: | :---: | :---: | :--- |
| **$q_0$** | $p_{viável}$ | **$q_1$** | $a_{lance}$ | Supera o valor atual e assume a liderança provisória. |
| **$q_0$** | $p_{inviável}$ | **$q_2$** | $a_{desistir}$ | O preço cobriu a margem orçamentária; sai da disputa. |
| **$q_0$** | $p_{fim}$ | **$q_2$** | $a_{esperar}$ | Sessão fechada sem posse; registra a perda do lote. |
| **$q_1$** | $p_{viável}$ | **$q_1$** | $a_{lance}$ | Lance coberto por adversário; contra-ataca dentro do teto $L$. |
| **$q_1$** | $p_{inviável}$ | **$q_2$** | $a_{desistir}$ | Cobertura adversária inviabilizou o teto; abandona o leilão. |
| **$q_1$** | $p_{fim}$ | **$q_2$** | $a_{esperar}$ | Sessão fechada com liderança mantida; registra vitória e arremate. |
| **$q_2$** | Qualquer | **$q_2$** | $a_{esperar}$ | Estado absorvente: processo inativo até o encerramento. |

---

### Análise do Papel do Estado Interno
A percepção $p_{fim}$ é sintaticamente idêntica quer o agente esteja em $q_0$ ou em $q_1$. Um agente puramente reativo (sem memória) seria incapaz de determinar o resultado da negociação ao receber $p_{fim}$, pois a percepção instantânea isolada omite a autoria do lance líder.

O autômato soluciona essa observabilidade parcial retendo a informação do histórico no estado interno:
* Chegar a $p_{fim}$ a partir de **$q_1$** consolida a vitória (o lance vencedor foi emitido anteriormente pelo agente).
* Chegar a $p_{fim}$ a partir de **$q_0$** confirma a perda.

O estado interno funciona como uma compressão suficiente da sequência de percepções passadas, validando a transição do agente para uma arquitetura baseada em modelo.

---

### Limitações do Modelo Finito
Este modelo formal abstrai simplificações severas:
1. **Dimensão Temporal Contínua:** Desconsidera a janela temporal entre lances, impedindo estratégias de *sniping* (disparar lances no último segundo para evitar a reação de outros participantes).
2. **Rigidez Paramétrica:** O teto de reserva $L$ é estático, ignorando atualizações de valor com base no interesse percebido dos concorrentes.
3. **Ausência de Estimação de Adversários:** Não constrói um perfil dos rivais para prever comportamentos agressivos ou conservadores, operando como uma máquina estritamente determinística de regras reativas.

---

## Referências

* RUSSELL, Stuart; NORVIG, Peter. **Inteligência Artificial: Uma Abordagem Moderna**. 3. ed. Rio de Janeiro: Elsevier, 2013. Cap. 2 (Agentes Inteligentes).