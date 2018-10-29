---
title: Matrizes multidimensionais (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: a1d7a0a014c330682316e869f6727082fa3b31ef
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48841067"
---
# <a name="multidimensional-arrays-c-programming-guide"></a><span data-ttu-id="83f12-102">Matrizes multidimensionais (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="83f12-102">Multidimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="83f12-103">As matrizes podem ter mais de uma dimensão.</span><span class="sxs-lookup"><span data-stu-id="83f12-103">Arrays can have more than one dimension.</span></span> <span data-ttu-id="83f12-104">Por exemplo, a declaração a seguir cria uma matriz bidimensional de quatro linhas e duas colunas.</span><span class="sxs-lookup"><span data-stu-id="83f12-104">For example, the following declaration creates a two-dimensional array of four rows and two columns.</span></span>  
  
 [!code-csharp[csProgGuideArrays#11](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_1.cs)]  
  
 <span data-ttu-id="83f12-105">A declaração a seguir cria uma matriz de três dimensões, 4, 2 e 3.</span><span class="sxs-lookup"><span data-stu-id="83f12-105">The following declaration creates an array of three dimensions, 4, 2, and 3.</span></span>  
  
 [!code-csharp[csProgGuideArrays#12](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_2.cs)]  
  
## <a name="array-initialization"></a><span data-ttu-id="83f12-106">Inicialização de Matriz</span><span class="sxs-lookup"><span data-stu-id="83f12-106">Array Initialization</span></span>

 <span data-ttu-id="83f12-107">É possível inicializar a matriz na declaração, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="83f12-107">You can initialize the array upon declaration, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#13](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_3.cs)]  
  
 <span data-ttu-id="83f12-108">Também é possível inicializar a matriz sem especificar a classificação.</span><span class="sxs-lookup"><span data-stu-id="83f12-108">You also can initialize the array without specifying the rank.</span></span>  
  
 [!code-csharp[csProgGuideArrays#14](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_4.cs)]  
  
 <span data-ttu-id="83f12-109">Caso você escolha declarar uma variável de matriz sem inicialização, será necessário usar o operador `new` ao atribuir uma matriz a essa variável.</span><span class="sxs-lookup"><span data-stu-id="83f12-109">If you choose to declare an array variable without initialization, you must use the `new` operator to assign an array to the variable.</span></span> <span data-ttu-id="83f12-110">O uso de `new` é mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="83f12-110">The use of `new` is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#15](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_5.cs)]  
  
 <span data-ttu-id="83f12-111">O exemplo a seguir atribui um valor a um elemento de matriz específico.</span><span class="sxs-lookup"><span data-stu-id="83f12-111">The following example assigns a value to a particular array element.</span></span>  
  
 [!code-csharp[csProgGuideArrays#16](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_6.cs)]  
  
 <span data-ttu-id="83f12-112">Da mesma forma, o exemplo a seguir obtém o valor de um elemento de matriz específico e o atribui à variável `elementValue`.</span><span class="sxs-lookup"><span data-stu-id="83f12-112">Similarly, the following example gets the value of a particular array element and assigns it to variable `elementValue`.</span></span>  
  
 [!code-csharp[csProgGuideArrays#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_7.cs)]  
  
 <span data-ttu-id="83f12-113">O exemplo de código a seguir inicializa os elementos da matriz com valores padrão (exceto em matrizes denteadas).</span><span class="sxs-lookup"><span data-stu-id="83f12-113">The following code example initializes the array elements to default values (except for jagged arrays).</span></span>  
  
 [!code-csharp[csProgGuideArrays#17](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_8.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="83f12-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83f12-114">See Also</span></span>

- [<span data-ttu-id="83f12-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="83f12-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="83f12-116">Matrizes</span><span class="sxs-lookup"><span data-stu-id="83f12-116">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
- [<span data-ttu-id="83f12-117">Matrizes unidimensionais</span><span class="sxs-lookup"><span data-stu-id="83f12-117">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
- [<span data-ttu-id="83f12-118">Matrizes denteadas</span><span class="sxs-lookup"><span data-stu-id="83f12-118">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
