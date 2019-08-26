---
title: Delegados genéricos – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: 31ab511bf88bfbc2134029564ecbf70aa75119d7
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659844"
---
# <a name="generic-delegates-c-programming-guide"></a><span data-ttu-id="8de71-102">Delegados genéricos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="8de71-102">Generic Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="8de71-103">Um [delegado](../../language-reference/keywords/delegate.md) pode definir seus próprios parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="8de71-103">A [delegate](../../language-reference/keywords/delegate.md) can define its own type parameters.</span></span> <span data-ttu-id="8de71-104">O código que referencia o delegado genérico pode especificar o argumento de tipo para criar um tipo construído fechado, assim como quando uma classe genérica é instanciada ou quando um método genérico é chamado, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="8de71-104">Code that references the generic delegate can specify the type argument to create a closed constructed type, just like when instantiating a generic class or calling a generic method, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#36)]  
  
 <span data-ttu-id="8de71-105">A versão 2.0 do C# tem um novo recurso chamado conversão de grupo de método, que pode ser aplicada a tipos concretos e de delegado genérico e habilita a gravação da linha anterior com esta sintaxe simplificada:</span><span class="sxs-lookup"><span data-stu-id="8de71-105">C# version 2.0 has a new feature called method group conversion, which applies to concrete as well as generic delegate types, and enables you to write the previous line with this simplified syntax:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#37)]  
  
 <span data-ttu-id="8de71-106">Os delegados definidos em uma classe genérica podem usar os parâmetros de tipo da classe genérica da mesma forma que os métodos da classe.</span><span class="sxs-lookup"><span data-stu-id="8de71-106">Delegates defined within a generic class can use the generic class type parameters in the same way that class methods do.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#38)]  
  
 <span data-ttu-id="8de71-107">O código que referencia o delegado deve especificar o argumento de tipo da classe recipiente, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="8de71-107">Code that references the delegate must specify the type argument of the containing class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#39)]  
  
 <span data-ttu-id="8de71-108">Os delegados genéricos são especialmente úteis na definição de eventos com base no padrão de design comum, pois o argumento do remetente pode ser fortemente tipado e não precisa ser convertido de e para <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="8de71-108">Generic delegates are especially useful in defining events based on the typical design pattern because the sender argument can be strongly typed and no longer has to be cast to and from <xref:System.Object>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#40)]  
  
## <a name="see-also"></a><span data-ttu-id="8de71-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8de71-109">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="8de71-110">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="8de71-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8de71-111">Introdução aos genéricos</span><span class="sxs-lookup"><span data-stu-id="8de71-111">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="8de71-112">Métodos genéricos</span><span class="sxs-lookup"><span data-stu-id="8de71-112">Generic Methods</span></span>](./generic-methods.md)
- [<span data-ttu-id="8de71-113">Classes genéricas</span><span class="sxs-lookup"><span data-stu-id="8de71-113">Generic Classes</span></span>](./generic-classes.md)
- [<span data-ttu-id="8de71-114">Interfaces genéricas</span><span class="sxs-lookup"><span data-stu-id="8de71-114">Generic Interfaces</span></span>](./generic-interfaces.md)
- [<span data-ttu-id="8de71-115">Delegados</span><span class="sxs-lookup"><span data-stu-id="8de71-115">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="8de71-116">Genéricos</span><span class="sxs-lookup"><span data-stu-id="8de71-116">Generics</span></span>](../../../standard/generics/index.md)
