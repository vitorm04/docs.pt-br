---
title: Interpretar modelos de ML.NET com importância de recurso de permuta
description: Entender a importância de recursos de modelos com a Importância de recursos de permutação no ML.NET
ms.date: 01/30/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: ed0d6736f1f2e988d96a397cad77a7fc743489da
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174225"
---
# <a name="interpret-model-predictions-using-permutation-feature-importance"></a><span data-ttu-id="1b8dc-103">Interpretar previsões de modelo usando a importância do recurso de permuta</span><span class="sxs-lookup"><span data-stu-id="1b8dc-103">Interpret model predictions using Permutation Feature Importance</span></span>

<span data-ttu-id="1b8dc-104">Usando a importância do recurso de permutação (PFI), saiba como interpretar previsões de modelo de aprendizado de máquina ML.NET.</span><span class="sxs-lookup"><span data-stu-id="1b8dc-104">Using Permutation Feature Importance (PFI), learn how to interpret ML.NET machine learning model predictions.</span></span> <span data-ttu-id="1b8dc-105">PFI fornece a contribuição relativa que cada recurso faz a uma previsão.</span><span class="sxs-lookup"><span data-stu-id="1b8dc-105">PFI gives the relative contribution each feature makes to a prediction.</span></span>

<span data-ttu-id="1b8dc-106">Os modelos de aprendizado de máquina costumam ser considerados como caixas opacas que recebem entradas e geram uma saída.</span><span class="sxs-lookup"><span data-stu-id="1b8dc-106">Machine learning models are often thought of as opaque boxes that take inputs and generate an output.</span></span> <span data-ttu-id="1b8dc-107">As etapas intermediárias ou as interações entre os recursos que influenciam a saída raramente são compreendidas.</span><span class="sxs-lookup"><span data-stu-id="1b8dc-107">The intermediate steps or interactions among the features that influence the output are rarely understood.</span></span> <span data-ttu-id="1b8dc-108">Conforme o aprendizado de máquina é introduzido em mais aspectos da vida diária, como serviços de saúde, é de extrema importância entender por que um modelo de machine learning toma as decisões que ele toma.</span><span class="sxs-lookup"><span data-stu-id="1b8dc-108">As machine learning is introduced into more aspects of everyday life such as healthcare, it's of utmost importance to understand why a machine learning model makes the decisions it does.</span></span> <span data-ttu-id="1b8dc-109">Por exemplo, se os diagnósticos forem feitos por um modelo de machine learning, os profissionais de saúde precisarão de uma maneira de examinar os fatores que contribuíram para esse diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="1b8dc-109">For example, if diagnoses are made by a machine learning model, healthcare professionals need a way to look into the factors that went into making that diagnoses.</span></span> <span data-ttu-id="1b8dc-110">Fornecer o diagnóstico certo pode fazer uma grande diferença em se um paciente tem uma recuperação rápida ou não.</span><span class="sxs-lookup"><span data-stu-id="1b8dc-110">Providing the right diagnosis could make a great difference on whether a patient has a speedy recovery or not.</span></span> <span data-ttu-id="1b8dc-111">Portanto, quanto maior o nível de capacidade de explicação de um modelo, mais confiança os profissionais de saúde terão em aceitar ou rejeitar as decisões tomadas pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="1b8dc-111">Therefore the higher the level of explainability in a model, the greater confidence healthcare professionals have to accept or reject the decisions made by the model.</span></span>

