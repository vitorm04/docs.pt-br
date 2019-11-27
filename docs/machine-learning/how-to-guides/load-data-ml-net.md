---
title: Carregar dados de arquivos e outras fontes
description: Saiba como carregar dados para processamento e treinamento no ML.NET usando a API. São armazenados em arquivos, bancos de dados, JSON, XML ou coleções na memória.
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: 83aaae2d2e75b3076841750bf5d505390a538bc0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344748"
---
# <a name="load-data-from-files-and-other-sources"></a>Carregar dados de arquivos e outras fontes

Saiba como carregar dados para processamento e treinamento no ML.NET usando a API. Originalmente, os dados são armazenados em arquivos ou outras fontes de dados, como bancos de dados, JSON, XML ou coleções na memória.

Se você estiver usando o construtor de modelos, consulte [carregar dados de treinamento no construtor de modelos](load-data-model-builder.md).

## <a name="create-the-data-model"></a>Criar o modelo de dados

O ML.NET permite que você defina modelos de dados por meio de classes. Por exemplo, considerando os seguintes dados de entrada:

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

Crie um modelo de dados que represente o snippet a seguir:

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

### <a name="annotating-the-data-model-with-column-attributes"></a>Anotando o modelo de dados com atributos de coluna

Atributos dão ao ML.NET mais informações sobre o modelo de dados e a fonte de dados.

O atributo [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) especifica os índices de colunas de suas propriedades.

> [!IMPORTANT]
> [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) é necessário apenas ao carregar dados de um arquivo.

Carregar colunas como:

- Colunas individuais como `Size` e `CurrentPrices` na classe `HousingData`.
- Como várias colunas por vez na forma de um vetor `HistoricalPrices` na classe `HousingData`.

Se você tiver uma propriedade de vetor, aplique o atributo [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) à propriedade em seu modelo de dados. É importante observar que todos os elementos no vetor precisam ser do mesmo tipo. Manter as colunas separadas permite a facilidade e a flexibilidade da engenharia de recursos, mas, para um número muito grande de colunas, a operação nas colunas individuais causa um impacto na velocidade de treinamento.

O ML.NET opera por meio de nomes de coluna. Se você quiser alterar o nome de uma coluna para algo diferente do nome de propriedade, use o atributo [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute). Ao criar objetos na memória, você ainda cria objetos usando o nome da propriedade. No entanto, para processar e criar modelos de machine learning, o ML.NET substitui e faz referência à propriedade com o valor fornecido no atributo [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute).

## <a name="load-data-from-a-single-file"></a>Carregar dados de um único arquivo

Para carregar dados de um arquivo, use o método [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) juntamente com o modelo de dados para os dados a serem carregados. Uma vez que o parâmetro `separatorChar` é delimitado por tabulação por padrão, altere-o para seu arquivo de dados conforme necessário. Se o arquivo tiver um cabeçalho, defina o parâmetro `hasHeader` como `true` para ignorar a primeira linha no arquivo e começar a carregar dados da segunda linha.

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a>Carregar dados de vários arquivos

Caso seus dados sejam armazenados em vários arquivos, desde que o esquema de dados seja o mesmo, o ML.NET permitirá que você carregue dados de vários arquivos que estejam no mesmo diretório ou em vários diretórios.

### <a name="load-from-files-in-a-single-directory"></a>Carregar de arquivos em um único diretório

Quando todos os seus arquivos de dados estão no mesmo diretório, use caracteres curinga no método [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*).

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a>Carregar de arquivos em vários diretórios

Para carregar dados de vários diretórios, use o método [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) para criar um [`TextLoader`](xref:Microsoft.ML.Data.TextLoader). Em seguida, use o método [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) e especifique os caminhos de arquivo individual (caracteres curinga não podem ser usados).

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-relational-database"></a>Carregar dados de um banco de dado relacional

