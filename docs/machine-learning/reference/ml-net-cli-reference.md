---
title: Referência de comando da CLI ML.NET
description: Visão geral, exemplos e referência para o comando de treinamento automático na ferramenta de CLI do ML.NET.
ms.date: 06/03/2020
ms.custom: mlnet-tooling
ms.openlocfilehash: 397f6fda8554024624b3ef630856dc8eca9696b2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594537"
---
# <a name="the-mlnet-cli-command-reference"></a><span data-ttu-id="d5ca3-103">A referência de comando da CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="d5ca3-103">The ML.NET CLI command reference</span></span>

<span data-ttu-id="d5ca3-104">Os `classification` `regression` comandos, e `recommendation` são os principais comandos fornecidos pela ferramenta CLI do ml.net.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-104">The `classification`, `regression`, and `recommendation` commands are the main commands provided by the ML.NET CLI tool.</span></span> <span data-ttu-id="d5ca3-105">Esses comandos permitem que você gere bons modelos de ML.NET de qualidade para classificação, regressão e modelos de recomendação usando o AutoML (Machine Learning automatizado), bem como o código C# de exemplo para executar/pontuar esse modelo.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-105">These commands allow you to generate good quality ML.NET models for classification, regression, and recommendation models using automated machine learning (AutoML) as well as the example C# code to run/score that model.</span></span> <span data-ttu-id="d5ca3-106">Além disso, o código C# para treinar o modelo é gerado para você pesquisar o algoritmo e as configurações do modelo.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-106">In addition, the C# code to train the model is generated for you to research the algorithm and settings of the model.</span></span>

> [!NOTE]
> <span data-ttu-id="d5ca3-107">Este tópico refere-se à CLI do ML.NET e ao AutoML do ML.NET, que estão atualmente em Versão Prévia. O material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-107">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="overview"></a><span data-ttu-id="d5ca3-108">Visão geral</span><span class="sxs-lookup"><span data-stu-id="d5ca3-108">Overview</span></span>

<span data-ttu-id="d5ca3-109">Exemplo de uso:</span><span class="sxs-lookup"><span data-stu-id="d5ca3-109">Example usage:</span></span>

```console
mlnet regression --dataset "cars.csv" --label-col price
```

<span data-ttu-id="d5ca3-110">Os `mlnet` comandos de tarefa ml ( `classification` , `regression` e `recommendation` ) geram os seguintes ativos:</span><span class="sxs-lookup"><span data-stu-id="d5ca3-110">The `mlnet` ML task commands (`classification`, `regression`, and `recommendation`) generate the following assets:</span></span>

- <span data-ttu-id="d5ca3-111">Um modelo serializado. zip ("melhor modelo") pronto para uso.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-111">A serialized model .zip ("best model") ready to use.</span></span>
- <span data-ttu-id="d5ca3-112">Código C# para executar/pontuar o modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-112">C# code to run/score that generated model.</span></span>
- <span data-ttu-id="d5ca3-113">Código C# com o código de treinamento usado para gerar esse modelo.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-113">C# code with the training code used to generate that model.</span></span>

<span data-ttu-id="d5ca3-114">Os dois primeiros ativos podem ser usados diretamente em seus aplicativos de usuário final (ASP.NET Core aplicativo Web, serviços, aplicativo de área de trabalho e muito mais) para fazer previsões com o modelo.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-114">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app and more) to make predictions with the model.</span></span>

<span data-ttu-id="d5ca3-115">O terceiro ativo, o código de treinamento, mostra o que o código da API ML.NET foi usado pela CLI para treinar o modelo gerado, para que você possa investigar o algoritmo e as configurações específicas do modelo.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-115">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate the specific algorithm and settings of the model.</span></span>

## <a name="examples"></a><span data-ttu-id="d5ca3-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="d5ca3-116">Examples</span></span>

<span data-ttu-id="d5ca3-117">O comando da CLI mais simples para um problema de classificação (AutoML infere a maior parte da configuração dos dados fornecidos):</span><span class="sxs-lookup"><span data-stu-id="d5ca3-117">The simplest CLI command for a classification problem (AutoML infers most of the configuration from the provided data):</span></span>

