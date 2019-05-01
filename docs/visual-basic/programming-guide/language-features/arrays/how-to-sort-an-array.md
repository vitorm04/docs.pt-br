---
title: 'Como: Classificar uma matriz no Visual Basic'
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: 3f4dbd6dce0957de3451b1f29c3a67ccd6791045
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053649"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a><span data-ttu-id="5d4da-102">Como: Classificar uma matriz no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5d4da-102">How to: Sort An Array in Visual Basic</span></span>
<span data-ttu-id="5d4da-103">Este exemplo declara uma matriz de `String` objetos nomeados `zooAnimals`, preenche-o e, em seguida, classifica-os em ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="5d4da-103">This example declares an array of `String` objects named `zooAnimals`, populates it, and then sorts it alphabetically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d4da-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5d4da-104">Example</span></span>  
  
```  
Private Sub sortAnimals()  
    Dim zooAnimals(2) As String  
    zooAnimals(0) = "lion"  
    zooAnimals(1) = "turtle"  
    zooAnimals(2) = "ostrich"  
    Array.Sort(zooAnimals)  
End Sub  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5d4da-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="5d4da-105">Compiling the Code</span></span>  
 <span data-ttu-id="5d4da-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="5d4da-106">This example requires:</span></span>  
  
- <span data-ttu-id="5d4da-107">Acesso ao mscorlib. dll e o <xref:System> namespace.</span><span class="sxs-lookup"><span data-stu-id="5d4da-107">Access to Mscorlib.dll and the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="5d4da-108">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="5d4da-108">Robust Programming</span></span>  
 <span data-ttu-id="5d4da-109">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="5d4da-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="5d4da-110">Matriz está vazia (<xref:System.ArgumentNullException> classe)</span><span class="sxs-lookup"><span data-stu-id="5d4da-110">Array is empty (<xref:System.ArgumentNullException> class)</span></span>  
  
- <span data-ttu-id="5d4da-111">A matriz é multidimensional (<xref:System.RankException> classe)</span><span class="sxs-lookup"><span data-stu-id="5d4da-111">Array is multidimensional (<xref:System.RankException> class)</span></span>  
  
- <span data-ttu-id="5d4da-112">Um ou mais elementos da matriz não implementam o <xref:System.IComparable> interface (<xref:System.InvalidOperationException> classe)</span><span class="sxs-lookup"><span data-stu-id="5d4da-112">One or more elements of the array do not implement the <xref:System.IComparable> interface (<xref:System.InvalidOperationException> class)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d4da-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d4da-113">See also</span></span>

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5d4da-114">Matrizes</span><span class="sxs-lookup"><span data-stu-id="5d4da-114">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="5d4da-115">Solução de problemas de matrizes</span><span class="sxs-lookup"><span data-stu-id="5d4da-115">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [<span data-ttu-id="5d4da-116">Coleções</span><span class="sxs-lookup"><span data-stu-id="5d4da-116">Collections</span></span>](../../concepts/collections.md)
- [<span data-ttu-id="5d4da-117">Instrução For Each...Next</span><span class="sxs-lookup"><span data-stu-id="5d4da-117">For Each...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
