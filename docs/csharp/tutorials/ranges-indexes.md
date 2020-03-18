---
title: Explore os intervalos de dados usando intervalos e índices
description: Este tutorial avançado ensina você a explorar dados usando intervalos e índices para examinar fatias de um conjunto de dados sequencial.
ms.date: 03/11/2020
ms.technology: csharp-fundamentals
ms.custom: mvc
ms.openlocfilehash: 82aad968e2efc437c82a7c8250bcd108b60b09e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156488"
---
# <a name="indices-and-ranges"></a><span data-ttu-id="69626-103">Índices e intervalos</span><span class="sxs-lookup"><span data-stu-id="69626-103">Indices and ranges</span></span>

<span data-ttu-id="69626-104">Faixas e índices fornecem uma sintaxe sucinta para acessar elementos únicos ou intervalos em uma seqüência.</span><span class="sxs-lookup"><span data-stu-id="69626-104">Ranges and indices provide a succinct syntax for accessing single elements or ranges in a sequence.</span></span>

<span data-ttu-id="69626-105">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="69626-105">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="69626-106">Use a sintaxe para intervalos em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="69626-106">Use the syntax for ranges in a sequence.</span></span>
> - <span data-ttu-id="69626-107">Compreenda as decisões de design para o início e o fim de cada sequência.</span><span class="sxs-lookup"><span data-stu-id="69626-107">Understand the design decisions for the start and end of each sequence.</span></span>
> - <span data-ttu-id="69626-108">Conheça cenários para os tipos <xref:System.Index> e <xref:System.Range>.</span><span class="sxs-lookup"><span data-stu-id="69626-108">Learn scenarios for the <xref:System.Index> and <xref:System.Range> types.</span></span>

## <a name="language-support-for-indices-and-ranges"></a><span data-ttu-id="69626-109">Suporte a idioma para intervalos e índices</span><span class="sxs-lookup"><span data-stu-id="69626-109">Language support for indices and ranges</span></span>

<span data-ttu-id="69626-110">Este suporte ao idioma conta com dois novos tipos e dois novos operadores:</span><span class="sxs-lookup"><span data-stu-id="69626-110">This language support relies on two new types and two new operators:</span></span>

- <span data-ttu-id="69626-111"><xref:System.Index?displayProperty=nameWithType> representa um índice em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="69626-111"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="69626-112">O índice do `^`operador final , que especifica que um índice é relativo ao fim de uma seqüência.</span><span class="sxs-lookup"><span data-stu-id="69626-112">The index from end operator `^`, which specifies that an index is relative to the end of a sequence.</span></span>
- <span data-ttu-id="69626-113"><xref:System.Range?displayProperty=nameWithType> representa um subintervalo de uma sequência.</span><span class="sxs-lookup"><span data-stu-id="69626-113"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="69626-114">O operador `..`de alcance , que especifica o início e o fim de uma faixa como seus operadores.</span><span class="sxs-lookup"><span data-stu-id="69626-114">The range operator `..`, which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="69626-115">Vamos começar com as regras para índices.</span><span class="sxs-lookup"><span data-stu-id="69626-115">Let's start with the rules for indices.</span></span> <span data-ttu-id="69626-116">Considere uma matriz `sequence`.</span><span class="sxs-lookup"><span data-stu-id="69626-116">Consider an array `sequence`.</span></span> <span data-ttu-id="69626-117">O índice `0` é o mesmo que `sequence[0]`.</span><span class="sxs-lookup"><span data-stu-id="69626-117">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="69626-118">O índice `^0` é o mesmo que `sequence[sequence.Length]`.</span><span class="sxs-lookup"><span data-stu-id="69626-118">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="69626-119">A `sequence[^0]` expressão faz uma exceção, assim como. `sequence[sequence.Length]`</span><span class="sxs-lookup"><span data-stu-id="69626-119">The expression `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="69626-120">Para qualquer número `n`, o índice `^n` é o mesmo que `sequence[sequence.Length - n]`.</span><span class="sxs-lookup"><span data-stu-id="69626-120">For any number `n`, the index `^n` is the same as `sequence[sequence.Length - n]`.</span></span>

