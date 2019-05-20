---
title: Use o ML.NET em um cenário de detecção de anomalias de vendas
description: Descubra como usar o ML.NET em um cenário de detecção de anomalias de vendas de produto para compreender como analisar os dados de anomalias de ponto de alteração e picos para tomar as devidas providências.
ms.date: 05/06/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: b0dbd8793e2be3973c37f0f78bc0ddd61b6bfea7
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65065649"
---
# <a name="tutorial-use-mlnet-for-product-sales-anomaly-detection"></a>Tutorial: Use o ML.NET para detecção de anomalias de vendas do produto 

Este tutorial de exemplo ilustra o uso do ML.NET para detectar anomalias nos dados de vendas de produto para executar a ação apropriada por meio de um aplicativo de console do .NET Core usando C# no Visual Studio de 2019. 

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
> * Carregar os dados
> * Treinar o modelo para detecção de anomalias de pico
> * Detectar anomalias de pico com o modelo treinado
> * Treinar o modelo para detecção de anomalias de ponto de alteração
> * Detectar anomalias de ponto de alteração com o modelo treinado

Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection).

## <a name="prerequisites"></a>Pré-requisitos

* [Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.

* [O conjunto de dados product-sales.csv](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> Os dados de formato em `product-sales.csv` baseiam-se no conjunto de dados "Vendas de xampu no período de três anos" originalmente adquiridos do DataMarket e fornecidos pela TSDL (Biblioteca de Dados de Série Temporal), criado por Rob Hyndman. Conjunto de dados de "Vendas de xampu no período de três anos" licenciado sob a Licença Aberta Padrão do DataMarket.

## <a name="create-a-console-application"></a>Criar um aplicativo de console

1. Crie um **Aplicativo de Console do .NET Core** chamado "ProductSalesAnomalyDetection".

2. Crie um diretório chamado *Data* no seu projeto para salvar os arquivos do conjunto de dados.

3. Instalar o **Pacote NuGet Microsoft.ML**:

    No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**. Escolha "nuget.org" como a origem do pacote, selecione a guia Procurar, pesquise **Microsoft.ML**, selecione o pacote **v1.0.0** na lista e selecione o botão **Instalar**. Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados. Repita essas etapas para **Microsoft.ML.TimeSeries v0.12.0**.

4. Adicione as seguintes instruções `using` à parte superior do arquivo *Program.cs*:

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a>Baixar os dados

1. Baixe o conjunto de dados e salve-o na pasta *Data* criada anteriormente:

   * Clique com o botão direito do mouse em [*product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) e selecione "Salvar Link (ou destino) como…"

     Salve o arquivo \*.csv na pasta *Data* ou, depois de salvá-lo em outro lugar, mova o arquivo \*.csv para a pasta *Data*.

2. No Gerenciador de Soluções, clique com o botão direito do mouse no arquivo \*.csv e selecione **Propriedades**. Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.

A tabela a seguir é uma visualização de dados do seu arquivo \*.csv:

|Mês  |ProductSales |
|-------|-------------|
|1-Jan  |    271      |
|2-Jan  |    150.9    |
|.....  |    .....    |
|1-Feb  |    199.3    |
|.....  |    .....    |

### <a name="create-classes-and-define-paths"></a>Criar classes e definir demarcadores

Em seguida, defina a estrutura de dados de classe de entrada.

Adicione uma nova classe ao seu projeto:

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e, em seguida, selecione **Adicionar > Novo Item**.

2. Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *ProductSalesData.cs*. Em seguida, selecione o botão **Adicionar**.

O arquivo *ProductSalesData.cs* é aberto no editor de códigos. Adicione a seguinte instrução `using` à parte superior do *ProductSalesData.cs*:

```csharp
using Microsoft.ML.Data;
```

Remova a definição de classe existente e adicione o seguinte código, que tem duas classes, `ProductSalesData` e `ProductSalesPrediction`, ao arquivo *ProductSalesData.cs*:

[!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/ProductSalesData.cs#DeclareTypes "Declare data record types")]

`ProductSalesData` especifica uma classe de dados de entrada. O atributo [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) especifica quais colunas (por índice de coluna) no conjunto de dados devem ser carregadas. 

Adicione as seguintes instruções `using` adicionais ao início do arquivo *Program.cs*:

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

Você precisa criar dois campos globais para armazenar o caminho do arquivo de conjunto de dados baixado recentemente e o caminho do arquivo de modelo salvo:

* `_dataPath` tem o demarcador para o conjunto de dados usado para treinar o modelo.
* O `_docsize` tem o número de registros no arquivo de conjunto de dados. Você usará isso para calcular `pvalueHistoryLength`.

Adicione o seguinte código à linha logo acima do método `Main` para especificar estes caminhos:

[!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DeclareGlobalVariables "Declare global variables")]

A [classe MLContext](xref:Microsoft.ML.MLContext) é um ponto de partida para todas as operações do ML.NET e a inicialização do `mlContext` cria um ambiente do ML.NET que pode ser compartilhado entre os objetos de fluxo de trabalho da criação de modelo. Ele é semelhante, conceitualmente, a `DBContext` no Entity Framework.

### <a name="initialize-variables-in-main"></a>Inicializar variáveis em Main

Substitua a linha `Console.WriteLine("Hello World!")` no método `Main` pelo seguinte código para declarar e inicializar a variável `mlContext`:

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateMLContext "Create the ML Context")]

