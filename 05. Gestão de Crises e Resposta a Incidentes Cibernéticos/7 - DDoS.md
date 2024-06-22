# DDoS

Um ataque DDoS (Distributed Denial of Service, ou Negação de Serviço Distribuída) é um tipo de ataque cibernético onde vários sistemas comprometidos, frequentemente distribuídos globalmente, são usados para sobrecarregar um alvo específico (como um servidor, serviço ou rede) com uma quantidade massiva de tráfego. O objetivo é tornar os recursos do alvo indisponíveis para seus usuários legítimos. 

### Componentes de um Ataque DDoS

1. **Atacante**: A pessoa ou grupo que inicia o ataque.
2. **Máquinas Comprometidas (Bots)**: Computadores e dispositivos que foram infectados com malware e são controlados pelo atacante. Coletivamente, essas máquinas formam uma botnet.
3. **Alvo**: O sistema, serviço ou rede que está sendo atacado.

### Tipos Comuns de Ataques DDoS

1. **Ataques de Volume**
   - **UDP Flood**: Envia uma grande quantidade de pacotes UDP (User Datagram Protocol) para alvos aleatórios em um servidor, consumindo sua largura de banda.
   - **ICMP Flood (Ping Flood)**: Inunda o alvo com pacotes ICMP (Internet Control Message Protocol), geralmente ping requests, para sobrecarregar sua capacidade de processamento.

2. **Ataques de Protocolo**
   - **SYN Flood**: Envia uma série de pacotes SYN (Synchronize) para iniciar conexões TCP, mas nunca conclui o handshake, deixando o servidor com conexões meio abertas.
   - **ACK Flood**: Envia pacotes TCP ACK (Acknowledge) para sobrecarregar a capacidade do servidor de gerenciar a tabela de estado de conexão.

3. **Ataques de Camada de Aplicação**
   - **HTTP Flood**: Envia requisições HTTP (normalmente GET ou POST) para um servidor web, simulando tráfego legítimo mas em grande volume para esgotar os recursos do servidor.
   - **Slowloris**: Mantém conexões HTTP abertas enviando cabeçalhos HTTP incompletos, esgotando a capacidade do servidor de gerenciar novas conexões.

### Impacto de um Ataque DDoS

- **Indisponibilidade de Serviço**: Os serviços online ficam indisponíveis para os usuários legítimos.
- **Perda Financeira**: Empresas podem perder receitas devido à interrupção de serviços.
- **Danos à Reputação**: A confiança dos clientes e parceiros pode ser abalada.
- **Custos de Mitigação**: Gastos significativos podem ser necessários para mitigar o ataque e restaurar os serviços.

### Técnicas de Mitigação

1. **Dimensionamento da Capacidade**
   - **Overprovisioning**: Ter mais capacidade de rede e servidores do que o normalmente necessário para lidar com picos de tráfego.

2. **Uso de Serviços Especializados**
   - **Content Delivery Networks (CDNs)**: Distribuir o tráfego através de uma rede de servidores para reduzir a carga em qualquer único ponto.
   - **Serviços de Mitigação DDoS**: Empresas especializadas oferecem proteção contra DDoS, analisando e filtrando o tráfego malicioso.

3. **Configurações de Rede**
   - **Rate Limiting**: Limitar o número de solicitações que um IP pode fazer em um determinado período.
   - **Firewalls e Sistemas de Detecção de Intrusões (IDS)**: Configurar regras para bloquear tráfego suspeito ou malicioso.

4. **Análise e Monitoramento Contínuos**
   - **Monitoramento de Tráfego**: Utilizar ferramentas para monitorar o tráfego de rede e identificar padrões anômalos.
   - **Alertas e Respostas Automatizadas**: Implementar sistemas que automaticamente detectam e respondem a ataques DDoS.

5. **Diversificação da Infraestrutura**
   - **Anycast**: Usar o roteamento Anycast para distribuir o tráfego entre vários data centers.

### Exemplo de Mitigação de um Ataque DDoS

Imagine que uma empresa de e-commerce está enfrentando um ataque DDoS que está sobrecarregando seus servidores web. Aqui está como a mitigação poderia ser feita:

1. **Detecção Inicial**: Ferramentas de monitoramento detectam um aumento anômalo no tráfego de rede.
2. **Redirecionamento de Tráfego**: O tráfego é redirecionado através de uma CDN que distribui o tráfego por vários servidores em diferentes localidades.
3. **Filtragem de Tráfego**: Regras de firewall são ajustadas para bloquear tráfego de IPs suspeitos ou de geografias que não são relevantes para o negócio.
4. **Rate Limiting**: Implementa-se rate limiting para limitar o número de requisições que um único IP pode fazer.
5. **Comunicação com o Fornecedor de Mitigação DDoS**: Se a empresa tiver um contrato com um fornecedor de mitigação DDoS, eles ativam serviços especializados para absorver e filtrar o tráfego de ataque.

### Conclusão

Ataques DDoS são uma ameaça significativa à disponibilidade de serviços online. A mitigação eficaz requer uma combinação de planejamento, implementação de tecnologias adequadas e uso de serviços especializados. Ao adotar uma abordagem proativa e camadas de defesa, as organizações podem reduzir o impacto de ataques DDoS e manter a continuidade dos negócios.