---
title: Conceitos básicos do treinamento de modelo no ML.NET
description: Este artigo explica os conceitos básicos que abrangem os cenários de *treinamento de modelo* no ML.NET. Nem todos os conceitos são relevantes para o cenário mais simples de *previsão com o modelo existente*.
ms.date: 03/05/2019
ms.topic: overview
ms.custom: mvc
ms.openlocfilehash: 78554cfd1dfdb3dba82a325d47245aeb313bb6fe
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675557"
---
# <a name="basic-concepts-for-model-training-in-mlnet"></a><span data-ttu-id="348a2-104">Conceitos básicos do treinamento de modelo no ML.NET</span><span class="sxs-lookup"><span data-stu-id="348a2-104">Basic concepts for model training in ML.NET</span></span>

<span data-ttu-id="348a2-105">Este artigo explica os conceitos básicos que abrangem os cenários de *treinamento de modelo* no ML.NET.</span><span class="sxs-lookup"><span data-stu-id="348a2-105">This article explains the basic concepts covering *model training* scenarios in ML.NET.</span></span> <span data-ttu-id="348a2-106">Nem todos os conceitos são relevantes para o cenário mais simples de *previsão com um modelo existente*.</span><span class="sxs-lookup"><span data-stu-id="348a2-106">Not all concepts are relevant to the more simple scenario of *prediction with an existing model*.</span></span>

