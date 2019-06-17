---
title: O comando auto-train na ferramenta de CLI do ML.NET
description: Visão geral, exemplos e referência para o comando de treinamento automático na ferramenta de CLI do ML.NET.
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: ce5994f392c492e80676b9e65ce54fe010cf03ab
ms.sourcegitcommit: 90f0bee0e8a416e45c78fa3ad4c91ef00e5228d5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66722607"
---
# <a name="the-auto-train-command-in-mlnet-cli"></a><span data-ttu-id="09b6e-103">O comando 'auto-train' no ML.NET</span><span class="sxs-lookup"><span data-stu-id="09b6e-103">The 'auto-train' command in ML.NET CLI</span></span>

> [!NOTE]
> <span data-ttu-id="09b6e-104">Este tópico refere-se à CLI do ML.NET e ao AutoML do ML.NET, que estão atualmente em Versão Prévia. O material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="09b6e-104">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

<span data-ttu-id="09b6e-105">O comando `auto-train` é o principal comando fornecido pela ferramenta de CLI do ML.NET.</span><span class="sxs-lookup"><span data-stu-id="09b6e-105">The `auto-train` command is the main command provided by the ML.NET CLI tool.</span></span> <span data-ttu-id="09b6e-106">O comando permite que você gere um modelo do ML.NET de boa qualidade (arquivo zip de modelo serializado) mais o código C# de exemplo para executar/pontuar esse modelo.</span><span class="sxs-lookup"><span data-stu-id="09b6e-106">The command allows you to generate a good quality ML.NET model (serialized model .zip file) plus the example C# code to run/score that model.</span></span> <span data-ttu-id="09b6e-107">Além disso, o código C# para criar/treinar esse modelo também é gerado para que você possa pesquisar qual algoritmo e configurações ele está usando para esse "melhor modelo" gerado.</span><span class="sxs-lookup"><span data-stu-id="09b6e-107">In addition, the C# code to create/train that model is also generated for you to research what algorithm and settings it is using for that generated "best model".</span></span>

<span data-ttu-id="09b6e-108">Você pode gerar esses ativos de seus próprios conjuntos de dados sem codificação por conta própria, portanto, ele também melhorará a sua produtividade, mesmo se você já conhecer o ML.NET.</span><span class="sxs-lookup"><span data-stu-id="09b6e-108">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="09b6e-109">Atualmente, as tarefas de ML compatíveis com a CLI do ML.NET são:</span><span class="sxs-lookup"><span data-stu-id="09b6e-109">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- `binary-classification`
- `multiclass-classification`
- `regression`

- <span data-ttu-id="09b6e-110">Futuro: Outra tarefas aprendizado de máquina, tais como</span><span class="sxs-lookup"><span data-stu-id="09b6e-110">Future: Other machine learning tasks, such as</span></span>
  - `recommendation`
  - `anomaly-detection`
  - `clustering`

<span data-ttu-id="09b6e-111">Exemplo de uso no prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="09b6e-111">Example of usage on the command prompt:</span></span>

