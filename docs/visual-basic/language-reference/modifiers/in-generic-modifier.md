---
title: "In (modificador genérico) (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.VarianceIn
dev_langs:
- VB
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 10b2becc15b439f76feaf083dcdbf816398e6752
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="in-generic-modifier-visual-basic"></a><span data-ttu-id="6c296-102">In (modificador genérico) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6c296-102">In (Generic Modifier) (Visual Basic)</span></span>
<span data-ttu-id="6c296-103">Para parâmetros de tipo genérico, o `In` palavra-chave especifica o parâmetro de tipo é contravariante.</span><span class="sxs-lookup"><span data-stu-id="6c296-103">For generic type parameters, the `In` keyword specifies that the type parameter is contravariant.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c296-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="6c296-104">Remarks</span></span>  
 <span data-ttu-id="6c296-105">Contravariância permite que você use um tipo derivado que o especificado pelo parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="6c296-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="6c296-106">Isso permite a conversão implícita de classes que implementam interfaces variantes e conversão implícita de tipos de delegado.</span><span class="sxs-lookup"><span data-stu-id="6c296-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>  
  
 <span data-ttu-id="6c296-107">Para obter mais informações, consulte [covariância e contravariância](http://msdn.microsoft.com/library/a58cc086-276f-4f91-a366-85b7f95f38b8).</span><span class="sxs-lookup"><span data-stu-id="6c296-107">For more information, see [Covariance and Contravariance](http://msdn.microsoft.com/library/a58cc086-276f-4f91-a366-85b7f95f38b8).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="6c296-108">Regras</span><span class="sxs-lookup"><span data-stu-id="6c296-108">Rules</span></span>  
 <span data-ttu-id="6c296-109">Você pode usar o `In` palavra-chave em interfaces e delegados genéricos.</span><span class="sxs-lookup"><span data-stu-id="6c296-109">You can use the `In` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="6c296-110">Um parâmetro de tipo pode ser declarado contravariant em uma interface genérica ou delegado se ele for usado apenas como um tipo de argumentos de método e não é usado como um tipo de retorno do método.</span><span class="sxs-lookup"><span data-stu-id="6c296-110">A type parameter can be declared contravariant in a generic interface or delegate if it is used only as a type of method arguments and not used as a method return type.</span></span> <span data-ttu-id="6c296-111">`ByRef`parâmetros não podem ser covariantes ou contravariant.</span><span class="sxs-lookup"><span data-stu-id="6c296-111">`ByRef` parameters cannot be covariant or contravariant.</span></span>  
  
 <span data-ttu-id="6c296-112">Covariância e contravariância são tem suporte para tipos de referência e não tem suporte para tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="6c296-112">Covariance and contravariance are supported for reference types and not supported for value types.</span></span>  
  
 <span data-ttu-id="6c296-113">No Visual Basic, você não pode declarar os eventos em interfaces contravariant sem especificar o tipo de delegado.</span><span class="sxs-lookup"><span data-stu-id="6c296-113">In Visual Basic, you cannot declare events in contravariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="6c296-114">Além disso, contravariant interfaces não podem ter aninhados classes, enums ou estruturas, mas podem ter aninhados interfaces.</span><span class="sxs-lookup"><span data-stu-id="6c296-114">Also, contravariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="6c296-115">Comportamento</span><span class="sxs-lookup"><span data-stu-id="6c296-115">Behavior</span></span>  
 <span data-ttu-id="6c296-116">Uma interface que tem um parâmetro de tipo contravariant permite que os seus métodos aceitam argumentos de menos tipos derivados que o especificado pelo parâmetro de tipo de interface.</span><span class="sxs-lookup"><span data-stu-id="6c296-116">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="6c296-117">Por exemplo, porque no .NET Framework 4, no <xref:System.Collections.Generic.IComparer%601>interface, tipo T contravariant, você pode atribuir um objeto do `IComparer(Of Person)` um objeto do tipo o `IComparer(Of Employee)` tipo sem usar qualquer método de conversão especial se `Person` herda `Employee`.</xref:System.Collections.Generic.IComparer%601></span><span class="sxs-lookup"><span data-stu-id="6c296-117">For example, because in .NET Framework 4, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer(Of Person)` type to an object of the `IComparer(Of Employee)` type without using any special conversion methods if `Person` inherits `Employee`.</span></span>  
  
 <span data-ttu-id="6c296-118">Um delegado contravariant pode ser atribuído a outro representante do mesmo tipo, mas com um parâmetro de tipo genérico menos derivado.</span><span class="sxs-lookup"><span data-stu-id="6c296-118">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c296-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6c296-119">Example</span></span>  
 <span data-ttu-id="6c296-120">O exemplo a seguir mostra como declarar, estender e implementar uma interface genérica contravariant.</span><span class="sxs-lookup"><span data-stu-id="6c296-120">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="6c296-121">Ele também mostra como você pode usar a conversão implícita para classes que implementam esta interface.</span><span class="sxs-lookup"><span data-stu-id="6c296-121">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>  
  
 <span data-ttu-id="6c296-122">[!code-vb[vbVarianceKeywords n º&1;](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="6c296-122">[!code-vb[vbVarianceKeywords#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c296-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6c296-123">Example</span></span>  
 <span data-ttu-id="6c296-124">O exemplo a seguir mostra como declarar e instanciar e invocar um delegado genérico contravariant.</span><span class="sxs-lookup"><span data-stu-id="6c296-124">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="6c296-125">Ele também mostra como você pode converter implicitamente um tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="6c296-125">It also shows how you can implicitly convert a delegate type.</span></span>  
  
 <span data-ttu-id="6c296-126">[!code-vb[vbVarianceKeywords n º&2;](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="6c296-126">[!code-vb[vbVarianceKeywords#2](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c296-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c296-127">See Also</span></span>  
 <span data-ttu-id="6c296-128">[Variação em Interfaces genéricas](http://msdn.microsoft.com/library/e14322da-1db3-42f2-9a67-397daddd6b6a) </span><span class="sxs-lookup"><span data-stu-id="6c296-128">[Variance in Generic Interfaces](http://msdn.microsoft.com/library/e14322da-1db3-42f2-9a67-397daddd6b6a) </span></span>  
<span data-ttu-id="6c296-129"> [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)</span><span class="sxs-lookup"><span data-stu-id="6c296-129"> [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)</span></span>
