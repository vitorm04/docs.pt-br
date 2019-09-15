---
title: Carregar dados de arquivos e outras fontes
description: Estas instruções mostram como carregar dados para processamento e treinamento no ML.NET. Originalmente, os dados são armazenados em arquivos ou outras fontes de dados, como bancos de dados, JSON, XML ou coleções na memória.
ms.date: 09/11/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: 4008f38bf4a20113a3f5c865e38222e5b82f2acc
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991357"
---
# <a name="load-data-from-files-and-other-sources"></a><span data-ttu-id="d3c39-104">Carregar dados de arquivos e outras fontes</span><span class="sxs-lookup"><span data-stu-id="d3c39-104">Load data from files and other sources</span></span>

<span data-ttu-id="d3c39-105">Estas instruções mostram como carregar dados para processamento e treinamento no ML.NET.</span><span class="sxs-lookup"><span data-stu-id="d3c39-105">This how-to shows you how to load data for processing and training into ML.NET.</span></span> <span data-ttu-id="d3c39-106">Originalmente, os dados são armazenados em arquivos ou outras fontes de dados, como bancos de dados, JSON, XML ou coleções na memória.</span><span class="sxs-lookup"><span data-stu-id="d3c39-106">The data is originally stored in files or other data sources such as databases, JSON, XML or in-memory collections.</span></span>

## <a name="create-the-data-model"></a><span data-ttu-id="d3c39-107">Criar o modelo de dados</span><span class="sxs-lookup"><span data-stu-id="d3c39-107">Create the data model</span></span>

<span data-ttu-id="d3c39-108">O ML.NET permite que você defina modelos de dados por meio de classes.</span><span class="sxs-lookup"><span data-stu-id="d3c39-108">ML.NET enables you to define data models via classes.</span></span> <span data-ttu-id="d3c39-109">Por exemplo, considerando os seguintes dados de entrada:</span><span class="sxs-lookup"><span data-stu-id="d3c39-109">For example, given the following input data:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

<span data-ttu-id="d3c39-110">Crie um modelo de dados que represente o snippet a seguir:</span><span class="sxs-lookup"><span data-stu-id="d3c39-110">Create a data model that represents the snippet below:</span></span>

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

### <a name="annotating-the-data-model-with-column-attributes"></a><span data-ttu-id="d3c39-111">Anotando o modelo de dados com atributos de coluna</span><span class="sxs-lookup"><span data-stu-id="d3c39-111">Annotating the data model with column attributes</span></span>

<span data-ttu-id="d3c39-112">Atributos dão ao ML.NET mais informações sobre o modelo de dados e a fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="d3c39-112">Attributes give ML.NET more information about the data model and the data source.</span></span>

