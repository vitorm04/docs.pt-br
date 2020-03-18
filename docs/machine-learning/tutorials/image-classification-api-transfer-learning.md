---
title: 'Tutorial: Inspeção visual automatizada usando aprendizado de transferência'
description: Este tutorial ilustra como usar o aprendizado de transferência para treinar um modelo de aprendizagem profunda TensorFlow em ML.NET usando a API de detecção de imagem para classificar imagens de superfícies de concreto como rachadas ou não rachadas.
author: luisquintanilla
ms.author: luquinta
ms.date: 12/12/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 2dfa3cdab9de47b55f7a3f73f0d6e9460390700c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76920095"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a>Tutorial: Inspeção visual automatizada usando aprendizado de transferência com a API de classificação de imagem ML.NET

Aprenda a treinar um modelo de aprendizagem profunda personalizado usando o aprendizado de transferência, um modelo TensorFlow pré-treinado e a API de classificação de imagem ML.NET para classificar imagens de superfícies de concreto como rachadas ou não rachadas.

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
>
> - Compreender o problema
> - Conheça a API de classificação de imagem ML.NET
> - Entenda o modelo pré-treinado
> - Use o aprendizado de transferência para treinar um modelo personalizado de classificação de imagem TensorFlow
> - Classificar imagens com o modelo personalizado

## <a name="prerequisites"></a>Pré-requisitos

- [Visual Studio 2017 versão 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) com a carga de trabalho ".NET Core cross-platform development" instalada.

## <a name="image-classification-transfer-learning-sample-overview"></a>Visão geral da amostra de aprendizado de transferência de classificação de imagem

Esta amostra é um aplicativo de console C# .NET Core que classifica as imagens usando um modelo tensorFlow de aprendizado profundo pré-treinado. O código para este exemplo pode ser encontrado no [repositório dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) no GitHub.

## <a name="understand-the-problem"></a>Compreender o problema

A classificação de imagem é um problema de visão computacional. A classificação da imagem toma uma imagem como entrada e a categoriza em uma classe prescrita. Alguns cenários em que a classificação de imagem é útil incluem:

- Reconhecimento de rosto
- Detecção de emoções
- Diagnóstico médico
- Detecção de monumentos

Este tutorial treina um modelo personalizado de classificação de imagens para realizar inspeção visual automatizada de decks de ponte para identificar estruturas que são danificadas por rachaduras.

## <a name="mlnet-image-classification-api"></a>API de classificação de imagem ML.NET

ML.NET fornece várias maneiras de realizar a classificação de imagem. Este tutorial aplica o aprendizado de transferência usando a API de classificação de imagem. A API de classificação de imagem faz uso de [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), uma biblioteca de baixo nível que fornece vinculações C# para a API TensorFlow C++.

## <a name="what-is-transfer-learning"></a>O que é o aprendizado por transferência?

Transferir aprendizagem aplica conhecimento adquirido ao resolver um problema para outro problema relacionado.

Treinar um modelo de aprendizagem profunda do zero requer a definição de vários parâmetros, uma grande quantidade de dados de treinamento rotulados e uma grande quantidade de recursos computacionais (centenas de horas de GPU). O uso de um modelo pré-treinado, juntamente com o aprendizado de transferência, permite que você insere o processo de treinamento.

## <a name="training-process"></a>Processo de treinamento

A API de classificação de imagem inicia o processo de treinamento carregando um modelo TensorFlow pré-treinado. O processo de treinamento consiste em duas etapas:

1. Fase de gargalo
2. Fase de treinamento

