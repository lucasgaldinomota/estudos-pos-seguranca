# Escalabilidade Vertical

A escalabilidade vertical (também conhecida como scale-up) é uma abordagem para aumentar a capacidade de um sistema adicionando mais recursos a um único servidor ou máquina, em vez de adicionar mais servidores ou máquinas ao sistema.

Como funciona a escalabilidade vertical?

Na escalabilidade vertical, os recursos de hardware de uma máquina existente são aumentados para atender a uma maior demanda. Isso pode ser feito por meio de:
	•	Aumento de memória (RAM).
	•	Substituição da CPU por uma mais potente.
	•	Adição de mais armazenamento (HDs ou SSDs).
	•	Melhoria de componentes de rede, como placas de rede mais rápidas.

Exemplo prático
	•	Antes da escalabilidade vertical: Um servidor possui 8 GB de RAM, 4 núcleos de CPU e 1 TB de armazenamento.
	•	Após a escalabilidade vertical: O mesmo servidor é atualizado para 32 GB de RAM, 16 núcleos de CPU e 5 TB de armazenamento.

Vantagens da escalabilidade vertical
	1.	Simplicidade:
	•	Mais fácil de implementar, pois não envolve alterações significativas na arquitetura do sistema.
	•	Reduz a complexidade de gerenciar múltiplos servidores.
	2.	Uso otimizado de recursos:
	•	Pode ser mais eficiente, pois evita o overhead de coordenação entre várias máquinas (como ocorre na escalabilidade horizontal).
	3.	Compatibilidade:
	•	Ideal para aplicações que não foram projetadas para rodar em múltiplos servidores ou sistemas distribuídos.

Desvantagens da escalabilidade vertical
	1.	Limites físicos:
	•	A capacidade de escalar é limitada pelas especificações máximas do hardware disponível.
	2.	Maior custo por unidade:
	•	Componentes de hardware de alta capacidade são mais caros.
	•	Pode ser mais caro do que adicionar várias máquinas menores.
	3.	Risco de ponto único de falha (SPOF):
	•	Se o servidor único falhar, toda a aplicação pode ser afetada.
	4.	Tempo de inatividade:
	•	Atualizações podem exigir que o sistema fique temporariamente offline.

Comparação: Escalabilidade Vertical x Escalabilidade Horizontal

Aspecto	Escalabilidade Vertical	Escalabilidade Horizontal
Estratégia	Adicionar recursos ao mesmo servidor	Adicionar mais servidores ao sistema
Complexidade	Menor	Maior (requer balanceamento de carga)
Custo inicial	Geralmente maior	Geralmente menor por unidade
Limite de crescimento	Restrito ao hardware disponível	Virtualmente ilimitado
Resiliência	Baixa (SPOF)	Alta (sem ponto único de falha)

Quando usar escalabilidade vertical?
	•	Aplicações legadas que não suportam múltiplos servidores.
	•	Sistemas com baixa complexidade e demandas previsíveis.
	•	Quando os custos de reestruturação de arquitetura (para escalabilidade horizontal) são proibitivos.