---
title: Prever os preços usando regressão com o Construtor de Modelo
description: Este tutorial mostra como criar um modelo de regressão usando o Construtor de Modelo do ML.NET para prever os preços, especificamente, as tarifas de táxi de Nova York.
author: luisquintanilla
ms.author: luquinta
ms.date: 06/26/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: db9788e3065a0f2f21d712b2d4826efea2d8a829
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410574"
---
# <a name="predict-prices-using-regression-with-model-builder"></a><span data-ttu-id="cf093-103">Prever os preços usando regressão com o Construtor de Modelo</span><span class="sxs-lookup"><span data-stu-id="cf093-103">Predict prices using regression with Model Builder</span></span>

<span data-ttu-id="cf093-104">Saiba como usar o Construtor de Modelo do ML.NET para criar um [modelo de regressão](../resources/glossary.md#regression) e prever preços.</span><span class="sxs-lookup"><span data-stu-id="cf093-104">Learn how to use ML.NET Model Builder to build a [regression model](../resources/glossary.md#regression) to predict prices.</span></span>  <span data-ttu-id="cf093-105">O aplicativo de console do .NET que você desenvolve neste tutorial prevê as tarifas de táxi com base em dados históricos de tarifas de táxi em Nova York.</span><span class="sxs-lookup"><span data-stu-id="cf093-105">The .NET console app that you develop in this tutorial predicts taxi fares based on historical New York taxi fare data.</span></span>

<span data-ttu-id="cf093-106">O modelo de previsão de preço do Construtor de Modelo pode ser usado em qualquer cenário que exija um valor de previsão numérico.</span><span class="sxs-lookup"><span data-stu-id="cf093-106">The Model Builder price prediction template can be used for any scenario requiring a numerical prediction value.</span></span> <span data-ttu-id="cf093-107">Exemplos de cenários incluem: previsão de preço, previsão de demanda e previsão de vendas de casas.</span><span class="sxs-lookup"><span data-stu-id="cf093-107">Example scenarios include: house price prediction, demand prediction, and sales forecasting.</span></span>

<span data-ttu-id="cf093-108">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="cf093-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="cf093-109">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="cf093-109">Prepare and understand the data</span></span>
> * <span data-ttu-id="cf093-110">Escolha um cenário</span><span class="sxs-lookup"><span data-stu-id="cf093-110">Choose a scenario</span></span>
> * <span data-ttu-id="cf093-111">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="cf093-111">Load the data</span></span>
> * <span data-ttu-id="cf093-112">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="cf093-112">Train the model</span></span>
> * <span data-ttu-id="cf093-113">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="cf093-113">Evaluate the model</span></span>
> * <span data-ttu-id="cf093-114">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="cf093-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="cf093-115">O Construtor de Modelo está atualmente na Versão Prévia.</span><span class="sxs-lookup"><span data-stu-id="cf093-115">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="cf093-116">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="cf093-116">Pre-requisites</span></span>

<span data-ttu-id="cf093-117">Para obter uma lista de pré-requisitos e instruções de instalação, visite o [guia de instalação do Construtor de Modelo](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="cf093-117">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="cf093-118">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="cf093-118">Create a console application</span></span>

1. <span data-ttu-id="cf093-119">Crie um **Aplicativo de Console do .NET Core** chamado "TaxiFarePrediction".</span><span class="sxs-lookup"><span data-stu-id="cf093-119">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

1. <span data-ttu-id="cf093-120">Instale o pacote NuGet **Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="cf093-120">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="cf093-121">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto *TaxiFarePrediction* e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="cf093-121">In **Solution Explorer**, right-click the *TaxiFarePrediction* project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="cf093-122">Escolha "nuget.org" como a origem do pacote, selecione a guia **Procurar**, pesquise por **Microsoft.ML**, selecione o pacote na lista e selecione o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="cf093-122">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="cf093-123">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="cf093-123">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="cf093-124">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="cf093-124">Prepare and understand the data</span></span>

1. <span data-ttu-id="cf093-125">Crie um diretório chamado *Data* no projeto para armazenar os arquivos do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="cf093-125">Create a directory named *Data* in your project to store the data set files.</span></span>

1. <span data-ttu-id="cf093-126">Baixe o conjunto de dados [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) e salve-o na pasta *Dados* criada na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="cf093-126">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) data set and save it to the *Data* folder you created at the previous step.</span></span> <span data-ttu-id="cf093-127">Esse conjunto de dados é usado para treinar e avaliar o modelo de machine learning.</span><span class="sxs-lookup"><span data-stu-id="cf093-127">This data set is used to train and evaluate the machine learning model.</span></span> <span data-ttu-id="cf093-128">Esse conjunto de dados é originalmente do [Conjunto de dados NYC TLC Taxi Trip](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="cf093-128">This data set is originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

1. <span data-ttu-id="cf093-129">No **Gerenciador de Soluções**, clique com o botão direito do mouse no arquivo *taxi-fare-train.csv* e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="cf093-129">In **Solution Explorer**, right-click the *taxi-fare-train.csv* file and select **Properties**.</span></span> <span data-ttu-id="cf093-130">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.</span><span class="sxs-lookup"><span data-stu-id="cf093-130">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="cf093-131">Cada linha no conjunto de dados `taxi-fare-train.csv` contém os detalhes de corridas feitas por um táxi.</span><span class="sxs-lookup"><span data-stu-id="cf093-131">Each row in the `taxi-fare-train.csv` data set contains details of trips made by a taxi.</span></span> 

1. <span data-ttu-id="cf093-132">Abra o conjunto de dados **taxi-fare-train.csv**</span><span class="sxs-lookup"><span data-stu-id="cf093-132">Open the **taxi-fare-train.csv** data set</span></span>

    <span data-ttu-id="cf093-133">O conjunto de dados fornecido contém as seguintes colunas:</span><span class="sxs-lookup"><span data-stu-id="cf093-133">The provided data set contains the following columns:</span></span>

    * <span data-ttu-id="cf093-134">**vendor_id:** A ID do taxista é um recurso.</span><span class="sxs-lookup"><span data-stu-id="cf093-134">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
    * <span data-ttu-id="cf093-135">**rate_code:** O tipo de tarifa da corrida de táxi é um recurso.</span><span class="sxs-lookup"><span data-stu-id="cf093-135">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
    * <span data-ttu-id="cf093-136">**passenger_count:** O número de passageiros na corrida é um recurso.</span><span class="sxs-lookup"><span data-stu-id="cf093-136">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
    * <span data-ttu-id="cf093-137">**trip_time_in_secs:** O tempo que levou a corrida.</span><span class="sxs-lookup"><span data-stu-id="cf093-137">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="cf093-138">Você deseja prever a tarifa da viagem antes de sua conclusão.</span><span class="sxs-lookup"><span data-stu-id="cf093-138">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="cf093-139">No momento, você não sabe a duração da viagem.</span><span class="sxs-lookup"><span data-stu-id="cf093-139">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="cf093-140">Portanto, o tempo da viagem não é um recurso e você excluirá essa coluna do modelo.</span><span class="sxs-lookup"><span data-stu-id="cf093-140">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
    * <span data-ttu-id="cf093-141">**trip_distance:** A distância da corrida é um recurso.</span><span class="sxs-lookup"><span data-stu-id="cf093-141">**trip_distance:** The distance of the trip is a feature.</span></span>
    * <span data-ttu-id="cf093-142">**payment_type:** A forma de pagamento (dinheiro ou cartão de crédito) é um recurso.</span><span class="sxs-lookup"><span data-stu-id="cf093-142">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
    * <span data-ttu-id="cf093-143">**fare_amount:** A tarifa total de táxi paga é o rótulo.</span><span class="sxs-lookup"><span data-stu-id="cf093-143">**fare_amount:** The total taxi fare paid is the label.</span></span>

<span data-ttu-id="cf093-144">O `label` é a coluna que você deseja prever.</span><span class="sxs-lookup"><span data-stu-id="cf093-144">The `label` is the column you want to predict.</span></span> <span data-ttu-id="cf093-145">Ao executar uma tarefa de regressão, o objetivo é prever um valor numérico.</span><span class="sxs-lookup"><span data-stu-id="cf093-145">When performing a regression task, the goal is to predict a numerical value.</span></span> <span data-ttu-id="cf093-146">Nesse cenário de previsão de preço, o custo de uma corrida de táxi está sendo previsto.</span><span class="sxs-lookup"><span data-stu-id="cf093-146">In this price prediction scenario, the cost of a taxi ride is being predicted.</span></span> <span data-ttu-id="cf093-147">Portanto, o **fare_amount** é o rótulo.</span><span class="sxs-lookup"><span data-stu-id="cf093-147">Therefore, the **fare_amount** is the label.</span></span> <span data-ttu-id="cf093-148">Os `features` identificados são as entradas que você atribui ao modelo para prever o `label`.</span><span class="sxs-lookup"><span data-stu-id="cf093-148">The identified `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="cf093-149">Nesse caso, o restante das colunas é usado como recursos ou entradas para prever o valor da tarifa.</span><span class="sxs-lookup"><span data-stu-id="cf093-149">In this case, the rest of the columns are used as features or inputs to predict the fare amount.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="cf093-150">Escolha um cenário</span><span class="sxs-lookup"><span data-stu-id="cf093-150">Choose a scenario</span></span>

<span data-ttu-id="cf093-151">Para treinar seu modelo, você precisa selecionar na lista de cenários disponíveis de aprendizado de máquina fornecidos pelo Construtor de Modelo.</span><span class="sxs-lookup"><span data-stu-id="cf093-151">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="cf093-152">Nesse caso, o cenário é `Price Prediction`.</span><span class="sxs-lookup"><span data-stu-id="cf093-152">In this case, the scenario is `Price Prediction`.</span></span> <span data-ttu-id="cf093-153">Para obter uma lista mais abrangente, visite o [artigo de visão geral do Construtor de Modelo](../automate-training-with-model-builder.md#scenarios).</span><span class="sxs-lookup"><span data-stu-id="cf093-153">For a more extensive list visit the [Model Builder overview article](../automate-training-with-model-builder.md#scenarios).</span></span>

1. <span data-ttu-id="cf093-154">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto *TaxiFarePrediction* e selecione **Adicionar** > **Aprendizado de Máquina**.</span><span class="sxs-lookup"><span data-stu-id="cf093-154">In **Solution Explorer**, right-click the *TaxiFarePrediction* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="cf093-155">Na etapa de cenário da ferramenta do Construtor de Modelo, selecione cenário de *Previsão de Preço*.</span><span class="sxs-lookup"><span data-stu-id="cf093-155">In the scenario step of the Model Builder tool, select *Price Prediction* scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="cf093-156">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="cf093-156">Load the data</span></span>

<span data-ttu-id="cf093-157">O Construtor do Modelo aceita dados de duas fontes: um banco de dados do SQL Server ou um arquivo local csv ou tsv.</span><span class="sxs-lookup"><span data-stu-id="cf093-157">Model Builder accepts data from two sources, a SQL Server database or a local file csv or tsv file.</span></span> <span data-ttu-id="cf093-158">Para obter mais informações sobre os requisitos de formato de dados, visite o seguinte [link](../how-to-guides/install-model-builder.md#limitations).</span><span class="sxs-lookup"><span data-stu-id="cf093-158">For more information on data format requirements, visit the following [link](../how-to-guides/install-model-builder.md#limitations).</span></span>

1. <span data-ttu-id="cf093-159">Na etapa de dados da ferramenta do Construtor de Modelo, selecione *Arquivo* na lista suspensa da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="cf093-159">In the data step of the Model Builder tool, select *File* from the data source dropdown.</span></span>
1. <span data-ttu-id="cf093-160">Selecione o botão ao lado da caixa de texto *Selecionar um arquivo* e use o Explorador de Arquivos para procurar e selecionar o *taxi-fare-test.csv* no diretório de *Dados*</span><span class="sxs-lookup"><span data-stu-id="cf093-160">Select the button next to the *Select a file* text box and use File Explorer to browse and select the *taxi-fare-test.csv* in the *Data* directory</span></span>
1. <span data-ttu-id="cf093-161">Escolha *fare_amount* na lista suspensa *Rótulo ou Coluna a Prever* e navegue para a etapa de treinamento da ferramenta do Construtor de Modelo.</span><span class="sxs-lookup"><span data-stu-id="cf093-161">Choose *fare_amount* in the *Label or Column to Predict* dropdown and navigate to the train step of the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="cf093-162">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="cf093-162">Train the model</span></span>

<span data-ttu-id="cf093-163">A tarefa de aprendizado de máquina usada para treinar o modelo de previsão de preço neste tutorial é a regressão.</span><span class="sxs-lookup"><span data-stu-id="cf093-163">The machine learning task used to train the price prediction model in this tutorial is regression.</span></span> <span data-ttu-id="cf093-164">Durante o processo de treinamento de modelo, o Construtor de Modelo treina modelos separados usando algoritmos de regressão diferentes e configurações para localizar o modelo com melhor desempenho para seu conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="cf093-164">During the model training process, Model Builder trains separate models using different regression algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="cf093-165">O tempo necessário para treinar o modelo é proporcional à quantidade de dados.</span><span class="sxs-lookup"><span data-stu-id="cf093-165">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="cf093-166">Use este gráfico como orientação para selecionar um valor adequado para o campo `Time to train (seconds)`:</span><span class="sxs-lookup"><span data-stu-id="cf093-166">Use this chart as guidance to select an adequate value for the `Time to train (seconds)` field:</span></span>

<span data-ttu-id="cf093-167">\*Tamanho do conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="cf093-167">\*Dataset Size</span></span>  | <span data-ttu-id="cf093-168">Tipo de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="cf093-168">Dataset Type</span></span>       | <span data-ttu-id="cf093-169">Média Hora de treinar\*</span><span class="sxs-lookup"><span data-stu-id="cf093-169">Avg. Time to train\*</span></span>
------------- | ------------------ | --------------
<span data-ttu-id="cf093-170">0 a 10 Mb</span><span class="sxs-lookup"><span data-stu-id="cf093-170">0 - 10 Mb</span></span>     | <span data-ttu-id="cf093-171">Numérico e texto</span><span class="sxs-lookup"><span data-stu-id="cf093-171">Numeric and Text</span></span>   | <span data-ttu-id="cf093-172">10 s</span><span class="sxs-lookup"><span data-stu-id="cf093-172">10 sec</span></span>
<span data-ttu-id="cf093-173">10 a 100 Mb</span><span class="sxs-lookup"><span data-stu-id="cf093-173">10 - 100 Mb</span></span>   | <span data-ttu-id="cf093-174">Numérico e texto</span><span class="sxs-lookup"><span data-stu-id="cf093-174">Numeric and Text</span></span>   | <span data-ttu-id="cf093-175">10 min</span><span class="sxs-lookup"><span data-stu-id="cf093-175">10 min</span></span>
<span data-ttu-id="cf093-176">100 a 500 Mb</span><span class="sxs-lookup"><span data-stu-id="cf093-176">100 - 500 Mb</span></span>  | <span data-ttu-id="cf093-177">Numérico e texto</span><span class="sxs-lookup"><span data-stu-id="cf093-177">Numeric and Text</span></span>   | <span data-ttu-id="cf093-178">30 min</span><span class="sxs-lookup"><span data-stu-id="cf093-178">30 min</span></span>
<span data-ttu-id="cf093-179">500 a 1 Gb</span><span class="sxs-lookup"><span data-stu-id="cf093-179">500 - 1 Gb</span></span>    | <span data-ttu-id="cf093-180">Numérico e texto</span><span class="sxs-lookup"><span data-stu-id="cf093-180">Numeric and Text</span></span>   | <span data-ttu-id="cf093-181">60 min</span><span class="sxs-lookup"><span data-stu-id="cf093-181">60 min</span></span>
<span data-ttu-id="cf093-182">Mais de 1 Gb</span><span class="sxs-lookup"><span data-stu-id="cf093-182">1 Gb+</span></span>         | <span data-ttu-id="cf093-183">Numérico e texto</span><span class="sxs-lookup"><span data-stu-id="cf093-183">Numeric and Text</span></span>   | <span data-ttu-id="cf093-184">Mais de 3 horas</span><span class="sxs-lookup"><span data-stu-id="cf093-184">3 hour+</span></span>

1. <span data-ttu-id="cf093-185">Como o arquivo de dados de treinamento é mais de 10MB, use 600 segundos (10 minutos) como o valor para *Tempo de treinamento (segundos)* .</span><span class="sxs-lookup"><span data-stu-id="cf093-185">Because the training data file is more than 10MB, use 600 seconds (10 minutes) as the value for *Time to train (seconds)*.</span></span>
2. <span data-ttu-id="cf093-186">Selecione *Iniciar Treinamento*.</span><span class="sxs-lookup"><span data-stu-id="cf093-186">Select *Start Training*.</span></span>

<span data-ttu-id="cf093-187">Durante o processo de treinamento, os dados de progresso são exibidos na seção `Progress` da etapa de treinamento.</span><span class="sxs-lookup"><span data-stu-id="cf093-187">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

- <span data-ttu-id="cf093-188">O status exibe o status de conclusão do processo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="cf093-188">Status displays the completion status of the training process.</span></span>
- <span data-ttu-id="cf093-189">A melhor precisão exibe a precisão do modelo de melhor desempenho encontrado pelo Construtor do Modelo até o momento.</span><span class="sxs-lookup"><span data-stu-id="cf093-189">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="cf093-190">Maior precisão significa que o modelo é previsto mais corretamente nos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="cf093-190">Higher accuracy means the model predicted more correctly on test data.</span></span> 
- <span data-ttu-id="cf093-191">O melhor algoritmo exibe o nome do algoritmo de melhor desempenho executado encontrado pelo Construtor de Modelo até o momento.</span><span class="sxs-lookup"><span data-stu-id="cf093-191">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
- <span data-ttu-id="cf093-192">O último algoritmo exibe o nome do algoritmo usado mais recentemente pelo Construtor de Modelo para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="cf093-192">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

<span data-ttu-id="cf093-193">Após a conclusão do treinamento, navegue até a etapa de avaliação.</span><span class="sxs-lookup"><span data-stu-id="cf093-193">Once training is complete, navigate to the evaluate step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="cf093-194">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="cf093-194">Evaluate the model</span></span>

<span data-ttu-id="cf093-195">O resultado da etapa de treinamento será um modelo que tinha o melhor desempenho.</span><span class="sxs-lookup"><span data-stu-id="cf093-195">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="cf093-196">Na etapa de avaliação da ferramenta do Construtor de Modelo, a seção de saída terá o algoritmo usado pelo modelo com melhor desempenho na entrada *Melhor Modelo*, juntamente com as métricas na *Qualidade do Melhor Modelo (RSquared)* .</span><span class="sxs-lookup"><span data-stu-id="cf093-196">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the *Best Model* entry along with metrics in *Best Model Quality (RSquared)*.</span></span> <span data-ttu-id="cf093-197">Além disso, uma tabela de resumo contém os cinco modelos principais e suas métricas.</span><span class="sxs-lookup"><span data-stu-id="cf093-197">Additionally, a summary table containing top five models and their metrics.</span></span> <span data-ttu-id="cf093-198">Visite o link a seguir para saber mais sobre [métricas de modelo de avaliação](https://docs.microsoft.com/dotnet/machine-learning/resources/metrics).</span><span class="sxs-lookup"><span data-stu-id="cf093-198">Visit the following link to learn more about [evaluating model metrics](https://docs.microsoft.com/dotnet/machine-learning/resources/metrics).</span></span>

<span data-ttu-id="cf093-199">Se você não estiver satisfeito com suas métricas de precisão, algumas maneiras fáceis de experimentar e aprimorar a precisão do modelo serão aumentar a quantidade de tempo para treinar o modelo ou usar mais dados.</span><span class="sxs-lookup"><span data-stu-id="cf093-199">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span>

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="cf093-200">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="cf093-200">Use the model for predictions</span></span>

<span data-ttu-id="cf093-201">Dois projetos serão criados como resultado do processo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="cf093-201">Two projects will be created as a result of the training process.</span></span>

- <span data-ttu-id="cf093-202">TaxiFarePredictionML.ConsoleApp: Um aplicativo do Console do .NET que contém o código de consumo e de modelo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="cf093-202">TaxiFarePredictionML.ConsoleApp: A .NET Console application that contains the model training and consumption code.</span></span>
- <span data-ttu-id="cf093-203">TaxiFarePredictionML.Model: Uma biblioteca de classes .NET Standard que contém os modelos de dados que definem o esquema de dados de modelo de entrada e saída, bem como a versão persistente do modelo com melhor desempenho durante o treinamento.</span><span class="sxs-lookup"><span data-stu-id="cf093-203">TaxiFarePredictionML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the persisted version of the best performing model during training.</span></span>

1. <span data-ttu-id="cf093-204">Na seção de código da ferramenta do Construtor de Modelo, selecione **Projetos Adicionados** para adicionar os projetos à solução.</span><span class="sxs-lookup"><span data-stu-id="cf093-204">In the code section of the Model Builder tool, select **Added Projects** to add the projects to the solution.</span></span>
1. <span data-ttu-id="cf093-205">No gerenciador de soluções, clique com o botão direito do mouse no projeto *TaxiFarePrediction*.</span><span class="sxs-lookup"><span data-stu-id="cf093-205">In solution explorer, right-click the *TaxiFarePrediction* project.</span></span> <span data-ttu-id="cf093-206">Em seguida, selecione **Adicionar > Item Existente**.</span><span class="sxs-lookup"><span data-stu-id="cf093-206">Then, select **Add > Existing Item**.</span></span> <span data-ttu-id="cf093-207">Para a lista suspensa de tipo de arquivo, selecione `All Files`, navegue até o diretório do projeto *TaxiFarePredictionML.Model* e selecione o arquivo `MLModel.zip`.</span><span class="sxs-lookup"><span data-stu-id="cf093-207">For file type drop down, select `All Files`, navigate to the *TaxiFarePredictionML.Model* project directory and select the `MLModel.zip` file.</span></span> <span data-ttu-id="cf093-208">Em seguida, clique com o botão direito do mouse no arquivo `MLModel.zip` adicionado e selecione *Propriedades*.</span><span class="sxs-lookup"><span data-stu-id="cf093-208">Then right-click the recently added `MLModel.zip` file and select *Properties*.</span></span> <span data-ttu-id="cf093-209">Para a opção Copiar para Diretório de Saída, selecione *Copiar se for mais recente* na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="cf093-209">For the Copy to Output Directory option, select *Copy if Newer* from the dropdown.</span></span>
1. <span data-ttu-id="cf093-210">Clique com botão direito do mouse no projeto *TaxiFarePrediction*.</span><span class="sxs-lookup"><span data-stu-id="cf093-210">Right-click *TaxiFarePrediction* project.</span></span> <span data-ttu-id="cf093-211">Em seguida, **Adicionar > Referência**.</span><span class="sxs-lookup"><span data-stu-id="cf093-211">Then, **Add > Reference**.</span></span> <span data-ttu-id="cf093-212">Escolha o nó **Projetos > Solução** e, na lista, confira o projeto *TaxiFarePredictionML.Model* e selecione OK.</span><span class="sxs-lookup"><span data-stu-id="cf093-212">Choose the **Projects > Solution** node and from the list, check the *TaxiFarePredictionML.Model* project and select OK.</span></span>

4. <span data-ttu-id="cf093-213">Abra o arquivo *Program.cs* no projeto *TaxiFarePrediction*.</span><span class="sxs-lookup"><span data-stu-id="cf093-213">Open the *Program.cs* file in the *TaxiFarePrediction* project.</span></span>
5. <span data-ttu-id="cf093-214">Adicione as seguintes instruções using:</span><span class="sxs-lookup"><span data-stu-id="cf093-214">Add the following using statements:</span></span>

    ```csharp
    using System;
    using Microsoft.ML;
    using TaxiFarePredictionML.Model.DataModels;
    ```

6. <span data-ttu-id="cf093-215">Adicione o método `ConsumeModel` à classe `Program`.</span><span class="sxs-lookup"><span data-stu-id="cf093-215">Add the `ConsumeModel` method to the `Program` class.</span></span> <span data-ttu-id="cf093-216">O `ConsumeModel` criará um `PredictionEngine` com base no modelo gerado pelo Construtor de Modelo para fazer previsões sobre novos dados e imprimi-las no console.</span><span class="sxs-lookup"><span data-stu-id="cf093-216">The `ConsumeModel` will create a `PredictionEngine` based on the model generated by Model Builder to make predictions on new data and print them out to the console.</span></span>

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

7. <span data-ttu-id="cf093-217">Adicione o código a seguir ao método `Main` para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf093-217">Add the following code to the `Main` method and run the application.</span></span>

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

    <span data-ttu-id="cf093-218">A saída gerada pelo programa deve ser semelhante ao trecho a seguir:</span><span class="sxs-lookup"><span data-stu-id="cf093-218">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Fare: 16.82245
    ```

<span data-ttu-id="cf093-219">Se precisar fazer referência aos projetos gerados em um momento posterior dentro de outra solução, você poderá encontrá-los no diretório `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`.</span><span class="sxs-lookup"><span data-stu-id="cf093-219">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="cf093-220">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="cf093-220">Next Steps</span></span>

<span data-ttu-id="cf093-221">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="cf093-221">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="cf093-222">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="cf093-222">Prepare and understand the data</span></span>
> * <span data-ttu-id="cf093-223">Escolha um cenário</span><span class="sxs-lookup"><span data-stu-id="cf093-223">Choose a scenario</span></span>
> * <span data-ttu-id="cf093-224">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="cf093-224">Load the data</span></span>
> * <span data-ttu-id="cf093-225">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="cf093-225">Train the model</span></span>
> * <span data-ttu-id="cf093-226">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="cf093-226">Evaluate the model</span></span>
> * <span data-ttu-id="cf093-227">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="cf093-227">Use the model for predictions</span></span>

<span data-ttu-id="cf093-228">Avance para qualquer um dos artigos de instruções a seguir para aprender a implantar seu modelo.</span><span class="sxs-lookup"><span data-stu-id="cf093-228">Advance to either of the following how-to articles to learn how to deploy your model.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cf093-229">Implantar um modelo no Azure Functions</span><span class="sxs-lookup"><span data-stu-id="cf093-229">Deploy a model to Azure Functions</span></span>](../how-to-guides/serve-model-serverless-azure-functions-ml-net.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="cf093-230">Implantar um modelo em uma API Web</span><span class="sxs-lookup"><span data-stu-id="cf093-230">Deploy a model to a Web API</span></span>](../how-to-guides/serve-model-web-api-ml-net.md)
