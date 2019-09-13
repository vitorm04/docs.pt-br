---
title: Explore os intervalos de dados usando intervalos e índices
description: Este tutorial avançado ensina você a explorar dados usando intervalos e índices para examinar fatias de um conjunto de dados sequencial.
ms.date: 04/19/2019
ms.custom: mvc
ms.openlocfilehash: 27f4b90f130345dd10517a5de78c759066afdf07
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926646"
---
# <a name="indices-and-ranges"></a><span data-ttu-id="46a1c-103">Índices e intervalos</span><span class="sxs-lookup"><span data-stu-id="46a1c-103">Indices and ranges</span></span>

<span data-ttu-id="46a1c-104">Intervalos e índices fornecem uma sintaxe sucinta para acessar elementos únicos ou intervalos em <xref:System.Array>, <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="46a1c-104">Ranges and indices provide a succinct syntax for accessing single elements or ranges in an <xref:System.Array>, <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="46a1c-105">Esses recursos permitem uma sintaxe mais concisa e clara para acessar elementos únicos ou intervalos de elementos em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="46a1c-105">These features enable more concise, clear syntax to access single elements or ranges of elements in a sequence.</span></span>

<span data-ttu-id="46a1c-106">Neste tutorial, você aprenderá a:</span><span class="sxs-lookup"><span data-stu-id="46a1c-106">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="46a1c-107">Use a sintaxe para intervalos em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="46a1c-107">Use the syntax for ranges in a sequence.</span></span>
> - <span data-ttu-id="46a1c-108">Compreenda as decisões de design para o início e o fim de cada sequência.</span><span class="sxs-lookup"><span data-stu-id="46a1c-108">Understand the design decisions for the start and end of each sequence.</span></span>
> - <span data-ttu-id="46a1c-109">Conheça cenários para os tipos <xref:System.Index> e <xref:System.Range>.</span><span class="sxs-lookup"><span data-stu-id="46a1c-109">Learn scenarios for the <xref:System.Index> and <xref:System.Range> types.</span></span>

## <a name="language-support-for-indices-and-ranges"></a><span data-ttu-id="46a1c-110">Suporte a idioma para intervalos e índices</span><span class="sxs-lookup"><span data-stu-id="46a1c-110">Language support for indices and ranges</span></span>

<span data-ttu-id="46a1c-111">Este suporte à linguagem depende de dois tipos novos e dois operadores novos.</span><span class="sxs-lookup"><span data-stu-id="46a1c-111">This language support relies on two new types and two new operators.</span></span>

- <span data-ttu-id="46a1c-112"><xref:System.Index?displayProperty=nameWithType> representa um índice em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="46a1c-112"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="46a1c-113">O operador `^`, que especifica que um índice é relativo ao final de uma sequência.</span><span class="sxs-lookup"><span data-stu-id="46a1c-113">The `^` operator, which specifies that an index is relative to the end of a sequence.</span></span>
- <span data-ttu-id="46a1c-114"><xref:System.Range?displayProperty=nameWithType> representa um subintervalo de uma sequência.</span><span class="sxs-lookup"><span data-stu-id="46a1c-114"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="46a1c-115">O operador Range (`..`), que especifica o início e o final de um intervalo como seus operandos.</span><span class="sxs-lookup"><span data-stu-id="46a1c-115">The Range operator (`..`), which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="46a1c-116">Vamos começar com as regras para índices.</span><span class="sxs-lookup"><span data-stu-id="46a1c-116">Let's start with the rules for indices.</span></span> <span data-ttu-id="46a1c-117">Considere uma matriz `sequence`.</span><span class="sxs-lookup"><span data-stu-id="46a1c-117">Consider an array `sequence`.</span></span> <span data-ttu-id="46a1c-118">O índice `0` é o mesmo que `sequence[0]`.</span><span class="sxs-lookup"><span data-stu-id="46a1c-118">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="46a1c-119">O índice `^0` é o mesmo que `sequence[sequence.Length]`.</span><span class="sxs-lookup"><span data-stu-id="46a1c-119">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="46a1c-120">Observe que `sequence[^0]` gera uma exceção, assim como `sequence[sequence.Length]` faz.</span><span class="sxs-lookup"><span data-stu-id="46a1c-120">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="46a1c-121">Para qualquer número `n`, o índice `^n` é o mesmo que `sequence[sequence.Length - n]`.</span><span class="sxs-lookup"><span data-stu-id="46a1c-121">For any number `n`, the index `^n` is the same as `sequence[sequence.Length - n]`.</span></span>

