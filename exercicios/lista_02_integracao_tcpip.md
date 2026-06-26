# Lista de Exercícios 02 — Integração de Serviços em Ambiente TCP/IP

## Questão 1

A arquitetura TCP/IP (*Transmission Control Protocol/Internet Protocol*) foi originalmente projetada para oferecer um serviço de melhor esforço (*best-effort*), sem garantias de entrega, ordem ou temporização.

**(a)** Explique por que o modelo *best-effort* é insuficiente para suportar aplicações de voz e vídeo em tempo real em uma rede convergente.

### Questão 1 (a)

O modelo Best-effort sugere que a rede fará o maior esforço possível para realizar a entrega de pacotes, porém, ele não garante nada explicitamente, visto que não existe: Reserva em largura de banda, garantias (Atraso máximo, Jitter, Perda de pacotes), ou seja, por mais que a rede "se esforce" ela não te dá garantias, garantias essas que são extremamente necessárias quando se trata de aplicações de multimídia em tempo real (Streamings, videoconferências, ensino remoto, etc.). Para aplicações de multimídia, é necessário assegurar QoS (A qualidade do serviço), e para isso, são utilizadas duas principais arquiteturas padronizadas, IntServ e DiffServ. A IntServ funciona seguindo o seguinte fluxo:

A Aplicação solicita recursos > A Rede checa a disponibilidade de recursos > Os Roteadores reservam recursos ao longo do trajeto > A transmissão agora tem garantia de QoS > E por fim, os dados são enviados.

**(b)** Descreva os dois modelos propostos pela IETF (*Internet Engineering Task Force* — Força-Tarefa de Engenharia da Internet) para adicionar suporte a qualidade de serviço sobre IP (*Internet Protocol*): **IntServ** (*Integrated Services* — Serviços Integrados) e **DiffServ** (*Differentiated Services* — Serviços Diferenciados), destacando suas diferenças em escalabilidade e granularidade de controle.

### Questão 1 (b)

Dentre as vantagens do IntServ, podemos citar que ela possui garantias determinísticas e alta precisão em QoS, porém, possui necessidade de manter estado por fluxo, alto consumo de memória e processamento, complexidade alta e escalabilidade extremamente limitada. Já o DiffServ foi criado com o objetivo de superar os problemas de escalabilidade do IntServ, por este motivo os pacotes recebem marcações no campo DSCP do cabeçalho IP, e sendo assim os roteadores analisam apenas a classe do pacote, ao invés de milhares de fluxos realizando o controle, temos classes predefinidas (Voz, Vídeo, Dados) e todos os pacotes de uma mesma categoria são tratados da mesma forma. Apesar disso, ele também possui certas desvantagens, como não possuir garantias determinísticas e ter uma menor precisão no controle dos recursos por não possuir reserva individual, apenas políticas de prioridade.

---

## Questão 2

O protocolo RSVP (*Resource Reservation Protocol* — Protocolo de Reserva de Recursos) é o mecanismo de sinalização associado ao modelo IntServ (*Integrated Services*).

**(a)** Descreva o funcionamento do RSVP, explicando o papel das mensagens `PATH` (caminho) e `RESV` (reserva) no estabelecimento de uma reserva de recursos fim a fim.

### Questão 2 (a)

O RSVP é o protocolo de reserva de recursos utilizado pelo IntServ, serve para solicitar e reservar recursos ao longo do caminho em uma comunicação fim a fim. A mensagem PATH é enviada do emissor ao receptor, ela informa o roteador e o receptor acerca do fluxo de dados, informações como nome do emissor, taxa/tamanho dos pacotes, etc. Cada roteador registra um Path State, que é depois utilizado para encaminhar a mensagem de reserva (RESV). A mensagem RESV "responde" a mensagem PATH, o receptor vai decidir se quer reservar recursos e envia uma mensagem RESV para o emissor, usando o mesmo caminho registrado pela mensagem PATH.

**(b)** Por que o RSVP enfrenta problemas de escalabilidade em redes de backbone? Como o modelo DiffServ (*Differentiated Services*) contorna essa limitação?

### Questão 2 (b)

O RSVP apresenta problemas de escalabilidade pois o modelo IntServ reserva os recursos individualmente, por fluxo. Em resumo, todos os roteadores devem manter informações de estado pra cada fluxo ativo no momento, além de precisarem processar mensagens PATH e RESV continuamente, ou seja, a medida que o número de fluxos aumenta, aumenta também o consumo de memória, processamento, e sinalização na rede. O DiffServ contorna esse problema pois não reserva recursos individualmente, ele separa e classifica os pacotes por tipo de serviço utilizando classes (voz, vídeo, etc.), de forma que os roteadores apenas identificam uma classe e aplicam protocolos/políticas pré-definidas de acordo com a classe do pacote.

---

## Questão 3

