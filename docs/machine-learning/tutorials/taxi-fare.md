---
title: Prever os preços usando um aprendiz de regressão com o ML.NET
description: Prever os preços usando um aprendiz de regressão com o ML.NET.
author: aditidugar
ms.author: johalex
ms.date: 02/08/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 10e0fa2cedff3e31575ad2b9c8bc2d9ecc81f3e8
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092534"
---
# <a name="tutorial-predict-prices-using-a-regression-learner-with-mlnet"></a><span data-ttu-id="c0837-103">Tutorial: Prever os preços usando um aprendiz de regressão com o ML.NET</span><span class="sxs-lookup"><span data-stu-id="c0837-103">Tutorial: Predict prices using a regression learner with ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="c0837-104">Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="c0837-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="c0837-105">Para obter mais informações, confira a [Introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="c0837-105">For more information, see the [ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="c0837-106">Este tutorial ilustra como usar o ML.NET para criar uma [modelo de regressão](../resources/glossary.md#regression) para prever preços. Nesse caso, as tarifas de táxi na cidade de Nova York.</span><span class="sxs-lookup"><span data-stu-id="c0837-106">This tutorial illustrates how to use ML.NET to build a [regression model](../resources/glossary.md#regression) for predicting prices, specifically, New York City taxi fares.</span></span>

<span data-ttu-id="c0837-107">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="c0837-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="c0837-108">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="c0837-108">Understand the problem</span></span>
> * <span data-ttu-id="c0837-109">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="c0837-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="c0837-110">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="c0837-110">Prepare and understand the data</span></span>
> * <span data-ttu-id="c0837-111">Criar um pipeline de aprendizado</span><span class="sxs-lookup"><span data-stu-id="c0837-111">Create a learning pipeline</span></span>
> * <span data-ttu-id="c0837-112">Carregar e transformar os dados</span><span class="sxs-lookup"><span data-stu-id="c0837-112">Load and transform the data</span></span>
> * <span data-ttu-id="c0837-113">Escolher um algoritmo de aprendizado</span><span class="sxs-lookup"><span data-stu-id="c0837-113">Choose a learning algorithm</span></span>
> * <span data-ttu-id="c0837-114">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="c0837-114">Train the model</span></span>
> * <span data-ttu-id="c0837-115">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="c0837-115">Evaluate the model</span></span>
> * <span data-ttu-id="c0837-116">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="c0837-116">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c0837-117">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="c0837-117">Prerequisites</span></span>

