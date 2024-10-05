# Cron Job

Cron jobs são tarefas agendadas para serem executadas automaticamente em intervalos específicos no sistema Linux, controladas pelo daemon cron. Eles são definidos em arquivos chamados crontabs e podem ser usados para realizar diversas operações, como backups, limpezas de logs, execução de scripts, entre outras.

Estrutura do Cron Job

A estrutura básica de um cron job segue este formato:

* * * * * comando-a-executar

Cada asterisco corresponde a uma unidade de tempo e define quando o comando deve ser executado. Os campos são:

	•	1º campo (Minuto): 0-59 — o minuto específico em que o trabalho será executado.
	•	2º campo (Hora): 0-23 — a hora específica.
	•	3º campo (Dia do mês): 1-31 — o dia do mês (1 a 31).
	•	4º campo (Mês): 1-12 — o mês (1 a 12, ou abreviaturas como “jan”, “feb”).
	•	5º campo (Dia da semana): 0-7 — o dia da semana (0 ou 7 é domingo; ou nomes como “mon”, “tue”).

Exemplos de Cron Jobs

	1.	Executar um script todos os dias às 2h30 da manhã:

30 2 * * * /home/user/backup.sh


	2.	Executar um comando toda segunda-feira às 8h:

0 8 * * 1 /usr/bin/relatorio.sh


	3.	Rodar uma tarefa a cada 15 minutos:

*/15 * * * * /home/user/verifica_status.sh


	4.	Executar um script no primeiro dia de cada mês às 3h:

0 3 1 * * /home/user/mensal.sh


	5.	Rodar um comando todos os domingos às 23h59:

59 23 * * 0 /usr/local/bin/relatorio_semanal.sh



Como Usar o Crontab

Para agendar um cron job, você precisa editar o arquivo crontab. Cada usuário no Linux pode ter seu próprio crontab.

	1.	Editar o crontab do usuário:
	•	Use o comando abaixo para abrir o arquivo crontab do usuário atual:

crontab -e


	2.	Verificar os cron jobs configurados:
	•	Para ver os cron jobs configurados para o usuário atual:

crontab -l


	3.	Remover um cron job:
	•	Para remover todos os cron jobs do usuário:

crontab -r



Operadores Especiais no Crontab

	1.	@reboot: Executa o comando uma vez no início do sistema.
	•	Exemplo:

@reboot /home/user/script_inicializacao.sh


	2.	@daily (ou @midnight): Executa o comando uma vez por dia, à meia-noite.
	•	Exemplo:

@daily /home/user/limpeza_diaria.sh


	3.	@hourly: Executa uma vez por hora.
	•	Exemplo:

@hourly /home/user/verifica_disco.sh


	4.	@weekly: Executa uma vez por semana.
	•	Exemplo:

@weekly /home/user/relatorio_semanal.sh


	5.	@monthly: Executa uma vez por mês.
	•	Exemplo:

@monthly /home/user/mensal.sh



Redirecionamento de Saída de Cron Jobs

Se não for especificado, o cron envia a saída dos jobs por e-mail ao usuário. Para evitar isso ou redirecionar a saída para um arquivo de log, você pode usar o redirecionamento:

	•	Redirecionar saída para um arquivo:

0 3 * * * /home/user/script.sh >> /var/log/script.log 2>&1

Aqui, >> adiciona a saída ao arquivo script.log, e 2>&1 redireciona os erros para o mesmo arquivo.

Os cron jobs são uma maneira eficaz de automatizar tarefas em sistemas Linux, garantindo que processos rotineiros sejam executados sem a necessidade de intervenção manual.