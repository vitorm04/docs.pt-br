---
title: 'Tutorial: analisar o sentimentos das análises de filmes usando um modelo de TensorFlow pré-treinado'
description: Este tutorial mostra como usar um modelo de TensorFlow pré-treinado para classificar as opiniões nos comentários do site. O classificador de sentimentos binário C# é um aplicativo de console desenvolvido usando o Visual Studio.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: nakersha
author: natke
ms.openlocfilehash: 417abb5052df95c8496d97894d3e11d2956d7a1a
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774394"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a><span data-ttu-id="3f235-104">Tutorial: analisar o sentimentos das análises de filmes usando um modelo de TensorFlow pré-treinado no ML.NET</span><span class="sxs-lookup"><span data-stu-id="3f235-104">Tutorial: Analyze sentiment of movie reviews using a pre-trained TensorFlow model in ML.NET</span></span>

<span data-ttu-id="3f235-105">Este tutorial mostra como usar um modelo de TensorFlow pré-treinado para classificar as opiniões nos comentários do site.</span><span class="sxs-lookup"><span data-stu-id="3f235-105">This tutorial shows you how to use a pre-trained TensorFlow model to classify sentiment in website comments.</span></span> <span data-ttu-id="3f235-106">O classificador de sentimentos binário C# é um aplicativo de console desenvolvido usando o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3f235-106">The binary sentiment classifier is a C# console application developed using Visual Studio.</span></span>

<span data-ttu-id="3f235-107">O modelo TensorFlow usado neste tutorial foi treinado usando revisões de filme do banco de dados do IMDB.</span><span class="sxs-lookup"><span data-stu-id="3f235-107">The TensorFlow model used in this tutorial was trained using movie reviews from the IMDB database.</span></span> <span data-ttu-id="3f235-108">Depois de concluir o desenvolvimento do aplicativo, você poderá fornecer o texto de revisão do filme e o aplicativo informará se a revisão tem uma opinião positiva ou negativa.</span><span class="sxs-lookup"><span data-stu-id="3f235-108">Once you have finished developing the application, you will be able to supply movie review text and the application will tell you whether the review has positive or negative sentiment.</span></span>

<span data-ttu-id="3f235-109">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="3f235-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="3f235-110">Carregar um modelo de TensorFlow pré-treinado</span><span class="sxs-lookup"><span data-stu-id="3f235-110">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="3f235-111">Transformar o texto de comentário do site em recursos adequados para o modelo</span><span class="sxs-lookup"><span data-stu-id="3f235-111">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="3f235-112">Usar o modelo para fazer uma previsão</span><span class="sxs-lookup"><span data-stu-id="3f235-112">Use the model to make a prediction</span></span>

<span data-ttu-id="3f235-113">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF).</span><span class="sxs-lookup"><span data-stu-id="3f235-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3f235-114">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="3f235-114">Prerequisites</span></span>

* <span data-ttu-id="3f235-115">[Visual Studio 2017 versão 15,6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) com a carga de trabalho "desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="3f235-115">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="setup"></a><span data-ttu-id="3f235-116">Configuração</span><span class="sxs-lookup"><span data-stu-id="3f235-116">Setup</span></span>

### <a name="create-the-application"></a><span data-ttu-id="3f235-117">Criar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="3f235-117">Create the application</span></span>

1. <span data-ttu-id="3f235-118">Crie um **aplicativo de console do .NET Core** chamado "TextClassificationTF".</span><span class="sxs-lookup"><span data-stu-id="3f235-118">Create a **.NET Core Console Application** called "TextClassificationTF".</span></span>

2. <span data-ttu-id="3f235-119">Crie um diretório chamado *Data* no seu projeto para salvar os arquivos do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="3f235-119">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="3f235-120">Instalar o **Pacote NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="3f235-120">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="3f235-121">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="3f235-121">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="3f235-122">Escolha "nuget.org" como a origem do pacote e, em seguida, selecione a guia **procurar** . procure **Microsoft.ml**, selecione o pacote desejado e, em seguida, selecione o botão **instalar** .</span><span class="sxs-lookup"><span data-stu-id="3f235-122">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="3f235-123">Prossiga com a instalação concordando com os termos de licença do pacote que você escolher.</span><span class="sxs-lookup"><span data-stu-id="3f235-123">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="3f235-124">Repita essas etapas para **Microsoft. ml. TensorFlow**.</span><span class="sxs-lookup"><span data-stu-id="3f235-124">Repeat these steps for **Microsoft.ML.TensorFlow**.</span></span>

