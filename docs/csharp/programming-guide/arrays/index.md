---
title: Matrizes – Guia de Programação em C#
description: Armazene várias variáveis do mesmo tipo em uma estrutura de dados de matriz em C#. Declare uma matriz especificando um tipo ou especifique um objeto para armazenar qualquer tipo.
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: e302ff2e4c2488c4899c4eb99a666d2d322119ce
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474729"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="e2ce5-104">Matrizes (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="e2ce5-104">Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="e2ce5-105">Você pode armazenar diversas variáveis do mesmo tipo em uma estrutura de dados de matriz.</span><span class="sxs-lookup"><span data-stu-id="e2ce5-105">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="e2ce5-106">Você pode declarar uma matriz especificando o tipo de seus elementos.</span><span class="sxs-lookup"><span data-stu-id="e2ce5-106">You declare an array by specifying the type of its elements.</span></span> <span data-ttu-id="e2ce5-107">Se você quiser que a matriz armazene elementos de qualquer tipo, você pode especificar `object` como seu tipo.</span><span class="sxs-lookup"><span data-stu-id="e2ce5-107">If you want the array to store elements of any type, you can specify `object` as its type.</span></span> <span data-ttu-id="e2ce5-108">No sistema de tipos unificado do C#, todos os tipos, predefinidos e definidos pelo usuário, tipos de referência e tipos de valor, herdam direta ou indiretamente de <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="e2ce5-108">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span>

```csharp
type[] arrayName;
```

## <a name="example"></a><span data-ttu-id="e2ce5-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e2ce5-109">Example</span></span>

<span data-ttu-id="e2ce5-110">O exemplo a seguir cria matrizes unidimensionais, multidimensionais e denteadas:</span><span class="sxs-lookup"><span data-stu-id="e2ce5-110">The following example creates single-dimensional, multidimensional, and jagged arrays:</span></span>

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a><span data-ttu-id="e2ce5-111">Visão geral da matriz</span><span class="sxs-lookup"><span data-stu-id="e2ce5-111">Array overview</span></span>

<span data-ttu-id="e2ce5-112">Uma matriz tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="e2ce5-112">An array has the following properties:</span></span>

- <span data-ttu-id="e2ce5-113">Uma matriz pode ser [Unidimensional](single-dimensional-arrays.md), [Multidimensional](multidimensional-arrays.md) ou [Denteada](jagged-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="e2ce5-113">An array can be [Single-Dimensional](single-dimensional-arrays.md), [Multidimensional](multidimensional-arrays.md) or [Jagged](jagged-arrays.md).</span></span>
- <span data-ttu-id="e2ce5-114">O número de dimensões e o tamanho de cada dimensão são estabelecidos quando a instância de matriz é criada.</span><span class="sxs-lookup"><span data-stu-id="e2ce5-114">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="e2ce5-115">Esses valores não podem ser alterados durante o ciclo de vida da instância.</span><span class="sxs-lookup"><span data-stu-id="e2ce5-115">These values can't be changed during the lifetime of the instance.</span></span>
- <span data-ttu-id="e2ce5-116">Os valores padrão dos elementos de matriz numérica são definidos como zero, e os elementos de referência são definidos como null.</span><span class="sxs-lookup"><span data-stu-id="e2ce5-116">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>
- <span data-ttu-id="e2ce5-117">Uma matriz denteada é uma matriz de matrizes e, portanto, seus elementos são tipos de referência e são inicializados para `null`.</span><span class="sxs-lookup"><span data-stu-id="e2ce5-117">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>
- <span data-ttu-id="e2ce5-118">As matrizes são indexadas por zero: uma matriz com elementos `n` é indexada de `0` para `n-1`.</span><span class="sxs-lookup"><span data-stu-id="e2ce5-118">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>
- <span data-ttu-id="e2ce5-119">Os elementos de matriz podem ser de qualquer tipo, inclusive um tipo de matriz.</span><span class="sxs-lookup"><span data-stu-id="e2ce5-119">Array elements can be of any type, including an array type.</span></span>
- <span data-ttu-id="e2ce5-120">Os tipos de matriz são [tipos de referência](../../language-reference/keywords/reference-types.md) derivados do tipo base abstrato <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="e2ce5-120">Array types are [reference types](../../language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="e2ce5-121">Como esse tipo implementa <xref:System.Collections.IEnumerable> e <xref:System.Collections.Generic.IEnumerable%601>, você pode usar a iteração [foreach](../../language-reference/keywords/foreach-in.md) em todas as matrizes em c#.</span><span class="sxs-lookup"><span data-stu-id="e2ce5-121">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>

## <a name="related-sections"></a><span data-ttu-id="e2ce5-122">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="e2ce5-122">Related sections</span></span>

- [<span data-ttu-id="e2ce5-123">Matrizes como Objetos</span><span class="sxs-lookup"><span data-stu-id="e2ce5-123">Arrays as Objects</span></span>](arrays-as-objects.md)
- [<span data-ttu-id="e2ce5-124">Usar foreach com matrizes</span><span class="sxs-lookup"><span data-stu-id="e2ce5-124">Using foreach with Arrays</span></span>](using-foreach-with-arrays.md)
- [<span data-ttu-id="e2ce5-125">Passar matrizes como argumentos</span><span class="sxs-lookup"><span data-stu-id="e2ce5-125">Passing Arrays as Arguments</span></span>](passing-arrays-as-arguments.md)

## <a name="c-language-specification"></a><span data-ttu-id="e2ce5-126">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="e2ce5-126">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="e2ce5-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2ce5-127">See also</span></span>

- [<span data-ttu-id="e2ce5-128">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="e2ce5-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e2ce5-129">Coleções</span><span class="sxs-lookup"><span data-stu-id="e2ce5-129">Collections</span></span>](../concepts/collections.md)
