---
title: O que é o Construtor de Modelo e como ele funciona?
description: Como usar o Construtor de Modelo do ML.NET para treinar automaticamente um modelo de machine learning
ms.date: 06/01/2020
ms.custom: overview, mlnet-tooling
ms.openlocfilehash: 2ed4a0c3c94ae9f46bb1cf6ddb1e9774baf82367
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289493"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a><span data-ttu-id="95271-103">O que é o Construtor de Modelo e como ele funciona?</span><span class="sxs-lookup"><span data-stu-id="95271-103">What is Model Builder and how does it work?</span></span>

<span data-ttu-id="95271-104">O Construtor de Modelo do ML.NET é uma extensão gráfica do Visual Studio intuitiva para criar, treinar e implantar modelos de aprendizado de máquina personalizados.</span><span class="sxs-lookup"><span data-stu-id="95271-104">ML.NET Model Builder is an intuitive graphical Visual Studio extension to build, train, and deploy custom machine learning models.</span></span>

<span data-ttu-id="95271-105">O Construtor de Modelo usa o aprendizado de máquina automatizado (AutoML) para explorar os algoritmos diferentes de aprendizado de máquina e as configurações para ajudar você a encontrar o que melhor atende ao seu cenário.</span><span class="sxs-lookup"><span data-stu-id="95271-105">Model Builder uses automated machine learning (AutoML) to explore different machine learning algorithms and settings to help you find the one that best suits your scenario.</span></span>

<span data-ttu-id="95271-106">Não é necessário ter experiência de aprendizado de máquina para usar o Construtor de Modelo.</span><span class="sxs-lookup"><span data-stu-id="95271-106">You don't need machine learning expertise to use Model Builder.</span></span> <span data-ttu-id="95271-107">Você só precisa de um problema para resolver e alguns dados.</span><span class="sxs-lookup"><span data-stu-id="95271-107">All you need is some data, and a problem to solve.</span></span> <span data-ttu-id="95271-108">O Construtor de Modelo gera o código para adicionar o modelo em seu aplicativo .NET.</span><span class="sxs-lookup"><span data-stu-id="95271-108">Model Builder generates the code to add the model to your .NET application.</span></span>

