---
title: A matriz declarada para a variável de controle do loop não pode ser declarada com um tamanho inicial
ms.date: 07/20/2015
f1_keywords:
- vbc32039
- bc32039
helpviewer_keywords:
- BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
ms.openlocfilehash: bee3bcd3701945f5cf77f6761defc8be77acf49f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58843572"
---
# <a name="array-declared-as-for-loop-control-variable-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="29092-102">A matriz declarada para a variável de controle do loop não pode ser declarada com um tamanho inicial</span><span class="sxs-lookup"><span data-stu-id="29092-102">Array declared as for loop control variable cannot be declared with an initial size</span></span>
<span data-ttu-id="29092-103">Um `For Each` loop usa uma matriz como seu *elemento* variável de iteração, mas inicializa essa matriz.</span><span class="sxs-lookup"><span data-stu-id="29092-103">A `For Each` loop uses an array as its *element* iteration variable but initializes that array.</span></span>  
  
 <span data-ttu-id="29092-104">As instruções a seguir mostram como esse erro pode ser gerado.</span><span class="sxs-lookup"><span data-stu-id="29092-104">The following statements show how this error can be generated.</span></span>  
  
```  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 <span data-ttu-id="29092-105">A primeira `For Each` instrução é a maneira correta de acessar elementos de `arrayList`.</span><span class="sxs-lookup"><span data-stu-id="29092-105">The first `For Each` statement is the correct way to access elements of `arrayList`.</span></span> <span data-ttu-id="29092-106">O segundo `For Each` instrução gera esse erro.</span><span class="sxs-lookup"><span data-stu-id="29092-106">The second `For Each` statement generates this error.</span></span>  
  
 <span data-ttu-id="29092-107">**ID do erro:** BC32039</span><span class="sxs-lookup"><span data-stu-id="29092-107">**Error ID:** BC32039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="29092-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="29092-108">To correct this error</span></span>  
  
-   <span data-ttu-id="29092-109">Remova a inicialização da declaração do *elemento* variável de iteração.</span><span class="sxs-lookup"><span data-stu-id="29092-109">Remove the initialization from the declaration of the *element* iteration variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29092-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29092-110">See also</span></span>

- [<span data-ttu-id="29092-111">Instrução For...Next</span><span class="sxs-lookup"><span data-stu-id="29092-111">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="29092-112">Matrizes</span><span class="sxs-lookup"><span data-stu-id="29092-112">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="29092-113">Coleções</span><span class="sxs-lookup"><span data-stu-id="29092-113">Collections</span></span>](../../../standard/collections/index.md)
