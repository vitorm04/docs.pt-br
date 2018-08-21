---
title: Usar o ML.NET para prever tarifas de táxi em Nova York (regressão)
description: Saiba como usar o ML.NET em um cenário de regressão.
author: aditidugar
ms.author: johalex
ms.date: 06/18/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e3ff2124a43cf42ce26cf94cfd5384387eef0ed9
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37937066"
---
# <a name="tutorial-use-mlnet-to-predict-new-york-taxi-fares-regression"></a><span data-ttu-id="885e2-103">Tutorial: Usar o ML.NET para prever tarifas de táxi em Nova York (regressão)</span><span class="sxs-lookup"><span data-stu-id="885e2-103">Tutorial: Use ML.NET to predict New York taxi fares (regression)</span></span>

> [!NOTE]
> <span data-ttu-id="885e2-104">Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="885e2-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="885e2-105">Para obter mais informações, visite [a introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="885e2-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="885e2-106">Este tutorial ilustra como usar o ML.NET para criar um [modelo de regressão](../resources/glossary.md#regression) para prever tarifas de táxi em Nova York.</span><span class="sxs-lookup"><span data-stu-id="885e2-106">This tutorial illustrates how to use ML.NET to build a [regression model](../resources/glossary.md#regression) for predicting New York City taxi fares.</span></span>

<span data-ttu-id="885e2-107">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="885e2-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="885e2-108">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="885e2-108">Understand the problem</span></span>
> * <span data-ttu-id="885e2-109">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="885e2-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="885e2-110">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="885e2-110">Prepare and understand the data</span></span>
> * <span data-ttu-id="885e2-111">Criar um pipeline de aprendizado</span><span class="sxs-lookup"><span data-stu-id="885e2-111">Create a learning pipeline</span></span>
> * <span data-ttu-id="885e2-112">Carregar e transformar os dados</span><span class="sxs-lookup"><span data-stu-id="885e2-112">Load and transform the data</span></span>
> * <span data-ttu-id="885e2-113">Escolher um algoritmo de aprendizado</span><span class="sxs-lookup"><span data-stu-id="885e2-113">Choose a learning algorithm</span></span>
> * <span data-ttu-id="885e2-114">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="885e2-114">Train the model</span></span>
> * <span data-ttu-id="885e2-115">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="885e2-115">Evaluate the model</span></span>
> * <span data-ttu-id="885e2-116">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="885e2-116">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="885e2-117">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="885e2-117">Prerequisites</span></span>

* <span data-ttu-id="885e2-118">[Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="885e2-118">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="885e2-119">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="885e2-119">Understand the problem</span></span>

<span data-ttu-id="885e2-120">Esse problema está centrado na **previsão da tarifa de uma viagem de táxi na cidade de Nova York**.</span><span class="sxs-lookup"><span data-stu-id="885e2-120">This problem is centered around **predicting the fare of a taxi trip in New York City**.</span></span> <span data-ttu-id="885e2-121">À primeira vista, pode parecer que depende simplesmente da distância percorrida.</span><span class="sxs-lookup"><span data-stu-id="885e2-121">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="885e2-122">No entanto, os taxistas em Nova York cobram valores variados por outros fatores, como passageiros adicionais ou pagamento por cartão de crédito em vez de dinheiro.</span><span class="sxs-lookup"><span data-stu-id="885e2-122">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="885e2-123">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="885e2-123">Select the appropriate machine learning task</span></span>

<span data-ttu-id="885e2-124">Para prever a tarifa de táxi, selecione primeiro a tarefa de aprendizado de máquina apropriada.</span><span class="sxs-lookup"><span data-stu-id="885e2-124">To predict the taxi fare, you first select the appropriate machine learning task.</span></span> <span data-ttu-id="885e2-125">Você está tentando prever um valor real (um duplo que representa o preço) com base nos outros fatores do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="885e2-125">You are looking to predict a real value (a double that represents price) based on the other factors in the dataset.</span></span> <span data-ttu-id="885e2-126">Você escolhe uma tarefa de [**regressão**](../resources/glossary.md#regression).</span><span class="sxs-lookup"><span data-stu-id="885e2-126">You choose a [**regression**](../resources/glossary.md#regression) task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="885e2-127">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="885e2-127">Create a console application</span></span>

1. <span data-ttu-id="885e2-128">Abra o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="885e2-128">Open Visual Studio 2017.</span></span> <span data-ttu-id="885e2-129">Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="885e2-129">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="885e2-130">Na caixa de diálogo **Novo Projeto**, selecione o nó **Visual C#** seguido pelo nó **.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="885e2-130">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="885e2-131">Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="885e2-131">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="885e2-132">Na caixa de texto **Nome**, digite "TaxiFarePrediction" e selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="885e2-132">In the **Name** text box, type "TaxiFarePrediction" and then select the **OK** button.</span></span>

2. <span data-ttu-id="885e2-133">Crie um diretório chamado *Data* no seu projeto para salvar seus arquivos do conjunto de dados:</span><span class="sxs-lookup"><span data-stu-id="885e2-133">Create a directory named *Data* in your project to save the data set files:</span></span>

    <span data-ttu-id="885e2-134">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Nova Pasta**.</span><span class="sxs-lookup"><span data-stu-id="885e2-134">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="885e2-135">Digite "Data" e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="885e2-135">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="885e2-136">Instalar o **Pacote NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="885e2-136">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="885e2-137">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="885e2-137">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="885e2-138">Escolha "nuget.org" como a origem do Pacote, selecione a guia **Procurar**, pesquise **Microsoft.ML**, selecione o pacote na lista e escolha o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="885e2-138">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="885e2-139">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="885e2-139">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="885e2-140">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="885e2-140">Prepare and understand the data</span></span>

1. <span data-ttu-id="885e2-141">Baixe os conjuntos de dados [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) e [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) e salve-os na pasta *Data* criada na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="885e2-141">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="885e2-142">Esses conjuntos de dados são usados para treinar o modelo de aprendizado de máquina e, em seguida, avaliar a precisão dele.</span><span class="sxs-lookup"><span data-stu-id="885e2-142">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="885e2-143">Esses conjuntos de dados são originalmente do [Conjunto de dados NYC TLC Taxi Trip](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="885e2-143">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

2. <span data-ttu-id="885e2-144">No **Gerenciador de Soluções**, clique com o botão direito do mouse em cada um dos arquivos \*.csv e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="885e2-144">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="885e2-145">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Sempre**.</span><span class="sxs-lookup"><span data-stu-id="885e2-145">Under **Advanced**, change the value of **Copy to Output Directory** to **Always**.</span></span>

3. <span data-ttu-id="885e2-146">Abra o conjunto de dados **taxi-fare-train.csv** e observe os cabeçalhos de coluna na primeira linha.</span><span class="sxs-lookup"><span data-stu-id="885e2-146">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="885e2-147">Dê uma olhada em cada uma das colunas.</span><span class="sxs-lookup"><span data-stu-id="885e2-147">Take a look at each of the columns.</span></span> <span data-ttu-id="885e2-148">Compreenda os dados e decida quais colunas são **recursos** e qual é o **rótulo**.</span><span class="sxs-lookup"><span data-stu-id="885e2-148">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="885e2-149">O **rótulo** é o identificador da coluna que você quer prever.</span><span class="sxs-lookup"><span data-stu-id="885e2-149">The **label** is the identifier of the column you want to predict.</span></span> <span data-ttu-id="885e2-150">Os **recursos** identificados são usados ​​para prever o rótulo.</span><span class="sxs-lookup"><span data-stu-id="885e2-150">The identified **features** are used to predict the label.</span></span>

<span data-ttu-id="885e2-151">O conjunto de dados fornecido contém as seguintes colunas:</span><span class="sxs-lookup"><span data-stu-id="885e2-151">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="885e2-152">**vendor_id:** o ID do taxista é um recurso.</span><span class="sxs-lookup"><span data-stu-id="885e2-152">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="885e2-153">**rate_code:** o tipo de tarifa da viagem de táxi é um recurso.</span><span class="sxs-lookup"><span data-stu-id="885e2-153">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="885e2-154">**passenger_count:** o número de passageiros na viagem é um recurso.</span><span class="sxs-lookup"><span data-stu-id="885e2-154">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="885e2-155">**trip_time_in_secs:** a quantidade de tempo que a viagem levou.</span><span class="sxs-lookup"><span data-stu-id="885e2-155">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="885e2-156">Você deseja prever a tarifa da viagem antes de sua conclusão.</span><span class="sxs-lookup"><span data-stu-id="885e2-156">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="885e2-157">No momento, você não sabe a duração da viagem.</span><span class="sxs-lookup"><span data-stu-id="885e2-157">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="885e2-158">Portanto, o tempo da viagem não é um recurso e você excluirá essa coluna do modelo.</span><span class="sxs-lookup"><span data-stu-id="885e2-158">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="885e2-159">**trip_distance:** a distância da viagem é um recurso.</span><span class="sxs-lookup"><span data-stu-id="885e2-159">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="885e2-160">**payment_type:** o método de pagamento (dinheiro ou cartão de crédito) é um recurso.</span><span class="sxs-lookup"><span data-stu-id="885e2-160">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="885e2-161">**fare_amount:** a tarifa total de táxi paga é o rótulo.</span><span class="sxs-lookup"><span data-stu-id="885e2-161">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="885e2-162">Criar classes de dados</span><span class="sxs-lookup"><span data-stu-id="885e2-162">Create data classes</span></span>

<span data-ttu-id="885e2-163">Crie classes para os dados de entrada e as previsões:</span><span class="sxs-lookup"><span data-stu-id="885e2-163">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="885e2-164">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="885e2-164">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="885e2-165">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="885e2-165">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="885e2-166">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="885e2-166">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="885e2-167">Adicione as seguintes diretivas `using` ao novo arquivo:</span><span class="sxs-lookup"><span data-stu-id="885e2-167">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="885e2-168">Remova a definição de classe existente e adicione o seguinte código, que tem duas classes `TaxiTrip` e `TaxiTripFarePrediction`, ao arquivo *TaxiTrip.cs*:</span><span class="sxs-lookup"><span data-stu-id="885e2-168">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="885e2-169">`TaxiTrip` é a classe de dados de entrada e tem definições para cada uma das colunas do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="885e2-169">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="885e2-170">Use o atributo [Coluna](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) para especificar os índices das colunas de origem no conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="885e2-170">Use the [Column](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="885e2-171">A classe `TaxiTripFarePrediction` é usada para representar os resultados previstos.</span><span class="sxs-lookup"><span data-stu-id="885e2-171">The `TaxiTripFarePrediction` class is used to represent predicted results.</span></span> <span data-ttu-id="885e2-172">Ele tem um único campo de float (`FareAmount`) com um atributo `Score`[ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) aplicado.</span><span class="sxs-lookup"><span data-stu-id="885e2-172">It has a single float (`FareAmount`) field with a `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) attribute applied.</span></span> <span data-ttu-id="885e2-173">**Score** é a coluna especial no ML.NET.</span><span class="sxs-lookup"><span data-stu-id="885e2-173">The **Score** column is the special column in ML.NET.</span></span> <span data-ttu-id="885e2-174">O modelo produz valores previstos nessa coluna.</span><span class="sxs-lookup"><span data-stu-id="885e2-174">The model outputs predicted values into that column.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="885e2-175">Definir dados e caminhos de modelo</span><span class="sxs-lookup"><span data-stu-id="885e2-175">Define data and model paths</span></span>

<span data-ttu-id="885e2-176">Volte para o arquivo *Program.cs* e adicione três campos para conter os caminhos para os arquivos com conjuntos de dados e o arquivo para salvar o modelo:</span><span class="sxs-lookup"><span data-stu-id="885e2-176">Go back to the *Program.cs* file and add three fields to hold the paths to the files with data sets and the file to save the model:</span></span>

* <span data-ttu-id="885e2-177">`_datapath` contém o caminho para o arquivo com o conjunto de dados usado para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="885e2-177">`_datapath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="885e2-178">`_testdatapath` contém o caminho para o arquivo com o conjunto de dados usado para avaliar o modelo.</span><span class="sxs-lookup"><span data-stu-id="885e2-178">`_testdatapath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="885e2-179">`_modelpath` contém o caminho para o arquivo em que o modelo treinado está armazenado.</span><span class="sxs-lookup"><span data-stu-id="885e2-179">`_modelpath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="885e2-180">Adicione o seguinte código logo acima do método `Main` para especificar estes caminhos:</span><span class="sxs-lookup"><span data-stu-id="885e2-180">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="885e2-181">Para fazer com que o código anterior seja compilado, adicione as seguintes diretivas `using` ao início do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="885e2-181">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsingsForPaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Using statements for path definitions")]

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="885e2-182">Criar um pipeline de aprendizado</span><span class="sxs-lookup"><span data-stu-id="885e2-182">Create a learning pipeline</span></span>

<span data-ttu-id="885e2-183">Adicione as seguintes diretivas `using` adicionais ao início do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="885e2-183">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="885e2-184">Em `Main`, substitua o `Console.WriteLine("Hello World!")` pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="885e2-184">In `Main`, replace the `Console.WriteLine("Hello World!")` with the following code:</span></span>

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

<span data-ttu-id="885e2-185">O método `Train` treina o modelo.</span><span class="sxs-lookup"><span data-stu-id="885e2-185">The `Train` method trains the model.</span></span> <span data-ttu-id="885e2-186">Crie esse método logo abaixo de `Main`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="885e2-186">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

<span data-ttu-id="885e2-187">O pipeline de aprendizado carrega todos os dados e algoritmos necessários para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="885e2-187">The learning pipeline loads all of the data and algorithms necessary to train the model.</span></span> <span data-ttu-id="885e2-188">Adicione o seguinte código ao método `Train`:</span><span class="sxs-lookup"><span data-stu-id="885e2-188">Add the following code into the `Train` method:</span></span>

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-data"></a><span data-ttu-id="885e2-189">Carregar e transformar dados</span><span class="sxs-lookup"><span data-stu-id="885e2-189">Load and transform data</span></span>

<span data-ttu-id="885e2-190">A primeira etapa executada pelo pipeline de aprendizado é carregar os dados do conjunto de dados de treinamento.</span><span class="sxs-lookup"><span data-stu-id="885e2-190">The first step that the learning pipeline performs is loading data from the training data set.</span></span> <span data-ttu-id="885e2-191">Em nosso caso, o conjunto de dados de treinamento é armazenado no arquivo de texto com um caminho definido pelo campo `_datapath`.</span><span class="sxs-lookup"><span data-stu-id="885e2-191">In our case, training data set is stored in the text file with a path defined by the `_datapath` field.</span></span> <span data-ttu-id="885e2-192">Esse arquivo contém o cabeçalho com os nomes de coluna, então, a primeira linha deve ser ignorada enquanto os dados são carregados.</span><span class="sxs-lookup"><span data-stu-id="885e2-192">That file contains the header with the column names, so the first row should be ignored while loading data.</span></span> <span data-ttu-id="885e2-193">As colunas no arquivo são separadas por uma vírgula (",").</span><span class="sxs-lookup"><span data-stu-id="885e2-193">Columns in the file are separated by the comma (",").</span></span> <span data-ttu-id="885e2-194">Adicione o seguinte código ao método `Train`:</span><span class="sxs-lookup"><span data-stu-id="885e2-194">Add the following code into the `Train` method:</span></span>

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(useHeader: true, separator: ','));
```

<span data-ttu-id="885e2-195">Nas próximas etapas, trataremos das colunas pelos nomes definidos na classe `TaxiTrip`.</span><span class="sxs-lookup"><span data-stu-id="885e2-195">In the next steps we refer to the columns by the names defined in the `TaxiTrip` class.</span></span>

<span data-ttu-id="885e2-196">Quando o modelo é treinado e avaliado, os valores na coluna **Label** são considerados os valores corretos a serem previstos.</span><span class="sxs-lookup"><span data-stu-id="885e2-196">When the model is trained and evaluated, the values in the **Label** column are considered as correct values to be predicted.</span></span> <span data-ttu-id="885e2-197">Como queremos prever a tarifa da viagem de táxi, copie a coluna `FareAmount` para a coluna **Label**.</span><span class="sxs-lookup"><span data-stu-id="885e2-197">As we want to predict the taxi trip fare, copy the `FareAmount` column into the **Label** column.</span></span> <span data-ttu-id="885e2-198">Para fazer isso, use <xref:Microsoft.ML.Transforms.ColumnCopier> e adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="885e2-198">To do that, use <xref:Microsoft.ML.Transforms.ColumnCopier> and add the following code:</span></span>

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

<span data-ttu-id="885e2-199">O algoritmo que treina o modelo requer recursos **numéricos**, então é necessário transformar os valores de dados categóricos (`VendorId`, `RateCode` e `PaymentType`) em números.</span><span class="sxs-lookup"><span data-stu-id="885e2-199">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers.</span></span> <span data-ttu-id="885e2-200">Para fazer isso, use <xref:Microsoft.ML.Transforms.CategoricalOneHotVectorizer>, que atribui valores numéricos de chave diferentes aos valores diferentes em cada uma das colunas, e adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="885e2-200">To do that, use <xref:Microsoft.ML.Transforms.CategoricalOneHotVectorizer>, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

<span data-ttu-id="885e2-201">A última etapa na preparação de dados combina todas as colunas de recursos na coluna **Features** usando a classe de transformação <xref:Microsoft.ML.Transforms.ColumnConcatenator>.</span><span class="sxs-lookup"><span data-stu-id="885e2-201">The last step in data preparation combines all of the feature columns into the **Features** column using the <xref:Microsoft.ML.Transforms.ColumnConcatenator> transformation class.</span></span> <span data-ttu-id="885e2-202">Essa etapa é necessária, pois o aprendiz processa apenas os recursos da coluna **Features**.</span><span class="sxs-lookup"><span data-stu-id="885e2-202">This step is necessary as a learner processes only features from the **Features** column.</span></span> <span data-ttu-id="885e2-203">Adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="885e2-203">Add the following code:</span></span>

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

<span data-ttu-id="885e2-204">Observe que a coluna `TripTime`, que corresponde à coluna `trip_time_in_secs` no arquivo do conjunto de dados, não foi incluída.</span><span class="sxs-lookup"><span data-stu-id="885e2-204">Notice that the `TripTime` column, which corresponds to the `trip_time_in_secs` column in the data set file, isn't included.</span></span> <span data-ttu-id="885e2-205">Você já determinou que ela não é um recurso de previsão útil.</span><span class="sxs-lookup"><span data-stu-id="885e2-205">You already determined that it isn't a useful prediction feature.</span></span>

> [!NOTE]
> <span data-ttu-id="885e2-206">Essas etapas devem ser adicionadas ao pipeline na ordem especificada acima para uma execução bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="885e2-206">These steps must be added to the pipeline in the order specified above for successful execution.</span></span>

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="885e2-207">Escolher um algoritmo de aprendizado</span><span class="sxs-lookup"><span data-stu-id="885e2-207">Choose a learning algorithm</span></span>

<span data-ttu-id="885e2-208">Após adicionar os dados ao pipeline e transformá-los no formato de entrada correto, selecione um algoritmo de aprendizado (**aluno**).</span><span class="sxs-lookup"><span data-stu-id="885e2-208">After adding the data to the pipeline and transforming it into the correct input format, you select a learning algorithm (**learner**).</span></span> <span data-ttu-id="885e2-209">O aprendiz treina o modelo.</span><span class="sxs-lookup"><span data-stu-id="885e2-209">The learner trains the model.</span></span> <span data-ttu-id="885e2-210">Você escolheu uma **tarefa de regressão** para esse problema, então, adicione um aprendiz <xref:Microsoft.ML.Trainers.FastTreeRegressor>, que é um dos aprendizes de regressão fornecidos pelo ML.NET.</span><span class="sxs-lookup"><span data-stu-id="885e2-210">You chose a **regression task** for this problem, so you add a <xref:Microsoft.ML.Trainers.FastTreeRegressor> learner, which is one of the regression learners provided by ML.NET.</span></span>

<span data-ttu-id="885e2-211">O aprendiz <xref:Microsoft.ML.Trainers.FastTreeRegressor> utiliza o aumento do gradiente.</span><span class="sxs-lookup"><span data-stu-id="885e2-211"><xref:Microsoft.ML.Trainers.FastTreeRegressor> learner utilizes gradient boosting.</span></span> <span data-ttu-id="885e2-212">O aumento de gradiente é uma técnica de aprendizado de máquina para problemas de regressão.</span><span class="sxs-lookup"><span data-stu-id="885e2-212">Gradient boosting is a machine learning technique for regression problems.</span></span> <span data-ttu-id="885e2-213">Ele cria cada árvore de regressão por etapas.</span><span class="sxs-lookup"><span data-stu-id="885e2-213">It builds each regression tree in a step-wise fashion.</span></span> <span data-ttu-id="885e2-214">Ele usa uma função de perda predefinida para medir o erro em cada etapa e corrigi-lo no próximo.</span><span class="sxs-lookup"><span data-stu-id="885e2-214">It uses a pre-defined loss function to measure the error in each step and correct for it in the next.</span></span> <span data-ttu-id="885e2-215">O resultado é um modelo de previsão que é, na verdade, um conjunto de modelos de previsão mais fracos.</span><span class="sxs-lookup"><span data-stu-id="885e2-215">The result is a prediction model that is actually an ensemble of weaker prediction models.</span></span> <span data-ttu-id="885e2-216">Para obter mais informações sobre o aumento de gradiente, consulte [Regressão da árvore de decisão aumentada](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span><span class="sxs-lookup"><span data-stu-id="885e2-216">For more information about gradient boosting, see [Boosted Decision Tree Regression](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span></span>

<span data-ttu-id="885e2-217">Adicione o seguinte código ao método `Train` após o código de processamento de dados adicionado na etapa anterior:</span><span class="sxs-lookup"><span data-stu-id="885e2-217">Add the following code into the `Train` method following the data processing code added in the previous step:</span></span>

```csharp
pipeline.Add(new FastTreeRegressor());
```

<span data-ttu-id="885e2-218">Você adicionou todas as etapas anteriores ao pipeline como instruções individuais, mas o C# tem uma sintaxe de inicialização de coleta útil que simplifica a criação e a inicialização do pipeline.</span><span class="sxs-lookup"><span data-stu-id="885e2-218">You added all the preceding steps to the pipeline as individual statements, but C# has a handy collection initialization syntax that makes it simpler to create and initialize the pipeline.</span></span> <span data-ttu-id="885e2-219">Substitua o código que você adicionou até o método `Train` com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="885e2-219">Replace the code you added so far to the `Train` method with the following code:</span></span>

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a><span data-ttu-id="885e2-220">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="885e2-220">Train the model</span></span>

<span data-ttu-id="885e2-221">A etapa final é treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="885e2-221">The final step is to train the model.</span></span> <span data-ttu-id="885e2-222">Até este ponto, nada no pipeline foi executado.</span><span class="sxs-lookup"><span data-stu-id="885e2-222">Until this point, nothing in the pipeline has been executed.</span></span> <span data-ttu-id="885e2-223">O método `pipeline.Train<TInput, TOutput>` produz o modelo que aceita uma instância do tipo `TInput` e produz uma instância do tipo `TOutput`.</span><span class="sxs-lookup"><span data-stu-id="885e2-223">The `pipeline.Train<TInput, TOutput>` method produces the model that takes in an instance of the `TInput` type and outputs an instance of the `TOutput` type.</span></span> <span data-ttu-id="885e2-224">Adicione o seguinte código ao método `Train`:</span><span class="sxs-lookup"><span data-stu-id="885e2-224">Add the following code into the `Train` method:</span></span>

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

<span data-ttu-id="885e2-225">E pronto.</span><span class="sxs-lookup"><span data-stu-id="885e2-225">And that's it!</span></span> <span data-ttu-id="885e2-226">Você treinou com sucesso um modelo de aprendizado de máquina que pode prever tarifas de táxi em Nova York.</span><span class="sxs-lookup"><span data-stu-id="885e2-226">You have successfully trained a machine learning model that can predict taxi fares in NYC.</span></span> <span data-ttu-id="885e2-227">Agora, vamos entender o nível de precisão do modelo e saber como usá-lo para prever os valores das tarifas de táxi.</span><span class="sxs-lookup"><span data-stu-id="885e2-227">Now let's take a look to understand how accurate the model is and learn how to use it to predict taxi fare values.</span></span>

### <a name="save-the-model"></a><span data-ttu-id="885e2-228">Salvar o modelo</span><span class="sxs-lookup"><span data-stu-id="885e2-228">Save the model</span></span>

<span data-ttu-id="885e2-229">Antes de seguir para a próxima etapa, salve o modelo em um arquivo .zip adicionando o seguinte código no final do método `Train`:</span><span class="sxs-lookup"><span data-stu-id="885e2-229">Before you go onto the next step, save the model to a .zip file by adding the following code at the end of the `Train` method:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

<span data-ttu-id="885e2-230">Adicionar a instrução `await` à chamada `model.WriteAsync` significa que o método `Train` deve ser alterado para um método assíncrono que retorne uma tarefa.</span><span class="sxs-lookup"><span data-stu-id="885e2-230">Adding the `await` statement to the `model.WriteAsync` call means that the `Train` method must be changed to an async method that returns a task.</span></span> <span data-ttu-id="885e2-231">Modifique a assinatura de `Train`, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="885e2-231">Modify the signature of `Train` as shown in the following code:</span></span>

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

<span data-ttu-id="885e2-232">Alterar o tipo de retorno do método `Train` significa que você precisa adicionar um `await` ao código que chama `Train` no método `Main`, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="885e2-232">Changing the return type of the `Train` method means you have to add an `await` to the code that calls `Train` in the `Main` method as shown in the following code:</span></span>

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

<span data-ttu-id="885e2-233">Usar um `await` no método `Main` significa que o método `Main` deve ter o modificador `async` e retornar um `Task`:</span><span class="sxs-lookup"><span data-stu-id="885e2-233">Using `await` in the `Main` method means the `Main` method must have the `async` modifier and return a `Task`:</span></span>

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

<span data-ttu-id="885e2-234">Também é preciso adicionar a seguinte diretiva `using` ao início do arquivo:</span><span class="sxs-lookup"><span data-stu-id="885e2-234">You also need to add the following `using` directive at the top of the file:</span></span>

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

<span data-ttu-id="885e2-235">Como o método `async Main` é um novo recurso adicionado no C# 7.1 e a versão da linguagem padrão do projeto é C# 7.0, é necessário alterar a versão da linguagem para C# 7.1 ou superior.</span><span class="sxs-lookup"><span data-stu-id="885e2-235">Because the `async Main` method is the feature added in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span> <span data-ttu-id="885e2-236">Para fazer isso, clique com o botão direito do mouse no nó do projeto no **Gerenciador de Soluções** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="885e2-236">To do that, right-click the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="885e2-237">Selecione a guia **Build** e o botão **Avançado**.</span><span class="sxs-lookup"><span data-stu-id="885e2-237">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="885e2-238">No menu suspenso, selecione **C# 7.1** (ou uma versão posterior).</span><span class="sxs-lookup"><span data-stu-id="885e2-238">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="885e2-239">Selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="885e2-239">Select the **OK** button.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="885e2-240">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="885e2-240">Evaluate the model</span></span>

<span data-ttu-id="885e2-241">Avaliação é o processo de verificar o quão bem modelo prevê os valores de rótulo.</span><span class="sxs-lookup"><span data-stu-id="885e2-241">Evaluation is the process of checking how well the model predicts label values.</span></span> <span data-ttu-id="885e2-242">É importante que o modelo faça boas previsões com base em dados que não foram usados para treiná-lo.</span><span class="sxs-lookup"><span data-stu-id="885e2-242">It's important that the model makes good predictions on data that was not used to train the model.</span></span> <span data-ttu-id="885e2-243">Uma forma de fazer isso é dividir os dados em conjuntos de dados de treinamento e teste, como neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="885e2-243">One way to do this is to split the data into train and test data sets, as it's done in this tutorial.</span></span> <span data-ttu-id="885e2-244">Agora que você treinou o modelo nos dados de treinamento, pode ver o desempenho dos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="885e2-244">Now that you've trained the model on the train data, you can see how well it performs on the test data.</span></span>

<span data-ttu-id="885e2-245">Volte para o método `Main` e adicione o seguinte código abaixo da chamada para o método `Train`:</span><span class="sxs-lookup"><span data-stu-id="885e2-245">Go back to the `Main` method and add the following code beneath the call to the `Train`method:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

<span data-ttu-id="885e2-246">O método `Evaluate` avalia o modelo.</span><span class="sxs-lookup"><span data-stu-id="885e2-246">The `Evaluate` method evaluates the model.</span></span> <span data-ttu-id="885e2-247">Para criá-lo, adicione o código a seguir abaixo do método `Train`:</span><span class="sxs-lookup"><span data-stu-id="885e2-247">To create that method, add the following code below the `Train` method:</span></span>

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

<span data-ttu-id="885e2-248">Adicione o código a seguir ao método `Evaluate` para configurar o carregamento dos dados de teste:</span><span class="sxs-lookup"><span data-stu-id="885e2-248">Add the following code into the `Evaluate` method to setup loading of the test data:</span></span>

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

<span data-ttu-id="885e2-249">Adicione o seguinte código para avaliar o modelo e produzir as métricas de avaliação:</span><span class="sxs-lookup"><span data-stu-id="885e2-249">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

<span data-ttu-id="885e2-250">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) é uma das métricas de avaliação do modelo de regressão.</span><span class="sxs-lookup"><span data-stu-id="885e2-250">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="885e2-251">Quanto menor, melhor o modelo.</span><span class="sxs-lookup"><span data-stu-id="885e2-251">The lower it is, the better the model is.</span></span> <span data-ttu-id="885e2-252">Adicione o seguinte código ao método `Evaluate` para exibir o valor RMS:</span><span class="sxs-lookup"><span data-stu-id="885e2-252">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

<span data-ttu-id="885e2-253">[RSquared](../resources/glossary.md#coefficient-of-determination) é outra métrica de avaliação dos modelos de regressão.</span><span class="sxs-lookup"><span data-stu-id="885e2-253">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="885e2-254">RSquared aceita valores entre 0 e 1.</span><span class="sxs-lookup"><span data-stu-id="885e2-254">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="885e2-255">Quanto mais perto de 1 estiver o valor, melhor o modelo será.</span><span class="sxs-lookup"><span data-stu-id="885e2-255">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="885e2-256">Adicione o seguinte código ao método `Evaluate` para exibir o valor RSquared:</span><span class="sxs-lookup"><span data-stu-id="885e2-256">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="885e2-257">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="885e2-257">Use the model for predictions</span></span>

<span data-ttu-id="885e2-258">Em seguida, crie uma classe para hospedar os cenários de teste que você pode usar para garantir que o modelo esteja funcionando corretamente:</span><span class="sxs-lookup"><span data-stu-id="885e2-258">Next, create a class to house test scenarios that you can use to make sure the model is working correctly:</span></span>

1. <span data-ttu-id="885e2-259">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="885e2-259">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="885e2-260">No **Adicionar Novo Item** caixa de diálogo, selecione **classe** e altere o **nome** campo *TestTrips.cs*.</span><span class="sxs-lookup"><span data-stu-id="885e2-260">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestTrips.cs*.</span></span> <span data-ttu-id="885e2-261">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="885e2-261">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="885e2-262">Modifique a classe para ser estática, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="885e2-262">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

<span data-ttu-id="885e2-263">Este tutorial usa uma viagem de teste dentro dessa classe.</span><span class="sxs-lookup"><span data-stu-id="885e2-263">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="885e2-264">Posteriormente, você pode adicionar outros cenários para fazer experiências com o modelo.</span><span class="sxs-lookup"><span data-stu-id="885e2-264">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="885e2-265">Adicione o seguinte código à classe `TestTrips`:</span><span class="sxs-lookup"><span data-stu-id="885e2-265">Add the following code into the `TestTrips` class:</span></span>

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

<span data-ttu-id="885e2-266">A tarifa real da viagem é 29,5.</span><span class="sxs-lookup"><span data-stu-id="885e2-266">This trip's actual fare is 29.5.</span></span> <span data-ttu-id="885e2-267">Use 0 como espaço reservado, pois o modelo preverá a tarifa.</span><span class="sxs-lookup"><span data-stu-id="885e2-267">Use 0 as a placeholder, as the model will predict the fare.</span></span>

<span data-ttu-id="885e2-268">Para prever a tarifa da viagem específica, volte para o arquivo *Program.cs* e adicione o código a seguir ao método `Main`:</span><span class="sxs-lookup"><span data-stu-id="885e2-268">To predict the fare of the specified trip, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

<span data-ttu-id="885e2-269">Execute o programa para ver a tarifa de táxi prevista para o seu caso de teste.</span><span class="sxs-lookup"><span data-stu-id="885e2-269">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="885e2-270">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="885e2-270">Congratulations!</span></span> <span data-ttu-id="885e2-271">Agora você criou com sucesso um modelo de aprendizado de máquina para prever tarifas de táxi, avaliou sua precisão e o usou para fazer previsões.</span><span class="sxs-lookup"><span data-stu-id="885e2-271">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="885e2-272">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction).</span><span class="sxs-lookup"><span data-stu-id="885e2-272">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="885e2-273">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="885e2-273">Next steps</span></span>

<span data-ttu-id="885e2-274">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="885e2-274">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="885e2-275">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="885e2-275">Understand the problem</span></span>
> * <span data-ttu-id="885e2-276">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="885e2-276">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="885e2-277">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="885e2-277">Prepare and understand the data</span></span>
> * <span data-ttu-id="885e2-278">Criar um pipeline de aprendizado</span><span class="sxs-lookup"><span data-stu-id="885e2-278">Create a learning pipeline</span></span>
> * <span data-ttu-id="885e2-279">Carregar e transformar os dados</span><span class="sxs-lookup"><span data-stu-id="885e2-279">Load and transform the data</span></span>
> * <span data-ttu-id="885e2-280">Escolher um algoritmo de aprendizado</span><span class="sxs-lookup"><span data-stu-id="885e2-280">Choose a learning algorithm</span></span>
> * <span data-ttu-id="885e2-281">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="885e2-281">Train the model</span></span>
> * <span data-ttu-id="885e2-282">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="885e2-282">Evaluate the model</span></span>
> * <span data-ttu-id="885e2-283">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="885e2-283">Use the model for predictions</span></span>

<span data-ttu-id="885e2-284">Avance para o próximo tutorial para saber mais.</span><span class="sxs-lookup"><span data-stu-id="885e2-284">Advance to the next tutorial to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="885e2-285">Clustering de Iris</span><span class="sxs-lookup"><span data-stu-id="885e2-285">Iris clustering</span></span>](iris-clustering.md)
