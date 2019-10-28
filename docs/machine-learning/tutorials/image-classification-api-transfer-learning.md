---
title: 'Tutorial: inspeção visual automatizada usando o aprendizado de transferência'
description: Este tutorial ilustra como usar o aprendizado de transferência para treinar um modelo de aprendizado profundo do TensorFlow no ML.NET usando a API de detecção de imagem para classificar imagens de superfícies concretas como rachadas ou não rachadas.
author: luisquintanilla
ms.author: luquinta
ms.date: 10/25/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: b8aec80134188811eb80ad1394e5a64d65a3c6f0
ms.sourcegitcommit: 9b2ef64c4fc10a4a10f28a223d60d17d7d249ee8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/26/2019
ms.locfileid: "72961983"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a>Tutorial: inspeção visual automatizada usando o aprendizado de transferência com a API de classificação de imagem ML.NET

Saiba como treinar um modelo de aprendizado profundo personalizado usando o aprendizado de transferência, um modelo TensorFlow pretreinado e a API de classificação de imagem ML.NET para classificar imagens de superfícies concretas como rachadas ou sem cracking.

> [!NOTE]
> Este tutorial usa uma versão de visualização da API de classificação de imagem ML.NET.

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
>
> - Compreender o problema
> - Saiba mais sobre a API de classificação de imagem ML.NET
> - Entender o modelo pretreinado
> - Usar o aprendizado de transferência para treinar um modelo de classificação de imagem TensorFlow personalizado
> - Classificar imagens com o modelo personalizado

## <a name="prerequisites"></a>Prerequisites

