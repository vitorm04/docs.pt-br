---
title: 'Tutorial: Categorizar problemas de suporte – classificação multiclasse'
description: Descubra como usar o ML.NET em um cenário de classificação multiclasse para classificar os problemas do GitHub a fim de atribuí-los a uma determinada área.
ms.date: 07/31/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 3bb556cc591ee35fc14c548e7f53bad58a786e99
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710298"
---
# <a name="tutorial-categorize-support-issues-using-multiclass-classification-with-ml-net"></a><span data-ttu-id="3804b-103">Tutorial: Categorizar problemas de suporte usando a classificação multiclasse com ML.NET</span><span class="sxs-lookup"><span data-stu-id="3804b-103">Tutorial: Categorize support issues using multiclass classification with ML .NET</span></span>

<span data-ttu-id="3804b-104">Este tutorial de exemplo ilustra o uso do ML.NET para criar uma classificação de problema do GitHub para treinar um modelo que classifica e prevê o rótulo de área de um problema do GitHub por meio de um aplicativo de console do .NET Core usando C# no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3804b-104">This sample tutorial illustrates using ML.NET to create a GitHub issue classifier to train a model that classifies and predicts the Area label for a GitHub issue via a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="3804b-105">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="3804b-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="3804b-106">Preparar seus dados</span><span class="sxs-lookup"><span data-stu-id="3804b-106">Prepare your data</span></span>
> * <span data-ttu-id="3804b-107">Transformar os dados</span><span class="sxs-lookup"><span data-stu-id="3804b-107">Transform the data</span></span>
> * <span data-ttu-id="3804b-108">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="3804b-108">Train the model</span></span>
> * <span data-ttu-id="3804b-109">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="3804b-109">Evaluate the model</span></span>
> * <span data-ttu-id="3804b-110">Prever com o modelo treinado</span><span class="sxs-lookup"><span data-stu-id="3804b-110">Predict with the trained model</span></span>
> * <span data-ttu-id="3804b-111">Implantar e prever com um modelo carregado</span><span class="sxs-lookup"><span data-stu-id="3804b-111">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="3804b-112">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification).</span><span class="sxs-lookup"><span data-stu-id="3804b-112">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3804b-113">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="3804b-113">Prerequisites</span></span>

