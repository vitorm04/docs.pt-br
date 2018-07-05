---
title: Usar o ML.NET para prever tarifas de táxi em Nova York (regressão)
description: Saiba como usar o ML.NET em um cenário de regressão.
author: aditidugar
ms.author: johalex
ms.date: 06/18/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 690e39dcbd02d81b8d4afe918a74795aa02f7fc6
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314959"
---
# <a name="tutorial-use-mlnet-to-predict-new-york-taxi-fares-regression"></a>Tutorial: Usar o ML.NET para prever tarifas de táxi em Nova York (regressão)

> [!NOTE]
> Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações. Para obter mais informações, visite [a introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Este tutorial ilustra como usar o ML.NET para criar um [modelo de regressão](../resources/glossary.md#regression) para prever tarifas de táxi em Nova York.

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

* [Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.

## <a name="understand-the-problem"></a>Compreender o problema

Esse problema está centrado na **previsão da tarifa de uma viagem de táxi na cidade de Nova York**. À primeira vista, pode parecer que depende simplesmente da distância percorrida. No entanto, os taxistas em Nova York cobram valores variados por outros fatores, como passageiros adicionais ou pagamento por cartão de crédito em vez de dinheiro.

## <a name="select-the-appropriate-machine-learning-task"></a>Selecionar a tarefa de aprendizado de máquina apropriada

Para prever a tarifa de táxi, selecione primeiro a tarefa de aprendizado de máquina apropriada. Você está tentando prever um valor real (um duplo que representa o preço) com base nos outros fatores do conjunto de dados. Você escolhe uma tarefa de [**regressão**](../resources/glossary.md#regression).

## <a name="create-a-console-application"></a>Criar um aplicativo de console

1. Abra o Visual Studio 2017. Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus. Na caixa de diálogo **Novo Projeto**, selecione o nó **Visual C#** seguido pelo nó **.NET Core**. Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)**. Na caixa de texto **Nome**, digite "TaxiFarePrediction" e selecione o botão **OK**.

2. Crie um diretório chamado *Dados* no seu projeto para salvar seus arquivos do conjunto de dados:

    No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Nova Pasta**. Digite "Dados" e pressione Enter.

3. Instalar o **Pacote NuGet Microsoft.ML**:

    No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Gerenciar Pacotes NuGet**. Escolha "nuget.org" como a origem do Pacote, selecione a guia **Procurar**, pesquise **Microsoft.ML**, selecione o pacote na lista e escolha o botão **Instalar**. Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.

## <a name="prepare-and-understand-the-data"></a>Preparar e compreender os dados

1. Baixe os conjuntos de dados [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) e [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) e salve-os na pasta *Dados* criada na etapa anterior. Esses conjuntos de dados são usados para treinar o modelo de aprendizado de máquina e, em seguida, avaliar a precisão dele. Esses conjuntos de dados são originalmente do [Conjunto de dados NYC TLC Taxi Trip](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).

2. No **Gerenciador de Soluções**, clique com o botão direito do mouse em cada um dos arquivos \*.csv e selecione **Propriedades**. Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Sempre**.

3. Abra o conjunto de dados **taxi-fare-train.csv** e observe os cabeçalhos de coluna na primeira linha. Dê uma olhada em cada uma das colunas. Compreenda os dados e decida quais colunas são **recursos** e qual é o **rótulo**.

O **rótulo** é o identificador da coluna que você quer prever. Os **recursos** identificados são usados ​​para prever o rótulo.

O conjunto de dados fornecido contém as seguintes colunas:

* **vendor_id:** o ID do taxista é um recurso.
* **rate_code:** o tipo de tarifa da viagem de táxi é um recurso.
* **passenger_count:** o número de passageiros na viagem é um recurso.
* **trip_time_in_secs:** a quantidade de tempo que a viagem levou. Você deseja prever a tarifa da viagem antes de sua conclusão. No momento, você não sabe a duração da viagem. Portanto, o tempo da viagem não é um recurso e você excluirá essa coluna do modelo.
* **trip_distance:** a distância da viagem é um recurso.
* **payment_type:** o método de pagamento (dinheiro ou cartão de crédito) é um recurso.
* **fare_amount:** a tarifa total de táxi paga é o rótulo.

## <a name="create-data-classes"></a>Criar classes de dados

Crie classes para os dados de entrada e as previsões:

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.
1. Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *TaxiTrip.cs*. Em seguida, selecione o botão **Adicionar**.
1. Inclua as seguintes instruções `using` no novo arquivo:

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

Remova a definição de classe existente e adicione o seguinte código, que tem duas classes `TaxiTrip` e `TaxiTripFarePrediction`, ao arquivo *TaxiTrip.cs*:

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip` é a classe de dados de entrada e tem definições para cada uma das colunas do conjunto de dados. Use o atributo [Coluna](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) para especificar os índices das colunas de origem no conjunto de dados.

A classe `TaxiTripFarePrediction` é usada para representar os resultados previstos. Ele tem um único campo de float (`FareAmount`) com um atributo `Score`[ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) aplicado. **Score** é a coluna especial no ML.NET. O modelo produz valores previstos nessa coluna.

## <a name="define-data-and-model-paths"></a>Definir dados e caminhos de modelo

Volte para o arquivo *Program.cs* e crie três constantes globais para manter os caminhos nos arquivos com conjuntos de dados e salvar o modelo:

* `_datapath` tem o demarcador para o conjunto de dados usado para treinar o modelo.
* `_testdatapath` tem o demarcador para o conjunto de dados usado para avaliar o modelo.
* `_modelpath` tem o demarcador em que o modelo treinado é armazenado.

Adicione o seguinte código à linha logo acima do método `Main` para especificar estes caminhos:

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

## <a name="create-a-learning-pipeline"></a>Criar um pipeline de aprendizado

Adicione as seguintes instruções `using` adicionais ao início do arquivo *Program.cs*:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

Em `Main`, substitua o `Console.WriteLine("Hello World!")` pelo seguinte código:

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

O método `Train` treina o modelo. Crie esse método logo abaixo de `Main`, usando o seguinte código:

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

O pipeline de aprendizado carrega todos os dados e algoritmos necessários para treinar o modelo. Adicione o seguinte código ao método `Train`:

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-data"></a>Carregar e transformar dados

A primeira etapa executada pelo pipeline de aprendizado é carregar os dados do conjunto de dados de treinamento. Neste caso, o conjunto de dados de treinamento é armazenado no arquivo de texto com um caminho definido pela constante `_datapath`. Esse arquivo contém o cabeçalho com os nomes de coluna, então, a primeira linha deve ser ignorada enquanto os dados são carregados. As colunas no arquivo são separadas por uma vírgula (","). Adicione o seguinte código ao método `Train`:

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(useHeader: true, separator: ','));
```

Nas próximas etapas, trataremos das colunas pelos nomes definidos na classe `TaxiTrip`.

Quando o modelo é treinado e avaliado, os valores na coluna **Label** são considerados os valores corretos a serem previstos. Como queremos prever a tarifa da viagem de táxi, copie a coluna `FareAmount` para a coluna **Label**. Para fazer isso, use <xref:Microsoft.ML.Transforms.ColumnCopier> e adicione o seguinte código:

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

O algoritmo que treina o modelo requer recursos **numéricos**, então é necessário transformar os valores de dados categóricos (`VendorId`, `RateCode` e `PaymentType`) em números. Para fazer isso, use <xref:Microsoft.ML.Transforms.CategoricalOneHotVectorizer>, que atribui valores numéricos de chave diferentes aos valores diferentes em cada uma das colunas, e adicione o seguinte código:

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

A última etapa na preparação de dados combina todas as colunas de recursos na coluna **Features** usando a classe de transformação <xref:Microsoft.ML.Transforms.ColumnConcatenator>. Essa etapa é necessária, pois o aprendiz processa apenas os recursos da coluna **Features**. Adicione o seguinte código:

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

Observe que a coluna `TripTime`, que corresponde à coluna `trip_time_in_secs` no arquivo do conjunto de dados, não foi incluída. Você já determinou que ela não é um recurso de previsão útil.

> [!NOTE]
> Essas etapas devem ser adicionadas ao pipeline na ordem especificada acima para uma execução bem-sucedida.

## <a name="choose-a-learning-algorithm"></a>Escolher um algoritmo de aprendizado

Após adicionar os dados ao pipeline e transformá-los no formato de entrada correto, selecione um algoritmo de aprendizado (**aluno**). O aprendiz treina o modelo. Você escolheu uma **tarefa de regressão** para esse problema, então, adicione um aprendiz <xref:Microsoft.ML.Trainers.FastTreeRegressor>, que é um dos aprendizes de regressão fornecidos pelo ML.NET.

O aprendiz <xref:Microsoft.ML.Trainers.FastTreeRegressor> utiliza o aumento do gradiente. O aumento de gradiente é uma técnica de aprendizado de máquina para problemas de regressão. Ele cria cada árvore de regressão por etapas. Ele usa uma função de perda predefinida para medir o erro em cada etapa e corrigi-lo no próximo. O resultado é um modelo de previsão que é, na verdade, um conjunto de modelos de previsão mais fracos. Para obter mais informações sobre o aumento de gradiente, consulte [Regressão da árvore de decisão aumentada](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).

Adicione o seguinte código ao método `Train` após o código de processamento de dados adicionado na etapa anterior:

```csharp
pipeline.Add(new FastTreeRegressor());
```

Você adicionou todas as etapas anteriores ao pipeline como instruções individuais, mas o C# tem uma sintaxe de inicialização de coleta útil que simplifica a criação e a inicialização do pipeline. Substitua o código que você adicionou até o método `Train` com o seguinte código:

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a>Treinar o modelo

A etapa final é treinar o modelo. Até este ponto, nada no pipeline foi executado. O método `pipeline.Train<TInput, TOutput>` produz o modelo que aceita uma instância do tipo `TInput` e produz uma instância do tipo `TOutput`. Adicione o seguinte código ao método `Train`:

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

E pronto. Você treinou com sucesso um modelo de aprendizado de máquina que pode prever tarifas de táxi em Nova York. Agora, vamos entender o nível de precisão do modelo e saber como usá-lo para prever os valores das tarifas de táxi.

### <a name="save-the-model"></a>Salvar o modelo

Antes de seguir para a próxima etapa, salve o modelo em um arquivo .zip adicionando o seguinte código no final do método `Train`:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

Adicionar a instrução `await` à chamada `model.WriteAsync` significa que o método `Train` deve ser alterado para um método assíncrono que retorne uma tarefa. Modifique a assinatura de `Train`, conforme mostrado no código a seguir:

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

Alterar o tipo de retorno do método `Train` significa que você precisa adicionar um `await` ao código que chama `Train` no método `Main`, conforme mostrado no código a seguir:

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

Usar um `await` no método `Main` significa que o método `Main` deve ter o modificador `async` e retornar um `Task`:

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

Também é preciso adicionar a seguinte instrução `using` à parte superior do arquivo:

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

Como o método `async Main` é um novo recurso adicionado no C# 7.1 e a versão da linguagem padrão do projeto é C# 7.0, é necessário alterar a versão da linguagem para C# 7.1 ou superior. Para fazer isso, clique com o botão direito do mouse no nó do projeto no **Gerenciador de Soluções** e selecione **Propriedades**. Selecione a guia **Build** e o botão **Avançado**. No menu suspenso, selecione **C# 7.1** (ou uma versão posterior). Selecione o botão **OK**.

## <a name="evaluate-the-model"></a>Avaliar o modelo

Avaliação é o processo de verificar o quão bem modelo prevê os valores de rótulo. É importante que o modelo faça boas previsões com base em dados que não foram usados para treiná-lo. Uma forma de fazer isso é dividir os dados em conjuntos de dados de treinamento e teste, como neste tutorial. Agora que você treinou o modelo nos dados de treinamento, pode ver o desempenho dos dados de teste.

Volte para o método `Main` e adicione o seguinte código abaixo da chamada para o método `Train`:

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

O método `Evaluate` avalia o modelo. Para criá-lo, adicione o código a seguir abaixo do método `Train`:

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

Adicione o código a seguir ao método `Evaluate` para configurar o carregamento dos dados de teste:

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

Adicione o seguinte código para avaliar o modelo e produzir as métricas de avaliação:

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) é uma das métricas de avaliação do modelo de regressão. Quanto menor, melhor o modelo. Adicione o seguinte código ao método `Evaluate` para exibir o valor RMS:

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

[RSquared](../resources/glossary.md#coefficient-of-determination) é outra métrica de avaliação dos modelos de regressão. RSquared aceita valores entre 0 e 1. Quanto mais perto de 1 estiver o valor, melhor o modelo será. Adicione o seguinte código ao método `Evaluate` para exibir o valor RSquared:

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a>Usar o modelo para previsões

Em seguida, crie uma classe para hospedar os cenários de teste que você pode usar para garantir que o modelo esteja funcionando corretamente:

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.
1. No **Adicionar Novo Item** caixa de diálogo, selecione **classe** e altere o **nome** campo *TestTrips.cs*. Em seguida, selecione o botão **Adicionar**.
1. Modifique a classe para ser estática, como no exemplo a seguir:

   [!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

Este tutorial usa uma viagem de teste dentro dessa classe. Posteriormente, você pode adicionar outros cenários para fazer experiências com o modelo. Adicione o seguinte código à classe `TestTrips`:

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

A tarifa real da viagem é 29,5. Use 0 como espaço reservado, pois o modelo preverá a tarifa.

Para prever a tarifa da viagem específica, volte para o arquivo *Program.cs* e adicione o código a seguir ao método `Main`:

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

Execute o programa para ver a tarifa de táxi prevista para o seu caso de teste.

Parabéns! Agora você criou com sucesso um modelo de aprendizado de máquina para prever tarifas de táxi, avaliou sua precisão e o usou para fazer previsões. Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction).

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

Confira nosso repositório GitHub para continuar aprendendo e encontrar mais amostras.
> [!div class="nextstepaction"]
> [dotnet/machinelearning GitHub repository](https://github.com/dotnet/machinelearning/)
