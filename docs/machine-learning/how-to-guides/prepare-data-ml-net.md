---
title: Preparar dados para criar um modelo
description: Saiba como usar transformações no ML.NET para manipular e preparar dados para construção de modelo ou processamento adicional.
author: luisquintanilla
ms.author: luquinta
ms.date: 01/29/2020
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 12f933253af9ea519d711c20227fe075fed003de
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452981"
---
# <a name="prepare-data-for-building-a-model"></a>Preparar dados para criar um modelo

Saiba como usar o ML.NET para preparar dados para construção de modelo ou processamento adicional.

Dados geralmente não estão limpos e são esparsos. Os algoritmos de aprendizado de máquina ML.NET esperam que a entrada ou os recursos estejam em um único vetor numérico. Da mesma forma, o valor a prever (rótulo), especialmente quando se trata de dados categóricos, deve ser codificado. Portanto, uma das metas da preparação de dados é obter os dados no formato esperado por algoritmos do ML.NET.

## <a name="filter-data"></a>Filtrar dados

Às vezes, nem todos os dados em um conjunto de dados são relevantes para análise. Uma abordagem para remover dados irrelevantes é a filtragem. O [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) contém um conjunto de operações do filtro que recebem um [`IDataView`](xref:Microsoft.ML.IDataView) que contém todos os dados e o retorno de um [IDataView](xref:Microsoft.ML.IDataView) contendo apenas o pontos de interesse dos dados. É importante observar que, como operações de filtro não são um [`IEstimator`](xref:Microsoft.ML.IEstimator%601) ou [`ITransformer`](xref:Microsoft.ML.ITransformer) como aquelas no [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), elas não podem ser incluídas como parte de um pipeline de preparação de dados [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) ou [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601).

Pegue os seguintes dados de entrada e carregue-os em um [`IDataView`](xref:Microsoft.ML.IDataView) chamado `data`:

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

Para filtrar dados com base no valor de uma coluna, use o método [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A).

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

O exemplo acima usa linhas no conjunto de dados com um preço entre 200.000 e 1.000.000. O resultado da aplicação desse filtro retornaria apenas as duas últimas linhas nos dados e excluiria a primeira linha, pois seu preço é 100.000 e não está no intervalo especificado.

## <a name="replace-missing-values"></a>Substituir valores ausentes

Valores ausentes são uma ocorrência comum em conjuntos de dados. Uma abordagem para lidar com valores ausentes é substituí-los pelo valor padrão para o tipo fornecido, se houver, ou outro valor significativo, como o valor médio dos dados.

Pegue os seguintes dados de entrada e carregue-os em um [`IDataView`](xref:Microsoft.ML.IDataView) chamado `data`:

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

Observe que o último elemento em nossa lista tem um valor ausente para `Price`. Para substituir os valores ausentes na coluna `Price`, use o método [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) para preencher esse valor ausente.

