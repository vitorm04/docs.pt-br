---
title: O que é o Construtor de Modelo e como ele funciona?
description: Como usar o Construtor de Modelo do ML.NET para treinar automaticamente um modelo de machine learning
ms.date: 01/07/2020
ms.custom: overview, mlnet-tooling
ms.openlocfilehash: cff4601843ec9ca7201ea7dbdbfbcfa18f50e46e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399220"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a><span data-ttu-id="83499-103">O que é o Construtor de Modelo e como ele funciona?</span><span class="sxs-lookup"><span data-stu-id="83499-103">What is Model Builder and how does it work?</span></span>

<span data-ttu-id="83499-104">O Construtor de Modelo do ML.NET é uma extensão gráfica do Visual Studio intuitiva para criar, treinar e implantar modelos de aprendizado de máquina personalizados.</span><span class="sxs-lookup"><span data-stu-id="83499-104">ML.NET Model Builder is an intuitive graphical Visual Studio extension to build, train, and deploy custom machine learning models.</span></span>

<span data-ttu-id="83499-105">O Construtor de Modelo usa o aprendizado de máquina automatizado (AutoML) para explorar os algoritmos diferentes de aprendizado de máquina e as configurações para ajudar você a encontrar o que melhor atende ao seu cenário.</span><span class="sxs-lookup"><span data-stu-id="83499-105">Model Builder uses automated machine learning (AutoML) to explore different machine learning algorithms and settings to help you find the one that best suits your scenario.</span></span>

<span data-ttu-id="83499-106">Não é necessário ter experiência de aprendizado de máquina para usar o Construtor de Modelo.</span><span class="sxs-lookup"><span data-stu-id="83499-106">You don't need machine learning expertise to use Model Builder.</span></span> <span data-ttu-id="83499-107">Você só precisa de um problema para resolver e alguns dados.</span><span class="sxs-lookup"><span data-stu-id="83499-107">All you need is some data, and a problem to solve.</span></span> <span data-ttu-id="83499-108">O Construtor de Modelo gera o código para adicionar o modelo em seu aplicativo .NET.</span><span class="sxs-lookup"><span data-stu-id="83499-108">Model Builder generates the code to add the model to your .NET application.</span></span>

