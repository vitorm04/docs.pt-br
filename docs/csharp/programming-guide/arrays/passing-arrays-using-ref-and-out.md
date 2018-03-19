---
title: "Passando matrizes com o uso de ref e out (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], passing using ref and out
ms.assetid: 6a2b261e-a1cc-49a6-b4f0-6cacae385a1e
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f76f63aee0100c6af6bde73c8543b4e7136b1954
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="passing-arrays-using-ref-and-out-c-programming-guide"></a><span data-ttu-id="c3c35-102">Passando matrizes com o uso de ref e out (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="c3c35-102">Passing Arrays Using ref and out (C# Programming Guide)</span></span>
<span data-ttu-id="c3c35-103">Como todos os parâmetros [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), um parâmetro `out` de um tipo de matriz deve ser atribuído antes que seja usado; ou seja, deve ser atribuído pelo computador chamado.</span><span class="sxs-lookup"><span data-stu-id="c3c35-103">Like all [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters, an `out` parameter of an array type must be assigned before it is used; that is, it must be assigned by the callee.</span></span> <span data-ttu-id="c3c35-104">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c3c35-104">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_1.cs)]  
  
 <span data-ttu-id="c3c35-105">Como todos os parâmetros [ref](../../../csharp/language-reference/keywords/ref.md), um parâmetro `ref` de um tipo de matriz deve ser definitivamente atribuído pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="c3c35-105">Like all [ref](../../../csharp/language-reference/keywords/ref.md) parameters, a `ref` parameter of an array type must be definitely assigned by the caller.</span></span> <span data-ttu-id="c3c35-106">Portanto, não há necessidade de ser atribuído definitivamente pelo receptor.</span><span class="sxs-lookup"><span data-stu-id="c3c35-106">Therefore, there is no need to be definitely assigned by the callee.</span></span> <span data-ttu-id="c3c35-107">Um parâmetro `ref` de um tipo de matriz pode ser alterado como resultado da chamada.</span><span class="sxs-lookup"><span data-stu-id="c3c35-107">A `ref` parameter of an array type may be altered as a result of the call.</span></span> <span data-ttu-id="c3c35-108">Por exemplo, o valor [nulo](../../../csharp/language-reference/keywords/null.md) pode ser atribuído à matriz ou ela pode ser inicializada em uma matriz diferente.</span><span class="sxs-lookup"><span data-stu-id="c3c35-108">For example, the array can be assigned the [null](../../../csharp/language-reference/keywords/null.md) value or can be initialized to a different array.</span></span> <span data-ttu-id="c3c35-109">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c3c35-109">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_2.cs)]  
  
 <span data-ttu-id="c3c35-110">Os dois exemplos a seguir demonstram a diferença entre `out` e `ref` quando usados ao passar matrizes para métodos.</span><span class="sxs-lookup"><span data-stu-id="c3c35-110">The following two examples demonstrate the difference between `out` and `ref` when used in passing arrays to methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3c35-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c3c35-111">Example</span></span>  
 <span data-ttu-id="c3c35-112">Neste exemplo, a matriz `theArray` é declarada no chamador (o método `Main`) e inicializada no método `FillArray`.</span><span class="sxs-lookup"><span data-stu-id="c3c35-112">In this example, the array `theArray` is declared in the caller (the `Main` method), and initialized in the `FillArray` method.</span></span> <span data-ttu-id="c3c35-113">Em seguida, os elementos da matriz são retornados para o chamador e exibidos.</span><span class="sxs-lookup"><span data-stu-id="c3c35-113">Then, the array elements are returned to the caller and displayed.</span></span>  
  
 [!code-csharp[csProgGuideArrays#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="c3c35-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c3c35-114">Example</span></span>  
 <span data-ttu-id="c3c35-115">Neste exemplo, a matriz `theArray` é inicializada no chamador (o método `Main`) e passada para o método `FillArray` ao usar o parâmetro `ref`.</span><span class="sxs-lookup"><span data-stu-id="c3c35-115">In this example, the array `theArray` is initialized in the caller (the `Main` method), and passed to the `FillArray` method by using the `ref` parameter.</span></span> <span data-ttu-id="c3c35-116">Alguns elementos da matriz são atualizados no método `FillArray`.</span><span class="sxs-lookup"><span data-stu-id="c3c35-116">Some of the array elements are updated in the `FillArray` method.</span></span> <span data-ttu-id="c3c35-117">Em seguida, os elementos da matriz são retornados para o chamador e exibidos.</span><span class="sxs-lookup"><span data-stu-id="c3c35-117">Then, the array elements are returned to the caller and displayed.</span></span>  
  
 [!code-csharp[csProgGuideArrays#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_4.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c3c35-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3c35-118">See Also</span></span>  
 [<span data-ttu-id="c3c35-119">ref</span><span class="sxs-lookup"><span data-stu-id="c3c35-119">ref</span></span>](../../../csharp/language-reference/keywords/ref.md)  
 [<span data-ttu-id="c3c35-120">Modificador de parâmetro out</span><span class="sxs-lookup"><span data-stu-id="c3c35-120">out parameter modifier</span></span>](../../../csharp/language-reference/keywords/out-parameter-modifier.md)  
 [<span data-ttu-id="c3c35-121">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="c3c35-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c3c35-122">Matrizes</span><span class="sxs-lookup"><span data-stu-id="c3c35-122">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="c3c35-123">Matrizes unidimensionais</span><span class="sxs-lookup"><span data-stu-id="c3c35-123">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="c3c35-124">Matrizes multidimensionais</span><span class="sxs-lookup"><span data-stu-id="c3c35-124">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="c3c35-125">Matrizes denteadas</span><span class="sxs-lookup"><span data-stu-id="c3c35-125">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
