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
# <a name="prepare-data-for-building-a-model"></a><span data-ttu-id="ed041-103">Preparar dados para criar um modelo</span><span class="sxs-lookup"><span data-stu-id="ed041-103">Prepare data for building a model</span></span>

<span data-ttu-id="ed041-104">Saiba como usar o ML.NET para preparar dados para construção de modelo ou processamento adicional.</span><span class="sxs-lookup"><span data-stu-id="ed041-104">Learn how to use ML.NET to prepare data for additional processing or building a model.</span></span>

<span data-ttu-id="ed041-105">Dados geralmente não estão limpos e são esparsos.</span><span class="sxs-lookup"><span data-stu-id="ed041-105">Data is often unclean and sparse.</span></span> <span data-ttu-id="ed041-106">ML.NET algoritmos de aprendizado de máquina esperam que a entrada ou os recursos estejam em um único vetor numérico.</span><span class="sxs-lookup"><span data-stu-id="ed041-106">ML.NET machine learning algorithms expect input or features to be in a single numerical vector.</span></span> <span data-ttu-id="ed041-107">Da mesma forma, o valor para prever (rótulo), especialmente quando são dados categóricos, tem que ser codificado.</span><span class="sxs-lookup"><span data-stu-id="ed041-107">Similarly, the value to predict (label), especially when it's categorical data, has to be encoded.</span></span> <span data-ttu-id="ed041-108">Portanto, uma das metas da preparação de dados é obter os dados no formato esperado por algoritmos do ML.NET.</span><span class="sxs-lookup"><span data-stu-id="ed041-108">Therefore one of the goals of data preparation is to get the data into the format expected by ML.NET algorithms.</span></span>

## <a name="filter-data"></a><span data-ttu-id="ed041-109">Filtrar dados</span><span class="sxs-lookup"><span data-stu-id="ed041-109">Filter data</span></span>

<span data-ttu-id="ed041-110">Às vezes, nem todos os dados em um conjunto de dados são relevantes para análise.</span><span class="sxs-lookup"><span data-stu-id="ed041-110">Sometimes, not all data in a dataset is relevant for analysis.</span></span> <span data-ttu-id="ed041-111">Uma abordagem para remover dados irrelevantes é a filtragem.</span><span class="sxs-lookup"><span data-stu-id="ed041-111">An approach to remove irrelevant data is filtering.</span></span> <span data-ttu-id="ed041-112">O [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) contém um conjunto de operações de filtro que levam em um [`IDataView`](xref:Microsoft.ML.IDataView) contendo todos os dados e retornam um [IDataView](xref:Microsoft.ML.IDataView) contendo apenas os pontos de interesse dos dados.</span><span class="sxs-lookup"><span data-stu-id="ed041-112">The [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) contains a set of filter operations that take in an [`IDataView`](xref:Microsoft.ML.IDataView) containing all of the data and return an [IDataView](xref:Microsoft.ML.IDataView) containing only the data points of interest.</span></span> <span data-ttu-id="ed041-113">É importante notar que, como as [`IEstimator`](xref:Microsoft.ML.IEstimator%601) operações de filtro não são [`ITransformer`](xref:Microsoft.ML.ITransformer) ou como as do [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), elas não podem ser incluídas como parte de um [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) pipeline ou [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) de preparação de dados.</span><span class="sxs-lookup"><span data-stu-id="ed041-113">It's important to note that because filter operations are not an [`IEstimator`](xref:Microsoft.ML.IEstimator%601) or [`ITransformer`](xref:Microsoft.ML.ITransformer) like those in the [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), they cannot be included as part of an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) or [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) data preparation pipeline.</span></span>

<span data-ttu-id="ed041-114">Pegue os seguintes dados de [`IDataView`](xref:Microsoft.ML.IDataView) `data`entrada e carregue-os em um chamado:</span><span class="sxs-lookup"><span data-stu-id="ed041-114">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="ed041-115">Para filtrar dados com base no [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) valor de uma coluna, use o método.</span><span class="sxs-lookup"><span data-stu-id="ed041-115">To filter data based on the value of a column, use the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) method.</span></span>

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

