---
title: Como classificar uma matriz
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: 3fb9af8de0fc86075fdccd64506c855c1c720660
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351849"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a><span data-ttu-id="fea3a-102">Como classificar uma matriz no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fea3a-102">How to: sort an array in Visual Basic</span></span>

<span data-ttu-id="fea3a-103">Este artigo mostra um exemplo de como classificar uma matriz de cadeias de caracteres no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fea3a-103">This article shows an example of how to sort an array of strings in Visual Basic.</span></span>

## <a name="example"></a><span data-ttu-id="fea3a-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fea3a-104">Example</span></span>

<span data-ttu-id="fea3a-105">Este exemplo declara uma matriz de `String` objetos chamada `zooAnimals`, popula-o e, em seguida, classifica-o em ordem alfabética:</span><span class="sxs-lookup"><span data-stu-id="fea3a-105">This example declares an array of `String` objects named `zooAnimals`, populates it, and then sorts it alphabetically:</span></span>
  
```vb
Private Sub SortAnimals()
    Dim zooAnimals(2) As String
    zooAnimals(0) = "lion"
    zooAnimals(1) = "turtle"
    zooAnimals(2) = "ostrich"
    Array.Sort(zooAnimals)
End Sub
```

## <a name="robust-programming"></a><span data-ttu-id="fea3a-106">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="fea3a-106">Robust programming</span></span>

<span data-ttu-id="fea3a-107">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="fea3a-107">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="fea3a-108">A matriz está vazia (classe<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="fea3a-108">Array is empty (<xref:System.ArgumentNullException> class).</span></span>
- <span data-ttu-id="fea3a-109">A matriz é multidimensional (<xref:System.RankException> classe).</span><span class="sxs-lookup"><span data-stu-id="fea3a-109">Array is multidimensional (<xref:System.RankException> class).</span></span>
- <span data-ttu-id="fea3a-110">Um ou mais elementos da matriz não implementam a interface de <xref:System.IComparable> (<xref:System.InvalidOperationException> classe).</span><span class="sxs-lookup"><span data-stu-id="fea3a-110">One or more elements of the array don't implement the <xref:System.IComparable> interface (<xref:System.InvalidOperationException> class).</span></span>

## <a name="see-also"></a><span data-ttu-id="fea3a-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fea3a-111">See also</span></span>

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [<span data-ttu-id="fea3a-112">Matrizes</span><span class="sxs-lookup"><span data-stu-id="fea3a-112">Arrays</span></span>](index.md)
- [<span data-ttu-id="fea3a-113">Solução de problemas de matrizes</span><span class="sxs-lookup"><span data-stu-id="fea3a-113">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)
- [<span data-ttu-id="fea3a-114">Coleções</span><span class="sxs-lookup"><span data-stu-id="fea3a-114">Collections</span></span>](../../concepts/collections.md)
- [<span data-ttu-id="fea3a-115">Instrução For Each...Next</span><span class="sxs-lookup"><span data-stu-id="fea3a-115">For Each...Next Statement</span></span>](../../../language-reference/statements/for-each-next-statement.md)
