# Storage Classes

No Kubernetes, StorageClasses são um recurso que define “classes” de armazenamento para a criação dinâmica de volumes persistentes (PVs, Persistent Volumes). Elas permitem que os administradores de clusters definam diferentes níveis e tipos de armazenamento com base em desempenho, custo ou características específicas (como SSDs, HDDs, armazenamento em rede, etc.).

O objetivo principal de uma StorageClass é automatizar a criação de Persistent Volumes (PVs) a partir de Persistent Volume Claims (PVCs), garantindo que o armazenamento certo seja provisionado conforme a necessidade do usuário ou aplicação.

Principais Conceitos:

	1.	Provisão Dinâmica: Usando StorageClasses, o Kubernetes pode provisionar automaticamente um Persistent Volume (PV) com as características solicitadas por uma Persistent Volume Claim (PVC). Sem StorageClasses, os administradores precisam pré-provisionar os volumes manualmente.
	2.	Tipos de Armazenamento: Cada StorageClass pode definir um tipo de armazenamento diferente, como:
	•	SSD (armazenamento rápido, mas caro)
	•	HDD (armazenamento mais barato e mais lento)
	•	Armazenamento em rede (NFS, GlusterFS, Ceph, etc.)
	•	Armazenamento em nuvem (EBS na AWS, Persistent Disks no GCP, etc.)
	3.	Provisioners: Cada StorageClass utiliza um provisioner, que é um driver que define como os volumes persistentes serão criados. Exemplo de provisioners:
	•	Para AWS: kubernetes.io/aws-ebs
	•	Para Google Cloud: kubernetes.io/gce-pd
	•	Para Azure: kubernetes.io/azure-disk
	4.	Parâmetros Personalizados: As StorageClasses podem ser configuradas com parâmetros que ajustam as características do volume a ser provisionado, como o tipo de disco, políticas de replicação, etc.

Exemplo de StorageClass:

Aqui está um exemplo básico de uma StorageClass que provisiona volumes EBS no AWS:

apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: fast-ssd
provisioner: kubernetes.io/aws-ebs
parameters:
  type: gp2  # Tipo de disco EBS (gp2 = SSD)
  fsType: ext4  # Sistema de arquivos do volume

Componentes Importantes de uma StorageClass:

	•	provisioner: Define o provisionador de armazenamento (geralmente específico para o provedor de nuvem ou tipo de armazenamento) que será utilizado para criar o volume.
	•	parameters: Define os parâmetros específicos para o provisionamento do volume. Esses parâmetros variam de acordo com o provisionador. Exemplo: type para especificar o tipo de disco (SSD, HDD), fsType para o sistema de arquivos (ext4, xfs), etc.
	•	reclaimPolicy: Define o que acontece com o volume quando um PVC associado é excluído. As opções são:
	•	Retain: O volume é mantido, mesmo que o PVC seja deletado.
	•	Delete: O volume é excluído quando o PVC é excluído (comum para armazenamento de nuvem).
Exemplo:

reclaimPolicy: Delete


	•	allowVolumeExpansion: Permite que os volumes criados por essa StorageClass sejam expandidos após sua criação (se suportado pelo provisionador).
Exemplo:

allowVolumeExpansion: true



Uso de StorageClass com Persistent Volume Claims (PVCs)

Uma Persistent Volume Claim (PVC) pode solicitar armazenamento de uma StorageClass específica ao fazer referência ao seu nome. Se nenhuma StorageClass for especificada, o Kubernetes pode usar uma classe de armazenamento padrão, se estiver configurada.

Exemplo de PVC que usa uma StorageClass:

apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: my-storage-claim
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 10Gi
  storageClassName: fast-ssd

Neste exemplo, o PVC está solicitando um volume de 10 GB com a classe de armazenamento fast-ssd, que provisionará automaticamente o volume com base nas características definidas pela StorageClass.

StorageClass Padrão

Cada cluster Kubernetes pode ter uma StorageClass padrão. Se um PVC for criado sem especificar uma StorageClass, o Kubernetes usará essa classe padrão. Para marcar uma StorageClass como padrão, você pode usar a seguinte annotation:

metadata:
  annotations:
    storageclass.kubernetes.io/is-default-class: "true"

Exemplo de StorageClass para o Google Cloud Platform (GCP):

apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: standard
provisioner: kubernetes.io/gce-pd
parameters:
  type: pd-standard  # Tipo de disco padrão
  fsType: ext4  # Sistema de arquivos padrão

Exemplo de StorageClass para o Azure:

apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: azure-managed
provisioner: kubernetes.io/azure-disk
parameters:
  storageaccounttype: Premium_LRS  # Tipo de conta de armazenamento (Premium SSD)
  kind: Managed  # Usar discos gerenciados no Azure

Quando Usar StorageClasses:

	•	Armazenamento com características diferentes: Se seu cluster Kubernetes possui workloads que precisam de diferentes tipos de armazenamento, como SSDs rápidos para bancos de dados e HDDs mais baratos para backups ou logs.
	•	Provisionamento automático de volumes: Se você quiser evitar o provisionamento manual de volumes persistentes e preferir que isso aconteça de forma dinâmica.
	•	Armazenamento em nuvem: No contexto de provedores de nuvem, como AWS, GCP e Azure, StorageClasses são essenciais para integrar e gerenciar volumes de forma eficiente.

Vantagens de StorageClasses:

	1.	Automação: Provisão automática de volumes persistentes com base nas demandas das aplicações.
	2.	Flexibilidade: Suporte a diferentes tipos de armazenamento, tanto em nuvem quanto em sistemas locais.
	3.	Facilidade de Gerenciamento: O provisionamento dinâmico simplifica o gerenciamento de armazenamento, pois os administradores não precisam criar volumes manualmente.
	4.	Escalabilidade: Adequado para ambientes de produção onde o crescimento do armazenamento é dinâmico.

Conclusão:

As StorageClasses são essenciais no Kubernetes para lidar com o provisionamento dinâmico de armazenamento, permitindo que o cluster atenda automaticamente às necessidades de armazenamento de uma aplicação com base em diferentes níveis de desempenho, custo e características técnicas. Elas são particularmente úteis em ambientes de nuvem, onde o provisionamento e a escalabilidade automáticos são fundamentais para o desempenho e a eficiência operacional.