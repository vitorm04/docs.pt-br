---
title: 'Tutorial: Analise o sentimento de revisão usando um modelo TensorFlow'
description: Este tutorial mostra como usar um modelo TensorFlow pré-treinado para classificar o sentimento nos comentários do site. O classificador binário de sentimentoé um aplicativo de console C# desenvolvido usando o Visual Studio.
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 688c5b83cef8f21eef8fa24521a85449a9cfbd48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241111"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a><span data-ttu-id="1dd64-104">Tutorial: Analise o sentimento das avaliações de filmes usando um modelo TensorFlow pré-treinado em ML.NET</span><span class="sxs-lookup"><span data-stu-id="1dd64-104">Tutorial: Analyze sentiment of movie reviews using a pre-trained TensorFlow model in ML.NET</span></span>

<span data-ttu-id="1dd64-105">Este tutorial mostra como usar um modelo TensorFlow pré-treinado para classificar o sentimento nos comentários do site.</span><span class="sxs-lookup"><span data-stu-id="1dd64-105">This tutorial shows you how to use a pre-trained TensorFlow model to classify sentiment in website comments.</span></span> <span data-ttu-id="1dd64-106">O classificador binário de sentimentoé um aplicativo de console C# desenvolvido usando o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1dd64-106">The binary sentiment classifier is a C# console application developed using Visual Studio.</span></span>

<span data-ttu-id="1dd64-107">O modelo TensorFlow usado neste tutorial foi treinado usando avaliações de filmes do banco de dados do IMDB.</span><span class="sxs-lookup"><span data-stu-id="1dd64-107">The TensorFlow model used in this tutorial was trained using movie reviews from the IMDB database.</span></span> <span data-ttu-id="1dd64-108">Depois de terminar de desenvolver o aplicativo, você poderá fornecer texto de revisão de filme e o aplicativo lhe dirá se a revisão tem sentimento positivo ou negativo.</span><span class="sxs-lookup"><span data-stu-id="1dd64-108">Once you have finished developing the application, you will be able to supply movie review text and the application will tell you whether the review has positive or negative sentiment.</span></span>

<span data-ttu-id="1dd64-109">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="1dd64-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="1dd64-110">Carregue um modelo TensorFlow pré-treinado</span><span class="sxs-lookup"><span data-stu-id="1dd64-110">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="1dd64-111">Transforme o texto de comentário do site em recursos adequados para o modelo</span><span class="sxs-lookup"><span data-stu-id="1dd64-111">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="1dd64-112">Usar o modelo para fazer uma previsão</span><span class="sxs-lookup"><span data-stu-id="1dd64-112">Use the model to make a prediction</span></span>

<span data-ttu-id="1dd64-113">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF).</span><span class="sxs-lookup"><span data-stu-id="1dd64-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1dd64-114">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="1dd64-114">Prerequisites</span></span>

* <span data-ttu-id="1dd64-115">[Visual Studio 2017 versão 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) com a carga de trabalho ".NET Core cross-platform development" instalada.</span><span class="sxs-lookup"><span data-stu-id="1dd64-115">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="setup"></a><span data-ttu-id="1dd64-116">Instalação</span><span class="sxs-lookup"><span data-stu-id="1dd64-116">Setup</span></span>

### <a name="create-the-application"></a><span data-ttu-id="1dd64-117">Criar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="1dd64-117">Create the application</span></span>

1. <span data-ttu-id="1dd64-118">Crie um **aplicativo de console .NET Core** chamado "TextClassificationTF".</span><span class="sxs-lookup"><span data-stu-id="1dd64-118">Create a **.NET Core Console Application** called "TextClassificationTF".</span></span>

2. <span data-ttu-id="1dd64-119">Crie um diretório chamado *Dados* em seu projeto para salvar seus arquivos do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="1dd64-119">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="1dd64-120">Instalar o **Pacote NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="1dd64-120">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="1dd64-121">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="1dd64-121">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="1dd64-122">Escolha "nuget.org" como a fonte do pacote e selecione a guia **Procurar** **Microsoft.ML,** selecione o pacote desejado e selecione o botão **Instalar.**</span><span class="sxs-lookup"><span data-stu-id="1dd64-122">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="1dd64-123">Prossiga com a instalação concordando com os termos de licença do pacote que você escolher.</span><span class="sxs-lookup"><span data-stu-id="1dd64-123">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="1dd64-124">Repita estas etapas para **Microsoft.ML.TensorFlow** e **SciSharp.TensorFlow.Redist**.</span><span class="sxs-lookup"><span data-stu-id="1dd64-124">Repeat these steps for **Microsoft.ML.TensorFlow** and **SciSharp.TensorFlow.Redist**.</span></span>

