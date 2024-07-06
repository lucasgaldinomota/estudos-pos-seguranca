# Reflexive DDoS

Reflexive DDoS, ou DDoS Reflexivo (Distributed Denial of Service Reflexivo), é uma variação dos ataques DDoS que faz uso de servidores mal configurados para amplificar o tráfego direcionado a um alvo específico. Neste tipo de ataque, os atacantes enviam pacotes de solicitação falsificados com o endereço IP de destino forjado para servidores vulneráveis que então respondem automaticamente ao endereço IP de destino, inundando-o com uma quantidade muito maior de tráfego do que o inicialmente enviado pelos atacantes.

### Funcionamento do Ataque Reflexivo DDoS

1. **Solicitação Falsificada**: O atacante envia pacotes de solicitação para servidores mal configurados, como servidores DNS abertos, servidores NTP (Network Time Protocol) ou servidores SNMP (Simple Network Management Protocol), com o endereço IP de destino forjado para parecer o endereço IP do alvo.
   
2. **Resposta Amplificada**: O servidor mal configurado, ao receber a solicitação falsificada, responde automaticamente ao endereço IP de destino, que é o alvo do ataque. A resposta é frequentemente amplificada, o que significa que é significativamente maior do que a solicitação inicial recebida pelo servidor.

3. **Sobrecarga do Alvo**: Como resultado, o alvo do ataque é inundado com uma quantidade massiva de tráfego, muito além de sua capacidade normal de processamento, causando indisponibilidade de serviço para os usuários legítimos.

### Características do Ataque Reflexivo DDoS

- **Amplificação**: O tráfego enviado ao alvo é amplificado pelo servidor mal configurado, o que aumenta significativamente o impacto do ataque.
- **Anonimato do Atacante**: Como o tráfego é originado de servidores legítimos, mas mal configurados, pode ser difícil rastrear a origem do ataque, proporcionando anonimato ao atacante.
- **Facilidade de Execução**: Os ataques reflexivos DDoS são relativamente fáceis de realizar, pois exploram vulnerabilidades conhecidas em servidores mal configurados.

### Exemplos de Servidores Usados em Ataques Reflexivos DDoS

1. **Servidores DNS Abertos**: Servidores DNS configurados incorretamente que permitem consultas recursivas de qualquer origem.
2. **Servidores NTP**: Servidores NTP que permitem consultas monlist, uma funcionalidade obsoleta que pode ser abusada para amplificar ataques.
3. **Servidores SNMP**: Servidores SNMP mal configurados que respondem a solicitações SNMP com grandes quantidades de dados, amplificando assim o tráfego.

### Mitigação de Ataques Reflexivos DDoS

1. **Filtragem de Tráfego**: Implementar filtros de entrada para bloquear pacotes de solicitação falsificados antes que atinjam o alvo.
2. **Configuração Segura de Servidores**: Garantir que servidores DNS, NTP e SNMP estejam corretamente configurados para evitar serem usados em ataques reflexivos.
3. **Monitoramento de Rede**: Monitorar a rede em busca de padrões de tráfego incomuns que possam indicar um ataque em andamento.
4. **Atualizações de Segurança**: Manter todos os sistemas e servidores atualizados com as últimas correções de segurança para mitigar vulnerabilidades conhecidas.
5. **Redução da Amplitude de Resposta**: Desativar ou limitar funcionalidades desnecessárias que possam ser usadas para amplificar o tráfego em servidores vulneráveis.

### Conclusão

Os ataques reflexivos DDoS representam uma ameaça significativa à disponibilidade de serviços online, aproveitando-se de servidores mal configurados para amplificar o tráfego direcionado a um alvo específico. A mitigação eficaz requer uma combinação de práticas de segurança adequadas, monitoramento contínuo e atualizações de segurança para evitar que servidores vulneráveis sejam usados em ataques DDoS.