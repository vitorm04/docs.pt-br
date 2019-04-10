---
title: Usar o ML.NET em um cenário de classificação multiclasse de problema do GitHub
description: Descubra como usar o ML.NET em um cenário de classificação multiclasse para classificar os problemas do GitHub a fim de atribuí-los a uma determinada área.
ms.date: 03/12/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: fc21a37fe585ed4b9880ec86ee26815e0668108c
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/04/2019
ms.locfileid: "58920981"
---
# <a name="tutorial-use-mlnet-in-a-multiclass-classification-scenario-to-classify-github-issues"></a>Tutorial: Usar o ML.NET em um cenário de classificação multiclasse para classificar os problemas do GitHub

Este tutorial de exemplo ilustra o uso do ML.NET para criar um classificador de problema do GitHub por meio de um aplicativo de console do .NET Core usando C# no Visual Studio 2017.

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

> [!NOTE]
> Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações. Para obter mais informações, visite [a introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Este tutorial e uma amostra relacionada estão usando o **ML.NET versão 0.11** no momento. Saiba mais nas notas de versão no [repositório do github dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

## <a name="github-issue-sample-overview"></a>Visão geral de exemplo de problema do GitHub

A amostra é um aplicativo de console que usa o ML.NET para treinar um modelo que classifica e prevê o rótulo da área para um problema do GitHub. Ele também avalia o modelo com um segundo conjunto de dados para análise de qualidade. Os conjuntos de dados do problema são do repositório do GitHub do dotnet/corefx.

Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification).

## <a name="prerequisites"></a>Pré-requisitos

* [Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.

* O [arquivo de problemas do Github separados por tabulação (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).
* O [arquivo de testes de problemas do Github separados por tabulação (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).

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
   * **Usar o Modelo para prever**

### <a name="understand-the-problem"></a>Compreender o problema

Você primeiro precisa compreender o problema, para que possa dividi-lo em partes que possam oferecer suporte à criação e ao treinamento do modelo. Dividir o problema permite prever e avaliar os resultados.

O problema neste tutorial é entender a qual área os problemas do GitHub em entrada pertencem, para rotulá-los corretamente para priorização e agendamento.

Você pode dividir o problema nas seguintes partes:

* o texto de título do problema
* o texto da descrição do problema
* um valor de área para os dados de treinamento de modelo
* um valor de área prevista que você pode avaliar e, em seguida, usar operacionalmente

Em seguida, você precisa **determinar** a área, o que ajuda na seleção da tarefa de aprendizado de máquina.

## <a name="select-the-appropriate-machine-learning-algorithm"></a>Selecionar o algoritmo de aprendizado de máquina apropriado

Com este problema, você está a par dos seguintes fatos:

Dados de treinamento:

Os problemas do GitHub podem ser rotulados em várias áreas (**Área**) como nos exemplos a seguir:

* area-System.Numerics
* area-System.Xml
* area-Infrastructure
* area-System.Linq
* area-System.IO

Preveja a **Área** de um novo problema do GitHub como nos exemplos a seguir:

* Contract.Assert versus Debug.Assert
* Tornar os campos somente leitura em System.Xml

O algoritmo de aprendizado de máquina de classificação é mais adequado para esse cenário.

### <a name="about-the-classification-learning-algorithm"></a>Sobre o algoritmo de aprendizado de classificação

A classificação é um algoritmo de aprendizado de máquina que usa os dados para **determinar** a categoria, o tipo ou a classe de um item ou de uma linha de dados. Por exemplo, você pode usar a classificação para:

* Identificar o sentimento como positivo ou negativo.
* Classificar email como spam, lixo eletrônico ou bom.
* Determinar se a amostra de laboratório de um paciente é cancerígena.
* Categorizar os clientes pela sua propensão a responder a uma campanha de vendas.

Os casos de uso do algoritmo de aprendizado de classificação são geralmente um dos seguintes tipos:

* Binário: A ou B.
* Multiclasse: várias categorias que podem ser previstas usando um único modelo.

Para esse tipo de problema, use um algoritmo de aprendizado de classificação Multiclasse, pois a previsão de categoria do problema pode ser uma das várias categorias (multiclasse), em vez de apenas duas (binária).

## <a name="create-a-console-application"></a>Criar um aplicativo de console

### <a name="create-a-project"></a>Criar um projeto

1. Abra o Visual Studio 2017. Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus. Na caixa de diálogo **Novo Projeto**, selecione o nó **Visual C#** seguido pelo nó **.NET Core**. Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)**. Na caixa de texto **Nome**, digite "GitHubIssueClassification" e selecione o botão **OK**.

2. Crie um diretório chamado *Data* no seu projeto para salvar seus arquivos do conjunto de dados:

    No **Gerenciador de Soluções**, clique com o botão direito do mouse no seu projeto e selecione **Adicionar** > **Nova Pasta**. Digite "Data" e pressione Enter.

3. Crie um diretório chamado *Modelos* em seu projeto para salvar seu modelo:

    No **Gerenciador de Soluções**, clique com o botão direito do mouse no seu projeto e selecione **Adicionar** > **Nova Pasta**. Digite "Modelos" e pressione ENTER.

4. Instalar o **Pacote NuGet Microsoft.ML**:

    No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**. Escolha "nuget.org" como a Origem do pacote, selecione a guia Procurar, pesquise por **Microsoft.ML**, selecione o pacote na lista e escolha o botão **Instalar**. Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.

### <a name="prepare-your-data"></a>Preparar seus dados

1. Baixe os conjuntos de dados [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) e [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) e salve-os na pasta *Dados* criada anteriormente. O primeiro conjunto de dados treina o modelo de aprendizado de máquina e o segundo pode ser usado para avaliar a precisão do seu modelo.

2. No Gerenciador de Soluções, clique com o botão direito do mouse em cada um dos arquivos \*.tsv e selecione **Propriedades**. Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.

### <a name="create-classes-and-define-paths"></a>Criar classes e definir demarcadores

Adicione as seguintes instruções `using` adicionais ao início do arquivo *Program.cs*:

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

Crie três campos globais para manter os caminhos para os arquivos baixados recentemente e variáveis globais para `MLContext`, `DataView`, `PredictionEngine` e `TextLoader`:

* `_trainDataPath` tem o demarcador para o conjunto de dados usado para treinar o modelo.
* `_testDataPath` tem o demarcador para o conjunto de dados usado para avaliar o modelo.
* `_modelPath` tem o demarcador em que o modelo treinado é salvo.
* `_mlContext` é o <xref:Microsoft.ML.MLContext> que fornece o contexto de processamento.
* `_trainingDataView` é o <xref:Microsoft.Data.DataView.IDataView> usado para processar o conjunto de dados de treinamento.
* `_predEngine` é o <xref:Microsoft.ML.PredictionEngine%602> usado para previsões individuais.
* `_reader` é o <xref:Microsoft.ML.Data.TextLoader> usado para carregar e transformar os conjuntos de dados.

Adicione o seguinte código à linha logo acima do método `Main` para especificar estes caminhos e as outras variáveis:

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

Crie algumas classes para os dados de entrada e as previsões. Adicione uma nova classe ao seu projeto:

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.

1. Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *GitHubIssueData.cs*. Em seguida, selecione o botão **Adicionar**.

    O arquivo *GitHubIssueData.cs* é aberto no editor de códigos. Adicione a seguinte instrução `using` acima de *GitHubIssueData.cs*:

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

Remova a definição de classe existente e adicione o seguinte código, que tem duas classes, `GitHubIssue` e `IssuePrediction`, ao arquivo *GitHubIssueData.cs*:

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

`GitHubIssue` é a classe de conjunto de dados de entrada e tem os seguintes campos <xref:System.String>:

* `ID` contém um valor para a ID do problema do GitHub
* `Area` contém um valor para o rótulo `Area`
* `Title` contém o título do problema do GitHub
* `Description` contém a descrição do problema do GitHub

`IssuePrediction` é a classe usada para previsão depois que o modelo foi treinado. Tem um único `string` (`Area`) e um atributo `PredictedLabel` `ColumnName`. O `Label` é usado para criar e treinar o modelo e também é usado com um segundo conjunto de dados para avaliar o modelo. O `PredictedLabel` é usado durante a previsão e avaliação. Para avaliação, uma entrada com dados de treinamento, os valores previstos e o modelo são usados.

Ao criar um modelo com o ML.NET, comece criando um <xref:Microsoft.ML.MLContext>. `MLContext` é conceitualmente comparável ao uso de `DbContext` no Entity Framework. O ambiente fornece um contexto para seu trabalho de ML que pode ser usado no acompanhamento e registro em log da exceção.

### <a name="initialize-variables-in-main"></a>Inicializar variáveis em Main

Inicialize a variável global `_mlContext` com uma nova instância de `MLContext` com uma semente aleatória (`seed: 0`) para obter resultados repetíveis/determinísticos entre vários treinamentos.  Substitua a linha `Console.WriteLine("Hello World!")` pelo seguinte código no método `Main`:

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a>Carregar os dados

Carregaremos os dados usando a variável global `_trainingDataView` <xref:Microsoft.Data.DataView.IDataView> com o parâmetro `_trainDataPath`.

 Como a entrada e a saída de [`Transforms`](../basic-concepts-model-training-in-mldotnet.md#transformer), uma `DataView` é o tipo de pipeline de dados fundamental, comparável a `IEnumerable` para `LINQ`.

No ML.NET, os dados são semelhantes a um `SQL view`. Eles são heterogêneos e avaliados e esquematizados lentamente. O objeto é a primeira parte do pipeline e carrega os dados. Para este tutorial, ele carrega um conjunto de dados com títulos, descrições e rótulo do GitHub da área correspondente do problema. O `DataView` é usado para criar o modelo e treiná-lo.

Já que o tipo do modelo de dados `GitHubIssue` criado anteriormente corresponde ao esquema de conjunto de dados, você pode combinar a inicialização, o mapeamento e o carregamento de conjunto de dados em uma única linha de código.

Carregue os dados, usando o wrapper `MLContext.Data.LoadFromTextFile` do [método LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29). Ele retorna um <xref:Microsoft.Data.DataView.IDataView> que infere o esquema de conjunto de dados a partir do tipo de modelo de dados `GitHubIssue` e usa o cabeçalho do conjunto de dados. 

Você definiu o esquema de dados anteriormente ao criar a classe `GitHubIssue`. Para o esquema:

* a primeira coluna `ID` (ID de problema do GitHub)
* a segunda coluna `Area` (a previsão do treinamento)
* a terceira coluna `Title` (título do problema de GitHub) é o primeiro [recurso](../resources/glossary.md##feature) usado para prever o `Area`
* a quarta coluna `Description` é o segundo recurso usado para prever o `Area`

Para inicializar e carregar a variável global `_trainingDataView` para utilizá-la para o pipeline, adicione o seguinte código após a inicialização de `mlContext`:

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]

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

O pré-processamento e a limpeza de dados são tarefas importantes que ocorrem antes de um conjunto de dados ser usado efetivamente para o aprendizado de máquina. Os dados brutos costumam ser ruidosos e pouco confiáveis, e podem apresentar valores faltantes. Usar dados sem essas tarefas de modelagem pode produzir resultados enganosos.

Os pipelines de transformação do ML.NET compõem um conjunto `transforms`personalizado que é aplicado aos dados antes do treinamento ou do teste. A principal finalidade das transformações é a [personalização](../resources/glossary.md#feature-engineering) de dados. Os algoritmos de aprendizado de máquina entendem os [dados personalizados](../resources/glossary.md#feature), portanto, a próximo etapa é transformar nossos dados textuais em um formato que nossos algoritmos de aprendizado de máquina reconheçam. Esse formato é um [vetor numérico](../resources/glossary.md#numerical-feature-vector).

Nas próximas etapas, trataremos das colunas pelos nomes definidos na classe `GitHubIssue`.

Quando o modelo é treinado e avaliado, por padrão, os valores na coluna **Rótulo** são considerados os valores corretos a serem previstos. Como queremos prever o rótulo do GitHub da Área para um `GitHubIssue`, copie a coluna `Area` na coluna **Rótulo**. Para fazer isso, use o `MLContext.Transforms.Conversion.MapValueToKey`, que é um wrapper para a classe de transformação <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A>.  O <xref:Microsoft.ML.Data.EstimatorChain%601> retorna um `MapValueToKey` que será efetivamente um pipeline. Dê ao `pipeline` um nome de sua preferência e, em seguida, anexe o instrutor à `EstimatorChain`. Adicione a seguinte linha de código:

[!code-csharp[MapValueToKey](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

 A personalização atribui valores de chaves numéricas diferentes para os diferentes valores em cada uma das colunas e é usado pelo algoritmo de aprendizado de máquina. Em seguida, chame `mlContext.Transforms.Text.FeaturizeText` que personaliza as colunas do texto (`Title` e `Description`) em um vetor numérico para cada `TitleFeaturized` e `DescriptionFeaturized` chamado. Acrescente a personalização para ambas as colunas ao pipeline com o código a seguir:

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

>[!WARNING]
> A versão do ML.NET 0.10 alterou a ordem dos parâmetros de transformação. Isso não apresentará erros até você compilar. Use os nomes de parâmetro para transformações, conforme ilustrado no snippet de código anterior.

A última etapa na preparação de dados combina todas as colunas de recursos na coluna **Features** usando a classe de transformação `Concatenate`. Por padrão, um algoritmo de aprendizado processa apenas os recursos da coluna **Features**. Acrescente esta transformação ao pipeline com o código a seguir:

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
* Salva o modelo em um arquivo `.zip`.
* Retorna o modelo.

Crie o método `BuildAndTrainModel`, logo após o método `Main`, usando o seguinte código:

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

Observe que dois parâmetros são passados para o método BuildAndTrainModel; um `IDataView` para o conjunto de dados de treinamento (`trainingDataView`) e um <xref:Microsoft.ML.Data.EstimatorChain%601> para o pipeline de processamento criado no ProcessData (`pipeline`).

 Adicione o seguinte código como a primeira linha do método `BuildAndTrainModel`:

### <a name="choose-a-learning-algorithm"></a>Escolher um algoritmo de aprendizado

Para adicionar o algoritmo de aprendizado, chame o método de wrapper `mlContext.MulticlassClassification.Trainers.StochasticDualCoordinateAscent` que retorna um objeto <xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer>.  O `SdcaMultiClassTrainer` é anexado ao `pipeline` e aceita os `Title` e `Description` (`Features`) personalizados e os parâmetro de entrada `Label` para aprender com os dados históricos. Você também precisa mapear o rótulo para o valor para retorná-lo ao seu estado legível original. Realize ambas essas ações com o código a seguir:

[!code-csharp[AddTrainer](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

### <a name="train-the-model"></a>Treinar o modelo

Você treina o modelo, <xref:Microsoft.ML.Data.TransformerChain%601>, com base no conjunto de dados que foi carregado e transformado. Depois que o avaliador tiver sido definido, treine o modelo usando o <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> e forneça os dados de treinamento já carregados. Esse método retorna um modelo a ser usado para previsões. `trainingPipeline.Fit()` treina o pipeline e retorna um `Transformer` com base no `DataView` passado. O teste não é executado até que o método `.Fit()` seja executado.

Adicione o seguinte código ao método `BuildAndTrainModel`:

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

Embora o `model` seja um `transformer` que opera em várias linhas de dados, a necessidade de previsões em exemplos individuais é um cenário comum de produção. O <xref:Microsoft.ML.PredictionEngine%602> é um wrapper que é retornado do método `CreatePredictionEngine`. Adicionaremos o seguinte código para criar `PredictionEngine` como a próxima linha no método `BuildAndTrainModel`:

[!code-csharp[CreatePredictionEngine1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a>Prever com o modelo treinado

Adicione um problema do GitHub para testar a previsão do modelo treinado no método `Predict` ao criar uma instância de `GitHubIssue`:

[!code-csharp[CreateTestIssue1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

Você pode usá-lo para prever o rótulo `Area` de uma única instância dos dados do problema. Para obter uma previsão, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> nos dados. Os dados de entrada são uma cadeia de caracteres e o modelo inclui a personalização. Seu pipeline está em sincronia durante o treinamento e a previsão. Você não precisou escrever código de pré-processamento/personalização especificamente para previsões, e a mesma API cuida das previsões de lote e de uso único.

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

Assim como você fez anteriormente com o conjunto de dados de treinamento, você pode combinar a inicialização, o mapeamento e testar o carregamento do conjunto de dados em uma linha de código. Você pode avaliar o modelo usando esse conjunto de dados como uma verificação de qualidade. Adicione o seguinte código ao método `Evaluate`:

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

O método `MulticlassClassificationContext.Evaluate` é o wrapper para o método <xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A>, que calcula as métricas de qualidade para o modelo usando o conjunto de dados especificado. Ele retorna um objeto <xref:Microsoft.ML.Data.MultiClassClassifierMetrics> que contém as métricas gerais calculadas pelos avaliadores de classificação multiclasse.
Para exibir as métricas para determinar a qualidade do modelo, você precisará obtê-las primeiro.
Observe o uso do método `Transform` da variável global `_trainedModel` de aprendizado de máquina (um transformador) para inserir os recursos e retornar previsões. Adicione o seguinte código ao método `Evaluate` como a linha seguinte:

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

As métricas a seguir são avaliadas para classificação multiclasse:

* Microprecisão – todo par de classe/exemplo contribui igualmente para a métrica de precisão.  Convém que a Microprecisão seja tão próxima de 1 quanto possível.

* Macroprecisão – toda classe contribui igualmente para a métrica de precisão. Classes minoritárias recebem o mesmo peso que as classes maiores. Convém que a Macroprecisão seja tão próxima de 1 quanto possível.

* Perda de log – consulte [Perda de log](../resources/glossary.md#log-loss). Convém que a Perda de log seja tão próxima de zero quanto possível.

* Redução de perda de log – varia de [-inf, 100], em que 100 é composto pelas previsões perfeitas e 0 indica previsões de média. Convém que a redução de perda de log seja tão próxima de zero quanto possível.

### <a name="displaying-the-metrics-for-model-validation"></a>Exibir as métricas para validação de modelo

Use o código a seguir para exibir as métricas, compartilhar os resultados e, em seguida, agir com relação a eles:

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

### <a name="save-the-trained-and-evaluated-model"></a>Salvar o modelo treinado e avaliado

Neste ponto, você tem um modelo de tipo <xref:Microsoft.ML.Data.TransformerChain%601> que pode ser integrado em qualquer um dos seus aplicativos .NET existentes ou novos. Para salvar seu modelo treinado como um arquivo .zip, adicione o seguinte código para chamar o método `SaveModelAsFile` como a linha seguinte em `BuildAndTrainModel`:

[!code-csharp[CallSaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallSaveModel)]

## <a name="save-the-model-as-a-zip-file"></a>Salvar o modelo como um arquivo .zip

Crie o método `SaveModelAsFile`, logo após o método `Evaluate`, usando o seguinte código:

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

O método `SaveModelAsFile` executa as seguintes tarefas:

* Salva o modelo como um arquivo .zip.

Em seguida, crie um método para salvar o modelo para que ele possa ser reutilizado e consumido em outros aplicativos. O `ITransformer` tem um método <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> que usa o campo global `_modelPath` e um <xref:System.IO.Stream>. Para salvar o modelo como um arquivo zip, crie o `FileStream` imediatamente antes de chamar o método `SaveTo`. Adicione o seguinte código ao método `SaveModelAsFile` como a linha seguinte:

[!code-csharp[SaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SaveModel)]

Você também pode exibir onde o arquivo foi gravado ao gravar uma mensagem de console com o `_modelPath`, usando o seguinte código:

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="deploy-and-predict-with-a-loaded-model"></a>Implantar e prever com um modelo carregado

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

Primeiro, carregue o modelo que você salvou anteriormente com o código a seguir:

[!code-csharp[LoadModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadModel)]

Adicione um problema do GitHub para testar a previsão do modelo treinado no método `Predict` ao criar uma instância de `GitHubIssue`:

[!code-csharp[AddTestIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]
  
Agora que tem um modelo, você pode usá-lo para prever o rótulo do GitHub da área de uma única instância dos dados do problema do GitHub. Para obter uma previsão, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> nos dados. Os dados de entrada são uma cadeia de caracteres e o modelo inclui a personalização. Seu pipeline está em sincronia durante o treinamento e a previsão. Você não precisou escrever código de pré-processamento/personalização especificamente para previsões, e a mesma API cuida das previsões de lote e de uso único. Adicione o código a seguir ao método `PredictIssue` para as previsões:

[!code-csharp[PredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a>Usando o modelo carregado para previsão

Exiba `Area` para categorizar o problema e agir adequadamente para solucioná-lo. Crie uma exibição para os resultados usando o seguinte código <xref:System.Console.WriteLine?displayProperty=nameWithType>:

[!code-csharp[DisplayResults](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a>Resultados

Seus resultados devem ser semelhantes aos seguintes. Conforme o pipeline processa, exibe mensagens. Você pode ver avisos ou mensagens de processamento. Essas mensagens foram removidas dos resultados a seguir para ficar mais claro.

```console
=============== Single Prediction just-trained-model - Result: area-System.Net ===============
The model is saved to C:\Users\johalex\dotnet-samples\samples\machine-learning\tutorials\GitHubIssueClassification\bin\Debug\netcoreapp2.0\..\..\..\Models\model.zip
*************************************************************************************************************
*       Metrics for Multi-class Classification model - Test Data
*------------------------------------------------------------------------------------------------------------
*       MicroAccuracy:    0.74
*       MacroAccuracy:    0.687
*       LogLoss:          .932
*       LogLossReduction: 63.852
*************************************************************************************************************
=============== Single Prediction - Result: area-System.Data ===============
```

Parabéns! Agora você criou com sucesso um modelo de machine learning para classificar e prever um rótulo de Área para um problema do GitHub. Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification).

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
> [Previsão do valor da corrida do táxi](taxi-fare.md)
