# Gerador de pauta de 1:1

Skill do Claude que gera, direto no chat, uma pauta estruturada para reuniões 1:1 (one-on-one) com membros de equipe — no formato usado pelo Product Owner de **Sites e Portais** no Banco Inter.

## O que ela faz

Ao pedir uma pauta de 1:1, o Claude monta uma agenda em markdown com:

- Tópico de abertura (rapport / como está a semana)
- Tópicos adaptados ao foco escolhido e ao contexto informado (bloqueios, entregas, carreira etc.)
- Tópico de encerramento (combinados / próximos passos)
- Tempo estimado por tópico, distribuído dentro da duração total da reunião

## Quando ela aciona

Sempre que você pedir para **montar, gerar, preparar ou organizar** uma pauta, agenda, roteiro ou pontos de conversa para uma reunião individual com um colaborador — mesmo sem usar a palavra "pauta". Exemplos:

- "monta a pauta do meu 1:1 com o Rafael"
- "vou conversar com a Marina amanhã, me ajuda a organizar os pontos"
- "preciso preparar meu 1:1 com a squad"

## Dados de entrada

| Campo | Obrigatório? | Se não informado |
|---|---|---|
| Nome do colaborador | Sim | Único campo que o Claude vai perguntar se estiver ausente |
| Squad | Não | Omitido/genérico se não ficar claro |
| Duração | Não | Padrão: 30 minutos |
| Foco principal | Não | Padrão: Check-in regular |
| Contexto recente | Não | Pauta fica no nível de perguntas-guia genéricas, sem inventar tarefas ou sistemas |

A skill **não interrompe a conversa** para pedir foco, duração ou contexto — ela assume os padrões acima e gera a pauta direto. Só pergunta se faltar o nome do colaborador.

## Contexto padrão assumido

- Product Owner de tecnologia, Banco Inter, time Sites e Portais
- Squads: Front Web Site, Front Web App, Service/Backend (ou cross-squad)
- Ferramentas do dia a dia: Scrum, Jira, GitLab, SAP, Kanban
- Tom: profissional, direto, português do Brasil

Esse contexto é o padrão, não uma regra fixa — se você pedir uma pauta em outra situação (outro cargo, outra empresa), o Claude adapta.

## Regra mais importante

O Claude **nunca inventa** nomes de tarefas, sistemas, PRs ou projetos que você não mencionou. Se o contexto for genérico, a pauta fica no nível de pergunta-guia (ex: "Como está o andamento das entregas da sprint atual?") em vez de citar algo específico que não foi dito.

## Exemplo

**Entrada:**
> "monta a pauta do meu 1:1 com a Marina amanhã, ela é do Front Web App, terminou a migração do header essa semana e mencionou estar sobrecarregada"

**Saída:**
```
## 1:1 — Marina · Front Web App · 30 minutos · Foco: Check-in regular

**1. Abertura (3 min)**
- Como foi a semana, de forma geral?
- Espaço livre para o que ela quiser trazer

**2. Migração do header (10 min)**
- Como se sentiu com a entrega da migração do header?
- Algo que ficou pendente ou que vale revisitar?

**3. Carga de trabalho (10 min)**
- Ela mencionou estar sobrecarregada — abrir espaço para entender o que está pesando
- O que poderia ser redistribuído ou repriorizado?

**4. Encerramento (7 min)**
- Combinados e próximos passos
- Algo que ela precisa de mim antes da próxima 1:1?
```

## Relação com a ferramenta HTML "Gerador de pauta de 1:1"

Esta skill é independente da ferramenta HTML com o mesmo nome (o artefato com armazenamento de colaboradores e histórico de pautas). Elas compartilham a mesma lógica de geração de pauta, mas a skill responde direto no chat, sem precisar abrir a ferramenta.

## Arquivos

- `SKILL.md` — instruções que o Claude consulta ao acionar a skill
- `README.md` — este arquivo, para referência humana
