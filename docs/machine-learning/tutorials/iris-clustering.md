---
title: Usar o ML.NET para agrupar flores Iris (clustering)
description: Saiba como usar o ML.NET em um cenário de clustering
author: pkulikov
ms.author: johalex
ms.date: 07/02/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: bb41fd317507c14b46aea94e1ce576e390932a65
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49453184"
---
# <a name="tutorial-use-mlnet-to-cluster-iris-flowers-clustering"></a><span data-ttu-id="b1e26-103">Tutorial: usar o ML.NET para agrupar flores Iris (clustering)</span><span class="sxs-lookup"><span data-stu-id="b1e26-103">Tutorial: Use ML.NET to cluster iris flowers (clustering)</span></span>

> [!NOTE]
> <span data-ttu-id="b1e26-104">Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="b1e26-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="b1e26-105">Para obter mais informações, confira a [Introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="b1e26-105">For more information, see the [ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="b1e26-106">Este tutorial ilustra como usar o ML.NET para criar um [modelo de clustering](../resources/tasks.md#clustering) para o [conjunto de dados de flor Iris](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span><span class="sxs-lookup"><span data-stu-id="b1e26-106">This tutorial illustrates how to use ML.NET to build a [clustering model](../resources/tasks.md#clustering) for the [iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span></span>

<span data-ttu-id="b1e26-107">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="b1e26-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="b1e26-108">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="b1e26-108">Understand the problem</span></span>
> - <span data-ttu-id="b1e26-109">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="b1e26-109">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="b1e26-110">Preparar os dados</span><span class="sxs-lookup"><span data-stu-id="b1e26-110">Prepare the data</span></span>
> - <span data-ttu-id="b1e26-111">Carregar e transformar os dados</span><span class="sxs-lookup"><span data-stu-id="b1e26-111">Load and transform the data</span></span>
> - <span data-ttu-id="b1e26-112">Escolher um algoritmo de aprendizado</span><span class="sxs-lookup"><span data-stu-id="b1e26-112">Choose a learning algorithm</span></span>
> - <span data-ttu-id="b1e26-113">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="b1e26-113">Train the model</span></span>
> - <span data-ttu-id="b1e26-114">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="b1e26-114">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b1e26-115">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b1e26-115">Prerequisites</span></span>

