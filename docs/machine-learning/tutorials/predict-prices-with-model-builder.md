---
title: 'Tutorial: prever os preços usando a regressão com o construtor de modelos'
description: Este tutorial mostra como criar um modelo de regressão usando o Construtor de Modelo do ML.NET para prever os preços, especificamente, as tarifas de táxi de Nova York.
author: luisquintanilla
ms.author: luquinta
ms.date: 10/08/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 314b637b4a43725f6daeefa6097544567dcaabc2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124304"
---
# <a name="tutorial-predict-prices-using-regression-with-model-builder"></a><span data-ttu-id="7e9dd-103">Tutorial: prever os preços usando a regressão com o construtor de modelos</span><span class="sxs-lookup"><span data-stu-id="7e9dd-103">Tutorial: Predict prices using regression with Model Builder</span></span>

<span data-ttu-id="7e9dd-104">Saiba como usar o ML.NET Model Builder para criar um modelo de regressão para prever os preços.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-104">Learn how to use ML.NET Model Builder to build a regression model to predict prices.</span></span>  <span data-ttu-id="7e9dd-105">O aplicativo de console do .NET que você desenvolve neste tutorial prevê as tarifas de táxi com base em dados históricos de tarifas de táxi em Nova York.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-105">The .NET console app that you develop in this tutorial predicts taxi fares based on historical New York taxi fare data.</span></span>

<span data-ttu-id="7e9dd-106">O modelo de previsão de preço do Construtor de Modelo pode ser usado em qualquer cenário que exija um valor de previsão numérico.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-106">The Model Builder price prediction template can be used for any scenario requiring a numerical prediction value.</span></span> <span data-ttu-id="7e9dd-107">Exemplos de cenários incluem: previsão de preço, previsão de demanda e previsão de vendas de casas.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-107">Example scenarios include: house price prediction, demand prediction, and sales forecasting.</span></span>

<span data-ttu-id="7e9dd-108">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="7e9dd-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="7e9dd-109">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="7e9dd-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="7e9dd-110">Escolha um cenário</span><span class="sxs-lookup"><span data-stu-id="7e9dd-110">Choose a scenario</span></span>
> - <span data-ttu-id="7e9dd-111">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="7e9dd-111">Load the data</span></span>
> - <span data-ttu-id="7e9dd-112">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="7e9dd-112">Train the model</span></span>
> - <span data-ttu-id="7e9dd-113">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="7e9dd-113">Evaluate the model</span></span>
> - <span data-ttu-id="7e9dd-114">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="7e9dd-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="7e9dd-115">O Construtor de Modelo está atualmente na Versão Prévia.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-115">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="7e9dd-116">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="7e9dd-116">Pre-requisites</span></span>

