---
title: O que é ML.NET e como ele funciona?
description: O ML.NET oferece a capacidade de adicionar aprendizado de máquina a aplicativos .NET, em cenários online ou offline. Com essa funcionalidade, você pode fazer previsões automáticas usando os dados disponíveis para o aplicativo sem precisar estar conectado a uma rede para usar o ML.NET. Este artigo explica os conceitos básicos do aprendizado de máquina em ML.NET.
ms.date: 11/5/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
author: natke
ms.openlocfilehash: 5d8093c77799a55f4bc13e82c06c856dbb8d85cd
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976732"
---
# <a name="what-is-mlnet-and-how-does-it-work"></a><span data-ttu-id="c266e-105">O que é ML.NET e como ele funciona?</span><span class="sxs-lookup"><span data-stu-id="c266e-105">What is ML.NET and how does it work?</span></span>

<span data-ttu-id="c266e-106">O ML.NET oferece a capacidade de adicionar aprendizado de máquina a aplicativos .NET, em cenários online ou offline.</span><span class="sxs-lookup"><span data-stu-id="c266e-106">ML.NET gives you the ability to add machine learning to .NET applications, in either online or offline scenarios.</span></span> <span data-ttu-id="c266e-107">Com essa funcionalidade, você pode fazer previsões automáticas usando os dados disponíveis ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c266e-107">With this capability, you can make automatic predictions using the data available to your application.</span></span>

<span data-ttu-id="c266e-108">Central para o ML.NET é um **modelo**de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="c266e-108">Central to ML.NET is a machine learning **model**.</span></span> <span data-ttu-id="c266e-109">O modelo especifica as etapas necessárias para transformar os dados de entrada em uma previsão.</span><span class="sxs-lookup"><span data-stu-id="c266e-109">The model specifies the steps needed to transform your input data into a prediction.</span></span> <span data-ttu-id="c266e-110">Com o ML.NET, você pode treinar um modelo personalizado especificando um algoritmo ou pode importar modelos TensorFlow e ONNX pré-treinados.</span><span class="sxs-lookup"><span data-stu-id="c266e-110">With ML.NET, you can train a custom model by specifying an algorithm, or you can import pre-trained TensorFlow and ONNX models.</span></span>

<span data-ttu-id="c266e-111">Depois de ter um modelo, você pode adicioná-lo ao seu aplicativo para fazer as previsões.</span><span class="sxs-lookup"><span data-stu-id="c266e-111">Once you have a model, you can add it to your application to make the predictions.</span></span>

<span data-ttu-id="c266e-112">O ML.NET é executado no Windows, no Linux e no macOS usando o .NET Core ou o Windows usando .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c266e-112">ML.NET runs on Windows, Linux, and macOS using .NET Core, or Windows using .NET Framework.</span></span> <span data-ttu-id="c266e-113">Há suporte para 64 bits em todas as plataformas.</span><span class="sxs-lookup"><span data-stu-id="c266e-113">64 bit is supported on all platforms.</span></span> <span data-ttu-id="c266e-114">Há suporte para 32 bits no Windows, exceto para a funcionalidade relacionada TensorFlow, LightGBM e ONNX.</span><span class="sxs-lookup"><span data-stu-id="c266e-114">32 bit is supported on Windows, except for TensorFlow, LightGBM, and ONNX related functionality.</span></span>

<span data-ttu-id="c266e-115">Exemplos do tipo de previsões que você pode fazer com ML.NET:</span><span class="sxs-lookup"><span data-stu-id="c266e-115">Examples of the type of predictions that you can make with ML.NET:</span></span>

|||
|-|-|
|<span data-ttu-id="c266e-116">Classificação/Categorização</span><span class="sxs-lookup"><span data-stu-id="c266e-116">Classification/Categorization</span></span>|<span data-ttu-id="c266e-117">Dividir automaticamente os comentários dos clientes em categorias positivas e negativas</span><span class="sxs-lookup"><span data-stu-id="c266e-117">Automatically divide customer feedback into positive and negative categories</span></span>|
|<span data-ttu-id="c266e-118">Regressão/Prever valores contínuos</span><span class="sxs-lookup"><span data-stu-id="c266e-118">Regression/Predict continuous values</span></span>|<span data-ttu-id="c266e-119">Prever o preço de residências com base em tamanho e local</span><span class="sxs-lookup"><span data-stu-id="c266e-119">Predict the price of houses based on size and location</span></span>|
|<span data-ttu-id="c266e-120">Detecção de Anomalias</span><span class="sxs-lookup"><span data-stu-id="c266e-120">Anomaly Detection</span></span>|<span data-ttu-id="c266e-121">Detectar transações bancárias fraudulentas</span><span class="sxs-lookup"><span data-stu-id="c266e-121">Detect fraudulent banking transactions</span></span> |
|<span data-ttu-id="c266e-122">Recomendações</span><span class="sxs-lookup"><span data-stu-id="c266e-122">Recommendations</span></span>|<span data-ttu-id="c266e-123">Sugerir produtos que compradores online talvez queiram comprar com base em suas compras anteriores</span><span class="sxs-lookup"><span data-stu-id="c266e-123">Suggest products that online shoppers may want to buy, based on their previous purchases</span></span>|
|<span data-ttu-id="c266e-124">Série temporal/dados sequenciais</span><span class="sxs-lookup"><span data-stu-id="c266e-124">Time series/sequential data</span></span>|<span data-ttu-id="c266e-125">Prever as vendas do clima/produto</span><span class="sxs-lookup"><span data-stu-id="c266e-125">Forecast the weather/product sales</span></span>|
|<span data-ttu-id="c266e-126">Classificação de imagem</span><span class="sxs-lookup"><span data-stu-id="c266e-126">Image classification</span></span>|<span data-ttu-id="c266e-127">Categorizar patologias em imagens médicas</span><span class="sxs-lookup"><span data-stu-id="c266e-127">Categorize pathologies in medical images</span></span>|

