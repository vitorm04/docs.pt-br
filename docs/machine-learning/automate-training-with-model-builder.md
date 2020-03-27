---
title: O que é o Construtor de Modelo e como ele funciona?
description: Como usar o Construtor de Modelo do ML.NET para treinar automaticamente um modelo de machine learning
ms.date: 03/25/2020
ms.custom: overview, mlnet-tooling
ms.openlocfilehash: 9cf66455109908ebd9fc10e62cf4f067609b57d9
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344785"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a><span data-ttu-id="6a057-103">O que é o Construtor de Modelo e como ele funciona?</span><span class="sxs-lookup"><span data-stu-id="6a057-103">What is Model Builder and how does it work?</span></span>

<span data-ttu-id="6a057-104">O Construtor de Modelo do ML.NET é uma extensão gráfica do Visual Studio intuitiva para criar, treinar e implantar modelos de aprendizado de máquina personalizados.</span><span class="sxs-lookup"><span data-stu-id="6a057-104">ML.NET Model Builder is an intuitive graphical Visual Studio extension to build, train, and deploy custom machine learning models.</span></span>

<span data-ttu-id="6a057-105">O Construtor de Modelo usa o aprendizado de máquina automatizado (AutoML) para explorar os algoritmos diferentes de aprendizado de máquina e as configurações para ajudar você a encontrar o que melhor atende ao seu cenário.</span><span class="sxs-lookup"><span data-stu-id="6a057-105">Model Builder uses automated machine learning (AutoML) to explore different machine learning algorithms and settings to help you find the one that best suits your scenario.</span></span>

<span data-ttu-id="6a057-106">Não é necessário ter experiência de aprendizado de máquina para usar o Construtor de Modelo.</span><span class="sxs-lookup"><span data-stu-id="6a057-106">You don't need machine learning expertise to use Model Builder.</span></span> <span data-ttu-id="6a057-107">Você só precisa de um problema para resolver e alguns dados.</span><span class="sxs-lookup"><span data-stu-id="6a057-107">All you need is some data, and a problem to solve.</span></span> <span data-ttu-id="6a057-108">O Construtor de Modelo gera o código para adicionar o modelo em seu aplicativo .NET.</span><span class="sxs-lookup"><span data-stu-id="6a057-108">Model Builder generates the code to add the model to your .NET application.</span></span>

