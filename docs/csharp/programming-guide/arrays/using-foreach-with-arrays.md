---
title: Usar foreach com matrizes – Guia de Programação em C#
ms.custom: seodec18
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: a22cb939370b38780881eca0d9585a14002c8250
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966405"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a><span data-ttu-id="c8c68-102">Usar foreach com matrizes (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="c8c68-102">Using foreach with arrays (C# Programming Guide)</span></span>

<span data-ttu-id="c8c68-103">Essa instrução [foreach](../../language-reference/keywords/foreach-in.md) fornece uma maneira simples e limpa de iterar através dos elementos de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="c8c68-103">The [foreach](../../language-reference/keywords/foreach-in.md) statement provides a simple, clean way to iterate through the elements of an array.</span></span>

<span data-ttu-id="c8c68-104">Em matrizes unidimensionais, a instrução `foreach` processa elementos em ordem crescente de índice, começando com o índice 0 e terminando com índice `Length - 1`:</span><span class="sxs-lookup"><span data-stu-id="c8c68-104">For single-dimensional arrays, the `foreach` statement processes elements in increasing index order, starting with index 0 and ending with index `Length - 1`:</span></span>

 [!code-csharp[csProgGuideArrays#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#28)]

<span data-ttu-id="c8c68-105">Em matrizes multidimensionais, os elementos são percorridos de modo a que os índices da dimensão mais à direita sejam aumentados primeiro e, em seguida, da próxima dimensão à esquerda, e assim por diante seguindo para a esquerda:</span><span class="sxs-lookup"><span data-stu-id="c8c68-105">For multi-dimensional arrays, elements are traversed such that the indices of the rightmost dimension are increased first, then the next left dimension, and so on to the left:</span></span>

 [!code-csharp[csProgGuideArrays#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#29)]

<span data-ttu-id="c8c68-106">No entanto, com matrizes multidimensionais, usar um loop aninhado [for](../../language-reference/keywords/for.md) oferece mais controle sobre a ordem na qual processar os elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="c8c68-106">However, with multidimensional arrays, using a nested [for](../../language-reference/keywords/for.md) loop gives you more control over the order in which to process the array elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="c8c68-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8c68-107">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="c8c68-108">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="c8c68-108">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c8c68-109">Matrizes</span><span class="sxs-lookup"><span data-stu-id="c8c68-109">Arrays</span></span>](index.md)
- [<span data-ttu-id="c8c68-110">Matrizes unidimensionais</span><span class="sxs-lookup"><span data-stu-id="c8c68-110">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="c8c68-111">Matrizes multidimensionais</span><span class="sxs-lookup"><span data-stu-id="c8c68-111">Multidimensional Arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="c8c68-112">Matrizes denteadas</span><span class="sxs-lookup"><span data-stu-id="c8c68-112">Jagged Arrays</span></span>](jagged-arrays.md)
