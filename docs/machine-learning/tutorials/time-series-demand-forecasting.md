---
title: 'Tutorial: Previsão de pressão de bicicletas – série temporal'
description: Este tutorial mostra como prever a demanda por um serviço de aluguel de bicicletas usando análise de série temporal monovariável e ML.NET.
ms.date: 10/31/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: f30aac5f8467c2410e9008bafea3cf35af3f4e2a
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425635"
---
# <a name="tutorial-forecast-bike-rental-service-demand-with-time-series-analysis-and-mlnet"></a><span data-ttu-id="3e2f3-103">Tutorial: prever a demanda de serviço de aluguel de bicicletas com análise de série temporal e ML.NET</span><span class="sxs-lookup"><span data-stu-id="3e2f3-103">Tutorial: Forecast bike rental service demand with time series analysis and ML.NET</span></span>

<span data-ttu-id="3e2f3-104">Saiba como prever a demanda por um serviço de aluguel de bicicletas usando a análise de série temporal monovariável nos dados armazenados em um banco de dados SQL Server com ML.NET.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-104">Learn how to forecast demand for a bike rental service using univariate time series analysis on data stored in a SQL Server database with ML.NET.</span></span>

<span data-ttu-id="3e2f3-105">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="3e2f3-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="3e2f3-106">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="3e2f3-106">Understand the problem</span></span>
> * <span data-ttu-id="3e2f3-107">Carregar dados de um banco</span><span class="sxs-lookup"><span data-stu-id="3e2f3-107">Load data from a database</span></span>
> * <span data-ttu-id="3e2f3-108">Criar um modelo de previsão</span><span class="sxs-lookup"><span data-stu-id="3e2f3-108">Create a forecasting model</span></span>
> * <span data-ttu-id="3e2f3-109">Avaliar modelo de previsão</span><span class="sxs-lookup"><span data-stu-id="3e2f3-109">Evaluate forecasting model</span></span>
> * <span data-ttu-id="3e2f3-110">Salvar um modelo de previsão</span><span class="sxs-lookup"><span data-stu-id="3e2f3-110">Save a forecasting model</span></span>
> * <span data-ttu-id="3e2f3-111">Usar um modelo de previsão</span><span class="sxs-lookup"><span data-stu-id="3e2f3-111">Use a forecasting model</span></span>

> [!NOTE]
> <span data-ttu-id="3e2f3-112">Este tutorial usa uma versão de visualização do DatabaseLoader.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-112">This tutorial uses a preview version of DatabaseLoader.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3e2f3-113">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="3e2f3-113">Prerequisites</span></span>

