---
title: 'Tutorial: Previsão de demanda de aluguel de bicicletas - série socorrida'
description: Este tutorial mostra como prever a demanda por um serviço de aluguel de bicicletas usando análise siporida de séries tempois e ML.NET.
ms.date: 11/07/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: 026421d7b1b2a0e39118ae712780ca7fc8f6e444
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76921251"
---
# <a name="tutorial-forecast-bike-rental-service-demand-with-time-series-analysis-and-mlnet"></a>Tutorial: Previsão da demanda de serviço de aluguel de bicicletas com análise de séries tempois e ML.NET

Saiba como prever a demanda por um serviço de aluguel de bicicletas usando análise de séries tempois univariadas em dados armazenados em um banco de dados do SQL Server com ML.NET.

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
>
> * Compreender o problema
> * Carregar dados de um banco de dados
> * Crie um modelo de previsão
> * Avaliar modelo de previsão
> * Salvar um modelo de previsão
> * Use um modelo de previsão

## <a name="prerequisites"></a>Pré-requisitos

- [Visual Studio 2017 versão 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) com a carga de trabalho ".NET Core cross-platform development" instalada.

## <a name="time-series-forecasting-sample-overview"></a>Visão geral da amostra da série temporal

Esta amostra é um **aplicativo de console C# .NET Core** que prevê a demanda por aluguel de bicicletas usando um algoritmo de análise de séries tempois univariado conhecido como Análise de Espectro Único. O código para esta amostra pode ser encontrado no repositório [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) no GitHub.

## <a name="understand-the-problem"></a>Compreender o problema

Para executar uma operação eficiente, o gerenciamento de estoque desempenha um papel fundamental. Ter muito de um produto em estoque significa que produtos não vendidos sentados nas prateleiras não geram nenhuma receita. Ter muito pouco produto leva a vendas perdidas e clientes comprando de concorrentes. Portanto, a pergunta constante é: qual é a quantidade ideal de inventário para manter na mão? A análise de séries tempois ajuda a fornecer uma resposta a essas perguntas olhando dados históricos, identificando padrões e usando essas informações para prever valores em algum momento no futuro.

A técnica para analisar os dados utilizados neste tutorial é a análise univariada da série temporal. A análise univariada da série temporal analisa uma única observação numérica durante um período de tempo em intervalos específicos, como vendas mensais.

O algoritmo usado neste tutorial é [o Single Spectrum Analysis(SSA).](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf) A SSA funciona decompondo uma série temporal em um conjunto de componentes principais. Esses componentes podem ser interpretados como as partes de um sinal que correspondem a tendências, ruídos, sazonalidade e muitos outros fatores. Então, esses componentes são reconstruídos e usados para prever valores algum tempo no futuro.

## <a name="create-console-application"></a>Criar um aplicativo de console

1. Crie um novo **aplicativo de console C# .NET Core** chamado "BikeDemandForecasting".
1. Instale **Microsoft.ML** versão **1.4.0** NuGet
    1. No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.
    1. Escolha "nuget.org" como fonte do Pacote, selecione a guia **Procurar,** procurar **Microsoft.ML**.
    1. Verifique a **caixa de seleção Incluir pré-lançamento.**
    1. Selecione o botão **Instalar**.
    1. Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo Aceitação da Licença, se concordar com o termos de licença para os pacotes listados.
    1. Repita estas etapas para **System.Data.SqlClient** versão **4.7.0** e **Microsoft.ML.TimeSeries** versão **1.4.0**.

### <a name="prepare-and-understand-the-data"></a>Preparar e compreender os dados

1. Crie um diretório chamado *Data*.
1. Baixe o arquivo de banco de dados [ *DailyDemand.mdf* ](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) e salve-o no diretório *Data.*

> [!NOTE]
> Os dados usados neste tutorial vêm do conjunto de dados de compartilhamento de [bicicletas UCI](https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset). Fanaee-T, Hadi, e Gama, João, 'Rotulagem de eventos combinando detectores de conjunto e conhecimento de fundo', Progresso em Inteligência Artificial (2013): pp. 1-15, Springer Berlin Heidelberg, [Web Link](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).

O conjunto de dados original contém várias colunas correspondentes à sazonalidade e ao clima. Para a brevidade e porque o algoritmo usado neste tutorial requer apenas os valores de uma única coluna numérica, o conjunto de dados original foi condensado para incluir apenas as seguintes colunas:

- **dia dteday**: A data da observação.
- **ano**: O ano codificado da observação (0=2011, 1=2012).
- **cnt**: O número total de aluguel de bicicletas para esse dia.

O conjunto de dados original é mapeado em uma tabela de banco de dados com o seguinte esquema em um banco de dados SQL Server.

```SQL
CREATE TABLE [Rentals] (
    [RentalDate] DATE NOT NULL,
    [Year] INT NOT NULL,
    [TotalRentals] INT NOT NULL
);
```

