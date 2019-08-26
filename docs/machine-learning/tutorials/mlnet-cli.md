---
title: Geração automática de um classificador binário usando a CLI do ML.NET
description: Gerar automaticamente um modelo de ML e o código C# relacionado de um conjunto de dados de exemplo
author: cesardl
ms.author: cesardl
ms.date: 04/24/2019
ms.custom: mvc
ms.topic: tutorial
ms.openlocfilehash: 403b1759164d588cb5af49c6cb05e001b030235f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963599"
---
# <a name="auto-generate-a-binary-classifier-using-the-cli"></a><span data-ttu-id="ca3ba-103">Gerar automaticamente um classificador binário usando a CLI</span><span class="sxs-lookup"><span data-stu-id="ca3ba-103">Auto generate a binary classifier using the CLI</span></span>

<span data-ttu-id="ca3ba-104">Saiba como usar a CLI do ML.NET para gerar automaticamente um modelo do ML.NET e o código C# subjacente.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-104">Learn how to use ML.NET CLI to automatically generate an ML.NET model and underlying C# code.</span></span> <span data-ttu-id="ca3ba-105">Você fornece o conjunto de dados e a tarefa de aprendizado de máquina que deseja implementar e a CLI usa o mecanismo de AutoML para criar o código-fonte de implantação e geração de modelo, bem como o modelo binário.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-105">You provide your dataset and the machine learning task you want to implement, and the CLI uses the AutoML engine to create model generation and deployment source code, as well as the binary model.</span></span>

<span data-ttu-id="ca3ba-106">Neste tutorial, você realizará as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="ca3ba-106">In this tutorial, you will do the following steps:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="ca3ba-107">Preparar os dados para a tarefa de aprendizado de máquina selecionada</span><span class="sxs-lookup"><span data-stu-id="ca3ba-107">Prepare your data for the selected machine learning task</span></span>
> * <span data-ttu-id="ca3ba-108">Executar o comando 'mlnet auto-train' da CLI</span><span class="sxs-lookup"><span data-stu-id="ca3ba-108">Run the 'mlnet auto-train' command from the CLI</span></span>
> * <span data-ttu-id="ca3ba-109">Examinar os resultados de métrica de qualidade</span><span class="sxs-lookup"><span data-stu-id="ca3ba-109">Review the quality metric results</span></span>
> * <span data-ttu-id="ca3ba-110">Entender o código C# gerado para usar o modelo em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="ca3ba-110">Understand the generated C# code to use the model in your application</span></span>
> * <span data-ttu-id="ca3ba-111">Explorar o código C# gerado que foi usado para treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="ca3ba-111">Explore the generated C# code that was used to train the model</span></span>

> [!NOTE]
> <span data-ttu-id="ca3ba-112">Este tópico refere-se à ferramenta de CLI do ML.NET que está atualmente em versão prévia. O material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-112">This topic refers to the ML.NET CLI tool, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="ca3ba-113">Para obter mais informações, visite [a introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="ca3ba-113">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="ca3ba-114">A CLI do ML.NET faz parte do ML.NET e sua meta principal é "democratizar" o ML.NET, durante seu aprendizado, para desenvolvedores do .NET, de modo que você não precise escrever o código do zero para começar a usar.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-114">The ML.NET CLI is part of ML.NET and its main goal is to "democratize" ML.NET for .NET developers when learning ML.NET so you don't need to code from scratch to get started.</span></span>

<span data-ttu-id="ca3ba-115">Você pode executar a CLI do ML.NET em qualquer prompt de comando (Windows, Mac ou Linux) para gerar modelos do ML.NET de boa qualidade e código-fonte com base em conjuntos de dados de treinamento que você fornecer.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-115">You can run the ML.NET CLI on any command-prompt (Windows, Mac, or Linux) to generate good quality ML.NET models and source code based on training datasets you provide.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="ca3ba-116">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ca3ba-116">Pre-requisites</span></span>

