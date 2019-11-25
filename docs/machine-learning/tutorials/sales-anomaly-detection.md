---
title: 'Tutorial: Detect anomalies in product sales'
description: Saiba como criar um aplicativo de detecção de anomalias para dados de vendas do produto. Este tutorial cria um aplicativo de console .NET Core usando C# no Visual Studio 2019.
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: fe2904dee349f32feb115ea533adbb4b1d8b7140
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204934"
---
# <a name="tutorial-detect-anomalies-in-product-sales-with-mlnet"></a><span data-ttu-id="200e5-104">Tutorial: Detect anomalies in product sales with ML.NET</span><span class="sxs-lookup"><span data-stu-id="200e5-104">Tutorial: Detect anomalies in product sales with ML.NET</span></span>

<span data-ttu-id="200e5-105">Saiba como criar um aplicativo de detecção de anomalias para dados de vendas do produto.</span><span class="sxs-lookup"><span data-stu-id="200e5-105">Learn how to build an anomaly detection application for product sales data.</span></span> <span data-ttu-id="200e5-106">Este tutorial cria um aplicativo de console .NET Core usando C# no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="200e5-106">This tutorial creates a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="200e5-107">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="200e5-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="200e5-108">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="200e5-108">Load the data</span></span>
> * <span data-ttu-id="200e5-109">Criar uma transformação para detecção de anomalias de pico</span><span class="sxs-lookup"><span data-stu-id="200e5-109">Create a transform for spike anomaly detection</span></span>
> * <span data-ttu-id="200e5-110">Detectar anomalias de pico com a transformação</span><span class="sxs-lookup"><span data-stu-id="200e5-110">Detect spike anomalies with the transform</span></span>
> * <span data-ttu-id="200e5-111">Criar uma transformação para detecção de anomalias de ponto de alteração</span><span class="sxs-lookup"><span data-stu-id="200e5-111">Create a transform for change point anomaly detection</span></span>
> * <span data-ttu-id="200e5-112">Detectar anomalias de ponto de alteração com a transformação</span><span class="sxs-lookup"><span data-stu-id="200e5-112">Detect change point anomalies with the transform</span></span>

<span data-ttu-id="200e5-113">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection).</span><span class="sxs-lookup"><span data-stu-id="200e5-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="200e5-114">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="200e5-114">Prerequisites</span></span>

* <span data-ttu-id="200e5-115">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span><span class="sxs-lookup"><span data-stu-id="200e5-115">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