![Etapas de treinamento](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a>Fase de gargalo

Durante a fase de gargalo, o conjunto de imagens de treinamento é carregado e os valores de pixel são usados como entrada, ou recursos, para as camadas congeladas do modelo pré-treinado. As camadas congeladas incluem todas as camadas da rede neural até a penúltima camada, informalmente conhecida como a camada de gargalo. Essas camadas são referidas como congeladas porque nenhum treinamento ocorrerá nessas camadas e as operações são de passagem. É nessas camadas congeladas onde os padrões de nível inferior que ajudam um modelo a diferenciar entre as diferentes classes são computados. Quanto maior o número de camadas, mais intensivo computacionalmente esta etapa é. Felizmente, como este é um cálculo único, os resultados podem ser armazenados em cache e usados em corridas posteriores ao experimentar com diferentes parâmetros.

### <a name="training-phase"></a>Fase de treinamento

Uma vez que os valores de saída da fase de gargalo são calculados, eles são usados como entrada para retreinar a camada final do modelo. Este processo é iterativo e executa para o número de vezes especificado por parâmetros do modelo. Durante cada corrida, a perda e a precisão são avaliadas. Em seguida, os ajustes apropriados são feitos para melhorar o modelo com o objetivo de minimizar a perda e maximizar a precisão. Uma vez que o treinamento é concluído, dois formatos de modelo são de saída. Uma delas é `.pb` a versão do modelo `.zip` e a outra é a ML.NET versão serializada do modelo. Ao trabalhar em ambientes suportados por ML.NET, `.zip` recomenda-se usar a versão do modelo. No entanto, em ambientes onde ML.NET não é `.pb` suportado, você tem a opção de usar a versão.

## <a name="understand-the-pretrained-model"></a>Entenda o modelo pré-treinado

O modelo pré-treinado usado neste tutorial é a variante de 101 camadas do modelo V2 da Rede Residual (ResNet). O modelo original é treinado para classificar imagens em mil categorias. O modelo toma como entrada uma imagem de tamanho 224 x 224 e produz as probabilidades de classe para cada uma das classes em que é treinado. Parte deste modelo é usado para treinar um novo modelo usando imagens personalizadas para fazer previsões entre duas classes.

## <a name="create-console-application"></a>Criar um aplicativo de console

Agora que você tem uma compreensão geral do aprendizado de transferência e da API de classificação de imagem, é hora de construir o aplicativo.

1. Crie um **aplicativo de console C# .NET Core** chamado "DeepLearning_ImageClassification_Binary".
1. Instale o pacote **1.4.0** NuGet versão **Microsoft.ML:**
    1. No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.
    1. Escolha "nuget.org" como fonte do Pacote.
    1. Selecione a guia **Procurar**.
    1. Verifique a **caixa de seleção Incluir pré-lançamento.**
    1. Procure por **Microsoft.ML**.
    1. Selecione o botão **Instalar**.
    1. Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.
    1. Repita essas etapas para os pacotes **Microsoft.ML.Vision** **1.4.0**, **SciSharp.TensorFlow.Redist** **versão 1.15.0**e **Microsoft.ML.ImageAnalytics** versão **1.4.0** NuGet.

### <a name="prepare-and-understand-the-data"></a>Preparar e compreender os dados

> [!NOTE]
> Os conjuntos de dados para este tutorial são de Maguire, Marc; Dorafshan, Sattar; e Thomas, Robert J., "SDNET2018: Um conjunto de dados de imagem de crack concreto para aplicações de aprendizagem de máquina" (2018). Navegue por todos os conjuntos de dados. Papel 48. https://digitalcommons.usu.edu/all_datasets/48

SDNET2018 é um conjunto de dados de imagem que contém anotações para estruturas de concreto rachadas e não rachadas (decks de ponte, paredes e pavimento).

![Amostras do deck da ponte do conjunto de dados SDNET2018](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

Os dados estão organizados em três subdiretórios:

- D contém imagens do convés da ponte
- P contém imagens de pavimento
- W contém imagens de parede

Cada um desses subdiretórios contém dois subdiretórios prefixados adicionais:

- C é o prefixo usado para superfícies rachadas
- U é o prefixo usado para superfícies não rachadas

Neste tutorial, apenas imagens de deck de ponte são usadas.

1. Baixe o [conjunto de dados](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) e desfaça o zíper.
1. Crie um diretório chamado "assets" em seu projeto para salvar seus arquivos de conjunto de dados.
1. Copie os subdiretórios *de CD* e *UD* do diretório recentemente descompactado para o diretório *de ativos.*

### <a name="create-input-and-output-classes"></a>Criar classes de entrada e saída

1. Abra o *arquivo Program.cs* e `using` substitua as instruções existentes na parte superior do arquivo pelo seguinte:

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. Abaixo `Program` da classe em *Program.cs,* crie uma classe chamada `ImageData`. Esta classe é usada para representar os dados inicialmente carregados.

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L137-L142)]

    `ImageData`contém as seguintes propriedades:

    - `ImagePath`é o caminho totalmente qualificado onde a imagem é armazenada.
    - `Label`é a categoria a que a imagem pertence. Este é o valor para prever.

