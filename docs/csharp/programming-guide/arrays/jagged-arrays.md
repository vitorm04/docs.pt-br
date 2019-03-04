---
title: Matrizes denteadas – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: 9fc05c8bdebf9c1c6b613db0b6a121e06765ac00
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200670"
---
# <a name="jagged-arrays-c-programming-guide"></a><span data-ttu-id="5787f-102">Matrizes denteadas (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="5787f-102">Jagged Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="5787f-103">Uma matriz denteada é uma matriz cujos elementos são matrizes.</span><span class="sxs-lookup"><span data-stu-id="5787f-103">A jagged array is an array whose elements are arrays.</span></span> <span data-ttu-id="5787f-104">Os elementos de uma matriz denteada podem ter diferentes dimensões e tamanhos.</span><span class="sxs-lookup"><span data-stu-id="5787f-104">The elements of a jagged array can be of different dimensions and sizes.</span></span> <span data-ttu-id="5787f-105">Às vezes, uma matriz denteada é chamada de uma "matriz de matrizes."</span><span class="sxs-lookup"><span data-stu-id="5787f-105">A jagged array is sometimes called an "array of arrays."</span></span> <span data-ttu-id="5787f-106">Os exemplos a seguir mostram como declarar, inicializar e acessar matrizes denteadas.</span><span class="sxs-lookup"><span data-stu-id="5787f-106">The following examples show how to declare, initialize, and access jagged arrays.</span></span>  
  
 <span data-ttu-id="5787f-107">A seguir, há uma declaração de uma matriz unidimensional que tem três elementos, cada um do qual é uma matriz de dimensão única de inteiros:</span><span class="sxs-lookup"><span data-stu-id="5787f-107">The following is a declaration of a single-dimensional array that has three elements, each of which is a single-dimensional array of integers:</span></span>  
  
 [!code-csharp[csProgGuideArrays#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#19)]  
  
 <span data-ttu-id="5787f-108">Antes de usar `jaggedArray`, seus elementos devem ser inicializados.</span><span class="sxs-lookup"><span data-stu-id="5787f-108">Before you can use `jaggedArray`, its elements must be initialized.</span></span> <span data-ttu-id="5787f-109">É possível inicializar os elementos dessa forma:</span><span class="sxs-lookup"><span data-stu-id="5787f-109">You can initialize the elements like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#20)]  
  
 <span data-ttu-id="5787f-110">Cada um dos elementos é uma matriz unidimensional de inteiros.</span><span class="sxs-lookup"><span data-stu-id="5787f-110">Each of the elements is a single-dimensional array of integers.</span></span> <span data-ttu-id="5787f-111">O primeiro elemento é uma matriz de 5 inteiros, o segundo é uma matriz de 4 inteiros e o terceiro é uma matriz de 2 inteiros.</span><span class="sxs-lookup"><span data-stu-id="5787f-111">The first element is an array of 5 integers, the second is an array of 4 integers, and the third is an array of 2 integers.</span></span>  
  
 <span data-ttu-id="5787f-112">Também é possível usar os inicializadores para preencher os elementos matriz com valores, caso em que não é necessário o tamanho da matriz.</span><span class="sxs-lookup"><span data-stu-id="5787f-112">It is also possible to use initializers to fill the array elements with values, in which case you do not need the array size.</span></span> <span data-ttu-id="5787f-113">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="5787f-113">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#21)]  
  
 <span data-ttu-id="5787f-114">Também é possível inicializar a matriz mediante uma declaração como esta:</span><span class="sxs-lookup"><span data-stu-id="5787f-114">You can also initialize the array upon declaration like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#22)]  
  
 <span data-ttu-id="5787f-115">É possível usar a seguinte forma abreviada.</span><span class="sxs-lookup"><span data-stu-id="5787f-115">You can use the following shorthand form.</span></span> <span data-ttu-id="5787f-116">Observe que não é possível omitir o operador `new` da inicialização de elementos, porque não há nenhuma inicialização padrão para os elementos:</span><span class="sxs-lookup"><span data-stu-id="5787f-116">Notice that you cannot omit the `new` operator from the elements initialization because there is no default initialization for the elements:</span></span>  
  
 [!code-csharp[csProgGuideArrays#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#23)]  
  
 <span data-ttu-id="5787f-117">Uma matriz denteada é uma matriz de matrizes e, portanto, seus elementos são tipos de referência e são inicializados para `null`.</span><span class="sxs-lookup"><span data-stu-id="5787f-117">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
 <span data-ttu-id="5787f-118">É possível acessar elementos de matrizes individuais como estes exemplos:</span><span class="sxs-lookup"><span data-stu-id="5787f-118">You can access individual array elements like these examples:</span></span>  
  
 [!code-csharp[csProgGuideArrays#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#24)]  
  
 <span data-ttu-id="5787f-119">É possível misturar matrizes denteadas e multidimensionais.</span><span class="sxs-lookup"><span data-stu-id="5787f-119">It is possible to mix jagged and multidimensional arrays.</span></span> <span data-ttu-id="5787f-120">A seguir, há uma declaração e inicialização de uma matriz denteada unidimensional que contém três elementos de matriz bidimensional de tamanhos diferentes.</span><span class="sxs-lookup"><span data-stu-id="5787f-120">The following is a declaration and initialization of a single-dimensional jagged array that contains three two-dimensional array elements of different sizes.</span></span> <span data-ttu-id="5787f-121">Para obter mais informações sobre matrizes bidimensionais, consulte [Matrizes Multidimensionais](../../../csharp/programming-guide/arrays/multidimensional-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="5787f-121">For more information about two-dimensional arrays, see [Multidimensional Arrays](../../../csharp/programming-guide/arrays/multidimensional-arrays.md).</span></span>  
  
 [!code-csharp[csProgGuideArrays#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#25)]  
  
 <span data-ttu-id="5787f-122">É possível acessar elementos individuais conforme mostrado neste exemplo, que exibe o valor do elemento `[1,0]` da primeira matriz (valor `5`):</span><span class="sxs-lookup"><span data-stu-id="5787f-122">You can access individual elements as shown in this example, which displays the value of the element `[1,0]` of the first array (value `5`):</span></span>  
  
 [!code-csharp[csProgGuideArrays#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#26)]  
  
 <span data-ttu-id="5787f-123">O método `Length` retorna inúmeros conjuntos contidos na matriz denteada.</span><span class="sxs-lookup"><span data-stu-id="5787f-123">The method `Length` returns the number of arrays contained in the jagged array.</span></span> <span data-ttu-id="5787f-124">Por exemplo, supondo que você tenha declarado a matriz anterior, esta linha:</span><span class="sxs-lookup"><span data-stu-id="5787f-124">For example, assuming you have declared the previous array, this line:</span></span>  
  
 [!code-csharp[csProgGuideArrays#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#27)]  
  
 <span data-ttu-id="5787f-125">retorna um valor de 3.</span><span class="sxs-lookup"><span data-stu-id="5787f-125">returns a value of 3.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5787f-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5787f-126">Example</span></span>

 <span data-ttu-id="5787f-127">Este exemplo cria uma matriz cujos elementos são matrizes.</span><span class="sxs-lookup"><span data-stu-id="5787f-127">This example builds an array whose elements are themselves arrays.</span></span> <span data-ttu-id="5787f-128">Cada um dos elementos da matriz tem um tamanho diferente.</span><span class="sxs-lookup"><span data-stu-id="5787f-128">Each one of the array elements has a different size.</span></span>  
  
 [!code-csharp[csProgGuideArrays#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#18)]  
  
## <a name="see-also"></a><span data-ttu-id="5787f-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5787f-129">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="5787f-130">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="5787f-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="5787f-131">Matrizes</span><span class="sxs-lookup"><span data-stu-id="5787f-131">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)
- [<span data-ttu-id="5787f-132">Matrizes unidimensionais</span><span class="sxs-lookup"><span data-stu-id="5787f-132">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)
- [<span data-ttu-id="5787f-133">Matrizes multidimensionais</span><span class="sxs-lookup"><span data-stu-id="5787f-133">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
