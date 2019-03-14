---
title: Usar o ML.NET em um cenário de classificação binária de análise de sentimento
description: Descubra como usar o ML.NET em um cenário de classificação binária para entender como usar a previsão de sentimentos para executar a ação apropriada.
ms.date: 03/07/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: d7e46b489506f4adad843ba5315afde4c7689b4e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723316"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a>Tutorial: Usar o ML.NET em um cenário de classificação binária de análise de sentimento

Este tutorial de exemplo ilustra o uso do ML.NET para criar um classificador de sentimento para prever um sentimento positivo ou negativo por meio de um aplicativo de console do .NET Core usando C# no Visual Studio 2017. No mundo do aprendizado de máquina, esse tipo de previsão é conhecido como classificação binária.

> [!NOTE]
> Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações. Para obter mais informações, visite [a introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Este tutorial e uma amostra relacionada estão usando o **ML.NET versão 0.11** no momento. Saiba mais nas notas de versão no [repositório do GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
> * Compreender o problema
> * Selecionar o algoritmo de aprendizado de máquina apropriado
> * Preparar seus dados
> * Transformar os dados
> * Treinar o modelo
> * Avaliar o modelo
> * Prever com o modelo treinado
> * Implantar e prever com um modelo carregado

## <a name="sentiment-analysis-sample-overview"></a>Visão geral da amostra de análise de sentimento

A amostra é um aplicativo de console que usa o ML.NET para treinar um modelo que classifica e prevê o sentimento como positivo ou negativo. O conjunto de dados de sentimentos do Yelp é da Universidade da Califórnia, Irvine (UCI), e é dividido em um conjunto de dados de treinamento e um conjunto de dados de teste. A amostra avalia o modelo com um conjunto de dados de teste para análise da qualidade. 

Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis).

## <a name="prerequisites"></a>Pré-requisitos

* [Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.

* [O arquivo zip do conjunto de dados de Sentenças de sentimentos rotuladas da UCI](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)

## <a name="machine-learning-workflow"></a>Fluxo de trabalho de aprendizado de máquina

Este tutorial segue um fluxo de trabalho de aprendizado de máquina que permite que o processo se mova de maneira ordenada.

As fases do fluxo de trabalho são as seguintes:

1. **Compreender o problema**
2. **Preparar seus dados**
   * **Carregar os dados**
   * **Extrair recursos (Transformar seus dados)**
3. **Compilar e treinar** 
   * **Treinar o modelo**
   * **Avaliar o modelo**
4. **Implantar Modelo**
   * **Usar o modelo para prever**

### <a name="understand-the-problem"></a>Compreender o problema

Você primeiro precisa compreender o problema, para que possa dividi-lo em partes que possam oferecer suporte à criação e ao treinamento do modelo. Dividir o problema permite prever e avaliar os resultados.

O problema deste tutorial é compreender o sentimento de comentário do site recebido para executar a ação apropriada.

Você pode dividir o problema com o texto de sentimento e o valor de sentimento para os dados com os quais deseja treinar o modelo e com um valor de sentimento previsto que você pode avaliar e usar operacionalmente.

Em seguida, você precisa **determinar** o sentimento, o que ajuda na seleção da tarefa de aprendizado de máquina.

## <a name="select-the-appropriate-machine-learning-algorithm"></a>Selecionar o algoritmo de aprendizado de máquina apropriado

Com este problema, você está a par dos seguintes fatos:

Dados de treinamento: os comentários do site podem ser positivos (1) ou negativos (0) (**sentimento**).

Preveja o **sentimento** de um novo comentário no site, seja positivo ou negativo, como nos exemplos a seguir:

* Adoro os garçons daqui. Eles são ótimos.
* Este lugar tem a pior sopa.

O algoritmo de aprendizado de máquina de classificação é mais adequado para esse cenário.

### <a name="about-the-classification-algorithm"></a>Sobre o algoritmo de classificação

A classificação é um algoritmo de aprendizado de máquina que usa os dados para **determinar** a categoria, o tipo ou a classe de um item ou de uma linha de dados. Por exemplo, você pode usar a classificação para:

* Identificar o sentimento como positivo ou negativo.
* Classificar email como spam, lixo eletrônico ou bom.
* Determinar se a amostra de laboratório de um paciente é cancerígena.
* Categorizar os clientes pela sua propensão a responder a uma campanha de vendas.

Algoritmos de classificação são frequentemente de um dos seguintes tipos:

* Binário: A ou B.
* Multiclasse: várias categorias que podem ser previstas usando um único modelo.

Visto que os comentários do site precisam ser classificados como positivos ou negativos, você pode usar o algoritmo de Classificação binária. 

## <a name="create-a-console-application"></a>Criar um aplicativo de console

1. Abra o Visual Studio 2017. Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus. Na caixa de diálogo **Novo Projeto**, selecione o nó **Visual C#** seguido pelo nó **.NET Core**. Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)**. Na caixa de texto **Nome**, digite "SentimentAnalysis" e, em seguida, selecione o botão **OK** .

2. Crie um diretório chamado *Data* no seu projeto para salvar seus arquivos do conjunto de dados:

    No **Gerenciador de Soluções**, clique com o botão direito do mouse no seu projeto e selecione **Adicionar** > **Nova Pasta**. Digite "Dados" e pressione Enter.

3. Instalar o **Pacote NuGet Microsoft.ML**:

    No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**. Escolha "nuget.org" como a Origem do pacote, selecione a guia Procurar, pesquise por **Microsoft.ML**, selecione o pacote na lista e escolha o botão **Instalar**. Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.

### <a name="prepare-your-data"></a>Preparar seus dados

1. Baixe o [arquivo zip do conjunto de dados de Sentenças de sentimentos rotuladas da UCI (consulte as citações na nota a seguir) ](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) e descompacte-o.

2. Copie o arquivo `yelp_labelled.txt` para o diretório *Dados* que você criou.

> [!NOTE]
> Os conjuntos de dados que este tutorial usa são de “From Group to Individual Labels using Deep Features”, Kotzias et. al,. KDD 2015, e hospedados no UCI Machine Learning Repository – Dua, D. e Karra Taniskidou, E. (2017). UCI Machine Learning Repository [http://archive.ics.uci.edu/ml]. Irvine, CA: University of California, School of Information and Computer Science.

3. No Gerenciador de Soluções, clique com o botão direito do mouse no arquivo `yelp_labeled.txt` e selecione **Propriedades**. Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.

### <a name="create-classes-and-define-paths"></a>Criar classes e definir demarcadores

Adicione as seguintes instruções `using` adicionais ao início do arquivo *Program.cs*:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

Você precisa criar dois campos globais para armazenar o caminho do arquivo de conjunto de dados baixado recentemente e o caminho do arquivo de modelo salvo:

* `_dataPath` tem o demarcador para o conjunto de dados usado para treinar o modelo.
* `_modelPath` tem o demarcador em que o modelo treinado é salvo.

Adicione o seguinte código à linha logo acima do método `Main` para especificar estes caminhos:

[!code-csharp[Declare global variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

Você precisa criar algumas classes para os dados e previsões de entrada. Adicione uma nova classe ao seu projeto:

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.

1. Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentData.cs*. Em seguida, selecione o botão **Adicionar**.

    O arquivo *SentimentData.cs* é aberto no editor de códigos. Adicione a seguinte instrução `using` acima de *SentimentData.cs*:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

Remova a definição de classe existente e adicione o seguinte código, que possui duas classes `SentimentData` e `SentimentPrediction`, ao arquivo *SentimentData.cs*:

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

A classe do conjunto de dados de entrada, `SentimentData`, tem um `string` para o comentário (`SentimentText`) e um `bool` (`Sentiment`) que tem um valor para sentimento positivo ou negativo. Ambos os campos têm atributos <xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29> anexados a eles. Este atributo descreve a ordem de cada campo no arquivo de dados.  Além disso, a propriedade `Sentiment` tem um <xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A> para designá-la como o campo `Label`. `SentimentPrediction` é a classe usada para previsão depois que o modelo foi treinado. Tem um único booliano (`Sentiment`) e um atributo `PredictedLabel` `ColumnName`. O `Label` é usado para criar e treinar o modelo, além de ser usado com o conjunto de dados de teste para avaliar o modelo. O `PredictedLabel` é usado durante a previsão e avaliação. Para avaliação, uma entrada com dados de treinamento, os valores previstos e o modelo são usados.

Ao criar um modelo com o ML.NET, comece criando um <xref:Microsoft.ML.MLContext>. `MLContext` é conceitualmente comparável ao uso de `DbContext` no Entity Framework. O ambiente fornece um contexto para seu trabalho de ML que pode ser usado no acompanhamento e registro em log da exceção.

### <a name="initialize-variables-in-main"></a>Inicializar variáveis em Main

Crie uma variável chamada `mlContext` e inicialize-a com uma nova instância de `MLContext`.  Substitua a linha `Console.WriteLine("Hello World!")` pelo seguinte código no método `Main`:

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

Adicione o seguinte como a linha seguinte de código no método `Main`:

[!code-csharp[CallLoadData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

O método `LoadData` executa as seguintes tarefas:

* Carrega os dados.
* Divide o conjunto de dados carregado em conjuntos de treinamento e teste.
* Retorna os conjuntos de treinamento e teste.

Crie o método `LoadData`, logo após o método `Main`, usando o seguinte código:

```csharp
public static (IDataView trainSet, IDataView testSet) LoadData(MLContext mlContext)
{

}
```
## <a name="load-the-data"></a>Carregar os dados

Já que o tipo do modelo de dados `SentimentData` criado anteriormente corresponde ao esquema de conjunto de dados, você pode combinar a inicialização, o mapeamento e o carregamento de conjunto de dados em uma única linha de código, usando o wrapper `MLContext.Data.ReadFromTextFile` para <xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29>. Ele retorna um <xref:Microsoft.Data.DataView.IDataView>. 

 Como a entrada e saída de `Transforms`, um `DataView` é o tipo de pipeline de dados fundamental, comparável ao `IEnumerable` para `LINQ`.

No ML.NET, os dados são semelhantes a um modo de exibição SQL. Eles são heterogêneos e avaliados e esquematizados lentamente. O objeto é a primeira parte do pipeline e carrega os dados. Neste tutorial, ele carrega um conjunto de dados com comentários e o sentimento tóxico ou não tóxico correspondente. Isso é usado para criar o modelo e treiná-lo.

 Adicione o seguinte código como a primeira linha do método `LoadData`:

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

### <a name="split-the-dataset-for-model-training-and-testing"></a>Dividir o conjunto de dados para o modelo de treinamento e de teste

Em seguida, você precisa de um conjunto de dados de treinamento para treinar o modelo e um conjunto de dados de teste para avaliar o modelo. Use o `MLContext.BinaryClassification.TrainTestSplit` que encapsula <xref:Microsoft.ML.StaticPipe.TrainingStaticExtensions.TrainTestSplit%2A> para dividir o conjunto de dados carregado em conjuntos de dados de treinamento e de teste e retorná-los dentro de um <xref:Microsoft.ML.TrainCatalogBase.TrainTestData>. Você pode especificar a fração de dados para o conjunto de teste com o parâmetro `testFraction`. O padrão é 10%, mas use 20% nesse caso, a fim de usar mais dados para a avaliação.  

Para dividir os dados carregados nos conjuntos de dados necessários, adicione o seguinte código como a próxima linha no método `LoadData`:

[!code-csharp[SplitData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

Retorne o `splitDataView` no final do método `LoadData`:

[!code-csharp[ReturnSplitData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a>Criar e treinar o modelo

Adicione a seguinte chamada ao método `BuildAndTrainModel` como a próxima linha de código no método `Main`:

[!code-csharp[CallBuildAndTrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

O método `BuildAndTrainModel` executa as seguintes tarefas:

* Extrai e transforma os dados.
* Treina o modelo.
* Prevê o sentimento com base nos dados de teste.
* Retorna o modelo.

Crie o método `Train`, logo após o método `Main`, usando o seguinte código:

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
{

}
```

Observe que dois parâmetros são passados para o método Train. Um `MLContext` para o contexto (`mlContext`) e um `IDataView` para o conjunto de dados de treinamento (`splitTrainSet`). 

## <a name="extract-and-transform-the-data"></a>Extrair e transformar os dados

O pré-processamento e a limpeza de dados são tarefas importantes que ocorrem antes de um conjunto de dados ser usado efetivamente para o aprendizado de máquina. Os dados brutos costumam ser ruidosos e pouco confiáveis, e podem apresentar valores faltantes. Usar dados sem essas tarefas de modelagem pode produzir resultados enganosos.

Os pipelines de transformação do ML.NET compõem um conjunto personalizado de transformações que são aplicadas aos seus dados antes do treinamento ou teste. A principal finalidade das transformações é a [personalização](../resources/glossary.md#feature-engineering) de dados. Os algoritmos de aprendizado de máquina entendem os [dados personalizados](../resources/glossary.md#feature), portanto, a próximo etapa é transformar nossos dados textuais em um formato que nossos algoritmos de aprendizado de máquina reconheçam. Esse formato é um [vetor numérico](../resources/glossary.md#numerical-feature-vector).

Em seguida, chame `mlContext.Transforms.Text.FeaturizeText` que personaliza a coluna de texto (`SentimentText`) em um vetor numérico chamado `Features`, usado pelo algoritmo de aprendizado de máquina. Essa é uma chamada de wrapper que retorna um <xref:Microsoft.ML.Data.EstimatorChain%601> que será efetivamente um pipeline. Dê ao `pipeline` um nome de sua preferência e, em seguida, anexe o instrutor à `EstimatorChain`. Adicione isso como a linha seguinte de código:

[!code-csharp[FeaturizeText](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

>[!WARNING]
> O ML.NET versão 0.10 alterou a ordem dos parâmetros de transformação. Isso não apresentará um erro até que você execute o aplicativo e compile o modelo. Use os nomes de parâmetro para transformações, conforme ilustrado no snippet de código anterior.

Esta é a etapa de pré-processamento/personalização. Usar componentes adicionais disponíveis no ML.NET pode permitir melhores resultados com o seu modelo.

## <a name="choose-a-learning-algorithm"></a>Escolher um algoritmo de aprendizado

Para adicionar o instrutor, chame o método `mlContext.BinaryClassification.Trainers.FastTree` do wrapper que retorna um objeto <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer>. Esse é um aprendiz de árvore de decisão que você usará neste pipeline. O `FastTreeBinaryClassificationTrainer` é anexado ao `pipeline` e aceita o parâmetro `SentimentText` (`Features`) personalizado e o parâmetro `Label` de entrada para aprender com os dados históricos.

Adicione o seguinte código ao método `BuildAndTrainModel`:

[!code-csharp[FastTreeBinaryClassificationTrainer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a FastTreeBinaryClassificationTrainer")]

## <a name="train-the-model"></a>Treinar o modelo

Você treina o modelo, <xref:Microsoft.ML.Data.TransformerChain%601>, com base no conjunto de dados que foi carregado e transformado. Depois que o avaliador tiver sido definido, treine o modelo usando o método <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> e forneça os dados de treinamento já carregados. Isso retornará um modelo que será usado nas previsões. `pipeline.Fit()` treina o pipeline e retorna um `Transformer` com base no `DataView` passado. O teste não é executado até que o método `.Fit()` seja executado.

Adicione o seguinte código ao método `BuildAndTrainModel`:

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a>Salvar e retornar o modelo treinado para usar na avaliação

Neste ponto, você tem um modelo de tipo <xref:Microsoft.ML.Data.TransformerChain%601> que pode ser integrado em qualquer um dos seus aplicativos .NET existentes ou novos. Retorne o modelo no final do método `BuildAndTrainModel`.

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a>Avaliar o modelo

Agora que você criou e treinou o modelo, precisa avaliá-lo com um conjunto de dados diferente para garantia de qualidade e validação. No método `Evaluate`, o modelo criado em `BuildAndTrainModel` é passado para ser avaliado. Crie o método `Evaluate` , logo após `BuildAndTrainModel`, como no código a seguir:

```csharp
public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
{

}
```

O método `Evaluate` executa as seguintes tarefas:

* Carrega o conjunto de dados de teste.
* Cria o avaliador de classificação binária.
* Avalia o modelo e cria métricas.
* Exibe as métricas.

Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `Train`, usando o seguinte código:

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

Em seguida, você usará o parâmetro `model` de aprendizado de máquina (um transformador) e o parâmetro `splitTestSet` para inserir os recursos e retornar previsões. Adicione o seguinte código ao método `Evaluate` como a linha seguinte:

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

O método `mlContext.BinaryClassification.Evaluate` calcula as métricas de qualidade para o `PredictionModel` usando o conjunto de dados especificado. Ele retorna um objeto <xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics> que contém as métricas gerais calculadas pelos avaliadores de classificação binária. Para exibi-los a fim de determinar a qualidade do modelo, é preciso primeiro obter as métricas. Adicione o seguinte código ao método `Evaluate` como a linha seguinte:

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a>Exibir as métricas para validação de modelo

Use o código a seguir para exibir as métricas, compartilhar os resultados e, em seguida, agir com relação a eles:

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

Para salvar seu modelo como um arquivo .zip antes de retornar, adicione o seguinte código para chamar o método `SaveModelAsFile` como a linha seguinte em `Evaluate`:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallSaveModel "Save the model")]

## <a name="save-the-model-as-azip-file"></a>Salvar o modelo como um arquivo .zip

Crie o método `SaveModelAsFile`, logo após o método `Evaluate`, usando o seguinte código:

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

O método `SaveModelAsFile` executa as seguintes tarefas:

* Salva o modelo como um arquivo .zip.

Em seguida, crie um método para salvar o modelo para que ele possa ser reutilizado e consumido em outros aplicativos. O `ITransformer` tem um método <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> que usa o campo global `_modelPath` e um <xref:System.IO.Stream>. Para salvá-lo como um arquivo zip, você criará o `FileStream` imediatamente antes de chamar o método `SaveTo`. Adicione o seguinte código ao método `SaveModelAsFile` como a linha seguinte:

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SaveModel "Add the SaveTo Method")]

## <a name="deploy-and-predict-with-a-loaded-model"></a>Implantar e prever com um modelo carregado

Você também pode exibir onde o arquivo foi gravado ao gravar uma mensagem de console com o `_modelPath`, usando o seguinte código:

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="predict-the-test-data-outcome-with-the-saved-model"></a>Prever o resultado dos dados de teste com o modelo salvo

Crie o método `UseModelWithSingleItem`, logo após o método `Evaluate`, usando o seguinte código:

```csharp
private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
{

}
```

O método `UseModelWithSingleItem` executa as seguintes tarefas:

* Cria um único comentário dos dados de teste.
* Prevê o sentimento com base nos dados de teste.
* Combina dados de teste e previsões para relatórios.
* Exibe os resultados previstos.

Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `Evaluate`, usando o seguinte código:

[!code-csharp[CallUseModelWithSingleItem](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

Enquanto o `model` é um `transformer` que opera em muitas linhas de dados, um cenário de produção muito comum é a necessidade de previsões em exemplos individuais. O <xref:Microsoft.ML.PredictionEngine%602> é um wrapper que é retornado do método `CreatePredictionEngine`. Vamos adicionar o seguinte código para criar `PredictionEngine` como a primeira linha no método `Predict`:

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]
  
Adicione um comentário para testar as previsões do modelo treinado no método `Predict` ao criar uma instância de `SentimentData`:

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

 Você pode usar isso para prever o sentimento positivo ou negativo de uma única instância dos dados de comentário. Para obter uma previsão, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> nos dados. Observe que os dados de entrada são uma cadeia de caracteres e o modelo inclui a personalização. Seu pipeline está em sincronia durante o treinamento e a previsão. Você não precisou escrever código de pré-processamento/personalização especificamente para previsões, e a mesma API cuida das previsões de lote e de uso único.

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

### <a name="use-the-model-prediction"></a>Usar o modelo: previsão

Exiba `SentimentText` e a previsão de sentimento correspondente para compartilhar os resultados e agir de acordo com eles. Isso é chamado de operacionalização, usar os dados retornados como parte das políticas operacionais. Crie uma exibição para os resultados usando o seguinte código <xref:System.Console.WriteLine?displayProperty=nameWithType>:

[!code-csharp[OutputPrediction](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="deploy-and-predict-with-a-loaded-model"></a>Implantar e prever com um modelo carregado

Crie o método `UseLoadedModelWithBatchItems`, logo antes do método `SaveModelAsFile`, usando o seguinte código:

```csharp
public static void UseLoadedModelWithBatchItems(MLContext mlContext)
{

}
```

O método `UseLoadedModelWithBatchItems` executa as seguintes tarefas:

* Cria dados de teste em lote.
* Prevê o sentimento com base nos dados de teste.
* Combina dados de teste e previsões para relatórios.
* Exibe os resultados previstos.

Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `UseModelWithSingleItem`, usando o seguinte código:

[!code-csharp[CallPredictModelLoaded](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseLoadedModelWithBatchItems "Call the CallUseLoadedModelWithBatchItems method")]

Adicione alguns comentários para testar as previsões do modelo treinado no método `UseLoadedModelWithBatchItems`:

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

Carregar o modelo

[!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadModel "Load the model")]

Agora que você tem um modelo, pode usá-lo para prever o sentimento tóxico ou não tóxico dos dados do comentário usando o método <xref:Microsoft.ML.ITransformer.Transform%2A>. Para obter uma previsão, use `Predict` em novos dados. Observe que os dados de entrada são uma cadeia de caracteres e o modelo inclui a personalização. Seu pipeline está em sincronia durante o treinamento e a previsão. Você não precisou escrever código de pré-processamento/personalização especificamente para previsões, e a mesma API cuida das previsões de lote e de uso único. Adicione o código a seguir ao método `UseLoadedModelWithBatchItems` para as previsões:

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="use-the-loaded-model-for-prediction"></a>Usar o modelo carregado para previsão

Exiba `SentimentText` e a previsão de sentimento correspondente para compartilhar os resultados e agir de acordo com eles. Isso é chamado de operacionalização, usar os dados retornados como parte das políticas operacionais. Crie um cabeçalho para os resultados usando o seguinte código <xref:System.Console.WriteLine?displayProperty=nameWithType>:

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

Antes de exibir os resultados previstos, combine o sentimento e a previsão juntos para ver o comentário original com o sentimento previsto. O código a seguir usa o método <xref:System.Linq.Enumerable.Zip%2A> para que isso aconteça, então adicione o seguinte código:

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#BuildSentimentPredictionPairs "Build the pairs of sentiment data and predictions")]

Agora que você combinou `SentimentText` e `Sentiment` em uma classe, você pode exibir os resultados usando o método <xref:System.Console.WriteLine?displayProperty=nameWithType>:

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

Como nomes de elementos de tuplas inferidos são um novo recurso no C# 7.1 e a versão da linguagem padrão do projeto é C# 7.0, é necessário alterar a versão da linguagem para C# 7.1 ou superior.
Para fazer isso, clique com o botão direito do mouse no nó do projeto no **Gerenciador de Soluções** e selecione **Propriedades**. Selecione a guia **Build** e o botão **Avançado**. No menu suspenso, selecione **C# 7.1** (ou uma versão posterior). Selecione o botão **OK**.

## <a name="results"></a>Resultados

Seus resultados devem ser semelhantes aos seguintes. Conforme o pipeline processa, exibe mensagens. Você pode ver avisos ou mensagens de processamento. Eles foram removidos dos seguintes resultados para maior clareza.

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 79.14%
Auc: 86.27%
F1Score: 80.60%

=============== End of model evaluation ===============
The model is saved to C:\Tutorials\SentimentAnalysis\bin\Debug\netcoreapp2.1\Data\Model.zip

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This was a very bad steak | Prediction: Negative | Probability: 0.4641322
=============== End of Predictions ===============


=============== Prediction Test of loaded model with a multiple samples ===============

Sentiment: This was a horrible meal | Prediction: Negative | Probability: 0.1391833
Sentiment: I love this spaghetti. | Prediction: Positive | Probability: 0.9819039
=============== End of predictions ===============

=============== End of process ===============
Press any key to continue . . .

```

Parabéns! Agora você criou com sucesso um modelo de aprendizado de máquina para classificar e prever o sentimento das mensagens. 

A criação de modelos bem-sucedidos é um processo iterativo. Esse modelo tem qualidade inicial inferior, pois o tutorial usa conjuntos de dados pequenos para fornecer um treinamento rápido do modelo. Se você não estiver satisfeito com a qualidade do modelo, tente melhorá-lo fornecendo conjuntos de dados de treinamento maiores ou escolhendo diferentes algoritmos de treinamento com diferentes hiperparâmetros para cada algoritmo.

Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis).

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como:
> [!div class="checklist"]
> * Compreender o problema
> * Selecionar o algoritmo de aprendizado de máquina apropriado
> * Preparar seus dados
> * Transformar os dados
> * Treinar o modelo
> * Avaliar o modelo
> * Prever com o modelo treinado
> * Implantar e prever com um modelo carregado

Avançar para o próximo tutorial para saber mais
> [!div class="nextstepaction"]
> [Classificação de problema](github-issue-classification.md)
