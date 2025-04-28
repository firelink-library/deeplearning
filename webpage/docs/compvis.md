---
sidebar_position: 3
slug: /compvis
title: Algoritmos de Visão Computacional Clássica
---


## 1. Introdução a Visão Computacional Clássica

Aqui pessoal, vamos avaliar o seguinte problema: temos uma imagem de um processo e precisamos classificar está imagem. Imagine quantos contextos diferentes está pequena descrição consegue atender: classificar produtos em uma linha de montagem, encontrar erros em um processo produtivo, determinar qual produto deve ser embalado em uma linha de produção, isso só para citar algumas aplicações.

> "Legal tudo isso Murilo, mas como podemos realizar tudo isso?"

É aqui que entram nossos algoritmos de ***visão computacional clássica***! Vamos compreender primeiro o fluxo de operações que vamos realizar e depois vamos implementar cada uma delas beleza?

<img  src={require('/img/compvis/diagrama-compvis.png').default} alt="Diagrama Visão Computacional Clássica" 
style={{marginLeft:'auto', marginRight:'auto', display:'block', width:'80%'}} />

Vamos explorar cada um dos quadros desta figura! Primeiro temos a imagem que vai ser captada para dentro do nosso sistema. Observe um ponto importante aqui: a imagem pode ser captada de várias formas, seja por uma câmera, seja por um scanner, seja por um celular, etc. O importante é que a imagem esteja em um formato que o computador consiga ler e processar. Para isso, existem várias bibliotecas disponíveis, como OpenCV, PIL, entre outras.

Depois de captada a imagem, precisamos realizar o seu pré-processamento. Mas o que é isso? O pré-processamento é uma etapa onde aplicamos algumas operações na imagem, como filtros, redimensionamento, normalização, entre outras. O objetivo do pré-processamento é melhorar a qualidade da imagem e facilitar a extração de características relevantes para a classificação. 

Na sequência, temos a segmentação da imagem. Ela é a etapa onde dividimos a imagem em regiões ou objetos de interesse. Isso é importante porque, muitas vezes, a imagem contém várias informações que não são relevantes para a tarefa de classificação. A segmentação nos ajuda a focar apenas nas partes da imagem que realmente importam. Existem várias técnicas de segmentação, como limiarização, segmentação baseada em regiões, entre outras.

Seguido da segmentação, temos a etapa da extração de características. Nesta etapa, extraímos informações relevantes da imagem que serão utilizadas para a classificação. Essas características podem ser, por exemplo, bordas, texturas, cores, formas, entre outras. A escolha das características a serem extraídas depende do problema que estamos tentando resolver e do tipo de imagem que estamos analisando.

Agora com a região de interesse e as característica extraídas das imagens, podemos começar a desenvolver o nosso modelo de classificação. Existem várias técnicas de classificação, como máquinas de vetor de suporte (SVM), árvores de decisão, redes neurais, entre outras. A escolha do modelo depende do problema que estamos tentando resolver e das características extraídas da imagem. O processo de classificação envolve o treinamento do modelo com um conjunto de dados rotulados. Esses dados rotulados são as imagens que serão utilizadas para ensinar o modelo a reconhecer os padrões presentes nas imagens. O modelo aprende a associar as características extraídas das imagens com as classes correspondentes. Após o treinamento, o modelo pode ser utilizado para classificar novas imagens, ou seja, imagens que não foram utilizadas durante o treinamento. O modelo irá analisar as características extraídas da nova imagem e associá-las à classe correspondente.

É importante ressaltar que o desempenho do modelo de classificação precisa ser verificado. Métricas como acurácia, precisão, recall e F1-score são utilizadas para avaliar o desempenho do modelo. Essas métricas ajudam a entender se o modelo está classificando corretamente as imagens e se ele é capaz de generalizar para novas imagens.

> "Legal Murilo, mas e como que eu faço para implementar tudo isso?"

Ótima pergunta! Vamos realizar essa implementação em conjunto. Para isso, vamos precisar de algumas coisas para trabalhar:

1. Um ambiente virtual Python para instalar as bibliotecas necessárias.

```bash
# Pessoal vamos criar um ambiente virtual para instalar as bibliotecas necessárias
# Vamos criar um diretório para nossa solução
mkdir visao-computacional
cd visao-computacional
# Agora vamos criar o ambiente virtual - Mac e Linux
python3 -m venv venv
# Vamos ativar o ambiente virtual - Mac e Linux
source venv/bin/activate
```

2. Vamos instalar as bibliotecas necessárias para o projeto.

```bash
# Agora vamos instalar as bibliotecas necessárias para o projeto
python3 -m pip install opencv-python
python3 -m pip install matplotlib
python3 -m pip install scikit-learn
```

