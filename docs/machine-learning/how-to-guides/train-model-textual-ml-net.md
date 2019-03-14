---
title: Aplicar a engenharia de funcionalidades ao treinamento de modelo em dados textuais – ML.NET
description: Saiba como aplicar a engenharia de funcionalidades ao treinamento de modelo em dados textuais com o ML.NET
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 8733db281dbc60ae3f4ac0c139c482b39089f2b8
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57680068"
---
# <a name="apply-feature-engineering-for-machine-learning-model-training-on-textual-data-with-mlnet"></a><span data-ttu-id="e0468-103">Aplicar a engenharia de funcionalidades ao treinamento de modelo de machine learning em dados textuais com o ML.NET</span><span class="sxs-lookup"><span data-stu-id="e0468-103">Apply feature engineering for machine learning model training on textual data with ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="e0468-104">Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="e0468-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="e0468-105">Para obter mais informações, visite [a introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="e0468-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="e0468-106">Esta instrução e a amostra relacionada estão usando o **ML.NET versão 0.10** no momento.</span><span class="sxs-lookup"><span data-stu-id="e0468-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="e0468-107">Saiba mais nas notas de versão no [repositório do GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="e0468-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="e0468-108">Você precisa converter os dados não float em tipos de dados `float`, pois todos os `learners` do ML.NET esperam as funcionalidades como um `float vector`.</span><span class="sxs-lookup"><span data-stu-id="e0468-108">You need to convert any non float data to `float` data types since all ML.NET `learners` expect features as a `float vector`.</span></span>

<span data-ttu-id="e0468-109">Para aprender mais sobre os dados textuais, você precisará extrair as funcionalidades de texto.</span><span class="sxs-lookup"><span data-stu-id="e0468-109">To learn on textual data, you need to extract text features.</span></span> <span data-ttu-id="e0468-110">O ML.NET tem alguns mecanismos básicos de extração de funcionalidades de texto:</span><span class="sxs-lookup"><span data-stu-id="e0468-110">ML.NET has some basic text feature extraction mechanisms:</span></span>

- <span data-ttu-id="e0468-111">`Text normalization` (remoção de pontuação, diacríticos, alternância para minúsculas, etc.)</span><span class="sxs-lookup"><span data-stu-id="e0468-111">`Text normalization` (removing punctuation, diacritics, switching to lowercase etc.)</span></span>
- <span data-ttu-id="e0468-112">`Separator-based tokenization`.</span><span class="sxs-lookup"><span data-stu-id="e0468-112">`Separator-based tokenization`.</span></span>
- <span data-ttu-id="e0468-113">Remoção de `Stopword`.</span><span class="sxs-lookup"><span data-stu-id="e0468-113">`Stopword` removal.</span></span>
- <span data-ttu-id="e0468-114">Extração de `Ngram` e `skip-gram`.</span><span class="sxs-lookup"><span data-stu-id="e0468-114">`Ngram` and `skip-gram` extraction.</span></span>
- <span data-ttu-id="e0468-115">Redimensionamento de`TF-IDF`.</span><span class="sxs-lookup"><span data-stu-id="e0468-115">`TF-IDF` rescaling.</span></span>
- <span data-ttu-id="e0468-116">Conversão de `Bag of words`.</span><span class="sxs-lookup"><span data-stu-id="e0468-116">`Bag of words` conversion.</span></span>

<span data-ttu-id="e0468-117">O seguinte exemplo demonstra os mecanismos de extração de funcionalidades de texto do ML.NET usando o [conjunto de dados detox do Wikipédia](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv):</span><span class="sxs-lookup"><span data-stu-id="e0468-117">The following example demonstrates ML.NET text feature extraction mechanisms using the [Wikipedia detox dataset](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv):</span></span>

```console
Sentiment   SentimentText
1   Stop trolling, zapatancas, calling me a liar merely demonstartes that you arer Zapatancas. You may choose to chase every legitimate editor from this site and ignore me but I am an editor with a record that isnt 99% trolling and therefore my wishes are not to be completely ignored by a sockpuppet like yourself. The consensus is overwhelmingly against you and your trolling lover Zapatancas,  
1   ::::: Why are you threatening me? I'm not being disruptive, its you who is being disruptive.   
0   " *::Your POV and propaganda pushing is dully noted. However listing interesting facts in a netral and unacusitory tone is not POV. You seem to be confusing Censorship with POV monitoring. I see nothing POV expressed in the listing of intersting facts. If you want to contribute more facts or edit wording of the cited fact to make them sound more netral then go ahead. No need to CENSOR interesting factual information. "
0   ::::::::This is a gross exaggeration. Nobody is setting a kangaroo court. There was a simple addition concerning the airline. It is the only one disputed here.   
```

```csharp
// Define the reader: specify the data columns and where to find them in the text file.
var reader = mlContext.Data.CreateTextLoader(new[] 
    {
        new TextLoader.Column("IsToxic", DataKind.BL, 0),
        new TextLoader.Column("Message", DataKind.TX, 1),
    },
    hasHeader: true
);

// Read the data.
var data = reader.Read(dataPath);

// Inspect the message texts that are read from the file.
var messageTexts = data.GetColumn<string>(mlContext, "Message").Take(20).ToArray();

// Apply various kinds of text operations supported by ML.NET.
var pipeline =
    // One-stop shop to run the full text featurization.
    mlContext.Transforms.Text.FeaturizeText("TextFeatures", "Message")

    // Normalize the message for later transforms
    .Append(mlContext.Transforms.Text.NormalizeText("NormalizedMessage", "Message"))

    // NLP pipeline 1: bag of words.
    .Append(new WordBagEstimator(mlContext, "BagOfWords", "NormalizedMessage"))

    // NLP pipeline 2: bag of bigrams, using hashes instead of dictionary indices.
    .Append(new WordHashBagEstimator(mlContext, "BagOfBigrams","NormalizedMessage", 
                ngramLength: 2, allLengths: false))

    // NLP pipeline 3: bag of tri-character sequences with TF-IDF weighting.
    .Append(mlContext.Transforms.Text.TokenizeCharacters("MessageChars", "Message"))
    .Append(new NgramExtractingEstimator(mlContext, "BagOfTrichar", "MessageChars", 
                ngramLength: 3, weighting: NgramExtractingEstimator.WeightingCriteria.TfIdf))

    // NLP pipeline 4: word embeddings.
    .Append(mlContext.Transforms.Text.TokenizeWords("TokenizedMessage", "NormalizedMessage"))
    .Append(mlContext.Transforms.Text.ExtractWordEmbeddings("Embeddings", "TokenizedMessage",
                WordEmbeddingsExtractingTransformer.PretrainedModelKind.GloVeTwitter25D));

// Let's train our pipeline, and then apply it to the same data.
// Note that even on a small dataset of 70KB the pipeline above can take up to a minute to completely train.
var transformedData = pipeline.Fit(data).Transform(data);

// Inspect some columns of the resulting dataset.
var embeddings = transformedData.GetColumn<float[]>(mlContext, "Embeddings").Take(10).ToArray();
var unigrams = transformedData.GetColumn<float[]>(mlContext, "BagOfWords").Take(10).ToArray();
```
