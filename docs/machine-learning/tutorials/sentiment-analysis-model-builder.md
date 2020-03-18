---
title: 'Tutorial: Analise o sentimento - classificação binária'
description: Este tutorial mostra como criar um aplicativo Razor Pages que classifica o sentimento a partir de comentários do site e toma as medidas apropriadas. O classificador binário de sentimentos usa Model Builder no Visual Studio.
ms.date: 11/21/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc,mlnet-tooling
ms.openlocfilehash: 3419afb36d73599b8fdb0417a8c0cc4057f60089
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187629"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a><span data-ttu-id="4ca8c-104">Tutorial: Analise o sentimento dos comentários do site em um aplicativo web usando ML.NET Model Builder</span><span class="sxs-lookup"><span data-stu-id="4ca8c-104">Tutorial: Analyze sentiment of website comments in a web application using ML.NET Model Builder</span></span>

<span data-ttu-id="4ca8c-105">Aprenda a analisar o sentimento a partir de comentários em tempo real dentro de um aplicativo web.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-105">Learn how to analyze sentiment from comments in real-time inside a web application.</span></span>

<span data-ttu-id="4ca8c-106">Este tutorial mostra como criar um aplicativo ASP.NET Core Razor Pages que classifica o sentimento dos comentários do site em tempo real.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-106">This tutorial shows you how to create an ASP.NET Core Razor Pages application that classifies sentiment from website comments in real-time.</span></span>

<span data-ttu-id="4ca8c-107">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="4ca8c-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="4ca8c-108">Crie um aplicativo de páginas de navalha ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4ca8c-108">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="4ca8c-109">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="4ca8c-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="4ca8c-110">Escolha um cenário</span><span class="sxs-lookup"><span data-stu-id="4ca8c-110">Choose a scenario</span></span>
> - <span data-ttu-id="4ca8c-111">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="4ca8c-111">Load the data</span></span>
> - <span data-ttu-id="4ca8c-112">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="4ca8c-112">Train the model</span></span>
> - <span data-ttu-id="4ca8c-113">Avalie o modelo</span><span class="sxs-lookup"><span data-stu-id="4ca8c-113">Evaluate the model</span></span>
> - <span data-ttu-id="4ca8c-114">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="4ca8c-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="4ca8c-115">O Construtor de Modelo está atualmente na Versão Prévia.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-115">Model Builder is currently in Preview.</span></span>

