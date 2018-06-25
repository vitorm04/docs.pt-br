---
title: foreach, in (Referência de C#)
ms.date: 05/24/2018
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 7613590686f7f7ec6439da4a2bb672e524ab01e8
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34565700"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="42464-102">foreach, in (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="42464-102">foreach, in (C# Reference)</span></span>

<span data-ttu-id="42464-103">A instrução `foreach` executa uma instrução ou um bloco de instruções para cada elemento em uma instância do tipo que implementa a interface <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="42464-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="42464-104">A instrução `foreach` não está limitada a esses tipos e pode ser aplicada a uma instância de qualquer tipo que satisfaça as seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="42464-104">The `foreach` statement is not limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="42464-105">incluir um método `GetEnumerator` público sem parâmetros, cujo tipo de retorno é um tipo de classe, estrutura ou interface,</span><span class="sxs-lookup"><span data-stu-id="42464-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="42464-106">o tipo de retorno do método `GetEnumerator` tem a propriedade `Current` pública e o método `MoveNext` público sem parâmetros, cujo tipo de retorno é <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="42464-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="42464-107">Em qualquer ponto dentro do bloco de instrução `foreach`, você pode sair do loop usando a instrução [break](break.md) ou seguir para a próxima iteração no loop usando a instrução [continue](continue.md).</span><span class="sxs-lookup"><span data-stu-id="42464-107">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="42464-108">Você também pode sair de um loop `foreach` com a instrução [goto](goto.md), [return](return.md) ou [throw](throw.md).</span><span class="sxs-lookup"><span data-stu-id="42464-108">You also can exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="examples"></a><span data-ttu-id="42464-109">Exemplos</span><span class="sxs-lookup"><span data-stu-id="42464-109">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="42464-110">O exemplo a seguir mostra o uso da instrução `foreach` com uma instância do tipo <xref:System.Collections.Generic.List%601> que implementa a interface <xref:System.Collections.Generic.IEnumerable%601>:</span><span class="sxs-lookup"><span data-stu-id="42464-110">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

<span data-ttu-id="42464-111">O exemplo a seguir usa a instrução `foreach` com uma instância do tipo <xref:System.Span%601?displayProperty=nameWithType>, que não implementa nenhuma interface:</span><span class="sxs-lookup"><span data-stu-id="42464-111">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

[!code-csharp-interactive[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="42464-112">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="42464-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="42464-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="42464-113">See also</span></span>

[<span data-ttu-id="42464-114">A instrução foreach (especificação da linguagem C#)</span><span class="sxs-lookup"><span data-stu-id="42464-114">The foreach statement (C# language specification)</span></span>](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)  
[<span data-ttu-id="42464-115">Usando foreach com matrizes</span><span class="sxs-lookup"><span data-stu-id="42464-115">Using foreach with Arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)  
[<span data-ttu-id="42464-116">for</span><span class="sxs-lookup"><span data-stu-id="42464-116">for</span></span>](for.md)  
[<span data-ttu-id="42464-117">Instruções de iteração</span><span class="sxs-lookup"><span data-stu-id="42464-117">Iteration Statements</span></span>](iteration-statements.md)  
[<span data-ttu-id="42464-118">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="42464-118">C# Keywords</span></span>](index.md)  
[<span data-ttu-id="42464-119">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="42464-119">C# Reference</span></span>](../index.md)  
[<span data-ttu-id="42464-120">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="42464-120">C# Programming Guide</span></span>](../../programming-guide/index.md)  