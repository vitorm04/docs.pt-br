---
title: Criar um classificador de imagens personalizadas do ML.NET com o TensorFlow
description: Descubra como criar um classificador de imagens personalizadas do ML.NET em um cenário de aprendizado de transferência do TensorFlow para classificar imagens reutilizando um modelo do TensorFlow pré-treinado.
ms.date: 04/05/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 9b9ac1f1f15b4003a19a3d30d6cadf3e86946376
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517961"
---
# <a name="tutorial-build-an-mlnet-custom-image-classifier-with-tensorflow"></a>Tutorial: Criar um classificador de imagens personalizadas do ML.NET com o TensorFlow

Este tutorial de amostra ilustra como você pode usar um modelo de Classificador de Imagens `TensorFlow` já treinado para criar um novo modelo customizado para classificar imagens em algumas categorias.

E se você pudesse reutilizar um modelo que já tenha sido pré-treinado para resolver um problema semelhante e treinar novamente todas ou algumas das camadas desse modelo para resolvê-lo? Essa técnica de reutilizar parte de um modelo já treinado para construir um novo modelo é conhecida como [aprendizado de transferência](https://en.wikipedia.org/wiki/Transfer_learning).

Treinar um modelo de [Classificação de Imagens](https://en.wikipedia.org/wiki/Outline_of_object_recognition) do zero requer a configuração de milhões de parâmetros, uma tonelada de dados de treinamento rotulados e uma grande quantidade de recursos de computação (centenas de horas de GPU). Embora não seja tão eficaz quanto treinar um modelo personalizado do zero, o aprendizado de transferência permite que você ative esse processo trabalhando com milhares de imagens em comparação com milhões de imagens rotuladas e crie um modelo personalizado rapidamente (em uma hora em uma máquina sem GPU).

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
> * Compreender o problema
> * Reutilizar e ajustar o modelo pré-treinado
> * Classificar imagens

> [!NOTE]
> Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações. Para obter mais informações, visite [a introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Este tutorial e uma amostra relacionada estão usando o **ML.NET versão 0.10** no momento. Para obter mais informações, confira as notas sobre a versão no repositório do GitHub [dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

## <a name="image-classification-sample-overview"></a>Visão geral da amostra de classificação de imagens

O exemplo é um aplicativo de console que usa o ML.NET para criar um classificador de imagens reutilizando um modelo pré-treinado para classificar imagens com uma pequena quantidade de dados de treinamento.

Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF).

## <a name="prerequisites"></a>Pré-requisitos

* [Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.

* Pacote Nuget Microsoft.ML 0.10.0
* Pacote Nuget Microsoft.ML.ImageAnalytics 0.10.0
* Pacote Nuget Microsoft.ML.TensorFlow 0.10.0

* [O arquivo .ZIP do diretório de recursos do tutorial](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)

* [O modelo de aprendizado de máquina InceptionV3](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-appropriate-machine-learning-task"></a>Selecionar a tarefa de aprendizado de máquina apropriada

[Aprendizado profundo](https://en.wikipedia.org/wiki/Deep_learning) é um subconjunto do aprendizado de máquina, que está revolucionando áreas como Pesquisa Visual Computacional e Reconhecimento de Fala.

Os modelos de aprendizado profundo são treinados usando grandes conjuntos de [dados rotulados](https://en.wikipedia.org/wiki/Labeled_data) e [redes neurais](https://en.wikipedia.org/wiki/Artificial_neural_network) que contêm várias camadas de aprendizado. Aprendizado profundo:

* Funciona melhor em algumas tarefas como a Pesquisa Visual Computacional.

* Funciona bem em enormes quantidades de dados.

A classificação de imagens é uma tarefa comum de aprendizado de máquina que nos permite classificar automaticamente as imagens em várias categorias, como:

* Detectar uma face humana em uma imagem ou não.
* Detectar gatos e cachorros.

 Ou, como nas imagens a seguir, que determinar se uma imagem é um alimento, brinquedo ou dispositivo:

![imagem de pizza](./media/image-classification/220px-Pepperoni_pizza.jpg)
![imagem de ursinho de pelúcia](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![imagem de torradeira](./media/image-classification/193px-Broodrooster.jpg)

>[!Note]
> As imagens anteriores pertencem ao Wikimedia Commons e são atribuídas da seguinte forma:
>
> * "220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,
> * "119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.
> * "193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403

O aprendizado de transferência inclui algumas estratégias, como *readaptar todas as camadas* e a *penúltima camada*. Esse tutorial explicará e mostrará como usar a *estratégia de penúltima camada*. A *estratégia de penúltima camada* reutiliza um modelo que já foi pré-treinado para resolver um problema específico. A estratégia, em seguida, treina novamente a camada final desse modelo para resolver um novo problema. Reutilizar o modelo pré-treinado como parte de seu novo modelo economizará tempo e recursos significativos.

Seu modelo de classificação de imagens reutiliza o modelo [Concepção](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), um popular modelo de reconhecimento de imagens treinado no conjunto de dados `ImageNet` em que o modelo TensorFlow tenta classificar imagens inteiras em mil classes, como “guarda-chuva”, “camiseta” e “lava-louças”.

O `Inception v3 model` pode ser classificado como uma [rede neural convolucional profunda](https://en.wikipedia.org/wiki/Convolutional_neural_network) e pode alcançar um desempenho razoável em tarefas de reconhecimento visual, combinando ou excedendo o desempenho humano em alguns domínios. O modelo/algoritmo foi desenvolvido por múltiplos pesquisadores e baseado no artigo original: ["Reformulação da arquitetura de concepção para pesquisa visual computacional" por Szegedy, et. Al.](https://arxiv.org/abs/1512.00567)

Como o `Inception model` já foi pré-treinado em milhares de imagens diferentes, ele contém os [recursos de imagem](https://en.wikipedia.org/wiki/Feature_(computer_vision)) necessários para a identificação da imagem. As camadas de recurso de imagens inferiores reconhecem recursos simples (como bordas), e as camadas superiores reconhecem recursos mais complexos (como formas). A camada final é treinada contra um conjunto muito menor de dados porque você está começando com um modelo pré-treinado que já entende como classificar imagens. Como seu modelo permite classificar mais de duas categorias, este é um exemplo de um [classificador multiclasse](../resources/tasks.md#multiclass-classification). 

`TensorFlow` é um popular kit de ferramentas de aprendizado profundo e aprendizado de máquina que permite o treinamento de redes neurais profundas (e cálculos numéricos gerais) e é implementado como um `transformer` no ML.NET. Para este tutorial, é usado para reutilizar o `Inception model`.

Conforme mostrado no diagrama a seguir, você adiciona uma referência aos pacotes ML.NET NuGet em seus aplicativos .NET Core ou .NET Framework. Nos bastidores, o ML.NET inclui e faz referência à biblioteca `TensorFlow` nativa que permite escrever código que carrega um arquivo de modelo `TensorFlow` existente e treinado para pontuação.  

![Diagrama de arco da transformação do TensorFlow do ML.NET](./media/image-classification/tensorflow-mlnet.png)

O `Inception model` é treinado para classificar imagens em mil categorias, mas é necessário classificar imagens em um conjunto de categorias menor e apenas nessas categorias. Digite a parte `transfer` de `transfer learning`. Você pode transferir a capacidade de `Inception model` de reconhecer e classificar imagens para as novas categorias limitadas do seu classificador de imagens personalizadas.  

 Você vai treinar novamente a camada final desse modelo usando um conjunto de três categorias:

* Alimentação
* Brinquedos
* Dispositivos

Sua camada usa um [algoritmo de regressão logística multinomial](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) para encontrar a categoria correta o mais rápido possível. Esse algoritmo classifica usando probabilidades para determinar a resposta, dando um valor para a categoria correta e um valor zero para os outros.  

### <a name="dataset"></a>DataSet

Há duas fontes de dados: o arquivo `.tsv` e os arquivos de imagem.  O arquivo `tags.tsv` contém duas colunas: a primeira é definida como `ImagePath` e a segunda é a `Label` correspondente à imagem. O arquivo de exemplo a seguir não possui uma linha de cabeçalho e tem a seguinte aparência:

<!-- markdownlint-disable MD010 -->
```tsv
broccoli.jpg    food
pizza.jpg   food
pizza2.jpg  food
teddy2.jpg  toy
teddy3.jpg  toy
teddy4.jpg  toy
toaster.jpg appliance
toaster2.png    appliance
```
<!-- markdownlint-enable MD010 -->

As imagens de treinamento e teste estão localizadas nas pastas de recursos que você baixará em um arquivo zip. Essas imagens pertencem ao Wikimedia Commons.
> *[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), o repositório de mídia gratuito.* Recuperado em 10:48, 17 de outubro de 2018 de:  
> https://commons.wikimedia.org/wiki/Pizza  
> https://commons.wikimedia.org/wiki/Toaster  
> https://commons.wikimedia.org/wiki/Teddy_bear  

## <a name="create-a-console-application"></a>Criar um aplicativo de console

### <a name="create-a-project"></a>Criar um projeto

1. Abra o Visual Studio 2017. Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus. Na caixa de diálogo **Novo Projeto**, selecione o nó **Visual C#** seguido pelo nó **.NET Core**. Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)**. Na caixa de texto**Nome**, digite "TransferLearningTF" e, em seguida, selecione o botão **OK**.

2. Instalar o **Pacote NuGet Microsoft.ML**:

    No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**. Escolha "nuget.org" como a fonte do pacote, selecione a guia Browse, procure por **Microsoft.ML**. Clique na lista suspensa **Versão**, selecione o pacote **0.10.0** na lista e selecione o botão **Instalar**. Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados. Repita essas etapas para **Microsoft.ML.ImageAnalytics v0.10.0** e **Microsoft.ML.TensorFlow v0.10.0**.

  > [!NOTE]
  > Esse tutorial usa **Microsoft.ML v0.10.0**, **Microsoft.ML.ImageAnalytics v0.10.0** e **Microsoft.ML.TensorFlow v0.10.0**.

### <a name="prepare-your-data"></a>Preparar seus dados

1. Baixe o [arquivo zip do diretório de materiais do projeto](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip) e descompacte.

2. Copie o diretório`assets` no diretório do projeto *TransferLearningTF*. Este diretório e seus subdiretórios contêm os arquivos de dados e de suporte (exceto o modelo Concepção, que você irá baixar e adicionar na próxima etapa) necessários para este tutorial.

3. Baixe o [modelo Concepção](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) e descompacte-o.

4. Copie o conteúdo do diretório `inception5h` apenas descompactado em seu diretório de projeto *TransferLearningTF*`assets\inputs-train\inception`. Este diretório contém o modelo e os arquivos de suporte adicionais necessários para este tutorial, conforme mostrado na imagem a seguir:

   ![Conteúdo do diretório de concepção](./media/image-classification/inception-files.png)

5. No Gerenciador de Soluções, clique com o botão direito do mouse em cada um dos arquivos no diretório e nos subdiretórios do ativo e selecione**Propriedades**. Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.

### <a name="create-classes-and-define-paths"></a>Criar classes e definir demarcadores

Adicione as seguintes instruções `using` adicionais ao início do arquivo *Program.cs*:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

Crie campos globais para manter os caminhos para os vários ativos e variáveis globais para `LabelTokey`, `ImageReal` e `PredictedLabelValue`:

* `_assetsPath` tem o demarcador para os ativos.
* `_trainTagsTsv` tem o demarcador para o arquivo tsv de tags de dados de imagem de treinamento.
* `_predictTagsTsv` tem o demarcador para o arquivo tsv de tags de dados de imagem de previsão.
* `_trainImagesFolder` tem o demarcador para as imagens usadas para treinar o modelo.
* `_predictImagesFolder` tem o demarcador para as imagens a serem classificadas pelo modelo treinado.
* `_inceptionPb`tem o demarcador para o modelo Concepção pré-treinado para ser reutilizado para treinar seu modelo.
* `_inputImageClassifierZip` tem o demarcador de onde o modelo treinado é carregado.
* `_outputImageClassifierZip` tem o demarcador em que o modelo treinado é salvo.
* `LabelTokey` é o `Label` valor mapeado para uma chave.
* `ImageReal` é a coluna que contém o valor da imagem prevista.
* `PredictedLabelValue` é a coluna que contém o valor do rótulo previsto.

Adicione o seguinte código à linha logo acima do método `Main` para especificar estes caminhos e as outras variáveis:

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

Crie algumas classes para os dados de entrada e as previsões. Adicione uma nova classe ao seu projeto:

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.

1. Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *ImageData.cs*. Em seguida, selecione o botão **Adicionar**.

    O arquivo *ImageData.cs* é aberto no editor de códigos. Adicione a seguinte instrução `using` à parte superior do *ImageData.cs*:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#AddUsings)]

Remova a definição de classe existente e adicione o seguinte código para a classe `ImageData` do arquivo *ImageData.cs*:

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#DeclareTypes)]

`ImageData` é a classe de conjunto de dados de entrada e tem os seguintes campos <xref:System.String>:

* `ImagePath` contém o nome do arquivo de imagem.
* `Label` contém um valor para o rótulo da imagem.

Adicione uma nova classe ao seu projeto para `ImagePrediction`:

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.

1. Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *ImagePrediction.cs*. Em seguida, selecione o botão **Adicionar**.

    O arquivo *ImagePrediction.cs* é aberto no editor de códigos. Remova as instruções `System.Collections.Generic` e `System.Text` `using` na parte superior do *ImagePrediction.cs*:

Remova a definição de classe existente e adicione o seguinte código, que tem a classe `ImagePrediction`, ao arquivo *ImagePrediction.cs*:

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/ImagePrediction.cs#DeclareTypes)]

`ImagePrediction` é a classe de previsão de imagem e possui os seguintes campos:

* `Score` contém a porcentagem de confiança para uma determinada classificação de imagem.
* `PredictedLabelValue` contém um valor para o rótulo de classificação de imagem previsto.

`ImagePrediction` é a classe usada para previsão depois que o modelo foi treinado. Tem um `string` (`ImagePath`) para o demarcador da imagem. O `Label` é usado para reutilizar e treinar novamente o modelo. O `PredictedLabelValue` é usado durante a previsão e avaliação. Para avaliação, uma entrada com dados de treinamento, os valores previstos e o modelo são usados.

A [classe MLContext](xref:Microsoft.ML.MLContext) é um ponto de partida para todas as operações do ML.NET e a inicialização do `mlContext` cria um ambiente do ML.NET que pode ser compartilhado entre os objetos de fluxo de trabalho da criação de modelo. Ele é semelhante, conceitualmente, a `DBContext` no Entity Framework.

### <a name="initialize-variables-in-main"></a>Inicializar variáveis em Main

Inicialize a variável `mlContext` com uma nova instância de `MLContext`.  Substitua a linha `Console.WriteLine("Hello World!")` pelo seguinte código no método `Main`:

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

### <a name="create-a-struct-for-default-parameters"></a>Crie um struct para os parâmetros padrão

O modelo Concepção possui vários parâmetros padrão que você precisa verificar. Crie um struct para mapear os valores de parâmetros padrão para nomes amigáveis com o seguinte código, logo após o método `Main()`:

[!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a>Criar um método de utilitário de exibição

Emparelhe e exiba os dados da imagem e as previsões relacionadas mais de uma vez, e você não deseja duplicar o código. Crie um método de utilitário de exibição para manipular o pareamento e exibir a imagem e os resultados de previsão.

O método `PairAndDisplayResults()` executa as seguintes tarefas:

* Combina dados e previsões para relatórios.
* Exibe os resultados previstos.

Crie o método `PairAndDisplayResults()`, logo após o struct `InceptionSettings`, usando o seguinte código:

```csharp
private static void PairAndDisplayResults(IEnumerable<ImageNetData> imageData, IEnumerable<ImageNetPrediction> imagePredictionData)
{

}
```

Antes de exibir os resultados previstos, combine `imageData` e `imagePrediction` juntos para ver o `Image Path` original com a categoria prevista. O código a seguir usa o método <xref:System.Linq.Enumerable.Zip%2A?displayProperty=nameWithType> para que isso aconteça, então adicione-o como a primeira linha do método `PairAndDisplayResults()`:

[!code-csharp[BuildImagePredictionPairs](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#BuildImagePredictionPairs)]

Agora que você combinou `imageData` e `imageData` em uma classe, você pode exibir os resultados usando o método <xref:System.Console.WriteLine?displayProperty=nameWithType>:

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

Você chamará o método `PairAndDisplayResults()` nos próximos dois métodos.

### <a name="create-a-tsv-file-utility-method"></a>Criar um método de utilitário de arquivo .tsv

O método `ReadFromTsv()` executa as seguintes tarefas:

* Lê o arquivo de dados de imagem `tags.tsv`.
* Adiciona o demarcador do arquivo ao nome do arquivo de imagem.
* Carrega os dados do arquivo em um objeto IEnumerable`ImageData`.

Crie o método `ReadFromTsv()`, logo após o método `PairAndDisplayResults()`, usando o seguinte código:

```csharp
public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
{

}
```

O código a seguir analisa o arquivo `tags.tsv` para adicionar o demarcador do arquivo ao nome do arquivo de imagem para a propriedade `ImagePath` e o carregá-lo e o `Label` em um objeto `ImageData`. Adicione-o como a primeira linha do método `ReadFromTsv()`.  Você precisa do demarcador completo do arquivo para exibir os resultados da previsão.

[!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]
Há três conceitos principais no ML.NET: [Dados](../basic-concepts-model-training-in-mldotnet.md#data), [Transformadores](../basic-concepts-model-training-in-mldotnet.md#transformer) e [Avaliadores](../basic-concepts-model-training-in-mldotnet.md#estimator).

## <a name="reuse-and-tune-pre-trained-model"></a>Reutilizar e ajustar um modelo pré-treinado

Adicione a seguinte chamada ao método `ReuseAndTuneInceptionModel()` como a próxima linha de código no método `Main()`:

[!code-csharp[CallReuseAndTuneInceptionModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReuseAndTuneInceptionModel)]

O método `ReuseAndTuneInceptionModel()` executa as seguintes tarefas:

* Carrega os dados.
* Extrai e transforma os dados.
* Pontua o modelo do TensorFlow.
* Ajusta (readapta) o modelo.
* Exibe os resultados do modelo.
* Avalia o modelo.
* Salva o modelo.

Crie o método `ReuseAndTuneInceptionModel()` logo após o struct `InceptionSettings` e antes do método `PairAndDisplayResults()`, usando o seguinte código:

```csharp
public static void ReuseAndTuneInceptionModel(MLContext mlContext, string dataLocation, string imagesFolder, string inputModelLocation, string outputModelLocation)
{

}
```

### <a name="load-the-data"></a>Carregar os dados

Os dados do ML.NET são representados como uma [classe IDataView](xref:Microsoft.Data.DataView.IDataView). `IDataView` é uma maneira flexível e eficiente de descrever dados tabulares (numéricos e texto). Os dados podem ser carregados de um arquivo de texto ou em tempo real (por exemplo, banco de dados SQL ou arquivos de log) para um objeto `IDataView`.

Carregue os dados usando o wrapper `MLContext.Data.ReadFromTextFile`. Adicione o seguinte código ao método `ReuseAndTuneInceptionModel()` como a linha seguinte:

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

### <a name="extract-features-and-transform-the-data"></a>Extrair recursos e transformar os dados

O pré-processamento e a limpeza de dados são tarefas importantes que ocorrem antes de um conjunto de dados ser usado efetivamente para o aprendizado de máquina.  Usar dados sem essas tarefas de modelagem pode produzir resultados enganosos.

Algoritmos de aprendizado de máquina entendem [dados caracterizados](../resources/glossary.md#feature), e ao lidar com redes neurais profundas você deve adaptar as imagens ao formato esperado pela rede. Esse formato é um [vetor numérico](../resources/glossary.md#numerical-feature-vector).

Após o treinamento e a avaliação, faça a previsão com os valores da coluna **Rótulo**. Ao usar um modelo pré-treinado, mapeie os campos para o novo modelo com o método [MapValueToKey ()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A). Este método transforma a coluna `Label` em um tipo de chave numérica (`LabelTokey`) e a adiciona como nova coluna do conjunto de dados:  Dê um nome a este `estimator` porque você também adicionará o treinador a ele. Adicione a seguinte linha de código:

[!code-csharp[MapValueToKey1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey1)]

O seu estimador de processamento de imagens usa recursos de recursos para extração de recursos pré-treinados [Deep Neural Network (DNN)](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks). Ao lidar com redes neurais profundas, você adapta as imagens ao formato de rede esperado. Essa é a razão pela qual você usa várias transformações de imagem para obter os dados da imagem no formato esperado do modelo:

1. As imagens de transformação `LoadImages` são carregadas na memória como um tipo de bitmap.
2. A transformação `Resize` redimensiona as imagens porque o modelo pré-treinado tem uma largura e altura de imagem de entrada definidas.
3. A transformação `ImagePixelExtractingEstimator` extrai os pixels das imagens de entrada e os converte em um vetor numérico.

Adicione essas transformações de imagem como as próximas linhas de código:

[!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

O `TensorFlowTransform` extrai as saídas especificadas (os recursos da imagem do `Inception model``softmax2_pre_activation`) e marca um conjunto de dados usando o model o`TensorFlow` pré-treinado.

`softmax2_pre_activation` auxilia o modelo a determinar a qual classe as imagens pertencem. `softmax2_pre_activation` retorna uma probabilidade para cada uma das categorias para uma imagem, e todas essas probabilidades devem somar 1. Ele pressupõe que uma imagem pertencerá a apenas uma categoria, conforme mostrado no exemplo a seguir:

| Classe         | Probabilidade   |
| ------------- | ------------- |
| `Food`        |  0.001        |
| `Toy`         |  0.95         |
| `Appliance`   |  0.06         |

Adicione `TensorFlowTransform` ao `estimator` com a seguinte linha de código:

[!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

### <a name="choose-a-training-algorithm"></a>Escolher um algoritmo de treinamento

Para adicionar o algoritmo de treinamento, chame o método wrapper `mlContext.MulticlassClassification.Trainers.LogisticRegression()`.  O `LogisticRegression` é anexado ao `estimator` e aceita os recursos da imagem Concepção (`softmax2_pre_activation`) e os parâmetros de entrada `Label` para aprender com os dados históricos.  Adicione o treinador com o seguinte código:

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

Você também precisa mapear o `predictedlabel` para o `predictedlabelvalue`:

[!code-csharp[MapValueToKey2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey2)]

O método `Fit()` treina o modelo com o conjunto de dados de treinamento fornecido. Ele executa as definições `Estimator` transformando os dados e aplicando o treinamento e retorna o modelo treinado, que é um `Transformer`. Ajuste o modelo aos dados `Train` e retorne o modelo treinado adicionando o seguinte como a próxima linha de código no método `ReuseAndTuneInceptionModel()`:

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

O método [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) faz previsões para várias linhas de entrada fornecidas de um conjunto de dados de teste.  Transforme os dados `Training` adicionando o seguinte código a `ReuseAndTuneInceptionModel()`:

[!code-csharp[TransformData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TransformData)]

Converta seus dados de imagem e previsão `DataViews` em `IEnumerables` fortemente tipados para emparelhar para exibição mais fácil. Use o método `MLContext.CreateEnumerable()` para fazer isso, usando o seguinte código:

[!code-csharp[EnumerateDataViews](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#EnumerateDataViews)]

Chame o método `PairAndDisplayResults()` para parear e exibir seus dados e previsões como a próxima linha no método `ReuseAndTuneInceptionModel()`:

[!code-csharp[CallPairAndDisplayResults1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallPairAndDisplayResults1)]

Depois de determinar a previsão, o método [Evaluate ()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A):

* Avalia o modelo (compara os valores previstos com o conjunto de dados real `Labels`).

* Retorna as métricas de desempenho do modelo. 

Adicione o seguinte código ao método `ReuseAndTuneInceptionModel()` como a linha seguinte:

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

As seguintes métricas são avaliadas para classificação de imagem:

* `Log-loss` - confira [Perda de log](../resources/glossary.md#log-loss). Convém que a Perda de log seja tão próxima de zero quanto possível.

* `Per class Log-loss`. Convém que a Perda de log por classe seja tão próxima de zero quanto possível.

Use o código a seguir para exibir as métricas, compartilhar os resultados e, em seguida, agir com relação a eles:

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

`mlContext.Model.Save` salva o modelo treinado em um arquivo .zip (na pasta "ativos/saídas"), que pode ser usado em outros aplicativos .NET para fazer previsões. Adicione o seguinte código ao método `ReuseAndTuneInceptionModel()` como a linha seguinte:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#SaveModel)]

## <a name="classify-images-with-a-loaded-model"></a>Classificar imagens com um modelo carregado

Adicione a seguinte chamada ao método `ClassifyImages()` como a próxima linha de código no método `Main`:

[!code-csharp[CallClassifyImages](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifyImages)]

O método `ClassifyImages()` executa as seguintes tarefas:

* Aplica o modelo.
* Lê o arquivo .TSV em `IEnumerable`.
* Prevê as classificações de imagens com base nos dados de teste.

Crie o método `ClassifyImages()` logo após o método `ReuseAndTuneInceptionModel()` (e antes do método `PairAndDisplayResults()`) usando o seguinte código:

```csharp
public static void ClassifyImages(MLContext mlContext, string dataLocation, string imagesFolder, string outputModelLocation)
{

}
```

Primeiro, carregue o modelo que você salvou anteriormente com o código a seguir:

[!code-csharp[LoadModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadModel)]

Chame o método `ReadFromTsv()` para criar uma classe `IEnumerable<ImageData>` que contenha o caminho absoluto para cada `ImagePath`. Você precisa desse caminho de arquivo para parear seus dados e resultados de previsão. Você também precisa converter a classe `IEnumerable<ImageData>` para uma `IDataView` que você usará para fazer a previsão. Adicione o seguinte código como as próximas duas linhas no método `ClassifyImages()`:

[!code-csharp[ReadFromTSV](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTSV)]

Como você fez anteriormente com os dados da imagem de treinamento, preveja a categoria dos dados da imagem de teste usando o método [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A). Adicione o seguinte código ao método `ClassifyImages()` para as previsões e converta `predictions``IDataView` em um `IEnumerable` para parear e exibir:

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Predict)]

Para parear e exibir os dados e as previsões da sua imagem de teste, adicione o código a seguir para chamar o método `PairAndDisplayResults()` criado anteriormente como a próxima linha no método `ClassifyImages()`:

[!code-csharp[CallPairAndDisplayResults2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallPairAndDisplayResults2)]

## <a name="classify-a-single-image-with-a-loaded-model"></a>Classifique uma única imagem com um modelo carregado

Adicione a seguinte chamada ao método `ClassifySingleImage()` como a próxima linha de código no método `Main`:

[!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

O método `ClassifyImages()` executa as seguintes tarefas:

* Aplica o modelo.
* Carrega uma instância `ImageData`.
* Prevê a classificação de imagens com base nos dados de teste.

Crie o método `ClassifySingleImage()` logo após o método `ClassifyImages()` (e antes do método `PairAndDisplayResults()`) usando o seguinte código:

```csharp
public static void ClassifySingleImage(MLContext mlContext, string imagePath, string outputModelLocation)
{

}
```

Primeiro, carregue o modelo que você salvou anteriormente com o código a seguir:

[!code-csharp[LoadModel2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadModel2)]

Crie uma classe `ImageData` que contenha o caminho completo e o nome do arquivo de imagem para o único `ImagePath`. Adicione o seguinte código como as próximas linhas no método `ClassifySingleImage()`:

[!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

A classe [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) é uma API de conveniência que executa uma previsão em uma única instância de dados. A função [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) faz uma previsão sobre uma única coluna de dados. Passe `imageData` para `PredictionEngine` para prever a categoria da imagem adicionando o seguinte código a `ClassifySingleImage()`:

[!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

Exiba o resultado da previsão como a próxima linha de código no método `ClassifySingleImage()`:

[!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="results"></a>Resultados

Depois de seguir as etapas anteriores, execute o aplicativo de console (Ctrl+F5). O resultado deverá ser semelhante à seguinte saída.  Você poderá ver avisos ou mensagens de processamento, mas essas mensagens foram removidas dos resultados a seguir para maior clareza.

```console
=============== Training classification model ===============
Image: broccoli.jpg predicted as: food with score: 0.976743
Image: pizza.jpg predicted as: food with score: 0.9751652
Image: pizza2.jpg predicted as: food with score: 0.9660203
Image: teddy2.jpg predicted as: toy with score: 0.9748783
Image: teddy3.jpg predicted as: toy with score: 0.9829691
Image: teddy4.jpg predicted as: toy with score: 0.9868168
Image: toaster.jpg predicted as: appliance with score: 0.9769174
Image: toaster2.png predicted as: appliance with score: 0.9800823
=============== Classification metrics ===============
LogLoss is: 0.0228266745633507
PerClassLogLoss is: 0.0277501705149937 , 0.0186303530571291 , 0.0217359128952187
=============== Save model to local file ===============
Model saved: C:\Tutorials\TransferLearningTF\bin\Debug\netcoreapp2.2\assets\outputs\imageClassifier.zip
=============== Loading model ===============
Model loaded: C:\Tutorials\TransferLearningTF\bin\Debug\netcoreapp2.2\assets\outputs\imageClassifier.zip
=============== Making classifications ===============
Image: broccoli.png predicted as: food with score: 0.905548
Image: pizza3.jpg predicted as: food with score: 0.9709008
Image: teddy6.jpg predicted as: toy with score: 0.9750155
=============== Loading model ===============
Model loaded: C:\Tutorials\TransferLearningTF\bin\Debug\netcoreapp2.2\assets\outputs\imageClassifier.zip
=============== Making single image classification ===============
Image: toaster3.jpg predicted as: appliance with score: 0.9625379
Press any key to continue . . .
```

Parabéns! Agora você criou com sucesso um modelo de aprendizado de máquina para classificação de imagem reutilizando um modelo `TensorFlow` pré-treinado no ML.NET.

Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF).

Neste tutorial, você aprendeu como:
> [!div class="checklist"]
> * Compreender o problema
> * Reutilizar e ajustar o modelo pré-treinado
> * Classificar imagens com um modelo carregado

Conferir o repositório GitHub de Amostras de Aprendizado de Máquina para explorar uma amostra de classificação de imagem expandida.
> [!div class="nextstepaction"]
> [dotnet/machinelearning-samples GitHub repository](https://github.com/dotnet/machinelearning-samples/)
