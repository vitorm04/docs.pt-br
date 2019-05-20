---
title: Preparar Dados
description: Saiba como usar transformações no ML.NET para manipular e preparar dados para construção de modelo ou processamento adicional.
author: luisquintanilla
ms.author: luquinta
ms.date: 05/03/2019
ms.custom: mvc, how-to
ms.openlocfilehash: 461a00c6ecc1d9a8b9caaca79f9d7905d2bb7528
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063468"
---
# <a name="prepare-data"></a><span data-ttu-id="87824-103">Preparar Dados</span><span class="sxs-lookup"><span data-stu-id="87824-103">Prepare Data</span></span>

<span data-ttu-id="87824-104">Saiba como usar o ML.NET para preparar dados para construção de modelo ou processamento adicional.</span><span class="sxs-lookup"><span data-stu-id="87824-104">Learn how to use ML.NET to prepare data for additional processing or building a model.</span></span>

<span data-ttu-id="87824-105">Dados geralmente não estão limpos e são esparsos.</span><span class="sxs-lookup"><span data-stu-id="87824-105">Data is often unclean and sparse.</span></span> <span data-ttu-id="87824-106">Além disso, os algoritmos de aprendizado de máquina do ML.NET esperam que a entrada ou os recursos estejam em um único vetor numérico.</span><span class="sxs-lookup"><span data-stu-id="87824-106">Additionally, ML.NET machine learning algorithms expect input or features to be in a single numerical vector.</span></span> <span data-ttu-id="87824-107">Portanto, uma das metas da preparação de dados é obter os dados no formato esperado por algoritmos do ML.NET.</span><span class="sxs-lookup"><span data-stu-id="87824-107">Therefore one of the goals of data preparation is to get the data into the format expected by ML.NET algorithms.</span></span> 

## <a name="filter-data"></a><span data-ttu-id="87824-108">Filtrar dados</span><span class="sxs-lookup"><span data-stu-id="87824-108">Filter data</span></span>

<span data-ttu-id="87824-109">Às vezes, nem todos os dados em um conjunto de dados são relevantes para análise.</span><span class="sxs-lookup"><span data-stu-id="87824-109">Sometimes, not all data in a dataset is relevant for analysis.</span></span> <span data-ttu-id="87824-110">Uma abordagem para remover dados irrelevantes é a filtragem.</span><span class="sxs-lookup"><span data-stu-id="87824-110">An approach to remove irrelevant data is filtering.</span></span> <span data-ttu-id="87824-111">O [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) contém um conjunto de operações do filtro que recebem um [`IDataView`](xref:Microsoft.ML.IDataView) que contém todos os dados e o retorno de um [IDataView](xref:Microsoft.ML.IDataView) contendo apenas o pontos de interesse dos dados.</span><span class="sxs-lookup"><span data-stu-id="87824-111">The [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) contains a set of filter operations that take in an [`IDataView`](xref:Microsoft.ML.IDataView) containing all of the data and return an [IDataView](xref:Microsoft.ML.IDataView) containing only the data points of interest.</span></span> <span data-ttu-id="87824-112">É importante observar que, como operações de filtro não são um [`IEstimator`](xref:Microsoft.ML.IEstimator%601) ou [`ITransformer`](xref:Microsoft.ML.ITransformer) como aquelas no [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), elas não podem ser incluídas como parte de um pipeline de preparação de dados [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) ou [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601).</span><span class="sxs-lookup"><span data-stu-id="87824-112">It's important to note that because filter operations are not an [`IEstimator`](xref:Microsoft.ML.IEstimator%601) or [`ITransformer`](xref:Microsoft.ML.ITransformer) like those in the [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), they cannot be included as part of an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) or [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) data preparation pipeline.</span></span> 

<span data-ttu-id="87824-113">Usando os seguintes dados de entrada que são carregados em um [`IDataView`](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="87824-113">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="87824-114">Para filtrar dados com base no valor de uma coluna, use o método [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*).</span><span class="sxs-lookup"><span data-stu-id="87824-114">To filter data based on the value of a column, use the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) method.</span></span>

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

