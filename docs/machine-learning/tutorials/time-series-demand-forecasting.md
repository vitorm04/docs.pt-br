---
title: 'Tutorial: Previsão de demanda de aluguel de bicicletas - série socorrida'
description: Este tutorial mostra como prever a demanda por um serviço de aluguel de bicicletas usando análise siporida de séries tempois e ML.NET.
ms.date: 11/07/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: 026421d7b1b2a0e39118ae712780ca7fc8f6e444
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76921251"
---
# <a name="tutorial-forecast-bike-rental-service-demand-with-time-series-analysis-and-mlnet"></a><span data-ttu-id="1d512-103">Tutorial: Previsão da demanda de serviço de aluguel de bicicletas com análise de séries tempois e ML.NET</span><span class="sxs-lookup"><span data-stu-id="1d512-103">Tutorial: Forecast bike rental service demand with time series analysis and ML.NET</span></span>

<span data-ttu-id="1d512-104">Saiba como prever a demanda por um serviço de aluguel de bicicletas usando análise de séries tempois univariadas em dados armazenados em um banco de dados do SQL Server com ML.NET.</span><span class="sxs-lookup"><span data-stu-id="1d512-104">Learn how to forecast demand for a bike rental service using univariate time series analysis on data stored in a SQL Server database with ML.NET.</span></span>

<span data-ttu-id="1d512-105">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="1d512-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="1d512-106">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="1d512-106">Understand the problem</span></span>
> * <span data-ttu-id="1d512-107">Carregar dados de um banco de dados</span><span class="sxs-lookup"><span data-stu-id="1d512-107">Load data from a database</span></span>
> * <span data-ttu-id="1d512-108">Crie um modelo de previsão</span><span class="sxs-lookup"><span data-stu-id="1d512-108">Create a forecasting model</span></span>
> * <span data-ttu-id="1d512-109">Avaliar modelo de previsão</span><span class="sxs-lookup"><span data-stu-id="1d512-109">Evaluate forecasting model</span></span>
> * <span data-ttu-id="1d512-110">Salvar um modelo de previsão</span><span class="sxs-lookup"><span data-stu-id="1d512-110">Save a forecasting model</span></span>
> * <span data-ttu-id="1d512-111">Use um modelo de previsão</span><span class="sxs-lookup"><span data-stu-id="1d512-111">Use a forecasting model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1d512-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="1d512-112">Prerequisites</span></span>

- <span data-ttu-id="1d512-113">[Visual Studio 2017 versão 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) com a carga de trabalho ".NET Core cross-platform development" instalada.</span><span class="sxs-lookup"><span data-stu-id="1d512-113">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="time-series-forecasting-sample-overview"></a><span data-ttu-id="1d512-114">Visão geral da amostra da série temporal</span><span class="sxs-lookup"><span data-stu-id="1d512-114">Time series forecasting sample overview</span></span>

<span data-ttu-id="1d512-115">Esta amostra é um **aplicativo de console C# .NET Core** que prevê a demanda por aluguel de bicicletas usando um algoritmo de análise de séries tempois univariado conhecido como Análise de Espectro Único.</span><span class="sxs-lookup"><span data-stu-id="1d512-115">This sample is a **C# .NET Core console application** that forecasts demand for bike rentals using a univariate time series analysis algorithm known as Single Spectrum Analysis.</span></span> <span data-ttu-id="1d512-116">O código para esta amostra pode ser encontrado no repositório [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="1d512-116">The code for this sample can be found on the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) repository on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="1d512-117">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="1d512-117">Understand the problem</span></span>

<span data-ttu-id="1d512-118">Para executar uma operação eficiente, o gerenciamento de estoque desempenha um papel fundamental.</span><span class="sxs-lookup"><span data-stu-id="1d512-118">In order to run an efficient operation, inventory management plays a key role.</span></span> <span data-ttu-id="1d512-119">Ter muito de um produto em estoque significa que produtos não vendidos sentados nas prateleiras não geram nenhuma receita.</span><span class="sxs-lookup"><span data-stu-id="1d512-119">Having too much of a product in stock means unsold products sitting on the shelves not generating any revenue.</span></span> <span data-ttu-id="1d512-120">Ter muito pouco produto leva a vendas perdidas e clientes comprando de concorrentes.</span><span class="sxs-lookup"><span data-stu-id="1d512-120">Having too little product leads to lost sales and customers purchasing from competitors.</span></span> <span data-ttu-id="1d512-121">Portanto, a pergunta constante é: qual é a quantidade ideal de inventário para manter na mão?</span><span class="sxs-lookup"><span data-stu-id="1d512-121">Therefore, the constant question is, what is the optimal amount of inventory to keep on hand?</span></span> <span data-ttu-id="1d512-122">A análise de séries tempois ajuda a fornecer uma resposta a essas perguntas olhando dados históricos, identificando padrões e usando essas informações para prever valores em algum momento no futuro.</span><span class="sxs-lookup"><span data-stu-id="1d512-122">Time-series analysis helps provide an answer to these questions by looking at historical data, identifying patterns, and using this information to forecast values some time in the future.</span></span>

