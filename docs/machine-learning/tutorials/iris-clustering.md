---
title: Categorizar as flores íris usando um modelo de clustering
description: Saiba como usar o ML.NET em um cenário de clustering
author: pkulikov
ms.author: johalex
ms.date: 05/02/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 7070189e289e8e18ba0d122d2411a9064182e2b1
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063572"
---
# <a name="tutorial-categorize-iris-flowers-using-a-clustering-model-with-mlnet"></a><span data-ttu-id="9b863-103">Tutorial: Categorizar as flores íris usando um modelo de clustering com ML.NET</span><span class="sxs-lookup"><span data-stu-id="9b863-103">Tutorial: Categorize iris flowers using a clustering model with ML.NET</span></span>

<span data-ttu-id="9b863-104">Este tutorial ilustra como usar o ML.NET para criar um [modelo de clustering](../resources/tasks.md#clustering) para o [conjunto de dados de flor Iris](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span><span class="sxs-lookup"><span data-stu-id="9b863-104">This tutorial illustrates how to use ML.NET to build a [clustering model](../resources/tasks.md#clustering) for the [iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span></span>

<span data-ttu-id="9b863-105">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="9b863-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="9b863-106">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="9b863-106">Understand the problem</span></span>
> - <span data-ttu-id="9b863-107">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="9b863-107">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="9b863-108">Preparar os dados</span><span class="sxs-lookup"><span data-stu-id="9b863-108">Prepare the data</span></span>
> - <span data-ttu-id="9b863-109">Carregar e transformar os dados</span><span class="sxs-lookup"><span data-stu-id="9b863-109">Load and transform the data</span></span>
> - <span data-ttu-id="9b863-110">Escolher um algoritmo de aprendizado</span><span class="sxs-lookup"><span data-stu-id="9b863-110">Choose a learning algorithm</span></span>
> - <span data-ttu-id="9b863-111">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="9b863-111">Train the model</span></span>
> - <span data-ttu-id="9b863-112">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="9b863-112">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9b863-113">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="9b863-113">Prerequisites</span></span>

- <span data-ttu-id="9b863-114">[Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="9b863-114">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="9b863-115">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="9b863-115">Understand the problem</span></span>

<span data-ttu-id="9b863-116">Esse problema abrange como dividir o conjunto de flores Iris em grupos diferentes com base nas características da flor.</span><span class="sxs-lookup"><span data-stu-id="9b863-116">This problem is about dividing the set of iris flowers in different groups based on the flower features.</span></span> <span data-ttu-id="9b863-117">Essas características são o comprimento e largura de uma sépala e o comprimento e a largura de uma pétala.</span><span class="sxs-lookup"><span data-stu-id="9b863-117">Those features are the length and width of a sepal and the length and width of a petal.</span></span> <span data-ttu-id="9b863-118">Para este tutorial, considere que o tipo de cada flor é desconhecido.</span><span class="sxs-lookup"><span data-stu-id="9b863-118">For this tutorial, assume that the type of each flower is unknown.</span></span> <span data-ttu-id="9b863-119">Você deseja conhecer a estrutura de um conjunto de dados por meio de suas características e prever como uma instância de dados se encaixa nessa estrutura.</span><span class="sxs-lookup"><span data-stu-id="9b863-119">You want to learn the structure of a data set from the features and predict how a data instance fits this structure.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="9b863-120">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="9b863-120">Select the appropriate machine learning task</span></span>

<span data-ttu-id="9b863-121">Como você não sabe a qual grupo cada flor pertence, escolha a tarefa [aprendizado de máquina não supervisionado](../resources/glossary.md#unsupervised-machine-learning).</span><span class="sxs-lookup"><span data-stu-id="9b863-121">As you don't know to which group each flower belongs to, you choose the [unsupervised machine learning](../resources/glossary.md#unsupervised-machine-learning) task.</span></span> <span data-ttu-id="9b863-122">Para dividir um conjunto de dados em grupos de forma que os elementos no mesmo grupo sejam mais semelhantes uns aos outros do que aos elementos de outros grupos, use a tarefa de aprendizado de máquina [clustering](../resources/tasks.md#clustering).</span><span class="sxs-lookup"><span data-stu-id="9b863-122">To divide a data set in groups in such a way that elements in the same group are more similar to each other than to those in other groups, use a [clustering](../resources/tasks.md#clustering) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="9b863-123">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="9b863-123">Create a console application</span></span>

1. <span data-ttu-id="9b863-124">Abra o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9b863-124">Open Visual Studio.</span></span> <span data-ttu-id="9b863-125">Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="9b863-125">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="9b863-126">Na caixa de diálogo **Novo Projeto**, selecione o nó **Visual C#** seguido pelo nó **.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="9b863-126">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="9b863-127">Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="9b863-127">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="9b863-128">Na caixa de texto **Nome**, digite "IrisFlowerClustering" e, em seguida, selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="9b863-128">In the **Name** text box, type "IrisFlowerClustering" and then select the **OK** button.</span></span>

1. <span data-ttu-id="9b863-129">Crie um diretório chamado *Dados* em seu projeto para armazenar o conjunto de dados e os arquivos de modelo:</span><span class="sxs-lookup"><span data-stu-id="9b863-129">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="9b863-130">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Nova Pasta**.</span><span class="sxs-lookup"><span data-stu-id="9b863-130">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="9b863-131">Digite "Data" e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="9b863-131">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="9b863-132">Instale o pacote NuGet **Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="9b863-132">Install the **Microsoft.ML** NuGet package:</span></span>

    <span data-ttu-id="9b863-133">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="9b863-133">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="9b863-134">Escolha "nuget.org" como a origem do pacote, selecione a guia **Procurar**, pesquise **Microsoft.ML**, selecione o pacote **v1.0.0** na lista e selecione o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="9b863-134">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the **v1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="9b863-135">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="9b863-135">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-the-data"></a><span data-ttu-id="9b863-136">Preparar os dados</span><span class="sxs-lookup"><span data-stu-id="9b863-136">Prepare the data</span></span>

1. <span data-ttu-id="9b863-137">Baixe o conjunto de dados [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) e salve-o na pasta *Dados* que você criou na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="9b863-137">Download the [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) data set and save it to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="9b863-138">Para obter mais informações sobre o conjunto de dados Iris, confira a página da Wikipédia [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) (Conjunto de dados de flor Iris) e a página [Iris Data Set](https://archive.ics.uci.edu/ml/datasets/Iris) (Conjunto de dados Iris), que é a fonte do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="9b863-138">For more information about the iris data set, see the [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia page and the [Iris Data Set](https://archive.ics.uci.edu/ml/datasets/Iris) page, which is the source of the data set.</span></span>

1. <span data-ttu-id="9b863-139">No **Gerenciador de Soluções**, clique com o botão direito do mouse no arquivo *iris.data* e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="9b863-139">In **Solution Explorer**, right-click the *iris.data* file and select **Properties**.</span></span> <span data-ttu-id="9b863-140">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.</span><span class="sxs-lookup"><span data-stu-id="9b863-140">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="9b863-141">O arquivo *iris.data* contém cinco colunas que representam:</span><span class="sxs-lookup"><span data-stu-id="9b863-141">The *iris.data* file contains five columns that represent:</span></span>

- <span data-ttu-id="9b863-142">o comprimento da sépala em centímetros</span><span class="sxs-lookup"><span data-stu-id="9b863-142">sepal length in centimetres</span></span>
- <span data-ttu-id="9b863-143">a largura da sépala em centímetros</span><span class="sxs-lookup"><span data-stu-id="9b863-143">sepal width in centimetres</span></span>
- <span data-ttu-id="9b863-144">o comprimento da pétala em centímetros</span><span class="sxs-lookup"><span data-stu-id="9b863-144">petal length in centimetres</span></span>
- <span data-ttu-id="9b863-145">a largura da pétala em centímetros</span><span class="sxs-lookup"><span data-stu-id="9b863-145">petal width in centimetres</span></span>
- <span data-ttu-id="9b863-146">o tipo de flor Iris</span><span class="sxs-lookup"><span data-stu-id="9b863-146">type of iris flower</span></span>

<span data-ttu-id="9b863-147">Para exemplificar o clustering, este tutorial ignora a última coluna.</span><span class="sxs-lookup"><span data-stu-id="9b863-147">For the sake of the clustering example, this tutorial ignores the last column.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="9b863-148">Criar classes de dados</span><span class="sxs-lookup"><span data-stu-id="9b863-148">Create data classes</span></span>

<span data-ttu-id="9b863-149">Crie classes para os dados de entrada e as previsões:</span><span class="sxs-lookup"><span data-stu-id="9b863-149">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="9b863-150">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="9b863-150">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="9b863-151">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *IrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="9b863-151">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *IrisData.cs*.</span></span> <span data-ttu-id="9b863-152">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="9b863-152">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="9b863-153">Adicione a seguinte diretiva `using` ao novo arquivo:</span><span class="sxs-lookup"><span data-stu-id="9b863-153">Add the following `using` directive to the new file:</span></span>

   [!code-csharp[Add necessary usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#Usings)]

<span data-ttu-id="9b863-154">Remova a definição de classe existente e adicione o código a seguir, que define as classes `IrisData` e `ClusterPrediction`, para o arquivo *IrisData.cs*:</span><span class="sxs-lookup"><span data-stu-id="9b863-154">Remove the existing class definition and add the following code, which defines the classes `IrisData` and `ClusterPrediction`, to the *IrisData.cs* file:</span></span>

[!code-csharp[Define data classes](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#ClassDefinitions)]

<span data-ttu-id="9b863-155">`IrisData` é a classe de dados de entrada e tem definições de cada característica provenientes do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="9b863-155">`IrisData` is the input data class and has definitions for each feature from the data set.</span></span> <span data-ttu-id="9b863-156">Use o atributo [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) para especificar os índices das colunas de origem no arquivo de conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="9b863-156">Use the [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute to specify the indices of the source columns in the data set file.</span></span>

<span data-ttu-id="9b863-157">A classe `ClusterPrediction` representa a saída do modelo de clustering aplicado a uma instância de `IrisData`.</span><span class="sxs-lookup"><span data-stu-id="9b863-157">The `ClusterPrediction` class represents the output of the clustering model applied to an `IrisData` instance.</span></span> <span data-ttu-id="9b863-158">Use o atributo [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) para associar os campos `PredictedClusterId` e `Distances` às colunas **PredictedLabel** e **Score**, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="9b863-158">Use the [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute to bind the `PredictedClusterId` and `Distances` fields to the **PredictedLabel** and **Score** columns respectively.</span></span> <span data-ttu-id="9b863-159">No caso da tarefa clustering, essas colunas têm o seguinte significado:</span><span class="sxs-lookup"><span data-stu-id="9b863-159">In case of the clustering task those columns have the following meaning:</span></span>

- <span data-ttu-id="9b863-160">A coluna **PredictedLabel** contém a ID do cluster previsto.</span><span class="sxs-lookup"><span data-stu-id="9b863-160">**PredictedLabel** column contains the ID of the predicted cluster.</span></span>
- <span data-ttu-id="9b863-161">A coluna **Score** contém uma matriz com as distâncias euclidianas quadradas para os centroides de cluster.</span><span class="sxs-lookup"><span data-stu-id="9b863-161">**Score** column contains an array with squared Euclidean distances to the cluster centroids.</span></span> <span data-ttu-id="9b863-162">O comprimento da matriz é igual ao número de clusters.</span><span class="sxs-lookup"><span data-stu-id="9b863-162">The array length is equal to the number of clusters.</span></span>

> [!NOTE]
> <span data-ttu-id="9b863-163">Use o tipo `float` para representar valores de ponto flutuante nas classes de dados de entrada e previsão.</span><span class="sxs-lookup"><span data-stu-id="9b863-163">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="9b863-164">Definir dados e caminhos de modelo</span><span class="sxs-lookup"><span data-stu-id="9b863-164">Define data and model paths</span></span>

<span data-ttu-id="9b863-165">Volte para o arquivo *Program.cs* e adicione dois campos para armazenar os caminhos no arquivo de conjunto de dados e no arquivo para salvar o modelo:</span><span class="sxs-lookup"><span data-stu-id="9b863-165">Go back to the *Program.cs* file and add two fields to hold the paths to the data set file and to the file to save the model:</span></span>

- <span data-ttu-id="9b863-166">`_dataPath` contém o caminho para o arquivo com o conjunto de dados usado para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="9b863-166">`_dataPath` contains the path to the file with the data set used to train the model.</span></span>
- <span data-ttu-id="9b863-167">`_modelPath` contém o caminho para o arquivo em que o modelo treinado está armazenado.</span><span class="sxs-lookup"><span data-stu-id="9b863-167">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="9b863-168">Adicione o seguinte código logo acima do método `Main` para especificar estes caminhos:</span><span class="sxs-lookup"><span data-stu-id="9b863-168">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Initialize paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Paths)]

<span data-ttu-id="9b863-169">Para fazer com que o código anterior seja compilado, adicione as seguintes diretivas `using` ao início do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="9b863-169">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add usings for paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a><span data-ttu-id="9b863-170">Criar o contexto de ML</span><span class="sxs-lookup"><span data-stu-id="9b863-170">Create ML context</span></span>

<span data-ttu-id="9b863-171">Adicione as seguintes diretivas `using` adicionais ao início do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="9b863-171">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[Add Microsoft.ML usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#MLUsings)]

<span data-ttu-id="9b863-172">No método `Main`, substitua a linha `Console.WriteLine("Hello World!");` pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="9b863-172">In the `Main` method, replace the `Console.WriteLine("Hello World!");` line with the following code:</span></span>

[!code-csharp[Create ML context](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateContext)]

<span data-ttu-id="9b863-173">A classe <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> representa o ambiente de aprendizado de máquina e fornece mecanismos para pontos de entrada e de log para carregamento de dados, treinamento do modelo, previsão e outras tarefas.</span><span class="sxs-lookup"><span data-stu-id="9b863-173">The <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> class represents the machine learning environment and provides mechanisms for logging and entry points for data loading, model training, prediction, and other tasks.</span></span> <span data-ttu-id="9b863-174">Isso é comparável conceitualmente ao uso de `DbContext` no Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="9b863-174">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span>

## <a name="setup-data-loading"></a><span data-ttu-id="9b863-175">Configurar o carregamento de dados</span><span class="sxs-lookup"><span data-stu-id="9b863-175">Setup data loading</span></span>

<span data-ttu-id="9b863-176">Adicione o seguinte código ao método `Main` para configurar a forma de carregamento de dados:</span><span class="sxs-lookup"><span data-stu-id="9b863-176">Add the following code to the `Main` method to setup the way to load data:</span></span>

[!code-csharp[Create text loader](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateDataView)]

<span data-ttu-id="9b863-177">O método de extensão [`MLContext.Data.LoadFromTextFile` genérico](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) infere o esquema do conjunto de dados do tipo `IrisData` fornecido e retorna <xref:Microsoft.ML.IDataView>, que pode ser usado como entrada para transformadores.</span><span class="sxs-lookup"><span data-stu-id="9b863-177">The generic [`MLContext.Data.LoadFromTextFile` extension method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) infers the data set schema from the provided `IrisData` type and returns <xref:Microsoft.ML.IDataView> which can be used as input for transformers.</span></span>

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="9b863-178">Criar um pipeline de aprendizado</span><span class="sxs-lookup"><span data-stu-id="9b863-178">Create a learning pipeline</span></span>

<span data-ttu-id="9b863-179">Para este tutorial, o pipeline de aprendizado da tarefa de clustering consiste nas duas seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="9b863-179">For this tutorial, the learning pipeline of the clustering task comprises two following steps:</span></span>

- <span data-ttu-id="9b863-180">concatenar colunas carregadas em uma coluna **Recursos**, que é usada por um treinador de clustering;</span><span class="sxs-lookup"><span data-stu-id="9b863-180">concatenate loaded columns into one **Features** column, which is used by a clustering trainer;</span></span>
- <span data-ttu-id="9b863-181">usar um treinador <xref:Microsoft.ML.Trainers.KMeansTrainer> para treinar o modelo usando o algoritmo de cluster K-means++.</span><span class="sxs-lookup"><span data-stu-id="9b863-181">use a <xref:Microsoft.ML.Trainers.KMeansTrainer> trainer to train the model using the k-means++ clustering algorithm.</span></span>

<span data-ttu-id="9b863-182">Adicione o seguinte código ao método `Main`:</span><span class="sxs-lookup"><span data-stu-id="9b863-182">Add the following code to the `Main` method:</span></span>

[!code-csharp[Create pipeline](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreatePipeline)]

<span data-ttu-id="9b863-183">O código especifica que o conjunto de dados deve ser dividido em três clusters.</span><span class="sxs-lookup"><span data-stu-id="9b863-183">The code specifies that the data set should be split in three clusters.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="9b863-184">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="9b863-184">Train the model</span></span>

<span data-ttu-id="9b863-185">As etapas adicionadas nas seções anteriores prepararam o pipeline para treinamento, no entanto, nenhuma foi executada.</span><span class="sxs-lookup"><span data-stu-id="9b863-185">The steps added in the preceding sections prepared the pipeline for training, however, none have been executed.</span></span> <span data-ttu-id="9b863-186">Adicione a seguinte linha ao método `Main` para executar o carregamento de dados e o treinamento do modelo:</span><span class="sxs-lookup"><span data-stu-id="9b863-186">Add the following line to the `Main` method to perform data loading and model training:</span></span>

[!code-csharp[Train the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#TrainModel)]

### <a name="save-the-model"></a><span data-ttu-id="9b863-187">Salvar o modelo</span><span class="sxs-lookup"><span data-stu-id="9b863-187">Save the model</span></span>

<span data-ttu-id="9b863-188">Neste ponto, você tem um modelo que pode ser integrado em qualquer um dos seus aplicativos .NET existentes ou novos.</span><span class="sxs-lookup"><span data-stu-id="9b863-188">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="9b863-189">Para salvar o modelo em um arquivo .zip, adicione o seguinte código ao método `Main`:</span><span class="sxs-lookup"><span data-stu-id="9b863-189">To save your model to a .zip file, add the following code to the `Main` method:</span></span>

[!code-csharp[Save the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="9b863-190">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="9b863-190">Use the model for predictions</span></span>

<span data-ttu-id="9b863-191">Para fazer previsões, use a classe <xref:Microsoft.ML.PredictionEngine%602> que usa instâncias do tipo de entrada por meio do pipeline transformador e produz instâncias do tipo de saída.</span><span class="sxs-lookup"><span data-stu-id="9b863-191">To make predictions, use the <xref:Microsoft.ML.PredictionEngine%602> class that takes instances of the input type through the transformer pipeline and produces instances of the output type.</span></span> <span data-ttu-id="9b863-192">Adicione a seguinte linha ao método `Main` para criar uma instância dessa classe:</span><span class="sxs-lookup"><span data-stu-id="9b863-192">Add the following line to the `Main` method to create an instance of that class:</span></span>

[!code-csharp[Create predictor](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Predictor)]

<span data-ttu-id="9b863-193">Crie a classe `TestIrisData` para hospedar as instâncias de dados de teste:</span><span class="sxs-lookup"><span data-stu-id="9b863-193">Create the `TestIrisData` class to house test data instances:</span></span>

1. <span data-ttu-id="9b863-194">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="9b863-194">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="9b863-195">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *TestIrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="9b863-195">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestIrisData.cs*.</span></span> <span data-ttu-id="9b863-196">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="9b863-196">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="9b863-197">Modifique a classe para ser estática, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="9b863-197">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[Make class static](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#Static)]

<span data-ttu-id="9b863-198">Este tutorial apresenta uma instância de dados de Iris dentro dessa classe.</span><span class="sxs-lookup"><span data-stu-id="9b863-198">This tutorial introduces one iris data instance within this class.</span></span> <span data-ttu-id="9b863-199">Você pode adicionar outros cenários para fazer experimentos com o modelo.</span><span class="sxs-lookup"><span data-stu-id="9b863-199">You can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="9b863-200">Adicione o seguinte código à classe `TestIrisData`:</span><span class="sxs-lookup"><span data-stu-id="9b863-200">Add the following code into the `TestIrisData` class:</span></span>

[!code-csharp[Test data](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#TestData)]

<span data-ttu-id="9b863-201">Para descobrir a qual cluster o item especificado pertence, volte para o arquivo *Program.cs* e adicione o seguinte código no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="9b863-201">To find out the cluster to which the specified item belongs to, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict and output results](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#PredictionExample)]

<span data-ttu-id="9b863-202">Execute o programa para ver qual cluster contém a instância de dados especificada e a distância quadrada daquela instância aos centroides do cluster.</span><span class="sxs-lookup"><span data-stu-id="9b863-202">Run the program to see which cluster contains the specified data instance and squared distances from that instance to the cluster centroids.</span></span> <span data-ttu-id="9b863-203">Os resultados devem ser semelhantes aos seguintes:</span><span class="sxs-lookup"><span data-stu-id="9b863-203">Your results should be similar to the following:</span></span>

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

<span data-ttu-id="9b863-204">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="9b863-204">Congratulations!</span></span> <span data-ttu-id="9b863-205">Você agora construiu um modelo de aprendizado de máquina para clustering de Iris e o usou para fazer previsões.</span><span class="sxs-lookup"><span data-stu-id="9b863-205">You've now successfully built a machine learning model for iris clustering and used it to make predictions.</span></span> <span data-ttu-id="9b863-206">Encontre o código-fonte deste tutorial no repositório do GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering).</span><span class="sxs-lookup"><span data-stu-id="9b863-206">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9b863-207">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="9b863-207">Next steps</span></span>

<span data-ttu-id="9b863-208">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="9b863-208">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="9b863-209">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="9b863-209">Understand the problem</span></span>
> - <span data-ttu-id="9b863-210">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="9b863-210">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="9b863-211">Preparar os dados</span><span class="sxs-lookup"><span data-stu-id="9b863-211">Prepare the data</span></span>
> - <span data-ttu-id="9b863-212">Carregar e transformar os dados</span><span class="sxs-lookup"><span data-stu-id="9b863-212">Load and transform the data</span></span>
> - <span data-ttu-id="9b863-213">Escolher um algoritmo de aprendizado</span><span class="sxs-lookup"><span data-stu-id="9b863-213">Choose a learning algorithm</span></span>
> - <span data-ttu-id="9b863-214">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="9b863-214">Train the model</span></span>
> - <span data-ttu-id="9b863-215">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="9b863-215">Use the model for predictions</span></span>

<span data-ttu-id="9b863-216">Confira nosso repositório GitHub para continuar aprendendo e encontrar mais amostras.</span><span class="sxs-lookup"><span data-stu-id="9b863-216">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="9b863-217">dotnet/machinelearning GitHub repository</span><span class="sxs-lookup"><span data-stu-id="9b863-217">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
