# Syslog

Syslog é um padrão para a mensagem de registro (logging) de informações em sistemas de computadores. Foi originalmente desenvolvido para o sistema operacional Unix, mas agora é amplamente utilizado em diversos sistemas operacionais, dispositivos de rede e aplicações. Syslog permite que os sistemas gerem, enviem, recebam e armazenem mensagens de log de uma maneira centralizada, o que é crucial para o monitoramento, manutenção e segurança de infraestruturas de TI.

Aqui estão os componentes e conceitos principais do Syslog:

1. **Syslog Message**:
   - Cada mensagem de syslog consiste em um cabeçalho e uma parte de mensagem.
   - O cabeçalho inclui a prioridade (PRI), a marca de data e hora e o nome do host.
   - A parte da mensagem contém o conteúdo da log, que pode variar conforme a aplicação ou dispositivo que está gerando a mensagem.

2. **Facility (Facilidade)**:
   - Representa o tipo de origem da mensagem. Exemplo de facilidades incluem `auth`, `cron`, `daemon`, `kern` (kernel), `mail`, `syslog`, `user`, `local0` a `local7` (definidas pelo usuário), entre outros.
   - A facilidade ajuda a categorizar as mensagens para que elas possam ser filtradas ou roteadas adequadamente.

3. **Severity (Severidade)**:
   - Representa a gravidade da mensagem de log.
   - Os níveis de severidade são numerados de 0 a 7, onde 0 é a mais crítica e 7 a menos crítica:
     - 0 - Emergency: o sistema está inutilizável
     - 1 - Alert: ação deve ser tomada imediatamente
     - 2 - Critical: condições críticas
     - 3 - Error: condições de erro
     - 4 - Warning: condições de aviso
     - 5 - Notice: condições normais, mas significativas
     - 6 - Informational: mensagens informativas
     - 7 - Debug: mensagens de debug, detalhadas

4. **Syslog Server (Servidor Syslog)**:
   - Um servidor centralizado que recebe e armazena mensagens de log de vários dispositivos e sistemas.
   - Ajuda na agregação, análise e monitoramento de logs em uma rede.
   - Exemplos de servidores Syslog incluem rsyslog, syslog-ng e Graylog.

5. **Syslog Client (Cliente Syslog)**:
   - Qualquer dispositivo ou aplicação que gera mensagens de log e as envia para um servidor Syslog.
   - Pode incluir servidores, roteadores, switches, firewalls, aplicações e até mesmo dispositivos IoT.

6. **Protocolo de Transporte**:
   - Syslog pode usar UDP (porta 514) para transporte de mensagens, que é rápido mas não garante a entrega das mensagens.
   - Pode também usar TCP para garantir a entrega das mensagens e, frequentemente, é configurado para usar TLS para encriptação e segurança adicional.

### Exemplo de Configuração Básica

Aqui está um exemplo básico de configuração do Syslog em um sistema Unix/Linux usando `rsyslog`:

**Configuração do Cliente Syslog (`/etc/rsyslog.conf`):**
```plaintext
# Carregar o módulo UDP Syslog
module(load="imudp")
input(type="imudp" port="514")

# Carregar o módulo TCP Syslog
module(load="imtcp")
input(type="imtcp" port="514")

# Definir o servidor Syslog remoto
*.* @192.168.1.100:514   # Para UDP
*.* @@192.168.1.100:514  # Para TCP
```

**Configuração do Servidor Syslog (`/etc/rsyslog.conf`):**
```plaintext
# Carregar o módulo UDP Syslog
module(load="imudp")
input(type="imudp" port="514")

# Carregar o módulo TCP Syslog
module(load="imtcp")
input(type="imtcp" port="514")

# Configurar o armazenamento das mensagens de log
*.* /var/log/syslog
```

### Benefícios do Uso do Syslog

- **Centralização**: Permite coletar e armazenar logs de diferentes dispositivos em um único local, facilitando o gerenciamento e a análise.
- **Monitoramento e Auditoria**: Facilita o monitoramento contínuo e a auditoria de atividades de rede e sistemas.
- **Correlação de Eventos**: Ajuda na correlação de eventos e na detecção de incidentes de segurança.
- **Análise e Relatórios**: Fornece uma base para a análise de logs e a geração de relatórios para conformidade e diagnóstico de problemas.

Syslog é uma ferramenta essencial para administradores de sistemas e profissionais de segurança cibernética, proporcionando uma visão unificada e detalhada do que está acontecendo em uma infraestrutura de TI.