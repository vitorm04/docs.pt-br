---
title: Glossário de aprendizado de máquina
description: Um glossário de termos de aprendizado de máquina.
author: jralexander
ms.author: johalex
ms.date: 05/31/2018
ms.topic: conceptual
ms.prod: dotnet-ml
ms.devlang: dotnet
manager: wpickett
ms.openlocfilehash: b7690eb6931f4a491b1a03812fe3f2d8a64cfcd4
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207712"
---
# <a name="machine-learning-glossary"></a>Glossário de aprendizado de máquina

A lista a seguir é uma compilação de importantes termos de aprendizado de máquina que são úteis ao criar seus modelos personalizados.

## <a name="accuracy"></a>Precisão

Na [classificação](#classification), a precisão consiste no número de itens classificados corretamente dividido pelo número total de itens no conjunto de testes. Varia de 0 (menos preciso) a 1 (mais preciso). A precisão é uma das métricas de avaliação do desempenho do seu modelo. Considere isso em conjunção com [precisão](#precision), [recall](#recall)e [F-score](#f-score).

API do ML.NET relacionada: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.Accuracy?displayProperty=nameWithType>.

## <a name="area-under-the-curve-auc"></a>Área sob a curva (AUC)

Na [classificação binária](#binary-classification), uma métrica de avaliação que é o valor da área sob a curva que plota a taxa de positivos reais (no eixo y) em relação à taxa de falsos positivos (no eixo x). Varia de 0,5 (pior) a 1 (melhor). Também conhecida como a área sob a curva ROC, isto é, a curva característica de operação do receptor. Para obter mais informações, consulte o artigo [Característica de operação do receptor](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) na Wikipédia.

API do ML.NET relacionada: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.Auc?displayProperty=nameWithType>.

## <a name="binary-classification"></a>Classificação binária

Um caso de [classificação](#classification), em que o [rótulo](#label) é apenas uma das duas classes. Para saber mais, confira a seção [Classificação binária](tasks.md#binary-classification) do tópico [Tarefas de aprendizado de máquina](tasks.md).

## <a name="classification"></a>Classificação

Quando os dados são usados ​​para prever uma categoria, a tarefa de [aprendizado de máquina supervisionado](#supervised-machine-learning) é chamada de classificação. [Classificação binária](#binary-classification) refere-se à previsão de apenas duas categorias (por exemplo, classificar uma imagem como uma figura de um "gato" ou um "cachorro"). [Classificação multiclasse](#multiclass-classification) refere-se à previsão de várias categorias (por exemplo, ao classificar uma imagem como uma imagem de uma raça específica de cão).

## <a name="coefficient-of-determination"></a>Coeficiente de determinação

Na [regressão](#regression), uma métrica de avaliação que indica como os dados se ajustam a um modelo. Varia de 0 a 1. Um valor de 0 significa que os dados são aleatórios ou não podem ser ajustados ao modelo. Um valor de 1 significa que o modelo corresponde exatamente aos dados. Geralmente denominado como r<sup>2</sup>, R<sup>2</sup>, ou r-quadrado.

API do ML.NET relacionada: <xref:Microsoft.ML.Models.RegressionMetrics.RSquared?displayProperty=nameWithType>.

## <a name="feature"></a>Recurso

Uma propriedade mensurável do fenômeno que está sendo medido, normalmente um valor numérico (duplo). Vários recursos são referidos como **Vetor de recursos** e normalmente armazenados como `double[]`. As características definem as características importantes do fenômeno que está sendo medido. Para obter mais informações, consulte o artigo [Recurso](https://en.wikipedia.org/wiki/Feature_(machine_learning)) na Wikipédia.

## <a name="feature-engineering"></a>Engenharia de recursos

A engenharia de recursos é o processo que envolve a definição de um conjunto de [recursos](#feature) e o desenvolvimento de software que produz vetores de recursos a partir de dados de fenômenos disponíveis, ou seja, a extração de recursos. Para obter mais informações, consulte o artigo [Engenharia de recursos](https://en.wikipedia.org/wiki/Feature_engineering) na Wikipédia.

## <a name="f-score"></a>F-score

Na [classificação](#classification), uma métrica de avaliação que equilibra [precisão](#precision) e [recall](#recall).

API do ML.NET relacionada: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.F1Score?displayProperty=nameWithType>.

## <a name="hyperparameter"></a>Hiperparâmetro

Um parâmetro de um algoritmo de aprendizado de máquina. Os exemplos incluem o número de árvores a serem aprendidas em uma floresta de decisão ou o tamanho da etapa em um algoritmo descendente de gradiente. Os valores de *Hiperparâmetros* são definidos antes de treinar o modelo e controlar o processo de localização dos parâmetros da função de previsão, por exemplo, os pontos de comparação em uma árvore de decisão ou os pesos em um modelo de regressão linear. Para obter mais informações, consulte o artigo [Hiperparâmetro](https://en.wikipedia.org/wiki/Hyperparameter_(machine_learning)) na Wikipédia.

## <a name="label"></a>Rotular

O elemento a ser previsto com o modelo de aprendizado de máquina. Por exemplo, a raça do cão ou um preço futuro da ação.

## <a name="log-loss"></a>Perda de log

Na [classificação](#classification), uma métrica de avaliação que caracteriza a precisão de um classificador. Quanto menor a perda de log, mais preciso é um classificador.

API do ML.NET relacionada: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.LogLoss?displayProperty=nameWithType>.

## <a name="mean-absolute-error-mae"></a>Erro de média absoluta (MAE)

Na [regressão](#regression), uma métrica de avaliação que é a média de todos os erros de modelo, em que erro de modelo consiste na distância entre o valor do [rótulo](#label) previsto e o valor do rótulo correto.

API do ML.NET relacionada: <xref:Microsoft.ML.Models.RegressionMetrics.L1?displayProperty=nameWithType>.

## <a name="model"></a>Modelo

Tradicionalmente, os parâmetros para a função de previsão. Por exemplo, os pesos em um modelo de regressão linear ou os pontos de divisão em uma árvore de decisão. No ML.NET, um modelo contém todas as informações necessárias para prever o [rótulo](#label) de um objeto de domínio (por exemplo, imagem ou texto). Isso significa que os modelos ML.NET incluem as etapas de personalização necessárias, bem como os parâmetros para a função de previsão.

## <a name="multiclass-classification"></a>Classificação multiclasse

Um caso de [classificação](#classification) em que o [rótulo](#label) é uma entre três ou mais classes. Para saber mais, confira a seção [Classificação multiclasse](tasks.md#multiclass-classification) do tópico [Tarefas de aprendizado de máquina](tasks.md).

## <a name="n-gram"></a>N-grama

Um esquema de extração de recursos para dados de texto: qualquer sequência de N palavras se transforma em um valor de [recurso](#feature).

## <a name="numerical-feature-vector"></a>Vetor de recurso numérico

Um vetor de [recurso](#feature) consistindo apenas em valores numéricos. Similar ao `double[]`.

## <a name="pipeline"></a>Pipeline

Todas as operações necessárias para ajustar um modelo a um conjunto de dados. Um pipeline consiste em etapas de importação, transformação, personalização e aprendizado de dados. Uma vez que um pipeline é treinado, ele se torna um modelo.

## <a name="precision"></a>Precisão

Na [classificação](#classification), a precisão de uma classe é o número de itens preditos corretamente como pertencentes a essa classe dividido pelo número total de itens previstos como pertencentes à classe.

APIs do ML.NET relacionadas: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.NegativePrecision?displayProperty=nameWithType>, <xref:Microsoft.ML.Models.BinaryClassificationMetrics.PositivePrecision?displayProperty=nameWithType>.

## <a name="recall"></a>Recall

Na [classificação](#classification), o recall de uma classe é o número de itens preditos corretamente como pertencentes a essa classe dividido pelo número total de itens que realmente pertencem à classe.

APIs do ML.NET relacionadas: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.NegativeRecall?displayProperty=nameWithType>, <xref:Microsoft.ML.Models.BinaryClassificationMetrics.PositiveRecall?displayProperty=nameWithType>.

## <a name="regression"></a>Regressão

Uma tarefa de [aprendizado de máquina supervisionado](#supervised-machine-learning) em que a saída é um valor real, por exemplo, duplo. Exemplos incluem a previsão de preços de ações. Para saber mais, confira a seção [Regressão](tasks.md#regression) do tópico [Tarefas de aprendizado de máquina](tasks.md).

## <a name="relative-absolute-error"></a>Erro absoluto relativo

Na [regressão](#regression), uma métrica de avaliação que é a soma de todos os erros absolutos dividida pela soma das distâncias entre os valores de [rótulo](#label) corretos e a média de todos os valores de rótulo corretos.

## <a name="relative-squared-error"></a>Erro quadrático relativo

Na [regressão](#regression), uma métrica de avaliação que é a soma de todos os erros absolutos quadráticos dividida pela soma das distâncias quadráticas entre os valores de [rótulo](#label) corretos e a média de todos os valores de rótulo corretos.

## <a name="root-of-mean-squared-error-rmse"></a>Raiz do erro quadrático médio (RMSE)

Na [regressão](#regression), uma métrica de avaliação que é a raiz quadrada da média dos quadrados dos erros.

API do ML.NET relacionada: <xref:Microsoft.ML.Models.RegressionMetrics.Rms?displayProperty=nameWithType>.

## <a name="supervised-machine-learning"></a>Aprendizado de máquina supervisionado

Uma subclasse de aprendizado de máquina na qual um modelo desejado prevê o rótulo para dados ainda não vistos. Exemplos incluem a classificação, regressão e previsão estruturada. Para obter mais informações, consulte o artigo [Aprendizado supervisionado](https://en.wikipedia.org/wiki/Supervised_learning) na Wikipédia.

## <a name="training"></a>Treinamento

O processo de identificar um [modelo](#model) para um determinado conjunto de dados de treinamento. Para um modelo linear, isso significa encontrar os pesos. Para uma árvore, envolve a identificação dos pontos de divisão.

## <a name="transform"></a>Transformar

Um componente do [pipeline](#pipeline) que transforma dados. Por exemplo, de texto para vetor de números.

## <a name="unsupervised-machine-learning"></a>Aprendizado de máquina não supervisionado

Uma subclasse de aprendizado de máquina na qual um modelo desejado encontra estrutura oculta (ou latente) nos dados. Exemplos incluem clustering, modelagem de tópico e redução de dimensionalidade. Para obter mais informações, consulte o artigo [Aprendizado não supervisionado](https://en.wikipedia.org/wiki/Unsupervised_learning) na Wikipédia.
