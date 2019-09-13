---
title: Prever os preços usando regressão com o Construtor de Modelo
description: Este tutorial mostra como criar um modelo de regressão usando o Construtor de Modelo do ML.NET para prever os preços, especificamente, as tarifas de táxi de Nova York.
author: luisquintanilla
ms.author: luquinta
ms.date: 07/15/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: bc1dacdad436cc5384bca4bbce224acc18d69201
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929437"
---
# <a name="predict-prices-using-regression-with-model-builder"></a><span data-ttu-id="f4453-103">Prever os preços usando regressão com o Construtor de Modelo</span><span class="sxs-lookup"><span data-stu-id="f4453-103">Predict prices using regression with Model Builder</span></span>

<span data-ttu-id="f4453-104">Saiba como usar o Construtor de Modelo do ML.NET para criar um modelo de regressão() e prever preços.</span><span class="sxs-lookup"><span data-stu-id="f4453-104">Learn how to use ML.NET Model Builder to build a regression model() to predict prices.</span></span>  <span data-ttu-id="f4453-105">O aplicativo de console do .NET que você desenvolve neste tutorial prevê as tarifas de táxi com base em dados históricos de tarifas de táxi em Nova York.</span><span class="sxs-lookup"><span data-stu-id="f4453-105">The .NET console app that you develop in this tutorial predicts taxi fares based on historical New York taxi fare data.</span></span>

<span data-ttu-id="f4453-106">O modelo de previsão de preço do Construtor de Modelo pode ser usado em qualquer cenário que exija um valor de previsão numérico.</span><span class="sxs-lookup"><span data-stu-id="f4453-106">The Model Builder price prediction template can be used for any scenario requiring a numerical prediction value.</span></span> <span data-ttu-id="f4453-107">Exemplos de cenários incluem: previsão de preço, previsão de demanda e previsão de vendas de casas.</span><span class="sxs-lookup"><span data-stu-id="f4453-107">Example scenarios include: house price prediction, demand prediction, and sales forecasting.</span></span>

<span data-ttu-id="f4453-108">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="f4453-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="f4453-109">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="f4453-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="f4453-110">Escolha um cenário</span><span class="sxs-lookup"><span data-stu-id="f4453-110">Choose a scenario</span></span>
> - <span data-ttu-id="f4453-111">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="f4453-111">Load the data</span></span>
> - <span data-ttu-id="f4453-112">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="f4453-112">Train the model</span></span>
> - <span data-ttu-id="f4453-113">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="f4453-113">Evaluate the model</span></span>
> - <span data-ttu-id="f4453-114">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="f4453-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="f4453-115">O Construtor de Modelo está atualmente na Versão Prévia.</span><span class="sxs-lookup"><span data-stu-id="f4453-115">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="f4453-116">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="f4453-116">Pre-requisites</span></span>