<span data-ttu-id="87824-115">O exemplo acima usa linhas no conjunto de dados com um preço entre 200.000 e 1.000.000.</span><span class="sxs-lookup"><span data-stu-id="87824-115">The sample above takes rows in the dataset with a price between 200000 and 1000000.</span></span> <span data-ttu-id="87824-116">O resultado da aplicação desse filtro retornaria apenas as duas últimas linhas nos dados e excluiria a primeira linha, pois seu preço é 100.000 e não está no intervalo especificado.</span><span class="sxs-lookup"><span data-stu-id="87824-116">The result of applying this filter would return only the last two rows in the data and exclude the first row because its price is 100000 and not between the specified range.</span></span>

## <a name="replace-missing-values"></a><span data-ttu-id="87824-117">Substituir valores ausentes</span><span class="sxs-lookup"><span data-stu-id="87824-117">Replace missing values</span></span>

<span data-ttu-id="87824-118">Valores ausentes são uma ocorrência comum em conjuntos de dados.</span><span class="sxs-lookup"><span data-stu-id="87824-118">Missing values are a common occurrence in datasets.</span></span> <span data-ttu-id="87824-119">Uma abordagem para lidar com valores ausentes é substituí-los pelo valor padrão para o tipo fornecido, se houver, ou outro valor significativo, como o valor médio dos dados.</span><span class="sxs-lookup"><span data-stu-id="87824-119">One approach to dealing with missing values is to replace them with the default value for the given type if any or another meaningful value such as the mean value in the data.</span></span> 

<span data-ttu-id="87824-120">Usando os seguintes dados de entrada que são carregados em um [`IDataView`](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="87824-120">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="87824-121">Observe que o último elemento em nossa lista tem um valor ausente para `Price`.</span><span class="sxs-lookup"><span data-stu-id="87824-121">Notice that the last element in our list has a missing value for `Price`.</span></span> <span data-ttu-id="87824-122">Para substituir os valores ausentes na coluna `Price`, use o método [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) para preencher esse valor ausente.</span><span class="sxs-lookup"><span data-stu-id="87824-122">To replace the missing values in the `Price` column, use the [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) method to fill in that missing value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="87824-123">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) funciona somente com os dados numéricos.</span><span class="sxs-lookup"><span data-stu-id="87824-123">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) only works with numerical data.</span></span>

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

