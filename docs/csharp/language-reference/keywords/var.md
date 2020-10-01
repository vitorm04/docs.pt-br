---
description: referência de var-C#
title: referência de var-C#
ms.date: 10/02/2020
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: d04bea9bcf5be726d3e81a1a53abed31f59330a0
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608706"
---
# <a name="var-c-reference"></a><span data-ttu-id="5caad-103">var (referência C#)</span><span class="sxs-lookup"><span data-stu-id="5caad-103">var (C# reference)</span></span>

<span data-ttu-id="5caad-104">Começando com o C# 3, as variáveis que são declaradas no escopo do método podem ter um "tipo" implícito `var` .</span><span class="sxs-lookup"><span data-stu-id="5caad-104">Beginning with C# 3, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="5caad-105">Uma variável local de tipo implícito é fortemente tipada, como se você mesmo tivesse declarado o tipo, mas o compilador determina o tipo.</span><span class="sxs-lookup"><span data-stu-id="5caad-105">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="5caad-106">As duas declarações a seguir de `i` são funcionalmente equivalentes:</span><span class="sxs-lookup"><span data-stu-id="5caad-106">The following two declarations of `i` are functionally equivalent:</span></span>

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

> [!IMPORTANT]
> <span data-ttu-id="5caad-107">Quando `var` é usado com [tipos de referência anuláveis](../builtin-types/nullable-reference-types.md) habilitados, ele sempre implica um tipo de referência anulável mesmo que o tipo de expressão não seja anulável.</span><span class="sxs-lookup"><span data-stu-id="5caad-107">When `var` is used with [nullable reference types](../builtin-types/nullable-reference-types.md) enabled, it always implies a nullable reference type even if the expression type isn't nullable.</span></span>

<span data-ttu-id="5caad-108">Um uso comum da `var` palavra-chave é com expressões de invocação de construtor.</span><span class="sxs-lookup"><span data-stu-id="5caad-108">A common use of the `var` keyword is with constructor invocation expressions.</span></span> <span data-ttu-id="5caad-109">O uso de `var` permite que você não repita um nome de tipo em uma declaração de variável e instanciação de objeto, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="5caad-109">The use of `var` allows you to not repeat a type name in a variable declaration and object instantiation, as the following example shows:</span></span>

```csharp
var xs = new List<int>();
```

<span data-ttu-id="5caad-110">A partir do C# 9,0, você pode usar uma [ `new` expressão](../operators/new-operator.md) de tipo de destino como alternativa:</span><span class="sxs-lookup"><span data-stu-id="5caad-110">Beginning with C# 9.0, you can use a target-typed [`new` expression](../operators/new-operator.md) as an alternative:</span></span>

```csharp
List<int> xs = new();
List<int>? ys = new();
```

## <a name="example"></a><span data-ttu-id="5caad-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5caad-111">Example</span></span>

<span data-ttu-id="5caad-112">O exemplo a seguir mostra duas expressões de consulta.</span><span class="sxs-lookup"><span data-stu-id="5caad-112">The following example shows two query expressions.</span></span> <span data-ttu-id="5caad-113">Na primeira expressão, o uso de `var` é permitido, mas não é necessário, pois o tipo do resultado da consulta pode ser declarado explicitamente como um `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="5caad-113">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="5caad-114">No entanto, na segunda expressão, `var` permite que o resultado seja uma coleção de tipos anônimos e o nome desse tipo não é acessível, exceto para o próprio compilador.</span><span class="sxs-lookup"><span data-stu-id="5caad-114">However, in the second expression, `var` allows the result to be a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="5caad-115">O uso de `var` elimina a necessidade de criar uma nova classe para o resultado.</span><span class="sxs-lookup"><span data-stu-id="5caad-115">Use of `var` eliminates the requirement to create a new class for the result.</span></span> <span data-ttu-id="5caad-116">Observe que no exemplo 2, a variável de iteração `foreach``item` também deve ser implicitamente tipada.</span><span class="sxs-lookup"><span data-stu-id="5caad-116">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a><span data-ttu-id="5caad-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="5caad-117">See also</span></span>

- [<span data-ttu-id="5caad-118">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="5caad-118">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5caad-119">Variáveis locais digitadas implicitamente</span><span class="sxs-lookup"><span data-stu-id="5caad-119">Implicitly typed local variables</span></span>](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
- [<span data-ttu-id="5caad-120">Relações de tipo em operações de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="5caad-120">Type relationships in LINQ query operations</span></span>](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)
