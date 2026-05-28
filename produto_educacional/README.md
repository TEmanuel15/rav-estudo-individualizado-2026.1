# Proposta de Produto Educacional Online — QoS em Redes de Alta Velocidade

## Visão Geral

**Nome:** QoSLab — Plataforma Interativa de Análise e Síntese em Qualidade de Serviço

**Formato:** Aplicação web single-page (SPA) com quatro módulos educacionais: mapa conceitual interativo, simulador de parâmetros de QoS, banco de estudos de caso e assistente de planejamento com geração de documento.

**Objetivo:** Permitir que o estudante transite do conceito teórico à aplicação prática de QoS por meio de simulações, estudos de caso reais e síntese visual de planejamentos de rede — consolidando os seis itens da ementa da disciplina Redes de Alta Velocidade.

**Público-alvo:** Estudantes de graduação em Engenharia de Computação, Ciência da Computação e Telecomunicações com conhecimento prévio de redes TCP/IP (*Transmission Control Protocol/Internet Protocol*).

---

## Stack Tecnológica

| Camada | Tecnologia | Justificativa |
|---|---|---|
| Framework frontend | React 18 + TypeScript | Componentização, tipagem e ecossistema maduro |
| Roteamento | React Router v6 | Navegação entre módulos sem reload |
| Estilo | Tailwind CSS | Utilitário, sem CSS customizado extenso |
| Gráficos e simulações | Chart.js + React-Chartjs-2 | Gráficos de linha/barra em tempo real |
| Mapa conceitual | React Flow | Grafo interativo com nós e arestas navegáveis |
| Geração de PDF | jsPDF + html2canvas | Export do documento de planejamento no browser |
| Build | Vite | Build rápido, HMR nativo |
| Hospedagem | GitHub Pages | Gratuito, deploy via GitHub Actions |
| Controle de versão | Git + GitHub | Histórico e CI/CD |

Toda a lógica de simulação roda no browser (sem backend). Não há banco de dados — os estudos de caso e conteúdos são arquivos JSON estáticos servidos junto ao bundle.

---

## Requisitos Funcionais

### RF01 — Navegação geral
- O sistema deve exibir um menu de navegação persistente com acesso a todos os módulos.
- O sistema deve indicar visualmente o módulo ativo.
- O sistema deve ser responsivo para telas de 1024px ou mais (uso em desktop/notebook).

### RF02 — Módulo Mapa Conceitual
- O sistema deve exibir um grafo com nós representando conceitos da ementa (protocolos, mecanismos, parâmetros, classes de aplicação).
- O sistema deve permitir clicar em um nó para abrir um painel lateral com definição, parâmetros-chave e referências.
- O sistema deve permitir filtrar os nós por categoria (ex.: "Protocolos de transporte", "Mecanismos de QoS", "Tecnologias de LAN").
- O sistema deve destacar visualmente as arestas de dependência ao selecionar um nó.
- O sistema deve permitir zoom e pan no grafo.

### RF03 — Módulo Simulador
- O sistema deve oferecer cinco cenários de simulação independentes.
- Cada cenário deve expor sliders ou campos numéricos para os parâmetros configuráveis.
- O sistema deve atualizar os gráficos de resultado em tempo real conforme os parâmetros são alterados.
- O sistema deve exibir um painel de interpretação textual do resultado (ex.: "MOS — *Mean Opinion Score* — abaixo de 3,5 — qualidade insatisfatória para VoIP — *Voice over IP*").
- O cenário de controle de congestionamento deve permitir comparar dois algoritmos simultaneamente em gráficos sobrepostos.

### RF04 — Módulo Estudos de Caso
- O sistema deve listar os estudos de caso com título, setor e nível de dificuldade.
- Cada caso deve ser exibido em etapas sequenciais: contextualização → análise guiada → solução comentada → lição aprendida.
- O sistema deve registrar localmente (localStorage) quais casos o usuário já concluiu.
- O sistema deve exibir perguntas intermediárias com resposta revelável (o estudante tenta responder antes de ver a solução).

### RF05 — Módulo Planejamento
- O sistema deve guiar o usuário por um formulário de seis etapas sequenciais.
- O sistema deve validar os campos obrigatórios antes de avançar cada etapa.
- O sistema deve gerar sugestões automáticas de DSCP (*Differentiated Services Code Point* — Ponto de Código de Serviços Diferenciados) e mecanismo de fila com base nas aplicações selecionadas pelo usuário.
- O sistema deve calcular automaticamente a largura de banda total com overhead de protocolo.
- O sistema deve gerar e fazer download de um documento PDF com todas as decisões e cálculos ao final.
- O sistema deve permitir salvar e retomar o planejamento em andamento via localStorage.

