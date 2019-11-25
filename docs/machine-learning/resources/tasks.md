---
title: Tarefas de aprendizado de máquina
description: Explore as diferentes tarefas de aprendizado de máquina e as tarefas associadas compatíveis com o ML.NET.
ms.custom: seodec18
ms.date: 04/23/2019
author: natke
ms.openlocfilehash: d0634ce8a0559ab3cdb5bf27fc5406ab02af8df6
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977249"
---
# <a name="machine-learning-tasks-in-mlnet"></a><span data-ttu-id="d5497-103">Tarefas de aprendizado de máquina no ML.NET</span><span class="sxs-lookup"><span data-stu-id="d5497-103">Machine learning tasks in ML.NET</span></span>

<span data-ttu-id="d5497-104">Ao criar um modelo de aprendizado de máquina, primeiro é preciso definir o que você espera conseguir com seus dados.</span><span class="sxs-lookup"><span data-stu-id="d5497-104">When building a machine learning model, you first need to define what you are hoping to achieve with your data.</span></span> <span data-ttu-id="d5497-105">Isso permite escolher a tarefa de aprendizado de máquina correta para sua situação.</span><span class="sxs-lookup"><span data-stu-id="d5497-105">This allows you to choose the right machine learning task for your situation.</span></span> <span data-ttu-id="d5497-106">A lista a seguir descreve as diferentes tarefas de aprendizado de máquina que você pode escolher e alguns casos de uso comuns.</span><span class="sxs-lookup"><span data-stu-id="d5497-106">The following list describes the different machine learning tasks that you can choose from and some common use cases.</span></span> <span data-ttu-id="d5497-107">Para obter mais informações sobre como escolher a tarefa apropriada para seu cenário, consulte [algoritmos](../how-to-choose-an-ml-net-algorithm.md).</span><span class="sxs-lookup"><span data-stu-id="d5497-107">For more information about choosing the task that is appropriate for your scenario, see [Algorithms](../how-to-choose-an-ml-net-algorithm.md).</span></span>

<span data-ttu-id="d5497-108">Depois de decidir a tarefa ideal para seu cenário, será preciso escolher o melhor algoritmo para treinar seu modelo.</span><span class="sxs-lookup"><span data-stu-id="d5497-108">Once you have decided which task works for your scenario, then you need to choose the best algorithm to train your model.</span></span> <span data-ttu-id="d5497-109">Os algoritmos disponíveis são listados na seção para cada tarefa.</span><span class="sxs-lookup"><span data-stu-id="d5497-109">The available algorithms are listed in the section for each task.</span></span>

## <a name="binary-classification"></a><span data-ttu-id="d5497-110">Classificação binária</span><span class="sxs-lookup"><span data-stu-id="d5497-110">Binary classification</span></span>