### <a name="load-the-data"></a>Carregar os dados

Os dados do ML.NET são representados como uma [classe IDataView](xref:Microsoft.ML.IDataView). `IDataView` é uma maneira flexível e eficiente de descrever dados tabulares (numéricos e texto). Os dados podem ser carregados de um arquivo de texto ou em tempo real (por exemplo, banco de dados SQL ou arquivos de log) para um objeto `IDataView`. Adicione o seguinte código como a próxima linha do método `Main()`:

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#LoadData "loading dataset")]

O [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) define o esquema de dados e lê o arquivo. Ele usa as variáveis de caminho de dados e retorna uma `IDataView`.

## <a name="ml-task---time-series-anomaly-detection"></a>Tarefa de ML – detecção de anomalias de série temporal 

Detecção de anomalias sinaliza comportamentos ou eventos incomuns ou inesperados. Ela dá dicas de em que local procurar problemas e ajuda a responder à pergunta "Isso é estranho?".

![Isso é estranho](./media/sales-anomaly-detection/anomalydetection.png)

A detecção de anomalias é o processo de detectar exceções de dados de série temporal; pontos em uma série temporal de entrada em que o comportamento não é o esperado ou "estranho".

Isso pode ser útil de várias formas. Por exemplo:

Se você tiver um carro, talvez queira saber: Essa leitura do medidor de gasolina está normal ou tenho um vazamento?
Se você estiver monitorando o consumo de energia, vai querer saber: Há uma interrupção?

Há dois tipos de anomalias de série temporal que podem ser detectados: 

* **Picos** indicam intermitências temporárias de comportamentos anormais no sistema. 

* **Pontos de alteração** indicam o início de alterações persistentes ao longo do tempo no sistema. 

No ML.NET, os algoritmos de Detecção de Pico IID ou Detecção de Ponto de Alteração IID são adequados para [conjuntos de dados independentes e distribuídos de forma idêntica](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables). 

Você vai analisar os mesmos dados de vendas do produto para detectar picos e pontos de alteração. O processo de criar e treinar o modelo é o mesmo para detecção de pico e detecção de ponto de alteração; a principal diferença é o algoritmo de detecção específico usado.

## <a name="spike-detection"></a>Detecção de pico 

A meta da detecção de pico é identificar picos repentinos, mas temporários, que diferem significativamente da maioria dos valores de dados de série temporal. É importante detectar esses itens raros, eventos ou observações suspeitos de maneira oportuna para que sejam minimizados. A abordagem a seguir pode ser usada para detectar uma variedade de anomalias, como: interrupções, ataques cibernéticos ou conteúdo da Web viral. A imagem a seguir é um exemplo de picos em um conjunto de dados de série temporal:

![SpikeDetection](./media/sales-anomaly-detection/SpikeDetection.png)

### <a name="create-the-detectspike-method"></a>Crie o método DetectSpike()

Adicione a seguinte chamada ao método `DetectSpike()` como a próxima linha de código no método `Main()`:

[!code-csharp[CallDetectSpike](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectSpike)]

O método `DetectSpike()` executa as seguintes tarefas:

* Treina o modelo.
* Detecta picos com base em dados históricos de vendas.
* Exibe os resultados.

Crie o método `DetectSpike()`, logo após o método `Main()`, usando o seguinte código:

