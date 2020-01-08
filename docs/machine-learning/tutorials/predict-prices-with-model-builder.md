---
title: 'Tutorial: prever os preços usando a regressão com o construtor de modelos'
description: Este tutorial mostra como criar um modelo de regressão usando o Construtor de Modelo do ML.NET para prever os preços, especificamente, as tarifas de táxi de Nova York.
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 254f3c4c05a2c18f6182fc5f18d93114e20ed953
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344984"
---
# <a name="tutorial-predict-prices-using-regression-with-model-builder"></a><span data-ttu-id="3f552-103">Tutorial: prever os preços usando a regressão com o construtor de modelos</span><span class="sxs-lookup"><span data-stu-id="3f552-103">Tutorial: Predict prices using regression with Model Builder</span></span>

<span data-ttu-id="3f552-104">Saiba como usar o ML.NET Model Builder para criar um modelo de regressão para prever os preços.</span><span class="sxs-lookup"><span data-stu-id="3f552-104">Learn how to use ML.NET Model Builder to build a regression model to predict prices.</span></span>  <span data-ttu-id="3f552-105">O aplicativo de console do .NET que você desenvolve neste tutorial prevê as tarifas de táxi com base em dados históricos de tarifas de táxi em Nova York.</span><span class="sxs-lookup"><span data-stu-id="3f552-105">The .NET console app that you develop in this tutorial predicts taxi fares based on historical New York taxi fare data.</span></span>

<span data-ttu-id="3f552-106">O modelo de previsão de preço do Construtor de Modelo pode ser usado em qualquer cenário que exija um valor de previsão numérico.</span><span class="sxs-lookup"><span data-stu-id="3f552-106">The Model Builder price prediction template can be used for any scenario requiring a numerical prediction value.</span></span> <span data-ttu-id="3f552-107">Exemplos de cenários incluem: previsão de preço, previsão de demanda e previsão de vendas de casas.</span><span class="sxs-lookup"><span data-stu-id="3f552-107">Example scenarios include: house price prediction, demand prediction, and sales forecasting.</span></span>

<span data-ttu-id="3f552-108">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="3f552-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="3f552-109">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="3f552-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="3f552-110">Escolha um cenário</span><span class="sxs-lookup"><span data-stu-id="3f552-110">Choose a scenario</span></span>
> - <span data-ttu-id="3f552-111">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="3f552-111">Load the data</span></span>
> - <span data-ttu-id="3f552-112">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="3f552-112">Train the model</span></span>
> - <span data-ttu-id="3f552-113">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="3f552-113">Evaluate the model</span></span>
> - <span data-ttu-id="3f552-114">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="3f552-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="3f552-115">O Construtor de Modelo está atualmente na Versão Prévia.</span><span class="sxs-lookup"><span data-stu-id="3f552-115">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="3f552-116">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="3f552-116">Pre-requisites</span></span>