A seguir está uma amostra dos dados:

| Data de aluguel | Ano | TotalRentals |
| --- | --- | --- |
|1/1/2011|0|985|
|1/2/2011|0|801|
|1/3/2011|0|1349|

### <a name="create-input-and-output-classes"></a>Criar classes de entrada e saída

1. Abra *Program.cs* arquivo e `using` substitua as instruções existentes pelo seguinte:

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L1-L8)]

1. Crie a classe `ModelInput`. Abaixo `Program` da classe, adicione o seguinte código.

    [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L120-L127)]

    A `ModelInput` classe contém as seguintes colunas:

    - **Data de aluguel**: A data da observação.
    - **Ano**: Ano codificado da observação (0=2011, 1=2012).
    - **TotalRentals**: O número total de aluguéis de bicicletas para esse dia.

1. Crie `ModelOutput` classe abaixo da `ModelInput` classe recém-criada.

    [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L129-L136)]

    A `ModelOutput` classe contém as seguintes colunas:

    - **Preços Previstos**: Os valores previstos para o período previsto.
    - **LowerBoundRentals**: Os valores mínimos previstos para o período previsto.
    - **UpperBoundRentals**: Os valores máximos previstos para o período previsto.

### <a name="define-paths-and-initialize-variables"></a>Defina caminhos e inicialize variáveis

1. Dentro `Main` do método, defina variáveis para armazenar a localização de seus dados, string de conexão e onde salvar o modelo treinado.

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L16-L19)]

1. Inicialize `mlContext` a variável com [`MLContext`](xref:Microsoft.ML.MLContext) uma nova instância de `Main` adicionando a seguinte linha ao método.

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L21)]

    A [`MLContext`](xref:Microsoft.ML.MLContext) classe é um ponto de partida para todas as operações ML.NET, e a inicialização do mlContext cria um novo ambiente ML.NET que pode ser compartilhado entre os objetos do fluxo de trabalho de criação de modelos. Ele é semelhante, conceitualmente, a `DBContext` no Entity Framework.

## <a name="load-the-data"></a>Carregar os dados

1. Criar `DatabaseLoader` que carrega registros `ModelInput`do tipo .

    [!code-csharp [CreateDBLoader](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L23)]

1. Defina a consulta para carregar os dados do banco de dados.

    [!code-csharp [DefineSQLQuery](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L25)]

    ML.NET algoritmos esperam que [`Single`](xref:System.Single)os dados sejam do tipo . Portanto, valores numéricos provenientes do banco [`Real`](xref:System.Data.SqlDbType)de dados que não são do tipo , [`Real`](xref:System.Data.SqlDbType)um valor de ponto flutuante de precisão única, devem ser convertidos para .

    As `Year` `TotalRental` colunas e colunas são tipos inteiros no banco de dados. Usando `CAST` a função incorporada, ambos são `Real`lançados para .

1. Crie `DatabaseSource` um para se conectar ao banco de dados e execute a consulta.

    [!code-csharp [CreateDBSource](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L27-L29)]

1. Carregar os dados em um `IDataView`.

    [!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L31)]

1. O conjunto de dados contém dois anos de dados. Apenas os dados do primeiro ano são utilizados para a formação, o segundo ano é realizado para comparar os valores reais com a previsão produzida pelo modelo. Filtre os [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) dados usando a transformação.

    [!code-csharp [SplitData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L33-L34)]

    Para o primeiro ano, apenas `Year` os valores da coluna `upperBound` inferior a 1 são selecionados definindo o parâmetro para 1. Por outro lado, para o segundo ano, valores maiores ou iguais a 1 são selecionados definindo o `lowerBound` parâmetro para 1.

## <a name="define-time-series-analysis-pipeline"></a>Definir pipeline de análise de séries tempois

1. Defina um pipeline que usa o [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) para prever valores em um conjunto de dados em série stempo.

    [!code-csharp [DefinePipeline](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L36-L45)]

    O `forecastingPipeline` conjunto de dados leva 365 pontos de dados para o primeiro ano e amostra ou divide o `seriesLength` conjunto de dados da série temporal em intervalos de 30 dias (mensais), conforme especificado pelo parâmetro. Cada uma dessas amostras é analisada por uma janela semanal ou de 7 dias. Ao determinar qual é o valor previsto para o próximo período, os valores dos sete dias anteriores são usados para fazer uma previsão. O modelo prevê sete períodos no futuro, `horizon` conforme definido pelo parâmetro. Como uma previsão é um palpite, nem sempre é 100% precisa. Portanto, é bom conhecer a gama de valores nos melhores e piores cenários, conforme definido pelos limites superior e inferior. Neste caso, o nível de confiança para os limites inferior e superior é definido para 95%. O nível de confiança pode ser aumentado ou diminuído em conformidade. Quanto maior o valor, maior a faixa entre os limites superior e inferior para alcançar o nível de confiança desejado.