## <a name="hello-mlnet-world"></a><span data-ttu-id="c266e-128">Olá, Mundo do ML.NET</span><span class="sxs-lookup"><span data-stu-id="c266e-128">Hello ML.NET World</span></span>

<span data-ttu-id="c266e-129">O código no snippet a seguir demonstra o aplicativo do ML.NET mais simples.</span><span class="sxs-lookup"><span data-stu-id="c266e-129">The code in the following snippet demonstrates the simplest ML.NET application.</span></span> <span data-ttu-id="c266e-130">Este exemplo cria um modelo de regressão linear para prever os preços de residências usando dados de tamanho e preço de residências.</span><span class="sxs-lookup"><span data-stu-id="c266e-130">This example constructs a linear regression model to predict house prices using house size and price data.</span></span> 

 ```csharp
    using System;
    using Microsoft.ML;
    using Microsoft.ML.Data;

    class Program
    {
        public class HouseData
        {
            public float Size { get; set; }
            public float Price { get; set; }
        }

        public class Prediction
        {
            [ColumnName("Score")]
            public float Price { get; set; }
        }

        static void Main(string[] args)
        {
            MLContext mlContext = new MLContext();

            // 1. Import or create training data
            HouseData[] houseData = {
                new HouseData() { Size = 1.1F, Price = 1.2F },
                new HouseData() { Size = 1.9F, Price = 2.3F },
                new HouseData() { Size = 2.8F, Price = 3.0F },
                new HouseData() { Size = 3.4F, Price = 3.7F } };
            IDataView trainingData = mlContext.Data.LoadFromEnumerable(houseData);

            // 2. Specify data preparation and model training pipeline
            var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
                .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));

            // 3. Train model
            var model = pipeline.Fit(trainingData);

            // 4. Make a prediction
            var size = new HouseData() { Size = 2.5F };
            var price = mlContext.Model.CreatePredictionEngine<HouseData, Prediction>(model).Predict(size);

            Console.WriteLine($"Predicted price for size: {size.Size*1000} sq ft= {price.Price*100:C}k");

            // Predicted price for size: 2500 sq ft= $261.98k
        }
    }
```

## <a name="code-workflow"></a><span data-ttu-id="c266e-131">Fluxo de trabalho de código</span><span class="sxs-lookup"><span data-stu-id="c266e-131">Code workflow</span></span>

<span data-ttu-id="c266e-132">O diagrama a seguir representa a estrutura de código do aplicativo, bem como o processo iterativo de desenvolvimento do modelo:</span><span class="sxs-lookup"><span data-stu-id="c266e-132">The following diagram represents the application code structure, as well as the iterative process of model development:</span></span>

- <span data-ttu-id="c266e-133">Coletar e carregar dados de treinamento em um objeto **IDataView**</span><span class="sxs-lookup"><span data-stu-id="c266e-133">Collect and load training data into an **IDataView** object</span></span>
- <span data-ttu-id="c266e-134">It makes sense to keep as infinitive in replace of the imperative.</span><span class="sxs-lookup"><span data-stu-id="c266e-134">Specify a pipeline of operations to extract features and apply a machine learning algorithm</span></span>
- <span data-ttu-id="c266e-135">Treinar um modelo chamando **Fit()** no pipeline</span><span class="sxs-lookup"><span data-stu-id="c266e-135">Train a model by calling **Fit()** on the pipeline</span></span>
- <span data-ttu-id="c266e-136">Avaliar o modelo e iterar para melhorar</span><span class="sxs-lookup"><span data-stu-id="c266e-136">Evaluate the model and iterate to improve</span></span>
- <span data-ttu-id="c266e-137">Salvar o modelo em um formato binário para uso em um aplicativo</span><span class="sxs-lookup"><span data-stu-id="c266e-137">Save the model into binary format, for use in an application</span></span>
- <span data-ttu-id="c266e-138">Carregar o modelo de volta para um objeto **ITransformer**</span><span class="sxs-lookup"><span data-stu-id="c266e-138">Load the model back into an **ITransformer** object</span></span>
- <span data-ttu-id="c266e-139">Fazer previsões chamando **CreatePredictionEngine.Predict()**</span><span class="sxs-lookup"><span data-stu-id="c266e-139">Make predictions by calling **CreatePredictionEngine.Predict()**</span></span>

![Fluxo de desenvolvimento de aplicativo do ML.NET incluindo componentes para geração de dados, desenvolvimento de pipeline, treinamento do modelo, avaliação de modelo e uso do modelo](./media/mldotnet-annotated-workflow.png)

<span data-ttu-id="c266e-141">Vamos nos aprofundar um pouco mais nesses conceitos.</span><span class="sxs-lookup"><span data-stu-id="c266e-141">Let's dig a little deeper into those concepts.</span></span>

## <a name="machine-learning-model"></a><span data-ttu-id="c266e-142">Suggestion Accepted</span><span class="sxs-lookup"><span data-stu-id="c266e-142">Machine learning model</span></span>

