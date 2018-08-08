---
title: in (modificador genérico) (Referência de C#)
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: 003ce26fe9ba315eefc748a406754026231004b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33266998"
---
# <a name="in-generic-modifier-c-reference"></a><span data-ttu-id="bbb73-102">in (modificador genérico) (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="bbb73-102">in (Generic Modifier) (C# Reference)</span></span>

<span data-ttu-id="bbb73-103">Para parâmetros de tipo genérico, a palavra-chave `in` especifica que o parâmetro de tipo é contravariante.</span><span class="sxs-lookup"><span data-stu-id="bbb73-103">For generic type parameters, the `in` keyword specifies that the type parameter is contravariant.</span></span> <span data-ttu-id="bbb73-104">Você pode usar a palavra-chave `in` em delegados e interfaces genéricas.</span><span class="sxs-lookup"><span data-stu-id="bbb73-104">You can use the `in` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="bbb73-105">A contravariância permite que você use um tipo menos derivado do que aquele especificado pelo parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="bbb73-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="bbb73-106">Isso permite a conversão implícita de classes que implementam interfaces variantes e a conversão implícita de tipos delegados.</span><span class="sxs-lookup"><span data-stu-id="bbb73-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="bbb73-107">A covariância e a contravariância em parâmetros de tipo genérico têm suporte para tipos de referência, mas não para tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="bbb73-107">Covariance and contravariance in generic type parameters are supported for reference types, but they are not supported for value types.</span></span>  
  
 <span data-ttu-id="bbb73-108">Um tipo pode ser declarado como contravariante em uma interface genérica ou como delegado somente se ele define o tipo de parâmetros de um método e não o tipo de retorno de um método.</span><span class="sxs-lookup"><span data-stu-id="bbb73-108">A type can be declared contravariant in a generic interface or delegate only if it defines the type of a method's parameters and not of a method's return type.</span></span> <span data-ttu-id="bbb73-109">Os parâmetros `In`, `ref` e `out` precisam ser invariáveis, ou seja, nem covariantes nem contravariantes.</span><span class="sxs-lookup"><span data-stu-id="bbb73-109">`In`, `ref`, and `out` parameters must be invariant, meaning they are neither covariant or contravariant.</span></span>
  
 <span data-ttu-id="bbb73-110">Uma interface que tem um parâmetro de tipo contravariante permite que os seus métodos aceitem argumentos de tipos menos derivados que aqueles especificados pelo parâmetro de tipo de interface.</span><span class="sxs-lookup"><span data-stu-id="bbb73-110">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="bbb73-111">Por exemplo, na interface <xref:System.Collections.Generic.IComparer%601>, o tipo T é contravariante e você pode atribuir um objeto do tipo `IComparer<Person>` a um objeto do tipo `IComparer<Employee>`, sem usar nenhum método de conversão especial caso `Employee` herde `Person`.</span><span class="sxs-lookup"><span data-stu-id="bbb73-111">For example, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer<Person>` type to an object of the `IComparer<Employee>` type without using any special conversion methods if `Employee` inherits `Person`.</span></span>  
  
 <span data-ttu-id="bbb73-112">Um delegado contravariante pode ser atribuído a outro delegado do mesmo tipo, mas com um parâmetro de tipo genérico menos derivado.</span><span class="sxs-lookup"><span data-stu-id="bbb73-112">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>  
  
 <span data-ttu-id="bbb73-113">Para obter mais informações, consulte [Covariância e contravariância](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="bbb73-113">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="contravariant-generic-interface"></a><span data-ttu-id="bbb73-114">Interface genérica contravariante</span><span class="sxs-lookup"><span data-stu-id="bbb73-114">Contravariant generic interface</span></span>   

 <span data-ttu-id="bbb73-115">O exemplo a seguir mostra como declarar, estender e implementar uma interface genérica contravariante.</span><span class="sxs-lookup"><span data-stu-id="bbb73-115">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="bbb73-116">Ele também mostra como você pode usar a conversão implícita para classes que implementam essa interface.</span><span class="sxs-lookup"><span data-stu-id="bbb73-116">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>  
  
 [!code-csharp[csVarianceKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_1.cs)]  
  
## <a name="contravariant-generic-delegate"></a><span data-ttu-id="bbb73-117">Delegado genérico contravariante</span><span class="sxs-lookup"><span data-stu-id="bbb73-117">Contravariant generic delegate</span></span>  

 <span data-ttu-id="bbb73-118">O exemplo a seguir mostra como declarar, instanciar e invocar um delegado genérico contravariante.</span><span class="sxs-lookup"><span data-stu-id="bbb73-118">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="bbb73-119">Ele também mostra como você pode converter implicitamente um tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="bbb73-119">It also shows how you can implicitly convert a delegate type.</span></span>  
  
 [!code-csharp[csVarianceKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="bbb73-120">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="bbb73-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bbb73-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bbb73-121">See Also</span></span>  
 [<span data-ttu-id="bbb73-122">out</span><span class="sxs-lookup"><span data-stu-id="bbb73-122">out</span></span>](../../../csharp/language-reference/keywords/out-generic-modifier.md)  
 [<span data-ttu-id="bbb73-123">Covariância e Contravariância</span><span class="sxs-lookup"><span data-stu-id="bbb73-123">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [<span data-ttu-id="bbb73-124">Modificadores</span><span class="sxs-lookup"><span data-stu-id="bbb73-124">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