<span data-ttu-id="1b8dc-112">Várias técnicas são usadas para explicar os modelos, uma delas é a PFI.</span><span class="sxs-lookup"><span data-stu-id="1b8dc-112">Various techniques are used to explain models, one of which is PFI.</span></span> <span data-ttu-id="1b8dc-113">PFI é uma técnica usada para explicar os modelos de classificação e regressão que são inspirados pelo [documento de *florestas aleatórias* do Breiman](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) (consulte a seção 10).</span><span class="sxs-lookup"><span data-stu-id="1b8dc-113">PFI is a technique used to explain classification and regression models that is inspired by [Breiman's *Random Forests* paper](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) (see section 10).</span></span> <span data-ttu-id="1b8dc-114">Em um alto nível, a maneira como eles funcionam é embaralhando aleatoriamente um recurso de dados por vez para todo o conjunto de dados e calculando o quanto a métrica de desempenho de interesse diminui.</span><span class="sxs-lookup"><span data-stu-id="1b8dc-114">At a high level, the way it works is by randomly shuffling data one feature at a time for the entire dataset and calculating how much the performance metric of interest decreases.</span></span> <span data-ttu-id="1b8dc-115">Quanto maior a alteração, mais importante é esse recurso.</span><span class="sxs-lookup"><span data-stu-id="1b8dc-115">The larger the change, the more important that feature is.</span></span>

<span data-ttu-id="1b8dc-116">Além disso, ao realçar os recursos mais importantes, construtores de modelo podem se concentrar no uso de um subconjunto de recursos mais significativos que pode reduzir o ruído e tempo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="1b8dc-116">Additionally, by highlighting the most important features, model builders can focus on using a subset of more meaningful features which can potentially reduce noise and training time.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="1b8dc-117">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="1b8dc-117">Load the data</span></span>

<span data-ttu-id="1b8dc-118">Os recursos no conjunto de dados que está sendo usado para este exemplo estão nas colunas 1 a 12.</span><span class="sxs-lookup"><span data-stu-id="1b8dc-118">The features in the dataset being used for this sample are in columns 1-12.</span></span> <span data-ttu-id="1b8dc-119">A meta é prever `Price`.</span><span class="sxs-lookup"><span data-stu-id="1b8dc-119">The goal is to predict `Price`.</span></span>

| <span data-ttu-id="1b8dc-120">Coluna</span><span class="sxs-lookup"><span data-stu-id="1b8dc-120">Column</span></span> | <span data-ttu-id="1b8dc-121">Recurso</span><span class="sxs-lookup"><span data-stu-id="1b8dc-121">Feature</span></span> | <span data-ttu-id="1b8dc-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="1b8dc-122">Description</span></span>
| --- | --- | --- |
| <span data-ttu-id="1b8dc-123">1</span><span class="sxs-lookup"><span data-stu-id="1b8dc-123">1</span></span> | <span data-ttu-id="1b8dc-124">CrimeRate</span><span class="sxs-lookup"><span data-stu-id="1b8dc-124">CrimeRate</span></span> | <span data-ttu-id="1b8dc-125">Taxa de criminalidade per capita</span><span class="sxs-lookup"><span data-stu-id="1b8dc-125">Per capita crime rate</span></span>
| <span data-ttu-id="1b8dc-126">2</span><span class="sxs-lookup"><span data-stu-id="1b8dc-126">2</span></span> | <span data-ttu-id="1b8dc-127">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="1b8dc-127">ResidentialZones</span></span> | <span data-ttu-id="1b8dc-128">Zonas residenciais da cidade</span><span class="sxs-lookup"><span data-stu-id="1b8dc-128">Residential zones in town</span></span>
| <span data-ttu-id="1b8dc-129">3</span><span class="sxs-lookup"><span data-stu-id="1b8dc-129">3</span></span> | <span data-ttu-id="1b8dc-130">CommercialZones</span><span class="sxs-lookup"><span data-stu-id="1b8dc-130">CommercialZones</span></span> | <span data-ttu-id="1b8dc-131">Zonas não residenciais da cidade</span><span class="sxs-lookup"><span data-stu-id="1b8dc-131">Non-residential zones in town</span></span>
| <span data-ttu-id="1b8dc-132">4</span><span class="sxs-lookup"><span data-stu-id="1b8dc-132">4</span></span> | <span data-ttu-id="1b8dc-133">NearWater</span><span class="sxs-lookup"><span data-stu-id="1b8dc-133">NearWater</span></span> | <span data-ttu-id="1b8dc-134">Proximidade a recursos hídricos</span><span class="sxs-lookup"><span data-stu-id="1b8dc-134">Proximity to body of water</span></span>
| <span data-ttu-id="1b8dc-135">5</span><span class="sxs-lookup"><span data-stu-id="1b8dc-135">5</span></span> | <span data-ttu-id="1b8dc-136">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="1b8dc-136">ToxicWasteLevels</span></span> | <span data-ttu-id="1b8dc-137">Níveis de toxicidade (PPM)</span><span class="sxs-lookup"><span data-stu-id="1b8dc-137">Toxicity levels (PPM)</span></span>
| <span data-ttu-id="1b8dc-138">6</span><span class="sxs-lookup"><span data-stu-id="1b8dc-138">6</span></span> | <span data-ttu-id="1b8dc-139">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="1b8dc-139">AverageRoomNumber</span></span> | <span data-ttu-id="1b8dc-140">Número médio de ambientes na casa</span><span class="sxs-lookup"><span data-stu-id="1b8dc-140">Average number of rooms in house</span></span>
| <span data-ttu-id="1b8dc-141">7</span><span class="sxs-lookup"><span data-stu-id="1b8dc-141">7</span></span> | <span data-ttu-id="1b8dc-142">HomeAge</span><span class="sxs-lookup"><span data-stu-id="1b8dc-142">HomeAge</span></span> | <span data-ttu-id="1b8dc-143">Idade da casa</span><span class="sxs-lookup"><span data-stu-id="1b8dc-143">Age of home</span></span>
| <span data-ttu-id="1b8dc-144">8</span><span class="sxs-lookup"><span data-stu-id="1b8dc-144">8</span></span> | <span data-ttu-id="1b8dc-145">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="1b8dc-145">BusinessCenterDistance</span></span> | <span data-ttu-id="1b8dc-146">Distância até o bairro comercial mais próximo</span><span class="sxs-lookup"><span data-stu-id="1b8dc-146">Distance to nearest business district</span></span>
| <span data-ttu-id="1b8dc-147">9</span><span class="sxs-lookup"><span data-stu-id="1b8dc-147">9</span></span> | <span data-ttu-id="1b8dc-148">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="1b8dc-148">HighwayAccess</span></span> | <span data-ttu-id="1b8dc-149">Proximidade de rodovias</span><span class="sxs-lookup"><span data-stu-id="1b8dc-149">Proximity to highways</span></span>
| <span data-ttu-id="1b8dc-150">10</span><span class="sxs-lookup"><span data-stu-id="1b8dc-150">10</span></span> | <span data-ttu-id="1b8dc-151">TaxRate</span><span class="sxs-lookup"><span data-stu-id="1b8dc-151">TaxRate</span></span> | <span data-ttu-id="1b8dc-152">Taxa de imposto sobre propriedade</span><span class="sxs-lookup"><span data-stu-id="1b8dc-152">Property tax rate</span></span>
| <span data-ttu-id="1b8dc-153">11</span><span class="sxs-lookup"><span data-stu-id="1b8dc-153">11</span></span> | <span data-ttu-id="1b8dc-154">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="1b8dc-154">StudentTeacherRatio</span></span> | <span data-ttu-id="1b8dc-155">Taxa de alunos para professores</span><span class="sxs-lookup"><span data-stu-id="1b8dc-155">Ratio of students to teachers</span></span>
| <span data-ttu-id="1b8dc-156">12</span><span class="sxs-lookup"><span data-stu-id="1b8dc-156">12</span></span> | <span data-ttu-id="1b8dc-157">PercentPopulationBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="1b8dc-157">PercentPopulationBelowPoverty</span></span> | <span data-ttu-id="1b8dc-158">Percentual da população vivendo abaixo da linha de pobreza</span><span class="sxs-lookup"><span data-stu-id="1b8dc-158">Percent of population living below poverty</span></span>
| <span data-ttu-id="1b8dc-159">13</span><span class="sxs-lookup"><span data-stu-id="1b8dc-159">13</span></span> | <span data-ttu-id="1b8dc-160">Preço</span><span class="sxs-lookup"><span data-stu-id="1b8dc-160">Price</span></span> | <span data-ttu-id="1b8dc-161">Preço da casa</span><span class="sxs-lookup"><span data-stu-id="1b8dc-161">Price of the home</span></span>

<span data-ttu-id="1b8dc-162">Um exemplo do conjunto de dados é mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="1b8dc-162">A sample of the dataset is shown below:</span></span>

```text
1,24,13,1,0.59,3,96,11,23,608,14,13,32
4,80,18,1,0.37,5,14,7,4,346,19,13,41
2,98,16,1,0.25,10,5,1,8,689,13,36,12
```

<span data-ttu-id="1b8dc-163">Os dados neste exemplo podem ser modelados por uma classe como `HousingPriceData` e carregados em um [`IDataView`](xref:Microsoft.ML.IDataView) .</span><span class="sxs-lookup"><span data-stu-id="1b8dc-163">The data in this sample can be modeled by a class like `HousingPriceData` and loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

```csharp
class HousingPriceData
{
    [LoadColumn(0)]
    public float CrimeRate { get; set; }

    [LoadColumn(1)]
    public float ResidentialZones { get; set; }

    [LoadColumn(2)]
    public float CommercialZones { get; set; }

    [LoadColumn(3)]
    public float NearWater { get; set; }

    [LoadColumn(4)]
    public float ToxicWasteLevels { get; set; }

    [LoadColumn(5)]
    public float AverageRoomNumber { get; set; }

    [LoadColumn(6)]
    public float HomeAge { get; set; }

    [LoadColumn(7)]
    public float BusinessCenterDistance { get; set; }

    [LoadColumn(8)]
    public float HighwayAccess { get; set; }

    [LoadColumn(9)]
    public float TaxRate { get; set; }

    [LoadColumn(10)]
    public float StudentTeacherRatio { get; set; }

    [LoadColumn(11)]
    public float PercentPopulationBelowPoverty { get; set; }

    [LoadColumn(12)]
    [ColumnName("Label")]
    public float Price { get; set; }
}
```

## <a name="train-the-model"></a><span data-ttu-id="1b8dc-164">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="1b8dc-164">Train the model</span></span>

<span data-ttu-id="1b8dc-165">O exemplo de código a seguir ilustra o processo de treinamento de um modelo de regressão linear para prever preços de casa.</span><span class="sxs-lookup"><span data-stu-id="1b8dc-165">The code sample below illustrates the process of training a linear regression model to predict house prices.</span></span>

```csharp
// 1. Get the column name of input features.
string[] featureColumnNames =
    data.Schema
        .Select(column => column.Name)
        .Where(columnName => columnName != "Label").ToArray();

// 2. Define estimator with data pre-processing steps
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", featureColumnNames)
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// 3. Create transformer using the data pre-processing estimator
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(data);

// 4. Pre-process the training data
IDataView preprocessedTrainData = dataPrepTransformer.Transform(data);

// 5. Define Stochastic Dual Coordinate Ascent machine learning estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// 6. Train machine learning model
var sdcaModel = sdcaEstimator.Fit(preprocessedTrainData);
```

## <a name="explain-the-model-with-permutation-feature-importance-pfi"></a><span data-ttu-id="1b8dc-166">Explicar o modelo com PFI (Importância de Recurso de Permutação)</span><span class="sxs-lookup"><span data-stu-id="1b8dc-166">Explain the model with Permutation Feature Importance (PFI)</span></span>

<span data-ttu-id="1b8dc-167">No ML.NET, use o [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) método para sua respectiva tarefa.</span><span class="sxs-lookup"><span data-stu-id="1b8dc-167">In ML.NET use the [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) method for your respective task.</span></span>

```csharp
ImmutableArray<RegressionMetricsStatistics> permutationFeatureImportance =
    mlContext
        .Regression
        .PermutationFeatureImportance(sdcaModel, preprocessedTrainData, permutationCount:3);
```

<span data-ttu-id="1b8dc-168">O resultado do uso do no conjunto de resultados de [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) treinamento é um [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) dos [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) objetos.</span><span class="sxs-lookup"><span data-stu-id="1b8dc-168">The result of using [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) on the training dataset is an [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) of [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) objects.</span></span> <span data-ttu-id="1b8dc-169">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics)fornece estatísticas de resumo como média e desvio padrão para várias observações de [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) igual ao número de permutações especificadas pelo `permutationCount` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1b8dc-169">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) provides summary statistics like mean and standard deviation for multiple observations of [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) equal to the number of permutations specified by the `permutationCount` parameter.</span></span>

