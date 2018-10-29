---
title: Usar o ML.NET para prever tarifas de táxi em Nova York (regressão)
description: Saiba como usar o ML.NET em um cenário de regressão.
author: aditidugar
ms.author: johalex
ms.date: 07/02/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: bfae97d65ec192e9289841c82d84807b4937b09a
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183809"
---
# <a name="tutorial-use-mlnet-to-predict-new-york-taxi-fares-regression"></a><span data-ttu-id="8188b-103">Tutorial: Usar o ML.NET para prever tarifas de táxi em Nova York (regressão)</span><span class="sxs-lookup"><span data-stu-id="8188b-103">Tutorial: Use ML.NET to predict New York taxi fares (regression)</span></span>

> [!NOTE]
> <span data-ttu-id="8188b-104">Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="8188b-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="8188b-105">Para obter mais informações, confira a [Introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="8188b-105">For more information, see the [ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="8188b-106">Este tutorial ilustra como usar o ML.NET para criar um [modelo de regressão](../resources/glossary.md#regression) para prever tarifas de táxi em Nova York.</span><span class="sxs-lookup"><span data-stu-id="8188b-106">This tutorial illustrates how to use ML.NET to build a [regression model](../resources/glossary.md#regression) for predicting New York City taxi fares.</span></span>

<span data-ttu-id="8188b-107">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="8188b-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="8188b-108">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="8188b-108">Understand the problem</span></span>
> * <span data-ttu-id="8188b-109">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="8188b-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="8188b-110">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="8188b-110">Prepare and understand the data</span></span>
> * <span data-ttu-id="8188b-111">Criar um pipeline de aprendizado</span><span class="sxs-lookup"><span data-stu-id="8188b-111">Create a learning pipeline</span></span>
> * <span data-ttu-id="8188b-112">Carregar e transformar os dados</span><span class="sxs-lookup"><span data-stu-id="8188b-112">Load and transform the data</span></span>
> * <span data-ttu-id="8188b-113">Escolher um algoritmo de aprendizado</span><span class="sxs-lookup"><span data-stu-id="8188b-113">Choose a learning algorithm</span></span>
> * <span data-ttu-id="8188b-114">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="8188b-114">Train the model</span></span>
> * <span data-ttu-id="8188b-115">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="8188b-115">Evaluate the model</span></span>
> * <span data-ttu-id="8188b-116">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="8188b-116">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8188b-117">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="8188b-117">Prerequisites</span></span>

