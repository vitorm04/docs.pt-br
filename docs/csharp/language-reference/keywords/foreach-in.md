---
title: foreach, in (Referência de C#)
ms.date: 06/29/2018
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: a6397cdc9d1e36423a14158a57ca2c1b3fe9df17
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874956"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="af00b-102">foreach, in (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="af00b-102">foreach, in (C# Reference)</span></span>

<span data-ttu-id="af00b-103">A instrução `foreach` executa uma instrução ou um bloco de instruções para cada elemento em uma instância do tipo que implementa a interface <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="af00b-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="af00b-104">A instrução `foreach` não está limitada a esses tipos e pode ser aplicada a uma instância de qualquer tipo que satisfaça as seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="af00b-104">The `foreach` statement is not limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="af00b-105">incluir um método `GetEnumerator` público sem parâmetros, cujo tipo de retorno é um tipo de classe, estrutura ou interface,</span><span class="sxs-lookup"><span data-stu-id="af00b-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="af00b-106">o tipo de retorno do método `GetEnumerator` tem a propriedade `Current` pública e o método `MoveNext` público sem parâmetros, cujo tipo de retorno é <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="af00b-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="af00b-107">Em qualquer ponto dentro do bloco de instrução `foreach`, você pode sair do loop usando a instrução [break](break.md) ou seguir para a próxima iteração no loop usando a instrução [continue](continue.md).</span><span class="sxs-lookup"><span data-stu-id="af00b-107">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="af00b-108">Você também pode sair de um loop `foreach` com a instrução [goto](goto.md), [return](return.md) ou [throw](throw.md).</span><span class="sxs-lookup"><span data-stu-id="af00b-108">You also can exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="examples"></a><span data-ttu-id="af00b-109">Exemplos</span><span class="sxs-lookup"><span data-stu-id="af00b-109">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="af00b-110">O exemplo a seguir mostra o uso da instrução `foreach` com uma instância do tipo <xref:System.Collections.Generic.List%601> que implementa a interface <xref:System.Collections.Generic.IEnumerable%601>:</span><span class="sxs-lookup"><span data-stu-id="af00b-110">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

<span data-ttu-id="af00b-111">O exemplo a seguir usa a instrução `foreach` com uma instância do tipo <xref:System.Span%601?displayProperty=nameWithType>, que não implementa nenhuma interface:</span><span class="sxs-lookup"><span data-stu-id="af00b-111">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

[!code-csharp-interactive[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

<span data-ttu-id="af00b-112">A partir do C# 7.3, se a propriedade `Current` do enumerador retornar um [valor retornado da referência](../../programming-guide/classes-and-structs/ref-returns.md) (`ref T`, em que `T` é o tipo do elemento da coleção), será possível declarar a variável de iteração com o modificador `ref` ou `ref readonly`.</span><span class="sxs-lookup"><span data-stu-id="af00b-112">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](../../programming-guide/classes-and-structs/ref-returns.md) (`ref T` where `T` is the type of the collection element), you can declare the iteration variable with the `ref` or `ref readonly` modifier.</span></span> <span data-ttu-id="af00b-113">O exemplo a seguir usa uma variável de iteração `ref` para definir o valor de cada item em uma matriz stackalloc.</span><span class="sxs-lookup"><span data-stu-id="af00b-113">The following example uses a `ref` iteration variable to set the value of each item in a stackalloc array.</span></span> <span data-ttu-id="af00b-114">A versão `ref readonly` itera a coleção para imprimir todos os valores.</span><span class="sxs-lookup"><span data-stu-id="af00b-114">The `ref readonly` version iterates the collection to print all the values.</span></span> <span data-ttu-id="af00b-115">A declaração `readonly` usa uma declaração de variável local implícita.</span><span class="sxs-lookup"><span data-stu-id="af00b-115">The `readonly` declaration uses an implicit local variable declaration.</span></span> <span data-ttu-id="af00b-116">Declarações de variável implícita podem ser usadas com declarações `ref` ou `ref readonly`, assim como declarações de variável tipadas explicitamente.</span><span class="sxs-lookup"><span data-stu-id="af00b-116">Implicit variable declarations can be used with either `ref` or `ref readonly` declarations, as can explicitly typed variable declarations.</span></span>

[!code-csharp-interactive[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

## <a name="c-language-specification"></a><span data-ttu-id="af00b-117">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="af00b-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="af00b-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af00b-118">See also</span></span>

[<span data-ttu-id="af00b-119">A instrução foreach (especificação da linguagem C#)</span><span class="sxs-lookup"><span data-stu-id="af00b-119">The foreach statement (C# language specification)</span></span>](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)  
[<span data-ttu-id="af00b-120">Usando foreach com matrizes</span><span class="sxs-lookup"><span data-stu-id="af00b-120">Using foreach with Arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)  
[<span data-ttu-id="af00b-121">for</span><span class="sxs-lookup"><span data-stu-id="af00b-121">for</span></span>](for.md)  
[<span data-ttu-id="af00b-122">Instruções de iteração</span><span class="sxs-lookup"><span data-stu-id="af00b-122">Iteration Statements</span></span>](iteration-statements.md)  
[<span data-ttu-id="af00b-123">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="af00b-123">C# Keywords</span></span>](index.md)  
[<span data-ttu-id="af00b-124">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="af00b-124">C# Reference</span></span>](../index.md)  
[<span data-ttu-id="af00b-125">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="af00b-125">C# Programming Guide</span></span>](../../programming-guide/index.md)  