- <span data-ttu-id="ca3ba-117">[SDK do .NET Core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2) ou posterior</span><span class="sxs-lookup"><span data-stu-id="ca3ba-117">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) or later</span></span>
- <span data-ttu-id="ca3ba-118">(Opcional) [Visual Studio 2017 ou 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="ca3ba-118">(Optional) [Visual Studio 2017 or 2019](https://visualstudio.microsoft.com/vs/)</span></span>
- [<span data-ttu-id="ca3ba-119">CLI do ML.NET</span><span class="sxs-lookup"><span data-stu-id="ca3ba-119">ML.NET CLI</span></span>](../how-to-guides/install-ml-net-cli.md)

<span data-ttu-id="ca3ba-120">Você pode executar os projetos de C# gerados do Visual Studio ou com o `dotnet run` (CLI do .NET Core).</span><span class="sxs-lookup"><span data-stu-id="ca3ba-120">You can either run the generated C# code projects from Visual Studio or with `dotnet run` (.NET Core CLI).</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="ca3ba-121">Preparar seus dados</span><span class="sxs-lookup"><span data-stu-id="ca3ba-121">Prepare your data</span></span>

<span data-ttu-id="ca3ba-122">Usaremos um conjunto de dados existente usado para um cenário de 'análise de sentimento ', que é uma tarefa de aprendizado de máquina de classificação binária.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-122">We are going to use an existing dataset used for a 'Sentiment Analysis' scenario, which is a binary classification machine learning task.</span></span> <span data-ttu-id="ca3ba-123">Você poderá usar seu próprio conjunto de dados de maneira semelhante, sendo que o modelo e o código serão gerados para você.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-123">You can use your own dataset in a similar way, and the model and code will be generated for you.</span></span>

1. <span data-ttu-id="ca3ba-124">Baixe [o arquivo zip do conjunto de dados de frases rotuladas por sentimento do UCI (consulte citações na observação abaixo)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) e descompacte-o na pasta que você escolher.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-124">Download [The UCI Sentiment Labeled Sentences dataset zip file (see citations in the following note)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip it on any folder you choose.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ca3ba-125">Os conjuntos de dados neste tutorial usam um conjunto de dados de 'From Group to Individual Labels using Deep Features' (de grupo para rótulos individuais usando recursos aprofundados), Kotzias et al.,</span><span class="sxs-lookup"><span data-stu-id="ca3ba-125">The datasets this tutorial uses a dataset from the 'From Group to Individual Labels using Deep Features', Kotzias et al,.</span></span> <span data-ttu-id="ca3ba-126">KDD 2015, e hospedados no UCI Machine Learning Repository – Dua, D. e Karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="ca3ba-126">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="ca3ba-127">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml ].</span><span class="sxs-lookup"><span data-stu-id="ca3ba-127">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="ca3ba-128">Irvine, CA: University of California, School of Information and Computer Science.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-128">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

2. <span data-ttu-id="ca3ba-129">Copie o arquivo `yelp_labelled.txt` em qualquer pasta que você criou anteriormente (assim como `/cli-test`).</span><span class="sxs-lookup"><span data-stu-id="ca3ba-129">Copy the `yelp_labelled.txt` file into any folder you previously created (such as `/cli-test`).</span></span>

3. <span data-ttu-id="ca3ba-130">Abra o prompt de comando preferido e mova-o para a pasta em que você copiou o arquivo de conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-130">Open your preferred command prompt and move to the folder where you copied the dataset file.</span></span> <span data-ttu-id="ca3ba-131">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="ca3ba-131">For example:</span></span>

    ```console
    > cd /cli-test
    ```

    <span data-ttu-id="ca3ba-132">Usando qualquer editor de texto, por exemplo, o Visual Studio Code, você pode abrir e explorar o arquivo de conjunto de dados `yelp_labelled.txt`.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-132">Using any text editor such as Visual Studio Code, you can open, and explore the `yelp_labelled.txt` dataset file.</span></span> <span data-ttu-id="ca3ba-133">Você pode ver que a estrutura é:</span><span class="sxs-lookup"><span data-stu-id="ca3ba-133">You can see that the structure is:</span></span>

    - <span data-ttu-id="ca3ba-134">O arquivo não tem cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-134">The file has no header.</span></span> <span data-ttu-id="ca3ba-135">Você usará o índice da coluna.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-135">You will use the column's index.</span></span>

    - <span data-ttu-id="ca3ba-136">Há apenas duas colunas:</span><span class="sxs-lookup"><span data-stu-id="ca3ba-136">There are just two columns:</span></span>

        | <span data-ttu-id="ca3ba-137">Texto (índice de coluna 0)</span><span class="sxs-lookup"><span data-stu-id="ca3ba-137">Text (Column index 0)</span></span> | <span data-ttu-id="ca3ba-138">Rótulo (índice de coluna 1)</span><span class="sxs-lookup"><span data-stu-id="ca3ba-138">Label (Column index 1)</span></span>|
        |--------------------------|-------|
        | <span data-ttu-id="ca3ba-139">Puxa! Adorei esse lugar.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-139">Wow... Loved this place.</span></span> | <span data-ttu-id="ca3ba-140">1</span><span class="sxs-lookup"><span data-stu-id="ca3ba-140">1</span></span> |
        | <span data-ttu-id="ca3ba-141">A torrada não é boa.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-141">Crust is not good.</span></span> | <span data-ttu-id="ca3ba-142">0</span><span class="sxs-lookup"><span data-stu-id="ca3ba-142">0</span></span> |
        | <span data-ttu-id="ca3ba-143">Não é saboroso e a textura é simplesmente horrível.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-143">Not tasty and the texture was just nasty.</span></span> | <span data-ttu-id="ca3ba-144">0</span><span class="sxs-lookup"><span data-stu-id="ca3ba-144">0</span></span> |
        | <span data-ttu-id="ca3ba-145">... MUITAS OUTRAS LINHAS DE TEXTO...</span><span class="sxs-lookup"><span data-stu-id="ca3ba-145">...MANY MORE TEXT ROWS...</span></span> | <span data-ttu-id="ca3ba-146">...(1 ou 0)...</span><span class="sxs-lookup"><span data-stu-id="ca3ba-146">...(1 or 0)...</span></span> |

    <span data-ttu-id="ca3ba-147">Feche o arquivo de conjunto de dados do editor.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-147">Make sure you close the dataset file from the editor.</span></span>

    <span data-ttu-id="ca3ba-148">Agora, você está pronto para começar a usar a CLI para esse cenário de 'análise de sentimento'.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-148">Now, you are ready to start using the CLI for this 'Sentiment Analysis' scenario.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ca3ba-149">Depois de concluir este tutorial, você também pode experimentar com seus próprios conjuntos de dados enquanto eles estão prontos para ser usados para qualquer uma das tarefas de ML atualmente compatíveis com a versão prévia da CLI do ML.NET, que são *'Classificação binária', 'Classificação multiclasse' e ' Regressão'* .</span><span class="sxs-lookup"><span data-stu-id="ca3ba-149">After finishing this tutorial you can also try with your own datasets as long as they are ready to be used for any of the ML tasks currently supported by the ML.NET CLI Preview which are *'Binary Classification', 'Multi-class Classification' and 'Regression'*).</span></span>