<span data-ttu-id="1d512-123">A técnica para analisar os dados utilizados neste tutorial é a análise univariada da série temporal.</span><span class="sxs-lookup"><span data-stu-id="1d512-123">The technique for analyzing data used in this tutorial is univariate time-series analysis.</span></span> <span data-ttu-id="1d512-124">A análise univariada da série temporal analisa uma única observação numérica durante um período de tempo em intervalos específicos, como vendas mensais.</span><span class="sxs-lookup"><span data-stu-id="1d512-124">Univariate time-series analysis takes a look at a single numerical observation over a period of time at specific intervals such as monthly sales.</span></span>

<span data-ttu-id="1d512-125">O algoritmo usado neste tutorial é [o Single Spectrum Analysis(SSA).](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf)</span><span class="sxs-lookup"><span data-stu-id="1d512-125">The algorithm used in this tutorial is [Single Spectrum Analysis(SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf).</span></span> <span data-ttu-id="1d512-126">A SSA funciona decompondo uma série temporal em um conjunto de componentes principais.</span><span class="sxs-lookup"><span data-stu-id="1d512-126">SSA works by decomposing a time-series into a set of principal components.</span></span> <span data-ttu-id="1d512-127">Esses componentes podem ser interpretados como as partes de um sinal que correspondem a tendências, ruídos, sazonalidade e muitos outros fatores.</span><span class="sxs-lookup"><span data-stu-id="1d512-127">These components can be interpreted as the parts of a signal that correspond to trends, noise, seasonality, and many other factors.</span></span> <span data-ttu-id="1d512-128">Então, esses componentes são reconstruídos e usados para prever valores algum tempo no futuro.</span><span class="sxs-lookup"><span data-stu-id="1d512-128">Then, these components are reconstructed and used to forecast values some time in the future.</span></span>

## <a name="create-console-application"></a><span data-ttu-id="1d512-129">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="1d512-129">Create console application</span></span>

1. <span data-ttu-id="1d512-130">Crie um novo **aplicativo de console C# .NET Core** chamado "BikeDemandForecasting".</span><span class="sxs-lookup"><span data-stu-id="1d512-130">Create a new **C# .NET Core console application** called "BikeDemandForecasting".</span></span>
1. <span data-ttu-id="1d512-131">Instale **Microsoft.ML** versão **1.4.0** NuGet</span><span class="sxs-lookup"><span data-stu-id="1d512-131">Install **Microsoft.ML** version **1.4.0** NuGet package</span></span>
    1. <span data-ttu-id="1d512-132">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="1d512-132">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="1d512-133">Escolha "nuget.org" como fonte do Pacote, selecione a guia **Procurar,** procurar **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="1d512-133">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="1d512-134">Verifique a **caixa de seleção Incluir pré-lançamento.**</span><span class="sxs-lookup"><span data-stu-id="1d512-134">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="1d512-135">Selecione o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="1d512-135">Select the **Install** button.</span></span>
    1. <span data-ttu-id="1d512-136">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo Aceitação da Licença, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="1d512-136">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="1d512-137">Repita estas etapas para **System.Data.SqlClient** versão **4.7.0** e **Microsoft.ML.TimeSeries** versão **1.4.0**.</span><span class="sxs-lookup"><span data-stu-id="1d512-137">Repeat these steps for **System.Data.SqlClient** version **4.7.0** and **Microsoft.ML.TimeSeries** version **1.4.0**.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="1d512-138">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="1d512-138">Prepare and understand the data</span></span>

1. <span data-ttu-id="1d512-139">Crie um diretório chamado *Data*.</span><span class="sxs-lookup"><span data-stu-id="1d512-139">Create a directory called *Data*.</span></span>
1. <span data-ttu-id="1d512-140">Baixe o arquivo de banco de dados [ *DailyDemand.mdf* ](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) e salve-o no diretório *Data.*</span><span class="sxs-lookup"><span data-stu-id="1d512-140">Download the [*DailyDemand.mdf* database file](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) and save it to the *Data* directory.</span></span>

> [!NOTE]
> <span data-ttu-id="1d512-141">Os dados usados neste tutorial vêm do conjunto de dados de compartilhamento de [bicicletas UCI](https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset).</span><span class="sxs-lookup"><span data-stu-id="1d512-141">The data used in this tutorial comes from the [UCI Bike Sharing Dataset](https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset).</span></span> <span data-ttu-id="1d512-142">Fanaee-T, Hadi, e Gama, João, 'Rotulagem de eventos combinando detectores de conjunto e conhecimento de fundo', Progresso em Inteligência Artificial (2013): pp. 1-15, Springer Berlin Heidelberg, [Web Link](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).</span><span class="sxs-lookup"><span data-stu-id="1d512-142">Fanaee-T, Hadi, and Gama, Joao, 'Event labeling combining ensemble detectors and background knowledge', Progress in Artificial Intelligence (2013): pp. 1-15, Springer Berlin Heidelberg, [Web Link](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).</span></span>

<span data-ttu-id="1d512-143">O conjunto de dados original contém várias colunas correspondentes à sazonalidade e ao clima.</span><span class="sxs-lookup"><span data-stu-id="1d512-143">The original dataset contains several columns corresponding to seasonality and weather.</span></span> <span data-ttu-id="1d512-144">Para a brevidade e porque o algoritmo usado neste tutorial requer apenas os valores de uma única coluna numérica, o conjunto de dados original foi condensado para incluir apenas as seguintes colunas:</span><span class="sxs-lookup"><span data-stu-id="1d512-144">For brevity and because the algorithm used in this tutorial only requires the values from a single numerical column, the original dataset has been condensed to include only the following columns:</span></span>

- <span data-ttu-id="1d512-145">**dia dteday**: A data da observação.</span><span class="sxs-lookup"><span data-stu-id="1d512-145">**dteday**: The date of the observation.</span></span>
- <span data-ttu-id="1d512-146">**ano**: O ano codificado da observação (0=2011, 1=2012).</span><span class="sxs-lookup"><span data-stu-id="1d512-146">**year**: The encoded year of the observation (0=2011, 1=2012).</span></span>
- <span data-ttu-id="1d512-147">**cnt**: O número total de aluguel de bicicletas para esse dia.</span><span class="sxs-lookup"><span data-stu-id="1d512-147">**cnt**: The total number of bike rentals for that day.</span></span>

<span data-ttu-id="1d512-148">O conjunto de dados original é mapeado em uma tabela de banco de dados com o seguinte esquema em um banco de dados SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1d512-148">The original dataset is mapped to a database table with the following schema in a SQL Server database.</span></span>

```SQL
CREATE TABLE [Rentals] (
    [RentalDate] DATE NOT NULL,
    [Year] INT NOT NULL,
    [TotalRentals] INT NOT NULL
);
```

<span data-ttu-id="1d512-149">A seguir está uma amostra dos dados:</span><span class="sxs-lookup"><span data-stu-id="1d512-149">The following is a sample of the data:</span></span>

| <span data-ttu-id="1d512-150">Data de aluguel</span><span class="sxs-lookup"><span data-stu-id="1d512-150">RentalDate</span></span> | <span data-ttu-id="1d512-151">Ano</span><span class="sxs-lookup"><span data-stu-id="1d512-151">Year</span></span> | <span data-ttu-id="1d512-152">TotalRentals</span><span class="sxs-lookup"><span data-stu-id="1d512-152">TotalRentals</span></span> |
| --- | --- | --- |
|<span data-ttu-id="1d512-153">1/1/2011</span><span class="sxs-lookup"><span data-stu-id="1d512-153">1/1/2011</span></span>|<span data-ttu-id="1d512-154">0</span><span class="sxs-lookup"><span data-stu-id="1d512-154">0</span></span>|<span data-ttu-id="1d512-155">985</span><span class="sxs-lookup"><span data-stu-id="1d512-155">985</span></span>|
|<span data-ttu-id="1d512-156">1/2/2011</span><span class="sxs-lookup"><span data-stu-id="1d512-156">1/2/2011</span></span>|<span data-ttu-id="1d512-157">0</span><span class="sxs-lookup"><span data-stu-id="1d512-157">0</span></span>|<span data-ttu-id="1d512-158">801</span><span class="sxs-lookup"><span data-stu-id="1d512-158">801</span></span>|
|<span data-ttu-id="1d512-159">1/3/2011</span><span class="sxs-lookup"><span data-stu-id="1d512-159">1/3/2011</span></span>|<span data-ttu-id="1d512-160">0</span><span class="sxs-lookup"><span data-stu-id="1d512-160">0</span></span>|<span data-ttu-id="1d512-161">1349</span><span class="sxs-lookup"><span data-stu-id="1d512-161">1349</span></span>|

### <a name="create-input-and-output-classes"></a><span data-ttu-id="1d512-162">Criar classes de entrada e saída</span><span class="sxs-lookup"><span data-stu-id="1d512-162">Create input and output classes</span></span>

1. <span data-ttu-id="1d512-163">Abra *Program.cs* arquivo e `using` substitua as instruções existentes pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="1d512-163">Open *Program.cs* file and replace the existing `using` statements with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L1-L8)]

