---
title: "Passando matrizes com o uso de ref e out (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- arrays [C#], passing using ref and out
ms.assetid: 6a2b261e-a1cc-49a6-b4f0-6cacae385a1e
caps.latest.revision: 16
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
ms.openlocfilehash: 58fc359881295a9e6627ac1269ef17aa298009c7
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="passing-arrays-using-ref-and-out-c-programming-guide"></a><span data-ttu-id="4e6b1-102">Passando matrizes com o uso de ref e out (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="4e6b1-102">Passing Arrays Using ref and out (C# Programming Guide)</span></span>
<span data-ttu-id="4e6b1-103">Como todos os parâmetros [out](../../../csharp/language-reference/keywords/out.md), um parâmetro `out` de um tipo de matriz deve ser atribuído antes que seja usado; ou seja, deve ser atribuído pelo computador chamado.</span><span class="sxs-lookup"><span data-stu-id="4e6b1-103">Like all [out](../../../csharp/language-reference/keywords/out.md) parameters, an `out` parameter of an array type must be assigned before it is used; that is, it must be assigned by the callee.</span></span> <span data-ttu-id="4e6b1-104">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4e6b1-104">For example:</span></span>  
  
 <span data-ttu-id="4e6b1-105">[!code-cs[csProgGuideArrays#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="4e6b1-105">[!code-cs[csProgGuideArrays#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_1.cs)]</span></span>  
  
 <span data-ttu-id="4e6b1-106">Como todos os parâmetros [ref](../../../csharp/language-reference/keywords/ref.md), um parâmetro `ref` de um tipo de matriz deve ser definitivamente atribuído pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="4e6b1-106">Like all [ref](../../../csharp/language-reference/keywords/ref.md) parameters, a `ref` parameter of an array type must be definitely assigned by the caller.</span></span> <span data-ttu-id="4e6b1-107">Portanto, não há necessidade de ser atribuído definitivamente pelo receptor.</span><span class="sxs-lookup"><span data-stu-id="4e6b1-107">Therefore, there is no need to be definitely assigned by the callee.</span></span> <span data-ttu-id="4e6b1-108">Um parâmetro `ref` de um tipo de matriz pode ser alterado como resultado da chamada.</span><span class="sxs-lookup"><span data-stu-id="4e6b1-108">A `ref` parameter of an array type may be altered as a result of the call.</span></span> <span data-ttu-id="4e6b1-109">Por exemplo, o valor [nulo](../../../csharp/language-reference/keywords/null.md) pode ser atribuído à matriz ou ela pode ser inicializada em uma matriz diferente.</span><span class="sxs-lookup"><span data-stu-id="4e6b1-109">For example, the array can be assigned the [null](../../../csharp/language-reference/keywords/null.md) value or can be initialized to a different array.</span></span> <span data-ttu-id="4e6b1-110">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4e6b1-110">For example:</span></span>  
  
 <span data-ttu-id="4e6b1-111">[!code-cs[csProgGuideArrays#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="4e6b1-111">[!code-cs[csProgGuideArrays#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_2.cs)]</span></span>  
  
 <span data-ttu-id="4e6b1-112">Os dois exemplos a seguir demonstram a diferença entre `out` e `ref` quando usados ao passar matrizes para métodos.</span><span class="sxs-lookup"><span data-stu-id="4e6b1-112">The following two examples demonstrate the difference between `out` and `ref` when used in passing arrays to methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e6b1-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4e6b1-113">Example</span></span>  
 <span data-ttu-id="4e6b1-114">Neste exemplo, a matriz `theArray` é declarada no chamador (o método `Main`) e inicializada no método `FillArray`.</span><span class="sxs-lookup"><span data-stu-id="4e6b1-114">In this example, the array `theArray` is declared in the caller (the `Main` method), and initialized in the `FillArray` method.</span></span> <span data-ttu-id="4e6b1-115">Em seguida, os elementos da matriz são retornados para o chamador e exibidos.</span><span class="sxs-lookup"><span data-stu-id="4e6b1-115">Then, the array elements are returned to the caller and displayed.</span></span>  
  
 <span data-ttu-id="4e6b1-116">[!code-cs[csProgGuideArrays#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="4e6b1-116">[!code-cs[csProgGuideArrays#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_3.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e6b1-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4e6b1-117">Example</span></span>  
 <span data-ttu-id="4e6b1-118">Neste exemplo, a matriz `theArray` é inicializada no chamador (o método `Main`) e passada para o método `FillArray` ao usar o parâmetro `ref`.</span><span class="sxs-lookup"><span data-stu-id="4e6b1-118">In this example, the array `theArray` is initialized in the caller (the `Main` method), and passed to the `FillArray` method by using the `ref` parameter.</span></span> <span data-ttu-id="4e6b1-119">Alguns elementos da matriz são atualizados no método `FillArray`.</span><span class="sxs-lookup"><span data-stu-id="4e6b1-119">Some of the array elements are updated in the `FillArray` method.</span></span> <span data-ttu-id="4e6b1-120">Em seguida, os elementos da matriz são retornados para o chamador e exibidos.</span><span class="sxs-lookup"><span data-stu-id="4e6b1-120">Then, the array elements are returned to the caller and displayed.</span></span>  
  
 <span data-ttu-id="4e6b1-121">[!code-cs[csProgGuideArrays#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="4e6b1-121">[!code-cs[csProgGuideArrays#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_4.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e6b1-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4e6b1-122">See Also</span></span>  
 <span data-ttu-id="4e6b1-123">[ref](../../../csharp/language-reference/keywords/ref.md) </span><span class="sxs-lookup"><span data-stu-id="4e6b1-123">[ref](../../../csharp/language-reference/keywords/ref.md) </span></span>  
 <span data-ttu-id="4e6b1-124">[Modificador de parâmetro out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) </span><span class="sxs-lookup"><span data-stu-id="4e6b1-124">[out parameter modifier](../../../csharp/language-reference/keywords/out-parameter-modifier.md) </span></span>  
 <span data-ttu-id="4e6b1-125">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="4e6b1-125">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="4e6b1-126">[Matrizes](../../../csharp/programming-guide/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="4e6b1-126">[Arrays](../../../csharp/programming-guide/arrays/index.md) </span></span>  
 <span data-ttu-id="4e6b1-127">[Matrizes Unidimensionais](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="4e6b1-127">[Single-Dimensional Arrays](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md) </span></span>  
 <span data-ttu-id="4e6b1-128">[Matrizes Multidimensionais](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="4e6b1-128">[Multidimensional Arrays](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) </span></span>  
 [<span data-ttu-id="4e6b1-129">Matrizes denteadas</span><span class="sxs-lookup"><span data-stu-id="4e6b1-129">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)