- <span data-ttu-id="3e2f3-114">[Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-114">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="time-series-forecasting-sample-overview"></a><span data-ttu-id="3e2f3-115">Visão geral de exemplo de previsão de série temporal</span><span class="sxs-lookup"><span data-stu-id="3e2f3-115">Time series forecasting sample overview</span></span>

<span data-ttu-id="3e2f3-116">Este exemplo é um  **C# aplicativo de console .NET Core** que prevê a demanda por locações de bicicletas usando um algoritmo de análise de série temporal monovariável conhecido como análise de espectro único.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-116">This sample is a **C# .NET Core console application** that forecasts demand for bike rentals using a univariate time series analysis algorithm known as Single Spectrum Analysis.</span></span> <span data-ttu-id="3e2f3-117">O código para este exemplo pode ser encontrado no repositório [dotnet/MachineLearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) no github.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-117">The code for this sample can be found on the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) repository on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="3e2f3-118">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="3e2f3-118">Understand the problem</span></span>

<span data-ttu-id="3e2f3-119">Para executar uma operação eficiente, o gerenciamento de inventário desempenha um papel fundamental.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-119">In order to run an efficient operation, inventory management plays a key role.</span></span> <span data-ttu-id="3e2f3-120">Ter muitos produtos em estoque significa que produtos não vendidos nos bastidores não geram receita.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-120">Having too much of a product in stock means unsold products sitting on the shelves not generating any revenue.</span></span> <span data-ttu-id="3e2f3-121">Ter um produto muito pequeno leva a uma perda de vendas e clientes comprando de concorrentes.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-121">Having too little product leads to lost sales and customers purchasing from competitors.</span></span> <span data-ttu-id="3e2f3-122">Portanto, a questão constante é, qual é a quantidade ideal de inventário a ser mantido disponível?</span><span class="sxs-lookup"><span data-stu-id="3e2f3-122">Therefore, the constant question is, what is the optimal amount of inventory to keep on hand?</span></span> <span data-ttu-id="3e2f3-123">A análise de série temporal ajuda a fornecer uma resposta a essas perguntas, examinando os dados históricos, identificando padrões e usando essas informações para prever valores em algum momento no futuro.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-123">Time-series analysis helps provide an answer to these questions by looking at historical data, identifying patterns, and using this information to forecast values some time in the future.</span></span> 

<span data-ttu-id="3e2f3-124">A técnica para analisar dados usados neste tutorial é a análise de série temporal monovariável.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-124">The technique for analyzing data used in this tutorial is univariate time-series analysis.</span></span> <span data-ttu-id="3e2f3-125">A análise da série temporal monovariável examina uma única observação numérica durante um período de tempo em intervalos específicos, como vendas mensais.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-125">Univariate time-series analysis takes a look at a single numerical observation over a period of time at specific intervals such as monthly sales.</span></span> 

<span data-ttu-id="3e2f3-126">O algoritmo usado neste tutorial é [uma análise de espectro único (SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf).</span><span class="sxs-lookup"><span data-stu-id="3e2f3-126">The algorithm used in this tutorial is [Single Spectrum Analysis(SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf).</span></span> <span data-ttu-id="3e2f3-127">O SSA funciona decompondo uma série temporal em um conjunto de componentes principais.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-127">SSA works by decomposing a time-series into a set of principal components.</span></span> <span data-ttu-id="3e2f3-128">Esses componentes podem ser interpretados como as partes de um sinal que correspondem a tendências, ruídos, sazonalidade e muitos outros fatores.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-128">These components can be interpreted as the parts of a signal that correspond to trends, noise, seasonality, and many other factors.</span></span> <span data-ttu-id="3e2f3-129">Em seguida, esses componentes são reconstruídos e usados para prever valores por algum tempo no futuro.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-129">Then, these components are reconstructed and used to forecast values some time in the future.</span></span>

## <a name="create-console-application"></a><span data-ttu-id="3e2f3-130">Criar aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="3e2f3-130">Create console application</span></span>

1. <span data-ttu-id="3e2f3-131">Crie um novo  **C# aplicativo de console .NET Core** chamado "BikeDemandForecasting".</span><span class="sxs-lookup"><span data-stu-id="3e2f3-131">Create a new **C# .NET Core console application** called "BikeDemandForecasting".</span></span>
1. <span data-ttu-id="3e2f3-132">Instalar o pacote NuGet do **Microsoft.ml** versão **1.4.0-Preview2**</span><span class="sxs-lookup"><span data-stu-id="3e2f3-132">Install **Microsoft.ML** version **1.4.0-preview2** NuGet package</span></span>
    1. <span data-ttu-id="3e2f3-133">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-133">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="3e2f3-134">Escolha "nuget.org" como a origem do pacote, selecione a guia **procurar** , procure **Microsoft.ml**.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-134">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="3e2f3-135">Marque a caixa de seleção **incluir pré-lançamento** .</span><span class="sxs-lookup"><span data-stu-id="3e2f3-135">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="3e2f3-136">Selecione o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-136">Select the **Install** button.</span></span>
    1. <span data-ttu-id="3e2f3-137">Selecione o botão **OK** na caixa de diálogo **Visualizar alterações** e, depois, o botão **Aceito** na caixa de diálogo Aceitação da Licença, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-137">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="3e2f3-138">Repita essas etapas para **System. Data. SqlClient** versão **4.7.0**, **Microsoft. ml. experimental** Version **0.16.0-Preview2**e **Microsoft. ml. timeseries** versão **1.4.0-Preview2**.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-138">Repeat these steps for **System.Data.SqlClient** version **4.7.0**, **Microsoft.ML.Experimental** version **0.16.0-preview2**, and **Microsoft.ML.TimeSeries** version **1.4.0-preview2**.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="3e2f3-139">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="3e2f3-139">Prepare and understand the data</span></span>

1. <span data-ttu-id="3e2f3-140">Crie um diretório chamado *Data*.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-140">Create a directory called *Data*.</span></span>
1. <span data-ttu-id="3e2f3-141">Baixe o arquivo de banco de dados [ *DailyDemand. MDF* ](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) e salve-o no diretório *Data* .</span><span class="sxs-lookup"><span data-stu-id="3e2f3-141">Download the [*DailyDemand.mdf* database file](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) and save it to the *Data* directory.</span></span>

> [!NOTE]
> <span data-ttu-id="3e2f3-142">Os dados usados neste tutorial são provenientes do [DataSet de compartilhamento de bicicletas de UCI](https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset).</span><span class="sxs-lookup"><span data-stu-id="3e2f3-142">The data used in this tutorial comes from the [UCI Bike Sharing Dataset](https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset).</span></span> <span data-ttu-id="3e2f3-143">Fanaee-T, Hadi e gama, Joao, ' rotulamento de evento combinando detectores de Ensemble e conhecimento em segundo plano ', progresso em inteligência artificial (2013): PP. 1-15, Springer Berlim Heidelberg, [link da Web](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).</span><span class="sxs-lookup"><span data-stu-id="3e2f3-143">Fanaee-T, Hadi, and Gama, Joao, 'Event labeling combining ensemble detectors and background knowledge', Progress in Artificial Intelligence (2013): pp. 1-15, Springer Berlin Heidelberg, [Web Link](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).</span></span>

<span data-ttu-id="3e2f3-144">O conjunto de conteúdo original contém várias colunas correspondentes ao sazonalidade e ao clima.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-144">The original dataset contains several columns corresponding to seasonality and weather.</span></span> <span data-ttu-id="3e2f3-145">Para resumir e como o algoritmo usado neste tutorial requer apenas os valores de uma única coluna numérica, o conjunto de um original foi condensado para incluir apenas as seguintes colunas:</span><span class="sxs-lookup"><span data-stu-id="3e2f3-145">For brevity and because the algorithm used in this tutorial only requires the values from a single numerical column, the original dataset has been condensed to include only the following columns:</span></span>  

- <span data-ttu-id="3e2f3-146">**dteday**: a data da observação.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-146">**dteday**: The date of the observation.</span></span>
- <span data-ttu-id="3e2f3-147">**year**: o ano codificado da observação (0 = 2011, 1 = 2012).</span><span class="sxs-lookup"><span data-stu-id="3e2f3-147">**year**: The encoded year of the observation (0=2011, 1=2012).</span></span>
- <span data-ttu-id="3e2f3-148">**CNT**: o número total de locações de bicicletas para esse dia.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-148">**cnt**: The total number of bike rentals for that day.</span></span>

<span data-ttu-id="3e2f3-149">O DataSet original é mapeado para uma tabela de banco de dados com o esquema a seguir em um banco de dados SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-149">The original dataset is mapped to a database table with the following schema in a SQL Server database.</span></span>

```SQL
CREATE TABLE [Rentals] (
    [RentalDate] DATE NOT NULL,
    [Year] INT NOT NULL,
    [TotalRentals] INT NOT NULL
);
```

<span data-ttu-id="3e2f3-150">Veja a seguir um exemplo dos dados:</span><span class="sxs-lookup"><span data-stu-id="3e2f3-150">The following is a sample of the data:</span></span>

| <span data-ttu-id="3e2f3-151">RentalDate</span><span class="sxs-lookup"><span data-stu-id="3e2f3-151">RentalDate</span></span> | <span data-ttu-id="3e2f3-152">Ano</span><span class="sxs-lookup"><span data-stu-id="3e2f3-152">Year</span></span> | <span data-ttu-id="3e2f3-153">TotalRentals</span><span class="sxs-lookup"><span data-stu-id="3e2f3-153">TotalRentals</span></span> |
| --- | --- | --- |
|<span data-ttu-id="3e2f3-154">1/1/2011</span><span class="sxs-lookup"><span data-stu-id="3e2f3-154">1/1/2011</span></span>|<span data-ttu-id="3e2f3-155">0</span><span class="sxs-lookup"><span data-stu-id="3e2f3-155">0</span></span>|<span data-ttu-id="3e2f3-156">985</span><span class="sxs-lookup"><span data-stu-id="3e2f3-156">985</span></span>|
|<span data-ttu-id="3e2f3-157">1/2/2011</span><span class="sxs-lookup"><span data-stu-id="3e2f3-157">1/2/2011</span></span>|<span data-ttu-id="3e2f3-158">0</span><span class="sxs-lookup"><span data-stu-id="3e2f3-158">0</span></span>|<span data-ttu-id="3e2f3-159">801</span><span class="sxs-lookup"><span data-stu-id="3e2f3-159">801</span></span>|
|<span data-ttu-id="3e2f3-160">1/3/2011</span><span class="sxs-lookup"><span data-stu-id="3e2f3-160">1/3/2011</span></span>|<span data-ttu-id="3e2f3-161">0</span><span class="sxs-lookup"><span data-stu-id="3e2f3-161">0</span></span>|<span data-ttu-id="3e2f3-162">1349</span><span class="sxs-lookup"><span data-stu-id="3e2f3-162">1349</span></span>|

### <a name="create-input-and-output-classes"></a><span data-ttu-id="3e2f3-163">Criar classes de entrada e saída</span><span class="sxs-lookup"><span data-stu-id="3e2f3-163">Create input and output classes</span></span>

1. <span data-ttu-id="3e2f3-164">Abra o arquivo *Program.cs* e substitua as instruções de `using` existentes pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="3e2f3-164">Open *Program.cs* file and replace the existing `using` statements with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L1-L8)]

1. <span data-ttu-id="3e2f3-165">Criar `ModelInput` classe.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-165">Create `ModelInput` class.</span></span> <span data-ttu-id="3e2f3-166">Abaixo da classe `Program`, adicione o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-166">Below the `Program` class, add the following code.</span></span>

    [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L120-L127)]    

    <span data-ttu-id="3e2f3-167">A classe `ModelInput` contém as seguintes colunas:</span><span class="sxs-lookup"><span data-stu-id="3e2f3-167">The `ModelInput` class contains the following columns:</span></span>

    - <span data-ttu-id="3e2f3-168">**RentalDate**: a data da observação.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-168">**RentalDate**: The date of the observation.</span></span>
    - <span data-ttu-id="3e2f3-169">**Year**: o ano codificado da observação (0 = 2011, 1 = 2012).</span><span class="sxs-lookup"><span data-stu-id="3e2f3-169">**Year**: The encoded year of the observation (0=2011, 1=2012).</span></span>
    - <span data-ttu-id="3e2f3-170">**TotalRentals**: o número total de locações de bicicletas para esse dia.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-170">**TotalRentals**: The total number of bike rentals for that day.</span></span>