```csharp
static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

Use [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) para treinar o modelo para a detecção de pico. Adicione-o ao método `DetectChangepoint()` com o seguinte código:

[!code-csharp[AddSpikeTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddSpikeTrainer)]

Ajuste o modelo aos dados `productSales` e retorne o modelo treinado adicionando o seguinte como a próxima linha de código no método `DetectSpike()`:

[!code-csharp[TrainModel1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel1)]

O método [Fit()](xref:Microsoft.ML.Data.TrivialEstimator%601.Fit%2A) treina o modelo transformando o conjunto de dados e aplicando o treinamento.

Adicione a seguinte linha de código para transformar os dados `productSales` como a próxima linha no método `DetectSpike()`:

[!code-csharp[TransformData1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData1)]

O código anterior usa o método [Transform](xref:Microsoft.ML.ITransformer.Transform%2A) para fazer previsões para várias linhas de entrada fornecidas por um conjunto de dados de teste.

Converta seu `transformedData` em um `IEnumerable` fortemente tipado para exibição mais fácil usando o método [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) com o código a seguir:

[!code-csharp[CreateEnumerable1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable1)]

Crie uma linha de cabeçalho de exibição usando o seguinte código <xref:System.Console.WriteLine?displayProperty=nameWithType>:

[!code-csharp[DisplayHeader1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader1)]

Você exibirá as informações a seguir nos resultados da detecção de pico:

* `Alert` indica um alerta de pico para um ponto de dados específico.

* `Score` é o valor `ProductSales` para um dado ponto de dados no conjunto de dados.

* `P-Value` O "P" significa probabilidade. Isso indica a probabilidade de esse ponto de dados ser uma anomalia. 

Use o seguinte código para iterar por `predictions` `IEnumerable` e exibir os resultados:

[!code-csharp[DisplayResults1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults1)]

## <a name="spike-detection-results"></a>Resultados da detecção de pico

Seus resultados devem ser semelhantes aos seguintes. Durante o processamento, as mensagens são exibidas. Você pode ver avisos ou mensagens de processamento. Eles foram removidos dos seguintes resultados para maior clareza.

```console
Detect temporary changes in pattern
=============== Training the model ===============
=============== End of training process ===============
Alert   Score   P-Value
0       271.00  0.50
0       150.90  0.00
0       188.10  0.41
0       124.30  0.13
0       185.30  0.47
0       173.50  0.47
0       236.80  0.19
0       229.50  0.27
0       197.80  0.48
0       127.90  0.13
1       341.50  0.00 <-- Spike detected
0       190.90  0.48
0       199.30  0.48
0       154.50  0.24
0       215.10  0.42
0       278.30  0.19
0       196.40  0.43
0       292.00  0.17
0       231.00  0.45
0       308.60  0.18
0       294.90  0.19
1       426.60  0.00 <-- Spike detected
0       269.50  0.47
0       347.30  0.21
0       344.70  0.27
0       445.40  0.06
0       320.90  0.49
0       444.30  0.12
0       406.30  0.29
0       442.40  0.21
1       580.50  0.00 <-- Spike detected
0       412.60  0.45
1       687.00  0.01 <-- Spike detected
0       480.30  0.40
0       586.30  0.20
0       651.90  0.14
```

## <a name="change-point-detection"></a>Detecção de ponto de alteração

`Change points` são alterações persistentes em uma distribuição de valores de fluxo de evento de série temporal, como alterações de nível e tendências. Essas alterações persistentes duram muito mais que `spikes` e podem indicar eventos catastróficos. `Change points` normalmente não estão visíveis a olho nu, mas podem ser detectados em seus dados usando abordagens como o método a seguir.  A imagem a seguir é um exemplo de uma detecção de ponto de alteração:

![ChangePointDetection](./media/sales-anomaly-detection/ChangePointDetection.png)

### <a name="create-the-detectchangepoint-method"></a>Crie o método DetectChangepoint()

Adicione a seguinte chamada ao método `DetectChangepoint()` como a próxima linha de código no método `Main()`:

[!code-csharp[CallDetectChangepoint](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectChangepoint)]

O método `DetectChangepoint()` executa as seguintes tarefas:

* Treina o modelo.
* Detecta pontos de alteração com base em dados históricos de vendas.
* Exibe os resultados.

Crie o método `DetectChangepoint()`, logo após o método `Main()`, usando o seguinte código:

```csharp
static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

