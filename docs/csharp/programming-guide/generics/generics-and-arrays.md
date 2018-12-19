---
title: Genéricos e matrizes – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: 50d649c4662114e76fdc0a6161ab0cbbeb04756d
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237448"
---
# <a name="generics-and-arrays-c-programming-guide"></a><span data-ttu-id="aa905-102">Genéricos e matrizes (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="aa905-102">Generics and Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="aa905-103">No C# 2.0 e versões posteriores, matrizes unidimensionais que têm um limite inferior a zero implementam <xref:System.Collections.Generic.IList%601> automaticamente.</span><span class="sxs-lookup"><span data-stu-id="aa905-103">In C# 2.0 and later, single-dimensional arrays that have a lower bound of zero automatically implement <xref:System.Collections.Generic.IList%601>.</span></span> <span data-ttu-id="aa905-104">Isso permite a criação de métodos genéricos que podem usar o mesmo código para iterar por meio de matrizes e outros tipos de coleção.</span><span class="sxs-lookup"><span data-stu-id="aa905-104">This enables you to create generic methods that can use the same code to iterate through arrays and other collection types.</span></span> <span data-ttu-id="aa905-105">Essa técnica é útil principalmente para ler dados em coleções.</span><span class="sxs-lookup"><span data-stu-id="aa905-105">This technique is primarily useful for reading data in collections.</span></span> <span data-ttu-id="aa905-106">A interface <xref:System.Collections.Generic.IList%601> não pode ser usada para adicionar ou remover elementos de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="aa905-106">The <xref:System.Collections.Generic.IList%601> interface cannot be used to add or remove elements from an array.</span></span> <span data-ttu-id="aa905-107">Uma exceção será lançada se você tentar chamar um método <xref:System.Collections.Generic.IList%601> tal como <xref:System.Collections.Generic.IList%601.RemoveAt%2A> em uma matriz neste contexto.</span><span class="sxs-lookup"><span data-stu-id="aa905-107">An exception will be thrown if you try to call an <xref:System.Collections.Generic.IList%601> method such as <xref:System.Collections.Generic.IList%601.RemoveAt%2A> on an array in this context.</span></span>  
  
 <span data-ttu-id="aa905-108">O exemplo de código a seguir demonstra como um único método genérico que usa um parâmetro de entrada <xref:System.Collections.Generic.IList%601> pode iterar por meio de uma lista e uma matriz, nesse caso, uma matriz de inteiros.</span><span class="sxs-lookup"><span data-stu-id="aa905-108">The following code example demonstrates how a single generic method that takes an <xref:System.Collections.Generic.IList%601> input parameter can iterate through both a list and an array, in this case an array of integers.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#35](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-arrays_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="aa905-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa905-109">See Also</span></span>

- <xref:System.Collections.Generic>  
- [<span data-ttu-id="aa905-110">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="aa905-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="aa905-111">Genéricos</span><span class="sxs-lookup"><span data-stu-id="aa905-111">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
- [<span data-ttu-id="aa905-112">Matrizes</span><span class="sxs-lookup"><span data-stu-id="aa905-112">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
- [<span data-ttu-id="aa905-113">Genéricos</span><span class="sxs-lookup"><span data-stu-id="aa905-113">Generics</span></span>](~/docs/standard/generics/index.md)
