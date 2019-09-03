---
title: Explicar previsões do modelo usando Importância do Recurso de Permutação
description: Entender a importância de recursos de modelos com a Importância de recursos de permutação no ML.NET
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: 9617582c79b2278e3a68e7acf84568247b81eca1
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70167651"
---
# <a name="explain-model-predictions-using-permutation-feature-importance"></a><span data-ttu-id="24dfd-103">Explicar previsões do modelo usando Importância do Recurso de Permutação</span><span class="sxs-lookup"><span data-stu-id="24dfd-103">Explain model predictions using Permutation Feature Importance</span></span>

<span data-ttu-id="24dfd-104">Aprenda a explicar as previsões de modelo de machine learning do ML.NET compreendendo a contribuição que os recursos dão para previsões usando PFI (Importância de Recurso de Permutação).</span><span class="sxs-lookup"><span data-stu-id="24dfd-104">Learn how to explain ML.NET machine learning model predictions by understanding the contribution features have to predictions using Permutation Feature Importance (PFI).</span></span>

<span data-ttu-id="24dfd-105">Modelos de machine learning geralmente são considerados caixas pretas que pegam entradas e geram uma saída.</span><span class="sxs-lookup"><span data-stu-id="24dfd-105">Machine learning models are often thought of as black boxes that take inputs and generate an output.</span></span> <span data-ttu-id="24dfd-106">As etapas intermediárias ou as interações entre os recursos que influenciam a saída raramente são compreendidas.</span><span class="sxs-lookup"><span data-stu-id="24dfd-106">The intermediate steps or interactions among the features that influence the output are rarely understood.</span></span> <span data-ttu-id="24dfd-107">Conforme o aprendizado de máquina é introduzido em mais aspectos da vida diária, como serviços de saúde, é de extrema importância entender por que um modelo de machine learning toma as decisões que ele toma.</span><span class="sxs-lookup"><span data-stu-id="24dfd-107">As machine learning is introduced into more aspects of everyday life such as healthcare, it's of utmost importance to understand why a machine learning model makes the decisions it does.</span></span> <span data-ttu-id="24dfd-108">Por exemplo, se os diagnósticos forem feitos por um modelo de machine learning, os profissionais de saúde precisarão de uma maneira de examinar os fatores que contribuíram para esse diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="24dfd-108">For example, if diagnoses are made by a machine learning model, healthcare professionals need a way to look into the factors that went into making that diagnoses.</span></span> <span data-ttu-id="24dfd-109">Fornecer o diagnóstico certo pode fazer uma grande diferença em se um paciente tem uma recuperação rápida ou não.</span><span class="sxs-lookup"><span data-stu-id="24dfd-109">Providing the right diagnosis could make a great difference on whether a patient has a speedy recovery or not.</span></span> <span data-ttu-id="24dfd-110">Portanto, quanto maior o nível de capacidade de explicação de um modelo, mais confiança os profissionais de saúde terão em aceitar ou rejeitar as decisões tomadas pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="24dfd-110">Therefore the higher the level of explainability in a model, the greater confidence healthcare professionals have to accept or reject the decisions made by the model.</span></span>

