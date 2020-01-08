---
title: Referência de comando da CLI ML.NET
description: Visão geral, exemplos e referência para o comando de treinamento automático na ferramenta de CLI do ML.NET.
ms.date: 12/18/2019
ms.openlocfilehash: 5e59eba91721b26622360818a73adb07a654dc28
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636114"
---
# <a name="the-mlnet-cli-command-reference"></a><span data-ttu-id="4b655-103">A referência de comando da CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="4b655-103">The ML.NET CLI command reference</span></span>

<span data-ttu-id="4b655-104">O comando `auto-train` é o principal comando fornecido pela ferramenta de CLI do ML.NET.</span><span class="sxs-lookup"><span data-stu-id="4b655-104">The `auto-train` command is the main command provided by the ML.NET CLI tool.</span></span> <span data-ttu-id="4b655-105">O comando permite gerar um bom modelo de ML.NET de qualidade usando o AutoML (Machine Learning automatizado), bem como o C# código de exemplo para executar/pontuar esse modelo.</span><span class="sxs-lookup"><span data-stu-id="4b655-105">The command allows you to generate a good quality ML.NET model using automated machine learning (AutoML) as well as the the example C# code to run/score that model.</span></span> <span data-ttu-id="4b655-106">Além disso, o C# código para treinar o modelo é gerado para você pesquisar o algoritmo e as configurações do modelo.</span><span class="sxs-lookup"><span data-stu-id="4b655-106">In addition, the C# code to train the model is generated for you to research the algorithm and settings of the model.</span></span>

> [!NOTE]
> <span data-ttu-id="4b655-107">Este tópico refere-se à CLI do ML.NET e ao AutoML do ML.NET, que estão atualmente em Versão Prévia. O material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="4b655-107">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="overview"></a><span data-ttu-id="4b655-108">{1&gt;Visão Geral&lt;1}</span><span class="sxs-lookup"><span data-stu-id="4b655-108">Overview</span></span>

<span data-ttu-id="4b655-109">Exemplo de uso:</span><span class="sxs-lookup"><span data-stu-id="4b655-109">Example usage:</span></span>

```console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

<span data-ttu-id="4b655-110">O comando `mlnet auto-train` gera os seguintes ativos:</span><span class="sxs-lookup"><span data-stu-id="4b655-110">The `mlnet auto-train` command generates the following assets:</span></span>

- <span data-ttu-id="4b655-111">Um modelo serializado. zip ("melhor modelo") pronto para uso.</span><span class="sxs-lookup"><span data-stu-id="4b655-111">A serialized model .zip ("best model") ready to use.</span></span>
- <span data-ttu-id="4b655-112">C#código para executar/pontuar o modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="4b655-112">C# code to run/score that generated model.</span></span>
- <span data-ttu-id="4b655-113">C#código com o código de treinamento usado para gerar esse modelo.</span><span class="sxs-lookup"><span data-stu-id="4b655-113">C# code with the training code used to generate that model.</span></span>

<span data-ttu-id="4b655-114">Os dois primeiros ativos podem ser usados diretamente em seus aplicativos de usuário final (ASP.NET Core aplicativo Web, serviços, aplicativo de área de trabalho e muito mais) para fazer previsões com o modelo.</span><span class="sxs-lookup"><span data-stu-id="4b655-114">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app and more) to make predictions with the model.</span></span>

<span data-ttu-id="4b655-115">O terceiro ativo, o código de treinamento, mostra o que o código da API ML.NET foi usado pela CLI para treinar o modelo gerado, para que você possa investigar o algoritmo e as configurações específicas do modelo.</span><span class="sxs-lookup"><span data-stu-id="4b655-115">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate the specific algorithm and settings of the model.</span></span>

## <a name="examples"></a><span data-ttu-id="4b655-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="4b655-116">Examples</span></span>

<span data-ttu-id="4b655-117">O comando da CLI mais simples para um problema de classificação binária (AutoML infere a maior parte da configuração dos dados fornecidos):</span><span class="sxs-lookup"><span data-stu-id="4b655-117">The simplest CLI command for a binary classification problem (AutoML infers most of the configuration from the provided data):</span></span>

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

<span data-ttu-id="4b655-118">Outro comando simples da CLI para um problema de regressão:</span><span class="sxs-lookup"><span data-stu-id="4b655-118">Another simple CLI command for a regression problem:</span></span>

``` console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