- [Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.

## <a name="image-classification-transfer-learning-sample-overview"></a>Visão geral do exemplo de aprendizado de transferência de classificação de imagem

Este exemplo é um C# aplicativo de console .NET Core que classifica imagens usando um modelo de TensorFlow de aprendizado profundo pretreinado. O código para este exemplo pode ser encontrado no [repositório dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) no GitHub.

## <a name="understand-the-problem"></a>Compreender o problema

A classificação de imagem é um problema de pesquisa Visual computacional. A classificação de imagem usa uma imagem como entrada e a categoriza em uma classe prescrita. Alguns cenários em que a classificação de imagem é útil incluem:

- Reconhecimento de rosto
- Detecção de emoções
- Diagnóstico médico
- Detecção de ponto de referência

Este tutorial treina um modelo de classificação de imagem personalizada para executar a inspeção visual automatizada de decks de ponte para identificar estruturas que estão danificadas por rachaduras.

## <a name="mlnet-image-classification-api"></a>API de classificação de imagem ML.NET

O ML.NET fornece várias maneiras de executar a classificação de imagem. Este tutorial aplica-se ao aprendizado de transferência usando a API de classificação de imagem. A API de classificação de imagem usa [TensorFlow.net](https://github.com/SciSharp/TensorFlow.NET), uma biblioteca de nível baixo que fornece C# associações para a API TensorFlow C++ .

## <a name="what-is-transfer-learning"></a>O que é o aprendizado por transferência?

O aprendizado de transferência aplica o conhecimento obtido da solução de um problema para outro problema relacionado.

Treinar um modelo de aprendizado profundo do zero exige a definição de vários parâmetros, uma grande quantidade de dados de treinamento rotulados e uma grande quantidade de recursos de computação (centenas de horas de GPU). Usar um modelo pretreinado junto com o aprendizado de transferência permite que você Modele o processo de treinamento. 

## <a name="training-process"></a>Processo de treinamento

A API de classificação de imagem inicia o processo de treinamento carregando um modelo de TensorFlow pré-treinado. O processo de treinamento consiste em duas etapas:

1. Fase de afunilamento
2. Fase de treinamento

![Etapas de treinamento](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a>Fase de afunilamento

Durante a fase de afunilamento, o conjunto de imagens de treinamento é carregado e os valores de pixel são usados como entrada, ou recursos, para as camadas congeladas do modelo pretreinado. As camadas congeladas incluem todas as camadas na rede neural até a camada penúltima, informalmente conhecida como a camada de afunilamento. Essas camadas são referidas como congeladas porque nenhum treinamento ocorrerá nessas camadas e as operações são passagem. Elas estão nessas camadas congeladas onde os padrões de nível inferior que ajudam um modelo diferenciar entre as diferentes classes são computadas. Quanto maior o número de camadas, mais intensivamente essa etapa é computada. Felizmente, como esse é um cálculo único, os resultados podem ser armazenados em cache e usados em execuções posteriores ao experimentar parâmetros diferentes.

### <a name="training-phase"></a>Fase de treinamento

Depois que os valores de saída da fase de afunilamento são computados, eles são usados como entrada para treinar novamente a camada final do modelo. Esse processo é iterativo e é executado para o número de vezes especificado por parâmetros de modelo. Durante cada execução, a perda e a precisão são avaliadas. Em seguida, os ajustes apropriados são feitos para melhorar o modelo com o objetivo de minimizar a perda e maximizar a precisão. Quando o treinamento for concluído, dois formatos de modelo serão gerados. Um deles é a versão `.pb` do modelo e o outro é a versão serializada `.zip` ML.NET do modelo. Ao trabalhar em ambientes com suporte do ML.NET, é recomendável usar a versão `.zip` do modelo. No entanto, em ambientes em que não há suporte para ML.NET, você tem a opção de usar a versão `.pb`.

## <a name="understand-the-pretrained-model"></a>Entender o modelo pretreinado

O modelo pretreinado usado neste tutorial é a variante de camada 101 do modelo de rede residual (ResNet) v2. O modelo original é treinado para classificar imagens em milhares de categorias. O modelo usa como entrada uma imagem de tamanho 224 x 224 e gera as probabilidades de classe para cada uma das classes em que é treinado. Parte desse modelo é usada para treinar um novo modelo usando imagens personalizadas para fazer previsões entre duas classes. 

## <a name="create-console-application"></a>Criar aplicativo de console

Agora que você tem uma compreensão geral do aprendizado de transferência e da API de classificação de imagem, é hora de criar o aplicativo.

1. Crie um  **C# aplicativo de console do .NET Core** chamado "DeepLearning_ImageClassification_Binary".
1. Instale o pacote NuGet **Microsoft.ml 1.4.0-Preview2** :
    1. No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.
    1. Escolha "nuget.org" como a origem do pacote.
    1. Selecione a guia **Procurar**.
    1. Marque a caixa de seleção **incluir pré-lançamento** .
    1. Procure **Microsoft.ml**.
    1. Selecione o botão **Instalar**.
    1. Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.
    1. Repita essas etapas para **Microsoft. ml. DNN 0.16.0-Preview2** e **Microsoft. ml. ImageAnalytics 1.4.0-Preview2**.

### <a name="prepare-and-understand-the-data"></a>Preparar e compreender os dados

> [!NOTE]
> Os conjuntos de valores para este tutorial são de Maguire, Marc; Dorafshan, Sattar; e Thomas, Robert J., "SDNET2018: um conjunto de imagem de quebra concreta para aplicativos de Machine Learning" (2018). Procurar todos os conjuntos de valores. Papel 48. https://digitalcommons.usu.edu/all_datasets/48

SDNET2018 é um conjunto de uma imagem que contém anotações para estruturas concretas rachadas e não rachadas (baralhos de ponte, paredes e Pavement). 

![Amostras de baralho da ponte do conjunto de SDNET2018](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

Os dados são organizados em três subdiretórios:

- D contém imagens do deck de ponte
- P contém imagens Pavement
- W contém imagens de parede

Cada um desses subdiretórios contém dois subdiretórios prefixais adicionais:

- C é o prefixo usado para superfícies rachadas
- U é o prefixo usado para superfícies não decifradas

Neste tutorial, somente imagens de baralho de ponte são usadas.

1. Baixe o [conjunto](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) de e descompacte.
1. Crie um diretório chamado "ativos" em seu projeto para salvar os arquivos do conjunto de recursos.
1. Copie os subdiretórios *CD* e *UD* do diretório recentemente descompactado para o diretório de *ativos* .

### <a name="create-input-and-output-classes"></a>Criar classes de entrada e saída

1. Abra o arquivo *Program.cs* e substitua as instruções de `using` existentes na parte superior do arquivo pelo seguinte:

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. Abaixo da classe `Program` em *Program.cs*, crie uma classe chamada `ImageData`. Essa classe é usada para representar os dados carregados inicialmente. 

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L135-L140)]

    `ImageData` contém as seguintes propriedades:

    - `ImagePath` é o caminho totalmente qualificado em que a imagem é armazenada.
    - `Label` é a categoria à qual a imagem pertence. Esse é o valor a prever.

1. Criar classes para os dados de entrada e saída

    1. Abaixo da classe `ImageData`, defina o esquema dos dados de entrada em uma nova classe chamada `ModelInput`.

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L142-L151)]

        `ModelInput` contém as seguintes propriedades:

        - `ImagePath` é o caminho totalmente qualificado em que a imagem é armazenada. 
        - `Label` é a categoria à qual a imagem pertence. Esse é o valor a prever.
        - `Image` é a representação `byte[]` da imagem. O modelo espera que os dados de imagem sejam desse tipo para treinamento.
        - `LabelAsKey` é a representação numérica do `Label`. 

        Somente `Image` e `LabelAsKey` são usados para treinar o modelo e fazer previsões. As propriedades `ImagePath` e `Label` são mantidas por conveniência para acessar o nome e a categoria do arquivo de imagem original.

    1. Em seguida, abaixo da classe `ModelInput`, defina o esquema dos dados de saída em uma nova classe chamada `ModelOutput`. 

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L153-L160)]

        `ModelOutput` contém as seguintes propriedades:

        - `ImagePath` é o caminho totalmente qualificado em que a imagem é armazenada.
        - `Label` é a categoria original à qual a imagem pertence. Esse é o valor a prever. 
        - `PredictedLabel` é o valor previsto pelo modelo.

        Semelhante à `ModelInput`, somente o `PredictedLabel` é necessário para fazer previsões, pois contém a previsão feita pelo modelo. As propriedades `ImagePath` e `Label` são mantidas por conveniência para acessar o nome e a categoria do arquivo de imagem original.