3. Vamos criar um diretório para armazenar as imagens que vamos utilizar no projeto.

```bash
# Agora vamos criar um diretório para armazenar as imagens que vamos utilizar no projeto
mkdir images
```

Dentro do diretório `images`, vamos colocar as imagens que vamos utilizar para o projeto. Para isso, vou deixar as imagens aqui para vocês:

<img  src={require('/img/compvis/tampinhas_01.jpeg').default} alt="Diagrama Visão Computacional Clássica" 
style={{marginLeft:'auto', marginRight:'auto', display:'block', width:'60%'}} />
<br />
<img  src={require('/img/compvis/tampinhas_02.jpeg').default} alt="Diagrama Visão Computacional Clássica" 
style={{marginLeft:'auto', marginRight:'auto', display:'block', width:'60%'}} />
<br />
<img  src={require('/img/compvis/tampinhas_03.jpeg').default} alt="Diagrama Visão Computacional Clássica" 
style={{marginLeft:'auto', marginRight:'auto', display:'block', width:'60%'}} />
<br />
<img  src={require('/img/compvis/tampinhas_04.jpeg').default} alt="Diagrama Visão Computacional Clássica" 
style={{marginLeft:'auto', marginRight:'auto', display:'block', width:'60%'}} />
<br />
<img  src={require('/img/compvis/tampinhas_05.jpeg').default} alt="Diagrama Visão Computacional Clássica" 
style={{marginLeft:'auto', marginRight:'auto', display:'block', width:'60%'}} />
<br />
<img  src={require('/img/compvis/tampinhas_06.jpeg').default} alt="Diagrama Visão Computacional Clássica" 
style={{marginLeft:'auto', marginRight:'auto', display:'block', width:'60%'}} />
<br />
<img  src={require('/img/compvis/tampinhas_07.jpeg').default} alt="Diagrama Visão Computacional Clássica" 
style={{marginLeft:'auto', marginRight:'auto', display:'block', width:'60%'}} />
<br />
<img  src={require('/img/compvis/tampinhas_08.jpeg').default} alt="Diagrama Visão Computacional Clássica" 
style={{marginLeft:'auto', marginRight:'auto', display:'block', width:'60%'}} />
<br />
<img  src={require('/img/compvis/tampinhas_09.jpeg').default} alt="Diagrama Visão Computacional Clássica" 
style={{marginLeft:'auto', marginRight:'auto', display:'block', width:'60%'}} />
<br />
<img  src={require('/img/compvis/tampinhas_10.jpeg').default} alt="Diagrama Visão Computacional Clássica" 
style={{marginLeft:'auto', marginRight:'auto', display:'block', width:'60%'}} />
<br />
<img  src={require('/img/compvis/tampinhas_11.jpeg').default} alt="Diagrama Visão Computacional Clássica" 
style={{marginLeft:'auto', marginRight:'auto', display:'block', width:'60%'}} />
<br />

## 2. Etapa de Pré-processamento

Vamos lá, agora já temos o nosso ambiente virtual criado, as bibliotecas instaladas e as imagens que vamos processar. Agora vamos iniciar a nossa etapa de carregamento das imagens. Para isso, vamos criar um primeiro arquivo chamado `carregamento.py` e vamos colocar o seguinte código nele:

```python
import cv2
import matplotlib.pyplot as plt
import os
import numpy as np

# Definindo o caminho para as imagens
caminho_imagens = 'images/'
# Definindo o tamanho da imagem
tamanho_imagem = (200, 200)
# Função para carregar as imagens
def carregar_imagens(caminho_imagens):
    imagens = []
    for arquivo in os.listdir(caminho_imagens):
        if arquivo.endswith('.jpeg'):
            imagem = cv2.imread(os.path.join(caminho_imagens, arquivo))
            imagem = cv2.resize(imagem, tamanho_imagem)
            imagens.append(imagem)
    return imagens
# Função para exibir as imagens
def exibir_imagens(imagens):
    # Determina o número de linhas e colunas para exibir as imagens
    total_colunas = len(imagens) // 2
    total_linhas = len(imagens) // total_colunas
    # Se o número de imagens não for divisível pelo número de colunas, adiciona mais uma linha
    if len(imagens) % total_colunas != 0:
        total_linhas += 1
    
    for i, imagem in enumerate(imagens):
        plt.subplot(total_colunas, total_linhas, i + 1)
        plt.imshow(cv2.cvtColor(imagem, cv2.COLOR_BGR2RGB))
        plt.axis('off')
    plt.show()

# Carregando as imagens
imagens = carregar_imagens(caminho_imagens)
# Exibindo as imagens
exibir_imagens(imagens)
```