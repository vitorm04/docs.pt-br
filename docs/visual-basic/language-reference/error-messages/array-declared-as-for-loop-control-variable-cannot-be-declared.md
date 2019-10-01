---
title: A matriz declarada para a variável de controle do loop não pode ser declarada com um tamanho inicial
ms.date: 07/20/2015
f1_keywords:
- vbc32039
- bc32039
helpviewer_keywords:
- BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
ms.openlocfilehash: 9e8bb7b79b5a770c3c92e47d8e7c01c5b83d6061
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701204"
---
# <a name="array-declared-as-for-loop-control-variable-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="43cbc-102">A matriz declarada para a variável de controle do loop não pode ser declarada com um tamanho inicial</span><span class="sxs-lookup"><span data-stu-id="43cbc-102">Array declared as for loop control variable cannot be declared with an initial size</span></span>
<span data-ttu-id="43cbc-103">Um loop `For Each` usa uma matriz como sua variável de iteração de *elemento* , mas inicializa essa matriz.</span><span class="sxs-lookup"><span data-stu-id="43cbc-103">A `For Each` loop uses an array as its *element* iteration variable but initializes that array.</span></span>  
  
 <span data-ttu-id="43cbc-104">As instruções a seguir mostram como esse erro pode ser gerado.</span><span class="sxs-lookup"><span data-stu-id="43cbc-104">The following statements show how this error can be generated.</span></span>  
  
```vb  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 <span data-ttu-id="43cbc-105">A primeira instrução `For Each` é a maneira correta de acessar elementos de `arrayList`.</span><span class="sxs-lookup"><span data-stu-id="43cbc-105">The first `For Each` statement is the correct way to access elements of `arrayList`.</span></span> <span data-ttu-id="43cbc-106">A segunda instrução `For Each` gera esse erro.</span><span class="sxs-lookup"><span data-stu-id="43cbc-106">The second `For Each` statement generates this error.</span></span>  
  
 <span data-ttu-id="43cbc-107">**ID do erro:** BC32039</span><span class="sxs-lookup"><span data-stu-id="43cbc-107">**Error ID:** BC32039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="43cbc-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="43cbc-108">To correct this error</span></span>  
  
- <span data-ttu-id="43cbc-109">Remova a inicialização da declaração da variável de iteração do *elemento* .</span><span class="sxs-lookup"><span data-stu-id="43cbc-109">Remove the initialization from the declaration of the *element* iteration variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43cbc-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43cbc-110">See also</span></span>

- [<span data-ttu-id="43cbc-111">Instrução For...Next</span><span class="sxs-lookup"><span data-stu-id="43cbc-111">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="43cbc-112">Matrizes</span><span class="sxs-lookup"><span data-stu-id="43cbc-112">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="43cbc-113">Coleções</span><span class="sxs-lookup"><span data-stu-id="43cbc-113">Collections</span></span>](../../../standard/collections/index.md)