<span data-ttu-id="c266e-143">Um modelo do ML.NET é um objeto que contém transformações para executar em seus dados de entrada para chegar na saída prevista.</span><span class="sxs-lookup"><span data-stu-id="c266e-143">An ML.NET model is an object that contains transformations to perform on your input data to arrive at the predicted output.</span></span>

### <a name="basic"></a><span data-ttu-id="c266e-144">Suggestion Accepted</span><span class="sxs-lookup"><span data-stu-id="c266e-144">Basic</span></span>

<span data-ttu-id="c266e-145">O modelo mais básico é regressão linear bidimensional, em que uma quantidade contínua é proporcional a outro, como no exemplo de preço de residência acima.</span><span class="sxs-lookup"><span data-stu-id="c266e-145">The most basic model is two-dimensional linear regression, where one continuous quantity is proportional to another, as in the house price example above.</span></span>

![Modelo de regressão linear com os parâmetros de peso e desvio](./media/linear-regression-model.svg)

<span data-ttu-id="c266e-147">O modelo é simplesmente: $Price = b + Size \* w$.</span><span class="sxs-lookup"><span data-stu-id="c266e-147">The model is simply: $Price = b + Size \* w$.</span></span> <span data-ttu-id="c266e-148">Os parâmetros $b$ e $w$ são estimados ajustando uma linha em um conjunto de pares (tamanho, preço).</span><span class="sxs-lookup"><span data-stu-id="c266e-148">The parameters $b$ and $w$ are estimated by fitting a line on a set of (size, price) pairs.</span></span> <span data-ttu-id="c266e-149">Os dados usados para localizar os parâmetros do modelo são chamados **dados de treinamento**.</span><span class="sxs-lookup"><span data-stu-id="c266e-149">The data used to find the parameters of the model is called **training data**.</span></span> <span data-ttu-id="c266e-150">As entradas de um modelo de machine learning são chamadas de **recursos**.</span><span class="sxs-lookup"><span data-stu-id="c266e-150">The inputs of a machine learning model are called **features**.</span></span> <span data-ttu-id="c266e-151">Neste exemplo, $Size$ é o único recurso.</span><span class="sxs-lookup"><span data-stu-id="c266e-151">In this example, $Size$ is the only feature.</span></span> <span data-ttu-id="c266e-152">Os valores de zero verdadeiro usados para treinar um modelo de machine learning são chamados de **rótulos**.</span><span class="sxs-lookup"><span data-stu-id="c266e-152">The ground-truth values used to train a machine learning model are called **labels**.</span></span> <span data-ttu-id="c266e-153">Aqui, os valores de $Price$ no conjunto de dados de treinamento são os rótulos.</span><span class="sxs-lookup"><span data-stu-id="c266e-153">Here, the $Price$ values in the training data set are the labels.</span></span>

### <a name="more-complex"></a><span data-ttu-id="c266e-154">Mais complexo</span><span class="sxs-lookup"><span data-stu-id="c266e-154">More complex</span></span>

<span data-ttu-id="c266e-155">Um modelo mais complexo classifica as transações financeiras em categorias usando a descrição de texto de transação.</span><span class="sxs-lookup"><span data-stu-id="c266e-155">A more complex model classifies financial transactions into categories using the transaction text description.</span></span>

<span data-ttu-id="c266e-156">Cada descrição de transação é dividida em um conjunto de recursos removendo caracteres e palavras redundantes e contando combinações de palavras e caracteres.</span><span class="sxs-lookup"><span data-stu-id="c266e-156">Each transaction description is broken down into a set of features by removing redundant words and characters, and counting word and character combinations.</span></span> <span data-ttu-id="c266e-157">O conjunto de recursos é usado para treinar um modelo linear com base no conjunto de categorias nos dados de treinamento.</span><span class="sxs-lookup"><span data-stu-id="c266e-157">The feature set is used to train a linear model based on the set of categories in the training data.</span></span> <span data-ttu-id="c266e-158">Quanto mais semelhante uma nova descrição é daquelas no conjunto de treinamento, mais provavelmente ela será atribuída à mesma categoria.</span><span class="sxs-lookup"><span data-stu-id="c266e-158">The more similar a new description is to the ones in the training set, the more likely it will be assigned to the same category.</span></span>

![Modelo de Classificação de Texto](./media/text-classification-model.svg)

<span data-ttu-id="c266e-160">Os modelos de preço de residência e o modelo de classificação de texto são modelos **lineares**.</span><span class="sxs-lookup"><span data-stu-id="c266e-160">Both the house price model and the text classification model are **linear** models.</span></span> <span data-ttu-id="c266e-161">Dependendo da natureza de seus dados e do problema que você está resolvendo, você também pode usar modelos de **árvore de decisão**, modelos **aditivos generalizados** e outros.</span><span class="sxs-lookup"><span data-stu-id="c266e-161">Depending on the nature of your data and the problem you are solving, you can also use **decision tree** models, **generalized additive** models, and others.</span></span> <span data-ttu-id="c266e-162">Você pode encontrar mais informações sobre os modelos em [Tarefas](./resources/tasks.md).</span><span class="sxs-lookup"><span data-stu-id="c266e-162">You can find out more about the models in [Tasks](./resources/tasks.md).</span></span>

## <a name="data-preparation"></a><span data-ttu-id="c266e-163">Preparação de dados</span><span class="sxs-lookup"><span data-stu-id="c266e-163">Data preparation</span></span>

