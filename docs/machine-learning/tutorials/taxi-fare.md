---
title: Prever os preços usando um aprendiz de regressão com o ML.NET
description: Prever os preços usando um aprendiz de regressão com o ML.NET.
author: aditidugar
ms.author: johalex
ms.date: 03/20/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 0a027b3b4930f7dda48d884faf0484cf33856c8d
ms.sourcegitcommit: 77854e8704b9689b73103d691db34d71c2bf1dad
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2019
ms.locfileid: "58307974"
---
# <a name="tutorial-predict-prices-using-a-regression-learner-with-mlnet"></a><span data-ttu-id="ee360-103">Tutorial: Prever os preços usando um aprendiz de regressão com o ML.NET</span><span class="sxs-lookup"><span data-stu-id="ee360-103">Tutorial: Predict prices using a regression learner with ML.NET</span></span>

<span data-ttu-id="ee360-104">Este tutorial ilustra como usar o ML.NET para criar uma [modelo de regressão](../resources/glossary.md#regression) para prever preços. Nesse caso, as tarifas de táxi na cidade de Nova York.</span><span class="sxs-lookup"><span data-stu-id="ee360-104">This tutorial illustrates how to use ML.NET to build a [regression model](../resources/glossary.md#regression) for predicting prices, specifically, New York City taxi fares.</span></span>

> [!NOTE]
> <span data-ttu-id="ee360-105">Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="ee360-105">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="ee360-106">Para obter mais informações, confira a [Introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="ee360-106">For more information, see the [ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="ee360-107">Este tutorial e uma amostra relacionada estão usando o **ML.NET versão 0.11** no momento.</span><span class="sxs-lookup"><span data-stu-id="ee360-107">This tutorial and related sample are currently using **ML.NET version 0.11**.</span></span> <span data-ttu-id="ee360-108">Saiba mais nas notas de versão no [repositório do GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="ee360-108">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="ee360-109">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="ee360-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="ee360-110">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="ee360-110">Understand the problem</span></span>
> * <span data-ttu-id="ee360-111">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="ee360-111">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="ee360-112">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="ee360-112">Prepare and understand the data</span></span>
> * <span data-ttu-id="ee360-113">Criar um pipeline de aprendizado</span><span class="sxs-lookup"><span data-stu-id="ee360-113">Create a learning pipeline</span></span>
> * <span data-ttu-id="ee360-114">Carregar e transformar os dados</span><span class="sxs-lookup"><span data-stu-id="ee360-114">Load and transform the data</span></span>
> * <span data-ttu-id="ee360-115">Escolher um algoritmo de aprendizado</span><span class="sxs-lookup"><span data-stu-id="ee360-115">Choose a learning algorithm</span></span>
> * <span data-ttu-id="ee360-116">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="ee360-116">Train the model</span></span>
> * <span data-ttu-id="ee360-117">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="ee360-117">Evaluate the model</span></span>
> * <span data-ttu-id="ee360-118">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="ee360-118">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ee360-119">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ee360-119">Prerequisites</span></span>

* <span data-ttu-id="ee360-120">[Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="ee360-120">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="ee360-121">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="ee360-121">Understand the problem</span></span>

<span data-ttu-id="ee360-122">Este problema trata-se de prever a tarifa de uma viagem de táxi na cidade de Nova York.</span><span class="sxs-lookup"><span data-stu-id="ee360-122">This problem is about predicting the fare of a taxi trip in New York City.</span></span> <span data-ttu-id="ee360-123">À primeira vista, pode parecer que depende simplesmente da distância percorrida.</span><span class="sxs-lookup"><span data-stu-id="ee360-123">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="ee360-124">No entanto, os taxistas em Nova York cobram valores variados por outros fatores, como passageiros adicionais ou pagamento por cartão de crédito em vez de dinheiro.</span><span class="sxs-lookup"><span data-stu-id="ee360-124">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="ee360-125">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="ee360-125">Select the appropriate machine learning task</span></span>

<span data-ttu-id="ee360-126">Convém prever o valor do preço, que é um valor real, com base nos outros fatores no conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="ee360-126">You want to predict the price value, which is a real value, based on the other factors in the data set.</span></span> <span data-ttu-id="ee360-127">Para fazer isso, escolha uma tarefa de aprendizado de máquina de [regressão](../resources/glossary.md#regression).</span><span class="sxs-lookup"><span data-stu-id="ee360-127">To do that you choose a [regression](../resources/glossary.md#regression) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="ee360-128">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="ee360-128">Create a console application</span></span>

1. <span data-ttu-id="ee360-129">Abra o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="ee360-129">Open Visual Studio 2017.</span></span> <span data-ttu-id="ee360-130">Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="ee360-130">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="ee360-131">Na caixa de diálogo **Novo Projeto**, selecione o nó **Visual C#** seguido pelo nó **.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="ee360-131">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="ee360-132">Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="ee360-132">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="ee360-133">Na caixa de texto **Nome**, digite "TaxiFarePrediction" e selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="ee360-133">In the **Name** text box, type "TaxiFarePrediction" and then select the **OK** button.</span></span>

1. <span data-ttu-id="ee360-134">Crie um diretório chamado *Dados* em seu projeto para armazenar o conjunto de dados e os arquivos de modelo:</span><span class="sxs-lookup"><span data-stu-id="ee360-134">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="ee360-135">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Nova Pasta**.</span><span class="sxs-lookup"><span data-stu-id="ee360-135">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="ee360-136">Digite "Data" e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="ee360-136">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="ee360-137">Instale o pacote NuGet **Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="ee360-137">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="ee360-138">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="ee360-138">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="ee360-139">Escolha "nuget.org" como a origem do Pacote, selecione a guia **Procurar**, pesquise **Microsoft.ML**, selecione o pacote na lista e escolha o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="ee360-139">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="ee360-140">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="ee360-140">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="ee360-141">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="ee360-141">Prepare and understand the data</span></span>

1. <span data-ttu-id="ee360-142">Baixe os conjuntos de dados [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) e [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) e salve-os na pasta *Dados* criada na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="ee360-142">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="ee360-143">Esses conjuntos de dados são usados para treinar o modelo de aprendizado de máquina e, em seguida, avaliar a precisão dele.</span><span class="sxs-lookup"><span data-stu-id="ee360-143">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="ee360-144">Esses conjuntos de dados são originalmente do [Conjunto de dados NYC TLC Taxi Trip](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="ee360-144">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

1. <span data-ttu-id="ee360-145">No **Gerenciador de Soluções**, clique com o botão direito do mouse em cada um dos arquivos \*.csv e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="ee360-145">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="ee360-146">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.</span><span class="sxs-lookup"><span data-stu-id="ee360-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

1. <span data-ttu-id="ee360-147">Abra o conjunto de dados **taxi-fare-train.csv** e observe os cabeçalhos de coluna na primeira linha.</span><span class="sxs-lookup"><span data-stu-id="ee360-147">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="ee360-148">Dê uma olhada em cada uma das colunas.</span><span class="sxs-lookup"><span data-stu-id="ee360-148">Take a look at each of the columns.</span></span> <span data-ttu-id="ee360-149">Compreenda os dados e decida quais colunas são **recursos** e qual é o **rótulo**.</span><span class="sxs-lookup"><span data-stu-id="ee360-149">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="ee360-150">O **rótulo** é o identificador da coluna que você quer prever.</span><span class="sxs-lookup"><span data-stu-id="ee360-150">The **label** is the identifier of the column you want to predict.</span></span> <span data-ttu-id="ee360-151">Os **recursos** identificados são usados ​​para prever o rótulo.</span><span class="sxs-lookup"><span data-stu-id="ee360-151">The identified **features** are used to predict the label.</span></span>

<span data-ttu-id="ee360-152">O conjunto de dados fornecido contém as seguintes colunas:</span><span class="sxs-lookup"><span data-stu-id="ee360-152">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="ee360-153">**vendor_id:** A ID do taxista é um recurso.</span><span class="sxs-lookup"><span data-stu-id="ee360-153">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="ee360-154">**rate_code:** O tipo de tarifa da corrida de táxi é um recurso.</span><span class="sxs-lookup"><span data-stu-id="ee360-154">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="ee360-155">**passenger_count:** O número de passageiros na corrida é um recurso.</span><span class="sxs-lookup"><span data-stu-id="ee360-155">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="ee360-156">**trip_time_in_secs:** O tempo que levou a corrida.</span><span class="sxs-lookup"><span data-stu-id="ee360-156">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="ee360-157">Você deseja prever a tarifa da viagem antes de sua conclusão.</span><span class="sxs-lookup"><span data-stu-id="ee360-157">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="ee360-158">No momento, você não sabe a duração da viagem.</span><span class="sxs-lookup"><span data-stu-id="ee360-158">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="ee360-159">Portanto, o tempo da viagem não é um recurso e você excluirá essa coluna do modelo.</span><span class="sxs-lookup"><span data-stu-id="ee360-159">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="ee360-160">**trip_distance:** A distância da corrida é um recurso.</span><span class="sxs-lookup"><span data-stu-id="ee360-160">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="ee360-161">**payment_type:** A forma de pagamento (dinheiro ou cartão de crédito) é um recurso.</span><span class="sxs-lookup"><span data-stu-id="ee360-161">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="ee360-162">**fare_amount:** A tarifa total de táxi paga é o rótulo.</span><span class="sxs-lookup"><span data-stu-id="ee360-162">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="ee360-163">Criar classes de dados</span><span class="sxs-lookup"><span data-stu-id="ee360-163">Create data classes</span></span>

<span data-ttu-id="ee360-164">Crie classes para os dados de entrada e as previsões:</span><span class="sxs-lookup"><span data-stu-id="ee360-164">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="ee360-165">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="ee360-165">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="ee360-166">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="ee360-166">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="ee360-167">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="ee360-167">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="ee360-168">Adicione as seguintes diretivas `using` ao novo arquivo:</span><span class="sxs-lookup"><span data-stu-id="ee360-168">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="ee360-169">Remova a definição de classe existente e adicione o seguinte código, que tem duas classes `TaxiTrip` e `TaxiTripFarePrediction`, ao arquivo *TaxiTrip.cs*:</span><span class="sxs-lookup"><span data-stu-id="ee360-169">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="ee360-170">`TaxiTrip` é a classe de dados de entrada e tem definições para cada uma das colunas do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="ee360-170">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="ee360-171">Use o atributo <xref:Microsoft.ML.Data.LoadColumnAttribute> para especificar os índices das colunas de origem no conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="ee360-171">Use the <xref:Microsoft.ML.Data.LoadColumnAttribute> attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="ee360-172">A classe `TaxiTripFarePrediction` representa os resultados previstos.</span><span class="sxs-lookup"><span data-stu-id="ee360-172">The `TaxiTripFarePrediction` class represents predicted results.</span></span> <span data-ttu-id="ee360-173">Ela tem um único campo de float, `FareAmount`, com um atributo `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> aplicado.</span><span class="sxs-lookup"><span data-stu-id="ee360-173">It has a single float field, `FareAmount`, with a `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> attribute applied.</span></span> <span data-ttu-id="ee360-174">No caso da tarefa de regressão, a coluna **Pontuação** contém valores de rótulo previsto.</span><span class="sxs-lookup"><span data-stu-id="ee360-174">In case of the regression task the **Score** column contains predicted label values.</span></span>

> [!NOTE]
> <span data-ttu-id="ee360-175">Use o tipo `float` para representar valores de ponto flutuante nas classes de dados de entrada e previsão.</span><span class="sxs-lookup"><span data-stu-id="ee360-175">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="ee360-176">Definir dados e caminhos de modelo</span><span class="sxs-lookup"><span data-stu-id="ee360-176">Define data and model paths</span></span>

<span data-ttu-id="ee360-177">Adicione as seguintes instruções `using` adicionais ao início do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="ee360-177">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="ee360-178">Você precisa criar três campos para conter os caminhos para os arquivos com conjuntos de dados e o arquivo para salvar o modelo:</span><span class="sxs-lookup"><span data-stu-id="ee360-178">You need to create three fields to hold the paths to the files with data sets and the file to save the model:</span></span>

* <span data-ttu-id="ee360-179">`_trainDataPath` contém o caminho para o arquivo com o conjunto de dados usado para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="ee360-179">`_trainDataPath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="ee360-180">`_testDataPath` contém o caminho para o arquivo com o conjunto de dados usado para avaliar o modelo.</span><span class="sxs-lookup"><span data-stu-id="ee360-180">`_testDataPath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="ee360-181">`_modelPath` contém o caminho para o arquivo em que o modelo treinado está armazenado.</span><span class="sxs-lookup"><span data-stu-id="ee360-181">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="ee360-182">Adicione o seguinte código logo acima do método `Main` para especificar estes caminhos e para a variável `_textLoader`:</span><span class="sxs-lookup"><span data-stu-id="ee360-182">Add the following code right above the `Main` method to specify those paths and for the `_textLoader` variable:</span></span>

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="ee360-183">Ao criar um modelo com o ML.NET, comece criando um Contexto de ML.</span><span class="sxs-lookup"><span data-stu-id="ee360-183">When building a model with ML.NET you start by creating an ML Context.</span></span> <span data-ttu-id="ee360-184">Isso é comparável conceitualmente ao uso de `DbContext` no Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="ee360-184">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span> <span data-ttu-id="ee360-185">O ambiente fornece um contexto para seu trabalho de aprendizado de máquina que pode ser usado na exceção do acompanhamento e registro em log.</span><span class="sxs-lookup"><span data-stu-id="ee360-185">The environment provides a context for your machine learning job that can be used for exception tracking and logging.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="ee360-186">Inicializar variáveis em Main</span><span class="sxs-lookup"><span data-stu-id="ee360-186">Initialize variables in Main</span></span>

<span data-ttu-id="ee360-187">Crie uma variável chamada `mlContext` e inicialize-a com uma nova instância de `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="ee360-187">Create a variable called `mlContext` and initialize it with a new instance of `MLContext`.</span></span>  <span data-ttu-id="ee360-188">Substitua a linha `Console.WriteLine("Hello World!")` pelo seguinte código no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="ee360-188">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="ee360-189">Adicione o seguinte como a linha seguinte de código no método `Main` para chamar o método `Train`:</span><span class="sxs-lookup"><span data-stu-id="ee360-189">Add the following as the next line of code in the `Main` method to call the `Train` method:</span></span>

[!code-csharp[Train](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Train your model")]

<span data-ttu-id="ee360-190">O método `Train` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="ee360-190">The `Train` method executes the following tasks:</span></span>

* <span data-ttu-id="ee360-191">Carrega os dados.</span><span class="sxs-lookup"><span data-stu-id="ee360-191">Loads the data.</span></span>
* <span data-ttu-id="ee360-192">Extrai e transforma os dados.</span><span class="sxs-lookup"><span data-stu-id="ee360-192">Extracts and transforms the data.</span></span>
* <span data-ttu-id="ee360-193">Treina o modelo.</span><span class="sxs-lookup"><span data-stu-id="ee360-193">Trains the model.</span></span>
* <span data-ttu-id="ee360-194">Salva o modelo como um arquivo .zip.</span><span class="sxs-lookup"><span data-stu-id="ee360-194">Saves the model as .zip file.</span></span>
* <span data-ttu-id="ee360-195">Retorna o modelo.</span><span class="sxs-lookup"><span data-stu-id="ee360-195">Returns the model.</span></span>

<span data-ttu-id="ee360-196">O método `Train` treina o modelo.</span><span class="sxs-lookup"><span data-stu-id="ee360-196">The `Train` method trains the model.</span></span> <span data-ttu-id="ee360-197">Crie esse método logo abaixo de `Main`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="ee360-197">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

<span data-ttu-id="ee360-198">Estamos passando dois parâmetros para o método `Train`. Um `MLContext` para o contexto (`mlContext`) e uma cadeia de caracteres para o caminho do conjunto de dados (`dataPath`).</span><span class="sxs-lookup"><span data-stu-id="ee360-198">We are passing two parameters into the `Train` method; an `MLContext` for the context (`mlContext`), and a string for the dataset path (`dataPath`).</span></span> <span data-ttu-id="ee360-199">Vamos reutilizar esse método no carregamento de conjuntos de dados.</span><span class="sxs-lookup"><span data-stu-id="ee360-199">We're going to reuse this method for loading datasets.</span></span>

## <a name="load-and-transform-data"></a><span data-ttu-id="ee360-200">Carregar e transformar dados</span><span class="sxs-lookup"><span data-stu-id="ee360-200">Load and transform data</span></span>

<span data-ttu-id="ee360-201">Carregue os dados, usando o wrapper `MLContext.Data.LoadFromTextFile` do [método LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29).</span><span class="sxs-lookup"><span data-stu-id="ee360-201">Load the data using the `MLContext.Data.LoadFromTextFile` wrapper for the [LoadFromTextFile method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29).</span></span> <span data-ttu-id="ee360-202">Ele retorna um <xref:Microsoft.Data.DataView.IDataView>.</span><span class="sxs-lookup"><span data-stu-id="ee360-202">It returns a <xref:Microsoft.Data.DataView.IDataView>.</span></span> 

<span data-ttu-id="ee360-203">Como a entrada e saída de `Transforms`, um `DataView` é o tipo de pipeline de dados fundamental, comparável ao `IEnumerable` para `LINQ`.</span><span class="sxs-lookup"><span data-stu-id="ee360-203">As the input and output of `Transforms`, a `DataView` is the fundamental data pipeline type, comparable to `IEnumerable` for `LINQ`.</span></span>

<span data-ttu-id="ee360-204">No ML.NET, os dados são semelhantes a um modo de exibição SQL.</span><span class="sxs-lookup"><span data-stu-id="ee360-204">In ML.NET, data is similar to a SQL view.</span></span> <span data-ttu-id="ee360-205">Eles são heterogêneos e avaliados e esquematizados lentamente.</span><span class="sxs-lookup"><span data-stu-id="ee360-205">It is lazily evaluated, schematized, and heterogenous.</span></span> <span data-ttu-id="ee360-206">O objeto é a primeira parte do pipeline e carrega os dados.</span><span class="sxs-lookup"><span data-stu-id="ee360-206">The object is the first part of the pipeline, and loads the data.</span></span> <span data-ttu-id="ee360-207">Para este tutorial, ele carrega um conjunto de dados com informações sobre preços de corridas de táxi.</span><span class="sxs-lookup"><span data-stu-id="ee360-207">For this tutorial, it loads a dataset with taxi trip pricing information.</span></span> <span data-ttu-id="ee360-208">Isso é usado para criar o modelo e treiná-lo.</span><span class="sxs-lookup"><span data-stu-id="ee360-208">This is used to create the model, and train it.</span></span>

<span data-ttu-id="ee360-209">Adicione o seguinte código como a primeira linha do método `Train`:</span><span class="sxs-lookup"><span data-stu-id="ee360-209">Add the following code as the first line of the `Train` method:</span></span>

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "loading training dataset")]

<span data-ttu-id="ee360-210">Nas próximas etapas, trataremos das colunas pelos nomes definidos na classe `TaxiTrip`.</span><span class="sxs-lookup"><span data-stu-id="ee360-210">In the next steps we refer to the columns by the names defined in the `TaxiTrip` class.</span></span>

<span data-ttu-id="ee360-211">Quando o modelo é treinado e avaliado, por padrão, os valores na coluna **Rótulo** são considerados os valores corretos a serem previstos.</span><span class="sxs-lookup"><span data-stu-id="ee360-211">When the model is trained and evaluated, by default, the values in the **Label** column are considered as correct values to be predicted.</span></span> <span data-ttu-id="ee360-212">Como queremos prever a tarifa da viagem de táxi, copie a coluna `FareAmount` para a coluna **Label**.</span><span class="sxs-lookup"><span data-stu-id="ee360-212">As we want to predict the taxi trip fare, copy the `FareAmount` column into the **Label** column.</span></span> <span data-ttu-id="ee360-213">Para fazer isso, use a classe de transformação `CopyColumnsEstimator` e adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="ee360-213">To do that, use the `CopyColumnsEstimator` transformation class, and add the following code:</span></span>

[!code-csharp[CopyColumnsEstimator](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Use the CopyColumnsEstimator")]

<span data-ttu-id="ee360-214">O algoritmo que treina o modelo requer recursos **numéricos**, então, é necessário transformar os valores de dados categóricos (`VendorId`, `RateCode` e `PaymentType`) em números (`VendorIdEncoded`, `RateCodeEncoded` e `PaymentTypeEncoded`).</span><span class="sxs-lookup"><span data-stu-id="ee360-214">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers (`VendorIdEncoded`, `RateCodeEncoded`, and `PaymentTypeEncoded`).</span></span> <span data-ttu-id="ee360-215">Para fazer isso, use a classe de transformação Microsoft.ML.Transforms.OneHotEncodingTransformer>, que atribui valores numéricos de chave diferentes aos valores diferentes em cada uma das colunas, e adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="ee360-215">To do that, use the Microsoft.ML.Transforms.OneHotEncodingTransformer> transformation class, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

[!code-csharp[OneHotEncodingEstimator](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Use the OneHotEncodingEstimator")]

<span data-ttu-id="ee360-216">A última etapa na preparação de dados combina todas as colunas de recursos na coluna **Features** usando a classe de transformação `mlContext.Transforms.Concatenate`.</span><span class="sxs-lookup"><span data-stu-id="ee360-216">The last step in data preparation combines all of the feature columns into the **Features** column using the `mlContext.Transforms.Concatenate` transformation class.</span></span> <span data-ttu-id="ee360-217">Por padrão, um algoritmo de aprendizado processa apenas os recursos da coluna **Features**.</span><span class="sxs-lookup"><span data-stu-id="ee360-217">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="ee360-218">Adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="ee360-218">Add the following code:</span></span>

[!code-csharp[ColumnConcatenatingEstimator](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="ee360-219">Escolher um algoritmo de aprendizado</span><span class="sxs-lookup"><span data-stu-id="ee360-219">Choose a learning algorithm</span></span>

<span data-ttu-id="ee360-220">Após adicionar os dados ao pipeline e transformá-los no formato de entrada correto, escolhemos um algoritmo de aprendizado (**aprendiz**).</span><span class="sxs-lookup"><span data-stu-id="ee360-220">After adding the data to the pipeline and transforming it into the correct input format, we select a learning algorithm (**learner**).</span></span> <span data-ttu-id="ee360-221">O aprendiz treina o modelo.</span><span class="sxs-lookup"><span data-stu-id="ee360-221">The learner trains the model.</span></span> <span data-ttu-id="ee360-222">Escolhemos uma tarefa de **regressão** para esse problema; portanto, usamos um aprendiz `FastTreeRegressionTrainer`, que é um dos aprendizes de regressão fornecidos pelo ML.NET.</span><span class="sxs-lookup"><span data-stu-id="ee360-222">We chose a **regression** task for this problem, so we use a `FastTreeRegressionTrainer` learner, which is one of the regression learners provided by ML.NET.</span></span>

<span data-ttu-id="ee360-223">O algoritmo de treinamento `FastTreeRegressionTrainer` utiliza o gradient boosting.</span><span class="sxs-lookup"><span data-stu-id="ee360-223">The `FastTreeRegressionTrainer` training algorithm utilizes gradient boosting.</span></span> <span data-ttu-id="ee360-224">O aumento de gradiente é uma técnica de aprendizado de máquina para problemas de regressão.</span><span class="sxs-lookup"><span data-stu-id="ee360-224">Gradient boosting is a machine learning technique for regression problems.</span></span> <span data-ttu-id="ee360-225">Ele cria cada árvore de regressão por etapas.</span><span class="sxs-lookup"><span data-stu-id="ee360-225">It builds each regression tree in a step-wise fashion.</span></span> <span data-ttu-id="ee360-226">Ele usa uma função de perda predefinida para medir o erro em cada etapa e corrigi-lo no próximo.</span><span class="sxs-lookup"><span data-stu-id="ee360-226">It uses a pre-defined loss function to measure the error in each step and correct for it in the next.</span></span> <span data-ttu-id="ee360-227">O resultado é um modelo de previsão que é, na verdade, um conjunto de modelos de previsão mais fracos.</span><span class="sxs-lookup"><span data-stu-id="ee360-227">The result is a prediction model that is actually an ensemble of weaker prediction models.</span></span> <span data-ttu-id="ee360-228">Para obter mais informações sobre o aumento de gradiente, consulte [Regressão da árvore de decisão aumentada](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span><span class="sxs-lookup"><span data-stu-id="ee360-228">For more information about gradient boosting, see [Boosted Decision Tree Regression](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span></span>

<span data-ttu-id="ee360-229">Adicione o seguinte código ao método `Train` para adicionar o `FastTreeRegressionTrainer` ao código de processamento de dados adicionado na etapa anterior:</span><span class="sxs-lookup"><span data-stu-id="ee360-229">Add the following code into the `Train` method to add the `FastTreeRegressionTrainer` to the data processing code added in the previous step:</span></span>

[!code-csharp[FastTreeRegressionTrainer](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="ee360-230">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="ee360-230">Train the model</span></span>

<span data-ttu-id="ee360-231">A etapa final é treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="ee360-231">The final step is to train the model.</span></span> <span data-ttu-id="ee360-232">Treinamos o modelo, <xref:Microsoft.ML.Data.TransformerChain>, com base no conjunto de dados que foi carregado e transformado.</span><span class="sxs-lookup"><span data-stu-id="ee360-232">We train the model, <xref:Microsoft.ML.Data.TransformerChain>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="ee360-233">Depois que o avaliador tiver sido definido, treinaremos o modelo usando o <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> e forneceremos os dados de treinamento já carregados.</span><span class="sxs-lookup"><span data-stu-id="ee360-233">Once the estimator has been defined, we train the model using the <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> while providing the already loaded training data.</span></span> <span data-ttu-id="ee360-234">Isso retornará um modelo que será usado nas previsões.</span><span class="sxs-lookup"><span data-stu-id="ee360-234">This returns a model to use for predictions.</span></span> <span data-ttu-id="ee360-235">`pipeline.Fit()` treina o pipeline e retorna um `Transformer` com base no `DataView` passado.</span><span class="sxs-lookup"><span data-stu-id="ee360-235">`pipeline.Fit()` trains the pipeline and returns a `Transformer` based on the `DataView` passed in.</span></span> <span data-ttu-id="ee360-236">O experimento não será executado até que isso ocorra.</span><span class="sxs-lookup"><span data-stu-id="ee360-236">The experiment is not executed until this happens.</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#11 "Train the model")]

### <a name="save-the-model"></a><span data-ttu-id="ee360-237">Salvar o modelo</span><span class="sxs-lookup"><span data-stu-id="ee360-237">Save the model</span></span>

<span data-ttu-id="ee360-238">Neste ponto, você tem um modelo de tipo <xref:Microsoft.ML.Data.TransformerChain> que pode ser integrado em qualquer um dos seus aplicativos .NET existentes ou novos.</span><span class="sxs-lookup"><span data-stu-id="ee360-238">At this point, you have a model of type <xref:Microsoft.ML.Data.TransformerChain> that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="ee360-239">Para salvar o modelo em um arquivo .zip, adicione o seguinte código no final do método `Train`:</span><span class="sxs-lookup"><span data-stu-id="ee360-239">To save the model to a .zip file, add the following code at the end of the `Train` method:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Save the model as a .zip file and return the model")]

## <a name="save-the-model-as-a-zip-file"></a><span data-ttu-id="ee360-240">Salvar o modelo como um arquivo .zip</span><span class="sxs-lookup"><span data-stu-id="ee360-240">Save the model as a .zip file</span></span>

<span data-ttu-id="ee360-241">Crie o método `SaveModelAsFile`, logo após o método `Train`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="ee360-241">Create the `SaveModelAsFile` method, just after the `Train` method, using the following code:</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="ee360-242">O método `SaveModelAsFile` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="ee360-242">The `SaveModelAsFile` method executes the following tasks:</span></span>

* <span data-ttu-id="ee360-243">Salva o modelo como um arquivo .zip.</span><span class="sxs-lookup"><span data-stu-id="ee360-243">Saves the model as a .zip file.</span></span>

<span data-ttu-id="ee360-244">É necessário criar um método para salvar o modelo para que ele possa ser reutilizado e consumido em outros aplicativos.</span><span class="sxs-lookup"><span data-stu-id="ee360-244">We need to create a method to save the model so that it can be reused and consumed in other applications.</span></span> <span data-ttu-id="ee360-245">O `ITransformer` tem um método <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> que usa o campo global `_modelPath` e um <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="ee360-245">The `ITransformer` has a <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> method that takes in the `_modelPath` global field, and a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="ee360-246">Como queremos salvá-lo como um arquivo zip, vamos criar o `FileStream` imediatamente antes de chamar o método `SaveTo`.</span><span class="sxs-lookup"><span data-stu-id="ee360-246">Since we want to save this as a zip file, we'll create the `FileStream` immediately before calling the `SaveTo` method.</span></span> <span data-ttu-id="ee360-247">Adicione o seguinte código ao método `SaveModelAsFile` como a linha seguinte:</span><span class="sxs-lookup"><span data-stu-id="ee360-247">Add the following code to the `SaveModelAsFile` method as the next line:</span></span>

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Add the SaveTo Method")]

<span data-ttu-id="ee360-248">Também poderíamos exibir o local onde o arquivo foi gravado ao gravar uma mensagem de console com o `_modelPath`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="ee360-248">We could also display where the file was written by writing a console message with the `_modelPath`, using the following code:</span></span>

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="evaluate-the-model"></a><span data-ttu-id="ee360-249">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="ee360-249">Evaluate the model</span></span>

<span data-ttu-id="ee360-250">Avaliação é o processo de verificar o quão bem modelo prevê os valores de rótulo.</span><span class="sxs-lookup"><span data-stu-id="ee360-250">Evaluation is the process of checking how well the model predicts label values.</span></span> <span data-ttu-id="ee360-251">É importante que o modelo faça boas previsões com base em dados que não foram usados para treiná-lo.</span><span class="sxs-lookup"><span data-stu-id="ee360-251">It's important that the model makes good predictions on data that was not used to train the model.</span></span> <span data-ttu-id="ee360-252">Uma forma de fazer isso é dividir os dados em conjuntos de dados de treinamento e teste, como neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="ee360-252">One way to do this is to split the data into training and test data sets, as it's done in this tutorial.</span></span> <span data-ttu-id="ee360-253">Agora que você treinou o modelo nos dados de treinamento, pode ver o desempenho dos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="ee360-253">Now that you've trained the model on the training data, you can see how well it performs on the test data.</span></span>

<span data-ttu-id="ee360-254">O método `Evaluate` avalia o modelo.</span><span class="sxs-lookup"><span data-stu-id="ee360-254">The `Evaluate` method evaluates the model.</span></span> <span data-ttu-id="ee360-255">Para criá-lo, adicione o código a seguir abaixo do método `Train`:</span><span class="sxs-lookup"><span data-stu-id="ee360-255">To create that method, add the following code below the `Train` method:</span></span>

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```
<span data-ttu-id="ee360-256">O método `Evaluate` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="ee360-256">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="ee360-257">Carrega o conjunto de dados de teste.</span><span class="sxs-lookup"><span data-stu-id="ee360-257">Loads the test dataset.</span></span>
* <span data-ttu-id="ee360-258">Cria o avaliador de regressão.</span><span class="sxs-lookup"><span data-stu-id="ee360-258">Creates the regression evaluator.</span></span>
* <span data-ttu-id="ee360-259">Avalia o modelo e cria métricas.</span><span class="sxs-lookup"><span data-stu-id="ee360-259">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="ee360-260">Exibe as métricas.</span><span class="sxs-lookup"><span data-stu-id="ee360-260">Displays the metrics.</span></span>

<span data-ttu-id="ee360-261">Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `Train`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="ee360-261">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Call the Evaluate method")]

<span data-ttu-id="ee360-262">Carregar o conjunto de dados de teste usando o wrapper `MLContext.Data.LoadFromTextFile`.</span><span class="sxs-lookup"><span data-stu-id="ee360-262">Load the test dataset using the `MLContext.Data.LoadFromTextFile` wrapper.</span></span> <span data-ttu-id="ee360-263">Você pode avaliar o modelo usando esse conjunto de dados como uma verificação de qualidade.</span><span class="sxs-lookup"><span data-stu-id="ee360-263">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="ee360-264">Adicione o seguinte código ao método `Evaluate`:</span><span class="sxs-lookup"><span data-stu-id="ee360-264">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Load the test dataset")]

<span data-ttu-id="ee360-265">Em seguida, use o parâmetro `model` de aprendizado de máquina (um transformador) para inserir os recursos e retornar previsões.</span><span class="sxs-lookup"><span data-stu-id="ee360-265">Next, use the machine learning `model` parameter (a transformer) to input the features and return predictions.</span></span> <span data-ttu-id="ee360-266">Adicione o seguinte código ao método `Evaluate` como a linha seguinte:</span><span class="sxs-lookup"><span data-stu-id="ee360-266">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Predict using the Transformer")]

<span data-ttu-id="ee360-267">O método `RegressionContext.Evaluate` calcula as métricas de qualidade para o `PredictionModel` usando o conjunto de dados especificado.</span><span class="sxs-lookup"><span data-stu-id="ee360-267">The `RegressionContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="ee360-268">Ele retorna um objeto <xref:Microsoft.ML.Data.RegressionMetrics> que contém as métricas gerais computadas pelos avaliadores de regressão.</span><span class="sxs-lookup"><span data-stu-id="ee360-268">It returns a <xref:Microsoft.ML.Data.RegressionMetrics> object that contains the overall metrics computed by regression evaluators.</span></span> <span data-ttu-id="ee360-269">Para exibi-los a fim de determinar a qualidade do modelo, é preciso primeiro obter as métricas.</span><span class="sxs-lookup"><span data-stu-id="ee360-269">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="ee360-270">Adicione o seguinte código ao método `Evaluate` como a linha seguinte:</span><span class="sxs-lookup"><span data-stu-id="ee360-270">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Compute Metrics")]

<span data-ttu-id="ee360-271">Adicione o seguinte código para avaliar o modelo e produzir as métricas de avaliação:</span><span class="sxs-lookup"><span data-stu-id="ee360-271">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

<span data-ttu-id="ee360-272">[RSquared](../resources/glossary.md#coefficient-of-determination) é outra métrica de avaliação dos modelos de regressão.</span><span class="sxs-lookup"><span data-stu-id="ee360-272">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="ee360-273">RSquared aceita valores entre 0 e 1.</span><span class="sxs-lookup"><span data-stu-id="ee360-273">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="ee360-274">Quanto mais perto de 1 estiver o valor, melhor o modelo será.</span><span class="sxs-lookup"><span data-stu-id="ee360-274">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="ee360-275">Adicione o seguinte código ao método `Evaluate` para exibir o valor RSquared:</span><span class="sxs-lookup"><span data-stu-id="ee360-275">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#18 "Display the RSquared metric.")]

<span data-ttu-id="ee360-276">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) é uma das métricas de avaliação do modelo de regressão.</span><span class="sxs-lookup"><span data-stu-id="ee360-276">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="ee360-277">Quanto menor, melhor o modelo.</span><span class="sxs-lookup"><span data-stu-id="ee360-277">The lower it is, the better the model is.</span></span> <span data-ttu-id="ee360-278">Adicione o seguinte código ao método `Evaluate` para exibir o valor RMS:</span><span class="sxs-lookup"><span data-stu-id="ee360-278">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="ee360-279">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="ee360-279">Use the model for predictions</span></span>


## <a name="predict-the-test-data-outcome-with-the-model-and-a-single-comment"></a><span data-ttu-id="ee360-280">Prever os resultados dos dados de teste com o modelo e um único comentário</span><span class="sxs-lookup"><span data-stu-id="ee360-280">Predict the test data outcome with the model and a single comment</span></span>

<span data-ttu-id="ee360-281">Crie o método `TestSinglePrediction`, logo após o método `Evaluate`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="ee360-281">Create the `TestSinglePrediction` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void TestSinglePrediction(MLContext mlContext)
{

}
```

<span data-ttu-id="ee360-282">O método `TestSinglePrediction` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="ee360-282">The `TestSinglePrediction` method executes the following tasks:</span></span>

* <span data-ttu-id="ee360-283">Cria um único comentário dos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="ee360-283">Creates a single comment of test data.</span></span>
* <span data-ttu-id="ee360-284">Prevê o valor da tarifa com base nos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="ee360-284">Predicts fare amount based on test data.</span></span>
* <span data-ttu-id="ee360-285">Combina dados de teste e previsões para relatórios.</span><span class="sxs-lookup"><span data-stu-id="ee360-285">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="ee360-286">Exibe os resultados previstos.</span><span class="sxs-lookup"><span data-stu-id="ee360-286">Displays the predicted results.</span></span>

<span data-ttu-id="ee360-287">Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `Evaluate`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="ee360-287">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallTestSinglePrediction](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#20 "Call the TestSinglePrediction method")]

<span data-ttu-id="ee360-288">Como queremos carregar o modelo do arquivo zip que foi salvo, vamos criar o `FileStream` imediatamente antes de chamar o método `Load`.</span><span class="sxs-lookup"><span data-stu-id="ee360-288">Since we want to load the model from the zip file we saved, we'll create the `FileStream` immediately before calling the `Load` method.</span></span> <span data-ttu-id="ee360-289">Adicione o seguinte código ao método `TestSinglePrediction` como a linha seguinte:</span><span class="sxs-lookup"><span data-stu-id="ee360-289">Add the following code to the `TestSinglePrediction` method as the next line:</span></span>

[!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#21 "Load the model")]

<span data-ttu-id="ee360-290">Enquanto o `model` é um `transformer` que opera em muitas linhas de dados, um cenário de produção muito comum é a necessidade de previsões em exemplos individuais.</span><span class="sxs-lookup"><span data-stu-id="ee360-290">While the `model` is a `transformer` that operates on many rows of data, a very common production scenario is a need for predictions on individual examples.</span></span> <span data-ttu-id="ee360-291">O <xref:Microsoft.ML.PredictionEngine%602> é um wrapper que é retornado do método `CreatePredictionEngine`.</span><span class="sxs-lookup"><span data-stu-id="ee360-291">The <xref:Microsoft.ML.PredictionEngine%602> is a wrapper that is returned from the `CreatePredictionEngine` method.</span></span> <span data-ttu-id="ee360-292">Adicionaremos o seguinte código para criar `PredictionEngine` como a próxima linha no método `TestSinglePrediction`:</span><span class="sxs-lookup"><span data-stu-id="ee360-292">Let's add the following code to create the `PredictionEngine` as the next line in the `TestSinglePrediction` Method:</span></span>

[!code-csharp[MakePredictionEngine](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#22 "Create the PredictionFunction")]
  
<span data-ttu-id="ee360-293">Este tutorial usa uma viagem de teste dentro dessa classe.</span><span class="sxs-lookup"><span data-stu-id="ee360-293">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="ee360-294">Posteriormente, você pode adicionar outros cenários para fazer experiências com o modelo.</span><span class="sxs-lookup"><span data-stu-id="ee360-294">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="ee360-295">Adicione uma corrida de teste à previsão do modelo treinado no método `TestSinglePrediction` ao criar uma instância de `TaxiTrip`:</span><span class="sxs-lookup"><span data-stu-id="ee360-295">Add a trip to test the trained model's prediction of cost in the `TestSinglePrediction` method by creating an instance of `TaxiTrip`:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#23 "Create test data for single prediction")]

 <span data-ttu-id="ee360-296">Podemos usar isso para prever as tarifas com base em uma única instância dos dados da corrida de táxi.</span><span class="sxs-lookup"><span data-stu-id="ee360-296">We can use that to predict the fare based on a single instance of the taxi trip data.</span></span> <span data-ttu-id="ee360-297">Para obter uma previsão, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> nos dados.</span><span class="sxs-lookup"><span data-stu-id="ee360-297">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="ee360-298">Observe que os dados de entrada são uma cadeia de caracteres e o modelo inclui a personalização.</span><span class="sxs-lookup"><span data-stu-id="ee360-298">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="ee360-299">Seu pipeline está em sincronia durante o treinamento e a previsão.</span><span class="sxs-lookup"><span data-stu-id="ee360-299">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="ee360-300">Você não precisou escrever código de pré-processamento/personalização especificamente para previsões, e a mesma API cuida das previsões de lote e de uso único.</span><span class="sxs-lookup"><span data-stu-id="ee360-300">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#24 "Create a prediction of taxi fare")]

<span data-ttu-id="ee360-301">Para exibir a tarifa prevista da corrida especificada, adicione o código a seguir ao método `TestSinglePrediction`:</span><span class="sxs-lookup"><span data-stu-id="ee360-301">To display the predicted fare of the specified trip, add the following code into the `TestSinglePrediction` method:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#25 "Display the prediction.")]

<span data-ttu-id="ee360-302">Execute o programa para ver a tarifa de táxi prevista para o seu caso de teste.</span><span class="sxs-lookup"><span data-stu-id="ee360-302">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="ee360-303">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="ee360-303">Congratulations!</span></span> <span data-ttu-id="ee360-304">Agora você criou com sucesso um modelo de aprendizado de máquina para prever tarifas de táxi, avaliou sua precisão e o usou para fazer previsões.</span><span class="sxs-lookup"><span data-stu-id="ee360-304">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="ee360-305">Encontre o código-fonte deste tutorial no repositório do GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction).</span><span class="sxs-lookup"><span data-stu-id="ee360-305">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ee360-306">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="ee360-306">Next steps</span></span>

<span data-ttu-id="ee360-307">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="ee360-307">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="ee360-308">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="ee360-308">Understand the problem</span></span>
> * <span data-ttu-id="ee360-309">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="ee360-309">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="ee360-310">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="ee360-310">Prepare and understand the data</span></span>
> * <span data-ttu-id="ee360-311">Criar um pipeline de aprendizado</span><span class="sxs-lookup"><span data-stu-id="ee360-311">Create a learning pipeline</span></span>
> * <span data-ttu-id="ee360-312">Carregar e transformar os dados</span><span class="sxs-lookup"><span data-stu-id="ee360-312">Load and transform the data</span></span>
> * <span data-ttu-id="ee360-313">Escolher um algoritmo de aprendizado</span><span class="sxs-lookup"><span data-stu-id="ee360-313">Choose a learning algorithm</span></span>
> * <span data-ttu-id="ee360-314">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="ee360-314">Train the model</span></span>
> * <span data-ttu-id="ee360-315">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="ee360-315">Evaluate the model</span></span>
> * <span data-ttu-id="ee360-316">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="ee360-316">Use the model for predictions</span></span>

<span data-ttu-id="ee360-317">Avance para o próximo tutorial para saber mais.</span><span class="sxs-lookup"><span data-stu-id="ee360-317">Advance to the next tutorial to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="ee360-318">Clustering de Iris</span><span class="sxs-lookup"><span data-stu-id="ee360-318">Iris clustering</span></span>](iris-clustering.md)
