---
title: Como usar a API de ML automatizado do ML.NET
description: A API de ML automatizado do ML.NET automatiza o processo de criação de modelo e gera um modelo pronto para implantação. Saiba as opções que você pode usar para configurar tarefas de aprendizado de máquina automatizada.
ms.date: 04/24/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 02e4203b0d9f388c7bd7133f3cd4e97cc60cff14
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929385"
---
# <a name="how-to-use-the-mlnet-automated-machine-learning-api"></a><span data-ttu-id="2ed37-104">Como usar a API de aprendizado de máquina automatizado do ML.NET</span><span class="sxs-lookup"><span data-stu-id="2ed37-104">How to use the ML.NET automated machine learning API</span></span>

<span data-ttu-id="2ed37-105">AutoML (aprendizado de máquina automatizado) automatiza o processo de aplicar o aprendizado de máquina a dados.</span><span class="sxs-lookup"><span data-stu-id="2ed37-105">Automated machine learning (AutoML) automates the process of applying machine learning to data.</span></span> <span data-ttu-id="2ed37-106">Dado um conjunto de dados, você pode executar um **experimento** de AutoML para iterar em diferentes personalizações de dados, algoritmos de aprendizado de máquina e hiperparâmetros para selecionar o melhor modelo.</span><span class="sxs-lookup"><span data-stu-id="2ed37-106">Given a dataset, you can run an AutoML **experiment** to iterate over different data featurizations, machine learning algorithms, and hyperparameters to select the best model.</span></span>

> [!NOTE]
> <span data-ttu-id="2ed37-107">Este tópico refere-se à API de aprendizado de máquina automatizado para ML.NET, que está atualmente em versão prévia.</span><span class="sxs-lookup"><span data-stu-id="2ed37-107">This topic refers to the automated machine learning API for ML.NET, which is currently in preview.</span></span> <span data-ttu-id="2ed37-108">O material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="2ed37-108">Material may be subject to change.</span></span>

## <a name="load-data"></a><span data-ttu-id="2ed37-109">Carregar dados</span><span class="sxs-lookup"><span data-stu-id="2ed37-109">Load data</span></span>

