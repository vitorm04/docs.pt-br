---
title: Passando matrizes como argumentos (Guia de Programação em C#)
ms.date: 07/05/2018
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: 0289297be9d7b4989cc95d2b50b92dae9ee831f7
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199210"
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a><span data-ttu-id="6017d-102">Passando matrizes como argumentos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="6017d-102">Passing arrays as arguments (C# Programming Guide)</span></span>

<span data-ttu-id="6017d-103">As matrizes podem ser passadas como argumentos para parâmetros de método.</span><span class="sxs-lookup"><span data-stu-id="6017d-103">Arrays can be passed as arguments to method parameters.</span></span> <span data-ttu-id="6017d-104">Como matrizes são tipos de referência, o método pode alterar o valor dos elementos.</span><span class="sxs-lookup"><span data-stu-id="6017d-104">Because arrays are reference types, the method can change the value of the elements.</span></span>

## <a name="passing-single-dimensional-arrays-as-arguments"></a><span data-ttu-id="6017d-105">Passando matrizes unidimensionais como argumentos</span><span class="sxs-lookup"><span data-stu-id="6017d-105">Passing single-dimensional arrays as arguments</span></span>

<span data-ttu-id="6017d-106">É possível passar uma matriz unidimensional inicializada para um método.</span><span class="sxs-lookup"><span data-stu-id="6017d-106">You can pass an initialized single-dimensional array to a method.</span></span> <span data-ttu-id="6017d-107">Por exemplo, a instrução a seguir envia uma matriz a um método de impressão.</span><span class="sxs-lookup"><span data-stu-id="6017d-107">For example, the following statement sends an array to a print method.</span></span>

[!code-csharp[csProgGuideArrays#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#34)]

<span data-ttu-id="6017d-108">O código a seguir mostra uma implementação parcial do método de impressão.</span><span class="sxs-lookup"><span data-stu-id="6017d-108">The following code shows a partial implementation of the print method.</span></span>

[!code-csharp[csProgGuideArrays#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#33)]

<span data-ttu-id="6017d-109">É possível inicializar e passar uma nova matriz em uma etapa, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6017d-109">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>

[!code-csharp[CsProgGuideArrays#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#35)]

### <a name="example"></a><span data-ttu-id="6017d-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6017d-110">Example</span></span>

<span data-ttu-id="6017d-111">No exemplo a seguir, uma matriz de cadeia de caracteres é inicializada e passada como um argumento para um método `DisplayArray` para cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="6017d-111">In the following example, an array of strings is initialized and passed as an argument to a `DisplayArray` method for strings.</span></span> <span data-ttu-id="6017d-112">O método exibe os elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="6017d-112">The method displays the elements of the array.</span></span> <span data-ttu-id="6017d-113">Em seguida, o método `ChangeArray` inverte os elementos da matriz, e o método `ChangeArrayElements` modifica os três primeiros elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="6017d-113">Next, the `ChangeArray` method reverses the array elements, and then the `ChangeArrayElements` method modifies the first three elements of the array.</span></span> <span data-ttu-id="6017d-114">Depois que cada método retorna, o método `DisplayArray` mostra que passar uma matriz por valor não impede alterações nos elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="6017d-114">After each method returns, the `DisplayArray` method shows that passing an array by value doesn't prevent changes to the array elements.</span></span>

[!code-csharp[csProgGuideArrays#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/ArrayExample.cs)]

## <a name="passing-multidimensional-arrays-as-arguments"></a><span data-ttu-id="6017d-115">Passando matrizes multidimensionais como argumentos</span><span class="sxs-lookup"><span data-stu-id="6017d-115">Passing multidimensional arrays as arguments</span></span>

<span data-ttu-id="6017d-116">Você passa uma matriz multidimensional inicializada para um método da mesma forma que você passa uma matriz unidimensional.</span><span class="sxs-lookup"><span data-stu-id="6017d-116">You pass an initialized multidimensional array to a method in the same way that you pass a one-dimensional array.</span></span>

[!code-csharp[csProgGuideArrays#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#41)]

<span data-ttu-id="6017d-117">O código a seguir mostra uma declaração parcial de um método de impressão que aceita uma matriz bidimensional como seu argumento.</span><span class="sxs-lookup"><span data-stu-id="6017d-117">The following code shows a partial declaration of a print method that accepts a two-dimensional array as its argument.</span></span>

[!code-csharp[csProgGuideArrays#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#36)]

<span data-ttu-id="6017d-118">É possível inicializar e passar uma nova matriz em uma única etapa, conforme é mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="6017d-118">You can initialize and pass a new array in one step, as is shown in the following example:</span></span>

[!code-csharp[csProgGuideArrays#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#32)]

### <a name="example"></a><span data-ttu-id="6017d-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6017d-119">Example</span></span>

<span data-ttu-id="6017d-120">No exemplo a seguir, uma matriz bidimensional de inteiros é inicializada e passada para o método `Print2DArray`.</span><span class="sxs-lookup"><span data-stu-id="6017d-120">In the following example, a two-dimensional array of integers is initialized and passed to the `Print2DArray` method.</span></span> <span data-ttu-id="6017d-121">O método exibe os elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="6017d-121">The method displays the elements of the array.</span></span>

[!code-csharp[csProgGuideArrays#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#31)]

## <a name="see-also"></a><span data-ttu-id="6017d-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6017d-122">See also</span></span>

[<span data-ttu-id="6017d-123">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="6017d-123">C# Programming Guide</span></span>](../index.md)  
[<span data-ttu-id="6017d-124">Matrizes</span><span class="sxs-lookup"><span data-stu-id="6017d-124">Arrays</span></span>](index.md)  
[<span data-ttu-id="6017d-125">Matrizes unidimensionais</span><span class="sxs-lookup"><span data-stu-id="6017d-125">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)  
[<span data-ttu-id="6017d-126">Matrizes multidimensionais</span><span class="sxs-lookup"><span data-stu-id="6017d-126">Multidimensional Arrays</span></span>](multidimensional-arrays.md)  
[<span data-ttu-id="6017d-127">Matrizes denteadas</span><span class="sxs-lookup"><span data-stu-id="6017d-127">Jagged Arrays</span></span>](jagged-arrays.md)  