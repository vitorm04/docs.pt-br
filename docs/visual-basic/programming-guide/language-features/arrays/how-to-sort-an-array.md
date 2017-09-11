---
title: 'Como: classificar uma matriz no Visual Basic | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- Array.Sort
dev_langs:
- VB
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 0f806de89bef3ad0a21c5cd6ec5a528fcfcad807
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-sort-an-array-in-visual-basic"></a><span data-ttu-id="2224a-102">Como classificar uma matriz no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2224a-102">How to: Sort An Array in Visual Basic</span></span>
<span data-ttu-id="2224a-103">Este exemplo declara uma matriz de `String` objetos nomeados `zooAnimals`, preenche-a e classifica em ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="2224a-103">This example declares an array of `String` objects named `zooAnimals`, populates it, and then sorts it alphabetically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2224a-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2224a-104">Example</span></span>  
  
```  
Private Sub sortAnimals()  
    Dim zooAnimals(2) As String  
    zooAnimals(0) = "lion"  
    zooAnimals(1) = "turtle"  
    zooAnimals(2) = "ostrich"  
    Array.Sort(zooAnimals)  
End Sub  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2224a-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="2224a-105">Compiling the Code</span></span>  
 <span data-ttu-id="2224a-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="2224a-106">This example requires:</span></span>  
  
-   <span data-ttu-id="2224a-107">Acesso ao mscorlib. dll e o <xref:System>namespace.</xref:System></span><span class="sxs-lookup"><span data-stu-id="2224a-107">Access to Mscorlib.dll and the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="2224a-108">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="2224a-108">Robust Programming</span></span>  
 <span data-ttu-id="2224a-109">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="2224a-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="2224a-110">Matriz está vazia (<xref:System.ArgumentNullException> classe)</xref:System.ArgumentNullException></span><span class="sxs-lookup"><span data-stu-id="2224a-110">Array is empty (<xref:System.ArgumentNullException> class)</span></span>  
  
-   <span data-ttu-id="2224a-111">Matriz é multidimensional (<xref:System.RankException> classe)</xref:System.RankException></span><span class="sxs-lookup"><span data-stu-id="2224a-111">Array is multidimensional (<xref:System.RankException> class)</span></span>  
  
-   <span data-ttu-id="2224a-112">Um ou mais elementos da matriz não implementam a <xref:System.IComparable>interface (<xref:System.InvalidOperationException> classe)</xref:System.InvalidOperationException> </xref:System.IComparable></span><span class="sxs-lookup"><span data-stu-id="2224a-112">One or more elements of the array do not implement the <xref:System.IComparable> interface (<xref:System.InvalidOperationException> class)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2224a-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2224a-113">See Also</span></span>  
 <span data-ttu-id="2224a-114"><xref:System.Array.Sort%2A?displayProperty=fullName></xref:System.Array.Sort%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="2224a-114"><xref:System.Array.Sort%2A?displayProperty=fullName></span></span>   
<span data-ttu-id="2224a-115"> [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="2224a-115"> [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md) </span></span>  
<span data-ttu-id="2224a-116"> [Solucionando problemas de matrizes](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="2224a-116"> [Troubleshooting Arrays](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md) </span></span>  
<span data-ttu-id="2224a-117"> [Coleções](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) </span><span class="sxs-lookup"><span data-stu-id="2224a-117"> [Collections](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) </span></span>  
<span data-ttu-id="2224a-118"> [Instrução For Each...Next](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)</span><span class="sxs-lookup"><span data-stu-id="2224a-118"> [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)</span></span>
