---
title: Tarefas de aprendizado de máquina
description: Explore as diferentes tarefas de aprendizado de máquina e as tarefas associadas compatíveis com o ML.NET.
ms.custom: seodec18
ms.date: 04/23/2019
author: natke
ms.openlocfilehash: ed6361fdcbca11c100ee5cae4ca76e152ddfba11
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063536"
---
# <a name="machine-learning-tasks-in-mlnet"></a><span data-ttu-id="7e37a-103">Tarefas de aprendizado de máquina no ML.NET</span><span class="sxs-lookup"><span data-stu-id="7e37a-103">Machine learning tasks in ML.NET</span></span>

<span data-ttu-id="7e37a-104">Ao criar um modelo de aprendizado de máquina, primeiro é preciso definir o que você espera conseguir com seus dados.</span><span class="sxs-lookup"><span data-stu-id="7e37a-104">When building a machine learning model, you first need to define what you are hoping to achieve with your data.</span></span> <span data-ttu-id="7e37a-105">Isso permite escolher a tarefa de aprendizado de máquina correta para sua situação.</span><span class="sxs-lookup"><span data-stu-id="7e37a-105">This allows you to choose the right machine learning task for your situation.</span></span> <span data-ttu-id="7e37a-106">A lista a seguir descreve as diferentes tarefas de aprendizado de máquina que você pode escolher e alguns casos de uso comuns.</span><span class="sxs-lookup"><span data-stu-id="7e37a-106">The following list describes the different machine learning tasks that you can choose from and some common use cases.</span></span>

<span data-ttu-id="7e37a-107">Depois de decidir a tarefa ideal para seu cenário, será preciso escolher o melhor algoritmo para treinar seu modelo.</span><span class="sxs-lookup"><span data-stu-id="7e37a-107">Once you have decided which task works for your scenario, then you need to choose the best algorithm to train your model.</span></span> <span data-ttu-id="7e37a-108">Os algoritmos disponíveis são listados na seção para cada tarefa.</span><span class="sxs-lookup"><span data-stu-id="7e37a-108">The available algorithms are listed in the section for each task.</span></span>

## <a name="binary-classification"></a><span data-ttu-id="7e37a-109">Classificação binária</span><span class="sxs-lookup"><span data-stu-id="7e37a-109">Binary classification</span></span>

