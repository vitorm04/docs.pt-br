---
title: Preparar dados para criar um modelo
description: Saiba como usar transformações no ML.NET para manipular e preparar dados para construção de modelo ou processamento adicional.
author: luisquintanilla
ms.author: luquinta
ms.date: 09/11/2019
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 4452aef351f33df532f3c673307dedbbf71631b8
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929366"
---
# <a name="prepare-data-for-building-a-model"></a>Preparar dados para criar um modelo

Saiba como usar o ML.NET para preparar dados para construção de modelo ou processamento adicional.

Dados geralmente não estão limpos e são esparsos. Os algoritmos de aprendizado de máquina ML.NET esperam que a entrada ou os recursos estejam em um único vetor numérico. Da mesma forma, o valor a prever (rótulo), especialmente quando se trata de dados categóricos, deve ser codificado. Portanto, uma das metas da preparação de dados é obter os dados no formato esperado por algoritmos do ML.NET. 

## <a name="filter-data"></a>Filtrar dados

Às vezes, nem todos os dados em um conjunto de dados são relevantes para análise. Uma abordagem para remover dados irrelevantes é a filtragem. O [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) contém um conjunto de operações do filtro que recebem um [`IDataView`](xref:Microsoft.ML.IDataView) que contém todos os dados e o retorno de um [IDataView](xref:Microsoft.ML.IDataView) contendo apenas o pontos de interesse dos dados. É importante observar que, como operações de filtro não são um [`IEstimator`](xref:Microsoft.ML.IEstimator%601) ou [`ITransformer`](xref:Microsoft.ML.ITransformer) como aquelas no [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), elas não podem ser incluídas como parte de um pipeline de preparação de dados [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) ou [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601). 

Usando os seguintes dados de entrada que são carregados em um [`IDataView`](xref:Microsoft.ML.IDataView):

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms=1f,
        Price=100000f
    },
    new HomeData
    {
        NumberOfBedrooms=2f,
        Price=300000f
    },
    new HomeData
    {
        NumberOfBedrooms=6f,
        Price=600000f
    }
};
```

Para filtrar dados com base no valor de uma coluna, use o método [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*).

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

O exemplo acima usa linhas no conjunto de dados com um preço entre 200.000 e 1.000.000. O resultado da aplicação desse filtro retornaria apenas as duas últimas linhas nos dados e excluiria a primeira linha, pois seu preço é 100.000 e não está no intervalo especificado.

## <a name="replace-missing-values"></a>Substituir valores ausentes

Valores ausentes são uma ocorrência comum em conjuntos de dados. Uma abordagem para lidar com valores ausentes é substituí-los pelo valor padrão para o tipo fornecido, se houver, ou outro valor significativo, como o valor médio dos dados. 

Usando os seguintes dados de entrada que são carregados em um [`IDataView`](xref:Microsoft.ML.IDataView):

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms=1f,
        Price=100000f
    },
    new HomeData
    {
        NumberOfBedrooms=2f,
        Price=300000f
    },
    new HomeData
    {
        NumberOfBedrooms=6f,
        Price=float.NaN
    }
};
```

Observe que o último elemento em nossa lista tem um valor ausente para `Price`. Para substituir os valores ausentes na coluna `Price`, use o método [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) para preencher esse valor ausente.

