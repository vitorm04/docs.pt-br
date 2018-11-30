---
title: Matrizes (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: 2c3f22cb2a011aea9f0fff9ef49d1fd780d6d832
ms.sourcegitcommit: 7f7664837d35320a0bad3f7e4ecd68d6624633b2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2018
ms.locfileid: "52671948"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="34ff1-102">Matrizes (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="34ff1-102">Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="34ff1-103">Você pode armazenar diversas variáveis do mesmo tipo em uma estrutura de dados de matriz.</span><span class="sxs-lookup"><span data-stu-id="34ff1-103">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="34ff1-104">Você pode declarar uma matriz especificando o tipo de seus elementos.</span><span class="sxs-lookup"><span data-stu-id="34ff1-104">You declare an array by specifying the type of its elements.</span></span>  
  
 `type[] arrayName;`  
  
 <span data-ttu-id="34ff1-105">Os exemplos a seguir criam matrizes unidimensionais, multidimensionais e denteadas:</span><span class="sxs-lookup"><span data-stu-id="34ff1-105">The following examples create single-dimensional, multidimensional, and jagged arrays:</span></span>  
  
 [!code-csharp[csProgGuideArrays#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/index_1.cs)]  
  
## <a name="array-overview"></a><span data-ttu-id="34ff1-106">Visão geral de matriz</span><span class="sxs-lookup"><span data-stu-id="34ff1-106">Array Overview</span></span>

 <span data-ttu-id="34ff1-107">Uma matriz tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="34ff1-107">An array has the following properties:</span></span>  
  
-   <span data-ttu-id="34ff1-108">Uma matriz pode ser [Unidimensional](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [Multidimensional](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) ou [Denteada](../../../csharp/programming-guide/arrays/jagged-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="34ff1-108">An array can be [Single-Dimensional](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [Multidimensional](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) or [Jagged](../../../csharp/programming-guide/arrays/jagged-arrays.md).</span></span>  
  
-   <span data-ttu-id="34ff1-109">O número de dimensões e o tamanho de cada dimensão são estabelecidos quando a instância de matriz é criada.</span><span class="sxs-lookup"><span data-stu-id="34ff1-109">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="34ff1-110">Esses valores não podem ser alterados durante o ciclo de vida da instância.</span><span class="sxs-lookup"><span data-stu-id="34ff1-110">These values can't be changed during the lifetime of the instance.</span></span>  
  
-   <span data-ttu-id="34ff1-111">Os valores padrão dos elementos de matriz numérica são definidos como zero, e os elementos de referência são definidos como null.</span><span class="sxs-lookup"><span data-stu-id="34ff1-111">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>  
  
-   <span data-ttu-id="34ff1-112">Uma matriz denteada é uma matriz de matrizes e, portanto, seus elementos são tipos de referência e são inicializados para `null`.</span><span class="sxs-lookup"><span data-stu-id="34ff1-112">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
-   <span data-ttu-id="34ff1-113">As matrizes são indexadas por zero: uma matriz com elementos `n` é indexada de `0` para `n-1`.</span><span class="sxs-lookup"><span data-stu-id="34ff1-113">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>  
  
-   <span data-ttu-id="34ff1-114">Os elementos de matriz podem ser de qualquer tipo, inclusive um tipo de matriz.</span><span class="sxs-lookup"><span data-stu-id="34ff1-114">Array elements can be of any type, including an array type.</span></span>  
  
-   <span data-ttu-id="34ff1-115">Os tipos de matriz são [tipos de referência](../../../csharp/language-reference/keywords/reference-types.md) derivados do tipo base abstrato <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="34ff1-115">Array types are [reference types](../../../csharp/language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="34ff1-116">Como esse tipo implementa <xref:System.Collections.IEnumerable> e <xref:System.Collections.Generic.IEnumerable%601>, você pode usar a iteração [foreach](../../../csharp/language-reference/keywords/foreach-in.md) em todas as matrizes em c#.</span><span class="sxs-lookup"><span data-stu-id="34ff1-116">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../../csharp/language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="34ff1-117">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="34ff1-117">Related Sections</span></span>  
  
-   [<span data-ttu-id="34ff1-118">Matrizes como objetos</span><span class="sxs-lookup"><span data-stu-id="34ff1-118">Arrays as Objects</span></span>](../../../csharp/programming-guide/arrays/arrays-as-objects.md)  
  
-   [<span data-ttu-id="34ff1-119">Usando foreach com matrizes</span><span class="sxs-lookup"><span data-stu-id="34ff1-119">Using foreach with Arrays</span></span>](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
-   [<span data-ttu-id="34ff1-120">Passando matrizes como argumentos</span><span class="sxs-lookup"><span data-stu-id="34ff1-120">Passing Arrays as Arguments</span></span>](../../../csharp/programming-guide/arrays/passing-arrays-as-arguments.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="34ff1-121">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="34ff1-121">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="34ff1-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34ff1-122">See Also</span></span>

- [<span data-ttu-id="34ff1-123">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="34ff1-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="34ff1-124">Coleções</span><span class="sxs-lookup"><span data-stu-id="34ff1-124">Collections</span></span>](../../../csharp/programming-guide/concepts/collections.md)
