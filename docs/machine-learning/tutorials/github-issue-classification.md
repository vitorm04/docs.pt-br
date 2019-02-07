---
title: Usar o ML.NET em um cenário de classificação multiclasse de problema do GitHub
description: Descubra como usar o ML.NET em um cenário de classificação multiclasse para classificar os problemas do GitHub a fim de atribuí-los a uma determinada área.
ms.date: 01/24/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: a951e884a7494b0dcc808fc3dafbfadebc5577dc
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254984"
---
# <a name="tutorial-use-mlnet-in-a-multiclass-classification-scenario-to-classify-github-issues"></a><span data-ttu-id="01cee-103">Tutorial: Use o ML.NET em um cenário de classificação multiclasse para classificar problemas do GitHub.</span><span class="sxs-lookup"><span data-stu-id="01cee-103">Tutorial: Use ML.NET in a multiclass classification scenario to classify GitHub issues.</span></span>

<span data-ttu-id="01cee-104">Este tutorial de exemplo ilustra o uso do ML.NET para criar um classificador de problema do GitHub por meio de um aplicativo de console do .NET Core usando C# no Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="01cee-104">This sample tutorial illustrates using ML.NET to create a GitHub issue classifier via a .NET Core console application using C# in Visual Studio 2017.</span></span>

<span data-ttu-id="01cee-105">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="01cee-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="01cee-106">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="01cee-106">Understand the problem</span></span>
> * <span data-ttu-id="01cee-107">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="01cee-107">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="01cee-108">Preparar seus dados</span><span class="sxs-lookup"><span data-stu-id="01cee-108">Prepare your data</span></span>
> * <span data-ttu-id="01cee-109">Criar o pipeline de aprendizado</span><span class="sxs-lookup"><span data-stu-id="01cee-109">Create the learning pipeline</span></span>
> * <span data-ttu-id="01cee-110">Carregar um classificador</span><span class="sxs-lookup"><span data-stu-id="01cee-110">Load a classifier</span></span>
> * <span data-ttu-id="01cee-111">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="01cee-111">Train the model</span></span>
> * <span data-ttu-id="01cee-112">Avaliar o modelo com um conjunto de dados diferente</span><span class="sxs-lookup"><span data-stu-id="01cee-112">Evaluate the model with a different dataset</span></span>
> * <span data-ttu-id="01cee-113">Prever uma única instância do resultado dos dados de teste com o modelo</span><span class="sxs-lookup"><span data-stu-id="01cee-113">Predict a single instance of test data outcome with the model</span></span>
> * <span data-ttu-id="01cee-114">Prever os resultados dos dados de teste com o modelo carregado</span><span class="sxs-lookup"><span data-stu-id="01cee-114">Predict the test data outcomes with a loaded model</span></span>