> [!IMPORTANT]
> [`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) funciona somente com os dados numéricos.

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

O ML.NET dá suporte a vários [modos de substituição](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode). O exemplo acima usa o modo de substituição `Mean` que preencherá o valor ausente com o valor da média da coluna. O resultado da substituição preenche a propriedade `Price` para o último elemento em nossos dados com 200.000, pois é a média de 300.000 e de 100.000. 

## <a name="use-normalizers"></a>Usar normalizadores

[Normalização](https://en.wikipedia.org/wiki/Feature_scaling) é uma técnica de pré-processamento de dados usada para padronizar os recursos que não estão na mesma escala, o que ajuda os algoritmos a convergir mais rapidamente. Por exemplo, os intervalos de valores, como idade e renda, variam significativamente, estando a idade geralmente no intervalo de 0 a 100 e a renda geralmente estando no intervalo de zero a milhares. Acesse a [página de transformações](../resources/transforms.md) para uma lista mais detalhada e uma descrição de transformações de normalização. 

### <a name="min-max-normalization"></a>Normalização de Mín-Máx

Usando os seguintes dados de entrada que são carregados em um [`IDataView`](xref:Microsoft.ML.IDataView):

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms = 2f,
        Price = 200000f
    },
    new HomeData
    {
        NumberOfBedrooms = 1f,
        Price = 100000f
    }
};
```

A normalização pode ser aplicada a colunas com valores numéricos únicos e também vetores. Normalize os dados na coluna `Price` usando a normalização Mín-Máx com o método [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*).

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

Os valores originais de preço `[200000,100000]` são convertidos em `[ 1, 0.5 ]` usando a fórmula de normalização `MinMax` que gera valores de saída no intervalo de 0 a 1.

### <a name="binning"></a>Compartimentalização

[Compartimentalização](https://en.wikipedia.org/wiki/Data_binning) converte valores contínuos em uma representação discreta da entrada. Por exemplo, suponha que um de seus recursos seja idade. Em vez de usar o valor real de idade, a compartimentalização cria intervalos para esse valor. 0-18 poderia ser um compartimento, outro poderia ser 19-35 e assim por diante. 

Usando os seguintes dados de entrada que são carregados em um [`IDataView`](xref:Microsoft.ML.IDataView):

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms=1f,
        Price=100000f
    },
    new HomeData
    {
        NumberOfBedrooms=2f,
        Price=300000f
    },
    new HomeData
    {
        NumberOfBedrooms=6f,
        Price=600000f
    }
};
```

Normalize os dados em compartimentos usando o método [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning*). O parâmetro `maximumBinCount` permite que você especifique o número de compartimentos necessários para classificar seus dados. Neste exemplo, os dados serão colocados em dois compartimentos.  

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

O resultado de compartimentalização cria limites de compartimento de `[0,200000,Infinity]`. Portanto os compartimentos resultantes são `[0,1,1]`, pois a primeira observação está entre 0 a 200.000 e os outros são maiores que 200.000, mas menores que infinito.

## <a name="work-with-categorical-data"></a>Trabalhar com os dados categóricos

Dados categóricos não numéricos precisam ser convertido em um número antes de serem usados para criar um modelo de machine learning. 

Usando os seguintes dados de entrada que são carregados em um [`IDataView`](xref:Microsoft.ML.IDataView):

```csharp
CarData[] cars = new CarData[] 
{
    new CarData
    {
        Color="Red",
        VehicleType="SUV"
    },
    new CarData
    {
        Color="Blue",
        VehicleType="Sedan"
    },
    new CarData
    {
        Color="Black",
        VehicleType="SUV"
    }
};
```

A propriedade `VehicleType` categórica pode ser convertida em um número usando o método [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*). 

```csharp
// Define categorical transform estimator
var categoricalEstimator = mlContext.Transforms.Categorical.OneHotEncoding("VehicleType");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer categoricalTransformer = categoricalEstimator.Fit(data);

// Transform Data
IDataView transformedData = categoricalTransformer.Transform(data);
```

A transformação resultante converte o valor de texto de `VehicleType` em um número. As entradas na coluna `VehicleType` tornam-se o seguinte quando a transformação é aplicada: 

```text
[
    1, // SUV
    2, // Sedan
    1 // SUV
]
```

## <a name="work-with-text-data"></a>Trabalhar com os dados de texto

Dados de texto precisam ser transformados em números antes de serem usados para compilar um modelo de machine learning. Acesse a [página de transformações](../resources/transforms.md) para uma lista mais detalhada e uma descrição de transformações de texto.

Usando dados, como os dados abaixo, que foram carregados em um [`IDataView`](xref:Microsoft.ML.IDataView):

```csharp
ReviewData[] reviews = new ReviewData[]
{
    new ReviewData
    {
        Description="This is a good product",
        Rating=4.7f
    },
    new ReviewData
    {
        Description="This is a bad product",
        Rating=2.3f
    }
};
```

O mínimo de etapas para converter texto em uma representação numérica do vetor é usar o método [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*). Usando a transformação [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*), uma série de transformações é aplicada à coluna de texto de entrada, resultando em um vetor numérico que representa a palavra normalizada para lp e caractere ngrams. 

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

A transformação resultante converteria os valores de texto na coluna `Description` a um vetor numérico semelhante à saída abaixo:

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

Combine etapas de processamento de texto complexas em um [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) para remover o ruído e potencialmente reduzir a quantidade de recursos de processamento exigidos conforme necessário.

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

`textEstimator` contém um subconjunto de operações realizadas pelo método [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*). O benefício de um pipeline mais complexo é a visibilidade e o controle sobre as transformações aplicadas aos dados. 

Usando a primeira entrada como um exemplo, a seguir está uma descrição detalhada dos resultados produzidos pelas etapas de transformação definidas pelo `textEstimator`:

**Texto original: Este é um bom produto**

|Transformar | Descrição | Resultado
|--|--|--|
|1. NormalizeText | Converte todas as letras em minúsculas por padrão | este é um bom produto
|2. TokenizeWords | Divide a cadeia de caracteres em palavras individuais | ["este", "é", "um","bom","produto"]
|3. RemoveDefaultStopWords | Remove palavras irrelevantes, como *está* e *um*. | ["bom","produto"]
|4. MapValueToKey | Mapeia os valores para chaves (categorias) com base nos dados de entrada |  [1,2]
|5. ProduceNGrams | Transforma o texto em sequência de palavras consecutivas | [1,1,1,0,0]
|6. NormalizeLpNorm | Escala as entradas por sua lp-norm | [ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]
