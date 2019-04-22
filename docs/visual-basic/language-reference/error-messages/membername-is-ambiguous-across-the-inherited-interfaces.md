---
title: "'<membername>' é ambíguo nas interfaces herdadas '<interfacename1>' e '<interfacename2>'"
ms.date: 07/20/2015
f1_keywords:
- vbc30685
- bc30685
helpviewer_keywords:
- BC30685
ms.assetid: 756add7a-23d5-4b4f-a48d-8297d6459c73
ms.openlocfilehash: 4415608bcfca63b43b3d9ebf17ce622ccd418775
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58820824"
---
# <a name="membername-is-ambiguous-across-the-inherited-interfaces-interfacename1-and-interfacename2"></a><span data-ttu-id="eefef-102">'\<membername >' é ambíguo entre as interfaces herdadas\<interfacename1 >' e '\<interfacename2 >'</span><span class="sxs-lookup"><span data-stu-id="eefef-102">'\<membername>' is ambiguous across the inherited interfaces '\<interfacename1>' and '\<interfacename2>'</span></span>
<span data-ttu-id="eefef-103">A interface herda dois ou mais membros com o mesmo nome de várias interfaces.</span><span class="sxs-lookup"><span data-stu-id="eefef-103">The interface inherits two or more members with the same name from multiple interfaces.</span></span>  
  
 <span data-ttu-id="eefef-104">**ID do erro:** BC30685</span><span class="sxs-lookup"><span data-stu-id="eefef-104">**Error ID:** BC30685</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="eefef-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="eefef-105">To correct this error</span></span>  
  
-   <span data-ttu-id="eefef-106">Converta o valor para a interface base que você deseja usar. Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="eefef-106">Cast the value to the base interface that you want to use; for example:</span></span>  
  
    ```  
    Interface Left  
        Sub MySub()  
    End Interface  
  
    Interface Right  
        Sub MySub()  
    End Interface  
  
    Interface LeftRight  
        Inherits Left, Right  
    End Interface  
  
    Module test  
        Sub Main()  
            Dim x As LeftRight  
            ' x.MySub()  'x is ambiguous.  
            CType(x, Left).MySub() ' Cast to base type.  
            CType(x, Right).MySub() ' Call the other base type.  
        End Sub  
    End Module  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="eefef-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eefef-107">See also</span></span>

- [<span data-ttu-id="eefef-108">Interfaces</span><span class="sxs-lookup"><span data-stu-id="eefef-108">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