## <a name="run-the-mlnet-auto-train-command"></a><span data-ttu-id="ca3ba-150">Execute o comando 'mlnet auto-train'</span><span class="sxs-lookup"><span data-stu-id="ca3ba-150">Run the 'mlnet auto-train' command</span></span>

1. <span data-ttu-id="ca3ba-151">Execute o comando da CLI do ML.NET a seguir:</span><span class="sxs-lookup"><span data-stu-id="ca3ba-151">Run the following ML.NET CLI command:</span></span>

    ```console
    > mlnet auto-train --task binary-classification --dataset "yelp_labelled.txt" --label-column-index 1 --has-header false --max-exploration-time 10
    ```

    <span data-ttu-id="ca3ba-152">Esse comando executa o **comando `mlnet auto-train`** :</span><span class="sxs-lookup"><span data-stu-id="ca3ba-152">This command runs the **`mlnet auto-train` command**:</span></span>
    - <span data-ttu-id="ca3ba-153">para uma **tarefa de ML** do tipo **`binary-classification`**</span><span class="sxs-lookup"><span data-stu-id="ca3ba-153">for an **ML task** of type **`binary-classification`**</span></span>
    - <span data-ttu-id="ca3ba-154">usa o **arquivo de conjunto de dados `yelp_labelled.txt`** como treinamento e teste do conjunto de dados (internamente, a CLI usará a validação cruzada ou será dividida em dois conjuntos de dados, um para treinamento e outro para teste)</span><span class="sxs-lookup"><span data-stu-id="ca3ba-154">uses the **dataset file `yelp_labelled.txt`** as training and testing dataset (internally the CLI will either use cross-validation or split it in two datasets, one for training and one for testing)</span></span>
    - <span data-ttu-id="ca3ba-155">em que a **coluna de destino/objetivo** que você deseja prever (comumente chamada de **'Rótulo'** ) é a coluna **com o índice 1** (que é a segunda coluna, já que o índice é baseado em zero )</span><span class="sxs-lookup"><span data-stu-id="ca3ba-155">where the **objective/target column** you want to predict (commonly called **'label'**) is the **column with index 1** (that is the second column, since the index is zero-based)</span></span>
    - <span data-ttu-id="ca3ba-156">**não usa um cabeçalho de arquivo** com nomes de coluna, pois esse arquivo de conjunto de dados específico não tem um cabeçalho</span><span class="sxs-lookup"><span data-stu-id="ca3ba-156">does **not use a file header** with column names since this particular dataset file doesn't have a header</span></span>
    - <span data-ttu-id="ca3ba-157">o **tempo de exploração de destino** para o experimento é de **10 segundos**</span><span class="sxs-lookup"><span data-stu-id="ca3ba-157">the **targeted exploration time** for the experiment is **10 seconds**</span></span>

    <span data-ttu-id="ca3ba-158">Você verá a saída da CLI, semelhante a:</span><span class="sxs-lookup"><span data-stu-id="ca3ba-158">You will see output from the CLI, similar to:</span></span>

    <!-- markdownlint-disable MD023 -->
    # <a name="windowstabwindows"></a>[<span data-ttu-id="ca3ba-159">Windows</span><span class="sxs-lookup"><span data-stu-id="ca3ba-159">Windows</span></span>](#tab/windows)

    ![Treinamento automático da CLI do ML.NET no PowerShell](./media/mlnet-cli/mlnet-auto-train-binary-classification-powershell.gif)

    # <a name="macos-bashtabmacosbash"></a>[<span data-ttu-id="ca3ba-161">Bash do macOS</span><span class="sxs-lookup"><span data-stu-id="ca3ba-161">macOS Bash</span></span>](#tab/macosbash)

    ![Treinamento automático da CLI do ML.NET no PowerShell](./media/mlnet-cli/mlnet-auto-train-binary-classification-bash.gif)

    <span data-ttu-id="ca3ba-163">Nesse caso específico, em apenas 10 segundos e com um pequeno conjunto de dados fornecido, a ferramenta da CLI foi capaz de executar um número considerável de iterações, o que significa que o treinamento foi realizado várias vezes com base em diferentes combinações de algoritmos/configuração com diferentes transformações de dados internos e hiperparâmetros de algoritmo.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-163">In this particular case, in only 10 seconds and with the small dataset provided, the CLI tool was able to run quite a few iterations, meaning training multiple times based on different combinations of algorithms/configuration with different internal data transformations and algorithm's hyper-parameters.</span></span> 

    <span data-ttu-id="ca3ba-164">Por fim, o modelo de "melhor qualidade" encontrado em 10 segundos é um modelo usando um treinador/algoritmo específico com qualquer configuração específica.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-164">Finally, the "best quality" model found in 10 seconds is a model using a particular trainer/algorithm with any specific configuration.</span></span> <span data-ttu-id="ca3ba-165">Dependendo do tempo de exploração, o comando pode produzir um resultado diferente.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-165">Depending on the exploration time, the command can produce a different result.</span></span> <span data-ttu-id="ca3ba-166">A seleção é baseada nas várias métricas mostradas, tais como `Accuracy`.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-166">The selection is based on the multiple metrics shown, such as `Accuracy`.</span></span>

    <span data-ttu-id="ca3ba-167">**Noções básicas sobre as métricas de qualidade do modelo**</span><span class="sxs-lookup"><span data-stu-id="ca3ba-167">**Understanding the model's quality metrics**</span></span>

    <span data-ttu-id="ca3ba-168">A primeira e mais fácil métrica para avaliar um modelo de classificação binária é a precisão, o que é simples de entender.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-168">The first and easiest metric to evaluate a binary-classification model is the accuracy, which is simple to understand.</span></span> <span data-ttu-id="ca3ba-169">"Precisão é a proporção de previsões corretas com um conjunto de dados de teste."</span><span class="sxs-lookup"><span data-stu-id="ca3ba-169">"Accuracy is the proportion of correct predictions with a test data set.".</span></span> <span data-ttu-id="ca3ba-170">Quanto mais próximo de 100% (1,00), melhor.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-170">The closer to 100% (1.00), the better.</span></span>

    <span data-ttu-id="ca3ba-171">No entanto, há casos em que apenas medir com a métrica de precisão não é suficiente, especialmente quando o rótulo (0 e 1 neste caso) é desbalanceado no conjunto de dados de teste.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-171">However, there are cases where just measuring with the Accuracy metric is not enough, especially when the label (0 and 1 in this case) is unbalanced in the test dataset.</span></span>

    <span data-ttu-id="ca3ba-172">Para obter métricas adicionais e muito mais **informações detalhadas sobre as métricas** (tais como precisão, AUC, AUCPR, pontuação F1) usadas para avaliar os modelos diferentes, você pode ler [Noções básicas sobre métricas do ML.NET](../resources/metrics.md)</span><span class="sxs-lookup"><span data-stu-id="ca3ba-172">For additional metrics and more **detailed information about the metrics** such as Accuracy, AUC, AUCPR, F1-score used to evaluate the different models, you can read [Understanding ML.NET metrics](../resources/metrics.md)</span></span>

    > [!NOTE]
    > <span data-ttu-id="ca3ba-173">Você pode experimentar esse mesmo conjunto de dados e especificar alguns minutos para `--max-exploration-time` (por exemplo, três minutos, então você especifica 180 segundos) que encontrará um "melhor modelo" para você com uma configuração de pipeline de treinamento diferente para esse conjunto de dados (que é bem pequeno, 1.000 linhas).</span><span class="sxs-lookup"><span data-stu-id="ca3ba-173">You can try this very same dataset and specify a few minutes for `--max-exploration-time` (for instance three minutes so you specify 180 seconds) which will find a better "best model" for you with a different training pipeline configuration for this dataset (which is pretty small, 1000 rows).</span></span> 
        
    <span data-ttu-id="ca3ba-174">Para localizar um modelo de "melhor/boa qualidade" que é um "modelo de produção" destinado a conjuntos de dados maiores, você deve fazer experimentos com a CLI, geralmente especificando muito mais tempo de exploração, dependendo do tamanho do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-174">In order to find a "best/good quality" model that is a "production-ready model" targeting larger datasets, you should make experiments with the CLI usually specifying much more exploration time depending on the size of the dataset.</span></span> <span data-ttu-id="ca3ba-175">Na verdade, em muitos casos você poderá exigir várias horas de tempo de exploração, especialmente se o conjunto de dados for grande em linhas e colunas.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-175">In fact, in many cases you might require multiple hours of exploration time especially if the dataset is large on rows and columns.</span></span> 

