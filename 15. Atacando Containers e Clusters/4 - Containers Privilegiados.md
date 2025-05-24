# Containers Privilegiados

⚠️ O que é um Privileged Container?

Um container com a flag --privileged tem acesso total ao host, incluindo:
	•	Todos os dispositivos (/dev)
	•	Módulos de kernel
	•	Capabilities que normalmente são restritas (como SYS_ADMIN)
	•	Possibilidade de montar volumes do host
	•	Possibilidade de usar ferramentas como nsenter, chroot, mount

⸻

🧪 Como criar um container privilegiado

docker run --rm -it --privileged alpine sh

Isso inicia um container Alpine com acesso root e todos os privilégios do host.

⸻

🔍 Como identificar se um container é privilegiado

Com docker inspect:

docker inspect CONTAINER_ID | jq '.[].HostConfig.Privileged'

Se retornar true, o container está rodando com acesso total.

⸻

💥 Exemplo de ataque: Escapar para o host

Se o container for privilegiado e tiver / montado, você pode fazer isso:

docker run --rm -it --privileged -v /:/host alpine sh
chroot /host

Você agora está dentro do sistema de arquivos do host como root.

⸻

🔓 Outro ataque: usar nsenter para invadir o host
	1.	Pegue o PID de 1 do host (ex: via docker inspect)

docker inspect -f '{{.State.Pid}}' CONTAINER_ID

	2.	Use nsenter para entrar no namespace do host:

nsenter --target PID --mount --uts --ipc --net --pid

Agora você acessou o host via container. Isso simula um escape de container via permissões privilegiadas.

⸻

🛡️ Defesa (Blue Team)
	•	Nunca use --privileged em produção
	•	Use perfis AppArmor ou SELinux para limitar containers
	•	Evite montar /var/run/docker.sock ou volumes críticos
	•	Use namespaces e controle de capabilities (--cap-drop, --cap-add)