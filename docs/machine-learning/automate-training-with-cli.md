---
title: Automatizar o treinamento de modelos com a CLI do ML.NET
description: Descubra como usar a ferramenta de CLI do ML.NET para treinar automaticamente o melhor modelo da linha de comando.
author: natke
ms.author: nakersha
ms.date: 12/17/2019
ms.custom: how-to
ms.openlocfilehash: c7ad80d627e69df329ffe6b53de60520188347d8
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636595"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a><span data-ttu-id="1b3f7-103">Automatizar o treinamento de modelos com a CLI do ML.NET</span><span class="sxs-lookup"><span data-stu-id="1b3f7-103">Automate model training with the ML.NET CLI</span></span>

<span data-ttu-id="1b3f7-104">A CLI do ML.NET automatiza a geração de modelos para desenvolvedores .NET.</span><span class="sxs-lookup"><span data-stu-id="1b3f7-104">The ML.NET CLI automates model generation for .NET developers.</span></span>

<span data-ttu-id="1b3f7-105">Para usar a API do ML.NET por si só (sem a CLI de AutoML do ML.NET), você precisa escolher um treinador (implementação de um algoritmo de aprendizado de máquina para uma tarefa específica) e o conjunto de transformações de dados (engenharia de recursos) para aplicar aos seus dados.</span><span class="sxs-lookup"><span data-stu-id="1b3f7-105">To use the ML.NET API by itself, (without the ML.NET AutoML CLI) you need to choose a trainer (implementation of a machine learning algorithm for a particular task), and the set of data transformations (feature engineering) to apply to your data.</span></span> <span data-ttu-id="1b3f7-106">O pipeline ideal variará para cada conjunto de dados e selecionar o algoritmo ideal entre todas as opções aumenta a complexidade.</span><span class="sxs-lookup"><span data-stu-id="1b3f7-106">The optimal pipeline will vary for each dataset and selecting the optimal algorithm from all the choices adds to the complexity.</span></span> <span data-ttu-id="1b3f7-107">Além disso, cada algoritmo tem um conjunto de hiperparâmetros a serem ajustados.</span><span class="sxs-lookup"><span data-stu-id="1b3f7-107">Even further, each algorithm has a set of hyperparameters to be tuned.</span></span> <span data-ttu-id="1b3f7-108">Portanto, você pode passar semanas e até meses em otimização de modelos de machine learning na tentativa de encontrar as combinações de engenharia de recursos, algoritmos de aprendizado e hiperparâmetros.</span><span class="sxs-lookup"><span data-stu-id="1b3f7-108">Hence, you can spend weeks and sometimes months on machine learning model optimization trying to find the best combinations of feature engineering, learning algorithms, and hyperparameters.</span></span>

<span data-ttu-id="1b3f7-109">A CLI do ML.NET simplifica esse processo usando o AutoML (Machine Learning automatizado).</span><span class="sxs-lookup"><span data-stu-id="1b3f7-109">The ML.NET CLI simplifies this process using automated machine learning (AutoML).</span></span> 

> [!NOTE]
> <span data-ttu-id="1b3f7-110">Este tópico refere-se à **CLI** do ML.NET e ao **AutoML** do ML.NET, que estão atualmente em Versão Prévia. O material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="1b3f7-110">This topic refers to ML.NET **CLI** and ML.NET **AutoML**, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="what-is-the-mlnet-command-line-interface-cli"></a><span data-ttu-id="1b3f7-111">O que é a CLI (interface de linha de comando) do ML.NET?</span><span class="sxs-lookup"><span data-stu-id="1b3f7-111">What is the ML.NET Command-line Interface (CLI)?</span></span>

<span data-ttu-id="1b3f7-112">A CLI do ML.NET é uma ferramenta de dotnet global.</span><span class="sxs-lookup"><span data-stu-id="1b3f7-112">The ML.NET CLI is a dotnet global tool.</span></span> <span data-ttu-id="1b3f7-113">Depois de instalado, dê a ele uma tarefa de aprendizado de máquina e um conjunto de dado de treinamento e ele gera um modelo C# ml.net, bem como o código a ser executado para usar o modelo em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1b3f7-113">Once installed you give it a machine learning task and a training dataset, and it generates an ML.NET model, as well as the C# code to run to use the model in your application.</span></span>