<span data-ttu-id="4ca8c-116">Você pode encontrar o código fonte para este tutorial no repositório [dotnet/machinelearning-samples.](https://github.com/dotnet/machinelearning-samples)</span><span class="sxs-lookup"><span data-stu-id="4ca8c-116">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples) repository.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="4ca8c-117">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="4ca8c-117">Pre-requisites</span></span>

<span data-ttu-id="4ca8c-118">Para obter uma lista de pré-requisitos e instruções de instalação, visite o [guia de instalação do Construtor de Modelo](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="4ca8c-118">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-razor-pages-application"></a><span data-ttu-id="4ca8c-119">Criar um aplicativo de páginas de barbear</span><span class="sxs-lookup"><span data-stu-id="4ca8c-119">Create a Razor Pages application</span></span>

1. <span data-ttu-id="4ca8c-120">Crie um **ASP.NET aplicativo de páginas de navalha do núcleo**.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-120">Create a **ASP.NET Core Razor Pages Application**.</span></span>

    1. <span data-ttu-id="4ca8c-121">Abra o Visual Studio e selecione **File > New > Project** na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-121">Open Visual Studio and select **File > New > Project** from the menu bar.</span></span>
    1. <span data-ttu-id="4ca8c-122">Na caixa de diálogo Novo projeto, selecione o nó **Visual C#** seguido pelo nó **Web**.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-122">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span>
    1. <span data-ttu-id="4ca8c-123">Em seguida, selecione o modelo de projeto **Aplicativo ASP.NET Core Web**.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-123">Then select the **ASP.NET Core Web Application** project template.</span></span>
    1. <span data-ttu-id="4ca8c-124">Na caixa de texto **Nome,** digite "SentimentRazor".</span><span class="sxs-lookup"><span data-stu-id="4ca8c-124">In the **Name** text box, type "SentimentRazor".</span></span>
    1. <span data-ttu-id="4ca8c-125">Certifique-se de que **a solução e o projeto place no mesmo diretório** não são **controlados** (VS 2019), ou **Criar diretório para solução** é **verificado** (VS 2017).</span><span class="sxs-lookup"><span data-stu-id="4ca8c-125">Make sure **Place solution and project in the same directory** is **unchecked** (VS 2019), or **Create directory for solution** is **checked** (VS 2017).</span></span>
    1. <span data-ttu-id="4ca8c-126">Selecione o botão **OK.**</span><span class="sxs-lookup"><span data-stu-id="4ca8c-126">Select the **OK** button.</span></span>
    1. <span data-ttu-id="4ca8c-127">Escolha **a aplicação da Web** na janela que exibe os diferentes tipos de ASP.NET Projetos principais e, em seguida, selecione o botão **OK.**</span><span class="sxs-lookup"><span data-stu-id="4ca8c-127">Choose **Web Application** in the window that displays the different types of ASP.NET Core Projects, and then select the **OK** button.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="4ca8c-128">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="4ca8c-128">Prepare and understand the data</span></span>

<span data-ttu-id="4ca8c-129">Baixe [o conjunto de dados desintoxicação da Wikipédia](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv).</span><span class="sxs-lookup"><span data-stu-id="4ca8c-129">Download [Wikipedia detox dataset](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span> <span data-ttu-id="4ca8c-130">Quando a página da Web for aberta, clique com o botão direito do mouse na página, **selecione Salvar como** e salve o arquivo em qualquer lugar do computador.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-130">When the webpage opens, right-click on the page, select **Save As** and save the file anywhere on your computer.</span></span>

<span data-ttu-id="4ca8c-131">Cada linha no conjunto *de dados wikipedia-detox-250-line.tsv* representa uma revisão diferente deixada por um usuário na Wikipédia.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-131">Each row in the *wikipedia-detox-250-line-data.tsv* dataset represents a different review left by a user on Wikipedia.</span></span> <span data-ttu-id="4ca8c-132">A primeira coluna representa o sentimento do texto (0 não é tóxico, 1 é tóxico), e a segunda coluna representa o comentário deixado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-132">The first column represents the sentiment of the text (0 is non-toxic, 1 is toxic), and the second column represents the comment left by the user.</span></span> <span data-ttu-id="4ca8c-133">As colunas são separadas por guias.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-133">The columns are separated by tabs.</span></span> <span data-ttu-id="4ca8c-134">Os dados se parecem com os seguintes:</span><span class="sxs-lookup"><span data-stu-id="4ca8c-134">The data looks like the following:</span></span>

| <span data-ttu-id="4ca8c-135">Sentimento</span><span class="sxs-lookup"><span data-stu-id="4ca8c-135">Sentiment</span></span> | <span data-ttu-id="4ca8c-136">SentimentText</span><span class="sxs-lookup"><span data-stu-id="4ca8c-136">SentimentText</span></span> |
| :---: | :---: |
<span data-ttu-id="4ca8c-137">1</span><span class="sxs-lookup"><span data-stu-id="4ca8c-137">1</span></span> | <span data-ttu-id="4ca8c-138">==RUDE== Cara, você é rude carregar aquela foto do Carl de volta, ou então.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-138">==RUDE== Dude, you are rude upload that carl picture back, or else.</span></span>
<span data-ttu-id="4ca8c-139">1</span><span class="sxs-lookup"><span data-stu-id="4ca8c-139">1</span></span> | <span data-ttu-id="4ca8c-140">== OK!</span><span class="sxs-lookup"><span data-stu-id="4ca8c-140">== OK!</span></span> <span data-ttu-id="4ca8c-141">== IM VAI VANDALIZAR OS SELVAGENS WIKI ENTÃO!!!</span><span class="sxs-lookup"><span data-stu-id="4ca8c-141">==  IM GOING TO VANDALIZE WILD ONES WIKI THEN!!!</span></span>
<span data-ttu-id="4ca8c-142">0</span><span class="sxs-lookup"><span data-stu-id="4ca8c-142">0</span></span> | <span data-ttu-id="4ca8c-143">Espero que isso ajude.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-143">I hope this helps.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="4ca8c-144">Escolha um cenário</span><span class="sxs-lookup"><span data-stu-id="4ca8c-144">Choose a scenario</span></span>

![Assistente do Construtor de Modelos no Visual Studio](./media/sentiment-analysis-model-builder/model-builder-screen.png)

<span data-ttu-id="4ca8c-146">Para treinar seu modelo, você precisa selecionar na lista de cenários disponíveis de aprendizado de máquina fornecidos pelo Construtor de Modelo.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-146">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span>

1. <span data-ttu-id="4ca8c-147">No **Solution Explorer,** clique com o botão direito do mouse no projeto *SentimentRazor* e selecione **Adicionar** > **aprendizado de máquina**.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-147">In **Solution Explorer**, right-click the *SentimentRazor* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="4ca8c-148">Para esta amostra, o cenário é a análise de sentimentos.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-148">For this sample, the scenario is sentiment analysis.</span></span> <span data-ttu-id="4ca8c-149">Na etapa de *cenário* da ferramenta Model Builder, selecione o cenário **de Análise de Sentimento.**</span><span class="sxs-lookup"><span data-stu-id="4ca8c-149">In the *scenario* step of the Model Builder tool, select the **Sentiment Analysis** scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="4ca8c-150">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="4ca8c-150">Load the data</span></span>

<span data-ttu-id="4ca8c-151">O Model Builder aceita dados de duas fontes, um banco `csv` `tsv` de dados SQL Server ou um arquivo local dentro ou formato.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-151">Model Builder accepts data from two sources, a SQL Server database or a local file in `csv` or `tsv` format.</span></span>

1. <span data-ttu-id="4ca8c-152">Na etapa de dados da ferramenta do Construtor de Modelo, selecione **Arquivo** na lista suspensa da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-152">In the data step of the Model Builder tool, select **File** from the data source dropdown.</span></span>
1. <span data-ttu-id="4ca8c-153">Selecione o botão ao lado da **Caixa Selecionar uma** caixa de texto de arquivo e use o File Explorer para navegar e selecionar o arquivo *wikipedia-detox-250-line-data.tsv.*</span><span class="sxs-lookup"><span data-stu-id="4ca8c-153">Select the button next to the **Select a file** text box and use File Explorer to browse and select the *wikipedia-detox-250-line-data.tsv* file.</span></span>
1. <span data-ttu-id="4ca8c-154">Escolha **Sentimento** na **coluna para prever (rótulo)** dropdown.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-154">Choose **Sentiment** in the **Column to Predict (Label)** dropdown.</span></span>
1. <span data-ttu-id="4ca8c-155">Deixe os valores padrão para a estada **'Colunas de entrada (Recursos].**</span><span class="sxs-lookup"><span data-stu-id="4ca8c-155">Leave the default values for the **Input Columns (Features)** dropdown.</span></span>
1. <span data-ttu-id="4ca8c-156">Selecione o link **Trem** para passar para a próxima etapa na ferramenta Construtor de modelos.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-156">Select the **Train** link to move to the next step in the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="4ca8c-157">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="4ca8c-157">Train the model</span></span>

<span data-ttu-id="4ca8c-158">A tarefa de aprendizado de máquina usada para treinar o modelo de análise de sentimento neste tutorial é a classificação binária.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-158">The machine learning task used to train the sentiment analysis model in this tutorial is binary classification.</span></span> <span data-ttu-id="4ca8c-159">Durante o processo de treinamento do modelo, o Model Builder treina modelos separados usando diferentes algoritmos de classificação binária e configurações para encontrar o modelo de melhor desempenho para o seu conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-159">During the model training process, Model Builder trains separate models using different binary classification algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="4ca8c-160">O tempo necessário para treinar o modelo é proporcional à quantidade de dados.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-160">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="4ca8c-161">O Model Builder seleciona automaticamente um valor padrão para **tempo de treinar (segundos)** com base no tamanho da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-161">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="4ca8c-162">Embora o Model Builder defina o valor do **Tempo para treinar (segundos)** para 10 segundos, aumente-o para 30 segundos.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-162">Although Model Builder sets the value of **Time to train (seconds)** to 10 seconds, increase it to 30 seconds.</span></span> <span data-ttu-id="4ca8c-163">O treinamento por um período maior de tempo permite ao Model Builder explorar um número maior de algoritmos e combinação de parâmetros em busca do melhor modelo.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-163">Training for a longer period of time allows Model Builder to explore a larger number of algorithms and combination of parameters in search of the best model.</span></span>
1. <span data-ttu-id="4ca8c-164">Selecione **Iniciar Treinamento**.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-164">Select **Start Training**.</span></span>

    <span data-ttu-id="4ca8c-165">Durante o processo de treinamento, os dados de progresso são exibidos na seção `Progress` da etapa de treinamento.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-165">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

    - <span data-ttu-id="4ca8c-166">O status exibe o status de conclusão do processo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-166">Status displays the completion status of the training process.</span></span>
    - <span data-ttu-id="4ca8c-167">A melhor precisão exibe a precisão do modelo de melhor desempenho encontrado pelo Construtor do Modelo até o momento.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-167">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="4ca8c-168">Maior precisão significa que o modelo é previsto mais corretamente nos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-168">Higher accuracy means the model predicted more correctly on test data.</span></span>
    - <span data-ttu-id="4ca8c-169">O melhor algoritmo exibe o nome do algoritmo de melhor desempenho executado encontrado pelo Construtor de Modelo até o momento.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-169">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
    - <span data-ttu-id="4ca8c-170">O último algoritmo exibe o nome do algoritmo usado mais recentemente pelo Construtor de Modelo para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-170">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

1. <span data-ttu-id="4ca8c-171">Uma vez que o treinamento esteja concluído, selecione o link **de avaliação** para passar para a próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-171">Once training is complete, select the **evaluate** link to move to the next step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="4ca8c-172">Avalie o modelo</span><span class="sxs-lookup"><span data-stu-id="4ca8c-172">Evaluate the model</span></span>

<span data-ttu-id="4ca8c-173">O resultado da etapa de treinamento será um modelo que tinha o melhor desempenho.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-173">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="4ca8c-174">Na etapa de avaliação da ferramenta Model Builder, a seção de saída, conterá o algoritmo usado pelo modelo de melhor desempenho na entrada **do Melhor Modelo,** juntamente com métricas em **Melhor Precisão de Modelo**.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-174">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the **Best Model** entry along with metrics in **Best Model Accuracy**.</span></span> <span data-ttu-id="4ca8c-175">Além disso, uma tabela de resumo contém os cinco modelos principais e suas métricas.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-175">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="4ca8c-176">Se você não estiver satisfeito com suas métricas de precisão, algumas maneiras fáceis de experimentar e aprimorar a precisão do modelo serão aumentar a quantidade de tempo para treinar o modelo ou usar mais dados.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-176">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="4ca8c-177">Caso contrário, selecione o link **de código** para passar para a etapa final na ferramenta Construtor de modelos.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-177">Otherwise, select the **code** link to move to the final step in the Model Builder tool.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="4ca8c-178">Adicionar o código para fazer previsões</span><span class="sxs-lookup"><span data-stu-id="4ca8c-178">Add the code to make predictions</span></span>

<span data-ttu-id="4ca8c-179">Dois projetos serão criados como resultado do processo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-179">Two projects will be created as a result of the training process.</span></span>

### <a name="reference-the-trained-model"></a><span data-ttu-id="4ca8c-180">Referência ao modelo treinado</span><span class="sxs-lookup"><span data-stu-id="4ca8c-180">Reference the trained model</span></span>

1. <span data-ttu-id="4ca8c-181">Na etapa de *código* da ferramenta Model Builder, **selecione Adicionar projetos** para adicionar os projetos gerados automaticamente à solução.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-181">In the *code* step of the Model Builder tool, select **Add Projects** to add the autogenerated projects to the solution.</span></span>

    <span data-ttu-id="4ca8c-182">Os seguintes projetos devem aparecer no **Solution Explorer**:</span><span class="sxs-lookup"><span data-stu-id="4ca8c-182">The following projects should appear in the **Solution Explorer**:</span></span>

    - <span data-ttu-id="4ca8c-183">*SentimentRazorML.ConsoleApp*: Um aplicativo .NET Core Console que contém o código de treinamento e previsão do modelo.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-183">*SentimentRazorML.ConsoleApp*: A .NET Core Console application that contains the model training and prediction code.</span></span>
    - <span data-ttu-id="4ca8c-184">*SentimentRazorML.Model*: Uma biblioteca de classe .NET Standard contendo os modelos de dados que definem o esquema de dados do modelo de entrada e saída, bem como a versão salva do modelo de melhor desempenho durante o treinamento.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-184">*SentimentRazorML.Model*: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the saved version of the best performing model during training.</span></span>

    <span data-ttu-id="4ca8c-185">Para este tutorial, apenas o projeto *SentimentRazorML.Model* é usado porque as previsões serão feitas no aplicativo web *SentimentRazor* em vez de no console.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-185">For this tutorial, only the *SentimentRazorML.Model* project is used because predictions will be made in the *SentimentRazor* web application rather than in the console.</span></span> <span data-ttu-id="4ca8c-186">Embora o *SentimentRazorML.ConsoleApp* não seja usado para marcar, ele pode ser usado para retreinar o modelo usando novos dados posteriormente.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-186">Although the *SentimentRazorML.ConsoleApp* won't be used for scoring, it can be used to retrain the model using new data at a later time.</span></span> <span data-ttu-id="4ca8c-187">O retreinamento está fora do escopo deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-187">Retraining is outside the scope of this tutorial though.</span></span>

### <a name="configure-the-predictionengine-pool"></a><span data-ttu-id="4ca8c-188">Configure o pool ForecastEngine</span><span class="sxs-lookup"><span data-stu-id="4ca8c-188">Configure the PredictionEngine pool</span></span>

<span data-ttu-id="4ca8c-189">Para fazer uma única previsão, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)você tem que criar um .</span><span class="sxs-lookup"><span data-stu-id="4ca8c-189">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="4ca8c-190">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)não é seguro para rosca.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-190">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="4ca8c-191">Além disso, você tem que criar uma instância dele em todos os lugares necessários dentro de sua aplicação.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-191">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="4ca8c-192">À medida que sua aplicação cresce, esse processo pode se tornar incontrolável.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-192">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="4ca8c-193">Para melhorar o desempenho e a segurança dos fios, use uma combinação de injeção de dependência e o `PredictionEnginePool` serviço, que cria um de [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objetos para uso em toda a sua aplicação.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-193">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

1. <span data-ttu-id="4ca8c-194">Instale o pacote *Microsoft.Extensions.ML* NuGet:</span><span class="sxs-lookup"><span data-stu-id="4ca8c-194">Install the *Microsoft.Extensions.ML* NuGet package:</span></span>

    1. <span data-ttu-id="4ca8c-195">No **Gerenciador de Soluções**, clique com o botão direito no projeto e escolha **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-195">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="4ca8c-196">Escolha "nuget.org" como fonte do Pacote.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-196">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="4ca8c-197">Selecione a guia **Procurar** e procurar por **Microsoft.Extensions.ML**.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-197">Select the **Browse** tab and search for **Microsoft.Extensions.ML**.</span></span>
    1. <span data-ttu-id="4ca8c-198">Selecione o pacote na lista e selecione o botão **Instalar.**</span><span class="sxs-lookup"><span data-stu-id="4ca8c-198">Select the package in the list, and select the **Install** button.</span></span>
    1. <span data-ttu-id="4ca8c-199">Selecione o botão **OK** na caixa **de diálogo Visualização Alterações**</span><span class="sxs-lookup"><span data-stu-id="4ca8c-199">Select the **OK** button on the **Preview Changes** dialog</span></span>
    1. <span data-ttu-id="4ca8c-200">Selecione o botão **Eu Aceito** na caixa de diálogo **Aceitação de Licença** se você concordar com os termos de licença dos pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-200">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="4ca8c-201">Abra o arquivo *Startup.cs* no projeto *SentimentRazor.*</span><span class="sxs-lookup"><span data-stu-id="4ca8c-201">Open the *Startup.cs* file in the *SentimentRazor* project.</span></span>
1. <span data-ttu-id="4ca8c-202">Adicione as seguintes instruções usando para referenciar o pacote *Microsoft.Extensions.ML* NuGet e o projeto *SentimentRazorML.Model:*</span><span class="sxs-lookup"><span data-stu-id="4ca8c-202">Add the following using statements to reference the *Microsoft.Extensions.ML* NuGet package and *SentimentRazorML.Model* project:</span></span>

    ```csharp
    using System.IO;
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

1. <span data-ttu-id="4ca8c-203">Crie uma variável global para armazenar a localização do arquivo de modelo treinado.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-203">Create a global variable to store the location of the trained model file.</span></span>

    ```csharp
    private readonly string _modelPath;
    ```

1. <span data-ttu-id="4ca8c-204">O arquivo modelo é armazenado no diretório de compilação ao lado dos arquivos de montagem do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-204">The model file is stored in the build directory alongside the assembly files of your application.</span></span> <span data-ttu-id="4ca8c-205">Para facilitar o acesso, crie um `GetAbsolutePath` método `Configure` auxiliar chamado após o método</span><span class="sxs-lookup"><span data-stu-id="4ca8c-205">To make it easier to access, create a helper method called `GetAbsolutePath` after the `Configure` method</span></span>

    ```csharp
    public static string GetAbsolutePath(string relativePath)
    {
        FileInfo _dataRoot = new FileInfo(typeof(Program).Assembly.Location);
        string assemblyFolderPath = _dataRoot.Directory.FullName;

        string fullPath = Path.Combine(assemblyFolderPath, relativePath);
        return fullPath;
    }
    ```

1. <span data-ttu-id="4ca8c-206">Use `GetAbsolutePath` o método `Startup` no construtor de `_modelPath`classe para definir o .</span><span class="sxs-lookup"><span data-stu-id="4ca8c-206">Use the `GetAbsolutePath` method in the `Startup` class constructor to set the `_modelPath`.</span></span>

    ```csharp
    _modelPath = GetAbsolutePath("MLModel.zip");
    ```

1. <span data-ttu-id="4ca8c-207">Configure `PredictionEnginePool` o para sua `ConfigureServices` aplicação no método:</span><span class="sxs-lookup"><span data-stu-id="4ca8c-207">Configure the `PredictionEnginePool` for your application in the `ConfigureServices` method:</span></span>

    ```csharp
    services.AddPredictionEnginePool<ModelInput, ModelOutput>()
            .FromFile(_modelPath);
    ```

### <a name="create-sentiment-analysis-handler"></a><span data-ttu-id="4ca8c-208">Crie manipulador de análise de sentimentos</span><span class="sxs-lookup"><span data-stu-id="4ca8c-208">Create sentiment analysis handler</span></span>

<span data-ttu-id="4ca8c-209">As previsões serão feitas dentro da página principal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-209">Predictions will be made inside the main page of the application.</span></span> <span data-ttu-id="4ca8c-210">Portanto, um método que leve a `PredictionEnginePool` entrada do usuário e use o para retornar uma previsão precisa ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-210">Therefore, a method that takes the user input and uses the `PredictionEnginePool` to return a prediction needs to be added.</span></span>

1. <span data-ttu-id="4ca8c-211">Abra o *arquivo Index.cshtml.cs* localizado no diretório *Páginas* e adicione as seguintes instruções usando:</span><span class="sxs-lookup"><span data-stu-id="4ca8c-211">Open the *Index.cshtml.cs* file located in the *Pages* directory and add the following using statements:</span></span>

    ```csharp
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

    <span data-ttu-id="4ca8c-212">Para usar o `PredictionEnginePool` configurado `Startup` na classe, você tem que injetá-lo no construtor do modelo onde você deseja usá-lo.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-212">In order to use the `PredictionEnginePool` configured in the `Startup` class, you have to inject it into the constructor of the model where you want to use it.</span></span>

1. <span data-ttu-id="4ca8c-213">Adicione uma variável `PredictionEnginePool` para `IndexModel` referenciar o interior da classe.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-213">Add a variable to reference the `PredictionEnginePool` inside the `IndexModel` class.</span></span>

    ```csharp
    private readonly PredictionEnginePool<ModelInput, ModelOutput> _predictionEnginePool;
    ```

1. <span data-ttu-id="4ca8c-214">Crie um construtor `IndexModel` na classe `PredictionEnginePool` e injete o serviço nele.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-214">Create a constructor in the `IndexModel` class and inject the `PredictionEnginePool` service into it.</span></span>

    ```csharp
    public IndexModel(PredictionEnginePool<ModelInput, ModelOutput> predictionEnginePool)
    {
        _predictionEnginePool = predictionEnginePool;
    }
    ```

1. <span data-ttu-id="4ca8c-215">Crie um manipulador de `PredictionEnginePool` métodos que use o para fazer previsões a partir da entrada do usuário recebida da página da Web.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-215">Create a method handler that uses the `PredictionEnginePool` to make predictions from user input received from the web page.</span></span>

    1. <span data-ttu-id="4ca8c-216">Abaixo `OnGet` do método, crie um novo método chamado`OnGetAnalyzeSentiment`</span><span class="sxs-lookup"><span data-stu-id="4ca8c-216">Below the `OnGet` method, create a new method called `OnGetAnalyzeSentiment`</span></span>

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. <span data-ttu-id="4ca8c-217">Dentro `OnGetAnalyzeSentiment` do método, retorne o sentimento *neutro* se a entrada do usuário estiver em branco ou nula.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-217">Inside the `OnGetAnalyzeSentiment` method, return *Neutral* sentiment if the input from the user is blank or null.</span></span>

        ```csharp
        if (String.IsNullOrEmpty(text)) return Content("Neutral");
        ```

    1. <span data-ttu-id="4ca8c-218">Dada uma entrada válida, `ModelInput`crie uma nova instância de .</span><span class="sxs-lookup"><span data-stu-id="4ca8c-218">Given a valid input, create a new instance of `ModelInput`.</span></span>

        ```csharp
        var input = new ModelInput { SentimentText = text };
        ```

    1. <span data-ttu-id="4ca8c-219">Use `PredictionEnginePool` o para prever sentimentos.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-219">Use the `PredictionEnginePool` to predict sentiment.</span></span>

        ```csharp
        var prediction = _predictionEnginePool.Predict(input);
        ```

    1. <span data-ttu-id="4ca8c-220">Converta o `bool` valor previsto em tóxico ou não tóxico com o seguinte código.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-220">Convert the predicted `bool` value into toxic or not toxic with the following code.</span></span>

        ```csharp
        var sentiment = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";
        ```

    1. <span data-ttu-id="4ca8c-221">Finalmente, retorne o sentimento para a página web.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-221">Finally, return the sentiment back to the web page.</span></span>

        ```csharp
        return Content(sentiment);
        ```

### <a name="configure-the-web-page"></a><span data-ttu-id="4ca8c-222">Configure a página da Web</span><span class="sxs-lookup"><span data-stu-id="4ca8c-222">Configure the web page</span></span>

<span data-ttu-id="4ca8c-223">Os resultados devolvidos `OnGetAnalyzeSentiment` pelo serão exibidos `Index` dinamicamente na página web.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-223">The results returned by the `OnGetAnalyzeSentiment` will be dynamically displayed on the `Index` web page.</span></span>

1. <span data-ttu-id="4ca8c-224">Abra o arquivo *Index.cshtml* no diretório *Páginas* e substitua seu conteúdo pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="4ca8c-224">Open the *Index.cshtml* file in the *Pages* directory and replace its contents with the following code:</span></span>

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. <span data-ttu-id="4ca8c-225">Em seguida, adicione o código de estilo css ao final da página *site.css* no diretório *wwwroot\css:*</span><span class="sxs-lookup"><span data-stu-id="4ca8c-225">Next, add css styling code to the end of the *site.css* page in the *wwwroot\css* directory:</span></span>

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. <span data-ttu-id="4ca8c-226">Depois disso, adicione código para enviar entradas `OnGetAnalyzeSentiment` da página web para o manipulador.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-226">After that, add code to send inputs from the web page to the `OnGetAnalyzeSentiment` handler.</span></span>

    1. <span data-ttu-id="4ca8c-227">No arquivo *site.js* localizado no diretório *wwwroot\js,* crie `getSentiment` uma função chamada para fazer uma `OnGetAnalyzeSentiment` solicitação GET HTTP com a entrada do usuário para o manipulador.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-227">In the *site.js* file located in the *wwwroot\js* directory, create a function called `getSentiment` to make a GET HTTP request with the user input to the `OnGetAnalyzeSentiment` handler.</span></span>

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. <span data-ttu-id="4ca8c-228">Abaixo disso, adicione `updateMarker` outra função chamada para atualizar dinamicamente a posição do marcador na página da Web como o sentimento é previsto.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-228">Below that, add another function called `updateMarker` to dynamically update the position of the marker on the web page as sentiment is predicted.</span></span>

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. <span data-ttu-id="4ca8c-229">Crie uma função `updateSentiment` manipuladora de eventos chamada para obter `OnGetAnalyzeSentiment` a `getSentiment` entrada do usuário, `updateMarker` envie-a para a função usando a função e atualize o marcador com a função.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-229">Create an event handler function called `updateSentiment` to get the input from the user, send it to the `OnGetAnalyzeSentiment` function using the `getSentiment` function and update the marker with the `updateMarker` function.</span></span>

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. <span data-ttu-id="4ca8c-230">Finalmente, registre o manipulador de `textarea` eventos e `id=Message` vincule-o ao elemento com o atributo.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-230">Finally, register the event handler and bind it to the `textarea` element with the `id=Message` attribute.</span></span>

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a><span data-ttu-id="4ca8c-231">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="4ca8c-231">Run the application</span></span>

<span data-ttu-id="4ca8c-232">Agora que seu aplicativo está configurado, execute o aplicativo que deve ser lançado no seu navegador.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-232">Now that your application is set up, run the application which should launch in your browser.</span></span>

<span data-ttu-id="4ca8c-233">Quando o aplicativo for lançado, digite *Model Builder é legal!*</span><span class="sxs-lookup"><span data-stu-id="4ca8c-233">When the application launches, enter *Model Builder is cool!*</span></span> <span data-ttu-id="4ca8c-234">na área de texto.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-234">into the text area.</span></span> <span data-ttu-id="4ca8c-235">O sentimento previsto exibido não deve ser *tóxico.*</span><span class="sxs-lookup"><span data-stu-id="4ca8c-235">The predicted sentiment displayed should be *Not Toxic*.</span></span>

![Janela de execução com a janela de sentimento prevista](./media/sentiment-analysis-model-builder/web-app.png)

<span data-ttu-id="4ca8c-237">Se você precisar referenciar os projetos gerados pelo Model Builder posteriormente `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` dentro de outra solução, você pode encontrá-los dentro do diretório.</span><span class="sxs-lookup"><span data-stu-id="4ca8c-237">If you need to reference the Model Builder generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4ca8c-238">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="4ca8c-238">Next steps</span></span>

<span data-ttu-id="4ca8c-239">Neste tutorial, você aprendeu a:</span><span class="sxs-lookup"><span data-stu-id="4ca8c-239">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="4ca8c-240">Crie um aplicativo de páginas de navalha ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4ca8c-240">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="4ca8c-241">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="4ca8c-241">Prepare and understand the data</span></span>
> - <span data-ttu-id="4ca8c-242">Escolha um cenário</span><span class="sxs-lookup"><span data-stu-id="4ca8c-242">Choose a scenario</span></span>
> - <span data-ttu-id="4ca8c-243">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="4ca8c-243">Load the data</span></span>
> - <span data-ttu-id="4ca8c-244">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="4ca8c-244">Train the model</span></span>
> - <span data-ttu-id="4ca8c-245">Avalie o modelo</span><span class="sxs-lookup"><span data-stu-id="4ca8c-245">Evaluate the model</span></span>
> - <span data-ttu-id="4ca8c-246">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="4ca8c-246">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="4ca8c-247">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="4ca8c-247">Additional Resources</span></span>

<span data-ttu-id="4ca8c-248">Para saber mais sobre os tópicos mencionados neste tutorial, visite os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="4ca8c-248">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="4ca8c-249">Cenários do Construtor de Modelo</span><span class="sxs-lookup"><span data-stu-id="4ca8c-249">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="4ca8c-250">Classificação Binária</span><span class="sxs-lookup"><span data-stu-id="4ca8c-250">Binary Classification</span></span>](../resources/glossary.md#binary-classification)
- [<span data-ttu-id="4ca8c-251">Métricas do modelo de classificação binária</span><span class="sxs-lookup"><span data-stu-id="4ca8c-251">Binary Classification Model Metrics</span></span>](../resources/metrics.md#evaluation-metrics-for-binary-classification)
