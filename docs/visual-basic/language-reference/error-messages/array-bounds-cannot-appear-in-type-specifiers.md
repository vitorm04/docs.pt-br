---
title: Os limites de matriz não podem ser exibidos em especificadores de tipo
ms.date: 07/20/2015
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
ms.openlocfilehash: f20ed883005641082eb89e2effa5221594910ffe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838775"
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a><span data-ttu-id="656a2-102">Os limites de matriz não podem ser exibidos em especificadores de tipo</span><span class="sxs-lookup"><span data-stu-id="656a2-102">Array bounds cannot appear in type specifiers</span></span>
<span data-ttu-id="656a2-103">Tamanhos de matriz não podem ser declarados como parte de um especificador de tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="656a2-103">Array sizes cannot be declared as part of a data type specifier.</span></span>  
  
 <span data-ttu-id="656a2-104">**ID do erro:** BC30638</span><span class="sxs-lookup"><span data-stu-id="656a2-104">**Error ID:** BC30638</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="656a2-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="656a2-105">To correct this error</span></span>  
  
-   <span data-ttu-id="656a2-106">Especifique o tamanho da matriz imediatamente após o nome da variável em vez de colocar o tamanho da matriz após o tipo, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="656a2-106">Specify the size of the array immediately following the variable name instead of placing the array size after the type, as shown in the following example.</span></span>  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
-   <span data-ttu-id="656a2-107">Definir uma matriz e inicialize-o com o número desejado de elementos, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="656a2-107">Define an array and initialize it with the desired number of elements, as shown in the following example.</span></span>  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="656a2-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="656a2-108">See also</span></span>

- [<span data-ttu-id="656a2-109">Matrizes</span><span class="sxs-lookup"><span data-stu-id="656a2-109">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