* [<span data-ttu-id="200e5-116">O conjunto de dados product-sales.csv</span><span class="sxs-lookup"><span data-stu-id="200e5-116">The product-sales.csv dataset</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> <span data-ttu-id="200e5-117">Os dados de formato em `product-sales.csv` baseiam-se no conjunto de dados "Vendas de xampu no período de três anos" originalmente adquiridos do DataMarket e fornecidos pela TSDL (Biblioteca de Dados de Série Temporal), criado por Rob Hyndman.</span><span class="sxs-lookup"><span data-stu-id="200e5-117">The data format in `product-sales.csv` is based on the dataset “Shampoo Sales Over a Three Year Period” originally sourced from DataMarket and provided by Time Series Data Library (TSDL), created by Rob Hyndman.</span></span>
> <span data-ttu-id="200e5-118">Conjunto de dados de "Vendas de xampu no período de três anos" licenciado sob a Licença Aberta Padrão do DataMarket.</span><span class="sxs-lookup"><span data-stu-id="200e5-118">“Shampoo Sales Over a Three Year Period” Dataset Licensed Under the DataMarket Default Open License.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="200e5-119">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="200e5-119">Create a console application</span></span>

1. <span data-ttu-id="200e5-120">Crie um **Aplicativo de Console do .NET Core** chamado "ProductSalesAnomalyDetection".</span><span class="sxs-lookup"><span data-stu-id="200e5-120">Create a **.NET Core Console Application** called "ProductSalesAnomalyDetection".</span></span>

2. <span data-ttu-id="200e5-121">Crie um diretório chamado *Data* no seu projeto para salvar os arquivos do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="200e5-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="200e5-122">Instalar o **Pacote NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="200e5-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="200e5-123">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="200e5-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="200e5-124">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML** and select the **Install** button.</span><span class="sxs-lookup"><span data-stu-id="200e5-124">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="200e5-125">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="200e5-125">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="200e5-126">Repeat these steps for **Microsoft.ML.TimeSeries**.</span><span class="sxs-lookup"><span data-stu-id="200e5-126">Repeat these steps for **Microsoft.ML.TimeSeries**.</span></span>

4. <span data-ttu-id="200e5-127">Adicione as seguintes instruções `using` à parte superior do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="200e5-127">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="200e5-128">Baixar os dados</span><span class="sxs-lookup"><span data-stu-id="200e5-128">Download your data</span></span>

1. <span data-ttu-id="200e5-129">Baixe o conjunto de dados e salve-o na pasta *Data* criada anteriormente:</span><span class="sxs-lookup"><span data-stu-id="200e5-129">Download the dataset and save it to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="200e5-130">Clique com o botão direito do mouse em [*product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) e selecione "Salvar Link (ou destino) como…"</span><span class="sxs-lookup"><span data-stu-id="200e5-130">Right click on [*product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="200e5-131">Salve o arquivo \*.csv na pasta *Data* ou, depois de salvá-lo em outro lugar, mova o arquivo \*.csv para a pasta *Data*.</span><span class="sxs-lookup"><span data-stu-id="200e5-131">Make sure you either save the \*.csv file to the *Data* folder, or after you save it elsewhere, move the \*.csv file to the *Data* folder.</span></span>

2. <span data-ttu-id="200e5-132">No Gerenciador de Soluções, clique com o botão direito do mouse no arquivo \*.csv e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="200e5-132">In Solution Explorer, right-click the \*.csv file and select **Properties**.</span></span> <span data-ttu-id="200e5-133">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.</span><span class="sxs-lookup"><span data-stu-id="200e5-133">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="200e5-134">A tabela a seguir é uma visualização de dados do seu arquivo \*.csv:</span><span class="sxs-lookup"><span data-stu-id="200e5-134">The following table is a data preview from your \*.csv file:</span></span>

|<span data-ttu-id="200e5-135">Mês</span><span class="sxs-lookup"><span data-stu-id="200e5-135">Month</span></span>  |<span data-ttu-id="200e5-136">ProductSales</span><span class="sxs-lookup"><span data-stu-id="200e5-136">ProductSales</span></span> |
|-------|-------------|
|<span data-ttu-id="200e5-137">1-Jan</span><span class="sxs-lookup"><span data-stu-id="200e5-137">1-Jan</span></span>  |    <span data-ttu-id="200e5-138">271</span><span class="sxs-lookup"><span data-stu-id="200e5-138">271</span></span>      |
|<span data-ttu-id="200e5-139">2-Jan</span><span class="sxs-lookup"><span data-stu-id="200e5-139">2-Jan</span></span>  |    <span data-ttu-id="200e5-140">150.9</span><span class="sxs-lookup"><span data-stu-id="200e5-140">150.9</span></span>    |
|<span data-ttu-id="200e5-141">.....</span><span class="sxs-lookup"><span data-stu-id="200e5-141">.....</span></span>  |    <span data-ttu-id="200e5-142">.....</span><span class="sxs-lookup"><span data-stu-id="200e5-142">.....</span></span>    |
|<span data-ttu-id="200e5-143">1-Feb</span><span class="sxs-lookup"><span data-stu-id="200e5-143">1-Feb</span></span>  |    <span data-ttu-id="200e5-144">199.3</span><span class="sxs-lookup"><span data-stu-id="200e5-144">199.3</span></span>    |
|<span data-ttu-id="200e5-145">.....</span><span class="sxs-lookup"><span data-stu-id="200e5-145">.....</span></span>  |    <span data-ttu-id="200e5-146">.....</span><span class="sxs-lookup"><span data-stu-id="200e5-146">.....</span></span>    |

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="200e5-147">Criar classes e definir demarcadores</span><span class="sxs-lookup"><span data-stu-id="200e5-147">Create classes and define paths</span></span>

<span data-ttu-id="200e5-148">Em seguida, defina suas estruturas de dados de classe de entrada e de previsão.</span><span class="sxs-lookup"><span data-stu-id="200e5-148">Next, define your input and prediction class data structures.</span></span>

<span data-ttu-id="200e5-149">Adicione uma nova classe ao seu projeto:</span><span class="sxs-lookup"><span data-stu-id="200e5-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="200e5-150">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e, em seguida, selecione **Adicionar > Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="200e5-150">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="200e5-151">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *ProductSalesData.cs*.</span><span class="sxs-lookup"><span data-stu-id="200e5-151">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *ProductSalesData.cs*.</span></span> <span data-ttu-id="200e5-152">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="200e5-152">Then, select the **Add** button.</span></span>

   <span data-ttu-id="200e5-153">O arquivo *ProductSalesData.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="200e5-153">The *ProductSalesData.cs* file opens in the code editor.</span></span>

3. <span data-ttu-id="200e5-154">Adicione a seguinte instrução `using` à parte superior do *ProductSalesData.cs*:</span><span class="sxs-lookup"><span data-stu-id="200e5-154">Add the following `using` statement to the top of *ProductSalesData.cs*:</span></span>

   ```csharp
   using Microsoft.ML.Data;
   ```

4. <span data-ttu-id="200e5-155">Remova a definição de classe existente e adicione o seguinte código, que tem duas classes, `ProductSalesData` e `ProductSalesPrediction`, ao arquivo *ProductSalesData.cs*:</span><span class="sxs-lookup"><span data-stu-id="200e5-155">Remove the existing class definition and add the following code, which has two classes `ProductSalesData` and `ProductSalesPrediction`, to the *ProductSalesData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/ProductSalesData.cs#DeclareTypes "Declare data record types")]

    <span data-ttu-id="200e5-156">`ProductSalesData` especifica uma classe de dados de entrada.</span><span class="sxs-lookup"><span data-stu-id="200e5-156">`ProductSalesData` specifies an input data class.</span></span> <span data-ttu-id="200e5-157">O atributo [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) especifica quais colunas (por índice de coluna) no conjunto de dados devem ser carregadas.</span><span class="sxs-lookup"><span data-stu-id="200e5-157">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span>

    <span data-ttu-id="200e5-158">`ProductSalesPrediction` especifica a classe de dados de previsão.</span><span class="sxs-lookup"><span data-stu-id="200e5-158">`ProductSalesPrediction` specifies the prediction data class.</span></span> <span data-ttu-id="200e5-159">Para detecção de anomalias, a previsão consiste em um alerta para indicar se há uma anomalia, uma pontuação bruta e um valor p.</span><span class="sxs-lookup"><span data-stu-id="200e5-159">For anomaly detection, the prediction consists of an alert to indicate whether there is an anomaly, a raw score, and p-value.</span></span> <span data-ttu-id="200e5-160">Quanto mais próximo o valor p for de 0, maior será a probabilidade de que uma anomalia tenha ocorrido.</span><span class="sxs-lookup"><span data-stu-id="200e5-160">The closer the p-value is to 0, the more likely an anomaly has occurred.</span></span>

5. <span data-ttu-id="200e5-161">Crie dois campos globais para armazenar o caminho do arquivo de conjunto de dados baixado recentemente e o caminho do arquivo de modelo salvo:</span><span class="sxs-lookup"><span data-stu-id="200e5-161">Create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

    * <span data-ttu-id="200e5-162">`_dataPath` tem o demarcador para o conjunto de dados usado para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="200e5-162">`_dataPath` has the path to the dataset used to train the model.</span></span>
    * <span data-ttu-id="200e5-163">O `_docsize` tem o número de registros no arquivo de conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="200e5-163">`_docsize` has the number of records in dataset file.</span></span> <span data-ttu-id="200e5-164">Você usará `_docSize` para calcular `pvalueHistoryLength`.</span><span class="sxs-lookup"><span data-stu-id="200e5-164">You'll use `_docSize` to calculate `pvalueHistoryLength`.</span></span>

6. <span data-ttu-id="200e5-165">Adicione o seguinte código à linha logo acima do método `Main` para especificar estes caminhos:</span><span class="sxs-lookup"><span data-stu-id="200e5-165">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

    [!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DeclareGlobalVariables "Declare global variables")]

### <a name="initialize-variables-in-main"></a><span data-ttu-id="200e5-166">Inicializar variáveis em Main</span><span class="sxs-lookup"><span data-stu-id="200e5-166">Initialize variables in Main</span></span>

1. <span data-ttu-id="200e5-167">Substitua a linha `Console.WriteLine("Hello World!")` no método `Main` pelo seguinte código para declarar e inicializar a variável `mlContext`:</span><span class="sxs-lookup"><span data-stu-id="200e5-167">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

    [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateMLContext "Create the ML Context")]

    <span data-ttu-id="200e5-168">A [classe MLContext](xref:Microsoft.ML.MLContext) é um ponto de partida para todas as operações do ML.NET e a inicialização do `mlContext` cria um ambiente do ML.NET que pode ser compartilhado entre os objetos de fluxo de trabalho da criação de modelo.</span><span class="sxs-lookup"><span data-stu-id="200e5-168">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="200e5-169">Ele é semelhante, conceitualmente, a `DBContext` no Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="200e5-169">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="load-the-data"></a><span data-ttu-id="200e5-170">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="200e5-170">Load the data</span></span>

