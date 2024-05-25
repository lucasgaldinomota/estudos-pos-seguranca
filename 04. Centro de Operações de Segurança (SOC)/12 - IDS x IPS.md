# IDS vs IPS

IDS (Intrusion Detection System) e IPS (Intrusion Prevention System) são duas tecnologias de segurança que ajudam a proteger redes contra ameaças cibernéticas, mas têm funções ligeiramente diferentes:

1. **IDS (Intrusion Detection System)**:
   - Um IDS monitora o tráfego de rede em busca de atividades suspeitas ou maliciosas.
   - Ele analisa os pacotes de dados que passam pela rede em tempo real em busca de padrões de tráfego que possam indicar uma violação de segurança.
   - Quando detecta uma possível ameaça, o IDS gera alertas para os administradores de rede, que então podem investigar e responder ao incidente.
   - No entanto, um IDS não toma medidas para interromper o tráfego malicioso. Ele apenas detecta e relata.

2. **IPS (Intrusion Prevention System)**:
   - Um IPS vai além do IDS, pois não apenas detecta atividades maliciosas, mas também toma medidas para bloqueá-las.
   - Assim como um IDS, um IPS monitora o tráfego de rede em busca de ameaças. No entanto, quando identifica uma ameaça, ele pode tomar medidas imediatas para bloquear o tráfego malicioso.
   - Essas medidas podem incluir bloqueio de IP, bloqueio de portas, rejeição de pacotes suspeitos ou outras ações para interromper a atividade maliciosa.
   - Em geral, um IPS é considerado uma solução mais proativa, pois não apenas alerta sobre ameaças, mas também as impede de causar danos à rede.

Em resumo, enquanto um IDS é passivo e apenas detecta atividades maliciosas, um IPS é ativo e pode tomar medidas para prevenir essas atividades. Ambos são componentes importantes da segurança da rede e muitas vezes são usados em conjunto para fornecer uma defesa mais abrangente contra ameaças cibernéticas.