### <a name="define-paths-and-initialize-variables"></a>Definir caminhos e inicializar variáveis

1. Dentro do método `Main`, defina o local de seus ativos.

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L16)]

1. Em seguida, inicialize a variável `mlContext` com uma nova instância de [MLContext](xref:Microsoft.ML.MLContext).

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L18)]

A classe [MLContext](xref:Microsoft.ML.MLContext) é um ponto de partida para todas as operações de ml.net, e a inicialização de MLContext cria um novo ambiente ml.NET que pode ser compartilhado entre os objetos de fluxo de trabalho de criação de modelo. Ele é semelhante, conceitualmente, a `DBContext` no Entity Framework.

## <a name="load-the-data"></a>Carregar os dados

### <a name="create-data-loading-utility-method"></a>Criar método de utilitário de carregamento de dados

As imagens são armazenadas em dois subdiretórios. Antes de carregar os dados, ele precisa ser formatado em uma lista de objetos de `ImageData`. Para fazer isso, crie o método `LoadImagesFromDirectory` abaixo do método `Main`.

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. Dentro do `LoadImagesDirectory` adicione o seguinte código para obter todos os caminhos de arquivo dos subdiretórios:

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L102-L103)]

1. Em seguida, Itere em cada um dos arquivos usando uma instrução `foreach`.

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. Dentro da instrução `foreach`, verifique se as extensões de arquivo têm suporte. A API de classificação de imagem dá suporte aos formatos JPEG e PNG.

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L107-L108)]

1. Em seguida, obtenha o rótulo para o arquivo. Se o parâmetro `useFolderNameAsLabel` for definido como `true`, o diretório pai onde o arquivo é salvo será usado como o rótulo. Caso contrário, ele espera que o rótulo seja um prefixo do nome do arquivo ou o próprio nome do arquivo.

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L110-L124)]

1. Por fim, crie uma nova instância do `ModelInput`.

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L126-L130)]

### <a name="prepare-the-data"></a>Preparar os dados

1. De volta ao método `Main`, use o método utilitário `LoadFromDirectory` para obter a lista de imagens usadas para treinamento.

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L20)]

1. Em seguida, carregue as imagens em um [`IDataView`](xref:Microsoft.ML.IDataView) usando o método [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) .

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L22)]    

1. Os dados são carregados na ordem em que foram lidos dos diretórios. Para balancear os dados, use a ordem aleatória usando o método [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) .

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L24)]

