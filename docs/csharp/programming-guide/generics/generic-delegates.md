---
title: Delegados genéricos (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: a9f06dcf608a83b53e894310f20810182cf6daa4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332901"
---
# <a name="generic-delegates-c-programming-guide"></a><span data-ttu-id="85db4-102">Delegados genéricos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="85db4-102">Generic Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="85db4-103">Um [delegado](../../../csharp/language-reference/keywords/delegate.md) pode definir seus próprios parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="85db4-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) can define its own type parameters.</span></span> <span data-ttu-id="85db4-104">O código que referencia o delegado genérico pode especificar o argumento de tipo para criar um tipo construído fechado, assim como quando uma classe genérica é instanciada ou quando um método genérico é chamado, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="85db4-104">Code that references the generic delegate can specify the type argument to create a closed constructed type, just like when instantiating a generic class or calling a generic method, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#36](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_1.cs)]  
  
 <span data-ttu-id="85db4-105">A versão 2.0 do C# tem um novo recurso chamado conversão de grupo de método, que pode ser aplicada a tipos concretos e de delegado genérico e habilita a gravação da linha anterior com esta sintaxe simplificada:</span><span class="sxs-lookup"><span data-stu-id="85db4-105">C# version 2.0 has a new feature called method group conversion, which applies to concrete as well as generic delegate types, and enables you to write the previous line with this simplified syntax:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#37](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_2.cs)]  
  
 <span data-ttu-id="85db4-106">Os delegados definidos em uma classe genérica podem usar os parâmetros de tipo da classe genérica da mesma forma que os métodos da classe.</span><span class="sxs-lookup"><span data-stu-id="85db4-106">Delegates defined within a generic class can use the generic class type parameters in the same way that class methods do.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#38](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_3.cs)]  
  
 <span data-ttu-id="85db4-107">O código que referencia o delegado deve especificar o argumento de tipo da classe recipiente, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="85db4-107">Code that references the delegate must specify the type argument of the containing class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#39](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_4.cs)]  
  
 <span data-ttu-id="85db4-108">Os delegados genéricos são especialmente úteis na definição de eventos com base no padrão de design comum, pois o argumento do remetente pode ser fortemente tipado e não precisa ser convertido de e para <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="85db4-108">Generic delegates are especially useful in defining events based on the typical design pattern because the sender argument can be strongly typed and no longer has to be cast to and from <xref:System.Object>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#40](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="85db4-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="85db4-109">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="85db4-110">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="85db4-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="85db4-111">Introdução aos genéricos</span><span class="sxs-lookup"><span data-stu-id="85db4-111">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [<span data-ttu-id="85db4-112">Métodos genéricos</span><span class="sxs-lookup"><span data-stu-id="85db4-112">Generic Methods</span></span>](../../../csharp/programming-guide/generics/generic-methods.md)  
 [<span data-ttu-id="85db4-113">Classes genéricas</span><span class="sxs-lookup"><span data-stu-id="85db4-113">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)  
 [<span data-ttu-id="85db4-114">Interfaces genéricas</span><span class="sxs-lookup"><span data-stu-id="85db4-114">Generic Interfaces</span></span>](../../../csharp/programming-guide/generics/generic-interfaces.md)  
 [<span data-ttu-id="85db4-115">Delegados</span><span class="sxs-lookup"><span data-stu-id="85db4-115">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="85db4-116">Genéricos</span><span class="sxs-lookup"><span data-stu-id="85db4-116">Generics</span></span>](~/docs/standard/generics/index.md)
