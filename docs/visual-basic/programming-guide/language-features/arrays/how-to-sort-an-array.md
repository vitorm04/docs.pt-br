---
title: 'Como: Classificar uma matriz no Visual Basic'
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: 467d1bcce6bda2feb5a8e59c152cb292d753e79b
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700969"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a><span data-ttu-id="4bc28-102">Como classificar uma matriz no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4bc28-102">How to: sort an array in Visual Basic</span></span>

<span data-ttu-id="4bc28-103">Este artigo mostra um exemplo de como classificar uma matriz de cadeias de caracteres no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4bc28-103">This article shows an example of how to sort an array of strings in Visual Basic.</span></span>

## <a name="example"></a><span data-ttu-id="4bc28-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4bc28-104">Example</span></span>

<span data-ttu-id="4bc28-105">Este exemplo declara uma matriz de objetos `String` chamados `zooAnimals`, popula-o e, em seguida, classifica-o em ordem alfabética:</span><span class="sxs-lookup"><span data-stu-id="4bc28-105">This example declares an array of `String` objects named `zooAnimals`, populates it, and then sorts it alphabetically:</span></span>
  
```vb
Private Sub SortAnimals()
    Dim zooAnimals(2) As String
    zooAnimals(0) = "lion"
    zooAnimals(1) = "turtle"
    zooAnimals(2) = "ostrich"
    Array.Sort(zooAnimals)
End Sub
```

## <a name="robust-programming"></a><span data-ttu-id="4bc28-106">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="4bc28-106">Robust programming</span></span>

<span data-ttu-id="4bc28-107">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="4bc28-107">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="4bc28-108">A matriz está vazia (classe <xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="4bc28-108">Array is empty (<xref:System.ArgumentNullException> class).</span></span>
- <span data-ttu-id="4bc28-109">A matriz é multidimensional (classe <xref:System.RankException>).</span><span class="sxs-lookup"><span data-stu-id="4bc28-109">Array is multidimensional (<xref:System.RankException> class).</span></span>
- <span data-ttu-id="4bc28-110">Um ou mais elementos da matriz não implementam a interface <xref:System.IComparable> (classe <xref:System.InvalidOperationException>).</span><span class="sxs-lookup"><span data-stu-id="4bc28-110">One or more elements of the array don't implement the <xref:System.IComparable> interface (<xref:System.InvalidOperationException> class).</span></span>

## <a name="see-also"></a><span data-ttu-id="4bc28-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4bc28-111">See also</span></span>

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [<span data-ttu-id="4bc28-112">Matrizes</span><span class="sxs-lookup"><span data-stu-id="4bc28-112">Arrays</span></span>](index.md)
- [<span data-ttu-id="4bc28-113">Solução de problemas de matrizes</span><span class="sxs-lookup"><span data-stu-id="4bc28-113">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)
- [<span data-ttu-id="4bc28-114">Coleções</span><span class="sxs-lookup"><span data-stu-id="4bc28-114">Collections</span></span>](../../concepts/collections.md)
- [<span data-ttu-id="4bc28-115">Instrução For Each...Next</span><span class="sxs-lookup"><span data-stu-id="4bc28-115">For Each...Next Statement</span></span>](../../../language-reference/statements/for-each-next-statement.md)
