---
title: Usar o ML.NET para prever tarifas de táxi em Nova York (regressão)
description: Saiba como usar o ML.NET em um cenário de regressão.
author: aditidugar
ms.author: johalex
ms.date: 06/05/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 048ed1d38408c1ba4901c554cae33d5552c9e303
ms.sourcegitcommit: 5b0802832fb9ad684d34e69b8644a16a5b7c4810
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34860631"
---
# <a name="tutorial-use-mlnet-to-predict-new-york-taxi-fares-regression"></a><span data-ttu-id="218cf-103">Tutorial: Usar o ML.NET para prever tarifas de táxi em Nova York (regressão)</span><span class="sxs-lookup"><span data-stu-id="218cf-103">Tutorial: Use ML.NET to predict New York taxi fares (regression)</span></span>

> [!NOTE]
> <span data-ttu-id="218cf-104">Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="218cf-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="218cf-105">Para obter mais informações, visite [a introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="218cf-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="218cf-106">Este tutorial ilustra como usar o ML.NET para criar um [modelo de regressão](../resources/glossary.md#regression) para prever tarifas de táxi em Nova York.</span><span class="sxs-lookup"><span data-stu-id="218cf-106">This tutorial illustrates how to use ML.NET to build a [regression model](../resources/glossary.md#regression) for predicting New York City taxi fares.</span></span>

<span data-ttu-id="218cf-107">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="218cf-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="218cf-108">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="218cf-108">Understand the problem</span></span>
> * <span data-ttu-id="218cf-109">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="218cf-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="218cf-110">Preparar e compreender seus dados</span><span class="sxs-lookup"><span data-stu-id="218cf-110">Prepare and understand your data</span></span>
> * <span data-ttu-id="218cf-111">Criar um pipeline de aprendizado</span><span class="sxs-lookup"><span data-stu-id="218cf-111">Create a learning pipeline</span></span>
> * <span data-ttu-id="218cf-112">Carregar e transformar seus dados</span><span class="sxs-lookup"><span data-stu-id="218cf-112">Load and transform your data</span></span>
> * <span data-ttu-id="218cf-113">Escolher um algoritmo de aprendizado</span><span class="sxs-lookup"><span data-stu-id="218cf-113">Choose a learning algorithm</span></span>
> * <span data-ttu-id="218cf-114">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="218cf-114">Train the model</span></span>
> * <span data-ttu-id="218cf-115">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="218cf-115">Evaluate the model</span></span>
> * <span data-ttu-id="218cf-116">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="218cf-116">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="218cf-117">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="218cf-117">Prerequisites</span></span>

* <span data-ttu-id="218cf-118">[Visual Studio 2017 15.6 ou posterior](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="218cf-118">[Visual Studio 2017 15.6 or later](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="218cf-119">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="218cf-119">Understand the problem</span></span>

<span data-ttu-id="218cf-120">Esse problema está centrado na **previsão da tarifa de uma viagem de táxi na cidade de Nova York**.</span><span class="sxs-lookup"><span data-stu-id="218cf-120">This problem is centered around **predicting the fare of a taxi trip in New York City**.</span></span> <span data-ttu-id="218cf-121">À primeira vista, pode parecer que depende simplesmente da distância percorrida.</span><span class="sxs-lookup"><span data-stu-id="218cf-121">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="218cf-122">No entanto, os taxistas em Nova York cobram valores variados por outros fatores, como passageiros adicionais ou pagamento por cartão de crédito em vez de dinheiro.</span><span class="sxs-lookup"><span data-stu-id="218cf-122">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="218cf-123">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="218cf-123">Select the appropriate machine learning task</span></span>

<span data-ttu-id="218cf-124">Para prever a tarifa de táxi, selecione primeiro a tarefa de aprendizado de máquina apropriada.</span><span class="sxs-lookup"><span data-stu-id="218cf-124">To predict the taxi fare, you first select the appropriate machine learning task.</span></span> <span data-ttu-id="218cf-125">Você está tentando prever um valor real (um duplo que representa o preço) com base nos outros fatores do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="218cf-125">You are looking to predict a real value (a double that represents price) based on the other factors in the dataset.</span></span> <span data-ttu-id="218cf-126">Você escolhe uma tarefa de [**regressão**](../resources/glossary.md#regression).</span><span class="sxs-lookup"><span data-stu-id="218cf-126">You choose a [**regression**](../resources/glossary.md#regression) task.</span></span>

<span data-ttu-id="218cf-127">O processo de treinamento do modelo identifica quais fatores no conjunto de dados são mais influentes ao prever o preço final da tarifa.</span><span class="sxs-lookup"><span data-stu-id="218cf-127">The process of training the model identifies which factors in the dataset are most influential when predicting the final fare price.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="218cf-128">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="218cf-128">Create a console application</span></span>

1. <span data-ttu-id="218cf-129">Abra o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="218cf-129">Open Visual Studio 2017.</span></span> <span data-ttu-id="218cf-130">Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="218cf-130">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="218cf-131">Na caixa de diálogo **Novo Projeto**, selecione o nó **Visual C#** seguido pelo nó **.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="218cf-131">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="218cf-132">Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="218cf-132">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="218cf-133">Na caixa de texto **Nome**, digite "TaxiFarePrediction" e selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="218cf-133">In the **Name** text box, type "TaxiFarePrediction" and then select the **OK** button.</span></span>

2. <span data-ttu-id="218cf-134">Crie um diretório chamado *Data* no seu projeto para salvar seus arquivos do conjunto de dados:</span><span class="sxs-lookup"><span data-stu-id="218cf-134">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="218cf-135">No **Gerenciador de Soluções**, clique com o botão direito do mouse no seu projeto e selecione **Adicionar** > **Nova Pasta**.</span><span class="sxs-lookup"><span data-stu-id="218cf-135">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="218cf-136">Digite "Dados" e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="218cf-136">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="218cf-137">Instalar o **Pacote NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="218cf-137">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="218cf-138">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="218cf-138">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="218cf-139">Escolha "nuget.org" como a Origem do pacote, selecione a guia Procurar, pesquise por **Microsoft.ML**, selecione o pacote na lista e escolha o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="218cf-139">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="218cf-140">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="218cf-140">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-and-understand-your-data"></a><span data-ttu-id="218cf-141">Preparar e compreender seus dados</span><span class="sxs-lookup"><span data-stu-id="218cf-141">Prepare and understand your data</span></span>

1. <span data-ttu-id="218cf-142">Baixe os conjuntos de dados [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) e [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) e salve-os na pasta *Dados* criada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="218cf-142">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="218cf-143">O conjunto de dados Taxi Trip treina o modelo de aprendizado de máquina e pode ser usado para avaliar a precisão do seu modelo.</span><span class="sxs-lookup"><span data-stu-id="218cf-143">The Taxi Trip data set trains the machine learning model and can be used to evaluate how accurate your model is.</span></span> <span data-ttu-id="218cf-144">Esses conjuntos de dados são originalmente do [Conjunto de dados NYC TLC Taxi Trip](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="218cf-144">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

2. <span data-ttu-id="218cf-145">No Gerenciador de Soluções, clique com o botão direito do mouse em cada um dos arquivos \*.csv e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="218cf-145">In Solution Explorer, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="218cf-146">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Sempre**.</span><span class="sxs-lookup"><span data-stu-id="218cf-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Always**.</span></span>

3. <span data-ttu-id="218cf-147">Abra o conjunto de dados **taxi-fare-train.csv** no editor de código e observe os cabeçalhos de coluna na primeira linha.</span><span class="sxs-lookup"><span data-stu-id="218cf-147">Open the **taxi-fare-train.csv** data set in the code editor and look at column headers in the first row.</span></span> <span data-ttu-id="218cf-148">Dê uma olhada em cada uma das colunas.</span><span class="sxs-lookup"><span data-stu-id="218cf-148">Take a look at each of the columns.</span></span> <span data-ttu-id="218cf-149">Compreenda os dados e decida quais colunas são **recursos** e qual é o **rótulo**.</span><span class="sxs-lookup"><span data-stu-id="218cf-149">Understand the data and decide which columns are **features** and which is the **label**.</span></span>

<span data-ttu-id="218cf-150">O **rótulo** é o identificador da coluna que você está tentando prever.</span><span class="sxs-lookup"><span data-stu-id="218cf-150">The **label** is the identifier of the column you are trying to predict.</span></span> <span data-ttu-id="218cf-151">Os **recursos** identificados são usados ​​para prever o rótulo.</span><span class="sxs-lookup"><span data-stu-id="218cf-151">The identified **features** are used to predict the label.</span></span>

* <span data-ttu-id="218cf-152">**vendor_id:** o ID do taxista é um recurso.</span><span class="sxs-lookup"><span data-stu-id="218cf-152">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="218cf-153">**rate_code:** o tipo de tarifa da viagem de táxi é um recurso.</span><span class="sxs-lookup"><span data-stu-id="218cf-153">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="218cf-154">**passenger_count:** o número de passageiros na viagem é um recurso.</span><span class="sxs-lookup"><span data-stu-id="218cf-154">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="218cf-155">**trip_time_in_secs:** a quantidade de tempo que a viagem levou.</span><span class="sxs-lookup"><span data-stu-id="218cf-155">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="218cf-156">Você não saberá quanto tempo a viagem demora até que seja concluída.</span><span class="sxs-lookup"><span data-stu-id="218cf-156">You won't know how long the trip takes until after it is completed.</span></span> <span data-ttu-id="218cf-157">Você pode excluir esta coluna do modelo.</span><span class="sxs-lookup"><span data-stu-id="218cf-157">You exclude this column from the model.</span></span>
* <span data-ttu-id="218cf-158">**trip_distance:** a distância da viagem é um recurso.</span><span class="sxs-lookup"><span data-stu-id="218cf-158">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="218cf-159">**payment_type:** o método de pagamento (dinheiro ou cartão de crédito) é um recurso.</span><span class="sxs-lookup"><span data-stu-id="218cf-159">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="218cf-160">**fare_amount:** a tarifa total de táxi paga é o rótulo.</span><span class="sxs-lookup"><span data-stu-id="218cf-160">**fare_amount:** The total taxi fare paid is the label.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="218cf-161">Criar classes e definir demarcadores</span><span class="sxs-lookup"><span data-stu-id="218cf-161">Create classes and define paths</span></span>

<span data-ttu-id="218cf-162">Adicione as seguintes instruções `using` adicionais ao início do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="218cf-162">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="218cf-163">Você precisa criar três variáveis ​​globais para manter os demarcadores dos arquivos baixados recentemente e salvar o modelo:</span><span class="sxs-lookup"><span data-stu-id="218cf-163">You need to create three global variables to hold the paths to the recently downloaded files and to save the model:</span></span>

* <span data-ttu-id="218cf-164">`_datapath` tem o demarcador para o conjunto de dados usado para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="218cf-164">`_datapath` has the path to the data set used to train the model.</span></span>
* <span data-ttu-id="218cf-165">`_testdatapath` tem o demarcador para o conjunto de dados usado para avaliar o modelo.</span><span class="sxs-lookup"><span data-stu-id="218cf-165">`_testdatapath` has the path to the data set used to evaluate the model.</span></span>
* <span data-ttu-id="218cf-166">`_modelpath` tem o demarcador em que o modelo treinado é armazenado.</span><span class="sxs-lookup"><span data-stu-id="218cf-166">`_modelpath` has the path where the trained model is stored.</span></span>

<span data-ttu-id="218cf-167">Adicione o seguinte código à linha logo acima de `Main` para especificar os arquivos baixados recentemente:</span><span class="sxs-lookup"><span data-stu-id="218cf-167">Add the following code to the line right above `Main` to specify the recently downloaded files:</span></span>

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="218cf-168">Em seguida, crie classes para os dados de entrada e as previsões:</span><span class="sxs-lookup"><span data-stu-id="218cf-168">Next, create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="218cf-169">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="218cf-169">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="218cf-170">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="218cf-170">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="218cf-171">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="218cf-171">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="218cf-172">Inclua as seguintes instruções `using` no novo arquivo:</span><span class="sxs-lookup"><span data-stu-id="218cf-172">Add the following `using` statements to the new file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="218cf-173">Remova a definição de classe existente e adicione o seguinte código, que tem duas classes `TaxiTrip` e `TaxiTripFarePrediction`, ao arquivo *TaxiTrip.cs*:</span><span class="sxs-lookup"><span data-stu-id="218cf-173">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="218cf-174">`TaxiTrip` é a classe do conjunto de dados de entrada e possui definições para cada uma das colunas do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="218cf-174">`TaxiTrip` is the input data set class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="218cf-175">`TaxiTripFarePrediction` é a classe usada para previsão depois que o modelo foi treinado.</span><span class="sxs-lookup"><span data-stu-id="218cf-175">The `TaxiTripFarePrediction` class is used for prediction after the model has been trained.</span></span> <span data-ttu-id="218cf-176">Ele tem um único float (`FareAmount`) e um atributo `Score`[ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) aplicado.</span><span class="sxs-lookup"><span data-stu-id="218cf-176">It has a single float (`FareAmount`) and a `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) attribute applied.</span></span>

<span data-ttu-id="218cf-177">Agora, volte para o arquivo **Program.cs**.</span><span class="sxs-lookup"><span data-stu-id="218cf-177">Now go back to the **Program.cs** file.</span></span> <span data-ttu-id="218cf-178">Em `Main`, substitua o `Console.WriteLine("Hello World!")` pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="218cf-178">In `Main`, replace the `Console.WriteLine("Hello World!")` with the following code:</span></span>

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

<span data-ttu-id="218cf-179">O método `Train` treina seu modelo.</span><span class="sxs-lookup"><span data-stu-id="218cf-179">The `Train` method trains your model.</span></span> <span data-ttu-id="218cf-180">Crie essa função logo abaixo de `Main`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="218cf-180">Create that function just below `Main`, using the following code:</span></span>

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="218cf-181">Criar um pipeline de aprendizado</span><span class="sxs-lookup"><span data-stu-id="218cf-181">Create a learning pipeline</span></span>

<span data-ttu-id="218cf-182">O pipeline de aprendizado carrega todos os dados e algoritmos necessários para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="218cf-182">The learning pipeline loads all of the data and algorithms necessary to train the model.</span></span> <span data-ttu-id="218cf-183">Adicione o seguinte código ao método `Train()`:</span><span class="sxs-lookup"><span data-stu-id="218cf-183">Add the following code into the `Train()` method:</span></span>

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-your-data"></a><span data-ttu-id="218cf-184">Carregar e transformar seus dados</span><span class="sxs-lookup"><span data-stu-id="218cf-184">Load and transform your data</span></span>

<span data-ttu-id="218cf-185">Em seguida, carregue seus dados no pipeline.</span><span class="sxs-lookup"><span data-stu-id="218cf-185">Next, load your data into the pipeline.</span></span> <span data-ttu-id="218cf-186">Aponte para o `_datapath` criado inicialmente e especifique o delimitador do arquivo .csv (,).</span><span class="sxs-lookup"><span data-stu-id="218cf-186">Point to the `_datapath` created initially and specify the delimiter of the .csv file (,).</span></span> <span data-ttu-id="218cf-187">Adicione o seguinte código ao método `Train()` abaixo da última etapa:</span><span class="sxs-lookup"><span data-stu-id="218cf-187">Add the following code into the `Train()` method underneath the last step:</span></span>

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(separator:','));
```

<span data-ttu-id="218cf-188">Você se referirá às colunas sem os sublinhados no código que está criando.</span><span class="sxs-lookup"><span data-stu-id="218cf-188">You'll refer to the columns without the underscores in the code you're creating.</span></span> <span data-ttu-id="218cf-189">Copie a coluna `FareAmount` para uma nova coluna chamada "Rótulo" usando a função `ColumnCopier()`.</span><span class="sxs-lookup"><span data-stu-id="218cf-189">Copy the `FareAmount` column into a new column called "Label" using the `ColumnCopier()` function.</span></span> <span data-ttu-id="218cf-190">Esta coluna é o **Rótulo**.</span><span class="sxs-lookup"><span data-stu-id="218cf-190">This column is the **Label**.</span></span>

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

<span data-ttu-id="218cf-191">Conduza alguma **engenharia de recursos** para transformar os dados de modo que possam ser usados ​​efetivamente para o aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="218cf-191">Conduct some **feature engineering** to transform the data so that it can be used effectively for machine learning.</span></span> <span data-ttu-id="218cf-192">O algoritmo que treina o modelo requer recursos **numéricos** , você transforma os dados categóricos (`VendorId`, `RateCode` e `PaymentType`) em números.</span><span class="sxs-lookup"><span data-stu-id="218cf-192">The algorithm that trains the model requires **numeric** features, you transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) into numbers.</span></span> <span data-ttu-id="218cf-193">A função `CategoricalOneHotVectorizer()` atribui uma chave numérica aos valores em cada uma dessas colunas.</span><span class="sxs-lookup"><span data-stu-id="218cf-193">The `CategoricalOneHotVectorizer()` function assigns a numeric key to the values in each of these columns.</span></span> <span data-ttu-id="218cf-194">Transforme seus dados adicionando este código:</span><span class="sxs-lookup"><span data-stu-id="218cf-194">Transform your data by adding this code:</span></span>

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

<span data-ttu-id="218cf-195">O último passo na preparação de dados combina todos os seus **recursos** em um vetor usando a função `ColumnConcatenator()`.</span><span class="sxs-lookup"><span data-stu-id="218cf-195">The last step in data preparation combines all of your **features** into one vector using the `ColumnConcatenator()` function.</span></span> <span data-ttu-id="218cf-196">Essa etapa necessária ajuda o algoritmo a processar facilmente seus recursos.</span><span class="sxs-lookup"><span data-stu-id="218cf-196">This necessary step helps the algorithm easily process your features.</span></span> <span data-ttu-id="218cf-197">Adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="218cf-197">Add the following code:</span></span>

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

<span data-ttu-id="218cf-198">Observe que a coluna `trip_time_in_secs` não está incluída.</span><span class="sxs-lookup"><span data-stu-id="218cf-198">Notice that the `trip_time_in_secs` column isn't included.</span></span> <span data-ttu-id="218cf-199">Você já determinou que ela não é um recurso de previsão útil.</span><span class="sxs-lookup"><span data-stu-id="218cf-199">You already determined that it isn't a useful prediction feature.</span></span>

> [!NOTE]
> <span data-ttu-id="218cf-200">Essas etapas devem ser adicionadas ao Pipeline na ordem especificada acima para uma execução bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="218cf-200">These steps must be added to Pipeline in the order specified above for successful execution.</span></span>

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="218cf-201">Escolher um algoritmo de aprendizado</span><span class="sxs-lookup"><span data-stu-id="218cf-201">Choose a learning algorithm</span></span>

<span data-ttu-id="218cf-202">Após adicionar os dados ao pipeline e transformá-los no formato de entrada correto, selecione um algoritmo de aprendizado (**aluno**).</span><span class="sxs-lookup"><span data-stu-id="218cf-202">After adding the data to the pipeline and transforming it into the correct input format, you select a learning algorithm (**learner**).</span></span> <span data-ttu-id="218cf-203">O algoritmo de aprendizado treina o modelo.</span><span class="sxs-lookup"><span data-stu-id="218cf-203">The learning algorithm trains the model.</span></span> <span data-ttu-id="218cf-204">Você escolheu uma **tarefa de regressão** para esse problema, então você adiciona um aprendiz chamado `FastTreeRegressor()` ao pipeline que utiliza o **aumento de gradiente**.</span><span class="sxs-lookup"><span data-stu-id="218cf-204">You chose a **regression task** for this problem, so you add a learner called `FastTreeRegressor()` to the pipeline that utilizes **gradient boosting**.</span></span>

<span data-ttu-id="218cf-205">O aumento de gradiente é uma técnica de aprendizado de máquina para problemas de regressão.</span><span class="sxs-lookup"><span data-stu-id="218cf-205">Gradient boosting is a machine learning technique for regression problems.</span></span> <span data-ttu-id="218cf-206">Ele cria cada árvore de regressão por etapas.</span><span class="sxs-lookup"><span data-stu-id="218cf-206">It builds each regression tree in a step-wise fashion.</span></span> <span data-ttu-id="218cf-207">Ele usa uma função de perda predefinida para medir o erro em cada etapa e corrigi-lo no próximo.</span><span class="sxs-lookup"><span data-stu-id="218cf-207">It uses a pre-defined loss function to measure the error in each step and correct for it in the next.</span></span> <span data-ttu-id="218cf-208">O resultado é um modelo de previsão que é, na verdade, um conjunto de modelos de previsão mais fracos.</span><span class="sxs-lookup"><span data-stu-id="218cf-208">The result is a prediction model that is actually an ensemble of weaker prediction models.</span></span> <span data-ttu-id="218cf-209">Para obter mais informações sobre o aumento de gradiente, consulte [Regressão da árvore de decisão aumentada](https://docs.microsoft.com/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span><span class="sxs-lookup"><span data-stu-id="218cf-209">For more information about gradient boosting, see [Boosted Decision Tree Regression](https://docs.microsoft.com/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span></span>

<span data-ttu-id="218cf-210">Adicione o seguinte código ao método `Train()` após o código de processamento de dados adicionado na última etapa:</span><span class="sxs-lookup"><span data-stu-id="218cf-210">Add the following code into the `Train()` method following the data processing code added in the last step:</span></span>

```csharp
pipeline.Add(new FastTreeRegressor());
```

<span data-ttu-id="218cf-211">Você adicionou todas as etapas anteriores ao pipeline como instruções individuais, mas o C# tem uma sintaxe de inicialização de coleta útil que simplifica a criação e a inicialização do pipeline.</span><span class="sxs-lookup"><span data-stu-id="218cf-211">You added all the preceding steps to the pipeline as individual statements, but C# has a handy collection initialization syntax that makes it simpler to create and initialize the pipeline.</span></span> <span data-ttu-id="218cf-212">Substitua o código que você adicionou até o método `Train()` com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="218cf-212">Replace the code you added so far to the `Train()` method with the following code:</span></span>

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a><span data-ttu-id="218cf-213">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="218cf-213">Train the model</span></span>

<span data-ttu-id="218cf-214">A etapa final é treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="218cf-214">The final step is to train the model.</span></span> <span data-ttu-id="218cf-215">Até este ponto, nada no pipeline foi executado.</span><span class="sxs-lookup"><span data-stu-id="218cf-215">Until this point, nothing in the pipeline has been executed.</span></span> <span data-ttu-id="218cf-216">A função `pipeline.Train<T_Input, T_Output>()` aceita o tipo de classe `TaxiTrip` predefinido e gera um tipo `TaxiTripFarePrediction`.</span><span class="sxs-lookup"><span data-stu-id="218cf-216">The `pipeline.Train<T_Input, T_Output>()` function takes in the pre-defined `TaxiTrip` class type and outputs a `TaxiTripFarePrediction` type.</span></span> <span data-ttu-id="218cf-217">Adicione este trecho final de código na função `Train()`:</span><span class="sxs-lookup"><span data-stu-id="218cf-217">Add this final piece of code into the `Train()` function:</span></span>

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

<span data-ttu-id="218cf-218">E pronto.</span><span class="sxs-lookup"><span data-stu-id="218cf-218">And that's it!</span></span> <span data-ttu-id="218cf-219">Você treinou com sucesso um modelo de aprendizado de máquina que pode prever tarifas de táxi em Nova York.</span><span class="sxs-lookup"><span data-stu-id="218cf-219">You have successfully trained a machine learning model that can predict taxi fares in NYC.</span></span> <span data-ttu-id="218cf-220">Agora, dê uma olhada para entender a precisão do seu modelo e aprenda a consumi-lo.</span><span class="sxs-lookup"><span data-stu-id="218cf-220">Now take a look to understand how accurate your model is and learn how to consume it.</span></span>

## <a name="save-the-model"></a><span data-ttu-id="218cf-221">Salvar o modelo</span><span class="sxs-lookup"><span data-stu-id="218cf-221">Save the model</span></span>

<span data-ttu-id="218cf-222">Antes de seguir para a próxima etapa, salve seu modelo em um arquivo .zip adicionando o seguinte código no final da sua função `Train()`:</span><span class="sxs-lookup"><span data-stu-id="218cf-222">Before you go onto the next step, save your model to a .zip file by adding the following code at the end of your `Train()` function:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

<span data-ttu-id="218cf-223">Adicionar a instrução `await` à chamada `model.WriteAsync()` significa que o método `Train()` deve ser alterado para um método assíncrono que retorne um `Task`.</span><span class="sxs-lookup"><span data-stu-id="218cf-223">Adding the `await` statement to the `model.WriteAsync()` call means that the `Train()` method must be changed to an async method that returns a `Task`.</span></span> <span data-ttu-id="218cf-224">Modifique a assinatura de `Train`, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="218cf-224">Modify the signature of `Train` as shown in the following code:</span></span>

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

<span data-ttu-id="218cf-225">Alterar o tipo de retorno do método `Train` significa que você precisa adicionar um `await` ao código que chama `Train` no método `Main`, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="218cf-225">Changing the return type of the `Train` method means you have to add an `await` to the code that calls `Train` in the `Main` method as shown in the following code:</span></span>

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

<span data-ttu-id="218cf-226">Adicionar um `await` ao seu método `Main` significa que o método `Main` deve ter o modificador `async` e retornar um `Task`:</span><span class="sxs-lookup"><span data-stu-id="218cf-226">Adding an `await` in your `Main` method means the `Main` method must have the `async` modifier and return a `Task`:</span></span>

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

<span data-ttu-id="218cf-227">Também é preciso adicionar o seguinte usando a instrução na parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="218cf-227">You also need to add the following using statement at the top of the file:</span></span>

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

<span data-ttu-id="218cf-228">Como o método `async Main` é um novo recurso do C# 7.1 e a versão da linguagem padrão do projeto é C# 7.0, é necessário alterar a versão da linguagem para C# 7.1 ou superior.</span><span class="sxs-lookup"><span data-stu-id="218cf-228">Because the `async Main` method is a new feature in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span>
<span data-ttu-id="218cf-229">Para fazer isso, clique com o botão direito do mouse no nó do projeto no **Gerenciador de Soluções** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="218cf-229">To do that, right-click on the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="218cf-230">Selecione a guia **Build** e o botão **Avançado**.</span><span class="sxs-lookup"><span data-stu-id="218cf-230">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="218cf-231">No menu suspenso, selecione **C# 7.1** (ou uma versão posterior).</span><span class="sxs-lookup"><span data-stu-id="218cf-231">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="218cf-232">Selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="218cf-232">Select the **OK** button.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="218cf-233">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="218cf-233">Evaluate the model</span></span>

<span data-ttu-id="218cf-234">Avaliação é o processo de verificar como o modelo funciona.</span><span class="sxs-lookup"><span data-stu-id="218cf-234">Evaluation is the process of checking how well the model works.</span></span> <span data-ttu-id="218cf-235">É importante que seu modelo faça boas previsões com base em dados que não foram usados ​​quando ele foi treinado.</span><span class="sxs-lookup"><span data-stu-id="218cf-235">It's important that your model makes good predictions on data that it didn't use when it was trained.</span></span> <span data-ttu-id="218cf-236">Uma forma de fazer isso é dividir os dados em conjuntos de dados de treinamento e teste, como você fez neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="218cf-236">One way to do this is by splitting the data into train and test datasets, as you did in this tutorial.</span></span> <span data-ttu-id="218cf-237">Agora que você treinou o modelo nos dados de treinamento, pode ver o desempenho dos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="218cf-237">Now that you've trained the model on the train data, you can see how well it performs on the test data.</span></span>

<span data-ttu-id="218cf-238">Volte para a sua função `Main` e adicione o seguinte código abaixo da chamada para o método `Train()`:</span><span class="sxs-lookup"><span data-stu-id="218cf-238">Go back to your `Main` function and add the following code beneath the call to the `Train()`method:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

<span data-ttu-id="218cf-239">A função `Evaluate()` avalia seu modelo.</span><span class="sxs-lookup"><span data-stu-id="218cf-239">The `Evaluate()` function evaluates your model.</span></span> <span data-ttu-id="218cf-240">Crie essa função abaixo de `Train()`.</span><span class="sxs-lookup"><span data-stu-id="218cf-240">Create that function below `Train()`.</span></span> <span data-ttu-id="218cf-241">Adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="218cf-241">Add the following code:</span></span>

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

<span data-ttu-id="218cf-242">Carregue os dados de teste usando a função `TextLoader()`.</span><span class="sxs-lookup"><span data-stu-id="218cf-242">Load the test data using the `TextLoader()` function.</span></span> <span data-ttu-id="218cf-243">Adicione o seguinte código ao método `Evaluate()`:</span><span class="sxs-lookup"><span data-stu-id="218cf-243">Add the following code into the `Evaluate()` method:</span></span>

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

<span data-ttu-id="218cf-244">Adicione o seguinte código para avaliar o modelo e produzir as métricas para ele:</span><span class="sxs-lookup"><span data-stu-id="218cf-244">Add the following code to evaluate the model and produce the metrics for it:</span></span>

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

<span data-ttu-id="218cf-245">O RMS é uma métrica para avaliar os problemas de regressão.</span><span class="sxs-lookup"><span data-stu-id="218cf-245">RMS is one metric for evaluating regression problems.</span></span> <span data-ttu-id="218cf-246">Quanto menor, melhor o seu modelo.</span><span class="sxs-lookup"><span data-stu-id="218cf-246">The lower it is, the better your model.</span></span> <span data-ttu-id="218cf-247">Adicione o seguinte código na função `Evaluate()` para imprimir o RMS do seu modelo.</span><span class="sxs-lookup"><span data-stu-id="218cf-247">Add the following code into the `Evaluate()` function to print the RMS for your model.</span></span>

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

<span data-ttu-id="218cf-248">O RSquared é uma métrica para avaliar os problemas de regressão.</span><span class="sxs-lookup"><span data-stu-id="218cf-248">RSquared is another metric for evaluating regression problems.</span></span> <span data-ttu-id="218cf-249">O RSquared será um valor entre 0 e 1.</span><span class="sxs-lookup"><span data-stu-id="218cf-249">RSquared will be a value between 0 and 1.</span></span> <span data-ttu-id="218cf-250">Quanto mais próximo de 1, melhor será seu modelo.</span><span class="sxs-lookup"><span data-stu-id="218cf-250">The closer you are to 1, the better your model.</span></span> <span data-ttu-id="218cf-251">Adicione o seguinte código na função `Evaluate()` para imprimir o valor de RSquared para o seu modelo.</span><span class="sxs-lookup"><span data-stu-id="218cf-251">Add the following code into the `Evaluate()` function to print the RSquared value for your model.</span></span>

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="218cf-252">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="218cf-252">Use the model for predictions</span></span>

<span data-ttu-id="218cf-253">Em seguida, crie uma classe para hospedar os cenários de teste que você pode usar para garantir que seu modelo esteja funcionando corretamente:</span><span class="sxs-lookup"><span data-stu-id="218cf-253">Next, create a class to house test scenarios that you can use to make sure your model is working correctly:</span></span>

1. <span data-ttu-id="218cf-254">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="218cf-254">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="218cf-255">No **Adicionar Novo Item** caixa de diálogo, selecione **classe** e altere o **nome** campo *TestTrips.cs*.</span><span class="sxs-lookup"><span data-stu-id="218cf-255">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestTrips.cs*.</span></span> <span data-ttu-id="218cf-256">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="218cf-256">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="218cf-257">Modifique a classe para ser estática, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="218cf-257">Modify the class to be static like in the following example:</span></span>

[!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

<span data-ttu-id="218cf-258">Este tutorial usa uma viagem de teste dentro dessa classe.</span><span class="sxs-lookup"><span data-stu-id="218cf-258">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="218cf-259">Posteriormente, você pode adicionar outros cenários para fazer experiências com essa amostra.</span><span class="sxs-lookup"><span data-stu-id="218cf-259">Later you can add other scenarios to experiment with this sample.</span></span> <span data-ttu-id="218cf-260">Adicione o seguinte código à classe `TestTrips`:</span><span class="sxs-lookup"><span data-stu-id="218cf-260">Add the following code into the `TestTrips` class:</span></span>

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

<span data-ttu-id="218cf-261">A tarifa real dessa viagem é 29,5, mas use 0 como espaço reservado.</span><span class="sxs-lookup"><span data-stu-id="218cf-261">This trip's actual fare is 29.5, but use 0 as a placeholder.</span></span> <span data-ttu-id="218cf-262">O algoritmo de aprendizado de máquina irá prever a tarifa.</span><span class="sxs-lookup"><span data-stu-id="218cf-262">The machine learning algorithm will predict the fare.</span></span>

<span data-ttu-id="218cf-263">Adicione o seguinte código na sua função `Main`.</span><span class="sxs-lookup"><span data-stu-id="218cf-263">Add the following code in your `Main` function.</span></span> <span data-ttu-id="218cf-264">Ele testa seu modelo usando os dados `TestTrip`:</span><span class="sxs-lookup"><span data-stu-id="218cf-264">It tests out your model using the `TestTrip` data:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

<span data-ttu-id="218cf-265">Execute o programa para ver a tarifa de táxi prevista para o seu caso de teste.</span><span class="sxs-lookup"><span data-stu-id="218cf-265">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="218cf-266">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="218cf-266">Congratulations!</span></span> <span data-ttu-id="218cf-267">Agora você criou com sucesso um modelo de aprendizado de máquina para prever tarifas de táxi, avaliou sua precisão e testou-o.</span><span class="sxs-lookup"><span data-stu-id="218cf-267">You've now successfully built a machine learning model for predicting taxi fares, evaluated its accuracy, and tested it.</span></span> <span data-ttu-id="218cf-268">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction).</span><span class="sxs-lookup"><span data-stu-id="218cf-268">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="218cf-269">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="218cf-269">Next steps</span></span>

<span data-ttu-id="218cf-270">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="218cf-270">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="218cf-271">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="218cf-271">Understand the problem</span></span>
> * <span data-ttu-id="218cf-272">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="218cf-272">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="218cf-273">Preparar e compreender seus dados</span><span class="sxs-lookup"><span data-stu-id="218cf-273">Prepare and understand your data</span></span>
> * <span data-ttu-id="218cf-274">Criar um pipeline de aprendizado</span><span class="sxs-lookup"><span data-stu-id="218cf-274">Create a learning pipeline</span></span>
> * <span data-ttu-id="218cf-275">Carregar e transformar seus dados</span><span class="sxs-lookup"><span data-stu-id="218cf-275">Load and transform your data</span></span>
> * <span data-ttu-id="218cf-276">Escolher um algoritmo de aprendizado</span><span class="sxs-lookup"><span data-stu-id="218cf-276">Choose a learning algorithm</span></span>
> * <span data-ttu-id="218cf-277">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="218cf-277">Train the model</span></span>
> * <span data-ttu-id="218cf-278">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="218cf-278">Evaluate the model</span></span>
> * <span data-ttu-id="218cf-279">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="218cf-279">Use the model for predictions</span></span>

<span data-ttu-id="218cf-280">Confira nosso repositório GitHub para continuar aprendendo e encontrar mais amostras.</span><span class="sxs-lookup"><span data-stu-id="218cf-280">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="218cf-281">dotnet/machinelearning GitHub repository</span><span class="sxs-lookup"><span data-stu-id="218cf-281">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