O ML.NET dá suporte ao carregamento de dados de uma variedade de bancos de dado relacionais com suporte de [`System.Data`](xref:System.Data) que incluem SQL Server, banco de dados SQL do Azure, Oracle, SQLite, PostgreSQL, progresso, IBM DB2 e muitos outros.

> [!NOTE]
> Para usar `DatabaseLoader`, faça referência ao pacote NuGet [System. Data. SqlClient](https://www.nuget.org/packages/System.Data.SqlClient) .

Dado um banco de dados com uma tabela chamada `House` e o esquema a seguir:

```SQL
CREATE TABLE [House] (
    [HouseId] INT NOT NULL IDENTITY,
    [Size] INT NOT NULL,
    [NumBed] INT NOT NULL,
    [Price] REAL NOT NULL
    CONSTRAINT [PK_House] PRIMARY KEY ([HouseId])
);
```

Os dados podem ser modelados por uma classe como `HouseData`.

```csharp
public class HouseData
{
    public float Size { get; set; }

    public float NumBed { get; set; }

    public float Price { get; set; }
}
```

Em seguida, dentro do seu aplicativo, crie um `DatabaseLoader`.

```csharp
MLContext mlContext = new MLContext();

DatabaseLoader loader = mlContext.Data.CreateDatabaseLoader<HouseData>();
```

Defina a cadeia de conexão, bem como o comando SQL a ser executado no banco de dados e crie uma instância de `DatabaseSource`. Este exemplo usa um banco de dados SQL Server LocalDB com um caminho de arquivo. No entanto, o DatabaseLoader dá suporte a qualquer outra cadeia de conexão válida para bancos de dados locais e na nuvem.

```csharp
string connectionString = @"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=<YOUR-DB-FILEPATH>;Database=<YOUR-DB-NAME>;Integrated Security=True;Connect Timeout=30";

string sqlCommand = "SELECT Size, CAST(NumBed as REAL) as NumBed, Price FROM House";

DatabaseSource dbSource = new DatabaseSource(SqlClientFactory.Instance, connectionString, sqlCommand);
```

Dados numéricos que não sejam do tipo [`Real`](xref:System.Data.SqlDbType) precisarão ser convertidos em [`Real`](xref:System.Data.SqlDbType). O tipo de [`Real`](xref:System.Data.SqlDbType) é representado como um valor de ponto flutuante de precisão simples ou [`Single`](xref:System.Single), o tipo de entrada esperado por algoritmos ml.net. Neste exemplo, a coluna `NumBed` é um número inteiro no banco de dados. Usando a função interna `CAST`, ela é convertida em [`Real`](xref:System.Data.SqlDbType). Como a propriedade `Price` já é do tipo [`Real`](xref:System.Data.SqlDbType) ela é carregada como está.

Use o método `Load` para carregar os dados em um [`IDataView`](xref:Microsoft.ML.IDataView).

```csharp
IDataView data = loader.Load(dbSource);
```

## <a name="load-data-from-other-sources"></a>Carregar dados de outras fontes

Além de carregar os dados armazenados em arquivos, o ML.NET dá suporte ao carregamento de dados de várias fontes que incluem, mas não se limitam a:

- Coleções na memória
- JSON/XML

Observe que, ao trabalhar com fontes de streaming, o ML.NET espera que a entrada esteja na forma de uma coleção em memória. Portanto, ao trabalhar com fontes, como JSON/XML, formate os dados em uma coleção em memória.

Dada a coleção em memória a seguir:

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

Carregue a coleção em memória em um [`IDataView`](xref:Microsoft.ML.IDataView) com o método [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*):

> [!IMPORTANT]
> O [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) pressupõe que o [`IEnumerable`](xref:System.Collections.IEnumerable) carregado é thread-safe.

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```

## <a name="next-steps"></a>Próximas etapas

- Para limpar ou, de outra forma, processar dados, consulte [preparar dados para criar um modelo](prepare-data-ml-net.md).
- Quando estiver pronto para criar um modelo, consulte [treinar e avaliar um modelo](train-machine-learning-model-ml-net.md).