* <span data-ttu-id="8188b-118">[Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="8188b-118">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="8188b-119">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="8188b-119">Understand the problem</span></span>

<span data-ttu-id="8188b-120">Este problema trata-se de prever a tarifa de uma viagem de táxi na cidade de Nova York.</span><span class="sxs-lookup"><span data-stu-id="8188b-120">This problem is about predicting the fare of a taxi trip in New York City.</span></span> <span data-ttu-id="8188b-121">À primeira vista, pode parecer que depende simplesmente da distância percorrida.</span><span class="sxs-lookup"><span data-stu-id="8188b-121">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="8188b-122">No entanto, os taxistas em Nova York cobram valores variados por outros fatores, como passageiros adicionais ou pagamento por cartão de crédito em vez de dinheiro.</span><span class="sxs-lookup"><span data-stu-id="8188b-122">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="8188b-123">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="8188b-123">Select the appropriate machine learning task</span></span>

<span data-ttu-id="8188b-124">Convém prever o valor do preço, que é um valor real, com base nos outros fatores no conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="8188b-124">You want to predict the price value, which is a real value, based on the other factors in the data set.</span></span> <span data-ttu-id="8188b-125">Para fazer isso, escolha uma tarefa de aprendizado de máquina de [regressão](../resources/glossary.md#regression).</span><span class="sxs-lookup"><span data-stu-id="8188b-125">To do that you choose a [regression](../resources/glossary.md#regression) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="8188b-126">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="8188b-126">Create a console application</span></span>

1. <span data-ttu-id="8188b-127">Abra o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="8188b-127">Open Visual Studio 2017.</span></span> <span data-ttu-id="8188b-128">Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="8188b-128">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="8188b-129">Na caixa de diálogo **Novo Projeto**, selecione o nó **Visual C#** seguido pelo nó **.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="8188b-129">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="8188b-130">Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="8188b-130">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="8188b-131">Na caixa de texto **Nome**, digite "TaxiFarePrediction" e selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="8188b-131">In the **Name** text box, type "TaxiFarePrediction" and then select the **OK** button.</span></span>

1. <span data-ttu-id="8188b-132">Crie um diretório chamado *Dados* em seu projeto para armazenar o conjunto de dados e os arquivos de modelo:</span><span class="sxs-lookup"><span data-stu-id="8188b-132">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="8188b-133">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Nova Pasta**.</span><span class="sxs-lookup"><span data-stu-id="8188b-133">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="8188b-134">Digite "Data" e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="8188b-134">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="8188b-135">Instale o pacote NuGet **Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="8188b-135">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="8188b-136">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="8188b-136">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="8188b-137">Escolha "nuget.org" como a origem do Pacote, selecione a guia **Procurar**, pesquise **Microsoft.ML**, selecione o pacote na lista e escolha o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="8188b-137">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="8188b-138">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="8188b-138">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="8188b-139">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="8188b-139">Prepare and understand the data</span></span>

1. <span data-ttu-id="8188b-140">Baixe os conjuntos de dados [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) e [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) e salve-os na pasta *Dados* criada na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="8188b-140">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="8188b-141">Esses conjuntos de dados são usados para treinar o modelo de aprendizado de máquina e, em seguida, avaliar a precisão dele.</span><span class="sxs-lookup"><span data-stu-id="8188b-141">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="8188b-142">Esses conjuntos de dados são originalmente do [Conjunto de dados NYC TLC Taxi Trip](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="8188b-142">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

1. <span data-ttu-id="8188b-143">No **Gerenciador de Soluções**, clique com o botão direito do mouse em cada um dos arquivos \*.csv e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="8188b-143">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="8188b-144">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.</span><span class="sxs-lookup"><span data-stu-id="8188b-144">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

1. <span data-ttu-id="8188b-145">Abra o conjunto de dados **taxi-fare-train.csv** e observe os cabeçalhos de coluna na primeira linha.</span><span class="sxs-lookup"><span data-stu-id="8188b-145">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="8188b-146">Dê uma olhada em cada uma das colunas.</span><span class="sxs-lookup"><span data-stu-id="8188b-146">Take a look at each of the columns.</span></span> <span data-ttu-id="8188b-147">Compreenda os dados e decida quais colunas são **recursos** e qual é o **rótulo**.</span><span class="sxs-lookup"><span data-stu-id="8188b-147">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="8188b-148">O **rótulo** é o identificador da coluna que você quer prever.</span><span class="sxs-lookup"><span data-stu-id="8188b-148">The **label** is the identifier of the column you want to predict.</span></span> <span data-ttu-id="8188b-149">Os **recursos** identificados são usados ​​para prever o rótulo.</span><span class="sxs-lookup"><span data-stu-id="8188b-149">The identified **features** are used to predict the label.</span></span>

<span data-ttu-id="8188b-150">O conjunto de dados fornecido contém as seguintes colunas:</span><span class="sxs-lookup"><span data-stu-id="8188b-150">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="8188b-151">**vendor_id:** o ID do taxista é um recurso.</span><span class="sxs-lookup"><span data-stu-id="8188b-151">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="8188b-152">**rate_code:** o tipo de tarifa da viagem de táxi é um recurso.</span><span class="sxs-lookup"><span data-stu-id="8188b-152">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="8188b-153">**passenger_count:** o número de passageiros na viagem é um recurso.</span><span class="sxs-lookup"><span data-stu-id="8188b-153">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="8188b-154">**trip_time_in_secs:** a quantidade de tempo que a viagem levou.</span><span class="sxs-lookup"><span data-stu-id="8188b-154">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="8188b-155">Você deseja prever a tarifa da viagem antes de sua conclusão.</span><span class="sxs-lookup"><span data-stu-id="8188b-155">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="8188b-156">No momento, você não sabe a duração da viagem.</span><span class="sxs-lookup"><span data-stu-id="8188b-156">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="8188b-157">Portanto, o tempo da viagem não é um recurso e você excluirá essa coluna do modelo.</span><span class="sxs-lookup"><span data-stu-id="8188b-157">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="8188b-158">**trip_distance:** a distância da viagem é um recurso.</span><span class="sxs-lookup"><span data-stu-id="8188b-158">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="8188b-159">**payment_type:** o método de pagamento (dinheiro ou cartão de crédito) é um recurso.</span><span class="sxs-lookup"><span data-stu-id="8188b-159">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="8188b-160">**fare_amount:** a tarifa total de táxi paga é o rótulo.</span><span class="sxs-lookup"><span data-stu-id="8188b-160">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="8188b-161">Criar classes de dados</span><span class="sxs-lookup"><span data-stu-id="8188b-161">Create data classes</span></span>

<span data-ttu-id="8188b-162">Crie classes para os dados de entrada e as previsões:</span><span class="sxs-lookup"><span data-stu-id="8188b-162">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="8188b-163">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="8188b-163">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="8188b-164">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="8188b-164">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="8188b-165">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="8188b-165">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="8188b-166">Adicione as seguintes diretivas `using` ao novo arquivo:</span><span class="sxs-lookup"><span data-stu-id="8188b-166">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="8188b-167">Remova a definição de classe existente e adicione o seguinte código, que tem duas classes `TaxiTrip` e `TaxiTripFarePrediction`, ao arquivo *TaxiTrip.cs*:</span><span class="sxs-lookup"><span data-stu-id="8188b-167">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="8188b-168">`TaxiTrip` é a classe de dados de entrada e tem definições para cada uma das colunas do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="8188b-168">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="8188b-169">Use o atributo [Coluna](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) para especificar os índices das colunas de origem no conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="8188b-169">Use the [Column](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="8188b-170">A classe `TaxiTripFarePrediction` representa os resultados previstos.</span><span class="sxs-lookup"><span data-stu-id="8188b-170">The `TaxiTripFarePrediction` class represents predicted results.</span></span> <span data-ttu-id="8188b-171">Ela tem um único campo de float, `FareAmount`, com um atributo `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) aplicado.</span><span class="sxs-lookup"><span data-stu-id="8188b-171">It has a single float field, `FareAmount`, with a `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) attribute applied.</span></span> <span data-ttu-id="8188b-172">No caso da tarefa de regressão, a coluna **Pontuação** contém valores de rótulo previsto.</span><span class="sxs-lookup"><span data-stu-id="8188b-172">In case of the regression task the **Score** column contains predicted label values.</span></span>

> [!NOTE]
> <span data-ttu-id="8188b-173">Use o tipo `float` para representar valores de ponto flutuante nas classes de dados de entrada e previsão.</span><span class="sxs-lookup"><span data-stu-id="8188b-173">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="8188b-174">Definir dados e caminhos de modelo</span><span class="sxs-lookup"><span data-stu-id="8188b-174">Define data and model paths</span></span>

<span data-ttu-id="8188b-175">Volte para o arquivo *Program.cs* e adicione três campos para conter os caminhos para os arquivos com conjuntos de dados e o arquivo para salvar o modelo:</span><span class="sxs-lookup"><span data-stu-id="8188b-175">Go back to the *Program.cs* file and add three fields to hold the paths to the files with data sets and the file to save the model:</span></span>

* <span data-ttu-id="8188b-176">`_datapath` contém o caminho para o arquivo com o conjunto de dados usado para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="8188b-176">`_datapath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="8188b-177">`_testdatapath` contém o caminho para o arquivo com o conjunto de dados usado para avaliar o modelo.</span><span class="sxs-lookup"><span data-stu-id="8188b-177">`_testdatapath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="8188b-178">`_modelpath` contém o caminho para o arquivo em que o modelo treinado está armazenado.</span><span class="sxs-lookup"><span data-stu-id="8188b-178">`_modelpath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="8188b-179">Adicione o seguinte código logo acima do método `Main` para especificar estes caminhos:</span><span class="sxs-lookup"><span data-stu-id="8188b-179">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="8188b-180">Para fazer com que o código anterior seja compilado, adicione as seguintes diretivas `using` ao início do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="8188b-180">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsingsForPaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Using statements for path definitions")]

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="8188b-181">Criar um pipeline de aprendizado</span><span class="sxs-lookup"><span data-stu-id="8188b-181">Create a learning pipeline</span></span>

<span data-ttu-id="8188b-182">Adicione as seguintes diretivas `using` adicionais ao início do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="8188b-182">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="8188b-183">No método `Main`, substitua `Console.WriteLine("Hello World!")` pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="8188b-183">In the `Main` method, replace the `Console.WriteLine("Hello World!")` with the following code:</span></span>

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

<span data-ttu-id="8188b-184">O método `Train` treina o modelo.</span><span class="sxs-lookup"><span data-stu-id="8188b-184">The `Train` method trains the model.</span></span> <span data-ttu-id="8188b-185">Crie esse método logo abaixo de `Main`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="8188b-185">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

<span data-ttu-id="8188b-186">O pipeline de aprendizado carrega todos os dados e algoritmos necessários para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="8188b-186">The learning pipeline loads all of the data and algorithms necessary to train the model.</span></span> <span data-ttu-id="8188b-187">Adicione o seguinte código ao método `Train`:</span><span class="sxs-lookup"><span data-stu-id="8188b-187">Add the following code into the `Train` method:</span></span>

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-data"></a><span data-ttu-id="8188b-188">Carregar e transformar dados</span><span class="sxs-lookup"><span data-stu-id="8188b-188">Load and transform data</span></span>

<span data-ttu-id="8188b-189">A primeira etapa a ser realizada é carregar os dados do conjunto de dados de treinamento.</span><span class="sxs-lookup"><span data-stu-id="8188b-189">The first step to perform is to load data from the training data set.</span></span> <span data-ttu-id="8188b-190">Em nosso caso, o conjunto de dados de treinamento é armazenado no arquivo de texto com um caminho definido pelo campo `_datapath`.</span><span class="sxs-lookup"><span data-stu-id="8188b-190">In our case, training data set is stored in the text file with a path defined by the `_datapath` field.</span></span> <span data-ttu-id="8188b-191">Esse arquivo tem o cabeçalho com os nomes de coluna, então, a primeira linha deve ser ignorada enquanto os dados são carregados.</span><span class="sxs-lookup"><span data-stu-id="8188b-191">That file has the header with the column names, so the first row should be ignored while loading data.</span></span> <span data-ttu-id="8188b-192">As colunas no arquivo são separadas por uma vírgula (",").</span><span class="sxs-lookup"><span data-stu-id="8188b-192">Columns in the file are separated by the comma (",").</span></span> <span data-ttu-id="8188b-193">Adicione o seguinte código ao método `Train`:</span><span class="sxs-lookup"><span data-stu-id="8188b-193">Add the following code into the `Train` method:</span></span>

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(useHeader: true, separator: ','));
```

<span data-ttu-id="8188b-194">Nas próximas etapas, trataremos das colunas pelos nomes definidos na classe `TaxiTrip`.</span><span class="sxs-lookup"><span data-stu-id="8188b-194">In the next steps we refer to the columns by the names defined in the `TaxiTrip` class.</span></span>

<span data-ttu-id="8188b-195">Quando o modelo é treinado e avaliado, por padrão, os valores na coluna **Rótulo** são considerados os valores corretos a serem previstos.</span><span class="sxs-lookup"><span data-stu-id="8188b-195">When the model is trained and evaluated, by default, the values in the **Label** column are considered as correct values to be predicted.</span></span> <span data-ttu-id="8188b-196">Como queremos prever a tarifa da viagem de táxi, copie a coluna `FareAmount` para a coluna **Label**.</span><span class="sxs-lookup"><span data-stu-id="8188b-196">As we want to predict the taxi trip fare, copy the `FareAmount` column into the **Label** column.</span></span> <span data-ttu-id="8188b-197">Para fazer isso, use <xref:Microsoft.ML.Legacy.Transforms.ColumnCopier> e adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="8188b-197">To do that, use <xref:Microsoft.ML.Legacy.Transforms.ColumnCopier> and add the following code:</span></span>

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

<span data-ttu-id="8188b-198">O algoritmo que treina o modelo requer recursos **numéricos**, então é necessário transformar os valores de dados categóricos (`VendorId`, `RateCode` e `PaymentType`) em números.</span><span class="sxs-lookup"><span data-stu-id="8188b-198">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers.</span></span> <span data-ttu-id="8188b-199">Para fazer isso, use <xref:Microsoft.ML.Legacy.Transforms.CategoricalOneHotVectorizer>, que atribui valores numéricos de chave diferentes aos valores diferentes em cada uma das colunas, e adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="8188b-199">To do that, use <xref:Microsoft.ML.Legacy.Transforms.CategoricalOneHotVectorizer>, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

<span data-ttu-id="8188b-200">A última etapa na preparação de dados combina todas as colunas de recursos na coluna **Features** usando a classe de transformação <xref:Microsoft.ML.Legacy.Transforms.ColumnConcatenator>.</span><span class="sxs-lookup"><span data-stu-id="8188b-200">The last step in data preparation combines all of the feature columns into the **Features** column using the <xref:Microsoft.ML.Legacy.Transforms.ColumnConcatenator> transformation class.</span></span> <span data-ttu-id="8188b-201">Por padrão, um algoritmo de aprendizado processa apenas os recursos da coluna **Features**.</span><span class="sxs-lookup"><span data-stu-id="8188b-201">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="8188b-202">Adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="8188b-202">Add the following code:</span></span>

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

<span data-ttu-id="8188b-203">Observe que a coluna `TripTime`, que corresponde à coluna `trip_time_in_secs` no arquivo do conjunto de dados, não foi incluída.</span><span class="sxs-lookup"><span data-stu-id="8188b-203">Notice that the `TripTime` column, which corresponds to the `trip_time_in_secs` column in the data set file, isn't included.</span></span> <span data-ttu-id="8188b-204">Você já determinou que ela não é um recurso de previsão útil.</span><span class="sxs-lookup"><span data-stu-id="8188b-204">You already determined that it isn't a useful prediction feature.</span></span>

> [!NOTE]
> <span data-ttu-id="8188b-205">Essas etapas devem ser adicionadas ao pipeline na ordem especificada acima para uma execução bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="8188b-205">These steps must be added to the pipeline in the order specified above for successful execution.</span></span>

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="8188b-206">Escolher um algoritmo de aprendizado</span><span class="sxs-lookup"><span data-stu-id="8188b-206">Choose a learning algorithm</span></span>

<span data-ttu-id="8188b-207">Após adicionar os dados ao pipeline e transformá-los no formato de entrada correto, selecione um algoritmo de aprendizado (**aluno**).</span><span class="sxs-lookup"><span data-stu-id="8188b-207">After adding the data to the pipeline and transforming it into the correct input format, you select a learning algorithm (**learner**).</span></span> <span data-ttu-id="8188b-208">O aprendiz treina o modelo.</span><span class="sxs-lookup"><span data-stu-id="8188b-208">The learner trains the model.</span></span> <span data-ttu-id="8188b-209">Você escolheu uma tarefa de **regressão** para esse problema, então, use um aprendiz <xref:Microsoft.ML.Legacy.Trainers.FastTreeRegressor>, que é um dos aprendizes de regressão fornecidos pelo ML.NET.</span><span class="sxs-lookup"><span data-stu-id="8188b-209">You chose a **regression** task for this problem, so you use a <xref:Microsoft.ML.Legacy.Trainers.FastTreeRegressor> learner, which is one of the regression learners provided by ML.NET.</span></span>

<span data-ttu-id="8188b-210">O aprendiz <xref:Microsoft.ML.Legacy.Trainers.FastTreeRegressor> utiliza o aumento do gradiente.</span><span class="sxs-lookup"><span data-stu-id="8188b-210"><xref:Microsoft.ML.Legacy.Trainers.FastTreeRegressor> learner utilizes gradient boosting.</span></span> <span data-ttu-id="8188b-211">O aumento de gradiente é uma técnica de aprendizado de máquina para problemas de regressão.</span><span class="sxs-lookup"><span data-stu-id="8188b-211">Gradient boosting is a machine learning technique for regression problems.</span></span> <span data-ttu-id="8188b-212">Ele cria cada árvore de regressão por etapas.</span><span class="sxs-lookup"><span data-stu-id="8188b-212">It builds each regression tree in a step-wise fashion.</span></span> <span data-ttu-id="8188b-213">Ele usa uma função de perda predefinida para medir o erro em cada etapa e corrigi-lo no próximo.</span><span class="sxs-lookup"><span data-stu-id="8188b-213">It uses a pre-defined loss function to measure the error in each step and correct for it in the next.</span></span> <span data-ttu-id="8188b-214">O resultado é um modelo de previsão que é, na verdade, um conjunto de modelos de previsão mais fracos.</span><span class="sxs-lookup"><span data-stu-id="8188b-214">The result is a prediction model that is actually an ensemble of weaker prediction models.</span></span> <span data-ttu-id="8188b-215">Para obter mais informações sobre o aumento de gradiente, consulte [Regressão da árvore de decisão aumentada](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span><span class="sxs-lookup"><span data-stu-id="8188b-215">For more information about gradient boosting, see [Boosted Decision Tree Regression](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span></span>

<span data-ttu-id="8188b-216">Adicione o seguinte código ao método `Train` após o código de processamento de dados adicionado na etapa anterior:</span><span class="sxs-lookup"><span data-stu-id="8188b-216">Add the following code into the `Train` method following the data processing code added in the previous step:</span></span>

```csharp
pipeline.Add(new FastTreeRegressor());
```

<span data-ttu-id="8188b-217">Você adicionou todas as etapas anteriores ao pipeline como instruções individuais, mas o C# tem uma sintaxe de inicialização de coleta útil que simplifica a criação e a inicialização do pipeline.</span><span class="sxs-lookup"><span data-stu-id="8188b-217">You added all the preceding steps to the pipeline as individual statements, but C# has a handy collection initialization syntax that makes it simpler to create and initialize the pipeline.</span></span> <span data-ttu-id="8188b-218">Substitua o código que você adicionou até o método `Train` com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="8188b-218">Replace the code you added so far to the `Train` method with the following code:</span></span>

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a><span data-ttu-id="8188b-219">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="8188b-219">Train the model</span></span>

<span data-ttu-id="8188b-220">A etapa final é treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="8188b-220">The final step is to train the model.</span></span> <span data-ttu-id="8188b-221">Até este ponto, nada no pipeline foi executado.</span><span class="sxs-lookup"><span data-stu-id="8188b-221">Until this point, nothing in the pipeline has been executed.</span></span> <span data-ttu-id="8188b-222">O método `pipeline.Train<TInput, TOutput>` produz o modelo que aceita uma instância do tipo `TInput` e produz uma instância do tipo `TOutput`.</span><span class="sxs-lookup"><span data-stu-id="8188b-222">The `pipeline.Train<TInput, TOutput>` method produces the model that takes in an instance of the `TInput` type and outputs an instance of the `TOutput` type.</span></span> <span data-ttu-id="8188b-223">Adicione o seguinte código ao método `Train`:</span><span class="sxs-lookup"><span data-stu-id="8188b-223">Add the following code into the `Train` method:</span></span>

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

<span data-ttu-id="8188b-224">E pronto.</span><span class="sxs-lookup"><span data-stu-id="8188b-224">And that's it!</span></span> <span data-ttu-id="8188b-225">Você treinou com sucesso um modelo de aprendizado de máquina que pode prever tarifas de táxi em Nova York.</span><span class="sxs-lookup"><span data-stu-id="8188b-225">You have successfully trained a machine learning model that can predict taxi fares in NYC.</span></span> <span data-ttu-id="8188b-226">Agora, vamos entender o nível de precisão do modelo e saber como usá-lo para prever os valores das tarifas de táxi.</span><span class="sxs-lookup"><span data-stu-id="8188b-226">Now let's take a look to understand how accurate the model is and learn how to use it to predict taxi fare values.</span></span>

### <a name="save-the-model"></a><span data-ttu-id="8188b-227">Salvar o modelo</span><span class="sxs-lookup"><span data-stu-id="8188b-227">Save the model</span></span>

<span data-ttu-id="8188b-228">Neste ponto, você tem um modelo que pode ser integrado em qualquer um dos seus aplicativos .NET existentes ou novos.</span><span class="sxs-lookup"><span data-stu-id="8188b-228">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="8188b-229">Para salvar o modelo em um arquivo .zip, adicione o seguinte código no final do método `Train`:</span><span class="sxs-lookup"><span data-stu-id="8188b-229">To save the model to a .zip file, add the following code at the end of the `Train` method:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

<span data-ttu-id="8188b-230">Adicionar a instrução `await` à chamada `model.WriteAsync` significa que o método `Train` deve ser alterado para um método assíncrono que retorne uma tarefa.</span><span class="sxs-lookup"><span data-stu-id="8188b-230">Adding the `await` statement to the `model.WriteAsync` call means that the `Train` method must be changed to an async method that returns a task.</span></span> <span data-ttu-id="8188b-231">Modifique a assinatura de `Train`, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="8188b-231">Modify the signature of `Train` as shown in the following code:</span></span>

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

<span data-ttu-id="8188b-232">Alterar o tipo de retorno do método `Train` significa que você precisa adicionar um `await` ao código que chama `Train` no método `Main`, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="8188b-232">Changing the return type of the `Train` method means you have to add an `await` to the code that calls `Train` in the `Main` method as shown in the following code:</span></span>

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

<span data-ttu-id="8188b-233">Usar um `await` no método `Main` significa que o método `Main` deve ter o modificador `async` e retornar um `Task`:</span><span class="sxs-lookup"><span data-stu-id="8188b-233">Using `await` in the `Main` method means the `Main` method must have the `async` modifier and return a `Task`:</span></span>

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

<span data-ttu-id="8188b-234">Também é preciso adicionar a seguinte diretiva `using` ao início do arquivo:</span><span class="sxs-lookup"><span data-stu-id="8188b-234">You also need to add the following `using` directive at the top of the file:</span></span>

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

<span data-ttu-id="8188b-235">Como o método `async Main` é um novo recurso adicionado no C# 7.1 e a versão da linguagem padrão do projeto é C# 7.0, é necessário alterar a versão da linguagem para C# 7.1 ou superior.</span><span class="sxs-lookup"><span data-stu-id="8188b-235">Because the `async Main` method is the feature added in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span> <span data-ttu-id="8188b-236">Para fazer isso, clique com o botão direito do mouse no nó do projeto no **Gerenciador de Soluções** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="8188b-236">To do that, right-click the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="8188b-237">Selecione a guia **Build** e o botão **Avançado**.</span><span class="sxs-lookup"><span data-stu-id="8188b-237">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="8188b-238">No menu suspenso, selecione **C# 7.1** (ou uma versão posterior).</span><span class="sxs-lookup"><span data-stu-id="8188b-238">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="8188b-239">Selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="8188b-239">Select the **OK** button.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="8188b-240">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="8188b-240">Evaluate the model</span></span>

<span data-ttu-id="8188b-241">Avaliação é o processo de verificar o quão bem modelo prevê os valores de rótulo.</span><span class="sxs-lookup"><span data-stu-id="8188b-241">Evaluation is the process of checking how well the model predicts label values.</span></span> <span data-ttu-id="8188b-242">É importante que o modelo faça boas previsões com base em dados que não foram usados para treiná-lo.</span><span class="sxs-lookup"><span data-stu-id="8188b-242">It's important that the model makes good predictions on data that was not used to train the model.</span></span> <span data-ttu-id="8188b-243">Uma forma de fazer isso é dividir os dados em conjuntos de dados de treinamento e teste, como neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="8188b-243">One way to do this is to split the data into training and test data sets, as it's done in this tutorial.</span></span> <span data-ttu-id="8188b-244">Agora que você treinou o modelo nos dados de treinamento, pode ver o desempenho dos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="8188b-244">Now that you've trained the model on the training data, you can see how well it performs on the test data.</span></span>

<span data-ttu-id="8188b-245">Volte para o método `Main` e adicione o seguinte código abaixo da chamada para o método `Train`:</span><span class="sxs-lookup"><span data-stu-id="8188b-245">Go back to the `Main` method and add the following code beneath the call to the `Train`method:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

<span data-ttu-id="8188b-246">O método `Evaluate` avalia o modelo.</span><span class="sxs-lookup"><span data-stu-id="8188b-246">The `Evaluate` method evaluates the model.</span></span> <span data-ttu-id="8188b-247">Para criá-lo, adicione o código a seguir abaixo do método `Train`:</span><span class="sxs-lookup"><span data-stu-id="8188b-247">To create that method, add the following code below the `Train` method:</span></span>

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

<span data-ttu-id="8188b-248">Adicione o código a seguir ao método `Evaluate` para configurar o carregamento dos dados de teste:</span><span class="sxs-lookup"><span data-stu-id="8188b-248">Add the following code into the `Evaluate` method to setup loading of the test data:</span></span>

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

<span data-ttu-id="8188b-249">Adicione o seguinte código para avaliar o modelo e produzir as métricas de avaliação:</span><span class="sxs-lookup"><span data-stu-id="8188b-249">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

<span data-ttu-id="8188b-250">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) é uma das métricas de avaliação do modelo de regressão.</span><span class="sxs-lookup"><span data-stu-id="8188b-250">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="8188b-251">Quanto menor, melhor o modelo.</span><span class="sxs-lookup"><span data-stu-id="8188b-251">The lower it is, the better the model is.</span></span> <span data-ttu-id="8188b-252">Adicione o seguinte código ao método `Evaluate` para exibir o valor RMS:</span><span class="sxs-lookup"><span data-stu-id="8188b-252">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

<span data-ttu-id="8188b-253">[RSquared](../resources/glossary.md#coefficient-of-determination) é outra métrica de avaliação dos modelos de regressão.</span><span class="sxs-lookup"><span data-stu-id="8188b-253">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="8188b-254">RSquared aceita valores entre 0 e 1.</span><span class="sxs-lookup"><span data-stu-id="8188b-254">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="8188b-255">Quanto mais perto de 1 estiver o valor, melhor o modelo será.</span><span class="sxs-lookup"><span data-stu-id="8188b-255">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="8188b-256">Adicione o seguinte código ao método `Evaluate` para exibir o valor RSquared:</span><span class="sxs-lookup"><span data-stu-id="8188b-256">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="8188b-257">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="8188b-257">Use the model for predictions</span></span>

<span data-ttu-id="8188b-258">Crie uma classe para hospedar as instâncias de dados de teste:</span><span class="sxs-lookup"><span data-stu-id="8188b-258">Create a class to house test data instances:</span></span>

1. <span data-ttu-id="8188b-259">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="8188b-259">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="8188b-260">No **Adicionar Novo Item** caixa de diálogo, selecione **classe** e altere o **nome** campo *TestTrips.cs*.</span><span class="sxs-lookup"><span data-stu-id="8188b-260">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestTrips.cs*.</span></span> <span data-ttu-id="8188b-261">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="8188b-261">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="8188b-262">Modifique a classe para ser estática, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="8188b-262">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

<span data-ttu-id="8188b-263">Este tutorial usa uma viagem de teste dentro dessa classe.</span><span class="sxs-lookup"><span data-stu-id="8188b-263">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="8188b-264">Posteriormente, você pode adicionar outros cenários para fazer experiências com o modelo.</span><span class="sxs-lookup"><span data-stu-id="8188b-264">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="8188b-265">Adicione o seguinte código à classe `TestTrips`:</span><span class="sxs-lookup"><span data-stu-id="8188b-265">Add the following code into the `TestTrips` class:</span></span>

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

<span data-ttu-id="8188b-266">A tarifa real da viagem é 29,5.</span><span class="sxs-lookup"><span data-stu-id="8188b-266">This trip's actual fare is 29.5.</span></span> <span data-ttu-id="8188b-267">Use 0 como espaço reservado, pois o modelo preverá a tarifa.</span><span class="sxs-lookup"><span data-stu-id="8188b-267">Use 0 as a placeholder, as the model will predict the fare.</span></span>

<span data-ttu-id="8188b-268">Para prever a tarifa da viagem específica, volte para o arquivo *Program.cs* e adicione o código a seguir ao método `Main`:</span><span class="sxs-lookup"><span data-stu-id="8188b-268">To predict the fare of the specified trip, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

<span data-ttu-id="8188b-269">Execute o programa para ver a tarifa de táxi prevista para o seu caso de teste.</span><span class="sxs-lookup"><span data-stu-id="8188b-269">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="8188b-270">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="8188b-270">Congratulations!</span></span> <span data-ttu-id="8188b-271">Agora você criou com sucesso um modelo de aprendizado de máquina para prever tarifas de táxi, avaliou sua precisão e o usou para fazer previsões.</span><span class="sxs-lookup"><span data-stu-id="8188b-271">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="8188b-272">Encontre o código-fonte deste tutorial no repositório do GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction).</span><span class="sxs-lookup"><span data-stu-id="8188b-272">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8188b-273">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="8188b-273">Next steps</span></span>

<span data-ttu-id="8188b-274">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="8188b-274">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="8188b-275">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="8188b-275">Understand the problem</span></span>
> * <span data-ttu-id="8188b-276">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="8188b-276">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="8188b-277">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="8188b-277">Prepare and understand the data</span></span>
> * <span data-ttu-id="8188b-278">Criar um pipeline de aprendizado</span><span class="sxs-lookup"><span data-stu-id="8188b-278">Create a learning pipeline</span></span>
> * <span data-ttu-id="8188b-279">Carregar e transformar os dados</span><span class="sxs-lookup"><span data-stu-id="8188b-279">Load and transform the data</span></span>
> * <span data-ttu-id="8188b-280">Escolher um algoritmo de aprendizado</span><span class="sxs-lookup"><span data-stu-id="8188b-280">Choose a learning algorithm</span></span>
> * <span data-ttu-id="8188b-281">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="8188b-281">Train the model</span></span>
> * <span data-ttu-id="8188b-282">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="8188b-282">Evaluate the model</span></span>
> * <span data-ttu-id="8188b-283">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="8188b-283">Use the model for predictions</span></span>

<span data-ttu-id="8188b-284">Avance para o próximo tutorial para saber mais.</span><span class="sxs-lookup"><span data-stu-id="8188b-284">Advance to the next tutorial to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="8188b-285">Clustering de Iris</span><span class="sxs-lookup"><span data-stu-id="8188b-285">Iris clustering</span></span>](iris-clustering.md)
