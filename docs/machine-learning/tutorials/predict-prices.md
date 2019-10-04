---
title: 'Tutorial: Prever os preços usando regressão'
description: Este tutorial mostra como criar um modelo de regressão usando do ML.NET para prever os preços, especificamente, as tarifas de táxi de Nova York.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc, seodec18, title-hack-0516
ms.openlocfilehash: 51617d14e84fa46464d7b44dbdb20afaf196924f
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71957380"
---
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a><span data-ttu-id="d4fd6-103">Tutorial: Prever os preços usando regressão com ML.NET</span><span class="sxs-lookup"><span data-stu-id="d4fd6-103">Tutorial: Predict prices using regression with ML.NET</span></span>

<span data-ttu-id="d4fd6-104">Este tutorial mostra como criar um [modelo de regressão](../resources/glossary.md#regression) usando do ML.NET para prever os preços, especificamente, as tarifas de táxi de Nova York.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-104">This tutorial illustrates how to build a [regression model](../resources/glossary.md#regression) using ML.NET to predict prices, specifically, New York City taxi fares.</span></span>

<span data-ttu-id="d4fd6-105">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="d4fd6-106">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="d4fd6-106">Prepare and understand the data</span></span>
> * <span data-ttu-id="d4fd6-107">Carregar e transformar os dados</span><span class="sxs-lookup"><span data-stu-id="d4fd6-107">Load and transform the data</span></span>
> * <span data-ttu-id="d4fd6-108">Escolher um algoritmo de aprendizado</span><span class="sxs-lookup"><span data-stu-id="d4fd6-108">Choose a learning algorithm</span></span>
> * <span data-ttu-id="d4fd6-109">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="d4fd6-109">Train the model</span></span>
> * <span data-ttu-id="d4fd6-110">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="d4fd6-110">Evaluate the model</span></span>
> * <span data-ttu-id="d4fd6-111">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="d4fd6-111">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d4fd6-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d4fd6-112">Prerequisites</span></span>

* <span data-ttu-id="d4fd6-113">[Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-113">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="d4fd6-114">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="d4fd6-114">Create a console application</span></span>

1. <span data-ttu-id="d4fd6-115">Crie um **Aplicativo de Console do .NET Core** chamado "TaxiFarePrediction".</span><span class="sxs-lookup"><span data-stu-id="d4fd6-115">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

1. <span data-ttu-id="d4fd6-116">Crie um diretório chamado *Dados* em seu projeto para armazenar o conjunto de dados e arquivos de modelo.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-116">Create a directory named *Data* in your project to store the data set and model files.</span></span>

1. <span data-ttu-id="d4fd6-117">Instale o pacote NuGet **Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-117">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="d4fd6-118">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-118">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="d4fd6-119">Escolha "nuget.org" como a origem do pacote, selecione a guia **Procurar**, pesquise por **Microsoft.ML**, selecione o pacote na lista e selecione o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-119">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="d4fd6-120">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-120">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="d4fd6-121">Faça o mesmo para o pacote do NuGet **Microsoft.ML.FastTree**.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-121">Do the same for the **Microsoft.ML.FastTree** Nuget package.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="d4fd6-122">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="d4fd6-122">Prepare and understand the data</span></span>

1. <span data-ttu-id="d4fd6-123">Baixe os conjuntos de dados [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) e [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) e salve-os na pasta *Dados* criada na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-123">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="d4fd6-124">Esses conjuntos de dados são usados para treinar o modelo de aprendizado de máquina e, em seguida, avaliar a precisão dele.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-124">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="d4fd6-125">Esses conjuntos de dados são originalmente do [Conjunto de dados NYC TLC Taxi Trip](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="d4fd6-125">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

1. <span data-ttu-id="d4fd6-126">No **Gerenciador de Soluções**, clique com o botão direito do mouse em cada um dos arquivos \*.csv e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-126">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="d4fd6-127">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-127">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

1. <span data-ttu-id="d4fd6-128">Abra o conjunto de dados **taxi-fare-train.csv** e observe os cabeçalhos de coluna na primeira linha.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-128">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="d4fd6-129">Dê uma olhada em cada uma das colunas.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-129">Take a look at each of the columns.</span></span> <span data-ttu-id="d4fd6-130">Compreenda os dados e decida quais colunas são **recursos** e qual é o **rótulo**.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-130">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="d4fd6-131">O `label` é a coluna que você deseja prever.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-131">The `label` is the column you want to predict.</span></span> <span data-ttu-id="d4fd6-132">O `Features`identificado são as entradas que você atribui ao modelo para prever o `Label`.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-132">The identified `Features`are the inputs you give the model to predict the `Label`.</span></span>

<span data-ttu-id="d4fd6-133">O conjunto de dados fornecido contém as seguintes colunas:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-133">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="d4fd6-134">**vendor_id:** A ID do taxista é um recurso.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-134">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="d4fd6-135">**rate_code:** O tipo de tarifa da corrida de táxi é um recurso.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-135">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="d4fd6-136">**passenger_count:** O número de passageiros na corrida é um recurso.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-136">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="d4fd6-137">**trip_time_in_secs:** O tempo que levou a corrida.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-137">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="d4fd6-138">Você deseja prever a tarifa da viagem antes de sua conclusão.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-138">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="d4fd6-139">No momento, você não sabe a duração da viagem.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-139">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="d4fd6-140">Portanto, o tempo da viagem não é um recurso e você excluirá essa coluna do modelo.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-140">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="d4fd6-141">**trip_distance:** A distância da corrida é um recurso.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-141">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="d4fd6-142">**payment_type:** A forma de pagamento (dinheiro ou cartão de crédito) é um recurso.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-142">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="d4fd6-143">**fare_amount:** A tarifa total de táxi paga é o rótulo.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-143">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="d4fd6-144">Criar classes de dados</span><span class="sxs-lookup"><span data-stu-id="d4fd6-144">Create data classes</span></span>

<span data-ttu-id="d4fd6-145">Crie classes para os dados de entrada e as previsões:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-145">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="d4fd6-146">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-146">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="d4fd6-147">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="d4fd6-148">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-148">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="d4fd6-149">Adicione as seguintes diretivas `using` ao novo arquivo:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-149">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="d4fd6-150">Remova a definição de classe existente e adicione o seguinte código, que tem duas classes `TaxiTrip` e `TaxiTripFarePrediction`, ao arquivo *TaxiTrip.cs*:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-150">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="d4fd6-151">`TaxiTrip` é a classe de dados de entrada e tem definições para cada uma das colunas do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-151">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="d4fd6-152">Use o atributo <xref:Microsoft.ML.Data.LoadColumnAttribute> para especificar os índices das colunas de origem no conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-152">Use the <xref:Microsoft.ML.Data.LoadColumnAttribute> attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="d4fd6-153">A classe `TaxiTripFarePrediction` representa os resultados previstos.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-153">The `TaxiTripFarePrediction` class represents predicted results.</span></span> <span data-ttu-id="d4fd6-154">Ela tem um único campo de float, `FareAmount`, com um atributo `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> aplicado.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-154">It has a single float field, `FareAmount`, with a `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> attribute applied.</span></span> <span data-ttu-id="d4fd6-155">No caso da tarefa de regressão, a coluna **Pontuação** contém valores de rótulo previsto.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-155">In case of the regression task the **Score** column contains predicted label values.</span></span>

> [!NOTE]
> <span data-ttu-id="d4fd6-156">Use o tipo `float` para representar valores de ponto flutuante nas classes de dados de entrada e previsão.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-156">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

### <a name="define-data-and-model-paths"></a><span data-ttu-id="d4fd6-157">Definir dados e caminhos de modelo</span><span class="sxs-lookup"><span data-stu-id="d4fd6-157">Define data and model paths</span></span>

<span data-ttu-id="d4fd6-158">Adicione as seguintes instruções `using` adicionais ao início do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-158">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="d4fd6-159">Você precisa criar três campos para conter os caminhos para os arquivos com conjuntos de dados e o arquivo para salvar o modelo:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-159">You need to create three fields to hold the paths to the files with data sets and the file to save the model:</span></span>

* <span data-ttu-id="d4fd6-160">`_trainDataPath` contém o caminho para o arquivo com o conjunto de dados usado para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-160">`_trainDataPath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="d4fd6-161">`_testDataPath` contém o caminho para o arquivo com o conjunto de dados usado para avaliar o modelo.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-161">`_testDataPath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="d4fd6-162">`_modelPath` contém o caminho para o arquivo em que o modelo treinado está armazenado.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-162">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="d4fd6-163">Adicione o seguinte código logo acima do método `Main` para especificar estes caminhos e para a variável `_textLoader`:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-163">Add the following code right above the `Main` method to specify those paths and for the `_textLoader` variable:</span></span>

[!code-csharp[InitializePaths](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="d4fd6-164">Todas as operações do ML.NET iniciam na [classe MLContext](xref:Microsoft.ML.MLContext).</span><span class="sxs-lookup"><span data-stu-id="d4fd6-164">All ML.NET operations start in the [MLContext class](xref:Microsoft.ML.MLContext).</span></span> <span data-ttu-id="d4fd6-165">Inicializar `mlContext` cria um novo ambiente do ML.NET que pode ser compartilhado entre os objetos do fluxo de trabalho de criação de modelo.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-165">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="d4fd6-166">Ele é semelhante, conceitualmente, a `DBContext` no Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-166">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="d4fd6-167">Inicializar variáveis em Main</span><span class="sxs-lookup"><span data-stu-id="d4fd6-167">Initialize variables in Main</span></span>

<span data-ttu-id="d4fd6-168">Substitua a linha `Console.WriteLine("Hello World!")` no método `Main` pelo seguinte código para declarar e inicializar a variável `mlContext`:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-168">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="d4fd6-169">Adicione o seguinte como a linha seguinte de código no método `Main` para chamar o método `Train`:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-169">Add the following as the next line of code in the `Main` method to call the `Train` method:</span></span>

[!code-csharp[Train](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Train your model")]

<span data-ttu-id="d4fd6-170">O método `Train()` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-170">The `Train()` method executes the following tasks:</span></span>

* <span data-ttu-id="d4fd6-171">Carrega os dados.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-171">Loads the data.</span></span>
* <span data-ttu-id="d4fd6-172">Extrai e transforma os dados.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-172">Extracts and transforms the data.</span></span>
* <span data-ttu-id="d4fd6-173">Treina o modelo.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-173">Trains the model.</span></span>
* <span data-ttu-id="d4fd6-174">Retorna o modelo.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-174">Returns the model.</span></span>

<span data-ttu-id="d4fd6-175">O método `Train` treina o modelo.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-175">The `Train` method trains the model.</span></span> <span data-ttu-id="d4fd6-176">Crie esse método logo abaixo de `Main`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-176">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a><span data-ttu-id="d4fd6-177">Carregar e transformar dados</span><span class="sxs-lookup"><span data-stu-id="d4fd6-177">Load and transform data</span></span>

<span data-ttu-id="d4fd6-178">O ML.NET usa a [classe IDataView](xref:Microsoft.ML.IDataView) como uma maneira flexível e eficiente de descrever dados tabulares de texto ou numéricos.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-178">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="d4fd6-179">O `IDataView` pode carregar arquivos de texto ou em tempo real (por exemplo, banco de dados SQL ou arquivos de log).</span><span class="sxs-lookup"><span data-stu-id="d4fd6-179">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span> <span data-ttu-id="d4fd6-180">Adicione o seguinte código como a primeira linha do método `Train()`:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-180">Add the following code as the first line of the `Train()` method:</span></span>

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "loading training dataset")]

<span data-ttu-id="d4fd6-181">Como você deseja prever as tarifas de corrida de táxi, a coluna `FareAmount` é o `Label` que você vai prever (a saída do modelo). Use a classe de transformação `CopyColumnsEstimator` para copiar `FareAmount` e adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-181">As you want to predict the taxi trip fare, the `FareAmount` column is the `Label` that you will predict (the output of the model)Use the `CopyColumnsEstimator` transformation class to copy `FareAmount`, and add the following code:</span></span> 

[!code-csharp[CopyColumnsEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Use the CopyColumnsEstimator")]

<span data-ttu-id="d4fd6-182">O algoritmo que treina o modelo requer recursos **numéricos**, então, é necessário transformar os valores de dados categóricos (`VendorId`, `RateCode` e `PaymentType`) em números (`VendorIdEncoded`, `RateCodeEncoded` e `PaymentTypeEncoded`).</span><span class="sxs-lookup"><span data-stu-id="d4fd6-182">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers (`VendorIdEncoded`, `RateCodeEncoded`, and `PaymentTypeEncoded`).</span></span> <span data-ttu-id="d4fd6-183">Para fazer isso, use a classe de transformação [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer), que atribui valores de chave numérica diferentes para os diferentes valores em cada uma das colunas e adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-183">To do that, use the [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) transformation class, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

[!code-csharp[OneHotEncodingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Use the OneHotEncodingEstimator")]

<span data-ttu-id="d4fd6-184">A última etapa na preparação de dados combina todas as colunas de recursos na coluna **Features** usando a classe de transformação `mlContext.Transforms.Concatenate`.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-184">The last step in data preparation combines all of the feature columns into the **Features** column using the `mlContext.Transforms.Concatenate` transformation class.</span></span> <span data-ttu-id="d4fd6-185">Por padrão, um algoritmo de aprendizado processa apenas os recursos da coluna **Features**.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-185">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="d4fd6-186">Adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-186">Add the following code:</span></span>

[!code-csharp[ColumnConcatenatingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="d4fd6-187">Escolher um algoritmo de aprendizado</span><span class="sxs-lookup"><span data-stu-id="d4fd6-187">Choose a learning algorithm</span></span>

<span data-ttu-id="d4fd6-188">Esse problema é sobre prever uma tarifa de corrida de táxi em Nova York.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-188">This problem is about predicting a taxi trip fare in New York City.</span></span> <span data-ttu-id="d4fd6-189">À primeira vista, pode parecer que depende simplesmente da distância percorrida.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-189">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="d4fd6-190">No entanto, os taxistas em Nova York cobram valores variados por outros fatores, como passageiros adicionais ou pagamento por cartão de crédito em vez de dinheiro.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-190">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span> <span data-ttu-id="d4fd6-191">Você deseja prever o valor de preço, que é um valor real, com base em outros fatores no conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-191">You want to predict the price value, which is a real value, based on the other factors in the dataset.</span></span> <span data-ttu-id="d4fd6-192">Para fazer isso, você deve escolher uma tarefa de aprendizado de máquina de [regressão](../resources/glossary.md#regression).</span><span class="sxs-lookup"><span data-stu-id="d4fd6-192">To do that, you choose a [regression](../resources/glossary.md#regression) machine learning task.</span></span>

<span data-ttu-id="d4fd6-193">Acrescente a tarefa de aprendizado de máquina [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) às definições de transformação de dados adicionando o seguinte como a próxima linha de código em `Train()`:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-193">Append the [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) machine learning task to the data transformation definitions by adding the following as the next line of code in `Train()`:</span></span>

[!code-csharp[FastTreeRegressionTrainer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="d4fd6-194">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="d4fd6-194">Train the model</span></span>

<span data-ttu-id="d4fd6-195">Ajuste o modelo à `dataview` do treinamento e retorne o modelo treinado adicionando a seguinte linha de código ao método `Train()`:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-195">Fit the model to the training `dataview` and return the trained model by adding the following line of code in the `Train()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#11 "Train the model")]

<span data-ttu-id="d4fd6-196">O método [Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) treina o modelo transformando o conjunto de dados e aplicando o treinamento.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-196">The [Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="d4fd6-197">Retorne o modelo treinado com a seguinte linha de código no método `Train()`:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-197">Return the trained model with the following line of code in the `Train()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="d4fd6-198">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="d4fd6-198">Evaluate the model</span></span>

<span data-ttu-id="d4fd6-199">Em seguida, avalie o desempenho do modelo com seus dados de teste para garantia de qualidade e validação.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-199">Next, evaluate your model performance with your test data for quality assurance and validation.</span></span> <span data-ttu-id="d4fd6-200">Crie o método `Evaluate()`, logo após `Train()`, com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-200">Create the `Evaluate()` method, just after `Train()`, with the following code:</span></span>

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="d4fd6-201">O método `Evaluate` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-201">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="d4fd6-202">Carrega o conjunto de dados de teste.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-202">Loads the test dataset.</span></span>
* <span data-ttu-id="d4fd6-203">Cria o avaliador de regressão.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-203">Creates the regression evaluator.</span></span>
* <span data-ttu-id="d4fd6-204">Avalia o modelo e cria métricas.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-204">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="d4fd6-205">Exibe as métricas.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-205">Displays the metrics.</span></span>

<span data-ttu-id="d4fd6-206">Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `Train`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-206">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Call the Evaluate method")]

<span data-ttu-id="d4fd6-207">Carregue o conjunto de dados de teste usando o método [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A).</span><span class="sxs-lookup"><span data-stu-id="d4fd6-207">Load the test dataset using the [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method.</span></span> <span data-ttu-id="d4fd6-208">Avalie o modelo usando esse conjunto de dados como uma verificação de qualidade adicionando o seguinte código ao método `Evaluate`:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-208">Evaluate the model using this dataset as a quality check by adding the following code in the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Load the test dataset")]

<span data-ttu-id="d4fd6-209">Em seguida, transforme os dados `Test` adicionando o seguinte código a `Evaluate()`:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-209">Next, transform the `Test` data by adding the following code to `Evaluate()`:</span></span>

[!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Predict using the Transformer")]

<span data-ttu-id="d4fd6-210">O método [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) faz previsões para testar as linhas de entrada do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-210">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for the test dataset input rows.</span></span>

<span data-ttu-id="d4fd6-211">O método `RegressionContext.Evaluate` calcula as métricas de qualidade para o `PredictionModel` usando o conjunto de dados especificado.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-211">The `RegressionContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="d4fd6-212">Ele retorna um objeto <xref:Microsoft.ML.Data.RegressionMetrics> que contém as métricas gerais computadas pelos avaliadores de regressão.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-212">It returns a <xref:Microsoft.ML.Data.RegressionMetrics> object that contains the overall metrics computed by regression evaluators.</span></span> 

<span data-ttu-id="d4fd6-213">Para exibi-los a fim de determinar a qualidade do modelo, é preciso primeiro obter as métricas.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-213">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="d4fd6-214">Adicione o seguinte código ao método `Evaluate` como a linha seguinte:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-214">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Compute Metrics")]

<span data-ttu-id="d4fd6-215">Depois que você define a previsão, o método [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) avalia o modelo, que compara os valores previstos com os `Labels` reais no conjunto de dados de teste e retorna métricas sobre o desempenho do modelo.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-215">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="d4fd6-216">Adicione o seguinte código para avaliar o modelo e produzir as métricas de avaliação:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-216">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

<span data-ttu-id="d4fd6-217">[RSquared](../resources/glossary.md#coefficient-of-determination) é outra métrica de avaliação dos modelos de regressão.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-217">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="d4fd6-218">RSquared aceita valores entre 0 e 1.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-218">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="d4fd6-219">Quanto mais perto de 1 estiver o valor, melhor o modelo será.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-219">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="d4fd6-220">Adicione o seguinte código ao método `Evaluate` para exibir o valor RSquared:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-220">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#18 "Display the RSquared metric.")]

<span data-ttu-id="d4fd6-221">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) é uma das métricas de avaliação do modelo de regressão.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-221">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="d4fd6-222">Quanto menor, melhor o modelo.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-222">The lower it is, the better the model is.</span></span> <span data-ttu-id="d4fd6-223">Adicione o seguinte código ao método `Evaluate` para exibir o valor RMS:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-223">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="d4fd6-224">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="d4fd6-224">Use the model for predictions</span></span>

<span data-ttu-id="d4fd6-225">Crie o método `TestSinglePrediction`, logo após o método `Evaluate`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-225">Create the `TestSinglePrediction` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="d4fd6-226">O método `TestSinglePrediction` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-226">The `TestSinglePrediction` method executes the following tasks:</span></span>

* <span data-ttu-id="d4fd6-227">Cria um único comentário dos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-227">Creates a single comment of test data.</span></span>
* <span data-ttu-id="d4fd6-228">Prevê o valor da tarifa com base nos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-228">Predicts fare amount based on test data.</span></span>
* <span data-ttu-id="d4fd6-229">Combina dados de teste e previsões para relatórios.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-229">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="d4fd6-230">Exibe os resultados previstos.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-230">Displays the predicted results.</span></span>

<span data-ttu-id="d4fd6-231">Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `Evaluate`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-231">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallTestSinglePrediction](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#20 "Call the TestSinglePrediction method")]

<span data-ttu-id="d4fd6-232">Use o `PredictionEngine` para prever a tarifa adicionando o seguinte código a `TestSinglePrediction()`:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-232">Use the `PredictionEngine` to predict the fare by adding the following code to `TestSinglePrediction()`:</span></span>

[!code-csharp[MakePredictionEngine](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#22 "Create the PredictionFunction")]

<span data-ttu-id="d4fd6-233">O [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) é uma API de conveniência, que permite que você execute uma previsão em uma única instância de dados.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-233">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="d4fd6-234">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) não é thread-safe.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-234">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="d4fd6-235">É aceitável usar em ambientes de protótipo ou de thread único.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-235">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="d4fd6-236">Para melhorar o desempenho e a segurança de thread em ambientes de produção, use o serviço `PredictionEnginePool`, que cria um [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) de objetos [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) para uso em todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-236">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="d4fd6-237">Consulte este guia sobre como [usar o `PredictionEnginePool` em uma API Web do ASP.NET Core](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application)</span><span class="sxs-lookup"><span data-stu-id="d4fd6-237">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application)</span></span>

> [!NOTE]
> <span data-ttu-id="d4fd6-238">A extensão de serviço `PredictionEnginePool` está atualmente em versão prévia.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-238">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="d4fd6-239">Este tutorial usa uma viagem de teste dentro dessa classe.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-239">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="d4fd6-240">Posteriormente, você pode adicionar outros cenários para fazer experiências com o modelo.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-240">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="d4fd6-241">Adicione uma corrida de teste à previsão do modelo treinado no método `TestSinglePrediction()` ao criar uma instância de `TaxiTrip`:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-241">Add a trip to test the trained model's prediction of cost in the `TestSinglePrediction()` method by creating an instance of `TaxiTrip`:</span></span>

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#23 "Create test data for single prediction")]

<span data-ttu-id="d4fd6-242">Em seguida, preveja a tarifa com base em uma única instância dos dados de corrida táxi e passe-a para o `PredictionEngine` adicionando o seguinte como as próximas linhas do código no método `TestSinglePrediction()`:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-242">Next, predict the fare based on a single instance of the taxi trip data and pass it to the `PredictionEngine` by adding the following as the next lines of code in the `TestSinglePrediction()` method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#24 "Create a prediction of taxi fare")]

<span data-ttu-id="d4fd6-243">A função [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) faz uma previsão em uma única instância de dados.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-243">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single instance of data.</span></span>

<span data-ttu-id="d4fd6-244">Para exibir a tarifa prevista da corrida especificada, adicione o código a seguir ao método `TestSinglePrediction`:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-244">To display the predicted fare of the specified trip, add the following code into the `TestSinglePrediction` method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#25 "Display the prediction.")]

<span data-ttu-id="d4fd6-245">Execute o programa para ver a tarifa de táxi prevista para o seu caso de teste.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-245">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="d4fd6-246">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="d4fd6-246">Congratulations!</span></span> <span data-ttu-id="d4fd6-247">Agora você criou com sucesso um modelo de aprendizado de máquina para prever tarifas de táxi, avaliou sua precisão e o usou para fazer previsões.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-247">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="d4fd6-248">Encontre o código-fonte deste tutorial no repositório do GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction).</span><span class="sxs-lookup"><span data-stu-id="d4fd6-248">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d4fd6-249">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="d4fd6-249">Next steps</span></span>

<span data-ttu-id="d4fd6-250">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="d4fd6-250">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="d4fd6-251">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="d4fd6-251">Prepare and understand the data</span></span>
> * <span data-ttu-id="d4fd6-252">Criar um pipeline de aprendizado</span><span class="sxs-lookup"><span data-stu-id="d4fd6-252">Create a learning pipeline</span></span>
> * <span data-ttu-id="d4fd6-253">Carregar e transformar os dados</span><span class="sxs-lookup"><span data-stu-id="d4fd6-253">Load and transform the data</span></span>
> * <span data-ttu-id="d4fd6-254">Escolher um algoritmo de aprendizado</span><span class="sxs-lookup"><span data-stu-id="d4fd6-254">Choose a learning algorithm</span></span>
> * <span data-ttu-id="d4fd6-255">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="d4fd6-255">Train the model</span></span>
> * <span data-ttu-id="d4fd6-256">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="d4fd6-256">Evaluate the model</span></span>
> * <span data-ttu-id="d4fd6-257">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="d4fd6-257">Use the model for predictions</span></span>

<span data-ttu-id="d4fd6-258">Avance para o próximo tutorial para saber mais.</span><span class="sxs-lookup"><span data-stu-id="d4fd6-258">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d4fd6-259">Clustering de Iris</span><span class="sxs-lookup"><span data-stu-id="d4fd6-259">Iris clustering</span></span>](iris-clustering.md)
