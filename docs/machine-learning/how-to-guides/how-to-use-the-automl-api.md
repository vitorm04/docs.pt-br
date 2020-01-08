---
title: Como usar a API de ML automatizado do ML.NET
description: A API de ML automatizado do ML.NET automatiza o processo de criação de modelo e gera um modelo pronto para implantação. Saiba as opções que você pode usar para configurar tarefas de aprendizado de máquina automatizada.
ms.date: 12/18/2019
ms.custom: mvc,how-to
ms.openlocfilehash: b322c484282d025033d747d2093f7b5b4d216fde
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636556"
---
# <a name="how-to-use-the-mlnet-automated-machine-learning-api"></a><span data-ttu-id="4c0a6-104">Como usar a API de aprendizado de máquina automatizado do ML.NET</span><span class="sxs-lookup"><span data-stu-id="4c0a6-104">How to use the ML.NET automated machine learning API</span></span>

<span data-ttu-id="4c0a6-105">AutoML (aprendizado de máquina automatizado) automatiza o processo de aplicar o aprendizado de máquina a dados.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-105">Automated machine learning (AutoML) automates the process of applying machine learning to data.</span></span> <span data-ttu-id="4c0a6-106">Dado um conjunto de dados, você pode executar um **experimento** de AutoML para iterar em diferentes personalizações de dados, algoritmos de aprendizado de máquina e hiperparâmetros para selecionar o melhor modelo.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-106">Given a dataset, you can run an AutoML **experiment** to iterate over different data featurizations, machine learning algorithms, and hyperparameters to select the best model.</span></span>

> [!NOTE]
> <span data-ttu-id="4c0a6-107">Este tópico refere-se à API de aprendizado de máquina automatizado para ML.NET, que está atualmente em versão prévia.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-107">This topic refers to the automated machine learning API for ML.NET, which is currently in preview.</span></span> <span data-ttu-id="4c0a6-108">O material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-108">Material may be subject to change.</span></span>

## <a name="load-data"></a><span data-ttu-id="4c0a6-109">Carregar dados</span><span class="sxs-lookup"><span data-stu-id="4c0a6-109">Load data</span></span>

