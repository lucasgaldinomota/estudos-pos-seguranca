# Distroless

O que é Distroless?

Distroless é um tipo de imagem Docker minimalista que não contém um sistema operacional completo, apenas os arquivos essenciais para executar uma aplicação. Ela remove pacotes desnecessários como shells (bash), gerenciadores de pacotes (apt, yum) e ferramentas de depuração, reduzindo a superfície de ataque e melhorando a segurança.

🔹 Menos dependências = menos vulnerabilidades.
🔹 Imagens menores = menos tempo de build e deploy.
🔹 Sem shell = mais difícil para atacantes explorarem a imagem.

⸻

1️⃣ Como Usar Imagens Distroless?

O Google mantém imagens Distroless para várias linguagens, como Go, Java, Node.js e Python. Você pode encontrá-las no repositório oficial:
👉 gcr.io/distroless

Exemplo: Usando Distroless com Node.js

FROM node:20 AS builder
WORKDIR /app
COPY . .
RUN npm install && npm run build

FROM gcr.io/distroless/nodejs:20
WORKDIR /app
COPY --from=builder /app .
CMD ["server.js"]

✅ Vantagens:
	•	A imagem final não contém npm, bash ou apt.
	•	A aplicação roda apenas com Node.js, reduzindo riscos.

⸻

2️⃣ Exemplos para Outras Linguagens

Distroless com Go

FROM golang:1.21 AS builder
WORKDIR /app
COPY . .
RUN go build -o app

FROM gcr.io/distroless/static
WORKDIR /app
COPY --from=builder /app/app .
CMD ["/app/app"]

🔹 A imagem final não contém libc, bash ou glibc, apenas o binário Go puro.

Distroless com Python

FROM python:3.11 AS builder
WORKDIR /app
COPY . .
RUN pip install -r requirements.txt

FROM gcr.io/distroless/python3
WORKDIR /app
COPY --from=builder /app .
CMD ["app.py"]

🔹 Sem pip, sem pacotes extras! Apenas Python e a aplicação.

⸻

3️⃣ Tipos de Imagens Distroless

O Google oferece diferentes tipos de imagens Distroless, dependendo da necessidade:

Imagem	Descrição
gcr.io/distroless/base	Imagem mínima com glibc e NSS.
gcr.io/distroless/static	Imagem super leve, sem glibc.
gcr.io/distroless/nodejs	Para rodar aplicações Node.js.
gcr.io/distroless/python3	Para rodar aplicações Python.
gcr.io/distroless/java17	Para rodar aplicações Java 17.

Se sua aplicação é um binário estático (como Go compilado com CGO_ENABLED=0), use distroless/static para ter a menor imagem possível! 🚀

⸻

4️⃣ Comparação: Distroless vs Outras Imagens

Base	Tamanho	Segurança	Shell / Pacotes Extras
ubuntu:latest	80MB+	🔴 Alta superfície de ataque	✅ Sim (bash, apt, curl)
alpine:latest	5MB	🟡 Pequena, mas tem apk	✅ Sim (sh, apk)
distroless/base	10MB	🟢 Muito segura	❌ Não (sem bash, sem apt)
distroless/static	~2MB	🟢 Extremamente segura	❌ Não

📌 Distroless é menor que Ubuntu e mais segura que Alpine, pois não contém pacotes desnecessários.

⸻

5️⃣ Segurança no Distroless

🔐 Por que Distroless é mais seguro?
	•	Sem shell (bash, sh) → Atacantes não conseguem abrir um terminal.
	•	Sem apt, yum, apk → Não dá para instalar ferramentas maliciosas.
	•	Menos pacotes → Menos CVEs e menos atualizações necessárias.
	•	Tamanho reduzido → Menos código = menos chances de bugs e falhas.

Como Debugar uma Imagem Distroless?

Como Distroless não tem shell, você não pode rodar bash dentro do container.
Se precisar debugar:

docker run --rm -it --entrypoint=sh gcr.io/distroless/base

Ou rode um shell temporário:

docker run --rm -it --entrypoint=/bin/sh busybox

Assim, você pode inspecionar arquivos e processos.

⸻

6️⃣ Conclusão

✔ Distroless melhora segurança, performance e reduz tamanho de imagens.
✔ Ideal para produção, onde containers devem ser imutáveis e mínimos.
✔ Funciona melhor para apps compilados (Go, Java, Node.js, Python).
✔ Não é ideal para desenvolvimento, pois não tem ferramentas de debug.

Se precisar de mais detalhes ou exemplos, me avise! 🚀