1. Crie classes para seus dados de entrada e saída

    1. Abaixo `ImageData` da classe, defina o esquema de seus `ModelInput`dados de entrada em uma nova classe chamada .

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L144-L153)]

        `ModelInput`contém as seguintes propriedades:

        - `Image`é `byte[]` a representação da imagem. O modelo espera que os dados de imagem sejam desse tipo para treinamento.
        - `LabelAsKey`é a representação numérica `Label`do .
        - `ImagePath`é o caminho totalmente qualificado onde a imagem é armazenada.
        - `Label`é a categoria a que a imagem pertence. Este é o valor para prever.

        Somente `Image` `LabelAsKey` e são usados para treinar o modelo e fazer previsões. As `ImagePath` `Label` propriedades e propriedades são mantidas por conveniência para acessar o nome e categoria do arquivo de imagem original.

    1. Em seguida, `ModelInput` abaixo da classe, defina o esquema de `ModelOutput`seus dados de saída em uma nova classe chamada .

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L155-L162)]

        `ModelOutput`contém as seguintes propriedades:

        - `ImagePath`é o caminho totalmente qualificado onde a imagem é armazenada.
        - `Label`é a categoria original a que a imagem pertence. Este é o valor para prever.
        - `PredictedLabel`é o valor previsto pelo modelo.

        Semelhante `ModelInput`a , `PredictedLabel` apenas o é necessário para fazer previsões, uma vez que contém a previsão feita pelo modelo. As `ImagePath` `Label` propriedades e propriedades são retidas para conveniência para acessar o nome e categoria do arquivo de imagem original.

### <a name="create-workspace-directory"></a>Criar diretório de espaço de trabalho

Quando os dados de treinamento e validação não mudam com frequência, é uma boa prática armazenar os valores de gargalo computados para outras corridas.

1. Em seu projeto, crie um novo diretório chamado *workspace* `.pb` para armazenar os valores de gargalo computados e a versão do modelo.

### <a name="define-paths-and-initialize-variables"></a>Defina caminhos e inicialize variáveis

1. Dentro `Main` do método, defina a localização de `.pb` seus ativos, valores de gargalo computados e versão do modelo.

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L17)]

1. Inicialize `mlContext` a variável com uma nova instância do [MLContext](xref:Microsoft.ML.MLContext).

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L19)]

    A classe [MLContext](xref:Microsoft.ML.MLContext) é um ponto de partida para todas as operações ML.NET, e a inicialização do mlContext cria um novo ambiente ML.NET que pode ser compartilhado entre os objetos do fluxo de trabalho de criação de modelos. Ele é semelhante, conceitualmente, a `DBContext` no Entity Framework.

## <a name="load-the-data"></a>Carregar os dados

### <a name="create-data-loading-utility-method"></a>Criar método utilitário de carregamento de dados

As imagens são armazenadas em dois subdiretórios. Antes de carregar os dados, ele precisa `ImageData` ser formatado em uma lista de objetos. Para isso, crie `LoadImagesFromDirectory` o método `Main` abaixo do método.

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. Dentro `LoadImagesDirectory` do adicionar o seguinte código para obter todos os caminhos de arquivo dos subdiretórios:

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L104-L105)]

1. Em seguida, iterar através de `foreach` cada um dos arquivos usando uma declaração.

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. Dentro `foreach` da declaração, verifique se as extensões de arquivo estão suportadas. A API de classificação de imagem suporta formatos JPEG e PNG.

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L109-L110)]

1. Então, pegue a etiqueta para o arquivo. Se `useFolderNameAsLabel` o parâmetro estiver `true`definido como , então o diretório pai onde o arquivo é salvo é usado como o rótulo. Caso contrário, espera que o rótulo seja um prefixo do nome do arquivo ou do próprio nome do arquivo.

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L112-L126)]

1. Finalmente, crie uma `ModelInput`nova instância de .

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L128-L132)]

### <a name="prepare-the-data"></a>Preparar os dados

1. De volta `Main` ao método, use o `LoadFromDirectory` método utilitário para obter a lista de imagens usadas para treinamento.

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L21)]

1. Em seguida, carregue [`IDataView`](xref:Microsoft.ML.IDataView) as [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) imagens em um uso do método.

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L23)]

1. Os dados são carregados na ordem em que foram lidos dos diretórios. Para equilibrar os dados, embaralhe-os usando o [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) método.

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L25)]

1. Os modelos de aprendizado de máquina esperam que a entrada seja em formato numérico. Portanto, alguns pré-processamentos precisam ser feitos nos dados antes do treinamento. Crie [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) uma forma [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) de `LoadRawImageBytes` transformação. A `MapValueToKey` transformação pega o `Label` valor categórico na coluna, `KeyType` converte-a em um `LabelAsKey`valor numérico e armazena-a em uma nova coluna chamada . O `LoadImages` leva os `ImagePath` valores da `imageFolder` coluna junto com o parâmetro para carregar imagens para treinamento.

    [!code-csharp [PreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L27-L33)]

