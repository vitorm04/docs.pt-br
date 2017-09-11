---
title: "Out (modificador genérico) (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.VarianceOut
dev_langs:
- VB
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
caps.latest.revision: 14
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
ms.openlocfilehash: 9fcec74c8708331441b28c4f119a2cd5b6343ca0
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="out-generic-modifier-visual-basic"></a><span data-ttu-id="afbb4-102">Out (modificador genérico) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afbb4-102">Out (Generic Modifier) (Visual Basic)</span></span>
<span data-ttu-id="afbb4-103">Para parâmetros de tipo genérico, o `Out` palavra-chave especifica que o tipo é covariante.</span><span class="sxs-lookup"><span data-stu-id="afbb4-103">For generic type parameters, the `Out` keyword specifies that the type is covariant.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="afbb4-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="afbb4-104">Remarks</span></span>  
 <span data-ttu-id="afbb4-105">Covariância permite que você use um tipo mais derivado que o especificado pelo parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="afbb4-105">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="afbb4-106">Isso permite a conversão implícita de classes que implementam interfaces variantes e conversão implícita de tipos de delegado.</span><span class="sxs-lookup"><span data-stu-id="afbb4-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>  
  
 <span data-ttu-id="afbb4-107">Para obter mais informações, consulte [covariância e contravariância](http://msdn.microsoft.com/library/a58cc086-276f-4f91-a366-85b7f95f38b8).</span><span class="sxs-lookup"><span data-stu-id="afbb4-107">For more information, see [Covariance and Contravariance](http://msdn.microsoft.com/library/a58cc086-276f-4f91-a366-85b7f95f38b8).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="afbb4-108">Regras</span><span class="sxs-lookup"><span data-stu-id="afbb4-108">Rules</span></span>  
 <span data-ttu-id="afbb4-109">Você pode usar o `Out` palavra-chave em interfaces e delegados genéricos.</span><span class="sxs-lookup"><span data-stu-id="afbb4-109">You can use the `Out` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="afbb4-110">Em uma interface genérica, um parâmetro de tipo pode ser declarado covariante se ele satisfaz as condições a seguir:</span><span class="sxs-lookup"><span data-stu-id="afbb4-110">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>  
  
-   <span data-ttu-id="afbb4-111">O parâmetro de tipo é usado apenas como um tipo de retorno dos métodos de interface e não é usado como um tipo de argumentos do método.</span><span class="sxs-lookup"><span data-stu-id="afbb4-111">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="afbb4-112">Há uma exceção a essa regra.</span><span class="sxs-lookup"><span data-stu-id="afbb4-112">There is one exception to this rule.</span></span> <span data-ttu-id="afbb4-113">Se tiver um delegado genérico contravariant como um parâmetro de método em uma interface covariante, você pode usar o tipo covariante como um parâmetro de tipo genérico para este delegado.</span><span class="sxs-lookup"><span data-stu-id="afbb4-113">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="afbb4-114">Para obter mais informações sobre covariant e contravariant delegados genéricos, consulte [variação em delegações](http://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca) e [usando variação para ação delegações genéricas Func e](http://msdn.microsoft.com/library/e69c4f39-09aa-4c6d-a752-08cc767d8290).</span><span class="sxs-lookup"><span data-stu-id="afbb4-114">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](http://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca) and [Using Variance for Func and Action Generic Delegates](http://msdn.microsoft.com/library/e69c4f39-09aa-4c6d-a752-08cc767d8290).</span></span>  
  
-   <span data-ttu-id="afbb4-115">O parâmetro de tipo não é usado como uma restrição genérica para os métodos de interface.</span><span class="sxs-lookup"><span data-stu-id="afbb4-115">The type parameter is not used as a generic constraint for the interface methods.</span></span>  
  
 <span data-ttu-id="afbb4-116">Um delegado genérico, um parâmetro de tipo pode ser declarado covariante se ele for usado apenas como um tipo de retorno do método e não usado para argumentos de método.</span><span class="sxs-lookup"><span data-stu-id="afbb4-116">In a generic delegate, a type parameter can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>  
  
 <span data-ttu-id="afbb4-117">Covariância e contravariância têm suporte para tipos de referência, mas eles não têm suporte para tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="afbb4-117">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>  
  
 <span data-ttu-id="afbb4-118">No Visual Basic, você não pode declarar os eventos em interfaces covariantes sem especificar o tipo de delegado.</span><span class="sxs-lookup"><span data-stu-id="afbb4-118">In Visual Basic, you cannot declare events in covariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="afbb4-119">Também não podem ter aninhados interfaces covariantes classes, enums ou estruturas, mas podem ter aninhados interfaces.</span><span class="sxs-lookup"><span data-stu-id="afbb4-119">Also, covariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="afbb4-120">Comportamento</span><span class="sxs-lookup"><span data-stu-id="afbb4-120">Behavior</span></span>  
 <span data-ttu-id="afbb4-121">Uma interface que tem um parâmetro de tipo covariant permite que seus métodos retornar mais tipos derivados que o especificado pelo parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="afbb4-121">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="afbb4-122">Por exemplo, porque no .NET Framework 4, em <xref:System.Collections.Generic.IEnumerable%601>, T tipo é covariante, você pode atribuir um objeto do `IEnumerabe(Of String)` tipo para um objeto do `IEnumerable(Of Object)` tipo sem usar qualquer método de conversão especial.</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="afbb4-122">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerabe(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>  
  
 <span data-ttu-id="afbb4-123">Um delegado de covariante pode ser atribuído a outro representante do mesmo tipo, mas com um parâmetro de tipo genérico mais derivado.</span><span class="sxs-lookup"><span data-stu-id="afbb4-123">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afbb4-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="afbb4-124">Example</span></span>  
 <span data-ttu-id="afbb4-125">O exemplo a seguir mostra como declarar, estender e implementar uma interface genérica covariante.</span><span class="sxs-lookup"><span data-stu-id="afbb4-125">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="afbb4-126">Ele também mostra como usar a conversão implícita para classes que implementam uma interface covariante.</span><span class="sxs-lookup"><span data-stu-id="afbb4-126">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>  
  
 <span data-ttu-id="afbb4-127">[!code-vb[vbVarianceKeywords n º&3;](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="afbb4-127">[!code-vb[vbVarianceKeywords#3](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="afbb4-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="afbb4-128">Example</span></span>  
 <span data-ttu-id="afbb4-129">O exemplo a seguir mostra como declarar e instanciar e invocar um delegado genérico covariante.</span><span class="sxs-lookup"><span data-stu-id="afbb4-129">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="afbb4-130">Ele também mostra como você pode usar a conversão implícita de tipos delegados.</span><span class="sxs-lookup"><span data-stu-id="afbb4-130">It also shows how you can use implicit conversion for delegate types.</span></span>  
  
 <span data-ttu-id="afbb4-131">[!code-vb[vbVarianceKeywords n º&4;](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="afbb4-131">[!code-vb[vbVarianceKeywords#4](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afbb4-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="afbb4-132">See Also</span></span>  
 <span data-ttu-id="afbb4-133">[Variação em Interfaces genéricas](http://msdn.microsoft.com/library/e14322da-1db3-42f2-9a67-397daddd6b6a) </span><span class="sxs-lookup"><span data-stu-id="afbb4-133">[Variance in Generic Interfaces](http://msdn.microsoft.com/library/e14322da-1db3-42f2-9a67-397daddd6b6a) </span></span>  
<span data-ttu-id="afbb4-134"> [Em](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)</span><span class="sxs-lookup"><span data-stu-id="afbb4-134"> [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)</span></span>