---

## Requisitos Não Funcionais

| ID | Requisito |
|---|---|
| RNF01 | A aplicação deve funcionar nos navegadores Chrome, Firefox e Edge nas últimas duas versões |
| RNF02 | A aplicação não deve exigir instalação, cadastro ou autenticação |
| RNF03 | O carregamento inicial deve ocorrer em menos de 3 segundos em conexão de 10 Mbps |
| RNF04 | Toda a lógica deve executar no cliente — nenhuma requisição a servidor externo além dos assets estáticos |
| RNF05 | O código deve ser organizado por módulo, com componentes reutilizáveis e separação entre lógica de simulação e apresentação |
| RNF06 | O PDF gerado deve ter no mínimo as seções: cabeçalho do projeto, tabela de aplicações × QoS (*Quality of Service* — Qualidade de Serviço), marcação DSCP, dimensionamento de banda e política de filas |

---

## Estrutura de Páginas

### Página 1 — Home (`/`)

**Propósito:** Apresentar o produto e orientar o estudante sobre como usar cada módulo.

**Componentes:**
- Hero com nome do produto, descrição em uma frase e botão "Começar"
- Grade de quatro cards, um por módulo, cada um com ícone, título, descrição de duas linhas e link de acesso
- Barra de progresso global mostrando quantos estudos de caso foram concluídos (lido do localStorage)
- Rodapé com referências bibliográficas da ementa

---

### Página 2 — Mapa Conceitual (`/mapa`)

**Propósito:** Síntese visual das relações entre os conceitos da disciplina.

**Layout:**
```
┌──────────────────────────────────────────────────────────┐
│  Filtros: [Todos] [Protocolos] [Mecanismos QoS] [LANs]   │
│           [Aplicações] [Parâmetros]                      │
├──────────────────────────────────┬───────────────────────┤
│                                  │  PAINEL LATERAL       │
│         GRAFO INTERATIVO         │  (visível ao          │
│         (React Flow)             │   clicar em nó)       │
│                                  │                       │
│  [nó: RTP] ──► [nó: RTCP]        │  Nome: RTP            │
│      │                           │  Categoria: Protocolo │
│      ▼                           │  Definição: ...       │
│  [nó: VoIP]                      │  Parâmetros: ...      │
│                                  │  Ver também: RTCP,    │
│                                  │  SIP, QoS             │
├──────────────────────────────────┴───────────────────────┤
│  [+] Zoom   [-] Zoom   [⊙] Centralizar                   │
└──────────────────────────────────────────────────────────┘
```

**Nós do grafo (agrupados por categoria):**

- *Protocolos de transporte:* TCP, UDP, RTP, RTCP, QUIC
- *Protocolos de sinalização:* SIP, SDP, RSVP
- *Mecanismos de QoS:* IntServ, DiffServ, DSCP, PHB (EF, AF, BE), ECN, RED/WRED
- *Controle de congestionamento:* Slow Start, CUBIC, BBR, Token Bucket, Leaky Bucket
- *Tecnologias de LAN:* Fast Ethernet, Gigabit Ethernet, 10GbE, Wi-Fi 6, Wi-Fi 7
- *Tecnologias WAN/móvel:* DWDM, 5G NR, SDN, NFV
- *Parâmetros de QoS:* Latência, Jitter, MOS, BDP, Throughput
- *Classes de aplicação:* VoIP, Videoconferência, Streaming, Jogos online

---

### Página 3 — Simulador (`/simulador`)

**Propósito:** Experimentação prática de parâmetros de QoS com feedback visual imediato.

**Layout geral:**
```
┌──────────────────────────────────────────────────────────┐
│  Cenários: [Rede Convergente] [Congestionamento TCP]     │
│            [Token Bucket] [DiffServ] [SLA Operadora]     │
├───────────────────────────┬──────────────────────────────┤
│  PAINEL DE PARÂMETROS     │  GRÁFICOS DE RESULTADO       │
│                           │                              │
│  Parâmetro 1: [slider]    │  Gráfico principal           │
│  Parâmetro 2: [slider]    │                              │
│  Parâmetro 3: [campo]     │  Gráfico secundário          │
│                           │                              │
│  [Resetar padrões]        ├──────────────────────────────┤
│                           │  INTERPRETAÇÃO               │
│                           │  "MOS = 3.2 — qualidade      │
│                           │   limítrofe para VoIP"       │
└───────────────────────────┴──────────────────────────────┘
```