1. Use [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) o método para aplicar `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) os [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) dados ao método [`IDataView`](xref:Microsoft.ML.IDataView) seguido, que retorna um contendo os dados pré-processados.

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. Para treinar um modelo, é importante ter um conjunto de dados de treinamento, bem como um conjunto de dados de validação. O modelo é treinado no conjunto de treinamento. O quão bem ele faz previsões sobre dados invisíveis é medido pelo desempenho em relação ao conjunto de validação. Com base nos resultados desse desempenho, o modelo faz ajustes no que aprendeu em um esforço para melhorar. O conjunto de validação pode vir da divisão do conjunto de dados original ou de outra fonte que já foi reservada para este fim. Neste caso, o conjunto de dados pré-processado é dividido em conjuntos de treinamento, validação e teste.

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    A amostra de código acima realiza duas divisões. Primeiro, os dados pré-processados são divididos e 70% são usados para treinamento, enquanto os 30% restantes são usados para validação. Em seguida, o conjunto de validação de 30% é dividido em conjuntos de validação e teste onde 90% é usado para validação e 10% é usado para testes.

    Uma maneira de pensar sobre o propósito dessas partições de dados é fazer um exame. Ao estudar para um exame, você revisa suas anotações, livros ou outros recursos para obter uma compreensão sobre os conceitos que estão no exame. É para isso que é o trem. Então, você pode fazer um exame simulado para validar seu conhecimento. É aqui que o conjunto de validação é útil. Você quer verificar se você tem uma boa compreensão dos conceitos antes de fazer o exame real. Com base nesses resultados, você toma nota do que você errou ou não entendeu bem e incorpora suas mudanças à medida que você revisa para o exame real. Finalmente, você faz o exame. É para isso que o conjunto de testes é usado. Você nunca viu as questões que estão no exame e agora usa o que aprendeu com o treinamento e validação para aplicar seus conhecimentos à tarefa em questão.

1. Atribuir as partições seus respectivos valores para os dados de trem, validação e teste.

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a>Defina o pipeline de treinamento

O treinamento de modelo consiste em alguns passos. Primeiro, a API de classificação de imagem é usada para treinar o modelo. Em seguida, os rótulos `PredictedLabel` codificados na coluna são convertidos `MapKeyToValue` de volta ao seu valor categórico original usando a transformação.

1. Crie uma nova variável para armazenar um conjunto `ImageClassificationTrainer`de parâmetros necessários e opcionais para um .

    [!code-csharp [ClassifierOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L57)]

    Um `ImageClassificationTrainer` toma vários parâmetros opcionais:

    - `FeatureColumnName`é a coluna que é usada como entrada para o modelo.
    - `LabelColumnName`é a coluna para o valor prever.
    - `ValidationSet`é [`IDataView`](xref:Microsoft.ML.IDataView) a contém os dados de validação.
    - `Arch`define qual das arquiteturas de modelo pré-treinadas usar. Este tutorial usa a variante de 101 camadas do modelo ResNetv2.
    - `MetricsCallback`liga uma função para acompanhar o progresso durante o treinamento.
    - `TestOnTrainSet`diz ao modelo para medir o desempenho em relação ao conjunto de treinamento quando não há um conjunto de validação.
    - `ReuseTrainSetBottleneckCachedValues`informa o modelo se deve usar os valores armazenados em cache a partir da fase de gargalo em corridas subseqüentes. A fase de gargalo é um cálculo de passagem única que é computacionalmente intensivo na primeira vez que é realizado. Se os dados de treinamento não mudarem e você quiser experimentar usando um número diferente de épocas ou tamanho de lote, usar os valores armazenados reduz significativamente o tempo necessário para treinar um modelo.
    - `ReuseValidationSetBottleneckCachedValues`é semelhante `ReuseTrainSetBottleneckCachedValues` apenas que, neste caso, é para o conjunto de dados de validação.
    - `WorkspacePath`define o diretório onde armazenar os valores `.pb` de gargalo computados e a versão do modelo.

1. Defina [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) o pipeline de treinamento `mapLabelEstimator` que `ImageClassificationTrainer`consiste tanto no e no .

    [!code-csharp [TrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L59-L60)]

1. Use [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) o método para treinar seu modelo.

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

## <a name="use-the-model"></a>Usar o modelo

Agora que você treinou seu modelo, é hora de usá-lo para classificar imagens.

Abaixo `Main` do método, crie um `OutputPrediction` novo método de utilidade chamado para exibir informações de previsão no console.

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L96-L100)]

### <a name="classify-a-single-image"></a>Classifique uma única imagem

1. Adicione um novo `ClassifySingleImage` método `Main` chamado abaixo do método para fazer e produzir uma única previsão de imagem.

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. Crie [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) um `ClassifySingleImage` dentro do método. A [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) é uma API de conveniência, que permite que você passe e, em seguida, execute uma previsão em uma única instância de dados.

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. Para acessar `ModelInput` uma única `data` [`IDataView`](xref:Microsoft.ML.IDataView) instância, [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) converta-a em um usando o [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) método e, em seguida, obtenha a primeira observação.

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. Use [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) o método para classificar a imagem.

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77)]

1. Saída a previsão para `OutputPrediction` o console com o método.

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L79-L80)]

1. Dentro `Main` do método, ligue `ClassifySingleImage` usando o conjunto de testes de imagens.

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

### <a name="classify-multiple-images"></a>Classificar várias imagens

1. Adicione um novo `ClassifyImages` método `ClassifySingleImage` chamado abaixo do método para fazer e produzir várias previsões de imagem.

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. Crie [`IDataView`](xref:Microsoft.ML.IDataView) uma contendo as previsões usando o [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) método. Adicione o seguinte código dentro do método `ClassifyImages`.

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. A fim de iterar sobre `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) as [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) previsões, converta-o em um usando o [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) método e, em seguida, obter as primeiras 10 observações.

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87)]