<span data-ttu-id="c266e-164">Na maioria dos casos, os dados que você tem disponíveis não são adequados para serem usados diretamente para treinar um modelo de machine learning.</span><span class="sxs-lookup"><span data-stu-id="c266e-164">In most cases, the data that you have available isn't suitable to be used directly to train a machine learning model.</span></span> <span data-ttu-id="c266e-165">Os dados brutos precisam ser preparados ou previamente processados antes de poderem ser usados para localizar os parâmetros do seu modelo.</span><span class="sxs-lookup"><span data-stu-id="c266e-165">The raw data needs to be prepared, or pre-processed before it can be used to find the parameters of your model.</span></span> <span data-ttu-id="c266e-166">Seus dados talvez precisem ser convertidos de valores de cadeia de caracteres em uma representação numérica.</span><span class="sxs-lookup"><span data-stu-id="c266e-166">Your data may need to be converted from string values to a numerical representation.</span></span> <span data-ttu-id="c266e-167">Você pode ter informações redundantes em seus dados de entrada.</span><span class="sxs-lookup"><span data-stu-id="c266e-167">You might have redundant information in your input data.</span></span> <span data-ttu-id="c266e-168">Talvez você precise reduzir ou expandir as dimensões de seus dados de entrada.</span><span class="sxs-lookup"><span data-stu-id="c266e-168">You may need to reduce or expand the dimensions of your input data.</span></span> <span data-ttu-id="c266e-169">Seus dados talvez precisem ser normalizados ou dimensionados.</span><span class="sxs-lookup"><span data-stu-id="c266e-169">Your data might need to be normalized or scaled.</span></span>

<span data-ttu-id="c266e-170">Os [tutoriais do ML.NET](./tutorials/index.md) ensinam a você sobre os diferentes pipelines de processamento de dados para texto, imagem, dados numéricos e de série temporal usados para tarefas de aprendizado de máquina específicas.</span><span class="sxs-lookup"><span data-stu-id="c266e-170">The [ML.NET tutorials](./tutorials/index.md) teach you about different data processing pipelines for text, image, numerical, and time-series data used for specific machine learning tasks.</span></span>

<span data-ttu-id="c266e-171">Accepted the correction</span><span class="sxs-lookup"><span data-stu-id="c266e-171">[How to prepare your data](./how-to-guides/prepare-data-ml-net.md) shows you how to applied data preparation more generally.</span></span>

<span data-ttu-id="c266e-172">Você pode encontrar um apêndice de todas as [transformações disponíveis](./resources/transforms.md) na seção de recursos.</span><span class="sxs-lookup"><span data-stu-id="c266e-172">You can find an appendix of all of the [available transformations](./resources/transforms.md) in the resources section.</span></span>

## <a name="model-evaluation"></a><span data-ttu-id="c266e-173">Avaliação do modelo</span><span class="sxs-lookup"><span data-stu-id="c266e-173">Model evaluation</span></span>

<span data-ttu-id="c266e-174">Depois de treinar seu modelo, como você sabe o quão bem ele fará previsões futuras?</span><span class="sxs-lookup"><span data-stu-id="c266e-174">Once you have trained your model, how do you know how well it will make future predictions?</span></span> <span data-ttu-id="c266e-175">Com o do ML.NET, você pode avaliar seu modelo em relação a alguns novos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="c266e-175">With ML.NET, you can evaluate your model against some new test data.</span></span>

<span data-ttu-id="c266e-176">Cada tipo de tarefa de aprendizado de máquina tem métricas usadas para avaliar a precisão e a exatidão do modelo em relação ao conjunto de dados de teste.</span><span class="sxs-lookup"><span data-stu-id="c266e-176">Each type of machine learning task has metrics used to evaluate the accuracy and precision of the model against the test data set.</span></span>

<span data-ttu-id="c266e-177">Para nosso exemplo de preço de residência, usamos a tarefa **Regressão**.</span><span class="sxs-lookup"><span data-stu-id="c266e-177">For our house price example, we used the **Regression** task.</span></span> <span data-ttu-id="c266e-178">Para avaliar o modelo, adicione o seguinte código à amostra original.</span><span class="sxs-lookup"><span data-stu-id="c266e-178">To evaluate the model, add the following code to the original sample.</span></span>

```csharp
        HouseData[] testHouseData =
        {
            new HouseData() { Size = 1.1F, Price = 0.98F },
            new HouseData() { Size = 1.9F, Price = 2.1F },
            new HouseData() { Size = 2.8F, Price = 2.9F },
            new HouseData() { Size = 3.4F, Price = 3.6F }
        };

        var testHouseDataView = mlContext.Data.LoadFromEnumerable(testHouseData);
        var testPriceDataView = model.Transform(testHouseDataView);

        var metrics = mlContext.Regression.Evaluate(testPriceDataView, labelColumnName: "Price");

        Console.WriteLine($"R^2: {metrics.RSquared:0.##}");
        Console.WriteLine($"RMS error: {metrics.RootMeanSquaredError:0.##}");

        // R^2: 0.96
        // RMS error: 0.19
```

