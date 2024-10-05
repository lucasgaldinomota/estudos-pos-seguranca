# Kubernetes

Kubernetes é uma plataforma open-source que automatiza a implantação, escalonamento e gerenciamento de aplicações em contêineres. Originalmente desenvolvido pelo Google, ele agora é mantido pela Cloud Native Computing Foundation (CNCF) e tornou-se um dos principais orquestradores de contêineres, sendo amplamente utilizado em ambientes de DevOps e nuvem.

Principais componentes e funcionalidades do Kubernetes:

	1.	Cluster: Um conjunto de nós (máquinas físicas ou virtuais) que executam aplicações em contêineres.
	•	Master Node: Gerencia o cluster, responsável por orquestrar as operações dos nós de trabalho.
	•	Worker Nodes: Hospedam os contêineres que executam as aplicações.
	2.	Pods: A menor unidade de execução no Kubernetes. Um pod pode conter um ou mais contêineres, que compartilham rede e armazenamento.
	3.	Deployment: Gerencia o ciclo de vida dos pods, garantindo que o número desejado de réplicas de uma aplicação esteja sempre em execução.
	4.	Services: Expõem um conjunto de pods como um serviço de rede, permitindo que os pods sejam acessados de maneira estável.
	5.	ConfigMaps e Secrets: Permitem injetar configurações e informações sensíveis, como senhas, nos pods.
	6.	Namespaces: Permitem a separação de recursos dentro de um cluster, ajudando a organizar e isolar aplicações.
	7.	Persistent Volumes (PV) e Persistent Volume Claims (PVC): Gerenciam o armazenamento persistente que pode ser reutilizado pelos pods.

Vantagens:

	•	Escalonamento automático: Kubernetes ajusta automaticamente o número de pods com base na demanda de recursos.
	•	Autocorreção: Em caso de falhas, ele recria ou substitui pods automaticamente.
	•	Portabilidade: Funciona em várias plataformas, incluindo nuvens públicas e privadas.
	•	Gerenciamento de atualizações: Suporta rollbacks e atualizações contínuas (rolling updates) sem tempo de inatividade.

Kubernetes é amplamente adotado para rodar aplicações em microserviços, especialmente em ambientes de produção que exigem alta disponibilidade e resiliência.