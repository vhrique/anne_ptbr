# Engenharia de Redes Neurais Artificiais

Este repositório mantém os materiais utilizados na disciplina "Engenharia de Redes Neurais Artificiais", do Programa de Pós-Graduação em Engenharia de Produção e Sistemas, da Pontifícia Universidade Católica do Paraná.

## Apresentação

Redes Neurais Artificiais (RNAs) são modelos matemáticos/computacionais que buscam simular a estrutura e a função do cérebro para processar dados e realizar tarefas complexas.
As pesquisas nesta área começaram na década de 1940, quando foram desenvolvidas as idéias iniciais de criar modelos computacionais para simular redes neurais.
Na década seguinte, foi implementado o primeiro modelo matemático capaz de simular um neurônio, o _perceptron_.
Este evento gerou uma grande comoção e iniciou uma onda de investimentos na área.

Porém, com o tempo, pesquisadores encontraram dificuldades em cumprir as promessas de utilizar estes modelos para resolver problemas não-lineares.
Os modelos iniciais de RNAs foram criticados por serem capazes de resolver apenas problemas lineares, e não havia ainda uma forma eficiente de criar modelos mais complexos.
Isto resultou no primeiro inverno de Inteligência Artificial entre as décadas de 1970 e 1980, quando havia muito pouco investimento na área.

Pesquisadores que continuaram estudando esta área conseguiram desenvolver modelos maiores, agregando diversos _perceptrons_ e criando redes complexas, capazes de processar dados não-lineares.
Isto foi possível principalmente pelo desenvolvimento do algorithmo de _backpropagration_, que permitiu treinar modelos maiores de forma eficiente.
Porém, realizar o treinamento de modelos muito grandes se tornou uma tarefa computacionalmente muito complexa, e outros modelos computacionais mais eficientes começaram a ser desenvolvidos na área de _machine learning_ entre as décadas de 1990 e 2000.

Anos depois, entre o final da década de 2000 e início de 2010, modelos cada vez maiores e mais eficientes foram desenvolvidos, graças a avanços em técnicas e a uma maior disponibilidade de poder computacional.
Finalmente, em 2012, a RNA AlexNet foi vencedora de uma famosa competição de Visão Computacional (ImageNet) por uma distância considerável em relação às outras técnicas clássicas de visão computacional.
Isto trouxe muito otimismo no uso de RNAs, resultando em novas pesquisas e em rápidos avanços na área de visão computacional.

Consequentemente, novas arquiteturas foram desenvolvidos para resolver outros problemas de engenharia.
Em 2017, foi desenvolvido o modelo _transformer_, que trouxe um rápido avanço na área de processamento de linguagem natural.
Tal modelo também foi utilizado em outras áreas, incluindo visão computacional, o que trouxe ainda mais avanços, como Inteligência Artificial Generativa, capaz de conversar, gerar imagens e vídeos.

Hoje em dia, estamos em uma fase de rápida transformação graças a esta tecnologia.
Utilizamos chatbots que nos auxiliam em nosso trabalho, nos livram de tarefas repetitivas, e conseguem inclusive realizar trabalho criativo.
Nosso objetivo nessa disciplina é estudar os fundamentos e o estado da arte de redes neurais para compreender como utilizar esta tecnologia para resolver problemas complexos de engenharia.

## Ementa

Ensinar conceitos básicos e avançados de redes neurais artificiais, assim como formas inovadoras de usar esta tecnologia para resolver problemas de _machine learning_ e engenharia.
Por meio de exemplos e atividades, os estudantes irão resolver problemas de diversos de engenharia e _machine learning_, como processamento de imagens e sinais e geração de dados sintéticos.

## Público-alvo

Esta disciplina esta aberta para estudantes das áreas de Engenharia e Computação que buscam aprimorar seus conhecimentos em _machine learning_.

## Requisitos

Os estudantes devem ter conhecimento intermediário dos seguintes tópicos:

- Aprendizagem de Máquina
- Linguagem de Programação Python

## Temas de Estudo

- Fundamentos de Redes Neurais Artificiais: _Perceptron_, _Multilayer Perceptron_ e _Backpropagation_.
- Paradigmas de Aprendizagem: Problemas de Classificação e Regressão, Algoritmos de Otimização, Funções de Perda. 
- Arquiteturas Especializadas para Visão Computacional: Redes Neurais Convolucionais, Classificação de Imagens, Detecção de Objetos, Segmentação de Imagens.
- Arquiteturas Especializadas para Dados Sequenciais: RNN, LSTM, GRU, Transformers.
- Paradigmas de Aprendizagem Avançadas I: Self-Supervised Learning: Auto-encoders, GANs, Redes Siamesas e Contrastive Learning
- Paradigmas de Aprendizagem Avançadas II: Multi-task Learning, Multi-modal Learning, Joint-embedding Learning
- Aspectos Práticos: Transfer Learning, Model Distillation, Domain Adaptation.
- Novas Fronteiras em RNAs: Diffusion, Mixture of Experts, State-space Models, Deep Equilibrium Networks, Hyper Networks, Graph Neural Networks, PointNet
- Tópicos Especiais: Explainable AI, Ética em IA, Deep Reinforcement Learning, Deep Recommender Systems, Meta-learning

