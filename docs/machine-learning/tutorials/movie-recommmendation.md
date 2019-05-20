---
title: 'Tutorial: Criar uma recomendação de filme'
description: Este tutorial mostra como criar uma recomendação de filme do ML.NET em um aplicativo de console do .NET Core. AS etapas usam C# e o Visual Studio 2019.
author: briacht
ms.author: johalex
ms.date: 05/06/2019
ms.custom: mvc
ms.topic: tutorial
ms.openlocfilehash: 5d459d8b28298250f3b815e33ff4d85ac54f79c2
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063373"
---
# <a name="tutorial-create-a-movie-recommender-with-mlnet"></a><span data-ttu-id="40936-104">Tutorial: Criar um sistema de recomendação de filmes com o ML.NET</span><span class="sxs-lookup"><span data-stu-id="40936-104">Tutorial: Create a Movie Recommender with ML.NET</span></span>

<span data-ttu-id="40936-105">Este tutorial mostra como criar uma recomendação de filme do ML.NET em um aplicativo de console do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="40936-105">This tutorial shows you how to build a movie recommender with ML.NET in a .NET Core console application.</span></span> <span data-ttu-id="40936-106">AS etapas usam C# e o Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="40936-106">The steps use C# and Visual Studio 2019.</span></span>

<span data-ttu-id="40936-107">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="40936-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="40936-108">Selecionar um algoritmo de aprendizado de máquina</span><span class="sxs-lookup"><span data-stu-id="40936-108">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="40936-109">Preparar e carregar os dados</span><span class="sxs-lookup"><span data-stu-id="40936-109">Prepare and load your data</span></span>
> * <span data-ttu-id="40936-110">Criar e treinar um modelo</span><span class="sxs-lookup"><span data-stu-id="40936-110">Build and train a model</span></span>
> * <span data-ttu-id="40936-111">Avaliar um modelo</span><span class="sxs-lookup"><span data-stu-id="40936-111">Evaluate a model</span></span>
> * <span data-ttu-id="40936-112">Implantar e consumir um modelo</span><span class="sxs-lookup"><span data-stu-id="40936-112">Deploy and consume a model</span></span>

<span data-ttu-id="40936-113">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation).</span><span class="sxs-lookup"><span data-stu-id="40936-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="40936-114">Fluxo de trabalho de aprendizado de máquina</span><span class="sxs-lookup"><span data-stu-id="40936-114">Machine learning workflow</span></span>

<span data-ttu-id="40936-115">Você usará as seguintes etapas para realizar sua tarefa, bem como qualquer outra tarefa do ML.NET:</span><span class="sxs-lookup"><span data-stu-id="40936-115">You will use the following steps to accomplish your task, as well as any other ML.NET task:</span></span>