1. <span data-ttu-id="1d512-164">Crie a classe `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="1d512-164">Create `ModelInput` class.</span></span> <span data-ttu-id="1d512-165">Abaixo `Program` da classe, adicione o seguinte código.</span><span class="sxs-lookup"><span data-stu-id="1d512-165">Below the `Program` class, add the following code.</span></span>

    [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L120-L127)]

    <span data-ttu-id="1d512-166">A `ModelInput` classe contém as seguintes colunas:</span><span class="sxs-lookup"><span data-stu-id="1d512-166">The `ModelInput` class contains the following columns:</span></span>

    - <span data-ttu-id="1d512-167">**Data de aluguel**: A data da observação.</span><span class="sxs-lookup"><span data-stu-id="1d512-167">**RentalDate**: The date of the observation.</span></span>
    - <span data-ttu-id="1d512-168">**Ano**: Ano codificado da observação (0=2011, 1=2012).</span><span class="sxs-lookup"><span data-stu-id="1d512-168">**Year**: The encoded year of the observation (0=2011, 1=2012).</span></span>
    - <span data-ttu-id="1d512-169">**TotalRentals**: O número total de aluguéis de bicicletas para esse dia.</span><span class="sxs-lookup"><span data-stu-id="1d512-169">**TotalRentals**: The total number of bike rentals for that day.</span></span>

1. <span data-ttu-id="1d512-170">Crie `ModelOutput` classe abaixo da `ModelInput` classe recém-criada.</span><span class="sxs-lookup"><span data-stu-id="1d512-170">Create `ModelOutput` class below the newly created `ModelInput` class.</span></span>

    [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L129-L136)]

    <span data-ttu-id="1d512-171">A `ModelOutput` classe contém as seguintes colunas:</span><span class="sxs-lookup"><span data-stu-id="1d512-171">The `ModelOutput` class contains the following columns:</span></span>

    - <span data-ttu-id="1d512-172">**Preços Previstos**: Os valores previstos para o período previsto.</span><span class="sxs-lookup"><span data-stu-id="1d512-172">**ForecastedRentals**: The predicted values for the forecasted period.</span></span>
    - <span data-ttu-id="1d512-173">**LowerBoundRentals**: Os valores mínimos previstos para o período previsto.</span><span class="sxs-lookup"><span data-stu-id="1d512-173">**LowerBoundRentals**: The predicted minimum values for the forecasted period.</span></span>
    - <span data-ttu-id="1d512-174">**UpperBoundRentals**: Os valores máximos previstos para o período previsto.</span><span class="sxs-lookup"><span data-stu-id="1d512-174">**UpperBoundRentals**: The predicted maximum values for the forecasted period.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="1d512-175">Defina caminhos e inicialize variáveis</span><span class="sxs-lookup"><span data-stu-id="1d512-175">Define paths and initialize variables</span></span>

1. <span data-ttu-id="1d512-176">Dentro `Main` do método, defina variáveis para armazenar a localização de seus dados, string de conexão e onde salvar o modelo treinado.</span><span class="sxs-lookup"><span data-stu-id="1d512-176">Inside the `Main` method, define variables to store the location of your data, connection string, and where to save the trained model.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L16-L19)]

1. <span data-ttu-id="1d512-177">Inicialize `mlContext` a variável com [`MLContext`](xref:Microsoft.ML.MLContext) uma nova instância de `Main` adicionando a seguinte linha ao método.</span><span class="sxs-lookup"><span data-stu-id="1d512-177">Initialize the `mlContext` variable with a new instance of [`MLContext`](xref:Microsoft.ML.MLContext) by adding the following line to the `Main` method.</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L21)]

    <span data-ttu-id="1d512-178">A [`MLContext`](xref:Microsoft.ML.MLContext) classe é um ponto de partida para todas as operações ML.NET, e a inicialização do mlContext cria um novo ambiente ML.NET que pode ser compartilhado entre os objetos do fluxo de trabalho de criação de modelos.</span><span class="sxs-lookup"><span data-stu-id="1d512-178">The [`MLContext`](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="1d512-179">Ele é semelhante, conceitualmente, a `DBContext` no Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="1d512-179">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="1d512-180">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="1d512-180">Load the data</span></span>

1. <span data-ttu-id="1d512-181">Criar `DatabaseLoader` que carrega registros `ModelInput`do tipo .</span><span class="sxs-lookup"><span data-stu-id="1d512-181">Create `DatabaseLoader` that loads records of type `ModelInput`.</span></span>

    [!code-csharp [CreateDBLoader](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L23)]

1. <span data-ttu-id="1d512-182">Defina a consulta para carregar os dados do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="1d512-182">Define the query to load the data from the database.</span></span>

    [!code-csharp [DefineSQLQuery](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L25)]

    <span data-ttu-id="1d512-183">ML.NET algoritmos esperam que [`Single`](xref:System.Single)os dados sejam do tipo .</span><span class="sxs-lookup"><span data-stu-id="1d512-183">ML.NET algorithms expect data to be of type [`Single`](xref:System.Single).</span></span> <span data-ttu-id="1d512-184">Portanto, valores numéricos provenientes do banco [`Real`](xref:System.Data.SqlDbType)de dados que não são do tipo , [`Real`](xref:System.Data.SqlDbType)um valor de ponto flutuante de precisão única, devem ser convertidos para .</span><span class="sxs-lookup"><span data-stu-id="1d512-184">Therefore, numerical values coming from the database that are not of type [`Real`](xref:System.Data.SqlDbType), a single-precision floating-point value, have to be converted to [`Real`](xref:System.Data.SqlDbType).</span></span>

    <span data-ttu-id="1d512-185">As `Year` `TotalRental` colunas e colunas são tipos inteiros no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="1d512-185">The `Year` and `TotalRental` columns are both integer types in the database.</span></span> <span data-ttu-id="1d512-186">Usando `CAST` a função incorporada, ambos são `Real`lançados para .</span><span class="sxs-lookup"><span data-stu-id="1d512-186">Using the `CAST` built-in function, they are both cast to `Real`.</span></span>

1. <span data-ttu-id="1d512-187">Crie `DatabaseSource` um para se conectar ao banco de dados e execute a consulta.</span><span class="sxs-lookup"><span data-stu-id="1d512-187">Create a `DatabaseSource` to connect to the database and execute the query.</span></span>

    [!code-csharp [CreateDBSource](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L27-L29)]

1. <span data-ttu-id="1d512-188">Carregar os dados em um `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="1d512-188">Load the data into an `IDataView`.</span></span>

    [!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L31)]

