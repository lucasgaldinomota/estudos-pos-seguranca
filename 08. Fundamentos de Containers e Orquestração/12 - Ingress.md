# Ingress

O Ingress no Kubernetes é um recurso que gerencia o acesso externo aos serviços dentro de um cluster, geralmente HTTP e HTTPS, oferecendo regras que definem como o tráfego deve ser roteado. Diferente de um Service, que pode expor um serviço através de um IP externo (usando NodePort ou LoadBalancer), o Ingress permite controlar e consolidar o tráfego de múltiplos serviços sob um único ponto de entrada, como um domínio ou subdomínios.

Principais Conceitos do Ingress:

	1.	Ingress Resource: Um recurso no Kubernetes que define as regras de roteamento. Essas regras especificam:
	•	Host: O nome de domínio ou subdomínio para o qual o tráfego é direcionado.
	•	Path: Caminhos dentro do domínio para diferentes serviços (e.g., /api, /login).
	•	Backend: O serviço que deve receber o tráfego correspondente ao host e ao caminho.
	2.	Ingress Controller: Um componente dentro do cluster que implementa as regras definidas no Ingress Resource. Ele escuta essas definições e faz as mudanças necessárias no roteamento. Alguns exemplos populares de Ingress Controllers:
	•	NGINX Ingress Controller: Um dos mais usados e amplamente suportados.
	•	Traefik: Oferece suporte nativo ao Kubernetes e a outros recursos de rede.
	•	HAProxy: Um controlador que fornece balanceamento de carga altamente configurável.

Benefícios do Ingress:

	•	Roteamento HTTP/HTTPS: Permite criar regras de roteamento com base em URLs, caminhos e hosts.
	•	TLS/SSL: Suporte integrado para gerenciamento de certificados TLS/SSL, possibilitando a configuração de HTTPS.
	•	Consolidação do Ponto de Acesso: Diferentes serviços podem ser acessados através de um único endereço IP público, cada um mapeado para caminhos diferentes.
	•	Regras de Balanceamento de Carga: Roteia o tráfego para serviços baseados em condições, como host ou path, e pode ser usado junto com balanceadores de carga externos.

Exemplo de Ingress Resource YAML:

Aqui está um exemplo básico de um recurso Ingress que roteia o tráfego HTTP para dois serviços diferentes com base no caminho da URL:

apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: example-ingress
  annotations:
    nginx.ingress.kubernetes.io/rewrite-target: /
spec:
  rules:
  - host: example.com
    http:
      paths:
      - path: /service1
        pathType: Prefix
        backend:
          service:
            name: service1
            port:
              number: 80
      - path: /service2
        pathType: Prefix
        backend:
          service:
            name: service2
            port:
              number: 80

Neste exemplo:

	•	O tráfego para example.com/service1 será roteado para o service1.
	•	O tráfego para example.com/service2 será roteado para o service2.

Considerações:

	•	O Ingress Controller precisa ser instalado separadamente, já que o Kubernetes por padrão não inclui um.
	•	Para HTTPS, você deve configurar certificados TLS e definir as regras de roteamento usando TLS no Ingress Resource.

Ingress é essencial em ambientes de produção onde várias aplicações precisam ser expostas ao mundo externo, utilizando um gerenciamento centralizado para roteamento e segurança.