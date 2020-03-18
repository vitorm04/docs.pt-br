---
title: 'Tutorial: Analise o sentimento de revisão usando um modelo TensorFlow'
description: Este tutorial mostra como usar um modelo TensorFlow pré-treinado para classificar o sentimento nos comentários do site. O classificador binário de sentimentoé um aplicativo de console C# desenvolvido usando o Visual Studio.
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 688c5b83cef8f21eef8fa24521a85449a9cfbd48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241111"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a>Tutorial: Analise o sentimento das avaliações de filmes usando um modelo TensorFlow pré-treinado em ML.NET

Este tutorial mostra como usar um modelo TensorFlow pré-treinado para classificar o sentimento nos comentários do site. O classificador binário de sentimentoé um aplicativo de console C# desenvolvido usando o Visual Studio.

O modelo TensorFlow usado neste tutorial foi treinado usando avaliações de filmes do banco de dados do IMDB. Depois de terminar de desenvolver o aplicativo, você poderá fornecer texto de revisão de filme e o aplicativo lhe dirá se a revisão tem sentimento positivo ou negativo.

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
>
> * Carregue um modelo TensorFlow pré-treinado
> * Transforme o texto de comentário do site em recursos adequados para o modelo
> * Usar o modelo para fazer uma previsão

Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF).

## <a name="prerequisites"></a>Pré-requisitos

* [Visual Studio 2017 versão 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) com a carga de trabalho ".NET Core cross-platform development" instalada.

## <a name="setup"></a>Instalação

### <a name="create-the-application"></a>Criar o aplicativo

1. Crie um **aplicativo de console .NET Core** chamado "TextClassificationTF".

2. Crie um diretório chamado *Dados* em seu projeto para salvar seus arquivos do conjunto de dados.

3. Instalar o **Pacote NuGet Microsoft.ML**:

    No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**. Escolha "nuget.org" como a fonte do pacote e selecione a guia **Procurar** **Microsoft.ML,** selecione o pacote desejado e selecione o botão **Instalar.** Prossiga com a instalação concordando com os termos de licença do pacote que você escolher. Repita estas etapas para **Microsoft.ML.TensorFlow** e **SciSharp.TensorFlow.Redist**.

### <a name="add-the-tensorflow-model-to-the-project"></a>Adicione o modelo TensorFlow ao projeto

> [!NOTE]
> O modelo para este tutorial é do [repo GitHub dotnet/machinelearning-testdata.](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) O modelo está no formato TensorFlow SavedModel.

1. Baixe o [arquivo zip sentiment_model](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true)e descompacte.

    O arquivo zip contém:

    * `saved_model.pb`: o próprio modelo TensorFlow. O modelo pega uma matriz de comprimento fixo (tamanho 600) inteiro de recursos representando o texto em uma seqüência de revisão do IMDB, e produz duas probabilidades que somam a 1: a probabilidade de que a revisão de entrada tenha um sentimento positivo, e a probabilidade de que a revisão de entrada tenha sentimento negativo.
    * `imdb_word_index.csv`: um mapeamento de palavras individuais para um valor inteiro. O mapeamento é usado para gerar os recursos de entrada para o modelo TensorFlow.

2. Copie o conteúdo do `sentiment_model` diretório mais íntimo no `sentiment_model` diretório *textclassificationTF.* Este diretório contém o modelo e os arquivos de suporte adicionais necessários para este tutorial, conforme mostrado na imagem a seguir:

   ![sentiment_model conteúdo do diretório](./media/text-classification-tf/sentiment-model-files.png)

3. No Solution Explorer, clique com o `sentiment_model` botão direito do mouse em cada um dos arquivos do diretório e do subdiretório e selecione **Propriedades**. Em **Avançado,** altere o valor de **Copiar para Diretório de Saída** para Copiar se mais **novo**.

### <a name="add-using-statements-and-global-variables"></a>Adicionar usando declarações e variáveis globais