<span data-ttu-id="c266e-179">As métricas de avaliação dizem que o erro é mais ou menos baixo. Essa correlação entre a saída prevista e a saída do teste é alta.</span><span class="sxs-lookup"><span data-stu-id="c266e-179">The evaluation metrics tell you that the error is low-ish, and that correlation between the predicted output and the test output is high.</span></span> <span data-ttu-id="c266e-180">Isso foi fácil.</span><span class="sxs-lookup"><span data-stu-id="c266e-180">That was easy!</span></span> <span data-ttu-id="c266e-181">Em exemplos reais, é necessário mais ajuste para obter métricas de modelo válidas.</span><span class="sxs-lookup"><span data-stu-id="c266e-181">In real examples, it takes more tuning to achieve good model metrics.</span></span>

## <a name="mlnet-architecture"></a><span data-ttu-id="c266e-182">Arquitetura do ML.NET</span><span class="sxs-lookup"><span data-stu-id="c266e-182">ML.NET architecture</span></span>

<span data-ttu-id="c266e-183">Nesta seção, vamos repassar os padrões de arquitetura do ML.NET.</span><span class="sxs-lookup"><span data-stu-id="c266e-183">In this section, we go through the architectural patterns of ML.NET.</span></span> <span data-ttu-id="c266e-184">Se você for um desenvolvedor .NET experiente, alguns destes padrões serão familiares, enquanto outros serão menos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="c266e-184">If you are an experienced .NET developer, some of these patterns will be familiar to you, and some will be less familiar.</span></span> <span data-ttu-id="c266e-185">Mantenha o foco enquanto nos aprofundamos.</span><span class="sxs-lookup"><span data-stu-id="c266e-185">Hold tight, while we dive in!</span></span>

<span data-ttu-id="c266e-186">Um aplicativo do ML.NET começa com um objeto <xref:Microsoft.ML.MLContext>.</span><span class="sxs-lookup"><span data-stu-id="c266e-186">An ML.NET application starts with an <xref:Microsoft.ML.MLContext> object.</span></span> <span data-ttu-id="c266e-187">Esse objeto singleton contém **catálogos**.</span><span class="sxs-lookup"><span data-stu-id="c266e-187">This singleton object contains **catalogs**.</span></span> <span data-ttu-id="c266e-188">Um catálogo é uma fábrica para carregar e salvar dados, componentes de operação de modelo, treinadores e transformações.</span><span class="sxs-lookup"><span data-stu-id="c266e-188">A catalog is a factory for data loading and saving, transforms, trainers, and model operation components.</span></span> <span data-ttu-id="c266e-189">Cada objeto de catálogo tem métodos para criar os diferentes tipos de componentes:</span><span class="sxs-lookup"><span data-stu-id="c266e-189">Each catalog object has methods to create the different types of components:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="c266e-190">Salvamento e carregamento de dados</span><span class="sxs-lookup"><span data-stu-id="c266e-190">Data loading and saving</span></span>||<xref:Microsoft.ML.DataOperationsCatalog>||
|<span data-ttu-id="c266e-191">Preparação de dados</span><span class="sxs-lookup"><span data-stu-id="c266e-191">Data preparation</span></span>||<xref:Microsoft.ML.TransformsCatalog>||
|<span data-ttu-id="c266e-192">Treinando algoritmos</span><span class="sxs-lookup"><span data-stu-id="c266e-192">Training algorithms</span></span>|<span data-ttu-id="c266e-193">Classificação binária</span><span class="sxs-lookup"><span data-stu-id="c266e-193">Binary classification</span></span>|<xref:Microsoft.ML.BinaryClassificationCatalog>||
||<span data-ttu-id="c266e-194">Classificação multiclasse</span><span class="sxs-lookup"><span data-stu-id="c266e-194">Multiclass classification</span></span>|<xref:Microsoft.ML.MulticlassClassificationCatalog>||
||<span data-ttu-id="c266e-195">Detecção de anomalias</span><span class="sxs-lookup"><span data-stu-id="c266e-195">Anomaly detection</span></span>|<xref:Microsoft.ML.AnomalyDetectionCatalog>||
||<span data-ttu-id="c266e-196">Clustering</span><span class="sxs-lookup"><span data-stu-id="c266e-196">Clustering</span></span>|<xref:Microsoft.ML.ClusteringCatalog>||
||<span data-ttu-id="c266e-197">Previsão</span><span class="sxs-lookup"><span data-stu-id="c266e-197">Forecasting</span></span>|<xref:Microsoft.ML.ForecastingCatalog>||
||<span data-ttu-id="c266e-198">Classificação</span><span class="sxs-lookup"><span data-stu-id="c266e-198">Ranking</span></span>|<xref:Microsoft.ML.RankingCatalog>||
||<span data-ttu-id="c266e-199">Regressão</span><span class="sxs-lookup"><span data-stu-id="c266e-199">Regression</span></span>|<xref:Microsoft.ML.RegressionCatalog>||
||<span data-ttu-id="c266e-200">Recomendação</span><span class="sxs-lookup"><span data-stu-id="c266e-200">Recommendation</span></span>|<xref:Microsoft.ML.RecommendationCatalog>|<span data-ttu-id="c266e-201">adicionar o pacote NuGet `Microsoft.ML.Recommender`</span><span class="sxs-lookup"><span data-stu-id="c266e-201">add the `Microsoft.ML.Recommender` NuGet package</span></span>|
||<span data-ttu-id="c266e-202">TimeSeries</span><span class="sxs-lookup"><span data-stu-id="c266e-202">TimeSeries</span></span>|<xref:Microsoft.ML.TimeSeriesCatalog>|<span data-ttu-id="c266e-203">adicionar o pacote NuGet `Microsoft.ML.TimeSeries`</span><span class="sxs-lookup"><span data-stu-id="c266e-203">add the `Microsoft.ML.TimeSeries` NuGet package</span></span>|
|<span data-ttu-id="c266e-204">Uso do modelo</span><span class="sxs-lookup"><span data-stu-id="c266e-204">Model usage</span></span> ||<xref:Microsoft.ML.ModelOperationsCatalog>||