![Animação de interface do usuário da extensão do Visual Studio do Construtor de Modelo](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> <span data-ttu-id="95271-110">O Construtor de Modelo está atualmente na Versão Prévia.</span><span class="sxs-lookup"><span data-stu-id="95271-110">Model Builder is currently in Preview.</span></span>

## <a name="scenario"></a><span data-ttu-id="95271-111">Cenário</span><span class="sxs-lookup"><span data-stu-id="95271-111">Scenario</span></span>

<span data-ttu-id="95271-112">Você pode trazer vários cenários diferentes para o Construtor de Modelo para gerar um modelo de machine learning para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="95271-112">You can bring many different scenarios to Model Builder, to generate a machine learning model for your application.</span></span>

<span data-ttu-id="95271-113">Um cenário é uma descrição do tipo de previsão que você deseja fazer usando seus dados.</span><span class="sxs-lookup"><span data-stu-id="95271-113">A scenario is a description of the type of prediction you want to make using your data.</span></span> <span data-ttu-id="95271-114">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="95271-114">For example:</span></span>

- <span data-ttu-id="95271-115">prever o volume de vendas futuras do produto com base em dados históricos de vendas</span><span class="sxs-lookup"><span data-stu-id="95271-115">predict future product sales volume based on historical sales data</span></span>
- <span data-ttu-id="95271-116">classificar sentimentos como positivos ou negativos com base em revisões de cliente</span><span class="sxs-lookup"><span data-stu-id="95271-116">classify sentiments as positive or negative based on customer reviews</span></span>
- <span data-ttu-id="95271-117">detectar se uma transação bancária é fraudulenta</span><span class="sxs-lookup"><span data-stu-id="95271-117">detect whether a banking transaction is fraudulent</span></span>
- <span data-ttu-id="95271-118">encaminhar problemas de comentários de clientes para a equipe correta em sua empresa</span><span class="sxs-lookup"><span data-stu-id="95271-118">route customer feedback issues to the correct team in your company</span></span>

### <a name="which-machine-learning-scenario-is-right-for-me"></a><span data-ttu-id="95271-119">Qual cenário do aprendizado de máquina é adequado para mim?</span><span class="sxs-lookup"><span data-stu-id="95271-119">Which machine learning scenario is right for me?</span></span>

<span data-ttu-id="95271-120">No construtor de modelos, você precisa selecionar um cenário.</span><span class="sxs-lookup"><span data-stu-id="95271-120">In Model Builder, you need to select a scenario.</span></span> <span data-ttu-id="95271-121">O tipo de cenário depende do tipo de previsão que você está tentando fazer.</span><span class="sxs-lookup"><span data-stu-id="95271-121">The type of scenario depends on what type of prediction you are trying to make.</span></span>

#### <a name="text-classification"></a><span data-ttu-id="95271-122">Classificação de texto</span><span class="sxs-lookup"><span data-stu-id="95271-122">Text classification</span></span>

<span data-ttu-id="95271-123">A classificação é usada para categorizar dados em categorias.</span><span class="sxs-lookup"><span data-stu-id="95271-123">Classification is used to categorize data into categories.</span></span>

![Diagrama mostrando exemplos de classificação binária incluindo detecção de fraude, mitigação de risco e triagem de aplicativo](media/binary-classification-examples.png)

![Os exemplos de classificação multiclasse que incluem a classificação de documentos e de produtos, roteamento de tíquete de suporte e priorização de problemas do cliente](media/multiclass-classification-examples.png)

#### <a name="value-prediction"></a><span data-ttu-id="95271-126">Previsão de valor</span><span class="sxs-lookup"><span data-stu-id="95271-126">Value prediction</span></span>

<span data-ttu-id="95271-127">A regressão é usada para prever números.</span><span class="sxs-lookup"><span data-stu-id="95271-127">Regression is used to predict numbers.</span></span>

![Diagrama mostrando exemplos de regressão, como a previsão de preços, a previsão de vendas e a manutenção preditiva](media/regression-examples.png)

#### <a name="image-classification"></a><span data-ttu-id="95271-129">Classificação de imagens</span><span class="sxs-lookup"><span data-stu-id="95271-129">Image classification</span></span>

<span data-ttu-id="95271-130">A classificação de imagem pode ser usada para identificar imagens de diferentes categorias.</span><span class="sxs-lookup"><span data-stu-id="95271-130">Image classification can be used to identify images of different categories.</span></span> <span data-ttu-id="95271-131">Por exemplo, tipos diferentes de terrenos, animais ou defeitos de fabricação.</span><span class="sxs-lookup"><span data-stu-id="95271-131">For example, different types of terrain or animals or manufacturing defects.</span></span>

<span data-ttu-id="95271-132">Você pode usar o cenário de classificação de imagem se tiver um conjunto de imagens e desejar classificar as imagens em categorias diferentes.</span><span class="sxs-lookup"><span data-stu-id="95271-132">You can use the image classification scenario if you have a set of images, and you want to classify the images into different categories.</span></span>

#### <a name="recommendation"></a><span data-ttu-id="95271-133">Recomendação</span><span class="sxs-lookup"><span data-stu-id="95271-133">Recommendation</span></span>

<span data-ttu-id="95271-134">O cenário de recomendação prevê uma lista de itens sugeridos para um usuário específico, de acordo com a semelhança com que seu gosto e não gosta de outros usuários.</span><span class="sxs-lookup"><span data-stu-id="95271-134">The recommendation scenario predicts a list of suggested items for a particular user, based on how similar their likes and dislikes are to other users'.</span></span>

<span data-ttu-id="95271-135">Você pode usar o cenário de recomendação quando tiver um conjunto de usuários e um conjunto de "produtos", como itens para compra, filmes, livros ou programas de TV, juntamente com um conjunto de "classificações" de usuários desses produtos.</span><span class="sxs-lookup"><span data-stu-id="95271-135">You can use the recommendation scenario when you have a set of users and a set of "products", such as items to purchase, movies, books, or TV shows, along with a set of users' "ratings" of those products.</span></span>

## <a name="environment"></a><span data-ttu-id="95271-136">Ambiente</span><span class="sxs-lookup"><span data-stu-id="95271-136">Environment</span></span>

<span data-ttu-id="95271-137">Você pode treinar seu modelo de aprendizado de máquina localmente no seu computador ou na nuvem no Azure.</span><span class="sxs-lookup"><span data-stu-id="95271-137">You can train your machine learning model locally on your machine or in the cloud on Azure.</span></span>

<span data-ttu-id="95271-138">Ao treinar localmente, você trabalha dentro das restrições dos recursos do computador (CPU, memória e disco).</span><span class="sxs-lookup"><span data-stu-id="95271-138">When you train locally, you work within the constraints of your computer resources (CPU, memory, and disk).</span></span> <span data-ttu-id="95271-139">Ao treinar na nuvem, você pode escalar verticalmente seus recursos para atender às demandas do seu cenário, especialmente para grandes conjuntos de altos.</span><span class="sxs-lookup"><span data-stu-id="95271-139">When you train in the cloud, you can scale up your resources to meet the demands of your scenario, especially for large datasets.</span></span>

<span data-ttu-id="95271-140">O treinamento local tem suporte para todos os cenários.</span><span class="sxs-lookup"><span data-stu-id="95271-140">Local training is supported for all scenarios.</span></span>

<span data-ttu-id="95271-141">Há suporte para o treinamento do Azure para classificação de imagem.</span><span class="sxs-lookup"><span data-stu-id="95271-141">Azure training is supported for Image Classification.</span></span>

## <a name="data"></a><span data-ttu-id="95271-142">Dados</span><span class="sxs-lookup"><span data-stu-id="95271-142">Data</span></span>

<span data-ttu-id="95271-143">Depois de escolher seu cenário, o construtor de modelos solicitará que você forneça um conjunto de um.</span><span class="sxs-lookup"><span data-stu-id="95271-143">Once you have chosen your scenario, Model Builder asks you to provide a dataset.</span></span> <span data-ttu-id="95271-144">Os dados são usados para treinar, avaliar e escolher o melhor modelo para seu cenário.</span><span class="sxs-lookup"><span data-stu-id="95271-144">The data is used to train, evaluate, and choose the best model for your scenario.</span></span>

![Diagrama mostrando as etapas do Construtor de Modelos](media/model-builder-steps.png)

<span data-ttu-id="95271-146">O construtor de modelos dá suporte a conjuntos de dados nos formatos. TSV,. csv,. txt, bem como no formato de banco de dados SQL.</span><span class="sxs-lookup"><span data-stu-id="95271-146">Model Builder supports datasets in .tsv, .csv, .txt formats, as well as SQL database format.</span></span> <span data-ttu-id="95271-147">Se você tiver um arquivo. txt, as colunas deverão ser separadas com `,` , `;` ou `/t` e o arquivo deverá ter uma linha de cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="95271-147">If you have a .txt file, columns should be separated with `,`, `;` or `/t` and the file must have a header row.</span></span>

<span data-ttu-id="95271-148">Se o conjunto de ativos for composto de imagens, os tipos de arquivo com suporte serão `.jpg` e `.png` .</span><span class="sxs-lookup"><span data-stu-id="95271-148">If the dataset is made up of images, the supported file types are `.jpg` and `.png`.</span></span>

<span data-ttu-id="95271-149">Para obter mais informações, consulte [carregar dados de treinamento no construtor de modelos](how-to-guides/load-data-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="95271-149">For more information, see [Load training data into Model Builder](how-to-guides/load-data-model-builder.md).</span></span>

### <a name="choose-the-output-to-predict-label"></a><span data-ttu-id="95271-150">Escolha a saída para prever (rótulo)</span><span class="sxs-lookup"><span data-stu-id="95271-150">Choose the output to predict (label)</span></span>

<span data-ttu-id="95271-151">Um conjunto de dados é uma tabela de linhas de exemplos de treinamento e colunas de atributos.</span><span class="sxs-lookup"><span data-stu-id="95271-151">A dataset is a table of rows of training examples, and columns of attributes.</span></span> <span data-ttu-id="95271-152">Cada linha tem:</span><span class="sxs-lookup"><span data-stu-id="95271-152">Each row has:</span></span>

- <span data-ttu-id="95271-153">um **rótulo** (o atributo que você deseja prever)</span><span class="sxs-lookup"><span data-stu-id="95271-153">a **label** (the attribute that you want to predict)</span></span>
- <span data-ttu-id="95271-154">**recursos** (atributos que são usados como entradas para prever o rótulo).</span><span class="sxs-lookup"><span data-stu-id="95271-154">**features** (attributes that are used as inputs to predict the label).</span></span>

<span data-ttu-id="95271-155">Para o cenário de previsão do preço das casas, os recursos podem ser:</span><span class="sxs-lookup"><span data-stu-id="95271-155">For the house-price prediction scenario, the features could be:</span></span>

- <span data-ttu-id="95271-156">os metros quadrados da casa</span><span class="sxs-lookup"><span data-stu-id="95271-156">the square footage of the house</span></span>
- <span data-ttu-id="95271-157">o número de quartos e banheiros</span><span class="sxs-lookup"><span data-stu-id="95271-157">the number of bedrooms and bathrooms</span></span>
- <span data-ttu-id="95271-158">o código postal</span><span class="sxs-lookup"><span data-stu-id="95271-158">the zip code</span></span>

<span data-ttu-id="95271-159">O rótulo é o preço histórico de casas para essa linha de valores de metro quadrado, quarto e banheiro e código postal.</span><span class="sxs-lookup"><span data-stu-id="95271-159">The label is the historical house price for that row of square footage, bedroom, and bathroom values and zip code.</span></span>

![Tabela mostrando linhas e colunas de dados de preços de casas com recursos que consistem em quartos de tamanho de código postal e etiqueta de preço](media/model-builder-data.png)

### <a name="example-datasets"></a><span data-ttu-id="95271-161">Conjuntos de dados de amostra</span><span class="sxs-lookup"><span data-stu-id="95271-161">Example datasets</span></span>

<span data-ttu-id="95271-162">Se você ainda não tiver seus próprios dados, experimente um desses conjuntos de dados:</span><span class="sxs-lookup"><span data-stu-id="95271-162">If you don't have your own data yet, try out one of these datasets:</span></span>

|<span data-ttu-id="95271-163">Cenário</span><span class="sxs-lookup"><span data-stu-id="95271-163">Scenario</span></span>|<span data-ttu-id="95271-164">Exemplo</span><span class="sxs-lookup"><span data-stu-id="95271-164">Example</span></span>|<span data-ttu-id="95271-165">Dados</span><span class="sxs-lookup"><span data-stu-id="95271-165">Data</span></span>|<span data-ttu-id="95271-166">Rotular</span><span class="sxs-lookup"><span data-stu-id="95271-166">Label</span></span>|<span data-ttu-id="95271-167">Recursos</span><span class="sxs-lookup"><span data-stu-id="95271-167">Features</span></span>|
|-|-|-|-|-|
|<span data-ttu-id="95271-168">classificação</span><span class="sxs-lookup"><span data-stu-id="95271-168">Classification</span></span>|<span data-ttu-id="95271-169">Prever anomalias de vendas</span><span class="sxs-lookup"><span data-stu-id="95271-169">Predict sales anomalies</span></span>|[<span data-ttu-id="95271-170">dados de vendas do produto</span><span class="sxs-lookup"><span data-stu-id="95271-170">product sales data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|<span data-ttu-id="95271-171">Vendas do Produto</span><span class="sxs-lookup"><span data-stu-id="95271-171">Product Sales</span></span>|<span data-ttu-id="95271-172">Month</span><span class="sxs-lookup"><span data-stu-id="95271-172">Month</span></span>|
||<span data-ttu-id="95271-173">Prever sentimentos de comentários do site</span><span class="sxs-lookup"><span data-stu-id="95271-173">Predict sentiment of website comments</span></span>|[<span data-ttu-id="95271-174">dados de comentário do site</span><span class="sxs-lookup"><span data-stu-id="95271-174">website comment data</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|<span data-ttu-id="95271-175">Rótulo (0 quando o sentimento é negativo, 1 quando é positivo)</span><span class="sxs-lookup"><span data-stu-id="95271-175">Label (0 when negative sentiment, 1 when positive)</span></span>|<span data-ttu-id="95271-176">Comentário, ano</span><span class="sxs-lookup"><span data-stu-id="95271-176">Comment, Year</span></span>|
||<span data-ttu-id="95271-177">Prever transações de cartão de crédito fraudulentas</span><span class="sxs-lookup"><span data-stu-id="95271-177">Predict fraudulent credit card transactions</span></span>|[<span data-ttu-id="95271-178">dados do cartão de crédito</span><span class="sxs-lookup"><span data-stu-id="95271-178">credit card data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|<span data-ttu-id="95271-179">Classe (1 quando fraudulenta, caso contrário, 0)</span><span class="sxs-lookup"><span data-stu-id="95271-179">Class (1 when fraudulent, 0 otherwise)</span></span>|<span data-ttu-id="95271-180">Quantidade, V1-V28 (recursos anônimos)</span><span class="sxs-lookup"><span data-stu-id="95271-180">Amount, V1-V28 (anonymized features)</span></span>|
||<span data-ttu-id="95271-181">Prever o tipo de problema em um repositório GitHub</span><span class="sxs-lookup"><span data-stu-id="95271-181">Predict the type of issue in a GitHub repository</span></span>|[<span data-ttu-id="95271-182">dados de problema do GitHub</span><span class="sxs-lookup"><span data-stu-id="95271-182">GitHub issue data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|<span data-ttu-id="95271-183">Área</span><span class="sxs-lookup"><span data-stu-id="95271-183">Area</span></span>|<span data-ttu-id="95271-184">Título, Descrição</span><span class="sxs-lookup"><span data-stu-id="95271-184">Title, Description</span></span>|
|<span data-ttu-id="95271-185">Previsão de valor</span><span class="sxs-lookup"><span data-stu-id="95271-185">Value prediction</span></span>|<span data-ttu-id="95271-186">Preço de Tarifa de táxi</span><span class="sxs-lookup"><span data-stu-id="95271-186">Predict taxi fare price</span></span>|[<span data-ttu-id="95271-187">dados de tarifas de táxi</span><span class="sxs-lookup"><span data-stu-id="95271-187">taxi fare data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|<span data-ttu-id="95271-188">Tarifa</span><span class="sxs-lookup"><span data-stu-id="95271-188">Fare</span></span>|<span data-ttu-id="95271-189">Tempo da corrida, distância</span><span class="sxs-lookup"><span data-stu-id="95271-189">Trip time, distance</span></span>|
|<span data-ttu-id="95271-190">Classificação de imagens</span><span class="sxs-lookup"><span data-stu-id="95271-190">Image classification</span></span>|<span data-ttu-id="95271-191">Prever a categoria de uma flor</span><span class="sxs-lookup"><span data-stu-id="95271-191">Predict the category of a flower</span></span> |[<span data-ttu-id="95271-192">imagens flor</span><span class="sxs-lookup"><span data-stu-id="95271-192">flower images</span></span>](http://download.tensorflow.org/example_images/flower_photos.tgz)|<span data-ttu-id="95271-193">O tipo de flor: Margarida, dandelion, rosas, flores, tulips</span><span class="sxs-lookup"><span data-stu-id="95271-193">The type of flower: daisy, dandelion, roses, sunflowers, tulips</span></span>|<span data-ttu-id="95271-194">Os próprios dados da imagem</span><span class="sxs-lookup"><span data-stu-id="95271-194">The image data itself</span></span>|
|<span data-ttu-id="95271-195">Recomendação</span><span class="sxs-lookup"><span data-stu-id="95271-195">Recommendation</span></span>|<span data-ttu-id="95271-196">Prever filmes que alguém gostará</span><span class="sxs-lookup"><span data-stu-id="95271-196">Predict movies that someone will like</span></span>|[<span data-ttu-id="95271-197">classificações de filme</span><span class="sxs-lookup"><span data-stu-id="95271-197">movie ratings</span></span>](http://files.grouplens.org/datasets/movielens/ml-latest-small.zip)|<span data-ttu-id="95271-198">Usuários, filmes</span><span class="sxs-lookup"><span data-stu-id="95271-198">Users, Movies</span></span>|<span data-ttu-id="95271-199">Classificações</span><span class="sxs-lookup"><span data-stu-id="95271-199">Ratings</span></span>|

## <a name="train"></a><span data-ttu-id="95271-200">Treinar</span><span class="sxs-lookup"><span data-stu-id="95271-200">Train</span></span>

<span data-ttu-id="95271-201">Depois de selecionar o cenário, o ambiente, os dados e o rótulo, o construtor de modelos treina o modelo.</span><span class="sxs-lookup"><span data-stu-id="95271-201">Once you select your scenario, environment, data, and label, Model Builder trains the model.</span></span>

### <a name="what-is-training"></a><span data-ttu-id="95271-202">O que é o treinamento?</span><span class="sxs-lookup"><span data-stu-id="95271-202">What is training?</span></span>

<span data-ttu-id="95271-203">O treinamento é um processo automático pelo qual Construtor de Modelo ensina seu modelo a responder perguntas para seu cenário.</span><span class="sxs-lookup"><span data-stu-id="95271-203">Training is an automatic process by which Model Builder teaches your model how to answer questions for your scenario.</span></span> <span data-ttu-id="95271-204">Depois de treinado, seu modelo pode fazer previsões com dados de entrada não vistos antes.</span><span class="sxs-lookup"><span data-stu-id="95271-204">Once trained, your model can make predictions with input data that it has not seen before.</span></span> <span data-ttu-id="95271-205">Por exemplo, se estiver prevendo preços de casas e uma nova casa for oferecida no mercado, você poderá prever o preço de venda.</span><span class="sxs-lookup"><span data-stu-id="95271-205">For example, if you are predicting house prices and a new house comes on the market, you can predict its sale price.</span></span>

<span data-ttu-id="95271-206">Como o Construtor de Modelo usa aprendizado de máquina automatizado (AutoML), ele não requer nenhuma entrada ou ajuste de você durante o treinamento.</span><span class="sxs-lookup"><span data-stu-id="95271-206">Because Model Builder uses automated machine learning (AutoML), it does not require any input or tuning from you during training.</span></span>

### <a name="how-long-should-i-train-for"></a><span data-ttu-id="95271-207">Por quanto tempo devo treinar?</span><span class="sxs-lookup"><span data-stu-id="95271-207">How long should I train for?</span></span>

<span data-ttu-id="95271-208">O construtor de modelos usa AutoML para explorar vários modelos para encontrar o modelo de melhor desempenho.</span><span class="sxs-lookup"><span data-stu-id="95271-208">Model Builder uses AutoML to explore multiple models to find you the best performing model.</span></span>

<span data-ttu-id="95271-209">Períodos de treinamento mais longos permitem que o AutoML Explore mais modelos com uma ampla gama de configurações.</span><span class="sxs-lookup"><span data-stu-id="95271-209">Longer training periods allow AutoML to explore more models with a wider range of settings.</span></span>

<span data-ttu-id="95271-210">A tabela a seguir resume o tempo médio necessário para obter um bom desempenho para um conjunto de conjuntos de data de exemplo, em um computador local.</span><span class="sxs-lookup"><span data-stu-id="95271-210">The table below summarizes the average time taken to get good performance for a suite of example datasets, on a local machine.</span></span>

|<span data-ttu-id="95271-211">Tamanho do conjunto de um</span><span class="sxs-lookup"><span data-stu-id="95271-211">Dataset size</span></span>|<span data-ttu-id="95271-212">Tempo médio para treinar</span><span class="sxs-lookup"><span data-stu-id="95271-212">Average time to train</span></span>|
|------------|---------------------|
|<span data-ttu-id="95271-213">0-10 MB</span><span class="sxs-lookup"><span data-stu-id="95271-213">0 - 10 MB</span></span>|<span data-ttu-id="95271-214">10 s</span><span class="sxs-lookup"><span data-stu-id="95271-214">10 sec</span></span>|
|<span data-ttu-id="95271-215">10-100 MB</span><span class="sxs-lookup"><span data-stu-id="95271-215">10 - 100 MB</span></span>|<span data-ttu-id="95271-216">10 min</span><span class="sxs-lookup"><span data-stu-id="95271-216">10 min</span></span>|
|<span data-ttu-id="95271-217">100-500 MB</span><span class="sxs-lookup"><span data-stu-id="95271-217">100 - 500 MB</span></span>|<span data-ttu-id="95271-218">30 min</span><span class="sxs-lookup"><span data-stu-id="95271-218">30 min</span></span>|
|<span data-ttu-id="95271-219">500-1 GB</span><span class="sxs-lookup"><span data-stu-id="95271-219">500 - 1 GB</span></span>|<span data-ttu-id="95271-220">60 min</span><span class="sxs-lookup"><span data-stu-id="95271-220">60 min</span></span>|
|<span data-ttu-id="95271-221">1 GB +</span><span class="sxs-lookup"><span data-stu-id="95271-221">1 GB+</span></span>|<span data-ttu-id="95271-222">mais de 3 horas</span><span class="sxs-lookup"><span data-stu-id="95271-222">3+ hours</span></span>|

<span data-ttu-id="95271-223">Esses números são apenas um guia.</span><span class="sxs-lookup"><span data-stu-id="95271-223">These numbers are a guide only.</span></span> <span data-ttu-id="95271-224">O tamanho exato do treinamento depende de:</span><span class="sxs-lookup"><span data-stu-id="95271-224">The exact length of training is dependent on:</span></span>

- <span data-ttu-id="95271-225">o número de recursos (colunas) que estão sendo usados como entrada para o modelo</span><span class="sxs-lookup"><span data-stu-id="95271-225">the number of features (columns) being used to as input to the model</span></span>
- <span data-ttu-id="95271-226">o tipo de colunas</span><span class="sxs-lookup"><span data-stu-id="95271-226">the type of columns</span></span>
- <span data-ttu-id="95271-227">a tarefa ML</span><span class="sxs-lookup"><span data-stu-id="95271-227">the ML task</span></span>
- <span data-ttu-id="95271-228">o desempenho de CPU, disco e memória do computador usado para treinamento</span><span class="sxs-lookup"><span data-stu-id="95271-228">the CPU, disk, and memory performance of the machine used for training</span></span>

<span data-ttu-id="95271-229">Geralmente, é recomendável que você use mais de 100 linhas como conjuntos de valores com menos de que isso pode não produzir resultados e pode levar um tempo significativamente maior para treinar.</span><span class="sxs-lookup"><span data-stu-id="95271-229">It's generally advised that you use more than 100 rows as datasets with less than that may not produce any results and may take a significantly longer time to train.</span></span>

## <a name="evaluate"></a><span data-ttu-id="95271-230">Avaliar</span><span class="sxs-lookup"><span data-stu-id="95271-230">Evaluate</span></span>

<span data-ttu-id="95271-231">A avaliação é o processo de medir a qualidade do seu modelo.</span><span class="sxs-lookup"><span data-stu-id="95271-231">Evaluation is the process of measuring how good your model is.</span></span> <span data-ttu-id="95271-232">O construtor de modelos usa o modelo treinado para fazer previsões com novos dados de teste e, em seguida, mede a qualidade das previsões.</span><span class="sxs-lookup"><span data-stu-id="95271-232">Model Builder uses the trained model to make predictions with new test data, and then measures how good the predictions are.</span></span>

<span data-ttu-id="95271-233">O Construtor de Modelo divide os dados de treinamento em um conjunto de treinamento e um conjunto de teste.</span><span class="sxs-lookup"><span data-stu-id="95271-233">Model Builder splits the training data into a training set and a test set.</span></span> <span data-ttu-id="95271-234">Os dados de treinamento (80%) são usados para treinar seu modelo e os dados de teste (20%) são retidos para avaliar seu modelo.</span><span class="sxs-lookup"><span data-stu-id="95271-234">The training data (80%) is used to train your model and the test data (20%) is held back to evaluate your model.</span></span>

### <a name="how-do-i-understand-my-model-performance"></a><span data-ttu-id="95271-235">Como fazer entender o desempenho do meu modelo?</span><span class="sxs-lookup"><span data-stu-id="95271-235">How do I understand my model performance?</span></span>

<span data-ttu-id="95271-236">Um cenário é mapeado para uma tarefa de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="95271-236">A scenario maps to a machine learning task.</span></span> <span data-ttu-id="95271-237">Cada tarefa ML tem seu próprio conjunto de métricas de avaliação.</span><span class="sxs-lookup"><span data-stu-id="95271-237">Each ML task has its own set of evaluation metrics.</span></span>

#### <a name="value-prediction"></a><span data-ttu-id="95271-238">Previsão de valor</span><span class="sxs-lookup"><span data-stu-id="95271-238">Value prediction</span></span>

<span data-ttu-id="95271-239">A métrica padrão para problemas de previsão de valor é RSquared, o valor de RSquared intervalos entre 0 e 1.</span><span class="sxs-lookup"><span data-stu-id="95271-239">The default metric for value prediction problems is RSquared, the value of RSquared ranges between 0 and 1.</span></span> <span data-ttu-id="95271-240">1 é o melhor valor possível ou, em outras palavras, quanto mais perto o valor de RSquared para 1 melhor o seu modelo está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="95271-240">1 is the best possible value or in other words the closer the value of RSquared to 1 the better your model is performing.</span></span>

<span data-ttu-id="95271-241">Outras métricas relatadas como perda absoluta, perda de quadrado e perda de RMS são métricas adicionais, que podem ser usadas para entender como o modelo está sendo executado e compará-lo com outros modelos de previsão de valor.</span><span class="sxs-lookup"><span data-stu-id="95271-241">Other metrics reported such as absolute-loss, squared-loss, and RMS loss are additional metrics, which can be used to understand how your model is performing and comparing it against other value prediction models.</span></span>

#### <a name="classification-2-categories"></a><span data-ttu-id="95271-242">Classificação (2 categorias)</span><span class="sxs-lookup"><span data-stu-id="95271-242">Classification (2 categories)</span></span>

<span data-ttu-id="95271-243">A métrica padrão para problemas de classificação é a precisão.</span><span class="sxs-lookup"><span data-stu-id="95271-243">The default metric for classification problems is accuracy.</span></span> <span data-ttu-id="95271-244">A precisão define a proporção de previsões corretas que seu modelo está fazendo sobre o conjunto de testes.</span><span class="sxs-lookup"><span data-stu-id="95271-244">Accuracy defines the proportion of correct predictions your model is making over the test dataset.</span></span> <span data-ttu-id="95271-245">Quanto mais perto de 100% ou 1,0, melhor será.</span><span class="sxs-lookup"><span data-stu-id="95271-245">The closer to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="95271-246">Outras métricas relatadas como AUC (área sob a curva), que mede a taxa positiva real versus a taxa de falsos positivos deve ser maior que 0,50 para que os modelos sejam aceitáveis.</span><span class="sxs-lookup"><span data-stu-id="95271-246">Other metrics reported such as AUC (Area under the curve), which measures the true positive rate vs. the false positive rate should be greater than 0.50 for models to be acceptable.</span></span>

<span data-ttu-id="95271-247">Métricas adicionais, como a pontuação F1, podem ser usadas para controlar o equilíbrio entre precisão e RECALL.</span><span class="sxs-lookup"><span data-stu-id="95271-247">Additional metrics like F1 score can be used to control the balance between Precision and Recall.</span></span>

#### <a name="classification-3-categories"></a><span data-ttu-id="95271-248">Classificação (3 + categorias)</span><span class="sxs-lookup"><span data-stu-id="95271-248">Classification (3+ categories)</span></span>

<span data-ttu-id="95271-249">A métrica padrão para classificação de várias classes é micro exatidão.</span><span class="sxs-lookup"><span data-stu-id="95271-249">The default metric for Multi-class classification is Micro Accuracy.</span></span> <span data-ttu-id="95271-250">Quanto mais próximo for a 100% ou 1,0, melhor será.</span><span class="sxs-lookup"><span data-stu-id="95271-250">The closer the Micro Accuracy to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="95271-251">Outra métrica importante para a classificação de várias classes é a precisão da macro, semelhante à superprecisão mais próxima de 1,0 a melhor delas.</span><span class="sxs-lookup"><span data-stu-id="95271-251">Another important metric for Multi-class classification is Macro-accuracy, similar to Micro-accuracy the closer to 1.0 the better it is.</span></span> <span data-ttu-id="95271-252">Uma boa maneira de pensar sobre esses dois tipos de precisão é:</span><span class="sxs-lookup"><span data-stu-id="95271-252">A good way to think about these two types of accuracy is:</span></span>

- <span data-ttu-id="95271-253">Micro-exatidão: com que frequência um tíquete de entrada é classificado para a equipe certa?</span><span class="sxs-lookup"><span data-stu-id="95271-253">Micro-accuracy: How often does an incoming ticket get classified to the right team?</span></span>
- <span data-ttu-id="95271-254">Precisão da macro: para uma equipe média, com que frequência um tíquete de entrada é correto para sua equipe?</span><span class="sxs-lookup"><span data-stu-id="95271-254">Macro-accuracy: For an average team, how often is an incoming ticket correct for their team?</span></span>

### <a name="more-information-on-evaluation-metrics"></a><span data-ttu-id="95271-255">Mais informações sobre métricas de avaliação</span><span class="sxs-lookup"><span data-stu-id="95271-255">More information on evaluation metrics</span></span>

<span data-ttu-id="95271-256">Para obter mais informações, consulte [métricas de avaliação de modelo](resources/metrics.md).</span><span class="sxs-lookup"><span data-stu-id="95271-256">For more information, see [model evaluation metrics](resources/metrics.md).</span></span>

## <a name="improve"></a><span data-ttu-id="95271-257">Aprimorar</span><span class="sxs-lookup"><span data-stu-id="95271-257">Improve</span></span>

<span data-ttu-id="95271-258">Se a sua pontuação de desempenho do modelo não for tão boa quanto deseja, você poderá:</span><span class="sxs-lookup"><span data-stu-id="95271-258">If your model performance score is not as good as you want it to be, you can:</span></span>

- <span data-ttu-id="95271-259">Treinar por um período maior de tempo.</span><span class="sxs-lookup"><span data-stu-id="95271-259">Train for a longer period of time.</span></span> <span data-ttu-id="95271-260">Com mais tempo, o mecanismo de aprendizado de máquina automatizado experimenta mais algoritmos e configurações.</span><span class="sxs-lookup"><span data-stu-id="95271-260">With more time, the automated machine learning engine experiments with more algorithms and settings.</span></span>

- <span data-ttu-id="95271-261">Adicionar mais dados.</span><span class="sxs-lookup"><span data-stu-id="95271-261">Add more data.</span></span> <span data-ttu-id="95271-262">Às vezes, a quantidade de dados não é suficiente para treinar um modelo de aprendizado de máquina de alta qualidade. Isso é especialmente verdadeiro com conjuntos de valores que têm um pequeno número de exemplos.</span><span class="sxs-lookup"><span data-stu-id="95271-262">Sometimes the amount of data is not sufficient to train a high-quality machine learning model.This is especially true with datasets that have a small number of examples.</span></span>

- <span data-ttu-id="95271-263">Balancear seus dados.</span><span class="sxs-lookup"><span data-stu-id="95271-263">Balance your data.</span></span> <span data-ttu-id="95271-264">Para tarefas de classificação, certifique-se de que o conjunto de treinamento esteja equilibrado nas categorias.</span><span class="sxs-lookup"><span data-stu-id="95271-264">For classification tasks, make sure that the training set is balanced across the categories.</span></span> <span data-ttu-id="95271-265">Por exemplo, se você tiver quatro classes para 100 exemplos de treinamento e as duas primeiras classes (tag1 e tag2) forem usadas para 90 registros, mas as outras duas (tag3 e tag4) forem usadas apenas nos 10 registros restantes, a falta de dados balanceados poderá fazer com que seu modelo tenha dificuldades para prever corretamente o tag3 ou o tag4.</span><span class="sxs-lookup"><span data-stu-id="95271-265">For example, if you have four classes for 100 training examples, and the two first classes (tag1 and tag2) are used for 90 records, but the other two (tag3 and tag4) are only used on the remaining 10 records, the lack of balanced data may cause your model to struggle to correctly predict tag3 or tag4.</span></span>

## <a name="code"></a><span data-ttu-id="95271-266">Código</span><span class="sxs-lookup"><span data-stu-id="95271-266">Code</span></span>

<span data-ttu-id="95271-267">Após a fase de avaliação, o Construtor de Modelo gera um arquivo de modelo e o código que você pode usar para adicionar o modelo ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="95271-267">After the evaluation phase, Model Builder outputs a model file, and code that you can use to add the model to your application.</span></span> <span data-ttu-id="95271-268">Modelos do ML.NET são salvos como um arquivo zip.</span><span class="sxs-lookup"><span data-stu-id="95271-268">ML.NET models are saved as a zip file.</span></span> <span data-ttu-id="95271-269">O código para carregar e usar o modelo é adicionado como um novo projeto em sua solução.</span><span class="sxs-lookup"><span data-stu-id="95271-269">The code to load and use your model is added as a new project in your solution.</span></span> <span data-ttu-id="95271-270">O Construtor de Modelo também adiciona um aplicativo de console de exemplo que você pode executar para ver seu modelo em ação.</span><span class="sxs-lookup"><span data-stu-id="95271-270">Model Builder also adds a sample console app that you can run to see your model in action.</span></span>

<span data-ttu-id="95271-271">Além disso, o Construtor de Modelo cria o código que gerou o modelo para que você possa entender as etapas usadas na geração do modelo.</span><span class="sxs-lookup"><span data-stu-id="95271-271">In addition, Model Builder outputs the code that generated the model, so that you can understand the steps used to generate the model.</span></span> <span data-ttu-id="95271-272">Você também pode usar o código de treinamento do modelo para treinar novamente seu modelo com novos dados.</span><span class="sxs-lookup"><span data-stu-id="95271-272">You can also use the model training code to retrain your model with new data.</span></span>

## <a name="whats-next"></a><span data-ttu-id="95271-273">O que vem a seguir?</span><span class="sxs-lookup"><span data-stu-id="95271-273">What's next?</span></span>

<span data-ttu-id="95271-274">[Instalar](how-to-guides/install-model-builder.md) a extensão do Visual Studio do Construtor de Modelos</span><span class="sxs-lookup"><span data-stu-id="95271-274">[Install](how-to-guides/install-model-builder.md) the Model Builder Visual Studio extension</span></span>

<span data-ttu-id="95271-275">Experimente a [previsão de preço ou qualquer cenário de regressão](tutorials/predict-prices-with-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="95271-275">Try [price prediction or any regression scenario](tutorials/predict-prices-with-model-builder.md)</span></span>
