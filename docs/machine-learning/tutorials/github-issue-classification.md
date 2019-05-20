---
title: Classificar problemas do GitHub – classificação multiclasse
description: Descubra como usar o ML.NET em um cenário de classificação multiclasse para classificar os problemas do GitHub a fim de atribuí-los a uma determinada área.
ms.date: 05/02/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: a4122d0cdfe6531275fabf94743882a82f2a13c1
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063529"
---
# <a name="tutorial-use-mlnet-in-a-multiclass-classification-scenario-to-classify-github-issues"></a>Tutorial: Usar o ML.NET em um cenário de classificação multiclasse para classificar os problemas do GitHub

Este tutorial de exemplo ilustra o uso do ML.NET para criar uma classificação de problema do GitHub para treinar um modelo que classifica e prevê o rótulo de área de um problema do GitHub por meio de um aplicativo de console do .NET Core usando C# no Visual Studio.

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
> * Preparar seus dados
> * Transformar os dados
> * Treinar o modelo
> * Avaliar o modelo
> * Prever com o modelo treinado
> * Implantar e prever com um modelo carregado

Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification).

## <a name="prerequisites"></a>Pré-requisitos

* [Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.

* O [arquivo de problemas do Github separados por tabulação (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).
* O [arquivo de testes de problemas do Github separados por tabulação (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).

## <a name="create-a-console-application"></a>Criar um aplicativo de console

### <a name="create-a-project"></a>Criar um projeto

1. Abra o Visual Studio 2017. Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus. Na caixa de diálogo **Novo Projeto**, selecione o nó **Visual C#** seguido pelo nó **.NET Core**. Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)**. Na caixa de texto **Nome**, digite "GitHubIssueClassification" e selecione o botão **OK**.

2. Crie um diretório chamado *Data* no seu projeto para salvar seus arquivos do conjunto de dados:

    No **Gerenciador de Soluções**, clique com o botão direito do mouse no seu projeto e selecione **Adicionar** > **Nova Pasta**. Digite "Data" e pressione Enter.

3. Crie um diretório chamado *Modelos* em seu projeto para salvar seu modelo:

    No **Gerenciador de Soluções**, clique com o botão direito do mouse no seu projeto e selecione **Adicionar** > **Nova Pasta**. Digite "Modelos" e pressione ENTER.

4. Instalar o **Pacote NuGet Microsoft.ML**:

    No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**. Escolha "nuget.org" como a origem do pacote, selecione a guia Procurar, pesquise **Microsoft.ML**, selecione o pacote **v 1.0.0** na lista e selecione o botão **Instalar**. Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.

### <a name="prepare-your-data"></a>Preparar seus dados

1. Baixe os conjuntos de dados [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) e [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) e salve-os na pasta *Dados* criada anteriormente. O primeiro conjunto de dados treina o modelo de aprendizado de máquina e o segundo pode ser usado para avaliar a precisão do seu modelo.

2. No Gerenciador de Soluções, clique com o botão direito do mouse em cada um dos arquivos \*.tsv e selecione **Propriedades**. Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.

### <a name="create-classes-and-define-paths"></a>Criar classes e definir demarcadores

Adicione as seguintes instruções `using` adicionais ao início do arquivo *Program.cs*:

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

Crie três campos globais para manter os caminhos para os arquivos baixados recentemente e variáveis globais para `MLContext`, `DataView` e `PredictionEngine`:

* `_trainDataPath` tem o demarcador para o conjunto de dados usado para treinar o modelo.
* `_testDataPath` tem o demarcador para o conjunto de dados usado para avaliar o modelo.
* `_modelPath` tem o demarcador em que o modelo treinado é salvo.
* `_mlContext` é o <xref:Microsoft.ML.MLContext> que fornece o contexto de processamento.
* `_trainingDataView` é o <xref:Microsoft.ML.IDataView> usado para processar o conjunto de dados de treinamento.
* `_predEngine` é o <xref:Microsoft.ML.PredictionEngine%602> usado para previsões individuais.

Adicione o seguinte código à linha logo acima do método `Main` para especificar estes caminhos e as outras variáveis:

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

Crie algumas classes para os dados de entrada e as previsões. Adicione uma nova classe ao seu projeto:

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.

1. Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *GitHubIssueData.cs*. Em seguida, selecione o botão **Adicionar**.

    O arquivo *GitHubIssueData.cs* é aberto no editor de códigos. Adicione a seguinte instrução `using` acima de *GitHubIssueData.cs*:

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

Remova a definição de classe existente e adicione o seguinte código, que tem duas classes, `GitHubIssue` e `IssuePrediction`, ao arquivo *GitHubIssueData.cs*:

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

O `label` é a coluna que você deseja prever. O `Features` identificado são as entradas que você atribui ao modelo para prever o rótulo.

Use o atributo [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) para especificar os índices das colunas de origem no conjunto de dados.

`GitHubIssue` é a classe de conjunto de dados de entrada e tem os seguintes campos <xref:System.String>:

* a primeira coluna `ID` (ID de problema do GitHub)
* a segunda coluna `Area` (a previsão do treinamento)
* a terceira coluna `Title` (título do problema de GitHub) é o primeiro `feature` usado para prever o `Area`
* a quarta coluna `Description` é o segundo `feature` usado para prever o `Area`

`IssuePrediction` é a classe usada para previsão depois que o modelo foi treinado. Tem um único `string` (`Area`) e um atributo `PredictedLabel` `ColumnName`.  O `PredictedLabel` é usado durante a previsão e avaliação. Para avaliação, uma entrada com dados de treinamento, os valores previstos e o modelo são usados.

Todas as operações do ML.NET iniciam na classe [MLContext](xref:Microsoft.ML.MLContext). Inicializar `mlContext` cria um novo ambiente do ML.NET que pode ser compartilhado entre os objetos do fluxo de trabalho de criação de modelo. É similar, conceitualmente, a `DBContext` em `Entity Framework`.

### <a name="initialize-variables-in-main"></a>Inicializar variáveis em Main

Inicialize a variável global `_mlContext` com uma nova instância de `MLContext` com uma semente aleatória (`seed: 0`) para obter resultados repetíveis/determinísticos entre vários treinamentos.  Substitua a linha `Console.WriteLine("Hello World!")` pelo seguinte código no método `Main`:

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a>Carregar os dados

O ML.NET usa a [classe IDataView](xref:Microsoft.ML.IDataView) como uma maneira flexível e eficiente de descrever dados tabulares de texto ou numéricos. O `IDataView` pode carregar arquivos de texto ou em tempo real (por exemplo, banco de dados SQL ou arquivos de log).

Para inicializar e carregar a variável global `_trainingDataView` para utilizá-la para o pipeline, adicione o seguinte código após a inicialização de `mlContext`:

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]

O [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) define o esquema de dados e lê o arquivo. Ele usa as variáveis de caminho de dados e retorna uma `IDataView`.

Adicione o seguinte como a linha seguinte de código no método `Main`:

[!code-csharp[CallProcessData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

O método `ProcessData` executa as seguintes tarefas:

* Extrai e transforma os dados.
* Retorna o pipeline de processamento.

Crie o método `ProcessData`, logo após o método `Main`, usando o seguinte código:

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a>Extrair recursos e transformar os dados

Uma vez que você deseja prever o rótulo do GitHub de Área de um `GitHubIssue`, use o método [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) para transformar a coluna `Area` em um tipo de chave numérica `Label` (um formato aceito pelos algoritmos de classificação da coluna) e adicione-o como uma nova coluna de conjunto de dados:

[!code-csharp[MapValueToKey](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

Em seguida, chame `mlContext.Transforms.Text.FeaturizeText` que transforma as colunas do texto (`Title` e `Description`) em um vetor numérico para cada `TitleFeaturized` e `DescriptionFeaturized` chamado. Acrescente a personalização para ambas as colunas ao pipeline com o código a seguir:

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

A última etapa na preparação de dados combina todas as colunas de recursos na coluna **Recursos** usando o método [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A). Por padrão, um algoritmo de aprendizado processa apenas os recursos da coluna **Features**. Acrescente esta transformação ao pipeline com o código a seguir:

[!code-csharp[Concatenate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 Em seguida, acrescente um <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> para armazenar a DataView em cache, para melhorar o desempenho ao iterar nos dados várias vezes usando o cache, como no código a seguir:

[!code-csharp[AppendCache](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

> [!WARNING]
> Use AppendCacheCheckpoint para conjuntos de dados pequenos/médios a fim de reduzir o tempo de treinamento. NÃO o utilize (remova .AppendCacheCheckpoint()) ao lidar com conjuntos de dados grandes.

Retorne o pipeline no final do método `ProcessData`.

[!code-csharp[ReturnPipeline](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

Esta etapa manipula o pré-processamento/personalização. Usar componentes adicionais disponíveis no ML.NET pode permitir melhores resultados com o seu modelo.

## <a name="build-and-train-the-model"></a>Criar e treinar o modelo

Adicione a seguinte chamada ao método `BuildAndTrainModel` como a próxima linha de código no método `Main`:

[!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

O método `BuildAndTrainModel` executa as seguintes tarefas:

* Cria a classe de algoritmo de treinamento.
* Treina o modelo.
* Prevê a área com base em dados de treinamento.
* Retorna o modelo.

Crie o método `BuildAndTrainModel`, logo após o método `Main`, usando o seguinte código:

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a>Sobre a tarefa de classificação

A classificação é uma tarefa de aprendizado de máquina que usa dados para **determinar** a categoria, o tipo ou a classe de um item ou linha de dados e costuma ser de um dos seguintes tipos:

* Binário: A ou B.
* Multiclasse: várias categorias que podem ser previstas usando um único modelo.

Para esse tipo de problema, use um algoritmo de aprendizado de classificação Multiclasse, pois a previsão de categoria do problema pode ser uma das várias categorias (multiclasse), em vez de apenas duas (binária).

Acrescente o algoritmo de aprendizado de máquina às definições de transformação de dados adicionando o seguinte como a primeira linha de código em `BuildAndTrainModel()`:

[!code-csharp[AddTrainer](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

O [SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) é seu algoritmo de treinamento de classificação multiclasse. Isso é anexado ao `pipeline` e aceita os `Title` e `Description` (`Features`) personalizados e os parâmetro de entrada `Label` para aprender com os dados históricos.

### <a name="train-the-model"></a>Treinar o modelo

Ajuste o modelo aos dados `splitTrainSet` e retorne o modelo treinado adicionando o seguinte como a próxima linha de código no método `BuildAndTrainModel()`:

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

O método `Fit()` treina o modelo transformando o conjunto de dados e aplicando o treinamento.

O [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) é uma API de conveniência, que permite passar uma única instância de dados e, em seguida, executar uma previsão nessa única instância de dados. Adicione isso como a próxima linha no método `BuildAndTrainModel()`:

[!code-csharp[CreatePredictionEngine1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a>Prever com o modelo treinado

Adicione um problema do GitHub para testar a previsão do modelo treinado no método `Predict` ao criar uma instância de `GitHubIssue`:

[!code-csharp[CreateTestIssue1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

Use a função [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) faz uma previsão em uma única coluna de dados:

[!code-csharp[Predict](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a>Usando o modelo: resultados de previsão

Exiba `GitHubIssue` e a previsão de rótulo `Area` correspondente para compartilhar os resultados e agir de acordo com eles.  Crie uma exibição para os resultados usando o seguinte código <xref:System.Console.WriteLine?displayProperty=nameWithType>:

[!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Retornar o modelo treinado a ser usado para avaliação

Retorne o modelo no final do método `BuildAndTrainModel`.

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a>Avaliar o modelo

Agora que você criou e treinou o modelo, precisa avaliá-lo com um conjunto de dados diferente para garantia de qualidade e validação. No método `Evaluate`, o modelo criado em `BuildAndTrainModel` é passado para ser avaliado. Crie o método `Evaluate` , logo após `BuildAndTrainModel`, como no código a seguir:

```csharp
public static void Evaluate()
{

}
```

O método `Evaluate` executa as seguintes tarefas:

* Carrega o conjunto de dados de teste.
* Cria o avaliador multiclasse.
* Avalia o modelo e cria métricas.
* Exibe as métricas.

Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `BuildAndTrainModel`, usando o seguinte código:

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

Como você fez anteriormente com o conjunto de dados de treinamento, carregue o conjunto de dados de teste adicionando o seguinte código ao método `Evaluate`:

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

O método [Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) calcula as métricas de qualidade para o modelo usando o conjunto de dados especificado. Ele retorna um objeto <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> que contém as métricas gerais calculadas pelos avaliadores de classificação multiclasse.
Para exibir as métricas para determinar a qualidade do modelo, você precisará obtê-las primeiro.
Observe o uso do método [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) da variável global `_trainedModel` de aprendizado de máquina (um [Transformador](xref:Microsoft.ML.ITransformer)) para inserir os recursos e retornar previsões. Adicione o seguinte código ao método `Evaluate` como a linha seguinte:

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

As métricas a seguir são avaliadas para classificação multiclasse:

* Microprecisão – todo par de classe/exemplo contribui igualmente para a métrica de precisão.  Convém que a Microprecisão seja tão próxima de 1 quanto possível.

* Macroprecisão – toda classe contribui igualmente para a métrica de precisão. Classes minoritárias recebem o mesmo peso que as classes maiores. Convém que a Macroprecisão seja tão próxima de 1 quanto possível.

* Perda de log – consulte [Perda de log](../resources/glossary.md#log-loss). Convém que a Perda de log seja tão próxima de zero quanto possível.

* Redução de perda de log – varia de [-inf, 100], em que 100 é composto pelas previsões perfeitas e 0 indica previsões de média. Convém que a redução de perda de log seja tão próxima de zero quanto possível.

### <a name="displaying-the-metrics-for-model-validation"></a>Exibir as métricas para validação de modelo

Use o código a seguir para exibir as métricas, compartilhar os resultados e, em seguida, agir com relação a eles:

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

## <a name="deploy-and-predict-with-a-model"></a>Implantar e prever com um modelo

Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `Evaluate`, usando o seguinte código:

[!code-csharp[CallPredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

Crie o método `PredictIssue` logo após o método `Evaluate` (e antes do método `SaveModelAsFile`) usando o seguinte código:

```csharp
private static void PredictIssue()
{

}
```

O método `PredictIssue` executa as seguintes tarefas:

* Cria um único problema dos dados de teste.
* Prevê a área com base em dados de teste.
* Combina dados de teste e previsões para relatórios.
* Exibe os resultados previstos.

Adicione um problema do GitHub para testar a previsão do modelo treinado no método `Predict` ao criar uma instância de `GitHubIssue`:

[!code-csharp[AddTestIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

Como você fez anteriormente, crie uma instância de `PredictionEngine` com o código a seguir:

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]
  
Use o `PredictionEngine` para prever o rótulo do GitHub de Área adicionando o seguinte código ao método `PredictIssue` para a previsão:

[!code-csharp[PredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a>Usando o modelo carregado para previsão

Exiba `Area` para categorizar o problema e agir adequadamente para solucioná-lo. Crie uma exibição para os resultados usando o seguinte código <xref:System.Console.WriteLine?displayProperty=nameWithType>:

[!code-csharp[DisplayResults](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a>Resultados

Seus resultados devem ser semelhantes aos seguintes. Conforme o pipeline processa, exibe mensagens. Você pode ver avisos ou mensagens de processamento. Essas mensagens foram removidas dos resultados a seguir para ficar mais claro.

```console
=============== Single Prediction just-trained-model - Result: area-System.Net ===============
*************************************************************************************************************
*       Metrics for Multi-class Classification model - Test Data
*------------------------------------------------------------------------------------------------------------
*       MicroAccuracy:    0.738
*       MacroAccuracy:    0.668
*       LogLoss:          .919
*       LogLossReduction: .643
*************************************************************************************************************
=============== Single Prediction - Result: area-System.Data ===============
```

Parabéns! Agora você criou com sucesso um modelo de machine learning para classificar e prever um rótulo de Área para um problema do GitHub. Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification).

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como:
> [!div class="checklist"]
> * Preparar seus dados
> * Transformar os dados
> * Treinar o modelo
> * Avaliar o modelo
> * Prever com o modelo treinado
> * Implantar e prever com um modelo carregado

Avançar para o próximo tutorial para saber mais
> [!div class="nextstepaction"]
> [Previsão do valor da corrida do táxi](taxi-fare.md)
