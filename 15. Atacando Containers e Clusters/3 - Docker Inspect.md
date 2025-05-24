# Docker Inspect

O comando docker inspect é uma ferramenta poderosa que permite ver todos os detalhes de um container, imagem, volume, rede, etc. Ele retorna os dados em formato JSON, e é muito útil tanto para debug quanto para reconhecimento em segurança ofensiva.

⸻

🔍 Sintaxe básica

docker inspect [OPTIONS] NOME|ID


⸻

✅ Exemplos práticos

🔧 Inspecionar um container:

docker inspect nginx

Retorna um JSON com informações detalhadas como IP, volumes, mounts, rede, comandos de inicialização, etc.

📦 Inspecionar uma imagem:

docker inspect nginx:latest

🌐 Inspecionar uma rede:

docker inspect bridge


⸻

🧠 Uso prático em segurança ofensiva

Durante enumeração e pós-exploração, docker inspect te ajuda a:
	•	Ver se o container está rodando com privileged mode:

docker inspect CONTAINER_ID | grep -i privileged


	•	Ver se há volumes montados do host (potencial para escape):

docker inspect CONTAINER_ID | jq '.[].Mounts'


	•	Ver o entrypoint e CMD do container (para entender o app):

docker inspect CONTAINER_ID | jq '.[].Config.Entrypoint'


	•	Ver as variáveis de ambiente:

docker inspect CONTAINER_ID | jq '.[].Config.Env'


	•	Obter o PID no host (útil para usar nsenter e escapar):

docker inspect -f '{{.State.Pid}}' CONTAINER_ID



⸻

🛠 Comando útil com jq (filtro JSON)

Se tiver jq instalado, pode filtrar melhor:

docker inspect CONTAINER_ID | jq '.[0].HostConfig.Privileged'