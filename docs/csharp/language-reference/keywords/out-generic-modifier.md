---
title: "out (modificador genérico) (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 25019408387bbf085475482c74a3fc6001321b24
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="out-generic-modifier-c-reference"></a><span data-ttu-id="426b4-102">out (modificador genérico) (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="426b4-102">out (Generic Modifier) (C# Reference)</span></span>
<span data-ttu-id="426b4-103">Para parâmetros de tipo genérico, a palavra-chave `out` especifica que o parâmetro de tipo é covariante.</span><span class="sxs-lookup"><span data-stu-id="426b4-103">For generic type parameters, the `out` keyword specifies that the type parameter is covariant.</span></span> <span data-ttu-id="426b4-104">Você pode usar a palavra-chave `out` em delegados e interfaces genéricas.</span><span class="sxs-lookup"><span data-stu-id="426b4-104">You can use the `out` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="426b4-105">A covariância permite que você use um tipo mais derivado do que aquele especificado pelo parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="426b4-105">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="426b4-106">Isso permite a conversão implícita de classes que implementam interfaces variantes e a conversão implícita de tipos delegados.</span><span class="sxs-lookup"><span data-stu-id="426b4-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="426b4-107">A covariância e a contravariância têm suporte para tipos de referência, mas não para tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="426b4-107">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>  
  
 <span data-ttu-id="426b4-108">Uma interface que tem um parâmetro de tipo covariante permite que seus métodos retornem tipos mais derivados do que aqueles especificados pelo parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="426b4-108">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="426b4-109">Por exemplo, já que no .NET Framework 4, em <xref:System.Collections.Generic.IEnumerable%601>, o tipo T é covariante, você pode atribuir um objeto do tipo `IEnumerable(Of String)` a um objeto do tipo `IEnumerable(Of Object)` sem usar nenhum método de conversão especial.</span><span class="sxs-lookup"><span data-stu-id="426b4-109">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerable(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>  
  
 <span data-ttu-id="426b4-110">Pode ser atribuído a um delegado covariante outro delegado do mesmo tipo, mas com um parâmetro de tipo genérico mais derivado.</span><span class="sxs-lookup"><span data-stu-id="426b4-110">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>  
  
 <span data-ttu-id="426b4-111">Para obter mais informações, consulte [Covariância e contravariância](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="426b4-111">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="426b4-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="426b4-112">Example</span></span>  
 <span data-ttu-id="426b4-113">O exemplo a seguir mostra como declarar, estender e implementar uma interface genérica covariante.</span><span class="sxs-lookup"><span data-stu-id="426b4-113">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="426b4-114">Ele também mostra como usar a conversão implícita para classes que implementam uma interface covariante.</span><span class="sxs-lookup"><span data-stu-id="426b4-114">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>  
  
 [!code-csharp[csVarianceKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_1.cs)]  
  
 <span data-ttu-id="426b4-115">Em uma interface genérica, um parâmetro de tipo pode ser declarado covariante se ele satisfizer as condições a seguir:</span><span class="sxs-lookup"><span data-stu-id="426b4-115">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>  
  
-   <span data-ttu-id="426b4-116">O parâmetro de tipo é usado apenas como um tipo de retorno dos métodos de interface e não é usado como um tipo de argumentos de método.</span><span class="sxs-lookup"><span data-stu-id="426b4-116">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="426b4-117">Há uma exceção a essa regra.</span><span class="sxs-lookup"><span data-stu-id="426b4-117">There is one exception to this rule.</span></span> <span data-ttu-id="426b4-118">Se, em uma interface covariante, você tiver um delegado genérico contravariante como um parâmetro de método, você poderá usar o tipo covariante como um parâmetro de tipo genérico para o delegado.</span><span class="sxs-lookup"><span data-stu-id="426b4-118">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="426b4-119">Para obter mais informações sobre delegados genéricos covariantes e contravariantes, consulte [Variância em delegados](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) e [Usando variância para delegados genéricos Func e Action](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="426b4-119">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
-   <span data-ttu-id="426b4-120">O parâmetro de tipo não é usado como uma restrição genérica para os métodos de interface.</span><span class="sxs-lookup"><span data-stu-id="426b4-120">The type parameter is not used as a generic constraint for the interface methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="426b4-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="426b4-121">Example</span></span>  
 <span data-ttu-id="426b4-122">O exemplo a seguir mostra como declarar, instanciar e invocar um delegado genérico covariante.</span><span class="sxs-lookup"><span data-stu-id="426b4-122">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="426b4-123">Ele também mostra como converter implicitamente os tipos delegados.</span><span class="sxs-lookup"><span data-stu-id="426b4-123">It also shows how to implicitly convert delegate types.</span></span>  
  
 [!code-csharp[csVarianceKeywords#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_2.cs)]  
  
 <span data-ttu-id="426b4-124">Um delegado genérico, um tipo pode ser declarado covariante se for usado apenas como um tipo de retorno do método e não usado para argumentos de método.</span><span class="sxs-lookup"><span data-stu-id="426b4-124">In a generic delegate, a type can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="426b4-125">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="426b4-125">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="426b4-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="426b4-126">See Also</span></span>  
 [<span data-ttu-id="426b4-127">Variação em Interfaces Genéricas</span><span class="sxs-lookup"><span data-stu-id="426b4-127">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [<span data-ttu-id="426b4-128">in</span><span class="sxs-lookup"><span data-stu-id="426b4-128">in</span></span>](../../../csharp/language-reference/keywords/in-generic-modifier.md)  
 [<span data-ttu-id="426b4-129">Modificadores</span><span class="sxs-lookup"><span data-stu-id="426b4-129">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