<span data-ttu-id="4b655-119">Crie e treine um modelo de classificação binária com um conjunto de dados de treinamento, um conjunto de dados de teste e ainda mais argumentos explícitos de personalização:</span><span class="sxs-lookup"><span data-stu-id="4b655-119">Create and train a binary-classification model with a train dataset, a test dataset, and further customization explicit arguments:</span></span>

```console
mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="command-options"></a><span data-ttu-id="4b655-120">Opções de comando</span><span class="sxs-lookup"><span data-stu-id="4b655-120">Command options</span></span>

<span data-ttu-id="4b655-121">`mlnet auto-train` treina vários modelos com base no conjunto de um fornecido e, finalmente, seleciona o melhor modelo, salva-o como um arquivo. C# zip serializado, além de gerar código relacionado para pontuação e treinamento.</span><span class="sxs-lookup"><span data-stu-id="4b655-121">`mlnet auto-train` trains multiple models based on the provided dataset and finally selects the best model, saves it as a serialized .zip file plus generates related C# code for scoring and training.</span></span>

```console
mlnet auto-train

--task | --mltask | -T <value>

--dataset | -d <value>

[
 [--validation-dataset | -v <value>]
  --test-dataset | -t <value>
]

--label-column-name | -n <value>
|
--label-column-index | -i <value>

[--ignore-columns | -I <value>]

[--has-header | -h <value>]

[--max-exploration-time | -x <value>]

[--verbosity | -V <value>]

[--cache | -c <value>]

[--name | -N <value>]

[--output-path | -o <value>]

[--help | -h]

