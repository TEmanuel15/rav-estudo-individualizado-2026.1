# Lista de Exercícios 03 — LANs de Alta Velocidade

## Questão 1

A Ethernet evoluiu de 10 Mbps até as versões de 400 Gbps e 800 Gbps atualmente disponíveis.

**(a)** Trace a linha evolutiva da Ethernet desde o padrão original (10BASE-T, onde T indica par trançado — *twisted pair*) até o 400GbE (400 Gigabit Ethernet), destacando as principais mudanças no meio físico, no método de acesso ao meio e na topologia de rede a cada salto de geração.

**(b)** Por que o CSMA/CD (*Carrier Sense Multiple Access with Collision Detection* — Acesso Múltiplo por Detecção de Portadora com Detecção de Colisão) tornou-se obsoleto nas redes Ethernet modernas? Qual característica da infraestrutura atual eliminou a necessidade desse mecanismo?

---

## Questão 2

O padrão **Fast Ethernet (IEEE 802.3u)** — onde IEEE significa *Institute of Electrical and Electronics Engineers* — introduziu operação a 100 Mbps mantendo compatibilidade com o cabeamento existente.

**(a)** Compare os padrões físicos **100BASE-TX** (par trançado, 2 pares), **100BASE-FX** (fibra óptica) e **100BASE-T4** (par trançado, 4 pares), indicando o tipo de meio, o número de pares utilizados e a distância máxima de segmento de cada um.

**(b)** Explique o mecanismo de **autonegociação** (IEEE 802.3u Cláusula 28) e sua importância para a coexistência de equipamentos de diferentes velocidades em uma mesma infraestrutura.

---

## Questão 3

O **Gigabit Ethernet (IEEE 802.3z / 802.3ab)** trouxe desafios específicos para manter a compatibilidade com o modelo CSMA/CD (*Carrier Sense Multiple Access with Collision Detection*) em topologias half-duplex (transmissão em apenas um sentido por vez).

**(a)** Explique o problema do **slot time** (tempo mínimo de slot de transmissão) no Gigabit Ethernet half-duplex e como as técnicas de *carrier extension* (extensão de portadora) e *packet bursting* (transmissão em rajada de pacotes) foram adotadas para contorná-lo.

**(b)** Na prática, o Gigabit Ethernet é implantado exclusivamente em modo full-duplex (transmissão simultânea nos dois sentidos) com switches. Por que essa escolha elimina os problemas citados no item anterior?

---

## Questão 4

O **10 Gigabit Ethernet (IEEE 802.3ae)** marcou a transição da Ethernet do ambiente LAN (*Local Area Network* — Rede Local) para o backbone metropolitano e de data center.

**(a)** Descreva as diferenças entre os padrões físicos **10GBASE-SR** (SR — *Short Range*, curto alcance), **10GBASE-LR** (LR — *Long Range*, longo alcance) e **10GBASE-ER** (ER — *Extended Range*, alcance estendido), indicando o tipo de fibra, o comprimento de onda e o alcance de cada um.

**(b)** O 10GbE (10 Gigabit Ethernet) não define operação half-duplex nem suporta CSMA/CD (*Carrier Sense Multiple Access with Collision Detection*). Quais implicações essa decisão tem sobre o modelo de comutação e o projeto da infraestrutura de rede?

---

## Questão 5

Um data center precisa interligar 48 servidores de alto desempenho a um switch de agregação, com os seguintes requisitos:

- Largura de banda de **10 Gbps por servidor** no acesso
- Uplinks (enlaces de subida) do switch de acesso para o switch de agregação com **sobresubscrição máxima de 4:1**
- Distância máxima entre servidor e switch: 30 metros

**(a)** Elabore a especificação técnica dos enlaces de acesso (servidor → switch) e dos uplinks (switch de acesso → switch de agregação), indicando para cada um: o padrão Ethernet adotado, o meio físico utilizado e a justificativa com base nos requisitos de velocidade e distância.

**(b)** Calcule a largura de banda total necessária nos uplinks para respeitar a sobresubscrição máxima de 4:1 e determine a solução adotada: número de uplinks e padrão (40 GbE ou 100 GbE). Apresente os cálculos intermediários.
