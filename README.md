# CP1 — Análise de Dados de Energia

Trabalho da disciplina **Soluções em Energias Renováveis e Sustentáveis**
(Ciência da Computação). O repositório tem dois notebooks feitos no Google Colab e
uma pasta `arquivos/` com as amostras `.csv` usadas no primeiro notebook.

## Integrantes

| Nome | RM |
|---|---|
| Luan de Araujo Carneiro | 573691 |
| Pedro Sampaio Mochnacs Arruda | 573522 |
| Raul Sampaio Mochnacs Arruda | 573523 |
| Pedro Ribeiro Lopes | 570083 |
| Kevin Rodrigues de Melo | 571777 |
| Pedro Vianna | 570747 |

## Como foi feito

Os dados vêm de bases públicas de energia (UCI e Kaggle). Cada amostra foi antes
tratada no **Orange Data Mining** — lá foram selecionadas só as colunas de
interesse e aplicado um *Data Sampler* para reduzir o volume — e depois a análise
propriamente dita foi feita em **Python com Pandas** dentro do notebook.

Os dois notebooks rodam no Colab. Basta abrir pelo botão *"Open in Colab"* no topo
de cada arquivo e subir os `.csv` da pasta `arquivos/` para a sessão (`/content/`)
antes de executar as células. O `Desafio_Final` também precisa de internet, porque
consulta uma API pública.

## `CP1_ori.ipynb`

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/pedrosampaiom2007-gif/cp1-Andre/blob/main/CP1_ori.ipynb)

São seis exercícios, todos seguindo a mesma ideia: carregar a amostra, olhar a
estrutura (`shape`, `head`, `info`, `describe`), renomear as colunas para nomes
mais claros, definir um limiar como uma porcentagem do valor máximo de uma
variável (70% na maioria dos casos, 75% nos exercícios 2 e 6), separar os
registros que ficam acima desse limiar e calcular quantos são e que percentual
representam. Depois entra um segundo critério — quase sempre uma condição
ambiental ou operacional — e compara-se o novo recorte com o recorte que só
considerava o consumo alto.

Os datasets usados, na ordem dos exercícios:

1. Appliances Energy Prediction (UCI) — consumo de eletrodomésticos de uma
   residência, cruzado com temperatura.
2. Steel Industry Energy Consumption (UCI) — consumo de uma siderúrgica, cruzado
   com o fator de potência.
3. Power Consumption of Tetouan City (UCI) — consumo em três zonas da cidade;
   escolhe-se a zona de maior pico e cruza-se com a temperatura ambiente.
4. Solar Power Generation Data (Kaggle) — geração de uma usina fotovoltaica;
   olha-se a potência CA e a frequência de cada inversor nos momentos de alta
   geração.
5. Wind & Solar Energy Production (Kaggle) — produção renovável hora a hora;
   solar e eólica são comparadas, cada uma contra o seu próprio máximo.
6. Individual Household Electric Power Consumption (UCI) — monitoramento elétrico
   de uma casa; potência ativa alta cruzada com corrente acima da média.

## `Desafio_Final_Energia_ONS_API_Final.ipynb`

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/pedrosampaiom2007-gif/cp1-Andre/blob/main/Desafio_Final_Energia_ONS_API_Final.ipynb)

Análise da carga elétrica do Sistema Interligado Nacional a partir da API pública
de Carga Verificada do **ONS** (`apicarga.ons.org.br`). Foi usada a área **SP**,
no período de **01 a 07/08/2025** — 336 medições de meia em meia hora.

O notebook está organizado em desafios numerados:

- **Desafios 1 e 2** — montar o DataFrame a partir do JSON da API, renomear as
  colunas principais, checar valores ausentes e tipos.
- **Desafio 3** — indicadores da carga: mínimo, máximo, média, mediana, amplitude
  e número de medições.
- **Desafio 4** — períodos de alta demanda, definidos como carga acima de 90% do
  máximo (50 registros, ~15% do período).
- **Desafio 5** — um segundo recorte escolhido pela equipe: carga abaixo da média
  (152 registros, ~45% do período), comparado com o recorte de alta demanda.
- **Desafio 6** — dois gráficos com interpretação: a série temporal da carga na
  semana, com o limiar de alta demanda em destaque, e o histograma da
  distribuição da carga, com média e mediana marcadas.
- **Desafio 7** — a variável `resumo_resultados` reúne num único texto os
  indicadores dos desafios anteriores (região, período, nº de registros, mínimo,
  máximo, média, mediana, limiar e percentual de alta demanda, momento do pico e
  o resultado do segundo critério), pronta para o relatório.

Todos os desafios obrigatórios (1 a 7) estão resolvidos no notebook.