```

<span data-ttu-id="4b655-122">As opções de entrada inválidas fazem com que a ferramenta CLI emita uma lista de entradas válidas e uma mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="4b655-122">Invalid input options cause the CLI tool to emit a list of valid inputs and an error message.</span></span>

## <a name="task"></a><span data-ttu-id="4b655-123">Tarefa</span><span class="sxs-lookup"><span data-stu-id="4b655-123">Task</span></span>

<span data-ttu-id="4b655-124">`--task | --mltask | -T` (string)</span><span class="sxs-lookup"><span data-stu-id="4b655-124">`--task | --mltask | -T` (string)</span></span>

<span data-ttu-id="4b655-125">Uma única cadeia de caracteres fornecendo o problema de ML a resolver.</span><span class="sxs-lookup"><span data-stu-id="4b655-125">A single string providing the ML problem to solve.</span></span> <span data-ttu-id="4b655-126">Por exemplo, qualquer uma das tarefas a seguir (a CLI eventualmente dará suporte a todas as tarefas compatíveis com o AutoML):</span><span class="sxs-lookup"><span data-stu-id="4b655-126">For instance, any of the following tasks (The CLI will eventually support all tasks supported in AutoML):</span></span>

- <span data-ttu-id="4b655-127">`regression` – escolha se o modelo do ML será usado para prever um valor numérico</span><span class="sxs-lookup"><span data-stu-id="4b655-127">`regression` - Choose if the ML Model will be used to predict a numeric value</span></span>
- <span data-ttu-id="4b655-128">`binary-classification` – escolha se o resultado do modelo de ML terá dois valores boolianos categóricos possíveis (0 ou 1).</span><span class="sxs-lookup"><span data-stu-id="4b655-128">`binary-classification` - Choose if the ML Model result has two possible categorical boolean values (0 or 1).</span></span>
- <span data-ttu-id="4b655-129">`multiclass-classification` – escolha se o resultado do modelo de ML terá vários valores boolianos categóricos possíveis.</span><span class="sxs-lookup"><span data-stu-id="4b655-129">`multiclass-classification` - Choose if the ML Model result has multiple categorical possible values.</span></span>

<span data-ttu-id="4b655-130">Uma tarefa de ML deve ser fornecida neste argumento.</span><span class="sxs-lookup"><span data-stu-id="4b655-130">Only one ML task should be provided in this argument.</span></span>

## <a name="dataset"></a><span data-ttu-id="4b655-131">Conjunto de Dados</span><span class="sxs-lookup"><span data-stu-id="4b655-131">Dataset</span></span>

<span data-ttu-id="4b655-132">`--dataset | -d` (string)</span><span class="sxs-lookup"><span data-stu-id="4b655-132">`--dataset | -d` (string)</span></span>

<span data-ttu-id="4b655-133">Esse argumento fornece o caminho do arquivo para uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="4b655-133">This argument provides the filepath to either one of the following options:</span></span>

- <span data-ttu-id="4b655-134">*R: todo o arquivo do conjunto de arquivos:* Se você estiver usando essa opção e o usuário não estiver fornecendo `--test-dataset` e `--validation-dataset`, em seguida, a validação cruzada (k-fold, etc.) ou abordagens de divisão de dados automatizadas serão usadas internamente para validar o modelo.</span><span class="sxs-lookup"><span data-stu-id="4b655-134">*A: The whole dataset file:* If using this option and the user is not providing `--test-dataset` and `--validation-dataset`, then cross-validation (k-fold, etc.) or automated data split approaches will be used internally for validating the model.</span></span> <span data-ttu-id="4b655-135">Nesse caso, o usuário precisará apenas fornecer o caminho do arquivo do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="4b655-135">In that case, the user will just need to provide the dataset filepath.</span></span>

- <span data-ttu-id="4b655-136">*B: o arquivo do conjunto de arquivos de treinamento:* Se o usuário também estiver fornecendo conjuntos de valores para validação de modelo (usando `--test-dataset` e, opcionalmente, `--validation-dataset`), o argumento de `--dataset` significará ter apenas o "conjunto de linhas de treinamento".</span><span class="sxs-lookup"><span data-stu-id="4b655-136">*B: The training dataset file:* If the user is also providing datasets for model validation (using `--test-dataset` and optionally `--validation-dataset`), then the `--dataset` argument means to only have the "training dataset".</span></span> <span data-ttu-id="4b655-137">Por exemplo, ao usar uma abordagem de 80-20% para validar a qualidade do modelo e obter métricas de precisão, o "conjunto de dados treinamento" terá 80% dos dados e o "conjunto de dados de teste" terá 20% dos dados.</span><span class="sxs-lookup"><span data-stu-id="4b655-137">For example, when using an 80% - 20% approach to validate the quality of the model and to obtain accuracy metrics, the "training dataset" will have 80% of the data and the "test dataset" would have 20% of the data.</span></span>

## <a name="test-dataset"></a><span data-ttu-id="4b655-138">Conjunto de dados de teste</span><span class="sxs-lookup"><span data-stu-id="4b655-138">Test dataset</span></span>

<span data-ttu-id="4b655-139">`--test-dataset | -t` (string)</span><span class="sxs-lookup"><span data-stu-id="4b655-139">`--test-dataset | -t` (string)</span></span>

<span data-ttu-id="4b655-140">Caminho do arquivo que aponta para o arquivo de conjunto de dados de teste, por exemplo, ao usar uma abordagem de 80-20% ao realizar validações regulares para obter métricas de precisão.</span><span class="sxs-lookup"><span data-stu-id="4b655-140">File path pointing to the test dataset file, for example when using an 80% - 20% approach when making regular validations to obtain accuracy metrics.</span></span>

<span data-ttu-id="4b655-141">Ao usar `--test-dataset`, `--dataset` também é necessária.</span><span class="sxs-lookup"><span data-stu-id="4b655-141">If using `--test-dataset`, then `--dataset` is also required.</span></span>

<span data-ttu-id="4b655-142">O argumento `--test-dataset` é opcional, a menos que o --validation-dataset seja usado.</span><span class="sxs-lookup"><span data-stu-id="4b655-142">The `--test-dataset` argument is optional unless the --validation-dataset is used.</span></span> <span data-ttu-id="4b655-143">Nesse caso, o usuário precisa usar os três argumentos.</span><span class="sxs-lookup"><span data-stu-id="4b655-143">In that case, the user must use the three arguments.</span></span>

## <a name="validation-dataset"></a><span data-ttu-id="4b655-144">Conjunto de dados de validação</span><span class="sxs-lookup"><span data-stu-id="4b655-144">Validation dataset</span></span>

<span data-ttu-id="4b655-145">`--validation-dataset | -v` (string)</span><span class="sxs-lookup"><span data-stu-id="4b655-145">`--validation-dataset | -v` (string)</span></span>

<span data-ttu-id="4b655-146">Caminho do arquivo apontando para o arquivo de conjunto de dados de validação.</span><span class="sxs-lookup"><span data-stu-id="4b655-146">File path pointing to the validation dataset file.</span></span> <span data-ttu-id="4b655-147">O conjunto de dados de validação é opcional em qualquer caso.</span><span class="sxs-lookup"><span data-stu-id="4b655-147">The validation dataset is optional, in any case.</span></span>

<span data-ttu-id="4b655-148">Se usar um `validation dataset`, o comportamento deverá ser:</span><span class="sxs-lookup"><span data-stu-id="4b655-148">If using a `validation dataset`, the behavior should be:</span></span>

- <span data-ttu-id="4b655-149">Os argumentos `test-dataset` e `--dataset` também são necessários.</span><span class="sxs-lookup"><span data-stu-id="4b655-149">The `test-dataset` and `--dataset` arguments are also required.</span></span>

- <span data-ttu-id="4b655-150">O conjunto de dados `validation-dataset` é usado para estimar o erro de previsão para a seleção de modelo.</span><span class="sxs-lookup"><span data-stu-id="4b655-150">The `validation-dataset` dataset is used to estimate prediction error for model selection.</span></span>

- <span data-ttu-id="4b655-151">O `test-dataset` é usado para a avaliação do erro de generalização do modelo final escolhido.</span><span class="sxs-lookup"><span data-stu-id="4b655-151">The `test-dataset` is used for assessment of the generalization error of the final chosen model.</span></span> <span data-ttu-id="4b655-152">O ideal é que o conjunto de teste seja mantido em um "cofre" e seja levado somente no final da análise de dados.</span><span class="sxs-lookup"><span data-stu-id="4b655-152">Ideally, the test set should be kept in a “vault,” and be brought out only at the end of the data analysis.</span></span>

<span data-ttu-id="4b655-153">Basicamente, ao usar um `validation dataset` mais o `test dataset`, a fase de validação é dividida em duas partes:</span><span class="sxs-lookup"><span data-stu-id="4b655-153">Basically, when using a `validation dataset` plus the `test dataset`, the validation phase is split into two parts:</span></span>

1. <span data-ttu-id="4b655-154">Na primeira parte, você apenas examina seus modelos e seleciona a abordagem com melhor desempenho usando os dados de validação (=validation)</span><span class="sxs-lookup"><span data-stu-id="4b655-154">In the first part, you just look at your models and select the best performing approach using the validation data (=validation)</span></span>
2. <span data-ttu-id="4b655-155">Em seguida, você pode estimar a precisão da abordagem selecionada (=test).</span><span class="sxs-lookup"><span data-stu-id="4b655-155">Then you estimate the accuracy of the selected approach (=test).</span></span>

<span data-ttu-id="4b655-156">Portanto, a separação dos dados pode ser 80/10/10 ou 75/15/10.</span><span class="sxs-lookup"><span data-stu-id="4b655-156">Hence, the separation of data could be 80/10/10 or 75/15/10.</span></span> <span data-ttu-id="4b655-157">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4b655-157">For example:</span></span>

- <span data-ttu-id="4b655-158">O arquivo `training-dataset` deve ter 75% dos dados.</span><span class="sxs-lookup"><span data-stu-id="4b655-158">`training-dataset` file should have 75% of the data.</span></span>
- <span data-ttu-id="4b655-159">O arquivo `validation-dataset` deve ter 15% dos dados.</span><span class="sxs-lookup"><span data-stu-id="4b655-159">`validation-dataset` file should have 15% of the data.</span></span>
- <span data-ttu-id="4b655-160">O arquivo `test-dataset` deve ter 10% dos dados.</span><span class="sxs-lookup"><span data-stu-id="4b655-160">`test-dataset` file should have 10% of the data.</span></span>

<span data-ttu-id="4b655-161">Em qualquer caso, essas porcentagens serão decididas pelo usuário usando a CLI que fornecerá os arquivos já dividido.</span><span class="sxs-lookup"><span data-stu-id="4b655-161">In any case, those percentages will be decided by the user using the CLI who will provide the files already split.</span></span>

## <a name="label-column-name"></a><span data-ttu-id="4b655-162">Nome da coluna do rótulo</span><span class="sxs-lookup"><span data-stu-id="4b655-162">Label column name</span></span>

<span data-ttu-id="4b655-163">`--label-column-name | -n` (string)</span><span class="sxs-lookup"><span data-stu-id="4b655-163">`--label-column-name | -n` (string)</span></span>

<span data-ttu-id="4b655-164">Com este argumento, uma coluna de destino/objetivo específica (a variável que você deseja prever) pode ser especificada usando o nome da coluna definido no cabeçalho do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="4b655-164">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's name set in the dataset's header.</span></span>

<span data-ttu-id="4b655-165">Esse argumento é usado somente para tarefas de ML supervisionadas, tais como um *problema de classificação*.</span><span class="sxs-lookup"><span data-stu-id="4b655-165">This argument is used only for supervised ML tasks such as a *classification problem*.</span></span> <span data-ttu-id="4b655-166">Ele não pode ser usado para tarefas de ML sem supervisão, tais como *clustering*.</span><span class="sxs-lookup"><span data-stu-id="4b655-166">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

## <a name="label-column-index"></a><span data-ttu-id="4b655-167">Índice de coluna de rótulo</span><span class="sxs-lookup"><span data-stu-id="4b655-167">Label column index</span></span>

<span data-ttu-id="4b655-168">`--label-column-index | -i` (int)</span><span class="sxs-lookup"><span data-stu-id="4b655-168">`--label-column-index | -i` (int)</span></span>

<span data-ttu-id="4b655-169">Com este argumento, uma coluna de destino/objetivo específico (a variável que você deseja prever) pode ser especificada usando o índice numérico da coluna no arquivo do conjunto de dados (os valores de coluna de índice começam em 1).</span><span class="sxs-lookup"><span data-stu-id="4b655-169">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's numeric index in the dataset's file (The column index values start at 1).</span></span>

<span data-ttu-id="4b655-170">*Observação:* Se o usuário também estiver usando o `--label-column-name`, o `--label-column-name` será usado.</span><span class="sxs-lookup"><span data-stu-id="4b655-170">*Note:* If the user is also using the `--label-column-name`, the `--label-column-name` is the one being used.</span></span>

<span data-ttu-id="4b655-171">Esse argumento é usado apenas para a tarefa de ML supervisionada, tal como um *problema de classificação*.</span><span class="sxs-lookup"><span data-stu-id="4b655-171">This argument is used only for supervised ML task such as a *classification problem*.</span></span> <span data-ttu-id="4b655-172">Ele não pode ser usado para tarefas de ML sem supervisão, tais como *clustering*.</span><span class="sxs-lookup"><span data-stu-id="4b655-172">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

## <a name="ignore-columns"></a><span data-ttu-id="4b655-173">Ignorar colunas</span><span class="sxs-lookup"><span data-stu-id="4b655-173">Ignore columns</span></span>

<span data-ttu-id="4b655-174">`--ignore-columns | -I` (string)</span><span class="sxs-lookup"><span data-stu-id="4b655-174">`--ignore-columns | -I` (string)</span></span>

<span data-ttu-id="4b655-175">Com este argumento, você pode ignorar as colunas existentes no arquivo de conjunto de dados para que elas não sejam carregadas e usadas pelos processos de treinamento.</span><span class="sxs-lookup"><span data-stu-id="4b655-175">With this argument, you can ignore existing columns in the dataset file so they are not loaded and used by the training processes.</span></span>

<span data-ttu-id="4b655-176">Especifique os nomes de colunas que você deseja ignorar.</span><span class="sxs-lookup"><span data-stu-id="4b655-176">Specify the columns names that you want to ignore.</span></span> <span data-ttu-id="4b655-177">Use ',' (vírgula com espaço) ou ' ' (espaço) para separar vários nomes de coluna.</span><span class="sxs-lookup"><span data-stu-id="4b655-177">Use ', ' (comma with space) or ' ' (space) to separate multiple column names.</span></span> <span data-ttu-id="4b655-178">Você pode usar aspas para nomes de coluna que contêm espaço em branco (por exemplo, "usuário logado").</span><span class="sxs-lookup"><span data-stu-id="4b655-178">You can use quotes for column names containing whitespace (e.g. "logged in").</span></span>

<span data-ttu-id="4b655-179">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="4b655-179">Example:</span></span>

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a><span data-ttu-id="4b655-180">Tem cabeçalho</span><span class="sxs-lookup"><span data-stu-id="4b655-180">Has header</span></span>

<span data-ttu-id="4b655-181">`--has-header | -h` (bool)</span><span class="sxs-lookup"><span data-stu-id="4b655-181">`--has-header | -h` (bool)</span></span>

<span data-ttu-id="4b655-182">Especifique se os arquivos de conjunto de dados têm uma linha de cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="4b655-182">Specify if the dataset file(s) have a header row.</span></span>
<span data-ttu-id="4b655-183">Os possíveis valores são:</span><span class="sxs-lookup"><span data-stu-id="4b655-183">Possible values are:</span></span>

- `true`
- `false`

<span data-ttu-id="4b655-184">O valor padrão será `true` se esse argumento não for especificado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="4b655-184">The by default value is `true` if this argument is not specified by the user.</span></span>

<span data-ttu-id="4b655-185">Para usar o argumento `--label-column-name`, você precisa ter um cabeçalho no arquivo de conjunto de dados e `--has-header` definido como `true` (o que ocorre por padrão).</span><span class="sxs-lookup"><span data-stu-id="4b655-185">In order to use the `--label-column-name` argument, you need to have a header in the dataset file and `--has-header` set to `true` (which is by default).</span></span>

## <a name="max-exploration-time"></a><span data-ttu-id="4b655-186">Tempo máximo de exploração</span><span class="sxs-lookup"><span data-stu-id="4b655-186">Max exploration time</span></span>

<span data-ttu-id="4b655-187">`--max-exploration-time | -x` (string)</span><span class="sxs-lookup"><span data-stu-id="4b655-187">`--max-exploration-time | -x` (string)</span></span>

<span data-ttu-id="4b655-188">Por padrão, o tempo máximo de exploração é de 30 minutos.</span><span class="sxs-lookup"><span data-stu-id="4b655-188">By default, the maximum exploration time is 30 minutes.</span></span>

<span data-ttu-id="4b655-189">Esse argumento define o tempo máximo (em segundos) para o processo explorar vários treinadores e configurações.</span><span class="sxs-lookup"><span data-stu-id="4b655-189">This argument sets the maximum time (in seconds) for the process to explore multiple trainers and configurations.</span></span> <span data-ttu-id="4b655-190">O tempo configurado poderá ser excedido se o tempo fornecido for muito curto (digamos, dois segundos) para uma única iteração.</span><span class="sxs-lookup"><span data-stu-id="4b655-190">The configured time may be exceeded if the provided time is too short (say 2 seconds) for a single iteration.</span></span> <span data-ttu-id="4b655-191">Nesse caso, o tempo real é o tempo necessário para produzir uma configuração de modelo em uma única iteração.</span><span class="sxs-lookup"><span data-stu-id="4b655-191">In this case, the actual time is the required time to produce one model configuration in a single iteration.</span></span>

<span data-ttu-id="4b655-192">O tempo necessário para iterações pode variar, dependendo do tamanho do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="4b655-192">The needed time for iterations can vary depending on the size of the dataset.</span></span>

## <a name="cache"></a><span data-ttu-id="4b655-193">Cache</span><span class="sxs-lookup"><span data-stu-id="4b655-193">Cache</span></span>

<span data-ttu-id="4b655-194">`--cache | -c` (string)</span><span class="sxs-lookup"><span data-stu-id="4b655-194">`--cache | -c` (string)</span></span>

<span data-ttu-id="4b655-195">Se você usar o armazenamento em cache, o conjunto de dados de treinamento inteiro será carregado na memória.</span><span class="sxs-lookup"><span data-stu-id="4b655-195">If you use caching, the whole training dataset will be loaded in-memory.</span></span>

<span data-ttu-id="4b655-196">Para conjuntos de dados pequenos e médios, usar o cache pode melhorar drasticamente o desempenho de treinamento, o que significa que o tempo de treinamento pode ser menor do que quando você não usa o cache.</span><span class="sxs-lookup"><span data-stu-id="4b655-196">For small and medium datasets, using cache can drastically improve the training performance, meaning the training time can be shorter than when you don't use cache.</span></span>

<span data-ttu-id="4b655-197">No entanto, para grandes conjuntos de dados, carregar todos os dados na memória pode ter um efeito negativo, pois você poderá ficar com memória insuficiente.</span><span class="sxs-lookup"><span data-stu-id="4b655-197">However, for large datasets, loading all the data in memory can impact negatively since you might get out of memory.</span></span> <span data-ttu-id="4b655-198">Ao treinar com arquivos de conjunto de dados grandes sem usar o cache, o ML.NET transmitirá partes de dados da unidade quando ele precisar carregar mais dados durante o treinamento.</span><span class="sxs-lookup"><span data-stu-id="4b655-198">When training with large dataset files and not using cache, ML.NET will be streaming chunks of data from the drive when it needs to load more data while training.</span></span>

<span data-ttu-id="4b655-199">Você pode especificar os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="4b655-199">You can specify the following values:</span></span>

<span data-ttu-id="4b655-200">`on`: força o cache a ser usado durante o treinamento.</span><span class="sxs-lookup"><span data-stu-id="4b655-200">`on`: Forces cache to be used when training.</span></span>
<span data-ttu-id="4b655-201">`off`: força o cache a não ser usado durante o treinamento.</span><span class="sxs-lookup"><span data-stu-id="4b655-201">`off`: Forces cache not to be used when training.</span></span>
<span data-ttu-id="4b655-202">`auto`: dependendo da heurística do AutoML, o cache será usado ou não.</span><span class="sxs-lookup"><span data-stu-id="4b655-202">`auto`: Depending on AutoML heuristics, the cache will be used or not.</span></span> <span data-ttu-id="4b655-203">Em geral, conjuntos de dados pequenos/médios usarão o cache e grandes conjuntos de dados não usarão o cache se você usar a escolha `auto`.</span><span class="sxs-lookup"><span data-stu-id="4b655-203">Usually, small/medium datasets will use cache and large datasets won't use cache if you use the `auto` choice.</span></span>

<span data-ttu-id="4b655-204">Se você não especificar o parâmetro `--cache`, a configuração de cache `auto` será usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="4b655-204">If you don't specify the `--cache` parameter, then the cache `auto` configuration will be used by default.</span></span>

## <a name="name"></a><span data-ttu-id="4b655-205">Name</span><span class="sxs-lookup"><span data-stu-id="4b655-205">Name</span></span>

<span data-ttu-id="4b655-206">`--name | -N` (string)</span><span class="sxs-lookup"><span data-stu-id="4b655-206">`--name | -N` (string)</span></span>

<span data-ttu-id="4b655-207">O nome para a solução ou projeto de saída criado.</span><span class="sxs-lookup"><span data-stu-id="4b655-207">The name for the created output project or solution.</span></span> <span data-ttu-id="4b655-208">Se nenhum nome for especificado, o nome `sample-{mltask}` será usado.</span><span class="sxs-lookup"><span data-stu-id="4b655-208">If no name is specified, the name `sample-{mltask}` is used.</span></span>

<span data-ttu-id="4b655-209">O arquivo de modelo do ML.NET (arquivo zip) também receberá o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="4b655-209">The ML.NET model file (.ZIP file) will get the same name, as well.</span></span>

## <a name="output-path"></a><span data-ttu-id="4b655-210">Caminho de saída</span><span class="sxs-lookup"><span data-stu-id="4b655-210">Output path</span></span>

<span data-ttu-id="4b655-211">`--output-path | -o` (string)</span><span class="sxs-lookup"><span data-stu-id="4b655-211">`--output-path | -o` (string)</span></span>

<span data-ttu-id="4b655-212">Local/pasta raiz para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="4b655-212">Root location/folder to place the generated output.</span></span> <span data-ttu-id="4b655-213">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="4b655-213">The default is the current directory.</span></span>

## <a name="verbosity"></a><span data-ttu-id="4b655-214">Detalhamento</span><span class="sxs-lookup"><span data-stu-id="4b655-214">Verbosity</span></span>

<span data-ttu-id="4b655-215">`--verbosity | -V` (string)</span><span class="sxs-lookup"><span data-stu-id="4b655-215">`--verbosity | -V` (string)</span></span>

<span data-ttu-id="4b655-216">Define o nível de detalhamento da saída padrão.</span><span class="sxs-lookup"><span data-stu-id="4b655-216">Sets the verbosity level of the standard output.</span></span>

<span data-ttu-id="4b655-217">Os valores permitidos são:</span><span class="sxs-lookup"><span data-stu-id="4b655-217">Allowed values are:</span></span>

- `q[uiet]`
- <span data-ttu-id="4b655-218">`m[inimal]` (por padrão)</span><span class="sxs-lookup"><span data-stu-id="4b655-218">`m[inimal]`  (by default)</span></span>
- <span data-ttu-id="4b655-219">`diag[nostic]` (nível de informações de registro em log)</span><span class="sxs-lookup"><span data-stu-id="4b655-219">`diag[nostic]` (logging information level)</span></span>

<span data-ttu-id="4b655-220">Por padrão, a ferramenta da CLI deve mostrar alguns comentários mínimos (mínimo) quando estiver funcionando, por exemplo, mencionar que ela está funcionando e, se possível, quanto tempo falta ou que percentual do tempo foi concluído.</span><span class="sxs-lookup"><span data-stu-id="4b655-220">By default, the CLI tool should show some minimum feedback (minimal) when working, such as mentioning that it is working and if possible how much time is left or what % of the time is completed.</span></span>

## <a name="help"></a><span data-ttu-id="4b655-221">Ajuda</span><span class="sxs-lookup"><span data-stu-id="4b655-221">Help</span></span>

`-h|--help`

<span data-ttu-id="4b655-222">Imprime uma ajuda para o comando com uma descrição para o parâmetro de cada comando.</span><span class="sxs-lookup"><span data-stu-id="4b655-222">Prints out help for the command with a description for each command's parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b655-223">Veja também</span><span class="sxs-lookup"><span data-stu-id="4b655-223">See also</span></span>

- [<span data-ttu-id="4b655-224">Como instalar a ferramenta de CLI do ML.NET</span><span class="sxs-lookup"><span data-stu-id="4b655-224">How to install the ML.NET CLI tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="4b655-225">Visão geral da CLI do ML.NET</span><span class="sxs-lookup"><span data-stu-id="4b655-225">Overview of the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="4b655-226">Tutorial: analisar o sentimentos usando a CLI do ML.NET</span><span class="sxs-lookup"><span data-stu-id="4b655-226">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="4b655-227">Telemetria na CLI do ML.NET</span><span class="sxs-lookup"><span data-stu-id="4b655-227">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
