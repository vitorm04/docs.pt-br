---
title: Agrupar flores íris usando um aprendiz de clustering – ML.NET
description: Saiba como usar o ML.NET em um cenário de clustering
author: pkulikov
ms.author: johalex
ms.date: 12/17/2018
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 012cea471c69f66ad9a61db858b4575606b31f74
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53656317"
---
# <a name="tutorial-cluster-iris-flowers-using-a-clustering-learner-with-mlnet"></a><span data-ttu-id="b292c-103">Tutorial: Agrupar flores íris usando um aprendiz de clustering com o ML.NET</span><span class="sxs-lookup"><span data-stu-id="b292c-103">Tutorial: Cluster iris flowers using a clustering learner with ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="b292c-104">Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="b292c-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="b292c-105">Para obter mais informações, confira a [Introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="b292c-105">For more information, see the [ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="b292c-106">Este tutorial ilustra como usar o ML.NET para criar um [modelo de clustering](../resources/tasks.md#clustering) para o [conjunto de dados de flor Iris](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span><span class="sxs-lookup"><span data-stu-id="b292c-106">This tutorial illustrates how to use ML.NET to build a [clustering model](../resources/tasks.md#clustering) for the [iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span></span>

<span data-ttu-id="b292c-107">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="b292c-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="b292c-108">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="b292c-108">Understand the problem</span></span>
> - <span data-ttu-id="b292c-109">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="b292c-109">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="b292c-110">Preparar os dados</span><span class="sxs-lookup"><span data-stu-id="b292c-110">Prepare the data</span></span>
> - <span data-ttu-id="b292c-111">Carregar e transformar os dados</span><span class="sxs-lookup"><span data-stu-id="b292c-111">Load and transform the data</span></span>
> - <span data-ttu-id="b292c-112">Escolher um algoritmo de aprendizado</span><span class="sxs-lookup"><span data-stu-id="b292c-112">Choose a learning algorithm</span></span>
> - <span data-ttu-id="b292c-113">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="b292c-113">Train the model</span></span>
> - <span data-ttu-id="b292c-114">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="b292c-114">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b292c-115">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b292c-115">Prerequisites</span></span>