<span data-ttu-id="200e5-171">Os dados do ML.NET são representados como uma [classe IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="200e5-171">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="200e5-172">`IDataView` é uma maneira flexível e eficiente de descrever dados tabulares (numéricos e texto).</span><span class="sxs-lookup"><span data-stu-id="200e5-172">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="200e5-173">Os dados podem ser carregados de um arquivo de texto ou de outras fontes (por exemplo, banco de dados SQL ou arquivos de log) para um objeto `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="200e5-173">Data can be loaded from a text file or from other sources (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="200e5-174">Adicione o seguinte código como a próxima linha do método `Main()`:</span><span class="sxs-lookup"><span data-stu-id="200e5-174">Add the following code as the next line of the `Main()` method:</span></span>

    [!code-csharp[LoadData](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="200e5-175">O [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) define o esquema de dados e lê o arquivo.</span><span class="sxs-lookup"><span data-stu-id="200e5-175">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="200e5-176">Ele usa as variáveis de caminho de dados e retorna uma `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="200e5-176">It takes in the data path variables and returns an `IDataView`.</span></span>

## <a name="time-series-anomaly-detection"></a><span data-ttu-id="200e5-177">Detecção de anomalias de série temporal</span><span class="sxs-lookup"><span data-stu-id="200e5-177">Time series anomaly detection</span></span>

<span data-ttu-id="200e5-178">Detecção de anomalias sinaliza comportamentos ou eventos incomuns ou inesperados.</span><span class="sxs-lookup"><span data-stu-id="200e5-178">Anomaly detection flags unexpected or unusual events or behaviors.</span></span> <span data-ttu-id="200e5-179">Ela dá dicas de em que local procurar problemas e ajuda a responder à pergunta "Isso é estranho?".</span><span class="sxs-lookup"><span data-stu-id="200e5-179">It gives clues where to look for problems and helps you answer the question "Is this weird?".</span></span>

![Example of the "Is this weird" anomaly detection.](./media/sales-anomaly-detection/time-series-anomaly-detection.png)

<span data-ttu-id="200e5-181">A detecção de anomalias é o processo de detectar exceções de dados de série temporal; pontos em uma série temporal de entrada em que o comportamento não é o esperado ou "estranho".</span><span class="sxs-lookup"><span data-stu-id="200e5-181">Anomaly detection is the process of detecting time-series data outliers; points on a given input time-series where the behavior isn't what was expected, or "weird".</span></span>

<span data-ttu-id="200e5-182">A detecção de anomalias pode ser útil de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="200e5-182">Anomaly detection can be useful in lots of ways.</span></span> <span data-ttu-id="200e5-183">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="200e5-183">For instance:</span></span>

<span data-ttu-id="200e5-184">If you have a car, you might want to know: Is this oil gauge reading normal, or do I have a leak?</span><span class="sxs-lookup"><span data-stu-id="200e5-184">If you have a car, you might want to know: Is this oil gauge reading normal, or do I have a leak?</span></span>
<span data-ttu-id="200e5-185">If you're monitoring power consumption, you’d want to know: Is there an outage?</span><span class="sxs-lookup"><span data-stu-id="200e5-185">If you're monitoring power consumption, you’d want to know: Is there an outage?</span></span>

<span data-ttu-id="200e5-186">Há dois tipos de anomalias de série temporal que podem ser detectados:</span><span class="sxs-lookup"><span data-stu-id="200e5-186">There are two types of time series anomalies that can be detected:</span></span>

* <span data-ttu-id="200e5-187">**Picos** indicam intermitências temporárias de comportamentos anormais no sistema.</span><span class="sxs-lookup"><span data-stu-id="200e5-187">**Spikes** indicate temporary bursts of anomalous behavior in the system.</span></span>

* <span data-ttu-id="200e5-188">**Pontos de alteração** indicam o início de alterações persistentes ao longo do tempo no sistema.</span><span class="sxs-lookup"><span data-stu-id="200e5-188">**Change points** indicate the beginning of persistent changes over time in the system.</span></span>

<span data-ttu-id="200e5-189">No ML.NET, os algoritmos de Detecção de Pico IID ou Detecção de Ponto de Alteração IID são adequados para [conjuntos de dados independentes e distribuídos de forma idêntica](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span><span class="sxs-lookup"><span data-stu-id="200e5-189">In ML.NET, The IID Spike Detection or IID Change point Detection algorithms are suited for [independent and identically distributed datasets](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span></span>

<span data-ttu-id="200e5-190">Ao contrário dos modelos nos outros tutoriais, as transformações do detector de anomalias de série temporal operam diretamente nos dados de entrada.</span><span class="sxs-lookup"><span data-stu-id="200e5-190">Unlike the models in the other tutorials, the time series anomaly detector transforms operate directly on input data.</span></span> <span data-ttu-id="200e5-191">O método `IEstimator.Fit()` não precisa de dados de treinamento para produzir a transformação.</span><span class="sxs-lookup"><span data-stu-id="200e5-191">The `IEstimator.Fit()` method does not need training data to produce the transform.</span></span> <span data-ttu-id="200e5-192">No entanto, ele precisa do esquema de dados, que é fornecido por uma exibição de dados gerada de uma lista vazia de `ProductSalesData`.</span><span class="sxs-lookup"><span data-stu-id="200e5-192">It does need the data schema though, which is provided by a data view generated from an empty list of `ProductSalesData`.</span></span>

<span data-ttu-id="200e5-193">Você vai analisar os mesmos dados de vendas do produto para detectar picos e pontos de alteração.</span><span class="sxs-lookup"><span data-stu-id="200e5-193">You'll analyze the same product sales data to detect spikes and change points.</span></span> <span data-ttu-id="200e5-194">O processo de criar e treinar o modelo é o mesmo para detecção de pico e detecção de ponto de alteração; a principal diferença é o algoritmo de detecção específico usado.</span><span class="sxs-lookup"><span data-stu-id="200e5-194">The building and training model process is the same for spike detection and change point detection; the main difference is the specific detection algorithm used.</span></span>

## <a name="spike-detection"></a><span data-ttu-id="200e5-195">Detecção de pico</span><span class="sxs-lookup"><span data-stu-id="200e5-195">Spike detection</span></span>

<span data-ttu-id="200e5-196">A meta da detecção de pico é identificar picos repentinos, mas temporários, que diferem significativamente da maioria dos valores de dados de série temporal.</span><span class="sxs-lookup"><span data-stu-id="200e5-196">The goal of spike detection is to identify sudden yet temporary bursts that significantly differ from the majority of the time series data values.</span></span> <span data-ttu-id="200e5-197">É importante detectar esses itens raros, eventos ou observações suspeitos de maneira oportuna para que sejam minimizados.</span><span class="sxs-lookup"><span data-stu-id="200e5-197">It's important to detect these suspicious rare items, events, or observations in a timely manner to be minimized.</span></span> <span data-ttu-id="200e5-198">A abordagem a seguir pode ser usada para detectar uma variedade de anomalias, como: interrupções, ataques cibernéticos ou conteúdo da Web viral.</span><span class="sxs-lookup"><span data-stu-id="200e5-198">The following approach can be used to detect a variety of anomalies such as: outages, cyber-attacks, or viral web content.</span></span> <span data-ttu-id="200e5-199">A imagem a seguir é um exemplo de picos em um conjunto de dados de série temporal:</span><span class="sxs-lookup"><span data-stu-id="200e5-199">The following image is an example of spikes in a time series dataset:</span></span>

![Screenshot that shows two spike detections.](./media/sales-anomaly-detection/two-spike-detections.png)

### <a name="add-the-createemptydataview-method"></a><span data-ttu-id="200e5-201">Adicionar o método CreateEmptyDataView()</span><span class="sxs-lookup"><span data-stu-id="200e5-201">Add the CreateEmptyDataView() method</span></span>

<span data-ttu-id="200e5-202">Adicione o seguinte método a `Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="200e5-202">Add the following method to `Program.cs`:</span></span>

[!code-csharp[CreateEmptyDataView](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEmptyDataView)]

<span data-ttu-id="200e5-203">O `CreateEmptyDataView()` produz um objeto de exibição de dados vazio com o esquema correto a ser usado como entrada para o método `IEstimator.Fit()`.</span><span class="sxs-lookup"><span data-stu-id="200e5-203">The `CreateEmptyDataView()` produces an empty data view object with the correct schema to be used as input to the `IEstimator.Fit()` method.</span></span>

### <a name="create-the-detectspike-method"></a><span data-ttu-id="200e5-204">Crie o método DetectSpike()</span><span class="sxs-lookup"><span data-stu-id="200e5-204">Create the DetectSpike() method</span></span>

<span data-ttu-id="200e5-205">O método `DetectSpike()`:</span><span class="sxs-lookup"><span data-stu-id="200e5-205">The `DetectSpike()` method:</span></span>

* <span data-ttu-id="200e5-206">Cria a transformação do estimador.</span><span class="sxs-lookup"><span data-stu-id="200e5-206">Creates the transform from the estimator.</span></span>
* <span data-ttu-id="200e5-207">Detecta picos com base em dados históricos de vendas.</span><span class="sxs-lookup"><span data-stu-id="200e5-207">Detects spikes based on historical sales data.</span></span>
* <span data-ttu-id="200e5-208">Exibe os resultados.</span><span class="sxs-lookup"><span data-stu-id="200e5-208">Displays the results.</span></span>

1. <span data-ttu-id="200e5-209">Crie o método `DetectSpike()`, logo após o método `Main()`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="200e5-209">Create the `DetectSpike()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. <span data-ttu-id="200e5-210">Use [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) para treinar o modelo para a detecção de pico.</span><span class="sxs-lookup"><span data-stu-id="200e5-210">Use the [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) to train the model for spike detection.</span></span> <span data-ttu-id="200e5-211">Adicione-o ao método `DetectSpike()` com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="200e5-211">Add it to the `DetectSpike()` method with the following code:</span></span>

    [!code-csharp[AddSpikeTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddSpikeTrainer)]

1. <span data-ttu-id="200e5-212">Crie a transformação detecção de pico adicionando o seguinte como a próxima linha de código no método `DetectSpike()`:</span><span class="sxs-lookup"><span data-stu-id="200e5-212">Create the spike detection transform by adding the following as the next line of code in the `DetectSpike()` method:</span></span>

    [!code-csharp[TrainModel1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel1)]

1. <span data-ttu-id="200e5-213">Adicione a seguinte linha de código para transformar os dados `productSales` como a próxima linha no método `DetectSpike()`:</span><span class="sxs-lookup"><span data-stu-id="200e5-213">Add the following line of code to transform the `productSales` data as the next line in the `DetectSpike()` method:</span></span>

    [!code-csharp[TransformData1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData1)]

    <span data-ttu-id="200e5-214">O código anterior usa o método [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) para fazer previsões para várias linhas de entrada de um conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="200e5-214">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple input rows of a dataset.</span></span>

1. <span data-ttu-id="200e5-215">Converta seu `transformedData` em um `IEnumerable` fortemente tipado para exibição mais fácil usando o método [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="200e5-215">Convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) method with the following code:</span></span>

    [!code-csharp[CreateEnumerable1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable1)]

1. <span data-ttu-id="200e5-216">Crie uma linha de cabeçalho de exibição usando o seguinte código <xref:System.Console.WriteLine?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="200e5-216">Create a display header line using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

    [!code-csharp[DisplayHeader1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader1)]

    <span data-ttu-id="200e5-217">Você exibirá as informações a seguir nos resultados da detecção de pico:</span><span class="sxs-lookup"><span data-stu-id="200e5-217">You'll display the following information in your spike detection results:</span></span>

    * <span data-ttu-id="200e5-218">`Alert` indica um alerta de pico para um ponto de dados específico.</span><span class="sxs-lookup"><span data-stu-id="200e5-218">`Alert` indicates a spike alert for a given data point.</span></span>
    * <span data-ttu-id="200e5-219">`Score` é o valor `ProductSales` para um dado ponto de dados no conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="200e5-219">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>
    * <span data-ttu-id="200e5-220">`P-Value` O "P" significa probabilidade.</span><span class="sxs-lookup"><span data-stu-id="200e5-220">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="200e5-221">Quanto mais próximo o valor p for de 0, maior será a probabilidade de que o ponto de dados seja uma anomalia.</span><span class="sxs-lookup"><span data-stu-id="200e5-221">The closer the p-value is to 0, the more likely the data point is an anomaly.</span></span>

1. <span data-ttu-id="200e5-222">Use o seguinte código para iterar por `predictions` `IEnumerable` e exibir os resultados:</span><span class="sxs-lookup"><span data-stu-id="200e5-222">Use the following code to iterate through the `predictions` `IEnumerable` and display the results:</span></span>

    [!code-csharp[DisplayResults1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults1)]

1. <span data-ttu-id="200e5-223">Adicione a chamada ao método `DetectSpike()` no método `Main()`:</span><span class="sxs-lookup"><span data-stu-id="200e5-223">Add the call to the `DetectSpike()`method in the `Main()` method:</span></span>

    [!code-csharp[CallDetectSpike](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectSpike)]

## <a name="spike-detection-results"></a><span data-ttu-id="200e5-224">Resultados da detecção de pico</span><span class="sxs-lookup"><span data-stu-id="200e5-224">Spike detection results</span></span>

<span data-ttu-id="200e5-225">Seus resultados devem ser semelhantes aos seguintes.</span><span class="sxs-lookup"><span data-stu-id="200e5-225">Your results should be similar to the following.</span></span> <span data-ttu-id="200e5-226">Durante o processamento, as mensagens são exibidas.</span><span class="sxs-lookup"><span data-stu-id="200e5-226">During processing, messages are displayed.</span></span> <span data-ttu-id="200e5-227">Você pode ver avisos ou mensagens de processamento.</span><span class="sxs-lookup"><span data-stu-id="200e5-227">You may see warnings, or processing messages.</span></span> <span data-ttu-id="200e5-228">Algumas das mensagens foram removidas dos resultados a seguir para fins de clareza.</span><span class="sxs-lookup"><span data-stu-id="200e5-228">Some of the messages have been removed from the following results for clarity.</span></span>

```console
Detect temporary changes in pattern
=============== Training the model ===============
=============== End of training process ===============
Alert   Score   P-Value
0       271.00  0.50
0       150.90  0.00
0       188.10  0.41
0       124.30  0.13
0       185.30  0.47
0       173.50  0.47
0       236.80  0.19
0       229.50  0.27
0       197.80  0.48
0       127.90  0.13
1       341.50  0.00 <-- Spike detected
0       190.90  0.48
0       199.30  0.48
0       154.50  0.24
0       215.10  0.42
0       278.30  0.19
0       196.40  0.43
0       292.00  0.17
0       231.00  0.45
0       308.60  0.18
0       294.90  0.19
1       426.60  0.00 <-- Spike detected
0       269.50  0.47
0       347.30  0.21
0       344.70  0.27
0       445.40  0.06
0       320.90  0.49
0       444.30  0.12
0       406.30  0.29
0       442.40  0.21
1       580.50  0.00 <-- Spike detected
0       412.60  0.45
1       687.00  0.01 <-- Spike detected
0       480.30  0.40
0       586.30  0.20
0       651.90  0.14
```

## <a name="change-point-detection"></a><span data-ttu-id="200e5-229">Detecção de ponto de alteração</span><span class="sxs-lookup"><span data-stu-id="200e5-229">Change point detection</span></span>

<span data-ttu-id="200e5-230">`Change points` são alterações persistentes em uma distribuição de valores de fluxo de evento de série temporal, como alterações de nível e tendências.</span><span class="sxs-lookup"><span data-stu-id="200e5-230">`Change points` are persistent changes in a time series event stream distribution of values, like level changes and trends.</span></span> <span data-ttu-id="200e5-231">Essas alterações persistentes duram muito mais que `spikes` e podem indicar eventos catastróficos.</span><span class="sxs-lookup"><span data-stu-id="200e5-231">These persistent changes last much longer than `spikes` and could indicate catastrophic event(s).</span></span> <span data-ttu-id="200e5-232">`Change points` normalmente não estão visíveis a olho nu, mas podem ser detectados em seus dados usando abordagens como o método a seguir.</span><span class="sxs-lookup"><span data-stu-id="200e5-232">`Change points` are not usually visible to the naked eye, but can be detected in your data using approaches such as in the following method.</span></span>  <span data-ttu-id="200e5-233">A imagem a seguir é um exemplo de uma detecção de ponto de alteração:</span><span class="sxs-lookup"><span data-stu-id="200e5-233">The following image is an example of a change point detection:</span></span>

![Screenshot that shows a change point detection.](./media/sales-anomaly-detection/change-point-detection.png)

### <a name="create-the-detectchangepoint-method"></a><span data-ttu-id="200e5-235">Crie o método DetectChangepoint()</span><span class="sxs-lookup"><span data-stu-id="200e5-235">Create the DetectChangepoint() method</span></span>

<span data-ttu-id="200e5-236">O método `DetectChangepoint()` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="200e5-236">The `DetectChangepoint()` method executes the following tasks:</span></span>

* <span data-ttu-id="200e5-237">Cria a transformação do estimador.</span><span class="sxs-lookup"><span data-stu-id="200e5-237">Creates the transform from the estimator.</span></span>
* <span data-ttu-id="200e5-238">Detecta pontos de alteração com base em dados históricos de vendas.</span><span class="sxs-lookup"><span data-stu-id="200e5-238">Detects change points based on historical sales data.</span></span>
* <span data-ttu-id="200e5-239">Exibe os resultados.</span><span class="sxs-lookup"><span data-stu-id="200e5-239">Displays the results.</span></span>

1. <span data-ttu-id="200e5-240">Crie o método `DetectChangepoint()`, logo após o método `Main()`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="200e5-240">Create the `DetectChangepoint()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. <span data-ttu-id="200e5-241">Crie o [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) no método `DetectChangepoint()` com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="200e5-241">Create the [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) in the `DetectChangepoint()` method with the following code:</span></span>

    [!code-csharp[AddChangepointTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddChangepointTrainer)]

1. <span data-ttu-id="200e5-242">Como você fez anteriormente, crie a transformação do estimador adicionando a seguinte linha de código ao método `DetectChangePoint()`:</span><span class="sxs-lookup"><span data-stu-id="200e5-242">As you did previously, create the transform from the estimator by adding the following line of code in the `DetectChangePoint()` method:</span></span>

    [!code-csharp[TrainModel2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel2)]

1. <span data-ttu-id="200e5-243">Use o método `Transform()` para transformar os dados adicionando o seguinte código a `DetectChangePoint()`:</span><span class="sxs-lookup"><span data-stu-id="200e5-243">Use the `Transform()` method to transform the data by adding the following code to `DetectChangePoint()`:</span></span>

    [!code-csharp[TransformData2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData2)]

1. <span data-ttu-id="200e5-244">Como você fez antes, converta seu `transformedData` em um `IEnumerable` fortemente tipado para exibição mais fácil usando o método `CreateEnumerable()` com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="200e5-244">As you did previously, convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the `CreateEnumerable()`method with the following code:</span></span>

    [!code-csharp[CreateEnumerable2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable2)]

1. <span data-ttu-id="200e5-245">Crie um cabeçalho de exibição com o código a seguir como a próxima linha no método `DetectChangePoint()`:</span><span class="sxs-lookup"><span data-stu-id="200e5-245">Create a display header with the following code as the next line in the `DetectChangePoint()` method:</span></span>

    [!code-csharp[DisplayHeader2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader2)]

    <span data-ttu-id="200e5-246">Você exibirá as informações a seguir nos resultados da detecção de ponto de alteração:</span><span class="sxs-lookup"><span data-stu-id="200e5-246">You'll display the following information in your change point detection results:</span></span>

    * <span data-ttu-id="200e5-247">`Alert` indica um alerta de ponto de alteração para um ponto de dados específico.</span><span class="sxs-lookup"><span data-stu-id="200e5-247">`Alert` indicates a change point alert for a given data point.</span></span>
    * <span data-ttu-id="200e5-248">`Score` é o valor `ProductSales` para um dado ponto de dados no conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="200e5-248">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>
    * <span data-ttu-id="200e5-249">`P-Value` O "P" significa probabilidade.</span><span class="sxs-lookup"><span data-stu-id="200e5-249">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="200e5-250">Quanto mais próximo o valor P for de 0, maior será a probabilidade de que o ponto de dados seja uma anomalia.</span><span class="sxs-lookup"><span data-stu-id="200e5-250">The closer the P-value is to 0, the more likely the data point is an anomaly.</span></span>
    * <span data-ttu-id="200e5-251">`Martingale value` é usado para identificar o quão "estranho" um ponto de dados é com base na sequência de valores de P.</span><span class="sxs-lookup"><span data-stu-id="200e5-251">`Martingale value` is used to identify how "weird" a data point is, based on the sequence of P-values.</span></span>

1. <span data-ttu-id="200e5-252">Itere por `predictions` `IEnumerable` e exiba os resultados com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="200e5-252">Iterate through the `predictions` `IEnumerable` and display the results with the following code:</span></span>

    [!code-csharp[DisplayResults2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults2)]

1. <span data-ttu-id="200e5-253">Adicione a seguinte chamada ao método `DetectChangepoint()` no método `Main()`:</span><span class="sxs-lookup"><span data-stu-id="200e5-253">Add the following call to the `DetectChangepoint()`method in the `Main()` method:</span></span>

    [!code-csharp[CallDetectChangepoint](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectChangepoint)]

## <a name="change-point-detection-results"></a><span data-ttu-id="200e5-254">Resultados da detecção de ponto de alteração</span><span class="sxs-lookup"><span data-stu-id="200e5-254">Change point detection results</span></span>

<span data-ttu-id="200e5-255">Seus resultados devem ser semelhantes aos seguintes.</span><span class="sxs-lookup"><span data-stu-id="200e5-255">Your results should be similar to the following.</span></span> <span data-ttu-id="200e5-256">Durante o processamento, as mensagens são exibidas.</span><span class="sxs-lookup"><span data-stu-id="200e5-256">During processing, messages are displayed.</span></span> <span data-ttu-id="200e5-257">Você pode ver avisos ou mensagens de processamento.</span><span class="sxs-lookup"><span data-stu-id="200e5-257">You may see warnings, or processing messages.</span></span> <span data-ttu-id="200e5-258">Algumas mensagens foram removidas dos resultados a seguir para fins de clareza.</span><span class="sxs-lookup"><span data-stu-id="200e5-258">Some messages have been removed from the following results for clarity.</span></span>

```console
Detect Persistent changes in pattern
=============== Training the model Using Change Point Detection Algorithm===============
=============== End of training process ===============
Alert   Score   P-Value Martingale value
0       271.00  0.50    0.00
0       150.90  0.00    2.33
0       188.10  0.41    2.80
0       124.30  0.13    9.16
0       185.30  0.47    9.77
0       173.50  0.47    10.41
0       236.80  0.19    24.46
0       229.50  0.27    42.38
1       197.80  0.48    44.23 <-- alert is on, predicted changepoint
0       127.90  0.13    145.25
0       341.50  0.00    0.01
0       190.90  0.48    0.01
0       199.30  0.48    0.00
0       154.50  0.24    0.00
0       215.10  0.42    0.00
0       278.30  0.19    0.00
0       196.40  0.43    0.00
0       292.00  0.17    0.01
0       231.00  0.45    0.00
0       308.60  0.18    0.00
0       294.90  0.19    0.00
0       426.60  0.00    0.00
0       269.50  0.47    0.00
0       347.30  0.21    0.00
0       344.70  0.27    0.00
0       445.40  0.06    0.02
0       320.90  0.49    0.01
0       444.30  0.12    0.02
0       406.30  0.29    0.01
0       442.40  0.21    0.01
0       580.50  0.00    0.01
0       412.60  0.45    0.01
0       687.00  0.01    0.12
0       480.30  0.40    0.08
0       586.30  0.20    0.03
0       651.90  0.14    0.09
```

<span data-ttu-id="200e5-259">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="200e5-259">Congratulations!</span></span> <span data-ttu-id="200e5-260">Você agora criou com êxito os modelos de machine learning para detectar anomalias de pontos de alteração e picos nos dados de vendas.</span><span class="sxs-lookup"><span data-stu-id="200e5-260">You've now successfully built machine learning models for detecting spikes and change point anomalies in sales data.</span></span>

<span data-ttu-id="200e5-261">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection).</span><span class="sxs-lookup"><span data-stu-id="200e5-261">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

<span data-ttu-id="200e5-262">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="200e5-262">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="200e5-263">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="200e5-263">Load the data</span></span>
> * <span data-ttu-id="200e5-264">Treinar o modelo para detecção de anomalias de pico</span><span class="sxs-lookup"><span data-stu-id="200e5-264">Train the model for spike anomaly detection</span></span>
> * <span data-ttu-id="200e5-265">Detectar anomalias de pico com o modelo treinado</span><span class="sxs-lookup"><span data-stu-id="200e5-265">Detect spike anomalies with the trained model</span></span>
> * <span data-ttu-id="200e5-266">Treinar o modelo para detecção de anomalias de ponto de alteração</span><span class="sxs-lookup"><span data-stu-id="200e5-266">Train the model for change point anomaly detection</span></span>
> * <span data-ttu-id="200e5-267">Detectar anomalias de ponto de alteração com o modo treinado</span><span class="sxs-lookup"><span data-stu-id="200e5-267">Detect change point anomalies with the trained mode</span></span>

## <a name="next-steps"></a><span data-ttu-id="200e5-268">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="200e5-268">Next steps</span></span>

<span data-ttu-id="200e5-269">Confira o repositório do GitHub de exemplos de Machine Learning para explorar um exemplo de Detecção de Anomalias de Consumo de Energia.</span><span class="sxs-lookup"><span data-stu-id="200e5-269">Check out the Machine Learning samples GitHub repository to explore a Power Consumption Anomaly Detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="200e5-270">dotnet/machinelearning-samples GitHub repository</span><span class="sxs-lookup"><span data-stu-id="200e5-270">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)
