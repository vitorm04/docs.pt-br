---
title: Genéricos e matrizes – Guia de Programação em C#
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: a8fad38fac07b9e8d51529d3ab7070328a333dbb
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75703007"
---
# <a name="generics-and-arrays-c-programming-guide"></a><span data-ttu-id="233aa-102">Genéricos e matrizes (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="233aa-102">Generics and Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="233aa-103">No C# 2.0 e versões posteriores, matrizes unidimensionais que têm um limite inferior a zero implementam <xref:System.Collections.Generic.IList%601> automaticamente.</span><span class="sxs-lookup"><span data-stu-id="233aa-103">In C# 2.0 and later, single-dimensional arrays that have a lower bound of zero automatically implement <xref:System.Collections.Generic.IList%601>.</span></span> <span data-ttu-id="233aa-104">Isso permite a criação de métodos genéricos que podem usar o mesmo código para iterar por meio de matrizes e outros tipos de coleção.</span><span class="sxs-lookup"><span data-stu-id="233aa-104">This enables you to create generic methods that can use the same code to iterate through arrays and other collection types.</span></span> <span data-ttu-id="233aa-105">Essa técnica é útil principalmente para ler dados em coleções.</span><span class="sxs-lookup"><span data-stu-id="233aa-105">This technique is primarily useful for reading data in collections.</span></span> <span data-ttu-id="233aa-106">A interface <xref:System.Collections.Generic.IList%601> não pode ser usada para adicionar ou remover elementos de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="233aa-106">The <xref:System.Collections.Generic.IList%601> interface cannot be used to add or remove elements from an array.</span></span> <span data-ttu-id="233aa-107">Uma exceção será lançada se você tentar chamar um método <xref:System.Collections.Generic.IList%601> tal como <xref:System.Collections.Generic.IList%601.RemoveAt%2A> em uma matriz neste contexto.</span><span class="sxs-lookup"><span data-stu-id="233aa-107">An exception will be thrown if you try to call an <xref:System.Collections.Generic.IList%601> method such as <xref:System.Collections.Generic.IList%601.RemoveAt%2A> on an array in this context.</span></span>  
  
 <span data-ttu-id="233aa-108">O exemplo de código a seguir demonstra como um único método genérico que usa um parâmetro de entrada <xref:System.Collections.Generic.IList%601> pode iterar por meio de uma lista e uma matriz, nesse caso, uma matriz de inteiros.</span><span class="sxs-lookup"><span data-stu-id="233aa-108">The following code example demonstrates how a single generic method that takes an <xref:System.Collections.Generic.IList%601> input parameter can iterate through both a list and an array, in this case an array of integers.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a><span data-ttu-id="233aa-109">Veja também</span><span class="sxs-lookup"><span data-stu-id="233aa-109">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="233aa-110">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="233aa-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="233aa-111">Genéricos</span><span class="sxs-lookup"><span data-stu-id="233aa-111">Generics</span></span>](./index.md)
- [<span data-ttu-id="233aa-112">Matrizes</span><span class="sxs-lookup"><span data-stu-id="233aa-112">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="233aa-113">Genéricos</span><span class="sxs-lookup"><span data-stu-id="233aa-113">Generics</span></span>](../../../standard/generics/index.md)