1. <span data-ttu-id="3e2f3-171">Crie `ModelOutput` classe abaixo da classe de `ModelInput` recém-criada.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-171">Create `ModelOutput` class below the newly created `ModelInput` class.</span></span>

    [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L129-L136)]

    <span data-ttu-id="3e2f3-172">A classe `ModelOutput` contém as seguintes colunas:</span><span class="sxs-lookup"><span data-stu-id="3e2f3-172">The `ModelOutput` class contains the following columns:</span></span>

    - <span data-ttu-id="3e2f3-173">**ForecastedRentals**: os valores previstos para o período previsto.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-173">**ForecastedRentals**: The predicted values for the forecasted period.</span></span>
    - <span data-ttu-id="3e2f3-174">**LowerBoundRentals**: os valores mínimos previstos para o período previsto.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-174">**LowerBoundRentals**: The predicted minimum values for the forecasted period.</span></span>
    - <span data-ttu-id="3e2f3-175">**UpperBoundRentals**: os valores máximos previstos para o período previsto.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-175">**UpperBoundRentals**: The predicted maximum values for the forecasted period.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="3e2f3-176">Definir caminhos e inicializar variáveis</span><span class="sxs-lookup"><span data-stu-id="3e2f3-176">Define paths and initialize variables</span></span>

