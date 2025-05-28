---
sidebar_position: 2
slug: /mlp
title: Perceptron multicamada
---

# Perceptrons multicamada

## 1. Contexto histórico

Depois do entusiasmo inicial com o perceptron de Rosenblatt (1957), a área entrou em estagnação quando **Minsky & Papert** publicaram, em 1969, a crítica de que um único perceptron não podia resolver problemas como XOR. Só em **1986** — quase **trinta anos** depois — **Rumelhart, Hinton & Williams** mostraram como treinar redes com muitas camadas usando **retropropagação do erro**.

Por que tanta demora? Três fatores principais:

* **Limitações de hardware** – No fim dos anos 1950 existiam máquinas como o IBM 704, GE 225 ou o novíssimo PDP‑1: caros, poucos kilobytes de memória e sem processadores de ponto‑flutuante rápidos. Treinar muitos pesos era inviável.
* **Falta de algoritmo** – Embora a ideia de empilhar perceptrons fosse simples, ninguém sabia como ajustar os pesos internos. A descida do gradiente só ganharia forma depois que o cálculo automático do gradiente se popularizou.
* **Baixa atratividade acadêmica** – A crítica de 1969 fez a área perder prestígio; a maioria dos pesquisadores migrou para simbologia/IA clássica. Apenas quando microcomputadores de 16/32 bits (VAX‑11/780, SUN‑3, IBM PC‑AT) se tornaram acessíveis e a retropropagação apareceu é que o tema renasceu.

## 2. Implementação feedforward

Em uma rede multicamada, a saída de uma camada vira a entrada da próxima. O cálculo deixa de ser um escalar por neurônio e passa a ser **vetor–matriz**.

Considere esta topologia mínima que resolve XOR:

* **Camada 1 (oculta)** – 2 entradas + bias → 2 neurônios
* **Camada 2 (saída)** – 2 entradas (vindas da camada 1) + bias → 1 neurônio

Algoritmo feedforward:

1. Forme o vetor `x = [1, x1, x2]` (o primeiro elemento é sempre 1, para o bias).
2. Multiplique por `W1` (2×3) obtendo `z1 = W1 · x`.
3. Aplique a ativação escolhida obtendo `a1 = f(z1)`.
4. Acrescente o bias: `a1_bias = [1, a1_1, a1_2]`.
5. Multiplique por `W2` (1×3) → `z2 = W2 · a1_bias`.
6. Aplique a ativação de saída: `y_hat = g(z2)`.

\:::tip Exercício
Implemente esta passagem direta em Python usando listas de listas ou NumPy. Teste com `[[0,0],[0,1],[1,0],[1,1]]` e verifique as saídas antes do treinamento.
\:::

## 3. Gradiente descendente

### 3.1. A função perda

Num perceptron simples bastava contar acertos/erros. Em redes profundas precisamos de um **objetivo suave** para aplicar otimização. O erro quadrático médio (MSE) é uma escolha comum:

```
MSE = (1/N) * Σ (y - y_hat)²
```

Ele penaliza desvios grandes de forma proporcional ao quadrado do erro.

### 3.2. Otimizando a perda

A minimização da MSE por **gradiente descendente** lembra o método dos mínimos quadrados na regressão linear: movemos os coeficientes na direção do gradiente negativo. A diferença é que na regressão há solução fechada; na MLP iteramos passo a passo porque a função é não‑linear e pode ter vários mínimos locais.

### 3.3. O gradiente

Para ajustar todos os pesos precisamos de `∂MSE/∂W`. Pela **regra da cadeia**, o gradiente da camada 2 depende da saída da camada 1, que por sua vez depende de `W1`. Muitos termos se repetem; a retropropagação aproveita isso propagando um **erro local** da saída para trás.

Exemplo resumido para nossa rede (com uma única amostra):

```
delta2 = (y_hat - y) * g'(z2)
∂MSE/∂W2 = delta2 * a1_bias

delta1 = (W2_no_biasᵀ * delta2) * f'(z1)
∂MSE/∂W1 = delta1 * xᵀ
```

Onde `W2_no_bias` remove o peso do bias para não propagá‑lo indevidamente.

### 3.4. Repensando as funções de ativação

O degrau de Heaviside não possui derivada útil (zero em quase todo lugar), inviabilizando o gradiente. Duas alternativas clássicas:

* **Logística (sigmoide)** – `g(z) = 1 / (1 + e^(−z))` – boa para saídas em \[0, 1].
* **Tangente hiperbólica (tanh)** – `f(z) = (e^z − e^{-z}) / (e^z + e^{-z})` – saída em \[−1, 1], centrada em zero; favorece convergência na camada oculta.

Nesta rede adotaremos `tanh` na camada oculta e `sigmoide` na camada de saída para representar XOR (classe 0 ou 1).

## 4. Treinamento por retropropagação
