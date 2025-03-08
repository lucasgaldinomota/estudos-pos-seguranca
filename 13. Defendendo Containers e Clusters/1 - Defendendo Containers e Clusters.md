# Defendendo Containers e Clusters

A segurança de containers e clusters é essencial para proteger aplicações em ambientes modernos baseados em microsserviços. Aqui estão algumas estratégias e melhores práticas para fortalecer a segurança:

⸻

1. Proteção na Construção da Imagem

Escolha de Imagens Seguras
	•	Use imagens oficiais e de fontes confiáveis (Docker Hub, Red Hat, etc.).
	•	Prefira imagens minimalistas (Alpine Linux, Distroless) para reduzir a superfície de ataque.

Scan de Vulnerabilidades
	•	Utilize scanners como:
	•	Trivy (Aqua Security)
	•	Anchore
	•	Clair (Red Hat)
	•	Grype (Syft)
	•	Automatize os scans no CI/CD.

Redução de Permissões
	•	Execute processos como usuário não root (USER no Dockerfile).
	•	Evite capabilities desnecessárias no kernel.

Imutabilidade e Assinatura de Imagens
	•	Assine e verifique imagens com:
	•	Cosign (parte do projeto Sigstore)
	•	Notary (Docker Content Trust)
	•	Armazene imagens em registries privados e configure políticas de acesso restrito.

⸻

2. Segurança na Execução de Containers

Privilégios e Isolamento
	•	Evite usar --privileged e conceder acesso ao host.
	•	Utilize seccomp, AppArmor ou SELinux para restringir chamadas de sistema.

Restrição de Recursos
	•	Defina limites de CPU e memória para evitar consumo excessivo.
	•	Use cgroups e namespaces para isolar containers.

Rede Segura
	•	Desative networking desnecessário (network=none para containers isolados).
	•	Utilize firewalls como iptables e Cilium para restringir comunicação.
	•	Prefira ingress controllers e proxies seguros (NGINX, Traefik, Envoy).

⸻

3. Proteção no Kubernetes

Controle de Acesso e RBAC
	•	Ative RBAC (Role-Based Access Control) e conceda privilégios mínimos.
	•	Evite cluster-admin para usuários e workloads.
	•	Use Service Accounts separadas para cada aplicação.

Políticas de Segurança
	•	Ative o Pod Security Admission (PSA) no Kubernetes.
	•	Utilize ferramentas como:
	•	Kyverno ou OPA/Gatekeeper para enforce de políticas.
	•	Falco para monitoramento de eventos suspeitos.

Segurança na Comunicação
	•	Ative TLS em serviços internos e use mTLS com service meshes (Istio, Linkerd).
	•	Configure NetworkPolicies para restringir tráfego entre pods.

⸻

4. Monitoramento e Resposta a Incidentes

Logging e Observabilidade
	•	Utilize ferramentas como:
	•	Prometheus + Grafana para métricas.
	•	Fluentd / Loki / ELK Stack para logs centralizados.

Detecção de Anomalias
	•	Falco para monitoramento de segurança em tempo real.
	•	Sysdig Secure ou Tetragon para detecção de ameaças.

Auditoria e Compliance
	•	Habilite audit logs no Kubernetes (auditPolicy.yaml).
	•	Utilize kube-bench para validar conformidade com CIS Benchmarks.

⸻

5. Atualizações e Backup
	•	Mantenha Kubernetes e Docker sempre atualizados.
	•	Use rolling updates para minimizar downtime e evitar exploração de CVEs.
	•	Faça backup regular de volumes persistentes e dos manifests do cluster.

⸻

Ferramentas Úteis

✅ Segurança de Imagens: Trivy, Clair, Grype
✅ Políticas de Segurança: OPA/Gatekeeper, Kyverno
✅ Monitoramento: Falco, Sysdig Secure, Prometheus
✅ Conformidade: kube-bench, kube-hunter

Essas práticas ajudam a mitigar riscos e fortalecer a segurança de containers e clusters. Tem algo específico que você quer explorar mais a fundo? 🚀