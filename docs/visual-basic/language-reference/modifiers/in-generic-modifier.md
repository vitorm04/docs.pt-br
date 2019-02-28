---
title: In (modificador genérico) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
ms.openlocfilehash: 91a0b9c1188820f8fc466ce1bb123b704fcd94b7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972502"
---
# <a name="in-generic-modifier-visual-basic"></a><span data-ttu-id="dc1fe-102">In (modificador genérico) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc1fe-102">In (Generic Modifier) (Visual Basic)</span></span>
<span data-ttu-id="dc1fe-103">Para parâmetros de tipo genérico, a palavra-chave `In` especifica que o parâmetro de tipo é contravariante.</span><span class="sxs-lookup"><span data-stu-id="dc1fe-103">For generic type parameters, the `In` keyword specifies that the type parameter is contravariant.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc1fe-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="dc1fe-104">Remarks</span></span>  
 <span data-ttu-id="dc1fe-105">A contravariância permite que você use um tipo menos derivado do que aquele especificado pelo parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="dc1fe-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="dc1fe-106">Isso permite a conversão implícita de classes que implementam interfaces variantes e a conversão implícita de tipos delegados.</span><span class="sxs-lookup"><span data-stu-id="dc1fe-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>  
  
 <span data-ttu-id="dc1fe-107">Para obter mais informações, consulte [Covariância e contravariância](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="dc1fe-107">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="dc1fe-108">Regras</span><span class="sxs-lookup"><span data-stu-id="dc1fe-108">Rules</span></span>  
 <span data-ttu-id="dc1fe-109">Você pode usar a palavra-chave `In` em delegados e interfaces genéricas.</span><span class="sxs-lookup"><span data-stu-id="dc1fe-109">You can use the `In` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="dc1fe-110">Um parâmetro de tipo pode ser declarado contravariante em uma interface genérica ou delegado se ele é usado apenas como um tipo de argumentos de método e não é usado como um tipo de retorno do método.</span><span class="sxs-lookup"><span data-stu-id="dc1fe-110">A type parameter can be declared contravariant in a generic interface or delegate if it is used only as a type of method arguments and not used as a method return type.</span></span> <span data-ttu-id="dc1fe-111">`ByRef` parâmetros não podem ser covariantes ou contravariantes.</span><span class="sxs-lookup"><span data-stu-id="dc1fe-111">`ByRef` parameters cannot be covariant or contravariant.</span></span>  
  
 <span data-ttu-id="dc1fe-112">Covariância e contravariância são tem suporte para tipos de referência e não tem suporte para tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="dc1fe-112">Covariance and contravariance are supported for reference types and not supported for value types.</span></span>  
  
 <span data-ttu-id="dc1fe-113">No Visual Basic, você não pode declarar eventos em interfaces de contravariante sem especificar o tipo de delegado.</span><span class="sxs-lookup"><span data-stu-id="dc1fe-113">In Visual Basic, you cannot declare events in contravariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="dc1fe-114">Além disso, contravariant interfaces não podem ter aninhados, classes, enumerações ou estruturas, mas eles podem ter interfaces aninhados.</span><span class="sxs-lookup"><span data-stu-id="dc1fe-114">Also, contravariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="dc1fe-115">Comportamento</span><span class="sxs-lookup"><span data-stu-id="dc1fe-115">Behavior</span></span>  
 <span data-ttu-id="dc1fe-116">Uma interface que tem um parâmetro de tipo contravariante permite que os seus métodos aceitem argumentos de tipos menos derivados que aqueles especificados pelo parâmetro de tipo de interface.</span><span class="sxs-lookup"><span data-stu-id="dc1fe-116">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="dc1fe-117">Por exemplo, como no .NET Framework 4, na interface <xref:System.Collections.Generic.IComparer%601>, o tipo T é contravariante, você poderá atribuir um objeto do tipo `IComparer(Of Person)` a um objeto do tipo `IComparer(Of Employee)`, sem usar qualquer método de conversão especial se o `Person` herdar o `Employee`.</span><span class="sxs-lookup"><span data-stu-id="dc1fe-117">For example, because in .NET Framework 4, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer(Of Person)` type to an object of the `IComparer(Of Employee)` type without using any special conversion methods if `Person` inherits `Employee`.</span></span>  
  
 <span data-ttu-id="dc1fe-118">Um delegado contravariante pode ser atribuído a outro delegado do mesmo tipo, mas com um parâmetro de tipo genérico menos derivado.</span><span class="sxs-lookup"><span data-stu-id="dc1fe-118">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc1fe-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dc1fe-119">Example</span></span>  
 <span data-ttu-id="dc1fe-120">O exemplo a seguir mostra como declarar, estender e implementar uma interface genérica contravariante.</span><span class="sxs-lookup"><span data-stu-id="dc1fe-120">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="dc1fe-121">Ele também mostra como você pode usar a conversão implícita para classes que implementam essa interface.</span><span class="sxs-lookup"><span data-stu-id="dc1fe-121">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>  
  
 [!code-vb[vbVarianceKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="dc1fe-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dc1fe-122">Example</span></span>  
 <span data-ttu-id="dc1fe-123">O exemplo a seguir mostra como declarar, instanciar e invocar um delegado genérico contravariante.</span><span class="sxs-lookup"><span data-stu-id="dc1fe-123">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="dc1fe-124">Ele também mostra como você pode converter implicitamente um tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="dc1fe-124">It also shows how you can implicitly convert a delegate type.</span></span>  
  
 [!code-vb[vbVarianceKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="dc1fe-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc1fe-125">See also</span></span>
- [<span data-ttu-id="dc1fe-126">Variação em Interfaces Genéricas</span><span class="sxs-lookup"><span data-stu-id="dc1fe-126">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="dc1fe-127">Saída</span><span class="sxs-lookup"><span data-stu-id="dc1fe-127">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
