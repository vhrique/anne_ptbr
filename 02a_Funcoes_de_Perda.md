# Funções de Perda

As funções de perda (ou funções de custo) são componentes centrais no treinamento de redes neurais, pois medem o quão bem o modelo está performando.
Elas comparam as predições feitas pela rede com os valores reais e retornam um valor numérico que indica o erro da previsão.
O objetivo do treinamento é minimizar essa função de perda ajustando os pesos da rede, com a ajuda de algoritmos de otimização, para que o erro se torne o menor possível.

Essencialmente, a função de perda informa à rede neural como melhorar suas predições ao longo do processo de aprendizado.
Dependendo do tipo de problema (classificação, regressão, multiclasse, etc.), diferentes funções de perda são utilizadas.

## Funções de Perda para Classificação

### Binary Cross-Entropy

A Binary Cross-Entropy (BCE) é comumente usada em problemas de classificação binária, onde o objetivo é prever se uma amostra pertence a uma de duas classes.
Essa função mede a diferença entre a probabilidade prevista e o valor real, penalizando fortemente predições erradas. A fórmula é:

$$
\text{BCE} = - \frac{1}{N}\sum_{i=1}^{N}\left[y_i.log(\hat{y}_i) + (1 - y_i).log(1-\hat{y}_i)\right]
$$

Aqui, $y_i$ é o valor real (0 ou 1) e $\hat{y}_i$ é a probabilidade prevista.
O objetivo é minimizar essa diferença, fazendo com que a probabilidade prevista se aproxime do valor real.

- Vantagem: Funciona muito bem com problemas binários, lidando com probabilidades.
- Desvantagem: Pode ser mais sensível a problemas de balanço de classes.

#### Multilabel Binary Cross-Entropy

Em problemas de classificação multilabel, onde uma entrada pode pertencer a mais de uma classe, a Multilabel Binary Cross-Entropy é utilizada.
É basicamente a BCE aplicada a cada rótulo individualmente.
A fórmula é semelhante à da BCE, mas ajustada para várias saídas simultâneas.

- Vantagem: Adequada para problemas onde uma entrada pertence a múltiplas classes.
- Desvantagem: Pode se tornar ineficiente com um grande número de classes.

### Categorical Cross-Entropy

A Entropia Cruzada Categórica é usada em problemas de classificação multiclasse, onde o objetivo é prever uma entre várias classes mutuamente exclusivas.
A fórmula é:

$$
\text{CCE} = - \frac{1}{N}\sum_{i=1}^{N}\sum_{j=1}^{C}y_{ij}.log(\hat{y}_{ij})
$$

Aqui, $C$ é o número de classes, $y_{ij}$ é o valor real (geralmente um vetor one-hot) e $\hat{y}_{ij}$ é a probabilidade prevista para a classe $j$.
A _softmax_ é usada como função de ativação na saída, convertendo as predições em probabilidades.

- Vantagem: Adequada para problemas com várias classes exclusivas.
- Desvantagem: Não lida bem com situações em que uma instância pode pertencer a múltiplas classes.

### Margin (Hinge) Loss

O Hinge Loss é usado com máquinas de vetores de suporte (SVMs), mas também pode ser aplicado em redes neurais para problemas de classificação binária.
Ele força o modelo a maximizar a margem entre as classes, penalizando erros de classificação de forma mais agressiva.

A fórmula para um problema binário é:

$$
L = \sum_{i=1}^{N}\text{max}(0,1-y_i.\hat{y}_i)
$$

Aqui, $y_i$ são os rótulos reais (+1 ou -1), $\hat{y}_{i}$ e são as predições do modelo.

- Vantagem: Eficaz em maximizar a separação entre as classes.
- Desvantagem: Principalmente usado em SVMs e menos comum em redes neurais.

## Funções de Perda para Problemas de Regressão

### Mean Squared Error

O MSE é amplamente usado em problemas de regressão, onde o objetivo é prever valores contínuos.
Ele mede a diferença média entre as predições do modelo e os valores reais, elevando ao quadrado essas diferenças para garantir que erros positivos e negativos não se cancelem.
A fórmula é:

$$
\text{MSE} = \frac{1}{N}\sum_{i=1}^N(y_i - \hat{y}_i)^2
$$

onde $y_i$ é o valor real e $\hat{y}_i$ é a predição do modelo.
O quadrado das diferenças garante que erros grandes tenham um impacto maior no valor final.

- Vantagem: Simples de calcular e amplifica grandes erros.
- Desvantagem: Sensível a outliers, já que erros grandes têm um impacto desproporcional.

### Mean Absolute Error

O MAE é outra função de perda usada para problemas de regressão, mas, ao contrário do MSE, mede a diferença absoluta média entre os valores previstos e os valores reais.
Sua fórmula é:

$$
\text{MSE} = \frac{1}{N}\sum_{i=1}^N \left|y_i - \hat{y}_i \right|
$$

- Vantagem: Mais robusto a outliers do que o MSE.
- Desvantagem: Não diferencia grandes e pequenos erros da mesma forma que o MSE.

### Huber Loss

A Huber Loss é uma função de perda que combina as vantagens do Erro Quadrático Médio (MSE) e do Erro Absoluto Médio (MAE), oferecendo uma abordagem robusta para problemas de regressão, especialmente na presença de outliers.
Ela foi projetada para tratar grandes erros de forma mais eficiente do que o MSE, que é altamente sensível a outliers, enquanto mantém a simplicidade do MAE em regiões de pequenos erros.
A fórmula da Huber Loss é definida de forma diferente para erros pequenos e grandes:

$$
L_{\delta}(y_i, \hat{y}_i) =
\begin{cases}
\frac{1}{2}(y_i - \hat{y}_i)^2 & \text{se } |y_i - \hat{y}_i| \leq \delta \\
\delta \cdot (|y_i - \hat{y}_i| - \frac{1}{2} \delta) & \text{se } |y_i - \hat{y}_i| > \delta
\end{cases}
$$

onde $y_i$ é o valor real, $\hat{y}_i$ é a previsão do modelo e $\delta$ é um parâmetro que define o limite entre erros pequenos e grandes.

A Huber Loss funciona de forma suave em relação a pequenos erros, como o MSE, mas trata erros grandes de maneira mais robusta, como o MAE.
Isso faz com que seja uma função intermediária que lida bem tanto com ruídos pequenos quanto com outliers, sendo especialmente útil em problemas de regressão.

Vantagens:

- Robustez a outliers: Quando há grandes erros ou outliers, a Huber Loss não amplifica esses erros tanto quanto o MSE, evitando que um pequeno número de outliers distorça significativamente o modelo.
- Suavidade em pequenos erros: Para erros pequenos, a Huber Loss se comporta como o MSE, permitindo que a função de perda seja diferenciável e suave, o que facilita a otimização.

Desvantagens:

- Escolha de $\delta$: O valor de
$\delta$ deve ser escolhido cuidadosamente, pois um valor mal ajustado pode levar a um comportamento inadequado da função de perda. Sefor muito pequeno, o modelo se comportará quase como o MAE, e se for muito grande, se aproximará do MSE, perdendo as vantagens da robustez

A Huber Loss é amplamente utilizada em problemas de regressão onde há a presença de outliers nos dados, pois oferece um equilíbrio entre ser suave para erros pequenos e robusta para grandes erros. Além disso, é preferida em aplicações de machine learning onde o MSE tende a ser excessivamente influenciado por grandes outliers.

## Outras Funções de Perda

A KL Divergence é utilizada para medir a diferença entre duas distribuições de probabilidade, sendo particularmente útil em modelos probabilísticos, como variational autoencoders (VAEs).
Ela não é propriamente uma função de perda no sentido tradicional, mas é amplamente usada para regularizar a distribuição de saída de um modelo para que seja similar a uma distribuição-alvo.

A Cosine Similarity Loss mede o ângulo entre dois vetores, sendo usada para comparar a similaridade entre vetores em vez de medir a diferença absoluta.
Isso é especialmente útil em problemas de aprendizado de representações, como em redes neurais siamesas e embedding learning.

A Focal Loss foi introduzida para tratar o problema de desbalanceamento de classes, em que algumas classes são muito mais representadas que outras.
Ela é uma modificação da entropia cruzada que coloca mais peso nas amostras difíceis (ou seja, aquelas que são classificadas de forma incorreta).

Também chamada de Huber Loss, mas com uma implementação ligeiramente diferente, a Smooth L1 Loss é amplamente utilizada em redes neurais para detecção de objetos. Ela é mais robusta a outliers do que a MSE e mais estável do que o MAE.

A Dice Loss é uma função de perda comumente usada em problemas de segmentação de imagens, especialmente em áreas médicas, onde é necessário calcular a sobreposição entre a área predita e a área verdadeira.
É derivada do coeficiente de Dice, que mede a similaridade entre dois conjuntos.

A Triplet Loss é usada para aprendizado de embeddings e aprendizado métrico, particularmente em redes siamesas.
A função de perda incentiva a rede a reduzir a distância entre embeddings de amostras semelhantes (o ancor e o positivo) e aumentar a distância entre o ancor e amostras dissimilares (o negativo).

A Wing Loss é uma função de perda desenhada especificamente para problemas de detecção de landmarks faciais, onde pequenos erros precisam ser suavemente penalizados, mas grandes erros devem ser penalizados de forma mais forte.

## Considerações Finais: Cross-Entropy como Função de Perda em Redes Neurais

A entropia cruzada (cross-entropy) tem suas origens na teoria da informação, desenvolvida por Claude Shannon na década de 1940.
A ideia central da teoria da informação é quantificar a quantidade de informação ou incerteza presente em um conjunto de dados, e a entropia é uma medida dessa incerteza.
A entropia de Shannon mede o grau de imprevisibilidade de um sistema de eventos, sendo usada para descrever a incerteza associada a uma distribuição de probabilidades.

No contexto de redes neurais, a entropia cruzada é uma medida da divergência entre duas distribuições de probabilidade: a distribuição verdadeira dos rótulos (a saída correta) e a distribuição prevista pelo modelo.
A fórmula original da entropia cruzada é baseada na divergência de Kullback-Leibler (KL Divergence), que mede a diferença entre duas distribuições de probabilidade $P$ e $Q$.
No caso de uma rede neural, $P$ é a distribuição verdadeira dos rótulos (normalmente representada por um vetor one-hot) e $Q$ é a distribuição de probabilidade prevista pelo modelo.

A fórmula da entropia cruzada é dada por:

$$
H(P,Q) = - \sum_{i=1}^{C}P(i)log(Q(i))
$$

Onde:

- $P(i)$ é a probabilidade verdadeira para a classe $i$ (em problemas de classificação, geralmente 0 ou 1).
- $Q(i)$ é a probabilidade prevista pelo modelo para a classe $i$.

A entropia cruzada mede o quão bem o modelo está capturando a distribuição verdadeira dos rótulos.
Quando $P(i)$ é 1 (ou seja, a classe $𝑖$ é a correta), a entropia cruzada penaliza o modelo se a probabilidade $𝑄(i)$ não estiver próxima de 1.