1. Adicione as seguintes instruções `using` adicionais ao início do arquivo *Program.cs*: 

   [!code-csharp[AddUsings](../../../samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#AddUsings "Add necessary usings")]

1. Crie duas variáveis globais `Main` logo acima do método para manter o caminho do arquivo do modelo salvo e o comprimento do vetor de recurso.

   [!code-csharp[DeclareGlobalVariables](../../../samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * `_modelPath`é o caminho do arquivo do modelo treinado.
    * `FeatureLength`é o comprimento da matriz de recursos inteiros que o modelo está esperando.

### <a name="model-the-data"></a>Modelar os dados

As críticas de filmes são textos de formulário gratuitos. Seu aplicativo converte o texto no formato de entrada esperado pelo modelo em uma série de etapas discretas.

A primeira é dividir o texto em palavras separadas e usar o arquivo de mapeamento fornecido para mapear cada palavra em uma codificação inteira. O resultado dessa transformação é uma matriz de inteiro de comprimento variável com um comprimento correspondente ao número de palavras na frase.

|Propriedade| Valor|Type|
|-------------|-----------------------|------|
|ComentárioTexto|este filme é muito bom|string|
|Recursos de duração de variáveis|14,22,9,66,78,... |int[]|

O conjunto de recursos de comprimento variável é então redimensionado para um comprimento fixo de 600. Este é o comprimento que o modelo TensorFlow espera.

|Propriedade| Valor|Type|
|-------------|-----------------------|------|
|ComentárioTexto|este filme é muito bom|string|
|Recursos de duração de variáveis|14,22,9,66,78,... |int[]|
|Recursos|14,22,9,66,78,... |int[600]|

1. Crie uma classe para seus `Main` dados de entrada, após o método:

    [!code-csharp[MovieReviewClass](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#MovieReviewClass "Declare movie review type")]

    A classe de `MovieReview`dados `string` de entrada,`ReviewText`tem um para comentários de usuários ( ).

1. Criar uma classe para as características `Main` de comprimento variável, após o método:

    [!code-csharp[VariableLengthFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    A `VariableLengthFeatures` propriedade tem um atributo [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) para designá-la como vetor.  Todos os elementos vetoriais devem ser do mesmo tipo. Em conjuntos de dados com um grande número de colunas, carregar várias colunas como um único vetor reduz o número de passes de dados quando você aplica transformações de dados.

    Esta classe é `ResizeFeatures` usada na ação. Os nomes de suas propriedades (neste caso, apenas uma) são usados para indicar quais colunas no DataView podem ser usadas como _entrada_ para a ação de mapeamento personalizado.

1. Criar uma classe para os recursos `Main` de comprimento fixo, após o método:

    [!code-csharp[FixedLengthFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#FixedLengthFeatures)]

    Esta classe é `ResizeFeatures` usada na ação. Os nomes de suas propriedades (neste caso, apenas uma) são usados para indicar quais colunas no DataView podem ser usadas como a _saída_ da ação de mapeamento personalizado.

    Observe que o nome `Features` da propriedade é determinado pelo modelo TensorFlow. Você não pode mudar este nome de propriedade.

1. Criar uma classe para `Main` a previsão após o método:

    [!code-csharp[Prediction](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#Prediction "Declare prediction class")]

    `MovieReviewSentimentPrediction` é a classe de previsão usada após o treinamento do modelo. `MovieReviewSentimentPrediction`tem uma `float` única`Prediction`matriz `VectorType` ( ) e um atributo.

### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a>Crie o MLContext, o dicionário de pesquisa e a ação para redimensionar os recursos

A [classe MLContext](xref:Microsoft.ML.MLContext) é um ponto de partida para todas as operações do ML.NET. Inicializar `mlContext` cria um novo ambiente do ML.NET que pode ser compartilhado entre os objetos do fluxo de trabalho de criação de modelo. Ele é semelhante, conceitualmente, a `DBContext` no Entity Framework.

1. Substitua a linha `Console.WriteLine("Hello World!")` no método `Main` pelo seguinte código para declarar e inicializar a variável mlContext:

   [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateMLContext "Create the ML Context")]

1. Crie um dicionário para codificar palavras como [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) inteiros usando o método para carregar dados de mapeamento de um arquivo, como visto na tabela a seguir:

    |Word     |Índice    |
    |---------|---------|
    |Crianças     |  362    |
    |desejar     |  181    |
    |Errado    |  355    |
    |effects  |  302    |
    |Sentimento  |  547    |

    Adicione o código abaixo para criar o mapa de procuração:

    [!code-csharp[CreateLookupMap](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateLookupMap)]

1. Adicione `Action` um para redimensionar a matriz de inteiros de palavras de comprimento variável a uma matriz inteira de tamanho fixo, com as próximas linhas de código:

   [!code-csharp[ResizeFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a>Carregar o modelo TensorFlow pré-treinado

1. Adicionar código para carregar o modelo TensorFlow:

    [!code-csharp[LoadTensorFlowModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#LoadTensorFlowModel)]

    Uma vez que o modelo é carregado, você pode extrair seu esquema de entrada e saída. Os esquemas são exibidos apenas por interesse e aprendizado. Você não precisa deste código para que a aplicação final funcione:

    [!code-csharp[GetModelSchema](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#GetModelSchema)]

    O esquema de entrada é a matriz de comprimento fixo de palavras codificadas inteiros. O esquema de saída é uma matriz flutuante de probabilidades indicando se o sentimento de uma revisão é negativo ou positivo . Esses valores somam-se a 1, pois a probabilidade de ser positivo é o complemento da probabilidade de o sentimento ser negativo.

## <a name="create-the-mlnet-pipeline"></a>Crie o ML.NET pipeline

1. Crie o pipeline e divida o texto de entrada em palavras usando [tokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transformar para quebrar o texto em palavras como a próxima linha de código:

   [!code-csharp[TokenizeIntoWords](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#TokenizeIntoWords)]

   A transformação [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) usa espaços para analisar o texto/string em palavras. Ele cria uma nova coluna e divide cada seqüência de entrada para um vetor de substrings com base no separador definido pelo usuário.

1. Mapeie as palavras em sua codificação de inteiros usando a tabela de pesquisa que você declarou acima:

    [!code-csharp[MapValue](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#MapValue)]

1. Redimensione as codificações de inteiro de comprimento variável para o comprimento fixo exigido pelo modelo:

    [!code-csharp[CustomMapping](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CustomMapping)]

1. Classifique a entrada com o modelo TensorFlow carregado:

    [!code-csharp[ScoreTensorFlowModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#ScoreTensorFlowModel)]

    A saída do modelo `Prediction/Softmax`TensorFlow é chamada . Observe que `Prediction/Softmax` o nome é determinado pelo modelo TensorFlow. Você não pode mudar este nome.

1. Criar uma nova coluna para a previsão de saída:

    [!code-csharp[SnippetCopyColumns](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#SnippetCopyColumns)]

    Você precisa copiar `Prediction/Softmax` a coluna em uma com um nome que pode `Prediction`ser usado como propriedade em uma classe C#: . O `/` personagem não é permitido em um nome de propriedade C#.

## <a name="create-the-mlnet-model-from-the-pipeline"></a>Crie o modelo ML.NET a partir do pipeline

1. Adicione o código para criar o modelo a partir do pipeline:

    [!code-csharp[SnippetCreateModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#SnippetCreateModel)]

    Um modelo ML.NET é criado a partir da cadeia de `Fit` estimadores no pipeline, chamando o método. Neste caso, não estamos adaptando nenhum dado para criar o modelo, já que o modelo TensorFlow já foi previamente treinado. Fornecemos um objeto de exibição de `Fit` dados vazio para satisfazer os requisitos do método.

## <a name="use-the-model-to-make-a-prediction"></a>Usar o modelo para fazer uma previsão

1. Adicione `PredictSentiment` o método `Main` abaixo do método:

    ```csharp
    public static void PredictSentiment(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. Adicione o seguinte código `PredictionEngine` para criar a `PredictSentiment()` primeira linha do método:

    [!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreatePredictionEngine)]

    O [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) é uma API de conveniência, que permite realizar uma previsão em uma única instância de dados. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)não é seguro para rosca. É aceitável usar em ambientes de um único fio ou protótipo. Para melhorar o desempenho e a segurança `PredictionEnginePool` dos fios nos [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) ambientes de produção, use o serviço, que cria um objeto para uso em toda a sua aplicação. Consulte este guia sobre como [usar `PredictionEnginePool` em uma API web ASP.NET.](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)

    > [!NOTE]
    > A extensão de serviço `PredictionEnginePool` está atualmente em versão prévia.

1. Adicione um comentário para testar as previsões do modelo treinado no método `Predict()` ao criar uma instância de `MovieReview`:

    [!code-csharp[CreateTestData](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateTestData)]

1. Passe os dados de `Prediction Engine` comentário do teste para `PredictSentiment()` o adicionando as próximas linhas de código no método:

    [!code-csharp[Predict](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#Predict)]

1. A função [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) faz uma previsão em uma única linha de dados:

    |Propriedade| Valor|Type|
    |-------------|-----------------------|------|
    |Previsão|[0.5459937, 0.454006255]|flutuar[]|

1. Exibir a previsão de sentimento usando o seguinte código:

    [!code-csharp[DisplayPredictions](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#DisplayPredictions)]

1. Adicionar uma `PredictSentiment` chamada ao final `Main` do método:

    [!code-csharp[CallPredictSentiment](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CallPredictSentiment)]

## <a name="results"></a>Resultados

Compile e execute seu aplicativo.

Seus resultados devem ser semelhantes aos seguintes. Durante o processamento, as mensagens são exibidas. Você pode ver avisos ou mensagens de processamento. Essas mensagens foram removidas dos resultados a seguir para ficar mais claro.

```console
Number of classes: 2
Is sentiment/review positive ? Yes
```

Parabéns! Agora você construiu com sucesso um modelo de aprendizado de máquina para classificar `TensorFlow` e prever o sentimento das mensagens reutilizando um modelo pré-treinado em ML.NET.

Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF).

Neste tutorial, você aprendeu a:
> [!div class="checklist"]
>
> * Carregue um modelo TensorFlow pré-treinado
> * Transforme o texto de comentário do site em recursos adequados para o modelo
> * Usar o modelo para fazer uma previsão