1. <span data-ttu-id="ca3ba-176">A execução do comando anterior gerou os seguintes ativos:</span><span class="sxs-lookup"><span data-stu-id="ca3ba-176">The previous command execution has generated the following assets:</span></span>

    - <span data-ttu-id="ca3ba-177">Um modelo serializado. zip ("melhor modelo") pronto para uso.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-177">A serialized model .zip ("best model") ready to use.</span></span> 
    - <span data-ttu-id="ca3ba-178">Código C# para a execução/pontuação que gerou o modelo (para fazer previsões em seus aplicativos do usuário final com esse modelo).</span><span class="sxs-lookup"><span data-stu-id="ca3ba-178">C# code to run/score that generated model (To make predictions in your end-user apps with that model).</span></span>
    - <span data-ttu-id="ca3ba-179">Código de treinamento C# usado para gerar o modelo (para fins de aprendizado).</span><span class="sxs-lookup"><span data-stu-id="ca3ba-179">C# training code used to generate that model (Learning purposes).</span></span>
    - <span data-ttu-id="ca3ba-180">Um arquivo de log com todas as iterações exploradas, tendo específicas informações detalhadas sobre cada algoritmo tentado com a respectiva combinação de hiperparâmetros e transformações de dados.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-180">A log file with all the iterations explored having specific detailed information about each algorithm tried with its combination of hyper-parameters and data transformations.</span></span> 

    <span data-ttu-id="ca3ba-181">Os primeiros dois ativos (modelo de arquivo zip e código C# a executar) podem ser usados diretamente em seus aplicativos de usuário final (aplicativo Web ASP.NET Core, serviços, aplicativo da Área de Trabalho etc.) para fazer previsões com esse modelo de ML gerado.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-181">The first two assets (.ZIP file model and C# code to run that model) can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

    <span data-ttu-id="ca3ba-182">O terceiro ativo, o código de treinamento, mostra a você que o código de API do ML.NET foi usado pela CLI para treinar o modelo gerado, de modo que você pode investigar qual treinador/algoritmo e parâmetros específicos foram selecionados pela CLI.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-182">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate what specific trainer/algorithm and hyper-parameters were selected by the CLI.</span></span>

<span data-ttu-id="ca3ba-183">Esses ativos enumerados são explicados nas etapas do tutorial a seguir.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-183">Those enumerated assets are explained in the following steps of the tutorial.</span></span>

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a><span data-ttu-id="ca3ba-184">Explore o código C# gerado a usar para executar o modelo para fazer previsões</span><span class="sxs-lookup"><span data-stu-id="ca3ba-184">Explore the generated C# code to use for running the model to make predictions</span></span>

1. <span data-ttu-id="ca3ba-185">No Visual Studio (2017 ou 2019), abra a solução gerada na pasta denominada `SampleBinaryClassification` dentro da pasta de destino original (no tutorial, foi nomeada `/cli-test`).</span><span class="sxs-lookup"><span data-stu-id="ca3ba-185">In Visual Studio (2017 or 2019) open the solution generated in the folder named `SampleBinaryClassification` within your original destination folder (in the tutorial was named `/cli-test`).</span></span> <span data-ttu-id="ca3ba-186">Você deve ver uma solução semelhante a:</span><span class="sxs-lookup"><span data-stu-id="ca3ba-186">You should see a solution similar to:</span></span>

    > [!NOTE]
    > <span data-ttu-id="ca3ba-187">No tutorial, sugerimos usar o Visual Studio, mas você também pode explorar o código C# gerado (dois projetos) com qualquer editor de texto e executar o aplicativo de console gerado com o `dotnet CLI` no computador macOS, Linux ou Windows.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-187">In the tutorial we suggest to use Visual Studio, but you can also explore the generated C# code (two projects) with any text editor and run the generated console app with the `dotnet CLI` on macOS, Linux or Windows machine.</span></span>

    ![Solução de VS gerada pela CLI](./media/mlnet-cli/generated-csharp-solution-detailed.png)

    - <span data-ttu-id="ca3ba-189">A **biblioteca de classes** gerada que contém o modelo de ML serializado (arquivo .zip) e as classes de dados (modelos de dados) é algo que você pode usar diretamente em seu aplicativo de usuário final, até mesmo referenciando diretamente essa biblioteca de classes (ou movendo o código, como preferir).</span><span class="sxs-lookup"><span data-stu-id="ca3ba-189">The generated **class library** containing the serialized ML model (.zip file) and the data classes (data models) is something you can directly use in your end-user application, even by directly referencing that class library (or moving the code, as you prefer).</span></span>
    - <span data-ttu-id="ca3ba-190">O **aplicativo de console** gerado contém o código de execução que você precisa revisar e, em seguida, você geralmente reutiliza o 'código de pontuação' (código que executa o modelo de ML para fazer previsões), movendo o código simples (apenas algumas linhas) para seu aplicativo de usuário final em que você deseja fazer as previsões.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-190">The generated **console app** contains execution code that you must review and then you usually reuse the 'scoring code' (code that runs the ML model to make predictions) by moving that simple code (just a few lines) to your end-user application where you want to make the predictions.</span></span> 

1. <span data-ttu-id="ca3ba-191">Abra os arquivos de classe **ModelInput.cs** e **ModelOutput.cs** dentro do projeto de biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-191">Open the **ModelInput.cs** and **ModelOutput.cs** class files within the class library project.</span></span> <span data-ttu-id="ca3ba-192">Você verá que essas classes são 'classes de dados' ou classes POCO usadas para armazenar dados.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-192">You will see that these classes are 'data classes' or POCO classes used to hold data.</span></span> <span data-ttu-id="ca3ba-193">Trata-se de "código clichê", mas útil gerá-lo se o seu conjunto de dados tiver dezenas ou até mesmo centenas de colunas.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-193">It is 'boilerplate code' but useful to have it generated if your dataset has tens or even hundreds of columns.</span></span> 
    - <span data-ttu-id="ca3ba-194">A classe `ModelInput` é usada ao ler dados do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-194">The `ModelInput` class is used when reading data from the dataset.</span></span> 
    - <span data-ttu-id="ca3ba-195">A classe `ModelOutput` é usada para obter o resultado da previsão (dados de previsão).</span><span class="sxs-lookup"><span data-stu-id="ca3ba-195">The `ModelOutput` class is used to get the prediction result (prediction data).</span></span>

1. <span data-ttu-id="ca3ba-196">Abra o arquivo Program.cs e explore o código.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-196">Open the Program.cs file and explore the code.</span></span> <span data-ttu-id="ca3ba-197">Em apenas algumas linhas, você pode executar o modelo e fazer uma previsão de exemplo.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-197">In just a few lines, you are able to run the model and make a sample prediction.</span></span>

    ```csharp
    static void Main(string[] args)
    {
        MLContext mlContext = new MLContext();

        // Training code used by ML.NET CLI and AutoML to generate the model
        //ModelBuilder.CreateModel();

        ITransformer mlModel = mlContext.Model.Load(MODEL_FILEPATH, out DataViewSchema inputSchema);
        var predEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(mlModel);

        // Create sample data to do a single prediction with it 
        ModelInput sampleData = CreateSingleDataSample(mlContext, DATA_FILEPATH);

        // Try a single prediction
        ModelOutput predictionResult = predEngine.Predict(sampleData);

        Console.WriteLine($"Single Prediction --> Actual value: {sampleData.Label} | Predicted value: {predictionResult.Prediction}");
    }
    ```

- <span data-ttu-id="ca3ba-198">A primeira linha de código simplesmente cria um objeto `MLContext` necessário sempre que você executa o código do ML.NET.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-198">The first line of code simply creates an `MLContext` object needed whenever you run ML.NET code.</span></span> 

- <span data-ttu-id="ca3ba-199">A segunda linha de código é comentada porque você não precisa treinar o modelo, já que ele já foi treinado para você pela ferramenta de CLI e salvo no arquivo zip serializado do modelo.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-199">The second line of code is commented because you don't need to train the model since it was already trained for you by the CLI tool and saved into the model's serialized .ZIP file.</span></span> <span data-ttu-id="ca3ba-200">Mas se quiser ver *"como o modelo foi treinado"* pela CLI, você poderá remover as marcas de comentários dessa linha e executar/depurar o código de treinamento usado por esse modelo de ML específico.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-200">But if you want to see *"how the model was trained"* by the CLI, you could uncomment that line and run/debug the training code used for that particular ML model.</span></span>

- <span data-ttu-id="ca3ba-201">Na terceira linha de código, você pode carregar o modelo do arquivo zip do modelo serializado com a API `mlContext.Model.Load()`, fornecendo o caminho para esse arquivo zip de modelo.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-201">In the third line of code, you load the model from the serialized model .ZIP file with the `mlContext.Model.Load()` API by providing the path to that model .ZIP file.</span></span>

- <span data-ttu-id="ca3ba-202">Na quarta linha de código que você carregar, crie o `PredictionEngine` do objeto com a API `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)`.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-202">In the fourth line of code you load create the `PredictionEngine` object with the `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)` API.</span></span> <span data-ttu-id="ca3ba-203">Você precisa do objeto `PredictionEngine` sempre que deseja fazer uma previsão visando um único exemplo de dados (nesse caso, uma única parte do texto para prever seu sentimento).</span><span class="sxs-lookup"><span data-stu-id="ca3ba-203">You need the `PredictionEngine` object whenever you want to make a prediction targeting a single sample of data (In this case, a single piece of text to predict its sentiment).</span></span>

- <span data-ttu-id="ca3ba-204">É na quinta linha de código que você cria esse *único dado de exemplo* a ser usado para a previsão chamando a função `CreateSingleDataSample()`.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-204">The fifth line of code is where you create that *single sample data* to be used for the prediction by calling the function `CreateSingleDataSample()`.</span></span> <span data-ttu-id="ca3ba-205">Já que a ferramenta da CLI não sabe que tipo de dados de exemplo usar, dentro dessa função, ela está carregando a primeira linha do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-205">Since the CLI tool doesn't know what kind of sample data to use, within that function it is loading the first row of the dataset.</span></span> <span data-ttu-id="ca3ba-206">No entanto, para esse caso, você também pode criar seus próprios dados embutidos em código em vez da implementação atual da função `CreateSingleDataSample()`, atualizando esse código mais simples implementando essa função:</span><span class="sxs-lookup"><span data-stu-id="ca3ba-206">However, for this case you can also create you own 'hard-coded' data instead of the current implementation of the `CreateSingleDataSample()` function by updating this simpler code implementing that function:</span></span>

    ```csharp
    private static ModelInput CreateSingleDataSample()
    {
        ModelInput sampleForPrediction = new ModelInput() { Col0 = "The ML.NET CLI is great for getting started. Very cool!", Label = true };
        return sampleForPrediction;
    }
    ```

1. <span data-ttu-id="ca3ba-207">Execute o projeto, usando os dados de exemplo originais carregados da primeira linha do conjunto de dados ou fornecendo seus próprios dados de exemplo embutidos em código personalizados.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-207">Run the project, either using the original sample data loaded from the first row of the dataset or by providing your own custom hard-coded sample data.</span></span> <span data-ttu-id="ca3ba-208">Você deve obter uma previsão comparável a:</span><span class="sxs-lookup"><span data-stu-id="ca3ba-208">You should get a prediction comparable to:</span></span>

    # <a name="windowstabwindows"></a>[<span data-ttu-id="ca3ba-209">Windows</span><span class="sxs-lookup"><span data-stu-id="ca3ba-209">Windows</span></span>](#tab/windows)

    <span data-ttu-id="ca3ba-210">Execute o aplicativo de console do Visual Studio pressionando F5 (botão Reproduzir):</span><span class="sxs-lookup"><span data-stu-id="ca3ba-210">Run the console app from Visual Studio by hitting F5 (Play button):</span></span>

    ![Treinamento automático da CLI do ML.NET no PowerShell](./media/mlnet-cli/sample-cli-prediction-execution.png)<span data-ttu-id="ca3ba-212">)</span><span class="sxs-lookup"><span data-stu-id="ca3ba-212">)</span></span>

    # <a name="macos-bashtabmacosbash"></a>[<span data-ttu-id="ca3ba-213">Bash do macOS</span><span class="sxs-lookup"><span data-stu-id="ca3ba-213">macOS Bash</span></span>](#tab/macosbash)

    <span data-ttu-id="ca3ba-214">Execute o aplicativo de console do prompt de comando, digitando os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="ca3ba-214">Run the console app from the command-prompt by typing the following commands:</span></span>

     ```
     > cd SampleBinaryClassification
     > cd SampleBinaryClassification.ConsoleApp

     > dotnet run
     ```

    ![Treinamento automático da CLI do ML.NET no PowerShell](./media/mlnet-cli/sample-cli-prediction-execution-bash.png)<span data-ttu-id="ca3ba-216">)</span><span class="sxs-lookup"><span data-stu-id="ca3ba-216">)</span></span>

    ---