<span data-ttu-id="c266e-205">Você pode navegar para os métodos de criação em cada uma das categorias acima.</span><span class="sxs-lookup"><span data-stu-id="c266e-205">You can navigate to the creation methods in each of the above categories.</span></span> <span data-ttu-id="c266e-206">Usando o Visual Studio, os catálogos aparecem por meio do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="c266e-206">Using Visual Studio, the catalogs show up via IntelliSense.</span></span>

   ![IntelliSense para Treinadores de Regressão](./media/catalog-intellisense.png)

### <a name="build-the-pipeline"></a><span data-ttu-id="c266e-208">Criar o pipeline</span><span class="sxs-lookup"><span data-stu-id="c266e-208">Build the pipeline</span></span>

<span data-ttu-id="c266e-209">Dentro de cada catálogo está um conjunto de métodos de extensão.</span><span class="sxs-lookup"><span data-stu-id="c266e-209">Inside each catalog is a set of extension methods.</span></span> <span data-ttu-id="c266e-210">Vamos examinar como os métodos de extensão são usados para criar um pipeline de treinamento.</span><span class="sxs-lookup"><span data-stu-id="c266e-210">Let's look at how extension methods are used to create a training pipeline.</span></span>

```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
        .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
```

<span data-ttu-id="c266e-211">No snippet, `Concatenate` e `Sdca` são ambos métodos no catálogo.</span><span class="sxs-lookup"><span data-stu-id="c266e-211">In the snippet, `Concatenate` and `Sdca` are both methods in the catalog.</span></span> <span data-ttu-id="c266e-212">Cada um deles criar um objeto [IEstimator](xref:Microsoft.ML.IEstimator%601) que é acrescentado ao pipeline.</span><span class="sxs-lookup"><span data-stu-id="c266e-212">They each create an [IEstimator](xref:Microsoft.ML.IEstimator%601) object that is appended to the pipeline.</span></span>

<span data-ttu-id="c266e-213">Neste ponto, os objetos são apenas criados.</span><span class="sxs-lookup"><span data-stu-id="c266e-213">At this point, the objects are created only.</span></span> <span data-ttu-id="c266e-214">Nenhuma execução aconteceu.</span><span class="sxs-lookup"><span data-stu-id="c266e-214">No execution has happened.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="c266e-215">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="c266e-215">Train the model</span></span>

<span data-ttu-id="c266e-216">Quando os objetos no pipeline foram criados, os dados podem ser usados para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="c266e-216">Once the objects in the pipeline have been created, data can be used to train the model.</span></span>

```csharp
    var model = pipeline.Fit(trainingData);
```

<span data-ttu-id="c266e-217">Chamar `Fit()` usa os dados de treinamento de entrada para estimar os parâmetros do modelo.</span><span class="sxs-lookup"><span data-stu-id="c266e-217">Calling `Fit()` uses the input training data to estimate the parameters of the model.</span></span> <span data-ttu-id="c266e-218">Isso é conhecido como treinamento do modelo.</span><span class="sxs-lookup"><span data-stu-id="c266e-218">This is known as training the model.</span></span> <span data-ttu-id="c266e-219">Lembre-se de que o modelo de regressão linear acima tinha dois parâmetros de modelo: **desvio** e **peso**.</span><span class="sxs-lookup"><span data-stu-id="c266e-219">Remember, the linear regression model above had two model parameters: **bias** and **weight**.</span></span> <span data-ttu-id="c266e-220">Após a chamada `Fit()`, os valores dos parâmetros são conhecidos.</span><span class="sxs-lookup"><span data-stu-id="c266e-220">After the `Fit()` call, the values of the parameters are known.</span></span> <span data-ttu-id="c266e-221">A maioria dos modelos terá muito mais parâmetros que isso.</span><span class="sxs-lookup"><span data-stu-id="c266e-221">Most models will have many more parameters than this.</span></span>

<span data-ttu-id="c266e-222">Você pode aprender mais sobre treinamento de modelo em [Como treinar seu modelo](./how-to-guides/train-machine-learning-model-ml-net.md)</span><span class="sxs-lookup"><span data-stu-id="c266e-222">You can learn more about model training in [How to train your model](./how-to-guides/train-machine-learning-model-ml-net.md)</span></span>

<span data-ttu-id="c266e-223">O objeto de modelo resultante implementa a interface do <xref:Microsoft.ML.ITransformer>.</span><span class="sxs-lookup"><span data-stu-id="c266e-223">The resulting model object implements the <xref:Microsoft.ML.ITransformer> interface.</span></span> <span data-ttu-id="c266e-224">Ou seja, o modelo transforma dados de entrada em previsões.</span><span class="sxs-lookup"><span data-stu-id="c266e-224">That is, the model transforms input data into predictions.</span></span>

```csharp
   IDataView predictions = model.Transform(inputData);
```

### <a name="use-the-model"></a><span data-ttu-id="c266e-225">Usar o modelo</span><span class="sxs-lookup"><span data-stu-id="c266e-225">Use the model</span></span>