O [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) é usado para treinar o modelo para a detecção de ponto de alteração. Adicione-o ao método `DetectChangepoint()` com o seguinte código:

[!code-csharp[AddChangepointTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddChangepointTrainer)]

Como você fez antes, ajuste o modelo aos dados `productSales` e retorne o modelo treinado adicionando o seguinte como a próxima linha de código no método `DetectChangePoint()`:

[!code-csharp[TrainModel2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel2)]

Use o método `Transform()` para transformar os dados `Training` adicionando o seguinte código a `DetectChangePoint()`:

[!code-csharp[TransformData2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData2)]

Como você fez antes, converta seu `transformedData` em um `IEnumerable` fortemente tipado para exibição mais fácil usando o método `CreateEnumerable()` com o código a seguir:

[!code-csharp[CreateEnumerable2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable2)]

Crie um cabeçalho de exibição com o código a seguir como a próxima linha no método `DetectChangePoint()`:

[!code-csharp[DisplayHeader2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader2)]

Você exibirá as informações a seguir nos resultados da detecção de ponto de alteração:

* `Alert` indica um alerta de ponto de alteração para um ponto de dados específico.
* `Score` é o valor `ProductSales` para um dado ponto de dados no conjunto de dados.
* `P-Value` O "P" significa probabilidade. Isso indica a probabilidade de esse ponto de dados ser uma anomalia. 
* `Martingale value` é usado para identificar o quão "estranho" um ponto de dados é com base na sequência de valores de P.  

Itere por `predictions` `IEnumerable` e exiba os resultados com o código a seguir:

[!code-csharp[DisplayResults2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults2)]

## <a name="change-point-detection-results"></a>Resultados da detecção de ponto de alteração

Seus resultados devem ser semelhantes aos seguintes. Durante o processamento, as mensagens são exibidas. Você pode ver avisos ou mensagens de processamento. Eles foram removidos dos seguintes resultados para maior clareza.

```console
Detect Persistent changes in pattern
=============== Training the model Using Change Point Detection Algorithm===============
=============== End of training process ===============
Alert   Score   P-Value Martingale value
0       271.00  0.50    0.00
0       150.90  0.00    2.33
0       188.10  0.41    2.80
0       124.30  0.13    9.16
0       185.30  0.47    9.77
0       173.50  0.47    10.41
0       236.80  0.19    24.46
0       229.50  0.27    42.38
1       197.80  0.48    44.23 <-- alert is on, predicted changepoint
0       127.90  0.13    145.25
0       341.50  0.00    0.01
0       190.90  0.48    0.01
0       199.30  0.48    0.00
0       154.50  0.24    0.00
0       215.10  0.42    0.00
0       278.30  0.19    0.00
0       196.40  0.43    0.00
0       292.00  0.17    0.01
0       231.00  0.45    0.00
0       308.60  0.18    0.00
0       294.90  0.19    0.00
0       426.60  0.00    0.00
0       269.50  0.47    0.00
0       347.30  0.21    0.00
0       344.70  0.27    0.00
0       445.40  0.06    0.02
0       320.90  0.49    0.01
0       444.30  0.12    0.02
0       406.30  0.29    0.01
0       442.40  0.21    0.01
0       580.50  0.00    0.01
0       412.60  0.45    0.01
0       687.00  0.01    0.12
0       480.30  0.40    0.08
0       586.30  0.20    0.03
0       651.90  0.14    0.09
```

Parabéns! Você agora criou com êxito os modelos de machine learning para detectar anomalias de pontos de alteração e picos nos dados de vendas.

Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection).

Neste tutorial, você aprendeu como:
> [!div class="checklist"]
> * Carregar os dados
> * Treinar o modelo para detecção de anomalias de pico
> * Detectar anomalias de pico com o modelo treinado
> * Treinar o modelo para detecção de anomalias de ponto de alteração
> * Detectar anomalias de ponto de alteração com o modo treinado

## <a name="next-steps"></a>Próximas etapas

Confira o repositório do GitHub de exemplos de Machine Learning para explorar um exemplo de Detecção de Anomalias de Consumo de Energia.
> [!div class="nextstepaction"]
> [dotnet/machinelearning-samples GitHub repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/TimeSeries_PowerAnomalyDetection)