<span data-ttu-id="7e9dd-117">Para obter uma lista de pré-requisitos e instruções de instalação, visite o [guia de instalação do Construtor de Modelo](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="7e9dd-117">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="7e9dd-118">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="7e9dd-118">Create a console application</span></span>

1. <span data-ttu-id="7e9dd-119">Crie um **Aplicativo de Console do .NET Core** chamado "TaxiFarePrediction".</span><span class="sxs-lookup"><span data-stu-id="7e9dd-119">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="7e9dd-120">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="7e9dd-120">Prepare and understand the data</span></span>

1. <span data-ttu-id="7e9dd-121">Crie um diretório chamado *Data* no projeto para armazenar os arquivos do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-121">Create a directory named *Data* in your project to store the data set files.</span></span>

1. <span data-ttu-id="7e9dd-122">O conjunto de dados usado para treinar e avaliar o modelo de machine learning pertence originalmente ao conjunto de dados Corrida de Táxi da NYC TLC.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-122">The data set used to train and evaluate the machine learning model is originally from the NYC TLC Taxi Trip data set.</span></span>

    1. <span data-ttu-id="7e9dd-123">Para baixar o conjunto de dados, navegue até o link de download [taxi-fare-train.csv](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span><span class="sxs-lookup"><span data-stu-id="7e9dd-123">To download the data set, navigate to the [taxi-fare-train.csv download link](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span></span>

    1. <span data-ttu-id="7e9dd-124">Quando a página for carregada, clique com o botão direito do mouse em qualquer lugar da página e escolha **Salvar como**.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-124">When the page loads, right-click anywhere on the page and select **Save as**.</span></span>

    1. <span data-ttu-id="7e9dd-125">Use a opção **Salvar como Diálogo** para salvar o arquivo na pasta *Dados* criada na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-125">Use the **Save As Dialog** to save the file in the *Data* folder you created at the previous step.</span></span>

1. <span data-ttu-id="7e9dd-126">No **Gerenciador de Soluções**, clique com o botão direito do mouse no arquivo *taxi-fare-train.csv* e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-126">In **Solution Explorer**, right-click the *taxi-fare-train.csv* file and select **Properties**.</span></span> <span data-ttu-id="7e9dd-127">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-127">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="7e9dd-128">Cada linha no conjunto de dados `taxi-fare-train.csv` contém os detalhes de corridas feitas por um táxi.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-128">Each row in the `taxi-fare-train.csv` data set contains details of trips made by a taxi.</span></span>

1. <span data-ttu-id="7e9dd-129">Abra o conjunto de dados **taxi-fare-train.csv**</span><span class="sxs-lookup"><span data-stu-id="7e9dd-129">Open the **taxi-fare-train.csv** data set</span></span>

    <span data-ttu-id="7e9dd-130">O conjunto de dados fornecido contém as seguintes colunas:</span><span class="sxs-lookup"><span data-stu-id="7e9dd-130">The provided data set contains the following columns:</span></span>

    - <span data-ttu-id="7e9dd-131">**vendor_id:** o ID do taxista é um recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-131">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
    - <span data-ttu-id="7e9dd-132">**rate_code:** o tipo de tarifa da viagem de táxi é um recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-132">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
    - <span data-ttu-id="7e9dd-133">**passenger_count:** o número de passageiros na viagem é um recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-133">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
    - <span data-ttu-id="7e9dd-134">**trip_time_in_secs:** a quantidade de tempo que a viagem levou.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-134">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="7e9dd-135">Você deseja prever a tarifa da viagem antes de sua conclusão.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-135">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="7e9dd-136">No momento, você não sabe a duração da viagem.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-136">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="7e9dd-137">Portanto, o tempo da viagem não é um recurso e você excluirá essa coluna do modelo.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-137">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
    - <span data-ttu-id="7e9dd-138">**trip_distance:** a distância da viagem é um recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-138">**trip_distance:** The distance of the trip is a feature.</span></span>
    - <span data-ttu-id="7e9dd-139">**payment_type:** o método de pagamento (dinheiro ou cartão de crédito) é um recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-139">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
    - <span data-ttu-id="7e9dd-140">**fare_amount:** a tarifa total de táxi paga é o rótulo.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-140">**fare_amount:** The total taxi fare paid is the label.</span></span>

<span data-ttu-id="7e9dd-141">O `label` é a coluna que você deseja prever.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-141">The `label` is the column you want to predict.</span></span> <span data-ttu-id="7e9dd-142">Ao executar uma tarefa de regressão, o objetivo é prever um valor numérico.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-142">When performing a regression task, the goal is to predict a numerical value.</span></span> <span data-ttu-id="7e9dd-143">Nesse cenário de previsão de preço, o custo de uma corrida de táxi está sendo previsto.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-143">In this price prediction scenario, the cost of a taxi ride is being predicted.</span></span> <span data-ttu-id="7e9dd-144">Portanto, o **fare_amount** é o rótulo.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-144">Therefore, the **fare_amount** is the label.</span></span> <span data-ttu-id="7e9dd-145">Os `features` identificados são as entradas que você atribui ao modelo para prever o `label`.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-145">The identified `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="7e9dd-146">Nesse caso, o restante das colunas com a exceção de **trip_time_in_secs** são usadas como recursos ou entradas para prever o valor da tarifa.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-146">In this case, the rest of the columns with the exception of **trip_time_in_secs** are used as features or inputs to predict the fare amount.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="7e9dd-147">Escolha um cenário</span><span class="sxs-lookup"><span data-stu-id="7e9dd-147">Choose a scenario</span></span>

<span data-ttu-id="7e9dd-148">Para treinar seu modelo, você precisa selecionar na lista de cenários disponíveis de aprendizado de máquina fornecidos pelo Construtor de Modelo.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-148">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="7e9dd-149">Nesse caso, o cenário é `Price Prediction`.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-149">In this case, the scenario is `Price Prediction`.</span></span>

1. <span data-ttu-id="7e9dd-150">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto *TaxiFarePrediction* e selecione **Adicionar** > **Aprendizado de Máquina**.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-150">In **Solution Explorer**, right-click the *TaxiFarePrediction* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="7e9dd-151">Na etapa de cenário da ferramenta do Construtor de Modelo, selecione cenário de *Previsão de Preço*.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-151">In the scenario step of the Model Builder tool, select *Price Prediction* scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="7e9dd-152">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="7e9dd-152">Load the data</span></span>

<span data-ttu-id="7e9dd-153">O Construtor de Modelo aceita dados de duas fontes: um banco de dados do SQL Server ou um arquivo local no formato csv ou tsv.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-153">Model Builder accepts data from two sources, a SQL Server database or a local file in csv or tsv format.</span></span>

1. <span data-ttu-id="7e9dd-154">Na etapa de dados da ferramenta do Construtor de Modelo, selecione *Arquivo* na lista suspensa da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-154">In the data step of the Model Builder tool, select *File* from the data source dropdown.</span></span>
1. <span data-ttu-id="7e9dd-155">Selecione o botão ao lado da caixa de texto *Selecionar um arquivo* e use o Explorador de Arquivos para procurar e selecionar o *taxi-fare-test.csv* no diretório de *Dados*</span><span class="sxs-lookup"><span data-stu-id="7e9dd-155">Select the button next to the *Select a file* text box and use File Explorer to browse and select the *taxi-fare-test.csv* in the *Data* directory</span></span>
1. <span data-ttu-id="7e9dd-156">Escolha *fare_amount* na *coluna para prever (rótulo)* DropDown.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-156">Choose *fare_amount* in the *Column to Predict (Label)* dropdown.</span></span>
1. <span data-ttu-id="7e9dd-157">Expanda a lista suspensa *colunas de entrada (recursos)* e desmarque a coluna *trip_time_in_secs* para excluí-la como um recurso durante o treinamento.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-157">Expand the *Input Columns (Features)* dropdown and uncheck the *trip_time_in_secs* column to exclude it as a feature during training.</span></span>  <span data-ttu-id="7e9dd-158">Navegue até a etapa treinar da ferramenta Construtor de modelos.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-158">Navigate to the train step of the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="7e9dd-159">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="7e9dd-159">Train the model</span></span>

<span data-ttu-id="7e9dd-160">A tarefa de aprendizado de máquina usada para treinar o modelo de previsão de preço neste tutorial é a regressão.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-160">The machine learning task used to train the price prediction model in this tutorial is regression.</span></span> <span data-ttu-id="7e9dd-161">Durante o processo de treinamento de modelo, o Construtor de Modelo treina modelos separados usando algoritmos de regressão diferentes e configurações para localizar o modelo com melhor desempenho para seu conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-161">During the model training process, Model Builder trains separate models using different regression algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="7e9dd-162">O tempo necessário para treinar o modelo é proporcional à quantidade de dados.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-162">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="7e9dd-163">O construtor de modelos seleciona automaticamente um valor padrão para o **tempo de treinamento (segundos)** com base no tamanho da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-163">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="7e9dd-164">Deixe o valor padrão como está para o *tempo de treinamento (segundos)* , a menos que você prefira treinar por um tempo maior.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-164">Leave the default value as is for *Time to train (seconds)* unless you prefer to train for a longer time.</span></span>
2. <span data-ttu-id="7e9dd-165">Selecione *Iniciar Treinamento*.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-165">Select *Start Training*.</span></span>

<span data-ttu-id="7e9dd-166">Durante o processo de treinamento, os dados de progresso são exibidos na seção `Progress` da etapa de treinamento.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-166">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

- <span data-ttu-id="7e9dd-167">O status exibe o status de conclusão do processo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-167">Status displays the completion status of the training process.</span></span>
- <span data-ttu-id="7e9dd-168">A melhor precisão exibe a precisão do modelo de melhor desempenho encontrado pelo Construtor do Modelo até o momento.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-168">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="7e9dd-169">Maior precisão significa que o modelo é previsto mais corretamente nos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-169">Higher accuracy means the model predicted more correctly on test data.</span></span>
- <span data-ttu-id="7e9dd-170">O melhor algoritmo exibe o nome do algoritmo de melhor desempenho executado encontrado pelo Construtor de Modelo até o momento.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-170">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
- <span data-ttu-id="7e9dd-171">O último algoritmo exibe o nome do algoritmo usado mais recentemente pelo Construtor de Modelo para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-171">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

<span data-ttu-id="7e9dd-172">Após a conclusão do treinamento, navegue até a etapa de avaliação.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-172">Once training is complete, navigate to the evaluate step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="7e9dd-173">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="7e9dd-173">Evaluate the model</span></span>

<span data-ttu-id="7e9dd-174">O resultado da etapa de treinamento será um modelo que tinha o melhor desempenho.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-174">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="7e9dd-175">Na etapa de avaliação da ferramenta do Construtor de Modelo, a seção de saída terá o algoritmo usado pelo modelo com melhor desempenho na entrada *Melhor Modelo*, juntamente com as métricas na *Qualidade do Melhor Modelo (RSquared)* .</span><span class="sxs-lookup"><span data-stu-id="7e9dd-175">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the *Best Model* entry along with metrics in *Best Model Quality (RSquared)*.</span></span> <span data-ttu-id="7e9dd-176">Além disso, uma tabela de resumo contém os cinco modelos principais e suas métricas.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-176">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="7e9dd-177">Se você não estiver satisfeito com suas métricas de precisão, algumas maneiras fáceis de experimentar e aprimorar a precisão do modelo serão aumentar a quantidade de tempo para treinar o modelo ou usar mais dados.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-177">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="7e9dd-178">Ou navegue até a etapa do código.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-178">Otherwise, navigate to the code step.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="7e9dd-179">Adicionar o código para fazer previsões</span><span class="sxs-lookup"><span data-stu-id="7e9dd-179">Add the code to make predictions</span></span>

<span data-ttu-id="7e9dd-180">Dois projetos serão criados como resultado do processo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-180">Two projects will be created as a result of the training process.</span></span>

- <span data-ttu-id="7e9dd-181">TaxiFarePredictionML. ConsoleApp: um aplicativo de console do .NET Core que contém o treinamento do modelo e o código de consumo de exemplo.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-181">TaxiFarePredictionML.ConsoleApp: A .NET Core Console application that contains the model training and sample consumption code.</span></span>
- <span data-ttu-id="7e9dd-182">TaxiFarePredictionML. Model: um .NET Standard biblioteca de classes que contém os modelos de dados que definem o esquema dos dados de modelo de entrada e saída, a versão salva do modelo de melhor desempenho durante o treinamento e uma classe auxiliar chamada `ConsumeModel` para fazer previsões.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-182">TaxiFarePredictionML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data, the saved version of the best performing model during training and a helper class called `ConsumeModel` to make predictions.</span></span>

1. <span data-ttu-id="7e9dd-183">Na etapa de código da ferramenta do Construtor de Modelo, escolha **Adicionar Projetos** para adicionar os projetos gerados automaticamente à solução.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-183">In the code step of the Model Builder tool, select **Add Projects** to add the auto-generated projects to the solution.</span></span>
1. <span data-ttu-id="7e9dd-184">Abra o arquivo *Program.cs* no projeto *TaxiFarePrediction*.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-184">Open the *Program.cs* file in the *TaxiFarePrediction* project.</span></span>
1. <span data-ttu-id="7e9dd-185">Adicione a seguinte instrução using para fazer referência ao projeto *TaxiFarePredictionML. Model* :</span><span class="sxs-lookup"><span data-stu-id="7e9dd-185">Add the following using statement to reference the *TaxiFarePredictionML.Model* project:</span></span>

    ```csharp
    using System;
    using TaxiFarePredictionML.Model;
    ```

1. <span data-ttu-id="7e9dd-186">Para fazer uma previsão sobre novos dados usando o modelo, crie uma nova instância da classe `ModelInput` dentro do método `Main` do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-186">To make a prediction on new data using the model, create a new instance of the `ModelInput` class inside the `Main` method of your application.</span></span> <span data-ttu-id="7e9dd-187">Observe que o valor da tarifa não faz parte da entrada.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-187">Notice that the fare amount is not part of the input.</span></span> <span data-ttu-id="7e9dd-188">Isso acontece porque o modelo gerará a previsão para ela.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-188">This is because the model will generate the prediction for it.</span></span> 

    ```csharp
    // Create sample data
    ModelInput input = new ModelInput()
    {
        Vendor_id = "CMT",
        Rate_code = 1,
        Passenger_count = 1,
        Trip_distance = 3.8f,
        Payment_type = "CRD"
    };
    ```

1. <span data-ttu-id="7e9dd-189">Use o método `Predict` da classe `ConsumeModel`.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-189">Use the `Predict` method from the `ConsumeModel` class.</span></span> <span data-ttu-id="7e9dd-190">O método `Predict` carrega o modelo treinado, cria um [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) para o modelo e o usa para fazer previsões sobre novos dados.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-190">The `Predict` method loads the trained model, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) for the model and uses it to make predictions on new data.</span></span> 

    ```csharp
    // Make prediction
    ModelOutput prediction = ConsumeModel.Predict(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

1. <span data-ttu-id="7e9dd-191">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-191">Run the application.</span></span>

    <span data-ttu-id="7e9dd-192">A saída gerada pelo programa deve ser semelhante ao snippet a seguir:</span><span class="sxs-lookup"><span data-stu-id="7e9dd-192">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Fare: 14.96086
    ```

<span data-ttu-id="7e9dd-193">Se precisar fazer referência aos projetos gerados em um momento posterior dentro de outra solução, você poderá encontrá-los no diretório `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`.</span><span class="sxs-lookup"><span data-stu-id="7e9dd-193">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7e9dd-194">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="7e9dd-194">Next Steps</span></span>

<span data-ttu-id="7e9dd-195">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="7e9dd-195">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="7e9dd-196">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="7e9dd-196">Prepare and understand the data</span></span>
> - <span data-ttu-id="7e9dd-197">Escolha um cenário</span><span class="sxs-lookup"><span data-stu-id="7e9dd-197">Choose a scenario</span></span>
> - <span data-ttu-id="7e9dd-198">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="7e9dd-198">Load the data</span></span>
> - <span data-ttu-id="7e9dd-199">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="7e9dd-199">Train the model</span></span>
> - <span data-ttu-id="7e9dd-200">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="7e9dd-200">Evaluate the model</span></span>
> - <span data-ttu-id="7e9dd-201">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="7e9dd-201">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="7e9dd-202">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="7e9dd-202">Additional Resources</span></span>

<span data-ttu-id="7e9dd-203">Para saber mais sobre os tópicos mencionados neste tutorial, visite os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="7e9dd-203">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="7e9dd-204">Cenários do Construtor de Modelo</span><span class="sxs-lookup"><span data-stu-id="7e9dd-204">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="7e9dd-205">Regressão</span><span class="sxs-lookup"><span data-stu-id="7e9dd-205">Regression</span></span>](../resources/glossary.md#regression)
- [<span data-ttu-id="7e9dd-206">Métricas do Modelo de Regressão</span><span class="sxs-lookup"><span data-stu-id="7e9dd-206">Regression Model Metrics</span></span>](../resources/metrics.md#metrics-for-regression)
- [<span data-ttu-id="7e9dd-207">Conjunto de dados Corrida de Táxi da NYC TLC</span><span class="sxs-lookup"><span data-stu-id="7e9dd-207">NYC TLC Taxi Trip data set</span></span>](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)
