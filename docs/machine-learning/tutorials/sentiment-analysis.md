---
title: Usar o ML.NET em um cenário de classificação binária de análise de sentimento
description: Descubra como usar o ML.NET em um cenário de classificação binária para entender como usar a previsão de sentimentos para executar a ação apropriada.
ms.date: 03/07/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: e88a85b96c1e5d33d748332991cb9480222a9c66
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612089"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a><span data-ttu-id="0f5e0-103">Tutorial: Usar o ML.NET em um cenário de classificação binária de análise de sentimento</span><span class="sxs-lookup"><span data-stu-id="0f5e0-103">Tutorial: Use ML.NET in a sentiment analysis binary classification scenario</span></span>

<span data-ttu-id="0f5e0-104">Este tutorial de exemplo ilustra o uso do ML.NET para criar um classificador de sentimento para prever um sentimento positivo ou negativo por meio de um aplicativo de console do .NET Core usando C# no Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-104">This sample tutorial illustrates using ML.NET to create a sentiment classifier to predict either positive or negative sentiment via a .NET Core console application using C# in Visual Studio 2017.</span></span> <span data-ttu-id="0f5e0-105">No mundo do aprendizado de máquina, esse tipo de previsão é conhecido como classificação binária.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-105">In the world of machine learning, this type of prediction is known as binary classification.</span></span>

> [!NOTE]
> <span data-ttu-id="0f5e0-106">Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-106">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="0f5e0-107">Para obter mais informações, visite [a introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="0f5e0-107">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="0f5e0-108">Este tutorial e uma amostra relacionada estão usando o **ML.NET versão 0.11** no momento.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-108">This tutorial and related sample are currently using **ML.NET version 0.11**.</span></span> <span data-ttu-id="0f5e0-109">Saiba mais nas notas de versão no [repositório do GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)</span><span class="sxs-lookup"><span data-stu-id="0f5e0-109">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)</span></span>

<span data-ttu-id="0f5e0-110">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-110">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="0f5e0-111">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="0f5e0-111">Understand the problem</span></span>
> * <span data-ttu-id="0f5e0-112">Selecionar o algoritmo de aprendizado de máquina apropriado</span><span class="sxs-lookup"><span data-stu-id="0f5e0-112">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="0f5e0-113">Preparar seus dados</span><span class="sxs-lookup"><span data-stu-id="0f5e0-113">Prepare your data</span></span>
> * <span data-ttu-id="0f5e0-114">Transformar os dados</span><span class="sxs-lookup"><span data-stu-id="0f5e0-114">Transform the data</span></span>
> * <span data-ttu-id="0f5e0-115">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="0f5e0-115">Train the model</span></span>
> * <span data-ttu-id="0f5e0-116">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="0f5e0-116">Evaluate the model</span></span>
> * <span data-ttu-id="0f5e0-117">Prever com o modelo treinado</span><span class="sxs-lookup"><span data-stu-id="0f5e0-117">Predict with the trained model</span></span>
> * <span data-ttu-id="0f5e0-118">Implantar e prever com um modelo carregado</span><span class="sxs-lookup"><span data-stu-id="0f5e0-118">Deploy and Predict with a loaded model</span></span>

## <a name="sentiment-analysis-sample-overview"></a><span data-ttu-id="0f5e0-119">Visão geral da amostra de análise de sentimento</span><span class="sxs-lookup"><span data-stu-id="0f5e0-119">Sentiment analysis sample overview</span></span>

<span data-ttu-id="0f5e0-120">A amostra é um aplicativo de console que usa o ML.NET para treinar um modelo que classifica e prevê o sentimento como positivo ou negativo.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-120">The sample is a console app that uses ML.NET to train a model that classifies and predicts sentiment as either positive or negative.</span></span> <span data-ttu-id="0f5e0-121">O conjunto de dados de sentimentos do Yelp é da Universidade da Califórnia, Irvine (UCI), e é dividido em um conjunto de dados de treinamento e um conjunto de dados de teste.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-121">The Yelp sentiment dataset is from University of California, Irvine (UCI), which is split into a train dataset and a test dataset.</span></span> <span data-ttu-id="0f5e0-122">A amostra avalia o modelo com um conjunto de dados de teste para análise da qualidade.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-122">The sample evaluates the model with the test dataset for quality analysis.</span></span>

<span data-ttu-id="0f5e0-123">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis).</span><span class="sxs-lookup"><span data-stu-id="0f5e0-123">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0f5e0-124">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="0f5e0-124">Prerequisites</span></span>