- <span data-ttu-id="b292c-116">[Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="b292c-116">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="b292c-117">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="b292c-117">Understand the problem</span></span>

<span data-ttu-id="b292c-118">Esse problema abrange como dividir o conjunto de flores Iris em grupos diferentes com base nas características da flor.</span><span class="sxs-lookup"><span data-stu-id="b292c-118">This problem is about dividing the set of iris flowers in different groups based on the flower features.</span></span> <span data-ttu-id="b292c-119">Essas características são o comprimento e largura de uma sépala e o comprimento e a largura de uma pétala.</span><span class="sxs-lookup"><span data-stu-id="b292c-119">Those features are the length and width of a sepal and the length and width of a petal.</span></span> <span data-ttu-id="b292c-120">Para este tutorial, considere que o tipo de cada flor é desconhecido.</span><span class="sxs-lookup"><span data-stu-id="b292c-120">For this tutorial, assume that the type of each flower is unknown.</span></span> <span data-ttu-id="b292c-121">Você deseja conhecer a estrutura de um conjunto de dados por meio de suas características e prever como uma instância de dados se encaixa nessa estrutura.</span><span class="sxs-lookup"><span data-stu-id="b292c-121">You want to learn the structure of a data set from the features and predict how a data instance fits this structure.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="b292c-122">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="b292c-122">Select the appropriate machine learning task</span></span>

<span data-ttu-id="b292c-123">Como você não sabe a qual grupo cada flor pertence, escolha a tarefa [aprendizado de máquina não supervisionado](../resources/glossary.md#unsupervised-machine-learning).</span><span class="sxs-lookup"><span data-stu-id="b292c-123">As you don't know to which group each flower belongs to, you choose the [unsupervised machine learning](../resources/glossary.md#unsupervised-machine-learning) task.</span></span> <span data-ttu-id="b292c-124">Para dividir um conjunto de dados em grupos de forma que os elementos no mesmo grupo sejam mais semelhantes uns aos outros do que aos elementos de outros grupos, use a tarefa de aprendizado de máquina [clustering](../resources/tasks.md#clustering).</span><span class="sxs-lookup"><span data-stu-id="b292c-124">To divide a data set in groups in such a way that elements in the same group are more similar to each other than to those in other groups, use a [clustering](../resources/tasks.md#clustering) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="b292c-125">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="b292c-125">Create a console application</span></span>

1. <span data-ttu-id="b292c-126">Abra o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="b292c-126">Open Visual Studio 2017.</span></span> <span data-ttu-id="b292c-127">Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="b292c-127">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="b292c-128">Na caixa de diálogo **Novo Projeto**, selecione o nó **Visual C#** seguido pelo nó **.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="b292c-128">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="b292c-129">Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="b292c-129">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="b292c-130">Na caixa de texto **Nome**, digite "IrisFlowerClustering" e, em seguida, selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="b292c-130">In the **Name** text box, type "IrisFlowerClustering" and then select the **OK** button.</span></span>

1. <span data-ttu-id="b292c-131">Crie um diretório chamado *Dados* em seu projeto para armazenar o conjunto de dados e os arquivos de modelo:</span><span class="sxs-lookup"><span data-stu-id="b292c-131">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="b292c-132">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Nova Pasta**.</span><span class="sxs-lookup"><span data-stu-id="b292c-132">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="b292c-133">Digite "Data" e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="b292c-133">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="b292c-134">Instale o pacote NuGet **Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="b292c-134">Install the **Microsoft.ML** NuGet package:</span></span>

    <span data-ttu-id="b292c-135">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="b292c-135">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="b292c-136">Escolha "nuget.org" como a origem do Pacote, selecione a guia **Procurar**, pesquise **Microsoft.ML**, selecione o pacote na lista e escolha o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="b292c-136">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="b292c-137">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="b292c-137">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-the-data"></a><span data-ttu-id="b292c-138">Preparar os dados</span><span class="sxs-lookup"><span data-stu-id="b292c-138">Prepare the data</span></span>

1. <span data-ttu-id="b292c-139">Baixe o conjunto de dados [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) e salve-o na pasta *Dados* que você criou na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="b292c-139">Download the [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) data set and save it to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="b292c-140">Para obter mais informações sobre o conjunto de dados Iris, confira a página da Wikipédia [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) (Conjunto de dados de flor Iris) e a página [Iris Data Set](http://archive.ics.uci.edu/ml/datasets/Iris) (Conjunto de dados Iris), que é a fonte do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="b292c-140">For more information about the iris data set, see the [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia page and the [Iris Data Set](http://archive.ics.uci.edu/ml/datasets/Iris) page, which is the source of the data set.</span></span>

1. <span data-ttu-id="b292c-141">No **Gerenciador de Soluções**, clique com o botão direito do mouse no arquivo *iris.data* e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="b292c-141">In **Solution Explorer**, right-click the *iris.data* file and select **Properties**.</span></span> <span data-ttu-id="b292c-142">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.</span><span class="sxs-lookup"><span data-stu-id="b292c-142">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="b292c-143">O arquivo *iris.data* contém cinco colunas que representam:</span><span class="sxs-lookup"><span data-stu-id="b292c-143">The *iris.data* file contains five columns that represent:</span></span>

- <span data-ttu-id="b292c-144">o comprimento da sépala em centímetros</span><span class="sxs-lookup"><span data-stu-id="b292c-144">sepal length in centimetres</span></span>
- <span data-ttu-id="b292c-145">a largura da sépala em centímetros</span><span class="sxs-lookup"><span data-stu-id="b292c-145">sepal width in centimetres</span></span>
- <span data-ttu-id="b292c-146">o comprimento da pétala em centímetros</span><span class="sxs-lookup"><span data-stu-id="b292c-146">petal length in centimetres</span></span>
- <span data-ttu-id="b292c-147">a largura da pétala em centímetros</span><span class="sxs-lookup"><span data-stu-id="b292c-147">petal width in centimetres</span></span>
- <span data-ttu-id="b292c-148">o tipo de flor Iris</span><span class="sxs-lookup"><span data-stu-id="b292c-148">type of iris flower</span></span>

<span data-ttu-id="b292c-149">Para exemplificar o clustering, este tutorial ignora a última coluna.</span><span class="sxs-lookup"><span data-stu-id="b292c-149">For the sake of the clustering example, this tutorial ignores the last column.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="b292c-150">Criar classes de dados</span><span class="sxs-lookup"><span data-stu-id="b292c-150">Create data classes</span></span>

<span data-ttu-id="b292c-151">Crie classes para os dados de entrada e as previsões:</span><span class="sxs-lookup"><span data-stu-id="b292c-151">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="b292c-152">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="b292c-152">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="b292c-153">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *IrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="b292c-153">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *IrisData.cs*.</span></span> <span data-ttu-id="b292c-154">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="b292c-154">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="b292c-155">Adicione a seguinte diretiva `using` ao novo arquivo:</span><span class="sxs-lookup"><span data-stu-id="b292c-155">Add the following `using` directive to the new file:</span></span>

   [!code-csharp[Add necessary usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#Usings)]

<span data-ttu-id="b292c-156">Remova a definição de classe existente e adicione o código a seguir, que define as classes `IrisData` e `ClusterPrediction`, para o arquivo *IrisData.cs*:</span><span class="sxs-lookup"><span data-stu-id="b292c-156">Remove the existing class definition and add the following code, which defines the classes `IrisData` and `ClusterPrediction`, to the *IrisData.cs* file:</span></span>

[!code-csharp[Define data classes](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#ClassDefinitions)]

<span data-ttu-id="b292c-157">`IrisData` é a classe de dados de entrada e tem definições de cada característica provenientes do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="b292c-157">`IrisData` is the input data class and has definitions for each feature from the data set.</span></span> <span data-ttu-id="b292c-158">Use o atributo [Column](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) para especificar os índices das colunas de origem no arquivo de conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="b292c-158">Use the [Column](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) attribute to specify the indices of the source columns in the data set file.</span></span>

<span data-ttu-id="b292c-159">A classe `ClusterPrediction` representa a saída do modelo de clustering aplicado a uma instância de `IrisData`.</span><span class="sxs-lookup"><span data-stu-id="b292c-159">The `ClusterPrediction` class represents the output of the clustering model applied to an `IrisData` instance.</span></span> <span data-ttu-id="b292c-160">Use o atributo [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) para associar os campos `PredictedClusterId` e `Distances` às colunas **PredictedLabel** e **Score**, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="b292c-160">Use the [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) attribute to bind the `PredictedClusterId` and `Distances` fields to the **PredictedLabel** and **Score** columns respectively.</span></span> <span data-ttu-id="b292c-161">No caso da tarefa clustering, essas colunas têm o seguinte significado:</span><span class="sxs-lookup"><span data-stu-id="b292c-161">In case of the clustering task those columns have the following meaning:</span></span>

- <span data-ttu-id="b292c-162">A coluna **PredictedLabel** contém a ID do cluster previsto.</span><span class="sxs-lookup"><span data-stu-id="b292c-162">**PredictedLabel** column contains the ID of the predicted cluster.</span></span>
- <span data-ttu-id="b292c-163">A coluna **Score** contém uma matriz com as distâncias euclidianas quadradas para os centroides de cluster.</span><span class="sxs-lookup"><span data-stu-id="b292c-163">**Score** column contains an array with squared Euclidean distances to the cluster centroids.</span></span> <span data-ttu-id="b292c-164">O comprimento da matriz é igual ao número de clusters.</span><span class="sxs-lookup"><span data-stu-id="b292c-164">The array length is equal to the number of clusters.</span></span>

> [!NOTE]
> <span data-ttu-id="b292c-165">Use o tipo `float` para representar valores de ponto flutuante nas classes de dados de entrada e previsão.</span><span class="sxs-lookup"><span data-stu-id="b292c-165">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="b292c-166">Definir dados e caminhos de modelo</span><span class="sxs-lookup"><span data-stu-id="b292c-166">Define data and model paths</span></span>

<span data-ttu-id="b292c-167">Volte para o arquivo *Program.cs* e adicione dois campos para armazenar os caminhos no arquivo de conjunto de dados e no arquivo para salvar o modelo:</span><span class="sxs-lookup"><span data-stu-id="b292c-167">Go back to the *Program.cs* file and add two fields to hold the paths to the data set file and to the file to save the model:</span></span>

- <span data-ttu-id="b292c-168">`_dataPath` contém o caminho para o arquivo com o conjunto de dados usado para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="b292c-168">`_dataPath` contains the path to the file with the data set used to train the model.</span></span>
- <span data-ttu-id="b292c-169">`_modelPath` contém o caminho para o arquivo em que o modelo treinado está armazenado.</span><span class="sxs-lookup"><span data-stu-id="b292c-169">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="b292c-170">Adicione o seguinte código logo acima do método `Main` para especificar estes caminhos:</span><span class="sxs-lookup"><span data-stu-id="b292c-170">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Initialize paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Paths)]

<span data-ttu-id="b292c-171">Para fazer com que o código anterior seja compilado, adicione as seguintes diretivas `using` ao início do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="b292c-171">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add usings for paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a><span data-ttu-id="b292c-172">Criar o contexto de ML</span><span class="sxs-lookup"><span data-stu-id="b292c-172">Create ML context</span></span>

<span data-ttu-id="b292c-173">Adicione as seguintes diretivas `using` adicionais ao início do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="b292c-173">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[Add Microsoft.ML usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#MLUsings)]

<span data-ttu-id="b292c-174">No método `Main`, substitua a linha `Console.WriteLine("Hello World!");` pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="b292c-174">In the `Main` method, replace the `Console.WriteLine("Hello World!");` line with the following code:</span></span>

[!code-csharp[Create ML context](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateContext)]

<span data-ttu-id="b292c-175">A classe <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> representa o ambiente de aprendizado de máquina e fornece mecanismos para pontos de entrada e de log para carregamento de dados, treinamento do modelo, previsão e outras tarefas.</span><span class="sxs-lookup"><span data-stu-id="b292c-175">The <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> class represents the machine learning environment and provides mechanisms for logging and entry points for data loading, model training, prediction, and other tasks.</span></span> <span data-ttu-id="b292c-176">Isso é comparável conceitualmente ao uso de `DbContext` no Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="b292c-176">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span>

## <a name="setup-data-loading"></a><span data-ttu-id="b292c-177">Configurar o carregamento de dados</span><span class="sxs-lookup"><span data-stu-id="b292c-177">Setup data loading</span></span>

<span data-ttu-id="b292c-178">Adicione o seguinte código ao método `Main` para configurar a forma de carregamento de dados:</span><span class="sxs-lookup"><span data-stu-id="b292c-178">Add the following code to the `Main` method to setup the way to load data:</span></span>

[!code-csharp[Create text loader](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SetupTextLoader)]

<span data-ttu-id="b292c-179">Observe que os nomes de coluna e os índices correspondem ao esquema definido pela classe `IrisData`.</span><span class="sxs-lookup"><span data-stu-id="b292c-179">Note that the column names and indices match the schema defined by the `IrisData` class.</span></span> <span data-ttu-id="b292c-180">O valor <xref:Microsoft.ML.Runtime.Data.DataKind.R4?displayProperty=nameWithType> especifica o tipo `float`.</span><span class="sxs-lookup"><span data-stu-id="b292c-180">The <xref:Microsoft.ML.Runtime.Data.DataKind.R4?displayProperty=nameWithType> value specifies the `float` type.</span></span>

<span data-ttu-id="b292c-181">Use a instância <xref:Microsoft.ML.Runtime.Data.TextLoader> criada para criar uma instância <xref:Microsoft.ML.Runtime.Data.IDataView>, que representa a fonte de dados do conjunto de dados de treinamento:</span><span class="sxs-lookup"><span data-stu-id="b292c-181">Use instantiated <xref:Microsoft.ML.Runtime.Data.TextLoader> instance to create an <xref:Microsoft.ML.Runtime.Data.IDataView> instance, which represents the data source for the training data set:</span></span>

[!code-csharp[Create IDataView](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateDataView)]

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="b292c-182">Criar um pipeline de aprendizado</span><span class="sxs-lookup"><span data-stu-id="b292c-182">Create a learning pipeline</span></span>

<span data-ttu-id="b292c-183">Para este tutorial, o pipeline de aprendizado da tarefa de clustering consiste nas duas seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="b292c-183">For this tutorial, the learning pipeline of the clustering task comprises two following steps:</span></span>

- <span data-ttu-id="b292c-184">concatenar colunas carregadas em uma coluna **Recursos**, que é usada por um treinador de clustering;</span><span class="sxs-lookup"><span data-stu-id="b292c-184">concatenate loaded columns into one **Features** column, which is used by a clustering trainer;</span></span>
- <span data-ttu-id="b292c-185">usar um treinador <xref:Microsoft.ML.Trainers.KMeans.KMeansPlusPlusTrainer> para treinar o modelo usando o algoritmo de cluster K-means++.</span><span class="sxs-lookup"><span data-stu-id="b292c-185">use a <xref:Microsoft.ML.Trainers.KMeans.KMeansPlusPlusTrainer> trainer to train the model using the k-means++ clustering algorithm.</span></span>

<span data-ttu-id="b292c-186">Adicione o seguinte código ao método `Main`:</span><span class="sxs-lookup"><span data-stu-id="b292c-186">Add the following code to the `Main` method:</span></span>

[!code-csharp[Create pipeline](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreatePipeline)]

<span data-ttu-id="b292c-187">O código especifica que o conjunto de dados deve ser dividido em três clusters.</span><span class="sxs-lookup"><span data-stu-id="b292c-187">The code specifies that the data set should be split in three clusters.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="b292c-188">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="b292c-188">Train the model</span></span>

<span data-ttu-id="b292c-189">As etapas adicionadas nas seções anteriores prepararam o pipeline para treinamento, no entanto, nenhuma foi executada.</span><span class="sxs-lookup"><span data-stu-id="b292c-189">The steps added in the preceding sections prepared the pipeline for training, however, none have been executed.</span></span> <span data-ttu-id="b292c-190">Adicione a seguinte linha ao método `Main` para executar o carregamento de dados e o treinamento do modelo:</span><span class="sxs-lookup"><span data-stu-id="b292c-190">Add the following line to the `Main` method to perform data loading and model training:</span></span>

[!code-csharp[Train the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#TrainModel)]

### <a name="save-the-model"></a><span data-ttu-id="b292c-191">Salvar o modelo</span><span class="sxs-lookup"><span data-stu-id="b292c-191">Save the model</span></span>

<span data-ttu-id="b292c-192">Neste ponto, você tem um modelo que pode ser integrado em qualquer um dos seus aplicativos .NET existentes ou novos.</span><span class="sxs-lookup"><span data-stu-id="b292c-192">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="b292c-193">Para salvar o modelo em um arquivo .zip, adicione o seguinte código ao método `Main`:</span><span class="sxs-lookup"><span data-stu-id="b292c-193">To save your model to a .zip file, add the following code to the `Main` method:</span></span>

[!code-csharp[Save the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="b292c-194">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="b292c-194">Use the model for predictions</span></span>

<span data-ttu-id="b292c-195">Para fazer previsões, use a classe <xref:Microsoft.ML.Runtime.Data.PredictionFunction%602> que usa instâncias do tipo de entrada por meio do pipeline transformador e produz instâncias do tipo de saída.</span><span class="sxs-lookup"><span data-stu-id="b292c-195">To make predictions, use the <xref:Microsoft.ML.Runtime.Data.PredictionFunction%602> class that takes instances of the input type through the transformer pipeline and produces instances of the output type.</span></span> <span data-ttu-id="b292c-196">Adicione a seguinte linha ao método `Main` para criar uma instância dessa classe:</span><span class="sxs-lookup"><span data-stu-id="b292c-196">Add the following line to the `Main` method to create an instance of that class:</span></span>

[!code-csharp[Create predictor](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Predictor)]

<span data-ttu-id="b292c-197">Crie a classe `TestIrisData` para hospedar as instâncias de dados de teste:</span><span class="sxs-lookup"><span data-stu-id="b292c-197">Create the `TestIrisData` class to house test data instances:</span></span>

1. <span data-ttu-id="b292c-198">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="b292c-198">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="b292c-199">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *TestIrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="b292c-199">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestIrisData.cs*.</span></span> <span data-ttu-id="b292c-200">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="b292c-200">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="b292c-201">Modifique a classe para ser estática, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b292c-201">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[Make class static](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#Static)]

<span data-ttu-id="b292c-202">Este tutorial apresenta uma instância de dados de Iris dentro dessa classe.</span><span class="sxs-lookup"><span data-stu-id="b292c-202">This tutorial introduces one iris data instance within this class.</span></span> <span data-ttu-id="b292c-203">Você pode adicionar outros cenários para fazer experimentos com o modelo.</span><span class="sxs-lookup"><span data-stu-id="b292c-203">You can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="b292c-204">Adicione o seguinte código à classe `TestIrisData`:</span><span class="sxs-lookup"><span data-stu-id="b292c-204">Add the following code into the `TestIrisData` class:</span></span>

[!code-csharp[Test data](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#TestData)]

<span data-ttu-id="b292c-205">Para descobrir a qual cluster o item especificado pertence, volte para o arquivo *Program.cs* e adicione o seguinte código no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="b292c-205">To find out the cluster to which the specified item belongs to, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict and output results](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#PredictionExample)]

<span data-ttu-id="b292c-206">Execute o programa para ver qual cluster contém a instância de dados especificada e a distância quadrada daquela instância aos centroides do cluster.</span><span class="sxs-lookup"><span data-stu-id="b292c-206">Run the program to see which cluster contains the specified data instance and squared distances from that instance to the cluster centroids.</span></span> <span data-ttu-id="b292c-207">Os resultados devem ser semelhantes aos seguintes:</span><span class="sxs-lookup"><span data-stu-id="b292c-207">Your results should be similar to the following:</span></span>

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

<span data-ttu-id="b292c-208">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="b292c-208">Congratulations!</span></span> <span data-ttu-id="b292c-209">Você agora construiu um modelo de aprendizado de máquina para clustering de Iris e o usou para fazer previsões.</span><span class="sxs-lookup"><span data-stu-id="b292c-209">You've now successfully built a machine learning model for iris clustering and used it to make predictions.</span></span> <span data-ttu-id="b292c-210">Encontre o código-fonte deste tutorial no repositório do GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering).</span><span class="sxs-lookup"><span data-stu-id="b292c-210">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b292c-211">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="b292c-211">Next steps</span></span>

<span data-ttu-id="b292c-212">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="b292c-212">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="b292c-213">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="b292c-213">Understand the problem</span></span>
> - <span data-ttu-id="b292c-214">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="b292c-214">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="b292c-215">Preparar os dados</span><span class="sxs-lookup"><span data-stu-id="b292c-215">Prepare the data</span></span>
> - <span data-ttu-id="b292c-216">Carregar e transformar os dados</span><span class="sxs-lookup"><span data-stu-id="b292c-216">Load and transform the data</span></span>
> - <span data-ttu-id="b292c-217">Escolher um algoritmo de aprendizado</span><span class="sxs-lookup"><span data-stu-id="b292c-217">Choose a learning algorithm</span></span>
> - <span data-ttu-id="b292c-218">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="b292c-218">Train the model</span></span>
> - <span data-ttu-id="b292c-219">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="b292c-219">Use the model for predictions</span></span>

<span data-ttu-id="b292c-220">Confira nosso repositório GitHub para continuar aprendendo e encontrar mais amostras.</span><span class="sxs-lookup"><span data-stu-id="b292c-220">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="b292c-221">dotnet/machinelearning GitHub repository</span><span class="sxs-lookup"><span data-stu-id="b292c-221">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