<span data-ttu-id="348a2-107">Este artigo e a amostra relacionada estão usando o **ML.NET versão 0.10** no momento.</span><span class="sxs-lookup"><span data-stu-id="348a2-107">This article and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="348a2-108">Saiba mais nas notas de versão no [repositório do GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="348a2-108">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

## <a name="model-training-concepts"></a><span data-ttu-id="348a2-109">Conceitos de treinamento de modelo</span><span class="sxs-lookup"><span data-stu-id="348a2-109">Model training concepts</span></span>

<span data-ttu-id="348a2-110">Este documento aborda os seguintes conceitos relacionados ao treinamento de modelo no ML.NET:</span><span class="sxs-lookup"><span data-stu-id="348a2-110">This document covers the following concepts related to model training in ML.NET:</span></span>

- <span data-ttu-id="348a2-111">[*Dados*](#data) representados como uma interface `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="348a2-111">[*Data*](#data) represented as an `IDataView` interface.</span></span>
  - <span data-ttu-id="348a2-112">No ML.NET, os dados são semelhantes a uma exibição SQL: Eles são um conjunto de dados avaliados lentamente, imutáveis, cursorizáveis, heterogêneos e esquematizados.</span><span class="sxs-lookup"><span data-stu-id="348a2-112">In ML.NET, data is similar to a SQL view: It's a lazily evaluated, immutable, cursorable, heterogenous, schematized dataset.</span></span> 
  - <span data-ttu-id="348a2-113">Um documento excelente sobre a interface de dados é [Princípios de design de IDataView](https://github.com/dotnet/machinelearning/blob/master/docs/code/IDataViewDesignPrinciples.md).</span><span class="sxs-lookup"><span data-stu-id="348a2-113">An excellent document about the data interface is [IDataView Design Principles](https://github.com/dotnet/machinelearning/blob/master/docs/code/IDataViewDesignPrinciples.md).</span></span>
- <span data-ttu-id="348a2-114">[*Transformador*](#transformer) representado como a interface `ITransformer`.</span><span class="sxs-lookup"><span data-stu-id="348a2-114">[*Transformer*](#transformer) represented as `ITransformer` interface.</span></span>
  - <span data-ttu-id="348a2-115">Um transformador é um componente que usa dados, realiza algumas tarefas nele e retorna novos dados transformados.</span><span class="sxs-lookup"><span data-stu-id="348a2-115">A transformer is a component that takes data, does some work on it, and returns new transformed data.</span></span>
  - <span data-ttu-id="348a2-116">Por exemplo, você pode pensar em um modelo de machine learning como um transformador que usa funcionalidades e retorna previsões.</span><span class="sxs-lookup"><span data-stu-id="348a2-116">For example, you can think of a machine learning model as a transformer that takes features and returns predictions.</span></span>
  - <span data-ttu-id="348a2-117">Outro exemplo: um criador de token de texto usa uma única coluna de texto e gera uma coluna de vetor com palavras individuais extraídas dos textos.</span><span class="sxs-lookup"><span data-stu-id="348a2-117">Another example, text tokenizer takes a single text column and outputs a vector column with individual words extracted out of the texts.</span></span>
- <span data-ttu-id="348a2-118">[*Leitor de dados*](#data-reader) representado como uma interface `IDataReader<T>`.</span><span class="sxs-lookup"><span data-stu-id="348a2-118">[*Data reader*](#data-reader) represented as an `IDataReader<T>` interface.</span></span>
  - <span data-ttu-id="348a2-119">O leitor de dados é o componente do ML.NET para criação de dados.</span><span class="sxs-lookup"><span data-stu-id="348a2-119">The data reader is ML.NET component to create data.</span></span> <span data-ttu-id="348a2-120">Ele usa uma instância de `T` e retorna dados dela.</span><span class="sxs-lookup"><span data-stu-id="348a2-120">It takes an instance of `T` and returns data out of it.</span></span> 
  - <span data-ttu-id="348a2-121">Por exemplo, um *TextLoader* é um `IDataReader<IMultiStreamSource>`.</span><span class="sxs-lookup"><span data-stu-id="348a2-121">For example, a *TextLoader* is an `IDataReader<IMultiStreamSource>`.</span></span> <span data-ttu-id="348a2-122">Ele usa a fonte e produz dados.</span><span class="sxs-lookup"><span data-stu-id="348a2-122">It takes the source and produces data.</span></span> 
- <span data-ttu-id="348a2-123">[*Avaliador*](#estimator) representado como uma interface `IEstimator<T>`.</span><span class="sxs-lookup"><span data-stu-id="348a2-123">[*Estimator*](#estimator) represented as an `IEstimator<T>` interface.</span></span>
  - <span data-ttu-id="348a2-124">Esse é um objeto que aprende com os dados.</span><span class="sxs-lookup"><span data-stu-id="348a2-124">This is an object that learns from data.</span></span> <span data-ttu-id="348a2-125">O resultado do aprendizado é um *transformador*.</span><span class="sxs-lookup"><span data-stu-id="348a2-125">The result of the learning is a *transformer*.</span></span>
  - <span data-ttu-id="348a2-126">Você pode pensar em um *algoritmo* de aprendizado de máquina como um avaliador que aprende com os dados e produz um *modelo* de machine learning.</span><span class="sxs-lookup"><span data-stu-id="348a2-126">You can think of a machine learning *algorithm* as an estimator that learns on data and produces a machine learning *model*.</span></span>
- <span data-ttu-id="348a2-127">[*Função de previsão*](#prediction-function) representada como uma classe `PredictionEngine<TSrc, TDst>`.</span><span class="sxs-lookup"><span data-stu-id="348a2-127">[*Prediction function*](#prediction-function) represented as a `PredictionEngine<TSrc, TDst>` class.</span></span>
  - <span data-ttu-id="348a2-128">A função de previsão pode ser vista como um computador que aplica um transformador a uma linha, como no momento da previsão.</span><span class="sxs-lookup"><span data-stu-id="348a2-128">The prediction function can be seen as a machine that applies a transformer to one row, such as at prediction time.</span></span>

## <a name="data"></a><span data-ttu-id="348a2-129">Dados</span><span class="sxs-lookup"><span data-stu-id="348a2-129">Data</span></span>

<span data-ttu-id="348a2-130">No ML.NET, os dados são semelhantes a uma exibição SQL: Eles são um conjunto de dados avaliados lentamente, cursorizáveis, heterogêneos e esquematizados.</span><span class="sxs-lookup"><span data-stu-id="348a2-130">In ML.NET, data is similar to a SQL view: It's a lazily evaluated, cursorable, heterogenous, schematized dataset.</span></span>

- <span data-ttu-id="348a2-131">Eles têm um *Esquema* (uma instância de uma interface `ISchema`) que contém as informações sobre as colunas da exibição de dados.</span><span class="sxs-lookup"><span data-stu-id="348a2-131">It has *Schema* (an instance of an `ISchema` interface) that contains the information about the data view's columns.</span></span>
  - <span data-ttu-id="348a2-132">Cada coluna tem um *Nome*, um *Tipo* e um conjunto arbitrário de *metadados* associados a ela.</span><span class="sxs-lookup"><span data-stu-id="348a2-132">Each column has a *Name*, a *Type*, and an arbitrary set of *metadata* associated with it.</span></span>
  - <span data-ttu-id="348a2-133">Os *metadados* da coluna contêm informações como nomes de slot de uma coluna de vetor e similares.</span><span class="sxs-lookup"><span data-stu-id="348a2-133">The column's *metadata* contains information like slot names of a vector column and the like.</span></span> <span data-ttu-id="348a2-134">Os metadados em si são representados como outros *dados* de uma linha que são exclusivos a cada coluna.</span><span class="sxs-lookup"><span data-stu-id="348a2-134">The metadata itself is represented as another one-row *data* that is unique to each column.</span></span>
  - <span data-ttu-id="348a2-135">A exibição de dados é uma fonte de *cursores*.</span><span class="sxs-lookup"><span data-stu-id="348a2-135">The data view is a source of *cursors*.</span></span> <span data-ttu-id="348a2-136">Pense nos cursores de SQL: Um cursor é um objeto que itera pelos dados, uma linha por vez e apresenta os dados disponíveis.</span><span class="sxs-lookup"><span data-stu-id="348a2-136">Think SQL cursors: A cursor is an object that iterates through the data, one row at a time, and presents the available data.</span></span>
  - <span data-ttu-id="348a2-137">Naturalmente, os dados podem ter tantos cursores ativos neles quanto necessário.</span><span class="sxs-lookup"><span data-stu-id="348a2-137">Naturally, data can have as many active cursors over it as needed.</span></span> <span data-ttu-id="348a2-138">Como os dados em si são imutáveis, os cursores são verdadeiramente independentes.</span><span class="sxs-lookup"><span data-stu-id="348a2-138">Since data itself is immutable, cursors are truly independent.</span></span>
  - <span data-ttu-id="348a2-139">Os cursores normalmente acessam somente um subconjunto de colunas: Para eficiência, o ML.NET calcula apenas os valores das colunas que são necessárias pelo cursor.</span><span class="sxs-lookup"><span data-stu-id="348a2-139">Cursors typically access only a subset of columns: For efficiency, ML.NET computes only the values of columns that are needed by the cursor.</span></span>

## <a name="transformer"></a><span data-ttu-id="348a2-140">Transformador</span><span class="sxs-lookup"><span data-stu-id="348a2-140">Transformer</span></span>

<span data-ttu-id="348a2-141">Um transformador é um componente que usa dados, realiza algumas tarefas nele e retorna novos dados transformados.</span><span class="sxs-lookup"><span data-stu-id="348a2-141">A transformer is a component that takes data, does some work on it, and returns new transformed data.</span></span>

<span data-ttu-id="348a2-142">A maioria dos transformadores do ML.NET tende a operar em uma *coluna de entrada* por vez e produzir a *coluna de saída*.</span><span class="sxs-lookup"><span data-stu-id="348a2-142">Most transformers in ML.NET tend to operate on one *input column* at a time, and produce the *output column*.</span></span> <span data-ttu-id="348a2-143">Por exemplo, um `new HashTransformer("bar", "foo")` usa os valores da coluna "foo", cria um hash deles e coloca-os na coluna "bar".</span><span class="sxs-lookup"><span data-stu-id="348a2-143">For example, a `new HashTransformer("bar", "foo")` takes the values from column "foo", hashes them, and puts them into column "bar".</span></span> 

<span data-ttu-id="348a2-144">Também é comum que os nomes de coluna de entrada e saída sejam os mesmos.</span><span class="sxs-lookup"><span data-stu-id="348a2-144">It's also common that the input and output column names are the same.</span></span> <span data-ttu-id="348a2-145">Nesse caso, a coluna antiga é substituída pela nova.</span><span class="sxs-lookup"><span data-stu-id="348a2-145">In this case, the old column is replaced with the new one.</span></span> <span data-ttu-id="348a2-146">Por exemplo, um `new HashTransformer("foo")` usa os valores da coluna "foo", cria um hash deles e coloca-os de volta em "foo".</span><span class="sxs-lookup"><span data-stu-id="348a2-146">For example, a `new HashTransformer("foo")` takes the values from column "foo", hashes them, and puts them back into "foo".</span></span> 

<span data-ttu-id="348a2-147">Qualquer transformador produz uma nova exibição de dados quando `Transform` é chamado.</span><span class="sxs-lookup"><span data-stu-id="348a2-147">Any transformer, produces a new data view when `Transform` is called.</span></span> <span data-ttu-id="348a2-148">Lembre-se de que as exibições de dados são imutáveis.</span><span class="sxs-lookup"><span data-stu-id="348a2-148">Remember, data views are immutable.</span></span>

<span data-ttu-id="348a2-149">Outra consideração importante é que, como os dados são avaliados lentamente, os *transformadores também são lentos*.</span><span class="sxs-lookup"><span data-stu-id="348a2-149">Another important consideration is that, because data is lazily evaluated, *transformers are lazy too*.</span></span> <span data-ttu-id="348a2-150">Essencialmente, depois que você chama,</span><span class="sxs-lookup"><span data-stu-id="348a2-150">Essentially, after you call</span></span>

```csharp
var newData = transformer.Transform(oldData)
```

<span data-ttu-id="348a2-151">nenhum cálculo real ocorre.</span><span class="sxs-lookup"><span data-stu-id="348a2-151">no actual computation happens.</span></span> <span data-ttu-id="348a2-152">Somente depois que você obtém um cursor de `newData` e começa a consumir o valor, `newData` invoca a lógica de transformação `transformer` (e mesmo então, isso só ocorre se o `transformer` em questão é necessário para produzir as colunas solicitadas).</span><span class="sxs-lookup"><span data-stu-id="348a2-152">Only after you get a cursor from `newData` and start consuming the value does `newData` invoke the `transformer` transformation logic (and even then, it only happens if the `transformer` in question is needed to produce the requested columns).</span></span>

### <a name="transformer-chains"></a><span data-ttu-id="348a2-153">Cadeias de transformador</span><span class="sxs-lookup"><span data-stu-id="348a2-153">Transformer chains</span></span>

<span data-ttu-id="348a2-154">Uma propriedade útil de um transformador é que *você pode compilar um aplicativo sequencial de transformadores como um outro transformador*:</span><span class="sxs-lookup"><span data-stu-id="348a2-154">A useful property of a transformer is that *you can build a sequential application of transformers as yet another transformer*:</span></span>

```csharp
var fullTransformer = transformer1.Append(transformer2).Append(transformer3);
```

<span data-ttu-id="348a2-155">Essa propriedade normalmente é usada no ML.NET: em geral, o modelo treinado do ML.NET é uma cadeia de transformadores, que é, para todas as intenções e finalidades, um *transformador*.</span><span class="sxs-lookup"><span data-stu-id="348a2-155">This property is commonly used in ML.NET: typically, the trained ML.NET model is a chain of transformers, which is, for all intents and purposes, a *transformer*.</span></span>

## <a name="data-reader"></a><span data-ttu-id="348a2-156">Leitor de dados</span><span class="sxs-lookup"><span data-stu-id="348a2-156">Data reader</span></span>

<span data-ttu-id="348a2-157">O leitor de dados é um componente do ML.NET para 'criação' de dados: ele usa uma instância de `T` e retorna os dados dela.</span><span class="sxs-lookup"><span data-stu-id="348a2-157">The data reader is an ML.NET component to 'create' data: it takes an instance of `T` and returns data out of it.</span></span>

<span data-ttu-id="348a2-158">Uma propriedade interessante a ser observada é que você pode criar um leitor de dados anexando um transformador a um leitor de dados existente.</span><span class="sxs-lookup"><span data-stu-id="348a2-158">An interesting property to note is that you can create a data reader by attaching a transformer to an existing data reader.</span></span> <span data-ttu-id="348a2-159">Dessa forma, você pode ter um leitor com o comportamento de transformação embutido:</span><span class="sxs-lookup"><span data-stu-id="348a2-159">This way you can have a reader with transformation behavior baked in:</span></span>

```csharp
var newReader = reader.Append(transformer1).Append(transformer2)
```

<span data-ttu-id="348a2-160">Outra similaridade com os transformadores é que, como os dados são avaliados lentamente, os *leitores são lentos*: a 'leitura' real é inexistente (ou mínima) quando você chama `reader.Read()`: somente quando um cursor é solicitado nos dados resultantes o leitor começa a trabalhar.</span><span class="sxs-lookup"><span data-stu-id="348a2-160">Another similarity to transformers is that, since data is lazily evaluated, *readers are lazy*: no (or minimal) actual 'reading' happens when you call `reader.Read()`: only when a cursor is requested on the resulting data does the reader begin to work.</span></span>

## <a name="estimator"></a><span data-ttu-id="348a2-161">Avaliador</span><span class="sxs-lookup"><span data-stu-id="348a2-161">Estimator</span></span>

<span data-ttu-id="348a2-162">O *avaliador* é um objeto que aprende com os dados.</span><span class="sxs-lookup"><span data-stu-id="348a2-162">The *estimator* is an object that learns from data.</span></span> <span data-ttu-id="348a2-163">O resultado do aprendizado é um *transformador*.</span><span class="sxs-lookup"><span data-stu-id="348a2-163">The result of the learning is a *transformer*.</span></span>

<span data-ttu-id="348a2-164">No ML.NET, use essa propriedade para criar pipelines de aprendizado que encadeiam diferentes avaliadores:</span><span class="sxs-lookup"><span data-stu-id="348a2-164">In ML.NET, use this property to create learning pipelines that chain together different estimators:</span></span>

```csharp
MLContext mlContext = new MLContext(seed: 0);

var pipeline = mlContext.Transforms.CopyColumns("Label","FareAmount")
    .Append(mlContext.Transforms.Categorical.OneHotEncoding("VendorId"))
    .Append(mlContext.Transforms.Categorical.OneHotEncoding("RateCode"))
    .Append(mlContext.Transforms.Categorical.OneHotEncoding("PaymentType"))
    .Append(mlContext.Transforms.Concatenate("Features","VendorId","RateCode","PassengerCount","TripTime","TripDistance","PaymentType"))
    .Append(mlContext.Regression.Trainers.FastTree("Label","Features"));

var model = pipeline.Fit(dataView);
```

<span data-ttu-id="348a2-165">Uma propriedade importante dos avaliadores é que os *avaliadores são adiantados, não lentos*: todas as chamadas a `Fit` proporcionam aprendizado, o que potencialmente é uma operação demorada.</span><span class="sxs-lookup"><span data-stu-id="348a2-165">One important property of estimators is that *estimators are eager, not lazy*: every call to `Fit` is causing learning to happen, which is potentially a time-consuming operation.</span></span>

## <a name="prediction-function"></a><span data-ttu-id="348a2-166">Função de previsão</span><span class="sxs-lookup"><span data-stu-id="348a2-166">Prediction function</span></span>

<span data-ttu-id="348a2-167">A função de previsão pode ser vista como um componente que aplica um transformador a uma linha.</span><span class="sxs-lookup"><span data-stu-id="348a2-167">The prediction function can be seen as a component that applies a transformer to one row.</span></span>

<span data-ttu-id="348a2-168">Depois que você obtém o modelo (um *transformador* treinado por meio de `Fit()` ou carregado de algum outro lugar), você pode usá-lo para fazer previsões usando as chamadas normais a `model.Transform(data)`.</span><span class="sxs-lookup"><span data-stu-id="348a2-168">Once you get the model (a *transformer* either trained via `Fit()`, or loaded from somewhere), you can use it to make predictions using the normal calls to `model.Transform(data)`.</span></span> <span data-ttu-id="348a2-169">No entanto, quando você usa esse modelo em um cenário da vida real, você geralmente não têm muitos exemplos sobre os quais prever.</span><span class="sxs-lookup"><span data-stu-id="348a2-169">However, when you use this model in a real-life scenario, you often don't have many examples to predict on.</span></span> <span data-ttu-id="348a2-170">Em vez disso, você tem um exemplo por vez e precisa fazer previsões em tempo hábil sobre eles imediatamente.</span><span class="sxs-lookup"><span data-stu-id="348a2-170">Instead, you have one example at a time, and you need to make timely predictions on them immediately.</span></span>

<span data-ttu-id="348a2-171">É claro que você pode reduzir isso à previsão em lote:</span><span class="sxs-lookup"><span data-stu-id="348a2-171">Of course, you can reduce this to the batch prediction:</span></span>

- <span data-ttu-id="348a2-172">Crie uma exibição de dados com exatamente uma linha.</span><span class="sxs-lookup"><span data-stu-id="348a2-172">Create a data view with exactly one row.</span></span>
- <span data-ttu-id="348a2-173">Chame `model.Transform(data)` para obter a exibição de dados prevista.</span><span class="sxs-lookup"><span data-stu-id="348a2-173">Call `model.Transform(data)` to get the predicted data view.</span></span>
- <span data-ttu-id="348a2-174">Coloque um cursor sobre os dados resultantes.</span><span class="sxs-lookup"><span data-stu-id="348a2-174">Get a cursor over the resulting data.</span></span>
- <span data-ttu-id="348a2-175">Avance o cursor em uma etapa para chegar à primeira (e única) linha.</span><span class="sxs-lookup"><span data-stu-id="348a2-175">Advance the cursor one step to get to the first (and only) row.</span></span>
- <span data-ttu-id="348a2-176">Extraia os valores previstos dela.</span><span class="sxs-lookup"><span data-stu-id="348a2-176">Extract the predicted values out of it.</span></span>

<span data-ttu-id="348a2-177">O algoritmo anterior pode ser implementado usando a [compreensão do esquema](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md), com dois objetos definidos pelo usuário `InputExample` e `OutputPrediction` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="348a2-177">The preceding algorithm can be implemented using the [schema comprehension](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md), with two user-defined objects `InputExample` and `OutputPrediction` as follows:</span></span>

```csharp
var inputData = mlContext.Data.ReadFromEnumerable(new InputExample[] { example });
var outputData = model.Transform(inputData);
var output = mlContext.CreateEnumerable<OutputPrediction>(outputData,reuseRowObject:false).First();
```

<span data-ttu-id="348a2-178">Porém, isso é complicado e gera custos de desempenho.</span><span class="sxs-lookup"><span data-stu-id="348a2-178">But this is cumbersome and incurs performance costs.</span></span> <span data-ttu-id="348a2-179">Em vez disso, um objeto de função de previsão faz o mesmo trabalho, porém, de maneira mais rápida e conveniente, por meio de um método de extensão `CreatePredictionEngine`:</span><span class="sxs-lookup"><span data-stu-id="348a2-179">Instead, a prediction function object performs the same work, but faster and more convenient, via an extension method `CreatePredictionEngine`:</span></span>

```csharp
var predictionEngine = model.CreatePredictionEngine<InputExample,OutputPrediction>(mlContext);
var prediction = predictionEngine.Predict(example);
```

<span data-ttu-id="348a2-180">A função de previsão *não é reentrante/thread-safe*.</span><span class="sxs-lookup"><span data-stu-id="348a2-180">The prediction function is *not re-entrant / thread-safe*.</span></span> <span data-ttu-id="348a2-181">Caso deseje realizar previsões simultaneamente com vários threads, você precisará ter uma função de previsão por thread.</span><span class="sxs-lookup"><span data-stu-id="348a2-181">If you want to conduct predictions simultaneously with multiple threads, you need to have a prediction function per thread.</span></span>