<span data-ttu-id="24dfd-111">Várias técnicas são usadas para explicar os modelos, uma delas é a PFI.</span><span class="sxs-lookup"><span data-stu-id="24dfd-111">Various techniques are used to explain models, one of which is PFI.</span></span> <span data-ttu-id="24dfd-112">PFI é uma técnica usada para explicar os modelos de classificação e regressão inspirados pelo artigo de [Breiman chamado *Random Forests* (Florestas aleatórias) ](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf)(veja a seção 10).</span><span class="sxs-lookup"><span data-stu-id="24dfd-112">PFI is a technique used to explain classification and regression models that is inspired by [Breiman's *Random Forests* paper](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf)(see section 10).</span></span> <span data-ttu-id="24dfd-113">Em um alto nível, a maneira como eles funcionam é embaralhando aleatoriamente um recurso de dados por vez para todo o conjunto de dados e calculando o quanto a métrica de desempenho de interesse diminui.</span><span class="sxs-lookup"><span data-stu-id="24dfd-113">At a high level, the way it works is by randomly shuffling data one feature at a time for the entire dataset and calculating how much the performance metric of interest decreases.</span></span> <span data-ttu-id="24dfd-114">Quanto maior a alteração, mais importante é esse recurso.</span><span class="sxs-lookup"><span data-stu-id="24dfd-114">The larger the change, the more important that feature is.</span></span> 

<span data-ttu-id="24dfd-115">Além disso, ao realçar os recursos mais importantes, construtores de modelo podem se concentrar no uso de um subconjunto de recursos mais significativos que pode reduzir o ruído e tempo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="24dfd-115">Additionally, by highlighting the most important features, model builders can focus on using a subset of more meaningful features which can potentially reduce noise and training time.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="24dfd-116">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="24dfd-116">Load the data</span></span>

<span data-ttu-id="24dfd-117">Os recursos no conjunto de dados que está sendo usado para este exemplo estão nas colunas 1 a 12.</span><span class="sxs-lookup"><span data-stu-id="24dfd-117">The features in the dataset being used for this sample are in columns 1-12.</span></span> <span data-ttu-id="24dfd-118">A meta é prever `Price`.</span><span class="sxs-lookup"><span data-stu-id="24dfd-118">The goal is to predict `Price`.</span></span> 

| <span data-ttu-id="24dfd-119">Column</span><span class="sxs-lookup"><span data-stu-id="24dfd-119">Column</span></span> | <span data-ttu-id="24dfd-120">Recurso</span><span class="sxs-lookup"><span data-stu-id="24dfd-120">Feature</span></span> | <span data-ttu-id="24dfd-121">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="24dfd-121">Description</span></span> 
| --- | --- | --- |
| <span data-ttu-id="24dfd-122">1</span><span class="sxs-lookup"><span data-stu-id="24dfd-122">1</span></span> | <span data-ttu-id="24dfd-123">CrimeRate</span><span class="sxs-lookup"><span data-stu-id="24dfd-123">CrimeRate</span></span> | <span data-ttu-id="24dfd-124">Taxa de criminalidade per capita</span><span class="sxs-lookup"><span data-stu-id="24dfd-124">Per capita crime rate</span></span>
| <span data-ttu-id="24dfd-125">2</span><span class="sxs-lookup"><span data-stu-id="24dfd-125">2</span></span> | <span data-ttu-id="24dfd-126">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="24dfd-126">ResidentialZones</span></span> | <span data-ttu-id="24dfd-127">Zonas residenciais da cidade</span><span class="sxs-lookup"><span data-stu-id="24dfd-127">Residential zones in town</span></span>
| <span data-ttu-id="24dfd-128">3</span><span class="sxs-lookup"><span data-stu-id="24dfd-128">3</span></span> | <span data-ttu-id="24dfd-129">CommercialZones</span><span class="sxs-lookup"><span data-stu-id="24dfd-129">CommercialZones</span></span> | <span data-ttu-id="24dfd-130">Zonas não residenciais da cidade</span><span class="sxs-lookup"><span data-stu-id="24dfd-130">Non-residential zones in town</span></span>
| <span data-ttu-id="24dfd-131">4</span><span class="sxs-lookup"><span data-stu-id="24dfd-131">4</span></span> | <span data-ttu-id="24dfd-132">NearWater</span><span class="sxs-lookup"><span data-stu-id="24dfd-132">NearWater</span></span> | <span data-ttu-id="24dfd-133">Proximidade a recursos hídricos</span><span class="sxs-lookup"><span data-stu-id="24dfd-133">Proximity to body of water</span></span>
| <span data-ttu-id="24dfd-134">5</span><span class="sxs-lookup"><span data-stu-id="24dfd-134">5</span></span> | <span data-ttu-id="24dfd-135">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="24dfd-135">ToxicWasteLevels</span></span> | <span data-ttu-id="24dfd-136">Níveis de toxicidade (PPM)</span><span class="sxs-lookup"><span data-stu-id="24dfd-136">Toxicity levels (PPM)</span></span>
| <span data-ttu-id="24dfd-137">6</span><span class="sxs-lookup"><span data-stu-id="24dfd-137">6</span></span> | <span data-ttu-id="24dfd-138">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="24dfd-138">AverageRoomNumber</span></span> | <span data-ttu-id="24dfd-139">Número médio de ambientes na casa</span><span class="sxs-lookup"><span data-stu-id="24dfd-139">Average number of rooms in house</span></span>
| <span data-ttu-id="24dfd-140">7</span><span class="sxs-lookup"><span data-stu-id="24dfd-140">7</span></span> | <span data-ttu-id="24dfd-141">HomeAge</span><span class="sxs-lookup"><span data-stu-id="24dfd-141">HomeAge</span></span> | <span data-ttu-id="24dfd-142">Idade da casa</span><span class="sxs-lookup"><span data-stu-id="24dfd-142">Age of home</span></span>
| <span data-ttu-id="24dfd-143">8</span><span class="sxs-lookup"><span data-stu-id="24dfd-143">8</span></span> | <span data-ttu-id="24dfd-144">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="24dfd-144">BusinessCenterDistance</span></span> | <span data-ttu-id="24dfd-145">Distância até o bairro comercial mais próximo</span><span class="sxs-lookup"><span data-stu-id="24dfd-145">Distance to nearest business district</span></span>
| <span data-ttu-id="24dfd-146">9</span><span class="sxs-lookup"><span data-stu-id="24dfd-146">9</span></span> | <span data-ttu-id="24dfd-147">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="24dfd-147">HighwayAccess</span></span> | <span data-ttu-id="24dfd-148">Proximidade de rodovias</span><span class="sxs-lookup"><span data-stu-id="24dfd-148">Proximity to highways</span></span>
| <span data-ttu-id="24dfd-149">10</span><span class="sxs-lookup"><span data-stu-id="24dfd-149">10</span></span> | <span data-ttu-id="24dfd-150">TaxRate</span><span class="sxs-lookup"><span data-stu-id="24dfd-150">TaxRate</span></span> | <span data-ttu-id="24dfd-151">Taxa de imposto sobre propriedade</span><span class="sxs-lookup"><span data-stu-id="24dfd-151">Property tax rate</span></span>
| <span data-ttu-id="24dfd-152">11</span><span class="sxs-lookup"><span data-stu-id="24dfd-152">11</span></span> | <span data-ttu-id="24dfd-153">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="24dfd-153">StudentTeacherRatio</span></span> | <span data-ttu-id="24dfd-154">Taxa de alunos para professores</span><span class="sxs-lookup"><span data-stu-id="24dfd-154">Ratio of students to teachers</span></span>
| <span data-ttu-id="24dfd-155">12</span><span class="sxs-lookup"><span data-stu-id="24dfd-155">12</span></span> | <span data-ttu-id="24dfd-156">PercentPopulationBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="24dfd-156">PercentPopulationBelowPoverty</span></span> | <span data-ttu-id="24dfd-157">Percentual da população vivendo abaixo da linha de pobreza</span><span class="sxs-lookup"><span data-stu-id="24dfd-157">Percent of population living below poverty</span></span>
| <span data-ttu-id="24dfd-158">13</span><span class="sxs-lookup"><span data-stu-id="24dfd-158">13</span></span> | <span data-ttu-id="24dfd-159">Preço</span><span class="sxs-lookup"><span data-stu-id="24dfd-159">Price</span></span> | <span data-ttu-id="24dfd-160">Preço da casa</span><span class="sxs-lookup"><span data-stu-id="24dfd-160">Price of the home</span></span>

<span data-ttu-id="24dfd-161">Um exemplo do conjunto de dados é mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="24dfd-161">A sample of the dataset is shown below:</span></span>

```text
1,24,13,1,0.59,3,96,11,23,608,14,13,32
4,80,18,1,0.37,5,14,7,4,346,19,13,41
2,98,16,1,0.25,10,5,1,8,689,13,36,12
```

<span data-ttu-id="24dfd-162">Os dados desta amostra podem ser modelados por uma classe como `HousingPriceData` e carregados em uma [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="24dfd-162">The data in this sample can be modeled by a class like `HousingPriceData` and loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

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

## <a name="train-the-model"></a><span data-ttu-id="24dfd-163">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="24dfd-163">Train the model</span></span>

<span data-ttu-id="24dfd-164">O exemplo de código a seguir ilustra o processo de treinamento de um modelo de regressão linear para prever preços de casa.</span><span class="sxs-lookup"><span data-stu-id="24dfd-164">The code sample below illustrates the process of training a linear regression model to predict house prices.</span></span>

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

## <a name="explain-the-model-with-permutation-feature-importance-pfi"></a><span data-ttu-id="24dfd-165">Explicar o modelo com PFI (Importância de Recurso de Permutação)</span><span class="sxs-lookup"><span data-stu-id="24dfd-165">Explain the model with Permutation Feature Importance (PFI)</span></span>

<span data-ttu-id="24dfd-166">No ML.NET, use o método [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) para suas respectivas tarefas.</span><span class="sxs-lookup"><span data-stu-id="24dfd-166">In ML.NET use the [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) method for your respective task.</span></span>

```csharp
ImmutableArray<RegressionMetricsStatistics> permutationFeatureImportance = 
    mlContext
        .Regression
        .PermutationFeatureImportance(sdcaModel, preprocessedTrainData, permutationCount:3);
```

<span data-ttu-id="24dfd-167">O resultado de usar [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) no conjunto de dados de treinamento é um [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) de objetos [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics).</span><span class="sxs-lookup"><span data-stu-id="24dfd-167">The result of using [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) on the training dataset is an [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) of [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) objects.</span></span> <span data-ttu-id="24dfd-168">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) fornece estatísticas resumidas, como média e desvio padrão para várias observações de [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) igual ao número de permutações especificado pelo parâmetro `permutationCount`.</span><span class="sxs-lookup"><span data-stu-id="24dfd-168">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) provides summary statistics like mean and standard deviation for multiple observations of [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) equal to the number of permutations specified by the `permutationCount` parameter.</span></span>

