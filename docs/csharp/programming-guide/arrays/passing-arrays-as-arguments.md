---
title: "Passando matrizes como argumentos (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
caps.latest.revision: 21
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
ms.openlocfilehash: 5e83c0c119bc1448be76f83416098158c7f5d684
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a><span data-ttu-id="958a3-102">Passando matrizes como argumentos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="958a3-102">Passing Arrays as Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="958a3-103">As matrizes podem ser passadas como argumentos para parâmetros de método.</span><span class="sxs-lookup"><span data-stu-id="958a3-103">Arrays can be passed as arguments to method parameters.</span></span> <span data-ttu-id="958a3-104">Como matrizes são tipos de referência, o método pode alterar o valor dos elementos.</span><span class="sxs-lookup"><span data-stu-id="958a3-104">Because arrays are reference types, the method can change the value of the elements.</span></span>  
  
## <a name="passing-single-dimensional-arrays-as-arguments"></a><span data-ttu-id="958a3-105">Passando matrizes unidimensionais como argumentos</span><span class="sxs-lookup"><span data-stu-id="958a3-105">Passing Single-Dimensional Arrays As Arguments</span></span>  
 <span data-ttu-id="958a3-106">É possível passar uma matriz unidimensional inicializada para um método.</span><span class="sxs-lookup"><span data-stu-id="958a3-106">You can pass an initialized single-dimensional array to a method.</span></span> <span data-ttu-id="958a3-107">Por exemplo, a instrução a seguir envia uma matriz a um método de impressão.</span><span class="sxs-lookup"><span data-stu-id="958a3-107">For example, the following statement sends an array to a print method.</span></span>  
  
 <span data-ttu-id="958a3-108">[!code-cs[csProgGuideArrays#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="958a3-108">[!code-cs[csProgGuideArrays#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_1.cs)]</span></span>  
  
 <span data-ttu-id="958a3-109">O código a seguir mostra uma implementação parcial do método de impressão.</span><span class="sxs-lookup"><span data-stu-id="958a3-109">The following code shows a partial implementation of the print method.</span></span>  
  
 <span data-ttu-id="958a3-110">[!code-cs[csProgGuideArrays#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="958a3-110">[!code-cs[csProgGuideArrays#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_2.cs)]</span></span>  
  
 <span data-ttu-id="958a3-111">É possível inicializar e passar uma nova matriz em uma etapa, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="958a3-111">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>  
  
 <span data-ttu-id="958a3-112">[!code-cs[CsProgGuideArrays#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="958a3-112">[!code-cs[CsProgGuideArrays#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_3.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="958a3-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="958a3-113">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="958a3-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="958a3-114">Description</span></span>  
 <span data-ttu-id="958a3-115">No exemplo a seguir, uma matriz de cadeia de caracteres é inicializada e passada como um argumento para um método `PrintArray` para cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="958a3-115">In the following example, an array of strings is initialized and passed as an argument to a `PrintArray` method for strings.</span></span> <span data-ttu-id="958a3-116">O método exibe os elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="958a3-116">The method displays the elements of the array.</span></span> <span data-ttu-id="958a3-117">Em seguida, os métodos `ChangeArray` e `ChangeArrayElement` são chamados para demonstrar que o envio de um argumento de matriz por valor não impede alterações nos elementos de matriz.</span><span class="sxs-lookup"><span data-stu-id="958a3-117">Next, methods `ChangeArray` and `ChangeArrayElement` are called to demonstrate that sending an array argument by value does not prevent changes to the array elements.</span></span>  
  
### <a name="code"></a><span data-ttu-id="958a3-118">Código</span><span class="sxs-lookup"><span data-stu-id="958a3-118">Code</span></span>  
 <span data-ttu-id="958a3-119">[!code-cs[csProgGuideArrays#30](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="958a3-119">[!code-cs[csProgGuideArrays#30](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_4.cs)]</span></span>  
  
## <a name="passing-multidimensional-arrays-as-arguments"></a><span data-ttu-id="958a3-120">Passando matrizes multidimensionais como argumentos</span><span class="sxs-lookup"><span data-stu-id="958a3-120">Passing Multidimensional Arrays As Arguments</span></span>  
 <span data-ttu-id="958a3-121">Você passa uma matriz multidimensional inicializada para um método da mesma forma que você passa uma matriz unidimensional.</span><span class="sxs-lookup"><span data-stu-id="958a3-121">You pass an initialized multidimensional array to a method in the same way that you pass a one-dimensional array.</span></span>  
  
 <span data-ttu-id="958a3-122">[!code-cs[csProgGuideArrays#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="958a3-122">[!code-cs[csProgGuideArrays#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_5.cs)]</span></span>  
  
 <span data-ttu-id="958a3-123">O código a seguir mostra uma declaração parcial de um método de impressão que aceita uma matriz bidimensional como seu argumento.</span><span class="sxs-lookup"><span data-stu-id="958a3-123">The following code shows a partial declaration of a print method that accepts a two-dimensional array as its argument.</span></span>  
  
 <span data-ttu-id="958a3-124">[!code-cs[csProgGuideArrays#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="958a3-124">[!code-cs[csProgGuideArrays#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_6.cs)]</span></span>  
  
 <span data-ttu-id="958a3-125">É possível inicializar e passar uma nova matriz em uma etapa, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="958a3-125">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>  
  
 <span data-ttu-id="958a3-126">[!code-cs[csProgGuideArrays#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="958a3-126">[!code-cs[csProgGuideArrays#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_7.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="958a3-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="958a3-127">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="958a3-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="958a3-128">Description</span></span>  
 <span data-ttu-id="958a3-129">No exemplo a seguir, uma matriz bidimensional de inteiros é inicializada e passada para o método `Print2DArray`.</span><span class="sxs-lookup"><span data-stu-id="958a3-129">In the following example, a two-dimensional array of integers is initialized and passed to the `Print2DArray` method.</span></span> <span data-ttu-id="958a3-130">O método exibe os elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="958a3-130">The method displays the elements of the array.</span></span>  
  
### <a name="code"></a><span data-ttu-id="958a3-131">Código</span><span class="sxs-lookup"><span data-stu-id="958a3-131">Code</span></span>  
 <span data-ttu-id="958a3-132">[!code-cs[csProgGuideArrays#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="958a3-132">[!code-cs[csProgGuideArrays#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_8.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="958a3-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="958a3-133">See Also</span></span>  
 <span data-ttu-id="958a3-134">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="958a3-134">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="958a3-135">[Matrizes](../../../csharp/programming-guide/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="958a3-135">[Arrays](../../../csharp/programming-guide/arrays/index.md) </span></span>  
 <span data-ttu-id="958a3-136">[Matrizes Unidimensionais](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="958a3-136">[Single-Dimensional Arrays](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md) </span></span>  
 <span data-ttu-id="958a3-137">[Matrizes Multidimensionais](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="958a3-137">[Multidimensional Arrays](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) </span></span>  
 [<span data-ttu-id="958a3-138">Matrizes denteadas</span><span class="sxs-lookup"><span data-stu-id="958a3-138">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)

