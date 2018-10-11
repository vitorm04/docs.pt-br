---
title: Usar o ML.NET em um cenário de classificação binária de análise de sentimento
description: Descubra como usar o ML.NET em um cenário de classificação binária para entender como usar a previsão de sentimentos para executar a ação apropriada.
ms.date: 06/04/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7d2935fafe9dbad28205c8a896d97d80474a686f
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/29/2018
ms.locfileid: "47436135"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a><span data-ttu-id="11197-103">Tutorial: Usar o ML.NET em um cenário de classificação binária de análise de sentimento</span><span class="sxs-lookup"><span data-stu-id="11197-103">Tutorial: Use ML.NET in a sentiment analysis binary classification scenario</span></span>

> [!NOTE]
> <span data-ttu-id="11197-104">Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="11197-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="11197-105">Para obter mais informações, visite [a introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="11197-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="11197-106">Este tutorial de exemplo ilustra o uso do ML.NET para criar um classificador de sentimento por meio de um aplicativo de console do .NET Core usando C# no Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="11197-106">This sample tutorial illustrates using ML.NET to create a sentiment classifier via a .NET Core console application using C# in Visual Studio 2017.</span></span>

<span data-ttu-id="11197-107">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="11197-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="11197-108">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="11197-108">Understand the problem</span></span>
> * <span data-ttu-id="11197-109">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="11197-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="11197-110">Preparar seus dados</span><span class="sxs-lookup"><span data-stu-id="11197-110">Prepare your data</span></span>
> * <span data-ttu-id="11197-111">Criar o pipeline de aprendizado</span><span class="sxs-lookup"><span data-stu-id="11197-111">Create the learning pipeline</span></span>
> * <span data-ttu-id="11197-112">Carregar um classificador</span><span class="sxs-lookup"><span data-stu-id="11197-112">Load a classifier</span></span>
> * <span data-ttu-id="11197-113">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="11197-113">Train the model</span></span>
> * <span data-ttu-id="11197-114">Avaliar o modelo com um conjunto de dados diferente</span><span class="sxs-lookup"><span data-stu-id="11197-114">Evaluate the model with a different dataset</span></span>
> * <span data-ttu-id="11197-115">Prever os resultados dos dados de teste com o modelo</span><span class="sxs-lookup"><span data-stu-id="11197-115">Predict the test data outcomes with the model</span></span>

## <a name="sentiment-analysis-sample-overview"></a><span data-ttu-id="11197-116">Visão geral da amostra de análise de sentimento</span><span class="sxs-lookup"><span data-stu-id="11197-116">Sentiment analysis sample overview</span></span>

<span data-ttu-id="11197-117">A amostra é um aplicativo de console que usa o ML.NET para treinar um modelo que classifica e prevê o sentimento como positivo ou negativo.</span><span class="sxs-lookup"><span data-stu-id="11197-117">The sample is a console app that uses ML.NET to train a model that classifies and predicts sentiment as either positive or negative.</span></span> <span data-ttu-id="11197-118">Ele também avalia o modelo com um segundo conjunto de dados para análise de qualidade.</span><span class="sxs-lookup"><span data-stu-id="11197-118">It also evaluates the model with a second dataset for quality analysis.</span></span> <span data-ttu-id="11197-119">Os conjuntos de dados de sentimento são do projeto WikiDetox.</span><span class="sxs-lookup"><span data-stu-id="11197-119">The sentiment datasets are from the WikiDetox project.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="11197-120">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="11197-120">Prerequisites</span></span>

