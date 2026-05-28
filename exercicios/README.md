# Índice de Listas de Exercícios — Redes de Alta Velocidade

## [Lista 01 — Novas Tecnologias de Comunicação em Redes de Alta Velocidade](lista_01_novas_tecnologias.md)

| # | Tema |
|---|------|
| Q1 | Evolução das redes: comutação de circuitos vs. pacotes; impacto da fibra óptica e DWDM |
| Q2 | Redes móveis: diferenças arquiteturais LTE vs. 5G NR; casos de uso eMBB, URLLC e mMTC |
| Q3 | Evolução do Wi-Fi: tabela comparativa Wi-Fi 4 / Wi-Fi 5 / Wi-Fi 6/6E / Wi-Fi 7 (802.11be) |
| Q4 | Dimensionamento de enlace: fibra óptica monomodo com DWDM vs. microondas e FSO |
| Q5 | SDN e NFV: plano de controle centralizado e network slicing em redes 5G |

---

## [Lista 02 — Integração de Serviços em Ambiente TCP/IP](lista_02_integracao_tcpip.md)

| # | Tema |
|---|------|
| Q1 | Modelo best-effort vs. IntServ e DiffServ: escalabilidade e granularidade de controle |
| Q2 | RSVP: mensagens PATH e RESV; problema de escalabilidade no backbone |
| Q3 | DSCP e PHBs (EF, AF, BE): marcação de tráfego convergente; policiamento vs. conformação |
| Q4 | SIP e SDP: sinalização de sessão VoIP e negociação de parâmetros de mídia |
| Q5 | Dimensionamento de rede convergente: cálculo de banda e projeto de filas LLQ + CBWFQ |

---

## [Lista 03 — LANs de Alta Velocidade](lista_03_lans_alta_velocidade.md)

| # | Tema |
|---|------|
| Q1 | Evolução da Ethernet: 10BASE-T ao 400GbE; obsolescência do CSMA/CD |
| Q2 | Fast Ethernet: padrões 100BASE-TX/FX/T4; mecanismo de autonegociação |
| Q3 | Gigabit Ethernet: slot time, carrier extension, packet bursting e full-duplex |
| Q4 | 10 Gigabit Ethernet: padrões ópticos SR/LR/ER; transição para backbone e data center |
| Q5 | Projeto de data center: dimensionamento de acesso e uplinks com restrição de sobresubscrição |

---

## [Lista 04 — Requisitos de QoS em Aplicações Multimídia Interativas](lista_04_qos_multimidia.md)

| # | Tema |
|---|------|
| Q1 | Parâmetros de QoS: latência, jitter, perda e largura de banda por classe de aplicação; playout buffer |
| Q2 | MOS e E-model (ITU-T G.107): avaliação subjetiva e objetiva de qualidade em VoIP; fator R |
| Q3 | RTP e RTCP: cabeçalho RTP (sequence number, timestamp, SSRC); monitoramento com SR/RR |
| Q4 | Codecs de vídeo: H.264 vs. H.265; avaliação de parâmetros de rede contra ITU-T G.1010 |
| Q5 | Projeto de telepresença 4K: dimensionamento de banda com overhead e análise de latência SP × NYC |

---

## [Lista 05 — Mecanismos de Controle de Congestionamento e Tráfego](lista_05_controle_congestionamento.md)

| # | Tema |
|---|------|
| Q1 | Controle de congestionamento TCP: Slow Start, Congestion Avoidance, Fast Recovery; Reno vs. CUBIC |
| Q2 | AQM e ECN: algoritmo RED (min_th, max_th, max_p); sinalização de congestionamento sem perda |
| Q3 | Token Bucket vs. Leaky Bucket: comparação e dimensionamento para tráfego de vídeo em rajada |
| Q4 | BBR: estimativa de BtlBw e RTprop; vantagens sobre CUBIC e questões de fairness |
| Q5 | QUIC: multiplexação, TLS 1.3, migração de conexão, 0-RTT; relação com BBR e desafios com middleboxes |
| Q6 | Projeto de filas: PQ + WFQ com cálculo de pesos e análise sob congestionamento |

---

## [Lista 06 — Classificação das Aplicações Interativas e Níveis de QoS](lista_06_classificacao_qos.md)

| # | Tema |
|---|------|
| Q1 | Categorias ITU-T G.1010: conversacional, streaming, interativa, background; elásticas vs. inelásticas |
| Q2 | Jogos online: requisitos FPS vs. RTS; tick rate e impacto na largura de banda |
| Q3 | PHBs e DiffServ: mapeamento EF/AF/BE para aplicações; projeto de DSCP e drop precedence |
| Q4 | SLA: parâmetros de contrato para voz/vídeo; monitoramento com IP SLA, RFC 2544 e TWAMP |
| Q5 | Arquitetura de QoS em operadora IP/MPLS: projeto de classes, cálculo de banda no pico e diagnóstico de violação de SLA em VoIP |
