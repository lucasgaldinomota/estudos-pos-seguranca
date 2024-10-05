# Daemon Sets

DaemonSets são um tipo de recurso do Kubernetes que garante que uma cópia específica de um pod seja executada em cada nó de um cluster. Eles são úteis quando você deseja que um pod seja automaticamente executado em todos os nós ou em uma seleção específica de nós, geralmente para tarefas como monitoramento, logging, gerenciamento de rede, ou qualquer outra função que precise estar presente em todos os nós.

Principais Características de DaemonSets:

	1.	Executa um Pod em Cada Nó: Um DaemonSet garante que haja exatamente uma instância de um pod em cada nó do cluster Kubernetes, sem a necessidade de escalá-lo manualmente para cada nó.
	2.	Ajuste Dinâmico: Quando novos nós são adicionados ao cluster, o DaemonSet cria automaticamente uma instância do pod nesse novo nó. Da mesma forma, quando um nó é removido, o pod associado a esse nó é também removido.
	3.	Aplicações Comuns:
	•	Monitoramento: Ferramentas de monitoramento como o Prometheus Node Exporter podem ser implantadas como DaemonSets para coletar métricas de cada nó.
	•	Logging: Soluções como Fluentd ou Logstash são frequentemente executadas como DaemonSets para centralizar logs.
	•	Gerenciamento de Rede: Pods que precisam ajustar configurações de rede em cada nó, como agentes de rede (Calico, Cilium), também são implantados como DaemonSets.

Exemplo de DaemonSet:

Aqui está um exemplo básico de DaemonSet que executa um contêiner NGINX em todos os nós do cluster:

apiVersion: apps/v1
kind: DaemonSet
metadata:
  name: nginx-daemonset
spec:
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:latest
        ports:
        - containerPort: 80

Como Funciona o DaemonSet:

	1.	Criação: Quando você cria um DaemonSet, o Kubernetes automaticamente garante que uma cópia do pod definido no DaemonSet seja executada em todos os nós do cluster que correspondam às regras do agendamento.
	2.	Adição de Nós: Se você adicionar novos nós ao cluster, o DaemonSet detecta e cria uma nova instância do pod nesses novos nós.
	3.	Atualização de Pods: Se você atualizar o DaemonSet (por exemplo, alterando a imagem do contêiner), ele irá recriar os pods em todos os nós para refletir a nova configuração.
	4.	Exclusão de DaemonSet: Quando você deleta um DaemonSet, o Kubernetes remove automaticamente os pods de todos os nós onde eles estavam sendo executados.

Gerenciamento Seletivo de Nós:

Caso você queira que o DaemonSet rode apenas em um subconjunto de nós, você pode usar node selectors ou tolerations. Isso permite que você controle onde os pods do DaemonSet serão agendados.

	•	Node Selectors: Define que os pods do DaemonSet só rodem em nós que possuem certas labels.

spec:
  template:
    spec:
      nodeSelector:
        disktype: ssd


	•	Tolerations: Usado para que os pods do DaemonSet possam rodar em nós com taints específicos.

spec:
  template:
    spec:
      tolerations:
      - key: "key1"
        operator: "Equal"
        value: "value1"
        effect: "NoSchedule"



Estratégias de Atualização do DaemonSet:

Ao atualizar um DaemonSet, você pode usar estratégias específicas para controlar como os pods são atualizados. A mais comum é a estratégia RollingUpdate, que atualiza os pods gradualmente, um nó de cada vez.

updateStrategy:
  type: RollingUpdate
  rollingUpdate:
    maxUnavailable: 1

Vantagens do DaemonSet:

	•	Simplicidade: Garante que uma única cópia de um pod seja executada em cada nó, sem necessidade de escalá-lo manualmente.
	•	Escalabilidade Automática: Quando nós são adicionados ou removidos, o DaemonSet gerencia automaticamente a criação ou remoção dos pods.
	•	Desempenho: Ideal para tarefas de monitoramento e coleta de dados, pois distribui a carga de trabalho uniformemente em todos os nós.

Limitações:

	•	Um Pod por Nó: Um DaemonSet executa apenas uma instância do pod por nó. Se você precisar de várias instâncias por nó, DaemonSet não seria a escolha ideal.
	•	Somente para Pods de Nós Específicos: O DaemonSet é mais adequado para workloads que precisam ser executadas em todos os nós ou em grupos específicos de nós. Para workloads gerais, Deployments podem ser uma opção melhor.

DaemonSets são essenciais para garantir a execução de tarefas críticas e serviços auxiliares em todos os nós de um cluster Kubernetes, simplificando o gerenciamento dessas funções distribuídas.