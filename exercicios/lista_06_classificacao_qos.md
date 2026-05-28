# Lista de Exercícios 06 — Classificação das Aplicações Interativas e Níveis de QoS

## Questão 1

A recomendação ITU-T G.1010 — onde ITU-T refere-se ao *International Telecommunication Union — Telecommunication Standardization Sector* (Setor de Padronização da União Internacional de Telecomunicações) — define categorias de aplicações de usuário final com requisitos distintos de QoS (*Quality of Service* — Qualidade de Serviço).

**(a)** Classifique as seguintes aplicações nas categorias definidas pelo ITU-T G.1010 (conversacional, streaming, interativa, em background), justificando cada classificação com base na tolerância a atraso e à perda de pacotes: VoIP (*Voice over IP* — Voz sobre IP), videoconferência, streaming de música, navegação web, transferência de arquivos FTP (*File Transfer Protocol* — Protocolo de Transferência de Arquivos) e jogos online em tempo real.

**(b)** Por que a distinção entre aplicações **elásticas** (que se adaptam à banda disponível) e **inelásticas** (que exigem banda mínima fixa) é fundamental para o projeto de políticas de QoS? Dê dois exemplos de cada tipo e explique como cada um reage à redução de largura de banda disponível.

---

## Questão 2

Os jogos online multiplayer em tempo real impõem requisitos de rede peculiares em comparação com outras aplicações interativas.

**(a)** Descreva os requisitos típicos de latência, jitter (variação de atraso) e perda de pacotes para jogos FPS (*First-Person Shooter* — Tiro em Primeira Pessoa) e jogos RTS (*Real-Time Strategy* — Estratégia em Tempo Real), explicando por que as exigências diferem entre os dois gêneros.

**(b)** Explique o conceito de **tick rate** (taxa de atualização do servidor de jogo, medida em Hz) e sua relação com a largura de banda consumida e a experiência do jogador. Como um tick rate de 128 Hz se compara ao de 64 Hz em termos de requisitos de rede?

---

## Questão 3

O modelo de classes de serviço do DiffServ (*Differentiated Services* — Serviços Diferenciados) define PHBs (*Per-Hop Behaviors* — Comportamentos por Salto) que mapeiam diretamente para categorias de aplicações interativas.

**(a)** Relacione cada PHB com as classes de aplicações interativas mais adequadas, justificando a escolha com base nos requisitos de atraso, jitter e perda de cada comportamento:
- **EF** (*Expedited Forwarding* — Encaminhamento Expresso)
- **AF** (*Assured Forwarding* — Encaminhamento Assegurado, classes AF1x a AF4x)
- **BE** (*Best Effort* — Melhor Esforço)

**(b)** Uma rede corporativa precisa atender simultaneamente a VoIP (*Voice over IP*), videoconferência, ERP (*Enterprise Resource Planning* — Sistema de Gestão Empresarial) via web e backup noturno. Elabore uma tabela de mapeamento DSCP (*Differentiated Services Code Point* — Ponto de Código de Serviços Diferenciados) para cada aplicação e especifique a política de Drop Precedence (precedência de descarte) para cada subclasse AF utilizada, explicando o comportamento esperado de cada classe em situação de congestionamento.

---

## Questão 4

O **SLA** (*Service Level Agreement* — Acordo de Nível de Serviço) formaliza os níveis de QoS (*Quality of Service*) contratados entre um provedor de rede e seus clientes.

**(a)** Defina os parâmetros típicos que compõem um SLA para serviços de voz e vídeo interativo: latência máxima, jitter (variação de atraso) máximo, perda de pacotes máxima e disponibilidade. Indique os valores de referência recomendados pelo ITU-T (*International Telecommunication Union — Telecommunication Standardization Sector*) e pela Cisco para cada parâmetro.

**(b)** Explique como os mecanismos de monitoramento de SLA a seguir permitem verificar continuamente o cumprimento dos parâmetros contratados e acionar alertas em caso de violação:
- **IP SLA** (*Internet Protocol Service Level Agreement* — ferramenta proprietária Cisco de medição ativa de QoS)
- **RFC 2544** (padrão de benchmarking para equipamentos de rede)
- **TWAMP** (*Two-Way Active Measurement Protocol* — Protocolo de Medição Ativa Bidirecional)