> [!NOTE]
> <span data-ttu-id="01cee-115">Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="01cee-115">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="01cee-116">Para obter mais informações, visite [a introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="01cee-116">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

## <a name="github-issue-sample-overview"></a><span data-ttu-id="01cee-117">Visão geral de exemplo de problema do GitHub</span><span class="sxs-lookup"><span data-stu-id="01cee-117">GitHub issue sample overview</span></span>

<span data-ttu-id="01cee-118">A amostra é um aplicativo de console que usa o ML.NET para treinar um modelo que classifica e prevê o rótulo da área para um problema do GitHub.</span><span class="sxs-lookup"><span data-stu-id="01cee-118">The sample is a console app that uses ML.NET to train a model that classifies and predicts the Area label for a GitHub issue.</span></span> <span data-ttu-id="01cee-119">Ele também avalia o modelo com um segundo conjunto de dados para análise de qualidade.</span><span class="sxs-lookup"><span data-stu-id="01cee-119">It also evaluates the model with a second dataset for quality analysis.</span></span> <span data-ttu-id="01cee-120">Os conjuntos de dados do problema são do repositório do GitHub do dotnet/corefx.</span><span class="sxs-lookup"><span data-stu-id="01cee-120">The issue datasets are from the dotnet/corefx GitHub repo.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="01cee-121">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="01cee-121">Prerequisites</span></span>

* <span data-ttu-id="01cee-122">[Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="01cee-122">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="01cee-123">O [arquivo de problemas do Github separados por tabulação (issues_train.tsv)](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span><span class="sxs-lookup"><span data-stu-id="01cee-123">The [Github issues tab separated file (issues_train.tsv)](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span></span>
* <span data-ttu-id="01cee-124">O [arquivo de testes de problemas do Github separados por tabulação (issues_test.tsv)](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span><span class="sxs-lookup"><span data-stu-id="01cee-124">The [Github issues test tab separated file (issues_test.tsv)](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="01cee-125">Fluxo de trabalho de aprendizado de máquina</span><span class="sxs-lookup"><span data-stu-id="01cee-125">Machine learning workflow</span></span>

<span data-ttu-id="01cee-126">Este tutorial segue um fluxo de trabalho de aprendizado de máquina que permite que o processo se mova de maneira ordenada.</span><span class="sxs-lookup"><span data-stu-id="01cee-126">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="01cee-127">As fases do fluxo de trabalho são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="01cee-127">The workflow phases are as follows:</span></span>

1. <span data-ttu-id="01cee-128">**Compreender o problema**</span><span class="sxs-lookup"><span data-stu-id="01cee-128">**Understand the problem**</span></span>
2. <span data-ttu-id="01cee-129">**Preparar seus dados**</span><span class="sxs-lookup"><span data-stu-id="01cee-129">**Prepare your data**</span></span>
   * <span data-ttu-id="01cee-130">**Carregar os dados**</span><span class="sxs-lookup"><span data-stu-id="01cee-130">**Load the data**</span></span>
   * <span data-ttu-id="01cee-131">**Extrair recursos (Transformar seus dados)**</span><span class="sxs-lookup"><span data-stu-id="01cee-131">**Extract features (Transform your data)**</span></span>
3. <span data-ttu-id="01cee-132">**Compilar e treinar**</span><span class="sxs-lookup"><span data-stu-id="01cee-132">**Build and train**</span></span> 
   * <span data-ttu-id="01cee-133">**Treinar o modelo**</span><span class="sxs-lookup"><span data-stu-id="01cee-133">**Train the model**</span></span>
   * <span data-ttu-id="01cee-134">**Avaliar o modelo**</span><span class="sxs-lookup"><span data-stu-id="01cee-134">**Evaluate the model**</span></span>
4. <span data-ttu-id="01cee-135">**Executar**</span><span class="sxs-lookup"><span data-stu-id="01cee-135">**Run**</span></span>
   * <span data-ttu-id="01cee-136">**Consumo do modelo**</span><span class="sxs-lookup"><span data-stu-id="01cee-136">**Model consumption**</span></span>

### <a name="understand-the-problem"></a><span data-ttu-id="01cee-137">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="01cee-137">Understand the problem</span></span>

<span data-ttu-id="01cee-138">Você primeiro precisa compreender o problema, para que possa dividi-lo em partes que possam oferecer suporte à criação e ao treinamento do modelo.</span><span class="sxs-lookup"><span data-stu-id="01cee-138">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="01cee-139">Dividir o problema permite prever e avaliar os resultados.</span><span class="sxs-lookup"><span data-stu-id="01cee-139">Breaking  down the problem allows you to predict and evaluate the results.</span></span>

<span data-ttu-id="01cee-140">O problema neste tutorial é entender a qual área os problemas do GitHub em entrada pertencem, para rotulá-los corretamente para priorização e agendamento.</span><span class="sxs-lookup"><span data-stu-id="01cee-140">The problem for this tutorial is to understand what area incoming GitHub issues belong to in order to label them correctly for prioritization and scheduling.</span></span>

<span data-ttu-id="01cee-141">Você pode dividir o problema no seguinte:</span><span class="sxs-lookup"><span data-stu-id="01cee-141">You can break down the problem to the following:</span></span>

* <span data-ttu-id="01cee-142">o texto de título do problema</span><span class="sxs-lookup"><span data-stu-id="01cee-142">the issue title text</span></span>
* <span data-ttu-id="01cee-143">o texto da descrição do problema</span><span class="sxs-lookup"><span data-stu-id="01cee-143">the issue description text</span></span>
* <span data-ttu-id="01cee-144">um valor de área para os dados de treinamento de modelo</span><span class="sxs-lookup"><span data-stu-id="01cee-144">an area value for the model training data</span></span>
* <span data-ttu-id="01cee-145">um valor de área prevista que você pode avaliar e, em seguida, usar operacionalmente</span><span class="sxs-lookup"><span data-stu-id="01cee-145">a predicted area value that you can evaluate and then use operationally</span></span>

<span data-ttu-id="01cee-146">Em seguida, você precisa **determinar** a área, o que ajuda na seleção da tarefa de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="01cee-146">You then need to **determine** the area, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="01cee-147">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="01cee-147">Select the appropriate machine learning task</span></span>

<span data-ttu-id="01cee-148">Com este problema, você está a par dos seguintes fatos:</span><span class="sxs-lookup"><span data-stu-id="01cee-148">With this problem, you know the following facts:</span></span>

<span data-ttu-id="01cee-149">Dados de treinamento:</span><span class="sxs-lookup"><span data-stu-id="01cee-149">Training data:</span></span>

<span data-ttu-id="01cee-150">Os problemas do GitHub podem ser rotulados em várias áreas (**Área**) como nos exemplos a seguir:</span><span class="sxs-lookup"><span data-stu-id="01cee-150">GitHub issues can be labeled in several areas (**Area**) as in the following examples:</span></span>

* <span data-ttu-id="01cee-151">area-System.Numerics</span><span class="sxs-lookup"><span data-stu-id="01cee-151">area-System.Numerics</span></span>
* <span data-ttu-id="01cee-152">area-System.Xml</span><span class="sxs-lookup"><span data-stu-id="01cee-152">area-System.Xml</span></span>
* <span data-ttu-id="01cee-153">area-Infrastructure</span><span class="sxs-lookup"><span data-stu-id="01cee-153">area-Infrastructure</span></span>
* <span data-ttu-id="01cee-154">area-System.Linq</span><span class="sxs-lookup"><span data-stu-id="01cee-154">area-System.Linq</span></span>
* <span data-ttu-id="01cee-155">area-System.IO</span><span class="sxs-lookup"><span data-stu-id="01cee-155">area-System.IO</span></span>

<span data-ttu-id="01cee-156">Preveja a **Área** de um novo problema do GitHub como nos exemplos a seguir:</span><span class="sxs-lookup"><span data-stu-id="01cee-156">Predict the **Area** of a new GitHub Issue such as in the following examples:</span></span>

* <span data-ttu-id="01cee-157">Contract.Assert versus Debug.Assert</span><span class="sxs-lookup"><span data-stu-id="01cee-157">Contract.Assert vs Debug.Assert</span></span>
* <span data-ttu-id="01cee-158">Tornar os campos somente leitura em System.Xml</span><span class="sxs-lookup"><span data-stu-id="01cee-158">Make fields readonly in System.Xml</span></span>

<span data-ttu-id="01cee-159">A tarefa de aprendizado da máquina de classificação é mais adequada para esse cenário.</span><span class="sxs-lookup"><span data-stu-id="01cee-159">The classification machine learning task is best suited for this scenario.</span></span>

### <a name="about-the-classification-task"></a><span data-ttu-id="01cee-160">Sobre a tarefa de classificação</span><span class="sxs-lookup"><span data-stu-id="01cee-160">About the classification task</span></span>

<span data-ttu-id="01cee-161">A classificação é uma tarefa de aprendizado de máquina que usa dados para **determinar** a categoria, o tipo ou a classe de um item ou linha de dados.</span><span class="sxs-lookup"><span data-stu-id="01cee-161">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="01cee-162">Por exemplo, você pode usar a classificação para:</span><span class="sxs-lookup"><span data-stu-id="01cee-162">For example, you can use classification to:</span></span>

* <span data-ttu-id="01cee-163">Identificar o sentimento como positivo ou negativo.</span><span class="sxs-lookup"><span data-stu-id="01cee-163">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="01cee-164">Classificar email como spam, lixo eletrônico ou bom.</span><span class="sxs-lookup"><span data-stu-id="01cee-164">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="01cee-165">Determinar se a amostra de laboratório de um paciente é cancerígena.</span><span class="sxs-lookup"><span data-stu-id="01cee-165">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="01cee-166">Categorizar os clientes pela sua propensão a responder a uma campanha de vendas.</span><span class="sxs-lookup"><span data-stu-id="01cee-166">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="01cee-167">Tarefas de classificação são frequentemente de um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="01cee-167">Classification tasks are frequently one of the following types:</span></span>

* <span data-ttu-id="01cee-168">Binário: A ou B.</span><span class="sxs-lookup"><span data-stu-id="01cee-168">Binary: either A or B.</span></span>
* <span data-ttu-id="01cee-169">Multiclasse: várias categorias que podem ser previstas usando um único modelo.</span><span class="sxs-lookup"><span data-stu-id="01cee-169">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="01cee-170">Para esse tipo de problema, use uma tarefa de classificação Multiclasse, como a previsão de categoria do problema pode ser uma das várias categorias (multiclasse), em vez de apenas duas (binário).</span><span class="sxs-lookup"><span data-stu-id="01cee-170">For this type of problem, use a Multiclass classification task, since your issue category prediction can be one of multiple categories (multiclass) rather than just two (binary).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="01cee-171">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="01cee-171">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="01cee-172">Criar um projeto</span><span class="sxs-lookup"><span data-stu-id="01cee-172">Create a project</span></span>

1. <span data-ttu-id="01cee-173">Abra o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="01cee-173">Open Visual Studio 2017.</span></span> <span data-ttu-id="01cee-174">Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="01cee-174">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="01cee-175">Na caixa de diálogo **Novo Projeto**, selecione o nó **Visual C#** seguido pelo nó **.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="01cee-175">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="01cee-176">Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="01cee-176">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="01cee-177">Na caixa de texto **Nome**, digite "SentimentAnalysis" e, em seguida, selecione o botão **OK** .</span><span class="sxs-lookup"><span data-stu-id="01cee-177">In the **Name** text box, type "SentimentAnalysis" and then select the **OK** button.</span></span>

2. <span data-ttu-id="01cee-178">Crie um diretório chamado *Data* no seu projeto para salvar seus arquivos do conjunto de dados:</span><span class="sxs-lookup"><span data-stu-id="01cee-178">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="01cee-179">No **Gerenciador de Soluções**, clique com o botão direito do mouse no seu projeto e selecione **Adicionar** > **Nova Pasta**.</span><span class="sxs-lookup"><span data-stu-id="01cee-179">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="01cee-180">Digite "Dados" e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="01cee-180">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="01cee-181">Instalar o **Pacote NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="01cee-181">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="01cee-182">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="01cee-182">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="01cee-183">Escolha "nuget.org" como a Origem do pacote, selecione a guia Procurar, pesquise por **Microsoft.ML**, selecione o pacote na lista e escolha o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="01cee-183">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="01cee-184">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="01cee-184">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="01cee-185">Preparar seus dados</span><span class="sxs-lookup"><span data-stu-id="01cee-185">Prepare your data</span></span>

1. <span data-ttu-id="01cee-186">Baixe os conjuntos de dados [issues_train.tsv](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) e [issues_test.tsv](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) e salve-os na pasta *Dados* criada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="01cee-186">Download the [issues_train.tsv](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) and the [issues_test.tsv](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="01cee-187">O primeiro conjunto de dados treina o modelo de aprendizado de máquina e o segundo pode ser usado para avaliar a precisão do seu modelo.</span><span class="sxs-lookup"><span data-stu-id="01cee-187">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="01cee-188">No Gerenciador de Soluções, clique com o botão direito do mouse em cada um dos arquivos \*.tsv e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="01cee-188">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="01cee-189">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.</span><span class="sxs-lookup"><span data-stu-id="01cee-189">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="01cee-190">Criar classes e definir demarcadores</span><span class="sxs-lookup"><span data-stu-id="01cee-190">Create classes and define paths</span></span>

<span data-ttu-id="01cee-191">Adicione as seguintes instruções `using` adicionais ao início do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="01cee-191">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

<span data-ttu-id="01cee-192">Você precisa criar três campos ​​globais para manter os caminhos dos arquivos baixados recentemente e uma variável global para o `TextLoader`:</span><span class="sxs-lookup"><span data-stu-id="01cee-192">You need to create three global fields to hold the paths to the recently downloaded files, and a global variable for the `TextLoader`:</span></span>

* <span data-ttu-id="01cee-193">`_trainDataPath` tem o demarcador para o conjunto de dados usado para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="01cee-193">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="01cee-194">`_testDataPath` tem o demarcador para o conjunto de dados usado para avaliar o modelo.</span><span class="sxs-lookup"><span data-stu-id="01cee-194">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="01cee-195">`_modelPath` tem o demarcador em que o modelo treinado é salvo.</span><span class="sxs-lookup"><span data-stu-id="01cee-195">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="01cee-196">`_mlContext` é o <xref:Microsoft.ML.MLContext> que fornece o contexto de processamento.</span><span class="sxs-lookup"><span data-stu-id="01cee-196">`_mlContext` is the <xref:Microsoft.ML.MLContext> that provides processing context.</span></span>
* <span data-ttu-id="01cee-197">`_trainingDataView` é o <xref:Microsoft.ML.Data.IDataView> usado para processar o conjunto de dados de treinamento.</span><span class="sxs-lookup"><span data-stu-id="01cee-197">`_trainingDataView` is the <xref:Microsoft.ML.Data.IDataView> used to process the training dataset.</span></span>
* <span data-ttu-id="01cee-198">`_predEngine` é o <xref:Microsoft.ML.PredictionEngine%602> usado para previsões individuais.</span><span class="sxs-lookup"><span data-stu-id="01cee-198">`_predEngine` is the <xref:Microsoft.ML.PredictionEngine%602> used for single predictions.</span></span>
* <span data-ttu-id="01cee-199">O `_reader` é o <xref:Microsoft.ML.Data.TextLoader> usado para carregar e transformar os conjuntos de dados.</span><span class="sxs-lookup"><span data-stu-id="01cee-199">`_reader` is the <xref:Microsoft.ML.Data.TextLoader> used to load and transform the datasets.</span></span>

<span data-ttu-id="01cee-200">Adicione o seguinte código à linha logo acima do método `Main` para especificar estes caminhos e as outras variáveis:</span><span class="sxs-lookup"><span data-stu-id="01cee-200">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="01cee-201">Você precisa criar algumas classes para os dados e previsões de entrada.</span><span class="sxs-lookup"><span data-stu-id="01cee-201">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="01cee-202">Adicione uma nova classe ao seu projeto:</span><span class="sxs-lookup"><span data-stu-id="01cee-202">Add a new class to your project:</span></span>

1. <span data-ttu-id="01cee-203">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="01cee-203">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="01cee-204">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *GitHubIssueData.cs*.</span><span class="sxs-lookup"><span data-stu-id="01cee-204">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *GitHubIssueData.cs*.</span></span> <span data-ttu-id="01cee-205">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="01cee-205">Then, select the **Add** button.</span></span>

    <span data-ttu-id="01cee-206">O arquivo *GitHubIssueData.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="01cee-206">The *GitHubIssueData.cs* file opens in the code editor.</span></span> <span data-ttu-id="01cee-207">Adicione a seguinte instrução `using` acima de *GitHubIssueData.cs*:</span><span class="sxs-lookup"><span data-stu-id="01cee-207">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

<span data-ttu-id="01cee-208">Remova a definição de classe existente e adicione o seguinte código, que tem duas classes, `GitHubIssue` e `IssuePrediction`, ao arquivo *GitHubIssueData.cs*:</span><span class="sxs-lookup"><span data-stu-id="01cee-208">Remove the existing class definition and add the following code, which has two classes `GitHubIssue` and `IssuePrediction`, to the *GitHubIssueData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

<span data-ttu-id="01cee-209">`GitHubIssue` é a classe de conjunto de dados de entrada e tem os seguintes campos <xref:System.String>:</span><span class="sxs-lookup"><span data-stu-id="01cee-209">`GitHubIssue` is the input dataset class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="01cee-210">`ID` contém um valor para a ID do problema do GitHub</span><span class="sxs-lookup"><span data-stu-id="01cee-210">`ID` contains a value for the GitHub issue ID</span></span>
* <span data-ttu-id="01cee-211">`Area` contém um valor para o rótulo `Area`</span><span class="sxs-lookup"><span data-stu-id="01cee-211">`Area` contains a value for the `Area` label</span></span>
* <span data-ttu-id="01cee-212">`Title` contém o título do problema do GitHub</span><span class="sxs-lookup"><span data-stu-id="01cee-212">`Title` contains the GitHub issue title</span></span>
* <span data-ttu-id="01cee-213">`Description` contém a descrição do problema do GitHub</span><span class="sxs-lookup"><span data-stu-id="01cee-213">`Description` contains the GitHub issue description</span></span>

<span data-ttu-id="01cee-214">`IssuePrediction` é a classe usada para previsão depois que o modelo foi treinado.</span><span class="sxs-lookup"><span data-stu-id="01cee-214">`IssuePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="01cee-215">Tem um único `string` (`Area`) e um atributo `PredictedLabel` `ColumnName`.</span><span class="sxs-lookup"><span data-stu-id="01cee-215">It has a single `string` (`Area`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="01cee-216">O `Label` é usado para criar e treinar o modelo e também é usado com um segundo conjunto de dados para avaliar o modelo.</span><span class="sxs-lookup"><span data-stu-id="01cee-216">The `Label` is used to create and train the model, and it's also used with a second dataset to evaluate the model.</span></span> <span data-ttu-id="01cee-217">O `PredictedLabel` é usado durante a previsão e avaliação.</span><span class="sxs-lookup"><span data-stu-id="01cee-217">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="01cee-218">Para avaliação, uma entrada com dados de treinamento, os valores previstos e o modelo são usados.</span><span class="sxs-lookup"><span data-stu-id="01cee-218">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="01cee-219">Ao criar um modelo com o ML.NET, comece criando um <xref:Microsoft.ML.MLContext>.</span><span class="sxs-lookup"><span data-stu-id="01cee-219">When building a model with ML.NET, you start by creating an <xref:Microsoft.ML.MLContext>.</span></span> <span data-ttu-id="01cee-220">Isso é comparável conceitualmente ao uso de `DbContext` no Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="01cee-220">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span> <span data-ttu-id="01cee-221">O ambiente fornece um contexto para seu trabalho de ML que pode ser usado no acompanhamento e registro em log da exceção.</span><span class="sxs-lookup"><span data-stu-id="01cee-221">The environment provides a context for your ML job that can be used for exception tracking and logging.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="01cee-222">Inicializar variáveis em Main</span><span class="sxs-lookup"><span data-stu-id="01cee-222">Initialize variables in Main</span></span>

<span data-ttu-id="01cee-223">Inicialize a variável global `_mlContext` com uma nova instância de `MLContext` com uma semente aleatória (`seed: 0`) para obter resultados repetíveis/determinísticos entre vários treinamentos.</span><span class="sxs-lookup"><span data-stu-id="01cee-223">Initialize the `_mlContext` global variable  with a new instance of `MLContext` with a random seed (`seed: 0`) for repeatable/deterministic results across multiple trainings.</span></span>  <span data-ttu-id="01cee-224">Substitua a linha `Console.WriteLine("Hello World!")` pelo seguinte código no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="01cee-224">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a><span data-ttu-id="01cee-225">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="01cee-225">Load the data</span></span>

<span data-ttu-id="01cee-226">Carregaremos os dados usando a variável global `_trainingDataView` <xref:Microsoft.ML.Data.IDataView> com o parâmetro `_trainDataPath`.</span><span class="sxs-lookup"><span data-stu-id="01cee-226">Next, initialize the `_trainingDataView` <xref:Microsoft.ML.Data.IDataView> global variable and load the data with the `_trainDataPath` parameter.</span></span>

 <span data-ttu-id="01cee-227">Como a entrada e saída de `Transforms`, um `DataView` é o tipo de pipeline de dados fundamental, comparável ao `IEnumerable` para `LINQ`.</span><span class="sxs-lookup"><span data-stu-id="01cee-227">As the input and output of `Transforms`, a `DataView` is the fundamental data pipeline type, comparable to `IEnumerable` for `LINQ`.</span></span>

<span data-ttu-id="01cee-228">No ML.NET, os dados são semelhantes a um `SQL view`.</span><span class="sxs-lookup"><span data-stu-id="01cee-228">In ML.NET, data is similar to a `SQL view`.</span></span> <span data-ttu-id="01cee-229">Eles são heterogêneos e avaliados e esquematizados lentamente.</span><span class="sxs-lookup"><span data-stu-id="01cee-229">It is lazily evaluated, schematized, and heterogenous.</span></span> <span data-ttu-id="01cee-230">O objeto é a primeira parte do pipeline e carrega os dados.</span><span class="sxs-lookup"><span data-stu-id="01cee-230">The object is the first part of the pipeline, and loads the data.</span></span> <span data-ttu-id="01cee-231">Para este tutorial, ele carrega um conjunto de dados com títulos, descrições e rótulo do GitHub da área correspondente do problema.</span><span class="sxs-lookup"><span data-stu-id="01cee-231">For this tutorial, it loads a dataset with issue titles, descriptions, and corresponding area GitHub label.</span></span> <span data-ttu-id="01cee-232">O `DataView` é usado para criar o modelo e treiná-lo.</span><span class="sxs-lookup"><span data-stu-id="01cee-232">The `DataView` is used to create and train the model.</span></span>

<span data-ttu-id="01cee-233">Já que o tipo do modelo de dados `GitHubIssue` criado anteriormente corresponde ao esquema de conjunto de dados, você pode combinar a inicialização, o mapeamento e o carregamento de conjunto de dados em uma única linha de código.</span><span class="sxs-lookup"><span data-stu-id="01cee-233">Since your previously created `GitHubIssue` data model type matches the dataset schema, you can combine the initialization, mapping, and dataset loading into one line of code.</span></span>

<span data-ttu-id="01cee-234">A primeira parte da linha (`CreateTextReader<GitHubIssue>(hasHeader: true)`) cria um <xref:Microsoft.ML.Data.TextLoader> por inferência de esquema de conjunto de dados do tipo de modelo de dados `GitHubIssue` e usando o cabeçalho do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="01cee-234">The first part of the line (`CreateTextReader<GitHubIssue>(hasHeader: true)`) creates a <xref:Microsoft.ML.Data.TextLoader> by inferencing the dataset schema from the `GitHubIssue` data model type and using the dataset header.</span></span>

<span data-ttu-id="01cee-235">Você definiu o esquema de dados anteriormente ao criar a classe `GitHubIssue`.</span><span class="sxs-lookup"><span data-stu-id="01cee-235">You defined the data schema previously when you created the `GitHubIssue` class.</span></span> <span data-ttu-id="01cee-236">Para o esquema:</span><span class="sxs-lookup"><span data-stu-id="01cee-236">For your schema:</span></span>

* <span data-ttu-id="01cee-237">a primeira coluna `ID` (ID de problema do GitHub)</span><span class="sxs-lookup"><span data-stu-id="01cee-237">the first column `ID` (GitHub Issue ID)</span></span>
* <span data-ttu-id="01cee-238">a segunda coluna `Area` (a previsão do treinamento)</span><span class="sxs-lookup"><span data-stu-id="01cee-238">the second column `Area` (the prediction for training)</span></span>
* <span data-ttu-id="01cee-239">a terceira coluna `Title` (título do problema de GitHub) é o primeiro [recurso](../resources/glossary.md##feature) usado para prever o `Area`</span><span class="sxs-lookup"><span data-stu-id="01cee-239">the third column `Title` (GitHub issue title) is the first [feature](../resources/glossary.md##feature)  used for predicting the `Area`</span></span>
* <span data-ttu-id="01cee-240">a quarta coluna `Description` é o segundo recurso usado para prever o `Area`</span><span class="sxs-lookup"><span data-stu-id="01cee-240">the fourth column  `Description` is the second feature used for predicting the `Area`</span></span>

<span data-ttu-id="01cee-241">A segunda parte da linha (`.Read(_trainDataPath)`) usa o método <xref:Microsoft.ML.Data.TextLoader.Read%2A> para carregar o arquivo de texto de treinamento usando o `_trainDataPath` na variável global `IDataView` (`_trainingDataView`).</span><span class="sxs-lookup"><span data-stu-id="01cee-241">The second part of the line  (`.Read(_trainDataPath)`) uses <xref:Microsoft.ML.Data.TextLoader.Read%2A> method to load the training text file using `_trainDataPath` into the `IDataView` (`_trainingDataView`) global variable.</span></span>  

<span data-ttu-id="01cee-242">Para inicializar e carregar a variável global `_trainingDataView` para utilizá-la para o pipeline, adicione o seguinte código após a inicialização de `mlContext`:</span><span class="sxs-lookup"><span data-stu-id="01cee-242">To initialize and load the `_trainingDataView` global variable in order to use it for the pipeline, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]


<span data-ttu-id="01cee-243">Adicione o seguinte como a linha seguinte de código no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="01cee-243">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallProcessData](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

<span data-ttu-id="01cee-244">O método `ProcessData` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="01cee-244">The `ProcessData` method executes the following tasks:</span></span>

* <span data-ttu-id="01cee-245">Extrai e transforma os dados.</span><span class="sxs-lookup"><span data-stu-id="01cee-245">Extracts and transforms the data.</span></span>
* <span data-ttu-id="01cee-246">Retorna o pipeline de processamento.</span><span class="sxs-lookup"><span data-stu-id="01cee-246">Returns the processing pipeline.</span></span>

<span data-ttu-id="01cee-247">Crie o método `ProcessData`, logo após o método `Main`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="01cee-247">Create the `ProcessData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static EstimatorChain<ITransformer> ProcessData()
{

}
```

## <a name="extract-and-transform-the-data"></a><span data-ttu-id="01cee-248">Extrair e transformar os dados</span><span class="sxs-lookup"><span data-stu-id="01cee-248">Extract and transform the data</span></span>

<span data-ttu-id="01cee-249">O pré-processamento e a limpeza de dados são tarefas importantes que ocorrem antes de um conjunto de dados ser usado efetivamente para o aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="01cee-249">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="01cee-250">Os dados brutos costumam ser ruidosos e pouco confiáveis, e podem apresentar valores faltantes.</span><span class="sxs-lookup"><span data-stu-id="01cee-250">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="01cee-251">Usar dados sem essas tarefas de modelagem pode produzir resultados enganosos.</span><span class="sxs-lookup"><span data-stu-id="01cee-251">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="01cee-252">Os pipelines de transformação do ML.NET compõem um conjunto personalizado de transformações que são aplicadas aos seus dados antes do treinamento ou teste.</span><span class="sxs-lookup"><span data-stu-id="01cee-252">ML.NET's transform pipelines compose a custom set of transforms that are applied to your data before training or testing.</span></span> <span data-ttu-id="01cee-253">A principal finalidade das transformações é a [personalização](../resources/glossary.md#feature-engineering) de dados.</span><span class="sxs-lookup"><span data-stu-id="01cee-253">The transforms' primary purpose is data [featurization](../resources/glossary.md#feature-engineering).</span></span> <span data-ttu-id="01cee-254">Os algoritmos de aprendizado de máquina entendem os [dados personalizados](../resources/glossary.md#feature), portanto, a próximo etapa é transformar nossos dados textuais em um formato que nossos algoritmos de aprendizado de máquina reconheçam.</span><span class="sxs-lookup"><span data-stu-id="01cee-254">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, so the next step is to transform our textual data into a format that our ML algorithms recognize.</span></span> <span data-ttu-id="01cee-255">Esse formato é um [vetor numérico](../resources/glossary.md#numerical-feature-vector).</span><span class="sxs-lookup"><span data-stu-id="01cee-255">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="01cee-256">Nas próximas etapas, trataremos das colunas pelos nomes definidos na classe `GitHubIssue`.</span><span class="sxs-lookup"><span data-stu-id="01cee-256">In the next steps, we refer to the columns by the names defined in the `GitHubIssue` class.</span></span>

<span data-ttu-id="01cee-257">Quando o modelo é treinado e avaliado, por padrão, os valores na coluna **Rótulo** são considerados os valores corretos a serem previstos.</span><span class="sxs-lookup"><span data-stu-id="01cee-257">When the model is trained and evaluated, by default, the values in the **Label** column are considered as correct values to be predicted.</span></span> <span data-ttu-id="01cee-258">Como queremos prever o rótulo do GitHub da Área para um `GitHubIssue`, copie a coluna `Area` na coluna **Rótulo**.</span><span class="sxs-lookup"><span data-stu-id="01cee-258">As we want to predict the Area GitHub label for a `GitHubIssue`, copy the `Area` column into the **Label** column.</span></span> <span data-ttu-id="01cee-259">Para fazer isso, use o `MLContext.Transforms.Conversion.MapValueToKey`, que é um wrapper para a classe de transformação <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="01cee-259">To do that, use the `MLContext.Transforms.Conversion.MapValueToKey`, which is a wrapper for the <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A> transformation class.</span></span>  <span data-ttu-id="01cee-260">O <xref:Microsoft.ML.Data.EstimatorChain%601> retorna um `MapValueToKey` que será efetivamente um pipeline.</span><span class="sxs-lookup"><span data-stu-id="01cee-260">The `MapValueToKey` returns an <xref:Microsoft.ML.Data.EstimatorChain%601> that will effectively be a pipeline.</span></span> <span data-ttu-id="01cee-261">Dê ao `pipeline` um nome de sua preferência e, em seguida, anexe o instrutor à `EstimatorChain`.</span><span class="sxs-lookup"><span data-stu-id="01cee-261">Name this `pipeline` as you will then append the trainer to the `EstimatorChain`.</span></span> <span data-ttu-id="01cee-262">Adicione isso como a linha seguinte de código:</span><span class="sxs-lookup"><span data-stu-id="01cee-262">Add this as the next line of code:</span></span>

[!code-csharp[MapValueToKey](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

<span data-ttu-id="01cee-263">O algoritmo que treina o modelo exige recursos **numéricos**, portanto, chame `mlContext.Transforms.Text.FeaturizeText` em seguida, que personaliza as colunas de texto (`Title` e `Description`) em um vetor numérico para cada `TitleFeaturized` e `DescriptionFeaturized` chamados.</span><span class="sxs-lookup"><span data-stu-id="01cee-263">The algorithm that trains the model requires **numeric** features, so you have Next, call `mlContext.Transforms.Text.FeaturizeText` which featurizes the text (`Title` and `Description`) columns into a numeric vector for each called `TitleFeaturized` and `DescriptionFeaturized`.</span></span> <span data-ttu-id="01cee-264">A personalização atribui valores de chaves numéricas diferentes para os diferentes valores em cada uma das colunas e é usado pelo algoritmo de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="01cee-264">Featurizing assigns different numeric key values to the different values in each of the columns and is used by the machine learning algorithm.</span></span>
<span data-ttu-id="01cee-265">Acrescente a personalização para ambas as colunas ao pipeline com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="01cee-265">Append the featurization for both columns to the pipeline with the following code:</span></span>

[!code-csharp[FeaturizeText](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

<span data-ttu-id="01cee-266">A última etapa na preparação de dados combina todas as colunas de recursos na coluna **Features** usando a classe de transformação `Concatenate`.</span><span class="sxs-lookup"><span data-stu-id="01cee-266">The last step in data preparation combines all of the feature columns into the **Features** column using the `Concatenate` transformation class.</span></span> <span data-ttu-id="01cee-267">Por padrão, um algoritmo de aprendizado processa apenas os recursos da coluna **Features**.</span><span class="sxs-lookup"><span data-stu-id="01cee-267">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="01cee-268">Acrescente esta transformação ao pipeline com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="01cee-268">Append this transformation to the pipeline with the following code:</span></span>

[!code-csharp[Concatenate](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 <span data-ttu-id="01cee-269">Em seguida, acrescente um <xref:Microsoft.ML.Data.EstimatorChain`1.AppendCacheCheckpoint%2A> para armazenar em cache o DataView, de modo que, quando iterar pelos dados várias vezes usando o cache, você possa obter um melhor desempenho, assim como acontece com o código a seguir</span><span class="sxs-lookup"><span data-stu-id="01cee-269">Next, append a <xref:Microsoft.ML.Data.EstimatorChain`1.AppendCacheCheckpoint%2A> to cache the DataView so when you iterate over the data multiple times using the cache might get better performance, as with the following code</span></span>

[!code-csharp[AppendCache](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

<span data-ttu-id="01cee-270">Retorne o pipeline no final do método `ProcessData`.</span><span class="sxs-lookup"><span data-stu-id="01cee-270">Return the pipeline at the end of the `ProcessData` method.</span></span>

[!code-csharp[ReturnPipeline](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

<span data-ttu-id="01cee-271">Esta etapa manipula o pré-processamento/personalização.</span><span class="sxs-lookup"><span data-stu-id="01cee-271">This step handles preprocessing/featurization.</span></span> <span data-ttu-id="01cee-272">Usar componentes adicionais disponíveis no ML.NET pode permitir melhores resultados com o seu modelo.</span><span class="sxs-lookup"><span data-stu-id="01cee-272">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="build-and-train-the-model"></a><span data-ttu-id="01cee-273">Criar e treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="01cee-273">Build and train the model</span></span>

<span data-ttu-id="01cee-274">Adicione a seguinte chamada ao método `BuildAndTrainModel` como a próxima linha de código no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="01cee-274">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="01cee-275">O método `BuildAndTrainModel` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="01cee-275">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="01cee-276">Cria a classe de algoritmo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="01cee-276">Creates the training algorithm class.</span></span>
* <span data-ttu-id="01cee-277">Treina o modelo.</span><span class="sxs-lookup"><span data-stu-id="01cee-277">Trains the model.</span></span>
* <span data-ttu-id="01cee-278">Prevê a área com base em dados de treinamento.</span><span class="sxs-lookup"><span data-stu-id="01cee-278">Predicts area based on training data.</span></span>
* <span data-ttu-id="01cee-279">Salva o modelo em um arquivo `.zip`.</span><span class="sxs-lookup"><span data-stu-id="01cee-279">Saves the model to a `.zip` file.</span></span>
* <span data-ttu-id="01cee-280">Retorna o modelo.</span><span class="sxs-lookup"><span data-stu-id="01cee-280">Returns the model.</span></span>

<span data-ttu-id="01cee-281">Crie o método `BuildAndTrainModel`, logo após o método `Main`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="01cee-281">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static void BuildAndTrainModel()
{

}
```

<span data-ttu-id="01cee-282">Observe que dois parâmetros são passados para o método BuildAndTrainModel; um `IDataView` para o conjunto de dados de treinamento (`trainingDataView`) e um <xref:Microsoft.ML.Data.EstimatorChain%601> para o pipeline de processamento criado no ProcessData (`pipeline`).</span><span class="sxs-lookup"><span data-stu-id="01cee-282">Notice that two parameters are passed into the BuildAndTrainModel method; an `IDataView` for the training dataset (`trainingDataView`), and a <xref:Microsoft.ML.Data.EstimatorChain%601> for the processing pipeline created in ProcessData (`pipeline`).</span></span>

 <span data-ttu-id="01cee-283">Adicione o seguinte código como a primeira linha do método `BuildAndTrainModel`:</span><span class="sxs-lookup"><span data-stu-id="01cee-283">Add the following code as the first line of the `BuildAndTrainModel` method:</span></span>

### <a name="choose-a-trainer-algorithm"></a><span data-ttu-id="01cee-284">Escolha um algoritmo instrutor</span><span class="sxs-lookup"><span data-stu-id="01cee-284">Choose a trainer algorithm</span></span>

<span data-ttu-id="01cee-285">Para adicionar o algoritmo instrutor, chame o método `mlContext.Transforms.Text.FeaturizeText` do wrapper que retorna um objeto <xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer>.</span><span class="sxs-lookup"><span data-stu-id="01cee-285">To add the trainer algorithm, call the `mlContext.Transforms.Text.FeaturizeText` wrapper method which returns a <xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer> object.</span></span> <span data-ttu-id="01cee-286">Esse é um aprendiz de árvore de decisão que você usará neste pipeline.</span><span class="sxs-lookup"><span data-stu-id="01cee-286">This is a decision tree learner you'll use in this pipeline.</span></span> <span data-ttu-id="01cee-287">O `SdcaMultiClassTrainer` é anexado ao `pipeline` e aceita os `Title` e `Description` (`Features`) personalizados e os parâmetro de entrada `Label` para aprender com os dados históricos.</span><span class="sxs-lookup"><span data-stu-id="01cee-287">The `SdcaMultiClassTrainer` is appended to the `pipeline` and accepts the featurized `Title` and `Description` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

<span data-ttu-id="01cee-288">Adicione o seguinte código ao método `BuildAndTrainModel`:</span><span class="sxs-lookup"><span data-stu-id="01cee-288">Add the following code to the `BuildAndTrainModel` method:</span></span>

[!code-csharp[SdcaMultiClassTrainer](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SdcaMultiClassTrainer)]

<span data-ttu-id="01cee-289">Agora que você criou um algoritmo de instrutor, acrescente-o ao `pipeline`.</span><span class="sxs-lookup"><span data-stu-id="01cee-289">Now that you've created a trainer algorithm, append it to the `pipeline`.</span></span> <span data-ttu-id="01cee-290">Você também precisa mapear o rótulo para o valor para retorná-lo ao seu estado legível original.</span><span class="sxs-lookup"><span data-stu-id="01cee-290">You also need to map the label to the value to return to its original readable state.</span></span> <span data-ttu-id="01cee-291">Realize ambas essas ações com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="01cee-291">Do both of those actions with the following code:</span></span>

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

### <a name="train-the-model"></a><span data-ttu-id="01cee-292">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="01cee-292">Train the model</span></span>

<span data-ttu-id="01cee-293">Você treina o modelo, <xref:Microsoft.ML.Data.TransformerChain%601>, com base no conjunto de dados que foi carregado e transformado.</span><span class="sxs-lookup"><span data-stu-id="01cee-293">You train the model, <xref:Microsoft.ML.Data.TransformerChain%601>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="01cee-294">Depois que o avaliador tiver sido definido, treine o modelo usando o <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> e forneça os dados de treinamento já carregados.</span><span class="sxs-lookup"><span data-stu-id="01cee-294">Once the estimator has been defined, you train your model using the <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> while providing the already loaded training data.</span></span> <span data-ttu-id="01cee-295">Isso retornará um modelo que será usado nas previsões.</span><span class="sxs-lookup"><span data-stu-id="01cee-295">This returns a model to use for predictions.</span></span> <span data-ttu-id="01cee-296">`trainingPipeline.Fit()` treina o pipeline e retorna um `Transformer` com base no `DataView` passado.</span><span class="sxs-lookup"><span data-stu-id="01cee-296">`trainingPipeline.Fit()` trains the pipeline and returns a `Transformer` based on the `DataView` passed in.</span></span> <span data-ttu-id="01cee-297">O experimento não será executado até que isso ocorra.</span><span class="sxs-lookup"><span data-stu-id="01cee-297">The experiment is not executed until this happens.</span></span>

<span data-ttu-id="01cee-298">Adicione o seguinte código ao método `BuildAndTrainModel`:</span><span class="sxs-lookup"><span data-stu-id="01cee-298">Add the following code to the `BuildAndTrainModel` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

<span data-ttu-id="01cee-299">Enquanto o `model` é um `transformer` que opera em muitas linhas de dados, um cenário de produção muito comum é a necessidade de previsões em exemplos individuais.</span><span class="sxs-lookup"><span data-stu-id="01cee-299">While the `model` is a `transformer` that operates on many rows of data, a very common production scenario is a need for predictions on individual examples.</span></span> <span data-ttu-id="01cee-300">O <xref:Microsoft.ML.PredictionEngine%602> é um wrapper que é retornado do método `CreatePredictionEngine`.</span><span class="sxs-lookup"><span data-stu-id="01cee-300">The <xref:Microsoft.ML.PredictionEngine%602> is a wrapper that is returned from the `CreatePredictionEngine` method.</span></span> <span data-ttu-id="01cee-301">Adicionaremos o seguinte código para criar `PredictionEngine` como a próxima linha no método `BuildAndTrainModel`:</span><span class="sxs-lookup"><span data-stu-id="01cee-301">Let's add the following code to create the `PredictionEngine` as the next line in the `BuildAndTrainModel` Method:</span></span>

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]

<span data-ttu-id="01cee-302">Adicione um problema do GitHub para testar a previsão do modelo treinado no método `Predict` ao criar uma instância de `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="01cee-302">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[CreateTestIssue1](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

<span data-ttu-id="01cee-303">Você pode usá-lo para prever o rótulo `Area` de uma única instância dos dados do problema.</span><span class="sxs-lookup"><span data-stu-id="01cee-303">You can use that to predict the `Area` label of a single instance of the issue data.</span></span> <span data-ttu-id="01cee-304">Para obter uma previsão, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> nos dados.</span><span class="sxs-lookup"><span data-stu-id="01cee-304">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="01cee-305">Observe que os dados de entrada são uma cadeia de caracteres e o modelo inclui a personalização.</span><span class="sxs-lookup"><span data-stu-id="01cee-305">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="01cee-306">Seu pipeline está em sincronia durante o treinamento e a previsão.</span><span class="sxs-lookup"><span data-stu-id="01cee-306">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="01cee-307">Você não precisou escrever código de pré-processamento/personalização especificamente para previsões, e a mesma API cuida das previsões de lote e de uso único.</span><span class="sxs-lookup"><span data-stu-id="01cee-307">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="model-operationalization-prediction"></a><span data-ttu-id="01cee-308">Operacionalização do modelo: previsão</span><span class="sxs-lookup"><span data-stu-id="01cee-308">Model operationalization: prediction</span></span>

<span data-ttu-id="01cee-309">Exiba `GitHubIssue` e a previsão de rótulo `Area` correspondente para compartilhar os resultados e agir de acordo com eles.</span><span class="sxs-lookup"><span data-stu-id="01cee-309">Display `GitHubIssue` and corresponding `Area` label prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="01cee-310">Isso é chamado de operacionalização, usar os dados retornados como parte das políticas operacionais.</span><span class="sxs-lookup"><span data-stu-id="01cee-310">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="01cee-311">Crie uma exibição para os resultados usando o seguinte código <xref:System.Console.WriteLine?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="01cee-311">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="01cee-312">Salve e retorne o modelo treinado para usar na avaliação</span><span class="sxs-lookup"><span data-stu-id="01cee-312">Save and return the model trained to use for evaluation</span></span>

<span data-ttu-id="01cee-313">Neste ponto, você tem um modelo de tipo <xref:Microsoft.ML.Data.TransformerChain%601> que pode ser integrado em qualquer um dos seus aplicativos .NET existentes ou novos.</span><span class="sxs-lookup"><span data-stu-id="01cee-313">At this point, you have a model of type <xref:Microsoft.ML.Data.TransformerChain%601> that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="01cee-314">Para salvar seu modelo treinado como um arquivo .zip, adicione o seguinte código para chamar o método `SaveModelAsFile` como a linha seguinte em `BuildAndTrainModel`:</span><span class="sxs-lookup"><span data-stu-id="01cee-314">To save your trained model to a .zip file, add the following code to call the `SaveModelAsFile` method as the next line in `BuildAndTrainModel`:</span></span>

[!code-csharp[CallSaveModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallSaveModel)]

<span data-ttu-id="01cee-315">Retorne o modelo no final do método `BuildAndTrainModel`.</span><span class="sxs-lookup"><span data-stu-id="01cee-315">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="save-the-model-as-azip-file"></a><span data-ttu-id="01cee-316">Salvar o modelo como um arquivo .zip</span><span class="sxs-lookup"><span data-stu-id="01cee-316">Save the model as a.zip file</span></span>

<span data-ttu-id="01cee-317">Crie o método `SaveModelAsFile`, logo após o método `BuildAndTrainModel`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="01cee-317">Create the `SaveModelAsFile` method, just after the `BuildAndTrainModel` method, using the following code:</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="01cee-318">O método `SaveModelAsFile` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="01cee-318">The `SaveModelAsFile` method executes the following tasks:</span></span>

* <span data-ttu-id="01cee-319">Salva o modelo como um arquivo .zip.</span><span class="sxs-lookup"><span data-stu-id="01cee-319">Saves the model as a .zip file.</span></span>

<span data-ttu-id="01cee-320">Em seguida, crie um método para salvar o modelo para que ele possa ser reutilizado e consumido em outros aplicativos.</span><span class="sxs-lookup"><span data-stu-id="01cee-320">Next, create a method to save the model so that it can be reused and consumed in other applications.</span></span> <span data-ttu-id="01cee-321">O `ITransformer` tem um método <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> que usa o campo global `_modelPath` e um <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="01cee-321">The `ITransformer` has a <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> method that takes in the `_modelPath` global field, and a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="01cee-322">Para salvá-lo como um arquivo zip, você criará o `FileStream` imediatamente antes de chamar o método `SaveTo`.</span><span class="sxs-lookup"><span data-stu-id="01cee-322">To save this as a zip file, you'll create the `FileStream` immediately before calling the `SaveTo` method.</span></span> <span data-ttu-id="01cee-323">Adicione o seguinte código ao método `SaveModelAsFile` como a linha seguinte:</span><span class="sxs-lookup"><span data-stu-id="01cee-323">Add the following code to the `SaveModelAsFile` method as the next line:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SaveModel)]

<span data-ttu-id="01cee-324">Você também pode exibir onde o arquivo foi gravado ao gravar uma mensagem de console com o `_modelPath`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="01cee-324">You could also display where the file was written by writing a console message with the `_modelPath`, using the following code:</span></span>

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="evaluate-the-model"></a><span data-ttu-id="01cee-325">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="01cee-325">Evaluate the model</span></span>

<span data-ttu-id="01cee-326">Agora que você criou e treinou o modelo, precisa avaliá-lo com um conjunto de dados diferente para garantia de qualidade e validação.</span><span class="sxs-lookup"><span data-stu-id="01cee-326">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="01cee-327">No método `Evaluate`, o modelo criado em `BuildAndTrainModel` é passado para ser avaliado.</span><span class="sxs-lookup"><span data-stu-id="01cee-327">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="01cee-328">Crie o método `Evaluate` , logo após `BuildAndTrainModel`, como no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="01cee-328">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate()
{

}
```

<span data-ttu-id="01cee-329">O método `Evaluate` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="01cee-329">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="01cee-330">Carrega o conjunto de dados de teste.</span><span class="sxs-lookup"><span data-stu-id="01cee-330">Loads the test dataset.</span></span>
* <span data-ttu-id="01cee-331">Cria o avaliador multiclasse.</span><span class="sxs-lookup"><span data-stu-id="01cee-331">Creates the multiclass evaluator.</span></span>
* <span data-ttu-id="01cee-332">Avalia o modelo e cria métricas.</span><span class="sxs-lookup"><span data-stu-id="01cee-332">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="01cee-333">Exibe as métricas.</span><span class="sxs-lookup"><span data-stu-id="01cee-333">Displays the metrics.</span></span>

<span data-ttu-id="01cee-334">Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `BuildAndTrainModel`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="01cee-334">Add a call to the new method from the `Main` method, right under the `BuildAndTrainModel` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

<span data-ttu-id="01cee-335">Assim como você fez anteriormente com o conjunto de dados de treinamento, você pode combinar a inicialização, o mapeamento e testar o carregamento do conjunto de dados em uma linha de código.</span><span class="sxs-lookup"><span data-stu-id="01cee-335">As you did previously with the training dataset, you can combine the initialization, mapping, and test dataset loading into one line of code.</span></span> <span data-ttu-id="01cee-336">Você pode avaliar o modelo usando esse conjunto de dados como uma verificação de qualidade.</span><span class="sxs-lookup"><span data-stu-id="01cee-336">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="01cee-337">Adicione o seguinte código ao método `Evaluate`:</span><span class="sxs-lookup"><span data-stu-id="01cee-337">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

<span data-ttu-id="01cee-338">O método `MulticlassClassificationContext.Evaluate` é o wrapper para o método <xref:Microsoft.ML.MulticlassClassificationContext.Evaluate%2A>, que calcula as métricas de qualidade para o modelo usando o conjunto de dados especificado.</span><span class="sxs-lookup"><span data-stu-id="01cee-338">The `MulticlassClassificationContext.Evaluate` is a wrapper for the <xref:Microsoft.ML.MulticlassClassificationContext.Evaluate%2A> method that computes the quality metrics for the model using the specified dataset.</span></span> <span data-ttu-id="01cee-339">Ele retorna um objeto <xref:Microsoft.ML.Data.MultiClassClassifierMetrics> que contém as métricas gerais calculadas pelos avaliadores de classificação multiclasse.</span><span class="sxs-lookup"><span data-stu-id="01cee-339">It returns a <xref:Microsoft.ML.Data.MultiClassClassifierMetrics> object that contains the overall metrics computed by multiclass classification evaluators.</span></span>
<span data-ttu-id="01cee-340">Para exibi-los a fim de determinar a qualidade do modelo, é preciso primeiro obter as métricas.</span><span class="sxs-lookup"><span data-stu-id="01cee-340">To display these to determine the quality of the model, you need to get the metrics first.</span></span>
<span data-ttu-id="01cee-341">Observe o uso do método `Transform` da variável global `_trainedModel` de aprendizado de máquina (um transformador) para inserir os recursos e retornar previsões.</span><span class="sxs-lookup"><span data-stu-id="01cee-341">Notice the use of the `Transform` method of the machine learning `_trainedModel` global variable (a transformer) to input the features and return predictions.</span></span> <span data-ttu-id="01cee-342">Adicione o seguinte código ao método `Evaluate` como a linha seguinte:</span><span class="sxs-lookup"><span data-stu-id="01cee-342">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

<span data-ttu-id="01cee-343">As métricas a seguir são avaliadas para classificação multiclasse:</span><span class="sxs-lookup"><span data-stu-id="01cee-343">The following metrics are evaluated for multiclass classification:</span></span>

* <span data-ttu-id="01cee-344">Microprecisão – todo par de classe/exemplo contribui igualmente para a métrica de precisão.</span><span class="sxs-lookup"><span data-stu-id="01cee-344">Micro Accuracy - Every sample-class pair contributes equally to the accuracy metric.</span></span>  <span data-ttu-id="01cee-345">Convém que a Microprecisão seja tão próxima de 1 quanto possível.</span><span class="sxs-lookup"><span data-stu-id="01cee-345">You want Micro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="01cee-346">Macroprecisão – toda classe contribui igualmente para a métrica de precisão.</span><span class="sxs-lookup"><span data-stu-id="01cee-346">Macro Accuracy - Every class contributes equally to the accuracy metric.</span></span> <span data-ttu-id="01cee-347">Classes minoritárias recebem o mesmo peso que as classes maiores.</span><span class="sxs-lookup"><span data-stu-id="01cee-347">Minority classes are given equal weight as the larger classes.</span></span> <span data-ttu-id="01cee-348">Convém que a Macroprecisão seja tão próxima de 1 quanto possível.</span><span class="sxs-lookup"><span data-stu-id="01cee-348">You want Macro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="01cee-349">Perda de log – consulte [Perda de log](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="01cee-349">Log-loss - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="01cee-350">Convém que a Perda de log seja tão próxima de zero quanto possível.</span><span class="sxs-lookup"><span data-stu-id="01cee-350">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="01cee-351">Redução de perda de log – varia de [-inf, 100], em que 100 é composto pelas previsões perfeitas e 0 indica previsões de média.</span><span class="sxs-lookup"><span data-stu-id="01cee-351">Log-loss reduction - Ranges from [-inf, 100], where 100 is perfect predictions and 0 indicates mean predictions.</span></span> <span data-ttu-id="01cee-352">Convém que a redução de perda de log seja tão próxima de zero quanto possível.</span><span class="sxs-lookup"><span data-stu-id="01cee-352">You want Log-loss reduction to be as close to zero as possible.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="01cee-353">Exibir as métricas para validação de modelo</span><span class="sxs-lookup"><span data-stu-id="01cee-353">Displaying the metrics for model validation</span></span>

<span data-ttu-id="01cee-354">Use o código a seguir para exibir as métricas, compartilhar os resultados e, em seguida, agir com relação a eles:</span><span class="sxs-lookup"><span data-stu-id="01cee-354">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

## <a name="predict-the-test-data-outcome-with-the-saved-model"></a><span data-ttu-id="01cee-355">Prever o resultado dos dados de teste com o modelo salvo</span><span class="sxs-lookup"><span data-stu-id="01cee-355">Predict the test data outcome with the saved model</span></span>

<span data-ttu-id="01cee-356">Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `Evaluate`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="01cee-356">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredictIssue](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

<span data-ttu-id="01cee-357">Crie o método `PredictIssue`, logo após o método `Evaluate`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="01cee-357">Create the `PredictIssue` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void PredictIssue()
{

}
```

<span data-ttu-id="01cee-358">O método `PredictIssue` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="01cee-358">The `PredictIssue` method executes the following tasks:</span></span>

* <span data-ttu-id="01cee-359">Cria um único problema dos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="01cee-359">Creates a single issue of test data.</span></span>
* <span data-ttu-id="01cee-360">Prevê a área com base em dados de teste.</span><span class="sxs-lookup"><span data-stu-id="01cee-360">Predicts Area based on test data.</span></span>
* <span data-ttu-id="01cee-361">Combina dados de teste e previsões para relatórios.</span><span class="sxs-lookup"><span data-stu-id="01cee-361">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="01cee-362">Exibe os resultados previstos.</span><span class="sxs-lookup"><span data-stu-id="01cee-362">Displays the predicted results.</span></span>

<span data-ttu-id="01cee-363">Primeiro, carregue o modelo que você salvou anteriormente com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="01cee-363">First, load the model that you saved previously with the following code:</span></span>

[!code-csharp[LoadModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadModel)]

<span data-ttu-id="01cee-364">Adicione um problema do GitHub para testar a previsão do modelo treinado no método `Predict` ao criar uma instância de `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="01cee-364">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[AddTestIssue](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]
  
<span data-ttu-id="01cee-365">Agora que tem um modelo, você pode usá-lo para prever o rótulo do GitHub da área de uma única instância dos dados do problema do GitHub.</span><span class="sxs-lookup"><span data-stu-id="01cee-365">Now that you have a model, you can use that to predict the Area GitHub label of a single instance of the GitHub issue data.</span></span> <span data-ttu-id="01cee-366">Para obter uma previsão, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> nos dados.</span><span class="sxs-lookup"><span data-stu-id="01cee-366">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="01cee-367">Observe que os dados de entrada são uma cadeia de caracteres e o modelo inclui a personalização.</span><span class="sxs-lookup"><span data-stu-id="01cee-367">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="01cee-368">Seu pipeline está em sincronia durante o treinamento e a previsão.</span><span class="sxs-lookup"><span data-stu-id="01cee-368">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="01cee-369">Você não precisou escrever código de pré-processamento/personalização especificamente para previsões, e a mesma API cuida das previsões de lote e de uso único.</span><span class="sxs-lookup"><span data-stu-id="01cee-369">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span> <span data-ttu-id="01cee-370">Adicione o código a seguir ao método `PredictIssue` para as previsões:</span><span class="sxs-lookup"><span data-stu-id="01cee-370">Add the following code to the `PredictIssue` method for the predictions:</span></span>

[!code-csharp[PredictIssue](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]

### <a name="model-operationalization-prediction"></a><span data-ttu-id="01cee-371">Operacionalização do modelo: previsão</span><span class="sxs-lookup"><span data-stu-id="01cee-371">Model operationalization: prediction</span></span>

<span data-ttu-id="01cee-372">Exiba `Area` para categorizar o problema e agir adequadamente para solucioná-lo.</span><span class="sxs-lookup"><span data-stu-id="01cee-372">Display `Area` in order to categorize the issue and act on it accordingly.</span></span> <span data-ttu-id="01cee-373">Isso é chamado de operacionalização, usar os dados retornados como parte das políticas operacionais.</span><span class="sxs-lookup"><span data-stu-id="01cee-373">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="01cee-374">Crie uma exibição para os resultados usando o seguinte código <xref:System.Console.WriteLine?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="01cee-374">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayResults](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a><span data-ttu-id="01cee-375">Resultados</span><span class="sxs-lookup"><span data-stu-id="01cee-375">Results</span></span>

<span data-ttu-id="01cee-376">Seus resultados devem ser semelhantes aos seguintes.</span><span class="sxs-lookup"><span data-stu-id="01cee-376">Your results should be similar to the following.</span></span> <span data-ttu-id="01cee-377">Conforme o pipeline processa, exibe mensagens.</span><span class="sxs-lookup"><span data-stu-id="01cee-377">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="01cee-378">Você pode ver avisos ou mensagens de processamento.</span><span class="sxs-lookup"><span data-stu-id="01cee-378">You may see warnings, or processing messages.</span></span> <span data-ttu-id="01cee-379">Eles foram removidos dos seguintes resultados para maior clareza.</span><span class="sxs-lookup"><span data-stu-id="01cee-379">These have been removed from the following results for clarity.</span></span>

```console
=============== Single Prediction just-trained-model - Result: area-System.Net ===============
The model is saved to C:\Users\johalex\dotnet-samples\samples\machine-learning\tutorials\GitHubIssueClassification\bin\Debug\netcoreapp2.0\..\..\..\Models\model.zip
*************************************************************************************************************
*       Metrics for Multi-class Classification model - Test Data
*------------------------------------------------------------------------------------------------------------
*       MicroAccuracy:    0.74
*       MacroAccuracy:    0.687
*       LogLoss:          .932
*       LogLossReduction: 63.852
*************************************************************************************************************
=============== Single Prediction - Result: area-System.Data ===============
```

<span data-ttu-id="01cee-380">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="01cee-380">Congratulations!</span></span> <span data-ttu-id="01cee-381">Agora você criou com sucesso um modelo de machine learning para classificar e prever um rótulo de Área para um problema do GitHub.</span><span class="sxs-lookup"><span data-stu-id="01cee-381">You've now successfully built a machine learning model for classifying and predicting an Area label for a GitHub issue.</span></span> <span data-ttu-id="01cee-382">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification).</span><span class="sxs-lookup"><span data-stu-id="01cee-382">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="01cee-383">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="01cee-383">Next steps</span></span>

<span data-ttu-id="01cee-384">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="01cee-384">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="01cee-385">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="01cee-385">Understand the problem</span></span>
> * <span data-ttu-id="01cee-386">Selecionar a tarefa de aprendizado de máquina apropriada</span><span class="sxs-lookup"><span data-stu-id="01cee-386">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="01cee-387">Preparar seus dados</span><span class="sxs-lookup"><span data-stu-id="01cee-387">Prepare your data</span></span>
> * <span data-ttu-id="01cee-388">Criar o pipeline de aprendizado</span><span class="sxs-lookup"><span data-stu-id="01cee-388">Create the learning pipeline</span></span>
> * <span data-ttu-id="01cee-389">Carregar um classificador</span><span class="sxs-lookup"><span data-stu-id="01cee-389">Load a classifier</span></span>
> * <span data-ttu-id="01cee-390">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="01cee-390">Train the model</span></span>
> * <span data-ttu-id="01cee-391">Avaliar o modelo com um conjunto de dados diferente</span><span class="sxs-lookup"><span data-stu-id="01cee-391">Evaluate the model with a different dataset</span></span>
> * <span data-ttu-id="01cee-392">Prever os resultados dos dados de teste com o modelo</span><span class="sxs-lookup"><span data-stu-id="01cee-392">Predict the test data outcomes with the model</span></span>

<span data-ttu-id="01cee-393">Avançar para o próximo tutorial para saber mais</span><span class="sxs-lookup"><span data-stu-id="01cee-393">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="01cee-394">Previsão do valor da corrida do táxi</span><span class="sxs-lookup"><span data-stu-id="01cee-394">Taxi Fare Predictor</span></span>](taxi-fare.md)
