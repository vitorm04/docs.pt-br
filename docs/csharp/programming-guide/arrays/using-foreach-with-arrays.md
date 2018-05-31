---
title: Usando foreach com matrizes (Guia de Programação em C#)
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: b858f35167e24390a729769487ce98908a3d349f
ms.sourcegitcommit: 54231aa56fca059e9297888a96fbca1d4cf3746c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2018
ms.locfileid: "34549449"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a><span data-ttu-id="f2cea-102">Usando foreach com matrizes (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="f2cea-102">Using foreach with Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="f2cea-103">Essa instrução [foreach](../../language-reference/keywords/foreach-in.md) fornece uma maneira simples e limpa de iterar através dos elementos de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="f2cea-103">The [foreach](../../language-reference/keywords/foreach-in.md) statement provides a simple, clean way to iterate through the elements of an array.</span></span>

<span data-ttu-id="f2cea-104">Em matrizes unidimensionais, a instrução `foreach` processa elementos em ordem crescente de índice, começando com o índice 0 e terminando com índice `Length - 1`:</span><span class="sxs-lookup"><span data-stu-id="f2cea-104">For single-dimensional arrays, the `foreach` statement processes elements in increasing index order, starting with index 0 and ending with index `Length - 1`:</span></span>

[!code-csharp[csProgGuideArrays#28](./codesnippet/CSharp/using-foreach-with-arrays_1.cs)]

<span data-ttu-id="f2cea-105">Em matrizes multidimensionais, os elementos são percorridos de modo a que os índices da dimensão mais à direita sejam aumentados primeiro e, em seguida, da próxima dimensão à esquerda, e assim por diante seguindo para a esquerda:</span><span class="sxs-lookup"><span data-stu-id="f2cea-105">For multi-dimensional arrays, elements are traversed such that the indices of the rightmost dimension are increased first, then the next left dimension, and so on to the left:</span></span>

[!code-csharp[csProgGuideArrays#29](./codesnippet/CSharp/using-foreach-with-arrays_2.cs)]

<span data-ttu-id="f2cea-106">No entanto, com matrizes multidimensionais, usar um loop aninhado [for](../../language-reference/keywords/for.md) oferece mais controle sobre a ordem na qual processar os elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="f2cea-106">However, with multidimensional arrays, using a nested [for](../../language-reference/keywords/for.md) loop gives you more control over the order in which to process the array elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2cea-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2cea-107">See also</span></span>  
 <xref:System.Array>  
 [<span data-ttu-id="f2cea-108">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="f2cea-108">C# Programming Guide</span></span>](../index.md)  
 [<span data-ttu-id="f2cea-109">Matrizes</span><span class="sxs-lookup"><span data-stu-id="f2cea-109">Arrays</span></span>](index.md)  
 [<span data-ttu-id="f2cea-110">Matrizes unidimensionais</span><span class="sxs-lookup"><span data-stu-id="f2cea-110">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)  
 [<span data-ttu-id="f2cea-111">Matrizes multidimensionais</span><span class="sxs-lookup"><span data-stu-id="f2cea-111">Multidimensional Arrays</span></span>](multidimensional-arrays.md)  
 [<span data-ttu-id="f2cea-112">Matrizes denteadas</span><span class="sxs-lookup"><span data-stu-id="f2cea-112">Jagged Arrays</span></span>](jagged-arrays.md)