1. Os modelos de aprendizado de máquina esperam que a entrada esteja em formato numérico. Portanto, algum pré-processamento precisa ser feito nos dados antes do treinamento. Crie uma [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) composta das transformações de [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) e [`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) . A transformação `MapValueToKey` usa o valor categórico na coluna `Label`, converte-o em um valor de `KeyType` numérico e o armazena em uma nova coluna chamada `LabelAsKey`. O `LoadImages` usa os valores da coluna `ImagePath` junto com o parâmetro `imageFolder` para carregar imagens para treinamento. Definir a `useImageType` como `false` converte as imagens em uma `byte[]`. 

    [!code-csharp [DefinePreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L26-L33)]

1. Use o método [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) para aplicar os dados ao `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) seguido pelo método [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) , que retorna um [`IDataView`](xref:Microsoft.ML.IDataView) contendo os dados previamente processados.

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. Para treinar um modelo, é importante ter um conjunto de um de treinamento, bem como um conjunto de uma validação. O modelo é treinado no conjunto de treinamento. O quão bem ele faz previsões sobre dados não vistos é medido pelo desempenho em relação ao conjunto de validação. Com base nos resultados desse desempenho, o modelo faz ajustes no que ele aprendeu em um esforço para melhorar. O conjunto de validação pode vir de uma divisão do conjunto de seus conjuntos de seus originais ou de outra fonte que já tenha sido reservada para essa finalidade. Nesse caso, o conjunto de valores previamente processados é dividido em conjuntos de treinamento, validação e teste.

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    O exemplo de código acima executa duas divisões. Primeiro, os dados previamente processados são divididos e 70% é usado para treinamento enquanto os 30% restantes são usados para validação. Em seguida, o conjunto de validação de 30% é mais dividido em conjuntos de validação e de teste em que 90% é usado para validação e 10% é usado para teste. 

    Uma maneira de pensar sobre a finalidade dessas partições de dados é fazer um exame. Ao estudar um exame, você examina suas notas, livros ou outros recursos para entender os conceitos que estão no exame. É para isso que se trata o conjunto de treinamento. Em seguida, você pode fazer um exame fictício para validar seu conhecimento. É aí que o conjunto de validação é útil. Você quer verificar se tem uma boa noção dos conceitos antes de pegar o exame real. Com base nesses resultados, anote o que você obteve errado ou não entendeu bem e incorpore suas alterações ao examinar o exame real. Por fim, você assume o exame. É para isso que o conjunto de testes é usado. Você nunca viu as perguntas que estão no exame e agora usa o que aprendeu do treinamento e da validação para aplicar seu conhecimento à tarefa em questão. 

1. Atribua as partições seus respectivos valores para os dados de treinamento, validação e teste.

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a>Definir o pipeline de treinamento

O treinamento de modelo consiste em algumas etapas. Primeiro, a API de classificação de imagem é usada para treinar o modelo. Em seguida, os rótulos codificados na coluna `PredictedLabel` são convertidos de volta para seu valor categórico original usando a transformação `MapKeyToValue`. 

1. Defina o pipeline de [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) de treinamento que consiste nas transformações `mapLabelEstimator` e `ImageClassification`.

    [!code-csharp [DefineTrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L58)]    

    O estimador de `ImageClassification` usa vários parâmetros:

    - `featuresColumnName` é a coluna usada como entrada para o modelo.
    - `labelColumnName` é a coluna do valor a prever.
    - `arch` define qual das arquiteturas de modelo pretreinados usar. Este tutorial usa a variante de camada 101 do modelo ResNetv2.
    - `epoch` especifica o número máximo de iterações em todo o conjunto de todos os processos de treinamento. Quanto maior o número, mais longo o modelo Treina e potencialmente o melhor modelo produzido.
    - `batchSize` é o número de amostras a ser usado por vez para treinamento. Durante uma época, vários lotes iguais ao batchSize são usados para treinar e atualizar o modelo. Quanto menor o número, menor a memória necessária quando cada lote é processado.
    - `testOnTrainSet` diz ao modelo para medir o desempenho em relação ao conjunto de treinamento quando nenhum conjunto de validação está presente.
    - `metricsCallback` associa uma função para acompanhar o progresso durante o treinamento.
    - `validationSet` é a [`IDataView`](xref:Microsoft.ML.IDataView) que contém os dados de validação.
    - `reuseTrainSetBottleneckCachedValues` informa ao modelo se os valores armazenados em cache devem ser usados da fase de afunilamento nas execuções subsequentes. A fase de afunilamento é uma computação de passagem única que é computacionalmente intensiva na primeira vez em que é executada. Se os dados de treinamento não forem alterados e você quiser experimentar o uso de um número diferente de épocas ou do tamanho do lote, usar os valores armazenados em cache reduz significativamente o tempo necessário para treinar um modelo.
    - `reuseValidationSetBottleneckCachedValues` é semelhante a `reuseTrainSetBottleneckCachedValues` apenas que, nesse caso, é para o conjunto de conjuntos de validação.
    - `disableEarlyStopping` diz ao estimador ImageClassification se deve empregar uma estratégia de interrupção inicial. Como o modelo pesquisa os valores ideais que o ajudarão a fazer previsões precisas durante o treinamento, o desempenho pode aumentar ou diminuir. Por fim, se o modelo atingir a última época, pode ser o caso de que os padrões aprendidos do treinamento sejam subótimos. A parada inicial dos monitores de treinamento para esses Descartes no desempenho e interrompe o processo de treinamento em um esforço para preservar uma versão ideal do modelo.

1. Use o método [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) para treinar seu modelo.

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L60)]

## <a name="use-the-model"></a>Usar o modelo

Agora que você treinou seu modelo, é hora de usá-lo para classificar imagens.

