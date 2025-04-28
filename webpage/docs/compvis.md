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

### 2.4 Filtro de Média

O filtro de média é um filtro linear que calcula a média dos valores dos pixels vizinhos e atribui esse valor ao pixel central. Isso resulta em um efeito de suavização na imagem, reduzindo o ruído e melhorando a qualidade da imagem. Vamos verificar como ele pode ser implementado utilizando o OpenCV.

```python showLineNumbers
import cv2
import matplotlib.pyplot as plt
import os
import numpy as np

# Definindo o caminho para as imagens
caminho_imagens = 'imagens/tampinhas_01.jpeg'

# Abre a imagem
imagem = cv2.imread(caminho_imagens)

# Redimensiona a imagem
imagem = cv2.resize(imagem, (512, 512))

# Converte a imagem para escala de cinza
imagem_cinza = cv2.cvtColor(imagem, cv2.COLOR_BGR2GRAY)

# Aplica o filtro de média
imagem_media = cv2.blur(imagem_cinza, (5, 5))

# Exibe a imagem original e a imagem filtrada
plt.subplot(1, 2, 1)
plt.imshow(imagem_cinza, cmap='gray')
plt.title('Imagem Original')
plt.axis('off')
plt.subplot(1, 2, 2)
plt.imshow(imagem_media, cmap='gray')
plt.title('Imagem Filtrada')
plt.axis('off')
plt.show()

```

Pontos importantes a serem observados:

1. Mesmo não sendo um filtro propriamente, a conversão da imagem para escala de cinza é uma etapa importante no pré-processamento de imagens. Isso porque, muitas vezes, as informações de cor não são relevantes para a tarefa de classificação e a conversão para escala de cinza reduz a complexidade da imagem.
2. O filtro de média é aplicado utilizando a função `cv2.blur`, que recebe como parâmetros a imagem e o tamanho do kernel (neste caso, 5x5). O tamanho do kernel determina a quantidade de pixels vizinhos que serão considerados para calcular a média. Um kernel maior resulta em uma suavização mais intensa, enquanto um kernel menor resulta em uma suavização mais leve. Testar outros tamanhos de kernel pode ser interessante para verificar o impacto na imagem.
3. A imagem original e a imagem filtrada são exibidas lado a lado utilizando o `matplotlib`. Isso facilita a comparação entre as duas imagens e permite visualizar o efeito do filtro de média. Para utilizar o `matplotlib`, é necessário importar a biblioteca e utilizar a função `plt.imshow` para exibir a imagem. O parâmetro `cmap='gray'` é utilizado para exibir a imagem em escala de cinza.


:::tip[O que é um filtro de média?]

<iframe width="560" height="315" src="https://www.youtube.com/embed/C_zFhWdM4ic?si=M2bbPh4KwTMW6iWO" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen style={{marginLeft:'auto', marginRight:'auto', display:'block', width:'60%'}}></iframe>
<br />

:::

### 2.5 Filtro Gaussiano

O filtro gaussiano é um filtro linear que aplica uma função gaussiana aos pixels vizinhos, dando mais peso aos pixels mais próximos do pixel central. Isso resulta em um efeito de desfoque suave na imagem. Vamos verificar como ele pode ser implementado utilizando o OpenCV.

:::tip[O que é uma função gaussiana?]

Pessoal minha sugestão para compreender melhor o conceito da função gaussiana como um filtro. A função gaussiana é uma função matemática que descreve a distribuição normal de uma variável aleatória. Ela é caracterizada por sua forma de sino e é amplamente utilizada em estatística, processamento de sinais e aprendizado de máquina. A função gaussiana é definida pela seguinte equação:

$$
f(x) = \frac{1}{\sigma \sqrt{2\pi}} e^{-\frac{(x - \mu)^2}{2\sigma^2}}
$$

Onde:
- $$ f(x) $$: é o valor da função gaussiana para um determinado valor de \(x\).
- $$ \mu $$: é a média da distribuição (o centro do sino).
- $$ \sigma $$: é o desvio padrão da distribuição (a largura do sino).
- $$ \e $$: é a base do logaritmo natural (aproximadamente 2.71828).
- $$ \pi $$ : é a constante matemática pi (aproximadamente 3.14159).

<iframe width="560" height="315" src="https://www.youtube.com/embed/Ud5f1P1lr8Q?si=nbm1a1S-S_xR3rj_" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen style={{marginLeft:'auto', marginRight:'auto', display:'block', width:'60%'}}></iframe>
<br />