1. <span data-ttu-id="ca3ba-217">Tente alterar os dados de exemplo embutidos em código para outras frases com sentimento diferente e veja como o modelo prevê sentimento positivo ou negativo.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-217">Try changing the hard-coded sample data to other sentences with different sentiment and see how the model predicts positive or negative sentiment.</span></span> 

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a><span data-ttu-id="ca3ba-218">Introduza previsões do modelo de ML em seus aplicativos de usuário final</span><span class="sxs-lookup"><span data-stu-id="ca3ba-218">Infuse your end-user applications with ML model predictions</span></span>

<span data-ttu-id="ca3ba-219">Você pode usar um 'código de pontuação de modelo de ML' semelhante para executar o modelo em seu aplicativo de usuário final e fazer previsões.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-219">You can use similar 'ML model scoring code' to run the model in your end-user application and make predictions.</span></span> 

<span data-ttu-id="ca3ba-220">Por exemplo, você poderia mover diretamente esse código para qualquer aplicativo da Área de Trabalho do Windows (assim como **WPF** e **WinForms**) e executar o modelo da mesma maneira que isso foi feito no aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-220">For instance, you could directly move that code to any Windows desktop application such as **WPF** and **WinForms** and run the model in the same way than it was done in the console app.</span></span>

<span data-ttu-id="ca3ba-221">No entanto, a maneira como você implementa essas linhas de código para executar um modelo de ML deverá ser otimizada (isto é, armazenar o arquivo zip de modelo em cache e carregue-o uma vez) e ter objetos singleton em vez de criá-los em cada solicitação, especialmente se seu aplicativo precisar ser escalonável, assim como no caso de um aplicativo Web ou um serviço distribuído, conforme explicado na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-221">However, the way you implement those lines of code to run an ML model should be optimized (that is, cache the model .zip file and load it once) and have singleton objects instead of creating them on every request, especially if your application needs to be scalable such as a web application or distributed service, as explained in the following section.</span></span>

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a><span data-ttu-id="ca3ba-222">Como executar modelos do ML.NET em aplicativos Web ASP.NET Core e serviços escalonáveis (aplicativos multi-threaded)</span><span class="sxs-lookup"><span data-stu-id="ca3ba-222">Running ML.NET models in scalable ASP.NET Core web apps and services (multi-threaded apps)</span></span>

