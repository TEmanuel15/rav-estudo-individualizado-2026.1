# Lista de Exercícios 01 — Novas Tecnologias de Comunicação em Redes de Alta Velocidade

## Questão 1

A evolução das redes de comunicação passou por diversas gerações, desde as redes de comutação de circuitos até as redes ópticas de alta velocidade.

**(a)** Compare os modelos de comutação de circuitos e comutação de pacotes em termos de alocação de recursos, latência e eficiência de uso do enlace.

### Questão 1 (a) 

Comparação entre os modelos por categoria:

Alocação de Recursos: Em comutação de circuitos, usa-se largura de banda fixa, que assegura uma qualidade de serviço muito boa ao custo de possíveis desperdícios com usuários "AFK" (Away from keyboard). Já em comutação de pacotes, são compartilhados enlaces em vários fluxos diferentes, o que permite acomodar vários usuários com variação no tráfego, que evita parcialmente o problema de desperdícios com usuários AFK.

Latência: Em comutação de circuitos existe um atraso inicial, pra criar o circuito, mas depois disso os atrasos são praticamente constantes (sem grande variação). Em comutação de pacotes, como cada pacote pode seguir por um caminho diferente, se houverem filas/congestionamentos acaba aumentando e causando mais variação nos atrasos.

Eficiência em aplicações modernas: Bom, atualmente a comutação de pacotes é bem mais eficiente em termos de uso em aplicações modernas, principalmente por dois motivos: 1- Os usuários não transmitem continuamente; 2- A multiplexação (acho que escrevi certo KK) estatística aumenta o aproveitamento da rede, reduzindo desperdícios.

**(b)** Explique como o surgimento da fibra óptica e das tecnologias DWDM (*Dense Wavelength Division Multiplexing* — Multiplexação por Divisão de Comprimento de Onda Densa) impactou a capacidade das redes de longa distância.

### Questão 1 (b)

Impacto da Fibra Óptica nas Redes de Longa Distância: Basicamente uma revolução nas telecomunicações pela capacidade muito superior aos cabos de cobre, suportando transmissões de até centenas de terabytes por segundo, além de não sofrer interferência eletromagnética. tirando o fato de que o sinal pode percorrer centenas de kilômetros antes de precisar de amplificação/regeneração (Conceitos que eu entendo vagamente apesar dos nomes serem bem sugestivos).

Impacto do DWDM nas Redes de Longa Distância: Aumento massivo na capacidade de transmissão, visto que uma única fibra pode transportar vários canais por diferentes comprimentos de onda, de modo que normalmente não é necessário adicionar novas fibras pra aumentar a capacidade, basta adicionar novos comprimentos de onda.

---

## Questão 2

As redes sem fio evoluíram significativamente com as gerações 4G LTE (*Long-Term Evolution* — Evolução de Longo Prazo) e 5G NR (*New Radio* — Nova Rádio).

**(a)** Descreva as principais diferenças arquiteturais entre o LTE e o 5G NR, destacando os avanços em largura de banda, latência e suporte a densidade de dispositivos.

### Questão 2 (a)

Diferenças Arquiteturais LTE Vs. 5G NR: A primeira diferença geral entre LTE e 5G NR, é que a LTE foi projetado com intuito de ser usado para banda larga móvel em específico, enquanto a 5G NR também busca atender aplicações até mesmo industriais, além de dispositivos IoT.

Largura de Banda: LTE chega a até 20 MHz, a 5G NR pode variar, até 100 MHz (Em faixas abaixo de 6 GHz) e 400 MHz (Em faixas entre 24~100 GHz, de ondas milimétricas (mmWavE) )

Latência: LTE possui uma latência variável entre 20 e 50 MS, enquanto a 5G NR foi projetada pra ser entre 10 e 50 vezes mais rápida, chegando a 1~5 MS sob as condições certas.

Densidade de Dispositivos: Na LTE a capacidade por kilômetro quadrado é de cem mil dispositivos, enquanto a 5G NR chega a até um milhão de dispositivos por kilômetro quadrado.