<span data-ttu-id="1b8dc-170">A importância, ou nesse caso, a redução média absoluta na métrica R-quadrado calculada por [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) pode ser ordenada da mais importante para a menos importante.</span><span class="sxs-lookup"><span data-stu-id="1b8dc-170">The importance, or in this case, the absolute average decrease in R-squared metric calculated by [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) can then be ordered from most important to least important.</span></span>

```csharp
// Order features by importance
var featureImportanceMetrics =
    permutationFeatureImportance
        .Select((metric, index) => new { index, metric.RSquared })
        .OrderByDescending(myFeatures => Math.Abs(myFeatures.RSquared.Mean));

Console.WriteLine("Feature\tPFI");

foreach (var feature in featureImportanceMetrics)
{
    Console.WriteLine($"{featureColumnNames[feature.index],-20}|\t{feature.RSquared.Mean:F6}");
}
```

<span data-ttu-id="1b8dc-171">Imprimir os valores para cada um dos recursos em `featureImportanceMetrics` geraria saída semelhante à abaixo.</span><span class="sxs-lookup"><span data-stu-id="1b8dc-171">Printing the values for each of the features in `featureImportanceMetrics` would generate output similar to that below.</span></span> <span data-ttu-id="1b8dc-172">Lembre-se de que você deve esperar ver resultados diferentes, pois esses valores variam conforme os dados apresentados.</span><span class="sxs-lookup"><span data-stu-id="1b8dc-172">Keep in mind that you should expect to see different results because these values vary based on the data that they are given.</span></span>

