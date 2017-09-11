---
title: "Usando foreach com matrizes (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
caps.latest.revision: 14
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
ms.openlocfilehash: a1d0b704233b110b5f499b8186a4a901f9b5408f
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="using-foreach-with-arrays-c-programming-guide"></a><span data-ttu-id="afa1b-102">Usando foreach com matrizes (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="afa1b-102">Using foreach with Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="afa1b-103">O C# também oferece a instrução [foreach](../../../csharp/language-reference/keywords/foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="afa1b-103">C# also provides the [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement.</span></span> <span data-ttu-id="afa1b-104">Essa instrução fornece uma maneira simples e limpa de iterar através dos elementos de uma matriz ou qualquer coleção enumerável.</span><span class="sxs-lookup"><span data-stu-id="afa1b-104">This statement provides a simple, clean way to iterate through the elements of an array or any enumerable collection.</span></span> <span data-ttu-id="afa1b-105">A instrução `foreach` processa os elementos na ordem retornada pela matriz ou enumerador do tipo de coleção que normalmente vai do elemento 0 ao último.</span><span class="sxs-lookup"><span data-stu-id="afa1b-105">The `foreach` statement processes elements in the order returned by the array or collection type’s enumerator, which is usually from the 0th element to the last.</span></span> <span data-ttu-id="afa1b-106">Por exemplo, o código a seguir cria uma matriz chamada `numbers` e itera por ela com a instrução `foreach`:</span><span class="sxs-lookup"><span data-stu-id="afa1b-106">For example, the following code creates an array called `numbers` and iterates through it with the `foreach` statement:</span></span>  
  
 <span data-ttu-id="afa1b-107">[!code-cs[csProgGuideArrays#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="afa1b-107">[!code-cs[csProgGuideArrays#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_1.cs)]</span></span>  
  
 <span data-ttu-id="afa1b-108">Com matrizes multidimensionais, você pode usar o mesmo método para iterar pelos elementos, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="afa1b-108">With multidimensional arrays, you can use the same method to iterate through the elements, for example:</span></span>  
  
 <span data-ttu-id="afa1b-109">[!code-cs[csProgGuideArrays#29](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="afa1b-109">[!code-cs[csProgGuideArrays#29](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_2.cs)]</span></span>  
  
 <span data-ttu-id="afa1b-110">No entanto, com matrizes multidimensionais, usar um loop aninhado [for](../../../csharp/language-reference/keywords/for.md) oferece mais controle sobre os elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="afa1b-110">However, with multidimensional arrays, using a nested [for](../../../csharp/language-reference/keywords/for.md) loop gives you more control over the array elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afa1b-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="afa1b-111">See Also</span></span>  
 <span data-ttu-id="afa1b-112"><xref:System.Array></span><span class="sxs-lookup"><span data-stu-id="afa1b-112"><xref:System.Array></span></span>   
 <span data-ttu-id="afa1b-113">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="afa1b-113">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="afa1b-114">[Matrizes](../../../csharp/programming-guide/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="afa1b-114">[Arrays](../../../csharp/programming-guide/arrays/index.md) </span></span>  
 <span data-ttu-id="afa1b-115">[Matrizes Unidimensionais](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="afa1b-115">[Single-Dimensional Arrays](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md) </span></span>  
 <span data-ttu-id="afa1b-116">[Matrizes Multidimensionais](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="afa1b-116">[Multidimensional Arrays](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) </span></span>  
 [<span data-ttu-id="afa1b-117">Matrizes denteadas</span><span class="sxs-lookup"><span data-stu-id="afa1b-117">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)

