---
title: "Matrizes unidimensionais (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: cc42640715274b89c4c4a12ced8c0ae6af603318
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="single-dimensional-arrays-c-programming-guide"></a><span data-ttu-id="a36c8-102">Matrizes unidimensionais (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="a36c8-102">Single-Dimensional Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="a36c8-103">É possível declarar uma matriz unidimensional de cinco inteiros, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="a36c8-103">You can declare a single-dimensional array of five integers as shown in the following example:</span></span>  
  
 <span data-ttu-id="a36c8-104">[!code-cs[csProgGuideArrays#4](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="a36c8-104">[!code-cs[csProgGuideArrays#4](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_1.cs)]</span></span>  
  
 <span data-ttu-id="a36c8-105">Essa matriz contém os elementos de `array[0]` a `array[4]`.</span><span class="sxs-lookup"><span data-stu-id="a36c8-105">This array contains the elements from `array[0]` to `array[4]`.</span></span> <span data-ttu-id="a36c8-106">O operador [new](../../../csharp/language-reference/keywords/new.md) é usado para criar a matriz e inicializar os elementos da matriz para seus valores padrão.</span><span class="sxs-lookup"><span data-stu-id="a36c8-106">The [new](../../../csharp/language-reference/keywords/new.md) operator is used to create the array and initialize the array elements to their default values.</span></span> <span data-ttu-id="a36c8-107">Neste exemplo, todos os elementos da matriz são inicializados em zero.</span><span class="sxs-lookup"><span data-stu-id="a36c8-107">In this example, all the array elements are initialized to zero.</span></span>  
  
 <span data-ttu-id="a36c8-108">Uma matriz que armazena os elementos da cadeia de caracteres pode ser declarada da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="a36c8-108">An array that stores string elements can be declared in the same way.</span></span> <span data-ttu-id="a36c8-109">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a36c8-109">For example:</span></span>  
  
 <span data-ttu-id="a36c8-110">[!code-cs[csProgGuideArrays#5](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="a36c8-110">[!code-cs[csProgGuideArrays#5](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_2.cs)]</span></span>  
  
## <a name="array-initialization"></a><span data-ttu-id="a36c8-111">Inicialização de Matriz</span><span class="sxs-lookup"><span data-stu-id="a36c8-111">Array Initialization</span></span>  
 <span data-ttu-id="a36c8-112">É possível inicializar uma matriz na declaração. Nesse caso, o especificador de classificação não é necessário, porque ele já é fornecido pelo número de elementos na lista de inicialização.</span><span class="sxs-lookup"><span data-stu-id="a36c8-112">It is possible to initialize an array upon declaration, in which case, the rank specifier is not needed because it is already supplied by the number of elements in the initialization list.</span></span> <span data-ttu-id="a36c8-113">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a36c8-113">For example:</span></span>  
  
 <span data-ttu-id="a36c8-114">[!code-cs[csProgGuideArrays#6](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="a36c8-114">[!code-cs[csProgGuideArrays#6](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_3.cs)]</span></span>  
  
 <span data-ttu-id="a36c8-115">Uma matriz de cadeia de caracteres pode ser inicializada da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="a36c8-115">A string array can be initialized in the same way.</span></span> <span data-ttu-id="a36c8-116">A seguir, há uma declaração de uma matriz de cadeia de caracteres em que cada elemento da matriz é inicializado por um nome de um dia:</span><span class="sxs-lookup"><span data-stu-id="a36c8-116">The following is a declaration of a string array where each array element is initialized by a name of a day:</span></span>  
  
 <span data-ttu-id="a36c8-117">[!code-cs[csProgGuideArrays#7](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="a36c8-117">[!code-cs[csProgGuideArrays#7](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_4.cs)]</span></span>  
  
 <span data-ttu-id="a36c8-118">Quando você inicializa uma matriz na declaração, é possível usar os seguintes atalhos:</span><span class="sxs-lookup"><span data-stu-id="a36c8-118">When you initialize an array upon declaration, you can use the following shortcuts:</span></span>  
  
 <span data-ttu-id="a36c8-119">[!code-cs[csProgGuideArrays#8](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="a36c8-119">[!code-cs[csProgGuideArrays#8](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_5.cs)]</span></span>  
  
 <span data-ttu-id="a36c8-120">É possível declarar uma variável de matriz sem inicialização, mas é necessário usar o operador `new` quando você atribui uma matriz a essa variável.</span><span class="sxs-lookup"><span data-stu-id="a36c8-120">It is possible to declare an array variable without initialization, but you must use the `new` operator when you assign an array to this variable.</span></span> <span data-ttu-id="a36c8-121">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a36c8-121">For example:</span></span>  
  
 <span data-ttu-id="a36c8-122">[!code-cs[csProgGuideArrays#9](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="a36c8-122">[!code-cs[csProgGuideArrays#9](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_6.cs)]</span></span>  
  
 <span data-ttu-id="a36c8-123">O C# 3.0 introduz matrizes de tipo implícito.</span><span class="sxs-lookup"><span data-stu-id="a36c8-123">C# 3.0 introduces implicitly typed arrays.</span></span> <span data-ttu-id="a36c8-124">Para obter mais informações, consulte [Matrizes de tipo implícito](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="a36c8-124">For more information, see [Implicitly Typed Arrays](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span></span>  
  
## <a name="value-type-and-reference-type-arrays"></a><span data-ttu-id="a36c8-125">Matrizes de tipo de valor e de tipo de referência</span><span class="sxs-lookup"><span data-stu-id="a36c8-125">Value Type and Reference Type Arrays</span></span>  
 <span data-ttu-id="a36c8-126">Considere a seguinte declaração de matriz:</span><span class="sxs-lookup"><span data-stu-id="a36c8-126">Consider the following array declaration:</span></span>  
  
 <span data-ttu-id="a36c8-127">[!code-cs[csProgGuideArrays#10](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="a36c8-127">[!code-cs[csProgGuideArrays#10](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_7.cs)]</span></span>  
  
 <span data-ttu-id="a36c8-128">O resultado dessa instrução depende se `SomeType` é um tipo de valor ou um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="a36c8-128">The result of this statement depends on whether `SomeType` is a value type or a reference type.</span></span> <span data-ttu-id="a36c8-129">Se for um tipo de valor, a instrução criará uma matriz de 10 elementos, cada um deles tem o tipo `SomeType`.</span><span class="sxs-lookup"><span data-stu-id="a36c8-129">If it is a value type, the statement creates an array of 10 elements, each of which has the type `SomeType`.</span></span> <span data-ttu-id="a36c8-130">Se `SomeType` for um tipo de referência, a instrução criará uma matriz de 10 elementos, cada um deles é inicializado com uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="a36c8-130">If `SomeType` is a reference type, the statement creates an array of 10 elements, each of which is initialized to a null reference.</span></span>  
  
 <span data-ttu-id="a36c8-131">Para obter mais informações sobre tipos de valor e de referência, consulte [Tipos](../../../csharp/language-reference/keywords/types.md).</span><span class="sxs-lookup"><span data-stu-id="a36c8-131">For more information about value types and reference types, see [Types](../../../csharp/language-reference/keywords/types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a36c8-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a36c8-132">See Also</span></span>  
 <span data-ttu-id="a36c8-133"><xref:System.Array></span><span class="sxs-lookup"><span data-stu-id="a36c8-133"><xref:System.Array></span></span>   
 <span data-ttu-id="a36c8-134">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="a36c8-134">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="a36c8-135">[Matrizes](../../../csharp/programming-guide/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="a36c8-135">[Arrays](../../../csharp/programming-guide/arrays/index.md) </span></span>  
 <span data-ttu-id="a36c8-136">[Matrizes Multidimensionais](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="a36c8-136">[Multidimensional Arrays](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) </span></span>  
 [<span data-ttu-id="a36c8-137">Matrizes denteadas</span><span class="sxs-lookup"><span data-stu-id="a36c8-137">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)

