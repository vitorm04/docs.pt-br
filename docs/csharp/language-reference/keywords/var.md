---
title: var (Referência de C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
caps.latest.revision: 13
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d2be56243f9c4ddafb3903d14fa6d6f9cb0e2f84
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="var-c-reference"></a><span data-ttu-id="bf4de-102">var (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="bf4de-102">var (C# Reference)</span></span>
<span data-ttu-id="bf4de-103">Começando com o Visual C# 3.0, as variáveis que são declaradas no escopo do método podem ter um “tipo” implícito `var`.</span><span class="sxs-lookup"><span data-stu-id="bf4de-103">Beginning in Visual C# 3.0, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="bf4de-104">Uma variável local de tipo implícito é fortemente tipada, como se você mesmo tivesse declarado o tipo, mas o compilador determina o tipo.</span><span class="sxs-lookup"><span data-stu-id="bf4de-104">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="bf4de-105">As duas declarações a seguir de `i` são funcionalmente equivalentes:</span><span class="sxs-lookup"><span data-stu-id="bf4de-105">The following two declarations of `i` are functionally equivalent:</span></span>  
  
```  
var i = 10; // implicitly typed  
int i = 10; //explicitly typed  
```  
  
 <span data-ttu-id="bf4de-106">Para obter mais informações, consulte [Variáveis locais de tipo implícito](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) e [Relacionamentos de tipo em operações de consulta LINQ](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="bf4de-106">For more information, see [Implicitly Typed Local Variables](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) and [Type Relationships in LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf4de-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bf4de-107">Example</span></span>  
 <span data-ttu-id="bf4de-108">O exemplo a seguir mostra duas expressões de consulta.</span><span class="sxs-lookup"><span data-stu-id="bf4de-108">The following example shows two query expressions.</span></span> <span data-ttu-id="bf4de-109">Na primeira expressão, o uso de `var` é permitido, mas não é necessário, pois o tipo do resultado da consulta pode ser declarado explicitamente como um `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="bf4de-109">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="bf4de-110">No entanto, na segunda expressão, `var` deve ser usado porque o resultado é uma coleção de tipos anônimos e o nome desse tipo não é acessível, exceto para o próprio compilador.</span><span class="sxs-lookup"><span data-stu-id="bf4de-110">However, in the second expression, `var` must be used because the result is a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="bf4de-111">Observe que no exemplo 2, a variável de iteração `foreach` `item` também deve ser implicitamente tipada.</span><span class="sxs-lookup"><span data-stu-id="bf4de-111">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/var_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="bf4de-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf4de-112">See Also</span></span>  
 [<span data-ttu-id="bf4de-113">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="bf4de-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="bf4de-114">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="bf4de-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bf4de-115">Variáveis Locais Tipadas Implicitamente</span><span class="sxs-lookup"><span data-stu-id="bf4de-115">Implicitly Typed Local Variables</span></span>](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
