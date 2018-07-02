---
title: Tarefas de aprendizado de máquina
description: Explore as diferentes tarefas de aprendizado de máquina com suporte no ML.NET.
ms.date: 06/04/2018
author: aditidugar
ms.author: johalex
ms.openlocfilehash: 875006a9cddb87b5f9436b78773420858fd842dd
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207711"
---
# <a name="machine-learning-tasks"></a>Tarefas de aprendizado de máquina

Ao criar um modelo de aprendizado de máquina, primeiro é preciso definir o que você espera conseguir com seus dados. Depois, você pode escolher a tarefa de aprendizado de máquina correta para sua situação. A lista a seguir descreve as diferentes tarefas de aprendizado de máquina que você pode escolher e alguns casos de uso comuns. 

> [!NOTE]
> O ML.NET está atualmente na Versão Prévia. Não há suporte para todas as tarefas de aprendizado de máquina atualmente. Para enviar uma solicitação para uma determinada tarefa, abra um problema no [dotnet/machinelearning repository](https://github.com/dotnet/machinelearning/issues).

> [!NOTE]
> Atualmente, o ML.NET não oferece suporte para tarefas de aprendizado de máquina com imagens. O suporte será adicionado em versões futuras. 

## <a name="binary-classification"></a>Classificação binária

Uma tarefa de [aprendizado de máquina supervisionado](glossary.md#supervised-machine-learning) que é usada para prever a qual das duas classes (categorias) uma instância de dados pertence. A entrada de um algoritmo de classificação é um conjunto de exemplos rotulados, em que cada rótulo é um número inteiro de 0 ou 1. A saída de um algoritmo de classificação binária é um classificador, que pode ser usado para prever a classe de novas instâncias sem rótulo. Exemplos de cenários de classificação binária incluem:

* [Reconhece](../tutorials/sentiment-analysis.md) como "positivo" ou "negativo".
* Diagnosticar se um paciente tem uma determinada doença ou não.
* Tomar a decisão de marcar um email como "spam" ou não.

Para obter mais informações, consulte o artigo [Classificação binária](https://en.wikipedia.org/wiki/Binary_classification) na Wikipédia.

## <a name="multiclass-classification"></a>Classificação multiclasse

Uma tarefa de [aprendizado de máquina supervisionado](glossary.md#supervised-machine-learning) que é usada para prever a classe (categoria) de uma instância de dados. A entrada de um algoritmo de classificação é um conjunto de exemplos rotulados. Cada rótulo é um inteiro entre 0 e k-1, onde k é o número de classes. A saída de um algoritmo de classificação é um classificador, que pode ser usado para prever a classe de novas instâncias sem rótulo. Exemplos de cenários de classificação multiclasse incluem:

* Determinar a raça de um cão como um "Husky Siberiano", "Golden Retriever", "Poodle", etc.
* Entender as resenhas de filmes como "positivas", "neutras" ou "negativas".
* Categorizar as avaliações de hotel como "local", "preço", "limpeza", etc.

Para obter mais informações, consulte o artigo [Classificação multiclasse](https://en.wikipedia.org/wiki/Multiclass_classification) na Wikipédia.

## <a name="regression"></a>Regressão

Uma tarefa de [aprendizado de máquina supervisionado](glossary.md#supervised-machine-learning) que é usada para prever o valor do rótulo de um conjunto de recursos relacionados. O rótulo pode ser de qualquer valor real e não pertence a um conjunto finito de valores como nas tarefas de classificação. Os algoritmos de regressão modelam a dependência do rótulo em seus recursos relacionados para determinar como o rótulo será alterado à medida que os valores dos recursos forem variados. A entrada de um algoritmo de regressão é um conjunto de exemplos com rótulos de valores conhecidos. A saída de um algoritmo de regressão é uma função, que você pode usar para prever o valor de rótulo para qualquer novo conjunto de recursos de entrada. Exemplos de cenários de regressão incluem:

* Previsão de preços de casas com base nos atributos da casa, como número de quartos, localização ou tamanho.
* Previsão de preços futuros de ações com base em dados históricos e tendências atuais do mercado.
* Previsão de vendas de um produto com base em orçamentos de publicidade.

> [!NOTE]
> Atualmente, o ML.NET ainda está criando suporte para tarefas de regressão que envolvem séries temporais.

## <a name="clustering"></a>Clustering

Uma tarefa de [aprendizado de máquina não supervisionado](glossary.md#unsupervised-machine-learning) que é usada para agrupar instâncias de dados em clusters que contêm características semelhantes. O clustering também pode ser usado para identificar relacionamentos em um conjunto de dados que você pode não obter logicamente por meio de navegação ou observação simples. As entradas e saídas de um algoritmo de clustering depende a metodologia escolhida. Você pode usar uma abordagem baseada em distribuição, centroide, conectividade ou densidade. Atualmente, o ML.NET oferece suporte a uma abordagem baseada em centroides usando o clustering de K-Means. Exemplos de cenários de clustering incluem:

* Compreender os segmentos de hóspedes do hotel com base nos hábitos e características das opções de hotel.
* Identificar segmentos de clientes e dados demográficos para ajudar a criar campanhas de publicidade segmentadas.
* Categorizar o inventário com base nas métricas de fabricação.

## <a name="anomaly-detection-coming-soon"></a>Detecção de anomalias (*em breve*)

## <a name="ranking-coming-soon"></a>Classificação (*em breve*)

## <a name="recommendation-coming-soon"></a>Recomendação (*em breve*)