**Cenário 3A — Rede Convergente:**

| Parâmetro configurável | Faixa |
|---|---|
| Capacidade do enlace | 10 – 1000 Mbps |
| Nº de chamadas VoIP simultâneas | 1 – 200 |
| Nº de sessões de vídeo HD | 1 – 50 |
| Codec de voz | G.711 / G.729 / Opus |

Saídas: ocupação do enlace por classe (gráfico de área empilhada), MOS (*Mean Opinion Score* — Pontuação Média de Opinião) estimado via E-model (ITU-T G.107), alerta de violação de SLA (*Service Level Agreement* — Acordo de Nível de Serviço).

**Cenário 3B — Controle de Congestionamento TCP:**

| Parâmetro configurável | Faixa |
|---|---|
| Algoritmo | Reno / CUBIC / BBR (*Bottleneck Bandwidth and Round-trip propagation time*) |
| RTT (*Round-Trip Time* — tempo de ida e volta) | 10 – 300 ms |
| Capacidade do gargalo | 1 – 1000 Mbps |
| Taxa de perda | 0 – 5% |

Saídas: evolução da cwnd (*congestion window* — janela de congestionamento) ao longo do tempo (dois algoritmos sobrepostos), throughput médio, comparação de eficiência.

**Cenário 3C — Token Bucket:**

| Parâmetro configurável | Faixa |
|---|---|
| Taxa de token (r) | 1 – 100 Mbps |
| Tamanho do balde (b) | 1 – 10000 KB |
| Perfil de entrada | constante / rajada periódica / personalizado |

Saídas: taxa de entrada vs. taxa de saída vs. nível do balde ao longo do tempo, pacotes descartados.

**Cenário 3D — DiffServ:**

| Parâmetro configurável | Faixa |
|---|---|
| Mecanismo de fila | PQ (*Priority Queuing*) / WFQ (*Weighted Fair Queuing*) / LLQ (*Low Latency Queuing*) + CBWFQ (*Class-Based Weighted Fair Queuing*) |
| Carga por classe: EF (*Expedited Forwarding*), AF (*Assured Forwarding*), BE (*Best Effort*) | 0 – 100% do enlace |
| Capacidade do enlace | 10 – 10000 Mbps |

Saídas: latência média por classe, jitter por classe, descarte por classe, starvation indicator para BE.

**Cenário 3E — SLA em Operadora:**

Réplica do exercício da Lista 06 Q5, com os três planos (Premium, Business, Standard) e carga ajustável. Saída: tabela de SLA contratado × SLA entregue com indicadores verde/amarelo/vermelho.

---

### Página 4 — Estudos de Caso (`/casos`)

**Propósito:** Desenvolvimento do raciocínio de análise e síntese por meio de problemas contextualizados.

**Sub-página 4A — Lista de casos (`/casos`):**
```
┌───────────────────────────────────────────────────────────┐
│  Filtros: [Todos] [VoIP] [Data Center] [Operadora]        │
│           [Telepresença] [Jogos]           [✓ Concluídos] │
├───────────────────────────────────────────────────────────┤
│  ┌──────────────────────────────────────────────────┐     │
│  │ ✓  Caso 01 — VoIP Corporativo      ● Básico      │     │
│  │    Migração de PABX (Central Telefônica Privada) │     │
│  │    para VoIP em 500 ramais                       │     │
│  │                              [Acessar →]         │     │
│  └──────────────────────────────────────────────────┘     │
│  ┌──────────────────────────────────────────────────┐     │
│  │    Caso 02 — Data Center 10GbE    ●● Médio       │     │
│  │    Projeto de switching com sobresubscrição      │     │
│  │                              [Acessar →]         │     │
│  └──────────────────────────────────────────────────┘     │
│  ... (5 casos no total)                                   │
└───────────────────────────────────────────────────────────┘
```