![Animação de interface do usuário da extensão do Visual Studio do Construtor de Modelo](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> <span data-ttu-id="6a057-110">O Construtor de Modelo está atualmente na Versão Prévia.</span><span class="sxs-lookup"><span data-stu-id="6a057-110">Model Builder is currently in Preview.</span></span>

## <a name="scenario"></a><span data-ttu-id="6a057-111">Cenário</span><span class="sxs-lookup"><span data-stu-id="6a057-111">Scenario</span></span>

<span data-ttu-id="6a057-112">Você pode trazer vários cenários diferentes para o Construtor de Modelo para gerar um modelo de machine learning para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6a057-112">You can bring many different scenarios to Model Builder, to generate a machine learning model for your application.</span></span>

<span data-ttu-id="6a057-113">Um cenário é uma descrição do tipo de previsão que você deseja fazer usando seus dados.</span><span class="sxs-lookup"><span data-stu-id="6a057-113">A scenario is a description of the type of prediction you want to make using your data.</span></span> <span data-ttu-id="6a057-114">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="6a057-114">For example:</span></span>

- <span data-ttu-id="6a057-115">prever o volume de vendas futuras do produto com base em dados históricos de vendas</span><span class="sxs-lookup"><span data-stu-id="6a057-115">predict future product sales volume based on historical sales data</span></span>
- <span data-ttu-id="6a057-116">classificar sentimentos como positivos ou negativos com base em revisões de cliente</span><span class="sxs-lookup"><span data-stu-id="6a057-116">classify sentiments as positive or negative based on customer reviews</span></span>
- <span data-ttu-id="6a057-117">detectar se uma transação bancária é fraudulenta</span><span class="sxs-lookup"><span data-stu-id="6a057-117">detect whether a banking transaction is fraudulent</span></span>
- <span data-ttu-id="6a057-118">encaminhar problemas de comentários de clientes para a equipe correta em sua empresa</span><span class="sxs-lookup"><span data-stu-id="6a057-118">route customer feedback issues to the correct team in your company</span></span>

### <a name="which-machine-learning-scenario-is-right-for-me"></a><span data-ttu-id="6a057-119">Qual cenário do aprendizado de máquina é adequado para mim?</span><span class="sxs-lookup"><span data-stu-id="6a057-119">Which machine learning scenario is right for me?</span></span>

<span data-ttu-id="6a057-120">No Model Builder, você precisa selecionar um cenário.</span><span class="sxs-lookup"><span data-stu-id="6a057-120">In Model Builder, you need to select a scenario.</span></span> <span data-ttu-id="6a057-121">O tipo de cenário depende do tipo de previsão que você está tentando fazer.</span><span class="sxs-lookup"><span data-stu-id="6a057-121">The type of scenario depends on what type of prediction you are trying to make.</span></span>

#### <a name="text-classification"></a><span data-ttu-id="6a057-122">Classificação de texto</span><span class="sxs-lookup"><span data-stu-id="6a057-122">Text classification</span></span>

<span data-ttu-id="6a057-123">A classificação é usada para categorizar dados em categorias.</span><span class="sxs-lookup"><span data-stu-id="6a057-123">Classification is used to categorize data into categories.</span></span>

![Diagrama mostrando exemplos de classificação binária incluindo detecção de fraude, mitigação de risco e triagem de aplicativo](media/binary-classification-examples.png)

![Os exemplos de classificação multiclasse que incluem a classificação de documentos e de produtos, roteamento de tíquete de suporte e priorização de problemas do cliente](media/multiclass-classification-examples.png)

#### <a name="value-prediction"></a><span data-ttu-id="6a057-126">Previsão de valor</span><span class="sxs-lookup"><span data-stu-id="6a057-126">Value prediction</span></span>

<span data-ttu-id="6a057-127">A regressão é usada para prever números.</span><span class="sxs-lookup"><span data-stu-id="6a057-127">Regression is used to predict numbers.</span></span>

![Diagrama mostrando exemplos de regressão, como a previsão de preços, a previsão de vendas e a manutenção preditiva](media/regression-examples.png)

#### <a name="image-classification"></a><span data-ttu-id="6a057-129">Classificação de imagens</span><span class="sxs-lookup"><span data-stu-id="6a057-129">Image classification</span></span>

<span data-ttu-id="6a057-130">A classificação de imagens pode ser usada para identificar imagens de diferentes categorias.</span><span class="sxs-lookup"><span data-stu-id="6a057-130">Image classification can be used to identify images of different categories.</span></span> <span data-ttu-id="6a057-131">Por exemplo, diferentes tipos de terreno ou animais ou defeitos de fabricação.</span><span class="sxs-lookup"><span data-stu-id="6a057-131">For example, different types of terrain or animals or manufacturing defects.</span></span>

<span data-ttu-id="6a057-132">Você pode usar o cenário de classificação de imagens se tiver um conjunto de imagens e quiser classificar as imagens em diferentes categorias.</span><span class="sxs-lookup"><span data-stu-id="6a057-132">You can use the image classification scenario if you have a set of images, and you want to classify the images into different categories.</span></span>

#### <a name="recommendation"></a><span data-ttu-id="6a057-133">Recomendação</span><span class="sxs-lookup"><span data-stu-id="6a057-133">Recommendation</span></span>

<span data-ttu-id="6a057-134">O cenário de recomendação prevê uma lista de itens sugeridos para um determinado usuário, com base no quão semelhantes seus gostos e desgostos são com os de outros usuários.</span><span class="sxs-lookup"><span data-stu-id="6a057-134">The recommendation scenario predicts a list of suggested items for a particular user, based on how similar their likes and dislikes are to other users'.</span></span>

<span data-ttu-id="6a057-135">Você pode usar o cenário de recomendação quando você tem um conjunto de usuários e um conjunto de "produtos", como itens para comprar, filmes, livros ou programas de TV, juntamente com um conjunto de "classificações" dos usuários desses produtos.</span><span class="sxs-lookup"><span data-stu-id="6a057-135">You can use the recommendation scenario when you have a set of users and a set of "products", such as items to purchase, movies, books, or TV shows, along with a set of users' "ratings" of those products.</span></span>

## <a name="environment"></a><span data-ttu-id="6a057-136">Ambiente</span><span class="sxs-lookup"><span data-stu-id="6a057-136">Environment</span></span>

<span data-ttu-id="6a057-137">Você pode treinar seu modelo de aprendizado de máquina localmente em sua máquina ou na nuvem no Azure.</span><span class="sxs-lookup"><span data-stu-id="6a057-137">You can train your machine learning model locally on your machine or in the cloud on Azure.</span></span>

<span data-ttu-id="6a057-138">Quando você treina localmente, você trabalha dentro das restrições dos recursos do seu computador (CPU, memória e disco).</span><span class="sxs-lookup"><span data-stu-id="6a057-138">When you train locally, you work within the constraints of your computer resources (CPU, memory, and disk).</span></span> <span data-ttu-id="6a057-139">Quando você treina na nuvem, você pode escalar seus recursos para atender às demandas do seu cenário, especialmente para grandes conjuntos de dados.</span><span class="sxs-lookup"><span data-stu-id="6a057-139">When you train in the cloud, you can scale up your resources to meet the demands of your scenario, especially for large datasets.</span></span>

<span data-ttu-id="6a057-140">O treinamento local é apoiado para todos os cenários.</span><span class="sxs-lookup"><span data-stu-id="6a057-140">Local training is supported for all scenarios.</span></span>

<span data-ttu-id="6a057-141">O treinamento do Azure é suportado para classificação de imagem.</span><span class="sxs-lookup"><span data-stu-id="6a057-141">Azure training is supported for Image Classification.</span></span>

## <a name="data"></a><span data-ttu-id="6a057-142">Dados</span><span class="sxs-lookup"><span data-stu-id="6a057-142">Data</span></span>

<span data-ttu-id="6a057-143">Depois de escolher seu cenário, o Model Builder pede que você forneça um conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="6a057-143">Once you have chosen your scenario, Model Builder asks you to provide a dataset.</span></span> <span data-ttu-id="6a057-144">Os dados são usados para treinar, avaliar e escolher o melhor modelo para seu cenário.</span><span class="sxs-lookup"><span data-stu-id="6a057-144">The data is used to train, evaluate, and choose the best model for your scenario.</span></span>

![Diagrama mostrando as etapas do Construtor de Modelos](media/model-builder-steps.png)

<span data-ttu-id="6a057-146">O Model Builder suporta conjuntos de dados nos formatos .tsv, .csv, .txt, bem como no formato de banco de dados SQL.</span><span class="sxs-lookup"><span data-stu-id="6a057-146">Model Builder supports datasets in .tsv, .csv, .txt formats, as well as SQL database format.</span></span> <span data-ttu-id="6a057-147">Se você tiver um arquivo .txt, as `,` `;` colunas devem ser separadas com , ou `/t` e o arquivo deve ter uma linha de cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="6a057-147">If you have a .txt file, columns should be separated with `,`, `;` or `/t` and the file must have a header row.</span></span>

<span data-ttu-id="6a057-148">Se o conjunto de dados for composto por `.jpg` imagens, os tipos de arquivos suportados serão e `.png`.</span><span class="sxs-lookup"><span data-stu-id="6a057-148">If the dataset is made up of images, the supported file types are `.jpg` and `.png`.</span></span>

<span data-ttu-id="6a057-149">Para obter mais informações, consulte [Carregar dados de treinamento no Model Builder](how-to-guides/load-data-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="6a057-149">For more information, see [Load training data into Model Builder](how-to-guides/load-data-model-builder.md).</span></span>

### <a name="choose-the-output-to-predict-label"></a><span data-ttu-id="6a057-150">Escolha a saída para prever (rótulo)</span><span class="sxs-lookup"><span data-stu-id="6a057-150">Choose the output to predict (label)</span></span>

<span data-ttu-id="6a057-151">Um conjunto de dados é uma tabela de linhas de exemplos de treinamento e colunas de atributos.</span><span class="sxs-lookup"><span data-stu-id="6a057-151">A dataset is a table of rows of training examples, and columns of attributes.</span></span> <span data-ttu-id="6a057-152">Cada linha tem:</span><span class="sxs-lookup"><span data-stu-id="6a057-152">Each row has:</span></span>

- <span data-ttu-id="6a057-153">um **rótulo** (o atributo que você deseja prever)</span><span class="sxs-lookup"><span data-stu-id="6a057-153">a **label** (the attribute that you want to predict)</span></span>
- <span data-ttu-id="6a057-154">**recursos** (atributos que são usados como entradas para prever o rótulo).</span><span class="sxs-lookup"><span data-stu-id="6a057-154">**features** (attributes that are used as inputs to predict the label).</span></span>

<span data-ttu-id="6a057-155">Para o cenário de previsão do preço das casas, os recursos podem ser:</span><span class="sxs-lookup"><span data-stu-id="6a057-155">For the house-price prediction scenario, the features could be:</span></span>

- <span data-ttu-id="6a057-156">os metros quadrados da casa</span><span class="sxs-lookup"><span data-stu-id="6a057-156">the square footage of the house</span></span>
- <span data-ttu-id="6a057-157">o número de quartos e banheiros</span><span class="sxs-lookup"><span data-stu-id="6a057-157">the number of bedrooms and bathrooms</span></span>
- <span data-ttu-id="6a057-158">o código postal</span><span class="sxs-lookup"><span data-stu-id="6a057-158">the zip code</span></span>

<span data-ttu-id="6a057-159">O rótulo é o preço histórico de casas para essa linha de valores de metro quadrado, quarto e banheiro e código postal.</span><span class="sxs-lookup"><span data-stu-id="6a057-159">The label is the historical house price for that row of square footage, bedroom, and bathroom values and zip code.</span></span>

![Tabela mostrando linhas e colunas de dados de preços de casas com recursos que consistem em quartos de tamanho de código postal e etiqueta de preço](media/model-builder-data.png)

### <a name="example-datasets"></a><span data-ttu-id="6a057-161">Conjuntos de dados de amostra</span><span class="sxs-lookup"><span data-stu-id="6a057-161">Example datasets</span></span>

<span data-ttu-id="6a057-162">Se você ainda não tiver seus próprios dados, experimente um desses conjuntos de dados:</span><span class="sxs-lookup"><span data-stu-id="6a057-162">If you don't have your own data yet, try out one of these datasets:</span></span>

|<span data-ttu-id="6a057-163">Cenário</span><span class="sxs-lookup"><span data-stu-id="6a057-163">Scenario</span></span>|<span data-ttu-id="6a057-164">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6a057-164">Example</span></span>|<span data-ttu-id="6a057-165">Dados</span><span class="sxs-lookup"><span data-stu-id="6a057-165">Data</span></span>|<span data-ttu-id="6a057-166">Rótulo</span><span class="sxs-lookup"><span data-stu-id="6a057-166">Label</span></span>|<span data-ttu-id="6a057-167">Recursos</span><span class="sxs-lookup"><span data-stu-id="6a057-167">Features</span></span>|
|-|-|-|-|-|
|<span data-ttu-id="6a057-168">classificação</span><span class="sxs-lookup"><span data-stu-id="6a057-168">Classification</span></span>|<span data-ttu-id="6a057-169">Prever anomalias de vendas</span><span class="sxs-lookup"><span data-stu-id="6a057-169">Predict sales anomalies</span></span>|[<span data-ttu-id="6a057-170">dados de vendas do produto</span><span class="sxs-lookup"><span data-stu-id="6a057-170">product sales data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|<span data-ttu-id="6a057-171">Vendas do Produto</span><span class="sxs-lookup"><span data-stu-id="6a057-171">Product Sales</span></span>|<span data-ttu-id="6a057-172">Month</span><span class="sxs-lookup"><span data-stu-id="6a057-172">Month</span></span>|
||<span data-ttu-id="6a057-173">Prever o sentimento dos comentários do site</span><span class="sxs-lookup"><span data-stu-id="6a057-173">Predict sentiment of website comments</span></span>|[<span data-ttu-id="6a057-174">dados de comentário do site</span><span class="sxs-lookup"><span data-stu-id="6a057-174">website comment data</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|<span data-ttu-id="6a057-175">Rótulo (0 quando o sentimento é negativo, 1 quando é positivo)</span><span class="sxs-lookup"><span data-stu-id="6a057-175">Label (0 when negative sentiment, 1 when positive)</span></span>|<span data-ttu-id="6a057-176">Comentário, ano</span><span class="sxs-lookup"><span data-stu-id="6a057-176">Comment, Year</span></span>|
||<span data-ttu-id="6a057-177">Prever transações fraudulentas de cartão de crédito</span><span class="sxs-lookup"><span data-stu-id="6a057-177">Predict fraudulent credit card transactions</span></span>|[<span data-ttu-id="6a057-178">dados do cartão de crédito</span><span class="sxs-lookup"><span data-stu-id="6a057-178">credit card data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|<span data-ttu-id="6a057-179">Classe (1 quando fraudulenta, caso contrário, 0)</span><span class="sxs-lookup"><span data-stu-id="6a057-179">Class (1 when fraudulent, 0 otherwise)</span></span>|<span data-ttu-id="6a057-180">Quantidade, V1-V28 (recursos anônimos)</span><span class="sxs-lookup"><span data-stu-id="6a057-180">Amount, V1-V28 (anonymized features)</span></span>|
||<span data-ttu-id="6a057-181">Prever o tipo de problema em um repositório do GitHub</span><span class="sxs-lookup"><span data-stu-id="6a057-181">Predict the type of issue in a GitHub repository</span></span>|[<span data-ttu-id="6a057-182">dados de problema do GitHub</span><span class="sxs-lookup"><span data-stu-id="6a057-182">GitHub issue data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|<span data-ttu-id="6a057-183">Área</span><span class="sxs-lookup"><span data-stu-id="6a057-183">Area</span></span>|<span data-ttu-id="6a057-184">Título, Descrição</span><span class="sxs-lookup"><span data-stu-id="6a057-184">Title, Description</span></span>|
|<span data-ttu-id="6a057-185">Previsão de valor</span><span class="sxs-lookup"><span data-stu-id="6a057-185">Value prediction</span></span>|<span data-ttu-id="6a057-186">Prever preço da tarifa de táxi</span><span class="sxs-lookup"><span data-stu-id="6a057-186">Predict taxi fare price</span></span>|[<span data-ttu-id="6a057-187">dados de tarifas de táxi</span><span class="sxs-lookup"><span data-stu-id="6a057-187">taxi fare data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|<span data-ttu-id="6a057-188">Tarifa</span><span class="sxs-lookup"><span data-stu-id="6a057-188">Fare</span></span>|<span data-ttu-id="6a057-189">Tempo da corrida, distância</span><span class="sxs-lookup"><span data-stu-id="6a057-189">Trip time, distance</span></span>|
|<span data-ttu-id="6a057-190">Classificação de imagens</span><span class="sxs-lookup"><span data-stu-id="6a057-190">Image classification</span></span>|<span data-ttu-id="6a057-191">Prever a categoria de um problema</span><span class="sxs-lookup"><span data-stu-id="6a057-191">Predict the category of an issue</span></span>|[<span data-ttu-id="6a057-192">imagens de flores</span><span class="sxs-lookup"><span data-stu-id="6a057-192">flower images</span></span>](http://download.tensorflow.org/example_images/flower_photos.tgz)|<span data-ttu-id="6a057-193">O tipo de flor: margarida, dente-de-leão, rosas, girassóis, tulipas</span><span class="sxs-lookup"><span data-stu-id="6a057-193">The type of flower: daisy, dandelion, roses, sunflowers, tulips</span></span>|<span data-ttu-id="6a057-194">Os dados da imagem em si</span><span class="sxs-lookup"><span data-stu-id="6a057-194">The image data itself</span></span>|
|<span data-ttu-id="6a057-195">Recomendação</span><span class="sxs-lookup"><span data-stu-id="6a057-195">Recommendation</span></span>|<span data-ttu-id="6a057-196">Prever filmes que alguém vai gostar</span><span class="sxs-lookup"><span data-stu-id="6a057-196">Predict movies that someone will like</span></span>|[<span data-ttu-id="6a057-197">classificações de filmes</span><span class="sxs-lookup"><span data-stu-id="6a057-197">movie ratings</span></span>](http://files.grouplens.org/datasets/movielens/ml-latest-small.zip)|<span data-ttu-id="6a057-198">Usuários, Filmes</span><span class="sxs-lookup"><span data-stu-id="6a057-198">Users, Movies</span></span>|<span data-ttu-id="6a057-199">Classificações</span><span class="sxs-lookup"><span data-stu-id="6a057-199">Ratings</span></span>|

## <a name="train"></a><span data-ttu-id="6a057-200">Treinar</span><span class="sxs-lookup"><span data-stu-id="6a057-200">Train</span></span>

<span data-ttu-id="6a057-201">Depois de selecionar seu cenário, dados e rótulo, o Construtor de Modelo treina o modelo.</span><span class="sxs-lookup"><span data-stu-id="6a057-201">Once you select your scenario, data, and label, Model Builder trains the model.</span></span>

### <a name="what-is-training"></a><span data-ttu-id="6a057-202">O que é o treinamento?</span><span class="sxs-lookup"><span data-stu-id="6a057-202">What is training?</span></span>

<span data-ttu-id="6a057-203">O treinamento é um processo automático pelo qual Construtor de Modelo ensina seu modelo a responder perguntas para seu cenário.</span><span class="sxs-lookup"><span data-stu-id="6a057-203">Training is an automatic process by which Model Builder teaches your model how to answer questions for your scenario.</span></span> <span data-ttu-id="6a057-204">Depois de treinado, seu modelo pode fazer previsões com dados de entrada não vistos antes.</span><span class="sxs-lookup"><span data-stu-id="6a057-204">Once trained, your model can make predictions with input data that it has not seen before.</span></span> <span data-ttu-id="6a057-205">Por exemplo, se estiver prevendo preços de casas e uma nova casa for oferecida no mercado, você poderá prever o preço de venda.</span><span class="sxs-lookup"><span data-stu-id="6a057-205">For example, if you are predicting house prices and a new house comes on the market, you can predict its sale price.</span></span>

<span data-ttu-id="6a057-206">Como o Construtor de Modelo usa aprendizado de máquina automatizado (AutoML), ele não requer nenhuma entrada ou ajuste de você durante o treinamento.</span><span class="sxs-lookup"><span data-stu-id="6a057-206">Because Model Builder uses automated machine learning (AutoML), it does not require any input or tuning from you during training.</span></span>

### <a name="how-long-should-i-train-for"></a><span data-ttu-id="6a057-207">Por quanto tempo devo treinar?</span><span class="sxs-lookup"><span data-stu-id="6a057-207">How long should I train for?</span></span>

<span data-ttu-id="6a057-208">O Model Builder usa o AutoML para explorar vários modelos para encontrar o modelo de melhor desempenho.</span><span class="sxs-lookup"><span data-stu-id="6a057-208">Model Builder uses AutoML to explore multiple models to find you the best performing model.</span></span>

<span data-ttu-id="6a057-209">Períodos de treinamento mais longos permitem que o AutoML explore mais modelos com uma gama mais ampla de configurações.</span><span class="sxs-lookup"><span data-stu-id="6a057-209">Longer training periods allow AutoML to explore more models with a wider range of settings.</span></span>

<span data-ttu-id="6a057-210">A tabela abaixo resume o tempo médio gasto para obter um bom desempenho para um conjunto de conjuntos de dados exemplos, em uma máquina local.</span><span class="sxs-lookup"><span data-stu-id="6a057-210">The table below summarizes the average time taken to get good performance for a suite of example datasets, on a local machine.</span></span>

|<span data-ttu-id="6a057-211">Tamanho do conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="6a057-211">Dataset size</span></span>|<span data-ttu-id="6a057-212">Tempo médio para treinar</span><span class="sxs-lookup"><span data-stu-id="6a057-212">Average time to train</span></span>|
|------------|---------------------|
|<span data-ttu-id="6a057-213">0 - 10 MB</span><span class="sxs-lookup"><span data-stu-id="6a057-213">0 - 10 MB</span></span>|<span data-ttu-id="6a057-214">10 s</span><span class="sxs-lookup"><span data-stu-id="6a057-214">10 sec</span></span>|
|<span data-ttu-id="6a057-215">10 - 100 MB</span><span class="sxs-lookup"><span data-stu-id="6a057-215">10 - 100 MB</span></span>|<span data-ttu-id="6a057-216">10 min</span><span class="sxs-lookup"><span data-stu-id="6a057-216">10 min</span></span>|
|<span data-ttu-id="6a057-217">100 - 500 MB</span><span class="sxs-lookup"><span data-stu-id="6a057-217">100 - 500 MB</span></span>|<span data-ttu-id="6a057-218">30 min</span><span class="sxs-lookup"><span data-stu-id="6a057-218">30 min</span></span>|
|<span data-ttu-id="6a057-219">500 - 1 GB</span><span class="sxs-lookup"><span data-stu-id="6a057-219">500 - 1 GB</span></span>|<span data-ttu-id="6a057-220">60 min</span><span class="sxs-lookup"><span data-stu-id="6a057-220">60 min</span></span>|
|<span data-ttu-id="6a057-221">1 GB+</span><span class="sxs-lookup"><span data-stu-id="6a057-221">1 GB+</span></span>|<span data-ttu-id="6a057-222">Mais de 3 horas</span><span class="sxs-lookup"><span data-stu-id="6a057-222">3+ hours</span></span>|

<span data-ttu-id="6a057-223">Esses números são apenas um guia.</span><span class="sxs-lookup"><span data-stu-id="6a057-223">These numbers are a guide only.</span></span> <span data-ttu-id="6a057-224">O tempo exato de treinamento depende de:</span><span class="sxs-lookup"><span data-stu-id="6a057-224">The exact length of training is dependent on:</span></span>

- <span data-ttu-id="6a057-225">o número de recursos (colunas) sendo usados como entrada para o modelo</span><span class="sxs-lookup"><span data-stu-id="6a057-225">the number of features (columns) being used to as input to the model</span></span>
- <span data-ttu-id="6a057-226">o tipo de colunas</span><span class="sxs-lookup"><span data-stu-id="6a057-226">the type of columns</span></span>
- <span data-ttu-id="6a057-227">a tarefa ML</span><span class="sxs-lookup"><span data-stu-id="6a057-227">the ML task</span></span>
- <span data-ttu-id="6a057-228">o desempenho da CPU, disco e memória da máquina usada para treinamento</span><span class="sxs-lookup"><span data-stu-id="6a057-228">the CPU, disk, and memory performance of the machine used for training</span></span>

## <a name="evaluate"></a><span data-ttu-id="6a057-229">Avaliar</span><span class="sxs-lookup"><span data-stu-id="6a057-229">Evaluate</span></span>

<span data-ttu-id="6a057-230">Avaliação é o processo de medir o quão bom é o seu modelo.</span><span class="sxs-lookup"><span data-stu-id="6a057-230">Evaluation is the process of measuring how good your model is.</span></span> <span data-ttu-id="6a057-231">O Model Builder usa o modelo treinado para fazer previsões com novos dados de teste e, em seguida, mede o quão boas são as previsões.</span><span class="sxs-lookup"><span data-stu-id="6a057-231">Model Builder uses the trained model to make predictions with new test data, and then measures how good the predictions are.</span></span>

<span data-ttu-id="6a057-232">O Construtor de Modelo divide os dados de treinamento em um conjunto de treinamento e um conjunto de teste.</span><span class="sxs-lookup"><span data-stu-id="6a057-232">Model Builder splits the training data into a training set and a test set.</span></span> <span data-ttu-id="6a057-233">Os dados de treinamento (80%) são usados para treinar seu modelo e os dados de teste (20%) são retidos para avaliar seu modelo.</span><span class="sxs-lookup"><span data-stu-id="6a057-233">The training data (80%) is used to train your model and the test data (20%) is held back to evaluate your model.</span></span>

### <a name="how-do-i-understand-my-model-performance"></a><span data-ttu-id="6a057-234">Como entendo meu desempenho como modelo?</span><span class="sxs-lookup"><span data-stu-id="6a057-234">How do I understand my model performance?</span></span>

<span data-ttu-id="6a057-235">Um cenário mapeia uma tarefa de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="6a057-235">A scenario maps to a machine learning task.</span></span> <span data-ttu-id="6a057-236">Cada tarefa ml tem seu próprio conjunto de métricas de avaliação.</span><span class="sxs-lookup"><span data-stu-id="6a057-236">Each ML task has its own set of evaluation metrics.</span></span>

#### <a name="value-prediction"></a><span data-ttu-id="6a057-237">Previsão de valor</span><span class="sxs-lookup"><span data-stu-id="6a057-237">Value prediction</span></span>

<span data-ttu-id="6a057-238">A métrica padrão para problemas de previsão de valor é RSquared, o valor do RSquared varia entre 0 e 1.</span><span class="sxs-lookup"><span data-stu-id="6a057-238">The default metric for value prediction problems is RSquared, the value of RSquared ranges between 0 and 1.</span></span> <span data-ttu-id="6a057-239">1 é o melhor valor possível ou, em outras palavras, quanto mais perto o valor de RSquared para 1, melhor o seu modelo está realizando.</span><span class="sxs-lookup"><span data-stu-id="6a057-239">1 is the best possible value or in other words the closer the value of RSquared to 1 the better your model is performing.</span></span>

<span data-ttu-id="6a057-240">Outras métricas relatadas, como perda absoluta, perda quadrada e perda de RMS são métricas adicionais, que podem ser usadas para entender como seu modelo está se saindo e compará-lo com outros modelos de previsão de valor.</span><span class="sxs-lookup"><span data-stu-id="6a057-240">Other metrics reported such as absolute-loss, squared-loss, and RMS loss are additional metrics, which can be used to understand how your model is performing and comparing it against other value prediction models.</span></span>

#### <a name="classification-2-categories"></a><span data-ttu-id="6a057-241">Classificação (2 categorias)</span><span class="sxs-lookup"><span data-stu-id="6a057-241">Classification (2 categories)</span></span>

<span data-ttu-id="6a057-242">A métrica padrão para problemas de classificação é a precisão.</span><span class="sxs-lookup"><span data-stu-id="6a057-242">The default metric for classification problems is accuracy.</span></span> <span data-ttu-id="6a057-243">A precisão define a proporção de previsões corretas que seu modelo está fazendo ao longo do conjunto de dados do teste.</span><span class="sxs-lookup"><span data-stu-id="6a057-243">Accuracy defines the proportion of correct predictions your model is making over the test dataset.</span></span> <span data-ttu-id="6a057-244">Quanto mais perto de 100% ou 1.0 melhor.</span><span class="sxs-lookup"><span data-stu-id="6a057-244">The closer to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="6a057-245">Outras métricas relatadas, como AUC (Área a curva), que mede a taxa positiva verdadeira versus a taxa falsa positiva, devem ser maiores que 0,50 para que os modelos sejam aceitáveis.</span><span class="sxs-lookup"><span data-stu-id="6a057-245">Other metrics reported such as AUC (Area under the curve), which measures the true positive rate vs. the false positive rate should be greater than 0.50 for models to be acceptable.</span></span>

<span data-ttu-id="6a057-246">Métricas adicionais como a pontuação da F1 podem ser usadas para controlar o equilíbrio entre Precisão e Recall.</span><span class="sxs-lookup"><span data-stu-id="6a057-246">Additional metrics like F1 score can be used to control the balance between Precision and Recall.</span></span>

#### <a name="classification-3-categories"></a><span data-ttu-id="6a057-247">Classificação (3+ categorias)</span><span class="sxs-lookup"><span data-stu-id="6a057-247">Classification (3+ categories)</span></span>

<span data-ttu-id="6a057-248">A métrica padrão para classificação multiclasse é Micro Accuracy.</span><span class="sxs-lookup"><span data-stu-id="6a057-248">The default metric for Multi-class classification is Micro Accuracy.</span></span> <span data-ttu-id="6a057-249">Quanto mais perto da Micro Precisão 100% ou 1.0, melhor será.</span><span class="sxs-lookup"><span data-stu-id="6a057-249">The closer the Micro Accuracy to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="6a057-250">Outra métrica importante para a classificação multiclasse é a macro-precisão, semelhante à Micro-precisão quanto mais perto de 1.0 melhor.</span><span class="sxs-lookup"><span data-stu-id="6a057-250">Another important metric for Multi-class classification is Macro-accuracy, similar to Micro-accuracy the closer to 1.0 the better it is.</span></span> <span data-ttu-id="6a057-251">Uma boa maneira de pensar sobre esses dois tipos de precisão é:</span><span class="sxs-lookup"><span data-stu-id="6a057-251">A good way to think about these two types of accuracy is:</span></span>

- <span data-ttu-id="6a057-252">Micro-precisão: Com que frequência um bilhete de entrada é classificado para a equipe certa?</span><span class="sxs-lookup"><span data-stu-id="6a057-252">Micro-accuracy: How often does an incoming ticket get classified to the right team?</span></span>
- <span data-ttu-id="6a057-253">Macro-precisão: Para uma equipe média, quantas vezes um bilhete de entrada é correto para sua equipe?</span><span class="sxs-lookup"><span data-stu-id="6a057-253">Macro-accuracy: For an average team, how often is an incoming ticket correct for their team?</span></span>

### <a name="more-information-on-evaluation-metrics"></a><span data-ttu-id="6a057-254">Mais informações sobre métricas de avaliação</span><span class="sxs-lookup"><span data-stu-id="6a057-254">More information on evaluation metrics</span></span>

<span data-ttu-id="6a057-255">Para obter mais informações, consulte [métricas de avaliação de modelo](resources/metrics.md).</span><span class="sxs-lookup"><span data-stu-id="6a057-255">For more information, see [model evaluation metrics](resources/metrics.md).</span></span>

## <a name="improve"></a><span data-ttu-id="6a057-256">Aprimorar</span><span class="sxs-lookup"><span data-stu-id="6a057-256">Improve</span></span>

<span data-ttu-id="6a057-257">Se a sua pontuação de desempenho do modelo não for tão boa quanto deseja, você poderá:</span><span class="sxs-lookup"><span data-stu-id="6a057-257">If your model performance score is not as good as you want it to be, you can:</span></span>

- <span data-ttu-id="6a057-258">Treinar por um período maior de tempo.</span><span class="sxs-lookup"><span data-stu-id="6a057-258">Train for a longer period of time.</span></span> <span data-ttu-id="6a057-259">Com mais tempo, o motor automatizado de aprendizado de máquina experimenta com mais algoritmos e configurações.</span><span class="sxs-lookup"><span data-stu-id="6a057-259">With more time, the automated machine learning engine experiments with more algorithms and settings.</span></span>

- <span data-ttu-id="6a057-260">Adicionar mais dados.</span><span class="sxs-lookup"><span data-stu-id="6a057-260">Add more data.</span></span> <span data-ttu-id="6a057-261">Às vezes, a quantidade de dados não é suficiente para treinar um modelo de machine learning de alta qualidade.</span><span class="sxs-lookup"><span data-stu-id="6a057-261">Sometimes the amount of data is not sufficient to train a high-quality machine learning model.</span></span>

- <span data-ttu-id="6a057-262">Balancear seus dados.</span><span class="sxs-lookup"><span data-stu-id="6a057-262">Balance your data.</span></span> <span data-ttu-id="6a057-263">Para tarefas de classificação, certifique-se de que o conjunto de treinamento esteja equilibrado nas categorias.</span><span class="sxs-lookup"><span data-stu-id="6a057-263">For classification tasks, make sure that the training set is balanced across the categories.</span></span> <span data-ttu-id="6a057-264">Por exemplo, se você tiver quatro classes para 100 exemplos de treinamento e as duas primeiras classes (tag1 e tag2) forem usadas para 90 registros, mas as outras duas (tag3 e tag4) forem usadas apenas nos 10 registros restantes, a falta de dados balanceados poderá fazer com que seu modelo tenha dificuldades para prever corretamente o tag3 ou o tag4.</span><span class="sxs-lookup"><span data-stu-id="6a057-264">For example, if you have four classes for 100 training examples, and the two first classes (tag1 and tag2) are used for 90 records, but the other two (tag3 and tag4) are only used on the remaining 10 records, the lack of balanced data may cause your model to struggle to correctly predict tag3 or tag4.</span></span>

## <a name="code"></a><span data-ttu-id="6a057-265">Código</span><span class="sxs-lookup"><span data-stu-id="6a057-265">Code</span></span>

<span data-ttu-id="6a057-266">Após a fase de avaliação, o Construtor de Modelo gera um arquivo de modelo e o código que você pode usar para adicionar o modelo ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6a057-266">After the evaluation phase, Model Builder outputs a model file, and code that you can use to add the model to your application.</span></span> <span data-ttu-id="6a057-267">Modelos do ML.NET são salvos como um arquivo zip.</span><span class="sxs-lookup"><span data-stu-id="6a057-267">ML.NET models are saved as a zip file.</span></span> <span data-ttu-id="6a057-268">O código para carregar e usar o modelo é adicionado como um novo projeto em sua solução.</span><span class="sxs-lookup"><span data-stu-id="6a057-268">The code to load and use your model is added as a new project in your solution.</span></span> <span data-ttu-id="6a057-269">O Construtor de Modelo também adiciona um aplicativo de console de exemplo que você pode executar para ver seu modelo em ação.</span><span class="sxs-lookup"><span data-stu-id="6a057-269">Model Builder also adds a sample console app that you can run to see your model in action.</span></span>

<span data-ttu-id="6a057-270">Além disso, o Construtor de Modelo cria o código que gerou o modelo para que você possa entender as etapas usadas na geração do modelo.</span><span class="sxs-lookup"><span data-stu-id="6a057-270">In addition, Model Builder outputs the code that generated the model, so that you can understand the steps used to generate the model.</span></span> <span data-ttu-id="6a057-271">Você também pode usar o código de treinamento do modelo para treinar novamente seu modelo com novos dados.</span><span class="sxs-lookup"><span data-stu-id="6a057-271">You can also use the model training code to retrain your model with new data.</span></span>

## <a name="whats-next"></a><span data-ttu-id="6a057-272">O que vem a seguir?</span><span class="sxs-lookup"><span data-stu-id="6a057-272">What's next?</span></span>

<span data-ttu-id="6a057-273">[Instalar](how-to-guides/install-model-builder.md) a extensão do Visual Studio do Construtor de Modelos</span><span class="sxs-lookup"><span data-stu-id="6a057-273">[Install](how-to-guides/install-model-builder.md) the Model Builder Visual Studio extension</span></span>

<span data-ttu-id="6a057-274">Experimente a [previsão de preço ou qualquer cenário de regressão](tutorials/predict-prices-with-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="6a057-274">Try [price prediction or any regression scenario](tutorials/predict-prices-with-model-builder.md)</span></span>