:::

```python showLineNumbers
import cv2
import matplotlib.pyplot as plt
import os
import numpy as np

# Definindo o caminho para as imagens
caminho_imagens = 'imagens/tampinhas_01.jpeg'

# Abre a imagem
imagem = cv2.imread(caminho_imagens)

# Redimensiona a imagem
imagem = cv2.resize(imagem, (512, 512))

# Converte a imagem para escala de cinza
imagem_cinza = cv2.cvtColor(imagem, cv2.COLOR_BGR2GRAY)

# Aplica o filtro gaussiano
imagem_gaussiana = cv2.GaussianBlur(imagem_cinza, (5, 5), 0)

# Exibe a imagem original e a imagem filtrada
plt.subplot(1, 2, 1)
plt.imshow(imagem_cinza, cmap='gray')
plt.title('Imagem Original')
plt.axis('off')
plt.subplot(1, 2, 2)
plt.imshow(imagem_gaussiana, cmap='gray')
plt.title('Imagem Filtrada')
plt.axis('off')
plt.show()
```

Pontos importantes a serem observados:

1. O filtro gaussiano é aplicado utilizando a função `cv2.GaussianBlur`, que recebe como parâmetros a imagem, o tamanho do kernel (neste caso, 5x5) e o desvio padrão da distribuição gaussiana (neste caso, 0). O tamanho do kernel e o desvio padrão determinam a quantidade de pixels vizinhos que serão considerados para calcular a média ponderada. Um kernel maior resulta em uma suavização mais intensa, enquanto um kernel menor resulta em uma suavização mais leve. Já o desvio padrão determina a largura do sino da função gaussiana. Um desvio padrão maior resulta em uma suavização mais intensa, enquanto um desvio padrão menor resulta em uma suavização mais leve.

### 2.6 Filtro de Mediana

O filtro de mediana é um filtro não linear que calcula a mediana dos valores dos pixels vizinhos e atribui esse valor ao pixel central. Isso resulta em um efeito de suavização que preserva as bordas da imagem. Vamos verificar como ele pode ser implementado utilizando o OpenCV.

```python showLineNumbers
import cv2
import matplotlib.pyplot as plt
import os
import numpy as np

# Definindo o caminho para as imagens
caminho_imagens = 'imagens/tampinhas_01.jpeg'
# Abre a imagem
imagem = cv2.imread(caminho_imagens)
# Redimensiona a imagem
imagem = cv2.resize(imagem, (512, 512))
# Converte a imagem para escala de cinza
imagem_cinza = cv2.cvtColor(imagem, cv2.COLOR_BGR2GRAY)
# Aplica o filtro de mediana
imagem_mediana = cv2.medianBlur(imagem_cinza, 5)
# Exibe a imagem original e a imagem filtrada
plt.subplot(1, 2, 1)
plt.imshow(imagem_cinza, cmap='gray')
plt.title('Imagem Original')
plt.axis('off')
plt.subplot(1, 2, 2)
plt.imshow(imagem_mediana, cmap='gray')
plt.title('Imagem Filtrada')
plt.axis('off')
plt.show()
```

Pontos importantes a serem observados:

1. O filtro de mediana é aplicado utilizando a função `cv2.medianBlur`, que recebe como parâmetros a imagem e o tamanho do kernel (neste caso, 5). O tamanho do kernel determina a quantidade de pixels vizinhos que serão considerados para calcular a mediana. Um kernel maior resulta em uma suavização mais intensa, enquanto um kernel menor resulta em uma suavização mais leve. Testar outros tamanhos de kernel pode ser interessante para verificar o impacto na imagem.

2. O filtro de mediana é especialmente útil para remover ruídos impulsivos, como o ruído sal e pimenta, que podem afetar a qualidade da imagem. Ele preserva as bordas da imagem, o que é importante para tarefas de segmentação e extração de características.

Aqui pessoal, já temos três filtros que podem ser utilizados para melhorar a qualidade das imagens. Vale destacar que o filtro de média e o filtro gaussiano são filtros lineares, enquanto o filtro de mediana é um filtro não linear. A escolha do filtro a ser utilizado depende do tipo de ruído presente na imagem e do efeito desejado. Como regra geral, o filtro de mediana é mais eficaz na remoção de ruídos impulsivos, enquanto os filtros de média e gaussiano são mais eficazes na suavização geral da imagem.