* <span data-ttu-id="c0837-118">[Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="c0837-118">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="c0837-119">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="c0837-119">Understand the problem</span></span>

<span data-ttu-id="c0837-120">Este problema trata-se de prever a tarifa de uma viagem de táxi na cidade de Nova York.</span><span class="sxs-lookup"><span data-stu-id="c0837-120">This problem is about predicting the fare of a taxi trip in New York City.</span></span> <span data-ttu-id="c0837-121">À primeira vista, pode parecer que depende simplesmente da distância percorrida.</span><span class="sxs-lookup"><span data-stu-id="c0837-121">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="c0837-122">No entanto, os taxistas em Nova York cobram valores variados por outros fatores, como passageiros adicionais ou pagamento por cartão de crédito em vez de dinheiro.</span><span class="sxs-lookup"><span data-stu-id="c0837-122">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="c0837-123">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="c0837-123">Select the appropriate machine learning task</span></span>

<span data-ttu-id="c0837-124">Convém prever o valor do preço, que é um valor real, com base nos outros fatores no conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="c0837-124">You want to predict the price value, which is a real value, based on the other factors in the data set.</span></span> <span data-ttu-id="c0837-125">Para fazer isso, escolha uma tarefa de aprendizado de máquina de [regressão](../resources/glossary.md#regression).</span><span class="sxs-lookup"><span data-stu-id="c0837-125">To do that you choose a [regression](../resources/glossary.md#regression) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="c0837-126">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="c0837-126">Create a console application</span></span>

1. <span data-ttu-id="c0837-127">Abra o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="c0837-127">Open Visual Studio 2017.</span></span> <span data-ttu-id="c0837-128">Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="c0837-128">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="c0837-129">Na caixa de diálogo **Novo Projeto**, selecione o nó **Visual C#** seguido pelo nó **.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="c0837-129">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="c0837-130">Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="c0837-130">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="c0837-131">Na caixa de texto **Nome**, digite "TaxiFarePrediction" e selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="c0837-131">In the **Name** text box, type "TaxiFarePrediction" and then select the **OK** button.</span></span>

1. <span data-ttu-id="c0837-132">Crie um diretório chamado *Dados* em seu projeto para armazenar o conjunto de dados e os arquivos de modelo:</span><span class="sxs-lookup"><span data-stu-id="c0837-132">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="c0837-133">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Nova Pasta**.</span><span class="sxs-lookup"><span data-stu-id="c0837-133">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="c0837-134">Digite "Data" e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="c0837-134">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="c0837-135">Instale o pacote NuGet **Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="c0837-135">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="c0837-136">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="c0837-136">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="c0837-137">Escolha "nuget.org" como a origem do Pacote, selecione a guia **Procurar**, pesquise **Microsoft.ML**, selecione o pacote na lista e escolha o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="c0837-137">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="c0837-138">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="c0837-138">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="c0837-139">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="c0837-139">Prepare and understand the data</span></span>

1. <span data-ttu-id="c0837-140">Baixe os conjuntos de dados [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) e [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) e salve-os na pasta *Dados* criada na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="c0837-140">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="c0837-141">Esses conjuntos de dados são usados para treinar o modelo de aprendizado de máquina e, em seguida, avaliar a precisão dele.</span><span class="sxs-lookup"><span data-stu-id="c0837-141">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="c0837-142">Esses conjuntos de dados são originalmente do [Conjunto de dados NYC TLC Taxi Trip](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="c0837-142">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

1. <span data-ttu-id="c0837-143">No **Gerenciador de Soluções**, clique com o botão direito do mouse em cada um dos arquivos \*.csv e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="c0837-143">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="c0837-144">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.</span><span class="sxs-lookup"><span data-stu-id="c0837-144">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

1. <span data-ttu-id="c0837-145">Abra o conjunto de dados **taxi-fare-train.csv** e observe os cabeçalhos de coluna na primeira linha.</span><span class="sxs-lookup"><span data-stu-id="c0837-145">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="c0837-146">Dê uma olhada em cada uma das colunas.</span><span class="sxs-lookup"><span data-stu-id="c0837-146">Take a look at each of the columns.</span></span> <span data-ttu-id="c0837-147">Compreenda os dados e decida quais colunas são **recursos** e qual é o **rótulo**.</span><span class="sxs-lookup"><span data-stu-id="c0837-147">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="c0837-148">O **rótulo** é o identificador da coluna que você quer prever.</span><span class="sxs-lookup"><span data-stu-id="c0837-148">The **label** is the identifier of the column you want to predict.</span></span> <span data-ttu-id="c0837-149">Os **recursos** identificados são usados ​​para prever o rótulo.</span><span class="sxs-lookup"><span data-stu-id="c0837-149">The identified **features** are used to predict the label.</span></span>

<span data-ttu-id="c0837-150">O conjunto de dados fornecido contém as seguintes colunas:</span><span class="sxs-lookup"><span data-stu-id="c0837-150">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="c0837-151">**vendor_id:** A ID do taxista é um recurso.</span><span class="sxs-lookup"><span data-stu-id="c0837-151">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="c0837-152">**rate_code:** O tipo de tarifa da corrida de táxi é um recurso.</span><span class="sxs-lookup"><span data-stu-id="c0837-152">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="c0837-153">**passenger_count:** O número de passageiros na corrida é um recurso.</span><span class="sxs-lookup"><span data-stu-id="c0837-153">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="c0837-154">**trip_time_in_secs:** O tempo que levou a corrida.</span><span class="sxs-lookup"><span data-stu-id="c0837-154">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="c0837-155">Você deseja prever a tarifa da viagem antes de sua conclusão.</span><span class="sxs-lookup"><span data-stu-id="c0837-155">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="c0837-156">No momento, você não sabe a duração da viagem.</span><span class="sxs-lookup"><span data-stu-id="c0837-156">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="c0837-157">Portanto, o tempo da viagem não é um recurso e você excluirá essa coluna do modelo.</span><span class="sxs-lookup"><span data-stu-id="c0837-157">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="c0837-158">**trip_distance:** A distância da corrida é um recurso.</span><span class="sxs-lookup"><span data-stu-id="c0837-158">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="c0837-159">**payment_type:** A forma de pagamento (dinheiro ou cartão de crédito) é um recurso.</span><span class="sxs-lookup"><span data-stu-id="c0837-159">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="c0837-160">**fare_amount:** A tarifa total de táxi paga é o rótulo.</span><span class="sxs-lookup"><span data-stu-id="c0837-160">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="c0837-161">Criar classes de dados</span><span class="sxs-lookup"><span data-stu-id="c0837-161">Create data classes</span></span>

<span data-ttu-id="c0837-162">Crie classes para os dados de entrada e as previsões:</span><span class="sxs-lookup"><span data-stu-id="c0837-162">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="c0837-163">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="c0837-163">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="c0837-164">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="c0837-164">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="c0837-165">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="c0837-165">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="c0837-166">Adicione as seguintes diretivas `using` ao novo arquivo:</span><span class="sxs-lookup"><span data-stu-id="c0837-166">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="c0837-167">Remova a definição de classe existente e adicione o seguinte código, que tem duas classes `TaxiTrip` e `TaxiTripFarePrediction`, ao arquivo *TaxiTrip.cs*:</span><span class="sxs-lookup"><span data-stu-id="c0837-167">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="c0837-168">`TaxiTrip` é a classe de dados de entrada e tem definições para cada uma das colunas do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="c0837-168">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="c0837-169">Use o atributo <xref:Microsoft.ML.Data.ColumnAttribute> para especificar os índices das colunas de origem no conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="c0837-169">Use the <xref:Microsoft.ML.Data.ColumnAttribute> attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="c0837-170">A classe `TaxiTripFarePrediction` representa os resultados previstos.</span><span class="sxs-lookup"><span data-stu-id="c0837-170">The `TaxiTripFarePrediction` class represents predicted results.</span></span> <span data-ttu-id="c0837-171">Ela tem um único campo de float, `FareAmount`, com um atributo `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> aplicado.</span><span class="sxs-lookup"><span data-stu-id="c0837-171">It has a single float field, `FareAmount`, with a `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> attribute applied.</span></span> <span data-ttu-id="c0837-172">No caso da tarefa de regressão, a coluna **Pontuação** contém valores de rótulo previsto.</span><span class="sxs-lookup"><span data-stu-id="c0837-172">In case of the regression task the **Score** column contains predicted label values.</span></span>

> [!NOTE]
> <span data-ttu-id="c0837-173">Use o tipo `float` para representar valores de ponto flutuante nas classes de dados de entrada e previsão.</span><span class="sxs-lookup"><span data-stu-id="c0837-173">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="c0837-174">Definir dados e caminhos de modelo</span><span class="sxs-lookup"><span data-stu-id="c0837-174">Define data and model paths</span></span>

<span data-ttu-id="c0837-175">Adicione as seguintes instruções `using` adicionais ao início do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="c0837-175">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="c0837-176">Você precisa criar três campos para conter os caminhos para os arquivos com conjuntos de dados e o arquivo para salvar o modelo e uma variável global para o `TextLoader`:</span><span class="sxs-lookup"><span data-stu-id="c0837-176">You need to create three fields to hold the paths to the files with data sets and the file to save the model, and a global variable for the `TextLoader`:</span></span>

* <span data-ttu-id="c0837-177">`_trainDataPath` contém o caminho para o arquivo com o conjunto de dados usado para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="c0837-177">`_trainDataPath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="c0837-178">`_testDataPath` contém o caminho para o arquivo com o conjunto de dados usado para avaliar o modelo.</span><span class="sxs-lookup"><span data-stu-id="c0837-178">`_testDataPath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="c0837-179">`_modelPath` contém o caminho para o arquivo em que o modelo treinado está armazenado.</span><span class="sxs-lookup"><span data-stu-id="c0837-179">`_modelPath` contains the path to the file where the trained model is stored.</span></span>
* <span data-ttu-id="c0837-180">O `_textLoader` é o <xref:Microsoft.ML.Data.TextLoader> usado para carregar e transformar os conjuntos de dados.</span><span class="sxs-lookup"><span data-stu-id="c0837-180">`_textLoader` is the <xref:Microsoft.ML.Data.TextLoader> used to load and transform the datasets.</span></span>

<span data-ttu-id="c0837-181">Adicione o seguinte código logo acima do método `Main` para especificar estes caminhos e para a variável `_textLoader`:</span><span class="sxs-lookup"><span data-stu-id="c0837-181">Add the following code right above the `Main` method to specify those paths and for the `_textLoader` variable:</span></span>

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="c0837-182">Ao criar um modelo com o ML.NET, comece criando um Contexto de ML.</span><span class="sxs-lookup"><span data-stu-id="c0837-182">When building a model with ML.NET you start by creating an ML Context.</span></span> <span data-ttu-id="c0837-183">Isso é comparável conceitualmente ao uso de `DbContext` no Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="c0837-183">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span> <span data-ttu-id="c0837-184">O ambiente fornece um contexto para seu trabalho de aprendizado de máquina que pode ser usado na exceção do acompanhamento e registro em log.</span><span class="sxs-lookup"><span data-stu-id="c0837-184">The environment provides a context for your machine learning job that can be used for exception tracking and logging.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="c0837-185">Inicializar variáveis em Main</span><span class="sxs-lookup"><span data-stu-id="c0837-185">Initialize variables in Main</span></span>

<span data-ttu-id="c0837-186">Crie uma variável chamada `mlContext` e inicialize-a com uma nova instância de `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="c0837-186">Create a variable called `mlContext` and initialize it with a new instance of `MLContext`.</span></span>  <span data-ttu-id="c0837-187">Substitua a linha `Console.WriteLine("Hello World!")` pelo seguinte código no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="c0837-187">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="c0837-188">Em seguida, para configurar o carregamento de dados, inicialize a variável global `_textLoader` para reutilizá-la.</span><span class="sxs-lookup"><span data-stu-id="c0837-188">Next, to setup for data loading initialize the `_textLoader` global variable in order to reuse it.</span></span> <span data-ttu-id="c0837-189">Quando você cria um `TextLoader`, você passa o contexto necessário e a classe <xref:Microsoft.ML.Data.TextLoader.Arguments> que permite a personalização.</span><span class="sxs-lookup"><span data-stu-id="c0837-189">When you create a `TextLoader`, you pass in the context needed and the <xref:Microsoft.ML.Data.TextLoader.Arguments> class which enables customization.</span></span> <span data-ttu-id="c0837-190">Especifique o esquema de dados passando uma matriz de objetos <xref:Microsoft.ML.Data.TextLoader.Column> para o `TextLoader` que contém todos os nomes de coluna e seus tipos.</span><span class="sxs-lookup"><span data-stu-id="c0837-190">Specify the data schema by passing an array of <xref:Microsoft.ML.Data.TextLoader.Column> objects to the `TextLoader` containing all the column names and their types.</span></span> <span data-ttu-id="c0837-191">Definimos o esquema de dados anteriormente quando criamos nossa classe `TaxiTrip`.</span><span class="sxs-lookup"><span data-stu-id="c0837-191">We defined the data schema previously when we created our `TaxiTrip` class.</span></span>

<span data-ttu-id="c0837-192">A classe `TextLoader` retorna um <xref:Microsoft.ML.Data.TextLoader> completamente inicializado</span><span class="sxs-lookup"><span data-stu-id="c0837-192">The `TextLoader` class returns a fully initialized <xref:Microsoft.ML.Data.TextLoader></span></span>  

<span data-ttu-id="c0837-193">Para inicializar a variável global `_textLoader` para reutilizá-la nos conjuntos de dados necessários, adicione o seguinte código após a inicialização de `mlContext`:</span><span class="sxs-lookup"><span data-stu-id="c0837-193">To initialize the `_textLoader` global variable in order to reuse it for the needed datasets, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[initTextLoader](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Initialize the TextLoader")]

<span data-ttu-id="c0837-194">Adicione o seguinte como a linha seguinte de código no método `Main` para chamar o método `Train`:</span><span class="sxs-lookup"><span data-stu-id="c0837-194">Add the following as the next line of code in the `Main` method to call the `Train` method:</span></span>

[!code-csharp[Train](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Train your model")]

<span data-ttu-id="c0837-195">O método `Train` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="c0837-195">The `Train` method executes the following tasks:</span></span>

* <span data-ttu-id="c0837-196">Carrega os dados.</span><span class="sxs-lookup"><span data-stu-id="c0837-196">Loads the data.</span></span>
* <span data-ttu-id="c0837-197">Extrai e transforma os dados.</span><span class="sxs-lookup"><span data-stu-id="c0837-197">Extracts and transforms the data.</span></span>
* <span data-ttu-id="c0837-198">Treina o modelo.</span><span class="sxs-lookup"><span data-stu-id="c0837-198">Trains the model.</span></span>
* <span data-ttu-id="c0837-199">Salva o modelo como um arquivo .zip.</span><span class="sxs-lookup"><span data-stu-id="c0837-199">Saves the model as .zip file.</span></span>
* <span data-ttu-id="c0837-200">Retorna o modelo.</span><span class="sxs-lookup"><span data-stu-id="c0837-200">Returns the model.</span></span>

<span data-ttu-id="c0837-201">O método `Train` treina o modelo.</span><span class="sxs-lookup"><span data-stu-id="c0837-201">The `Train` method trains the model.</span></span> <span data-ttu-id="c0837-202">Crie esse método logo abaixo de `Main`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="c0837-202">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

<span data-ttu-id="c0837-203">Estamos passando dois parâmetros para o método `Train`. Um `MLContext` para o contexto (`mlContext`) e uma cadeia de caracteres para o caminho do conjunto de dados (`dataPath`).</span><span class="sxs-lookup"><span data-stu-id="c0837-203">We are passing two parameters into the `Train` method; an `MLContext` for the context (`mlContext`), and a string for the dataset path (`dataPath`).</span></span> <span data-ttu-id="c0837-204">Vamos reutilizar esse método no carregamento de conjuntos de dados.</span><span class="sxs-lookup"><span data-stu-id="c0837-204">We're going to reuse this method for loading datasets.</span></span>

## <a name="load-and-transform-data"></a><span data-ttu-id="c0837-205">Carregar e transformar dados</span><span class="sxs-lookup"><span data-stu-id="c0837-205">Load and transform data</span></span>

<span data-ttu-id="c0837-206">Carregaremos os dados usando a variável global `_textLoader` com o parâmetro `dataPath`.</span><span class="sxs-lookup"><span data-stu-id="c0837-206">We'll load the data using the `_textLoader` global variable with the `dataPath` parameter.</span></span> <span data-ttu-id="c0837-207">Ele retorna um <xref:Microsoft.Data.DataView.IDataView>.</span><span class="sxs-lookup"><span data-stu-id="c0837-207">It returns a <xref:Microsoft.Data.DataView.IDataView>.</span></span> <span data-ttu-id="c0837-208">Como a entrada e saída de Transformações, um `IDataView` é o tipo de pipeline de dados fundamental, comparável ao `IEnumerable` para `LINQ`.</span><span class="sxs-lookup"><span data-stu-id="c0837-208">As the input and output of Transforms, an `IDataView` is the fundamental data pipeline type, comparable to `IEnumerable` for `LINQ`.</span></span>

<span data-ttu-id="c0837-209">No ML.NET, os dados são semelhantes a um modo de exibição SQL.</span><span class="sxs-lookup"><span data-stu-id="c0837-209">In ML.NET, data is similar to a SQL view.</span></span> <span data-ttu-id="c0837-210">Eles são heterogêneos e avaliados e esquematizados lentamente.</span><span class="sxs-lookup"><span data-stu-id="c0837-210">It is lazily evaluated, schematized, and heterogenous.</span></span> <span data-ttu-id="c0837-211">O objeto é a primeira parte do pipeline e carrega os dados.</span><span class="sxs-lookup"><span data-stu-id="c0837-211">The object is the first part of the pipeline, and loads the data.</span></span> <span data-ttu-id="c0837-212">Neste tutorial, ele carrega um conjunto de dados com informações úteis sobre a corrida de táxi para prever tarifas.</span><span class="sxs-lookup"><span data-stu-id="c0837-212">For this tutorial, it loads a dataset with taxi trip information useful to predict fares.</span></span> <span data-ttu-id="c0837-213">Isso é usado para criar o modelo e treiná-lo.</span><span class="sxs-lookup"><span data-stu-id="c0837-213">This is used to create the model, and train it.</span></span>

 <span data-ttu-id="c0837-214">Adicione o seguinte código como a primeira linha do método `Train`:</span><span class="sxs-lookup"><span data-stu-id="c0837-214">Add the following code as the first line of the `Train` method:</span></span>

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "loading training dataset")]

<span data-ttu-id="c0837-215">Nas próximas etapas, trataremos das colunas pelos nomes definidos na classe `TaxiTrip`.</span><span class="sxs-lookup"><span data-stu-id="c0837-215">In the next steps we refer to the columns by the names defined in the `TaxiTrip` class.</span></span>

<span data-ttu-id="c0837-216">Quando o modelo é treinado e avaliado, por padrão, os valores na coluna **Rótulo** são considerados os valores corretos a serem previstos.</span><span class="sxs-lookup"><span data-stu-id="c0837-216">When the model is trained and evaluated, by default, the values in the **Label** column are considered as correct values to be predicted.</span></span> <span data-ttu-id="c0837-217">Como queremos prever a tarifa da viagem de táxi, copie a coluna `FareAmount` para a coluna **Label**.</span><span class="sxs-lookup"><span data-stu-id="c0837-217">As we want to predict the taxi trip fare, copy the `FareAmount` column into the **Label** column.</span></span> <span data-ttu-id="c0837-218">Para fazer isso, use a classe de transformação `CopyColumnsEstimator` e adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="c0837-218">To do that, use the `CopyColumnsEstimator` transformation class, and add the following code:</span></span>

[!code-csharp[CopyColumnsEstimator](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Use the CopyColumnsEstimator")]

<span data-ttu-id="c0837-219">O algoritmo que treina o modelo requer recursos **numéricos**, então é necessário transformar os valores de dados categóricos (`VendorId`, `RateCode` e `PaymentType`) em números.</span><span class="sxs-lookup"><span data-stu-id="c0837-219">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers.</span></span> <span data-ttu-id="c0837-220">Para fazer isso, use a classe de transformação `OneHotEncodingEstimator`, que atribui valores numéricos de chave diferentes aos valores diferentes em cada uma das colunas, e adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="c0837-220">To do that, use the `OneHotEncodingEstimator` transformation class, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

[!code-csharp[OneHotEncodingEstimator](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Use the OneHotEncodingEstimator")]

<span data-ttu-id="c0837-221">A última etapa na preparação de dados combina todas as colunas de recursos na coluna **Features** usando a classe de transformação `ColumnConcatenatingEstimator`.</span><span class="sxs-lookup"><span data-stu-id="c0837-221">The last step in data preparation combines all of the feature columns into the **Features** column using the `ColumnConcatenatingEstimator` transformation class.</span></span> <span data-ttu-id="c0837-222">Por padrão, um algoritmo de aprendizado processa apenas os recursos da coluna **Features**.</span><span class="sxs-lookup"><span data-stu-id="c0837-222">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="c0837-223">Adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="c0837-223">Add the following code:</span></span>

[!code-csharp[ColumnConcatenatingEstimator](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="c0837-224">Escolher um algoritmo de aprendizado</span><span class="sxs-lookup"><span data-stu-id="c0837-224">Choose a learning algorithm</span></span>

<span data-ttu-id="c0837-225">Após adicionar os dados ao pipeline e transformá-los no formato de entrada correto, escolhemos um algoritmo de aprendizado (**aprendiz**).</span><span class="sxs-lookup"><span data-stu-id="c0837-225">After adding the data to the pipeline and transforming it into the correct input format, we select a learning algorithm (**learner**).</span></span> <span data-ttu-id="c0837-226">O aprendiz treina o modelo.</span><span class="sxs-lookup"><span data-stu-id="c0837-226">The learner trains the model.</span></span> <span data-ttu-id="c0837-227">Escolhemos uma tarefa de **regressão** para esse problema; portanto, usamos um aprendiz `FastTreeRegressionTrainer`, que é um dos aprendizes de regressão fornecidos pelo ML.NET.</span><span class="sxs-lookup"><span data-stu-id="c0837-227">We chose a **regression** task for this problem, so we use a `FastTreeRegressionTrainer` learner, which is one of the regression learners provided by ML.NET.</span></span>

<span data-ttu-id="c0837-228">O aprendiz `FastTreeRegressionTrainer` utiliza o aumento de gradiente.</span><span class="sxs-lookup"><span data-stu-id="c0837-228">The `FastTreeRegressionTrainer` learner utilizes gradient boosting.</span></span> <span data-ttu-id="c0837-229">O aumento de gradiente é uma técnica de aprendizado de máquina para problemas de regressão.</span><span class="sxs-lookup"><span data-stu-id="c0837-229">Gradient boosting is a machine learning technique for regression problems.</span></span> <span data-ttu-id="c0837-230">Ele cria cada árvore de regressão por etapas.</span><span class="sxs-lookup"><span data-stu-id="c0837-230">It builds each regression tree in a step-wise fashion.</span></span> <span data-ttu-id="c0837-231">Ele usa uma função de perda predefinida para medir o erro em cada etapa e corrigi-lo no próximo.</span><span class="sxs-lookup"><span data-stu-id="c0837-231">It uses a pre-defined loss function to measure the error in each step and correct for it in the next.</span></span> <span data-ttu-id="c0837-232">O resultado é um modelo de previsão que é, na verdade, um conjunto de modelos de previsão mais fracos.</span><span class="sxs-lookup"><span data-stu-id="c0837-232">The result is a prediction model that is actually an ensemble of weaker prediction models.</span></span> <span data-ttu-id="c0837-233">Para obter mais informações sobre o aumento de gradiente, consulte [Regressão da árvore de decisão aumentada](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span><span class="sxs-lookup"><span data-stu-id="c0837-233">For more information about gradient boosting, see [Boosted Decision Tree Regression](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span></span>

<span data-ttu-id="c0837-234">Adicione o seguinte código ao método `Train` para adicionar o `FastTreeRegressionTrainer` ao código de processamento de dados adicionado na etapa anterior:</span><span class="sxs-lookup"><span data-stu-id="c0837-234">Add the following code into the `Train` method to add the `FastTreeRegressionTrainer` to the data processing code added in the previous step:</span></span>

[!code-csharp[FastTreeRegressionTrainer](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="c0837-235">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="c0837-235">Train the model</span></span>

<span data-ttu-id="c0837-236">A etapa final é treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="c0837-236">The final step is to train the model.</span></span> <span data-ttu-id="c0837-237">Treinamos o modelo, <xref:Microsoft.ML.Data.TransformerChain>, com base no conjunto de dados que foi carregado e transformado.</span><span class="sxs-lookup"><span data-stu-id="c0837-237">We train the model, <xref:Microsoft.ML.Data.TransformerChain>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="c0837-238">Depois que o avaliador tiver sido definido, treinaremos o modelo usando o <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> e forneceremos os dados de treinamento já carregados.</span><span class="sxs-lookup"><span data-stu-id="c0837-238">Once the estimator has been defined, we train the model using the <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> while providing the already loaded training data.</span></span> <span data-ttu-id="c0837-239">Isso retornará um modelo que será usado nas previsões.</span><span class="sxs-lookup"><span data-stu-id="c0837-239">This returns a model to use for predictions.</span></span> <span data-ttu-id="c0837-240">`pipeline.Fit()` treina o pipeline e retorna um `Transformer` com base no `DataView` passado.</span><span class="sxs-lookup"><span data-stu-id="c0837-240">`pipeline.Fit()` trains the pipeline and returns a `Transformer` based on the `DataView` passed in.</span></span> <span data-ttu-id="c0837-241">O experimento não será executado até que isso ocorra.</span><span class="sxs-lookup"><span data-stu-id="c0837-241">The experiment is not executed until this happens.</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#11 "Train the model")]

<span data-ttu-id="c0837-242">E pronto.</span><span class="sxs-lookup"><span data-stu-id="c0837-242">And that's it!</span></span> <span data-ttu-id="c0837-243">Você treinou com sucesso um modelo de aprendizado de máquina que pode prever tarifas de táxi em Nova York.</span><span class="sxs-lookup"><span data-stu-id="c0837-243">You have successfully trained a machine learning model that can predict taxi fares in NYC.</span></span> <span data-ttu-id="c0837-244">Agora, vamos entender o nível de precisão do modelo e saber como usá-lo para prever os valores das tarifas de táxi.</span><span class="sxs-lookup"><span data-stu-id="c0837-244">Now let's take a look to understand how accurate the model is and learn how to use it to predict taxi fare values.</span></span>

### <a name="save-the-model"></a><span data-ttu-id="c0837-245">Salvar o modelo</span><span class="sxs-lookup"><span data-stu-id="c0837-245">Save the model</span></span>

<span data-ttu-id="c0837-246">Neste ponto, você tem um modelo de tipo <xref:Microsoft.ML.Data.TransformerChain> que pode ser integrado em qualquer um dos seus aplicativos .NET existentes ou novos.</span><span class="sxs-lookup"><span data-stu-id="c0837-246">At this point, you have a model of type <xref:Microsoft.ML.Data.TransformerChain> that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="c0837-247">Para salvar o modelo em um arquivo .zip, adicione o seguinte código no final do método `Train`:</span><span class="sxs-lookup"><span data-stu-id="c0837-247">To save the model to a .zip file, add the following code at the end of the `Train` method:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Save the model as a .zip file and return the model")]

## <a name="save-the-model-as-a-zip-file"></a><span data-ttu-id="c0837-248">Salvar o modelo como um arquivo .zip</span><span class="sxs-lookup"><span data-stu-id="c0837-248">Save the model as a .zip file</span></span>

<span data-ttu-id="c0837-249">Crie o método `SaveModelAsFile`, logo após o método `Train`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="c0837-249">Create the `SaveModelAsFile` method, just after the `Train` method, using the following code:</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="c0837-250">O método `SaveModelAsFile` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="c0837-250">The `SaveModelAsFile` method executes the following tasks:</span></span>

* <span data-ttu-id="c0837-251">Salva o modelo como um arquivo .zip.</span><span class="sxs-lookup"><span data-stu-id="c0837-251">Saves the model as a .zip file.</span></span>

<span data-ttu-id="c0837-252">É necessário criar um método para salvar o modelo para que ele possa ser reutilizado e consumido em outros aplicativos.</span><span class="sxs-lookup"><span data-stu-id="c0837-252">We need to create a method to save the model so that it can be reused and consumed in other applications.</span></span> <span data-ttu-id="c0837-253">O `ITransformer` tem um método <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> que usa o campo global `_modelPath` e um <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="c0837-253">The `ITransformer` has a <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> method that takes in the `_modelPath` global field, and a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="c0837-254">Como queremos salvá-lo como um arquivo zip, vamos criar o `FileStream` imediatamente antes de chamar o método `SaveTo`.</span><span class="sxs-lookup"><span data-stu-id="c0837-254">Since we want to save this as a zip file, we'll create the `FileStream` immediately before calling the `SaveTo` method.</span></span> <span data-ttu-id="c0837-255">Adicione o seguinte código ao método `SaveModelAsFile` como a linha seguinte:</span><span class="sxs-lookup"><span data-stu-id="c0837-255">Add the following code to the `SaveModelAsFile` method as the next line:</span></span>

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Add the SaveTo Method")]

<span data-ttu-id="c0837-256">Também poderíamos exibir o local onde o arquivo foi gravado ao gravar uma mensagem de console com o `_modelPath`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="c0837-256">We could also display where the file was written by writing a console message with the `_modelPath`, using the following code:</span></span>

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="evaluate-the-model"></a><span data-ttu-id="c0837-257">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="c0837-257">Evaluate the model</span></span>

<span data-ttu-id="c0837-258">Avaliação é o processo de verificar o quão bem modelo prevê os valores de rótulo.</span><span class="sxs-lookup"><span data-stu-id="c0837-258">Evaluation is the process of checking how well the model predicts label values.</span></span> <span data-ttu-id="c0837-259">É importante que o modelo faça boas previsões com base em dados que não foram usados para treiná-lo.</span><span class="sxs-lookup"><span data-stu-id="c0837-259">It's important that the model makes good predictions on data that was not used to train the model.</span></span> <span data-ttu-id="c0837-260">Uma forma de fazer isso é dividir os dados em conjuntos de dados de treinamento e teste, como neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="c0837-260">One way to do this is to split the data into training and test data sets, as it's done in this tutorial.</span></span> <span data-ttu-id="c0837-261">Agora que você treinou o modelo nos dados de treinamento, pode ver o desempenho dos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="c0837-261">Now that you've trained the model on the training data, you can see how well it performs on the test data.</span></span>

<span data-ttu-id="c0837-262">O método `Evaluate` avalia o modelo.</span><span class="sxs-lookup"><span data-stu-id="c0837-262">The `Evaluate` method evaluates the model.</span></span> <span data-ttu-id="c0837-263">Para criá-lo, adicione o código a seguir abaixo do método `Train`:</span><span class="sxs-lookup"><span data-stu-id="c0837-263">To create that method, add the following code below the `Train` method:</span></span>

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```
<span data-ttu-id="c0837-264">O método `Evaluate` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="c0837-264">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="c0837-265">Carrega o conjunto de dados de teste.</span><span class="sxs-lookup"><span data-stu-id="c0837-265">Loads the test dataset.</span></span>
* <span data-ttu-id="c0837-266">Cria o avaliador de regressão.</span><span class="sxs-lookup"><span data-stu-id="c0837-266">Creates the regression evaluator.</span></span>
* <span data-ttu-id="c0837-267">Avalia o modelo e cria métricas.</span><span class="sxs-lookup"><span data-stu-id="c0837-267">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="c0837-268">Exibe as métricas.</span><span class="sxs-lookup"><span data-stu-id="c0837-268">Displays the metrics.</span></span>

<span data-ttu-id="c0837-269">Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `Train`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="c0837-269">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Call the Evaluate method")]

<span data-ttu-id="c0837-270">Carregaremos o conjunto de dados de teste usando a variável global `_textLoader` anteriormente inicializada com o campo global `_testDataPath`.</span><span class="sxs-lookup"><span data-stu-id="c0837-270">We'll load the test dataset using the previously initialized  `_textLoader` global variable with the `_testDataPath` global field.</span></span> <span data-ttu-id="c0837-271">Você pode avaliar o modelo usando esse conjunto de dados como uma verificação de qualidade.</span><span class="sxs-lookup"><span data-stu-id="c0837-271">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="c0837-272">Adicione o seguinte código ao método `Evaluate`:</span><span class="sxs-lookup"><span data-stu-id="c0837-272">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Load the test dataset")]

<span data-ttu-id="c0837-273">Em seguida, usaremos o parâmetro `model` de aprendizado de máquina (um transformador) para inserir os recursos e retornar previsões.</span><span class="sxs-lookup"><span data-stu-id="c0837-273">Next, we'll use the machine learning `model` parameter (a transformer) to input the features and return predictions.</span></span> <span data-ttu-id="c0837-274">Adicione o seguinte código ao método `Evaluate` como a linha seguinte:</span><span class="sxs-lookup"><span data-stu-id="c0837-274">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Predict using the Transformer")]

<span data-ttu-id="c0837-275">O método `RegressionContext.Evaluate` calcula as métricas de qualidade para o `PredictionModel` usando o conjunto de dados especificado.</span><span class="sxs-lookup"><span data-stu-id="c0837-275">The `RegressionContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="c0837-276">Ele retorna um objeto <xref:Microsoft.ML.Data.RegressionMetrics> que contém as métricas gerais computadas pelos avaliadores de regressão.</span><span class="sxs-lookup"><span data-stu-id="c0837-276">It returns a <xref:Microsoft.ML.Data.RegressionMetrics> object that contains the overall metrics computed by regression evaluators.</span></span> <span data-ttu-id="c0837-277">Para exibi-los a fim de determinar a qualidade do modelo, é preciso primeiro obter as métricas.</span><span class="sxs-lookup"><span data-stu-id="c0837-277">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="c0837-278">Adicione o seguinte código ao método `Evaluate` como a linha seguinte:</span><span class="sxs-lookup"><span data-stu-id="c0837-278">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Compute Metrics")]

<span data-ttu-id="c0837-279">Adicione o seguinte código para avaliar o modelo e produzir as métricas de avaliação:</span><span class="sxs-lookup"><span data-stu-id="c0837-279">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

<span data-ttu-id="c0837-280">[RSquared](../resources/glossary.md#coefficient-of-determination) é outra métrica de avaliação dos modelos de regressão.</span><span class="sxs-lookup"><span data-stu-id="c0837-280">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="c0837-281">RSquared aceita valores entre 0 e 1.</span><span class="sxs-lookup"><span data-stu-id="c0837-281">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="c0837-282">Quanto mais perto de 1 estiver o valor, melhor o modelo será.</span><span class="sxs-lookup"><span data-stu-id="c0837-282">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="c0837-283">Adicione o seguinte código ao método `Evaluate` para exibir o valor RSquared:</span><span class="sxs-lookup"><span data-stu-id="c0837-283">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#18 "Display the RSquared metric.")]

<span data-ttu-id="c0837-284">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) é uma das métricas de avaliação do modelo de regressão.</span><span class="sxs-lookup"><span data-stu-id="c0837-284">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="c0837-285">Quanto menor, melhor o modelo.</span><span class="sxs-lookup"><span data-stu-id="c0837-285">The lower it is, the better the model is.</span></span> <span data-ttu-id="c0837-286">Adicione o seguinte código ao método `Evaluate` para exibir o valor RMS:</span><span class="sxs-lookup"><span data-stu-id="c0837-286">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="c0837-287">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="c0837-287">Use the model for predictions</span></span>


## <a name="predict-the-test-data-outcome-with-the-model-and-a-single-comment"></a><span data-ttu-id="c0837-288">Prever os resultados dos dados de teste com o modelo e um único comentário</span><span class="sxs-lookup"><span data-stu-id="c0837-288">Predict the test data outcome with the model and a single comment</span></span>

<span data-ttu-id="c0837-289">Crie o método `TestSinglePrediction`, logo após o método `Evaluate`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="c0837-289">Create the `TestSinglePrediction` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void TestSinglePrediction(MLContext mlContext)
{

}
```

<span data-ttu-id="c0837-290">O método `TestSinglePrediction` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="c0837-290">The `TestSinglePrediction` method executes the following tasks:</span></span>

* <span data-ttu-id="c0837-291">Cria um único comentário dos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="c0837-291">Creates a single comment of test data.</span></span>
* <span data-ttu-id="c0837-292">Prevê o valor da tarifa com base nos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="c0837-292">Predicts fare amount based on test data.</span></span>
* <span data-ttu-id="c0837-293">Combina dados de teste e previsões para relatórios.</span><span class="sxs-lookup"><span data-stu-id="c0837-293">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="c0837-294">Exibe os resultados previstos.</span><span class="sxs-lookup"><span data-stu-id="c0837-294">Displays the predicted results.</span></span>

<span data-ttu-id="c0837-295">Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `Evaluate`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="c0837-295">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallTestSinglePrediction](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#20 "Call the TestSinglePrediction method")]

<span data-ttu-id="c0837-296">Como queremos carregar o modelo do arquivo zip que foi salvo, vamos criar o `FileStream` imediatamente antes de chamar o método `Load`.</span><span class="sxs-lookup"><span data-stu-id="c0837-296">Since we want to load the model from the zip file we saved, we'll create the `FileStream` immediately before calling the `Load` method.</span></span> <span data-ttu-id="c0837-297">Adicione o seguinte código ao método `TestSinglePrediction` como a linha seguinte:</span><span class="sxs-lookup"><span data-stu-id="c0837-297">Add the following code to the `TestSinglePrediction` method as the next line:</span></span>

[!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#21 "Load the model")]

<span data-ttu-id="c0837-298">Enquanto o `model` é um `transformer` que opera em muitas linhas de dados, um cenário de produção muito comum é a necessidade de previsões em exemplos individuais.</span><span class="sxs-lookup"><span data-stu-id="c0837-298">While the `model` is a `transformer` that operates on many rows of data, a very common production scenario is a need for predictions on individual examples.</span></span> <span data-ttu-id="c0837-299">O <xref:Microsoft.ML.PredictionEngine%602> é um wrapper que é retornado do método `CreatePredictionEngine`.</span><span class="sxs-lookup"><span data-stu-id="c0837-299">The <xref:Microsoft.ML.PredictionEngine%602> is a wrapper that is returned from the `CreatePredictionEngine` method.</span></span> <span data-ttu-id="c0837-300">Vamos adicionar o seguinte código para criar `PredictionEngine` como a primeira linha no método `Predict`:</span><span class="sxs-lookup"><span data-stu-id="c0837-300">Let's add the following code to create the `PredictionEngine` as the first line in the `Predict` Method:</span></span>

[!code-csharp[MakePredictionEngine](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#22 "Create the PredictionFunction")]
  
<span data-ttu-id="c0837-301">Este tutorial usa uma viagem de teste dentro dessa classe.</span><span class="sxs-lookup"><span data-stu-id="c0837-301">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="c0837-302">Posteriormente, você pode adicionar outros cenários para fazer experiências com o modelo.</span><span class="sxs-lookup"><span data-stu-id="c0837-302">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="c0837-303">Adicione uma corrida de teste à previsão do modelo treinado no método `Predict` ao criar uma instância de `TaxiTrip`:</span><span class="sxs-lookup"><span data-stu-id="c0837-303">Add a trip to test the trained model's prediction of cost in the `Predict` method by creating an instance of `TaxiTrip`:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#23 "Create test data for single prediction")]

 <span data-ttu-id="c0837-304">Podemos usar isso para prever as tarifas com base em uma única instância dos dados da corrida de táxi.</span><span class="sxs-lookup"><span data-stu-id="c0837-304">We can use that to predict the fare based on a single instance of the taxi trip data.</span></span> <span data-ttu-id="c0837-305">Para obter uma previsão, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> nos dados.</span><span class="sxs-lookup"><span data-stu-id="c0837-305">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="c0837-306">Observe que os dados de entrada são uma cadeia de caracteres e o modelo inclui a personalização.</span><span class="sxs-lookup"><span data-stu-id="c0837-306">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="c0837-307">Seu pipeline está em sincronia durante o treinamento e a previsão.</span><span class="sxs-lookup"><span data-stu-id="c0837-307">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="c0837-308">Você não precisou escrever código de pré-processamento/personalização especificamente para previsões, e a mesma API cuida das previsões de lote e de uso único.</span><span class="sxs-lookup"><span data-stu-id="c0837-308">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#24 "Create a prediction of taxi fare")]

<span data-ttu-id="c0837-309">Para exibir a tarifa prevista da corrida especificada, adicione o código a seguir ao método `Main`:</span><span class="sxs-lookup"><span data-stu-id="c0837-309">To display the predicted fare of the specified trip, add the following code into the `Main` method:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#25 "Display the prediction.")]

<span data-ttu-id="c0837-310">Execute o programa para ver a tarifa de táxi prevista para o seu caso de teste.</span><span class="sxs-lookup"><span data-stu-id="c0837-310">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="c0837-311">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="c0837-311">Congratulations!</span></span> <span data-ttu-id="c0837-312">Agora você criou com sucesso um modelo de aprendizado de máquina para prever tarifas de táxi, avaliou sua precisão e o usou para fazer previsões.</span><span class="sxs-lookup"><span data-stu-id="c0837-312">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="c0837-313">Encontre o código-fonte deste tutorial no repositório do GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction).</span><span class="sxs-lookup"><span data-stu-id="c0837-313">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c0837-314">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="c0837-314">Next steps</span></span>

<span data-ttu-id="c0837-315">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="c0837-315">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="c0837-316">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="c0837-316">Understand the problem</span></span>
> * <span data-ttu-id="c0837-317">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="c0837-317">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="c0837-318">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="c0837-318">Prepare and understand the data</span></span>
> * <span data-ttu-id="c0837-319">Criar um pipeline de aprendizado</span><span class="sxs-lookup"><span data-stu-id="c0837-319">Create a learning pipeline</span></span>
> * <span data-ttu-id="c0837-320">Carregar e transformar os dados</span><span class="sxs-lookup"><span data-stu-id="c0837-320">Load and transform the data</span></span>
> * <span data-ttu-id="c0837-321">Escolher um algoritmo de aprendizado</span><span class="sxs-lookup"><span data-stu-id="c0837-321">Choose a learning algorithm</span></span>
> * <span data-ttu-id="c0837-322">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="c0837-322">Train the model</span></span>
> * <span data-ttu-id="c0837-323">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="c0837-323">Evaluate the model</span></span>
> * <span data-ttu-id="c0837-324">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="c0837-324">Use the model for predictions</span></span>

<span data-ttu-id="c0837-325">Avance para o próximo tutorial para saber mais.</span><span class="sxs-lookup"><span data-stu-id="c0837-325">Advance to the next tutorial to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="c0837-326">Clustering de Iris</span><span class="sxs-lookup"><span data-stu-id="c0837-326">Iris clustering</span></span>](iris-clustering.md)
