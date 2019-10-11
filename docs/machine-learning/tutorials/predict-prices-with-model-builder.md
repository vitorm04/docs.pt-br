---
title: 'Tutorial: Prever os preços usando regressão com o Construtor de Modelo'
description: Este tutorial mostra como criar um modelo de regressão usando o Construtor de Modelo do ML.NET para prever os preços, especificamente, as tarifas de táxi de Nova York.
author: luisquintanilla
ms.author: luquinta
ms.date: 10/08/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: a851bf3c405d15243bc1457b8c3dff815d072ebe
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180277"
---
# <a name="tutorial-predict-prices-using-regression-with-model-builder"></a><span data-ttu-id="5bdd6-103">Tutorial: Prever os preços usando regressão com o Construtor de Modelo</span><span class="sxs-lookup"><span data-stu-id="5bdd6-103">Tutorial: Predict prices using regression with Model Builder</span></span>

<span data-ttu-id="5bdd6-104">Saiba como usar o ML.NET Model Builder para criar um modelo de regressão para prever os preços.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-104">Learn how to use ML.NET Model Builder to build a regression model to predict prices.</span></span>  <span data-ttu-id="5bdd6-105">O aplicativo de console do .NET que você desenvolve neste tutorial prevê as tarifas de táxi com base em dados históricos de tarifas de táxi em Nova York.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-105">The .NET console app that you develop in this tutorial predicts taxi fares based on historical New York taxi fare data.</span></span>

<span data-ttu-id="5bdd6-106">O modelo de previsão de preço do Construtor de Modelo pode ser usado em qualquer cenário que exija um valor de previsão numérico.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-106">The Model Builder price prediction template can be used for any scenario requiring a numerical prediction value.</span></span> <span data-ttu-id="5bdd6-107">Exemplos de cenários incluem: previsão de preço, previsão de demanda e previsão de vendas de casas.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-107">Example scenarios include: house price prediction, demand prediction, and sales forecasting.</span></span>

<span data-ttu-id="5bdd6-108">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="5bdd6-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="5bdd6-109">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="5bdd6-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="5bdd6-110">Escolha um cenário</span><span class="sxs-lookup"><span data-stu-id="5bdd6-110">Choose a scenario</span></span>
> - <span data-ttu-id="5bdd6-111">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="5bdd6-111">Load the data</span></span>
> - <span data-ttu-id="5bdd6-112">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="5bdd6-112">Train the model</span></span>
> - <span data-ttu-id="5bdd6-113">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="5bdd6-113">Evaluate the model</span></span>
> - <span data-ttu-id="5bdd6-114">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="5bdd6-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="5bdd6-115">O Construtor de Modelo está atualmente na Versão Prévia.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-115">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="5bdd6-116">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="5bdd6-116">Pre-requisites</span></span>

