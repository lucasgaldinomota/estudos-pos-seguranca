# / # docker run --rm -it -v /:/mnt/acesso alpine:latest chroot /mnt/acesso bash

📌 Explicação Detalhada

Comando/flag			Significado
docker run	    		Inicia um novo container
--rm					Remove o container ao sair
-it						Modo interativo com terminal TTY
-v /:/mnt/acesso		Monta o diretório raiz do host dentro do container em /mnt/acesso
alpine:latest			Usa a imagem Alpine
chroot /mnt/acesso		Muda o root do container para o root do host montado
bash					Tenta iniciar uma shell bash (não existe no Alpine, normalmente)

⸻

⚠️ Observação importante

O Alpine não vem com bash por padrão, só com sh. Isso causará erro:

chroot: can't execute 'bash': No such file or directory

✅ Correto seria:

docker run --rm -it -v /:/mnt/acesso alpine:latest chroot /mnt/acesso sh


⸻

💣 O que isso permite?
	•	Você está executando um shell diretamente dentro do host (não no container).
	•	A partir daí, tem acesso root irrestrito ao sistema do host.
	•	Isso é equivalente a um escape de container completo.

⸻

🛡️ Riscos e Defesas

Riscos:
	•	Controle total do host a partir de dentro de um container
	•	Leitura e modificação de arquivos do host
	•	Criação de usuários, backdoors e rootkits

Defesas:
	•	Nunca monte / no container
	•	Use AppArmor/SELinux para isolar containers
	•	Use rootless Docker se possível
	•	Restringir docker.sock e docker group (qualquer usuário que pode rodar docker tem root)

⸻

📄 Arquivo Markdown

Aqui está o conteúdo em formato .md para salvar e estudar:

⸻


# ⚠️ Análise de Segurança: Docker + chroot com Volume do Host

## 🧪 Comando Executado

```bash
docker run --rm -it -v /:/mnt/acesso alpine:latest chroot /mnt/acesso bash

⚠️ Corrigido para Alpine:

docker run --rm -it -v /:/mnt/acesso alpine:latest chroot /mnt/acesso sh


⸻

🔍 Explicação

Parte					Descrição
--rm					Remove o container ao encerrar
-it						Modo interativo
-v /:/mnt/acesso		Monta o sistema de arquivos do host dentro do container
chroot /mnt/acesso		Redefine a raiz do sistema para o host montado
sh						Inicia um shell com a nova raiz


⸻

💣 Efeito prático
	•	Você está operando como root no host
	•	Pode ler, editar, apagar qualquer arquivo do host
	•	Pode instalar backdoors, modificar sistema, etc.

⸻

🔐 Defesa
	•	Nunca monte / no container
	•	Evite dar acesso Docker para usuários não confiáveis
	•	Use perfis de segurança (AppArmor, Seccomp, SELinux)
	•	Prefira Docker rootless para ambientes multiusuário
	•	Monitore containers com ferramentas como Falco, Osquery, etc.

⸻

📌 Conclusão

Esse tipo de comando demonstra como containers mal configurados podem ser usados para comprometer o host.
Use esse conhecimento com responsabilidade e apenas em laboratórios controlados.
