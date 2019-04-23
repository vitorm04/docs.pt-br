---
title: Prever os preços usando um aprendiz de regressão com o ML.NET
description: Prever os preços usando um aprendiz de regressão com o ML.NET.
author: aditidugar
ms.author: johalex
ms.date: 03/20/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 49770672ebcff98d8779a888372b5c9f40a55b1d
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611803"
---
# <a name="tutorial-predict-prices-using-a-regression-learner-with-mlnet"></a>Tutorial: Prever os preços usando um aprendiz de regressão com o ML.NET

Este tutorial ilustra como usar o ML.NET para criar uma [modelo de regressão](../resources/glossary.md#regression) para prever preços. Nesse caso, as tarifas de táxi na cidade de Nova York.

> [!NOTE]
> Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações. Para obter mais informações, confira a [Introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Este tutorial e uma amostra relacionada estão usando o **ML.NET versão 0.11** no momento. Saiba mais nas notas de versão no [repositório do GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
> * Compreender o problema
> * Selecionar a tarefa de aprendizado de máquina apropriada
> * Preparar e compreender os dados
> * Criar um pipeline de aprendizado
> * Carregar e transformar os dados
> * Escolher um algoritmo de aprendizado
> * Treinar o modelo
> * Avaliar o modelo
> * Usar o modelo para previsões

## <a name="prerequisites"></a>Pré-requisitos

* [Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.

## <a name="understand-the-problem"></a>Compreender o problema

Este problema trata-se de prever a tarifa de uma viagem de táxi na cidade de Nova York. À primeira vista, pode parecer que depende simplesmente da distância percorrida. No entanto, os taxistas em Nova York cobram valores variados por outros fatores, como passageiros adicionais ou pagamento por cartão de crédito em vez de dinheiro.

## <a name="select-the-appropriate-machine-learning-task"></a>Selecionar a tarefa de aprendizado de máquina apropriada

Convém prever o valor do preço, que é um valor real, com base nos outros fatores no conjunto de dados. Para fazer isso, escolha uma tarefa de aprendizado de máquina de [regressão](../resources/glossary.md#regression).

## <a name="create-a-console-application"></a>Criar um aplicativo de console

1. Abra o Visual Studio 2017. Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus. Na caixa de diálogo **Novo Projeto**, selecione o nó **Visual C#** seguido pelo nó **.NET Core**. Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)**. Na caixa de texto **Nome**, digite "TaxiFarePrediction" e selecione o botão **OK**.

1. Crie um diretório chamado *Dados* em seu projeto para armazenar o conjunto de dados e os arquivos de modelo:

    No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Nova Pasta**. Digite "Data" e pressione Enter.

1. Instale o pacote NuGet **Microsoft.ML**:

    No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Gerenciar Pacotes NuGet**. Escolha "nuget.org" como a origem do Pacote, selecione a guia **Procurar**, pesquise **Microsoft.ML**, selecione o pacote na lista e escolha o botão **Instalar**. Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.

## <a name="prepare-and-understand-the-data"></a>Preparar e compreender os dados

1. Baixe os conjuntos de dados [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) e [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) e salve-os na pasta *Dados* criada na etapa anterior. Esses conjuntos de dados são usados para treinar o modelo de aprendizado de máquina e, em seguida, avaliar a precisão dele. Esses conjuntos de dados são originalmente do [Conjunto de dados NYC TLC Taxi Trip](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse em cada um dos arquivos \*.csv e selecione **Propriedades**. Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.

1. Abra o conjunto de dados **taxi-fare-train.csv** e observe os cabeçalhos de coluna na primeira linha. Dê uma olhada em cada uma das colunas. Compreenda os dados e decida quais colunas são **recursos** e qual é o **rótulo**.

O **rótulo** é o identificador da coluna que você quer prever. Os **recursos** identificados são usados ​​para prever o rótulo.

O conjunto de dados fornecido contém as seguintes colunas:

* **vendor_id:** A ID do taxista é um recurso.
* **rate_code:** O tipo de tarifa da corrida de táxi é um recurso.
* **passenger_count:** O número de passageiros na corrida é um recurso.
* **trip_time_in_secs:** O tempo que levou a corrida. Você deseja prever a tarifa da viagem antes de sua conclusão. No momento, você não sabe a duração da viagem. Portanto, o tempo da viagem não é um recurso e você excluirá essa coluna do modelo.
* **trip_distance:** A distância da corrida é um recurso.
* **payment_type:** A forma de pagamento (dinheiro ou cartão de crédito) é um recurso.
* **fare_amount:** A tarifa total de táxi paga é o rótulo.

## <a name="create-data-classes"></a>Criar classes de dados

Crie classes para os dados de entrada e as previsões:

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.
1. Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *TaxiTrip.cs*. Em seguida, selecione o botão **Adicionar**.
1. Adicione as seguintes diretivas `using` ao novo arquivo:

   [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

Remova a definição de classe existente e adicione o seguinte código, que tem duas classes `TaxiTrip` e `TaxiTripFarePrediction`, ao arquivo *TaxiTrip.cs*:

[!code-csharp[DefineTaxiTrip](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip` é a classe de dados de entrada e tem definições para cada uma das colunas do conjunto de dados. Use o atributo <xref:Microsoft.ML.Data.LoadColumnAttribute> para especificar os índices das colunas de origem no conjunto de dados.

A classe `TaxiTripFarePrediction` representa os resultados previstos. Ela tem um único campo de float, `FareAmount`, com um atributo `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> aplicado. No caso da tarefa de regressão, a coluna **Pontuação** contém valores de rótulo previsto.

> [!NOTE]
> Use o tipo `float` para representar valores de ponto flutuante nas classes de dados de entrada e previsão.

## <a name="define-data-and-model-paths"></a>Definir dados e caminhos de modelo

Adicione as seguintes instruções `using` adicionais ao início do arquivo *Program.cs*:

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

Você precisa criar três campos para conter os caminhos para os arquivos com conjuntos de dados e o arquivo para salvar o modelo:

* `_trainDataPath` contém o caminho para o arquivo com o conjunto de dados usado para treinar o modelo.
* `_testDataPath` contém o caminho para o arquivo com o conjunto de dados usado para avaliar o modelo.
* `_modelPath` contém o caminho para o arquivo em que o modelo treinado está armazenado.

Adicione o seguinte código logo acima do método `Main` para especificar estes caminhos e para a variável `_textLoader`:

[!code-csharp[InitializePaths](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

Ao criar um modelo com o ML.NET, comece criando um Contexto de ML. Isso é comparável conceitualmente ao uso de `DbContext` no Entity Framework. O ambiente fornece um contexto para seu trabalho de aprendizado de máquina que pode ser usado na exceção do acompanhamento e registro em log.

### <a name="initialize-variables-in-main"></a>Inicializar variáveis em Main

Crie uma variável chamada `mlContext` e inicialize-a com uma nova instância de `MLContext`.  Substitua a linha `Console.WriteLine("Hello World!")` pelo seguinte código no método `Main`:

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create the ML Context")]

Adicione o seguinte como a linha seguinte de código no método `Main` para chamar o método `Train`:

[!code-csharp[Train](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Train your model")]

O método `Train` executa as seguintes tarefas:

* Carrega os dados.
* Extrai e transforma os dados.
* Treina o modelo.
* Salva o modelo como um arquivo .zip.
* Retorna o modelo.

O método `Train` treina o modelo. Crie esse método logo abaixo de `Main`, usando o seguinte código:

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

Estamos passando dois parâmetros para o método `Train`. Um `MLContext` para o contexto (`mlContext`) e uma cadeia de caracteres para o caminho do conjunto de dados (`dataPath`). Vamos reutilizar esse método no carregamento de conjuntos de dados.

## <a name="load-and-transform-data"></a>Carregar e transformar dados

Carregue os dados, usando o wrapper `MLContext.Data.LoadFromTextFile` do [método LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29). Ele retorna um <xref:Microsoft.Data.DataView.IDataView>.

Como a entrada e saída de `Transforms`, um `DataView` é o tipo de pipeline de dados fundamental, comparável ao `IEnumerable` para `LINQ`.

No ML.NET, os dados são semelhantes a um modo de exibição SQL. Eles são heterogêneos e avaliados e esquematizados lentamente. O objeto é a primeira parte do pipeline e carrega os dados. Para este tutorial, ele carrega um conjunto de dados com informações sobre preços de corridas de táxi. Isso é usado para criar o modelo e treiná-lo.

Adicione o seguinte código como a primeira linha do método `Train`:

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "loading training dataset")]

Nas próximas etapas, trataremos das colunas pelos nomes definidos na classe `TaxiTrip`.

Quando o modelo é treinado e avaliado, por padrão, os valores na coluna **Rótulo** são considerados os valores corretos a serem previstos. Como queremos prever a tarifa da viagem de táxi, copie a coluna `FareAmount` para a coluna **Label**. Para fazer isso, use a classe de transformação `CopyColumnsEstimator` e adicione o seguinte código:

[!code-csharp[CopyColumnsEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Use the CopyColumnsEstimator")]

O algoritmo que treina o modelo requer recursos **numéricos**, então, é necessário transformar os valores de dados categóricos (`VendorId`, `RateCode` e `PaymentType`) em números (`VendorIdEncoded`, `RateCodeEncoded` e `PaymentTypeEncoded`). Para fazer isso, use a classe de transformação Microsoft.ML.Transforms.OneHotEncodingTransformer>, que atribui valores numéricos de chave diferentes aos valores diferentes em cada uma das colunas, e adicione o seguinte código:

[!code-csharp[OneHotEncodingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Use the OneHotEncodingEstimator")]

A última etapa na preparação de dados combina todas as colunas de recursos na coluna **Features** usando a classe de transformação `mlContext.Transforms.Concatenate`. Por padrão, um algoritmo de aprendizado processa apenas os recursos da coluna **Features**. Adicione o seguinte código:

[!code-csharp[ColumnConcatenatingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a>Escolher um algoritmo de aprendizado

Após adicionar os dados ao pipeline e transformá-los no formato de entrada correto, escolhemos um algoritmo de aprendizado (**aprendiz**). O aprendiz treina o modelo. Escolhemos uma tarefa de **regressão** para esse problema; portanto, usamos um aprendiz `FastTreeRegressionTrainer`, que é um dos aprendizes de regressão fornecidos pelo ML.NET.

O algoritmo de treinamento `FastTreeRegressionTrainer` utiliza o gradient boosting. O aumento de gradiente é uma técnica de aprendizado de máquina para problemas de regressão. Ele cria cada árvore de regressão por etapas. Ele usa uma função de perda predefinida para medir o erro em cada etapa e corrigi-lo no próximo. O resultado é um modelo de previsão que é, na verdade, um conjunto de modelos de previsão mais fracos. Para obter mais informações sobre o aumento de gradiente, consulte [Regressão da árvore de decisão aumentada](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).

Adicione o seguinte código ao método `Train` para adicionar o `FastTreeRegressionTrainer` ao código de processamento de dados adicionado na etapa anterior:

[!code-csharp[FastTreeRegressionTrainer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a>Treinar o modelo

A etapa final é treinar o modelo. Treinamos o modelo, <xref:Microsoft.ML.Data.TransformerChain>, com base no conjunto de dados que foi carregado e transformado. Depois que o avaliador tiver sido definido, treinaremos o modelo usando o <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> e forneceremos os dados de treinamento já carregados. Isso retornará um modelo que será usado nas previsões. `pipeline.Fit()` treina o pipeline e retorna um `Transformer` com base no `DataView` passado. O experimento não será executado até que isso ocorra.

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#11 "Train the model")]

### <a name="save-the-model"></a>Salvar o modelo

Neste ponto, você tem um modelo de tipo <xref:Microsoft.ML.Data.TransformerChain> que pode ser integrado em qualquer um dos seus aplicativos .NET existentes ou novos. Para salvar o modelo em um arquivo .zip, adicione o seguinte código no final do método `Train`:

[!code-csharp[SaveModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Save the model as a .zip file and return the model")]

## <a name="save-the-model-as-a-zip-file"></a>Salvar o modelo como um arquivo .zip

Crie o método `SaveModelAsFile`, logo após o método `Train`, usando o seguinte código:

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

O método `SaveModelAsFile` executa as seguintes tarefas:

* Salva o modelo como um arquivo .zip.

É necessário criar um método para salvar o modelo para que ele possa ser reutilizado e consumido em outros aplicativos. O `ITransformer` tem um método <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> que usa o campo global `_modelPath` e um <xref:System.IO.Stream>. Como queremos salvá-lo como um arquivo zip, vamos criar o `FileStream` imediatamente antes de chamar o método `SaveTo`. Adicione o seguinte código ao método `SaveModelAsFile` como a linha seguinte:

[!code-csharp[SaveToMethod](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Add the SaveTo Method")]

Também poderíamos exibir o local onde o arquivo foi gravado ao gravar uma mensagem de console com o `_modelPath`, usando o seguinte código:

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="evaluate-the-model"></a>Avaliar o modelo

Avaliação é o processo de verificar o quão bem modelo prevê os valores de rótulo. É importante que o modelo faça boas previsões com base em dados que não foram usados para treiná-lo. Uma forma de fazer isso é dividir os dados em conjuntos de dados de treinamento e teste, como neste tutorial. Agora que você treinou o modelo nos dados de treinamento, pode ver o desempenho dos dados de teste.

O método `Evaluate` avalia o modelo. Para criá-lo, adicione o código a seguir abaixo do método `Train`:

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

O método `Evaluate` executa as seguintes tarefas:

* Carrega o conjunto de dados de teste.
* Cria o avaliador de regressão.
* Avalia o modelo e cria métricas.
* Exibe as métricas.

Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `Train`, usando o seguinte código:

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Call the Evaluate method")]

Carregar o conjunto de dados de teste usando o wrapper `MLContext.Data.LoadFromTextFile`. Você pode avaliar o modelo usando esse conjunto de dados como uma verificação de qualidade. Adicione o seguinte código ao método `Evaluate`:

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Load the test dataset")]

Em seguida, use o parâmetro `model` de aprendizado de máquina (um transformador) para inserir os recursos e retornar previsões. Adicione o seguinte código ao método `Evaluate` como a linha seguinte:

[!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Predict using the Transformer")]

O método `RegressionContext.Evaluate` calcula as métricas de qualidade para o `PredictionModel` usando o conjunto de dados especificado. Ele retorna um objeto <xref:Microsoft.ML.Data.RegressionMetrics> que contém as métricas gerais computadas pelos avaliadores de regressão. Para exibi-los a fim de determinar a qualidade do modelo, é preciso primeiro obter as métricas. Adicione o seguinte código ao método `Evaluate` como a linha seguinte:

[!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Compute Metrics")]

Adicione o seguinte código para avaliar o modelo e produzir as métricas de avaliação:

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

[RSquared](../resources/glossary.md#coefficient-of-determination) é outra métrica de avaliação dos modelos de regressão. RSquared aceita valores entre 0 e 1. Quanto mais perto de 1 estiver o valor, melhor o modelo será. Adicione o seguinte código ao método `Evaluate` para exibir o valor RSquared:

[!code-csharp[DisplayRSquared](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#18 "Display the RSquared metric.")]

[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) é uma das métricas de avaliação do modelo de regressão. Quanto menor, melhor o modelo. Adicione o seguinte código ao método `Evaluate` para exibir o valor RMS:

[!code-csharp[DisplayRMS](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a>Usar o modelo para previsões

## <a name="predict-the-test-data-outcome-with-the-model-and-a-single-comment"></a>Prever os resultados dos dados de teste com o modelo e um único comentário

Crie o método `TestSinglePrediction`, logo após o método `Evaluate`, usando o seguinte código:

```csharp
private static void TestSinglePrediction(MLContext mlContext)
{

}
```

O método `TestSinglePrediction` executa as seguintes tarefas:

* Cria um único comentário dos dados de teste.
* Prevê o valor da tarifa com base nos dados de teste.
* Combina dados de teste e previsões para relatórios.
* Exibe os resultados previstos.

Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `Evaluate`, usando o seguinte código:

[!code-csharp[CallTestSinglePrediction](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#20 "Call the TestSinglePrediction method")]

Como queremos carregar o modelo do arquivo zip que foi salvo, vamos criar o `FileStream` imediatamente antes de chamar o método `Load`. Adicione o seguinte código ao método `TestSinglePrediction` como a linha seguinte:

[!code-csharp[LoadTheModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#21 "Load the model")]

Enquanto o `model` é um `transformer` que opera em muitas linhas de dados, um cenário de produção muito comum é a necessidade de previsões em exemplos individuais. O <xref:Microsoft.ML.PredictionEngine%602> é um wrapper que é retornado do método `CreatePredictionEngine`. Adicionaremos o seguinte código para criar `PredictionEngine` como a próxima linha no método `TestSinglePrediction`:

[!code-csharp[MakePredictionEngine](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#22 "Create the PredictionFunction")]

Este tutorial usa uma viagem de teste dentro dessa classe. Posteriormente, você pode adicionar outros cenários para fazer experiências com o modelo. Adicione uma corrida de teste à previsão do modelo treinado no método `TestSinglePrediction` ao criar uma instância de `TaxiTrip`:

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#23 "Create test data for single prediction")]

Podemos usar isso para prever as tarifas com base em uma única instância dos dados da corrida de táxi. Para obter uma previsão, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> nos dados. Observe que os dados de entrada são uma cadeia de caracteres e o modelo inclui a personalização. Seu pipeline está em sincronia durante o treinamento e a previsão. Você não precisou escrever código de pré-processamento/personalização especificamente para previsões, e a mesma API cuida das previsões de lote e de uso único.

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#24 "Create a prediction of taxi fare")]

Para exibir a tarifa prevista da corrida especificada, adicione o código a seguir ao método `TestSinglePrediction`:

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#25 "Display the prediction.")]

Execute o programa para ver a tarifa de táxi prevista para o seu caso de teste.

Parabéns! Agora você criou com sucesso um modelo de aprendizado de máquina para prever tarifas de táxi, avaliou sua precisão e o usou para fazer previsões. Encontre o código-fonte deste tutorial no repositório do GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction).

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como:

> [!div class="checklist"]
> * Compreender o problema
> * Selecionar a tarefa de aprendizado de máquina apropriada
> * Preparar e compreender os dados
> * Criar um pipeline de aprendizado
> * Carregar e transformar os dados
> * Escolher um algoritmo de aprendizado
> * Treinar o modelo
> * Avaliar o modelo
> * Usar o modelo para previsões

Avance para o próximo tutorial para saber mais.

> [!div class="nextstepaction"]
> [Clustering de Iris](iris-clustering.md)
