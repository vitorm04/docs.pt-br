---
title: Explore os intervalos de dados usando intervalos e índices
description: Este tutorial avançado ensina você a explorar dados usando intervalos e índices para examinar fatias de um conjunto de dados sequencial.
ms.date: 09/20/2019
ms.technology: csharp-fundamentals
ms.custom: mvc
ms.openlocfilehash: 3d4c022ff8d6e7f260632e34d6f28277014c85c8
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345628"
---
# <a name="indices-and-ranges"></a><span data-ttu-id="17608-103">Índices e intervalos</span><span class="sxs-lookup"><span data-stu-id="17608-103">Indices and ranges</span></span>

<span data-ttu-id="17608-104">Intervalos e índices fornecem uma sintaxe sucinta para acessar elementos únicos ou intervalos em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="17608-104">Ranges and indices provide a succinct syntax for accessing single elements or ranges in a sequence.</span></span>

<span data-ttu-id="17608-105">Neste tutorial, você aprenderá a:</span><span class="sxs-lookup"><span data-stu-id="17608-105">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="17608-106">Use a sintaxe para intervalos em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="17608-106">Use the syntax for ranges in a sequence.</span></span>
> - <span data-ttu-id="17608-107">Compreenda as decisões de design para o início e o fim de cada sequência.</span><span class="sxs-lookup"><span data-stu-id="17608-107">Understand the design decisions for the start and end of each sequence.</span></span>
> - <span data-ttu-id="17608-108">Conheça cenários para os tipos <xref:System.Index> e <xref:System.Range>.</span><span class="sxs-lookup"><span data-stu-id="17608-108">Learn scenarios for the <xref:System.Index> and <xref:System.Range> types.</span></span>

## <a name="language-support-for-indices-and-ranges"></a><span data-ttu-id="17608-109">Suporte a idioma para intervalos e índices</span><span class="sxs-lookup"><span data-stu-id="17608-109">Language support for indices and ranges</span></span>

<span data-ttu-id="17608-110">Esse suporte a idioma depende de dois novos tipos e de dois novos operadores:</span><span class="sxs-lookup"><span data-stu-id="17608-110">This language support relies on two new types and two new operators:</span></span>

- <span data-ttu-id="17608-111"><xref:System.Index?displayProperty=nameWithType> representa um índice em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="17608-111"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="17608-112">O índice do operador end `^`, que especifica que um índice é relativo ao final de uma sequência.</span><span class="sxs-lookup"><span data-stu-id="17608-112">The index from end operator `^`, which specifies that an index is relative to the end of a sequence.</span></span>
- <span data-ttu-id="17608-113"><xref:System.Range?displayProperty=nameWithType> representa um subintervalo de uma sequência.</span><span class="sxs-lookup"><span data-stu-id="17608-113"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="17608-114">O operador Range `..`, que especifica o início e o término de um intervalo como seus operandos.</span><span class="sxs-lookup"><span data-stu-id="17608-114">The range operator `..`, which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="17608-115">Vamos começar com as regras para índices.</span><span class="sxs-lookup"><span data-stu-id="17608-115">Let's start with the rules for indices.</span></span> <span data-ttu-id="17608-116">Considere uma matriz `sequence`.</span><span class="sxs-lookup"><span data-stu-id="17608-116">Consider an array `sequence`.</span></span> <span data-ttu-id="17608-117">O índice `0` é o mesmo que `sequence[0]`.</span><span class="sxs-lookup"><span data-stu-id="17608-117">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="17608-118">O índice `^0` é o mesmo que `sequence[sequence.Length]`.</span><span class="sxs-lookup"><span data-stu-id="17608-118">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="17608-119">Observe que `sequence[^0]` gera uma exceção, assim como `sequence[sequence.Length]` faz.</span><span class="sxs-lookup"><span data-stu-id="17608-119">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="17608-120">Para qualquer número `n`, o índice `^n` é o mesmo que `sequence[sequence.Length - n]`.</span><span class="sxs-lookup"><span data-stu-id="17608-120">For any number `n`, the index `^n` is the same as `sequence[sequence.Length - n]`.</span></span>

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

<span data-ttu-id="17608-121">Você pode recuperar a última palavra com o índice `^1`.</span><span class="sxs-lookup"><span data-stu-id="17608-121">You can retrieve the last word with the `^1` index.</span></span> <span data-ttu-id="17608-122">Adicione o código a seguir abaixo da inicialização:</span><span class="sxs-lookup"><span data-stu-id="17608-122">Add the following code below the initialization:</span></span>