| <span data-ttu-id="1b8dc-173">Recurso</span><span class="sxs-lookup"><span data-stu-id="1b8dc-173">Feature</span></span> | <span data-ttu-id="1b8dc-174">Alterar para R ao quadrado</span><span class="sxs-lookup"><span data-stu-id="1b8dc-174">Change to R-Squared</span></span> |
|:--|:--:|
<span data-ttu-id="1b8dc-175">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="1b8dc-175">HighwayAccess</span></span>       |   <span data-ttu-id="1b8dc-176">-0,042731</span><span class="sxs-lookup"><span data-stu-id="1b8dc-176">-0.042731</span></span>
<span data-ttu-id="1b8dc-177">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="1b8dc-177">StudentTeacherRatio</span></span> |   <span data-ttu-id="1b8dc-178">-0,012730</span><span class="sxs-lookup"><span data-stu-id="1b8dc-178">-0.012730</span></span>
<span data-ttu-id="1b8dc-179">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="1b8dc-179">BusinessCenterDistance</span></span>| <span data-ttu-id="1b8dc-180">-0,010491</span><span class="sxs-lookup"><span data-stu-id="1b8dc-180">-0.010491</span></span>
<span data-ttu-id="1b8dc-181">TaxRate</span><span class="sxs-lookup"><span data-stu-id="1b8dc-181">TaxRate</span></span>             |   <span data-ttu-id="1b8dc-182">-0,008545</span><span class="sxs-lookup"><span data-stu-id="1b8dc-182">-0.008545</span></span>
<span data-ttu-id="1b8dc-183">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="1b8dc-183">AverageRoomNumber</span></span>   |   <span data-ttu-id="1b8dc-184">-0,003949</span><span class="sxs-lookup"><span data-stu-id="1b8dc-184">-0.003949</span></span>
<span data-ttu-id="1b8dc-185">CrimeRate</span><span class="sxs-lookup"><span data-stu-id="1b8dc-185">CrimeRate</span></span>           |   <span data-ttu-id="1b8dc-186">-0,003665</span><span class="sxs-lookup"><span data-stu-id="1b8dc-186">-0.003665</span></span>
<span data-ttu-id="1b8dc-187">CommercialZones</span><span class="sxs-lookup"><span data-stu-id="1b8dc-187">CommercialZones</span></span>     |   <span data-ttu-id="1b8dc-188">0,002749</span><span class="sxs-lookup"><span data-stu-id="1b8dc-188">0.002749</span></span>
<span data-ttu-id="1b8dc-189">HomeAge</span><span class="sxs-lookup"><span data-stu-id="1b8dc-189">HomeAge</span></span>             |   <span data-ttu-id="1b8dc-190">-0,002426</span><span class="sxs-lookup"><span data-stu-id="1b8dc-190">-0.002426</span></span>
<span data-ttu-id="1b8dc-191">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="1b8dc-191">ResidentialZones</span></span>    |   <span data-ttu-id="1b8dc-192">-0,002319</span><span class="sxs-lookup"><span data-stu-id="1b8dc-192">-0.002319</span></span>
<span data-ttu-id="1b8dc-193">NearWater</span><span class="sxs-lookup"><span data-stu-id="1b8dc-193">NearWater</span></span>           |   <span data-ttu-id="1b8dc-194">0,000203</span><span class="sxs-lookup"><span data-stu-id="1b8dc-194">0.000203</span></span>
<span data-ttu-id="1b8dc-195">PercentPopulationLivingBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="1b8dc-195">PercentPopulationLivingBelowPoverty</span></span>|    <span data-ttu-id="1b8dc-196">0,000031</span><span class="sxs-lookup"><span data-stu-id="1b8dc-196">0.000031</span></span>
<span data-ttu-id="1b8dc-197">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="1b8dc-197">ToxicWasteLevels</span></span>    |   <span data-ttu-id="1b8dc-198">-0,000019</span><span class="sxs-lookup"><span data-stu-id="1b8dc-198">-0.000019</span></span>

<span data-ttu-id="1b8dc-199">Vamos analisar os cinco recursos mais importantes para este conjunto de dados, o preço de uma casa previsto por esse modelo é influenciado pela sua proximidade a rodovias, pela proporção de alunos para professor das escolas na área, pela proximidade com centros de emprego importantes, pela taxa de impostos sobre propriedade e pelo número médio de ambientes na casa.</span><span class="sxs-lookup"><span data-stu-id="1b8dc-199">Taking a look at the five most important features for this dataset, the price of a house predicted by this model is influenced by its proximity to highways, student teacher ratio of schools in the area, proximity to major employment centers, property tax rate and average number of rooms in the home.</span></span>