Vale destacar que existem outros filtros que podem ser utilizados para melhorar a qualidade das imagens, como o filtro de Sobel, o filtro de Laplace, entre outros. Esses filtros são utilizados para detectar bordas e contornos na imagem e podem ser utilizados em conjunto com os filtros de média, gaussiano e mediana para melhorar ainda mais a qualidade da imagem.

Agora vamos estudar alguns filtros que podem ser utilizados para detectar bordas e contornos na imagem. Esses filtros são utilizados para destacar as bordas e contornos da imagem, o que pode ser útil para tarefas de segmentação e extração de características.

### 2.7 Conceito de Gradiente

O gradiente é uma medida da variação de intensidade de uma imagem em relação a uma direção específica. Ele é utilizado para detectar bordas e contornos na imagem, pois as bordas são regiões onde há uma mudança abrupta na intensidade dos pixels. O gradiente é calculado utilizando operadores de derivada, como o operador Sobel, o operador Prewitt e o operador Laplace.

:::tip[O que é um gradiente?]

Pessoal aqui tem uma definição mais formal do que é um gradiente. O gradiente de uma função escalar \(f(x, y)\) em duas dimensões é um vetor que aponta na direção da maior taxa de variação da função e tem magnitude igual à taxa de variação máxima. Eu sei que não é uma leitura fácil, aqui é o ponto de ver um vídeo pesado de conceito, mas vale a pena colocar energia para compreender o conceito. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/Dl5lPdoCXi8?si=CyXRbkRvDJ6Y3s88" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen style={{marginLeft:'auto', marginRight:'auto', display:'block', width:'60%'}}></iframe>
<br />

<iframe width="560" height="315" src="https://www.youtube.com/embed/lOEBsQodtEQ?si=7nuvFcbnPIoAevXn" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen style={{marginLeft:'auto', marginRight:'auto', display:'block', width:'60%'}}></iframe>
<br />

:::

Agora vamos aplicar esses filtros para verificar como eles detectam bordas e contornos na imagem.

### 2.8 Filtro de Sobel

O filtro de Sobel é um operador de derivada que calcula o gradiente da imagem em duas direções: horizontal e vertical. Ele é utilizado para detectar bordas e contornos na imagem. Algumas características do filtro de Sobel:

- O filtro de Sobel é um operador de derivada que calcula o gradiente da imagem em duas direções: horizontal e vertical.
- Ele utiliza duas matrizes de convolução (kernels) para calcular o gradiente: uma para a direção horizontal e outra para a direção vertical.
- O filtro de Sobel é mais sensível a bordas diagonais do que o filtro de Prewitt, o que pode ser útil em algumas aplicações.
- O filtro de Sobel é amplamente utilizado em processamento de imagens e visão computacional para detectar bordas e contornos. Contudo, ele não é aplicado em imagens coloridas, apenas em imagens em escala de cinza.
- O filtro de Sobel é utilizado em conjunto com outros filtros, como o filtro gaussiano, para melhorar a qualidade da imagem antes de aplicar o filtro de Sobel. Isso ajuda a reduzir o ruído e melhorar a detecção de bordas. Ele é um filtro bastante sensível a ruídos, portanto, é importante aplicar um filtro de suavização antes de aplicar o filtro de Sobel.

:::tip[O que é um operador de Sobel?]

<iframe width="560" height="315" src="https://www.youtube.com/embed/uihBwtPIBxM?si=ETdy8nnpaX_ZADnm" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen style={{marginLeft:'auto', marginRight:'auto', display:'block', width:'60%'}}></iframe>
<br />

:::

Vamos verificar como ele pode ser implementado utilizando o OpenCV.

