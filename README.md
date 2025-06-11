## Spotify Insights: EDA + Clustering + ML

Meu objetivo neste projeto foi entender padrões de músicas e obter insights sobre as faixas que compõem as melhores posições do ranking.
Além disso, também classifiquei as músicas por meio de clusters para identificar padrões com base no número de streams.
Por fim, criei um modelo com regressão logística para verificar se seria possível prever se uma música teria ou não sucesso nos rankings.

base: https://www.kaggle.com/datasets/edumucelli/spotifys-worldwide-daily-song-ranking/data

A base é composta por rankings globais coletados diariamente durante o ano de 2017.

## Métodos Utilizados

##1. EDA

* **Visualizações com `ggplot2`**: Utilizadas para identificar tendências de distribuição de `Streams`, posições (`Position`) e frequência por artistas.
* **Análise temporal**: Observamos a evolução das faixas ao longo do tempo para identificar padrões e sazonalidades.
* **Ranking por artistas**: Identificação dos artistas mais recorrentes no top 100.
* **Análise de correlação**: Explorei a relação entre número de streams e posição no ranking, mostrando forte correlação negativa (quanto maior o número de streams, melhor a posição).

---

##2. Clusterização

Foi realizada a técnica de **K-Means Clustering** com base nas variáveis **Position** e **Streams**, a fim de segmentar as músicas em grupos com comportamentos similares.

* **Normalização**: Os dados foram padronizados para evitar viés devido à escala.
* **Elbow Method**: Utilizado para identificar o número ideal de clusters (sugerindo 3 ou 4).
* **Clusters interpretados** como:

  * Cluster 1: Músicas com poucos streams e baixa posição.
  * Cluster 2: Faixas medianas em performance.
  * Cluster 3: Faixas de altíssimo desempenho, geralmente nas primeiras posições e com alto número de reproduções.

---

## 3.Machine Learning

Utilizou-se **Regressão Logística** para prever se uma música tem chance de ser considerada um **"sucesso"** com base no número de **Streams**:

* **Definição de variável resposta (`Sucesso`)**: Criada a partir de um critério (por exemplo, estar entre as 100 primeiras posições).
* **Divisão dos dados em treino e teste (80/20)**.
* **Modelo de regressão logística binária**:

  * Modelo treinado com `Streams` como variável explicativa.
  * Acurácia e desempenho avaliados via **matriz de confusão** e **AUC**.
  * Resultado: **AUC ≈ 0.70**, indicando desempenho aceitável para prever se uma música será ou não um sucesso com base apenas na quantidade de streams.
 
##Conclusões Finais

1. A maioria das músicas do Top 100 compartilha características similares, o que explica a formação de poucos clusters representativos.

2. É possível prever com aceitável grau de confiança se uma música tem potencial de sucesso, mas o sucesso extremo ainda depende de fatores exógenos (marketing, artista, contexto cultural).

3. O modelo de regressão pode ser uma boa base para sistemas de recomendação ou scouting musical, auxiliando gravadoras e produtores na curadoria de novos talentos.

4. A clusterização pode servir para segmentar músicas por perfil sonoro, facilitando estratégias de playlisting ou campanhas direcionadas por estilo.

5. O mercado de falantes da língua espanhola é extremamente bem sucedido, ocupando diversas posições dentro do top 100. Indicativo forte influência da música latina no cenário global.

6. Para uma análise mais aprofundada, outras variáveis se fazem necessárias. De modo a deixar a previsão de sucesso simplória.

