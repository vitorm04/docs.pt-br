---
title: Tarefas de aprendizado de máquina
description: Explore as diferentes tarefas de aprendizado de máquina e as tarefas associadas compatíveis com o ML.NET.
ms.date: 12/23/2019
ms.openlocfilehash: badb096ab3e7fbd575d8594b4fbd0e2ebaf63820
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75739633"
---
# <a name="machine-learning-tasks-in-mlnet"></a><span data-ttu-id="efa2b-103">Tarefas de aprendizado de máquina no ML.NET</span><span class="sxs-lookup"><span data-stu-id="efa2b-103">Machine learning tasks in ML.NET</span></span>

<span data-ttu-id="efa2b-104">Uma tarefa de aprendizado de máquina é o tipo de previsão ou inferência que está sendo feita, com base no problema ou na pergunta que está sendo solicitada e nos dados disponíveis.</span><span class="sxs-lookup"><span data-stu-id="efa2b-104">A machine learning task is the type of prediction or inference being made, based on the problem or question that is being asked, and the available data.</span></span> <span data-ttu-id="efa2b-105">Por exemplo, a tarefa de classificação atribui dados a categorias e a tarefa de clustering agrupa os dados de acordo com a similaridade.</span><span class="sxs-lookup"><span data-stu-id="efa2b-105">For example, the classification task assigns data to categories, and the clustering task groups data according to similarity.</span></span>

<span data-ttu-id="efa2b-106">As tarefas de aprendizado de máquina dependem de padrões nos dados em vez de serem programadas explicitamente.</span><span class="sxs-lookup"><span data-stu-id="efa2b-106">Machine learning tasks rely on patterns in the data rather than being explicitly programmed.</span></span>

<span data-ttu-id="efa2b-107">Este artigo descreve as diferentes tarefas de aprendizado de máquina que você pode escolher em ML.NET e alguns casos de uso comuns.</span><span class="sxs-lookup"><span data-stu-id="efa2b-107">This article describes the different machine learning tasks that you can choose from in ML.NET and some common use cases.</span></span>

<span data-ttu-id="efa2b-108">Depois de decidir a tarefa ideal para seu cenário, será preciso escolher o melhor algoritmo para treinar seu modelo.</span><span class="sxs-lookup"><span data-stu-id="efa2b-108">Once you have decided which task works for your scenario, then you need to choose the best algorithm to train your model.</span></span> <span data-ttu-id="efa2b-109">Os algoritmos disponíveis são listados na seção para cada tarefa.</span><span class="sxs-lookup"><span data-stu-id="efa2b-109">The available algorithms are listed in the section for each task.</span></span>

## <a name="binary-classification"></a><span data-ttu-id="efa2b-110">Classificação binária</span><span class="sxs-lookup"><span data-stu-id="efa2b-110">Binary classification</span></span>

