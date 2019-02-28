---
title: Usar o ML.NET em um cenário de classificação binária de análise de sentimento
description: Descubra como usar o ML.NET em um cenário de classificação binária para entender como usar a previsão de sentimentos para executar a ação apropriada.
ms.date: 02/15/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 9afdf1d8369e71f9614ebc2bf327e98d31b988ff
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748382"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a>Tutorial: Usar o ML.NET em um cenário de classificação binária de análise de sentimento

> [!NOTE]
> Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações. Para obter mais informações, visite [a introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Este tutorial de exemplo ilustra o uso do ML.NET para criar um classificador de sentimento por meio de um aplicativo de console do .NET Core usando C# no Visual Studio 2017.

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

A amostra é um aplicativo de console que usa o ML.NET para treinar um modelo que classifica e prevê o sentimento como positivo ou negativo. Ele também avalia o modelo com um segundo conjunto de dados para análise de qualidade. Os conjuntos de dados de sentimento são do projeto WikiDetox.

Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis).

## <a name="prerequisites"></a>Pré-requisitos

* [Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.

* [Arquivo separado de guia de dados de linha detox da Wikipédia (wikiPedia-detox-250-line-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).
* [Arquivo separado de guia de teste de linha detox da Wikipédia (wikipedia-detox-250-line-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).

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

Dados de treinamento: os comentários no site podem ser tóxicos (1) ou não tóxicos (0) (**sentimento**).
Preveja o **sentimento** de um novo comentário no site, seja tóxico ou não tóxico, como nos exemplos a seguir:

* Evite inserir qualquer conteúdo sem sentido na Wikipédia.
* Ele é o melhor, e o artigo deve dizer isso.

O algoritmo de aprendizado de máquina de classificação é mais adequado para esse cenário.

### <a name="about-the-classification-task"></a>Sobre a tarefa de classificação

A classificação é um algoritmo de aprendizado de máquina que usa os dados para **determinar** a categoria, o tipo ou a classe de um item ou de uma linha de dados. Por exemplo, você pode usar a classificação para:

* Identificar o sentimento como positivo ou negativo.
* Classificar email como spam, lixo eletrônico ou bom.
* Determinar se a amostra de laboratório de um paciente é cancerígena.
* Categorizar os clientes pela sua propensão a responder a uma campanha de vendas.

Algoritmos de classificação são frequentemente de um dos seguintes tipos:

* Binário: A ou B.
* Multiclasse: várias categorias que podem ser previstas usando um único modelo.

## <a name="create-a-console-application"></a>Criar um aplicativo de console

1. Abra o Visual Studio 2017. Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus. Na caixa de diálogo **Novo Projeto**, selecione o nó **Visual C#** seguido pelo nó **.NET Core**. Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)**. Na caixa de texto **Nome**, digite "SentimentAnalysis" e, em seguida, selecione o botão **OK** .

2. Crie um diretório chamado *Data* no seu projeto para salvar seus arquivos do conjunto de dados:

    No **Gerenciador de Soluções**, clique com o botão direito do mouse no seu projeto e selecione **Adicionar** > **Nova Pasta**. Digite "Dados" e pressione Enter.

3. Instalar o **Pacote NuGet Microsoft.ML**:

    No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**. Escolha "nuget.org" como a Origem do pacote, selecione a guia Procurar, pesquise por **Microsoft.ML**, selecione o pacote na lista e escolha o botão **Instalar**. Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.

### <a name="prepare-your-data"></a>Preparar seus dados

1. Baixe os conjuntos de dados [Wikipedia detox-250-line-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) e [wikipedia-detox-250-line-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) e salve-os na pasta *Dados* criada anteriormente. O primeiro conjunto de dados treina o modelo de aprendizado de máquina e o segundo pode ser usado para avaliar a precisão do seu modelo.

2. No Gerenciador de Soluções, clique com o botão direito do mouse em cada um dos arquivos \*.tsv e selecione **Propriedades**. Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.

### <a name="create-classes-and-define-paths"></a>Criar classes e definir demarcadores

Adicione as seguintes instruções `using` adicionais ao início do arquivo *Program.cs*:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#1 "Add necessary usings")]

Você precisa criar três campos ​​globais para manter os caminhos dos arquivos baixados recentemente e uma variável global para o `TextLoader`:

* `_trainDataPath` tem o demarcador para o conjunto de dados usado para treinar o modelo.
* `_testDataPath` tem o demarcador para o conjunto de dados usado para avaliar o modelo.
* `_modelPath` tem o demarcador em que o modelo treinado é salvo.
* O `_textLoader` é o <xref:Microsoft.ML.Data.TextLoader> usado para carregar e transformar os conjuntos de dados.

Adicione o seguinte código à linha logo acima do método `Main` para especificar estes caminhos e a variável `_textLoader`:

[!code-csharp[Declare global variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#2 "Declare global variables")]

Você precisa criar algumas classes para os dados e previsões de entrada. Adicione uma nova classe ao seu projeto:

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.

1. Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentData.cs*. Em seguida, selecione o botão **Adicionar**.

    O arquivo *SentimentData.cs* é aberto no editor de códigos. Adicione a seguinte instrução `using` acima de *SentimentData.cs*:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#1 "Add necessary usings")]

Remova a definição de classe existente e adicione o seguinte código, que possui duas classes `SentimentData` e `SentimentPrediction`, ao arquivo *SentimentData.cs*:

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#2 "Declare data record types")]

`SentimentData` é a classe do conjunto de dados de entrada e tem um `float` (`Sentiment`) que tem um valor para sentimento positivo ou negativo e uma cadeia de caracteres para o comentário (`SentimentText`). Ambos os campos têm atributos `Column` anexados a eles. Este atributo descreve a ordem de cada campo no arquivo de dados e é o campo `Label`. `SentimentPrediction` é a classe usada para previsão depois que o modelo foi treinado. Tem um único booliano (`Sentiment`) e um atributo `PredictedLabel` `ColumnName`. O `Label` é usado para criar e treinar o modelo e também é usado com um segundo conjunto de dados para avaliar o modelo. O `PredictedLabel` é usado durante a previsão e avaliação. Para avaliação, uma entrada com dados de treinamento, os valores previstos e o modelo são usados.

Ao criar um modelo com o ML.NET, comece criando um `MLContext`. Isso é comparável conceitualmente ao uso de `DbContext` no Entity Framework. O ambiente fornece um contexto para seu trabalho de ML que pode ser usado no acompanhamento e registro em log da exceção.

### <a name="initialize-variables-in-main"></a>Inicializar variáveis em Main

Crie uma variável chamada `mlContext` e inicialize-a com uma nova instância de `MLContext`.  Substitua a linha `Console.WriteLine("Hello World!")` pelo seguinte código no método `Main`:

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#3 "Create the ML Context")]

Em seguida, para configurar o carregamento de dados, inicialize a variável global `_textLoader` para reutilizá-la.  Quando você cria um `TextLoader` usando `MLContext.Data.CreateTextLoader`, você passa o contexto necessário e a classe <xref:Microsoft.ML.Data.TextLoader.Arguments> que permite a personalização.

 Especifique o esquema de dados passando uma matriz de objetos <xref:Microsoft.ML.Data.TextLoader.Column> para o carregador que contém todos os nomes de coluna e seus tipos. Você definiu o esquema de dados anteriormente ao criar nossa classe `SentimentData`. Para nosso esquema, a primeira coluna (Label) é <xref:System.Boolean> (a previsão) e a segunda coluna (SentimentText) é o recurso do tipo texto/cadeia de caracteres usado para prever o sentimento.
A classe `TextLoader` retorna um <xref:Microsoft.ML.Data.TextLoader> completamente inicializado  

Para inicializar a variável global `_textLoader` para reutilizá-la nos conjuntos de dados necessários, adicione o seguinte código após a inicialização de `mlContext`:

[!code-csharp[initTextLoader](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#4 "Initialize the TextLoader")]

Adicione o seguinte como a linha seguinte de código no método `Main`:

[!code-csharp[Train](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#5 "Train your model")]

O método `Train` executa as seguintes tarefas:

* Carrega os dados.
* Extrai e transforma os dados.
* Treina o modelo.
* Prevê o sentimento com base nos dados de teste.
* Retorna o modelo.

Crie o método `Train`, logo após o método `Main`, usando o seguinte código:

```csharp
 public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

Observe que dois parâmetros são passados para o método Train. Um `MLContext` para o contexto (`mlContext`) e um <xref:System.String> para o caminho do conjunto de dados (`dataPath`). Você vai usar esse método mais de uma vez para treinamento e teste.

## <a name="load-the-data"></a>Carregar os dados

Você carregará os dados usando a variável global `_textLoader` com o parâmetro `dataPath`. Ele retorna um <xref:Microsoft.Data.DataView.IDataView>. Como a entrada e saída de `Transforms`, um `DataView` é o tipo de pipeline de dados fundamental, comparável ao `IEnumerable` para `LINQ`.

No ML.NET, os dados são semelhantes a um modo de exibição SQL. Eles são heterogêneos e avaliados e esquematizados lentamente. O objeto é a primeira parte do pipeline e carrega os dados. Neste tutorial, ele carrega um conjunto de dados com comentários e o sentimento tóxico ou não tóxico correspondente. Isso é usado para criar o modelo e treiná-lo.

 Adicione o seguinte código como a primeira linha do método `Train`:

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#6 "loading training dataset")]

## <a name="extract-and-transform-the-data"></a>Extrair e transformar os dados

O pré-processamento e a limpeza de dados são tarefas importantes que ocorrem antes de um conjunto de dados ser usado efetivamente para o aprendizado de máquina. Os dados brutos costumam ser ruidosos e pouco confiáveis, e podem apresentar valores faltantes. Usar dados sem essas tarefas de modelagem pode produzir resultados enganosos.

Os pipelines de transformação do ML.NET compõem um conjunto personalizado de transformações que são aplicadas aos seus dados antes do treinamento ou teste. A principal finalidade das transformações é a [personalização](../resources/glossary.md#feature-engineering) de dados. Os algoritmos de aprendizado de máquina entendem os [dados personalizados](../resources/glossary.md#feature), portanto, a próximo etapa é transformar nossos dados textuais em um formato que nossos algoritmos de aprendizado de máquina reconheçam. Esse formato é um [vetor numérico](../resources/glossary.md#numerical-feature-vector).

Em seguida, chame `mlContext.Transforms.Text.FeaturizeText` que personaliza a coluna de texto (`SentimentText`) em um vetor numérico chamado `Features`, usado pelo algoritmo de aprendizado de máquina. Essa é uma chamada de wrapper que retorna um <xref:Microsoft.ML.Data.EstimatorChain%601> que será efetivamente um pipeline. Dê ao `pipeline` um nome de sua preferência e, em seguida, anexe o instrutor à `EstimatorChain`. Adicione isso como a linha seguinte de código:

[!code-csharp[TextFeaturizingEstimator](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#7 "Add a TextFeaturizingEstimator")]

>[!WARNING]
> A versão do ML.NET 0.10 alterou a ordem dos parâmetros de transformação. Isso não apresentará um erro até que você execute o aplicativo e compile o modelo. Use os nomes de parâmetro para transformações, conforme ilustrado no snippet de código anterior.

Esta é a etapa de pré-processamento/personalização. Usar componentes adicionais disponíveis no ML.NET pode permitir melhores resultados com o seu modelo.

## <a name="choose-a-learning-algorithm"></a>Escolher um algoritmo de aprendizado

Para adicionar o instrutor, chame o método `mlContext.Transforms.Text.FeaturizeText` do wrapper que retorna um objeto <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer>. Esse é um aprendiz de árvore de decisão que você usará neste pipeline. O `FastTreeBinaryClassificationTrainer` é anexado ao `pipeline` e aceita o parâmetro `SentimentText` (`Features`) personalizado e o parâmetro `Label` de entrada para aprender com os dados históricos.

Adicione o seguinte código ao método `Train`:

[!code-csharp[FastTreeBinaryClassificationTrainer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#8 "Add a FastTreeBinaryClassificationTrainer")]

## <a name="train-the-model"></a>Treinar o modelo

Você treina o modelo, <xref:Microsoft.ML.Data.TransformerChain%601>, com base no conjunto de dados que foi carregado e transformado. Depois que o avaliador tiver sido definido, treine o modelo usando o <xref:Microsoft.ML.Data.EstimatorChain%601.Fit*> e forneça os dados de treinamento já carregados. Isso retornará um modelo que será usado nas previsões. `pipeline.Fit()` treina o pipeline e retorna um `Transformer` com base no `DataView` passado. O experimento não será executado até que isso ocorra.

Adicione o seguinte código ao método `Train`:

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#9 "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a>Salvar e retornar o modelo treinado para usar na avaliação

Neste ponto, você tem um modelo de tipo <xref:Microsoft.ML.Data.TransformerChain%601> que pode ser integrado em qualquer um dos seus aplicativos .NET existentes ou novos. Retorne o modelo no final do método `Train`.

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#10 "Return the model")]

## <a name="evaluate-the-model"></a>Avaliar o modelo

Agora que você criou e treinou o modelo, precisa avaliá-lo com um conjunto de dados diferente para garantia de qualidade e validação. No método `Evaluate`, o modelo criado em `Train` é passado para ser avaliado. Crie o método `Evaluate` , logo após `Train`, como no código a seguir:

```csharp
public static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

O método `Evaluate` executa as seguintes tarefas:

* Carrega o conjunto de dados de teste.
* Cria o avaliador binário.
* Avalia o modelo e cria métricas.
* Exibe as métricas.

Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `Train`, usando o seguinte código:

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#11 "Call the Evaluate method")]

Você carregará o conjunto de dados de teste usando a variável global `_textLoader` anteriormente inicializada com o campo global `_testDataPath`. Você pode avaliar o modelo usando esse conjunto de dados como uma verificação de qualidade. Adicione o seguinte código ao método `Evaluate`:

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#12 "Load the test dataset")]

Em seguida, você usará o parâmetro `model` de aprendizado de máquina (um transformador) para inserir os recursos e retornar previsões. Adicione o seguinte código ao método `Evaluate` como a linha seguinte:

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#13 "Predict using the Transformer")]

O método `BinaryClassificationContext.Evaluate` calcula as métricas de qualidade para o `PredictionModel` usando o conjunto de dados especificado. Ele retorna um objeto `BinaryClassificationEvaluator.CalibratedResult` que contém as métricas gerais calculadas pelos avaliadores de classificação binária. Para exibi-los a fim de determinar a qualidade do modelo, é preciso primeiro obter as métricas. Adicione o seguinte código ao método `Evaluate` como a linha seguinte:

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#14 "Compute Metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a>Exibir as métricas para validação de modelo

Use o código a seguir para exibir as métricas, compartilhar os resultados e, em seguida, agir com relação a eles:

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#15 "Display selected metrics")]

Para salvar seu modelo como um arquivo .zip antes de retornar, adicione o seguinte código para chamar o método `SaveModelAsFile` como a linha seguinte em `Evaluate`:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#23 "Save the model")]

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

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#24 "Add the SaveTo Method")]
Implante e preveja com um modelo carregado. Você também pode exibir onde o arquivo foi gravado ao gravar uma mensagem de console com o `_modelPath`, usando o seguinte código:

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="predict-the-test-data-outcome-with-the-saved-model"></a>Prever o resultado dos dados de teste com o modelo salvo

Crie o método `Predict`, logo após o método `Evaluate`, usando o seguinte código:

```csharp
private static void Predict(MLContext mlContext, ITransformer model)
{

}
```

O método `Predict` executa as seguintes tarefas:

* Cria um único comentário dos dados de teste.
* Prevê o sentimento com base nos dados de teste.
* Combina dados de teste e previsões para relatórios.
* Exibe os resultados previstos.

Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `Evaluate`, usando o seguinte código:

[!code-csharp[CallPredict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#16 "Call the Predict method")]

Enquanto o `model` é um `transformer` que opera em muitas linhas de dados, um cenário de produção muito comum é a necessidade de previsões em exemplos individuais. O <xref:Microsoft.ML.PredictionEngine%602> é um wrapper que é retornado do método `CreatePredictionEngine`. Vamos adicionar o seguinte código para criar `PredictionEngine` como a primeira linha no método `Predict`:

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#17 "Create the PredictionEngine")]
  
Adicione um comentário para testar as previsões do modelo treinado no método `Predict` ao criar uma instância de `SentimentData`:

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#18 "Create test data for single prediction")]

 Você pode usar isso para prever o sentimento Tóxico ou Não Tóxico de uma única instância dos dados de comentário. Para obter uma previsão, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> nos dados. Observe que os dados de entrada são uma cadeia de caracteres e o modelo inclui a personalização. Seu pipeline está em sincronia durante o treinamento e a previsão. Você não precisou escrever código de pré-processamento/personalização especificamente para previsões, e a mesma API cuida das previsões de lote e de uso único.

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#19 "Create a prediction of sentiment")]

### <a name="using-the-model-prediction"></a>Usando o modelo: previsão

Exiba `SentimentText` e a previsão de sentimento correspondente para compartilhar os resultados e agir de acordo com eles. Isso é chamado de operacionalização, usar os dados retornados como parte das políticas operacionais. Crie uma exibição para os resultados usando o seguinte código <xref:System.Console.WriteLine?displayProperty=nameWithType>:

[!code-csharp[OutputPrediction](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#20 "Display prediction output")]

## <a name="deploy-and-predict-with-a-loaded-model"></a>Implantar e prever com um modelo carregado

Crie o método `PredictWithModelLoadedFromFile`, logo antes do método `SaveModelAsFile`, usando o seguinte código:

```csharp
public static void PredictWithModelLoadedFromFile(MLContext mlContext)
{

}
```

O método `PredictWithModelLoadedFromFile` executa as seguintes tarefas:

* Cria dados de teste em lote.
* Prevê o sentimento com base nos dados de teste.
* Combina dados de teste e previsões para relatórios.
* Exibe os resultados previstos.

Adicione uma chamada ao novo método a partir do método `Main`, logo abaixo da chamada do método `Predict`, usando o seguinte código:

[!code-csharp[CallPredictModelLoaded](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#25 "Call the PredictWithModelLoadedFromFile method")]

Adicione alguns comentários para testar as previsões do modelo treinado no método `PredictWithModelLoadedFromFile`:

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#26 "Create test data for predictions")]

Carregar o modelo

[!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#27 "Load the model")]

Agora que você tem um modelo, pode usá-lo para prever o sentimento tóxico ou não tóxico dos dados do comentário usando o método <xref:Microsoft.ML.Core.Data.ITransformer.Transform%2A>. Para obter uma previsão, use `Predict` em novos dados. Observe que os dados de entrada são uma cadeia de caracteres e o modelo inclui a personalização. Seu pipeline está em sincronia durante o treinamento e a previsão. Você não precisou escrever código de pré-processamento/personalização especificamente para previsões, e a mesma API cuida das previsões de lote e de uso único. Adicione o código a seguir ao método `PredictWithModelLoadedFromFile` para as previsões:

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#28 "Create predictions of sentiments")]

### <a name="using-the-loaded-model-for-prediction"></a>Usando o modelo carregado para previsão

Exiba `SentimentText` e a previsão de sentimento correspondente para compartilhar os resultados e agir de acordo com eles. Isso é chamado de operacionalização, usar os dados retornados como parte das políticas operacionais. Crie um cabeçalho para os resultados usando o seguinte código <xref:System.Console.WriteLine?displayProperty=nameWithType>:

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#29 "Display prediction outputs")]

Antes de exibir os resultados previstos, combine o sentimento e a previsão juntos para ver o comentário original com o sentimento previsto. O código a seguir usa o método <xref:System.Linq.Enumerable.Zip%2A> para que isso aconteça, então adicione o seguinte código:

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#30 "Build the pairs of sentiment data and predictions")]

Agora que você combinou `SentimentText` e `Sentiment` em uma classe, você pode exibir os resultados usando o método <xref:System.Console.WriteLine?displayProperty=nameWithType>:

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#31 "Display the predictions")]

Como nomes de elementos de tuplas inferidos são um novo recurso no C# 7.1 e a versão da linguagem padrão do projeto é C# 7.0, é necessário alterar a versão da linguagem para C# 7.1 ou superior.
Para fazer isso, clique com o botão direito do mouse no nó do projeto no **Gerenciador de Soluções** e selecione **Propriedades**. Selecione a guia **Build** e o botão **Avançado**. No menu suspenso, selecione **C# 7.1** (ou uma versão posterior). Selecione o botão **OK**.

## <a name="results"></a>Resultados

Seus resultados devem ser semelhantes aos seguintes. Conforme o pipeline processa, exibe mensagens. Você pode ver avisos ou mensagens de processamento. Eles foram removidos dos seguintes resultados para maior clareza.

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 94.44%
Auc: 98.77%
F1Score: 94.74%
=============== End of model evaluation ===============

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This is a very rude movie | Prediction: Toxic | Probability: 0.5297049
=============== End of Predictions ===============

=============== New iteration of Model ===============
=============== Create and Train the Model ===============
=============== End of training ===============


The model is saved to: C:\Tutorial\SentimentAnalysis\bin\Debug\netcoreapp2.1\Data\Model.zip

=============== Prediction Test of loaded model with a multiple sample ===============

Sentiment: This is a very rude movie | Prediction: Toxic | Probability: 0.4585565
Sentiment: I love this article. | Prediction: Not Toxic | Probability: 0.09454837

```

Parabéns! Agora você criou com sucesso um modelo de aprendizado de máquina para classificar e prever o sentimento das mensagens. Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis).

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
