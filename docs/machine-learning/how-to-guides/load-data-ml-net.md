---
title: Carregar dados
description: Carregar arquivo de dados e transmitir dados para o ML.NET
ms.date: 05/03/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 6edcc92b610e2e1f5e21c371b9f0aefd0b216d31
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063640"
---
# <a name="load-data-from-file-and-in-memory-sources"></a><span data-ttu-id="d7b7e-103">Carregar dados de origens de fontes na memória e de arquivo</span><span class="sxs-lookup"><span data-stu-id="d7b7e-103">Load data from file and in-memory sources</span></span>

<span data-ttu-id="d7b7e-104">Estas instruções mostram como carregar dados para processamento e treinamento no ML.NET.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-104">This how-to shows you how to load data for processing and training into ML.NET.</span></span> <span data-ttu-id="d7b7e-105">Originalmente, os dados são armazenados em arquivos ou fontes de dados de streaming/tempo real.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-105">The data is originally stored in files or real-time / streaming data sources.</span></span>

## <a name="create-the-data-model"></a><span data-ttu-id="d7b7e-106">Criar o modelo de dados</span><span class="sxs-lookup"><span data-stu-id="d7b7e-106">Create the data model</span></span>

<span data-ttu-id="d7b7e-107">O ML.NET permite que você defina modelos de dados por meio de classes.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-107">ML.NET enables you to define data models via classes.</span></span> <span data-ttu-id="d7b7e-108">Por exemplo, considerando os seguintes dados de entrada:</span><span class="sxs-lookup"><span data-stu-id="d7b7e-108">For example, given the following input data:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

<span data-ttu-id="d7b7e-109">Crie um modelo de dados que represente o snippet a seguir:</span><span class="sxs-lookup"><span data-stu-id="d7b7e-109">Create a data model that represents the snippet below:</span></span>

```csharp
public class HousingData
{
    [LoadColumn(0)]
    public float Size { get; set; }
 
    [LoadColumn(1, 3)]
    [VectorType(3)]
    public float[] HistoricalPrices { get; set; }

    [LoadColumn(4)]
    [ColumnName("Label")]
    public float CurrentPrice { get; set; }
}
```

### <a name="annotating-the-data-model-with-column-attributes"></a><span data-ttu-id="d7b7e-110">Anotando o modelo de dados com atributos de coluna</span><span class="sxs-lookup"><span data-stu-id="d7b7e-110">Annotating the data model with column attributes</span></span>

<span data-ttu-id="d7b7e-111">Atributos dão ao ML.NET mais informações sobre o modelo de dados e a fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-111">Attributes give ML.NET more information about the data model and the data source.</span></span>

<span data-ttu-id="d7b7e-112">O atributo [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) especifica os índices de colunas de suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-112">The [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute specifies your properties' column indices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d7b7e-113">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) é necessário apenas ao carregar dados de um arquivo.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-113">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) is only required when loading data from a file.</span></span>

<span data-ttu-id="d7b7e-114">Carregar colunas como:</span><span class="sxs-lookup"><span data-stu-id="d7b7e-114">Load columns as:</span></span> 
- <span data-ttu-id="d7b7e-115">Colunas individuais como `Size` e `CurrentPrices` na classe `HousingData`.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-115">Individual columns like `Size` and `CurrentPrices` in the `HousingData` class.</span></span>
- <span data-ttu-id="d7b7e-116">Como várias colunas por vez na forma de um vetor `HistoricalPrices` na classe `HousingData`.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-116">Multiple columns at a time in the form of a vector like `HistoricalPrices` in the `HousingData` class.</span></span>

<span data-ttu-id="d7b7e-117">Se você tiver uma propriedade de vetor, aplique o atributo [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) à propriedade em seu modelo de dados.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-117">If you have a vector property, apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to the property in your data model.</span></span> <span data-ttu-id="d7b7e-118">É importante observar que todos os elementos no vetor precisam ser do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-118">It's important to note that all of the elements in the vector need to be the same type.</span></span>

<span data-ttu-id="d7b7e-119">O ML.NET opera por meio de nomes de coluna.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-119">ML.NET Operates through column names.</span></span> <span data-ttu-id="d7b7e-120">Se você quiser alterar o nome de uma coluna para algo diferente do nome de propriedade, use o atributo [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute).</span><span class="sxs-lookup"><span data-stu-id="d7b7e-120">If you want to change the name of a column to something other than the property name, use the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span> <span data-ttu-id="d7b7e-121">Ao criar objetos na memória, você ainda cria objetos usando o nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-121">When creating in-memory objects, you still create objects using the property name.</span></span> <span data-ttu-id="d7b7e-122">No entanto, para processar e criar modelos de machine learning, o ML.NET substitui e faz referência à propriedade com o valor fornecido no atributo [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute).</span><span class="sxs-lookup"><span data-stu-id="d7b7e-122">However, for data processing and building machine learning models, ML.NET overrides and references the property with the value provided in the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span>

## <a name="load-data-from-a-single-file"></a><span data-ttu-id="d7b7e-123">Carregar dados de um único arquivo</span><span class="sxs-lookup"><span data-stu-id="d7b7e-123">Load data from a single file</span></span>