1. <span data-ttu-id="3e2f3-177">Dentro do método `Main`, defina variáveis para armazenar o local dos dados, a cadeia de conexão e onde salvar o modelo treinado.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-177">Inside the `Main` method, define variables to store the location of your data, connection string, and where to save the trained model.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L16-L19)]

1. <span data-ttu-id="3e2f3-178">Inicialize a variável `mlContext` com uma nova instância de [`MLContext`](xref:Microsoft.ML.MLContext) adicionando a linha a seguir ao método `Main`.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-178">Initialize the `mlContext` variable with a new instance of [`MLContext`](xref:Microsoft.ML.MLContext) by adding the following line to the `Main` method.</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L21)]

    <span data-ttu-id="3e2f3-179">A classe [`MLContext`](xref:Microsoft.ML.MLContext) é um ponto de partida para todas as operações de ml.net e a inicialização de mlContext cria um novo ambiente ml.NET que pode ser compartilhado entre os objetos de fluxo de trabalho de criação de modelo.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-179">The [`MLContext`](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="3e2f3-180">Ele é semelhante, conceitualmente, a `DBContext` no Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-180">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="3e2f3-181">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="3e2f3-181">Load the data</span></span>

1. <span data-ttu-id="3e2f3-182">Criar `DatabaseLoader` que carrega registros do tipo `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-182">Create `DatabaseLoader` that loads records of type `ModelInput`.</span></span>

    [!code-csharp [CreateDBLoader](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L23)]

1. <span data-ttu-id="3e2f3-183">Defina a consulta para carregar os dados do banco de dado.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-183">Define the query to load the data from the database.</span></span>

    [!code-csharp [DefineSQLQuery](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L25)]

    <span data-ttu-id="3e2f3-184">Os algoritmos ML.NET esperam que os dados sejam do tipo [`Single`](xref:System.Single).</span><span class="sxs-lookup"><span data-stu-id="3e2f3-184">ML.NET algorithms expect data to be of type [`Single`](xref:System.Single).</span></span> <span data-ttu-id="3e2f3-185">Portanto, os valores numéricos provenientes do banco de dados que não são do tipo [`Real`](xref:System.Data.SqlDbType), um valor de ponto flutuante de precisão simples, precisam ser convertidos em [`Real`](xref:System.Data.SqlDbType).</span><span class="sxs-lookup"><span data-stu-id="3e2f3-185">Therefore, numerical values coming from the database that are not of type [`Real`](xref:System.Data.SqlDbType), a single-precision floating-point value, have to be converted to [`Real`](xref:System.Data.SqlDbType).</span></span> 

    <span data-ttu-id="3e2f3-186">As colunas `Year` e `TotalRental` são tipos inteiros no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-186">The `Year` and `TotalRental` columns are both integer types in the database.</span></span> <span data-ttu-id="3e2f3-187">Usando a função interna `CAST`, elas são convertidas para `Real`.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-187">Using the `CAST` built-in function, they are both cast to `Real`.</span></span>

1. <span data-ttu-id="3e2f3-188">Crie um `DatabaseSource` para se conectar ao banco de dados e executar a consulta.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-188">Create a `DatabaseSource` to connect to the database and execute the query.</span></span>

    [!code-csharp [CreateDBSource](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L27-L29)]

1. <span data-ttu-id="3e2f3-189">Carregue os dados em um `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-189">Load the data into an `IDataView`.</span></span>

    [!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L31)]