<span data-ttu-id="1b3f7-114">Conforme mostrado na figura abaixo, é simples gerar um modelo de alta qualidade do ML.NET (arquivo. zip de modelo serializado) mais o código C# de exemplo para executar/pontuar esse modelo.</span><span class="sxs-lookup"><span data-stu-id="1b3f7-114">As shown in the figure below, it is simple to generate a high quality ML.NET model (serialized model .zip file) plus the sample C# code to run/score that model.</span></span> <span data-ttu-id="1b3f7-115">Além disso, o código C# para criar/treinar esse modelo também é gerado, de modo que você pode pesquisar e iterar pelo algoritmo e pelas configurações usados para esse "melhor modelo" gerado.</span><span class="sxs-lookup"><span data-stu-id="1b3f7-115">In addition, the C# code to create/train that model is also generated, so that you can research and iterate on the algorithm and settings used for that generated "best model".</span></span>

<span data-ttu-id="1b3f7-116">![image](media/automate-training-with-cli/cli-high-level-process.png "O mecanismo AutoML está trabalhando dentro da CLI do ML.NET")</span><span class="sxs-lookup"><span data-stu-id="1b3f7-116">![image](media/automate-training-with-cli/cli-high-level-process.png "AutoML engine working inside the ML.NET CLI")</span></span>

<span data-ttu-id="1b3f7-117">Você pode gerar esses ativos de seus próprios conjuntos de dados sem codificação por conta própria, portanto, ele também melhorará a sua produtividade, mesmo se você já conhecer o ML.NET.</span><span class="sxs-lookup"><span data-stu-id="1b3f7-117">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="1b3f7-118">Atualmente, as tarefas de ML compatíveis com a CLI do ML.NET são:</span><span class="sxs-lookup"><span data-stu-id="1b3f7-118">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- `binary-classification`
- `multiclass-classification`
- `regression`
- <span data-ttu-id="1b3f7-119">Futuro: outras tarefas de aprendizado de máquina, tais como `recommendation`, `ranking`, `anomaly-detection` e `clustering`</span><span class="sxs-lookup"><span data-stu-id="1b3f7-119">Future: other machine learning tasks such as `recommendation`, `ranking`, `anomaly-detection`, `clustering`</span></span>

<span data-ttu-id="1b3f7-120">Exemplo de uso:</span><span class="sxs-lookup"><span data-stu-id="1b3f7-120">Example of usage:</span></span>

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

![imagem](media/automate-training-with-cli/cli-model-generation.gif)

<span data-ttu-id="1b3f7-122">Você pode executá-los do mesmo modo que no *Windows PowerShell*, no \*bash do macOS/Linux ou no *CMD do Windows*.</span><span class="sxs-lookup"><span data-stu-id="1b3f7-122">You can run it the same way on *Windows PowerShell*, \*macOS/Linux bash, or *Windows CMD*.</span></span> <span data-ttu-id="1b3f7-123">No entanto, o preenchimento automático de tabela (sugestões de parâmetro) não funcionará no *CMD do Windows*.</span><span class="sxs-lookup"><span data-stu-id="1b3f7-123">However, tabular auto-completion (parameter suggestions) won't work on *Windows CMD*.</span></span>

## <a name="output-assets-generated"></a><span data-ttu-id="1b3f7-124">Ativos de saída gerados</span><span class="sxs-lookup"><span data-stu-id="1b3f7-124">Output assets generated</span></span>

<span data-ttu-id="1b3f7-125">O comando `auto-train` da CLI gera os seguintes ativos na pasta de saída:</span><span class="sxs-lookup"><span data-stu-id="1b3f7-125">The CLI `auto-train` command generates the following assets in the output folder:</span></span>

