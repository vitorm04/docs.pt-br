---
title: 'Tutorial: analisar comentários do site-classificação binária'
description: Este tutorial mostra como criar um aplicativo de console do .NET Core que classifica sentimentos de comentários de um site e executa a ação adequada. O classificador binário de sentimento usa C# no Visual Studio.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: b193752437c3e84476858bb3b70ba642d8562769
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803242"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a><span data-ttu-id="58df7-104">Tutorial: analisar o sentimentos dos comentários do site com a classificação binária no ML.NET</span><span class="sxs-lookup"><span data-stu-id="58df7-104">Tutorial: Analyze sentiment of website comments with binary classification in ML.NET</span></span>

<span data-ttu-id="58df7-105">Este tutorial mostra como criar um aplicativo de console do .NET Core que classifica sentimentos de comentários de um site e executa a ação adequada.</span><span class="sxs-lookup"><span data-stu-id="58df7-105">This tutorial shows you how to create a .NET Core console application that classifies sentiment from website comments and takes the appropriate action.</span></span> <span data-ttu-id="58df7-106">O classificador binário de sentimento usa C# no Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="58df7-106">The binary sentiment classifier uses C# in Visual Studio 2017.</span></span>

<span data-ttu-id="58df7-107">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="58df7-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="58df7-108">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="58df7-108">Create a console application</span></span>
> - <span data-ttu-id="58df7-109">Preparar os dados</span><span class="sxs-lookup"><span data-stu-id="58df7-109">Prepare data</span></span>
> - <span data-ttu-id="58df7-110">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="58df7-110">Load the data</span></span>
> - <span data-ttu-id="58df7-111">Criar e treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="58df7-111">Build and train the model</span></span>
> - <span data-ttu-id="58df7-112">Avalie o modelo</span><span class="sxs-lookup"><span data-stu-id="58df7-112">Evaluate the model</span></span>
> - <span data-ttu-id="58df7-113">Usar o modelo para fazer uma previsão</span><span class="sxs-lookup"><span data-stu-id="58df7-113">Use the model to make a prediction</span></span>
> - <span data-ttu-id="58df7-114">Confira os resultados</span><span class="sxs-lookup"><span data-stu-id="58df7-114">See the results</span></span>

<span data-ttu-id="58df7-115">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis).</span><span class="sxs-lookup"><span data-stu-id="58df7-115">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="58df7-116">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="58df7-116">Prerequisites</span></span>

- <span data-ttu-id="58df7-117">[Visual Studio 2017 versão 15,6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) com a carga de trabalho "desenvolvimento de plataforma cruzada do .NET Core" instalada</span><span class="sxs-lookup"><span data-stu-id="58df7-117">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed</span></span>