```console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

<span data-ttu-id="09b6e-112">O comando `mlnet auto-train` gera os seguintes ativos:</span><span class="sxs-lookup"><span data-stu-id="09b6e-112">The `mlnet auto-train` command generates the following assets:</span></span>

- <span data-ttu-id="09b6e-113">Um modelo serializado. zip ("melhor modelo") pronto para uso.</span><span class="sxs-lookup"><span data-stu-id="09b6e-113">A serialized model .zip ("best model") ready to use.</span></span>
- <span data-ttu-id="09b6e-114">Código C# para a execução/pontuação que gerou o modelo (para fazer previsões em seus aplicativos do usuário final com esse modelo).</span><span class="sxs-lookup"><span data-stu-id="09b6e-114">C# code to run/score that generated model (To make predictions in your end-user apps with that model).</span></span>
- <span data-ttu-id="09b6e-115">Código C# com o código de treinamento usado para gerar esse modelo (fins de aprendizado).</span><span class="sxs-lookup"><span data-stu-id="09b6e-115">C# code with the training code used to generate that model (Learning purposes).</span></span>

<span data-ttu-id="09b6e-116">Os primeiros dois ativos podem ser usados diretamente em seus aplicativos de usuário final (aplicativo Web ASP.NET Core, serviços, aplicativo da área de trabalho etc.) para fazer previsões com esse modelo de ML gerado.</span><span class="sxs-lookup"><span data-stu-id="09b6e-116">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="09b6e-117">O terceiro ativo, o código de treinamento, mostra o que o código de API do ML.NET foi usado pela CLI para treinar o modelo gerado, portanto, você pode investigar quais treinador/algoritmo e hiperparâmetros específicos foram selecionados pela CLI e pelo mecanismo de AutoML do ML.NET.</span><span class="sxs-lookup"><span data-stu-id="09b6e-117">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate what specific trainer/algorithm and hyper-paramenters were selected by the CLI and the ML.NET AutoML engine.</span></span>

## <a name="the-auto-train-command-uses-the-automl-engine"></a><span data-ttu-id="09b6e-118">O comando 'auto-train' usa o mecanismo de AutoML</span><span class="sxs-lookup"><span data-stu-id="09b6e-118">The 'auto-train' command uses the AutoML engine</span></span>

<span data-ttu-id="09b6e-119">A CLI usa o mecanismo de AutoML do ML.NET (pacote do NuGet) para pesquisar com inteligência para os modelos de melhor qualidade, conforme mostrado no diagrama a seguir:</span><span class="sxs-lookup"><span data-stu-id="09b6e-119">The CLI uses the ML.NET AutoML engine (NuGet package) to intelligently search for the best quality models, as shown in the following diagram:</span></span>

<span data-ttu-id="09b6e-120">![imagem](./media/ml-net-automl-working-diagram.png "Mecanismo AutoML funcionando dentro da CLI do ML.NET")</span><span class="sxs-lookup"><span data-stu-id="09b6e-120">![image](./media/ml-net-automl-working-diagram.png "AutoML engine working inside the ML.NET CLI")</span></span>

<span data-ttu-id="09b6e-121">Ao executar a ferramenta de CLI do ML.NET com o comando 'auto-train', você verá a ferramenta tentar muitas iterações com algoritmos e combinações de configuração diferentes.</span><span class="sxs-lookup"><span data-stu-id="09b6e-121">When running the ML.NET CLI tool with the \`auto-train- command, you'll see the tool trying many iterations with different algorithms and combinations of configuration.</span></span>

## <a name="reference-for-auto-train-command"></a><span data-ttu-id="09b6e-122">Referência do comando 'auto-train'</span><span class="sxs-lookup"><span data-stu-id="09b6e-122">Reference for 'auto-train' command</span></span>

## <a name="examples"></a><span data-ttu-id="09b6e-123">Exemplos</span><span class="sxs-lookup"><span data-stu-id="09b6e-123">Examples</span></span>

<span data-ttu-id="09b6e-124">Comando mais simples da CLI para um problema de classificação binária (o AutoML precisará inferir a maior parte da configuração dos dados fornecidos):</span><span class="sxs-lookup"><span data-stu-id="09b6e-124">Simplest CLI command for a binary classification problem (AutoML will need to infer most of the configuration from the provided data):</span></span>

```console
> mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

<span data-ttu-id="09b6e-125">Outro comando simples da CLI para um problema de regressão:</span><span class="sxs-lookup"><span data-stu-id="09b6e-125">Another simple CLI command for a regression problem:</span></span>

``` console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

<span data-ttu-id="09b6e-126">Crie e treine um modelo de classificação binária com um conjunto de dados de treinamento, um conjunto de dados de teste e ainda mais argumentos explícitos de personalização:</span><span class="sxs-lookup"><span data-stu-id="09b6e-126">Create and train a binary-classification model with a train dataset, a test dataset, and further customization explicit arguments:</span></span>

```console
> mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="name"></a><span data-ttu-id="09b6e-127">Nome</span><span class="sxs-lookup"><span data-stu-id="09b6e-127">Name</span></span>

<span data-ttu-id="09b6e-128">`mlnet auto-train` – Treina vários modelos ('n' iterações) com base no conjunto de dados fornecido e, finalmente, seleciona o melhor modelo, salva-o como um arquivo zip serializado e gera o código C# relacionado para pontuação e treinamento.</span><span class="sxs-lookup"><span data-stu-id="09b6e-128">`mlnet auto-train` - Trains multiple models ('n' iterations) based on the provided dataset and finally selects the best model, saves it as a serialized .zip file plus generates related C# code for scoring and training.</span></span>