- <span data-ttu-id="1b3f7-126">Um modelo .zip serializado ("melhor modelo") pronto para uso voltado à execução de previsões.</span><span class="sxs-lookup"><span data-stu-id="1b3f7-126">A serialized model .zip ("best model") ready to use for running predictions.</span></span>
- <span data-ttu-id="1b3f7-127">Solução em C# com:</span><span class="sxs-lookup"><span data-stu-id="1b3f7-127">C# solution with:</span></span>
  - <span data-ttu-id="1b3f7-128">Código C# para a execução/pontuação que gerou o modelo (para fazer previsões em seus aplicativos do usuário final com esse modelo).</span><span class="sxs-lookup"><span data-stu-id="1b3f7-128">C# code to run/score that generated model (to make predictions in your end-user apps with that model).</span></span>
  - <span data-ttu-id="1b3f7-129">Código C# com o código de treinamento usado para gerar esse modelo (para fins de aprendizado ou retreinamento de modelo).</span><span class="sxs-lookup"><span data-stu-id="1b3f7-129">C# code with the training code used to generate that model (for learning purposes or model retraining).</span></span>
- <span data-ttu-id="1b3f7-130">Arquivo de log com informações de todas as iterações/varreduras entre vários algoritmos avaliados, incluindo sua configuração/pipeline detalhado.</span><span class="sxs-lookup"><span data-stu-id="1b3f7-130">Log file with information of all iterations/sweeps across the multiple algorithms evaluated, including their detailed configuration/pipeline.</span></span>

<span data-ttu-id="1b3f7-131">Os primeiros dois ativos podem ser usados diretamente em seus aplicativos de usuário final (aplicativo Web ASP.NET Core, serviços, aplicativo da área de trabalho etc.) para fazer previsões com esse modelo de ML gerado.</span><span class="sxs-lookup"><span data-stu-id="1b3f7-131">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="1b3f7-132">O terceiro ativo, o código de treinamento, mostra a você qual código de API do ML.NET foi usado pela CLI para treinar o modelo gerado, de modo que você pode treinar novamente seu modelo e investigar e iterar em quais hiperparâmetros e treinador/algoritmo específicos foram selecionados pela CLI e AutoML nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="1b3f7-132">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can retrain your model and investigate and iterate on which specific trainer/algorithm and hyperparameters were selected by the CLI and AutoML under the covers.</span></span>

## <a name="understanding-the-quality-of-the-model"></a><span data-ttu-id="1b3f7-133">Noções básicas sobre a qualidade do modelo</span><span class="sxs-lookup"><span data-stu-id="1b3f7-133">Understanding the quality of the model</span></span>

<span data-ttu-id="1b3f7-134">Quando você gera um "melhor modelo" com a ferramenta da CLI, você vê métricas de qualidade (tais como precisão e R-quadrado) conforme apropriado para a tarefa de ML que você está usando como destino.</span><span class="sxs-lookup"><span data-stu-id="1b3f7-134">When you generate a 'best model' with the CLI tool, you see quality metrics (such as accuracy, and R-Squared) as appropriate for the ML task you are targeting.</span></span>

<span data-ttu-id="1b3f7-135">Aqui, resumiremos essas métricas agrupadas pela tarefa de ML para que você possa entender a qualidade do seu "melhor modelo" gerado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="1b3f7-135">Here we summarize those metrics grouped by ML task so you can understand the quality of your auto-generated 'best model'.</span></span>

### <a name="metrics-for-binary-classification-models"></a><span data-ttu-id="1b3f7-136">Métricas para modelos de classificação binária</span><span class="sxs-lookup"><span data-stu-id="1b3f7-136">Metrics for Binary Classification models</span></span>

<span data-ttu-id="1b3f7-137">A seguir, é exibida a lista de métricas de tarefas de classificação binária de ML para os cinco principais modelos encontrados pela CLI:</span><span class="sxs-lookup"><span data-stu-id="1b3f7-137">The following displays the binary classification ML task metrics list for the top five models found by the CLI:</span></span>

![imagem](media/automate-training-with-cli/cli-binary-classification-metrics.png)

<span data-ttu-id="1b3f7-139">A precisão é uma métrica popular para problemas de classificação, mas precisão nem sempre é a melhor métrica para selecionar o melhor modelo, conforme explicado nas referências abaixo.</span><span class="sxs-lookup"><span data-stu-id="1b3f7-139">Accuracy is a popular metric for classification problems, however accuracy is not always the best metric to select the best model from as explained in the references below.</span></span> <span data-ttu-id="1b3f7-140">Há casos em que você precisa avaliar a qualidade do seu modelo com métricas adicionais.</span><span class="sxs-lookup"><span data-stu-id="1b3f7-140">There are cases where you need to evaluate the quality of your model with additional metrics.</span></span>

