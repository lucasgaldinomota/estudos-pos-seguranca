# RDP VS Ransomware

A porta 3389, utilizada pelo Protocolo de Desktop Remoto (RDP), está frequentemente associada a ataques de ransomware devido à sua ampla utilização e potencial para vulnerabilidades. O RDP permite que usuários se conectem remotamente a um computador, mas se não for configurado e protegido adequadamente, pode ser explorado por cibercriminosos. Aqui estão as principais formas pelas quais a porta 3389 se relaciona com ataques de ransomware:

### Como a Porta 3389 Relaciona-se com Ransomware

1. **Acesso Não Autorizado**
   - Criminosos podem usar ataques de força bruta para adivinhar senhas de RDP, ganhando acesso ao sistema. Uma vez dentro, eles podem implantar ransomware e criptografar dados críticos.
   - Ferramentas automatizadas de ataque são frequentemente usadas para varrer a internet em busca de sistemas que tenham a porta 3389 aberta.

2. **Vulnerabilidades Exploratórias**
   - Vulnerabilidades conhecidas no RDP, como a BlueKeep (CVE-2019-0708), permitem a execução de código remoto sem necessidade de autenticação. Explorar tais vulnerabilidades pode permitir a instalação de ransomware sem qualquer interação do usuário.

3. **Movimentação Lateral**
   - Uma vez que um atacante obtém acesso a um sistema via RDP, ele pode se mover lateralmente na rede para comprometer outros sistemas, propagando o ransomware.

4. **Ferramentas de Exploração Automatizadas**
   - Existem ferramentas específicas criadas para automatizar a exploração de sistemas RDP vulneráveis, facilitando o trabalho dos atacantes em implantar ransomware em grande escala.

### Exemplos de Ransomware Usando RDP

1. **SamSam**
   - O grupo por trás do ransomware SamSam usou ataques de força bruta em RDP para obter acesso a redes corporativas e implantar o ransomware, causando prejuízos significativos a várias organizações.

2. **Dharma/Crysis**
   - Esse ransomware também se espalha usando credenciais RDP fracas ou comprometidas, criptografando dados e exigindo resgates em Bitcoin.

3. **Ryuk**
   - Ryuk é conhecido por utilizar RDP comprometido como um vetor inicial de ataque, frequentemente em combinação com outras ferramentas de ataque automatizadas.

### Medidas de Proteção

Para proteger a porta 3389 contra ataques de ransomware, considere as seguintes práticas:

1. **Autenticação Multi-Fator (MFA)**
   - Implementar MFA para reduzir a probabilidade de acesso não autorizado mesmo se as credenciais forem comprometidas.

2. **VPNs**
   - Use uma VPN para acessar o RDP, restringindo o acesso à rede interna da organização e escondendo a porta 3389 da internet pública.

3. **Firewalls e Filtragem de IP**
   - Configurar firewalls para limitar o acesso à porta 3389 apenas a endereços IP específicos e confiáveis.

4. **Alteração da Porta Padrão**
   - Mudar a porta padrão 3389 para outra porta pode reduzir ataques automatizados, embora não elimine completamente o risco.

5. **Atualizações e Patches**
   - Manter todos os sistemas e o software RDP atualizados com os patches de segurança mais recentes para corrigir vulnerabilidades conhecidas.

6. **Monitoramento e Logs**
   - Implementar monitoramento contínuo e revisar logs de acesso para detectar e responder rapidamente a atividades suspeitas.