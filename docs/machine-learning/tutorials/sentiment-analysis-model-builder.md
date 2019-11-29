---
title: 'Tutorial: analisar sentimentos – classificação binária'
description: Este tutorial mostra como criar um aplicativo Razor Pages que classifica as opiniões dos comentários do site e executa a ação apropriada. O classificador de sentimentos binários usa o construtor de modelos no Visual Studio.
ms.date: 11/21/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e919341130c6778207f324dd9eb3b3f54c8a9c68
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74551841"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a><span data-ttu-id="8b3dc-104">Tutorial: analisar o sentimentos dos comentários do site em um aplicativo Web usando o ML.NET Model Builder</span><span class="sxs-lookup"><span data-stu-id="8b3dc-104">Tutorial: Analyze sentiment of website comments in a web application using ML.NET Model Builder</span></span>

<span data-ttu-id="8b3dc-105">Saiba como analisar as opiniões de comentários em tempo real dentro de um aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-105">Learn how to analyze sentiment from comments in real-time inside a web application.</span></span>

<span data-ttu-id="8b3dc-106">Este tutorial mostra como criar um aplicativo ASP.NET Core Razor Pages que classifica as opiniões dos comentários do site em tempo real.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-106">This tutorial shows you how to create an ASP.NET Core Razor Pages application that classifies sentiment from website comments in real-time.</span></span>

<span data-ttu-id="8b3dc-107">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="8b3dc-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="8b3dc-108">Criar um aplicativo de Razor Pages de ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8b3dc-108">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="8b3dc-109">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="8b3dc-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="8b3dc-110">Escolha um cenário</span><span class="sxs-lookup"><span data-stu-id="8b3dc-110">Choose a scenario</span></span>
> - <span data-ttu-id="8b3dc-111">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="8b3dc-111">Load the data</span></span>
> - <span data-ttu-id="8b3dc-112">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="8b3dc-112">Train the model</span></span>
> - <span data-ttu-id="8b3dc-113">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="8b3dc-113">Evaluate the model</span></span>
> - <span data-ttu-id="8b3dc-114">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="8b3dc-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="8b3dc-115">O Construtor de Modelo está atualmente na Versão Prévia.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-115">Model Builder is currently in Preview.</span></span>

