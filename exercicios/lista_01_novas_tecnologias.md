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

**(b)** Quais são as três grandes classes de casos de uso definidas pelo ITU-R (*International Telecommunication Union — Radiocommunication Sector*, Setor de Radiocomunicações da União Internacional de Telecomunicações) para o 5G? Dê um exemplo de aplicação para cada uma:
- **eMBB** (*enhanced Mobile Broadband* — Banda Larga Móvel Aprimorada)
- **URLLC** (*Ultra-Reliable Low Latency Communications* — Comunicações Ultraconfiáveis de Baixa Latência)
- **mMTC** (*massive Machine-Type Communications* — Comunicações Massivas entre Máquinas)

---

## Questão 3

O padrão IEEE (*Institute of Electrical and Electronics Engineers*) 802.11, conhecido como Wi-Fi (*Wireless Fidelity*), passou por diversas revisões ao longo dos anos.

Construa uma tabela comparativa entre os padrões **802.11n (Wi-Fi 4)**, **802.11ac (Wi-Fi 5)**, **802.11ax (Wi-Fi 6/6E)** e **802.11be (Wi-Fi 7)**, considerando as seguintes características:

- Faixas de frequência utilizadas
- Taxa de transferência máxima teórica
- Principais técnicas de acesso ao meio introduzidas
- Melhorias em ambientes com alta densidade de usuários

---

## Questão 4

As Redes Definidas por Software (SDN — *Software-Defined Networking*) e a Virtualização de Funções de Rede (NFV — *Network Functions Virtualization*) são consideradas tecnologias habilitadoras para redes de alta velocidade de nova geração.

**(a)** Explique o papel do plano de controle centralizado no SDN e como ele difere da arquitetura distribuída das redes tradicionais.

**(b)** Descreva como SDN e NFV, atuando em conjunto, permitem a criação de *network slices* (fatias de rede virtualizadas) em redes 5G, possibilitando o atendimento simultâneo de requisitos distintos de QoS (*Quality of Service* — Qualidade de Serviço) para diferentes classes de serviço.

---

## Questão 5

Uma empresa precisa interligar dois data centers distantes 80 km, com requisito de throughput (vazão) agregado de 400 Gbps e tolerância máxima de latência de 1 ms.

**(a)** Elabore uma recomendação técnica de tecnologia de transmissão para esse enlace, comparando fibra óptica monomodo com DWDM (*Dense Wavelength Division Multiplexing* — Multiplexação por Divisão de Comprimento de Onda Densa) frente às alternativas sem fio: microondas e FSO (*Free Space Optics* — Óptica de Espaço Livre). A recomendação deve indicar a tecnologia escolhida e apresentar os critérios técnicos que descartam cada alternativa.

**(b)** Com base na tecnologia recomendada, elabore o dimensionamento do enlace, identificando e quantificando os parâmetros determinantes: atenuação por quilômetro, dispersão cromática, número mínimo de comprimentos de onda DWDM necessários para atingir 400 Gbps e principais condicionantes de custo de implantação.
