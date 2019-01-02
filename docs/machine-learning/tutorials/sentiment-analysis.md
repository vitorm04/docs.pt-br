---
title: Usar o ML.NET em um cenário de classificação binária de análise de sentimento
description: Descubra como usar o ML.NET em um cenário de classificação binária para entender como usar a previsão de sentimentos para executar a ação apropriada.
ms.date: 12/20/2018
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 90f3b79226b16ac1ea4cbbe49ce07d95a138323b
ms.sourcegitcommit: 0888d7b24f475c346a3f444de8d83ec1ca7cd234
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2018
ms.locfileid: "53779126"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a><span data-ttu-id="edcd9-103">Tutorial: Usar o ML.NET em um cenário de classificação binária de análise de sentimento</span><span class="sxs-lookup"><span data-stu-id="edcd9-103">Tutorial: Use ML.NET in a sentiment analysis binary classification scenario</span></span>

> [!NOTE]
> <span data-ttu-id="edcd9-104">Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="edcd9-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="edcd9-105">Para obter mais informações, visite [a introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="edcd9-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="edcd9-106">Este tutorial de exemplo ilustra o uso do ML.NET para criar um classificador de sentimento por meio de um aplicativo de console do .NET Core usando C# no Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="edcd9-106">This sample tutorial illustrates using ML.NET to create a sentiment classifier via a .NET Core console application using C# in Visual Studio 2017.</span></span>

<span data-ttu-id="edcd9-107">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="edcd9-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="edcd9-108">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="edcd9-108">Understand the problem</span></span>
> * <span data-ttu-id="edcd9-109">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="edcd9-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="edcd9-110">Preparar seus dados</span><span class="sxs-lookup"><span data-stu-id="edcd9-110">Prepare your data</span></span>
> * <span data-ttu-id="edcd9-111">Criar o pipeline de aprendizado</span><span class="sxs-lookup"><span data-stu-id="edcd9-111">Create the learning pipeline</span></span>
> * <span data-ttu-id="edcd9-112">Carregar um classificador</span><span class="sxs-lookup"><span data-stu-id="edcd9-112">Load a classifier</span></span>
> * <span data-ttu-id="edcd9-113">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="edcd9-113">Train the model</span></span>
> * <span data-ttu-id="edcd9-114">Avaliar o modelo com um conjunto de dados diferente</span><span class="sxs-lookup"><span data-stu-id="edcd9-114">Evaluate the model with a different dataset</span></span>
> * <span data-ttu-id="edcd9-115">Prever uma única instância do resultado dos dados de teste com o modelo</span><span class="sxs-lookup"><span data-stu-id="edcd9-115">Predict a single instance of test data outcome with the model</span></span>
> * <span data-ttu-id="edcd9-116">Prever os resultados dos dados de teste com o modelo carregado</span><span class="sxs-lookup"><span data-stu-id="edcd9-116">Predict the test data outcomes with a loaded model</span></span>

## <a name="sentiment-analysis-sample-overview"></a><span data-ttu-id="edcd9-117">Visão geral da amostra de análise de sentimento</span><span class="sxs-lookup"><span data-stu-id="edcd9-117">Sentiment analysis sample overview</span></span>

<span data-ttu-id="edcd9-118">A amostra é um aplicativo de console que usa o ML.NET para treinar um modelo que classifica e prevê o sentimento como positivo ou negativo.</span><span class="sxs-lookup"><span data-stu-id="edcd9-118">The sample is a console app that uses ML.NET to train a model that classifies and predicts sentiment as either positive or negative.</span></span> <span data-ttu-id="edcd9-119">Ele também avalia o modelo com um segundo conjunto de dados para análise de qualidade.</span><span class="sxs-lookup"><span data-stu-id="edcd9-119">It also evaluates the model with a second dataset for quality analysis.</span></span> <span data-ttu-id="edcd9-120">Os conjuntos de dados de sentimento são do projeto WikiDetox.</span><span class="sxs-lookup"><span data-stu-id="edcd9-120">The sentiment datasets are from the WikiDetox project.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="edcd9-121">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="edcd9-121">Prerequisites</span></span>