1. [<span data-ttu-id="40936-116">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="40936-116">Load your data</span></span>](#load-your-data)
2. [<span data-ttu-id="40936-117">Criar e treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="40936-117">Build and train your model</span></span>](#build-and-train-your-model)
3. [<span data-ttu-id="40936-118">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="40936-118">Evaluate your model</span></span>](#evaluate-your-model)
4. [<span data-ttu-id="40936-119">Usar o modelo</span><span class="sxs-lookup"><span data-stu-id="40936-119">Use your model</span></span>](#use-your-model)

## <a name="prerequisites"></a><span data-ttu-id="40936-120">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="40936-120">Prerequisites</span></span>

* <span data-ttu-id="40936-121">[Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="40936-121">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="40936-122">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="40936-122">Select the appropriate machine learning task</span></span>

<span data-ttu-id="40936-123">Há várias maneiras de abordar problemas de recomendação, como recomendar uma lista de filmes ou uma lista de produtos relacionados, mas, nesse caso, você preverá qual classificação (1 a 5) um usuário dará a um filme específico e recomendará esse filme se ele for superior a um limite definido (quanto maior a classificação, maior a probabilidade de um usuário gostar de um filme específico).</span><span class="sxs-lookup"><span data-stu-id="40936-123">There are several ways to approach recommendation problems, such as recommending a list of movies or recommending a list of related products, but in this case you will predict what rating (1-5) a user will give to a particular movie and recommend that movie if it's higher than a defined threshold (the higher the rating, the higher the likelihood of a user liking a particular movie).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="40936-124">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="40936-124">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="40936-125">Criar um projeto</span><span class="sxs-lookup"><span data-stu-id="40936-125">Create a project</span></span>

1. <span data-ttu-id="40936-126">Abra o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="40936-126">Open Visual Studio 2017.</span></span> <span data-ttu-id="40936-127">Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="40936-127">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="40936-128">Na caixa de diálogo **Novo Projeto**, selecione o nó **Visual C#** seguido pelo nó **.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="40936-128">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="40936-129">Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="40936-129">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="40936-130">Na caixa de texto **Nome**, digite "MovieRecommender" e, em seguida, selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="40936-130">In the **Name** text box, type "MovieRecommender" and then select the **OK** button.</span></span>

2. <span data-ttu-id="40936-131">Crie um diretório chamado *Data* no projeto para armazenar o conjunto de dados:</span><span class="sxs-lookup"><span data-stu-id="40936-131">Create a directory named *Data* in your project to store the data set:</span></span>

    <span data-ttu-id="40936-132">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Nova Pasta**.</span><span class="sxs-lookup"><span data-stu-id="40936-132">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="40936-133">Digite "Data" e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="40936-133">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="40936-134">Instale os pacotes NuGet **Microsoft.ML** e **Microsoft.ML.Recommender**:</span><span class="sxs-lookup"><span data-stu-id="40936-134">Install the **Microsoft.ML** and **Microsoft.ML.Recommender** NuGet Packages:</span></span>

    <span data-ttu-id="40936-135">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="40936-135">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="40936-136">Escolha "nuget.org" como a origem do pacote, selecione a guia **Procurar**, pesquise **Microsoft.ML**, selecione o pacote **1.0.0** na lista e selecione o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="40936-136">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the **1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="40936-137">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="40936-137">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="40936-138">Repita essas etapas para o **Microsoft.ML.Recommender v0.12.0**.</span><span class="sxs-lookup"><span data-stu-id="40936-138">Repeat these steps for **Microsoft.ML.Recommender v0.12.0**.</span></span>

4. <span data-ttu-id="40936-139">Adicione as seguintes instruções `using` à parte superior do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="40936-139">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[UsingStatements](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UsingStatements "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="40936-140">Baixar os dados</span><span class="sxs-lookup"><span data-stu-id="40936-140">Download your data</span></span>

1. <span data-ttu-id="40936-141">Baixe os dois conjuntos de dados e salve-os na pasta *Data* criada anteriormente:</span><span class="sxs-lookup"><span data-stu-id="40936-141">Download the two datasets and save them to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="40936-142">Clique com o botão direito do mouse em [*recommendation-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) e selecione "Salvar Link (ou Destino) como..."</span><span class="sxs-lookup"><span data-stu-id="40936-142">Right click on [*recommendation-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) and select "Save Link (or Target) As..."</span></span>
   * <span data-ttu-id="40936-143">Clique com o botão direito do mouse em [*recommendation-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) e selecione "Salvar Link (ou Destino) como..."</span><span class="sxs-lookup"><span data-stu-id="40936-143">Right click on [*recommendation-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="40936-144">Salve os arquivos \*.csv na pasta *Data* ou, depois de salvá-los em outro lugar, mova os arquivos \*.csv para a pasta *Data*.</span><span class="sxs-lookup"><span data-stu-id="40936-144">Make sure you either save the \*.csv files to the *Data* folder, or after you save it elsewhere, move the \*.csv files to the *Data* folder.</span></span>

2. <span data-ttu-id="40936-145">No Gerenciador de Soluções, clique com o botão direito do mouse em cada um dos arquivos \*.csv e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="40936-145">In Solution Explorer, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="40936-146">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.</span><span class="sxs-lookup"><span data-stu-id="40936-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

   ![Copiar se for o mais recente no VS](./media/movie-recommendation/copytoout.gif)

## <a name="load-your-data"></a><span data-ttu-id="40936-148">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="40936-148">Load your data</span></span>

<span data-ttu-id="40936-149">A primeira etapa no processo do ML.NET é preparar e carregar os dados de treinamento e teste de modelo.</span><span class="sxs-lookup"><span data-stu-id="40936-149">The first step in the ML.NET process is to prepare and load your model training and testing data.</span></span>

<span data-ttu-id="40936-150">Os dados de classificações de recomendação são divididos nos conjuntos de dados `Train` e `Test`.</span><span class="sxs-lookup"><span data-stu-id="40936-150">The recommendation ratings data is split into `Train` and `Test` datasets.</span></span> <span data-ttu-id="40936-151">Os dados `Train` são usados para ajustar o modelo.</span><span class="sxs-lookup"><span data-stu-id="40936-151">The `Train` data is used to fit your model.</span></span> <span data-ttu-id="40936-152">Os dados `Test` são usados para fazer previsões com o modelo treinado e avaliar o desempenho do modelo.</span><span class="sxs-lookup"><span data-stu-id="40936-152">The `Test` data is used to make predictions with your trained model and evaluate model performance.</span></span> <span data-ttu-id="40936-153">É comum ter uma divisão 80/20 com os dados `Train` e `Test`.</span><span class="sxs-lookup"><span data-stu-id="40936-153">It's common to have an 80/20 split with `Train` and `Test` data.</span></span>

<span data-ttu-id="40936-154">Segue abaixo uma visualização dos dados nos arquivos \*.csv:</span><span class="sxs-lookup"><span data-stu-id="40936-154">Below is a preview of the data from your \*.csv files:</span></span>

![visualização de dados](./media/movie-recommendation/csv-dataset-preview.png)

<span data-ttu-id="40936-156">Nos arquivos \*.csv, há quatro colunas:</span><span class="sxs-lookup"><span data-stu-id="40936-156">In the \*.csv files, there are four columns:</span></span>

* `userId`
* `movieId`
* `rating`
* `timestamp`

<span data-ttu-id="40936-157">No aprendizado de máquina, as colunas que são usadas para fazer uma previsão são chamadas [Recursos](../resources/glossary.md#feature) e a coluna com a previsão retornada é chamada o [Rótulo](../resources/glossary.md#label).</span><span class="sxs-lookup"><span data-stu-id="40936-157">In machine learning, the columns that are used to make a prediction are called [Features](../resources/glossary.md#feature), and the column with the returned prediction is called the [Label](../resources/glossary.md#label).</span></span>

<span data-ttu-id="40936-158">Você deseja prever as classificações de filmes, portanto, a coluna de classificação é o `Label`.</span><span class="sxs-lookup"><span data-stu-id="40936-158">You want to predict movie ratings, so the rating column is the `Label`.</span></span> <span data-ttu-id="40936-159">As outras três colunas, `userId`, `movieId` e `timestamp`, são todos `Features` usados para prever o `Label`.</span><span class="sxs-lookup"><span data-stu-id="40936-159">The other three columns, `userId`, `movieId`, and `timestamp` are all `Features` used to predict the `Label`.</span></span>

| <span data-ttu-id="40936-160">Recursos</span><span class="sxs-lookup"><span data-stu-id="40936-160">Features</span></span>      | <span data-ttu-id="40936-161">Rotular</span><span class="sxs-lookup"><span data-stu-id="40936-161">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |
| `timestamp`     |               |

<span data-ttu-id="40936-162">Cabe a você decidir quais `Features` são usados para prever o `Label`.</span><span class="sxs-lookup"><span data-stu-id="40936-162">It's up to you to decide which `Features` are used to predict the `Label`.</span></span> <span data-ttu-id="40936-163">Você também pode usar métodos como [Importância de Permuta do Recurso](../how-to-guides/determine-global-feature-importance-in-model.md) para ajudar a selecionar os melhores `Features`.</span><span class="sxs-lookup"><span data-stu-id="40936-163">You can also use methods like [Feature Permutation Importance](../how-to-guides/determine-global-feature-importance-in-model.md) to help with selecting the best `Features`.</span></span>

<span data-ttu-id="40936-164">Nesse caso, você deve eliminar a coluna `timestamp` como um `Feature` porque o carimbo de data/hora não afeta como um usuário classifica determinado filme e, portanto, não contribui para uma previsão mais precisa:</span><span class="sxs-lookup"><span data-stu-id="40936-164">In this case, you should eliminate the `timestamp` column as a `Feature` because the timestamp does not really affect how a user rates a given movie and thus would not contribute to making a more accurate prediction:</span></span>

| <span data-ttu-id="40936-165">Recursos</span><span class="sxs-lookup"><span data-stu-id="40936-165">Features</span></span>      | <span data-ttu-id="40936-166">Rotular</span><span class="sxs-lookup"><span data-stu-id="40936-166">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |

<span data-ttu-id="40936-167">Em seguida, é necessário definir a estrutura de dados para a classe de entrada.</span><span class="sxs-lookup"><span data-stu-id="40936-167">Next you must define your data structure for the input class.</span></span>

<span data-ttu-id="40936-168">Adicione uma nova classe ao seu projeto:</span><span class="sxs-lookup"><span data-stu-id="40936-168">Add a new class to your project:</span></span>

1. <span data-ttu-id="40936-169">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e, em seguida, selecione **Adicionar > Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="40936-169">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="40936-170">Na **caixa de diálogo Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *MovieRatingData.cs*.</span><span class="sxs-lookup"><span data-stu-id="40936-170">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *MovieRatingData.cs*.</span></span> <span data-ttu-id="40936-171">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="40936-171">Then, select the **Add** button.</span></span>

<span data-ttu-id="40936-172">O arquivo *MovieRatingData.cs* será aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="40936-172">The *MovieRatingData.cs* file opens in the code editor.</span></span> <span data-ttu-id="40936-173">Adicione a seguinte instrução `using` acima de *MovieRatingData.cs*:</span><span class="sxs-lookup"><span data-stu-id="40936-173">Add the following `using` statement to the top of *MovieRatingData.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="40936-174">Crie uma classe chamada `MovieRating` removendo a definição de classe existente e adicionando o seguinte código a *MovieRatingData.cs*:</span><span class="sxs-lookup"><span data-stu-id="40936-174">Create a class called `MovieRating` by removing the existing class definition and adding the following code in *MovieRatingData.cs*:</span></span>

[!code-csharp[MovieRatingClass](~/samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#MovieRatingClass "Add the Movie Rating class")]

<span data-ttu-id="40936-175">`MovieRating` especifica uma classe de dados de entrada.</span><span class="sxs-lookup"><span data-stu-id="40936-175">`MovieRating` specifies an input data class.</span></span> <span data-ttu-id="40936-176">O atributo [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) especifica quais colunas (por índice de coluna) no conjunto de dados devem ser carregadas.</span><span class="sxs-lookup"><span data-stu-id="40936-176">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> <span data-ttu-id="40936-177">As colunas `userId` e `movieId` são os `Features` (as entradas que você fornecerá ao modelo para prever o `Label`), e a coluna de classificação é o `Label`, que você preverá (a saída do modelo).</span><span class="sxs-lookup"><span data-stu-id="40936-177">The `userId` and `movieId` columns are your `Features` (the inputs you will give the model to predict the `Label`), and the rating column is the `Label` that you will predict (the output of the model).</span></span>

<span data-ttu-id="40936-178">Crie outra classe, `MovieRatingPrediction`, para representar os resultados previstos adicionando o seguinte código após a classe `MovieRating` em *MovieRatingData.cs*:</span><span class="sxs-lookup"><span data-stu-id="40936-178">Create another class, `MovieRatingPrediction`, to represent predicted results by adding the following code after the `MovieRating` class in *MovieRatingData.cs*:</span></span>

[!code-csharp[PredictionClass](~/samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#PredictionClass "Add the Movie Prediction Class")]

<span data-ttu-id="40936-179">Em *Program.cs*, substitua o `Console.WriteLine("Hello World!")` pelo seguinte código dentro de `Main()`:</span><span class="sxs-lookup"><span data-stu-id="40936-179">In *Program.cs*, replace the `Console.WriteLine("Hello World!")` with the following code inside `Main()`:</span></span>

[!code-csharp[MLContext](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MLContext "Add MLContext")]

<span data-ttu-id="40936-180">A [classe MLContext](xref:Microsoft.ML.MLContext) é um ponto de partida para todas as operações do ML.NET e a inicialização do `mlContext` cria um ambiente do ML.NET que pode ser compartilhado entre os objetos de fluxo de trabalho da criação de modelo.</span><span class="sxs-lookup"><span data-stu-id="40936-180">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="40936-181">Ele é semelhante, conceitualmente, a `DBContext` no Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="40936-181">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="40936-182">Após `Main()`, crie um método chamado `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="40936-182">After `Main()`, create a method called `LoadData()`:</span></span>

```csharp
public static (IDataView training, IDataView test) LoadData(MLContext mlContext)
{

}
```

> [!NOTE]
> <span data-ttu-id="40936-183">Esse método apresentará um erro até que você adicione uma instrução de retorno nas etapas a seguir.</span><span class="sxs-lookup"><span data-stu-id="40936-183">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="40936-184">Inicialize as variáveis do caminho de dados, carregue os dados dos arquivos \*.csv e retorne os dados `Train` e `Test` como objetos `IDataView` adicionando o seguinte como a próxima linha de código em `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="40936-184">Initialize your data path variables, load the data from the \*.csv files, and return the `Train` and `Test` data as `IDataView` objects by adding the following as the next line of code in `LoadData()`:</span></span>

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadData "Load data from data paths")]

<span data-ttu-id="40936-185">Os dados do ML.NET são representados como uma [classe IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="40936-185">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="40936-186">`IDataView` é uma maneira flexível e eficiente de descrever dados tabulares (numéricos e texto).</span><span class="sxs-lookup"><span data-stu-id="40936-186">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="40936-187">Os dados podem ser carregados de um arquivo de texto ou em tempo real (por exemplo, banco de dados SQL ou arquivos de log) para um objeto `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="40936-187">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="40936-188">O [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) define o esquema de dados e lê o arquivo.</span><span class="sxs-lookup"><span data-stu-id="40936-188">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="40936-189">Ele usa as variáveis de caminho de dados e retorna uma `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="40936-189">It takes in the data path variables and returns an `IDataView`.</span></span> <span data-ttu-id="40936-190">Nesse caso, você fornece o caminho para os arquivos `Test` e `Train` e indica o cabeçalho do arquivo de texto (para que ele possa usar os nomes de coluna corretamente) e o separador de dados de caractere de vírgula (o separador padrão é uma guia).</span><span class="sxs-lookup"><span data-stu-id="40936-190">In this case, you provide the path for your `Test` and `Train` files and indicate both the text file header (so it can use the column names properly) and the comma character data separator (the default separator is a tab).</span></span>

<span data-ttu-id="40936-191">Adicione o seguinte como as próximas duas linhas de código no método `Main()` para chamar o método `LoadData()` e retornar os dados `Train` e `Test`:</span><span class="sxs-lookup"><span data-stu-id="40936-191">Add the following as the next two lines of code in the `Main()` method to call your `LoadData()` method and return the `Train` and `Test` data:</span></span>

[!code-csharp[LoadDataMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadDataMain "Add LoadData method to Main")]

## <a name="build-and-train-your-model"></a><span data-ttu-id="40936-192">Criar e treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="40936-192">Build and train your model</span></span>

<span data-ttu-id="40936-193">Há três conceitos principais no ML.NET: [Dados](../resources/glossary.md#data), [Transformadores](../resources/glossary.md#transformer) e [Avaliadores](../resources/glossary.md#estimator).</span><span class="sxs-lookup"><span data-stu-id="40936-193">There are three major concepts in ML.NET: [Data](../resources/glossary.md#data), [Transformers](../resources/glossary.md#transformer), and [Estimators](../resources/glossary.md#estimator).</span></span>

<span data-ttu-id="40936-194">Os algoritmos de treinamento de aprendizado de máquina exigem que os dados estejam em determinado formato.</span><span class="sxs-lookup"><span data-stu-id="40936-194">Machine learning training algorithms require data in a certain format.</span></span> <span data-ttu-id="40936-195">`Transformers` são usados para transformar dados de tabela em um formato compatível.</span><span class="sxs-lookup"><span data-stu-id="40936-195">`Transformers` are used to transform tabular data to a compatible format.</span></span>

![imagem do transformador](./media/movie-recommendation/transformer.png)

<span data-ttu-id="40936-197">Crie `Transformers` no ML.NET criando `Estimators`.</span><span class="sxs-lookup"><span data-stu-id="40936-197">You create `Transformers` in ML.NET by creating `Estimators`.</span></span> <span data-ttu-id="40936-198">`Estimators` usa dados e retorna `Transformers`.</span><span class="sxs-lookup"><span data-stu-id="40936-198">`Estimators` take in data and return `Transformers`.</span></span>

![imagem do avaliador](./media/movie-recommendation/estimator.png)

<span data-ttu-id="40936-200">O algoritmo de treinamento de recomendação que você usará para treinar seu modelo é um exemplo de `Estimator`.</span><span class="sxs-lookup"><span data-stu-id="40936-200">The recommendation training algorithm you will use for training your model is an example of an `Estimator`.</span></span>

<span data-ttu-id="40936-201">Crie um `Estimator` com as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="40936-201">Build an `Estimator` with the following steps:</span></span>

<span data-ttu-id="40936-202">Crie o método `BuildAndTrainModel()`, logo após o método `LoadData()`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="40936-202">Create the `BuildAndTrainModel()` method, just after the `LoadData()` method, using the following code:</span></span>

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView trainingDataView)
{

}
```

> [!NOTE]
> <span data-ttu-id="40936-203">Esse método apresentará um erro até que você adicione uma instrução de retorno nas etapas a seguir.</span><span class="sxs-lookup"><span data-stu-id="40936-203">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="40936-204">Defina as transformações de dados adicionando o seguinte código a `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="40936-204">Define the data transformations by adding the following code to `BuildAndTrainModel()`:</span></span>

[!code-csharp[DataTransformations](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#DataTransformations "Define data transformations")]

<span data-ttu-id="40936-205">Como `userId` e `movieId` representam usuários e títulos de filmes, não valores reais, use o método [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) para transformar cada `userId` e cada `movieId` em uma coluna `Feature` de tipo de chave numérica (um formato aceito pelos algoritmos de recomendação) e adicioná-los como novas colunas de conjunto de dados:</span><span class="sxs-lookup"><span data-stu-id="40936-205">Since `userId` and `movieId` represent users and movie titles, not real values, you use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform each `userId` and each `movieId` into a numeric key type `Feature` column (a format accepted by recommendation algorithms) and add them as new dataset columns:</span></span>

| <span data-ttu-id="40936-206">userId</span><span class="sxs-lookup"><span data-stu-id="40936-206">userId</span></span> | <span data-ttu-id="40936-207">movieId</span><span class="sxs-lookup"><span data-stu-id="40936-207">movieId</span></span> | <span data-ttu-id="40936-208">Rotular</span><span class="sxs-lookup"><span data-stu-id="40936-208">Label</span></span> | <span data-ttu-id="40936-209">userIdEncoded</span><span class="sxs-lookup"><span data-stu-id="40936-209">userIdEncoded</span></span> | <span data-ttu-id="40936-210">movieIdEncoded</span><span class="sxs-lookup"><span data-stu-id="40936-210">movieIdEncoded</span></span> |
| ------------- |:-------------:| -----:|-----:|-----:|
| <span data-ttu-id="40936-211">1</span><span class="sxs-lookup"><span data-stu-id="40936-211">1</span></span> | <span data-ttu-id="40936-212">1</span><span class="sxs-lookup"><span data-stu-id="40936-212">1</span></span> | <span data-ttu-id="40936-213">4</span><span class="sxs-lookup"><span data-stu-id="40936-213">4</span></span> | <span data-ttu-id="40936-214">userKey1</span><span class="sxs-lookup"><span data-stu-id="40936-214">userKey1</span></span> | <span data-ttu-id="40936-215">movieKey1</span><span class="sxs-lookup"><span data-stu-id="40936-215">movieKey1</span></span> |
| <span data-ttu-id="40936-216">1</span><span class="sxs-lookup"><span data-stu-id="40936-216">1</span></span> | <span data-ttu-id="40936-217">3</span><span class="sxs-lookup"><span data-stu-id="40936-217">3</span></span> | <span data-ttu-id="40936-218">4</span><span class="sxs-lookup"><span data-stu-id="40936-218">4</span></span> | <span data-ttu-id="40936-219">userKey1</span><span class="sxs-lookup"><span data-stu-id="40936-219">userKey1</span></span> | <span data-ttu-id="40936-220">movieKey2</span><span class="sxs-lookup"><span data-stu-id="40936-220">movieKey2</span></span> |
| <span data-ttu-id="40936-221">1</span><span class="sxs-lookup"><span data-stu-id="40936-221">1</span></span> | <span data-ttu-id="40936-222">6</span><span class="sxs-lookup"><span data-stu-id="40936-222">6</span></span> | <span data-ttu-id="40936-223">4</span><span class="sxs-lookup"><span data-stu-id="40936-223">4</span></span> | <span data-ttu-id="40936-224">userKey1</span><span class="sxs-lookup"><span data-stu-id="40936-224">userKey1</span></span> | <span data-ttu-id="40936-225">movieKey3</span><span class="sxs-lookup"><span data-stu-id="40936-225">movieKey3</span></span> |

<span data-ttu-id="40936-226">Escolha o algoritmo de aprendizado de máquina e acrescente-o às definições de transformação de dados adicionando o seguinte como a próxima linha de código em `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="40936-226">Choose the machine learning algorithm and append it to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddAlgorithm](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#AddAlgorithm "Add the training algorithm with options")]

<span data-ttu-id="40936-227">O [MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) é o algoritmo de treinamento de recomendação.</span><span class="sxs-lookup"><span data-stu-id="40936-227">The [MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) is your recommendation training algorithm.</span></span>  <span data-ttu-id="40936-228">A [Fatoração de Matriz](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) é uma abordagem comum de recomendação quando você tem dados sobre como os usuários classificaram produtos no passado, que é o caso para os conjuntos de dados deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="40936-228">[Matrix Factorization](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) is a common approach to recommendation when you have data on how users have rated products in the past, which is the case for the datasets in this tutorial.</span></span> <span data-ttu-id="40936-229">Há outros algoritmos de recomendação para quando você tem diferentes dados disponíveis (confira a seção [Outros algoritmos de recomendação](#other-recommendation-algorithms) abaixo para saber mais).</span><span class="sxs-lookup"><span data-stu-id="40936-229">There are other recommendation algorithms for when you have different data available (see the [Other recommendation algorithms](#other-recommendation-algorithms) section below to learn more).</span></span>

<span data-ttu-id="40936-230">Nesse caso, o algoritmo `Matrix Factorization` usa um método chamado "filtragem colaborativa", que supõe que, se o Usuário 1 tem a mesma opinião do Usuário 2 sobre determinada questão, é mais provável que o Usuário 1 sinta-se da mesma forma que o Usuário 2 sobre outra questão.</span><span class="sxs-lookup"><span data-stu-id="40936-230">In this case, the `Matrix Factorization` algorithm uses a method called "collaborative filtering", which assumes that if User 1 has the same opinion as User 2 on a certain issue, then User 1 is more likely to feel the same way as User 2 about a different issue.</span></span>

<span data-ttu-id="40936-231">Por exemplo, se o Usuário 1 e o Usuário 2 classificam filmes de forma semelhante, é mais provável que o Usuário 2 goste de um filme que o Usuário 1 assistiu e forneceu uma classificação alta:</span><span class="sxs-lookup"><span data-stu-id="40936-231">For instance, if User 1 and User 2 rate movies similarly, then User 2 is more likely to enjoy a movie that User 1 has watched and rated highly:</span></span>

| | `Incredibles 2 (2018)` | `The Avengers (2012)` | `Guardians of the Galaxy (2014)` |
| -------------:|-------------:| -----:|-----:|
| <span data-ttu-id="40936-232">Usuário 1</span><span class="sxs-lookup"><span data-stu-id="40936-232">User 1</span></span> | <span data-ttu-id="40936-233">Assistiu e gostou do filme</span><span class="sxs-lookup"><span data-stu-id="40936-233">Watched and liked movie</span></span> | <span data-ttu-id="40936-234">Assistiu e gostou do filme</span><span class="sxs-lookup"><span data-stu-id="40936-234">Watched and liked movie</span></span> | <span data-ttu-id="40936-235">Assistiu e gostou do filme</span><span class="sxs-lookup"><span data-stu-id="40936-235">Watched and liked movie</span></span> |
| <span data-ttu-id="40936-236">Usuário 2</span><span class="sxs-lookup"><span data-stu-id="40936-236">User 2</span></span> | <span data-ttu-id="40936-237">Assistiu e gostou do filme</span><span class="sxs-lookup"><span data-stu-id="40936-237">Watched and liked movie</span></span> | <span data-ttu-id="40936-238">Assistiu e gostou do filme</span><span class="sxs-lookup"><span data-stu-id="40936-238">Watched and liked movie</span></span> | <span data-ttu-id="40936-239">Não assistiu – RECOMENDAR o filme</span><span class="sxs-lookup"><span data-stu-id="40936-239">Has not watched -- RECOMMEND movie</span></span> |

<span data-ttu-id="40936-240">O treinador `Matrix Factorization` tem várias [Opções](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), sobre as quais você pode ler mais na seção [Hiperparâmetros de algoritmo](#algorithm-hyperparameters) abaixo.</span><span class="sxs-lookup"><span data-stu-id="40936-240">The `Matrix Factorization` trainer has several [Options](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), which you can read more about in the [Algorithm hyperparameters](#algorithm-hyperparameters) section below.</span></span>

<span data-ttu-id="40936-241">Ajuste o modelo aos dados `Train` e retorne o modelo treinado adicionando o seguinte como a próxima linha de código no método `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="40936-241">Fit the model to the `Train` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[FitModel](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#FitModel "Call the Fit method and return back the trained model")]

<span data-ttu-id="40936-242">O método [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) treina o modelo com o conjunto de dados de treinamento fornecido.</span><span class="sxs-lookup"><span data-stu-id="40936-242">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model with the provided training dataset.</span></span> <span data-ttu-id="40936-243">Tecnicamente, ele executa as definições `Estimator` transformando os dados e aplicando o treinamento e retorna o modelo treinado, que é um `Transformer`.</span><span class="sxs-lookup"><span data-stu-id="40936-243">Technically, it executes the `Estimator` definitions by transforming the data and applying the training, and it returns back the trained model, which is a `Transformer`.</span></span>

<span data-ttu-id="40936-244">Adicione o seguinte como a próxima linha de código no método `Main()` para chamar o método `BuildAndTrainModel()` e retornar o modelo treinado:</span><span class="sxs-lookup"><span data-stu-id="40936-244">Add the following as the next line of code in the `Main()` method to call your `BuildAndTrainModel()` method and return the trained model:</span></span>

[!code-csharp[BuildTrainModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#BuildTrainModelMain "Add BuildAndTrainModel method in Main")]

## <a name="evaluate-your-model"></a><span data-ttu-id="40936-245">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="40936-245">Evaluate your model</span></span>

<span data-ttu-id="40936-246">Depois de treinar o modelo, use os dados de teste para avaliar o desempenho do modelo.</span><span class="sxs-lookup"><span data-stu-id="40936-246">Once you have trained your model, use your test data to evaluate how your model is performing.</span></span>

<span data-ttu-id="40936-247">Crie o método `EvaluateModel()`, logo após o método `BuildAndTrainModel()`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="40936-247">Create the `EvaluateModel()` method, just after the `BuildAndTrainModel()` method, using the following code:</span></span>

```csharp
public static void EvaluateModel(MLContext mlContext, IDataView testDataView, ITransformer model)
{

}
```

<span data-ttu-id="40936-248">Transforme os dados `Test` adicionando o seguinte código a `EvaluateModel()`: [!code-csharp[Transform](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Transform "Transform the test data")]</span><span class="sxs-lookup"><span data-stu-id="40936-248">Transform the `Test` data by adding the following code to `EvaluateModel()`: [!code-csharp[Transform](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Transform "Transform the test data")]</span></span>

<span data-ttu-id="40936-249">O método [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) faz previsões para várias linhas de entrada fornecidas de um conjunto de dados de teste.</span><span class="sxs-lookup"><span data-stu-id="40936-249">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for multiple provided input rows of a test dataset.</span></span>

<span data-ttu-id="40936-250">Avalie o modelo adicionando o seguinte como a próxima linha de código no método `EvaluateModel()`:</span><span class="sxs-lookup"><span data-stu-id="40936-250">Evaluate the model by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Evaluate "Evaluate the model using predictions from the test data")]

<span data-ttu-id="40936-251">Depois que você define a previsão, o método [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) avalia o modelo, que compara os valores previstos com os `Labels` reais no conjunto de dados de teste e retorna métricas sobre o desempenho do modelo.</span><span class="sxs-lookup"><span data-stu-id="40936-251">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="40936-252">Imprima as métricas de avaliação no console adicionando o seguinte como a próxima linha de código no método `EvaluateModel()`:</span><span class="sxs-lookup"><span data-stu-id="40936-252">Print your evaluation metrics to the console by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[PrintMetrics](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintMetrics "Print the evaluation metrics")]

<span data-ttu-id="40936-253">Adicione o seguinte como a próxima linha de código no método `Main()` para chamar o método `EvaluateModel()`:</span><span class="sxs-lookup"><span data-stu-id="40936-253">Add the following as the next line of code in the `Main()` method to call your `EvaluateModel()` method:</span></span>

[!code-csharp[EvaluateModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#EvaluateModelMain "Add EvaluateModel method in Main")]

<span data-ttu-id="40936-254">Até agora, a saída deve ser semelhante ao seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="40936-254">The output so far should look similar to the following text:</span></span>

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

<span data-ttu-id="40936-255">Nessa saída, há 20 iterações.</span><span class="sxs-lookup"><span data-stu-id="40936-255">In this output, there are 20 iterations.</span></span> <span data-ttu-id="40936-256">Em cada iteração, a medida de erro diminui e é convergida para mais próximo de 0.</span><span class="sxs-lookup"><span data-stu-id="40936-256">In each iteration, the measure of error decreases and converges closer and closer to 0.</span></span>

<span data-ttu-id="40936-257">A `root of mean squared error` (RMS ou RMSE) é usada para medir as diferenças entre os valores previstos do modelo e os valores observados do conjunto de dados de teste.</span><span class="sxs-lookup"><span data-stu-id="40936-257">The `root of mean squared error` (RMS or RMSE) is used to measure the differences between the model predicted values and the test dataset observed values.</span></span> <span data-ttu-id="40936-258">Tecnicamente, ela é a raiz quadrada da média dos quadrados dos erros.</span><span class="sxs-lookup"><span data-stu-id="40936-258">Technically it's the square root of the average of the squares of the errors.</span></span> <span data-ttu-id="40936-259">Quanto menor, melhor o modelo.</span><span class="sxs-lookup"><span data-stu-id="40936-259">The lower it is, the better the model is.</span></span>

<span data-ttu-id="40936-260">`R Squared` indica o quanto os dados se ajustam a um modelo.</span><span class="sxs-lookup"><span data-stu-id="40936-260">`R Squared` indicates how well data fits a model.</span></span> <span data-ttu-id="40936-261">Varia de 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="40936-261">Ranges from 0 to 1.</span></span> <span data-ttu-id="40936-262">Um valor de 0 significa que os dados são aleatórios ou não podem ser ajustados ao modelo.</span><span class="sxs-lookup"><span data-stu-id="40936-262">A value of 0 means that the data is random or otherwise can't be fit to the model.</span></span> <span data-ttu-id="40936-263">Um valor de 1 significa que o modelo corresponde exatamente aos dados.</span><span class="sxs-lookup"><span data-stu-id="40936-263">A value of 1 means that the model exactly matches the data.</span></span> <span data-ttu-id="40936-264">Você deseja que a pontuação `R Squared` esteja o mais próximo possível de 1.</span><span class="sxs-lookup"><span data-stu-id="40936-264">You want your `R Squared` score to be as close to 1 as possible.</span></span>

<span data-ttu-id="40936-265">A criação de modelos bem-sucedidos é um processo iterativo.</span><span class="sxs-lookup"><span data-stu-id="40936-265">Building successful models is an iterative process.</span></span> <span data-ttu-id="40936-266">Esse modelo tem qualidade inicial inferior, pois o tutorial usa conjuntos de dados pequenos para fornecer um treinamento rápido do modelo.</span><span class="sxs-lookup"><span data-stu-id="40936-266">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="40936-267">Se você não estiver satisfeito com a qualidade do modelo, tente melhorá-lo fornecendo conjuntos de dados de treinamento maiores ou escolhendo diferentes algoritmos de treinamento com diferentes hiperparâmetros para cada algoritmo.</span><span class="sxs-lookup"><span data-stu-id="40936-267">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different hyper-parameters for each algorithm.</span></span> <span data-ttu-id="40936-268">Para obter mais informações, confira a seção [Melhorar o modelo](#improve-your-model) abaixo.</span><span class="sxs-lookup"><span data-stu-id="40936-268">For more information, check out the [Improve your model](#improve-your-model) section below.</span></span>

## <a name="use-your-model"></a><span data-ttu-id="40936-269">Usar o modelo</span><span class="sxs-lookup"><span data-stu-id="40936-269">Use your model</span></span>

<span data-ttu-id="40936-270">Agora você pode usar o modelo treinado para fazer previsões sobre novos dados.</span><span class="sxs-lookup"><span data-stu-id="40936-270">Now you can use your trained model to make predictions on new data.</span></span>

<span data-ttu-id="40936-271">Crie o método `UseModelForSinglePrediction()`, logo após o método `EvaluateModel()`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="40936-271">Create the `UseModelForSinglePrediction()` method, just after the `EvaluateModel()` method, using the following code:</span></span>

```csharp
public static void UseModelForSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="40936-272">Use o `PredictionEngine` para prever a classificação adicionando o seguinte código à `UseModelForSinglePrediction()`:</span><span class="sxs-lookup"><span data-stu-id="40936-272">Use the `PredictionEngine` to predict the rating by adding the following code to `UseModelForSinglePrediction()`:</span></span>

[!code-csharp[PredictionEngine](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PredictionEngine "Create Prediction Engine")]

<span data-ttu-id="40936-273">A [classe PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) é uma API de conveniência, que permite passar uma única instância de dados e, em seguida, executar uma previsão nessa única instância de dados.</span><span class="sxs-lookup"><span data-stu-id="40936-273">The [PredictionEngine class](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass a single instance of data and then perform a prediction on this single instance of data.</span></span>

<span data-ttu-id="40936-274">Crie uma instância de `MovieRating` chamada `testInput` e passe-a para o Mecanismo de Previsão adicionando o seguinte como as próximas linhas do código no método `UseModelForSinglePrediction()`:</span><span class="sxs-lookup"><span data-stu-id="40936-274">Create an instance of `MovieRating` called `testInput` and pass it to the Prediction Engine by adding the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[MakeSinglePrediction](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MakeSinglePrediction "Make a single prediction with the Prediction Engine")]

<span data-ttu-id="40936-275">A função [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) faz uma previsão sobre uma única coluna de dados.</span><span class="sxs-lookup"><span data-stu-id="40936-275">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single column of data.</span></span>

<span data-ttu-id="40936-276">Em seguida, use a `Score`, ou a classificação prevista, para determinar se deseja recomendar o filme com a movieId 10 para o usuário 6.</span><span class="sxs-lookup"><span data-stu-id="40936-276">You can then use the `Score`, or the predicted rating, to determine whether you want to recommend the movie with movieId 10 to user 6.</span></span> <span data-ttu-id="40936-277">Quanto mais alta a `Score`, maior a probabilidade de um usuário gostar de um filme específico.</span><span class="sxs-lookup"><span data-stu-id="40936-277">The higher the `Score`, the higher the likelihood of a user liking a particular movie.</span></span> <span data-ttu-id="40936-278">Nesse caso, digamos que você recomende filmes com uma classificação prevista de > 3,5.</span><span class="sxs-lookup"><span data-stu-id="40936-278">In this case, let’s say that you recommend movies with a predicted rating of > 3.5.</span></span>

<span data-ttu-id="40936-279">Para imprimir os resultados, adicione o seguinte como as próximas linhas de código no método `UseModelForSinglePrediction()`:</span><span class="sxs-lookup"><span data-stu-id="40936-279">To print the results, add the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[PrintResults](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintResults "Print the recommendation prediction results")]

<span data-ttu-id="40936-280">Adicione o seguinte como a próxima linha de código no método `Main()` para chamar o método `UseModelForSinglePrediction()`:</span><span class="sxs-lookup"><span data-stu-id="40936-280">Add the following as the next line of code in the `Main()` method to call your `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[UseModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UseModelMain "Add UseModelForSinglePrediction method in Main")]

<span data-ttu-id="40936-281">A saída desse método deve ser semelhante ao seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="40936-281">The output of this method should look similar to the following text:</span></span>

```console
=============== Making a prediction ===============
Movie 10 is recommended for user 6
```

### <a name="save-your-model"></a><span data-ttu-id="40936-282">Salvar o modelo</span><span class="sxs-lookup"><span data-stu-id="40936-282">Save your model</span></span>

<span data-ttu-id="40936-283">Para usar o modelo para fazer previsões em aplicativos de usuário final, primeiro é necessário salvar o modelo.</span><span class="sxs-lookup"><span data-stu-id="40936-283">To use your model to make predictions in end-user applications, you must first save the model.</span></span>

<span data-ttu-id="40936-284">Crie o método `SaveModel()`, logo após o método `UseModelForSinglePrediction()`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="40936-284">Create the `SaveModel()` method, just after the `UseModelForSinglePrediction()` method, using the following code:</span></span>

```csharp
public static void SaveModel(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="40936-285">Salve o modelo treinado adicionando o seguinte código ao método `SaveModel()`:</span><span class="sxs-lookup"><span data-stu-id="40936-285">Save your trained model by adding the following code in the `SaveModel()` method:</span></span>

[!code-csharp[SaveModel](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModel "Save the model to a zip file")]

<span data-ttu-id="40936-286">Esse método salva o modelo treinado em um arquivo .zip (na pasta "Data"), que pode ser usado em outros aplicativos .NET para fazer previsões.</span><span class="sxs-lookup"><span data-stu-id="40936-286">This method saves your trained model to a .zip file (in the "Data" folder), which can then be used in other .NET applications to make predictions.</span></span>

<span data-ttu-id="40936-287">Adicione o seguinte como a próxima linha de código no método `Main()` para chamar o método `SaveModel()`:</span><span class="sxs-lookup"><span data-stu-id="40936-287">Add the following as the next line of code in the `Main()` method to call your `SaveModel()` method:</span></span>

[!code-csharp[SaveModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModelMain "Create SaveModel method in Main")]

### <a name="use-your-saved-model"></a><span data-ttu-id="40936-288">Usar o modelo salvo</span><span class="sxs-lookup"><span data-stu-id="40936-288">Use your saved model</span></span>

<span data-ttu-id="40936-289">Depois de salvar o modelo treinado, você poderá consumir o modelo em ambientes diferentes (confira o ["Guia de instruções"](../how-to-guides/consuming-model-ml-net.md) para saber como operacionalizar um modelo de machine learning treinado em aplicativos).</span><span class="sxs-lookup"><span data-stu-id="40936-289">Once you have saved your trained model, you can consume the model in different environments (see the ["How-to guide"](../how-to-guides/consuming-model-ml-net.md) to learn how to operationalize a trained machine learning model in apps).</span></span>

## <a name="results"></a><span data-ttu-id="40936-290">Resultados</span><span class="sxs-lookup"><span data-stu-id="40936-290">Results</span></span>

<span data-ttu-id="40936-291">Depois de seguir as etapas acima, execute o aplicativo de console (Ctrl + F5).</span><span class="sxs-lookup"><span data-stu-id="40936-291">After following the steps above, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="40936-292">Os resultados da previsão individual acima deverão ser semelhantes ao mostrado a seguir.</span><span class="sxs-lookup"><span data-stu-id="40936-292">Your results from the single prediction above should be similar to the following.</span></span> <span data-ttu-id="40936-293">Você poderá ver avisos ou mensagens de processamento, mas essas mensagens foram removidas dos resultados a seguir para maior clareza.</span><span class="sxs-lookup"><span data-stu-id="40936-293">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="40936-294">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="40936-294">Congratulations!</span></span> <span data-ttu-id="40936-295">Você agora criou um modelo de machine learning para recomendação de filmes.</span><span class="sxs-lookup"><span data-stu-id="40936-295">You've now successfully built a machine learning model for recommending movies.</span></span> <span data-ttu-id="40936-296">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation).</span><span class="sxs-lookup"><span data-stu-id="40936-296">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="improve-your-model"></a><span data-ttu-id="40936-297">Melhorar o modelo</span><span class="sxs-lookup"><span data-stu-id="40936-297">Improve your model</span></span>

<span data-ttu-id="40936-298">Há várias maneiras de melhorar o desempenho do modelo para obter previsões mais precisas.</span><span class="sxs-lookup"><span data-stu-id="40936-298">There are several ways that you can improve the performance of your model so that you can get more accurate predictions.</span></span>

### <a name="data"></a><span data-ttu-id="40936-299">Dados</span><span class="sxs-lookup"><span data-stu-id="40936-299">Data</span></span>

<span data-ttu-id="40936-300">A adição de mais dados de treinamento que tenham amostras suficientes para cada usuário e a ID de filme pode ajudar a melhorar a qualidade do modelo de recomendação.</span><span class="sxs-lookup"><span data-stu-id="40936-300">Adding more training data that has enough samples for each user and movie id can help improve the quality of the recommendation model.</span></span>

<span data-ttu-id="40936-301">A [validação cruzada](../how-to-guides/train-cross-validation-ml-net.md) é uma técnica para avaliação de modelos que divide dados aleatoriamente em subconjuntos (em vez de extrair os dados de teste do conjunto de dados como você fez neste tutorial) e usa alguns dos grupos como dados de treinamento e alguns dos grupos como dados de teste.</span><span class="sxs-lookup"><span data-stu-id="40936-301">[Cross validation](../how-to-guides/train-cross-validation-ml-net.md) is a technique for evaluating models that randomly splits up data into subsets (instead of extracting out test data from the dataset like you did in this tutorial) and takes some of the groups as train data and some of the groups as test data.</span></span> <span data-ttu-id="40936-302">Esse método tem um melhor desempenho do que a divisão treinamento/teste em termos de qualidade do modelo.</span><span class="sxs-lookup"><span data-stu-id="40936-302">This method outperforms making a train-test split in terms of model quality.</span></span>

### <a name="features"></a><span data-ttu-id="40936-303">Recursos</span><span class="sxs-lookup"><span data-stu-id="40936-303">Features</span></span>

<span data-ttu-id="40936-304">Neste tutorial, você só usará os três `Features` (`user id`, `movie id` e `rating`) fornecidos pelo conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="40936-304">In this tutorial, you only use the three `Features` (`user id`, `movie id`, and `rating`) that are provided by the dataset.</span></span>

<span data-ttu-id="40936-305">Embora esse seja um bom começo, na verdade, o ideal será adicionar outros atributos ou `Features` (por exemplo, idade, sexo, localização geográfica etc.) se eles forem incluídos no conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="40936-305">While this is a good start, in reality you might want to add other attributes or `Features` (for example, age, gender, geo-location, etc.) if they are included in the dataset.</span></span> <span data-ttu-id="40936-306">A adição de `Features` mais relevantes pode ajudar a melhorar o desempenho do modelo de recomendação.</span><span class="sxs-lookup"><span data-stu-id="40936-306">Adding more relevant `Features` can help improve the performance of your recommendation model.</span></span>

<span data-ttu-id="40936-307">Caso não tenha certeza sobre quais `Features` podem ser mais relevantes para sua tarefa de aprendizado de máquina, use também o FCC (Cálculo de Contribuição do Recurso) e a [Importância de Permuta do Recurso](../how-to-guides/determine-global-feature-importance-in-model.md), fornecidos pelo ML.NET para descobrir `Features` mais influentes.</span><span class="sxs-lookup"><span data-stu-id="40936-307">If you are unsure about which `Features` might be the most relevant for your machine learning task, you can also make use of Feature Contribution Calculation (FCC) and [Feature Permutation Importance](../how-to-guides/determine-global-feature-importance-in-model.md), which ML.NET provides to discover the most influential `Features`.</span></span>

### <a name="algorithm-hyperparameters"></a><span data-ttu-id="40936-308">Hiperparâmetros de algoritmo</span><span class="sxs-lookup"><span data-stu-id="40936-308">Algorithm hyperparameters</span></span>

<span data-ttu-id="40936-309">Embora o ML.NET forneça bons algoritmos de treinamento padrão, você pode ajustar ainda mais o desempenho alterando os [hiperparâmetros](../resources/glossary.md#hyperparameter) do algoritmo.</span><span class="sxs-lookup"><span data-stu-id="40936-309">While ML.NET provides good default training algorithms, you can further fine-tune performance by changing the algorithm's [hyperparameters](../resources/glossary.md#hyperparameter).</span></span>

<span data-ttu-id="40936-310">Para a `Matrix Factorization`, você pode experimentar com hiperparâmetros, como [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) e [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) para ver se ele oferece melhores resultados.</span><span class="sxs-lookup"><span data-stu-id="40936-310">For `Matrix Factorization`, you can experiment with hyperparameters such as [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) and [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) to see if that gives you better results.</span></span>

<span data-ttu-id="40936-311">Por exemplo, neste tutorial, as opções de algoritmo são:</span><span class="sxs-lookup"><span data-stu-id="40936-311">For instance, in this tutorial the algorithm options are:</span></span>

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

### <a name="other-recommendation-algorithms"></a><span data-ttu-id="40936-312">Outros algoritmos de recomendação</span><span class="sxs-lookup"><span data-stu-id="40936-312">Other Recommendation Algorithms</span></span>

<span data-ttu-id="40936-313">O algoritmo de fatoração de matriz com a filtragem colaborativa é apenas uma abordagem para fazer recomendações de filmes.</span><span class="sxs-lookup"><span data-stu-id="40936-313">The matrix factorization algorithm with collaborative filtering is only one approach for performing movie recommendations.</span></span> <span data-ttu-id="40936-314">Em muitos casos, talvez você não tenha os dados de classificações disponíveis e tenha apenas o histórico de filmes disponível dos usuários.</span><span class="sxs-lookup"><span data-stu-id="40936-314">In many cases, you may not have the ratings data available and only have movie history available from users.</span></span> <span data-ttu-id="40936-315">Em outros casos, você pode ter mais do que apenas os dados de classificação do usuário.</span><span class="sxs-lookup"><span data-stu-id="40936-315">In other cases, you may have more than just the user’s rating data.</span></span>

| <span data-ttu-id="40936-316">Algoritmo</span><span class="sxs-lookup"><span data-stu-id="40936-316">Algorithm</span></span>       | <span data-ttu-id="40936-317">Cenário</span><span class="sxs-lookup"><span data-stu-id="40936-317">Scenario</span></span>           | <span data-ttu-id="40936-318">Amostra</span><span class="sxs-lookup"><span data-stu-id="40936-318">Sample</span></span>  |
| ------------- |:-------------:| -----:|
| <span data-ttu-id="40936-319">Fatoração de Matriz de uma Classe</span><span class="sxs-lookup"><span data-stu-id="40936-319">One Class Matrix Factorization</span></span> | <span data-ttu-id="40936-320">Use isso quando você tiver apenas userId e movieId.</span><span class="sxs-lookup"><span data-stu-id="40936-320">Use this when you only have userId and movieId.</span></span> <span data-ttu-id="40936-321">Esse estilo de recomendação é baseado no cenário de cocompra, ou produtos frequentemente comprados juntos, o que significa que ele recomendará aos clientes um conjunto de produtos de acordo com seu próprio histórico de ordens de compra.</span><span class="sxs-lookup"><span data-stu-id="40936-321">This style of recommendation is based upon the co-purchase scenario, or products frequently bought together, which means it will recommend to customers a set of products based upon their own purchase order history.</span></span> | [<span data-ttu-id="40936-322">>Experimentar</span><span class="sxs-lookup"><span data-stu-id="40936-322">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/MatrixFactorization_ProductRecommendation) |
| <span data-ttu-id="40936-323">Computadores de Fatoração com Reconhecimento de Campo</span><span class="sxs-lookup"><span data-stu-id="40936-323">Field Aware Factorization Machines</span></span> | <span data-ttu-id="40936-324">Use isso para fazer recomendações quando você tiver mais Recursos do que userId, productId e a classificação (como descrição ou preço do produto).</span><span class="sxs-lookup"><span data-stu-id="40936-324">Use this to make recommendations when you have more Features beyond userId, productId, and rating (such as product description or product price).</span></span> <span data-ttu-id="40936-325">Esse método também usa uma abordagem de filtragem colaborativa.</span><span class="sxs-lookup"><span data-stu-id="40936-325">This method also uses a collaborative filtering approach.</span></span> | [<span data-ttu-id="40936-326">>Experimentar</span><span class="sxs-lookup"><span data-stu-id="40936-326">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/Recommendation-MovieRecommender) |

### <a name="new-user-scenario"></a><span data-ttu-id="40936-327">Novo cenário de usuário</span><span class="sxs-lookup"><span data-stu-id="40936-327">New user scenario</span></span>

<span data-ttu-id="40936-328">Um problema comum na filtragem colaborativa é o problema de inicialização a frio, que é quando você tem um novo usuário sem nenhum dado anterior do qual fazer inferências.</span><span class="sxs-lookup"><span data-stu-id="40936-328">One common problem in collaborative filtering is the cold start problem, which is when you have a new user with no previous data to draw inferences from.</span></span> <span data-ttu-id="40936-329">Esse problema costuma ser resolvido com a solicitação da criação de um perfil aos novos usuários e, por exemplo, da classificação de filmes que assistiram no passado.</span><span class="sxs-lookup"><span data-stu-id="40936-329">This problem is often solved by asking new users to create a profile and, for instance, rate movies they have seen in the past.</span></span> <span data-ttu-id="40936-330">Embora esse método seja um fardo para o usuário, ele fornece alguns dados iniciais para novos usuários sem nenhum histórico de classificação.</span><span class="sxs-lookup"><span data-stu-id="40936-330">While this method puts some burden on the user, it provides some starting data for new users with no rating history.</span></span>

## <a name="resources"></a><span data-ttu-id="40936-331">Recursos</span><span class="sxs-lookup"><span data-stu-id="40936-331">Resources</span></span>

<span data-ttu-id="40936-332">Os dados usados neste tutorial foram obtidos do [Conjunto de dados MovieLens](http://files.grouplens.org/datasets/movielens/).</span><span class="sxs-lookup"><span data-stu-id="40936-332">The data used in this tutorial is derived from [MovieLens Dataset](http://files.grouplens.org/datasets/movielens/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="40936-333">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="40936-333">Next steps</span></span>

<span data-ttu-id="40936-334">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="40936-334">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="40936-335">Selecionar um algoritmo de aprendizado de máquina</span><span class="sxs-lookup"><span data-stu-id="40936-335">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="40936-336">Preparar e carregar os dados</span><span class="sxs-lookup"><span data-stu-id="40936-336">Prepare and load your data</span></span>
> * <span data-ttu-id="40936-337">Criar e treinar um modelo</span><span class="sxs-lookup"><span data-stu-id="40936-337">Build and train a model</span></span>
> * <span data-ttu-id="40936-338">Avaliar um modelo</span><span class="sxs-lookup"><span data-stu-id="40936-338">Evaluate a model</span></span>
> * <span data-ttu-id="40936-339">Implantar e consumir um modelo</span><span class="sxs-lookup"><span data-stu-id="40936-339">Deploy and consume a model</span></span>

<span data-ttu-id="40936-340">Avançar para o próximo tutorial para saber mais</span><span class="sxs-lookup"><span data-stu-id="40936-340">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="40936-341">Análise de Sentimento</span><span class="sxs-lookup"><span data-stu-id="40936-341">Sentiment Analysis</span></span>](sentiment-analysis.md)
