---
title: "Usando foreach com matrizes (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 797cb9a63a5e1009b170b2afda8634bd21a50035
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a><span data-ttu-id="2b4d5-102">Usando foreach com matrizes (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="2b4d5-102">Using foreach with Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="2b4d5-103">O C# também oferece a instrução [foreach](../../../csharp/language-reference/keywords/foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="2b4d5-103">C# also provides the [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement.</span></span> <span data-ttu-id="2b4d5-104">Essa instrução fornece uma maneira simples e limpa de iterar através dos elementos de uma matriz ou qualquer coleção enumerável.</span><span class="sxs-lookup"><span data-stu-id="2b4d5-104">This statement provides a simple, clean way to iterate through the elements of an array or any enumerable collection.</span></span> <span data-ttu-id="2b4d5-105">A instrução `foreach` processa os elementos na ordem retornada pela matriz ou enumerador do tipo de coleção que normalmente vai do elemento 0 ao último.</span><span class="sxs-lookup"><span data-stu-id="2b4d5-105">The `foreach` statement processes elements in the order returned by the array or collection type’s enumerator, which is usually from the 0th element to the last.</span></span> <span data-ttu-id="2b4d5-106">Por exemplo, o código a seguir cria uma matriz chamada `numbers` e itera por ela com a instrução `foreach`:</span><span class="sxs-lookup"><span data-stu-id="2b4d5-106">For example, the following code creates an array called `numbers` and iterates through it with the `foreach` statement:</span></span>  
  
 [!code-csharp[csProgGuideArrays#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_1.cs)]  
  
 <span data-ttu-id="2b4d5-107">Com matrizes multidimensionais, você pode usar o mesmo método para iterar pelos elementos, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="2b4d5-107">With multidimensional arrays, you can use the same method to iterate through the elements, for example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#29](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_2.cs)]  
  
 <span data-ttu-id="2b4d5-108">No entanto, com matrizes multidimensionais, usar um loop aninhado [for](../../../csharp/language-reference/keywords/for.md) oferece mais controle sobre os elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="2b4d5-108">However, with multidimensional arrays, using a nested [for](../../../csharp/language-reference/keywords/for.md) loop gives you more control over the array elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b4d5-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b4d5-109">See Also</span></span>  
 <xref:System.Array>  
 [<span data-ttu-id="2b4d5-110">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="2b4d5-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2b4d5-111">Matrizes</span><span class="sxs-lookup"><span data-stu-id="2b4d5-111">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="2b4d5-112">Matrizes unidimensionais</span><span class="sxs-lookup"><span data-stu-id="2b4d5-112">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="2b4d5-113">Matrizes multidimensionais</span><span class="sxs-lookup"><span data-stu-id="2b4d5-113">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="2b4d5-114">Matrizes denteadas</span><span class="sxs-lookup"><span data-stu-id="2b4d5-114">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