### <a name="add-the-tensorflow-model-to-the-project"></a><span data-ttu-id="3f235-125">Adicionar o modelo TensorFlow ao projeto</span><span class="sxs-lookup"><span data-stu-id="3f235-125">Add the TensorFlow model to the project</span></span>

> [!NOTE]
> <span data-ttu-id="3f235-126">O modelo para este tutorial é do repositório GitHub [dotnet/MachineLearning-TestData](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) .</span><span class="sxs-lookup"><span data-stu-id="3f235-126">The model for this tutorial is from the [dotnet/machinelearning-testdata](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) GitHub repo.</span></span> <span data-ttu-id="3f235-127">O modelo está no formato TensorFlow SavedModel.</span><span class="sxs-lookup"><span data-stu-id="3f235-127">The model is in TensorFlow SavedModel format.</span></span>

1. <span data-ttu-id="3f235-128">Baixe o [arquivo zip sentiment_model](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true)e descompacte.</span><span class="sxs-lookup"><span data-stu-id="3f235-128">Download the [sentiment_model zip file](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true), and unzip.</span></span>

    <span data-ttu-id="3f235-129">O arquivo zip contém:</span><span class="sxs-lookup"><span data-stu-id="3f235-129">The zip file contains:</span></span>

    * <span data-ttu-id="3f235-130">`saved_model.pb`: o próprio modelo de TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="3f235-130">`saved_model.pb`: the TensorFlow model itself.</span></span> <span data-ttu-id="3f235-131">O modelo usa uma matriz de inteiros de tamanho fixo (tamanho 600) de recursos que representam o texto em uma cadeia de caracteres de revisão do IMDB e gera duas probabilidades que somam 1: a probabilidade de que a revisão de entrada tenha uma opinião positiva e a probabilidade de que a revisão de entrada tenha sentimentos negativo.</span><span class="sxs-lookup"><span data-stu-id="3f235-131">The model takes a fixed length (size 600) integer array of features representing the text in an IMDB review string, and outputs two probabilities which sum to 1: the probability that the input review has positive sentiment, and the probability that the input review has negative sentiment.</span></span>
    * <span data-ttu-id="3f235-132">`imdb_word_index.csv`: um mapeamento de palavras individuais para um valor inteiro.</span><span class="sxs-lookup"><span data-stu-id="3f235-132">`imdb_word_index.csv`: a mapping from individual words to an integer value.</span></span> <span data-ttu-id="3f235-133">O mapeamento é usado para gerar os recursos de entrada para o modelo TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="3f235-133">The mapping is used to generate the input features for the TensorFlow model.</span></span>

2. <span data-ttu-id="3f235-134">Copie o conteúdo do diretório `sentiment_model` mais interno para o seu projeto do *TextClassificationTF* `sentiment_model` diretório.</span><span class="sxs-lookup"><span data-stu-id="3f235-134">Copy the contents of the innermost `sentiment_model` directory into your *TextClassificationTF* project `sentiment_model` directory.</span></span> <span data-ttu-id="3f235-135">Este diretório contém o modelo e os arquivos de suporte adicionais necessários para este tutorial, conforme mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="3f235-135">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![conteúdo do diretório sentiment_model](./media/text-classification-tf/sentiment-model-files.png)

3. <span data-ttu-id="3f235-137">Em Gerenciador de Soluções, clique com o botão direito do mouse em cada um dos arquivos no diretório `sentiment_model` e no subdiretório e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="3f235-137">In Solution Explorer, right-click each of the files in the `sentiment_model` directory and subdirectory and select **Properties**.</span></span> <span data-ttu-id="3f235-138">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.</span><span class="sxs-lookup"><span data-stu-id="3f235-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="add-using-statements-and-global-variables"></a><span data-ttu-id="3f235-139">Adicionar instruções using e variáveis globais</span><span class="sxs-lookup"><span data-stu-id="3f235-139">Add using statements and global variables</span></span>

