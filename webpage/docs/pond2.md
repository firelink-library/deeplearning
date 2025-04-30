---
sidebar_position: 12
slug: /pond2
title: Atividade Classificador Customizado de Imagens
---

Este projeto tem por objetivo construir um visualizador de imagens que permita a aplicação de um classificador customizado treinado pelo desenvolvedor. As imagens devem ser exibidas da webcam do usuário ou de um arquivo local, e o classificador deve ser capaz de identificar e classificar as imagens em diferentes categorias.

As categorias que o classificador deve ser capaz de identificar podem incluir, mas não estão limitadas a:
- Animais (cachorros, gatos, pássaros, etc.)
- Objetos (carros, bicicletas, etc.)
- Cenários (praias, montanhas, florestas, etc.)
- Pessoas (adultos, crianças, idosos, etc.)
- Alimentos (frutas, vegetais, pratos prontos, etc.)

O classificador deve ser capaz de lidar com diferentes condições de iluminação e ângulos de visão, e deve ser treinado com um conjunto de dados representativo das categorias mencionadas.

O visualizador deve permitir ao usuário escolher entre usar a webcam ou carregar uma imagem de um arquivo local. O classificador deve ser capaz de processar a imagem e exibir o resultado da classificação na tela, juntamente com a imagem original.

Não é necessário capturar e exibir o vídeo da webcam em tempo real, mas o classificador deve ser capaz de processar imagens estáticas capturadas pela webcam.

O algoritmos classificador pode ser implementado utilizando bibliotecas como o Skit-learn, focar nos algoritmos de visão computacional clássicos, como SVM, Decision Trees, Random Forests, entre outros. O classificador deve ser capaz de lidar com diferentes tamanhos de imagem e deve ser otimizado para garantir um desempenho adequado.

Apresentar no README do projeto uma breve descrição do classificador, incluindo o algoritmo utilizado, as categorias de imagens que ele é capaz de identificar e o conjunto de dados utilizado para o treinamento. Incluir também instruções sobre como executar o projeto e como utilizar o visualizador. Trazer também os dados do desempenho do classificador, como acurácia, precisão e recall, para que o usuário possa entender a eficácia do classificador.

**Requisitos:**

    - O visualizador deve ser implementado em Python, utilizando alguma biblioteca de interface gráfica local, como o [FreeSimpleGUI](https://freesimplegui.readthedocs.io/en/latest/), para a interface gráfica.
    - O carregamento da imagem deve ser feito através de um diálogo de arquivo, permitindo ao usuário escolher a imagem desejada.
    - Também deve ser possível capturar imagens da webcam do usuário.
    - O classificador deve ser capaz de identificar e classificar as imagens em diferentes categorias.

**Padrão de Qualidade:**

    - O código deve estar estruturado de forma clara, legível, modular e construído de acordo com as boas práticas de programação.
    - O visualizador deve ter uma interface amigável e intuitiva, com botões e menus claros para a exibição do resultado do classificador.
    - O visualizador deve ser testado com diferentes imagens para garantir que o classificador funciona corretamente.
    - Todo o projeto deve ser entregue em um repositório do GitHub, com um README claro e conciso, explicando como executar o projeto e suas funcionalidades.