* <span data-ttu-id="edcd9-122">[Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="edcd9-122">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="edcd9-123">[Arquivo separado de guia de dados de linha detox da Wikipédia (wikiPedia-detox-250-line-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).</span><span class="sxs-lookup"><span data-stu-id="edcd9-123">The [Wikipedia detox line data tab separated file (wikiPedia-detox-250-line-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span>
* <span data-ttu-id="edcd9-124">[Arquivo separado de guia de teste de linha detox da Wikipédia (wikipedia-detox-250-line-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).</span><span class="sxs-lookup"><span data-stu-id="edcd9-124">The [Wikipedia detox line test tab separated file (wikipedia-detox-250-line-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="edcd9-125">Fluxo de trabalho de aprendizado de máquina</span><span class="sxs-lookup"><span data-stu-id="edcd9-125">Machine learning workflow</span></span>

<span data-ttu-id="edcd9-126">Este tutorial segue um fluxo de trabalho de aprendizado de máquina que permite que o processo se mova de maneira ordenada.</span><span class="sxs-lookup"><span data-stu-id="edcd9-126">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="edcd9-127">As fases do fluxo de trabalho são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="edcd9-127">The workflow phases are as follows:</span></span>

1. <span data-ttu-id="edcd9-128">**Compreender o problema**</span><span class="sxs-lookup"><span data-stu-id="edcd9-128">**Understand the problem**</span></span>
2. <span data-ttu-id="edcd9-129">**Preparar seus dados**</span><span class="sxs-lookup"><span data-stu-id="edcd9-129">**Prepare your data**</span></span>
   * <span data-ttu-id="edcd9-130">**Carregar os dados**</span><span class="sxs-lookup"><span data-stu-id="edcd9-130">**Load the data**</span></span>
   * <span data-ttu-id="edcd9-131">**Extrair recursos (Transformar seus dados)**</span><span class="sxs-lookup"><span data-stu-id="edcd9-131">**Extract features (Transform your data)**</span></span>
3. <span data-ttu-id="edcd9-132">**Compilar e treinar**</span><span class="sxs-lookup"><span data-stu-id="edcd9-132">**Build and train**</span></span> 
   * <span data-ttu-id="edcd9-133">**Treinar o modelo**</span><span class="sxs-lookup"><span data-stu-id="edcd9-133">**Train the model**</span></span>
   * <span data-ttu-id="edcd9-134">**Avaliar o modelo**</span><span class="sxs-lookup"><span data-stu-id="edcd9-134">**Evaluate the model**</span></span>
4. <span data-ttu-id="edcd9-135">**Executar**</span><span class="sxs-lookup"><span data-stu-id="edcd9-135">**Run**</span></span>
   * <span data-ttu-id="edcd9-136">**Consumo do modelo**</span><span class="sxs-lookup"><span data-stu-id="edcd9-136">**Model consumption**</span></span>

### <a name="understand-the-problem"></a><span data-ttu-id="edcd9-137">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="edcd9-137">Understand the problem</span></span>

<span data-ttu-id="edcd9-138">Você primeiro precisa compreender o problema, para que possa dividi-lo em partes que possam oferecer suporte à criação e ao treinamento do modelo.</span><span class="sxs-lookup"><span data-stu-id="edcd9-138">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="edcd9-139">Dividir o problema permite prever e avaliar os resultados.</span><span class="sxs-lookup"><span data-stu-id="edcd9-139">Breaking the problem down allows you to predict and evaluate the results.</span></span>

<span data-ttu-id="edcd9-140">O problema deste tutorial é compreender o sentimento de comentário do site recebido para executar a ação apropriada.</span><span class="sxs-lookup"><span data-stu-id="edcd9-140">The problem for this tutorial is to understand incoming website comment sentiment to take the appropriate action.</span></span>

<span data-ttu-id="edcd9-141">Você pode dividir o problema com o texto de sentimento e o valor de sentimento para os dados com os quais deseja treinar o modelo e com um valor de sentimento previsto que você pode avaliar e usar operacionalmente.</span><span class="sxs-lookup"><span data-stu-id="edcd9-141">You can break down the problem to the sentiment text and sentiment value for the data you want to train the model with, and a predicted sentiment value that you can evaluate and then use operationally.</span></span>

<span data-ttu-id="edcd9-142">Em seguida, você precisa **determinar** o sentimento, o que ajuda na seleção da tarefa de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="edcd9-142">You then need to **determine** the sentiment, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="edcd9-143">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="edcd9-143">Select the appropriate machine learning task</span></span>

<span data-ttu-id="edcd9-144">Com este problema, você está a par dos seguintes fatos:</span><span class="sxs-lookup"><span data-stu-id="edcd9-144">With this problem, you know the following facts:</span></span>

<span data-ttu-id="edcd9-145">Dados de treinamento: os comentários no site podem ser tóxicos (1) ou não tóxicos (0) (**sentimento**).</span><span class="sxs-lookup"><span data-stu-id="edcd9-145">Training data: website comments can be toxic (1) or not toxic (0) (**sentiment**).</span></span>
<span data-ttu-id="edcd9-146">Preveja o **sentimento** de um novo comentário no site, seja tóxico ou não tóxico, como nos exemplos a seguir:</span><span class="sxs-lookup"><span data-stu-id="edcd9-146">Predict the **sentiment** of a new website comment, either toxic or not toxic, such as in the following examples:</span></span>

* <span data-ttu-id="edcd9-147">Evite inserir qualquer conteúdo sem sentido na Wikipédia.</span><span class="sxs-lookup"><span data-stu-id="edcd9-147">Please refrain from adding nonsense to Wikipedia.</span></span>
* <span data-ttu-id="edcd9-148">Ele é o melhor, e o artigo deve dizer isso.</span><span class="sxs-lookup"><span data-stu-id="edcd9-148">He is the best, and the article should say that.</span></span>

<span data-ttu-id="edcd9-149">A tarefa de aprendizado da máquina de classificação é mais adequada para esse cenário.</span><span class="sxs-lookup"><span data-stu-id="edcd9-149">The classification machine learning task is best suited for this scenario.</span></span>

### <a name="about-the-classification-task"></a><span data-ttu-id="edcd9-150">Sobre a tarefa de classificação</span><span class="sxs-lookup"><span data-stu-id="edcd9-150">About the classification task</span></span>

<span data-ttu-id="edcd9-151">A classificação é uma tarefa de aprendizado de máquina que usa dados para **determinar** a categoria, o tipo ou a classe de um item ou linha de dados.</span><span class="sxs-lookup"><span data-stu-id="edcd9-151">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="edcd9-152">Por exemplo, você pode usar a classificação para:</span><span class="sxs-lookup"><span data-stu-id="edcd9-152">For example, you can use classification to:</span></span>

* <span data-ttu-id="edcd9-153">Identificar o sentimento como positivo ou negativo.</span><span class="sxs-lookup"><span data-stu-id="edcd9-153">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="edcd9-154">Classificar email como spam, lixo eletrônico ou bom.</span><span class="sxs-lookup"><span data-stu-id="edcd9-154">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="edcd9-155">Determinar se a amostra de laboratório de um paciente é cancerígena.</span><span class="sxs-lookup"><span data-stu-id="edcd9-155">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="edcd9-156">Categorizar os clientes pela sua propensão a responder a uma campanha de vendas.</span><span class="sxs-lookup"><span data-stu-id="edcd9-156">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="edcd9-157">Tarefas de classificação são frequentemente de um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="edcd9-157">Classification tasks are frequently one of the following types:</span></span>

* <span data-ttu-id="edcd9-158">Binário: A ou B.</span><span class="sxs-lookup"><span data-stu-id="edcd9-158">Binary: either A or B.</span></span>
* <span data-ttu-id="edcd9-159">Multiclasse: várias categorias que podem ser previstas usando um único modelo.</span><span class="sxs-lookup"><span data-stu-id="edcd9-159">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="edcd9-160">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="edcd9-160">Create a console application</span></span>

1. <span data-ttu-id="edcd9-161">Abra o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="edcd9-161">Open Visual Studio 2017.</span></span> <span data-ttu-id="edcd9-162">Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="edcd9-162">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="edcd9-163">Na caixa de diálogo **Novo Projeto**, selecione o nó **Visual C#** seguido pelo nó **.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="edcd9-163">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="edcd9-164">Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="edcd9-164">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="edcd9-165">Na caixa de texto **Nome**, digite "SentimentAnalysis" e, em seguida, selecione o botão **OK** .</span><span class="sxs-lookup"><span data-stu-id="edcd9-165">In the **Name** text box, type "SentimentAnalysis" and then select the **OK** button.</span></span>

2. <span data-ttu-id="edcd9-166">Crie um diretório chamado *Data* no seu projeto para salvar seus arquivos do conjunto de dados:</span><span class="sxs-lookup"><span data-stu-id="edcd9-166">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="edcd9-167">No **Gerenciador de Soluções**, clique com o botão direito do mouse no seu projeto e selecione **Adicionar** > **Nova Pasta**.</span><span class="sxs-lookup"><span data-stu-id="edcd9-167">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="edcd9-168">Digite "Dados" e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="edcd9-168">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="edcd9-169">Instalar o **Pacote NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="edcd9-169">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="edcd9-170">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="edcd9-170">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="edcd9-171">Escolha "nuget.org" como a Origem do pacote, selecione a guia Procurar, pesquise por **Microsoft.ML**, selecione o pacote na lista e escolha o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="edcd9-171">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="edcd9-172">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="edcd9-172">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="edcd9-173">Preparar seus dados</span><span class="sxs-lookup"><span data-stu-id="edcd9-173">Prepare your data</span></span>

1. <span data-ttu-id="edcd9-174">Baixe os conjuntos de dados [WikiPedia detox-250-line-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) e [wikipedia-detox-250-line-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) e salve-os na pasta *Dados* criada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="edcd9-174">Download the [WikiPedia detox-250-line-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) and the [wikipedia-detox-250-line-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="edcd9-175">O primeiro conjunto de dados treina o modelo de aprendizado de máquina e o segundo pode ser usado para avaliar a precisão do seu modelo.</span><span class="sxs-lookup"><span data-stu-id="edcd9-175">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="edcd9-176">No Gerenciador de Soluções, clique com o botão direito do mouse em cada um dos arquivos \*.tsv e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="edcd9-176">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="edcd9-177">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.</span><span class="sxs-lookup"><span data-stu-id="edcd9-177">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="edcd9-178">Criar classes e definir demarcadores</span><span class="sxs-lookup"><span data-stu-id="edcd9-178">Create classes and define paths</span></span>

<span data-ttu-id="edcd9-179">Adicione as seguintes instruções `using` adicionais ao início do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="edcd9-179">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="edcd9-180">Você precisa criar três campos ​​globais para manter os caminhos dos arquivos baixados recentemente e uma variável global para o `TextLoader`:</span><span class="sxs-lookup"><span data-stu-id="edcd9-180">You need to create three global fields to hold the paths to the recently downloaded files, and a global variable for the `TextLoader`:</span></span>

* <span data-ttu-id="edcd9-181">`_trainDataPath` tem o demarcador para o conjunto de dados usado para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="edcd9-181">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="edcd9-182">`_testDataPath` tem o demarcador para o conjunto de dados usado para avaliar o modelo.</span><span class="sxs-lookup"><span data-stu-id="edcd9-182">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="edcd9-183">`_modelPath` tem o demarcador em que o modelo treinado é salvo.</span><span class="sxs-lookup"><span data-stu-id="edcd9-183">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="edcd9-184">O `_textLoader` é o <xref:Microsoft.ML.Runtime.Data.TextLoader> usado para carregar e transformar os conjuntos de dados.</span><span class="sxs-lookup"><span data-stu-id="edcd9-184">`_textLoader` is the <xref:Microsoft.ML.Runtime.Data.TextLoader> used to load and transform the datasets.</span></span>

<span data-ttu-id="edcd9-185">Adicione o seguinte código à linha logo acima do método `Main` para especificar estes caminhos e a variável `_textLoader`:</span><span class="sxs-lookup"><span data-stu-id="edcd9-185">Add the following code to the line right above the `Main` method to specify those paths and the `_textLoader` variable:</span></span>

[!code-csharp[Declare global variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#2 "Declare global variables")]

<span data-ttu-id="edcd9-186">Você precisa criar algumas classes para os dados e previsões de entrada.</span><span class="sxs-lookup"><span data-stu-id="edcd9-186">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="edcd9-187">Adicione uma nova classe ao seu projeto:</span><span class="sxs-lookup"><span data-stu-id="edcd9-187">Add a new class to your project:</span></span>

1. <span data-ttu-id="edcd9-188">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="edcd9-188">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="edcd9-189">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="edcd9-189">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="edcd9-190">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="edcd9-190">Then, select the **Add** button.</span></span>

    <span data-ttu-id="edcd9-191">O arquivo *SentimentData.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="edcd9-191">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="edcd9-192">Adicione a seguinte instrução `using` acima de *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="edcd9-192">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#1 "Add necessary usings")]

<span data-ttu-id="edcd9-193">Remova a definição de classe existente e adicione o seguinte código, que possui duas classes `SentimentData` e `SentimentPrediction`, ao arquivo *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="edcd9-193">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#2 "Declare data record types")]

<span data-ttu-id="edcd9-194">`SentimentData` é a classe do conjunto de dados de entrada e tem um `float` (`Sentiment`) que tem um valor para sentimento positivo ou negativo e uma cadeia de caracteres para o comentário (`SentimentText`).</span><span class="sxs-lookup"><span data-stu-id="edcd9-194">`SentimentData` is the input dataset class and has a `float` (`Sentiment`) that has a value for sentiment of either positive or negative, and a string for the comment (`SentimentText`).</span></span> <span data-ttu-id="edcd9-195">Ambos os campos têm atributos `Column` anexados a eles.</span><span class="sxs-lookup"><span data-stu-id="edcd9-195">Both fields have `Column` attributes attached to them.</span></span> <span data-ttu-id="edcd9-196">Este atributo descreve a ordem de cada campo no arquivo de dados e é o campo `Label`.</span><span class="sxs-lookup"><span data-stu-id="edcd9-196">This attribute describes the order of each field in the data file, and which is the `Label` field.</span></span> <span data-ttu-id="edcd9-197">`SentimentPrediction` é a classe usada para previsão depois que o modelo foi treinado.</span><span class="sxs-lookup"><span data-stu-id="edcd9-197">`SentimentPrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="edcd9-198">Tem um único booliano (`Sentiment`) e um atributo `PredictedLabel` `ColumnName`.</span><span class="sxs-lookup"><span data-stu-id="edcd9-198">It has a single boolean (`Sentiment`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="edcd9-199">O `Label` é usado para criar e treinar o modelo e também é usado com um segundo conjunto de dados para avaliar o modelo.</span><span class="sxs-lookup"><span data-stu-id="edcd9-199">The `Label` is used to create and train the model, and it's also used with a second dataset to evaluate the model.</span></span> <span data-ttu-id="edcd9-200">O `PredictedLabel` é usado durante a previsão e avaliação.</span><span class="sxs-lookup"><span data-stu-id="edcd9-200">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="edcd9-201">Para avaliação, uma entrada com dados de treinamento, os valores previstos e o modelo são usados.</span><span class="sxs-lookup"><span data-stu-id="edcd9-201">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="edcd9-202">Ao criar um modelo com o ML.NET, comece criando um `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="edcd9-202">When building a model with ML.NET you start by creating an `MLContext`.</span></span> <span data-ttu-id="edcd9-203">Isso é comparável conceitualmente ao uso de `DbContext` no Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="edcd9-203">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span> <span data-ttu-id="edcd9-204">O ambiente fornece um contexto para seu trabalho de ML que pode ser usado no acompanhamento e registro em log da exceção.</span><span class="sxs-lookup"><span data-stu-id="edcd9-204">The environment provides a context for your ML job that can be used for exception tracking and logging.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="edcd9-205">Inicializar variáveis em Main</span><span class="sxs-lookup"><span data-stu-id="edcd9-205">Initialize variables in Main</span></span>

<span data-ttu-id="edcd9-206">Crie uma variável chamada `mlContext` e inicialize-a com uma nova instância de `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="edcd9-206">Create a variable called `mlContext` and initialize it with a new instance of `MLContext`.</span></span>  <span data-ttu-id="edcd9-207">Substitua a linha `Console.WriteLine("Hello World!")` pelo seguinte código no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="edcd9-207">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="edcd9-208">Em seguida, para configurar o carregamento de dados, inicialize a variável global `_textLoader` para reutilizá-la.</span><span class="sxs-lookup"><span data-stu-id="edcd9-208">Next, to setup for data loading initialize the `_textLoader` global variable in order to reuse it.</span></span>  <span data-ttu-id="edcd9-209">Observe que você está usando um `TextReader`.</span><span class="sxs-lookup"><span data-stu-id="edcd9-209">Notice that you're using a `TextReader`.</span></span> <span data-ttu-id="edcd9-210">Quando você cria um `TextLoader` usando um `TextReader`, você passa o contexto necessário e a classe <xref:Microsoft.ML.Runtime.Data.TextLoader.Arguments> que permite a personalização.</span><span class="sxs-lookup"><span data-stu-id="edcd9-210">When you create a `TextLoader` using a `TextReader`, you pass in the context needed and the <xref:Microsoft.ML.Runtime.Data.TextLoader.Arguments> class which enables customization.</span></span>

 <span data-ttu-id="edcd9-211">Especifique o esquema de dados passando uma matriz de objetos <xref:Microsoft.ML.Runtime.Data.TextLoader.Column> para o carregador que contém todos os nomes de coluna e seus tipos.</span><span class="sxs-lookup"><span data-stu-id="edcd9-211">Specify the data schema by passing an array of <xref:Microsoft.ML.Runtime.Data.TextLoader.Column> objects to the loader containing all the column names and their types.</span></span> <span data-ttu-id="edcd9-212">Você definiu o esquema de dados anteriormente ao criar nossa classe `SentimentData`.</span><span class="sxs-lookup"><span data-stu-id="edcd9-212">You defined the data schema previously when you created our `SentimentData` class.</span></span> <span data-ttu-id="edcd9-213">Para nosso esquema, a primeira coluna (Label) é <xref:System.Boolean> (a previsão) e a segunda coluna (SentimentText) é o recurso do tipo texto/cadeia de caracteres usado para prever o sentimento.</span><span class="sxs-lookup"><span data-stu-id="edcd9-213">For our schema, the first column (Label) is a <xref:System.Boolean> (the prediction) and the second column (SentimentText) is the feature of type text/string used for predicting the sentiment.</span></span>
<span data-ttu-id="edcd9-214">A classe `TextReader` retorna um <xref:Microsoft.ML.Runtime.Data.TextLoader> completamente inicializado</span><span class="sxs-lookup"><span data-stu-id="edcd9-214">The `TextReader` class returns a fully initialized <xref:Microsoft.ML.Runtime.Data.TextLoader></span></span>  

<span data-ttu-id="edcd9-215">Para inicializar a variável global `_textLoader` para reutilizá-la nos conjuntos de dados necessários, adicione o seguinte código após a inicialização de `mlContext`:</span><span class="sxs-lookup"><span data-stu-id="edcd9-215">To initialize the `_textLoader` global variable in order to reuse it for the needed datasets, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[initTextReader](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#4 "Initialize the TextReader")]

<span data-ttu-id="edcd9-216">Adicione o seguinte como a linha seguinte de código no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="edcd9-216">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[Train](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#5 "Train your model")]

<span data-ttu-id="edcd9-217">O método `Train` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="edcd9-217">The `Train` method executes the following tasks:</span></span>

* <span data-ttu-id="edcd9-218">Carrega os dados.</span><span class="sxs-lookup"><span data-stu-id="edcd9-218">Loads the data.</span></span>
* <span data-ttu-id="edcd9-219">Extrai e transforma os dados.</span><span class="sxs-lookup"><span data-stu-id="edcd9-219">Extracts and transforms the data.</span></span>
* <span data-ttu-id="edcd9-220">Treina o modelo.</span><span class="sxs-lookup"><span data-stu-id="edcd9-220">Trains the model.</span></span>
* <span data-ttu-id="edcd9-221">Prevê o sentimento com base nos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="edcd9-221">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="edcd9-222">Retorna o modelo.</span><span class="sxs-lookup"><span data-stu-id="edcd9-222">Returns the model.</span></span>

<span data-ttu-id="edcd9-223">Crie o método `Train`, logo após o método `Main`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="edcd9-223">Create the `Train` method, just after the `Main` method, using the following code:</span></span>

```csharp
 public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

<span data-ttu-id="edcd9-224">Observe que dois parâmetros são passados para o método Train. Um `MLContext` para o contexto (`mlContext`) e um <xref:System.String> para o caminho do conjunto de dados (`dataPath`).</span><span class="sxs-lookup"><span data-stu-id="edcd9-224">Notice that two parameters are passed into the Train method; a `MLContext` for the context (`mlContext`), and a <xref:System.String> for the dataset path (`dataPath`).</span></span> <span data-ttu-id="edcd9-225">Você vai usar esse método mais de uma vez para treinamento e teste.</span><span class="sxs-lookup"><span data-stu-id="edcd9-225">You're going to use this method more than once for training and testing.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="edcd9-226">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="edcd9-226">Load the data</span></span>

<span data-ttu-id="edcd9-227">Você carregará os dados usando a variável global `_textLoader` com o parâmetro `dataPath`.</span><span class="sxs-lookup"><span data-stu-id="edcd9-227">You'll load the data using the `_textLoader` global variable with the `dataPath` parameter.</span></span> <span data-ttu-id="edcd9-228">Ele retorna um <xref:Microsoft.ML.Runtime.Data.IDataView>.</span><span class="sxs-lookup"><span data-stu-id="edcd9-228">It returns a <xref:Microsoft.ML.Runtime.Data.IDataView>.</span></span> <span data-ttu-id="edcd9-229">Como a entrada e saída de `Transforms`, um `DataView` é o tipo de pipeline de dados fundamental, comparável ao `IEnumerable` para `LINQ`.</span><span class="sxs-lookup"><span data-stu-id="edcd9-229">As the input and output of `Transforms`, a `DataView` is the fundamental data pipeline type, comparable to `IEnumerable` for `LINQ`.</span></span>

<span data-ttu-id="edcd9-230">No ML.NET, os dados são semelhantes a um modo de exibição SQL.</span><span class="sxs-lookup"><span data-stu-id="edcd9-230">In ML.NET, data is similar to a SQL view.</span></span> <span data-ttu-id="edcd9-231">Eles são heterogêneos e avaliados e esquematizados lentamente.</span><span class="sxs-lookup"><span data-stu-id="edcd9-231">It is lazily evaluated, schematized, and heterogenous.</span></span> <span data-ttu-id="edcd9-232">O objeto é a primeira parte do pipeline e carrega os dados.</span><span class="sxs-lookup"><span data-stu-id="edcd9-232">The object is the first part of the pipeline, and loads the data.</span></span> <span data-ttu-id="edcd9-233">Neste tutorial, ele carrega um conjunto de dados com comentários e o sentimento tóxico ou não tóxico correspondente.</span><span class="sxs-lookup"><span data-stu-id="edcd9-233">For this tutorial, it loads a dataset with comments and corresponding toxic or non toxic sentiment.</span></span> <span data-ttu-id="edcd9-234">Isso é usado para criar o modelo e treiná-lo.</span><span class="sxs-lookup"><span data-stu-id="edcd9-234">This is used to create the model, and train it.</span></span>

 <span data-ttu-id="edcd9-235">Adicione o seguinte código como a primeira linha do método `Train`:</span><span class="sxs-lookup"><span data-stu-id="edcd9-235">Add the following code as the first line of the `Train` method:</span></span>

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#6 "loading training dataset")]

## <a name="extract-and-transform-the-data"></a><span data-ttu-id="edcd9-236">Extrair e transformar os dados</span><span class="sxs-lookup"><span data-stu-id="edcd9-236">Extract and transform the data</span></span>

<span data-ttu-id="edcd9-237">O pré-processamento e a limpeza de dados são tarefas importantes que ocorrem antes de um conjunto de dados ser usado efetivamente para o aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="edcd9-237">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="edcd9-238">Os dados brutos costumam ser ruidosos e pouco confiáveis, e podem apresentar valores faltantes.</span><span class="sxs-lookup"><span data-stu-id="edcd9-238">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="edcd9-239">Usar dados sem essas tarefas de modelagem pode produzir resultados enganosos.</span><span class="sxs-lookup"><span data-stu-id="edcd9-239">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="edcd9-240">Os pipelines de transformação do ML.NET compõem um conjunto personalizado de transformações que são aplicadas aos seus dados antes do treinamento ou teste.</span><span class="sxs-lookup"><span data-stu-id="edcd9-240">ML.NET's transform pipelines compose a custom set of transforms that are applied to your data before training or testing.</span></span> <span data-ttu-id="edcd9-241">A principal finalidade das transformações é a [personalização](../resources/glossary.md#feature-engineering) de dados.</span><span class="sxs-lookup"><span data-stu-id="edcd9-241">The transforms' primary purpose is data [featurization](../resources/glossary.md#feature-engineering).</span></span> <span data-ttu-id="edcd9-242">Os algoritmos de aprendizado de máquina entendem os [dados personalizados](../resources/glossary.md#feature), portanto, a próximo etapa é transformar nossos dados textuais em um formato que nossos algoritmos de aprendizado de máquina reconheçam.</span><span class="sxs-lookup"><span data-stu-id="edcd9-242">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, so the next step is to transform our textual data into a format that our ML algorithms recognize.</span></span> <span data-ttu-id="edcd9-243">Esse formato é um [vetor numérico](../resources/glossary.md#numerical-feature-vector).</span><span class="sxs-lookup"><span data-stu-id="edcd9-243">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="edcd9-244">Em seguida, chame `mlContext.Transforms.Text.FeaturizeText` que personaliza a coluna de texto (`SentimentText`) em um vetor numérico chamado `Features`, usado pelo algoritmo de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="edcd9-244">Next, call `mlContext.Transforms.Text.FeaturizeText` which featurizes the text column (`SentimentText`) column into a numeric vector called `Features` used by the machine learning algorithm.</span></span> <span data-ttu-id="edcd9-245">Essa é uma chamada de wrapper que retorna um <xref:Microsoft.ML.Runtime.Data.EstimatorChain%601> que será efetivamente um pipeline.</span><span class="sxs-lookup"><span data-stu-id="edcd9-245">This is a wrapper call that returns an <xref:Microsoft.ML.Runtime.Data.EstimatorChain%601> that will effectively be a pipeline.</span></span> <span data-ttu-id="edcd9-246">Dê ao `pipeline` um nome de sua preferência e, em seguida, anexe o instrutor à `EstimatorChain`.</span><span class="sxs-lookup"><span data-stu-id="edcd9-246">Name this `pipeline` as you will then append the trainer to the `EstimatorChain`.</span></span> <span data-ttu-id="edcd9-247">Adicione isso como a linha seguinte de código:</span><span class="sxs-lookup"><span data-stu-id="edcd9-247">Add this as the next line of code:</span></span>

[!code-csharp[TextFeaturizingEstimator](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#7 "Add a TextFeaturizingEstimator")]

<span data-ttu-id="edcd9-248">Esta é a etapa de pré-processamento/personalização.</span><span class="sxs-lookup"><span data-stu-id="edcd9-248">This is the preprocessing/featurization step.</span></span> <span data-ttu-id="edcd9-249">Usar componentes adicionais disponíveis no ML.NET pode permitir melhores resultados com o seu modelo.</span><span class="sxs-lookup"><span data-stu-id="edcd9-249">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="edcd9-250">Escolher um algoritmo de aprendizado</span><span class="sxs-lookup"><span data-stu-id="edcd9-250">Choose a learning algorithm</span></span>

<span data-ttu-id="edcd9-251">Para adicionar o instrutor, chame o método `mlContext.Transforms.Text.FeaturizeText` do wrapper que retorna um objeto <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer>.</span><span class="sxs-lookup"><span data-stu-id="edcd9-251">To add the trainer, call the `mlContext.Transforms.Text.FeaturizeText` wrapper method which returns a <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> object.</span></span> <span data-ttu-id="edcd9-252">Esse é um aprendiz de árvore de decisão que você usará neste pipeline.</span><span class="sxs-lookup"><span data-stu-id="edcd9-252">This is a decision tree learner you'll use in this pipeline.</span></span> <span data-ttu-id="edcd9-253">O `FastTreeBinaryClassificationTrainer` é anexado ao `pipeline` e aceita o parâmetro `SentimentText` (`Features`) personalizado e o parâmetro `Label` de entrada para aprender com os dados históricos.</span><span class="sxs-lookup"><span data-stu-id="edcd9-253">The `FastTreeBinaryClassificationTrainer` is appended to the `pipeline` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

<span data-ttu-id="edcd9-254">Adicione o seguinte código ao método `Train`:</span><span class="sxs-lookup"><span data-stu-id="edcd9-254">Add the following code to the `Train` method:</span></span>

[!code-csharp[FastTreeBinaryClassificationTrainer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#8 "Add a FastTreeBinaryClassificationTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="edcd9-255">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="edcd9-255">Train the model</span></span>

<span data-ttu-id="edcd9-256">Você treina o modelo, <xref:Microsoft.ML.Data.TransformerChain%601>, com base no conjunto de dados que foi carregado e transformado.</span><span class="sxs-lookup"><span data-stu-id="edcd9-256">You train the model, <xref:Microsoft.ML.Data.TransformerChain%601>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="edcd9-257">Depois que o avaliador tiver sido definido, treine o modelo usando o <xref:Microsoft.ML.Runtime.Data.EstimatorChain%601.Fit%2A> e forneça os dados de treinamento já carregados.</span><span class="sxs-lookup"><span data-stu-id="edcd9-257">Once the estimator has been defined, you train your model using the <xref:Microsoft.ML.Runtime.Data.EstimatorChain%601.Fit%2A> while providing the already loaded training data.</span></span> <span data-ttu-id="edcd9-258">Isso retornará um modelo que será usado nas previsões.</span><span class="sxs-lookup"><span data-stu-id="edcd9-258">This returns a model to use for predictions.</span></span> <span data-ttu-id="edcd9-259">`pipeline.Fit()` treina o pipeline e retorna um `Transformer` com base no `DataView` passado.</span><span class="sxs-lookup"><span data-stu-id="edcd9-259">`pipeline.Fit()` trains the pipeline and returns a `Transformer` based on the `DataView` passed in.</span></span> <span data-ttu-id="edcd9-260">O experimento não será executado até que isso ocorra.</span><span class="sxs-lookup"><span data-stu-id="edcd9-260">The experiment is not executed until this happens.</span></span>

<span data-ttu-id="edcd9-261">Adicione o seguinte código ao método `Train`:</span><span class="sxs-lookup"><span data-stu-id="edcd9-261">Add the following code to the `Train` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#9 "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="edcd9-262">Salvar e retornar o modelo treinado para usar na avaliação</span><span class="sxs-lookup"><span data-stu-id="edcd9-262">Save and Return the model trained to use for evaluation</span></span>

<span data-ttu-id="edcd9-263">Neste ponto, você tem um modelo de tipo <xref:Microsoft.ML.Data.TransformerChain%601> que pode ser integrado em qualquer um dos seus aplicativos .NET existentes ou novos.</span><span class="sxs-lookup"><span data-stu-id="edcd9-263">At this point, you have a model of type <xref:Microsoft.ML.Data.TransformerChain%601> that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="edcd9-264">Retorne o modelo no final do método `Train`.</span><span class="sxs-lookup"><span data-stu-id="edcd9-264">Return the model at the end of the `Train` method.</span></span>

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#10 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="edcd9-265">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="edcd9-265">Evaluate the model</span></span>

<span data-ttu-id="edcd9-266">Agora que você criou e treinou o modelo, precisa avaliá-lo com um conjunto de dados diferente para garantia de qualidade e validação.</span><span class="sxs-lookup"><span data-stu-id="edcd9-266">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="edcd9-267">No método `Evaluate`, o modelo criado em `Train` é passado para ser avaliado.</span><span class="sxs-lookup"><span data-stu-id="edcd9-267">In the `Evaluate` method, the model created in `Train` is passed in to be evaluated.</span></span> <span data-ttu-id="edcd9-268">Crie o método `Evaluate` , logo após `Train`, como no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="edcd9-268">Create the `Evaluate` method, just after `Train`, as in the following code:</span></span>

```csharp
public static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="edcd9-269">O método `Evaluate` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="edcd9-269">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="edcd9-270">Carrega o conjunto de dados de teste.</span><span class="sxs-lookup"><span data-stu-id="edcd9-270">Loads the test dataset.</span></span>
* <span data-ttu-id="edcd9-271">Cria o avaliador binário.</span><span class="sxs-lookup"><span data-stu-id="edcd9-271">Creates the binary evaluator.</span></span>
* <span data-ttu-id="edcd9-272">Avalia o modelo e cria métricas.</span><span class="sxs-lookup"><span data-stu-id="edcd9-272">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="edcd9-273">Exibe as métricas.</span><span class="sxs-lookup"><span data-stu-id="edcd9-273">Displays the metrics.</span></span>

<span data-ttu-id="edcd9-274">Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `Train`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="edcd9-274">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#11 "Call the Evaluate method")]

<span data-ttu-id="edcd9-275">Você carregará o conjunto de dados de teste usando a variável global `_textLoader` anteriormente inicializada com o campo global `_testDataPath`.</span><span class="sxs-lookup"><span data-stu-id="edcd9-275">You'll load the test dataset using the previously initialized  `_textLoader` global variable with the `_testDataPath` global field.</span></span> <span data-ttu-id="edcd9-276">Você pode avaliar o modelo usando esse conjunto de dados como uma verificação de qualidade.</span><span class="sxs-lookup"><span data-stu-id="edcd9-276">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="edcd9-277">Adicione o seguinte código ao método `Evaluate`:</span><span class="sxs-lookup"><span data-stu-id="edcd9-277">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#12 "Load the test dataset")]

<span data-ttu-id="edcd9-278">Em seguida, você usará o parâmetro `model` de aprendizado de máquina (um transformador) para inserir os recursos e retornar previsões.</span><span class="sxs-lookup"><span data-stu-id="edcd9-278">Next, you'll use the machine learning `model` parameter (a transformer) to input the features and return predictions.</span></span> <span data-ttu-id="edcd9-279">Adicione o seguinte código ao método `Evaluate` como a linha seguinte:</span><span class="sxs-lookup"><span data-stu-id="edcd9-279">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#13 "Predict using the Transformer")]

<span data-ttu-id="edcd9-280">O método `BinaryClassificationContext.Evaluate` calcula as métricas de qualidade para o `PredictionModel` usando o conjunto de dados especificado.</span><span class="sxs-lookup"><span data-stu-id="edcd9-280">The `BinaryClassificationContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="edcd9-281">Ele retorna um objeto `BinaryClassificationEvaluator.CalibratedResult` que contém as métricas gerais calculadas pelos avaliadores de classificação binária.</span><span class="sxs-lookup"><span data-stu-id="edcd9-281">It returns a `BinaryClassificationEvaluator.CalibratedResult` object contains the overall metrics computed by binary classification evaluators.</span></span> <span data-ttu-id="edcd9-282">Para exibi-los a fim de determinar a qualidade do modelo, é preciso primeiro obter as métricas.</span><span class="sxs-lookup"><span data-stu-id="edcd9-282">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="edcd9-283">Adicione o seguinte código ao método `Evaluate` como a linha seguinte:</span><span class="sxs-lookup"><span data-stu-id="edcd9-283">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#14 "Compute Metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="edcd9-284">Exibir as métricas para validação de modelo</span><span class="sxs-lookup"><span data-stu-id="edcd9-284">Displaying the metrics for model validation</span></span>

<span data-ttu-id="edcd9-285">Use o código a seguir para exibir as métricas, compartilhar os resultados e, em seguida, agir com relação a eles:</span><span class="sxs-lookup"><span data-stu-id="edcd9-285">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#15 "Display selected metrics")]

<span data-ttu-id="edcd9-286">Para salvar seu modelo como um arquivo .zip antes de retornar, adicione o seguinte código para chamar o método `SaveModelAsFile` como a linha seguinte em `TrainFinalModel`:</span><span class="sxs-lookup"><span data-stu-id="edcd9-286">To save your model to a .zip file before returning, add the following code to call the `SaveModelAsFile` method as the next line in `TrainFinalModel`:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#23 "Save the model")]

## <a name="save-the-model-as-azip-file"></a><span data-ttu-id="edcd9-287">Salvar o modelo como um arquivo .zip</span><span class="sxs-lookup"><span data-stu-id="edcd9-287">Save the model as a.zip file</span></span>

<span data-ttu-id="edcd9-288">Crie o método `SaveModelAsFile`, logo após o método `Evaluate`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="edcd9-288">Create the `SaveModelAsFile` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="edcd9-289">O método `SaveModelAsFile` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="edcd9-289">The `SaveModelAsFile` method executes the following tasks:</span></span>

* <span data-ttu-id="edcd9-290">Salva o modelo como um arquivo .zip.</span><span class="sxs-lookup"><span data-stu-id="edcd9-290">Saves the model as a .zip file.</span></span>

<span data-ttu-id="edcd9-291">Em seguida, crie um método para salvar o modelo para que ele possa ser reutilizado e consumido em outros aplicativos.</span><span class="sxs-lookup"><span data-stu-id="edcd9-291">Next, create a method to save the model so that it can be reused and consumed in other applications.</span></span> <span data-ttu-id="edcd9-292">O `ITransformer` tem um método <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.Runtime.IHostEnvironment,System.IO.Stream)> que usa o campo global `_modelPath` e um <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="edcd9-292">The `ITransformer` has a <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.Runtime.IHostEnvironment,System.IO.Stream)> method that takes in the `_modelPath` global field, and a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="edcd9-293">Para salvá-lo como um arquivo zip, você criará o `FileStream` imediatamente antes de chamar o método `SaveTo`.</span><span class="sxs-lookup"><span data-stu-id="edcd9-293">To save this as a zip file, you'll create the `FileStream` immediately before calling the `SaveTo` method.</span></span> <span data-ttu-id="edcd9-294">Adicione o seguinte código ao método `SaveModelAsFile` como a linha seguinte:</span><span class="sxs-lookup"><span data-stu-id="edcd9-294">Add the following code to the `SaveModelAsFile` method as the next line:</span></span>

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#24 "Add the SaveTo Method")]

<span data-ttu-id="edcd9-295">Você também pode exibir onde o arquivo foi gravado ao gravar uma mensagem de console com o `_modelPath`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="edcd9-295">You could also display where the file was written by writing a console message with the `_modelPath`, using the following code:</span></span>

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="predict-the-test-data-outcome-with-the-model-and-a-single-comment"></a><span data-ttu-id="edcd9-296">Prever os resultados dos dados de teste com o modelo e um único comentário</span><span class="sxs-lookup"><span data-stu-id="edcd9-296">Predict the test data outcome with the model and a single comment</span></span>

<span data-ttu-id="edcd9-297">Crie o método `Predict`, logo após o método `Evaluate`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="edcd9-297">Create the `Predict` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void Predict(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="edcd9-298">O método `Predict` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="edcd9-298">The `Predict` method executes the following tasks:</span></span>

* <span data-ttu-id="edcd9-299">Cria um único comentário dos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="edcd9-299">Creates a single comment of test data.</span></span>
* <span data-ttu-id="edcd9-300">Prevê o sentimento com base nos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="edcd9-300">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="edcd9-301">Combina dados de teste e previsões para relatórios.</span><span class="sxs-lookup"><span data-stu-id="edcd9-301">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="edcd9-302">Exibe os resultados previstos.</span><span class="sxs-lookup"><span data-stu-id="edcd9-302">Displays the predicted results.</span></span>

<span data-ttu-id="edcd9-303">Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `Evaluate`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="edcd9-303">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#16 "Call the Predict method")]

<span data-ttu-id="edcd9-304">Enquanto o `model` é um `transformer` que opera em muitas linhas de dados, um cenário de produção muito comum é a necessidade de previsões em exemplos individuais.</span><span class="sxs-lookup"><span data-stu-id="edcd9-304">While the `model` is a `transformer` that operates on many rows of data, a very common production scenario is a need for predictions on individual examples.</span></span> <span data-ttu-id="edcd9-305">O <xref:Microsoft.ML.Runtime.Data.PredictionFunction%602> é um wrapper que é retornado do método `MakePredictionFunction`.</span><span class="sxs-lookup"><span data-stu-id="edcd9-305">The <xref:Microsoft.ML.Runtime.Data.PredictionFunction%602> is a wrapper that is returned from the `MakePredictionFunction` method.</span></span> <span data-ttu-id="edcd9-306">Vamos adicionar o seguinte código para criar o PredictionFunction como a primeira linha no método `Predict`:</span><span class="sxs-lookup"><span data-stu-id="edcd9-306">Let's add the following code to create the PredictionFunction as the first line in the `Predict` Method:</span></span>

[!code-csharp[MakePredictionFunction](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#17 "Create the PredictionFunction")]
  
<span data-ttu-id="edcd9-307">Adicione um comentário para testar as previsões do modelo treinado no método `Predict` ao criar uma instância de `SentimentData`:</span><span class="sxs-lookup"><span data-stu-id="edcd9-307">Add a comment to test the trained model's prediction in the `Predict` method by creating an instance of `SentimentData`:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#18 "Create test data for single prediction")]


 <span data-ttu-id="edcd9-308">Você pode usar isso para prever o sentimento Tóxico ou Não Tóxico de uma única instância dos dados de comentário.</span><span class="sxs-lookup"><span data-stu-id="edcd9-308">You can use that to predict the Toxic or Non Toxic sentiment of a single instance of the comment data.</span></span> <span data-ttu-id="edcd9-309">Para obter uma previsão, use <xref:Microsoft.ML.Runtime.Data.PredictionFunction%602.Predict(%600)> nos dados.</span><span class="sxs-lookup"><span data-stu-id="edcd9-309">To get a prediction, use <xref:Microsoft.ML.Runtime.Data.PredictionFunction%602.Predict(%600)> on the data.</span></span> <span data-ttu-id="edcd9-310">Observe que os dados de entrada são uma cadeia de caracteres e o modelo inclui a personalização.</span><span class="sxs-lookup"><span data-stu-id="edcd9-310">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="edcd9-311">Seu pipeline está em sincronia durante o treinamento e a previsão.</span><span class="sxs-lookup"><span data-stu-id="edcd9-311">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="edcd9-312">Você não precisou escrever código de pré-processamento/personalização especificamente para previsões, e a mesma API cuida das previsões de lote e de uso único.</span><span class="sxs-lookup"><span data-stu-id="edcd9-312">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#19 "Create a prediction of sentiment")]

### <a name="model-operationalization-prediction"></a><span data-ttu-id="edcd9-313">Operacionalização do modelo: previsão</span><span class="sxs-lookup"><span data-stu-id="edcd9-313">Model operationalization: prediction</span></span>

<span data-ttu-id="edcd9-314">Exiba `SentimentText` e a previsão de sentimento correspondente para compartilhar os resultados e agir de acordo com eles.</span><span class="sxs-lookup"><span data-stu-id="edcd9-314">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="edcd9-315">Isso é chamado de operacionalização, usar os dados retornados como parte das políticas operacionais.</span><span class="sxs-lookup"><span data-stu-id="edcd9-315">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="edcd9-316">Crie uma exibição para os resultados usando o seguinte código <xref:System.Console.WriteLine?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="edcd9-316">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#20 "Display prediction output")]

## <a name="predict-the-test-data-outcomes-with-the-saved-model"></a><span data-ttu-id="edcd9-317">Prever os resultados dos dados de teste com o modelo salvo</span><span class="sxs-lookup"><span data-stu-id="edcd9-317">Predict the test data outcomes with the saved model</span></span>

<span data-ttu-id="edcd9-318">Crie o método `PredictWithModelLoadedFromFile`, logo antes do método `SaveModelAsFile`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="edcd9-318">Create the `PredictWithModelLoadedFromFile` method, just before the `SaveModelAsFile` method, using the following code:</span></span>

```csharp
public static void PredictWithModelLoadedFromFile(MLContext mlContext)
{

}
```

<span data-ttu-id="edcd9-319">O método `PredictWithModelLoadedFromFile` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="edcd9-319">The `PredictWithModelLoadedFromFile` method executes the following tasks:</span></span>

* <span data-ttu-id="edcd9-320">Cria dados de teste em lote.</span><span class="sxs-lookup"><span data-stu-id="edcd9-320">Creates batch test data.</span></span>
* <span data-ttu-id="edcd9-321">Prevê o sentimento com base nos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="edcd9-321">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="edcd9-322">Combina dados de teste e previsões para relatórios.</span><span class="sxs-lookup"><span data-stu-id="edcd9-322">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="edcd9-323">Exibe os resultados previstos.</span><span class="sxs-lookup"><span data-stu-id="edcd9-323">Displays the predicted results.</span></span>

<span data-ttu-id="edcd9-324">Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `Predict`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="edcd9-324">Add a call to the new method from the `Main` method, right under the `Predict` method call, using the following code:</span></span>

[!code-csharp[CallPredictModelLoaded](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#25 "Call the PredictWithModelLoadedFromFile method")]

<span data-ttu-id="edcd9-325">Adicione alguns comentários para testar as previsões do modelo treinado no método `PredictWithModelLoadedFromFile`:</span><span class="sxs-lookup"><span data-stu-id="edcd9-325">Add some comments to test the trained model's predictions in the `PredictWithModelLoadedFromFile` method:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#26 "Create test data for predictions")]

<span data-ttu-id="edcd9-326">Carregar o modelo [!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#27 "Load the model")]</span><span class="sxs-lookup"><span data-stu-id="edcd9-326">Load the model [!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#27 "Load the model")]</span></span>

<span data-ttu-id="edcd9-327">Agora que você tem um modelo, pode usá-lo para prever o sentimento tóxico ou não tóxico dos dados do comentário usando o método <xref:Microsoft.ML.Core.Data.ITransformer.Transform(Microsoft.ML.Runtime.Data.IDataView)>.</span><span class="sxs-lookup"><span data-stu-id="edcd9-327">Now that you have a model, you can use that to predict the Toxic or Non Toxic sentiment of the comment data using the <xref:Microsoft.ML.Core.Data.ITransformer.Transform(Microsoft.ML.Runtime.Data.IDataView)> method.</span></span> <span data-ttu-id="edcd9-328">Para obter uma previsão, use `Predict` em novos dados.</span><span class="sxs-lookup"><span data-stu-id="edcd9-328">To get a prediction, use `Predict` on new data.</span></span> <span data-ttu-id="edcd9-329">Observe que os dados de entrada são uma cadeia de caracteres e o modelo inclui a personalização.</span><span class="sxs-lookup"><span data-stu-id="edcd9-329">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="edcd9-330">Seu pipeline está em sincronia durante o treinamento e a previsão.</span><span class="sxs-lookup"><span data-stu-id="edcd9-330">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="edcd9-331">Você não precisou escrever código de pré-processamento/personalização especificamente para previsões, e a mesma API cuida das previsões de lote e de uso único.</span><span class="sxs-lookup"><span data-stu-id="edcd9-331">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span> <span data-ttu-id="edcd9-332">Adicione o código a seguir ao método `PredictWithModelLoadedFromFile` para as previsões:</span><span class="sxs-lookup"><span data-stu-id="edcd9-332">Add the following code to the `PredictWithModelLoadedFromFile` method for the predictions:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#28 "Create predictions of sentiments")]

### <a name="model-operationalization-prediction"></a><span data-ttu-id="edcd9-333">Operacionalização do modelo: previsão</span><span class="sxs-lookup"><span data-stu-id="edcd9-333">Model operationalization: prediction</span></span>

<span data-ttu-id="edcd9-334">Exiba `SentimentText` e a previsão de sentimento correspondente para compartilhar os resultados e agir de acordo com eles.</span><span class="sxs-lookup"><span data-stu-id="edcd9-334">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="edcd9-335">Isso é chamado de operacionalização, usar os dados retornados como parte das políticas operacionais.</span><span class="sxs-lookup"><span data-stu-id="edcd9-335">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="edcd9-336">Crie um cabeçalho para os resultados usando o seguinte código <xref:System.Console.WriteLine?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="edcd9-336">Create a header for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#29 "Display prediction outputs")]

<span data-ttu-id="edcd9-337">Antes de exibir os resultados previstos, combine o sentimento e a previsão juntos para ver o comentário original com o sentimento previsto.</span><span class="sxs-lookup"><span data-stu-id="edcd9-337">Before displaying the predicted results, combine the sentiment and prediction together to see the original comment with its predicted sentiment.</span></span> <span data-ttu-id="edcd9-338">O código a seguir usa o método <xref:System.Linq.Enumerable.Zip%2A> para que isso aconteça, então adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="edcd9-338">The following code uses the <xref:System.Linq.Enumerable.Zip%2A> method to make that happen, so add that code next:</span></span>

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#30 "Build the pairs of sentiment data and predictions")]

<span data-ttu-id="edcd9-339">Agora que você combinou `SentimentText` e `Sentiment` em uma classe, você pode exibir os resultados usando o método <xref:System.Console.WriteLine?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="edcd9-339">Now that you've combined the `SentimentText` and `Sentiment` into a class, you can display the results using the <xref:System.Console.WriteLine?displayProperty=nameWithType> method:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#31 "Display the predictions")]

<span data-ttu-id="edcd9-340">Como nomes de elementos de tuplas inferidos são um novo recurso no C# 7.1 e a versão da linguagem padrão do projeto é C# 7.0, é necessário alterar a versão da linguagem para C# 7.1 ou superior.</span><span class="sxs-lookup"><span data-stu-id="edcd9-340">Because inferred tuple element names are a new feature in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span>
<span data-ttu-id="edcd9-341">Para fazer isso, clique com o botão direito do mouse no nó do projeto no **Gerenciador de Soluções** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="edcd9-341">To do that, right-click on the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="edcd9-342">Selecione a guia **Build** e o botão **Avançado**.</span><span class="sxs-lookup"><span data-stu-id="edcd9-342">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="edcd9-343">No menu suspenso, selecione **C# 7.1** (ou uma versão posterior).</span><span class="sxs-lookup"><span data-stu-id="edcd9-343">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="edcd9-344">Selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="edcd9-344">Select the **OK** button.</span></span>

## <a name="results"></a><span data-ttu-id="edcd9-345">Resultados</span><span class="sxs-lookup"><span data-stu-id="edcd9-345">Results</span></span>

<span data-ttu-id="edcd9-346">Seus resultados devem ser semelhantes aos seguintes.</span><span class="sxs-lookup"><span data-stu-id="edcd9-346">Your results should be similar to the following.</span></span> <span data-ttu-id="edcd9-347">Conforme o pipeline processa, exibe mensagens.</span><span class="sxs-lookup"><span data-stu-id="edcd9-347">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="edcd9-348">Você pode ver avisos ou mensagens de processamento.</span><span class="sxs-lookup"><span data-stu-id="edcd9-348">You may see warnings, or processing messages.</span></span> <span data-ttu-id="edcd9-349">Eles foram removidos dos seguintes resultados para maior clareza.</span><span class="sxs-lookup"><span data-stu-id="edcd9-349">These have been removed from the following results for clarity.</span></span>

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 94.44%
Auc: 98.77%
F1Score: 94.74%
=============== End of model evaluation ===============

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This is a very rude movie | Prediction: Toxic | Probability: 0.5297049
=============== End of Predictions ===============

=============== New iteration of Model ===============
=============== Create and Train the Model ===============
=============== End of training ===============


The model is saved to: C:\Tutorial\SentimentAnalysis\bin\Debug\netcoreapp2.0\Data\Model.zip

=============== Prediction Test of loaded model with a multiple samples ===============

Sentiment: This is a very rude movie | Prediction: Toxic | Probability: 0.4585565
Sentiment: He is the best, and the article should say that. | Prediction: Not Toxic | Probability: 0.9924279

```

<span data-ttu-id="edcd9-350">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="edcd9-350">Congratulations!</span></span> <span data-ttu-id="edcd9-351">Agora você criou com sucesso um modelo de aprendizado de máquina para classificar e prever o sentimento das mensagens.</span><span class="sxs-lookup"><span data-stu-id="edcd9-351">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span> <span data-ttu-id="edcd9-352">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis).</span><span class="sxs-lookup"><span data-stu-id="edcd9-352">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="edcd9-353">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="edcd9-353">Next steps</span></span>

<span data-ttu-id="edcd9-354">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="edcd9-354">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="edcd9-355">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="edcd9-355">Understand the problem</span></span>
> * <span data-ttu-id="edcd9-356">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="edcd9-356">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="edcd9-357">Preparar seus dados</span><span class="sxs-lookup"><span data-stu-id="edcd9-357">Prepare your data</span></span>
> * <span data-ttu-id="edcd9-358">Criar o pipeline de aprendizado</span><span class="sxs-lookup"><span data-stu-id="edcd9-358">Create the learning pipeline</span></span>
> * <span data-ttu-id="edcd9-359">Carregar um classificador</span><span class="sxs-lookup"><span data-stu-id="edcd9-359">Load a classifier</span></span>
> * <span data-ttu-id="edcd9-360">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="edcd9-360">Train the model</span></span>
> * <span data-ttu-id="edcd9-361">Avaliar o modelo com um conjunto de dados diferente</span><span class="sxs-lookup"><span data-stu-id="edcd9-361">Evaluate the model with a different dataset</span></span>
> * <span data-ttu-id="edcd9-362">Prever os resultados dos dados de teste com o modelo</span><span class="sxs-lookup"><span data-stu-id="edcd9-362">Predict the test data outcomes with the model</span></span>

<span data-ttu-id="edcd9-363">Avançar para o próximo tutorial para saber mais</span><span class="sxs-lookup"><span data-stu-id="edcd9-363">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="edcd9-364">Previsão do valor da corrida do táxi</span><span class="sxs-lookup"><span data-stu-id="edcd9-364">Taxi Fare Predictor</span></span>](taxi-fare.md)
