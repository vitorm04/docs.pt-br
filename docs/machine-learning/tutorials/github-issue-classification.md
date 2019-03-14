---
title: Usar o ML.NET em um cenário de classificação multiclasse de problema do GitHub
description: Descubra como usar o ML.NET em um cenário de classificação multiclasse para classificar os problemas do GitHub a fim de atribuí-los a uma determinada área.
ms.date: 02/20/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 4f6a95fbd470c688c977b406d1813d6a453e8a79
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471466"
---
# <a name="tutorial-use-mlnet-in-a-multiclass-classification-scenario-to-classify-github-issues"></a><span data-ttu-id="78939-103">Tutorial: Usar o ML.NET em um cenário de classificação multiclasse para classificar os problemas do GitHub</span><span class="sxs-lookup"><span data-stu-id="78939-103">Tutorial: Use ML.NET in a multiclass classification scenario to classify GitHub issues</span></span>

<span data-ttu-id="78939-104">Este tutorial de exemplo ilustra o uso do ML.NET para criar um classificador de problema do GitHub por meio de um aplicativo de console do .NET Core usando C# no Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="78939-104">This sample tutorial illustrates using ML.NET to create a GitHub issue classifier via a .NET Core console application using C# in Visual Studio 2017.</span></span>

<span data-ttu-id="78939-105">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="78939-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="78939-106">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="78939-106">Understand the problem</span></span>
> * <span data-ttu-id="78939-107">Selecionar o algoritmo de aprendizado de máquina apropriado</span><span class="sxs-lookup"><span data-stu-id="78939-107">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="78939-108">Preparar seus dados</span><span class="sxs-lookup"><span data-stu-id="78939-108">Prepare your data</span></span>
> * <span data-ttu-id="78939-109">Transformar os dados</span><span class="sxs-lookup"><span data-stu-id="78939-109">Transform the data</span></span>
> * <span data-ttu-id="78939-110">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="78939-110">Train the model</span></span>
> * <span data-ttu-id="78939-111">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="78939-111">Evaluate the model</span></span>
> * <span data-ttu-id="78939-112">Prever com o modelo treinado</span><span class="sxs-lookup"><span data-stu-id="78939-112">Predict with the trained model</span></span>
> * <span data-ttu-id="78939-113">Implantar e prever com um modelo carregado</span><span class="sxs-lookup"><span data-stu-id="78939-113">Deploy and Predict with a loaded model</span></span>

