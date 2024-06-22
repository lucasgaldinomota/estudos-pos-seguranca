# SSTP e PPTP

SSTP (Secure Socket Tunneling Protocol) e PPTP (Point-to-Point Tunneling Protocol) são protocolos usados para criar redes privadas virtuais (VPNs). Ambos permitem a criação de túneis seguros através da internet para conectar dispositivos ou redes remotas, mas têm diferenças significativas em termos de segurança, performance e compatibilidade.

### PPTP (Point-to-Point Tunneling Protocol)

#### Características:

1. **Desenvolvido pela Microsoft**: Originalmente desenvolvido pela Microsoft em parceria com outras empresas.
2. **Fácil Configuração**: Simples de configurar e disponível em quase todos os sistemas operacionais, incluindo Windows, macOS, Linux, Android, e iOS.
3. **Desempenho**: Oferece boas velocidades de conexão devido à sua menor sobrecarga.
4. **Segurança**: Utiliza o protocolo GRE (Generic Routing Encapsulation) e autenticação MS-CHAP v2. No entanto, PPTP é considerado inseguro por muitos especialistas em segurança, pois suas vulnerabilidades foram bem documentadas e exploradas ao longo dos anos.
5. **Porta Utilizada**: Utiliza a porta TCP 1723.

#### Vantagens:

- **Compatibilidade**: Suporte amplo em vários dispositivos e sistemas operacionais.
- **Desempenho**: Baixa sobrecarga, resultando em conexões rápidas.

#### Desvantagens:

- **Segurança**: Vulnerabilidades conhecidas tornam o PPTP inadequado para ambientes que requerem alta segurança.
- **Criptografia Fraca**: Usa MPPE (Microsoft Point-to-Point Encryption), que não é considerada segura para dados sensíveis.

### SSTP (Secure Socket Tunneling Protocol)

#### Características:

1. **Desenvolvido pela Microsoft**: Lançado com o Windows Vista e nativamente suportado em sistemas operacionais Windows posteriores.
2. **Segurança**: Utiliza SSL/TLS para criar uma conexão segura. Isso oferece uma camada robusta de criptografia e autenticação, tornando o SSTP muito mais seguro que o PPTP.
3. **Compatibilidade**: Nativamente suportado no Windows, mas suporte limitado em outros sistemas operacionais sem software adicional.
4. **Porta Utilizada**: Utiliza a porta TCP 443, o que facilita a passagem por firewalls e proxies que geralmente bloqueiam outras portas VPN.
5. **Desempenho**: Pode ser mais lento que o PPTP devido à criptografia mais forte e maior sobrecarga.

#### Vantagens:

- **Segurança**: Usa SSL/TLS, que oferece uma forte proteção contra interceptação e ataques.
- **Bypass de Firewalls**: A utilização da porta TCP 443, a mesma usada pelo HTTPS, permite que o SSTP passe por firewalls e proxies que bloqueiam outras portas VPN.
- **Estabilidade**: Menos propenso a ser bloqueado, proporcionando uma conexão VPN mais estável.

#### Desvantagens:

- **Compatibilidade**: Suporte limitado fora dos sistemas Windows. Pode necessitar de software adicional para funcionar em outras plataformas.
- **Desempenho**: A forte criptografia pode introduzir alguma latência.

### Comparação entre SSTP e PPTP

| Característica                 | PPTP                                       | SSTP                                            |
| ------------------------------ | ------------------------------------------ | ----------------------------------------------- |
| **Segurança**                  | Fraca, vulnerável                          | Forte, usando SSL/TLS                           |
| **Facilidade de Configuração** | Fácil, amplamente suportado                | Moderada, melhor no Windows                     |
| **Desempenho**                 | Alta velocidade, baixa sobrecarga          | Pode ser mais lento devido à criptografia forte |
| **Compatibilidade**            | Alta, suporta muitos sistemas operacionais | Principalmente suportado no Windows             |
| **Porta Utilizada**            | TCP 1723                                   | TCP 443                                         |

### Conclusão

- **PPTP** é uma opção mais simples e amplamente suportada, mas suas vulnerabilidades de segurança o tornam inadequado para proteger dados sensíveis.
- **SSTP** oferece uma segurança muito melhor através do uso de SSL/TLS e é menos provável de ser bloqueado por firewalls, mas é mais compatível principalmente com sistemas Windows e pode introduzir mais latência devido à criptografia robusta.

A escolha entre SSTP e PPTP deve ser baseada nas necessidades específicas de segurança, desempenho e compatibilidade da sua rede. Em ambientes onde a segurança é uma prioridade, SSTP é a escolha recomendada.