1. Use [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) o método para treinar o modelo e `forecastingPipeline`encaixar os dados no previamente definido .

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L47)]

## <a name="evaluate-the-model"></a>Avalie o modelo

Avalie o desempenho do modelo, prevendo os dados do próximo ano e comparando-os com os valores reais.

1. Abaixo `Main` do método, crie um `Evaluate`novo método de utilidade chamado .

    ```csharp
    static void Evaluate(IDataView testData, ITransformer model, MLContext mlContext)
    {

    }
    ```

1. Dentro `Evaluate` do método, preveja os dados [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) do segundo ano utilizando o método com o modelo treinado.

    [!code-csharp [EvaluateForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L62)]

1. Obtenha os valores reais a [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) partir dos dados usando o método.

    [!code-csharp [GetActualRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L65-L67)]

1. Obtenha os valores [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) de previsão usando o método.

    [!code-csharp [GetForecastRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L70-L72)]

1. Calcule a diferença entre os valores reais e de previsão, comumente referido como erro.

    [!code-csharp [CalculateError](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L75)]

1. Medir o desempenho calculando os valores de erro absoluto médio e erro quadrado de média raiz.

    [!code-csharp [CalculateMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L78-L79)]

    Para avaliar o desempenho, são utilizadas as seguintes métricas:

    - **Erro Absoluto Médio**: Mede o quão próximas as previsões são do valor real. Este valor varia entre 0 e infinito. Quanto mais perto de 0, melhor a qualidade do modelo.
    - **Erro quadrado de média raiz**: resume o erro no modelo. Este valor varia entre 0 e infinito. Quanto mais perto de 0, melhor a qualidade do modelo.

1. Saída as métricas para o console.

    [!code-csharp [OutputMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L82-L85)]

1. Use `Evaluate` o método `Main` dentro do método.

    [!code-csharp [EvaluateModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L49)]

## <a name="save-the-model"></a>Salvar o modelo

Se você estiver satisfeito com o seu modelo, guarde-o para uso posterior em outros aplicativos.

1. No `Main` método, crie [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602)um . [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602)é um método de conveniência para fazer previsões únicas.

    [!code-csharp [CreateTimeSeriesEngine](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L51)]

1. Salve o modelo em `MLModel.zip` um arquivo chamado conforme `modelPath` especificado pela variável previamente definida. Use [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) o método para salvar o modelo.

    [!code-csharp [SaveModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L52)]

## <a name="use-the-model-to-forecast-demand"></a>Use o modelo para prever a demanda

1. Abaixo `Evaluate` do método, crie um `Forecast`novo método de utilidade chamado .

    ```csharp
    static void Forecast(IDataView testData, int horizon, TimeSeriesPredictionEngine<ModelInput, ModelOutput> forecaster, MLContext mlContext)
    {

    }
    ```

1. Dentro `Forecast` do método, [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) use o método para prever aluguéis para os próximos sete dias.

    [!code-csharp [SingleForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L91)]

1. Alinhar os valores reais e de previsão para sete períodos.

    [!code-csharp [GetForecastOutput](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L93-L108)]

1. Iterar através da saída de previsão e exibi-lo no console.

    [!code-csharp [DisplayForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L111-L116)]

## <a name="run-the-application"></a>Executar o aplicativo

1. Dentro `Main` do método, `Forecast` chame o método.

    [!code-csharp [BuildForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L54)]

1. Execute o aplicativo. Saída semelhante à abaixo deve aparecer no console. Para a brevidade, a saída foi condensada.

    ```text
    Evaluation Metrics
    ---------------------
    Mean Absolute Error: 726.416
    Root Mean Squared Error: 987.658

    Rental Forecast
    ---------------------
    Date: 1/1/2012
    Actual Rentals: 2294
    Lower Estimate: 1197.842
    Forecast: 2334.443
    Upper Estimate: 3471.044

    Date: 1/2/2012
    Actual Rentals: 1951
    Lower Estimate: 1148.412
    Forecast: 2360.861
    Upper Estimate: 3573.309
    ```

A inspeção dos valores reais e previstos mostra as seguintes relações:

![Comparação real vs previsão](./media/time-series-demand-forecasting/forecast.png)

Embora os valores previstos não estejam prevendo o número exato de aluguéis, eles fornecem uma faixa mais estreita de valores que permite uma operação para otimizar seu uso de recursos.

Parabéns! Agora você construiu com sucesso um modelo de aprendizado de máquina de séries temporias para prever a demanda de aluguel de bicicletas.

Você pode encontrar o código fonte para este tutorial no repositório [dotnet/machinelearning-samples.](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand)

## <a name="next-steps"></a>Próximas etapas

- [Tarefas de aprendizado de máquina no ML.NET](../resources/tasks.md)
- [Aprimorar a precisão do modelo](../resources/improve-machine-learning-model-ml-net.md)