1. Iterar e produzir os rótulos originais e previstos para as previsões.

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L89-L93)]

1. Finalmente, dentro `Main` do `ClassifyImages` método, ligue usando o conjunto de testes de imagens.

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L66)]

## <a name="run-the-application"></a>Executar o aplicativo

Execute seu aplicativo de console. A saída deve ser semelhante à abaixo. Você poderá ver avisos ou mensagens de processamento, mas essas mensagens foram removidas dos resultados a seguir para maior clareza. Para a brevidade, a saída foi condensada.

**Fase de gargalo**

Nenhum valor é impresso para o nome da imagem `byte[]` porque as imagens são carregadas como uma, portanto, não há nome de imagem para exibir.

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2
```

**Fase de treinamento**

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

**Classificar a saída de imagens**

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

Após a inspeção da imagem *7001-220.jpg,* você pode ver que ela de fato não está rachada.

![Imagem do conjunto de dados SDNET2018 usada para previsão](./media/image-classification-api-transfer-learning/predictedimage.jpg)

Parabéns! Agora você construiu com sucesso um modelo de aprendizagem profunda para classificar imagens.

### <a name="improve-the-model"></a>Melhorar o modelo

Se você não está satisfeito com os resultados do seu modelo, você pode tentar melhorar seu desempenho, tentando algumas das seguintes abordagens:

- **Mais Dados**: Quanto mais exemplos um modelo aprende, melhor ele se sai. Baixe o [conjunto de dados SDNET2018 completo](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) e use-o para treinar.
- **Aumentar os dados**: Uma técnica comum para adicionar variedade aos dados é aumentar os dados tirando uma imagem e aplicando diferentes transformações (girar, virar, mudar, cortar). Isso adiciona exemplos mais variados para o modelo aprender.
- **Trem por mais tempo**: Quanto mais você treinar, mais sintonizado será o modelo. Aumentar o número de épocas pode melhorar o desempenho do seu modelo.
- **Experimente com os hiperparâmetros**: Além dos parâmetros utilizados neste tutorial, outros parâmetros podem ser ajustados para potencialmente melhorar o desempenho. Alterar a taxa de aprendizado, que determina a magnitude das atualizações feitas no modelo após cada época pode melhorar o desempenho.
- **Use uma arquitetura de modelo diferente**: Dependendo de como seus dados se parecem, o modelo que pode melhor aprender suas características pode diferir. Se você não está satisfeito com o desempenho do seu modelo, tente mudar a arquitetura.

### <a name="additional-resources"></a>Recursos adicionais

- [Deep Learning vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como construir um modelo de aprendizagem profunda personalizado usando o aprendizado de transferência, um modelo de classificação de imagem pré-treinado TensorFlow e a API de classificação de imagem ML.NET para classificar imagens de superfícies de concreto como rachadas ou não rachadas.

Avance para o próximo tutorial para saber mais.

> [!div class="nextstepaction"]
> [Detecção de objetos](object-detection-onnx.md)