* <span data-ttu-id="11197-121">[Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="11197-121">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="11197-122">[Arquivo separado de guia de dados de linha detox da Wikipédia (wikiPedia-detox-250-line-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).</span><span class="sxs-lookup"><span data-stu-id="11197-122">The [Wikipedia detox line data tab separated file (wikiPedia-detox-250-line-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span>
* <span data-ttu-id="11197-123">[Arquivo separado de guia de teste de linha detox da Wikipédia (wikipedia-detox-250-line-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).</span><span class="sxs-lookup"><span data-stu-id="11197-123">The [Wikipedia detox line test tab separated file (wikipedia-detox-250-line-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="11197-124">Fluxo de trabalho de aprendizado de máquina</span><span class="sxs-lookup"><span data-stu-id="11197-124">Machine learning workflow</span></span>

<span data-ttu-id="11197-125">Este tutorial segue um fluxo de trabalho de aprendizado de máquina que permite que o processo se mova de maneira ordenada.</span><span class="sxs-lookup"><span data-stu-id="11197-125">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="11197-126">As fases do fluxo de trabalho são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="11197-126">The workflow phases are as follows:</span></span>

1. <span data-ttu-id="11197-127">**Compreender o problema**</span><span class="sxs-lookup"><span data-stu-id="11197-127">**Understand the problem**</span></span>
2. <span data-ttu-id="11197-128">**Ingerir dados**</span><span class="sxs-lookup"><span data-stu-id="11197-128">**Ingest the data**</span></span>
3. <span data-ttu-id="11197-129">**Pré-processamento de dados e engenharia de recursos**</span><span class="sxs-lookup"><span data-stu-id="11197-129">**Data preprocess and feature engineering**</span></span>
4. <span data-ttu-id="11197-130">**Treinar e prever o modelo**</span><span class="sxs-lookup"><span data-stu-id="11197-130">**Train and predict the model**</span></span>
5. <span data-ttu-id="11197-131">**Avaliar o modelo**</span><span class="sxs-lookup"><span data-stu-id="11197-131">**Evaluate the model**</span></span>
6. <span data-ttu-id="11197-132">**Operacionalização do modelo**</span><span class="sxs-lookup"><span data-stu-id="11197-132">**Model operationalization**</span></span>

### <a name="understand-the-problem"></a><span data-ttu-id="11197-133">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="11197-133">Understand the problem</span></span>

<span data-ttu-id="11197-134">Você primeiro precisa compreender o problema, para que possa dividi-lo em partes que possam oferecer suporte à criação e ao treinamento do modelo.</span><span class="sxs-lookup"><span data-stu-id="11197-134">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="11197-135">Dividir o problema permite prever e avaliar os resultados.</span><span class="sxs-lookup"><span data-stu-id="11197-135">Breaking the problem down allows you to predict and evaluate the results.</span></span>

<span data-ttu-id="11197-136">O problema deste tutorial é compreender o sentimento de comentário do site recebido para executar a ação apropriada.</span><span class="sxs-lookup"><span data-stu-id="11197-136">The problem for this tutorial is to understand incoming website comment sentiment to take the appropriate action.</span></span>

<span data-ttu-id="11197-137">Você pode dividir o problema com o texto de sentimento e o valor de sentimento para os dados com os quais deseja treinar o modelo e com um valor de sentimento previsto que você pode avaliar e usar operacionalmente.</span><span class="sxs-lookup"><span data-stu-id="11197-137">You can break down the problem to the sentiment text and sentiment value for the data you want to train the model with, and a predicted sentiment value that you can evaluate and then use operationally.</span></span>

<span data-ttu-id="11197-138">Em seguida, você precisa **determinar** o sentimento, o que ajuda na seleção da tarefa de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="11197-138">You then need to **determine** the sentiment, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="11197-139">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="11197-139">Select the appropriate machine learning task</span></span>

<span data-ttu-id="11197-140">Com este problema, você está a par dos seguintes fatos:</span><span class="sxs-lookup"><span data-stu-id="11197-140">With this problem, you know the following facts:</span></span>

<span data-ttu-id="11197-141">Dados de treinamento: os comentários do site podem ser positivos ou negativos (**sentimento**).</span><span class="sxs-lookup"><span data-stu-id="11197-141">Training data: website comments can be positive or negative (**sentiment**).</span></span>
<span data-ttu-id="11197-142">Preveja o **sentimento** de um novo comentário no site, seja positivo ou negativo, como nos exemplos a seguir:</span><span class="sxs-lookup"><span data-stu-id="11197-142">Predict the **sentiment** of a new website comment, either positive or negative, such as in the following examples:</span></span>

* <span data-ttu-id="11197-143">Evite inserir qualquer conteúdo sem sentido na Wikipédia.</span><span class="sxs-lookup"><span data-stu-id="11197-143">Please refrain from adding nonsense to Wikipedia.</span></span>
* <span data-ttu-id="11197-144">Ele é o melhor, e o artigo deve dizer isso.</span><span class="sxs-lookup"><span data-stu-id="11197-144">He is the best, and the article should say that.</span></span>

<span data-ttu-id="11197-145">A tarefa de aprendizado da máquina de classificação é mais adequada para esse cenário.</span><span class="sxs-lookup"><span data-stu-id="11197-145">The classification machine learning task is best suited for this scenario.</span></span>

### <a name="about-the-classification-task"></a><span data-ttu-id="11197-146">Sobre a tarefa de classificação</span><span class="sxs-lookup"><span data-stu-id="11197-146">About the classification task</span></span>

<span data-ttu-id="11197-147">A classificação é uma tarefa de aprendizado de máquina que usa dados para **determinar** a categoria, o tipo ou a classe de um item ou linha de dados.</span><span class="sxs-lookup"><span data-stu-id="11197-147">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="11197-148">Por exemplo, você pode usar a classificação para:</span><span class="sxs-lookup"><span data-stu-id="11197-148">For example, you can use classification to:</span></span>

* <span data-ttu-id="11197-149">Identificar o sentimento como positivo ou negativo.</span><span class="sxs-lookup"><span data-stu-id="11197-149">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="11197-150">Classificar email como spam, lixo eletrônico ou bom.</span><span class="sxs-lookup"><span data-stu-id="11197-150">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="11197-151">Determinar se a amostra de laboratório de um paciente é cancerígena.</span><span class="sxs-lookup"><span data-stu-id="11197-151">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="11197-152">Categorizar os clientes pela sua propensão a responder a uma campanha de vendas.</span><span class="sxs-lookup"><span data-stu-id="11197-152">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="11197-153">Tarefas de classificação são frequentemente de um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="11197-153">Classification tasks are frequently one of the following types:</span></span>

* <span data-ttu-id="11197-154">Binário: A ou B.</span><span class="sxs-lookup"><span data-stu-id="11197-154">Binary: either A or B.</span></span>
* <span data-ttu-id="11197-155">Multiclasse: várias categorias que podem ser previstas usando um único modelo.</span><span class="sxs-lookup"><span data-stu-id="11197-155">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="11197-156">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="11197-156">Create a console application</span></span>

1. <span data-ttu-id="11197-157">Abra o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="11197-157">Open Visual Studio 2017.</span></span> <span data-ttu-id="11197-158">Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="11197-158">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="11197-159">Na caixa de diálogo **Novo Projeto**, selecione o nó **Visual C#** seguido pelo nó **.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="11197-159">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="11197-160">Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="11197-160">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="11197-161">Na caixa de texto **Nome**, digite "SentimentAnalysis" e, em seguida, selecione o botão **OK** .</span><span class="sxs-lookup"><span data-stu-id="11197-161">In the **Name** text box, type "SentimentAnalysis" and then select the **OK** button.</span></span>

2. <span data-ttu-id="11197-162">Crie um diretório chamado *Data* no seu projeto para salvar seus arquivos do conjunto de dados:</span><span class="sxs-lookup"><span data-stu-id="11197-162">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="11197-163">No **Gerenciador de Soluções**, clique com o botão direito do mouse no seu projeto e selecione **Adicionar** > **Nova Pasta**.</span><span class="sxs-lookup"><span data-stu-id="11197-163">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="11197-164">Digite "Dados" e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="11197-164">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="11197-165">Instalar o **Pacote NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="11197-165">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="11197-166">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="11197-166">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="11197-167">Escolha "nuget.org" como a Origem do pacote, selecione a guia Procurar, pesquise por **Microsoft.ML**, selecione o pacote na lista e escolha o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="11197-167">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="11197-168">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="11197-168">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="11197-169">Preparar seus dados</span><span class="sxs-lookup"><span data-stu-id="11197-169">Prepare your data</span></span>

1. <span data-ttu-id="11197-170">Baixe os conjuntos de dados [WikiPedia detox-250-line-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) e [wikipedia-detox-250-line-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) e salve-os na pasta *Dados* criada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="11197-170">Download the [WikiPedia detox-250-line-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) and the [wikipedia-detox-250-line-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="11197-171">O primeiro conjunto de dados treina o modelo de aprendizado de máquina e o segundo pode ser usado para avaliar a precisão do seu modelo.</span><span class="sxs-lookup"><span data-stu-id="11197-171">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="11197-172">No Gerenciador de Soluções, clique com o botão direito do mouse em cada um dos arquivos \*.tsv e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="11197-172">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="11197-173">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.</span><span class="sxs-lookup"><span data-stu-id="11197-173">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="11197-174">Criar classes e definir demarcadores</span><span class="sxs-lookup"><span data-stu-id="11197-174">Create classes and define paths</span></span>

<span data-ttu-id="11197-175">Adicione as seguintes instruções `using` adicionais ao início do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="11197-175">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="11197-176">Você precisa criar três campos ​​globais para manter o caminho nos arquivos baixados recentemente:</span><span class="sxs-lookup"><span data-stu-id="11197-176">You need to create three global fields to hold the paths to the recently downloaded files:</span></span>

* <span data-ttu-id="11197-177">`_dataPath` tem o demarcador para o conjunto de dados usado para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="11197-177">`_dataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="11197-178">`_testDataPath` tem o demarcador para o conjunto de dados usado para avaliar o modelo.</span><span class="sxs-lookup"><span data-stu-id="11197-178">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="11197-179">`_modelPath` tem o demarcador em que o modelo treinado é salvo.</span><span class="sxs-lookup"><span data-stu-id="11197-179">`_modelPath` has the path where the trained model is saved.</span></span>

<span data-ttu-id="11197-180">Adicione o seguinte código à linha logo acima do método `Main` para especificar estes caminhos:</span><span class="sxs-lookup"><span data-stu-id="11197-180">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Declare file variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#2 "Declare variables to store data files")]

<span data-ttu-id="11197-181">Você precisa criar algumas classes para os dados e previsões de entrada.</span><span class="sxs-lookup"><span data-stu-id="11197-181">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="11197-182">Adicione uma nova classe ao seu projeto:</span><span class="sxs-lookup"><span data-stu-id="11197-182">Add a new class to your project:</span></span>

1. <span data-ttu-id="11197-183">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="11197-183">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="11197-184">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="11197-184">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="11197-185">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="11197-185">Then, select the **Add** button.</span></span>

    <span data-ttu-id="11197-186">O arquivo *SentimentData.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="11197-186">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="11197-187">Adicione a seguinte instrução `using` acima de *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="11197-187">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#1 "Add necessary usings")]

<span data-ttu-id="11197-188">Remova a definição de classe existente e adicione o seguinte código, que possui duas classes `SentimentData` e `SentimentPrediction`, ao arquivo *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="11197-188">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#2 "Declare data record types")]

<span data-ttu-id="11197-189">`SentimentData` é a classe do conjunto de dados de entrada e tem um `float` (`Sentiment`) que tem um valor para sentimento positivo ou negativo e uma cadeia de caracteres para o comentário (`SentimentText`).</span><span class="sxs-lookup"><span data-stu-id="11197-189">`SentimentData` is the input dataset class and has a `float` (`Sentiment`) that has a value for sentiment of either positive or negative, and a string for the comment (`SentimentText`).</span></span> <span data-ttu-id="11197-190">Ambos os campos têm atributos `Column` anexados a eles.</span><span class="sxs-lookup"><span data-stu-id="11197-190">Both fields have `Column` attributes attached to them.</span></span> <span data-ttu-id="11197-191">Este atributo descreve a ordem de cada campo no arquivo de dados e é o campo `Label`.</span><span class="sxs-lookup"><span data-stu-id="11197-191">This attribute describes the order of each field in the data file, and which is the `Label` field.</span></span> <span data-ttu-id="11197-192">`SentimentPrediction` é a classe usada para previsão depois que o modelo foi treinado.</span><span class="sxs-lookup"><span data-stu-id="11197-192">`SentimentPrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="11197-193">Tem um único booliano (`Sentiment`) e um atributo `PredictedLabel` `ColumnName`.</span><span class="sxs-lookup"><span data-stu-id="11197-193">It has a single boolean (`Sentiment`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="11197-194">O `Label` é usado para criar e treinar o modelo e também é usado com um segundo conjunto de dados para avaliar o modelo.</span><span class="sxs-lookup"><span data-stu-id="11197-194">The `Label` is used to create and train the model, and it's also used with a second dataset to evaluate the model.</span></span> <span data-ttu-id="11197-195">O `PredictedLabel` é usado durante a previsão e avaliação.</span><span class="sxs-lookup"><span data-stu-id="11197-195">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="11197-196">Para avaliação, uma entrada com dados de treinamento, os valores previstos e o modelo são usados.</span><span class="sxs-lookup"><span data-stu-id="11197-196">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="11197-197">No arquivo *Program.cs*, altere a assinatura do método `Main` substituindo `void` por `async Task`, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="11197-197">In the *Program.cs* file, change the `Main` method signature by replacing `void` with `async Task`, as in the following example:</span></span>

```csharp
static async Task Main(string[] args) 
{

}
```

<span data-ttu-id="11197-198">Você adiciona `async` a `Main` com um tipo de retorno <xref:System.Threading.Tasks.Task> porque está salvando o modelo em um arquivo zip posteriormente, e o programa precisa aguardar até que a tarefa externa seja concluída.</span><span class="sxs-lookup"><span data-stu-id="11197-198">You add `async` to `Main` with a <xref:System.Threading.Tasks.Task> return type because you're saving the model to a zip file later, and the program needs to wait until that external task completes.</span></span>

> [!NOTE]
> <span data-ttu-id="11197-199">Um método *async main* permite que você use `await` no método `Main`.</span><span class="sxs-lookup"><span data-stu-id="11197-199">An *async main* method enables you to use `await` in your `Main` method.</span></span> <span data-ttu-id="11197-200">Para obter mais informações, consulte o tópico [​​async main](../../../docs/csharp/programming-guide/main-and-command-args/index.md) no guia de programação em C#.</span><span class="sxs-lookup"><span data-stu-id="11197-200">For more information, see the [async main](../../../docs/csharp/programming-guide/main-and-command-args/index.md) topic in the C# programming guide.</span></span>

<span data-ttu-id="11197-201">Substitua a linha `Console.WriteLine("Hello World!")` pelo seguinte código no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="11197-201">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[Train](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#3 "Train your model")]

<span data-ttu-id="11197-202">O método `Train` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="11197-202">The `Train` method executes the following tasks:</span></span>

* <span data-ttu-id="11197-203">Carrega ou consome os dados.</span><span class="sxs-lookup"><span data-stu-id="11197-203">Loads or ingests the data.</span></span>
* <span data-ttu-id="11197-204">Pré-processa e personaliza os dados.</span><span class="sxs-lookup"><span data-stu-id="11197-204">Preprocesses and featurizes the data.</span></span>
* <span data-ttu-id="11197-205">Treina o modelo.</span><span class="sxs-lookup"><span data-stu-id="11197-205">Trains the model.</span></span>
* <span data-ttu-id="11197-206">Prevê o sentimento com base nos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="11197-206">Predicts sentiment based on test data.</span></span>

<span data-ttu-id="11197-207">Crie o método `Train`, logo após o método `Main`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="11197-207">Create the `Train` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static async Task<PredictionModel<SentimentData, SentimentPrediction>> Train()
{

}
```

## <a name="ingest-the-data"></a><span data-ttu-id="11197-208">Ingerir dados</span><span class="sxs-lookup"><span data-stu-id="11197-208">Ingest the data</span></span>

<span data-ttu-id="11197-209">Inicialize uma nova instância de <xref:Microsoft.ML.LearningPipeline> que incluirá o carregamento de dados, o processamento/personalização de dados e o modelo.</span><span class="sxs-lookup"><span data-stu-id="11197-209">Initialize a new instance of <xref:Microsoft.ML.LearningPipeline> that will include the data loading, data processing/featurization, and model.</span></span> <span data-ttu-id="11197-210">Adicione o seguinte código como a primeira linha do método `Train`:</span><span class="sxs-lookup"><span data-stu-id="11197-210">Add the following code as the first line of the `Train` method:</span></span>

[!code-csharp[LearningPipeline](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#5 "Create a learning pipeline")]

<span data-ttu-id="11197-211">O objeto <xref:Microsoft.ML.Data.TextLoader> é a primeira parte do pipeline e carrega os dados do arquivo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="11197-211">The <xref:Microsoft.ML.Data.TextLoader> object is the first part of the pipeline, and loads the training file data.</span></span>

[!code-csharp[TextLoader](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#6 "Add a text loader to the pipeline")]

## <a name="data-preprocess-and-feature-engineering"></a><span data-ttu-id="11197-212">Pré-processamento de dados e engenharia de recursos</span><span class="sxs-lookup"><span data-stu-id="11197-212">Data preprocess and feature engineering</span></span>

<span data-ttu-id="11197-213">O pré-processamento e a limpeza de dados são tarefas importantes que ocorrem antes de um conjunto de dados ser usado efetivamente para o aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="11197-213">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="11197-214">Os dados brutos costumam ser ruidosos e pouco confiáveis, e podem apresentar valores faltantes.</span><span class="sxs-lookup"><span data-stu-id="11197-214">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="11197-215">Usar dados sem essas tarefas de modelagem pode produzir resultados enganosos.</span><span class="sxs-lookup"><span data-stu-id="11197-215">Using data without these modeling tasks can produce misleading results.</span></span> <span data-ttu-id="11197-216">Os pipelines de transformação do ML.NET permitem que você componha um conjunto personalizado de transformações que são aplicadas aos seus dados antes do treinamento ou teste.</span><span class="sxs-lookup"><span data-stu-id="11197-216">ML.NET's transform pipelines allow you to compose a custom set of transforms that are applied to your data before training or testing.</span></span> <span data-ttu-id="11197-217">A principal finalidade das transformações é a personalização de dados.</span><span class="sxs-lookup"><span data-stu-id="11197-217">The transforms' primary purpose is for data featurization.</span></span> <span data-ttu-id="11197-218">A vantagem de um pipeline de transformação é que, após a definição de pipeline de transformação, salve o pipeline para aplicá-lo aos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="11197-218">A transform pipeline's advantage is that after transform pipeline definition, save the pipeline to apply it to test data.</span></span>

<span data-ttu-id="11197-219">Aplique um <xref:Microsoft.ML.Transforms.TextFeaturizer> para converter a coluna `SentimentText` em um [vetor numérico](../resources/glossary.md#numerical-feature-vector) chamado `Features`, usado pelo algoritmo de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="11197-219">Apply a <xref:Microsoft.ML.Transforms.TextFeaturizer> to convert the `SentimentText` column into a [numeric vector](../resources/glossary.md#numerical-feature-vector) called `Features` used by the machine learning algorithm.</span></span> <span data-ttu-id="11197-220">Esta é a etapa de pré-processamento/personalização.</span><span class="sxs-lookup"><span data-stu-id="11197-220">This is the preprocessing/featurization step.</span></span> <span data-ttu-id="11197-221">Usar componentes adicionais disponíveis no ML.NET pode permitir melhores resultados com o seu modelo.</span><span class="sxs-lookup"><span data-stu-id="11197-221">Using additional components available in ML.NET can enable better results with your model.</span></span> <span data-ttu-id="11197-222">Adicione `TextFeaturizer` ao pipeline como a próxima linha de código:</span><span class="sxs-lookup"><span data-stu-id="11197-222">Add `TextFeaturizer` to the pipeline as the next line of code:</span></span>

[!code-csharp[TextFeaturizer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#7 "Add a TextFeaturizer to the pipeline")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="11197-223">Escolher um algoritmo de aprendizado</span><span class="sxs-lookup"><span data-stu-id="11197-223">Choose a learning algorithm</span></span>

<span data-ttu-id="11197-224">O objeto <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier> é um aprendiz de árvore de decisão que você usará neste pipeline.</span><span class="sxs-lookup"><span data-stu-id="11197-224">The <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier> object is a decision tree learner you'll use in this pipeline.</span></span> <span data-ttu-id="11197-225">Semelhante à etapa de personalização, experimentar diferentes aprendizes disponíveis no ML.NET e alterar seus parâmetros leva a resultados diferentes.</span><span class="sxs-lookup"><span data-stu-id="11197-225">Similar to the featurization step, trying out different learners available in ML.NET and changing their parameters leads to different results.</span></span> <span data-ttu-id="11197-226">Para ajuste, você pode definir [hiperparâmetros](../resources/glossary.md#hyperparameter) como <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumTrees>, <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumLeaves>e <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.MinDocumentsInLeafs>.</span><span class="sxs-lookup"><span data-stu-id="11197-226">For tuning, you can set [hyperparameters](../resources/glossary.md#hyperparameter) like <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumTrees>, <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumLeaves>, and <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.MinDocumentsInLeafs>.</span></span> <span data-ttu-id="11197-227">Esses hiperparâmetros são definidos antes que qualquer coisa afete o modelo e são específicos do modelo.</span><span class="sxs-lookup"><span data-stu-id="11197-227">These hyperparameters are set before anything affects the model and are model-specific.</span></span> <span data-ttu-id="11197-228">Eles são usados ​​para ajustar a árvore de decisão quanto ao desempenho, para que valores maiores possam afetar negativamente o desempenho.</span><span class="sxs-lookup"><span data-stu-id="11197-228">They're used to tune the decision tree for performance, so larger values can negatively impact performance.</span></span>

<span data-ttu-id="11197-229">Adicione o seguinte código ao método `Train`:</span><span class="sxs-lookup"><span data-stu-id="11197-229">Add the following code to the `Train` method:</span></span>

[!code-csharp[BinaryClassifier](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#8 "Add a fast binary tree classifier")]

## <a name="train-the-model"></a><span data-ttu-id="11197-230">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="11197-230">Train the model</span></span>

<span data-ttu-id="11197-231">Você treina o modelo, <xref:Microsoft.ML.PredictionModel%602>, com base no conjunto de dados que foi carregado e transformado.</span><span class="sxs-lookup"><span data-stu-id="11197-231">You train the model, <xref:Microsoft.ML.PredictionModel%602>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="11197-232">`pipeline.Train<SentimentData, SentimentPrediction>()` treina o pipeline (carrega os dados, treina o personalizador e o aprendiz).</span><span class="sxs-lookup"><span data-stu-id="11197-232">`pipeline.Train<SentimentData, SentimentPrediction>()` trains the pipeline (loads the data, trains the featurizer and learner).</span></span> <span data-ttu-id="11197-233">O experimento não será executado até que isso ocorra.</span><span class="sxs-lookup"><span data-stu-id="11197-233">The experiment is not executed until this happens.</span></span>

<span data-ttu-id="11197-234">Adicione o seguinte código ao método `Train`:</span><span class="sxs-lookup"><span data-stu-id="11197-234">Add the following code to the `Train` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#9 "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="11197-235">Salvar e retornar o modelo treinado para usar na avaliação</span><span class="sxs-lookup"><span data-stu-id="11197-235">Save and Return the model trained to use for evaluation</span></span>

<span data-ttu-id="11197-236">Neste ponto, você tem um modelo que pode ser integrado em qualquer um dos seus aplicativos .NET existentes ou novos.</span><span class="sxs-lookup"><span data-stu-id="11197-236">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="11197-237">Para salvar seu modelo em um arquivo .zip antes de retornar, adicione o seguinte código à linha seguinte em `Train`:</span><span class="sxs-lookup"><span data-stu-id="11197-237">To save your model to a .zip file before returning, add the following code to the next line in `Train`:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#10 "Save the model")]

<span data-ttu-id="11197-238">Retorne o modelo no final do método `Train`.</span><span class="sxs-lookup"><span data-stu-id="11197-238">Return the model at the end of the `Train` method.</span></span>

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#11 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="11197-239">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="11197-239">Evaluate the model</span></span>

<span data-ttu-id="11197-240">Agora que você criou e treinou o modelo, precisa avaliá-lo com um conjunto de dados diferente para garantia de qualidade e validação.</span><span class="sxs-lookup"><span data-stu-id="11197-240">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="11197-241">No método `Evaluate`, o modelo criado em `Train` é passado para ser avaliado.</span><span class="sxs-lookup"><span data-stu-id="11197-241">In the `Evaluate` method, the model created in `Train` is passed in to be evaluated.</span></span> <span data-ttu-id="11197-242">Crie o método `Evaluate` , logo após `Train`, como no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="11197-242">Create the `Evaluate` method, just after `Train`, as in the following code:</span></span>

```csharp
public static void Evaluate(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

<span data-ttu-id="11197-243">O método `Evaluate` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="11197-243">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="11197-244">Carrega o conjunto de dados de teste.</span><span class="sxs-lookup"><span data-stu-id="11197-244">Loads the test dataset.</span></span>
* <span data-ttu-id="11197-245">Cria o avaliador binário.</span><span class="sxs-lookup"><span data-stu-id="11197-245">Creates the binary evaluator.</span></span>
* <span data-ttu-id="11197-246">Avalia o modelo e cria métricas.</span><span class="sxs-lookup"><span data-stu-id="11197-246">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="11197-247">Exibe as métricas.</span><span class="sxs-lookup"><span data-stu-id="11197-247">Displays the metrics.</span></span>

<span data-ttu-id="11197-248">Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `Train`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="11197-248">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#12 "Call the Evaluate method")]

<span data-ttu-id="11197-249">A classe <xref:Microsoft.ML.Data.TextLoader> carrega o novo conjunto de dados de teste com o mesmo esquema.</span><span class="sxs-lookup"><span data-stu-id="11197-249">The <xref:Microsoft.ML.Data.TextLoader> class loads the new test dataset with the same schema.</span></span> <span data-ttu-id="11197-250">Você pode avaliar o modelo usando esse conjunto de dados como uma verificação de qualidade.</span><span class="sxs-lookup"><span data-stu-id="11197-250">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="11197-251">Adicione o seguinte código ao método `Evaluate`:</span><span class="sxs-lookup"><span data-stu-id="11197-251">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadText](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#13 "Load the test dataset")]

<span data-ttu-id="11197-252">O objeto <xref:Microsoft.ML.Models.BinaryClassificationEvaluator> calcula as métricas de qualidade para o `PredictionModel` usando o conjunto de dados especificado.</span><span class="sxs-lookup"><span data-stu-id="11197-252">The <xref:Microsoft.ML.Models.BinaryClassificationEvaluator> object computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="11197-253">Para ver essas métricas, adicione o avaliador como a próxima linha no método `Evaluate`, com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="11197-253">To see those metrics, add the evaluator as the next line in the `Evaluate` method, with the following code:</span></span>

[!code-csharp[BinaryEvaluator](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#14 "Create the binary evaluator")]

<span data-ttu-id="11197-254">O <xref:Microsoft.ML.Models.BinaryClassificationMetrics> contém as métricas gerais calculadas pelos avaliadores de classificação binária.</span><span class="sxs-lookup"><span data-stu-id="11197-254">The <xref:Microsoft.ML.Models.BinaryClassificationMetrics> contains the overall metrics computed by binary classification evaluators.</span></span> <span data-ttu-id="11197-255">Para exibi-los a fim de determinar a qualidade do modelo, é preciso primeiro obter as métricas.</span><span class="sxs-lookup"><span data-stu-id="11197-255">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="11197-256">Adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="11197-256">Add the following code:</span></span>

[!code-csharp[CreateMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#15 "Evaluate the model and create metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="11197-257">Exibir as métricas para validação de modelo</span><span class="sxs-lookup"><span data-stu-id="11197-257">Displaying the metrics for model validation</span></span>

<span data-ttu-id="11197-258">Use o código a seguir para exibir as métricas, compartilhar os resultados e, em seguida, agir com relação a eles:</span><span class="sxs-lookup"><span data-stu-id="11197-258">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#16 "Display selected metrics")]

## <a name="predict-the-test-data-outcomes-with-the-model"></a><span data-ttu-id="11197-259">Prever os resultados dos dados de teste com o modelo</span><span class="sxs-lookup"><span data-stu-id="11197-259">Predict the test data outcomes with the model</span></span>

<span data-ttu-id="11197-260">Crie o método `Predict`, logo após o método `Evaluate`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="11197-260">Create the `Predict` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
public static void Predict(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

<span data-ttu-id="11197-261">O método `Predict` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="11197-261">The `Predict` method executes the following tasks:</span></span>

* <span data-ttu-id="11197-262">Cria dados de teste.</span><span class="sxs-lookup"><span data-stu-id="11197-262">Creates test data.</span></span>
* <span data-ttu-id="11197-263">Prevê o sentimento com base nos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="11197-263">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="11197-264">Combina dados de teste e previsões para relatórios.</span><span class="sxs-lookup"><span data-stu-id="11197-264">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="11197-265">Exibe os resultados previstos.</span><span class="sxs-lookup"><span data-stu-id="11197-265">Displays the predicted results.</span></span>

<span data-ttu-id="11197-266">Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `Evaluate`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="11197-266">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#17 "Call the Predict method")]

<span data-ttu-id="11197-267">Adicione alguns comentários para testar as previsões do modelo treinado no método `Predict`:</span><span class="sxs-lookup"><span data-stu-id="11197-267">Add some comments to test the trained model's predictions in the `Predict` method:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#18 "Create test data for predictions")]

<span data-ttu-id="11197-268">Agora que você tem um modelo, pode usá-lo para prever o sentimento positivo ou negativo dos dados do comentário usando o método <xref:Microsoft.ML.PredictionModel.Predict%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="11197-268">Now that you have a model, you can use that to predict the positive or negative sentiment of the comment data using the <xref:Microsoft.ML.PredictionModel.Predict%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="11197-269">Para obter uma previsão, use `Predict` em novos dados.</span><span class="sxs-lookup"><span data-stu-id="11197-269">To get a prediction, use `Predict` on new data.</span></span> <span data-ttu-id="11197-270">Observe que os dados de entrada são uma cadeia de caracteres e o modelo inclui a personalização.</span><span class="sxs-lookup"><span data-stu-id="11197-270">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="11197-271">Seu pipeline está em sincronia durante o treinamento e a previsão.</span><span class="sxs-lookup"><span data-stu-id="11197-271">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="11197-272">Você não precisou escrever código de pré-processamento/personalização especificamente para previsões, e a mesma API cuida das previsões de lote e de uso único.</span><span class="sxs-lookup"><span data-stu-id="11197-272">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#19 "Create predictions of sentiments")]

### <a name="model-operationalization-prediction"></a><span data-ttu-id="11197-273">Operacionalização do modelo: previsão</span><span class="sxs-lookup"><span data-stu-id="11197-273">Model operationalization: prediction</span></span>

<span data-ttu-id="11197-274">Exiba `SentimentText` e a previsão de sentimento correspondente para compartilhar os resultados e agir de acordo com eles.</span><span class="sxs-lookup"><span data-stu-id="11197-274">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="11197-275">Isso é chamado de operacionalização, usar os dados retornados como parte das políticas operacionais.</span><span class="sxs-lookup"><span data-stu-id="11197-275">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="11197-276">Crie um cabeçalho para os resultados usando o seguinte código <xref:System.Console.WriteLine?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="11197-276">Create a header for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#20 "Display prediction outputs")]

<span data-ttu-id="11197-277">Antes de exibir os resultados previstos, combine o sentimento e a previsão juntos para ver o comentário original com o sentimento previsto.</span><span class="sxs-lookup"><span data-stu-id="11197-277">Before displaying the predicted results, combine the sentiment and prediction together to see the original comment with its predicted sentiment.</span></span> <span data-ttu-id="11197-278">O código a seguir usa o método <xref:System.Linq.Enumerable.Zip%2A> para que isso aconteça, então adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="11197-278">The following code uses the <xref:System.Linq.Enumerable.Zip%2A> method to make that happen, so add that code next:</span></span>

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#21 "Build the pairs of sentiment data and predictions")]

<span data-ttu-id="11197-279">Agora que você combinou `SentimentText` e `Sentiment` em uma classe, você pode exibir os resultados usando o método <xref:System.Console.WriteLine?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="11197-279">Now that you've combined the `SentimentText` and `Sentiment` into a class, you can display the results using the <xref:System.Console.WriteLine?displayProperty=nameWithType> method:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#22 "Display the predictions")]

<span data-ttu-id="11197-280">Como nomes de elementos de tuplas inferidos são um novo recurso no C# 7.1 e a versão da linguagem padrão do projeto é C# 7.0, é necessário alterar a versão da linguagem para C# 7.1 ou superior.</span><span class="sxs-lookup"><span data-stu-id="11197-280">Because inferred tuple element names are a new feature in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span>
<span data-ttu-id="11197-281">Para fazer isso, clique com o botão direito do mouse no nó do projeto no **Gerenciador de Soluções** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="11197-281">To do that, right-click on the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="11197-282">Selecione a guia **Build** e o botão **Avançado**.</span><span class="sxs-lookup"><span data-stu-id="11197-282">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="11197-283">No menu suspenso, selecione **C# 7.1** (ou uma versão posterior).</span><span class="sxs-lookup"><span data-stu-id="11197-283">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="11197-284">Selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="11197-284">Select the **OK** button.</span></span>

## <a name="results"></a><span data-ttu-id="11197-285">Resultados</span><span class="sxs-lookup"><span data-stu-id="11197-285">Results</span></span>

<span data-ttu-id="11197-286">Seus resultados devem ser semelhantes aos seguintes.</span><span class="sxs-lookup"><span data-stu-id="11197-286">Your results should be similar to the following.</span></span> <span data-ttu-id="11197-287">Conforme o pipeline processa, exibe mensagens.</span><span class="sxs-lookup"><span data-stu-id="11197-287">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="11197-288">Você pode ver avisos ou mensagens de processamento.</span><span class="sxs-lookup"><span data-stu-id="11197-288">You may see warnings, or processing messages.</span></span> <span data-ttu-id="11197-289">Eles foram removidos dos seguintes resultados para maior clareza.</span><span class="sxs-lookup"><span data-stu-id="11197-289">These have been removed from the following results for clarity.</span></span>

```

PredictionModel quality metrics evaluation
------------------------------------------
Accuracy: 66.67%
Auc: 94.44%
F1Score: 75.00%

Sentiment Predictions
---------------------
Sentiment: Please refrain from adding nonsense to Wikipedia. | Prediction: Negative
Sentiment: He is the best, and the article should say that. | Prediction: Positive

```

<span data-ttu-id="11197-290">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="11197-290">Congratulations!</span></span> <span data-ttu-id="11197-291">Agora você criou com sucesso um modelo de aprendizado de máquina para classificar e prever o sentimento das mensagens.</span><span class="sxs-lookup"><span data-stu-id="11197-291">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span> <span data-ttu-id="11197-292">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis).</span><span class="sxs-lookup"><span data-stu-id="11197-292">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="11197-293">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="11197-293">Next steps</span></span>

<span data-ttu-id="11197-294">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="11197-294">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="11197-295">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="11197-295">Understand the problem</span></span>
> * <span data-ttu-id="11197-296">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="11197-296">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="11197-297">Preparar seus dados</span><span class="sxs-lookup"><span data-stu-id="11197-297">Prepare your data</span></span>
> * <span data-ttu-id="11197-298">Criar o pipeline de aprendizado</span><span class="sxs-lookup"><span data-stu-id="11197-298">Create the learning pipeline</span></span>
> * <span data-ttu-id="11197-299">Carregar um classificador</span><span class="sxs-lookup"><span data-stu-id="11197-299">Load a classifier</span></span>
> * <span data-ttu-id="11197-300">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="11197-300">Train the model</span></span>
> * <span data-ttu-id="11197-301">Avaliar o modelo com um conjunto de dados diferente</span><span class="sxs-lookup"><span data-stu-id="11197-301">Evaluate the model with a different dataset</span></span>
> * <span data-ttu-id="11197-302">Prever os resultados dos dados de teste com o modelo</span><span class="sxs-lookup"><span data-stu-id="11197-302">Predict the test data outcomes with the model</span></span>

<span data-ttu-id="11197-303">Avançar para o próximo tutorial para saber mais</span><span class="sxs-lookup"><span data-stu-id="11197-303">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="11197-304">Previsão do valor da corrida do táxi</span><span class="sxs-lookup"><span data-stu-id="11197-304">Taxi Fare Predictor</span></span>](taxi-fare.md)