### <a name="add-the-tensorflow-model-to-the-project"></a><span data-ttu-id="1dd64-125">Adicione o modelo TensorFlow ao projeto</span><span class="sxs-lookup"><span data-stu-id="1dd64-125">Add the TensorFlow model to the project</span></span>

> [!NOTE]
> <span data-ttu-id="1dd64-126">O modelo para este tutorial é do [repo GitHub dotnet/machinelearning-testdata.](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model)</span><span class="sxs-lookup"><span data-stu-id="1dd64-126">The model for this tutorial is from the [dotnet/machinelearning-testdata](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) GitHub repo.</span></span> <span data-ttu-id="1dd64-127">O modelo está no formato TensorFlow SavedModel.</span><span class="sxs-lookup"><span data-stu-id="1dd64-127">The model is in TensorFlow SavedModel format.</span></span>

1. <span data-ttu-id="1dd64-128">Baixe o [arquivo zip sentiment_model](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true)e descompacte.</span><span class="sxs-lookup"><span data-stu-id="1dd64-128">Download the [sentiment_model zip file](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true), and unzip.</span></span>

    <span data-ttu-id="1dd64-129">O arquivo zip contém:</span><span class="sxs-lookup"><span data-stu-id="1dd64-129">The zip file contains:</span></span>

    * <span data-ttu-id="1dd64-130">`saved_model.pb`: o próprio modelo TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="1dd64-130">`saved_model.pb`: the TensorFlow model itself.</span></span> <span data-ttu-id="1dd64-131">O modelo pega uma matriz de comprimento fixo (tamanho 600) inteiro de recursos representando o texto em uma seqüência de revisão do IMDB, e produz duas probabilidades que somam a 1: a probabilidade de que a revisão de entrada tenha um sentimento positivo, e a probabilidade de que a revisão de entrada tenha sentimento negativo.</span><span class="sxs-lookup"><span data-stu-id="1dd64-131">The model takes a fixed length (size 600) integer array of features representing the text in an IMDB review string, and outputs two probabilities which sum to 1: the probability that the input review has positive sentiment, and the probability that the input review has negative sentiment.</span></span>
    * <span data-ttu-id="1dd64-132">`imdb_word_index.csv`: um mapeamento de palavras individuais para um valor inteiro.</span><span class="sxs-lookup"><span data-stu-id="1dd64-132">`imdb_word_index.csv`: a mapping from individual words to an integer value.</span></span> <span data-ttu-id="1dd64-133">O mapeamento é usado para gerar os recursos de entrada para o modelo TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="1dd64-133">The mapping is used to generate the input features for the TensorFlow model.</span></span>

2. <span data-ttu-id="1dd64-134">Copie o conteúdo do `sentiment_model` diretório mais íntimo no `sentiment_model` diretório *textclassificationTF.*</span><span class="sxs-lookup"><span data-stu-id="1dd64-134">Copy the contents of the innermost `sentiment_model` directory into your *TextClassificationTF* project `sentiment_model` directory.</span></span> <span data-ttu-id="1dd64-135">Este diretório contém o modelo e os arquivos de suporte adicionais necessários para este tutorial, conforme mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="1dd64-135">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![sentiment_model conteúdo do diretório](./media/text-classification-tf/sentiment-model-files.png)

3. <span data-ttu-id="1dd64-137">No Solution Explorer, clique com o `sentiment_model` botão direito do mouse em cada um dos arquivos do diretório e do subdiretório e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="1dd64-137">In Solution Explorer, right-click each of the files in the `sentiment_model` directory and subdirectory and select **Properties**.</span></span> <span data-ttu-id="1dd64-138">Em **Avançado,** altere o valor de **Copiar para Diretório de Saída** para Copiar se mais **novo**.</span><span class="sxs-lookup"><span data-stu-id="1dd64-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="add-using-statements-and-global-variables"></a><span data-ttu-id="1dd64-139">Adicionar usando declarações e variáveis globais</span><span class="sxs-lookup"><span data-stu-id="1dd64-139">Add using statements and global variables</span></span>

