# Fundamentos de Aprendizagem

Existem diferentes paradigmas de aprendizagem em redes neurais artificiais (RNAs), baseados em diferentes maneiras de treinar um modelo e interagir com os dados.
De forma geral, existem três paradigmas principais, comuns à área de aprendizagem de máquina: aprendizagem supervisionada, aprendizagem não supervisionada e aprendizagem por reforço.
Cada um desses paradigmas possui métodos distintos de treinar modelos, com base na disponibilidade e tipo de dados, bem como no objetivo final da tarefa.

Na aprendizagem supervisionada, o modelo aprende a partir de dados rotulados, tentando prever uma saída correta com base em entradas específicas.

<center><img src="https://github.com/vhrique/anne_ptbr/blob/main/figures/supervised.jpg?raw=true" width="500"></center>

Já na aprendizagem não supervisionada, os dados não possuem rótulos, e o modelo busca identificar padrões ou estruturas nos dados, como clusters ou associações.

<center><img src="https://github.com/vhrique/anne_ptbr/blob/main/figures/clustering.jpg?raw=true" width="500"></center>

Por fim, na aprendizagem por reforço, o modelo aprende através da interação com um ambiente, recebendo recompensas ou penalidades com base nas ações tomadas, ajustando seu comportamento para maximizar a recompensa ao longo do tempo.

<center><img src="https://github.com/vhrique/anne_ptbr/blob/main/figures/reinforcement.jpg?raw=true" width="300"></center>

Com o uso de redes neurais, novas formas de aprendizagem também surgiram, como aprendizagem auto-supervisionada e aprendizagem contrastiva, as quais veremos nos materiais seguitnes.

# Aprendizagem = Representação + Avaliação + Otimização

Conforme indicado por Pedro Domingos (2012), três componentes aparecem em todos os paradigmas de aprendizagem: representação, avaliação e otimização.
Esses três componentes são fundamentais para qualquer paradigma de aprendizagem, desde as tarefas supervisionadas mais simples até as mais complexas formas de aprendizado, como o _self-supervised learning_, que veremos nos capítulos futuros.
A interação entre esses componentes define o sucesso e a eficácia de um modelo ao generalizar para novos dados e resolver problemas reais.

<center><img src="https://raw.githubusercontent.com/vhrique/anne2024/8eb24ed5fc4d5ffd55d1664b512417ad8a2d71a0/figures/mapa_mental_supervised_learning_reduced.drawio.svg" width="600"></center>

## Representação

A representação refere-se a como os dados e o conhecimento são modelados internamente pelo modelo. Ela define como as características dos dados serão manipuladas para que o modelo possa aprender padrões úteis, e sua escolha tem um impacto significativo no desempenho de um modelo.

### Considerações sobre Representação e Viés Indutivo

Diferentes algoritmos de aprendizado de máquina utilizam diferentes tipos de representação. Por exemplo, o K-Nearest Neighbors (KNN) representa os dados como pontos em um espaço métrico, assumindo que amostras próximas têm comportamentos similares, o que reflete um viés indutivo de proximidade espacial. Já em árvores de decisão, a representação dos dados é estruturada hierarquicamente, onde divisões sucessivas criam nós e folhas que categorizam as amostras, impondo um viés de segmentação binária nos dados.

Nas redes neurais, os dados são representados de forma abstrata através de camadas de neurônios, onde cada camada transforma os dados em representações progressivamente mais complexas e abstratas, refletindo um viés indutivo de que os padrões nos dados podem ser aprendidos através de composições hierárquicas de funções não-lineares. Em uma rede neural profunda, por exemplo, camadas sucessivas de neurônios aprendem representações progressivamente mais complexas dos dados. No início, as camadas podem detectar bordas ou formas simples em uma imagem, enquanto camadas mais profundas podem aprender a identificar objetos ou partes mais complexas.

## Avaliação

A avaliação mede o quão bem o modelo aprendeu a tarefa. As métricas de avaliação variam conforme a tarefa e o tipo de aprendizado. Na aprendizagem supervisionada, por exemplo, para classificação, utilizamos métricas como acurácia ou F1-score, enquanto, em regressão, utilizamos erro quadrático médio (MSE) ou erro absoluto médio (MAE). Ao treinar redes neurais artificiais, utilizamos **funções de perda**.

As funções de perda (ou funções de custo) são componentes centrais no treinamento de redes neurais, pois medem o quão bem o modelo está performando.
Elas comparam as predições feitas pela rede com os valores reais e retornam um valor numérico que indica o erro da previsão.
Dependendo do tipo de problema (classificação, regressão, etc.), diferentes funções de perda são utilizadas.

Essencialmente, a função de perda informa à rede neural como melhorar suas predições ao longo do processo de aprendizado por meio de otimização. Otimização e avaliação são, portanto, componentes complementares e essenciais para garantir que o modelo de aprendizado de máquina aprenda de forma eficiente e seja capaz de realizar boas previsões em novos dados.


## Otimização

O processo de otimização envolve a maneira como o modelo ajusta seus parâmetros internos para minimizar uma função de perda, que mede o quão longe as previsões estão das saídas desejadas. Em redes neurais, esse processo é realizado por **algoritmos de otimização**, como o **gradiente descendente**, que, com o auxílio do algoritmo de _backpropagation_, ajusta os pesos das conexões neurais para minimizar a diferença entre a predição do modelo e o rótulo correto. Em suma, a otimização busca garantir que o modelo aprenda da melhor maneira possível com os dados disponíveis, ajustando-se para capturar os padrões mais relevantes e reduzir o erro nas predições.

# Referências

- Murphy, K. P. (2022). Probabilistic machine learning: an introduction. MIT press.
- Domingos, P. (2012). A few useful things to know about machine learning. Communications of the ACM, 55(10), 78-87.
