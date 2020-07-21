---
title: Matrizes como objetos – Guia de Programação em C#
description: As matrizes em C# são objetos da matriz de tipo base abstrata. Você pode usar as propriedades e outros membros de classe da matriz, como a propriedade Length.
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 984def3ef74b07d7099fae6cae6d6f8ce7e03e12
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474716"
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="904e4-104">Matrizes como objetos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="904e4-104">Arrays as Objects (C# Programming Guide)</span></span>

<span data-ttu-id="904e4-105">No C#, as matrizes são objetos e não apenas regiões endereçáveis de memória contígua, como no C e no C++.</span><span class="sxs-lookup"><span data-stu-id="904e4-105">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="904e4-106"><xref:System.Array> é o tipo base abstrato de todos os tipos de matriz.</span><span class="sxs-lookup"><span data-stu-id="904e4-106"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="904e4-107">Você pode usar as propriedades e outros membros da classe que o <xref:System.Array> tem.</span><span class="sxs-lookup"><span data-stu-id="904e4-107">You can use the properties and other class members that <xref:System.Array> has.</span></span> <span data-ttu-id="904e4-108">Um exemplo disso é usar a <xref:System.Array.Length%2A> propriedade para obter o comprimento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="904e4-108">An example of this is using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="904e4-109">O código a seguir atribui o comprimento da matriz `numbers`, que é `5`, a uma variável denominada `lengthOfNumbers`:</span><span class="sxs-lookup"><span data-stu-id="904e4-109">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<span data-ttu-id="904e4-110">A classe <xref:System.Array> fornece vários outros métodos e propriedades úteis para classificar, pesquisar e copiar matrizes.</span><span class="sxs-lookup"><span data-stu-id="904e4-110">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>

## <a name="example"></a><span data-ttu-id="904e4-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="904e4-111">Example</span></span>

<span data-ttu-id="904e4-112">Este exemplo usa a propriedade <xref:System.Array.Rank%2A> para exibir a quantidade de dimensões de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="904e4-112">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a><span data-ttu-id="904e4-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="904e4-113">See also</span></span>

- [<span data-ttu-id="904e4-114">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="904e4-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="904e4-115">matrizes</span><span class="sxs-lookup"><span data-stu-id="904e4-115">Arrays</span></span>](./index.md)
- [<span data-ttu-id="904e4-116">Matrizes unidimensionais</span><span class="sxs-lookup"><span data-stu-id="904e4-116">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="904e4-117">Matrizes multidimensionais</span><span class="sxs-lookup"><span data-stu-id="904e4-117">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="904e4-118">Matrizes denteadas</span><span class="sxs-lookup"><span data-stu-id="904e4-118">Jagged Arrays</span></span>](./jagged-arrays.md)