<span data-ttu-id="7e37a-110">Uma tarefa de [aprendizado de máquina supervisionado](glossary.md#supervised-machine-learning) que é usada para prever a qual das duas classes (categorias) uma instância de dados pertence.</span><span class="sxs-lookup"><span data-stu-id="7e37a-110">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict which of two classes (categories) an instance of data belongs to.</span></span> <span data-ttu-id="7e37a-111">A entrada de um algoritmo de classificação é um conjunto de exemplos rotulados, em que cada rótulo é um número inteiro de 0 ou 1.</span><span class="sxs-lookup"><span data-stu-id="7e37a-111">The input of a classification algorithm is a set of labeled examples, where each label is an integer of either 0 or 1.</span></span> <span data-ttu-id="7e37a-112">A saída de um algoritmo de classificação binária é um classificador, que pode ser usado para prever a classe de novas instâncias sem rótulo.</span><span class="sxs-lookup"><span data-stu-id="7e37a-112">The output of a binary classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="7e37a-113">Exemplos de cenários de classificação binária incluem:</span><span class="sxs-lookup"><span data-stu-id="7e37a-113">Examples of binary classification scenarios include:</span></span>

* <span data-ttu-id="7e37a-114">[Reconhece](../tutorials/sentiment-analysis.md) como "positivo" ou "negativo".</span><span class="sxs-lookup"><span data-stu-id="7e37a-114">[Understanding sentiment of Twitter comments](../tutorials/sentiment-analysis.md) as either "positive" or "negative".</span></span>
* <span data-ttu-id="7e37a-115">Diagnosticar se um paciente tem uma determinada doença ou não.</span><span class="sxs-lookup"><span data-stu-id="7e37a-115">Diagnosing whether a patient has a certain disease or not.</span></span>
* <span data-ttu-id="7e37a-116">Tomar a decisão de marcar um email como "spam" ou não.</span><span class="sxs-lookup"><span data-stu-id="7e37a-116">Making a decision to mark an email as "spam" or not.</span></span>
* <span data-ttu-id="7e37a-117">Determinar se uma foto exibe um cachorro ou frutas.</span><span class="sxs-lookup"><span data-stu-id="7e37a-117">Determining if a photo contains a dog or fruit.</span></span>

<span data-ttu-id="7e37a-118">Para obter mais informações, consulte o artigo [Classificação binária](https://en.wikipedia.org/wiki/Binary_classification) na Wikipédia.</span><span class="sxs-lookup"><span data-stu-id="7e37a-118">For more information, see the [Binary classification](https://en.wikipedia.org/wiki/Binary_classification) article on Wikipedia.</span></span>

### <a name="binary-classification-trainers"></a><span data-ttu-id="7e37a-119">Treinadores da classificação binária</span><span class="sxs-lookup"><span data-stu-id="7e37a-119">Binary classification trainers</span></span>

<span data-ttu-id="7e37a-120">Você pode treinar um modelo de classificação binária usando os seguintes algoritmos:</span><span class="sxs-lookup"><span data-stu-id="7e37a-120">You can train a binary classification model using the following algorithms:</span></span>

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

### <a name="binary-classification-inputs-and-outputs"></a><span data-ttu-id="7e37a-121">Saídas e entradas de classificação binária</span><span class="sxs-lookup"><span data-stu-id="7e37a-121">Binary classification inputs and outputs</span></span>

<span data-ttu-id="7e37a-122">Para obter melhores resultados com a classificação binária, os dados de treinamento devem ser equilibrados (ou seja, números iguais de dados de treinamento positivos e negativos).</span><span class="sxs-lookup"><span data-stu-id="7e37a-122">For best results with binary classification, the training data should be balanced (i.e. equal numbers of positive and negative training data).</span></span> <span data-ttu-id="7e37a-123">Ausente e valores devem ser manipulados antes do treinamento.</span><span class="sxs-lookup"><span data-stu-id="7e37a-123">Missing and values should be handled before training.</span></span>

<span data-ttu-id="7e37a-124">Os dados da coluna de rótulo de entrada devem ser <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="7e37a-124">The input label column data must be <xref:System.Boolean>.</span></span>
<span data-ttu-id="7e37a-125">Os dados da coluna de recursos de entrada devem ser um vetor de tamanho fixo de <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="7e37a-125">The input features column data must be a fixed-size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="7e37a-126">Esses treinadores geram as seguintes colunas:</span><span class="sxs-lookup"><span data-stu-id="7e37a-126">These trainers outputs the following columns:</span></span>

| <span data-ttu-id="7e37a-127">Nome da Coluna de Saída</span><span class="sxs-lookup"><span data-stu-id="7e37a-127">Output Column Name</span></span> | <span data-ttu-id="7e37a-128">Tipo de coluna</span><span class="sxs-lookup"><span data-stu-id="7e37a-128">Column Type</span></span> | <span data-ttu-id="7e37a-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e37a-129">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="7e37a-130">A pontuação bruta calculada pelo modelo</span><span class="sxs-lookup"><span data-stu-id="7e37a-130">The raw score that was calculated by the model</span></span>|
| `PredictedLabel` | <xref:System.Boolean> | <span data-ttu-id="7e37a-131">O rótulo previsto com base no sinal da pontuação.</span><span class="sxs-lookup"><span data-stu-id="7e37a-131">The predicted label, based on the sign of the score.</span></span> <span data-ttu-id="7e37a-132">Uma pontuação negativa é mapeada para `false` e uma pontuação positiva é mapeada para `true`.</span><span class="sxs-lookup"><span data-stu-id="7e37a-132">A negative score maps to `false` and a positive score maps to `true`.</span></span>|

## <a name="multiclass-classification"></a><span data-ttu-id="7e37a-133">Classificação multiclasse</span><span class="sxs-lookup"><span data-stu-id="7e37a-133">Multiclass classification</span></span>

<span data-ttu-id="7e37a-134">Uma tarefa de [aprendizado de máquina supervisionado](glossary.md#supervised-machine-learning) que é usada para prever a classe (categoria) de uma instância de dados.</span><span class="sxs-lookup"><span data-stu-id="7e37a-134">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the class (category) of an instance of data.</span></span> <span data-ttu-id="7e37a-135">A entrada de um algoritmo de classificação é um conjunto de exemplos rotulados.</span><span class="sxs-lookup"><span data-stu-id="7e37a-135">The input of a classification algorithm is a set of labeled examples.</span></span> <span data-ttu-id="7e37a-136">Cada rótulo normalmente começa como texto.</span><span class="sxs-lookup"><span data-stu-id="7e37a-136">Each label normally starts as text.</span></span> <span data-ttu-id="7e37a-137">Ele é executado por meio de TermTransform, que converte-o para o tipo de Chave (numérico).</span><span class="sxs-lookup"><span data-stu-id="7e37a-137">It is then run through the TermTransform, which converts it to the Key (numeric) type.</span></span> <span data-ttu-id="7e37a-138">A saída de um algoritmo de classificação é um classificador, que pode ser usado para prever a classe de novas instâncias sem rótulo.</span><span class="sxs-lookup"><span data-stu-id="7e37a-138">The output of a classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="7e37a-139">Exemplos de cenários de classificação multiclasse incluem:</span><span class="sxs-lookup"><span data-stu-id="7e37a-139">Examples of multi-class classification scenarios include:</span></span>

* <span data-ttu-id="7e37a-140">Determinar a raça de um cão como um "Husky Siberiano", "Golden Retriever", "Poodle", etc.</span><span class="sxs-lookup"><span data-stu-id="7e37a-140">Determining the breed of a dog as a "Siberian Husky", "Golden Retriever", "Poodle", etc.</span></span>
* <span data-ttu-id="7e37a-141">Entender as resenhas de filmes como "positivas", "neutras" ou "negativas".</span><span class="sxs-lookup"><span data-stu-id="7e37a-141">Understanding movie reviews as "positive", "neutral", or "negative".</span></span>
* <span data-ttu-id="7e37a-142">Categorizar as avaliações de hotel como "local", "preço", "limpeza", etc.</span><span class="sxs-lookup"><span data-stu-id="7e37a-142">Categorizing hotel reviews as "location", "price", "cleanliness", etc.</span></span>

<span data-ttu-id="7e37a-143">Para obter mais informações, consulte o artigo [Classificação multiclasse](https://en.wikipedia.org/wiki/Multiclass_classification) na Wikipédia.</span><span class="sxs-lookup"><span data-stu-id="7e37a-143">For more information, see the [Multiclass classification](https://en.wikipedia.org/wiki/Multiclass_classification) article on Wikipedia.</span></span>

>[!NOTE]
><span data-ttu-id="7e37a-144">Uma vs todas as atualizações de [aprendizes de classificação binária](#binary-classification) para atuar em conjuntos de dados multiclasse.</span><span class="sxs-lookup"><span data-stu-id="7e37a-144">One vs all upgrades any [binary classification learner](#binary-classification) to act on multiclass datasets.</span></span> <span data-ttu-id="7e37a-145">Mais informações em [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span><span class="sxs-lookup"><span data-stu-id="7e37a-145">More information on [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span></span>

### <a name="multiclass-classification-trainers"></a><span data-ttu-id="7e37a-146">Treinadores de classificação multiclasse</span><span class="sxs-lookup"><span data-stu-id="7e37a-146">Multiclass classification trainers</span></span>

<span data-ttu-id="7e37a-147">Você pode treinar um modelo de classificação multiclasse usando os seguintes algoritmos de treinamento:</span><span class="sxs-lookup"><span data-stu-id="7e37a-147">You can train a multiclass classification model using the following training algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer> 
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer> 
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer> 

### <a name="multiclass-classification-inputs-and-outputs"></a><span data-ttu-id="7e37a-148">Saídas e entradas de classificação multiclasse</span><span class="sxs-lookup"><span data-stu-id="7e37a-148">Multiclass classification inputs and outputs</span></span>

<span data-ttu-id="7e37a-149">Os dados da coluna de rótulo de entrada devem ser do tipo [chave](xref:Microsoft.ML.Data.KeyDataViewType).</span><span class="sxs-lookup"><span data-stu-id="7e37a-149">The input label column data must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>
<span data-ttu-id="7e37a-150">A coluna de recursos deve ser um vetor de tamanho fixo de <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="7e37a-150">The feature column must be a fixed size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="7e37a-151">Este treinador produz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="7e37a-151">This trainer outputs the following:</span></span>

| <span data-ttu-id="7e37a-152">Nome de Saída</span><span class="sxs-lookup"><span data-stu-id="7e37a-152">Output Name</span></span> | <span data-ttu-id="7e37a-153">Tipo</span><span class="sxs-lookup"><span data-stu-id="7e37a-153">Type</span></span> | <span data-ttu-id="7e37a-154">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e37a-154">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="7e37a-155">Vetor de <xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="7e37a-155">Vector of <xref:System.Single></span></span> | <span data-ttu-id="7e37a-156">As pontuações de todas as classes.</span><span class="sxs-lookup"><span data-stu-id="7e37a-156">The scores of all classes.</span></span> <span data-ttu-id="7e37a-157">Um valor mais alto significa maior probabilidade de se enquadrar na classe associada.</span><span class="sxs-lookup"><span data-stu-id="7e37a-157">Higher value means higher probability to fall into the associated class.</span></span> <span data-ttu-id="7e37a-158">Se o elemento iº elemento tiver o maior valor, o índice de rótulo previsto será i.</span><span class="sxs-lookup"><span data-stu-id="7e37a-158">If the i-th element has the largest value, the predicted label index would be i.</span></span> <span data-ttu-id="7e37a-159">Observe que i é o índice baseado em zero.</span><span class="sxs-lookup"><span data-stu-id="7e37a-159">Note that i is zero-based index.</span></span> |
| `PredictedLabel` | <span data-ttu-id="7e37a-160">Tipo de [chave](xref:Microsoft.ML.Data.KeyDataViewType)</span><span class="sxs-lookup"><span data-stu-id="7e37a-160">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="7e37a-161">O índice do rótulo previsto.</span><span class="sxs-lookup"><span data-stu-id="7e37a-161">The predicted label's index.</span></span> <span data-ttu-id="7e37a-162">Se seu valor for i, o rótulo real será a iº categoria no tipo de rótulo de entrada com valor de chave.</span><span class="sxs-lookup"><span data-stu-id="7e37a-162">If its value is i, the actual label would be the i-th category in the key-valued input label type.</span></span> |

## <a name="regression"></a><span data-ttu-id="7e37a-163">Regressão</span><span class="sxs-lookup"><span data-stu-id="7e37a-163">Regression</span></span>

<span data-ttu-id="7e37a-164">Uma tarefa de [aprendizado de máquina supervisionado](glossary.md#supervised-machine-learning) que é usada para prever o valor do rótulo de um conjunto de recursos relacionados.</span><span class="sxs-lookup"><span data-stu-id="7e37a-164">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the value of the label from a set of related features.</span></span> <span data-ttu-id="7e37a-165">O rótulo pode ser de qualquer valor real e não pertence a um conjunto finito de valores como nas tarefas de classificação.</span><span class="sxs-lookup"><span data-stu-id="7e37a-165">The label can be of any real value and is not from a finite set of values as in classification tasks.</span></span> <span data-ttu-id="7e37a-166">Os algoritmos de regressão modelam a dependência do rótulo em seus recursos relacionados para determinar como o rótulo será alterado à medida que os valores dos recursos forem variados.</span><span class="sxs-lookup"><span data-stu-id="7e37a-166">Regression algorithms model the dependency of the label on its related features to determine how the label will change as the values of the features are varied.</span></span> <span data-ttu-id="7e37a-167">A entrada de um algoritmo de regressão é um conjunto de exemplos com rótulos de valores conhecidos.</span><span class="sxs-lookup"><span data-stu-id="7e37a-167">The input of a regression algorithm is a set of examples with labels of known values.</span></span> <span data-ttu-id="7e37a-168">A saída de um algoritmo de regressão é uma função, que você pode usar para prever o valor de rótulo para qualquer novo conjunto de recursos de entrada.</span><span class="sxs-lookup"><span data-stu-id="7e37a-168">The output of a regression algorithm is a function, which you can use to predict the label value for any new set of input features.</span></span> <span data-ttu-id="7e37a-169">Exemplos de cenários de regressão incluem:</span><span class="sxs-lookup"><span data-stu-id="7e37a-169">Examples of regression scenarios include:</span></span>

* <span data-ttu-id="7e37a-170">Previsão de preços de casas com base nos atributos da casa, como número de quartos, localização ou tamanho.</span><span class="sxs-lookup"><span data-stu-id="7e37a-170">Predicting house prices based on house attributes such as number of bedrooms, location, or size.</span></span>
* <span data-ttu-id="7e37a-171">Previsão de preços futuros de ações com base em dados históricos e tendências atuais do mercado.</span><span class="sxs-lookup"><span data-stu-id="7e37a-171">Predicting future stock prices based on historical data and current market trends.</span></span>
* <span data-ttu-id="7e37a-172">Previsão de vendas de um produto com base em orçamentos de publicidade.</span><span class="sxs-lookup"><span data-stu-id="7e37a-172">Predicting sales of a product based on advertising budgets.</span></span>

### <a name="regression-trainers"></a><span data-ttu-id="7e37a-173">Treinadores de regressão</span><span class="sxs-lookup"><span data-stu-id="7e37a-173">Regression trainers</span></span>

<span data-ttu-id="7e37a-174">Você pode treinar um modelo de regressão usando os seguintes algoritmos:</span><span class="sxs-lookup"><span data-stu-id="7e37a-174">You can train a regression model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer> 
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>

### <a name="regression-inputs-and-outputs"></a><span data-ttu-id="7e37a-175">Saídas e entradas de regressão</span><span class="sxs-lookup"><span data-stu-id="7e37a-175">Regression inputs and outputs</span></span>

<span data-ttu-id="7e37a-176">Os dados da coluna de rótulo de entrada devem ser <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="7e37a-176">The input label column data must be <xref:System.Single>.</span></span>

<span data-ttu-id="7e37a-177">Os treinadores para esta tarefa produzem a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="7e37a-177">The trainers for this task output the following:</span></span>

| <span data-ttu-id="7e37a-178">Nome de Saída</span><span class="sxs-lookup"><span data-stu-id="7e37a-178">Output Name</span></span> | <span data-ttu-id="7e37a-179">Tipo</span><span class="sxs-lookup"><span data-stu-id="7e37a-179">Type</span></span> | <span data-ttu-id="7e37a-180">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e37a-180">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="7e37a-181">A pontuação bruta prevista pelo modelo</span><span class="sxs-lookup"><span data-stu-id="7e37a-181">The raw score that was predicted by the model</span></span> |

## <a name="clustering"></a><span data-ttu-id="7e37a-182">Clustering</span><span class="sxs-lookup"><span data-stu-id="7e37a-182">Clustering</span></span>

<span data-ttu-id="7e37a-183">Uma tarefa de [aprendizado de máquina não supervisionado](glossary.md#unsupervised-machine-learning) que é usada para agrupar instâncias de dados em clusters que contêm características semelhantes.</span><span class="sxs-lookup"><span data-stu-id="7e37a-183">An [unsupervised machine learning](glossary.md#unsupervised-machine-learning) task that is used to group instances of data into clusters that contain similar characteristics.</span></span> <span data-ttu-id="7e37a-184">O clustering também pode ser usado para identificar relacionamentos em um conjunto de dados que você pode não obter logicamente por meio de navegação ou observação simples.</span><span class="sxs-lookup"><span data-stu-id="7e37a-184">Clustering can also be used to identify relationships in a dataset that you might not logically derive by browsing or simple observation.</span></span> <span data-ttu-id="7e37a-185">As entradas e saídas de um algoritmo de clustering depende a metodologia escolhida.</span><span class="sxs-lookup"><span data-stu-id="7e37a-185">The inputs and outputs of a clustering algorithm depends on the methodology chosen.</span></span> <span data-ttu-id="7e37a-186">Você pode usar uma abordagem baseada em distribuição, centroide, conectividade ou densidade.</span><span class="sxs-lookup"><span data-stu-id="7e37a-186">You can take a distribution, centroid, connectivity, or density-based approach.</span></span> <span data-ttu-id="7e37a-187">Atualmente, o ML.NET oferece suporte a uma abordagem baseada em centroides usando o clustering de K-Means.</span><span class="sxs-lookup"><span data-stu-id="7e37a-187">ML.NET currently supports a centroid-based approach using K-Means clustering.</span></span> <span data-ttu-id="7e37a-188">Exemplos de cenários de clustering incluem:</span><span class="sxs-lookup"><span data-stu-id="7e37a-188">Examples of clustering scenarios include:</span></span>

* <span data-ttu-id="7e37a-189">Compreender os segmentos de hóspedes do hotel com base nos hábitos e características das opções de hotel.</span><span class="sxs-lookup"><span data-stu-id="7e37a-189">Understanding segments of hotel guests based on habits and characteristics of hotel choices.</span></span>
* <span data-ttu-id="7e37a-190">Identificar segmentos de clientes e dados demográficos para ajudar a criar campanhas de publicidade segmentadas.</span><span class="sxs-lookup"><span data-stu-id="7e37a-190">Identifying customer segments and demographics to help build targeted advertising campaigns.</span></span>
* <span data-ttu-id="7e37a-191">Categorizar o inventário com base nas métricas de fabricação.</span><span class="sxs-lookup"><span data-stu-id="7e37a-191">Categorizing inventory based on manufacturing metrics.</span></span>

### <a name="clustering-trainer"></a><span data-ttu-id="7e37a-192">Treinador de clustering</span><span class="sxs-lookup"><span data-stu-id="7e37a-192">Clustering trainer</span></span>

<span data-ttu-id="7e37a-193">Você pode treinar um modelo de clustering usando os seguintes algoritmos:</span><span class="sxs-lookup"><span data-stu-id="7e37a-193">You can train a clustering model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.KMeansTrainer> 

### <a name="clustering-inputs-and-outputs"></a><span data-ttu-id="7e37a-194">Entradas e saídas de clustering</span><span class="sxs-lookup"><span data-stu-id="7e37a-194">Clustering inputs and outputs</span></span>

<span data-ttu-id="7e37a-195">Os dados de recursos de entrada devem ser <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="7e37a-195">The input features data must be <xref:System.Single>.</span></span> <span data-ttu-id="7e37a-196">Nenhum rótulo é necessário.</span><span class="sxs-lookup"><span data-stu-id="7e37a-196">No labels are needed.</span></span>

<span data-ttu-id="7e37a-197">Este treinador produz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="7e37a-197">This trainer outputs the following:</span></span>

| <span data-ttu-id="7e37a-198">Nome de Saída</span><span class="sxs-lookup"><span data-stu-id="7e37a-198">Output Name</span></span> | <span data-ttu-id="7e37a-199">Tipo</span><span class="sxs-lookup"><span data-stu-id="7e37a-199">Type</span></span> | <span data-ttu-id="7e37a-200">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e37a-200">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="7e37a-201">vetor de <xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="7e37a-201">vector of <xref:System.Single></span></span> | <span data-ttu-id="7e37a-202">As distâncias do ponto de dados fornecido para todos os centroides</span><span class="sxs-lookup"><span data-stu-id="7e37a-202">The distances of the given data point to all clusters' centriods</span></span> |
| `PredictedLabel` | <span data-ttu-id="7e37a-203">Tipo de [chave](xref:Microsoft.ML.Data.KeyDataViewType)</span><span class="sxs-lookup"><span data-stu-id="7e37a-203">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="7e37a-204">O índice do cluster mais próximo previsto pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="7e37a-204">The closest cluster's index predicted by the model.</span></span> |

## <a name="anomaly-detection"></a><span data-ttu-id="7e37a-205">Detecção de anomalias</span><span class="sxs-lookup"><span data-stu-id="7e37a-205">Anomaly detection</span></span>

<span data-ttu-id="7e37a-206">Esta tarefa cria um modelo de detecção de anomalias usando a Análise de Componente Principal (PCA).</span><span class="sxs-lookup"><span data-stu-id="7e37a-206">This task creates an anomaly detection model by using Principal Component Analysis (PCA).</span></span> <span data-ttu-id="7e37a-207">A Detecção de Anomalias Baseada em PCA ajuda a criar um modelo em cenários onde é fácil obter dados de treinamento de uma classe, como transações válidas, mas é difícil obter exemplos suficientes das anomalias direcionadas.</span><span class="sxs-lookup"><span data-stu-id="7e37a-207">PCA-Based Anomaly Detection helps you build a model in scenarios where it is easy to obtain training data from one class, such as valid transactions, but difficult to obtain sufficient samples of the targeted anomalies.</span></span>

<span data-ttu-id="7e37a-208">O PCA, uma técnica estabelecida no aprendizado de máquina, é frequentemente usado na análise exploratória de dados, pois revela a estrutura interna dos dados e explica sua variação.</span><span class="sxs-lookup"><span data-stu-id="7e37a-208">An established technique in machine learning, PCA is frequently used in exploratory data analysis because it reveals the inner structure of the data and explains the variance in the data.</span></span> <span data-ttu-id="7e37a-209">O PCA trabalha analisando dados que contêm muitas variáveis.</span><span class="sxs-lookup"><span data-stu-id="7e37a-209">PCA works by analyzing data that contains multiple variables.</span></span> <span data-ttu-id="7e37a-210">Ele procura correlações entre as variáveis e determina a combinação de valores que melhor detecta as diferenças nos resultados.</span><span class="sxs-lookup"><span data-stu-id="7e37a-210">It looks for correlations among the variables and determines the combination of values that best captures differences in outcomes.</span></span> <span data-ttu-id="7e37a-211">Esses valores de recursos combinados são usados para criar um espaço de recurso mais compacto chamado de componentes principais.</span><span class="sxs-lookup"><span data-stu-id="7e37a-211">These combined feature values are used to create a more compact feature space called the principal components.</span></span>

<span data-ttu-id="7e37a-212">A detecção de anomalias abrange várias tarefas importantes no aprendizado de máquina:</span><span class="sxs-lookup"><span data-stu-id="7e37a-212">Anomaly detection encompasses many important tasks in machine learning:</span></span>

* <span data-ttu-id="7e37a-213">Identificar transações que são potencialmente fraudulentas.</span><span class="sxs-lookup"><span data-stu-id="7e37a-213">Identifying transactions that are potentially fraudulent.</span></span>
* <span data-ttu-id="7e37a-214">Aprender padrões que indicam que ocorreu uma invasão da rede.</span><span class="sxs-lookup"><span data-stu-id="7e37a-214">Learning patterns that indicate that a network intrusion has occurred.</span></span>
* <span data-ttu-id="7e37a-215">Localizar clusters anormais de pacientes.</span><span class="sxs-lookup"><span data-stu-id="7e37a-215">Finding abnormal clusters of patients.</span></span>
* <span data-ttu-id="7e37a-216">Verificar valores inseridos em um sistema.</span><span class="sxs-lookup"><span data-stu-id="7e37a-216">Checking values entered into a system.</span></span>

<span data-ttu-id="7e37a-217">Como as anomalias são eventos raros por definição, pode ser difícil coletar um exemplo representativo dos dados para usar na modelagem.</span><span class="sxs-lookup"><span data-stu-id="7e37a-217">Because anomalies are rare events by definition, it can be difficult to collect a representative sample of data to use for modeling.</span></span> <span data-ttu-id="7e37a-218">Os algoritmos incluídos nesta categoria foram especialmente projetados para abordar os principais desafios de criar e treinar modelos usando conjuntos de dados desequilibrados.</span><span class="sxs-lookup"><span data-stu-id="7e37a-218">The algorithms included in this category have been especially designed to address the core challenges of building and training models by using imbalanced data sets.</span></span>

### <a name="anomaly-detection-trainer"></a><span data-ttu-id="7e37a-219">Treinador de detecção de anomalias</span><span class="sxs-lookup"><span data-stu-id="7e37a-219">Anomaly detection trainer</span></span>

<span data-ttu-id="7e37a-220">Você pode treinar um modelo de detecção de anomalias usando os seguintes algoritmos:</span><span class="sxs-lookup"><span data-stu-id="7e37a-220">You can train an anomaly detection model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

### <a name="anomaly-detection-inputs-and-outputs"></a><span data-ttu-id="7e37a-221">Saídas e entradas de detecção de anomalias</span><span class="sxs-lookup"><span data-stu-id="7e37a-221">Anomaly detection inputs and outputs</span></span>

<span data-ttu-id="7e37a-222">Os recursos de entrada devem ser um vetor de tamanho fixo de <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="7e37a-222">The input features must be a fixed-sized vector of <xref:System.Single>.</span></span>

<span data-ttu-id="7e37a-223">Este treinador produz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="7e37a-223">This trainer outputs the following:</span></span>

| <span data-ttu-id="7e37a-224">Nome de Saída</span><span class="sxs-lookup"><span data-stu-id="7e37a-224">Output Name</span></span> | <span data-ttu-id="7e37a-225">Tipo</span><span class="sxs-lookup"><span data-stu-id="7e37a-225">Type</span></span> | <span data-ttu-id="7e37a-226">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e37a-226">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="7e37a-227">A pontuação não negativa não associada calculada pelo modelo de detecção de anomalias</span><span class="sxs-lookup"><span data-stu-id="7e37a-227">The non-negative, unbounded score that was calculated by the anomaly detection model</span></span> |

## <a name="ranking"></a><span data-ttu-id="7e37a-228">Classificação</span><span class="sxs-lookup"><span data-stu-id="7e37a-228">Ranking</span></span>

<span data-ttu-id="7e37a-229">Uma tarefa de classificação cria um classificador a partir de um conjunto de exemplos rotulados.</span><span class="sxs-lookup"><span data-stu-id="7e37a-229">A ranking task constructs a ranker from a set of labeled examples.</span></span> <span data-ttu-id="7e37a-230">Este conjunto de exemplo consiste em grupos de instâncias que podem ser marcados com um determinado critério.</span><span class="sxs-lookup"><span data-stu-id="7e37a-230">This example set consists of instance groups that can be scored with a given criteria.</span></span> <span data-ttu-id="7e37a-231">Os rótulos de classificação são { 0, 1, 2, 3, 4 } para cada instância.</span><span class="sxs-lookup"><span data-stu-id="7e37a-231">The ranking labels are { 0, 1, 2, 3, 4 } for each instance.</span></span>  <span data-ttu-id="7e37a-232">O classificador é treinado para classificar novos grupos de instâncias com pontuações desconhecidas para cada instância.</span><span class="sxs-lookup"><span data-stu-id="7e37a-232">The ranker is trained to rank new instance groups with unknown scores for each instance.</span></span> <span data-ttu-id="7e37a-233">Os aprendizes de classificação do ML.NET são baseados na [classificação de máquinas aprendidas](https://en.wikipedia.org/wiki/Learning_to_rank).</span><span class="sxs-lookup"><span data-stu-id="7e37a-233">ML.NET ranking learners are [machine learned ranking](https://en.wikipedia.org/wiki/Learning_to_rank) based.</span></span>

### <a name="ranking-training-algorithms"></a><span data-ttu-id="7e37a-234">Algoritmos de treinamento de classificação</span><span class="sxs-lookup"><span data-stu-id="7e37a-234">Ranking training algorithms</span></span>

<span data-ttu-id="7e37a-235">Você pode treinar um modelo de classificação usando os seguintes algoritmos:</span><span class="sxs-lookup"><span data-stu-id="7e37a-235">You can train a ranking model with the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer> 

### <a name="ranking-input-and-outputs"></a><span data-ttu-id="7e37a-236">Entrada e saídas de classificação</span><span class="sxs-lookup"><span data-stu-id="7e37a-236">Ranking input and outputs</span></span>

<span data-ttu-id="7e37a-237">O tipo de dados de rótulo de entrada deve ser do tipo [chave](xref:Microsoft.ML.Data.KeyDataViewType) ou <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="7e37a-237">The input label data type must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type or <xref:System.Single>.</span></span> <span data-ttu-id="7e37a-238">O valor do rótulo determina a relevância, em que valores mais altos indicam maior relevância.</span><span class="sxs-lookup"><span data-stu-id="7e37a-238">The value of the label determines relevance, where higher values indicate higher relevance.</span></span> <span data-ttu-id="7e37a-239">Se o rótulo for um tipo [chave](xref:Microsoft.ML.Data.KeyDataViewType), o índice de chave será o valor de relevância, em que o menor índice é o menos relevante.</span><span class="sxs-lookup"><span data-stu-id="7e37a-239">If the label is a [key](xref:Microsoft.ML.Data.KeyDataViewType) type, then the key index is the relevance value, where the smallest index is the least relevant.</span></span> <span data-ttu-id="7e37a-240">Se o rótulo for um <xref:System.Single>, valores maiores indicarão maior relevância.</span><span class="sxs-lookup"><span data-stu-id="7e37a-240">If the label is a <xref:System.Single>, larger values indicate higher relevance.</span></span>

<span data-ttu-id="7e37a-241">Os dados do recurso devem ser um vetor de tamanho fixo de <xref:System.Single> e a coluna de grupo de linha de entrada deve ser do tipo [chave](xref:Microsoft.ML.Data.KeyDataViewType).</span><span class="sxs-lookup"><span data-stu-id="7e37a-241">The feature data must be a fixed size vector of <xref:System.Single> and input row group column must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>

<span data-ttu-id="7e37a-242">Este treinador produz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="7e37a-242">This trainer outputs the following:</span></span>

| <span data-ttu-id="7e37a-243">Nome de Saída</span><span class="sxs-lookup"><span data-stu-id="7e37a-243">Output Name</span></span> | <span data-ttu-id="7e37a-244">Tipo</span><span class="sxs-lookup"><span data-stu-id="7e37a-244">Type</span></span> | <span data-ttu-id="7e37a-245">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e37a-245">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="7e37a-246">A pontuação não associada calculada pelo modelo para determinar a previsão</span><span class="sxs-lookup"><span data-stu-id="7e37a-246">The unbounded score that was calculated by the model to determine the prediction</span></span> |

## <a name="recommendation"></a><span data-ttu-id="7e37a-247">Recomendação</span><span class="sxs-lookup"><span data-stu-id="7e37a-247">Recommendation</span></span>

<span data-ttu-id="7e37a-248">Uma tarefa de recomendação permite produzir uma lista de produtos ou serviços recomendados.</span><span class="sxs-lookup"><span data-stu-id="7e37a-248">A recommendation task enables producing a list of recommended products or services.</span></span> <span data-ttu-id="7e37a-249">O ML.NET usa a [Fatoração matricial (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), um algoritmo de [filtragem colaborativa](https://en.wikipedia.org/wiki/Collaborative_filtering) para as recomendações quando você tem dados históricos de classificação do produto em seu catálogo.</span><span class="sxs-lookup"><span data-stu-id="7e37a-249">ML.NET uses [Matrix factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), a [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) algorithm for recommendations when you have historical product rating data in your catalog.</span></span> <span data-ttu-id="7e37a-250">Por exemplo, você tem dados históricos de classificação de filmes para seus usuários e deseja recomendar outros filmes que eles provavelmente assistirão posteriormente.</span><span class="sxs-lookup"><span data-stu-id="7e37a-250">For example, you have historical movie rating data for your users and want to recommend  other movies they are likely to watch next.</span></span>

### <a name="recommendation-training-algorithms"></a><span data-ttu-id="7e37a-251">Algoritmos de treinamento de recomendação</span><span class="sxs-lookup"><span data-stu-id="7e37a-251">Recommendation training algorithms</span></span>

<span data-ttu-id="7e37a-252">Você pode treinar um modelo de recomendação usando os seguintes algoritmos:</span><span class="sxs-lookup"><span data-stu-id="7e37a-252">You can train a recommendation model with the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>