<span data-ttu-id="ca3ba-223">A criação do objeto de modelo (`ITransformer` carregado do arquivo zip de um modelo) e do objeto `PredictionEngine` deve ser otimizada, especialmente durante a execução em aplicativos Web escalonáveis e serviços distribuídos.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-223">The creation of the model object (`ITransformer` loaded from a model's .zip file) and the `PredictionEngine` object should be optimized especially when running on scalable web apps and distributed services.</span></span> <span data-ttu-id="ca3ba-224">No primeiro caso, a otimização do objeto de modelo (`ITransformer`) é simples.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-224">For the first case, the model object (`ITransformer`) the optimization is straightforward.</span></span> <span data-ttu-id="ca3ba-225">Já que o objeto `ITransformer` é thread-safe, você pode armazenar em cache o objeto como um singleton ou um objeto estático, de modo que você carregue o modelo uma vez.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-225">Since the `ITransformer` object is thread-safe, you can cache the object as a singleton or static object so you load the model once.</span></span>

<span data-ttu-id="ca3ba-226">Para o segundo objeto (`PredictionEngine`), isso não é tão fácil porque o objeto `PredictionEngine` não é thread-safe, portanto, você não pode instanciá-lo como singleton ou como um objeto estático em um aplicativo ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-226">For the second object, the `PredictionEngine` object, it is not so easy because the `PredictionEngine` object is not thread-safe, therefore you cannot instantiate this object as singleton or static object in an ASP.NET Core app.</span></span> <span data-ttu-id="ca3ba-227">Esse problema de thread-safe e escalabilidade é discutido em profundidade nesta [postagem no blog](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span><span class="sxs-lookup"><span data-stu-id="ca3ba-227">This thread-safe and scalability problem is deeply discussed in this [Blog Post](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span> 

