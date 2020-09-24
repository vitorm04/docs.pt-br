---
title: Métodos genéricos – Guia de Programação em C#
description: Saiba mais sobre os métodos declarados com parâmetros de tipo, conhecidos como métodos genéricos. Confira exemplos de código e exiba recursos adicionais disponíveis.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 195e3f11c73a17931fa6331750e2ae4ee8fd6f10
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151461"
---
# <a name="generic-methods-c-programming-guide"></a><span data-ttu-id="4a61b-104">Métodos genéricos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="4a61b-104">Generic Methods (C# Programming Guide)</span></span>

<span data-ttu-id="4a61b-105">Um método genérico é um método declarado com parâmetros de tipo, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="4a61b-105">A generic method is a method that is declared with type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#22)]  
  
 <span data-ttu-id="4a61b-106">O exemplo de código a seguir mostra uma maneira de chamar o método usando `int` para o argumento de tipo:</span><span class="sxs-lookup"><span data-stu-id="4a61b-106">The following code example shows one way to call the method by using `int` for the type argument:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#23)]  
  
 <span data-ttu-id="4a61b-107">Também é possível omitir o argumento de tipo e o compilador o inferirá.</span><span class="sxs-lookup"><span data-stu-id="4a61b-107">You can also omit the type argument and the compiler will infer it.</span></span> <span data-ttu-id="4a61b-108">Esta chamada para `Swap` é equivalente à chamada anterior:</span><span class="sxs-lookup"><span data-stu-id="4a61b-108">The following call to `Swap` is equivalent to the previous call:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#24)]  
  
 <span data-ttu-id="4a61b-109">As mesmas regras de inferência de tipos se aplicam a métodos estáticos e métodos de instância.</span><span class="sxs-lookup"><span data-stu-id="4a61b-109">The same rules for type inference apply to static methods and instance methods.</span></span> <span data-ttu-id="4a61b-110">O compilador pode inferir os parâmetros de tipo com base nos argumentos de método passados; não é possível inferir os parâmetros de tipo somente de uma restrição ou valor retornado.</span><span class="sxs-lookup"><span data-stu-id="4a61b-110">The compiler can infer the type parameters based on the method arguments you pass in; it cannot infer the type parameters only from a constraint or return value.</span></span> <span data-ttu-id="4a61b-111">Portanto, a inferência de tipos não funciona com métodos que não têm parâmetros.</span><span class="sxs-lookup"><span data-stu-id="4a61b-111">Therefore type inference does not work with methods that have no parameters.</span></span> <span data-ttu-id="4a61b-112">A inferência de tipos ocorre em tempo de compilação, antes de o compilador tentar resolver assinaturas de método sobrecarregadas.</span><span class="sxs-lookup"><span data-stu-id="4a61b-112">Type inference occurs at compile time before the compiler tries to resolve overloaded method signatures.</span></span> <span data-ttu-id="4a61b-113">O compilador aplica a lógica da inferência de tipos a todos os métodos genéricos que compartilham o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="4a61b-113">The compiler applies type inference logic to all generic methods that share the same name.</span></span> <span data-ttu-id="4a61b-114">Na etapa de resolução de sobrecarga, o compilador incluirá somente os métodos genéricos em que a inferência de tipos foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="4a61b-114">In the overload resolution step, the compiler includes only those generic methods on which type inference succeeded.</span></span>  
  
 <span data-ttu-id="4a61b-115">Em uma classe genérica, métodos não genéricos podem acessar os parâmetros de tipo de nível de classe, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="4a61b-115">Within a generic class, non-generic methods can access the class-level type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#25)]  
  
 <span data-ttu-id="4a61b-116">Se um método genérico que usa os mesmos parâmetros de tipo da classe que o contém for definido, o compilador gerará um aviso [CS0693](../../misc/cs0693.md), pois, dentro do escopo do método, o argumento fornecido para o `T` interno oculta o argumento fornecido para o `T` externo.</span><span class="sxs-lookup"><span data-stu-id="4a61b-116">If you define a generic method that takes the same type parameters as the containing class, the compiler generates warning [CS0693](../../misc/cs0693.md) because within the method scope, the argument supplied for the inner `T` hides the argument supplied for the outer `T`.</span></span> <span data-ttu-id="4a61b-117">Caso seja necessária a flexibilidade de chamar um método de classe genérica com argumentos de tipo diferentes dos fornecidos quando a instância da classe foi criada, considere fornecer outro identificador ao parâmetro de tipo do método, conforme mostrado no `GenericList2<T>` do exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4a61b-117">If you require the flexibility of calling a generic class method with type arguments other than the ones provided when the class was instantiated, consider providing another identifier for the type parameter of the method, as shown in `GenericList2<T>` in the following example.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#26)]  
  
 <span data-ttu-id="4a61b-118">Use restrições para permitir operações mais especializadas em parâmetros de tipo de métodos.</span><span class="sxs-lookup"><span data-stu-id="4a61b-118">Use constraints to enable more specialized operations on type parameters in methods.</span></span> <span data-ttu-id="4a61b-119">Essa versão do `Swap<T>`, agora denominada `SwapIfGreater<T>`, pode ser usada somente com argumentos de tipo que implementam <xref:System.IComparable%601>.</span><span class="sxs-lookup"><span data-stu-id="4a61b-119">This version of `Swap<T>`, now named `SwapIfGreater<T>`, can only be used with type arguments that implement <xref:System.IComparable%601>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#27)]  
  
 <span data-ttu-id="4a61b-120">Métodos genéricos podem ser sobrecarregados vários parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="4a61b-120">Generic methods can be overloaded on several type parameters.</span></span> <span data-ttu-id="4a61b-121">Por exemplo, todos os seguintes métodos podem ser localizados na mesma classe:</span><span class="sxs-lookup"><span data-stu-id="4a61b-121">For example, the following methods can all be located in the same class:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#28)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="4a61b-122">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="4a61b-122">C# Language Specification</span></span>  

 <span data-ttu-id="4a61b-123">Para obter mais informações, consulte a [especificação da linguagem C#](~/_csharplang/spec/classes.md#methods).</span><span class="sxs-lookup"><span data-stu-id="4a61b-123">For more information, see the [C# Language Specification](~/_csharplang/spec/classes.md#methods).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a61b-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="4a61b-124">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="4a61b-125">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="4a61b-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4a61b-126">Introdução aos genéricos</span><span class="sxs-lookup"><span data-stu-id="4a61b-126">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="4a61b-127">Métodos</span><span class="sxs-lookup"><span data-stu-id="4a61b-127">Methods</span></span>](../classes-and-structs/methods.md)