<span data-ttu-id="d3c39-113">O atributo [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) especifica os índices de colunas de suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="d3c39-113">The [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute specifies your properties' column indices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d3c39-114">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) é necessário apenas ao carregar dados de um arquivo.</span><span class="sxs-lookup"><span data-stu-id="d3c39-114">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) is only required when loading data from a file.</span></span>

<span data-ttu-id="d3c39-115">Carregar colunas como:</span><span class="sxs-lookup"><span data-stu-id="d3c39-115">Load columns as:</span></span>

- <span data-ttu-id="d3c39-116">Colunas individuais como `Size` e `CurrentPrices` na classe `HousingData`.</span><span class="sxs-lookup"><span data-stu-id="d3c39-116">Individual columns like `Size` and `CurrentPrices` in the `HousingData` class.</span></span>
- <span data-ttu-id="d3c39-117">Como várias colunas por vez na forma de um vetor `HistoricalPrices` na classe `HousingData`.</span><span class="sxs-lookup"><span data-stu-id="d3c39-117">Multiple columns at a time in the form of a vector like `HistoricalPrices` in the `HousingData` class.</span></span>

<span data-ttu-id="d3c39-118">Se você tiver uma propriedade de vetor, aplique o atributo [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) à propriedade em seu modelo de dados.</span><span class="sxs-lookup"><span data-stu-id="d3c39-118">If you have a vector property, apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to the property in your data model.</span></span> <span data-ttu-id="d3c39-119">É importante observar que todos os elementos no vetor precisam ser do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="d3c39-119">It's important to note that all of the elements in the vector need to be the same type.</span></span> <span data-ttu-id="d3c39-120">Manter as colunas separadas permite a facilidade e a flexibilidade da engenharia de recursos, mas, para um número muito grande de colunas, a operação nas colunas individuais causa um impacto na velocidade de treinamento.</span><span class="sxs-lookup"><span data-stu-id="d3c39-120">Keeping the columns separated allows for ease and flexibility of feature engineering, but for a very large number of columns, operating on the individual columns causes an impact on training speed.</span></span>

<span data-ttu-id="d3c39-121">O ML.NET opera por meio de nomes de coluna.</span><span class="sxs-lookup"><span data-stu-id="d3c39-121">ML.NET Operates through column names.</span></span> <span data-ttu-id="d3c39-122">Se você quiser alterar o nome de uma coluna para algo diferente do nome de propriedade, use o atributo [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute).</span><span class="sxs-lookup"><span data-stu-id="d3c39-122">If you want to change the name of a column to something other than the property name, use the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span> <span data-ttu-id="d3c39-123">Ao criar objetos na memória, você ainda cria objetos usando o nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="d3c39-123">When creating in-memory objects, you still create objects using the property name.</span></span> <span data-ttu-id="d3c39-124">No entanto, para processar e criar modelos de machine learning, o ML.NET substitui e faz referência à propriedade com o valor fornecido no atributo [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute).</span><span class="sxs-lookup"><span data-stu-id="d3c39-124">However, for data processing and building machine learning models, ML.NET overrides and references the property with the value provided in the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span>

## <a name="load-data-from-a-single-file"></a><span data-ttu-id="d3c39-125">Carregar dados de um único arquivo</span><span class="sxs-lookup"><span data-stu-id="d3c39-125">Load data from a single file</span></span>

<span data-ttu-id="d3c39-126">Para carregar dados de um arquivo, use o método [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) juntamente com o modelo de dados para os dados a serem carregados.</span><span class="sxs-lookup"><span data-stu-id="d3c39-126">To load data from a file use the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method along with the data model for the data to be loaded.</span></span> <span data-ttu-id="d3c39-127">Uma vez que o parâmetro `separatorChar` é delimitado por tabulação por padrão, altere-o para seu arquivo de dados conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="d3c39-127">Since `separatorChar` parameter is tab-delimited by default, change it for your data file as needed.</span></span> <span data-ttu-id="d3c39-128">Se o arquivo tiver um cabeçalho, defina o parâmetro `hasHeader` como `true` para ignorar a primeira linha no arquivo e começar a carregar dados da segunda linha.</span><span class="sxs-lookup"><span data-stu-id="d3c39-128">If your file has a header, set the `hasHeader` parameter to `true` to ignore the first line in the file and begin to load data from the second line.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a><span data-ttu-id="d3c39-129">Carregar dados de vários arquivos</span><span class="sxs-lookup"><span data-stu-id="d3c39-129">Load data from multiple files</span></span>

<span data-ttu-id="d3c39-130">Caso seus dados sejam armazenados em vários arquivos, desde que o esquema de dados seja o mesmo, o ML.NET permitirá que você carregue dados de vários arquivos que estejam no mesmo diretório ou em vários diretórios.</span><span class="sxs-lookup"><span data-stu-id="d3c39-130">In the event that your data is stored in multiple files, as long as the data schema is the same, ML.NET allows you to load data from multiple files that are either in the same directory or multiple directories.</span></span>

### <a name="load-from-files-in-a-single-directory"></a><span data-ttu-id="d3c39-131">Carregar de arquivos em um único diretório</span><span class="sxs-lookup"><span data-stu-id="d3c39-131">Load from files in a single directory</span></span>

<span data-ttu-id="d3c39-132">Quando todos os seus arquivos de dados estão no mesmo diretório, use caracteres curinga no método [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*).</span><span class="sxs-lookup"><span data-stu-id="d3c39-132">When all of your data files are in the same directory, use wildcards in the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a><span data-ttu-id="d3c39-133">Carregar de arquivos em vários diretórios</span><span class="sxs-lookup"><span data-stu-id="d3c39-133">Load from files in multiple directories</span></span>

<span data-ttu-id="d3c39-134">Para carregar dados de vários diretórios, use o método [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) para criar um [`TextLoader`](xref:Microsoft.ML.Data.TextLoader).</span><span class="sxs-lookup"><span data-stu-id="d3c39-134">To load data from multiple directories, use the [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) method to create a [`TextLoader`](xref:Microsoft.ML.Data.TextLoader).</span></span> <span data-ttu-id="d3c39-135">Em seguida, use o método [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) e especifique os caminhos de arquivo individual (caracteres curinga não podem ser usados).</span><span class="sxs-lookup"><span data-stu-id="d3c39-135">Then, use the [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) method and specify the individual file paths (wildcards can't be used).</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-relational-database"></a><span data-ttu-id="d3c39-136">Carregar dados de um banco de dado relacional</span><span class="sxs-lookup"><span data-stu-id="d3c39-136">Load data from a relational database</span></span>

> [!NOTE]
> <span data-ttu-id="d3c39-137">O DatabaseLoader está atualmente em versão prévia.</span><span class="sxs-lookup"><span data-stu-id="d3c39-137">DatabaseLoader is currently in preview.</span></span> <span data-ttu-id="d3c39-138">Ele pode ser usado referenciando os pacotes NuGet [Microsoft. ml. experimental](https://www.nuget.org/packages/Microsoft.ML.Experimental/0.16.0-preview) e [System. Data. SqlClient](https://www.nuget.org/packages/System.Data.SqlClient/4.6.1) .</span><span class="sxs-lookup"><span data-stu-id="d3c39-138">It can be used by referencing the [Microsoft.ML.Experimental](https://www.nuget.org/packages/Microsoft.ML.Experimental/0.16.0-preview) and [System.Data.SqlClient](https://www.nuget.org/packages/System.Data.SqlClient/4.6.1) NuGet packages.</span></span>

<span data-ttu-id="d3c39-139">O ml.net dá suporte ao carregamento de dados de uma variedade de bancos de dado [`System.Data`](xref:System.Data) relacionais com suporte pelo que incluem SQL Server, banco de dados SQL do Azure, Oracle, SQLite, PostgreSQL, progresso, IBM DB2 e muito mais.</span><span class="sxs-lookup"><span data-stu-id="d3c39-139">ML.NET supports loading data from a variety of relational databases supported by [`System.Data`](xref:System.Data) that include SQL Server, Azure SQL Database, Oracle, SQLite, PostgreSQL, Progress, IBM DB2, and many more.</span></span>

<span data-ttu-id="d3c39-140">Dado um banco de dados com uma `House` tabela chamada e o esquema a seguir:</span><span class="sxs-lookup"><span data-stu-id="d3c39-140">Given a database with a table named `House` and the following schema:</span></span>

```SQL
CREATE TABLE [House] (
    [HouseId] int NOT NULL IDENTITY,
    [Size] real NOT NULL,
    [Price] real NOT NULL
    CONSTRAINT [PK_House] PRIMARY KEY ([HouseId])
);
```

<span data-ttu-id="d3c39-141">Os dados podem ser modelados por uma classe como `HouseData`.</span><span class="sxs-lookup"><span data-stu-id="d3c39-141">The data can be modeled by a class like `HouseData`.</span></span>

```csharp
public class HouseData
{
    public float Size { get; set; }

    public float Price { get; set; }
}
```

<span data-ttu-id="d3c39-142">Em seguida, dentro do seu aplicativo, crie `DatabaseLoader`um.</span><span class="sxs-lookup"><span data-stu-id="d3c39-142">Then, inside of your application, create a `DatabaseLoader`.</span></span>

```csharp
MLContext mlContext = new MLContext();

DatabaseLoader loader = mlContext.Data.CreateDatabaseLoader<HouseData>();
```

<span data-ttu-id="d3c39-143">Defina a cadeia de conexão, bem como o comando SQL a ser executado no banco de dados e `DatabaseSource` crie uma instância.</span><span class="sxs-lookup"><span data-stu-id="d3c39-143">Define your connection string as well as the SQL command to be executed on the database and create a `DatabaseSource` instance.</span></span> <span data-ttu-id="d3c39-144">Este exemplo usa um banco de dados SQL Server LocalDB com um caminho de arquivo.</span><span class="sxs-lookup"><span data-stu-id="d3c39-144">This sample uses a LocalDB SQL Server database with a file path.</span></span> <span data-ttu-id="d3c39-145">No entanto, o DatabaseLoader dá suporte a qualquer outra cadeia de conexão válida para bancos de dados locais e na nuvem.</span><span class="sxs-lookup"><span data-stu-id="d3c39-145">However, DatabaseLoader supports any other valid connection string for databases on-premises and in the cloud.</span></span>

```csharp
string connectionString = @"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=<YOUR-DB-FILEPATH>;Database=<YOUR-DB-NAME>;Integrated Security=True;Connect Timeout=30";

string sqlCommand = "SELECT Size,Price FROM House";

DatabaseSource dbSource = new DatabaseSource(SqlClientFactory.Instance,connectionString,sqlCommand);
```

<span data-ttu-id="d3c39-146">Por fim, use `Load` o método para carregar os dados em [`IDataView`](xref:Microsoft.ML.IDataView)um.</span><span class="sxs-lookup"><span data-stu-id="d3c39-146">Finally, use the `Load` method to load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

```csharp
IDataView data = loader.Load(dbSource);
```

## <a name="load-data-from-other-sources"></a><span data-ttu-id="d3c39-147">Carregar dados de outras fontes</span><span class="sxs-lookup"><span data-stu-id="d3c39-147">Load data from other sources</span></span>

<span data-ttu-id="d3c39-148">Além de carregar os dados armazenados em arquivos, o ML.NET dá suporte ao carregamento de dados de várias fontes que incluem, mas não se limitam a:</span><span class="sxs-lookup"><span data-stu-id="d3c39-148">In addition to loading data stored in files, ML.NET supports loading data from sources that include but are not limited to:</span></span>

- <span data-ttu-id="d3c39-149">Coleções na memória</span><span class="sxs-lookup"><span data-stu-id="d3c39-149">In-memory collections</span></span>
- <span data-ttu-id="d3c39-150">JSON/XML</span><span class="sxs-lookup"><span data-stu-id="d3c39-150">JSON/XML</span></span>

<span data-ttu-id="d3c39-151">Observe que, ao trabalhar com fontes de streaming, o ML.NET espera que a entrada esteja na forma de uma coleção em memória.</span><span class="sxs-lookup"><span data-stu-id="d3c39-151">Note that when working with streaming sources, ML.NET expects input to be in the form of an in-memory collection.</span></span> <span data-ttu-id="d3c39-152">Portanto, ao trabalhar com fontes, como JSON/XML, formate os dados em uma coleção em memória.</span><span class="sxs-lookup"><span data-stu-id="d3c39-152">Therefore, when working with sources like JSON/XML, make sure to format the data into an in-memory collection.</span></span>

<span data-ttu-id="d3c39-153">Dada a coleção em memória a seguir:</span><span class="sxs-lookup"><span data-stu-id="d3c39-153">Given the following in-memory collection:</span></span>

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

<span data-ttu-id="d3c39-154">Carregue a coleção em memória em um [`IDataView`](xref:Microsoft.ML.IDataView) com o método [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*):</span><span class="sxs-lookup"><span data-stu-id="d3c39-154">Load the in-memory collection into an [`IDataView`](xref:Microsoft.ML.IDataView) with the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d3c39-155">O [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) pressupõe que o [`IEnumerable`](xref:System.Collections.IEnumerable) carregado é thread-safe.</span><span class="sxs-lookup"><span data-stu-id="d3c39-155">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) assumes that the [`IEnumerable`](xref:System.Collections.IEnumerable) it loads from is thread-safe.</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```
