---
title: Matrizes como objetos – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 0bbbf7ecc5eff650f7a2edc73546833afd2be094
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242328"
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="24e15-102">Matrizes como objetos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="24e15-102">Arrays as Objects (C# Programming Guide)</span></span>

<span data-ttu-id="24e15-103">No C#, as matrizes são objetos e não apenas regiões endereçáveis de memória contígua, como no C e no C++.</span><span class="sxs-lookup"><span data-stu-id="24e15-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="24e15-104"><xref:System.Array> é o tipo base abstrato de todos os tipos de matriz.</span><span class="sxs-lookup"><span data-stu-id="24e15-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="24e15-105">É possível usar as propriedades e outros membros de classe do <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="24e15-105">You can use the properties, and other class members, that <xref:System.Array> has.</span></span> <span data-ttu-id="24e15-106">Um exemplo disso é o uso da propriedade <xref:System.Array.Length%2A> para obter o comprimento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="24e15-106">An example of this would be using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="24e15-107">O código a seguir atribui o comprimento da matriz `numbers`, que é `5`, a uma variável denominada `lengthOfNumbers`:</span><span class="sxs-lookup"><span data-stu-id="24e15-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>  
  
 [!code-csharp[csProgGuideArrays#3](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_1.cs)]  
  
 <span data-ttu-id="24e15-108">A classe <xref:System.Array> fornece vários outros métodos e propriedades úteis para classificar, pesquisar e copiar matrizes.</span><span class="sxs-lookup"><span data-stu-id="24e15-108">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24e15-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="24e15-109">Example</span></span>

 <span data-ttu-id="24e15-110">Este exemplo usa a propriedade <xref:System.Array.Rank%2A> para exibir a quantidade de dimensões de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="24e15-110">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>  
  
 [!code-csharp[csProgGuideArrays#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="24e15-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24e15-111">See Also</span></span>

- [<span data-ttu-id="24e15-112">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="24e15-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="24e15-113">Matrizes</span><span class="sxs-lookup"><span data-stu-id="24e15-113">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
- [<span data-ttu-id="24e15-114">Matrizes unidimensionais</span><span class="sxs-lookup"><span data-stu-id="24e15-114">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
- [<span data-ttu-id="24e15-115">Matrizes multidimensionais</span><span class="sxs-lookup"><span data-stu-id="24e15-115">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
- [<span data-ttu-id="24e15-116">Matrizes denteadas</span><span class="sxs-lookup"><span data-stu-id="24e15-116">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
