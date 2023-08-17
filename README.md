# Mineração OilyGiant

## Visão geral do projeto
Tarefa é encontrar os melhores lugares para o desenvolvimento de novos poços de petróleo para a empresa de mineração OilyGiant.
Para concluir essa tarefa, executei as seguintes etapas:
-	Ler os arquivos com parâmetros coletados de poços de petróleo na região selecionada: a quantidade de petróleo e o volume de reservas;
-	Construir um modelo para predizer o volume de reservas em novos poços;
-	Escolher os poços de petróleo que têm os maiores valores estimados;
-	Escolher a região com o maior lucro total para os poços de petróleo selecionados.

Temos dados sobre amostras de petróleo de três regiões. Os parâmetros de cada poço de petróleo na região já são conhecidos. Construi um modelo que ajudará a escolher a região com a margem de lucro mais alta. Utilizei a técnica de Bootstrapping para analisar lucro potencial e riscos.

## Descrição de dados
Os dados de exploração geológica para as três regiões estão armazenados em arquivos:
-	geo_data_0.csv. baixe o conjunto de dados
-	geo_data_1.csv. baixe o conjunto de dados
-	geo_data_2.csv. baixe o conjunto de dados
-	id — identificador unívoco de poço de petróleo
-	f0, f1, f2 — três características de pontos (seu significado específico não é importante, mas as próprias características são significativas)
-	product — volume de reservas no poço de petróleo (milhares de barris).

### Condições:
-	Apenas regressão linear pode ser usada para o treinamento do modelo.
-	Ao explorar a região, um estudo de 500 pontos é realizado e os melhores 200 pontos são selecionados para calcular o lucro.
-	O orçamento para o desenvolvimento de 200 poços de petróleo é 100 milhões de dólares.
-	Um barril de petróleo bruto traz 4.5 dólares de receita. A receita de uma unidade de produto é 4.500 dólares (o volume de reservas está em milhares de barris).
-	Depois de ter avaliado os riscos, mantenha apenas as regiões com o risco de perdas inferior a 2.5%. Entre aquelas que se enquadram no critério, você precisa selecionar a região com o lucro médio mais alto.

Os dados são sintéticos e não incluem nenhum detalhe de contratos ou características de poços.

## Instruções do projeto
1.	Baixei e preparei os dados. 
2.	Treinei e testei o modelo para cada região em geo_data_0.csv:
-	Dividi os dados em um conjunto de treinamento e um conjunto de validação em uma proporção de 75:25.
-	Treinei o modelo e fiz predições para o conjunto de validação.
-	Salvei as predições e respostas corretas no conjunto de validação.
-	Imprimi o volume médio previsto de reservas e o REQM do modelo.
-	Analisei os resultados.
-	Coloquei todos os passos anteriores em funções, executei os passos 2.1 a 2.5 nos arquivos 'geo_data_1.csv' e 'geo_data_2.csv'.

3.	Prepare-se para o cálculo de lucro:
-	Armazenei todos os valores necessários para os cálculos em variáveis separadas.
-	Dado o investimento de 100 milhões para 200 poços de petróleo, cada um precisa produzir, em média, uma quantidade de unidades equivalente a pelo menos 500 mil dólares para evitar prejuízos (isso é aproximadamente 111,1 unidades). Comparei essa quantidade com o volume médio de cada região.
- Forneci conclusões sobre a etapa de preparação para o cálculo de lucro.

4.	Escrevi uma função para calcular lucro de um conjunto de poços de petróleo selecionados e predições do modelo:
-	Escolhi os 200 poços com os valores mais altos previstos de cada uma das 3 regiões (ou seja, arquivos 'csv').
-	Sumarizei o volume alvo de reservas de acordo com essas predições. Armazenei as predições para os 200 poços para cada uma das 3 regiões.
-	Calculei o lucro potencial dos 200 melhores poços por região. Apresentei suas conclusões: sugeri uma região para o desenvolvimento de poços de petróleo e justifiquei sua escolha.

5.	Calculei riscos e lucro para cada região:
-	Usando as predições que armazenei na etapa 4.2, usei a técnica de bootstrapping com 1.000 amostras para encontrar a distribuição de lucros.
-	Encontrei lucro médio, intervalo de confiança de 95% e o risco de prejuízo. Prejuízo é um lucro negativo, calculei-o como uma probabilidade e depois o expressei como uma porcentagem.

