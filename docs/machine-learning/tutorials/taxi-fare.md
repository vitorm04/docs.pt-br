---
title: Usar o ML.NET para prever tarifas de táxi em Nova York (regressão)
description: Saiba como usar o ML.NET em um cenário de regressão.
author: aditidugar
ms.author: johalex
ms.date: 06/05/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 048ed1d38408c1ba4901c554cae33d5552c9e303
ms.sourcegitcommit: 5b0802832fb9ad684d34e69b8644a16a5b7c4810
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34860631"
---
# <a name="tutorial-use-mlnet-to-predict-new-york-taxi-fares-regression"></a>Tutorial: Usar o ML.NET para prever tarifas de táxi em Nova York (regressão)

> [!NOTE]
> Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações. Para obter mais informações, visite [a introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Este tutorial ilustra como usar o ML.NET para criar um [modelo de regressão](../resources/glossary.md#regression) para prever tarifas de táxi em Nova York.

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
> * Compreender o problema
> * Selecionar a tarefa de aprendizado de máquina apropriada
> * Preparar e compreender seus dados
> * Criar um pipeline de aprendizado
> * Carregar e transformar seus dados
> * Escolher um algoritmo de aprendizado
> * Treinar o modelo
> * Avaliar o modelo
> * Usar o modelo para previsões

## <a name="prerequisites"></a>Pré-requisitos

* [Visual Studio 2017 15.6 ou posterior](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.

## <a name="understand-the-problem"></a>Compreender o problema

Esse problema está centrado na **previsão da tarifa de uma viagem de táxi na cidade de Nova York**. À primeira vista, pode parecer que depende simplesmente da distância percorrida. No entanto, os taxistas em Nova York cobram valores variados por outros fatores, como passageiros adicionais ou pagamento por cartão de crédito em vez de dinheiro.

## <a name="select-the-appropriate-machine-learning-task"></a>Selecionar a tarefa de aprendizado de máquina apropriada

Para prever a tarifa de táxi, selecione primeiro a tarefa de aprendizado de máquina apropriada. Você está tentando prever um valor real (um duplo que representa o preço) com base nos outros fatores do conjunto de dados. Você escolhe uma tarefa de [**regressão**](../resources/glossary.md#regression).

O processo de treinamento do modelo identifica quais fatores no conjunto de dados são mais influentes ao prever o preço final da tarifa.

## <a name="create-a-console-application"></a>Criar um aplicativo de console

1. Abra o Visual Studio 2017. Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus. Na caixa de diálogo **Novo Projeto**, selecione o nó **Visual C#** seguido pelo nó **.NET Core**. Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)**. Na caixa de texto **Nome**, digite "TaxiFarePrediction" e selecione o botão **OK**.

2. Crie um diretório chamado *Data* no seu projeto para salvar seus arquivos do conjunto de dados:

    No **Gerenciador de Soluções**, clique com o botão direito do mouse no seu projeto e selecione **Adicionar** > **Nova Pasta**. Digite "Dados" e pressione Enter.

3. Instalar o **Pacote NuGet Microsoft.ML**:

    No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**. Escolha "nuget.org" como a Origem do pacote, selecione a guia Procurar, pesquise por **Microsoft.ML**, selecione o pacote na lista e escolha o botão **Instalar**. Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.

### <a name="prepare-and-understand-your-data"></a>Preparar e compreender seus dados

1. Baixe os conjuntos de dados [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) e [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) e salve-os na pasta *Dados* criada anteriormente. O conjunto de dados Taxi Trip treina o modelo de aprendizado de máquina e pode ser usado para avaliar a precisão do seu modelo. Esses conjuntos de dados são originalmente do [Conjunto de dados NYC TLC Taxi Trip](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).

2. No Gerenciador de Soluções, clique com o botão direito do mouse em cada um dos arquivos \*.csv e selecione **Propriedades**. Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Sempre**.

3. Abra o conjunto de dados **taxi-fare-train.csv** no editor de código e observe os cabeçalhos de coluna na primeira linha. Dê uma olhada em cada uma das colunas. Compreenda os dados e decida quais colunas são **recursos** e qual é o **rótulo**.

O **rótulo** é o identificador da coluna que você está tentando prever. Os **recursos** identificados são usados ​​para prever o rótulo.

* **vendor_id:** o ID do taxista é um recurso.
* **rate_code:** o tipo de tarifa da viagem de táxi é um recurso.
* **passenger_count:** o número de passageiros na viagem é um recurso.
* **trip_time_in_secs:** a quantidade de tempo que a viagem levou. Você não saberá quanto tempo a viagem demora até que seja concluída. Você pode excluir esta coluna do modelo.
* **trip_distance:** a distância da viagem é um recurso.
* **payment_type:** o método de pagamento (dinheiro ou cartão de crédito) é um recurso.
* **fare_amount:** a tarifa total de táxi paga é o rótulo.

### <a name="create-classes-and-define-paths"></a>Criar classes e definir demarcadores

Adicione as seguintes instruções `using` adicionais ao início do arquivo *Program.cs*:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

Você precisa criar três variáveis ​​globais para manter os demarcadores dos arquivos baixados recentemente e salvar o modelo:

* `_datapath` tem o demarcador para o conjunto de dados usado para treinar o modelo.
* `_testdatapath` tem o demarcador para o conjunto de dados usado para avaliar o modelo.
* `_modelpath` tem o demarcador em que o modelo treinado é armazenado.

Adicione o seguinte código à linha logo acima de `Main` para especificar os arquivos baixados recentemente:

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

Em seguida, crie classes para os dados de entrada e as previsões:

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.
1. Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *TaxiTrip.cs*. Em seguida, selecione o botão **Adicionar**.
1. Inclua as seguintes instruções `using` no novo arquivo:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

Remova a definição de classe existente e adicione o seguinte código, que tem duas classes `TaxiTrip` e `TaxiTripFarePrediction`, ao arquivo *TaxiTrip.cs*:

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip` é a classe do conjunto de dados de entrada e possui definições para cada uma das colunas do conjunto de dados. `TaxiTripFarePrediction` é a classe usada para previsão depois que o modelo foi treinado. Ele tem um único float (`FareAmount`) e um atributo `Score`[ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) aplicado.

Agora, volte para o arquivo **Program.cs**. Em `Main`, substitua o `Console.WriteLine("Hello World!")` pelo seguinte código:

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

O método `Train` treina seu modelo. Crie essa função logo abaixo de `Main`, usando o seguinte código:

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

## <a name="create-a-learning-pipeline"></a>Criar um pipeline de aprendizado

O pipeline de aprendizado carrega todos os dados e algoritmos necessários para treinar o modelo. Adicione o seguinte código ao método `Train()`:

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-your-data"></a>Carregar e transformar seus dados

Em seguida, carregue seus dados no pipeline. Aponte para o `_datapath` criado inicialmente e especifique o delimitador do arquivo .csv (,). Adicione o seguinte código ao método `Train()` abaixo da última etapa:

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(separator:','));
```

Você se referirá às colunas sem os sublinhados no código que está criando. Copie a coluna `FareAmount` para uma nova coluna chamada "Rótulo" usando a função `ColumnCopier()`. Esta coluna é o **Rótulo**.

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

Conduza alguma **engenharia de recursos** para transformar os dados de modo que possam ser usados ​​efetivamente para o aprendizado de máquina. O algoritmo que treina o modelo requer recursos **numéricos** , você transforma os dados categóricos (`VendorId`, `RateCode` e `PaymentType`) em números. A função `CategoricalOneHotVectorizer()` atribui uma chave numérica aos valores em cada uma dessas colunas. Transforme seus dados adicionando este código:

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

O último passo na preparação de dados combina todos os seus **recursos** em um vetor usando a função `ColumnConcatenator()`. Essa etapa necessária ajuda o algoritmo a processar facilmente seus recursos. Adicione o seguinte código:

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

Observe que a coluna `trip_time_in_secs` não está incluída. Você já determinou que ela não é um recurso de previsão útil.

> [!NOTE]
> Essas etapas devem ser adicionadas ao Pipeline na ordem especificada acima para uma execução bem-sucedida.

## <a name="choose-a-learning-algorithm"></a>Escolher um algoritmo de aprendizado

Após adicionar os dados ao pipeline e transformá-los no formato de entrada correto, selecione um algoritmo de aprendizado (**aluno**). O algoritmo de aprendizado treina o modelo. Você escolheu uma **tarefa de regressão** para esse problema, então você adiciona um aprendiz chamado `FastTreeRegressor()` ao pipeline que utiliza o **aumento de gradiente**.

O aumento de gradiente é uma técnica de aprendizado de máquina para problemas de regressão. Ele cria cada árvore de regressão por etapas. Ele usa uma função de perda predefinida para medir o erro em cada etapa e corrigi-lo no próximo. O resultado é um modelo de previsão que é, na verdade, um conjunto de modelos de previsão mais fracos. Para obter mais informações sobre o aumento de gradiente, consulte [Regressão da árvore de decisão aumentada](https://docs.microsoft.com/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).

Adicione o seguinte código ao método `Train()` após o código de processamento de dados adicionado na última etapa:

```csharp
pipeline.Add(new FastTreeRegressor());
```

Você adicionou todas as etapas anteriores ao pipeline como instruções individuais, mas o C# tem uma sintaxe de inicialização de coleta útil que simplifica a criação e a inicialização do pipeline. Substitua o código que você adicionou até o método `Train()` com o seguinte código:

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a>Treinar o modelo

A etapa final é treinar o modelo. Até este ponto, nada no pipeline foi executado. A função `pipeline.Train<T_Input, T_Output>()` aceita o tipo de classe `TaxiTrip` predefinido e gera um tipo `TaxiTripFarePrediction`. Adicione este trecho final de código na função `Train()`:

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

E pronto. Você treinou com sucesso um modelo de aprendizado de máquina que pode prever tarifas de táxi em Nova York. Agora, dê uma olhada para entender a precisão do seu modelo e aprenda a consumi-lo.

## <a name="save-the-model"></a>Salvar o modelo

Antes de seguir para a próxima etapa, salve seu modelo em um arquivo .zip adicionando o seguinte código no final da sua função `Train()`:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

Adicionar a instrução `await` à chamada `model.WriteAsync()` significa que o método `Train()` deve ser alterado para um método assíncrono que retorne um `Task`. Modifique a assinatura de `Train`, conforme mostrado no código a seguir:

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

Alterar o tipo de retorno do método `Train` significa que você precisa adicionar um `await` ao código que chama `Train` no método `Main`, conforme mostrado no código a seguir:

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

Adicionar um `await` ao seu método `Main` significa que o método `Main` deve ter o modificador `async` e retornar um `Task`:

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

Também é preciso adicionar o seguinte usando a instrução na parte superior do arquivo:

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

Como o método `async Main` é um novo recurso do C# 7.1 e a versão da linguagem padrão do projeto é C# 7.0, é necessário alterar a versão da linguagem para C# 7.1 ou superior.
Para fazer isso, clique com o botão direito do mouse no nó do projeto no **Gerenciador de Soluções** e selecione **Propriedades**. Selecione a guia **Build** e o botão **Avançado**. No menu suspenso, selecione **C# 7.1** (ou uma versão posterior). Selecione o botão **OK**.

## <a name="evaluate-the-model"></a>Avaliar o modelo

Avaliação é o processo de verificar como o modelo funciona. É importante que seu modelo faça boas previsões com base em dados que não foram usados ​​quando ele foi treinado. Uma forma de fazer isso é dividir os dados em conjuntos de dados de treinamento e teste, como você fez neste tutorial. Agora que você treinou o modelo nos dados de treinamento, pode ver o desempenho dos dados de teste.

Volte para a sua função `Main` e adicione o seguinte código abaixo da chamada para o método `Train()`:

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

A função `Evaluate()` avalia seu modelo. Crie essa função abaixo de `Train()`. Adicione o seguinte código:

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

Carregue os dados de teste usando a função `TextLoader()`. Adicione o seguinte código ao método `Evaluate()`:

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

Adicione o seguinte código para avaliar o modelo e produzir as métricas para ele:

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

O RMS é uma métrica para avaliar os problemas de regressão. Quanto menor, melhor o seu modelo. Adicione o seguinte código na função `Evaluate()` para imprimir o RMS do seu modelo.

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

O RSquared é uma métrica para avaliar os problemas de regressão. O RSquared será um valor entre 0 e 1. Quanto mais próximo de 1, melhor será seu modelo. Adicione o seguinte código na função `Evaluate()` para imprimir o valor de RSquared para o seu modelo.

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a>Usar o modelo para previsões

Em seguida, crie uma classe para hospedar os cenários de teste que você pode usar para garantir que seu modelo esteja funcionando corretamente:

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.
1. No **Adicionar Novo Item** caixa de diálogo, selecione **classe** e altere o **nome** campo *TestTrips.cs*. Em seguida, selecione o botão **Adicionar**.
1. Modifique a classe para ser estática, como no exemplo a seguir:

[!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

Este tutorial usa uma viagem de teste dentro dessa classe. Posteriormente, você pode adicionar outros cenários para fazer experiências com essa amostra. Adicione o seguinte código à classe `TestTrips`:

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

A tarifa real dessa viagem é 29,5, mas use 0 como espaço reservado. O algoritmo de aprendizado de máquina irá prever a tarifa.

Adicione o seguinte código na sua função `Main`. Ele testa seu modelo usando os dados `TestTrip`:

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

Execute o programa para ver a tarifa de táxi prevista para o seu caso de teste.

Parabéns! Agora você criou com sucesso um modelo de aprendizado de máquina para prever tarifas de táxi, avaliou sua precisão e testou-o. Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction).

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como:
> [!div class="checklist"]
> * Compreender o problema
> * Selecionar a tarefa de aprendizado de máquina apropriada
> * Preparar e compreender seus dados
> * Criar um pipeline de aprendizado
> * Carregar e transformar seus dados
> * Escolher um algoritmo de aprendizado
> * Treinar o modelo
> * Avaliar o modelo
> * Usar o modelo para previsões

Confira nosso repositório GitHub para continuar aprendendo e encontrar mais amostras.
> [!div class="nextstepaction"]
> [dotnet/machinelearning GitHub repository](https://github.com/dotnet/machinelearning/)