1. <span data-ttu-id="1dd64-140">Adicione as seguintes instruções `using` adicionais ao início do arquivo *Program.cs*: </span><span class="sxs-lookup"><span data-stu-id="1dd64-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

   [!code-csharp[AddUsings](../../../samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="1dd64-141">Crie duas variáveis globais `Main` logo acima do método para manter o caminho do arquivo do modelo salvo e o comprimento do vetor de recurso.</span><span class="sxs-lookup"><span data-stu-id="1dd64-141">Create two global variables right above the `Main` method to hold the saved model file path, and the feature vector length.</span></span>

   [!code-csharp[DeclareGlobalVariables](../../../samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * <span data-ttu-id="1dd64-142">`_modelPath`é o caminho do arquivo do modelo treinado.</span><span class="sxs-lookup"><span data-stu-id="1dd64-142">`_modelPath` is the file path of the trained model.</span></span>
    * <span data-ttu-id="1dd64-143">`FeatureLength`é o comprimento da matriz de recursos inteiros que o modelo está esperando.</span><span class="sxs-lookup"><span data-stu-id="1dd64-143">`FeatureLength` is the length of the integer feature array that the model is expecting.</span></span>

### <a name="model-the-data"></a><span data-ttu-id="1dd64-144">Modelar os dados</span><span class="sxs-lookup"><span data-stu-id="1dd64-144">Model the data</span></span>

<span data-ttu-id="1dd64-145">As críticas de filmes são textos de formulário gratuitos.</span><span class="sxs-lookup"><span data-stu-id="1dd64-145">Movie reviews are free form text.</span></span> <span data-ttu-id="1dd64-146">Seu aplicativo converte o texto no formato de entrada esperado pelo modelo em uma série de etapas discretas.</span><span class="sxs-lookup"><span data-stu-id="1dd64-146">Your application converts the text into the input format expected by the model in a number of discrete stages.</span></span>

<span data-ttu-id="1dd64-147">A primeira é dividir o texto em palavras separadas e usar o arquivo de mapeamento fornecido para mapear cada palavra em uma codificação inteira.</span><span class="sxs-lookup"><span data-stu-id="1dd64-147">The first is to split the text into separate words and use the provided mapping file to map each word onto an integer encoding.</span></span> <span data-ttu-id="1dd64-148">O resultado dessa transformação é uma matriz de inteiro de comprimento variável com um comprimento correspondente ao número de palavras na frase.</span><span class="sxs-lookup"><span data-stu-id="1dd64-148">The result of this transformation is a variable length integer array with a length corresponding to the number of words in the sentence.</span></span>

|<span data-ttu-id="1dd64-149">Propriedade</span><span class="sxs-lookup"><span data-stu-id="1dd64-149">Property</span></span>| <span data-ttu-id="1dd64-150">Valor</span><span class="sxs-lookup"><span data-stu-id="1dd64-150">Value</span></span>|<span data-ttu-id="1dd64-151">Type</span><span class="sxs-lookup"><span data-stu-id="1dd64-151">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="1dd64-152">ComentárioTexto</span><span class="sxs-lookup"><span data-stu-id="1dd64-152">ReviewText</span></span>|<span data-ttu-id="1dd64-153">este filme é muito bom</span><span class="sxs-lookup"><span data-stu-id="1dd64-153">this film is really good</span></span>|<span data-ttu-id="1dd64-154">string</span><span class="sxs-lookup"><span data-stu-id="1dd64-154">string</span></span>|
|<span data-ttu-id="1dd64-155">Recursos de duração de variáveis</span><span class="sxs-lookup"><span data-stu-id="1dd64-155">VariableLengthFeatures</span></span>|<span data-ttu-id="1dd64-156">14,22,9,66,78,...</span><span class="sxs-lookup"><span data-stu-id="1dd64-156">14,22,9,66,78,...</span></span> |<span data-ttu-id="1dd64-157">int[]</span><span class="sxs-lookup"><span data-stu-id="1dd64-157">int[]</span></span>|

<span data-ttu-id="1dd64-158">O conjunto de recursos de comprimento variável é então redimensionado para um comprimento fixo de 600.</span><span class="sxs-lookup"><span data-stu-id="1dd64-158">The variable length feature array is then resized to a fixed length of 600.</span></span> <span data-ttu-id="1dd64-159">Este é o comprimento que o modelo TensorFlow espera.</span><span class="sxs-lookup"><span data-stu-id="1dd64-159">This is the length that the TensorFlow model expects.</span></span>

|<span data-ttu-id="1dd64-160">Propriedade</span><span class="sxs-lookup"><span data-stu-id="1dd64-160">Property</span></span>| <span data-ttu-id="1dd64-161">Valor</span><span class="sxs-lookup"><span data-stu-id="1dd64-161">Value</span></span>|<span data-ttu-id="1dd64-162">Type</span><span class="sxs-lookup"><span data-stu-id="1dd64-162">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="1dd64-163">ComentárioTexto</span><span class="sxs-lookup"><span data-stu-id="1dd64-163">ReviewText</span></span>|<span data-ttu-id="1dd64-164">este filme é muito bom</span><span class="sxs-lookup"><span data-stu-id="1dd64-164">this film is really good</span></span>|<span data-ttu-id="1dd64-165">string</span><span class="sxs-lookup"><span data-stu-id="1dd64-165">string</span></span>|
|<span data-ttu-id="1dd64-166">Recursos de duração de variáveis</span><span class="sxs-lookup"><span data-stu-id="1dd64-166">VariableLengthFeatures</span></span>|<span data-ttu-id="1dd64-167">14,22,9,66,78,...</span><span class="sxs-lookup"><span data-stu-id="1dd64-167">14,22,9,66,78,...</span></span> |<span data-ttu-id="1dd64-168">int[]</span><span class="sxs-lookup"><span data-stu-id="1dd64-168">int[]</span></span>|
|<span data-ttu-id="1dd64-169">Recursos</span><span class="sxs-lookup"><span data-stu-id="1dd64-169">Features</span></span>|<span data-ttu-id="1dd64-170">14,22,9,66,78,...</span><span class="sxs-lookup"><span data-stu-id="1dd64-170">14,22,9,66,78,...</span></span> |<span data-ttu-id="1dd64-171">int[600]</span><span class="sxs-lookup"><span data-stu-id="1dd64-171">int[600]</span></span>|

1. <span data-ttu-id="1dd64-172">Crie uma classe para seus `Main` dados de entrada, após o método:</span><span class="sxs-lookup"><span data-stu-id="1dd64-172">Create a class for your input data, after the `Main` method:</span></span>

    [!code-csharp[MovieReviewClass](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#MovieReviewClass "Declare movie review type")]

    <span data-ttu-id="1dd64-173">A classe de `MovieReview`dados `string` de entrada,`ReviewText`tem um para comentários de usuários ( ).</span><span class="sxs-lookup"><span data-stu-id="1dd64-173">The input data class, `MovieReview`, has a `string` for user comments (`ReviewText`).</span></span>

1. <span data-ttu-id="1dd64-174">Criar uma classe para as características `Main` de comprimento variável, após o método:</span><span class="sxs-lookup"><span data-stu-id="1dd64-174">Create a class for the variable length features, after the `Main` method:</span></span>

    [!code-csharp[VariableLengthFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    <span data-ttu-id="1dd64-175">A `VariableLengthFeatures` propriedade tem um atributo [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) para designá-la como vetor.</span><span class="sxs-lookup"><span data-stu-id="1dd64-175">The `VariableLengthFeatures` property has a [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) attribute to designate it as a vector.</span></span>  <span data-ttu-id="1dd64-176">Todos os elementos vetoriais devem ser do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="1dd64-176">All of the vector elements must be the same type.</span></span> <span data-ttu-id="1dd64-177">Em conjuntos de dados com um grande número de colunas, carregar várias colunas como um único vetor reduz o número de passes de dados quando você aplica transformações de dados.</span><span class="sxs-lookup"><span data-stu-id="1dd64-177">In data sets with a large number of columns, loading multiple columns as a single vector reduces the number of data passes when you apply data transformations.</span></span>

    <span data-ttu-id="1dd64-178">Esta classe é `ResizeFeatures` usada na ação.</span><span class="sxs-lookup"><span data-stu-id="1dd64-178">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="1dd64-179">Os nomes de suas propriedades (neste caso, apenas uma) são usados para indicar quais colunas no DataView podem ser usadas como _entrada_ para a ação de mapeamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="1dd64-179">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _input_ to the custom mapping action.</span></span>

1. <span data-ttu-id="1dd64-180">Criar uma classe para os recursos `Main` de comprimento fixo, após o método:</span><span class="sxs-lookup"><span data-stu-id="1dd64-180">Create a class for the fixed length features, after the `Main` method:</span></span>

    [!code-csharp[FixedLengthFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#FixedLengthFeatures)]

    <span data-ttu-id="1dd64-181">Esta classe é `ResizeFeatures` usada na ação.</span><span class="sxs-lookup"><span data-stu-id="1dd64-181">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="1dd64-182">Os nomes de suas propriedades (neste caso, apenas uma) são usados para indicar quais colunas no DataView podem ser usadas como a _saída_ da ação de mapeamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="1dd64-182">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _output_ of the custom mapping action.</span></span>

    <span data-ttu-id="1dd64-183">Observe que o nome `Features` da propriedade é determinado pelo modelo TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="1dd64-183">Note that the name of the property `Features` is determined by the TensorFlow model.</span></span> <span data-ttu-id="1dd64-184">Você não pode mudar este nome de propriedade.</span><span class="sxs-lookup"><span data-stu-id="1dd64-184">You cannot change this property name.</span></span>

1. <span data-ttu-id="1dd64-185">Criar uma classe para `Main` a previsão após o método:</span><span class="sxs-lookup"><span data-stu-id="1dd64-185">Create a class for the prediction after the `Main` method:</span></span>

    [!code-csharp[Prediction](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#Prediction "Declare prediction class")]

    <span data-ttu-id="1dd64-186">`MovieReviewSentimentPrediction` é a classe de previsão usada após o treinamento do modelo.</span><span class="sxs-lookup"><span data-stu-id="1dd64-186">`MovieReviewSentimentPrediction` is the prediction class used after the model training.</span></span> <span data-ttu-id="1dd64-187">`MovieReviewSentimentPrediction`tem uma `float` única`Prediction`matriz `VectorType` ( ) e um atributo.</span><span class="sxs-lookup"><span data-stu-id="1dd64-187">`MovieReviewSentimentPrediction` has a single `float` array (`Prediction`) and a `VectorType` attribute.</span></span>

### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a><span data-ttu-id="1dd64-188">Crie o MLContext, o dicionário de pesquisa e a ação para redimensionar os recursos</span><span class="sxs-lookup"><span data-stu-id="1dd64-188">Create the MLContext, lookup dictionary, and action to resize features</span></span>

<span data-ttu-id="1dd64-189">A [classe MLContext](xref:Microsoft.ML.MLContext) é um ponto de partida para todas as operações do ML.NET.</span><span class="sxs-lookup"><span data-stu-id="1dd64-189">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="1dd64-190">Inicializar `mlContext` cria um novo ambiente do ML.NET que pode ser compartilhado entre os objetos do fluxo de trabalho de criação de modelo.</span><span class="sxs-lookup"><span data-stu-id="1dd64-190">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="1dd64-191">Ele é semelhante, conceitualmente, a `DBContext` no Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="1dd64-191">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

1. <span data-ttu-id="1dd64-192">Substitua a linha `Console.WriteLine("Hello World!")` no método `Main` pelo seguinte código para declarar e inicializar a variável mlContext:</span><span class="sxs-lookup"><span data-stu-id="1dd64-192">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

   [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateMLContext "Create the ML Context")]

1. <span data-ttu-id="1dd64-193">Crie um dicionário para codificar palavras como [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) inteiros usando o método para carregar dados de mapeamento de um arquivo, como visto na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="1dd64-193">Create a dictionary to encode words as integers by using the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method to load mapping data from a file, as seen in the following table:</span></span>

    |<span data-ttu-id="1dd64-194">Word</span><span class="sxs-lookup"><span data-stu-id="1dd64-194">Word</span></span>     |<span data-ttu-id="1dd64-195">Índice</span><span class="sxs-lookup"><span data-stu-id="1dd64-195">Index</span></span>    |
    |---------|---------|
    |<span data-ttu-id="1dd64-196">Crianças</span><span class="sxs-lookup"><span data-stu-id="1dd64-196">kids</span></span>     |  <span data-ttu-id="1dd64-197">362</span><span class="sxs-lookup"><span data-stu-id="1dd64-197">362</span></span>    |
    |<span data-ttu-id="1dd64-198">desejar</span><span class="sxs-lookup"><span data-stu-id="1dd64-198">want</span></span>     |  <span data-ttu-id="1dd64-199">181</span><span class="sxs-lookup"><span data-stu-id="1dd64-199">181</span></span>    |
    |<span data-ttu-id="1dd64-200">Errado</span><span class="sxs-lookup"><span data-stu-id="1dd64-200">wrong</span></span>    |  <span data-ttu-id="1dd64-201">355</span><span class="sxs-lookup"><span data-stu-id="1dd64-201">355</span></span>    |
    |<span data-ttu-id="1dd64-202">effects</span><span class="sxs-lookup"><span data-stu-id="1dd64-202">effects</span></span>  |  <span data-ttu-id="1dd64-203">302</span><span class="sxs-lookup"><span data-stu-id="1dd64-203">302</span></span>    |
    |<span data-ttu-id="1dd64-204">Sentimento</span><span class="sxs-lookup"><span data-stu-id="1dd64-204">feeling</span></span>  |  <span data-ttu-id="1dd64-205">547</span><span class="sxs-lookup"><span data-stu-id="1dd64-205">547</span></span>    |

    <span data-ttu-id="1dd64-206">Adicione o código abaixo para criar o mapa de procuração:</span><span class="sxs-lookup"><span data-stu-id="1dd64-206">Add the code below to create the lookup map:</span></span>

    [!code-csharp[CreateLookupMap](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateLookupMap)]

1. <span data-ttu-id="1dd64-207">Adicione `Action` um para redimensionar a matriz de inteiros de palavras de comprimento variável a uma matriz inteira de tamanho fixo, com as próximas linhas de código:</span><span class="sxs-lookup"><span data-stu-id="1dd64-207">Add an `Action` to resize the variable length word integer array to an integer array of fixed size, with the next lines of code:</span></span>

   [!code-csharp[ResizeFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a><span data-ttu-id="1dd64-208">Carregar o modelo TensorFlow pré-treinado</span><span class="sxs-lookup"><span data-stu-id="1dd64-208">Load the pre-trained TensorFlow model</span></span>

1. <span data-ttu-id="1dd64-209">Adicionar código para carregar o modelo TensorFlow:</span><span class="sxs-lookup"><span data-stu-id="1dd64-209">Add code to load the TensorFlow model:</span></span>

    [!code-csharp[LoadTensorFlowModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#LoadTensorFlowModel)]

    <span data-ttu-id="1dd64-210">Uma vez que o modelo é carregado, você pode extrair seu esquema de entrada e saída.</span><span class="sxs-lookup"><span data-stu-id="1dd64-210">Once the model is loaded, you can extract its input and output schema.</span></span> <span data-ttu-id="1dd64-211">Os esquemas são exibidos apenas por interesse e aprendizado.</span><span class="sxs-lookup"><span data-stu-id="1dd64-211">The schemas are displayed for interest and learning only.</span></span> <span data-ttu-id="1dd64-212">Você não precisa deste código para que a aplicação final funcione:</span><span class="sxs-lookup"><span data-stu-id="1dd64-212">You do not need this code for the final application to function:</span></span>

    [!code-csharp[GetModelSchema](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#GetModelSchema)]

    <span data-ttu-id="1dd64-213">O esquema de entrada é a matriz de comprimento fixo de palavras codificadas inteiros.</span><span class="sxs-lookup"><span data-stu-id="1dd64-213">The input schema is the fixed-length array of integer encoded words.</span></span> <span data-ttu-id="1dd64-214">O esquema de saída é uma matriz flutuante de probabilidades indicando se o sentimento de uma revisão é negativo ou positivo .</span><span class="sxs-lookup"><span data-stu-id="1dd64-214">The output schema is a float array of probabilities indicating whether a review's sentiment is negative, or positive .</span></span> <span data-ttu-id="1dd64-215">Esses valores somam-se a 1, pois a probabilidade de ser positivo é o complemento da probabilidade de o sentimento ser negativo.</span><span class="sxs-lookup"><span data-stu-id="1dd64-215">These values sum to 1, as the probability of being positive is the complement of the probability of the sentiment being negative.</span></span>

## <a name="create-the-mlnet-pipeline"></a><span data-ttu-id="1dd64-216">Crie o ML.NET pipeline</span><span class="sxs-lookup"><span data-stu-id="1dd64-216">Create the ML.NET pipeline</span></span>

1. <span data-ttu-id="1dd64-217">Crie o pipeline e divida o texto de entrada em palavras usando [tokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transformar para quebrar o texto em palavras como a próxima linha de código:</span><span class="sxs-lookup"><span data-stu-id="1dd64-217">Create the pipeline and split the input text into words using [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform to break the text into words as the next line of code:</span></span>

   [!code-csharp[TokenizeIntoWords](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#TokenizeIntoWords)]

   <span data-ttu-id="1dd64-218">A transformação [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) usa espaços para analisar o texto/string em palavras.</span><span class="sxs-lookup"><span data-stu-id="1dd64-218">The [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform uses spaces to parse the text/string into words.</span></span> <span data-ttu-id="1dd64-219">Ele cria uma nova coluna e divide cada seqüência de entrada para um vetor de substrings com base no separador definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="1dd64-219">It creates a new column and splits each input string to a vector of substrings based on the user-defined separator.</span></span>

1. <span data-ttu-id="1dd64-220">Mapeie as palavras em sua codificação de inteiros usando a tabela de pesquisa que você declarou acima:</span><span class="sxs-lookup"><span data-stu-id="1dd64-220">Map the words onto their integer encoding using the lookup table that you declared above:</span></span>

    [!code-csharp[MapValue](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#MapValue)]

1. <span data-ttu-id="1dd64-221">Redimensione as codificações de inteiro de comprimento variável para o comprimento fixo exigido pelo modelo:</span><span class="sxs-lookup"><span data-stu-id="1dd64-221">Resize the variable length integer encodings to the fixed-length one required by the model:</span></span>

    [!code-csharp[CustomMapping](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CustomMapping)]

1. <span data-ttu-id="1dd64-222">Classifique a entrada com o modelo TensorFlow carregado:</span><span class="sxs-lookup"><span data-stu-id="1dd64-222">Classify the input with the loaded TensorFlow model:</span></span>

    [!code-csharp[ScoreTensorFlowModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="1dd64-223">A saída do modelo `Prediction/Softmax`TensorFlow é chamada .</span><span class="sxs-lookup"><span data-stu-id="1dd64-223">The TensorFlow model output is called `Prediction/Softmax`.</span></span> <span data-ttu-id="1dd64-224">Observe que `Prediction/Softmax` o nome é determinado pelo modelo TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="1dd64-224">Note that the name `Prediction/Softmax` is determined by the TensorFlow model.</span></span> <span data-ttu-id="1dd64-225">Você não pode mudar este nome.</span><span class="sxs-lookup"><span data-stu-id="1dd64-225">You cannot change this name.</span></span>

1. <span data-ttu-id="1dd64-226">Criar uma nova coluna para a previsão de saída:</span><span class="sxs-lookup"><span data-stu-id="1dd64-226">Create a new column for the output prediction:</span></span>

    [!code-csharp[SnippetCopyColumns](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#SnippetCopyColumns)]

    <span data-ttu-id="1dd64-227">Você precisa copiar `Prediction/Softmax` a coluna em uma com um nome que pode `Prediction`ser usado como propriedade em uma classe C#: .</span><span class="sxs-lookup"><span data-stu-id="1dd64-227">You need to copy the `Prediction/Softmax` column into one with a name that can be used as a property in a C# class: `Prediction`.</span></span> <span data-ttu-id="1dd64-228">O `/` personagem não é permitido em um nome de propriedade C#.</span><span class="sxs-lookup"><span data-stu-id="1dd64-228">The `/` character is not allowed in a C# property name.</span></span>

## <a name="create-the-mlnet-model-from-the-pipeline"></a><span data-ttu-id="1dd64-229">Crie o modelo ML.NET a partir do pipeline</span><span class="sxs-lookup"><span data-stu-id="1dd64-229">Create the ML.NET model from the pipeline</span></span>

1. <span data-ttu-id="1dd64-230">Adicione o código para criar o modelo a partir do pipeline:</span><span class="sxs-lookup"><span data-stu-id="1dd64-230">Add the code to create the model from the pipeline:</span></span>

    [!code-csharp[SnippetCreateModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#SnippetCreateModel)]

    <span data-ttu-id="1dd64-231">Um modelo ML.NET é criado a partir da cadeia de `Fit` estimadores no pipeline, chamando o método.</span><span class="sxs-lookup"><span data-stu-id="1dd64-231">An ML.NET model is created from the chain of estimators in the pipeline by calling the `Fit` method.</span></span> <span data-ttu-id="1dd64-232">Neste caso, não estamos adaptando nenhum dado para criar o modelo, já que o modelo TensorFlow já foi previamente treinado.</span><span class="sxs-lookup"><span data-stu-id="1dd64-232">In this case, we are not fitting any data to create the model, as the TensorFlow model has already been previously trained.</span></span> <span data-ttu-id="1dd64-233">Fornecemos um objeto de exibição de `Fit` dados vazio para satisfazer os requisitos do método.</span><span class="sxs-lookup"><span data-stu-id="1dd64-233">We supply an empty data view object to satisfy the requirements of the `Fit` method.</span></span>

## <a name="use-the-model-to-make-a-prediction"></a><span data-ttu-id="1dd64-234">Usar o modelo para fazer uma previsão</span><span class="sxs-lookup"><span data-stu-id="1dd64-234">Use the model to make a prediction</span></span>

1. <span data-ttu-id="1dd64-235">Adicione `PredictSentiment` o método `Main` abaixo do método:</span><span class="sxs-lookup"><span data-stu-id="1dd64-235">Add the `PredictSentiment` method below the `Main` method:</span></span>

    ```csharp
    public static void PredictSentiment(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="1dd64-236">Adicione o seguinte código `PredictionEngine` para criar a `PredictSentiment()` primeira linha do método:</span><span class="sxs-lookup"><span data-stu-id="1dd64-236">Add the following code to create the `PredictionEngine` as the first line in the `PredictSentiment()` method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreatePredictionEngine)]

    <span data-ttu-id="1dd64-237">O [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) é uma API de conveniência, que permite realizar uma previsão em uma única instância de dados.</span><span class="sxs-lookup"><span data-stu-id="1dd64-237">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="1dd64-238">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)não é seguro para rosca.</span><span class="sxs-lookup"><span data-stu-id="1dd64-238">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="1dd64-239">É aceitável usar em ambientes de um único fio ou protótipo.</span><span class="sxs-lookup"><span data-stu-id="1dd64-239">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="1dd64-240">Para melhorar o desempenho e a segurança `PredictionEnginePool` dos fios nos [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) ambientes de produção, use o serviço, que cria um objeto para uso em toda a sua aplicação.</span><span class="sxs-lookup"><span data-stu-id="1dd64-240">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="1dd64-241">Consulte este guia sobre como [usar `PredictionEnginePool` em uma API web ASP.NET.](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)</span><span class="sxs-lookup"><span data-stu-id="1dd64-241">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="1dd64-242">A extensão de serviço `PredictionEnginePool` está atualmente em versão prévia.</span><span class="sxs-lookup"><span data-stu-id="1dd64-242">`PredictionEnginePool` service extension is currently in preview.</span></span>

1. <span data-ttu-id="1dd64-243">Adicione um comentário para testar as previsões do modelo treinado no método `Predict()` ao criar uma instância de `MovieReview`:</span><span class="sxs-lookup"><span data-stu-id="1dd64-243">Add a comment to test the trained model's prediction in the `Predict()` method by creating an instance of `MovieReview`:</span></span>

    [!code-csharp[CreateTestData](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateTestData)]

1. <span data-ttu-id="1dd64-244">Passe os dados de `Prediction Engine` comentário do teste para `PredictSentiment()` o adicionando as próximas linhas de código no método:</span><span class="sxs-lookup"><span data-stu-id="1dd64-244">Pass the test comment data to the `Prediction Engine` by adding the next lines of code in the `PredictSentiment()` method:</span></span>

    [!code-csharp[Predict](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#Predict)]

1. <span data-ttu-id="1dd64-245">A função [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) faz uma previsão em uma única linha de dados:</span><span class="sxs-lookup"><span data-stu-id="1dd64-245">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

    |<span data-ttu-id="1dd64-246">Propriedade</span><span class="sxs-lookup"><span data-stu-id="1dd64-246">Property</span></span>| <span data-ttu-id="1dd64-247">Valor</span><span class="sxs-lookup"><span data-stu-id="1dd64-247">Value</span></span>|<span data-ttu-id="1dd64-248">Type</span><span class="sxs-lookup"><span data-stu-id="1dd64-248">Type</span></span>|
    |-------------|-----------------------|------|
    |<span data-ttu-id="1dd64-249">Previsão</span><span class="sxs-lookup"><span data-stu-id="1dd64-249">Prediction</span></span>|<span data-ttu-id="1dd64-250">[0.5459937, 0.454006255]</span><span class="sxs-lookup"><span data-stu-id="1dd64-250">[0.5459937, 0.454006255]</span></span>|<span data-ttu-id="1dd64-251">flutuar[]</span><span class="sxs-lookup"><span data-stu-id="1dd64-251">float[]</span></span>|

1. <span data-ttu-id="1dd64-252">Exibir a previsão de sentimento usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="1dd64-252">Display sentiment prediction using the following code:</span></span>

    [!code-csharp[DisplayPredictions](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#DisplayPredictions)]

1. <span data-ttu-id="1dd64-253">Adicionar uma `PredictSentiment` chamada ao final `Main` do método:</span><span class="sxs-lookup"><span data-stu-id="1dd64-253">Add a call to `PredictSentiment` at the end of the `Main` method:</span></span>

    [!code-csharp[CallPredictSentiment](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CallPredictSentiment)]

## <a name="results"></a><span data-ttu-id="1dd64-254">Resultados</span><span class="sxs-lookup"><span data-stu-id="1dd64-254">Results</span></span>

<span data-ttu-id="1dd64-255">Compile e execute seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1dd64-255">Build and run your application.</span></span>

<span data-ttu-id="1dd64-256">Seus resultados devem ser semelhantes aos seguintes.</span><span class="sxs-lookup"><span data-stu-id="1dd64-256">Your results should be similar to the following.</span></span> <span data-ttu-id="1dd64-257">Durante o processamento, as mensagens são exibidas.</span><span class="sxs-lookup"><span data-stu-id="1dd64-257">During processing, messages are displayed.</span></span> <span data-ttu-id="1dd64-258">Você pode ver avisos ou mensagens de processamento.</span><span class="sxs-lookup"><span data-stu-id="1dd64-258">You may see warnings, or processing messages.</span></span> <span data-ttu-id="1dd64-259">Essas mensagens foram removidas dos resultados a seguir para ficar mais claro.</span><span class="sxs-lookup"><span data-stu-id="1dd64-259">These messages have been removed from the following results for clarity.</span></span>

```console
Number of classes: 2
Is sentiment/review positive ? Yes
```

<span data-ttu-id="1dd64-260">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="1dd64-260">Congratulations!</span></span> <span data-ttu-id="1dd64-261">Agora você construiu com sucesso um modelo de aprendizado de máquina para classificar `TensorFlow` e prever o sentimento das mensagens reutilizando um modelo pré-treinado em ML.NET.</span><span class="sxs-lookup"><span data-stu-id="1dd64-261">You've now successfully built a machine learning model for classifying and predicting messages sentiment by reusing a pre-trained `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="1dd64-262">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF).</span><span class="sxs-lookup"><span data-stu-id="1dd64-262">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

<span data-ttu-id="1dd64-263">Neste tutorial, você aprendeu a:</span><span class="sxs-lookup"><span data-stu-id="1dd64-263">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="1dd64-264">Carregue um modelo TensorFlow pré-treinado</span><span class="sxs-lookup"><span data-stu-id="1dd64-264">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="1dd64-265">Transforme o texto de comentário do site em recursos adequados para o modelo</span><span class="sxs-lookup"><span data-stu-id="1dd64-265">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="1dd64-266">Usar o modelo para fazer uma previsão</span><span class="sxs-lookup"><span data-stu-id="1dd64-266">Use the model to make a prediction</span></span>