> [!NOTE]
> <span data-ttu-id="78939-114">Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="78939-114">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="78939-115">Para obter mais informações, visite [a introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="78939-115">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="78939-116">Este tutorial e uma amostra relacionada estão usando o **ML.NET versão 0.10** no momento.</span><span class="sxs-lookup"><span data-stu-id="78939-116">This tutorial and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="78939-117">Saiba mais nas notas de versão no [repositório do github dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="78939-117">For more information, see the release notes at the [dotnet/machinelearning github repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

## <a name="github-issue-sample-overview"></a><span data-ttu-id="78939-118">Visão geral de exemplo de problema do GitHub</span><span class="sxs-lookup"><span data-stu-id="78939-118">GitHub issue sample overview</span></span>

<span data-ttu-id="78939-119">A amostra é um aplicativo de console que usa o ML.NET para treinar um modelo que classifica e prevê o rótulo da área para um problema do GitHub.</span><span class="sxs-lookup"><span data-stu-id="78939-119">The sample is a console app that uses ML.NET to train a model that classifies and predicts the Area label for a GitHub issue.</span></span> <span data-ttu-id="78939-120">Ele também avalia o modelo com um segundo conjunto de dados para análise de qualidade.</span><span class="sxs-lookup"><span data-stu-id="78939-120">It also evaluates the model with a second dataset for quality analysis.</span></span> <span data-ttu-id="78939-121">Os conjuntos de dados do problema são do repositório do GitHub do dotnet/corefx.</span><span class="sxs-lookup"><span data-stu-id="78939-121">The issue datasets are from the dotnet/corefx GitHub repo.</span></span>

<span data-ttu-id="78939-122">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification).</span><span class="sxs-lookup"><span data-stu-id="78939-122">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="78939-123">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="78939-123">Prerequisites</span></span>

* <span data-ttu-id="78939-124">[Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="78939-124">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="78939-125">O [arquivo de problemas do Github separados por tabulação (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span><span class="sxs-lookup"><span data-stu-id="78939-125">The [Github issues tab separated file (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span></span>
* <span data-ttu-id="78939-126">O [arquivo de testes de problemas do Github separados por tabulação (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span><span class="sxs-lookup"><span data-stu-id="78939-126">The [Github issues test tab separated file (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="78939-127">Fluxo de trabalho de aprendizado de máquina</span><span class="sxs-lookup"><span data-stu-id="78939-127">Machine learning workflow</span></span>

<span data-ttu-id="78939-128">Este tutorial segue um fluxo de trabalho de aprendizado de máquina que permite que o processo se mova de maneira ordenada.</span><span class="sxs-lookup"><span data-stu-id="78939-128">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="78939-129">As fases do fluxo de trabalho são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="78939-129">The workflow phases are as follows:</span></span>

1. <span data-ttu-id="78939-130">**Compreender o problema**</span><span class="sxs-lookup"><span data-stu-id="78939-130">**Understand the problem**</span></span>
2. <span data-ttu-id="78939-131">**Preparar seus dados**</span><span class="sxs-lookup"><span data-stu-id="78939-131">**Prepare your data**</span></span>
   * <span data-ttu-id="78939-132">**Carregar os dados**</span><span class="sxs-lookup"><span data-stu-id="78939-132">**Load the data**</span></span>
   * <span data-ttu-id="78939-133">**Extrair recursos (Transformar seus dados)**</span><span class="sxs-lookup"><span data-stu-id="78939-133">**Extract features (Transform your data)**</span></span>
3. <span data-ttu-id="78939-134">**Compilar e treinar**</span><span class="sxs-lookup"><span data-stu-id="78939-134">**Build and train**</span></span> 
   * <span data-ttu-id="78939-135">**Treinar o modelo**</span><span class="sxs-lookup"><span data-stu-id="78939-135">**Train the model**</span></span>
   * <span data-ttu-id="78939-136">**Avaliar o modelo**</span><span class="sxs-lookup"><span data-stu-id="78939-136">**Evaluate the model**</span></span>
4. <span data-ttu-id="78939-137">**Implantar Modelo**</span><span class="sxs-lookup"><span data-stu-id="78939-137">**Deploy Model**</span></span>
   * <span data-ttu-id="78939-138">**Usar o modelo para prever**</span><span class="sxs-lookup"><span data-stu-id="78939-138">**Use the Model to predict**</span></span>

### <a name="understand-the-problem"></a><span data-ttu-id="78939-139">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="78939-139">Understand the problem</span></span>

<span data-ttu-id="78939-140">Você primeiro precisa compreender o problema, para que possa dividi-lo em partes que possam oferecer suporte à criação e ao treinamento do modelo.</span><span class="sxs-lookup"><span data-stu-id="78939-140">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="78939-141">Dividir o problema permite prever e avaliar os resultados.</span><span class="sxs-lookup"><span data-stu-id="78939-141">Breaking  down the problem allows you to predict and evaluate the results.</span></span>

<span data-ttu-id="78939-142">O problema neste tutorial é entender a qual área os problemas do GitHub em entrada pertencem, para rotulá-los corretamente para priorização e agendamento.</span><span class="sxs-lookup"><span data-stu-id="78939-142">The problem for this tutorial is to understand what area incoming GitHub issues belong to in order to label them correctly for prioritization and scheduling.</span></span>

<span data-ttu-id="78939-143">Você pode dividir o problema nas seguintes partes:</span><span class="sxs-lookup"><span data-stu-id="78939-143">You can break down the problem to the following parts:</span></span>

* <span data-ttu-id="78939-144">o texto de título do problema</span><span class="sxs-lookup"><span data-stu-id="78939-144">the issue title text</span></span>
* <span data-ttu-id="78939-145">o texto da descrição do problema</span><span class="sxs-lookup"><span data-stu-id="78939-145">the issue description text</span></span>
* <span data-ttu-id="78939-146">um valor de área para os dados de treinamento de modelo</span><span class="sxs-lookup"><span data-stu-id="78939-146">an area value for the model training data</span></span>
* <span data-ttu-id="78939-147">um valor de área prevista que você pode avaliar e, em seguida, usar operacionalmente</span><span class="sxs-lookup"><span data-stu-id="78939-147">a predicted area value that you can evaluate and then use operationally</span></span>

<span data-ttu-id="78939-148">Em seguida, você precisa **determinar** a área, o que ajuda na seleção da tarefa de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="78939-148">You then need to **determine** the area, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-algorithm"></a><span data-ttu-id="78939-149">Selecionar o algoritmo de aprendizado de máquina apropriado</span><span class="sxs-lookup"><span data-stu-id="78939-149">Select the appropriate machine learning algorithm</span></span>

<span data-ttu-id="78939-150">Com este problema, você está a par dos seguintes fatos:</span><span class="sxs-lookup"><span data-stu-id="78939-150">With this problem, you know the following facts:</span></span>

<span data-ttu-id="78939-151">Dados de treinamento:</span><span class="sxs-lookup"><span data-stu-id="78939-151">Training data:</span></span>

<span data-ttu-id="78939-152">Os problemas do GitHub podem ser rotulados em várias áreas (**Área**) como nos exemplos a seguir:</span><span class="sxs-lookup"><span data-stu-id="78939-152">GitHub issues can be labeled in several areas (**Area**) as in the following examples:</span></span>

* <span data-ttu-id="78939-153">area-System.Numerics</span><span class="sxs-lookup"><span data-stu-id="78939-153">area-System.Numerics</span></span>
* <span data-ttu-id="78939-154">area-System.Xml</span><span class="sxs-lookup"><span data-stu-id="78939-154">area-System.Xml</span></span>
* <span data-ttu-id="78939-155">area-Infrastructure</span><span class="sxs-lookup"><span data-stu-id="78939-155">area-Infrastructure</span></span>
* <span data-ttu-id="78939-156">area-System.Linq</span><span class="sxs-lookup"><span data-stu-id="78939-156">area-System.Linq</span></span>
* <span data-ttu-id="78939-157">area-System.IO</span><span class="sxs-lookup"><span data-stu-id="78939-157">area-System.IO</span></span>

<span data-ttu-id="78939-158">Preveja a **Área** de um novo problema do GitHub como nos exemplos a seguir:</span><span class="sxs-lookup"><span data-stu-id="78939-158">Predict the **Area** of a new GitHub Issue such as in the following examples:</span></span>

* <span data-ttu-id="78939-159">Contract.Assert versus Debug.Assert</span><span class="sxs-lookup"><span data-stu-id="78939-159">Contract.Assert vs Debug.Assert</span></span>
* <span data-ttu-id="78939-160">Tornar os campos somente leitura em System.Xml</span><span class="sxs-lookup"><span data-stu-id="78939-160">Make fields readonly in System.Xml</span></span>

<span data-ttu-id="78939-161">O algoritmo de aprendizado de máquina de classificação é mais adequado para esse cenário.</span><span class="sxs-lookup"><span data-stu-id="78939-161">The classification machine learning algorithm is best suited for this scenario.</span></span>

### <a name="about-the-classification-learning-algorithm"></a><span data-ttu-id="78939-162">Sobre o algoritmo de aprendizado de classificação</span><span class="sxs-lookup"><span data-stu-id="78939-162">About the classification learning algorithm</span></span>

<span data-ttu-id="78939-163">A classificação é um algoritmo de aprendizado de máquina que usa os dados para **determinar** a categoria, o tipo ou a classe de um item ou de uma linha de dados.</span><span class="sxs-lookup"><span data-stu-id="78939-163">Classification is a machine learning algorithm that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="78939-164">Por exemplo, você pode usar a classificação para:</span><span class="sxs-lookup"><span data-stu-id="78939-164">For example, you can use classification to:</span></span>

* <span data-ttu-id="78939-165">Identificar o sentimento como positivo ou negativo.</span><span class="sxs-lookup"><span data-stu-id="78939-165">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="78939-166">Classificar email como spam, lixo eletrônico ou bom.</span><span class="sxs-lookup"><span data-stu-id="78939-166">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="78939-167">Determinar se a amostra de laboratório de um paciente é cancerígena.</span><span class="sxs-lookup"><span data-stu-id="78939-167">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="78939-168">Categorizar os clientes pela sua propensão a responder a uma campanha de vendas.</span><span class="sxs-lookup"><span data-stu-id="78939-168">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="78939-169">Os casos de uso do algoritmo de aprendizado de classificação são geralmente um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="78939-169">Classification learning algorithm use cases are frequently one of the following types:</span></span>

* <span data-ttu-id="78939-170">Binário: A ou B.</span><span class="sxs-lookup"><span data-stu-id="78939-170">Binary: either A or B.</span></span>
* <span data-ttu-id="78939-171">Multiclasse: várias categorias que podem ser previstas usando um único modelo.</span><span class="sxs-lookup"><span data-stu-id="78939-171">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="78939-172">Para esse tipo de problema, use um algoritmo de aprendizado de classificação Multiclasse, pois a previsão de categoria do problema pode ser uma das várias categorias (multiclasse), em vez de apenas duas (binária).</span><span class="sxs-lookup"><span data-stu-id="78939-172">For this type of problem, use a Multiclass classification learning algorithm, since your issue category prediction can be one of multiple categories (multiclass) rather than just two (binary).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="78939-173">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="78939-173">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="78939-174">Criar um projeto</span><span class="sxs-lookup"><span data-stu-id="78939-174">Create a project</span></span>

1. <span data-ttu-id="78939-175">Abra o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="78939-175">Open Visual Studio 2017.</span></span> <span data-ttu-id="78939-176">Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="78939-176">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="78939-177">Na caixa de diálogo **Novo Projeto**, selecione o nó **Visual C#** seguido pelo nó **.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="78939-177">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="78939-178">Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="78939-178">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="78939-179">Na caixa de texto **Nome**, digite "GitHubIssueClassification" e selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="78939-179">In the **Name** text box, type "GitHubIssueClassification" and then select the **OK** button.</span></span>

2. <span data-ttu-id="78939-180">Crie um diretório chamado *Data* no seu projeto para salvar seus arquivos do conjunto de dados:</span><span class="sxs-lookup"><span data-stu-id="78939-180">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="78939-181">No **Gerenciador de Soluções**, clique com o botão direito do mouse no seu projeto e selecione **Adicionar** > **Nova Pasta**.</span><span class="sxs-lookup"><span data-stu-id="78939-181">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="78939-182">Digite "Data" e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="78939-182">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="78939-183">Crie um diretório chamado *Modelos* em seu projeto para salvar seu modelo:</span><span class="sxs-lookup"><span data-stu-id="78939-183">Create a directory named *Models* in your project to save your model:</span></span>

    <span data-ttu-id="78939-184">No **Gerenciador de Soluções**, clique com o botão direito do mouse no seu projeto e selecione **Adicionar** > **Nova Pasta**.</span><span class="sxs-lookup"><span data-stu-id="78939-184">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="78939-185">Digite "Modelos" e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="78939-185">Type "Models" and hit Enter.</span></span>

4. <span data-ttu-id="78939-186">Instalar o **Pacote NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="78939-186">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="78939-187">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="78939-187">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="78939-188">Escolha "nuget.org" como a Origem do pacote, selecione a guia Procurar, pesquise por **Microsoft.ML**, selecione o pacote na lista e escolha o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="78939-188">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="78939-189">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="78939-189">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="78939-190">Preparar seus dados</span><span class="sxs-lookup"><span data-stu-id="78939-190">Prepare your data</span></span>

1. <span data-ttu-id="78939-191">Baixe os conjuntos de dados [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) e [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) e salve-os na pasta *Dados* criada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="78939-191">Download the [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) and the [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="78939-192">O primeiro conjunto de dados treina o modelo de aprendizado de máquina e o segundo pode ser usado para avaliar a precisão do seu modelo.</span><span class="sxs-lookup"><span data-stu-id="78939-192">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="78939-193">No Gerenciador de Soluções, clique com o botão direito do mouse em cada um dos arquivos \*.tsv e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="78939-193">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="78939-194">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.</span><span class="sxs-lookup"><span data-stu-id="78939-194">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="78939-195">Criar classes e definir demarcadores</span><span class="sxs-lookup"><span data-stu-id="78939-195">Create classes and define paths</span></span>

<span data-ttu-id="78939-196">Adicione as seguintes instruções `using` adicionais ao início do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="78939-196">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

<span data-ttu-id="78939-197">Crie três campos globais para manter os caminhos para os arquivos baixados recentemente e variáveis globais para `MLContext`, `DataView`, `PredictionEngine` e `TextLoader`:</span><span class="sxs-lookup"><span data-stu-id="78939-197">Create three global fields to hold the paths to the recently downloaded files, and global variables for the `MLContext`,`DataView`, `PredictionEngine`, and `TextLoader`:</span></span>

* <span data-ttu-id="78939-198">`_trainDataPath` tem o demarcador para o conjunto de dados usado para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="78939-198">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="78939-199">`_testDataPath` tem o demarcador para o conjunto de dados usado para avaliar o modelo.</span><span class="sxs-lookup"><span data-stu-id="78939-199">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="78939-200">`_modelPath` tem o demarcador em que o modelo treinado é salvo.</span><span class="sxs-lookup"><span data-stu-id="78939-200">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="78939-201">`_mlContext` é o <xref:Microsoft.ML.MLContext> que fornece o contexto de processamento.</span><span class="sxs-lookup"><span data-stu-id="78939-201">`_mlContext` is the <xref:Microsoft.ML.MLContext> that provides processing context.</span></span>
* <span data-ttu-id="78939-202">`_trainingDataView` é o <xref:Microsoft.Data.DataView.IDataView> usado para processar o conjunto de dados de treinamento.</span><span class="sxs-lookup"><span data-stu-id="78939-202">`_trainingDataView` is the <xref:Microsoft.Data.DataView.IDataView> used to process the training dataset.</span></span>
* <span data-ttu-id="78939-203">`_predEngine` é o <xref:Microsoft.ML.PredictionEngine%602> usado para previsões individuais.</span><span class="sxs-lookup"><span data-stu-id="78939-203">`_predEngine` is the <xref:Microsoft.ML.PredictionEngine%602> used for single predictions.</span></span>
* <span data-ttu-id="78939-204">O `_reader` é o <xref:Microsoft.ML.Data.TextLoader> usado para carregar e transformar os conjuntos de dados.</span><span class="sxs-lookup"><span data-stu-id="78939-204">`_reader` is the <xref:Microsoft.ML.Data.TextLoader> used to load and transform the datasets.</span></span>

<span data-ttu-id="78939-205">Adicione o seguinte código à linha logo acima do método `Main` para especificar estes caminhos e as outras variáveis:</span><span class="sxs-lookup"><span data-stu-id="78939-205">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="78939-206">Crie algumas classes para os dados de entrada e as previsões.</span><span class="sxs-lookup"><span data-stu-id="78939-206">Create some classes for your input data and predictions.</span></span> <span data-ttu-id="78939-207">Adicione uma nova classe ao seu projeto:</span><span class="sxs-lookup"><span data-stu-id="78939-207">Add a new class to your project:</span></span>

1. <span data-ttu-id="78939-208">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="78939-208">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="78939-209">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *GitHubIssueData.cs*.</span><span class="sxs-lookup"><span data-stu-id="78939-209">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *GitHubIssueData.cs*.</span></span> <span data-ttu-id="78939-210">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="78939-210">Then, select the **Add** button.</span></span>

    <span data-ttu-id="78939-211">O arquivo *GitHubIssueData.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="78939-211">The *GitHubIssueData.cs* file opens in the code editor.</span></span> <span data-ttu-id="78939-212">Adicione a seguinte instrução `using` acima de *GitHubIssueData.cs*:</span><span class="sxs-lookup"><span data-stu-id="78939-212">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

<span data-ttu-id="78939-213">Remova a definição de classe existente e adicione o seguinte código, que tem duas classes, `GitHubIssue` e `IssuePrediction`, ao arquivo *GitHubIssueData.cs*:</span><span class="sxs-lookup"><span data-stu-id="78939-213">Remove the existing class definition and add the following code, which has two classes `GitHubIssue` and `IssuePrediction`, to the *GitHubIssueData.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

<span data-ttu-id="78939-214">`GitHubIssue` é a classe de conjunto de dados de entrada e tem os seguintes campos <xref:System.String>:</span><span class="sxs-lookup"><span data-stu-id="78939-214">`GitHubIssue` is the input dataset class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="78939-215">`ID` contém um valor para a ID do problema do GitHub</span><span class="sxs-lookup"><span data-stu-id="78939-215">`ID` contains a value for the GitHub issue ID</span></span>
* <span data-ttu-id="78939-216">`Area` contém um valor para o rótulo `Area`</span><span class="sxs-lookup"><span data-stu-id="78939-216">`Area` contains a value for the `Area` label</span></span>
* <span data-ttu-id="78939-217">`Title` contém o título do problema do GitHub</span><span class="sxs-lookup"><span data-stu-id="78939-217">`Title` contains the GitHub issue title</span></span>
* <span data-ttu-id="78939-218">`Description` contém a descrição do problema do GitHub</span><span class="sxs-lookup"><span data-stu-id="78939-218">`Description` contains the GitHub issue description</span></span>

<span data-ttu-id="78939-219">`IssuePrediction` é a classe usada para previsão depois que o modelo foi treinado.</span><span class="sxs-lookup"><span data-stu-id="78939-219">`IssuePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="78939-220">Tem um único `string` (`Area`) e um atributo `PredictedLabel` `ColumnName`.</span><span class="sxs-lookup"><span data-stu-id="78939-220">It has a single `string` (`Area`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="78939-221">O `Label` é usado para criar e treinar o modelo e também é usado com um segundo conjunto de dados para avaliar o modelo.</span><span class="sxs-lookup"><span data-stu-id="78939-221">The `Label` is used to create and train the model, and it's also used with a second dataset to evaluate the model.</span></span> <span data-ttu-id="78939-222">O `PredictedLabel` é usado durante a previsão e avaliação.</span><span class="sxs-lookup"><span data-stu-id="78939-222">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="78939-223">Para avaliação, uma entrada com dados de treinamento, os valores previstos e o modelo são usados.</span><span class="sxs-lookup"><span data-stu-id="78939-223">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="78939-224">Ao criar um modelo com o ML.NET, comece criando um <xref:Microsoft.ML.MLContext>.</span><span class="sxs-lookup"><span data-stu-id="78939-224">When building a model with ML.NET, you start by creating an <xref:Microsoft.ML.MLContext>.</span></span> <span data-ttu-id="78939-225">`MLContext` é conceitualmente comparável ao uso de `DbContext` no Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="78939-225">`MLContext` is comparable conceptually to using `DbContext` in Entity Framework.</span></span> <span data-ttu-id="78939-226">O ambiente fornece um contexto para seu trabalho de ML que pode ser usado no acompanhamento e registro em log da exceção.</span><span class="sxs-lookup"><span data-stu-id="78939-226">The environment provides a context for your ML job that can be used for exception tracking and logging.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="78939-227">Inicializar variáveis em Main</span><span class="sxs-lookup"><span data-stu-id="78939-227">Initialize variables in Main</span></span>

<span data-ttu-id="78939-228">Inicialize a variável global `_mlContext` com uma nova instância de `MLContext` com uma semente aleatória (`seed: 0`) para obter resultados repetíveis/determinísticos entre vários treinamentos.</span><span class="sxs-lookup"><span data-stu-id="78939-228">Initialize the `_mlContext` global variable  with a new instance of `MLContext` with a random seed (`seed: 0`) for repeatable/deterministic results across multiple trainings.</span></span>  <span data-ttu-id="78939-229">Substitua a linha `Console.WriteLine("Hello World!")` pelo seguinte código no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="78939-229">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a><span data-ttu-id="78939-230">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="78939-230">Load the data</span></span>

<span data-ttu-id="78939-231">Carregaremos os dados usando a variável global `_trainingDataView` <xref:Microsoft.Data.DataView.IDataView> com o parâmetro `_trainDataPath`.</span><span class="sxs-lookup"><span data-stu-id="78939-231">Next, initialize the `_trainingDataView` <xref:Microsoft.Data.DataView.IDataView> global variable and load the data with the `_trainDataPath` parameter.</span></span>

 <span data-ttu-id="78939-232">Como a entrada e a saída de [`Transforms`](../basic-concepts-model-training-in-mldotnet.md#transformer), uma `DataView` é o tipo de pipeline de dados fundamental, comparável a `IEnumerable` para `LINQ`.</span><span class="sxs-lookup"><span data-stu-id="78939-232">As the input and output of [`Transforms`](../basic-concepts-model-training-in-mldotnet.md#transformer), a `DataView` is the fundamental data pipeline type, comparable to `IEnumerable` for `LINQ`.</span></span>

<span data-ttu-id="78939-233">No ML.NET, os dados são semelhantes a um `SQL view`.</span><span class="sxs-lookup"><span data-stu-id="78939-233">In ML.NET, data is similar to a `SQL view`.</span></span> <span data-ttu-id="78939-234">Eles são heterogêneos e avaliados e esquematizados lentamente.</span><span class="sxs-lookup"><span data-stu-id="78939-234">It is lazily evaluated, schematized, and heterogenous.</span></span> <span data-ttu-id="78939-235">O objeto é a primeira parte do pipeline e carrega os dados.</span><span class="sxs-lookup"><span data-stu-id="78939-235">The object is the first part of the pipeline, and loads the data.</span></span> <span data-ttu-id="78939-236">Para este tutorial, ele carrega um conjunto de dados com títulos, descrições e rótulo do GitHub da área correspondente do problema.</span><span class="sxs-lookup"><span data-stu-id="78939-236">For this tutorial, it loads a dataset with issue titles, descriptions, and corresponding area GitHub label.</span></span> <span data-ttu-id="78939-237">O `DataView` é usado para criar o modelo e treiná-lo.</span><span class="sxs-lookup"><span data-stu-id="78939-237">The `DataView` is used to create and train the model.</span></span>

<span data-ttu-id="78939-238">Já que o tipo do modelo de dados `GitHubIssue` criado anteriormente corresponde ao esquema de conjunto de dados, você pode combinar a inicialização, o mapeamento e o carregamento de conjunto de dados em uma única linha de código.</span><span class="sxs-lookup"><span data-stu-id="78939-238">Since your previously created `GitHubIssue` data model type matches the dataset schema, you can combine the initialization, mapping, and dataset loading into one line of code.</span></span>

<span data-ttu-id="78939-239">A primeira parte da linha (`CreateTextLoader<GitHubIssue>(hasHeader: true)`) cria um <xref:Microsoft.ML.Data.TextLoader> por inferência do esquema de conjunto de dados do tipo de modelo de dados `GitHubIssue` e usando o cabeçalho do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="78939-239">The first part of the line (`CreateTextLoader<GitHubIssue>(hasHeader: true)`) creates a <xref:Microsoft.ML.Data.TextLoader> by inferring the dataset schema from the `GitHubIssue` data model type and using the dataset header.</span></span>

<span data-ttu-id="78939-240">Você definiu o esquema de dados anteriormente ao criar a classe `GitHubIssue`.</span><span class="sxs-lookup"><span data-stu-id="78939-240">You defined the data schema previously when you created the `GitHubIssue` class.</span></span> <span data-ttu-id="78939-241">Para o esquema:</span><span class="sxs-lookup"><span data-stu-id="78939-241">For your schema:</span></span>

* <span data-ttu-id="78939-242">a primeira coluna `ID` (ID de problema do GitHub)</span><span class="sxs-lookup"><span data-stu-id="78939-242">the first column `ID` (GitHub Issue ID)</span></span>
* <span data-ttu-id="78939-243">a segunda coluna `Area` (a previsão do treinamento)</span><span class="sxs-lookup"><span data-stu-id="78939-243">the second column `Area` (the prediction for training)</span></span>
* <span data-ttu-id="78939-244">a terceira coluna `Title` (título do problema de GitHub) é o primeiro [recurso](../resources/glossary.md##feature) usado para prever o `Area`</span><span class="sxs-lookup"><span data-stu-id="78939-244">the third column `Title` (GitHub issue title) is the first [feature](../resources/glossary.md##feature)  used for predicting the `Area`</span></span>
* <span data-ttu-id="78939-245">a quarta coluna `Description` é o segundo recurso usado para prever o `Area`</span><span class="sxs-lookup"><span data-stu-id="78939-245">the fourth column  `Description` is the second feature used for predicting the `Area`</span></span>

<span data-ttu-id="78939-246">A segunda parte da linha (`.Read(_trainDataPath)`) usa o método <xref:Microsoft.ML.Data.TextLoader.Read%2A> para carregar o arquivo de texto de treinamento usando o `_trainDataPath` na variável global `IDataView` (`_trainingDataView`).</span><span class="sxs-lookup"><span data-stu-id="78939-246">The second part of the line  (`.Read(_trainDataPath)`) uses <xref:Microsoft.ML.Data.TextLoader.Read%2A> method to load the training text file using `_trainDataPath` into the `IDataView` (`_trainingDataView`) global variable.</span></span>  

<span data-ttu-id="78939-247">Para inicializar e carregar a variável global `_trainingDataView` para utilizá-la para o pipeline, adicione o seguinte código após a inicialização de `mlContext`:</span><span class="sxs-lookup"><span data-stu-id="78939-247">To initialize and load the `_trainingDataView` global variable in order to use it for the pipeline, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]


<span data-ttu-id="78939-248">Adicione o seguinte como a linha seguinte de código no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="78939-248">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallProcessData](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

<span data-ttu-id="78939-249">O método `ProcessData` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="78939-249">The `ProcessData` method executes the following tasks:</span></span>

* <span data-ttu-id="78939-250">Extrai e transforma os dados.</span><span class="sxs-lookup"><span data-stu-id="78939-250">Extracts and transforms the data.</span></span>
* <span data-ttu-id="78939-251">Retorna o pipeline de processamento.</span><span class="sxs-lookup"><span data-stu-id="78939-251">Returns the processing pipeline.</span></span>

<span data-ttu-id="78939-252">Crie o método `ProcessData`, logo após o método `Main`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="78939-252">Create the `ProcessData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static EstimatorChain<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="78939-253">Extrair recursos e transformar os dados</span><span class="sxs-lookup"><span data-stu-id="78939-253">Extract Features and transform the data</span></span>

<span data-ttu-id="78939-254">O pré-processamento e a limpeza de dados são tarefas importantes que ocorrem antes de um conjunto de dados ser usado efetivamente para o aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="78939-254">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="78939-255">Os dados brutos costumam ser ruidosos e pouco confiáveis, e podem apresentar valores faltantes.</span><span class="sxs-lookup"><span data-stu-id="78939-255">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="78939-256">Usar dados sem essas tarefas de modelagem pode produzir resultados enganosos.</span><span class="sxs-lookup"><span data-stu-id="78939-256">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="78939-257">Os pipelines de transformação do ML.NET compõem um conjunto `transforms`personalizado que é aplicado aos dados antes do treinamento ou do teste.</span><span class="sxs-lookup"><span data-stu-id="78939-257">ML.NET's transform pipelines compose a custom `transforms`set that is applied to your data before training or testing.</span></span> <span data-ttu-id="78939-258">A principal finalidade das transformações é a [personalização](../resources/glossary.md#feature-engineering) de dados.</span><span class="sxs-lookup"><span data-stu-id="78939-258">The transforms' primary purpose is data [featurization](../resources/glossary.md#feature-engineering).</span></span> <span data-ttu-id="78939-259">Os algoritmos de aprendizado de máquina entendem os [dados personalizados](../resources/glossary.md#feature), portanto, a próximo etapa é transformar nossos dados textuais em um formato que nossos algoritmos de aprendizado de máquina reconheçam.</span><span class="sxs-lookup"><span data-stu-id="78939-259">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, so the next step is to transform our textual data into a format that our ML algorithms recognize.</span></span> <span data-ttu-id="78939-260">Esse formato é um [vetor numérico](../resources/glossary.md#numerical-feature-vector).</span><span class="sxs-lookup"><span data-stu-id="78939-260">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="78939-261">Nas próximas etapas, trataremos das colunas pelos nomes definidos na classe `GitHubIssue`.</span><span class="sxs-lookup"><span data-stu-id="78939-261">In the next steps, we refer to the columns by the names defined in the `GitHubIssue` class.</span></span>

<span data-ttu-id="78939-262">Quando o modelo é treinado e avaliado, por padrão, os valores na coluna **Rótulo** são considerados os valores corretos a serem previstos.</span><span class="sxs-lookup"><span data-stu-id="78939-262">When the model is trained and evaluated, by default, the values in the **Label** column are considered as correct values to be predicted.</span></span> <span data-ttu-id="78939-263">Como queremos prever o rótulo do GitHub da Área para um `GitHubIssue`, copie a coluna `Area` na coluna **Rótulo**.</span><span class="sxs-lookup"><span data-stu-id="78939-263">As we want to predict the Area GitHub label for a `GitHubIssue`, copy the `Area` column into the **Label** column.</span></span> <span data-ttu-id="78939-264">Para fazer isso, use o `MLContext.Transforms.Conversion.MapValueToKey`, que é um wrapper para a classe de transformação <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="78939-264">To do that, use the `MLContext.Transforms.Conversion.MapValueToKey`, which is a wrapper for the <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A> transformation class.</span></span>  <span data-ttu-id="78939-265">O <xref:Microsoft.ML.Data.EstimatorChain%601> retorna um `MapValueToKey` que será efetivamente um pipeline.</span><span class="sxs-lookup"><span data-stu-id="78939-265">The `MapValueToKey` returns an <xref:Microsoft.ML.Data.EstimatorChain%601> that will effectively be a pipeline.</span></span> <span data-ttu-id="78939-266">Dê ao `pipeline` um nome de sua preferência e, em seguida, anexe o instrutor à `EstimatorChain`.</span><span class="sxs-lookup"><span data-stu-id="78939-266">Name this `pipeline` as you will then append the trainer to the `EstimatorChain`.</span></span> <span data-ttu-id="78939-267">Adicione a seguinte linha de código:</span><span class="sxs-lookup"><span data-stu-id="78939-267">Add the next line of code:</span></span>

[!code-csharp[MapValueToKey](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

 <span data-ttu-id="78939-268">A personalização atribui valores de chaves numéricas diferentes para os diferentes valores em cada uma das colunas e é usado pelo algoritmo de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="78939-268">Featurizing assigns different numeric key values to the different values in each of the columns and is used by the machine learning algorithm.</span></span> <span data-ttu-id="78939-269">Em seguida, chame `mlContext.Transforms.Text.FeaturizeText` que personaliza as colunas do texto (`Title` e `Description`) em um vetor numérico para cada `TitleFeaturized` e `DescriptionFeaturized` chamado.</span><span class="sxs-lookup"><span data-stu-id="78939-269">Next, call `mlContext.Transforms.Text.FeaturizeText` which featurizes the text (`Title` and `Description`) columns into a numeric vector for each called `TitleFeaturized` and `DescriptionFeaturized`.</span></span> <span data-ttu-id="78939-270">Acrescente a personalização para ambas as colunas ao pipeline com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="78939-270">Append the featurization for both columns to the pipeline with the following code:</span></span>

[!code-csharp[FeaturizeText](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

>[!WARNING]
> <span data-ttu-id="78939-271">A versão do ML.NET 0.10 alterou a ordem dos parâmetros de transformação.</span><span class="sxs-lookup"><span data-stu-id="78939-271">ML.NET Version 0.10 has changed the order of the Transform parameters.</span></span> <span data-ttu-id="78939-272">Isso não apresentará erros até você compilar.</span><span class="sxs-lookup"><span data-stu-id="78939-272">This will not error out until you build.</span></span> <span data-ttu-id="78939-273">Use os nomes de parâmetro para transformações, conforme ilustrado no snippet de código anterior.</span><span class="sxs-lookup"><span data-stu-id="78939-273">Use the parameter names for Transforms as illustrated in the previous code snippet.</span></span>

<span data-ttu-id="78939-274">A última etapa na preparação de dados combina todas as colunas de recursos na coluna **Features** usando a classe de transformação `Concatenate`.</span><span class="sxs-lookup"><span data-stu-id="78939-274">The last step in data preparation combines all of the feature columns into the **Features** column using the `Concatenate` transformation class.</span></span> <span data-ttu-id="78939-275">Por padrão, um algoritmo de aprendizado processa apenas os recursos da coluna **Features**.</span><span class="sxs-lookup"><span data-stu-id="78939-275">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="78939-276">Acrescente esta transformação ao pipeline com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="78939-276">Append this transformation to the pipeline with the following code:</span></span>

[!code-csharp[Concatenate](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 <span data-ttu-id="78939-277">Em seguida, acrescente um <xref:Microsoft.ML.Data.EstimatorChain`1.AppendCacheCheckpoint%2A> para armazenar a DataView em cache, para melhorar o desempenho ao iterar nos dados várias vezes usando o cache, como no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="78939-277">Next, append a <xref:Microsoft.ML.Data.EstimatorChain`1.AppendCacheCheckpoint%2A> to cache the DataView so when you iterate over the data multiple times using the cache might get better performance, as with the following code:</span></span>

[!code-csharp[AppendCache](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

> [!WARNING]
> <span data-ttu-id="78939-278">Use AppendCacheCheckpoint para conjuntos de dados pequenos/médios a fim de reduzir o tempo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="78939-278">Use AppendCacheCheckpoint for small/medium datasets to lower training time.</span></span> <span data-ttu-id="78939-279">NÃO o utilize (remova .AppendCacheCheckpoint()) ao lidar com conjuntos de dados grandes.</span><span class="sxs-lookup"><span data-stu-id="78939-279">Do NOT use it (remove .AppendCacheCheckpoint()) when handling very large datasets.</span></span>

<span data-ttu-id="78939-280">Retorne o pipeline no final do método `ProcessData`.</span><span class="sxs-lookup"><span data-stu-id="78939-280">Return the pipeline at the end of the `ProcessData` method.</span></span>

[!code-csharp[ReturnPipeline](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

<span data-ttu-id="78939-281">Esta etapa manipula o pré-processamento/personalização.</span><span class="sxs-lookup"><span data-stu-id="78939-281">This step handles preprocessing/featurization.</span></span> <span data-ttu-id="78939-282">Usar componentes adicionais disponíveis no ML.NET pode permitir melhores resultados com o seu modelo.</span><span class="sxs-lookup"><span data-stu-id="78939-282">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="build-and-train-the-model"></a><span data-ttu-id="78939-283">Criar e treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="78939-283">Build and train the model</span></span>

<span data-ttu-id="78939-284">Adicione a seguinte chamada ao método `BuildAndTrainModel` como a próxima linha de código no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="78939-284">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="78939-285">O método `BuildAndTrainModel` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="78939-285">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="78939-286">Cria a classe de algoritmo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="78939-286">Creates the training algorithm class.</span></span>
* <span data-ttu-id="78939-287">Treina o modelo.</span><span class="sxs-lookup"><span data-stu-id="78939-287">Trains the model.</span></span>
* <span data-ttu-id="78939-288">Prevê a área com base em dados de treinamento.</span><span class="sxs-lookup"><span data-stu-id="78939-288">Predicts area based on training data.</span></span>
* <span data-ttu-id="78939-289">Salva o modelo em um arquivo `.zip`.</span><span class="sxs-lookup"><span data-stu-id="78939-289">Saves the model to a `.zip` file.</span></span>
* <span data-ttu-id="78939-290">Retorna o modelo.</span><span class="sxs-lookup"><span data-stu-id="78939-290">Returns the model.</span></span>

<span data-ttu-id="78939-291">Crie o método `BuildAndTrainModel`, logo após o método `Main`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="78939-291">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static EstimatorChain<KeyToValueMappingTransformer> BuildAndTrainModel(IDataView trainingDataView, EstimatorChain<ITransformer> pipeline)
{

}
```

<span data-ttu-id="78939-292">Observe que dois parâmetros são passados para o método BuildAndTrainModel; um `IDataView` para o conjunto de dados de treinamento (`trainingDataView`) e um <xref:Microsoft.ML.Data.EstimatorChain%601> para o pipeline de processamento criado no ProcessData (`pipeline`).</span><span class="sxs-lookup"><span data-stu-id="78939-292">Notice that two parameters are passed into the BuildAndTrainModel method; an `IDataView` for the training dataset (`trainingDataView`), and a <xref:Microsoft.ML.Data.EstimatorChain%601> for the processing pipeline created in ProcessData (`pipeline`).</span></span>

 <span data-ttu-id="78939-293">Adicione o seguinte código como a primeira linha do método `BuildAndTrainModel`:</span><span class="sxs-lookup"><span data-stu-id="78939-293">Add the following code as the first line of the `BuildAndTrainModel` method:</span></span>

### <a name="choose-a-learning-algorithm"></a><span data-ttu-id="78939-294">Escolher um algoritmo de aprendizado</span><span class="sxs-lookup"><span data-stu-id="78939-294">Choose a learning algorithm</span></span>

<span data-ttu-id="78939-295">Para adicionar o algoritmo de aprendizado, chame o método de wrapper `mlContext.MulticlassClassification.Trainers.StochasticDualCoordinateAscent` que retorna um objeto <xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer>.</span><span class="sxs-lookup"><span data-stu-id="78939-295">To add the learning algorithm, call the `mlContext.MulticlassClassification.Trainers.StochasticDualCoordinateAscent` wrapper method which returns a <xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer> object.</span></span>  <span data-ttu-id="78939-296">O `SdcaMultiClassTrainer` é anexado ao `pipeline` e aceita os `Title` e `Description` (`Features`) personalizados e os parâmetro de entrada `Label` para aprender com os dados históricos.</span><span class="sxs-lookup"><span data-stu-id="78939-296">The `SdcaMultiClassTrainer` is appended to the `pipeline` and accepts the featurized `Title` and `Description` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span> <span data-ttu-id="78939-297">Você também precisa mapear o rótulo para o valor para retorná-lo ao seu estado legível original.</span><span class="sxs-lookup"><span data-stu-id="78939-297">You also need to map the label to the value to return to its original readable state.</span></span> <span data-ttu-id="78939-298">Realize ambas essas ações com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="78939-298">Do both of those actions with the following code:</span></span>

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

### <a name="train-the-model"></a><span data-ttu-id="78939-299">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="78939-299">Train the model</span></span>

<span data-ttu-id="78939-300">Você treina o modelo, <xref:Microsoft.ML.Data.TransformerChain%601>, com base no conjunto de dados que foi carregado e transformado.</span><span class="sxs-lookup"><span data-stu-id="78939-300">You train the model, <xref:Microsoft.ML.Data.TransformerChain%601>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="78939-301">Depois que o avaliador tiver sido definido, treine o modelo usando o <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> e forneça os dados de treinamento já carregados.</span><span class="sxs-lookup"><span data-stu-id="78939-301">Once the estimator has been defined, you train your model using the <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> while providing the already loaded training data.</span></span> <span data-ttu-id="78939-302">Esse método retorna um modelo a ser usado para previsões.</span><span class="sxs-lookup"><span data-stu-id="78939-302">This  method returns a model to use for predictions.</span></span> <span data-ttu-id="78939-303">`trainingPipeline.Fit()` treina o pipeline e retorna um `Transformer` com base no `DataView` passado.</span><span class="sxs-lookup"><span data-stu-id="78939-303">`trainingPipeline.Fit()` trains the pipeline and returns a `Transformer` based on the `DataView` passed in.</span></span> <span data-ttu-id="78939-304">O teste não é executado até que o método `.Fit()` seja executado.</span><span class="sxs-lookup"><span data-stu-id="78939-304">The experiment is not executed until the `.Fit()` method runs.</span></span>

<span data-ttu-id="78939-305">Adicione o seguinte código ao método `BuildAndTrainModel`:</span><span class="sxs-lookup"><span data-stu-id="78939-305">Add the following code to the `BuildAndTrainModel` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

<span data-ttu-id="78939-306">Embora o `model` seja um `transformer` que opera em várias linhas de dados, a necessidade de previsões em exemplos individuais é um cenário comum de produção.</span><span class="sxs-lookup"><span data-stu-id="78939-306">While the `model` is a `transformer` that operates on many rows of data, a need for predictions on individual examples is a common production scenario.</span></span> <span data-ttu-id="78939-307">O <xref:Microsoft.ML.PredictionEngine%602> é um wrapper que é retornado do método `CreatePredictionEngine`.</span><span class="sxs-lookup"><span data-stu-id="78939-307">The <xref:Microsoft.ML.PredictionEngine%602> is a wrapper that is returned from the `CreatePredictionEngine` method.</span></span> <span data-ttu-id="78939-308">Adicionaremos o seguinte código para criar `PredictionEngine` como a próxima linha no método `BuildAndTrainModel`:</span><span class="sxs-lookup"><span data-stu-id="78939-308">Let's add the following code to create the `PredictionEngine` as the next line in the `BuildAndTrainModel` Method:</span></span>

[!code-csharp[CreatePredictionEngine1](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a><span data-ttu-id="78939-309">Prever com o modelo treinado</span><span class="sxs-lookup"><span data-stu-id="78939-309">Predict with the trained model</span></span>

<span data-ttu-id="78939-310">Adicione um problema do GitHub para testar a previsão do modelo treinado no método `Predict` ao criar uma instância de `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="78939-310">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[CreateTestIssue1](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

<span data-ttu-id="78939-311">Você pode usá-lo para prever o rótulo `Area` de uma única instância dos dados do problema.</span><span class="sxs-lookup"><span data-stu-id="78939-311">You can use that to predict the `Area` label of a single instance of the issue data.</span></span> <span data-ttu-id="78939-312">Para obter uma previsão, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> nos dados.</span><span class="sxs-lookup"><span data-stu-id="78939-312">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="78939-313">Os dados de entrada são uma cadeia de caracteres e o modelo inclui a personalização.</span><span class="sxs-lookup"><span data-stu-id="78939-313">The input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="78939-314">Seu pipeline está em sincronia durante o treinamento e a previsão.</span><span class="sxs-lookup"><span data-stu-id="78939-314">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="78939-315">Você não precisou escrever código de pré-processamento/personalização especificamente para previsões, e a mesma API cuida das previsões de lote e de uso único.</span><span class="sxs-lookup"><span data-stu-id="78939-315">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a><span data-ttu-id="78939-316">Usando o modelo: resultados de previsão</span><span class="sxs-lookup"><span data-stu-id="78939-316">Using the model: prediction results</span></span>

<span data-ttu-id="78939-317">Exiba `GitHubIssue` e a previsão de rótulo `Area` correspondente para compartilhar os resultados e agir de acordo com eles.</span><span class="sxs-lookup"><span data-stu-id="78939-317">Display `GitHubIssue` and corresponding `Area` label prediction in order to share the results and act on them accordingly.</span></span>  <span data-ttu-id="78939-318">Crie uma exibição para os resultados usando o seguinte código <xref:System.Console.WriteLine?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="78939-318">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="78939-319">Retornar o modelo treinado a ser usado para avaliação</span><span class="sxs-lookup"><span data-stu-id="78939-319">Return the model trained to use for evaluation</span></span>

<span data-ttu-id="78939-320">Retorne o modelo no final do método `BuildAndTrainModel`.</span><span class="sxs-lookup"><span data-stu-id="78939-320">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a><span data-ttu-id="78939-321">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="78939-321">Evaluate the model</span></span>

<span data-ttu-id="78939-322">Agora que você criou e treinou o modelo, precisa avaliá-lo com um conjunto de dados diferente para garantia de qualidade e validação.</span><span class="sxs-lookup"><span data-stu-id="78939-322">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="78939-323">No método `Evaluate`, o modelo criado em `BuildAndTrainModel` é passado para ser avaliado.</span><span class="sxs-lookup"><span data-stu-id="78939-323">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="78939-324">Crie o método `Evaluate` , logo após `BuildAndTrainModel`, como no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="78939-324">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate()
{

}
```

<span data-ttu-id="78939-325">O método `Evaluate` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="78939-325">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="78939-326">Carrega o conjunto de dados de teste.</span><span class="sxs-lookup"><span data-stu-id="78939-326">Loads the test dataset.</span></span>
* <span data-ttu-id="78939-327">Cria o avaliador multiclasse.</span><span class="sxs-lookup"><span data-stu-id="78939-327">Creates the multiclass evaluator.</span></span>
* <span data-ttu-id="78939-328">Avalia o modelo e cria métricas.</span><span class="sxs-lookup"><span data-stu-id="78939-328">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="78939-329">Exibe as métricas.</span><span class="sxs-lookup"><span data-stu-id="78939-329">Displays the metrics.</span></span>

<span data-ttu-id="78939-330">Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `BuildAndTrainModel`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="78939-330">Add a call to the new method from the `Main` method, right under the `BuildAndTrainModel` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

<span data-ttu-id="78939-331">Assim como você fez anteriormente com o conjunto de dados de treinamento, você pode combinar a inicialização, o mapeamento e testar o carregamento do conjunto de dados em uma linha de código.</span><span class="sxs-lookup"><span data-stu-id="78939-331">As you did previously with the training dataset, you can combine the initialization, mapping, and test dataset loading into one line of code.</span></span> <span data-ttu-id="78939-332">Você pode avaliar o modelo usando esse conjunto de dados como uma verificação de qualidade.</span><span class="sxs-lookup"><span data-stu-id="78939-332">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="78939-333">Adicione o seguinte código ao método `Evaluate`:</span><span class="sxs-lookup"><span data-stu-id="78939-333">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

<span data-ttu-id="78939-334">O método `MulticlassClassificationContext.Evaluate` é o wrapper para o método <xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A>, que calcula as métricas de qualidade para o modelo usando o conjunto de dados especificado.</span><span class="sxs-lookup"><span data-stu-id="78939-334">The `MulticlassClassificationContext.Evaluate` is a wrapper for the <xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A> method that computes the quality metrics for the model using the specified dataset.</span></span> <span data-ttu-id="78939-335">Ele retorna um objeto <xref:Microsoft.ML.Data.MultiClassClassifierMetrics> que contém as métricas gerais calculadas pelos avaliadores de classificação multiclasse.</span><span class="sxs-lookup"><span data-stu-id="78939-335">It returns a <xref:Microsoft.ML.Data.MultiClassClassifierMetrics> object that contains the overall metrics computed by multiclass classification evaluators.</span></span>
<span data-ttu-id="78939-336">Para exibir as métricas para determinar a qualidade do modelo, você precisará obtê-las primeiro.</span><span class="sxs-lookup"><span data-stu-id="78939-336">To display the metrics to determine the quality of the model, you need to get them first.</span></span>
<span data-ttu-id="78939-337">Observe o uso do método `Transform` da variável global `_trainedModel` de aprendizado de máquina (um transformador) para inserir os recursos e retornar previsões.</span><span class="sxs-lookup"><span data-stu-id="78939-337">Notice the use of the `Transform` method of the machine learning `_trainedModel` global variable (a transformer) to input the features and return predictions.</span></span> <span data-ttu-id="78939-338">Adicione o seguinte código ao método `Evaluate` como a linha seguinte:</span><span class="sxs-lookup"><span data-stu-id="78939-338">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

<span data-ttu-id="78939-339">As métricas a seguir são avaliadas para classificação multiclasse:</span><span class="sxs-lookup"><span data-stu-id="78939-339">The following metrics are evaluated for multiclass classification:</span></span>

* <span data-ttu-id="78939-340">Microprecisão – todo par de classe/exemplo contribui igualmente para a métrica de precisão.</span><span class="sxs-lookup"><span data-stu-id="78939-340">Micro Accuracy - Every sample-class pair contributes equally to the accuracy metric.</span></span>  <span data-ttu-id="78939-341">Convém que a Microprecisão seja tão próxima de 1 quanto possível.</span><span class="sxs-lookup"><span data-stu-id="78939-341">You want Micro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="78939-342">Macroprecisão – toda classe contribui igualmente para a métrica de precisão.</span><span class="sxs-lookup"><span data-stu-id="78939-342">Macro Accuracy - Every class contributes equally to the accuracy metric.</span></span> <span data-ttu-id="78939-343">Classes minoritárias recebem o mesmo peso que as classes maiores.</span><span class="sxs-lookup"><span data-stu-id="78939-343">Minority classes are given equal weight as the larger classes.</span></span> <span data-ttu-id="78939-344">Convém que a Macroprecisão seja tão próxima de 1 quanto possível.</span><span class="sxs-lookup"><span data-stu-id="78939-344">You want Macro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="78939-345">Perda de log – consulte [Perda de log](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="78939-345">Log-loss - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="78939-346">Convém que a Perda de log seja tão próxima de zero quanto possível.</span><span class="sxs-lookup"><span data-stu-id="78939-346">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="78939-347">Redução de perda de log – varia de [-inf, 100], em que 100 é composto pelas previsões perfeitas e 0 indica previsões de média.</span><span class="sxs-lookup"><span data-stu-id="78939-347">Log-loss reduction - Ranges from [-inf, 100], where 100 is perfect predictions and 0 indicates mean predictions.</span></span> <span data-ttu-id="78939-348">Convém que a redução de perda de log seja tão próxima de zero quanto possível.</span><span class="sxs-lookup"><span data-stu-id="78939-348">You want Log-loss reduction to be as close to zero as possible.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="78939-349">Exibir as métricas para validação de modelo</span><span class="sxs-lookup"><span data-stu-id="78939-349">Displaying the metrics for model validation</span></span>

<span data-ttu-id="78939-350">Use o código a seguir para exibir as métricas, compartilhar os resultados e, em seguida, agir com relação a eles:</span><span class="sxs-lookup"><span data-stu-id="78939-350">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

### <a name="save-the-trained-and-evaluated-model"></a><span data-ttu-id="78939-351">Salvar o modelo treinado e avaliado</span><span class="sxs-lookup"><span data-stu-id="78939-351">Save the trained and evaluated model</span></span>

<span data-ttu-id="78939-352">Neste ponto, você tem um modelo de tipo <xref:Microsoft.ML.Data.TransformerChain%601> que pode ser integrado em qualquer um dos seus aplicativos .NET existentes ou novos.</span><span class="sxs-lookup"><span data-stu-id="78939-352">At this point, you have a model of type <xref:Microsoft.ML.Data.TransformerChain%601> that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="78939-353">Para salvar seu modelo treinado como um arquivo .zip, adicione o seguinte código para chamar o método `SaveModelAsFile` como a linha seguinte em `BuildAndTrainModel`:</span><span class="sxs-lookup"><span data-stu-id="78939-353">To save your trained model to a .zip file, add the following code to call the `SaveModelAsFile` method as the next line in `BuildAndTrainModel`:</span></span>

[!code-csharp[CallSaveModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallSaveModel)]

## <a name="save-the-model-as-a-zip-file"></a><span data-ttu-id="78939-354">Salvar o modelo como um arquivo .zip</span><span class="sxs-lookup"><span data-stu-id="78939-354">Save the model as a .zip file</span></span>

<span data-ttu-id="78939-355">Crie o método `SaveModelAsFile`, logo após o método `Evaluate`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="78939-355">Create the `SaveModelAsFile` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="78939-356">O método `SaveModelAsFile` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="78939-356">The `SaveModelAsFile` method executes the following tasks:</span></span>

* <span data-ttu-id="78939-357">Salva o modelo como um arquivo .zip.</span><span class="sxs-lookup"><span data-stu-id="78939-357">Saves the model as a .zip file.</span></span>

<span data-ttu-id="78939-358">Em seguida, crie um método para salvar o modelo para que ele possa ser reutilizado e consumido em outros aplicativos.</span><span class="sxs-lookup"><span data-stu-id="78939-358">Next, create a method to save the model so that it can be reused and consumed in other applications.</span></span> <span data-ttu-id="78939-359">O `ITransformer` tem um método <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> que usa o campo global `_modelPath` e um <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="78939-359">The `ITransformer` has a <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> method that takes in the `_modelPath` global field, and a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="78939-360">Para salvar o modelo como um arquivo zip, crie o `FileStream` imediatamente antes de chamar o método `SaveTo`.</span><span class="sxs-lookup"><span data-stu-id="78939-360">To save the model as a zip file, you'll create the `FileStream` immediately before calling the `SaveTo` method.</span></span> <span data-ttu-id="78939-361">Adicione o seguinte código ao método `SaveModelAsFile` como a linha seguinte:</span><span class="sxs-lookup"><span data-stu-id="78939-361">Add the following code to the `SaveModelAsFile` method as the next line:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SaveModel)]

<span data-ttu-id="78939-362">Você também pode exibir onde o arquivo foi gravado ao gravar uma mensagem de console com o `_modelPath`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="78939-362">You could also display where the file was written by writing a console message with the `_modelPath`, using the following code:</span></span>

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="deploy-and-predict-with-a-loaded-model"></a><span data-ttu-id="78939-363">Implantar e prever com um modelo carregado</span><span class="sxs-lookup"><span data-stu-id="78939-363">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="78939-364">Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `Evaluate`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="78939-364">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredictIssue](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

<span data-ttu-id="78939-365">Crie o método `PredictIssue` logo após o método `Evaluate` (e antes do método `SaveModelAsFile`) usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="78939-365">Create the `PredictIssue` method, just after the `Evaluate` method (and just before the `SaveModelAsFile` method), using the following code:</span></span>

```csharp
private static void PredictIssue()
{

}
```

<span data-ttu-id="78939-366">O método `PredictIssue` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="78939-366">The `PredictIssue` method executes the following tasks:</span></span>

* <span data-ttu-id="78939-367">Cria um único problema dos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="78939-367">Creates a single issue of test data.</span></span>
* <span data-ttu-id="78939-368">Prevê a área com base em dados de teste.</span><span class="sxs-lookup"><span data-stu-id="78939-368">Predicts Area based on test data.</span></span>
* <span data-ttu-id="78939-369">Combina dados de teste e previsões para relatórios.</span><span class="sxs-lookup"><span data-stu-id="78939-369">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="78939-370">Exibe os resultados previstos.</span><span class="sxs-lookup"><span data-stu-id="78939-370">Displays the predicted results.</span></span>

<span data-ttu-id="78939-371">Primeiro, carregue o modelo que você salvou anteriormente com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="78939-371">First, load the model that you saved previously with the following code:</span></span>

[!code-csharp[LoadModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadModel)]

<span data-ttu-id="78939-372">Adicione um problema do GitHub para testar a previsão do modelo treinado no método `Predict` ao criar uma instância de `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="78939-372">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[AddTestIssue](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]
  
<span data-ttu-id="78939-373">Agora que tem um modelo, você pode usá-lo para prever o rótulo do GitHub da área de uma única instância dos dados do problema do GitHub.</span><span class="sxs-lookup"><span data-stu-id="78939-373">Now that you have a model, you can use that to predict the Area GitHub label of a single instance of the GitHub issue data.</span></span> <span data-ttu-id="78939-374">Para obter uma previsão, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> nos dados.</span><span class="sxs-lookup"><span data-stu-id="78939-374">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="78939-375">Os dados de entrada são uma cadeia de caracteres e o modelo inclui a personalização.</span><span class="sxs-lookup"><span data-stu-id="78939-375">The input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="78939-376">Seu pipeline está em sincronia durante o treinamento e a previsão.</span><span class="sxs-lookup"><span data-stu-id="78939-376">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="78939-377">Você não precisou escrever código de pré-processamento/personalização especificamente para previsões, e a mesma API cuida das previsões de lote e de uso único.</span><span class="sxs-lookup"><span data-stu-id="78939-377">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span> <span data-ttu-id="78939-378">Adicione o código a seguir ao método `PredictIssue` para as previsões:</span><span class="sxs-lookup"><span data-stu-id="78939-378">Add the following code to the `PredictIssue` method for the predictions:</span></span>

[!code-csharp[PredictIssue](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a><span data-ttu-id="78939-379">Usando o modelo carregado para previsão</span><span class="sxs-lookup"><span data-stu-id="78939-379">Using the loaded model for prediction</span></span>

<span data-ttu-id="78939-380">Exiba `Area` para categorizar o problema e agir adequadamente para solucioná-lo.</span><span class="sxs-lookup"><span data-stu-id="78939-380">Display `Area` in order to categorize the issue and act on it accordingly.</span></span> <span data-ttu-id="78939-381">Crie uma exibição para os resultados usando o seguinte código <xref:System.Console.WriteLine?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="78939-381">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayResults](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a><span data-ttu-id="78939-382">Resultados</span><span class="sxs-lookup"><span data-stu-id="78939-382">Results</span></span>

<span data-ttu-id="78939-383">Seus resultados devem ser semelhantes aos seguintes.</span><span class="sxs-lookup"><span data-stu-id="78939-383">Your results should be similar to the following.</span></span> <span data-ttu-id="78939-384">Conforme o pipeline processa, exibe mensagens.</span><span class="sxs-lookup"><span data-stu-id="78939-384">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="78939-385">Você pode ver avisos ou mensagens de processamento.</span><span class="sxs-lookup"><span data-stu-id="78939-385">You may see warnings, or processing messages.</span></span> <span data-ttu-id="78939-386">Essas mensagens foram removidas dos resultados a seguir para ficar mais claro.</span><span class="sxs-lookup"><span data-stu-id="78939-386">These messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="78939-387">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="78939-387">Congratulations!</span></span> <span data-ttu-id="78939-388">Agora você criou com sucesso um modelo de machine learning para classificar e prever um rótulo de Área para um problema do GitHub.</span><span class="sxs-lookup"><span data-stu-id="78939-388">You've now successfully built a machine learning model for classifying and predicting an Area label for a GitHub issue.</span></span> <span data-ttu-id="78939-389">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification).</span><span class="sxs-lookup"><span data-stu-id="78939-389">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="78939-390">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="78939-390">Next steps</span></span>

<span data-ttu-id="78939-391">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="78939-391">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="78939-392">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="78939-392">Understand the problem</span></span>
> * <span data-ttu-id="78939-393">Selecionar o algoritmo de aprendizado de máquina apropriado</span><span class="sxs-lookup"><span data-stu-id="78939-393">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="78939-394">Preparar seus dados</span><span class="sxs-lookup"><span data-stu-id="78939-394">Prepare your data</span></span>
> * <span data-ttu-id="78939-395">Transformar os dados</span><span class="sxs-lookup"><span data-stu-id="78939-395">Transform the data</span></span>
> * <span data-ttu-id="78939-396">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="78939-396">Train the model</span></span>
> * <span data-ttu-id="78939-397">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="78939-397">Evaluate the model</span></span>
> * <span data-ttu-id="78939-398">Prever com o modelo treinado</span><span class="sxs-lookup"><span data-stu-id="78939-398">Predict with the trained model</span></span>
> * <span data-ttu-id="78939-399">Implantar e prever com um modelo carregado</span><span class="sxs-lookup"><span data-stu-id="78939-399">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="78939-400">Avançar para o próximo tutorial para saber mais</span><span class="sxs-lookup"><span data-stu-id="78939-400">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="78939-401">Previsão do valor da corrida do táxi</span><span class="sxs-lookup"><span data-stu-id="78939-401">Taxi Fare Predictor</span></span>](taxi-fare.md)
