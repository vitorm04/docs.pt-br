---
title: "&quot;&lt;membername&gt;&quot;é ambíguo nas interfaces herdadas&quot;&lt;interfacename1&gt;&quot;e&quot;&lt;interfacename2&gt;&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30685
- bc30685
dev_langs:
- VB
helpviewer_keywords:
- BC30685
ms.assetid: 756add7a-23d5-4b4f-a48d-8297d6459c73
caps.latest.revision: 8
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
ms.openlocfilehash: 64b30fc1b1637ce52a6cd6faa89373297e2bf5c3
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="39ltmembernamegt39-is-ambiguous-across-the-inherited-interfaces-39ltinterfacename1gt39-and-39ltinterfacename2gt39"></a><span data-ttu-id="7ca4c-102">'&lt;membername&gt;'é ambíguo nas interfaces herdadas'&lt;interfacename1&gt;'e'&lt;interfacename2&gt;'</span><span class="sxs-lookup"><span data-stu-id="7ca4c-102">&#39;&lt;membername&gt;&#39; is ambiguous across the inherited interfaces &#39;&lt;interfacename1&gt;&#39; and &#39;&lt;interfacename2&gt;&#39;</span></span>
<span data-ttu-id="7ca4c-103">A interface herda dois ou mais membros com o mesmo nome de várias interfaces.</span><span class="sxs-lookup"><span data-stu-id="7ca4c-103">The interface inherits two or more members with the same name from multiple interfaces.</span></span>  
  
 <span data-ttu-id="7ca4c-104">**ID do erro:** BC30685</span><span class="sxs-lookup"><span data-stu-id="7ca4c-104">**Error ID:** BC30685</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7ca4c-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="7ca4c-105">To correct this error</span></span>  
  
-   <span data-ttu-id="7ca4c-106">Converter o valor para a interface base que você deseja usar; Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="7ca4c-106">Cast the value to the base interface that you want to use; for example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7ca4c-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ca4c-107">See Also</span></span>  
 [<span data-ttu-id="7ca4c-108">Interfaces</span><span class="sxs-lookup"><span data-stu-id="7ca4c-108">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