<span data-ttu-id="2ed37-110">O aprendizado de máquina automatizado dá suporte para carregar um conjunto de dados para uma [IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="2ed37-110">Automated machine learning supports loading a dataset into an [IDataView](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="2ed37-111">Os dados podem estar na forma de arquivos TSV (valor separado por tabulações) e CSV (valor separado por vírgulas).</span><span class="sxs-lookup"><span data-stu-id="2ed37-111">Data can be in the form of tab-separated value (TSV) files and comma separated value (CSV) files.</span></span>

<span data-ttu-id="2ed37-112">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="2ed37-112">Example:</span></span>

```csharp
using Microsoft.ML;
using Microsoft.ML.AutoML;
    // ...
    MLContext mlContext = new MLContext();
    IDataView trainDataView = mlContext.Data.LoadFromTextFile<SentimentIssue>("my-data-file.csv", hasHeader: true);
```

## <a name="select-the-machine-learning-task-type"></a><span data-ttu-id="2ed37-113">Selecione o tipo de tarefa de aprendizado de máquina</span><span class="sxs-lookup"><span data-stu-id="2ed37-113">Select the machine learning task type</span></span>
<span data-ttu-id="2ed37-114">Antes de criar um experimento, determine o tipo de problema de aprendizado de máquina que você deseja resolver.</span><span class="sxs-lookup"><span data-stu-id="2ed37-114">Before creating an experiment, determine the kind of machine learning problem you want to solve.</span></span> <span data-ttu-id="2ed37-115">Aprendizado de máquina automatizado é compatível com as seguintes tarefas de ML:</span><span class="sxs-lookup"><span data-stu-id="2ed37-115">Automated machine learning supports the following ML tasks:</span></span>

* <span data-ttu-id="2ed37-116">Classificação Binária</span><span class="sxs-lookup"><span data-stu-id="2ed37-116">Binary Classification</span></span>
* <span data-ttu-id="2ed37-117">Classificação Multiclasse</span><span class="sxs-lookup"><span data-stu-id="2ed37-117">Multiclass Classification</span></span>
* <span data-ttu-id="2ed37-118">Regressão</span><span class="sxs-lookup"><span data-stu-id="2ed37-118">Regression</span></span>

## <a name="create-experiment-settings"></a><span data-ttu-id="2ed37-119">Criar configurações de experimento</span><span class="sxs-lookup"><span data-stu-id="2ed37-119">Create experiment settings</span></span>

<span data-ttu-id="2ed37-120">Criar configurações de experimento para o tipo de tarefa de ML determinado:</span><span class="sxs-lookup"><span data-stu-id="2ed37-120">Create experiment settings for the determined ML task type:</span></span>

* <span data-ttu-id="2ed37-121">Classificação Binária</span><span class="sxs-lookup"><span data-stu-id="2ed37-121">Binary Classification</span></span>

  ```csharp
  var experimentSettings = new BinaryExperimentSettings();
  ```

* <span data-ttu-id="2ed37-122">Classificação Multiclasse</span><span class="sxs-lookup"><span data-stu-id="2ed37-122">Multiclass Classification</span></span>

  ```csharp
  var experimentSettings = new MulticlassExperimentSettings();
  ```

* <span data-ttu-id="2ed37-123">Regressão</span><span class="sxs-lookup"><span data-stu-id="2ed37-123">Regression</span></span>

  ```csharp
  var experimentSettings = new RegressionExperimentSettings();
  ```

## <a name="configure-experiment-settings"></a><span data-ttu-id="2ed37-124">Definir as configurações de teste</span><span class="sxs-lookup"><span data-stu-id="2ed37-124">Configure experiment settings</span></span>

<span data-ttu-id="2ed37-125">Os experimentos são altamente configuráveis.</span><span class="sxs-lookup"><span data-stu-id="2ed37-125">Experiments are highly configurable.</span></span> <span data-ttu-id="2ed37-126">Veja os [documentos de API de AutoML](https://docs.microsoft.com/dotnet/api/?view=automl-dotnet) para obter uma lista completa de definições de configuração.</span><span class="sxs-lookup"><span data-stu-id="2ed37-126">See the [AutoML API docs](https://docs.microsoft.com/dotnet/api/?view=automl-dotnet) for a full list of configuration settings.</span></span>

<span data-ttu-id="2ed37-127">Eis alguns exemplos:</span><span class="sxs-lookup"><span data-stu-id="2ed37-127">Some examples include:</span></span>

1. <span data-ttu-id="2ed37-128">Especifique o tempo máximo pelo qual o experimento pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="2ed37-128">Specify the maximum time that the experiment is allowed to run.</span></span>

    ```csharp
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    ```

1. <span data-ttu-id="2ed37-129">Use um token de cancelamento para cancelar o experimento antes de seu término agendado.</span><span class="sxs-lookup"><span data-stu-id="2ed37-129">Use a cancellation token to cancel the experiment before it is scheduled to finish.</span></span>

    ```csharp
    experimentSettings.CancellationToken = cts.Token;

    // Cancel experiment after the user presses any key
    CancelExperimentAfterAnyKeyPress(cts);
    ```

1. <span data-ttu-id="2ed37-130">Especifique uma métrica de otimização diferente.</span><span class="sxs-lookup"><span data-stu-id="2ed37-130">Specify a different optimizing metric.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.OptimizingMetric = RegressionMetric.MeanSquaredError;
    ```

1. <span data-ttu-id="2ed37-131">A configuração `CacheDirectory` é um ponteiro para um diretório em que todos os modelos treinados durante a tarefa AutoML serão salvos.</span><span class="sxs-lookup"><span data-stu-id="2ed37-131">The `CacheDirectory` setting is a pointer to a directory where all models trained during the AutoML task will be saved.</span></span> <span data-ttu-id="2ed37-132">Se `CacheDirectory` for definido como nulo, os modelos serão mantidos na memória, em vez de gravados em disco.</span><span class="sxs-lookup"><span data-stu-id="2ed37-132">If `CacheDirectory` is set to null, models will be kept in memory instead of written to disk.</span></span>
 
    ```csharp
    experimentSettings.CacheDirectory = null;
    ```

1. <span data-ttu-id="2ed37-133">Instrua ML automatizado a não usar determinados treinadores.</span><span class="sxs-lookup"><span data-stu-id="2ed37-133">Instruct automated ML not to use certain trainers.</span></span>

    <span data-ttu-id="2ed37-134">Uma lista padrão de treinadores para otimizar é explorada por tarefa.</span><span class="sxs-lookup"><span data-stu-id="2ed37-134">A default list of trainers to optimize are explored per task.</span></span> <span data-ttu-id="2ed37-135">Essa lista pode ser modificada para cada experimento.</span><span class="sxs-lookup"><span data-stu-id="2ed37-135">This list can be modified for each experiment.</span></span> <span data-ttu-id="2ed37-136">Por exemplo, treinadores executados lentamente em seu conjunto de dados podem ser removidos da lista.</span><span class="sxs-lookup"><span data-stu-id="2ed37-136">For instance, trainers that run slowly on your dataset can be removed from the list.</span></span> <span data-ttu-id="2ed37-137">Para otimizar um treinador específico, chame `experimentSettings.Trainers.Clear()` e adicione o treinador que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="2ed37-137">To optimize on one specific trainer call `experimentSettings.Trainers.Clear()`, then add the trainer that you want to use.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.Trainers.Remove(RegressionTrainer.LbfgsPoissonRegression);
    experimentSettings.Trainers.Remove(RegressionTrainer.OnlineGradientDescent);
    ```

<span data-ttu-id="2ed37-138">A lista de treinadores com suporte por tarefa de ML pode ser encontrada no link correspondente abaixo:</span><span class="sxs-lookup"><span data-stu-id="2ed37-138">The list of supported trainers per ML task can be found at the corresponding link below:</span></span>

* [<span data-ttu-id="2ed37-139">Algoritmos de Classificação Binária com Suporte</span><span class="sxs-lookup"><span data-stu-id="2ed37-139">Supported Binary Classification Algorithms</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationTrainer)
* [<span data-ttu-id="2ed37-140">Algoritmos de Classificação Multiclasse com Suporte</span><span class="sxs-lookup"><span data-stu-id="2ed37-140">Supported Multiclass Classification Algorithms</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationTrainer)
* [<span data-ttu-id="2ed37-141">Algoritmos de Regressão com Suporte</span><span class="sxs-lookup"><span data-stu-id="2ed37-141">Supported Regression Algorithms</span></span>](xref:Microsoft.ML.AutoML.RegressionTrainer)

## <a name="optimizing-metric"></a><span data-ttu-id="2ed37-142">Métrica de otimização</span><span class="sxs-lookup"><span data-stu-id="2ed37-142">Optimizing metric</span></span>

<span data-ttu-id="2ed37-143">A métrica da otimiza, conforme mostrado no exemplo acima, determina a métrica a ser otimizada durante o treinamento de modelo.</span><span class="sxs-lookup"><span data-stu-id="2ed37-143">The optimizing metric, as shown in the example above, determines the metric to be optimized during model training.</span></span> <span data-ttu-id="2ed37-144">A métrica de otimização que você pode selecionar é determinada pelo tipo de tarefa que você escolher.</span><span class="sxs-lookup"><span data-stu-id="2ed37-144">The optimizing metric you can select is determined by the task type you choose.</span></span> <span data-ttu-id="2ed37-145">Abaixo está uma lista de métricas disponíveis.</span><span class="sxs-lookup"><span data-stu-id="2ed37-145">Below is a list of available metrics.</span></span>

|[<span data-ttu-id="2ed37-146">Classificação Binária</span><span class="sxs-lookup"><span data-stu-id="2ed37-146">Binary Classification</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationMetric) | [<span data-ttu-id="2ed37-147">Classificação Multiclasse</span><span class="sxs-lookup"><span data-stu-id="2ed37-147">Multiclass Classification</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric) |[<span data-ttu-id="2ed37-148">Regressão</span><span class="sxs-lookup"><span data-stu-id="2ed37-148">Regression</span></span>](xref:Microsoft.ML.AutoML.RegressionMetric)
|-- |-- |--
|<span data-ttu-id="2ed37-149">Precisão</span><span class="sxs-lookup"><span data-stu-id="2ed37-149">Accuracy</span></span>| <span data-ttu-id="2ed37-150">LogLoss</span><span class="sxs-lookup"><span data-stu-id="2ed37-150">LogLoss</span></span> | <span data-ttu-id="2ed37-151">RSquared</span><span class="sxs-lookup"><span data-stu-id="2ed37-151">RSquared</span></span>
|<span data-ttu-id="2ed37-152">AreaUnderPrecisionRecallCurve</span><span class="sxs-lookup"><span data-stu-id="2ed37-152">AreaUnderPrecisionRecallCurve</span></span> | <span data-ttu-id="2ed37-153">LogLossReduction</span><span class="sxs-lookup"><span data-stu-id="2ed37-153">LogLossReduction</span></span> | <span data-ttu-id="2ed37-154">MeanAbsoluteError</span><span class="sxs-lookup"><span data-stu-id="2ed37-154">MeanAbsoluteError</span></span>
|<span data-ttu-id="2ed37-155">AreaUnderRocCurve</span><span class="sxs-lookup"><span data-stu-id="2ed37-155">AreaUnderRocCurve</span></span> | <span data-ttu-id="2ed37-156">MacroAccuracy</span><span class="sxs-lookup"><span data-stu-id="2ed37-156">MacroAccuracy</span></span> | <span data-ttu-id="2ed37-157">MeanSquaredError</span><span class="sxs-lookup"><span data-stu-id="2ed37-157">MeanSquaredError</span></span>
|<span data-ttu-id="2ed37-158">F1Score</span><span class="sxs-lookup"><span data-stu-id="2ed37-158">F1Score</span></span> | <span data-ttu-id="2ed37-159">MicroAccuracy</span><span class="sxs-lookup"><span data-stu-id="2ed37-159">MicroAccuracy</span></span> | <span data-ttu-id="2ed37-160">RootMeanSquaredError</span><span class="sxs-lookup"><span data-stu-id="2ed37-160">RootMeanSquaredError</span></span>
|<span data-ttu-id="2ed37-161">NegativePrecision</span><span class="sxs-lookup"><span data-stu-id="2ed37-161">NegativePrecision</span></span> | <span data-ttu-id="2ed37-162">TopKAccuracy</span><span class="sxs-lookup"><span data-stu-id="2ed37-162">TopKAccuracy</span></span>
|<span data-ttu-id="2ed37-163">NegativeRecall</span><span class="sxs-lookup"><span data-stu-id="2ed37-163">NegativeRecall</span></span> |
|<span data-ttu-id="2ed37-164">PositivePrecision</span><span class="sxs-lookup"><span data-stu-id="2ed37-164">PositivePrecision</span></span>
|<span data-ttu-id="2ed37-165">PositiveRecall</span><span class="sxs-lookup"><span data-stu-id="2ed37-165">PositiveRecall</span></span>

## <a name="data-pre-processing-and-featurization"></a><span data-ttu-id="2ed37-166">Pré-processamento de dados e personalização</span><span class="sxs-lookup"><span data-stu-id="2ed37-166">Data pre-processing and featurization</span></span>

<span data-ttu-id="2ed37-167">O pré-processamento de dados ocorre por padrão e as etapas a seguir são executadas automaticamente para você:</span><span class="sxs-lookup"><span data-stu-id="2ed37-167">Data pre-processing happens by default and the following steps are performed automatically for you:</span></span>

1. <span data-ttu-id="2ed37-168">Remover os recursos sem informações úteis</span><span class="sxs-lookup"><span data-stu-id="2ed37-168">Drop features with no useful information</span></span>

    <span data-ttu-id="2ed37-169">Remover os recursos sem informações úteis de conjuntos de treinamento e validação.</span><span class="sxs-lookup"><span data-stu-id="2ed37-169">Drop features with no useful information from training and validation sets.</span></span> <span data-ttu-id="2ed37-170">Incluem recursos com todos os valores ausentes, com o mesmo valor em todas as linhas ou com cardinalidade muito alta (por exemplo, hashes, IDs ou GUIDs).</span><span class="sxs-lookup"><span data-stu-id="2ed37-170">These include features with all values missing, same value across all rows or with extremely high cardinality (e.g., hashes, IDs or GUIDs).</span></span>

1. <span data-ttu-id="2ed37-171">Imputação e indicação de valor ausente</span><span class="sxs-lookup"><span data-stu-id="2ed37-171">Missing value indication and imputation</span></span>

    <span data-ttu-id="2ed37-172">Preencha as células de valor ausente com o valor padrão para o tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="2ed37-172">Fill missing value cells with the default value for the datatype.</span></span> <span data-ttu-id="2ed37-173">Acrescente recursos de indicador com o mesmo número de slots de que a coluna de entrada.</span><span class="sxs-lookup"><span data-stu-id="2ed37-173">Append indicator features with the same number of slots as the input column.</span></span> <span data-ttu-id="2ed37-174">O valor nos recursos de indicador acrescentados será `1` se o valor na coluna de entrada estiver ausente e `0`, caso contrário.</span><span class="sxs-lookup"><span data-stu-id="2ed37-174">The value in the appended indicator features is `1` if the value in the input column is missing and `0` otherwise.</span></span>

1. <span data-ttu-id="2ed37-175">Gerar recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="2ed37-175">Generate additional features</span></span>
    
    <span data-ttu-id="2ed37-176">Para recursos de texto: Recursos da bolsa de palavras usando unigrams e tri-character-grams.</span><span class="sxs-lookup"><span data-stu-id="2ed37-176">For text features: Bag-of-word features using unigrams and tri-character-grams.</span></span>
    
    <span data-ttu-id="2ed37-177">Para recursos categóricos: Codificação one-hot para recursos de baixa cardinalidade e codificação one-hot-hash para recursos categóricos de alta cardinalidade.</span><span class="sxs-lookup"><span data-stu-id="2ed37-177">For categorical features: One-hot encoding for low cardinality features, and one-hot-hash encoding for high cardinality categorical features.</span></span>

1. <span data-ttu-id="2ed37-178">Codificações e transformações</span><span class="sxs-lookup"><span data-stu-id="2ed37-178">Transformations and encodings</span></span>

    <span data-ttu-id="2ed37-179">Recursos de texto com poucos valores exclusivos transformados em recursos categóricos.</span><span class="sxs-lookup"><span data-stu-id="2ed37-179">Text features with very few unique values transformed into categorical features.</span></span> <span data-ttu-id="2ed37-180">Dependendo da cardinalidade de recursos categóricos, execute codificação one-hot ou codificação one-hot hash.</span><span class="sxs-lookup"><span data-stu-id="2ed37-180">Depending on cardinality of categorical features, perform one-hot encoding or one-hot hash encoding.</span></span>

## <a name="exit-criteria"></a><span data-ttu-id="2ed37-181">Critérios de saída</span><span class="sxs-lookup"><span data-stu-id="2ed37-181">Exit criteria</span></span>

<span data-ttu-id="2ed37-182">Defina os critérios para concluir sua tarefa:</span><span class="sxs-lookup"><span data-stu-id="2ed37-182">Define the criteria to complete your task:</span></span>

1. <span data-ttu-id="2ed37-183">Saída após um período – usando `MaxExperimentTimeInSeconds` em suas configurações de experimento, você pode definir quanto tempo em segundos uma tarefa deve continuar em execução.</span><span class="sxs-lookup"><span data-stu-id="2ed37-183">Exit after a length of time - Using `MaxExperimentTimeInSeconds` in your experiment settings you can define how long in seconds that an task should continue to run.</span></span>

1. <span data-ttu-id="2ed37-184">Saída em um token de cancelamento – você pode usar um token de cancelamento que permita cancelar a tarefa antes de seu término agendado.</span><span class="sxs-lookup"><span data-stu-id="2ed37-184">Exit on a cancellation token -  You can use a cancellation token that lets you cancel the task before it is scheduled to finish.</span></span>

    ```csharp
    var cts = new CancellationTokenSource();
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    experimentSettings.CancellationToken = cts.Token;
    ```

## <a name="create-an-experiment"></a><span data-ttu-id="2ed37-185">Criar um experimento</span><span class="sxs-lookup"><span data-stu-id="2ed37-185">Create an experiment</span></span>

<span data-ttu-id="2ed37-186">Depois de definir as configurações de teste, você está pronto para criar o experimento.</span><span class="sxs-lookup"><span data-stu-id="2ed37-186">Once you have configured the experiment settings, you are ready to create the experiment.</span></span>

```csharp
RegressionExperiment experiment = mlContext.Auto().CreateRegressionExperiment(experimentSettings);
```

## <a name="run-the-experiment"></a><span data-ttu-id="2ed37-187">Executar o experimento</span><span class="sxs-lookup"><span data-stu-id="2ed37-187">Run the experiment</span></span>

<span data-ttu-id="2ed37-188">Executar o experimento dispara o pré-processamento de dados, a seleção do algoritmo de aprendizado e o ajuste de hiperparâmetro.</span><span class="sxs-lookup"><span data-stu-id="2ed37-188">Running the experiment triggers data pre-processing, learning algorithm selection, and hyperparameter tuning.</span></span> <span data-ttu-id="2ed37-189">AutoML continuará a gerar combinações de personalização, algoritmos de aprendizado e hiperparâmetros até o `MaxExperimentTimeInSeconds` ser atingido ou o experimento ser encerrado.</span><span class="sxs-lookup"><span data-stu-id="2ed37-189">AutoML will continue to generate combinations of featurization, learning algorithms, and hyperparameters until the `MaxExperimentTimeInSeconds` is reached or the experiment is terminated.</span></span>

```csharp
ExperimentResult<RegressionMetrics> experimentResult = experiment
    .Execute(trainingDataView, LabelColumnName, progressHandler: progressHandler);
```

<span data-ttu-id="2ed37-190">Explore outras sobrecargas para `Execute()` se quiser passar dados de validação, informações de coluna indicando a finalidade de coluna ou pré-personalizações.</span><span class="sxs-lookup"><span data-stu-id="2ed37-190">Explore other overloads for `Execute()` if you want to pass in validation data, column information indicating the column purpose, or prefeaturizers.</span></span>

## <a name="training-modes"></a><span data-ttu-id="2ed37-191">Modos de treinamento</span><span class="sxs-lookup"><span data-stu-id="2ed37-191">Training modes</span></span>

### <a name="training-dataset"></a><span data-ttu-id="2ed37-192">Conjunto de dados de treinamento</span><span class="sxs-lookup"><span data-stu-id="2ed37-192">Training dataset</span></span>

<span data-ttu-id="2ed37-193">O AutoML oferece um método de execução de experimento sobrecarregado que possibilita que você forneça dados de treinamento.</span><span class="sxs-lookup"><span data-stu-id="2ed37-193">AutoML provides an overloaded experiment execute method which allows you to provide training data.</span></span> <span data-ttu-id="2ed37-194">Internamente, o ML automatizado divide os dados em divisões train-validate.</span><span class="sxs-lookup"><span data-stu-id="2ed37-194">Internally, automated ML divides the data into train-validate splits.</span></span>

```csharp
experiment.Execute(trainDataView);   
```

### <a name="custom-validation-dataset"></a><span data-ttu-id="2ed37-195">Conjunto de dados de validação personalizado</span><span class="sxs-lookup"><span data-stu-id="2ed37-195">Custom validation dataset</span></span>

<span data-ttu-id="2ed37-196">Use o conjunto de dados de validação personalizado se divisão aleatória não for aceitável, como normalmente é o caso para dados de série temporal.</span><span class="sxs-lookup"><span data-stu-id="2ed37-196">Use custom validation dataset if random split is not acceptable, as is usually the case with time series data.</span></span> <span data-ttu-id="2ed37-197">Você pode especificar seu próprio conjunto de dados de validação.</span><span class="sxs-lookup"><span data-stu-id="2ed37-197">You can specify your own validation dataset.</span></span> <span data-ttu-id="2ed37-198">O modelo será avaliado em relação ao conjunto de dados de validação especificado, em vez de um ou mais conjuntos de dados aleatórios.</span><span class="sxs-lookup"><span data-stu-id="2ed37-198">The model will be evaluated against the validation dataset specified instead of one or more random datasets.</span></span>

```csharp
experiment.Execute(trainDataView, validationDataView);   
```

## <a name="explore-model-metrics"></a><span data-ttu-id="2ed37-199">Explore as métricas do modelo</span><span class="sxs-lookup"><span data-stu-id="2ed37-199">Explore model metrics</span></span>

<span data-ttu-id="2ed37-200">Depois de cada iteração de um experimento de ML, as métricas relacionadas à tarefa são armazenadas.</span><span class="sxs-lookup"><span data-stu-id="2ed37-200">After each iteration of an ML experiment, metrics relating to that task are stored.</span></span>

<span data-ttu-id="2ed37-201">Por exemplo, podemos acessar as métricas de validação da melhor execução:</span><span class="sxs-lookup"><span data-stu-id="2ed37-201">For example, we can access validation metrics from the best run:</span></span>

```csharp
RegressionMetrics metrics = experimentResult.BestRun.ValidationMetrics;
Console.WriteLine($"R-Squared: {metrics.RSquared:0.##}");
Console.WriteLine($"Root Mean Squared Error: {metrics.RootMeanSquaredError:0.##}");
```

<span data-ttu-id="2ed37-202">Estas são todas as métricas disponíveis por tarefa de ML:</span><span class="sxs-lookup"><span data-stu-id="2ed37-202">The following are all the available metrics per ML task:</span></span>

* [<span data-ttu-id="2ed37-203">Métricas de classificação binária</span><span class="sxs-lookup"><span data-stu-id="2ed37-203">Binary classification metrics</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationMetric)
* [<span data-ttu-id="2ed37-204">Métricas de classificação multiclasse</span><span class="sxs-lookup"><span data-stu-id="2ed37-204">Multiclass classification metrics</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric)
* [<span data-ttu-id="2ed37-205">Métricas de regressão</span><span class="sxs-lookup"><span data-stu-id="2ed37-205">Regression metrics</span></span>](xref:Microsoft.ML.AutoML.RegressionMetric)

## <a name="see-also"></a><span data-ttu-id="2ed37-206">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ed37-206">See also</span></span>

<span data-ttu-id="2ed37-207">Para exemplos de código completos e muito mais, acesse o repositório do GitHub [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state).</span><span class="sxs-lookup"><span data-stu-id="2ed37-207">For full code samples and more visit the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) GitHub repository.</span></span>
