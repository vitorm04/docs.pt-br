---
description: foreach, in (Referência em C#)
title: Instrução foreach do C#
ms.date: 09/18/2020
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: ea8a6f86595348a32b707caf9782f84147fefc87
ms.sourcegitcommit: 43ed174f085840ca18a791dc89fe833174da766d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/21/2020
ms.locfileid: "90828884"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="0f474-103">foreach, in (Referência em C#)</span><span class="sxs-lookup"><span data-stu-id="0f474-103">foreach, in (C# reference)</span></span>

<span data-ttu-id="0f474-104">A `foreach` instrução executa uma instrução ou um bloco de instruções para cada elemento em uma instância do tipo que implementa a <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface ou, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0f474-104">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface, as the following example shows:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="1" interactive="try-dotnet-method" :::

<span data-ttu-id="0f474-105">A `foreach` instrução não está limitada a esses tipos.</span><span class="sxs-lookup"><span data-stu-id="0f474-105">The `foreach` statement isn't limited to those types.</span></span> <span data-ttu-id="0f474-106">Você pode usá-lo com uma instância de qualquer tipo que atenda às seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="0f474-106">You can use it with an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="0f474-107">Um tipo tem o método público sem parâmetros `GetEnumerator` cujo tipo de retorno é Class, struct ou interface Type.</span><span class="sxs-lookup"><span data-stu-id="0f474-107">A type has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type.</span></span> <span data-ttu-id="0f474-108">A partir do C# 9,0, o `GetEnumerator` método pode ser o [método de extensão](../../programming-guide/classes-and-structs/extension-methods.md)de um tipo.</span><span class="sxs-lookup"><span data-stu-id="0f474-108">Beginning with C# 9.0, the `GetEnumerator` method can be a type's [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>
- <span data-ttu-id="0f474-109">O tipo de retorno do `GetEnumerator` método tem a `Current` propriedade Public e o método público sem parâmetros `MoveNext` cujo tipo de retorno é <xref:System.Boolean> .</span><span class="sxs-lookup"><span data-stu-id="0f474-109">The return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="0f474-110">O exemplo a seguir usa a `foreach` instrução com uma instância do <xref:System.Span%601?displayProperty=nameWithType> tipo, que não implementa nenhuma interface:</span><span class="sxs-lookup"><span data-stu-id="0f474-110">The following example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="2" :::

<span data-ttu-id="0f474-111">A partir do C# 7,3, se a propriedade do enumerador `Current` retornar um [valor de retorno de referência](ref.md#reference-return-values) ( `ref T` em que `T` é o tipo de um elemento de coleção), você poderá declarar uma variável de iteração com o `ref` `ref readonly` modificador ou, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0f474-111">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](ref.md#reference-return-values) (`ref T` where `T` is the type of a collection element), you can declare an iteration variable with the `ref` or `ref readonly` modifier, as the following example shows:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="RefSpan" :::

<span data-ttu-id="0f474-112">A partir do C# 8,0, você pode usar a `await foreach` instrução para consumir um fluxo de dados assíncrono, ou seja, o tipo de coleção que implementa a <xref:System.Collections.Generic.IAsyncEnumerable%601> interface.</span><span class="sxs-lookup"><span data-stu-id="0f474-112">Beginning with C# 8.0, you can use the `await foreach` statement to consume an asynchronous stream of data, that is, the collection type that implements the <xref:System.Collections.Generic.IAsyncEnumerable%601> interface.</span></span> <span data-ttu-id="0f474-113">Cada iteração do loop pode ser suspensa enquanto o próximo elemento é recuperado de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="0f474-113">Each iteration of the loop may be suspended while the next element is retrieved asynchronously.</span></span> <span data-ttu-id="0f474-114">O exemplo a seguir mostra como usar a `await foreach` instrução:</span><span class="sxs-lookup"><span data-stu-id="0f474-114">The following example shows how to use the `await foreach` statement:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="AwaitForeach" :::

<span data-ttu-id="0f474-115">Por padrão, os elementos de fluxo são processados no contexto capturado.</span><span class="sxs-lookup"><span data-stu-id="0f474-115">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="0f474-116">Se você quiser desabilitar a captura do contexto, use o <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> método de extensão.</span><span class="sxs-lookup"><span data-stu-id="0f474-116">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="0f474-117">Para obter mais informações sobre contextos de sincronização e como capturar o contexto atual, consulte [consumindo o padrão assíncrono baseado em tarefa](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="0f474-117">For more information about synchronization contexts and capturing the current context, see [Consuming the Task-based asynchronous pattern](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span> <span data-ttu-id="0f474-118">Para obter mais informações sobre fluxos assíncronos, consulte a seção [fluxos assíncronos](../../whats-new/csharp-8.md#asynchronous-streams) do artigo [novidades no C# 8,0](../../whats-new/csharp-8.md) .</span><span class="sxs-lookup"><span data-stu-id="0f474-118">For more information about asynchronous streams, see the [Asynchronous streams](../../whats-new/csharp-8.md#asynchronous-streams) section of the [What's new in C# 8.0](../../whats-new/csharp-8.md) article.</span></span>

<span data-ttu-id="0f474-119">Em qualquer ponto dentro do bloco de instrução `foreach`, você pode sair do loop usando a instrução [break](break.md) ou seguir para a próxima iteração no loop usando a instrução [continue](continue.md).</span><span class="sxs-lookup"><span data-stu-id="0f474-119">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="0f474-120">Você também pode sair de um `foreach` loop pelas instruções [goto](goto.md), [Return](return.md)ou [throw](throw.md) .</span><span class="sxs-lookup"><span data-stu-id="0f474-120">You can also exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

<span data-ttu-id="0f474-121">Se a instrução `foreach` for aplicada a `null`, uma <xref:System.NullReferenceException> será gerada.</span><span class="sxs-lookup"><span data-stu-id="0f474-121">If the `foreach` statement is applied to `null`, a <xref:System.NullReferenceException> is thrown.</span></span> <span data-ttu-id="0f474-122">Se a coleção de origem da `foreach` instrução estiver vazia, o corpo do `foreach` loop não será executado e ignorado.</span><span class="sxs-lookup"><span data-stu-id="0f474-122">If the source collection of the `foreach` statement is empty, the body of the `foreach` loop isn't executed and skipped.</span></span>

## <a name="type-of-an-iteration-variable"></a><span data-ttu-id="0f474-123">Tipo de uma variável de iteração</span><span class="sxs-lookup"><span data-stu-id="0f474-123">Type of an iteration variable</span></span>

<span data-ttu-id="0f474-124">Você pode usar a `var` palavra-chave para permitir que o compilador inferir o tipo de uma variável de iteração na `foreach` instrução, como mostra o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="0f474-124">You can use the `var` keyword to let the compiler infer the type of an iteration variable in the `foreach` statement, as the following code shows:</span></span>

```csharp
foreach (var item in collection) { }
```

<span data-ttu-id="0f474-125">Você também pode especificar explicitamente o tipo de uma variável de iteração, como mostra o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="0f474-125">You can also explicitly specify the type of an iteration variable, as the following code shows:</span></span>

```csharp
IEnumerable<T> collection = new T[5];
foreach (V item in collection) { }
```

<span data-ttu-id="0f474-126">No formulário anterior, o tipo `T` de um elemento de coleção deve ser implicitamente ou explicitamente conversível para `V` o tipo de uma variável de iteração.</span><span class="sxs-lookup"><span data-stu-id="0f474-126">In the preceding form, type `T` of a collection element must be implicitly or explicitly convertible to type `V` of an iteration variable.</span></span> <span data-ttu-id="0f474-127">Se uma conversão explícita de `T` para `V` falhar em tempo de execução, a `foreach` instrução lançará um <xref:System.InvalidCastException> .</span><span class="sxs-lookup"><span data-stu-id="0f474-127">If an explicit conversion from `T` to `V` fails at run time, the `foreach` statement throws an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="0f474-128">Por exemplo, se `T` for um tipo de classe não lacrado, `V` pode ser qualquer tipo de interface, até mesmo aquele que `T` não implementa.</span><span class="sxs-lookup"><span data-stu-id="0f474-128">For example, if `T` is a non-sealed class type, `V` can be any interface type, even the one that `T` doesn't implement.</span></span> <span data-ttu-id="0f474-129">No tempo de execução, o tipo de um elemento de coleção pode ser o que deriva de `T` e realmente implementa `V` .</span><span class="sxs-lookup"><span data-stu-id="0f474-129">At run time, the type of a collection element may be the one that derives from `T` and actually implements `V`.</span></span> <span data-ttu-id="0f474-130">Se esse não for o caso, um <xref:System.InvalidCastException> será lançado.</span><span class="sxs-lookup"><span data-stu-id="0f474-130">If that's not the case, an <xref:System.InvalidCastException> is thrown.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0f474-131">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="0f474-131">C# language specification</span></span>

<span data-ttu-id="0f474-132">Para obter mais informações, confira a seção [A instrução foreach](~/_csharplang/spec/statements.md#the-foreach-statement) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="0f474-132">For more information, see [The foreach statement](~/_csharplang/spec/statements.md#the-foreach-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="0f474-133">Para obter mais informações sobre os recursos adicionados em C# 8,0 e posterior, consulte as seguintes notas de proposta de recurso:</span><span class="sxs-lookup"><span data-stu-id="0f474-133">For more information about features added in C# 8.0 and later, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="0f474-134">Fluxos assíncronos (C# 8,0)</span><span class="sxs-lookup"><span data-stu-id="0f474-134">Async streams (C# 8.0)</span></span>](~/_csharplang/proposals/csharp-8.0/async-streams.md)
- [<span data-ttu-id="0f474-135">`GetEnumerator`Suporte de extensão para `foreach` loops (C# 9,0)</span><span class="sxs-lookup"><span data-stu-id="0f474-135">Extension `GetEnumerator` support for `foreach` loops (C# 9.0)</span></span>](~/_csharplang/proposals/csharp-9.0/extension-getenumerator.md)

## <a name="see-also"></a><span data-ttu-id="0f474-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f474-136">See also</span></span>

- [<span data-ttu-id="0f474-137">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="0f474-137">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0f474-138">Palavras-chave de C#</span><span class="sxs-lookup"><span data-stu-id="0f474-138">C# keywords</span></span>](index.md)
- [<span data-ttu-id="0f474-139">Usando foreach com matrizes</span><span class="sxs-lookup"><span data-stu-id="0f474-139">Using foreach with arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="0f474-140">Instrução for</span><span class="sxs-lookup"><span data-stu-id="0f474-140">for statement</span></span>](for.md)