Abaixo do método `Main`, crie um novo método utilitário chamado `OutputPrediction` para exibir informações de previsão no console do.

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L94-L98)]

### <a name="classify-a-single-image"></a>Classificar uma única imagem

1. Adicione um novo método chamado `ClassifySingleImage` abaixo do método `Main` para fazer e gerar uma previsão de imagem única.

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. Crie um [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) dentro do método `ClassifySingleImage`. A [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) é uma API de conveniência, que permite que você passe e execute uma previsão em uma única instância de dados.

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L71)]    

1. Para acessar uma única instância de `ModelInput`, converta o [`IDataView`](xref:Microsoft.ML.IDataView) de `data` em um [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) usando o método [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) e, em seguida, obtenha a primeira observação. 

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. Use o método [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) para classificar a imagem.

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. Gere a previsão para o console com o método `OutputPrediction`.

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77-L78)]

1. Dentro do método `Main`, chame `ClassifySingleImage` usando o conjunto de teste de imagens.

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

### <a name="classify-multiple-images"></a>Classificar várias imagens

1. Adicione um novo método chamado `ClassifyImages` abaixo do método `ClassifySingleImage` para fazer e gerar várias previsões de imagem.

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. Crie um [`IDataView`](xref:Microsoft.ML.IDataView) que contenha as previsões usando o método [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) . Adicione o seguinte código dentro do método `ClassifyImages`.

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L83)]

1. Para iterar as previsões, converta o `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) em um [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) usando o método [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) e, em seguida, obtenha as 10 primeiras observações.

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. Itere e gere os rótulos original e previsto para as previsões.

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87-L91)]

1. Por fim, dentro do método `Main`, chame `ClassifyImages` usando o conjunto de teste de imagens.

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

## <a name="run-the-application"></a>Executar o aplicativo

Execute o aplicativo de console. A saída deve ser semelhante à mostrada abaixo. Você poderá ver avisos ou mensagens de processamento, mas essas mensagens foram removidas dos resultados a seguir para maior clareza. Para resumir, a saída foi condensada.

**Fase de afunilamento**

Nenhum valor é impresso para o nome da imagem porque as imagens são carregadas como um `byte[]`, portanto, não há nenhum nome de imagem a ser exibido.

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279, Image Name:
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280, Image Name:
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1, Image Name:
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2, Image Name:
```

**Fase de treinamento**

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

**Classificar saída de imagens**

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

Após a inspeção da imagem *7001 -220. jpg* , você pode ver que, na verdade, ela não está quebrada. 

![Imagem do conjunto de SDNET2018 usado para previsão](./media/image-classification-api-transfer-learning/predictedimage.jpg)

Parabéns! Agora você criou com êxito um modelo de aprendizado profundo para classificar imagens.

### <a name="improve-the-model"></a>Melhorar o modelo

Se você não estiver satisfeito com os resultados do modelo, poderá tentar melhorar seu desempenho experimentando algumas das seguintes abordagens:

- **Mais dados**: quanto mais exemplos um modelo aprende, melhor é o desempenho. Baixe o [conjunto de SDNET2018](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) completo e use-o para treinar. 
- **Aumentar os dados**: uma técnica comum para adicionar uma variedade aos dados é aumentar os dados, tirando uma imagem e aplicando transformações diferentes (girar, virar, deslocar, cortar). Isso adiciona exemplos mais variados para o modelo a ser aprendedo. 
- **Treine por mais tempo**: quanto mais longo for o treinamento, mais ajustado será o modelo. Aumentar o número de épocas pode melhorar o desempenho do seu modelo.
- **Experimente os hiperparâmetros**: além dos parâmetros usados neste tutorial, outros parâmetros podem ser ajustados para melhorar potencialmente o desempenho. Alterar a taxa de aprendizado, que determina a magnitude das atualizações feitas ao modelo depois que cada época pode melhorar o desempenho.
- **Use uma arquitetura de modelo diferente**: dependendo de como seus dados se parecem, o modelo que pode aprender melhor seus recursos pode ser diferente. Se você não estiver satisfeito com o desempenho do seu modelo, tente alterar a arquitetura.

### <a name="additional-resources"></a>Recursos adicionais

- [Aprendizado profundo versus Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu a criar um modelo de aprendizado profundo personalizado usando o aprendizado de transferência, um modelo TensorFlow de classificação de imagem previamente treinado e a API de classificação de imagem ML.NET para classificar imagens de superfícies concretas como rachadas ou sem cracking.

Avance para o próximo tutorial para saber mais.

> [!div class="nextstepaction"]
> [Detecção de objeto](object-detection-onnx.md)