**Sub-página 4B — Caso individual (`/casos/:id`):**
```
┌──────────────────────────────────────────────────────────┐
│  ← Voltar   Caso 01 — VoIP Corporativo                   │
│  Progresso: [████████░░] Etapa 3 de 4                    │
├──────────────────────────────────────────────────────────┤
│                                                          │
│  [1. Contexto] [2. Análise] [3. Solução] [4. Lição]      │
│       ✓             ✓           ativo                    │
│                                                          │
│  Conteúdo da etapa atual...                              │
│                                                          │
│  ┌───────────────────────────────────────────────────┐   │
│  │ Pergunta intermediária:                           │   │
│  │ "Qual codec você escolheria para minimizar        │   │
│  │  o consumo de banda mantendo MOS ≥ 4?"            │   │
│  │                                                   │   │
│  │ [Escreva sua resposta]                            │   │
│  │                           [Ver resposta sugerida] │   │
│  └───────────────────────────────────────────────────┘   │
│                                                          │
│                              [← Anterior] [Próxima →]    │
└──────────────────────────────────────────────────────────┘
```

---

### Página 5 — Planejamento (`/planejamento`)

**Propósito:** Conduzir o estudante pelo processo completo de projeto de QoS e gerar um documento exportável.

**Etapa 1 — Identificação do projeto:**
- Campos: nome do projeto, tipo de organização (corporativa / operadora / data center), número de usuários, observações gerais

**Etapa 2 — Levantamento de aplicações:**
- Tabela editável onde o estudante adiciona as aplicações do cenário
- Para cada aplicação: nome, tipo (VoIP / vídeo / dados / backup), usuários simultâneos, bitrate estimado
- O sistema preenche automaticamente os parâmetros de QoS recomendados (latência, jitter, perda) com base no tipo selecionado, permitindo edição

**Etapa 3 — Classificação e marcação DSCP:**
- O sistema sugere automaticamente o PHB e o valor DSCP para cada aplicação
- O estudante pode aceitar ou alterar a sugestão
- Painel lateral mostra a tabela de PHBs com descrição de cada um

**Etapa 4 — Dimensionamento de banda:**
- Calculadora automática: soma de (bitrate × usuários simultâneos) por aplicação + overhead configurável (padrão 5%)
- Gráfico de pizza mostrando a distribuição de banda por classe
- Campo para inserir a capacidade do enlace disponível e alerta caso a demanda exceda

**Etapa 5 — Projeto de filas:**
- O sistema recomenda o mecanismo de fila por classe — LLQ (*Low Latency Queuing*) para EF (*Expedited Forwarding*), CBWFQ (*Class-Based Weighted Fair Queuing*) para AF (*Assured Forwarding*) e WFQ (*Weighted Fair Queuing*) para BE (*Best Effort*) — com justificativa exibida
- Campos para definir banda garantida e prioridade de cada classe
- Simulação simplificada mostrando o comportamento sob congestionamento com os parâmetros definidos

**Etapa 6 — Revisão e exportação:**
```
┌──────────────────────────────────────────────────────────┐
│  Resumo do Planejamento                                  │
│                                                          │
│  Projeto: Rede Corporativa XYZ                           │
│  Aplicações: 4 classes definidas                         │
│  Banda total necessária: 487 Mbps                        │
│  Enlace disponível: 500 Mbps  ✓ Suficiente               │
│                                                          │
│  ┌─────────────────────────────────────────────────┐     │
│  │ Classe    │ DSCP │ Mecanismo │ Banda garantida  │     │
│  │ VoIP      │ EF   │ LLQ       │ 50 Mbps          │     │
│  │ Vídeo     │ AF41 │ CBWFQ     │ 200 Mbps         │     │
│  │ Dados     │ AF21 │ CBWFQ     │ 200 Mbps         │     │
│  │ Backup    │ BE   │ WFQ       │ restante         │     │
│  └─────────────────────────────────────────────────┘     │
│                                                          │
│              [← Editar]   [⬇ Exportar PDF]               │
└──────────────────────────────────────────────────────────┘
```

---

## Cronograma de 4 Semanas

### Semana 1 — Fundação e Módulo Mapa Conceitual

| Dia | Tarefa |
|---|---|
| 1 | Criação do repositório, configuração Vite + React + TypeScript + Tailwind, estrutura de rotas |
| 2 | Componente de layout (navbar, footer), página Home com cards dos módulos |
| 3 | Integração do React Flow, definição do JSON de nós e arestas do grafo |
| 4 | Renderização do grafo, painel lateral com conteúdo dos nós |
| 5 | Filtros por categoria, zoom/pan, ajuste visual do grafo |
| 6–7 | Revisão da Semana 1, deploy inicial no GitHub Pages |

