---
title: Matrizes como objetos – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: fd4496e0f84953204ad8c3f40db699e911c3f477
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597353"
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="7177d-102">Matrizes como objetos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="7177d-102">Arrays as Objects (C# Programming Guide)</span></span>

<span data-ttu-id="7177d-103">No C#, as matrizes são objetos e não apenas regiões endereçáveis de memória contígua, como no C e no C++.</span><span class="sxs-lookup"><span data-stu-id="7177d-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="7177d-104"><xref:System.Array> é o tipo base abstrato de todos os tipos de matriz.</span><span class="sxs-lookup"><span data-stu-id="7177d-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="7177d-105">É possível usar as propriedades e outros membros de classe do <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="7177d-105">You can use the properties, and other class members, that <xref:System.Array> has.</span></span> <span data-ttu-id="7177d-106">Um exemplo disso é o uso da propriedade <xref:System.Array.Length%2A> para obter o comprimento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="7177d-106">An example of this would be using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="7177d-107">O código a seguir atribui o comprimento da matriz `numbers`, que é `5`, a uma variável denominada `lengthOfNumbers`:</span><span class="sxs-lookup"><span data-stu-id="7177d-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>  
  
 [!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]  
  
 <span data-ttu-id="7177d-108">A classe <xref:System.Array> fornece vários outros métodos e propriedades úteis para classificar, pesquisar e copiar matrizes.</span><span class="sxs-lookup"><span data-stu-id="7177d-108">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7177d-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7177d-109">Example</span></span>

 <span data-ttu-id="7177d-110">Este exemplo usa a propriedade <xref:System.Array.Rank%2A> para exibir a quantidade de dimensões de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="7177d-110">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>  
  
 [!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]  
  
## <a name="see-also"></a><span data-ttu-id="7177d-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7177d-111">See also</span></span>

- [<span data-ttu-id="7177d-112">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="7177d-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7177d-113">Matrizes</span><span class="sxs-lookup"><span data-stu-id="7177d-113">Arrays</span></span>](./index.md)
- [<span data-ttu-id="7177d-114">Matrizes unidimensionais</span><span class="sxs-lookup"><span data-stu-id="7177d-114">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="7177d-115">Matrizes multidimensionais</span><span class="sxs-lookup"><span data-stu-id="7177d-115">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="7177d-116">Matrizes denteadas</span><span class="sxs-lookup"><span data-stu-id="7177d-116">Jagged Arrays</span></span>](./jagged-arrays.md)
