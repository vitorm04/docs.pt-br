---
title: 'Tutorial: Analisar o sentimentos das revisões de filmes usando um modelo de TensorFlow pré-treinado'
description: Este tutorial mostra como usar um modelo de TensorFlow pré-treinado para classificar as opiniões nos comentários do site. O classificador de sentimentos binário C# é um aplicativo de console desenvolvido usando o Visual Studio.
ms.date: 09/11/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: nakersha
author: natke
ms.openlocfilehash: 2dd10c0843b2bea4755d5f4f0aceea6509c7cf46
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054303"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a><span data-ttu-id="d709b-104">Tutorial: Analise as opiniões das revisões de filmes usando um modelo de TensorFlow pré-treinado no ML.NET</span><span class="sxs-lookup"><span data-stu-id="d709b-104">Tutorial: Analyze sentiment of movie reviews using a pre-trained TensorFlow model in ML.NET</span></span>

<span data-ttu-id="d709b-105">Este tutorial mostra como usar um modelo de TensorFlow pré-treinado para classificar as opiniões nos comentários do site.</span><span class="sxs-lookup"><span data-stu-id="d709b-105">This tutorial shows you how to use a pre-trained TensorFlow model to classify sentiment in website comments.</span></span> <span data-ttu-id="d709b-106">O classificador de sentimentos binário C# é um aplicativo de console desenvolvido usando o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d709b-106">The binary sentiment classifier is a C# console application developed using Visual Studio.</span></span>

<span data-ttu-id="d709b-107">O modelo TensorFlow usado neste tutorial foi treinado usando revisões de filme do banco de dados do IMDB.</span><span class="sxs-lookup"><span data-stu-id="d709b-107">The TensorFlow model used in this tutorial was trained using movie reviews from the IMDB database.</span></span> <span data-ttu-id="d709b-108">Depois de concluir o desenvolvimento do aplicativo, você poderá fornecer o texto de revisão do filme e o aplicativo informará se a revisão tem uma opinião positiva ou negativa.</span><span class="sxs-lookup"><span data-stu-id="d709b-108">Once you have finished developing the application, you will be able to supply movie review text and the application will tell you whether the review has positive or negative sentiment.</span></span>

<span data-ttu-id="d709b-109">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="d709b-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="d709b-110">Carregar um modelo de TensorFlow pré-treinado</span><span class="sxs-lookup"><span data-stu-id="d709b-110">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="d709b-111">Transformar o texto de comentário do site em recursos adequados para o modelo</span><span class="sxs-lookup"><span data-stu-id="d709b-111">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="d709b-112">Usar o modelo para fazer uma previsão</span><span class="sxs-lookup"><span data-stu-id="d709b-112">Use the model to make a prediction</span></span>

<span data-ttu-id="d709b-113">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF).</span><span class="sxs-lookup"><span data-stu-id="d709b-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d709b-114">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d709b-114">Prerequisites</span></span>