<span data-ttu-id="8b3dc-116">Você pode encontrar o código-fonte deste tutorial no repositório [dotnet/MachineLearning-Samples](https://github.com/dotnet/machinelearning-samples) .</span><span class="sxs-lookup"><span data-stu-id="8b3dc-116">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples) repository.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="8b3dc-117">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="8b3dc-117">Pre-requisites</span></span>

<span data-ttu-id="8b3dc-118">Para obter uma lista de pré-requisitos e instruções de instalação, visite o [guia de instalação do Construtor de Modelo](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="8b3dc-118">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-razor-pages-application"></a><span data-ttu-id="8b3dc-119">Criar um aplicativo Razor Pages</span><span class="sxs-lookup"><span data-stu-id="8b3dc-119">Create a Razor Pages application</span></span>

1. <span data-ttu-id="8b3dc-120">Crie um **aplicativo de Razor pages de ASP.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-120">Create a **ASP.NET Core Razor Pages Application**.</span></span>

    1. <span data-ttu-id="8b3dc-121">Abra o Visual Studio e selecione **arquivo > novo projeto de >** na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-121">Open Visual Studio and select **File > New > Project** from the menu bar.</span></span>
    1. <span data-ttu-id="8b3dc-122">Na caixa de diálogo Novo projeto, selecione o nó **Visual C#** seguido pelo nó **Web**.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-122">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span>
    1. <span data-ttu-id="8b3dc-123">Em seguida, selecione o modelo de projeto **Aplicativo ASP.NET Core Web**.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-123">Then select the **ASP.NET Core Web Application** project template.</span></span>
    1. <span data-ttu-id="8b3dc-124">Na caixa de texto **nome** , digite "SentimentRazor".</span><span class="sxs-lookup"><span data-stu-id="8b3dc-124">In the **Name** text box, type "SentimentRazor".</span></span>
    1. <span data-ttu-id="8b3dc-125">Verifique se a opção **Colocar solução e projeto no mesmo diretório** está **desmarcada** (vs 2019) ou **criar diretório para solução** está **marcado** (vs 2017).</span><span class="sxs-lookup"><span data-stu-id="8b3dc-125">Make sure **Place solution and project in the same directory** is **unchecked** (VS 2019), or **Create directory for solution** is **checked** (VS 2017).</span></span>
    1. <span data-ttu-id="8b3dc-126">Selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-126">Select the **OK** button.</span></span>
    1. <span data-ttu-id="8b3dc-127">Escolha **aplicativo Web** na janela que exibe os diferentes tipos de projetos de ASP.NET Core e, em seguida, selecione o botão **OK** .</span><span class="sxs-lookup"><span data-stu-id="8b3dc-127">Choose **Web Application** in the window that displays the different types of ASP.NET Core Projects, and then select the **OK** button.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="8b3dc-128">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="8b3dc-128">Prepare and understand the data</span></span>

<span data-ttu-id="8b3dc-129">Baixe o [conjunto de Detox Wikipédia](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv).</span><span class="sxs-lookup"><span data-stu-id="8b3dc-129">Download [Wikipedia detox dataset](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span> <span data-ttu-id="8b3dc-130">Quando a página da Web for aberta, clique com o botão direito do mouse na página, selecione **salvar como** e salve o arquivo em qualquer lugar no computador.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-130">When the webpage opens, right-click on the page, select **Save As** and save the file anywhere on your computer.</span></span>

<span data-ttu-id="8b3dc-131">Cada linha no conjunto de *Detox da Wikipédia--line-data-250 o DataSet. tsv* representa uma revisão diferente deixada por um usuário na Wikipédia.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-131">Each row in the *wikipedia-detox-250-line-data.tsv* dataset represents a different review left by a user on Wikipedia.</span></span> <span data-ttu-id="8b3dc-132">A primeira coluna representa a folga do texto (0 é não tóxicos, 1 é tóxicos) e a segunda coluna representa o comentário deixado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-132">The first column represents the sentiment of the text (0 is non-toxic, 1 is toxic), and the second column represents the comment left by the user.</span></span> <span data-ttu-id="8b3dc-133">As colunas são separadas por tabulações.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-133">The columns are separated by tabs.</span></span> <span data-ttu-id="8b3dc-134">Os dados são parecidos com os seguintes:</span><span class="sxs-lookup"><span data-stu-id="8b3dc-134">The data looks like the following:</span></span>

| <span data-ttu-id="8b3dc-135">Sentimento</span><span class="sxs-lookup"><span data-stu-id="8b3dc-135">Sentiment</span></span> | <span data-ttu-id="8b3dc-136">SentimentText</span><span class="sxs-lookup"><span data-stu-id="8b3dc-136">SentimentText</span></span> |
| :---: | :---: |
<span data-ttu-id="8b3dc-137">1</span><span class="sxs-lookup"><span data-stu-id="8b3dc-137">1</span></span> | <span data-ttu-id="8b3dc-138">= = RUDE = = cara, você é um carregamento rude que Carl imagem de volta ou outra coisa.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-138">==RUDE== Dude, you are rude upload that carl picture back, or else.</span></span>
<span data-ttu-id="8b3dc-139">1</span><span class="sxs-lookup"><span data-stu-id="8b3dc-139">1</span></span> | <span data-ttu-id="8b3dc-140">= = OK!</span><span class="sxs-lookup"><span data-stu-id="8b3dc-140">== OK!</span></span> <span data-ttu-id="8b3dc-141">= = IM INDO PARA VANDALIZE DE CURINGAS E, EM SEGUIDA,!!!</span><span class="sxs-lookup"><span data-stu-id="8b3dc-141">==  IM GOING TO VANDALIZE WILD ONES WIKI THEN!!!</span></span>
<span data-ttu-id="8b3dc-142">0</span><span class="sxs-lookup"><span data-stu-id="8b3dc-142">0</span></span> | <span data-ttu-id="8b3dc-143">Espero que isso ajude.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-143">I hope this helps.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="8b3dc-144">Escolha um cenário</span><span class="sxs-lookup"><span data-stu-id="8b3dc-144">Choose a scenario</span></span>

![Assistente do construtor de modelos no Visual Studio](./media/sentiment-analysis-model-builder/model-builder-screen.png)

<span data-ttu-id="8b3dc-146">Para treinar seu modelo, você precisa selecionar na lista de cenários disponíveis de aprendizado de máquina fornecidos pelo Construtor de Modelo.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-146">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span>

1. <span data-ttu-id="8b3dc-147">Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto *SentimentRazor* e selecione **Adicionar** > **Machine Learning**.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-147">In **Solution Explorer**, right-click the *SentimentRazor* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="8b3dc-148">Para este exemplo, o cenário é análise de sentimentos.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-148">For this sample, the scenario is sentiment analysis.</span></span> <span data-ttu-id="8b3dc-149">Na etapa *cenário* da ferramenta Construtor de modelos, selecione o cenário de **análise de sentimento** .</span><span class="sxs-lookup"><span data-stu-id="8b3dc-149">In the *scenario* step of the Model Builder tool, select the **Sentiment Analysis** scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="8b3dc-150">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="8b3dc-150">Load the data</span></span>

<span data-ttu-id="8b3dc-151">O construtor de modelos aceita dados de duas fontes, de um SQL Server um ou de um arquivo local no formato `csv` ou `tsv`.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-151">Model Builder accepts data from two sources, a SQL Server database or a local file in `csv` or `tsv` format.</span></span>

1. <span data-ttu-id="8b3dc-152">Na etapa de dados da ferramenta do Construtor de Modelo, selecione **Arquivo** na lista suspensa da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-152">In the data step of the Model Builder tool, select **File** from the data source dropdown.</span></span>
1. <span data-ttu-id="8b3dc-153">Selecione o botão ao lado da caixa de texto **selecionar um arquivo** e use o explorador de arquivos para procurar e selecionar o arquivo *Wikipédia-Detox-250-line-Data. tsv* .</span><span class="sxs-lookup"><span data-stu-id="8b3dc-153">Select the button next to the **Select a file** text box and use File Explorer to browse and select the *wikipedia-detox-250-line-data.tsv* file.</span></span>
1. <span data-ttu-id="8b3dc-154">Escolha **sentimentos** na **coluna para prever (rótulo)** DropDown.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-154">Choose **Sentiment** in the **Column to Predict (Label)** dropdown.</span></span>
1. <span data-ttu-id="8b3dc-155">Deixe os valores padrão para a lista suspensa **colunas de entrada (recursos)** .</span><span class="sxs-lookup"><span data-stu-id="8b3dc-155">Leave the default values for the **Input Columns (Features)** dropdown.</span></span>
1. <span data-ttu-id="8b3dc-156">Selecione o link **treinar** para mover para a próxima etapa na ferramenta do construtor de modelos.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-156">Select the **Train** link to move to the next step in the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="8b3dc-157">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="8b3dc-157">Train the model</span></span>

<span data-ttu-id="8b3dc-158">A tarefa de aprendizado de máquina usada para treinar o modelo de análise de sentimentos neste tutorial é a classificação binária.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-158">The machine learning task used to train the sentiment analysis model in this tutorial is binary classification.</span></span> <span data-ttu-id="8b3dc-159">Durante o processo de treinamento do modelo, o construtor de modelos treina modelos separados usando diferentes algoritmos de classificação binária e configurações para encontrar o modelo de melhor desempenho para seu conjunto de seus conjuntos de seus.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-159">During the model training process, Model Builder trains separate models using different binary classification algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="8b3dc-160">O tempo necessário para treinar o modelo é proporcional à quantidade de dados.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-160">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="8b3dc-161">O construtor de modelos seleciona automaticamente um valor padrão para o **tempo de treinamento (segundos)** com base no tamanho da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-161">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="8b3dc-162">Embora o construtor de modelos defina o valor de **tempo para treinar (segundos)** como 10 segundos, aumente-o para 30 segundos.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-162">Although Model Builder sets the value of **Time to train (seconds)** to 10 seconds, increase it to 30 seconds.</span></span> <span data-ttu-id="8b3dc-163">O treinamento para um período de tempo maior permite que o construtor de modelos Explore um número maior de algoritmos e uma combinação de parâmetros na pesquisa do melhor modelo.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-163">Training for a longer period of time allows Model Builder to explore a larger number of algorithms and combination of parameters in search of the best model.</span></span>
1. <span data-ttu-id="8b3dc-164">Selecione **Iniciar Treinamento**.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-164">Select **Start Training**.</span></span>

    <span data-ttu-id="8b3dc-165">Durante o processo de treinamento, os dados de progresso são exibidos na seção `Progress` da etapa de treinamento.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-165">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

    - <span data-ttu-id="8b3dc-166">O status exibe o status de conclusão do processo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-166">Status displays the completion status of the training process.</span></span>
    - <span data-ttu-id="8b3dc-167">A melhor precisão exibe a precisão do modelo de melhor desempenho encontrado pelo Construtor do Modelo até o momento.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-167">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="8b3dc-168">Maior precisão significa que o modelo é previsto mais corretamente nos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-168">Higher accuracy means the model predicted more correctly on test data.</span></span>
    - <span data-ttu-id="8b3dc-169">O melhor algoritmo exibe o nome do algoritmo de melhor desempenho executado encontrado pelo Construtor de Modelo até o momento.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-169">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
    - <span data-ttu-id="8b3dc-170">O último algoritmo exibe o nome do algoritmo usado mais recentemente pelo Construtor de Modelo para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-170">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

1. <span data-ttu-id="8b3dc-171">Quando o treinamento estiver concluído, selecione o link **avaliar** para passar para a próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-171">Once training is complete, select the **evaluate** link to move to the next step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="8b3dc-172">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="8b3dc-172">Evaluate the model</span></span>

<span data-ttu-id="8b3dc-173">O resultado da etapa de treinamento será um modelo que tinha o melhor desempenho.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-173">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="8b3dc-174">Na etapa avaliar da ferramenta Construtor de modelos, a seção saída conterá o algoritmo usado pelo melhor modelo de desempenho na melhor entrada de **modelo** , juntamente com as métricas na **melhor precisão do modelo**.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-174">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the **Best Model** entry along with metrics in **Best Model Accuracy**.</span></span> <span data-ttu-id="8b3dc-175">Além disso, uma tabela de resumo contém os cinco modelos principais e suas métricas.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-175">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="8b3dc-176">Se você não estiver satisfeito com suas métricas de precisão, algumas maneiras fáceis de experimentar e aprimorar a precisão do modelo serão aumentar a quantidade de tempo para treinar o modelo ou usar mais dados.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-176">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="8b3dc-177">Caso contrário, selecione o link de **código** para mover para a etapa final na ferramenta do construtor de modelos.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-177">Otherwise, select the **code** link to move to the final step in the Model Builder tool.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="8b3dc-178">Adicionar o código para fazer previsões</span><span class="sxs-lookup"><span data-stu-id="8b3dc-178">Add the code to make predictions</span></span>

<span data-ttu-id="8b3dc-179">Dois projetos serão criados como resultado do processo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-179">Two projects will be created as a result of the training process.</span></span>

### <a name="reference-the-trained-model"></a><span data-ttu-id="8b3dc-180">Referenciar o modelo treinado</span><span class="sxs-lookup"><span data-stu-id="8b3dc-180">Reference the trained model</span></span>

1. <span data-ttu-id="8b3dc-181">Na etapa de *código* da ferramenta Construtor de modelos, selecione **adicionar projetos** para adicionar os projetos gerados automaticamente à solução.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-181">In the *code* step of the Model Builder tool, select **Add Projects** to add the autogenerated projects to the solution.</span></span>

    <span data-ttu-id="8b3dc-182">Os projetos a seguir devem aparecer no **Gerenciador de soluções**:</span><span class="sxs-lookup"><span data-stu-id="8b3dc-182">The following projects should appear in the **Solution Explorer**:</span></span>

    - <span data-ttu-id="8b3dc-183">*SentimentRazorML. ConsoleApp*: um aplicativo de console do .NET Core que contém o treinamento do modelo e o código de previsão.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-183">*SentimentRazorML.ConsoleApp*: A .NET Core Console application that contains the model training and prediction code.</span></span>
    - <span data-ttu-id="8b3dc-184">*SentimentRazorML. Model*: um .net Standard biblioteca de classes que contém os modelos de dados que definem o esquema de dados de modelo de entrada e saída, bem como a versão salva do modelo de melhor desempenho durante o treinamento.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-184">*SentimentRazorML.Model*: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the saved version of the best performing model during training.</span></span>

    <span data-ttu-id="8b3dc-185">Para este tutorial, somente o projeto *SentimentRazorML. Model* é usado porque as previsões serão feitas no aplicativo Web *SentimentRazor* , e não no console.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-185">For this tutorial, only the *SentimentRazorML.Model* project is used because predictions will be made in the *SentimentRazor* web application rather than in the console.</span></span> <span data-ttu-id="8b3dc-186">Embora o *SentimentRazorML. ConsoleApp* não seja usado para pontuação, ele pode ser usado para treinar novamente o modelo usando novos dados em um momento posterior.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-186">Although the *SentimentRazorML.ConsoleApp* won't be used for scoring, it can be used to retrain the model using new data at a later time.</span></span> <span data-ttu-id="8b3dc-187">No entanto, o novo treinamento está fora do escopo deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-187">Retraining is outside the scope of this tutorial though.</span></span>

### <a name="configure-the-predictionengine-pool"></a><span data-ttu-id="8b3dc-188">Configurar o pool PredictionEngine</span><span class="sxs-lookup"><span data-stu-id="8b3dc-188">Configure the PredictionEngine pool</span></span>

<span data-ttu-id="8b3dc-189">Para fazer uma única previsão, você precisa criar um [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="8b3dc-189">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="8b3dc-190">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) não é thread-safe.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-190">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="8b3dc-191">Além disso, você precisa criar uma instância dela em qualquer lugar em que seja necessário dentro de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-191">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="8b3dc-192">À medida que seu aplicativo cresce, esse processo pode se tornar não gerenciável.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-192">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="8b3dc-193">Para melhorar o desempenho e a segurança do thread, use uma combinação de injeção de dependência e o serviço de `PredictionEnginePool`, que cria uma [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) de objetos [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) para uso em todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-193">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

1. <span data-ttu-id="8b3dc-194">Instale o pacote NuGet do *Microsoft.Extensions.ml* :</span><span class="sxs-lookup"><span data-stu-id="8b3dc-194">Install the *Microsoft.Extensions.ML* NuGet package:</span></span>

    1. <span data-ttu-id="8b3dc-195">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-195">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="8b3dc-196">Escolha "nuget.org" como a origem do pacote.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-196">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="8b3dc-197">Selecione a guia **procurar** e procure **Microsoft.Extensions.ml**.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-197">Select the **Browse** tab and search for **Microsoft.Extensions.ML**.</span></span>
    1. <span data-ttu-id="8b3dc-198">Selecione o pacote na lista e selecione o botão **instalar** .</span><span class="sxs-lookup"><span data-stu-id="8b3dc-198">Select the package in the list, and select the **Install** button.</span></span>
    1. <span data-ttu-id="8b3dc-199">Selecione o botão **OK** na caixa de diálogo **Visualizar alterações**</span><span class="sxs-lookup"><span data-stu-id="8b3dc-199">Select the **OK** button on the **Preview Changes** dialog</span></span>
    1. <span data-ttu-id="8b3dc-200">Selecione o botão **aceito** na caixa de diálogo de **aceitação da licença** se você concordar com os termos de licença dos pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-200">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="8b3dc-201">Abra o arquivo *Startup.cs* no projeto *SentimentRazor* .</span><span class="sxs-lookup"><span data-stu-id="8b3dc-201">Open the *Startup.cs* file in the *SentimentRazor* project.</span></span>
1. <span data-ttu-id="8b3dc-202">Adicione as seguintes instruções using para fazer referência ao pacote NuGet do *Microsoft.Extensions.ml* e ao projeto *SentimentRazorML. Model* :</span><span class="sxs-lookup"><span data-stu-id="8b3dc-202">Add the following using statements to reference the *Microsoft.Extensions.ML* NuGet package and *SentimentRazorML.Model* project:</span></span>

    ```csharp
    using System.IO;
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

1. <span data-ttu-id="8b3dc-203">Crie uma variável global para armazenar o local do arquivo de modelo treinado.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-203">Create a global variable to store the location of the trained model file.</span></span>

    ```csharp
    private readonly string _modelPath;
    ```

1. <span data-ttu-id="8b3dc-204">O arquivo de modelo é armazenado no diretório de compilação junto com os arquivos de assembly do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-204">The model file is stored in the build directory alongside the assembly files of your application.</span></span> <span data-ttu-id="8b3dc-205">Para facilitar o acesso, crie um método auxiliar chamado `GetAbsolutePath` depois do método `Configure`</span><span class="sxs-lookup"><span data-stu-id="8b3dc-205">To make it easier to access, create a helper method called `GetAbsolutePath` after the `Configure` method</span></span>

    ```csharp
    public static string GetAbsolutePath(string relativePath)
    {
        FileInfo _dataRoot = new FileInfo(typeof(Program).Assembly.Location);
        string assemblyFolderPath = _dataRoot.Directory.FullName;

        string fullPath = Path.Combine(assemblyFolderPath, relativePath);
        return fullPath;
    }
    ```

1. <span data-ttu-id="8b3dc-206">Use o método `GetAbsolutePath` no construtor da classe `Startup` para definir o `_modelPath`.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-206">Use the `GetAbsolutePath` method in the `Startup` class constructor to set the `_modelPath`.</span></span>

    ```csharp
    _modelPath = GetAbsolutePath("MLModel.zip");
    ```

1. <span data-ttu-id="8b3dc-207">Configure o `PredictionEnginePool` para seu aplicativo no método `ConfigureServices`:</span><span class="sxs-lookup"><span data-stu-id="8b3dc-207">Configure the `PredictionEnginePool` for your application in the `ConfigureServices` method:</span></span>

    ```csharp
    services.AddPredictionEnginePool<ModelInput, ModelOutput>()
            .FromFile(_modelPath);
    ```

### <a name="create-sentiment-analysis-handler"></a><span data-ttu-id="8b3dc-208">Criar manipulador de análise de sentimentos</span><span class="sxs-lookup"><span data-stu-id="8b3dc-208">Create sentiment analysis handler</span></span>

<span data-ttu-id="8b3dc-209">As previsões serão feitas dentro da página principal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-209">Predictions will be made inside the main page of the application.</span></span> <span data-ttu-id="8b3dc-210">Portanto, um método que leva a entrada do usuário e usa o `PredictionEnginePool` para retornar uma previsão precisa ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-210">Therefore, a method that takes the user input and uses the `PredictionEnginePool` to return a prediction needs to be added.</span></span>

1. <span data-ttu-id="8b3dc-211">Abra o arquivo *index.cshtml.cs* localizado no diretório *pages* e adicione as seguintes instruções using:</span><span class="sxs-lookup"><span data-stu-id="8b3dc-211">Open the *Index.cshtml.cs* file located in the *Pages* directory and add the following using statements:</span></span>

    ```csharp
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

    <span data-ttu-id="8b3dc-212">Para usar a `PredictionEnginePool` configurada na classe `Startup`, é necessário inseri-la no construtor do modelo em que você deseja usá-la.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-212">In order to use the `PredictionEnginePool` configured in the `Startup` class, you have to inject it into the constructor of the model where you want to use it.</span></span>

1. <span data-ttu-id="8b3dc-213">Adicione uma variável para fazer referência à `PredictionEnginePool` dentro da classe `IndexModel`.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-213">Add a variable to reference the `PredictionEnginePool` inside the `IndexModel` class.</span></span>

    ```csharp
    private readonly PredictionEnginePool<ModelInput, ModelOutput> _predictionEnginePool;
    ```

1. <span data-ttu-id="8b3dc-214">Crie um construtor na classe `IndexModel` e insira o serviço `PredictionEnginePool` nele.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-214">Create a constructor in the `IndexModel` class and inject the `PredictionEnginePool` service into it.</span></span>

    ```csharp
    public IndexModel(PredictionEnginePool<ModelInput, ModelOutput> predictionEnginePool)
    {
        _predictionEnginePool = predictionEnginePool;
    }
    ```

1. <span data-ttu-id="8b3dc-215">Crie um manipulador de método que usa o `PredictionEnginePool` para fazer previsões da entrada do usuário recebida da página da Web.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-215">Create a method handler that uses the `PredictionEnginePool` to make predictions from user input received from the web page.</span></span>

    1. <span data-ttu-id="8b3dc-216">Abaixo do método `OnGet`, crie um novo método chamado `OnGetAnalyzeSentiment`</span><span class="sxs-lookup"><span data-stu-id="8b3dc-216">Below the `OnGet` method, create a new method called `OnGetAnalyzeSentiment`</span></span>

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. <span data-ttu-id="8b3dc-217">Dentro do método `OnGetAnalyzeSentiment`, retorne um sentimentos *neutro* se a entrada do usuário estiver em branco ou em nulo.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-217">Inside the `OnGetAnalyzeSentiment` method, return *Neutral* sentiment if the input from the user is blank or null.</span></span>

        ```csharp
        if (String.IsNullOrEmpty(text)) return Content("Neutral");
        ```

    1. <span data-ttu-id="8b3dc-218">Dada uma entrada válida, crie uma nova instância do `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-218">Given a valid input, create a new instance of `ModelInput`.</span></span>

        ```csharp
        var input = new ModelInput { SentimentText = text };
        ```

    1. <span data-ttu-id="8b3dc-219">Use o `PredictionEnginePool` para prever sentimentos.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-219">Use the `PredictionEnginePool` to predict sentiment.</span></span>

        ```csharp
        var prediction = _predictionEnginePool.Predict(input);
        ```

    1. <span data-ttu-id="8b3dc-220">Converta o valor de `bool` previsto em tóxicos ou não tóxicos com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-220">Convert the predicted `bool` value into toxic or not toxic with the following code.</span></span>

        ```csharp
        var sentiment = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";
        ```

    1. <span data-ttu-id="8b3dc-221">Por fim, retorne a resposta para a página da Web.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-221">Finally, return the sentiment back to the web page.</span></span>

        ```csharp
        return Content(sentiment);
        ```

### <a name="configure-the-web-page"></a><span data-ttu-id="8b3dc-222">Configurar a página da Web</span><span class="sxs-lookup"><span data-stu-id="8b3dc-222">Configure the web page</span></span>

<span data-ttu-id="8b3dc-223">Os resultados retornados pelo `OnGetAnalyzeSentiment` serão exibidos dinamicamente na página da Web do `Index`.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-223">The results returned by the `OnGetAnalyzeSentiment` will be dynamically displayed on the `Index` web page.</span></span>

1. <span data-ttu-id="8b3dc-224">Abra o arquivo *index. cshtml* no diretório *pages* e substitua seu conteúdo pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="8b3dc-224">Open the *Index.cshtml* file in the *Pages* directory and replace its contents with the following code:</span></span>

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. <span data-ttu-id="8b3dc-225">Em seguida, adicione o código de estilo CSS ao final da página *site. css* no diretório *wwwroot\css* :</span><span class="sxs-lookup"><span data-stu-id="8b3dc-225">Next, add css styling code to the end of the *site.css* page in the *wwwroot\css* directory:</span></span>

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. <span data-ttu-id="8b3dc-226">Depois disso, adicione o código para enviar entradas da página da Web para o manipulador de `OnGetAnalyzeSentiment`.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-226">After that, add code to send inputs from the web page to the `OnGetAnalyzeSentiment` handler.</span></span>

    1. <span data-ttu-id="8b3dc-227">No arquivo *site. js* localizado no diretório *wwwroot\js* , crie uma função chamada `getSentiment` para fazer uma solicitação HTTP Get com a entrada do usuário para o manipulador de `OnGetAnalyzeSentiment`.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-227">In the *site.js* file located in the *wwwroot\js* directory, create a function called `getSentiment` to make a GET HTTP request with the user input to the `OnGetAnalyzeSentiment` handler.</span></span>

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. <span data-ttu-id="8b3dc-228">Abaixo disso, adicione outra função chamada `updateMarker` para atualizar dinamicamente a posição do marcador na página da Web como uma opinião é prevista.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-228">Below that, add another function called `updateMarker` to dynamically update the position of the marker on the web page as sentiment is predicted.</span></span>

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. <span data-ttu-id="8b3dc-229">Crie uma função de manipulador de eventos chamada `updateSentiment` para obter a entrada do usuário, enviá-la para a função `OnGetAnalyzeSentiment` usando a função `getSentiment` e atualize o marcador com a função `updateMarker`.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-229">Create an event handler function called `updateSentiment` to get the input from the user, send it to the `OnGetAnalyzeSentiment` function using the `getSentiment` function and update the marker with the `updateMarker` function.</span></span>

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. <span data-ttu-id="8b3dc-230">Por fim, registre o manipulador de eventos e vincule-o ao elemento `textarea` com o atributo `id=Message`.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-230">Finally, register the event handler and bind it to the `textarea` element with the `id=Message` attribute.</span></span>

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a><span data-ttu-id="8b3dc-231">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="8b3dc-231">Run the application</span></span>

<span data-ttu-id="8b3dc-232">Agora que seu aplicativo está configurado, execute o aplicativo que deve ser iniciado no navegador.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-232">Now that your application is set up, run the application which should launch in your browser.</span></span>

<span data-ttu-id="8b3dc-233">Quando o aplicativo for iniciado, insira o *Construtor de modelos é legal!*</span><span class="sxs-lookup"><span data-stu-id="8b3dc-233">When the application launches, enter *Model Builder is cool!*</span></span> <span data-ttu-id="8b3dc-234">na área de texto.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-234">into the text area.</span></span> <span data-ttu-id="8b3dc-235">As opiniões previstas exibidas *não*devem ser tóxicos.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-235">The predicted sentiment displayed should be *Not Toxic*.</span></span>

![Executando a janela com a janela de opiniões prevista](./media/sentiment-analysis-model-builder/web-app.png)

<span data-ttu-id="8b3dc-237">Se você precisar fazer referência aos projetos gerados pelo construtor de modelos em um momento posterior dentro de outra solução, você poderá encontrá-los dentro do diretório `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-237">If you need to reference the Model Builder generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8b3dc-238">{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="8b3dc-238">Next steps</span></span>

<span data-ttu-id="8b3dc-239">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="8b3dc-239">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="8b3dc-240">Criar um aplicativo de Razor Pages de ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8b3dc-240">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="8b3dc-241">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="8b3dc-241">Prepare and understand the data</span></span>
> - <span data-ttu-id="8b3dc-242">Escolha um cenário</span><span class="sxs-lookup"><span data-stu-id="8b3dc-242">Choose a scenario</span></span>
> - <span data-ttu-id="8b3dc-243">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="8b3dc-243">Load the data</span></span>
> - <span data-ttu-id="8b3dc-244">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="8b3dc-244">Train the model</span></span>
> - <span data-ttu-id="8b3dc-245">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="8b3dc-245">Evaluate the model</span></span>
> - <span data-ttu-id="8b3dc-246">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="8b3dc-246">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="8b3dc-247">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="8b3dc-247">Additional Resources</span></span>

<span data-ttu-id="8b3dc-248">Para saber mais sobre os tópicos mencionados neste tutorial, visite os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="8b3dc-248">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="8b3dc-249">Cenários do Construtor de Modelo</span><span class="sxs-lookup"><span data-stu-id="8b3dc-249">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="8b3dc-250">Classificação Binária</span><span class="sxs-lookup"><span data-stu-id="8b3dc-250">Binary Classification</span></span>](../resources/glossary.md#binary-classification)
- [<span data-ttu-id="8b3dc-251">Métricas do modelo de classificação binária</span><span class="sxs-lookup"><span data-stu-id="8b3dc-251">Binary Classification Model Metrics</span></span>](../resources/metrics.md#metrics-for-binary-classification)
