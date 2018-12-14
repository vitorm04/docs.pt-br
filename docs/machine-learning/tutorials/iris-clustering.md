---
title: Agrupar flores íris usando um aprendiz de clustering – ML.NET
description: Saiba como usar o ML.NET em um cenário de clustering
author: pkulikov
ms.author: johalex
ms.date: 07/02/2018
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 5bd73c774f60466daaf52215c34e7e17b5f5cc9c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145616"
---
# <a name="tutorial-cluster-iris-flowers-using-a-clustering-learner-with-mlnet"></a>Tutorial: Agrupar flores íris usando um aprendiz de clustering com o ML.NET

> [!NOTE]
> Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações. Para obter mais informações, confira a [Introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Este tutorial ilustra como usar o ML.NET para criar um [modelo de clustering](../resources/tasks.md#clustering) para o [conjunto de dados de flor Iris](https://en.wikipedia.org/wiki/Iris_flower_data_set).

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
> - Compreender o problema
> - Selecionar a tarefa de aprendizado de máquina apropriada
> - Preparar os dados
> - Carregar e transformar os dados
> - Escolher um algoritmo de aprendizado
> - Treinar o modelo
> - Usar o modelo para previsões

## <a name="prerequisites"></a>Pré-requisitos

- [Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.

## <a name="understand-the-problem"></a>Compreender o problema

Esse problema abrange como dividir o conjunto de flores Iris em grupos diferentes com base nas características da flor. Essas características são o comprimento e largura de uma sépala e o comprimento e a largura de uma pétala. Para este tutorial, considere que o tipo de cada flor é desconhecido. Você deseja conhecer a estrutura de um conjunto de dados por meio de suas características e prever como uma instância de dados se encaixa nessa estrutura.

## <a name="select-the-appropriate-machine-learning-task"></a>Selecionar a tarefa de aprendizado de máquina apropriada

Como você não sabe a qual grupo cada flor pertence, escolha a tarefa [aprendizado de máquina não supervisionado](../resources/glossary.md#unsupervised-machine-learning). Para dividir um conjunto de dados em grupos de forma que os elementos no mesmo grupo sejam mais semelhantes uns aos outros do que aos elementos de outros grupos, use a tarefa de aprendizado de máquina [clustering](../resources/tasks.md#clustering).

## <a name="create-a-console-application"></a>Criar um aplicativo de console

1. Abra o Visual Studio 2017. Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus. Na caixa de diálogo **Novo Projeto**, selecione o nó **Visual C#** seguido pelo nó **.NET Core**. Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)**. Na caixa de texto **Nome**, digite "IrisClustering" e, em seguida, selecione o botão **OK**.

1. Crie um diretório chamado *Dados* em seu projeto para armazenar o conjunto de dados e os arquivos de modelo:

    No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Nova Pasta**. Digite "Data" e pressione Enter.

1. Instale o pacote NuGet **Microsoft.ML**:

    No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Gerenciar Pacotes NuGet**. Escolha "nuget.org" como a origem do Pacote, selecione a guia **Procurar**, pesquise **Microsoft.ML**, selecione o pacote na lista e escolha o botão **Instalar**. Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.

## <a name="prepare-the-data"></a>Preparar os dados

1. Baixe o conjunto de dados [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) e salve-o na pasta *Dados* que você criou na etapa anterior. Para obter mais informações sobre o conjunto de dados Iris, confira a página da Wikipédia [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) (Conjunto de dados de flor Iris) e a página [Iris Data Set](http://archive.ics.uci.edu/ml/datasets/Iris) (Conjunto de dados Iris), que é a fonte do conjunto de dados.

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no arquivo *iris.data* e selecione **Propriedades**. Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.

O arquivo *iris.data* contém cinco colunas que representam:

- o comprimento da sépala em centímetros
- a largura da sépala em centímetros
- o comprimento da pétala em centímetros
- a largura da pétala em centímetros
- o tipo de flor Iris

Para exemplificar o clustering, este tutorial ignora a última coluna.

## <a name="create-data-classes"></a>Criar classes de dados

Crie classes para os dados de entrada e as previsões:

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.
1. Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *IrisData.cs*. Em seguida, selecione o botão **Adicionar**.
1. Adicione a seguinte diretiva `using` ao novo arquivo:

   [!code-csharp[Add necessary usings](../../../samples/machine-learning/tutorials/IrisClustering/IrisData.cs#1)]

Remova a definição de classe existente e adicione o código a seguir, que define as classes `IrisData` e `ClusterPrediction`, para o arquivo *IrisData.cs*:

[!code-csharp[Define data classes](../../../samples/machine-learning/tutorials/IrisClustering/IrisData.cs#2)]

`IrisData` é a classe de dados de entrada e tem definições de cada característica provenientes do conjunto de dados. Use o atributo [Column](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) para especificar os índices das colunas de origem no arquivo de conjunto de dados.

A classe `ClusterPrediction` representa a saída do modelo de clustering aplicado a uma instância de `IrisData`. Use o atributo [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) para associar os campos `PredictedClusterId` e `Distances` às colunas **PredictedLabel** e **Score**, respectivamente. No caso da tarefa clustering, essas colunas têm o seguinte significado:

- A coluna **PredictedLabel** contém a ID do cluster previsto.
- A coluna **Score** contém uma matriz com as distâncias euclidianas quadradas para os centroides de cluster. O comprimento da matriz é igual ao número de clusters.

> [!NOTE]
> Use o tipo `float` para representar valores de ponto flutuante nas classes de dados de entrada e previsão.

## <a name="define-data-and-model-paths"></a>Definir dados e caminhos de modelo

Volte para o arquivo *Program.cs* e adicione dois campos para armazenar os caminhos no arquivo de conjunto de dados e no arquivo para salvar o modelo:

- `_dataPath` contém o caminho para o arquivo com o conjunto de dados usado para treinar o modelo.
- `_modelPath` contém o caminho para o arquivo em que o modelo treinado está armazenado.

Adicione o seguinte código logo acima do método `Main` para especificar estes caminhos:

[!code-csharp[Initialize paths](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#1)]

Para fazer com que o código anterior seja compilado, adicione as seguintes diretivas `using` ao início do arquivo *Program.cs*:

[!code-csharp[Add usings for paths](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#2)]

## <a name="create-a-learning-pipeline"></a>Criar um pipeline de aprendizado

Adicione as seguintes diretivas `using` adicionais ao início do arquivo *Program.cs*:

[!code-csharp[Add Microsoft.ML usings](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#3)]

No método `Main`, substitua `Console.WriteLine("Hello World!")` pelo código a seguir:

[!code-csharp[Call the Train method](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#4)]

O método `Train` treina o modelo. Crie esse método logo abaixo do método `Main`, usando o seguinte código:

```csharp
private static PredictionModel<IrisData, ClusterPrediction> Train()
{

}
```

O pipeline de aprendizado carrega todos os dados e algoritmos necessários para treinar o modelo. Adicione o seguinte código ao método `Train`:

[!code-csharp[Initialize pipeline](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#5)]

## <a name="load-and-transform-data"></a>Carregar e transformar dados

A primeira etapa a ser realizada é carregar o conjunto de dados de treinamento. Em nosso caso, o conjunto de dados de treinamento é armazenado no arquivo de texto com um caminho definido pelo campo `_dataPath`. As colunas no arquivo são separadas por uma vírgula (","). Adicione o seguinte código ao método `Train`:

[!code-csharp[Add step to load data](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#6)]

A próxima etapa é combinar todas as colunas de característica na coluna **Features** usando a classe de transformação <xref:Microsoft.ML.Legacy.Transforms.ColumnConcatenator>. Por padrão, um algoritmo de aprendizado processa apenas os recursos da coluna **Features**. Adicione o seguinte código:

[!code-csharp[Add step to concatenate columns](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#7)]

## <a name="choose-a-learning-algorithm"></a>Escolher um algoritmo de aprendizado

Após adicionar os dados ao pipeline e transformá-los no formato de entrada correto, selecione um algoritmo de aprendizado (**aluno**). O aprendiz treina o modelo. O ML.NET fornece um aprendiz <xref:Microsoft.ML.Legacy.Trainers.KMeansPlusPlusClusterer> que implementa o [algoritmo k-means](https://en.wikipedia.org/wiki/K-means_clustering) com um método melhor para escolher os centroides iniciais do cluster.

Adicione o seguinte código ao método `Train` após o código de processamento de dados adicionado na etapa anterior:

[!code-csharp[Add a learner step](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#8)]

Use a propriedade <xref:Microsoft.ML.Legacy.Trainers.KMeansPlusPlusClusterer.K?displayProperty=nameWithType> para especificar o número de clusters. O código acima especifica que o conjunto de dados deve ser dividido em três clusters.

## <a name="train-the-model"></a>Treinar o modelo

As etapas adicionadas nas seções anteriores prepararam o pipeline para treinamento, no entanto, nenhuma foi executada. O método `pipeline.Train<TInput, TOutput>` produz o modelo que aceita uma instância do tipo `TInput` e produz uma instância do tipo `TOutput`. Adicione o seguinte código ao método `Train`:

[!code-csharp[Train the model and return](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#9)]

### <a name="save-the-model"></a>Salvar o modelo

Neste ponto, você tem um modelo que pode ser integrado em qualquer um dos seus aplicativos .NET existentes ou novos. Para salvar seu modelo em um arquivo .zip, adicione o seguinte código no método `Main` abaixo da chamada ao método `Train`:

[!code-csharp[Save the model](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#10)]

Usar um `await` no método `Main` significa que o método `Main` deve ter o modificador `async` e retornar um `Task`:

[!code-csharp[Make the Main method async](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#11)]

Também é preciso adicionar a seguinte diretiva `using` ao início do arquivo *Program.cs*:

[!code-csharp[Add System.Threading.Tasks using](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#12)]

Como o método `async Main` é um novo recurso adicionado no C# 7.1 e a versão da linguagem padrão do projeto é C# 7.0, é necessário alterar a versão da linguagem para C# 7.1 ou superior. Para fazer isso, clique com o botão direito do mouse no nó do projeto no **Gerenciador de Soluções** e selecione **Propriedades**. Selecione a guia **Build** e o botão **Avançado**. No menu suspenso, selecione **C# 7.1** (ou uma versão posterior). Selecione o botão **OK**.

## <a name="use-the-model-for-predictions"></a>Usar o modelo para previsões

Crie a classe `TestIrisData` para hospedar as instâncias de dados de teste:

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.
1. Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *TestIrisData.cs*. Em seguida, selecione o botão **Adicionar**.
1. Modifique a classe para ser estática, como no exemplo a seguir:

   [!code-csharp[Make class static](../../../samples/machine-learning/tutorials/IrisClustering/TestIrisData.cs#1)]

Este tutorial apresenta uma instância de dados de Iris dentro dessa classe. Você pode adicionar outros cenários para fazer experimentos com o modelo. Adicione o seguinte código à classe `TestIrisData`:

[!code-csharp[Test data](../../../samples/machine-learning/tutorials/IrisClustering/TestIrisData.cs#2)]

Para descobrir a qual cluster o item especificado pertence, volte para o arquivo *Program.cs* e adicione o seguinte código no método `Main`:

[!code-csharp[Predict and output results](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#13)]

Execute o programa para ver qual cluster contém a instância de dados especificada e a distância quadrada daquela instância aos centroides do cluster. Seus resultados devem ser semelhantes aos seguintes. À medida que o pipeline é processado, ele pode exibir avisos ou mensagens de processamento. Esses itens foram removidos da saída a seguir para deixá-la mais clara.

```text
Cluster: 2
Distances: 0.4192338 0.0008847713 0.9660053
```

Parabéns! Você agora construiu um modelo de aprendizado de máquina para clustering de Iris e o usou para fazer previsões. Encontre o código-fonte deste tutorial no repositório do GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisClustering).

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como:
> [!div class="checklist"]
> - Compreender o problema
> - Selecionar a tarefa de aprendizado de máquina apropriada
> - Preparar os dados
> - Carregar e transformar os dados
> - Escolher um algoritmo de aprendizado
> - Treinar o modelo
> - Usar o modelo para previsões

Confira nosso repositório GitHub para continuar aprendendo e encontrar mais amostras.
> [!div class="nextstepaction"]
> [dotnet/machinelearning GitHub repository](https://github.com/dotnet/machinelearning/)