- <span data-ttu-id="b1e26-116">[Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="b1e26-116">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="b1e26-117">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="b1e26-117">Understand the problem</span></span>

<span data-ttu-id="b1e26-118">Esse problema abrange como dividir o conjunto de flores Iris em grupos diferentes com base nas características da flor.</span><span class="sxs-lookup"><span data-stu-id="b1e26-118">This problem is about dividing the set of iris flowers in different groups based on the flower features.</span></span> <span data-ttu-id="b1e26-119">Essas características são o comprimento e largura de uma sépala e o comprimento e a largura de uma pétala.</span><span class="sxs-lookup"><span data-stu-id="b1e26-119">Those features are the length and width of a sepal and the length and width of a petal.</span></span> <span data-ttu-id="b1e26-120">Para este tutorial, considere que o tipo de cada flor é desconhecido.</span><span class="sxs-lookup"><span data-stu-id="b1e26-120">For this tutorial, assume that the type of each flower is unknown.</span></span> <span data-ttu-id="b1e26-121">Você deseja conhecer a estrutura de um conjunto de dados por meio de suas características e prever como uma instância de dados se encaixa nessa estrutura.</span><span class="sxs-lookup"><span data-stu-id="b1e26-121">You want to learn the structure of a data set from the features and predict how a data instance fits this structure.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="b1e26-122">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="b1e26-122">Select the appropriate machine learning task</span></span>

<span data-ttu-id="b1e26-123">Como você não sabe a qual grupo cada flor pertence, escolha a tarefa [aprendizado de máquina não supervisionado](../resources/glossary.md#unsupervised-machine-learning).</span><span class="sxs-lookup"><span data-stu-id="b1e26-123">As you don't know to which group each flower belongs to, you choose the [unsupervised machine learning](../resources/glossary.md#unsupervised-machine-learning) task.</span></span> <span data-ttu-id="b1e26-124">Para dividir um conjunto de dados em grupos de forma que os elementos no mesmo grupo sejam mais semelhantes uns aos outros do que aos elementos de outros grupos, use a tarefa de aprendizado de máquina [clustering](../resources/tasks.md#clustering).</span><span class="sxs-lookup"><span data-stu-id="b1e26-124">To divide a data set in groups in such a way that elements in the same group are more similar to each other than to those in other groups, use a [clustering](../resources/tasks.md#clustering) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="b1e26-125">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="b1e26-125">Create a console application</span></span>

1. <span data-ttu-id="b1e26-126">Abra o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="b1e26-126">Open Visual Studio 2017.</span></span> <span data-ttu-id="b1e26-127">Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="b1e26-127">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="b1e26-128">Na caixa de diálogo **Novo Projeto**, selecione o nó **Visual C#** seguido pelo nó **.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="b1e26-128">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="b1e26-129">Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="b1e26-129">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="b1e26-130">Na caixa de texto **Nome**, digite "IrisClustering" e, em seguida, selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="b1e26-130">In the **Name** text box, type "IrisClustering" and then select the **OK** button.</span></span>

1. <span data-ttu-id="b1e26-131">Crie um diretório chamado *Dados* em seu projeto para armazenar o conjunto de dados e os arquivos de modelo:</span><span class="sxs-lookup"><span data-stu-id="b1e26-131">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="b1e26-132">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Nova Pasta**.</span><span class="sxs-lookup"><span data-stu-id="b1e26-132">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="b1e26-133">Digite "Data" e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="b1e26-133">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="b1e26-134">Instale o pacote NuGet **Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="b1e26-134">Install the **Microsoft.ML** NuGet package:</span></span>

    <span data-ttu-id="b1e26-135">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="b1e26-135">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="b1e26-136">Escolha "nuget.org" como a origem do Pacote, selecione a guia **Procurar**, pesquise **Microsoft.ML**, selecione o pacote na lista e escolha o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="b1e26-136">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="b1e26-137">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="b1e26-137">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-the-data"></a><span data-ttu-id="b1e26-138">Preparar os dados</span><span class="sxs-lookup"><span data-stu-id="b1e26-138">Prepare the data</span></span>

1. <span data-ttu-id="b1e26-139">Baixe o conjunto de dados [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) e salve-o na pasta *Dados* que você criou na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="b1e26-139">Download the [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) data set and save it to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="b1e26-140">Para obter mais informações sobre o conjunto de dados Iris, confira a página da Wikipédia [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) (Conjunto de dados de flor Iris) e a página [Iris Data Set](http://archive.ics.uci.edu/ml/datasets/Iris) (Conjunto de dados Iris), que é a fonte do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="b1e26-140">For more information about the iris data set, see the [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia page and the [Iris Data Set](http://archive.ics.uci.edu/ml/datasets/Iris) page, which is the source of the data set.</span></span>

1. <span data-ttu-id="b1e26-141">No **Gerenciador de Soluções**, clique com o botão direito do mouse no arquivo *iris.data* e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="b1e26-141">In **Solution Explorer**, right-click the *iris.data* file and select **Properties**.</span></span> <span data-ttu-id="b1e26-142">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.</span><span class="sxs-lookup"><span data-stu-id="b1e26-142">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="b1e26-143">O arquivo *iris.data* contém cinco colunas que representam:</span><span class="sxs-lookup"><span data-stu-id="b1e26-143">The *iris.data* file contains five columns that represent:</span></span>

- <span data-ttu-id="b1e26-144">o comprimento da sépala em centímetros</span><span class="sxs-lookup"><span data-stu-id="b1e26-144">sepal length in centimetres</span></span>
- <span data-ttu-id="b1e26-145">a largura da sépala em centímetros</span><span class="sxs-lookup"><span data-stu-id="b1e26-145">sepal width in centimetres</span></span>
- <span data-ttu-id="b1e26-146">o comprimento da pétala em centímetros</span><span class="sxs-lookup"><span data-stu-id="b1e26-146">petal length in centimetres</span></span>
- <span data-ttu-id="b1e26-147">a largura da pétala em centímetros</span><span class="sxs-lookup"><span data-stu-id="b1e26-147">petal width in centimetres</span></span>
- <span data-ttu-id="b1e26-148">o tipo de flor Iris</span><span class="sxs-lookup"><span data-stu-id="b1e26-148">type of iris flower</span></span>

<span data-ttu-id="b1e26-149">Para exemplificar o clustering, este tutorial ignora a última coluna.</span><span class="sxs-lookup"><span data-stu-id="b1e26-149">For the sake of the clustering example, this tutorial ignores the last column.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="b1e26-150">Criar classes de dados</span><span class="sxs-lookup"><span data-stu-id="b1e26-150">Create data classes</span></span>

<span data-ttu-id="b1e26-151">Crie classes para os dados de entrada e as previsões:</span><span class="sxs-lookup"><span data-stu-id="b1e26-151">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="b1e26-152">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="b1e26-152">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="b1e26-153">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *IrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="b1e26-153">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *IrisData.cs*.</span></span> <span data-ttu-id="b1e26-154">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="b1e26-154">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="b1e26-155">Adicione a seguinte diretiva `using` ao novo arquivo:</span><span class="sxs-lookup"><span data-stu-id="b1e26-155">Add the following `using` directive to the new file:</span></span>

   [!code-csharp[Add necessary usings](../../../samples/machine-learning/tutorials/IrisClustering/IrisData.cs#1)]

<span data-ttu-id="b1e26-156">Remova a definição de classe existente e adicione o código a seguir, que define as classes `IrisData` e `ClusterPrediction`, para o arquivo *IrisData.cs*:</span><span class="sxs-lookup"><span data-stu-id="b1e26-156">Remove the existing class definition and add the following code, which defines the classes `IrisData` and `ClusterPrediction`, to the *IrisData.cs* file:</span></span>

[!code-csharp[Define data classes](../../../samples/machine-learning/tutorials/IrisClustering/IrisData.cs#2)]

<span data-ttu-id="b1e26-157">`IrisData` é a classe de dados de entrada e tem definições de cada característica provenientes do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="b1e26-157">`IrisData` is the input data class and has definitions for each feature from the data set.</span></span> <span data-ttu-id="b1e26-158">Use o atributo [Column](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) para especificar os índices das colunas de origem no arquivo de conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="b1e26-158">Use the [Column](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) attribute to specify the indices of the source columns in the data set file.</span></span>

<span data-ttu-id="b1e26-159">A classe `ClusterPrediction` representa a saída do modelo de clustering aplicado a uma instância de `IrisData`.</span><span class="sxs-lookup"><span data-stu-id="b1e26-159">The `ClusterPrediction` class represents the output of the clustering model applied to an `IrisData` instance.</span></span> <span data-ttu-id="b1e26-160">Use o atributo [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) para associar os campos `PredictedClusterId` e `Distances` às colunas **PredictedLabel** e **Score**, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="b1e26-160">Use the [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) attribute to bind the `PredictedClusterId` and `Distances` fields to the **PredictedLabel** and **Score** columns respectively.</span></span> <span data-ttu-id="b1e26-161">No caso da tarefa clustering, essas colunas têm o seguinte significado:</span><span class="sxs-lookup"><span data-stu-id="b1e26-161">In case of the clustering task those columns have the following meaning:</span></span>

- <span data-ttu-id="b1e26-162">A coluna **PredictedLabel** contém a ID do cluster previsto.</span><span class="sxs-lookup"><span data-stu-id="b1e26-162">**PredictedLabel** column contains the ID of the predicted cluster.</span></span>
- <span data-ttu-id="b1e26-163">A coluna **Score** contém uma matriz com as distâncias euclidianas quadradas para os centroides de cluster.</span><span class="sxs-lookup"><span data-stu-id="b1e26-163">**Score** column contains an array with squared Euclidean distances to the cluster centroids.</span></span> <span data-ttu-id="b1e26-164">O comprimento da matriz é igual ao número de clusters.</span><span class="sxs-lookup"><span data-stu-id="b1e26-164">The array length is equal to the number of clusters.</span></span>

> [!NOTE]
> <span data-ttu-id="b1e26-165">Use o tipo `float` para representar valores de ponto flutuante nas classes de dados de entrada e previsão.</span><span class="sxs-lookup"><span data-stu-id="b1e26-165">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="b1e26-166">Definir dados e caminhos de modelo</span><span class="sxs-lookup"><span data-stu-id="b1e26-166">Define data and model paths</span></span>

<span data-ttu-id="b1e26-167">Volte para o arquivo *Program.cs* e adicione dois campos para armazenar os caminhos no arquivo de conjunto de dados e no arquivo para salvar o modelo:</span><span class="sxs-lookup"><span data-stu-id="b1e26-167">Go back to the *Program.cs* file and add two fields to hold the paths to the data set file and to the file to save the model:</span></span>

- <span data-ttu-id="b1e26-168">`_dataPath` contém o caminho para o arquivo com o conjunto de dados usado para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="b1e26-168">`_dataPath` contains the path to the file with the data set used to train the model.</span></span>
- <span data-ttu-id="b1e26-169">`_modelPath` contém o caminho para o arquivo em que o modelo treinado está armazenado.</span><span class="sxs-lookup"><span data-stu-id="b1e26-169">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="b1e26-170">Adicione o seguinte código logo acima do método `Main` para especificar estes caminhos:</span><span class="sxs-lookup"><span data-stu-id="b1e26-170">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Initialize paths](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#1)]

<span data-ttu-id="b1e26-171">Para fazer com que o código anterior seja compilado, adicione as seguintes diretivas `using` ao início do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="b1e26-171">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add usings for paths](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#2)]

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="b1e26-172">Criar um pipeline de aprendizado</span><span class="sxs-lookup"><span data-stu-id="b1e26-172">Create a learning pipeline</span></span>

<span data-ttu-id="b1e26-173">Adicione as seguintes diretivas `using` adicionais ao início do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="b1e26-173">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[Add Microsoft.ML usings](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#3)]

<span data-ttu-id="b1e26-174">No método `Main`, substitua `Console.WriteLine("Hello World!")` pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="b1e26-174">In the `Main` method, replace the `Console.WriteLine("Hello World!")` with the following code:</span></span>

[!code-csharp[Call the Train method](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#4)]

<span data-ttu-id="b1e26-175">O método `Train` treina o modelo.</span><span class="sxs-lookup"><span data-stu-id="b1e26-175">The `Train` method trains the model.</span></span> <span data-ttu-id="b1e26-176">Crie esse método logo abaixo do método `Main`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="b1e26-176">Create that method just below the `Main` method, using the following code:</span></span>

```csharp
private static PredictionModel<IrisData, ClusterPrediction> Train()
{

}
```

<span data-ttu-id="b1e26-177">O pipeline de aprendizado carrega todos os dados e algoritmos necessários para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="b1e26-177">The learning pipeline loads all of the data and algorithms necessary to train the model.</span></span> <span data-ttu-id="b1e26-178">Adicione o seguinte código ao método `Train`:</span><span class="sxs-lookup"><span data-stu-id="b1e26-178">Add the following code into the `Train` method:</span></span>

[!code-csharp[Initialize pipeline](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#5)]

## <a name="load-and-transform-data"></a><span data-ttu-id="b1e26-179">Carregar e transformar dados</span><span class="sxs-lookup"><span data-stu-id="b1e26-179">Load and transform data</span></span>

<span data-ttu-id="b1e26-180">A primeira etapa a ser realizada é carregar o conjunto de dados de treinamento.</span><span class="sxs-lookup"><span data-stu-id="b1e26-180">The first step to perform is to load the training data set.</span></span> <span data-ttu-id="b1e26-181">Em nosso caso, o conjunto de dados de treinamento é armazenado no arquivo de texto com um caminho definido pelo campo `_dataPath`.</span><span class="sxs-lookup"><span data-stu-id="b1e26-181">In our case, the training data set is stored in the text file with a path defined by the `_dataPath` field.</span></span> <span data-ttu-id="b1e26-182">As colunas no arquivo são separadas por uma vírgula (",").</span><span class="sxs-lookup"><span data-stu-id="b1e26-182">Columns in the file are separated by the comma (",").</span></span> <span data-ttu-id="b1e26-183">Adicione o seguinte código ao método `Train`:</span><span class="sxs-lookup"><span data-stu-id="b1e26-183">Add the following code into the `Train` method:</span></span>

[!code-csharp[Add step to load data](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#6)]

<span data-ttu-id="b1e26-184">A próxima etapa é combinar todas as colunas de característica na coluna **Features** usando a classe de transformação <xref:Microsoft.ML.Legacy.Transforms.ColumnConcatenator>.</span><span class="sxs-lookup"><span data-stu-id="b1e26-184">The next step is to combine all of the feature columns into the **Features** column using the <xref:Microsoft.ML.Legacy.Transforms.ColumnConcatenator> transformation class.</span></span> <span data-ttu-id="b1e26-185">Por padrão, um algoritmo de aprendizado processa apenas os recursos da coluna **Features**.</span><span class="sxs-lookup"><span data-stu-id="b1e26-185">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="b1e26-186">Adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="b1e26-186">Add the following code:</span></span>

[!code-csharp[Add step to concatenate columns](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#7)]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="b1e26-187">Escolher um algoritmo de aprendizado</span><span class="sxs-lookup"><span data-stu-id="b1e26-187">Choose a learning algorithm</span></span>

<span data-ttu-id="b1e26-188">Após adicionar os dados ao pipeline e transformá-los no formato de entrada correto, selecione um algoritmo de aprendizado (**aluno**).</span><span class="sxs-lookup"><span data-stu-id="b1e26-188">After adding the data to the pipeline and transforming it into the correct input format, you select a learning algorithm (**learner**).</span></span> <span data-ttu-id="b1e26-189">O aprendiz treina o modelo.</span><span class="sxs-lookup"><span data-stu-id="b1e26-189">The learner trains the model.</span></span> <span data-ttu-id="b1e26-190">O ML.NET fornece um aprendiz <xref:Microsoft.ML.Legacy.Trainers.KMeansPlusPlusClusterer> que implementa o [algoritmo k-means](https://en.wikipedia.org/wiki/K-means_clustering) com um método melhor para escolher os centroides iniciais do cluster.</span><span class="sxs-lookup"><span data-stu-id="b1e26-190">ML.NET provides a <xref:Microsoft.ML.Legacy.Trainers.KMeansPlusPlusClusterer> learner that implements [k-means algorithm](https://en.wikipedia.org/wiki/K-means_clustering) with an improved method for choosing the initial cluster centroids.</span></span>

<span data-ttu-id="b1e26-191">Adicione o seguinte código ao método `Train` após o código de processamento de dados adicionado na etapa anterior:</span><span class="sxs-lookup"><span data-stu-id="b1e26-191">Add the following code into the `Train` method following the data processing code added in the previous step:</span></span>

[!code-csharp[Add a learner step](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#8)]

<span data-ttu-id="b1e26-192">Use a propriedade <xref:Microsoft.ML.Legacy.Trainers.KMeansPlusPlusClusterer.K?displayProperty=nameWithType> para especificar o número de clusters.</span><span class="sxs-lookup"><span data-stu-id="b1e26-192">Use the <xref:Microsoft.ML.Legacy.Trainers.KMeansPlusPlusClusterer.K?displayProperty=nameWithType> property to specify number of clusters.</span></span> <span data-ttu-id="b1e26-193">O código acima especifica que o conjunto de dados deve ser dividido em três clusters.</span><span class="sxs-lookup"><span data-stu-id="b1e26-193">The code above specifies that the data set should be split in three clusters.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="b1e26-194">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="b1e26-194">Train the model</span></span>

<span data-ttu-id="b1e26-195">As etapas adicionadas nas seções anteriores prepararam o pipeline para treinamento, no entanto, nenhuma foi executada.</span><span class="sxs-lookup"><span data-stu-id="b1e26-195">The steps added in the preceding sections prepared the pipeline for training, however, none have been executed.</span></span> <span data-ttu-id="b1e26-196">O método `pipeline.Train<TInput, TOutput>` produz o modelo que aceita uma instância do tipo `TInput` e produz uma instância do tipo `TOutput`.</span><span class="sxs-lookup"><span data-stu-id="b1e26-196">The `pipeline.Train<TInput, TOutput>` method produces the model that takes in an instance of the `TInput` type and outputs an instance of the `TOutput` type.</span></span> <span data-ttu-id="b1e26-197">Adicione o seguinte código ao método `Train`:</span><span class="sxs-lookup"><span data-stu-id="b1e26-197">Add the following code into the `Train` method:</span></span>

[!code-csharp[Train the model and return](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#9)]

### <a name="save-the-model"></a><span data-ttu-id="b1e26-198">Salvar o modelo</span><span class="sxs-lookup"><span data-stu-id="b1e26-198">Save the model</span></span>

<span data-ttu-id="b1e26-199">Neste ponto, você tem um modelo que pode ser integrado em qualquer um dos seus aplicativos .NET existentes ou novos.</span><span class="sxs-lookup"><span data-stu-id="b1e26-199">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="b1e26-200">Para salvar seu modelo em um arquivo .zip, adicione o seguinte código no método `Main` abaixo da chamada ao método `Train`:</span><span class="sxs-lookup"><span data-stu-id="b1e26-200">To save your model to a .zip file, add the following code to the `Main` method below the call to the `Train` method:</span></span>

[!code-csharp[Save the model](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#10)]

<span data-ttu-id="b1e26-201">Usar um `await` no método `Main` significa que o método `Main` deve ter o modificador `async` e retornar um `Task`:</span><span class="sxs-lookup"><span data-stu-id="b1e26-201">Using `await` in the `Main` method means the `Main` method must have the `async` modifier and return a `Task`:</span></span>

[!code-csharp[Make the Main method async](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#11)]

<span data-ttu-id="b1e26-202">Também é preciso adicionar a seguinte diretiva `using` ao início do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="b1e26-202">You also need to add the following `using` directive at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add System.Threading.Tasks using](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#12)]

<span data-ttu-id="b1e26-203">Como o método `async Main` é um novo recurso adicionado no C# 7.1 e a versão da linguagem padrão do projeto é C# 7.0, é necessário alterar a versão da linguagem para C# 7.1 ou superior.</span><span class="sxs-lookup"><span data-stu-id="b1e26-203">Because the `async Main` method is the feature added in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span> <span data-ttu-id="b1e26-204">Para fazer isso, clique com o botão direito do mouse no nó do projeto no **Gerenciador de Soluções** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="b1e26-204">To do that, right-click the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="b1e26-205">Selecione a guia **Build** e o botão **Avançado**.</span><span class="sxs-lookup"><span data-stu-id="b1e26-205">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="b1e26-206">No menu suspenso, selecione **C# 7.1** (ou uma versão posterior).</span><span class="sxs-lookup"><span data-stu-id="b1e26-206">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="b1e26-207">Selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="b1e26-207">Select the **OK** button.</span></span>

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="b1e26-208">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="b1e26-208">Use the model for predictions</span></span>

<span data-ttu-id="b1e26-209">Crie a classe `TestIrisData` para hospedar as instâncias de dados de teste:</span><span class="sxs-lookup"><span data-stu-id="b1e26-209">Create the `TestIrisData` class to house test data instances:</span></span>

1. <span data-ttu-id="b1e26-210">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="b1e26-210">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="b1e26-211">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *TestIrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="b1e26-211">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestIrisData.cs*.</span></span> <span data-ttu-id="b1e26-212">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="b1e26-212">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="b1e26-213">Modifique a classe para ser estática, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b1e26-213">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[Make class static](../../../samples/machine-learning/tutorials/IrisClustering/TestIrisData.cs#1)]

<span data-ttu-id="b1e26-214">Este tutorial apresenta uma instância de dados de Iris dentro dessa classe.</span><span class="sxs-lookup"><span data-stu-id="b1e26-214">This tutorial introduces one iris data instance within this class.</span></span> <span data-ttu-id="b1e26-215">Você pode adicionar outros cenários para fazer experimentos com o modelo.</span><span class="sxs-lookup"><span data-stu-id="b1e26-215">You can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="b1e26-216">Adicione o seguinte código à classe `TestIrisData`:</span><span class="sxs-lookup"><span data-stu-id="b1e26-216">Add the following code into the `TestIrisData` class:</span></span>

[!code-csharp[Test data](../../../samples/machine-learning/tutorials/IrisClustering/TestIrisData.cs#2)]

<span data-ttu-id="b1e26-217">Para descobrir a qual cluster o item especificado pertence, volte para o arquivo *Program.cs* e adicione o seguinte código no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="b1e26-217">To find out the cluster to which the specified item belongs to, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict and output results](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#13)]

<span data-ttu-id="b1e26-218">Execute o programa para ver qual cluster contém a instância de dados especificada e a distância quadrada daquela instância aos centroides do cluster.</span><span class="sxs-lookup"><span data-stu-id="b1e26-218">Run the program to see which cluster contains the specified data instance and squared distances from that instance to the cluster centroids.</span></span> <span data-ttu-id="b1e26-219">Seus resultados devem ser semelhantes aos seguintes.</span><span class="sxs-lookup"><span data-stu-id="b1e26-219">Your results should be similar to the following.</span></span> <span data-ttu-id="b1e26-220">À medida que o pipeline é processado, ele pode exibir avisos ou mensagens de processamento.</span><span class="sxs-lookup"><span data-stu-id="b1e26-220">As the pipeline processes, it might display warnings or processing messages.</span></span> <span data-ttu-id="b1e26-221">Esses itens foram removidos da saída a seguir para deixá-la mais clara.</span><span class="sxs-lookup"><span data-stu-id="b1e26-221">These have been removed from the following output for clarity.</span></span>

```text
Cluster: 2
Distances: 0.4192338 0.0008847713 0.9660053
```

<span data-ttu-id="b1e26-222">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="b1e26-222">Congratulations!</span></span> <span data-ttu-id="b1e26-223">Você agora construiu um modelo de aprendizado de máquina para clustering de Iris e o usou para fazer previsões.</span><span class="sxs-lookup"><span data-stu-id="b1e26-223">You've now successfully built a machine learning model for iris clustering and used it to make predictions.</span></span> <span data-ttu-id="b1e26-224">Encontre o código-fonte deste tutorial no repositório do GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisClustering).</span><span class="sxs-lookup"><span data-stu-id="b1e26-224">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisClustering) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b1e26-225">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="b1e26-225">Next steps</span></span>

<span data-ttu-id="b1e26-226">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="b1e26-226">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="b1e26-227">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="b1e26-227">Understand the problem</span></span>
> - <span data-ttu-id="b1e26-228">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="b1e26-228">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="b1e26-229">Preparar os dados</span><span class="sxs-lookup"><span data-stu-id="b1e26-229">Prepare the data</span></span>
> - <span data-ttu-id="b1e26-230">Carregar e transformar os dados</span><span class="sxs-lookup"><span data-stu-id="b1e26-230">Load and transform the data</span></span>
> - <span data-ttu-id="b1e26-231">Escolher um algoritmo de aprendizado</span><span class="sxs-lookup"><span data-stu-id="b1e26-231">Choose a learning algorithm</span></span>
> - <span data-ttu-id="b1e26-232">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="b1e26-232">Train the model</span></span>
> - <span data-ttu-id="b1e26-233">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="b1e26-233">Use the model for predictions</span></span>

<span data-ttu-id="b1e26-234">Confira nosso repositório GitHub para continuar aprendendo e encontrar mais amostras.</span><span class="sxs-lookup"><span data-stu-id="b1e26-234">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="b1e26-235">dotnet/machinelearning GitHub repository</span><span class="sxs-lookup"><span data-stu-id="b1e26-235">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
