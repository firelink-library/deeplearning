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

```python showLineNumbers
import cv2
import matplotlib.pyplot as plt
import os
import numpy as np

# Definindo o caminho para as imagens
caminho_imagens = 'imagens/'
# Definindo o tamanho da imagem
tamanho_imagem = (512, 512)
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
    print(total_linhas, total_colunas)
    # Se o número de imagens não for divisível pelo número de colunas, adiciona mais uma linha
    if len(imagens) % total_colunas != 0:
        total_colunas += 1
    
    for i, imagem in enumerate(imagens):
        plt.subplot(total_linhas, total_colunas, i + 1)
        plt.imshow(cv2.cvtColor(imagem, cv2.COLOR_BGR2RGB))
        plt.axis('off')
    plt.show()

# Carregando as imagens
imagens = carregar_imagens(caminho_imagens)
# Exibindo as imagens
exibir_imagens(imagens)
```

Pessoal vamos aqui avaliar o que está acontecendo no nosso código:
1. Estamos importando as bibliotecas necessárias para o nosso projeto: `cv2` para manipulação de imagens, `matplotlib.pyplot` para exibição das imagens, `os` para manipulação de arquivos e diretórios e `numpy` para manipulação de arrays.
2. Definimos o caminho para as imagens que vamos utilizar no projeto e o tamanho da imagem que vamos utilizar. No nosso caso, estamos utilizando o diretório `imagens` e o tamanho de 512x512 pixels para as imagens. Aqui tem um ponto interessante para avaliar: o tamanho da imagem pode influenciar no desempenho do nosso modelo de classificação. Imagens muito grandes podem levar mais tempo para serem processadas e podem aumentar o tempo de treinamento do modelo. Por outro lado, imagens muito pequenas podem perder informações importantes. Portanto, é importante encontrar um equilíbrio entre o tamanho da imagem e a qualidade da imagem. Outro ponto importante de se observar é por onde o programa será executado. No caso do exemplo, o programa está dentro de um diretório que está no mesmo nível que o diretório `imagens`. Desta forma, o terminal para executar o programa deve estar em um ponto que ele `consiga acessar o diretório imagens`. No caso do exemplo, ele está dentro do diretório `visao-computacional`, portanto, para executar o programa, utilizar o comando `python3 visao-computacional/carregamento.py`.
3. Criamos a função `carregar_imagens` que vai carregar as imagens do diretório `imagens`, redimensioná-las para o tamanho definido e armazená-las em uma lista.
4. Criamos a função `exibir_imagens` que vai exibir as imagens carregadas. Aqui estamos utilizando o `matplotlib` para exibir as imagens. O `matplotlib` é uma biblioteca muito poderosa para visualização de dados e pode ser utilizada para exibir gráficos, imagens, entre outros. No nosso caso, estamos utilizando o `imshow` para exibir as imagens e o `axis('off')` para remover os eixos das imagens. Estamos utilizando também o `subplot` para exibir as imagens em um grid. O número de linhas e colunas do grid é determinado pelo número de imagens carregadas. Se o número de imagens não for divisível pelo número de colunas, adicionamos mais uma linha.
5. Por fim, estamos chamando a função `carregar_imagens` para carregar as imagens do diretório `imagens` e a função `exibir_imagens` para exibir as imagens carregadas.

Agora, vamos verificar um pouco sobre as ferramentas de pré-processamento que podemos utilizar para melhorar a qualidade das iamgens. Para isso, vamos compreender quais são os principais filtros que podemos aplicar nas imagens.

:::danger[EXTREMAMENTE IMPORTANTE]

Pessoal só para deixar claro uma etapa muito importante: todo o pré-processamento que vamos utilizar em nossas imagens, deve ser aplicado no momento do treinamento do modelo, na validação do modelo e quando ele estiver em produção. Isso é necessário para garantir que o modelo esteja sempre recebendo as imagens no mesmo formato e com as mesmas características. Caso contrário, o modelo pode apresentar resultados inesperados e não conseguir classificar as imagens corretamente.

<iframe width="560" height="315" src="https://www.youtube.com/embed/VMeDbP8gX80?si=Z7GXvNkG4xvX5kh4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen style={{marginLeft:'auto', marginRight:'auto', display:'block', width:'60%'}}></iframe>

:::

### 2.1 Filtros de Pré-processamento

Os filtros de pré-processamento de imagens são técnicas aplicadas às imagens antes da análise ou extração de informações. A importância deles reside em:

- **Redução de ruído**: O ruído é uma variação aleatória de brilho ou cor nas imagens. Filtros como o Gaussiano ou a mediana podem diminuir essa variação, resultando em imagens mais nítidas e facilitando etapas subsequentes.
- **Realce de características**: Alguns filtros podem destacar bordas, contornos ou outras características relevantes, o que simplifica a segmentação ou a extração de informações.
- **Conversão de espaço de cores**: Alterar o espaço de cores, por exemplo, para escala de cinza ou HSV, pode simplificar o processamento, dependendo da tarefa.
- **Normalização**: Ajustar a intensidade dos pixels dentro de uma faixa específica auxilia na consistência do processamento.
- **Operações morfológicas**: Filtros como erosão e dilatação são úteis para remover pequenas irregularidades ou conectar regiões segmentadas.

Esses filtros adaptam a imagem para torná-la mais adequada para análise posterior, melhorando a qualidade dos resultados em tarefas como segmentação, extração de características ou classificação.

Vamos agora verificar alguns filtros que podemos aplicar nas imagens e quando eles podem ser utilizados.

### 2.2 Compreendendo o conceito de Filtros

Para iniciarmos nosso jornada com os filtros, primeiro vamos compreender o que eles são. Podemos entender os filtros como uma pequena matriz (o kernel) que desliza sobre a imagem, realizando uma operação matemática em cada vizinhança de pixels para calcular o novo valor do pixel central.

<img  src="https://www.opto-e.com/media/basics/software/3D_Convolution_Animation.gif" alt="Diagrama Visão Computacional Clássica" 
style={{marginLeft:'auto', marginRight:'auto', display:'block', width:'80%'}} />
<br />

Como podemos observar na imagem acima, o filtro (kernel) desliza sobre a imagem e realiza uma operação matemática em cada vizinhança de pixels para calcular o novo valor do pixel central. Essa operação pode ser uma soma, uma média, uma multiplicação, entre outras. O resultado dessa operação é o novo valor do pixel central.

O tipo dessa operação depende do filtro que estamos utilizando. Existem vários tipos de filtros, cada um com uma finalidade específica. Podemos classificá-los em duas categorias principais: **filtros lineares** e **filtros não lineares**.

Os **filtros lineares** são aqueles que realizam uma operação linear sobre os pixels da imagem. Isso significa que o novo valor do pixel central é uma combinação linear dos valores dos pixels vizinhos. Os filtros lineares mais comuns são os filtros de média e os filtros de Gauss. Em geral, são utilizados para suavizar a imagem, reduzindo o ruído e melhorando a qualidade da imagem. O filtro de média, por exemplo, calcula a média dos valores dos pixels vizinhos e atribui esse valor ao pixel central. O filtro de Gauss, por sua vez, aplica uma função gaussiana aos pixels vizinhos, dando mais peso aos pixels mais próximos do pixel central. Isso resulta em um efeito de desfoque suave na imagem.

<img  src="https://image5.slideserve.com/9535829/linear-filters-examples-l.jpg" alt="Diagrama Visão Computacional Clássica" 
style={{marginLeft:'auto', marginRight:'auto', display:'block', width:'60%'}} />
<br />

Os **filtros não lineares**, por outro lado, realizam uma operação não linear sobre os pixels da imagem. Isso significa que o novo valor do pixel central não é uma combinação linear dos valores dos pixels vizinhos. Os filtros não lineares mais comuns são os filtros de mediana e os filtros de máximo. O filtro de mediana, por exemplo, calcula a mediana dos valores dos pixels vizinhos e atribui esse valor ao pixel central. Isso resulta em um efeito de suavização que preserva as bordas da imagem. O filtro de máximo, por sua vez, atribui o valor máximo dos pixels vizinhos ao pixel central. Isso resulta em um efeito de realce das bordas da imagem.

<img  src="https://pyihub.org/wp-content/uploads/2023/11/Median-filter-in-Image-processing-with-Python-and-OpenCV.png" alt="Diagrama Visão Computacional Clássica" 
style={{marginLeft:'auto', marginRight:'auto', display:'block', width:'60%'}} />
<br />

### 2.3 Aplicando os Filtros

Agora vamos aplicar os filtros que conversamos no nosso conjunto de imagens acima. Antes de colocarmos todos os filtros no nosso pipeline de pré-processamento, vamos criar um arquivo chamado `filtros.py` e investigar cada um dos filtros separadamente. Vamos lá?

:::tip[O que são pipelines?]

Importante conhecer este conceito! Pipelines são sequências de etapas de processamento de dados, onde a saída de uma etapa se torna a entrada da próxima. Eles são bastante utilizados em aprendizado de máquina e ciência de dados para organizar e automatizar o fluxo de trabalho, garantindo que os dados sejam processados de maneira consistente. Em visão computacional, pipelines podem incluir etapas como pré-processamento, extração de características, treinamento de modelos e avaliação.

<iframe width="560" height="315" src="https://www.youtube.com/embed/UdlZGYCzjAo?si=PP2ntMNkOEzdlawv" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen style={{marginLeft:'auto', marginRight:'auto', display:'block', width:'60%'}}></iframe>
<br />

:::

