---
title: Delegados com métodos nomeados vs. anônimos – guia de programação C#
description: Saiba mais sobre delegados com métodos nomeados vs. anônimos. Confira exemplos de código e exiba recursos adicionais disponíveis.
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
ms.openlocfilehash: d8d2c6d8c7792b81f2fc2e25d0836e3780e58e52
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202494"
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a><span data-ttu-id="34490-104">Delegados com métodos nomeados versus anônimos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="34490-104">Delegates with Named vs. Anonymous Methods (C# Programming Guide)</span></span>

<span data-ttu-id="34490-105">Um [delegado](../../language-reference/builtin-types/reference-types.md) pode ser associado a um método nomeado.</span><span class="sxs-lookup"><span data-stu-id="34490-105">A [delegate](../../language-reference/builtin-types/reference-types.md) can be associated with a named method.</span></span> <span data-ttu-id="34490-106">Ao instanciar um delegado usando um método nomeado, o método é passado como um parâmetro, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="34490-106">When you instantiate a delegate by using a named method, the method is passed as a parameter, for example:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#1)]  
  
 <span data-ttu-id="34490-107">Isso é chamado usando um método nomeado.</span><span class="sxs-lookup"><span data-stu-id="34490-107">This is called using a named method.</span></span> <span data-ttu-id="34490-108">Os delegados construídos com um método nomeado podem encapsular um método [estático](../../language-reference/keywords/static.md) ou um método de instância.</span><span class="sxs-lookup"><span data-stu-id="34490-108">Delegates constructed with a named method can encapsulate either a [static](../../language-reference/keywords/static.md) method or an instance method.</span></span> <span data-ttu-id="34490-109">Métodos nomeados são a única maneira de instanciar um delegado nas versões anteriores do C#.</span><span class="sxs-lookup"><span data-stu-id="34490-109">Named methods are the only way to instantiate a delegate in earlier versions of C#.</span></span> <span data-ttu-id="34490-110">No entanto, em uma situação em que a criação de um novo método for uma sobrecarga indesejada, o C# permite instanciar um delegado e especificar imediatamente um bloco de código que esse delegado processará quando for chamado.</span><span class="sxs-lookup"><span data-stu-id="34490-110">However, in a situation where creating a new method is unwanted overhead, C# enables you to instantiate a delegate and immediately specify a code block that the delegate will process when it is called.</span></span> <span data-ttu-id="34490-111">O bloco pode conter uma expressão lambda ou um método anônimo.</span><span class="sxs-lookup"><span data-stu-id="34490-111">The block can contain either a lambda expression or an anonymous method.</span></span> <span data-ttu-id="34490-112">Para obter mais informações, consulte [Funções Anônimas](../statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="34490-112">For more information, see [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34490-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="34490-113">Remarks</span></span>  

 <span data-ttu-id="34490-114">O método passado como parâmetro delegado deve ter a mesma assinatura da declaração delegada.</span><span class="sxs-lookup"><span data-stu-id="34490-114">The method that you pass as a delegate parameter must have the same signature as the delegate declaration.</span></span>  
  
 <span data-ttu-id="34490-115">Uma instância de delegado pode encapsular o método estático ou de instância.</span><span class="sxs-lookup"><span data-stu-id="34490-115">A delegate instance may encapsulate either static or instance method.</span></span>  
  
 <span data-ttu-id="34490-116">Embora o delegado possa usar um parâmetro [out](../../language-reference/keywords/out-parameter-modifier.md), não é recomendável utilizá-lo com delegados de evento multicast, pois não é possível saber qual delegado será chamado.</span><span class="sxs-lookup"><span data-stu-id="34490-116">Although the delegate can use an [out](../../language-reference/keywords/out-parameter-modifier.md) parameter, we do not recommend its use with multicast event delegates because you cannot know which delegate will be called.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="34490-117">Exemplo 1</span><span class="sxs-lookup"><span data-stu-id="34490-117">Example 1</span></span>  

 <span data-ttu-id="34490-118">Este é um exemplo simples de declaração usando um delegado.</span><span class="sxs-lookup"><span data-stu-id="34490-118">The following is a simple example of declaring and using a delegate.</span></span> <span data-ttu-id="34490-119">Observe que tanto o delegado, `Del` e o método associado, `MultiplyNumbers`, têm a mesma assinatura</span><span class="sxs-lookup"><span data-stu-id="34490-119">Notice that both the delegate, `Del`, and the associated method, `MultiplyNumbers`, have the same signature</span></span>  
  
 [!code-csharp[csProgGuideDelegates#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#2)]  
  
## <a name="example-2"></a><span data-ttu-id="34490-120">Exemplo 2</span><span class="sxs-lookup"><span data-stu-id="34490-120">Example 2</span></span>  

 <span data-ttu-id="34490-121">No exemplo a seguir, um delegado é mapeado para métodos estáticos e de instância e retorna informações específicas sobre cada um.</span><span class="sxs-lookup"><span data-stu-id="34490-121">In the following example, one delegate is mapped to both static and instance methods and returns specific information from each.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="34490-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="34490-122">See also</span></span>

- [<span data-ttu-id="34490-123">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="34490-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="34490-124">Representantes</span><span class="sxs-lookup"><span data-stu-id="34490-124">Delegates</span></span>](./index.md)
- [<span data-ttu-id="34490-125">Como combinar delegados (delegados de multicast)</span><span class="sxs-lookup"><span data-stu-id="34490-125">How to combine delegates (Multicast Delegates)</span></span>](./how-to-combine-delegates-multicast-delegates.md)
- [<span data-ttu-id="34490-126">Eventos</span><span class="sxs-lookup"><span data-stu-id="34490-126">Events</span></span>](../events/index.md)