<span data-ttu-id="c266e-226">Você pode transformar dados de entrada em previsões em massa ou uma entrada por vez.</span><span class="sxs-lookup"><span data-stu-id="c266e-226">You can transform input data into predictions in bulk, or one input at a time.</span></span> <span data-ttu-id="c266e-227">No exemplo de preço de residência, fizemos ambos: em massa para fins de avaliar o modelo e um por vez para fazer uma nova previsão.</span><span class="sxs-lookup"><span data-stu-id="c266e-227">In the house price example, we did both: in bulk for the purpose of evaluating the model, and one at a time to make a new prediction.</span></span> <span data-ttu-id="c266e-228">Vamos examinar como fazer previsões únicas.</span><span class="sxs-lookup"><span data-stu-id="c266e-228">Let's look at making single predictions.</span></span>

```csharp
    var size = new HouseData() { Size = 2.5F };
    var predEngine = mlContext.CreatePredictionEngine<HouseData, Prediction>(model);
    var price = predEngine.Predict(size);
```

<span data-ttu-id="c266e-229">O método `CreatePredictionEngine()` usa uma classe de entrada e uma classe de saída.</span><span class="sxs-lookup"><span data-stu-id="c266e-229">The `CreatePredictionEngine()` method takes an input class and an output class.</span></span> <span data-ttu-id="c266e-230">Os nomes de campo e/ou atributos de código determinam os nomes das colunas de dados usadas durante a previsão e o treinamento do modelo.</span><span class="sxs-lookup"><span data-stu-id="c266e-230">The field names and/or code attributes determine the names of the data columns used during model training and prediction.</span></span> <span data-ttu-id="c266e-231">Você pode ler sobre [como fazer uma previsão única](./how-to-guides/single-predict-model-ml-net.md) na seção de instruções.</span><span class="sxs-lookup"><span data-stu-id="c266e-231">You can read about  [How to make a single prediction](./how-to-guides/single-predict-model-ml-net.md) in the How-to section.</span></span>

### <a name="data-models-and-schema"></a><span data-ttu-id="c266e-232">Esquema e modelos de dados</span><span class="sxs-lookup"><span data-stu-id="c266e-232">Data models and schema</span></span>