<span data-ttu-id="5bdd6-117">Para obter uma lista de pré-requisitos e instruções de instalação, visite o [guia de instalação do Construtor de Modelo](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="5bdd6-117">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="5bdd6-118">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="5bdd6-118">Create a console application</span></span>

1. <span data-ttu-id="5bdd6-119">Crie um **Aplicativo de Console do .NET Core** chamado "TaxiFarePrediction".</span><span class="sxs-lookup"><span data-stu-id="5bdd6-119">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="5bdd6-120">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="5bdd6-120">Prepare and understand the data</span></span>

1. <span data-ttu-id="5bdd6-121">Crie um diretório chamado *Data* no projeto para armazenar os arquivos do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-121">Create a directory named *Data* in your project to store the data set files.</span></span>

1. <span data-ttu-id="5bdd6-122">O conjunto de dados usado para treinar e avaliar o modelo de machine learning pertence originalmente ao conjunto de dados Corrida de Táxi da NYC TLC.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-122">The data set used to train and evaluate the machine learning model is originally from the NYC TLC Taxi Trip data set.</span></span>

    1. <span data-ttu-id="5bdd6-123">Para baixar o conjunto de dados, navegue até o link de download [taxi-fare-train.csv](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span><span class="sxs-lookup"><span data-stu-id="5bdd6-123">To download the data set, navigate to the [taxi-fare-train.csv download link](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span></span>

    1. <span data-ttu-id="5bdd6-124">Quando a página for carregada, clique com o botão direito do mouse em qualquer lugar da página e escolha **Salvar como**.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-124">When the page loads, right-click anywhere on the page and select **Save as**.</span></span>

    1. <span data-ttu-id="5bdd6-125">Use a opção **Salvar como Diálogo** para salvar o arquivo na pasta *Dados* criada na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-125">Use the **Save As Dialog** to save the file in the *Data* folder you created at the previous step.</span></span>

1. <span data-ttu-id="5bdd6-126">No **Gerenciador de Soluções**, clique com o botão direito do mouse no arquivo *taxi-fare-train.csv* e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-126">In **Solution Explorer**, right-click the *taxi-fare-train.csv* file and select **Properties**.</span></span> <span data-ttu-id="5bdd6-127">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-127">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="5bdd6-128">Cada linha no conjunto de dados `taxi-fare-train.csv` contém os detalhes de corridas feitas por um táxi.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-128">Each row in the `taxi-fare-train.csv` data set contains details of trips made by a taxi.</span></span>

1. <span data-ttu-id="5bdd6-129">Abra o conjunto de dados **taxi-fare-train.csv**</span><span class="sxs-lookup"><span data-stu-id="5bdd6-129">Open the **taxi-fare-train.csv** data set</span></span>

    <span data-ttu-id="5bdd6-130">O conjunto de dados fornecido contém as seguintes colunas:</span><span class="sxs-lookup"><span data-stu-id="5bdd6-130">The provided data set contains the following columns:</span></span>

    - <span data-ttu-id="5bdd6-131">**vendor_id:** A ID do taxista é um recurso.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-131">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
    - <span data-ttu-id="5bdd6-132">**rate_code:** O tipo de tarifa da corrida de táxi é um recurso.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-132">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
    - <span data-ttu-id="5bdd6-133">**passenger_count:** O número de passageiros na corrida é um recurso.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-133">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
    - <span data-ttu-id="5bdd6-134">**trip_time_in_secs:** O tempo que levou a corrida.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-134">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="5bdd6-135">Você deseja prever a tarifa da viagem antes de sua conclusão.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-135">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="5bdd6-136">No momento, você não sabe a duração da viagem.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-136">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="5bdd6-137">Portanto, o tempo da viagem não é um recurso e você excluirá essa coluna do modelo.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-137">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
    - <span data-ttu-id="5bdd6-138">**trip_distance:** A distância da corrida é um recurso.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-138">**trip_distance:** The distance of the trip is a feature.</span></span>
    - <span data-ttu-id="5bdd6-139">**payment_type:** A forma de pagamento (dinheiro ou cartão de crédito) é um recurso.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-139">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
    - <span data-ttu-id="5bdd6-140">**fare_amount:** A tarifa total de táxi paga é o rótulo.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-140">**fare_amount:** The total taxi fare paid is the label.</span></span>

<span data-ttu-id="5bdd6-141">O `label` é a coluna que você deseja prever.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-141">The `label` is the column you want to predict.</span></span> <span data-ttu-id="5bdd6-142">Ao executar uma tarefa de regressão, o objetivo é prever um valor numérico.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-142">When performing a regression task, the goal is to predict a numerical value.</span></span> <span data-ttu-id="5bdd6-143">Nesse cenário de previsão de preço, o custo de uma corrida de táxi está sendo previsto.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-143">In this price prediction scenario, the cost of a taxi ride is being predicted.</span></span> <span data-ttu-id="5bdd6-144">Portanto, o **fare_amount** é o rótulo.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-144">Therefore, the **fare_amount** is the label.</span></span> <span data-ttu-id="5bdd6-145">Os `features` identificados são as entradas que você atribui ao modelo para prever o `label`.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-145">The identified `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="5bdd6-146">Nesse caso, o restante das colunas com a exceção de **trip_time_in_secs** são usadas como recursos ou entradas para prever o valor da tarifa.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-146">In this case, the rest of the columns with the exception of **trip_time_in_secs** are used as features or inputs to predict the fare amount.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="5bdd6-147">Escolha um cenário</span><span class="sxs-lookup"><span data-stu-id="5bdd6-147">Choose a scenario</span></span>

<span data-ttu-id="5bdd6-148">Para treinar seu modelo, você precisa selecionar na lista de cenários disponíveis de aprendizado de máquina fornecidos pelo Construtor de Modelo.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-148">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="5bdd6-149">Nesse caso, o cenário é `Price Prediction`.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-149">In this case, the scenario is `Price Prediction`.</span></span>

1. <span data-ttu-id="5bdd6-150">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto *TaxiFarePrediction* e selecione **Adicionar** > **Aprendizado de Máquina**.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-150">In **Solution Explorer**, right-click the *TaxiFarePrediction* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="5bdd6-151">Na etapa de cenário da ferramenta do Construtor de Modelo, selecione cenário de *Previsão de Preço*.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-151">In the scenario step of the Model Builder tool, select *Price Prediction* scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="5bdd6-152">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="5bdd6-152">Load the data</span></span>

<span data-ttu-id="5bdd6-153">O Construtor de Modelo aceita dados de duas fontes: um banco de dados do SQL Server ou um arquivo local no formato csv ou tsv.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-153">Model Builder accepts data from two sources, a SQL Server database or a local file in csv or tsv format.</span></span>

1. <span data-ttu-id="5bdd6-154">Na etapa de dados da ferramenta do Construtor de Modelo, selecione *Arquivo* na lista suspensa da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-154">In the data step of the Model Builder tool, select *File* from the data source dropdown.</span></span>
1. <span data-ttu-id="5bdd6-155">Selecione o botão ao lado da caixa de texto *Selecionar um arquivo* e use o Explorador de Arquivos para procurar e selecionar o *taxi-fare-test.csv* no diretório de *Dados*</span><span class="sxs-lookup"><span data-stu-id="5bdd6-155">Select the button next to the *Select a file* text box and use File Explorer to browse and select the *taxi-fare-test.csv* in the *Data* directory</span></span>
1. <span data-ttu-id="5bdd6-156">Escolha *fare_amount* na *coluna para prever (rótulo)* DropDown e navegue até a etapa treinar da ferramenta Construtor de modelos.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-156">Choose *fare_amount* in the *Column to Predict (Label)* dropdown and navigate to the train step of the Model Builder tool.</span></span>
1. <span data-ttu-id="5bdd6-157">Expanda a lista suspensa *colunas de entrada (recursos)* e desmarque a coluna *trip_time_in_secs* para excluí-la como um recurso durante o treinamento.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-157">Expand the *Input Columns (Features)* dropdown and uncheck the *trip_time_in_secs* column to exclude it as a feature during training.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="5bdd6-158">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="5bdd6-158">Train the model</span></span>

<span data-ttu-id="5bdd6-159">A tarefa de aprendizado de máquina usada para treinar o modelo de previsão de preço neste tutorial é a regressão.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-159">The machine learning task used to train the price prediction model in this tutorial is regression.</span></span> <span data-ttu-id="5bdd6-160">Durante o processo de treinamento de modelo, o Construtor de Modelo treina modelos separados usando algoritmos de regressão diferentes e configurações para localizar o modelo com melhor desempenho para seu conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-160">During the model training process, Model Builder trains separate models using different regression algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="5bdd6-161">O tempo necessário para treinar o modelo é proporcional à quantidade de dados.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-161">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="5bdd6-162">O construtor de modelos seleciona automaticamente um valor padrão para o **tempo de treinamento (segundos)** com base no tamanho da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-162">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="5bdd6-163">Deixe o valor padrão como está para o *tempo de treinamento (segundos)* , a menos que você prefira treinar por um tempo maior.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-163">Leave the default value as is for *Time to train (seconds)* unless you prefer to train for a longer time.</span></span>
2. <span data-ttu-id="5bdd6-164">Selecione *Iniciar Treinamento*.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-164">Select *Start Training*.</span></span>

<span data-ttu-id="5bdd6-165">Durante o processo de treinamento, os dados de progresso são exibidos na seção `Progress` da etapa de treinamento.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-165">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

- <span data-ttu-id="5bdd6-166">O status exibe o status de conclusão do processo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-166">Status displays the completion status of the training process.</span></span>
- <span data-ttu-id="5bdd6-167">A melhor precisão exibe a precisão do modelo de melhor desempenho encontrado pelo Construtor do Modelo até o momento.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-167">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="5bdd6-168">Maior precisão significa que o modelo é previsto mais corretamente nos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-168">Higher accuracy means the model predicted more correctly on test data.</span></span>
- <span data-ttu-id="5bdd6-169">O melhor algoritmo exibe o nome do algoritmo de melhor desempenho executado encontrado pelo Construtor de Modelo até o momento.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-169">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
- <span data-ttu-id="5bdd6-170">O último algoritmo exibe o nome do algoritmo usado mais recentemente pelo Construtor de Modelo para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-170">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

<span data-ttu-id="5bdd6-171">Após a conclusão do treinamento, navegue até a etapa de avaliação.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-171">Once training is complete, navigate to the evaluate step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="5bdd6-172">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="5bdd6-172">Evaluate the model</span></span>

<span data-ttu-id="5bdd6-173">O resultado da etapa de treinamento será um modelo que tinha o melhor desempenho.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-173">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="5bdd6-174">Na etapa de avaliação da ferramenta do Construtor de Modelo, a seção de saída terá o algoritmo usado pelo modelo com melhor desempenho na entrada *Melhor Modelo*, juntamente com as métricas na *Qualidade do Melhor Modelo (RSquared)* .</span><span class="sxs-lookup"><span data-stu-id="5bdd6-174">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the *Best Model* entry along with metrics in *Best Model Quality (RSquared)*.</span></span> <span data-ttu-id="5bdd6-175">Além disso, uma tabela de resumo contém os cinco modelos principais e suas métricas.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-175">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="5bdd6-176">Se você não estiver satisfeito com suas métricas de precisão, algumas maneiras fáceis de experimentar e aprimorar a precisão do modelo serão aumentar a quantidade de tempo para treinar o modelo ou usar mais dados.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-176">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="5bdd6-177">Ou navegue até a etapa do código.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-177">Otherwise, navigate to the code step.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="5bdd6-178">Adicionar o código para fazer previsões</span><span class="sxs-lookup"><span data-stu-id="5bdd6-178">Add the code to make predictions</span></span>

<span data-ttu-id="5bdd6-179">Dois projetos serão criados como resultado do processo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-179">Two projects will be created as a result of the training process.</span></span>

- <span data-ttu-id="5bdd6-180">TaxiFarePredictionML.ConsoleApp: Um aplicativo de console .NET Core que contém o treinamento do modelo e o código de consumo de exemplo.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-180">TaxiFarePredictionML.ConsoleApp: A .NET Core Console application that contains the model training and sample consumption code.</span></span>
- <span data-ttu-id="5bdd6-181">TaxiFarePredictionML.Model: Um .NET Standard biblioteca de classes que contém os modelos de dados que definem o esquema de dados de modelo de entrada e saída, a versão salva do modelo de melhor desempenho durante o treinamento e uma classe auxiliar chamada `ConsumeModel` para fazer previsões.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-181">TaxiFarePredictionML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data, the saved version of the best performing model during training and a helper class called `ConsumeModel` to make predictions.</span></span>

1. <span data-ttu-id="5bdd6-182">Na etapa de código da ferramenta do Construtor de Modelo, escolha **Adicionar Projetos** para adicionar os projetos gerados automaticamente à solução.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-182">In the code step of the Model Builder tool, select **Add Projects** to add the auto-generated projects to the solution.</span></span>
1. <span data-ttu-id="5bdd6-183">Abra o arquivo *Program.cs* no projeto *TaxiFarePrediction*.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-183">Open the *Program.cs* file in the *TaxiFarePrediction* project.</span></span>
1. <span data-ttu-id="5bdd6-184">Adicione a seguinte instrução using para fazer referência ao projeto *TaxiFarePredictionML. Model* :</span><span class="sxs-lookup"><span data-stu-id="5bdd6-184">Add the following using statement to reference the *TaxiFarePredictionML.Model* project:</span></span>

    ```csharp
    using System;
    using TaxiFarePredictionML.Model;
    ```

1. <span data-ttu-id="5bdd6-185">Para fazer uma previsão sobre novos dados usando o modelo, crie uma nova instância da classe `ModelInput` dentro do método `Main` do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-185">To make a prediction on new data using the model, create a new instance of the `ModelInput` class inside the `Main` method of your application.</span></span> <span data-ttu-id="5bdd6-186">Observe que o valor da tarifa não faz parte da entrada.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-186">Notice that the fare amount is not part of the input.</span></span> <span data-ttu-id="5bdd6-187">Isso acontece porque o modelo gerará a previsão para ela.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-187">This is because the model will generate the prediction for it.</span></span> 

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

1. <span data-ttu-id="5bdd6-188">Use o método `Predict` da classe `ConsumeModel`.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-188">Use the `Predict` method from the `ConsumeModel` class.</span></span> <span data-ttu-id="5bdd6-189">O método `Predict` carrega o modelo treinado, cria um [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) para o modelo e o usa para fazer previsões sobre novos dados.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-189">The `Predict` method loads the trained model, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) for the model and uses it to make predictions on new data.</span></span> 

    ```csharp
    // Make prediction
    ModelOutput prediction = ConsumeModel.Predict(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

1. <span data-ttu-id="5bdd6-190">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-190">Run the application.</span></span>

    <span data-ttu-id="5bdd6-191">A saída gerada pelo programa deve ser semelhante ao snippet a seguir:</span><span class="sxs-lookup"><span data-stu-id="5bdd6-191">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Fare: 14.96086
    ```

<span data-ttu-id="5bdd6-192">Se precisar fazer referência aos projetos gerados em um momento posterior dentro de outra solução, você poderá encontrá-los no diretório `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`.</span><span class="sxs-lookup"><span data-stu-id="5bdd6-192">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5bdd6-193">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="5bdd6-193">Next Steps</span></span>

<span data-ttu-id="5bdd6-194">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="5bdd6-194">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="5bdd6-195">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="5bdd6-195">Prepare and understand the data</span></span>
> - <span data-ttu-id="5bdd6-196">Escolha um cenário</span><span class="sxs-lookup"><span data-stu-id="5bdd6-196">Choose a scenario</span></span>
> - <span data-ttu-id="5bdd6-197">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="5bdd6-197">Load the data</span></span>
> - <span data-ttu-id="5bdd6-198">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="5bdd6-198">Train the model</span></span>
> - <span data-ttu-id="5bdd6-199">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="5bdd6-199">Evaluate the model</span></span>
> - <span data-ttu-id="5bdd6-200">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="5bdd6-200">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="5bdd6-201">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="5bdd6-201">Additional Resources</span></span>

<span data-ttu-id="5bdd6-202">Para saber mais sobre os tópicos mencionados neste tutorial, visite os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="5bdd6-202">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="5bdd6-203">Cenários do Construtor de Modelo</span><span class="sxs-lookup"><span data-stu-id="5bdd6-203">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="5bdd6-204">Regressão</span><span class="sxs-lookup"><span data-stu-id="5bdd6-204">Regression</span></span>](../resources/glossary.md#regression)
- [<span data-ttu-id="5bdd6-205">Métricas do Modelo de Regressão</span><span class="sxs-lookup"><span data-stu-id="5bdd6-205">Regression Model Metrics</span></span>](../resources/metrics.md#metrics-for-regression)
- [<span data-ttu-id="5bdd6-206">Conjunto de dados Corrida de Táxi da NYC TLC</span><span class="sxs-lookup"><span data-stu-id="5bdd6-206">NYC TLC Taxi Trip data set</span></span>](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)