```python showLineNumbers
import cv2
import matplotlib.pyplot as plt
import os
import numpy as np

# Definindo o caminho para as imagens
caminho_imagens = 'imagens/tampinhas_01.jpeg'
# Abre a imagem
imagem = cv2.imread(caminho_imagens)
# Redimensiona a imagem
imagem = cv2.resize(imagem, (512, 512))
# Converte a imagem para escala de cinza
imagem_cinza = cv2.cvtColor(imagem, cv2.COLOR_BGR2GRAY)
# Aplica o filtro gaussiano
imagem_gaussiana = cv2.GaussianBlur(imagem_cinza, (5, 5), 0)
# Aplica o filtro de Sobel
sobel_x = cv2.Sobel(imagem_gaussiana, cv2.CV_64F, 1, 0, ksize=5)
sobel_y = cv2.Sobel(imagem_gaussiana, cv2.CV_64F, 0, 1, ksize=5)
# Calcula a magnitude do gradiente
magnitude = np.sqrt(sobel_x**2 + sobel_y**2)
# Normaliza a magnitude do gradiente
magnitude = cv2.normalize(magnitude, None, 0, 255, cv2.NORM_MINMAX)
# Exibe a imagem original e a imagem filtrada
plt.subplot(1, 2, 1)
plt.imshow(imagem_gaussiana, cmap='gray')
plt.title('Imagem Original')
plt.axis('off')
plt.subplot(1, 2, 2)
plt.imshow(magnitude, cmap='gray')
plt.title('Imagem Filtrada')
plt.axis('off')
plt.show()
```

Pontos importantes a serem observados:

1. O filtro de Sobel é aplicado utilizando a função `cv2.Sobel`, que recebe como parâmetros a imagem, o tipo de dado da imagem (neste caso, `cv2.CV_64F`), as derivadas em relação às direções x e y (neste caso, 1 e 0 para a direção x e 0 e 1 para a direção y) e o tamanho do kernel (neste caso, 5). O tamanho do kernel determina a quantidade de pixels vizinhos que serão considerados para calcular o gradiente. Um kernel maior resulta em uma detecção de bordas mais intensa, enquanto um kernel menor resulta em uma detecção de bordas mais leve. Testar outros tamanhos de kernel pode ser interessante para verificar o impacto na imagem.
2. A magnitude do gradiente é calculada utilizando a fórmula da raiz quadrada da soma dos quadrados das derivadas em relação às direções x e y. Isso resulta em uma imagem que representa a intensidade do gradiente em cada pixel.
3. A magnitude do gradiente é normalizada utilizando a função `cv2.normalize`, que recebe como parâmetros a imagem, o valor mínimo e máximo da normalização e o tipo de normalização (neste caso, `cv2.NORM_MINMAX`). Isso resulta em uma imagem que representa a intensidade do gradiente em cada pixel, com valores entre 0 e 255.

### 2.9 Filtro de Canny

O filtro de Canny é um operador de detecção de bordas que utiliza uma série de etapas para detectar bordas na imagem. Ele é utilizado em processamento de imagens e visão computacional para detectar bordas e contornos, devolvendo para nós a localização das bordas e não focando em sua dimensão (o quão espessa é uma borda, por exemplo). Algumas características do filtro de Canny:

- O filtro de Canny é um operador de detecção de bordas que utiliza uma série de etapas para detectar bordas na imagem.
- Ele utiliza um filtro gaussiano para suavizar a imagem e reduzir o ruído.
- Utiliza o operador de Sobel para calcular o gradiente da imagem em duas direções: horizontal e vertical.
- Ele utiliza a supressão de não-máximos para eliminar pixels que não são bordas.
- Utiliza a histerese para conectar bordas fracas a bordas fortes.
- Utilizado em processamento de imagens e visão computacional para detectar bordas e contornos. Ele é um filtro bastante sensível a ruídos, portanto, é importante aplicar um filtro de suavização antes de aplicar o filtro de Canny. O filtro gaussiano é o mais utilizado para suavizar a imagem antes de aplicar o filtro de Canny.

:::tip[O que é um operador de Canny?]

<iframe width="560" height="315" src="https://www.youtube.com/embed/sRFM5IEqR2w?si=hO1sZYlARQyqywrZ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen style={{marginLeft:'auto', marginRight:'auto', display:'block', width:'60%'}}></iframe>
<br />

:::

Vamos a sua implementação utilizando o OpenCV.

```python showLineNumbers
import cv2
import matplotlib.pyplot as plt
import os
import numpy as np

# Definindo o caminho para as imagens
caminho_imagens = 'imagens/tampinhas_01.jpeg'
# Abre a imagem
imagem = cv2.imread(caminho_imagens)
# Redimensiona a imagem
imagem = cv2.resize(imagem, (512, 512))
# Converte a imagem para escala de cinza
imagem_cinza = cv2.cvtColor(imagem, cv2.COLOR_BGR2GRAY)
# Aplica o filtro gaussiano
imagem_gaussiana = cv2.GaussianBlur(imagem_cinza, (5, 5), 0)
# Aplica o filtro de Canny
imagem_canny = cv2.Canny(imagem_gaussiana, 100, 200)
# Exibe a imagem original e a imagem filtrada
plt.subplot(1, 2, 1)
plt.imshow(imagem_gaussiana, cmap='gray')
plt.title('Imagem Original')
plt.axis('off')
plt.subplot(1, 2, 2)
plt.imshow(imagem_canny, cmap='gray')
plt.title('Imagem Filtrada')
plt.axis('off')
plt.show()
```