<span data-ttu-id="ca3ba-228">No entanto, as coisas ficaram muito mais fáceis para você do que aquilo que é explicado nessa postagem no blog.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-228">However, things got a lot easier for you than what's explained in that blog post.</span></span> <span data-ttu-id="ca3ba-229">Trabalhamos em uma abordagem mais simples para você e criamos um ótimo **'Pacote de integração do .NET Core'** , que você pode usar facilmente em seus serviços e aplicativos ASP.NET Core registrando-o nos serviços de DI (injeção de dependência) do aplicativo e, em seguida, usando-o diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-229">We worked on a simpler approach for you and have created a nice **'.NET Core Integration Package'** that you can  easily use in your ASP.NET Core apps and services by registering it in the application DI services (Dependency Injection services) and then directly use it from your code.</span></span> <span data-ttu-id="ca3ba-230">Verifique o tutorial e exemplo a seguir para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="ca3ba-230">Check the following tutorial and example for doing that:</span></span>

- [<span data-ttu-id="ca3ba-231">Tutorial: Executando modelos do ML.NET em aplicativos Web e APIs Web escalonáveis do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ca3ba-231">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="ca3ba-232">Exemplo: Modelo do ML.NET escalonável na API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ca3ba-232">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a><span data-ttu-id="ca3ba-233">Explore o código C# gerado que foi usado para treinar o modelo de "melhor qualidade"</span><span class="sxs-lookup"><span data-stu-id="ca3ba-233">Explore the generated C# code that was used to train the "best quality" model</span></span> 

<span data-ttu-id="ca3ba-234">Para fins de aprendizado mais avançado, você também pode explorar o código C# gerado que foi usado pela ferramenta da CLI para treinar o modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-234">For more advanced learning purposes, you can also explore the generated C# code that was used by the CLI tool to train the generated model.</span></span>

<span data-ttu-id="ca3ba-235">Esse código de modelo de treinamento é gerado atualmente na classe personalizada gerada chamada `ModelBuilder`, de modo que você pode investigar esse código de treinamento.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-235">That 'training model code' is currently generated in the custom class generated named `ModelBuilder` so you can investigate that training code.</span></span>

<span data-ttu-id="ca3ba-236">Mais importante, para esse cenário específico (modelo de análise de sentimento) também é possível comparar esse código de treinamento gerado com o código explicado no tutorial a seguir:</span><span class="sxs-lookup"><span data-stu-id="ca3ba-236">More importantly, for this particular scenario (Sentiment Analysis model) you can also compare that generated training code with the code explained in the following tutorial:</span></span>

- <span data-ttu-id="ca3ba-237">Compare: [Tutorial: Use do ML.NET em um cenário de classificação binária de análise de sentimento](sentiment-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="ca3ba-237">Compare: [Tutorial: Use ML.NET in a sentiment analysis binary classification scenario](sentiment-analysis.md).</span></span>

<span data-ttu-id="ca3ba-238">É interessante comparar a configuração de pipeline e o algoritmo escolhido no tutorial com o código gerado pela ferramenta de CLI.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-238">It is interesting to compare the chosen algorithm and pipeline configuration in the tutorial with the code generated by the CLI tool.</span></span> <span data-ttu-id="ca3ba-239">Dependendo de quanto tempo você gasta em iteração e pesquisa por modelos melhores, o algoritmo escolhido pode ser diferente, juntamente com os respectivos hiperparâmetros e configuração de pipeline específicos.</span><span class="sxs-lookup"><span data-stu-id="ca3ba-239">Depending on how much time you spend iterating and searching for better models, the chosen algorithm might be different along with its particular hyper-parameters and pipeline configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca3ba-240">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca3ba-240">See also</span></span>

- [<span data-ttu-id="ca3ba-241">Automatizar o treinamento de modelos com a CLI do ML.NET</span><span class="sxs-lookup"><span data-stu-id="ca3ba-241">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="ca3ba-242">Tutorial: Executando modelos do ML.NET em aplicativos Web e APIs Web escalonáveis do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ca3ba-242">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="ca3ba-243">Exemplo: Modelo do ML.NET escalonável na API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ca3ba-243">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [<span data-ttu-id="ca3ba-244">Guia de referência de comando auto-train da CLI do ML.NET</span><span class="sxs-lookup"><span data-stu-id="ca3ba-244">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md) 
- [<span data-ttu-id="ca3ba-245">Como instalar a ferramenta da CLI (Interface de Linha de Comando) do ML.NET</span><span class="sxs-lookup"><span data-stu-id="ca3ba-245">How to install the ML.NET Command-Line Interface (CLI) tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="ca3ba-246">Telemetria na CLI do ML.NET</span><span class="sxs-lookup"><span data-stu-id="ca3ba-246">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)

## <a name="next-steps"></a><span data-ttu-id="ca3ba-247">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="ca3ba-247">Next steps</span></span>

<span data-ttu-id="ca3ba-248">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="ca3ba-248">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="ca3ba-249">Prepare seus dados para a tarefa de ML selecionada (problema a ser resolvido)</span><span class="sxs-lookup"><span data-stu-id="ca3ba-249">Prepare your data for the selected ML task (problem to solve)</span></span>
> * <span data-ttu-id="ca3ba-250">Execute o comando 'mlnet auto-train' na ferramenta de CLI</span><span class="sxs-lookup"><span data-stu-id="ca3ba-250">Run the 'mlnet auto-train' command in the CLI tool</span></span>
> * <span data-ttu-id="ca3ba-251">Examinar os resultados de métrica de qualidade</span><span class="sxs-lookup"><span data-stu-id="ca3ba-251">Review the quality metric results</span></span>
> * <span data-ttu-id="ca3ba-252">Entenda o código C# gerado para executar o modelo (o código para usar em seu aplicativo de usuário final)</span><span class="sxs-lookup"><span data-stu-id="ca3ba-252">Understand the generated C# code to run the model (Code to use in your end-user app)</span></span>
> * <span data-ttu-id="ca3ba-253">Explore o código C# gerado que foi usado para treinar o modelo de "melhor qualidade" (para fins de aprendizado)</span><span class="sxs-lookup"><span data-stu-id="ca3ba-253">Explore the generated C# code that was used to train the "best quality" model (Learning purposes)</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ca3ba-254">Automatizar o treinamento de modelos com a CLI do ML.NET</span><span class="sxs-lookup"><span data-stu-id="ca3ba-254">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