1. <span data-ttu-id="1d512-189">O conjunto de dados contém dois anos de dados.</span><span class="sxs-lookup"><span data-stu-id="1d512-189">The dataset contains two years worth of data.</span></span> <span data-ttu-id="1d512-190">Apenas os dados do primeiro ano são utilizados para a formação, o segundo ano é realizado para comparar os valores reais com a previsão produzida pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="1d512-190">Only data from the first year is used for training, the second year is held out to compare the actual values against the forecast produced by the model.</span></span> <span data-ttu-id="1d512-191">Filtre os [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) dados usando a transformação.</span><span class="sxs-lookup"><span data-stu-id="1d512-191">Filter the data using the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) transform.</span></span>

    [!code-csharp [SplitData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L33-L34)]

    <span data-ttu-id="1d512-192">Para o primeiro ano, apenas `Year` os valores da coluna `upperBound` inferior a 1 são selecionados definindo o parâmetro para 1.</span><span class="sxs-lookup"><span data-stu-id="1d512-192">For the first year, only the values in the `Year` column less than 1 are selected by setting the `upperBound` parameter to 1.</span></span> <span data-ttu-id="1d512-193">Por outro lado, para o segundo ano, valores maiores ou iguais a 1 são selecionados definindo o `lowerBound` parâmetro para 1.</span><span class="sxs-lookup"><span data-stu-id="1d512-193">Conversely, for the second year, values greater than or equal to 1 are selected by setting the `lowerBound` parameter to 1.</span></span>