Pontos importantes a serem observados:

1. O filtro de Canny é aplicado utilizando a função `cv2.Canny`, que recebe como parâmetros a imagem, os limites inferior e superior para a histerese (neste caso, 100 e 200). Os limites inferior e superior determinam quais bordas serão consideradas fortes e fracas. Bordas fortes são aquelas que têm uma intensidade de gradiente maior que o limite superior, enquanto bordas fracas são aquelas que têm uma intensidade de gradiente menor que o limite inferior. Bordas fracas que estão conectadas a bordas fortes são consideradas bordas válidas.
2. O filtro de Canny é um filtro bastante sensível a ruídos, portanto, é importante aplicar um filtro de suavização antes de aplicar o filtro de Canny. O filtro gaussiano é o mais utilizado para suavizar a imagem antes de aplicar o filtro de Canny.

### 2.10 Operação de Segmentação

O objetivo da segmentação é dividir a imagem em regiões homogêneas, ou seja, regiões que possuem características semelhantes. A segmentação é uma etapa importante no processamento de imagens e visão computacional, pois permite extrair informações relevantes da imagem e facilitar a análise.

A segmentação pode ser realizada utilizando diferentes técnicas, como segmentação por cor, segmentação por textura, segmentação por forma, entre outras. A escolha da técnica de segmentação depende do tipo de imagem e do objetivo da análise.

:::tip[O que é segmentação?]

<iframe width="560" height="315" src="https://www.youtube.com/embed/BA00xTv5-Z4?si=fTXF8sZexY0BU88Q" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen style={{marginLeft:'auto', marginRight:'auto', display:'block', width:'60%'}}></iframe>
<br />

:::

Vamos avaliar a implementação de um código para realizar a segmentação de uma imagem por thresholding. O thresholding é uma técnica de segmentação que utiliza um valor de limiar para dividir a imagem em duas regiões: uma região com intensidade de pixel acima do limiar e outra região com intensidade de pixel abaixo do limiar. Essa técnica é amplamente utilizada em processamento de imagens e visão computacional para segmentar objetos em imagens.

```python showLineNumbers

import cv2
import matplotlib.pyplot as plt
import os
import numpy as np

# Definindo o caminho para as imagens
caminho_imagens = 'imagens/tampinhas_01.jpeg'
# Abre a imagem
imagem = cv2.imread(caminho_imagens)
# Redimensiona a imagem
imagem = cv2.resize(imagem, (512, 512))
# Converte a imagem para escala de cinza
imagem_cinza = cv2.cvtColor(imagem, cv2.COLOR_BGR2GRAY)
# Aplica o filtro gaussiano
imagem_gaussiana = cv2.GaussianBlur(imagem_cinza, (5, 5), 0)
# Aplica o filtro de Canny
imagem_canny = cv2.Canny(imagem_gaussiana, 100, 200)
# Aplica o thresholding
_, imagem_threshold = cv2.threshold(imagem_canny, 127, 255, cv2.THRESH_BINARY)
# Exibe a imagem original e a imagem filtrada
plt.subplot(1, 2, 1)
plt.imshow(imagem_gaussiana, cmap='gray')
plt.title('Imagem Original')
plt.axis('off')
plt.subplot(1, 2, 2)
plt.imshow(imagem_threshold, cmap='gray')
plt.title('Imagem Filtrada')
plt.axis('off')
plt.show()

```

