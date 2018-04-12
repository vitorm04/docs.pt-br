---
title: Métodos genéricos (Guia de Programação em C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
caps.latest.revision: 27
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 63252dbe4307889f57d35e23eb0575f84358d737
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="generic-methods-c-programming-guide"></a><span data-ttu-id="6e014-102">Métodos genéricos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="6e014-102">Generic Methods (C# Programming Guide)</span></span>
<span data-ttu-id="6e014-103">Um método genérico é um método declarado com parâmetros de tipo, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="6e014-103">A generic method is a method that is declared with type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#22](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_1.cs)]  
  
 <span data-ttu-id="6e014-104">O exemplo de código a seguir mostra uma maneira de chamar o método usando `int` para o argumento de tipo:</span><span class="sxs-lookup"><span data-stu-id="6e014-104">The following code example shows one way to call the method by using `int` for the type argument:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#23](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_2.cs)]  
  
 <span data-ttu-id="6e014-105">Também é possível omitir o argumento de tipo e o compilador o inferirá.</span><span class="sxs-lookup"><span data-stu-id="6e014-105">You can also omit the type argument and the compiler will infer it.</span></span> <span data-ttu-id="6e014-106">Esta chamada para `Swap` é equivalente à chamada anterior:</span><span class="sxs-lookup"><span data-stu-id="6e014-106">The following call to `Swap` is equivalent to the previous call:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#24](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_3.cs)]  
  
 <span data-ttu-id="6e014-107">As mesmas regras de inferência de tipos se aplicam a métodos estáticos e métodos de instância.</span><span class="sxs-lookup"><span data-stu-id="6e014-107">The same rules for type inference apply to static methods and instance methods.</span></span> <span data-ttu-id="6e014-108">O compilador pode inferir os parâmetros de tipo com base nos argumentos de método passados; não é possível inferir os parâmetros de tipo somente de uma restrição ou valor retornado.</span><span class="sxs-lookup"><span data-stu-id="6e014-108">The compiler can infer the type parameters based on the method arguments you pass in; it cannot infer the type parameters only from a constraint or return value.</span></span> <span data-ttu-id="6e014-109">Portanto, a inferência de tipos não funciona com métodos que não têm parâmetros.</span><span class="sxs-lookup"><span data-stu-id="6e014-109">Therefore type inference does not work with methods that have no parameters.</span></span> <span data-ttu-id="6e014-110">A inferência de tipos ocorre em tempo de compilação, antes de o compilador tentar resolver assinaturas de método sobrecarregadas.</span><span class="sxs-lookup"><span data-stu-id="6e014-110">Type inference occurs at compile time before the compiler tries to resolve overloaded method signatures.</span></span> <span data-ttu-id="6e014-111">O compilador aplica a lógica da inferência de tipos a todos os métodos genéricos que compartilham o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="6e014-111">The compiler applies type inference logic to all generic methods that share the same name.</span></span> <span data-ttu-id="6e014-112">Na etapa de resolução de sobrecarga, o compilador incluirá somente os métodos genéricos em que a inferência de tipos foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e014-112">In the overload resolution step, the compiler includes only those generic methods on which type inference succeeded.</span></span>  
  
 <span data-ttu-id="6e014-113">Em uma classe genérica, métodos não genéricos podem acessar os parâmetros de tipo de nível de classe, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="6e014-113">Within a generic class, non-generic methods can access the class-level type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#25](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_4.cs)]  
  
 <span data-ttu-id="6e014-114">Se um método genérico que usa os mesmos parâmetros de tipo da classe que o contém for definido, o compilador gerará um aviso CS0693, pois, dentro do escopo do método, o argumento fornecido para o `T` interno oculta o argumento fornecido para o `T` externo.</span><span class="sxs-lookup"><span data-stu-id="6e014-114">If you define a generic method that takes the same type parameters as the containing class, the compiler generates warning CS0693 because within the method scope, the argument supplied for the inner `T` hides the argument supplied for the outer `T`.</span></span> <span data-ttu-id="6e014-115">Caso seja necessária a flexibilidade de chamar um método de classe genérica com argumentos de tipo diferentes dos fornecidos quando a instância da classe foi criada, considere fornecer outro identificador ao parâmetro de tipo do método, conforme mostrado no `GenericList2<T>` do exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6e014-115">If you require the flexibility of calling a generic class method with type arguments other than the ones provided when the class was instantiated, consider providing another identifier for the type parameter of the method, as shown in `GenericList2<T>` in the following example.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#26](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_5.cs)]  
  
 <span data-ttu-id="6e014-116">Use restrições para permitir operações mais especializadas em parâmetros de tipo de métodos.</span><span class="sxs-lookup"><span data-stu-id="6e014-116">Use constraints to enable more specialized operations on type parameters in methods.</span></span> <span data-ttu-id="6e014-117">Essa versão do `Swap<T>`, agora denominada `SwapIfGreater<T>`, pode ser usada somente com argumentos de tipo que implementam <xref:System.IComparable%601>.</span><span class="sxs-lookup"><span data-stu-id="6e014-117">This version of `Swap<T>`, now named `SwapIfGreater<T>`, can only be used with type arguments that implement <xref:System.IComparable%601>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#27](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_6.cs)]  
  
 <span data-ttu-id="6e014-118">Métodos genéricos podem ser sobrecarregados vários parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="6e014-118">Generic methods can be overloaded on several type parameters.</span></span> <span data-ttu-id="6e014-119">Por exemplo, todos os seguintes métodos podem ser localizados na mesma classe:</span><span class="sxs-lookup"><span data-stu-id="6e014-119">For example, the following methods can all be located in the same class:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#28](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_7.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="6e014-120">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="6e014-120">C# Language Specification</span></span>  
 <span data-ttu-id="6e014-121">Para obter mais informações, consulte a [Especificação da linguagem C#](../../../csharp/language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="6e014-121">For more information, see the [C# Language Specification](../../../csharp/language-reference/language-specification/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e014-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e014-122">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="6e014-123">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="6e014-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6e014-124">Introdução aos genéricos</span><span class="sxs-lookup"><span data-stu-id="6e014-124">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [<span data-ttu-id="6e014-125">Métodos</span><span class="sxs-lookup"><span data-stu-id="6e014-125">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