> [!IMPORTANT]
> [`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) funciona somente com os dados numéricos.

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

O ML.NET dá suporte a vários [modos de substituição](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode). O exemplo acima usa o `Mean` modo de substituição, que preenche o valor ausente com o valor médio dessa coluna. O resultado da substituição preenche a propriedade `Price` para o último elemento em nossos dados com 200.000, pois é a média de 300.000 e de 100.000.

## <a name="use-normalizers"></a>Usar normalizadores

A [normalização](https://en.wikipedia.org/wiki/Feature_scaling) é uma técnica de pré-processamento de dados usada para dimensionar os recursos para estarem no mesmo intervalo, geralmente entre 0 e 1, para que eles possam ser processados com mais precisão por um algoritmo de aprendizado de máquina. Por exemplo, os intervalos de idade e renda variam significativamente com a idade, em geral, que está no intervalo de 0-100 e a renda geralmente está no intervalo de zero a milhares. Acesse a [página de transformações](../resources/transforms.md) para uma lista mais detalhada e uma descrição de transformações de normalização.

### <a name="min-max-normalization"></a>Normalização de Mín-Máx

Pegue os seguintes dados de entrada e carregue-os em um [`IDataView`](xref:Microsoft.ML.IDataView) chamado `data`:

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

A normalização pode ser aplicada a colunas com valores numéricos únicos e também vetores. Normalize os dados na coluna `Price` usando a normalização Mín-Máx com o método [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A).

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

Os valores de preço originais `[200000,100000]` são convertidos em `[ 1, 0.5 ]` usando a fórmula de normalização de `MinMax` que gera valores de saída no intervalo de 0-1.

### <a name="binning"></a>Compartimentalização

[Compartimentalização](https://en.wikipedia.org/wiki/Data_binning) converte valores contínuos em uma representação discreta da entrada. Por exemplo, suponha que um de seus recursos seja idade. Em vez de usar o valor real de idade, a compartimentalização cria intervalos para esse valor. 0-18 poderia ser um compartimento, outro poderia ser 19-35 e assim por diante.

Pegue os seguintes dados de entrada e carregue-os em um [`IDataView`](xref:Microsoft.ML.IDataView) chamado `data`:

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

Normalize os dados em compartimentos usando o método [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A). O parâmetro `maximumBinCount` permite que você especifique o número de compartimentos necessários para classificar seus dados. Neste exemplo, os dados serão colocados em dois compartimentos.

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

Um dos tipos de dados mais comuns são dados categóricos. Os dados categóricos têm um número finito de categorias. Por exemplo, os Estados dos EUA ou uma lista dos tipos de animais encontrados em um conjunto de imagens. Se os dados categóricos são recursos ou rótulos, eles devem ser mapeados em um valor numérico para que possam ser usados para gerar um modelo de aprendizado de máquina. Há várias maneiras de trabalhar com dados categóricos no ML.NET, dependendo do problema que você está resolvendo.

### <a name="key-value-mapping"></a>Mapeamento de valor de chave

No ML.NET, uma chave é um valor inteiro que representa uma categoria. O mapeamento de valor de chave é usado com mais frequência para mapear rótulos de cadeia de caracteres em valores inteiros exclusivos para treinamento e, em seguida, voltar para seus valores de cadeia de caracteres quando o modelo for usado para fazer uma previsão.

As transformações usadas para executar o mapeamento de valor de chave são [MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) e [MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A).

`MapValueToKey` adiciona um dicionário de mapeamentos no modelo, para que `MapKeyToValue` possa executar a transformação inversa ao fazer uma previsão.

### <a name="one-hot-encoding"></a>Uma codificação ativa

Uma codificação ativa usa um conjunto finito de valores e os mapeia em inteiros cuja representação binária tem um único valor `1` em posições exclusivas na cadeia de caracteres. Uma codificação ativa pode ser a melhor opção se não houver nenhuma ordem implícita dos dados categóricos. A tabela a seguir mostra um exemplo com CEPs como valores brutos.

|Valor bruto|Um valor codificado por quente|
|---------|---------------------|
|98052|00... 01|
|98100|00... 10|
|...|...|
|98109|10... 00|

A transformação para converter dados categóricos em números com codificação um-quente é [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A).

### <a name="hashing"></a>Hash

O hash é outra maneira de converter dados categóricos em números. Uma função de hash mapeia dados de um tamanho arbitrário (uma cadeia de caracteres de texto, por exemplo) para um número com um intervalo fixo. O hash pode ser uma maneira rápida e eficiente de recursos de vetorização. Um exemplo notável de hash no aprendizado de máquina é a filtragem de spam por email em que, em vez de manter um dicionário de palavras conhecidas, todas as palavras no email são codificadas e adicionadas a um vetor de recurso grande. O uso de hash dessa maneira evita o problema de burlação de filtragem de spam mal-intencionado pelo uso de palavras que não estão no dicionário.

O ML.NET fornece transformação de [hash](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A) para executar hash em texto, datas e dados numéricos. Assim como o mapeamento de chave de valor, as saídas da transformação de hash são tipos de chave.

## <a name="work-with-text-data"></a>Trabalhar com os dados de texto

Como dados categóricos, os dados de texto precisam ser transformados em recursos numéricos antes de usá-los para criar um modelo de aprendizado de máquina. Acesse a [página de transformações](../resources/transforms.md) para uma lista mais detalhada e uma descrição de transformações de texto.

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

O ML.NET fornece a [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) transformação que usa um valor de cadeia de caracteres de texto e cria um conjunto de recursos a partir do texto, aplicando uma série de transformações individuais.

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

A transformação resultante converte os valores de texto na coluna `Description` em um vetor numérico que é semelhante à saída abaixo:

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

As transformações que compõem `FeaturizeText` também podem ser aplicadas individualmente para exercer um controle mais detalhado sobre a geração de recursos.

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

`textEstimator` contém um subconjunto de operações realizadas pelo método [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A). O benefício de um pipeline mais complexo é a visibilidade e o controle sobre as transformações aplicadas aos dados.

Usando a primeira entrada como um exemplo, a seguir está uma descrição detalhada dos resultados produzidos pelas etapas de transformação definidas pelo `textEstimator`:

**Texto original: Este é um bom produto**

|Transformar | DESCRIÇÃO | Result
|--|--|--|
|1. NormalizeText | Converte todas as letras em minúsculas por padrão | este é um bom produto
|2. TokenizeWords | Divide a cadeia de caracteres em palavras individuais | ["este", "é", "um","bom","produto"]
|3. RemoveDefaultStopWords | Remove palavras irrelevantes, como *está* e *um*. | ["bom","produto"]
|4. MapValueToKey | Mapeia os valores para chaves (categorias) com base nos dados de entrada |  [1,2]
|5. ProduceNGrams | Transforma o texto em sequência de palavras consecutivas | [1,1,1,0,0]
|6. NormalizeLpNorm | Escala as entradas por sua lp-norm | [ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]