Pontos importantes a serem observados:
1. O thresholding é aplicado utilizando a função `cv2.threshold`, que recebe como parâmetros a imagem, o valor do limiar (neste caso, 127), o valor máximo (neste caso, 255) e o tipo de thresholding (neste caso, `cv2.THRESH_BINARY`). O valor do limiar determina quais pixels serão considerados acima ou abaixo do limiar. Pixels com intensidade acima do limiar são definidos como 255 (branco) e pixels com intensidade abaixo do limiar são definidos como 0 (preto). Testar outros valores de limiar pode ser interessante para verificar o impacto na imagem.
2. Existem outros tipos de thresholding, como o `cv2.THRESH_BINARY_INV`, que inverte os valores do thresholding binário, e o `cv2.THRESH_TRUNC`, que trunca os valores acima do limiar. Esses tipos de thresholding podem ser utilizados dependendo do tipo de imagem e do objetivo da análise.
3. O thresholding é uma técnica de segmentação simples, mas eficaz, que pode ser utilizada para segmentar objetos em imagens. No entanto, ele pode ser sensível a ruídos e variações de iluminação na imagem. Para melhorar a qualidade da segmentação, é recomendável aplicar um filtro de suavização antes de aplicar o thresholding.
4. O thresholding pode ser utilizado em conjunto com outras técnicas de segmentação, como a segmentação por cor e a segmentação por textura, para melhorar a qualidade da segmentação. Essas técnicas podem ser utilizadas para extrair informações relevantes da imagem e facilitar a análise.

### 2.11 Encontrando Contornos

Os contornos são linhas que delimitam a forma de um objeto em uma imagem. Eles são utilizados para representar a forma e a estrutura dos objetos na imagem. A detecção de contornos é uma etapa importante no processamento de imagens e visão computacional, pois permite extrair informações relevantes da imagem e facilitar a análise.

A detecção de contornos pode ser realizada utilizando a função `cv2.findContours`, que recebe como parâmetros a imagem, o modo de detecção de contornos e o método de aproximação de contornos. O modo de detecção de contornos determina como os contornos serão detectados na imagem, enquanto o método de aproximação de contornos determina como os contornos serão aproximados.

A função `cv2.findContours` retorna uma lista de contornos detectados na imagem, onde cada contorno é representado por um array de pontos que delimitam a forma do objeto. Esses contornos podem ser utilizados para extrair informações relevantes da imagem, como a área, o perímetro e a forma do objeto.

Vamos verificar como encontrar os contornos na imagem utilizando o OpenCV.

```python showLineNumbers
import cv2
import matplotlib.pyplot as plt
import os
import numpy as np
# Definindo o caminho para as imagens
caminho_imagens = 'imagens/tampinhas_01.jpeg'
# Abre a imagem
imagem = cv2.imread(caminho_imagens)
# Redimensiona a imagem
imagem = cv2.resize(imagem, (512, 512))
# Converte a imagem para escala de cinza
imagem_cinza = cv2.cvtColor(imagem, cv2.COLOR_BGR2GRAY)
# Aplica o filtro gaussiano
imagem_gaussiana = cv2.GaussianBlur(imagem_cinza, (5, 5), 0)
# Aplica o filtro de Canny
imagem_canny = cv2.Canny(imagem_gaussiana, 100, 200)
# Aplica o thresholding
_, imagem_threshold = cv2.threshold(imagem_canny, 127, 255, cv2.THRESH_BINARY)
# Encontra os contornos
contornos, _ = cv2.findContours(imagem_threshold, cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_SIMPLE)
# Desenha os contornos na imagem original
imagem_contornos = cv2.drawContours(imagem.copy(), contornos, -1, (0, 255, 0), 3)
# Exibe a imagem original e a imagem filtrada
plt.subplot(1, 2, 1)
plt.imshow(imagem_gaussiana, cmap='gray')
plt.title('Imagem Original')
plt.axis('off')
plt.subplot(1, 2, 2)
plt.imshow(imagem_contornos, cmap='gray')
plt.title('Imagem Filtrada')
plt.axis('off')
plt.show()
```

Pontos importantes a serem observados:

1. A função `cv2.findContours` é utilizada para encontrar os contornos na imagem, recebendo como parâmetros a imagem, o modo de detecção de contornos (neste caso, `cv2.RETR_EXTERNAL`, que detecta apenas os contornos externos) e o método de aproximação de contornos (neste caso, `cv2.CHAIN_APPROX_SIMPLE`, que simplifica os contornos).
2. A função `cv2.drawContours` é utilizada para desenhar os contornos na imagem original, recebendo como parâmetros a imagem, a lista de contornos, o índice do contorno (-1 para desenhar todos os contornos), a cor (neste caso, verde) e a espessura da linha (neste caso, 3).
3. Os contornos detectados podem ser utilizados para extrair informações relevantes da imagem, como a área, o perímetro e a forma do objeto. Essas informações podem ser utilizadas para realizar tarefas de classificação e reconhecimento de objetos.