[!code-csharp[LastIndex](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

<span data-ttu-id="17608-123">Um intervalo especifica o *início* e o *final* de um intervalo.</span><span class="sxs-lookup"><span data-stu-id="17608-123">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="17608-124">Intervalos são exclusivos, o que significa que *final* não está incluído no intervalo.</span><span class="sxs-lookup"><span data-stu-id="17608-124">Ranges are exclusive, meaning the *end* is not included in the range.</span></span> <span data-ttu-id="17608-125">O intervalo `[0..^0]` representa todo o intervalo, assim como `[0..sequence.Length]` representa todo o intervalo.</span><span class="sxs-lookup"><span data-stu-id="17608-125">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span> 

<span data-ttu-id="17608-126">O código a seguir cria um subintervalo com as palavras "quick", "brown" e "fox".</span><span class="sxs-lookup"><span data-stu-id="17608-126">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="17608-127">Ele inclui `words[1]` até `words[3]`.</span><span class="sxs-lookup"><span data-stu-id="17608-127">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="17608-128">O elemento `words[4]` não está no intervalo.</span><span class="sxs-lookup"><span data-stu-id="17608-128">The element `words[4]` isn't in the range.</span></span> <span data-ttu-id="17608-129">Adicione o seguinte código ao mesmo método.</span><span class="sxs-lookup"><span data-stu-id="17608-129">Add the following code to the same method.</span></span> <span data-ttu-id="17608-130">Copie e cole-o na parte inferior da janela interativa.</span><span class="sxs-lookup"><span data-stu-id="17608-130">Copy and paste it at the bottom of the interactive window.</span></span>

[!code-csharp[Range](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

<span data-ttu-id="17608-131">O código a seguir cria um subintervalo com "lazy" e "dog".</span><span class="sxs-lookup"><span data-stu-id="17608-131">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="17608-132">Ele inclui `words[^2]` e `words[^1]`.</span><span class="sxs-lookup"><span data-stu-id="17608-132">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="17608-133">O índice final `words[^0]` não está incluído.</span><span class="sxs-lookup"><span data-stu-id="17608-133">The end index `words[^0]` isn't included.</span></span> <span data-ttu-id="17608-134">Adicione o seguinte código também:</span><span class="sxs-lookup"><span data-stu-id="17608-134">Add the following code as well:</span></span>

[!code-csharp[LastRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

<span data-ttu-id="17608-135">Os exemplos a seguir criam intervalos abertos para o início, fim ou ambos:</span><span class="sxs-lookup"><span data-stu-id="17608-135">The following examples create ranges that are open ended for the start, end, or both:</span></span>

[!code-csharp[PartialRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

<span data-ttu-id="17608-136">Você também pode declarar intervalos ou índices como variáveis.</span><span class="sxs-lookup"><span data-stu-id="17608-136">You can also declare ranges or indices as variables.</span></span> <span data-ttu-id="17608-137">A variável então pode ser usada dentro dos caracteres `[` e `]`:</span><span class="sxs-lookup"><span data-stu-id="17608-137">The variable can then be used inside the `[` and `]` characters:</span></span>

[!code-csharp[IndexRangeTypes](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

<span data-ttu-id="17608-138">O exemplo a seguir mostra muitos dos motivos para essas escolhas.</span><span class="sxs-lookup"><span data-stu-id="17608-138">The following sample shows many of the reasons for those choices.</span></span> <span data-ttu-id="17608-139">Modifique `x`, `y` e `z` para tentar combinações diferentes.</span><span class="sxs-lookup"><span data-stu-id="17608-139">Modify `x`, `y`, and `z` to try different combinations.</span></span> <span data-ttu-id="17608-140">Quando você testar, use valores em que `x` é menor que `y` e `y` é menor que `z` para as combinações válidas.</span><span class="sxs-lookup"><span data-stu-id="17608-140">When you experiment, use values where `x` is less than `y`, and `y` is less than `z` for valid combinations.</span></span> <span data-ttu-id="17608-141">Adicione o seguinte código a um novo método.</span><span class="sxs-lookup"><span data-stu-id="17608-141">Add the following code in a new method.</span></span> <span data-ttu-id="17608-142">Tente usar combinações diferentes:</span><span class="sxs-lookup"><span data-stu-id="17608-142">Try different combinations:</span></span>

[!code-csharp[SemanticsExamples](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="type-support-for-indices-and-ranges"></a><span data-ttu-id="17608-143">Suporte de tipo para índices e intervalos</span><span class="sxs-lookup"><span data-stu-id="17608-143">Type support for indices and ranges</span></span>

<span data-ttu-id="17608-144">Índices e intervalos fornecem sintaxe clara e concisa para acessar um único elemento ou um subintervalo de elementos em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="17608-144">Indexes and ranges provide clear, concise syntax to access a single element or a sub-range of elements in a sequence.</span></span> <span data-ttu-id="17608-145">Uma expressão de índice normalmente retorna o tipo dos elementos de uma sequência.</span><span class="sxs-lookup"><span data-stu-id="17608-145">An index expression typically returns the type of the elements of a sequence.</span></span> <span data-ttu-id="17608-146">Uma expressão de intervalo normalmente retorna o mesmo tipo de sequência que a sequência de origem.</span><span class="sxs-lookup"><span data-stu-id="17608-146">A range expression typically returns the same sequence type as the source sequence.</span></span>

<span data-ttu-id="17608-147">Se um tipo fornecer um [indexador](../programming-guide/indexers/index.md) com um parâmetro <xref:System.Index> ou <xref:System.Range>, ele dará suporte explicitamente a índices ou intervalos, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="17608-147">If a type provides an [indexer](../programming-guide/indexers/index.md) with an <xref:System.Index> or <xref:System.Range> parameter, it explicitly supports indices or ranges respectively.</span></span> <span data-ttu-id="17608-148">Quando o tipo fornece um indexador que usa um único parâmetro de <xref:System.Range>, ele pode optar por retornar um tipo de sequência diferente, como <xref:System.Span%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="17608-148">When the type provides an indexer that takes a single <xref:System.Range> parameter, it may choose to return a different sequence type, such as <xref:System.Span%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="17608-149">Um tipo é **contável** se tiver uma propriedade chamada `Length` ou `Count` com um getter acessível e um tipo de retorno de `int`.</span><span class="sxs-lookup"><span data-stu-id="17608-149">A type is **countable** if it has a property named `Length` or `Count` with an accessible getter and a return type of `int`.</span></span> <span data-ttu-id="17608-150">Um tipo com contagem que não dá suporte explicitamente a índices ou intervalos pode fornecer um suporte implícito para eles.</span><span class="sxs-lookup"><span data-stu-id="17608-150">A countable type that doesn't explicitly support indices or ranges may provide an implicit support for them.</span></span> <span data-ttu-id="17608-151">Para obter mais informações, consulte as seções [suporte ao índice implícito](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) e [suporte de intervalo implícito](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) da [Nota de proposta de recurso](~/_csharplang/proposals/csharp-8.0/ranges.md).</span><span class="sxs-lookup"><span data-stu-id="17608-151">For more information, see the [Implicit Index support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) and [Implicit Range support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) sections of the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span> <span data-ttu-id="17608-152">Intervalos usando o suporte de intervalo implícito retornam o mesmo tipo de sequência que a sequência de origem.</span><span class="sxs-lookup"><span data-stu-id="17608-152">Ranges using implicit range support return the same sequence type as the source sequence.</span></span>

<span data-ttu-id="17608-153">Por exemplo, os seguintes tipos .NET oferecem suporte a índices e intervalos: <xref:System.Array>, <xref:System.String>, <xref:System.Span%601>e <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="17608-153">For example, the following .NET types support both indices and ranges: <xref:System.Array>, <xref:System.String>, <xref:System.Span%601>, and <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="17608-154">O <xref:System.Collections.Generic.List%601> dá suporte a índices, mas não dá suporte a intervalos.</span><span class="sxs-lookup"><span data-stu-id="17608-154">The <xref:System.Collections.Generic.List%601> supports indices but doesn't support ranges.</span></span>

## <a name="scenarios-for-indices-and-ranges"></a><span data-ttu-id="17608-155">Cenários para índices e intervalos</span><span class="sxs-lookup"><span data-stu-id="17608-155">Scenarios for indices and ranges</span></span>

<span data-ttu-id="17608-156">Você muitas vezes usará intervalos e índices quando quiser executar uma análise no subintervalo de uma sequência inteira.</span><span class="sxs-lookup"><span data-stu-id="17608-156">You'll often use ranges and indices when you want to perform some analysis on subrange of an entire sequence.</span></span> <span data-ttu-id="17608-157">A nova sintaxe é mais clara para ler exatamente quais subintervalo está envolvido.</span><span class="sxs-lookup"><span data-stu-id="17608-157">The new syntax is clearer in reading exactly what subrange is involved.</span></span> <span data-ttu-id="17608-158">A função local `MovingAverage` usa um <xref:System.Range> como seu argumento.</span><span class="sxs-lookup"><span data-stu-id="17608-158">The local function `MovingAverage` takes a <xref:System.Range> as its argument.</span></span> <span data-ttu-id="17608-159">O método então enumera apenas esse intervalo ao calcular o mínimo, máximo e média.</span><span class="sxs-lookup"><span data-stu-id="17608-159">The method then enumerates just that range when calculating the min, max, and average.</span></span> <span data-ttu-id="17608-160">Experimente o seguinte código em seu projeto:</span><span class="sxs-lookup"><span data-stu-id="17608-160">Try the following code in your project:</span></span>

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

<span data-ttu-id="17608-161">Baixe o código concluído no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes).</span><span class="sxs-lookup"><span data-stu-id="17608-161">You can download the completed code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) repository.</span></span>