![Animação de interface do usuário da extensão do Visual Studio do Construtor de Modelo](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> <span data-ttu-id="83499-110">O Construtor de Modelo está atualmente na Versão Prévia.</span><span class="sxs-lookup"><span data-stu-id="83499-110">Model Builder is currently in Preview.</span></span>

## <a name="scenarios"></a><span data-ttu-id="83499-111">Cenários</span><span class="sxs-lookup"><span data-stu-id="83499-111">Scenarios</span></span>

<span data-ttu-id="83499-112">Você pode trazer vários cenários diferentes para o Construtor de Modelo para gerar um modelo de machine learning para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="83499-112">You can bring many different scenarios to Model Builder, to generate a machine learning model for your application.</span></span>

<span data-ttu-id="83499-113">Um cenário é uma descrição do tipo de previsão que você deseja fazer usando seus dados.</span><span class="sxs-lookup"><span data-stu-id="83499-113">A scenario is a description of the type of prediction you want to make using your data.</span></span> <span data-ttu-id="83499-114">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="83499-114">For example:</span></span>

- <span data-ttu-id="83499-115">prever o volume de vendas futuras do produto com base em dados históricos de vendas</span><span class="sxs-lookup"><span data-stu-id="83499-115">predict future product sales volume based on historical sales data</span></span>
- <span data-ttu-id="83499-116">classificar sentimentos como positivos ou negativos com base em revisões de cliente</span><span class="sxs-lookup"><span data-stu-id="83499-116">classify sentiments as positive or negative based on customer reviews</span></span>
- <span data-ttu-id="83499-117">detectar se uma transação bancária é fraudulenta</span><span class="sxs-lookup"><span data-stu-id="83499-117">detect whether a banking transaction is fraudulent</span></span>
- <span data-ttu-id="83499-118">encaminhar problemas de comentários de clientes para a equipe correta em sua empresa</span><span class="sxs-lookup"><span data-stu-id="83499-118">route customer feedback issues to the correct team in your company</span></span>

### <a name="which-machine-learning-scenario-is-right-for-me"></a><span data-ttu-id="83499-119">Qual cenário do aprendizado de máquina é adequado para mim?</span><span class="sxs-lookup"><span data-stu-id="83499-119">Which machine learning scenario is right for me?</span></span>

<span data-ttu-id="83499-120">No Model Builder, você precisa selecionar um cenário.</span><span class="sxs-lookup"><span data-stu-id="83499-120">In Model Builder, you need to select a scenario.</span></span> <span data-ttu-id="83499-121">O tipo de cenário depende do tipo de previsão que você está tentando fazer.</span><span class="sxs-lookup"><span data-stu-id="83499-121">The type of scenario depends on what type of prediction you are trying to make.</span></span>

#### <a name="predict-a-category-when-there-are-only-two-categories"></a><span data-ttu-id="83499-122">Prever uma categoria (quando há apenas duas categorias)</span><span class="sxs-lookup"><span data-stu-id="83499-122">Predict a category (when there are only two categories)</span></span>

<span data-ttu-id="83499-123">A classificação binária é usada para classificar dados em duas categorias (sim/não; aprovados/reprovados, verdadeiros/falsos; positivos/negativos).</span><span class="sxs-lookup"><span data-stu-id="83499-123">Binary classification is used to categorize data into two categories (yes/no; pass/fail; true/false; positive/negative).</span></span>

![Diagrama mostrando exemplos de classificação binária incluindo detecção de fraude, mitigação de risco e triagem de aplicativo](media/binary-classification-examples.png)

<span data-ttu-id="83499-125">A análise de sentimento pode ser usada para prever o sentimento positivo ou negativo de comentários do cliente.</span><span class="sxs-lookup"><span data-stu-id="83499-125">Sentiment analysis can be used to predict positive or negative sentiment of customer feedback.</span></span> <span data-ttu-id="83499-126">É um exemplo da tarefa de aprendizado de máquina de classificação binária.</span><span class="sxs-lookup"><span data-stu-id="83499-126">It is an example of the binary classification machine learning task.</span></span>

<span data-ttu-id="83499-127">Se seu cenário exigir a classificação em duas categorias, você poderá usar esse modelo com seu próprio conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="83499-127">If your scenario requires classification into two categories, you can use this template with your own dataset.</span></span>

#### <a name="predict-a-category-when-there-are-three-or-more-categories"></a><span data-ttu-id="83499-128">Prever uma categoria (quando há três ou mais categorias)</span><span class="sxs-lookup"><span data-stu-id="83499-128">Predict a category (when there are three or more categories)</span></span>

<span data-ttu-id="83499-129">A classificação multiclasse pode ser usada para categorizar os dados em três ou mais classes.</span><span class="sxs-lookup"><span data-stu-id="83499-129">Multiclass classification can be used to categorize data into three or more classes.</span></span>

![Os exemplos de classificação multiclasse que incluem a classificação de documentos e de produtos, roteamento de tíquete de suporte e priorização de problemas do cliente](media/multiclass-classification-examples.png)

<span data-ttu-id="83499-131">A classificação de problema pode ser usada para categorizar os problemas de comentários (por exemplo, sobre o GitHub) do cliente usando o título do problema e a descrição.</span><span class="sxs-lookup"><span data-stu-id="83499-131">Issue classification can be used to categorize customer feedback (for example, on GitHub) issues using the issue title and description.</span></span> <span data-ttu-id="83499-132">É um exemplo da tarefa de aprendizagem de máquina de classificação multiclasse.</span><span class="sxs-lookup"><span data-stu-id="83499-132">It is an example of the multi-class classification machine learning task.</span></span>

<span data-ttu-id="83499-133">Você poderá usar o modelo de classificação do problema para seu cenário se quiser categorizar os dados em três ou mais categorias.</span><span class="sxs-lookup"><span data-stu-id="83499-133">You can use the issue classification template for your scenario if you want to categorize data into three or more categories.</span></span>

#### <a name="predict-a-number"></a><span data-ttu-id="83499-134">Prever um número</span><span class="sxs-lookup"><span data-stu-id="83499-134">Predict a number</span></span>

<span data-ttu-id="83499-135">A regressão é usada para prever números.</span><span class="sxs-lookup"><span data-stu-id="83499-135">Regression is used to predict numbers.</span></span>

![Diagrama mostrando exemplos de regressão, como a previsão de preços, a previsão de vendas e a manutenção preditiva](media/regression-examples.png)

<span data-ttu-id="83499-137">A previsão de preço pode ser usada para prever preços de casas usando local, tamanho e outras características da casa.</span><span class="sxs-lookup"><span data-stu-id="83499-137">Price prediction can be used to predict house prices using location, size, and other characteristics of the house.</span></span> <span data-ttu-id="83499-138">É um exemplo da tarefa de aprendizado de máquina de regressão.</span><span class="sxs-lookup"><span data-stu-id="83499-138">It is an example of the regression machine learning task.</span></span>

<span data-ttu-id="83499-139">Você poderá usar o modelo de previsão de preço para o seu cenário se quiser prever um valor numérico com seu próprio conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="83499-139">You can use the price prediction template for your scenario if you want to predict a numerical value with your own dataset.</span></span>

#### <a name="classify-images-into-categories"></a><span data-ttu-id="83499-140">Classificar imagens em categorias</span><span class="sxs-lookup"><span data-stu-id="83499-140">Classify images into categories</span></span>

<span data-ttu-id="83499-141">Este cenário é um caso especial de classificação multiclasse, onde os dados de entrada a serem categorizados é um conjunto de imagens.</span><span class="sxs-lookup"><span data-stu-id="83499-141">This scenario is a special case of multiclass classification, where the input data to be categorized is a set of images.</span></span>

<span data-ttu-id="83499-142">A classificação de imagens pode ser usada para identificar imagens de diferentes categorias.</span><span class="sxs-lookup"><span data-stu-id="83499-142">Image classification can be used to identify images of different categories.</span></span> <span data-ttu-id="83499-143">Por exemplo, diferentes tipos de terreno ou animais ou defeitos de fabricação.</span><span class="sxs-lookup"><span data-stu-id="83499-143">For example, different types of terrain or animals or manufacturing defects.</span></span>

<span data-ttu-id="83499-144">Você pode usar o modelo de classificação de imagem para o seu cenário se você tiver um conjunto de imagens e quiser classificar as imagens em diferentes categorias.</span><span class="sxs-lookup"><span data-stu-id="83499-144">You can use the image classification template for your scenario if you have a set of images, and you want to classify the images into different categories.</span></span>

#### <a name="custom-scenario"></a><span data-ttu-id="83499-145">Cenário personalizado</span><span class="sxs-lookup"><span data-stu-id="83499-145">Custom scenario</span></span>

<span data-ttu-id="83499-146">O cenário personalizado permite que você escolha manualmente o seu cenário.</span><span class="sxs-lookup"><span data-stu-id="83499-146">The custom scenario allows you to manually choose your scenario.</span></span>

## <a name="data"></a><span data-ttu-id="83499-147">Dados</span><span class="sxs-lookup"><span data-stu-id="83499-147">Data</span></span>

<span data-ttu-id="83499-148">Depois de escolher seu cenário, o Model Builder pede que você forneça um conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="83499-148">Once you have chosen your scenario, Model Builder asks you to provide a dataset.</span></span> <span data-ttu-id="83499-149">Os dados são usados para treinar, avaliar e escolher o melhor modelo para seu cenário.</span><span class="sxs-lookup"><span data-stu-id="83499-149">The data is used to train, evaluate, and choose the best model for your scenario.</span></span>

![Diagrama mostrando as etapas do Construtor de Modelos](media/model-builder-steps.png)

<span data-ttu-id="83499-151">O Model Builder suporta conjuntos de dados nos formatos .tsv, .csv, .txt, bem como no formato de banco de dados SQL.</span><span class="sxs-lookup"><span data-stu-id="83499-151">Model Builder supports datasets in .tsv, .csv, .txt formats, as well as SQL database format.</span></span> <span data-ttu-id="83499-152">Se você tiver um arquivo .txt, as `,` `;` colunas devem ser separadas com , ou `/t` e o arquivo deve ter uma linha de cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="83499-152">If you have a .txt file, columns should be separated with `,`, `;` or `/t` and the file must have a header row.</span></span>

<span data-ttu-id="83499-153">Se o conjunto de dados for composto por `.jpg` imagens, os tipos de arquivos suportados serão e `.png`.</span><span class="sxs-lookup"><span data-stu-id="83499-153">If the dataset is made up of images, the supported file types are `.jpg` and `.png`.</span></span>

<span data-ttu-id="83499-154">Para obter mais informações, consulte [Carregar dados de treinamento no Model Builder](how-to-guides/load-data-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="83499-154">For more information, see [Load training data into Model Builder](how-to-guides/load-data-model-builder.md).</span></span>

### <a name="choose-the-output-to-predict-label"></a><span data-ttu-id="83499-155">Escolha a saída para prever (rótulo)</span><span class="sxs-lookup"><span data-stu-id="83499-155">Choose the output to predict (label)</span></span>

<span data-ttu-id="83499-156">Um conjunto de dados é uma tabela de linhas de exemplos de treinamento e colunas de atributos.</span><span class="sxs-lookup"><span data-stu-id="83499-156">A dataset is a table of rows of training examples, and columns of attributes.</span></span> <span data-ttu-id="83499-157">Cada linha tem:</span><span class="sxs-lookup"><span data-stu-id="83499-157">Each row has:</span></span>

- <span data-ttu-id="83499-158">um **rótulo** (o atributo que você deseja prever)</span><span class="sxs-lookup"><span data-stu-id="83499-158">a **label** (the attribute that you want to predict)</span></span>
- <span data-ttu-id="83499-159">**recursos** (atributos que são usados como entradas para prever o rótulo).</span><span class="sxs-lookup"><span data-stu-id="83499-159">**features** (attributes that are used as inputs to predict the label).</span></span>

<span data-ttu-id="83499-160">Para o cenário de previsão do preço das casas, os recursos podem ser:</span><span class="sxs-lookup"><span data-stu-id="83499-160">For the house-price prediction scenario, the features could be:</span></span>

- <span data-ttu-id="83499-161">os metros quadrados da casa</span><span class="sxs-lookup"><span data-stu-id="83499-161">the square footage of the house</span></span>
- <span data-ttu-id="83499-162">o número de quartos e banheiros</span><span class="sxs-lookup"><span data-stu-id="83499-162">the number of bedrooms and bathrooms</span></span>
- <span data-ttu-id="83499-163">o código postal</span><span class="sxs-lookup"><span data-stu-id="83499-163">the zip code</span></span>

<span data-ttu-id="83499-164">O rótulo é o preço histórico de casas para essa linha de valores de metro quadrado, quarto e banheiro e código postal.</span><span class="sxs-lookup"><span data-stu-id="83499-164">The label is the historical house price for that row of square footage, bedroom, and bathroom values and zip code.</span></span>

![Tabela mostrando linhas e colunas de dados de preços de casas com recursos que consistem em quartos de tamanho de código postal e etiqueta de preço](media/model-builder-data.png)

### <a name="example-datasets"></a><span data-ttu-id="83499-166">Conjuntos de dados de amostra</span><span class="sxs-lookup"><span data-stu-id="83499-166">Example datasets</span></span>

<span data-ttu-id="83499-167">Se você ainda não tiver seus próprios dados, experimente um desses conjuntos de dados:</span><span class="sxs-lookup"><span data-stu-id="83499-167">If you don't have your own data yet, try out one of these datasets:</span></span>

|<span data-ttu-id="83499-168">Cenário</span><span class="sxs-lookup"><span data-stu-id="83499-168">Scenario</span></span>|<span data-ttu-id="83499-169">Tarefa ML</span><span class="sxs-lookup"><span data-stu-id="83499-169">ML task</span></span>|<span data-ttu-id="83499-170">Dados</span><span class="sxs-lookup"><span data-stu-id="83499-170">Data</span></span>|<span data-ttu-id="83499-171">Rótulo</span><span class="sxs-lookup"><span data-stu-id="83499-171">Label</span></span>|<span data-ttu-id="83499-172">Recursos</span><span class="sxs-lookup"><span data-stu-id="83499-172">Features</span></span>|
|-|-|-|-|-|
|<span data-ttu-id="83499-173">Previsão de preço</span><span class="sxs-lookup"><span data-stu-id="83499-173">Price prediction</span></span>|<span data-ttu-id="83499-174">regressão</span><span class="sxs-lookup"><span data-stu-id="83499-174">regression</span></span>|[<span data-ttu-id="83499-175">dados de tarifas de táxi</span><span class="sxs-lookup"><span data-stu-id="83499-175">taxi fare data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|<span data-ttu-id="83499-176">Tarifa</span><span class="sxs-lookup"><span data-stu-id="83499-176">Fare</span></span>|<span data-ttu-id="83499-177">Tempo da corrida, distância</span><span class="sxs-lookup"><span data-stu-id="83499-177">Trip time, distance</span></span>|
|<span data-ttu-id="83499-178">Detecção de anomalias</span><span class="sxs-lookup"><span data-stu-id="83499-178">Anomaly detection</span></span>|<span data-ttu-id="83499-179">classificação binária</span><span class="sxs-lookup"><span data-stu-id="83499-179">binary classification</span></span>|[<span data-ttu-id="83499-180">dados de vendas do produto</span><span class="sxs-lookup"><span data-stu-id="83499-180">product sales data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|<span data-ttu-id="83499-181">Vendas do Produto</span><span class="sxs-lookup"><span data-stu-id="83499-181">Product Sales</span></span>|<span data-ttu-id="83499-182">Month</span><span class="sxs-lookup"><span data-stu-id="83499-182">Month</span></span>|
|<span data-ttu-id="83499-183">Análise de sentimento</span><span class="sxs-lookup"><span data-stu-id="83499-183">Sentiment analysis</span></span>|<span data-ttu-id="83499-184">classificação binária</span><span class="sxs-lookup"><span data-stu-id="83499-184">binary classification</span></span>|[<span data-ttu-id="83499-185">dados de comentário do site</span><span class="sxs-lookup"><span data-stu-id="83499-185">website comment data</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|<span data-ttu-id="83499-186">Rótulo (0 quando o sentimento é negativo, 1 quando é positivo)</span><span class="sxs-lookup"><span data-stu-id="83499-186">Label (0 when negative sentiment, 1 when positive)</span></span>|<span data-ttu-id="83499-187">Comentário, ano</span><span class="sxs-lookup"><span data-stu-id="83499-187">Comment, Year</span></span>|
|<span data-ttu-id="83499-188">Detecção de fraude</span><span class="sxs-lookup"><span data-stu-id="83499-188">Fraud detection</span></span>|<span data-ttu-id="83499-189">classificação binária</span><span class="sxs-lookup"><span data-stu-id="83499-189">binary classification</span></span>|[<span data-ttu-id="83499-190">dados do cartão de crédito</span><span class="sxs-lookup"><span data-stu-id="83499-190">credit card data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|<span data-ttu-id="83499-191">Classe (1 quando fraudulenta, caso contrário, 0)</span><span class="sxs-lookup"><span data-stu-id="83499-191">Class (1 when fraudulent, 0 otherwise)</span></span>|<span data-ttu-id="83499-192">Quantidade, V1-V28 (recursos anônimos)</span><span class="sxs-lookup"><span data-stu-id="83499-192">Amount, V1-V28 (anonymized features)</span></span>|
|<span data-ttu-id="83499-193">Classificação de texto</span><span class="sxs-lookup"><span data-stu-id="83499-193">Text classification</span></span>|<span data-ttu-id="83499-194">classificação multiclasse</span><span class="sxs-lookup"><span data-stu-id="83499-194">multiclass classification</span></span>|[<span data-ttu-id="83499-195">dados de problema do GitHub</span><span class="sxs-lookup"><span data-stu-id="83499-195">GitHub issue data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|<span data-ttu-id="83499-196">Área</span><span class="sxs-lookup"><span data-stu-id="83499-196">Area</span></span>|<span data-ttu-id="83499-197">Título, Descrição</span><span class="sxs-lookup"><span data-stu-id="83499-197">Title, Description</span></span>|
|<span data-ttu-id="83499-198">Classificação de imagens</span><span class="sxs-lookup"><span data-stu-id="83499-198">Image classification</span></span>|<span data-ttu-id="83499-199">classificação multiclasse</span><span class="sxs-lookup"><span data-stu-id="83499-199">multiclass classification</span></span>|[<span data-ttu-id="83499-200">Imagens de flores</span><span class="sxs-lookup"><span data-stu-id="83499-200">Flowers images</span></span>](http://download.tensorflow.org/example_images/flower_photos.tgz)|<span data-ttu-id="83499-201">O tipo de flor: margarida, dente-de-leão, rosas, girassóis, tulipas</span><span class="sxs-lookup"><span data-stu-id="83499-201">The type of flower: daisy, dandelion, roses, sunflowers, tulips</span></span>|<span data-ttu-id="83499-202">Os dados da imagem em si</span><span class="sxs-lookup"><span data-stu-id="83499-202">The image data itself</span></span>|

## <a name="train"></a><span data-ttu-id="83499-203">Treinar</span><span class="sxs-lookup"><span data-stu-id="83499-203">Train</span></span>

<span data-ttu-id="83499-204">Depois de selecionar seu cenário, dados e rótulo, o Construtor de Modelo treina o modelo.</span><span class="sxs-lookup"><span data-stu-id="83499-204">Once you select your scenario, data, and label, Model Builder trains the model.</span></span>

### <a name="what-is-training"></a><span data-ttu-id="83499-205">O que é o treinamento?</span><span class="sxs-lookup"><span data-stu-id="83499-205">What is training?</span></span>

<span data-ttu-id="83499-206">O treinamento é um processo automático pelo qual Construtor de Modelo ensina seu modelo a responder perguntas para seu cenário.</span><span class="sxs-lookup"><span data-stu-id="83499-206">Training is an automatic process by which Model Builder teaches your model how to answer questions for your scenario.</span></span> <span data-ttu-id="83499-207">Depois de treinado, seu modelo pode fazer previsões com dados de entrada não vistos antes.</span><span class="sxs-lookup"><span data-stu-id="83499-207">Once trained, your model can make predictions with input data that it has not seen before.</span></span> <span data-ttu-id="83499-208">Por exemplo, se estiver prevendo preços de casas e uma nova casa for oferecida no mercado, você poderá prever o preço de venda.</span><span class="sxs-lookup"><span data-stu-id="83499-208">For example, if you are predicting house prices and a new house comes on the market, you can predict its sale price.</span></span>

<span data-ttu-id="83499-209">Como o Construtor de Modelo usa aprendizado de máquina automatizado (AutoML), ele não requer nenhuma entrada ou ajuste de você durante o treinamento.</span><span class="sxs-lookup"><span data-stu-id="83499-209">Because Model Builder uses automated machine learning (AutoML), it does not require any input or tuning from you during training.</span></span>

### <a name="how-long-should-i-train-for"></a><span data-ttu-id="83499-210">Por quanto tempo devo treinar?</span><span class="sxs-lookup"><span data-stu-id="83499-210">How long should I train for?</span></span>

<span data-ttu-id="83499-211">O Model Builder usa o AutoML para explorar vários modelos para encontrar o modelo de melhor desempenho.</span><span class="sxs-lookup"><span data-stu-id="83499-211">Model Builder uses AutoML to explore multiple models to find you the best performing model.</span></span>

<span data-ttu-id="83499-212">Períodos de treinamento mais longos permitem que o AutoML explore mais modelos com uma gama mais ampla de configurações.</span><span class="sxs-lookup"><span data-stu-id="83499-212">Longer training periods allow AutoML to explore more models with a wider range of settings.</span></span>

<span data-ttu-id="83499-213">A tabela abaixo resume o tempo médio gasto para obter um bom desempenho para um conjunto de conjuntos de dados exemplos, em uma máquina local.</span><span class="sxs-lookup"><span data-stu-id="83499-213">The table below summarizes the average time taken to get good performance for a suite of example datasets, on a local machine.</span></span>

|<span data-ttu-id="83499-214">Tamanho do conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="83499-214">Dataset size</span></span>|<span data-ttu-id="83499-215">Tempo médio para treinar</span><span class="sxs-lookup"><span data-stu-id="83499-215">Average time to train</span></span>|
|------------|---------------------|
|<span data-ttu-id="83499-216">0 - 10 MB</span><span class="sxs-lookup"><span data-stu-id="83499-216">0 - 10 MB</span></span>|<span data-ttu-id="83499-217">10 s</span><span class="sxs-lookup"><span data-stu-id="83499-217">10 sec</span></span>|
|<span data-ttu-id="83499-218">10 - 100 MB</span><span class="sxs-lookup"><span data-stu-id="83499-218">10 - 100 MB</span></span>|<span data-ttu-id="83499-219">10 min</span><span class="sxs-lookup"><span data-stu-id="83499-219">10 min</span></span>|
|<span data-ttu-id="83499-220">100 - 500 MB</span><span class="sxs-lookup"><span data-stu-id="83499-220">100 - 500 MB</span></span>|<span data-ttu-id="83499-221">30 min</span><span class="sxs-lookup"><span data-stu-id="83499-221">30 min</span></span>|
|<span data-ttu-id="83499-222">500 - 1 GB</span><span class="sxs-lookup"><span data-stu-id="83499-222">500 - 1 GB</span></span>|<span data-ttu-id="83499-223">60 min</span><span class="sxs-lookup"><span data-stu-id="83499-223">60 min</span></span>|
|<span data-ttu-id="83499-224">1 GB+</span><span class="sxs-lookup"><span data-stu-id="83499-224">1 GB+</span></span>|<span data-ttu-id="83499-225">Mais de 3 horas</span><span class="sxs-lookup"><span data-stu-id="83499-225">3+ hours</span></span>|

<span data-ttu-id="83499-226">Esses números são apenas um guia.</span><span class="sxs-lookup"><span data-stu-id="83499-226">These numbers are a guide only.</span></span> <span data-ttu-id="83499-227">O tempo exato de treinamento depende de:</span><span class="sxs-lookup"><span data-stu-id="83499-227">The exact length of training is dependent on:</span></span>

- <span data-ttu-id="83499-228">o número de recursos (colunas) sendo usados como entrada para o modelo</span><span class="sxs-lookup"><span data-stu-id="83499-228">the number of features (columns) being used to as input to the model</span></span>
- <span data-ttu-id="83499-229">o tipo de colunas</span><span class="sxs-lookup"><span data-stu-id="83499-229">the type of columns</span></span>
- <span data-ttu-id="83499-230">a tarefa ML</span><span class="sxs-lookup"><span data-stu-id="83499-230">the ML task</span></span>
- <span data-ttu-id="83499-231">o desempenho da CPU, disco e memória da máquina usada para treinamento</span><span class="sxs-lookup"><span data-stu-id="83499-231">the CPU, disk and memory performance of the machine used for training</span></span>

## <a name="evaluate"></a><span data-ttu-id="83499-232">Avaliar</span><span class="sxs-lookup"><span data-stu-id="83499-232">Evaluate</span></span>

<span data-ttu-id="83499-233">Avaliação é o processo de medir o quão bom é o seu modelo.</span><span class="sxs-lookup"><span data-stu-id="83499-233">Evaluation is the process of measuring how good your model is.</span></span> <span data-ttu-id="83499-234">O Model Builder usa o modelo treinado para fazer previsões com novos dados de teste e, em seguida, mede o quão boas são as previsões.</span><span class="sxs-lookup"><span data-stu-id="83499-234">Model Builder uses the trained model to make predictions with new test data, and then measures how good the predictions are.</span></span>

<span data-ttu-id="83499-235">O Construtor de Modelo divide os dados de treinamento em um conjunto de treinamento e um conjunto de teste.</span><span class="sxs-lookup"><span data-stu-id="83499-235">Model Builder splits the training data into a training set and a test set.</span></span> <span data-ttu-id="83499-236">Os dados de treinamento (80%) são usados para treinar seu modelo e os dados de teste (20%) são retidos para avaliar seu modelo.</span><span class="sxs-lookup"><span data-stu-id="83499-236">The training data (80%) is used to train your model and the test data (20%) is held back to evaluate your model.</span></span>

### <a name="how-do-i-understand-my-model-performance"></a><span data-ttu-id="83499-237">Como entendo meu desempenho como modelo?</span><span class="sxs-lookup"><span data-stu-id="83499-237">How do I understand my model performance?</span></span>

<span data-ttu-id="83499-238">Um cenário mapeia uma tarefa de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="83499-238">A scenario maps to a machine learning task.</span></span> <span data-ttu-id="83499-239">Cada tarefa ml tem seu próprio conjunto de métricas de avaliação.</span><span class="sxs-lookup"><span data-stu-id="83499-239">Each ML task has its own set of evaluation metrics.</span></span>

#### <a name="regression-for-example-price-prediction"></a><span data-ttu-id="83499-240">Regressão (por exemplo, Previsão de Preços)</span><span class="sxs-lookup"><span data-stu-id="83499-240">Regression (for example, Price Prediction)</span></span>

<span data-ttu-id="83499-241">A métrica padrão para problemas de regressão é RSquared, o valor do RSquared varia entre 0 e 1.</span><span class="sxs-lookup"><span data-stu-id="83499-241">The default metric for regression problems is RSquared, the value of RSquared ranges between 0 and 1.</span></span> <span data-ttu-id="83499-242">1 é o melhor valor possível ou, em outras palavras, quanto mais perto o valor de RSquared para 1, melhor o seu modelo está realizando.</span><span class="sxs-lookup"><span data-stu-id="83499-242">1 is the best possible value or in other words the closer the value of RSquared to 1 the better your model is performing.</span></span>

<span data-ttu-id="83499-243">Outras métricas relatadas, como perda absoluta, perda quadrada e perda de RMS são métricas adicionais, que podem ser usadas para entender como seu modelo está se saindo e compará-lo com outros modelos de regressão.</span><span class="sxs-lookup"><span data-stu-id="83499-243">Other metrics reported such as absolute-loss, squared-loss, and RMS loss are additional metrics, which can be used to understand how your model is performing and comparing it against other regression models.</span></span>

#### <a name="binary-classification-for-example-sentiment-analysis"></a><span data-ttu-id="83499-244">Classificação Binária (por exemplo, Análise de Sentimento)</span><span class="sxs-lookup"><span data-stu-id="83499-244">Binary Classification (for example, Sentiment Analysis)</span></span>

<span data-ttu-id="83499-245">A métrica padrão para problemas de classificação é a precisão.</span><span class="sxs-lookup"><span data-stu-id="83499-245">The default metric for classification problems is accuracy.</span></span> <span data-ttu-id="83499-246">A precisão define a proporção de previsões corretas que seu modelo está fazendo ao longo do conjunto de dados do teste.</span><span class="sxs-lookup"><span data-stu-id="83499-246">Accuracy defines the proportion of correct predictions your model is making over the test dataset.</span></span> <span data-ttu-id="83499-247">Quanto mais perto de 100% ou 1.0 melhor.</span><span class="sxs-lookup"><span data-stu-id="83499-247">The closer to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="83499-248">Outras métricas relatadas, como AUC (Área a curva), que mede a taxa positiva verdadeira versus a taxa falsa positiva, devem ser maiores que 0,50 para que os modelos sejam aceitáveis.</span><span class="sxs-lookup"><span data-stu-id="83499-248">Other metrics reported such as AUC (Area under the curve), which measures the true positive rate vs. the false positive rate should be greater than 0.50 for models to be acceptable.</span></span>

<span data-ttu-id="83499-249">Métricas adicionais como a pontuação da F1 podem ser usadas para controlar o equilíbrio entre Precisão e Recall.</span><span class="sxs-lookup"><span data-stu-id="83499-249">Additional metrics like F1 score can be used to control the balance between Precision and Recall.</span></span>

#### <a name="multi-class-classification-for-example-issue-classification-image-classification"></a><span data-ttu-id="83499-250">Classificação multiclasse (por exemplo, Classificação de problemas, classificação de imagem)</span><span class="sxs-lookup"><span data-stu-id="83499-250">Multi-Class Classification (for example, Issue Classification, Image Classification)</span></span>

<span data-ttu-id="83499-251">A métrica padrão para classificação multiclasse é Micro Accuracy.</span><span class="sxs-lookup"><span data-stu-id="83499-251">The default metric for Multi-class classification is Micro Accuracy.</span></span> <span data-ttu-id="83499-252">Quanto mais perto da Micro Precisão 100% ou 1.0, melhor será.</span><span class="sxs-lookup"><span data-stu-id="83499-252">The closer the Micro Accuracy to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="83499-253">Outra métrica importante para a classificação multiclasse é a macro-precisão, semelhante à Micro-precisão quanto mais perto de 1.0 melhor.</span><span class="sxs-lookup"><span data-stu-id="83499-253">Another important metric for Multi-class classification is Macro-accuracy, similar to Micro-accuracy the closer to 1.0 the better it is.</span></span> <span data-ttu-id="83499-254">Uma boa maneira de pensar sobre esses dois tipos de precisão é:</span><span class="sxs-lookup"><span data-stu-id="83499-254">A good way to think about these two types of accuracy is:</span></span>

- <span data-ttu-id="83499-255">Micro-precisão: Com que frequência um bilhete de entrada é classificado para a equipe certa?</span><span class="sxs-lookup"><span data-stu-id="83499-255">Micro-accuracy: How often does an incoming ticket get classified to the right team?</span></span>
- <span data-ttu-id="83499-256">Macro-precisão: Para uma equipe média, quantas vezes um bilhete de entrada é correto para sua equipe?</span><span class="sxs-lookup"><span data-stu-id="83499-256">Macro-accuracy: For an average team, how often is an incoming ticket correct for their team?</span></span>

### <a name="more-information-on-evaluation-metrics"></a><span data-ttu-id="83499-257">Mais informações sobre métricas de avaliação</span><span class="sxs-lookup"><span data-stu-id="83499-257">More information on evaluation metrics</span></span>

<span data-ttu-id="83499-258">Para obter mais informações, consulte [métricas de avaliação de modelo](resources/metrics.md).</span><span class="sxs-lookup"><span data-stu-id="83499-258">For more information, see [model evaluation metrics](resources/metrics.md).</span></span>

## <a name="improve"></a><span data-ttu-id="83499-259">Aprimorar</span><span class="sxs-lookup"><span data-stu-id="83499-259">Improve</span></span>

<span data-ttu-id="83499-260">Se a sua pontuação de desempenho do modelo não for tão boa quanto deseja, você poderá:</span><span class="sxs-lookup"><span data-stu-id="83499-260">If your model performance score is not as good as you want it to be, you can:</span></span>

- <span data-ttu-id="83499-261">Treinar por um período maior de tempo.</span><span class="sxs-lookup"><span data-stu-id="83499-261">Train for a longer period of time.</span></span> <span data-ttu-id="83499-262">Com mais tempo, usar o mecanismo de aprendizado de máquina automatizado para experimentar mais algoritmos e configurações.</span><span class="sxs-lookup"><span data-stu-id="83499-262">With more time, the automated machine learning engine to try more algorithms and settings.</span></span>

- <span data-ttu-id="83499-263">Adicionar mais dados.</span><span class="sxs-lookup"><span data-stu-id="83499-263">Add more data.</span></span> <span data-ttu-id="83499-264">Às vezes, a quantidade de dados não é suficiente para treinar um modelo de machine learning de alta qualidade.</span><span class="sxs-lookup"><span data-stu-id="83499-264">Sometimes the amount of data is not sufficient to train a high-quality machine learning model.</span></span>

- <span data-ttu-id="83499-265">Balancear seus dados.</span><span class="sxs-lookup"><span data-stu-id="83499-265">Balance your data.</span></span> <span data-ttu-id="83499-266">Para tarefas de classificação, certifique-se de que o conjunto de treinamento esteja equilibrado nas categorias.</span><span class="sxs-lookup"><span data-stu-id="83499-266">For classification tasks, make sure that the training set is balanced across the categories.</span></span> <span data-ttu-id="83499-267">Por exemplo, se você tiver quatro classes para 100 exemplos de treinamento e as duas primeiras classes (tag1 e tag2) forem usadas para 90 registros, mas as outras duas (tag3 e tag4) forem usadas apenas nos 10 registros restantes, a falta de dados balanceados poderá fazer com que seu modelo tenha dificuldades para prever corretamente o tag3 ou o tag4.</span><span class="sxs-lookup"><span data-stu-id="83499-267">For example, if you have four classes for 100 training examples, and the two first classes (tag1 and tag2) are used for 90 records, but the other two (tag3 and tag4) are only used on the remaining 10 records, the lack of balanced data may cause your model to struggle to correctly predict tag3 or tag4.</span></span>

## <a name="code"></a><span data-ttu-id="83499-268">Código</span><span class="sxs-lookup"><span data-stu-id="83499-268">Code</span></span>

<span data-ttu-id="83499-269">Após a fase de avaliação, o Construtor de Modelo gera um arquivo de modelo e o código que você pode usar para adicionar o modelo ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="83499-269">After the evaluation phase, Model Builder outputs a model file, and code that you can use to add the model to your application.</span></span> <span data-ttu-id="83499-270">Modelos do ML.NET são salvos como um arquivo zip.</span><span class="sxs-lookup"><span data-stu-id="83499-270">ML.NET models are saved as a zip file.</span></span> <span data-ttu-id="83499-271">O código para carregar e usar o modelo é adicionado como um novo projeto em sua solução.</span><span class="sxs-lookup"><span data-stu-id="83499-271">The code to load and use your model is added as a new project in your solution.</span></span> <span data-ttu-id="83499-272">O Construtor de Modelo também adiciona um aplicativo de console de exemplo que você pode executar para ver seu modelo em ação.</span><span class="sxs-lookup"><span data-stu-id="83499-272">Model Builder also adds a sample console app that you can run to see your model in action.</span></span>

<span data-ttu-id="83499-273">Além disso, o Construtor de Modelo cria o código que gerou o modelo para que você possa entender as etapas usadas na geração do modelo.</span><span class="sxs-lookup"><span data-stu-id="83499-273">In addition, Model Builder outputs the code that generated the model, so that you can understand the steps used to generate the model.</span></span> <span data-ttu-id="83499-274">Você também pode usar o código de treinamento do modelo para treinar novamente seu modelo com novos dados.</span><span class="sxs-lookup"><span data-stu-id="83499-274">You can also use the model training code to retrain your model with new data.</span></span>

## <a name="whats-next"></a><span data-ttu-id="83499-275">O que vem a seguir?</span><span class="sxs-lookup"><span data-stu-id="83499-275">What's next?</span></span>

<span data-ttu-id="83499-276">[Instalar](how-to-guides/install-model-builder.md) a extensão do Visual Studio do Construtor de Modelos</span><span class="sxs-lookup"><span data-stu-id="83499-276">[Install](how-to-guides/install-model-builder.md) the Model Builder Visual Studio extension</span></span>

<span data-ttu-id="83499-277">Experimente a [previsão de preço ou qualquer cenário de regressão](tutorials/predict-prices-with-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="83499-277">Try [price prediction or any regression scenario](tutorials/predict-prices-with-model-builder.md)</span></span>
