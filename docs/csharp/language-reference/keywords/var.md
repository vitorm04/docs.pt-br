---
description: var – Referência de C#
title: var – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: 303a880a54a79e50515060e0ea28e8d021fa1b76
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141706"
---
# <a name="var-c-reference"></a><span data-ttu-id="e4167-103">var (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="e4167-103">var (C# Reference)</span></span>

<span data-ttu-id="e4167-104">Começando com o Visual C# 3.0, as variáveis que são declaradas no escopo do método podem ter um “tipo” implícito `var`.</span><span class="sxs-lookup"><span data-stu-id="e4167-104">Beginning in Visual C# 3.0, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="e4167-105">Uma variável local de tipo implícito é fortemente tipada, como se você mesmo tivesse declarado o tipo, mas o compilador determina o tipo.</span><span class="sxs-lookup"><span data-stu-id="e4167-105">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="e4167-106">As duas declarações a seguir de `i` são funcionalmente equivalentes:</span><span class="sxs-lookup"><span data-stu-id="e4167-106">The following two declarations of `i` are functionally equivalent:</span></span>

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

<span data-ttu-id="e4167-107">Para obter mais informações, consulte [variáveis locais digitadas implicitamente](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) e [relações de tipo em operações de consulta LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="e4167-107">For more information, see [Implicitly Typed Local Variables](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) and [Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e4167-108">Quando `var` é usado com tipos de referência anuláveis habilitados, ele sempre implica um tipo de referência anulável mesmo que o tipo de expressão não seja anulável.</span><span class="sxs-lookup"><span data-stu-id="e4167-108">When `var` is used with nullable reference types enabled, it always implies a nullable reference type even if the expression type isn't nullable.</span></span>

## <a name="example"></a><span data-ttu-id="e4167-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e4167-109">Example</span></span>

<span data-ttu-id="e4167-110">O exemplo a seguir mostra duas expressões de consulta.</span><span class="sxs-lookup"><span data-stu-id="e4167-110">The following example shows two query expressions.</span></span> <span data-ttu-id="e4167-111">Na primeira expressão, o uso de `var` é permitido, mas não é necessário, pois o tipo do resultado da consulta pode ser declarado explicitamente como um `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="e4167-111">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="e4167-112">No entanto, na segunda expressão, `var` permite que o resultado seja uma coleção de tipos anônimos e o nome desse tipo não é acessível, exceto para o próprio compilador.</span><span class="sxs-lookup"><span data-stu-id="e4167-112">However, in the second expression, `var` allows the result to be a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="e4167-113">O uso de `var` elimina a necessidade de criar uma nova classe para o resultado.</span><span class="sxs-lookup"><span data-stu-id="e4167-113">Use of `var` eliminates the requirement to create a new class for the result.</span></span> <span data-ttu-id="e4167-114">Observe que no exemplo 2, a variável de iteração `foreach``item` também deve ser implicitamente tipada.</span><span class="sxs-lookup"><span data-stu-id="e4167-114">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a><span data-ttu-id="e4167-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="e4167-115">See also</span></span>

- [<span data-ttu-id="e4167-116">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="e4167-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e4167-117">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="e4167-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e4167-118">Variáveis Locais Tipadas Implicitamente</span><span class="sxs-lookup"><span data-stu-id="e4167-118">Implicitly Typed Local Variables</span></span>](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