```csharp
string[] words = new string[]
{
                // index from start    index from end
    "The",      // 0                   ^9
    "quick",    // 1                   ^8
    "brown",    // 2                   ^7
    "fox",      // 3                   ^6
    "jumped",   // 4                   ^5
    "over",     // 5                   ^4
    "the",      // 6                   ^3
    "lazy",     // 7                   ^2
    "dog"       // 8                   ^1
};              // 9 (or words.Length) ^0
```

<span data-ttu-id="69626-121">Você pode recuperar a última palavra com o índice `^1`.</span><span class="sxs-lookup"><span data-stu-id="69626-121">You can retrieve the last word with the `^1` index.</span></span> <span data-ttu-id="69626-122">Adicione o código a seguir abaixo da inicialização:</span><span class="sxs-lookup"><span data-stu-id="69626-122">Add the following code below the initialization:</span></span>

[!code-csharp[LastIndex](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

<span data-ttu-id="69626-123">Um intervalo especifica o *início* e o *final* de um intervalo.</span><span class="sxs-lookup"><span data-stu-id="69626-123">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="69626-124">As faixas são exclusivas, o que significa que o *final* não está incluído na gama.</span><span class="sxs-lookup"><span data-stu-id="69626-124">Ranges are exclusive, meaning the *end* isn't included in the range.</span></span> <span data-ttu-id="69626-125">O intervalo `[0..^0]` representa todo o intervalo, assim como `[0..sequence.Length]` representa todo o intervalo.</span><span class="sxs-lookup"><span data-stu-id="69626-125">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span>

<span data-ttu-id="69626-126">O código a seguir cria um subintervalo com as palavras "quick", "brown" e "fox".</span><span class="sxs-lookup"><span data-stu-id="69626-126">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="69626-127">Ele inclui `words[1]` até `words[3]`.</span><span class="sxs-lookup"><span data-stu-id="69626-127">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="69626-128">O elemento `words[4]` não está no intervalo.</span><span class="sxs-lookup"><span data-stu-id="69626-128">The element `words[4]` isn't in the range.</span></span> <span data-ttu-id="69626-129">Adicione o seguinte código ao mesmo método.</span><span class="sxs-lookup"><span data-stu-id="69626-129">Add the following code to the same method.</span></span> <span data-ttu-id="69626-130">Copie e cole-o na parte inferior da janela interativa.</span><span class="sxs-lookup"><span data-stu-id="69626-130">Copy and paste it at the bottom of the interactive window.</span></span>

[!code-csharp[Range](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

<span data-ttu-id="69626-131">O código a seguir cria um subintervalo com "lazy" e "dog".</span><span class="sxs-lookup"><span data-stu-id="69626-131">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="69626-132">Ele inclui `words[^2]` e `words[^1]`.</span><span class="sxs-lookup"><span data-stu-id="69626-132">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="69626-133">O índice final `words[^0]` não está incluído.</span><span class="sxs-lookup"><span data-stu-id="69626-133">The end index `words[^0]` isn't included.</span></span> <span data-ttu-id="69626-134">Adicione o seguinte código também:</span><span class="sxs-lookup"><span data-stu-id="69626-134">Add the following code as well:</span></span>

[!code-csharp[LastRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

<span data-ttu-id="69626-135">Os exemplos a seguir criam intervalos abertos para o início, fim ou ambos:</span><span class="sxs-lookup"><span data-stu-id="69626-135">The following examples create ranges that are open ended for the start, end, or both:</span></span>

[!code-csharp[PartialRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

<span data-ttu-id="69626-136">Você também pode declarar intervalos ou índices como variáveis.</span><span class="sxs-lookup"><span data-stu-id="69626-136">You can also declare ranges or indices as variables.</span></span> <span data-ttu-id="69626-137">A variável então pode ser usada dentro dos caracteres `[` e `]`:</span><span class="sxs-lookup"><span data-stu-id="69626-137">The variable can then be used inside the `[` and `]` characters:</span></span>

[!code-csharp[IndexRangeTypes](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

<span data-ttu-id="69626-138">O exemplo a seguir mostra muitos dos motivos para essas escolhas.</span><span class="sxs-lookup"><span data-stu-id="69626-138">The following sample shows many of the reasons for those choices.</span></span> <span data-ttu-id="69626-139">Modifique `x`, `y` e `z` para tentar combinações diferentes.</span><span class="sxs-lookup"><span data-stu-id="69626-139">Modify `x`, `y`, and `z` to try different combinations.</span></span> <span data-ttu-id="69626-140">Quando você testar, use valores em que `x` é menor que `y` e `y` é menor que `z` para as combinações válidas.</span><span class="sxs-lookup"><span data-stu-id="69626-140">When you experiment, use values where `x` is less than `y`, and `y` is less than `z` for valid combinations.</span></span> <span data-ttu-id="69626-141">Adicione o seguinte código a um novo método.</span><span class="sxs-lookup"><span data-stu-id="69626-141">Add the following code in a new method.</span></span> <span data-ttu-id="69626-142">Tente usar combinações diferentes:</span><span class="sxs-lookup"><span data-stu-id="69626-142">Try different combinations:</span></span>

[!code-csharp[SemanticsExamples](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="type-support-for-indices-and-ranges"></a><span data-ttu-id="69626-143">Tipo suporte para índices e faixas</span><span class="sxs-lookup"><span data-stu-id="69626-143">Type support for indices and ranges</span></span>

<span data-ttu-id="69626-144">Índices e faixas fornecem sintaxe clara e concisa para acessar um único elemento ou uma subgama de elementos em uma seqüência.</span><span class="sxs-lookup"><span data-stu-id="69626-144">Indexes and ranges provide clear, concise syntax to access a single element or a subrange of elements in a sequence.</span></span> <span data-ttu-id="69626-145">Uma expressão de índice normalmente retorna o tipo de elementos de uma seqüência.</span><span class="sxs-lookup"><span data-stu-id="69626-145">An index expression typically returns the type of the elements of a sequence.</span></span> <span data-ttu-id="69626-146">Uma expressão de intervalo normalmente retorna o mesmo tipo de seqüência da seqüência de origem.</span><span class="sxs-lookup"><span data-stu-id="69626-146">A range expression typically returns the same sequence type as the source sequence.</span></span>

<span data-ttu-id="69626-147">Qualquer tipo que forneça um <xref:System.Index> <xref:System.Range> [indexador](../programming-guide/indexers/index.md) com um ou parâmetro suporta explicitamente índices ou faixas, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="69626-147">Any type that provides an [indexer](../programming-guide/indexers/index.md) with an <xref:System.Index> or <xref:System.Range> parameter explicitly supports indices or ranges respectively.</span></span> <span data-ttu-id="69626-148">Um indexador que <xref:System.Range> toma um único parâmetro pode <xref:System.Span%601?displayProperty=nameWithType>retornar um tipo de seqüência diferente, como .</span><span class="sxs-lookup"><span data-stu-id="69626-148">An indexer that takes a single <xref:System.Range> parameter may return a different sequence type, such as <xref:System.Span%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="69626-149">Um tipo é **contável** se `Length` `Count` tiver uma propriedade nomeada ou `int`com um getter acessível e um tipo de retorno de .</span><span class="sxs-lookup"><span data-stu-id="69626-149">A type is **countable** if it has a property named `Length` or `Count` with an accessible getter and a return type of `int`.</span></span> <span data-ttu-id="69626-150">Um tipo contável que não suporta explicitamente índices ou intervalos pode fornecer um suporte implícito para eles.</span><span class="sxs-lookup"><span data-stu-id="69626-150">A countable type that doesn't explicitly support indices or ranges may provide an implicit support for them.</span></span> <span data-ttu-id="69626-151">Para obter mais informações, consulte as seções [de suporte ao Índice Implícito](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) e à Faixa [Implícita](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) da [nota de proposta de recurso](~/_csharplang/proposals/csharp-8.0/ranges.md).</span><span class="sxs-lookup"><span data-stu-id="69626-151">For more information, see the [Implicit Index support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) and [Implicit Range support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) sections of the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span> <span data-ttu-id="69626-152">Intervalos usando suporte de intervalo implícito retornam o mesmo tipo de seqüência que a seqüência de origem.</span><span class="sxs-lookup"><span data-stu-id="69626-152">Ranges using implicit range support return the same sequence type as the source sequence.</span></span>

<span data-ttu-id="69626-153">Por exemplo, os seguintes tipos .NET suportam índices e intervalos: <xref:System.String>, <xref:System.Span%601>e <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="69626-153">For example, the following .NET types support both indices and ranges: <xref:System.String>, <xref:System.Span%601>, and <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="69626-154">Os <xref:System.Collections.Generic.List%601> índices suportam, mas não suportam faixas.</span><span class="sxs-lookup"><span data-stu-id="69626-154">The <xref:System.Collections.Generic.List%601> supports indices but doesn't support ranges.</span></span>

<span data-ttu-id="69626-155"><xref:System.Array>tem um comportamento mais matizado.</span><span class="sxs-lookup"><span data-stu-id="69626-155"><xref:System.Array> has more nuanced behavior.</span></span> <span data-ttu-id="69626-156">Os arrays de dimensões únicas suportam índices e intervalos.</span><span class="sxs-lookup"><span data-stu-id="69626-156">Single dimension arrays support both indices and ranges.</span></span> <span data-ttu-id="69626-157">Matrizes multidimensionais não.</span><span class="sxs-lookup"><span data-stu-id="69626-157">Multi-dimensional arrays don't.</span></span> <span data-ttu-id="69626-158">O indexador para uma matriz multidimensional tem múltiplos parâmetros, não um único parâmetro.</span><span class="sxs-lookup"><span data-stu-id="69626-158">The indexer for a multi-dimensional array has multiple parameters, not a single parameter.</span></span> <span data-ttu-id="69626-159">Os arrays irregulares, também referidos como uma matriz de matrizes, suportam ambos os intervalos e indexadores.</span><span class="sxs-lookup"><span data-stu-id="69626-159">Jagged arrays, also referred to as an array of arrays, support both ranges and indexers.</span></span> <span data-ttu-id="69626-160">O exemplo a seguir mostra como iterar uma subseção retangular de uma matriz irregular.</span><span class="sxs-lookup"><span data-stu-id="69626-160">The following example shows how to iterate a rectangular subsection of a jagged array.</span></span> <span data-ttu-id="69626-161">Itenumera a seção no centro, excluindo a primeira e a última três linhas, e as duas primeiras e últimas duas colunas de cada linha selecionada:</span><span class="sxs-lookup"><span data-stu-id="69626-161">It iterates the section in the center, excluding the first and last three rows, and the first and last two columns from each selected row:</span></span>

[!code-csharp[JaggedArrays](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_JaggedArrays)]

## <a name="scenarios-for-indices-and-ranges"></a><span data-ttu-id="69626-162">Cenários para índices e faixas</span><span class="sxs-lookup"><span data-stu-id="69626-162">Scenarios for indices and ranges</span></span>

<span data-ttu-id="69626-163">Muitas vezes você usará intervalos e índices quando quiser analisar uma subgama de uma seqüência maior.</span><span class="sxs-lookup"><span data-stu-id="69626-163">You'll often use ranges and indices when you want to analyze a subrange of a larger sequence.</span></span> <span data-ttu-id="69626-164">A nova sintaxe é mais clara para ler exatamente quais subintervalo está envolvido.</span><span class="sxs-lookup"><span data-stu-id="69626-164">The new syntax is clearer in reading exactly what subrange is involved.</span></span> <span data-ttu-id="69626-165">A função local `MovingAverage` usa um <xref:System.Range> como seu argumento.</span><span class="sxs-lookup"><span data-stu-id="69626-165">The local function `MovingAverage` takes a <xref:System.Range> as its argument.</span></span> <span data-ttu-id="69626-166">O método então enumera apenas esse intervalo ao calcular o mínimo, máximo e média.</span><span class="sxs-lookup"><span data-stu-id="69626-166">The method then enumerates just that range when calculating the min, max, and average.</span></span> <span data-ttu-id="69626-167">Experimente o seguinte código em seu projeto:</span><span class="sxs-lookup"><span data-stu-id="69626-167">Try the following code in your project:</span></span>

[!code-csharp[MovingAverages](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]
