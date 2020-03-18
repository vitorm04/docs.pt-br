---
title: Preparar dados para criar um modelo
description: Saiba como usar transformações no ML.NET para manipular e preparar dados para construção de modelo ou processamento adicional.
author: luisquintanilla
ms.author: luquinta
ms.date: 01/29/2020
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 12f933253af9ea519d711c20227fe075fed003de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77452981"
---
# <a name="prepare-data-for-building-a-model"></a>Preparar dados para criar um modelo

Saiba como usar o ML.NET para preparar dados para construção de modelo ou processamento adicional.

Dados geralmente não estão limpos e são esparsos. ML.NET algoritmos de aprendizado de máquina esperam que a entrada ou os recursos estejam em um único vetor numérico. Da mesma forma, o valor para prever (rótulo), especialmente quando são dados categóricos, tem que ser codificado. Portanto, uma das metas da preparação de dados é obter os dados no formato esperado por algoritmos do ML.NET.

## <a name="filter-data"></a>Filtrar dados

Às vezes, nem todos os dados em um conjunto de dados são relevantes para análise. Uma abordagem para remover dados irrelevantes é a filtragem. O [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) contém um conjunto de operações de filtro que levam em um [`IDataView`](xref:Microsoft.ML.IDataView) contendo todos os dados e retornam um [IDataView](xref:Microsoft.ML.IDataView) contendo apenas os pontos de interesse dos dados. É importante notar que, como as [`IEstimator`](xref:Microsoft.ML.IEstimator%601) operações de filtro não são [`ITransformer`](xref:Microsoft.ML.ITransformer) ou como as do [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), elas não podem ser incluídas como parte de um [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) pipeline ou [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) de preparação de dados.

Pegue os seguintes dados de [`IDataView`](xref:Microsoft.ML.IDataView) `data`entrada e carregue-os em um chamado:

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

Para filtrar dados com base no [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) valor de uma coluna, use o método.

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

O exemplo acima usa linhas no conjunto de dados com um preço entre 200.000 e 1.000.000. O resultado da aplicação desse filtro retornaria apenas as duas últimas linhas nos dados e excluiria a primeira linha, pois seu preço é 100.000 e não está no intervalo especificado.

## <a name="replace-missing-values"></a>Substituir valores ausentes

Valores ausentes são uma ocorrência comum em conjuntos de dados. Uma abordagem para lidar com valores ausentes é substituí-los pelo valor padrão para o tipo fornecido, se houver, ou outro valor significativo, como o valor médio dos dados.

Pegue os seguintes dados de [`IDataView`](xref:Microsoft.ML.IDataView) `data`entrada e carregue-os em um chamado:

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

Observe que o último elemento em nossa lista tem um valor ausente para `Price`. Para substituir os valores perdidos na `Price` coluna, use o [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) método para preencher esse valor perdido.