1. <span data-ttu-id="3e2f3-190">O DataSet contém dois anos de dados.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-190">The dataset contains two years worth of data.</span></span> <span data-ttu-id="3e2f3-191">Somente os dados do primeiro ano são usados para treinamento, o segundo ano é mantido para comparar os valores reais com a previsão produzida pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-191">Only data from the first year is used for training, the second year is held out to compare the actual values against the forecast produced by the model.</span></span> <span data-ttu-id="3e2f3-192">Filtre os dados usando a transformação [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) .</span><span class="sxs-lookup"><span data-stu-id="3e2f3-192">Filter the data using the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) transform.</span></span> 

    [!code-csharp [SplitData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L33-L34)]

    <span data-ttu-id="3e2f3-193">No primeiro ano, somente os valores na coluna `Year` menor que 1 são selecionados definindo o parâmetro `upperBound` como 1.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-193">For the first year, only the values in the `Year` column less than 1 are selected by setting the `upperBound` parameter to 1.</span></span> <span data-ttu-id="3e2f3-194">Por outro lado, no segundo ano, valores maiores ou iguais a 1 são selecionados definindo o parâmetro `lowerBound` como 1.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-194">Conversely, for the second year, values greater than or equal to 1 are selected by setting the `lowerBound` parameter to 1.</span></span>

