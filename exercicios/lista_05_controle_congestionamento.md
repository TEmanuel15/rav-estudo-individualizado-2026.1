# Lista de Exercícios 05 — Mecanismos de Controle de Congestionamento e Tráfego

## Questão 1

O controle de congestionamento no TCP (*Transmission Control Protocol* — Protocolo de Controle de Transmissão) é realizado por meio de um conjunto de algoritmos que ajustam dinamicamente a taxa de envio em resposta a sinais da rede.

**(a)** Descreva as fases **Slow Start** (início lento), **Congestion Avoidance** (prevenção de congestionamento) e **Fast Recovery** (recuperação rápida) do TCP, explicando como a *cwnd* (*congestion window* — janela de congestionamento) evolui em cada fase e quais eventos provocam as transições entre elas.

**(b)** Compare os algoritmos **TCP Reno** e **TCP CUBIC** em termos de comportamento da janela de congestionamento após uma perda de pacote. Por que o CUBIC é mais adequado para redes de alta velocidade com grande BDP (*Bandwidth-Delay Product* — Produto Banda-Atraso)?

---

## Questão 2

Os mecanismos de descarte ativo de pacotes, conhecidos como AQM (*Active Queue Management* — Gerenciamento Ativo de Fila), foram desenvolvidos para sinalizar congestionamento antes que as filas transbordem.

**(a)** Explique o funcionamento do algoritmo **RED** (*Random Early Detection* — Detecção Aleatória Antecipada), descrevendo os parâmetros *min_th* (limiar mínimo de fila), *max_th* (limiar máximo de fila) e *max_p* (probabilidade máxima de descarte), e como eles determinam a probabilidade de descarte de um pacote em função do tamanho médio da fila.

**(b)** O **ECN** (*Explicit Congestion Notification* — Notificação Explícita de Congestionamento) permite sinalizar congestionamento sem descartar pacotes. Descreva como os bits ECN no cabeçalho IP (*Internet Protocol*) e no cabeçalho TCP interagem para comunicar o congestionamento do roteador ao transmissor sem perda de dados.

---

## Questão 3

O *Token Bucket* (balde de tokens) e o *Leaky Bucket* (balde com vazamento) são os dois algoritmos clássicos de conformação de tráfego (*traffic shaping* — modelagem do perfil de envio).

**(a)** Descreva o funcionamento de cada algoritmo e compare-os em termos de capacidade de absorver rajadas (*bursts*) de tráfego e de garantia de taxa de saída.

**(b)** Um fluxo de vídeo gera rajadas de até 8 Mbps por 200 ms, seguidas de períodos de 600 ms a 1 Mbps. Dimensione um *Token Bucket* (taxa de token *r* e tamanho do balde *b*) que permita transmitir essas rajadas sem descarte, garantindo uma taxa média de conformidade de 2 Mbps. Mostre os cálculos.

---

## Questão 4

O BBR (*Bottleneck Bandwidth and Round-trip propagation time* — Largura de Banda do Gargalo e Tempo de Propagação de Ida e Volta), desenvolvido pelo Google, representa uma abordagem alternativa ao controle de congestionamento baseado em perda de pacotes.

**(a)** Explique como o BBR estima a *BtlBw* (*Bottleneck Bandwidth* — largura de banda do gargalo) e o *RTprop* (*Round-trip propagation time* — tempo mínimo de propagação de ida e volta), e como esses dois parâmetros determinam a taxa de envio e o tamanho da janela de voo (*inflight* — pacotes em trânsito sem confirmação).

**(b)** Em que cenários o BBR apresenta vantagens significativas sobre o TCP CUBIC? Quais críticas ou problemas de equidade (*fairness*) foram identificados quando fluxos BBR competem com fluxos CUBIC em um mesmo gargalo?

---

## Questão 5

O protocolo **QUIC** (RFC 9000 — *Request for Comments* 9000, documento de padronização do IETF), desenvolvido pelo Google e padronizado pelo IETF (*Internet Engineering Task Force*), reimplementa funcionalidades de transporte confiável sobre UDP (*User Datagram Protocol* — Protocolo de Datagrama de Usuário), incorporando controle de congestionamento nativo.

**(a)** Descreva as principais características do QUIC que o diferenciam do TCP (*Transmission Control Protocol*):
- Multiplexação de streams sem bloqueio de cabeça de fila (*HoL blocking* — *Head-of-Line blocking*, em que um pacote perdido bloqueia todos os demais na fila)
- Integração nativa com TLS 1.3 (*Transport Layer Security* — Segurança da Camada de Transporte)
- Migração de conexão (manutenção da sessão ao trocar de rede)
- Redução de latência no estabelecimento: *0-RTT* (zero viagens de ida e volta para reconexões) e *1-RTT handshake* (uma única viagem de ida e volta para novas conexões)

Por que essas características são especialmente relevantes para aplicações multimídia interativas?

**(b)** O QUIC utiliza BBR (*Bottleneck Bandwidth and Round-trip propagation time*) como algoritmo de controle de congestionamento padrão em muitas implementações, incluindo o HTTP/3 (*HyperText Transfer Protocol* versão 3). Explique como a arquitetura do QUIC — rodando no espaço do usuário (*userspace*) em vez do kernel do sistema operacional — facilita a atualização e experimentação de algoritmos de controle de congestionamento em comparação com o TCP. Quais desafios isso impõe para a interoperabilidade em redes com middleboxes como firewalls, NATs (*Network Address Translators* — Tradutores de Endereços de Rede) e proxies?

---

## Questão 6

Um roteador de borda possui um enlace de saída de 1 Gbps compartilhado entre três classes de tráfego com os seguintes requisitos:

| Classe   | Tipo de tráfego            | Banda garantida | Prioridade |
|----------|----------------------------|-----------------|------------|
| Classe A | VoIP (*Voice over IP*)     | 50 Mbps         | Alta       |
| Classe B | Videoconferência           | 300 Mbps        | Média      |
| Classe C | Dados corporativos         | 650 Mbps        | Baixa      |

**(a)** Elabore o projeto da política de gerenciamento de filas, especificando: o mecanismo adotado para a Classe A com PQ (*Priority Queuing* — Enfileiramento por Prioridade) e para as Classes B e C com WFQ (*Weighted Fair Queuing* — Enfileiramento Justo Ponderado), os pesos relativos calculados para B e C de modo que as bandas garantidas sejam respeitadas, e a justificativa técnica de cada decisão. Apresente os cálculos dos pesos.

**(b)** Analise o comportamento da política projetada em um cenário de congestionamento em que a demanda total atinge 1,2 Gbps (A: 60 Mbps, B: 400 Mbps, C: 740 Mbps). Determine a banda efetivamente entregue a cada classe e verifique se os requisitos de banda garantida são respeitados.