<span data-ttu-id="d7b7e-124">Para carregar dados de um arquivo, use o método [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) juntamente com o modelo de dados para os dados a serem carregados.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-124">To load data from a file use the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method along with the data model for the data to be loaded.</span></span> <span data-ttu-id="d7b7e-125">Uma vez que o parâmetro `separatorChar` é delimitado por tabulação por padrão, altere-o para seu arquivo de dados conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-125">Since `separatorChar` parameter is tab-delimited by default, change it for your data file as needed.</span></span> <span data-ttu-id="d7b7e-126">Se o arquivo tiver um cabeçalho, defina o parâmetro `hasHeader` como `true` para ignorar a primeira linha no arquivo e começar a carregar dados da segunda linha.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-126">If your file has a header, set the `hasHeader` parameter to `true` to ignore the first line in the file and begin to load data from the second line.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a><span data-ttu-id="d7b7e-127">Carregar dados de vários arquivos</span><span class="sxs-lookup"><span data-stu-id="d7b7e-127">Load data from multiple files</span></span>

<span data-ttu-id="d7b7e-128">Caso seus dados sejam armazenados em vários arquivos, desde que o esquema de dados seja o mesmo, o ML.NET permitirá que você carregue dados de vários arquivos que estejam no mesmo diretório ou em vários diretórios.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-128">In the event that your data is stored in multiple files, as long as the data schema is the same, ML.NET allows you to load data from multiple files that are either in the same directory or multiple directories.</span></span>

### <a name="load-from-files-in-a-single-directory"></a><span data-ttu-id="d7b7e-129">Carregar de arquivos em um único diretório</span><span class="sxs-lookup"><span data-stu-id="d7b7e-129">Load from files in a single directory</span></span>

<span data-ttu-id="d7b7e-130">Quando todos os seus arquivos de dados estão no mesmo diretório, use caracteres curinga no método [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*).</span><span class="sxs-lookup"><span data-stu-id="d7b7e-130">When all of your data files are in the same directory, use wildcards in the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a><span data-ttu-id="d7b7e-131">Carregar de arquivos em vários diretórios</span><span class="sxs-lookup"><span data-stu-id="d7b7e-131">Load from files in multiple directories</span></span>

<span data-ttu-id="d7b7e-132">Para carregar dados de vários diretórios, use o método [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) para criar um [`TextLoader`](xref:Microsoft.ML.Data.TextLoader).</span><span class="sxs-lookup"><span data-stu-id="d7b7e-132">To load data from multiple directories, use the [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) method to create a [`TextLoader`](xref:Microsoft.ML.Data.TextLoader).</span></span> <span data-ttu-id="d7b7e-133">Em seguida, use o método [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) e especifique os caminhos de arquivo individual (caracteres curinga não podem ser usados).</span><span class="sxs-lookup"><span data-stu-id="d7b7e-133">Then, use the [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) method and specify the individual file paths (wildcards can't be used).</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-streaming-source"></a><span data-ttu-id="d7b7e-134">Carregar dados de uma fonte de streaming</span><span class="sxs-lookup"><span data-stu-id="d7b7e-134">Load data from a streaming source</span></span>

<span data-ttu-id="d7b7e-135">Além de carregar os dados armazenados no disco, o ML.NET dá suporte ao carregamento de dados de várias fontes de streaming que incluem, entre outras:</span><span class="sxs-lookup"><span data-stu-id="d7b7e-135">In addition to loading data stored on disk, ML.NET supports loading data from various streaming sources that include but are not limited to:</span></span>

- <span data-ttu-id="d7b7e-136">Coleções na memória</span><span class="sxs-lookup"><span data-stu-id="d7b7e-136">In-memory collections</span></span>
- <span data-ttu-id="d7b7e-137">JSON/XML</span><span class="sxs-lookup"><span data-stu-id="d7b7e-137">JSON/XML</span></span>
- <span data-ttu-id="d7b7e-138">Bancos de dados</span><span class="sxs-lookup"><span data-stu-id="d7b7e-138">Databases</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d7b7e-139">Observe que, ao trabalhar com fontes de streaming, o ML.NET espera que a entrada esteja na forma de uma coleção em memória.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-139">Note that when working with streaming sources, ML.NET expects input to be in the form of an in-memory collection.</span></span> <span data-ttu-id="d7b7e-140">Portanto, ao trabalhar com fontes, como JSON/XML, formate os dados em uma coleção em memória.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-140">Therefore, when working with sources like JSON/XML, make sure to format the data into an in-memory collection.</span></span>

<span data-ttu-id="d7b7e-141">Dada a coleção em memória a seguir:</span><span class="sxs-lookup"><span data-stu-id="d7b7e-141">Given the following in-memory collection:</span></span>

```csharp
HousingData[] inMemoryCollection = new HousingData[]
{
    new HousingData
    {
        Size =700f,
        HistoricalPrices = new float[]
        {
            100000f, 3000000f, 250000f
        },
        CurrentPrice = 500000f
    },
    new HousingData
    {
        Size =1000f,
        HistoricalPrices = new float[]
        {
            600000f, 400000f, 650000f
        },
        CurrentPrice=700000f
    }
};
```

<span data-ttu-id="d7b7e-142">Carregue a coleção em memória em um [`IDataView`](xref:Microsoft.ML.IDataView) com o método [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*):</span><span class="sxs-lookup"><span data-stu-id="d7b7e-142">Load the in-memory collection into an [`IDataView`](xref:Microsoft.ML.IDataView) with the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method:</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```