## <a name="define-time-series-analysis-pipeline"></a><span data-ttu-id="3e2f3-195">Definir pipeline de análise de série temporal</span><span class="sxs-lookup"><span data-stu-id="3e2f3-195">Define time series analysis pipeline</span></span>

1. <span data-ttu-id="3e2f3-196">Defina um pipeline que usa o [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) para prever valores em um conjunto de tempo de série temporal.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-196">Define a pipeline that uses the [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) to forecast values in a time-series dataset.</span></span>

    [!code-csharp [DefinePipeline](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L36-L45)]

    <span data-ttu-id="3e2f3-197">O `forecastingPipeline` leva 365 pontos de dados para o primeiro ano e os exemplos ou divide o conjunto de tempo da série temporal em intervalos de 30 dias (mensais), conforme especificado pelo parâmetro `seriesLength`.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-197">The `forecastingPipeline` takes 365 data points for the first year and samples or splits the time-series dataset into 30-day (monthly) intervals as specified by the `seriesLength` parameter.</span></span> <span data-ttu-id="3e2f3-198">Cada um desses exemplos é analisado por meio de uma janela semanal ou de 7 dias.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-198">Each of these samples is analyzed through weekly or a 7-day window.</span></span> <span data-ttu-id="3e2f3-199">Ao determinar qual é o valor previsto para o próximo período, os valores dos sete dias anteriores são usados para fazer uma previsão.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-199">When determining what the forecasted value for the next period(s) is, the values from previous seven days are used to make a prediction.</span></span> <span data-ttu-id="3e2f3-200">O modelo é definido para prever sete períodos no futuro, conforme definido pelo parâmetro `horizon`.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-200">The model is set to forecast seven periods into the future as defined by the `horizon` parameter.</span></span> <span data-ttu-id="3e2f3-201">Como uma previsão é uma estimativa informada, nem sempre é mais 100% precisa.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-201">Because a forecast is an informed guess, it's not always 100% accurate.</span></span> <span data-ttu-id="3e2f3-202">Portanto, é bom saber o intervalo de valores nos melhores e piores cenários, conforme definido pelos limites superior e inferior.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-202">Therefore, it's good to know the range of values in the best and worst-case scenarios as defined by the upper and lower bounds.</span></span> <span data-ttu-id="3e2f3-203">Nesse caso, o nível de confiança para os limites inferior e superior é definido como 95%.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-203">In this case, the level of confidence for the lower and upper bounds is set to 95%.</span></span> <span data-ttu-id="3e2f3-204">O nível de confiança pode ser aumentado ou diminuído adequadamente.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-204">The confidence level can be increased or decreased accordingly.</span></span> <span data-ttu-id="3e2f3-205">Quanto maior o valor, mais largo o intervalo é entre os limites superior e inferior para obter o nível de confiança desejado.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-205">The higher the value, the wider the range is between the upper and lower bounds to achieve the desired level of confidence.</span></span> 

1. <span data-ttu-id="3e2f3-206">Use o método [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) para treinar o modelo e ajustar os dados ao `forecastingPipeline`definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-206">Use the [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) method to train the model and fit the data to the previously defined `forecastingPipeline`.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L47)]

## <a name="evaluate-the-model"></a><span data-ttu-id="3e2f3-207">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="3e2f3-207">Evaluate the model</span></span>

<span data-ttu-id="3e2f3-208">Avalie como o modelo é executado prevendo os dados do próximo ano e comparando-os com os valores reais.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-208">Evaluate how well the model performs by forecasting next year's data and comparing it against the actual values.</span></span>

1. <span data-ttu-id="3e2f3-209">Abaixo do método `Main`, crie um novo método utilitário chamado `Evaluate`.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-209">Below the `Main` method, create a new utility method called `Evaluate`.</span></span>

    ```csharp
    static void Evaluate(IDataView testData, ITransformer model, MLContext mlContext)
    {
        
    }
    ```

1. <span data-ttu-id="3e2f3-210">Dentro do método `Evaluate`, preveja os dados do segundo ano usando o método [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) com o modelo treinado.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-210">Inside the `Evaluate` method, forecast the second year's data by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method with the trained model.</span></span>

    [!code-csharp [EvaluateForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L62)]