```csharp-interactive
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

<span data-ttu-id="46a1c-122">Você pode recuperar a última palavra com o índice `^1`.</span><span class="sxs-lookup"><span data-stu-id="46a1c-122">You can retrieve the last word with the `^1` index.</span></span> <span data-ttu-id="46a1c-123">Adicione o código a seguir abaixo da inicialização:</span><span class="sxs-lookup"><span data-stu-id="46a1c-123">Add the following code below the initialization:</span></span>

[!code-csharp[LastIndex](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

<span data-ttu-id="46a1c-124">Um intervalo especifica o *início* e o *final* de um intervalo.</span><span class="sxs-lookup"><span data-stu-id="46a1c-124">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="46a1c-125">Intervalos são exclusivos, o que significa que *final* não está incluído no intervalo.</span><span class="sxs-lookup"><span data-stu-id="46a1c-125">Ranges are exclusive, meaning the *end* is not included in the range.</span></span> <span data-ttu-id="46a1c-126">O intervalo `[0..^0]` representa todo o intervalo, assim como `[0..sequence.Length]` representa todo o intervalo.</span><span class="sxs-lookup"><span data-stu-id="46a1c-126">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span> 

<span data-ttu-id="46a1c-127">O código a seguir cria um subintervalo com as palavras "quick", "brown" e "fox".</span><span class="sxs-lookup"><span data-stu-id="46a1c-127">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="46a1c-128">Ele inclui `words[1]` até `words[3]`.</span><span class="sxs-lookup"><span data-stu-id="46a1c-128">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="46a1c-129">O elemento `words[4]` não está no intervalo.</span><span class="sxs-lookup"><span data-stu-id="46a1c-129">The element `words[4]` isn't in the range.</span></span> <span data-ttu-id="46a1c-130">Adicione o seguinte código ao mesmo método.</span><span class="sxs-lookup"><span data-stu-id="46a1c-130">Add the following code to the same method.</span></span> <span data-ttu-id="46a1c-131">Copie e cole-o na parte inferior da janela interativa.</span><span class="sxs-lookup"><span data-stu-id="46a1c-131">Copy and paste it at the bottom of the interactive window.</span></span>

[!code-csharp[Range](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

<span data-ttu-id="46a1c-132">O código a seguir cria um subintervalo com "lazy" e "dog".</span><span class="sxs-lookup"><span data-stu-id="46a1c-132">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="46a1c-133">Ele inclui `words[^2]` e `words[^1]`.</span><span class="sxs-lookup"><span data-stu-id="46a1c-133">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="46a1c-134">O índice final `words[^0]` não está incluído.</span><span class="sxs-lookup"><span data-stu-id="46a1c-134">The end index `words[^0]` isn't included.</span></span> <span data-ttu-id="46a1c-135">Adicione o seguinte código também:</span><span class="sxs-lookup"><span data-stu-id="46a1c-135">Add the following code as well:</span></span>

[!code-csharp[LastRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

<span data-ttu-id="46a1c-136">Os exemplos a seguir criam intervalos abertos para o início, fim ou ambos:</span><span class="sxs-lookup"><span data-stu-id="46a1c-136">The following examples create ranges that are open ended for the start, end, or both:</span></span>

[!code-csharp[PartialRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

<span data-ttu-id="46a1c-137">Você também pode declarar intervalos ou índices como variáveis.</span><span class="sxs-lookup"><span data-stu-id="46a1c-137">You can also declare ranges or indices as variables.</span></span> <span data-ttu-id="46a1c-138">A variável então pode ser usada dentro dos caracteres `[` e `]`:</span><span class="sxs-lookup"><span data-stu-id="46a1c-138">The variable can then be used inside the `[` and `]` characters:</span></span>

[!code-csharp[IndexRangeTypes](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

<span data-ttu-id="46a1c-139">O exemplo a seguir mostra muitos dos motivos para essas escolhas.</span><span class="sxs-lookup"><span data-stu-id="46a1c-139">The following sample shows many of the reasons for those choices.</span></span> <span data-ttu-id="46a1c-140">Modifique `x`, `y` e `z` para tentar combinações diferentes.</span><span class="sxs-lookup"><span data-stu-id="46a1c-140">Modify `x`, `y`, and `z` to try different combinations.</span></span> <span data-ttu-id="46a1c-141">Quando você testar, use valores em que `x` é menor que `y` e `y` é menor que `z` para as combinações válidas.</span><span class="sxs-lookup"><span data-stu-id="46a1c-141">When you experiment, use values where `x` is less than `y`, and `y` is less than `z` for valid combinations.</span></span> <span data-ttu-id="46a1c-142">Adicione o seguinte código a um novo método.</span><span class="sxs-lookup"><span data-stu-id="46a1c-142">Add the following code in a new method.</span></span> <span data-ttu-id="46a1c-143">Tente usar combinações diferentes:</span><span class="sxs-lookup"><span data-stu-id="46a1c-143">Try different combinations:</span></span>

[!code-csharp[SemanticsExamples](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="scenarios-for-indices-and-ranges"></a><span data-ttu-id="46a1c-144">Cenários para Intervalos e Índices</span><span class="sxs-lookup"><span data-stu-id="46a1c-144">Scenarios for Indices and Ranges</span></span>

<span data-ttu-id="46a1c-145">Você muitas vezes usará intervalos e índices quando quiser executar uma análise no subintervalo de uma sequência inteira.</span><span class="sxs-lookup"><span data-stu-id="46a1c-145">You'll often use ranges and indices when you want to perform some analysis on subrange of an entire sequence.</span></span> <span data-ttu-id="46a1c-146">A nova sintaxe é mais clara para ler exatamente quais subintervalo está envolvido.</span><span class="sxs-lookup"><span data-stu-id="46a1c-146">The new syntax is clearer in reading exactly what subrange is involved.</span></span> <span data-ttu-id="46a1c-147">A função local `MovingAverage` usa um <xref:System.Range> como seu argumento.</span><span class="sxs-lookup"><span data-stu-id="46a1c-147">The local function `MovingAverage` takes a <xref:System.Range> as its argument.</span></span> <span data-ttu-id="46a1c-148">O método então enumera apenas esse intervalo ao calcular o mínimo, máximo e média.</span><span class="sxs-lookup"><span data-stu-id="46a1c-148">The method then enumerates just that range when calculating the min, max, and average.</span></span> <span data-ttu-id="46a1c-149">Experimente o seguinte código em seu projeto:</span><span class="sxs-lookup"><span data-stu-id="46a1c-149">Try the following code in your project:</span></span>

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

<span data-ttu-id="46a1c-150">Baixe o código concluído no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes).</span><span class="sxs-lookup"><span data-stu-id="46a1c-150">You can download the completed code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) repository.</span></span>