**(b)** Quais são as três grandes classes de casos de uso definidas pelo ITU-R (*International Telecommunication Union — Radiocommunication Sector*, Setor de Radiocomunicações da União Internacional de Telecomunicações) para o 5G? Dê um exemplo de aplicação para cada uma:
- **eMBB** (*enhanced Mobile Broadband* — Banda Larga Móvel Aprimorada)
- **URLLC** (*Ultra-Reliable Low Latency Communications* — Comunicações Ultraconfiáveis de Baixa Latência)
- **mMTC** (*massive Machine-Type Communications* — Comunicações Massivas entre Máquinas)

### Questão 2 (b)

Descrição e Exemplos das categorias definidas pelo ITU-R:

eMBB - Enhanced Mobile Broadband: Tem como objetivo a conexão de alta velocidade para usuários mobile, como por exemplo: Streaming de altíssima resolução (UHD), downloads de arquivos grandes, jogos em nuvem.

URLCC - Ultra-Reliable Low-Latency Communications: Tem como objetivo garantir comunicações de latência baixíssima e de alto nível de confiabilidade, como por exemplo: comunicação de sistemas anti-colisão entre veículos, cirurgias remotas, telemedicina.

mMTC - massive Machine-Type Communications: Tem como objetivo conectar múltiplos dispositivos de baixo consumo, tem várias técnicas de uso, mas a mais conhecida é em sensores para realizar monitoramentos precisos de condições, onde é necessário um grande número de sensores para um alto nível de precisão.

---

## Questão 3

O padrão IEEE (*Institute of Electrical and Electronics Engineers*) 802.11, conhecido como Wi-Fi (*Wireless Fidelity*), passou por diversas revisões ao longo dos anos.

Construa uma tabela comparativa entre os padrões **802.11n (Wi-Fi 4)**, **802.11ac (Wi-Fi 5)**, **802.11ax (Wi-Fi 6/6E)** e **802.11be (Wi-Fi 7)**, considerando as seguintes características:

- Faixas de frequência utilizadas
- Taxa de transferência máxima teórica
- Principais técnicas de acesso ao meio introduzidas
- Melhorias em ambientes com alta densidade de usuários

### Questão 3

Comparativo entre os padrões:

802.11n (Wi-Fi 4):
- Faixas de Frequência: 2.4 GHz e 5 GHz
- Taxa Máxima Teórica: 600 mbps
- Técnicas de Acesso ao Meio: CSMA/CA, OFDM, MIMO
- Melhorias em Alta Densidade: Aumento da Taxa usando MIMO

802.11ac (Wi-Fi 5):
- Faixas de Frequência: 5 GHz
- Taxa Máxima Teórica: 6.9 gbps
- Técnicas de Acesso ao Meio: CSMA/CA, OFDM, MU-MIMO (downlink)
- Melhorias em Alta Densidade: Implementação de MU-MIMO e canais com maior largura

802.11ax (Wi-Fi 6/6E):
- Faixas de Frequência: 2.4 GHz, 5 GHz, 6 GHz (6E)
- Taxa Máxima Teórica: 9.6 gbps
- Técnicas de Acesso ao Meio: OFDMA, MU-MIMO (uplink e downlink), BSS Coloring, TWT (Target wake time)
- Melhorias em Alta Densidade: OFDMA (Permite dividir canais em unidades menores), BSS Coloring (Reduz interferência) e MU-MIMO up e down

802.11be (Wi-Fi 7):
- Faixas de Frequência: 2.4 GHz, 5 GHz, 6 GHz
- Taxa Máxima Teórica: 46 gbps
- Técnicas de Acesso ao Meio: OFDMA Aprimorado, MU-MIMO Expandido, MLO (Multi-link operator)
- Melhorias em Alta Densidade: Maior número de Fluxos Espaciais, OFDMA melhorado, MLO (Permite que um mesmo dispositivo use múltiplas bandas e canais).

---

## Questão 4

As Redes Definidas por Software (SDN — *Software-Defined Networking*) e a Virtualização de Funções de Rede (NFV — *Network Functions Virtualization*) são consideradas tecnologias habilitadoras para redes de alta velocidade de nova geração.

**(a)** Explique o papel do plano de controle centralizado no SDN e como ele difere da arquitetura distribuída das redes tradicionais.

### Questão 4 (a)

