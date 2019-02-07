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
# <a name="basic-concepts-for-model-training-in-mlnet"></a><span data-ttu-id="a8cca-104">Conceitos básicos do treinamento de modelo no ML.NET</span><span class="sxs-lookup"><span data-stu-id="a8cca-104">Basic concepts for model training in ML.NET</span></span>

<span data-ttu-id="a8cca-105">Este artigo explica os conceitos básicos que abrangem os cenários de *treinamento de modelo* no ML.NET.</span><span class="sxs-lookup"><span data-stu-id="a8cca-105">This article explains the basic concepts covering *model training* scenarios in ML.NET.</span></span> <span data-ttu-id="a8cca-106">Nem todos os conceitos são relevantes para o cenário mais simples de *previsão com o modelo existente*.</span><span class="sxs-lookup"><span data-stu-id="a8cca-106">Not all concepts are relevant to the more simple scenario of *prediction with existing model*.</span></span>

## <a name="model-training-concepts"></a><span data-ttu-id="a8cca-107">Conceitos de treinamento de modelo</span><span class="sxs-lookup"><span data-stu-id="a8cca-107">Model training concepts</span></span>

<span data-ttu-id="a8cca-108">Este documento aborda os seguintes conceitos relacionados ao treinamento de modelo no ML.NET:</span><span class="sxs-lookup"><span data-stu-id="a8cca-108">This document covers the following concepts related to model training in ML.NET:</span></span>

