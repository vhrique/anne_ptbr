# Algoritmos de Otimização

Os algoritmos de otimização são fundamentais para o processo de aprendizagem de redes neurais, pois determinam como os pesos dos neurônios são ajustados para minimizar a função de perda durante o treinamento.
O objetivo da otimização é encontrar os melhores parâmetros (pesos e vieses) que permitam à rede fazer previsões precisas em novos dados.

A função de perda mede o quão longe as previsões do modelo estão dos valores reais, e o papel do algoritmo de otimização é minimizar essa função ajustando gradualmente os pesos.
Isso é feito por meio do cálculo do gradiente, que indica a direção e a magnitude da mudança necessária nos pesos.

Agora, vamos explorar alguns dos principais algoritmos de otimização e suas evoluções

## Gradiente Descendente

O gradiente descendente é o algoritmo de otimização mais simples e amplamente utilizado.
Ele funciona ajustando os pesos na direção oposta ao gradiente da função de perda com relação a esses pesos.
A ideia é que, ao seguir essa direção de forma iterativa, o algoritmo chegue ao mínimo da função de perda, onde o modelo realiza as previsões mais precisas.

Existem três variações principais do gradiente descendente:

- Batch Gradient Descent: Calcula o gradiente em todo o conjunto de dados de treinamento antes de atualizar os pesos. Esse método pode ser lento e ineficiente para grandes conjuntos de dados.
- Stochastic Gradient Descent (SGD): Atualiza os pesos para cada exemplo de treino individual, tornando o processo mais rápido, mas introduzindo maior variação nas atualizações.
- Mini-Batch Gradient Descent: Combina os dois anteriores, calculando o gradiente em pequenos lotes de dados, acelerando o treinamento e suavizando a variação das atualizações.

## Momentum

O Momentum foi introduzido como uma melhoria ao gradiente descendente.
Ele acelera o processo de convergência em direção ao mínimo, acumulando uma fração do gradiente anterior em cada atualização.
Isso ajuda a suavizar o caminho em direção ao mínimo, evitando oscilações, especialmente em direções que têm gradientes mais ruidosos.

A ideia é que, em vez de seguir estritamente a direção do gradiente atual, o modelo leva em conta o "momento" da direção em que está se movendo, como uma bola rolando por uma superfície irregular.
Isso permite que o modelo alcance o mínimo mais rapidamente.

## RMSProp

O RMSProp é um método de otimização adaptativo que ajusta a taxa de aprendizado individualmente para cada parâmetro, com base na magnitude dos gradientes recentes.
Ele mantém uma média móvel quadrada dos gradientes ao longo do tempo e, ao dividir o gradiente atual por essa média, corrige a taxa de aprendizado para cada parâmetro.
Isso faz com que RMSProp se adapte melhor a problemas com gradientes que variam em escalas diferentes.

Essa adaptação da taxa de aprendizado para cada peso torna o treinamento mais estável e eficaz, especialmente em problemas como redes neurais profundas, onde as atualizações dos pesos podem variar muito.

## ADAM

O ADAM combina o melhor de dois mundos: as ideias do Momentum e do RMSProp.
Ele calcula uma média móvel dos gradientes (como o Momentum) e uma média móvel dos quadrados dos gradientes (como o RMSProp), ajustando a taxa de aprendizado de forma adaptativa para cada parâmetro.

ADAM também inclui uma correção para viés nos primeiros passos, garantindo que as médias móveis comecem corretamente ajustadas.

## Outros Algoritmos

Além dos algoritmos clássicos que discutimos (Gradiente Descendente, Momentum, RMSProp e ADAM), existem outros algoritmos de otimização relevantes que, dependendo do problema e das características da rede neural, podem oferecer vantagens em termos de desempenho ou convergência.

O AdaGrad é um dos primeiros algoritmos de otimização adaptativos, introduzido antes do RMSProp.
Ele ajusta a taxa de aprendizado para cada parâmetro de forma individual, com base nas atualizações anteriores.
Isso significa que parâmetros raramente atualizados têm uma taxa de aprendizado maior, enquanto aqueles que já foram ajustados várias vezes têm a taxa de aprendizado reduzida.
Embora seja útil em problemas esparsos, como no processamento de linguagem natural, onde algumas features são raras, AdaGrad pode sofrer de um decaimento excessivo da taxa de aprendizado, o que leva a convergência mais lenta em muitos casos.

O AdaDelta é uma variação do AdaGrad, projetada para corrigir o problema de decaimento da taxa de aprendizado.
Em vez de acumular todas as atualizações anteriores, como o AdaGrad, o AdaDelta mantém uma janela deslizante de atualizações recentes, limitando o impacto de atualizações passadas muito distantes.
Isso mantém a adaptabilidade da taxa de aprendizado sem que ela diminua drasticamente ao longo do tempo.
Assim como o RMSProp, AdaDelta é muito utilizado em redes profundas e outros problemas complexos.

O Nadam é uma combinação de ADAM com o conceito de Nesterov Momentum.
A diferença em relação ao Momentum clássico é que, no Nesterov Momentum, o cálculo do gradiente é realizado com uma "visão antecipada" da direção para onde os pesos estão se movendo, o que pode acelerar o processo de convergência.
O Nadam aplica essa ideia no contexto do ADAM, resultando em um algoritmo que pode ser ligeiramente mais eficiente e estável do que o ADAM em certos cenários.

O AMSGrad é uma modificação do ADAM que tenta resolver um problema de convergência observada no ADAM original, especialmente em situações onde a função de perda não é convexa.
No ADAM, os parâmetros de aprendizado podem não convergir para o ótimo global em algumas situações.
O AMSGrad corrige isso, garantindo que as médias móveis dos gradientes só decaiam, o que melhora a convergência em alguns problemas.
Esse algoritmo é um dos mais populares atualmente, pois oferece uma convergência mais rápida e estável em diversos tipos de problemas de redes neurais, sendo menos sensível à escolha da taxa de aprendizado inicial.
