---
title: '&#39; &lt;membername&gt;&#39; é ambíguo nas interfaces herdadas &#39;&lt; interfacename1&gt;&#39; e &#39;&lt; interfacename2&gt;&#39;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30685
- bc30685
helpviewer_keywords:
- BC30685
ms.assetid: 756add7a-23d5-4b4f-a48d-8297d6459c73
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0bf4a9c263fd197cdd5d5b4886ee18e2ff112488
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="39ltmembernamegt39-is-ambiguous-across-the-inherited-interfaces-39ltinterfacename1gt39-and-39ltinterfacename2gt39"></a><span data-ttu-id="0acea-102">&#39; &lt;membername&gt;&#39; é ambíguo nas interfaces herdadas &#39;&lt; interfacename1&gt;&#39; e &#39;&lt; interfacename2&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="0acea-102">&#39;&lt;membername&gt;&#39; is ambiguous across the inherited interfaces &#39;&lt;interfacename1&gt;&#39; and &#39;&lt;interfacename2&gt;&#39;</span></span>
<span data-ttu-id="0acea-103">A interface herda dois ou mais membros com o mesmo nome de várias interfaces.</span><span class="sxs-lookup"><span data-stu-id="0acea-103">The interface inherits two or more members with the same name from multiple interfaces.</span></span>  
  
 <span data-ttu-id="0acea-104">**ID do erro:** BC30685</span><span class="sxs-lookup"><span data-stu-id="0acea-104">**Error ID:** BC30685</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0acea-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="0acea-105">To correct this error</span></span>  
  
-   <span data-ttu-id="0acea-106">Converter o valor para a interface base que você deseja usar; Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="0acea-106">Cast the value to the base interface that you want to use; for example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0acea-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0acea-107">See Also</span></span>  
 [<span data-ttu-id="0acea-108">Interfaces</span><span class="sxs-lookup"><span data-stu-id="0acea-108">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
