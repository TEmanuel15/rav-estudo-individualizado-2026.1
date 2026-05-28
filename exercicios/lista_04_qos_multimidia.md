# Lista de Exercícios 04 — Requisitos de QoS em Aplicações Multimídia Interativas

## Questão 1

As aplicações multimídia interativas possuem requisitos de rede distintos das aplicações tradicionais de transferência de dados.

**(a)** Defina e diferencie os seguintes parâmetros de QoS (*Quality of Service* — Qualidade de Serviço): **largura de banda**, **latência fim a fim**, **jitter** (variação de atraso) e **taxa de perda de pacotes**. Para cada um, indique qual classe de aplicação — VoIP (*Voice over IP* — Voz sobre IP), videoconferência ou streaming de vídeo — é mais sensível a variações nesse parâmetro.

**(b)** Por que aplicações de voz interativa toleram mais perda de pacotes do que variação de atraso? Explique o impacto do jitter na qualidade percebida pelo usuário e como o *playout buffer* (buffer de reprodução adaptativa) é utilizado para mitigá-lo.

---

## Questão 2

O MOS (*Mean Opinion Score* — Pontuação Média de Opinião) é uma métrica subjetiva amplamente utilizada para avaliar a qualidade de chamadas VoIP (*Voice over IP*).

**(a)** Descreva a escala MOS e os fatores de rede — latência, jitter (variação de atraso) e perda de pacotes — que influenciam diretamente a pontuação obtida.

**(b)** O modelo E (*E-model*, ITU-T G.107 — onde ITU-T refere-se ao *International Telecommunication Union — Telecommunication Standardization Sector*, Setor de Padronização da União Internacional de Telecomunicações) permite estimar objetivamente o MOS a partir de parâmetros mensuráveis da rede. Explique o conceito do fator R e como ele se relaciona com a experiência do usuário em chamadas VoIP.

---

## Questão 3

O protocolo RTP (*Real-time Transport Protocol* — Protocolo de Transporte em Tempo Real) é a base do transporte de mídia em tempo real sobre IP (*Internet Protocol*).

**(a)** Descreva a estrutura do cabeçalho RTP, explicando a função dos campos **sequence number** (número de sequência), **timestamp** (marca temporal) e **SSRC** (*Synchronization Source* — Identificador da Fonte de Sincronização) no contexto de uma sessão de videoconferência.

**(b)** Qual é o papel do **RTCP** (*RTP Control Protocol* — Protocolo de Controle do RTP) em relação ao RTP? Como as mensagens RTCP **SR** (*Sender Report* — Relatório do Emissor) e **RR** (*Receiver Report* — Relatório do Receptor) são utilizadas para monitorar a qualidade da sessão em tempo real?

---

## Questão 4

A videoconferência em HD (*High Definition* — Alta Definição) impõe requisitos rigorosos de QoS (*Quality of Service*) que variam conforme o codec (codificador/decodificador) utilizado.

**(a)** Compare os codecs de vídeo **H.264 (AVC — *Advanced Video Coding*, Codificação de Vídeo Avançada)** e **H.265 (HEVC — *High Efficiency Video Coding*, Codificação de Vídeo de Alta Eficiência)** em termos de eficiência de compressão, requisitos de largura de banda para resolução 1080p e complexidade computacional de codificação/decodificação.

**(b)** Uma sessão de videoconferência H.264 a 1080p30 (1080 linhas de resolução, 30 fps — *frames per second*, quadros por segundo) requer aproximadamente 4 Mbps. Considerando uma rede com latência de 80 ms, jitter de 15 ms e perda de pacotes de 1%, avalie se esses parâmetros atendem aos requisitos recomendados pelo ITU-T (*International Telecommunication Union — Telecommunication Standardization Sector*) G.1010 para videoconferência interativa. Justifique sua resposta.

---

## Questão 5

Uma empresa deseja implantar um sistema de telepresença de alta definição interligando escritórios em São Paulo e Nova York, com as seguintes características:

- Vídeo: resolução 4K a 60 fps (*frames per second* — quadros por segundo), codec H.265, bitrate de 15 Mbps por sentido
- Áudio: estéreo, codec Opus a 128 kbps
- Latência fim a fim máxima aceitável: 150 ms
- Enlace WAN (*Wide Area Network* — Rede de Longa Distância) disponível: 50 Mbps simétrico

**(a)** Calcule a largura de banda total necessária para a sessão — somando os bitrates de vídeo e áudio acrescidos do overhead (sobrecarga) de protocolo RTP/*UDP* (*User Datagram Protocol*)/IP (*Internet Protocol*) de 5% sobre o payload (dados úteis) — e verifique se o enlace WAN disponível de 50 Mbps simétrico é suficiente. Apresente os valores intermediários do cálculo.

**(b)** A latência de propagação entre São Paulo e Nova York é de aproximadamente 120 ms. Dado o requisito máximo de 150 ms fim a fim, calcule a margem disponível para atrasos variáveis (serialização, enfileiramento e processamento) e especifique os mecanismos de QoS que devem ser aplicados para garantir o cumprimento do requisito.