---

## Questão 5

Considere uma operadora que oferece três planos de serviço sobre uma infraestrutura IP/MPLS (*Multiprotocol Label Switching* — Comutação por Rótulos Multiprotocolo) compartilhada, com um enlace de backbone de **10 Gbps** operando a **85% de utilização média** no horário de pico:

| Plano      | Perfil de uso                          | Banda contratada | Latência máxima | Jitter máximo | Perda máxima |
|------------|----------------------------------------|------------------|-----------------|---------------|--------------|
| Premium    | VoIP + videoconferência corporativa    | 2 Gbps           | 50 ms           | 10 ms         | 0,1%         |
| Business   | Aplicações web interativas + streaming | 4 Gbps           | 150 ms          | 30 ms         | 0,5%         |
| Standard   | Navegação, e-mail, backup              | 4 Gbps           | 400 ms          | Sem garantia  | 1%           |

**(a)** Projete a arquitetura completa de classes de serviço para esse enlace, detalhando:

- A marcação DSCP (*Differentiated Services Code Point*) atribuída a cada plano e, dentro do plano Premium, a diferenciação entre tráfego de voz (VoIP — *Voice over IP*) e vídeo (videoconferência)
- O mecanismo de escalonamento de filas para cada classe — PQ (*Priority Queuing* — Enfileiramento por Prioridade), WFQ (*Weighted Fair Queuing* — Enfileiramento Justo Ponderado), CBWFQ (*Class-Based Weighted Fair Queuing* — Enfileiramento Justo Ponderado Baseado em Classes) ou LLQ (*Low Latency Queuing* — Enfileiramento de Baixa Latência) — justificando a escolha com base nos requisitos de latência e jitter de cada plano
- A política de policiamento (*policing*) na borda de entrada para garantir que cada cliente respeite a banda contratada, incluindo o comportamento adotado para tráfego excedente (descarte ou remarking — remarcação de DSCP)
- O mecanismo de AQM (*Active Queue Management* — Gerenciamento Ativo de Fila), RED (*Random Early Detection* — Detecção Aleatória Antecipada) ou WRED (*Weighted RED* — RED Ponderado), configurado para as filas Business e Standard, com os parâmetros *min_th* (limiar mínimo), *max_th* (limiar máximo) e *max_p* (probabilidade máxima de descarte) justificados para cada classe

**(b)** Calcule a banda efetivamente disponível para cada plano no pico de utilização (85% de 10 Gbps = 8,5 Gbps) e verifique se as bandas contratadas podem ser garantidas simultaneamente. Caso haja déficit, proponha um mecanismo de compartilhamento do excedente entre as classes sem violar os SLAs (*Service Level Agreements*).

**(c)** Um cliente Premium reporta degradação de qualidade em chamadas VoIP (*Voice over IP*) durante horários de pico, com MOS (*Mean Opinion Score* — Pontuação Média de Opinião) caindo de 4,2 para 2,8. Descreva a metodologia completa de diagnóstico, incluindo:

- Quais métricas coletar (latência, jitter, perda, utilização de fila) e em quais pontos da rede: CPE (*Customer Premises Equipment* — equipamento instalado na premissa do cliente), borda da operadora e nós de backbone
- Quais ferramentas utilizar e o que cada uma permite observar: IP SLA (*Internet Protocol Service Level Agreement*), TWAMP (*Two-Way Active Measurement Protocol*), Wireshark (analisador de protocolos de rede) e SNMP (*Simple Network Management Protocol* — Protocolo Simples de Gerenciamento de Rede) com MIBs (*Management Information Base* — Base de Informações de Gerenciamento) de fila
- As hipóteses de causa mais prováveis — diferenciando falhas na marcação DSCP (*Differentiated Services Code Point*), saturação de fila, policiamento incorreto na borda e problemas na rede do próprio cliente — e como confirmar ou descartar cada uma
- O procedimento de escalonamento caso a causa seja identificada como violação de SLA por parte da própria operadora
