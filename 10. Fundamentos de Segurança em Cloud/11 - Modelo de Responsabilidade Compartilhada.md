# Modelo de Responsabilidade Compartilhada

O modelo de responsabilidade compartilhada é um princípio fundamental em serviços de computação em nuvem. Ele define claramente as responsabilidades de segurança entre o provedor de nuvem e o cliente, garantindo proteção e conformidade com os requisitos de segurança.

As responsabilidades variam dependendo do modelo de serviço adotado: IaaS (Infraestrutura como Serviço), PaaS (Plataforma como Serviço) ou SaaS (Software como Serviço).

Estrutura do Modelo de Responsabilidade Compartilhada

1. Responsabilidades do Provedor de Nuvem
	•	Segurança da Nuvem: Refere-se à infraestrutura subjacente, incluindo hardware, rede, armazenamento e data centers.
	•	Principais atribuições:
	•	Gerenciar hardware físico, como servidores e sistemas de rede.
	•	Garantir a disponibilidade e resiliência dos serviços.
	•	Proteger contra ameaças físicas e cibernéticas no nível da infraestrutura.
	•	Oferecer ferramentas de segurança para o cliente, como criptografia e autenticação multifator.

2. Responsabilidades do Cliente
	•	Segurança na Nuvem: Refere-se à proteção dos dados, configurações, aplicativos e controles dentro do ambiente fornecido.
	•	Principais atribuições:
	•	Configuração segura de recursos e permissões de acesso.
	•	Gerenciamento de identidade e controle de acesso (IAM).
	•	Proteção de dados, incluindo criptografia e backup.
	•	Implementação de controles adicionais, como firewalls e antivírus, quando necessário.

Responsabilidades por Modelo de Serviço

Modelo	Provedor de Nuvem (Segurança da Nuvem)	Cliente (Segurança na Nuvem)
IaaS (Infraestrutura como Serviço)	Hardware, rede, data centers e hipervisores.	Sistemas operacionais, aplicativos, dados, configurações de rede e políticas de acesso.
PaaS (Plataforma como Serviço)	Infraestrutura, sistema operacional e middleware.	Configuração de aplicativos, dados, gerenciamento de identidade e acesso.
SaaS (Software como Serviço)	Toda a infraestrutura, sistema operacional, aplicativos e interfaces do software.	Configuração de permissões, gerenciamento de identidade e segurança dos dados inseridos.

Exemplo Prático

IaaS (Ex.: Amazon EC2, Google Compute Engine)
	•	Provedor: Mantém os servidores físicos, armazenamento e rede.
	•	Cliente: Configura o sistema operacional, instala patches de segurança e define regras de firewall.

PaaS (Ex.: Google App Engine, Microsoft Azure App Service)
	•	Provedor: Gerencia a infraestrutura e o sistema operacional.
	•	Cliente: Desenvolve e protege os aplicativos implantados.

SaaS (Ex.: Microsoft 365, Google Workspace)
	•	Provedor: Oferece o software pronto para uso, cuidando de infraestrutura e manutenção.
	•	Cliente: Gerencia permissões de usuário e protege dados confidenciais dentro do sistema.

Benefícios do Modelo de Responsabilidade Compartilhada
	1.	Clareza de responsabilidades:
	•	Evita ambiguidades sobre quem é responsável por qual parte da segurança.
	2.	Redução de riscos:
	•	Provedores cuidam da infraestrutura, permitindo que os clientes se concentrem em proteger seus dados e aplicativos.
	3.	Conformidade:
	•	Garante alinhamento com regulamentações, como LGPD e GDPR, ao definir papéis específicos.
	4.	Escalabilidade:
	•	O modelo é flexível e se adapta ao tipo de serviço contratado.

Riscos e Desafios
	1.	Configuração inadequada:
	•	Erros no lado do cliente, como permissões mal configuradas, podem levar a falhas de segurança.
	2.	Falta de conscientização:
	•	Clientes podem assumir que o provedor cuida de tudo, deixando brechas de segurança.
	3.	Gerenciamento de identidade:
	•	Contas comprometidas podem expor dados sensíveis, especialmente em ambientes SaaS.

Melhores Práticas no Modelo de Responsabilidade Compartilhada
	1.	Entenda suas responsabilidades:
	•	Revise o contrato com o provedor para saber o que está sob sua responsabilidade.
	2.	Use ferramentas fornecidas pelo provedor:
	•	Ative recursos como IAM, criptografia e monitoramento de segurança.
	3.	Implemente controles adicionais:
	•	Inclua soluções como firewalls, ferramentas de detecção de ameaças e backups regulares.
	4.	Treine sua equipe:
	•	Capacite colaboradores para gerenciar configurações e seguir boas práticas de segurança.
	5.	Realize auditorias regulares:
	•	Monitore o ambiente e revise políticas de acesso periodicamente.