---
title: '&lt;type1&gt;&quot;&lt;typename&gt;&quot;deve implementar&quot;&lt;methodname&gt;&quot;para interface&quot;&lt;interfacename&gt;&quot; | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30149
- bc30149
dev_langs:
- VB
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
caps.latest.revision: 10
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
ms.openlocfilehash: 270d9770b90becf85de68712b8d374282bff135d
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmethodnamegt39-for-interface-39ltinterfacenamegt39"></a><span data-ttu-id="165d7-102">&lt;type1&gt;'&lt;typename&gt;'deve implementar'&lt;methodname&gt;'para interface'&lt;interfacename&gt;'</span><span class="sxs-lookup"><span data-stu-id="165d7-102">&lt;type1&gt;&#39;&lt;typename&gt;&#39; must implement &#39;&lt;methodname&gt;&#39; for interface &#39;&lt;interfacename&gt;&#39;</span></span>
<span data-ttu-id="165d7-103">Uma classe ou estrutura alega implementar uma interface mas não implementa um procedimento definido pela interface.</span><span class="sxs-lookup"><span data-stu-id="165d7-103">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="165d7-104">Cada membro da interface deve ser implementado.</span><span class="sxs-lookup"><span data-stu-id="165d7-104">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="165d7-105">**ID do erro:** BC30149</span><span class="sxs-lookup"><span data-stu-id="165d7-105">**Error ID:** BC30149</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="165d7-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="165d7-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="165d7-107">Declare um procedimento com o mesmo nome e assinatura, conforme definido na interface.</span><span class="sxs-lookup"><span data-stu-id="165d7-107">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="165d7-108">Não se esqueça de incluir pelo menos o `End Function` ou `End Sub` instrução.</span><span class="sxs-lookup"><span data-stu-id="165d7-108">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="165d7-109">Adicionar uma `Implements` cláusula no final do `Function` ou `Sub` instrução.</span><span class="sxs-lookup"><span data-stu-id="165d7-109">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="165d7-110">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="165d7-110">For example:</span></span>  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="165d7-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="165d7-111">See Also</span></span>  
 <span data-ttu-id="165d7-112">[Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md) </span><span class="sxs-lookup"><span data-stu-id="165d7-112">[Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md) </span></span>  
<span data-ttu-id="165d7-113"> [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)</span><span class="sxs-lookup"><span data-stu-id="165d7-113"> [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)</span></span>
