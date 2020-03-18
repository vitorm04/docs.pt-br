---
title: Carregar dados de arquivos e outras fontes
description: Aprenda a carregar dados para processamento e treinamento em ML.NET usando a API. Os dados são armazenados em arquivos, bancos de dados, JSON, XML ou coleções na memória.
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: 83aaae2d2e75b3076841750bf5d505390a538bc0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74344748"
---
# <a name="load-data-from-files-and-other-sources"></a>Carregar dados de arquivos e outras fontes

Aprenda a carregar dados para processamento e treinamento em ML.NET usando a API. Originalmente, os dados são armazenados em arquivos ou outras fontes de dados, como bancos de dados, JSON, XML ou coleções na memória.

Se você estiver usando o Model Builder, consulte [Carregar dados de treinamento no Model Builder](load-data-model-builder.md).

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

O [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) atributo especifica os índices da coluna de suas propriedades.

> [!IMPORTANT]
> [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute)só é necessário ao carregar dados de um arquivo.

Carregar colunas como:

- Colunas individuais como `Size` e `CurrentPrices` na classe `HousingData`.
- Como várias colunas por vez na forma de um vetor `HistoricalPrices` na classe `HousingData`.

Se você tiver uma propriedade [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) vetorial, aplique o atributo à propriedade em seu modelo de dados. É importante observar que todos os elementos no vetor precisam ser do mesmo tipo. Manter as colunas separadas permite a facilidade e a flexibilidade da engenharia de recursos, mas, para um número muito grande de colunas, a operação nas colunas individuais causa um impacto na velocidade de treinamento.

O ML.NET opera por meio de nomes de coluna. Se você quiser mudar o nome de uma coluna para [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) algo diferente do nome da propriedade, use o atributo. Ao criar objetos na memória, você ainda cria objetos usando o nome da propriedade. No entanto, para o processamento de dados e construção de modelos de [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) machine learning, ML.NET substitui e faz referência ao imóvel com o valor fornecido no atributo.

## <a name="load-data-from-a-single-file"></a>Carregar dados de um único arquivo

Para carregar dados de [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) um arquivo, use o método juntamente com o modelo de dados para que os dados sejam carregados. Uma vez que o parâmetro `separatorChar` é delimitado por tabulação por padrão, altere-o para seu arquivo de dados conforme necessário. Se o arquivo tiver um cabeçalho, defina o parâmetro `hasHeader` como `true` para ignorar a primeira linha no arquivo e começar a carregar dados da segunda linha.

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a>Carregar dados de vários arquivos

Caso seus dados sejam armazenados em vários arquivos, desde que o esquema de dados seja o mesmo, o ML.NET permitirá que você carregue dados de vários arquivos que estejam no mesmo diretório ou em vários diretórios.

### <a name="load-from-files-in-a-single-directory"></a>Carregar de arquivos em um único diretório

Quando todos os seus arquivos de dados estiverem no [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) mesmo diretório, use curingas no método.

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a>Carregar de arquivos em vários diretórios

Para carregar dados de vários [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) diretórios, [`TextLoader`](xref:Microsoft.ML.Data.TextLoader)use o método para criar um . Em seguida, [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) use o método e especifique os caminhos de arquivo individuais (curingas não podem ser usados).

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-relational-database"></a>Carregar dados de um banco de dados relacional

ML.NET suporta o carregamento de dados de uma [`System.Data`](xref:System.Data) variedade de bancos de dados relacionais suportados por isso incluem SQL Server, Azure SQL Database, Oracle, SQLite, PostgreSQL, Progress, IBM DB2 e muito mais.

> [!NOTE]
> Para `DatabaseLoader`usar, consulte o pacote [System.Data.SqlClient](https://www.nuget.org/packages/System.Data.SqlClient) NuGet.

Dado um banco `House` de dados com uma tabela nomeada e o seguinte esquema:

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

Então, dentro de sua `DatabaseLoader`aplicação, crie um .

```csharp
MLContext mlContext = new MLContext();

DatabaseLoader loader = mlContext.Data.CreateDatabaseLoader<HouseData>();
```

Defina sua seqüência de conexões, bem como o comando `DatabaseSource` SQL a ser executado no banco de dados e crie uma instância. Esta amostra usa um banco de dados LocalDB SQL Server com um caminho de arquivo. No entanto, o DatabaseLoader suporta qualquer outra seqüência de conexão válida para bancos de dados no local e na nuvem.

```csharp
string connectionString = @"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=<YOUR-DB-FILEPATH>;Database=<YOUR-DB-NAME>;Integrated Security=True;Connect Timeout=30";

string sqlCommand = "SELECT Size, CAST(NumBed as REAL) as NumBed, Price FROM House";

DatabaseSource dbSource = new DatabaseSource(SqlClientFactory.Instance, connectionString, sqlCommand);
```

Dados numéricos que não [`Real`](xref:System.Data.SqlDbType) sejam do tipo [`Real`](xref:System.Data.SqlDbType)devem ser convertidos em . O [`Real`](xref:System.Data.SqlDbType) tipo é representado como um valor [`Single`](xref:System.Single)de ponto flutuante de precisão única ou , o tipo de entrada esperado por algoritmos ML.NET. Nesta amostra, `NumBed` a coluna é um inteiro no banco de dados. Usando `CAST` a função incorporada, ela é [`Real`](xref:System.Data.SqlDbType)convertida em . Como `Price` a propriedade já [`Real`](xref:System.Data.SqlDbType) é do tipo que está carregada como está.

Use `Load` o método para carregar [`IDataView`](xref:Microsoft.ML.IDataView)os dados em um .

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

Carregue a coleção na [`IDataView`](xref:Microsoft.ML.IDataView) memória [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) em um com o método:

> [!IMPORTANT]
> [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*)assume que [`IEnumerable`](xref:System.Collections.IEnumerable) o que ele carrega é seguro para rosca.

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```

## <a name="next-steps"></a>Próximas etapas

- Para limpar ou processar dados, consulte [Preparar dados para a construção de um modelo](prepare-data-ml-net.md).
- Quando estiver pronto para construir um modelo, consulte [Treinar e avaliar um modelo](train-machine-learning-model-ml-net.md).
