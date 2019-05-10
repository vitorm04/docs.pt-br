---
title: Matrizes – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: 258ade63ab7c9008f6c892ed109bf5ea5ab974f3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584602"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="ac89a-102">Matrizes (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="ac89a-102">Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="ac89a-103">Você pode armazenar diversas variáveis do mesmo tipo em uma estrutura de dados de matriz.</span><span class="sxs-lookup"><span data-stu-id="ac89a-103">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="ac89a-104">Você pode declarar uma matriz especificando o tipo de seus elementos.</span><span class="sxs-lookup"><span data-stu-id="ac89a-104">You declare an array by specifying the type of its elements.</span></span>  
  
 `type[] arrayName;`  
  
 <span data-ttu-id="ac89a-105">O exemplo a seguir cria matrizes unidimensionais, multidimensionais e denteadas:</span><span class="sxs-lookup"><span data-stu-id="ac89a-105">The following example creates single-dimensional, multidimensional, and jagged arrays:</span></span>  
  
 [!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]  
  
## <a name="array-overview"></a><span data-ttu-id="ac89a-106">Visão geral de matriz</span><span class="sxs-lookup"><span data-stu-id="ac89a-106">Array Overview</span></span>

 <span data-ttu-id="ac89a-107">Uma matriz tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="ac89a-107">An array has the following properties:</span></span>  
  
- <span data-ttu-id="ac89a-108">Uma matriz pode ser [Unidimensional](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [Multidimensional](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) ou [Denteada](../../../csharp/programming-guide/arrays/jagged-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="ac89a-108">An array can be [Single-Dimensional](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [Multidimensional](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) or [Jagged](../../../csharp/programming-guide/arrays/jagged-arrays.md).</span></span>  
  
- <span data-ttu-id="ac89a-109">O número de dimensões e o tamanho de cada dimensão são estabelecidos quando a instância de matriz é criada.</span><span class="sxs-lookup"><span data-stu-id="ac89a-109">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="ac89a-110">Esses valores não podem ser alterados durante o ciclo de vida da instância.</span><span class="sxs-lookup"><span data-stu-id="ac89a-110">These values can't be changed during the lifetime of the instance.</span></span>  
  
- <span data-ttu-id="ac89a-111">Os valores padrão dos elementos de matriz numérica são definidos como zero, e os elementos de referência são definidos como null.</span><span class="sxs-lookup"><span data-stu-id="ac89a-111">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>  
  
- <span data-ttu-id="ac89a-112">Uma matriz denteada é uma matriz de matrizes e, portanto, seus elementos são tipos de referência e são inicializados para `null`.</span><span class="sxs-lookup"><span data-stu-id="ac89a-112">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
- <span data-ttu-id="ac89a-113">As matrizes são indexadas por zero: uma matriz com elementos `n` é indexada de `0` para `n-1`.</span><span class="sxs-lookup"><span data-stu-id="ac89a-113">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>  
  
- <span data-ttu-id="ac89a-114">Os elementos de matriz podem ser de qualquer tipo, inclusive um tipo de matriz.</span><span class="sxs-lookup"><span data-stu-id="ac89a-114">Array elements can be of any type, including an array type.</span></span>  
  
- <span data-ttu-id="ac89a-115">Os tipos de matriz são [tipos de referência](../../../csharp/language-reference/keywords/reference-types.md) derivados do tipo base abstrato <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="ac89a-115">Array types are [reference types](../../../csharp/language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="ac89a-116">Como esse tipo implementa <xref:System.Collections.IEnumerable> e <xref:System.Collections.Generic.IEnumerable%601>, você pode usar a iteração [foreach](../../../csharp/language-reference/keywords/foreach-in.md) em todas as matrizes em c#.</span><span class="sxs-lookup"><span data-stu-id="ac89a-116">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../../csharp/language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ac89a-117">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="ac89a-117">Related Sections</span></span>  
  
- [<span data-ttu-id="ac89a-118">Matrizes como objetos</span><span class="sxs-lookup"><span data-stu-id="ac89a-118">Arrays as Objects</span></span>](../../../csharp/programming-guide/arrays/arrays-as-objects.md)  
  
- [<span data-ttu-id="ac89a-119">Usando foreach com matrizes</span><span class="sxs-lookup"><span data-stu-id="ac89a-119">Using foreach with Arrays</span></span>](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
- [<span data-ttu-id="ac89a-120">Passando matrizes como argumentos</span><span class="sxs-lookup"><span data-stu-id="ac89a-120">Passing Arrays as Arguments</span></span>](../../../csharp/programming-guide/arrays/passing-arrays-as-arguments.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="ac89a-121">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="ac89a-121">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ac89a-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac89a-122">See also</span></span>

- [<span data-ttu-id="ac89a-123">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="ac89a-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="ac89a-124">Coleções</span><span class="sxs-lookup"><span data-stu-id="ac89a-124">Collections</span></span>](../../../csharp/programming-guide/concepts/collections.md)
