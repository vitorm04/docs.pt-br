---
title: Tarefas de aprendizado de máquina – ML.NET
description: Explore as diferentes tarefas de aprendizado de máquina e as tarefas associadas compatíveis com o ML.NET.
ms.custom: seodec18
ms.date: 04/12/2019
author: natke
ms.openlocfilehash: bfed9cf12f8d539c4327549e5305415ce096e022
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613155"
---
# <a name="machine-learning-tasks-in-mlnet"></a><span data-ttu-id="471ac-103">Tarefas de aprendizado de máquina no ML.NET</span><span class="sxs-lookup"><span data-stu-id="471ac-103">Machine learning tasks in ML.NET</span></span>

<span data-ttu-id="471ac-104">Ao criar um modelo de aprendizado de máquina, primeiro é preciso definir o que você espera conseguir com seus dados.</span><span class="sxs-lookup"><span data-stu-id="471ac-104">When building a machine learning model, you first need to define what you are hoping to achieve with your data.</span></span> <span data-ttu-id="471ac-105">Isso permite escolher a tarefa de aprendizado de máquina correta para sua situação.</span><span class="sxs-lookup"><span data-stu-id="471ac-105">This allows you to choose the right machine learning task for your situation.</span></span> <span data-ttu-id="471ac-106">A lista a seguir descreve as diferentes tarefas de aprendizado de máquina que você pode escolher e alguns casos de uso comuns.</span><span class="sxs-lookup"><span data-stu-id="471ac-106">The following list describes the different machine learning tasks that you can choose from and some common use cases.</span></span>

<span data-ttu-id="471ac-107">Depois de decidir a tarefa ideal para seu cenário, será preciso escolher o melhor algoritmo para treinar seu modelo.</span><span class="sxs-lookup"><span data-stu-id="471ac-107">Once you have decided which task works for your scenario, then you need to choose the best algorithm to train your model.</span></span> <span data-ttu-id="471ac-108">Os algoritmos disponíveis são listados na seção para cada tarefa.</span><span class="sxs-lookup"><span data-stu-id="471ac-108">The available algorithms are listed in the section for each task.</span></span>

## <a name="binary-classification"></a><span data-ttu-id="471ac-109">Classificação binária</span><span class="sxs-lookup"><span data-stu-id="471ac-109">Binary classification</span></span>