<span data-ttu-id="f4453-117">Para obter uma lista de pré-requisitos e instruções de instalação, visite o [guia de instalação do Construtor de Modelo](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="f4453-117">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="f4453-118">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="f4453-118">Create a console application</span></span>

1. <span data-ttu-id="f4453-119">Crie um **Aplicativo de Console do .NET Core** chamado "TaxiFarePrediction".</span><span class="sxs-lookup"><span data-stu-id="f4453-119">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="f4453-120">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="f4453-120">Prepare and understand the data</span></span>

1. <span data-ttu-id="f4453-121">Crie um diretório chamado *Data* no projeto para armazenar os arquivos do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="f4453-121">Create a directory named *Data* in your project to store the data set files.</span></span>

1. <span data-ttu-id="f4453-122">O conjunto de dados usado para treinar e avaliar o modelo de machine learning pertence originalmente ao conjunto de dados Corrida de Táxi da NYC TLC.</span><span class="sxs-lookup"><span data-stu-id="f4453-122">The data set used to train and evaluate the machine learning model is originally from the NYC TLC Taxi Trip data set.</span></span>

    <span data-ttu-id="f4453-123">Para baixar o conjunto de dados, navegue até o link de download [taxi-fare-train.csv](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span><span class="sxs-lookup"><span data-stu-id="f4453-123">To download the data set, navigate to the [taxi-fare-train.csv download link](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span></span>

    <span data-ttu-id="f4453-124">Quando a página for carregada, clique com o botão direito do mouse em qualquer lugar da página e escolha **Salvar como**.</span><span class="sxs-lookup"><span data-stu-id="f4453-124">When the page loads, right-click anywhere on the page and select **Save as**.</span></span>

    <span data-ttu-id="f4453-125">Use a opção **Salvar como Diálogo** para salvar o arquivo na pasta *Dados* criada na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="f4453-125">Use the **Save As Dialog** to save the file in the *Data* folder you created at the previous step.</span></span>

1. <span data-ttu-id="f4453-126">No **Gerenciador de Soluções**, clique com o botão direito do mouse no arquivo *taxi-fare-train.csv* e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="f4453-126">In **Solution Explorer**, right-click the *taxi-fare-train.csv* file and select **Properties**.</span></span> <span data-ttu-id="f4453-127">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.</span><span class="sxs-lookup"><span data-stu-id="f4453-127">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="f4453-128">Cada linha no conjunto de dados `taxi-fare-train.csv` contém os detalhes de corridas feitas por um táxi.</span><span class="sxs-lookup"><span data-stu-id="f4453-128">Each row in the `taxi-fare-train.csv` data set contains details of trips made by a taxi.</span></span>

1. <span data-ttu-id="f4453-129">Abra o conjunto de dados **taxi-fare-train.csv**</span><span class="sxs-lookup"><span data-stu-id="f4453-129">Open the **taxi-fare-train.csv** data set</span></span>

    <span data-ttu-id="f4453-130">O conjunto de dados fornecido contém as seguintes colunas:</span><span class="sxs-lookup"><span data-stu-id="f4453-130">The provided data set contains the following columns:</span></span>

    - <span data-ttu-id="f4453-131">**vendor_id:** A ID do taxista é um recurso.</span><span class="sxs-lookup"><span data-stu-id="f4453-131">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
    - <span data-ttu-id="f4453-132">**rate_code:** O tipo de tarifa da corrida de táxi é um recurso.</span><span class="sxs-lookup"><span data-stu-id="f4453-132">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
    - <span data-ttu-id="f4453-133">**passenger_count:** O número de passageiros na corrida é um recurso.</span><span class="sxs-lookup"><span data-stu-id="f4453-133">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
    - <span data-ttu-id="f4453-134">**trip_time_in_secs:** O tempo que levou a corrida.</span><span class="sxs-lookup"><span data-stu-id="f4453-134">**trip_time_in_secs:** The amount of time the trip took.</span></span>
    - <span data-ttu-id="f4453-135">**trip_distance:** A distância da corrida é um recurso.</span><span class="sxs-lookup"><span data-stu-id="f4453-135">**trip_distance:** The distance of the trip is a feature.</span></span>
    - <span data-ttu-id="f4453-136">**payment_type:** A forma de pagamento (dinheiro ou cartão de crédito) é um recurso.</span><span class="sxs-lookup"><span data-stu-id="f4453-136">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
    - <span data-ttu-id="f4453-137">**fare_amount:** A tarifa total de táxi paga é o rótulo.</span><span class="sxs-lookup"><span data-stu-id="f4453-137">**fare_amount:** The total taxi fare paid is the label.</span></span>

<span data-ttu-id="f4453-138">O `label` é a coluna que você deseja prever.</span><span class="sxs-lookup"><span data-stu-id="f4453-138">The `label` is the column you want to predict.</span></span> <span data-ttu-id="f4453-139">Ao executar uma tarefa de regressão, o objetivo é prever um valor numérico.</span><span class="sxs-lookup"><span data-stu-id="f4453-139">When performing a regression task, the goal is to predict a numerical value.</span></span> <span data-ttu-id="f4453-140">Nesse cenário de previsão de preço, o custo de uma corrida de táxi está sendo previsto.</span><span class="sxs-lookup"><span data-stu-id="f4453-140">In this price prediction scenario, the cost of a taxi ride is being predicted.</span></span> <span data-ttu-id="f4453-141">Portanto, o **fare_amount** é o rótulo.</span><span class="sxs-lookup"><span data-stu-id="f4453-141">Therefore, the **fare_amount** is the label.</span></span> <span data-ttu-id="f4453-142">Os `features` identificados são as entradas que você atribui ao modelo para prever o `label`.</span><span class="sxs-lookup"><span data-stu-id="f4453-142">The identified `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="f4453-143">Nesse caso, o restante das colunas é usado como recursos ou entradas para prever o valor da tarifa.</span><span class="sxs-lookup"><span data-stu-id="f4453-143">In this case, the rest of the columns are used as features or inputs to predict the fare amount.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="f4453-144">Escolha um cenário</span><span class="sxs-lookup"><span data-stu-id="f4453-144">Choose a scenario</span></span>

<span data-ttu-id="f4453-145">Para treinar seu modelo, você precisa selecionar na lista de cenários disponíveis de aprendizado de máquina fornecidos pelo Construtor de Modelo.</span><span class="sxs-lookup"><span data-stu-id="f4453-145">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="f4453-146">Nesse caso, o cenário é `Price Prediction`.</span><span class="sxs-lookup"><span data-stu-id="f4453-146">In this case, the scenario is `Price Prediction`.</span></span>

1. <span data-ttu-id="f4453-147">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto *TaxiFarePrediction* e selecione **Adicionar** > **Aprendizado de Máquina**.</span><span class="sxs-lookup"><span data-stu-id="f4453-147">In **Solution Explorer**, right-click the *TaxiFarePrediction* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="f4453-148">Na etapa de cenário da ferramenta do Construtor de Modelo, selecione cenário de *Previsão de Preço*.</span><span class="sxs-lookup"><span data-stu-id="f4453-148">In the scenario step of the Model Builder tool, select *Price Prediction* scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="f4453-149">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="f4453-149">Load the data</span></span>

<span data-ttu-id="f4453-150">O Construtor de Modelo aceita dados de duas fontes: um banco de dados do SQL Server ou um arquivo local no formato csv ou tsv.</span><span class="sxs-lookup"><span data-stu-id="f4453-150">Model Builder accepts data from two sources, a SQL Server database or a local file in csv or tsv format.</span></span>

1. <span data-ttu-id="f4453-151">Na etapa de dados da ferramenta do Construtor de Modelo, selecione *Arquivo* na lista suspensa da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="f4453-151">In the data step of the Model Builder tool, select *File* from the data source dropdown.</span></span>
1. <span data-ttu-id="f4453-152">Selecione o botão ao lado da caixa de texto *Selecionar um arquivo* e use o Explorador de Arquivos para procurar e selecionar o *taxi-fare-test.csv* no diretório de *Dados*</span><span class="sxs-lookup"><span data-stu-id="f4453-152">Select the button next to the *Select a file* text box and use File Explorer to browse and select the *taxi-fare-test.csv* in the *Data* directory</span></span>
1. <span data-ttu-id="f4453-153">Escolha *fare_amount* na lista suspensa *Rótulo ou Coluna a Prever* e navegue para a etapa de treinamento da ferramenta do Construtor de Modelo.</span><span class="sxs-lookup"><span data-stu-id="f4453-153">Choose *fare_amount* in the *Label or Column to Predict* dropdown and navigate to the train step of the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="f4453-154">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="f4453-154">Train the model</span></span>

<span data-ttu-id="f4453-155">A tarefa de aprendizado de máquina usada para treinar o modelo de previsão de preço neste tutorial é a regressão.</span><span class="sxs-lookup"><span data-stu-id="f4453-155">The machine learning task used to train the price prediction model in this tutorial is regression.</span></span> <span data-ttu-id="f4453-156">Durante o processo de treinamento de modelo, o Construtor de Modelo treina modelos separados usando algoritmos de regressão diferentes e configurações para localizar o modelo com melhor desempenho para seu conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="f4453-156">During the model training process, Model Builder trains separate models using different regression algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="f4453-157">O tempo necessário para treinar o modelo é proporcional à quantidade de dados.</span><span class="sxs-lookup"><span data-stu-id="f4453-157">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="f4453-158">Use este gráfico como orientação para selecionar um valor adequado para o campo `Time to train (seconds)`:</span><span class="sxs-lookup"><span data-stu-id="f4453-158">Use this chart as guidance to select an adequate value for the `Time to train (seconds)` field:</span></span>

<span data-ttu-id="f4453-159">\*Tamanho do conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="f4453-159">\*Dataset Size</span></span>  | <span data-ttu-id="f4453-160">Tipo de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="f4453-160">Dataset Type</span></span>       | <span data-ttu-id="f4453-161">Média Hora de treinar\*</span><span class="sxs-lookup"><span data-stu-id="f4453-161">Avg. Time to train\*</span></span>
------------- | ------------------ | --------------
<span data-ttu-id="f4453-162">0 a 10 Mb</span><span class="sxs-lookup"><span data-stu-id="f4453-162">0 - 10 Mb</span></span>     | <span data-ttu-id="f4453-163">Numérico e texto</span><span class="sxs-lookup"><span data-stu-id="f4453-163">Numeric and Text</span></span>   | <span data-ttu-id="f4453-164">10 s</span><span class="sxs-lookup"><span data-stu-id="f4453-164">10 sec</span></span>
<span data-ttu-id="f4453-165">10 a 100 Mb</span><span class="sxs-lookup"><span data-stu-id="f4453-165">10 - 100 Mb</span></span>   | <span data-ttu-id="f4453-166">Numérico e texto</span><span class="sxs-lookup"><span data-stu-id="f4453-166">Numeric and Text</span></span>   | <span data-ttu-id="f4453-167">10 min</span><span class="sxs-lookup"><span data-stu-id="f4453-167">10 min</span></span>
<span data-ttu-id="f4453-168">100 a 500 Mb</span><span class="sxs-lookup"><span data-stu-id="f4453-168">100 - 500 Mb</span></span>  | <span data-ttu-id="f4453-169">Numérico e texto</span><span class="sxs-lookup"><span data-stu-id="f4453-169">Numeric and Text</span></span>   | <span data-ttu-id="f4453-170">30 min</span><span class="sxs-lookup"><span data-stu-id="f4453-170">30 min</span></span>
<span data-ttu-id="f4453-171">500 a 1 Gb</span><span class="sxs-lookup"><span data-stu-id="f4453-171">500 - 1 Gb</span></span>    | <span data-ttu-id="f4453-172">Numérico e texto</span><span class="sxs-lookup"><span data-stu-id="f4453-172">Numeric and Text</span></span>   | <span data-ttu-id="f4453-173">60 min</span><span class="sxs-lookup"><span data-stu-id="f4453-173">60 min</span></span>
<span data-ttu-id="f4453-174">Mais de 1 Gb</span><span class="sxs-lookup"><span data-stu-id="f4453-174">1 Gb+</span></span>         | <span data-ttu-id="f4453-175">Numérico e texto</span><span class="sxs-lookup"><span data-stu-id="f4453-175">Numeric and Text</span></span>   | <span data-ttu-id="f4453-176">Mais de 3 horas</span><span class="sxs-lookup"><span data-stu-id="f4453-176">3 hour+</span></span>

1. <span data-ttu-id="f4453-177">Como o arquivo de dados de treinamento é mais de 10MB, use 600 segundos (10 minutos) como o valor para *Tempo de treinamento (segundos)* .</span><span class="sxs-lookup"><span data-stu-id="f4453-177">Because the training data file is more than 10MB, use 600 seconds (10 minutes) as the value for *Time to train (seconds)*.</span></span>
2. <span data-ttu-id="f4453-178">Selecione *Iniciar Treinamento*.</span><span class="sxs-lookup"><span data-stu-id="f4453-178">Select *Start Training*.</span></span>

<span data-ttu-id="f4453-179">Durante o processo de treinamento, os dados de progresso são exibidos na seção `Progress` da etapa de treinamento.</span><span class="sxs-lookup"><span data-stu-id="f4453-179">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

- <span data-ttu-id="f4453-180">O status exibe o status de conclusão do processo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="f4453-180">Status displays the completion status of the training process.</span></span>
- <span data-ttu-id="f4453-181">A melhor precisão exibe a precisão do modelo de melhor desempenho encontrado pelo Construtor do Modelo até o momento.</span><span class="sxs-lookup"><span data-stu-id="f4453-181">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="f4453-182">Maior precisão significa que o modelo é previsto mais corretamente nos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="f4453-182">Higher accuracy means the model predicted more correctly on test data.</span></span>
- <span data-ttu-id="f4453-183">O melhor algoritmo exibe o nome do algoritmo de melhor desempenho executado encontrado pelo Construtor de Modelo até o momento.</span><span class="sxs-lookup"><span data-stu-id="f4453-183">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
- <span data-ttu-id="f4453-184">O último algoritmo exibe o nome do algoritmo usado mais recentemente pelo Construtor de Modelo para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="f4453-184">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

<span data-ttu-id="f4453-185">Após a conclusão do treinamento, navegue até a etapa de avaliação.</span><span class="sxs-lookup"><span data-stu-id="f4453-185">Once training is complete, navigate to the evaluate step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="f4453-186">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="f4453-186">Evaluate the model</span></span>

<span data-ttu-id="f4453-187">O resultado da etapa de treinamento será um modelo que tinha o melhor desempenho.</span><span class="sxs-lookup"><span data-stu-id="f4453-187">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="f4453-188">Na etapa de avaliação da ferramenta do Construtor de Modelo, a seção de saída terá o algoritmo usado pelo modelo com melhor desempenho na entrada *Melhor Modelo*, juntamente com as métricas na *Qualidade do Melhor Modelo (RSquared)* .</span><span class="sxs-lookup"><span data-stu-id="f4453-188">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the *Best Model* entry along with metrics in *Best Model Quality (RSquared)*.</span></span> <span data-ttu-id="f4453-189">Além disso, uma tabela de resumo contém os cinco modelos principais e suas métricas.</span><span class="sxs-lookup"><span data-stu-id="f4453-189">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="f4453-190">Se você não estiver satisfeito com suas métricas de precisão, algumas maneiras fáceis de experimentar e aprimorar a precisão do modelo serão aumentar a quantidade de tempo para treinar o modelo ou usar mais dados.</span><span class="sxs-lookup"><span data-stu-id="f4453-190">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="f4453-191">Ou navegue até a etapa do código.</span><span class="sxs-lookup"><span data-stu-id="f4453-191">Otherwise, navigate to the code step.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="f4453-192">Adicionar o código para fazer previsões</span><span class="sxs-lookup"><span data-stu-id="f4453-192">Add the code to make predictions</span></span>

<span data-ttu-id="f4453-193">Dois projetos serão criados como resultado do processo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="f4453-193">Two projects will be created as a result of the training process.</span></span>

- <span data-ttu-id="f4453-194">TaxiFarePredictionML.ConsoleApp: Um aplicativo do Console do .NET Core que contém o código de consumo e de modelo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="f4453-194">TaxiFarePredictionML.ConsoleApp: A .NET Core Console application that contains the model training and consumption code.</span></span>
- <span data-ttu-id="f4453-195">TaxiFarePredictionML.Model: Uma biblioteca de classes .NET Standard que contém os modelos de dados que definem o esquema de dados de modelo de entrada e saída, bem como a versão persistente do modelo com melhor desempenho durante o treinamento.</span><span class="sxs-lookup"><span data-stu-id="f4453-195">TaxiFarePredictionML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the persisted version of the best performing model during training.</span></span>

1. <span data-ttu-id="f4453-196">Na etapa de código da ferramenta do Construtor de Modelo, escolha **Adicionar Projetos** para adicionar os projetos gerados automaticamente à solução.</span><span class="sxs-lookup"><span data-stu-id="f4453-196">In the code step of the Model Builder tool, select **Add Projects** to add the auto-generated projects to the solution.</span></span>
1. <span data-ttu-id="f4453-197">Clique com botão direito do mouse no projeto *TaxiFarePrediction*.</span><span class="sxs-lookup"><span data-stu-id="f4453-197">Right-click *TaxiFarePrediction* project.</span></span> <span data-ttu-id="f4453-198">Em seguida, **Adicionar > Referência**.</span><span class="sxs-lookup"><span data-stu-id="f4453-198">Then, **Add > Reference**.</span></span> <span data-ttu-id="f4453-199">Escolha o nó **Projetos > Solução** e, na lista, confira o projeto *TaxiFarePredictionML.Model* e selecione OK.</span><span class="sxs-lookup"><span data-stu-id="f4453-199">Choose the **Projects > Solution** node and from the list, check the *TaxiFarePredictionML.Model* project and select OK.</span></span>
1. <span data-ttu-id="f4453-200">Abra o arquivo *Program.cs* no projeto *TaxiFarePrediction*.</span><span class="sxs-lookup"><span data-stu-id="f4453-200">Open the *Program.cs* file in the *TaxiFarePrediction* project.</span></span>
1. <span data-ttu-id="f4453-201">Adicione o seguinte usando instruções para fazer referência ao pacote NuGet *Microsoft.ML* e ao projeto *TaxiFarePredictionML.Model*:</span><span class="sxs-lookup"><span data-stu-id="f4453-201">Add the following using statements to reference the *Microsoft.ML* NuGet package and *TaxiFarePredictionML.Model* project:</span></span>

    ```csharp
    using System;
    using Microsoft.ML;
    using TaxiFarePredictionML.Model.DataModels;
    ```

1. <span data-ttu-id="f4453-202">Adicione o método `ConsumeModel` à classe `Program`.</span><span class="sxs-lookup"><span data-stu-id="f4453-202">Add the `ConsumeModel` method to the `Program` class.</span></span>

    ```csharp
    static ModelOutput ConsumeModel(ModelInput input)
    {
        // 1. Load the model
        MLContext mlContext = new MLContext();
        ITransformer mlModel = mlContext.Model.Load("MLModel.zip", out var modelInputSchema);

        // 2. Create PredictionEngine
        var predictionEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(mlModel);

        // 3. Use PredictionEngine to use model on input data
        ModelOutput result = predictionEngine.Predict(input);

        // 4. Return prediction result
        return result;
    }
    ```

    <span data-ttu-id="f4453-203">O `ConsumeModel` vai carregar o modelo treinado, criar um [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) para o modelo e usá-lo para fazer previsões sobre novos dados.</span><span class="sxs-lookup"><span data-stu-id="f4453-203">The `ConsumeModel` will load the trained model, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) for the model and use it to make predictions on new data.</span></span>

1. <span data-ttu-id="f4453-204">Para fazer uma previsão sobre novos dados usando o modelo, crie uma nova instância da classe `ModelInput` e use o método `ConsumeModel`.</span><span class="sxs-lookup"><span data-stu-id="f4453-204">To make a prediction on new data using the model, create a new instance of the `ModelInput` class and use the `ConsumeModel` method.</span></span> <span data-ttu-id="f4453-205">Observe que o valor da tarifa não faz parte da entrada.</span><span class="sxs-lookup"><span data-stu-id="f4453-205">Notice that the fare amount is not part of the input.</span></span> <span data-ttu-id="f4453-206">Isso acontece porque o modelo gerará a previsão para ela.</span><span class="sxs-lookup"><span data-stu-id="f4453-206">This is because the model will generate the prediction for it.</span></span> <span data-ttu-id="f4453-207">Adicionar o código a seguir ao método `Main` para executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="f4453-207">Add the following code to the `Main` method and run the application</span></span>

    ```csharp
    // Create sample data
    ModelInput input = new ModelInput()
    {
        Vendor_id = "CMT",
        Rate_code = 1,
        Passenger_count = 1,
        Trip_time_in_secs = 1271,
        Trip_distance = 3.8f,
        Payment_type = "CRD"
    };

    // Make prediction
    ModelOutput prediction = ConsumeModel(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

    <span data-ttu-id="f4453-208">A saída gerada pelo programa deve ser semelhante ao snippet a seguir:</span><span class="sxs-lookup"><span data-stu-id="f4453-208">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Fare: 16.82245
    ```

<span data-ttu-id="f4453-209">Se precisar fazer referência aos projetos gerados em um momento posterior dentro de outra solução, você poderá encontrá-los no diretório `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`.</span><span class="sxs-lookup"><span data-stu-id="f4453-209">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f4453-210">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="f4453-210">Next Steps</span></span>

<span data-ttu-id="f4453-211">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="f4453-211">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="f4453-212">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="f4453-212">Prepare and understand the data</span></span>
> - <span data-ttu-id="f4453-213">Escolha um cenário</span><span class="sxs-lookup"><span data-stu-id="f4453-213">Choose a scenario</span></span>
> - <span data-ttu-id="f4453-214">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="f4453-214">Load the data</span></span>
> - <span data-ttu-id="f4453-215">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="f4453-215">Train the model</span></span>
> - <span data-ttu-id="f4453-216">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="f4453-216">Evaluate the model</span></span>
> - <span data-ttu-id="f4453-217">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="f4453-217">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f4453-218">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="f4453-218">Additional Resources</span></span>

<span data-ttu-id="f4453-219">Para saber mais sobre os tópicos mencionados neste tutorial, visite os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="f4453-219">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="f4453-220">Cenários do Construtor de Modelo</span><span class="sxs-lookup"><span data-stu-id="f4453-220">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="f4453-221">Regressão</span><span class="sxs-lookup"><span data-stu-id="f4453-221">Regression</span></span>](../resources/glossary.md#regression)
- [<span data-ttu-id="f4453-222">Métricas do Modelo de Regressão</span><span class="sxs-lookup"><span data-stu-id="f4453-222">Regression Model Metrics</span></span>](../resources/metrics.md#metrics-for-regression)
- [<span data-ttu-id="f4453-223">Conjunto de dados Corrida de Táxi da NYC TLC</span><span class="sxs-lookup"><span data-stu-id="f4453-223">NYC TLC Taxi Trip data set</span></span>](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)