1. <span data-ttu-id="3e2f3-211">Obtenha os valores reais dos dados usando o método [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) .</span><span class="sxs-lookup"><span data-stu-id="3e2f3-211">Get the actual values from the data by using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

    [!code-csharp [GetActualRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L65-L67)]

1. <span data-ttu-id="3e2f3-212">Obtenha os valores de previsão usando o método [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) .</span><span class="sxs-lookup"><span data-stu-id="3e2f3-212">Get the forecast values by using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

    [!code-csharp [GetForecastRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L70-L72)]

1. <span data-ttu-id="3e2f3-213">Calcule a diferença entre os valores real e de previsão, normalmente chamados de erro.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-213">Calculate the difference between the actual and forecast values, commonly referred to as the error.</span></span>

    [!code-csharp [CalculateError](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L75)]

1. <span data-ttu-id="3e2f3-214">Meça o desempenho computando os valores de erro médio de média e de erro no quadrado da média de raiz.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-214">Measure performance by computing the Mean Absolute Error and Root Mean Squared Error values.</span></span>

    [!code-csharp [CalculateMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L78-L79)]

    <span data-ttu-id="3e2f3-215">Para avaliar o desempenho, as seguintes métricas são usadas:</span><span class="sxs-lookup"><span data-stu-id="3e2f3-215">To evaluate performance, the following metrics are used:</span></span>

    - <span data-ttu-id="3e2f3-216">**Erro de média absoluta**: mede como as previsões fechadas são para o valor real.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-216">**Mean Absolute Error**: Measures how close predictions are to the actual value.</span></span> <span data-ttu-id="3e2f3-217">Esse valor varia entre 0 e infinito.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-217">This value ranges between 0 and infinity.</span></span> <span data-ttu-id="3e2f3-218">Quanto mais próximo de 0, melhor a qualidade do modelo.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-218">The closer to 0, the better the quality of the model.</span></span>
    - <span data-ttu-id="3e2f3-219">**Erro de raiz quadrada média**: resume o erro thhe no modelo.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-219">**Root Mean Squared Error**: Summarizes thhe error in the model.</span></span> <span data-ttu-id="3e2f3-220">Esse valor varia entre 0 e infinito.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-220">This value ranges between 0 and infinity.</span></span> <span data-ttu-id="3e2f3-221">Quanto mais próximo de 0, melhor a qualidade do modelo.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-221">The closer to 0, the better the quality of the model.</span></span>

1. <span data-ttu-id="3e2f3-222">Gere as métricas para o console.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-222">Output the metrics to the console.</span></span>

    [!code-csharp [OutputMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L82-L85)]

1. <span data-ttu-id="3e2f3-223">Use o método `Evaluate` dentro do método `Main`.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-223">Use the `Evaluate` method inside the `Main` method.</span></span>

    [!code-csharp [EvaluateModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L49)]

## <a name="save-the-model"></a><span data-ttu-id="3e2f3-224">Salvar o modelo</span><span class="sxs-lookup"><span data-stu-id="3e2f3-224">Save the model</span></span>

<span data-ttu-id="3e2f3-225">Se você estiver satisfeito com seu modelo, salve-o para uso posterior em outros aplicativos.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-225">If you're satisfied with your model, save it for later use in other applications.</span></span>

