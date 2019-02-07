---
title: Conceitos básicos do treinamento de modelo no ML.NET
description: Este artigo explica os conceitos básicos que abrangem os cenários de *treinamento de modelo* no ML.NET. Nem todos os conceitos são relevantes para o cenário mais simples de *previsão com o modelo existente*.
ms.date: 11/06/2018
ms.topic: overview
ms.custom: mvc
ms.openlocfilehash: cff833b45583bc752bb42616820a95ca6c5c6b12
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "55252435"
---
# <a name="basic-concepts-for-model-training-in-mlnet"></a>Conceitos básicos do treinamento de modelo no ML.NET

Este artigo explica os conceitos básicos que abrangem os cenários de *treinamento de modelo* no ML.NET. Nem todos os conceitos são relevantes para o cenário mais simples de *previsão com o modelo existente*.

## <a name="model-training-concepts"></a>Conceitos de treinamento de modelo

Este documento aborda os seguintes conceitos relacionados ao treinamento de modelo no ML.NET:

- [*Dados*](#data) representados como uma interface `IDataView`.
  - No ML.NET, os dados são semelhantes a uma exibição SQL: Eles são um conjunto de dados avaliados lentamente, imutáveis, cursorizáveis, heterogêneos e esquematizados. 
  - Um documento excelente sobre a interface de dados é [Princípios de design de IDataView](https://github.com/dotnet/machinelearning/blob/master/docs/code/IDataViewDesignPrinciples.md).
- [*Transformador*](#transformer) representado como a interface `ITransformer`.
  - Um transformador é um componente que usa dados, realiza algumas tarefas nele e retorna novos dados transformados.
  - Por exemplo, você pode pensar em um modelo de machine learning como um transformador que usa funcionalidades e retorna previsões.
  - Outro exemplo: um criador de token de texto usa uma única coluna de texto e gera uma coluna de vetor com palavras individuais extraídas dos textos.
- [*Leitor de dados*](#data-reader) representado como uma interface `IDataReader<T>`.
  - O leitor de dados é o componente do ML.NET para criação de dados. Ele usa uma instância de `T` e retorna dados dela. 
  - Por exemplo, um *TextLoader* é um `IDataReader<FileSource>`. Ele usa uma fonte de arquivo e produz dados. 
- [*Avaliador*](#estimator) representado como uma interface `IEstimator<T>`.
  - Esse é um objeto que aprende com os dados. O resultado do aprendizado é um *transformador*.
  - Você pode pensar em um *algoritmo* de aprendizado de máquina como um avaliador que aprende com os dados e produz um *modelo* de machine learning.
- [*Função de previsão*](#prediction-function) representada como uma classe `PredictionFunction<TSrc, TDst>`.
  - A função de previsão pode ser vista como um computador que aplica um transformador a uma linha, como no momento da previsão.

## <a name="data"></a>Dados

No ML.NET, os dados são semelhantes a uma exibição SQL: Eles são um conjunto de dados avaliados lentamente, cursorizáveis, heterogêneos e esquematizados.

- Eles têm um *Esquema* (uma instância de uma interface `ISchema`) que contém as informações sobre as colunas da exibição de dados.
  - Cada coluna tem um *Nome*, um *Tipo* e um conjunto arbitrário de *metadados* associados a ela.
  - Os *metadados* da coluna contêm informações como nomes de slot de uma coluna de vetor e similares. Os metadados em si são representados como outros *dados* de uma linha que são exclusivos a cada coluna.
  - A exibição de dados é uma fonte de *cursores*. Pense nos cursores de SQL: Um cursor é um objeto que itera pelos dados, uma linha por vez e apresenta os dados disponíveis.
  - Naturalmente, os dados podem ter tantos cursores ativos neles quanto necessário. Como os dados em si são imutáveis, os cursores são verdadeiramente independentes.
  - Os cursores normalmente acessam somente um subconjunto de colunas: Para eficiência, o ML.NET calcula apenas os valores das colunas que são necessárias pelo cursor.

## <a name="transformer"></a>Transformador

Um transformador é um componente que usa dados, realiza algumas tarefas nele e retorna novos dados transformados.

A maioria dos transformadores do ML.NET tende a operar em uma *coluna de entrada* por vez e produzir a *coluna de saída*. Por exemplo, um `new HashTransformer("foo", "bar")` usa os valores da coluna "foo", cria um hash deles e coloca-os na coluna "bar". 

Também é comum que os nomes de coluna de entrada e saída sejam os mesmos. Nesse caso, a coluna antiga é substituída pela nova. Por exemplo, um `new HashTransformer("foo")` usa os valores da coluna "foo", cria um hash deles e coloca-os novamente em "foo". 

Evidentemente, qualquer transformador produz uma nova exibição de dados quando `Transform` é chamado. Lembre-se de que as exibições de dados são imutáveis.

Outra consideração importante é que, como os dados são avaliados lentamente, os *transformadores também são lentos*. Essencialmente, depois que você chama,

```csharp
var newData = transformer.Transform(oldData)
```

nenhum cálculo real ocorre. Somente depois que você obtém um cursor de `newData` e começa a consumir o valor, `newData` invoca a lógica de transformação `transformer` (e isso só ocorre se o `transformer` em questão é necessário para produzir as colunas solicitadas).

### <a name="transformer-chains"></a>Cadeias de transformador

Uma propriedade útil de um transformador é que *você pode formular um aplicativo sequencial de transformadores em outro transformador*:

```csharp
var fullTransformer = transformer1.Append(transformer2).Append(transformer3);
```

Essa propriedade normalmente é usada no ML.NET: em geral, o modelo treinado do ML.NET é uma cadeia de transformadores, que é, para todas as intenções e finalidades, um *transformador*. 

## <a name="data-reader"></a>Leitor de dados

O leitor de dados é o componente do ML.NET para 'criação' de dados: ele usa uma instância de `T` e retorna os dados dela.

Uma propriedade interessante a ser observada é que você pode criar um leitor de dados anexando um transformador a um leitor de dados existente. Dessa forma, você pode ter um leitor com o comportamento de transformação embutido:

```c#
var newReader = reader.Append(transformer1).Append(transformer2)
```

Outra similaridade com os transformadores é que, como os dados são avaliados lentamente, os *leitores são lentos*: a 'leitura' real é inexistente (ou mínima) quando você chama `dataReader.Read()`: somente quando um cursor é solicitado nos dados resultantes o leitor começa a trabalhar.

## <a name="estimator"></a>Avaliador

O *avaliador* é um objeto que aprende com os dados. O resultado do aprendizado é um *transformador*.

No ML.NET, use essa propriedade para criar pipelines de aprendizado que encadeiam diferentes avaliadores:

```csharp
MLContext mlContext = new MLContext(seed: 0);

var pipeline = new CopyColumnsEstimator(mlContext, "FareAmount", "Label")
.Append(mlContextml.Transforms.Categorical.OneHotEncoding(mlContext, "VendorId"))
.Append(mlContextml.Transforms.Categorical.OneHotEncoding(mlContext, "RateCode"))
.Append(mlContextml.Transforms.Categorical.OneHotEncoding(mlContext, "PaymentType"))
.Append(new ColumnConcatenatingEstimator(mlContext, "Features", "VendorId", "RateCode", "PassengerCount", "TripTime", "TripDistance", "PaymentType"))
.Append(mlContext.Regression.Trainers.FastTree("Label", "Features"));

var model = pipeline.Fit(dataView);
```

Uma propriedade importante dos avaliadores é que os *avaliadores são adiantados, não lentos*: todas as chamadas a `Fit` proporcionam aprendizado, o que potencialmente é uma operação demorada.

## <a name="prediction-function"></a>Função de previsão

A função de previsão pode ser vista como um computador que aplica um transformador a uma linha.

Depois que você obtém o modelo (um *transformador* treinado por meio de `Fit()` ou carregado de algum outro lugar), você pode usá-lo para fazer previsões usando as chamadas normais a `model.Transform(data)`. No entanto, quando você usa esse modelo em um cenário da vida real, você geralmente não têm muitos exemplos sobre os quais prever. Em vez disso, você tem um exemplo por vez e precisa fazer previsões em tempo hábil sobre eles imediatamente.

É claro que você pode reduzir isso à previsão em lote:

- Crie uma exibição de dados com exatamente uma linha.
- Chame `model.Transform(data)` para obter a exibição de dados prevista.
- Coloque um cursor sobre os dados resultantes.
- Avance o cursor em uma etapa para chegar à primeira (e única) linha.
- Extraia os valores previstos dela.

O algoritmo anterior pode ser implementado usando a [compreensão do esquema](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md), com dois objetos definidos pelo usuário `InputExample` e `OutputPrediction` da seguinte maneira:

```c#
var inputData = env.CreateDataView(new InputExample[] { example });
var outputData = model.Transform(inputData);
var output = outputData.AsDynamic.AsEnumerable<OutputPrediction>(env, reuseRowObject: false).Single();
```

Porém, isso é complicado e gera custos de desempenho. Em vez disso, um objeto de função de previsão faz o mesmo trabalho, porém, de maneira mais rápida e conveniente, por meio de um método de extensão `MakePredictionFunction`:

```c#
var predictionFunc = model.MakePredictionFunction<InputExample, OutputPrediction>(env);
var output = predictionFunc.Predict(example);
```

A função de previsão *não é reentrante/thread-safe*. Caso deseje realizar previsões simultaneamente com vários threads, você precisará ter uma função de previsão por thread.
