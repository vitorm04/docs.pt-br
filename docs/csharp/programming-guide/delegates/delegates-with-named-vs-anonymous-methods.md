---
title: "Delegados com Métodos Nomeados vs. Métodos anônimos (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d242f9ab1ecb1963f674d6094f05d78b77fbee9c
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a><span data-ttu-id="bce8f-102">Delegados com Métodos Nomeados vs. Métodos anônimos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="bce8f-102">Delegates with Named vs. Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="bce8f-103">Um [delegado](../../../csharp/language-reference/keywords/delegate.md) pode ser associado a um método nomeado.</span><span class="sxs-lookup"><span data-stu-id="bce8f-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) can be associated with a named method.</span></span> <span data-ttu-id="bce8f-104">Ao instanciar um delegado usando um método nomeado, o método é passado como um parâmetro, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="bce8f-104">When you instantiate a delegate by using a named method, the method is passed as a parameter, for example:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#1](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_1.cs)]  
  
 <span data-ttu-id="bce8f-105">Isso é chamado usando um método nomeado.</span><span class="sxs-lookup"><span data-stu-id="bce8f-105">This is called using a named method.</span></span> <span data-ttu-id="bce8f-106">Os delegados construídos com um método nomeado podem encapsular um método [estático](../../../csharp/language-reference/keywords/static.md) ou um método de instância.</span><span class="sxs-lookup"><span data-stu-id="bce8f-106">Delegates constructed with a named method can encapsulate either a [static](../../../csharp/language-reference/keywords/static.md) method or an instance method.</span></span> <span data-ttu-id="bce8f-107">Métodos nomeados são a única maneira de instanciar um delegado nas versões anteriores do C#.</span><span class="sxs-lookup"><span data-stu-id="bce8f-107">Named methods are the only way to instantiate a delegate in earlier versions of C#.</span></span> <span data-ttu-id="bce8f-108">No entanto, em uma situação em que a criação de um novo método for uma sobrecarga indesejada, o C# permite instanciar um delegado e especificar imediatamente um bloco de código que esse delegado processará quando for chamado.</span><span class="sxs-lookup"><span data-stu-id="bce8f-108">However, in a situation where creating a new method is unwanted overhead, C# enables you to instantiate a delegate and immediately specify a code block that the delegate will process when it is called.</span></span> <span data-ttu-id="bce8f-109">O bloco pode conter uma expressão lambda ou um método anônimo.</span><span class="sxs-lookup"><span data-stu-id="bce8f-109">The block can contain either a lambda expression or an anonymous method.</span></span> <span data-ttu-id="bce8f-110">Para obter mais informações, consulte [Funções Anônimas](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="bce8f-110">For more information, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bce8f-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="bce8f-111">Remarks</span></span>  
 <span data-ttu-id="bce8f-112">O método passado como parâmetro delegado deve ter a mesma assinatura da declaração delegada.</span><span class="sxs-lookup"><span data-stu-id="bce8f-112">The method that you pass as a delegate parameter must have the same signature as the delegate declaration.</span></span>  
  
 <span data-ttu-id="bce8f-113">Uma instância de delegado pode encapsular o método estático ou de instância.</span><span class="sxs-lookup"><span data-stu-id="bce8f-113">A delegate instance may encapsulate either static or instance method.</span></span>  
  
 <span data-ttu-id="bce8f-114">Embora o delegado possa usar um parâmetro [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), não é recomendável utilizá-lo com delegados de evento multicast, pois não é possível saber qual delegado será chamado.</span><span class="sxs-lookup"><span data-stu-id="bce8f-114">Although the delegate can use an [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter, we do not recommend its use with multicast event delegates because you cannot know which delegate will be called.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="bce8f-115">Exemplo 1</span><span class="sxs-lookup"><span data-stu-id="bce8f-115">Example 1</span></span>  
 <span data-ttu-id="bce8f-116">Este é um exemplo simples de declaração usando um delegado.</span><span class="sxs-lookup"><span data-stu-id="bce8f-116">The following is a simple example of declaring and using a delegate.</span></span> <span data-ttu-id="bce8f-117">Observe que tanto o delegado, `Del` e o método associado, `MultiplyNumbers`, têm a mesma assinatura</span><span class="sxs-lookup"><span data-stu-id="bce8f-117">Notice that both the delegate, `Del`, and the associated method, `MultiplyNumbers`, have the same signature</span></span>  
  
 [!code-csharp[csProgGuideDelegates#2](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_2.cs)]  
  
## <a name="example-2"></a><span data-ttu-id="bce8f-118">Exemplo 2</span><span class="sxs-lookup"><span data-stu-id="bce8f-118">Example 2</span></span>  
 <span data-ttu-id="bce8f-119">No exemplo a seguir, um delegado é mapeado para métodos estáticos e de instância e retorna informações específicas sobre cada um.</span><span class="sxs-lookup"><span data-stu-id="bce8f-119">In the following example, one delegate is mapped to both static and instance methods and returns specific information from each.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#3](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="bce8f-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bce8f-120">See Also</span></span>  
 [<span data-ttu-id="bce8f-121">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="bce8f-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bce8f-122">Delegados</span><span class="sxs-lookup"><span data-stu-id="bce8f-122">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="bce8f-123">Métodos anônimos</span><span class="sxs-lookup"><span data-stu-id="bce8f-123">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [<span data-ttu-id="bce8f-124">Como combinar delegados (delegados multicast)</span><span class="sxs-lookup"><span data-stu-id="bce8f-124">How to: Combine Delegates (Multicast Delegates)</span></span>](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)  
 [<span data-ttu-id="bce8f-125">Eventos</span><span class="sxs-lookup"><span data-stu-id="bce8f-125">Events</span></span>](../../../csharp/programming-guide/events/index.md)