1. <span data-ttu-id="3e2f3-226">No método `Main`, crie um [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="3e2f3-226">In the `Main` method, create a [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602).</span></span> <span data-ttu-id="3e2f3-227">[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) é um método de conveniência para fazer previsões únicas.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-227">[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) is a convenience method to make single predictions.</span></span>

    [!code-csharp [CreateTimeSeriesEngine](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L51)]

1. <span data-ttu-id="3e2f3-228">Salve o modelo em um arquivo chamado `MLModel.zip` conforme especificado pela variável `modelPath` definida anteriormente.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-228">Save the model to a file called `MLModel.zip` as specified by the previously defined `modelPath` variable.</span></span> <span data-ttu-id="3e2f3-229">Use o método [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) para salvar o modelo.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-229">Use the [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) method to save the model.</span></span>

    [!code-csharp [SaveModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L52)]

## <a name="use-the-model-to-forecast-demand"></a><span data-ttu-id="3e2f3-230">Usar o modelo para prever a demanda</span><span class="sxs-lookup"><span data-stu-id="3e2f3-230">Use the model to forecast demand</span></span>

1. <span data-ttu-id="3e2f3-231">Abaixo do método `Evaluate`, crie um novo método utilitário chamado `Forecast`.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-231">Below the `Evaluate` method, create a new utility method called `Forecast`.</span></span>

    ```csharp
    static void Forecast(IDataView testData, int horizon, TimeSeriesPredictionEngine<ModelInput, ModelOutput> forecaster, MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="3e2f3-232">Dentro do método `Forecast`, use o método [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) para prever locações para os próximos sete dias.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-232">Inside the `Forecast` method, use the [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) method to forecast rentals for the next seven days.</span></span>

    [!code-csharp [SingleForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L91)]

1. <span data-ttu-id="3e2f3-233">Alinhe os valores reais e de previsão por sete períodos.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-233">Align the actual and forecast values for seven periods.</span></span>

    [!code-csharp [GetForecastOutput](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L93-L108)]

1. <span data-ttu-id="3e2f3-234">Itere na saída da previsão e exiba-a no console.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-234">Iterate through the forecast output and display it on the console.</span></span>

    [!code-csharp [DisplayForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L111-L116)]

## <a name="run-the-application"></a><span data-ttu-id="3e2f3-235">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="3e2f3-235">Run the application</span></span>

1. <span data-ttu-id="3e2f3-236">Dentro do método `Main`, chame o método `Forecast`.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-236">Inside the `Main` method, call the `Forecast` method.</span></span>

    [!code-csharp [BuildForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L54)]

1. <span data-ttu-id="3e2f3-237">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-237">Run the application.</span></span> <span data-ttu-id="3e2f3-238">Uma saída semelhante à mostrada abaixo deve aparecer no console do.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-238">Output similar to that below should appear on the console.</span></span> <span data-ttu-id="3e2f3-239">Para resumir, a saída foi condensada.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-239">For brevity, the output has been condensed.</span></span>

    ```text
    Evaluation Metrics
    ---------------------
    Mean Absolute Error: 726.416
    Root Mean Squared Error: 987.658

    Rental Forecast
    ---------------------
    Date: 1/1/2012
    Actual Rentals: 2294
    Lower Estimate: 1197.842
    Forecast: 2334.443
    Upper Estimate: 3471.044

    Date: 1/2/2012
    Actual Rentals: 1951
    Lower Estimate: 1148.412
    Forecast: 2360.861
    Upper Estimate: 3573.309
    ```

<span data-ttu-id="3e2f3-240">A inspeção dos valores reais e previstos mostra as seguintes relações:</span><span class="sxs-lookup"><span data-stu-id="3e2f3-240">Inspection of the actual and forecasted values shows the following relationships:</span></span>

![Comparação real de previsão vs](./media/time-series-demand-forecasting/forecast.png)

<span data-ttu-id="3e2f3-242">Embora os valores previstos não prevejam o número exato de locações, eles fornecem um intervalo mais estreito de valores que permite que uma operação Otimize o uso dos recursos.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-242">While the forecasted values are not predicting the exact number of rentals, they provide a more narrow range of values that allows an operation to optimize their use of resources.</span></span> 

<span data-ttu-id="3e2f3-243">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="3e2f3-243">Congratulations!</span></span> <span data-ttu-id="3e2f3-244">Agora você criou com êxito um modelo de aprendizado de máquina de série temporal para prever a demanda de aluguel de bicicletas.</span><span class="sxs-lookup"><span data-stu-id="3e2f3-244">You've now successfully built a time series machine learning model to forecast bike rental demand.</span></span>

<span data-ttu-id="3e2f3-245">Você pode encontrar o código-fonte deste tutorial no repositório [dotnet/MachineLearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) .</span><span class="sxs-lookup"><span data-stu-id="3e2f3-245">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3e2f3-246">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="3e2f3-246">Next steps</span></span>

- [<span data-ttu-id="3e2f3-247">Tarefas de Machine Learning no ML.NET</span><span class="sxs-lookup"><span data-stu-id="3e2f3-247">Machine learning tasks in ML.NET</span></span>](../resources/tasks.md)
- [<span data-ttu-id="3e2f3-248">Melhorar a precisão do modelo</span><span class="sxs-lookup"><span data-stu-id="3e2f3-248">Improve model accuracy</span></span>](../resources/improve-machine-learning-model-ml-net.md)
