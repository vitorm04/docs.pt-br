---
title: Usar o ML.NET em um cenário de recomendação de filmes
description: Descubra como usar o ML.NET em um cenário de recomendação para recomendar filmes aos usuários.
author: briacht
ms.author: johalex
ms.date: 03/08/2019
ms.custom: mvc
ms.topic: tutorial
ms.openlocfilehash: e78772df1cf7e5f8999305a1b726a7085f94601b
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410063"
---
# <a name="tutorial-create-a-movie-recommender-with-mlnet"></a><span data-ttu-id="4b2ab-103">Tutorial: Criar um sistema de recomendação de filmes com o ML.NET</span><span class="sxs-lookup"><span data-stu-id="4b2ab-103">Tutorial: Create a Movie Recommender with ML.NET</span></span>

<span data-ttu-id="4b2ab-104">Este tutorial de exemplo ilustra o uso do ML.NET para criação de um sistema de recomendação de filmes por meio de um aplicativo de console .NET Core usando C# no Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-104">This sample tutorial illustrates using ML.NET to build a movie recommender via a .NET Core console application using C# in Visual Studio 2017.</span></span>

<span data-ttu-id="4b2ab-105">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="4b2ab-106">Selecionar um algoritmo de aprendizado de máquina</span><span class="sxs-lookup"><span data-stu-id="4b2ab-106">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="4b2ab-107">Preparar e carregar os dados</span><span class="sxs-lookup"><span data-stu-id="4b2ab-107">Prepare and load your data</span></span>
> * <span data-ttu-id="4b2ab-108">Criar e treinar um modelo</span><span class="sxs-lookup"><span data-stu-id="4b2ab-108">Build and train a model</span></span>
> * <span data-ttu-id="4b2ab-109">Avaliar um modelo</span><span class="sxs-lookup"><span data-stu-id="4b2ab-109">Evaluate a model</span></span>
> * <span data-ttu-id="4b2ab-110">Implantar e consumir um modelo</span><span class="sxs-lookup"><span data-stu-id="4b2ab-110">Deploy and consume a model</span></span>

> [!NOTE]
> <span data-ttu-id="4b2ab-111">Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-111">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="4b2ab-112">Para obter mais informações, visite [a introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="4b2ab-112">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="4b2ab-113">Este tutorial e uma amostra relacionada estão usando o **ML.NET versão 0.11** no momento.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-113">This tutorial and related sample are currently using **ML.NET version 0.11**.</span></span> <span data-ttu-id="4b2ab-114">Saiba mais nas notas de versão no [repositório do GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="4b2ab-114">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="4b2ab-115">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation).</span><span class="sxs-lookup"><span data-stu-id="4b2ab-115">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="4b2ab-116">Fluxo de trabalho de aprendizado de máquina</span><span class="sxs-lookup"><span data-stu-id="4b2ab-116">Machine learning workflow</span></span>
<span data-ttu-id="4b2ab-117">Você usará as seguintes etapas para realizar sua tarefa, bem como qualquer outra tarefa do ML.NET:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-117">You will use the following steps to accomplish your task, as well as any other ML.NET task:</span></span>

