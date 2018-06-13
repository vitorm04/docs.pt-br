---
title: Os limites de matriz não podem ser exibidos em especificadores de tipo
ms.date: 07/20/2015
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
ms.openlocfilehash: 45787db51de562f2266c587fd2bb15ef29ebefbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583677"
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a><span data-ttu-id="7e4a0-102">Os limites de matriz não podem ser exibidos em especificadores de tipo</span><span class="sxs-lookup"><span data-stu-id="7e4a0-102">Array bounds cannot appear in type specifiers</span></span>
<span data-ttu-id="7e4a0-103">Tamanhos de matriz não podem ser declarados como parte de um especificador de tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="7e4a0-103">Array sizes cannot be declared as part of a data type specifier.</span></span>  
  
 <span data-ttu-id="7e4a0-104">**ID do erro:** BC30638</span><span class="sxs-lookup"><span data-stu-id="7e4a0-104">**Error ID:** BC30638</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7e4a0-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="7e4a0-105">To correct this error</span></span>  
  
-   <span data-ttu-id="7e4a0-106">Especifique o tamanho da matriz imediatamente após o nome da variável em vez de fazer o tamanho da matriz após o tipo, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="7e4a0-106">Specify the size of the array immediately following the variable name instead of placing the array size after the type, as shown in the following example.</span></span>  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
-   <span data-ttu-id="7e4a0-107">Defina uma matriz e inicialize-o com o número desejado de elementos, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="7e4a0-107">Define an array and initialize it with the desired number of elements, as shown in the following example.</span></span>  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7e4a0-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e4a0-108">See Also</span></span>  
 [<span data-ttu-id="7e4a0-109">Matrizes</span><span class="sxs-lookup"><span data-stu-id="7e4a0-109">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
