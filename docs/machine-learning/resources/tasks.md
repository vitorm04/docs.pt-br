---
title: Tarefas de aprendizado de máquina – ML.NET
description: Explore as diferentes tarefas de aprendizado de máquina e as tarefas associadas compatíveis com o ML.NET.
ms.custom: seodec18
ms.date: 01/15/2019
author: jralexander
ms.openlocfilehash: 02b454d18eca36c94c27ae15665af5df2ec87905
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415696"
---
# <a name="machine-learning-tasks-in-mlnet"></a>Tarefas de aprendizado de máquina no ML.NET

Ao criar um modelo de aprendizado de máquina, primeiro é preciso definir o que você espera conseguir com seus dados. Depois, você pode escolher a tarefa de aprendizado de máquina correta para sua situação. A lista a seguir descreve as diferentes tarefas de aprendizado de máquina que você pode escolher e alguns casos de uso comuns.

> [!NOTE]
> O ML.NET está atualmente na Versão Prévia. Não há suporte para todas as tarefas de aprendizado de máquina atualmente. Para enviar uma solicitação para uma determinada tarefa, abra um problema no [dotnet/machinelearning repository](https://github.com/dotnet/machinelearning/issues).

## <a name="binary-classification"></a>Classificação binária

Uma tarefa de [aprendizado de máquina supervisionado](glossary.md#supervised-machine-learning) que é usada para prever a qual das duas classes (categorias) uma instância de dados pertence. A entrada de um algoritmo de classificação é um conjunto de exemplos rotulados, em que cada rótulo é um número inteiro de 0 ou 1. A saída de um algoritmo de classificação binária é um classificador, que pode ser usado para prever a classe de novas instâncias sem rótulo. Exemplos de cenários de classificação binária incluem:

* [Reconhece](../tutorials/sentiment-analysis.md) como "positivo" ou "negativo".
* Diagnosticar se um paciente tem uma determinada doença ou não.
* Tomar a decisão de marcar um email como "spam" ou não.
* Determinar se uma foto exibe um cachorro ou frutas.

Para obter mais informações, consulte o artigo [Classificação binária](https://en.wikipedia.org/wiki/Binary_classification) na Wikipédia.

Aprendizes recomendados para a classificação binária:

* AveragedPerceptronTrainer
* StochasticGradientDescentClassificationTrainer
* LightGbmBinaryTrainer
* FastTreeBinaryClassificationTrainer
* SymSgdClassificationTrainer

### <a name="binary-classification-learners"></a>Aprendizes da classificação binária

Os aprendizes a seguir estão disponíveis para tarefas de classificação binária:

* [AveragedPerceptronTrainer](xref:Microsoft.ML.Trainers.Online.AveragedPerceptronTrainer)
* [BinaryClassificationGamTrainer](xref:Microsoft.ML.Trainers.FastTree.BinaryClassificationGamTrainer)
* [FastForestClassification](xref:Microsoft.ML.Trainers.FastTree.FastForestClassification)
* [FastTreeBinaryClassificationTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer)
* [FieldAwareFactorizationMachineTrainer](xref:Microsoft.ML.FactorizationMachine.FieldAwareFactorizationMachineTrainer)
* [LightGbmBinaryTrainer](xref:Microsoft.ML.LightGBM.LightGbmBinaryTrainer)
* [LinearSvmTrainer](xref:Microsoft.ML.Trainers.Online.LinearSvmTrainer)
* [LogisticRegression](xref:Microsoft.ML.Learners.LogisticRegression)
* [PriorTrainer](xref:Microsoft.ML.Trainers.PriorTrainer)
* [RandomTrainer](xref:Microsoft.ML.Trainers.RandomTrainer)
* [StochasticGradientDescentClassificationTrainer](xref:Microsoft.ML.Trainers.StochasticGradientDescentClassificationTrainer)
* [SymSgdClassificationTrainer](xref:Microsoft.ML.Trainers.SymSgd.SymSgdClassificationTrainer)

## <a name="multiclass-classification"></a>Classificação multiclasse

Uma tarefa de [aprendizado de máquina supervisionado](glossary.md#supervised-machine-learning) que é usada para prever a classe (categoria) de uma instância de dados. A entrada de um algoritmo de classificação é um conjunto de exemplos rotulados. Cada rótulo normalmente começa como texto. Ele é executado por meio de TermTransform, que converte-o para o tipo de Chave (numérico). A saída de um algoritmo de classificação é um classificador, que pode ser usado para prever a classe de novas instâncias sem rótulo. Exemplos de cenários de classificação multiclasse incluem:

* Determinar a raça de um cão como um "Husky Siberiano", "Golden Retriever", "Poodle", etc.
* Entender as resenhas de filmes como "positivas", "neutras" ou "negativas".
* Categorizar as avaliações de hotel como "local", "preço", "limpeza", etc.

Para obter mais informações, consulte o artigo [Classificação multiclasse](https://en.wikipedia.org/wiki/Multiclass_classification) na Wikipédia.

Aprendizes recomendados para Multiclasse:

* OVA-AveragedPerceptronTrainer
* SdcaMultiClassTrainer
* LightGbmMulticlassTrainer
* OVA-FastTreeBinaryClassificationTrainer

>[!NOTE]
>OVA e PKPD atualizam os [aprendizes de classificação binária](#binary-classification) para atuar em conjuntos de dados multiclasse. Mais informações em [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).

### <a name="multiclass-classification-learners"></a>Aprendizes da classificação multiclasse

Os aprendizes a seguir estão disponíveis para tarefas de classificação multiclasse:

* [LightGbmMulticlassTrainer](xref:Microsoft.ML.LightGBM.LightGbmMulticlassTrainer)
* [MetaMulticlassTrainer<TTransformer,TModel>](xref:Microsoft.ML.Learners.MetaMulticlassTrainer%602)
* [MultiClassNaiveBayesTrainer](xref:Microsoft.ML.Trainers.MultiClassNaiveBayesTrainer)
* [Ova](xref:Microsoft.ML.Trainers.Ova)
* [Pkpd](xref:Microsoft.ML.Trainers.Pkpd)
* [SdcaMultiClassTrainer](xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer)

## <a name="regression"></a>Regressão

Uma tarefa de [aprendizado de máquina supervisionado](glossary.md#supervised-machine-learning) que é usada para prever o valor do rótulo de um conjunto de recursos relacionados. O rótulo pode ser de qualquer valor real e não pertence a um conjunto finito de valores como nas tarefas de classificação. Os algoritmos de regressão modelam a dependência do rótulo em seus recursos relacionados para determinar como o rótulo será alterado à medida que os valores dos recursos forem variados. A entrada de um algoritmo de regressão é um conjunto de exemplos com rótulos de valores conhecidos. A saída de um algoritmo de regressão é uma função, que você pode usar para prever o valor de rótulo para qualquer novo conjunto de recursos de entrada. Exemplos de cenários de regressão incluem:

* Previsão de preços de casas com base nos atributos da casa, como número de quartos, localização ou tamanho.
* Previsão de preços futuros de ações com base em dados históricos e tendências atuais do mercado.
* Previsão de vendas de um produto com base em orçamentos de publicidade.

Aprendizes recomendados para regressão:

* FastTreeTweedieTrainer 
* LightGbmRegressorTrainer 
* SdcaRegressionTrainer 
* FastTreeRegressionTrainer

### <a name="regression-learners"></a>Aprendizes de regressão

Os aprendizes a seguir estão disponíveis para tarefas de regressão:

* [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer)
* [FastTreeTweedieTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer)
* [LightGbmRegressorTrainer](xref:Microsoft.ML.LightGBM.LightGbmRegressorTrainer)
* [OlsLinearRegressionTrainer](xref:Microsoft.ML.Trainers.HalLearners.OlsLinearRegressionTrainer)
* [OnlineGradientDescentTrainer](xref:Microsoft.ML.Trainers.Online.OnlineGradientDescentTrainer)
* [PoissonRegression](xref:Microsoft.ML.Trainers.PoissonRegression)
* [RegressionGamTrainer](xref:Microsoft.ML.Trainers.FastTree.RegressionGamTrainer)
* [SdcaRegressionTrainer](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer)
* [FastTree.SingleTrainer](xref:Microsoft.ML.Trainers.FastTree.SingleTrainer)
* [LightGBM.SingleTrainer](xref:Microsoft.ML.LightGBM.SingleTrainer)

## <a name="clustering"></a>Clustering

Uma tarefa de [aprendizado de máquina não supervisionado](glossary.md#unsupervised-machine-learning) que é usada para agrupar instâncias de dados em clusters que contêm características semelhantes. O clustering também pode ser usado para identificar relacionamentos em um conjunto de dados que você pode não obter logicamente por meio de navegação ou observação simples. As entradas e saídas de um algoritmo de clustering depende a metodologia escolhida. Você pode usar uma abordagem baseada em distribuição, centroide, conectividade ou densidade. Atualmente, o ML.NET oferece suporte a uma abordagem baseada em centroides usando o clustering de K-Means. Exemplos de cenários de clustering incluem:

* Compreender os segmentos de hóspedes do hotel com base nos hábitos e características das opções de hotel.
* Identificar segmentos de clientes e dados demográficos para ajudar a criar campanhas de publicidade segmentadas.
* Categorizar o inventário com base nas métricas de fabricação.

### <a name="clustering-learners"></a>Aprendizes de clustering

Os aprendizes a seguir estão disponíveis para tarefas de clustering:

* [KMeansPlusPlusTrainer](xref:Microsoft.ML.Trainers.KMeans.KMeansPlusPlusTrainer)

## <a name="anomaly-detection"></a>Detecção de anomalias

Esta tarefa cria um modelo de detecção de anomalias usando a Análise de Componente Principal (PCA). A Detecção de Anomalias Baseada em PCA ajuda a criar um modelo em cenários onde é fácil obter dados de treinamento de uma classe, como transações válidas, mas é difícil obter exemplos suficientes das anomalias direcionadas.

O PCA, uma técnica estabelecida no aprendizado de máquina, é frequentemente usado na análise exploratória de dados, pois revela a estrutura interna dos dados e explica sua variação. O PCA trabalha analisando dados que contêm muitas variáveis. Ele procura correlações entre as variáveis e determina a combinação de valores que melhor detecta as diferenças nos resultados. Esses valores de recursos combinados são usados para criar um espaço de recurso mais compacto chamado de componentes principais.

A detecção de anomalias abrange várias tarefas importantes no aprendizado de máquina:

* Identificar transações que são potencialmente fraudulentas.
* Aprender padrões que indicam que ocorreu uma invasão da rede.
* Localizar clusters anormais de pacientes.
* Verificar valores inseridos em um sistema.

Como as anomalias são eventos raros por definição, pode ser difícil coletar um exemplo representativo dos dados para usar na modelagem. Os algoritmos incluídos nesta categoria foram especialmente projetados para abordar os principais desafios de criar e treinar modelos usando conjuntos de dados desequilibrados.

### <a name="anomaly-detection-learners"></a>Aprendizes de detecção de anomalias

Os aprendizes a seguir estão disponíveis para tarefas de detecção de anomalias:

* [RandomizedPcaTrainer](xref:Microsoft.ML.Trainers.PCA.RandomizedPcaTrainer)

## <a name="ranking"></a>Classificação

Uma tarefa de classificação cria um classificador a partir de um conjunto de exemplos rotulados. Este conjunto de exemplo consiste em grupos de instâncias que podem ser marcados com um determinado critério. Os rótulos de classificação são { 0, 1, 2, 3, 4 } para cada instância.  O classificador é treinado para classificar novos grupos de instâncias com pontuações desconhecidas para cada instância. Os aprendizes de classificação do ML.NET são baseados na [classificação de máquinas aprendidas](https://en.wikipedia.org/wiki/Learning_to_rank).

### <a name="ranking-learners"></a>Aprendizes de classificação

Os aprendizes a seguir estão disponíveis para tarefas de classificação:

* [FastTreeRankingTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer)
* [LightGbmRankingTrainer](xref:Microsoft.ML.LightGBM.LightGbmRankingTrainer)

## <a name="recommendation"></a>Recomendação

Uma tarefa de recomendação permite produzir uma lista de produtos ou serviços recomendados. O ML.NET usa a [Fatoração matricial (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), um algoritmo de [filtragem colaborativa](https://en.wikipedia.org/wiki/Collaborative_filtering) para as recomendações quando você tem dados históricos de classificação do produto em seu catálogo. Por exemplo, você tem dados históricos de classificação de filmes para seus usuários e deseja recomendar outros filmes que eles provavelmente assistirão posteriormente.

### <a name="recommendation-learners"></a>Aprendizes de recomendação

Os aprendizes a seguir estão disponíveis para tarefas de recomendação:

* [MatrixFactorizationTrainer](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer)
* [MatrixFactorizationPredictionTransformer](xref:Microsoft.ML.Trainers.Recommender.MatrixFactorizationPredictionTransformer)
