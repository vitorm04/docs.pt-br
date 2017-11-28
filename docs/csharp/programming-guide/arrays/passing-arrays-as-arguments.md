---
title: "Passando matrizes como argumentos (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f152173b747a171052ab99f261ed91ced9465fdc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a><span data-ttu-id="9b143-102">Passando matrizes como argumentos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="9b143-102">Passing Arrays as Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="9b143-103">As matrizes podem ser passadas como argumentos para parâmetros de método.</span><span class="sxs-lookup"><span data-stu-id="9b143-103">Arrays can be passed as arguments to method parameters.</span></span> <span data-ttu-id="9b143-104">Como matrizes são tipos de referência, o método pode alterar o valor dos elementos.</span><span class="sxs-lookup"><span data-stu-id="9b143-104">Because arrays are reference types, the method can change the value of the elements.</span></span>  
  
## <a name="passing-single-dimensional-arrays-as-arguments"></a><span data-ttu-id="9b143-105">Passando matrizes unidimensionais como argumentos</span><span class="sxs-lookup"><span data-stu-id="9b143-105">Passing Single-Dimensional Arrays As Arguments</span></span>  
 <span data-ttu-id="9b143-106">É possível passar uma matriz unidimensional inicializada para um método.</span><span class="sxs-lookup"><span data-stu-id="9b143-106">You can pass an initialized single-dimensional array to a method.</span></span> <span data-ttu-id="9b143-107">Por exemplo, a instrução a seguir envia uma matriz a um método de impressão.</span><span class="sxs-lookup"><span data-stu-id="9b143-107">For example, the following statement sends an array to a print method.</span></span>  
  
 [!code-csharp[csProgGuideArrays#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_1.cs)]  
  
 <span data-ttu-id="9b143-108">O código a seguir mostra uma implementação parcial do método de impressão.</span><span class="sxs-lookup"><span data-stu-id="9b143-108">The following code shows a partial implementation of the print method.</span></span>  
  
 [!code-csharp[csProgGuideArrays#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_2.cs)]  
  
 <span data-ttu-id="9b143-109">É possível inicializar e passar uma nova matriz em uma etapa, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="9b143-109">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>  
  
 [!code-csharp[CsProgGuideArrays#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="9b143-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9b143-110">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="9b143-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="9b143-111">Description</span></span>  
 <span data-ttu-id="9b143-112">No exemplo a seguir, uma matriz de cadeia de caracteres é inicializada e passada como um argumento para um método `PrintArray` para cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="9b143-112">In the following example, an array of strings is initialized and passed as an argument to a `PrintArray` method for strings.</span></span> <span data-ttu-id="9b143-113">O método exibe os elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="9b143-113">The method displays the elements of the array.</span></span> <span data-ttu-id="9b143-114">Em seguida, os métodos `ChangeArray` e `ChangeArrayElement` são chamados para demonstrar que o envio de um argumento de matriz por valor não impede alterações nos elementos de matriz.</span><span class="sxs-lookup"><span data-stu-id="9b143-114">Next, methods `ChangeArray` and `ChangeArrayElement` are called to demonstrate that sending an array argument by value does not prevent changes to the array elements.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9b143-115">Código</span><span class="sxs-lookup"><span data-stu-id="9b143-115">Code</span></span>  
 [!code-csharp[csProgGuideArrays#30](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_4.cs)]  
  
## <a name="passing-multidimensional-arrays-as-arguments"></a><span data-ttu-id="9b143-116">Passando matrizes multidimensionais como argumentos</span><span class="sxs-lookup"><span data-stu-id="9b143-116">Passing Multidimensional Arrays As Arguments</span></span>  
 <span data-ttu-id="9b143-117">Você passa uma matriz multidimensional inicializada para um método da mesma forma que você passa uma matriz unidimensional.</span><span class="sxs-lookup"><span data-stu-id="9b143-117">You pass an initialized multidimensional array to a method in the same way that you pass a one-dimensional array.</span></span>  
  
 [!code-csharp[csProgGuideArrays#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_5.cs)]  
  
 <span data-ttu-id="9b143-118">O código a seguir mostra uma declaração parcial de um método de impressão que aceita uma matriz bidimensional como seu argumento.</span><span class="sxs-lookup"><span data-stu-id="9b143-118">The following code shows a partial declaration of a print method that accepts a two-dimensional array as its argument.</span></span>  
  
 [!code-csharp[csProgGuideArrays#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_6.cs)]  
  
 <span data-ttu-id="9b143-119">É possível inicializar e passar uma nova matriz em uma etapa, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="9b143-119">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_7.cs)]  
  
## <a name="example"></a><span data-ttu-id="9b143-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9b143-120">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="9b143-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="9b143-121">Description</span></span>  
 <span data-ttu-id="9b143-122">No exemplo a seguir, uma matriz bidimensional de inteiros é inicializada e passada para o método `Print2DArray`.</span><span class="sxs-lookup"><span data-stu-id="9b143-122">In the following example, a two-dimensional array of integers is initialized and passed to the `Print2DArray` method.</span></span> <span data-ttu-id="9b143-123">O método exibe os elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="9b143-123">The method displays the elements of the array.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9b143-124">Código</span><span class="sxs-lookup"><span data-stu-id="9b143-124">Code</span></span>  
 [!code-csharp[csProgGuideArrays#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_8.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="9b143-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b143-125">See Also</span></span>  
 [<span data-ttu-id="9b143-126">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="9b143-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9b143-127">Matrizes</span><span class="sxs-lookup"><span data-stu-id="9b143-127">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="9b143-128">Matrizes unidimensionais</span><span class="sxs-lookup"><span data-stu-id="9b143-128">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="9b143-129">Matrizes multidimensionais</span><span class="sxs-lookup"><span data-stu-id="9b143-129">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="9b143-130">Matrizes denteadas</span><span class="sxs-lookup"><span data-stu-id="9b143-130">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
