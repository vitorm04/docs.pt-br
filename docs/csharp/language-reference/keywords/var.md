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
ms.openlocfilehash: e0df25eb46bb769214412646d0ac3a7a576b3b73
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="var-c-reference"></a><span data-ttu-id="04185-102">var (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="04185-102">var (C# Reference)</span></span>
<span data-ttu-id="04185-103">Começando com o Visual C# 3.0, as variáveis que são declaradas no escopo do método podem ter um “tipo” implícito `var`.</span><span class="sxs-lookup"><span data-stu-id="04185-103">Beginning in Visual C# 3.0, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="04185-104">Uma variável local de tipo implícito é fortemente tipada, como se você mesmo tivesse declarado o tipo, mas o compilador determina o tipo.</span><span class="sxs-lookup"><span data-stu-id="04185-104">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="04185-105">As duas declarações a seguir de `i` são funcionalmente equivalentes:</span><span class="sxs-lookup"><span data-stu-id="04185-105">The following two declarations of `i` are functionally equivalent:</span></span>  
  
```  
var i = 10; // implicitly typed  
int i = 10; //explicitly typed  
```  
  
 <span data-ttu-id="04185-106">Para obter mais informações, consulte [Variáveis locais de tipo implícito](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) e [Relacionamentos de tipo em operações de consulta LINQ](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="04185-106">For more information, see [Implicitly Typed Local Variables](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) and [Type Relationships in LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="04185-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="04185-107">Example</span></span>  
 <span data-ttu-id="04185-108">O exemplo a seguir mostra duas expressões de consulta.</span><span class="sxs-lookup"><span data-stu-id="04185-108">The following example shows two query expressions.</span></span> <span data-ttu-id="04185-109">Na primeira expressão, o uso de `var` é permitido, mas não é necessário, pois o tipo do resultado da consulta pode ser declarado explicitamente como um `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="04185-109">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="04185-110">No entanto, na segunda expressão, `var` permite que o resultado seja uma coleção de tipos anônimos e o nome desse tipo não é acessível, exceto para o próprio compilador.</span><span class="sxs-lookup"><span data-stu-id="04185-110">However, in the second expression, `var` allows the result to be a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="04185-111">O uso de `var` elimina a necessidade de criar uma nova classe para o resultado.</span><span class="sxs-lookup"><span data-stu-id="04185-111">Use of `var` eliminates the requirement to create a new class for the result.</span></span> <span data-ttu-id="04185-112">Observe que no exemplo 2, a variável de iteração `foreach` `item` também deve ser implicitamente tipada.</span><span class="sxs-lookup"><span data-stu-id="04185-112">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/var_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="04185-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="04185-113">See Also</span></span>  
 [<span data-ttu-id="04185-114">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="04185-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="04185-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="04185-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="04185-116">Variáveis Locais Tipadas Implicitamente</span><span class="sxs-lookup"><span data-stu-id="04185-116">Implicitly Typed Local Variables</span></span>](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
