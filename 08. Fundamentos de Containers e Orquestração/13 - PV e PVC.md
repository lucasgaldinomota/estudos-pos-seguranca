# PV E PVC

No Kubernetes, PV (Persistent Volume) e PVC (Persistent Volume Claim) são componentes usados para gerenciar armazenamento persistente, permitindo que dados sejam armazenados e acessados por pods, mesmo que eles sejam reiniciados ou realocados. Isso é crucial para aplicações que precisam manter estado, como bancos de dados.

Persistent Volume (PV)

Um Persistent Volume (PV) é um recurso de armazenamento no cluster que foi provisionado de maneira dinâmica ou estática. Ele é uma abstração de armazenamento físico (discos locais, volumes de rede, etc.), permitindo que o Kubernetes interaja com várias soluções de armazenamento de maneira uniforme.

Características do PV:

	•	Independência do ciclo de vida dos pods: PVs não estão diretamente ligados a um pod específico, ou seja, eles permanecem disponíveis mesmo que os pods que os utilizam sejam destruídos.
	•	Tipos de provisionamento:
	•	Estático: Administradores criam PVs manualmente e os disponibilizam para uso.
	•	Dinâmico: PVs são provisionados automaticamente quando um PVC correspondente é criado, caso haja suporte no provedor de armazenamento.

Persistent Volume Claim (PVC)

O Persistent Volume Claim (PVC) é uma solicitação de armazenamento feita por um pod. Ele define a quantidade de armazenamento e as características que o pod precisa, como tamanho e modo de acesso, e faz a ligação entre o pod e um PV disponível que atenda aos requisitos.

Características do PVC:

	•	Solicitação de armazenamento: O PVC é usado pelos pods para pedir uma quantidade específica de espaço e outros atributos, como modos de acesso (e.g., leitura/escrita, somente leitura).
	•	Ligação ao PV: O PVC busca por um PV que atenda às suas especificações. Quando um PV adequado é encontrado, ele é vinculado ao PVC e o pod pode usar o volume.

Modos de Acesso:

Os PVs e PVCs suportam diferentes modos de acesso, que definem como o volume pode ser montado nos pods:

	•	ReadWriteOnce (RWO): O volume pode ser montado para leitura e escrita por um único nó de cada vez.
	•	ReadOnlyMany (ROX): O volume pode ser montado como somente leitura por muitos nós simultaneamente.
	•	ReadWriteMany (RWX): O volume pode ser montado para leitura e escrita por muitos nós simultaneamente.

Exemplo de PV e PVC

Exemplo de Persistent Volume (PV):

apiVersion: v1
kind: PersistentVolume
metadata:
  name: example-pv
spec:
  capacity:
    storage: 10Gi
  accessModes:
    - ReadWriteOnce
  persistentVolumeReclaimPolicy: Retain
  hostPath:
    path: /mnt/data

Aqui:

	•	O PV oferece 10 GiB de armazenamento e suporta o modo de acesso ReadWriteOnce, ou seja, apenas um nó pode montá-lo por vez.
	•	O campo hostPath indica que o volume é fornecido a partir do diretório local /mnt/data no nó host.

Exemplo de Persistent Volume Claim (PVC):

apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: example-pvc
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 5Gi

Aqui:

	•	O PVC está solicitando 5 GiB de armazenamento com o modo de acesso ReadWriteOnce.
	•	O Kubernetes tentará encontrar um PV disponível que atenda a essa solicitação (neste caso, o example-pv acima seria compatível).

Funcionamento:

	1.	O administrador ou o sistema provisiona um PV.
	2.	Um pod faz uma solicitação de armazenamento criando um PVC.
	3.	O Kubernetes verifica se há um PV disponível que satisfaça os critérios definidos no PVC.
	4.	Se encontrar, o PV é associado ao PVC, e o pod pode acessar o armazenamento persistente.

Estratégias de Reclaim:

Quando o PVC deixa de usar o PV (por exemplo, se o PVC for deletado), o PV entra em um dos seguintes estados de reclaim:

	•	Retain: O PV é preservado com os dados ainda nele, mas não pode ser imediatamente reutilizado.
	•	Recycle: Os dados são apagados e o PV é reaproveitado.
	•	Delete: O PV e os dados associados são completamente removidos.

PV e PVC são essenciais para aplicações de estado em Kubernetes, como bancos de dados, garantindo que os dados possam sobreviver a reinicializações e movendo os pods em um cluster.