* <span data-ttu-id="d709b-115">[Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="d709b-115">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="setup"></a><span data-ttu-id="d709b-116">Configuração</span><span class="sxs-lookup"><span data-stu-id="d709b-116">Setup</span></span>

### <a name="create-the-application"></a><span data-ttu-id="d709b-117">Criar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="d709b-117">Create the application</span></span>

1. <span data-ttu-id="d709b-118">Crie um **aplicativo de console do .NET Core** chamado "TextClassificationTF".</span><span class="sxs-lookup"><span data-stu-id="d709b-118">Create a **.NET Core Console Application** called "TextClassificationTF".</span></span>

2. <span data-ttu-id="d709b-119">Crie um diretório chamado *Data* no seu projeto para salvar os arquivos do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="d709b-119">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="d709b-120">Instalar o **Pacote NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="d709b-120">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="d709b-121">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="d709b-121">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="d709b-122">Escolha "nuget.org" como a fonte do pacote e, em seguida, selecione a guia **Procurar**. Pesquise **Microsoft.ML**, selecione o pacote que você deseja e, em seguida, selecione o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="d709b-122">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="d709b-123">Prossiga com a instalação concordando com os termos de licença do pacote que você escolher.</span><span class="sxs-lookup"><span data-stu-id="d709b-123">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="d709b-124">Repita essas etapas para **Microsoft. ml. TensorFlow**.</span><span class="sxs-lookup"><span data-stu-id="d709b-124">Repeat these steps for **Microsoft.ML.TensorFlow**.</span></span>

### <a name="add-the-tensorflow-model-to-the-project"></a><span data-ttu-id="d709b-125">Adicionar o modelo TensorFlow ao projeto</span><span class="sxs-lookup"><span data-stu-id="d709b-125">Add the TensorFlow model to the project</span></span>

> [!NOTE]
> <span data-ttu-id="d709b-126">O modelo para este tutorial é do repositório GitHub [dotnet/MachineLearning-TestData](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) .</span><span class="sxs-lookup"><span data-stu-id="d709b-126">The model for this tutorial is from the [dotnet/machinelearning-testdata](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) GitHub repo.</span></span> <span data-ttu-id="d709b-127">O modelo está no formato TensorFlow SavedModel.</span><span class="sxs-lookup"><span data-stu-id="d709b-127">The model is in TensorFlow SavedModel format.</span></span>

1. <span data-ttu-id="d709b-128">Baixe o [arquivo zip sentiment_model](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true)e descompacte.</span><span class="sxs-lookup"><span data-stu-id="d709b-128">Download the [sentiment_model zip file](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true), and unzip.</span></span>

    <span data-ttu-id="d709b-129">O arquivo zip contém:</span><span class="sxs-lookup"><span data-stu-id="d709b-129">The zip file contains:</span></span>

    * <span data-ttu-id="d709b-130">`saved_model.pb`: o próprio modelo de TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="d709b-130">`saved_model.pb`: the TensorFlow model itself.</span></span> <span data-ttu-id="d709b-131">O modelo usa uma matriz de inteiros de tamanho fixo (tamanho 600) de recursos que representam o texto em uma cadeia de caracteres de revisão do IMDB e gera duas probabilidades que somam 1: a probabilidade de que a revisão de entrada tenha uma opinião positiva e a probabilidade de que a revisão de entrada tenha sentimentos negativo.</span><span class="sxs-lookup"><span data-stu-id="d709b-131">The model takes a fixed length (size 600) integer array of features representing the text in an IMDB review string, and outputs two probabilities which sum to 1: the probability that the input review has positive sentiment, and the probability that the input review has negative sentiment.</span></span>
    * <span data-ttu-id="d709b-132">`imdb_word_index.csv`: um mapeamento de palavras individuais para um valor inteiro.</span><span class="sxs-lookup"><span data-stu-id="d709b-132">`imdb_word_index.csv`: a mapping from individual words to an integer value.</span></span> <span data-ttu-id="d709b-133">O mapeamento é usado para gerar os recursos de entrada para o modelo TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="d709b-133">The mapping is used to generate the input features for the TensorFlow model.</span></span>

2. <span data-ttu-id="d709b-134">Copie o conteúdo do diretório mais `sentiment_model` interno em seu diretório de `sentiment_model` projeto do *TextClassificationTF* .</span><span class="sxs-lookup"><span data-stu-id="d709b-134">Copy the contents of the innermost `sentiment_model` directory into your *TextClassificationTF* project `sentiment_model` directory.</span></span> <span data-ttu-id="d709b-135">Este diretório contém o modelo e os arquivos de suporte adicionais necessários para este tutorial, conforme mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="d709b-135">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![conteúdo do diretório sentiment_model](./media/text-classification-tf/sentiment-model-files.png)

3. <span data-ttu-id="d709b-137">Em Gerenciador de soluções, clique com o botão direito do mouse em cada `sentiment_model` um dos arquivos no diretório e no subdiretório e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="d709b-137">In Solution Explorer, right-click each of the files in the `sentiment_model` directory and subdirectory and select **Properties**.</span></span> <span data-ttu-id="d709b-138">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.</span><span class="sxs-lookup"><span data-stu-id="d709b-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="add-using-statements-and-global-variables"></a><span data-ttu-id="d709b-139">Adicionar instruções using e variáveis globais</span><span class="sxs-lookup"><span data-stu-id="d709b-139">Add using statements and global variables</span></span>

1. <span data-ttu-id="d709b-140">Adicione as seguintes instruções `using` adicionais ao início do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="d709b-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TextClassificationTF/Program.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="d709b-141">Crie duas variáveis globais logo acima do `Main` método para manter o caminho do arquivo de modelo salvo e o comprimento do vetor de recurso.</span><span class="sxs-lookup"><span data-stu-id="d709b-141">Create two global variables right above the `Main` method to hold the saved model file path, and the feature vector length.</span></span>

   [!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TextClassificationTF/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * <span data-ttu-id="d709b-142">`_modelPath`é o caminho do arquivo do modelo treinado.</span><span class="sxs-lookup"><span data-stu-id="d709b-142">`_modelPath` is the file path of the trained model.</span></span>
    * <span data-ttu-id="d709b-143">`FeatureLength`é o comprimento da matriz de recursos de inteiro que o modelo espera.</span><span class="sxs-lookup"><span data-stu-id="d709b-143">`FeatureLength` is the length of the integer feature array that the model is expecting.</span></span>

### <a name="model-the-data"></a><span data-ttu-id="d709b-144">Modelar os dados</span><span class="sxs-lookup"><span data-stu-id="d709b-144">Model the data</span></span>

<span data-ttu-id="d709b-145">As revisões de filme são texto de forma livre.</span><span class="sxs-lookup"><span data-stu-id="d709b-145">Movie reviews are free form text.</span></span> <span data-ttu-id="d709b-146">Seu aplicativo converte o texto no formato de entrada esperado pelo modelo em uma série de estágios discretos.</span><span class="sxs-lookup"><span data-stu-id="d709b-146">Your application converts the text into the input format expected by the model in a number of discrete stages.</span></span>

<span data-ttu-id="d709b-147">A primeira é dividir o texto em palavras separadas e usar o arquivo de mapeamento fornecido para mapear cada palavra em uma codificação de número inteiro.</span><span class="sxs-lookup"><span data-stu-id="d709b-147">The first is to split the text into separate words and use the provided mapping file to map each word onto an integer encoding.</span></span> <span data-ttu-id="d709b-148">O resultado dessa transformação é uma matriz de inteiro de comprimento variável com um comprimento correspondente ao número de palavras na sentença.</span><span class="sxs-lookup"><span data-stu-id="d709b-148">The result of this transformation is a variable length integer array with a length corresponding to the number of words in the sentence.</span></span>

|<span data-ttu-id="d709b-149">Propriedade</span><span class="sxs-lookup"><span data-stu-id="d709b-149">Property</span></span>| <span data-ttu-id="d709b-150">Valor</span><span class="sxs-lookup"><span data-stu-id="d709b-150">Value</span></span>|<span data-ttu-id="d709b-151">Tipo</span><span class="sxs-lookup"><span data-stu-id="d709b-151">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="d709b-152">ReviewText</span><span class="sxs-lookup"><span data-stu-id="d709b-152">ReviewText</span></span>|<span data-ttu-id="d709b-153">Esse filme é realmente bom</span><span class="sxs-lookup"><span data-stu-id="d709b-153">this film is really good</span></span>|<span data-ttu-id="d709b-154">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="d709b-154">string</span></span>|
|<span data-ttu-id="d709b-155">VariableLengthFeatures</span><span class="sxs-lookup"><span data-stu-id="d709b-155">VariableLengthFeatures</span></span>|<span data-ttu-id="d709b-156">14, 22, 9, 66, 78,...</span><span class="sxs-lookup"><span data-stu-id="d709b-156">14,22,9,66,78,...</span></span> |<span data-ttu-id="d709b-157">int []</span><span class="sxs-lookup"><span data-stu-id="d709b-157">int[]</span></span>|

<span data-ttu-id="d709b-158">Em seguida, a matriz de recursos de comprimento variável é redimensionada para um comprimento fixo de 600.</span><span class="sxs-lookup"><span data-stu-id="d709b-158">The variable length feature array is then resized to a fixed length of 600.</span></span> <span data-ttu-id="d709b-159">Esse é o comprimento esperado pelo modelo TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="d709b-159">This is the length that the TensorFlow model expects.</span></span>

|<span data-ttu-id="d709b-160">Propriedade</span><span class="sxs-lookup"><span data-stu-id="d709b-160">Property</span></span>| <span data-ttu-id="d709b-161">Valor</span><span class="sxs-lookup"><span data-stu-id="d709b-161">Value</span></span>|<span data-ttu-id="d709b-162">Tipo</span><span class="sxs-lookup"><span data-stu-id="d709b-162">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="d709b-163">ReviewText</span><span class="sxs-lookup"><span data-stu-id="d709b-163">ReviewText</span></span>|<span data-ttu-id="d709b-164">Esse filme é realmente bom</span><span class="sxs-lookup"><span data-stu-id="d709b-164">this film is really good</span></span>|<span data-ttu-id="d709b-165">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="d709b-165">string</span></span>|
|<span data-ttu-id="d709b-166">VariableLengthFeatures</span><span class="sxs-lookup"><span data-stu-id="d709b-166">VariableLengthFeatures</span></span>|<span data-ttu-id="d709b-167">14, 22, 9, 66, 78,...</span><span class="sxs-lookup"><span data-stu-id="d709b-167">14,22,9,66,78,...</span></span> |<span data-ttu-id="d709b-168">int []</span><span class="sxs-lookup"><span data-stu-id="d709b-168">int[]</span></span>|
|<span data-ttu-id="d709b-169">Recursos</span><span class="sxs-lookup"><span data-stu-id="d709b-169">Features</span></span>|<span data-ttu-id="d709b-170">14, 22, 9, 66, 78,...</span><span class="sxs-lookup"><span data-stu-id="d709b-170">14,22,9,66,78,...</span></span> |<span data-ttu-id="d709b-171">int [600]</span><span class="sxs-lookup"><span data-stu-id="d709b-171">int[600]</span></span>|

1. <span data-ttu-id="d709b-172">Crie uma classe para os dados de entrada, após `Main` o método:</span><span class="sxs-lookup"><span data-stu-id="d709b-172">Create a class for your input data, after the `Main` method:</span></span>

    [!code-csharp[MovieReviewClass](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#MovieReviewClass "Declare movie review type")]

    <span data-ttu-id="d709b-173">A classe de dados de `MovieReview`entrada,, `string` tem um para comentários`ReviewText`do usuário ().</span><span class="sxs-lookup"><span data-stu-id="d709b-173">The input data class, `MovieReview`, has a `string` for user comments (`ReviewText`).</span></span>

1. <span data-ttu-id="d709b-174">Crie uma classe para os recursos de comprimento variável, após `Main` o método:</span><span class="sxs-lookup"><span data-stu-id="d709b-174">Create a class for the variable length features, after the `Main` method:</span></span>

    [!code-csharp[VariableLengthFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    <span data-ttu-id="d709b-175">A `VariableLengthFeatures` propriedade tem um atributo [vectortype](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) para designá-lo como um vetor.</span><span class="sxs-lookup"><span data-stu-id="d709b-175">The `VariableLengthFeatures` property has a [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) attribute to designate it as a vector.</span></span>  <span data-ttu-id="d709b-176">Todos os elementos de vetor devem ser do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="d709b-176">All of the vector elements must be the same type.</span></span> <span data-ttu-id="d709b-177">Em conjuntos de dados com um grande número de colunas, carregar várias colunas como um único vetor reduz o número de passagens de dados quando você aplica transformações de dados.</span><span class="sxs-lookup"><span data-stu-id="d709b-177">In data sets with a large number of columns, loading multiple columns as a single vector reduces the number of data passes when you apply data transformations.</span></span>

    <span data-ttu-id="d709b-178">Essa classe é usada na `ResizeFeatures` ação.</span><span class="sxs-lookup"><span data-stu-id="d709b-178">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="d709b-179">Os nomes de suas propriedades (neste caso, apenas um) são usados para indicar quais colunas no DataView podem ser usadas como _entrada_ para a ação de mapeamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="d709b-179">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _input_ to the custom mapping action.</span></span>

1. <span data-ttu-id="d709b-180">Crie uma classe para os recursos de comprimento fixo, após `Main` o método:</span><span class="sxs-lookup"><span data-stu-id="d709b-180">Create a class for the fixed length features, after the `Main` method:</span></span>

    [!code-csharp[FixedLengthFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#FixedLengthFeatures)]

    <span data-ttu-id="d709b-181">Essa classe é usada na `ResizeFeatures` ação.</span><span class="sxs-lookup"><span data-stu-id="d709b-181">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="d709b-182">Os nomes de suas propriedades (neste caso, apenas um) são usados para indicar quais colunas no DataView podem ser usadas como a _saída_ da ação de mapeamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="d709b-182">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _output_ of the custom mapping action.</span></span>

    <span data-ttu-id="d709b-183">Observe que o nome da propriedade `Features` é determinado pelo modelo TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="d709b-183">Note that the name of the property `Features` is determined by the TensorFlow model.</span></span> <span data-ttu-id="d709b-184">Você não pode alterar esse nome de propriedade.</span><span class="sxs-lookup"><span data-stu-id="d709b-184">You cannot change this property name.</span></span>

1. <span data-ttu-id="d709b-185">Crie uma classe para a previsão após o `Main` método:</span><span class="sxs-lookup"><span data-stu-id="d709b-185">Create a class for the prediction after the `Main` method:</span></span>

    [!code-csharp[Prediction](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#Prediction "Declare prediction class")]

    <span data-ttu-id="d709b-186">`MovieReviewSentimentPrediction` é a classe de previsão usada após o treinamento do modelo.</span><span class="sxs-lookup"><span data-stu-id="d709b-186">`MovieReviewSentimentPrediction` is the prediction class used after the model training.</span></span> <span data-ttu-id="d709b-187">`MovieReviewSentimentPrediction`tem uma única `float` matriz (`Prediction`) e um `VectorType` atributo.</span><span class="sxs-lookup"><span data-stu-id="d709b-187">`MovieReviewSentimentPrediction` has a single `float` array (`Prediction`) and a `VectorType` attribute.</span></span>
    
### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a><span data-ttu-id="d709b-188">Criar o MLContext, o dicionário de pesquisa e a ação para redimensionar recursos</span><span class="sxs-lookup"><span data-stu-id="d709b-188">Create the MLContext, lookup dictionary, and action to resize features</span></span>

<span data-ttu-id="d709b-189">A [classe MLContext](xref:Microsoft.ML.MLContext) é um ponto de partida para todas as operações do ML.NET.</span><span class="sxs-lookup"><span data-stu-id="d709b-189">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="d709b-190">Inicializar `mlContext` cria um novo ambiente do ML.NET que pode ser compartilhado entre os objetos do fluxo de trabalho de criação de modelo.</span><span class="sxs-lookup"><span data-stu-id="d709b-190">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="d709b-191">Ele é semelhante, conceitualmente, a `DBContext` no Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="d709b-191">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

1. <span data-ttu-id="d709b-192">Substitua a linha `Console.WriteLine("Hello World!")` no método `Main` pelo seguinte código para declarar e inicializar a variável mlContext:</span><span class="sxs-lookup"><span data-stu-id="d709b-192">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

   [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateMLContext "Create the ML Context")]

1. <span data-ttu-id="d709b-193">Crie um dicionário para codificar palavras como inteiros usando o [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) método para carregar dados de mapeamento de um arquivo, como mostrado na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="d709b-193">Create a dictionary to encode words as integers by using the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method to load mapping data from a file, as seen in the following table:</span></span>

    |<span data-ttu-id="d709b-194">Palavra</span><span class="sxs-lookup"><span data-stu-id="d709b-194">Word</span></span>     |<span data-ttu-id="d709b-195">Índice</span><span class="sxs-lookup"><span data-stu-id="d709b-195">Index</span></span>    |
    |---------|---------|
    |<span data-ttu-id="d709b-196">Kids</span><span class="sxs-lookup"><span data-stu-id="d709b-196">kids</span></span>     |  <span data-ttu-id="d709b-197">362</span><span class="sxs-lookup"><span data-stu-id="d709b-197">362</span></span>    |
    |<span data-ttu-id="d709b-198">deseja</span><span class="sxs-lookup"><span data-stu-id="d709b-198">want</span></span>     |  <span data-ttu-id="d709b-199">181</span><span class="sxs-lookup"><span data-stu-id="d709b-199">181</span></span>    |
    |<span data-ttu-id="d709b-200">errado</span><span class="sxs-lookup"><span data-stu-id="d709b-200">wrong</span></span>    |  <span data-ttu-id="d709b-201">355</span><span class="sxs-lookup"><span data-stu-id="d709b-201">355</span></span>    |
    |<span data-ttu-id="d709b-202">efeitos</span><span class="sxs-lookup"><span data-stu-id="d709b-202">effects</span></span>  |  <span data-ttu-id="d709b-203">302</span><span class="sxs-lookup"><span data-stu-id="d709b-203">302</span></span>    |
    |<span data-ttu-id="d709b-204">sensação</span><span class="sxs-lookup"><span data-stu-id="d709b-204">feeling</span></span>  |  <span data-ttu-id="d709b-205">547</span><span class="sxs-lookup"><span data-stu-id="d709b-205">547</span></span>    |

    <span data-ttu-id="d709b-206">Adicione o código abaixo para criar o mapa de pesquisa:</span><span class="sxs-lookup"><span data-stu-id="d709b-206">Add the code below to create the lookup map:</span></span>

    [!code-csharp[CreateLookupMap](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateLookupMap)]

1. <span data-ttu-id="d709b-207">Adicione um `Action` para redimensionar a matriz de comprimento variável do Word para uma matriz de número inteiro de tamanho fixo, com as próximas linhas de código:</span><span class="sxs-lookup"><span data-stu-id="d709b-207">Add an `Action` to resize the variable length word integer array to an integer array of fixed size, with the next lines of code:</span></span>

   [!code-csharp[ResizeFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a><span data-ttu-id="d709b-208">Carregar o modelo de TensorFlow pré-treinado</span><span class="sxs-lookup"><span data-stu-id="d709b-208">Load the pre-trained TensorFlow model</span></span>

1. <span data-ttu-id="d709b-209">Adicione o código para carregar o modelo TensorFlow:</span><span class="sxs-lookup"><span data-stu-id="d709b-209">Add code to load the TensorFlow model:</span></span>

    [!code-csharp[LoadTensorFlowModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#LoadTensorFlowModel)]

    <span data-ttu-id="d709b-210">Depois que o modelo for carregado, você poderá extrair seu esquema de entrada e saída.</span><span class="sxs-lookup"><span data-stu-id="d709b-210">Once the model is loaded, you can extract its input and output schema.</span></span> <span data-ttu-id="d709b-211">Os esquemas são exibidos apenas para fins de interesse e aprendizado.</span><span class="sxs-lookup"><span data-stu-id="d709b-211">The schemas are displayed for interest and learning only.</span></span> <span data-ttu-id="d709b-212">Você não precisa desse código para que o aplicativo final funcione:</span><span class="sxs-lookup"><span data-stu-id="d709b-212">You do not need this code for the final application to function:</span></span>

    [!code-csharp[GetModelSchema](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#GetModelSchema)]

    <span data-ttu-id="d709b-213">O esquema de entrada é a matriz de comprimento fixo de palavras codificadas por inteiro.</span><span class="sxs-lookup"><span data-stu-id="d709b-213">The input schema is the fixed-length array of integer encoded words.</span></span> <span data-ttu-id="d709b-214">O esquema de saída é uma matriz float de probabilidades que indica se a opinião de uma revisão é negativa ou positiva.</span><span class="sxs-lookup"><span data-stu-id="d709b-214">The output schema is a float array of probabilities indicating whether a review's sentiment is negative, or positive .</span></span> <span data-ttu-id="d709b-215">Esses valores somam 1, uma vez que a probabilidade de ser positiva é o complemento da probabilidade de que o sentimentos seja negativo.</span><span class="sxs-lookup"><span data-stu-id="d709b-215">These values sum to 1, as the probability of being positive is the complement of the probability of the sentiment being negative.</span></span>

## <a name="create-the-mlnet-pipeline"></a><span data-ttu-id="d709b-216">Criar o pipeline ML.NET</span><span class="sxs-lookup"><span data-stu-id="d709b-216">Create the ML.NET pipeline</span></span>

1. <span data-ttu-id="d709b-217">Crie o pipeline e divida o texto de entrada em palavras usando [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) Transform para quebrar o texto em palavras como a próxima linha de código:</span><span class="sxs-lookup"><span data-stu-id="d709b-217">Create the pipeline and split the input text into words using [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform to break the text into words as the next line of code:</span></span>

   [!code-csharp[TokenizeIntoWords](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#TokenizeIntoWords)]

   <span data-ttu-id="d709b-218">A transformação [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) usa espaços para analisar o texto/cadeia de caracteres em palavras.</span><span class="sxs-lookup"><span data-stu-id="d709b-218">The [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform uses spaces to parse the text/string into words.</span></span> <span data-ttu-id="d709b-219">Ele cria uma nova coluna e divide cada cadeia de caracteres de entrada em um vetor de subcadeias de caracteres com base no separador definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="d709b-219">It creates a new column and splits each input string to a vector of substrings based on the user-defined separator.</span></span>

1. <span data-ttu-id="d709b-220">Mapeie as palavras em sua codificação de número inteiro usando a tabela de pesquisa declarada acima:</span><span class="sxs-lookup"><span data-stu-id="d709b-220">Map the words onto their integer encoding using the lookup table that you declared above:</span></span>

    [!code-csharp[MapValue](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#MapValue)]

1. <span data-ttu-id="d709b-221">Redimensione as codificações de inteiro de comprimento variável para o comprimento fixo exigido pelo modelo:</span><span class="sxs-lookup"><span data-stu-id="d709b-221">Resize the variable length integer encodings to the fixed-length one required by the model:</span></span>

    [!code-csharp[CustomMapping](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CustomMapping)]

1. <span data-ttu-id="d709b-222">Classifique a entrada com o modelo TensorFlow carregado:</span><span class="sxs-lookup"><span data-stu-id="d709b-222">Classify the input with the loaded TensorFlow model:</span></span>

    [!code-csharp[ScoreTensorFlowModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="d709b-223">A saída do modelo TensorFlow é `Prediction/Softmax`chamada.</span><span class="sxs-lookup"><span data-stu-id="d709b-223">The TensorFlow model output is called `Prediction/Softmax`.</span></span> <span data-ttu-id="d709b-224">Observe que o nome `Prediction/Softmax` é determinado pelo modelo TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="d709b-224">Note that the name `Prediction/Softmax` is determined by the TensorFlow model.</span></span> <span data-ttu-id="d709b-225">Você não pode alterar esse nome.</span><span class="sxs-lookup"><span data-stu-id="d709b-225">You cannot change this name.</span></span>

1. <span data-ttu-id="d709b-226">Crie uma nova coluna para a previsão de saída:</span><span class="sxs-lookup"><span data-stu-id="d709b-226">Create a new column for the output prediction:</span></span>

    [!code-csharp[SnippetCopyColumns](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#SnippetCopyColumns)]

    <span data-ttu-id="d709b-227">Você precisa copiar a `Prediction/Softmax` coluna em uma com um nome que possa ser usado como uma propriedade em uma C# classe: `Prediction`.</span><span class="sxs-lookup"><span data-stu-id="d709b-227">You need to copy the `Prediction/Softmax` column into one with a name that can be used as a property in a C# class: `Prediction`.</span></span> <span data-ttu-id="d709b-228">O `/` caractere não é permitido em um C# nome de propriedade.</span><span class="sxs-lookup"><span data-stu-id="d709b-228">The `/` character is not allowed in a C# property name.</span></span>

## <a name="create-the-mlnet-model-from-the-pipeline"></a><span data-ttu-id="d709b-229">Criar o modelo ML.NET a partir do pipeline</span><span class="sxs-lookup"><span data-stu-id="d709b-229">Create the ML.NET model from the pipeline</span></span>

1. <span data-ttu-id="d709b-230">Adicione o código para criar o modelo a partir do pipeline:</span><span class="sxs-lookup"><span data-stu-id="d709b-230">Add the code to create the model from the pipeline:</span></span>

    [!code-csharp[SnippetCreateModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#SnippetCreateModel)]  

    <span data-ttu-id="d709b-231">Um modelo ml.net é criado a partir da cadeia de estimadores no pipeline chamando o `Fit` método.</span><span class="sxs-lookup"><span data-stu-id="d709b-231">An ML.NET model is created from the chain of estimators in the pipeline by calling the `Fit` method.</span></span> <span data-ttu-id="d709b-232">Nesse caso, não estamos ajustando nenhum dado para criar o modelo, pois o modelo TensorFlow já foi treinado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d709b-232">In this case, we are not fitting any data to create the model, as the TensorFlow model has already been previously trained.</span></span> <span data-ttu-id="d709b-233">Fornecemos um objeto de exibição de dados vazio para atender aos requisitos `Fit` do método.</span><span class="sxs-lookup"><span data-stu-id="d709b-233">We supply an empty data view object to satisfy the requirements of the `Fit` method.</span></span>

## <a name="use-the-model-to-make-a-prediction"></a><span data-ttu-id="d709b-234">Usar o modelo para fazer uma previsão</span><span class="sxs-lookup"><span data-stu-id="d709b-234">Use the model to make a prediction</span></span>

1. <span data-ttu-id="d709b-235">Adicione o `PredictSentiment` método abaixo do `Main` método:</span><span class="sxs-lookup"><span data-stu-id="d709b-235">Add the `PredictSentiment` method below the `Main` method:</span></span>

    ```csharp
        public static void PredictSentiment(MLContext mlContext, ITransformer model)
        {

        }
    ```

1. <span data-ttu-id="d709b-236">Adicione o seguinte código para criar o `PredictionEngine` como a primeira linha `PredictSentiment()` no método:</span><span class="sxs-lookup"><span data-stu-id="d709b-236">Add the following code to create the `PredictionEngine` as the first line in the `PredictSentiment()` method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreatePredictionEngine)]

    <span data-ttu-id="d709b-237">O [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) é uma API de conveniência, que permite que você faça uma previsão em uma única instância de dados.</span><span class="sxs-lookup"><span data-stu-id="d709b-237">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to make a prediction on a single instance of data.</span></span>

1. <span data-ttu-id="d709b-238">Adicione um comentário para testar as previsões do modelo treinado no método `Predict()` ao criar uma instância de `MovieReview`:</span><span class="sxs-lookup"><span data-stu-id="d709b-238">Add a comment to test the trained model's prediction in the `Predict()` method by creating an instance of `MovieReview`:</span></span>

    [!code-csharp[CreateTestData](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateTestData)]

1. <span data-ttu-id="d709b-239">Passe os dados de comentário de teste `Prediction Engine` para o adicionando as próximas linhas de código `PredictSentiment()` no método:</span><span class="sxs-lookup"><span data-stu-id="d709b-239">Pass the test comment data to the `Prediction Engine` by adding the next lines of code in the `PredictSentiment()` method:</span></span>

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#Predict)]

1. <span data-ttu-id="d709b-240">A função [Predict ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) faz uma previsão em uma única linha de dados:</span><span class="sxs-lookup"><span data-stu-id="d709b-240">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

    |<span data-ttu-id="d709b-241">Propriedade</span><span class="sxs-lookup"><span data-stu-id="d709b-241">Property</span></span>| <span data-ttu-id="d709b-242">Valor</span><span class="sxs-lookup"><span data-stu-id="d709b-242">Value</span></span>|<span data-ttu-id="d709b-243">Tipo</span><span class="sxs-lookup"><span data-stu-id="d709b-243">Type</span></span>|
    |-------------|-----------------------|------|
    |<span data-ttu-id="d709b-244">Previsão</span><span class="sxs-lookup"><span data-stu-id="d709b-244">Prediction</span></span>|<span data-ttu-id="d709b-245">[0,5459937, 0,454006255]</span><span class="sxs-lookup"><span data-stu-id="d709b-245">[0.5459937, 0.454006255]</span></span>|<span data-ttu-id="d709b-246">float []</span><span class="sxs-lookup"><span data-stu-id="d709b-246">float[]</span></span>|

1. <span data-ttu-id="d709b-247">Exiba a previsão de sentimentos usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="d709b-247">Display sentiment prediction using the following code:</span></span>

    [!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#DisplayPredictions)]

1. <span data-ttu-id="d709b-248">Adicione uma chamada ao `PredictSentiment` no final `Main` do método:</span><span class="sxs-lookup"><span data-stu-id="d709b-248">Add a call to `PredictSentiment` at the end of the `Main` method:</span></span>

    [!code-csharp[CallPredictSentiment](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CallPredictSentiment)]

## <a name="results"></a><span data-ttu-id="d709b-249">Resultados</span><span class="sxs-lookup"><span data-stu-id="d709b-249">Results</span></span>

<span data-ttu-id="d709b-250">Compile e execute seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d709b-250">Build and run your application.</span></span>

<span data-ttu-id="d709b-251">Seus resultados devem ser semelhantes aos seguintes.</span><span class="sxs-lookup"><span data-stu-id="d709b-251">Your results should be similar to the following.</span></span> <span data-ttu-id="d709b-252">Durante o processamento, as mensagens são exibidas.</span><span class="sxs-lookup"><span data-stu-id="d709b-252">During processing, messages are displayed.</span></span> <span data-ttu-id="d709b-253">Você pode ver avisos ou mensagens de processamento.</span><span class="sxs-lookup"><span data-stu-id="d709b-253">You may see warnings, or processing messages.</span></span> <span data-ttu-id="d709b-254">Essas mensagens foram removidas dos resultados a seguir para ficar mais claro.</span><span class="sxs-lookup"><span data-stu-id="d709b-254">These messages have been removed from the following results for clarity.</span></span>

```console
   Number of classes: 2
   Is sentiment/review positive ? Yes
```

<span data-ttu-id="d709b-255">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="d709b-255">Congratulations!</span></span> <span data-ttu-id="d709b-256">Agora você criou com êxito um modelo de aprendizado de máquina para classificar e prever os sentimentos de mensagens reutilizando um modelo pretreinado `TensorFlow` no ml.net.</span><span class="sxs-lookup"><span data-stu-id="d709b-256">You've now successfully built a machine learning model for classifying and predicting messages sentiment by reusing a pre-trained `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="d709b-257">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF).</span><span class="sxs-lookup"><span data-stu-id="d709b-257">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

<span data-ttu-id="d709b-258">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="d709b-258">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="d709b-259">Carregar um modelo de TensorFlow pré-treinado</span><span class="sxs-lookup"><span data-stu-id="d709b-259">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="d709b-260">Transformar o texto de comentário do site em recursos adequados para o modelo</span><span class="sxs-lookup"><span data-stu-id="d709b-260">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="d709b-261">Usar o modelo para fazer uma previsão</span><span class="sxs-lookup"><span data-stu-id="d709b-261">Use the model to make a prediction</span></span>
