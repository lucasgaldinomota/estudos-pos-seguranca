# Escalabilidade Horizontal

A escalabilidade horizontal (também conhecida como scale-out) é o processo de aumentar a capacidade de um sistema adicionando mais máquinas ou servidores ao ambiente, em vez de melhorar as especificações de um único servidor. Essa abordagem é amplamente utilizada em arquiteturas modernas, como sistemas distribuídos e serviços em nuvem.

Como funciona a escalabilidade horizontal?

Na escalabilidade horizontal, o sistema é projetado para trabalhar de maneira distribuída. Quando a demanda cresce, mais unidades (servidores ou máquinas virtuais) são adicionadas ao grupo, compartilhando a carga de trabalho.

Exemplo:
	•	Antes da escalabilidade horizontal: O sistema opera com 3 servidores.
	•	Após a escalabilidade horizontal: Mais 2 servidores são adicionados, totalizando 5.

Vantagens da escalabilidade horizontal
	1.	Crescimento ilimitado:
	•	Permite adicionar servidores conforme necessário, possibilitando expansão quase ilimitada.
	2.	Alta disponibilidade:
	•	Reduz o risco de falhas catastróficas, pois o sistema distribui a carga entre várias máquinas (resiliência).
	3.	Custo proporcional:
	•	É possível escalar gradualmente, adicionando máquinas menores e menos caras.
	4.	Manutenção sem interrupções:
	•	Máquinas individuais podem ser substituídas ou atualizadas sem que o sistema inteiro seja desligado.
	5.	Flexibilidade:
	•	Ideal para sistemas distribuídos, como bancos de dados NoSQL (ex.: Cassandra, MongoDB) e microsserviços.

Desvantagens da escalabilidade horizontal
	1.	Complexidade:
	•	Requer balanceadores de carga e arquiteturas projetadas para lidar com múltiplas máquinas.
	•	Sistemas precisam ser desenhados para lidar com paralelismo e consistência de dados.
	2.	Custo inicial de configuração:
	•	A configuração inicial pode ser mais cara e complexa devido à necessidade de software de gerenciamento e balanceamento.
	3.	Coerência de dados:
	•	Gerenciar a consistência entre múltiplas máquinas pode ser desafiador, especialmente em sistemas de banco de dados.
	4.	Latência de comunicação:
	•	A comunicação entre diferentes servidores pode adicionar atrasos.

Comparação: Escalabilidade Horizontal x Escalabilidade Vertical

Aspecto	Escalabilidade Horizontal	Escalabilidade Vertical
Estratégia	Adicionar mais máquinas	Melhorar especificações do servidor
Complexidade	Maior	Menor
Custo inicial	Geralmente maior	Geralmente menor
Limite de crescimento	Virtualmente ilimitado	Restrito ao hardware disponível
Resiliência	Alta (sem ponto único de falha)	Baixa (ponto único de falha - SPOF)
Tempo de inatividade	Geralmente nulo	Potencialmente alto durante upgrades

Quando usar escalabilidade horizontal?
	•	Sistemas com grande volume de usuários simultâneos:
	•	Exemplo: Plataformas de streaming (Netflix, YouTube), redes sociais.
	•	Sistemas distribuídos:
	•	Exemplo: Bancos de dados NoSQL, processamento de big data.
	•	Alta disponibilidade e tolerância a falhas:
	•	Exemplo: Serviços financeiros, e-commerces.
	•	Infraestruturas em nuvem:
	•	Exemplo: Uso de auto-scaling no AWS, Azure, ou Google Cloud para adicionar máquinas automaticamente conforme a demanda.

Ferramentas e Tecnologias Comuns
	1.	Balanceadores de carga:
Distribuem o tráfego entre vários servidores.
	•	Exemplo: NGINX, HAProxy, AWS Elastic Load Balancer.
	2.	Bancos de dados escaláveis horizontalmente:
	•	Exemplo: MongoDB, Apache Cassandra, Google Bigtable.
	3.	Orquestradores e Containers:
Facilitam a escalabilidade horizontal de aplicações em contêineres.
	•	Exemplo: Kubernetes, Docker Swarm.
	4.	Infraestruturas elásticas:
Escalam automaticamente conforme a necessidade.
	•	Exemplo: AWS Auto Scaling, Google Kubernetes Engine (GKE).

Exemplo Prático de Escalabilidade Horizontal

Um e-commerce com alto tráfego sazonal implementa escalabilidade horizontal:
	•	Durante o período normal, 3 servidores atendem a 5.000 usuários simultâneos.
	•	Durante promoções, o sistema adiciona automaticamente mais 7 servidores para suportar 50.000 usuários simultâneos.
	•	Após o evento, os servidores extras são removidos para reduzir custos.