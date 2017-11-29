---
title: "in (modificador genérico) (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.assetid: 3a778c36-8aed-4ebe-aa8b-39f4057215b1
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 84773fca826b5a25679f1385a11c51b590ea20f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="in-generic-modifier-c-reference"></a><span data-ttu-id="8ec98-102">in (modificador genérico) (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="8ec98-102">in (Generic Modifier) (C# Reference)</span></span>
<span data-ttu-id="8ec98-103">Para parâmetros de tipo genérico, a palavra-chave `in` especifica que o parâmetro de tipo é contravariante.</span><span class="sxs-lookup"><span data-stu-id="8ec98-103">For generic type parameters, the `in` keyword specifies that the type parameter is contravariant.</span></span> <span data-ttu-id="8ec98-104">Você pode usar a palavra-chave `in` em delegados e interfaces genéricas.</span><span class="sxs-lookup"><span data-stu-id="8ec98-104">You can use the `in` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="8ec98-105">A contravariância permite que você use um tipo menos derivado do que aquele especificado pelo parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="8ec98-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="8ec98-106">Isso permite a conversão implícita de classes que implementam interfaces variantes e a conversão implícita de tipos delegados.</span><span class="sxs-lookup"><span data-stu-id="8ec98-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="8ec98-107">A covariância e a contravariância em parâmetros de tipo genérico têm suporte para tipos de referência, mas não para tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="8ec98-107">Covariance and contravariance in generic type parameters are supported for reference types, but they are not supported for value types.</span></span>  
  
 <span data-ttu-id="8ec98-108">Um tipo pode ser declarado contravariante em uma interface genérica ou delegado se ele for usado apenas como um tipo de argumentos de método e não como um tipo de retorno do método.</span><span class="sxs-lookup"><span data-stu-id="8ec98-108">A type can be declared contravariant in a generic interface or delegate if it is used only as a type of method arguments and not used as a method return type.</span></span> <span data-ttu-id="8ec98-109">Os parâmetros `Ref` e `out` não podem ser variantes.</span><span class="sxs-lookup"><span data-stu-id="8ec98-109">`Ref` and `out` parameters cannot be variant.</span></span>  
  
 <span data-ttu-id="8ec98-110">Uma interface que tem um parâmetro de tipo contravariante permite que os seus métodos aceitem argumentos de tipos menos derivados que aqueles especificados pelo parâmetro de tipo de interface.</span><span class="sxs-lookup"><span data-stu-id="8ec98-110">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="8ec98-111">Por exemplo, como no .NET Framework 4, na interface <xref:System.Collections.Generic.IComparer%601>, o tipo T é contravariante, você poderá atribuir um objeto do tipo `IComparer(Of Person)` a um objeto do tipo `IComparer(Of Employee)`, sem usar qualquer método de conversão especial se o `Employee` herdar o `Person`.</span><span class="sxs-lookup"><span data-stu-id="8ec98-111">For example, because in .NET Framework 4, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer(Of Person)` type to an object of the `IComparer(Of Employee)` type without using any special conversion methods if `Employee` inherits `Person`.</span></span>  
  
 <span data-ttu-id="8ec98-112">Um delegado contravariante pode ser atribuído a outro delegado do mesmo tipo, mas com um parâmetro de tipo genérico menos derivado.</span><span class="sxs-lookup"><span data-stu-id="8ec98-112">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>  
  
 <span data-ttu-id="8ec98-113">Para obter mais informações, consulte [Covariância e contravariância](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="8ec98-113">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ec98-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8ec98-114">Example</span></span>  
 <span data-ttu-id="8ec98-115">O exemplo a seguir mostra como declarar, estender e implementar uma interface genérica contravariante.</span><span class="sxs-lookup"><span data-stu-id="8ec98-115">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="8ec98-116">Ele também mostra como você pode usar a conversão implícita para classes que implementam essa interface.</span><span class="sxs-lookup"><span data-stu-id="8ec98-116">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>  
  
 [!code-csharp[csVarianceKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="8ec98-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8ec98-117">Example</span></span>  
 <span data-ttu-id="8ec98-118">O exemplo a seguir mostra como declarar, instanciar e invocar um delegado genérico contravariante.</span><span class="sxs-lookup"><span data-stu-id="8ec98-118">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="8ec98-119">Ele também mostra como você pode converter implicitamente um tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="8ec98-119">It also shows how you can implicitly convert a delegate type.</span></span>  
  
 [!code-csharp[csVarianceKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="8ec98-120">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="8ec98-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8ec98-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ec98-121">See Also</span></span>  
 [<span data-ttu-id="8ec98-122">out</span><span class="sxs-lookup"><span data-stu-id="8ec98-122">out</span></span>](../../../csharp/language-reference/keywords/out-generic-modifier.md)  
 [<span data-ttu-id="8ec98-123">Covariância e Contravariância</span><span class="sxs-lookup"><span data-stu-id="8ec98-123">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [<span data-ttu-id="8ec98-124">Modificadores</span><span class="sxs-lookup"><span data-stu-id="8ec98-124">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