- <span data-ttu-id="a8cca-109">[*Dados*](#data) representados como uma interface `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="a8cca-109">[*Data*](#data) represented as an `IDataView` interface.</span></span>
  - <span data-ttu-id="a8cca-110">No ML.NET, os dados são semelhantes a uma exibição SQL: Eles são um conjunto de dados avaliados lentamente, imutáveis, cursorizáveis, heterogêneos e esquematizados.</span><span class="sxs-lookup"><span data-stu-id="a8cca-110">In ML.NET, data is similar to a SQL view: It's a lazily evaluated, immutable, cursorable, heterogenous, schematized dataset.</span></span> 
  - <span data-ttu-id="a8cca-111">Um documento excelente sobre a interface de dados é [Princípios de design de IDataView](https://github.com/dotnet/machinelearning/blob/master/docs/code/IDataViewDesignPrinciples.md).</span><span class="sxs-lookup"><span data-stu-id="a8cca-111">An excellent document about the data interface is [IDataView Design Principles](https://github.com/dotnet/machinelearning/blob/master/docs/code/IDataViewDesignPrinciples.md).</span></span>
- <span data-ttu-id="a8cca-112">[*Transformador*](#transformer) representado como a interface `ITransformer`.</span><span class="sxs-lookup"><span data-stu-id="a8cca-112">[*Transformer*](#transformer) represented as `ITransformer` interface.</span></span>
  - <span data-ttu-id="a8cca-113">Um transformador é um componente que usa dados, realiza algumas tarefas nele e retorna novos dados transformados.</span><span class="sxs-lookup"><span data-stu-id="a8cca-113">A transformer is a component that takes data, does some work on it, and returns new transformed data.</span></span>
  - <span data-ttu-id="a8cca-114">Por exemplo, você pode pensar em um modelo de machine learning como um transformador que usa funcionalidades e retorna previsões.</span><span class="sxs-lookup"><span data-stu-id="a8cca-114">For example, you can think of a machine learning model as a transformer that takes features and returns predictions.</span></span>
  - <span data-ttu-id="a8cca-115">Outro exemplo: um criador de token de texto usa uma única coluna de texto e gera uma coluna de vetor com palavras individuais extraídas dos textos.</span><span class="sxs-lookup"><span data-stu-id="a8cca-115">Another example, text tokenizer takes a single text column and output a vector column with individual words extracted out of the texts.</span></span>
- <span data-ttu-id="a8cca-116">[*Leitor de dados*](#data-reader) representado como uma interface `IDataReader<T>`.</span><span class="sxs-lookup"><span data-stu-id="a8cca-116">[*Data reader*](#data-reader) represented as an `IDataReader<T>` interface.</span></span>
  - <span data-ttu-id="a8cca-117">O leitor de dados é o componente do ML.NET para criação de dados.</span><span class="sxs-lookup"><span data-stu-id="a8cca-117">The data reader is ML.NET component to create data.</span></span> <span data-ttu-id="a8cca-118">Ele usa uma instância de `T` e retorna dados dela.</span><span class="sxs-lookup"><span data-stu-id="a8cca-118">It takes an instance of `T` and returns data out of it.</span></span> 
  - <span data-ttu-id="a8cca-119">Por exemplo, um *TextLoader* é um `IDataReader<FileSource>`.</span><span class="sxs-lookup"><span data-stu-id="a8cca-119">For example, a *TextLoader* is an `IDataReader<FileSource>`.</span></span> <span data-ttu-id="a8cca-120">Ele usa uma fonte de arquivo e produz dados.</span><span class="sxs-lookup"><span data-stu-id="a8cca-120">It takes the file source and produces data.</span></span> 
- <span data-ttu-id="a8cca-121">[*Avaliador*](#estimator) representado como uma interface `IEstimator<T>`.</span><span class="sxs-lookup"><span data-stu-id="a8cca-121">[*Estimator*](#estimator) represented as an `IEstimator<T>` interface.</span></span>
  - <span data-ttu-id="a8cca-122">Esse é um objeto que aprende com os dados.</span><span class="sxs-lookup"><span data-stu-id="a8cca-122">This is an object that learns from data.</span></span> <span data-ttu-id="a8cca-123">O resultado do aprendizado é um *transformador*.</span><span class="sxs-lookup"><span data-stu-id="a8cca-123">The result of the learning is a *transformer*.</span></span>
  - <span data-ttu-id="a8cca-124">Você pode pensar em um *algoritmo* de aprendizado de máquina como um avaliador que aprende com os dados e produz um *modelo* de machine learning.</span><span class="sxs-lookup"><span data-stu-id="a8cca-124">You can think of a machine learning *algorithm* as an estimator that learns on data and produces a machine learning *model*.</span></span>
- <span data-ttu-id="a8cca-125">[*Função de previsão*](#prediction-function) representada como uma classe `PredictionFunction<TSrc, TDst>`.</span><span class="sxs-lookup"><span data-stu-id="a8cca-125">[*Prediction function*](#prediction-function) represented as a `PredictionFunction<TSrc, TDst>` class.</span></span>
  - <span data-ttu-id="a8cca-126">A função de previsão pode ser vista como um computador que aplica um transformador a uma linha, como no momento da previsão.</span><span class="sxs-lookup"><span data-stu-id="a8cca-126">The prediction function can be seen as a machine that applies a transformer to one row, such as at prediction time.</span></span>

## <a name="data"></a><span data-ttu-id="a8cca-127">Dados</span><span class="sxs-lookup"><span data-stu-id="a8cca-127">Data</span></span>

<span data-ttu-id="a8cca-128">No ML.NET, os dados são semelhantes a uma exibição SQL: Eles são um conjunto de dados avaliados lentamente, cursorizáveis, heterogêneos e esquematizados.</span><span class="sxs-lookup"><span data-stu-id="a8cca-128">In ML.NET, data is similar to a SQL view: It's a lazily evaluated, cursorable, heterogenous, schematized dataset.</span></span>

- <span data-ttu-id="a8cca-129">Eles têm um *Esquema* (uma instância de uma interface `ISchema`) que contém as informações sobre as colunas da exibição de dados.</span><span class="sxs-lookup"><span data-stu-id="a8cca-129">It has *Schema* (an instance of an `ISchema` interface) that contains the information about the data view's columns.</span></span>
  - <span data-ttu-id="a8cca-130">Cada coluna tem um *Nome*, um *Tipo* e um conjunto arbitrário de *metadados* associados a ela.</span><span class="sxs-lookup"><span data-stu-id="a8cca-130">Each column has a *Name*, a *Type*, and an arbitrary set of *metadata* associated with it.</span></span>
  - <span data-ttu-id="a8cca-131">Os *metadados* da coluna contêm informações como nomes de slot de uma coluna de vetor e similares.</span><span class="sxs-lookup"><span data-stu-id="a8cca-131">The column's *metadata* contains information like slot names of a vector column and the like.</span></span> <span data-ttu-id="a8cca-132">Os metadados em si são representados como outros *dados* de uma linha que são exclusivos a cada coluna.</span><span class="sxs-lookup"><span data-stu-id="a8cca-132">The metadata itself is represented as another one-row *data* that is unique to each column.</span></span>
  - <span data-ttu-id="a8cca-133">A exibição de dados é uma fonte de *cursores*.</span><span class="sxs-lookup"><span data-stu-id="a8cca-133">The data view is a source of *cursors*.</span></span> <span data-ttu-id="a8cca-134">Pense nos cursores de SQL: Um cursor é um objeto que itera pelos dados, uma linha por vez e apresenta os dados disponíveis.</span><span class="sxs-lookup"><span data-stu-id="a8cca-134">Think SQL cursors: A cursor is an object that iterates through the data, one row at a time, and presents the available data.</span></span>
  - <span data-ttu-id="a8cca-135">Naturalmente, os dados podem ter tantos cursores ativos neles quanto necessário.</span><span class="sxs-lookup"><span data-stu-id="a8cca-135">Naturally, data can have as many active cursors over it as needed.</span></span> <span data-ttu-id="a8cca-136">Como os dados em si são imutáveis, os cursores são verdadeiramente independentes.</span><span class="sxs-lookup"><span data-stu-id="a8cca-136">Since data itself is immutable, cursors are truly independent.</span></span>
  - <span data-ttu-id="a8cca-137">Os cursores normalmente acessam somente um subconjunto de colunas: Para eficiência, o ML.NET calcula apenas os valores das colunas que são necessárias pelo cursor.</span><span class="sxs-lookup"><span data-stu-id="a8cca-137">Cursors typically access only a subset of columns: For efficiency, ML.NET computes only the values of columns that are needed by the cursor.</span></span>

## <a name="transformer"></a><span data-ttu-id="a8cca-138">Transformador</span><span class="sxs-lookup"><span data-stu-id="a8cca-138">Transformer</span></span>

<span data-ttu-id="a8cca-139">Um transformador é um componente que usa dados, realiza algumas tarefas nele e retorna novos dados transformados.</span><span class="sxs-lookup"><span data-stu-id="a8cca-139">A transformer is a component that takes data, does some work on it, and return new transformed data.</span></span>

<span data-ttu-id="a8cca-140">A maioria dos transformadores do ML.NET tende a operar em uma *coluna de entrada* por vez e produzir a *coluna de saída*.</span><span class="sxs-lookup"><span data-stu-id="a8cca-140">Most transformers in ML.NET tend to operate on one *input column* at a time, and produce the *output column*.</span></span> <span data-ttu-id="a8cca-141">Por exemplo, um `new HashTransformer("foo", "bar")` usa os valores da coluna "foo", cria um hash deles e coloca-os na coluna "bar".</span><span class="sxs-lookup"><span data-stu-id="a8cca-141">For example, a `new HashTransformer("foo", "bar")` takes the values from column "foo", hash them, and put them into column "bar".</span></span> 

<span data-ttu-id="a8cca-142">Também é comum que os nomes de coluna de entrada e saída sejam os mesmos.</span><span class="sxs-lookup"><span data-stu-id="a8cca-142">It's also common that the input and output column names are the same.</span></span> <span data-ttu-id="a8cca-143">Nesse caso, a coluna antiga é substituída pela nova.</span><span class="sxs-lookup"><span data-stu-id="a8cca-143">In this case, the old column is replaced with the new one.</span></span> <span data-ttu-id="a8cca-144">Por exemplo, um `new HashTransformer("foo")` usa os valores da coluna "foo", cria um hash deles e coloca-os novamente em "foo".</span><span class="sxs-lookup"><span data-stu-id="a8cca-144">For example, a `new HashTransformer("foo")` takes the values from column "foo", hash them, and put them back into "foo".</span></span> 

<span data-ttu-id="a8cca-145">Evidentemente, qualquer transformador produz uma nova exibição de dados quando `Transform` é chamado.</span><span class="sxs-lookup"><span data-stu-id="a8cca-145">Any transformer, of course, produces a new data view when `Transform` is called.</span></span> <span data-ttu-id="a8cca-146">Lembre-se de que as exibições de dados são imutáveis.</span><span class="sxs-lookup"><span data-stu-id="a8cca-146">Remember, data views are immutable.</span></span>

<span data-ttu-id="a8cca-147">Outra consideração importante é que, como os dados são avaliados lentamente, os *transformadores também são lentos*.</span><span class="sxs-lookup"><span data-stu-id="a8cca-147">Another important consideration is that, because data is lazily evaluated, *transformers are lazy too*.</span></span> <span data-ttu-id="a8cca-148">Essencialmente, depois que você chama,</span><span class="sxs-lookup"><span data-stu-id="a8cca-148">Essentially, after you call</span></span>

```csharp
var newData = transformer.Transform(oldData)
```

<span data-ttu-id="a8cca-149">nenhum cálculo real ocorre.</span><span class="sxs-lookup"><span data-stu-id="a8cca-149">no actual computation happens.</span></span> <span data-ttu-id="a8cca-150">Somente depois que você obtém um cursor de `newData` e começa a consumir o valor, `newData` invoca a lógica de transformação `transformer` (e isso só ocorre se o `transformer` em questão é necessário para produzir as colunas solicitadas).</span><span class="sxs-lookup"><span data-stu-id="a8cca-150">Only after you get a cursor from `newData` and start consuming the value does `newData` invoke the `transformer` transformation logic (and even that only if `transformer` in question is needed to produce the requested columns).</span></span>

### <a name="transformer-chains"></a><span data-ttu-id="a8cca-151">Cadeias de transformador</span><span class="sxs-lookup"><span data-stu-id="a8cca-151">Transformer chains</span></span>

<span data-ttu-id="a8cca-152">Uma propriedade útil de um transformador é que *você pode formular um aplicativo sequencial de transformadores em outro transformador*:</span><span class="sxs-lookup"><span data-stu-id="a8cca-152">A useful property of a transformer is that *you can phrase a sequential application of transformers as yet another transformer*:</span></span>

```csharp
var fullTransformer = transformer1.Append(transformer2).Append(transformer3);
```

<span data-ttu-id="a8cca-153">Essa propriedade normalmente é usada no ML.NET: em geral, o modelo treinado do ML.NET é uma cadeia de transformadores, que é, para todas as intenções e finalidades, um *transformador*.</span><span class="sxs-lookup"><span data-stu-id="a8cca-153">This property is commonly used in ML.NET: typically, the trained ML.NET model is a chain of transformers, which is, for all intents and purposes, a *transformer*.</span></span> 

## <a name="data-reader"></a><span data-ttu-id="a8cca-154">Leitor de dados</span><span class="sxs-lookup"><span data-stu-id="a8cca-154">Data reader</span></span>

<span data-ttu-id="a8cca-155">O leitor de dados é o componente do ML.NET para 'criação' de dados: ele usa uma instância de `T` e retorna os dados dela.</span><span class="sxs-lookup"><span data-stu-id="a8cca-155">The data reader is ML.NET component to 'create' data: it takes an instance of `T` and returns data out of it.</span></span>

<span data-ttu-id="a8cca-156">Uma propriedade interessante a ser observada é que você pode criar um leitor de dados anexando um transformador a um leitor de dados existente.</span><span class="sxs-lookup"><span data-stu-id="a8cca-156">An interesting property to note is that you can create a data reader by attaching a transformer to an existing data reader.</span></span> <span data-ttu-id="a8cca-157">Dessa forma, você pode ter um leitor com o comportamento de transformação embutido:</span><span class="sxs-lookup"><span data-stu-id="a8cca-157">This way you can have a reader with transformation behavior baked in:</span></span>

```c#
var newReader = reader.Append(transformer1).Append(transformer2)
```

<span data-ttu-id="a8cca-158">Outra similaridade com os transformadores é que, como os dados são avaliados lentamente, os *leitores são lentos*: a 'leitura' real é inexistente (ou mínima) quando você chama `dataReader.Read()`: somente quando um cursor é solicitado nos dados resultantes o leitor começa a trabalhar.</span><span class="sxs-lookup"><span data-stu-id="a8cca-158">Another similarity to transformers is that, since data is lazily evaluated, *readers are lazy*: no (or minimal) actual 'reading' happens when you call `dataReader.Read()`: only when a cursor is requested on the resulting data does the reader begin to work.</span></span>

## <a name="estimator"></a><span data-ttu-id="a8cca-159">Avaliador</span><span class="sxs-lookup"><span data-stu-id="a8cca-159">Estimator</span></span>

<span data-ttu-id="a8cca-160">O *avaliador* é um objeto que aprende com os dados.</span><span class="sxs-lookup"><span data-stu-id="a8cca-160">The *estimator* is an object that learns from data.</span></span> <span data-ttu-id="a8cca-161">O resultado do aprendizado é um *transformador*.</span><span class="sxs-lookup"><span data-stu-id="a8cca-161">The result of the learning is a *transformer*.</span></span>

<span data-ttu-id="a8cca-162">No ML.NET, use essa propriedade para criar pipelines de aprendizado que encadeiam diferentes avaliadores:</span><span class="sxs-lookup"><span data-stu-id="a8cca-162">In ML.NET, use this property to create learning pipelines that chain together different estimators:</span></span>

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

<span data-ttu-id="a8cca-163">Uma propriedade importante dos avaliadores é que os *avaliadores são adiantados, não lentos*: todas as chamadas a `Fit` proporcionam aprendizado, o que potencialmente é uma operação demorada.</span><span class="sxs-lookup"><span data-stu-id="a8cca-163">One important property of estimators is that *estimators are eager, not lazy*: every call to `Fit` is causing learning to happen, which is potentially a time-consuming operation.</span></span>

## <a name="prediction-function"></a><span data-ttu-id="a8cca-164">Função de previsão</span><span class="sxs-lookup"><span data-stu-id="a8cca-164">Prediction function</span></span>

<span data-ttu-id="a8cca-165">A função de previsão pode ser vista como um computador que aplica um transformador a uma linha.</span><span class="sxs-lookup"><span data-stu-id="a8cca-165">The prediction function can be seen as a machine that applies a transformer to one row.</span></span>

<span data-ttu-id="a8cca-166">Depois que você obtém o modelo (um *transformador* treinado por meio de `Fit()` ou carregado de algum outro lugar), você pode usá-lo para fazer previsões usando as chamadas normais a `model.Transform(data)`.</span><span class="sxs-lookup"><span data-stu-id="a8cca-166">Once you get the model (a *transformer* either trained via `Fit()`, or loaded from somewhere), you can use it to make predictions using the normal calls to `model.Transform(data)`.</span></span> <span data-ttu-id="a8cca-167">No entanto, quando você usa esse modelo em um cenário da vida real, você geralmente não têm muitos exemplos sobre os quais prever.</span><span class="sxs-lookup"><span data-stu-id="a8cca-167">However, when you use this model in a real-life scenario, you often don't have many examples to predict on.</span></span> <span data-ttu-id="a8cca-168">Em vez disso, você tem um exemplo por vez e precisa fazer previsões em tempo hábil sobre eles imediatamente.</span><span class="sxs-lookup"><span data-stu-id="a8cca-168">Instead, you have one example at a time, and you need to make timely predictions on them immediately.</span></span>

<span data-ttu-id="a8cca-169">É claro que você pode reduzir isso à previsão em lote:</span><span class="sxs-lookup"><span data-stu-id="a8cca-169">Of course, you can reduce this to the batch prediction:</span></span>

- <span data-ttu-id="a8cca-170">Crie uma exibição de dados com exatamente uma linha.</span><span class="sxs-lookup"><span data-stu-id="a8cca-170">Create a data view with exactly one row.</span></span>
- <span data-ttu-id="a8cca-171">Chame `model.Transform(data)` para obter a exibição de dados prevista.</span><span class="sxs-lookup"><span data-stu-id="a8cca-171">Call `model.Transform(data)` to get the predicted data view.</span></span>
- <span data-ttu-id="a8cca-172">Coloque um cursor sobre os dados resultantes.</span><span class="sxs-lookup"><span data-stu-id="a8cca-172">Get a cursor over the resulting data.</span></span>
- <span data-ttu-id="a8cca-173">Avance o cursor em uma etapa para chegar à primeira (e única) linha.</span><span class="sxs-lookup"><span data-stu-id="a8cca-173">Advance the cursor one step to get to the first (and only) row.</span></span>
- <span data-ttu-id="a8cca-174">Extraia os valores previstos dela.</span><span class="sxs-lookup"><span data-stu-id="a8cca-174">Extract the predicted values out of it.</span></span>

<span data-ttu-id="a8cca-175">O algoritmo anterior pode ser implementado usando a [compreensão do esquema](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md), com dois objetos definidos pelo usuário `InputExample` e `OutputPrediction` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="a8cca-175">The preceding algorithm can be implemented using the [schema comprehension](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md), with two user-defined objects `InputExample` and `OutputPrediction` as follows:</span></span>

```c#
var inputData = env.CreateDataView(new InputExample[] { example });
var outputData = model.Transform(inputData);
var output = outputData.AsDynamic.AsEnumerable<OutputPrediction>(env, reuseRowObject: false).Single();
```

<span data-ttu-id="a8cca-176">Porém, isso é complicado e gera custos de desempenho.</span><span class="sxs-lookup"><span data-stu-id="a8cca-176">But this is cumbersome and incurs performance costs.</span></span> <span data-ttu-id="a8cca-177">Em vez disso, um objeto de função de previsão faz o mesmo trabalho, porém, de maneira mais rápida e conveniente, por meio de um método de extensão `MakePredictionFunction`:</span><span class="sxs-lookup"><span data-stu-id="a8cca-177">Instead, a prediction function object performs the same work, but faster and more convenient, via an extension method `MakePredictionFunction`:</span></span>

```c#
var predictionFunc = model.MakePredictionFunction<InputExample, OutputPrediction>(env);
var output = predictionFunc.Predict(example);
```

<span data-ttu-id="a8cca-178">A função de previsão *não é reentrante/thread-safe*.</span><span class="sxs-lookup"><span data-stu-id="a8cca-178">The prediction function is *not re-entrant / thread-safe*.</span></span> <span data-ttu-id="a8cca-179">Caso deseje realizar previsões simultaneamente com vários threads, você precisará ter uma função de previsão por thread.</span><span class="sxs-lookup"><span data-stu-id="a8cca-179">If you want to conduct predictions simultaneously with multiple threads, you need to have a prediction function per thread.</span></span>