<span data-ttu-id="d5497-111">Uma tarefa de [aprendizado de máquina supervisionado](glossary.md#supervised-machine-learning) que é usada para prever a qual das duas classes (categorias) uma instância de dados pertence.</span><span class="sxs-lookup"><span data-stu-id="d5497-111">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict which of two classes (categories) an instance of data belongs to.</span></span> <span data-ttu-id="d5497-112">A entrada de um algoritmo de classificação é um conjunto de exemplos rotulados, em que cada rótulo é um número inteiro de 0 ou 1.</span><span class="sxs-lookup"><span data-stu-id="d5497-112">The input of a classification algorithm is a set of labeled examples, where each label is an integer of either 0 or 1.</span></span> <span data-ttu-id="d5497-113">A saída de um algoritmo de classificação binária é um classificador, que pode ser usado para prever a classe de novas instâncias sem rótulo.</span><span class="sxs-lookup"><span data-stu-id="d5497-113">The output of a binary classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="d5497-114">Exemplos de cenários de classificação binária incluem:</span><span class="sxs-lookup"><span data-stu-id="d5497-114">Examples of binary classification scenarios include:</span></span>

* <span data-ttu-id="d5497-115">[Reconhece](../tutorials/sentiment-analysis.md) como "positivo" ou "negativo".</span><span class="sxs-lookup"><span data-stu-id="d5497-115">[Understanding sentiment of Twitter comments](../tutorials/sentiment-analysis.md) as either "positive" or "negative".</span></span>
* <span data-ttu-id="d5497-116">Diagnosticar se um paciente tem uma determinada doença ou não.</span><span class="sxs-lookup"><span data-stu-id="d5497-116">Diagnosing whether a patient has a certain disease or not.</span></span>
* <span data-ttu-id="d5497-117">Tomar a decisão de marcar um email como "spam" ou não.</span><span class="sxs-lookup"><span data-stu-id="d5497-117">Making a decision to mark an email as "spam" or not.</span></span>
* <span data-ttu-id="d5497-118">Determinar se uma foto contém um item específico ou não, como um cão ou frutas.</span><span class="sxs-lookup"><span data-stu-id="d5497-118">Determining if a photo contains a particular item or not, such as a dog or fruit.</span></span>

<span data-ttu-id="d5497-119">Para obter mais informações, consulte o artigo [Classificação binária](https://en.wikipedia.org/wiki/Binary_classification) na Wikipédia.</span><span class="sxs-lookup"><span data-stu-id="d5497-119">For more information, see the [Binary classification](https://en.wikipedia.org/wiki/Binary_classification) article on Wikipedia.</span></span>

### <a name="binary-classification-trainers"></a><span data-ttu-id="d5497-120">Treinadores da classificação binária</span><span class="sxs-lookup"><span data-stu-id="d5497-120">Binary classification trainers</span></span>

<span data-ttu-id="d5497-121">Você pode treinar um modelo de classificação binária usando os seguintes algoritmos:</span><span class="sxs-lookup"><span data-stu-id="d5497-121">You can train a binary classification model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>
* <xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>
* <xref:Microsoft.ML.Trainers.PriorTrainer>
* <xref:Microsoft.ML.Trainers.LinearSvmTrainer>

### <a name="binary-classification-inputs-and-outputs"></a><span data-ttu-id="d5497-122">Saídas e entradas de classificação binária</span><span class="sxs-lookup"><span data-stu-id="d5497-122">Binary classification inputs and outputs</span></span>

<span data-ttu-id="d5497-123">Para obter melhores resultados com a classificação binária, os dados de treinamento devem ser equilibrados (ou seja, números iguais de dados de treinamento positivos e negativos).</span><span class="sxs-lookup"><span data-stu-id="d5497-123">For best results with binary classification, the training data should be balanced (that is, equal numbers of positive and negative training data).</span></span> <span data-ttu-id="d5497-124">Os valores ausentes devem ser manipulados antes do treinamento.</span><span class="sxs-lookup"><span data-stu-id="d5497-124">Missing values should be handled before training.</span></span>

<span data-ttu-id="d5497-125">Os dados da coluna de rótulo de entrada devem ser <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="d5497-125">The input label column data must be <xref:System.Boolean>.</span></span>
<span data-ttu-id="d5497-126">Os dados da coluna de recursos de entrada devem ser um vetor de tamanho fixo de <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="d5497-126">The input features column data must be a fixed-size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="d5497-127">Esses treinadores geram as seguintes colunas:</span><span class="sxs-lookup"><span data-stu-id="d5497-127">These trainers output the following columns:</span></span>

| <span data-ttu-id="d5497-128">Nome da Coluna de Saída</span><span class="sxs-lookup"><span data-stu-id="d5497-128">Output Column Name</span></span> | <span data-ttu-id="d5497-129">Tipo de coluna</span><span class="sxs-lookup"><span data-stu-id="d5497-129">Column Type</span></span> | <span data-ttu-id="d5497-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="d5497-130">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="d5497-131">A pontuação bruta calculada pelo modelo</span><span class="sxs-lookup"><span data-stu-id="d5497-131">The raw score that was calculated by the model</span></span>|
| `PredictedLabel` | <xref:System.Boolean> | <span data-ttu-id="d5497-132">O rótulo previsto com base no sinal da pontuação.</span><span class="sxs-lookup"><span data-stu-id="d5497-132">The predicted label, based on the sign of the score.</span></span> <span data-ttu-id="d5497-133">Uma pontuação negativa é mapeada para `false` e uma pontuação positiva é mapeada para `true`.</span><span class="sxs-lookup"><span data-stu-id="d5497-133">A negative score maps to `false` and a positive score maps to `true`.</span></span>|

## <a name="multiclass-classification"></a><span data-ttu-id="d5497-134">Classificação multiclasse</span><span class="sxs-lookup"><span data-stu-id="d5497-134">Multiclass classification</span></span>

<span data-ttu-id="d5497-135">Uma tarefa de [aprendizado de máquina supervisionado](glossary.md#supervised-machine-learning) que é usada para prever a classe (categoria) de uma instância de dados.</span><span class="sxs-lookup"><span data-stu-id="d5497-135">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the class (category) of an instance of data.</span></span> <span data-ttu-id="d5497-136">A entrada de um algoritmo de classificação é um conjunto de exemplos rotulados.</span><span class="sxs-lookup"><span data-stu-id="d5497-136">The input of a classification algorithm is a set of labeled examples.</span></span> <span data-ttu-id="d5497-137">Cada rótulo normalmente começa como texto.</span><span class="sxs-lookup"><span data-stu-id="d5497-137">Each label normally starts as text.</span></span> <span data-ttu-id="d5497-138">Ele é executado por meio de TermTransform, que converte-o para o tipo de Chave (numérico).</span><span class="sxs-lookup"><span data-stu-id="d5497-138">It is then run through the TermTransform, which converts it to the Key (numeric) type.</span></span> <span data-ttu-id="d5497-139">A saída de um algoritmo de classificação é um classificador, que pode ser usado para prever a classe de novas instâncias sem rótulo.</span><span class="sxs-lookup"><span data-stu-id="d5497-139">The output of a classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="d5497-140">Exemplos de cenários de classificação multiclasse incluem:</span><span class="sxs-lookup"><span data-stu-id="d5497-140">Examples of multi-class classification scenarios include:</span></span>

* <span data-ttu-id="d5497-141">Determinar a raça de um cão como um "Husky Siberiano", "Golden Retriever", "Poodle", etc.</span><span class="sxs-lookup"><span data-stu-id="d5497-141">Determining the breed of a dog as a "Siberian Husky", "Golden Retriever", "Poodle", etc.</span></span>
* <span data-ttu-id="d5497-142">Entender as resenhas de filmes como "positivas", "neutras" ou "negativas".</span><span class="sxs-lookup"><span data-stu-id="d5497-142">Understanding movie reviews as "positive", "neutral", or "negative".</span></span>
* <span data-ttu-id="d5497-143">Categorizar as avaliações de hotel como "local", "preço", "limpeza", etc.</span><span class="sxs-lookup"><span data-stu-id="d5497-143">Categorizing hotel reviews as "location", "price", "cleanliness", etc.</span></span>

<span data-ttu-id="d5497-144">Para obter mais informações, consulte o artigo [Classificação multiclasse](https://en.wikipedia.org/wiki/Multiclass_classification) na Wikipédia.</span><span class="sxs-lookup"><span data-stu-id="d5497-144">For more information, see the [Multiclass classification](https://en.wikipedia.org/wiki/Multiclass_classification) article on Wikipedia.</span></span>

>[!NOTE]
><span data-ttu-id="d5497-145">Uma vs todas as atualizações de [aprendizes de classificação binária](#binary-classification) para atuar em conjuntos de dados multiclasse.</span><span class="sxs-lookup"><span data-stu-id="d5497-145">One vs all upgrades any [binary classification learner](#binary-classification) to act on multiclass datasets.</span></span> <span data-ttu-id="d5497-146">Mais informações em [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span><span class="sxs-lookup"><span data-stu-id="d5497-146">More information on [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span></span>

### <a name="multiclass-classification-trainers"></a><span data-ttu-id="d5497-147">Treinadores de classificação multiclasse</span><span class="sxs-lookup"><span data-stu-id="d5497-147">Multiclass classification trainers</span></span>

<span data-ttu-id="d5497-148">Você pode treinar um modelo de classificação multiclasse usando os seguintes algoritmos de treinamento:</span><span class="sxs-lookup"><span data-stu-id="d5497-148">You can train a multiclass classification model using the following training algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>

### <a name="multiclass-classification-inputs-and-outputs"></a><span data-ttu-id="d5497-149">Saídas e entradas de classificação multiclasse</span><span class="sxs-lookup"><span data-stu-id="d5497-149">Multiclass classification inputs and outputs</span></span>

<span data-ttu-id="d5497-150">Os dados da coluna de rótulo de entrada devem ser do tipo [chave](xref:Microsoft.ML.Data.KeyDataViewType).</span><span class="sxs-lookup"><span data-stu-id="d5497-150">The input label column data must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>
<span data-ttu-id="d5497-151">A coluna de recursos deve ser um vetor de tamanho fixo de <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="d5497-151">The feature column must be a fixed size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="d5497-152">Este treinador produz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d5497-152">This trainer outputs the following:</span></span>

| <span data-ttu-id="d5497-153">Nome de Saída</span><span class="sxs-lookup"><span data-stu-id="d5497-153">Output Name</span></span> | <span data-ttu-id="d5497-154">Digite</span><span class="sxs-lookup"><span data-stu-id="d5497-154">Type</span></span> | <span data-ttu-id="d5497-155">Descrição</span><span class="sxs-lookup"><span data-stu-id="d5497-155">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="d5497-156">Vetor de <xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="d5497-156">Vector of <xref:System.Single></span></span> | <span data-ttu-id="d5497-157">As pontuações de todas as classes.</span><span class="sxs-lookup"><span data-stu-id="d5497-157">The scores of all classes.</span></span> <span data-ttu-id="d5497-158">Um valor mais alto significa maior probabilidade de se enquadrar na classe associada.</span><span class="sxs-lookup"><span data-stu-id="d5497-158">Higher value means higher probability to fall into the associated class.</span></span> <span data-ttu-id="d5497-159">Se o elemento iº elemento tiver o maior valor, o índice de rótulo previsto será i.</span><span class="sxs-lookup"><span data-stu-id="d5497-159">If the i-th element has the largest value, the predicted label index would be i.</span></span> <span data-ttu-id="d5497-160">Observe que i é o índice baseado em zero.</span><span class="sxs-lookup"><span data-stu-id="d5497-160">Note that i is zero-based index.</span></span> |
| `PredictedLabel` | <span data-ttu-id="d5497-161">Tipo de [chave](xref:Microsoft.ML.Data.KeyDataViewType)</span><span class="sxs-lookup"><span data-stu-id="d5497-161">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="d5497-162">O índice do rótulo previsto.</span><span class="sxs-lookup"><span data-stu-id="d5497-162">The predicted label's index.</span></span> <span data-ttu-id="d5497-163">Se seu valor for i, o rótulo real será a iº categoria no tipo de rótulo de entrada com valor de chave.</span><span class="sxs-lookup"><span data-stu-id="d5497-163">If its value is i, the actual label would be the i-th category in the key-valued input label type.</span></span> |

## <a name="regression"></a><span data-ttu-id="d5497-164">Regressão</span><span class="sxs-lookup"><span data-stu-id="d5497-164">Regression</span></span>

<span data-ttu-id="d5497-165">Uma tarefa de [aprendizado de máquina supervisionado](glossary.md#supervised-machine-learning) que é usada para prever o valor do rótulo de um conjunto de recursos relacionados.</span><span class="sxs-lookup"><span data-stu-id="d5497-165">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the value of the label from a set of related features.</span></span> <span data-ttu-id="d5497-166">O rótulo pode ser de qualquer valor real e não pertence a um conjunto finito de valores como nas tarefas de classificação.</span><span class="sxs-lookup"><span data-stu-id="d5497-166">The label can be of any real value and is not from a finite set of values as in classification tasks.</span></span> <span data-ttu-id="d5497-167">Os algoritmos de regressão modelam a dependência do rótulo em seus recursos relacionados para determinar como o rótulo será alterado à medida que os valores dos recursos forem variados.</span><span class="sxs-lookup"><span data-stu-id="d5497-167">Regression algorithms model the dependency of the label on its related features to determine how the label will change as the values of the features are varied.</span></span> <span data-ttu-id="d5497-168">A entrada de um algoritmo de regressão é um conjunto de exemplos com rótulos de valores conhecidos.</span><span class="sxs-lookup"><span data-stu-id="d5497-168">The input of a regression algorithm is a set of examples with labels of known values.</span></span> <span data-ttu-id="d5497-169">A saída de um algoritmo de regressão é uma função, que você pode usar para prever o valor de rótulo para qualquer novo conjunto de recursos de entrada.</span><span class="sxs-lookup"><span data-stu-id="d5497-169">The output of a regression algorithm is a function, which you can use to predict the label value for any new set of input features.</span></span> <span data-ttu-id="d5497-170">Exemplos de cenários de regressão incluem:</span><span class="sxs-lookup"><span data-stu-id="d5497-170">Examples of regression scenarios include:</span></span>

* <span data-ttu-id="d5497-171">Previsão de preços de casas com base nos atributos da casa, como número de quartos, localização ou tamanho.</span><span class="sxs-lookup"><span data-stu-id="d5497-171">Predicting house prices based on house attributes such as number of bedrooms, location, or size.</span></span>
* <span data-ttu-id="d5497-172">Previsão de preços futuros de ações com base em dados históricos e tendências atuais do mercado.</span><span class="sxs-lookup"><span data-stu-id="d5497-172">Predicting future stock prices based on historical data and current market trends.</span></span>
* <span data-ttu-id="d5497-173">Previsão de vendas de um produto com base em orçamentos de publicidade.</span><span class="sxs-lookup"><span data-stu-id="d5497-173">Predicting sales of a product based on advertising budgets.</span></span>

### <a name="regression-trainers"></a><span data-ttu-id="d5497-174">Treinadores de regressão</span><span class="sxs-lookup"><span data-stu-id="d5497-174">Regression trainers</span></span>

<span data-ttu-id="d5497-175">Você pode treinar um modelo de regressão usando os seguintes algoritmos:</span><span class="sxs-lookup"><span data-stu-id="d5497-175">You can train a regression model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>

### <a name="regression-inputs-and-outputs"></a><span data-ttu-id="d5497-176">Saídas e entradas de regressão</span><span class="sxs-lookup"><span data-stu-id="d5497-176">Regression inputs and outputs</span></span>

<span data-ttu-id="d5497-177">Os dados da coluna de rótulo de entrada devem ser <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="d5497-177">The input label column data must be <xref:System.Single>.</span></span>

<span data-ttu-id="d5497-178">Os treinadores para esta tarefa produzem a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="d5497-178">The trainers for this task output the following:</span></span>

| <span data-ttu-id="d5497-179">Nome de Saída</span><span class="sxs-lookup"><span data-stu-id="d5497-179">Output Name</span></span> | <span data-ttu-id="d5497-180">Digite</span><span class="sxs-lookup"><span data-stu-id="d5497-180">Type</span></span> | <span data-ttu-id="d5497-181">Descrição</span><span class="sxs-lookup"><span data-stu-id="d5497-181">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="d5497-182">A pontuação bruta prevista pelo modelo</span><span class="sxs-lookup"><span data-stu-id="d5497-182">The raw score that was predicted by the model</span></span> |

## <a name="clustering"></a><span data-ttu-id="d5497-183">Clustering</span><span class="sxs-lookup"><span data-stu-id="d5497-183">Clustering</span></span>

<span data-ttu-id="d5497-184">Uma tarefa de [aprendizado de máquina não supervisionado](glossary.md#unsupervised-machine-learning) que é usada para agrupar instâncias de dados em clusters que contêm características semelhantes.</span><span class="sxs-lookup"><span data-stu-id="d5497-184">An [unsupervised machine learning](glossary.md#unsupervised-machine-learning) task that is used to group instances of data into clusters that contain similar characteristics.</span></span> <span data-ttu-id="d5497-185">O clustering também pode ser usado para identificar relacionamentos em um conjunto de dados que você pode não obter logicamente por meio de navegação ou observação simples.</span><span class="sxs-lookup"><span data-stu-id="d5497-185">Clustering can also be used to identify relationships in a dataset that you might not logically derive by browsing or simple observation.</span></span> <span data-ttu-id="d5497-186">As entradas e saídas de um algoritmo de clustering depende a metodologia escolhida.</span><span class="sxs-lookup"><span data-stu-id="d5497-186">The inputs and outputs of a clustering algorithm depends on the methodology chosen.</span></span> <span data-ttu-id="d5497-187">Você pode usar uma abordagem baseada em distribuição, centroide, conectividade ou densidade.</span><span class="sxs-lookup"><span data-stu-id="d5497-187">You can take a distribution, centroid, connectivity, or density-based approach.</span></span> <span data-ttu-id="d5497-188">Atualmente, o ML.NET oferece suporte a uma abordagem baseada em centroides usando o clustering de K-Means.</span><span class="sxs-lookup"><span data-stu-id="d5497-188">ML.NET currently supports a centroid-based approach using K-Means clustering.</span></span> <span data-ttu-id="d5497-189">Exemplos de cenários de clustering incluem:</span><span class="sxs-lookup"><span data-stu-id="d5497-189">Examples of clustering scenarios include:</span></span>

* <span data-ttu-id="d5497-190">Compreender os segmentos de hóspedes do hotel com base nos hábitos e características das opções de hotel.</span><span class="sxs-lookup"><span data-stu-id="d5497-190">Understanding segments of hotel guests based on habits and characteristics of hotel choices.</span></span>
* <span data-ttu-id="d5497-191">Identificar segmentos de clientes e dados demográficos para ajudar a criar campanhas de publicidade segmentadas.</span><span class="sxs-lookup"><span data-stu-id="d5497-191">Identifying customer segments and demographics to help build targeted advertising campaigns.</span></span>
* <span data-ttu-id="d5497-192">Categorizar o inventário com base nas métricas de fabricação.</span><span class="sxs-lookup"><span data-stu-id="d5497-192">Categorizing inventory based on manufacturing metrics.</span></span>

### <a name="clustering-trainer"></a><span data-ttu-id="d5497-193">Treinador de clustering</span><span class="sxs-lookup"><span data-stu-id="d5497-193">Clustering trainer</span></span>

<span data-ttu-id="d5497-194">Você pode treinar um modelo de clustering usando os seguintes algoritmos:</span><span class="sxs-lookup"><span data-stu-id="d5497-194">You can train a clustering model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.KMeansTrainer>

### <a name="clustering-inputs-and-outputs"></a><span data-ttu-id="d5497-195">Entradas e saídas de clustering</span><span class="sxs-lookup"><span data-stu-id="d5497-195">Clustering inputs and outputs</span></span>

<span data-ttu-id="d5497-196">Os dados de recursos de entrada devem ser <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="d5497-196">The input features data must be <xref:System.Single>.</span></span> <span data-ttu-id="d5497-197">Nenhum rótulo é necessário.</span><span class="sxs-lookup"><span data-stu-id="d5497-197">No labels are needed.</span></span>

<span data-ttu-id="d5497-198">Este treinador produz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d5497-198">This trainer outputs the following:</span></span>

| <span data-ttu-id="d5497-199">Nome de Saída</span><span class="sxs-lookup"><span data-stu-id="d5497-199">Output Name</span></span> | <span data-ttu-id="d5497-200">Digite</span><span class="sxs-lookup"><span data-stu-id="d5497-200">Type</span></span> | <span data-ttu-id="d5497-201">Descrição</span><span class="sxs-lookup"><span data-stu-id="d5497-201">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="d5497-202">vetor de <xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="d5497-202">vector of <xref:System.Single></span></span> | <span data-ttu-id="d5497-203">As distâncias do ponto de dados fornecido para todos os centroides</span><span class="sxs-lookup"><span data-stu-id="d5497-203">The distances of the given data point to all clusters' centriods</span></span> |
| `PredictedLabel` | <span data-ttu-id="d5497-204">Tipo de [chave](xref:Microsoft.ML.Data.KeyDataViewType)</span><span class="sxs-lookup"><span data-stu-id="d5497-204">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="d5497-205">O índice do cluster mais próximo previsto pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="d5497-205">The closest cluster's index predicted by the model.</span></span> |

## <a name="anomaly-detection"></a><span data-ttu-id="d5497-206">Detecção de anomalias</span><span class="sxs-lookup"><span data-stu-id="d5497-206">Anomaly detection</span></span>

<span data-ttu-id="d5497-207">Esta tarefa cria um modelo de detecção de anomalias usando a Análise de Componente Principal (PCA).</span><span class="sxs-lookup"><span data-stu-id="d5497-207">This task creates an anomaly detection model by using Principal Component Analysis (PCA).</span></span> <span data-ttu-id="d5497-208">A Detecção de Anomalias Baseada em PCA ajuda a criar um modelo em cenários onde é fácil obter dados de treinamento de uma classe, como transações válidas, mas é difícil obter exemplos suficientes das anomalias direcionadas.</span><span class="sxs-lookup"><span data-stu-id="d5497-208">PCA-Based Anomaly Detection helps you build a model in scenarios where it is easy to obtain training data from one class, such as valid transactions, but difficult to obtain sufficient samples of the targeted anomalies.</span></span>

<span data-ttu-id="d5497-209">O PCA, uma técnica estabelecida no aprendizado de máquina, é frequentemente usado na análise exploratória de dados, pois revela a estrutura interna dos dados e explica sua variação.</span><span class="sxs-lookup"><span data-stu-id="d5497-209">An established technique in machine learning, PCA is frequently used in exploratory data analysis because it reveals the inner structure of the data and explains the variance in the data.</span></span> <span data-ttu-id="d5497-210">O PCA trabalha analisando dados que contêm muitas variáveis.</span><span class="sxs-lookup"><span data-stu-id="d5497-210">PCA works by analyzing data that contains multiple variables.</span></span> <span data-ttu-id="d5497-211">Ele procura correlações entre as variáveis e determina a combinação de valores que melhor detecta as diferenças nos resultados.</span><span class="sxs-lookup"><span data-stu-id="d5497-211">It looks for correlations among the variables and determines the combination of values that best captures differences in outcomes.</span></span> <span data-ttu-id="d5497-212">Esses valores de recursos combinados são usados para criar um espaço de recurso mais compacto chamado de componentes principais.</span><span class="sxs-lookup"><span data-stu-id="d5497-212">These combined feature values are used to create a more compact feature space called the principal components.</span></span>

<span data-ttu-id="d5497-213">A detecção de anomalias abrange várias tarefas importantes no aprendizado de máquina:</span><span class="sxs-lookup"><span data-stu-id="d5497-213">Anomaly detection encompasses many important tasks in machine learning:</span></span>

* <span data-ttu-id="d5497-214">Identificar transações que são potencialmente fraudulentas.</span><span class="sxs-lookup"><span data-stu-id="d5497-214">Identifying transactions that are potentially fraudulent.</span></span>
* <span data-ttu-id="d5497-215">Aprender padrões que indicam que ocorreu uma invasão da rede.</span><span class="sxs-lookup"><span data-stu-id="d5497-215">Learning patterns that indicate that a network intrusion has occurred.</span></span>
* <span data-ttu-id="d5497-216">Localizar clusters anormais de pacientes.</span><span class="sxs-lookup"><span data-stu-id="d5497-216">Finding abnormal clusters of patients.</span></span>
* <span data-ttu-id="d5497-217">Verificar valores inseridos em um sistema.</span><span class="sxs-lookup"><span data-stu-id="d5497-217">Checking values entered into a system.</span></span>

<span data-ttu-id="d5497-218">Como as anomalias são eventos raros por definição, pode ser difícil coletar um exemplo representativo dos dados para usar na modelagem.</span><span class="sxs-lookup"><span data-stu-id="d5497-218">Because anomalies are rare events by definition, it can be difficult to collect a representative sample of data to use for modeling.</span></span> <span data-ttu-id="d5497-219">Os algoritmos incluídos nesta categoria foram especialmente projetados para abordar os principais desafios de criar e treinar modelos usando conjuntos de dados desequilibrados.</span><span class="sxs-lookup"><span data-stu-id="d5497-219">The algorithms included in this category have been especially designed to address the core challenges of building and training models by using imbalanced data sets.</span></span>

### <a name="anomaly-detection-trainer"></a><span data-ttu-id="d5497-220">Treinador de detecção de anomalias</span><span class="sxs-lookup"><span data-stu-id="d5497-220">Anomaly detection trainer</span></span>

<span data-ttu-id="d5497-221">Você pode treinar um modelo de detecção de anomalias usando os seguintes algoritmos:</span><span class="sxs-lookup"><span data-stu-id="d5497-221">You can train an anomaly detection model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

### <a name="anomaly-detection-inputs-and-outputs"></a><span data-ttu-id="d5497-222">Saídas e entradas de detecção de anomalias</span><span class="sxs-lookup"><span data-stu-id="d5497-222">Anomaly detection inputs and outputs</span></span>

<span data-ttu-id="d5497-223">Os recursos de entrada devem ser um vetor de tamanho fixo de <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="d5497-223">The input features must be a fixed-sized vector of <xref:System.Single>.</span></span>

<span data-ttu-id="d5497-224">Este treinador produz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d5497-224">This trainer outputs the following:</span></span>

| <span data-ttu-id="d5497-225">Nome de Saída</span><span class="sxs-lookup"><span data-stu-id="d5497-225">Output Name</span></span> | <span data-ttu-id="d5497-226">Digite</span><span class="sxs-lookup"><span data-stu-id="d5497-226">Type</span></span> | <span data-ttu-id="d5497-227">Descrição</span><span class="sxs-lookup"><span data-stu-id="d5497-227">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="d5497-228">A pontuação não negativa não associada calculada pelo modelo de detecção de anomalias</span><span class="sxs-lookup"><span data-stu-id="d5497-228">The non-negative, unbounded score that was calculated by the anomaly detection model</span></span> |

## <a name="ranking"></a><span data-ttu-id="d5497-229">Classificação</span><span class="sxs-lookup"><span data-stu-id="d5497-229">Ranking</span></span>

<span data-ttu-id="d5497-230">Uma tarefa de classificação cria um classificador a partir de um conjunto de exemplos rotulados.</span><span class="sxs-lookup"><span data-stu-id="d5497-230">A ranking task constructs a ranker from a set of labeled examples.</span></span> <span data-ttu-id="d5497-231">Este conjunto de exemplo consiste em grupos de instâncias que podem ser marcados com um determinado critério.</span><span class="sxs-lookup"><span data-stu-id="d5497-231">This example set consists of instance groups that can be scored with a given criteria.</span></span> <span data-ttu-id="d5497-232">Os rótulos de classificação são { 0, 1, 2, 3, 4 } para cada instância.</span><span class="sxs-lookup"><span data-stu-id="d5497-232">The ranking labels are { 0, 1, 2, 3, 4 } for each instance.</span></span>  <span data-ttu-id="d5497-233">O classificador é treinado para classificar novos grupos de instâncias com pontuações desconhecidas para cada instância.</span><span class="sxs-lookup"><span data-stu-id="d5497-233">The ranker is trained to rank new instance groups with unknown scores for each instance.</span></span> <span data-ttu-id="d5497-234">Os aprendizes de classificação do ML.NET são baseados na [classificação de máquinas aprendidas](https://en.wikipedia.org/wiki/Learning_to_rank).</span><span class="sxs-lookup"><span data-stu-id="d5497-234">ML.NET ranking learners are [machine learned ranking](https://en.wikipedia.org/wiki/Learning_to_rank) based.</span></span>

### <a name="ranking-training-algorithms"></a><span data-ttu-id="d5497-235">Algoritmos de treinamento de classificação</span><span class="sxs-lookup"><span data-stu-id="d5497-235">Ranking training algorithms</span></span>

<span data-ttu-id="d5497-236">Você pode treinar um modelo de classificação usando os seguintes algoritmos:</span><span class="sxs-lookup"><span data-stu-id="d5497-236">You can train a ranking model with the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>

### <a name="ranking-input-and-outputs"></a><span data-ttu-id="d5497-237">Entrada e saídas de classificação</span><span class="sxs-lookup"><span data-stu-id="d5497-237">Ranking input and outputs</span></span>

<span data-ttu-id="d5497-238">O tipo de dados de rótulo de entrada deve ser do tipo [chave](xref:Microsoft.ML.Data.KeyDataViewType) ou <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="d5497-238">The input label data type must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type or <xref:System.Single>.</span></span> <span data-ttu-id="d5497-239">O valor do rótulo determina a relevância, em que valores mais altos indicam maior relevância.</span><span class="sxs-lookup"><span data-stu-id="d5497-239">The value of the label determines relevance, where higher values indicate higher relevance.</span></span> <span data-ttu-id="d5497-240">Se o rótulo for um tipo [chave](xref:Microsoft.ML.Data.KeyDataViewType), o índice de chave será o valor de relevância, em que o menor índice é o menos relevante.</span><span class="sxs-lookup"><span data-stu-id="d5497-240">If the label is a [key](xref:Microsoft.ML.Data.KeyDataViewType) type, then the key index is the relevance value, where the smallest index is the least relevant.</span></span> <span data-ttu-id="d5497-241">Se o rótulo for um <xref:System.Single>, valores maiores indicarão maior relevância.</span><span class="sxs-lookup"><span data-stu-id="d5497-241">If the label is a <xref:System.Single>, larger values indicate higher relevance.</span></span>

<span data-ttu-id="d5497-242">Os dados do recurso devem ser um vetor de tamanho fixo de <xref:System.Single> e a coluna de grupo de linha de entrada deve ser do tipo [chave](xref:Microsoft.ML.Data.KeyDataViewType).</span><span class="sxs-lookup"><span data-stu-id="d5497-242">The feature data must be a fixed size vector of <xref:System.Single> and input row group column must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>

<span data-ttu-id="d5497-243">Este treinador produz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d5497-243">This trainer outputs the following:</span></span>

| <span data-ttu-id="d5497-244">Nome de Saída</span><span class="sxs-lookup"><span data-stu-id="d5497-244">Output Name</span></span> | <span data-ttu-id="d5497-245">Digite</span><span class="sxs-lookup"><span data-stu-id="d5497-245">Type</span></span> | <span data-ttu-id="d5497-246">Descrição</span><span class="sxs-lookup"><span data-stu-id="d5497-246">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="d5497-247">A pontuação não associada calculada pelo modelo para determinar a previsão</span><span class="sxs-lookup"><span data-stu-id="d5497-247">The unbounded score that was calculated by the model to determine the prediction</span></span> |

## <a name="recommendation"></a><span data-ttu-id="d5497-248">Recomendação</span><span class="sxs-lookup"><span data-stu-id="d5497-248">Recommendation</span></span>

<span data-ttu-id="d5497-249">Uma tarefa de recomendação permite produzir uma lista de produtos ou serviços recomendados.</span><span class="sxs-lookup"><span data-stu-id="d5497-249">A recommendation task enables producing a list of recommended products or services.</span></span> <span data-ttu-id="d5497-250">O ML.NET usa a [Fatoração matricial (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), um algoritmo de [filtragem colaborativa](https://en.wikipedia.org/wiki/Collaborative_filtering) para as recomendações quando você tem dados históricos de classificação do produto em seu catálogo.</span><span class="sxs-lookup"><span data-stu-id="d5497-250">ML.NET uses [Matrix factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), a [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) algorithm for recommendations when you have historical product rating data in your catalog.</span></span> <span data-ttu-id="d5497-251">Por exemplo, você tem dados históricos de classificação de filmes para seus usuários e deseja recomendar outros filmes que eles provavelmente assistirão posteriormente.</span><span class="sxs-lookup"><span data-stu-id="d5497-251">For example, you have historical movie rating data for your users and want to recommend  other movies they are likely to watch next.</span></span>

### <a name="recommendation-training-algorithms"></a><span data-ttu-id="d5497-252">Algoritmos de treinamento de recomendação</span><span class="sxs-lookup"><span data-stu-id="d5497-252">Recommendation training algorithms</span></span>

<span data-ttu-id="d5497-253">Você pode treinar um modelo de recomendação usando os seguintes algoritmos:</span><span class="sxs-lookup"><span data-stu-id="d5497-253">You can train a recommendation model with the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>