## <a name="define-time-series-analysis-pipeline"></a><span data-ttu-id="1d512-194">Definir pipeline de análise de séries tempois</span><span class="sxs-lookup"><span data-stu-id="1d512-194">Define time series analysis pipeline</span></span>

1. <span data-ttu-id="1d512-195">Defina um pipeline que usa o [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) para prever valores em um conjunto de dados em série stempo.</span><span class="sxs-lookup"><span data-stu-id="1d512-195">Define a pipeline that uses the [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) to forecast values in a time-series dataset.</span></span>

    [!code-csharp [DefinePipeline](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L36-L45)]

    <span data-ttu-id="1d512-196">O `forecastingPipeline` conjunto de dados leva 365 pontos de dados para o primeiro ano e amostra ou divide o `seriesLength` conjunto de dados da série temporal em intervalos de 30 dias (mensais), conforme especificado pelo parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1d512-196">The `forecastingPipeline` takes 365 data points for the first year and samples or splits the time-series dataset into 30-day (monthly) intervals as specified by the `seriesLength` parameter.</span></span> <span data-ttu-id="1d512-197">Cada uma dessas amostras é analisada por uma janela semanal ou de 7 dias.</span><span class="sxs-lookup"><span data-stu-id="1d512-197">Each of these samples is analyzed through weekly or a 7-day window.</span></span> <span data-ttu-id="1d512-198">Ao determinar qual é o valor previsto para o próximo período, os valores dos sete dias anteriores são usados para fazer uma previsão.</span><span class="sxs-lookup"><span data-stu-id="1d512-198">When determining what the forecasted value for the next period(s) is, the values from previous seven days are used to make a prediction.</span></span> <span data-ttu-id="1d512-199">O modelo prevê sete períodos no futuro, `horizon` conforme definido pelo parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1d512-199">The model is set to forecast seven periods into the future as defined by the `horizon` parameter.</span></span> <span data-ttu-id="1d512-200">Como uma previsão é um palpite, nem sempre é 100% precisa.</span><span class="sxs-lookup"><span data-stu-id="1d512-200">Because a forecast is an informed guess, it's not always 100% accurate.</span></span> <span data-ttu-id="1d512-201">Portanto, é bom conhecer a gama de valores nos melhores e piores cenários, conforme definido pelos limites superior e inferior.</span><span class="sxs-lookup"><span data-stu-id="1d512-201">Therefore, it's good to know the range of values in the best and worst-case scenarios as defined by the upper and lower bounds.</span></span> <span data-ttu-id="1d512-202">Neste caso, o nível de confiança para os limites inferior e superior é definido para 95%.</span><span class="sxs-lookup"><span data-stu-id="1d512-202">In this case, the level of confidence for the lower and upper bounds is set to 95%.</span></span> <span data-ttu-id="1d512-203">O nível de confiança pode ser aumentado ou diminuído em conformidade.</span><span class="sxs-lookup"><span data-stu-id="1d512-203">The confidence level can be increased or decreased accordingly.</span></span> <span data-ttu-id="1d512-204">Quanto maior o valor, maior a faixa entre os limites superior e inferior para alcançar o nível de confiança desejado.</span><span class="sxs-lookup"><span data-stu-id="1d512-204">The higher the value, the wider the range is between the upper and lower bounds to achieve the desired level of confidence.</span></span>

