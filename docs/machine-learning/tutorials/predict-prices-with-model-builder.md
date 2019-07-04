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
# <a name="predict-prices-using-regression-with-model-builder"></a>Prever os preços usando regressão com o Construtor de Modelo

Saiba como usar o Construtor de Modelo do ML.NET para criar um [modelo de regressão](../resources/glossary.md#regression) e prever preços.  O aplicativo de console do .NET que você desenvolve neste tutorial prevê as tarifas de táxi com base em dados históricos de tarifas de táxi em Nova York.

O modelo de previsão de preço do Construtor de Modelo pode ser usado em qualquer cenário que exija um valor de previsão numérico. Exemplos de cenários incluem: previsão de preço, previsão de demanda e previsão de vendas de casas.

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
> * Preparar e compreender os dados
> * Escolha um cenário
> * Carregar os dados
> * Treinar o modelo
> * Avaliar o modelo
> * Usar o modelo para previsões

> [!NOTE]
> O Construtor de Modelo está atualmente na Versão Prévia.

## <a name="pre-requisites"></a>Pré-requisitos

Para obter uma lista de pré-requisitos e instruções de instalação, visite o [guia de instalação do Construtor de Modelo](../how-to-guides/install-model-builder.md).

## <a name="create-a-console-application"></a>Criar um aplicativo de console

1. Crie um **Aplicativo de Console do .NET Core** chamado "TaxiFarePrediction".

1. Instale o pacote NuGet **Microsoft.ML**:

    No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto *TaxiFarePrediction* e selecione **Gerenciar Pacotes NuGet**. Escolha "nuget.org" como a origem do pacote, selecione a guia **Procurar**, pesquise por **Microsoft.ML**, selecione o pacote na lista e selecione o botão **Instalar**. Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.

## <a name="prepare-and-understand-the-data"></a>Preparar e compreender os dados

1. Crie um diretório chamado *Data* no projeto para armazenar os arquivos do conjunto de dados.

1. Baixe o conjunto de dados [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) e salve-o na pasta *Dados* criada na etapa anterior. Esse conjunto de dados é usado para treinar e avaliar o modelo de machine learning. Esse conjunto de dados é originalmente do [Conjunto de dados NYC TLC Taxi Trip](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no arquivo *taxi-fare-train.csv* e selecione **Propriedades**. Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.

Cada linha no conjunto de dados `taxi-fare-train.csv` contém os detalhes de corridas feitas por um táxi. 

1. Abra o conjunto de dados **taxi-fare-train.csv**

    O conjunto de dados fornecido contém as seguintes colunas:

    * **vendor_id:** A ID do taxista é um recurso.
    * **rate_code:** O tipo de tarifa da corrida de táxi é um recurso.
    * **passenger_count:** O número de passageiros na corrida é um recurso.
    * **trip_time_in_secs:** O tempo que levou a corrida. Você deseja prever a tarifa da viagem antes de sua conclusão. No momento, você não sabe a duração da viagem. Portanto, o tempo da viagem não é um recurso e você excluirá essa coluna do modelo.
    * **trip_distance:** A distância da corrida é um recurso.
    * **payment_type:** A forma de pagamento (dinheiro ou cartão de crédito) é um recurso.
    * **fare_amount:** A tarifa total de táxi paga é o rótulo.

O `label` é a coluna que você deseja prever. Ao executar uma tarefa de regressão, o objetivo é prever um valor numérico. Nesse cenário de previsão de preço, o custo de uma corrida de táxi está sendo previsto. Portanto, o **fare_amount** é o rótulo. Os `features` identificados são as entradas que você atribui ao modelo para prever o `label`. Nesse caso, o restante das colunas é usado como recursos ou entradas para prever o valor da tarifa.

## <a name="choose-a-scenario"></a>Escolha um cenário

Para treinar seu modelo, você precisa selecionar na lista de cenários disponíveis de aprendizado de máquina fornecidos pelo Construtor de Modelo. Nesse caso, o cenário é `Price Prediction`. Para obter uma lista mais abrangente, visite o [artigo de visão geral do Construtor de Modelo](../automate-training-with-model-builder.md#scenarios).

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto *TaxiFarePrediction* e selecione **Adicionar** > **Aprendizado de Máquina**.
1. Na etapa de cenário da ferramenta do Construtor de Modelo, selecione cenário de *Previsão de Preço*.

## <a name="load-the-data"></a>Carregar os dados

O Construtor do Modelo aceita dados de duas fontes: um banco de dados do SQL Server ou um arquivo local csv ou tsv. Para obter mais informações sobre os requisitos de formato de dados, visite o seguinte [link](../how-to-guides/install-model-builder.md#limitations).

1. Na etapa de dados da ferramenta do Construtor de Modelo, selecione *Arquivo* na lista suspensa da fonte de dados.
1. Selecione o botão ao lado da caixa de texto *Selecionar um arquivo* e use o Explorador de Arquivos para procurar e selecionar o *taxi-fare-test.csv* no diretório de *Dados*
1. Escolha *fare_amount* na lista suspensa *Rótulo ou Coluna a Prever* e navegue para a etapa de treinamento da ferramenta do Construtor de Modelo.

## <a name="train-the-model"></a>Treinar o modelo

A tarefa de aprendizado de máquina usada para treinar o modelo de previsão de preço neste tutorial é a regressão. Durante o processo de treinamento de modelo, o Construtor de Modelo treina modelos separados usando algoritmos de regressão diferentes e configurações para localizar o modelo com melhor desempenho para seu conjunto de dados.

O tempo necessário para treinar o modelo é proporcional à quantidade de dados. Use este gráfico como orientação para selecionar um valor adequado para o campo `Time to train (seconds)`:

*Tamanho do conjunto de dados  | Tipo de conjunto de dados       | Média Hora de treinar*
------------- | ------------------ | --------------
0 a 10 Mb     | Numérico e texto   | 10 s
10 a 100 Mb   | Numérico e texto   | 10 min
100 a 500 Mb  | Numérico e texto   | 30 min
500 a 1 Gb    | Numérico e texto   | 60 min
Mais de 1 Gb         | Numérico e texto   | Mais de 3 horas

1. Como o arquivo de dados de treinamento é mais de 10MB, use 600 segundos (10 minutos) como o valor para *Tempo de treinamento (segundos)* .
2. Selecione *Iniciar Treinamento*.

Durante o processo de treinamento, os dados de progresso são exibidos na seção `Progress` da etapa de treinamento.

- O status exibe o status de conclusão do processo de treinamento.
- A melhor precisão exibe a precisão do modelo de melhor desempenho encontrado pelo Construtor do Modelo até o momento. Maior precisão significa que o modelo é previsto mais corretamente nos dados de teste. 
- O melhor algoritmo exibe o nome do algoritmo de melhor desempenho executado encontrado pelo Construtor de Modelo até o momento.
- O último algoritmo exibe o nome do algoritmo usado mais recentemente pelo Construtor de Modelo para treinar o modelo.

Após a conclusão do treinamento, navegue até a etapa de avaliação.

## <a name="evaluate-the-model"></a>Avaliar o modelo

O resultado da etapa de treinamento será um modelo que tinha o melhor desempenho. Na etapa de avaliação da ferramenta do Construtor de Modelo, a seção de saída terá o algoritmo usado pelo modelo com melhor desempenho na entrada *Melhor Modelo*, juntamente com as métricas na *Qualidade do Melhor Modelo (RSquared)* . Além disso, uma tabela de resumo contém os cinco modelos principais e suas métricas. Visite o link a seguir para saber mais sobre [métricas de modelo de avaliação](https://docs.microsoft.com/dotnet/machine-learning/resources/metrics).

Se você não estiver satisfeito com suas métricas de precisão, algumas maneiras fáceis de experimentar e aprimorar a precisão do modelo serão aumentar a quantidade de tempo para treinar o modelo ou usar mais dados.

## <a name="use-the-model-for-predictions"></a>Usar o modelo para previsões

Dois projetos serão criados como resultado do processo de treinamento.

- TaxiFarePredictionML.ConsoleApp: Um aplicativo do Console do .NET que contém o código de consumo e de modelo de treinamento.
- TaxiFarePredictionML.Model: Uma biblioteca de classes .NET Standard que contém os modelos de dados que definem o esquema de dados de modelo de entrada e saída, bem como a versão persistente do modelo com melhor desempenho durante o treinamento.

1. Na seção de código da ferramenta do Construtor de Modelo, selecione **Projetos Adicionados** para adicionar os projetos à solução.
1. No gerenciador de soluções, clique com o botão direito do mouse no projeto *TaxiFarePrediction*. Em seguida, selecione **Adicionar > Item Existente**. Para a lista suspensa de tipo de arquivo, selecione `All Files`, navegue até o diretório do projeto *TaxiFarePredictionML.Model* e selecione o arquivo `MLModel.zip`. Em seguida, clique com o botão direito do mouse no arquivo `MLModel.zip` adicionado e selecione *Propriedades*. Para a opção Copiar para Diretório de Saída, selecione *Copiar se for mais recente* na lista suspensa.
1. Clique com botão direito do mouse no projeto *TaxiFarePrediction*. Em seguida, **Adicionar > Referência**. Escolha o nó **Projetos > Solução** e, na lista, confira o projeto *TaxiFarePredictionML.Model* e selecione OK.

4. Abra o arquivo *Program.cs* no projeto *TaxiFarePrediction*.
5. Adicione as seguintes instruções using:

    ```csharp
    using System;
    using Microsoft.ML;
    using TaxiFarePredictionML.Model.DataModels;
    ```

6. Adicione o método `ConsumeModel` à classe `Program`. O `ConsumeModel` criará um `PredictionEngine` com base no modelo gerado pelo Construtor de Modelo para fazer previsões sobre novos dados e imprimi-las no console.

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

7. Adicione o código a seguir ao método `Main` para executar o aplicativo.

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

    A saída gerada pelo programa deve ser semelhante ao trecho a seguir:

    ```bash
    Predicted Fare: 16.82245
    ```

Se precisar fazer referência aos projetos gerados em um momento posterior dentro de outra solução, você poderá encontrá-los no diretório `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como:
> [!div class="checklist"]
> * Preparar e compreender os dados
> * Escolha um cenário
> * Carregar os dados
> * Treinar o modelo
> * Avaliar o modelo
> * Usar o modelo para previsões

Avance para qualquer um dos artigos de instruções a seguir para aprender a implantar seu modelo.

> [!div class="nextstepaction"]
> [Implantar um modelo no Azure Functions](../how-to-guides/serve-model-serverless-azure-functions-ml-net.md)
> [!div class="nextstepaction"]
> [Implantar um modelo em uma API Web](../how-to-guides/serve-model-web-api-ml-net.md)
