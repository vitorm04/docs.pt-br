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
ms.openlocfilehash: af4850b4c33727c818fb5a67d17fb6146627fa06
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67267740"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="0c9d3-102">foreach, in (Referência em C#)</span><span class="sxs-lookup"><span data-stu-id="0c9d3-102">foreach, in (C# reference)</span></span>

<span data-ttu-id="0c9d3-103">A instrução `foreach` executa uma instrução ou um bloco de instruções para cada elemento em uma instância do tipo que implementa a interface <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0c9d3-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="0c9d3-104">A instrução `foreach` não está limitada a esses tipos e pode ser aplicada a uma instância de qualquer tipo que satisfaça as seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="0c9d3-104">The `foreach` statement is not limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="0c9d3-105">incluir um método `GetEnumerator` público sem parâmetros, cujo tipo de retorno é um tipo de classe, estrutura ou interface,</span><span class="sxs-lookup"><span data-stu-id="0c9d3-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="0c9d3-106">o tipo de retorno do método `GetEnumerator` tem a propriedade `Current` pública e o método `MoveNext` público sem parâmetros, cujo tipo de retorno é <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="0c9d3-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="0c9d3-107">A partir do C# 7.3, se a propriedade `Current` do enumerador retornar um [valor retornado da referência](ref.md#reference-return-values) (`ref T`, em que `T` é o tipo do elemento da coleção), será possível declarar a variável de iteração com o modificador `ref` ou `ref readonly`.</span><span class="sxs-lookup"><span data-stu-id="0c9d3-107">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](ref.md#reference-return-values) (`ref T` where `T` is the type of the collection element), you can declare the iteration variable with the `ref` or `ref readonly` modifier.</span></span>

<span data-ttu-id="0c9d3-108">Em qualquer ponto dentro do bloco de instrução `foreach`, você pode sair do loop usando a instrução [break](break.md) ou seguir para a próxima iteração no loop usando a instrução [continue](continue.md).</span><span class="sxs-lookup"><span data-stu-id="0c9d3-108">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="0c9d3-109">Você também pode sair de um loop `foreach` com a instrução [goto](goto.md), [return](return.md) ou [throw](throw.md).</span><span class="sxs-lookup"><span data-stu-id="0c9d3-109">You also can exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

<span data-ttu-id="0c9d3-110">Se a instrução `foreach` for aplicada a `null`, uma <xref:System.NullReferenceException> será gerada.</span><span class="sxs-lookup"><span data-stu-id="0c9d3-110">If the `foreach` statement is applied to `null`, a <xref:System.NullReferenceException> is thrown.</span></span> <span data-ttu-id="0c9d3-111">Se a coleção de origem da instrução `foreach` estiver vazia, o corpo do loop `foreach` não será executado e será ignorado.</span><span class="sxs-lookup"><span data-stu-id="0c9d3-111">If the source collection of the `foreach` statement is empty, the body of the `foreach` loop is not executed and skipped.</span></span>

## <a name="examples"></a><span data-ttu-id="0c9d3-112">Exemplos</span><span class="sxs-lookup"><span data-stu-id="0c9d3-112">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="0c9d3-113">O exemplo a seguir mostra o uso da instrução `foreach` com uma instância do tipo <xref:System.Collections.Generic.List%601> que implementa a interface <xref:System.Collections.Generic.IEnumerable%601>:</span><span class="sxs-lookup"><span data-stu-id="0c9d3-113">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

<span data-ttu-id="0c9d3-114">O exemplo a seguir usa a instrução `foreach` com uma instância do tipo <xref:System.Span%601?displayProperty=nameWithType>, que não implementa nenhuma interface:</span><span class="sxs-lookup"><span data-stu-id="0c9d3-114">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

[!code-csharp[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

<span data-ttu-id="0c9d3-115">O exemplo a seguir usa uma variável de iteração `ref` para definir o valor de cada item em uma matriz stackalloc.</span><span class="sxs-lookup"><span data-stu-id="0c9d3-115">The following example uses a `ref` iteration variable to set the value of each item in a stackalloc array.</span></span> <span data-ttu-id="0c9d3-116">A versão `ref readonly` itera a coleção para imprimir todos os valores.</span><span class="sxs-lookup"><span data-stu-id="0c9d3-116">The `ref readonly` version iterates the collection to print all the values.</span></span> <span data-ttu-id="0c9d3-117">A declaração `readonly` usa uma declaração de variável local implícita.</span><span class="sxs-lookup"><span data-stu-id="0c9d3-117">The `readonly` declaration uses an implicit local variable declaration.</span></span> <span data-ttu-id="0c9d3-118">Declarações de variável implícita podem ser usadas com declarações `ref` ou `ref readonly`, assim como declarações de variável tipadas explicitamente.</span><span class="sxs-lookup"><span data-stu-id="0c9d3-118">Implicit variable declarations can be used with either `ref` or `ref readonly` declarations, as can explicitly typed variable declarations.</span></span>

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

## <a name="c-language-specification"></a><span data-ttu-id="0c9d3-119">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="0c9d3-119">C# language specification</span></span>

<span data-ttu-id="0c9d3-120">Para obter mais informações, confira a seção [A instrução foreach](~/_csharplang/spec/statements.md#the-foreach-statement) na [Especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="0c9d3-120">For more information, see [The foreach statement](~/_csharplang/spec/statements.md#the-foreach-statement) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0c9d3-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0c9d3-121">See also</span></span>

- [<span data-ttu-id="0c9d3-122">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="0c9d3-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0c9d3-123">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="0c9d3-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0c9d3-124">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="0c9d3-124">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="0c9d3-125">Usar foreach com matrizes</span><span class="sxs-lookup"><span data-stu-id="0c9d3-125">Using foreach with arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="0c9d3-126">instrução for</span><span class="sxs-lookup"><span data-stu-id="0c9d3-126">for statement</span></span>](for.md)
