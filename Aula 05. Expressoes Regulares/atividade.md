Respostas das Atividades - Expressões Regulares
Linguagens Formais e Autômatos | Engenharia de Software | Profa. Kadidja Valéria

1. Exercício Guiado (Slide 20)
Questão 1: Sobre {0,1}, descreva palavras que terminam em 00
 Expressão Regular Clássica: (0 | 1)* 00
 Regex (com âncoras): ^[01]*00$
 Explicação: A cadeia começa com qualquer combinação de 0 e 1 (inclusive nenhuma) e termina
obrigatoriamente com dois zeros seguidos.
 Exemplos que aceita: 00, 100, 000, 110100
 Exemplos que rejeita: ε (vazio), 0, 1, 01, 10, 1001
Questão 2: Sobre {a,b}, descreva palavras com exatamente dois &#39;a&#39;
 Expressão Regular Clássica: b* a b* a b*
 Regex (com âncoras): ^b*ab*ab*$
 Explicação: Garante que existem exatamente duas letras &#39;a&#39;, enquanto a letra &#39;b&#39; pode aparecer
qualquer quantidade de vezes antes, no meio ou no fim.
 Exemplos que aceita: aa, baa, aba, aab, bbabbabbb
 Exemplos que rejeita: ε, a, b, aaa, baaab
Questão 3: Crie um identificador com duas maiúsculas, três algarismos e uma minúscula opcional
 Expressão Regular Clássica: [A-Z][A-Z] [0-9][0-9][0-9] ( [a-z] | ε )
 Regex (com âncoras): ^[A-Z]{2}[0-9]{3}[a-z]?$
 Explicação: Valida 2 letras maiúsculas seguidas de 3 números e no máximo 1 letra minúscula ao
final.
 Exemplos que aceita: AB123, XY000, SP202a, DF999z
 Exemplos que rejeita: A123, ABC123, AB12, AB1234, AB123ab, ab123
2. Desafio: Matrícula Acadêmica (Slides 21 e 22)
Regra: CURSO-ANO-NÚMERO-TURNO sem caracteres extras.
 Regex completa: ^(CCO|ESW|SIS)-202[4-9]-[0-9]{4}-[MTN]$
Explicação dos blocos:
 CURSO: (CCO|ESW|SIS) aceita apenas uma dessas três siglas.
 ANO: 202[4-9] valida os anos entre 2024 e 2029.
 NÚMERO: [0-9]{4} exige exatamente 4 algarismos.
 TURNO: [MTN] permite apenas M (matutino), T (vespertino) ou N (noturno).
Casos de Teste:

 Aceitos (Válidos): ESW-2026-0001-N, CCO-2024-1234-M, SIS-2029-9999-T
 Rejeitados (Inválidos): ADM-2026-0001-N (curso errado), ESW-2023-0001-N (ano fora), ESW-2026-
001-N (faltam dígitos), ESW-2026-0001-X (turno inválido)
3. Questões para Reflexão (Slide 23)
1. Toda expressão regular formal representa uma linguagem regular?
Sim. Pelo Teorema de Kleene, toda expressão regular formal define exatamente uma linguagem regular
reconhecível por autômatos finitos.
2. Toda linguagem regular possui uma expressão regular?
Sim. Pelo mesmo princípio de equivalência, qualquer linguagem regular pode ser convertida para uma
expressão regular (por exemplo, pelo método de eliminação de estados de um autômato).
3. Como uma Regex se relaciona com DFA e NFA?
Possuem o mesmo poder computacional. Uma Regex pode ser convertida em um AFN (NFA com
transições vazias pela construção de Thompson), que depois pode ser transformado em um AFD (DFA
pelo método dos subconjuntos).
4. Quais extensões de motores de Regex não pertencem à definição clássica?
Backreferences (retrovisores como \1), lookaheads/lookbehinds e recursão. Motores práticos com essas
extensões conseguem reconhecer padrões além das linguagens regulares clássicas.
5. Por que a linguagem L = {aⁿbⁿ | n ≥ 0} não pode ser reconhecida por um DFA?
Porque autômatos finitos têm memória limitada (número finito de estados) e não conseguem contar a
quantidade de letras &#39;a&#39; para comparar com a quantidade de &#39;b&#39; para um n arbitrariamente grande (fato
comprovado pelo Lema do Bombeamento).
