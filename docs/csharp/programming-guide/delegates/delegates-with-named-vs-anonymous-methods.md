---
title: Delegados com Métodos Nomeados vs. Métodos anônimos (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
ms.openlocfilehash: 93e140859e44aab860577feede40df6eab4c8e00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33330759"
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a><span data-ttu-id="06255-102">Delegados com Métodos Nomeados vs. Métodos anônimos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="06255-102">Delegates with Named vs. Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="06255-103">Um [delegado](../../../csharp/language-reference/keywords/delegate.md) pode ser associado a um método nomeado.</span><span class="sxs-lookup"><span data-stu-id="06255-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) can be associated with a named method.</span></span> <span data-ttu-id="06255-104">Ao instanciar um delegado usando um método nomeado, o método é passado como um parâmetro, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="06255-104">When you instantiate a delegate by using a named method, the method is passed as a parameter, for example:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#1](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_1.cs)]  
  
 <span data-ttu-id="06255-105">Isso é chamado usando um método nomeado.</span><span class="sxs-lookup"><span data-stu-id="06255-105">This is called using a named method.</span></span> <span data-ttu-id="06255-106">Os delegados construídos com um método nomeado podem encapsular um método [estático](../../../csharp/language-reference/keywords/static.md) ou um método de instância.</span><span class="sxs-lookup"><span data-stu-id="06255-106">Delegates constructed with a named method can encapsulate either a [static](../../../csharp/language-reference/keywords/static.md) method or an instance method.</span></span> <span data-ttu-id="06255-107">Métodos nomeados são a única maneira de instanciar um delegado nas versões anteriores do C#.</span><span class="sxs-lookup"><span data-stu-id="06255-107">Named methods are the only way to instantiate a delegate in earlier versions of C#.</span></span> <span data-ttu-id="06255-108">No entanto, em uma situação em que a criação de um novo método for uma sobrecarga indesejada, o C# permite instanciar um delegado e especificar imediatamente um bloco de código que esse delegado processará quando for chamado.</span><span class="sxs-lookup"><span data-stu-id="06255-108">However, in a situation where creating a new method is unwanted overhead, C# enables you to instantiate a delegate and immediately specify a code block that the delegate will process when it is called.</span></span> <span data-ttu-id="06255-109">O bloco pode conter uma expressão lambda ou um método anônimo.</span><span class="sxs-lookup"><span data-stu-id="06255-109">The block can contain either a lambda expression or an anonymous method.</span></span> <span data-ttu-id="06255-110">Para obter mais informações, consulte [Funções Anônimas](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="06255-110">For more information, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06255-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="06255-111">Remarks</span></span>  
 <span data-ttu-id="06255-112">O método passado como parâmetro delegado deve ter a mesma assinatura da declaração delegada.</span><span class="sxs-lookup"><span data-stu-id="06255-112">The method that you pass as a delegate parameter must have the same signature as the delegate declaration.</span></span>  
  
 <span data-ttu-id="06255-113">Uma instância de delegado pode encapsular o método estático ou de instância.</span><span class="sxs-lookup"><span data-stu-id="06255-113">A delegate instance may encapsulate either static or instance method.</span></span>  
  
 <span data-ttu-id="06255-114">Embora o delegado possa usar um parâmetro [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), não é recomendável utilizá-lo com delegados de evento multicast, pois não é possível saber qual delegado será chamado.</span><span class="sxs-lookup"><span data-stu-id="06255-114">Although the delegate can use an [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter, we do not recommend its use with multicast event delegates because you cannot know which delegate will be called.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="06255-115">Exemplo 1</span><span class="sxs-lookup"><span data-stu-id="06255-115">Example 1</span></span>  
 <span data-ttu-id="06255-116">Este é um exemplo simples de declaração usando um delegado.</span><span class="sxs-lookup"><span data-stu-id="06255-116">The following is a simple example of declaring and using a delegate.</span></span> <span data-ttu-id="06255-117">Observe que tanto o delegado, `Del` e o método associado, `MultiplyNumbers`, têm a mesma assinatura</span><span class="sxs-lookup"><span data-stu-id="06255-117">Notice that both the delegate, `Del`, and the associated method, `MultiplyNumbers`, have the same signature</span></span>  
  
 [!code-csharp[csProgGuideDelegates#2](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_2.cs)]  
  
## <a name="example-2"></a><span data-ttu-id="06255-118">Exemplo 2</span><span class="sxs-lookup"><span data-stu-id="06255-118">Example 2</span></span>  
 <span data-ttu-id="06255-119">No exemplo a seguir, um delegado é mapeado para métodos estáticos e de instância e retorna informações específicas sobre cada um.</span><span class="sxs-lookup"><span data-stu-id="06255-119">In the following example, one delegate is mapped to both static and instance methods and returns specific information from each.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#3](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="06255-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="06255-120">See Also</span></span>  
 [<span data-ttu-id="06255-121">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="06255-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="06255-122">Delegados</span><span class="sxs-lookup"><span data-stu-id="06255-122">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="06255-123">Métodos anônimos</span><span class="sxs-lookup"><span data-stu-id="06255-123">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [<span data-ttu-id="06255-124">Como combinar delegados (delegados multicast)</span><span class="sxs-lookup"><span data-stu-id="06255-124">How to: Combine Delegates (Multicast Delegates)</span></span>](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)  
 [<span data-ttu-id="06255-125">Eventos</span><span class="sxs-lookup"><span data-stu-id="06255-125">Events</span></span>](../../../csharp/programming-guide/events/index.md)