* <span data-ttu-id="3804b-114">[Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="3804b-114">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="3804b-115">O [arquivo de problemas do Github separados por tabulação (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span><span class="sxs-lookup"><span data-stu-id="3804b-115">The [Github issues tab separated file (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span></span>
* <span data-ttu-id="3804b-116">O [arquivo de testes de problemas do Github separados por tabulação (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span><span class="sxs-lookup"><span data-stu-id="3804b-116">The [Github issues test tab separated file (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="3804b-117">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="3804b-117">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="3804b-118">Criar um projeto</span><span class="sxs-lookup"><span data-stu-id="3804b-118">Create a project</span></span>

1. <span data-ttu-id="3804b-119">Abra o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="3804b-119">Open Visual Studio 2017.</span></span> <span data-ttu-id="3804b-120">Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="3804b-120">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="3804b-121">Na caixa de diálogo **Novo Projeto**, selecione o nó **Visual C#** seguido pelo nó **.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="3804b-121">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="3804b-122">Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="3804b-122">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="3804b-123">Na caixa de texto **Nome**, digite "GitHubIssueClassification" e selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="3804b-123">In the **Name** text box, type "GitHubIssueClassification" and then select the **OK** button.</span></span>

2. <span data-ttu-id="3804b-124">Crie um diretório chamado *Data* no seu projeto para salvar seus arquivos do conjunto de dados:</span><span class="sxs-lookup"><span data-stu-id="3804b-124">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="3804b-125">No **Gerenciador de Soluções**, clique com o botão direito do mouse no seu projeto e selecione **Adicionar** > **Nova Pasta**.</span><span class="sxs-lookup"><span data-stu-id="3804b-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="3804b-126">Digite "Data" e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="3804b-126">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="3804b-127">Crie um diretório chamado *Modelos* em seu projeto para salvar seu modelo:</span><span class="sxs-lookup"><span data-stu-id="3804b-127">Create a directory named *Models* in your project to save your model:</span></span>

    <span data-ttu-id="3804b-128">No **Gerenciador de Soluções**, clique com o botão direito do mouse no seu projeto e selecione **Adicionar** > **Nova Pasta**.</span><span class="sxs-lookup"><span data-stu-id="3804b-128">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="3804b-129">Digite "Modelos" e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="3804b-129">Type "Models" and hit Enter.</span></span>

4. <span data-ttu-id="3804b-130">Instalar o **Pacote NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="3804b-130">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="3804b-131">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="3804b-131">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="3804b-132">Escolha "nuget.org" como a origem do pacote, selecione a guia Procurar, pesquise **Microsoft.ML**, selecione o pacote **v 1.0.0** na lista e selecione o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="3804b-132">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select the **v 1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="3804b-133">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="3804b-133">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="3804b-134">Preparar seus dados</span><span class="sxs-lookup"><span data-stu-id="3804b-134">Prepare your data</span></span>

1. <span data-ttu-id="3804b-135">Baixe os conjuntos de dados [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) e [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) e salve-os na pasta *Dados* criada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="3804b-135">Download the [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) and the [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="3804b-136">O primeiro conjunto de dados treina o modelo de aprendizado de máquina e o segundo pode ser usado para avaliar a precisão do seu modelo.</span><span class="sxs-lookup"><span data-stu-id="3804b-136">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="3804b-137">No Gerenciador de Soluções, clique com o botão direito do mouse em cada um dos arquivos \*.tsv e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="3804b-137">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="3804b-138">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.</span><span class="sxs-lookup"><span data-stu-id="3804b-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="3804b-139">Criar classes e definir demarcadores</span><span class="sxs-lookup"><span data-stu-id="3804b-139">Create classes and define paths</span></span>

<span data-ttu-id="3804b-140">Adicione as seguintes instruções `using` adicionais ao início do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="3804b-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

<span data-ttu-id="3804b-141">Crie três campos globais para manter os caminhos para os arquivos baixados recentemente e variáveis globais para `MLContext`, `DataView` e `PredictionEngine`:</span><span class="sxs-lookup"><span data-stu-id="3804b-141">Create three global fields to hold the paths to the recently downloaded files, and global variables for the `MLContext`,`DataView`, and `PredictionEngine`:</span></span>

* <span data-ttu-id="3804b-142">`_trainDataPath` tem o demarcador para o conjunto de dados usado para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="3804b-142">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="3804b-143">`_testDataPath` tem o demarcador para o conjunto de dados usado para avaliar o modelo.</span><span class="sxs-lookup"><span data-stu-id="3804b-143">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="3804b-144">`_modelPath` tem o demarcador em que o modelo treinado é salvo.</span><span class="sxs-lookup"><span data-stu-id="3804b-144">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="3804b-145">`_mlContext` é o <xref:Microsoft.ML.MLContext> que fornece o contexto de processamento.</span><span class="sxs-lookup"><span data-stu-id="3804b-145">`_mlContext` is the <xref:Microsoft.ML.MLContext> that provides processing context.</span></span>
* <span data-ttu-id="3804b-146">`_trainingDataView` é o <xref:Microsoft.ML.IDataView> usado para processar o conjunto de dados de treinamento.</span><span class="sxs-lookup"><span data-stu-id="3804b-146">`_trainingDataView` is the <xref:Microsoft.ML.IDataView> used to process the training dataset.</span></span>
* <span data-ttu-id="3804b-147">`_predEngine` é o <xref:Microsoft.ML.PredictionEngine%602> usado para previsões individuais.</span><span class="sxs-lookup"><span data-stu-id="3804b-147">`_predEngine` is the <xref:Microsoft.ML.PredictionEngine%602> used for single predictions.</span></span>

<span data-ttu-id="3804b-148">Adicione o seguinte código à linha logo acima do método `Main` para especificar estes caminhos e as outras variáveis:</span><span class="sxs-lookup"><span data-stu-id="3804b-148">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="3804b-149">Crie algumas classes para os dados de entrada e as previsões.</span><span class="sxs-lookup"><span data-stu-id="3804b-149">Create some classes for your input data and predictions.</span></span> <span data-ttu-id="3804b-150">Adicione uma nova classe ao seu projeto:</span><span class="sxs-lookup"><span data-stu-id="3804b-150">Add a new class to your project:</span></span>

1. <span data-ttu-id="3804b-151">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="3804b-151">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="3804b-152">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *GitHubIssueData.cs*.</span><span class="sxs-lookup"><span data-stu-id="3804b-152">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *GitHubIssueData.cs*.</span></span> <span data-ttu-id="3804b-153">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="3804b-153">Then, select the **Add** button.</span></span>

    <span data-ttu-id="3804b-154">O arquivo *GitHubIssueData.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="3804b-154">The *GitHubIssueData.cs* file opens in the code editor.</span></span> <span data-ttu-id="3804b-155">Adicione a seguinte instrução `using` acima de *GitHubIssueData.cs*:</span><span class="sxs-lookup"><span data-stu-id="3804b-155">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

<span data-ttu-id="3804b-156">Remova a definição de classe existente e adicione o seguinte código, que tem duas classes, `GitHubIssue` e `IssuePrediction`, ao arquivo *GitHubIssueData.cs*:</span><span class="sxs-lookup"><span data-stu-id="3804b-156">Remove the existing class definition and add the following code, which has two classes `GitHubIssue` and `IssuePrediction`, to the *GitHubIssueData.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

<span data-ttu-id="3804b-157">O `label` é a coluna que você deseja prever.</span><span class="sxs-lookup"><span data-stu-id="3804b-157">The `label` is the column you want to predict.</span></span> <span data-ttu-id="3804b-158">O `Features` identificado são as entradas que você atribui ao modelo para prever o rótulo.</span><span class="sxs-lookup"><span data-stu-id="3804b-158">The identified `Features` are the inputs you give the model to predict the Label.</span></span>

<span data-ttu-id="3804b-159">Use o atributo [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) para especificar os índices das colunas de origem no conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="3804b-159">Use the [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="3804b-160">`GitHubIssue` é a classe de conjunto de dados de entrada e tem os seguintes campos <xref:System.String>:</span><span class="sxs-lookup"><span data-stu-id="3804b-160">`GitHubIssue` is the input dataset class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="3804b-161">a primeira coluna `ID` (ID de problema do GitHub)</span><span class="sxs-lookup"><span data-stu-id="3804b-161">the first column `ID` (GitHub Issue ID)</span></span>
* <span data-ttu-id="3804b-162">a segunda coluna `Area` (a previsão do treinamento)</span><span class="sxs-lookup"><span data-stu-id="3804b-162">the second column `Area` (the prediction for training)</span></span>
* <span data-ttu-id="3804b-163">a terceira coluna `Title` (título do problema de GitHub) é o primeiro `feature` usado para prever o `Area`</span><span class="sxs-lookup"><span data-stu-id="3804b-163">the third column `Title` (GitHub issue title) is the first `feature` used for predicting the `Area`</span></span>
* <span data-ttu-id="3804b-164">a quarta coluna `Description` é o segundo `feature` usado para prever o `Area`</span><span class="sxs-lookup"><span data-stu-id="3804b-164">the fourth column  `Description` is the second `feature` used for predicting the `Area`</span></span>

<span data-ttu-id="3804b-165">`IssuePrediction` é a classe usada para previsão depois que o modelo foi treinado.</span><span class="sxs-lookup"><span data-stu-id="3804b-165">`IssuePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="3804b-166">Tem um único `string` (`Area`) e um atributo `PredictedLabel` `ColumnName`.</span><span class="sxs-lookup"><span data-stu-id="3804b-166">It has a single `string` (`Area`) and a `PredictedLabel` `ColumnName` attribute.</span></span>  <span data-ttu-id="3804b-167">O `PredictedLabel` é usado durante a previsão e avaliação.</span><span class="sxs-lookup"><span data-stu-id="3804b-167">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="3804b-168">Para avaliação, uma entrada com dados de treinamento, os valores previstos e o modelo são usados.</span><span class="sxs-lookup"><span data-stu-id="3804b-168">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="3804b-169">Todas as operações do ML.NET iniciam na classe [MLContext](xref:Microsoft.ML.MLContext).</span><span class="sxs-lookup"><span data-stu-id="3804b-169">All ML.NET operations start in the [MLContext](xref:Microsoft.ML.MLContext) class.</span></span> <span data-ttu-id="3804b-170">Inicializar `mlContext` cria um novo ambiente do ML.NET que pode ser compartilhado entre os objetos do fluxo de trabalho de criação de modelo.</span><span class="sxs-lookup"><span data-stu-id="3804b-170">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="3804b-171">É similar, conceitualmente, a `DBContext` em `Entity Framework`.</span><span class="sxs-lookup"><span data-stu-id="3804b-171">It's similar, conceptually, to `DBContext` in `Entity Framework`.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="3804b-172">Inicializar variáveis em Main</span><span class="sxs-lookup"><span data-stu-id="3804b-172">Initialize variables in Main</span></span>

<span data-ttu-id="3804b-173">Inicialize a variável global `_mlContext` com uma nova instância de `MLContext` com uma semente aleatória (`seed: 0`) para obter resultados repetíveis/determinísticos entre vários treinamentos.</span><span class="sxs-lookup"><span data-stu-id="3804b-173">Initialize the `_mlContext` global variable  with a new instance of `MLContext` with a random seed (`seed: 0`) for repeatable/deterministic results across multiple trainings.</span></span>  <span data-ttu-id="3804b-174">Substitua a linha `Console.WriteLine("Hello World!")` pelo seguinte código no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="3804b-174">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a><span data-ttu-id="3804b-175">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="3804b-175">Load the data</span></span>

<span data-ttu-id="3804b-176">O ML.NET usa a [classe IDataView](xref:Microsoft.ML.IDataView) como uma maneira flexível e eficiente de descrever dados tabulares de texto ou numéricos.</span><span class="sxs-lookup"><span data-stu-id="3804b-176">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="3804b-177">O `IDataView` pode carregar arquivos de texto ou em tempo real (por exemplo, banco de dados SQL ou arquivos de log).</span><span class="sxs-lookup"><span data-stu-id="3804b-177">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span>

<span data-ttu-id="3804b-178">Para inicializar e carregar a variável global `_trainingDataView` para utilizá-la para o pipeline, adicione o seguinte código após a inicialização de `mlContext`:</span><span class="sxs-lookup"><span data-stu-id="3804b-178">To initialize and load the `_trainingDataView` global variable in order to use it for the pipeline, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]

<span data-ttu-id="3804b-179">O [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) define o esquema de dados e lê o arquivo.</span><span class="sxs-lookup"><span data-stu-id="3804b-179">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="3804b-180">Ele usa as variáveis de caminho de dados e retorna uma `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="3804b-180">It takes in the data path variables and returns an `IDataView`.</span></span>

<span data-ttu-id="3804b-181">Adicione o seguinte como a linha seguinte de código no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="3804b-181">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallProcessData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

<span data-ttu-id="3804b-182">O método `ProcessData` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="3804b-182">The `ProcessData` method executes the following tasks:</span></span>

* <span data-ttu-id="3804b-183">Extrai e transforma os dados.</span><span class="sxs-lookup"><span data-stu-id="3804b-183">Extracts and transforms the data.</span></span>
* <span data-ttu-id="3804b-184">Retorna o pipeline de processamento.</span><span class="sxs-lookup"><span data-stu-id="3804b-184">Returns the processing pipeline.</span></span>

<span data-ttu-id="3804b-185">Crie o método `ProcessData`, logo após o método `Main`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="3804b-185">Create the `ProcessData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="3804b-186">Extrair recursos e transformar os dados</span><span class="sxs-lookup"><span data-stu-id="3804b-186">Extract Features and transform the data</span></span>

<span data-ttu-id="3804b-187">Uma vez que você deseja prever o rótulo do GitHub de Área de um `GitHubIssue`, use o método [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) para transformar a coluna `Area` em um tipo de chave numérica `Label` (um formato aceito pelos algoritmos de classificação da coluna) e adicione-o como uma nova coluna de conjunto de dados:</span><span class="sxs-lookup"><span data-stu-id="3804b-187">As you want to predict the Area GitHub label for a `GitHubIssue`, use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform the `Area` column into a numeric key type `Label` column (a format accepted by classification algorithms) and add it as a new dataset column:</span></span>

[!code-csharp[MapValueToKey](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

<span data-ttu-id="3804b-188">Em seguida, chame `mlContext.Transforms.Text.FeaturizeText` que transforma as colunas do texto (`Title` e `Description`) em um vetor numérico para cada `TitleFeaturized` e `DescriptionFeaturized` chamado.</span><span class="sxs-lookup"><span data-stu-id="3804b-188">Next, call `mlContext.Transforms.Text.FeaturizeText` which transforms the text (`Title` and `Description`) columns into a numeric vector for each called `TitleFeaturized` and `DescriptionFeaturized`.</span></span> <span data-ttu-id="3804b-189">Acrescente a personalização para ambas as colunas ao pipeline com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="3804b-189">Append the featurization for both columns to the pipeline with the following code:</span></span>

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

<span data-ttu-id="3804b-190">A última etapa na preparação de dados combina todas as colunas de recursos na coluna **Recursos** usando o método [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A).</span><span class="sxs-lookup"><span data-stu-id="3804b-190">The last step in data preparation combines all of the feature columns into the **Features** column using the [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) method.</span></span> <span data-ttu-id="3804b-191">Por padrão, um algoritmo de aprendizado processa apenas os recursos da coluna **Features**.</span><span class="sxs-lookup"><span data-stu-id="3804b-191">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="3804b-192">Acrescente esta transformação ao pipeline com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="3804b-192">Append this transformation to the pipeline with the following code:</span></span>

[!code-csharp[Concatenate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 <span data-ttu-id="3804b-193">Em seguida, acrescente um <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> para armazenar a DataView em cache, para melhorar o desempenho ao iterar nos dados várias vezes usando o cache, como no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="3804b-193">Next, append a <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> to cache the DataView so when you iterate over the data multiple times using the cache might get better performance, as with the following code:</span></span>

[!code-csharp[AppendCache](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

> [!WARNING]
> <span data-ttu-id="3804b-194">Use AppendCacheCheckpoint para conjuntos de dados pequenos/médios a fim de reduzir o tempo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="3804b-194">Use AppendCacheCheckpoint for small/medium datasets to lower training time.</span></span> <span data-ttu-id="3804b-195">NÃO o utilize (remova .AppendCacheCheckpoint()) ao lidar com conjuntos de dados grandes.</span><span class="sxs-lookup"><span data-stu-id="3804b-195">Do NOT use it (remove .AppendCacheCheckpoint()) when handling very large datasets.</span></span>

<span data-ttu-id="3804b-196">Retorne o pipeline no final do método `ProcessData`.</span><span class="sxs-lookup"><span data-stu-id="3804b-196">Return the pipeline at the end of the `ProcessData` method.</span></span>

[!code-csharp[ReturnPipeline](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

<span data-ttu-id="3804b-197">Esta etapa manipula o pré-processamento/personalização.</span><span class="sxs-lookup"><span data-stu-id="3804b-197">This step handles preprocessing/featurization.</span></span> <span data-ttu-id="3804b-198">Usar componentes adicionais disponíveis no ML.NET pode permitir melhores resultados com o seu modelo.</span><span class="sxs-lookup"><span data-stu-id="3804b-198">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="build-and-train-the-model"></a><span data-ttu-id="3804b-199">Criar e treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="3804b-199">Build and train the model</span></span>

<span data-ttu-id="3804b-200">Adicione a seguinte chamada ao método `BuildAndTrainModel` como a próxima linha de código no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="3804b-200">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="3804b-201">O método `BuildAndTrainModel` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="3804b-201">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="3804b-202">Cria a classe de algoritmo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="3804b-202">Creates the training algorithm class.</span></span>
* <span data-ttu-id="3804b-203">Treina o modelo.</span><span class="sxs-lookup"><span data-stu-id="3804b-203">Trains the model.</span></span>
* <span data-ttu-id="3804b-204">Prevê a área com base em dados de treinamento.</span><span class="sxs-lookup"><span data-stu-id="3804b-204">Predicts area based on training data.</span></span>
* <span data-ttu-id="3804b-205">Retorna o modelo.</span><span class="sxs-lookup"><span data-stu-id="3804b-205">Returns the model.</span></span>

<span data-ttu-id="3804b-206">Crie o método `BuildAndTrainModel`, logo após o método `Main`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="3804b-206">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a><span data-ttu-id="3804b-207">Sobre a tarefa de classificação</span><span class="sxs-lookup"><span data-stu-id="3804b-207">About the classification task</span></span>

<span data-ttu-id="3804b-208">A classificação é uma tarefa de aprendizado de máquina que usa dados para **determinar** a categoria, o tipo ou a classe de um item ou linha de dados e costuma ser de um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="3804b-208">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data and is frequently one of the following types:</span></span>

* <span data-ttu-id="3804b-209">Binário: A ou B.</span><span class="sxs-lookup"><span data-stu-id="3804b-209">Binary: either A or B.</span></span>
* <span data-ttu-id="3804b-210">Multiclasse: várias categorias que podem ser previstas usando um único modelo.</span><span class="sxs-lookup"><span data-stu-id="3804b-210">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="3804b-211">Para esse tipo de problema, use um algoritmo de aprendizado de classificação Multiclasse, pois a previsão de categoria do problema pode ser uma das várias categorias (multiclasse), em vez de apenas duas (binária).</span><span class="sxs-lookup"><span data-stu-id="3804b-211">For this type of problem, use a Multiclass classification learning algorithm, since your issue category prediction can be one of multiple categories (multiclass) rather than just two (binary).</span></span>

<span data-ttu-id="3804b-212">Acrescente o algoritmo de aprendizado de máquina às definições de transformação de dados adicionando o seguinte como a primeira linha de código em `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="3804b-212">Append the machine learning algorithm to the data transformation definitions by adding the following as the first line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddTrainer](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

<span data-ttu-id="3804b-213">O [SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) é seu algoritmo de treinamento de classificação multiclasse.</span><span class="sxs-lookup"><span data-stu-id="3804b-213">The [SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) is your multiclass classification training algorithm.</span></span> <span data-ttu-id="3804b-214">Isso é anexado ao `pipeline` e aceita os `Title` e `Description` (`Features`) personalizados e os parâmetro de entrada `Label` para aprender com os dados históricos.</span><span class="sxs-lookup"><span data-stu-id="3804b-214">This is appended to the `pipeline` and accepts the featurized `Title` and `Description` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="3804b-215">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="3804b-215">Train the model</span></span>

<span data-ttu-id="3804b-216">Ajuste o modelo aos dados `splitTrainSet` e retorne o modelo treinado adicionando o seguinte como a próxima linha de código no método `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="3804b-216">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

<span data-ttu-id="3804b-217">O método `Fit()` treina o modelo transformando o conjunto de dados e aplicando o treinamento.</span><span class="sxs-lookup"><span data-stu-id="3804b-217">The `Fit()`method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="3804b-218">O [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) é uma API de conveniência, que permite passar uma única instância de dados e, em seguida, executar uma previsão nessa única instância de dados.</span><span class="sxs-lookup"><span data-stu-id="3804b-218">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span> <span data-ttu-id="3804b-219">Adicione isso como a próxima linha no método `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="3804b-219">Add this as the next line in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[CreatePredictionEngine1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a><span data-ttu-id="3804b-220">Prever com o modelo treinado</span><span class="sxs-lookup"><span data-stu-id="3804b-220">Predict with the trained model</span></span>

<span data-ttu-id="3804b-221">Adicione um problema do GitHub para testar a previsão do modelo treinado no método `Predict` ao criar uma instância de `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="3804b-221">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[CreateTestIssue1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

<span data-ttu-id="3804b-222">Use a função [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) faz uma previsão em uma única coluna de dados:</span><span class="sxs-lookup"><span data-stu-id="3804b-222">Use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a><span data-ttu-id="3804b-223">Usando o modelo: resultados de previsão</span><span class="sxs-lookup"><span data-stu-id="3804b-223">Using the model: prediction results</span></span>

<span data-ttu-id="3804b-224">Exiba `GitHubIssue` e a previsão de rótulo `Area` correspondente para compartilhar os resultados e agir de acordo com eles.</span><span class="sxs-lookup"><span data-stu-id="3804b-224">Display `GitHubIssue` and corresponding `Area` label prediction in order to share the results and act on them accordingly.</span></span>  <span data-ttu-id="3804b-225">Crie uma exibição para os resultados usando o seguinte código <xref:System.Console.WriteLine?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="3804b-225">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="3804b-226">Retornar o modelo treinado a ser usado para avaliação</span><span class="sxs-lookup"><span data-stu-id="3804b-226">Return the model trained to use for evaluation</span></span>

<span data-ttu-id="3804b-227">Retorne o modelo no final do método `BuildAndTrainModel`.</span><span class="sxs-lookup"><span data-stu-id="3804b-227">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a><span data-ttu-id="3804b-228">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="3804b-228">Evaluate the model</span></span>

<span data-ttu-id="3804b-229">Agora que você criou e treinou o modelo, precisa avaliá-lo com um conjunto de dados diferente para garantia de qualidade e validação.</span><span class="sxs-lookup"><span data-stu-id="3804b-229">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="3804b-230">No método `Evaluate`, o modelo criado em `BuildAndTrainModel` é passado para ser avaliado.</span><span class="sxs-lookup"><span data-stu-id="3804b-230">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="3804b-231">Crie o método `Evaluate` , logo após `BuildAndTrainModel`, como no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="3804b-231">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate(DataViewSchema trainingDataViewSchema)
{

}
```

<span data-ttu-id="3804b-232">O método `Evaluate` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="3804b-232">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="3804b-233">Carrega o conjunto de dados de teste.</span><span class="sxs-lookup"><span data-stu-id="3804b-233">Loads the test dataset.</span></span>
* <span data-ttu-id="3804b-234">Cria o avaliador multiclasse.</span><span class="sxs-lookup"><span data-stu-id="3804b-234">Creates the multiclass evaluator.</span></span>
* <span data-ttu-id="3804b-235">Avalia o modelo e cria métricas.</span><span class="sxs-lookup"><span data-stu-id="3804b-235">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="3804b-236">Exibe as métricas.</span><span class="sxs-lookup"><span data-stu-id="3804b-236">Displays the metrics.</span></span>

<span data-ttu-id="3804b-237">Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `BuildAndTrainModel`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="3804b-237">Add a call to the new method from the `Main` method, right under the `BuildAndTrainModel` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

<span data-ttu-id="3804b-238">Como você fez anteriormente com o conjunto de dados de treinamento, carregue o conjunto de dados de teste adicionando o seguinte código ao método `Evaluate`:</span><span class="sxs-lookup"><span data-stu-id="3804b-238">As you did previously with the training dataset, load the test dataset by adding the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

<span data-ttu-id="3804b-239">O método [Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) calcula as métricas de qualidade para o modelo usando o conjunto de dados especificado.</span><span class="sxs-lookup"><span data-stu-id="3804b-239">The [Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) method computes the quality metrics for the model using the specified dataset.</span></span> <span data-ttu-id="3804b-240">Ele retorna um objeto <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> que contém as métricas gerais calculadas pelos avaliadores de classificação multiclasse.</span><span class="sxs-lookup"><span data-stu-id="3804b-240">It returns a <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> object that contains the overall metrics computed by multiclass classification evaluators.</span></span>
<span data-ttu-id="3804b-241">Para exibir as métricas para determinar a qualidade do modelo, você precisará obtê-las primeiro.</span><span class="sxs-lookup"><span data-stu-id="3804b-241">To display the metrics to determine the quality of the model, you need to get them first.</span></span>
<span data-ttu-id="3804b-242">Observe o uso do método [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) da variável global `_trainedModel` de aprendizado de máquina (um [Transformador](xref:Microsoft.ML.ITransformer)) para inserir os recursos e retornar previsões.</span><span class="sxs-lookup"><span data-stu-id="3804b-242">Notice the use of the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method of the machine learning `_trainedModel` global variable (an [ITransformer](xref:Microsoft.ML.ITransformer)) to input the features and return predictions.</span></span> <span data-ttu-id="3804b-243">Adicione o seguinte código ao método `Evaluate` como a linha seguinte:</span><span class="sxs-lookup"><span data-stu-id="3804b-243">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

<span data-ttu-id="3804b-244">As métricas a seguir são avaliadas para classificação multiclasse:</span><span class="sxs-lookup"><span data-stu-id="3804b-244">The following metrics are evaluated for multiclass classification:</span></span>

* <span data-ttu-id="3804b-245">Microprecisão – todo par de classe/exemplo contribui igualmente para a métrica de precisão.</span><span class="sxs-lookup"><span data-stu-id="3804b-245">Micro Accuracy - Every sample-class pair contributes equally to the accuracy metric.</span></span>  <span data-ttu-id="3804b-246">Convém que a Microprecisão seja tão próxima de 1 quanto possível.</span><span class="sxs-lookup"><span data-stu-id="3804b-246">You want Micro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="3804b-247">Macroprecisão – toda classe contribui igualmente para a métrica de precisão.</span><span class="sxs-lookup"><span data-stu-id="3804b-247">Macro Accuracy - Every class contributes equally to the accuracy metric.</span></span> <span data-ttu-id="3804b-248">Classes minoritárias recebem o mesmo peso que as classes maiores.</span><span class="sxs-lookup"><span data-stu-id="3804b-248">Minority classes are given equal weight as the larger classes.</span></span> <span data-ttu-id="3804b-249">Convém que a Macroprecisão seja tão próxima de 1 quanto possível.</span><span class="sxs-lookup"><span data-stu-id="3804b-249">You want Macro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="3804b-250">Perda de log – consulte [Perda de log](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="3804b-250">Log-loss - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="3804b-251">Convém que a Perda de log seja tão próxima de zero quanto possível.</span><span class="sxs-lookup"><span data-stu-id="3804b-251">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="3804b-252">Redução de perda de log – varia de [-inf, 100], em que 100 é composto pelas previsões perfeitas e 0 indica previsões de média.</span><span class="sxs-lookup"><span data-stu-id="3804b-252">Log-loss reduction - Ranges from [-inf, 100], where 100 is perfect predictions and 0 indicates mean predictions.</span></span> <span data-ttu-id="3804b-253">Convém que a redução de perda de log seja tão próxima de zero quanto possível.</span><span class="sxs-lookup"><span data-stu-id="3804b-253">You want Log-loss reduction to be as close to zero as possible.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="3804b-254">Exibir as métricas para validação de modelo</span><span class="sxs-lookup"><span data-stu-id="3804b-254">Displaying the metrics for model validation</span></span>

<span data-ttu-id="3804b-255">Use o código a seguir para exibir as métricas, compartilhar os resultados e, em seguida, agir com relação a eles:</span><span class="sxs-lookup"><span data-stu-id="3804b-255">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

### <a name="save-the-model-to-a-file"></a><span data-ttu-id="3804b-256">Salvar o modelo em um arquivo</span><span class="sxs-lookup"><span data-stu-id="3804b-256">Save the model to a file</span></span>

<span data-ttu-id="3804b-257">Quando estiver satisfeito com seu modelo, salve-o em um arquivo para fazer previsões posteriormente ou em outro aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3804b-257">Once satisfied with your model, save it to a file to make predictions at a later time or in another application.</span></span> <span data-ttu-id="3804b-258">Adicione o seguinte código ao método de `Evaluate` .</span><span class="sxs-lookup"><span data-stu-id="3804b-258">Add the following code to the `Evaluate` method.</span></span> 

[!code-csharp[SnippetCallSaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SnippetCallSaveModel)]

<span data-ttu-id="3804b-259">Crie o método `SaveModelAsFile` abaixo de seu método `Evaluate`.</span><span class="sxs-lookup"><span data-stu-id="3804b-259">Create the `SaveModelAsFile` method below your `Evaluate` method.</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext,DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

<span data-ttu-id="3804b-260">Adicione o código a seguir ao método `SaveModelAsFile`.</span><span class="sxs-lookup"><span data-stu-id="3804b-260">Add the following code to your `SaveModelAsFile` method.</span></span> <span data-ttu-id="3804b-261">Esse código usa o método [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) para serializar e armazenar o modelo treinado como um arquivo zip.</span><span class="sxs-lookup"><span data-stu-id="3804b-261">This code uses the [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) method to serialize and store the trained model as a zip file.</span></span>

[!code-csharp[SnippetSaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SnippetSaveModel)]

## <a name="deploy-and-predict-with-a-model"></a><span data-ttu-id="3804b-262">Implantar e prever com um modelo</span><span class="sxs-lookup"><span data-stu-id="3804b-262">Deploy and Predict with a model</span></span>

<span data-ttu-id="3804b-263">Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `Evaluate`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="3804b-263">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

<span data-ttu-id="3804b-264">Crie o método `PredictIssue` logo após o método `Evaluate` (e antes do método `SaveModelAsFile`) usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="3804b-264">Create the `PredictIssue` method, just after the `Evaluate` method (and just before the `SaveModelAsFile` method), using the following code:</span></span>

```csharp
private static void PredictIssue()
{

}
```

<span data-ttu-id="3804b-265">O método `PredictIssue` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="3804b-265">The `PredictIssue` method executes the following tasks:</span></span>

* <span data-ttu-id="3804b-266">Carrega o modelo salvo</span><span class="sxs-lookup"><span data-stu-id="3804b-266">Loads the saved model</span></span>
* <span data-ttu-id="3804b-267">Cria um único problema dos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="3804b-267">Creates a single issue of test data.</span></span>
* <span data-ttu-id="3804b-268">Prevê a área com base em dados de teste.</span><span class="sxs-lookup"><span data-stu-id="3804b-268">Predicts Area based on test data.</span></span>
* <span data-ttu-id="3804b-269">Combina dados de teste e previsões para relatórios.</span><span class="sxs-lookup"><span data-stu-id="3804b-269">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="3804b-270">Exibe os resultados previstos.</span><span class="sxs-lookup"><span data-stu-id="3804b-270">Displays the predicted results.</span></span>

<span data-ttu-id="3804b-271">Carregue o modelo salvo em seu aplicativo adicionando o seguinte código ao método `PredictIssue`:</span><span class="sxs-lookup"><span data-stu-id="3804b-271">Load the saved model into your application by adding the following code to the `PredictIssue` method:</span></span>

[!code-csharp[SnippetLoadModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SnippetLoadModel)]

<span data-ttu-id="3804b-272">Adicione um problema do GitHub para testar a previsão do modelo treinado no método `Predict` ao criar uma instância de `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="3804b-272">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[AddTestIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

<span data-ttu-id="3804b-273">Como você fez anteriormente, crie uma instância de `PredictionEngine` com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="3804b-273">As you did previously, create a `PredictionEngine` instance with the following code:</span></span>

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]
  
<span data-ttu-id="3804b-274">Use o `PredictionEngine` para prever o rótulo do GitHub de Área adicionando o seguinte código ao método `PredictIssue` para a previsão:</span><span class="sxs-lookup"><span data-stu-id="3804b-274">Use the `PredictionEngine` to predict the Area GitHub label by adding the following code to the `PredictIssue` method for the prediction:</span></span>

[!code-csharp[PredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a><span data-ttu-id="3804b-275">Usando o modelo carregado para previsão</span><span class="sxs-lookup"><span data-stu-id="3804b-275">Using the loaded model for prediction</span></span>

<span data-ttu-id="3804b-276">Exiba `Area` para categorizar o problema e agir adequadamente para solucioná-lo.</span><span class="sxs-lookup"><span data-stu-id="3804b-276">Display `Area` in order to categorize the issue and act on it accordingly.</span></span> <span data-ttu-id="3804b-277">Crie uma exibição para os resultados usando o seguinte código <xref:System.Console.WriteLine?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="3804b-277">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayResults](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a><span data-ttu-id="3804b-278">Resultados</span><span class="sxs-lookup"><span data-stu-id="3804b-278">Results</span></span>

<span data-ttu-id="3804b-279">Seus resultados devem ser semelhantes aos seguintes.</span><span class="sxs-lookup"><span data-stu-id="3804b-279">Your results should be similar to the following.</span></span> <span data-ttu-id="3804b-280">Conforme o pipeline processa, exibe mensagens.</span><span class="sxs-lookup"><span data-stu-id="3804b-280">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="3804b-281">Você pode ver avisos ou mensagens de processamento.</span><span class="sxs-lookup"><span data-stu-id="3804b-281">You may see warnings, or processing messages.</span></span> <span data-ttu-id="3804b-282">Essas mensagens foram removidas dos resultados a seguir para ficar mais claro.</span><span class="sxs-lookup"><span data-stu-id="3804b-282">These messages have been removed from the following results for clarity.</span></span>

```console
=============== Single Prediction just-trained-model - Result: area-System.Net ===============
*************************************************************************************************************
*       Metrics for Multi-class Classification model - Test Data
*------------------------------------------------------------------------------------------------------------
*       MicroAccuracy:    0.738
*       MacroAccuracy:    0.668
*       LogLoss:          .919
*       LogLossReduction: .643
*************************************************************************************************************
=============== Single Prediction - Result: area-System.Data ===============
```

<span data-ttu-id="3804b-283">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="3804b-283">Congratulations!</span></span> <span data-ttu-id="3804b-284">Agora você criou com sucesso um modelo de machine learning para classificar e prever um rótulo de Área para um problema do GitHub.</span><span class="sxs-lookup"><span data-stu-id="3804b-284">You've now successfully built a machine learning model for classifying and predicting an Area label for a GitHub issue.</span></span> <span data-ttu-id="3804b-285">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification).</span><span class="sxs-lookup"><span data-stu-id="3804b-285">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3804b-286">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="3804b-286">Next steps</span></span>

<span data-ttu-id="3804b-287">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="3804b-287">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="3804b-288">Preparar seus dados</span><span class="sxs-lookup"><span data-stu-id="3804b-288">Prepare your data</span></span>
> * <span data-ttu-id="3804b-289">Transformar os dados</span><span class="sxs-lookup"><span data-stu-id="3804b-289">Transform the data</span></span>
> * <span data-ttu-id="3804b-290">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="3804b-290">Train the model</span></span>
> * <span data-ttu-id="3804b-291">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="3804b-291">Evaluate the model</span></span>
> * <span data-ttu-id="3804b-292">Prever com o modelo treinado</span><span class="sxs-lookup"><span data-stu-id="3804b-292">Predict with the trained model</span></span>
> * <span data-ttu-id="3804b-293">Implantar e prever com um modelo carregado</span><span class="sxs-lookup"><span data-stu-id="3804b-293">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="3804b-294">Avançar para o próximo tutorial para saber mais</span><span class="sxs-lookup"><span data-stu-id="3804b-294">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="3804b-295">Previsão do valor da corrida do táxi</span><span class="sxs-lookup"><span data-stu-id="3804b-295">Taxi Fare Predictor</span></span>](taxi-fare.md)