> [!IMPORTANT]
> [`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A)só funciona com dados numéricos.

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

O ML.NET dá suporte a vários [modos de substituição](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode). A amostra acima `Mean` usa o modo de substituição, que preenche o valor faltante com o valor médio dessa coluna. O resultado da substituição preenche a propriedade `Price` para o último elemento em nossos dados com 200.000, pois é a média de 300.000 e de 100.000.

## <a name="use-normalizers"></a>Usar normalizadores

[A normalização](https://en.wikipedia.org/wiki/Feature_scaling) é uma técnica de pré-processamento de dados usada para dimensionar recursos para estar na mesma faixa, geralmente entre 0 e 1, para que possam ser processados com mais precisão por um algoritmo de aprendizagem de máquina. Por exemplo, as faixas de idade e renda variam significativamente com a idade geralmente na faixa de 0-100 e a renda geralmente estando na faixa de zero a milhares. Acesse a [página de transformações](../resources/transforms.md) para uma lista mais detalhada e uma descrição de transformações de normalização.

### <a name="min-max-normalization"></a>Normalização de Mín-Máx

Pegue os seguintes dados de [`IDataView`](xref:Microsoft.ML.IDataView) `data`entrada e carregue-os em um chamado:

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

A normalização pode ser aplicada a colunas com valores numéricos únicos e também vetores. Normalize os dados `Price` na coluna usando a normalização min-max com o [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) método.

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

Os valores `[200000,100000]` de preço `[ 1, 0.5 ]` originais são convertidos em utilização da `MinMax` fórmula de normalização que gera valores de saída na faixa de 0-1.

### <a name="binning"></a>Compartimentalização

[Compartimentalização](https://en.wikipedia.org/wiki/Data_binning) converte valores contínuos em uma representação discreta da entrada. Por exemplo, suponha que um de seus recursos seja idade. Em vez de usar o valor real de idade, a compartimentalização cria intervalos para esse valor. 0-18 poderia ser um compartimento, outro poderia ser 19-35 e assim por diante.

Pegue os seguintes dados de [`IDataView`](xref:Microsoft.ML.IDataView) `data`entrada e carregue-os em um chamado:

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

Normalize os dados em [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A) lixeiras usando o método. O parâmetro `maximumBinCount` permite que você especifique o número de compartimentos necessários para classificar seus dados. Neste exemplo, os dados serão colocados em dois compartimentos.

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

Um dos tipos de dados mais comuns são os dados categóricos. Os dados categóricos têm um número finito de categorias. Por exemplo, os estados dos EUA, ou uma lista dos tipos de animais encontrados em um conjunto de fotos. Se os dados categóricos são características ou rótulos, eles devem ser mapeados em um valor numérico para que possam ser usados para gerar um modelo de aprendizado de máquina. Existem várias maneiras de trabalhar com dados categóricos em ML.NET, dependendo do problema que você está resolvendo.

### <a name="key-value-mapping"></a>Mapeamento de valor-chave

Em ML.NET, uma chave é um valor inteiro que representa uma categoria. O mapeamento de valor-chave é mais frequentemente usado para mapear rótulos de strings em valores inteiros únicos para treinamento, em seguida, de volta aos seus valores de seqüência quando o modelo é usado para fazer uma previsão.

As transformações usadas para realizar mapeamento de valor-chave são [MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) e [MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A).

`MapValueToKey`adiciona um dicionário de mapeamentos no `MapKeyToValue` modelo, para que possa realizar a transformação inversa ao fazer uma previsão.

### <a name="one-hot-encoding"></a>Uma codificação quente

Uma codificação quente pega um conjunto finito de valores e mapeia-os em inteiros cuja representação binária tem um único `1` valor em posições únicas na string. Uma codificação quente pode ser a melhor escolha se não houver uma ordem implícita dos dados categóricos. A tabela a seguir mostra um exemplo com CEP como valores brutos.

|Valor bruto|Um valor codificado quente|
|---------|---------------------|
|98052|00...01|
|98100|00...10|
|...|...|
|98109|10...00|

A transformação para converter dados categóricos [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A)em números codificados de um único hot é .

### <a name="hashing"></a>Hash

Hashing é outra maneira de converter dados categóricos em números. Uma função hash mapeia dados de um tamanho arbitrário (uma seqüência de texto, por exemplo) em um número com um intervalo fixo. O hashing pode ser uma maneira rápida e eficiente de espaço de vetorização de recursos. Um exemplo notável de hashing no aprendizado de máquina é a filtragem de spam de e-mail onde, em vez de manter um dicionário de palavras conhecidas, cada palavra no e-mail é hashed e adicionada a um grande vetor de recursos. O uso de hashs dessa forma evita o problema da filtragem de spam maliciosa pelo uso de palavras que não estão no dicionário.

ML.NET fornece a transformação [hash](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A) para executar hashing em texto, datas e dados numéricos. Como mapeamento de tecla de valor, as saídas da transformação de hash são tipos-chave.

## <a name="work-with-text-data"></a>Trabalhar com os dados de texto

Como dados categóricos, os dados de texto precisam ser transformados em recursos numéricos antes de usá-los para construir um modelo de aprendizado de máquina. Acesse a [página de transformações](../resources/transforms.md) para uma lista mais detalhada e uma descrição de transformações de texto.

Usando dados como os dados abaixo que [`IDataView`](xref:Microsoft.ML.IDataView)foram carregados em um:

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

ML.NET fornece [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) a transformação que leva o valor da seqüência de texto e cria um conjunto de recursos a partir do texto, aplicando uma série de transformações individuais.

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

A transformação resultante converte os `Description` valores de texto na coluna para um vetor numérico que se parece com a saída abaixo:

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

As transformações que `FeaturizeText` compõem também podem ser aplicadas individualmente para um controle mais fino de grãos sobre a geração de recursos.

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

`textEstimator`contém um subconjunto de [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) operações realizadas pelo método. O benefício de um pipeline mais complexo é a visibilidade e o controle sobre as transformações aplicadas aos dados.

Usando a primeira entrada como um exemplo, a seguir está uma descrição detalhada dos resultados produzidos pelas etapas de transformação definidas pelo `textEstimator`:

**Texto Original: Este é um bom produto**

|Transformar | Descrição | Result
|--|--|--|
|1. NormalizeText | Converte todas as letras em minúsculas por padrão | este é um bom produto
|2. TokenizeWords | Divide a cadeia de caracteres em palavras individuais | ["este", "é", "um","bom","produto"]
|3. RemoverDefaultStopWords | Remove palavras irrelevantes, como *está* e *um*. | ["bom","produto"]
|4. MapValueToKey | Mapeia os valores para chaves (categorias) com base nos dados de entrada |  [1,2]
|5. ProduzirNGramas | Transforma o texto em sequência de palavras consecutivas | [1,1,1,0,0]
|6. NormalizeLpNorm | Escala as entradas por sua lp-norm | [ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]
