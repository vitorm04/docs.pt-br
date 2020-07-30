---
title: Delegados genéricos – Guia de Programação em C#
description: Saiba mais sobre como usar delegados genéricos em C#. Consulte exemplos de código e exiba recursos adicionais disponíveis.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: d99271ca9f12e95743d633caac16aaa4151e9c41
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301899"
---
# <a name="generic-delegates-c-programming-guide"></a><span data-ttu-id="b3f63-104">Delegados genéricos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="b3f63-104">Generic Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="b3f63-105">Um [delegado](../../language-reference/builtin-types/reference-types.md) pode definir seus próprios parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="b3f63-105">A [delegate](../../language-reference/builtin-types/reference-types.md) can define its own type parameters.</span></span> <span data-ttu-id="b3f63-106">O código que referencia o delegado genérico pode especificar o argumento de tipo para criar um tipo construído fechado, assim como quando uma classe genérica é instanciada ou quando um método genérico é chamado, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b3f63-106">Code that references the generic delegate can specify the type argument to create a closed constructed type, just like when instantiating a generic class or calling a generic method, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#36)]  
  
 <span data-ttu-id="b3f63-107">A versão 2.0 do C# tem um novo recurso chamado conversão de grupo de método, que pode ser aplicada a tipos concretos e de delegado genérico e habilita a gravação da linha anterior com esta sintaxe simplificada:</span><span class="sxs-lookup"><span data-stu-id="b3f63-107">C# version 2.0 has a new feature called method group conversion, which applies to concrete as well as generic delegate types, and enables you to write the previous line with this simplified syntax:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#37)]  
  
 <span data-ttu-id="b3f63-108">Os delegados definidos em uma classe genérica podem usar os parâmetros de tipo da classe genérica da mesma forma que os métodos da classe.</span><span class="sxs-lookup"><span data-stu-id="b3f63-108">Delegates defined within a generic class can use the generic class type parameters in the same way that class methods do.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#38)]  
  
 <span data-ttu-id="b3f63-109">O código que referencia o delegado deve especificar o argumento de tipo da classe recipiente, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b3f63-109">Code that references the delegate must specify the type argument of the containing class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#39)]  
  
 <span data-ttu-id="b3f63-110">Os delegados genéricos são especialmente úteis na definição de eventos com base no padrão de design comum, pois o argumento do remetente pode ser fortemente tipado e não precisa ser convertido de e para <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="b3f63-110">Generic delegates are especially useful in defining events based on the typical design pattern because the sender argument can be strongly typed and no longer has to be cast to and from <xref:System.Object>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#40)]  
  
## <a name="see-also"></a><span data-ttu-id="b3f63-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="b3f63-111">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="b3f63-112">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="b3f63-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b3f63-113">Introdução aos genéricos</span><span class="sxs-lookup"><span data-stu-id="b3f63-113">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="b3f63-114">Métodos genéricos</span><span class="sxs-lookup"><span data-stu-id="b3f63-114">Generic Methods</span></span>](./generic-methods.md)
- [<span data-ttu-id="b3f63-115">Classes genéricas</span><span class="sxs-lookup"><span data-stu-id="b3f63-115">Generic Classes</span></span>](./generic-classes.md)
- [<span data-ttu-id="b3f63-116">Interfaces genéricas</span><span class="sxs-lookup"><span data-stu-id="b3f63-116">Generic Interfaces</span></span>](./generic-interfaces.md)
- [<span data-ttu-id="b3f63-117">Representantes</span><span class="sxs-lookup"><span data-stu-id="b3f63-117">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="b3f63-118">Genéricos</span><span class="sxs-lookup"><span data-stu-id="b3f63-118">Generics</span></span>](../../../standard/generics/index.md)