<span data-ttu-id="c266e-233">No núcleo de um pipeline de aprendizado de máquina do ML.NET estão objetos [DataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="c266e-233">At the core of an ML.NET machine learning pipeline are [DataView](xref:Microsoft.ML.IDataView) objects.</span></span>

<span data-ttu-id="c266e-234">Cada transformação no pipeline tem um esquema de entrada (nomes, tipos e tamanhos de dados que a transformação espera ver em sua entrada); e um esquema de saída (nomes, tipos e tamanhos de dados que a transformação produz após a transformação).</span><span class="sxs-lookup"><span data-stu-id="c266e-234">Each transformation in the pipeline has an input schema (data names, types, and sizes that the transform expects to see on its input); and an output schema (data names, types, and sizes that the transform produces after the transformation).</span></span> <span data-ttu-id="c266e-235">O documento a seguir fornece uma explicação detalhada da [interface IDataView e de seu sistema de tipos](https://xadupre.github.io/machinelearningext/mlnetdocs/idataviewtypesystem.html).</span><span class="sxs-lookup"><span data-stu-id="c266e-235">The following document provides an in-depth explanation of the [IDataView interface and its type system](https://xadupre.github.io/machinelearningext/mlnetdocs/idataviewtypesystem.html).</span></span>

<span data-ttu-id="c266e-236">Se o esquema de saída de uma transformação no pipeline não corresponder ao esquema de entrada da transformação seguinte, o ML.NET gerará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="c266e-236">If the output schema from one transform in the pipeline doesn't match the input schema of the next transform, ML.NET will throw an exception.</span></span>

<span data-ttu-id="c266e-237">Um objeto de exibição de dados tem colunas e linhas.</span><span class="sxs-lookup"><span data-stu-id="c266e-237">A data view object has columns and rows.</span></span> <span data-ttu-id="c266e-238">Cada coluna tem um nome, um tipo e um comprimento.</span><span class="sxs-lookup"><span data-stu-id="c266e-238">Each column has a name and a type and a length.</span></span> <span data-ttu-id="c266e-239">Por exemplo: as colunas de entrada no exemplo de preço de residência são **Tamanho** e **Preço**.</span><span class="sxs-lookup"><span data-stu-id="c266e-239">For example: the input columns in the house price example are **Size** and **Price**.</span></span> <span data-ttu-id="c266e-240">São ambas tipo e são quantidades escalares, em vez de vetoriais.</span><span class="sxs-lookup"><span data-stu-id="c266e-240">They are both type  and they are scalar quantities rather than vector ones.</span></span>

   ![Exemplo de Exibição de Dados do ML.NET com os dados de previsão de preço de residência](./media/ml-net-dataview.png)

<span data-ttu-id="c266e-242">Todos os algoritmos do ML.NET procuram por uma coluna de entrada que é um vetor.</span><span class="sxs-lookup"><span data-stu-id="c266e-242">All ML.NET algorithms look for an input column that is a vector.</span></span> <span data-ttu-id="c266e-243">Por padrão, essa coluna de vetor é chamada **Recursos**.</span><span class="sxs-lookup"><span data-stu-id="c266e-243">By default this vector column is called **Features**.</span></span> <span data-ttu-id="c266e-244">É por isso que estamos concatenados a coluna **Tamanho** em uma nova coluna chamada **Recursos** em nosso exemplo de preço de residência.</span><span class="sxs-lookup"><span data-stu-id="c266e-244">This is why we concatenated the **Size** column into a new column called **Features** in our house price example.</span></span>

 ```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
 ```

<span data-ttu-id="c266e-245">Todos os algoritmos também criam novas colunas depois que executaram uma previsão.</span><span class="sxs-lookup"><span data-stu-id="c266e-245">All algorithms also create new columns after they have performed a prediction.</span></span> <span data-ttu-id="c266e-246">Os nomes fixos dessas novas colunas dependem do tipo de algoritmo de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="c266e-246">The fixed names of these new columns depend on the type of machine learning algorithm.</span></span> <span data-ttu-id="c266e-247">Para a tarefa de regressão, uma das novas colunas é chamada **Pontuação**.</span><span class="sxs-lookup"><span data-stu-id="c266e-247">For the regression task, one of the new columns is called **Score**.</span></span> <span data-ttu-id="c266e-248">É por isso que atribuímos nossos dados de preço com esse nome.</span><span class="sxs-lookup"><span data-stu-id="c266e-248">This is why we attributed our price data with this name.</span></span>

```csharp
    public class Prediction
    {
        [ColumnName("Score")]
        public float Price { get; set; }
    }
```

<span data-ttu-id="c266e-249">Você pode encontrar mais informações sobre colunas de saída das diferentes tarefas de aprendizado de máquina na guia [Tarefas de Aprendizado de Máquina](resources/tasks.md).</span><span class="sxs-lookup"><span data-stu-id="c266e-249">You can find out more about output columns of different machine learning tasks in the [Machine Learning Tasks](resources/tasks.md) guide.</span></span>

<span data-ttu-id="c266e-250">Uma propriedade importante de objetos DataView é que eles são avaliados **lentamente**.</span><span class="sxs-lookup"><span data-stu-id="c266e-250">An important property of DataView objects is that they are evaluated **lazily**.</span></span> <span data-ttu-id="c266e-251">Exibições de dados só são carregadas e operadas durante o treinamento e a avaliação do modelo e a previsão de dados.</span><span class="sxs-lookup"><span data-stu-id="c266e-251">Data views are only loaded and operated on during model training and evaluation, and data prediction.</span></span> <span data-ttu-id="c266e-252">Enquanto você está escrevendo e testando seu aplicativo do ML.NET, pode usar o depurador do Visual Studio para dar uma espiada em qualquer objeto de exibição de dados chamando o método [Preview](xref:Microsoft.ML.DebuggerExtensions.Preview*).</span><span class="sxs-lookup"><span data-stu-id="c266e-252">While you are writing and testing your ML.NET application, you can use the Visual Studio debugger to take a peek at any data view object by calling the [Preview](xref:Microsoft.ML.DebuggerExtensions.Preview*) method.</span></span>

```csharp
    var debug = testPriceDataView.Preview();
```

<span data-ttu-id="c266e-253">Você pode assistir à variável `debug` no depurador e examinar seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="c266e-253">You can watch the `debug` variable in the debugger and examine its contents.</span></span> <span data-ttu-id="c266e-254">Não use o método Preview em código de produção, pois ele reduz significativamente o desempenho.</span><span class="sxs-lookup"><span data-stu-id="c266e-254">Do not use the Preview method in production code, as it significantly degrades performance.</span></span>

### <a name="model-deployment"></a><span data-ttu-id="c266e-255">Implantação de Modelo</span><span class="sxs-lookup"><span data-stu-id="c266e-255">Model Deployment</span></span>

<span data-ttu-id="c266e-256">Em aplicativos da vida real, seu código de avaliação e modelo de treinamento serão separados da sua previsão.</span><span class="sxs-lookup"><span data-stu-id="c266e-256">In real-life applications, your model training and evaluation code will be separate from your prediction.</span></span> <span data-ttu-id="c266e-257">Na verdade, essas duas atividades geralmente são executadas por equipes separadas.</span><span class="sxs-lookup"><span data-stu-id="c266e-257">In fact, these two activities are often performed by separate teams.</span></span> <span data-ttu-id="c266e-258">Sua equipe de desenvolvimento do modelo pode salvar o modelo para uso no aplicativo de previsão.</span><span class="sxs-lookup"><span data-stu-id="c266e-258">Your model development team can save the model for use in the prediction application.</span></span>

```csharp
   mlContext.Model.Save(model, trainingData.Schema,"model.zip");
```

## <a name="next-steps"></a><span data-ttu-id="c266e-259">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="c266e-259">Next steps</span></span>

* <span data-ttu-id="c266e-260">Saiba como criar aplicativos usando tarefas de aprendizado de máquina diferentes com conjuntos de dados mais realistas nos [tutoriais](./tutorials/index.md).</span><span class="sxs-lookup"><span data-stu-id="c266e-260">Learn how to build applications using different machine learning tasks with more realistic data sets in the [tutorials](./tutorials/index.md).</span></span>

* <span data-ttu-id="c266e-261">Saiba mais sobre tópicos específicos em mais detalhes nos [guias de instruções](./how-to-guides/index.md).</span><span class="sxs-lookup"><span data-stu-id="c266e-261">Learn about specific topics in more depth in the [How To Guides](./how-to-guides/index.md).</span></span>

* <span data-ttu-id="c266e-262">Se você estiver superando, poderá se aprofundar diretamente na [documentação de referência da API](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="c266e-262">If you're super keen, you can dive straight into the [API Reference documentation](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet).</span></span>