<span data-ttu-id="efa2b-111">Uma tarefa de [aprendizado de máquina supervisionado](glossary.md#supervised-machine-learning) que é usada para prever a qual das duas classes (categorias) uma instância de dados pertence.</span><span class="sxs-lookup"><span data-stu-id="efa2b-111">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict which of two classes (categories) an instance of data belongs to.</span></span> <span data-ttu-id="efa2b-112">A entrada de um algoritmo de classificação é um conjunto de exemplos rotulados, em que cada rótulo é um número inteiro de 0 ou 1.</span><span class="sxs-lookup"><span data-stu-id="efa2b-112">The input of a classification algorithm is a set of labeled examples, where each label is an integer of either 0 or 1.</span></span> <span data-ttu-id="efa2b-113">A saída de um algoritmo de classificação binária é um classificador, que pode ser usado para prever a classe de novas instâncias sem rótulo.</span><span class="sxs-lookup"><span data-stu-id="efa2b-113">The output of a binary classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="efa2b-114">Exemplos de cenários de classificação binária incluem:</span><span class="sxs-lookup"><span data-stu-id="efa2b-114">Examples of binary classification scenarios include:</span></span>

* <span data-ttu-id="efa2b-115">[Reconhece](../tutorials/sentiment-analysis.md) como "positivo" ou "negativo".</span><span class="sxs-lookup"><span data-stu-id="efa2b-115">[Understanding sentiment of Twitter comments](../tutorials/sentiment-analysis.md) as either "positive" or "negative".</span></span>
* <span data-ttu-id="efa2b-116">Diagnosticar se um paciente tem uma determinada doença ou não.</span><span class="sxs-lookup"><span data-stu-id="efa2b-116">Diagnosing whether a patient has a certain disease or not.</span></span>
* <span data-ttu-id="efa2b-117">Tomar a decisão de marcar um email como "spam" ou não.</span><span class="sxs-lookup"><span data-stu-id="efa2b-117">Making a decision to mark an email as "spam" or not.</span></span>
* <span data-ttu-id="efa2b-118">Determinar se uma foto contém um item específico ou não, como um cão ou frutas.</span><span class="sxs-lookup"><span data-stu-id="efa2b-118">Determining if a photo contains a particular item or not, such as a dog or fruit.</span></span>

<span data-ttu-id="efa2b-119">Para obter mais informações, consulte o artigo [Classificação binária](https://en.wikipedia.org/wiki/Binary_classification) na Wikipédia.</span><span class="sxs-lookup"><span data-stu-id="efa2b-119">For more information, see the [Binary classification](https://en.wikipedia.org/wiki/Binary_classification) article on Wikipedia.</span></span>

### <a name="binary-classification-trainers"></a><span data-ttu-id="efa2b-120">Treinadores da classificação binária</span><span class="sxs-lookup"><span data-stu-id="efa2b-120">Binary classification trainers</span></span>

<span data-ttu-id="efa2b-121">Você pode treinar um modelo de classificação binária usando os seguintes algoritmos:</span><span class="sxs-lookup"><span data-stu-id="efa2b-121">You can train a binary classification model using the following algorithms:</span></span>

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

### <a name="binary-classification-inputs-and-outputs"></a><span data-ttu-id="efa2b-122">Saídas e entradas de classificação binária</span><span class="sxs-lookup"><span data-stu-id="efa2b-122">Binary classification inputs and outputs</span></span>

<span data-ttu-id="efa2b-123">Para obter melhores resultados com a classificação binária, os dados de treinamento devem ser equilibrados (ou seja, números iguais de dados de treinamento positivos e negativos).</span><span class="sxs-lookup"><span data-stu-id="efa2b-123">For best results with binary classification, the training data should be balanced (that is, equal numbers of positive and negative training data).</span></span> <span data-ttu-id="efa2b-124">Os valores ausentes devem ser manipulados antes do treinamento.</span><span class="sxs-lookup"><span data-stu-id="efa2b-124">Missing values should be handled before training.</span></span>

<span data-ttu-id="efa2b-125">Os dados da coluna de rótulo de entrada devem ser <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="efa2b-125">The input label column data must be <xref:System.Boolean>.</span></span>
<span data-ttu-id="efa2b-126">Os dados da coluna de recursos de entrada devem ser um vetor de tamanho fixo de <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="efa2b-126">The input features column data must be a fixed-size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="efa2b-127">Esses treinadores geram as seguintes colunas:</span><span class="sxs-lookup"><span data-stu-id="efa2b-127">These trainers output the following columns:</span></span>

| <span data-ttu-id="efa2b-128">Nome da Coluna de Saída</span><span class="sxs-lookup"><span data-stu-id="efa2b-128">Output Column Name</span></span> | <span data-ttu-id="efa2b-129">Tipo de coluna</span><span class="sxs-lookup"><span data-stu-id="efa2b-129">Column Type</span></span> | <span data-ttu-id="efa2b-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="efa2b-130">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="efa2b-131">A pontuação bruta calculada pelo modelo</span><span class="sxs-lookup"><span data-stu-id="efa2b-131">The raw score that was calculated by the model</span></span>|
| `PredictedLabel` | <xref:System.Boolean> | <span data-ttu-id="efa2b-132">O rótulo previsto com base no sinal da pontuação.</span><span class="sxs-lookup"><span data-stu-id="efa2b-132">The predicted label, based on the sign of the score.</span></span> <span data-ttu-id="efa2b-133">Uma pontuação negativa é mapeada para `false` e uma pontuação positiva é mapeada para `true`.</span><span class="sxs-lookup"><span data-stu-id="efa2b-133">A negative score maps to `false` and a positive score maps to `true`.</span></span>|

## <a name="multiclass-classification"></a><span data-ttu-id="efa2b-134">Classificação multiclasse</span><span class="sxs-lookup"><span data-stu-id="efa2b-134">Multiclass classification</span></span>

<span data-ttu-id="efa2b-135">Uma tarefa de [aprendizado de máquina supervisionado](glossary.md#supervised-machine-learning) que é usada para prever a classe (categoria) de uma instância de dados.</span><span class="sxs-lookup"><span data-stu-id="efa2b-135">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the class (category) of an instance of data.</span></span> <span data-ttu-id="efa2b-136">A entrada de um algoritmo de classificação é um conjunto de exemplos rotulados.</span><span class="sxs-lookup"><span data-stu-id="efa2b-136">The input of a classification algorithm is a set of labeled examples.</span></span> <span data-ttu-id="efa2b-137">Cada rótulo normalmente começa como texto.</span><span class="sxs-lookup"><span data-stu-id="efa2b-137">Each label normally starts as text.</span></span> <span data-ttu-id="efa2b-138">Ele é executado por meio de TermTransform, que converte-o para o tipo de Chave (numérico).</span><span class="sxs-lookup"><span data-stu-id="efa2b-138">It is then run through the TermTransform, which converts it to the Key (numeric) type.</span></span> <span data-ttu-id="efa2b-139">A saída de um algoritmo de classificação é um classificador, que pode ser usado para prever a classe de novas instâncias sem rótulo.</span><span class="sxs-lookup"><span data-stu-id="efa2b-139">The output of a classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="efa2b-140">Exemplos de cenários de classificação multiclasse incluem:</span><span class="sxs-lookup"><span data-stu-id="efa2b-140">Examples of multi-class classification scenarios include:</span></span>

* <span data-ttu-id="efa2b-141">Determinar a raça de um cão como um "Husky Siberiano", "Golden Retriever", "Poodle", etc.</span><span class="sxs-lookup"><span data-stu-id="efa2b-141">Determining the breed of a dog as a "Siberian Husky", "Golden Retriever", "Poodle", etc.</span></span>
* <span data-ttu-id="efa2b-142">Entender as resenhas de filmes como "positivas", "neutras" ou "negativas".</span><span class="sxs-lookup"><span data-stu-id="efa2b-142">Understanding movie reviews as "positive", "neutral", or "negative".</span></span>
* <span data-ttu-id="efa2b-143">Categorizar as avaliações de hotel como "local", "preço", "limpeza", etc.</span><span class="sxs-lookup"><span data-stu-id="efa2b-143">Categorizing hotel reviews as "location", "price", "cleanliness", etc.</span></span>

<span data-ttu-id="efa2b-144">Para obter mais informações, consulte o artigo [Classificação multiclasse](https://en.wikipedia.org/wiki/Multiclass_classification) na Wikipédia.</span><span class="sxs-lookup"><span data-stu-id="efa2b-144">For more information, see the [Multiclass classification](https://en.wikipedia.org/wiki/Multiclass_classification) article on Wikipedia.</span></span>

>[!NOTE]
><span data-ttu-id="efa2b-145">Uma vs todas as atualizações de [aprendizes de classificação binária](#binary-classification) para atuar em conjuntos de dados multiclasse.</span><span class="sxs-lookup"><span data-stu-id="efa2b-145">One vs all upgrades any [binary classification learner](#binary-classification) to act on multiclass datasets.</span></span> <span data-ttu-id="efa2b-146">Mais informações em [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span><span class="sxs-lookup"><span data-stu-id="efa2b-146">More information on [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span></span>

### <a name="multiclass-classification-trainers"></a><span data-ttu-id="efa2b-147">Treinadores de classificação multiclasse</span><span class="sxs-lookup"><span data-stu-id="efa2b-147">Multiclass classification trainers</span></span>

<span data-ttu-id="efa2b-148">Você pode treinar um modelo de classificação multiclasse usando os seguintes algoritmos de treinamento:</span><span class="sxs-lookup"><span data-stu-id="efa2b-148">You can train a multiclass classification model using the following training algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>

### <a name="multiclass-classification-inputs-and-outputs"></a><span data-ttu-id="efa2b-149">Saídas e entradas de classificação multiclasse</span><span class="sxs-lookup"><span data-stu-id="efa2b-149">Multiclass classification inputs and outputs</span></span>

<span data-ttu-id="efa2b-150">Os dados da coluna de rótulo de entrada devem ser do tipo [chave](xref:Microsoft.ML.Data.KeyDataViewType).</span><span class="sxs-lookup"><span data-stu-id="efa2b-150">The input label column data must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>
<span data-ttu-id="efa2b-151">A coluna de recursos deve ser um vetor de tamanho fixo de <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="efa2b-151">The feature column must be a fixed size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="efa2b-152">Este treinador produz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="efa2b-152">This trainer outputs the following:</span></span>

| <span data-ttu-id="efa2b-153">Nome de Saída</span><span class="sxs-lookup"><span data-stu-id="efa2b-153">Output Name</span></span> | <span data-ttu-id="efa2b-154">{1&gt;Tipo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="efa2b-154">Type</span></span> | <span data-ttu-id="efa2b-155">Descrição</span><span class="sxs-lookup"><span data-stu-id="efa2b-155">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="efa2b-156">Vetor de <xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="efa2b-156">Vector of <xref:System.Single></span></span> | <span data-ttu-id="efa2b-157">As pontuações de todas as classes.</span><span class="sxs-lookup"><span data-stu-id="efa2b-157">The scores of all classes.</span></span> <span data-ttu-id="efa2b-158">Um valor mais alto significa maior probabilidade de se enquadrar na classe associada.</span><span class="sxs-lookup"><span data-stu-id="efa2b-158">Higher value means higher probability to fall into the associated class.</span></span> <span data-ttu-id="efa2b-159">Se o elemento iº elemento tiver o maior valor, o índice de rótulo previsto será i.</span><span class="sxs-lookup"><span data-stu-id="efa2b-159">If the i-th element has the largest value, the predicted label index would be i.</span></span> <span data-ttu-id="efa2b-160">Observe que i é o índice baseado em zero.</span><span class="sxs-lookup"><span data-stu-id="efa2b-160">Note that i is zero-based index.</span></span> |
| `PredictedLabel` | <span data-ttu-id="efa2b-161">Tipo de [chave](xref:Microsoft.ML.Data.KeyDataViewType)</span><span class="sxs-lookup"><span data-stu-id="efa2b-161">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="efa2b-162">O índice do rótulo previsto.</span><span class="sxs-lookup"><span data-stu-id="efa2b-162">The predicted label's index.</span></span> <span data-ttu-id="efa2b-163">Se seu valor for i, o rótulo real será a iº categoria no tipo de rótulo de entrada com valor de chave.</span><span class="sxs-lookup"><span data-stu-id="efa2b-163">If its value is i, the actual label would be the i-th category in the key-valued input label type.</span></span> |

## <a name="regression"></a><span data-ttu-id="efa2b-164">Regressão</span><span class="sxs-lookup"><span data-stu-id="efa2b-164">Regression</span></span>

<span data-ttu-id="efa2b-165">Uma tarefa de [aprendizado de máquina supervisionado](glossary.md#supervised-machine-learning) que é usada para prever o valor do rótulo de um conjunto de recursos relacionados.</span><span class="sxs-lookup"><span data-stu-id="efa2b-165">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the value of the label from a set of related features.</span></span> <span data-ttu-id="efa2b-166">O rótulo pode ser de qualquer valor real e não pertence a um conjunto finito de valores como nas tarefas de classificação.</span><span class="sxs-lookup"><span data-stu-id="efa2b-166">The label can be of any real value and is not from a finite set of values as in classification tasks.</span></span> <span data-ttu-id="efa2b-167">Os algoritmos de regressão modelam a dependência do rótulo em seus recursos relacionados para determinar como o rótulo será alterado à medida que os valores dos recursos forem variados.</span><span class="sxs-lookup"><span data-stu-id="efa2b-167">Regression algorithms model the dependency of the label on its related features to determine how the label will change as the values of the features are varied.</span></span> <span data-ttu-id="efa2b-168">A entrada de um algoritmo de regressão é um conjunto de exemplos com rótulos de valores conhecidos.</span><span class="sxs-lookup"><span data-stu-id="efa2b-168">The input of a regression algorithm is a set of examples with labels of known values.</span></span> <span data-ttu-id="efa2b-169">A saída de um algoritmo de regressão é uma função, que você pode usar para prever o valor de rótulo para qualquer novo conjunto de recursos de entrada.</span><span class="sxs-lookup"><span data-stu-id="efa2b-169">The output of a regression algorithm is a function, which you can use to predict the label value for any new set of input features.</span></span> <span data-ttu-id="efa2b-170">Exemplos de cenários de regressão incluem:</span><span class="sxs-lookup"><span data-stu-id="efa2b-170">Examples of regression scenarios include:</span></span>

* <span data-ttu-id="efa2b-171">Previsão de preços de casas com base nos atributos da casa, como número de quartos, localização ou tamanho.</span><span class="sxs-lookup"><span data-stu-id="efa2b-171">Predicting house prices based on house attributes such as number of bedrooms, location, or size.</span></span>
* <span data-ttu-id="efa2b-172">Previsão de preços futuros de ações com base em dados históricos e tendências atuais do mercado.</span><span class="sxs-lookup"><span data-stu-id="efa2b-172">Predicting future stock prices based on historical data and current market trends.</span></span>
* <span data-ttu-id="efa2b-173">Previsão de vendas de um produto com base em orçamentos de publicidade.</span><span class="sxs-lookup"><span data-stu-id="efa2b-173">Predicting sales of a product based on advertising budgets.</span></span>

### <a name="regression-trainers"></a><span data-ttu-id="efa2b-174">Treinadores de regressão</span><span class="sxs-lookup"><span data-stu-id="efa2b-174">Regression trainers</span></span>

<span data-ttu-id="efa2b-175">Você pode treinar um modelo de regressão usando os seguintes algoritmos:</span><span class="sxs-lookup"><span data-stu-id="efa2b-175">You can train a regression model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>

### <a name="regression-inputs-and-outputs"></a><span data-ttu-id="efa2b-176">Saídas e entradas de regressão</span><span class="sxs-lookup"><span data-stu-id="efa2b-176">Regression inputs and outputs</span></span>

<span data-ttu-id="efa2b-177">Os dados da coluna de rótulo de entrada devem ser <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="efa2b-177">The input label column data must be <xref:System.Single>.</span></span>

<span data-ttu-id="efa2b-178">Os treinadores para esta tarefa produzem a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="efa2b-178">The trainers for this task output the following:</span></span>

| <span data-ttu-id="efa2b-179">Nome de Saída</span><span class="sxs-lookup"><span data-stu-id="efa2b-179">Output Name</span></span> | <span data-ttu-id="efa2b-180">{1&gt;Tipo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="efa2b-180">Type</span></span> | <span data-ttu-id="efa2b-181">Descrição</span><span class="sxs-lookup"><span data-stu-id="efa2b-181">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="efa2b-182">A pontuação bruta prevista pelo modelo</span><span class="sxs-lookup"><span data-stu-id="efa2b-182">The raw score that was predicted by the model</span></span> |

## <a name="clustering"></a><span data-ttu-id="efa2b-183">Clustering</span><span class="sxs-lookup"><span data-stu-id="efa2b-183">Clustering</span></span>

<span data-ttu-id="efa2b-184">Uma tarefa de [aprendizado de máquina não supervisionado](glossary.md#unsupervised-machine-learning) que é usada para agrupar instâncias de dados em clusters que contêm características semelhantes.</span><span class="sxs-lookup"><span data-stu-id="efa2b-184">An [unsupervised machine learning](glossary.md#unsupervised-machine-learning) task that is used to group instances of data into clusters that contain similar characteristics.</span></span> <span data-ttu-id="efa2b-185">O clustering também pode ser usado para identificar relacionamentos em um conjunto de dados que você pode não obter logicamente por meio de navegação ou observação simples.</span><span class="sxs-lookup"><span data-stu-id="efa2b-185">Clustering can also be used to identify relationships in a dataset that you might not logically derive by browsing or simple observation.</span></span> <span data-ttu-id="efa2b-186">As entradas e saídas de um algoritmo de clustering depende a metodologia escolhida.</span><span class="sxs-lookup"><span data-stu-id="efa2b-186">The inputs and outputs of a clustering algorithm depends on the methodology chosen.</span></span> <span data-ttu-id="efa2b-187">Você pode usar uma abordagem baseada em distribuição, centroide, conectividade ou densidade.</span><span class="sxs-lookup"><span data-stu-id="efa2b-187">You can take a distribution, centroid, connectivity, or density-based approach.</span></span> <span data-ttu-id="efa2b-188">Atualmente, o ML.NET oferece suporte a uma abordagem baseada em centroides usando o clustering de K-Means.</span><span class="sxs-lookup"><span data-stu-id="efa2b-188">ML.NET currently supports a centroid-based approach using K-Means clustering.</span></span> <span data-ttu-id="efa2b-189">Exemplos de cenários de clustering incluem:</span><span class="sxs-lookup"><span data-stu-id="efa2b-189">Examples of clustering scenarios include:</span></span>

* <span data-ttu-id="efa2b-190">Compreender os segmentos de hóspedes do hotel com base nos hábitos e características das opções de hotel.</span><span class="sxs-lookup"><span data-stu-id="efa2b-190">Understanding segments of hotel guests based on habits and characteristics of hotel choices.</span></span>
* <span data-ttu-id="efa2b-191">Identificar segmentos de clientes e dados demográficos para ajudar a criar campanhas de publicidade segmentadas.</span><span class="sxs-lookup"><span data-stu-id="efa2b-191">Identifying customer segments and demographics to help build targeted advertising campaigns.</span></span>
* <span data-ttu-id="efa2b-192">Categorizar o inventário com base nas métricas de fabricação.</span><span class="sxs-lookup"><span data-stu-id="efa2b-192">Categorizing inventory based on manufacturing metrics.</span></span>

### <a name="clustering-trainer"></a><span data-ttu-id="efa2b-193">Treinador de clustering</span><span class="sxs-lookup"><span data-stu-id="efa2b-193">Clustering trainer</span></span>

<span data-ttu-id="efa2b-194">Você pode treinar um modelo de clustering usando os seguintes algoritmos:</span><span class="sxs-lookup"><span data-stu-id="efa2b-194">You can train a clustering model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.KMeansTrainer>

### <a name="clustering-inputs-and-outputs"></a><span data-ttu-id="efa2b-195">Entradas e saídas de clustering</span><span class="sxs-lookup"><span data-stu-id="efa2b-195">Clustering inputs and outputs</span></span>

<span data-ttu-id="efa2b-196">Os dados de recursos de entrada devem ser <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="efa2b-196">The input features data must be <xref:System.Single>.</span></span> <span data-ttu-id="efa2b-197">Nenhum rótulo é necessário.</span><span class="sxs-lookup"><span data-stu-id="efa2b-197">No labels are needed.</span></span>

<span data-ttu-id="efa2b-198">Este treinador produz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="efa2b-198">This trainer outputs the following:</span></span>

| <span data-ttu-id="efa2b-199">Nome de Saída</span><span class="sxs-lookup"><span data-stu-id="efa2b-199">Output Name</span></span> | <span data-ttu-id="efa2b-200">{1&gt;Tipo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="efa2b-200">Type</span></span> | <span data-ttu-id="efa2b-201">Descrição</span><span class="sxs-lookup"><span data-stu-id="efa2b-201">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="efa2b-202">vetor de <xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="efa2b-202">vector of <xref:System.Single></span></span> | <span data-ttu-id="efa2b-203">As distâncias do ponto de dados fornecido para todos os centroides</span><span class="sxs-lookup"><span data-stu-id="efa2b-203">The distances of the given data point to all clusters' centriods</span></span> |
| `PredictedLabel` | <span data-ttu-id="efa2b-204">Tipo de [chave](xref:Microsoft.ML.Data.KeyDataViewType)</span><span class="sxs-lookup"><span data-stu-id="efa2b-204">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="efa2b-205">O índice do cluster mais próximo previsto pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="efa2b-205">The closest cluster's index predicted by the model.</span></span> |

## <a name="anomaly-detection"></a><span data-ttu-id="efa2b-206">Detecção de anomalias</span><span class="sxs-lookup"><span data-stu-id="efa2b-206">Anomaly detection</span></span>

<span data-ttu-id="efa2b-207">Esta tarefa cria um modelo de detecção de anomalias usando a Análise de Componente Principal (PCA).</span><span class="sxs-lookup"><span data-stu-id="efa2b-207">This task creates an anomaly detection model by using Principal Component Analysis (PCA).</span></span> <span data-ttu-id="efa2b-208">A Detecção de Anomalias Baseada em PCA ajuda a criar um modelo em cenários onde é fácil obter dados de treinamento de uma classe, como transações válidas, mas é difícil obter exemplos suficientes das anomalias direcionadas.</span><span class="sxs-lookup"><span data-stu-id="efa2b-208">PCA-Based Anomaly Detection helps you build a model in scenarios where it is easy to obtain training data from one class, such as valid transactions, but difficult to obtain sufficient samples of the targeted anomalies.</span></span>

<span data-ttu-id="efa2b-209">O PCA, uma técnica estabelecida no aprendizado de máquina, é frequentemente usado na análise exploratória de dados, pois revela a estrutura interna dos dados e explica sua variação.</span><span class="sxs-lookup"><span data-stu-id="efa2b-209">An established technique in machine learning, PCA is frequently used in exploratory data analysis because it reveals the inner structure of the data and explains the variance in the data.</span></span> <span data-ttu-id="efa2b-210">O PCA trabalha analisando dados que contêm muitas variáveis.</span><span class="sxs-lookup"><span data-stu-id="efa2b-210">PCA works by analyzing data that contains multiple variables.</span></span> <span data-ttu-id="efa2b-211">Ele procura correlações entre as variáveis e determina a combinação de valores que melhor detecta as diferenças nos resultados.</span><span class="sxs-lookup"><span data-stu-id="efa2b-211">It looks for correlations among the variables and determines the combination of values that best captures differences in outcomes.</span></span> <span data-ttu-id="efa2b-212">Esses valores de recursos combinados são usados para criar um espaço de recurso mais compacto chamado de componentes principais.</span><span class="sxs-lookup"><span data-stu-id="efa2b-212">These combined feature values are used to create a more compact feature space called the principal components.</span></span>

<span data-ttu-id="efa2b-213">A detecção de anomalias abrange várias tarefas importantes no aprendizado de máquina:</span><span class="sxs-lookup"><span data-stu-id="efa2b-213">Anomaly detection encompasses many important tasks in machine learning:</span></span>

* <span data-ttu-id="efa2b-214">Identificar transações que são potencialmente fraudulentas.</span><span class="sxs-lookup"><span data-stu-id="efa2b-214">Identifying transactions that are potentially fraudulent.</span></span>
* <span data-ttu-id="efa2b-215">Aprender padrões que indicam que ocorreu uma invasão da rede.</span><span class="sxs-lookup"><span data-stu-id="efa2b-215">Learning patterns that indicate that a network intrusion has occurred.</span></span>
* <span data-ttu-id="efa2b-216">Localizar clusters anormais de pacientes.</span><span class="sxs-lookup"><span data-stu-id="efa2b-216">Finding abnormal clusters of patients.</span></span>
* <span data-ttu-id="efa2b-217">Verificar valores inseridos em um sistema.</span><span class="sxs-lookup"><span data-stu-id="efa2b-217">Checking values entered into a system.</span></span>

<span data-ttu-id="efa2b-218">Como as anomalias são eventos raros por definição, pode ser difícil coletar um exemplo representativo dos dados para usar na modelagem.</span><span class="sxs-lookup"><span data-stu-id="efa2b-218">Because anomalies are rare events by definition, it can be difficult to collect a representative sample of data to use for modeling.</span></span> <span data-ttu-id="efa2b-219">Os algoritmos incluídos nesta categoria foram especialmente projetados para abordar os principais desafios de criar e treinar modelos usando conjuntos de dados desequilibrados.</span><span class="sxs-lookup"><span data-stu-id="efa2b-219">The algorithms included in this category have been especially designed to address the core challenges of building and training models by using imbalanced data sets.</span></span>

### <a name="anomaly-detection-trainer"></a><span data-ttu-id="efa2b-220">Treinador de detecção de anomalias</span><span class="sxs-lookup"><span data-stu-id="efa2b-220">Anomaly detection trainer</span></span>

<span data-ttu-id="efa2b-221">Você pode treinar um modelo de detecção de anomalias usando os seguintes algoritmos:</span><span class="sxs-lookup"><span data-stu-id="efa2b-221">You can train an anomaly detection model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

### <a name="anomaly-detection-inputs-and-outputs"></a><span data-ttu-id="efa2b-222">Saídas e entradas de detecção de anomalias</span><span class="sxs-lookup"><span data-stu-id="efa2b-222">Anomaly detection inputs and outputs</span></span>

<span data-ttu-id="efa2b-223">Os recursos de entrada devem ser um vetor de tamanho fixo de <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="efa2b-223">The input features must be a fixed-sized vector of <xref:System.Single>.</span></span>

<span data-ttu-id="efa2b-224">Este treinador produz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="efa2b-224">This trainer outputs the following:</span></span>

| <span data-ttu-id="efa2b-225">Nome de Saída</span><span class="sxs-lookup"><span data-stu-id="efa2b-225">Output Name</span></span> | <span data-ttu-id="efa2b-226">{1&gt;Tipo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="efa2b-226">Type</span></span> | <span data-ttu-id="efa2b-227">Descrição</span><span class="sxs-lookup"><span data-stu-id="efa2b-227">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="efa2b-228">A pontuação não negativa não associada calculada pelo modelo de detecção de anomalias</span><span class="sxs-lookup"><span data-stu-id="efa2b-228">The non-negative, unbounded score that was calculated by the anomaly detection model</span></span> |
| `PredictedLabel` | <xref:System.Boolean> | <span data-ttu-id="efa2b-229">Um valor true/false que representa se a entrada é uma anomalia (PredictedLabel = true) ou não (PredictedLabel = false)</span><span class="sxs-lookup"><span data-stu-id="efa2b-229">A true/false value representing whether the input is an anomaly (PredictedLabel=true) or not (PredictedLabel=false)</span></span> |

## <a name="ranking"></a><span data-ttu-id="efa2b-230">Classificação</span><span class="sxs-lookup"><span data-stu-id="efa2b-230">Ranking</span></span>

<span data-ttu-id="efa2b-231">Uma tarefa de classificação cria um classificador a partir de um conjunto de exemplos rotulados.</span><span class="sxs-lookup"><span data-stu-id="efa2b-231">A ranking task constructs a ranker from a set of labeled examples.</span></span> <span data-ttu-id="efa2b-232">Este conjunto de exemplo consiste em grupos de instâncias que podem ser marcados com um determinado critério.</span><span class="sxs-lookup"><span data-stu-id="efa2b-232">This example set consists of instance groups that can be scored with a given criteria.</span></span> <span data-ttu-id="efa2b-233">Os rótulos de classificação são { 0, 1, 2, 3, 4 } para cada instância.</span><span class="sxs-lookup"><span data-stu-id="efa2b-233">The ranking labels are { 0, 1, 2, 3, 4 } for each instance.</span></span>  <span data-ttu-id="efa2b-234">O classificador é treinado para classificar novos grupos de instâncias com pontuações desconhecidas para cada instância.</span><span class="sxs-lookup"><span data-stu-id="efa2b-234">The ranker is trained to rank new instance groups with unknown scores for each instance.</span></span> <span data-ttu-id="efa2b-235">Os aprendizes de classificação do ML.NET são baseados na [classificação de máquinas aprendidas](https://en.wikipedia.org/wiki/Learning_to_rank).</span><span class="sxs-lookup"><span data-stu-id="efa2b-235">ML.NET ranking learners are [machine learned ranking](https://en.wikipedia.org/wiki/Learning_to_rank) based.</span></span>

### <a name="ranking-training-algorithms"></a><span data-ttu-id="efa2b-236">Algoritmos de treinamento de classificação</span><span class="sxs-lookup"><span data-stu-id="efa2b-236">Ranking training algorithms</span></span>

<span data-ttu-id="efa2b-237">Você pode treinar um modelo de classificação usando os seguintes algoritmos:</span><span class="sxs-lookup"><span data-stu-id="efa2b-237">You can train a ranking model with the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>

### <a name="ranking-input-and-outputs"></a><span data-ttu-id="efa2b-238">Entrada e saídas de classificação</span><span class="sxs-lookup"><span data-stu-id="efa2b-238">Ranking input and outputs</span></span>

<span data-ttu-id="efa2b-239">O tipo de dados de rótulo de entrada deve ser do tipo [chave](xref:Microsoft.ML.Data.KeyDataViewType) ou <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="efa2b-239">The input label data type must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type or <xref:System.Single>.</span></span> <span data-ttu-id="efa2b-240">O valor do rótulo determina a relevância, em que valores mais altos indicam maior relevância.</span><span class="sxs-lookup"><span data-stu-id="efa2b-240">The value of the label determines relevance, where higher values indicate higher relevance.</span></span> <span data-ttu-id="efa2b-241">Se o rótulo for um tipo [chave](xref:Microsoft.ML.Data.KeyDataViewType), o índice de chave será o valor de relevância, em que o menor índice é o menos relevante.</span><span class="sxs-lookup"><span data-stu-id="efa2b-241">If the label is a [key](xref:Microsoft.ML.Data.KeyDataViewType) type, then the key index is the relevance value, where the smallest index is the least relevant.</span></span> <span data-ttu-id="efa2b-242">Se o rótulo for um <xref:System.Single>, valores maiores indicarão maior relevância.</span><span class="sxs-lookup"><span data-stu-id="efa2b-242">If the label is a <xref:System.Single>, larger values indicate higher relevance.</span></span>

<span data-ttu-id="efa2b-243">Os dados do recurso devem ser um vetor de tamanho fixo de <xref:System.Single> e a coluna de grupo de linha de entrada deve ser do tipo [chave](xref:Microsoft.ML.Data.KeyDataViewType).</span><span class="sxs-lookup"><span data-stu-id="efa2b-243">The feature data must be a fixed size vector of <xref:System.Single> and input row group column must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>

<span data-ttu-id="efa2b-244">Este treinador produz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="efa2b-244">This trainer outputs the following:</span></span>

| <span data-ttu-id="efa2b-245">Nome de Saída</span><span class="sxs-lookup"><span data-stu-id="efa2b-245">Output Name</span></span> | <span data-ttu-id="efa2b-246">{1&gt;Tipo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="efa2b-246">Type</span></span> | <span data-ttu-id="efa2b-247">Descrição</span><span class="sxs-lookup"><span data-stu-id="efa2b-247">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="efa2b-248">A pontuação não associada calculada pelo modelo para determinar a previsão</span><span class="sxs-lookup"><span data-stu-id="efa2b-248">The unbounded score that was calculated by the model to determine the prediction</span></span> |

## <a name="recommendation"></a><span data-ttu-id="efa2b-249">Recomendação</span><span class="sxs-lookup"><span data-stu-id="efa2b-249">Recommendation</span></span>

<span data-ttu-id="efa2b-250">Uma tarefa de recomendação permite produzir uma lista de produtos ou serviços recomendados.</span><span class="sxs-lookup"><span data-stu-id="efa2b-250">A recommendation task enables producing a list of recommended products or services.</span></span> <span data-ttu-id="efa2b-251">O ML.NET usa a [Fatoração matricial (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), um algoritmo de [filtragem colaborativa](https://en.wikipedia.org/wiki/Collaborative_filtering) para as recomendações quando você tem dados históricos de classificação do produto em seu catálogo.</span><span class="sxs-lookup"><span data-stu-id="efa2b-251">ML.NET uses [Matrix factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), a [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) algorithm for recommendations when you have historical product rating data in your catalog.</span></span> <span data-ttu-id="efa2b-252">Por exemplo, você tem dados históricos de classificação de filmes para seus usuários e deseja recomendar outros filmes que eles provavelmente assistirão posteriormente.</span><span class="sxs-lookup"><span data-stu-id="efa2b-252">For example, you have historical movie rating data for your users and want to recommend  other movies they are likely to watch next.</span></span>

### <a name="recommendation-training-algorithms"></a><span data-ttu-id="efa2b-253">Algoritmos de treinamento de recomendação</span><span class="sxs-lookup"><span data-stu-id="efa2b-253">Recommendation training algorithms</span></span>

<span data-ttu-id="efa2b-254">Você pode treinar um modelo de recomendação usando os seguintes algoritmos:</span><span class="sxs-lookup"><span data-stu-id="efa2b-254">You can train a recommendation model with the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>
