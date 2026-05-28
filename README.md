# Redes de Alta Velocidade

Repositório de material produzido para a disciplina **Redes de Alta Velocidade**, composto por listas de exercícios e pela especificação de um produto educacional online centrado em Qualidade de Serviço (QoS).

## Ementa

1. Novas tecnologias de comunicação em redes de alta velocidade
2. Integração de serviços em ambiente TCP/IP (*Transmission Control Protocol/Internet Protocol*)
3. LANs (*Local Area Networks* — Redes Locais) de alta velocidade (Gigabit Ethernet, Fast Ethernet, entre outras)
4. Requisitos de QoS em aplicações multimídia interativas
5. Mecanismos de controle de congestionamento e tráfego
6. Classificação das aplicações interativas e diferentes níveis de QoS

## Atividades de Estudo

### Listas de Exercícios

Para cada item da ementa foi elaborada uma lista de questões dissertativas e de aplicação, totalizando 31 questões distribuídas em 6 listas. As questões transitam entre conceitos teóricos, comparações entre protocolos e mecanismos, e exercícios de dimensionamento e projeto de redes.

| Lista | Tema | Questões |
|---|---|---|
| [Lista 01](exercicios/lista_01_novas_tecnologias.md) | Novas Tecnologias de Comunicação | 5 |
| [Lista 02](exercicios/lista_02_integracao_tcpip.md) | Integração de Serviços em Ambiente TCP/IP | 5 |
| [Lista 03](exercicios/lista_03_lans_alta_velocidade.md) | LANs de Alta Velocidade | 5 |
| [Lista 04](exercicios/lista_04_qos_multimidia.md) | Requisitos de QoS em Aplicações Multimídia | 5 |
| [Lista 05](exercicios/lista_05_controle_congestionamento.md) | Controle de Congestionamento e Tráfego | 6 |
| [Lista 06](exercicios/lista_06_classificacao_qos.md) | Classificação de Aplicações e Níveis de QoS | 5 |

O índice completo com o tema de cada questão está em [exercicios/README.md](exercicios/README.md).

### Produto Educacional — QoSLab

O **QoSLab** é uma plataforma web interativa desenvolvida como síntese prática dos conteúdos da disciplina. Seu objetivo é permitir que o estudante analise o comportamento de redes sob diferentes políticas de QoS e produza planejamentos técnicos fundamentados, indo além da resolução de exercícios isolados.

A plataforma é composta por quatro módulos:

| Módulo | Descrição |
|---|---|
| Mapa Conceitual | Grafo navegável que relaciona protocolos, mecanismos, parâmetros e classes de aplicação da ementa |
| Simulador de QoS (*Quality of Service*) | Cinco cenários configuráveis com feedback visual em tempo real (rede convergente, algoritmos TCP — *Transmission Control Protocol*, Token Bucket, DiffServ — *Differentiated Services* e SLA — *Service Level Agreement* — em operadora) |
| Estudos de Caso | Cinco casos contextualizados com análise guiada, perguntas intermediárias e solução comentada |
| Assistente de Planejamento | Formulário em seis etapas que conduz o estudante do levantamento de requisitos à geração de um documento de projeto em PDF (*Portable Document Format*) |

A especificação completa — requisitos, descrição de páginas e cronograma de 4 semanas — está em [produto_educacional/README.md](produto_educacional/README.md).

## Bibliografia

### Básica

- KUROSE, J. F.; ROSS, K. W. *Redes de Computadores e a Internet: Uma Abordagem Top-down*. 3. ed. São Paulo: Pearson Addison Wesley, 2007. 634 p. ISBN 85-88639-18-1.
- TANENBAUM, A. S. *Redes de Computadores*. 4. ed. Rio de Janeiro: Campus, 2003. 945 p. ISBN 85-352-1185-3.
- COMER, D. E. *Redes de Computadores e Internet*. 2. ed. Porto Alegre: Bookman, 2001. 522 p. ISBN 85-7307-778-6.

### Complementar

- SOARES, L. F. G.; LEMOS, G.; COLCHER, S. *Redes de Computadores: das LANs, MANs e WANs às redes ATM*. 2. ed. Rio de Janeiro: Campus, 1995. 705 p. ISBN 85-7001-954-8.
- HUNT, C. *TCP/IP Network Administration*. 3. ed. Sebastopol: O'Reilly, 2002. 725 p. ISBN 978-0-596-00297-8.
- STALLINGS, W. *Redes e Sistemas de Comunicação de Dados: Teoria e Aplicações Corporativas*. 5. ed. Rio de Janeiro: Campus, 2005. 449 p. ISBN 85-352-1731-2.
- PAULA FILHO, W. P. *Multimídia: Conceitos e Aplicações*. Rio de Janeiro: LTC, 2009. 321 p. ISBN 85-216-1222-2.
- FOROUZAN, B. A. *Comunicação de Dados e Redes de Computadores*. 4. ed. São Paulo: McGraw Hill, 2008. 1134 p. ISBN 9788586804885.