<span data-ttu-id="4c0a6-110">O aprendizado de máquina automatizado dá suporte para carregar um conjunto de dados para uma [IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="4c0a6-110">Automated machine learning supports loading a dataset into an [IDataView](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="4c0a6-111">Os dados podem estar na forma de arquivos TSV (valor separado por tabulações) e CSV (valor separado por vírgulas).</span><span class="sxs-lookup"><span data-stu-id="4c0a6-111">Data can be in the form of tab-separated value (TSV) files and comma separated value (CSV) files.</span></span>

<span data-ttu-id="4c0a6-112">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="4c0a6-112">Example:</span></span>

```csharp
using Microsoft.ML;
using Microsoft.ML.AutoML;
    // ...
    MLContext mlContext = new MLContext();
    IDataView trainDataView = mlContext.Data.LoadFromTextFile<SentimentIssue>("my-data-file.csv", hasHeader: true);
```

## <a name="select-the-machine-learning-task-type"></a><span data-ttu-id="4c0a6-113">Selecione o tipo de tarefa de aprendizado de máquina</span><span class="sxs-lookup"><span data-stu-id="4c0a6-113">Select the machine learning task type</span></span>

<span data-ttu-id="4c0a6-114">Antes de criar um experimento, determine o tipo de problema de aprendizado de máquina que você deseja resolver.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-114">Before creating an experiment, determine the kind of machine learning problem you want to solve.</span></span> <span data-ttu-id="4c0a6-115">Aprendizado de máquina automatizado é compatível com as seguintes tarefas de ML:</span><span class="sxs-lookup"><span data-stu-id="4c0a6-115">Automated machine learning supports the following ML tasks:</span></span>

* <span data-ttu-id="4c0a6-116">Classificação Binária</span><span class="sxs-lookup"><span data-stu-id="4c0a6-116">Binary Classification</span></span>
* <span data-ttu-id="4c0a6-117">Classificação Multiclasse</span><span class="sxs-lookup"><span data-stu-id="4c0a6-117">Multiclass Classification</span></span>
* <span data-ttu-id="4c0a6-118">Regressão</span><span class="sxs-lookup"><span data-stu-id="4c0a6-118">Regression</span></span>
* <span data-ttu-id="4c0a6-119">Recomendação</span><span class="sxs-lookup"><span data-stu-id="4c0a6-119">Recommendation</span></span>

## <a name="create-experiment-settings"></a><span data-ttu-id="4c0a6-120">Criar configurações de experimento</span><span class="sxs-lookup"><span data-stu-id="4c0a6-120">Create experiment settings</span></span>

<span data-ttu-id="4c0a6-121">Criar configurações de experimento para o tipo de tarefa de ML determinado:</span><span class="sxs-lookup"><span data-stu-id="4c0a6-121">Create experiment settings for the determined ML task type:</span></span>

* <span data-ttu-id="4c0a6-122">Classificação Binária</span><span class="sxs-lookup"><span data-stu-id="4c0a6-122">Binary Classification</span></span>

  ```csharp
  var experimentSettings = new BinaryExperimentSettings();
  ```

* <span data-ttu-id="4c0a6-123">Classificação Multiclasse</span><span class="sxs-lookup"><span data-stu-id="4c0a6-123">Multiclass Classification</span></span>

  ```csharp
  var experimentSettings = new MulticlassExperimentSettings();
  ```

* <span data-ttu-id="4c0a6-124">Regressão</span><span class="sxs-lookup"><span data-stu-id="4c0a6-124">Regression</span></span>

  ```csharp
  var experimentSettings = new RegressionExperimentSettings();
  ```

* <span data-ttu-id="4c0a6-125">Recomendação</span><span class="sxs-lookup"><span data-stu-id="4c0a6-125">Recommendation</span></span>

  ```csharp
  var experimentSettings = new RecommendationExperimentSettings();
  ```

## <a name="configure-experiment-settings"></a><span data-ttu-id="4c0a6-126">Definir as configurações de teste</span><span class="sxs-lookup"><span data-stu-id="4c0a6-126">Configure experiment settings</span></span>

<span data-ttu-id="4c0a6-127">Os experimentos são altamente configuráveis.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-127">Experiments are highly configurable.</span></span> <span data-ttu-id="4c0a6-128">Veja os [documentos de API de AutoML](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl?view=ml-dotnet-preview) para obter uma lista completa de definições de configuração.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-128">See the [AutoML API docs](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl?view=ml-dotnet-preview) for a full list of configuration settings.</span></span>

<span data-ttu-id="4c0a6-129">Eis alguns exemplos:</span><span class="sxs-lookup"><span data-stu-id="4c0a6-129">Some examples include:</span></span>

1. <span data-ttu-id="4c0a6-130">Especifique o tempo máximo pelo qual o experimento pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-130">Specify the maximum time that the experiment is allowed to run.</span></span>

    ```csharp
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    ```

1. <span data-ttu-id="4c0a6-131">Use um token de cancelamento para cancelar o experimento antes de seu término agendado.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-131">Use a cancellation token to cancel the experiment before it is scheduled to finish.</span></span>

    ```csharp
    experimentSettings.CancellationToken = cts.Token;

    // Cancel experiment after the user presses any key
    CancelExperimentAfterAnyKeyPress(cts);
    ```

1. <span data-ttu-id="4c0a6-132">Especifique uma métrica de otimização diferente.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-132">Specify a different optimizing metric.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.OptimizingMetric = RegressionMetric.MeanSquaredError;
    ```

1. <span data-ttu-id="4c0a6-133">A configuração `CacheDirectory` é um ponteiro para um diretório em que todos os modelos treinados durante a tarefa AutoML serão salvos.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-133">The `CacheDirectory` setting is a pointer to a directory where all models trained during the AutoML task will be saved.</span></span> <span data-ttu-id="4c0a6-134">Se `CacheDirectory` for definido como nulo, os modelos serão mantidos na memória, em vez de gravados em disco.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-134">If `CacheDirectory` is set to null, models will be kept in memory instead of written to disk.</span></span>

    ```csharp
    experimentSettings.CacheDirectory = null;
    ```

1. <span data-ttu-id="4c0a6-135">Instrua ML automatizado a não usar determinados treinadores.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-135">Instruct automated ML not to use certain trainers.</span></span>

    <span data-ttu-id="4c0a6-136">Uma lista padrão de treinadores para otimizar é explorada por tarefa.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-136">A default list of trainers to optimize are explored per task.</span></span> <span data-ttu-id="4c0a6-137">Essa lista pode ser modificada para cada experimento.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-137">This list can be modified for each experiment.</span></span> <span data-ttu-id="4c0a6-138">Por exemplo, treinadores executados lentamente em seu conjunto de dados podem ser removidos da lista.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-138">For instance, trainers that run slowly on your dataset can be removed from the list.</span></span> <span data-ttu-id="4c0a6-139">Para otimizar um treinador específico, chame `experimentSettings.Trainers.Clear()` e adicione o treinador que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-139">To optimize on one specific trainer call `experimentSettings.Trainers.Clear()`, then add the trainer that you want to use.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.Trainers.Remove(RegressionTrainer.LbfgsPoissonRegression);
    experimentSettings.Trainers.Remove(RegressionTrainer.OnlineGradientDescent);
    ```

<span data-ttu-id="4c0a6-140">A lista de treinadores com suporte por tarefa de ML pode ser encontrada no link correspondente abaixo:</span><span class="sxs-lookup"><span data-stu-id="4c0a6-140">The list of supported trainers per ML task can be found at the corresponding link below:</span></span>

* [<span data-ttu-id="4c0a6-141">Algoritmos de Classificação Binária com Suporte</span><span class="sxs-lookup"><span data-stu-id="4c0a6-141">Supported Binary Classification Algorithms</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationTrainer)
* [<span data-ttu-id="4c0a6-142">Algoritmos de Classificação Multiclasse com Suporte</span><span class="sxs-lookup"><span data-stu-id="4c0a6-142">Supported Multiclass Classification Algorithms</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationTrainer)
* [<span data-ttu-id="4c0a6-143">Algoritmos de Regressão com Suporte</span><span class="sxs-lookup"><span data-stu-id="4c0a6-143">Supported Regression Algorithms</span></span>](xref:Microsoft.ML.AutoML.RegressionTrainer)
* [<span data-ttu-id="4c0a6-144">Algoritmos de recomendação com suporte</span><span class="sxs-lookup"><span data-stu-id="4c0a6-144">Supported Recommendation Algorithms</span></span>](xref:Microsoft.ML.AutoML.RecommendationTrainer)

## <a name="optimizing-metric"></a><span data-ttu-id="4c0a6-145">Métrica de otimização</span><span class="sxs-lookup"><span data-stu-id="4c0a6-145">Optimizing metric</span></span>

<span data-ttu-id="4c0a6-146">A métrica da otimiza, conforme mostrado no exemplo acima, determina a métrica a ser otimizada durante o treinamento de modelo.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-146">The optimizing metric, as shown in the example above, determines the metric to be optimized during model training.</span></span> <span data-ttu-id="4c0a6-147">A métrica de otimização que você pode selecionar é determinada pelo tipo de tarefa que você escolher.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-147">The optimizing metric you can select is determined by the task type you choose.</span></span> <span data-ttu-id="4c0a6-148">Abaixo está uma lista de métricas disponíveis.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-148">Below is a list of available metrics.</span></span>

|[<span data-ttu-id="4c0a6-149">Classificação Binária</span><span class="sxs-lookup"><span data-stu-id="4c0a6-149">Binary Classification</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationMetric) | [<span data-ttu-id="4c0a6-150">Classificação Multiclasse</span><span class="sxs-lookup"><span data-stu-id="4c0a6-150">Multiclass Classification</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric) |[<span data-ttu-id="4c0a6-151">Regressão & recomendação</span><span class="sxs-lookup"><span data-stu-id="4c0a6-151">Regression & Recommendation</span></span>](xref:Microsoft.ML.AutoML.RegressionMetric)
|-- |-- |--
|<span data-ttu-id="4c0a6-152">Precisão</span><span class="sxs-lookup"><span data-stu-id="4c0a6-152">Accuracy</span></span>| <span data-ttu-id="4c0a6-153">LogLoss</span><span class="sxs-lookup"><span data-stu-id="4c0a6-153">LogLoss</span></span> | <span data-ttu-id="4c0a6-154">RSquared</span><span class="sxs-lookup"><span data-stu-id="4c0a6-154">RSquared</span></span>
|<span data-ttu-id="4c0a6-155">AreaUnderPrecisionRecallCurve</span><span class="sxs-lookup"><span data-stu-id="4c0a6-155">AreaUnderPrecisionRecallCurve</span></span> | <span data-ttu-id="4c0a6-156">LogLossReduction</span><span class="sxs-lookup"><span data-stu-id="4c0a6-156">LogLossReduction</span></span> | <span data-ttu-id="4c0a6-157">MeanAbsoluteError</span><span class="sxs-lookup"><span data-stu-id="4c0a6-157">MeanAbsoluteError</span></span>
|<span data-ttu-id="4c0a6-158">AreaUnderRocCurve</span><span class="sxs-lookup"><span data-stu-id="4c0a6-158">AreaUnderRocCurve</span></span> | <span data-ttu-id="4c0a6-159">MacroAccuracy</span><span class="sxs-lookup"><span data-stu-id="4c0a6-159">MacroAccuracy</span></span> | <span data-ttu-id="4c0a6-160">MeanSquaredError</span><span class="sxs-lookup"><span data-stu-id="4c0a6-160">MeanSquaredError</span></span>
|<span data-ttu-id="4c0a6-161">F1Score</span><span class="sxs-lookup"><span data-stu-id="4c0a6-161">F1Score</span></span> | <span data-ttu-id="4c0a6-162">MicroAccuracy</span><span class="sxs-lookup"><span data-stu-id="4c0a6-162">MicroAccuracy</span></span> | <span data-ttu-id="4c0a6-163">RootMeanSquaredError</span><span class="sxs-lookup"><span data-stu-id="4c0a6-163">RootMeanSquaredError</span></span>
|<span data-ttu-id="4c0a6-164">NegativePrecision</span><span class="sxs-lookup"><span data-stu-id="4c0a6-164">NegativePrecision</span></span> | <span data-ttu-id="4c0a6-165">TopKAccuracy</span><span class="sxs-lookup"><span data-stu-id="4c0a6-165">TopKAccuracy</span></span>
|<span data-ttu-id="4c0a6-166">NegativeRecall</span><span class="sxs-lookup"><span data-stu-id="4c0a6-166">NegativeRecall</span></span> |
|<span data-ttu-id="4c0a6-167">PositivePrecision</span><span class="sxs-lookup"><span data-stu-id="4c0a6-167">PositivePrecision</span></span>
|<span data-ttu-id="4c0a6-168">PositiveRecall</span><span class="sxs-lookup"><span data-stu-id="4c0a6-168">PositiveRecall</span></span>

## <a name="data-pre-processing-and-featurization"></a><span data-ttu-id="4c0a6-169">Pré-processamento de dados e personalização</span><span class="sxs-lookup"><span data-stu-id="4c0a6-169">Data pre-processing and featurization</span></span>

> [!NOTE]
> <span data-ttu-id="4c0a6-170">A coluna de recursos tem suporte apenas para tipos de <xref:System.Boolean>, <xref:System.Single>e <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-170">The feature column only supported types of <xref:System.Boolean>, <xref:System.Single>, and <xref:System.String>.</span></span>

<span data-ttu-id="4c0a6-171">O pré-processamento de dados ocorre por padrão e as etapas a seguir são executadas automaticamente para você:</span><span class="sxs-lookup"><span data-stu-id="4c0a6-171">Data pre-processing happens by default and the following steps are performed automatically for you:</span></span>

1. <span data-ttu-id="4c0a6-172">Remover os recursos sem informações úteis</span><span class="sxs-lookup"><span data-stu-id="4c0a6-172">Drop features with no useful information</span></span>

    <span data-ttu-id="4c0a6-173">Remover os recursos sem informações úteis de conjuntos de treinamento e validação.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-173">Drop features with no useful information from training and validation sets.</span></span> <span data-ttu-id="4c0a6-174">Incluem recursos com todos os valores ausentes, com o mesmo valor em todas as linhas ou com cardinalidade muito alta (por exemplo, hashes, IDs ou GUIDs).</span><span class="sxs-lookup"><span data-stu-id="4c0a6-174">These include features with all values missing, same value across all rows or with extremely high cardinality (e.g., hashes, IDs or GUIDs).</span></span>

1. <span data-ttu-id="4c0a6-175">Imputação e indicação de valor ausente</span><span class="sxs-lookup"><span data-stu-id="4c0a6-175">Missing value indication and imputation</span></span>

    <span data-ttu-id="4c0a6-176">Preencha as células de valor ausente com o valor padrão para o tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-176">Fill missing value cells with the default value for the datatype.</span></span> <span data-ttu-id="4c0a6-177">Acrescente recursos de indicador com o mesmo número de slots de que a coluna de entrada.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-177">Append indicator features with the same number of slots as the input column.</span></span> <span data-ttu-id="4c0a6-178">O valor nos recursos de indicador acrescentados será `1` se o valor na coluna de entrada estiver ausente e `0`, caso contrário.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-178">The value in the appended indicator features is `1` if the value in the input column is missing and `0` otherwise.</span></span>

1. <span data-ttu-id="4c0a6-179">Gerar recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="4c0a6-179">Generate additional features</span></span>

    <span data-ttu-id="4c0a6-180">Para recursos de texto: recursos de conjunto de palavras usando unigrams e Tri-Character-grams.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-180">For text features: Bag-of-word features using unigrams and tri-character-grams.</span></span>

    <span data-ttu-id="4c0a6-181">Para recursos categóricos: codificação One-Hot para recursos de cardinalidade baixa e codificação de hash One-Hot para recursos categóricos de alta cardinalidade.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-181">For categorical features: One-hot encoding for low cardinality features, and one-hot-hash encoding for high cardinality categorical features.</span></span>

1. <span data-ttu-id="4c0a6-182">Codificações e transformações</span><span class="sxs-lookup"><span data-stu-id="4c0a6-182">Transformations and encodings</span></span>

    <span data-ttu-id="4c0a6-183">Recursos de texto com poucos valores exclusivos transformados em recursos categóricos.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-183">Text features with very few unique values transformed into categorical features.</span></span> <span data-ttu-id="4c0a6-184">Dependendo da cardinalidade de recursos categóricos, execute codificação one-hot ou codificação one-hot hash.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-184">Depending on cardinality of categorical features, perform one-hot encoding or one-hot hash encoding.</span></span>

## <a name="exit-criteria"></a><span data-ttu-id="4c0a6-185">Critérios de saída</span><span class="sxs-lookup"><span data-stu-id="4c0a6-185">Exit criteria</span></span>

<span data-ttu-id="4c0a6-186">Defina os critérios para concluir sua tarefa:</span><span class="sxs-lookup"><span data-stu-id="4c0a6-186">Define the criteria to complete your task:</span></span>

1. <span data-ttu-id="4c0a6-187">Saída após um período – usando `MaxExperimentTimeInSeconds` em suas configurações de experimento, você pode definir quanto tempo em segundos uma tarefa deve continuar em execução.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-187">Exit after a length of time - Using `MaxExperimentTimeInSeconds` in your experiment settings you can define how long in seconds that an task should continue to run.</span></span>

1. <span data-ttu-id="4c0a6-188">Saída em um token de cancelamento – você pode usar um token de cancelamento que permita cancelar a tarefa antes de seu término agendado.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-188">Exit on a cancellation token -  You can use a cancellation token that lets you cancel the task before it is scheduled to finish.</span></span>

    ```csharp
    var cts = new CancellationTokenSource();
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    experimentSettings.CancellationToken = cts.Token;
    ```

## <a name="create-an-experiment"></a><span data-ttu-id="4c0a6-189">Criar um experimento</span><span class="sxs-lookup"><span data-stu-id="4c0a6-189">Create an experiment</span></span>

<span data-ttu-id="4c0a6-190">Depois de definir as configurações de teste, você está pronto para criar o experimento.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-190">Once you have configured the experiment settings, you are ready to create the experiment.</span></span>

```csharp
RegressionExperiment experiment = mlContext.Auto().CreateRegressionExperiment(experimentSettings);
```

## <a name="run-the-experiment"></a><span data-ttu-id="4c0a6-191">Executar o experimento</span><span class="sxs-lookup"><span data-stu-id="4c0a6-191">Run the experiment</span></span>

<span data-ttu-id="4c0a6-192">Executar o experimento dispara o pré-processamento de dados, a seleção do algoritmo de aprendizado e o ajuste de hiperparâmetro.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-192">Running the experiment triggers data pre-processing, learning algorithm selection, and hyperparameter tuning.</span></span> <span data-ttu-id="4c0a6-193">AutoML continuará a gerar combinações de personalização, algoritmos de aprendizado e hiperparâmetros até o `MaxExperimentTimeInSeconds` ser atingido ou o experimento ser encerrado.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-193">AutoML will continue to generate combinations of featurization, learning algorithms, and hyperparameters until the `MaxExperimentTimeInSeconds` is reached or the experiment is terminated.</span></span>

```csharp
ExperimentResult<RegressionMetrics> experimentResult = experiment
    .Execute(trainingDataView, LabelColumnName, progressHandler: progressHandler);
```

<span data-ttu-id="4c0a6-194">Explore outras sobrecargas para `Execute()` se quiser passar dados de validação, informações de coluna indicando a finalidade de coluna ou pré-personalizações.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-194">Explore other overloads for `Execute()` if you want to pass in validation data, column information indicating the column purpose, or prefeaturizers.</span></span>

## <a name="training-modes"></a><span data-ttu-id="4c0a6-195">Modos de treinamento</span><span class="sxs-lookup"><span data-stu-id="4c0a6-195">Training modes</span></span>

### <a name="training-dataset"></a><span data-ttu-id="4c0a6-196">Conjunto de dados de treinamento</span><span class="sxs-lookup"><span data-stu-id="4c0a6-196">Training dataset</span></span>

<span data-ttu-id="4c0a6-197">O AutoML oferece um método de execução de experimento sobrecarregado que possibilita que você forneça dados de treinamento.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-197">AutoML provides an overloaded experiment execute method which allows you to provide training data.</span></span> <span data-ttu-id="4c0a6-198">Internamente, o ML automatizado divide os dados em divisões train-validate.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-198">Internally, automated ML divides the data into train-validate splits.</span></span>

```csharp
experiment.Execute(trainDataView);
```

### <a name="custom-validation-dataset"></a><span data-ttu-id="4c0a6-199">Conjunto de dados de validação personalizado</span><span class="sxs-lookup"><span data-stu-id="4c0a6-199">Custom validation dataset</span></span>

<span data-ttu-id="4c0a6-200">Use o conjunto de dados de validação personalizado se divisão aleatória não for aceitável, como normalmente é o caso para dados de série temporal.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-200">Use custom validation dataset if random split is not acceptable, as is usually the case with time series data.</span></span> <span data-ttu-id="4c0a6-201">Você pode especificar seu próprio conjunto de dados de validação.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-201">You can specify your own validation dataset.</span></span> <span data-ttu-id="4c0a6-202">O modelo será avaliado em relação ao conjunto de dados de validação especificado, em vez de um ou mais conjuntos de dados aleatórios.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-202">The model will be evaluated against the validation dataset specified instead of one or more random datasets.</span></span>

```csharp
experiment.Execute(trainDataView, validationDataView);
```

## <a name="explore-model-metrics"></a><span data-ttu-id="4c0a6-203">Explore as métricas do modelo</span><span class="sxs-lookup"><span data-stu-id="4c0a6-203">Explore model metrics</span></span>

<span data-ttu-id="4c0a6-204">Depois de cada iteração de um experimento de ML, as métricas relacionadas à tarefa são armazenadas.</span><span class="sxs-lookup"><span data-stu-id="4c0a6-204">After each iteration of an ML experiment, metrics relating to that task are stored.</span></span>

<span data-ttu-id="4c0a6-205">Por exemplo, podemos acessar as métricas de validação da melhor execução:</span><span class="sxs-lookup"><span data-stu-id="4c0a6-205">For example, we can access validation metrics from the best run:</span></span>

```csharp
RegressionMetrics metrics = experimentResult.BestRun.ValidationMetrics;
Console.WriteLine($"R-Squared: {metrics.RSquared:0.##}");
Console.WriteLine($"Root Mean Squared Error: {metrics.RootMeanSquaredError:0.##}");
```

<span data-ttu-id="4c0a6-206">Estas são todas as métricas disponíveis por tarefa de ML:</span><span class="sxs-lookup"><span data-stu-id="4c0a6-206">The following are all the available metrics per ML task:</span></span>

* [<span data-ttu-id="4c0a6-207">Métricas de classificação binária</span><span class="sxs-lookup"><span data-stu-id="4c0a6-207">Binary classification metrics</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationMetric)
* [<span data-ttu-id="4c0a6-208">Métricas de classificação multiclasse</span><span class="sxs-lookup"><span data-stu-id="4c0a6-208">Multiclass classification metrics</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric)
* [<span data-ttu-id="4c0a6-209">Regressão & métricas de recomendação</span><span class="sxs-lookup"><span data-stu-id="4c0a6-209">Regression & recommendation metrics</span></span>](xref:Microsoft.ML.AutoML.RegressionMetric)

## <a name="see-also"></a><span data-ttu-id="4c0a6-210">Veja também</span><span class="sxs-lookup"><span data-stu-id="4c0a6-210">See also</span></span>

<span data-ttu-id="4c0a6-211">Para exemplos de código completos e muito mais, acesse o repositório do GitHub [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state).</span><span class="sxs-lookup"><span data-stu-id="4c0a6-211">For full code samples and more visit the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) GitHub repository.</span></span>