1. <span data-ttu-id="3f235-140">Adicione as seguintes instruções `using` adicionais ao início do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="3f235-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TextClassificationTF/Program.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="3f235-141">Crie duas variáveis globais logo acima do método `Main` para manter o caminho do arquivo de modelo salvo e o comprimento do vetor de recurso.</span><span class="sxs-lookup"><span data-stu-id="3f235-141">Create two global variables right above the `Main` method to hold the saved model file path, and the feature vector length.</span></span>

   [!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TextClassificationTF/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * <span data-ttu-id="3f235-142">`_modelPath` é o caminho do arquivo do modelo treinado.</span><span class="sxs-lookup"><span data-stu-id="3f235-142">`_modelPath` is the file path of the trained model.</span></span>
    * <span data-ttu-id="3f235-143">`FeatureLength` é o comprimento da matriz de recursos de inteiro que o modelo espera.</span><span class="sxs-lookup"><span data-stu-id="3f235-143">`FeatureLength` is the length of the integer feature array that the model is expecting.</span></span>

### <a name="model-the-data"></a><span data-ttu-id="3f235-144">Modelar os dados</span><span class="sxs-lookup"><span data-stu-id="3f235-144">Model the data</span></span>

<span data-ttu-id="3f235-145">As revisões de filme são texto de forma livre.</span><span class="sxs-lookup"><span data-stu-id="3f235-145">Movie reviews are free form text.</span></span> <span data-ttu-id="3f235-146">Seu aplicativo converte o texto no formato de entrada esperado pelo modelo em uma série de estágios discretos.</span><span class="sxs-lookup"><span data-stu-id="3f235-146">Your application converts the text into the input format expected by the model in a number of discrete stages.</span></span>

<span data-ttu-id="3f235-147">A primeira é dividir o texto em palavras separadas e usar o arquivo de mapeamento fornecido para mapear cada palavra em uma codificação de número inteiro.</span><span class="sxs-lookup"><span data-stu-id="3f235-147">The first is to split the text into separate words and use the provided mapping file to map each word onto an integer encoding.</span></span> <span data-ttu-id="3f235-148">O resultado dessa transformação é uma matriz de inteiro de comprimento variável com um comprimento correspondente ao número de palavras na sentença.</span><span class="sxs-lookup"><span data-stu-id="3f235-148">The result of this transformation is a variable length integer array with a length corresponding to the number of words in the sentence.</span></span>

|<span data-ttu-id="3f235-149">propriedade</span><span class="sxs-lookup"><span data-stu-id="3f235-149">Property</span></span>| <span data-ttu-id="3f235-150">Valor</span><span class="sxs-lookup"><span data-stu-id="3f235-150">Value</span></span>|<span data-ttu-id="3f235-151">Digite</span><span class="sxs-lookup"><span data-stu-id="3f235-151">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="3f235-152">ReviewText</span><span class="sxs-lookup"><span data-stu-id="3f235-152">ReviewText</span></span>|<span data-ttu-id="3f235-153">Esse filme é realmente bom</span><span class="sxs-lookup"><span data-stu-id="3f235-153">this film is really good</span></span>|<span data-ttu-id="3f235-154">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="3f235-154">string</span></span>|
|<span data-ttu-id="3f235-155">VariableLengthFeatures</span><span class="sxs-lookup"><span data-stu-id="3f235-155">VariableLengthFeatures</span></span>|<span data-ttu-id="3f235-156">14, 22, 9, 66, 78,...</span><span class="sxs-lookup"><span data-stu-id="3f235-156">14,22,9,66,78,...</span></span> |<span data-ttu-id="3f235-157">int []</span><span class="sxs-lookup"><span data-stu-id="3f235-157">int[]</span></span>|

<span data-ttu-id="3f235-158">Em seguida, a matriz de recursos de comprimento variável é redimensionada para um comprimento fixo de 600.</span><span class="sxs-lookup"><span data-stu-id="3f235-158">The variable length feature array is then resized to a fixed length of 600.</span></span> <span data-ttu-id="3f235-159">Esse é o comprimento esperado pelo modelo TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="3f235-159">This is the length that the TensorFlow model expects.</span></span>

|<span data-ttu-id="3f235-160">propriedade</span><span class="sxs-lookup"><span data-stu-id="3f235-160">Property</span></span>| <span data-ttu-id="3f235-161">Valor</span><span class="sxs-lookup"><span data-stu-id="3f235-161">Value</span></span>|<span data-ttu-id="3f235-162">Digite</span><span class="sxs-lookup"><span data-stu-id="3f235-162">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="3f235-163">ReviewText</span><span class="sxs-lookup"><span data-stu-id="3f235-163">ReviewText</span></span>|<span data-ttu-id="3f235-164">Esse filme é realmente bom</span><span class="sxs-lookup"><span data-stu-id="3f235-164">this film is really good</span></span>|<span data-ttu-id="3f235-165">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="3f235-165">string</span></span>|
|<span data-ttu-id="3f235-166">VariableLengthFeatures</span><span class="sxs-lookup"><span data-stu-id="3f235-166">VariableLengthFeatures</span></span>|<span data-ttu-id="3f235-167">14, 22, 9, 66, 78,...</span><span class="sxs-lookup"><span data-stu-id="3f235-167">14,22,9,66,78,...</span></span> |<span data-ttu-id="3f235-168">int []</span><span class="sxs-lookup"><span data-stu-id="3f235-168">int[]</span></span>|
|<span data-ttu-id="3f235-169">Recursos</span><span class="sxs-lookup"><span data-stu-id="3f235-169">Features</span></span>|<span data-ttu-id="3f235-170">14, 22, 9, 66, 78,...</span><span class="sxs-lookup"><span data-stu-id="3f235-170">14,22,9,66,78,...</span></span> |<span data-ttu-id="3f235-171">int [600]</span><span class="sxs-lookup"><span data-stu-id="3f235-171">int[600]</span></span>|

1. <span data-ttu-id="3f235-172">Crie uma classe para os dados de entrada, após o método de `Main`:</span><span class="sxs-lookup"><span data-stu-id="3f235-172">Create a class for your input data, after the `Main` method:</span></span>

    [!code-csharp[MovieReviewClass](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#MovieReviewClass "Declare movie review type")]

    <span data-ttu-id="3f235-173">A classe de dados de entrada, `MovieReview`, tem um `string` para comentários do usuário (`ReviewText`).</span><span class="sxs-lookup"><span data-stu-id="3f235-173">The input data class, `MovieReview`, has a `string` for user comments (`ReviewText`).</span></span>

1. <span data-ttu-id="3f235-174">Crie uma classe para os recursos de comprimento variável, após o método de `Main`:</span><span class="sxs-lookup"><span data-stu-id="3f235-174">Create a class for the variable length features, after the `Main` method:</span></span>

    [!code-csharp[VariableLengthFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    <span data-ttu-id="3f235-175">A propriedade `VariableLengthFeatures` tem um atributo [vectortype](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) para designá-la como um vetor.</span><span class="sxs-lookup"><span data-stu-id="3f235-175">The `VariableLengthFeatures` property has a [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) attribute to designate it as a vector.</span></span>  <span data-ttu-id="3f235-176">Todos os elementos de vetor devem ser do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="3f235-176">All of the vector elements must be the same type.</span></span> <span data-ttu-id="3f235-177">Em conjuntos de dados com um grande número de colunas, carregar várias colunas como um único vetor reduz o número de passagens de dados quando você aplica transformações de dados.</span><span class="sxs-lookup"><span data-stu-id="3f235-177">In data sets with a large number of columns, loading multiple columns as a single vector reduces the number of data passes when you apply data transformations.</span></span>

    <span data-ttu-id="3f235-178">Essa classe é usada na ação `ResizeFeatures`.</span><span class="sxs-lookup"><span data-stu-id="3f235-178">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="3f235-179">Os nomes de suas propriedades (neste caso, apenas um) são usados para indicar quais colunas no DataView podem ser usadas como _entrada_ para a ação de mapeamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="3f235-179">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _input_ to the custom mapping action.</span></span>

1. <span data-ttu-id="3f235-180">Crie uma classe para os recursos de comprimento fixo, após o método de `Main`:</span><span class="sxs-lookup"><span data-stu-id="3f235-180">Create a class for the fixed length features, after the `Main` method:</span></span>

    [!code-csharp[FixedLengthFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#FixedLengthFeatures)]

    <span data-ttu-id="3f235-181">Essa classe é usada na ação `ResizeFeatures`.</span><span class="sxs-lookup"><span data-stu-id="3f235-181">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="3f235-182">Os nomes de suas propriedades (neste caso, apenas um) são usados para indicar quais colunas no DataView podem ser usadas como a _saída_ da ação de mapeamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="3f235-182">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _output_ of the custom mapping action.</span></span>

    <span data-ttu-id="3f235-183">Observe que o nome da propriedade `Features` é determinado pelo modelo TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="3f235-183">Note that the name of the property `Features` is determined by the TensorFlow model.</span></span> <span data-ttu-id="3f235-184">Você não pode alterar esse nome de propriedade.</span><span class="sxs-lookup"><span data-stu-id="3f235-184">You cannot change this property name.</span></span>

1. <span data-ttu-id="3f235-185">Crie uma classe para a previsão após o método de `Main`:</span><span class="sxs-lookup"><span data-stu-id="3f235-185">Create a class for the prediction after the `Main` method:</span></span>

    [!code-csharp[Prediction](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#Prediction "Declare prediction class")]

    <span data-ttu-id="3f235-186">`MovieReviewSentimentPrediction` é a classe de previsão usada após o treinamento do modelo.</span><span class="sxs-lookup"><span data-stu-id="3f235-186">`MovieReviewSentimentPrediction` is the prediction class used after the model training.</span></span> <span data-ttu-id="3f235-187">`MovieReviewSentimentPrediction` tem uma única matriz de `float` (`Prediction`) e um atributo de `VectorType`.</span><span class="sxs-lookup"><span data-stu-id="3f235-187">`MovieReviewSentimentPrediction` has a single `float` array (`Prediction`) and a `VectorType` attribute.</span></span>

### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a><span data-ttu-id="3f235-188">Criar o MLContext, o dicionário de pesquisa e a ação para redimensionar recursos</span><span class="sxs-lookup"><span data-stu-id="3f235-188">Create the MLContext, lookup dictionary, and action to resize features</span></span>

<span data-ttu-id="3f235-189">A [classe MLContext](xref:Microsoft.ML.MLContext) é um ponto de partida para todas as operações do ML.NET.</span><span class="sxs-lookup"><span data-stu-id="3f235-189">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="3f235-190">Inicializar `mlContext` cria um novo ambiente do ML.NET que pode ser compartilhado entre os objetos do fluxo de trabalho de criação de modelo.</span><span class="sxs-lookup"><span data-stu-id="3f235-190">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="3f235-191">Ele é semelhante, conceitualmente, a `DBContext` no Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="3f235-191">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

1. <span data-ttu-id="3f235-192">Substitua a linha `Console.WriteLine("Hello World!")` no método `Main` pelo seguinte código para declarar e inicializar a variável mlContext:</span><span class="sxs-lookup"><span data-stu-id="3f235-192">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

   [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateMLContext "Create the ML Context")]

1. <span data-ttu-id="3f235-193">Crie um dicionário para codificar palavras como inteiros usando o método [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) para carregar dados de mapeamento de um arquivo, como mostrado na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="3f235-193">Create a dictionary to encode words as integers by using the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method to load mapping data from a file, as seen in the following table:</span></span>

    |<span data-ttu-id="3f235-194">Palavra</span><span class="sxs-lookup"><span data-stu-id="3f235-194">Word</span></span>     |<span data-ttu-id="3f235-195">Índice</span><span class="sxs-lookup"><span data-stu-id="3f235-195">Index</span></span>    |
    |---------|---------|
    |<span data-ttu-id="3f235-196">Kids</span><span class="sxs-lookup"><span data-stu-id="3f235-196">kids</span></span>     |  <span data-ttu-id="3f235-197">362</span><span class="sxs-lookup"><span data-stu-id="3f235-197">362</span></span>    |
    |<span data-ttu-id="3f235-198">deseja</span><span class="sxs-lookup"><span data-stu-id="3f235-198">want</span></span>     |  <span data-ttu-id="3f235-199">181</span><span class="sxs-lookup"><span data-stu-id="3f235-199">181</span></span>    |
    |<span data-ttu-id="3f235-200">errado</span><span class="sxs-lookup"><span data-stu-id="3f235-200">wrong</span></span>    |  <span data-ttu-id="3f235-201">355</span><span class="sxs-lookup"><span data-stu-id="3f235-201">355</span></span>    |
    |<span data-ttu-id="3f235-202">efeitos</span><span class="sxs-lookup"><span data-stu-id="3f235-202">effects</span></span>  |  <span data-ttu-id="3f235-203">302</span><span class="sxs-lookup"><span data-stu-id="3f235-203">302</span></span>    |
    |<span data-ttu-id="3f235-204">sensação</span><span class="sxs-lookup"><span data-stu-id="3f235-204">feeling</span></span>  |  <span data-ttu-id="3f235-205">547</span><span class="sxs-lookup"><span data-stu-id="3f235-205">547</span></span>    |

    <span data-ttu-id="3f235-206">Adicione o código abaixo para criar o mapa de pesquisa:</span><span class="sxs-lookup"><span data-stu-id="3f235-206">Add the code below to create the lookup map:</span></span>

    [!code-csharp[CreateLookupMap](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateLookupMap)]

1. <span data-ttu-id="3f235-207">Adicione um `Action` para redimensionar o tamanho da variável matriz de inteiros da palavra para uma matriz de tamanho inteiro fixo, com as próximas linhas de código:</span><span class="sxs-lookup"><span data-stu-id="3f235-207">Add an `Action` to resize the variable length word integer array to an integer array of fixed size, with the next lines of code:</span></span>

   [!code-csharp[ResizeFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a><span data-ttu-id="3f235-208">Carregar o modelo de TensorFlow pré-treinado</span><span class="sxs-lookup"><span data-stu-id="3f235-208">Load the pre-trained TensorFlow model</span></span>

1. <span data-ttu-id="3f235-209">Adicione o código para carregar o modelo TensorFlow:</span><span class="sxs-lookup"><span data-stu-id="3f235-209">Add code to load the TensorFlow model:</span></span>

    [!code-csharp[LoadTensorFlowModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#LoadTensorFlowModel)]

    <span data-ttu-id="3f235-210">Depois que o modelo for carregado, você poderá extrair seu esquema de entrada e saída.</span><span class="sxs-lookup"><span data-stu-id="3f235-210">Once the model is loaded, you can extract its input and output schema.</span></span> <span data-ttu-id="3f235-211">Os esquemas são exibidos apenas para fins de interesse e aprendizado.</span><span class="sxs-lookup"><span data-stu-id="3f235-211">The schemas are displayed for interest and learning only.</span></span> <span data-ttu-id="3f235-212">Você não precisa desse código para que o aplicativo final funcione:</span><span class="sxs-lookup"><span data-stu-id="3f235-212">You do not need this code for the final application to function:</span></span>

    [!code-csharp[GetModelSchema](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#GetModelSchema)]

    <span data-ttu-id="3f235-213">O esquema de entrada é a matriz de comprimento fixo de palavras codificadas por inteiro.</span><span class="sxs-lookup"><span data-stu-id="3f235-213">The input schema is the fixed-length array of integer encoded words.</span></span> <span data-ttu-id="3f235-214">O esquema de saída é uma matriz float de probabilidades que indica se a opinião de uma revisão é negativa ou positiva.</span><span class="sxs-lookup"><span data-stu-id="3f235-214">The output schema is a float array of probabilities indicating whether a review's sentiment is negative, or positive .</span></span> <span data-ttu-id="3f235-215">Esses valores somam 1, uma vez que a probabilidade de ser positiva é o complemento da probabilidade de que o sentimentos seja negativo.</span><span class="sxs-lookup"><span data-stu-id="3f235-215">These values sum to 1, as the probability of being positive is the complement of the probability of the sentiment being negative.</span></span>

## <a name="create-the-mlnet-pipeline"></a><span data-ttu-id="3f235-216">Criar o pipeline ML.NET</span><span class="sxs-lookup"><span data-stu-id="3f235-216">Create the ML.NET pipeline</span></span>

1. <span data-ttu-id="3f235-217">Crie o pipeline e divida o texto de entrada em palavras usando [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) Transform para quebrar o texto em palavras como a próxima linha de código:</span><span class="sxs-lookup"><span data-stu-id="3f235-217">Create the pipeline and split the input text into words using [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform to break the text into words as the next line of code:</span></span>

   [!code-csharp[TokenizeIntoWords](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#TokenizeIntoWords)]

   <span data-ttu-id="3f235-218">A transformação [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) usa espaços para analisar o texto/cadeia de caracteres em palavras.</span><span class="sxs-lookup"><span data-stu-id="3f235-218">The [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform uses spaces to parse the text/string into words.</span></span> <span data-ttu-id="3f235-219">Ele cria uma nova coluna e divide cada cadeia de caracteres de entrada em um vetor de subcadeias de caracteres com base no separador definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="3f235-219">It creates a new column and splits each input string to a vector of substrings based on the user-defined separator.</span></span>

1. <span data-ttu-id="3f235-220">Mapeie as palavras em sua codificação de número inteiro usando a tabela de pesquisa declarada acima:</span><span class="sxs-lookup"><span data-stu-id="3f235-220">Map the words onto their integer encoding using the lookup table that you declared above:</span></span>

    [!code-csharp[MapValue](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#MapValue)]

1. <span data-ttu-id="3f235-221">Redimensione as codificações de inteiro de comprimento variável para o comprimento fixo exigido pelo modelo:</span><span class="sxs-lookup"><span data-stu-id="3f235-221">Resize the variable length integer encodings to the fixed-length one required by the model:</span></span>

    [!code-csharp[CustomMapping](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CustomMapping)]

1. <span data-ttu-id="3f235-222">Classifique a entrada com o modelo TensorFlow carregado:</span><span class="sxs-lookup"><span data-stu-id="3f235-222">Classify the input with the loaded TensorFlow model:</span></span>

    [!code-csharp[ScoreTensorFlowModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="3f235-223">A saída do modelo TensorFlow é chamada de `Prediction/Softmax`.</span><span class="sxs-lookup"><span data-stu-id="3f235-223">The TensorFlow model output is called `Prediction/Softmax`.</span></span> <span data-ttu-id="3f235-224">Observe que o nome `Prediction/Softmax` é determinado pelo modelo TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="3f235-224">Note that the name `Prediction/Softmax` is determined by the TensorFlow model.</span></span> <span data-ttu-id="3f235-225">Você não pode alterar esse nome.</span><span class="sxs-lookup"><span data-stu-id="3f235-225">You cannot change this name.</span></span>

1. <span data-ttu-id="3f235-226">Crie uma nova coluna para a previsão de saída:</span><span class="sxs-lookup"><span data-stu-id="3f235-226">Create a new column for the output prediction:</span></span>

    [!code-csharp[SnippetCopyColumns](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#SnippetCopyColumns)]

    <span data-ttu-id="3f235-227">Você precisa copiar a coluna `Prediction/Softmax` em uma com um nome que possa ser usado como uma propriedade em uma C# classe:`Prediction`.</span><span class="sxs-lookup"><span data-stu-id="3f235-227">You need to copy the `Prediction/Softmax` column into one with a name that can be used as a property in a C# class: `Prediction`.</span></span> <span data-ttu-id="3f235-228">O caractere de `/` não é permitido em C# um nome de propriedade.</span><span class="sxs-lookup"><span data-stu-id="3f235-228">The `/` character is not allowed in a C# property name.</span></span>

## <a name="create-the-mlnet-model-from-the-pipeline"></a><span data-ttu-id="3f235-229">Criar o modelo ML.NET a partir do pipeline</span><span class="sxs-lookup"><span data-stu-id="3f235-229">Create the ML.NET model from the pipeline</span></span>

1. <span data-ttu-id="3f235-230">Adicione o código para criar o modelo a partir do pipeline:</span><span class="sxs-lookup"><span data-stu-id="3f235-230">Add the code to create the model from the pipeline:</span></span>

    [!code-csharp[SnippetCreateModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#SnippetCreateModel)]

    <span data-ttu-id="3f235-231">Um modelo ML.NET é criado a partir da cadeia de estimadores no pipeline chamando o método `Fit`.</span><span class="sxs-lookup"><span data-stu-id="3f235-231">An ML.NET model is created from the chain of estimators in the pipeline by calling the `Fit` method.</span></span> <span data-ttu-id="3f235-232">Nesse caso, não estamos ajustando nenhum dado para criar o modelo, pois o modelo TensorFlow já foi treinado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="3f235-232">In this case, we are not fitting any data to create the model, as the TensorFlow model has already been previously trained.</span></span> <span data-ttu-id="3f235-233">Fornecemos um objeto de exibição de dados vazio para atender aos requisitos do método `Fit`.</span><span class="sxs-lookup"><span data-stu-id="3f235-233">We supply an empty data view object to satisfy the requirements of the `Fit` method.</span></span>

## <a name="use-the-model-to-make-a-prediction"></a><span data-ttu-id="3f235-234">Usar o modelo para fazer uma previsão</span><span class="sxs-lookup"><span data-stu-id="3f235-234">Use the model to make a prediction</span></span>

1. <span data-ttu-id="3f235-235">Adicione o método `PredictSentiment` abaixo do método `Main`:</span><span class="sxs-lookup"><span data-stu-id="3f235-235">Add the `PredictSentiment` method below the `Main` method:</span></span>

    ```csharp
    public static void PredictSentiment(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="3f235-236">Adicione o seguinte código para criar o `PredictionEngine` como a primeira linha no método `PredictSentiment()`:</span><span class="sxs-lookup"><span data-stu-id="3f235-236">Add the following code to create the `PredictionEngine` as the first line in the `PredictSentiment()` method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreatePredictionEngine)]

    <span data-ttu-id="3f235-237">O [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) é uma API de conveniência, que permite que você execute uma previsão em uma única instância de dados.</span><span class="sxs-lookup"><span data-stu-id="3f235-237">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="3f235-238">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) não é thread-safe.</span><span class="sxs-lookup"><span data-stu-id="3f235-238">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="3f235-239">É aceitável usar em ambientes de protótipo ou de thread único.</span><span class="sxs-lookup"><span data-stu-id="3f235-239">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="3f235-240">Para melhorar o desempenho e a segurança de thread em ambientes de produção, use o serviço `PredictionEnginePool`, que cria um [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) de objetos [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) para uso em todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3f235-240">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="3f235-241">Consulte este guia sobre como [usar `PredictionEnginePool` em uma API Web do ASP.NET Core](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="3f235-241">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="3f235-242">A extensão de serviço `PredictionEnginePool` está atualmente em versão prévia.</span><span class="sxs-lookup"><span data-stu-id="3f235-242">`PredictionEnginePool` service extension is currently in preview.</span></span>

1. <span data-ttu-id="3f235-243">Adicione um comentário para testar as previsões do modelo treinado no método `Predict()` ao criar uma instância de `MovieReview`:</span><span class="sxs-lookup"><span data-stu-id="3f235-243">Add a comment to test the trained model's prediction in the `Predict()` method by creating an instance of `MovieReview`:</span></span>

    [!code-csharp[CreateTestData](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateTestData)]

1. <span data-ttu-id="3f235-244">Passe os dados de comentário de teste para a `Prediction Engine` adicionando as próximas linhas de código no método `PredictSentiment()`:</span><span class="sxs-lookup"><span data-stu-id="3f235-244">Pass the test comment data to the `Prediction Engine` by adding the next lines of code in the `PredictSentiment()` method:</span></span>

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#Predict)]

1. <span data-ttu-id="3f235-245">A função [Predict ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) faz uma previsão em uma única linha de dados:</span><span class="sxs-lookup"><span data-stu-id="3f235-245">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

    |<span data-ttu-id="3f235-246">propriedade</span><span class="sxs-lookup"><span data-stu-id="3f235-246">Property</span></span>| <span data-ttu-id="3f235-247">Valor</span><span class="sxs-lookup"><span data-stu-id="3f235-247">Value</span></span>|<span data-ttu-id="3f235-248">Digite</span><span class="sxs-lookup"><span data-stu-id="3f235-248">Type</span></span>|
    |-------------|-----------------------|------|
    |<span data-ttu-id="3f235-249">Previsão</span><span class="sxs-lookup"><span data-stu-id="3f235-249">Prediction</span></span>|<span data-ttu-id="3f235-250">[0,5459937, 0,454006255]</span><span class="sxs-lookup"><span data-stu-id="3f235-250">[0.5459937, 0.454006255]</span></span>|<span data-ttu-id="3f235-251">float []</span><span class="sxs-lookup"><span data-stu-id="3f235-251">float[]</span></span>|

1. <span data-ttu-id="3f235-252">Exiba a previsão de sentimentos usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="3f235-252">Display sentiment prediction using the following code:</span></span>

    [!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#DisplayPredictions)]

1. <span data-ttu-id="3f235-253">Adicione uma chamada para `PredictSentiment` no final do método `Main`:</span><span class="sxs-lookup"><span data-stu-id="3f235-253">Add a call to `PredictSentiment` at the end of the `Main` method:</span></span>

    [!code-csharp[CallPredictSentiment](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CallPredictSentiment)]

## <a name="results"></a><span data-ttu-id="3f235-254">Resultados</span><span class="sxs-lookup"><span data-stu-id="3f235-254">Results</span></span>

<span data-ttu-id="3f235-255">Compile e execute seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3f235-255">Build and run your application.</span></span>

<span data-ttu-id="3f235-256">Seus resultados devem ser semelhantes aos seguintes.</span><span class="sxs-lookup"><span data-stu-id="3f235-256">Your results should be similar to the following.</span></span> <span data-ttu-id="3f235-257">Durante o processamento, as mensagens são exibidas.</span><span class="sxs-lookup"><span data-stu-id="3f235-257">During processing, messages are displayed.</span></span> <span data-ttu-id="3f235-258">Você pode ver avisos ou mensagens de processamento.</span><span class="sxs-lookup"><span data-stu-id="3f235-258">You may see warnings, or processing messages.</span></span> <span data-ttu-id="3f235-259">Essas mensagens foram removidas dos resultados a seguir para ficar mais claro.</span><span class="sxs-lookup"><span data-stu-id="3f235-259">These messages have been removed from the following results for clarity.</span></span>

```console
Number of classes: 2
Is sentiment/review positive ? Yes
```

<span data-ttu-id="3f235-260">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="3f235-260">Congratulations!</span></span> <span data-ttu-id="3f235-261">Agora você criou com êxito um modelo de aprendizado de máquina para classificar e prever os sentimentos de mensagens reutilizando um modelo de `TensorFlow` pré-treinado em ML.NET.</span><span class="sxs-lookup"><span data-stu-id="3f235-261">You've now successfully built a machine learning model for classifying and predicting messages sentiment by reusing a pre-trained `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="3f235-262">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF).</span><span class="sxs-lookup"><span data-stu-id="3f235-262">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

<span data-ttu-id="3f235-263">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="3f235-263">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="3f235-264">Carregar um modelo de TensorFlow pré-treinado</span><span class="sxs-lookup"><span data-stu-id="3f235-264">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="3f235-265">Transformar o texto de comentário do site em recursos adequados para o modelo</span><span class="sxs-lookup"><span data-stu-id="3f235-265">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="3f235-266">Usar o modelo para fazer uma previsão</span><span class="sxs-lookup"><span data-stu-id="3f235-266">Use the model to make a prediction</span></span>