<span data-ttu-id="ed041-116">O exemplo acima usa linhas no conjunto de dados com um preço entre 200.000 e 1.000.000.</span><span class="sxs-lookup"><span data-stu-id="ed041-116">The sample above takes rows in the dataset with a price between 200000 and 1000000.</span></span> <span data-ttu-id="ed041-117">O resultado da aplicação desse filtro retornaria apenas as duas últimas linhas nos dados e excluiria a primeira linha, pois seu preço é 100.000 e não está no intervalo especificado.</span><span class="sxs-lookup"><span data-stu-id="ed041-117">The result of applying this filter would return only the last two rows in the data and exclude the first row because its price is 100000 and not between the specified range.</span></span>

## <a name="replace-missing-values"></a><span data-ttu-id="ed041-118">Substituir valores ausentes</span><span class="sxs-lookup"><span data-stu-id="ed041-118">Replace missing values</span></span>

<span data-ttu-id="ed041-119">Valores ausentes são uma ocorrência comum em conjuntos de dados.</span><span class="sxs-lookup"><span data-stu-id="ed041-119">Missing values are a common occurrence in datasets.</span></span> <span data-ttu-id="ed041-120">Uma abordagem para lidar com valores ausentes é substituí-los pelo valor padrão para o tipo fornecido, se houver, ou outro valor significativo, como o valor médio dos dados.</span><span class="sxs-lookup"><span data-stu-id="ed041-120">One approach to dealing with missing values is to replace them with the default value for the given type if any or another meaningful value such as the mean value in the data.</span></span>

<span data-ttu-id="ed041-121">Pegue os seguintes dados de [`IDataView`](xref:Microsoft.ML.IDataView) `data`entrada e carregue-os em um chamado:</span><span class="sxs-lookup"><span data-stu-id="ed041-121">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="ed041-122">Observe que o último elemento em nossa lista tem um valor ausente para `Price`.</span><span class="sxs-lookup"><span data-stu-id="ed041-122">Notice that the last element in our list has a missing value for `Price`.</span></span> <span data-ttu-id="ed041-123">Para substituir os valores perdidos na `Price` coluna, use o [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) método para preencher esse valor perdido.</span><span class="sxs-lookup"><span data-stu-id="ed041-123">To replace the missing values in the `Price` column, use the [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) method to fill in that missing value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ed041-124">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A)só funciona com dados numéricos.</span><span class="sxs-lookup"><span data-stu-id="ed041-124">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) only works with numerical data.</span></span>

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