Em uma rede corporativa convergente, VoIP (*Voice over IP* — Voz sobre IP), videoconferência e dados de escritório trafegam sobre a mesma infraestrutura IP (*Internet Protocol*).

**(a)** Explique como o campo DSCP (*Differentiated Services Code Point* — Ponto de Código de Serviços Diferenciados) no cabeçalho IP é utilizado para classificar e marcar os pacotes nesse cenário, citando os valores PHB (*Per-Hop Behavior* — Comportamento por Salto) recomendados para cada classe de tráfego: EF (*Expedited Forwarding* — Encaminhamento Expresso), AF (*Assured Forwarding* — Encaminhamento Assegurado) e BE (*Best Effort* — Melhor Esforço).

### Questão 3 (a)

O campo DSCP vai separar os tipos de pacote por códigos, definindo seu nível de prioridade e que tipo de política aplicar, VoIP utiliza PHB EF (Expedited Fowarding), possui baixa latência e máxima prioridade. Videoconferência utiliza o PHB AF(Assured Fowarding), possui alta prioridade, garantia de encaminhamento e níveis de precedência para descartar em caso de congestionamento. Dados gerais do escritório, utilizam da BE(Best Effort), onde os pacotes são encaminhados de acordo com a disponibilidade da rede, não possuindo garantia alguma de QoS e nem nível de prioridade.

**(b)** Descreva o papel dos mecanismos de **policiamento** (*policing*) e **conformação** (*shaping*) de tráfego na borda da rede, explicando a diferença entre os dois.

### Questão 3 (b)

O Policiamento tem objetivo de fiscalizar o tráfego recebido e checar se ele respeita as definições estabelecidas, o funcionamento consiste em: Medir o tráfego > Comparar com o Perfil de Tráfego Permitido > Se o tráfego exceder os limites estabelecidos, aplica uma correção pré-definida (descartar pacotes, reduzir prioridade, etc.). A Conformação procura adaptar o tráfego de acordo com o perfil permitido, utilizando buffers para armazenar pacotes que excedam as pré-definições, é útil para reduzir congestionamentos, porém aumenta latência devido o enfileiramento.

---

## Questão 4

O protocolo SIP (*Session Initiation Protocol* — Protocolo de Iniciação de Sessão) é amplamente utilizado para sinalização de sessões multimídia sobre IP (*Internet Protocol*).

**(a)** Descreva a sequência de mensagens SIP envolvida no estabelecimento e encerramento de uma chamada VoIP (*Voice over IP*) entre dois *user agents* (agentes de usuário), incluindo os papéis de *proxy* (intermediário de sinalização) e servidor de registro.

### Questão 4 (a)

A sequência de mensagens é: REGISTER > INVITE > 100 TRYING > 180 RINGING > 200 OK > ACK. Após a última mensagem (ACK), se tudo correr bem, a sessão SIP está estabelecida. No encerramento, a sequência é bem menor: BYE > 200 OK. A sessão é finalizada, liberando os recursos associados à chamada. O servidor de resgistros serve para autenticar os usuários, associar os identificadores SIP aos IPs atuais e guardar informações em um servidor de localização (Isso permite que os usuários sejam encontrados mesmo que mudem de rede).

**(b)** Como o SDP (*Session Description Protocol* — Protocolo de Descrição de Sessão) complementa o SIP na negociação dos parâmetros de mídia — codecs, endereço IP e porta RTP (*Real-time Transport Protocol* — Protocolo de Transporte em Tempo Real) — de uma sessão?

### Questão 4 (b)

O SDP complementa o SIP pois ele especifica como a mídia será transmitida, descrevendo os parâmetros da mídia (codecs, endereço IP, portas RTP) para garantir que a comunicação ocorra corretamente, enquanto o SIP realiza mais o controle de "Estabelecer - Alterar - Finalizar" a sessão.

---

## Questão 5

Considere uma rede empresarial que integra serviços de voz, vídeo sob demanda e acesso à internet sobre um único enlace WAN (*Wide Area Network* — Rede de Longa Distância) de 100 Mbps.

A distribuição de tráfego esperada é:
- VoIP (*Voice over IP*): 20 chamadas simultâneas de 64 kbps cada
- Videoconferência HD (*High Definition* — Alta Definição): 5 sessões de 4 Mbps cada
- Dados: tráfego restante

**(a)** Calcule a largura de banda reservada para voz e para vídeo, apresentando os valores intermediários por classe, e determine a banda remanescente disponível para dados.

**(b)** Elabore o projeto da política de filas LLQ (*Low Latency Queuing* — Enfileiramento de Baixa Latência) + CBWFQ (*Class-Based Weighted Fair Queuing* — Enfileiramento Justo Ponderado Baseado em Classes) para esse enlace, especificando para cada classe: o mecanismo de escalonamento utilizado, a banda garantida ou peso relativo atribuído e a justificativa técnica com base nos requisitos de latência e sensibilidade a jitter (variação de atraso) de cada tipo de tráfego.