### Mapa Mental da Disciplina

![Mapa Mental](https://raw.githubusercontent.com/vhrique/anne2024/main/figures/mapa_mental.drawio.svg)

## Ferramentas Utilizadas

- Ambiente de Desenvolvimento Cloud (Gratuito): Google Colaboratory ou Lightning AI
- Python: Pytorch, Numpy, Pyplot, Scikit-learn, OpenCV, etc.

## Aulas

- [Aula 01: Fundamentos de Redes Neurais Artificiais](01_Fundamentos_de_Redes_Neurais_Artificiais.ipynb)
- [Aula 02: Introdução à Paradigmas de Aprendizagem](02_Paradigmas_Aprendizagem.ipynb)
- [Aula 03: Arquiteturas Especializadas em Visão Computacional](03_CNN.ipynb)
- [Aula 04: Arquiteturas Especializadas em Dados Sequenciais](04_RNN_Transformers.ipynb)
- [Aula 05: Paradigmas de Aprendizagem Avançadas](05_Paradigmas_Avancados.ipynb)
- [Aula 06: Paradigmas de Aprendizagem Compostas](06_Paradigmas_Compostos.ipynb)
- [Aula 07: Aspectos Práticos](07_Aspectos_Praticos.ipynb)
- [Aula 08: Novas Fronteiras](08a_Novas_Fronteiras.ipynb) e [Aula 08: Tópicos Especiais](08b_Topicos_Especiais.ipynb)
- [Aula 09: Apresentação do Projeto Final](09_Intrucoes_para_Projeto_Final.md)

## Materiais Adicionais

- [Aula 01: Fundamentos de Pytorch](01a_Fundamentos_de_Pytorch.ipynb)
- [Aula 03: Exemplo Visão Computacional](03a_Exemplo_Visao_Computacional.ipynb)
- [Aula 04: Exemplo de Série Temporal](04a_Exemplo_Serie_Temporal.ipynb)
- [Aula 04: Exemplo de Processamento de Linguagem Natural](04b_Exemplo_PLN.ipynb)

## Avaliação

Esta disciplina será avaliada da seguinte forma:

- Listas de Exercícios (40%):
  - Cada aula terá uma lista de exercícios que deve ser entregue até o final do curso.
  - As listas deverão ser entregues como arquivos ipynb pelo sistema da disciplina.
- Projeto Final (60%):
  - O projeto final deve ser desenvolvido durante a disciplina, conforme [Instruções do Projeto Final](09_Intrucoes_para_Projeto_Final.md)
  - O projeto final deverá ser apresentado na Aula 09
  - O relatório deverá ser entregue no sistema da disciplina.

## Materiais Externos

- [Materiais de Curso sobre Deep Learning, de Yann LeCun](https://atcold.github.io/NYU-DLSP21/)
- [Notas de Aula sobre Algoritmos de Otimização, de Geoffrey Hinton](https://www.cs.toronto.edu/~tijmen/csc321/slides/lecture_slides_lec6.pdf)
- [Livro Interativo _Dive into Deep Learning_](https://pt.d2l.ai/index.html)

## Referências

- [Livro sobre Deep Learning, de Ian Goodfellow](https://www.deeplearningbook.org/)
- [Livro sobre Deep Learning, de Christopher Bishop](https://www.bishopbook.com/)
- [Livro de Bolso sobre Deep Learning, de François Fleuret](https://fleuret.org/public/lbdl.pdf)
- [Livro sobre Tópicos Avançados de Machine Learning (Deep Learning), de Kevin Murphy](https://probml.github.io/pml-book/book2.html)
- [Livro sobre Introdução de Machine Learning, de Kevin Murphy](https://probml.github.io/pml-book/book1.html)
- [Livro de Aprendizagem Estatística, de Hastie et al.](https://hastie.su.domains/Papers/ESLII.pdf)

## Professor

Dr. Eng. Victor Henrique Alves Ribeiro

[![Linkedin](https://skillicons.dev/icons?i=linkedin)](https://www.linkedin.com/in/vhrique/) [![Twitter](https://skillicons.dev/icons?i=twitter)](https://x.com/vhrique)