```console
mlnet classification --dataset "customer-feedback.tsv" --label-col Sentiment
```

<span data-ttu-id="d5ca3-118">Outro comando simples da CLI para um problema de regressão:</span><span class="sxs-lookup"><span data-stu-id="d5ca3-118">Another simple CLI command for a regression problem:</span></span>

``` console
mlnet regression --dataset "cars.csv" --label-col Price
```

<span data-ttu-id="d5ca3-119">Crie e treine um modelo de classificação com um conjunto de informações de treinamento, um conjunto de testes e mais argumentos explícitos de personalização:</span><span class="sxs-lookup"><span data-stu-id="d5ca3-119">Create and train a classification model with a train dataset, a test dataset, and further customization explicit arguments:</span></span>

```console
mlnet classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-col "InsuranceRisk" --cache on --train-time 600
```

## <a name="command-options"></a><span data-ttu-id="d5ca3-120">Opções de comando</span><span class="sxs-lookup"><span data-stu-id="d5ca3-120">Command options</span></span>

<span data-ttu-id="d5ca3-121">Os `mlnet` comandos de tarefa ml ( `classification` , `regression` , e `recommendation` ) treinam vários modelos com base nas opções de conjunto de ml.net e CLI fornecidas.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-121">The `mlnet` ML task commands (`classification`, `regression`, and `recommendation`) train multiple models based on the provided dataset and ML.NET CLI options.</span></span> <span data-ttu-id="d5ca3-122">Esses comandos também selecionam o melhor modelo, salvam o modelo como um arquivo. zip serializado e geram código C# relacionado para pontuação e treinamento.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-122">These commands also select the best model, save the model as a serialized .zip file, and generate related C# code for scoring and training.</span></span>

### <a name="classification-options"></a><span data-ttu-id="d5ca3-123">Opções de classificação</span><span class="sxs-lookup"><span data-stu-id="d5ca3-123">Classification options</span></span>

<span data-ttu-id="d5ca3-124">`mlnet classification`A execução treinará um modelo de classificação.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-124">Running `mlnet classification` will train a classification model.</span></span> <span data-ttu-id="d5ca3-125">Escolha este comando se desejar que um modelo de ML categorize dados em duas ou mais classes (por exemplo, análise de sentimentos).</span><span class="sxs-lookup"><span data-stu-id="d5ca3-125">Choose this command if you want an ML Model to categorize data into 2 or more classes (e.g. sentiment analysis).</span></span>

```console
mlnet classification

--dataset <path> (REQUIRED)

--label-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--ignore-cols <cols>

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

### <a name="regression-options"></a><span data-ttu-id="d5ca3-126">Opções de regressão</span><span class="sxs-lookup"><span data-stu-id="d5ca3-126">Regression options</span></span>

<span data-ttu-id="d5ca3-127">`mlnet regression`A execução treinará um modelo de regressão.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-127">Running `mlnet regression` will train a regression model.</span></span> <span data-ttu-id="d5ca3-128">Escolha este comando se desejar que um modelo de ML preveja um valor numérico (por exemplo, previsão de preço).</span><span class="sxs-lookup"><span data-stu-id="d5ca3-128">Choose this command if you want an ML Model to predict a numeric value (e.g. price prediction).</span></span>

```console
mlnet classification

--dataset <path> (REQUIRED)

--label-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--ignore-cols <cols>

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

### <a name="recommendation-options"></a><span data-ttu-id="d5ca3-129">Opções de recomendação</span><span class="sxs-lookup"><span data-stu-id="d5ca3-129">Recommendation options</span></span>

<span data-ttu-id="d5ca3-130">`mlnet recommendation`A execução treinará um modelo de recomendação.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-130">Running `mlnet recommendation` will train a recommendation model.</span></span>  <span data-ttu-id="d5ca3-131">Escolha este comando se desejar que um modelo de ML recomende itens aos usuários com base em classificações (por exemplo, recomendação de produto).</span><span class="sxs-lookup"><span data-stu-id="d5ca3-131">Choose this command if you want an ML Model to recommend items to users based on ratings (e.g. product recommendation).</span></span>