<span data-ttu-id="3f552-117">Para obter uma lista de pré-requisitos e instruções de instalação, visite o [guia de instalação do Construtor de Modelo](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="3f552-117">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="3f552-118">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="3f552-118">Create a console application</span></span>

1. <span data-ttu-id="3f552-119">Crie um  **C# aplicativo de console do .NET Core** chamado "TaxiFarePrediction".</span><span class="sxs-lookup"><span data-stu-id="3f552-119">Create a **C# .NET Core Console Application** called "TaxiFarePrediction".</span></span> <span data-ttu-id="3f552-120">Verifique se a opção **Colocar solução e projeto no mesmo diretório** está **desmarcada** (vs 2019) ou **criar diretório para solução** está **marcado** (vs 2017).</span><span class="sxs-lookup"><span data-stu-id="3f552-120">Make sure **Place solution and project in the same directory** is **unchecked** (VS 2019), or **Create directory for solution** is **checked** (VS 2017).</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="3f552-121">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="3f552-121">Prepare and understand the data</span></span>

1. <span data-ttu-id="3f552-122">Crie um diretório chamado *Data* no projeto para armazenar os arquivos do conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="3f552-122">Create a directory named *Data* in your project to store the data set files.</span></span>

1. <span data-ttu-id="3f552-123">O conjunto de dados usado para treinar e avaliar o modelo de machine learning pertence originalmente ao conjunto de dados Corrida de Táxi da NYC TLC.</span><span class="sxs-lookup"><span data-stu-id="3f552-123">The data set used to train and evaluate the machine learning model is originally from the NYC TLC Taxi Trip data set.</span></span>

    1. <span data-ttu-id="3f552-124">Para baixar o conjunto de dados, navegue até o link de download [taxi-fare-train.csv](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span><span class="sxs-lookup"><span data-stu-id="3f552-124">To download the data set, navigate to the [taxi-fare-train.csv download link](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span></span>

    1. <span data-ttu-id="3f552-125">Quando a página for carregada, clique com o botão direito do mouse em qualquer lugar da página e escolha **Salvar como**.</span><span class="sxs-lookup"><span data-stu-id="3f552-125">When the page loads, right-click anywhere on the page and select **Save as**.</span></span>

    1. <span data-ttu-id="3f552-126">Use a opção **Salvar como Diálogo** para salvar o arquivo na pasta *Dados* criada na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="3f552-126">Use the **Save As Dialog** to save the file in the *Data* folder you created at the previous step.</span></span>

1. <span data-ttu-id="3f552-127">No **Gerenciador de Soluções**, clique com o botão direito do mouse no arquivo *taxi-fare-train.csv* e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="3f552-127">In **Solution Explorer**, right-click the *taxi-fare-train.csv* file and select **Properties**.</span></span> <span data-ttu-id="3f552-128">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.</span><span class="sxs-lookup"><span data-stu-id="3f552-128">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="3f552-129">Cada linha no conjunto de dados `taxi-fare-train.csv` contém os detalhes de corridas feitas por um táxi.</span><span class="sxs-lookup"><span data-stu-id="3f552-129">Each row in the `taxi-fare-train.csv` data set contains details of trips made by a taxi.</span></span>

1. <span data-ttu-id="3f552-130">Abra o conjunto de dados **taxi-fare-train.csv**</span><span class="sxs-lookup"><span data-stu-id="3f552-130">Open the **taxi-fare-train.csv** data set</span></span>

    <span data-ttu-id="3f552-131">O conjunto de dados fornecido contém as seguintes colunas:</span><span class="sxs-lookup"><span data-stu-id="3f552-131">The provided data set contains the following columns:</span></span>

    - <span data-ttu-id="3f552-132">**vendor_id:** o ID do taxista é um recurso.</span><span class="sxs-lookup"><span data-stu-id="3f552-132">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
    - <span data-ttu-id="3f552-133">**rate_code:** o tipo de tarifa da viagem de táxi é um recurso.</span><span class="sxs-lookup"><span data-stu-id="3f552-133">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
    - <span data-ttu-id="3f552-134">**passenger_count:** o número de passageiros na viagem é um recurso.</span><span class="sxs-lookup"><span data-stu-id="3f552-134">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
    - <span data-ttu-id="3f552-135">**trip_time_in_secs:** a quantidade de tempo que a viagem levou.</span><span class="sxs-lookup"><span data-stu-id="3f552-135">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="3f552-136">Você deseja prever a tarifa da viagem antes de sua conclusão.</span><span class="sxs-lookup"><span data-stu-id="3f552-136">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="3f552-137">No momento, você não sabe a duração da viagem.</span><span class="sxs-lookup"><span data-stu-id="3f552-137">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="3f552-138">Portanto, o tempo da viagem não é um recurso e você excluirá essa coluna do modelo.</span><span class="sxs-lookup"><span data-stu-id="3f552-138">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
    - <span data-ttu-id="3f552-139">**trip_distance:** a distância da viagem é um recurso.</span><span class="sxs-lookup"><span data-stu-id="3f552-139">**trip_distance:** The distance of the trip is a feature.</span></span>
    - <span data-ttu-id="3f552-140">**payment_type:** o método de pagamento (dinheiro ou cartão de crédito) é um recurso.</span><span class="sxs-lookup"><span data-stu-id="3f552-140">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
    - <span data-ttu-id="3f552-141">**fare_amount:** a tarifa total de táxi paga é o rótulo.</span><span class="sxs-lookup"><span data-stu-id="3f552-141">**fare_amount:** The total taxi fare paid is the label.</span></span>

<span data-ttu-id="3f552-142">O `label` é a coluna que você deseja prever.</span><span class="sxs-lookup"><span data-stu-id="3f552-142">The `label` is the column you want to predict.</span></span> <span data-ttu-id="3f552-143">Ao executar uma tarefa de regressão, o objetivo é prever um valor numérico.</span><span class="sxs-lookup"><span data-stu-id="3f552-143">When performing a regression task, the goal is to predict a numerical value.</span></span> <span data-ttu-id="3f552-144">Nesse cenário de previsão de preço, o custo de uma corrida de táxi está sendo previsto.</span><span class="sxs-lookup"><span data-stu-id="3f552-144">In this price prediction scenario, the cost of a taxi ride is being predicted.</span></span> <span data-ttu-id="3f552-145">Portanto, o **fare_amount** é o rótulo.</span><span class="sxs-lookup"><span data-stu-id="3f552-145">Therefore, the **fare_amount** is the label.</span></span> <span data-ttu-id="3f552-146">Os `features` identificados são as entradas que você atribui ao modelo para prever o `label`.</span><span class="sxs-lookup"><span data-stu-id="3f552-146">The identified `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="3f552-147">Nesse caso, o restante das colunas com exceção de **trip_time_in_secs** são usadas como recursos ou entradas para prever o valor da tarifa.</span><span class="sxs-lookup"><span data-stu-id="3f552-147">In this case, the rest of the columns with the exception of **trip_time_in_secs** are used as features or inputs to predict the fare amount.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="3f552-148">Escolha um cenário</span><span class="sxs-lookup"><span data-stu-id="3f552-148">Choose a scenario</span></span>

<span data-ttu-id="3f552-149">Para treinar seu modelo, você precisa selecionar na lista de cenários disponíveis de aprendizado de máquina fornecidos pelo Construtor de Modelo.</span><span class="sxs-lookup"><span data-stu-id="3f552-149">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="3f552-150">Nesse caso, o cenário é `Price Prediction`.</span><span class="sxs-lookup"><span data-stu-id="3f552-150">In this case, the scenario is `Price Prediction`.</span></span>

1. <span data-ttu-id="3f552-151">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto *TaxiFarePrediction* e selecione **Adicionar** > **Aprendizado de Máquina**.</span><span class="sxs-lookup"><span data-stu-id="3f552-151">In **Solution Explorer**, right-click the *TaxiFarePrediction* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="3f552-152">Na etapa de cenário da ferramenta do Construtor de Modelo, selecione cenário de *Previsão de Preço*.</span><span class="sxs-lookup"><span data-stu-id="3f552-152">In the scenario step of the Model Builder tool, select *Price Prediction* scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="3f552-153">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="3f552-153">Load the data</span></span>

<span data-ttu-id="3f552-154">O Construtor de Modelo aceita dados de duas fontes: um banco de dados do SQL Server ou um arquivo local no formato csv ou tsv.</span><span class="sxs-lookup"><span data-stu-id="3f552-154">Model Builder accepts data from two sources, a SQL Server database or a local file in csv or tsv format.</span></span>

1. <span data-ttu-id="3f552-155">Na etapa de dados da ferramenta do Construtor de Modelo, selecione *Arquivo* na lista suspensa da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="3f552-155">In the data step of the Model Builder tool, select *File* from the data source dropdown.</span></span>
1. <span data-ttu-id="3f552-156">Selecione o botão ao lado da caixa de texto *Selecionar um arquivo* e use o Explorador de Arquivos para procurar e selecionar o *taxi-fare-test.csv* no diretório de *Dados*</span><span class="sxs-lookup"><span data-stu-id="3f552-156">Select the button next to the *Select a file* text box and use File Explorer to browse and select the *taxi-fare-test.csv* in the *Data* directory</span></span>
1. <span data-ttu-id="3f552-157">Escolha *fare_amount* na *coluna para prever (rótulo)* suspenso.</span><span class="sxs-lookup"><span data-stu-id="3f552-157">Choose *fare_amount* in the *Column to Predict (Label)* dropdown.</span></span>
1. <span data-ttu-id="3f552-158">Expanda a lista suspensa *colunas de entrada (recursos)* e desmarque a coluna *trip_time_in_secs* para excluí-la como um recurso durante o treinamento.</span><span class="sxs-lookup"><span data-stu-id="3f552-158">Expand the *Input Columns (Features)* dropdown and uncheck the *trip_time_in_secs* column to exclude it as a feature during training.</span></span>  <span data-ttu-id="3f552-159">Navegue até a etapa treinar da ferramenta Construtor de modelos.</span><span class="sxs-lookup"><span data-stu-id="3f552-159">Navigate to the train step of the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="3f552-160">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="3f552-160">Train the model</span></span>

<span data-ttu-id="3f552-161">A tarefa de aprendizado de máquina usada para treinar o modelo de previsão de preço neste tutorial é a regressão.</span><span class="sxs-lookup"><span data-stu-id="3f552-161">The machine learning task used to train the price prediction model in this tutorial is regression.</span></span> <span data-ttu-id="3f552-162">Durante o processo de treinamento de modelo, o Construtor de Modelo treina modelos separados usando algoritmos de regressão diferentes e configurações para localizar o modelo com melhor desempenho para seu conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="3f552-162">During the model training process, Model Builder trains separate models using different regression algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="3f552-163">O tempo necessário para treinar o modelo é proporcional à quantidade de dados.</span><span class="sxs-lookup"><span data-stu-id="3f552-163">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="3f552-164">O construtor de modelos seleciona automaticamente um valor padrão para o **tempo de treinamento (segundos)** com base no tamanho da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="3f552-164">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="3f552-165">Deixe o valor padrão como está para o *tempo de treinamento (segundos)* , a menos que você prefira treinar por um tempo maior.</span><span class="sxs-lookup"><span data-stu-id="3f552-165">Leave the default value as is for *Time to train (seconds)* unless you prefer to train for a longer time.</span></span>
2. <span data-ttu-id="3f552-166">Selecione *Iniciar Treinamento*.</span><span class="sxs-lookup"><span data-stu-id="3f552-166">Select *Start Training*.</span></span>

<span data-ttu-id="3f552-167">Durante o processo de treinamento, os dados de progresso são exibidos na seção `Progress` da etapa de treinamento.</span><span class="sxs-lookup"><span data-stu-id="3f552-167">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

- <span data-ttu-id="3f552-168">O status exibe o status de conclusão do processo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="3f552-168">Status displays the completion status of the training process.</span></span>
- <span data-ttu-id="3f552-169">A melhor precisão exibe a precisão do modelo de melhor desempenho encontrado pelo Construtor do Modelo até o momento.</span><span class="sxs-lookup"><span data-stu-id="3f552-169">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="3f552-170">Maior precisão significa que o modelo é previsto mais corretamente nos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="3f552-170">Higher accuracy means the model predicted more correctly on test data.</span></span>
- <span data-ttu-id="3f552-171">O melhor algoritmo exibe o nome do algoritmo de melhor desempenho executado encontrado pelo Construtor de Modelo até o momento.</span><span class="sxs-lookup"><span data-stu-id="3f552-171">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
- <span data-ttu-id="3f552-172">O último algoritmo exibe o nome do algoritmo usado mais recentemente pelo Construtor de Modelo para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="3f552-172">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

<span data-ttu-id="3f552-173">Após a conclusão do treinamento, navegue até a etapa de avaliação.</span><span class="sxs-lookup"><span data-stu-id="3f552-173">Once training is complete, navigate to the evaluate step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="3f552-174">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="3f552-174">Evaluate the model</span></span>

<span data-ttu-id="3f552-175">O resultado da etapa de treinamento será um modelo que tinha o melhor desempenho.</span><span class="sxs-lookup"><span data-stu-id="3f552-175">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="3f552-176">Na etapa de avaliação da ferramenta do Construtor de Modelo, a seção de saída terá o algoritmo usado pelo modelo com melhor desempenho na entrada *Melhor Modelo*, juntamente com as métricas na *Qualidade do Melhor Modelo (RSquared)* .</span><span class="sxs-lookup"><span data-stu-id="3f552-176">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the *Best Model* entry along with metrics in *Best Model Quality (RSquared)*.</span></span> <span data-ttu-id="3f552-177">Além disso, uma tabela de resumo contém os cinco modelos principais e suas métricas.</span><span class="sxs-lookup"><span data-stu-id="3f552-177">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="3f552-178">Se você não estiver satisfeito com suas métricas de precisão, algumas maneiras fáceis de experimentar e aprimorar a precisão do modelo serão aumentar a quantidade de tempo para treinar o modelo ou usar mais dados.</span><span class="sxs-lookup"><span data-stu-id="3f552-178">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="3f552-179">Ou navegue até a etapa do código.</span><span class="sxs-lookup"><span data-stu-id="3f552-179">Otherwise, navigate to the code step.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="3f552-180">Adicionar o código para fazer previsões</span><span class="sxs-lookup"><span data-stu-id="3f552-180">Add the code to make predictions</span></span>

<span data-ttu-id="3f552-181">Dois projetos serão criados como resultado do processo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="3f552-181">Two projects will be created as a result of the training process.</span></span>

- <span data-ttu-id="3f552-182">TaxiFarePredictionML. ConsoleApp: um aplicativo de console do .NET Core que contém o treinamento do modelo e o código de consumo de exemplo.</span><span class="sxs-lookup"><span data-stu-id="3f552-182">TaxiFarePredictionML.ConsoleApp: A .NET Core Console application that contains the model training and sample consumption code.</span></span>
- <span data-ttu-id="3f552-183">TaxiFarePredictionML. Model: um .NET Standard biblioteca de classes que contém os modelos de dados que definem o esquema dos dados de modelo de entrada e saída, a versão salva do modelo de melhor desempenho durante o treinamento e uma classe auxiliar chamada `ConsumeModel` para fazer previsões.</span><span class="sxs-lookup"><span data-stu-id="3f552-183">TaxiFarePredictionML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data, the saved version of the best performing model during training and a helper class called `ConsumeModel` to make predictions.</span></span>

1. <span data-ttu-id="3f552-184">Na etapa de código da ferramenta do Construtor de Modelo, escolha **Adicionar Projetos** para adicionar os projetos gerados automaticamente à solução.</span><span class="sxs-lookup"><span data-stu-id="3f552-184">In the code step of the Model Builder tool, select **Add Projects** to add the auto-generated projects to the solution.</span></span>
1. <span data-ttu-id="3f552-185">Abra o arquivo *Program.cs* no projeto *TaxiFarePrediction*.</span><span class="sxs-lookup"><span data-stu-id="3f552-185">Open the *Program.cs* file in the *TaxiFarePrediction* project.</span></span>
1. <span data-ttu-id="3f552-186">Adicione a seguinte instrução using para fazer referência ao projeto *TaxiFarePredictionML. Model* :</span><span class="sxs-lookup"><span data-stu-id="3f552-186">Add the following using statement to reference the *TaxiFarePredictionML.Model* project:</span></span>

    ```csharp
    using System;
    using TaxiFarePredictionML.Model;
    ```

1. <span data-ttu-id="3f552-187">Para fazer uma previsão sobre novos dados usando o modelo, crie uma nova instância da classe `ModelInput` dentro do método `Main` do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3f552-187">To make a prediction on new data using the model, create a new instance of the `ModelInput` class inside the `Main` method of your application.</span></span> <span data-ttu-id="3f552-188">Observe que o valor da tarifa não faz parte da entrada.</span><span class="sxs-lookup"><span data-stu-id="3f552-188">Notice that the fare amount is not part of the input.</span></span> <span data-ttu-id="3f552-189">Isso acontece porque o modelo gerará a previsão para ela.</span><span class="sxs-lookup"><span data-stu-id="3f552-189">This is because the model will generate the prediction for it.</span></span>

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

1. <span data-ttu-id="3f552-190">Use o método `Predict` da classe `ConsumeModel`.</span><span class="sxs-lookup"><span data-stu-id="3f552-190">Use the `Predict` method from the `ConsumeModel` class.</span></span> <span data-ttu-id="3f552-191">O método `Predict` carrega o modelo treinado, cria um [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) para o modelo e o usa para fazer previsões sobre novos dados.</span><span class="sxs-lookup"><span data-stu-id="3f552-191">The `Predict` method loads the trained model, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) for the model and uses it to make predictions on new data.</span></span>

    ```csharp
    // Make prediction
    ModelOutput prediction = ConsumeModel.Predict(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

1. <span data-ttu-id="3f552-192">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3f552-192">Run the application.</span></span>

    <span data-ttu-id="3f552-193">A saída gerada pelo programa deve ser semelhante ao snippet a seguir:</span><span class="sxs-lookup"><span data-stu-id="3f552-193">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Fare: 14.96086
    ```

<span data-ttu-id="3f552-194">Se precisar fazer referência aos projetos gerados em um momento posterior dentro de outra solução, você poderá encontrá-los no diretório `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`.</span><span class="sxs-lookup"><span data-stu-id="3f552-194">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3f552-195">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="3f552-195">Next Steps</span></span>

<span data-ttu-id="3f552-196">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="3f552-196">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="3f552-197">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="3f552-197">Prepare and understand the data</span></span>
> - <span data-ttu-id="3f552-198">Escolha um cenário</span><span class="sxs-lookup"><span data-stu-id="3f552-198">Choose a scenario</span></span>
> - <span data-ttu-id="3f552-199">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="3f552-199">Load the data</span></span>
> - <span data-ttu-id="3f552-200">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="3f552-200">Train the model</span></span>
> - <span data-ttu-id="3f552-201">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="3f552-201">Evaluate the model</span></span>
> - <span data-ttu-id="3f552-202">Usar o modelo para previsões</span><span class="sxs-lookup"><span data-stu-id="3f552-202">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="3f552-203">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="3f552-203">Additional Resources</span></span>

<span data-ttu-id="3f552-204">Para saber mais sobre os tópicos mencionados neste tutorial, visite os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="3f552-204">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="3f552-205">Cenários do Construtor de Modelo</span><span class="sxs-lookup"><span data-stu-id="3f552-205">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="3f552-206">Regressão</span><span class="sxs-lookup"><span data-stu-id="3f552-206">Regression</span></span>](../resources/glossary.md#regression)
- [<span data-ttu-id="3f552-207">Métricas do Modelo de Regressão</span><span class="sxs-lookup"><span data-stu-id="3f552-207">Regression Model Metrics</span></span>](../resources/metrics.md#evaluation-metrics-for-regression-and-recommendation)
- [<span data-ttu-id="3f552-208">Conjunto de dados Corrida de Táxi da NYC TLC</span><span class="sxs-lookup"><span data-stu-id="3f552-208">NYC TLC Taxi Trip data set</span></span>](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
