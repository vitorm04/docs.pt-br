---
title: Instrução foreach do C#
ms.date: 05/17/2019
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 188d909fd33b14755d9b121953b1fa434ecf536d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738811"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="068a0-102">foreach, in (Referência em C#)</span><span class="sxs-lookup"><span data-stu-id="068a0-102">foreach, in (C# reference)</span></span>

<span data-ttu-id="068a0-103">A instrução `foreach` executa uma instrução ou um bloco de instruções para cada elemento em uma instância do tipo que implementa a interface <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="068a0-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="068a0-104">A instrução `foreach` não está limitada a esses tipos e pode ser aplicada a uma instância de qualquer tipo que satisfaça as seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="068a0-104">The `foreach` statement is not limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="068a0-105">incluir um método `GetEnumerator` público sem parâmetros, cujo tipo de retorno é um tipo de classe, estrutura ou interface,</span><span class="sxs-lookup"><span data-stu-id="068a0-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="068a0-106">o tipo de retorno do método `GetEnumerator` tem a propriedade `Current` pública e o método `MoveNext` público sem parâmetros, cujo tipo de retorno é <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="068a0-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="068a0-107">Começando com C# 7.3, se a `Current` propriedade do enumerador`ref T` `T` retornar um valor de retorno [de referência](ref.md#reference-return-values) (onde está `ref` `ref readonly` o tipo do elemento de coleta), você pode declarar a variável de iteração com o ou modificador.</span><span class="sxs-lookup"><span data-stu-id="068a0-107">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](ref.md#reference-return-values) (`ref T` where `T` is the type of the collection element), you can declare the iteration variable with the `ref` or `ref readonly` modifier.</span></span>

<span data-ttu-id="068a0-108">A partir de C# `await` 8.0, o `foreach` operador pode ser aplicado <xref:System.Collections.Generic.IAsyncEnumerable%601> à declaração quando o tipo de coleta implementa a interface.</span><span class="sxs-lookup"><span data-stu-id="068a0-108">Beginning with C# 8.0, the `await` operator may be applied to the `foreach` statement when the collection type implements the <xref:System.Collections.Generic.IAsyncEnumerable%601> interface.</span></span> <span data-ttu-id="068a0-109">Cada iteração do loop pode ser suspensa enquanto o próximo elemento é recuperado assíncronamente.</span><span class="sxs-lookup"><span data-stu-id="068a0-109">Each iteration of the loop may be suspended while the next element is retrieved asynchronously.</span></span> <span data-ttu-id="068a0-110">Por padrão, os elementos de fluxo são processados no contexto capturado.</span><span class="sxs-lookup"><span data-stu-id="068a0-110">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="068a0-111">Se você quiser desativar a captura do <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> contexto, use o método de extensão.</span><span class="sxs-lookup"><span data-stu-id="068a0-111">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="068a0-112">Para obter mais informações sobre contextos de sincronização e captura do contexto atual, consulte o artigo sobre [o consumo do padrão assíncrono baseado em tarefas](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="068a0-112">For more information about synchronization contexts and capturing the current context, see the article on [consuming the Task-based asynchronous pattern](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span>

<span data-ttu-id="068a0-113">Em qualquer ponto dentro do bloco de instrução `foreach`, você pode sair do loop usando a instrução [break](break.md) ou seguir para a próxima iteração no loop usando a instrução [continue](continue.md).</span><span class="sxs-lookup"><span data-stu-id="068a0-113">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="068a0-114">Você também pode `foreach` sair de um loop pelas declarações [goto](goto.md), [return](return.md)ou [throw.](throw.md)</span><span class="sxs-lookup"><span data-stu-id="068a0-114">You can also exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

<span data-ttu-id="068a0-115">Se a instrução `foreach` for aplicada a `null`, uma <xref:System.NullReferenceException> será gerada.</span><span class="sxs-lookup"><span data-stu-id="068a0-115">If the `foreach` statement is applied to `null`, a <xref:System.NullReferenceException> is thrown.</span></span> <span data-ttu-id="068a0-116">Se a coleta `foreach` de origem da declaração `foreach` estiver vazia, o corpo do laço não é executado e pulado.</span><span class="sxs-lookup"><span data-stu-id="068a0-116">If the source collection of the `foreach` statement is empty, the body of the `foreach` loop isn't executed and skipped.</span></span>

## <a name="examples"></a><span data-ttu-id="068a0-117">Exemplos</span><span class="sxs-lookup"><span data-stu-id="068a0-117">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="068a0-118">O exemplo a seguir mostra o uso da instrução `foreach` com uma instância do tipo <xref:System.Collections.Generic.List%601> que implementa a interface <xref:System.Collections.Generic.IEnumerable%601>:</span><span class="sxs-lookup"><span data-stu-id="068a0-118">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

<span data-ttu-id="068a0-119">O exemplo a seguir usa a instrução `foreach` com uma instância do tipo <xref:System.Span%601?displayProperty=nameWithType>, que não implementa nenhuma interface:</span><span class="sxs-lookup"><span data-stu-id="068a0-119">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

[!code-csharp[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

<span data-ttu-id="068a0-120">O exemplo a seguir usa uma variável de iteração `ref` para definir o valor de cada item em uma matriz stackalloc.</span><span class="sxs-lookup"><span data-stu-id="068a0-120">The following example uses a `ref` iteration variable to set the value of each item in a stackalloc array.</span></span> <span data-ttu-id="068a0-121">A versão `ref readonly` itera a coleção para imprimir todos os valores.</span><span class="sxs-lookup"><span data-stu-id="068a0-121">The `ref readonly` version iterates the collection to print all the values.</span></span> <span data-ttu-id="068a0-122">A declaração `readonly` usa uma declaração de variável local implícita.</span><span class="sxs-lookup"><span data-stu-id="068a0-122">The `readonly` declaration uses an implicit local variable declaration.</span></span> <span data-ttu-id="068a0-123">Declarações de variável implícita podem ser usadas com declarações `ref` ou `ref readonly`, assim como declarações de variável tipadas explicitamente.</span><span class="sxs-lookup"><span data-stu-id="068a0-123">Implicit variable declarations can be used with either `ref` or `ref readonly` declarations, as can explicitly typed variable declarations.</span></span>

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

<span data-ttu-id="068a0-124">O exemplo `await foreach` a seguir usa para iterar uma coleção que gera cada elemento assíncronamente:</span><span class="sxs-lookup"><span data-stu-id="068a0-124">The following example uses `await foreach` to iterate a collection that generates each element asynchronously:</span></span>

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#AwaitForeach)]

## <a name="c-language-specification"></a><span data-ttu-id="068a0-125">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="068a0-125">C# language specification</span></span>

<span data-ttu-id="068a0-126">Para obter mais informações, confira a seção [A instrução foreach](~/_csharplang/spec/statements.md#the-foreach-statement) na [Especificação da linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="068a0-126">For more information, see [The foreach statement](~/_csharplang/spec/statements.md#the-foreach-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="068a0-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="068a0-127">See also</span></span>

- [<span data-ttu-id="068a0-128">C# Referência</span><span class="sxs-lookup"><span data-stu-id="068a0-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="068a0-129">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="068a0-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="068a0-130">C# Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="068a0-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="068a0-131">Usando foreach com matrizes</span><span class="sxs-lookup"><span data-stu-id="068a0-131">Using foreach with arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="068a0-132">para declaração</span><span class="sxs-lookup"><span data-stu-id="068a0-132">for statement</span></span>](for.md)