- <span data-ttu-id="58df7-118">[Conjunto de dados de Sentenças de sentimentos rotuladas da UCI](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (arquivo zip)</span><span class="sxs-lookup"><span data-stu-id="58df7-118">[UCI Sentiment Labeled Sentences dataset](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP file)</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="58df7-119">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="58df7-119">Create a console application</span></span>

1. <span data-ttu-id="58df7-120">Crie um **Aplicativo de console do .NET Core** chamado "SentimentAnalysis".</span><span class="sxs-lookup"><span data-stu-id="58df7-120">Create a **.NET Core Console Application** called "SentimentAnalysis".</span></span>

2. <span data-ttu-id="58df7-121">Crie um diretório chamado *dados* em seu projeto para salvar os arquivos do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="58df7-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="58df7-122">Instalar o **Pacote NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="58df7-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    <span data-ttu-id="58df7-123">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="58df7-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="58df7-124">Escolha "nuget.org" como a origem do pacote e, em seguida, selecione a guia **procurar** . procure **Microsoft.ml**, selecione o pacote desejado e, em seguida, selecione o botão **instalar** .</span><span class="sxs-lookup"><span data-stu-id="58df7-124">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="58df7-125">Prossiga com a instalação concordando com os termos de licença do pacote que você escolher.</span><span class="sxs-lookup"><span data-stu-id="58df7-125">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="58df7-126">Preparar seus dados</span><span class="sxs-lookup"><span data-stu-id="58df7-126">Prepare your data</span></span>

> [!NOTE]
> <span data-ttu-id="58df7-127">Os conjuntos de dados deste tutorial são de "From Group to Individual Labels using Deep Features”, Kotzias et.</span><span class="sxs-lookup"><span data-stu-id="58df7-127">The datasets for this tutorial are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="58df7-128">al,.</span><span class="sxs-lookup"><span data-stu-id="58df7-128">al,.</span></span> <span data-ttu-id="58df7-129">KDD 2015 e hospedado na UCI Machine Learning Repository-Dua, D. e Karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="58df7-129">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="58df7-130">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span><span class="sxs-lookup"><span data-stu-id="58df7-130">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="58df7-131">Irvine, CA: University of California, School of Information and Computer Science.</span><span class="sxs-lookup"><span data-stu-id="58df7-131">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

1. <span data-ttu-id="58df7-132">Baixe o [arquivo zip do conjunto de dados de Sentenças de sentimentos rotuladas da UCI](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) e descompacte-o.</span><span class="sxs-lookup"><span data-stu-id="58df7-132">Download [UCI Sentiment Labeled Sentences dataset ZIP file](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="58df7-133">Copie o arquivo `yelp_labelled.txt` para o diretório *Dados* que você criou.</span><span class="sxs-lookup"><span data-stu-id="58df7-133">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

3. <span data-ttu-id="58df7-134">No Gerenciador de Soluções, clique com o botão direito do mouse no arquivo `yelp_labeled.txt` e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="58df7-134">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="58df7-135">Em **avançado**, altere o valor de **copiar para diretório de saída** para **copiar se mais recente**.</span><span class="sxs-lookup"><span data-stu-id="58df7-135">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="58df7-136">Criar classes e definir demarcadores</span><span class="sxs-lookup"><span data-stu-id="58df7-136">Create classes and define paths</span></span>

1. <span data-ttu-id="58df7-137">Adicione as seguintes instruções `using` adicionais ao início do arquivo *Program.cs*: </span><span class="sxs-lookup"><span data-stu-id="58df7-137">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="58df7-138">Adicione o seguinte código à linha à direita acima do `Main` método, para criar um campo para manter o caminho do arquivo do conjunto de código baixado recentemente:</span><span class="sxs-lookup"><span data-stu-id="58df7-138">Add the following code to the line right above the `Main` method, to create a field to hold the recently downloaded dataset file path:</span></span>

    [!code-csharp[Declare global variables](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

1. <span data-ttu-id="58df7-139">Em seguida, crie classes para os dados de entrada e as previsões.</span><span class="sxs-lookup"><span data-stu-id="58df7-139">Next, create classes for your input data and predictions.</span></span> <span data-ttu-id="58df7-140">Adicione uma nova classe ao seu projeto:</span><span class="sxs-lookup"><span data-stu-id="58df7-140">Add a new class to your project:</span></span>

    - <span data-ttu-id="58df7-141">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="58df7-141">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

    - <span data-ttu-id="58df7-142">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="58df7-142">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="58df7-143">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="58df7-143">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="58df7-144">O arquivo *SentimentData.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="58df7-144">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="58df7-145">Adicione a seguinte instrução `using` acima de *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="58df7-145">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="58df7-146">Remova a definição de classe existente e adicione o seguinte código, que possui duas classes `SentimentData` e `SentimentPrediction`, ao arquivo *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="58df7-146">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a><span data-ttu-id="58df7-147">Como os dados foram preparados</span><span class="sxs-lookup"><span data-stu-id="58df7-147">How the data was prepared</span></span>

<span data-ttu-id="58df7-148">A classe de conjunto de dados de entrada, `SentimentData`, tem um `string` para comentários do usuário (`SentimentText`) e um valor `bool` (`Sentiment`) de 1 (positivo) ou 0 (negativo) para sentimento.</span><span class="sxs-lookup"><span data-stu-id="58df7-148">The input dataset class, `SentimentData`, has a `string` for user comments (`SentimentText`) and a `bool` (`Sentiment`) value of either 1 (positive) or 0 (negative) for sentiment.</span></span> <span data-ttu-id="58df7-149">Ambos os campos têm atributos [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) anexados a eles, que descrevem a ordem do arquivo de dados de cada campo.</span><span class="sxs-lookup"><span data-stu-id="58df7-149">Both fields have [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attributes attached to them, which describes the data file order of each field.</span></span>  <span data-ttu-id="58df7-150">Além disso, a propriedade `Sentiment` tem um atributo [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) para designá-lo como o campo `Label`.</span><span class="sxs-lookup"><span data-stu-id="58df7-150">In addition, the `Sentiment` property has a [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) attribute to designate it as the `Label` field.</span></span> <span data-ttu-id="58df7-151">O arquivo de exemplo a seguir não possui uma linha de cabeçalho e tem a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="58df7-151">The following example file doesn't have a header row, and looks like this:</span></span>

|<span data-ttu-id="58df7-152">SentimentText</span><span class="sxs-lookup"><span data-stu-id="58df7-152">SentimentText</span></span>                         |<span data-ttu-id="58df7-153">Sentimento (rótulo)</span><span class="sxs-lookup"><span data-stu-id="58df7-153">Sentiment (Label)</span></span> |
|--------------------------------------|----------|
|<span data-ttu-id="58df7-154">A garçonete foi um pouco lenta no serviço.</span><span class="sxs-lookup"><span data-stu-id="58df7-154">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="58df7-155">0</span><span class="sxs-lookup"><span data-stu-id="58df7-155">0</span></span>     |
|<span data-ttu-id="58df7-156">A torrada não é boa.</span><span class="sxs-lookup"><span data-stu-id="58df7-156">Crust is not good.</span></span>                    |    <span data-ttu-id="58df7-157">0</span><span class="sxs-lookup"><span data-stu-id="58df7-157">0</span></span>     |
|<span data-ttu-id="58df7-158">Wow... Adorei este lugar.</span><span class="sxs-lookup"><span data-stu-id="58df7-158">Wow... Loved this place.</span></span>              |    <span data-ttu-id="58df7-159">1</span><span class="sxs-lookup"><span data-stu-id="58df7-159">1</span></span>     |
|<span data-ttu-id="58df7-160">O serviço era muito rápido.</span><span class="sxs-lookup"><span data-stu-id="58df7-160">Service was very prompt.</span></span>              |    <span data-ttu-id="58df7-161">1</span><span class="sxs-lookup"><span data-stu-id="58df7-161">1</span></span>     |

<span data-ttu-id="58df7-162">`SentimentPrediction` é a classe de previsão usada após o treinamento do modelo.</span><span class="sxs-lookup"><span data-stu-id="58df7-162">`SentimentPrediction` is the prediction class used after model training.</span></span> <span data-ttu-id="58df7-163">Ela herda `SentimentData` de modo que a entrada `SentimentText` possa ser exibida junto com a previsão de saída.</span><span class="sxs-lookup"><span data-stu-id="58df7-163">It inherits from `SentimentData` so that the input `SentimentText` can be displayed along with the output prediction.</span></span> <span data-ttu-id="58df7-164">O booliano `Prediction` é o valor que o modelo prevê quando fornecido com a nova entrada `SentimentText`.</span><span class="sxs-lookup"><span data-stu-id="58df7-164">The `Prediction` boolean is the value that the model predicts when supplied with new input `SentimentText`.</span></span>

<span data-ttu-id="58df7-165">A classe de saída `SentimentPrediction` contém duas outras propriedades calculadas pelo modelo: `Score` – a pontuação bruta calculada pelo modelo e `Probability` – a pontuação calibrada para a probabilidade de o texto ter sentimento positivo.</span><span class="sxs-lookup"><span data-stu-id="58df7-165">The output class `SentimentPrediction` contains two other properties calculated by the model: `Score` - the raw score calculated by the model, and `Probability` - the score calibrated to the likelihood of the text having positive sentiment.</span></span>

<span data-ttu-id="58df7-166">Para este tutorial, a propriedade mais importante é `Prediction`.</span><span class="sxs-lookup"><span data-stu-id="58df7-166">For this tutorial, the most important property is `Prediction`.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="58df7-167">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="58df7-167">Load the data</span></span>

<span data-ttu-id="58df7-168">Os dados do ML.NET são representados como uma [classe IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="58df7-168">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="58df7-169">`IDataView` é uma maneira flexível e eficiente de descrever dados tabulares (numéricos e texto).</span><span class="sxs-lookup"><span data-stu-id="58df7-169">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="58df7-170">Os dados podem ser carregados de um arquivo de texto ou em tempo real (por exemplo, banco de dados SQL ou arquivos de log) para um objeto `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="58df7-170">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="58df7-171">A [classe MLContext](xref:Microsoft.ML.MLContext) é um ponto de partida para todas as operações do ML.NET.</span><span class="sxs-lookup"><span data-stu-id="58df7-171">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="58df7-172">Inicializar `mlContext` cria um novo ambiente do ML.NET que pode ser compartilhado entre os objetos do fluxo de trabalho de criação de modelo.</span><span class="sxs-lookup"><span data-stu-id="58df7-172">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="58df7-173">Ele é semelhante, conceitualmente, a `DBContext` no Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="58df7-173">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="58df7-174">Você prepara o aplicativo e, em seguida, carrega os dados:</span><span class="sxs-lookup"><span data-stu-id="58df7-174">You prepare the app, and then load data:</span></span>

1. <span data-ttu-id="58df7-175">Substitua a linha `Console.WriteLine("Hello World!")` no método `Main` pelo seguinte código para declarar e inicializar a variável mlContext:</span><span class="sxs-lookup"><span data-stu-id="58df7-175">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

    [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateMLContext "Create the ML Context")]

2. <span data-ttu-id="58df7-176">Adicione o seguinte como a linha seguinte de código no método `Main()`:</span><span class="sxs-lookup"><span data-stu-id="58df7-176">Add the following as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallLoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallLoadData)]

3. <span data-ttu-id="58df7-177">Crie o método `LoadData()`, logo após o método `Main()`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="58df7-177">Create the `LoadData()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    <span data-ttu-id="58df7-178">O método `LoadData()` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="58df7-178">The `LoadData()` method executes the following tasks:</span></span>

    - <span data-ttu-id="58df7-179">Carrega os dados.</span><span class="sxs-lookup"><span data-stu-id="58df7-179">Loads the data.</span></span>
    - <span data-ttu-id="58df7-180">Divide o conjunto de dados carregado em conjuntos de treinamento e teste.</span><span class="sxs-lookup"><span data-stu-id="58df7-180">Splits the loaded dataset into train and test datasets.</span></span>
    - <span data-ttu-id="58df7-181">Retorna os conjuntos de treinamento e teste.</span><span class="sxs-lookup"><span data-stu-id="58df7-181">Returns the split train and test datasets.</span></span>

4. <span data-ttu-id="58df7-182">Adicione o seguinte código como a primeira linha do método `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="58df7-182">Add the following code as the first line of the `LoadData()` method:</span></span>

    [!code-csharp[LoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="58df7-183">O método [LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) define o esquema de dados e lê o arquivo.</span><span class="sxs-lookup"><span data-stu-id="58df7-183">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) method defines the data schema and reads in the file.</span></span> <span data-ttu-id="58df7-184">Ele usa as variáveis de caminho de dados e retorna uma `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="58df7-184">It takes in the data path variables and returns an `IDataView`.</span></span>

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="58df7-185">Dividir o conjunto de dados para o modelo de treinamento e de teste</span><span class="sxs-lookup"><span data-stu-id="58df7-185">Split the dataset for model training and testing</span></span>

<span data-ttu-id="58df7-186">Ao preparar um modelo, você usa parte do conjunto de dados para treiná-lo e parte do conjunto de dados para testar a precisão do modelo.</span><span class="sxs-lookup"><span data-stu-id="58df7-186">When preparing a model, you use part of the dataset to train it and part of the dataset to test the model's accuracy.</span></span>

1. <span data-ttu-id="58df7-187">Para dividir os dados carregados nos conjuntos de dados necessários, adicione o seguinte código como a próxima linha no método `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="58df7-187">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData()` method:</span></span>

    [!code-csharp[SplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#SplitData "Split the Data")]

    <span data-ttu-id="58df7-188">O código anterior usa o método [TrainTestSplit ()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) para dividir o DataSet carregado em conjuntos de valores de teste e de treinamento e retorná-los na <xref:Microsoft.ML.DataOperationsCatalog.TrainTestData> classe.</span><span class="sxs-lookup"><span data-stu-id="58df7-188">The previous code uses the [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the loaded dataset into train and test datasets and return them in the <xref:Microsoft.ML.DataOperationsCatalog.TrainTestData> class.</span></span> <span data-ttu-id="58df7-189">Especifique o percentual de dados do conjunto de teste com o parâmetro `testFraction`.</span><span class="sxs-lookup"><span data-stu-id="58df7-189">Specify the test set percentage of data with the `testFraction`parameter.</span></span> <span data-ttu-id="58df7-190">O padrão é 10% e, nesse caso, você usa 20% para avaliar mais dados.</span><span class="sxs-lookup"><span data-stu-id="58df7-190">The default is 10%, in this case you use 20% to evaluate more data.</span></span>

2. <span data-ttu-id="58df7-191">Retorne o `splitDataView` no final do método `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="58df7-191">Return the `splitDataView` at the end of the `LoadData()` method:</span></span>

    [!code-csharp[ReturnSplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="58df7-192">Criar e treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="58df7-192">Build and train the model</span></span>

1. <span data-ttu-id="58df7-193">Adicione a seguinte chamada ao método `BuildAndTrainModel` como a próxima linha de código no método `Main()`:</span><span class="sxs-lookup"><span data-stu-id="58df7-193">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallBuildAndTrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallBuildAndTrainModel)]

    <span data-ttu-id="58df7-194">O método `BuildAndTrainModel()` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="58df7-194">The `BuildAndTrainModel()` method executes the following tasks:</span></span>

    - <span data-ttu-id="58df7-195">Extrai e transforma os dados.</span><span class="sxs-lookup"><span data-stu-id="58df7-195">Extracts and transforms the data.</span></span>
    - <span data-ttu-id="58df7-196">Treina o modelo.</span><span class="sxs-lookup"><span data-stu-id="58df7-196">Trains the model.</span></span>
    - <span data-ttu-id="58df7-197">Prevê o sentimento com base nos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="58df7-197">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="58df7-198">Retorna o modelo.</span><span class="sxs-lookup"><span data-stu-id="58df7-198">Returns the model.</span></span>

2. <span data-ttu-id="58df7-199">Crie o método `BuildAndTrainModel()`, logo após o método `Main()`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="58df7-199">Create the `BuildAndTrainModel()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a><span data-ttu-id="58df7-200">Extrair e transformar os dados</span><span class="sxs-lookup"><span data-stu-id="58df7-200">Extract and transform the data</span></span>

1. <span data-ttu-id="58df7-201">Chame `FeaturizeText` como a próxima linha de código:</span><span class="sxs-lookup"><span data-stu-id="58df7-201">Call `FeaturizeText` as the next line of code:</span></span>

    [!code-csharp[FeaturizeText](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#FeaturizeText "Featurize the text")]

    <span data-ttu-id="58df7-202">O método `FeaturizeText()` no código anterior converte a coluna de texto (`SentimentText`) em uma coluna `Features` do tipo chave numérica usada pelo algoritmo de aprendizado de máquina, adicionando-a como uma nova coluna do conjunto de dados:</span><span class="sxs-lookup"><span data-stu-id="58df7-202">The `FeaturizeText()` method in the previous code converts the text column (`SentimentText`) into a numeric key type `Features` column used by the machine learning algorithm and adds it as a new dataset column:</span></span>

    |<span data-ttu-id="58df7-203">SentimentText</span><span class="sxs-lookup"><span data-stu-id="58df7-203">SentimentText</span></span>                         |<span data-ttu-id="58df7-204">Sentimento</span><span class="sxs-lookup"><span data-stu-id="58df7-204">Sentiment</span></span> |<span data-ttu-id="58df7-205">Recursos</span><span class="sxs-lookup"><span data-stu-id="58df7-205">Features</span></span>              |
    |--------------------------------------|----------|----------------------|
    |<span data-ttu-id="58df7-206">A garçonete foi um pouco lenta no serviço.</span><span class="sxs-lookup"><span data-stu-id="58df7-206">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="58df7-207">0</span><span class="sxs-lookup"><span data-stu-id="58df7-207">0</span></span>     |<span data-ttu-id="58df7-208">[0,76, 0,65, 0,44, …]</span><span class="sxs-lookup"><span data-stu-id="58df7-208">[0.76, 0.65, 0.44, …]</span></span> |
    |<span data-ttu-id="58df7-209">A torrada não é boa.</span><span class="sxs-lookup"><span data-stu-id="58df7-209">Crust is not good.</span></span>                    |    <span data-ttu-id="58df7-210">0</span><span class="sxs-lookup"><span data-stu-id="58df7-210">0</span></span>     |<span data-ttu-id="58df7-211">[0,98, 0,43, 0,54, …]</span><span class="sxs-lookup"><span data-stu-id="58df7-211">[0.98, 0.43, 0.54, …]</span></span> |
    |<span data-ttu-id="58df7-212">Wow... Adorei este lugar.</span><span class="sxs-lookup"><span data-stu-id="58df7-212">Wow... Loved this place.</span></span>              |    <span data-ttu-id="58df7-213">1</span><span class="sxs-lookup"><span data-stu-id="58df7-213">1</span></span>     |<span data-ttu-id="58df7-214">[0,35, 0,73, 0,46, …]</span><span class="sxs-lookup"><span data-stu-id="58df7-214">[0.35, 0.73, 0.46, …]</span></span> |
    |<span data-ttu-id="58df7-215">O serviço era muito rápido.</span><span class="sxs-lookup"><span data-stu-id="58df7-215">Service was very prompt.</span></span>              |    <span data-ttu-id="58df7-216">1</span><span class="sxs-lookup"><span data-stu-id="58df7-216">1</span></span>     |<span data-ttu-id="58df7-217">[0,39, 0, 0,75, …]</span><span class="sxs-lookup"><span data-stu-id="58df7-217">[0.39, 0, 0.75, …]</span></span>    |

### <a name="add-a-learning-algorithm"></a><span data-ttu-id="58df7-218">Adicionar um algoritmo de aprendizado</span><span class="sxs-lookup"><span data-stu-id="58df7-218">Add a learning algorithm</span></span>

<span data-ttu-id="58df7-219">Este aplicativo usa um algoritmo de classificação que categoriza itens ou linhas de dados.</span><span class="sxs-lookup"><span data-stu-id="58df7-219">This app uses a classification algorithm that categorizes items or rows of data.</span></span> <span data-ttu-id="58df7-220">O aplicativo categoriza comentários de site como positivos ou negativos, portanto, use a tarefa de classificação binária.</span><span class="sxs-lookup"><span data-stu-id="58df7-220">The app categorizes website comments as either positive or negative, so use the binary classification task.</span></span>

<span data-ttu-id="58df7-221">Acrescente a tarefa de aprendizado de máquina às definições de transformação de dados adicionando o seguinte como a próxima linha de código em `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="58df7-221">Append the machine learning task to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

<span data-ttu-id="58df7-222">O [SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) é o algoritmo de treinamento de classificação.</span><span class="sxs-lookup"><span data-stu-id="58df7-222">The [SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) is your classification training algorithm.</span></span> <span data-ttu-id="58df7-223">Ele é acrescentado ao `estimator` e aceita o parâmetro `SentimentText` (`Features`) personalizado e o parâmetro de entrada `Label` para aprender com os dados históricos.</span><span class="sxs-lookup"><span data-stu-id="58df7-223">This is appended to the `estimator` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="58df7-224">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="58df7-224">Train the model</span></span>

<span data-ttu-id="58df7-225">Ajuste o modelo aos dados `splitTrainSet` e retorne o modelo treinado adicionando o seguinte como a próxima linha de código no método `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="58df7-225">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TrainModel "Train the model")]

<span data-ttu-id="58df7-226">O método [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) treina o modelo transformando o conjunto de dados e aplicando o treinamento.</span><span class="sxs-lookup"><span data-stu-id="58df7-226">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="58df7-227">Retornar o modelo treinado a ser usado para avaliação</span><span class="sxs-lookup"><span data-stu-id="58df7-227">Return the model trained to use for evaluation</span></span>

 <span data-ttu-id="58df7-228">Retorne o modelo no final do método `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="58df7-228">Return the model at the end of the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="58df7-229">Avalie o modelo</span><span class="sxs-lookup"><span data-stu-id="58df7-229">Evaluate the model</span></span>

<span data-ttu-id="58df7-230">Depois que o modelo é treinado, use os dados de teste para validar o desempenho do modelo.</span><span class="sxs-lookup"><span data-stu-id="58df7-230">After your model is trained, use your test data validate the model's performance.</span></span>

1. <span data-ttu-id="58df7-231">Crie o método `Evaluate()`, logo após `BuildAndTrainModel()`, com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="58df7-231">Create the `Evaluate()` method, just after `BuildAndTrainModel()`, with the following code:</span></span>

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    <span data-ttu-id="58df7-232">O método `Evaluate()` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="58df7-232">The `Evaluate()` method executes the following tasks:</span></span>

    - <span data-ttu-id="58df7-233">Carrega o conjunto de dados de teste.</span><span class="sxs-lookup"><span data-stu-id="58df7-233">Loads the test dataset.</span></span>
    - <span data-ttu-id="58df7-234">Cria o avaliador BinaryClassification.</span><span class="sxs-lookup"><span data-stu-id="58df7-234">Creates the BinaryClassification evaluator.</span></span>
    - <span data-ttu-id="58df7-235">Avalia o modelo e cria métricas.</span><span class="sxs-lookup"><span data-stu-id="58df7-235">Evaluates the model and creates metrics.</span></span>
    - <span data-ttu-id="58df7-236">Exibe as métricas.</span><span class="sxs-lookup"><span data-stu-id="58df7-236">Displays the metrics.</span></span>

2. <span data-ttu-id="58df7-237">Adicione uma chamada ao novo método a partir do método `Main()`, logo abaixo da chamada do método `BuildAndTrainModel()`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="58df7-237">Add a call to the new method from the `Main()` method, right under the `BuildAndTrainModel()` method call, using the following code:</span></span>

    [!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallEvaluate "Call the Evaluate method")]

3. <span data-ttu-id="58df7-238">Transforme os dados `splitTestSet` adicionando o seguinte código a `Evaluate()`:</span><span class="sxs-lookup"><span data-stu-id="58df7-238">Transform the `splitTestSet` data by adding the following code to `Evaluate()`:</span></span>

    [!code-csharp[PredictWithTransformer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TransformData "Predict using the Transformer")]

    <span data-ttu-id="58df7-239">O código anterior usa o método [Transform](xref:Microsoft.ML.ITransformer.Transform%2A) para fazer previsões para várias linhas de entrada fornecidas por um conjunto de dados de teste.</span><span class="sxs-lookup"><span data-stu-id="58df7-239">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

4. <span data-ttu-id="58df7-240">Avalie o modelo adicionando o seguinte como a próxima linha de código no método `Evaluate()`:</span><span class="sxs-lookup"><span data-stu-id="58df7-240">Evaluate the model by adding the following as the next line of code in the `Evaluate()` method:</span></span>

    [!code-csharp[ComputeMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Evaluate "Compute Metrics")]

<span data-ttu-id="58df7-241">Uma vez que você tem o conjunto de previsão (`predictions`), o método [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) avalia o modelo, que compara os valores previstos com os `Labels` reais no conjunto de dados de teste e retorna um objeto [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) sobre o desempenho do modelo.</span><span class="sxs-lookup"><span data-stu-id="58df7-241">Once you have the prediction set (`predictions`), the [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns a [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) object on how the model is performing.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="58df7-242">Exibir as métricas para validação de modelo</span><span class="sxs-lookup"><span data-stu-id="58df7-242">Displaying the metrics for model validation</span></span>

<span data-ttu-id="58df7-243">Use o código a seguir para exibir as métricas:</span><span class="sxs-lookup"><span data-stu-id="58df7-243">Use the following code to display the metrics:</span></span>

[!code-csharp[DisplayMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayMetrics "Display selected metrics")]

- <span data-ttu-id="58df7-244">A métrica `Accuracy` obtém a precisão de um modelo, que é a proporção de previsões corretas no conjunto de teste.</span><span class="sxs-lookup"><span data-stu-id="58df7-244">The `Accuracy` metric gets the accuracy of a model, which is the proportion of correct predictions in the test set.</span></span>

- <span data-ttu-id="58df7-245">A métrica `AreaUnderRocCurve` indica a confiabilidade do modelo ao classificar corretamente as classes positivas e negativas.</span><span class="sxs-lookup"><span data-stu-id="58df7-245">The `AreaUnderRocCurve` metric indicates how confident the model is correctly classifying the positive and negative classes.</span></span> <span data-ttu-id="58df7-246">Você deseja que o `AreaUnderRocCurve` seja o mais próximo possível de um.</span><span class="sxs-lookup"><span data-stu-id="58df7-246">You want the `AreaUnderRocCurve` to be as close to one as possible.</span></span>

- <span data-ttu-id="58df7-247">A métrica `F1Score` obtém a pontuação F1 do modelo, que é uma medida do equilíbrio entre [precisão](../resources/glossary.md#precision) e [recall](../resources/glossary.md#recall).</span><span class="sxs-lookup"><span data-stu-id="58df7-247">The `F1Score` metric gets the model's F1 score, which is a measure of balance between [precision](../resources/glossary.md#precision) and [recall](../resources/glossary.md#recall).</span></span>  <span data-ttu-id="58df7-248">Você deseja que o `F1Score` seja o mais próximo possível de um.</span><span class="sxs-lookup"><span data-stu-id="58df7-248">You want the `F1Score` to be as close to one as possible.</span></span>

### <a name="predict-the-test-data-outcome"></a><span data-ttu-id="58df7-249">Prever o resultado dos dados de teste</span><span class="sxs-lookup"><span data-stu-id="58df7-249">Predict the test data outcome</span></span>

1. <span data-ttu-id="58df7-250">Crie o método `UseModelWithSingleItem()`, logo após o método `Evaluate()`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="58df7-250">Create the `UseModelWithSingleItem()` method, just after the `Evaluate()` method, using the following code:</span></span>

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="58df7-251">O método `UseModelWithSingleItem()` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="58df7-251">The `UseModelWithSingleItem()` method executes the following tasks:</span></span>

    - <span data-ttu-id="58df7-252">Cria um único comentário dos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="58df7-252">Creates a single comment of test data.</span></span>
    - <span data-ttu-id="58df7-253">Prevê o sentimento com base nos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="58df7-253">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="58df7-254">Combina dados de teste e previsões para relatórios.</span><span class="sxs-lookup"><span data-stu-id="58df7-254">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="58df7-255">Exibe os resultados previstos.</span><span class="sxs-lookup"><span data-stu-id="58df7-255">Displays the predicted results.</span></span>

2. <span data-ttu-id="58df7-256">Adicione uma chamada ao novo método a partir do método `Main()`, logo abaixo da chamada do método `Evaluate()`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="58df7-256">Add a call to the new method from the `Main()` method, right under the `Evaluate()` method call, using the following code:</span></span>

    [!code-csharp[CallUseModelWithSingleItem](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. <span data-ttu-id="58df7-257">Adicione o seguinte código para criar a primeira linha no método `UseModelWithSingleItem()`:</span><span class="sxs-lookup"><span data-stu-id="58df7-257">Add the following code to create as the first line in the `UseModelWithSingleItem()` Method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    <span data-ttu-id="58df7-258">O [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) é uma API de conveniência, que permite que você execute uma previsão em uma única instância de dados.</span><span class="sxs-lookup"><span data-stu-id="58df7-258">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="58df7-259">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)Não é thread-safe.</span><span class="sxs-lookup"><span data-stu-id="58df7-259">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="58df7-260">É aceitável usar em ambientes de protótipo ou de thread único.</span><span class="sxs-lookup"><span data-stu-id="58df7-260">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="58df7-261">Para melhorar o desempenho e a segurança de thread em ambientes de produção, use o `PredictionEnginePool` serviço, que cria um [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) dos [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objetos para uso em todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="58df7-261">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="58df7-262">Consulte este guia sobre como [usar o `PredictionEnginePool` em uma API Web do ASP.NET Core](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="58df7-262">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="58df7-263">A extensão de serviço `PredictionEnginePool` está atualmente em versão prévia.</span><span class="sxs-lookup"><span data-stu-id="58df7-263">`PredictionEnginePool` service extension is currently in preview.</span></span>

4. <span data-ttu-id="58df7-264">Adicione um comentário para testar as previsões do modelo treinado no método `UseModelWithSingleItem()` ao criar uma instância de `SentimentData`:</span><span class="sxs-lookup"><span data-stu-id="58df7-264">Add a comment to test the trained model's prediction in the `UseModelWithSingleItem()` method by creating an instance of `SentimentData`:</span></span>

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. <span data-ttu-id="58df7-265">Passe os dados do comentário de teste para o [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) adicionando o seguinte como as próximas linhas de código no `UseModelWithSingleItem()` método:</span><span class="sxs-lookup"><span data-stu-id="58df7-265">Pass the test comment data to the [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) by adding the following as the next lines of code in the `UseModelWithSingleItem()` method:</span></span>

    [!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Predict "Create a prediction of sentiment")]

    <span data-ttu-id="58df7-266">A função [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) faz uma previsão em uma única coluna de dados.</span><span class="sxs-lookup"><span data-stu-id="58df7-266">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data.</span></span>

6. <span data-ttu-id="58df7-267">Exiba `SentimentText` e a previsão de sentimento correspondente usando o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="58df7-267">Display `SentimentText` and corresponding sentiment prediction using the following code:</span></span>

    [!code-csharp[OutputPrediction](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a><span data-ttu-id="58df7-268">Usar o modelo para previsão</span><span class="sxs-lookup"><span data-stu-id="58df7-268">Use the model for prediction</span></span>

### <a name="deploy-and-predict-batch-items"></a><span data-ttu-id="58df7-269">Implantar e prever itens em lotes</span><span class="sxs-lookup"><span data-stu-id="58df7-269">Deploy and predict batch items</span></span>

1. <span data-ttu-id="58df7-270">Crie o método `UseModelWithBatchItems()`, logo após o método `UseModelWithSingleItem()`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="58df7-270">Create the `UseModelWithBatchItems()` method, just after the `UseModelWithSingleItem()` method, using the following code:</span></span>

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="58df7-271">O método `UseModelWithBatchItems()` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="58df7-271">The `UseModelWithBatchItems()` method executes the following tasks:</span></span>

    - <span data-ttu-id="58df7-272">Cria dados de teste em lote.</span><span class="sxs-lookup"><span data-stu-id="58df7-272">Creates batch test data.</span></span>
    - <span data-ttu-id="58df7-273">Prevê o sentimento com base nos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="58df7-273">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="58df7-274">Combina dados de teste e previsões para relatórios.</span><span class="sxs-lookup"><span data-stu-id="58df7-274">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="58df7-275">Exibe os resultados previstos.</span><span class="sxs-lookup"><span data-stu-id="58df7-275">Displays the predicted results.</span></span>

2. <span data-ttu-id="58df7-276">Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `UseModelWithSingleItem()`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="58df7-276">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem()` method call, using the following code:</span></span>

    [!code-csharp[CallPredictModelBatchItems](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. <span data-ttu-id="58df7-277">Adicione alguns comentários para testar as previsões do modelo treinado no método `UseModelWithBatchItems()`:</span><span class="sxs-lookup"><span data-stu-id="58df7-277">Add some comments to test the trained model's predictions in the `UseModelWithBatchItems()` method:</span></span>

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a><span data-ttu-id="58df7-278">Prever sentimento de comentário</span><span class="sxs-lookup"><span data-stu-id="58df7-278">Predict comment sentiment</span></span>

<span data-ttu-id="58df7-279">Use o modelo para prever o sentimento dos dados de comentários usando o método [Transform](xref:Microsoft.ML.ITransformer.Transform%2A):</span><span class="sxs-lookup"><span data-stu-id="58df7-279">Use the model to predict the comment data sentiment using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method:</span></span>

[!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a><span data-ttu-id="58df7-280">Combinar e exibir as previsões</span><span class="sxs-lookup"><span data-stu-id="58df7-280">Combine and display the predictions</span></span>

<span data-ttu-id="58df7-281">Crie um cabeçalho para as previsões usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="58df7-281">Create a header for the predictions using the following code:</span></span>

[!code-csharp[OutputHeaders](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="58df7-282">Como `SentimentPrediction` é herdado de `SentimentData`, o método `Transform()` preencheu `SentimentText` com os campos previstos.</span><span class="sxs-lookup"><span data-stu-id="58df7-282">Because `SentimentPrediction` is inherited from `SentimentData`, the `Transform()` method populated `SentimentText` with the predicted fields.</span></span> <span data-ttu-id="58df7-283">Conforme o processo do ML.NET processa, cada componente adiciona colunas e isso facilita a exibição dos resultados:</span><span class="sxs-lookup"><span data-stu-id="58df7-283">As the ML.NET process processes, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a><span data-ttu-id="58df7-284">Resultados</span><span class="sxs-lookup"><span data-stu-id="58df7-284">Results</span></span>

<span data-ttu-id="58df7-285">Seus resultados devem ser semelhantes aos seguintes.</span><span class="sxs-lookup"><span data-stu-id="58df7-285">Your results should be similar to the following.</span></span> <span data-ttu-id="58df7-286">Durante o processamento, as mensagens são exibidas.</span><span class="sxs-lookup"><span data-stu-id="58df7-286">During processing, messages are displayed.</span></span> <span data-ttu-id="58df7-287">Você pode ver avisos ou mensagens de processamento.</span><span class="sxs-lookup"><span data-stu-id="58df7-287">You may see warnings, or processing messages.</span></span> <span data-ttu-id="58df7-288">Eles foram removidos dos seguintes resultados para maior clareza.</span><span class="sxs-lookup"><span data-stu-id="58df7-288">These have been removed from the following results for clarity.</span></span>

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 83.96%
Auc: 90.51%
F1Score: 84.04%

=============== End of model evaluation ===============

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This was a very bad steak | Prediction: Negative | Probability: 0.1027377
=============== End of Predictions ===============

=============== Prediction Test of loaded model with a multiple samples ===============

Sentiment: This was a horrible meal | Prediction: Negative | Probability: 0.1369192
Sentiment: I love this spaghetti. | Prediction: Positive | Probability: 0.9960636
=============== End of predictions ===============

=============== End of process ===============
Press any key to continue . . .

```

<span data-ttu-id="58df7-289">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="58df7-289">Congratulations!</span></span> <span data-ttu-id="58df7-290">Agora você criou com sucesso um modelo de aprendizado de máquina para classificar e prever o sentimento das mensagens.</span><span class="sxs-lookup"><span data-stu-id="58df7-290">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span>

<span data-ttu-id="58df7-291">A criação de modelos bem-sucedidos é um processo iterativo.</span><span class="sxs-lookup"><span data-stu-id="58df7-291">Building successful models is an iterative process.</span></span> <span data-ttu-id="58df7-292">Esse modelo tem qualidade inicial inferior, pois o tutorial usa conjuntos de dados pequenos para fornecer um treinamento rápido do modelo.</span><span class="sxs-lookup"><span data-stu-id="58df7-292">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="58df7-293">Se você não estiver satisfeito com a qualidade do modelo, poderá tentar melhorá-la fornecendo um conjunto de maiores conjuntos de grandes ou escolhendo algoritmos de treinamento diferentes com [hiperparâmetros](../resources/glossary.md#hyperparameter) diferentes para cada algoritmo.</span><span class="sxs-lookup"><span data-stu-id="58df7-293">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different [hyper-parameters](../resources/glossary.md#hyperparameter) for each algorithm.</span></span>

<span data-ttu-id="58df7-294">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis).</span><span class="sxs-lookup"><span data-stu-id="58df7-294">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="58df7-295">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="58df7-295">Next steps</span></span>

<span data-ttu-id="58df7-296">Neste tutorial, você aprendeu a:</span><span class="sxs-lookup"><span data-stu-id="58df7-296">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="58df7-297">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="58df7-297">Create a console application</span></span>
> - <span data-ttu-id="58df7-298">Preparar os dados</span><span class="sxs-lookup"><span data-stu-id="58df7-298">Prepare data</span></span>
> - <span data-ttu-id="58df7-299">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="58df7-299">Load the data</span></span>
> - <span data-ttu-id="58df7-300">Criar e treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="58df7-300">Build and train the model</span></span>
> - <span data-ttu-id="58df7-301">Avalie o modelo</span><span class="sxs-lookup"><span data-stu-id="58df7-301">Evaluate the model</span></span>
> - <span data-ttu-id="58df7-302">Usar o modelo para fazer uma previsão</span><span class="sxs-lookup"><span data-stu-id="58df7-302">Use the model to make a prediction</span></span>
> - <span data-ttu-id="58df7-303">Confira os resultados</span><span class="sxs-lookup"><span data-stu-id="58df7-303">See the results</span></span>

<span data-ttu-id="58df7-304">Avançar para o próximo tutorial para saber mais</span><span class="sxs-lookup"><span data-stu-id="58df7-304">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="58df7-305">Classificação de problema</span><span class="sxs-lookup"><span data-stu-id="58df7-305">Issue Classification</span></span>](github-issue-classification.md)
