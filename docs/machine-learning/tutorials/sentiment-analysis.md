---
title: Usar o ML.NET em um cenário de classificação binária de análise de sentimento
description: Descubra como usar o ML.NET em um cenário de classificação binária para entender como usar a previsão de sentimentos para executar a ação apropriada.
ms.date: 06/04/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 898b4664120b6eeb0ef18aac3acdc94b0ca0bacd
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314832"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a>Tutorial: Usar o ML.NET em um cenário de classificação binária de análise de sentimento

> [!NOTE]
> Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações. Para obter mais informações, visite [a introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Este tutorial de exemplo ilustra o uso do ML.NET para criar um classificador de sentimento por meio de um aplicativo de console do .NET Core usando C# no Visual Studio 2017.

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
> * Compreender o problema
> * Selecionar a tarefa de aprendizado de máquina apropriada
> * Preparar seus dados
> * Criar o pipeline de aprendizado
> * Carregar um classificador
> * Treinar o modelo
> * Avaliar o modelo com um conjunto de dados diferente
> * Prever os resultados dos dados de teste com o modelo

## <a name="sentiment-analysis-sample-overview"></a>Visão geral da amostra de análise de sentimento

A amostra é um aplicativo de console que usa o ML.NET para treinar um modelo que classifica e prevê o sentimento como positivo ou negativo. Ele também avalia o modelo com um segundo conjunto de dados para análise de qualidade. Os conjuntos de dados de sentimento são do projeto WikiDetox.

## <a name="prerequisites"></a>Pré-requisitos

* [Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.

* [Arquivo separado de guia de dados de linha detox da Wikipédia (wikiPedia-detox-250-line-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).
* [Arquivo separado de guia de teste de linha detox da Wikipédia (wikipedia-detox-250-line-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).

## <a name="machine-learning-workflow"></a>Fluxo de trabalho de aprendizado de máquina

Este tutorial segue um fluxo de trabalho de aprendizado de máquina que permite que o processo se mova de maneira ordenada.

As fases do fluxo de trabalho são as seguintes:

1. **Compreender o problema**
2. **Ingerir dados**
3. **Pré-processamento de dados e engenharia de recursos**
4. **Treinar e prever o modelo**
5. **Avaliar o modelo**
6. **Operacionalização do modelo**

### <a name="understand-the-problem"></a>Compreender o problema

Você primeiro precisa compreender o problema, para que possa dividi-lo em partes que possam oferecer suporte à criação e ao treinamento do modelo. Divida o problema para prever e avaliar os resultados.

O problema deste tutorial é compreender o sentimento de comentário do site recebido para executar a ação apropriada.

Você pode dividir o problema com o texto de sentimento e o valor de sentimento para os dados com os quais deseja treinar o modelo e com um valor de sentimento previsto que você pode avaliar e usar operacionalmente.

Em seguida, você precisa **determinar** o sentimento, o que ajuda na seleção da tarefa de aprendizado de máquina.

## <a name="select-the-appropriate-machine-learning-task"></a>Selecionar a tarefa de aprendizado de máquina apropriada

Com este problema, você está a par dos seguintes fatos:

Dados de treinamento: os comentários do site podem ser positivos ou negativos (**sentimento**).
Preveja o **sentimento** de um novo comentário no site, seja positivo ou negativo, como nos exemplos a seguir:

* Evite inserir qualquer conteúdo sem sentido na Wikipédia.
* Ele é o melhor, e o artigo deve dizer isso.

A tarefa de aprendizado da máquina de classificação é mais adequada para esse cenário.

### <a name="about-the-classification-task"></a>Sobre a tarefa de classificação

A classificação é uma tarefa de aprendizado de máquina que usa dados para **determinar** a categoria, o tipo ou a classe de um item ou linha de dados. Por exemplo, você pode usar a classificação para:

* Identificar o sentimento como positivo ou negativo.
* Classificar email como spam, lixo eletrônico ou bom.
* Determinar se a amostra de laboratório de um paciente é cancerígena.
* Categorizar os clientes pela sua propensão a responder a uma campanha de vendas.

Tarefas de classificação são frequentemente de um dos seguintes tipos:

* Binário: A ou B.
* Multiclasse: várias categorias que podem ser previstas usando um único modelo.

## <a name="create-a-console-application"></a>Criar um aplicativo de console

1. Abra o Visual Studio 2017. Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus. Na caixa de diálogo *Novo projeto**, selecione o nó **Visual C#** seguido pelo nó **.NET Core**. Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)**. Na caixa de texto **Nome**, digite "SentimentAnalysis" e, em seguida, selecione o botão **OK** .

2. Crie um diretório chamado *Data* no seu projeto para salvar seus arquivos do conjunto de dados:

    No **Gerenciador de Soluções**, clique com o botão direito do mouse no seu projeto e selecione **Adicionar** > **Nova Pasta**. Digite "Dados" e pressione Enter.

3. Instalar o **Pacote NuGet Microsoft.ML**:

    No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**. Escolha "nuget.org" como a Origem do pacote, selecione a guia Procurar, pesquise por **Microsoft.ML**, selecione o pacote na lista e escolha o botão **Instalar**. Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.

### <a name="prepare-your-data"></a>Preparar seus dados

1. Baixe os conjuntos de dados [WikiPedia detox-250-line-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) e [wikipedia-detox-250-line-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) e salve-os na pasta *Dados* criada anteriormente. O primeiro conjunto de dados treina o modelo de aprendizado de máquina e o segundo pode ser usado para avaliar a precisão do seu modelo.

2. No Gerenciador de Soluções, clique com o botão direito do mouse em cada um dos arquivos \*.tsv e selecione **Propriedades**. Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Sempre**.

### <a name="create-classes-and-define-paths"></a>Criar classes e definir demarcadores

Adicione as seguintes instruções `using` adicionais ao início do arquivo *Program.cs*:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#1 "Add necessary usings")]

Você precisa criar três variáveis ​​globais para manter o demarcador para os arquivos baixados recentemente:

* `_dataPath` tem o demarcador para o conjunto de dados usado para treinar o modelo.
* `_testDataPath` tem o demarcador para o conjunto de dados usado para avaliar o modelo.
* `_modelPath` tem o demarcador em que o modelo treinado é salvo.

Adicione o seguinte código à linha logo acima do método `Main` para especificar os arquivos baixados recentemente:

[!code-csharp[Declare file variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#2 "Declare variables to store data files")]

Você precisa criar algumas classes para os dados e previsões de entrada. Adicione uma nova classe ao seu projeto:

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.

1. Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentData.cs*. Em seguida, selecione o botão **Adicionar**.

    O arquivo *SentimentData.cs* é aberto no editor de códigos. Adicione a seguinte instrução `using` acima de *SentimentData.cs*:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#1 "Add necessary usings")]

Remova a definição de classe existente e adicione o seguinte código, que possui duas classes `SentimentData` e `SentimentPrediction`, ao arquivo *SentimentData.cs*:

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#2 "Declare data record types")]

`SentimentData` é a classe do conjunto de dados de entrada e tem um `float` (`Sentiment`) que tem um valor para sentimento positivo ou negativo e uma cadeia de caracteres para o comentário (`SentimentText`). Ambos os campos têm atributos `Column` anexados a eles. Este atributo descreve a ordem de cada campo no arquivo de dados e é o campo `Label`. `SentimentPrediction` é a classe usada para previsão depois que o modelo foi treinado. Tem um único booliano (`Sentiment`) e um atributo `PredictedLabel` `ColumnName`. O `Label` é usado para criar e treinar o modelo e também é usado com um segundo conjunto de dados para avaliar o modelo. O `PredictedLabel` é usado durante a previsão e avaliação. Para avaliação, uma entrada com dados de treinamento, os valores previstos e o modelo são usados.

No arquivo *Program.cs*, altere a assinatura do método `Main` substituindo `void` por `async Task`, como no exemplo a seguir:

```csharp
static async Task Main(string[] args) 
{

}
```

Você adiciona `async` a `Main` com um tipo de retorno <xref:System.Threading.Tasks.Task> porque está salvando o modelo em um arquivo zip posteriormente, e o programa precisa aguardar até que a tarefa externa seja concluída.

> [!NOTE]
> Um método *async main* permite que você use `await` no método `Main`. Para obter mais informações, consulte o tópico [​​async main](../../../docs/csharp/programming-guide/main-and-command-args/index.md) no guia de programação em C#.

Substitua a linha `Console.WriteLine("Hello World!")` pelo seguinte código no método `Main`:

[!code-csharp[Train](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#3 "Train your model")]

O método `Train` executa as seguintes tarefas:

* Carrega ou consome os dados.
* Pré-processa e personaliza os dados.
* Treina o modelo.
* Prevê o sentimento com base nos dados de teste.

Crie o método `Train`, logo após o método `Main`, usando o seguinte código:

```csharp
public static async Task<PredictionModel<SentimentData, SentimentPrediction>> Train()
{

}
```

## <a name="ingest-the-data"></a>Ingerir dados

Inicialize uma nova instância de <xref:Microsoft.ML.LearningPipeline> que incluirá o carregamento de dados, o processamento/personalização de dados e o modelo. Adicione o seguinte código como a primeira linha do método `Train`:

[!code-csharp[LearningPipeline](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#5 "Create a learning pipeline")]

O objeto <xref:Microsoft.ML.Data.TextLoader> é a primeira parte do pipeline e carrega os dados do arquivo de treinamento.

[!code-csharp[TextLoader](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#6 "Add a text loader to the pipeline")]

## <a name="data-preprocess-and-feature-engineering"></a>Pré-processamento de dados e engenharia de recursos

O pré-processamento e a limpeza de dados são tarefas importantes que ocorrem antes de um conjunto de dados ser usado efetivamente para o aprendizado de máquina. Os dados brutos costumam ser ruidosos e pouco confiáveis, e podem apresentar valores faltantes. Usar dados sem essas tarefas de modelagem pode produzir resultados enganosos. Os pipelines de transformação do ML.NET permitem que você componha um conjunto personalizado de transformações que são aplicadas aos seus dados antes do treinamento ou teste. A principal finalidade das transformações é a personalização de dados. A vantagem de um pipeline de transformação é que, após a definição de pipeline de transformação, salve o pipeline para aplicá-lo aos dados de teste.

Aplique um <xref:Microsoft.ML.Transforms.TextFeaturizer> para converter a coluna `SentimentText` em um [vetor numérico](../resources/glossary.md#numerical-feature-vector) chamado `Features`, usado pelo algoritmo de aprendizado de máquina. Esta é a etapa de pré-processamento/personalização. Usar componentes adicionais disponíveis no ML.NET pode permitir melhores resultados com o seu modelo. Adicione `TextFeaturizer` ao pipeline como a próxima linha de código:

[!code-csharp[TextFeaturizer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#7 "Add a TextFeaturizer to the pipeline")]

## <a name="choose-a-learning-algorithm"></a>Escolher um algoritmo de aprendizado

O objeto <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier> é um aprendiz de árvore de decisão que você usará neste pipeline. Semelhante à etapa de personalização, experimentar diferentes aprendizes disponíveis no ML.NET e alterar seus parâmetros leva a resultados diferentes. Para ajuste, você pode definir [hiperparâmetros](../resources/glossary.md#hyperparameter) como <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumTrees>, <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumLeaves>e <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.MinDocumentsInLeafs>. Esses hiperparâmetros são definidos antes que qualquer coisa afete o modelo e são específicos do modelo. Eles são usados ​​para ajustar a árvore de decisão quanto ao desempenho, para que valores maiores possam afetar negativamente o desempenho.

Adicione o seguinte código ao método `Train`:

[!code-csharp[BinaryClassifier](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#8 "Add a fast binary tree classifier")]

## <a name="train-the-model"></a>Treinar o modelo

Você treina o modelo, <xref:Microsoft.ML.PredictionModel%602>, com base no conjunto de dados que foi carregado e transformado. `pipeline.Train<SentimentData, SentimentPrediction>()` treina o pipeline (carrega os dados, treina o personalizador e o aprendiz). O experimento não será executado até que isso ocorra.

Adicione o seguinte código ao método `Train`:

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#9 "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a>Salvar e retornar o modelo treinado para usar na avaliação

Neste ponto, você tem um modelo que pode ser integrado em qualquer um dos seus aplicativos .NET existentes ou novos. Para salvar seu modelo em um arquivo .zip antes de retornar, adicione o seguinte código à linha seguinte em `Train`:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#10 "Save the model")]

Retorne o modelo no final do método `Train`.

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#11 "Return the model")]

## <a name="evaluate-the-model"></a>Avaliar o modelo

Agora que você criou e treinou o modelo, precisa avaliá-lo com um conjunto de dados diferente para garantia de qualidade e validação. No método `Evaluate`, o modelo criado em `Train` é passado para ser avaliado. Crie o método `Evaluate` , logo após `Train`, como no código a seguir:

```csharp
public static void Evaluate(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

O método `Evaluate` executa as seguintes tarefas:

* Carrega o conjunto de dados de teste.
* Cria o avaliador binário.
* Avalia o modelo e cria métricas.
* Exibe as métricas.

Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `Train`, usando o seguinte código:

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#12 "Call the Evaluate method")]

A classe <xref:Microsoft.ML.Data.TextLoader> carrega o novo conjunto de dados de teste com o mesmo esquema. Você pode avaliar o modelo usando esse conjunto de dados como uma verificação de qualidade. Adicione o seguinte código ao método `Evaluate`:

[!code-csharp[LoadText](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#13 "Load the test dataset")]

O objeto <xref:Microsoft.ML.Models.BinaryClassificationEvaluator> calcula as métricas de qualidade para o `PredictionModel` usando o conjunto de dados especificado. Para ver essas métricas, adicione o avaliador como a próxima linha no método `Evaluate`, com o seguinte código:

[!code-csharp[BinaryEvaluator](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#14 "Create the binary evaluator")]

O <xref:Microsoft.ML.Models.BinaryClassificationMetrics> contém as métricas gerais calculadas pelos avaliadores de classificação binária. Para exibi-los a fim de determinar a qualidade do modelo, é preciso primeiro obter as métricas. Adicione o seguinte código:

[!code-csharp[CreateMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#15 "Evaluate the model and create metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a>Exibir as métricas para validação de modelo

Use o código a seguir para exibir as métricas, compartilhar os resultados e, em seguida, agir com relação a eles:

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#16 "Display selected metrics")]

## <a name="predict-the-test-data-outcomes-with-the-model"></a>Prever os resultados dos dados de teste com o modelo

Crie o método `Predict`, logo após o método `Evaluate`, usando o seguinte código:

```csharp
public static void Predict(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

O método `Predict` executa as seguintes tarefas:

* Cria dados de teste.
* Prevê o sentimento com base nos dados de teste.
* Combina dados de teste e previsões para relatórios.
* Exibe os resultados previstos.

Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `Evaluate`, usando o seguinte código:

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#17 "Call the Predict method")]

Adicione alguns comentários para testar as previsões do modelo treinado no método `Predict`:

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#18 "Create test data for predictions")]

Agora que você tem um modelo, pode usá-lo para prever o sentimento positivo ou negativo dos dados do comentário usando o método <xref:Microsoft.ML.PredictionModel.Predict%2A?displayProperty=nameWithType>. Para obter uma previsão, use `Predict` em novos dados. Observe que os dados de entrada são uma cadeia de caracteres e o modelo inclui a personalização. Seu pipeline está em sincronia durante o treinamento e a previsão. Você não precisou escrever código de pré-processamento/personalização especificamente para previsões, e a mesma API cuida das previsões de lote e de uso único.

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#19 "Create predictions of sentiments")]

### <a name="model-operationalization-prediction"></a>Operacionalização do modelo: previsão

Exiba `SentimentText` e a previsão de sentimento correspondente para compartilhar os resultados e agir de acordo com eles. Isso é chamado de operacionalização, usar os dados retornados como parte das políticas operacionais. Crie um cabeçalho para os resultados usando o seguinte código <xref:System.Console.WriteLine?displayProperty=nameWithType>:

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#20 "Display prediction outputs")]

Antes de exibir os resultados previstos, combine o sentimento e a previsão juntos para ver o comentário original com o sentimento previsto. O código a seguir usa o método <xref:System.Linq.Enumerable.Zip%2A> para que isso aconteça, então adicione o seguinte código:

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#21 "Build the pairs of sentiment data and predictions")]

Agora que você combinou `SentimentText` e `Sentiment` em uma classe, você pode exibir os resultados usando o método <xref:System.Console.WriteLine?displayProperty=nameWithType>:

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#22 "Display the predictions")]

Como nomes de elementos de tuplas inferidos são um novo recurso no C# 7.1 e a versão da linguagem padrão do projeto é C# 7.0, é necessário alterar a versão da linguagem para C# 7.1 ou superior.
Para fazer isso, clique com o botão direito do mouse no nó do projeto no **Gerenciador de Soluções** e selecione **Propriedades**. Selecione a guia **Build** e o botão **Avançado**. No menu suspenso, selecione **C# 7.1** (ou uma versão posterior). Selecione o botão **OK**.

## <a name="results"></a>Resultados

Seus resultados devem ser semelhantes aos seguintes. Conforme o pipeline processa, exibe mensagens. Você pode ver avisos ou mensagens de processamento. Eles foram removidos dos seguintes resultados para maior clareza.

```

PredictionModel quality metrics evaluation
------------------------------------------
Accuracy: 66.67%
Auc: 94.44%
F1Score: 75.00%

Sentiment Predictions
---------------------
Sentiment: Please refrain from adding nonsense to Wikipedia. | Prediction: Negative
Sentiment: He is the best, and the article should say that. | Prediction: Positive

```

Parabéns! Agora você criou com sucesso um modelo de aprendizado de máquina para classificar e prever o sentimento das mensagens. Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis).

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como:
> [!div class="checklist"]
> * Compreender o problema
> * Selecionar a tarefa de aprendizado de máquina apropriada
> * Preparar seus dados
> * Criar o pipeline de aprendizado
> * Carregar um classificador
> * Treinar o modelo
> * Avaliar o modelo com um conjunto de dados diferente
> * Prever os resultados dos dados de teste com o modelo

Avançar para o próximo tutorial para saber mais
> [!div class="nextstepaction"]
> [Previsão do valor da corrida do táxi](taxi-fare.md)