<span data-ttu-id="87824-124">O ML.NET dá suporte a vários [modos de substituição](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span><span class="sxs-lookup"><span data-stu-id="87824-124">ML.NET supports various [replacement modes](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span></span> <span data-ttu-id="87824-125">O exemplo acima usa o modo de substituição `Mean` que preencherá o valor ausente com o valor da média da coluna.</span><span class="sxs-lookup"><span data-stu-id="87824-125">The sample above uses the `Mean` replacement mode which will fill in the missing value with that column's average value.</span></span> <span data-ttu-id="87824-126">O resultado da substituição preenche a propriedade `Price` para o último elemento em nossos dados com 200.000, pois é a média de 300.000 e de 100.000.</span><span class="sxs-lookup"><span data-stu-id="87824-126">The replacement 's result fills in the `Price` property for the last element in our data with 200,000 since it's the average of 100,000 and 300,000.</span></span> 

## <a name="use-normalizers"></a><span data-ttu-id="87824-127">Usar normalizadores</span><span class="sxs-lookup"><span data-stu-id="87824-127">Use normalizers</span></span>

<span data-ttu-id="87824-128">[Normalização](https://en.wikipedia.org/wiki/Feature_scaling) é uma técnica de pré-processamento de dados usada para padronizar os recursos que não estão na mesma escala, o que ajuda os algoritmos a convergir mais rapidamente.</span><span class="sxs-lookup"><span data-stu-id="87824-128">[Normalization](https://en.wikipedia.org/wiki/Feature_scaling) is a data pre-processing technique used to standardize features that are not on the same scale which helps algorithms converge faster.</span></span> <span data-ttu-id="87824-129">Por exemplo, os intervalos de valores, como idade e renda, variam significativamente, estando a idade geralmente no intervalo de 0 a 100 e a renda geralmente estando no intervalo de zero a milhares.</span><span class="sxs-lookup"><span data-stu-id="87824-129">For example, the ranges for values like age and income vary significantly with age generally being in the range of 0-100 and income generally being in the range of zero to thousands.</span></span> <span data-ttu-id="87824-130">Acesse a [página de transformações](../resources/transforms.md) para uma lista mais detalhada e uma descrição de transformações de normalização.</span><span class="sxs-lookup"><span data-stu-id="87824-130">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of normalization transforms.</span></span> 

### <a name="min-max-normalization"></a><span data-ttu-id="87824-131">Normalização de Mín-Máx</span><span class="sxs-lookup"><span data-stu-id="87824-131">Min-Max normalization</span></span>

<span data-ttu-id="87824-132">Usando os seguintes dados de entrada que são carregados em um [`IDataView`](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="87824-132">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="87824-133">Normalize os dados usando a normalização Mín-Máx com o método [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*).</span><span class="sxs-lookup"><span data-stu-id="87824-133">Normalize the data using min-max normalization using the [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) method.</span></span>

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

<span data-ttu-id="87824-134">Os valores originais de preço `[200000,100000]` são convertidos em `[ 1, 0.5 ]` usando a fórmula de normalização `MinMax` que gera valores de saída no intervalo de 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="87824-134">The original price values `[200000,100000]` are converted to `[ 1, 0.5 ]` using the `MinMax` normalization formula which generates output values in the range of 0-1.</span></span>

### <a name="binning"></a><span data-ttu-id="87824-135">Compartimentalização</span><span class="sxs-lookup"><span data-stu-id="87824-135">Binning</span></span>

<span data-ttu-id="87824-136">[Compartimentalização](https://en.wikipedia.org/wiki/Data_binning) converte valores contínuos em uma representação discreta da entrada.</span><span class="sxs-lookup"><span data-stu-id="87824-136">[Binning](https://en.wikipedia.org/wiki/Data_binning) converts continuous values into a discrete representation of the input.</span></span> <span data-ttu-id="87824-137">Por exemplo, suponha que um de seus recursos seja idade.</span><span class="sxs-lookup"><span data-stu-id="87824-137">For example, suppose one of your features is age.</span></span> <span data-ttu-id="87824-138">Em vez de usar o valor real de idade, a compartimentalização cria intervalos para esse valor.</span><span class="sxs-lookup"><span data-stu-id="87824-138">Instead of using the actual age value,  binning creates ranges for that value.</span></span> <span data-ttu-id="87824-139">0-18 poderia ser um compartimento, outro poderia ser 19-35 e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="87824-139">0-18 could be one bin, another could be 19-35 and so on.</span></span> 

<span data-ttu-id="87824-140">Usando os seguintes dados de entrada que são carregados em um [`IDataView`](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="87824-140">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="87824-141">Normalize os dados em compartimentos usando o método [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning*).</span><span class="sxs-lookup"><span data-stu-id="87824-141">Normalize the data into bins using the [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning*) method.</span></span> <span data-ttu-id="87824-142">O parâmetro `maximumBinCount` permite que você especifique o número de compartimentos necessários para classificar seus dados.</span><span class="sxs-lookup"><span data-stu-id="87824-142">The `maximumBinCount` parameter enables you to specify the number of bins needed to classify your data.</span></span> <span data-ttu-id="87824-143">Neste exemplo, os dados serão colocados em dois compartimentos.</span><span class="sxs-lookup"><span data-stu-id="87824-143">In this example, data will be put into two bins.</span></span>  

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

<span data-ttu-id="87824-144">O resultado de compartimentalização cria limites de compartimento de `[0,200000,Infinity]`.</span><span class="sxs-lookup"><span data-stu-id="87824-144">The result of binning creates bin bounds of `[0,200000,Infinity]`.</span></span> <span data-ttu-id="87824-145">Portanto os compartimentos resultantes são `[0,1,1]`, pois a primeira observação está entre 0 a 200.000 e os outros são maiores que 200.000, mas menores que infinito.</span><span class="sxs-lookup"><span data-stu-id="87824-145">Therefore the resulting bins are `[0,1,1]` because the first observation is between 0-200000 and the others are greater than 200000 but less than infinity.</span></span>

## <a name="work-with-categorical-data"></a><span data-ttu-id="87824-146">Trabalhar com os dados categóricos</span><span class="sxs-lookup"><span data-stu-id="87824-146">Work with categorical data</span></span>

<span data-ttu-id="87824-147">Dados categóricos não numéricos precisam ser convertido em um número antes de serem usados para criar um modelo de machine learning.</span><span class="sxs-lookup"><span data-stu-id="87824-147">Non-numeric categorical data needs to be converted to a number before being used to build a machine learning model.</span></span> 

<span data-ttu-id="87824-148">Usando os seguintes dados de entrada que são carregados em um [`IDataView`](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="87824-148">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="87824-149">A propriedade `VehicleType` categórica pode ser convertida em um número usando o método [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*).</span><span class="sxs-lookup"><span data-stu-id="87824-149">The categorical `VehicleType` property can be converted into a number using the [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*) method.</span></span> 

```csharp
// Define categorical transform estimator
var categoricalEstimator = mlContext.Transforms.Categorical.OneHotEncoding("VehicleType");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer categoricalTransformer = categoricalEstimator.Fit(data);

// Transform Data
IDataView transformedData = categoricalTransformer.Transform(data);
```

<span data-ttu-id="87824-150">A transformação resultante converte o valor de texto de `VehicleType` em um número.</span><span class="sxs-lookup"><span data-stu-id="87824-150">The resulting transform converts the text value of `VehicleType` to a number.</span></span> <span data-ttu-id="87824-151">As entradas na coluna `VehicleType` tornam-se o seguinte quando a transformação é aplicada:</span><span class="sxs-lookup"><span data-stu-id="87824-151">The entries in the `VehicleType` column become the following when the transform is applied:</span></span> 

```text
[
    1, // SUV
    2, // Sedan
    1 // SUV
]
```

## <a name="work-with-text-data"></a><span data-ttu-id="87824-152">Trabalhar com os dados de texto</span><span class="sxs-lookup"><span data-stu-id="87824-152">Work with text data</span></span>

<span data-ttu-id="87824-153">Dados de texto precisam ser transformados em números antes de serem usados para compilar um modelo de machine learning.</span><span class="sxs-lookup"><span data-stu-id="87824-153">Text data needs to be transformed into numbers before using it to build a machine learning model.</span></span> <span data-ttu-id="87824-154">Acesse a [página de transformações](../resources/transforms.md) para uma lista mais detalhada e uma descrição de transformações de texto.</span><span class="sxs-lookup"><span data-stu-id="87824-154">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of text transforms.</span></span>

<span data-ttu-id="87824-155">Usando dados, como os dados abaixo, que foram carregados em um [`IDataView`](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="87824-155">Using data like the data below that has been loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="87824-156">O mínimo de etapas para converter texto em uma representação numérica do vetor é usar o método [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*).</span><span class="sxs-lookup"><span data-stu-id="87824-156">The minimum step to convert text to a numerical vector representation is to use the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) method.</span></span> <span data-ttu-id="87824-157">Usando a transformação [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*), uma série de transformações é aplicada à coluna de texto de entrada, resultando em um vetor numérico que representa a palavra normalizada para lp e caractere ngrams.</span><span class="sxs-lookup"><span data-stu-id="87824-157">By using the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) transform, a series of transformations is applied to the input text column resulting in a numerical vector representing the lp-normalized word and character ngrams.</span></span> 

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

<span data-ttu-id="87824-158">A transformação resultante converteria os valores de texto na coluna `Description` a um vetor numérico semelhante à saída abaixo:</span><span class="sxs-lookup"><span data-stu-id="87824-158">The resulting transform would convert the text values in the `Description` column to a numerical vector that looks similar to the output below:</span></span>

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

<span data-ttu-id="87824-159">Combine etapas de processamento de texto complexas em um [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) para remover o ruído e potencialmente reduzir a quantidade de recursos de processamento exigidos conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="87824-159">Combine complex text processing steps into an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) to remove noise and potentially reduce the amount of required processing resources as needed.</span></span>

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

<span data-ttu-id="87824-160">`textEstimator` contém um subconjunto de operações realizadas pelo método [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*).</span><span class="sxs-lookup"><span data-stu-id="87824-160">`textEstimator` contains a subset of operations performed by the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) method.</span></span> <span data-ttu-id="87824-161">O benefício de um pipeline mais complexo é a visibilidade e o controle sobre as transformações aplicadas aos dados.</span><span class="sxs-lookup"><span data-stu-id="87824-161">The benefit of a more complex pipeline is control and visibility over the transformations applied to the data.</span></span> 

<span data-ttu-id="87824-162">Usando a primeira entrada como um exemplo, a seguir está uma descrição detalhada dos resultados produzidos pelas etapas de transformação definidas pelo `textEstimator`:</span><span class="sxs-lookup"><span data-stu-id="87824-162">Using the first entry as an example, the following is a detailed description of the results produced by the transformation steps defined by `textEstimator`:</span></span>

<span data-ttu-id="87824-163">**Texto original: Este é um bom produto**</span><span class="sxs-lookup"><span data-stu-id="87824-163">**Original Text: This is a good product**</span></span>

|<span data-ttu-id="87824-164">Transformar</span><span class="sxs-lookup"><span data-stu-id="87824-164">Transform</span></span> | <span data-ttu-id="87824-165">Descrição</span><span class="sxs-lookup"><span data-stu-id="87824-165">Description</span></span> | <span data-ttu-id="87824-166">Resultado</span><span class="sxs-lookup"><span data-stu-id="87824-166">Result</span></span>
|--|--|--|
|<span data-ttu-id="87824-167">1. NormalizeText</span><span class="sxs-lookup"><span data-stu-id="87824-167">1. NormalizeText</span></span> | <span data-ttu-id="87824-168">Converte todas as letras em minúsculas por padrão</span><span class="sxs-lookup"><span data-stu-id="87824-168">Converts all letters to lowercase by default</span></span> | <span data-ttu-id="87824-169">este é um bom produto</span><span class="sxs-lookup"><span data-stu-id="87824-169">this is a good product</span></span>
|<span data-ttu-id="87824-170">2. TokenizeWords</span><span class="sxs-lookup"><span data-stu-id="87824-170">2. TokenizeWords</span></span> | <span data-ttu-id="87824-171">Divide a cadeia de caracteres em palavras individuais</span><span class="sxs-lookup"><span data-stu-id="87824-171">Splits string into individual words</span></span> | <span data-ttu-id="87824-172">["este", "é", "um","bom","produto"]</span><span class="sxs-lookup"><span data-stu-id="87824-172">["this","is","a","good","product"]</span></span>
|<span data-ttu-id="87824-173">3. RemoveDefaultStopWords</span><span class="sxs-lookup"><span data-stu-id="87824-173">3. RemoveDefaultStopWords</span></span> | <span data-ttu-id="87824-174">Remove palavras irrelevantes, como *está* e *um*.</span><span class="sxs-lookup"><span data-stu-id="87824-174">Removes stopwords like *is* and *a*.</span></span> | <span data-ttu-id="87824-175">["bom","produto"]</span><span class="sxs-lookup"><span data-stu-id="87824-175">["good","product"]</span></span>
|<span data-ttu-id="87824-176">4. MapValueToKey</span><span class="sxs-lookup"><span data-stu-id="87824-176">4. MapValueToKey</span></span> | <span data-ttu-id="87824-177">Mapeia os valores para chaves (categorias) com base nos dados de entrada</span><span class="sxs-lookup"><span data-stu-id="87824-177">Maps the values to keys (categories) based on the input data</span></span> |  <span data-ttu-id="87824-178">[1,2]</span><span class="sxs-lookup"><span data-stu-id="87824-178">[1,2]</span></span>
|<span data-ttu-id="87824-179">5. ProduceNGrams</span><span class="sxs-lookup"><span data-stu-id="87824-179">5. ProduceNGrams</span></span> | <span data-ttu-id="87824-180">Transforma o texto em sequência de palavras consecutivas</span><span class="sxs-lookup"><span data-stu-id="87824-180">Transforms text into sequence of consecutive words</span></span> | <span data-ttu-id="87824-181">[1,1,1,0,0]</span><span class="sxs-lookup"><span data-stu-id="87824-181">[1,1,1,0,0]</span></span>
|<span data-ttu-id="87824-182">6. NormalizeLpNorm</span><span class="sxs-lookup"><span data-stu-id="87824-182">6. NormalizeLpNorm</span></span> | <span data-ttu-id="87824-183">Escala as entradas por sua lp-norm</span><span class="sxs-lookup"><span data-stu-id="87824-183">Scale inputs by their lp-norm</span></span> | <span data-ttu-id="87824-184">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span><span class="sxs-lookup"><span data-stu-id="87824-184">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span></span>