1. [<span data-ttu-id="4b2ab-118">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="4b2ab-118">Load your data</span></span>](#load-your-data)
2. [<span data-ttu-id="4b2ab-119">Criar e treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="4b2ab-119">Build and train your model</span></span>](#build-and-train-your-model)
3. [<span data-ttu-id="4b2ab-120">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="4b2ab-120">Evaluate your model</span></span>](#evaluate-your-model)
4. [<span data-ttu-id="4b2ab-121">Usar o modelo</span><span class="sxs-lookup"><span data-stu-id="4b2ab-121">Use your model</span></span>](#use-your-model)

## <a name="prerequisites"></a><span data-ttu-id="4b2ab-122">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="4b2ab-122">Prerequisites</span></span>

* <span data-ttu-id="4b2ab-123">[Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-123">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="4b2ab-124">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="4b2ab-124">Select the appropriate machine learning task</span></span>

<span data-ttu-id="4b2ab-125">Há várias maneiras de abordar problemas de recomendação, como recomendar uma lista de filmes ou uma lista de produtos relacionados, mas, nesse caso, você preverá qual classificação (1 a 5) um usuário dará a um filme específico e recomendará esse filme se ele for superior a um limite definido (quanto maior a classificação, maior a probabilidade de um usuário gostar de um filme específico).</span><span class="sxs-lookup"><span data-stu-id="4b2ab-125">There are several ways to approach recommendation problems, such as recommending a list of movies or recommending a list of related products, but in this case you will predict what rating (1-5) a user will give to a particular movie and recommend that movie if it's higher than a defined threshold (the higher the rating, the higher the likelihood of a user liking a particular movie).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="4b2ab-126">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="4b2ab-126">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="4b2ab-127">Criar um projeto</span><span class="sxs-lookup"><span data-stu-id="4b2ab-127">Create a project</span></span>

1. <span data-ttu-id="4b2ab-128">Abra o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-128">Open Visual Studio 2017.</span></span> <span data-ttu-id="4b2ab-129">Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-129">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="4b2ab-130">Na caixa de diálogo **Novo Projeto**, selecione o nó **Visual C#** seguido pelo nó **.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-130">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="4b2ab-131">Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-131">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="4b2ab-132">Na caixa de texto **Nome**, digite "MovieRecommender" e, em seguida, selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-132">In the **Name** text box, type "MovieRecommender" and then select the **OK** button.</span></span>

2. <span data-ttu-id="4b2ab-133">Crie um diretório chamado *Data* no projeto para armazenar o conjunto de dados:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-133">Create a directory named *Data* in your project to store the data set:</span></span>

    <span data-ttu-id="4b2ab-134">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Nova Pasta**.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-134">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="4b2ab-135">Digite "Data" e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-135">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="4b2ab-136">Instale os pacotes NuGet **Microsoft.ML** e **Microsoft.ML.Recommender**:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-136">Install the **Microsoft.ML** and **Microsoft.ML.Recommender** NuGet Packages:</span></span>

    <span data-ttu-id="4b2ab-137">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-137">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="4b2ab-138">Escolha "nuget.org" como a origem do Pacote, selecione a guia **Procurar**, pesquise **Microsoft.ML**, selecione o pacote na lista e escolha o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-138">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="4b2ab-139">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-139">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="4b2ab-140">Repita essas etapas para o **Microsoft.ML.Recommender**.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-140">Repeat these steps for **Microsoft.ML.Recommender**.</span></span>

  > [!NOTE]
  > <span data-ttu-id="4b2ab-141">Este tutorial usa o **Microsoft.ML v0.11.0** e o **Microsoft.ML.Recommender v0.11.0**.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-141">This tutorial uses **Microsoft.ML v0.11.0** and **Microsoft.ML.Recommender v0.11.0**.</span></span>
    
4. <span data-ttu-id="4b2ab-142">Adicione as seguintes instruções `using` à parte superior do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-142">Add the following `using` statements at the top of your *Program.cs* file:</span></span>
    
    [!code-csharp[UsingStatements](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UsingStatements "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="4b2ab-143">Baixar os dados</span><span class="sxs-lookup"><span data-stu-id="4b2ab-143">Download your data</span></span>

1. <span data-ttu-id="4b2ab-144">Baixe os dois conjuntos de dados e salve-os na pasta *Data* criada anteriormente:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-144">Download the two datasets and save them to the *Data* folder you previously created:</span></span>

*   <span data-ttu-id="4b2ab-145">Clique com o botão direito do mouse em [*recommendation-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) e selecione "Salvar Link (ou Destino) como..."</span><span class="sxs-lookup"><span data-stu-id="4b2ab-145">Right click on [*recommendation-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) and select "Save Link (or Target) As..."</span></span>
*   <span data-ttu-id="4b2ab-146">Clique com o botão direito do mouse em [*recommendation-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) e selecione "Salvar Link (ou Destino) como..."</span><span class="sxs-lookup"><span data-stu-id="4b2ab-146">Right click on [*recommendation-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="4b2ab-147">Salve os arquivos \*.csv na pasta *Data* ou, depois de salvá-los em outro lugar, mova os arquivos \*.csv para a pasta *Data*.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-147">Make sure you either save the \*.csv files to the *Data* folder, or after you save it elsewhere, move the \*.csv files to the *Data* folder.</span></span>

2. <span data-ttu-id="4b2ab-148">No Gerenciador de Soluções, clique com o botão direito do mouse em cada um dos arquivos \*.csv e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-148">In Solution Explorer, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="4b2ab-149">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-149">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

   ![Copiar se for o mais recente no VS](./media/movie-recommendation/copytoout.gif)

## <a name="load-your-data"></a><span data-ttu-id="4b2ab-151">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="4b2ab-151">Load your data</span></span>

<span data-ttu-id="4b2ab-152">A primeira etapa no processo do ML.NET é preparar e carregar os dados de treinamento e teste de modelo.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-152">The first step in the ML.NET process is to prepare and load your model training and testing data.</span></span>

<span data-ttu-id="4b2ab-153">Os dados de classificações de recomendação são divididos nos conjuntos de dados `Train` e `Test`.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-153">The recommendation ratings data is split into `Train` and `Test` datasets.</span></span> <span data-ttu-id="4b2ab-154">Os dados `Train` são usados para ajustar o modelo.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-154">The `Train` data is used to fit your model.</span></span> <span data-ttu-id="4b2ab-155">Os dados `Test` são usados para fazer previsões com o modelo treinado e avaliar o desempenho do modelo.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-155">The `Test` data is used to make predictions with your trained model and evaluate model performance.</span></span> <span data-ttu-id="4b2ab-156">É comum ter uma divisão 80/20 com os dados `Train` e `Test`.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-156">It's common to have an 80/20 split with `Train` and `Test` data.</span></span>

<span data-ttu-id="4b2ab-157">Segue abaixo uma visualização dos dados nos arquivos \*.csv:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-157">Below is a preview of the data from your \*.csv files:</span></span>

![visualização de dados](./media/movie-recommendation/csv-dataset-preview.png)

<span data-ttu-id="4b2ab-159">Nos arquivos \*.csv, há quatro colunas:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-159">In the \*.csv files, there are four columns:</span></span>

* `userId`
* `movieId`
* `rating`
* `timestamp`

<span data-ttu-id="4b2ab-160">No aprendizado de máquina, as colunas que são usadas para fazer uma previsão são chamadas [Recursos](../resources/glossary.md#feature) e a coluna com a previsão retornada é chamada o [Rótulo](../resources/glossary.md#label).</span><span class="sxs-lookup"><span data-stu-id="4b2ab-160">In machine learning, the columns that are used to make a prediction are called [Features](../resources/glossary.md#feature), and the column with the returned prediction is called the [Label](../resources/glossary.md#label).</span></span>

<span data-ttu-id="4b2ab-161">Você deseja prever as classificações de filmes, portanto, a coluna de classificação é o `Label`.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-161">You want to predict movie ratings, so the rating column is the `Label`.</span></span> <span data-ttu-id="4b2ab-162">As outras três colunas, `userId`, `movieId` e `timestamp`, são todos `Features` usados para prever o `Label`.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-162">The other three columns, `userId`, `movieId`, and `timestamp` are all `Features` used to predict the `Label`.</span></span>

| <span data-ttu-id="4b2ab-163">Recursos</span><span class="sxs-lookup"><span data-stu-id="4b2ab-163">Features</span></span>      | <span data-ttu-id="4b2ab-164">Rotular</span><span class="sxs-lookup"><span data-stu-id="4b2ab-164">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |
| `timestamp`     |               |

<span data-ttu-id="4b2ab-165">Cabe a você decidir quais `Features` são usados para prever o `Label`.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-165">It's up to you to decide which `Features` are used to predict the `Label`.</span></span> <span data-ttu-id="4b2ab-166">Você também pode usar métodos como [Importância de Permuta do Recurso](../how-to-guides/determine-global-feature-importance-in-model.md) para ajudar a selecionar os melhores `Features`.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-166">You can also use methods like [Feature Permutation Importance](../how-to-guides/determine-global-feature-importance-in-model.md) to help with selecting the best `Features`.</span></span>

<span data-ttu-id="4b2ab-167">Nesse caso, você deve eliminar a coluna `timestamp` como um `Feature` porque o carimbo de data/hora não afeta como um usuário classifica determinado filme e, portanto, não contribui para uma previsão mais precisa:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-167">In this case, you should eliminate the `timestamp` column as a `Feature` because the timestamp does not really affect how a user rates a given movie and thus would not contribute to making a more accurate prediction:</span></span>

| <span data-ttu-id="4b2ab-168">Recursos</span><span class="sxs-lookup"><span data-stu-id="4b2ab-168">Features</span></span>      | <span data-ttu-id="4b2ab-169">Rotular</span><span class="sxs-lookup"><span data-stu-id="4b2ab-169">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |

<span data-ttu-id="4b2ab-170">Em seguida, é necessário definir a estrutura de dados para a classe de entrada.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-170">Next you must define your data structure for the input class.</span></span>

<span data-ttu-id="4b2ab-171">Adicione uma nova classe ao seu projeto:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-171">Add a new class to your project:</span></span>

1. <span data-ttu-id="4b2ab-172">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e, em seguida, selecione **Adicionar > Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-172">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="4b2ab-173">Na **caixa de diálogo Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *MovieRatingData.cs*.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-173">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *MovieRatingData.cs*.</span></span> <span data-ttu-id="4b2ab-174">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-174">Then, select the **Add** button.</span></span>

<span data-ttu-id="4b2ab-175">O arquivo *MovieRatingData.cs* será aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-175">The *MovieRatingData.cs* file opens in the code editor.</span></span> <span data-ttu-id="4b2ab-176">Adicione a seguinte instrução `using` acima de *MovieRatingData.cs*:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-176">Add the following `using` statement to the top of *MovieRatingData.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="4b2ab-177">Crie uma classe chamada `MovieRating` removendo a definição de classe existente e adicionando o seguinte código a *MovieRatingData.cs*:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-177">Create a class called `MovieRating` by removing the existing class definition and adding the following code in *MovieRatingData.cs*:</span></span>

[!code-csharp[MovieRatingClass](../../../samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#MovieRatingClass "Add the Movie Rating class")]

<span data-ttu-id="4b2ab-178">`MovieRating` especifica uma classe de dados de entrada.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-178">`MovieRating` specifies an input data class.</span></span> <span data-ttu-id="4b2ab-179">O atributo [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) especifica quais colunas (por índice de coluna) no conjunto de dados devem ser carregadas.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-179">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> <span data-ttu-id="4b2ab-180">As colunas `userId` e `movieId` são os `Features` (as entradas que você fornecerá ao modelo para prever o `Label`), e a coluna de classificação é o `Label`, que você preverá (a saída do modelo).</span><span class="sxs-lookup"><span data-stu-id="4b2ab-180">The `userId` and `movieId` columns are your `Features` (the inputs you will give the model to predict the `Label`), and the rating column is the `Label` that you will predict (the output of the model).</span></span>

<span data-ttu-id="4b2ab-181">Crie outra classe, `MovieRatingPrediction`, para representar os resultados previstos adicionando o seguinte código após a classe `MovieRating` em *MovieRatingData.cs*:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-181">Create another class, `MovieRatingPrediction`, to represent predicted results by adding the following code after the `MovieRating` class in *MovieRatingData.cs*:</span></span>

[!code-csharp[PredictionClass](../../../samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#PredictionClass "Add the Movie Prediction Class")]

<span data-ttu-id="4b2ab-182">Em *Program.cs*, substitua o `Console.WriteLine("Hello World!")` pelo seguinte código dentro de `Main()`:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-182">In *Program.cs*, replace the `Console.WriteLine("Hello World!")` with the following code inside `Main()`:</span></span>

[!code-csharp[MLContext](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MLContext "Add MLContext")]

<span data-ttu-id="4b2ab-183">A [classe MLContext](xref:Microsoft.ML.MLContext) é um ponto de partida para todas as operações do ML.NET e a inicialização do `mlContext` cria um ambiente do ML.NET que pode ser compartilhado entre os objetos de fluxo de trabalho da criação de modelo.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-183">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="4b2ab-184">Ele é semelhante, conceitualmente, a `DBContext` no Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-184">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="4b2ab-185">Após `Main()`, crie um método chamado `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-185">After `Main()`, create a method called `LoadData()`:</span></span>
```csharp
public static (IDataView training, IDataView test) LoadData(MLContext mlContext)
{


}
```

> [!NOTE]
> <span data-ttu-id="4b2ab-186">Esse método apresentará um erro até que você adicione uma instrução de retorno nas etapas a seguir.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-186">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="4b2ab-187">Inicialize as variáveis do caminho de dados, carregue os dados nos arquivos \*.csv e retorne os dados `Train` e `Test` como objetos `IDataView` adicionando o seguinte como a próxima linha de código em `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-187">Initialize your data path variables, load the data from the \*.csv files, and return the `Train` and `Test` data as `IDataView` objects by adding the following as the next line of code in `LoadData()`:</span></span>

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadData "Load data from data paths")]

<span data-ttu-id="4b2ab-188">Os dados do ML.NET são representados como uma [classe IDataView](xref:Microsoft.Data.DataView.IDataView).</span><span class="sxs-lookup"><span data-stu-id="4b2ab-188">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.Data.DataView.IDataView).</span></span> <span data-ttu-id="4b2ab-189">`IDataView` é uma maneira flexível e eficiente de descrever dados tabulares (numéricos e texto).</span><span class="sxs-lookup"><span data-stu-id="4b2ab-189">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="4b2ab-190">Os dados podem ser carregados de um arquivo de texto ou em tempo real (por exemplo, banco de dados SQL ou arquivos de log) para um objeto `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-190">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="4b2ab-191">O [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) define o esquema de dados e lê o arquivo.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-191">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="4b2ab-192">Ele usa as variáveis de caminho de dados e retorna uma `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-192">It takes in the data path variables and returns an `IDataView`.</span></span> <span data-ttu-id="4b2ab-193">Nesse caso, você fornece o caminho para os arquivos `Test` e `Train` e indica o cabeçalho do arquivo de texto (para que ele possa usar os nomes de coluna corretamente) e o separador de dados de caractere de vírgula (o separador padrão é uma guia).</span><span class="sxs-lookup"><span data-stu-id="4b2ab-193">In this case, you provide the path for your `Test` and `Train` files and indicate both the text file header (so it can use the column names properly) and the comma character data separator (the default separator is a tab).</span></span>

<span data-ttu-id="4b2ab-194">Adicione o seguinte como as próximas duas linhas de código no método `Main()` para chamar o método `LoadData()` e retornar os dados `Train` e `Test`:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-194">Add the following as the next two lines of code in the `Main()` method to call your `LoadData()` method and return the `Train` and `Test` data:</span></span>

[!code-csharp[LoadDataMain](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadDataMain "Add LoadData method to Main")]


## <a name="build-and-train-your-model"></a><span data-ttu-id="4b2ab-195">Criar e treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="4b2ab-195">Build and train your model</span></span>

<span data-ttu-id="4b2ab-196">Há três conceitos principais no ML.NET: [Dados](../basic-concepts-model-training-in-mldotnet.md#data), [Transformadores](../basic-concepts-model-training-in-mldotnet.md#transformer) e [Avaliadores](../basic-concepts-model-training-in-mldotnet.md#estimator).</span><span class="sxs-lookup"><span data-stu-id="4b2ab-196">There are three major concepts in ML.NET: [Data](../basic-concepts-model-training-in-mldotnet.md#data), [Transformers](../basic-concepts-model-training-in-mldotnet.md#transformer), and [Estimators](../basic-concepts-model-training-in-mldotnet.md#estimator).</span></span>

<span data-ttu-id="4b2ab-197">Os algoritmos de treinamento de aprendizado de máquina exigem que os dados estejam em determinado formato.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-197">Machine learning training algorithms require data in a certain format.</span></span> <span data-ttu-id="4b2ab-198">`Transformers` são usados para transformar dados de tabela em um formato compatível.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-198">`Transformers` are used to transform tabular data to a compatible format.</span></span>

![imagem do transformador](./media/movie-recommendation/transformer.png)

<span data-ttu-id="4b2ab-200">Crie `Transformers` no ML.NET criando `Estimators`.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-200">You create `Transformers` in ML.NET by creating `Estimators`.</span></span> <span data-ttu-id="4b2ab-201">`Estimators` usa dados e retorna `Transformers`.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-201">`Estimators` take in data and return `Transformers`.</span></span>

![imagem do avaliador](./media/movie-recommendation/estimator.png)

<span data-ttu-id="4b2ab-203">O algoritmo de treinamento de recomendação que você usará para treinar seu modelo é um exemplo de `Estimator`.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-203">The recommendation training algorithm you will use for training your model is an example of an `Estimator`.</span></span>

<span data-ttu-id="4b2ab-204">Crie um `Estimator` com as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-204">Build an `Estimator` with the following steps:</span></span>

<span data-ttu-id="4b2ab-205">Crie o método `BuildAndTrainModel()`, logo após o método `LoadData()`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-205">Create the `BuildAndTrainModel()` method, just after the `LoadData()` method, using the following code:</span></span>
```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView trainingDataView)
{


}
```
> [!NOTE]
> <span data-ttu-id="4b2ab-206">Esse método apresentará um erro até que você adicione uma instrução de retorno nas etapas a seguir.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-206">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="4b2ab-207">Defina as transformações de dados adicionando o seguinte código a `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-207">Define the data transformations by adding the following code to `BuildAndTrainModel()`:</span></span>
   
[!code-csharp[DataTransformations](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#DataTransformations "Define data transformations")]

<span data-ttu-id="4b2ab-208">Como `userId` e `movieId` representam usuários e títulos de filmes, não valores reais, use o método [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) para transformar cada `userId` e cada `movieId` em uma coluna `Feature` de tipo de chave numérica (um formato aceito pelos algoritmos de recomendação) e adicioná-los como novas colunas de conjunto de dados:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-208">Since `userId` and `movieId` represent users and movie titles, not real values, you use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform each `userId` and each `movieId` into a numeric key type `Feature` column (a format accepted by recommendation algorithms) and add them as new dataset columns:</span></span>

| <span data-ttu-id="4b2ab-209">userId</span><span class="sxs-lookup"><span data-stu-id="4b2ab-209">userId</span></span> | <span data-ttu-id="4b2ab-210">movieId</span><span class="sxs-lookup"><span data-stu-id="4b2ab-210">movieId</span></span> | <span data-ttu-id="4b2ab-211">Rotular</span><span class="sxs-lookup"><span data-stu-id="4b2ab-211">Label</span></span> | <span data-ttu-id="4b2ab-212">userIdEncoded</span><span class="sxs-lookup"><span data-stu-id="4b2ab-212">userIdEncoded</span></span> | <span data-ttu-id="4b2ab-213">movieIdEncoded</span><span class="sxs-lookup"><span data-stu-id="4b2ab-213">movieIdEncoded</span></span> |
| ------------- |:-------------:| -----:|-----:|-----:|
| <span data-ttu-id="4b2ab-214">1</span><span class="sxs-lookup"><span data-stu-id="4b2ab-214">1</span></span> | <span data-ttu-id="4b2ab-215">1</span><span class="sxs-lookup"><span data-stu-id="4b2ab-215">1</span></span> | <span data-ttu-id="4b2ab-216">4</span><span class="sxs-lookup"><span data-stu-id="4b2ab-216">4</span></span> | <span data-ttu-id="4b2ab-217">userKey1</span><span class="sxs-lookup"><span data-stu-id="4b2ab-217">userKey1</span></span> | <span data-ttu-id="4b2ab-218">movieKey1</span><span class="sxs-lookup"><span data-stu-id="4b2ab-218">movieKey1</span></span> |
| <span data-ttu-id="4b2ab-219">1</span><span class="sxs-lookup"><span data-stu-id="4b2ab-219">1</span></span> | <span data-ttu-id="4b2ab-220">3</span><span class="sxs-lookup"><span data-stu-id="4b2ab-220">3</span></span> | <span data-ttu-id="4b2ab-221">4</span><span class="sxs-lookup"><span data-stu-id="4b2ab-221">4</span></span> | <span data-ttu-id="4b2ab-222">userKey1</span><span class="sxs-lookup"><span data-stu-id="4b2ab-222">userKey1</span></span> | <span data-ttu-id="4b2ab-223">movieKey2</span><span class="sxs-lookup"><span data-stu-id="4b2ab-223">movieKey2</span></span> |
| <span data-ttu-id="4b2ab-224">1</span><span class="sxs-lookup"><span data-stu-id="4b2ab-224">1</span></span> | <span data-ttu-id="4b2ab-225">6</span><span class="sxs-lookup"><span data-stu-id="4b2ab-225">6</span></span> | <span data-ttu-id="4b2ab-226">4</span><span class="sxs-lookup"><span data-stu-id="4b2ab-226">4</span></span> | <span data-ttu-id="4b2ab-227">userKey1</span><span class="sxs-lookup"><span data-stu-id="4b2ab-227">userKey1</span></span> | <span data-ttu-id="4b2ab-228">movieKey3</span><span class="sxs-lookup"><span data-stu-id="4b2ab-228">movieKey3</span></span> |


<span data-ttu-id="4b2ab-229">Escolha o algoritmo de aprendizado de máquina e acrescente-o às definições de transformação de dados adicionando o seguinte como a próxima linha de código em `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-229">Choose the machine learning algorithm and append it to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddAlgorithm](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#AddAlgorithm "Add the training algorithm with options")]

<span data-ttu-id="4b2ab-230">O [MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) é o algoritmo de treinamento de recomendação.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-230">The [MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) is your recommendation training algorithm.</span></span>  <span data-ttu-id="4b2ab-231">A [Fatoração de Matriz](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) é uma abordagem comum de recomendação quando você tem dados sobre como os usuários classificaram produtos no passado, que é o caso para os conjuntos de dados deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-231">[Matrix Factorization](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) is a common approach to recommendation when you have data on how users have rated products in the past, which is the case for the datasets in this tutorial.</span></span> <span data-ttu-id="4b2ab-232">Há outros algoritmos de recomendação para quando você tem diferentes dados disponíveis (confira a seção [Outros algoritmos de recomendação](#other-recommendation-algorithms) abaixo para saber mais).</span><span class="sxs-lookup"><span data-stu-id="4b2ab-232">There are other recommendation algorithms for when you have different data available (see the [Other recommendation algorithms](#other-recommendation-algorithms) section below to learn more).</span></span> 

<span data-ttu-id="4b2ab-233">Nesse caso, o algoritmo `Matrix Factorization` usa um método chamado "filtragem colaborativa", que supõe que, se o Usuário 1 tem a mesma opinião do Usuário 2 sobre determinada questão, é mais provável que o Usuário 1 sinta-se da mesma forma que o Usuário 2 sobre outra questão.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-233">In this case, the `Matrix Factorization` algorithm uses a method called "collaborative filtering", which assumes that if User 1 has the same opinion as User 2 on a certain issue, then User 1 is more likely to feel the same way as User 2 about a different issue.</span></span>

<span data-ttu-id="4b2ab-234">Por exemplo, se o Usuário 1 e o Usuário 2 classificam filmes de forma semelhante, é mais provável que o Usuário 2 goste de um filme que o Usuário 1 assistiu e forneceu uma classificação alta:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-234">For instance, if User 1 and User 2 rate movies similarly, then User 2 is more likely to enjoy a movie that User 1 has watched and rated highly:</span></span>

| | `Incredibles 2 (2018)` | `The Avengers (2012)` | `Guardians of the Galaxy (2014)` |
| -------------:|-------------:| -----:|-----:|
| <span data-ttu-id="4b2ab-235">Usuário 1</span><span class="sxs-lookup"><span data-stu-id="4b2ab-235">User 1</span></span> | <span data-ttu-id="4b2ab-236">Assistiu e gostou do filme</span><span class="sxs-lookup"><span data-stu-id="4b2ab-236">Watched and liked movie</span></span> | <span data-ttu-id="4b2ab-237">Assistiu e gostou do filme</span><span class="sxs-lookup"><span data-stu-id="4b2ab-237">Watched and liked movie</span></span> | <span data-ttu-id="4b2ab-238">Assistiu e gostou do filme</span><span class="sxs-lookup"><span data-stu-id="4b2ab-238">Watched and liked movie</span></span> |
| <span data-ttu-id="4b2ab-239">Usuário 2</span><span class="sxs-lookup"><span data-stu-id="4b2ab-239">User 2</span></span> | <span data-ttu-id="4b2ab-240">Assistiu e gostou do filme</span><span class="sxs-lookup"><span data-stu-id="4b2ab-240">Watched and liked movie</span></span> | <span data-ttu-id="4b2ab-241">Assistiu e gostou do filme</span><span class="sxs-lookup"><span data-stu-id="4b2ab-241">Watched and liked movie</span></span> | <span data-ttu-id="4b2ab-242">Não assistiu – RECOMENDAR o filme</span><span class="sxs-lookup"><span data-stu-id="4b2ab-242">Has not watched -- RECOMMEND movie</span></span> |

<span data-ttu-id="4b2ab-243">O treinador `Matrix Factorization` tem várias [Opções](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), sobre as quais você pode ler mais na seção [Hiperparâmetros de algoritmo](#algorithm-hyperparameters) abaixo.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-243">The `Matrix Factorization` trainer has several [Options](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), which you can read more about in the [Algorithm hyperparameters](#algorithm-hyperparameters) section below.</span></span>

<span data-ttu-id="4b2ab-244">Ajuste o modelo aos dados `Train` e retorne o modelo treinado adicionando o seguinte como a próxima linha de código no método `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-244">Fit the model to the `Train` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[FitModel](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#FitModel "Call the Fit method and return back the trained model")]

<span data-ttu-id="4b2ab-245">O método [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.Data.DataView.IDataView,Microsoft.Data.DataView.IDataView%29) treina o modelo com o conjunto de dados de treinamento fornecido.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-245">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.Data.DataView.IDataView,Microsoft.Data.DataView.IDataView%29) method trains your model with the provided training dataset.</span></span> <span data-ttu-id="4b2ab-246">Tecnicamente, ele executa as definições `Estimator` transformando os dados e aplicando o treinamento e retorna o modelo treinado, que é um `Transformer`.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-246">Technically, it executes the `Estimator` definitions by transforming the data and applying the training, and it returns back the trained model, which is a `Transformer`.</span></span>

<span data-ttu-id="4b2ab-247">Adicione o seguinte como a próxima linha de código no método `Main()` para chamar o método `BuildAndTrainModel()` e retornar o modelo treinado:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-247">Add the following as the next line of code in the `Main()` method to call your `BuildAndTrainModel()` method and return the trained model:</span></span>

[!code-csharp[BuildTrainModelMain](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#BuildTrainModelMain "Add BuildAndTrainModel method in Main")]

## <a name="evaluate-your-model"></a><span data-ttu-id="4b2ab-248">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="4b2ab-248">Evaluate your model</span></span>

<span data-ttu-id="4b2ab-249">Depois de treinar o modelo, use os dados de teste para avaliar o desempenho do modelo.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-249">Once you have trained your model, use your test data to evaluate how your model is performing.</span></span> 

<span data-ttu-id="4b2ab-250">Crie o método `EvaluateModel()`, logo após o método `BuildAndTrainModel()`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-250">Create the `EvaluateModel()` method, just after the `BuildAndTrainModel()` method, using the following code:</span></span>
```csharp
public static void EvaluateModel(MLContext mlContext, IDataView testDataView, ITransformer model)
{


}
```

<span data-ttu-id="4b2ab-251">Transforme os dados `Test` adicionando o seguinte código a `EvaluateModel()`: [!code-csharp[Transform](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Transform "Transform the test data")]</span><span class="sxs-lookup"><span data-stu-id="4b2ab-251">Transform the `Test` data by adding the following code to `EvaluateModel()`: [!code-csharp[Transform](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Transform "Transform the test data")]</span></span>

<span data-ttu-id="4b2ab-252">O método [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) faz previsões para várias linhas de entrada fornecidas de um conjunto de dados de teste.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-252">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for multiple provided input rows of a test dataset.</span></span>

<span data-ttu-id="4b2ab-253">Avalie o modelo adicionando o seguinte como a próxima linha de código no método `EvaluateModel()`:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-253">Evaluate the model by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Evaluate "Evaluate the model using predictions from the test data")]

<span data-ttu-id="4b2ab-254">Depois que você define a previsão, o método [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) avalia o modelo, que compara os valores previstos com os `Labels` reais no conjunto de dados de teste e retorna métricas sobre o desempenho do modelo.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-254">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="4b2ab-255">Imprima as métricas de avaliação no console adicionando o seguinte como a próxima linha de código no método `EvaluateModel()`:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-255">Print your evaluation metrics to the console by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[PrintMetrics](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintMetrics "Print the evaluation metrics")]

<span data-ttu-id="4b2ab-256">Adicione o seguinte como a próxima linha de código no método `Main()` para chamar o método `EvaluateModel()`:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-256">Add the following as the next line of code in the `Main()` method to call your `EvaluateModel()` method:</span></span>

[!code-csharp[EvaluateModelMain](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#EvaluateModelMain "Add EvaluateModel method in Main")]

<span data-ttu-id="4b2ab-257">Até agora, a saída deve ser semelhante ao seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-257">The output so far should look similar to the following text:</span></span>

```console
=============== Training the model ===============
iter      tr_rmse          obj
   0       1.5403   3.1262e+05
   1       0.9221   1.6030e+05
   2       0.8687   1.5046e+05
   3       0.8416   1.4584e+05
   4       0.8142   1.4209e+05
   5       0.7849   1.3907e+05
   6       0.7544   1.3594e+05
   7       0.7266   1.3361e+05
   8       0.6987   1.3110e+05
   9       0.6751   1.2948e+05
  10       0.6530   1.2766e+05
  11       0.6350   1.2644e+05
  12       0.6197   1.2541e+05
  13       0.6067   1.2470e+05
  14       0.5953   1.2382e+05
  15       0.5871   1.2342e+05
  16       0.5781   1.2279e+05
  17       0.5713   1.2240e+05
  18       0.5660   1.2230e+05
  19       0.5592   1.2179e+05
=============== Evaluating the model ===============
Rms: 0.994051469730769
RSquared: 0.412556298844873
```

<span data-ttu-id="4b2ab-258">Nessa saída, há 20 iterações.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-258">In this output, there are 20 iterations.</span></span> <span data-ttu-id="4b2ab-259">Em cada iteração, a medida de erro diminui e é convergida para mais próximo de 0.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-259">In each iteration, the measure of error decreases and converges closer and closer to 0.</span></span>

<span data-ttu-id="4b2ab-260">A `root of mean squared error` (RMS ou RMSE) é frequentemente usada para medir as diferenças entre os valores previstos por um modelo e os valores observados em um conjunto de dados de teste.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-260">The `root of mean squared error` (RMS or RMSE) is frequently used to measure the differences between values predicted by a model and the values observed in a test dataset.</span></span> <span data-ttu-id="4b2ab-261">Tecnicamente, ela é a raiz quadrada da média dos quadrados dos erros.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-261">Technically it's the square root of the average of the squares of the errors.</span></span> <span data-ttu-id="4b2ab-262">Você deseja que a pontuação RMSE esteja o mais próximo possível de 1.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-262">You want your RMSE score to be as close to 1 as possible.</span></span>

<span data-ttu-id="4b2ab-263">`R Squared` é o percentual de variação nos valores previstos explicados pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-263">`R Squared` is the variation percentage in the predicted values explained by your model.</span></span> <span data-ttu-id="4b2ab-264">É um valor entre 0 e 1 e, quanto mais próximo o valor estiver de 0, melhor será o modelo.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-264">It's a value between 0 and 1, and the closer the value is to 0, the better the model is.</span></span>

## <a name="use-your-model"></a><span data-ttu-id="4b2ab-265">Usar o modelo</span><span class="sxs-lookup"><span data-stu-id="4b2ab-265">Use your model</span></span>

<span data-ttu-id="4b2ab-266">Agora você pode usar o modelo treinado para fazer previsões sobre novos dados.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-266">Now you can use your trained model to make predictions on new data.</span></span>

<span data-ttu-id="4b2ab-267">Crie o método `UseModelForSinglePrediction()`, logo após o método `EvaluateModel()`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-267">Create the `UseModelForSinglePrediction()` method, just after the `EvaluateModel()` method, using the following code:</span></span>
```csharp
public static void UseModelForSinglePrediction(MLContext mlContext, ITransformer model)
{


}
```

<span data-ttu-id="4b2ab-268">Use o `PredictionEngine` para prever a classificação adicionando o seguinte código à `UseModelForSinglePrediction()`:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-268">Use the `PredictionEngine` to predict the rating by adding the following code to `UseModelForSinglePrediction()`:</span></span>

[!code-csharp[PredictionEngine](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PredictionEngine "Create Prediction Engine")]

<span data-ttu-id="4b2ab-269">A [classe PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) é uma API de conveniência, que permite passar uma única instância de dados e, em seguida, executar uma previsão nessa única instância de dados.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-269">The [PredictionEngine class](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass a single instance of data and then perform a prediction on this single instance of data.</span></span>

<span data-ttu-id="4b2ab-270">Crie uma instância de `MovieRating` chamada `testInput` e passe-a para o Mecanismo de Previsão adicionando o seguinte como as próximas linhas do código no método `UseModelForSinglePrediction()`:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-270">Create an instance of `MovieRating` called `testInput` and pass it to the Prediction Engine by adding the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[MakeSinglePrediction](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MakeSinglePrediction "Make a single prediction with the Prediction Engine")]

<span data-ttu-id="4b2ab-271">A função [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) faz uma previsão sobre uma única coluna de dados.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-271">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single column of data.</span></span>

<span data-ttu-id="4b2ab-272">Em seguida, use a `Score`, ou a classificação prevista, para determinar se deseja recomendar o filme com a movieId 10 para o usuário 6.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-272">You can then use the `Score`, or the predicted rating, to determine whether you want to recommend the movie with movieId 10 to user 6.</span></span> <span data-ttu-id="4b2ab-273">Quanto mais alta a `Score`, maior a probabilidade de um usuário gostar de um filme específico.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-273">The higher the `Score`, the higher the likelihood of a user liking a particular movie.</span></span> <span data-ttu-id="4b2ab-274">Nesse caso, digamos que você recomende filmes com uma classificação prevista de > 3,5.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-274">In this case, let’s say that you recommend movies with a predicted rating of > 3.5.</span></span>

<span data-ttu-id="4b2ab-275">Para imprimir os resultados, adicione o seguinte como as próximas linhas de código no método `UseModelForSinglePrediction()`:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-275">To print the results, add the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[PrintResults](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintResults "Print the recommendation prediction results")]

<span data-ttu-id="4b2ab-276">Adicione o seguinte como a próxima linha de código no método `Main()` para chamar o método `UseModelForSinglePrediction()`:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-276">Add the following as the next line of code in the `Main()` method to call your `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[UseModelMain](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UseModelMain "Add UseModelForSinglePrediction method in Main")]

<span data-ttu-id="4b2ab-277">A saída desse método deve ser semelhante ao seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-277">The output of this method should look similar to the following text:</span></span>

```console
=============== Making a prediction ===============
Movie 10 is recommended for user 6
```

### <a name="save-your-model"></a><span data-ttu-id="4b2ab-278">Salvar o modelo</span><span class="sxs-lookup"><span data-stu-id="4b2ab-278">Save your model</span></span>
<span data-ttu-id="4b2ab-279">Para usar o modelo para fazer previsões em aplicativos de usuário final, primeiro é necessário salvar o modelo.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-279">To use your model to make predictions in end-user applications, you must first save the model.</span></span>

<span data-ttu-id="4b2ab-280">Crie o método `SaveModel()`, logo após o método `UseModelForSinglePrediction()`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-280">Create the `SaveModel()` method, just after the `UseModelForSinglePrediction()` method, using the following code:</span></span>
```csharp
public static void SaveModel(MLContext mlContext, ITransformer model)
{


}
```

<span data-ttu-id="4b2ab-281">Salve o modelo treinado adicionando o seguinte código ao método `SaveModel()`:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-281">Save your trained model by adding the following code in the `SaveModel()` method:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModel "Save the model to a zip file")]

<span data-ttu-id="4b2ab-282">Esse método salva o modelo treinado em um arquivo .zip (na pasta "Data"), que pode ser usado em outros aplicativos .NET para fazer previsões.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-282">This method saves your trained model to a .zip file (in the "Data" folder), which can then be used in other .NET applications to make predictions.</span></span>

<span data-ttu-id="4b2ab-283">Adicione o seguinte como a próxima linha de código no método `Main()` para chamar o método `SaveModel()`:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-283">Add the following as the next line of code in the `Main()` method to call your `SaveModel()` method:</span></span>

[!code-csharp[SaveModelMain](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModelMain "Create SaveModel method in Main")]

### <a name="use-your-saved-model"></a><span data-ttu-id="4b2ab-284">Usar o modelo salvo</span><span class="sxs-lookup"><span data-stu-id="4b2ab-284">Use your saved model</span></span>
<span data-ttu-id="4b2ab-285">Depois de salvar o modelo treinado, você poderá consumir o modelo em ambientes diferentes (confira o ["Guia de instruções"](../how-to-guides/consuming-model-ml-net.md) para saber como operacionalizar um modelo de machine learning treinado em aplicativos).</span><span class="sxs-lookup"><span data-stu-id="4b2ab-285">Once you have saved your trained model, you can consume the model in different environments (see the ["How-to guide"](../how-to-guides/consuming-model-ml-net.md) to learn how to operationalize a trained machine learning model in apps).</span></span>

## <a name="results"></a><span data-ttu-id="4b2ab-286">Resultados</span><span class="sxs-lookup"><span data-stu-id="4b2ab-286">Results</span></span>

<span data-ttu-id="4b2ab-287">Depois de seguir as etapas acima, execute o aplicativo de console (Ctrl + F5).</span><span class="sxs-lookup"><span data-stu-id="4b2ab-287">After following the steps above, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="4b2ab-288">Os resultados da previsão individual acima deverão ser semelhantes ao mostrado a seguir.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-288">Your results from the single prediction above should be similar to the following.</span></span> <span data-ttu-id="4b2ab-289">Você poderá ver avisos ou mensagens de processamento, mas essas mensagens foram removidas dos resultados a seguir para maior clareza.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-289">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

```console
=============== Training the model ===============
iter      tr_rmse          obj
   0       1.5382   3.1213e+05
   1       0.9223   1.6051e+05
   2       0.8691   1.5050e+05
   3       0.8413   1.4576e+05
   4       0.8145   1.4208e+05
   5       0.7848   1.3895e+05
   6       0.7552   1.3613e+05
   7       0.7259   1.3357e+05
   8       0.6987   1.3121e+05
   9       0.6747   1.2949e+05
  10       0.6533   1.2766e+05
  11       0.6353   1.2636e+05
  12       0.6209   1.2561e+05
  13       0.6072   1.2462e+05
  14       0.5965   1.2394e+05
  15       0.5868   1.2352e+05
  16       0.5782   1.2279e+05
  17       0.5713   1.2227e+05
  18       0.5637   1.2190e+05
  19       0.5604   1.2178e+05
=============== Evaluating the model ===============
Rms: 0.977175077487166
RSquared: 0.43233349213192
=============== Making a prediction ===============
Movie 10 is recommended for user 6
=============== Saving the model to a file ===============
```

<span data-ttu-id="4b2ab-290">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="4b2ab-290">Congratulations!</span></span> <span data-ttu-id="4b2ab-291">Você agora criou um modelo de machine learning para recomendação de filmes.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-291">You've now successfully built a machine learning model for recommending movies.</span></span> <span data-ttu-id="4b2ab-292">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation).</span><span class="sxs-lookup"><span data-stu-id="4b2ab-292">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="improve-your-model"></a><span data-ttu-id="4b2ab-293">Melhorar o modelo</span><span class="sxs-lookup"><span data-stu-id="4b2ab-293">Improve your model</span></span>

<span data-ttu-id="4b2ab-294">Há várias maneiras de melhorar o desempenho do modelo para obter previsões mais precisas.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-294">There are several ways that you can improve the performance of your model so that you can get more accurate predictions.</span></span>

### <a name="data"></a><span data-ttu-id="4b2ab-295">Dados</span><span class="sxs-lookup"><span data-stu-id="4b2ab-295">Data</span></span> 

<span data-ttu-id="4b2ab-296">A adição de mais dados de treinamento que tenham amostras suficientes para cada usuário e a ID de filme pode ajudar a melhorar a qualidade do modelo de recomendação.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-296">Adding more training data that has enough samples for each user and movie id can help improve the quality of the recommendation model.</span></span>

<span data-ttu-id="4b2ab-297">A [validação cruzada](../how-to-guides/train-cross-validation-ml-net.md) é uma técnica para avaliação de modelos que divide dados aleatoriamente em subconjuntos (em vez de extrair os dados de teste do conjunto de dados como você fez neste tutorial) e usa alguns dos grupos como dados de treinamento e alguns dos grupos como dados de teste.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-297">[Cross validation](../how-to-guides/train-cross-validation-ml-net.md) is a technique for evaluating models that randomly splits up data into subsets (instead of extracting out test data from the dataset like you did in this tutorial) and takes some of the groups as train data and some of the groups as test data.</span></span> <span data-ttu-id="4b2ab-298">Esse método tem um melhor desempenho do que a divisão treinamento/teste em termos de qualidade do modelo.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-298">This method outperforms making a train-test split in terms of model quality.</span></span>

### <a name="features"></a><span data-ttu-id="4b2ab-299">Recursos</span><span class="sxs-lookup"><span data-stu-id="4b2ab-299">Features</span></span>

<span data-ttu-id="4b2ab-300">Neste tutorial, você só usará os três `Features` (`user id`, `movie id` e `rating`) fornecidos pelo conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-300">In this tutorial, you only use the three `Features` (`user id`, `movie id`, and `rating`) that are provided by the dataset.</span></span> 

<span data-ttu-id="4b2ab-301">Embora esse seja um bom começo, na verdade, o ideal será adicionar outros atributos ou `Features` (por exemplo, idade, sexo, localização geográfica etc.) se eles forem incluídos no conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-301">While this is a good start, in reality you might want to add other attributes or `Features` (for example, age, gender, geo-location, etc.) if they are included in the dataset.</span></span> <span data-ttu-id="4b2ab-302">A adição de `Features` mais relevantes pode ajudar a melhorar o desempenho do modelo de recomendação.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-302">Adding more relevant `Features` can help improve the performance of your recommendation model.</span></span> 

<span data-ttu-id="4b2ab-303">Caso não tenha certeza sobre quais `Features` podem ser mais relevantes para sua tarefa de aprendizado de máquina, use também o FCC (Cálculo de Contribuição do Recurso) e a [Importância de Permuta do Recurso](../how-to-guides/determine-global-feature-importance-in-model.md), fornecidos pelo ML.NET para descobrir `Features` mais influentes.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-303">If you are unsure about which `Features` might be the most relevant for your machine learning task, you can also make use of Feature Contribution Calculation (FCC) and [Feature Permutation Importance](../how-to-guides/determine-global-feature-importance-in-model.md), which ML.NET provides to discover the most influential `Features`.</span></span>

### <a name="algorithm-hyperparameters"></a><span data-ttu-id="4b2ab-304">Hiperparâmetros de algoritmo</span><span class="sxs-lookup"><span data-stu-id="4b2ab-304">Algorithm hyperparameters</span></span>

<span data-ttu-id="4b2ab-305">Embora o ML.NET forneça bons algoritmos de treinamento padrão, você pode ajustar ainda mais o desempenho alterando os [hiperparâmetros](../resources/glossary.md#hyperparameter) do algoritmo.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-305">While ML.NET provides good default training algorithms, you can further fine-tune performance by changing the algorithm's [hyperparameters](../resources/glossary.md#hyperparameter).</span></span>

<span data-ttu-id="4b2ab-306">Para a `Matrix Factorization`, você pode experimentar com hiperparâmetros, como [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) e [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) para ver se ele oferece melhores resultados.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-306">For `Matrix Factorization`, you can experiment with hyperparameters such as [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) and [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) to see if that gives you better results.</span></span>

<span data-ttu-id="4b2ab-307">Por exemplo, neste tutorial, as opções de algoritmo são:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-307">For instance, in this tutorial the algorithm options are:</span></span>

```csharp
var options = new MatrixFactorizationTrainer.Options
{
    MatrixColumnIndexColumnName = "userIdEncoded",
    MatrixRowIndexColumnName = "movieIdEncoded", 
    LabelColumnName = "Label",
    NumberOfIterations = 20,
    ApproximationRank = 100
};
```

### <a name="other-recommendation-algorithms"></a><span data-ttu-id="4b2ab-308">Outros algoritmos de recomendação</span><span class="sxs-lookup"><span data-stu-id="4b2ab-308">Other Recommendation Algorithms</span></span>
<span data-ttu-id="4b2ab-309">O algoritmo de fatoração de matriz com a filtragem colaborativa é apenas uma abordagem para fazer recomendações de filmes.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-309">The matrix factorization algorithm with collaborative filtering is only one approach for performing movie recommendations.</span></span> <span data-ttu-id="4b2ab-310">Em muitos casos, talvez você não tenha os dados de classificações disponíveis e tenha apenas o histórico de filmes disponível dos usuários.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-310">In many cases, you may not have the ratings data available and only have movie history available from users.</span></span> <span data-ttu-id="4b2ab-311">Em outros casos, você pode ter mais do que apenas os dados de classificação do usuário.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-311">In other cases, you may have more than just the user’s rating data.</span></span>

| <span data-ttu-id="4b2ab-312">Algoritmo</span><span class="sxs-lookup"><span data-stu-id="4b2ab-312">Algorithm</span></span>       | <span data-ttu-id="4b2ab-313">Cenário</span><span class="sxs-lookup"><span data-stu-id="4b2ab-313">Scenario</span></span>           | <span data-ttu-id="4b2ab-314">Amostra</span><span class="sxs-lookup"><span data-stu-id="4b2ab-314">Sample</span></span>  |
| ------------- |:-------------:| -----:|
| <span data-ttu-id="4b2ab-315">Fatoração de Matriz de uma Classe</span><span class="sxs-lookup"><span data-stu-id="4b2ab-315">One Class Matrix Factorization</span></span> | <span data-ttu-id="4b2ab-316">Use isso quando você tiver apenas userId e movieId.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-316">Use this when you only have userId and movieId.</span></span> <span data-ttu-id="4b2ab-317">Esse estilo de recomendação é baseado no cenário de cocompra, ou produtos frequentemente comprados juntos, o que significa que ele recomendará aos clientes um conjunto de produtos de acordo com seu próprio histórico de ordens de compra.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-317">This style of recommendation is based upon the co-purchase scenario, or products frequently bought together, which means it will recommend to customers a set of products based upon their own purchase order history.</span></span> | [<span data-ttu-id="4b2ab-318">>Experimentar</span><span class="sxs-lookup"><span data-stu-id="4b2ab-318">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/MatrixFactorization_ProductRecommendation) |
| <span data-ttu-id="4b2ab-319">Computadores de Fatoração com Reconhecimento de Campo</span><span class="sxs-lookup"><span data-stu-id="4b2ab-319">Field Aware Factorization Machines</span></span> | <span data-ttu-id="4b2ab-320">Use isso para fazer recomendações quando você tiver mais Recursos do que userId, productId e a classificação (como descrição ou preço do produto).</span><span class="sxs-lookup"><span data-stu-id="4b2ab-320">Use this to make recommendations when you have more Features beyond userId, productId, and rating (such as product description or product price).</span></span> <span data-ttu-id="4b2ab-321">Esse método também usa uma abordagem de filtragem colaborativa.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-321">This method also uses a collaborative filtering approach.</span></span> | [<span data-ttu-id="4b2ab-322">>Experimentar</span><span class="sxs-lookup"><span data-stu-id="4b2ab-322">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/Recommendation-MovieRecommender) |

### <a name="new-user-scenario"></a><span data-ttu-id="4b2ab-323">Novo cenário de usuário</span><span class="sxs-lookup"><span data-stu-id="4b2ab-323">New user scenario</span></span>
<span data-ttu-id="4b2ab-324">Um problema comum na filtragem colaborativa é o problema de inicialização a frio, que é quando você tem um novo usuário sem nenhum dado anterior do qual fazer inferências.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-324">One common problem in collaborative filtering is the cold start problem, which is when you have a new user with no previous data to draw inferences from.</span></span> <span data-ttu-id="4b2ab-325">Esse problema costuma ser resolvido com a solicitação da criação de um perfil aos novos usuários e, por exemplo, da classificação de filmes que assistiram no passado.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-325">This problem is often solved by asking new users to create a profile and, for instance, rate movies they have seen in the past.</span></span> <span data-ttu-id="4b2ab-326">Embora esse método seja um fardo para o usuário, ele fornece alguns dados iniciais para novos usuários sem nenhum histórico de classificação.</span><span class="sxs-lookup"><span data-stu-id="4b2ab-326">While this method puts some burden on the user, it provides some starting data for new users with no rating history.</span></span>

## <a name="resources"></a><span data-ttu-id="4b2ab-327">Recursos</span><span class="sxs-lookup"><span data-stu-id="4b2ab-327">Resources</span></span>
<span data-ttu-id="4b2ab-328">Os dados usados neste tutorial foram obtidos do [Conjunto de dados MovieLens](http://files.grouplens.org/datasets/movielens/).</span><span class="sxs-lookup"><span data-stu-id="4b2ab-328">The data used in this tutorial is derived from [MovieLens Dataset](http://files.grouplens.org/datasets/movielens/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="4b2ab-329">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="4b2ab-329">Next steps</span></span>
<span data-ttu-id="4b2ab-330">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="4b2ab-330">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="4b2ab-331">Selecionar um algoritmo de aprendizado de máquina</span><span class="sxs-lookup"><span data-stu-id="4b2ab-331">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="4b2ab-332">Preparar e carregar os dados</span><span class="sxs-lookup"><span data-stu-id="4b2ab-332">Prepare and load your data</span></span>
> * <span data-ttu-id="4b2ab-333">Criar e treinar um modelo</span><span class="sxs-lookup"><span data-stu-id="4b2ab-333">Build and train a model</span></span>
> * <span data-ttu-id="4b2ab-334">Avaliar um modelo</span><span class="sxs-lookup"><span data-stu-id="4b2ab-334">Evaluate a model</span></span>
> * <span data-ttu-id="4b2ab-335">Implantar e consumir um modelo</span><span class="sxs-lookup"><span data-stu-id="4b2ab-335">Deploy and consume a model</span></span>

<span data-ttu-id="4b2ab-336">Avançar para o próximo tutorial para saber mais</span><span class="sxs-lookup"><span data-stu-id="4b2ab-336">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="4b2ab-337">Análise de Sentimento</span><span class="sxs-lookup"><span data-stu-id="4b2ab-337">Sentiment Analysis</span></span>](sentiment-analysis.md)
