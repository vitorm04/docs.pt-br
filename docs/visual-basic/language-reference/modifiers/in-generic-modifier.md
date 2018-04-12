---
title: In (modificador genérico) (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 83e9aab4fc361754cfd750ae68f04b36dce13d0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="in-generic-modifier-visual-basic"></a><span data-ttu-id="48048-102">In (modificador genérico) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48048-102">In (Generic Modifier) (Visual Basic)</span></span>
<span data-ttu-id="48048-103">Para parâmetros de tipo genérico, a palavra-chave `In` especifica que o parâmetro de tipo é contravariante.</span><span class="sxs-lookup"><span data-stu-id="48048-103">For generic type parameters, the `In` keyword specifies that the type parameter is contravariant.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48048-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="48048-104">Remarks</span></span>  
 <span data-ttu-id="48048-105">A contravariância permite que você use um tipo menos derivado do que aquele especificado pelo parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="48048-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="48048-106">Isso permite a conversão implícita de classes que implementam interfaces variantes e a conversão implícita de tipos delegados.</span><span class="sxs-lookup"><span data-stu-id="48048-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>  
  
 <span data-ttu-id="48048-107">Para obter mais informações, consulte [Covariância e contravariância](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="48048-107">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="48048-108">Regras</span><span class="sxs-lookup"><span data-stu-id="48048-108">Rules</span></span>  
 <span data-ttu-id="48048-109">Você pode usar a palavra-chave `In` em delegados e interfaces genéricas.</span><span class="sxs-lookup"><span data-stu-id="48048-109">You can use the `In` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="48048-110">Um parâmetro de tipo pode ser declarado contravariant em uma interface genérica ou representante se ele é usado apenas como um tipo de argumentos de método e não é usado como um tipo de retorno do método.</span><span class="sxs-lookup"><span data-stu-id="48048-110">A type parameter can be declared contravariant in a generic interface or delegate if it is used only as a type of method arguments and not used as a method return type.</span></span> <span data-ttu-id="48048-111">`ByRef`parâmetros não podem ser covariantes ou contravariant.</span><span class="sxs-lookup"><span data-stu-id="48048-111">`ByRef` parameters cannot be covariant or contravariant.</span></span>  
  
 <span data-ttu-id="48048-112">Covariância e contravariância são com suporte para tipos de referência e não tem suporte para tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="48048-112">Covariance and contravariance are supported for reference types and not supported for value types.</span></span>  
  
 <span data-ttu-id="48048-113">No Visual Basic, você não pode declarar eventos em interfaces contravariant sem especificar o tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="48048-113">In Visual Basic, you cannot declare events in contravariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="48048-114">Além disso, contravariant interfaces não podem ter aninhados classes, enumerações ou estruturas, mas eles podem ter aninhados interfaces.</span><span class="sxs-lookup"><span data-stu-id="48048-114">Also, contravariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="48048-115">Comportamento</span><span class="sxs-lookup"><span data-stu-id="48048-115">Behavior</span></span>  
 <span data-ttu-id="48048-116">Uma interface que tem um parâmetro de tipo contravariante permite que os seus métodos aceitem argumentos de tipos menos derivados que aqueles especificados pelo parâmetro de tipo de interface.</span><span class="sxs-lookup"><span data-stu-id="48048-116">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="48048-117">Por exemplo, como no .NET Framework 4, na interface <xref:System.Collections.Generic.IComparer%601>, o tipo T é contravariante, você poderá atribuir um objeto do tipo `IComparer(Of Person)` a um objeto do tipo `IComparer(Of Employee)`, sem usar qualquer método de conversão especial se o `Person` herdar o `Employee`.</span><span class="sxs-lookup"><span data-stu-id="48048-117">For example, because in .NET Framework 4, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer(Of Person)` type to an object of the `IComparer(Of Employee)` type without using any special conversion methods if `Person` inherits `Employee`.</span></span>  
  
 <span data-ttu-id="48048-118">Um delegado contravariante pode ser atribuído a outro delegado do mesmo tipo, mas com um parâmetro de tipo genérico menos derivado.</span><span class="sxs-lookup"><span data-stu-id="48048-118">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48048-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="48048-119">Example</span></span>  
 <span data-ttu-id="48048-120">O exemplo a seguir mostra como declarar, estender e implementar uma interface genérica contravariante.</span><span class="sxs-lookup"><span data-stu-id="48048-120">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="48048-121">Ele também mostra como você pode usar a conversão implícita para classes que implementam essa interface.</span><span class="sxs-lookup"><span data-stu-id="48048-121">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>  
  
 [!code-vb[vbVarianceKeywords#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="48048-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="48048-122">Example</span></span>  
 <span data-ttu-id="48048-123">O exemplo a seguir mostra como declarar, instanciar e invocar um delegado genérico contravariante.</span><span class="sxs-lookup"><span data-stu-id="48048-123">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="48048-124">Ele também mostra como você pode converter implicitamente um tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="48048-124">It also shows how you can implicitly convert a delegate type.</span></span>  
  
 [!code-vb[vbVarianceKeywords#2](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="48048-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48048-125">See Also</span></span>  
 [<span data-ttu-id="48048-126">Variação em Interfaces Genéricas</span><span class="sxs-lookup"><span data-stu-id="48048-126">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [<span data-ttu-id="48048-127">Saída</span><span class="sxs-lookup"><span data-stu-id="48048-127">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