A maior diferença entre o SDN e a arquitetura distribuída é na forma que cada uma administra o controle e gerenciamento de tráfego. Na arquitetura distribuída, temos que cada roteador/switch possui Data Plane (Para encaminhar pacotes) e Control Plane (Para gerenciar decisões de roteamento), enquanto no SDN existe uma separação entre Data Plane e Control Plane, as decisões de roteamento pertencem a um controlador central que enxerga a rede globalmente e gerencia seus recursos, enquanto os switches apenas executam as regras do controlador central e encaminham os pacotes conforme as instruções. O SDN possui uma maior afinidade com automações e implementações de políticas, visto que não é necessário atualizar configurações aparelho por aparelho individualmente.

**(b)** Descreva como SDN e NFV, atuando em conjunto, permitem a criação de *network slices* (fatias de rede virtualizadas) em redes 5G, possibilitando o atendimento simultâneo de requisitos distintos de QoS (*Quality of Service* — Qualidade de Serviço) para diferentes classes de serviço.

### Questão 4 (b)

O principal uso de SDN na criação de network slices é para poder direcionar diferentes serviços por diferentes caminhos, de acordo com a necessidade do serviço, por exemplo, se tratando de um serviço de streaming não é muito relevante se teremos uma alta eficiência energética, porém, o controle da largura de banda é fundamental pra esse serviço, e o SDN realiza esse direcionamento de função. Além de permitir ao controlador priorizar determinados fluxos (Servindo como uma garantia de QoS), bem como pode reservar largura de banda, e reconfigurar rotas de forma dinâmica. Já o NFV serve para virtualizar funções que normalmente seriam implementadas em um hardware dedicado (Firewall, NAT, Gateway, etc.). A combinação do SDN e do NFV permitem a criação de múltiplas redes virtuais (Slices) especializadas em uma mesma infraestrutura física, mesmo que elas possuam requisitos muito diferentes.

---

## Questão 5

Uma empresa precisa interligar dois data centers distantes 80 km, com requisito de throughput (vazão) agregado de 400 Gbps e tolerância máxima de latência de 1 ms.

**(a)** Elabore uma recomendação técnica de tecnologia de transmissão para esse enlace, comparando fibra óptica monomodo com DWDM (*Dense Wavelength Division Multiplexing* — Multiplexação por Divisão de Comprimento de Onda Densa) frente às alternativas sem fio: microondas e FSO (*Free Space Optics* — Óptica de Espaço Livre). A recomendação deve indicar a tecnologia escolhida e apresentar os critérios técnicos que descartam cada alternativa.

### Questão 5 (a)

A minha recomendação técnica para este enlace é o de Fibra Óptica Monomodo com DWDM, a recomendação é essa por vários motivos e entre eles, a distância entre os data centers, a vazão agregada de 400gbps e latência máxima de 1ms. Todos esses requisitos pedem por essa tecnologia de transmissão. Microondas possuem capacidade insuficiente, normalmente transmitindo apenas alguns gbps, no máximo algumas dezenas de gbps, além disso, a 80km seria necessaria uma torre intermediária (além das duas principais) por conta da curvatura da terra. Já a tecnologia FSO simplesmente não tem capacidade de atender à demanda por uma questão de distância entre os data centers visto que FSO's só podem ser implementados em distâncias curtas (No máximo alguns poucos kilômetros), é sim teoricamente possível fazer um enlace de 80km, porém o sistema perderia toda a confiabilidade e não seria nada prático.

**(b)** Com base na tecnologia recomendada, elabore o dimensionamento do enlace, identificando e quantificando os parâmetros determinantes: atenuação por quilômetro, dispersão cromática, número mínimo de comprimentos de onda DWDM necessários para atingir 400 Gbps e principais condicionantes de custo de implantação.

### Questão 5 (b)

Atenuação por Quilômetro: 0,20 a 0,25 dB por kilômetro.
Dispersão Cromática: Aproximadamente 1360 ps/nm de dispersão cromática acumulada, dispersão relevante já em taxas de 100gbps, usar DSP nos transceptores coerentes pode resolver.
Número mínimo de comprimetos de onda DWDM: 4 comprimentos de onda de 100gb por lambda (mais convencional), ou 2 comprimentos de onda de 200 gb por lambda, ou em uma situação de altíssimo nível, 1 comprimento de onda de 400gb por lambda.