## <a name="synopsis"></a><span data-ttu-id="09b6e-129">Sinopse</span><span class="sxs-lookup"><span data-stu-id="09b6e-129">Synopsis</span></span>

```console
> mlnet auto-train

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

<span data-ttu-id="09b6e-130">Opções de entrada inválidas devem fazer com que a ferramenta de CLI emita uma lista de entradas válidas e uma mensagem de erro explicando qual argumento está ausente, se esse for o caso.</span><span class="sxs-lookup"><span data-stu-id="09b6e-130">Invalid input options should cause the CLI tool to emit a list of valid inputs and an error message explaining which arg is missing, if that is the case.</span></span>

## <a name="options"></a><span data-ttu-id="09b6e-131">Opções</span><span class="sxs-lookup"><span data-stu-id="09b6e-131">Options</span></span>

 ----------------------------------------------------------

<span data-ttu-id="09b6e-132">`--task | --mltask | -T` (string)</span><span class="sxs-lookup"><span data-stu-id="09b6e-132">`--task | --mltask | -T` (string)</span></span>

<span data-ttu-id="09b6e-133">Uma única cadeia de caracteres fornecendo o problema de ML a resolver.</span><span class="sxs-lookup"><span data-stu-id="09b6e-133">A single string providing the ML problem to solve.</span></span> <span data-ttu-id="09b6e-134">Por exemplo, qualquer uma das tarefas a seguir (a CLI eventualmente dará suporte a todas as tarefas compatíveis com o AutoML):</span><span class="sxs-lookup"><span data-stu-id="09b6e-134">For instance, any of the following tasks (The CLI will eventually support all tasks supported in AutoML):</span></span>

- <span data-ttu-id="09b6e-135">`regression` – escolha se o modelo do ML será usado para prever um valor numérico</span><span class="sxs-lookup"><span data-stu-id="09b6e-135">`regression` - Choose if the ML Model will be used to predict a numeric value</span></span>
- <span data-ttu-id="09b6e-136">`binary-classification` – escolha se o resultado do modelo de ML terá dois valores boolianos categóricos possíveis (0 ou 1).</span><span class="sxs-lookup"><span data-stu-id="09b6e-136">`binary-classification` - Choose if the ML Model result has two possible categorical boolean values (0 or 1).</span></span>
- <span data-ttu-id="09b6e-137">`multiclass-classification` – escolha se o resultado do modelo de ML terá vários valores boolianos categóricos possíveis.</span><span class="sxs-lookup"><span data-stu-id="09b6e-137">`multiclass-classification` - Choose if the ML Model result has multiple categorical possible values.</span></span>

<span data-ttu-id="09b6e-138">Em versões futuras, tarefas de ML e cenários como `recommendations`, `clustering` e `ranking` serão compatíveis.</span><span class="sxs-lookup"><span data-stu-id="09b6e-138">In future releases additional ML Tasks and scenarios such as `recommendations`, `clustering` and `ranking` will be supported.</span></span>

 <span data-ttu-id="09b6e-139">Uma tarefa de ML deve ser fornecida neste argumento.</span><span class="sxs-lookup"><span data-stu-id="09b6e-139">Only one ML task should be provided in this argument.</span></span>

 ----------------------------------------------------------

<span data-ttu-id="09b6e-140">`--dataset | -d` (string)</span><span class="sxs-lookup"><span data-stu-id="09b6e-140">`--dataset | -d` (string)</span></span>

<span data-ttu-id="09b6e-141">Esse argumento fornece o caminho do arquivo para uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="09b6e-141">This argument provides the filepath to either one of the following options:</span></span>

- <span data-ttu-id="09b6e-142">*A: O arquivo de conjunto de dados inteiro:* Se essa opção for usada e o usuário não estiver fornecendo `--test-dataset` e `--validation-dataset`, as abordagens de validação cruzada (k vezes etc.) ou de divisão de dados automatizada serão usadas internamente para validar o modelo.</span><span class="sxs-lookup"><span data-stu-id="09b6e-142">*A: The whole dataset file:* If using this option and the user is not providing `--test-dataset` and `--validation-dataset`, then cross-validation (k-fold, etc.) or automated data split approaches will be used internally for validating the model.</span></span> <span data-ttu-id="09b6e-143">Nesse caso, o usuário precisará apenas fornecer o caminho do arquivo do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="09b6e-143">In that case, the user will just need to provide the dataset filepath.</span></span>

- <span data-ttu-id="09b6e-144">*B: O arquivo de conjunto de dados de treinamento:* Se o usuário também estiver fornecendo conjuntos de dados para a validação de modelo (usando `--test-dataset` e, opcionalmente `--validation-dataset`), então o argumento `--dataset` significará ter apenas o "conjunto de dados de treinamento".</span><span class="sxs-lookup"><span data-stu-id="09b6e-144">*B: The training dataset file:* If the user is also providing datasets for model validation (using `--test-dataset` and optionally `--validation-dataset`), then the `--dataset` argument means to only have the "training dataset".</span></span> <span data-ttu-id="09b6e-145">Por exemplo, ao usar uma abordagem de 80-20% para validar a qualidade do modelo e obter métricas de precisão, o "conjunto de dados treinamento" terá 80% dos dados e o "conjunto de dados de teste" terá 20% dos dados.</span><span class="sxs-lookup"><span data-stu-id="09b6e-145">For example, when using an 80% - 20% approach to validate the quality of the model and to obtain accuracy metrics, the "training dataset" will have 80% of the data and the "test dataset" would have 20% of the data.</span></span>

----------------------------------------------------------

<span data-ttu-id="09b6e-146">`--test-dataset | -t` (string)</span><span class="sxs-lookup"><span data-stu-id="09b6e-146">`--test-dataset | -t` (string)</span></span>

<span data-ttu-id="09b6e-147">Caminho do arquivo que aponta para o arquivo de conjunto de dados de teste, por exemplo, ao usar uma abordagem de 80-20% ao realizar validações regulares para obter métricas de precisão.</span><span class="sxs-lookup"><span data-stu-id="09b6e-147">File path pointing to the test dataset file, for example when using an 80% - 20% approach when making regular validations to obtain accuracy metrics.</span></span>

<span data-ttu-id="09b6e-148">Ao usar `--test-dataset`, `--dataset` também é necessária.</span><span class="sxs-lookup"><span data-stu-id="09b6e-148">If using `--test-dataset`, then `--dataset` is also required.</span></span>

<span data-ttu-id="09b6e-149">O argumento `--test-dataset` é opcional, a menos que o --validation-dataset seja usado.</span><span class="sxs-lookup"><span data-stu-id="09b6e-149">The `--test-dataset` argument is optional unless the --validation-dataset is used.</span></span> <span data-ttu-id="09b6e-150">Nesse caso, o usuário precisa usar os três argumentos.</span><span class="sxs-lookup"><span data-stu-id="09b6e-150">In that case, the user must use the three arguments.</span></span>

----------------------------------------------------------

<span data-ttu-id="09b6e-151">`--validation-dataset | -v` (string)</span><span class="sxs-lookup"><span data-stu-id="09b6e-151">`--validation-dataset | -v` (string)</span></span>

<span data-ttu-id="09b6e-152">Caminho do arquivo apontando para o arquivo de conjunto de dados de validação.</span><span class="sxs-lookup"><span data-stu-id="09b6e-152">File path pointing to the validation dataset file.</span></span> <span data-ttu-id="09b6e-153">O conjunto de dados de validação é opcional em qualquer caso.</span><span class="sxs-lookup"><span data-stu-id="09b6e-153">The validation dataset is optional, in any case.</span></span>

<span data-ttu-id="09b6e-154">Se usar um `validation dataset`, o comportamento deverá ser:</span><span class="sxs-lookup"><span data-stu-id="09b6e-154">If using a `validation dataset`, the behavior should be:</span></span>

- <span data-ttu-id="09b6e-155">Os argumentos `test-dataset` e `--dataset` também são necessários.</span><span class="sxs-lookup"><span data-stu-id="09b6e-155">The `test-dataset` and `--dataset` arguments are also required.</span></span>

- <span data-ttu-id="09b6e-156">O conjunto de dados `validation-dataset` é usado para estimar o erro de previsão para a seleção de modelo.</span><span class="sxs-lookup"><span data-stu-id="09b6e-156">The `validation-dataset` dataset is used to estimate prediction error for model selection.</span></span>

- <span data-ttu-id="09b6e-157">O `test-dataset` é usado para a avaliação do erro de generalização do modelo final escolhido.</span><span class="sxs-lookup"><span data-stu-id="09b6e-157">The `test-dataset` is used for assessment of the generalization error of the final chosen model.</span></span> <span data-ttu-id="09b6e-158">O ideal é que o conjunto de teste seja mantido em um "cofre" e seja levado somente no final da análise de dados.</span><span class="sxs-lookup"><span data-stu-id="09b6e-158">Ideally, the test set should be kept in a “vault,” and be brought out only at the end of the data analysis.</span></span>

<span data-ttu-id="09b6e-159">Basicamente, ao usar um `validation dataset` mais o `test dataset`, a fase de validação é dividida em duas partes:</span><span class="sxs-lookup"><span data-stu-id="09b6e-159">Basically, when using a `validation dataset` plus the `test dataset`, the validation phase is split into two parts:</span></span>

1. <span data-ttu-id="09b6e-160">Na primeira parte, você apenas examina seus modelos e seleciona a abordagem com melhor desempenho usando os dados de validação (=validation)</span><span class="sxs-lookup"><span data-stu-id="09b6e-160">In the first part, you just look at your models and select the best performing approach using the validation data (=validation)</span></span>
2. <span data-ttu-id="09b6e-161">Em seguida, você pode estimar a precisão da abordagem selecionada (=test).</span><span class="sxs-lookup"><span data-stu-id="09b6e-161">Then you estimate the accuracy of the selected approach (=test).</span></span>

<span data-ttu-id="09b6e-162">Portanto, a separação dos dados pode ser 80/10/10 ou 75/15/10.</span><span class="sxs-lookup"><span data-stu-id="09b6e-162">Hence, the separation of data could be 80/10/10 or 75/15/10.</span></span> <span data-ttu-id="09b6e-163">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="09b6e-163">For example:</span></span>

- <span data-ttu-id="09b6e-164">O arquivo `training-dataset` deve ter 75% dos dados.</span><span class="sxs-lookup"><span data-stu-id="09b6e-164">`training-dataset` file should have 75% of the data.</span></span>
- <span data-ttu-id="09b6e-165">O arquivo `validation-dataset` deve ter 15% dos dados.</span><span class="sxs-lookup"><span data-stu-id="09b6e-165">`validation-dataset` file should have 15% of the data.</span></span>
- <span data-ttu-id="09b6e-166">O arquivo `test-dataset` deve ter 10% dos dados.</span><span class="sxs-lookup"><span data-stu-id="09b6e-166">`test-dataset` file should have 10% of the data.</span></span>

<span data-ttu-id="09b6e-167">Em qualquer caso, essas porcentagens serão decididas pelo usuário usando a CLI que fornecerá os arquivos já dividido.</span><span class="sxs-lookup"><span data-stu-id="09b6e-167">In any case, those percentages will be decided by the user using the CLI who will provide the files already split.</span></span>

----------------------------------------------------------

<span data-ttu-id="09b6e-168">`--label-column-name | -n` (string)</span><span class="sxs-lookup"><span data-stu-id="09b6e-168">`--label-column-name | -n` (string)</span></span>

<span data-ttu-id="09b6e-169">Com este argumento, uma coluna de destino/objetivo específica (a variável que você deseja prever) pode ser especificada usando o nome da coluna definido no cabeçalho do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="09b6e-169">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's name set in the dataset's header.</span></span>

<span data-ttu-id="09b6e-170">Esse argumento é usado somente para tarefas de ML supervisionadas, tais como um *problema de classificação*.</span><span class="sxs-lookup"><span data-stu-id="09b6e-170">This argument is used only for supervised ML tasks such as a *classification problem*.</span></span> <span data-ttu-id="09b6e-171">Ele não pode ser usado para tarefas de ML sem supervisão, tais como *clustering*.</span><span class="sxs-lookup"><span data-stu-id="09b6e-171">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

----------------------------------------------------------

<span data-ttu-id="09b6e-172">`--label-column-index | -i` (int)</span><span class="sxs-lookup"><span data-stu-id="09b6e-172">`--label-column-index | -i` (int)</span></span>

<span data-ttu-id="09b6e-173">Com este argumento, uma coluna de destino/objetivo específico (a variável que você deseja prever) pode ser especificada usando o índice numérico da coluna no arquivo do conjunto de dados (os valores de coluna de índice começam em 1).</span><span class="sxs-lookup"><span data-stu-id="09b6e-173">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's numeric index in the dataset's file (The column index values start at 1).</span></span>

<span data-ttu-id="09b6e-174">*Observação:* Se o usuário também estiver usando o `--label-column-name`, o `--label-column-name` será aquele sendo usado.</span><span class="sxs-lookup"><span data-stu-id="09b6e-174">*Note:* If the user is also using the `--label-column-name`, the `--label-column-name` is the one being used.</span></span>

<span data-ttu-id="09b6e-175">Esse argumento é usado apenas para a tarefa de ML supervisionada, tal como um *problema de classificação*.</span><span class="sxs-lookup"><span data-stu-id="09b6e-175">This argument is used only for supervised ML task such as a *classification problem*.</span></span> <span data-ttu-id="09b6e-176">Ele não pode ser usado para tarefas de ML sem supervisão, tais como *clustering*.</span><span class="sxs-lookup"><span data-stu-id="09b6e-176">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

----------------------------------------------------------

<span data-ttu-id="09b6e-177">`--ignore-columns | -I` (string)</span><span class="sxs-lookup"><span data-stu-id="09b6e-177">`--ignore-columns | -I` (string)</span></span>

<span data-ttu-id="09b6e-178">Com este argumento, você pode ignorar as colunas existentes no arquivo de conjunto de dados para que elas não sejam carregadas e usadas pelos processos de treinamento.</span><span class="sxs-lookup"><span data-stu-id="09b6e-178">With this argument, you can ignore existing columns in the dataset file so they are not loaded and used by the training processes.</span></span>

<span data-ttu-id="09b6e-179">Especifique os nomes de colunas que você deseja ignorar.</span><span class="sxs-lookup"><span data-stu-id="09b6e-179">Specify the columns names that you want to ignore.</span></span> <span data-ttu-id="09b6e-180">Use ',' (vírgula com espaço) ou ' ' (espaço) para separar vários nomes de coluna.</span><span class="sxs-lookup"><span data-stu-id="09b6e-180">Use ', ' (comma with space) or ' ' (space) to separate multiple column names.</span></span> <span data-ttu-id="09b6e-181">Você pode usar aspas para nomes de coluna que contêm espaço em branco (por exemplo, "usuário logado").</span><span class="sxs-lookup"><span data-stu-id="09b6e-181">You can use quotes for column names containing whitespace (e.g. "logged in").</span></span>

<span data-ttu-id="09b6e-182">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="09b6e-182">Example:</span></span>

`--ignore-columns email, address, id, logged_in`

----------------------------------------------------------

<span data-ttu-id="09b6e-183">`--has-header | -h` (bool)</span><span class="sxs-lookup"><span data-stu-id="09b6e-183">`--has-header | -h` (bool)</span></span>

<span data-ttu-id="09b6e-184">Especifique se os arquivos de conjunto de dados têm uma linha de cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="09b6e-184">Specify if the dataset file(s) have a header row.</span></span>
<span data-ttu-id="09b6e-185">Os possíveis valores são:</span><span class="sxs-lookup"><span data-stu-id="09b6e-185">Possible values are:</span></span>
- `true`
- `false`

<span data-ttu-id="09b6e-186">O valor padrão será `true` se esse argumento não for especificado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="09b6e-186">The by default value is `true` if this argument is not specified by the user.</span></span>

<span data-ttu-id="09b6e-187">Para usar o argumento `--label-column-name`, você precisa ter um cabeçalho no arquivo de conjunto de dados e `--has-header` definido como `true` (o que ocorre por padrão).</span><span class="sxs-lookup"><span data-stu-id="09b6e-187">In order to use the `--label-column-name` argument, you need to have a header in the dataset file and `--has-header` set to `true` (which is by default).</span></span>

----------------------------------------------------------

<span data-ttu-id="09b6e-188">`--max-exploration-time | -x` (string)</span><span class="sxs-lookup"><span data-stu-id="09b6e-188">`--max-exploration-time | -x` (string)</span></span>

<span data-ttu-id="09b6e-189">Por padrão, o tempo máximo de exploração é de 30 minutos.</span><span class="sxs-lookup"><span data-stu-id="09b6e-189">By default, the maximum exploration time is 30 minutes.</span></span>

<span data-ttu-id="09b6e-190">Esse argumento define o tempo máximo (em segundos) para o processo explorar vários treinadores e configurações.</span><span class="sxs-lookup"><span data-stu-id="09b6e-190">This argument sets the maximum time (in seconds) for the process to explore multiple trainers and configurations.</span></span> <span data-ttu-id="09b6e-191">O tempo configurado poderá ser excedido se o tempo fornecido for muito curto (digamos, dois segundos) para uma única iteração.</span><span class="sxs-lookup"><span data-stu-id="09b6e-191">The configured time may be exceeded if the provided time is too short (say 2 seconds) for a single iteration.</span></span> <span data-ttu-id="09b6e-192">Nesse caso, o tempo real é o tempo necessário para produzir uma configuração de modelo em uma única iteração.</span><span class="sxs-lookup"><span data-stu-id="09b6e-192">In this case, the actual time is the required time to produce one model configuration in a single iteration.</span></span>

<span data-ttu-id="09b6e-193">O tempo necessário para iterações pode variar, dependendo do tamanho do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="09b6e-193">The needed time for iterations can vary depending on the size of the dataset.</span></span>

----------------------------------------------------------

<span data-ttu-id="09b6e-194">`--cache | -c` (string)</span><span class="sxs-lookup"><span data-stu-id="09b6e-194">`--cache | -c` (string)</span></span>

<span data-ttu-id="09b6e-195">Se você usar o armazenamento em cache, o conjunto de dados de treinamento inteiro será carregado na memória.</span><span class="sxs-lookup"><span data-stu-id="09b6e-195">If you use caching, the whole training dataset will be loaded in-memory.</span></span>

<span data-ttu-id="09b6e-196">Para conjuntos de dados pequenos e médios, usar o cache pode melhorar drasticamente o desempenho de treinamento, o que significa que o tempo de treinamento pode ser menor do que quando você não usa o cache.</span><span class="sxs-lookup"><span data-stu-id="09b6e-196">For small and medium datasets, using cache can drastically improve the training performance, meaning the training time can be shorter than when you don't use cache.</span></span>

<span data-ttu-id="09b6e-197">No entanto, para grandes conjuntos de dados, carregar todos os dados na memória pode ter um efeito negativo, pois você poderá ficar com memória insuficiente.</span><span class="sxs-lookup"><span data-stu-id="09b6e-197">However, for large datasets, loading all the data in memory can impact negatively since you might get out of memory.</span></span> <span data-ttu-id="09b6e-198">Ao treinar com arquivos de conjunto de dados grandes sem usar o cache, o ML.NET transmitirá partes de dados da unidade quando ele precisar carregar mais dados durante o treinamento.</span><span class="sxs-lookup"><span data-stu-id="09b6e-198">When training with large dataset files and not using cache, ML.NET will be streaming chunks of data from the drive when it needs to load more data while training.</span></span>

<span data-ttu-id="09b6e-199">Você pode especificar os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="09b6e-199">You can specify the following values:</span></span>

<span data-ttu-id="09b6e-200">`on`: Força o cache a ser usado durante o treinamento.</span><span class="sxs-lookup"><span data-stu-id="09b6e-200">`on`: Forces cache to be used when training.</span></span>
<span data-ttu-id="09b6e-201">`off`: Força o cache a não ser usado durante o treinamento.</span><span class="sxs-lookup"><span data-stu-id="09b6e-201">`off`: Forces cache not to be used when training.</span></span>
<span data-ttu-id="09b6e-202">`auto`: Dependendo da heurística de AutoML, o cache será usado ou não.</span><span class="sxs-lookup"><span data-stu-id="09b6e-202">`auto`: Depending on AutoML heuristics, the cache will be used or not.</span></span> <span data-ttu-id="09b6e-203">Em geral, conjuntos de dados pequenos/médios usarão o cache e grandes conjuntos de dados não usarão o cache se você usar a escolha `auto`.</span><span class="sxs-lookup"><span data-stu-id="09b6e-203">Usually, small/medium datasets will use cache and large datasets won't use cache if you use the `auto` choice.</span></span>

<span data-ttu-id="09b6e-204">Se você não especificar o parâmetro `--cache`, a configuração de cache `auto` será usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="09b6e-204">If you don't specify the `--cache` parameter, then the cache `auto` configuration will be used by default.</span></span>

----------------------------------------------------------

<span data-ttu-id="09b6e-205">`--name | -N` (string)</span><span class="sxs-lookup"><span data-stu-id="09b6e-205">`--name | -N` (string)</span></span>

<span data-ttu-id="09b6e-206">O nome para a solução ou projeto de saída criado.</span><span class="sxs-lookup"><span data-stu-id="09b6e-206">The name for the created output project or solution.</span></span> <span data-ttu-id="09b6e-207">Se nenhum nome for especificado, o nome `sample-{mltask}` será usado.</span><span class="sxs-lookup"><span data-stu-id="09b6e-207">If no name is specified, the name `sample-{mltask}` is used.</span></span>

<span data-ttu-id="09b6e-208">O arquivo de modelo do ML.NET (arquivo zip) também receberá o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="09b6e-208">The ML.NET model file (.ZIP file) will get the same name, as well.</span></span>

----------------------------------------------------------

<span data-ttu-id="09b6e-209">`--output-path | -o` (string)</span><span class="sxs-lookup"><span data-stu-id="09b6e-209">`--output-path | -o` (string)</span></span>

<span data-ttu-id="09b6e-210">Local/pasta raiz para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="09b6e-210">Root location/folder to place the generated output.</span></span> <span data-ttu-id="09b6e-211">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="09b6e-211">The default is the current directory.</span></span>

----------------------------------------------------------

<span data-ttu-id="09b6e-212">`--verbosity | -V` (string)</span><span class="sxs-lookup"><span data-stu-id="09b6e-212">`--verbosity | -V` (string)</span></span>

<span data-ttu-id="09b6e-213">Define o nível de detalhamento da saída padrão.</span><span class="sxs-lookup"><span data-stu-id="09b6e-213">Sets the verbosity level of the standard output.</span></span>

<span data-ttu-id="09b6e-214">Os valores permitidos são:</span><span class="sxs-lookup"><span data-stu-id="09b6e-214">Allowed values are:</span></span>

- `q[uiet]`
- <span data-ttu-id="09b6e-215">`m[inimal]` (por padrão)</span><span class="sxs-lookup"><span data-stu-id="09b6e-215">`m[inimal]`  (by default)</span></span>
- <span data-ttu-id="09b6e-216">`diag[nostic]` (nível de informações de registro em log)</span><span class="sxs-lookup"><span data-stu-id="09b6e-216">`diag[nostic]` (logging information level)</span></span>

<span data-ttu-id="09b6e-217">Por padrão, a ferramenta da CLI deve mostrar alguns comentários mínimos (mínimo) quando estiver funcionando, por exemplo, mencionar que ela está funcionando e, se possível, quanto tempo falta ou que percentual do tempo foi concluído.</span><span class="sxs-lookup"><span data-stu-id="09b6e-217">By default, the CLI tool should show some minimum feedback (minimal) when working, such as mentioning that it is working and if possible how much time is left or what % of the time is completed.</span></span>

----------------------------------------------------------

`-h|--help`

<span data-ttu-id="09b6e-218">Imprime uma ajuda para o comando com uma descrição para o parâmetro de cada comando.</span><span class="sxs-lookup"><span data-stu-id="09b6e-218">Prints out help for the command with a description for each command's parameter.</span></span>

----------------------------------------------------------

## <a name="see-also"></a><span data-ttu-id="09b6e-219">Consulte também</span><span class="sxs-lookup"><span data-stu-id="09b6e-219">See also</span></span>

- [<span data-ttu-id="09b6e-220">Como instalar a ferramenta de CLI do ML.NET</span><span class="sxs-lookup"><span data-stu-id="09b6e-220">How to install the ML.NET CLI tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="09b6e-221">Automatizar o treinamento de modelos com a CLI do ML.NET</span><span class="sxs-lookup"><span data-stu-id="09b6e-221">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="09b6e-222">Tutorial: Geração automática de um classificador binário usando a CLI do ML.NET</span><span class="sxs-lookup"><span data-stu-id="09b6e-222">Tutorial: Auto generate a binary classifier using the ML.NET CLI</span></span>](../tutorials/mlnet-cli.md)
- [<span data-ttu-id="09b6e-223">Telemetria na CLI do ML.NET</span><span class="sxs-lookup"><span data-stu-id="09b6e-223">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
