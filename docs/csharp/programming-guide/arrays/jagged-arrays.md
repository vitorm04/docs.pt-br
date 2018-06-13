---
title: Matrizes denteadas (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: c1825e1a731c40a5945060f8085bd612b5d62008
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33297362"
---
# <a name="jagged-arrays-c-programming-guide"></a><span data-ttu-id="016d0-102">Matrizes denteadas (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="016d0-102">Jagged Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="016d0-103">Uma matriz denteada é uma matriz cujos elementos são matrizes.</span><span class="sxs-lookup"><span data-stu-id="016d0-103">A jagged array is an array whose elements are arrays.</span></span> <span data-ttu-id="016d0-104">Os elementos de uma matriz denteada podem ter diferentes dimensões e tamanhos.</span><span class="sxs-lookup"><span data-stu-id="016d0-104">The elements of a jagged array can be of different dimensions and sizes.</span></span> <span data-ttu-id="016d0-105">Às vezes, uma matriz denteada é chamada de uma "matriz de matrizes."</span><span class="sxs-lookup"><span data-stu-id="016d0-105">A jagged array is sometimes called an "array of arrays."</span></span> <span data-ttu-id="016d0-106">Os exemplos a seguir mostram como declarar, inicializar e acessar matrizes denteadas.</span><span class="sxs-lookup"><span data-stu-id="016d0-106">The following examples show how to declare, initialize, and access jagged arrays.</span></span>  
  
 <span data-ttu-id="016d0-107">A seguir, há uma declaração de uma matriz unidimensional que tem três elementos, cada um do qual é uma matriz de dimensão única de inteiros:</span><span class="sxs-lookup"><span data-stu-id="016d0-107">The following is a declaration of a single-dimensional array that has three elements, each of which is a single-dimensional array of integers:</span></span>  
  
 [!code-csharp[csProgGuideArrays#19](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_1.cs)]  
  
 <span data-ttu-id="016d0-108">Antes de usar `jaggedArray`, seus elementos devem ser inicializados.</span><span class="sxs-lookup"><span data-stu-id="016d0-108">Before you can use `jaggedArray`, its elements must be initialized.</span></span> <span data-ttu-id="016d0-109">É possível inicializar os elementos dessa forma:</span><span class="sxs-lookup"><span data-stu-id="016d0-109">You can initialize the elements like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#20](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_2.cs)]  
  
 <span data-ttu-id="016d0-110">Cada um dos elementos é uma matriz unidimensional de inteiros.</span><span class="sxs-lookup"><span data-stu-id="016d0-110">Each of the elements is a single-dimensional array of integers.</span></span> <span data-ttu-id="016d0-111">O primeiro elemento é uma matriz de 5 inteiros, o segundo é uma matriz de 4 inteiros e o terceiro é uma matriz de 2 inteiros.</span><span class="sxs-lookup"><span data-stu-id="016d0-111">The first element is an array of 5 integers, the second is an array of 4 integers, and the third is an array of 2 integers.</span></span>  
  
 <span data-ttu-id="016d0-112">Também é possível usar os inicializadores para preencher os elementos matriz com valores, caso em que não é necessário o tamanho da matriz.</span><span class="sxs-lookup"><span data-stu-id="016d0-112">It is also possible to use initializers to fill the array elements with values, in which case you do not need the array size.</span></span> <span data-ttu-id="016d0-113">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="016d0-113">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#21](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_3.cs)]  
  
 <span data-ttu-id="016d0-114">Também é possível inicializar a matriz mediante uma declaração como esta:</span><span class="sxs-lookup"><span data-stu-id="016d0-114">You can also initialize the array upon declaration like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#22](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_4.cs)]  
  
 <span data-ttu-id="016d0-115">É possível usar a seguinte forma abreviada.</span><span class="sxs-lookup"><span data-stu-id="016d0-115">You can use the following shorthand form.</span></span> <span data-ttu-id="016d0-116">Observe que não é possível omitir o operador `new` da inicialização de elementos, porque não há nenhuma inicialização padrão para os elementos:</span><span class="sxs-lookup"><span data-stu-id="016d0-116">Notice that you cannot omit the `new` operator from the elements initialization because there is no default initialization for the elements:</span></span>  
  
 [!code-csharp[csProgGuideArrays#23](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_5.cs)]  
  
 <span data-ttu-id="016d0-117">Uma matriz denteada é uma matriz de matrizes e, portanto, seus elementos são tipos de referência e são inicializados para `null`.</span><span class="sxs-lookup"><span data-stu-id="016d0-117">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
 <span data-ttu-id="016d0-118">É possível acessar elementos de matrizes individuais como estes exemplos:</span><span class="sxs-lookup"><span data-stu-id="016d0-118">You can access individual array elements like these examples:</span></span>  
  
 [!code-csharp[csProgGuideArrays#24](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_6.cs)]  
  
 <span data-ttu-id="016d0-119">É possível misturar matrizes denteadas e multidimensionais.</span><span class="sxs-lookup"><span data-stu-id="016d0-119">It is possible to mix jagged and multidimensional arrays.</span></span> <span data-ttu-id="016d0-120">A seguir, há uma declaração e inicialização de uma matriz denteada unidimensional que contém três elementos de matriz bidimensional de tamanhos diferentes.</span><span class="sxs-lookup"><span data-stu-id="016d0-120">The following is a declaration and initialization of a single-dimensional jagged array that contains three two-dimensional array elements of different sizes.</span></span> <span data-ttu-id="016d0-121">Para obter mais informações sobre matrizes bidimensionais, consulte [Matrizes Multidimensionais](../../../csharp/programming-guide/arrays/multidimensional-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="016d0-121">For more information about two-dimensional arrays, see [Multidimensional Arrays](../../../csharp/programming-guide/arrays/multidimensional-arrays.md).</span></span>  
  
 [!code-csharp[csProgGuideArrays#25](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_7.cs)]  
  
 <span data-ttu-id="016d0-122">É possível acessar elementos individuais conforme mostrado neste exemplo, que exibe o valor do elemento `[1,0]` da primeira matriz (valor `5`):</span><span class="sxs-lookup"><span data-stu-id="016d0-122">You can access individual elements as shown in this example, which displays the value of the element `[1,0]` of the first array (value `5`):</span></span>  
  
 [!code-csharp[csProgGuideArrays#26](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_8.cs)]  
  
 <span data-ttu-id="016d0-123">O método `Length` retorna inúmeros conjuntos contidos na matriz denteada.</span><span class="sxs-lookup"><span data-stu-id="016d0-123">The method `Length` returns the number of arrays contained in the jagged array.</span></span> <span data-ttu-id="016d0-124">Por exemplo, supondo que você tenha declarado a matriz anterior, esta linha:</span><span class="sxs-lookup"><span data-stu-id="016d0-124">For example, assuming you have declared the previous array, this line:</span></span>  
  
 [!code-csharp[csProgGuideArrays#27](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_9.cs)]  
  
 <span data-ttu-id="016d0-125">retorna um valor de 3.</span><span class="sxs-lookup"><span data-stu-id="016d0-125">returns a value of 3.</span></span>  
  
## <a name="example"></a><span data-ttu-id="016d0-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="016d0-126">Example</span></span>  
 <span data-ttu-id="016d0-127">Este exemplo cria uma matriz cujos elementos são matrizes.</span><span class="sxs-lookup"><span data-stu-id="016d0-127">This example builds an array whose elements are themselves arrays.</span></span> <span data-ttu-id="016d0-128">Cada um dos elementos da matriz tem um tamanho diferente.</span><span class="sxs-lookup"><span data-stu-id="016d0-128">Each one of the array elements has a different size.</span></span>  
  
 [!code-csharp[csProgGuideArrays#18](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_10.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="016d0-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="016d0-129">See Also</span></span>  
 <xref:System.Array>  
 [<span data-ttu-id="016d0-130">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="016d0-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="016d0-131">Matrizes</span><span class="sxs-lookup"><span data-stu-id="016d0-131">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="016d0-132">Matrizes unidimensionais</span><span class="sxs-lookup"><span data-stu-id="016d0-132">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="016d0-133">Matrizes multidimensionais</span><span class="sxs-lookup"><span data-stu-id="016d0-133">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