1. <span data-ttu-id="1d512-205">Use [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) o método para treinar o modelo e `forecastingPipeline`encaixar os dados no previamente definido .</span><span class="sxs-lookup"><span data-stu-id="1d512-205">Use the [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) method to train the model and fit the data to the previously defined `forecastingPipeline`.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L47)]

## <a name="evaluate-the-model"></a><span data-ttu-id="1d512-206">Avalie o modelo</span><span class="sxs-lookup"><span data-stu-id="1d512-206">Evaluate the model</span></span>

<span data-ttu-id="1d512-207">Avalie o desempenho do modelo, prevendo os dados do próximo ano e comparando-os com os valores reais.</span><span class="sxs-lookup"><span data-stu-id="1d512-207">Evaluate how well the model performs by forecasting next year's data and comparing it against the actual values.</span></span>

1. <span data-ttu-id="1d512-208">Abaixo `Main` do método, crie um `Evaluate`novo método de utilidade chamado .</span><span class="sxs-lookup"><span data-stu-id="1d512-208">Below the `Main` method, create a new utility method called `Evaluate`.</span></span>

    ```csharp
    static void Evaluate(IDataView testData, ITransformer model, MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="1d512-209">Dentro `Evaluate` do método, preveja os dados [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) do segundo ano utilizando o método com o modelo treinado.</span><span class="sxs-lookup"><span data-stu-id="1d512-209">Inside the `Evaluate` method, forecast the second year's data by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method with the trained model.</span></span>

    [!code-csharp [EvaluateForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L62)]

1. <span data-ttu-id="1d512-210">Obtenha os valores reais a [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) partir dos dados usando o método.</span><span class="sxs-lookup"><span data-stu-id="1d512-210">Get the actual values from the data by using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

    [!code-csharp [GetActualRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L65-L67)]

1. <span data-ttu-id="1d512-211">Obtenha os valores [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) de previsão usando o método.</span><span class="sxs-lookup"><span data-stu-id="1d512-211">Get the forecast values by using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

    [!code-csharp [GetForecastRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L70-L72)]

1. <span data-ttu-id="1d512-212">Calcule a diferença entre os valores reais e de previsão, comumente referido como erro.</span><span class="sxs-lookup"><span data-stu-id="1d512-212">Calculate the difference between the actual and forecast values, commonly referred to as the error.</span></span>

    [!code-csharp [CalculateError](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L75)]

1. <span data-ttu-id="1d512-213">Medir o desempenho calculando os valores de erro absoluto médio e erro quadrado de média raiz.</span><span class="sxs-lookup"><span data-stu-id="1d512-213">Measure performance by computing the Mean Absolute Error and Root Mean Squared Error values.</span></span>

    [!code-csharp [CalculateMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L78-L79)]

    <span data-ttu-id="1d512-214">Para avaliar o desempenho, são utilizadas as seguintes métricas:</span><span class="sxs-lookup"><span data-stu-id="1d512-214">To evaluate performance, the following metrics are used:</span></span>

    - <span data-ttu-id="1d512-215">**Erro Absoluto Médio**: Mede o quão próximas as previsões são do valor real.</span><span class="sxs-lookup"><span data-stu-id="1d512-215">**Mean Absolute Error**: Measures how close predictions are to the actual value.</span></span> <span data-ttu-id="1d512-216">Este valor varia entre 0 e infinito.</span><span class="sxs-lookup"><span data-stu-id="1d512-216">This value ranges between 0 and infinity.</span></span> <span data-ttu-id="1d512-217">Quanto mais perto de 0, melhor a qualidade do modelo.</span><span class="sxs-lookup"><span data-stu-id="1d512-217">The closer to 0, the better the quality of the model.</span></span>
    - <span data-ttu-id="1d512-218">**Erro quadrado de média raiz**: resume o erro no modelo.</span><span class="sxs-lookup"><span data-stu-id="1d512-218">**Root Mean Squared Error**: Summarizes the error in the model.</span></span> <span data-ttu-id="1d512-219">Este valor varia entre 0 e infinito.</span><span class="sxs-lookup"><span data-stu-id="1d512-219">This value ranges between 0 and infinity.</span></span> <span data-ttu-id="1d512-220">Quanto mais perto de 0, melhor a qualidade do modelo.</span><span class="sxs-lookup"><span data-stu-id="1d512-220">The closer to 0, the better the quality of the model.</span></span>

1. <span data-ttu-id="1d512-221">Saída as métricas para o console.</span><span class="sxs-lookup"><span data-stu-id="1d512-221">Output the metrics to the console.</span></span>

    [!code-csharp [OutputMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L82-L85)]

1. <span data-ttu-id="1d512-222">Use `Evaluate` o método `Main` dentro do método.</span><span class="sxs-lookup"><span data-stu-id="1d512-222">Use the `Evaluate` method inside the `Main` method.</span></span>

    [!code-csharp [EvaluateModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L49)]

## <a name="save-the-model"></a><span data-ttu-id="1d512-223">Salvar o modelo</span><span class="sxs-lookup"><span data-stu-id="1d512-223">Save the model</span></span>

<span data-ttu-id="1d512-224">Se você estiver satisfeito com o seu modelo, guarde-o para uso posterior em outros aplicativos.</span><span class="sxs-lookup"><span data-stu-id="1d512-224">If you're satisfied with your model, save it for later use in other applications.</span></span>

1. <span data-ttu-id="1d512-225">No `Main` método, crie [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602)um .</span><span class="sxs-lookup"><span data-stu-id="1d512-225">In the `Main` method, create a [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602).</span></span> <span data-ttu-id="1d512-226">[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602)é um método de conveniência para fazer previsões únicas.</span><span class="sxs-lookup"><span data-stu-id="1d512-226">[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) is a convenience method to make single predictions.</span></span>

    [!code-csharp [CreateTimeSeriesEngine](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L51)]

1. <span data-ttu-id="1d512-227">Salve o modelo em `MLModel.zip` um arquivo chamado conforme `modelPath` especificado pela variável previamente definida.</span><span class="sxs-lookup"><span data-stu-id="1d512-227">Save the model to a file called `MLModel.zip` as specified by the previously defined `modelPath` variable.</span></span> <span data-ttu-id="1d512-228">Use [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) o método para salvar o modelo.</span><span class="sxs-lookup"><span data-stu-id="1d512-228">Use the [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) method to save the model.</span></span>

    [!code-csharp [SaveModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L52)]

## <a name="use-the-model-to-forecast-demand"></a><span data-ttu-id="1d512-229">Use o modelo para prever a demanda</span><span class="sxs-lookup"><span data-stu-id="1d512-229">Use the model to forecast demand</span></span>

1. <span data-ttu-id="1d512-230">Abaixo `Evaluate` do método, crie um `Forecast`novo método de utilidade chamado .</span><span class="sxs-lookup"><span data-stu-id="1d512-230">Below the `Evaluate` method, create a new utility method called `Forecast`.</span></span>

    ```csharp
    static void Forecast(IDataView testData, int horizon, TimeSeriesPredictionEngine<ModelInput, ModelOutput> forecaster, MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="1d512-231">Dentro `Forecast` do método, [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) use o método para prever aluguéis para os próximos sete dias.</span><span class="sxs-lookup"><span data-stu-id="1d512-231">Inside the `Forecast` method, use the [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) method to forecast rentals for the next seven days.</span></span>

    [!code-csharp [SingleForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L91)]

1. <span data-ttu-id="1d512-232">Alinhar os valores reais e de previsão para sete períodos.</span><span class="sxs-lookup"><span data-stu-id="1d512-232">Align the actual and forecast values for seven periods.</span></span>

    [!code-csharp [GetForecastOutput](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L93-L108)]

1. <span data-ttu-id="1d512-233">Iterar através da saída de previsão e exibi-lo no console.</span><span class="sxs-lookup"><span data-stu-id="1d512-233">Iterate through the forecast output and display it on the console.</span></span>

    [!code-csharp [DisplayForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L111-L116)]

## <a name="run-the-application"></a><span data-ttu-id="1d512-234">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="1d512-234">Run the application</span></span>

1. <span data-ttu-id="1d512-235">Dentro `Main` do método, `Forecast` chame o método.</span><span class="sxs-lookup"><span data-stu-id="1d512-235">Inside the `Main` method, call the `Forecast` method.</span></span>

    [!code-csharp [BuildForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L54)]

1. <span data-ttu-id="1d512-236">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1d512-236">Run the application.</span></span> <span data-ttu-id="1d512-237">Saída semelhante à abaixo deve aparecer no console.</span><span class="sxs-lookup"><span data-stu-id="1d512-237">Output similar to that below should appear on the console.</span></span> <span data-ttu-id="1d512-238">Para a brevidade, a saída foi condensada.</span><span class="sxs-lookup"><span data-stu-id="1d512-238">For brevity, the output has been condensed.</span></span>

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

<span data-ttu-id="1d512-239">A inspeção dos valores reais e previstos mostra as seguintes relações:</span><span class="sxs-lookup"><span data-stu-id="1d512-239">Inspection of the actual and forecasted values shows the following relationships:</span></span>

![Comparação real vs previsão](./media/time-series-demand-forecasting/forecast.png)

<span data-ttu-id="1d512-241">Embora os valores previstos não estejam prevendo o número exato de aluguéis, eles fornecem uma faixa mais estreita de valores que permite uma operação para otimizar seu uso de recursos.</span><span class="sxs-lookup"><span data-stu-id="1d512-241">While the forecasted values are not predicting the exact number of rentals, they provide a more narrow range of values that allows an operation to optimize their use of resources.</span></span>

<span data-ttu-id="1d512-242">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="1d512-242">Congratulations!</span></span> <span data-ttu-id="1d512-243">Agora você construiu com sucesso um modelo de aprendizado de máquina de séries temporias para prever a demanda de aluguel de bicicletas.</span><span class="sxs-lookup"><span data-stu-id="1d512-243">You've now successfully built a time series machine learning model to forecast bike rental demand.</span></span>

<span data-ttu-id="1d512-244">Você pode encontrar o código fonte para este tutorial no repositório [dotnet/machinelearning-samples.](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand)</span><span class="sxs-lookup"><span data-stu-id="1d512-244">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1d512-245">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="1d512-245">Next steps</span></span>

- [<span data-ttu-id="1d512-246">Tarefas de aprendizado de máquina no ML.NET</span><span class="sxs-lookup"><span data-stu-id="1d512-246">Machine learning tasks in ML.NET</span></span>](../resources/tasks.md)
- [<span data-ttu-id="1d512-247">Aprimorar a precisão do modelo</span><span class="sxs-lookup"><span data-stu-id="1d512-247">Improve model accuracy</span></span>](../resources/improve-machine-learning-model-ml-net.md)