## 3. Etapa de Extração de Características

Legal, agora temos nossa imagem pré-processada e segmentada. A próxima etapa é a extração de características. A extração de características é uma etapa importante no processamento de imagens e visão computacional, pois permite extrair informações relevantes da imagem e facilitar a análise.

A extração de características pode ser realizada utilizando diferentes técnicas, como extração de características de cor, textura e forma. A escolha da técnica de extração de características depende do tipo de imagem e do objetivo da análise. Ela podo acontecer com a imagem original ou com a imagem segmentada. A imagem segmentada pode conter informações mais relevantes para a tarefa de classificação, pois elimina informações desnecessárias da imagem original.

Vamos avaliar um exemplo de extração de características utilizando o OpenCV:

```python showLineNumbers
import cv2
import matplotlib.pyplot as plt
import os
import numpy as np
# Definindo o caminho para as imagens
caminho_imagens = 'imagens/tampinhas_01.jpeg'
# Abre a imagem
imagem = cv2.imread(caminho_imagens)
# Redimensiona a imagem
imagem = cv2.resize(imagem, (512, 512))
# Converte a imagem para escala de cinza
imagem_cinza = cv2.cvtColor(imagem, cv2.COLOR_BGR2GRAY)
# Aplica o filtro gaussiano
imagem_gaussiana = cv2.GaussianBlur(imagem_cinza, (5, 5), 0)
# Aplica o filtro de Canny
imagem_canny = cv2.Canny(imagem_gaussiana, 100, 200)
# Aplica o thresholding
_, imagem_threshold = cv2.threshold(imagem_canny, 127, 255, cv2.THRESH_BINARY)
# Encontra os contornos
contornos, _ = cv2.findContours(imagem_threshold, cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_SIMPLE)

# Remove os contornos pequenos
contornos = [c for c in contornos if cv2.contourArea(c) > 100]

# Desenha os contornos na imagem original
imagem_contornos = cv2.drawContours(imagem.copy(), contornos, -1, (0, 255, 0), 3)
# Calcula a área e o perímetro dos contornos
for contorno in contornos:
    area = cv2.contourArea(contorno)
    perimetro = cv2.arcLength(contorno, True)
    print(f'Área: {area}, Perímetro: {perimetro}')
# Exibe a imagem original e a imagem filtrada
plt.subplot(1, 2, 1)
plt.imshow(imagem_gaussiana, cmap='gray')
plt.title('Imagem Original')
plt.axis('off')
plt.subplot(1, 2, 2)
plt.imshow(imagem_contornos, cmap='gray')
plt.title('Imagem Filtrada')
plt.axis('off')
plt.show()
```

Pontos importantes a serem observados:
1. A função `cv2.contourArea` é utilizada para calcular a área dos contornos, enquanto a função `cv2.arcLength` é utilizada para calcular o perímetro dos contornos. Essas informações podem ser utilizadas para realizar tarefas de classificação e reconhecimento de objetos.
2. A área e o perímetro dos contornos são impressos no console, mas podem ser armazenados em uma lista ou array para serem utilizados posteriormente na análise.
3. A extração de características pode ser realizada utilizando diferentes técnicas, como extração de características de cor, textura e forma. A escolha da técnica de extração de características depende do tipo de imagem e do objetivo da análise.
4. A extração de características pode ser realizada em conjunto com outras técnicas de processamento de imagens, como a segmentação e a detecção de bordas, para melhorar a qualidade da análise. Essas técnicas podem ser utilizadas para extrair informações relevantes da imagem e facilitar a análise.






---

:::warning[ATENÇÃO]

Pessoal eu vou terminar ainda de curar o material. Por hora, peço que vocês verifiquem esse material de estudo nas referências.
Obrigado!

:::

## x. Referências

- Playlist de pré-processamento: https://www.youtube.com/watch?v=vqRzOGg9mi8&list=PL2zRqk16wsdorCSZ5GWZQr1EMWXs2TDeu

- https://www.youtube.com/watch?v=ZSqg-fZJ9tQ

- https://www.youtube.com/watch?v=KkM5skOXZYQ

- https://www.youtube.com/watch?v=88HdqNDQsEk&list=PLqyxJaY2tD7hRV3atvl2LzKz6eWXcq_hi

- https://docs.opencv.org/3.4/dc/d88/tutorial_traincascade.html