**Entregável:** Aplicação publicada com Home e Mapa Conceitual funcionais.

---

### Semana 2 — Módulo Simulador

| Dia | Tarefa |
|---|---|
| 1 | Estrutura do módulo Simulador, componente de seleção de cenários, layout base |
| 2 | Cenário 3A (Rede Convergente): lógica de cálculo de MOS via E-model simplificado, gráfico de área empilhada |
| 3 | Cenário 3B (Controle de Congestionamento): simulação de cwnd para Reno, CUBIC e BBR, gráfico de linha comparativo |
| 4 | Cenário 3C (Token Bucket): lógica do balde, gráficos de taxa de entrada/saída e nível do balde |
| 5 | Cenário 3D (DiffServ): simulação de filas PQ/WFQ/LLQ, gráficos de latência e descarte por classe |
| 6 | Cenário 3E (SLA Operadora): tabela de conformidade com indicadores de status |
| 7 | Painel de interpretação textual para todos os cenários, revisão e testes |

**Entregável:** Todos os cinco cenários do Simulador funcionais com feedback em tempo real.

---

### Semana 3 — Módulos Estudos de Caso e Planejamento

| Dia | Tarefa |
|---|---|
| 1 | Estrutura JSON dos estudos de caso, página de listagem com filtros e indicador de progresso |
| 2 | Página de caso individual: navegação por etapas, perguntas com resposta revelável |
| 3 | Conteúdo dos 5 casos (contextualização, análise, solução, lição aprendida) |
| 4 | Módulo Planejamento: estrutura do wizard, Etapas 1 e 2 (identificação e levantamento de aplicações) |
| 5 | Etapas 3 e 4 (DSCP automático e dimensionamento de banda com calculadora) |
| 6 | Etapas 5 e 6 (projeto de filas e tela de revisão) |
| 7 | Persistência via localStorage (progresso dos casos e planejamento em andamento) |

**Entregável:** Estudos de Caso e formulário de Planejamento funcionais com persistência local.

---

### Semana 4 — Exportação PDF, Integração e Publicação Final

| Dia | Tarefa |
|---|---|
| 1 | Implementação da geração de PDF com jsPDF (cabeçalho, tabelas, sumário de decisões) |
| 2 | Testes de geração de PDF em diferentes cenários, ajustes de layout do documento |
| 3 | Integração entre módulos: links do Mapa Conceitual para cenários do Simulador e casos relacionados |
| 4 | Testes de ponta a ponta em Chrome, Firefox e Edge; correção de bugs |
| 5 | Ajustes de responsividade e acessibilidade, revisão de conteúdo técnico |
| 6 | Configuração do GitHub Actions para deploy automático no GitHub Pages |
| 7 | Deploy final, testes no ambiente de produção, documentação de uso no README |

**Entregável:** Aplicação completa publicada, com PDF funcional e todos os módulos integrados.

---

## Estrutura de Arquivos do Projeto

```
qoslab/
├── public/
├── src/
│   ├── assets/
│   ├── components/          # Componentes reutilizáveis (Navbar, Card, Slider, Badge)
│   ├── data/
│   │   ├── nodes.json       # Nós e arestas do mapa conceitual
│   │   └── cases.json       # Conteúdo dos estudos de caso
│   ├── modules/
│   │   ├── map/             # Módulo Mapa Conceitual
│   │   ├── simulator/       # Módulo Simulador (um subdiretório por cenário)
│   │   ├── cases/           # Módulo Estudos de Caso
│   │   └── planner/         # Módulo Planejamento
│   ├── utils/
│   │   ├── qos.ts           # Funções de cálculo (MOS, Token Bucket, cwnd, DSCP)
│   │   └── pdf.ts           # Geração do documento PDF
│   ├── App.tsx
│   └── main.tsx
├── index.html
├── vite.config.ts
└── package.json
```

---

## Critérios de Avaliação do Produto

| Critério | Descrição |
|---|---|
| Cobertura temática | Todos os seis itens da ementa estão representados em ao menos um módulo |
| Corretude técnica | Os cálculos do simulador e do planejador produzem resultados coerentes com a literatura |
| Interatividade | O estudante modifica parâmetros e observa consequências sem intervenção do professor |
| Síntese | O Módulo Planejamento gera um documento PDF completo e tecnicamente estruturado |
| Usabilidade | Navegação entre módulos sem necessidade de instruções externas |
| Disponibilidade | Aplicação acessível via URL pública sem instalação ou cadastro |