<span data-ttu-id="24dfd-169">A importância ou, neste caso, a redução média absoluta de métrica R ao quadrado calculada por [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) pode ser ordenada da mais importante para a menos importante.</span><span class="sxs-lookup"><span data-stu-id="24dfd-169">The importance, or in this case, the absolute average decrease in R-squared metric calculated by [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) can then be ordered from most important to least important.</span></span>  

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

<span data-ttu-id="24dfd-170">Imprimir os valores para cada um dos recursos em `featureImportanceMetrics` geraria saída semelhante à abaixo.</span><span class="sxs-lookup"><span data-stu-id="24dfd-170">Printing the values for each of the features in `featureImportanceMetrics` would generate output similar to that below.</span></span> <span data-ttu-id="24dfd-171">Lembre-se de que você deve esperar ver resultados diferentes, pois esses valores variam conforme os dados apresentados.</span><span class="sxs-lookup"><span data-stu-id="24dfd-171">Keep in mind that you should expect to see different results because these values vary based on the data that they are given.</span></span>  

| <span data-ttu-id="24dfd-172">Recurso</span><span class="sxs-lookup"><span data-stu-id="24dfd-172">Feature</span></span> | <span data-ttu-id="24dfd-173">Alterar para R ao quadrado</span><span class="sxs-lookup"><span data-stu-id="24dfd-173">Change to R-Squared</span></span> |
|:--|:--:|
<span data-ttu-id="24dfd-174">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="24dfd-174">HighwayAccess</span></span>       |   <span data-ttu-id="24dfd-175">-0,042731</span><span class="sxs-lookup"><span data-stu-id="24dfd-175">-0.042731</span></span>
<span data-ttu-id="24dfd-176">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="24dfd-176">StudentTeacherRatio</span></span> |   <span data-ttu-id="24dfd-177">-0,012730</span><span class="sxs-lookup"><span data-stu-id="24dfd-177">-0.012730</span></span>
<span data-ttu-id="24dfd-178">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="24dfd-178">BusinessCenterDistance</span></span>| <span data-ttu-id="24dfd-179">-0,010491</span><span class="sxs-lookup"><span data-stu-id="24dfd-179">-0.010491</span></span>
<span data-ttu-id="24dfd-180">TaxRate</span><span class="sxs-lookup"><span data-stu-id="24dfd-180">TaxRate</span></span>             |   <span data-ttu-id="24dfd-181">-0,008545</span><span class="sxs-lookup"><span data-stu-id="24dfd-181">-0.008545</span></span>
<span data-ttu-id="24dfd-182">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="24dfd-182">AverageRoomNumber</span></span>   |   <span data-ttu-id="24dfd-183">-0,003949</span><span class="sxs-lookup"><span data-stu-id="24dfd-183">-0.003949</span></span>
<span data-ttu-id="24dfd-184">CrimeRate</span><span class="sxs-lookup"><span data-stu-id="24dfd-184">CrimeRate</span></span>           |   <span data-ttu-id="24dfd-185">-0,003665</span><span class="sxs-lookup"><span data-stu-id="24dfd-185">-0.003665</span></span>
<span data-ttu-id="24dfd-186">CommercialZones</span><span class="sxs-lookup"><span data-stu-id="24dfd-186">CommercialZones</span></span>     |   <span data-ttu-id="24dfd-187">0,002749</span><span class="sxs-lookup"><span data-stu-id="24dfd-187">0.002749</span></span>
<span data-ttu-id="24dfd-188">HomeAge</span><span class="sxs-lookup"><span data-stu-id="24dfd-188">HomeAge</span></span>             |   <span data-ttu-id="24dfd-189">-0,002426</span><span class="sxs-lookup"><span data-stu-id="24dfd-189">-0.002426</span></span>
<span data-ttu-id="24dfd-190">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="24dfd-190">ResidentialZones</span></span>    |   <span data-ttu-id="24dfd-191">-0,002319</span><span class="sxs-lookup"><span data-stu-id="24dfd-191">-0.002319</span></span>
<span data-ttu-id="24dfd-192">NearWater</span><span class="sxs-lookup"><span data-stu-id="24dfd-192">NearWater</span></span>           |   <span data-ttu-id="24dfd-193">0,000203</span><span class="sxs-lookup"><span data-stu-id="24dfd-193">0.000203</span></span>
<span data-ttu-id="24dfd-194">PercentPopulationLivingBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="24dfd-194">PercentPopulationLivingBelowPoverty</span></span>|    <span data-ttu-id="24dfd-195">0,000031</span><span class="sxs-lookup"><span data-stu-id="24dfd-195">0.000031</span></span>
<span data-ttu-id="24dfd-196">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="24dfd-196">ToxicWasteLevels</span></span>    |   <span data-ttu-id="24dfd-197">-0,000019</span><span class="sxs-lookup"><span data-stu-id="24dfd-197">-0.000019</span></span>

<span data-ttu-id="24dfd-198">Vamos analisar os cinco recursos mais importantes para este conjunto de dados, o preço de uma casa previsto por esse modelo é influenciado pela sua proximidade a rodovias, pela proporção de alunos para professor das escolas na área, pela proximidade com centros de emprego importantes, pela taxa de impostos sobre propriedade e pelo número médio de ambientes na casa.</span><span class="sxs-lookup"><span data-stu-id="24dfd-198">Taking a look at the five most important features for this dataset, the price of a house predicted by this model is influenced by its proximity to highways, student teacher ratio of schools in the area, proximity to major employment centers, property tax rate and average number of rooms in the home.</span></span>