* <span data-ttu-id="0f5e0-125">[Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-125">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* [<span data-ttu-id="0f5e0-126">O arquivo zip do conjunto de dados de Sentenças de sentimentos rotuladas da UCI</span><span class="sxs-lookup"><span data-stu-id="0f5e0-126">The UCI Sentiment Labeled Sentences dataset zip file</span></span>](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)

## <a name="machine-learning-workflow"></a><span data-ttu-id="0f5e0-127">Fluxo de trabalho de aprendizado de máquina</span><span class="sxs-lookup"><span data-stu-id="0f5e0-127">Machine learning workflow</span></span>

<span data-ttu-id="0f5e0-128">Este tutorial segue um fluxo de trabalho de aprendizado de máquina que permite que o processo se mova de maneira ordenada.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-128">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="0f5e0-129">As fases do fluxo de trabalho são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-129">The workflow phases are as follows:</span></span>

1. <span data-ttu-id="0f5e0-130">**Compreender o problema**</span><span class="sxs-lookup"><span data-stu-id="0f5e0-130">**Understand the problem**</span></span>
2. <span data-ttu-id="0f5e0-131">**Preparar seus dados**</span><span class="sxs-lookup"><span data-stu-id="0f5e0-131">**Prepare your data**</span></span>
   * <span data-ttu-id="0f5e0-132">**Carregar os dados**</span><span class="sxs-lookup"><span data-stu-id="0f5e0-132">**Load the data**</span></span>
   * <span data-ttu-id="0f5e0-133">**Extrair recursos (Transformar seus dados)**</span><span class="sxs-lookup"><span data-stu-id="0f5e0-133">**Extract features (Transform your data)**</span></span>
3. <span data-ttu-id="0f5e0-134">**Compilar e treinar**</span><span class="sxs-lookup"><span data-stu-id="0f5e0-134">**Build and train**</span></span>
   * <span data-ttu-id="0f5e0-135">**Treinar o modelo**</span><span class="sxs-lookup"><span data-stu-id="0f5e0-135">**Train the model**</span></span>
   * <span data-ttu-id="0f5e0-136">**Avaliar o modelo**</span><span class="sxs-lookup"><span data-stu-id="0f5e0-136">**Evaluate the model**</span></span>
4. <span data-ttu-id="0f5e0-137">**Implantar Modelo**</span><span class="sxs-lookup"><span data-stu-id="0f5e0-137">**Deploy Model**</span></span>
   * <span data-ttu-id="0f5e0-138">**Usar o modelo para prever**</span><span class="sxs-lookup"><span data-stu-id="0f5e0-138">**Use the Model to predict**</span></span>

### <a name="understand-the-problem"></a><span data-ttu-id="0f5e0-139">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="0f5e0-139">Understand the problem</span></span>

<span data-ttu-id="0f5e0-140">Você primeiro precisa compreender o problema, para que possa dividi-lo em partes que possam oferecer suporte à criação e ao treinamento do modelo.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-140">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="0f5e0-141">Dividir o problema permite prever e avaliar os resultados.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-141">Breaking the problem down allows you to predict and evaluate the results.</span></span>

<span data-ttu-id="0f5e0-142">O problema deste tutorial é compreender o sentimento de comentário do site recebido para executar a ação apropriada.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-142">The problem for this tutorial is to understand incoming website comment sentiment to take the appropriate action.</span></span>

<span data-ttu-id="0f5e0-143">Você pode dividir o problema com o texto de sentimento e o valor de sentimento para os dados com os quais deseja treinar o modelo e com um valor de sentimento previsto que você pode avaliar e usar operacionalmente.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-143">You can break down the problem to the sentiment text and sentiment value for the data you want to train the model with, and a predicted sentiment value that you can evaluate and then use operationally.</span></span>

<span data-ttu-id="0f5e0-144">Em seguida, você precisa **determinar** o sentimento, o que ajuda na seleção da tarefa de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-144">You then need to **determine** the sentiment, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-algorithm"></a><span data-ttu-id="0f5e0-145">Selecionar o algoritmo de aprendizado de máquina apropriado</span><span class="sxs-lookup"><span data-stu-id="0f5e0-145">Select the appropriate machine learning algorithm</span></span>

<span data-ttu-id="0f5e0-146">Com este problema, você está a par dos seguintes fatos:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-146">With this problem, you know the following facts:</span></span>

<span data-ttu-id="0f5e0-147">Dados de treinamento: os comentários do site podem ser positivos (1) ou negativos (0) (**sentimento**).</span><span class="sxs-lookup"><span data-stu-id="0f5e0-147">Training data: website comments can be positive (1) or negative (0) (**sentiment**).</span></span>

<span data-ttu-id="0f5e0-148">Preveja o **sentimento** de um novo comentário no site, seja positivo ou negativo, como nos exemplos a seguir:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-148">Predict the **sentiment** of a new website comment, either positive or negative, such as in the following examples:</span></span>

* <span data-ttu-id="0f5e0-149">Adoro os garçons daqui.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-149">I love the wait staff here.</span></span> <span data-ttu-id="0f5e0-150">Eles são ótimos.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-150">They rock.</span></span>
* <span data-ttu-id="0f5e0-151">Este lugar tem a pior sopa.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-151">This place has the worst soup.</span></span>

<span data-ttu-id="0f5e0-152">O algoritmo de aprendizado de máquina de classificação é mais adequado para esse cenário.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-152">The classification machine learning algorithm is best suited for this scenario.</span></span>

### <a name="about-the-classification-algorithm"></a><span data-ttu-id="0f5e0-153">Sobre o algoritmo de classificação</span><span class="sxs-lookup"><span data-stu-id="0f5e0-153">About the classification algorithm</span></span>

<span data-ttu-id="0f5e0-154">A classificação é um algoritmo de aprendizado de máquina que usa os dados para **determinar** a categoria, o tipo ou a classe de um item ou de uma linha de dados.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-154">Classification is a machine learning algorithm that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="0f5e0-155">Por exemplo, você pode usar a classificação para:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-155">For example, you can use classification to:</span></span>

* <span data-ttu-id="0f5e0-156">Identificar o sentimento como positivo ou negativo.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-156">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="0f5e0-157">Classificar email como spam, lixo eletrônico ou bom.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-157">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="0f5e0-158">Determinar se a amostra de laboratório de um paciente é cancerígena.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-158">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="0f5e0-159">Categorizar os clientes pela sua propensão a responder a uma campanha de vendas.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-159">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="0f5e0-160">Algoritmos de classificação são frequentemente de um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-160">Classification algorithms are frequently one of the following types:</span></span>

* <span data-ttu-id="0f5e0-161">Binário: A ou B.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-161">Binary: either A or B.</span></span>
* <span data-ttu-id="0f5e0-162">Multiclasse: várias categorias que podem ser previstas usando um único modelo.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-162">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="0f5e0-163">Visto que os comentários do site precisam ser classificados como positivos ou negativos, você pode usar o algoritmo de Classificação binária.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-163">Because the website comments need to be classified as either positive or negative, you use the Binary Classification algorithm.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="0f5e0-164">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="0f5e0-164">Create a console application</span></span>

1. <span data-ttu-id="0f5e0-165">Abra o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-165">Open Visual Studio 2017.</span></span> <span data-ttu-id="0f5e0-166">Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-166">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="0f5e0-167">Na caixa de diálogo **Novo Projeto**, selecione o nó **Visual C#** seguido pelo nó **.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-167">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="0f5e0-168">Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-168">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="0f5e0-169">Na caixa de texto **Nome**, digite "SentimentAnalysis" e, em seguida, selecione o botão **OK** .</span><span class="sxs-lookup"><span data-stu-id="0f5e0-169">In the **Name** text box, type "SentimentAnalysis" and then select the **OK** button.</span></span>

2. <span data-ttu-id="0f5e0-170">Crie um diretório chamado *Data* no seu projeto para salvar seus arquivos do conjunto de dados:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-170">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="0f5e0-171">No **Gerenciador de Soluções**, clique com o botão direito do mouse no seu projeto e selecione **Adicionar** > **Nova Pasta**.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-171">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="0f5e0-172">Digite "Dados" e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-172">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="0f5e0-173">Instalar o **Pacote NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-173">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="0f5e0-174">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-174">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="0f5e0-175">Escolha "nuget.org" como a Origem do pacote, selecione a guia Procurar, pesquise por **Microsoft.ML**, selecione o pacote na lista e escolha o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-175">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="0f5e0-176">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-176">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="0f5e0-177">Preparar seus dados</span><span class="sxs-lookup"><span data-stu-id="0f5e0-177">Prepare your data</span></span>

1. <span data-ttu-id="0f5e0-178">Baixe o [arquivo zip do conjunto de dados de Sentenças de sentimentos rotuladas da UCI (consulte as citações na nota a seguir) ](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) e descompacte-o.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-178">Download [The UCI Sentiment Labeled Sentences dataset zip file (see citations in the following note)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="0f5e0-179">Copie o arquivo `yelp_labelled.txt` para o diretório *Dados* que você criou.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-179">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

> [!NOTE]
> <span data-ttu-id="0f5e0-180">Os conjuntos de dados que este tutorial usa são de “From Group to Individual Labels using Deep Features”, Kotzias et.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-180">The datasets this tutorial uses are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="0f5e0-181">al,.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-181">al,.</span></span> <span data-ttu-id="0f5e0-182">KDD 2015, e hospedados no UCI Machine Learning Repository – Dua, D. e Karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="0f5e0-182">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="0f5e0-183">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span><span class="sxs-lookup"><span data-stu-id="0f5e0-183">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="0f5e0-184">Irvine, CA: University of California, School of Information and Computer Science.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-184">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

3. <span data-ttu-id="0f5e0-185">No Gerenciador de Soluções, clique com o botão direito do mouse no arquivo `yelp_labeled.txt` e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-185">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="0f5e0-186">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-186">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="0f5e0-187">Criar classes e definir demarcadores</span><span class="sxs-lookup"><span data-stu-id="0f5e0-187">Create classes and define paths</span></span>

<span data-ttu-id="0f5e0-188">Adicione as seguintes instruções `using` adicionais ao início do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-188">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

<span data-ttu-id="0f5e0-189">Você precisa criar dois campos globais para armazenar o caminho do arquivo de conjunto de dados baixado recentemente e o caminho do arquivo de modelo salvo:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-189">You need to create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

* <span data-ttu-id="0f5e0-190">`_dataPath` tem o demarcador para o conjunto de dados usado para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-190">`_dataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="0f5e0-191">`_modelPath` tem o demarcador em que o modelo treinado é salvo.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-191">`_modelPath` has the path where the trained model is saved.</span></span>

<span data-ttu-id="0f5e0-192">Adicione o seguinte código à linha logo acima do método `Main` para especificar estes caminhos:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-192">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

<span data-ttu-id="0f5e0-193">Você precisa criar algumas classes para os dados e previsões de entrada.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-193">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="0f5e0-194">Adicione uma nova classe ao seu projeto:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-194">Add a new class to your project:</span></span>

1. <span data-ttu-id="0f5e0-195">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-195">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="0f5e0-196">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-196">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="0f5e0-197">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-197">Then, select the **Add** button.</span></span>

    <span data-ttu-id="0f5e0-198">O arquivo *SentimentData.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-198">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="0f5e0-199">Adicione a seguinte instrução `using` acima de *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-199">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

<span data-ttu-id="0f5e0-200">Remova a definição de classe existente e adicione o seguinte código, que possui duas classes `SentimentData` e `SentimentPrediction`, ao arquivo *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-200">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

[!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

<span data-ttu-id="0f5e0-201">A classe do conjunto de dados de entrada, `SentimentData`, tem um `string` para o comentário (`SentimentText`) e um `bool` (`Sentiment`) que tem um valor para sentimento positivo ou negativo.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-201">The input dataset class, `SentimentData`, has a `string` for the comment (`SentimentText`) and a `bool` (`Sentiment`) that has a value for sentiment of either positive or negative.</span></span> <span data-ttu-id="0f5e0-202">Ambos os campos têm atributos <xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29> anexados a eles.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-202">Both fields have <xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29> attributes attached to them.</span></span> <span data-ttu-id="0f5e0-203">Este atributo descreve a ordem de cada campo no arquivo de dados.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-203">This attribute describes the order of each field in the data file.</span></span>  <span data-ttu-id="0f5e0-204">Além disso, a propriedade `Sentiment` tem um <xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A> para designá-la como o campo `Label`.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-204">In addition, the `Sentiment` property has a <xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A> to designate it as the `Label` field.</span></span> <span data-ttu-id="0f5e0-205">`SentimentPrediction` é a classe usada para previsão depois que o modelo foi treinado.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-205">`SentimentPrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="0f5e0-206">Tem um único booliano (`Sentiment`) e um atributo `PredictedLabel` `ColumnName`.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-206">It has a single boolean (`Sentiment`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="0f5e0-207">O `Label` é usado para criar e treinar o modelo, além de ser usado com o conjunto de dados de teste para avaliar o modelo.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-207">The `Label` is used to create and train the model, and it's also used with the split out test dataset to evaluate the model.</span></span> <span data-ttu-id="0f5e0-208">O `PredictedLabel` é usado durante a previsão e avaliação.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-208">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="0f5e0-209">Para avaliação, uma entrada com dados de treinamento, os valores previstos e o modelo são usados.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-209">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="0f5e0-210">Ao criar um modelo com o ML.NET, comece criando um <xref:Microsoft.ML.MLContext>.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-210">When building a model with ML.NET you start by creating an <xref:Microsoft.ML.MLContext>.</span></span> <span data-ttu-id="0f5e0-211">`MLContext` é conceitualmente comparável ao uso de `DbContext` no Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-211">`MLContext` is comparable conceptually to using `DbContext` in Entity Framework.</span></span> <span data-ttu-id="0f5e0-212">O ambiente fornece um contexto para seu trabalho de ML que pode ser usado no acompanhamento e registro em log da exceção.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-212">The environment provides a context for your ML job that can be used for exception tracking and logging.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="0f5e0-213">Inicializar variáveis em Main</span><span class="sxs-lookup"><span data-stu-id="0f5e0-213">Initialize variables in Main</span></span>

<span data-ttu-id="0f5e0-214">Crie uma variável chamada `mlContext` e inicialize-a com uma nova instância de `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-214">Create a variable called `mlContext` and initialize it with a new instance of `MLContext`.</span></span>  <span data-ttu-id="0f5e0-215">Substitua a linha `Console.WriteLine("Hello World!")` pelo seguinte código no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-215">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

<span data-ttu-id="0f5e0-216">Adicione o seguinte como a linha seguinte de código no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-216">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallLoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

<span data-ttu-id="0f5e0-217">O método `LoadData` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-217">The `LoadData` method executes the following tasks:</span></span>

* <span data-ttu-id="0f5e0-218">Carrega os dados.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-218">Loads the data.</span></span>
* <span data-ttu-id="0f5e0-219">Divide o conjunto de dados carregado em conjuntos de treinamento e teste.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-219">Splits the loaded dataset into train and test datasets.</span></span>
* <span data-ttu-id="0f5e0-220">Retorna os conjuntos de treinamento e teste.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-220">Returns the split train and test datasets.</span></span>

<span data-ttu-id="0f5e0-221">Crie o método `LoadData`, logo após o método `Main`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-221">Create the `LoadData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static TrainCatalogBase.TrainTestData LoadData(MLContext mlContext)
{

}
```

## <a name="load-the-data"></a><span data-ttu-id="0f5e0-222">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="0f5e0-222">Load the data</span></span>

<span data-ttu-id="0f5e0-223">Já que o tipo do modelo de dados `SentimentData` criado anteriormente corresponde ao esquema de conjunto de dados, é possível combinar a inicialização, o mapeamento e o carregamento de conjunto de dados em uma única linha de código, usando o wrapper `MLContext.Data.LoadFromTextFile` para o [método LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29).</span><span class="sxs-lookup"><span data-stu-id="0f5e0-223">Since your previously created `SentimentData` data model type matches the dataset schema, you can combine the initialization, mapping, and dataset loading into one line of code using the `MLContext.Data.LoadFromTextFile` wrapper for the [LoadFromTextFile method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29).</span></span> <span data-ttu-id="0f5e0-224">Ele retorna um <xref:Microsoft.Data.DataView.IDataView>.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-224">It returns a <xref:Microsoft.Data.DataView.IDataView>.</span></span>

<span data-ttu-id="0f5e0-225">Como a entrada e saída de `Transforms`, um `DataView` é o tipo de pipeline de dados fundamental, comparável ao `IEnumerable` para `LINQ`.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-225">As the input and output of `Transforms`, a `DataView` is the fundamental data pipeline type, comparable to `IEnumerable` for `LINQ`.</span></span>

<span data-ttu-id="0f5e0-226">No ML.NET, os dados são semelhantes a um modo de exibição SQL.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-226">In ML.NET, data is similar to a SQL view.</span></span> <span data-ttu-id="0f5e0-227">Eles são heterogêneos e avaliados e esquematizados lentamente.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-227">It is lazily evaluated, schematized, and heterogenous.</span></span> <span data-ttu-id="0f5e0-228">O objeto é a primeira parte do pipeline e carrega os dados.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-228">The object is the first part of the pipeline, and loads the data.</span></span> <span data-ttu-id="0f5e0-229">Neste tutorial, ele carrega um conjunto de dados com comentários e o sentimento tóxico ou não tóxico correspondente.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-229">For this tutorial, it loads a dataset with comments and corresponding toxic or non toxic sentiment.</span></span> <span data-ttu-id="0f5e0-230">Isso é usado para criar o modelo e treiná-lo.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-230">This is used to create the model, and train it.</span></span>

<span data-ttu-id="0f5e0-231">Adicione o seguinte código como a primeira linha do método `LoadData`:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-231">Add the following code as the first line of the `LoadData` method:</span></span>

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="0f5e0-232">Dividir o conjunto de dados para o modelo de treinamento e de teste</span><span class="sxs-lookup"><span data-stu-id="0f5e0-232">Split the dataset for model training and testing</span></span>

<span data-ttu-id="0f5e0-233">Em seguida, você precisa de um conjunto de dados de treinamento para treinar o modelo e um conjunto de dados de teste para avaliar o modelo.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-233">Next, you need both a training dataset to train the model and a test dataset to evaluate the model.</span></span> <span data-ttu-id="0f5e0-234">Use o `MLContext.BinaryClassification.TrainTestSplit` que encapsula <xref:Microsoft.ML.StaticPipe.TrainingStaticExtensions.TrainTestSplit%2A> para dividir o conjunto de dados carregado em conjuntos de dados de treinamento e de teste e retorná-los dentro de um <xref:Microsoft.ML.TrainCatalogBase.TrainTestData>.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-234">Use the `MLContext.BinaryClassification.TrainTestSplit` which wraps <xref:Microsoft.ML.StaticPipe.TrainingStaticExtensions.TrainTestSplit%2A> to split the loaded dataset into train and test datasets and return them inside of a <xref:Microsoft.ML.TrainCatalogBase.TrainTestData>.</span></span> <span data-ttu-id="0f5e0-235">Você pode especificar a fração de dados para o conjunto de teste com o parâmetro `testFraction`.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-235">You can specify the fraction of data for the test set with the `testFraction`parameter.</span></span> <span data-ttu-id="0f5e0-236">O padrão é 10%, mas use 20% nesse caso, a fim de usar mais dados para a avaliação.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-236">The default is 10% but you use 20% in this case to use more data for the evaluation.</span></span>

<span data-ttu-id="0f5e0-237">Para dividir os dados carregados nos conjuntos de dados necessários, adicione o seguinte código como a próxima linha no método `LoadData`:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-237">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData` method:</span></span>

[!code-csharp[SplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

<span data-ttu-id="0f5e0-238">Retorne o `splitDataView` no final do método `LoadData`:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-238">Return the `splitDataView` at the end of the `LoadData` method:</span></span>

[!code-csharp[ReturnSplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="0f5e0-239">Criar e treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="0f5e0-239">Build and train the model</span></span>

<span data-ttu-id="0f5e0-240">Adicione a seguinte chamada ao método `BuildAndTrainModel` como a próxima linha de código no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-240">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="0f5e0-241">O método `BuildAndTrainModel` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-241">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="0f5e0-242">Extrai e transforma os dados.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-242">Extracts and transforms the data.</span></span>
* <span data-ttu-id="0f5e0-243">Treina o modelo.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-243">Trains the model.</span></span>
* <span data-ttu-id="0f5e0-244">Prevê o sentimento com base nos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-244">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="0f5e0-245">Retorna o modelo.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-245">Returns the model.</span></span>

<span data-ttu-id="0f5e0-246">Crie o método `BuildAndTrainModel`, logo após o método `Main`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-246">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
{

}
```

<span data-ttu-id="0f5e0-247">Observe que dois parâmetros são passados para o método Train. Um `MLContext` para o contexto (`mlContext`) e um `IDataView` para o conjunto de dados de treinamento (`splitTrainSet`).</span><span class="sxs-lookup"><span data-stu-id="0f5e0-247">Notice that two parameters are passed into the Train method; a `MLContext` for the context (`mlContext`), and an `IDataView`for the training dataset (`splitTrainSet`).</span></span>

## <a name="extract-and-transform-the-data"></a><span data-ttu-id="0f5e0-248">Extrair e transformar os dados</span><span class="sxs-lookup"><span data-stu-id="0f5e0-248">Extract and transform the data</span></span>

<span data-ttu-id="0f5e0-249">O pré-processamento e a limpeza de dados são tarefas importantes que ocorrem antes de um conjunto de dados ser usado efetivamente para o aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-249">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="0f5e0-250">Os dados brutos costumam ser ruidosos e pouco confiáveis, e podem apresentar valores faltantes.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-250">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="0f5e0-251">Usar dados sem essas tarefas de modelagem pode produzir resultados enganosos.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-251">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="0f5e0-252">Os pipelines de transformação do ML.NET compõem um conjunto personalizado de transformações que são aplicadas aos seus dados antes do treinamento ou teste.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-252">ML.NET's transform pipelines compose a custom set of transforms that are applied to your data before training or testing.</span></span> <span data-ttu-id="0f5e0-253">A principal finalidade das transformações é a [personalização](../resources/glossary.md#feature-engineering) de dados.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-253">The transforms' primary purpose is data [featurization](../resources/glossary.md#feature-engineering).</span></span> <span data-ttu-id="0f5e0-254">Os algoritmos de aprendizado de máquina entendem os [dados personalizados](../resources/glossary.md#feature), portanto, a próximo etapa é transformar nossos dados textuais em um formato que nossos algoritmos de aprendizado de máquina reconheçam.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-254">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, so the next step is to transform our textual data into a format that our ML algorithms recognize.</span></span> <span data-ttu-id="0f5e0-255">Esse formato é um [vetor numérico](../resources/glossary.md#numerical-feature-vector).</span><span class="sxs-lookup"><span data-stu-id="0f5e0-255">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="0f5e0-256">Em seguida, chame `mlContext.Transforms.Text.FeaturizeText` que personaliza a coluna de texto (`SentimentText`) em um vetor numérico chamado `Features`, usado pelo algoritmo de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-256">Next, call `mlContext.Transforms.Text.FeaturizeText` which featurizes the text column (`SentimentText`) column into a numeric vector called `Features` used by the machine learning algorithm.</span></span> <span data-ttu-id="0f5e0-257">Essa é uma chamada de wrapper que retorna um <xref:Microsoft.ML.Data.EstimatorChain%601> que será efetivamente um pipeline.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-257">This is a wrapper call that returns an <xref:Microsoft.ML.Data.EstimatorChain%601> that will effectively be a pipeline.</span></span> <span data-ttu-id="0f5e0-258">Dê ao `pipeline` um nome de sua preferência e, em seguida, anexe o instrutor à `EstimatorChain`.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-258">Name this `pipeline` as you will then append the trainer to the `EstimatorChain`.</span></span> <span data-ttu-id="0f5e0-259">Adicione isso como a linha seguinte de código:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-259">Add this as the next line of code:</span></span>

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

>[!WARNING]
> <span data-ttu-id="0f5e0-260">O ML.NET versão 0.10 alterou a ordem dos parâmetros de transformação.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-260">ML.NET Version 0.10 changed the order of the Transform parameters.</span></span> <span data-ttu-id="0f5e0-261">Isso não apresentará um erro até que você execute o aplicativo e compile o modelo.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-261">This will not error out until you run the application and build the model.</span></span> <span data-ttu-id="0f5e0-262">Use os nomes de parâmetro para transformações, conforme ilustrado no snippet de código anterior.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-262">Use the parameter names for Transforms as illustrated in the previous code snippet.</span></span>

<span data-ttu-id="0f5e0-263">Esta é a etapa de pré-processamento/personalização.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-263">This is the preprocessing/featurization step.</span></span> <span data-ttu-id="0f5e0-264">Usar componentes adicionais disponíveis no ML.NET pode permitir melhores resultados com o seu modelo.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-264">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="0f5e0-265">Escolher um algoritmo de aprendizado</span><span class="sxs-lookup"><span data-stu-id="0f5e0-265">Choose a learning algorithm</span></span>

<span data-ttu-id="0f5e0-266">Para adicionar o instrutor, chame o método `mlContext.BinaryClassification.Trainers.FastTree` do wrapper que retorna um objeto <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer>.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-266">To add the trainer, call the `mlContext.BinaryClassification.Trainers.FastTree` wrapper method which returns a <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> object.</span></span> <span data-ttu-id="0f5e0-267">Esse é um aprendiz de árvore de decisão que você usará neste pipeline.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-267">This is a decision tree learner you'll use in this pipeline.</span></span> <span data-ttu-id="0f5e0-268">O `FastTreeBinaryClassificationTrainer` é anexado ao `pipeline` e aceita o parâmetro `SentimentText` (`Features`) personalizado e o parâmetro `Label` de entrada para aprender com os dados históricos.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-268">The `FastTreeBinaryClassificationTrainer` is appended to the `pipeline` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

<span data-ttu-id="0f5e0-269">Adicione o seguinte código ao método `BuildAndTrainModel`:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-269">Add the following code to the `BuildAndTrainModel` method:</span></span>

[!code-csharp[FastTreeBinaryClassificationTrainer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a FastTreeBinaryClassificationTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="0f5e0-270">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="0f5e0-270">Train the model</span></span>

<span data-ttu-id="0f5e0-271">Você treina o modelo, <xref:Microsoft.ML.Data.TransformerChain%601>, com base no conjunto de dados que foi carregado e transformado.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-271">You train the model, <xref:Microsoft.ML.Data.TransformerChain%601>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="0f5e0-272">Depois que o avaliador tiver sido definido, treine o modelo usando o método <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> e forneça os dados de treinamento já carregados.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-272">Once the estimator has been defined, you train your model using the <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> method while providing the already loaded training data.</span></span> <span data-ttu-id="0f5e0-273">Isso retornará um modelo que será usado nas previsões.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-273">This returns a model to use for predictions.</span></span> <span data-ttu-id="0f5e0-274">`pipeline.Fit()` treina o pipeline e retorna um `Transformer` com base no `DataView` passado.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-274">`pipeline.Fit()` trains the pipeline and returns a `Transformer` based on the `DataView` passed in.</span></span> <span data-ttu-id="0f5e0-275">O teste não é executado até que o método `.Fit()` seja executado.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-275">The experiment is not executed until the `.Fit()` method runs.</span></span>

<span data-ttu-id="0f5e0-276">Adicione o seguinte código ao método `BuildAndTrainModel`:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-276">Add the following code to the `BuildAndTrainModel` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="0f5e0-277">Salvar e retornar o modelo treinado para usar na avaliação</span><span class="sxs-lookup"><span data-stu-id="0f5e0-277">Save and Return the model trained to use for evaluation</span></span>

<span data-ttu-id="0f5e0-278">Neste ponto, você tem um modelo de tipo <xref:Microsoft.ML.Data.TransformerChain%601> que pode ser integrado em qualquer um dos seus aplicativos .NET existentes ou novos.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-278">At this point, you have a model of type <xref:Microsoft.ML.Data.TransformerChain%601> that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="0f5e0-279">Retorne o modelo no final do método `BuildAndTrainModel`.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-279">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="0f5e0-280">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="0f5e0-280">Evaluate the model</span></span>

<span data-ttu-id="0f5e0-281">Agora que você criou e treinou o modelo, precisa avaliá-lo com um conjunto de dados diferente para garantia de qualidade e validação.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-281">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="0f5e0-282">No método `Evaluate`, o modelo criado em `BuildAndTrainModel` é passado para ser avaliado.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-282">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="0f5e0-283">Crie o método `Evaluate` , logo após `BuildAndTrainModel`, como no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-283">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
{

}
```

<span data-ttu-id="0f5e0-284">O método `Evaluate` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-284">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="0f5e0-285">Carrega o conjunto de dados de teste.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-285">Loads the test dataset.</span></span>
* <span data-ttu-id="0f5e0-286">Cria o avaliador de classificação binária.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-286">Creates the binaryclassification evaluator.</span></span>
* <span data-ttu-id="0f5e0-287">Avalia o modelo e cria métricas.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-287">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="0f5e0-288">Exibe as métricas.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-288">Displays the metrics.</span></span>

<span data-ttu-id="0f5e0-289">Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `Train`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-289">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

<span data-ttu-id="0f5e0-290">Em seguida, você usará o parâmetro `model` de aprendizado de máquina (um transformador) e o parâmetro `splitTestSet` para inserir os recursos e retornar previsões.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-290">Next, you'll use the machine learning `model` parameter (a transformer) and the `splitTestSet` parameter to input the features and return predictions.</span></span> <span data-ttu-id="0f5e0-291">Adicione o seguinte código ao método `Evaluate` como a linha seguinte:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-291">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

<span data-ttu-id="0f5e0-292">O método `mlContext.BinaryClassification.Evaluate` calcula as métricas de qualidade para o `PredictionModel` usando o conjunto de dados especificado.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-292">The `mlContext.BinaryClassification.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="0f5e0-293">Ele retorna um objeto <xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics> que contém as métricas gerais calculadas pelos avaliadores de classificação binária.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-293">It returns a <xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics> object that contains the overall metrics computed by binary classification evaluators.</span></span> <span data-ttu-id="0f5e0-294">Para exibi-los a fim de determinar a qualidade do modelo, é preciso primeiro obter as métricas.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-294">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="0f5e0-295">Adicione o seguinte código ao método `Evaluate` como a linha seguinte:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-295">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="0f5e0-296">Exibir as métricas para validação de modelo</span><span class="sxs-lookup"><span data-stu-id="0f5e0-296">Displaying the metrics for model validation</span></span>

<span data-ttu-id="0f5e0-297">Use o código a seguir para exibir as métricas, compartilhar os resultados e, em seguida, agir com relação a eles:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-297">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

<span data-ttu-id="0f5e0-298">Para salvar seu modelo como um arquivo .zip antes de retornar, adicione o seguinte código para chamar o método `SaveModelAsFile` como a linha seguinte em `Evaluate`:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-298">To save your model to a .zip file before returning, add the following code to call the `SaveModelAsFile` method as the next line in `Evaluate`:</span></span>

[!code-csharp[SaveModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallSaveModel "Save the model")]

## <a name="save-the-model-as-azip-file"></a><span data-ttu-id="0f5e0-299">Salvar o modelo como um arquivo .zip</span><span class="sxs-lookup"><span data-stu-id="0f5e0-299">Save the model as a.zip file</span></span>

<span data-ttu-id="0f5e0-300">Crie o método `SaveModelAsFile`, logo após o método `Evaluate`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-300">Create the `SaveModelAsFile` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="0f5e0-301">O método `SaveModelAsFile` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-301">The `SaveModelAsFile` method executes the following tasks:</span></span>

* <span data-ttu-id="0f5e0-302">Salva o modelo como um arquivo .zip.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-302">Saves the model as a .zip file.</span></span>

<span data-ttu-id="0f5e0-303">Em seguida, crie um método para salvar o modelo para que ele possa ser reutilizado e consumido em outros aplicativos.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-303">Next, create a method to save the model so that it can be reused and consumed in other applications.</span></span> <span data-ttu-id="0f5e0-304">O `ITransformer` tem um método <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> que usa o campo global `_modelPath` e um <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-304">The `ITransformer` has a <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> method that takes in the `_modelPath` global field, and a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="0f5e0-305">Para salvá-lo como um arquivo zip, você criará o `FileStream` imediatamente antes de chamar o método `SaveTo`.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-305">To save this as a zip file, you'll create the `FileStream` immediately before calling the `SaveTo` method.</span></span> <span data-ttu-id="0f5e0-306">Adicione o seguinte código ao método `SaveModelAsFile` como a linha seguinte:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-306">Add the following code to the `SaveModelAsFile` method as the next line:</span></span>

[!code-csharp[SaveToMethod](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SaveModel "Add the SaveTo Method")]

<span data-ttu-id="0f5e0-307">Você também pode exibir onde o arquivo foi gravado ao gravar uma mensagem de console com o `_modelPath`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-307">You could also display where the file was written by writing a console message with the `_modelPath`, using the following code:</span></span>

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="predict-the-test-data-outcome-with-the-saved-model"></a><span data-ttu-id="0f5e0-308">Prever o resultado dos dados de teste com o modelo salvo</span><span class="sxs-lookup"><span data-stu-id="0f5e0-308">Predict the test data outcome with the saved model</span></span>

<span data-ttu-id="0f5e0-309">Crie o método `UseModelWithSingleItem`, logo após o método `Evaluate`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-309">Create the `UseModelWithSingleItem` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="0f5e0-310">O método `UseModelWithSingleItem` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-310">The `UseModelWithSingleItem` method executes the following tasks:</span></span>

* <span data-ttu-id="0f5e0-311">Cria um único comentário dos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-311">Creates a single comment of test data.</span></span>
* <span data-ttu-id="0f5e0-312">Prevê o sentimento com base nos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-312">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="0f5e0-313">Combina dados de teste e previsões para relatórios.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-313">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="0f5e0-314">Exibe os resultados previstos.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-314">Displays the predicted results.</span></span>

<span data-ttu-id="0f5e0-315">Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `Evaluate`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-315">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallUseModelWithSingleItem](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

<span data-ttu-id="0f5e0-316">Enquanto o `model` é um `transformer` que opera em muitas linhas de dados, um cenário de produção muito comum é a necessidade de previsões em exemplos individuais.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-316">While the `model` is a `transformer` that operates on many rows of data, a very common production scenario is a need for predictions on individual examples.</span></span> <span data-ttu-id="0f5e0-317">O <xref:Microsoft.ML.PredictionEngine%602> é um wrapper que é retornado do método `CreatePredictionEngine`.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-317">The <xref:Microsoft.ML.PredictionEngine%602> is a wrapper that is returned from the `CreatePredictionEngine` method.</span></span> <span data-ttu-id="0f5e0-318">Vamos adicionar o seguinte código para criar `PredictionEngine` como a primeira linha no método `Predict`:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-318">Let's add the following code to create the `PredictionEngine` as the first line in the `Predict` Method:</span></span>

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

<span data-ttu-id="0f5e0-319">Adicione um comentário para testar as previsões do modelo treinado no método `Predict` ao criar uma instância de `SentimentData`:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-319">Add a comment to test the trained model's prediction in the `Predict` method by creating an instance of `SentimentData`:</span></span>

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

 <span data-ttu-id="0f5e0-320">Você pode usar isso para prever o sentimento positivo ou negativo de uma única instância dos dados de comentário.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-320">You can use that to predict the positive or negative sentiment of a single instance of the comment data.</span></span> <span data-ttu-id="0f5e0-321">Para obter uma previsão, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> nos dados.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-321">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="0f5e0-322">Observe que os dados de entrada são uma cadeia de caracteres e o modelo inclui a personalização.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-322">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="0f5e0-323">Seu pipeline está em sincronia durante o treinamento e a previsão.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-323">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="0f5e0-324">Você não precisou escrever código de pré-processamento/personalização especificamente para previsões, e a mesma API cuida das previsões de lote e de uso único.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-324">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

### <a name="use-the-model-prediction"></a><span data-ttu-id="0f5e0-325">Usar o modelo: previsão</span><span class="sxs-lookup"><span data-stu-id="0f5e0-325">Use the model: prediction</span></span>

<span data-ttu-id="0f5e0-326">Exiba `SentimentText` e a previsão de sentimento correspondente para compartilhar os resultados e agir de acordo com eles.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-326">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="0f5e0-327">Isso é chamado de operacionalização, usar os dados retornados como parte das políticas operacionais.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-327">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="0f5e0-328">Crie uma exibição para os resultados usando o seguinte código <xref:System.Console.WriteLine?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-328">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="deploy-and-predict-with-a-loaded-model"></a><span data-ttu-id="0f5e0-329">Implantar e prever com um modelo carregado</span><span class="sxs-lookup"><span data-stu-id="0f5e0-329">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="0f5e0-330">Crie o método `UseLoadedModelWithBatchItems`, logo antes do método `SaveModelAsFile`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-330">Create the `UseLoadedModelWithBatchItems` method, just before the `SaveModelAsFile` method, using the following code:</span></span>

```csharp
public static void UseLoadedModelWithBatchItems(MLContext mlContext)
{

}
```

<span data-ttu-id="0f5e0-331">O método `UseLoadedModelWithBatchItems` executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-331">The `UseLoadedModelWithBatchItems` method executes the following tasks:</span></span>

* <span data-ttu-id="0f5e0-332">Cria dados de teste em lote.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-332">Creates batch test data.</span></span>
* <span data-ttu-id="0f5e0-333">Prevê o sentimento com base nos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-333">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="0f5e0-334">Combina dados de teste e previsões para relatórios.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-334">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="0f5e0-335">Exibe os resultados previstos.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-335">Displays the predicted results.</span></span>

<span data-ttu-id="0f5e0-336">Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `UseModelWithSingleItem`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-336">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem` method call, using the following code:</span></span>

[!code-csharp[CallPredictModelLoaded](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseLoadedModelWithBatchItems "Call the CallUseLoadedModelWithBatchItems method")]

<span data-ttu-id="0f5e0-337">Adicione alguns comentários para testar as previsões do modelo treinado no método `UseLoadedModelWithBatchItems`:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-337">Add some comments to test the trained model's predictions in the `UseLoadedModelWithBatchItems` method:</span></span>

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

<span data-ttu-id="0f5e0-338">Carregar o modelo</span><span class="sxs-lookup"><span data-stu-id="0f5e0-338">Load the model</span></span>

[!code-csharp[LoadTheModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadModel "Load the model")]

<span data-ttu-id="0f5e0-339">Agora que você tem um modelo, pode usá-lo para prever o sentimento tóxico ou não tóxico dos dados do comentário usando o método <xref:Microsoft.ML.ITransformer.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-339">Now that you have a model, you can use that to predict the Toxic or Non Toxic sentiment of the comment data using the <xref:Microsoft.ML.ITransformer.Transform%2A> method.</span></span> <span data-ttu-id="0f5e0-340">Para obter uma previsão, use `Predict` em novos dados.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-340">To get a prediction, use `Predict` on new data.</span></span> <span data-ttu-id="0f5e0-341">Observe que os dados de entrada são uma cadeia de caracteres e o modelo inclui a personalização.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-341">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="0f5e0-342">Seu pipeline está em sincronia durante o treinamento e a previsão.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-342">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="0f5e0-343">Você não precisou escrever código de pré-processamento/personalização especificamente para previsões, e a mesma API cuida das previsões de lote e de uso único.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-343">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span> <span data-ttu-id="0f5e0-344">Adicione o código a seguir ao método `UseLoadedModelWithBatchItems` para as previsões:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-344">Add the following code to the `UseLoadedModelWithBatchItems` method for the predictions:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="use-the-loaded-model-for-prediction"></a><span data-ttu-id="0f5e0-345">Usar o modelo carregado para previsão</span><span class="sxs-lookup"><span data-stu-id="0f5e0-345">Use the loaded model for prediction</span></span>

<span data-ttu-id="0f5e0-346">Exiba `SentimentText` e a previsão de sentimento correspondente para compartilhar os resultados e agir de acordo com eles.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-346">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="0f5e0-347">Isso é chamado de operacionalização, usar os dados retornados como parte das políticas operacionais.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-347">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="0f5e0-348">Crie um cabeçalho para os resultados usando o seguinte código <xref:System.Console.WriteLine?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-348">Create a header for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputHeaders](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="0f5e0-349">Antes de exibir os resultados previstos, combine o sentimento e a previsão juntos para ver o comentário original com o sentimento previsto.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-349">Before displaying the predicted results, combine the sentiment and prediction together to see the original comment with its predicted sentiment.</span></span> <span data-ttu-id="0f5e0-350">O código a seguir usa o método <xref:System.Linq.Enumerable.Zip%2A> para que isso aconteça, então adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-350">The following code uses the <xref:System.Linq.Enumerable.Zip%2A> method to make that happen, so add that code next:</span></span>

[!code-csharp[BuildTuples](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#BuildSentimentPredictionPairs "Build the pairs of sentiment data and predictions")]

<span data-ttu-id="0f5e0-351">Agora que você combinou `SentimentText` e `Sentiment` em uma classe, você pode exibir os resultados usando o método <xref:System.Console.WriteLine?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-351">Now that you've combined the `SentimentText` and `Sentiment` into a class, you can display the results using the <xref:System.Console.WriteLine?displayProperty=nameWithType> method:</span></span>

[!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

<span data-ttu-id="0f5e0-352">Como nomes de elementos de tuplas inferidos são um novo recurso no C# 7.1 e a versão da linguagem padrão do projeto é C# 7.0, é necessário alterar a versão da linguagem para C# 7.1 ou superior.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-352">Because inferred tuple element names are a new feature in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span>
<span data-ttu-id="0f5e0-353">Para fazer isso, clique com o botão direito do mouse no nó do projeto no **Gerenciador de Soluções** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-353">To do that, right-click on the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="0f5e0-354">Selecione a guia **Build** e o botão **Avançado**.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-354">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="0f5e0-355">No menu suspenso, selecione **C# 7.1** (ou uma versão posterior).</span><span class="sxs-lookup"><span data-stu-id="0f5e0-355">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="0f5e0-356">Selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-356">Select the **OK** button.</span></span>

## <a name="results"></a><span data-ttu-id="0f5e0-357">Resultados</span><span class="sxs-lookup"><span data-stu-id="0f5e0-357">Results</span></span>

<span data-ttu-id="0f5e0-358">Seus resultados devem ser semelhantes aos seguintes.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-358">Your results should be similar to the following.</span></span> <span data-ttu-id="0f5e0-359">Conforme o pipeline processa, exibe mensagens.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-359">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="0f5e0-360">Você pode ver avisos ou mensagens de processamento.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-360">You may see warnings, or processing messages.</span></span> <span data-ttu-id="0f5e0-361">Eles foram removidos dos seguintes resultados para maior clareza.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-361">These have been removed from the following results for clarity.</span></span>

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 79.14%
Auc: 86.27%
F1Score: 80.60%

=============== End of model evaluation ===============
The model is saved to C:\Tutorials\SentimentAnalysis\bin\Debug\netcoreapp2.1\Data\Model.zip

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This was a very bad steak | Prediction: Negative | Probability: 0.4641322
=============== End of Predictions ===============


=============== Prediction Test of loaded model with a multiple samples ===============

Sentiment: This was a horrible meal | Prediction: Negative | Probability: 0.1391833
Sentiment: I love this spaghetti. | Prediction: Positive | Probability: 0.9819039
=============== End of predictions ===============

=============== End of process ===============
Press any key to continue . . .

```

<span data-ttu-id="0f5e0-362">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="0f5e0-362">Congratulations!</span></span> <span data-ttu-id="0f5e0-363">Agora você criou com sucesso um modelo de aprendizado de máquina para classificar e prever o sentimento das mensagens.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-363">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span>

<span data-ttu-id="0f5e0-364">A criação de modelos bem-sucedidos é um processo iterativo.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-364">Building successful models is an iterative process.</span></span> <span data-ttu-id="0f5e0-365">Esse modelo tem qualidade inicial inferior, pois o tutorial usa conjuntos de dados pequenos para fornecer um treinamento rápido do modelo.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-365">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="0f5e0-366">Se você não estiver satisfeito com a qualidade do modelo, tente melhorá-lo fornecendo conjuntos de dados de treinamento maiores ou escolhendo diferentes algoritmos de treinamento com diferentes hiperparâmetros para cada algoritmo.</span><span class="sxs-lookup"><span data-stu-id="0f5e0-366">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different hyper-parameters for each algorithm.</span></span>

<span data-ttu-id="0f5e0-367">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis).</span><span class="sxs-lookup"><span data-stu-id="0f5e0-367">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0f5e0-368">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="0f5e0-368">Next steps</span></span>

<span data-ttu-id="0f5e0-369">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="0f5e0-369">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="0f5e0-370">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="0f5e0-370">Understand the problem</span></span>
> * <span data-ttu-id="0f5e0-371">Selecionar o algoritmo de aprendizado de máquina apropriado</span><span class="sxs-lookup"><span data-stu-id="0f5e0-371">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="0f5e0-372">Preparar seus dados</span><span class="sxs-lookup"><span data-stu-id="0f5e0-372">Prepare your data</span></span>
> * <span data-ttu-id="0f5e0-373">Transformar os dados</span><span class="sxs-lookup"><span data-stu-id="0f5e0-373">Transform the data</span></span>
> * <span data-ttu-id="0f5e0-374">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="0f5e0-374">Train the model</span></span>
> * <span data-ttu-id="0f5e0-375">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="0f5e0-375">Evaluate the model</span></span>
> * <span data-ttu-id="0f5e0-376">Prever com o modelo treinado</span><span class="sxs-lookup"><span data-stu-id="0f5e0-376">Predict with the trained model</span></span>
> * <span data-ttu-id="0f5e0-377">Implantar e prever com um modelo carregado</span><span class="sxs-lookup"><span data-stu-id="0f5e0-377">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="0f5e0-378">Avançar para o próximo tutorial para saber mais</span><span class="sxs-lookup"><span data-stu-id="0f5e0-378">Advance to the next tutorial to learn more</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0f5e0-379">Classificação de problema</span><span class="sxs-lookup"><span data-stu-id="0f5e0-379">Issue Classification</span></span>](github-issue-classification.md)