<span data-ttu-id="471ac-110">Uma tarefa de [aprendizado de máquina supervisionado](glossary.md#supervised-machine-learning) que é usada para prever a qual das duas classes (categorias) uma instância de dados pertence.</span><span class="sxs-lookup"><span data-stu-id="471ac-110">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict which of two classes (categories) an instance of data belongs to.</span></span> <span data-ttu-id="471ac-111">A entrada de um algoritmo de classificação é um conjunto de exemplos rotulados, em que cada rótulo é um número inteiro de 0 ou 1.</span><span class="sxs-lookup"><span data-stu-id="471ac-111">The input of a classification algorithm is a set of labeled examples, where each label is an integer of either 0 or 1.</span></span> <span data-ttu-id="471ac-112">A saída de um algoritmo de classificação binária é um classificador, que pode ser usado para prever a classe de novas instâncias sem rótulo.</span><span class="sxs-lookup"><span data-stu-id="471ac-112">The output of a binary classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="471ac-113">Exemplos de cenários de classificação binária incluem:</span><span class="sxs-lookup"><span data-stu-id="471ac-113">Examples of binary classification scenarios include:</span></span>

* <span data-ttu-id="471ac-114">[Reconhece](../tutorials/sentiment-analysis.md) como "positivo" ou "negativo".</span><span class="sxs-lookup"><span data-stu-id="471ac-114">[Understanding sentiment of Twitter comments](../tutorials/sentiment-analysis.md) as either "positive" or "negative".</span></span>
* <span data-ttu-id="471ac-115">Diagnosticar se um paciente tem uma determinada doença ou não.</span><span class="sxs-lookup"><span data-stu-id="471ac-115">Diagnosing whether a patient has a certain disease or not.</span></span>
* <span data-ttu-id="471ac-116">Tomar a decisão de marcar um email como "spam" ou não.</span><span class="sxs-lookup"><span data-stu-id="471ac-116">Making a decision to mark an email as "spam" or not.</span></span>
* <span data-ttu-id="471ac-117">Determinar se uma foto exibe um cachorro ou frutas.</span><span class="sxs-lookup"><span data-stu-id="471ac-117">Determining if a photo contains a dog or fruit.</span></span>

<span data-ttu-id="471ac-118">Para obter mais informações, consulte o artigo [Classificação binária](https://en.wikipedia.org/wiki/Binary_classification) na Wikipédia.</span><span class="sxs-lookup"><span data-stu-id="471ac-118">For more information, see the [Binary classification](https://en.wikipedia.org/wiki/Binary_classification) article on Wikipedia.</span></span>

### <a name="binary-classification-training-algorithms"></a><span data-ttu-id="471ac-119">Algoritmos de treinamento de classificação binária</span><span class="sxs-lookup"><span data-stu-id="471ac-119">Binary Classification Training Algorithms</span></span>

<span data-ttu-id="471ac-120">Você pode treinar um modelo de classificação binária usando os seguintes algoritmos:</span><span class="sxs-lookup"><span data-stu-id="471ac-120">You can train a binary classification model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>
* <xref:Microsoft.ML.Trainers.LinearSvmTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.PriorTrainer>
* <xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>

## <a name="multiclass-classification"></a><span data-ttu-id="471ac-121">Classificação multiclasse</span><span class="sxs-lookup"><span data-stu-id="471ac-121">Multiclass classification</span></span>

<span data-ttu-id="471ac-122">Uma tarefa de [aprendizado de máquina supervisionado](glossary.md#supervised-machine-learning) que é usada para prever a classe (categoria) de uma instância de dados.</span><span class="sxs-lookup"><span data-stu-id="471ac-122">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the class (category) of an instance of data.</span></span> <span data-ttu-id="471ac-123">A entrada de um algoritmo de classificação é um conjunto de exemplos rotulados.</span><span class="sxs-lookup"><span data-stu-id="471ac-123">The input of a classification algorithm is a set of labeled examples.</span></span> <span data-ttu-id="471ac-124">Cada rótulo normalmente começa como texto.</span><span class="sxs-lookup"><span data-stu-id="471ac-124">Each label normally starts as text.</span></span> <span data-ttu-id="471ac-125">Ele é executado por meio de TermTransform, que converte-o para o tipo de Chave (numérico).</span><span class="sxs-lookup"><span data-stu-id="471ac-125">It is then run through the TermTransform, which converts it to the Key (numeric) type.</span></span> <span data-ttu-id="471ac-126">A saída de um algoritmo de classificação é um classificador, que pode ser usado para prever a classe de novas instâncias sem rótulo.</span><span class="sxs-lookup"><span data-stu-id="471ac-126">The output of a classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="471ac-127">Exemplos de cenários de classificação multiclasse incluem:</span><span class="sxs-lookup"><span data-stu-id="471ac-127">Examples of multi-class classification scenarios include:</span></span>

* <span data-ttu-id="471ac-128">Determinar a raça de um cão como um "Husky Siberiano", "Golden Retriever", "Poodle", etc.</span><span class="sxs-lookup"><span data-stu-id="471ac-128">Determining the breed of a dog as a "Siberian Husky", "Golden Retriever", "Poodle", etc.</span></span>
* <span data-ttu-id="471ac-129">Entender as resenhas de filmes como "positivas", "neutras" ou "negativas".</span><span class="sxs-lookup"><span data-stu-id="471ac-129">Understanding movie reviews as "positive", "neutral", or "negative".</span></span>
* <span data-ttu-id="471ac-130">Categorizar as avaliações de hotel como "local", "preço", "limpeza", etc.</span><span class="sxs-lookup"><span data-stu-id="471ac-130">Categorizing hotel reviews as "location", "price", "cleanliness", etc.</span></span>

<span data-ttu-id="471ac-131">Para obter mais informações, consulte o artigo [Classificação multiclasse](https://en.wikipedia.org/wiki/Multiclass_classification) na Wikipédia.</span><span class="sxs-lookup"><span data-stu-id="471ac-131">For more information, see the [Multiclass classification](https://en.wikipedia.org/wiki/Multiclass_classification) article on Wikipedia.</span></span>

>[!NOTE]
><span data-ttu-id="471ac-132">Uma vs todas as atualizações de [aprendizes de classificação binária](#binary-classification) para atuar em conjuntos de dados multiclasse.</span><span class="sxs-lookup"><span data-stu-id="471ac-132">One vs all upgrades any [binary classification learner](#binary-classification) to act on multiclass datasets.</span></span> <span data-ttu-id="471ac-133">Mais informações em [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span><span class="sxs-lookup"><span data-stu-id="471ac-133">More information on [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span></span>

### <a name="multiclass-classification-training-algorithms"></a><span data-ttu-id="471ac-134">Algoritmos de treinamento de classificação multiclasse</span><span class="sxs-lookup"><span data-stu-id="471ac-134">Multiclass Classification training algorithms</span></span>

<span data-ttu-id="471ac-135">Você pode treinar um modelo de classificação multiclasse usando os seguintes algoritmos de treinamento:</span><span class="sxs-lookup"><span data-stu-id="471ac-135">You can train a multiclass classification model using the following training algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>

## <a name="regression"></a><span data-ttu-id="471ac-136">Regressão</span><span class="sxs-lookup"><span data-stu-id="471ac-136">Regression</span></span>

<span data-ttu-id="471ac-137">Uma tarefa de [aprendizado de máquina supervisionado](glossary.md#supervised-machine-learning) que é usada para prever o valor do rótulo de um conjunto de recursos relacionados.</span><span class="sxs-lookup"><span data-stu-id="471ac-137">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the value of the label from a set of related features.</span></span> <span data-ttu-id="471ac-138">O rótulo pode ser de qualquer valor real e não pertence a um conjunto finito de valores como nas tarefas de classificação.</span><span class="sxs-lookup"><span data-stu-id="471ac-138">The label can be of any real value and is not from a finite set of values as in classification tasks.</span></span> <span data-ttu-id="471ac-139">Os algoritmos de regressão modelam a dependência do rótulo em seus recursos relacionados para determinar como o rótulo será alterado à medida que os valores dos recursos forem variados.</span><span class="sxs-lookup"><span data-stu-id="471ac-139">Regression algorithms model the dependency of the label on its related features to determine how the label will change as the values of the features are varied.</span></span> <span data-ttu-id="471ac-140">A entrada de um algoritmo de regressão é um conjunto de exemplos com rótulos de valores conhecidos.</span><span class="sxs-lookup"><span data-stu-id="471ac-140">The input of a regression algorithm is a set of examples with labels of known values.</span></span> <span data-ttu-id="471ac-141">A saída de um algoritmo de regressão é uma função, que você pode usar para prever o valor de rótulo para qualquer novo conjunto de recursos de entrada.</span><span class="sxs-lookup"><span data-stu-id="471ac-141">The output of a regression algorithm is a function, which you can use to predict the label value for any new set of input features.</span></span> <span data-ttu-id="471ac-142">Exemplos de cenários de regressão incluem:</span><span class="sxs-lookup"><span data-stu-id="471ac-142">Examples of regression scenarios include:</span></span>

* <span data-ttu-id="471ac-143">Previsão de preços de casas com base nos atributos da casa, como número de quartos, localização ou tamanho.</span><span class="sxs-lookup"><span data-stu-id="471ac-143">Predicting house prices based on house attributes such as number of bedrooms, location, or size.</span></span>
* <span data-ttu-id="471ac-144">Previsão de preços futuros de ações com base em dados históricos e tendências atuais do mercado.</span><span class="sxs-lookup"><span data-stu-id="471ac-144">Predicting future stock prices based on historical data and current market trends.</span></span>
* <span data-ttu-id="471ac-145">Previsão de vendas de um produto com base em orçamentos de publicidade.</span><span class="sxs-lookup"><span data-stu-id="471ac-145">Predicting sales of a product based on advertising budgets.</span></span>

### <a name="regression-training-algorithms"></a><span data-ttu-id="471ac-146">Algoritmos de treinamento de regressão</span><span class="sxs-lookup"><span data-stu-id="471ac-146">Regression training algorithms</span></span>

<span data-ttu-id="471ac-147">Você pode treinar um modelo de regressão usando os seguintes algoritmos:</span><span class="sxs-lookup"><span data-stu-id="471ac-147">You can train a regression model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>

## <a name="clustering"></a><span data-ttu-id="471ac-148">Clustering</span><span class="sxs-lookup"><span data-stu-id="471ac-148">Clustering</span></span>

<span data-ttu-id="471ac-149">Uma tarefa de [aprendizado de máquina não supervisionado](glossary.md#unsupervised-machine-learning) que é usada para agrupar instâncias de dados em clusters que contêm características semelhantes.</span><span class="sxs-lookup"><span data-stu-id="471ac-149">An [unsupervised machine learning](glossary.md#unsupervised-machine-learning) task that is used to group instances of data into clusters that contain similar characteristics.</span></span> <span data-ttu-id="471ac-150">O clustering também pode ser usado para identificar relacionamentos em um conjunto de dados que você pode não obter logicamente por meio de navegação ou observação simples.</span><span class="sxs-lookup"><span data-stu-id="471ac-150">Clustering can also be used to identify relationships in a dataset that you might not logically derive by browsing or simple observation.</span></span> <span data-ttu-id="471ac-151">As entradas e saídas de um algoritmo de clustering depende a metodologia escolhida.</span><span class="sxs-lookup"><span data-stu-id="471ac-151">The inputs and outputs of a clustering algorithm depends on the methodology chosen.</span></span> <span data-ttu-id="471ac-152">Você pode usar uma abordagem baseada em distribuição, centroide, conectividade ou densidade.</span><span class="sxs-lookup"><span data-stu-id="471ac-152">You can take a distribution, centroid, connectivity, or density-based approach.</span></span> <span data-ttu-id="471ac-153">Atualmente, o ML.NET oferece suporte a uma abordagem baseada em centroides usando o clustering de K-Means.</span><span class="sxs-lookup"><span data-stu-id="471ac-153">ML.NET currently supports a centroid-based approach using K-Means clustering.</span></span> <span data-ttu-id="471ac-154">Exemplos de cenários de clustering incluem:</span><span class="sxs-lookup"><span data-stu-id="471ac-154">Examples of clustering scenarios include:</span></span>

* <span data-ttu-id="471ac-155">Compreender os segmentos de hóspedes do hotel com base nos hábitos e características das opções de hotel.</span><span class="sxs-lookup"><span data-stu-id="471ac-155">Understanding segments of hotel guests based on habits and characteristics of hotel choices.</span></span>
* <span data-ttu-id="471ac-156">Identificar segmentos de clientes e dados demográficos para ajudar a criar campanhas de publicidade segmentadas.</span><span class="sxs-lookup"><span data-stu-id="471ac-156">Identifying customer segments and demographics to help build targeted advertising campaigns.</span></span>
* <span data-ttu-id="471ac-157">Categorizar o inventário com base nas métricas de fabricação.</span><span class="sxs-lookup"><span data-stu-id="471ac-157">Categorizing inventory based on manufacturing metrics.</span></span>

### <a name="clustering-training-algorithms"></a><span data-ttu-id="471ac-158">Algoritmos de treinamento de clustering</span><span class="sxs-lookup"><span data-stu-id="471ac-158">Clustering training algorithms</span></span>

<span data-ttu-id="471ac-159">Você pode treinar um modelo de clustering usando os seguintes algoritmos:</span><span class="sxs-lookup"><span data-stu-id="471ac-159">You can train a clustering model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.KMeansTrainer>

## <a name="anomaly-detection"></a><span data-ttu-id="471ac-160">Detecção de anomalias</span><span class="sxs-lookup"><span data-stu-id="471ac-160">Anomaly detection</span></span>

<span data-ttu-id="471ac-161">Esta tarefa cria um modelo de detecção de anomalias usando a Análise de Componente Principal (PCA).</span><span class="sxs-lookup"><span data-stu-id="471ac-161">This task creates an anomaly detection model by using Principal Component Analysis (PCA).</span></span> <span data-ttu-id="471ac-162">A Detecção de Anomalias Baseada em PCA ajuda a criar um modelo em cenários onde é fácil obter dados de treinamento de uma classe, como transações válidas, mas é difícil obter exemplos suficientes das anomalias direcionadas.</span><span class="sxs-lookup"><span data-stu-id="471ac-162">PCA-Based Anomaly Detection helps you build a model in scenarios where it is easy to obtain training data from one class, such as valid transactions, but difficult to obtain sufficient samples of the targeted anomalies.</span></span>

<span data-ttu-id="471ac-163">O PCA, uma técnica estabelecida no aprendizado de máquina, é frequentemente usado na análise exploratória de dados, pois revela a estrutura interna dos dados e explica sua variação.</span><span class="sxs-lookup"><span data-stu-id="471ac-163">An established technique in machine learning, PCA is frequently used in exploratory data analysis because it reveals the inner structure of the data and explains the variance in the data.</span></span> <span data-ttu-id="471ac-164">O PCA trabalha analisando dados que contêm muitas variáveis.</span><span class="sxs-lookup"><span data-stu-id="471ac-164">PCA works by analyzing data that contains multiple variables.</span></span> <span data-ttu-id="471ac-165">Ele procura correlações entre as variáveis e determina a combinação de valores que melhor detecta as diferenças nos resultados.</span><span class="sxs-lookup"><span data-stu-id="471ac-165">It looks for correlations among the variables and determines the combination of values that best captures differences in outcomes.</span></span> <span data-ttu-id="471ac-166">Esses valores de recursos combinados são usados para criar um espaço de recurso mais compacto chamado de componentes principais.</span><span class="sxs-lookup"><span data-stu-id="471ac-166">These combined feature values are used to create a more compact feature space called the principal components.</span></span>

<span data-ttu-id="471ac-167">A detecção de anomalias abrange várias tarefas importantes no aprendizado de máquina:</span><span class="sxs-lookup"><span data-stu-id="471ac-167">Anomaly detection encompasses many important tasks in machine learning:</span></span>

* <span data-ttu-id="471ac-168">Identificar transações que são potencialmente fraudulentas.</span><span class="sxs-lookup"><span data-stu-id="471ac-168">Identifying transactions that are potentially fraudulent.</span></span>
* <span data-ttu-id="471ac-169">Aprender padrões que indicam que ocorreu uma invasão da rede.</span><span class="sxs-lookup"><span data-stu-id="471ac-169">Learning patterns that indicate that a network intrusion has occurred.</span></span>
* <span data-ttu-id="471ac-170">Localizar clusters anormais de pacientes.</span><span class="sxs-lookup"><span data-stu-id="471ac-170">Finding abnormal clusters of patients.</span></span>
* <span data-ttu-id="471ac-171">Verificar valores inseridos em um sistema.</span><span class="sxs-lookup"><span data-stu-id="471ac-171">Checking values entered into a system.</span></span>

<span data-ttu-id="471ac-172">Como as anomalias são eventos raros por definição, pode ser difícil coletar um exemplo representativo dos dados para usar na modelagem.</span><span class="sxs-lookup"><span data-stu-id="471ac-172">Because anomalies are rare events by definition, it can be difficult to collect a representative sample of data to use for modeling.</span></span> <span data-ttu-id="471ac-173">Os algoritmos incluídos nesta categoria foram especialmente projetados para abordar os principais desafios de criar e treinar modelos usando conjuntos de dados desequilibrados.</span><span class="sxs-lookup"><span data-stu-id="471ac-173">The algorithms included in this category have been especially designed to address the core challenges of building and training models by using imbalanced data sets.</span></span>

### <a name="anomaly-detection-training-algorithms"></a><span data-ttu-id="471ac-174">Algoritmos de treinamento de detecção de anomalias</span><span class="sxs-lookup"><span data-stu-id="471ac-174">Anomaly detection training algorithms</span></span>

<span data-ttu-id="471ac-175">Você pode treinar um modelo de detecção de anomalias usando os seguintes algoritmos:</span><span class="sxs-lookup"><span data-stu-id="471ac-175">You can train an anomaly detection model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

## <a name="ranking"></a><span data-ttu-id="471ac-176">Classificação</span><span class="sxs-lookup"><span data-stu-id="471ac-176">Ranking</span></span>

<span data-ttu-id="471ac-177">Uma tarefa de classificação cria um classificador a partir de um conjunto de exemplos rotulados.</span><span class="sxs-lookup"><span data-stu-id="471ac-177">A ranking task constructs a ranker from a set of labeled examples.</span></span> <span data-ttu-id="471ac-178">Este conjunto de exemplo consiste em grupos de instâncias que podem ser marcados com um determinado critério.</span><span class="sxs-lookup"><span data-stu-id="471ac-178">This example set consists of instance groups that can be scored with a given criteria.</span></span> <span data-ttu-id="471ac-179">Os rótulos de classificação são { 0, 1, 2, 3, 4 } para cada instância.</span><span class="sxs-lookup"><span data-stu-id="471ac-179">The ranking labels are { 0, 1, 2, 3, 4 } for each instance.</span></span>  <span data-ttu-id="471ac-180">O classificador é treinado para classificar novos grupos de instâncias com pontuações desconhecidas para cada instância.</span><span class="sxs-lookup"><span data-stu-id="471ac-180">The ranker is trained to rank new instance groups with unknown scores for each instance.</span></span> <span data-ttu-id="471ac-181">Os aprendizes de classificação do ML.NET são baseados na [classificação de máquinas aprendidas](https://en.wikipedia.org/wiki/Learning_to_rank).</span><span class="sxs-lookup"><span data-stu-id="471ac-181">ML.NET ranking learners are [machine learned ranking](https://en.wikipedia.org/wiki/Learning_to_rank) based.</span></span>

### <a name="ranking-training-algorithms"></a><span data-ttu-id="471ac-182">Algoritmos de treinamento de classificação</span><span class="sxs-lookup"><span data-stu-id="471ac-182">Ranking training algorithms</span></span>

<span data-ttu-id="471ac-183">Você pode treinar um modelo de classificação usando os seguintes algoritmos:</span><span class="sxs-lookup"><span data-stu-id="471ac-183">You can train a ranking model with the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>

## <a name="recommendation"></a><span data-ttu-id="471ac-184">Recomendação</span><span class="sxs-lookup"><span data-stu-id="471ac-184">Recommendation</span></span>

<span data-ttu-id="471ac-185">Uma tarefa de recomendação permite produzir uma lista de produtos ou serviços recomendados.</span><span class="sxs-lookup"><span data-stu-id="471ac-185">A recommendation task enables producing a list of recommended products or services.</span></span> <span data-ttu-id="471ac-186">O ML.NET usa a [Fatoração matricial (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), um algoritmo de [filtragem colaborativa](https://en.wikipedia.org/wiki/Collaborative_filtering) para as recomendações quando você tem dados históricos de classificação do produto em seu catálogo.</span><span class="sxs-lookup"><span data-stu-id="471ac-186">ML.NET uses [Matrix factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), a [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) algorithm for recommendations when you have historical product rating data in your catalog.</span></span> <span data-ttu-id="471ac-187">Por exemplo, você tem dados históricos de classificação de filmes para seus usuários e deseja recomendar outros filmes que eles provavelmente assistirão posteriormente.</span><span class="sxs-lookup"><span data-stu-id="471ac-187">For example, you have historical movie rating data for your users and want to recommend  other movies they are likely to watch next.</span></span>

### <a name="recommendation-training-algorithms"></a><span data-ttu-id="471ac-188">Algoritmos de treinamento de recomendação</span><span class="sxs-lookup"><span data-stu-id="471ac-188">Recommendation training algorithms</span></span>

<span data-ttu-id="471ac-189">Você pode treinar um modelo de recomendação usando os seguintes algoritmos:</span><span class="sxs-lookup"><span data-stu-id="471ac-189">You can train a recommendation model with the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>
