---
title: O que é o Construtor de Modelo e como ele funciona?
description: Como usar o Construtor de Modelo do ML.NET para treinar automaticamente um modelo de machine learning
author: natke
ms.date: 08/07/2019
ms.custom: overview
ms.openlocfilehash: 77fe56dba3532617ad9fb0c89bfaac7c8e031ce7
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971519"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a><span data-ttu-id="aa7a9-103">O que é o Construtor de Modelo e como ele funciona?</span><span class="sxs-lookup"><span data-stu-id="aa7a9-103">What is Model Builder and how does it work?</span></span>

<span data-ttu-id="aa7a9-104">O Construtor de Modelo do ML.NET é uma extensão gráfica do Visual Studio intuitiva para criar, treinar e implantar modelos de aprendizado de máquina personalizados.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-104">ML.NET Model Builder is an intuitive graphical Visual Studio extension to build, train, and deploy custom machine learning models.</span></span>

<span data-ttu-id="aa7a9-105">O Construtor de Modelo usa o aprendizado de máquina automatizado (AutoML) para explorar os algoritmos diferentes de aprendizado de máquina e as configurações para ajudar você a encontrar o que melhor atende ao seu cenário.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-105">Model Builder uses automated machine learning (AutoML) to explore different machine learning algorithms and settings to help you find the one that best suits your scenario.</span></span>

<span data-ttu-id="aa7a9-106">Não é necessário ter experiência de aprendizado de máquina para usar o Construtor de Modelo.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-106">You don't need machine learning expertise to use Model Builder.</span></span> <span data-ttu-id="aa7a9-107">Você só precisa de um problema para resolver e alguns dados.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-107">All you need is some data, and a problem to solve.</span></span> <span data-ttu-id="aa7a9-108">O Construtor de Modelo gera o código para adicionar o modelo em seu aplicativo .NET.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-108">Model Builder generates the code to add the model to your .NET application.</span></span>

