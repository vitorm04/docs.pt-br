---
title: "where (restrição de tipo genérico) (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords: where (generic type constraint) [C#]
ms.assetid: d7aa871b-0714-416a-bab2-96f87ada4310
caps.latest.revision: "10"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f2b7b159689aa771d3f9d59e3b1dd340c85b1d79
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="where-generic-type-constraint-c-reference"></a><span data-ttu-id="e5a38-102">where (restrição de tipo genérico) (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="e5a38-102">where (generic type constraint) (C# Reference)</span></span>
<span data-ttu-id="e5a38-103">Em uma definição de tipo genérico, a cláusula `where` é usada para especificar as restrições nos tipos que podem ser usados como argumentos para um parâmetro de tipo definido em uma declaração genérica.</span><span class="sxs-lookup"><span data-stu-id="e5a38-103">In a generic type definition, the `where` clause is used to specify constraints on the types that can be used as arguments for a type parameter defined in a generic declaration.</span></span> <span data-ttu-id="e5a38-104">Por exemplo, você pode declarar uma classe genérica, `MyGenericClass`, de modo que o parâmetro de tipo `T` implementa a interface <xref:System.IComparable%601>:</span><span class="sxs-lookup"><span data-stu-id="e5a38-104">For example, you can declare a generic class, `MyGenericClass`, such that the type parameter `T` implements the <xref:System.IComparable%601> interface:</span></span>  
  
```csharp  
public class MyGenericClass<T> where T:IComparable { }  
```  
  
> [!NOTE]
>  <span data-ttu-id="e5a38-105">Para obter mais informações sobre a cláusula where em uma expressão de consulta, consulte [Cláusula where](../../../csharp/language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="e5a38-105">For more information on the where clause in a query expression, see [where clause](../../../csharp/language-reference/keywords/where-clause.md).</span></span>  
  
 <span data-ttu-id="e5a38-106">Além das restrições de interface, uma cláusula `where` pode incluir uma restrição de classe base, que declara que um tipo deve ter a classe especificada como uma classe base (ou ser essa classe em si) para ser usada como um argumento de tipo para o tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="e5a38-106">In addition to interface constraints, a `where` clause can include a base class constraint, which states that a type must have the specified class as a base class (or be that class itself) in order to be used as a type argument for that generic type.</span></span> <span data-ttu-id="e5a38-107">Se tal restrição for usada, ela deverá aparecer antes de qualquer outra restrição nesse parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="e5a38-107">If such a constraint is used, it must appear before any other constraints on that type parameter.</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_1.cs)]  
  
 <span data-ttu-id="e5a38-108">A cláusula `where` também pode incluir uma restrição de construtor.</span><span class="sxs-lookup"><span data-stu-id="e5a38-108">The `where` clause may also include a constructor constraint.</span></span> <span data-ttu-id="e5a38-109">É possível criar uma instância de um parâmetro de tipo usando o operador new, no entanto, para fazer isso o parâmetro de tipo deve ser restrito pela restrição de construtor, `new()`.</span><span class="sxs-lookup"><span data-stu-id="e5a38-109">It is possible to create an instance of a type parameter using the new operator; however, in order to do so the type parameter must be constrained by the constructor constraint, `new()`.</span></span> <span data-ttu-id="e5a38-110">A [restrição new()](../../../csharp/language-reference/keywords/new-constraint.md) informa o compilador que qualquer argumento de tipo fornecido deve ter um construtor – ou padrão – sem parâmetros acessível.</span><span class="sxs-lookup"><span data-stu-id="e5a38-110">The [new() Constraint](../../../csharp/language-reference/keywords/new-constraint.md) lets the compiler know that any type argument supplied must have an accessible parameterless--or default-- constructor.</span></span> <span data-ttu-id="e5a38-111">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e5a38-111">For example:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_2.cs)]  
  
 <span data-ttu-id="e5a38-112">A restrição `new()` aparece por último na cláusula `where`.</span><span class="sxs-lookup"><span data-stu-id="e5a38-112">The `new()` constraint appears last in the `where` clause.</span></span>  
  
 <span data-ttu-id="e5a38-113">Com vários parâmetros de tipo, use uma cláusula `where` para cada parâmetro de tipo, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e5a38-113">With multiple type parameters, use one `where` clause for each type parameter, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_3.cs)]  
  
 <span data-ttu-id="e5a38-114">Você também pode anexar restrições aos parâmetros de tipo de métodos genéricos, como esse:</span><span class="sxs-lookup"><span data-stu-id="e5a38-114">You can also attach constraints to type parameters of generic methods, like this:</span></span>  
  
```csharp  
public bool MyMethod<T>(T t) where T : IMyInterface { }  
```  
  
 <span data-ttu-id="e5a38-115">Observe que a sintaxe para descrever as restrições de parâmetro de tipo em delegados é a mesma que a dos métodos:</span><span class="sxs-lookup"><span data-stu-id="e5a38-115">Notice that the syntax to describe type parameter constraints on delegates is the same as that of methods:</span></span>  
  
```csharp  
delegate T MyDelegate<T>() where T : new()  
```  
  
 <span data-ttu-id="e5a38-116">Para obter informações sobre delegados genéricos, consulte [Delegados genéricos](../../../csharp/programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="e5a38-116">For information on generic delegates, see [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>  
  
 <span data-ttu-id="e5a38-117">Para obter detalhes sobre a sintaxe e o uso de restrições, consulte [Restrições a parâmetros de tipo](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e5a38-117">For details on the syntax and use of constraints, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="e5a38-118">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="e5a38-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e5a38-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5a38-119">See Also</span></span>  
 [<span data-ttu-id="e5a38-120">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="e5a38-120">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e5a38-121">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="e5a38-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e5a38-122">Introdução aos genéricos</span><span class="sxs-lookup"><span data-stu-id="e5a38-122">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [<span data-ttu-id="e5a38-123">Restrição new</span><span class="sxs-lookup"><span data-stu-id="e5a38-123">new Constraint</span></span>](../../../csharp/language-reference/keywords/new-constraint.md)  
 [<span data-ttu-id="e5a38-124">Restrições a parâmetros de tipo</span><span class="sxs-lookup"><span data-stu-id="e5a38-124">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
