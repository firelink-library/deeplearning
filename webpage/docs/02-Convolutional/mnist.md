---
sidebar_position: 3
slug: /mnist
title: Visão computacional moderna
---

# Visão computacional com redes neurais

## 1. O dataset MNIST

O vídeo abaixo exemplifica como utilizar redes neurais com camadas densas para
identificar padrões em imagens. Especificamente, o vídeo apresenta como exemplo
o dataset MNIST.

<div style={{ textAlign: 'center' }}>
    <iframe 
        style={{
            display: 'block',
            margin: 'auto',
            width: '100%',
            height: '50vh',
        }}
        src="https://www.youtube.com/embed/aircAruvnKk" 
        frameborder="0" 
        allowFullScreen>
    </iframe>
</div>

:::tip Exercício

Carregue o dataset MNIST (disponível no scikit learn e pytorch) e, utilizando
a implementação de MLP da seção anterior, crie uma rede neural capaz de 
aprender os padrões de imagem do dataset MNIST.

Para isso, lembre-se de explorar o dataset para entender qual o tamanho das
imagens e definir a quantidade de entradas da rede neural.

:::

## 2. O dataset CIFAR-10

Há um outro dataset famoso chamado CIFAR-10 que consiste em 60.000 imagens de
treinamento e 10.000 de teste. Cada uma de suas imagens tem 32x32 pixels e
contem uma de dez categorias: 

* avião;
* automóvel;
* ave;
* gato;
* veado;
* cachorro;
* sapo;
* cavalo;
* navio; ou
* caminhão.

Este dataset apresenta, no mesmo tamanho de imagem, um desafio mais complexo
que o MNIST.

:::tip Exercício

Dessa vez utilizando o seu framework de preferência (e.g. pytorch, keras), crie
uma rede neural densa para resolver o problema de classificação do CIFAR-10

:::