![Animação de interface do usuário da extensão do Visual Studio do Construtor de Modelo](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> <span data-ttu-id="aa7a9-110">O Construtor de Modelo está atualmente na Versão Prévia.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-110">Model Builder is currently in Preview.</span></span>

## <a name="scenarios"></a><span data-ttu-id="aa7a9-111">Cenários</span><span class="sxs-lookup"><span data-stu-id="aa7a9-111">Scenarios</span></span>

<span data-ttu-id="aa7a9-112">Você pode trazer vários cenários diferentes para o Construtor de Modelo para gerar um modelo de machine learning para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-112">You can bring many different scenarios to Model Builder, to generate a machine learning model for your application.</span></span>

<span data-ttu-id="aa7a9-113">Um cenário é uma descrição do tipo de previsão que você deseja fazer usando seus dados.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-113">A scenario is a description of the type of prediction you want to make using your data.</span></span> <span data-ttu-id="aa7a9-114">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="aa7a9-114">For example:</span></span>

- <span data-ttu-id="aa7a9-115">prever o volume de vendas futuras do produto com base em dados históricos de vendas</span><span class="sxs-lookup"><span data-stu-id="aa7a9-115">predict future product sales volume based on historical sales data</span></span>
- <span data-ttu-id="aa7a9-116">classificar sentimentos como positivos ou negativos com base em revisões de cliente</span><span class="sxs-lookup"><span data-stu-id="aa7a9-116">classify sentiments as positive or negative based on customer reviews</span></span>
- <span data-ttu-id="aa7a9-117">detectar se uma transação bancária é fraudulenta</span><span class="sxs-lookup"><span data-stu-id="aa7a9-117">detect whether a banking transaction is fraudulent</span></span>
- <span data-ttu-id="aa7a9-118">encaminhar problemas de comentários de clientes para a equipe correta em sua empresa</span><span class="sxs-lookup"><span data-stu-id="aa7a9-118">route customer feedback issues to the correct team in your company</span></span>

## <a name="choose-a-model-type"></a><span data-ttu-id="aa7a9-119">Escolha um tipo de modelo</span><span class="sxs-lookup"><span data-stu-id="aa7a9-119">Choose a model type</span></span>

<span data-ttu-id="aa7a9-120">No Construtor de Modelos, é necessário selecionar um tipo de modelo de machine learning.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-120">In Model Builder, you need to select a machine learning model type.</span></span> <span data-ttu-id="aa7a9-121">O tipo de modelo depende de qual tipo de previsão você está tentando fazer.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-121">The type of model depends on what sort of prediction you are trying to make.</span></span>

<span data-ttu-id="aa7a9-122">Para cenários que preveem um número, o tipo de modelo de machine learning é chamado `regression`.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-122">For scenarios that predict a number, the machine learning model type is called `regression`.</span></span>

<span data-ttu-id="aa7a9-123">Para cenários que preveem uma categoria, o tipo de modelo é `classification`.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-123">For scenarios that predict a category, the model type is `classification`.</span></span> <span data-ttu-id="aa7a9-124">Há dois tipos de classificação:</span><span class="sxs-lookup"><span data-stu-id="aa7a9-124">There are two types of classification:</span></span>

- <span data-ttu-id="aa7a9-125">em que há apenas duas categorias: `binary classification`.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-125">where there are only 2 categories: `binary classification`.</span></span>
- <span data-ttu-id="aa7a9-126">em que há apenas três ou mais categorias: `multiclass classification`.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-126">where there are three or more categories: `multiclass classification`.</span></span>

### <a name="which-model-type-is-right-for-me"></a><span data-ttu-id="aa7a9-127">Qual tipo de modelo é certo para mim?</span><span class="sxs-lookup"><span data-stu-id="aa7a9-127">Which model type is right for me?</span></span>

#### <a name="predict-a-category-when-there-are-only-two-categories"></a><span data-ttu-id="aa7a9-128">Prever uma categoria (quando há apenas duas categorias)</span><span class="sxs-lookup"><span data-stu-id="aa7a9-128">Predict a category (when there are only two categories)</span></span>

<span data-ttu-id="aa7a9-129">A classificação binária é usada para classificar dados em duas categorias (sim/não; aprovados/reprovados, verdadeiros/falsos; positivos/negativos).</span><span class="sxs-lookup"><span data-stu-id="aa7a9-129">Binary classification is used to categorize data into two categories (yes/no; pass/fail; true/false; positive/negative).</span></span>

![Diagrama mostrando exemplos de classificação binária incluindo detecção de fraude, mitigação de risco e triagem de aplicativo](media/binary-classification-examples.png)

<span data-ttu-id="aa7a9-131">A análise de sentimento pode ser usada para prever o sentimento positivo ou negativo de comentários do cliente.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-131">Sentiment analysis can be used to predict positive or negative sentiment of customer feedback.</span></span> <span data-ttu-id="aa7a9-132">É um exemplo de tipo de modelo de classificação binária.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-132">It is an example of a binary classification model type.</span></span>

<span data-ttu-id="aa7a9-133">Se seu cenário exigir a classificação em duas categorias, você poderá usar esse modelo com seu próprio conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-133">If your scenario requires classification into two categories, you can use this template with your own dataset.</span></span>

#### <a name="predict-a-category-when-there-are-three-or-more-categories"></a><span data-ttu-id="aa7a9-134">Prever uma categoria (quando há três ou mais categorias)</span><span class="sxs-lookup"><span data-stu-id="aa7a9-134">Predict a category (when there are three or more categories)</span></span>

<span data-ttu-id="aa7a9-135">A classificação multiclasse pode ser usada para categorizar os dados em três ou mais classes.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-135">Multiclass classification can be used to categorize data into three or more classes.</span></span>

![Os exemplos de classificação multiclasse que incluem a classificação de documentos e de produtos, roteamento de tíquete de suporte e priorização de problemas do cliente](media/multiclass-classification-examples.png)

<span data-ttu-id="aa7a9-137">A classificação de problema pode ser usada para categorizar os problemas de comentários (por exemplo, sobre o GitHub) do cliente usando o título do problema e a descrição.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-137">Issue classification can be used to categorize customer feedback (for example, on GitHub) issues using the issue title and description.</span></span> <span data-ttu-id="aa7a9-138">É um exemplo do tipo de modelo de classificação multiclasse.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-138">It is an example of the multi-class classification model type.</span></span>

<span data-ttu-id="aa7a9-139">Você poderá usar o modelo de classificação do problema para seu cenário se quiser categorizar os dados em três ou mais categorias.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-139">You can use the issue classification template for your scenario if you want to categorize data into three or more categories.</span></span>

#### <a name="predict-a-number"></a><span data-ttu-id="aa7a9-140">Prever um número</span><span class="sxs-lookup"><span data-stu-id="aa7a9-140">Predict a number</span></span>

<span data-ttu-id="aa7a9-141">A regressão é usada para prever números.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-141">Regression is used to predict numbers.</span></span>

![Diagrama mostrando exemplos de regressão, como a previsão de preços, a previsão de vendas e a manutenção preditiva](media/regression-examples.png)

<span data-ttu-id="aa7a9-143">A previsão de preço pode ser usada para prever preços de casas usando local, tamanho e outras características da casa.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-143">Price prediction can be used to predict house prices using location, size, and other characteristics of the house.</span></span> <span data-ttu-id="aa7a9-144">É um exemplo de um tipo de modelo de regressão.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-144">It is an example of a regression model type.</span></span>

<span data-ttu-id="aa7a9-145">Você poderá usar o modelo de previsão de preço para o seu cenário se quiser prever um valor numérico com seu próprio conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-145">You can use the price prediction template for your scenario if you want to predict a numerical value with your own dataset.</span></span>

#### <a name="custom-scenario-choose-your-model-type"></a><span data-ttu-id="aa7a9-146">Cenário personalizado (escolha seu tipo de modelo)</span><span class="sxs-lookup"><span data-stu-id="aa7a9-146">Custom scenario (choose your model type)</span></span>

<span data-ttu-id="aa7a9-147">O cenário personalizado permite que você escolha manualmente seu tipo de modelo.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-147">The custom scenario allows you to manually choose your model type.</span></span>

## <a name="data"></a><span data-ttu-id="aa7a9-148">Dados</span><span class="sxs-lookup"><span data-stu-id="aa7a9-148">Data</span></span>

<span data-ttu-id="aa7a9-149">Depois de escolher seu tipo de modelo, o Construtor de Modelos solicita que você forneça um conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-149">Once you have chosen your model type, Model Builder asks you to provide a dataset.</span></span> <span data-ttu-id="aa7a9-150">Os dados são usados para treinar, avaliar e escolher o melhor modelo para seu cenário.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-150">The data is used to train, evaluate, and choose the best model for your scenario.</span></span>

![Diagrama mostrando as etapas do Construtor de Modelos](media/model-builder-steps.png)

### <a name="choose-the-output-to-predict-label"></a><span data-ttu-id="aa7a9-152">Escolha a saída para prever (rótulo)</span><span class="sxs-lookup"><span data-stu-id="aa7a9-152">Choose the output to predict (label)</span></span>

<span data-ttu-id="aa7a9-153">Um conjunto de dados é uma tabela de linhas de exemplos de treinamento e colunas de atributos.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-153">A dataset is a table of rows of training examples, and columns of attributes.</span></span> <span data-ttu-id="aa7a9-154">Cada linha tem:</span><span class="sxs-lookup"><span data-stu-id="aa7a9-154">Each row has:</span></span>

- <span data-ttu-id="aa7a9-155">um **rótulo** (o atributo que você deseja prever)</span><span class="sxs-lookup"><span data-stu-id="aa7a9-155">a **label** (the attribute that you want to predict)</span></span>
- <span data-ttu-id="aa7a9-156">**recursos** (atributos que são usados como entradas para prever o rótulo).</span><span class="sxs-lookup"><span data-stu-id="aa7a9-156">**features** (attributes that are used as inputs to predict the label).</span></span>

<span data-ttu-id="aa7a9-157">Para o cenário de previsão do preço das casas, os recursos podem ser:</span><span class="sxs-lookup"><span data-stu-id="aa7a9-157">For the house-price prediction scenario, the features could be:</span></span>

- <span data-ttu-id="aa7a9-158">os metros quadrados da casa</span><span class="sxs-lookup"><span data-stu-id="aa7a9-158">the square footage of the house</span></span>
- <span data-ttu-id="aa7a9-159">o número de quartos e banheiros</span><span class="sxs-lookup"><span data-stu-id="aa7a9-159">the number of bedrooms and bathrooms</span></span>
- <span data-ttu-id="aa7a9-160">o código postal</span><span class="sxs-lookup"><span data-stu-id="aa7a9-160">the zip code</span></span>

<span data-ttu-id="aa7a9-161">O rótulo é o preço histórico de casas para essa linha de valores de metro quadrado, quarto e banheiro e código postal.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-161">The label is the historical house price for that row of square footage, bedroom, and bathroom values and zip code.</span></span>

![Tabela mostrando linhas e colunas de dados de preços de casas com recursos que consistem em quartos de tamanho de código postal e etiqueta de preço](media/model-builder-data.png)

### <a name="example-datasets"></a><span data-ttu-id="aa7a9-163">Conjuntos de dados de amostra</span><span class="sxs-lookup"><span data-stu-id="aa7a9-163">Example datasets</span></span>

<span data-ttu-id="aa7a9-164">Se você ainda não tiver seus próprios dados, experimente um desses conjuntos de dados:</span><span class="sxs-lookup"><span data-stu-id="aa7a9-164">If you don't have your own data yet, try out one of these datasets:</span></span>

|<span data-ttu-id="aa7a9-165">Cenário</span><span class="sxs-lookup"><span data-stu-id="aa7a9-165">Scenario</span></span>|<span data-ttu-id="aa7a9-166">Tipo de modelo</span><span class="sxs-lookup"><span data-stu-id="aa7a9-166">Model Type</span></span>|<span data-ttu-id="aa7a9-167">Dados</span><span class="sxs-lookup"><span data-stu-id="aa7a9-167">Data</span></span>|<span data-ttu-id="aa7a9-168">Rotular</span><span class="sxs-lookup"><span data-stu-id="aa7a9-168">Label</span></span>|<span data-ttu-id="aa7a9-169">Recursos</span><span class="sxs-lookup"><span data-stu-id="aa7a9-169">Features</span></span>|
|-|-|-|-|-|
|<span data-ttu-id="aa7a9-170">Previsão de preço</span><span class="sxs-lookup"><span data-stu-id="aa7a9-170">Price prediction</span></span>|<span data-ttu-id="aa7a9-171">regressão</span><span class="sxs-lookup"><span data-stu-id="aa7a9-171">regression</span></span>|[<span data-ttu-id="aa7a9-172">dados de tarifas de táxi</span><span class="sxs-lookup"><span data-stu-id="aa7a9-172">taxi fare data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|<span data-ttu-id="aa7a9-173">Tarifa</span><span class="sxs-lookup"><span data-stu-id="aa7a9-173">Fare</span></span>|<span data-ttu-id="aa7a9-174">Tempo da corrida, distância</span><span class="sxs-lookup"><span data-stu-id="aa7a9-174">Trip time, distance</span></span>|
|<span data-ttu-id="aa7a9-175">Detecção de anomalias</span><span class="sxs-lookup"><span data-stu-id="aa7a9-175">Anomaly detection</span></span>|<span data-ttu-id="aa7a9-176">classificação binária</span><span class="sxs-lookup"><span data-stu-id="aa7a9-176">binary classification</span></span>|[<span data-ttu-id="aa7a9-177">dados de vendas do produto</span><span class="sxs-lookup"><span data-stu-id="aa7a9-177">product sales data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|<span data-ttu-id="aa7a9-178">Vendas do Produto</span><span class="sxs-lookup"><span data-stu-id="aa7a9-178">Product Sales</span></span>|<span data-ttu-id="aa7a9-179">Mês</span><span class="sxs-lookup"><span data-stu-id="aa7a9-179">Month</span></span>|
|<span data-ttu-id="aa7a9-180">Análise de sentimentos</span><span class="sxs-lookup"><span data-stu-id="aa7a9-180">Sentiment analysis</span></span>|<span data-ttu-id="aa7a9-181">classificação binária</span><span class="sxs-lookup"><span data-stu-id="aa7a9-181">binary classification</span></span>|[<span data-ttu-id="aa7a9-182">dados de comentário do site</span><span class="sxs-lookup"><span data-stu-id="aa7a9-182">website comment data</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|<span data-ttu-id="aa7a9-183">Rótulo (0 quando o sentimento é negativo, 1 quando é positivo)</span><span class="sxs-lookup"><span data-stu-id="aa7a9-183">Label (0 when negative sentiment, 1 when positive)</span></span>|<span data-ttu-id="aa7a9-184">Comentário, ano</span><span class="sxs-lookup"><span data-stu-id="aa7a9-184">Comment, Year</span></span>|
|<span data-ttu-id="aa7a9-185">Detecção de fraudes</span><span class="sxs-lookup"><span data-stu-id="aa7a9-185">Fraud detection</span></span>|<span data-ttu-id="aa7a9-186">classificação binária</span><span class="sxs-lookup"><span data-stu-id="aa7a9-186">binary classification</span></span>|[<span data-ttu-id="aa7a9-187">dados do cartão de crédito</span><span class="sxs-lookup"><span data-stu-id="aa7a9-187">credit card data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|<span data-ttu-id="aa7a9-188">Classe (1 quando fraudulenta, caso contrário, 0)</span><span class="sxs-lookup"><span data-stu-id="aa7a9-188">Class (1 when fraudulent, 0 otherwise)</span></span>|<span data-ttu-id="aa7a9-189">Quantidade, V1-V28 (recursos anônimos)</span><span class="sxs-lookup"><span data-stu-id="aa7a9-189">Amount, V1-V28 (anonymized features)</span></span>|
|<span data-ttu-id="aa7a9-190">Classificação de texto</span><span class="sxs-lookup"><span data-stu-id="aa7a9-190">Text classification</span></span>|<span data-ttu-id="aa7a9-191">classificação multiclasse</span><span class="sxs-lookup"><span data-stu-id="aa7a9-191">multiclass classification</span></span>|[<span data-ttu-id="aa7a9-192">dados de problema do GitHub</span><span class="sxs-lookup"><span data-stu-id="aa7a9-192">GitHub issue data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|<span data-ttu-id="aa7a9-193">Área</span><span class="sxs-lookup"><span data-stu-id="aa7a9-193">Area</span></span>|<span data-ttu-id="aa7a9-194">Título, Descrição</span><span class="sxs-lookup"><span data-stu-id="aa7a9-194">Title, Description</span></span>|

## <a name="train"></a><span data-ttu-id="aa7a9-195">Trem</span><span class="sxs-lookup"><span data-stu-id="aa7a9-195">Train</span></span>

<span data-ttu-id="aa7a9-196">Depois de selecionar seu cenário, dados e rótulo, o Construtor de Modelo treina o modelo.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-196">Once you select your scenario, data, and label, Model Builder trains the model.</span></span>

### <a name="what-is-training"></a><span data-ttu-id="aa7a9-197">O que é o treinamento?</span><span class="sxs-lookup"><span data-stu-id="aa7a9-197">What is training?</span></span>

<span data-ttu-id="aa7a9-198">O treinamento é um processo automático pelo qual Construtor de Modelo ensina seu modelo a responder perguntas para seu cenário.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-198">Training is an automatic process by which Model Builder teaches your model how to answer questions for your scenario.</span></span> <span data-ttu-id="aa7a9-199">Depois de treinado, seu modelo pode fazer previsões com dados de entrada não vistos antes.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-199">Once trained, your model can make predictions with input data that it has not seen before.</span></span> <span data-ttu-id="aa7a9-200">Por exemplo, se estiver prevendo preços de casas e uma nova casa for oferecida no mercado, você poderá prever o preço de venda.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-200">For example, if you are predicting house prices and a new house comes on the market, you can predict its sale price.</span></span>

<span data-ttu-id="aa7a9-201">Como o Construtor de Modelo usa aprendizado de máquina automatizado (AutoML), ele não requer nenhuma entrada ou ajuste de você durante o treinamento.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-201">Because Model Builder uses automated machine learning (AutoML), it does not require any input or tuning from you during training.</span></span>

## <a name="evaluate"></a><span data-ttu-id="aa7a9-202">Avaliar o</span><span class="sxs-lookup"><span data-stu-id="aa7a9-202">Evaluate</span></span>

<span data-ttu-id="aa7a9-203">A avaliação é o processo de usar o modelo treinado para fazer previsões com novos dados de teste e, em seguida, medir quão boas são as previsões.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-203">Evaluation is the process of using the trained model to make predictions with new test data, and then measuring how good the predictions are.</span></span>

<span data-ttu-id="aa7a9-204">O Construtor de Modelo divide os dados de treinamento em um conjunto de treinamento e um conjunto de teste.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-204">Model Builder splits the training data into a training set and a test set.</span></span> <span data-ttu-id="aa7a9-205">Os dados de treinamento (80%) são usados para treinar seu modelo e os dados de teste (20%) são retidos para avaliar seu modelo.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-205">The training data (80%) is used to train your model and the test data (20%) is held back to evaluate your model.</span></span> <span data-ttu-id="aa7a9-206">O Construtor de Modelos usa métricas para medir a qualidade do modelo.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-206">Model Builder uses metrics to measure how good the model is.</span></span> <span data-ttu-id="aa7a9-207">As métricas específicas usadas dependem do tipo de modelo.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-207">The specific metrics used are dependent on the type of model.</span></span> <span data-ttu-id="aa7a9-208">Para obter mais informações, consulte [métricas de avaliação de modelo](resources/metrics.md).</span><span class="sxs-lookup"><span data-stu-id="aa7a9-208">For more information, see [model evaluation metrics](resources/metrics.md).</span></span>

## <a name="improve"></a><span data-ttu-id="aa7a9-209">Aprimorar</span><span class="sxs-lookup"><span data-stu-id="aa7a9-209">Improve</span></span>

<span data-ttu-id="aa7a9-210">Se a sua pontuação de desempenho do modelo não for tão boa quanto deseja, você poderá:</span><span class="sxs-lookup"><span data-stu-id="aa7a9-210">If your model performance score is not as good as you want it to be, you can:</span></span>

- <span data-ttu-id="aa7a9-211">Treinar por um período maior de tempo.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-211">Train for a longer period of time.</span></span> <span data-ttu-id="aa7a9-212">Com mais tempo, usar o mecanismo de aprendizado de máquina automatizado para experimentar mais algoritmos e configurações.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-212">With more time, the automated machine learning engine to try more algorithms and settings.</span></span>

- <span data-ttu-id="aa7a9-213">Adicionar mais dados.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-213">Add more data.</span></span> <span data-ttu-id="aa7a9-214">Às vezes, a quantidade de dados não é suficiente para treinar um modelo de machine learning de alta qualidade.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-214">Sometimes the amount of data is not sufficient to train a high-quality machine learning model.</span></span>

- <span data-ttu-id="aa7a9-215">Balancear seus dados.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-215">Balance your data.</span></span> <span data-ttu-id="aa7a9-216">Para tarefas de classificação, certifique-se de que o conjunto de treinamento esteja equilibrado nas categorias.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-216">For classification tasks, make sure that the training set is balanced across the categories.</span></span> <span data-ttu-id="aa7a9-217">Por exemplo, se você tiver quatro classes para 100 exemplos de treinamento e as duas primeiras classes (tag1 e tag2) forem usadas para 90 registros, mas as outras duas (tag3 e tag4) forem usadas apenas nos 10 registros restantes, a falta de dados balanceados poderá fazer com que seu modelo tenha dificuldades para prever corretamente o tag3 ou o tag4.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-217">For example, if you have four classes for 100 training examples, and the two first classes (tag1 and tag2) are used for 90 records, but the other two (tag3 and tag4) are only used on the remaining 10 records, the lack of balanced data may cause your model to struggle to correctly predict tag3 or tag4.</span></span>

## <a name="code"></a><span data-ttu-id="aa7a9-218">Código</span><span class="sxs-lookup"><span data-stu-id="aa7a9-218">Code</span></span>

<span data-ttu-id="aa7a9-219">Após a fase de avaliação, o Construtor de Modelo gera um arquivo de modelo e o código que você pode usar para adicionar o modelo ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-219">After the evaluation phase, Model Builder outputs a model file, and code that you can use to add the model to your application.</span></span> <span data-ttu-id="aa7a9-220">Modelos do ML.NET são salvos como um arquivo zip.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-220">ML.NET models are saved as a zip file.</span></span> <span data-ttu-id="aa7a9-221">O código para carregar e usar o modelo é adicionado como um novo projeto em sua solução.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-221">The code to load and use your model is added as a new project in your solution.</span></span> <span data-ttu-id="aa7a9-222">O Construtor de Modelo também adiciona um aplicativo de console de exemplo que você pode executar para ver seu modelo em ação.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-222">Model Builder also adds a sample console app that you can run to see your model in action.</span></span>

<span data-ttu-id="aa7a9-223">Além disso, o Construtor de Modelo cria o código que gerou o modelo para que você possa entender as etapas usadas na geração do modelo.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-223">In addition, Model Builder outputs the code that generated the model, so that you can understand the steps used to generate the model.</span></span> <span data-ttu-id="aa7a9-224">Você também pode usar o código de treinamento do modelo para treinar novamente seu modelo com novos dados.</span><span class="sxs-lookup"><span data-stu-id="aa7a9-224">You can also use the model training code to retrain your model with new data.</span></span>

## <a name="whats-next"></a><span data-ttu-id="aa7a9-225">O que vem a seguir?</span><span class="sxs-lookup"><span data-stu-id="aa7a9-225">What's next?</span></span>

<span data-ttu-id="aa7a9-226">[Instalar](how-to-guides/install-model-builder.md) a extensão do Visual Studio do Construtor de Modelos</span><span class="sxs-lookup"><span data-stu-id="aa7a9-226">[Install](how-to-guides/install-model-builder.md) the Model Builder Visual Studio extension</span></span>

<span data-ttu-id="aa7a9-227">Experimente a [previsão de preço ou qualquer cenário de regressão](tutorials/predict-prices-with-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="aa7a9-227">Try [price prediction or any regression scenario](tutorials/predict-prices-with-model-builder.md)</span></span>