```console
mlnet classification

--dataset <path> (REQUIRED)

--item-col <col> (REQUIRED)

--rating-col <col> (REQUIRED)

--user-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

<span data-ttu-id="d5ca3-132">As opções de entrada inválidas fazem com que a ferramenta CLI emita uma lista de entradas válidas e uma mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-132">Invalid input options cause the CLI tool to emit a list of valid inputs and an error message.</span></span>

## <a name="dataset"></a><span data-ttu-id="d5ca3-133">Dataset</span><span class="sxs-lookup"><span data-stu-id="d5ca3-133">Dataset</span></span>

<span data-ttu-id="d5ca3-134">`--dataset | -d` (string)</span><span class="sxs-lookup"><span data-stu-id="d5ca3-134">`--dataset | -d` (string)</span></span>

<span data-ttu-id="d5ca3-135">Esse argumento fornece o caminho do arquivo para uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="d5ca3-135">This argument provides the filepath to either one of the following options:</span></span>

- <span data-ttu-id="d5ca3-136">*R: todo o arquivo do conjunto de arquivos:* Se você estiver usando essa opção e o usuário não estiver fornecendo `--test-dataset` e `--validation-dataset` , em seguida, a validação cruzada (k-fold, etc.) ou abordagens de divisão de dados automatizadas serão usadas internamente para validar o modelo.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-136">*A: The whole dataset file:* If using this option and the user is not providing `--test-dataset` and `--validation-dataset`, then cross-validation (k-fold, etc.) or automated data split approaches will be used internally for validating the model.</span></span> <span data-ttu-id="d5ca3-137">Nesse caso, o usuário precisará apenas fornecer o caminho do arquivo do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-137">In that case, the user will just need to provide the dataset filepath.</span></span>

- <span data-ttu-id="d5ca3-138">*B: o arquivo do conjunto de arquivos de treinamento:* Se o usuário também estiver fornecendo conjuntos de valores para validação de modelo (usando `--test-dataset` e, opcionalmente `--validation-dataset` ), o `--dataset` argumento significará ter apenas o "conjunto de linhas de treinamento".</span><span class="sxs-lookup"><span data-stu-id="d5ca3-138">*B: The training dataset file:* If the user is also providing datasets for model validation (using `--test-dataset` and optionally `--validation-dataset`), then the `--dataset` argument means to only have the "training dataset".</span></span> <span data-ttu-id="d5ca3-139">Por exemplo, ao usar uma abordagem de 80-20% para validar a qualidade do modelo e obter métricas de precisão, o "conjunto de dados treinamento" terá 80% dos dados e o "conjunto de dados de teste" terá 20% dos dados.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-139">For example, when using an 80% - 20% approach to validate the quality of the model and to obtain accuracy metrics, the "training dataset" will have 80% of the data and the "test dataset" would have 20% of the data.</span></span>

## <a name="test-dataset"></a><span data-ttu-id="d5ca3-140">Conjunto de dados de teste</span><span class="sxs-lookup"><span data-stu-id="d5ca3-140">Test dataset</span></span>

<span data-ttu-id="d5ca3-141">`--test-dataset | -t` (string)</span><span class="sxs-lookup"><span data-stu-id="d5ca3-141">`--test-dataset | -t` (string)</span></span>

<span data-ttu-id="d5ca3-142">Caminho do arquivo que aponta para o arquivo de conjunto de dados de teste, por exemplo, ao usar uma abordagem de 80-20% ao realizar validações regulares para obter métricas de precisão.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-142">File path pointing to the test dataset file, for example when using an 80% - 20% approach when making regular validations to obtain accuracy metrics.</span></span>

<span data-ttu-id="d5ca3-143">Ao usar `--test-dataset`, `--dataset` também é necessária.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-143">If using `--test-dataset`, then `--dataset` is also required.</span></span>

<span data-ttu-id="d5ca3-144">O argumento `--test-dataset` é opcional, a menos que o --validation-dataset seja usado.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-144">The `--test-dataset` argument is optional unless the --validation-dataset is used.</span></span> <span data-ttu-id="d5ca3-145">Nesse caso, o usuário precisa usar os três argumentos.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-145">In that case, the user must use the three arguments.</span></span>

## <a name="validation-dataset"></a><span data-ttu-id="d5ca3-146">Conjunto de dados de validação</span><span class="sxs-lookup"><span data-stu-id="d5ca3-146">Validation dataset</span></span>

<span data-ttu-id="d5ca3-147">`--validation-dataset | -v` (string)</span><span class="sxs-lookup"><span data-stu-id="d5ca3-147">`--validation-dataset | -v` (string)</span></span>

<span data-ttu-id="d5ca3-148">Caminho do arquivo apontando para o arquivo de conjunto de dados de validação.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-148">File path pointing to the validation dataset file.</span></span> <span data-ttu-id="d5ca3-149">O conjunto de dados de validação é opcional em qualquer caso.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-149">The validation dataset is optional, in any case.</span></span>

<span data-ttu-id="d5ca3-150">Se usar um `validation dataset`, o comportamento deverá ser:</span><span class="sxs-lookup"><span data-stu-id="d5ca3-150">If using a `validation dataset`, the behavior should be:</span></span>

- <span data-ttu-id="d5ca3-151">Os argumentos `test-dataset` e `--dataset` também são necessários.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-151">The `test-dataset` and `--dataset` arguments are also required.</span></span>

- <span data-ttu-id="d5ca3-152">O conjunto de dados `validation-dataset` é usado para estimar o erro de previsão para a seleção de modelo.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-152">The `validation-dataset` dataset is used to estimate prediction error for model selection.</span></span>

- <span data-ttu-id="d5ca3-153">O `test-dataset` é usado para a avaliação do erro de generalização do modelo final escolhido.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-153">The `test-dataset` is used for assessment of the generalization error of the final chosen model.</span></span> <span data-ttu-id="d5ca3-154">O ideal é que o conjunto de teste seja mantido em um "cofre" e seja levado somente no final da análise de dados.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-154">Ideally, the test set should be kept in a “vault,” and be brought out only at the end of the data analysis.</span></span>

<span data-ttu-id="d5ca3-155">Basicamente, ao usar um `validation dataset` mais o `test dataset`, a fase de validação é dividida em duas partes:</span><span class="sxs-lookup"><span data-stu-id="d5ca3-155">Basically, when using a `validation dataset` plus the `test dataset`, the validation phase is split into two parts:</span></span>

1. <span data-ttu-id="d5ca3-156">Na primeira parte, você apenas examina seus modelos e seleciona a abordagem com melhor desempenho usando os dados de validação (=validation)</span><span class="sxs-lookup"><span data-stu-id="d5ca3-156">In the first part, you just look at your models and select the best performing approach using the validation data (=validation)</span></span>
2. <span data-ttu-id="d5ca3-157">Em seguida, você pode estimar a precisão da abordagem selecionada (=test).</span><span class="sxs-lookup"><span data-stu-id="d5ca3-157">Then you estimate the accuracy of the selected approach (=test).</span></span>

<span data-ttu-id="d5ca3-158">Portanto, a separação dos dados pode ser 80/10/10 ou 75/15/10.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-158">Hence, the separation of data could be 80/10/10 or 75/15/10.</span></span> <span data-ttu-id="d5ca3-159">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="d5ca3-159">For example:</span></span>

- <span data-ttu-id="d5ca3-160">O arquivo `training-dataset` deve ter 75% dos dados.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-160">`training-dataset` file should have 75% of the data.</span></span>
- <span data-ttu-id="d5ca3-161">O arquivo `validation-dataset` deve ter 15% dos dados.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-161">`validation-dataset` file should have 15% of the data.</span></span>
- <span data-ttu-id="d5ca3-162">O arquivo `test-dataset` deve ter 10% dos dados.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-162">`test-dataset` file should have 10% of the data.</span></span>

<span data-ttu-id="d5ca3-163">Em qualquer caso, essas porcentagens serão decididas pelo usuário usando a CLI que fornecerá os arquivos já dividido.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-163">In any case, those percentages will be decided by the user using the CLI who will provide the files already split.</span></span>

## <a name="label-column"></a><span data-ttu-id="d5ca3-164">Coluna de rótulo</span><span class="sxs-lookup"><span data-stu-id="d5ca3-164">Label column</span></span>

<span data-ttu-id="d5ca3-165">`--label-col`(int ou String)</span><span class="sxs-lookup"><span data-stu-id="d5ca3-165">`--label-col` (int or string)</span></span>

<span data-ttu-id="d5ca3-166">Com esse argumento, uma coluna de objetivo/destino específica (a variável que você deseja prever) pode ser especificada usando o nome da coluna definido no cabeçalho do conjunto de informações ou no índice numérico da coluna no arquivo do conjunto de informações (os valores de índice da coluna começam em 0).</span><span class="sxs-lookup"><span data-stu-id="d5ca3-166">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="d5ca3-167">Esse argumento é usado para problemas de *classificação* e *regressão* .</span><span class="sxs-lookup"><span data-stu-id="d5ca3-167">This argument is used for *classification* and *regression* problems.</span></span>

## <a name="item-column"></a><span data-ttu-id="d5ca3-168">Coluna do item</span><span class="sxs-lookup"><span data-stu-id="d5ca3-168">Item column</span></span>

<span data-ttu-id="d5ca3-169">`--item-col`(int ou String)</span><span class="sxs-lookup"><span data-stu-id="d5ca3-169">`--item-col` (int or string)</span></span>

<span data-ttu-id="d5ca3-170">A coluna item tem a lista de itens que os usuários avaliam (itens são recomendados para os usuários).</span><span class="sxs-lookup"><span data-stu-id="d5ca3-170">The item column has the list of items that users rate (items are recommended to users).</span></span> <span data-ttu-id="d5ca3-171">Essa coluna pode ser especificada usando-se o nome da coluna definido no cabeçalho do conjunto de valores ou no índice numérico da coluna no arquivo do conjunto de arquivos (o valor do índice da coluna começa em 0).</span><span class="sxs-lookup"><span data-stu-id="d5ca3-171">This column can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="d5ca3-172">Esse argumento é usado somente para a tarefa de *recomendação* .</span><span class="sxs-lookup"><span data-stu-id="d5ca3-172">This argument is used only for the *recommendation* task.</span></span>

## <a name="rating-column"></a><span data-ttu-id="d5ca3-173">Coluna de classificação</span><span class="sxs-lookup"><span data-stu-id="d5ca3-173">Rating column</span></span>

<span data-ttu-id="d5ca3-174">`--rating-col`(int ou String)</span><span class="sxs-lookup"><span data-stu-id="d5ca3-174">`--rating-col` (int or string)</span></span>

<span data-ttu-id="d5ca3-175">A coluna classificação tem a lista de classificações que são dadas aos itens pelos usuários.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-175">The rating column has the list of ratings that are given to items by users.</span></span> <span data-ttu-id="d5ca3-176">Essa coluna pode ser especificada usando-se o nome da coluna definido no cabeçalho do conjunto de valores ou no índice numérico da coluna no arquivo do conjunto de arquivos (o valor do índice da coluna começa em 0).</span><span class="sxs-lookup"><span data-stu-id="d5ca3-176">This column can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="d5ca3-177">Esse argumento é usado somente para a tarefa de *recomendação* .</span><span class="sxs-lookup"><span data-stu-id="d5ca3-177">This argument is used only for the *recommendation* task.</span></span>

## <a name="user-column"></a><span data-ttu-id="d5ca3-178">Coluna do usuário</span><span class="sxs-lookup"><span data-stu-id="d5ca3-178">User column</span></span>

<span data-ttu-id="d5ca3-179">`--user-col`(int ou String)</span><span class="sxs-lookup"><span data-stu-id="d5ca3-179">`--user-col` (int or string)</span></span>

<span data-ttu-id="d5ca3-180">A coluna usuário tem a lista de usuários que fornecem classificações aos itens.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-180">The user column has the list of users that give ratings to items.</span></span> <span data-ttu-id="d5ca3-181">Essa coluna pode ser especificada usando-se o nome da coluna definido no cabeçalho do conjunto de valores ou no índice numérico da coluna no arquivo do conjunto de arquivos (o valor do índice da coluna começa em 0).</span><span class="sxs-lookup"><span data-stu-id="d5ca3-181">This column can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="d5ca3-182">Esse argumento é usado somente para a tarefa de *recomendação* .</span><span class="sxs-lookup"><span data-stu-id="d5ca3-182">This argument is used only for the *recommendation* task.</span></span>

## <a name="ignore-columns"></a><span data-ttu-id="d5ca3-183">Ignorar colunas</span><span class="sxs-lookup"><span data-stu-id="d5ca3-183">Ignore columns</span></span>

<span data-ttu-id="d5ca3-184">`--ignore-columns` (string)</span><span class="sxs-lookup"><span data-stu-id="d5ca3-184">`--ignore-columns` (string)</span></span>

<span data-ttu-id="d5ca3-185">Com este argumento, você pode ignorar as colunas existentes no arquivo de conjunto de dados para que elas não sejam carregadas e usadas pelos processos de treinamento.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-185">With this argument, you can ignore existing columns in the dataset file so they are not loaded and used by the training processes.</span></span>

<span data-ttu-id="d5ca3-186">Especifique os nomes de colunas que você deseja ignorar.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-186">Specify the columns names that you want to ignore.</span></span> <span data-ttu-id="d5ca3-187">Use ',' (vírgula com espaço) ou ' ' (espaço) para separar vários nomes de coluna.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-187">Use ', ' (comma with space) or ' ' (space) to separate multiple column names.</span></span> <span data-ttu-id="d5ca3-188">Você pode usar aspas para nomes de coluna que contêm espaço em branco (por exemplo, "usuário logado").</span><span class="sxs-lookup"><span data-stu-id="d5ca3-188">You can use quotes for column names containing whitespace (e.g. "logged in").</span></span>

<span data-ttu-id="d5ca3-189">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="d5ca3-189">Example:</span></span>

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a><span data-ttu-id="d5ca3-190">Tem cabeçalho</span><span class="sxs-lookup"><span data-stu-id="d5ca3-190">Has header</span></span>

<span data-ttu-id="d5ca3-191">`--has-header` (bool)</span><span class="sxs-lookup"><span data-stu-id="d5ca3-191">`--has-header` (bool)</span></span>

<span data-ttu-id="d5ca3-192">Especifique se os arquivos de conjunto de dados têm uma linha de cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-192">Specify if the dataset file(s) have a header row.</span></span>
<span data-ttu-id="d5ca3-193">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="d5ca3-193">Possible values are:</span></span>

- `true`
- `false`

<span data-ttu-id="d5ca3-194">A CLI do ML.NET tentará detectar essa propriedade se esse argumento não for especificado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-194">The ML.NET CLI will try to detect this property if this argument is not specified by the user.</span></span>

## <a name="train-time"></a><span data-ttu-id="d5ca3-195">Tempo de treinamento</span><span class="sxs-lookup"><span data-stu-id="d5ca3-195">Train time</span></span>

<span data-ttu-id="d5ca3-196">`--train-time` (string)</span><span class="sxs-lookup"><span data-stu-id="d5ca3-196">`--train-time` (string)</span></span>

<span data-ttu-id="d5ca3-197">Por padrão, o tempo máximo de exploração/treinamento é de 30 minutos.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-197">By default, the maximum exploration / train time is 30 minutes.</span></span>

<span data-ttu-id="d5ca3-198">Esse argumento define o tempo máximo (em segundos) para o processo explorar vários treinadores e configurações.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-198">This argument sets the maximum time (in seconds) for the process to explore multiple trainers and configurations.</span></span> <span data-ttu-id="d5ca3-199">O tempo configurado poderá ser excedido se o tempo fornecido for muito curto (digamos, dois segundos) para uma única iteração.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-199">The configured time may be exceeded if the provided time is too short (say 2 seconds) for a single iteration.</span></span> <span data-ttu-id="d5ca3-200">Nesse caso, o tempo real é o tempo necessário para produzir uma configuração de modelo em uma única iteração.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-200">In this case, the actual time is the required time to produce one model configuration in a single iteration.</span></span>

<span data-ttu-id="d5ca3-201">O tempo necessário para iterações pode variar, dependendo do tamanho do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-201">The needed time for iterations can vary depending on the size of the dataset.</span></span>

## <a name="cache"></a><span data-ttu-id="d5ca3-202">Cache</span><span class="sxs-lookup"><span data-stu-id="d5ca3-202">Cache</span></span>

<span data-ttu-id="d5ca3-203">`--cache` (string)</span><span class="sxs-lookup"><span data-stu-id="d5ca3-203">`--cache` (string)</span></span>

<span data-ttu-id="d5ca3-204">Se você usar o armazenamento em cache, o conjunto de dados de treinamento inteiro será carregado na memória.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-204">If you use caching, the whole training dataset will be loaded in-memory.</span></span>

<span data-ttu-id="d5ca3-205">Para conjuntos de dados pequenos e médios, usar o cache pode melhorar drasticamente o desempenho de treinamento, o que significa que o tempo de treinamento pode ser menor do que quando você não usa o cache.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-205">For small and medium datasets, using cache can drastically improve the training performance, meaning the training time can be shorter than when you don't use cache.</span></span>

<span data-ttu-id="d5ca3-206">No entanto, para grandes conjuntos de dados, carregar todos os dados na memória pode ter um efeito negativo, pois você poderá ficar com memória insuficiente.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-206">However, for large datasets, loading all the data in memory can impact negatively since you might get out of memory.</span></span> <span data-ttu-id="d5ca3-207">Ao treinar com arquivos de conjunto de dados grandes sem usar o cache, o ML.NET transmitirá partes de dados da unidade quando ele precisar carregar mais dados durante o treinamento.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-207">When training with large dataset files and not using cache, ML.NET will be streaming chunks of data from the drive when it needs to load more data while training.</span></span>

<span data-ttu-id="d5ca3-208">É possível especificar os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="d5ca3-208">You can specify the following values:</span></span>

<span data-ttu-id="d5ca3-209">`on`: Força o cache a ser usado durante o treinamento.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-209">`on`: Forces cache to be used when training.</span></span>
<span data-ttu-id="d5ca3-210">`off`: Força o cache a não ser usado durante o treinamento.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-210">`off`: Forces cache not to be used when training.</span></span>
<span data-ttu-id="d5ca3-211">`auto`: Dependendo da heurística do AutoML, o cache será usado ou não.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-211">`auto`: Depending on AutoML heuristics, the cache will be used or not.</span></span> <span data-ttu-id="d5ca3-212">Em geral, conjuntos de dados pequenos/médios usarão o cache e grandes conjuntos de dados não usarão o cache se você usar a escolha `auto`.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-212">Usually, small/medium datasets will use cache and large datasets won't use cache if you use the `auto` choice.</span></span>

<span data-ttu-id="d5ca3-213">Se você não especificar o parâmetro `--cache`, a configuração de cache `auto` será usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-213">If you don't specify the `--cache` parameter, then the cache `auto` configuration will be used by default.</span></span>

## <a name="name"></a><span data-ttu-id="d5ca3-214">Nome</span><span class="sxs-lookup"><span data-stu-id="d5ca3-214">Name</span></span>

<span data-ttu-id="d5ca3-215">`--name` (string)</span><span class="sxs-lookup"><span data-stu-id="d5ca3-215">`--name` (string)</span></span>

<span data-ttu-id="d5ca3-216">O nome para a solução ou projeto de saída criado.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-216">The name for the created output project or solution.</span></span> <span data-ttu-id="d5ca3-217">Se nenhum nome for especificado, o nome `sample-{mltask}` será usado.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-217">If no name is specified, the name `sample-{mltask}` is used.</span></span>

<span data-ttu-id="d5ca3-218">O arquivo de modelo do ML.NET (arquivo zip) também receberá o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-218">The ML.NET model file (.ZIP file) will get the same name, as well.</span></span>

## <a name="output-path"></a><span data-ttu-id="d5ca3-219">Caminho de saída</span><span class="sxs-lookup"><span data-stu-id="d5ca3-219">Output path</span></span>

<span data-ttu-id="d5ca3-220">`--output-path | -o` (string)</span><span class="sxs-lookup"><span data-stu-id="d5ca3-220">`--output-path | -o` (string)</span></span>

<span data-ttu-id="d5ca3-221">Local/pasta raiz para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-221">Root location/folder to place the generated output.</span></span> <span data-ttu-id="d5ca3-222">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-222">The default is the current directory.</span></span>

## <a name="verbosity"></a><span data-ttu-id="d5ca3-223">Detalhamento</span><span class="sxs-lookup"><span data-stu-id="d5ca3-223">Verbosity</span></span>

<span data-ttu-id="d5ca3-224">`--verbosity | -v` (string)</span><span class="sxs-lookup"><span data-stu-id="d5ca3-224">`--verbosity | -v` (string)</span></span>

<span data-ttu-id="d5ca3-225">Define o nível de detalhamento da saída padrão.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-225">Sets the verbosity level of the standard output.</span></span>

<span data-ttu-id="d5ca3-226">Valores permitidos são:</span><span class="sxs-lookup"><span data-stu-id="d5ca3-226">Allowed values are:</span></span>

- `q[uiet]`
- <span data-ttu-id="d5ca3-227">`m[inimal]` (por padrão)</span><span class="sxs-lookup"><span data-stu-id="d5ca3-227">`m[inimal]`  (by default)</span></span>
- <span data-ttu-id="d5ca3-228">`diag[nostic]` (nível de informações de registro em log)</span><span class="sxs-lookup"><span data-stu-id="d5ca3-228">`diag[nostic]` (logging information level)</span></span>

<span data-ttu-id="d5ca3-229">Por padrão, a ferramenta CLI deve mostrar alguns comentários mínimos ( `minimal` ) ao trabalhar, como mencionar que ele está funcionando e, se possível, quanto tempo é deixado ou qual% do tempo é concluído.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-229">By default, the CLI tool should show some minimum feedback (`minimal`) when working, such as mentioning that it is working and if possible how much time is left or what % of the time is completed.</span></span>

## <a name="help"></a><span data-ttu-id="d5ca3-230">Ajuda</span><span class="sxs-lookup"><span data-stu-id="d5ca3-230">Help</span></span>

`-h |--help`

<span data-ttu-id="d5ca3-231">Imprime uma ajuda para o comando com uma descrição para o parâmetro de cada comando.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-231">Prints out help for the command with a description for each command's parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="d5ca3-232">Confira também</span><span class="sxs-lookup"><span data-stu-id="d5ca3-232">See also</span></span>

- [<span data-ttu-id="d5ca3-233">Como instalar a ferramenta de CLI do ML.NET</span><span class="sxs-lookup"><span data-stu-id="d5ca3-233">How to install the ML.NET CLI tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="d5ca3-234">Visão geral da CLI do ML.NET</span><span class="sxs-lookup"><span data-stu-id="d5ca3-234">Overview of the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="d5ca3-235">Tutorial: analisar o sentimentos usando a CLI do ML.NET</span><span class="sxs-lookup"><span data-stu-id="d5ca3-235">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="d5ca3-236">Telemetria na CLI do ML.NET</span><span class="sxs-lookup"><span data-stu-id="d5ca3-236">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