<span data-ttu-id="1b3f7-141">Para explorar e entender as métricas que são geradas pela CLI, consulte [métricas de avaliação para classificação binária](resources/metrics.md#evaluation-metrics-for-binary-classification).</span><span class="sxs-lookup"><span data-stu-id="1b3f7-141">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for binary classification](resources/metrics.md#evaluation-metrics-for-binary-classification).</span></span>

### <a name="metrics-for-multi-class-classification-models"></a><span data-ttu-id="1b3f7-142">Métricas para modelos de classificação multiclasse</span><span class="sxs-lookup"><span data-stu-id="1b3f7-142">Metrics for Multi-class Classification models</span></span>

<span data-ttu-id="1b3f7-143">A seguir é exibida a lista de métricas de tarefas de ML de classificação multiclasse para os cinco principais modelos encontrados pela CLI:</span><span class="sxs-lookup"><span data-stu-id="1b3f7-143">The following displays the multi-class classification ML task metrics list for the top five models found by the CLI:</span></span>

![imagem](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

<span data-ttu-id="1b3f7-145">Para explorar e entender as métricas que são geradas pela CLI, consulte [métricas de avaliação para classificação multiclasse](resources/metrics.md#evaluation-metrics-for-multi-class-classification).</span><span class="sxs-lookup"><span data-stu-id="1b3f7-145">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for multiclass classification](resources/metrics.md#evaluation-metrics-for-multi-class-classification).</span></span>

### <a name="metrics-for-regression-and-recommendation-models"></a><span data-ttu-id="1b3f7-146">Métricas para modelos de regressão e recomendação</span><span class="sxs-lookup"><span data-stu-id="1b3f7-146">Metrics for Regression and Recommendation models</span></span>

<span data-ttu-id="1b3f7-147">Um modelo de regressão se ajustará bem aos dados se as diferenças entre os valores observados e os previstos do modelo forem pequenas e sem desvio.</span><span class="sxs-lookup"><span data-stu-id="1b3f7-147">A regression model fits the data well if the differences between the observed values and the model's predicted values are small and unbiased.</span></span> <span data-ttu-id="1b3f7-148">A regressão pode ser avaliada com certas métricas.</span><span class="sxs-lookup"><span data-stu-id="1b3f7-148">Regression can be evaluated with certain metrics.</span></span>

<span data-ttu-id="1b3f7-149">Você verá uma lista semelhante de métricas para os cinco modelos com melhor qualidade encontrados pela CLI.</span><span class="sxs-lookup"><span data-stu-id="1b3f7-149">You will see a similar list of metrics for the best top five quality models found by the CLI.</span></span> <span data-ttu-id="1b3f7-150">Neste caso em particular, relacionados a uma tarefa de ML de regressão:</span><span class="sxs-lookup"><span data-stu-id="1b3f7-150">In this particular case related to a regression ML task:</span></span>

![imagem](media/automate-training-with-cli/cli-regression-metrics.png)

<span data-ttu-id="1b3f7-152">Para explorar e entender as métricas que são geradas pela CLI, consulte [métricas de avaliação para regressão](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).</span><span class="sxs-lookup"><span data-stu-id="1b3f7-152">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for regression](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).</span></span>

## <a name="see-also"></a><span data-ttu-id="1b3f7-153">Veja também</span><span class="sxs-lookup"><span data-stu-id="1b3f7-153">See also</span></span>

- [<span data-ttu-id="1b3f7-154">Como instalar a ferramenta de CLI do ML.NET</span><span class="sxs-lookup"><span data-stu-id="1b3f7-154">How to install the ML.NET CLI tool</span></span>](how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="1b3f7-155">Tutorial: analisar o sentimentos usando a CLI do ML.NET</span><span class="sxs-lookup"><span data-stu-id="1b3f7-155">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="1b3f7-156">Referência de comandos da CLI do ML.NET</span><span class="sxs-lookup"><span data-stu-id="1b3f7-156">ML.NET CLI command reference</span></span>](reference/ml-net-cli-reference.md)
- [<span data-ttu-id="1b3f7-157">Telemetria na CLI do ML.NET</span><span class="sxs-lookup"><span data-stu-id="1b3f7-157">Telemetry in ML.NET CLI</span></span>](resources/ml-net-cli-telemetry.md)
