---
title: Matrizes unidimensionais – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: 17c384ec327d4a80ed614dce6254baa5bfb2e960
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597301"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a><span data-ttu-id="2b1ab-102">Matrizes unidimensionais (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="2b1ab-102">Single-Dimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="2b1ab-103">É possível declarar uma matriz unidimensional de cinco inteiros, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="2b1ab-103">You can declare a single-dimensional array of five integers as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#4)]  
  
 <span data-ttu-id="2b1ab-104">Essa matriz contém os elementos de `array[0]` a `array[4]`.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-104">This array contains the elements from `array[0]` to `array[4]`.</span></span> <span data-ttu-id="2b1ab-105">O operador [new](../../language-reference/operators/new-operator.md) é usado para criar a matriz e inicializar os elementos da matriz para seus valores padrão.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-105">The [new](../../language-reference/operators/new-operator.md) operator is used to create the array and initialize the array elements to their default values.</span></span> <span data-ttu-id="2b1ab-106">Neste exemplo, todos os elementos da matriz são inicializados em zero.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-106">In this example, all the array elements are initialized to zero.</span></span>  
  
 <span data-ttu-id="2b1ab-107">Uma matriz que armazena os elementos da cadeia de caracteres pode ser declarada da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-107">An array that stores string elements can be declared in the same way.</span></span> <span data-ttu-id="2b1ab-108">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="2b1ab-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#5)]  
  
## <a name="array-initialization"></a><span data-ttu-id="2b1ab-109">Inicialização de Matriz</span><span class="sxs-lookup"><span data-stu-id="2b1ab-109">Array Initialization</span></span>

 <span data-ttu-id="2b1ab-110">É possível inicializar uma matriz na declaração. Nesse caso, o especificador de comprimento não é necessário porque ele já é fornecido pelo número de elementos na lista de inicialização.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-110">It is possible to initialize an array upon declaration, in which case, the length specifier is not needed because it is already supplied by the number of elements in the initialization list.</span></span> <span data-ttu-id="2b1ab-111">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="2b1ab-111">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#6)]  
  
 <span data-ttu-id="2b1ab-112">Uma matriz de cadeia de caracteres pode ser inicializada da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-112">A string array can be initialized in the same way.</span></span> <span data-ttu-id="2b1ab-113">A seguir, há uma declaração de uma matriz de cadeia de caracteres em que cada elemento da matriz é inicializado por um nome de um dia:</span><span class="sxs-lookup"><span data-stu-id="2b1ab-113">The following is a declaration of a string array where each array element is initialized by a name of a day:</span></span>  
 
 ```csharp
 string[] weekDays = new string[] { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
 ```
  
 <span data-ttu-id="2b1ab-114">Quando você inicializa uma matriz na declaração, é possível usar os seguintes atalhos:</span><span class="sxs-lookup"><span data-stu-id="2b1ab-114">When you initialize an array upon declaration, you can use the following shortcuts:</span></span>  
  
 [!code-csharp[csProgGuideArrays#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#8)]  
  
 <span data-ttu-id="2b1ab-115">É possível declarar uma variável de matriz sem inicialização, mas é necessário usar o operador `new` quando você atribui uma matriz a essa variável.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-115">It is possible to declare an array variable without initialization, but you must use the `new` operator when you assign an array to this variable.</span></span> <span data-ttu-id="2b1ab-116">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="2b1ab-116">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#9)]  
  
 <span data-ttu-id="2b1ab-117">O C# 3.0 introduz matrizes de tipo implícito.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-117">C# 3.0 introduces implicitly typed arrays.</span></span> <span data-ttu-id="2b1ab-118">Para obter mais informações, consulte [Matrizes de tipo implícito](./implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="2b1ab-118">For more information, see [Implicitly Typed Arrays](./implicitly-typed-arrays.md).</span></span>  
  
## <a name="value-type-and-reference-type-arrays"></a><span data-ttu-id="2b1ab-119">Matrizes de tipo de valor e de tipo de referência</span><span class="sxs-lookup"><span data-stu-id="2b1ab-119">Value Type and Reference Type Arrays</span></span>

 <span data-ttu-id="2b1ab-120">Considere a seguinte declaração de matriz:</span><span class="sxs-lookup"><span data-stu-id="2b1ab-120">Consider the following array declaration:</span></span>  
  
 [!code-csharp[csProgGuideArrays#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#10)]  
  
 <span data-ttu-id="2b1ab-121">O resultado dessa instrução depende se `SomeType` é um tipo de valor ou um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-121">The result of this statement depends on whether `SomeType` is a value type or a reference type.</span></span> <span data-ttu-id="2b1ab-122">Se for um tipo de valor, a instrução criará uma matriz de 10 elementos, cada um deles tem o tipo `SomeType`.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-122">If it is a value type, the statement creates an array of 10 elements, each of which has the type `SomeType`.</span></span> <span data-ttu-id="2b1ab-123">Se `SomeType` for um tipo de referência, a instrução criará uma matriz de 10 elementos, cada um deles é inicializado com uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-123">If `SomeType` is a reference type, the statement creates an array of 10 elements, each of which is initialized to a null reference.</span></span>  
  
 <span data-ttu-id="2b1ab-124">Para obter mais informações sobre tipos de valor e de referência, consulte [Tipos](../../language-reference/keywords/types.md).</span><span class="sxs-lookup"><span data-stu-id="2b1ab-124">For more information about value types and reference types, see [Types](../../language-reference/keywords/types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b1ab-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b1ab-125">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="2b1ab-126">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="2b1ab-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2b1ab-127">Matrizes</span><span class="sxs-lookup"><span data-stu-id="2b1ab-127">Arrays</span></span>](./index.md)
- [<span data-ttu-id="2b1ab-128">Matrizes multidimensionais</span><span class="sxs-lookup"><span data-stu-id="2b1ab-128">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="2b1ab-129">Matrizes denteadas</span><span class="sxs-lookup"><span data-stu-id="2b1ab-129">Jagged Arrays</span></span>](./jagged-arrays.md)
