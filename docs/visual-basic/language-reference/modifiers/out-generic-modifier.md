---
title: Out (modificador genérico) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceOut
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
ms.openlocfilehash: 7ba774bfcd629a7518602d4b971e86a690b2dd83
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598147"
---
# <a name="out-generic-modifier-visual-basic"></a><span data-ttu-id="6cc2e-102">Out (modificador genérico) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6cc2e-102">Out (Generic Modifier) (Visual Basic)</span></span>
<span data-ttu-id="6cc2e-103">Para parâmetros de tipo genérico, o `Out` palavra-chave especifica que o tipo é covariante.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-103">For generic type parameters, the `Out` keyword specifies that the type is covariant.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6cc2e-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="6cc2e-104">Remarks</span></span>  
 <span data-ttu-id="6cc2e-105">A covariância permite que você use um tipo mais derivado do que aquele especificado pelo parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-105">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="6cc2e-106">Isso permite a conversão implícita de classes que implementam interfaces variantes e a conversão implícita de tipos delegados.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>  
  
 <span data-ttu-id="6cc2e-107">Para obter mais informações, consulte [Covariância e contravariância](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="6cc2e-107">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="6cc2e-108">Regras</span><span class="sxs-lookup"><span data-stu-id="6cc2e-108">Rules</span></span>  
 <span data-ttu-id="6cc2e-109">Você pode usar a palavra-chave `Out` em delegados e interfaces genéricas.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-109">You can use the `Out` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="6cc2e-110">Em uma interface genérica, um parâmetro de tipo pode ser declarado covariante se ele satisfizer as condições a seguir:</span><span class="sxs-lookup"><span data-stu-id="6cc2e-110">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>  
  
-   <span data-ttu-id="6cc2e-111">O parâmetro de tipo é usado apenas como um tipo de retorno dos métodos de interface e não é usado como um tipo de argumentos de método.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-111">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6cc2e-112">Há uma exceção a essa regra.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-112">There is one exception to this rule.</span></span> <span data-ttu-id="6cc2e-113">Se, em uma interface covariante, você tiver um delegado genérico contravariante como um parâmetro de método, você poderá usar o tipo covariante como um parâmetro de tipo genérico para o delegado.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-113">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="6cc2e-114">Para obter mais informações sobre delegados genéricos covariantes e contravariantes, consulte [Variância em delegados](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) e [Usando variância para delegados genéricos Func e Action](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="6cc2e-114">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
-   <span data-ttu-id="6cc2e-115">O parâmetro de tipo não é usado como uma restrição genérica para os métodos de interface.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-115">The type parameter is not used as a generic constraint for the interface methods.</span></span>  
  
 <span data-ttu-id="6cc2e-116">Em um delegate genérico, um parâmetro de tipo pode ser declarado covariante se ele é usado apenas como um tipo de retorno do método e não usado para argumentos de método.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-116">In a generic delegate, a type parameter can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>  
  
 <span data-ttu-id="6cc2e-117">A covariância e a contravariância têm suporte para tipos de referência, mas não para tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-117">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>  
  
 <span data-ttu-id="6cc2e-118">No Visual Basic, você não pode declarar eventos em interfaces covariantes sem especificar o tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-118">In Visual Basic, you cannot declare events in covariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="6cc2e-119">Além disso, covariantes interfaces não podem ter aninhados classes, enumerações ou estruturas, mas podem ter aninhados interfaces.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-119">Also, covariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="6cc2e-120">Comportamento</span><span class="sxs-lookup"><span data-stu-id="6cc2e-120">Behavior</span></span>  
 <span data-ttu-id="6cc2e-121">Uma interface que tem um parâmetro de tipo covariante permite que seus métodos retornem tipos mais derivados do que aqueles especificados pelo parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-121">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="6cc2e-122">Por exemplo, já que no .NET Framework 4, em <xref:System.Collections.Generic.IEnumerable%601>, o tipo T é covariante, você pode atribuir um objeto do tipo `IEnumerabe(Of String)` a um objeto do tipo `IEnumerable(Of Object)` sem usar nenhum método de conversão especial.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-122">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerabe(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>  
  
 <span data-ttu-id="6cc2e-123">Pode ser atribuído a um delegado covariante outro delegado do mesmo tipo, mas com um parâmetro de tipo genérico mais derivado.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-123">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6cc2e-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6cc2e-124">Example</span></span>  
 <span data-ttu-id="6cc2e-125">O exemplo a seguir mostra como declarar, estender e implementar uma interface genérica covariante.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-125">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="6cc2e-126">Ele também mostra como usar a conversão implícita para classes que implementam uma interface covariante.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-126">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>  
  
 [!code-vb[vbVarianceKeywords#3](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="6cc2e-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6cc2e-127">Example</span></span>  
 <span data-ttu-id="6cc2e-128">O exemplo a seguir mostra como declarar, instanciar e invocar um delegado genérico covariante.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-128">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="6cc2e-129">Ele também mostra como você pode usar a conversão implícita de tipos delegados.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-129">It also shows how you can use implicit conversion for delegate types.</span></span>  
  
 [!code-vb[vbVarianceKeywords#4](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6cc2e-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6cc2e-130">See Also</span></span>  
 [<span data-ttu-id="6cc2e-131">Variação em Interfaces Genéricas</span><span class="sxs-lookup"><span data-stu-id="6cc2e-131">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [<span data-ttu-id="6cc2e-132">In</span><span class="sxs-lookup"><span data-stu-id="6cc2e-132">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
