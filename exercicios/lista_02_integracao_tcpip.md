# Lista de Exercícios 02 — Integração de Serviços em Ambiente TCP/IP

## Questão 1

A arquitetura TCP/IP (*Transmission Control Protocol/Internet Protocol*) foi originalmente projetada para oferecer um serviço de melhor esforço (*best-effort*), sem garantias de entrega, ordem ou temporização.

**(a)** Explique por que o modelo *best-effort* é insuficiente para suportar aplicações de voz e vídeo em tempo real em uma rede convergente.

**(b)** Descreva os dois modelos propostos pela IETF (*Internet Engineering Task Force* — Força-Tarefa de Engenharia da Internet) para adicionar suporte a qualidade de serviço sobre IP (*Internet Protocol*): **IntServ** (*Integrated Services* — Serviços Integrados) e **DiffServ** (*Differentiated Services* — Serviços Diferenciados), destacando suas diferenças em escalabilidade e granularidade de controle.

---

## Questão 2

O protocolo RSVP (*Resource Reservation Protocol* — Protocolo de Reserva de Recursos) é o mecanismo de sinalização associado ao modelo IntServ (*Integrated Services*).

**(a)** Descreva o funcionamento do RSVP, explicando o papel das mensagens `PATH` (caminho) e `RESV` (reserva) no estabelecimento de uma reserva de recursos fim a fim.

**(b)** Por que o RSVP enfrenta problemas de escalabilidade em redes de backbone? Como o modelo DiffServ (*Differentiated Services*) contorna essa limitação?

---

## Questão 3

Em uma rede corporativa convergente, VoIP (*Voice over IP* — Voz sobre IP), videoconferência e dados de escritório trafegam sobre a mesma infraestrutura IP (*Internet Protocol*).

**(a)** Explique como o campo DSCP (*Differentiated Services Code Point* — Ponto de Código de Serviços Diferenciados) no cabeçalho IP é utilizado para classificar e marcar os pacotes nesse cenário, citando os valores PHB (*Per-Hop Behavior* — Comportamento por Salto) recomendados para cada classe de tráfego: EF (*Expedited Forwarding* — Encaminhamento Expresso), AF (*Assured Forwarding* — Encaminhamento Assegurado) e BE (*Best Effort* — Melhor Esforço).

**(b)** Descreva o papel dos mecanismos de **policiamento** (*policing*) e **conformação** (*shaping*) de tráfego na borda da rede, explicando a diferença entre os dois.

---

## Questão 4

O protocolo SIP (*Session Initiation Protocol* — Protocolo de Iniciação de Sessão) é amplamente utilizado para sinalização de sessões multimídia sobre IP (*Internet Protocol*).

**(a)** Descreva a sequência de mensagens SIP envolvida no estabelecimento e encerramento de uma chamada VoIP (*Voice over IP*) entre dois *user agents* (agentes de usuário), incluindo os papéis de *proxy* (intermediário de sinalização) e servidor de registro.

**(b)** Como o SDP (*Session Description Protocol* — Protocolo de Descrição de Sessão) complementa o SIP na negociação dos parâmetros de mídia — codecs, endereço IP e porta RTP (*Real-time Transport Protocol* — Protocolo de Transporte em Tempo Real) — de uma sessão?

---

## Questão 5

Considere uma rede empresarial que integra serviços de voz, vídeo sob demanda e acesso à internet sobre um único enlace WAN (*Wide Area Network* — Rede de Longa Distância) de 100 Mbps.

A distribuição de tráfego esperada é:
- VoIP (*Voice over IP*): 20 chamadas simultâneas de 64 kbps cada
- Videoconferência HD (*High Definition* — Alta Definição): 5 sessões de 4 Mbps cada
- Dados: tráfego restante

**(a)** Calcule a largura de banda reservada para voz e para vídeo, apresentando os valores intermediários por classe, e determine a banda remanescente disponível para dados.

**(b)** Elabore o projeto da política de filas LLQ (*Low Latency Queuing* — Enfileiramento de Baixa Latência) + CBWFQ (*Class-Based Weighted Fair Queuing* — Enfileiramento Justo Ponderado Baseado em Classes) para esse enlace, especificando para cada classe: o mecanismo de escalonamento utilizado, a banda garantida ou peso relativo atribuído e a justificativa técnica com base nos requisitos de latência e sensibilidade a jitter (variação de atraso) de cada tipo de tráfego.
