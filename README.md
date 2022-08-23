# Prevendo um Hit da Billboard


*A Billboard Hot 100 é o gráfico padrão da indústria da música nos Estados Unidos, publicado
semanalmente pela revista Billboard

1. Introdução

Neste projeto tentei resolver um problema de Hit Song Science, tema em debate e pesquisa entre a comunidade de Music Information Retrieval (MIR), que visa
prever quais músicas estarão no “topo das paradas”. Estudos demonstram que a utilização de técnicas de Machine Learning podem capturar informações de sinais de áudio e letras que poderiam explicar sua popularidade. A previsão de sucesso é especialmente útil para músicos, gravadoras e distribuidores de música, que podem optar por investir recursos limitados (campanhas publicitárias, equipamento de estúdio, etc.) em faixas que provavelmente se tornarão populares.

2. Análise Exploratória

2.1 Base de dados

Foi utilizada uma base de dados do Kaggle “The Spotify Hit Predictor Dataset”. A base de dados apresenta características das músicas obtidas através da API do Spotify. Outra base de dados foi obtida através do API da Billboard contendo os TOP 100 Hits do mesmo período. Por fim, os dados foram relacionados e as faixas rotuladas como '1' ou '0' ('Hit' ou 'Não Hit). A base de dados resultante pode ser utilizada para criar um modelo de classificação que prevê se uma música será um 'Hit' ou não. Para o projeto trabalhei apenas com músicas da última década totalizando 6398 registros, 19 colunas, sendo 18 atributos mais a coluna da classe (target) Foi verificado que a base de dados está balanceada contendo 3199 Hits e 3199 Não Hits.

2.2 Atributos

Os 18 atributos de cada registro são:
● track: O nome da faixa musical
● artist: Nome do artista.
● url: identifica a origem da faixa
● danceability: descreve como uma faixa é adequada para dançar com base em uma
combinação de elementos musicais, incluindo andamento, estabilidade do ritmo,
intensidade da batida e regularidade geral. Um valor de 0,0 é menos dançável e 1,0 é
mais dançante.
● energy: medida de 0,0 a 1,0 e representa uma medida perceptual de intensidade e
atividade. Normalmente, as faixas energéticas parecem rápidas, altas e barulhentas.
Por exemplo, death metal tem alta energia, enquanto um prelúdio de Bach tem
pontuação baixa na escala. As características perceptivas que contribuem para este
atributo incluem faixa dinâmica, intensidade percebida, timbre, taxa de início e entropia
geral.
● key: O Tom da faixa no geral. Números inteiros mapeiam os tons utilizando notação
padrão. Ex\;. 0 = C, 1 = C#/Db, 2 = D, e e assim por diante. Se o tom não foi
identificado, o valor é -1.
● loudness: O volume geral de uma faixa em decibéis (dB). Os valores são calculados
em toda a faixa e são úteis para comparar a sonoridade relativa das faixas. Loudness é
a qualidade de um som que é o principal correlato psicológico da força física
(amplitude). Os valores típicos variam entre -60 e 0 db.
● mode: Modo indica a modalidade (maior ou menor) de uma faixa, o tipo de escala da
qual seu conteúdo melódico é derivado. Maior é representado por 1 e menor é 0.
● speechiness: detecta a presença de palavras faladas em uma faixa. Quanto mais
exclusivamente falada for a gravação (por exemplo, talk show, audiolivro, poesia), mais
próximo de 1,0 será o valor do atributo. Valores acima de 0,66 descrevem faixas que
provavelmente são compostas inteiramente de palavras faladas. Valores entre 0,33 e
0,66 descrevem faixas que podem conter música e fala, em seções ou em camadas,
incluindo casos como música rap. Valores abaixo de 0,33 provavelmente representam
faixas com mais ênfase na música e menos na fala.
● acousticness: Uma medida de confiança de 0,0 a 1,0 para saber se a faixa é acústica.
1.0 representa alta confiança de que a faixa é acústica.
● instrumentalness: Prevê se uma faixa não contém vocais. Os sons “Ooh” e “aah” são
tratados como instrumentais neste contexto. Faixas de rap ou palavra falada são
claramente “vocais”. Quanto mais próximo o valor da instrumentalidade estiver de 1,0,
maior será a probabilidade de a faixa não conter conteúdo vocal. Valores acima de 0,5
destinam-se a representar faixas instrumentais, mas a confiança é maior à medida que
o valor se aproxima de 1,0.
● liveness: Detecta a presença de um público na gravação. Valores de vivacidade mais
altos representam um aumento na probabilidade de a trilha ter sido executada ao vivo.
Um valor acima de 0,8 fornece uma forte probabilidade de que a faixa esteja ao vivo.
● valence: A measure from 0.0 to 1.0 describing the musical positiveness conveyed by a
track. Tracks with high valence sound more positive (e.g. happy, cheerful, euphoric),
while tracks with low valence sound more negative (e.g. sad, depressed, angry).
● tempo: O tempo estimado geral de uma faixa em batidas por minuto (BPM). Na
terminologia musical, o tempo é a velocidade ou ritmo de uma determinada peça e
deriva diretamente da duração média do tempo.
● duration_ms: A duração da faixa em milissegundos.
● time_signature: Uma estimativa geral do compasso de uma faixa. O compasso
(medidor) é uma convenção notacional para especificar quantas batidas existem em
cada barra.
● chorus_hit: Estimativa do trecho em que o refrão aparece.
● sections: O número de seções que a faixa específica possui.a
● target: A variável de destino da faixa. Pode ser '0' ou '1'. '1' implica que essa música
apareceu na lista semanal (publicada pela Billboards) das faixas do Hot-100 naquela
década pelo menos uma vez e, portanto, é um 'hit'. '0' implica que a faixa é um 'flop'.


Matriz de Correlação
Foi verificada a ausência de missing values e foram retiradas as categorias
desnecessárias (track, artist, uri). Depois de processar os atributos a base de
dados foi dividida para treinamento e teste, tendo a proporção de 20% para
treinamento.
3. Modelos e Algoritmos
Para previsão foram utilizados 4 tipos de modelo de classificação:
● Logistic Regression (LR)
● Random Forest (RF)
● AdaBoost
● K-nearest neighbors (KNN)
Foram obtidos os seguintes resultados:
Logistic Regression (LR)
Random Forest (RF)
AdaBoost
KNN
4. Resultados
O modelo de classificação escolhido foi Random Forest apresentando precisão
de 99% no treinamento e 91% no teste. O resultado final indicou 85,7% de
acurácia.
5. Conclusão
O projeto final da disciplina data mining foi uma oportunidade de iniciar estudos
preliminares para um provável projeto final tendo como foco a área de Music
Information Retrieval. Optei por realizar em Python como forma de me
aprofundar na linguagem e certamente é um código que seguirei trabalhando e
aperfeiçoando. Agradeço pelas excelentes aulas que estão possibilitando
compreender melhor os debates sobre MIR, meu foco de pesquisa.