<span data-ttu-id="ed041-125">O ML.NET dá suporte a vários [modos de substituição](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span><span class="sxs-lookup"><span data-stu-id="ed041-125">ML.NET supports various [replacement modes](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span></span> <span data-ttu-id="ed041-126">A amostra acima `Mean` usa o modo de substituição, que preenche o valor faltante com o valor médio dessa coluna.</span><span class="sxs-lookup"><span data-stu-id="ed041-126">The sample above uses the `Mean` replacement mode, which fills in the missing value with that column's average value.</span></span> <span data-ttu-id="ed041-127">O resultado da substituição preenche a propriedade `Price` para o último elemento em nossos dados com 200.000, pois é a média de 300.000 e de 100.000.</span><span class="sxs-lookup"><span data-stu-id="ed041-127">The replacement 's result fills in the `Price` property for the last element in our data with 200,000 since it's the average of 100,000 and 300,000.</span></span>

## <a name="use-normalizers"></a><span data-ttu-id="ed041-128">Usar normalizadores</span><span class="sxs-lookup"><span data-stu-id="ed041-128">Use normalizers</span></span>

<span data-ttu-id="ed041-129">[A normalização](https://en.wikipedia.org/wiki/Feature_scaling) é uma técnica de pré-processamento de dados usada para dimensionar recursos para estar na mesma faixa, geralmente entre 0 e 1, para que possam ser processados com mais precisão por um algoritmo de aprendizagem de máquina.</span><span class="sxs-lookup"><span data-stu-id="ed041-129">[Normalization](https://en.wikipedia.org/wiki/Feature_scaling) is a data pre-processing technique used to scale features to be in the same range, usually between 0 and 1, so that they can be more accurately processed by a machine learning algorithm.</span></span> <span data-ttu-id="ed041-130">Por exemplo, as faixas de idade e renda variam significativamente com a idade geralmente na faixa de 0-100 e a renda geralmente estando na faixa de zero a milhares.</span><span class="sxs-lookup"><span data-stu-id="ed041-130">For example, the ranges for age and income vary significantly with age generally being in the range of 0-100 and income generally being in the range of zero to thousands.</span></span> <span data-ttu-id="ed041-131">Acesse a [página de transformações](../resources/transforms.md) para uma lista mais detalhada e uma descrição de transformações de normalização.</span><span class="sxs-lookup"><span data-stu-id="ed041-131">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of normalization transforms.</span></span>

### <a name="min-max-normalization"></a><span data-ttu-id="ed041-132">Normalização de Mín-Máx</span><span class="sxs-lookup"><span data-stu-id="ed041-132">Min-Max normalization</span></span>

<span data-ttu-id="ed041-133">Pegue os seguintes dados de [`IDataView`](xref:Microsoft.ML.IDataView) `data`entrada e carregue-os em um chamado:</span><span class="sxs-lookup"><span data-stu-id="ed041-133">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="ed041-134">A normalização pode ser aplicada a colunas com valores numéricos únicos e também vetores.</span><span class="sxs-lookup"><span data-stu-id="ed041-134">Normalization can be applied to columns with single numerical values as well as vectors.</span></span> <span data-ttu-id="ed041-135">Normalize os dados `Price` na coluna usando a normalização min-max com o [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) método.</span><span class="sxs-lookup"><span data-stu-id="ed041-135">Normalize the data in the `Price` column using min-max normalization with the [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) method.</span></span>

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

<span data-ttu-id="ed041-136">Os valores `[200000,100000]` de preço `[ 1, 0.5 ]` originais são convertidos em utilização da `MinMax` fórmula de normalização que gera valores de saída na faixa de 0-1.</span><span class="sxs-lookup"><span data-stu-id="ed041-136">The original price values `[200000,100000]` are converted to `[ 1, 0.5 ]` using the `MinMax` normalization formula that generates output values in the range of 0-1.</span></span>

### <a name="binning"></a><span data-ttu-id="ed041-137">Compartimentalização</span><span class="sxs-lookup"><span data-stu-id="ed041-137">Binning</span></span>

<span data-ttu-id="ed041-138">[Compartimentalização](https://en.wikipedia.org/wiki/Data_binning) converte valores contínuos em uma representação discreta da entrada.</span><span class="sxs-lookup"><span data-stu-id="ed041-138">[Binning](https://en.wikipedia.org/wiki/Data_binning) converts continuous values into a discrete representation of the input.</span></span> <span data-ttu-id="ed041-139">Por exemplo, suponha que um de seus recursos seja idade.</span><span class="sxs-lookup"><span data-stu-id="ed041-139">For example, suppose one of your features is age.</span></span> <span data-ttu-id="ed041-140">Em vez de usar o valor real de idade, a compartimentalização cria intervalos para esse valor.</span><span class="sxs-lookup"><span data-stu-id="ed041-140">Instead of using the actual age value,  binning creates ranges for that value.</span></span> <span data-ttu-id="ed041-141">0-18 poderia ser um compartimento, outro poderia ser 19-35 e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="ed041-141">0-18 could be one bin, another could be 19-35 and so on.</span></span>

<span data-ttu-id="ed041-142">Pegue os seguintes dados de [`IDataView`](xref:Microsoft.ML.IDataView) `data`entrada e carregue-os em um chamado:</span><span class="sxs-lookup"><span data-stu-id="ed041-142">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="ed041-143">Normalize os dados em [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A) lixeiras usando o método.</span><span class="sxs-lookup"><span data-stu-id="ed041-143">Normalize the data into bins using the [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A) method.</span></span> <span data-ttu-id="ed041-144">O parâmetro `maximumBinCount` permite que você especifique o número de compartimentos necessários para classificar seus dados.</span><span class="sxs-lookup"><span data-stu-id="ed041-144">The `maximumBinCount` parameter enables you to specify the number of bins needed to classify your data.</span></span> <span data-ttu-id="ed041-145">Neste exemplo, os dados serão colocados em dois compartimentos.</span><span class="sxs-lookup"><span data-stu-id="ed041-145">In this example, data will be put into two bins.</span></span>

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

<span data-ttu-id="ed041-146">O resultado de compartimentalização cria limites de compartimento de `[0,200000,Infinity]`.</span><span class="sxs-lookup"><span data-stu-id="ed041-146">The result of binning creates bin bounds of `[0,200000,Infinity]`.</span></span> <span data-ttu-id="ed041-147">Portanto os compartimentos resultantes são `[0,1,1]`, pois a primeira observação está entre 0 a 200.000 e os outros são maiores que 200.000, mas menores que infinito.</span><span class="sxs-lookup"><span data-stu-id="ed041-147">Therefore the resulting bins are `[0,1,1]` because the first observation is between 0-200000 and the others are greater than 200000 but less than infinity.</span></span>

## <a name="work-with-categorical-data"></a><span data-ttu-id="ed041-148">Trabalhar com os dados categóricos</span><span class="sxs-lookup"><span data-stu-id="ed041-148">Work with categorical data</span></span>

<span data-ttu-id="ed041-149">Um dos tipos de dados mais comuns são os dados categóricos.</span><span class="sxs-lookup"><span data-stu-id="ed041-149">One of the most common types of data is categorical data.</span></span> <span data-ttu-id="ed041-150">Os dados categóricos têm um número finito de categorias.</span><span class="sxs-lookup"><span data-stu-id="ed041-150">Categorical data has a finite number of categories.</span></span> <span data-ttu-id="ed041-151">Por exemplo, os estados dos EUA, ou uma lista dos tipos de animais encontrados em um conjunto de fotos.</span><span class="sxs-lookup"><span data-stu-id="ed041-151">For example, the states of the USA, or a list of the types of animals found in a set of pictures.</span></span> <span data-ttu-id="ed041-152">Se os dados categóricos são características ou rótulos, eles devem ser mapeados em um valor numérico para que possam ser usados para gerar um modelo de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="ed041-152">Whether the categorical data are features or labels, they must be mapped onto a numerical value so they can be used to generate a machine learning model.</span></span> <span data-ttu-id="ed041-153">Existem várias maneiras de trabalhar com dados categóricos em ML.NET, dependendo do problema que você está resolvendo.</span><span class="sxs-lookup"><span data-stu-id="ed041-153">There are a number of ways of working with categorical data in ML.NET, depending on the problem you are solving.</span></span>

### <a name="key-value-mapping"></a><span data-ttu-id="ed041-154">Mapeamento de valor-chave</span><span class="sxs-lookup"><span data-stu-id="ed041-154">Key value mapping</span></span>

<span data-ttu-id="ed041-155">Em ML.NET, uma chave é um valor inteiro que representa uma categoria.</span><span class="sxs-lookup"><span data-stu-id="ed041-155">In ML.NET, a key is an integer value that represents a category.</span></span> <span data-ttu-id="ed041-156">O mapeamento de valor-chave é mais frequentemente usado para mapear rótulos de strings em valores inteiros únicos para treinamento, em seguida, de volta aos seus valores de seqüência quando o modelo é usado para fazer uma previsão.</span><span class="sxs-lookup"><span data-stu-id="ed041-156">Key value mapping is most often used to map string labels into unique integer values for training, then back to their string values when the model is used to make a prediction.</span></span>

<span data-ttu-id="ed041-157">As transformações usadas para realizar mapeamento de valor-chave são [MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) e [MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A).</span><span class="sxs-lookup"><span data-stu-id="ed041-157">The transforms used to perform key value mapping are [MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) and [MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A).</span></span>

<span data-ttu-id="ed041-158">`MapValueToKey`adiciona um dicionário de mapeamentos no `MapKeyToValue` modelo, para que possa realizar a transformação inversa ao fazer uma previsão.</span><span class="sxs-lookup"><span data-stu-id="ed041-158">`MapValueToKey` adds a dictionary of mappings in the model, so that `MapKeyToValue` can perform the reverse transform when making a prediction.</span></span>

### <a name="one-hot-encoding"></a><span data-ttu-id="ed041-159">Uma codificação quente</span><span class="sxs-lookup"><span data-stu-id="ed041-159">One hot encoding</span></span>

<span data-ttu-id="ed041-160">Uma codificação quente pega um conjunto finito de valores e mapeia-os em inteiros cuja representação binária tem um único `1` valor em posições únicas na string.</span><span class="sxs-lookup"><span data-stu-id="ed041-160">One hot encoding takes a finite set of values and maps them onto integers whose binary representation has a single `1` value in unique positions in the string.</span></span> <span data-ttu-id="ed041-161">Uma codificação quente pode ser a melhor escolha se não houver uma ordem implícita dos dados categóricos.</span><span class="sxs-lookup"><span data-stu-id="ed041-161">One hot encoding can be the best choice if there is no implicit ordering of the categorical data.</span></span> <span data-ttu-id="ed041-162">A tabela a seguir mostra um exemplo com CEP como valores brutos.</span><span class="sxs-lookup"><span data-stu-id="ed041-162">The following table shows an example with zip codes as raw values.</span></span>

|<span data-ttu-id="ed041-163">Valor bruto</span><span class="sxs-lookup"><span data-stu-id="ed041-163">Raw value</span></span>|<span data-ttu-id="ed041-164">Um valor codificado quente</span><span class="sxs-lookup"><span data-stu-id="ed041-164">One hot encoded value</span></span>|
|---------|---------------------|
|<span data-ttu-id="ed041-165">98052</span><span class="sxs-lookup"><span data-stu-id="ed041-165">98052</span></span>|<span data-ttu-id="ed041-166">00...01</span><span class="sxs-lookup"><span data-stu-id="ed041-166">00...01</span></span>|
|<span data-ttu-id="ed041-167">98100</span><span class="sxs-lookup"><span data-stu-id="ed041-167">98100</span></span>|<span data-ttu-id="ed041-168">00...10</span><span class="sxs-lookup"><span data-stu-id="ed041-168">00...10</span></span>|
|<span data-ttu-id="ed041-169">...</span><span class="sxs-lookup"><span data-stu-id="ed041-169">...</span></span>|<span data-ttu-id="ed041-170">...</span><span class="sxs-lookup"><span data-stu-id="ed041-170">...</span></span>|
|<span data-ttu-id="ed041-171">98109</span><span class="sxs-lookup"><span data-stu-id="ed041-171">98109</span></span>|<span data-ttu-id="ed041-172">10...00</span><span class="sxs-lookup"><span data-stu-id="ed041-172">10...00</span></span>|

<span data-ttu-id="ed041-173">A transformação para converter dados categóricos [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A)em números codificados de um único hot é .</span><span class="sxs-lookup"><span data-stu-id="ed041-173">The transform to convert categorical data to one-hot encoded numbers is [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A).</span></span>

### <a name="hashing"></a><span data-ttu-id="ed041-174">Hash</span><span class="sxs-lookup"><span data-stu-id="ed041-174">Hashing</span></span>

<span data-ttu-id="ed041-175">Hashing é outra maneira de converter dados categóricos em números.</span><span class="sxs-lookup"><span data-stu-id="ed041-175">Hashing is another way to convert categorical data to numbers.</span></span> <span data-ttu-id="ed041-176">Uma função hash mapeia dados de um tamanho arbitrário (uma seqüência de texto, por exemplo) em um número com um intervalo fixo.</span><span class="sxs-lookup"><span data-stu-id="ed041-176">A hash function maps data of an arbitrary size (a string of text for example) onto a number with a fixed range.</span></span> <span data-ttu-id="ed041-177">O hashing pode ser uma maneira rápida e eficiente de espaço de vetorização de recursos.</span><span class="sxs-lookup"><span data-stu-id="ed041-177">Hashing can be a fast and space-efficient way of vectorizing features.</span></span> <span data-ttu-id="ed041-178">Um exemplo notável de hashing no aprendizado de máquina é a filtragem de spam de e-mail onde, em vez de manter um dicionário de palavras conhecidas, cada palavra no e-mail é hashed e adicionada a um grande vetor de recursos.</span><span class="sxs-lookup"><span data-stu-id="ed041-178">One notable example of hashing in machine learning is email spam filtering where, instead of maintaining a dictionary of known words, every word in the email is hashed and added to a large feature vector.</span></span> <span data-ttu-id="ed041-179">O uso de hashs dessa forma evita o problema da filtragem de spam maliciosa pelo uso de palavras que não estão no dicionário.</span><span class="sxs-lookup"><span data-stu-id="ed041-179">Using hashing in this way avoids the problem of malicious spam filtering circumvention by the use of words that are not in the dictionary.</span></span>

<span data-ttu-id="ed041-180">ML.NET fornece a transformação [hash](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A) para executar hashing em texto, datas e dados numéricos.</span><span class="sxs-lookup"><span data-stu-id="ed041-180">ML.NET provides [Hash](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A) transform to perform hashing on text, dates, and numerical data.</span></span> <span data-ttu-id="ed041-181">Como mapeamento de tecla de valor, as saídas da transformação de hash são tipos-chave.</span><span class="sxs-lookup"><span data-stu-id="ed041-181">Like value key mapping, the outputs of the hash transform are key types.</span></span>

## <a name="work-with-text-data"></a><span data-ttu-id="ed041-182">Trabalhar com os dados de texto</span><span class="sxs-lookup"><span data-stu-id="ed041-182">Work with text data</span></span>

<span data-ttu-id="ed041-183">Como dados categóricos, os dados de texto precisam ser transformados em recursos numéricos antes de usá-los para construir um modelo de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="ed041-183">Like categorical data, text data needs to be transformed into numerical features before using it to build a machine learning model.</span></span> <span data-ttu-id="ed041-184">Acesse a [página de transformações](../resources/transforms.md) para uma lista mais detalhada e uma descrição de transformações de texto.</span><span class="sxs-lookup"><span data-stu-id="ed041-184">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of text transforms.</span></span>

<span data-ttu-id="ed041-185">Usando dados como os dados abaixo que [`IDataView`](xref:Microsoft.ML.IDataView)foram carregados em um:</span><span class="sxs-lookup"><span data-stu-id="ed041-185">Using data like the data below that has been loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="ed041-186">ML.NET fornece [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) a transformação que leva o valor da seqüência de texto e cria um conjunto de recursos a partir do texto, aplicando uma série de transformações individuais.</span><span class="sxs-lookup"><span data-stu-id="ed041-186">ML.NET provides the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) transform that takes a text's string value and creates a set of features from the text, by applying a series of individual transforms.</span></span>

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

<span data-ttu-id="ed041-187">A transformação resultante converte os `Description` valores de texto na coluna para um vetor numérico que se parece com a saída abaixo:</span><span class="sxs-lookup"><span data-stu-id="ed041-187">The resulting transform converts the text values in the `Description` column to a numerical vector that looks similar to the output below:</span></span>

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

<span data-ttu-id="ed041-188">As transformações que `FeaturizeText` compõem também podem ser aplicadas individualmente para um controle mais fino de grãos sobre a geração de recursos.</span><span class="sxs-lookup"><span data-stu-id="ed041-188">The transforms that make up `FeaturizeText` can also be applied individually for finer grain control over feature generation.</span></span>

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

<span data-ttu-id="ed041-189">`textEstimator`contém um subconjunto de [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) operações realizadas pelo método.</span><span class="sxs-lookup"><span data-stu-id="ed041-189">`textEstimator` contains a subset of operations performed by the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) method.</span></span> <span data-ttu-id="ed041-190">O benefício de um pipeline mais complexo é a visibilidade e o controle sobre as transformações aplicadas aos dados.</span><span class="sxs-lookup"><span data-stu-id="ed041-190">The benefit of a more complex pipeline is control and visibility over the transformations applied to the data.</span></span>

<span data-ttu-id="ed041-191">Usando a primeira entrada como um exemplo, a seguir está uma descrição detalhada dos resultados produzidos pelas etapas de transformação definidas pelo `textEstimator`:</span><span class="sxs-lookup"><span data-stu-id="ed041-191">Using the first entry as an example, the following is a detailed description of the results produced by the transformation steps defined by `textEstimator`:</span></span>

<span data-ttu-id="ed041-192">**Texto Original: Este é um bom produto**</span><span class="sxs-lookup"><span data-stu-id="ed041-192">**Original Text: This is a good product**</span></span>

|<span data-ttu-id="ed041-193">Transformar</span><span class="sxs-lookup"><span data-stu-id="ed041-193">Transform</span></span> | <span data-ttu-id="ed041-194">Descrição</span><span class="sxs-lookup"><span data-stu-id="ed041-194">Description</span></span> | <span data-ttu-id="ed041-195">Result</span><span class="sxs-lookup"><span data-stu-id="ed041-195">Result</span></span>
|--|--|--|
|<span data-ttu-id="ed041-196">1. NormalizeText</span><span class="sxs-lookup"><span data-stu-id="ed041-196">1. NormalizeText</span></span> | <span data-ttu-id="ed041-197">Converte todas as letras em minúsculas por padrão</span><span class="sxs-lookup"><span data-stu-id="ed041-197">Converts all letters to lowercase by default</span></span> | <span data-ttu-id="ed041-198">este é um bom produto</span><span class="sxs-lookup"><span data-stu-id="ed041-198">this is a good product</span></span>
|<span data-ttu-id="ed041-199">2. TokenizeWords</span><span class="sxs-lookup"><span data-stu-id="ed041-199">2. TokenizeWords</span></span> | <span data-ttu-id="ed041-200">Divide a cadeia de caracteres em palavras individuais</span><span class="sxs-lookup"><span data-stu-id="ed041-200">Splits string into individual words</span></span> | <span data-ttu-id="ed041-201">["este", "é", "um","bom","produto"]</span><span class="sxs-lookup"><span data-stu-id="ed041-201">["this","is","a","good","product"]</span></span>
|<span data-ttu-id="ed041-202">3. RemoverDefaultStopWords</span><span class="sxs-lookup"><span data-stu-id="ed041-202">3. RemoveDefaultStopWords</span></span> | <span data-ttu-id="ed041-203">Remove palavras irrelevantes, como *está* e *um*.</span><span class="sxs-lookup"><span data-stu-id="ed041-203">Removes stopwords like *is* and *a*.</span></span> | <span data-ttu-id="ed041-204">["bom","produto"]</span><span class="sxs-lookup"><span data-stu-id="ed041-204">["good","product"]</span></span>
|<span data-ttu-id="ed041-205">4. MapValueToKey</span><span class="sxs-lookup"><span data-stu-id="ed041-205">4. MapValueToKey</span></span> | <span data-ttu-id="ed041-206">Mapeia os valores para chaves (categorias) com base nos dados de entrada</span><span class="sxs-lookup"><span data-stu-id="ed041-206">Maps the values to keys (categories) based on the input data</span></span> |  <span data-ttu-id="ed041-207">[1,2]</span><span class="sxs-lookup"><span data-stu-id="ed041-207">[1,2]</span></span>
|<span data-ttu-id="ed041-208">5. ProduzirNGramas</span><span class="sxs-lookup"><span data-stu-id="ed041-208">5. ProduceNGrams</span></span> | <span data-ttu-id="ed041-209">Transforma o texto em sequência de palavras consecutivas</span><span class="sxs-lookup"><span data-stu-id="ed041-209">Transforms text into sequence of consecutive words</span></span> | <span data-ttu-id="ed041-210">[1,1,1,0,0]</span><span class="sxs-lookup"><span data-stu-id="ed041-210">[1,1,1,0,0]</span></span>
|<span data-ttu-id="ed041-211">6. NormalizeLpNorm</span><span class="sxs-lookup"><span data-stu-id="ed041-211">6. NormalizeLpNorm</span></span> | <span data-ttu-id="ed041-212">Escala as entradas por sua lp-norm</span><span class="sxs-lookup"><span data-stu-id="ed041-212">Scale inputs by their lp-norm</span></span> | <span data-ttu-id="ed041-213">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span><span class="sxs-lookup"><span data-stu-id="ed041-213">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span></span>
